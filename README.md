# Daily Journal Book

A beautiful, feature-rich personal journaling application built with Flutter and Supabase. Designed for normal users only - no admin, worker, or role-based functionality.

## Features

### Core Journaling
- ✅ Create, edit, delete journal entries
- ✅ Morning, Evening, and Anytime journal types
- ✅ Rich text content with titles
- ✅ Mood tracking with 14 moods and intensity (1-10)
- ✅ Gratitude journaling
- ✅ Daily reflections and goals
- ✅ Custom tags with colors
- ✅ Favorite and pin important entries
- ✅ Multiple photos per entry with captions

### Personal Features
- ✅ Daily prompts (rotating based on date)
- ✅ Daily inspirational quotes
- ✅ Writing streaks (current, longest, total days)
- ✅ 18 achievements to unlock
- ✅ "On This Day" memories from previous years
- ✅ Memory timeline (chronological view)
- ✅ Photo gallery with full-screen viewer

### Statistics & Insights
- ✅ Calendar heatmap (GitHub-style)
- ✅ Mood distribution charts
- ✅ Mood trend analysis
- ✅ Monthly writing activity
- ✅ Day of week patterns
- ✅ Morning vs Evening distribution
- ✅ Most used tags

### Security & Privacy
- ✅ App lock with PIN (4-6 digits)
- ✅ Biometric authentication (fingerprint/face ID)
- ✅ Supabase Row Level Security (RLS)
- ✅ User data isolation
- ✅ Secure image storage
- ✅ Delete account & data

### Customization
- ✅ Light, Dark, and System themes
- ✅ 6 journal themes (Classic, Notebook, Minimal, Nature, Sunset, Ocean)
- ✅ Adjustable font size
- ✅ Default mood and journal type preferences
- ✅ Custom profile with avatar

### Export & Sharing
- ✅ Export as PDF (single entry, date range, all)
- ✅ Export as text file
- ✅ Share exported files
- ✅ Trash/Recently deleted with restore

### Notifications
- ✅ Daily journal reminder
- ✅ Configurable reminder time
- ✅ Local notifications (no server needed)

## Tech Stack

- **Frontend**: Flutter 3.3+, Dart 3+
- **Backend**: Supabase (PostgreSQL, Auth, Storage)
- **State Management**: Provider
- **Local Storage**: SharedPreferences
- **Notifications**: flutter_local_notifications
- **PDF Generation**: pdf + printing
- **Images**: cached_network_image, image_picker
- **Biometrics**: local_auth

## Project Structure

```
daily_journal/
├── lib/
│   ├── main.dart                 # App entry point
│   ├── app.dart                  # App configuration & routing
│   ├── config/
│   │   └── app_config.dart       # App constants & Supabase config
│   ├── models/
│   │   └── journal_entry.dart    # All data models
│   ├── services/
│   │   ├── auth_service.dart     # Supabase Auth
│   │   ├── journal_service.dart  # Journal CRUD & queries
│   │   ├── storage_service.dart  # Supabase Storage
│   │   ├── notification_service.dart # Local notifications
│   │   ├── export_service.dart   # PDF/Text export
│   │   └── profile_service.dart  # User profile
│   ├── controllers/
│   │   ├── journal_controller.dart
│   │   ├── theme_controller.dart
│   │   └── app_lock_controller.dart
│   ├── screens/
│   │   ├── auth/
│   │   │   ├── login_screen.dart
│   │   │   ├── register_screen.dart
│   │   │   ├── forgot_password_screen.dart
│   │   │   └── reset_password_screen.dart
│   │   ├── home_screen.dart
│   │   ├── add_journal_screen.dart
│   │   ├── edit_journal_screen.dart
│   │   ├── journal_detail_screen.dart
│   │   ├── calendar_screen.dart
│   │   ├── statistics_screen.dart
│   │   ├── mood_insights_screen.dart
│   │   ├── favorites_screen.dart
│   │   ├── memory_gallery_screen.dart
│   │   ├── timeline_screen.dart
│   │   ├── on_this_day_screen.dart
│   │   ├── achievements_screen.dart
│   │   ├── reflection_screen.dart
│   │   ├── profile_screen.dart
│   │   ├── settings_screen.dart
│   │   ├── app_lock_screen.dart
│   │   ├── trash_screen.dart
│   │   └── search_screen.dart
│   ├── widgets/
│   │   ├── app_logo.dart
│   │   ├── journal_card.dart
│   │   ├── mood_selector.dart
│   │   ├── mood_chart.dart
│   │   ├── streak_card.dart
│   │   ├── achievement_card.dart
│   │   ├── daily_prompt_card.dart
│   │   ├── gratitude_card.dart
│   │   ├── memory_card.dart
│   │   ├── empty_journal.dart
│   │   ├── loading_widget.dart
│   │   └── error_widget.dart
│   ├── theme/
│   │   └── app_theme.dart
│   └── utils/
│       ├── validators.dart
│       ├── date_utils.dart
│       ├── mood_utils.dart
│       └── constants.dart
├── supabase/
│   └── database.sql              # Complete database schema
├── assets/
│   ├── images/
│   ├── icons/
│   └── quotes/
├── pubspec.yaml
└── README.md
```

## Setup Instructions

### 1. Prerequisites
- Flutter SDK 3.3.0 or higher
- Dart SDK 3.0 or higher
- Android Studio / VS Code
- Supabase account (free tier)

### 2. Clone and Install
```bash
git clone <repository-url>
cd daily_journal
flutter pub get
```

### 3. Create Supabase Project
1. Go to [supabase.com](https://supabase.com) and create a new project
2. Wait for database to be ready
3. Go to Settings → API to get your:
   - Project URL
   - Anon/Public key

### 4. Configure Supabase
1. Open `supabase/database.sql` in Supabase SQL Editor
2. Run the entire script (creates tables, RLS, functions, triggers)
3. Go to Storage → Create two buckets:
   - `journal_images` (private)
   - `avatars` (private)
4. Apply storage policies (see comments in database.sql)

### 5. Configure App
Edit `lib/config/app_config.dart`:
```dart
static const String supabaseUrl = 'YOUR_SUPABASE_URL';
static const String supabaseAnonKey = 'YOUR_ANON_KEY';
```

### 6. Run the App
```bash
flutter run
```

## Supabase Database Verification

After running the app, verify data in Supabase Dashboard:

### Authentication
```
Supabase Dashboard → Authentication → Users
```

### Profiles
```
Table Editor → profiles
```

### Journal Entries
```
Table Editor → journal_entries
```

### Memory Images
```
Table Editor → memory_images
```

### Storage
```
Storage → journal_images (user folders)
Storage → avatars (user folders)
```

## Building APK

```bash
# Debug APK
flutter build apk --debug

# Release APK
flutter build apk --release

# App Bundle (for Play Store)
flutter build appbundle --release
```

## Testing

```bash
# Run unit/widget tests
flutter test

# Run with coverage
flutter test --coverage

# Analyze code
flutter analyze
```

## Troubleshooting

### Common Issues

**1. Supabase Connection Failed**
- Verify URL and anon key in `app_config.dart`
- Check Supabase project is not paused
- Ensure network connectivity

**2. Authentication Not Working**
- Check email confirmation settings in Supabase Auth
- Verify RLS policies are enabled
- Check browser/device storage permissions

**3. Images Not Uploading**
- Verify storage buckets exist (`journal_images`, `avatars`)
- Check storage policies allow user uploads
- Ensure file size < 5MB

**4. Notifications Not Showing**
- Grant notification permission on device
- Check `flutter_local_notifications` setup
- Verify timezone configuration

**5. Build Errors**
```bash
flutter clean
flutter pub get
flutter build apk --debug
```

**6. RLS Policy Errors**
- Ensure user is authenticated before queries
- Check policies match table structure
- Verify `auth.uid()` is used correctly

### Performance Tips
- Use pagination for large journal lists
- Enable image caching with `cached_network_image`
- Compress images before upload (already implemented)
- Use database indexes (included in schema)

## Architecture Notes

### Clean Architecture
- **Models**: Pure Dart classes with JSON serialization
- **Services**: Business logic, Supabase communication
- **Controllers**: State management with Provider
- **Screens**: UI components, minimal logic
- **Widgets**: Reusable UI components
- **Utils**: Helper functions, constants

### Security
- All database queries filtered by `auth.uid() = user_id`
- Storage paths prefixed with user ID
- No service role keys in client
- PINs stored as simple hashes (use proper crypto in production)

### Offline Support
- Basic cached reads implemented
- Pending writes queued for sync
- Clear offline indicators

## Contributing

1. Fork the repository
2. Create feature branch
3. Make changes
4. Run tests and analyze
5. Submit pull request

## License

MIT License - feel free to use for personal or commercial projects.

## Support

For issues, please check:
1. Supabase logs (Dashboard → Logs)
2. Flutter debug console
3. Device logs (`adb logcat`)

## Roadmap

- [ ] Cloud sync across devices
- [ ] Rich text editor (bold, italic, lists)
- [ ] Voice-to-text journaling
- [ ] Backup/restore to Google Drive/iCloud
- [ ] Widget for home screen
- [ ] Apple Watch / Wear OS companion
- [ ] AI-powered insights (local only)
- [ ] Habit tracker integration