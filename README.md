# Social Media in Django

A multi-app social media / blogging platform built with **Django**. Users can sign up, create posts, like and comment on them, follow other users, and send each other direct messages through a built-in chat system.

## Features

**Accounts**
- Sign up, log in, and log out
- Change password
- Edit profile (with a status field via a one-to-one `Profile` model)
- Public profile pages, including a read-only "anonymous" view for visitors who aren't following the user

**Blog / Posts**
- Create, edit, and delete posts
- Like / unlike posts
- Comment on posts
- Post detail view with its comment thread
- Home feed showing posts only from users you follow
- "All posts" view showing every post on the platform

**Follow system**
- Follow / unfollow other users
- View a user's followers and following lists
- Follower / following counts on each profile

**Chat**
- Direct messaging between users
- Conversation list showing your most recent chats
- Search for users to start a new conversation

## Tech Stack

- **Backend:** Django 3.1
- **Database:** SQLite (default, via `db.sqlite3`)
- **Forms/UI:** `django-crispy-forms`
- **Frontend:** Django templates + Bootstrap 5

## Project Structure

The project is split into three Django apps, wired together in the `theblog` project:

```
theblog/          # Project settings and root URL configuration
account/          # Signup, login, logout
blog/             # Posts, comments, likes, profiles, follow/following
chat/             # Direct messages between users
manage.py
db.sqlite3
```

Key models:

| App  | Model        | Purpose                                             |
|------|--------------|------------------------------------------------------|
| blog | `Profile`    | Extra profile info (status) linked to a `User`       |
| blog | `Post`       | A blog/social post with a title, description, likes  |
| blog | `Comment`    | A comment on a `Post`                                |
| blog | `Follower`   | Tracks who follows a given user                      |
| blog | `Following`  | Tracks who a given user follows                      |
| chat | `Message`    | A direct message between a sender and a recipient    |

## Getting Started

### Prerequisites
- Python 3.8+
- pip

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/Tanish3701/Social-media-in-Django.git
   cd Social-media-in-Django
   ```

2. Create and activate a virtual environment:
   ```bash
   python -m venv venv
   source venv/bin/activate      # On Windows: venv\Scripts\activate
   ```

3. Install dependencies:
   ```bash
   pip install django django-crispy-forms
   ```

4. Apply migrations:
   ```bash
   python manage.py migrate
   ```

5. (Optional) Create an admin user:
   ```bash
   python manage.py createsuperuser
   ```

6. Run the development server:
   ```bash
   python manage.py runserver
   ```

7. Open your browser at [http://127.0.0.1:8000/](http://127.0.0.1:8000/)

## Usage

- Visit `/` to sign up or log in.
- Once logged in, visit `/blog/` for your following feed, or `/blog/homeAll/` to see all posts.
- Visit `/blog/profile/<username>` to view a profile, edit your own, or follow/unfollow others.
- Visit `/chat/` to see your conversations, or `/chat/searchUser/` to find someone to message.

## Notes

- `DEBUG = True` and the `SECRET_KEY` are currently hardcoded in `theblog/settings.py` for local development — replace both with environment-based configuration before deploying anywhere public.
- There is no `requirements.txt` in the repository yet; the dependencies above (`django`, `django-crispy-forms`) are inferred from `INSTALLED_APPS` and the imports used in the code.

## License

No license file is currently included in this repository.
