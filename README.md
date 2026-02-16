# 302 – Redirect to Any URLs

Minimal static redirect page. It removes `location.origin + "/"` from `location.href`, prepends `https://` to the remainder, validates the result as a URL, and redirects. If invalid, it renders an inline message on the page.

## How It Works

- Remove `location.origin + "/"` from `location.href`.
- Prepend `https://` to the remaining string to form the target.
- Validate with `new URL(...)`.
- If parsing fails or there is no valid hostname, render “Target URL is not a valid URL.” and do not redirect.
- Uses `https://` by default; adjust the front-end logic if you need another scheme.

## Usage

1. Visit your domain with the desired target domain and its path/query in the URL path, for example:
   - `https://example.com/target.com/?search`  
     redirects to: `https://target.com/?search`

> As long as the path begins with a valid domain (e.g., `target.com`, `sub.domain.org`), it will be prefixed with `https://` and redirected.

## Notes

- No whitelist or security filtering is performed; review before using in production.
- Ensure the path starts with a valid domain; otherwise the page shows an error and stays.
