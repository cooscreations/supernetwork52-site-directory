# Supernetwork52 (Joomla 6 Component)

## Overview

Supernetwork52 is a custom Joomla 6 component designed to manage and display a structured directory of external websites ("Sites") with categorisation, filtering, and frontend rendering.

It provides:

- Admin CRUD interface for managing sites
- Category support via Joomla core categories
- Frontend directory output via menu item
- Search and filtering capabilities
- Featured and published state handling

---

## Core Features

### Admin (Backend)

- Create, edit, delete Sites
- Assign Sites to Categories
- Toggle Published / Featured status
- Search Sites by:
  - Title
  - URL
  - Description
  - ID (`id:123`)
- Filter by:
  - Category
  - Featured status

### Frontend

- Public directory of Sites
- Menu-driven rendering
- Optional filtering:
  - Category
  - Featured only
- Optional search bar

---

## Data Model

### Table: `#__supernetwork52_sites`

| Field       | Type        | Notes                          |
|------------|------------|--------------------------------|
| id         | INT        | Primary key                    |
| title      | VARCHAR    | Site name                      |
| url        | VARCHAR    | External link                  |
| description| TEXT       | Optional description           |
| catid      | INT        | Joomla category ID             |
| featured   | TINYINT    | Featured flag                  |
| published  | TINYINT    | Publish state                  |
| created    | DATETIME   | Auto timestamp                 |

---

## Installation

### Fresh Install

1. Log into Joomla Administrator
2. Navigate to:

```text
System → Install → Extensions
```

3. Upload the component ZIP:

```text
com_supernetwork52_v0.3.2_fresh_install_safe_henry.zip
```

4. Install

---

### Upgrade

To upgrade:

- Install new ZIP over existing version
- Do NOT uninstall (prevents data loss)

---

## Usage

### Admin

Access:

```text
Components → Supernetwork52 → Sites
```

Create new site:

1. Click **New**
2. Enter:
   - Title
   - URL
   - Category
3. Save

Manage categories:

```text
Components → Supernetwork52 → Categories
```

---

### Frontend

Create a menu item:

```text
Menus → Main Menu → New
```

Set:

| Field           | Value                        |
|----------------|------------------------------|
| Title          | Site Directory               |
| Menu Item Type | Supernetwork52 → Site Directory |
| Status         | Published                    |

Optional:

- Filter by category
- Show featured only
- Enable search

Visit:

```text
/site-directory
```

---

## Architecture

Follows Joomla 6 MVC pattern:

```text
administrator/
  components/com_supernetwork52/
    src/
      Controller/
      Model/
      Table/
      View/
    tmpl/

components/
  com_supernetwork52/
    src/
      View/
    tmpl/
```

Key elements:

- Model handles data and form logic
- Table enforces validation
- View renders layouts
- Controller manages CRUD actions

---

## Key Implementation Notes

- Uses Joomla table prefix abstraction (`#__`)
- No hardcoded database prefixes
- Compatible with Joomla 6 / PHP 8.3
- Category integration uses Joomla core `com_categories`
- Form XML defines admin fields

---

## Sample Data (v0.3.2)

Included for testing:

- http://www.largeproductions.com/
- https://www.zobbster.co.uk/
- https://www.cooscreations.com
- https://www.markclulow.com

---

## Known Limitations

- No ACL fine-grained permissions yet
- No import/export (CSV) functionality
- No API endpoints
- No caching layer
- Screenshot/media handling basic or not fully implemented
- No schema versioning system yet

---

## Future Enhancements

- CSV bulk import
- API endpoints (REST)
- SEO routing (slug-based URLs)
- Media/image handling
- Advanced filtering UI
- Ordering and ranking logic
- Caching for frontend performance
- Full schema migrations (`updates/mysql`)

---

## Development Notes

- Built iteratively through live debugging on Joomla 6
- Resolved issues including:
  - Encoding (UTF-16 → UTF-8)
  - Layout path mismatches
  - Form loading failures
  - MVC signature mismatches (PHP 8.3)
  - Toolbar binding (`adminForm`)
  - Missing DB table creation
  - Incorrect application state handling

---

## Deployment Considerations

- Safe for fresh install (v0.3.2+)
- Safe for upgrade without uninstall
- Portable across environments (no hardcoded prefixes)
- Requires Joomla 6+

---

## License

Internal / proprietary (adjust as needed)

---

## Project Owner

Henry Johnson
Large Productions

---

## Author

Mark Clulow  
Coos Creations Ltd
