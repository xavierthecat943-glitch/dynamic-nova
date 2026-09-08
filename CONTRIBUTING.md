# Contributing to Dynamic Nova

Thanks for considering contributing! Please follow these guidelines to make the review process smooth.

1. Fork the repository and create a feature branch:

   git checkout -b feature/your-feature

2. Keep changes small and focused. Open a pull request against `main`.

3. Write tests for backend logic where applicable.

4. Run formatters and linters before submitting:

   cargo fmt
   cargo clippy -- -D warnings

5. Describe your changes clearly in the PR description and reference any related issues.

Issue & PR templates (suggestions):
- For bugs: include steps to reproduce, logs, Hyprland version, and expected behavior.
- For features: explain the user-facing change, configuration impact, and any migration notes.

Maintainer
- Be patient — maintainers will review PRs when available.
