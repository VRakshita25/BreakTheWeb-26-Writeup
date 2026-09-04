THE SILENT API

Category: GraphQL / API Information Disclosure
Difficulty: Medium

Challenge

The employee portal only shows what it wants you to see.

Sometimes, asking the right questions reveals much more.

Intended solution

The visible interface only requests limited employee fields.

The application communicates with a GraphQL API:

/api/graphql

Players inspect the request and discover that the backend supports more fields than the frontend displays.

The intended first step is GraphQL introspection.

For example:

{
  __schema {
    queryType {
      fields {
        name
      }
    }
  }
}

After discovering the available query structure, players request additional fields that were never exposed by the frontend.

The hidden API functionality eventually reveals the flag.

Flag
BTWCTF{silent_api_never_sleeps_8X4QI365HUE}