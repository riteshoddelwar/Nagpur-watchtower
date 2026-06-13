import { useEffect, useMemo } from "react";
import { MapContainer, TileLayer, Marker, Popup, useMap } from "react-leaflet";
import L from "leaflet";
import { NAGPUR_CENTER, activityLabel } from "@/lib/areas";

// Fix default marker icons (Leaflet's default URLs don't resolve through Vite)
const defaultIcon = L.icon({
  iconUrl: "https://unpkg.com/leaflet@1.9.4/dist/images/marker-icon.png",
  iconRetinaUrl: "https://unpkg.com/leaflet@1.9.4/dist/images/marker-icon-2x.png",
  shadowUrl: "https://unpkg.com/leaflet@1.9.4/dist/images/marker-shadow.png",
  iconSize: [25, 41],
  iconAnchor: [12, 41],
  popupAnchor: [1, -34],
  shadowSize: [41, 41],
});
L.Marker.prototype.options.icon = defaultIcon;

export interface MapIncident {
  id: string;
  area: string;
  activity_type: string;
  occurred_at: string;
  description: string;
  latitude: number | null;
  longitude: number | null;
}

function Recenter({ center }: { center: [number, number] }) {
  const map = useMap();
  useEffect(() => {
    map.setView(center, map.getZoom());
  }, [center, map]);
  return null;
}

export function IncidentMap({
  incidents,
  center = NAGPUR_CENTER,
  zoom = 12,
  height = 480,
}: {
  incidents: MapIncident[];
  center?: [number, number];
  zoom?: number;
  height?: number | string;
}) {
  const pins = useMemo(
    () => incidents.filter((i) => typeof i.latitude === "number" && typeof i.longitude === "number"),
    [incidents],
  );

  return (
    <div
      className="overflow-hidden rounded-xl border shadow-sm"
      style={{ height }}
    >
      <MapContainer
        center={center}
        zoom={zoom}
        scrollWheelZoom
        style={{ height: "100%", width: "100%" }}
      >
        <TileLayer
          attribution='&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a>'
          url="https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png"
        />
        <Recenter center={center} />
        {pins.map((i) => (
          <Marker key={i.id} position={[i.latitude as number, i.longitude as number]}>
            <Popup>
              <div className="space-y-1 text-sm">
                <div className="font-semibold">{activityLabel(i.activity_type)}</div>
                <div className="text-muted-foreground">
                  {i.area} · {new Date(i.occurred_at).toLocaleString()}
                </div>
                <p className="mt-1 line-clamp-4">{i.description}</p>
              </div>
            </Popup>
          </Marker>
        ))}
      </MapContainer>
    </div>
  );
}

export default IncidentMap;
