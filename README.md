To reproduce:

1. Run `turbo lint` in the root of the project, or run `turbo lint -F app-a` (same thing for this case)
2. Run the command `npx turbo lint -F app-a --dry=json | jq -r '[.tasks[] | .cache | .status][0]'` to get the status of the cache for the app1 lint task
3. Edit anything in the /packages/pkg-a/a.js file.
4. Run the command described in step 2 again. You will see "HIT" even though the cache should be invalidated.
