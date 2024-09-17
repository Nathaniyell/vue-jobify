
# Vue Jobify

This is a job search platform built with Vue.js that allows users to create, view, update and delete job postings. The platform utilizes the Vue Composition API, routing for navigation and a JSON Server for backend data storage and retrieval.

## Features

- **CRUD Operations:** Users can perform Create, Read, Update, and Delete operations on job listings.
- **Vue Composition API:** Modern API for better component composition and reusability.
- **Vue Router:** Handles navigation between different pages (e.g., Job Listings, Job Details, Add/Edit/Delete Job).
- **JSON Server:** Simulates a backend database to store and manage job postings as JSON data.
- **Responsive Design:** The platform is optimized for mobile and desktop viewing.
- **Pagination:** Allows browsing through large datasets of job listings in manageable chunks.
- **Form Validation:** Ensures that all required fields in job forms are filled out correctly before submission.
  
## Tech Stack

- **Vue 3:** Frontend framework used to build the application.
- **Vue Composition API:** Used for component logic and managing state.
- **Vue Router:** For handling routing between different views.
- **JSON Server:** Provides a mock backend to handle RESTful CRUD operations.
- **FetchAPI:** Used for making HTTP requests to interact with the JSON Server.
- **TailwindCSS:** Styling for the application.

## Getting Started

### Prerequisites

- **Node.js** (v14 or above)
- **npm** or **yarn**

### Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/Nathaniyell/vue-jobify.git
   ```

2. Navigate to the project directory:

   ```bash
   cd vue-jobify
   ```

3. Install dependencies:

   ```bash
   npm install
   ```

4. Run the Vue development server:

   ```bash
   npm run serve
   ```

6. Open your browser and go to `http://localhost:8080` to view the application.

### File Structure

```bash
├── public/
│   └── index.html          # Main HTML file
├── src/
│   ├── assets/             # Static assets (images, etc.)
│   ├── components/         # Vue components
│   ├── views/              # Pages for different views
│   ├── router/             # Vue Router configuration
│   ├── services/           # API services to interact with JSON Server
│   ├── App.vue             # Root component
│   └── main.js             # Application entry point
├── jobs2.json              # Mock data for JSON Server
└── package.json            # Project dependencies and scripts
```

### Available Scripts

- `npm run serve`: Starts the development server.
- `npm run build`: Builds the application for production.
- `npm run lint`: Runs the linter to check for code style issues.

### Routes

The application consists of the following main routes:

- `/`: Home page, listing all available jobs.
- `/jobs`:  Jobs details page, showing information about all the jobs
- `/jobs/:id`: Job details page, showing information about a specific job.
- `/jobs/add`: Add new job posting.
- `/jobs/edit/:id`: Edit an existing job posting.



### Future Improvements

- User authentication (Login/Signup)
- Job application tracking system
- Enhanced job filtering options (e.g., salary range, experience level)

### License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more information.
