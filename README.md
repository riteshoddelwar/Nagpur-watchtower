# Nagpur City Watch 📍🚔

Nagpur City Watch is an open-source, AI-assisted, crowdsourced community safety and anonymous crime-reporting platform. Built specifically to address the rising safety concerns in Nagpur, this web application empowers local citizens to report suspicious activities, street crimes, and public safety hazards anonymously, helping to map out high-risk zones and assist community awareness.

> ⚠️ **CRITICAL DISCLAIMER:** This platform is strictly for informational purposes and community awareness. It is NOT a replacement for emergency services. In case of an active emergency, citizens must immediately dial 100 or 112 to reach the Nagpur Police.

---

## ✨ Features

- **Anonymous Incident Reporting:** A streamlined, secure form allowing citizens to report incidents (Theft, Vandalism, Suspicious Behavior, Gang Activity) without revealing their identity or IP address.
- **Hyper-Local Categorization:** Built-in filtering for major Nagpur wards and localities (Sakkardara, Sitabuldi, Dharampeth, Sadar, Mahal, Manish Nagar, Nandanvan, etc.).
- **Interactive Safety Map:** Uses open-source mapping (OpenStreetMap/Leaflet) centered on Nagpur to pin reported incidents visually without heavy API costs.
- **Admin Moderation Queue:** To prevent defamation, spam, and personal vendettas, all user submissions enter a "Pending" state and must be approved by an administrator before appearing on the public map.
- **Zero Public Chat/Comments:** Designed intentionally without peer-to-peer messaging or comment sections to eliminate gossip, trolling, and retaliation risks.
- **Official Resources Portal:** Direct routing and quick-links to official channels like the Nagpur Police portals and the National Cyber Crime Portal.

---

## 🛠️ Tech Stack

This project was developed using a modern, lightweight, and cost-effective no-code/AI stack:

- **Frontend:** React.js / Vite (Generated via AI-assisted builders like Lovable.dev / Bolt.new)
- **Styling:** Tailwind CSS
- **Mapping:** OpenStreetMap / React-Leaflet (100% Free & Open-Source)
- **Database & Backend:** Supabase (PostgreSQL)
- **Image Storage:** Cloudinary (Secure storage for user-uploaded evidence/photos)

---

## 🔒 Security & Privacy Measures

Given the sensitive nature of crime reporting, this repository strictly adheres to the following principles:
1. **Data Minimization:** No user accounts, emails, or PII (Personally Identifiable Information) are tracked or stored for reporters.
2. **Strict Moderation:** No raw user input goes live automatically; the admin dashboard acts as a strict filter to protect innocent private individuals from unverified claims.
3. **Defamation Protection:** The system automatically flags and holds posts containing specific names or personal target details.

---

## 🚀 Future Roadmap

- Integrate automated data exports to format community tips into easily readable PDFs for local police stations.
- Implement automated SMS alerts for specific neighborhoods when a high-priority hazard is approved by admins.
- Add AI-driven text analysis to group similar/duplicate reports automatically.

---

## 🤝 Contributing

Contributions are welcome! If you want to help improve the mapping system, add more localized Nagpur ward boundaries, or improve database security, please fork the repo and submit a pull request.
