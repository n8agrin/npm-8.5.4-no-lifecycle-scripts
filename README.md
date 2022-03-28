To reproduce:

# Expected

1. clone this repo
2. ensure your npm version is <= 8.5.3: `npm i -g npm@8.5.3`
3. in root of project run: `npm i --foreground-scripts`

Expect to see message with ⭐️⭐️⭐️⭐️:

```
➜  npm-8.5.4-no-lifecycle-scripts git:(main) ✗ npm i --foreground-scripts
(#########⠂⠂⠂⠂⠂⠂⠂⠂⠂) ⠋ idealTree: timing idealTree Completed in 9ms
> proj-w-postinstall-dep@1.0.0 postinstall
> echo "⭐️⭐️⭐️⭐️ In >=8.5.4 this is never echoed. ⭐️⭐️⭐️⭐️"

⭐️⭐️⭐️⭐️ In >=8.5.4 this is never echoed. ⭐️⭐️⭐️⭐️

up to date, audited 3 packages in 294ms

found 0 vulnerabilities
```

# Bug

1. ensure your npm version is >= 8.5.4: `npm i -g npm@8.5.4`
2. `rm -rf node_modules` to start repository fresh (not needed, just a sanity check)
3. in root of project run: `npm i --foreground-scripts`
4. 💥 postinstall echo message is not printed:

Message with ⭐️⭐️⭐️⭐️ is missing from output:

```
➜  npm-8.5.4-no-lifecycle-scripts git:(main) ✗ npm i --foreground-scripts

added 1 package, and audited 3 packages in 326ms

found 0 vulnerabilities
```
