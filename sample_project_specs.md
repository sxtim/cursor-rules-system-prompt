# Calendar App Project Specifications

## Project Overview
A personal calendar application that allows users to manage events, set reminders, and share events with other users.

## Tech Stack
- **Frontend:**
  - HTML5
  - CSS3
  - JavaScript (Vanilla)
- **Backend:**
  - PHP 8.x
- **Database:**
  - MySQL/MariaDB

## Core Features

### 1. User Management
- User registration and authentication
- Profile management
- Password reset functionality

### 2. Event Management
- Create, read, update, and delete (CRUD) events
- Event properties:
  - Title and description
  - Start and end times
  - Location
  - All-day event option
- Event recurrence options:
  - Daily, weekly, monthly, yearly
  - Custom intervals
  - End date setting

### 3. Reminder System
- Multiple reminder types:
  - Email notifications
  - Push notifications
  - SMS alerts
- Customizable reminder timing
- Reminder status tracking

### 4. Event Sharing
- Invite other users to events
- Attendee status management (pending/accepted/declined)
- View shared events in personal calendar

## Project Structure

### Frontend Components
1. **Authentication Pages**
   - Login page
   - Registration page
   - Password reset page

2. **Calendar Views**
   - Monthly view (default)
   - Weekly view
   - Daily view
   - Agenda view

3. **Event Management**
   - Event creation/edit form
   - Event details modal
   - Recurrence pattern selector
   - Reminder configuration panel

4. **User Interface**
   - Responsive navigation
   - Calendar grid
   - Event cards
   - Settings panel

### Backend Components
1. **Authentication System**
   - User session management
   - Password hashing
   - Security middleware

2. **API Endpoints**
   - User management endpoints
   - Event CRUD endpoints
   - Reminder management endpoints
   - Attendee management endpoints

3. **Database Interactions**
   - PDO database connection
   - CRUD operations
   - Data validation
   - Query optimization

4. **Notification System**
   - Email service integration
   - Push notification service
   - SMS gateway integration

## Database Structure
- Follows the schema defined in `db_structure.md`
- Includes tables for:
  - users
  - events
  - event_reminders
  - event_recurrence
  - event_attendees

## Development Status

### Completed
- Database schema design
- Basic project structure

### In Progress
- User authentication system
- Basic calendar view
- Event CRUD operations

### Pending
- Reminder system implementation
- Event sharing functionality
- Notification system
- UI/UX improvements
- Mobile responsiveness
- Testing and debugging

## Development Guidelines
1. Follow PHP PSR-12 coding standards
2. Use prepared statements for database queries
3. Implement input validation and sanitization
4. Maintain responsive design principles
5. Document all API endpoints
6. Write clean, maintainable code
7. Implement proper error handling

## Security Considerations
1. HTTPS implementation
2. XSS prevention
3. CSRF protection
4. SQL injection prevention
5. Input validation
6. Secure password storage
7. Rate limiting
8. Session security

## Performance Optimization
1. Database query optimization
2. Asset minification
3. Caching implementation
4. Lazy loading of resources
5. Image optimization
6. API response optimization
