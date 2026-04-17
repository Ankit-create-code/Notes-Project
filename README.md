<div align="center">

# NoteKeep

**A full-stack MERN notes application with rate limiting and clean REST API**

[![React](https://img.shields.io/badge/React-19-61DAFB?style=for-the-badge&logo=react&logoColor=black)](https://react.dev)
[![Node.js](https://img.shields.io/badge/Node.js-Express-339933?style=for-the-badge&logo=nodedotjs&logoColor=white)](https://nodejs.org)
[![MongoDB](https://img.shields.io/badge/MongoDB-Mongoose-47A248?style=for-the-badge&logo=mongodb&logoColor=white)](https://mongodb.com)
[![Deployed on AWS](https://img.shields.io/badge/AWS-Elastic%20Beanstalk-FF9900?style=for-the-badge&logo=amazonaws&logoColor=white)](https://aws.amazon.com/elasticbeanstalk)

[Live Demo](http://notekeep-env.eba-ckzggpdw.ap-south-1.elasticbeanstalk.com)  | [Report Bug](https://github.com/Ankit-create-code/Notes-Project/issues)

</div>

---

## Features

- Create & Edit Notes - Add a title and content, edit inline
- Delete Notes - With confirmation prompt to prevent accidents
- Rate Limiting - Upstash Redis sliding-window limiter (100 req/min) with a friendly UI fallback
- Responsive Design - Mobile-first grid layout via Tailwind CSS + DaisyUI
- Production-Ready - Express serves the built React frontend in production

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| **Frontend** | React 19, Vite 7, Tailwind CSS, DaisyUI |
| **Backend** | Node.js, Express 5 |
| **Database** | MongoDB Atlas (Mongoose ODM) |
| **Rate Limiting** | Upstash Redis (sliding window) |
| **Deployment** | AWS Elastic Beanstalk |

---

## Project Structure

```
Notes-Project/
Notes-Project/
  backend/
      src/
            config/         # DB & Upstash Redis setup
                  controllers/    # CRUD logic (notesController.js)
                        middleware/      # Rate limiter
                              models/          # Mongoose Note schema
                                    routes/          # Express router
                                          server.js        # App entry point
                                            frontend/
                                                src/
                                                      components/     # Navbar, NoteCard, RateLimitedUI, etc.
                                                            lib/             # Axios instance, utils
                                                                  pages/           # HomePage, CreatePage, NoteDetailPage
                                                                    package.json             # Root scripts (build + start)
                                                                    ```

                                                                    ---

                                                                    ## Getting Started

                                                                    ### Prerequisites

                                                                    - Node.js >= 18
                                                                    - A [MongoDB Atlas](https://cloud.mongodb.com) cluster
                                                                    - An [Upstash Redis](https://upstash.com) database

                                                                    ### 1. Clone the repo

                                                                    ```bash
                                                                    git clone https://github.com/Ankit-create-code/Notes-Project.git
                                                                    cd Notes-Project
                                                                    ```

                                                                    ### 2. Configure environment variables

                                                                    Create `backend/.env`:

                                                                    ```env
                                                                    MONGO_URI=your_mongodb_connection_string
                                                                    PORT=5001
                                                                    UPSTASH_REDIS_REST_URL=your_upstash_url
                                                                    UPSTASH_REDIS_REST_TOKEN=your_upstash_token
                                                                    NODE_ENV=development
                                                                    ```
                                                                    ```

                                                                    ### 3. Install & run in development

                                                                    ```bash
                                                                    # Install backend dependencies
                                                                    cd backend && npm install

                                                                    # Install frontend dependencies
                                                                    cd ../frontend && npm install

                                                                    # Run backend (from /backend)
                                                                    npm run dev

                                                                    # Run frontend in a separate terminal (from /frontend)
                                                                    npm run dev
                                                                    ```

                                                                    Frontend -> `http://localhost:5173`
                                                                    Backend API -> `http://localhost:5001/api`

                                                                    ---

                                                                    ## API Endpoints

                                                                    Base URL: `/api/notes`

                                                                    | Method | Endpoint | Description |
                                                                    |--------|----------|-------------|
                                                                    | `GET` | `/` | Get all notes (newest first) |
                                                                    | `GET` | `/:id` | Get a single note by ID |
                                                                    | `POST` | `/` | Create a new note |
                                                                    | `PUT` | `/:id` | Update a note |
                                                                    | `DELETE` | `/:id` | Delete a note |

                                                                    ---

                                                                    ## Deployment (AWS Elastic Beanstalk)

                                                                    ```bash
                                                                    # Build the frontend and wire it into the backend
                                                                    npm run build

                                                                    # The backend serves the built frontend from ../frontend/dist in production
                                                                    npm start
                                                                    ```

                                                                    ---

                                                                    ## Challenges & Learnings

                                                                    - IAM Role Configuration - Setting up the correct instance profile and service role for EB took iteration
                                                                    - API Base URL - Used `import.meta.env.MODE` to dynamically switch between dev and production base URLs
                                                                    - Deployment Structure - Learned how EB expects the `package.json` start script to work with a monorepo layout

                                                                    ---

                                                                    ## License

                                                                    MIT - feel free to fork and build on this.

                                                                    ---

                                                                    <div align="center">
                                                                    Made with Coffee by [Ankit](https://github.com/Ankit-create-code)
                                                                    </div>

                                                                    </div>
