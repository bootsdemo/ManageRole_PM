# PMUM Role Management System

This repository contains the prototype and documentation for the Product Management User Management (PMUM) Role-Based Access Control (RBAC) system.

## 🚀 Overview
The PMUM Role Management system is designed to allow Product Managers to manage granular permissions for their respective products. It supports a full lifecycle from "Out of the Box" (OOB) templates to customizable drafts and finalized active roles.

## 📋 Core Requirements

### 1. Product & Role Architecture
* **Multi-Product Support:** Manage roles across multiple distinct products (e.g., Product A, Product S) within a single interface.
* **PM Data Isolation:** Product Managers are restricted to viewing and managing roles associated only with their assigned product.
* **Granular Permissions:** Roles are defined by a specific set of permissions:
    * `View Reports`, `Invite User`, `Refunds`, `Manage Schedule`, `Create Sale`, `View Catalog`, `Void Transactions`.

### 2. Role Lifecycle Management
* **Master Templates (OOB):** A read-only library of baseline roles available to all products.
* **Drafting Workflow:** PMs can copy a template into a "Draft" state to customize the name and permissions.
* **Activation:** Once a role is moved to "Active" status, it is locked from further editing to ensure environmental stability.

### 3. Naming & Uniqueness Logic
* **Intra-Product Uniqueness:** Within a single product, no two roles (Active or Draft) can share the same name.
* **Case-Insensitivity:** Naming collisions are checked regardless of capitalization (e.g., "Manager" and "manager" are duplicates).
* **Cross-Product Reuse:** The same role name is permitted to exist across different products.
* **Template Collision Handling:** To avoid immediate naming conflicts when copying from a template, the system automatically prepends a **"Draft - "** prefix to the role name.

### 4. Validation & UX
* **Error Handling:** Attempts to save a role with a non-unique name are blocked with an explicit error message.
* **Visual Context:** The interface uses color-coding to identify the specific product environment being managed.
* **Read-Only Integrity:** Active roles and Master Templates strictly prohibit modifications.

## 🛠 Tech Stack
* **Frontend:** HTML5, Tailwind CSS, JavaScript (ES6+).
* **Backend:** Supabase (PostgreSQL) for data persistence.
* **Multi-tenancy:** Implemented via `project_key` and `product` filtering logic.# ManageRole_PM
