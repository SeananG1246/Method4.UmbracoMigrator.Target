<img src="./docs/images/UmbracoMigratorTarget_Logo.png" alt="Method4.UmbracoMigrator.Target Logo" height="130" align="right">

# Method4.UmbracoMigrator.Target
[![Mozilla Public License](https://img.shields.io/badge/MPL--2.0-orange?label=license)](https://opensource.org/licenses/MPL-2) 
[![Latest version](https://img.shields.io/nuget/v/Method4.UmbracoMigrator.Target?label=version)](https://marketplace.umbraco.com/package/method4.umbracomigrator.target) 
[![NuGet download count](https://img.shields.io/nuget/dt/Method4.UmbracoMigrator.Target?label=downloads)](https://www.nuget.org/packages/Method4.UmbracoMigrator.Target)
[![Umbraco Marketplace](https://img.shields.io/badge/umbraco-marketplace-%233544B1)](https://marketplace.umbraco.com/package/method4.umbracomigrator.target)

## What is the Method4.UmbracoMigrator?
The Method4 Umbraco Migrator allows migrating content and media from an Umbraco v7/v8 site to an Umbraco 10+ site.

This tool was originally created as an intenral tool, for us at Method4, to make migrating our client's Umbraco sites easy. We've decided to make it available as an open source package as we belive other devs in the Umbraco community may find it useful too.

Read our blog post about this tool here:

The migrator tool consists of 2 packages, _Method4.UmbracoMigrator.Source_ and _Method4.UmbracoMigrator.Target_.

### 📤 [Method4.UmbracoMigrator.Source](https://github.com/Method4Ltd/Method4.UmbracoMigrator.Source)
Generates the Migration Snapshot .zip files that will be imported into your shiny new 10+ site!

### 📥 Method4.UmbracoMigrator.Target
Imports the migration snapshots and runs mappers to transform the data.

The Target package ships with built-in default mappers that perform "lazy" mappings, e.g. if an old Node's DocType matches one of our new DocTypes it will attempt to map it, and if any of its properties have identical aliases, then their raw values be copied across.

- Migrate a node if it's old DocType alias matches one of the new DocType aliases
- Migrate a property if it's old alias matches one of the new property aliases
     - The raw property value will be copied accross
     - it will also attempt to convert the format if the new data type has been updated to a new version
          - E.g. MediaPicker (legacy)  can be converted to the new MediPicker 3's format
    

If you need to perform any transformation logic on any of the doctypes/properties, e.g. if a doctype has changed alias, or a property has changed data type, then you will need to create some custom mappers implementing our `IDocTypeMapping`/`IMediaTypeMapping` interfaces.

## 🛠️Features

![A screenshot of the backoffice dashboard](./docs/images/backofficedashboard.png)

### 🔁 Repeatable migrations
When a migration snapshot is imported, a lookup table is populated with the old node IDs and Keys (from the source site) alongside the new IDs and Keys (generated by the target site); This means that future migration snapshots will simply update the previously migrated nodes, rather than creating new nodes, when imported.

This allows you to continue editing content on your source site, all the way up until you perform your final migration!

### ⚒️ Default Mappers & Custom Mappers
The package ships with built-in default mappers that perform "lazy" mappings, e.g. if an old Node's DocType matches one of our new DocTypes it will attempt to map it, and if any of its properties have identical aliases, then their raw values be copied across.

You can also define custom mapping logic by implementing our `IDocTypeMapping`/`IMediaTypeMapping` interfaces, read the documentation for more information.

### 🖼️ Automatically convert Media Picker formats
MediaPicker (legacy) can be converted to the new MediPicker 3's format automatically, or by using our helper classes.

## 🚀 Installation & Umbraco Version Support
> The Package's major versions will match the minimum compatible Umbraco version.<br>
> Whilst this does go against semantic versioning, it should make it easier to figure out which version will work for you.<br>
> We'll try to keep breaking changes out of minor versions, but they may happen if we need them.

<table>
  <tr>
    <th><strong>Umbraco Version</strong></th>
    <th><string>Package Version</strong></th>
  </tr>
  <tr>
    <td>v10, 11, 12</td>
    <td>v10.x</td>
  </tr>
  <tr>
    <td>v13</td>
    <td>v13.x</td>
  </tr>
</table>

### NuGet package repository

To [install from NuGet](https://www.nuget.org/packages/Method4.UmbracoMigrator.Target), you can run the following command from the `dotnet` CLI:

```
dotnet add package Method4.UmbracoMigrator.Target
```

## 📄 [Documentation](./docs/README.md)
Documentation can be found in the `/docs` folder, and there are examples of custom mappers on the `/custom_mapper_examples` folder.

### How do I create a migration snapshot?
You will need to install the [Method4.UmbracoMigrator.Source](https://github.com/Method4Ltd/Method4.UmbracoMigrator.Source) package onto your source website, to generate the snapshots.

![Diagram showing a snapshot export from a va8 to v13 site](./docs/images/Snapshot_diagram.png)

## ❤️ Support
This package was originally created as an internal tool to help us at Method4 perform migrations for our clients, it is being released as open source as we belive the Umbraco community might find it useful.

The package will be updated as and when we need it, feel free to report any bugs/issues you find, contribute by opening a pull request, and we will take a look when we have capacity. Please read the [Contributing Guide](./docs/CONTRIBUTING.md) for information on how to setup the project locally.

## 🛣️ Roadmap
Please see the [roadmap](./docs/ROADMAP.md) for a list of outstanding features and TODOs.

## 📝 License
Copyright &copy; [Method4](https://www.method4.co.uk/).

All source code is licensed under the [Mozilla Public License](./LICENSE).

### 🤝 Acknowledgements
#### Developers

- [Owain Jones](https://owainjones.dev) - ([GitHub](https://github.com/OwainJ), [Mastodon](https://umbracocommunity.social/@ojodev), [Twitter](https://twitter.com/The_DarkGhost))

#### Logo
The package logo uses the [Local Shipping](https://fonts.google.com/icons?selected=Material%20Symbols%20Outlined%3Alocal_shipping%3AFILL%400%3Bwght%40400%3BGRAD%400%3Bopsz%4024) icon from [Google Fonts](https://fonts.google.com/icons), licensed under [SIL Open Font License](https://openfontlicense.org/).

## 🙌 Alternatives
If this package doesn't fit your needs, then check out these other awesome community packages:
- [uSyncMigrations](https://github.com/Jumoo/uSyncMigrations)
