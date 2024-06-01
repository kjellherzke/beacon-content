# Community Content for [**beacon**](https://github.com/kjellherzke/beacon)

This repository is the library of all community-related content for _beacon_.

Hence there are certain _"guidelines"_ as well as tips for constructive and welcome contributions:

- Follow the basic, systematic folder and file structure
- For **Learning Paths** look [here](#learning-paths)

We would be very pleased, if you may contribute to the site's open source content.

## Learning Paths

This is one of the core features of beacon, providing "roadmaps" to everyone.

A basic visual `/example/index.json` file may look like this:

```json
{
  "title": "An example learning path",
  "nodes": [
    {
      "name": "A simple primary node",
      "x": 0,
      "y": 0
    },
    {
      "name": "A second node to the right",
      "x": 300,
      "y": 0
    }
  ]
}
```

You can see that this concept of nodes is expandable, allowing recursions:

```json
{
  "title": "An example learning path",
  "nodes": [
    {
      "name": "A simple primary node",
      "x": 0,
      "y": 0,
      "nodes": [
        {
          "name": "A child node just below",
          "x": 0,
          "y": 75
        }
      ]
    },
    {
      "name": "A second node to the right",
      "x": 300,
      "y": 0
    }
  ]
}
```

Now a primary node has a direct child node, it's as simple as that.

We could also have child nodes for this child node specifically, by again passing a `nodes` property, and so on. Although this design behaviour is not really recommended.

You may be ready to now start relating markdown files, for instance `/example/index.md`, by doing:

```json
{
  "title": "An example learning path",
  "markdownUrl": "/example/index.md",
  "nodes": [
    {
      "name": "A simple primary node",
      "x": 0,
      "y": 0,
      "nodes": [
        {
          "name": "A child node just below",
          "x": 0,
          "y": 75
        }
      ]
    },
    {
      "name": "A second node to the right",
      "x": 300,
      "y": 0
    }
  ]
}
```

This markdown file will then be the standard text document for this very visual json file.

Furthermore, we can add `markdownUrl`'s to the nodes (and their child nodes):

```json
{
  "title": "An example learning path",
  "markdownUrl": "/example/index.md",
  "nodes": [
    {
      "name": "A simple primary node",
      "markdownUrl": "/example/primary_node/index.md",
      "x": 0,
      "y": 0
    },
    {
      "name": "A second node to the right",
      "markdownUrl": "/example/secondary_node/index.md",
      "x": 300,
      "y": 0
    }
  ]
}
```

See? Now, when clicking a node, the corresponding markdown file (if existing) will be opened too.

> [!IMPORTANT]
> Subtrees and Subnodes

You can also link other (sub-)nodes:

Say that you have a json visual file for a node, called `/example/primary_node/index.json` with the following content:

```json
{
  "title": "A very own sub-tree system",
  "nodes": [
    {
      "name": "I am the only, simple node here",
      "x": 0,
      "y": 0
    }
  ]
}
```

Now you can link this (child) node with the `nodeUrl` property in your `/example/index.json` file:

```json
{
  "title": "An example learning path",
  "markdownUrl": "/example/index.md",
  "nodes": [
    {
      "name": "A simple primary sub-node",
      "nodeUrl": "/example/primary_node/index.json",
      "x": 0,
      "y": 0
    }
  ]
}
```

You see where this is going? Good... Well, note that the `markdownUrl` and `nodeUrl` are competitive properties, and their can only be one of them, because:

If you click on that single node, it will **either** open the new sub node if `nodeUrl` is supplied, or try opening the markdown file with the `markdownUrl` field.

> [!NOTE]
> The `nodeUrl` property has priority over the `markdownUrl` property.

Now the heading can have a `x` and `y` property too, which will then vary the position of the visual graph's title.
By default the values are both `0`.

## More coming soon...
