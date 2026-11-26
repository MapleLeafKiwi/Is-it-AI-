# LED in Action Christmas Dinner: Real or AI? 🎄

Everyone scans a QR code, picks a name, and sees the same picture or video on their own phone at the same time. They guess **AI** or **Real**, you reveal the answer to everyone at once, and a leaderboard tracks the scores. You run the game from your phone.

**Scoring:** 100 points for a correct guess, plus a speed bonus of up to 50 points for answering quickly. The bonus drops to 0 after 20 seconds. Players can change their guess any time before you reveal the answer.

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

1. On your phone, open `https://mapleleafkiwi.github.io/Is-it-AI-/?host`. You'll see a QR code.
2. **Turn off auto-lock on your phone.** Your phone runs the game, so if it sleeps, players drop off. They reconnect on their own once your screen is back on.
3. Players scan, type their name and tap **Join**. Tap **Start game** when everyone's in.
4. For each item:
   - You'll see **⏳ Waiting on …** with the names of anyone still deciding. When everyone has answered, it switches to **✅ Everyone has answered!** and the Reveal button turns green.
   - If someone's distracted or stuck, tap **Reveal now (skip N still deciding)**. Anyone who didn't answer gets 0 for that item.
   - Faded names are phones that have disconnected. The game doesn't wait for them.
   - After the reveal, every phone shows the answer, how the table split, and a top-5 leaderboard. Tap **Next item →** when you're ready. You can take as long as you like between items, such as between courses.
5. After the last item, tap **Final results 🏆**. Everyone sees the podium, how many they got right, how often AI fooled them, and the item that fooled the most people.

## Do a test run first

Open the `?host` link on your laptop and scan the QR code with your phone, or open the link in a second browser tab. Play through a couple of items. It takes two minutes and confirms your media loads.

## If something goes wrong

| Problem | Fix |
|---|---|
| A player is stuck on "Connecting…" | Have them refresh. If it still fails, ask them to switch between wifi and mobile data. |
| Your host page refreshed by accident | Just reopen the `?host` link. The game, scores and QR code are saved, and players reconnect on their own. |
| "Game ID busy" | You have the host page open in two tabs. Close one. |
| You want a completely fresh game | Tap **Reset everything** on the host screen. This makes a new QR code, and everyone starts from item 1. |
| A picture doesn't show up | Check that the filename in `items.js` matches the file exactly, including capital letters. |

**How it works:** the page connects your phone directly to each player's phone using PeerJS, a free connection service, so there's no server or account to set up. It needs internet on every phone.
