## About

Very minimal Rails 6 + Webpacker app

## Key lessons

- If build failed, add this new build environment variable:
    - `NODE_OPTIONS=--openssl-legacy-provider`
- If you see `404 Not Found` errors in production for the compiled JS files, add this new build environment variable:
    - `RAILS_SERVE_STATIC_FILES=true`
- If you're building on non-Linux environment e.g. Mac, you may need to run `bundle lock --add-platform x86_64-linux` to update the _Gemfile.lock_ file so the build can run smoothly
- You may need to change these lines inside _babel.config.js_ file:
    ```diff
    - '@babel/plugin-proposal-private-methods',
    + '@babel/plugin-transform-private-methods',
    ...
    - '@babel/plugin-proposal-private-property-in-object',
    + '@babel/plugin-transform-private-property-in-object',
    ```
- If your JS file under _app/javascript/packs_ directory ends with `.erb`, you may need to add `- .js.erb` inside _config/webpacker.yml_ file under the `extensions:` key
- At minimum, [you just need these 3 environment variables](docs/images/env-vars.png). However, `DATABASE_URL` may be required if you're using database e.g. MySQL/PostgreSQL.
