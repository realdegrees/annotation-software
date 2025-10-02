> ❓ Acknowledged by the stakeholder on October 2, 2025  

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
- Account recovery via **email**

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

### 🔒 1.4.1 Permissions  
- **Fine-grained access control** at group level  
- Permission structure documented in the [database schema](./schema.puml)  
- Determines what actions users can perform within a group (e.g., manage documents, manage members, view restricted comments)

---

# 📄 2. Document Management  

## 📤 2.1 Document Handling  
- Upload **personal or group documents (PDFs only initially)**  
- Transfer documents between **users & groups**  
- **Persistent share links** with [permission](#-14-permissions) control
  - Share links are **revocable per-document**  
  - Share links can be used to work on documents without an account (User is prompted to create an account but can skip it and use an alias temporarily)
- **View Mode**  
  The view mode can be changed by the document owner for personal documents or by authorized group members for group documents. It controls how annotations are displayed to regular viewers (users without permissions to view restricted content).
  - **Private:** Regular viewers can only see their own annotations & comments
  - **Anonymous:** Regular viewers see all public annotations & comments but without info about the creator
  - **Public:** Regular viewers see all public annotations & comments with creator info
- **Live sync**: [annotations](#️-22-annotations) & [comments](#-23-comments) are instantly shared with all users who have access (based on visibility settings + doc mode)

## 🖊️ 2.2 Annotations  
- Create annotations with a **visual editor**  
  - Text highlights initially (other types like shapes, drawings, etc. may be added later)  
  - Optionally add a [comment](#-221-comments) to an annotation  
  *(Annotations internally create a an empty comment to associate them with a visibility level and user)*  
- Anonymous annotation creation with **temporary alias** (via shared links)(no account needed)
  - *(If browser storage is not cleared)* Previous anonymous annotations are linked to a user on account creation


## 📜 2.3 Comments

- **Visibility**  
  Comments can have different visibility types that (in combination with the document's View Mode) determine if other document viewers can see them.
  - **Private** → only visible to creator  
  - **Restricted** → visible to group members with permission to view restricted comments
  - **Public** → visible to all group users  
- Comments can be
  - document comments (restricted visibility by default)
  - annotation comments (public visibility by default)
  - replies to other comments (inherit visibility from parent comment)
- Comment visibility can be changed by the creator
- Comments support **threaded replies**
- Comments can be **edited or deleted** by their creator
- Anonymous commenting with **temporary alias** (via shared links)(no account needed)
  - *(If browser storage is not cleared)* Previous anonymous comments are linked to a user on account creation

---

# 💡 Additional Feature Ideas  

*(Future / optional extensions that may be too complex for initial release)*  
This section will be expanded as the project progresses.  

| Idea | Description |
|------|-------------|
| 🏆 **Endorsements** | Document viewers (with endorse permission) can endorse annotations, endorsements are listed in the user statistics and endorsed comments can be highlighted depending on number of endorsements |
| 💬 **Annotation Replies** | Threaded replies for annotations, turning them into discussions |
| 🗂️ **Versioning** | Automatic or manual versioning of annotated documents → owners can browse history & revert changes |
