---
cssclass: dashboard
banner: "![[Japanese_sakura_garden_alone_male_person_with_long_whit_344d6a80-4a9d-49ae-80ad-1b8b4d19b397.png]]"
banner_y: 0.7
---

# Knownledge

- ![[SQL]]
- ![[Internet]]
- ![[Golang]]
- ![[OS]]
- ![[Programming]]

# Kanbans

- ![[University]]

# Vault Info
- 📂 Recent file updates
 `$=dv.list(dv.pages('').sort(f=>f.file.mtime.ts,"desc").limit(4).file.link)`
- ⭐ Tagged: favorite 
 `$=dv.list(dv.pages('#favorite').sort(f=>f.file.name,"desc").limit(4).file.link)`
- 🤖 Tagged: api 
 `$=dv.list(dv.pages('#api').sort(f=>f.file.name,"desc").limit(4).file.link)`
- 〽️ Stats
	-  File Count: `$=dv.pages().length`