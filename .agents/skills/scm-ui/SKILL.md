---
name: scm-ui
description: Develops and modifies the SCM React UI following the project's architecture, titleProps, CustomTableContainer, Redux, routing, CRUD, WMS modules, and reusable component standards.
---

# SCM-UI Development Guidelines

## Overview

This repository contains the React/TypeScript frontend for the SCM (Supply Chain Management) platform.

The application follows a generic, configuration-driven architecture where reusable components are preferred over module-specific implementations. Any new feature should integrate with the existing framework instead of introducing new patterns.

---

# Core Principles

## Analyse Before Coding

Before implementing any feature:

- Analyse the existing implementation.
- Identify reusable components.
- Reuse existing architecture.
- Follow the project's coding standards.
- Make the implementation feel like it originally belonged in the project.

Never create duplicate implementations if a reusable solution already exists.

---

# Technology Stack

- React
- TypeScript
- Redux Toolkit
- React Router
- Axios
- Material UI (existing components)
- Custom reusable component library
- Toastr notifications

---

# Folder Structure

Follow the existing folder structure.

Do not introduce a different project organization.

New modules should follow the same structure as existing modules.

---

# Routing Standards

Every module should follow this routing convention.

List Page

```
/module/viewAll
```

Add

```
/module/add
```

Edit

```
/module/:id/edit
```

View

```
/module/:id/view
```

If a module belongs under a parent menu:

```
/master-data/drivers/viewAll

/master-data/drivers/add

/master-data/drivers/:id/edit

/master-data/drivers/:id/view
```

Refreshing the browser should always restore the current page.

---

# Sidebar

Reuse the existing sidebar implementation.

Do not hardcode menu logic.

Parent-child menus should follow the current architecture.

---

# Tabs

Preserve the existing tab implementation.

Opening pages should create tabs.

Refreshing should restore the current tab.

Switching tabs should preserve Redux state.

---

# Generic Table Architecture

Always reuse:

```
CustomTableContainer
```

Never build module-specific tables.

---

# titleProps

All tables must be configuration-driven.

Each table has its own JSON.

Example

```
src/config/tables/
```

```
drivers.json

shipments.json

locations.json
```

Every table is identified using

```
tableId
```

Example

```tsx
<CustomTableContainer
    tableId="drivers"
    ...
/>
```

Never define columns inside pages.

---

# titleProps Structure

```json
{
  "title": "Driver Name",
  "accessPath": "driverName",
  "bodyType": "text",
  "dataType": "String",
  "displayable": true
}
```

---

# displayable

```
displayable = true
```

Render column.

```
displayable = false
```

Hide column.

Never hardcode visibility.

---

# Checkbox Column

Checkbox rendering is configuration-driven.

```
bodyType = "select"
```

Only then should the table render checkbox selection.

---

# Redux

Store:

- Selected rows
- Filters
- Search
- Pagination
- Current tab
- Current page
- Table state

Switching tabs should preserve state.

---

# Delete

Support

Single Delete

Multiple Delete

Delete button above table.

Delete icon inside every row.

---

# Forms

Reuse existing generic components.

Never create new input implementations.

Supported controls

- Text
- Number
- Dropdown
- Checkbox
- Textarea
- Date
- DateTime
- Time
- Switch

---

# Validation

Reuse the existing validation framework.

Do not introduce another validation library.

---

# API Integration

Reuse the existing Axios utilities.

Reuse API services.

Never call Axios directly from components.

---

# Notifications

Reuse Toastr.

Examples

```
Created Successfully

Updated Successfully

Deleted Successfully
```

---

# Search

Reuse existing implementation.

---

# Pagination

Reuse existing implementation.

---

# Sorting

Reuse existing implementation.

---

# Filtering

Reuse existing implementation.

---

# Export

Reuse existing ExportService.

Never create a different export implementation.

---

# Configuration Driven Development

Whenever possible, implement features through configuration.

Examples

- titleProps
- displayable
- tableId
- toolbar
- actions
- filters

Avoid module-specific logic.

---

# Date Handling

Use the existing date utilities.

If unavailable,

use

```
date-fns
```

Do not manually parse Java ZonedDateTime repeatedly throughout components.

Centralize formatting.

---

# UI Consistency

Reuse

- Icons
- Buttons
- Dialogs
- Modals
- Cards
- Layout
- Tables
- Colors
- Typography

Do not introduce a different design language.

---

# Code Reuse

Always prefer

- Existing Hooks
- Existing Components
- Existing Redux slices
- Existing Utilities
- Existing Services

Never duplicate logic.

---

# Performance

Avoid unnecessary renders.

Memoize where appropriate.

Reuse selectors.

Refresh only affected components.

---

# Feature Development Checklist

Before implementing:

- Analyse existing implementation.
- Find reusable components.
- Find existing utilities.
- Understand Redux flow.
- Understand routing.

During implementation:

- Reuse architecture.
- Keep implementation generic.
- Avoid duplication.

After implementation:

- Verify routing.
- Verify Redux persistence.
- Verify table rendering.
- Verify titleProps.
- Verify CRUD.
- Verify Add/Edit/View/List.
- Verify Refresh.
- Verify Delete.
- Verify Toastr.
- Verify Browser Refresh.

---

# WMS Modules

Every new WMS module must include

- List
- Add
- Edit
- View

Reuse

- CustomTableContainer
- titleProps
- Redux
- Routing
- Forms
- Validation
- Toastr
- Delete
- Search
- Pagination

---

# Development Rules

Always:

✅ Analyse first

✅ Reuse existing implementation

✅ Keep implementation generic

✅ Follow existing architecture

✅ Prefer configuration over hardcoding

✅ Keep code maintainable

Never:

❌ Create duplicate implementations

❌ Hardcode module-specific logic

❌ Introduce new architectures

❌ Ignore reusable components

❌ Break existing UI behaviour

---

# Goal

Every new feature should integrate seamlessly into the existing SCM UI, appearing as though it was part of the original application while remaining reusable, scalable, and configuration-driven.