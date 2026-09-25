---
title: Edición en la Nube 
toc: true
--- 

# {{ page.title }}



## CodeSpaces

Codespaces es un servicio de GH que provee el mismo entorno de desarrollo que VSCode en la nube de GH. 

* Este conjunto de videos es conveniente para empezar con Codespaces <https://m.youtube.com/playlist?list=PLmsFUfdnGr3wTl-NCblzcrEv2lFSX975->
* [GitHub Codespaces](https://docs.github.com/en/codespaces) en docs.github.com
* [GitHub Codespaces vs Gitpod – Full Stack Development Moves to the Cloud](https://www.freecodecamp.org/news/github-codespaces-vs-gitpod-cloud-based-dev-environments/) AUGUST 30, 2021
* Consulte también la discusión en <https://github.com/community/Global-Campus-Teachers/discussions/118#discussioncomment-3715087>

### Personalización 

Si quieres personalizar tu Codespace, puedes leer [Personalizing GitHub Codespaces for your account](https://docs.github.com/en/codespaces/customizing-your-codespace/personalizing-github-codespaces-for-your-account).Puedes personalizar GitHub Codespaces usando un [repositorio `dotfiles` en GitHub](https://docs.github.com/en/codespaces/customizing-your-codespace/personalizing-github-codespaces-for-your-account#dotfiles) o usando [Settings Sync](https://docs.github.com/en/codespaces/customizing-your-codespace/personalizing-github-codespaces-for-your-account#settings-sync).

To speed up codespace creation, you can configure your project to **prebuild codespaces** for specific branches in specific regions. You create and configure prebuilds in your repository's settings. 

- Repository-level settings for GitHub Codespaces are available for all repositories owned by personal accounts.
- For repositories owned by organizations, repository-level settings for GitHub Codespaces are available for organizations on GitHub Team plans that there is the one you get from GH Education as a teacher. 

See the documentation at [codespaces/prebuilding-your-codespaces](https://docs.github.com/en/codespaces/prebuilding-your-codespaces).

A prebuild assembles the main components of a codespace for a particular combination of repository, branch, and devcontainer.json configuration file. 
It provides a quick way to create a new codespace. For complex and/or large repositories in particular, you can create a new codespace more quickly by using a prebuild.
Whenever you push changes to your repository, GitHub Codespaces uses GitHub Actions to automatically update your prebuilds.


