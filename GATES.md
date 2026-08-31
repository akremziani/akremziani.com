# Gates: Akrem Ziani personal site

OWNS: index.html, assets/profile.css, about/index.html, onzaris/index.html, writing/**, sitemap.xml

Scope: Replace the legacy homepage with a focused founder site for Akrem Ziani and align the supporting navigation/contact copy.

- [ ] G1: Homepage contains the approved founder/Onzaris message and does not contain the legacy newsletter/media copy.
  CHECK: node -e "const fs=require('fs'); const p=fs.readFileSync('index.html','utf8'); const yes=['I build companies from the field.','Currently building Onzaris','business/GTM cofounder','Start a founder conversation']; const no=['Hi, Hey','Get access to my weekly newsletter','Media features','Acces now','NO to $30 million']; if(yes.some(x=>!p.includes(x))) throw new Error('required homepage copy missing'); if(no.some(x=>p.includes(x))) throw new Error('legacy homepage copy remains'); console.log('HOME_COPY_PASS');"
  EXPECT: HOME_COPY_PASS
  EVIDENCE: `node -e ...` exited 0; output `HOME_COPY_PASS`.

- [ ] G2: Homepage and supporting pages use accessible, real navigation/contact links and contain no placeholder hash links.
  CHECK: node -e "const fs=require('fs'); const files=['index.html','about/index.html','onzaris/index.html','writing/index.html','writing/why-i-started-onzaris/index.html']; const all=files.map(f=>fs.readFileSync(f,'utf8')).join('\\n'); if(all.includes('href=\"#\"')) throw new Error('placeholder hash link remains'); if(all.includes('mailto:akrem@onzaris.com')) throw new Error('old contact identity remains'); if(!all.includes('mailto:akrem@akremziani.com')) throw new Error('personal contact link missing'); console.log('LINKS_PASS');"
  EXPECT: LINKS_PASS
  EVIDENCE: `node -e ...` exited 0; output `LINKS_PASS`.

- [ ] G3: Production deployment serves the new homepage and the supporting routes remain reachable.
  EVIDENCE: pending
