# Rider Saathi Pro X — Extreme Edition

ही आवृत्ती Rider Saathi Pro V9 Command Center वर आधारित आहे. कमाई, खर्च, GPS (foreground browser session), रिपोर्ट, PIN आणि backup सुविधा ठेवून Extreme Intelligence पॅनेल जोडले आहे.

## वापर
1. ZIP Extract करा.
2. `index.html` Chrome मध्ये उघडा. GPS आणि PWA install सारखी browser features HTTPS hosting वर अधिक विश्वासार्ह चालतात.
3. पहिल्यांदा PIN सेट करा आणि नियमित Backup घ्या.

## या आवृत्तीत
- AI Daily Goal Simulator (डिव्हाइसवरील नियमाधारित गणना)
- बोनस व नोंदवलेले खर्च धरून दैनिक नेट / KM आणि प्रति ऑर्डर विश्लेषण
- संभाव्य duplicate नोंदींची तपासणी
- Bike Care Reminder
- Online / Offline स्थिती
- Auto backup आणि JSON restore
- GitHub Pages साठी आवश्यक `index.html`, `manifest.webmanifest`, `sw.js`, `icon.svg`

## मर्यादा स्पष्टपणे
- हे HTML/PWA आहे; स्क्रीन बंद असताना सतत GPS चालण्याची हमी नाही.
- Swiggy/Zomato/Shadowfax मधील ऑर्डर किंवा कमाई आपोआप वाचली जात नाही. समर्थित API किंवा स्पष्ट परवानगी असलेली Native Android सेवा आवश्यक आहे.
- AI insight हा या डिव्हाइसवरील नोंदींवर आधारित नियमाधारित सारांश आहे; cloud AI नाही आणि कमाईची हमी नाही.
- Android Native Background Location, Notification Listener, सुरक्षित OCR, Cloud Sync आणि SOS यांची प्रत्यक्ष अंमलबजावणी या ZIP मध्ये नाही.
- PIN हा या browser storage वरील स्थानिक लॉक आहे; तो encrypted cloud security किंवा server authentication समजू नये.

## GitHub वर टाकणे
1. ZIP Extract करा.
2. GitHub वर नवीन repository तयार करा. नाव उदा. `rider-saathi-pro-x`.
3. Extract केलेल्या folder मधील फाईल्स repository च्या root मध्ये upload करा (ZIP फाईल एकटी upload करू नका).
4. Commit करा.
5. मोफत GitHub Pages वापरायचे असल्यास repository Public ठेवा; Settings → Pages → Deploy from a branch → `main` → `/ (root)` → Save.
6. काही वेळाने Pages URL दिसेल: `https://USERNAME.github.io/rider-saathi-pro-x/`.

फोनवर ZIP extract करून GitHub च्या browser upload मधून फाईल्स निवडता येतात. ZIP मधील `README_MR.md` आणि `GITHUB_UPLOAD_GUIDE_MR.md` मार्गदर्शनासाठी आहेत.

**सुरक्षा:** कोणतेही API keys, passwords, personal backup JSON किंवा rider चे खाजगी डेटा repository मध्ये upload करू नका. Public repository मधील कोड सर्वांना दिसतो.
