# Real or AI? 🎄: Christmas party game

Everyone scans a QR code and sees the same picture or video on their own phone. They guess **AI** or **Real**, you reveal the answer, and a leaderboard tracks the scores. You run the whole game from your phone.

**Scoring:** 100 points for a correct guess, plus a speed bonus of up to 50 points for answering quickly (it drops to 0 after 20 seconds). Players can change their guess any time before you reveal the answer.

---

## 1. Add your pictures and videos

1. Put your files in the `media` folder. Simple names work best, like `01.jpg`, `02.mp4` and so on.
2. Open `items.js` in any text editor and add one line for each file:
   ```js
   { file: "media/04.jpg", answer: "real", note: "Optional text shown at the reveal" },
   ```
   `answer` must be `"ai"` or `"real"`. Items play in the order they're listed.
3. Delete the three example lines that point to files you don't have.

**Media tips**
- Keep videos **under 15 seconds and under about 10 MB**. Twenty phones loading big files on restaurant wifi will lag. A free tool like HandBrake (its "Fast 720p" preset) makes them small.
- Use .mp4 for video. It plays on both iPhone and Android.
- Videos start muted and loop. Each player can tap the sound button if they want audio.
- Good sources: AI images from Midjourney, ChatGPT or Gemini, and AI video from Sora, Veo or Kling. For real photos, use your own or free sites like Unsplash and Pexels. Tricky real photos that *look* fake make the best rounds.

## 2. Put it online with GitHub Pages (free, about 5 minutes)

1. Go to github.com and sign in. Click **+ → New repository**, name it something like `xmas-game`, make it **Public**, and click **Create**.
2. Click **"uploading an existing file"**. Drag in `index.html`, `items.js` and the whole `media` folder, then click **Commit changes**.
3. Go to **Settings → Pages**. Under *Branch*, choose `main`, keep the folder as `/ (root)`, and click **Save**.
4. After about a minute, your game is live at `https://<your-username>.github.io/xmas-game/`.

To change items later, edit `items.js` on GitHub or upload new media. The live site updates within a minute.

> Note: a public repo means anyone with the link can see the media and the answers in `items.js`. Nobody will go looking for it, but don't give the link out before the party.

## 3. Run the game

1. On your phone, open `https://<your-username>.github.io/xmas-game/?host`. You'll see a QR code.
2. **Turn off auto-lock on your phone** (iPhone: Settings → Display & Brightness → Auto-Lock → Never). Your phone is the game server, so if it sleeps, players drop off. They reconnect on their own once your screen is back on.
3. Players scan the QR code, type their name and tap **Join**. You'll see each name appear.
4. Tap **Start game**. For each item:
   - Players vote. You see who has voted, and you can tap to peek at the answer.
   - Tap **Reveal answer**. Every phone shows the answer, whether that player was right, their points and their rank.
   - Tap **Leaderboard** (optional) or **Next item →**.
5. After the last item, tap **Final results 🏆**.

Late arrivals: tap **Show join QR** at any point during the game. They join with 0 points.

## Do a test run first

Open the `?host` link on your laptop and scan the QR code with your phone, or open the link in a second browser tab. Play through a couple of items. It takes two minutes and confirms your media loads.

## If something goes wrong

| Problem | Fix |
|---|---|
| A player is stuck on "Connecting…" | Have them refresh. If it still fails, ask them to switch between wifi and mobile data. |
| Your host page refreshed by accident | Just reopen the `?host` link. The game, scores and QR code are saved, and players reconnect on their own. |
| "Game ID busy" | You have the host page open in two tabs. Close one. |
| You want a completely fresh game | Tap **Reset everything** at the bottom of the host screen. This makes a new QR code. |
| A picture doesn't show up | Check that the filename in `items.js` matches the file exactly, including capital letters. |

**How it works:** the page connects your phone directly to each player's phone using PeerJS, a free connection service, so there's no server or account to set up. It needs internet on every phone.
