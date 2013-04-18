<img src="http://static.creativemarket.com/images/github/logos/csxs@2x.png" width="215" height="123">

### Requirements

  * [Build and Install Node.js](https://github.com/joyent/node/wiki/Installation)
  * Install [NPM](http://npmjs.org/): `curl http://npmjs.org/install.sh | sh`
  * Install [csxs](https://github.com/creativemarket/csxs): `npm install -g csxs`

## Getting Started

To create a new project, make an empty folder and use the "create" target to set up
an empty project that's ready to go for development. To compile a debug version and add
it to Photoshop, use the "debug" target.

```sh
# create a folder for a project
$ mkdir my-extension
$ cd my-extension

# create the project & start it
$ csxs create
$ csxs debug --launch
```

More information about building and publishing the extension will be
listed in the ["README.md"](project/README.md) created with the project.

## Project Structure

### Configuration

All project settings live in **"csxs.json"** ([guide](docs/configuration.md)). The settings in this file are synthesized to various
XML files needed by the Flex Compiler and Signing Tool during the build process.

### Folders

<table width="100%">
	<tr>
		<td valign="top" width="160px"><strong>assets/</strong></td>
		<td valign="top">Icons for the panel and Adobe Extension Manager.</td>
	</tr>
	<tr>
		<td valign="top"><strong>changes/</strong></td>
		<td valign="top">A directory containing individual changelog files, by version.</td>
	</tr>
	<tr>
		<td valign="top"><strong>src/</strong></td>
		<td valign="top">Extension source code.</td>
	</tr>
	<tr>
		<td valign="top">README.md</td>
		<td valign="top">Getting started guide.</td>
	</tr>
	<tr>
		<td valign="top">HISTORY.md</td>
		<td valign="top">An aggregated list of changes built automatically by the "changelogs" target.</td>
	</tr>
	<tr>
		<td valign="top">csxs.json</td>
		<td valign="top">All project settings (in lieu of *.xml files).</td>
	</tr>
</table>

## Advanced Topics

### Conditional Compilation

The following [conditional compilation](http://livedocs.adobe.com/flex/3/html/help.html?content=compilers_21.html) variables are automatically provided:

* `CONFIG::version` (string)
* `CONFIG::debug` (boolean)
* `CONFIG::release` (boolean)

#### Adding Custom Variables

Custom variables can be set by adding them to the "properties" object in "csxs.json"
([guide](docs/configuration.md#properties)). The values *must* be scalar. The one exception to
this is if you want different values for debug builds and release builds. In this case, provide an
object with two properties: "debug" and "release".

```json
{
	"properties": {
		"url": {
			"debug": "http://domain.com",
			"release": "http://sandbox.domain.com"
		}
	}
}
```

### Editing XML and MXI Files

XML and MXI files in the project are populated by the properties in ["csxs.json"](docs/configuration.md) at build time.
For complicated extensions, it might be necessary to make changes in these files. Any of the files in
the "src/" folder can be safely edited. Template variables should adhere to [handlebars syntax](http://handlebarsjs.com/).

### Automated S3 Deployment

Automated deployment of releases can be done with the "publish" target. The build tool will compile a release build,
package it as a *.zxp installer, and place it on [S3](http://aws.amazon.com/s3/) (along with a history of changes).
All that's needed is an S3 account. See the [documentation on the `"s3"` property](docs/configuration.md#s3) to see how to
add S3 configuration.

```sh
$ csxs publish
```

#### Deployed Files & Folders

<table width="100%">
	<tr>
		<td valign="top"><strong>changes/</strong></td>
		<td valign="top">Contains changelogs by version and a "master.txt" file (an aggregated list).</td>
	</tr>
	<tr>
		<td valign="top">update.xml</td>
		<td valign="top">Update info read by Adobe Extension Manager.</td>
	</tr>
	<tr>
		<td valign="top">update.json</td>
		<td valign="top">Update info in JSON format.</td>
	</tr>
	<tr>
		<td valign="top">MyExtension.zxp</td>
		<td valign="top">Latest version.</td>
	</tr>
	<tr>
		<td valign="top">MyExtension.0.0.1.zxp</td>
		<td valign="top">Archival version.</td>
	</tr>
</table>

### Automated Git Tagging

When running "publish", HEAD will be tagged with the version being deployed for reference. It is the equivalent of running:

```sh
$ git tag vX.X.X
$ git push origin --tags
```

## Footnotes

* If your project needs host adapters, they have to be extracted manually from Extension Builder (see [Adobe Forums thread](http://forums.adobe.com/message/5245782)).

## License

Copyright &copy; 2013 Creative Market

Licensed under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with the License. You may obtain a copy of the License at: http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.

#### Copyrights & Trademarks

The included ["bin/ucf.jar"](bin/ucf.jar) binary is copyright Adobe Systems Incorporated. The license can be found [here](http://www.adobe.com/devnet/creativesuite/sdk/eula_cs6-signing-toolkit.html). "Creative Suite" is a registered trademark of Adobe Systems Incorporated.