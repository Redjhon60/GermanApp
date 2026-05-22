# 🇩🇪 SnowB German AI — Complete Build Guide

## Prerequisites
- Node.js 18+
- npm or yarn
- Expo CLI + EAS CLI
- Android Studio (for local builds)
- A free Expo account at expo.dev

---

## 1. Project Setup

```bash
# Clone / enter project directory
cd snowb-german-ai

# Install dependencies
npm install

# Install Expo CLI globally
npm install -g @expo/cli eas-cli

# Login to Expo
eas login
```

---

## 2. Environment Variables

Create `.env` file:
```
EXPO_PUBLIC_ANTHROPIC_KEY=your_anthropic_api_key_here
EXPO_PUBLIC_FIREBASE_API_KEY=your_firebase_key_here
```

---

## 3. Download Required Fonts

Place these Nunito font files in `assets/fonts/`:
- `Nunito-Regular.ttf`
- `Nunito-SemiBold.ttf`
- `Nunito-Bold.ttf`
- `Nunito-ExtraBold.ttf`
- `Nunito-Black.ttf`

Download from: https://fonts.google.com/specimen/Nunito

---

## 4. Firebase Setup (Optional for full auth)

1. Create project at console.firebase.google.com
2. Add Android app with package: `com.snowb.germanlanguage`
3. Download `google-services.json` → place in project root
4. Enable Email/Password + Google authentication

---

## 5. Build APK — Method A: EAS Cloud Build (Recommended)

```bash
# Initialize EAS project
eas init

# Build preview APK (free tier available)
eas build --platform android --profile preview

# Build production APK
eas build --platform android --profile production-apk
```

The APK download link appears in your terminal and at expo.dev/accounts.

---

## 6. Build APK — Method B: Local Build

```bash
# Install Android SDK + set ANDROID_HOME
export ANDROID_HOME=$HOME/Android/Sdk

# Pre-build native code
npx expo prebuild --platform android

# Build debug APK
cd android && ./gradlew assembleDebug

# APK location:
# android/app/build/outputs/apk/debug/app-debug.apk
```

---

## 7. Build APK — Method C: Expo Go (Development)

```bash
# Start development server
npx expo start

# Press 'a' to open on Android emulator
# Or scan QR code with Expo Go app
```

---

## 8. Install APK on Device

```bash
# Via ADB
adb install android/app/build/outputs/apk/debug/app-debug.apk

# Or transfer APK file to phone and open it
# (Enable "Unknown Sources" in Android Settings → Security)
```

---

## App Architecture

```
snowb-german-ai/
├── App.tsx                    # Entry point
├── app.json                   # Expo config
├── eas.json                   # EAS build profiles
├── src/
│   ├── screens/
│   │   ├── AuthScreen.tsx     # Login / Signup / Google
│   │   ├── HomeScreen.tsx     # Dashboard, streak, XP
│   │   ├── CourseScreen.tsx   # A1→B2 lesson browser
│   │   ├── ConversationsScreen.tsx  # Dialogue topics
│   │   ├── DialogScreen.tsx   # Full dialogue with audio
│   │   ├── AITutorScreen.tsx  # AI chatbot (Claude API)
│   │   ├── QuizScreen.tsx     # Gamified quiz system
│   │   ├── VocabularyScreen.tsx # Word cards + TTS
│   │   ├── GrammarScreen.tsx  # Grammar rules + cases
│   │   └── ProgressScreen.tsx # Stats, skills, leaderboard
│   ├── navigation/
│   │   └── AppNavigator.tsx   # Bottom tabs + stack nav
│   ├── context/
│   │   └── store.ts           # Zustand global state
│   ├── services/
│   │   ├── firebase.ts        # Auth + Firestore
│   │   ├── aiService.ts       # Anthropic Claude API
│   │   ├── notifications.ts   # Push notifications
│   │   └── offlineStorage.ts  # Caching + downloads
│   ├── data/
│   │   └── germanData.ts      # Vocabulary, grammar, dialogues
│   └── utils/
│       └── theme.ts           # Colors, fonts, spacing
└── assets/
    ├── fonts/                 # Nunito font files
    └── images/                # Icons, splash, adaptive icon
```

---

## Features Implemented

| Feature | Status |
|---------|--------|
| ✅ Auth (Email + Google) | Complete |
| ✅ Home dashboard + streak | Complete |
| ✅ A1/A2/B1/B2 levels | Complete |
| ✅ Vocabulary (DE + FR + AR) | Complete |
| ✅ Grammar + exercises | Complete |
| ✅ 8 conversation scenarios | Complete |
| ✅ Dialogue with audio (TTS) | Complete |
| ✅ AI Tutor (Claude API) | Complete |
| ✅ Quiz system (MCQ + Fill) | Complete |
| ✅ XP + streak gamification | Complete |
| ✅ Progress + leaderboard | Complete |
| ✅ Dark mode | Complete |
| ✅ Offline storage | Complete |
| ✅ Push notifications | Complete |
| ✅ Animated UI | Complete |
| ✅ APK build ready | Complete |

---

## Publish to Google Play Store

```bash
# Build production bundle
eas build --platform android --profile production

# Submit to Play Store
eas submit --platform android
```

---

## Support
Built with React Native + Expo + Claude AI
