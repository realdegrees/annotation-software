# ❓ WIP  

# ✨ Features  

This document outlines all **user-facing** features of the annotation software project to be implemented.  

---

# 👤 1. User Management  

## 📝 1.1 Registration  
- Create an account with **email + password**  
- **Email verification** required for identity confirmation  

## 🔑 1.2 Login  
- Secure login with **email + password**  
- **Session management** via secure cookies  

## 🏠 1.3 Profile & Dashboard  
Each user has a personal profile/dashboard containing:  

| Section | Contents |
|---------|----------|
| **Identity** | Username, Email address |
| **Memberships** | Overview of Document & Group memberships |
| **Stats** | Number of annotations made, other profile statistics |

## 👥 1.4 Groups  
- Users can **create groups** for collaboration  
- Group owners can invite others via **email, username, or invite URL**  
- Role-based permissions determine actions (add annotations, manage docs, manage members, etc.)  

### 🔒 1.4.1 Permissions  
- **Fine-grained access control** at group level  
- Permission structure documented in the [database schema](./schema.puml)  

---

# 📄 2. Document Management  

## 📤 2.1 Document Handling  
- Upload **personal or group documents (PDFs only initially)**  
- Transfer documents between **users & groups**  
- **Persistent share links** with permission control (read / annotate / manage)  
  - Share links are **revocable per-document**  
  - Share links can be used to work on documents without an account (User is prompted to create an account but can skip it and use an alias temporarily)
- Group documents: accessible to all members (editable depending on permissions)  
- **Annotation Visibility Mode**  
  - Toggle visibility of annotations (e.g. teacher mode to hide/show student annotations)  

## 🖊️ 2.2 Annotations  
- Create annotations with a **visual editor**  
- Annotation types:  
  - **Private** → only visible to creator  
  - **Restricted** → visible to group members with permission  
  - **Public** → visible to all group users  
- **Live sync**: annotations instantly shared with all users who have access (based on visibility settings + doc mode)  
- Anonymous annotation creation with **temporary alias** (via shared links)(no account needed)
  - *(If browser storage is not cleared)* Previous anonymous annotations are linked to a user on account creation

---

# 💡 Additional Feature Ideas  

*(Future / optional extensions that may be too complex for initial release)*  

| Idea | Description |
|------|-------------|
| 🏆 **Score Templates** | Document managers predefine template annotations with scores → users earn points for matching annotations |
| 💬 **Annotation Replies** | Threaded replies for annotations, turning them into discussions |
| 🗂️ **Versioning** | Automatic or manual versioning of annotated documents → owners can browse history & revert changes |
