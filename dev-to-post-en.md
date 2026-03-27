# 💊 Did You Take Your Medicine Today? I Built a Pure-Frontend Medication Reminder App

> A lightweight, no-sign-up, plug-and-play daily medication reminder tool

---

## 🎯 The Origin

As a working professional who kept forgetting to take my vitamins, I realized I needed a simple tool to remind myself to take medications on time. The medical apps out there were too heavy, too complex, and required registration — I just wanted to casually log "did I take my medicine today?"

That's how this project was born: **"Did You Take Your Medicine Today?"**

**Core Philosophy:**
- ✅ Open and use instantly, no registration
- ✅ Data stays local, privacy protected
- ✅ Clean interface, one-tap check-in
- ✅ Browser push notifications for reminders

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|------------|
| Frontend | HTML5 + CSS3 + Vanilla JS |
| Storage | LocalStorage |
| Reminders | Web Notification API |
| Deployment | Static files (hosted on Cloudflare Pages) |

**Why pure frontend?**
- Zero backend dependency, lowest cost
- No need to deal with server security or data compliance
- User data stays completely private, never uploaded to any server

---

## 📱 Features

### Core Features

1. **Daily Check-in** — One tap to mark "I took my medicine today", never forget again
2. **Medication Management** — Add/edit/delete medications, set reminder times and dosages
3. **Browser Notifications** — Scheduled push reminders for taking medications
4. **Today's Status** — Open the page and know immediately if you took your medicine today

### Additional Features

- 7-day medication history
- Adherence statistics
- Responsive design, mobile-friendly

---

## 🎨 UI Design

Using a **purple gradient** as the primary color, paired with green (success) and red (incomplete) for contrast:

```css
/* Primary color */
background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);

/* Success / Taken */
background: linear-gradient(135deg, #11998e 0%, #38ef7d 100%);

/* Incomplete */
background: linear-gradient(135deg, #eb3349 0%, #f45c43 100%);
```

**Design Principles:**
- Large buttons, high contrast, suitable for elderly users
- Card-based layout, clear hierarchy
- Max width 480px, mobile-first

---

## 💾 Data Structure

```json
{
  "medicines": [
    { "name": "Vitamin C", "time": "09:00", "dose": "1 tablet" },
    { "name": "Calcium", "time": "21:00", "dose": "2 capsules" }
  ],
  "records": {
    "2026-03-27": ["Vitamin C", "Calcium"],
    "2026-03-26": ["Vitamin C"]
  }
}
```

All data is stored in the user's browser LocalStorage, **never uploaded**.

---

## 🤔 Technical Challenges

### 1. Browser Notification Permissions

Many users reject notification permissions on first use. Need to gracefully handle the fallback scenario:

```javascript
// Request notification permission
Notification.requestPermission().then(permission => {
  if (permission === 'granted') {
    // Can send notifications now
  } else {
    // Show a prompt to guide user to enable manually
  }
});
```

### 2. Cross-Date Data Synchronization

Users might add tomorrow's medication at 23:59. Need to ensure data consistency during date transitions.

### 3. LocalStorage Capacity Limits

While LocalStorage has a 5-10MB limit, for plain-text medication records this is more than sufficient.

---

## 📂 Project Structure

```
medicine-reminder/
├── medicine-reminder.html   # Main page
├── user.html               # User page
├── login.html              # Login page
├── donation.html           # Donation page
├── MVP-需求文档.md          # Requirements doc (Chinese)
└── _headers                # Cloudflare deployment config
```

---

## 🚀 Deployment

The project is deployed on Cloudflare Pages with a custom domain.

**Deployment:**
```bash
# Install wrangler CLI
npm install -g wrangler

# Deploy
wrangler pages deploy .
```

---

## 📈 Roadmap

| Version | Features |
|---------|----------|
| V1.1 | 7-day history, adherence stats, data export |
| V2.0 | User accounts, multi-device sync, family reminders |

---

## 💡 Conclusion

This tool is simple, but it solves a real problem: helping people build the habit of taking medications on time.

**On the tech choices**, the pure frontend approach sacrifices some "advanced features" (like multi-device sync) in exchange for extremely low development and maintenance costs, plus complete user control over their data. This is a classic "good enough is enough" product decision.

If you have similar needs, feel free to use it or fork it for customization!

---

*Project: [GitHub Repository] (to be added)*  
*Live Demo: [https://your-domain.com] (to be added)*

---

**#javascript #webdev #sideproject #productivity #health**
