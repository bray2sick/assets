# Free Content Delivery Network (CDN) with GitHub Repositories

## Introduction

A Content Delivery Network (CDN) can help you serve your static assets (like images, CSS, and JavaScript files) faster by caching them on servers located around the world. This guide will show you how to use a free CDN with your GitHub repository.

## Steps

### 1. Create a GitHub Repository

If you haven't already, create a GitHub repository and upload your static assets. For example, you can create a repository named `assets` and upload your images, CSS, and JavaScript files.

### 2. Use jsDelivr as a CDN

[jsDelivr](https://www.jsdelivr.com/?docs=gh) is a free CDN that can serve files directly from GitHub repositories. [jsDelivr](https://www.jsdelivr.com/?docs=gh) uses a unique Multi-CDN infrastructure built on top of CDN networks provided by [Cloudflare](https://www.cloudflare.com/en-au/application-services/products/cdn/), [Fastly](https://www.fastly.com/products/cdn), [Bunny](https://bunny.net/), and [GCore](https://gcore.com/). 

To use [jsDelivr](https://www.jsdelivr.com/?docs=gh):

1. Navigate to the images folder (or the folder where you placed your assets) in your GitHub repository.
2. Copy the Permalink:

To get the correct URL with a specific commit hash (for the production link), click the image or file you want to reference.

In the top-right corner of the file preview, click the three dots `...` and select Copy permalink or use the hotkey `Ctrl` + `Shift` + `,` (on Windows/Linux) or `Cmd` + `Shift` + `,` (on macOS).

<p align="center">
  <img src="https://github.com/user-attachments/assets/8eeec9f5-5c45-41f7-8412-0d7dab336816">
</p>

This will give you a link that looks something like:
```
https://github.com/<your-username>/<your-repo>/blob/8af9c43c8b6a6cee840cb10d6933ae579834508d/images/apple.webp
```

3. Modify the URL:

To convert this into the production-ready URL for the CDN, you need to remove the following part:

```
https://github.com/<your-username>/<your-repo>/blob/
```

And replace it, so for the example above, the production URL would be:
```
https://cdn.jsdelivr.net/gh/<your-username>/<your-repo>@8af9c43c8b6a6cee840cb10d6933ae579834508d/images/apple.webp
```
Now, you have both development and production URLs to choose from:

**Development URL** (latest changes reflected instantly):
```
https://cdn.jsdelivr.net/gh/<your-username>/<your-repo>@master/images/apple.webp
```

Uses the master branch, reflecting changes within minutes. Ideal for testing and development.

**Production URL** (stable and permanent version):

```
https://cdn.jsdelivr.net/gh/<your-username>/<your-repo>@8af9c43c8b6a6cee840cb10d6933ae579834508d/images/apple.webp
```

Points to a specific commit, ensuring stable, cached content. Best for production environments where stability is key.

### 3. Alternative CDNs

While I prefer [jsDelivr](https://www.jsdelivr.com/), you can also use other free CDNs like [Statically](https://statically.io/) or [raw.githack.com](https://raw.githack.com/):

**Statically**:
```
https://cdn.statically.io/gh/<your-username>/<your-repo>@master/images/apple.webp
```
**raw.githack.com**:
```
https://raw.githack.com/<your-username>/<your-repo>/main/images/apple.webp
```
When you enter your GitHub URL (static image, CSS, JS, etc.), [raw.githack.com](https://raw.githack.com/) will provide you with **two links** (same concept as jsDeliver instead of doing it manually):

- **Use this URL for production**:
  - No traffic limits. Files are served via CloudFlare's CDN.
  - Files can be automatically optimized if you add ?min=1 query parameter.
  - Use a specific tag or commit hash in the URL instead of a branch. Files are cached permanently based on the URL. The query string is ignored in this case.

- **Use this URL for development**:
  - New changes you push will be reflected within minutes.
  - Excessive traffic may lead to temporary redirection to corresponding CDN URLs.

You can now use this URL in your HTML, CSS, or JavaScript files to serve the image via the CDN.

```html
<!-- jsDelivr -->
<img src="https://cdn.jsdelivr.net/gh/<your-username>/<your-repo>@master/images/apple.webp">
<img src="https://cdn.jsdelivr.net/gh/<your-username>/<your-repo>@8af9c43c8b6a6cee840cb10d6933ae579834508d/images/apple.webp">

<!-- Statically -->
<img src="https://cdn.statically.io/gh/<your-username>/<your-repo>@master/images/apple.webp">
<img src="https://cdn.statically.io/gh/<your-username>/<your-repo>@8af9c43c8b6a6cee840cb10d6933ae579834508d/images/apple.webp">

<!-- raw.githack.com -->
<img src="https://raw.githack.com/<your-username>/<your-repo>/main/images/apple.webp">
<img src="https://rawcdn.githack.com/<your-username>/<your-repo>/8af9c43c8b6a6cee840cb10d6933ae579834508d/images/apple.webp">
```

Note: Make sure to use the production URL when publishing your website. Otherwise, Google Lighthouse will flag the audit with the issue "Serve static assets with an efficient cache policy."

<p align="center">
  <img src="https://github.com/user-attachments/assets/974d988b-7a68-45d7-b8a0-c1e9623e4f05">
</p>

## Conclusion

Using a free CDN like [jsDelivr](https://www.jsdelivr.com/) with your GitHub repository is a simple and effective way to improve the performance of your website by serving static assets faster.

Follow the steps above to set it up and start benefiting from faster load times.

For more information, check out the jsDelivr official documentation on [GitHub](https://www.jsdelivr.com/?docs=gh)
