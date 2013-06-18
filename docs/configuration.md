<img src="http://static.creativemarket.com/images/github/logos/csxs@2x.png" width="215" height="123">

### csxs.json

All project settings live in ["csxs.json"](../project/csxs.json). The settings are synthesized to the following files at build-time:

- [".actionScriptProperties"](../project/.actionScriptProperties)
- ["src/manifest.cs5.xml"](../project/src/manifest.cs5.xml)
- ["src/manifest.cs6.xml"](../project/src/manifest.cs6.xml)
- ["src/update.xml"](../project/src/update.xml)
- ["src/ProjectID.mxi"](../project/src/ID.mxi)

## Properties

<table width="100%">
	<tr>
		<th align="left">Property</th>
		<th align="left">Description</th>
	</tr>
	<tr>
		<td valign="top" width="160px"><code>"uuid"</code></td>
		<td valign="top">A random globally-unique id to the project. Used by <a href="http://www.adobe.com/devnet/creativesuite/cs-extension-builder.html">Flash Builder</a>.</td>
	</tr>
	<tr>
		<td valign="top"><code>"version"</code></td>
		<td valign="top">The current version number of the extension. This should be in the format of "0.0.0".</td>
	</tr>
	<tr>
		<td valign="top"><code>"id"</code></td>
		<td valign="top">Unique identifier to represent the extension.</td>
	</tr>
	<tr>
		<td valign="top"><code>"name"</code></td>
		<td valign="top">Extension name. Used in <a href="http://www.adobe.com/exchange/em_download/">Extension Manager</a> and is shown in the panel header.</td>
	</tr>
	<tr>
		<td valign="top"><code>"author"</code></td>
		<td valign="top">Your name or your company name.</td>
	</tr>
	<tr>
		<td valign="top"><code>"description"</code></td>
		<td valign="top">A description of the extension (shown in Extension Manager).</td>
	</tr>
	<tr>
		<td valign="top"><code>"filename"</code></td>
		<td valign="top">The name of the file (excluding the extension) to create when packaging.</td>
	</tr>
	<tr>
		<td valign="top"><code>"license-agreement"</code></td>
		<td valign="top">Legal jargon to display when the user installs the extension.</td>
	</tr>
	<tr>
		<td valign="top"><code>"ui-access"</code></td>
		<td valign="top">A description of how to access the extension.</td>
	</tr>
	<tr>
		<td valign="top"><code>"flex-version"</code></td>
		<td valign="top">Flex version to compile against. This can be overridden by the <code>--flex-version</code> flag.</td>
	</tr>
	<tr>
		<td valign="top"><code>"compiler-arguments"</code></td>
		<td valign="top">An array of additional arguments to provide the Flex compiler.</td>
	</tr>
	<tr>
		<td valign="top"><a name="properties"></a><code>"properties"</code></td>
		<td valign="top">An object containing custom conditional compilation variables. Note: values must be scalar.</td>
	</tr>
	<tr>
		<td valign="top"><a name="certificate"></a><code>"certificate"</code></td>
		<td valign="top">
			Code signing certificate settings. For more information on code signing, see <a href="http://cssdk.host.adobe.com/sdk/1.5/docs/WebHelp/programmers_guide/Deploy.htm">"Packaging and Signing an Extension for Distribution"</a>.
			<table width="100%">
				<tr>
					<th align="left" width="100px">Property</th>
					<th align="left">Description</th>
				</tr>
				<tr>
					<td><code>"location"</code></td>
					<td>Path to the *.p12 code signing certificate (relative to the project root).</td>
				</tr>
				<tr>
					<td><code>"password"</code></td>
					<td>Certificate password.</td>
				</tr>
			</table>
		</td>
	</tr>
	<tr>
		<td valign="top"><a name="s3"></a><code>"s3"</code></td>
		<td valign="top">
			<a href="http://aws.amazon.com/s3/">Amazon S3</a> configuration for automated deploys via the "publish" target.
			<table width="100%">
				<tr>
					<th align="left" width="100px">Property</th>
					<th align="left">Description</th>
				</tr>
				<tr>
					<td><code>"bucket"</code></td>
					<td>S3 bucket name.</td>
				</tr>
				<tr>
					<td><code>"key"</code></td>
					<td>S3 account key.</td>
				</tr>
				<tr>
					<td><code>"secret"</code></td>
					<td>S3 account secret.</td>
				</tr>
				<tr>
					<td><code>"path"</code></td>
					<td>The path to the folder within the bucket to place the files.</td>
				</tr>
			</table>
		</td>
	</tr>
	<tr>
		<td valign="top"><code>"icons"</code></td>
		<td valign="top">
			An object containing paths to extension icon assets.
			<table width="100%">
				<tr>
					<th align="left" width="100px">Property</th>
					<th align="left">Description</th>
				</tr>
				<tr>
					<td><code>"light"</code></td>
					<td>An object containing "normal", "hover", and "disabled" image paths.</td>
				</tr>
				<tr>
					<td><code>"dark"</code></td>
					<td>An object containing "normal", "hover", and "disabled" image paths.</td>
				</tr>
			</table>
		</td>
	</tr>
	<tr>
		<td valign="top"><code>"flex"</code></td>
		<td valign="top">
			An object containing arrays of libraries to link by Flex version.
			<table width="100%">
				<tr>
					<th align="left" width="100px">Property</th>
					<th align="left">Description</th>
				</tr>
				<tr>
					<td><code>"4.5.0"</code></td>
					<td>An array of paths to libraries used when compiling with the Flex 4 compiler.</td>
				</tr>
				<tr>
					<td><code>"3.4.0"</code></td>
					<td>An array of paths to libraries used when compiling with the Flex 3 compiler.</td>
				</tr>
			</table>
		</td>
	</tr>
	<tr>
		<td valign="top"><code>"builds"</code></td>
		<td valign="top">
			An array containing the configuration for the individual builds that make up the *.zxp package.
			Each item in the array extends the base project configuration and must have the following properties defined:
			<table width="100%">
				<tr>
					<th align="left" width="100px">Property</th>
					<th align="left">Description</th>
				</tr>
				<tr>
					<td valign="top"><code>"manifest"</code></td>
					<td valign="top">The filename of the XML manifest in the "src" folder to compile from.</td>
				</tr>
				<tr>
					<td valign="top"><code>"flex-version"</code></td>
					<td valign="top">Flex compiler version.</td>
				</tr>
				<tr>
					<td valign="top"><code>"cs-products"</code></td>
					<td valign="top">An array containing the Creative Suite products to target. Possible items: "photoshop", "illustrator", "indesign", "flash", "fireworks", "dreamweaver", "premiere", "prelude".</td>
				</tr>
				<tr>
					<td valign="top"><code>"cs-versions"</code></td>
					<td valign="top">An array containing all Creative Suite versions to target. Possible items: "6.0", "5.5", "5.0".</td>
				</tr>
				<tr>
					<td valign="top"><code>"cc-products"</code></td>
					<td valign="top">An object mapping Creative Cloud products to target. Each key ("photoshop", "illustrator", "indesign", "flash", "fireworks", "dreamweaver", "premiere", "prelude") should point to an array of version ranges (objects containing "min" and "max" version properties).</td>
				</tr>
			</table>
		</td>
	</tr>
</table>