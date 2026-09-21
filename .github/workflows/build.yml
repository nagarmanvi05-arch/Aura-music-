name: Build APK
on: [push]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Unzip
        run: |
          FILE=$(ls | grep -i aura | head -n 1)
          unzip -o "$FILE"
          FOLDER=$(ls -d */ | head -n 1)
          cp -r $FOLDER*. || true
          cp -r $FOLDER.*. 2>/dev/null || true
      - uses: actions/setup-java@v4
        with:
          java-version: '17'
          distribution: 'temurin'
      - uses: gradle/actions/setup-gradle@v3
      - run: chmod +x gradlew
      - run:./gradlew assembleDebug
      - uses: actions/upload-artifact@v4
        with:
          name: AURA-APK
          path: app/build/outputs/apk/debug/app-debug.apk
