# 🔍 Google Dorking Cheat-Sheet for Developers

Google Dorking = Advanced Google Search Operators  
Use cases → **Developer resumes, portfolios, projects, documents** search.

---

## 📂 1. File Search
- `filetype:pdf resume developer` → Sirf PDF resumes  
- `filetype:docx "software engineer cv"` → DOCX resumes  
- `filetype:txt "password"` ⚠️ Security research only  

---

## 🌐 2. Site-Specific Search
- `site:github.com "machine learning project"` → GitHub par projects  
- `site:linkedin.com/in "React Developer"` → LinkedIn profiles  
- `site:github.io portfolio` → GitHub Pages par portfolios  
- `site:vercel.app "developer portfolio"` → Vercel par portfolios  

---

## 🏷️ 3. Title & URL Based
- `intitle:resume "python developer"` → Page title me "resume"  
- `inurl:portfolio "full stack developer"` → URL me "portfolio"`  

---

## ✨ 4. Exact Phrase
- `"full stack developer resume"` → Exact phrase  
- `"react developer" "portfolio"` → Dono phrases saath me  

---

## 🔗 5. Combine Operators
- `"software engineer" AND "resume" filetype:pdf`  
- `("React developer" OR "Angular developer") site:github.com`  

---

## 🚫 6. Exclude Terms
- `developer portfolio -template -sample` → Template/sample exclude karega  

---

## 📅 7. Date Filters
- `resume "python developer" filetype:pdf after:2022` → 2022 ke baad ke resumes  

---

## ⚡ Quick Copy Examples
```sh
"portfolio" "devops engineer" site:github.io
"React Developer" site:vercel.app
resume "Java Developer" filetype:pdf
intitle:resume "Django developer"
```

---

⚠️ **Note**:  
Google Dorking originally **cybersecurity research** me use hota hai. Is cheat-sheet ko **ethical aur safe purposes** ke liye hi use karein (portfolio inspiration, resume samples, open-source projects).
