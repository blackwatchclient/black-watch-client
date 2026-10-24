# Microsoft sign-in and Minecraft Services access

[Back to Black Watch](../README.md)

## Purpose

Black Watch intends to support alpha participants using their own Microsoft accounts with Minecraft: Java Edition. Minecraft Services access is needed to complete authentication, retrieve the player's profile and provide an authenticated game session.

## Implemented sign-in path

1. The player starts sign-in in the launcher.
2. The launcher requests a device code from Microsoft and displays Microsoft's verification page and the code.
3. The player signs in and grants consent on Microsoft's website. Black Watch does not ask for the Microsoft password.
4. The launcher exchanges the resulting authorization through Xbox Live and XSTS, then obtains a Minecraft Services token and retrieves the Minecraft profile.
5. The launcher retains account and session data locally so it can display the selected account and renew an authorized session.

The desktop implementation uses personal Microsoft accounts and the `XboxLive.signin` and `offline_access` scopes. It does not use a distributed client secret.

The current development build stores account and token data in a local launcher file. Protection of that storage is part of the remaining release review; this document does not claim encrypted storage or a completed security audit. Account files and tokens are not included in this documentation repository.

## Review status

The project's own application registration and Minecraft Services access approval must be confirmed before the public alpha sign-in path is considered ready. Working local development sessions do not establish that approval. This repository describes the project and intended use; it does not represent an approval from Microsoft or Mojang.

## Protocol references

- [Microsoft: device authorization flow](https://learn.microsoft.com/en-us/entra/identity-platform/v2-oauth2-device-code)
- [Microsoft: public desktop client configuration](https://learn.microsoft.com/en-us/azure/active-directory/develop/scenario-desktop-overview)
