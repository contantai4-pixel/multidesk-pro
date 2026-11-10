# MultiDesk PRO V1.1 — বাংলা নির্দেশিকা

## এই ZIP-এ কী আছে
- Responsive Web App / PWA source
- Profile add, select, search, delete
- JSON backup ও restore
- Capacitor Android configuration
- GitHub Actions workflow: push বা manual run করলে debug APK build করে artifact হিসেবে প্রকাশ করবে

## নিরাপত্তা ও সীমাবদ্ধতা
MultiDesk শুধু profile label ও note local browser storage-এ রাখে। Facebook password, 2FA code, `c_user`, `xs` বা অন্য session cookie চাইবে না এবং সংরক্ষণ করবে না। Facebook-এ লগইন শুধু facebook.com-এ নিজে করবেন।

এই সংস্করণে প্রতিটি profile-এর পৃথক isolated Facebook browser session নেই। একই browser/WebView-তে খোলা profile-গুলো একই login state ব্যবহার করতে পারে। তাই আলাদা session-এর প্রতিশ্রুতি দেওয়া হচ্ছে না। এটি Meta/Facebook-এর অফিসিয়াল অ্যাপ নয়।

## GitHub-এ আপলোড — ফোন বা কম্পিউটার
1. GitHub-এ সাইন ইন করুন।
2. `+` → **New repository** নির্বাচন করুন।
3. Repository name দিন `multidesk-pro` এবং **Public** বা **Private** বেছে Create repository করুন।
4. এই ZIP extract করে ভেতরের সব ফাইল ও `.github` ফোল্ডার repository-র root-এ upload করুন। `.github/workflows/android-apk.yml` ফাইলটি যেন ঠিক ওই path-এ থাকে।
5. GitHub repository-র **Actions** tab খুলুন।
6. `Build MultiDesk PRO APK` workflow নির্বাচন করে **Run workflow** চাপুন। `main` branch-এ push করলেও build চলবে।
7. Build শেষ হলে workflow run-এর পেজের **Artifacts** অংশ থেকে `MultiDesk-PRO-debug` ডাউনলোড করুন।
8. ZIP artifact extract করে `app-debug.apk` Android ফোনে নিন এবং ইনস্টল করুন। Android চাইলে browser/files app-এর জন্য install permission দিন। শুধু নিজের তৈরি APK ইনস্টল করুন।

## Web App প্রকাশ
GitHub repository-তে **Settings → Pages** খুলে Deploy from a branch নির্বাচন করুন, `main` এবং `/ (root)` সেট করে Save করুন। কয়েক মিনিট পরে Pages URL-এ app দেখা যাবে। HTTPS URL-এ Chrome থেকে Add to Home screen করা যাবে।

## চাইলে নিজের কম্পিউটারে build
Node.js 22 এবং Android Studio/SDK ইনস্টল করে:
```bash
npm install
npm run build
npx cap add android
npx cap sync android
```
তারপর Android Studio-তে `android/` folder খুলে APK build করুন।

## গুরুত্বপূর্ণ
- Debug APK পরীক্ষা করার জন্য; Play Store-এ প্রকাশের জন্য release signing দরকার।
- GitHub Actions build failure হলে Actions log-এর error দেখুন।
- GitHub password, access token, signing key বা Facebook credentials কাউকে দেবেন না।
