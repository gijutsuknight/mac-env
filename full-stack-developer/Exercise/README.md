# Full-Stack Developer Exercises

Combine frontend and backend exercises, then run one full-stack verification.

---

## 1. Complete role-specific exercises

- Do the tasks in [frontend-developer/Exercise/](../frontend-developer/Exercise/) (Node switch, Java switch, package managers, optional Android/iOS).
- Do the tasks in [backend-developer/Exercise/](../backend-developer/Exercise/) (Python switch, Spring Boot run).

---

## 2. Full-stack verification (backend + frontend)

Prove that both stacks work together and that version switching affects the right runtime.

1. **Backend:** Start a minimal API (choose one):
   - **Spring Boot:** From [start.spring.io](https://start.spring.io), create a project with "Web", run `./mvnw spring-boot:run`. Ensure an endpoint is available (e.g. http://localhost:8080).
   - **Python/Flask:** `pip install flask`, create a small app that serves e.g. `GET /api/hello` → `{"message":"hello"}` and run it (e.g. port 5000).

2. **Frontend:** Create a minimal React app that calls the backend:
   ```bash
   npx create-react-app fullstack-test
   cd fullstack-test
   ```
   In the app, add a `useEffect` or button that fetches your backend URL (e.g. `http://localhost:8080/...` or `http://localhost:5000/api/hello`) and displays the response.

3. **Version switch check:**
   - Switch Node (e.g. `nvm use 18` then `nvm use 20`), restart the React dev server, and confirm the app still runs and reaches the backend.
   - Switch Python or Java, restart the backend, and confirm the frontend still gets a response.

Success: both backend and frontend run; switching Node or Python/Java and restarting the corresponding server shows the right runtime version and the full-stack flow still works.
