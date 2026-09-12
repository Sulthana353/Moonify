# Moonify

> Every spherical light deserves to be the Moon.

Moonify is a deliberately useless computer-vision project that takes an ordinary photograph and replaces every suspiciously spherical light source with the exact same high-resolution Moon.

Streetlights? Moon.
Headlights? Moon.
Lamps? Moon.
Random glowing orb? Moon.

No astronomical accuracy. No reason. Just Moon.

## How It Works

```text
Upload Image
     ↓
Detect bright spherical objects
     ↓
Estimate their position and size
     ↓
Remove the background from the Moon image
     ↓
Resize the Moon to each detected object
     ↓
Replace them
     ↓
Moonified Image
```

Moonify uses browser-based computer vision to identify approximately circular bright regions in the uploaded image. It intentionally favors **false positives** because accurately identifying what is actually a Moon would defeat the entire purpose.

The same Moon is used for every detected object.

## Features

* Upload JPG, PNG, JPEG, or WebP images
* Automatic spherical-light detection
* Aggressive detection of potential Moon candidates
* Automatic Moon background removal
* Identical Moon replacement for every detected target
* Original vs. Moonified comparison
* Client-side image processing
* PNG export
* No image editing skills required
* Absolutely no astronomical usefulness

## Tech Stack

* **React**
* **TypeScript**
* **OpenCV.js**
* **HTML Canvas**
* **Vite**

Everything is processed locally in the browser where practical. Your photograph does not need to be uploaded to a backend for the computer-vision processing.

## The Algorithm

Moonify follows one fundamental principle:

```text
if (looksEvenSlightlySpherical && isBrightEnough) {
    replaceWithMoon();
}
```

More conventionally, the detection pipeline:

1. Convert the image to grayscale.
2. Identify bright regions.
3. Apply image processing to isolate candidate regions.
4. Find contours.
5. Calculate circularity and aspect ratio.
6. Keep sufficiently circular bright objects.
7. Determine each object's center and approximate diameter.
8. Composite the Moon over each target.

The detection threshold is intentionally permissive.

Precision is not the objective.

**Moon density is.**

## Example

### Before

A completely normal photograph containing several streetlights.

### After

The same photograph containing several Moons.

Nothing else has been improved.

## Why?

This project was created for a **Useless Projects Makeathon**.

The original concept was to replace a poorly photographed Moon with a high-quality lunar photograph. That was technically reasonable.

That was unacceptable.

Moonify instead asks:

> What if we replaced **every spherical light source** with the Moon?

The answer is Moonify.

## Running Locally

Clone the repository:

```bash
git clone <your-repository-url>
cd moonify
```

Install dependencies:

```bash
npm install
```

Start the development server:

```bash
npm run dev
```

Build for production:

```bash
npm run build
```

Preview the production build:

```bash
npm run preview
```

## Project Structure

```text
moonify/
├── src/
│   ├── components/
│   │   ├── Upload.tsx
│   │   └── ImageComparison.tsx
│   │
│   ├── cv/
│   │   ├── detectSpheres.ts
│   │   ├── extractMoon.ts
│   │   └── moonify.ts
│   │
│   ├── assets/
│   │   └── moon.jpg
│   │
│   └── App.tsx
│
├── public/
├── package.json
└── README.md
```

## Limitations

Moonify does not understand what an object actually is.

It doesn't know the difference between:

* the Moon
* a streetlamp
* a light bulb
* a headlight
* a Christmas ornament
* a suspiciously bright circle

This is intentional.

It may therefore produce results that are technically incorrect, visually absurd, and completely useless.

**This is a feature.**

