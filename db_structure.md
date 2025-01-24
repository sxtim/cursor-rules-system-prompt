# Database Structure Documentation (Calendar App)

## Tables Overview

### users
- `id` (PRIMARY KEY, UUID)
- `email` (VARCHAR(255), UNIQUE, NOT NULL)
- `password_hash` (VARCHAR(255), NOT NULL)
- `name` (VARCHAR(100))
- `created_at` (TIMESTAMP, DEFAULT NOW())
- `updated_at` (TIMESTAMP)

### events
- `id` (PRIMARY KEY, UUID) 
- `user_id` (UUID, FOREIGN KEY -> users.id)
- `title` (VARCHAR(255), NOT NULL)
- `description` (TEXT)
- `start_time` (TIMESTAMP, NOT NULL)
- `end_time` (TIMESTAMP, NOT NULL)
- `location` (VARCHAR(255))
- `is_all_day` (BOOLEAN, DEFAULT false)
- `created_at` (TIMESTAMP, DEFAULT NOW())
- `updated_at` (TIMESTAMP)

### event_reminders
- `id` (PRIMARY KEY, UUID)
- `event_id` (UUID, FOREIGN KEY -> events.id)
- `reminder_time` (TIMESTAMP, NOT NULL)
- `reminder_type` (ENUM('email', 'push', 'sms'))
- `status` (ENUM('pending', 'sent', 'failed'))
- `created_at` (TIMESTAMP, DEFAULT NOW())

### event_recurrence
- `id` (PRIMARY KEY, UUID)
- `event_id` (UUID, FOREIGN KEY -> events.id)
- `recurrence_type` (ENUM('daily', 'weekly', 'monthly', 'yearly'))
- `interval` (INTEGER, DEFAULT 1)
- `ends_at` (TIMESTAMP)
- `created_at` (TIMESTAMP, DEFAULT NOW())

### event_attendees
- `id` (PRIMARY KEY, UUID)
- `event_id` (UUID, FOREIGN KEY -> events.id)
- `user_id` (UUID, FOREIGN KEY -> users.id)
- `status` (ENUM('pending', 'accepted', 'declined'))
- `created_at` (TIMESTAMP, DEFAULT NOW())
- `updated_at` (TIMESTAMP)

## Indexes
- users_email_idx ON users(email)
- events_user_id_idx ON events(user_id)
- events_start_time_idx ON events(start_time)
- event_reminders_event_id_idx ON event_reminders(event_id)
- event_recurrence_event_id_idx ON event_recurrence(event_id)
- event_attendees_event_id_idx ON event_attendees(event_id)
- event_attendees_user_id_idx ON event_attendees(user_id)

## Relationships
1. events -> users (Many-to-One)
   - An event belongs to one user (creator)
   - A user can have many events

2. event_reminders -> events (Many-to-One)
   - A reminder belongs to one event
   - An event can have multiple reminders

3. event_recurrence -> events (One-to-One)
   - A recurrence pattern belongs to one event
   - An event can have one recurrence pattern

4. event_attendees -> events (Many-to-One)
   - An attendee record belongs to one event
   - An event can have multiple attendees

5. event_attendees -> users (Many-to-One)
   - An attendee record belongs to one user
   - A user can be an attendee of multiple events

## Notes
- All timestamps are stored in UTC
- UUIDs are used instead of auto-incrementing IDs for better distribution and security
- Soft deletes are not implemented but could be added with a `deleted_at` column if needed
- The schema supports recurring events, reminders, and event sharing
- Indexes are added on frequently queried columns and foreign keys
