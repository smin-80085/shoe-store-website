# Haney Shoe Stores – Work & Safety (S 108th St, Omaha)

Website for the Haney Shoe Stores safety-footwear location at 5018 S 108th Street, Omaha, NE 68137 · (402) 339-1542.

It's a static site: one `index.html` page plus an `img/` folder. It needs no build step and no server code, so it runs as-is on GitHub Pages.

## What's in this folder

| Path | What it is |
|---|---|
| `index.html` | The whole site: layout, styles, and the In-Stock product list (the `PRODUCTS` array near the bottom) |
| `img/haney-logo.png` | Haney logo used in the header |
| `img/store-floor.jpg`, `img/store-wall.jpg` | Store photos |
| `img/products/` | Product photos: `-side.jpg` is the main view, `-angle.jpg` is the hover view |
| `.nojekyll` | Tells GitHub Pages to serve the files exactly as they are |

## Publish on GitHub Pages

1. Create a new **public** repository on GitHub, for example `haney-safety-site`.
2. Upload the *contents* of this folder to the root of the repository. `index.html` must sit at the top level, not inside a subfolder.
   - In the browser: open the repo, click **Add file → Upload files**, drag in `index.html`, `README.md`, `.nojekyll` and the `img` folder, then click **Commit changes**.
   - Or from a terminal:
     ```
     git init
     git add .
     git commit -m "Haney 108th St site"
     git branch -M main
     git remote add origin https://github.com/YOUR-USERNAME/haney-safety-site.git
     git push -u origin main
     ```
3. In the repo, go to **Settings → Pages**. Under **Build and deployment**, set Source to **Deploy from a branch**, the branch to **main**, and the folder to **/ (root)**. Click **Save**.
4. After a minute or two the site is live at `https://YOUR-USERNAME.github.io/haney-safety-site/`.

## Using haneyshoeswork.com (optional)

You need to own the domain first.

1. In **Settings → Pages → Custom domain**, enter `haneyshoeswork.com` and save. GitHub adds a `CNAME` file to the repo for you.
2. At your domain registrar, add these DNS records:
   - Four `A` records for `@`: `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - One `CNAME` record for `www` pointing to `YOUR-USERNAME.github.io`
3. Once DNS has updated (minutes to a day), check **Enforce HTTPS** on the same Pages screen.

## Updating products

Products are listed in the `PRODUCTS` array in `index.html`, one line per style:

```js
{brand:"Keen",name:"Women's Sparta 2",style:"1025571",color:"Black",img:"img/products/keen-1025571-side.jpg?v=2",img2:"img/products/keen-1025571-angle.jpg?v=2",price:"$124.99",tags:["Aluminum Toe","EH","Slip Resistant","Women's"]}
```

- To add a style, put an 800×800 photo in `img/products/` and add a line.
- To remove a style, delete its line.
- The brand filter buttons update automatically.
- If you replace a photo but keep the same file name, change `?v=2` to `?v=3` so browsers load the new picture instead of the old one.
