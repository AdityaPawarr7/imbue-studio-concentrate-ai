# imbue-studio-concentrate-ai

Adds Concentrate AI as a sign-in option in Imbue Studio's chat app. Once signed in, the chat's model picker lists Concentrate's models (about 160, from a single key), each with its vendor's logo.

## What it changes

- Sign-in: a "Concentrate AI" option with its logo and the subtitle "200+ models from a single key."
- Model picker: a Concentrate account lists the gateway's full model list with vendor logos. The Claude models keep their existing options, including the 1M-context aliases.
- Fixes a blank model list when the chat window is narrow.

## Install

The patch is made against Imbue Studio at commit `210ca1f3b` (the initial workspace commit). Apply it to a workspace at that commit with a clean working tree:

```
git apply concentrate-provider.patch
cd system && npm ci && npm run build
```

Then restart the chat app or reload the chat window.

## Known issues

- Signing in with a Concentrate key does not check the key. A wrong key is only caught when you send the first message. This existed before the change and is not fixed here.
- Grok models have no logo, because no matching mark is available.
- The model list is fetched live from the gateway, so a slow gateway delays the picker. It shows the built-in list until the answer arrives.
