# Noise Event Logger

A timestamped log of loud-noise events, kept on your device and exportable as CSV or a printable report.

- **Problem source**: Bengaluru residents describing noise complaints dismissed for incomplete details: [r/bangalore thread](https://www.reddit.com/r/bangalore/comments/1xqrjez/).
- **Features**: microphone-based relative loudness monitoring with a learned room baseline, automatic event start/stop with timestamps and duration, manual entries, per-event notes, CSV export, print-friendly report, localStorage persistence.
- **Run it**: open `index.html` in a browser, or use the GitHub Pages site. Microphone access is requested only when you press Start.
- **Privacy and limits**: no audio is recorded or sent anywhere - only relative loudness numbers are computed in the browser. Phone microphones are not calibrated; levels are indicative, not measurements of any legal standard. The tool only keeps a personal record; it does not file complaints and makes no legal claims.
