---
cssclass: dashboard
banner: "![[banner-1.jpg]]"
banner_y: 0.814
---

# Trackers

- ![[Drink Water Tracker]]
- ![[Warning Up Tracker]]

# Knownledge

- ![[SQL]]

# Kanbans

- ![[University]]

# Vault Info
- 📂 Recent file updates
 `$=dv.list(dv.pages('').sort(f=>f.file.mtime.ts,"desc").limit(4).file.link)`
- ⭐ Tagged:  favorite 
 `$=dv.list(dv.pages('#favorite').sort(f=>f.file.name,"desc").limit(4).file.link)`
- 〽️ Stats
	-  File Count: `$=dv.pages().length`