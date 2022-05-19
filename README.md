# renovate-minimal-reproduction-nexus-rubygems

## Current

- The dependency lookup fails and Renovate does not raise a PR to update the dependency.
- Example logs:

    ```shell
    DEBUG: packageFiles with updates (repository=JrobT/renovate-minimal-reproduction-nexus-rubygems)
        "config": {
            "bundler": [
            {
                "packageFile": "Gemfile",
                "registryUrls": ["http://localhost:8081/repository/gems/"],
                "deps": [
                {
                    "depName": "rubocop",
                    "managerData": {"lineNumber": 4},
                    "currentValue": "1.28.1",
                    "datasource": "rubygems",
                    "lockedVersion": "1.28.1",
                    "depIndex": 0,
                    "updates": [],
                    "warnings": [
                    {
                        "topic": "rubocop",
                        "message": "Failed to look up dependency rubocop"
                    }
                    ],
                    "versioning": "ruby"
                }
                ],
                "lockFiles": ["Gemfile.lock"]
            }
            ]
        }
    ...
    DEBUG: http statistics (repository=JrobT/renovate-minimal-reproduction-nexus-rubygems)
        "urls": {
            "http://localhost:8081/repository/gems/api/v1/dependencies (GET,200)": 1,
            "http://localhost:8081/repository/gems/api/v1/gems/rubocop.json (GET,404)": 1,
            "https://api.github.com/graphql (POST,200)": 2,
            "https://api.github.com/repos/JrobT/renovate-minimal-reproduction-nexus-rubygems/issues/1 (GET,200)": 2,
            "https://api.github.com/repos/JrobT/renovate-minimal-reproduction-nexus-rubygems/pulls (GET,200)": 1
        },
        "hostStats": {
            "localhost": {"requestCount": 2, "requestAvgMs": 12, "queueAvgMs": 0},
            "api.github.com": {"requestCount": 5, "requestAvgMs": 231, "queueAvgMs": 0}
        },
        "totalRequests": 7
    ```

## Expected

- Renovate would raise a PR updating `rubocop` to `1.29.0`.
