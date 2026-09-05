# Micro Hauling & Junk Removal website

One file: `index.html`. No software to install, nothing to build. Double-click it and it opens in your browser exactly as customers will see it.

## Where the site lives (from 2026-09-04)

- Live address for now: https://trexadavis-prog.github.io/micro-hauling-site/
- Real domain, once bought: https://microhaulingjunkremoval.com (see "Getting the domain" below).
- The files are in a GitHub project called `micro-hauling-site` under Trex's GitHub account. It is its own project and shares nothing with the other projects in that account. GitHub Pages serves it free.

How updates happen: tell Claude what to change. Claude edits `index.html`, checks it in a browser, and pushes it to GitHub. The live site updates within a minute or two. Nothing in this folder has to be touched by hand, and there is no hosting bill.

If you ever want to change something without Claude: edit `index.html`, then on github.com open the `micro-hauling-site` project, click the file, click the pencil, paste the new content, and click **Commit changes**. Same result.

## Getting the domain

microhaulingjunkremoval.com was unregistered on 2026-09-04. To buy it (about $11 a year, you pay, Claude cannot enter payment details):

The owners chose Spaceship (spaceship.com, run by Namecheap) as the place to buy it.

1. Go to https://www.spaceship.com and search `microhaulingjunkremoval.com`. Click **Add to cart**, then **Checkout**. Create the Spaceship account with the business email. Pick a 1-year term with auto-renew on. Decline every add-on (hosting, email, SSL, "premium DNS"); the site needs none of them, and WHOIS privacy is included free.
2. After paying, open **Domain Manager** (top menu), click the domain, then find **DNS records** (Spaceship groups it under "Launchpad", and may call the list "Advanced DNS"). Delete the records already in the list: Spaceship adds two A records that point the name at its own parking page, and the site cannot connect until they are gone, then click **Add record** five times and type these exactly. For "Host", Spaceship uses `@` to mean the bare domain.

   | Type  | Host | Value / Points to             | TTL     |
   |-------|------|-------------------------------|---------|
   | A     | @    | 185.199.108.153               | default |
   | A     | @    | 185.199.109.153               | default |
   | A     | @    | 185.199.110.153               | default |
   | A     | @    | 185.199.111.153               | default |
   | CNAME | www  | trexadavis-prog.github.io     | default |

   Click **Save** after each one. Leave the nameservers on Spaceship's own (the default), or the records above will not apply.
3. Tell Claude "domain bought". Claude connects it to the GitHub project and turns on the HTTPS padlock. Within an hour or so the site answers at microhaulingjunkremoval.com and www.microhaulingjunkremoval.com, and the github.io address keeps working too.

Renewal is yearly on the business email; turn auto-renew on so the site never goes dark.

## The quote form (done 2026-09-04)

The form delivers to microhaulingjunkremoval@gmail.com through Web3Forms. The key is already in `index.html` (search `access_key`).

To change the email later: go to https://web3forms.com, type the new address, click **Create Access Key**, copy the key from the email it sends, open `index.html` in Notepad, search `access_key`, and paste the new key in place of the old one, keeping the quote marks. Nothing else on the page needs to change.

Free plan limits: 250 form submissions a month and no photo attachments. That is why the page asks customers to text photos to 385-204-6385 after submitting.

## Changing words and prices

Everything on the page is plain text inside `index.html`. Search for the thing you want to change and retype it. Common edits:

- **Prices**: search `$75`, `$105`, `$150`, `$250`. Each appears once in the price cards. The `$65` in the title, meta description, and Driveway line is the single-item driveway price ($75 less the $10 discount); the `$30` add-on and `$40` trailer fee sit under the cards.
- **Surcharges**: search `+$25`, `+$20`, `+$15`, `+$10`.
- **Phone number**: search `3852046385` (used in the call and text links) and `385-204-6385` (the printed number). Change every one.
- **Hours**: search `7am to 6pm` and `5pm to 9pm`. They appear three times each.
- **Towns list**: search `Orem, Vineyard`.
- **Colors**: near the top of the file, in the `:root` block, `--accent` is the green. Swap the hex code for another color and every button and price changes with it.

After any edit, save and refresh the browser to check it. If something looks broken, undo the last change, or ask Claude to fix it and paste in the error.

## Adding photos

The page has five photo slots. For launch they are hidden completely (the "LAUNCH MODE" block in the CSS does that), so customers see no gaps. Each slot shows itself again the moment a photo is inside it. The slots: the truck and trailer in the top section, the swept "after" under step 3, the two of you in the About section, and a before-and-after pair under "What we take". Price-card photos (one per fill level) come later, after the first jobs.

1. Put the photo in the `img` folder next to this file. Use the name in the slot's comment: `hero-truck.jpg`, `how-after.jpg`, `about-owners.jpg`, `job1-before.jpg`, `job1-after.jpg`. Landscape, taken on a phone, under about 1 MB each (most phones have a "resize" or "small" option when sharing).
2. Easiest: send the photos to Claude and say which is which. Claude drops them in.
3. Doing it yourself: open `index.html` in Notepad, search for the slot's comment (for example `PHOTO SLOT 1`), and put `<img src="img/hero-truck.jpg" alt="Our truck and trailer">` on the line right after `<figure class="photo" ...>`. Save, refresh. The slot appears on its own once an image is inside it.
4. The truck photo (`hero-truck.jpg`) also becomes the picture in link previews on Facebook and in text messages, so take that one first.

Rules: wipe the truck first, no filters, customer's OK before any before/after is used, no house numbers or customer faces.

## Changing the About section

Search `id="about"`. The heading, the paragraph, the two name cards, and the four promise lines are plain text. Each name card holds a two-sentence first-person bio; retype it like any other text.

## What the buttons do

- **Call or text** in the header opens the phone dialer on a mobile phone.
- **Text us a photo** opens the texting app with a starter message already typed.
- **Request a quote online** scrolls down to the form.
- The form sends to your email through Web3Forms and then shows a green thank-you box in place of the form, with a button to text the photos. If the send fails, a red line asks the customer to text instead.

## Also on the page, invisible to customers

- Link-preview tags, so pasting the address into Facebook, Nextdoor, or a text shows the name, a one-line pitch, and (once the truck photo exists) the picture.
- A business-facts block for Google (name, phone, hours, service towns, price range). City only; no street address anywhere.
- A green tab icon with a white M. No file needed for it.

## Not done yet (on purpose)

- The domain is not bought yet; the site answers at the github.io address until then (see "Getting the domain").
- The five photo slots are hidden until you send photos. Fill-level photos on the price cards come after the first jobs.
- No insurance claim on the page. Add "Insured" only after a policy is actually in place.
- One test send of the quote form by you, from the live site, to confirm it lands in the inbox.
