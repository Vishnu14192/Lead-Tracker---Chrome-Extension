# 🔗 Lead Tracker - Chrome Extension

A simple Chrome extension to save and manage website leads locally using JavaScript and Chrome APIs.

---

## 📑 Table of Contents

- [Overview](#overview)  
- [Features](#features)    
- [Links](#links)  
- [Installation](#installation)  
- [My Process](#my-process)  
- [Built With](#built-with)  
- [What I Learned](#what-i-learned)  


---

## ✅ Overview

This Chrome Extension allows you to:

- Save leads by typing them into an input box  
- Save the currently active Chrome tab instantly  
- View and click on saved leads (open in a new tab)  
- Store leads using localStorage  
- Delete all leads with a double-click on the delete button  
- Persist leads even after restarting Chrome  

---

## 🎯 Features

- Add new leads manually  
- Save current tab URL with one click  
- Clear all leads (with double-click safety)  
- Fully responsive design  
- Local storage for offline persistence  
- Clean and minimal UI  

---


## 🔗 Links

 
- **Live Extension**: Load it manually in Chrome using developer mode (see below)

---

## 🛠 Installation

1. Clone or download this repository  
2. Open Google Chrome and go to `chrome://extensions/`  
3. Turn on **Developer Mode** (top-right switch)  
4. Click **Load Unpacked**  
5. Select the root folder of this project  
6. The extension will appear in your browser toolbar 🎉

---

## 🔧 My Process

- Planned core functionality: add, display, persist, and delete leads  
- Built a responsive layout using HTML & CSS  
- Used localStorage to make data persistent  
- Implemented Chrome tab capture using `chrome.tabs.query`  
- Used `dblclick` event to protect from accidental deletions  
- Enhanced user experience with simple hover effects and open-in-new-tab links

---

## 🛠 Built With

- HTML5 (Semantic Markup)  
- CSS3 (Custom Properties & Grid)  
- Vanilla JavaScript  
- Chrome Extensions API  
- Mobile-first and minimal design  

---

## 📚 What I Learned

While building this extension, I gained deeper experience with:

### 🔗 Saving the current tab

```js
tabBtn.addEventListener("click", function () {
  chrome.tabs.query({ active: true, currentWindow: true }, function (tabs) {
    myLeads.push(tabs[0].url);
    localStorage.setItem("myLeads", JSON.stringify(myLeads));
    render(myLeads);
  });
});

### 🧾 Rendering leads with template strings
function render(leads) {
  let listItems = "";
  for (let i = 0; i < leads.length; i++) {
    listItems += `<li>
      <a target="_blank" href="${leads[i]}">
        ${leads[i]}
      </a>
    </li>`;
  }
  ulEl.innerHTML = listItems;
}

