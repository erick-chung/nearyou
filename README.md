# NearYou — Restaurant Discovery Web Application

NearYou is a full-stack restaurant discovery application that allows users to search for restaurants around any destination, rather than being limited to their current location.

## Why I Built NearYou

I built NearYou after noticing a UX limitation while using Google Maps.

When I wanted to find restaurants near a place I planned to visit later, I found the process unnecessarily complicated. Search results and distance information often centered around my current location rather than the destination I actually cared about.

For example, if I was planning to meet someone near Times Square while I was currently in New Jersey, I wanted to be able to enter the Times Square address and browse restaurants based on their proximity to that destination.

NearYou was designed to solve that problem.

Users can enter any address or location and browse nearby restaurants as if they were already there. Restaurant results are displayed alongside an interactive map and can be filtered, sorted, and saved to a personal favorites list.

**Status:** Previously deployed on Vercel. The application is currently available through its source code and can be run locally.

---

## Screenshots

### Restaurant Search Results

Users can enter an address or destination and browse nearby restaurants on an interactive map alongside a list of results.

**ADD YOUR SEARCH RESULTS SCREENSHOT HERE**

```md
![NearYou restaurant search results](docs/images/search-results.png)
```

### Filters

Users can filter and reorder restaurant results to make it easier to find relevant options around their selected destination.

**ADD YOUR FILTER MENU SCREENSHOT HERE**

```md
![NearYou filter menu](docs/images/filter-menu.png)
```

### Favorites

Authenticated users can save restaurants to their account and access their favorites across sessions.

**ADD YOUR FAVORITES SCREENSHOT HERE**

```md
![NearYou favorites page](docs/images/favorites.png)
```

---

## Key Features

- Search for restaurants near any entered address or destination
- Search using restaurant names or locations
- Interactive Google Maps interface with clickable restaurant markers
- Display restaurant results relative to the user's selected destination
- Filter and sort restaurant results
- Secure user authentication with Clerk
- Save and remove favorite restaurants
- Persist favorites using PostgreSQL
- Optimistic UI updates for responsive favorite interactions
- Responsive user interface with loading states and keyboard navigation

---

## Tech Stack

| Category | Technology |
|---|---|
| Framework | Next.js 15 |
| Language | TypeScript |
| Frontend | React, Tailwind CSS |
| Database | PostgreSQL (Neon) |
| ORM | Prisma |
| Authentication | Clerk |
| Maps & Places | Google Maps JavaScript API, Google Places API |
| Deployment | Vercel |
| Version Control | Git, GitHub |

---

## Technical Implementation

### Full-Stack Architecture

NearYou was built as a full-stack application using Next.js and the App Router.

The application combines the user interface, server-side application logic, database operations, authentication, and external API integrations within a single architecture.

### Google Maps & Places Integration

NearYou integrates with the Google Maps and Places APIs to retrieve restaurant and location data based on the destination entered by the user.

Rather than centering the experience around the user's current location, the application uses the searched destination as the reference point for restaurant discovery.

This allows users to explore restaurants around places they plan to visit before physically arriving there.

### Database Design

PostgreSQL is used to persist user favorites, with Prisma providing type-safe database access.

Favorite records store the restaurant information required to render saved restaurants rather than depending entirely on external Google Places records.

A composite unique constraint using the authenticated user ID and restaurant ID prevents duplicate favorites from being created.

### Authentication

Clerk is used to provide authentication and associate saved restaurants with individual users.

Only authenticated users can maintain a persistent favorites list tied to their account.

### Optimistic UI Updates

The favorites system uses optimistic UI updates so that saving or removing a restaurant appears immediately to the user while the database operation is processed.

If the server-side operation fails, the application can reconcile the interface with the actual server state.

I implemented this behavior manually to better understand the update-and-reconciliation process rather than relying entirely on a built-in abstraction.

### Server-Side Operations

Database mutations are handled using Next.js server actions rather than separate API routes.

This allowed database operations to remain closely integrated with the App Router while keeping client-side components focused on interaction and presentation.

---

## What I Learned

NearYou was my first experience building a complete full-stack web application from the ground up.

The project gave me hands-on experience with the full development lifecycle, including:

- identifying a real user-experience problem
- designing an application around that problem
- making architectural decisions
- building reusable React components
- working with TypeScript
- integrating external APIs
- designing a relational database schema
- working with PostgreSQL and Prisma
- implementing user authentication
- managing client and server state
- debugging interactions across multiple parts of an application
- working with environment variables and API credentials
- deploying a production application
- maintaining and improving an existing codebase

More importantly, the project helped me understand how the individual technologies I had been learning fit together into a complete software system.

---

## Running NearYou Locally

### Prerequisites

You will need:

- Node.js
- A PostgreSQL database
- A Clerk account
- A Google Maps Platform API key with the necessary Maps and Places APIs enabled

### Installation

Clone the repository:

```bash
git clone https://github.com/erick-chung/near-you.git
cd near-you
```

Install dependencies:

```bash
npm install
```

Generate the Prisma client:

```bash
npx prisma generate
```

Start the development server:

```bash
npm run dev
```

Then open:

```text
http://localhost:3000
```

### Environment Variables

The application requires environment variables for:

- PostgreSQL database connection
- Clerk authentication
- Google Maps API access

Environment files containing API keys or credentials are intentionally excluded from this repository.

---

## Future Improvements

Potential features I would like to explore include:

- restaurant reviews and ratings
- shareable restaurant lists
- additional cuisine and price filters
- improved restaurant ranking and recommendation logic
- additional travel-time and transportation options

---

## Author

**Erick Chung**

[LinkedIn](https://linkedin.com/in/erick-chung)  
[GitHub](https://github.com/erick-chung)
