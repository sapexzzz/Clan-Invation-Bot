# CHANGELOG

## [1.2.0] — 2026-03-20

### Added
- `🚫 Block` button in group ticket messages
- `admin_block:{app_id}` handler: checks permissions, blocks a user, rejects a ticket, notifies the user
- `is_blocked` column in the `users` table (with automatic migration for existing databases)
- `database.py` functions: `block_user`, `unblock_user`, `is_user_blocked`, `get_all_users_stats`
- Check for blocking when clicking "Submit ticket" (`start.py`)
- **`clanpanel.py`** — terminal control panel: user list, block/unblock by TG ID, viewing tickets with a status filter
- Automatic database migration when `clanpanel.py` starts (adds `is_blocked` to old databases without data loss)

---

## [1.1.0] — 2026-03-20

### Added
- README in Russian (`README.ru.md`) and English (`README.en.md`)
- Brief description for GitHub (`github-description.txt`)

---

## [1.0.0] — 2026-03-20

### Initial release

#### Functionality
- FSM request submission scenario: game ID, nickname, ranks (Competitive / Allies / Duels), hours, KD
- Automatic rejection for KD < 1.0 / > 10 or hours < 50 (`rejected_auto` status)
- Request confirmation with inline editing menu for any field
- Anti-spam: not more often 1 request per 10 minutes
- Resubmission block if there is an active request (`pending`)
- Sending a request to a Telegram group with `✅ Accept` / `❌ Reject` buttons
- Permissions check via `getChatMember` before each action
- Upon acceptance, a one-time invite link is generated (24 hours, 1 use)
- Support for forum groups with topics (`TOPIC_ID`)
- Data storage in SQLite via `aiosqlite`
- Loading configuration from `.env` (`BOT_TOKEN`, `GROUP_ID`, `TOPIC_ID`)

#### Stack
- Python 3.11+, aiogram 3.x, aiosqlite, python-dotenv, rich
