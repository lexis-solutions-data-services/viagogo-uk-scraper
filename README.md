# Viagogo UK Event Scraper

![banner](https://i.ibb.co/SwvGb68N/Screenshot-2025-11-15-at-11-50-47-PM.png)

Capture Viagogo UK ticket availability and pricing straight from the source.

<p align="center">
  <img src="https://apify-image-uploads-prod.s3.us-east-1.amazonaws.com/DevbkY3adMTBuoECt-actor-5jotmyiHhbLzHQaC9-nL12plEsRp-5767109.png" alt="Viagogo.uk Scraper" style="height: 60px; margin-right: 15px;" /><a href="https://apify.com/lexis-solutions/viagogo-uk-scraper" target="_blank">
    <img src="https://img.shields.io/badge/Try%20it%20on-Apify-0066FF?style=for-the-badge&logo=data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iNDA4IiBoZWlnaHQ9IjQwOCIgdmlld0JveD0iMCAwIDQwOCA0MDgiIGZpbGw9Im5vbmUiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyI+CjxnIGNsaXAtcGF0aD0idXJsKCNjbGlwMF8zNDFfNDE1NykiPgo8cGF0aCBkPSJNMjE4LjY5NSAxMDRIMzAwLjk3QzMwMi42NDMgMTA0IDMwNCAxMDUuMzU3IDMwNCAxMDcuMDNWMjMyLjc2NkMzMDQgMjM1Ljc3OCAzMDAuMDgzIDIzNi45NDUgMjk4LjQzNCAyMzQuNDI1TDIxNi4xNTkgMTA4LjY5QzIxNC44NDEgMTA2LjY3NCAyMTYuMjg3IDEwNCAyMTguNjk1IDEwNFoiIGZpbGw9IndoaXRlIi8+CjxwYXRoIGQ9Ik0xODkuMzA1IDEwNEgxMDcuMDNDMTA1LjM1NyAxMDQgMTA0IDEwNS4zNTcgMTA0IDEwNy4wM1YyMzIuNzY2QzEwNCAyMzUuNzc4IDEwNy45MTcgMjM2Ljk0NSAxMDkuNTY2IDIzNC40MjVMMTkxLjg0IDEwOC42OUMxOTMuMTU5IDEwNi42NzQgMTkxLjcxMyAxMDQgMTg5LjMwNSAxMDRaIiBmaWxsPSJ3aGl0ZSIvPgo8cGF0aCBkPSJNMjAyLjU5MSAyMDQuNjY4TDEwOS4xMjcgMjk4LjgzNUMxMDcuMjI5IDMwMC43NDcgMTA4LjU4MyAzMDQgMTExLjI3OCAzMDRIMjk2LjhDMjk5LjQ4MyAzMDQgMzAwLjg0MiAzMDAuNzcgMjk4Ljk2NyAyOTguODUyTDIwNi45MDggMjA0LjY4NUMyMDUuNzI2IDIwMy40NzUgMjAzLjc4MiAyMDMuNDY4IDIwMi41OTEgMjA0LjY2OFoiIGZpbGw9IndoaXRlIi8+CjwvZz4KPGRlZnM+CjxjbGlwUGF0aCBpZD0iY2xpcDBfMzQxXzQxNTciPgo8cmVjdCB3aWR0aD0iMjAwIiBoZWlnaHQ9IjIwMCIgZmlsbD0id2hpdGUiIHRyYW5zZm9ybT0idHJhbnNsYXRlKDEwNCAxMDQpIi8+CjwvY2xpcFBhdGg+CjwvZGVmcz4KPC9zdmc+Cg==&logoColor=white" alt="Try it on Apify" style="border-radius: 12px; height: 60px;" />
  </a>
</p>



## 📊 Actor Stats

| Stat | Value |
|------|-------|
| **Version** | `1.0.1` |
| **Last Update** | Dec 1, 2025 |

---



## 💻 Integration Examples

This repository includes example code showing how to integrate the `viagogo-uk-scraper` actor into your projects.

You can find example implementations in the [`examples/`](./examples) folder:
- **TypeScript/JavaScript**: See [`examples/typescript/`](./examples/typescript) for a complete TypeScript example
- **Python**: See [`examples/python/`](./examples/python) for a complete Python example

Each example includes:
- Ready-to-use code templates
- Setup instructions
- Documentation links

---


## Features

- 🎯 **Single-run coverage** – Pull both venue map availability and individual ticket listings in one pass.
- 🔁 **Proxy support** 
- 🛡️ **Max items cap** – Stop after a configurable number of listings to keep payloads manageable.

## Input

```json
{
  "startUrls": [
    {
      "url": "https://www.viagogo.co.uk/Concert-Tickets/Other-Concerts/Lewis-Capaldi-Tickets/E-159436715?quantity=2"
    }
  ],
  "maxItems": 20
}
```

| Field       | Type    | Required | Description                                                                                     |
|-------------|---------|----------|-------------------------------------------------------------------------------------------------|
| `startUrls` | array   | ✅        | Array of Viagogo event URLs. Accepts either strings or objects with a `url` key.                |
| `maxItems`  | integer | ❌        | Maximum number of listings to keep per event (0 = unlimited) |

## Output

- 📦 **Dataset**: One item per processed event combining map availability + listing details
- 🗂️ **Key-value store**: Latest event payload stored under the `OUTPUT` key

Each item uses the structure:

```json
{
  "eventId": "157374369",
  "scrapedAt": "2025-11-14T11:42:26.950Z",
  "mapAvailability": {
    "totalSections": 48,
    "sections": [
      {
        "sectionKey": "267_56342",
        "ticketClassId": 267,
        "sectionId": 56342,
        "row": "Upper",
        "listingCount": 1,
        "ticketCount": 2,
        "minPrice": {
          "raw": 239.22,
          "formatted": "£239"
        },
        "dealScore": 6.716455370651891,
        "hasAisleSeat": false,
        "listingId": 10804104792
      }
    ],
    "metadata": {
      "bestDealFeatureIds": ["listing::10804104792"],
      "cheapestFeatureIds": ["listing::10804104792"]
    }
  },
  "listings": {
    "totalListings": 20,
    "totalAvailable": 60,
    "pageSize": 6,
    "items": [
      {
        "id": 10838642974,
        "section": "M15",
        "row": "62",
        "seats": "413_414",
        "availableTickets": 2,
        "ticketClassName": "Middle Tier",
        "ticketTypeName": "Mobile Transfer ticket",
        "rawPrice": 260.57,
        "price": "£261",
        "faceValue": 193,
        "formattedDealScore": "5.3",
        "listingNotes": [
          {
            "content": "Clear view",
            "description": "You'll have an unrestricted view of the show."
          }
        ],
        "createdDateTime": "2025-11-13T09:44:33.2800000Z"
      }
    ]
  }
}
```

> Map and listings arrays are trimmed by `maxItems` when the limit is non-zero.

## Support

Need tailored data, automation tweaks, or a managed scraping pipeline? Lexis Solutions is a [certified Apify Partner](https://apify.com/partners/find). Reach out via [Email](mailto:scraping@lexis.solutions) or [LinkedIn](https://www.linkedin.com/company/lexis-solutions) for expert help.

If this actor saves you time, we’d appreciate a quick review on our [partner page](https://apify.com/partners/find/lexis-solutions/review) 🙌
