# Community Event Manager

## Project Description
The **Community Event Manager** is a web-based application designed to simplify the process of organizing, discovering, and managing local events. This platform provides event organizers with tools to create events, invite participants, and manage RSVPs, while attendees can discover events, RSVP, and interact with event organizers or other participants. 

The goal of this project is to improve event attendance, boost user engagement, and streamline the event organization process. The application leverages modern technologies, offering a seamless experience for both organizers and participants.

## Features

### 1. User Registration and Authentication
- Users can register with their email and password.
- Secure password hashing is used for credential storage.
- JWT tokens handle authentication and maintain sessions.

### 2. Event Management
- Organizers can create, update, and delete events.
- Events include details such as title, description, date, time, image, location, category, and RSVP limit.
- Event organizers can track attendance and adjust event details.

### 3. RSVP System
- Attendees can RSVP to events with a limited number of spots.
- Real-time tracking of available spots.
- Users can cancel RSVPs or update their attendance status.

### 4. Event Discovery
- Users can filter and search for events by location, date, and category (e.g., Tech, Sports, Arts).
- Events are displayed in both list and map formats for easier navigation.

### 5. Messaging System
- A direct messaging feature allows communication between attendees and event organizers.
- Attendees can ask questions or clarify event details.

### 6. Event Notifications
- Email notifications are sent for RSVPs, event updates, and reminders.
- Real-time notifications alert users about changes or cancellations for events they RSVP'd to.

## Technology Stack
### Backend
- **Node.js**
- **Express.js**
- **MongoDB**

### Frontend
- **HTML**
- **CSS**
- **JavaScript / React.js**

## Endpoints
### **User Authentication**
1. **User Registration**
   - **POST** `/api/auth/register`
   - Request Body: `{ email, password }`
   - Response: `{ success, token, user }`

2. **User Login**
   - **POST** `/api/auth/login`
   - Request Body: `{ email, password }`
   - Response: `{ success, token, user }`

3. **Get Current User**
   - **GET** `/api/auth/user`
   - Response: `{ user: { name, email, role } }`

### **Event Management**
4. **Create Event**
   - **POST** `/api/events`
   - Request Body: `{ title, description, date, time, location, bannerImage, category, maxRSVP }`
   - Response: `{ success, event }`

5. **Update Event**
   - **PUT** `/api/events/:eventId`
   - Request Body: `{ title, description, date, time, location, bannerImage, category, maxRSVP }`
   - Response: `{ success, updatedEvent }`

6. **Delete Event**
   - **DELETE** `/api/events/:eventId`
   - Response: `{ success }`

### **RSVP System**
7. **RSVP to Event**
   - **POST** `/api/events/:eventId/rsvp`
   - Request Body: `{ userId }`
   - Response: `{ success, rsvp }`

8. **Get RSVPs for an Event**
   - **GET** `/api/events/:eventId/rsvps`
   - Response: `{ success, attendees: [ { user1 }, { user2 } ] }`

9. **Cancel RSVP**
   - **DELETE** `/api/events/:eventId/rsvp/:userId`
   - Response: `{ success }`

### **Event Discovery**
10. **Get All Events**
    - **GET** `/api/events`
    - Query Params: `location, date, category`
    - Response: `{ success, events: [ { event1 }, { event2 } ... ] }`

11. **Get Event Details**
    - **GET** `/api/events/:eventId`
    - Response: `{ success, event }`

### **Notifications**
12. **Send Event Reminder**
    - **POST** `/api/notifications/reminder`
    - Request Body: `{ eventId, userId }`
    - Response: `{ success }`

13. **Notify RSVP Update**
    - **POST** `/api/notifications/rsvp-update`
    - Request Body: `{ eventId, message }`
    - Response: `{ success }`

### **Messaging System**
14. **Send Message**
    - Event: `sendMessage`
    - Message Data: `{ eventId, senderId, receiverId, message }`

15. **Receive Message**
    - Event: `receiveMessage`
    - Response: `{ eventId, senderId, message, timestamp }`

## How to Run the Project
1. Clone this repository:
   ```bash
   git clone <repository-url>
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Set up environment variables in a `.env` file:
   ```env
   CORS_ORIGIN=<frontend-url>
   CLOUDINARY_CLOUD_NAME=<your-cloudinary-cloud-name>
   CLOUDINARY_API_KEY=<your-cloudinary-api-key>
   CLOUDINARY_API_SECRET=<your-cloudinary-api-secret>
   JWT_SECRET=<your-jwt-secret>
   MONGO_URI=<your-mongodb-connection-string>
   ```

4. Start the server:
   ```bash
   npm start
   ```

5. Access the application at `http://localhost:<PORT>`.

## Contribution
Contributions are welcome! Feel free to open issues or submit pull requests to improve the project.

## License
This project is licensed under the MIT License. See the `LICENSE` file for details.
