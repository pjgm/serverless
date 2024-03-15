# Changelog

All notable changes to this project will be documented in this file. See [standard-version](https://github.com/conventional-changelog/standard-version) for commit guidelines.

## 4.0.0 (2024-03-15)


### ⚠ BREAKING CHANGES

* **Dashboard:** `tenant` configuration setting is no longer respected. Ensure to rely on `org` instead
* **Variables:** Old variables resolver is permanently removed. Any resolution error as approached with current resolver is assumed as final (there's no longer fallback to old resolver)
* `enableLocalInstallationFallback` configuration property is no longer supported.
* Serverless Components v1 (`@serverless/cli`) CLI is no longer integrated with Framework CLI.
* Opt-in tab-tab autocompletion feature is removed due to performance and security issues
* Lifecycle events marked as deprecated (in context of v1) are no longer evaluated
* **CLI:** CLI params put before command tokens are no longer recgonized (e.g. `sls -f <function-name> deploy function` will no longer work). In all cases construct CLI args in `sls <command> <options>` order
* Serverless Components (`@serverless/components`) CLI is no longer integrated with Framework CLI.
* **AWS Lambda:** Default lambda hashing algorithm was changed to `20201221`
* **AWS Lambda:** Runtimes `nodejs10.x`, `python2.7`, `ruby2.5` and
`dotnetcore2.1` reached end of support on AWS and are no longer recognized
in configuration.
* Custom nested configuration paths will no longer be
supported and such usage will result in an error.
* **AWS API Gateway:** Enabling logs or tracing for imported API Gateway will
now result in an error instead of warning
* Remove `studio` command schema
* **CLI:** Unrecognized CLI options will no longer be supported and
will result in an error.
* **AWS EventBridge:** By default, EventBridge resources now will be deployed using
native CloudFormation resources instead of Custom Resources.
* **AWS API Gateway:** For authorizers with `request` type and caching disabled
(`resultTtlInSeconds: 0`), the `identitySource` will no longer be set to
`method.request.header.Authorization` by default.
* Object notation is no longer supported for `service` property.
Set name directly to `service`.
* When creating `Serverless` class instance programatically,
both "options" and "commands" have to be passed via "config" to the constructor.
* **AWS API Gateway:** Support for `usagePlan`, `resourcePolicy` and `apiKeys` on
`provider` level is removed. Use `provider.apiGateway` level instead to set
them.
* **AWS Alexa:** Support for simple `alexaSkill` event was removed and now
`appId` is required for all `alexaSkill` events.
* **AWS HTTP API:** Tags from `provider.tags` are applied by default to HTTP API
Gateway.
* **AWS API Gateway:** Support for `http.request.schema` has been removed and replaced
with `http.request.schemas`.
* **CLI:** The `--verbose` CLI flag does no longer support `-v` alias
* **AWS CloudFront:** Support for `MinTTL`, `MaxTTL`, `DefaultTTL` and
`ForwardedValues` on `cloudfront.behavior` has been removed.
* Duplicate plugin definition in configuration will now result
in an error instead of a warning.
* Using `--aws-s3-accelerate` flag will result in an error
instead of deprecation when custom S3 bucket is used.
* Removed support for `provider.disableDefaultOutputExportNames`
* **AWS Lambda:** Default runtime has been changed from `nodejs12.x` to
`nodejs14.x`
* **AWS Lambda:** Properties `service.awsKmsKeyArn` and
`functions[].awsKmsKeyArn` are no longer supported. Use `provider.kmsKeyArn`
and `functions[].kmsKeyArn` instead.
* Node in versions lower than 12 is no longer supported
* **AWS HTTP API:** `timeout` setting as configured directly for `httpApi` event,  is no longer supported.  Timeout value is now unconditionally resolved from  function timeout setting. It's to guarantee that configured endpoint has necessary room to process function invocation
* **CLI:** When globally installed `serverless` CLI is invoked in a context of a service, which has locally installed (in its `node_modules`) `serverless`. The locally installed CLI will be (by default) run instead of a global one.
* **AWS ALB:** Support for `providers.alb.authorizers[].allowUnauthenticated` setting was removed. Rely on `providers.alb.authorizers[].onUnauthenticatedRequest` instead.
* **CLI:** `slss` alias for `serverless` CLI ommand was removed. Rely on `sls` instead
* **AWS HTTP API:** In AWS HTTP API events (`httpApi`) default `payload` was changed from `1.0` to `2.0`
* **CLI:** `bin/serverless` was removed. If you want to address CLI script directly, point `bin/serverless.js` instead
* Node.js versions below v10 are no longer supported
* Preserver whitespace in variable fallback

### Features

* `azure-nodejs-typescript` template. ([#7252](https://github.com/pjgm/serverless/issues/7252)) ([0549d85](https://github.com/pjgm/serverless/commit/0549d85bc0254a10d3314613892e335da2bc3722))
* `provider.logDataProtectionPolicy` and `functions[].logDataProtectionPolicy` ([#11599](https://github.com/pjgm/serverless/issues/11599)) ([2a5e11a](https://github.com/pjgm/serverless/commit/2a5e11a9977708504e95e011f1cf401a43b94237))
* `uninstall` command for installed binaries ([53e596f](https://github.com/pjgm/serverless/commit/53e596fa6708aa1c3a4359c5679a898cfbd406ec))
* `upgrade` command for installed binaries ([c4efd66](https://github.com/pjgm/serverless/commit/c4efd66e4e9a808d8c79511af6cca7bc653bdec4))
* Account for functions with containers for analytics ([c88a2ea](https://github.com/pjgm/serverless/commit/c88a2ea61a2016982cd24050af8cac5989b07f79))
* Add `has-local-credentials` util ([82a35b3](https://github.com/pjgm/serverless/commit/82a35b3903ad5d8f761612105036fc11a37e9e55))
* Add `X-Amzn-Trace-Id` to default CORS headers ([#11168](https://github.com/pjgm/serverless/issues/11168)) ([9fd56fd](https://github.com/pjgm/serverless/commit/9fd56fddbedf85c01d6f4ebd2f63ab26746f6005))
* add dotnet 8 support ([780812a](https://github.com/pjgm/serverless/commit/780812a78b857cdbbb6703bb9050811eb1072a62))
* add node 8.9 to travis and appveyor ([92f1ef9](https://github.com/pjgm/serverless/commit/92f1ef9fd491818e456b66f16f63a523d0666473))
* add qualifier option to invoke command ([70fa0d8](https://github.com/pjgm/serverless/commit/70fa0d82dde239bdd45b65a945afc70dfcae650b))
* add support for condition and dependsOn ([b2cd8b7](https://github.com/pjgm/serverless/commit/b2cd8b7c0aba472f682b26dde4014312462106ec))
* Add support for java21 runtime ([#12273](https://github.com/pjgm/serverless/issues/12273)) ([#12274](https://github.com/pjgm/serverless/issues/12274)) ([e4dfebd](https://github.com/pjgm/serverless/commit/e4dfebdcf66a0f26138f6774b057924128efbfa5))
* Add support for nodejs20.x runtime ([#12251](https://github.com/pjgm/serverless/issues/12251)) ([f3f0af8](https://github.com/pjgm/serverless/commit/f3f0af85f0783451b7fdf9216d9ab8536853fa46))
* Add support for plain .git template URLs ([3cfa750](https://github.com/pjgm/serverless/commit/3cfa7502e233819d060140b356483d9fd8799800))
* Add support for provided.al2023 runtime ([#12263](https://github.com/pjgm/serverless/issues/12263)) ([6cdf14e](https://github.com/pjgm/serverless/commit/6cdf14e7a81016a69c18d7a1fa6ba293cc3b2a6b))
* Added docs for SFPro SDK endpoint instrumentation ([#7475](https://github.com/pjgm/serverless/issues/7475)) ([2a0f786](https://github.com/pjgm/serverless/commit/2a0f786074f9ac6b0489c85f3efaf98c79ee9f3d))
* Allow `legacy` option for `lambdaHashingVersion` property ([50a8457](https://github.com/pjgm/serverless/commit/50a845709eb846ce5ca3b60116c4ec278896a8b3))
* **Analytics:** Distinguish different standalone installations ([5f81f58](https://github.com/pjgm/serverless/commit/5f81f58b3af615205fb7b0d92c3828ad723a1595))
* **Analytics:** Distinguish npm and other global installations ([7cc898c](https://github.com/pjgm/serverless/commit/7cc898cd0f8ed6cdb63664bed10ecfff74827084))
* **Analytics:** Introduce "isLocallyInstalled" characteristics ([246e4a6](https://github.com/pjgm/serverless/commit/246e4a6756571e00f84b0f0567a305be402d5512))
* **Analytics:** Recognize four different installation modes ([f9e955c](https://github.com/pjgm/serverless/commit/f9e955c8f8ae9c1f8d8f883a052f91d57a7ffa4a))
* **Analytics:** Remove handling of obsolete `serverlessExecutionSpan` ([3e913fa](https://github.com/pjgm/serverless/commit/3e913fafd45ac3a502a49b577e892cbe9a3644b7))
* **Analytics:** Report `isAutoUpdateEnabled` ([48a3e11](https://github.com/pjgm/serverless/commit/48a3e11f333c4e45a58f6810c1f3137fa953f2b8))
* **Analytics:** Report tabtab autocomplete usage ([04b868f](https://github.com/pjgm/serverless/commit/04b868fd3b143c27148e3e1cbbd901c2b19944e1))
* **Analytics:** Send all payloads with single request ([278935d](https://github.com/pjgm/serverless/commit/278935d3f504d040783d508b4f99a132715c751b))
* **Analytics:** Send info on reported deprecations ([83c4b16](https://github.com/pjgm/serverless/commit/83c4b167ee69d4bbd1933e415319a40a27b11daa))
* AWS `iotFleetProvisioning` event support ([#8324](https://github.com/pjgm/serverless/issues/8324)) ([7d80245](https://github.com/pjgm/serverless/commit/7d80245839918f10c3f5681e896ef36c657b38cb))
* **AWS ActiveMQ:** Support `functions[].events[].filterPatterns` ([#11656](https://github.com/pjgm/serverless/issues/11656)) ([1b55710](https://github.com/pjgm/serverless/commit/1b55710f0a869aff2b0d5dfc499a487eb62d204d))
* **AWS ActiveMQ:** Support `maximumBatchingWindow` ([658dc28](https://github.com/pjgm/serverless/commit/658dc28b8b1e087948482553be98b12bd5783c09))
* **AWS ALB:** Cognito and Oidc authentication support ([#7372](https://github.com/pjgm/serverless/issues/7372)) ([8c644f1](https://github.com/pjgm/serverless/commit/8c644f1b07d355544328bd008e831b40aea57af7))
* **AWS ALB:** Recognize `path` as optional condition ([#8571](https://github.com/pjgm/serverless/issues/8571)) ([3632e0e](https://github.com/pjgm/serverless/commit/3632e0ee09945ed5f293779a68409cb297c7d0cc))
* **AWS ALB:** Remove support for `authorizers[].allowUnauthenticated` ([7c304df](https://github.com/pjgm/serverless/commit/7c304df5ffcaaf1dbbd90ccf714f55f4a6cc6a0b)), closes [#8160](https://github.com/pjgm/serverless/issues/8160)
* **AWS ALB:** Support  `onUnauthenticatedRequest` ([#7780](https://github.com/pjgm/serverless/issues/7780)) ([b976677](https://github.com/pjgm/serverless/commit/b9766775148b15f8b19fd9d657149813cb5e8bfa))
* **AWS ALB:** Support `functions[].events[].alb.targetGroupName` ([#9222](https://github.com/pjgm/serverless/issues/9222)) ([2cb8160](https://github.com/pjgm/serverless/commit/2cb81608c8cb7dff7d6b9139235f2285b4b76044))
* **AWS ALB:** Support health check configuration target groups ([#7947](https://github.com/pjgm/serverless/issues/7947)) ([a2f977c](https://github.com/pjgm/serverless/commit/a2f977c8ced67e5002ce5735ce30d44cc36b17be))
* **AWS Alexa:** Remove support for alexaSkill without appId ([8d803e3](https://github.com/pjgm/serverless/commit/8d803e33920015b982eb914350cf15ebe395e72b))
* **AWS API Gateway:** Add HttpApiId to httpApi CF Outputs ([#8664](https://github.com/pjgm/serverless/issues/8664)) ([f9c8677](https://github.com/pjgm/serverless/commit/f9c8677eccdfe14382c7e90079abce9f7bfed866))
* **AWS API Gateway:** Allow CF funcs in `authorizer.scopes` ([#11505](https://github.com/pjgm/serverless/issues/11505)) ([4169ae1](https://github.com/pjgm/serverless/commit/4169ae183f64c5c580d90e653e23cc3c52a6f971))
* **AWS API Gateway:** Allow reuse and customization of schema models ([aeb64fd](https://github.com/pjgm/serverless/commit/aeb64fd3cc6d27c495ce19efc3745a16a46b6534))
* **AWS API Gateway:** Allow to opt-out from default request templates ([7aad819](https://github.com/pjgm/serverless/commit/7aad8193787f591cd3186b2f86e0f9bec23f4dcf)), closes [#8159](https://github.com/pjgm/serverless/issues/8159)
* **AWS API Gateway:** Allow use of custom authorizer with authorizerId ([c0eda27](https://github.com/pjgm/serverless/commit/c0eda272901fd91947c6f37589b33f65c804dc9b))
* **AWS API Gateway:** Change default identity source for authorizers ([786a76d](https://github.com/pjgm/serverless/commit/786a76d1dd7435a373aa9a104f446fb7a062a91a))
* **AWS API Gateway:** Error on tracing or logs set for external API ([d4222c1](https://github.com/pjgm/serverless/commit/d4222c10cf717ada4963ca4a1b5ce7dc86d3985c))
* **AWS API Gateway:** Fix API Gateway naming convention ([#8339](https://github.com/pjgm/serverless/issues/8339)) ([8566135](https://github.com/pjgm/serverless/commit/85661353410d53a94c1d04f1a5c86f1fa456b3ff))
* **AWS API Gateway:** Move api-specific keys to `provider.apiGateway` ([eacae9a](https://github.com/pjgm/serverless/commit/eacae9a64da22ddf0fca8beff580a951e20d4fc0))
* **AWS API Gateway:** Remove API specific settings from `provider` ([bd3ec28](https://github.com/pjgm/serverless/commit/bd3ec282732079c6cc4526afac3466c990ae51d3))
* **AWS API Gateway:** Remove deprecation for old naming convention ([b530d6a](https://github.com/pjgm/serverless/commit/b530d6a288a9881c12382c8004447b94a80f1847))
* **AWS API Gateway:** Remove support for `request.schema` ([dcc9fc0](https://github.com/pjgm/serverless/commit/dcc9fc0cab7fd88c4e95df7a254921f12b1537ff))
* **AWS API Gateway:** Schema for provider.resourcePolicy setting ([#8051](https://github.com/pjgm/serverless/issues/8051)) ([20d9c64](https://github.com/pjgm/serverless/commit/20d9c6414af9a06e2479d203e62aa6427a80f87f))
* **AWS API Gateway:** Simplify referencing local CognitoUserPool ([2e4377e](https://github.com/pjgm/serverless/commit/2e4377ecf038401456c3fca29feeab624846a300)), closes [#7799](https://github.com/pjgm/serverless/issues/7799)
* **AWS API Gateway:** Support `customerId` in API keys ([#7786](https://github.com/pjgm/serverless/issues/7786)) ([c6894b5](https://github.com/pjgm/serverless/commit/c6894b5129c14a43fce0017187cf69aa1bdc9185))
* **AWS API Gateway:** Support `enabled` for `apiKeys` config ([1107763](https://github.com/pjgm/serverless/commit/1107763df8fb07a40ec45529f77d99e5a0f6d4d6))
* **AWS API Gateway:** Support `operationId` setting ([#7617](https://github.com/pjgm/serverless/issues/7617)) ([23bbcea](https://github.com/pjgm/serverless/commit/23bbcea65c3571798435aefc6d6dc9151814cab8))
* **AWS API Gateway:** support `provider.apiGateway.stage` ([#11487](https://github.com/pjgm/serverless/issues/11487)) ([0a49c4f](https://github.com/pjgm/serverless/commit/0a49c4f5df8ef4942ac4758b62a8de5dfc4bf4d8))
* **AWS API Gateway:** Support disabling default endpoint ([#9404](https://github.com/pjgm/serverless/issues/9404)) ([ec90945](https://github.com/pjgm/serverless/commit/ec909452b5167e05d892d2c44bc46b4ff7d7470a))
* **AWS API Gateway:** Support integration mapping of request headers ([56b335f](https://github.com/pjgm/serverless/commit/56b335f99930aa9c2a35ce28e68dfea6d5bf3b7f)), closes [#7897](https://github.com/pjgm/serverless/issues/7897)
* **AWS API Gateway:** Support singular string value for CORS header ([fb4ea15](https://github.com/pjgm/serverless/commit/fb4ea153f0a30f18aad5b93456a1b26ed2d189ac)), closes [#7668](https://github.com/pjgm/serverless/issues/7668)
* **AWS API Gateway:** Support toggling CloudWatch metrics ([#7754](https://github.com/pjgm/serverless/issues/7754)) ([87d40aa](https://github.com/pjgm/serverless/commit/87d40aa8a7fea136a9c05d6e3c350b0d24a58183))
* **AWS APIGW:** Support `logs.restApi.roleManagedExternally`  ([#7333](https://github.com/pjgm/serverless/issues/7333)) ([9b701a4](https://github.com/pjgm/serverless/commit/9b701a405627273fb54e411eb4e87bc085282c6b))
* **AWS APIGW:** Support association of VPC endpoint ids ([#7382](https://github.com/pjgm/serverless/issues/7382)) ([19012a9](https://github.com/pjgm/serverless/commit/19012a9068357f307693823bc56bb2ce1d881a64))
* **AWS CloudFormation:** Add default export names to outputs ([#9313](https://github.com/pjgm/serverless/issues/9313)) ([7e139bb](https://github.com/pjgm/serverless/commit/7e139bb0136e0d053f4f6f8cb2876480bb2a485e))
* **AWS CloudFormation:** Allow to disable default export names ([6f49488](https://github.com/pjgm/serverless/commit/6f494888cc01853894ec33859edbd77a06dc9d76))
* **AWS CloudFront:** Allow legacy behavior configuration ([#11411](https://github.com/pjgm/serverless/issues/11411)) ([65e9860](https://github.com/pjgm/serverless/commit/65e9860838de40c8ef0189c723e09936c8ca71a7))
* **AWS CloudFront:** Recognize `behavior.ResponseHeadersPolicyId` ([906ea31](https://github.com/pjgm/serverless/commit/906ea319dd1486f79d6e088a999fd5634526c4bc)), closes [#11633](https://github.com/pjgm/serverless/issues/11633)
* **AWS CLoudFront:** Recognize `OriginAccessControlId` field ([#11855](https://github.com/pjgm/serverless/issues/11855)) ([9339377](https://github.com/pjgm/serverless/commit/93393777cb5e170bedb5f1a390a544c300ed4101))
* **AWS CloudFront:** Remove support for deprecated `behavior` props ([ff9bbb0](https://github.com/pjgm/serverless/commit/ff9bbb0ff4b33b142da01e7d194e33e1edfa718f))
* **AWS CloudFront:** Support `behavior.CachePolicyId` ([#9895](https://github.com/pjgm/serverless/issues/9895)) ([3abc2f0](https://github.com/pjgm/serverless/commit/3abc2f06428b72d964aa8683c34cdcf1d761d140))
* **AWS CloudFront:** Support CF functions for origin and domain ([0839b58](https://github.com/pjgm/serverless/commit/0839b5862caddb71f31b62493bbb7324d278bd70))
* **AWS CloudFront:** Switch from `ForwardedValues` to cache policies ([479727e](https://github.com/pjgm/serverless/commit/479727e1f4363cef1dd2fa1c20bdb9f7f8493838)), closes [#8381](https://github.com/pjgm/serverless/issues/8381)
* **AWS Cognito:** Add Support for Custom Sender Triggers ([#11201](https://github.com/pjgm/serverless/issues/11201)) ([22802ef](https://github.com/pjgm/serverless/commit/22802efde1d1721404b4e0d704f7806938183522))
* **AWS Cognito:** Support `forceDeploy` setting ([#10435](https://github.com/pjgm/serverless/issues/10435)) ([c67a3f1](https://github.com/pjgm/serverless/commit/c67a3f1a4fe6c64f2b6c68ef1b184b2642ad2266))
* **AWS Deploy:** `--minify-template` CLI param ([#11980](https://github.com/pjgm/serverless/issues/11980)) ([4d64730](https://github.com/pjgm/serverless/commit/4d64730130c44cdfbb872f8a16111df409135dc8))
* **AWS Deploy:** Ensure consistent function state in `deploy function` ([d52526b](https://github.com/pjgm/serverless/commit/d52526bb6059ce20eba341c29ad5a2373c238624))
* **AWS Deploy:** Ensure existence of S3 bucket if possible ([f358585](https://github.com/pjgm/serverless/commit/f35858599ad749b5417c238f510e726615e221dc))
* **AWS Deploy:** Gently handle (strip) `null`'s in CF template ([#8975](https://github.com/pjgm/serverless/issues/8975)) ([9b030ad](https://github.com/pjgm/serverless/commit/9b030ad5f4797c31ea37e621c1a3f297a29dfa86))
* **AWS Deploy:** Introduce new version of hashing algorithm ([#8661](https://github.com/pjgm/serverless/issues/8661)) ([ef53050](https://github.com/pjgm/serverless/commit/ef530506d5044ab3312c829838bb29cfcd2c889f))
* **AWS Deploy:** Introduce warning about `deploy -f` alias ([40f574f](https://github.com/pjgm/serverless/commit/40f574f946e2f40cba13e18b22ee82c7aaa31d3f))
* **AWS Deploy:** Re-introduce `direct` deployment method ([efa3a28](https://github.com/pjgm/serverless/commit/efa3a28f0727602b02989c731054697608c22bbc))
* **AWS Deploy:** Recognize `nodejs.18.x` runtime ([#11526](https://github.com/pjgm/serverless/issues/11526)) ([c25f854](https://github.com/pjgm/serverless/commit/c25f854f29204d1fb6c6254ae89d020751aa8198))
* **AWS Deploy:** Remove `deploy -f` deprecation ([1084251](https://github.com/pjgm/serverless/commit/10842513f0c5422f8627b652b6483523e0351a3c))
* **AWS Deploy:** Retry retryable SDK errors in custom resources ([#8338](https://github.com/pjgm/serverless/issues/8338)) ([a3ebc01](https://github.com/pjgm/serverless/commit/a3ebc01f2bcd6484cfd790bd576bc12962f1b2ff))
* **AWS Deploy:** Support `disableRollback` parameter ([#10236](https://github.com/pjgm/serverless/issues/10236)) ([c9fefce](https://github.com/pjgm/serverless/commit/c9fefced103e47d5d793d979cbb10072daeabf01))
* **AWS Deploy:** Support all regions from iso and isob partition  ([25eb571](https://github.com/pjgm/serverless/commit/25eb571dd3299ac0f61dd1ea40b6b44b355f6898)), closes [#10299](https://github.com/pjgm/serverless/issues/10299)
* **AWS Deploy:** Support customization of request retries count ([6c2fabf](https://github.com/pjgm/serverless/commit/6c2fabf9b98fea921a497c7ad15f4943e78c9b73))
* **AWS Deploy:** Update according to shifted CloudFormation limits ([7e9b2ea](https://github.com/pjgm/serverless/commit/7e9b2eac74cd9b720ac1aba4e01a31f06476165c)), closes [#8433](https://github.com/pjgm/serverless/issues/8433)
* **AWS EventBridge:** `description` property ([#11821](https://github.com/pjgm/serverless/issues/11821)) ([2efe816](https://github.com/pjgm/serverless/commit/2efe8169c9abf5f4f3652774f5055e60b21dd721))
* **AWS EventBridge:** Adjust deprecation of deployment method ([bf62b7c](https://github.com/pjgm/serverless/commit/bf62b7c4dabbecc892fde4d0d988dc2dd2cb7461))
* **AWS EventBridge:** Change default deployment method to native CF ([16f2159](https://github.com/pjgm/serverless/commit/16f2159761063c8f4d42cf513e9367e489bba8c9))
* **AWS EventBridge:** Recognize `$or` in pattern property ([#11967](https://github.com/pjgm/serverless/issues/11967)) ([d6de334](https://github.com/pjgm/serverless/commit/d6de3346ce962392c053f7f6480f52dcdb918624))
* **AWS EventBridge:** Support `deadLetterQueue` and `retryPolicy` ([130fb38](https://github.com/pjgm/serverless/commit/130fb3838fd3ea382caabffad74fde8a4041d4fc))
* **AWS EventBridge:** Support `functions[].events[].eventBridge.name` ([b925c4c](https://github.com/pjgm/serverless/commit/b925c4cf9c2f6a2dddf9eae10b0e62a88f40ff41)), closes [#11690](https://github.com/pjgm/serverless/issues/11690)
* **AWS EventBridge:** Support disabling a rule ([#9865](https://github.com/pjgm/serverless/issues/9865)) ([6193d38](https://github.com/pjgm/serverless/commit/6193d3867ec826898d4effbd641e49a35d9efbbc))
* **AWS EventBridge:** Support for using native CloudFormation ([#8437](https://github.com/pjgm/serverless/issues/8437)) ([13444ca](https://github.com/pjgm/serverless/commit/13444caa28a5fdb268599c8fa67f4bfef1dd5e36))
* **AWS HTTP API:**  Support `provider.httpApi.disableDefaultEndpoint` ([#8649](https://github.com/pjgm/serverless/issues/8649)) ([bebf343](https://github.com/pjgm/serverless/commit/bebf3430b4a22f90497312759e3728a8a233115b))
* **AWS HTTP API:** Add ability to apply `provider.tags` ([#8938](https://github.com/pjgm/serverless/issues/8938)) ([9f5fd61](https://github.com/pjgm/serverless/commit/9f5fd6100978a0bda1c300b9429b24b6e586c52f))
* **AWS HTTP API:** Add support for AWS IAM authorization ([d3c6e43](https://github.com/pjgm/serverless/commit/d3c6e4323b9a3345d71ec43e6ac3013c0ffa02b7))
* **AWS HTTP API:** Add support for custom Lambda authorizers ([37d03b6](https://github.com/pjgm/serverless/commit/37d03b6888788b2ee0b4a679de30ba94d25d7d53))
* **AWS HTTP API:** Allow use of CF ImportValue for httpApi id ([#7905](https://github.com/pjgm/serverless/issues/7905)) ([5a444c4](https://github.com/pjgm/serverless/commit/5a444c415ce31b2c219be47390be165a8da233ea))
* **AWS HTTP API:** Always apply `provider.tags` to HTTP API ([afc0955](https://github.com/pjgm/serverless/commit/afc095509344f94bb73b36481d1bb534af84bc8c))
* **AWS HTTP API:** CORS configuration ([ca69387](https://github.com/pjgm/serverless/commit/ca693872855a59799ec22079d20d048b40ab33a1))
* **AWS HTTP API:** Deprecate `provider.httpApi.useProviderTags` ([650ed37](https://github.com/pjgm/serverless/commit/650ed37db3fd5bab5b4573d85cf7c401181cd2a6))
* **AWS HTTP API:** Deprecate payload 1.0 default ([#7919](https://github.com/pjgm/serverless/issues/7919)) ([ec954f6](https://github.com/pjgm/serverless/commit/ec954f61220f48b379bf4903820bdbb7c2352caf))
* **AWS HTTP API:** Drop support for `timeout` setting ([1cfd1f2](https://github.com/pjgm/serverless/commit/1cfd1f25a278679d94e4cd30baf1b2092ff83d8a))
* **AWS HTTP API:** Initial basic routes configuration support ([69170d0](https://github.com/pjgm/serverless/commit/69170d09a8595605cce9c9c8cafe0d676ea87746))
* **AWS HTTP API:** JWT authorizers support ([fbf99fa](https://github.com/pjgm/serverless/commit/fbf99fa2abf9ce3bc13fc4a6c8439a650d3eaa4e))
* **AWS HTTP API:** Recognize support for CF instructions in authorizers ([428fc79](https://github.com/pjgm/serverless/commit/428fc796c178fc5fcb7478d048ba0b2251ab78e9)), closes [#8200](https://github.com/pjgm/serverless/issues/8200)
* **AWS HTTP API:** Support `payload` version per function ([#9551](https://github.com/pjgm/serverless/issues/9551)) ([87ce28e](https://github.com/pjgm/serverless/commit/87ce28ee4ea0e975859b8d32be8f2edd824b4cda))
* **AWS HTTP API:** Support `shouldStartNameWithService` option ([#9758](https://github.com/pjgm/serverless/issues/9758)) ([ef5a8fa](https://github.com/pjgm/serverless/commit/ef5a8faf13a8fbf8564e7c0621e88d1ea5357ea5))
* **AWS HTTP API:** Support `timeout` configuration ([df9846d](https://github.com/pjgm/serverless/commit/df9846d9afa56bb7d5d8bc07b6a58c2f58eaf59e))
* **AWS HTTP API:** Support access logs configuration ([f2cb89a](https://github.com/pjgm/serverless/commit/f2cb89a3cadc34235ccd62c35beb165942fb60d6))
* **AWS HTTP API:** Support attachment to externally created API ([f47b340](https://github.com/pjgm/serverless/commit/f47b340e4fbe5163595225d450e857ae36211d98))
* **AWS HTTP API:** Support CF functions at `httpApi.authorizer.id` ([453b802](https://github.com/pjgm/serverless/commit/453b8026409e5fdd107fc9cefb7da8ec4b1e8f14)), closes [#8171](https://github.com/pjgm/serverless/issues/8171)
* **AWS HTTP API:** Support externally configured JWT authorizers ([4074739](https://github.com/pjgm/serverless/commit/4074739476e22631b0e06a9d23a2e21d8f29c21e)), closes [#7789](https://github.com/pjgm/serverless/issues/7789)
* **AWS HTTP API:** Support metrics toggle ([#8510](https://github.com/pjgm/serverless/issues/8510)) ([3feafbc](https://github.com/pjgm/serverless/commit/3feafbceb5777904ea19aab1765c85935d5aa904))
* **AWS HTTP API:** Support payload format version customization ([#7623](https://github.com/pjgm/serverless/issues/7623)) ([4c2a52d](https://github.com/pjgm/serverless/commit/4c2a52d1bf8fdb15683c09a8db800aa0e5842950))
* **AWS HTTP API:** Switch default payload mode to 2.0 ([#8133](https://github.com/pjgm/serverless/issues/8133)) ([1596738](https://github.com/pjgm/serverless/commit/1596738cf919bfb5ed702c40f9d3f2b39d529a81))
* **AWS HTTP API:** Use the default API Gateway timeout of 30s ([#11223](https://github.com/pjgm/serverless/issues/11223)) ([16b0cd6](https://github.com/pjgm/serverless/commit/16b0cd60c9914d871eaa3639562ec580c855af43))
* **AWS IAM:**  Resign from deprecating old format of IAM settings ([847dd8f](https://github.com/pjgm/serverless/commit/847dd8f47503ddf03971122e5700110aa3ff77d1))
* **AWS IAM:** Add support for `iam.role.name` definition ([#9166](https://github.com/pjgm/serverless/issues/9166)) ([8c3e1be](https://github.com/pjgm/serverless/commit/8c3e1be735120f5e49f6850259072c13e175b71f))
* **AWS IAM:** Allow `tags` parameter on lambda execution role ([#9039](https://github.com/pjgm/serverless/issues/9039)) ([42a1cdb](https://github.com/pjgm/serverless/commit/42a1cdb6f1b4ca90e9e7f43852672897cb9ec1f9))
* **AWS IAM:** Deprecate IAM settings grouped directly at `provider` ([6f3a632](https://github.com/pjgm/serverless/commit/6f3a63277312bb1819c31eccefacfcda278bd068))
* **AWS IAM:** Group IAM-related settings under `provider.iam` ([#8701](https://github.com/pjgm/serverless/issues/8701)) ([9ad4d07](https://github.com/pjgm/serverless/commit/9ad4d07886d8bca29cb7c0802c3623defb6c8c3a))
* **AWS IAM:** Support `provider.iam.role.path` ([#9363](https://github.com/pjgm/serverless/issues/9363)) ([c8adc0c](https://github.com/pjgm/serverless/commit/c8adc0c796a6558c3fe1bc86e3647d3fe711a9ad))
* **AWS Kafka:** Add support for `mTLS` access configuration ([#10273](https://github.com/pjgm/serverless/issues/10273)) ([9faf37a](https://github.com/pjgm/serverless/commit/9faf37aa153a60784ca783b1e2b7364625e8761f))
* **AWS Kafka:** Support `consumerGroupId` option ([#11345](https://github.com/pjgm/serverless/issues/11345)) ([9bb3f11](https://github.com/pjgm/serverless/commit/9bb3f1154151b1e1a4ca24addd034cf59deb2037))
* **AWS Kafka:** Support `functions[].events[].filterPatterns` ([#11645](https://github.com/pjgm/serverless/issues/11645)) ([6a5e8d9](https://github.com/pjgm/serverless/commit/6a5e8d9ff3ce3cd526470ef3418f3e08c9d3dc76))
* **AWS Kafka:** Support `maximumBatchingWindow` ([e90c114](https://github.com/pjgm/serverless/commit/e90c114932362d79727800f0787237764ce767c3))
* **AWS Kafka:** Support `startingPositionTimestamp` ([#11479](https://github.com/pjgm/serverless/issues/11479)) ([858758e](https://github.com/pjgm/serverless/commit/858758ea1efed07f38e491d21ecfd9873f07b4dd))
* **AWS Kinesis:** More reliable consumer naming mode ([#9706](https://github.com/pjgm/serverless/issues/9706)) ([9d7b121](https://github.com/pjgm/serverless/commit/9d7b121bd1b1ff0f3adcc14bf3dfecf27d589c0f))
* **AWS Kinesis:** Support `AT_TIMESTAMP` starting position  ([#11483](https://github.com/pjgm/serverless/issues/11483)) ([5d41995](https://github.com/pjgm/serverless/commit/5d41995c1939955e48cea0660dac5c32446f7b58))
* **AWS Lambda:**  Basic container image support ([c0ea4c1](https://github.com/pjgm/serverless/commit/c0ea4c14615f90e93baa1dfccfe5b309680b42b1))
* **AWS Lambda:** `functions[].snapStart` support ([#11576](https://github.com/pjgm/serverless/issues/11576)) ([adf11b7](https://github.com/pjgm/serverless/commit/adf11b75e51aefe468005d9daa656377f02ae5ac))
* **AWS Lambda:** Add `ecr.scanOnPush` configuration option ([#9379](https://github.com/pjgm/serverless/issues/9379)) ([078ec59](https://github.com/pjgm/serverless/commit/078ec59058e1c37bd81388c7e81087b48fc2ba24))
* **AWS Lambda:** Add `platform` option for container images ([#10237](https://github.com/pjgm/serverless/issues/10237)) ([5b61b41](https://github.com/pjgm/serverless/commit/5b61b415a0f19ce0755924eae969caf02185d8af))
* **AWS Lambda:** Add ability to customize file for Dockerfile ([785f97b](https://github.com/pjgm/serverless/commit/785f97b1a9e9b4c9cb24f3cb05a502f2d3ae1680))
* **AWS Lambda:** Add support for `activemq` event ([#8840](https://github.com/pjgm/serverless/issues/8840)) ([cacb529](https://github.com/pjgm/serverless/commit/cacb529925ed2b2c591984f48bc52cf31f88e698))
* **AWS Lambda:** Add support for `buildArgs` to `images` ([#9198](https://github.com/pjgm/serverless/issues/9198)) ([efd32d4](https://github.com/pjgm/serverless/commit/efd32d4725cd36e5365aa09f50b75d9ca241d26e))
* **AWS Lambda:** Add support for `cacheFrom` to `images` ([#9251](https://github.com/pjgm/serverless/issues/9251)) ([341a886](https://github.com/pjgm/serverless/commit/341a886874eb8a6c671f576323e75a77cffa1fd2))
* **AWS Lambda:** Add support for `dotnet6` runtime ([#10757](https://github.com/pjgm/serverless/issues/10757)) ([818dda2](https://github.com/pjgm/serverless/commit/818dda21a9b97fbc911d9885d71b8b708b7b1ecf))
* **AWS Lambda:** Add support for `nodejs14.x` runtime ([#8894](https://github.com/pjgm/serverless/issues/8894)) ([8799cbb](https://github.com/pjgm/serverless/commit/8799cbbae76c1e189bd5d576fc68406daf9d9787))
* **AWS Lambda:** Add support for `nodejs16.x` runtime ([#11049](https://github.com/pjgm/serverless/issues/11049)) ([719766b](https://github.com/pjgm/serverless/commit/719766b03088f6acf4045c83045ec2d220c11819))
* **AWS Lambda:** Add support for `SASL/PLAIN` auth to `kafka` event ([3e14f06](https://github.com/pjgm/serverless/commit/3e14f063052385026425021379bfc883dac5ff74))
* **AWS Lambda:** Add support for building Docker images ([#8725](https://github.com/pjgm/serverless/issues/8725)) ([789c2e3](https://github.com/pjgm/serverless/commit/789c2e35ab26b7e8dc0679f36110234fb899d57c))
* **AWS Lambda:** Add support for function URLs ([d215517](https://github.com/pjgm/serverless/commit/d215517cf009ded63e50cd37e55c0be99bdba754))
* **AWS Lambda:** Add support for image config ([#8778](https://github.com/pjgm/serverless/issues/8778)) ([9a55537](https://github.com/pjgm/serverless/commit/9a5553742a3c3ebee03bfab5663a9183d5c228ba))
* **AWS Lambda:** Add support for multiple subscription filters ([#9760](https://github.com/pjgm/serverless/issues/9760)) ([5c9ca56](https://github.com/pjgm/serverless/commit/5c9ca56d14a90dfd9aa5c064bd15137504336ed7))
* **AWS Lambda:** Add support for self-managed `kafka` event ([ff60501](https://github.com/pjgm/serverless/commit/ff605018a70a7156b0ca021adb080a4b4e0f2ede))
* **AWS Lambda:** Allow overriding provider VPC with no VPC on function ([44a81fc](https://github.com/pjgm/serverless/commit/44a81fcc6a229ac6ff59b8c8e51742a9470eef15))
* **AWS Lambda:** Change default hashing algorithm ([9a83415](https://github.com/pjgm/serverless/commit/9a834152a9fe87a561b7c1b0b37a7e92503d8310))
* **AWS Lambda:** Change default runtime to `nodejs14.x` ([c71bab3](https://github.com/pjgm/serverless/commit/c71bab3cd42ed096edaa4a10242de147250a2794))
* **AWS Lambda:** Deprecate `nodejs12.x` as default runtime ([#9416](https://github.com/pjgm/serverless/issues/9416)) ([9e558ee](https://github.com/pjgm/serverless/commit/9e558eefd66e9dafcb16b3636b934d753ade001e))
* **AWS Lambda:** Do not recognize dropped `nodejs12.x` runtime ([032e43c](https://github.com/pjgm/serverless/commit/032e43c77d935b398b162311fa8c37d79a62b20e))
* **AWS Lambda:** Do not require all image properties ([14f5743](https://github.com/pjgm/serverless/commit/14f57438467b5d5c9a3dc356ac4a8b0a6021657f))
* **AWS Lambda:** Ensure `logs:TagResource` permission to IAM role ([#11766](https://github.com/pjgm/serverless/issues/11766)) ([7410275](https://github.com/pjgm/serverless/commit/7410275f66292a67a2d4972d43542f450a687477))
* **AWS Lambda:** Increase memory limits per changes on AWS side ([#8569](https://github.com/pjgm/serverless/issues/8569)) ([c5ae979](https://github.com/pjgm/serverless/commit/c5ae9798d2feca03cbcf2290661a08442c2f1c7d))
* **AWS Lambda:** Prevent external subscription filter removal ([#9839](https://github.com/pjgm/serverless/issues/9839)) ([afc9a13](https://github.com/pjgm/serverless/commit/afc9a13386479f79b4c9ef64b65af5bbcdfaa68b))
* **AWS Lambda:** Recognize `ap-southeast-4` Melbourne region ([#11700](https://github.com/pjgm/serverless/issues/11700)) ([6591504](https://github.com/pjgm/serverless/commit/6591504000f16974f83db1fb0b599fdacf688c52))
* **AWS Lambda:** Recognize `Fn::If` for properties of `vpc` ([#10877](https://github.com/pjgm/serverless/issues/10877)) ([6a86ed7](https://github.com/pjgm/serverless/commit/6a86ed77f8f9702f033b043f47d781d60ab76d4e))
* **AWS Lambda:** Recognize `java17` runtime ([#11938](https://github.com/pjgm/serverless/issues/11938)) ([e1703c8](https://github.com/pjgm/serverless/commit/e1703c8551eaa7051274cf83f302de20264f345e))
* **AWS Lambda:** Recognize `python3.10` runtime ([#11922](https://github.com/pjgm/serverless/issues/11922)) ([8341d7a](https://github.com/pjgm/serverless/commit/8341d7ae736e9e79b83027e5b160307a3641e94a))
* **AWS Lambda:** Recognize `python3.9` as valid runtime ([1aa24b8](https://github.com/pjgm/serverless/commit/1aa24b8991032ba3fe6f2c4b65bf0e70bc4171dd))
* **AWS Lambda:** Recognize CF functions at `.provisionedConcurrency` ([56d8bec](https://github.com/pjgm/serverless/commit/56d8bec84981952497e6db1858af80dd9cf224f1)), closes [#11760](https://github.com/pjgm/serverless/issues/11760)
* **AWS Lambda:** Recognize CF functions in `fileSystemConfig.arn` ([4bf6543](https://github.com/pjgm/serverless/commit/4bf654376f9820efbd78876c72dad95d4cc52831)), closes [#8265](https://github.com/pjgm/serverless/issues/8265)
* **AWS Lambda:** Recognize new .NET runtimes ([#11941](https://github.com/pjgm/serverless/issues/11941)) ([314f32c](https://github.com/pjgm/serverless/commit/314f32cd2bc249ddeae9e6fe2cd00c59be515796))
* **AWS Lambda:** Remove support for `awsKmsKeyArn` setting ([5911675](https://github.com/pjgm/serverless/commit/59116758c973e2c3e3022cb1ade7ad477079955c))
* **AWS Lambda:** Remove support for obsolete runtimes ([7abbde6](https://github.com/pjgm/serverless/commit/7abbde611c3275f151dff28e444f935eb59704ef))
* **AWS Lambda:** Response streaming for Lambda URL ([#11907](https://github.com/pjgm/serverless/issues/11907)) ([3afb71e](https://github.com/pjgm/serverless/commit/3afb71e39d144e8ed6b7634f50a3d8fe8e27daed))
* **AWS Lambda:** Simplify `logs` command output ([d8f251c](https://github.com/pjgm/serverless/commit/d8f251cfd4798672aa36e869882df0e24ebddc10))
* **AWS Lambda:** Support `disableLogs` setting for functions ([#7720](https://github.com/pjgm/serverless/issues/7720)) ([3144be8](https://github.com/pjgm/serverless/commit/3144be82d1a5cd966ed5fb7851cc481e71fe4608))
* **AWS Lambda:** Support `ephemeralStorageSize` ([d317cff](https://github.com/pjgm/serverless/commit/d317cff875535a0de47578e12de395b1d52043a0))
* **AWS Lambda:** Support `Fn::FindInMap` for `vpc` config ([34a9d91](https://github.com/pjgm/serverless/commit/34a9d91870c36d154427830d3555425b5fd2d14c))
* **AWS Lambda:** Support `Fn::If` for `Principal.AWS` ([894ac5b](https://github.com/pjgm/serverless/commit/894ac5b6b67eb384dbc29b927161121679afce2d))
* **AWS Lambda:** Support `logRetentionInDays` per function ([#10878](https://github.com/pjgm/serverless/issues/10878)) ([4c25184](https://github.com/pjgm/serverless/commit/4c25184ca0cffa273c4171f5fccac52ab8ee3413))
* **AWS Lambda:** Support `maximumEventAge` and `maximumRetryAttempts` ([8573ec1](https://github.com/pjgm/serverless/commit/8573ec1e50e4d49baf1a5ae178c32851902f073d)), closes [#7987](https://github.com/pjgm/serverless/issues/7987)
* **AWS Lambda:** Support `Ref` for `destinations` properties ([#10845](https://github.com/pjgm/serverless/issues/10845)) ([9e0ca03](https://github.com/pjgm/serverless/commit/9e0ca03900feb19be21ebe7498ed0fc592af37e0))
* **AWS Lambda:** Support `runtimeManagement` config ([#11715](https://github.com/pjgm/serverless/issues/11715)) ([18d4d69](https://github.com/pjgm/serverless/commit/18d4d69eb3b1220814ab031690b6ef899280a93a))
* **AWS Lambda:** Support 64-bit ARM architecture ([fe655d4](https://github.com/pjgm/serverless/commit/fe655d4f15ca789a1e3a46ce49dc7d23ca806c00))
* **AWS Lambda:** Support CF funcs at `functions[].reservedConcurrency` ([7cfddff](https://github.com/pjgm/serverless/commit/7cfddff31433582ac031be0a168eba2d356d7ee9)), closes [#10129](https://github.com/pjgm/serverless/issues/10129)
* **AWS Lambda:** Support destinations configuration ([8ed6a6e](https://github.com/pjgm/serverless/commit/8ed6a6e7d7efc2857c68acf6e7c641f6ad8fb37c))
* **AWS Lambda:** Support EFS attachment ([#8042](https://github.com/pjgm/serverless/issues/8042)) ([149f64a](https://github.com/pjgm/serverless/commit/149f64ad1c8cec41bfc72ceebcb7c8095b2f8c5c))
* **AWS Lambda:** Support for Amazon MQ RabbitMQ events ([#9919](https://github.com/pjgm/serverless/issues/9919)) ([a3edecf](https://github.com/pjgm/serverless/commit/a3edecf0c6b4e066bde2de8095582432d9fdd635))
* **AWS Lambda:** Support referencing images with tags ([68b7ed5](https://github.com/pjgm/serverless/commit/68b7ed5089f9226c1dbe3b992b93afdcf2015736))
* **AWS Local Invocation:** Randomize awsRequestId ([#8380](https://github.com/pjgm/serverless/issues/8380)) ([6a81137](https://github.com/pjgm/serverless/commit/6a81137406fd2a2283663af93596ba79d23e38ef))
* **AWS Local Invocation:** Resolve "Fn::ImportValue" instructions in env vars ([06ed01b](https://github.com/pjgm/serverless/commit/06ed01b8742260c01411d5e371ab56a6c02219f6)), closes [#8157](https://github.com/pjgm/serverless/issues/8157)
* **AWS Local Invocation:** Resolve CF Ref in env variables ([#8198](https://github.com/pjgm/serverless/issues/8198)) ([72745c9](https://github.com/pjgm/serverless/commit/72745c9e77476f65604fdc68e8e3c55feffdf90f))
* **AWS Local Invocation:** Support `python3.9` runtime ([#9879](https://github.com/pjgm/serverless/issues/9879)) ([ee17ee5](https://github.com/pjgm/serverless/commit/ee17ee5aca25af152c2720a55199d92dfab3216d))
* **AWS Local Invocation:** Support `ruby3.2` ([#12004](https://github.com/pjgm/serverless/issues/12004)) ([0a0a4fc](https://github.com/pjgm/serverless/commit/0a0a4fc8af4c88a2a2d85401b3fb89341b927f47))
* **AWS Local Invocation:** Support decimal serialization for Python ([9ef46ba](https://github.com/pjgm/serverless/commit/9ef46ba05ff033dbf04c451a214bf4ced23c90e8))
* **AWS Local Invocation:** Support ESM handlers ([#11212](https://github.com/pjgm/serverless/issues/11212)) ([675b1db](https://github.com/pjgm/serverless/commit/675b1dbed764f70a7443cdd5e4a53c54315fec36))
* **AWS Local Invocation:** Support Node handlers with `.cjs` extension ([688f50d](https://github.com/pjgm/serverless/commit/688f50d670b84a1dce097256776651b3138de456))
* **AWS Local Invocation:** Support ruby2.7 runtime ([#7538](https://github.com/pjgm/serverless/issues/7538)) ([a6b3154](https://github.com/pjgm/serverless/commit/a6b3154deebdcd530afa0c716a6d7efca13de6f2))
* **AWS Local Invocation:** Upgrade Java dependencies ([#11535](https://github.com/pjgm/serverless/issues/11535)) ([eb741fe](https://github.com/pjgm/serverless/commit/eb741fed22773f6b4b08a67837ab39a518101825))
* **AWS Local Invoke:** Revert breaking jackson-databind upgrade ([#11589](https://github.com/pjgm/serverless/issues/11589)) ([f00eb82](https://github.com/pjgm/serverless/commit/f00eb824c201a09206337a34aab700500314fe50))
* **AWS MSK:** Add support for SASL/SCRAM authentication ([#11060](https://github.com/pjgm/serverless/issues/11060)) ([184cb03](https://github.com/pjgm/serverless/commit/184cb030a87a20d0491ee3d79244ca017d44aabf))
* **AWS MSK:** Support `AT_TIMESTAMP` starting position ([#12034](https://github.com/pjgm/serverless/issues/12034)) ([483ea16](https://github.com/pjgm/serverless/commit/483ea166fc6af2bed363a2a9ebf3ec8d06900618))
* **AWS MSK:** Support `functions[].events[].filterPatterns` ([#11636](https://github.com/pjgm/serverless/issues/11636)) ([63584a9](https://github.com/pjgm/serverless/commit/63584a9a0d1a9523c23367de47e7fe575c5cf12b))
* **AWS MSK:** Support `maximumBatchingWindow` ([#10580](https://github.com/pjgm/serverless/issues/10580)) ([d341b6b](https://github.com/pjgm/serverless/commit/d341b6b99d61e44cbb00e18cbfd791e963890bfd))
* **AWS MSK:** Support MSK through "msk" event ([#8164](https://github.com/pjgm/serverless/issues/8164)) ([05d703e](https://github.com/pjgm/serverless/commit/05d703e6d5a7b100aaf6203209b0d596a3e70496))
* **AWS RabbitMQ:** Support `functions[].events[].filterPatterns` ([#11659](https://github.com/pjgm/serverless/issues/11659)) ([e769570](https://github.com/pjgm/serverless/commit/e769570704fee372c2fa849c332d476d38e858be))
* **AWS RabbitMQ:** Support `maximumBatchingWindow` ([d0554b7](https://github.com/pjgm/serverless/commit/d0554b738543221e0fe3d9c6fd83d30a15aae79f))
* **AWS RabbitMQ:** Support `virtualHost` ([#10814](https://github.com/pjgm/serverless/issues/10814)) ([e21fb75](https://github.com/pjgm/serverless/commit/e21fb756fc8625c7dc1bfe86137effbcf09f8287))
* **AWS S3:** Recognize `ExpirationInDays` property for `s3` events ([8e6dcd1](https://github.com/pjgm/serverless/commit/8e6dcd1aaed50007b5b99e18f61dfa849b898cd9))
* **AWS S3:** Support `Fn::If` CF function for s3 event ([a4fa498](https://github.com/pjgm/serverless/commit/a4fa49844d23afea90f7c9aa4616beedd2a80db8))
* **AWS S3:** Support `forceDeploy` setting ([#11066](https://github.com/pjgm/serverless/issues/11066)) ([5af44a4](https://github.com/pjgm/serverless/commit/5af44a478e66cb7361dd09a79e9acc1869552f19))
* **AWS S3:** Support CF functions for `bucket` event property ([#9617](https://github.com/pjgm/serverless/issues/9617)) ([42690a7](https://github.com/pjgm/serverless/commit/42690a7352751581a8dbd44a4f776af17ab20da8))
* **AWS Schedule:** `AWS::Scheduler::Schedule` based triggers ([#11935](https://github.com/pjgm/serverless/issues/11935)) ([34d922d](https://github.com/pjgm/serverless/commit/34d922d3d8d33f6e17e697610fdef7f13003a2f3))
* **AWS Schedule:** Allow multiple rate expressions in single event ([9f0bc68](https://github.com/pjgm/serverless/commit/9f0bc689cc2ac3e53b4db665b899e1446ac37456))
* **AWS Schedule:** Support CF instrinsic functions at `.rate` ([#11714](https://github.com/pjgm/serverless/issues/11714)) ([fc6bd57](https://github.com/pjgm/serverless/commit/fc6bd57bbf18898976f6caa18e310cbd921a7270))
* **AWS SNS:** Support `functions[].events[].filterPolicyScope` ([#11644](https://github.com/pjgm/serverless/issues/11644)) ([b7d6af6](https://github.com/pjgm/serverless/commit/b7d6af6b1309a5b4fbfac54265e7900196416976))
* **AWS SQS:** Support `filterPatterns` ([3f0a80a](https://github.com/pjgm/serverless/commit/3f0a80acd3fcf9eb7768625eb6cfe06cf572afa0))
* **AWS SQS:** Support `functionResponseType` ([#10265](https://github.com/pjgm/serverless/issues/10265)) ([44511f3](https://github.com/pjgm/serverless/commit/44511f343b1a68ca147e8ba9e8b493143b89c324))
* **AWS SQS:** Support `functions[].events[].sqs.maximumConcurrency` ([57f2719](https://github.com/pjgm/serverless/commit/57f27193e052b01cd67745c7576f77b2d8988a6f)), closes [#11678](https://github.com/pjgm/serverless/issues/11678)
* **AWS SQS:** Support `maximumBatchingWindow` ([#8555](https://github.com/pjgm/serverless/issues/8555)) ([ffde506](https://github.com/pjgm/serverless/commit/ffde506db76b15a873e88aded7cfa32eb3382c6c))
* **AWS SQS:** Support `maximumRetryAttempts` option ([#7620](https://github.com/pjgm/serverless/issues/7620)) ([9416e72](https://github.com/pjgm/serverless/commit/9416e72cba58c0a83b6bad07cdb740d36d131e96))
* **AWS Stream:** Add support for `maximumRecordAgeInSeconds` property ([003fcfb](https://github.com/pjgm/serverless/commit/003fcfb8fc1b083e01daa2e478086ee89e74c644)), closes [#7833](https://github.com/pjgm/serverless/issues/7833)
* **AWS Stream:** Add support for custom checkpoint ([#9056](https://github.com/pjgm/serverless/issues/9056)) ([b2188a2](https://github.com/pjgm/serverless/commit/b2188a20d935b2ae8fccf594c4bd39eddcb7ef8c))
* **AWS Stream:** Support `filterPatterns` ([#10285](https://github.com/pjgm/serverless/issues/10285)) ([fc00505](https://github.com/pjgm/serverless/commit/fc0050559cd1ee7b8a53a08fae73940177da93cb))
* **AWS Stream:** Support `tumblingWindowInSeconds` ([#9979](https://github.com/pjgm/serverless/issues/9979)) ([af39fc0](https://github.com/pjgm/serverless/commit/af39fc016bd6386ea7d5d1ff71a26553a25b7ec5))
* **AWS Websocket:** `routeResponseSelectionExpression` setting ([#7233](https://github.com/pjgm/serverless/issues/7233)) ([2d25e67](https://github.com/pjgm/serverless/commit/2d25e678cb1390d3cfb8899f424ff4638b239ddc)), closes [#6130](https://github.com/pjgm/serverless/issues/6130)
* **AWS Websocket:** Add ability to configure log format and types ([82ce1c8](https://github.com/pjgm/serverless/commit/82ce1c83d23008a5f7b48d149fcaac828c782871))
* **AWS Websocket:** Allow propagating tags to Websocket APIGW ([#10931](https://github.com/pjgm/serverless/issues/10931)) ([22e4842](https://github.com/pjgm/serverless/commit/22e4842d97ac3cbc11d8c398e84639af0b6068b8))
* **AWS Websocket:** Support CF intrinsic functions at `arn` ([#8335](https://github.com/pjgm/serverless/issues/8335)) ([9303d8e](https://github.com/pjgm/serverless/commit/9303d8ecd46059121082c3308e5fe5385e0be38e))
* aws-nodejs-typescript template improvements ([83cfbd2](https://github.com/pjgm/serverless/commit/83cfbd25e80c8ad5254240c7d7ae3dd8851b5e21))
* Bring back support for `serverlessExecutionSpan` ([f805786](https://github.com/pjgm/serverless/commit/f805786d7cfdb5176af766beb29e229b98da7d7f))
* Clear `null` valued props in service configuration ([57996a0](https://github.com/pjgm/serverless/commit/57996a06a0704ea5ca79df9907c8dad56e0824b8))
* **CLI:**  Deprecate support for `deploy -f` alias ([b5069ef](https://github.com/pjgm/serverless/commit/b5069ef8cb3dff0127781cecad1774faa62a7415))
* **CLI Onboarding:** Add deploy step ([f5c1c47](https://github.com/pjgm/serverless/commit/f5c1c47fa293d3471ace071701cd1932cafce311))
* **CLI Onboarding:** Add deploy step ([28a06a0](https://github.com/pjgm/serverless/commit/28a06a05aba4306d2f28d26652067b44ed105151))
* **CLI Onboarding:** Add telemetry for interactive flow ([0eba2dc](https://github.com/pjgm/serverless/commit/0eba2dcdfeabba58920462ac2cd54d86e3101e05))
* **CLI Onboarding:** Auto login if `org` provided or configured ([dcf5273](https://github.com/pjgm/serverless/commit/dcf52731ea3920ecf16b2484e2673080acbfe1cd))
* **CLI Onboarding:** Dont allow setup with options in service dir ([7e8e1b6](https://github.com/pjgm/serverless/commit/7e8e1b62bb2b454ba23387a4c93b906b6de07890))
* **CLI Onboarding:** Fetch templates from `serverless/examples` ([e4ea50d](https://github.com/pjgm/serverless/commit/e4ea50d401628cb22612196b7e9b50c4344dab8a))
* **CLI Onboarding:** Improve deploy messaging ([97fda34](https://github.com/pjgm/serverless/commit/97fda34b29ecd3711bcd4b94c741ff9b17663188))
* **CLI Onboarding:** Improve onboarding messaging ([f69a19c](https://github.com/pjgm/serverless/commit/f69a19c6804366a34324e7cfcbbdb3f247a12b85))
* **CLI Onboarding:** Present default project name if possible ([dee54ed](https://github.com/pjgm/serverless/commit/dee54ed55c0a0697eefdde99d5ec8aee321ce041))
* **CLI Onboarding:** Remove `serverless.template.yml` from template ([da7a70d](https://github.com/pjgm/serverless/commit/da7a70d83f1c77814c34a21c39116f39335ba9c4))
* **CLI Onboarding:** Remove `tab-completion` from interactive flow ([3bac0f3](https://github.com/pjgm/serverless/commit/3bac0f37f0f23abed387f0952772e3cdf5d47320))
* **CLI Onboarding:** Remove initial `confirm` question from the flow ([d5e2baf](https://github.com/pjgm/serverless/commit/d5e2baf714958c5718610659887f485f9bd161e4))
* **CLI Onboarding:** Run `npm i` after fetching template ([acc9010](https://github.com/pjgm/serverless/commit/acc9010d7906dc7e56a97b60e25bf1920f402925))
* **CLI Onboarding:** Skip "enable" question when options provided ([e63302b](https://github.com/pjgm/serverless/commit/e63302bcb5cd8e20db4272d1d73b6c9e4cb09958))
* **CLI Onboarding:** Support `--console` flag ([a34d07a](https://github.com/pjgm/serverless/commit/a34d07a5c129e21d1a0b902479bcaa4a92c158fb))
* **CLI Onboarding:** Support `--name` CLI option ([53575dc](https://github.com/pjgm/serverless/commit/53575dc36017ded5ff60e5edf18fb7a9fd9d30e9))
* **CLI Onboarding:** Support `template-path` param ([98c9700](https://github.com/pjgm/serverless/commit/98c9700bcda328552f04116a51549f66e3d7b026))
* **CLI Onboarding:** Support `template` and `template-url` options ([f1a288c](https://github.com/pjgm/serverless/commit/f1a288ce2c30e1377d8b411a90db3b1b2857d4fb))
* **CLI Onboarding:** Support all runtimes for dashboard ([0ca0cff](https://github.com/pjgm/serverless/commit/0ca0cfffda6dbf5c3179a6d2de4b2dd52e07af59))
* **CLI Onboarding:** Support joint Console & Dashboard configurations ([48609f7](https://github.com/pjgm/serverless/commit/48609f72762ffe8eabd9415084eed42e01ea061e))
* **CLI Onboarding:** Support provider creation flow ([e8681ee](https://github.com/pjgm/serverless/commit/e8681ee157a697bbc560ff8b6b0da9adde57c048))
* **CLI Onboarding:** Support provider creation flow ([feb0421](https://github.com/pjgm/serverless/commit/feb04219f6be186cc54462906394bbd82f9747b5))
* **CLI Onboarding:** Switch to `httpApi`-based templates ([12216db](https://github.com/pjgm/serverless/commit/12216db579f7f2d055410f1ea9449825628631b7))
* **CLI:** Add auto update config step to interactive setup ([2c4fa7b](https://github.com/pjgm/serverless/commit/2c4fa7baec13ae13a631068513e62c2fe0fe1e6d))
* **CLI:** Add deprecation summary for modern logs ([7eba95f](https://github.com/pjgm/serverless/commit/7eba95fcb7f9b09a8a2aebd50c433f92e15cac97))
* **CLI:** Add timer to final message in modern logs ([7828cc7](https://github.com/pjgm/serverless/commit/7828cc77f1fcea8f901887c12b07f5e18b34dcc8))
* **CLI:** Announce `frameworkVersion` requirement ([9f7f9d3](https://github.com/pjgm/serverless/commit/9f7f9d398339d9c8ba09ae3b74d3e7bbbca4dcee))
* **CLI:** Automatically expand loaded env variables ([#9615](https://github.com/pjgm/serverless/issues/9615)) ([1864969](https://github.com/pjgm/serverless/commit/186496922a0c4d69f3101dde0a9f4a0d89995ad0))
* **CLI:** Conditional support for .env files ([#8413](https://github.com/pjgm/serverless/issues/8413)) ([d1a22c8](https://github.com/pjgm/serverless/commit/d1a22c85f2220a2f4691255fb3b9961aeaa4abcb))
* **CLI:** Configure log writing with new (experimental) log engine ([ec93174](https://github.com/pjgm/serverless/commit/ec93174b8ccfe1715ce3615dcb2223b145ad0f31))
* **CLI:** Deprecate "slss" alias ([#8156](https://github.com/pjgm/serverless/issues/8156)) ([a2d1031](https://github.com/pjgm/serverless/commit/a2d1031fb88ac750685b5940b60c0b241c90e319))
* **CLI:** Deprecate bin/serverless binary ([a60d2c7](https://github.com/pjgm/serverless/commit/a60d2c7dd8648a17c9ca09c363d3ab88b797a11c))
* **CLI:** Deprecate missing options schema ([a196e04](https://github.com/pjgm/serverless/commit/a196e0403ea551e9bd1cb9708415f603ca97c0b2))
* **CLI:** Deprecate recognition of `projectDir` configuration setting ([79820d6](https://github.com/pjgm/serverless/commit/79820d619105679894b9f0f33117bbd7c13f5608))
* **CLI:** Deprecations logger ([#7741](https://github.com/pjgm/serverless/issues/7741)) ([6f32f23](https://github.com/pjgm/serverless/commit/6f32f236d8c44464b34e8c666e4ecbb3abe287d4))
* **CLI:** Do not run `compose` for non-service commands ([e56bc4b](https://github.com/pjgm/serverless/commit/e56bc4be0c5941e76a6433782aa1462b83f5d13f))
* **CLI:** Enable `env` variables in `provider.stage` property ([bbb6c6c](https://github.com/pjgm/serverless/commit/bbb6c6cd7dea9100af3ff84dd490b2cac1e2971e))
* **CLI:** Ensure to clear progress in expected time points ([29aec52](https://github.com/pjgm/serverless/commit/29aec529b53d7dd10f4ec61db7c0dc3859995d27))
* **CLI:** Expose installation type by `serverless-tencent` version info ([4c5f834](https://github.com/pjgm/serverless/commit/4c5f8349050cb870f80f210be4f93f7fb55bd71c))
* **CLI:** Fallback to service local serverless installation by default ([dfc7839](https://github.com/pjgm/serverless/commit/dfc78396c7c555887163c5f3f60361568eebbfa4))
* **CLI:** First iteration of support for `verbose` mode in `deploy` ([fbdd124](https://github.com/pjgm/serverless/commit/fbdd124029d10ef029ee5446777db44f907e026c))
* **CLI:** Global `--debug` flag for debug logging ([dc0bf5c](https://github.com/pjgm/serverless/commit/dc0bf5c9aaeb5bb349ee5c113878010f98fcd555))
* **CLI:** Global `--verbose` flag for verbose logging ([5194030](https://github.com/pjgm/serverless/commit/5194030462add10a7ce0c83897fc71109ceb6fb6))
* **CLI:** Improve general `--help` and remove `--verbose` option ([#8532](https://github.com/pjgm/serverless/issues/8532)) ([4287494](https://github.com/pjgm/serverless/commit/42874946fc7ff92323d3ce5643415449122d2f38))
* **CLI:** Introduce deprecation for duplicate plugin definition ([d2a75ea](https://github.com/pjgm/serverless/commit/d2a75ea95e814cd5aaba5eca4c5acebd2aad0bb8))
* **CLI:** Introduce deprecation on S3 Accelerate for user bucket ([04b921a](https://github.com/pjgm/serverless/commit/04b921acdc5fd486ffd10fe81fcb2243f37329db))
* **CLI:** Introduce first iteration of modern logs for `deploy` ([#9934](https://github.com/pjgm/serverless/issues/9934)) ([171897d](https://github.com/pjgm/serverless/commit/171897d60e5adaa590be1f08c99ab2cc76e89ee4))
* **CLI:** Modern debug (previously verbose) logs related to deploy ([655140b](https://github.com/pjgm/serverless/commit/655140b764c8f2998188c3d47110494cbd742688))
* **CLI:** Modern help output ([b2df3cc](https://github.com/pjgm/serverless/commit/b2df3cc0c8cba17c1995d3038e4a2caaca2f47f5))
* **CLI:** Modern logs for `deploy function` command ([4d42ce3](https://github.com/pjgm/serverless/commit/4d42ce3fa4f44f63d68a3841752746021500fe4f))
* **CLI:** Modern logs for `deploy list functions` command ([ffbdfed](https://github.com/pjgm/serverless/commit/ffbdfed292fdc379040052e6ec73107e5fdae5a8))
* **CLI:** Modern logs for `deploy list` command ([9d6482c](https://github.com/pjgm/serverless/commit/9d6482c6710cb2d05c8c03a29e207881efcc0138))
* **CLI:** Modern logs for `package` command ([fa2507d](https://github.com/pjgm/serverless/commit/fa2507dad06b037aa5a24b3392432cefc810a972))
* **CLI:** Modern verbose logs for `deploy function` command ([10df2e5](https://github.com/pjgm/serverless/commit/10df2e5300e04ec9d00ebd343d9d8fe30c96afa7))
* **CLI:** Modern verbose logs related to deploy operation ([e423404](https://github.com/pjgm/serverless/commit/e423404290a757a8adfc97d45e9aef7aa93f1404))
* **CLI:** New `warn:summary` (default) deprecations logging mode ([9b624a5](https://github.com/pjgm/serverless/commit/9b624a50677a0363c052b4ea567c050af7863073))
* **CLI:** Optionally fallback to local installation of "serverless" ([9fb62f1](https://github.com/pjgm/serverless/commit/9fb62f1138fc36e035993740496336af314171aa))
* **CLI:** Register `-v` as global `--version` alias ([bd6fd4f](https://github.com/pjgm/serverless/commit/bd6fd4fc3dd1906c9e5d027bb712ebdfe7368d92))
* **CLI:** Remove "slss", "serverless" command alias ([#8161](https://github.com/pjgm/serverless/issues/8161)) ([33eef9f](https://github.com/pjgm/serverless/commit/33eef9f06b83b889baaa28cab1eaece275790a52))
* **CLI:** Remove `-v` alias for `--verbose` flag ([b5e6857](https://github.com/pjgm/serverless/commit/b5e6857c8322789497171f614336020737ecaaaa))
* **CLI:** Remove missing CLI options schema deprecation ([5b38232](https://github.com/pjgm/serverless/commit/5b38232e631e1fb6d944d5f323f533d7dd7b701f))
* **CLI:** Remove support for unrecognized cli options ([fe1a2db](https://github.com/pjgm/serverless/commit/fe1a2db773043e6924246e7744f6dfb687781058))
* **CLI:** Report Platform Client instead of SDK version ([#9092](https://github.com/pjgm/serverless/issues/9092)) ([2b857c7](https://github.com/pjgm/serverless/commit/2b857c7eb45e6543ca5afb5604542e8f76175910))
* **CLI:** Revert from unconditional `.env` support ([40cdb4f](https://github.com/pjgm/serverless/commit/40cdb4f1a191d330e31ddadc4caaa4b314229e3d))
* **CLI:** Simplify CLI args parsing to <command> <options> format ([eedaa24](https://github.com/pjgm/serverless/commit/eedaa2469f231270112ab31fb5b63baa454ec701))
* **CLI:** Support `serverless-tencent` CLI ([a646135](https://github.com/pjgm/serverless/commit/a6461351189b541dabbac1cf1595ba7d362e9ce1))
* **CLI:** Support absolute path at "--config" ([aea9f93](https://github.com/pjgm/serverless/commit/aea9f9397c3806edda9958e324678af168b46b2f))
* **CLI:** Validate command and options against resolved schema ([2dacbcc](https://github.com/pjgm/serverless/commit/2dacbcce8529378d94abc7a0b0d0039ecee4d790))
* Coerce input configuration values ([6d1ee37](https://github.com/pjgm/serverless/commit/6d1ee37004509ccb46737f2a87c6b74799de2cb7))
* Coerce primitive config values to arrays, when array is expected ([a6ff964](https://github.com/pjgm/serverless/commit/a6ff964d84834985f485ae657e8fc5ecd6801958))
* **Config Schema:** `defineFunctionProperties` schema extension method ([5003bbf](https://github.com/pjgm/serverless/commit/5003bbf983e7218c673a94a7042ca118aa0ae431)), closes [#8462](https://github.com/pjgm/serverless/issues/8462)
* **Config Schema:** Accept `accountId` as policy principal ([0f631f7](https://github.com/pjgm/serverless/commit/0f631f7bd17285c89bf73aa7da788186cebb2d05))
* **Config Schema:** Announce that crashing on error will become default ([6537a5e](https://github.com/pjgm/serverless/commit/6537a5e48dd4f6846f4ba41bb6c4542ea0c0117d)), closes [#9066](https://github.com/pjgm/serverless/issues/9066)
* **Config Schema:** Async invocations AWS functions[] schema ([#8385](https://github.com/pjgm/serverless/issues/8385)) ([719fa3a](https://github.com/pjgm/serverless/commit/719fa3a3bf8e5d5dfa135a8225519fc77b719c8e))
* **Config Schema:** AWS eventBridge schema validation ([#8114](https://github.com/pjgm/serverless/issues/8114)) ([796ce0b](https://github.com/pjgm/serverless/commit/796ce0b5ddaf893878912b5edeeec54718bf04ad))
* **Config Schema:** AWS HTTP API schema ([#8068](https://github.com/pjgm/serverless/issues/8068)) ([f091c07](https://github.com/pjgm/serverless/commit/f091c07992a414f2534c9de80caf76faf2744367))
* **Config Schema:** Configure schema for AWS `sns` event  ([#8112](https://github.com/pjgm/serverless/issues/8112)) ([87fd3c1](https://github.com/pjgm/serverless/commit/87fd3c17fb7d975b37c952293480bdc5ea4a8226))
* **Config Schema:** Deprecate `warn` as a validation mode default ([b408386](https://github.com/pjgm/serverless/commit/b40838630c18945bf00bf931bc98cf5fe6eac8c5))
* **Config Schema:** Filter out duplicate error messages ([e0bc57a](https://github.com/pjgm/serverless/commit/e0bc57ab1fee0a40a9e9278fa00eb2b851df2e55))
* **Config Schema:** Fix `cloudFront` event `behavior` schema ([#8308](https://github.com/pjgm/serverless/issues/8308)) ([5b740f6](https://github.com/pjgm/serverless/commit/5b740f6e1890b105e6aa7d931aed834dd30afb7e))
* **Config Schema:** Recognize `Fn::Transport` at `resoures.Resources` ([11a9d37](https://github.com/pjgm/serverless/commit/11a9d37f6e89d203b1bced2a30c89d40e9aae041)), closes [#8337](https://github.com/pjgm/serverless/issues/8337)
* **Config Schema:** Remove validation mode related deprecation ([a9bf916](https://github.com/pjgm/serverless/commit/a9bf916fbb15140373a54d22c624296b8a1dbe03))
* **Config Schema:** Schame for AWS `sqs` event ([#8227](https://github.com/pjgm/serverless/issues/8227)) ([4f96ce1](https://github.com/pjgm/serverless/commit/4f96ce1042079c08578ef70ddbb4c2def32d6663))
* **Config Schema:** Schema for  AWS `resources` section ([#8139](https://github.com/pjgm/serverless/issues/8139)) ([00d6f79](https://github.com/pjgm/serverless/commit/00d6f79c5022fd1bf1537d4095769916369d30ea))
* **Config Schema:** Schema for `functions[]` properties ([#8222](https://github.com/pjgm/serverless/issues/8222)) ([feece9a](https://github.com/pjgm/serverless/commit/feece9a2ec5be0f49af7147b84bed76e9ba50155))
* **Config Schema:** Schema for `layers` ([#8299](https://github.com/pjgm/serverless/issues/8299)) ([4168dc1](https://github.com/pjgm/serverless/commit/4168dc1f303148012f2027b6fbcbd686749a9357))
* **Config Schema:** Schema for `provider.logs.restApi` ([#8309](https://github.com/pjgm/serverless/issues/8309)) ([dd9a011](https://github.com/pjgm/serverless/commit/dd9a011f6073d33db9043f102e0cce84743a8a6b))
* **Config Schema:** Schema for `provider` props of AWS `http` event ([e51e0f2](https://github.com/pjgm/serverless/commit/e51e0f22da4625a65e5d7fd7bf3b4b1d5b46dd91)), closes [#8383](https://github.com/pjgm/serverless/issues/8383)
* **Config Schema:** Schema for AWS `alb` event ([#8291](https://github.com/pjgm/serverless/issues/8291)) ([c96b429](https://github.com/pjgm/serverless/commit/c96b429c6082f203e1cc06c2ae27a40a8a259bcd))
* **Config Schema:** Schema for AWS `alexaSkill` event ([#8290](https://github.com/pjgm/serverless/issues/8290)) ([7f47448](https://github.com/pjgm/serverless/commit/7f474481b60c545f3855efc7857474c4277413e0))
* **Config Schema:** Schema for AWS `alexaSmartHome` event ([#8255](https://github.com/pjgm/serverless/issues/8255)) ([bd5099e](https://github.com/pjgm/serverless/commit/bd5099e15019352ab5ae9b2cd5519eaff50c520e))
* **Config Schema:** Schema for AWS `cloudfront` event ([#8250](https://github.com/pjgm/serverless/issues/8250)) ([8943693](https://github.com/pjgm/serverless/commit/8943693c33359749d6685d867c01151cfd8000cf))
* **Config Schema:** Schema for AWS `cloudwatch` event ([#8230](https://github.com/pjgm/serverless/issues/8230)) ([3730fd4](https://github.com/pjgm/serverless/commit/3730fd4fd1ca3610415968e4633a0cba275b2e43))
* **Config Schema:** Schema for AWS `cloudwatchLog` event ([#8228](https://github.com/pjgm/serverless/issues/8228)) ([42676d3](https://github.com/pjgm/serverless/commit/42676d34d4cb33cb59fd54c6a78ed07c965146e5))
* **Config Schema:** Schema for AWS `http` event ([#8301](https://github.com/pjgm/serverless/issues/8301)) ([f235041](https://github.com/pjgm/serverless/commit/f235041d0b94e21cf07e11c4b818f44670ff39ae))
* **Config Schema:** Schema for AWS `provider` properties ([#8297](https://github.com/pjgm/serverless/issues/8297)) ([38c2047](https://github.com/pjgm/serverless/commit/38c204762cbe16b00d102fa71409c3c8ba22220b))
* **Config Schema:** Schema for AWS `s3` event ([#8330](https://github.com/pjgm/serverless/issues/8330)) ([61d8ee9](https://github.com/pjgm/serverless/commit/61d8ee9884cdee652fae131fed1e753301a351bf))
* **Config Schema:** Schema for AWS `schedule` event ([#8143](https://github.com/pjgm/serverless/issues/8143)) ([d9b91e9](https://github.com/pjgm/serverless/commit/d9b91e97fb81b6f19c9f95920b509d623bdca37d))
* **Config Schema:** Schema for AWS `stream` event ([#8201](https://github.com/pjgm/serverless/issues/8201)) ([1fb338b](https://github.com/pjgm/serverless/commit/1fb338b184ed770bc5d8d162bf5c54336f3d2ddd))
* **Config Schema:** Schema for AWS `websocket` event ([#8218](https://github.com/pjgm/serverless/issues/8218)) ([e1ca63c](https://github.com/pjgm/serverless/commit/e1ca63c06a824e18fdd92f5c6c3efbf7f5f644d2))
* **Config Schema:** Schema for AWS iot event ([#8177](https://github.com/pjgm/serverless/issues/8177)) ([e55fc36](https://github.com/pjgm/serverless/commit/e55fc36e1a3e78d155cbaaa5517c99ecc74a113f))
* **Config Schema:** Schema for Cognito Pool events ([#8105](https://github.com/pjgm/serverless/issues/8105)) ([184cb48](https://github.com/pjgm/serverless/commit/184cb48033ce92f771188c27c0ad3e541adab528))
* **Config Schema:** Validate extensions against collisions ([#8655](https://github.com/pjgm/serverless/issues/8655)) ([7266599](https://github.com/pjgm/serverless/commit/7266599a7dcfcb96cdfcb73a95c3d162fe6f3a1f))
* **ConfigSchema:** `defineFuntionEventProperties` schema extension method ([#8471](https://github.com/pjgm/serverless/issues/8471)) ([b5abfd8](https://github.com/pjgm/serverless/commit/b5abfd8554a2641ca92c16db4cdd20c08be4001e))
* Configure binaries generation ([49f6e1e](https://github.com/pjgm/serverless/commit/49f6e1e8a57929862c79b6fea90c7515469bca7c))
* Console Dev Mode onboarding via `dev` command ([#11896](https://github.com/pjgm/serverless/issues/11896)) ([73d0dc6](https://github.com/pjgm/serverless/commit/73d0dc6cf4e98d9c27f3fd6edb439d36e030c051))
* **Console:** dev mode onbaording via `dev` command ([#11782](https://github.com/pjgm/serverless/issues/11782)) ([a8f118b](https://github.com/pjgm/serverless/commit/a8f118bca12e30b974e6b0671df4dae7f50f9837))
* **Console:** External Console integration ([9a41468](https://github.com/pjgm/serverless/commit/9a414683090cb3edcac61d9a782c4d136f18c6f6))
* **Console:** In uneven scenario let user decide where to log-in ([0f21362](https://github.com/pjgm/serverless/commit/0f2136209199dad43410b0a71b2fa2c211a027a7))
* **Console:** Initial integration ([bdaf21e](https://github.com/pjgm/serverless/commit/bdaf21e1a1e839b7f2a2575cfeba741305080a92))
* **Console:** Rely on Console ready layers published to AWS ([f9bc405](https://github.com/pjgm/serverless/commit/f9bc4051844d1d54259216914fd28048d8749409))
* **Console:** Remove support for integrated configuration ([f3a1915](https://github.com/pjgm/serverless/commit/f3a191590b317a324198bfd2bf72601b136ed1e7))
* **Console:** Report org mismatch with a meaningful error ([ecaeb1f](https://github.com/pjgm/serverless/commit/ecaeb1f1bb210e8f6eced3011ce54ab854d23ff8))
* **Console:** Retain console properties on function deploy ([#11849](https://github.com/pjgm/serverless/issues/11849)) ([4ee5505](https://github.com/pjgm/serverless/commit/4ee5505b18bf6ca4ac83f411d76d71c45dc9fb18))
* **Console:** Support `console.org` setting ([3b3cfae](https://github.com/pjgm/serverless/commit/3b3cfae4986f0e022b8906ec59743482a5540068))
* **Console:** Support new user settings format ([21461b5](https://github.com/pjgm/serverless/commit/21461b5581bb759c259e82295fde952d907112b3))
* **Console:** Switch to new Identity system ([d40866a](https://github.com/pjgm/serverless/commit/d40866a0e845123ceecdd5b2b05e96e8dde09b04))
* **Dashboard:** Drop support for `tenant` ([e61674f](https://github.com/pjgm/serverless/commit/e61674f8dc2b367d2e215aa88b7e7360ac12eb1c))
* Deprecate `awsKmsKeyArn` in favor of `kmsKeyArn` ([#8277](https://github.com/pjgm/serverless/issues/8277)) ([a55009e](https://github.com/pjgm/serverless/commit/a55009e221de91fee46a343483eb31539352410b))
* Deprecate `service` object notation  ([#8466](https://github.com/pjgm/serverless/issues/8466)) ([c0a2ecf](https://github.com/pjgm/serverless/commit/c0a2ecf453fa82d46bf2fda34708864bc440203d))
* Deprecate an attempt to extend nonexistent resources ([#8266](https://github.com/pjgm/serverless/issues/8266)) ([0ced414](https://github.com/pjgm/serverless/commit/0ced414174c8acf7dd70dd9b5e4b7a525cd8320e))
* Deprecate Node.js v10 ([#9600](https://github.com/pjgm/serverless/issues/9600)) ([e24fdc9](https://github.com/pjgm/serverless/commit/e24fdc9f08f9849aad4136261695e44476484b0d))
* Detect Serverless CI/CD engine for analytics ([e20766c](https://github.com/pjgm/serverless/commit/e20766cf25e82442979662e0a415888f1727482a))
* Disallow custom nested configuration path ([fcd386b](https://github.com/pjgm/serverless/commit/fcd386b33b5ec130b086bd9b14719b71880612d9))
* Do not decorate `cli.log` logs ([30a3be8](https://github.com/pjgm/serverless/commit/30a3be8de7877d21f0ce64a706ac2b74babefe63))
* Do not retry AWS requests if the token has expired ([#9914](https://github.com/pjgm/serverless/issues/9914)) ([b0ca237](https://github.com/pjgm/serverless/commit/b0ca2376bbfb543d98db1585c3a20a391e1791c6))
* drastically improved dev dependency exclusion performance ([23c37b7](https://github.com/pjgm/serverless/commit/23c37b7543238e4a98ab605c2cf8146a3095bcce))
* Draw CLI boxes with `boxes` package ([80f9a65](https://github.com/pjgm/serverless/commit/80f9a6570fc139da1da7b0e53778d7fdc1ff507b))
* Drop support for Node.js versions below v10 ([69dd4b9](https://github.com/pjgm/serverless/commit/69dd4b97453a7ca34b541313d1063a1e0c1c7876))
* Enhance configuration options of cloudFront event ([#7170](https://github.com/pjgm/serverless/issues/7170)) ([9591d5a](https://github.com/pjgm/serverless/commit/9591d5a232c641155613d23b0f88ca05ea51b436)), closes [#7151](https://github.com/pjgm/serverless/issues/7151) [#6843](https://github.com/pjgm/serverless/issues/6843) [#6785](https://github.com/pjgm/serverless/issues/6785)
* Error instead of warning when missing "commands" or "options" ([33bd501](https://github.com/pjgm/serverless/commit/33bd501f06856a291de86cec8f921ae1bd1415c7))
* Expose `sls doctor` command ([3df6d15](https://github.com/pjgm/serverless/commit/3df6d1566458b8b7536def4d4253b7232e6d5118))
* Expose logDeprecation throuch which plugins may deprecate features ([f444a8d](https://github.com/pjgm/serverless/commit/f444a8d0a11434d89f1e2b2df5045850c45664c9))
* Extend `generatePayload` ([f6292b2](https://github.com/pjgm/serverless/commit/f6292b2d4912e04ff79b2565fd0a57ced47ca0c1))
* **iam:** use common prefix loggroup prefix to reduce size of iamRoleLambdaExecution to avoid reaching 10240 bytes limit ([c393d4b](https://github.com/pjgm/serverless/commit/c393d4b22c005f2982bdf461179cb01a9e905a94))
* Improve CLI messages when onboarding into Console ([cefb762](https://github.com/pjgm/serverless/commit/cefb7623355508aab0fdcbeaa8519c61c8bf6291))
* Improve performance of local invocation using docker ([#7178](https://github.com/pjgm/serverless/issues/7178)) ([f6d9bfd](https://github.com/pjgm/serverless/commit/f6d9bfd6c6bb5cd49ee67ce20e35e78090c18ab3))
* Improve the wording in the onboarding ([da15711](https://github.com/pjgm/serverless/commit/da157112031893873b140f5b89bed619ba5ba482))
* Improved dashboard documentation and gitignore ([#12176](https://github.com/pjgm/serverless/issues/12176)) ([eb462ed](https://github.com/pjgm/serverless/commit/eb462edc18de633bb0e479423babcbb43d4c3a33))
* Internal API to register service outputs ([b425cf1](https://github.com/pjgm/serverless/commit/b425cf1582623c1e796ae9f3d33dc060a9492cb5))
* Introduce `enforce-hash-update` flag to help hashing migration ([afd0a5b](https://github.com/pjgm/serverless/commit/afd0a5bd6f131c9b12148199d4995e055e5963f0))
* Introduce an opt-in "error" deprecation notification mode ([c22a8b9](https://github.com/pjgm/serverless/commit/c22a8b99f2f64a76c592e800a8cf698dbff75b9c))
* Introduce project directory setting, configurable via `projectDir` ([d6e4b49](https://github.com/pjgm/serverless/commit/d6e4b49ae28d5898d92b913a0d2c100bd29f4303))
* Linux & macOS binary installer ([f0f9698](https://github.com/pjgm/serverless/commit/f0f96980ee94727177f9306ab5bf31ac8e7e209b))
* **log:** Log AWS SDK calls in debug mode ([14c8af8](https://github.com/pjgm/serverless/commit/14c8af82469f0535da9940ccdad91fb7f9014dbd))
* Make dashboard monitoring opt-out ([#12138](https://github.com/pjgm/serverless/issues/12138)) ([45cbd52](https://github.com/pjgm/serverless/commit/45cbd525014ad3bf60aac3d482ec76ce68b51820))
* MaximumRetryAttempts config for stream ([998b6fd](https://github.com/pjgm/serverless/commit/998b6fd296f54d5a05f1609b29cc09fbc541935f)), closes [#7012](https://github.com/pjgm/serverless/issues/7012)
* Memoize resolution of dev deps exclusion paths ([#7091](https://github.com/pjgm/serverless/issues/7091)) ([5143c2a](https://github.com/pjgm/serverless/commit/5143c2ad3af84e198fb256b8cebf585aac3886e6))
* **methods:** Add custom codes support ([87a0bd3](https://github.com/pjgm/serverless/commit/87a0bd3b7e29e0fe8009bc18b097e70969c1b0df))
* **methods:** Add multiple response templates per content type ([d3c5d37](https://github.com/pjgm/serverless/commit/d3c5d37230a5ec4d11187b1291688b14b184e2e2))
* Opt-in auto update global installation ([e3f4546](https://github.com/pjgm/serverless/commit/e3f454680e528e51a61f4e203b5ec72e8947f0b1))
* Opt-in support for deployment bucket versioning ([#9912](https://github.com/pjgm/serverless/issues/9912)) ([c4cb0f3](https://github.com/pjgm/serverless/commit/c4cb0f30f5f565e2fd34877dfc383f6b81d135fd))
* **Packaging:** Deprecate `include` & `exclude` in favor of `patterns` ([e1678fb](https://github.com/pjgm/serverless/commit/e1678fb1c65ab0246e60d44857466be6771f889d)), closes [#8581](https://github.com/pjgm/serverless/issues/8581)
* **Packaging:** Deprecate `package.include` and `package.exclude` ([6201775](https://github.com/pjgm/serverless/commit/62017754f771c02478ac06e015db6767230b2fc3))
* **Packaging:** Remove `package[include|exclude]` deprecation ([70e2736](https://github.com/pjgm/serverless/commit/70e27362260f97b68bb1dfaf52fa3fe7877a2adc))
* **Plugins:** Announce "type" requirement in CLI option definitions ([959da67](https://github.com/pjgm/serverless/commit/959da67a5eb49f2256b4763f5f235537e6253659))
* **Plugins:** Fallback plugins search to global installation folder  ([82f6db7](https://github.com/pjgm/serverless/commit/82f6db7a1fcd27cd723b9100538355dd297774d5)), closes [#8038](https://github.com/pjgm/serverless/issues/8038)
* **Plugins:** Pass log writers to plugin constructor ([f9e6e2c](https://github.com/pjgm/serverless/commit/f9e6e2c4058f3bcf2a13f9a5b1c985d1d80e3146))
* **Plugins:** Support ESM format for plugins ([#10657](https://github.com/pjgm/serverless/issues/10657)) ([ec3271f](https://github.com/pjgm/serverless/commit/ec3271f3e8b7e055ad26eec89dfccfd3ca59fd0e))
* **Plugins:** Support variables in configuration extensions ([#11558](https://github.com/pjgm/serverless/issues/11558)) ([968ddd5](https://github.com/pjgm/serverless/commit/968ddd5994750a6d1677f195f7a86a823c558d16))
* Post deploy serverless dashboard integration ([#12063](https://github.com/pjgm/serverless/issues/12063)) ([66e3107](https://github.com/pjgm/serverless/commit/66e31077a71c61854db3246a50ddd2c1c303c110)), closes [#12059](https://github.com/pjgm/serverless/issues/12059)
* Recognise as standalone ([59bea09](https://github.com/pjgm/serverless/commit/59bea09dad12bd8484042e773e5a1c716aaec4a7))
* Recognize `ap-southeast-3` AWS region ([#10586](https://github.com/pjgm/serverless/issues/10586)) ([f77477e](https://github.com/pjgm/serverless/commit/f77477e3cc6c0c13749af1352d28b88cbadbeb6b))
* Recognize `eu-central-2`, `eu-south-1` and `me-central-1` regions ([54f4fc7](https://github.com/pjgm/serverless/commit/54f4fc73b4a2277c7485b877e57ec9ced6e66d1a)), closes [#11524](https://github.com/pjgm/serverless/issues/11524)
* Recognize `Fn::Base64` as CloudFormation instruction ([#11671](https://github.com/pjgm/serverless/issues/11671)) ([f020bd8](https://github.com/pjgm/serverless/commit/f020bd823905f012d2936a876e0ea841f5688883))
* Refactor constructor to accept new service configuration options ([c02cd06](https://github.com/pjgm/serverless/commit/c02cd06d907b7e54fb5a36ddbea8df1e4d29d897))
* Register service outputs ([312266e](https://github.com/pjgm/serverless/commit/312266e90819866199354183641954636bd5a076))
* Remove `@serverless/cli` CLI integration ([bdce13e](https://github.com/pjgm/serverless/commit/bdce13e36450ae5d3b2183df22e6f121e7ad6ea6))
* Remove `@serverless/components` CLI integration ([a4e5e5f](https://github.com/pjgm/serverless/commit/a4e5e5f3e32555c1fe2052e5fdcf822e0f95a437))
* Remove `ongoingRequestCount` counter ([010fa2c](https://github.com/pjgm/serverless/commit/010fa2ca8390d102ceaf57dd3b0ec73f4e1f480a))
* Remove `studio` command schema ([9912939](https://github.com/pjgm/serverless/commit/99129394320dad89f3ba2170767d24b2665d5112))
* Remove Console Login ([#12153](https://github.com/pjgm/serverless/issues/12153)) ([590bb7e](https://github.com/pjgm/serverless/commit/590bb7e17717253bfa37b1b511e5a6610c5657cb))
* Remove Dashboard onboarding from framework ([#12151](https://github.com/pjgm/serverless/issues/12151)) ([6ee277d](https://github.com/pjgm/serverless/commit/6ee277dfcb0d9055a3b20cbf493b1fd79b524fd2))
* Remove support for `provider.disableDefaultOutputExportNames` ([7474746](https://github.com/pjgm/serverless/commit/7474746a8eb34b9f4bf1b4a963ec1b23cac6e5f5))
* Remove support for Node v10 ([13e8ca6](https://github.com/pjgm/serverless/commit/13e8ca6f8307089fcd22dafa2055de336f6bb4b4))
* Remove support for object notation for `service` ([46e47d0](https://github.com/pjgm/serverless/commit/46e47d0225d26103ec5e5c131be16bf23de3238f))
* Remove support for Serverless Tencent CLI ([0a148b4](https://github.com/pjgm/serverless/commit/0a148b444c535df262bf79111066df03216f2f58))
* Remove tab autocomplete feature ([b4a25d7](https://github.com/pjgm/serverless/commit/b4a25d70d3ddc25ad94bed9a181692173e2a380c))
* Restrict stage name with pattern ([5374e04](https://github.com/pjgm/serverless/commit/5374e04503b0d01cf8d6979800b49a8de153537b))
* Schema based validation of service config ([#7335](https://github.com/pjgm/serverless/issues/7335)) ([268f714](https://github.com/pjgm/serverless/commit/268f714357ea909e6897d3377331ed7b1a38e5f5))
* Script to upload generated binaries to GitHub release ([5563b28](https://github.com/pjgm/serverless/commit/5563b284f265e20db5058922e65e08425e978efc))
* Seclude main error handler to standalone util ([847fa34](https://github.com/pjgm/serverless/commit/847fa3412d221c2ff98ab0cd9165bfc193c8a224))
* Send list of sevice npm dependencies for notifications generator ([dba0548](https://github.com/pjgm/serverless/commit/dba05481d10d0ffbf198990c9b460bb0b0ad24d2))
* Simplify `logs` command output ([38412ce](https://github.com/pjgm/serverless/commit/38412ce88bbc3cf9bc5c80a8e8a87fabc968e60e))
* **Standalone:** Allow to install specific versions ([#8858](https://github.com/pjgm/serverless/issues/8858)) ([019f0bf](https://github.com/pjgm/serverless/commit/019f0bf410c5c1c0ff0383221863cca171e1dcc9))
* **Standalone:** Prevent accidental upgrades to a new major ([56aa5aa](https://github.com/pjgm/serverless/commit/56aa5aa15abed64db6758aecd8c27719928b5a14))
* **Standalone:** Support China mirror for binary downloads ([8e85fe6](https://github.com/pjgm/serverless/commit/8e85fe611b4b4d619e0ad4fd347d669af6418634))
* **Standalone:** Support installation on M1-based Macs ([92ae054](https://github.com/pjgm/serverless/commit/92ae054f02dc631c178628492af7049ce2936204))
* **Standalone:** Support non-latest version builds ([92ebb18](https://github.com/pjgm/serverless/commit/92ebb18bdd08501899193944d2a7531514054a7d))
* **Standalone:** Upgrade `npm` to v8 ([96015a1](https://github.com/pjgm/serverless/commit/96015a11f6fc48c904714ba86582e7fbc0e15cfe))
* **Standalone:** Use Node 16 as base for binaries ([eb8f474](https://github.com/pjgm/serverless/commit/eb8f474940c4cd69f08ec062adfaa15d62d81ee2))
* **Standalone:** Windows Chocolatey PM integration ([85b196f](https://github.com/pjgm/serverless/commit/85b196ff4dd9fb64594bc1b362f882ee350dd01e))
* Suport `--context` and `--contextPath` at `invoke` command ([#8652](https://github.com/pjgm/serverless/issues/8652)) ([ff253e3](https://github.com/pjgm/serverless/commit/ff253e32dd5e9c17f46f5a359ebfb9007b6ffa7d))
* Support `.cjs` and `.mjs` configuration extensions ([#11586](https://github.com/pjgm/serverless/issues/11586)) ([9d57933](https://github.com/pjgm/serverless/commit/9d579336fadea1080f86f85e3fc304a102ab07f6))
* Support `destinations` config on stream events ([#7262](https://github.com/pjgm/serverless/issues/7262)) ([ea4ac26](https://github.com/pjgm/serverless/commit/ea4ac262ea4b9efdebc1fc357ffe906900295823))
* Support `error` hook to be triggered on command error ([5c9766c](https://github.com/pjgm/serverless/commit/5c9766c085531b04e169aa36a552159755029cca))
* Support `finalize` hook, triggered on command finalization ([cb4f08a](https://github.com/pjgm/serverless/commit/cb4f08ad7dd8eed3da69d61d51c6d5379a486bd0))
* Support `Fn::Split` for `vpc` properties ([#9266](https://github.com/pjgm/serverless/issues/9266)) ([19805d7](https://github.com/pjgm/serverless/commit/19805d71eabb68bd7fd4046aa23090ef85fb1c36))
* Support `Fn::ToJsonString` in environment variables ([#11461](https://github.com/pjgm/serverless/issues/11461)) ([0c186a6](https://github.com/pjgm/serverless/commit/0c186a608fd1a754a65abf63e431ad9c2d13534e))
* Support `kmsKeyArn` for `deploy function` ([8a92be9](https://github.com/pjgm/serverless/commit/8a92be9be37b554c0e1ec95f5d040ecc5b2d63cc))
* Support `mainProgressTitles` config on commands schema ([fd68f9e](https://github.com/pjgm/serverless/commit/fd68f9e8038a9ac253bdf47816703edefe0de28e))
* Support `managedExternally` option for authorizers ([#7327](https://github.com/pjgm/serverless/issues/7327)) ([7abb23e](https://github.com/pjgm/serverless/commit/7abb23edc8dfbe5005ac716aa137330741759929))
* Support `params` configuration ([bd50628](https://github.com/pjgm/serverless/commit/bd506286ad931c0cc22b2dd8b96615ea87d1918a))
* Support `provider.rolePermissionsBoundary` to set IAM boundary ([#7319](https://github.com/pjgm/serverless/issues/7319)) ([09466b5](https://github.com/pjgm/serverless/commit/09466b5a172a743b1c2d5c1045c08f5c2ad32a2e))
* Support `provider.stackParameters` ([#7677](https://github.com/pjgm/serverless/issues/7677)) ([a0a43a6](https://github.com/pjgm/serverless/commit/a0a43a68f339f6995937a0743fe042e9e11784f9))
* Support `resource.extensions` for safe resource extensions ([#7352](https://github.com/pjgm/serverless/issues/7352)) ([08ec261](https://github.com/pjgm/serverless/commit/08ec261a3cd34e7225f471cbeab8cef605ac61fc))
* Support BisectBatchOnFunctionError option on event streams ([#7105](https://github.com/pjgm/serverless/issues/7105)) ([560ceee](https://github.com/pjgm/serverless/commit/560ceee5b3abf90999c61074b8a94d5ef31e967b))
* Support CF instructions in awsKmsKeyArn setting ([#7083](https://github.com/pjgm/serverless/issues/7083)) ([f9b6507](https://github.com/pjgm/serverless/commit/f9b650782539808e796c1544a9dc7f2d02603db1))
* Support Cloud Components ([#7390](https://github.com/pjgm/serverless/issues/7390)) ([0ed52f6](https://github.com/pjgm/serverless/commit/0ed52f61de98101fd570bc6e7794a74ab7afa0ff))
* Support deploymentBucket.maxPreviousDeploymentArtifacts customization ([#7283](https://github.com/pjgm/serverless/issues/7283)) ([0241468](https://github.com/pjgm/serverless/commit/024146885a913f545ebf8b0f5f6734b7650c64cc))
* Support Kinesis Enhanced Fan-out (Consumer) streams ([#7320](https://github.com/pjgm/serverless/issues/7320)) ([9eba218](https://github.com/pjgm/serverless/commit/9eba2187f9565b39d31e88572c06ea2ccaa4bade))
* Support new analytics and notifications backend ([49b5914](https://github.com/pjgm/serverless/commit/49b5914378038a9a35433e40233e9f49acd0e964))
* Support provider.alb.targetGroupPrefix setting ([#7322](https://github.com/pjgm/serverless/issues/7322)) ([3910df1](https://github.com/pjgm/serverless/commit/3910df1ba6a8b39367ce8d51adb90216251be2ba))
* Support RedrivePolicy configuration on SNS events ([#7239](https://github.com/pjgm/serverless/issues/7239)) ([4f27378](https://github.com/pjgm/serverless/commit/4f273785f4b7cceaffd2fb6b9255e4187962d53c))
* Support rich and reusable S3 buckets configuration ([#7156](https://github.com/pjgm/serverless/issues/7156)) ([382c0bf](https://github.com/pjgm/serverless/commit/382c0bfc21b98fdadb8ad86340a97f6cc18ce84d))
* support RollbackConfiguration in service config ([#7193](https://github.com/pjgm/serverless/issues/7193)) ([5973c9f](https://github.com/pjgm/serverless/commit/5973c9fd58631beaea45047345cac8d348e93911))
* Support serverless.ts as configuration input ([#7755](https://github.com/pjgm/serverless/issues/7755)) ([4db8b63](https://github.com/pjgm/serverless/commit/4db8b630a285d40b117d7043f024cb3e036951b4))
* Support tweaking max concurrent artifcat uploads count ([#7295](https://github.com/pjgm/serverless/issues/7295)) ([0592a27](https://github.com/pjgm/serverless/commit/0592a27dbc084eb9b96791f24c1ef636395e42dc))
* **Telemetry:** Add `commandDurationMs` to payload ([d647125](https://github.com/pjgm/serverless/commit/d647125ff5daa07972675fd28690d42746ab223b))
* **Telemetry:** Add `commandOptionNames` to payload ([f5b2b9b](https://github.com/pjgm/serverless/commit/f5b2b9be395c9c2d3de4c4f91f991276bc22dc33))
* **Telemetry:** Add `hasLocalCredentials` ([5e0d805](https://github.com/pjgm/serverless/commit/5e0d80579e857d016fb4db13288b9d81a3859ee1))
* **Telemetry:** Add `projectId` to payload ([cc7d7e4](https://github.com/pjgm/serverless/commit/cc7d7e4d531090e81bf08842433397588d00afce))
* **Telemetry:** Adjust generatePayload for service-agnostic command ([cde1e54](https://github.com/pjgm/serverless/commit/cde1e54878e37937db377cec2a3cc5382cdf5788))
* **Telemetry:** Allow to disable telemetry via `SLS_TELEMETRY_DISABLED` ([ba7fd2e](https://github.com/pjgm/serverless/commit/ba7fd2e1b428b2b76378aa90d0a19e8ec0d12498))
* **Telemetry:** Detect used variable sources ([60d729b](https://github.com/pjgm/serverless/commit/60d729b5d42ae32cc418b9578582da3dc8492754))
* **Telemetry:** Do not report telemetry for help commands ([d81730c](https://github.com/pjgm/serverless/commit/d81730c219c70cd11d04a23ee217c4af3b320985))
* **Telemetry:** Do not send `request` during `storeLocally` ([5be1fd0](https://github.com/pjgm/serverless/commit/5be1fd04865abcc40ee74b61e0e48207654fbd69))
* **Telemetry:** Handle interruptions and persist telemetry data ([502f7e7](https://github.com/pjgm/serverless/commit/502f7e711f0954c2960fb790b749002aeb1789fc))
* **Telemetry:** Inspect `docker` availability ([83670f9](https://github.com/pjgm/serverless/commit/83670f98c54b71670d0f6d677b1f23b0fb5200ce))
* **Telemetry:** Record all commands and send only on deploy ([d3ecb7c](https://github.com/pjgm/serverless/commit/d3ecb7cc3b95853b9ad7c1574a0c8fcbc6d08007))
* **Telemetry:** Record initial context for interactive setup ([560aee5](https://github.com/pjgm/serverless/commit/560aee5feb9f143e93933f6536e76edc9a3e56bb))
* **Telemetry:** Remove `send` invocation from `serverless` script ([cbc4627](https://github.com/pjgm/serverless/commit/cbc4627dfe32ec5eb31e52852ccd8f6e9594e560))
* **Telemetry:** Report `configValidationMode` ([8e2d48f](https://github.com/pjgm/serverless/commit/8e2d48fee5a471a960b6a7b55cbd12edc5eb07e6))
* **Telemetry:** Report `didCreateService` property ([4fa20a5](https://github.com/pjgm/serverless/commit/4fa20a56eafcab9d8675baa2f0fe6a9c6ee5e184))
* **Telemetry:** Report `projectId` in remove command ([0de3bc3](https://github.com/pjgm/serverless/commit/0de3bc3cb9c1685226ea0c610e030f9279e79e4e))
* **Telemetry:** Report awsUserResourceTypes ([8d0ff07](https://github.com/pjgm/serverless/commit/8d0ff078f7f0b565c1d35af1319f76a407afeb4b))
* **Telemetry:** Report configuration validation result ([01f1586](https://github.com/pjgm/serverless/commit/01f158695b22d721320a77a9a0b68b166c63dc3f))
* **Telemetry:** Report failures via telemetry ([5861d08](https://github.com/pjgm/serverless/commit/5861d08768a06e2e88609d0785ce590d3f693683))
* **Tempates:** Upgrade `log4j` in Java based templates ([#10363](https://github.com/pjgm/serverless/issues/10363)) ([7de020b](https://github.com/pjgm/serverless/commit/7de020bbadad0aed47859f2129c9e58409b9ac65))
* **Templates:** Add `aws-kotlin-jvm-gradle-kts` template ([#7992](https://github.com/pjgm/serverless/issues/7992)) ([4727216](https://github.com/pjgm/serverless/commit/4727216760e16d5a11402f74fdcf38c70a8634be))
* **Templates:** Add `google-nodejs-typescript` template ([#9445](https://github.com/pjgm/serverless/issues/9445)) ([9cc05ad](https://github.com/pjgm/serverless/commit/9cc05ad2f659709746d1df9811b95118c583db27))
* **Templates:** Add `package.json` to `plugin` template ([410f0ec](https://github.com/pjgm/serverless/commit/410f0ec3b5f09f9bef22d14fcaccbb8bd6e70460))
* **Templates:** Add a simple README for `plugin` template ([769214c](https://github.com/pjgm/serverless/commit/769214cb2a234968fd2e76391fdcebb179cfddab))
* **Templates:** Add aws-nodejs-docker template ([1a0390b](https://github.com/pjgm/serverless/commit/1a0390b59722d84e87595bc462c83b6baf214da1))
* **Templates:** Add aws-python-docker template ([fd9b26a](https://github.com/pjgm/serverless/commit/fd9b26a9e898685da81663064274250c5771363c))
* **Templates:** Add node version constraint to aws-nodejs-typescript ([37d5f9e](https://github.com/pjgm/serverless/commit/37d5f9e74024b54955eb4d503edfefcaf0b03444))
* **Templates:** Azure C# template ([#7738](https://github.com/pjgm/serverless/issues/7738)) ([9611137](https://github.com/pjgm/serverless/commit/96111379823fc1fc68835b9bcdb4f0f585ff554e))
* **Templates:** Ensure "frameworkVersion" in all templates ([3089abc](https://github.com/pjgm/serverless/commit/3089abc5c48335375ed8f9a67814e3b4cf82f53d))
* **Templates:** Improve source maps handling in `aws-nodejs-typescript` ([28d230f](https://github.com/pjgm/serverless/commit/28d230f946df6cbcc8173822494b50cd056ef63c)), closes [#9961](https://github.com/pjgm/serverless/issues/9961)
* **Templates:** Improve TypeScript template ([#7934](https://github.com/pjgm/serverless/issues/7934)) ([5e322c8](https://github.com/pjgm/serverless/commit/5e322c87358cd33e7c703ae3ab5e9f1cf863c7e1))
* **Templates:** Package lambdas individually in `aws-nodejs-typescript` ([3aab5f8](https://github.com/pjgm/serverless/commit/3aab5f86985598d6bb3135f4ab934092ad467df5))
* **Templates:** Support ssh format download template urls ([#7588](https://github.com/pjgm/serverless/issues/7588)) ([d3bf39a](https://github.com/pjgm/serverless/commit/d3bf39aa05f861cc8dc5115b1a7350af3b1916d9))
* **Templates:** Support TS path mapping in `aws-nodejs-typescript` ([e050440](https://github.com/pjgm/serverless/commit/e0504406ea8c70e2c42363bef9da468899a0ca03)), closes [#8968](https://github.com/pjgm/serverless/issues/8968)
* **Templates:** Switch to esbuild in `aws-nodejs-typescript` ([#9962](https://github.com/pjgm/serverless/issues/9962)) ([aaabb50](https://github.com/pjgm/serverless/commit/aaabb50f1beb12683506ca7ab9e93ded75294694))
* **Templates:** Update `aws-nodejs-typescript` for `nodejs14.x` ([5fa51dc](https://github.com/pjgm/serverless/commit/5fa51dc53d039814aef80dd2a8c8069015215696))
* **Templates:** Update `ts-node` for es2020 and es2021 support ([e131609](https://github.com/pjgm/serverless/commit/e13160902848912a6bb652299d1bc6107cf09eb1))
* **Templates:** Update aws-csharp to .NET Core 3.1 ([#7708](https://github.com/pjgm/serverless/issues/7708)) ([46df82e](https://github.com/pjgm/serverless/commit/46df82ea92ced3ba7542f6de5da6cfda73554ffc))
* **Templates:** Update aws-fsharp to netcoreapp3.1 ([#7709](https://github.com/pjgm/serverless/issues/7709)) ([a5a136f](https://github.com/pjgm/serverless/commit/a5a136f982f19043cf4cf3236db1ac2d17c8a266))
* **Templates:** Update aws-nodejs-typescript template ([#8646](https://github.com/pjgm/serverless/issues/8646)) ([c9db035](https://github.com/pjgm/serverless/commit/c9db035266db23518011a4b7457319add0c00994))
* **Templates:** Update dependencies for `cloudflare` template ([#9373](https://github.com/pjgm/serverless/issues/9373)) ([543423d](https://github.com/pjgm/serverless/commit/543423d869ba35c6866506bb49a8642700214b3a))
* **Templates:** Update dependencies in `aws-java-maven` ([#10289](https://github.com/pjgm/serverless/issues/10289)) ([0714f7d](https://github.com/pjgm/serverless/commit/0714f7df0642d7a900c9d72eb26ae8c5ae1eddd7))
* **Templates:** Upgrade `aws-nodejs-typescript` template ([#8496](https://github.com/pjgm/serverless/issues/8496)) ([786809e](https://github.com/pjgm/serverless/commit/786809e262b56490a78a923b0b031378badb18c0))
* **Templates:** Upgrade `azure-nodejs-typescript` ([#10163](https://github.com/pjgm/serverless/issues/10163)) ([26846d5](https://github.com/pjgm/serverless/commit/26846d5879d655ffe299db694a33f1f6d187a941))
* **Templates:** Upgrade `log4j` dependencies ([#10392](https://github.com/pjgm/serverless/issues/10392)) ([86fa604](https://github.com/pjgm/serverless/commit/86fa60445c83cf35f3411ae49c2a1c4fc7fd82f0))
* **Templates:** Upgrade `log4j` in Java based templates ([#10339](https://github.com/pjgm/serverless/issues/10339)) ([c1df4f8](https://github.com/pjgm/serverless/commit/c1df4f860a585ff62c364ac8fd6d8b64b323b156))
* **Templates:** Upgrade azure-nodejs template ([#7918](https://github.com/pjgm/serverless/issues/7918)) ([a88cf00](https://github.com/pjgm/serverless/commit/a88cf00ae7d306341771d9445f3aba6f06d46fa7))
* **Templates:** Upgrade google-nodejs template ([#8152](https://github.com/pjgm/serverless/issues/8152)) ([40fb8ae](https://github.com/pjgm/serverless/commit/40fb8ae1123b4f898ff008602242d5b5bba24b6b))
* **Templates:** Upgrade gradle-wrapper and gradle ([#7972](https://github.com/pjgm/serverless/issues/7972)) ([6da0964](https://github.com/pjgm/serverless/commit/6da09649bb6cbc9074d5dec574856acc8eaa388d))
* **Templates:** Upgreate nodejs-typescript template ([#8543](https://github.com/pjgm/serverless/issues/8543)) ([fef389b](https://github.com/pjgm/serverless/commit/fef389b770a3f09431aa761dc98da8cd384eec3f))
* **Templates:** Use `iam.role` syntax in templates ([a55d51c](https://github.com/pjgm/serverless/commit/a55d51c6a4aa38153f61192d374cb23bf09ff66c))
* Temporarily revert `dev` command ([#11854](https://github.com/pjgm/serverless/issues/11854)) ([0f930c5](https://github.com/pjgm/serverless/commit/0f930c51c429ad2e93148f5140fef598b69b7050))
* Throw error on duplicated plugin definition ([b24ab3c](https://github.com/pjgm/serverless/commit/b24ab3c0590e37597dbed533778f5d4d0bad1806))
* Throw for `--aws-s3-accelerate` when custom bucket used ([98848ab](https://github.com/pjgm/serverless/commit/98848ab4fc8ff7232fb6a9974388d252b34c92c4))
* Unconditionally display browser url ([c900900](https://github.com/pjgm/serverless/commit/c90090048847c4280081a7b7fb1a8c3171cc7771))
* Unconditionally fallback when local installation found ([d62c328](https://github.com/pjgm/serverless/commit/d62c3288b28c952702e18ea7bb8f31b1f2489b2b))
* Update and improve aws-kotlin-jvm-gradle template ([#7072](https://github.com/pjgm/serverless/issues/7072)) ([0b3a08a](https://github.com/pjgm/serverless/commit/0b3a08afaaf520fe6c3d4ebaac1a12fbd83c1fe4))
* Update to Node 14 for standalone binaries ([5cc3be1](https://github.com/pjgm/serverless/commit/5cc3be15be83b5358b78fccc9ef7e7f2a3bed45d))
* Upgrade to @serverless/dashboard-plugin ([#12157](https://github.com/pjgm/serverless/issues/12157)) ([f057629](https://github.com/pjgm/serverless/commit/f057629cbebf07f3415ef996ecbc10c7c7b866d4))
* **Variables:** "env" source configuration for new resolver ([d052206](https://github.com/pjgm/serverless/commit/d052206cb317358227fe68c833d2eb3eb3fdd848))
* **Variables:** "file" source configuration for new resolver ([238d002](https://github.com/pjgm/serverless/commit/238d002006461efde9769cd6512f0ded5374179a))
* **Variables:** "opt" source configuration for new resolver ([99f5014](https://github.com/pjgm/serverless/commit/99f5014fa39e2f11b24daa445e70144e4ade5a81))
* **Variables:** "self" source configuration for new resolver ([3b7b177](https://github.com/pjgm/serverless/commit/3b7b17718f6e3422e0022f327ae335751c692840))
* **Variables:** "strToBool" source configuration for new resolver ([4d134d8](https://github.com/pjgm/serverless/commit/4d134d828b4bf78c1c128f6db19d835163f37da1))
* **Variables:** `serviceDir` option as replacement for `servicePath` ([712a569](https://github.com/pjgm/serverless/commit/712a569d5258f7770d4c23d8f0803c3d0062b79e))
* **Variables:** `sls:stage` variable ([#9296](https://github.com/pjgm/serverless/issues/9296)) ([ef91ae1](https://github.com/pjgm/serverless/commit/ef91ae1972448fd342aeda6189884f2d8b454756))
* **Variables:** Accept case-insensitive strings in `strToBool` ([#9770](https://github.com/pjgm/serverless/issues/9770)) ([612f668](https://github.com/pjgm/serverless/commit/612f668c931013bea21b91f47d9cbfd1c7dbb888))
* **Variables:** Add support for `csj` in `file` source ([#10776](https://github.com/pjgm/serverless/issues/10776)) ([df08283](https://github.com/pjgm/serverless/commit/df0828381057b7edb2731f3763c2d60eed126d8a))
* **Variables:** Add support for Terraform state file parsing ([#8755](https://github.com/pjgm/serverless/issues/8755)) ([461a396](https://github.com/pjgm/serverless/commit/461a3965a52eb9707121700608dc8bdbafc367d1))
* **Variables:** Allow to reference files in scope of project directory ([8dbb56e](https://github.com/pjgm/serverless/commit/8dbb56ecbda2c6b8e8eaccbba7c7842ba8382847))
* **Variables:** Communicate not accessible "provider" properties ([e5307b0](https://github.com/pjgm/serverless/commit/e5307b05d31b7a80be80fc72e1829aead8762680))
* **Variables:** Disallow `provider.variableSyntax` with new resolver ([5a2da44](https://github.com/pjgm/serverless/commit/5a2da444ea5f896f56cf03e509631d2df548457c))
* **Variables:** Ensure support for promise properties at `file` source ([8dae213](https://github.com/pjgm/serverless/commit/8dae21375801be00f24d68d6a3e12854132b7bb9))
* **Variables:** Expose variable resolver function to variable sources ([2ff58b1](https://github.com/pjgm/serverless/commit/2ff58b16bf3fe766685d5b6c30fd9a2bb6e22f0f))
* **Variables:** First phase of variables resolution ([1ccb19b](https://github.com/pjgm/serverless/commit/1ccb19b43a37f332368654babeb53f5840f3e3a2))
* **Variables:** For `--help` output resolve just needed properties ([d851914](https://github.com/pjgm/serverless/commit/d851914a44cc0f0a7bb6c4bf7dd2454b6f83189c))
* **Variables:** Introduce unresolvedVariablesNotificationMode ([#8710](https://github.com/pjgm/serverless/issues/8710)) ([33cffc3](https://github.com/pjgm/serverless/commit/33cffc3509255663c9ab94f3cd38f115d71bd1d2))
* **Variables:** Meaningfully reject not resolvable `provider.name` ([f67d95a](https://github.com/pjgm/serverless/commit/f67d95a553be8986b8b21c164f9d292f4fca21cd))
* **Variables:** New parser and resolver implementation ([fb2c425](https://github.com/pjgm/serverless/commit/fb2c425ed2869d7faab4ae52cb001785aa389a40))
* **Variables:** Recognize `:` in address to support `output` source ([723927f](https://github.com/pjgm/serverless/commit/723927f2dcdcc425025da03ac0be5edd3c203dc7))
* **Variables:** Recognize CLI command plugin extensions in new resolver ([3422a12](https://github.com/pjgm/serverless/commit/3422a121d787fa716f708051f0bfe97644a3c1aa))
* **Variables:** Remove old variables resolver ([731b3ba](https://github.com/pjgm/serverless/commit/731b3ba1e14dc5be5ba99b72127bfb6327d2918b))
* **Variables:** Report errors on unresolved variables ([f112e4b](https://github.com/pjgm/serverless/commit/f112e4b91c140d915cee493b24b66f94b8033d3d))
* **Variables:** Resign from `projectDir` concept ([5a76437](https://github.com/pjgm/serverless/commit/5a764373c49d5fb313f50218ab8166f1638c2c32))
* **Variables:** Resolve vars in strings which are subject to be joined ([0e3db01](https://github.com/pjgm/serverless/commit/0e3db01db8aeb08b03a98dd7f58a09b66ec8c49e))
* **Variables:** Support `aws:region` and `aws:accountId` variables ([33794ea](https://github.com/pjgm/serverless/commit/33794ea504e714912137796009c29c802f2e24f0))
* **Variables:** Support boolean and integer fallbacks ([#7632](https://github.com/pjgm/serverless/issues/7632)) ([f22bffc](https://github.com/pjgm/serverless/commit/f22bffc2b49e0badef8a3253478337808222964c))
* **Variables:** Support for `--param` CLI options ([964b883](https://github.com/pjgm/serverless/commit/964b8834554e4607fa68f4460cab995af1352746))
* **Variables:** Support non-function exports in js files ([#7540](https://github.com/pjgm/serverless/issues/7540)) ([89ba272](https://github.com/pjgm/serverless/commit/89ba272a63a153df0655c85a5d5a2487580c73a1))
* **Variables:** Support region selection of SSM variables ([#7625](https://github.com/pjgm/serverless/issues/7625)) ([7d3636f](https://github.com/pjgm/serverless/commit/7d3636f9682c7c9929a9061f105ed232d139aa56))
* **Variables:** Support source extensions from plugins for new resolver ([ee76876](https://github.com/pjgm/serverless/commit/ee7687672557125b68a300f0cb1f7d8ec1785ec4))
* **Variables:** Support variables across file address resolution ([80b7640](https://github.com/pjgm/serverless/commit/80b76406ac305ccb7e55cabd0bd39be6ac7c67c6))


### Bug Fixes

* [#1973](https://github.com/pjgm/serverless/issues/1973) deploy fails with unhelpful error message when service name is not a valid CF stack name ([478209b](https://github.com/pjgm/serverless/commit/478209bfa6025248a1ef949f940a20fc80cca316))
* [#1973](https://github.com/pjgm/serverless/issues/1973) deploy fails with unhelpful error message when service name is not a valid CF stack name ([eaf175d](https://github.com/pjgm/serverless/commit/eaf175da06f52753fe4051c259f34a8da6b4d370))
* [#1973](https://github.com/pjgm/serverless/issues/1973) deploy fails with unhelpful error message when service name is not a valid CF stack name ([b8e5bb4](https://github.com/pjgm/serverless/commit/b8e5bb4eca1b9d92e263e580b484b9efbbc7b8cf))
* [#1973](https://github.com/pjgm/serverless/issues/1973) deploy fails with unhelpful error message when service name is not a valid CF stack name ([dbeaa54](https://github.com/pjgm/serverless/commit/dbeaa54832983a09b3940e4d9edd8f4e95249e00))
* [#1973](https://github.com/pjgm/serverless/issues/1973) deploy fails with unhelpful error message when service name is not a valid CF stack name ([73617d0](https://github.com/pjgm/serverless/commit/73617d0a66d7a4cd390eff9a4ac00b036df0575c))
* Add source account to lambda permissions for s3 events ([#7417](https://github.com/pjgm/serverless/issues/7417)) ([7d67f33](https://github.com/pjgm/serverless/commit/7d67f33b085c29ce0e57431629e33e657b93c474))
* Adjust copy for clarity ([#12162](https://github.com/pjgm/serverless/issues/12162)) ([101ce53](https://github.com/pjgm/serverless/commit/101ce53c18bae3709d5cc70a483cce81206752ec))
* Adjust providers endpoint ([#12154](https://github.com/pjgm/serverless/issues/12154)) ([9b770a2](https://github.com/pjgm/serverless/commit/9b770a27dc0a093d05d36e58f077b3a527565718)), closes [#12151](https://github.com/pjgm/serverless/issues/12151)
* Allow S3 event rule prefix and suffix to use CF functions ([#11018](https://github.com/pjgm/serverless/issues/11018)) ([0279e1e](https://github.com/pjgm/serverless/commit/0279e1eb9d79abce52c595b3cde190ff96599e42))
* **Analytics:** Ensure to send payload when having all meta ([03859c0](https://github.com/pjgm/serverless/commit/03859c04720f9071d0590b5d0ad1fa0e2c6770b3))
* **API:** Bring back legacy `service.serviceFilename` for plugins ([6c896a5](https://github.com/pjgm/serverless/commit/6c896a5ffdfc067ffded0791a34a943c89ea6136))
* **API:** Ensure `config.servicePath` is `config.serviceDir` live alias ([2967065](https://github.com/pjgm/serverless/commit/2967065bc7e45d7b0f0fac4ad9b9c33b977482fa))
* **API:** Ensure `serverless.config.servicePath` ([ff589ba](https://github.com/pjgm/serverless/commit/ff589baef483ecd53d9d4301bf2e846d87d62224)), closes [#9307](https://github.com/pjgm/serverless/issues/9307)
* Avoid re-registration of `ts-node` ([#9254](https://github.com/pjgm/serverless/issues/9254)) ([88baf06](https://github.com/pjgm/serverless/commit/88baf06b42d4c08f3034965b8a7ffa23455ae3e3))
* **AWS ALB:** Allow multiple http-header conditions ([#11888](https://github.com/pjgm/serverless/issues/11888)) ([72b27cb](https://github.com/pjgm/serverless/commit/72b27cb4fe0e17bf980fcc441808f4db6939e545))
* **AWS ALB:** Conform to CF schema with multiple host header ([#8965](https://github.com/pjgm/serverless/issues/8965)) ([36c78c7](https://github.com/pjgm/serverless/commit/36c78c70d1cf306556a5a9f8a3c3908e8b4c7d05))
* **AWS ALB:** Ensure to treat `provider.alb.authorizers` as optional ([e990c09](https://github.com/pjgm/serverless/commit/e990c09edb8fb711152485bed46dfefd827ac92d))
* **AWS ALB:** Fix handling of provisioned concurrency ([#7285](https://github.com/pjgm/serverless/issues/7285)) ([3138ef1](https://github.com/pjgm/serverless/commit/3138ef1771a31a52429777241f67dcf07a69bebd))
* **AWS ALB:** Recognize CIDR format at `ip` configuration ([#11889](https://github.com/pjgm/serverless/issues/11889)) ([04db0f0](https://github.com/pjgm/serverless/commit/04db0f045c3d6e3772ef9f82ca4d51ac1aa5bbb8))
* **AWS Alexa:** Ensure to log deprecation at initialization stage ([a5a1a23](https://github.com/pjgm/serverless/commit/a5a1a230a5714fc2859773077d57eba6d654af74))
* **AWS API Gateway:** Apply contentHandling only to successful responses ([aa48f0a](https://github.com/pjgm/serverless/commit/aa48f0a0766fc07e6e3ca4bb7ba4b6ad3427cc03)), closes [#7757](https://github.com/pjgm/serverless/issues/7757)
* **AWS API Gateway:** Correctly construct resource name for schema ([0a0f6c6](https://github.com/pjgm/serverless/commit/0a0f6c6102b3cb8921ef7448d5b3a8f1294b6802))
* **AWS API Gateway:** Correctly recognize `type` for `authorizerId` ([ef25d68](https://github.com/pjgm/serverless/commit/ef25d681372d1ef16cdba24981a41eb957e59821))
* **AWS API Gateway:** Correctly set `throttle` when `quota` missing ([4a30bb1](https://github.com/pjgm/serverless/commit/4a30bb1e5b36b52207e1bd3f3fc37e12878fb3b3))
* **AWS API Gateway:** Create one request validator and reuse ([#9319](https://github.com/pjgm/serverless/issues/9319)) ([154351f](https://github.com/pjgm/serverless/commit/154351f1a5925a745873895014ed31f03b2842b3))
* **AWS API Gateway:** Deprecate invalid `apiGateway` settings ([#9238](https://github.com/pjgm/serverless/issues/9238)) ([bca46e5](https://github.com/pjgm/serverless/commit/bca46e5ab509065e6b3b2031446593ac23aac261))
* **AWS API Gateway:** Do not attempt to remove `aws:` tags during update ([dac06c8](https://github.com/pjgm/serverless/commit/dac06c8ce644f0d219329474cb83c644ca61d880))
* **AWS API Gateway:** Dont create logGroup if logs disabled ([a116dfe](https://github.com/pjgm/serverless/commit/a116dfec22697dd0511623c6a1e6d2d829d4ba10))
* **AWS API Gateway:** Ensure `MinimumCompressionSize` can be 0 ([#9806](https://github.com/pjgm/serverless/issues/9806)) ([f0ae032](https://github.com/pjgm/serverless/commit/f0ae032252f88d4d864c2bfe526d70064168231a))
* **AWS API Gateway:** Ensure `shouldStartNameWithService` support ([e8c8d25](https://github.com/pjgm/serverless/commit/e8c8d259fb79ae04e33e01af162c6666f0060189))
* **AWS API Gateway:** Ensure consistent default for `cors` conf ([#9909](https://github.com/pjgm/serverless/issues/9909)) ([7cd3966](https://github.com/pjgm/serverless/commit/7cd3966897fa4432caf3f2bda0037df0c76e382b))
* **AWS API Gateway:** Ensure correct type for StatusCode property  ([#7977](https://github.com/pjgm/serverless/issues/7977)) ([d0edb5d](https://github.com/pjgm/serverless/commit/d0edb5d85991bd6563610c768da80e0791735bc8))
* **AWS API Gateway:** Ensure proper `apiId` resolution ([95f3a56](https://github.com/pjgm/serverless/commit/95f3a5603897ad43ba6e008a7ea2a35d21a4eacf))
* **AWS API Gateway:** Ensure proper `RequestValidator` name ([510b1d1](https://github.com/pjgm/serverless/commit/510b1d165924d000aa8e81e74e27c69ac1a2e0b6))
* **AWS API Gateway:** Ensure that `method` depends on `permission` ([93b9027](https://github.com/pjgm/serverless/commit/93b9027f0d48650df50d0a8352d0edaf2bd2e0da))
* **AWS API Gateway:** Ensure to attach validator when required ([#9793](https://github.com/pjgm/serverless/issues/9793)) ([d275459](https://github.com/pjgm/serverless/commit/d2754594c462afd39e1576312e361ca57d4f13f2))
* **AWS API Gateway:** Ensure to log deprecation at initialization stage ([b6d033a](https://github.com/pjgm/serverless/commit/b6d033a044e722f9cd0bd751c4067bf05aa50558))
* **AWS API Gateway:** Ensure to update stage only for deployed API's ([81953ef](https://github.com/pjgm/serverless/commit/81953ef74c0c80256d8f8235df0bbb4fc8eeb1b9)), closes [#6699](https://github.com/pjgm/serverless/issues/6699) [#7186](https://github.com/pjgm/serverless/issues/7186) [#7650](https://github.com/pjgm/serverless/issues/7650)
* **AWS API Gateway:** Ensure unique name for request validator ([a05e88d](https://github.com/pjgm/serverless/commit/a05e88d92e010ddfe019d5b5b873547b7d187d6d))
* **AWS API Gateway:** Fix `integration` schema ([09231c0](https://github.com/pjgm/serverless/commit/09231c059abdbab1f9a6ac371b8dc6e0784e72da))
* **AWS API Gateway:** Fix `usagePlan.throttle` handling ([#8472](https://github.com/pjgm/serverless/issues/8472)) ([04e18cb](https://github.com/pjgm/serverless/commit/04e18cbebf70ca6fd0534fcee5544de8f6569ed3))
* **AWS API Gateway:** Fix API key names resolution ([f9f6a3b](https://github.com/pjgm/serverless/commit/f9f6a3b560f70b81ce0ab6f802e05596bd700916)), closes [#5982](https://github.com/pjgm/serverless/issues/5982)
* **AWS API Gateway:** Fix handling of usagePlan array ([85cc447](https://github.com/pjgm/serverless/commit/85cc4476b35b144ed28e71302230df2d626a4e60))
* **AWS API Gateway:** Fix handling stage settings when in nested stack ([cf1692f](https://github.com/pjgm/serverless/commit/cf1692f1a42c3756619869c7cdba24c660141522))
* **AWS API Gateway:** Fix model resource name generator ([#8204](https://github.com/pjgm/serverless/issues/8204)) ([f727631](https://github.com/pjgm/serverless/commit/f7276311008134f57f24d85d2b16730c9ab75574))
* **AWS API Gateway:** Fix origin wildcard handling with `cors: true` ([57fec3f](https://github.com/pjgm/serverless/commit/57fec3f3d0429411b19f65d69cac85306b5ef950)), closes [#7482](https://github.com/pjgm/serverless/issues/7482)
* **AWS API Gateway:** Fix referencing provisioned authorizers ([5a691f4](https://github.com/pjgm/serverless/commit/5a691f44573180e1dd5a833aeae196b89a24b697))
* **AWS API Gateway:** Fix request validator triage ([cb109dd](https://github.com/pjgm/serverless/commit/cb109dd835ec358bfb1af10fe8f82aa283ffbafe))
* **AWS API Gateway:** Fix resolution of request parameters required value ([d2fb696](https://github.com/pjgm/serverless/commit/d2fb696ebd25b1b99bd6043523e2c0051bfbac3d)), closes [#8329](https://github.com/pjgm/serverless/issues/8329)
* **AWS API Gateway:** Fix schema for `apiKeys` and `permissionsBoundary` ([5601025](https://github.com/pjgm/serverless/commit/5601025dd8a4075cb463e2dcfb67d6c52984582a))
* **AWS API Gateway:** Fix support for `provider.apiGateway.stage` ([6fe2ea5](https://github.com/pjgm/serverless/commit/6fe2ea5bc84c01434ba6f044d8ab3623dea85574)), closes [#11772](https://github.com/pjgm/serverless/issues/11772)
* **AWS API Gateway:** Fix visibility of ..-Allow-Credentials CORS header ([bd9fbfb](https://github.com/pjgm/serverless/commit/bd9fbfb392afc2dc95f7d83864bfdc4dc1602728)), closes [#7576](https://github.com/pjgm/serverless/issues/7576)
* **AWS API Gateway:** Improve configuration validation ([e472a04](https://github.com/pjgm/serverless/commit/e472a0491a720863ab44fb81b6fada0da21507e3))
* **AWS API Gateway:** Meaningfully reject missing `restApiRootResourceId` ([2c0a962](https://github.com/pjgm/serverless/commit/2c0a962c4fc0ad82ecbc6a266d56bfaa81ad8054)), closes [#10371](https://github.com/pjgm/serverless/issues/10371)
* **AWS API Gateway:** Proper stage resolution for custom resource ([50e4425](https://github.com/pjgm/serverless/commit/50e44258835551523a089714396f12f6b229239c))
* **AWS API Gateway:** Properly apply `description` to REST API ([#10746](https://github.com/pjgm/serverless/issues/10746)) ([451def9](https://github.com/pjgm/serverless/commit/451def93ae1997df6dde10439bd931d73e926708))
* **AWS API Gateway:** Recognize CF functions for `connectionId` ([3e8858b](https://github.com/pjgm/serverless/commit/3e8858b1a8cde32a3659498c6dbdc7d8637e86c6))
* **AWS API Gateway:** Recognize CF functions for `mappedValue` ([868ac02](https://github.com/pjgm/serverless/commit/868ac02fd4d41a893d23a3f29101e3a3b952597b))
* **AWS API Gateway:** Recognize CF functions for `request.uri` ([13ce56a](https://github.com/pjgm/serverless/commit/13ce56ae314dff1c157fc8351fc702bf15573fce))
* **AWS API Gateway:** Silence timeout warning for `async: true` ([#8748](https://github.com/pjgm/serverless/issues/8748)) ([0384776](https://github.com/pjgm/serverless/commit/03847769cd238824cbe9ea9fdec1889645081b17))
* **AWS API Gateway:** Support `Fn::Split` for `vpcEndpointIds` schema ([56f8587](https://github.com/pjgm/serverless/commit/56f85874c6b9da44b8fbc326dfe3bce33bf8c41e))
* **AWS APIGW:**  Fix default resource policy configuration ([8814671](https://github.com/pjgm/serverless/commit/8814671435a2b78ec281e527227e1b4a0fbbe093)), closes [#7138](https://github.com/pjgm/serverless/issues/7138) [#7194](https://github.com/pjgm/serverless/issues/7194) [#7211](https://github.com/pjgm/serverless/issues/7211)
* **AWS APIGW:** Ensure to apply API GW stage settings with no endpoints ([dfa0967](https://github.com/pjgm/serverless/commit/dfa0967ecf693e8fdc191ac1c9f6bc3d1e4ae366)), closes [#7036](https://github.com/pjgm/serverless/issues/7036)
* **AWS APIGW:** Ensure to point provisioned version ([38f6ac1](https://github.com/pjgm/serverless/commit/38f6ac125e54d927871b4e5f5b387e0d4c28a6a7)), closes [#7059](https://github.com/pjgm/serverless/issues/7059)
* **AWS APIGW:** Fix handling of provisionedConcurrency: 0 setting ([2995f8f](https://github.com/pjgm/serverless/commit/2995f8fef9c051b4054fa05e45b1de300956530d)), closes [#7133](https://github.com/pjgm/serverless/issues/7133)
* **AWS APIGW:** Fix handling of removal of `resourcePolicy` setting ([e662a91](https://github.com/pjgm/serverless/commit/e662a91d92651111c86b6e72eed57075be95decb)), closes [#6789](https://github.com/pjgm/serverless/issues/6789)
* **AWS APIGW:** Fix Rest API id detection when no API GW involved ([b05d5bc](https://github.com/pjgm/serverless/commit/b05d5bcce3fdd0f9908cb4c37f95d74d8553dbf6)), closes [#7126](https://github.com/pjgm/serverless/issues/7126)
* **AWS CloudFront:** Accept CF intrinsic functions in `behavior` ([41e90c3](https://github.com/pjgm/serverless/commit/41e90c304306aabca1879ebba542328460bf2133)), closes [#11994](https://github.com/pjgm/serverless/issues/11994)
* **AWS CloudFront:** Ensure lambda edge has no vpc or env ([#7721](https://github.com/pjgm/serverless/issues/7721)) ([a1472ba](https://github.com/pjgm/serverless/commit/a1472ba6f0f10bb801de944661079174fec1a062))
* **AWS CloudFront:** Ensure to describe resolved stage in comment ([120bfb7](https://github.com/pjgm/serverless/commit/120bfb7c0273e2ddd120a4311ee736694568fc53))
* **AWS CloudFront:** Ensure to log deprecation at initialization stage ([61f90a3](https://github.com/pjgm/serverless/commit/61f90a362d33425dc10d4c5bd851132ec5779e8e))
* **AWS CloudFront:** Ensure unique names for cache policy ([a108b76](https://github.com/pjgm/serverless/commit/a108b761d05fc72987542588fefa65d7e57ac7ec)), closes [#8818](https://github.com/pjgm/serverless/issues/8818)
* **AWS CloudFront:** Fix check for deprecated CacheBehavior properties ([c3a61e2](https://github.com/pjgm/serverless/commit/c3a61e234bf73429b946e09121b48306e56e0ed5))
* **AWS CloudFront:** Fix deprecations visibility ([6c67cd7](https://github.com/pjgm/serverless/commit/6c67cd7f074ef27c9410f29b368dc7e87b5b6e2d))
* **AWS CloudFront:** Fix merge of template configuration ([#7739](https://github.com/pjgm/serverless/issues/7739)) ([304a502](https://github.com/pjgm/serverless/commit/304a50261dbccfe73b7eb9f6e6210209f63051ad))
* **AWS CloudFront:** Fix origin object schema ([#8827](https://github.com/pjgm/serverless/issues/8827)) ([90d9fc2](https://github.com/pjgm/serverless/commit/90d9fc2b5fbf700a6c1b4da60a6f211ca5e43bd4))
* **AWS CloudFront:** Recognize "?" character in `pathPattern` property ([9d84596](https://github.com/pjgm/serverless/commit/9d84596604a7338e82616723fe1a486c09272ae7))
* **AWS CloudFront:** Recognize `behavior.TrustedKeyGroups` in schema ([da71df6](https://github.com/pjgm/serverless/commit/da71df603295397229589c88dd8366426e06e982))
* **AWS CloudWatch:** Ensure no circular resource references ([#11893](https://github.com/pjgm/serverless/issues/11893)) ([75ce58b](https://github.com/pjgm/serverless/commit/75ce58b194f19b4fc5a37a7a437733befefccf06))
* **AWS Cognito:**  Fix low level refactor regression ([3e54858](https://github.com/pjgm/serverless/commit/3e54858fe68384b10b0ccbf2dc5b3f65f35027a4)), closes [#7915](https://github.com/pjgm/serverless/issues/7915)
* **AWS Cognito:**  FIx properly resource resolution ([6188bc4](https://github.com/pjgm/serverless/commit/6188bc48f5ab187dd525ed8518bbf493ddc67c4f)), closes [#7915](https://github.com/pjgm/serverless/issues/7915)
* **AWS Cognito:** Correct `logicalIds` based on triggers ([#9592](https://github.com/pjgm/serverless/issues/9592)) ([f4c9b58](https://github.com/pjgm/serverless/commit/f4c9b58b10a45ae342934e9a61dcdea0c2ef11e2))
* **AWS Cognito:** Fix pool update handling ([0898664](https://github.com/pjgm/serverless/commit/0898664c6807a6f0530281be2615d210470420fe))
* **AWS Credentials:** Fail when profile is already configured ([f8ad7bc](https://github.com/pjgm/serverless/commit/f8ad7bca6a26e39864d139fec4aadddd24b34a5b))
* **AWS Credentials:** Fix credentials resolution ([6f8b5b4](https://github.com/pjgm/serverless/commit/6f8b5b41ebfd173d33e2ad9717f8727cc0592915))
* **AWS Credentials:** Fix credentials resolution (right way) ([41df6fb](https://github.com/pjgm/serverless/commit/41df6fbee2705307ad7b44f614d70b5d801e0114))
* **AWS Credentials:** Fix error message resolution ([2faa20e](https://github.com/pjgm/serverless/commit/2faa20e8354d65eed767f88f52919e47edd32866))
* **AWS Credentials:** Fix unrecognized profile error reporting ([6c4beb6](https://github.com/pjgm/serverless/commit/6c4beb64ee6fe6722fbb7ca757611807d4025a26))
* **AWS Credentials:** Improve AWS SDK workaround ([32cde98](https://github.com/pjgm/serverless/commit/32cde98750a91449d352187a8e2f042a38eb3f64))
* **AWS Credentials:** Improve credentials error recognition ([863bc51](https://github.com/pjgm/serverless/commit/863bc51904778dbfcb984c663517172c8292ff9d))
* **AWS Credentials:** Recognize AWS_DEFAULT_PROFILE env variable ([#8354](https://github.com/pjgm/serverless/issues/8354)) ([261c16f](https://github.com/pjgm/serverless/commit/261c16fc594baf6e7f1884304e722ca23e26286c))
* **AWS Deploy:** Add descriptive error if S3 bucket cant be cleaned ([d4ee656](https://github.com/pjgm/serverless/commit/d4ee656de1fd4cb6b2803cb531725a016cc7e428))
* **AWS Deploy:** Allow removal of stack with bucket missing ([1a85a4a](https://github.com/pjgm/serverless/commit/1a85a4a901caf4ca05096bf11bfcad31959c8044))
* **AWS Deploy:** Apply stack policy after executing change sets ([#10903](https://github.com/pjgm/serverless/issues/10903)) ([2d2cb3e](https://github.com/pjgm/serverless/commit/2d2cb3ed11919ccdb5b99e8316906ad5eccd836f))
* **AWS Deploy:** Check for VPC config change in `deploy function` ([0190d0d](https://github.com/pjgm/serverless/commit/0190d0df05f4e37c8e965913ef1ceaf6b8a9b525))
* **AWS Deploy:** Correctly detect finished stack removal with DEBUG ([2712f3b](https://github.com/pjgm/serverless/commit/2712f3b493ff5b9d1e30c63426114c266388aa1a))
* **AWS Deploy:** Correctly identify "no updates" error during deploy ([0e6a1ce](https://github.com/pjgm/serverless/commit/0e6a1ce2d4a28a480683192cc6ac639c7bfe0d8b))
* **AWS Deploy:** Dont update `vpc` during `deploy function` if uses CF ([2c7f024](https://github.com/pjgm/serverless/commit/2c7f024a57dd70c0e05d6ab7f40e530c96f2351a))
* **AWS Deploy:** Ensure `vpc` configuration on custom resources ([#11985](https://github.com/pjgm/serverless/issues/11985)) ([f2d1e23](https://github.com/pjgm/serverless/commit/f2d1e23f591a8cae2d41a93ca476b135dfcdac68))
* **AWS Deploy:** Ensure no duplicate (case-insensitive) stack tags ([71919f1](https://github.com/pjgm/serverless/commit/71919f1d1f34386fa3429e3e47196c849218f82b)), closes [#7887](https://github.com/pjgm/serverless/issues/7887)
* **AWS Deploy:** Ensure right code for `deploy -f` deprecation ([90877d5](https://github.com/pjgm/serverless/commit/90877d575ec9436db30a3a16fc90e5190ea30018))
* **AWS Deploy:** Ensure to clear `notificationArns` if needed ([a2e58cd](https://github.com/pjgm/serverless/commit/a2e58cdeae51f7fc034743743354bf75c3817413))
* **AWS Deploy:** Ensure to handle artifact stream read errors ([300e3a9](https://github.com/pjgm/serverless/commit/300e3a92d5d5d54c4269dd05b6e5d9e2e96b380d))
* **AWS Deploy:** Ensure to handle right overriden package.artifact ([#8351](https://github.com/pjgm/serverless/issues/8351)) ([661caad](https://github.com/pjgm/serverless/commit/661caad22d4d1154aa197bbfc95948ae74bbc1aa))
* **AWS Deploy:** Ensure to only remove specific stage deploy artifacts ([9eae965](https://github.com/pjgm/serverless/commit/9eae9652bdfca78eeb29bc4e9dfd4f8a12125d56))
* **AWS Deploy:** Ensure to strip all `null` properties ([#10304](https://github.com/pjgm/serverless/issues/10304)) ([1f58760](https://github.com/pjgm/serverless/commit/1f58760f467f2dcb960e23c2eb028f4abef23209))
* **AWS Deploy:** Fix `deploy function` command error handling ([aa7b66a](https://github.com/pjgm/serverless/commit/aa7b66a66c199c236bedfbc3b3aab39acb0eb6ad))
* **AWS Deploy:** Fix `provider.layers` support in `deploy function` cmd ([ed15cb2](https://github.com/pjgm/serverless/commit/ed15cb27aee68954c93d875da96274914943ad71))
* **AWS Deploy:** Fix default runtime resolution ([943bf6d](https://github.com/pjgm/serverless/commit/943bf6dfad3750dabd4754708a3649da9798984c))
* **AWS Deploy:** Fix format of url data as passed to `https-proxy-agent` ([d935dcc](https://github.com/pjgm/serverless/commit/d935dccb268ff8e54d9f1fb56beee01115e041c1)), closes [#9147](https://github.com/pjgm/serverless/issues/9147)
* **AWS Deploy:** Fix generation of custom resource lambda zip ([6b3a789](https://github.com/pjgm/serverless/commit/6b3a78950c4d02049b76675a3df093891de4317a))
* **AWS Deploy:** Fix handling of AWS SDK numeric error codes ([#8412](https://github.com/pjgm/serverless/issues/8412)) ([6e62e1c](https://github.com/pjgm/serverless/commit/6e62e1c5e8f66237e45e83d667e6b50bfb8ea753))
* **AWS Deploy:** Fix handling of deployment bucket extensions ([#10137](https://github.com/pjgm/serverless/issues/10137)) ([39bdea0](https://github.com/pjgm/serverless/commit/39bdea07500b8fb814a5cce83ec6f78a0c75006c))
* **AWS Deploy:** Fix handling of inactive CloudFormation stack state ([0d850fc](https://github.com/pjgm/serverless/commit/0d850fcca70d329a0d597d29cb985abd418bd955)), closes [#11863](https://github.com/pjgm/serverless/issues/11863)
* **AWS Deploy:** Fix handling of state file in check for changes logic ([12d95dc](https://github.com/pjgm/serverless/commit/12d95dcee1985ff32c02e1ba507a236eceab65ba))
* **AWS Deploy:** Fix packaging logic after [#7742](https://github.com/pjgm/serverless/issues/7742) regression ([b97e2b4](https://github.com/pjgm/serverless/commit/b97e2b421138def7131069771fc820e81edafc73))
* **AWS Deploy:** Fix resolution of CloudFormation error ([4579045](https://github.com/pjgm/serverless/commit/4579045ed12ad0ad44c38df7e38f892ebbe5263d))
* **AWS Deploy:** Fix resolution of first deploy event ([9bc1060](https://github.com/pjgm/serverless/commit/9bc1060dceb6a155abdb27364a9d0061b4d95983))
* **AWS Deploy:** Fix resolution of SLS_AWS_REQUEST_MAX_RETRIES setting ([4d1b3b5](https://github.com/pjgm/serverless/commit/4d1b3b571d76d235b547a4149e3c19b6510ebf6c))
* **AWS Deploy:** Fix stack errors processing ([18a9b2b](https://github.com/pjgm/serverless/commit/18a9b2b6f5734083de751cf182c6be61736be11f))
* **AWS Deploy:** Gracefully handle denied access to ecr ([816394c](https://github.com/pjgm/serverless/commit/816394c6e5dfc50b332314aef66eeb9ed75d139a))
* **AWS Deploy:** Handle gently missing template body ([195c3f2](https://github.com/pjgm/serverless/commit/195c3f2f15b581ac8f400e091cbf40941a20ff5e))
* **AWS Deploy:** Improve S3 bucket policy security ([#8542](https://github.com/pjgm/serverless/issues/8542)) ([2a9b57b](https://github.com/pjgm/serverless/commit/2a9b57b62074d3e58f987aefb7888e14dfc35dce))
* **AWS Deploy:** Improve vague S3-related access errors ([1b2ac24](https://github.com/pjgm/serverless/commit/1b2ac245666fdd5b903a2ffb8ba5376ecfaab182))
* **AWS Deploy:** Properly apply `stackPolicy` with changesets ([ee30a7b](https://github.com/pjgm/serverless/commit/ee30a7be628de24dfdfe35bfd5ad7df3653891f7))
* **AWS Deploy:** Recognize `LogicalResourceId` in `stackPolicy` ([1a528c2](https://github.com/pjgm/serverless/commit/1a528c2cc0746bfe6a692183f96b0831e3dd92f4))
* **AWS Deploy:** Recognize all boolean values at `provider.disableRollback` ([2485c7e](https://github.com/pjgm/serverless/commit/2485c7efcc4f6f5b1d65b56d4d0d71297d113fa5))
* **AWS Deploy:** Recognize otel extension in check for changes logic ([6da0b65](https://github.com/pjgm/serverless/commit/6da0b6554ee1d42dca4f02ac874ff8e992051de0))
* **AWS Deploy:** Report meaningfully inaccessible file artifacts ([23c290e](https://github.com/pjgm/serverless/commit/23c290e4b4049242d62cfb57f4be6aadff6aecf8))
* **AWS Deploy:** Respect existing YAML CF templates ([#11521](https://github.com/pjgm/serverless/issues/11521)) ([20d79a2](https://github.com/pjgm/serverless/commit/20d79a2876875f73755ccae4e1e2c2a9c02c9ad7))
* **AWS Deploy:** Support `0` as SLS_AWS_REQUEST_MAX_RETRIES setting ([da1b75a](https://github.com/pjgm/serverless/commit/da1b75ac889f99a82afa5606e4e0f1f7f3ee2bcf))
* **AWS Deploy:** Throw on attempt of extending not existing resource ([02be86c](https://github.com/pjgm/serverless/commit/02be86ca4954553388ac70845d8ff3aca205abcd))
* **AWS Deploy:** Warn when invalid IAM policy to fetch lambda ([#9041](https://github.com/pjgm/serverless/issues/9041)) ([dea7b5a](https://github.com/pjgm/serverless/commit/dea7b5a3c0b5b1208c44c0762566a0fdab298f83))
* **AWS EventBridge:** Addres typos in error messages ([#10165](https://github.com/pjgm/serverless/issues/10165)) ([ee38f6a](https://github.com/pjgm/serverless/commit/ee38f6a3081a3a0f22ee9fea8975f13520ac18ec))
* **AWS EventBridge:** Allow intrinsic functions in `pattern` ([#10120](https://github.com/pjgm/serverless/issues/10120)) ([1c105a4](https://github.com/pjgm/serverless/commit/1c105a4c16e8bdca9fc66c5eddf12153ebc9a1fb))
* **AWS EventBridge:** Clarify CF functions support for `eventBus` ([5183620](https://github.com/pjgm/serverless/commit/5183620e9e4795c3ab07d30e7386d9360a2d7eb7))
* **AWS EventBridge:** Ensure no duplicate event bus IAM policies ([#7644](https://github.com/pjgm/serverless/issues/7644)) ([a1fde35](https://github.com/pjgm/serverless/commit/a1fde35db47db76b18ddcb006e4faab22f58dc73))
* **AWS EventBridge:** Ensure proper support for `deadLetterQueueArn` ([846cfa1](https://github.com/pjgm/serverless/commit/846cfa1bcf678a748678014c6359e5f0907d35ff))
* **AWS EventBridge:** Fix `MaximumEventAgeInSecond` template reference ([cd03f55](https://github.com/pjgm/serverless/commit/cd03f550ae5307ca44e1e27d4d0822bef6cc9dcf))
* **AWS EventBridge:** Fix attaching lambdas to "default" stage ([#7995](https://github.com/pjgm/serverless/issues/7995)) ([b53f080](https://github.com/pjgm/serverless/commit/b53f080a4dfc8439333090d2a177ac0272b6d1fe))
* **AWS EventBridge:** Fix handling of events removal ([#8004](https://github.com/pjgm/serverless/issues/8004)) ([41d19b3](https://github.com/pjgm/serverless/commit/41d19b3834609ae6bf96439df554b99a082ccb0f))
* **AWS HTTP API:** Adjust schema for correct `typescript` generation ([fce73ad](https://github.com/pjgm/serverless/commit/fce73ad4df0f776cf950733f9e88c3d390d6fc66))
* **AWS HTTP API:** Always allow to define catch-all route ([#9840](https://github.com/pjgm/serverless/issues/9840))  ([7e9bfd6](https://github.com/pjgm/serverless/commit/7e9bfd63fce56f880a3ad0379fd97fdfce89d91b))
* **AWS HTTP API:** Configure default stage explicity ([3d79a7a](https://github.com/pjgm/serverless/commit/3d79a7a169fdc2c43c86d6b509f9151af32665dc))
* **AWS HTTP API:** Do not validate timeout when no httpApi event ([841aac9](https://github.com/pjgm/serverless/commit/841aac941fdfc65f55b321382cfd349bd5caa209))
* **AWS HTTP API:** Ensure function timeout setting is respected ([b52a41d](https://github.com/pjgm/serverless/commit/b52a41d9ee08efc875815b239c7d25d32b3be92f))
* **AWS HTTP API:** Ensure to apply tags to stage ([#9407](https://github.com/pjgm/serverless/issues/9407)) ([80511a4](https://github.com/pjgm/serverless/commit/80511a4b17e77e22cf8b20d1ce50eef7506d4f7f))
* **AWS HTTP API:** Fix config schema issues discovered in tests ([fc9edfc](https://github.com/pjgm/serverless/commit/fc9edfc90e4571b91e7b2c8c44f08f15f90510eb))
* **AWS HTTP API:** Fix default log format ([90ceecd](https://github.com/pjgm/serverless/commit/90ceecd00d2e623f3d8a0aef13aa5a23e496d057)), closes [#7559](https://github.com/pjgm/serverless/issues/7559)
* **AWS HTTP API:** Properly handle authorizer function with alias ([0ca6aaa](https://github.com/pjgm/serverless/commit/0ca6aaae526b16df2039edff5db166a39bb1de10))
* **AWS HTTP API:** Publish to default stage ([44c2342](https://github.com/pjgm/serverless/commit/44c2342aeba76bd98c097a78be1d762eeccbbfd3))
* **AWS HTTP API:** Recognize API id passed as CF import instruction ([3f6b3ce](https://github.com/pjgm/serverless/commit/3f6b3ce9a47cf00eab52c033c472a86cfc8c5c1c))
* **AWS HTTP API:** Recognize max timeout as 30s not 29s ([#10119](https://github.com/pjgm/serverless/issues/10119)) ([e3e02fe](https://github.com/pjgm/serverless/commit/e3e02fe8e2f1bbd236cfa49f80a360fd828c1ead))
* **AWS HTTP API:** Respect logRetentionInDays setting ([#7856](https://github.com/pjgm/serverless/issues/7856)) ([9dad77c](https://github.com/pjgm/serverless/commit/9dad77ce1b12218f3c38b62c716d4dbc9d68bb5d))
* **AWS HTTP API:** Support HTTP API name customization ([#7434](https://github.com/pjgm/serverless/issues/7434)) ([7479a9a](https://github.com/pjgm/serverless/commit/7479a9ae82b44fb06de3ab84094b18e8f72affc4))
* **AWS IAM:** Accept `arn:${AWS::Partition}` in function roles ([#9103](https://github.com/pjgm/serverless/issues/9103)) ([e77a00d](https://github.com/pjgm/serverless/commit/e77a00dfff734ccb74a7ca77ef92135c4f4dc06b))
* **AWS IAM:** Allow `iam.role` to use `awsLambdaRole` definition ([#9094](https://github.com/pjgm/serverless/issues/9094)) ([82bf35c](https://github.com/pjgm/serverless/commit/82bf35c1b9abd81fe52cdc7fd57b63cab4cecc6e))
* **AWS IAM:** Deprecate 'iam.role.permissionBoundary' ([#9318](https://github.com/pjgm/serverless/issues/9318)) ([d1c3b3f](https://github.com/pjgm/serverless/commit/d1c3b3fbac0d2c80db7284d3ef4d8b808c33fa03))
* **AWS IAM:** Fix role and policy name resolution ([08dc745](https://github.com/pjgm/serverless/commit/08dc745cbfa403860bc7e08cbaf10cd90f15be05)), closes [#7357](https://github.com/pjgm/serverless/issues/7357)
* **AWS IAM:** Prevent logs write access with disabled logging ([#8561](https://github.com/pjgm/serverless/issues/8561)) ([ee18167](https://github.com/pjgm/serverless/commit/ee1816772e4d3db8acda779f622904500d8072ec))
* **AWS IAM:** Remove  iamRoleLambdaExecution from DependsOn ([#7722](https://github.com/pjgm/serverless/issues/7722)) ([d8222fa](https://github.com/pjgm/serverless/commit/d8222fa0dc80ac4f6e7c23b3ccfd0d91f80b3e2e))
* **AWS IAM:** Report missing `RoleName` on custom role ([#8219](https://github.com/pjgm/serverless/issues/8219)) ([60cfa75](https://github.com/pjgm/serverless/commit/60cfa75d6b5ce5b41b70739612d1f128abf05316))
* **AWS IAM:** Support for CF functions for `provider.iam.role` ([0a84f1c](https://github.com/pjgm/serverless/commit/0a84f1c84ee4e7ac32d9b5c247eba7f25da0d14a))
* **AWS Info:** Fix calculation of resources count ([#7587](https://github.com/pjgm/serverless/issues/7587)) ([946d32c](https://github.com/pjgm/serverless/commit/946d32cb48dbcdc3f02a8c1521b7f5cabf1eb1f9))
* **AWS Invocation:** Ensure proper log formatting for `invoke` ([c4eb2ad](https://github.com/pjgm/serverless/commit/c4eb2ad908cbb4cbf646d9ffc73da31e9db1482f))
* **AWS Invocation:** Fix resolution of options with non-AWS provider ([#9602](https://github.com/pjgm/serverless/issues/9602)) ([54da80e](https://github.com/pjgm/serverless/commit/54da80e26497b8f1dbcd3027775628d11e1c6814))
* **AWS Kafka:** Allow usage of Server Root CA without client TLS auth ([6a6417c](https://github.com/pjgm/serverless/commit/6a6417c29fe6c06286562ab7604536004bf62334))
* **AWS Lambda:** Add schema dependencies for image config ([297c229](https://github.com/pjgm/serverless/commit/297c22972ea7d477a9ced296f591f8ab0a8ac77f))
* **AWS Lambda:** Do not break permission resource ([5e63cee](https://github.com/pjgm/serverless/commit/5e63cee340591af5aaa65828a6907fca445d76e4)), closes [#7189](https://github.com/pjgm/serverless/issues/7189)
* **AWS Lambda:** Ensure correct schema for `vpc` definition ([4cd629a](https://github.com/pjgm/serverless/commit/4cd629ac44f5a1a1442d7245878df6b361a94973))
* **AWS Lambda:** Ensure ECR repository name is lowercased ([d8bda1e](https://github.com/pjgm/serverless/commit/d8bda1edb7e2657250b646f8edb184d9e422b675))
* **AWS Lambda:** Ensure function update works when image used ([#8786](https://github.com/pjgm/serverless/issues/8786)) ([420e937](https://github.com/pjgm/serverless/commit/420e93740f1e9bffc285559b2567379f550f28af))
* **AWS Lambda:** Ensure image region matches provider region ([#11081](https://github.com/pjgm/serverless/issues/11081)) ([447704f](https://github.com/pjgm/serverless/commit/447704f404ebe1026192d6534250a5a1a1026f74))
* **AWS Lambda:** Ensure proper `DependsOn` settings when `url: true` ([2107aec](https://github.com/pjgm/serverless/commit/2107aec965e4e1e0cec98c3e2f0ff8dcc534a333))
* **AWS Lambda:** Ensure proper normalization of ecr repo name ([c5639d2](https://github.com/pjgm/serverless/commit/c5639d21ea4db9fe7ab9d9f00c8bcf42e4b81ad7))
* **AWS Lambda:** Ensure that docker image is build and pushed only once ([277f4e8](https://github.com/pjgm/serverless/commit/277f4e8e9c53c0572981407eb45cecba050462a7))
* **AWS Lambda:** Ensure to attempt ECR login on expired token ([e4f368c](https://github.com/pjgm/serverless/commit/e4f368ced9d7d032285091039e47279b0678dd1c))
* **AWS Lambda:** Ensure to respect `maximumRetryAttempts` set to `0` ([bab0d56](https://github.com/pjgm/serverless/commit/bab0d56bd9be6ba1afe0eef352c8732dd7fe4f73))
* **AWS Lambda:** Ensure version hash is affected by layer changes ([e43c889](https://github.com/pjgm/serverless/commit/e43c889647f45bc93cf3cb1fd45d4a18ad95da58)), closes [#8066](https://github.com/pjgm/serverless/issues/8066)
* **AWS Lambda:** Ensure version hash is in all cases effective ([#8310](https://github.com/pjgm/serverless/issues/8310)) ([73c34b9](https://github.com/pjgm/serverless/commit/73c34b9f2bbe3b7c063a257a5b032b7460f263c0))
* **AWS Lambda:** Fix `runtimeManagment` handling ([#11778](https://github.com/pjgm/serverless/issues/11778)) ([8db2f4c](https://github.com/pjgm/serverless/commit/8db2f4cbc56a46110d82e3d36e8a63f50e06d495))
* **AWS Lambda:** Fix CloudWatch logs creation access ([4a947b2](https://github.com/pjgm/serverless/commit/4a947b215cc8f80b058967d21db354bab1fd62ea)), closes [#6241](https://github.com/pjgm/serverless/issues/6241) [#6692](https://github.com/pjgm/serverless/issues/6692)
* **AWS Lambda:** Fix DependsOn handling in case of disabled logs ([#7731](https://github.com/pjgm/serverless/issues/7731)) ([2a26493](https://github.com/pjgm/serverless/commit/2a26493951307f6c30d2d86fdff4034c00274999))
* **AWS Lambda:** Fix event config setup for provisioned lambdas ([3b4e453](https://github.com/pjgm/serverless/commit/3b4e4539d8b56de6a7cccb2e9c8455f34a5289f6))
* **AWS Lambda:** Fix provisioned concurrency configuration ([eaf9b61](https://github.com/pjgm/serverless/commit/eaf9b6117f89f79d8964119a4ac3ed0159578d61)), closes [#7059](https://github.com/pjgm/serverless/issues/7059)
* **AWS Lambda:** Improve "image" property validation ([a8be1d1](https://github.com/pjgm/serverless/commit/a8be1d1776a26b033d821d70e99ad654a39a4158))
* **AWS Lambda:** Permissions on lambda layer retained ([bf418ac](https://github.com/pjgm/serverless/commit/bf418ac6ca14f3a5570998f5fecf2bfd8a3d12a6))
* **AWS Lambda:** Properly format `logs` with missing init duration ([0bb64e2](https://github.com/pjgm/serverless/commit/0bb64e21cbe7250f9b14ccb3fd9537d6dec64c67))
* **AWS Lambda:** Properly resolve SHA for repo with slashes ([4c74792](https://github.com/pjgm/serverless/commit/4c7479283cd2bfb20b2ddb9d21b824b4757234ed))
* **AWS Lambda:** Recognize `Fn::If` function for `environment` ([63743ad](https://github.com/pjgm/serverless/commit/63743ade31207049eee1811203db5622bc510f1a))
* **AWS Lambda:** Recognize function-wide settings for version hashing ([1fceb89](https://github.com/pjgm/serverless/commit/1fceb898d0ea10b00bc6759a5204065c81b560e8)), closes [#8212](https://github.com/pjgm/serverless/issues/8212)
* **AWS Lambda:** Recognize only valid .NET runtimes ([#11960](https://github.com/pjgm/serverless/issues/11960)) ([dd081bb](https://github.com/pjgm/serverless/commit/dd081bbc4189e3b4757b8e704d048191e59a932f))
* **AWS Lambda:** Remove AWS  issue workaround ([4821ad2](https://github.com/pjgm/serverless/commit/4821ad21a5da5622a5686a7dc6eafdcd90ffe538)), closes [#7137](https://github.com/pjgm/serverless/issues/7137)
* **AWS Lambda:** Respect external IAM role at destinations ([7a3a45f](https://github.com/pjgm/serverless/commit/7a3a45f0b3f2b42a0ab68b6f638d3d97fda7cf31)), closes [#7448](https://github.com/pjgm/serverless/issues/7448)
* **AWS Lambda:** Revert inclusion of version hashi in env var ([#8332](https://github.com/pjgm/serverless/issues/8332)) ([5851bca](https://github.com/pjgm/serverless/commit/5851bcadcf6016914013d447de899cc98efb8346))
* **AWS Lambda:** Throw verbose error when referencing invalid layer ([5057f9a](https://github.com/pjgm/serverless/commit/5057f9ab865dd62d12e8ff1f673615462470bb74))
* **AWS Lambda:** Workaround AWS issue related to alias redeployments ([3210a94](https://github.com/pjgm/serverless/commit/3210a94ef9615367d16feb82e1dec4e55f549869)), closes [#7059](https://github.com/pjgm/serverless/issues/7059)
* **AWS Layers:** Support references to external layers ([dc74f41](https://github.com/pjgm/serverless/commit/dc74f41470447c1fab0a646c15284a4eb212ecb6))
* **AWS Local Invocation:** Add java11 support. ([dc1edc1](https://github.com/pjgm/serverless/commit/dc1edc10c0088f57b104b8296df6f78d6205b4a0)), closes [#7956](https://github.com/pjgm/serverless/issues/7956)
* **AWS Local Invocation:** Adjust `.gitignore` [#9273](https://github.com/pjgm/serverless/issues/9273). ([#9274](https://github.com/pjgm/serverless/issues/9274)) ([ce210f7](https://github.com/pjgm/serverless/commit/ce210f785271bf0fb54685ed1ef84fb09ceaf05d))
* **AWS Local Invocation:** Allow optional `package.artifact` for `java` ([924a698](https://github.com/pjgm/serverless/commit/924a698d2a9d7a663c1fcbb11707ad8d2ed30b6b))
* **AWS Local Invocation:** Artifact permissions for `rust` func ([#10891](https://github.com/pjgm/serverless/issues/10891)) ([11dd77e](https://github.com/pjgm/serverless/commit/11dd77ecde61b690023067dacdabf759121cd17c))
* **AWS Local Invocation:** Bump AWS Java pom version to pull in fix ([504b42a](https://github.com/pjgm/serverless/commit/504b42ae0fefd04ccfa013746371c49a02d8a4d3)), closes [#9714](https://github.com/pjgm/serverless/issues/9714)
* **AWS Local Invocation:** Correctly `decompress` artifact ([#9259](https://github.com/pjgm/serverless/issues/9259)) ([af8d2a1](https://github.com/pjgm/serverless/commit/af8d2a19269bf5480a6a87d91a17609f7f931eac))
* **AWS Local Invocation:** Do not document `-c` as `--context` alias ([e969bb3](https://github.com/pjgm/serverless/commit/e969bb356bb4a1b5e861a3b0b76986f82b767b85))
* **AWS Local Invocation:** Dont build bridge if artifact missing ([#9280](https://github.com/pjgm/serverless/issues/9280)) ([5392a7d](https://github.com/pjgm/serverless/commit/5392a7dce2a325d3f93d8e8508d63d16d93c6f51))
* **AWS Local Invocation:** Ensure env vars resolve for docker ([#10962](https://github.com/pjgm/serverless/issues/10962)) ([1a8e7d9](https://github.com/pjgm/serverless/commit/1a8e7d948efe696cd4970f73ac4262cc15ebe977))
* **AWS Local Invocation:** Ensure IS_LOCAL env variable in docker ([21babec](https://github.com/pjgm/serverless/commit/21babec2ce5d56ecb7ddaad3e89387f6186cc52e)), closes [#8372](https://github.com/pjgm/serverless/issues/8372)
* **AWS Local Invocation:** Ensure package before resolving runtime ([80b3e1a](https://github.com/pjgm/serverless/commit/80b3e1a9e59746dd795828207a2badf683638df4))
* **AWS Local Invocation:** Ensure to mount as read only in docker ([4252422](https://github.com/pjgm/serverless/commit/4252422a94857eb3b446562ba3b24188f0116f19)), closes [#7622](https://github.com/pjgm/serverless/issues/7622)
* **AWS Local Invocation:** Fix Dockerfile layer path on Windows ([#8273](https://github.com/pjgm/serverless/issues/8273)) ([0164327](https://github.com/pjgm/serverless/commit/01643273df742239cd020e7d08941c505e540217))
* **AWS Local Invocation:** Fix error handling of invalid file content ([e836722](https://github.com/pjgm/serverless/commit/e836722f976af98eb69fc6d3a85781bb7434dfac))
* **AWS Local Invocation:** Fix invalid result handling ([bbff029](https://github.com/pjgm/serverless/commit/bbff0290db8a56cf599522c5ec0abc901359a0f9))
* **AWS Local Invocation:** Improve `ruby` context ([#10705](https://github.com/pjgm/serverless/issues/10705)) ([ce5bf0b](https://github.com/pjgm/serverless/commit/ce5bf0b40f64c087fa5ec114d0d28750b4813aaa))
* **AWS Local Invocation:** Remove log4j dependency from java wrapper ([8b17338](https://github.com/pjgm/serverless/commit/8b1733807fe76b01f03880652111f8085a664e31))
* **AWS Local Invocation:** Report invalid handler path meaningfully ([a2297ee](https://github.com/pjgm/serverless/commit/a2297ee916dd79463d4efcfd6f7fe1f8e0e50d87))
* **AWS Local Invocation:** Strip `null` envvars for local invoke ([#9263](https://github.com/pjgm/serverless/issues/9263)) ([34d2c2f](https://github.com/pjgm/serverless/commit/34d2c2feacc3a19c740cf78e6dbeb0b9a9ad5a74))
* **AWS Local Invocation:** Support `env` vars with `=` in value ([#9079](https://github.com/pjgm/serverless/issues/9079)) ([ab8529c](https://github.com/pjgm/serverless/commit/ab8529cb24d63edba798ea6fba3d783f256d3998))
* **AWS Local Invocation:** Upgrade log4j to version 2.17.0 ([#10396](https://github.com/pjgm/serverless/issues/10396)) ([2782ed4](https://github.com/pjgm/serverless/commit/2782ed4221caa410708cbabbbd09d45a6363be29))
* **AWS S3:** Fix error message generation ([#7564](https://github.com/pjgm/serverless/issues/7564)) ([2e56dea](https://github.com/pjgm/serverless/commit/2e56dea5652540cf5d82c9d35a999c8c921fa020))
* **AWS S3:** Fix handling of lambda removal permissions ([#8384](https://github.com/pjgm/serverless/issues/8384)) ([c2d40ea](https://github.com/pjgm/serverless/commit/c2d40ea63baa930dad31bf6950c25852ccd8adf4))
* **AWS S3:** Fix parsing of the artifact S3 url ([#9380](https://github.com/pjgm/serverless/issues/9380)) ([360925d](https://github.com/pjgm/serverless/commit/360925d2e0cddb6fbbbb72ca47495aa71a43d1fc))
* **AWS S3:** Recognize `BucketKeyEnabled` setting ([#9985](https://github.com/pjgm/serverless/issues/9985)) ([54bb13b](https://github.com/pjgm/serverless/commit/54bb13b6a6d3fd41548615fc23f4ae4d6d663dcc))
* **AWS Schedule:** Fix IAM role assignment ([#12030](https://github.com/pjgm/serverless/issues/12030)) ([e1039de](https://github.com/pjgm/serverless/commit/e1039ded5c5e35595b5d4c59e81d480a16c4dd67))
* **AWS SNS:** Fix setup of redrive policy ([#8268](https://github.com/pjgm/serverless/issues/8268)) ([3e9e6aa](https://github.com/pjgm/serverless/commit/3e9e6aacc675cd7bf92499b9494a15ff9b21981b))
* **AWS SNS:** Recognize `displayName` as optional ([#8323](https://github.com/pjgm/serverless/issues/8323)) ([a020a4a](https://github.com/pjgm/serverless/commit/a020a4a683f7c5ef3625fc52cb319300b9e302d2))
* **AWS SQS:** Accept only plain string form in direct ARN assignement ([f7bbd17](https://github.com/pjgm/serverless/commit/f7bbd176866b99725dcf1fef1128b0d2194217e0)), closes [#10263](https://github.com/pjgm/serverless/issues/10263)
* **AWS SQS:** Ensure to depend on provisioned alias if needed ([#8298](https://github.com/pjgm/serverless/issues/8298)) ([8c4d972](https://github.com/pjgm/serverless/commit/8c4d97211aa3dd4c41d9205a3ca0ccaab3564225))
* **AWS SQS:** Fix referencing lambdas with provisioned concurrency ([2abb9ad](https://github.com/pjgm/serverless/commit/2abb9ad8552d4edc77df5fe1c542373997443950))
* **AWS SQS:** Fix resolution of `Enabled` property  ([#7532](https://github.com/pjgm/serverless/issues/7532)) ([8abae84](https://github.com/pjgm/serverless/commit/8abae84b8003567b6cb8affae018245a806a272b)), closes [#7438](https://github.com/pjgm/serverless/issues/7438)
* **AWS SQS:** Revert support for `maximumRetryAttempts` option ([#7832](https://github.com/pjgm/serverless/issues/7832)) ([5a5a986](https://github.com/pjgm/serverless/commit/5a5a9864149e962375bb252adcaf32bbe10662da))
* **AWS Stream:** Fix configuration of boolean `Enabled` setting ([#7552](https://github.com/pjgm/serverless/issues/7552)) ([10c016f](https://github.com/pjgm/serverless/commit/10c016f35378e91910ee2cda3df87ddb592e95ab))
* **AWS Stream:** Fix handling of configuration properties  ([#7682](https://github.com/pjgm/serverless/issues/7682)) ([7e1dd66](https://github.com/pjgm/serverless/commit/7e1dd66f8ee72010826a7a56b7cae2479c852a60))
* **AWS Stream:** Fix support for `batchWindow: 0` ([b0547e6](https://github.com/pjgm/serverless/commit/b0547e6e1a673eff956f417110ce6bf40fc32f92))
* **AWS Stream:** Fix support for lambdas with provisioned concurrency ([c382d86](https://github.com/pjgm/serverless/commit/c382d869a84a5c7c84fd827eb815e0b881737c69)), closes [#8342](https://github.com/pjgm/serverless/issues/8342)
* **AWS Websocket:** Fix AWS partition support ([#7430](https://github.com/pjgm/serverless/issues/7430)) ([9b627fb](https://github.com/pjgm/serverless/commit/9b627fbf7e69d123f60e31c27289788fed7115ae))
* **AWS Websocket:** Fix internal authorizers handling ([#11871](https://github.com/pjgm/serverless/issues/11871)) ([a50773b](https://github.com/pjgm/serverless/commit/a50773b60d0c528ad7734dfa4a84cd9dc109f7e1))
* **AWS Websocket:** Fix resources dependency chain ([9c0f646](https://github.com/pjgm/serverless/commit/9c0f6461b73976958ebdd7e2762c6d1fbd469da1))
* binary support for OPTIONS method ([611e43c](https://github.com/pjgm/serverless/commit/611e43cdffd944e828a2108648a713d5a4b6ad15))
* Bring back "provider.sdk" property, to not break plugins ([3e983f3](https://github.com/pjgm/serverless/commit/3e983f347a10601e5dc5b1e6c19ae2822c94f682))
* bump platform-client version for axios ([#12260](https://github.com/pjgm/serverless/issues/12260)) ([10980b9](https://github.com/pjgm/serverless/commit/10980b9578cb4da6820300b69ae2f001feb1f38e))
* Check for Serverless Dashboard IAM stack prior to creation ([#12147](https://github.com/pjgm/serverless/issues/12147)) ([bf518b9](https://github.com/pjgm/serverless/commit/bf518b9135997c67ea940ff396af14a4b4b62948))
* **CLI Onboarding:** Do not attempt local fallback during onboarding ([ae5be0f](https://github.com/pjgm/serverless/commit/ae5be0f5dafaad933000e98142fcb1ec60e04555))
* **CLI Onboarding:** Don't crash if Dashboar server is inaccessible ([983a3b9](https://github.com/pjgm/serverless/commit/983a3b9be6af1e156b0793afbf19f1d81282e6d1))
* **CLI Onboarding:** Enable console in config, only with `--console` ([b173d90](https://github.com/pjgm/serverless/commit/b173d90e643a472817f90c9d9a31d4924d35c56f))
* **CLI Onboarding:** Ensure credentials resolution before deploy ([b85f393](https://github.com/pjgm/serverless/commit/b85f3934ed87e9c78494e9ad26163ee1d041599e))
* **CLI Onboarding:** Ensure to enable console when commented out ([f0bff74](https://github.com/pjgm/serverless/commit/f0bff7463c29e346dc61aa05db2c6f530b9282fb))
* **CLI Onboarding:** Ensure to not show backend notification ([ba831b8](https://github.com/pjgm/serverless/commit/ba831b8b3e4a9371091db9e709545adba324d822))
* **CLI Onboarding:** Ensure to process fully resolved service config ([6a1f083](https://github.com/pjgm/serverless/commit/6a1f083ac80aa9ba04e072b55f53ea1a4367fc2a))
* **CLI Onboarding:** Ensure variables resolution for templates ([17df292](https://github.com/pjgm/serverless/commit/17df2928cfb2efa8eab27e625b4609f8047eab5a))
* **CLI Onboarding:** Fix `initialContext.isDashboardEnabled` resolution ([10c24f6](https://github.com/pjgm/serverless/commit/10c24f6398bf8fc987cb2e79fd33ee70964b7836))
* **CLI Onboarding:** Fix `isConsole` resolution in `login` step ([688bfcf](https://github.com/pjgm/serverless/commit/688bfcf00d276dcc39dc1b67e9a673ccbdc78512))
* **CLI Onboarding:** Fix resolution of onboarding message ([624536f](https://github.com/pjgm/serverless/commit/624536f77ebe1a0cd6759cb90ef1cb9a209fb64d))
* **CLI Onboarding:** Improve fix for initial variables resolution ([1f12b19](https://github.com/pjgm/serverless/commit/1f12b19a22bd40ce34c8bf45f090e46074409887))
* **CLI Onboarding:** Leave `app` intact with also enabled dashboard ([a043624](https://github.com/pjgm/serverless/commit/a0436248e7b127b56b5444a67870ea2671de0a21))
* **CLI Onboarding:** Only call `handleError` if plugin defined ([a80681f](https://github.com/pjgm/serverless/commit/a80681ffbf23391cb31d34b8eecaef310d9599a3))
* **CLI Onboarding:** Prevent side-effects of not supported `app` option ([0c65663](https://github.com/pjgm/serverless/commit/0c65663861b80a4fbd395018141ed90dd41cbdce))
* **CLI Onboarding:** Recognize Dashboard providers for deployment ([38ff287](https://github.com/pjgm/serverless/commit/38ff287bc79614803b82ada3728c1432381bc59b))
* **CLI Onboarding:** Setup `app` when console and dashboard enabled ([bffbfe3](https://github.com/pjgm/serverless/commit/bffbfe32fd54f5f1fa01db3fcbb81287be246092))
* **CLI Onboarding:** Support Dashboard providers with Console ([8825e86](https://github.com/pjgm/serverless/commit/8825e867d833a28ace051047ce17bf3cdc3e7526))
* **CLI Onboarding:** With console always favor console messaging ([f0d441e](https://github.com/pjgm/serverless/commit/f0d441e0d469640e04d880b81e361da539aa5f62))
* **CLI:** Bring back support for referencing nested configurations ([7339351](https://github.com/pjgm/serverless/commit/7339351de3b9829750a94bb5a98053da7c0b7bd5))
* **CLI:** Communicate access to Components CLI ([79b4718](https://github.com/pjgm/serverless/commit/79b4718dec5de1d567af25d1abd0e46d87ff1c6e))
* **CLI:** Correctly resolve version during local fallback ([bbfe742](https://github.com/pjgm/serverless/commit/bbfe742b2458f31254b11128b8ed506a47293abe))
* **CLI:** Display final packaging log only with `package` command ([9fcb283](https://github.com/pjgm/serverless/commit/9fcb28350e529c220fcbd3cdd602998e1b3adefc))
* **CLI:** Do not assume "string" param type, when not type set ([c9be9bc](https://github.com/pjgm/serverless/commit/c9be9bcc45d2da606d1660fb60156e56f5912e49))
* **CLI:** Do not attempt to resolve full config for `login` ([9b62d14](https://github.com/pjgm/serverless/commit/9b62d14e691eedafcefc0cc414c82f3f7d13636d))
* **CLI:** Do not crash on help request ([f6feb0b](https://github.com/pjgm/serverless/commit/f6feb0b7b3b5ceb727119056e44e756a8105ec5b))
* **CLI:** Do not duplicate variables error information ([2f62bdf](https://github.com/pjgm/serverless/commit/2f62bdf2316a76a0dd4b855e178857ecff7c7402))
* **CLI:** Do not recomment `frameworkVersion` when running pre release ([53490a5](https://github.com/pjgm/serverless/commit/53490a55183db5f304d0e3ef69feadd9a20fa815))
* **CLI:** Do not show options order deprecation info with help request ([ad8f9b0](https://github.com/pjgm/serverless/commit/ad8f9b059740bb2581445457b6751e918a57e585))
* **CLI:** Do not validate command when falling back to old version ([9624338](https://github.com/pjgm/serverless/commit/962433864ff4f52bf178b7afc1b6e54e58e58702))
* **CLI:** Do not validate configuration with `plugin ..` commands ([040036d](https://github.com/pjgm/serverless/commit/040036d1869ceb207da6dad53f17e1ee1b6ee20a))
* **CLI:** Ensure `--version` is only top level command option ([1f7534c](https://github.com/pjgm/serverless/commit/1f7534c4d89a0e37e61a8eea76f6f0241909d265))
* **CLI:** Ensure `processedInput` is properly resolved in local fallback ([464467e](https://github.com/pjgm/serverless/commit/464467e2bece1bf3f35fe60041fa170f412087d3))
* **CLI:** Ensure all expected command schemas in collections ([031ca4d](https://github.com/pjgm/serverless/commit/031ca4dd2aa35b3a15e00db0601a11b7b25d3b4d))
* **CLI:** Ensure command validation for service independent commands ([6022fb9](https://github.com/pjgm/serverless/commit/6022fb98331e8f7d8893a28d3dcb20d91d0a1e20))
* **CLI:** Ensure help output with missing provider.name ([dae9058](https://github.com/pjgm/serverless/commit/dae9058501ecc4ae8ff6b70e2bd1b22e914c241d))
* **CLI:** Ensure no general help is listed under interactive setup help ([132c830](https://github.com/pjgm/serverless/commit/132c830b0a86998efbae1b4984dc9cea85957d61))
* **CLI:** Ensure proper resolution of options for service commands ([#10846](https://github.com/pjgm/serverless/issues/10846)) ([dd421cc](https://github.com/pjgm/serverless/commit/dd421cc8a65816c59572c581e275455f9793754e))
* **CLI:** Ensure resolved CLI params are correct in local fallback ([65a1f38](https://github.com/pjgm/serverless/commit/65a1f3875cda7f06d3ab47f21362a630d7d0415f))
* **CLI:** Ensure support for upper case params ([b17c461](https://github.com/pjgm/serverless/commit/b17c461a1291728cda8fe6fbfbc7a9f56ab59d33))
* **CLI:** Ensure to copy and not modify preset schemas ([64684f2](https://github.com/pjgm/serverless/commit/64684f2ed58e643726e4cea403b80af9844575ab))
* **CLI:** Ensure to expose accurate `commandsSchema` in resolved input ([01b135c](https://github.com/pjgm/serverless/commit/01b135c69f731ec6841953491d310d06fd5740c0))
* **CLI:** Ensure to list version in case of fallback from some versions ([989cb82](https://github.com/pjgm/serverless/commit/989cb82db313177a64e062cc800eb85ba501fab5))
* **CLI:** Ensure to not diplay programmatic use deprecation ([fa626a8](https://github.com/pjgm/serverless/commit/fa626a8e22870d0e5ad549a9d7eab656e7e664aa))
* **CLI:** Ensure to not fallback to Framework on components run error ([15332c5](https://github.com/pjgm/serverless/commit/15332c55525b91dc0ad11d903789581fb5104b64))
* **CLI:** Ensure to not follow with project setup on existing path ([293cd6d](https://github.com/pjgm/serverless/commit/293cd6d0e2b595a35031eae1ae1f981a6e51e3f5))
* **CLI:** Ensure to pass through `serverless-tencent` exit code ([4d091b4](https://github.com/pjgm/serverless/commit/4d091b42cbcfadf8f8922aba9e46f756ebfe3e88))
* **CLI:** Ensure to recognize "-v" param as boolean in all cases ([82b95fc](https://github.com/pjgm/serverless/commit/82b95fc4924d4e93a7ae79bb741859df3dd464c0))
* **CLI:** Ensure to recognize interactive CLI command properly ([40fddcc](https://github.com/pjgm/serverless/commit/40fddcc0eecee0c34310ac36508975fdd58da939))
* **CLI:** Ensure to report only unrecognized sources as unrecognized ([27e21e8](https://github.com/pjgm/serverless/commit/27e21e8fca560732df3fa5c36c56682ef89b53c5))
* **CLI:** Ensure to respect `disabledDeprecations` config options ([05635c5](https://github.com/pjgm/serverless/commit/05635c5e2df2f63710cac333fa6b2bab4e53c0c7))
* **CLI:** Ensure to show help and version in context of invalid service ([3ffa549](https://github.com/pjgm/serverless/commit/3ffa54918342aeb9c334631c6f710aba234ba241))
* **CLI:** Ensure to strip error messages from colors in modern logs ([80005aa](https://github.com/pjgm/serverless/commit/80005aaf6b57aa8d013fe4cda0be52d494cd4d78))
* **CLI:** Ensure to support "_" in param names ([#8952](https://github.com/pjgm/serverless/issues/8952)) ([7e3e50b](https://github.com/pjgm/serverless/commit/7e3e50bca2c038398736eef8d867ff901da0aaae))
* **CLI:** Ensure to support `disableDeprecations` setting ([da476ad](https://github.com/pjgm/serverless/commit/da476ad7ac52b331ae47102e01a9270a18b40833))
* **CLI:** Ensure to write outputs with modern logs on `sls info` ([43d17de](https://github.com/pjgm/serverless/commit/43d17debee20bfc7ee535fd643df0538f8bee9f8))
* **CLI:** Fallback to local version only if we're not in its context ([7047c34](https://github.com/pjgm/serverless/commit/7047c349299ea829b0d43efedd191782dad10219))
* **CLI:** Fix `commands` pass to local installation ([80bddce](https://github.com/pjgm/serverless/commit/80bddce66729a82dde488a497e228cc42775a174))
* **CLI:** Fix `generate-event` and `test` commands schema visibility ([ae645e7](https://github.com/pjgm/serverless/commit/ae645e7e8ec165115cfb30fe24790a6741d858aa))
* **CLI:** Fix `help` command usage information ([#10175](https://github.com/pjgm/serverless/issues/10175)) ([254e70c](https://github.com/pjgm/serverless/commit/254e70cd0ad9bb1803d3a5741b966f5807e9d869))
* **CLI:** Fix `SIGINT` signal handling ([c5a3f69](https://github.com/pjgm/serverless/commit/c5a3f6907a115ea2d511b0aa9905a2e762514867))
* **CLI:** Fix ambiguity of '-v' option ([074647c](https://github.com/pjgm/serverless/commit/074647c50244b11573e5ece1cfd7429da0a9bf2f))
* **CLI:** Fix categorization of service dependent commands ([a1804f6](https://github.com/pjgm/serverless/commit/a1804f6300a469463ceb3d3e413816442ffdb435))
* **CLI:** Fix component template recognition in triage ([4494f77](https://github.com/pjgm/serverless/commit/4494f77f6111249d97295923a706883a8910840d))
* **CLI:** Fix configuration of a new service in interactive setup ([76fa62d](https://github.com/pjgm/serverless/commit/76fa62da3b050260063f52cb0586f626ff6de018))
* **CLI:** Fix dashboard error handler error reporting ([aa9dc0a](https://github.com/pjgm/serverless/commit/aa9dc0a8dc46c8dcb51a88c62d6337b8cc68f2b0))
* **CLI:** Fix deprecation warning message ([fa728e1](https://github.com/pjgm/serverless/commit/fa728e1478405f6a512afaef6f0719a2a273c6b8))
* **CLI:** Fix general help output when in context of AWS service ([0833fd0](https://github.com/pjgm/serverless/commit/0833fd03d17d292bd4393ecec9569328daae68d2))
* **CLI:** Fix handling of command options in help display ([2fffb16](https://github.com/pjgm/serverless/commit/2fffb168bc7f957ed9e8e048fd08dfb9669e8eca))
* **CLI:** Fix handling of container commands ([d9cf52b](https://github.com/pjgm/serverless/commit/d9cf52b2c81d9332f7289ef046fa161137ee1d19))
* **CLI:** Fix handling of provider URL handling ([7ebe133](https://github.com/pjgm/serverless/commit/7ebe133b35fa9affafd73b61ee4626d8ce5aee1f))
* **CLI:** Fix handling of singular `--config` param ([7bcad68](https://github.com/pjgm/serverless/commit/7bcad688c515a8c504f8958b7e15f3ac6d90e0d0)), closes [#7736](https://github.com/pjgm/serverless/issues/7736)
* **CLI:** Fix handling when local `serverless` is removed in command run ([1a3ccdb](https://github.com/pjgm/serverless/commit/1a3ccdbef8cd9c41b87f7fe440ca300970f3e138))
* **CLI:** Fix internal commands merge logic ([a9a48f6](https://github.com/pjgm/serverless/commit/a9a48f675e8695dc3b795218d0eb23553c33f9d8))
* **CLI:** Fix local installation fallback ([fa8c076](https://github.com/pjgm/serverless/commit/fa8c076c564377ec632992a6a156bc4937ec08e1))
* **CLI:** Fix log messages timing ([084a995](https://github.com/pjgm/serverless/commit/084a9955f440ee18847df8a3087aba38405883b7))
* **CLI:** Fix options schema for "info" command ([aa9d8df](https://github.com/pjgm/serverless/commit/aa9d8df2de20c4ba63af1c15ee3e966226c5079f))
* **CLI:** Fix options validations for custom providers ([5004fb1](https://github.com/pjgm/serverless/commit/5004fb1ea0ba168d6a7ccc0d07070e6b716f78a2))
* **CLI:** Fix reference to AWS service options ([6a8ea90](https://github.com/pjgm/serverless/commit/6a8ea9051865ea4975e335d952de3695d044a0f3))
* **CLI:** Fix resolution of "--config=<configPath>" format ([cd5a739](https://github.com/pjgm/serverless/commit/cd5a739265e2fe90f53f900f567eddcb9010b3aa))
* **CLI:** Fix resolution of empty valued params as `param=` ([5acdc0a](https://github.com/pjgm/serverless/commit/5acdc0a5e03994b6835a3be5411bffb905ca4cc2))
* **CLI:** Fix resolution of handler in case of local fallback ([7d31410](https://github.com/pjgm/serverless/commit/7d31410b74efb4c48c1c1b18ca33733a564268f2))
* **CLI:** Fix resolution of help for not integrated commands ([204f205](https://github.com/pjgm/serverless/commit/204f2051f6a5ca5f046eb905292dfae0c597e33f))
* **CLI:** Fix resolution of service path with nested config involved ([9b7315f](https://github.com/pjgm/serverless/commit/9b7315f080d5bbccf2c9e7d618e7a7dbeb9a12b2))
* **CLI:** Fix resources status log in verbose mode ([bcd8a02](https://github.com/pjgm/serverless/commit/bcd8a022a1e2e50a5d2708c374f4d5bcc30c80b5))
* **CLI:** Fix standalone detection (case of a fallback from standalone) ([1681af4](https://github.com/pjgm/serverless/commit/1681af4897eeec20c1d1af292f9bfde5b1e9ffc3))
* **CLI:** Fix standalone detection on Windows ([4bc8e2e](https://github.com/pjgm/serverless/commit/4bc8e2e1944364e2c218cbfc05039c43afa9ab01))
* **CLI:** Fix support for `-c` (`--config`) shortcut ([06fc4df](https://github.com/pjgm/serverless/commit/06fc4df7880e8f03cb0dbd5229b7bd2a92e11a87))
* **CLI:** Fix validation of `deprecationNotificationMode` config option ([916c76f](https://github.com/pjgm/serverless/commit/916c76f48ca86c3e31b719d2bb655c34d0287cec)), closes [#9762](https://github.com/pjgm/serverless/issues/9762)
* **CLI:** Get `serverless-tencent` version from all supported locations ([395ea7d](https://github.com/pjgm/serverless/commit/395ea7d2a8d7c6d95417bde8448e6d58c2094125))
* **CLI:** Handle gently case where temp folder is on other device ([a030636](https://github.com/pjgm/serverless/commit/a0306365fc2c18c04698640723db2f4efeb34e2f))
* **CLI:** Improve error handler resolution ([0dedd3e](https://github.com/pjgm/serverless/commit/0dedd3e8790f568527b8a2444720fe47048ba719))
* **CLI:** Improve handling of container commands ([6ec463c](https://github.com/pjgm/serverless/commit/6ec463cbe7f0bc6a7827a504175f2c3aae9bb8d6))
* **CLI:** Mark 'help' as command that doesn't depend on external plugins ([4660acd](https://github.com/pjgm/serverless/commit/4660acd324cfa6c786245ea581691a23758ce960))
* **CLI:** Mark `dashboard` command with optional service dependency ([9a8e7e4](https://github.com/pjgm/serverless/commit/9a8e7e44b44fdcf4c43d6e11c5eefa5051782506))
* **CLI:** Move deprecation report to init phase ([1eaa626](https://github.com/pjgm/serverless/commit/1eaa6260aa9f747d0aa01006ce54d3313e7b7e0f))
* **CLI:** Output "Plugin: " prefix only for external plugin comands ([acf720c](https://github.com/pjgm/serverless/commit/acf720cdefd65508fc0e5183271cff03009b7441))
* **CLI:** Properly report SDK version when handling errors ([a79473d](https://github.com/pjgm/serverless/commit/a79473d8b1dac5c4da1473dec4b02ba192e696ca))
* **CLI:** Recognize "--stage" as provider agnostic option ([271ac82](https://github.com/pjgm/serverless/commit/271ac8281c10e23ce609165582b3b996b60d5bd1))
* **CLI:** Recognize "--version" option in commands help ([6cefe7a](https://github.com/pjgm/serverless/commit/6cefe7a08452586498fe1612daf6f95f5a754925))
* **CLI:** Recognize "-s" as "--stage" alias, when expected ([9ae6045](https://github.com/pjgm/serverless/commit/9ae604591dbb7e82aff0668d2055ed9d69bb920a))
* **CLI:** Recognize `--aws-profile` option by schema ([014ff94](https://github.com/pjgm/serverless/commit/014ff949b7a8d62e246fd47f2addc48a37e362e2))
* **CLI:** Recognize `--env` option for `sls invoke local` as multiple  ([a941e87](https://github.com/pjgm/serverless/commit/a941e87cbfbd272f27fc6360c7a733b337e83f2d)), closes [#9131](https://github.com/pjgm/serverless/issues/9131)
* **CLI:** Recognize `--stage` & `--region` on every AWS service command ([bfde219](https://github.com/pjgm/serverless/commit/bfde21907be3508350bf2487d2ef8bc69be695ad))
* **CLI:** Recognize `--verbose` option in `info` command ([b124152](https://github.com/pjgm/serverless/commit/b1241522ec378f7b7b431050ddc861fef040efc4))
* **CLI:** Recognize CLI aliases as documented ([7a804e1](https://github.com/pjgm/serverless/commit/7a804e1c06b0991e2f9371b3bb794c660e2514d4)), closes [#7106](https://github.com/pjgm/serverless/issues/7106)
* **CLI:** Reject multitple 'config' params ([#7728](https://github.com/pjgm/serverless/issues/7728)) ([ca2a73f](https://github.com/pjgm/serverless/commit/ca2a73f91a86ae41b4cf48384177c0fd74ff4f1f))
* **CLI:** Remove bluebird config ([1019e60](https://github.com/pjgm/serverless/commit/1019e608762c45d1c868fce15224aca4c4e5a56c))
* **CLI:** Respect old Node.js versions in version detection ([427920e](https://github.com/pjgm/serverless/commit/427920ee0fc1c98109c0b673c794baac1cc5caf7))
* **CLI:** Show interactive help unconditionally on --help-interactive ([ff0af1e](https://github.com/pjgm/serverless/commit/ff0af1e6ac8b89b4d610c141c78fe0fea843a5de))
* **CLI:** Show version info unconditionally on -v or --version ([c042dd5](https://github.com/pjgm/serverless/commit/c042dd5144e4e283e565da97933d03bc70b3c8e9))
* **CLI:** Unconditionally crash on unrecognized command ([f1af86a](https://github.com/pjgm/serverless/commit/f1af86ab55b873e87a1d6bef2c0b02e133eba4a2))
* Complete async refactor for aws/deploy and customResources ([5331065](https://github.com/pjgm/serverless/commit/533106515e2a7a943f2a7f9f68ce864062203a72))
* **Components:** Handle gently initialization errors ([7b0c18e](https://github.com/pjgm/serverless/commit/7b0c18ededa149687942fb3318fefb26656e9e9d))
* **Config Schema:** Add type to logRetentionInDays ([#8844](https://github.com/pjgm/serverless/issues/8844)) ([ec12a2b](https://github.com/pjgm/serverless/commit/ec12a2be0a9510ababca8ffc5fe8836dcef82773))
* **Config Schema:** Address invalid schema definitions ([9e1fe0a](https://github.com/pjgm/serverless/commit/9e1fe0ad5da8b936ccb238041fb2b452e6309faf))
* **Config Schema:** Allow both `arn` and `topicName` in `sns` event ([c27f5b3](https://github.com/pjgm/serverless/commit/c27f5b3e9eb322338c92bac5d3f67798fb5c93f2))
* **Config Schema:** Bring back non-array supported variants ([244ae11](https://github.com/pjgm/serverless/commit/244ae111c19d6e39b121ac387a38747823af6723)), closes [#8319](https://github.com/pjgm/serverless/issues/8319)
* **Config Schema:** Do not mark `layers[].path` as required ([0394025](https://github.com/pjgm/serverless/commit/03940254385e138eb40f2f25bd56fcdbee0c3a22))
* **Config Schema:** Ensure schema for core properties ([a3f624e](https://github.com/pjgm/serverless/commit/a3f624e25cb257afc5d8668a8a5e63e6c67d8827))
* **Config Schema:** Ensure to preserve `null` properties in user config ([c93a799](https://github.com/pjgm/serverless/commit/c93a799653d4825339f8bf9f4556cc8a1f2a9838))
* **Config Schema:** Ensure to validate `provider` as in config file ([b04ab55](https://github.com/pjgm/serverless/commit/b04ab55fabd193b879244718ed87047ec961904c))
* **Config Schema:** Ensure to validate direct config where applicable ([af60319](https://github.com/pjgm/serverless/commit/af603198a1522094ca0607c24e9325657a41e442))
* **Config Schema:** Fix "Fn:Sub" function definition ([#8174](https://github.com/pjgm/serverless/issues/8174)) ([72e77f5](https://github.com/pjgm/serverless/commit/72e77f57557e9289d63b5bc8839e968f539e9ac3))
* **Config Schema:** Fix `defineFunctionEventProperties` ([e32b771](https://github.com/pjgm/serverless/commit/e32b7714253108f9078d2218e68c5994f20cde64)), closes [#8486](https://github.com/pjgm/serverless/issues/8486)
* **Config Schema:** Fix `Fn::Join` delimiter length ([#8349](https://github.com/pjgm/serverless/issues/8349)) ([faa1dce](https://github.com/pjgm/serverless/commit/faa1dce9eef4384cda07c8553a0d972c06be0e2f))
* **Config Schema:** Fix `provider.apiKeys` required properties config ([73f6549](https://github.com/pjgm/serverless/commit/73f6549157cfa35413229060a6f0bf05c1405d6e))
* **Config Schema:** Fix `provider.apiKeys` schema ([166f3ce](https://github.com/pjgm/serverless/commit/166f3ce6bf225342dfa3d4399771b9fa3dccf897))
* **Config Schema:** Fix `provider.tags` schema ([#8314](https://github.com/pjgm/serverless/issues/8314)) ([fc34140](https://github.com/pjgm/serverless/commit/fc34140f4ec03958564a5868b339c40056f6b04e))
* **Config Schema:** Fix API Gateway authorizer schema ([f166546](https://github.com/pjgm/serverless/commit/f1665460d4bba7562ad88ecf7a471949bfd1baa4))
* **Config Schema:** Fix AWS `stream` event `consumer` schema ([b0fe67d](https://github.com/pjgm/serverless/commit/b0fe67d8466c97f0be045d87780e5e78f6611e7b))
* **Config Schema:** Fix CF template extension `Transform`schema ([#8229](https://github.com/pjgm/serverless/issues/8229)) ([6961b62](https://github.com/pjgm/serverless/commit/6961b629e72aada33ff5a3a12f1a04f686b58329))
* **Config Schema:** Fix configuration of common properties in `resources` ([9399f2b](https://github.com/pjgm/serverless/commit/9399f2b89c8a841d1d7d96a22a8de640d8214479)), closes [#8553](https://github.com/pjgm/serverless/issues/8553)
* **Config Schema:** Fix errors normalization for oneOf case ([f4803ee](https://github.com/pjgm/serverless/commit/f4803ee363253ebefc1c509d8d808db53bcc6e7a))
* **Config Schema:** Fix errors normalization with external refs ([d171f54](https://github.com/pjgm/serverless/commit/d171f5476d260f90ff0fe9916aed4a0eea49dfde))
* **Config Schema:** Fix IAM Policy resource reference schema ([85f823c](https://github.com/pjgm/serverless/commit/85f823cf46713b110d0f70892e6130315e1d3972))
* **Config Schema:** Fix required properties configuration ([1dd42b0](https://github.com/pjgm/serverless/commit/1dd42b0c62d6eb0cc6036fe1529e85e05c616a09))
* **Config Schema:** Improve AWS tags validation ([b093609](https://github.com/pjgm/serverless/commit/b093609f7952d5a63c91e6435b6a3a7d7d09cb1a))
* **Config Schema:** Recognize `Condition` on resource configuration ([3477562](https://github.com/pjgm/serverless/commit/34775627f2eb4477e0e76a8d5570a07d6f259c8d))
* **Config Schema:** Recognize `provider.websocketsDescription` ([#10663](https://github.com/pjgm/serverless/issues/10663)) ([9778751](https://github.com/pjgm/serverless/commit/977875144798d4c1e2e37ecccc7bbab286f4684d))
* **Config Schema:** Recognize API Gateway resource policy shorthands ([b7901cd](https://github.com/pjgm/serverless/commit/b7901cdb77cb2c81dee62cb614d39d5d2fc824ff)), closes [#8506](https://github.com/pjgm/serverless/issues/8506)
* **Config Schema:** Recognize boolean format for `provider.logs.restApi` ([ab5cdd1](https://github.com/pjgm/serverless/commit/ab5cdd10aad2cc64331b67cab716a0d1ae120264))
* **Config Schema:** Recognize catch-all pattern in disabledDeprecations ([c9ee6d5](https://github.com/pjgm/serverless/commit/c9ee6d53b688561a154b55dc4fd4fca648ff2ab1))
* **Config Schema:** Recognize CF intrinsic functions in vpc config ([e75e998](https://github.com/pjgm/serverless/commit/e75e998e9238c8d59653ec2533c9fb7c3f0e546a)), closes [#8283](https://github.com/pjgm/serverless/issues/8283)
* **Config Schema:** Recognize deployment valid env variables format ([eb5e548](https://github.com/pjgm/serverless/commit/eb5e54847e6e2f6b89a1b5325df4d8421efe479a))
* **Config Schema:** Recognize enhanced object syntax for plugins ([#8259](https://github.com/pjgm/serverless/issues/8259)) ([4b86fa5](https://github.com/pjgm/serverless/commit/4b86fa5759a4b52771bb69d3ea50762b87583765))
* **Config Schema:** Recognize string format of `service` ([#8537](https://github.com/pjgm/serverless/issues/8537)) ([6c6881c](https://github.com/pjgm/serverless/commit/6c6881c853d9a42ed3c99f7c7acaa7cb98bd0a1b))
* **Config Schema:** Recognize string value at DependsOn ([4c36753](https://github.com/pjgm/serverless/commit/4c367535074f7b82799ed4bd16cd5fcdef445eb5))
* **Config Schema:** Report configuration errors as warnings ([e1ee0dc](https://github.com/pjgm/serverless/commit/e1ee0dc6f9cf03c872e65d1e258e1162e2d6071e))
* **Config Schema:** Revert invalid "oneOf" based validation ([a9b28b6](https://github.com/pjgm/serverless/commit/a9b28b6d7f703ce29e92d05fc129a2a3b5fbce2a))
* **Config Schema:** Revert to ajv v6 ([#8762](https://github.com/pjgm/serverless/issues/8762)) ([d1c6568](https://github.com/pjgm/serverless/commit/d1c656838f5d19dd2b1d214c30ea2f292915a5b2))
* **Config Schema:** Run validation logic unconditionally ([df1b8a9](https://github.com/pjgm/serverless/commit/df1b8a9433615c9c6efdff4dcef1f5477ea46d8a))
* **Config Schema:** Safe generation of standalone AJV validator ([6093ee4](https://github.com/pjgm/serverless/commit/6093ee480aceba35d7eb74d7a0ea3c378a596e63))
* **Config Schema:** Support CF functions for managed policies ([#9089](https://github.com/pjgm/serverless/issues/9089)) ([5f5d2e5](https://github.com/pjgm/serverless/commit/5f5d2e580e267ad8bbd34f29c4613ca751908992))
* **Config Schema:** Support empty string as environment variables ([ff9db3e](https://github.com/pjgm/serverless/commit/ff9db3e7bd0e4cd1261984e048373afc843eb053))
* **Config Schema:** Treat explicit `null` or `undefined` as no value ([e5e42ba](https://github.com/pjgm/serverless/commit/e5e42bab8cec9c508e465ee259ec75aff183168c))
* **Config Schema:** Use ajv formats ([036698c](https://github.com/pjgm/serverless/commit/036698ca5b46dc27a2844114813812a83f64813e))
* **Console:** Ensure errorneus resolution of url to not break deploys ([f72c595](https://github.com/pjgm/serverless/commit/f72c5958c354c47123427988f6a48528987c45cb))
* **Console:** Ensure single layer attachment with `package.individually` ([fac8a73](https://github.com/pjgm/serverless/commit/fac8a73eec9ed6a6cf7535a1c723da3cb882905a))
* **Console:** Ensure to always deploy CF stack to `us-east-1` region ([f0932a4](https://github.com/pjgm/serverless/commit/f0932a4e1d5ad23f6d88b4b462a957e1ec115066))
* **Console:** Ensure to package extension without errors ([64ee4a5](https://github.com/pjgm/serverless/commit/64ee4a528815354905b1f5c92fb7ba1e1604e4b4))
* **Console:** Fix console url for platform dev stage case ([543612a](https://github.com/pjgm/serverless/commit/543612acbec08a76c085f84ff18578c3875810c2))
* **Console:** Fix reference to bucket name in CF template ([fcaa9c2](https://github.com/pjgm/serverless/commit/fcaa9c2c4f756b552ba990438df8866e304f3b56))
* **Console:** Fix upload of extension to S3 bucket ([23719d8](https://github.com/pjgm/serverless/commit/23719d868c0b4270b57ea025a4271c62a58cb65f))
* **Console:** Keep currently attached layers with `function deploy` ([198d3b7](https://github.com/pjgm/serverless/commit/198d3b7738e36ca1d8e516e257b2be81e04b8e6a))
* **Console:** Prevent AWS region mismatch ([43480ee](https://github.com/pjgm/serverless/commit/43480ee872d7d999d398eccdf56172860d40be56))
* **Console:** Respect custom deployment bucket configuration ([4d705cc](https://github.com/pjgm/serverless/commit/4d705cc96d1bec29c3328879e41a71f907b0696d))
* correct misspelled eventType value ([d381106](https://github.com/pjgm/serverless/commit/d381106b8e176fcb82690c99740ecbede2450668))
* Correctly define print hook ([#8979](https://github.com/pjgm/serverless/issues/8979)) ([265b9b8](https://github.com/pjgm/serverless/commit/265b9b80f56cd370f7186fe82dd1ad4455565fb3))
* Dashboard documentation improvements ([bb4d7c8](https://github.com/pjgm/serverless/commit/bb4d7c8938c3eff0b8412137e25c352327650fa5))
* **Dashboard:** Ensure service independent commands work unconditionally ([d8a73b8](https://github.com/pjgm/serverless/commit/d8a73b8326825b3020fa238057072c837d188d3c))
* **deploy:** Functions no longer need to maintain order ([18fbc6e](https://github.com/pjgm/serverless/commit/18fbc6ef7638b3e0d0d89e765156f1ab828cd7ac)), closes [#1683](https://github.com/pjgm/serverless/issues/1683)
* **deploy:** Transform parameters paths into alphanumeric paths for resource keys ([1ba1079](https://github.com/pjgm/serverless/commit/1ba1079c6cbb53c6b037e75cfa21c883c2748293))
* Display version related deprecations only with functions ([4f64e56](https://github.com/pjgm/serverless/commit/4f64e560b9157dc8700328686a778ebd2a78ba9e))
* Do not crash on `null` resource properties input ([#11789](https://github.com/pjgm/serverless/issues/11789)) ([86bb67d](https://github.com/pjgm/serverless/commit/86bb67d15fe611cdaffb6aea57d25cb0cfc51029))
* Do not overwrite `go.mod` on `make` in Go template ([#7245](https://github.com/pjgm/serverless/issues/7245)) ([1793cf8](https://github.com/pjgm/serverless/commit/1793cf8d7a55b85fc6505ae493dcca2292e443d2))
* Do not set optional ParallelizationFactor when not explicitly set ([f29dd79](https://github.com/pjgm/serverless/commit/f29dd7943eccb354805866f153ebccd2232c3517)), closes [#7049](https://github.com/pjgm/serverless/issues/7049)
* Do not stumble on missing resource properties ([f87aee2](https://github.com/pjgm/serverless/commit/f87aee268dd19f9b90a7018032c77454d2084f12))
* Do not use isDashboard in onboarding flow ([#12160](https://github.com/pjgm/serverless/issues/12160)) ([1f8d786](https://github.com/pjgm/serverless/commit/1f8d786b16d7682912c464d67add589f48666987))
* Dont depend on default execution role when custom role provided ([29f0e9c](https://github.com/pjgm/serverless/commit/29f0e9c840e4b1ae9949925bc5a2a9d2de742271))
* duplicated and broken markdown links to api gw ([ffe5f42](https://github.com/pjgm/serverless/commit/ffe5f42bafd86260d4df4bf8527d664a34100731))
* Ensure `serverless.ts` is handled properly at plugin commands  ([dc96b9a](https://github.com/pjgm/serverless/commit/dc96b9a876b04e10ced474b7bb32416a204c67a3)), closes [#7806](https://github.com/pjgm/serverless/issues/7806)
* Ensure async function is memoized as promise returning ([eb0b65d](https://github.com/pjgm/serverless/commit/eb0b65dc1673dde94379bf22bcbdf83d1baace5c))
* Ensure AWS creds resolution for local docker invocation ([#7375](https://github.com/pjgm/serverless/issues/7375)) ([90b3a8f](https://github.com/pjgm/serverless/commit/90b3a8f81eea8fb27c24b2b05888e7f386ee47bd))
* Ensure AWS env vars in local invocation made with docker ([#7349](https://github.com/pjgm/serverless/issues/7349)) ([c09f718](https://github.com/pjgm/serverless/commit/c09f71897a67fe8ec98d460075f0f02b397f8ee5))
* Ensure AWS EventBrigde target ids fit 64 chars limit ([#7359](https://github.com/pjgm/serverless/issues/7359)) ([103fdac](https://github.com/pjgm/serverless/commit/103fdacc294ab87f4bd079847d05d9448fd4b494))
* Ensure CF stacks are deleted on failed creaton attempt ([#7158](https://github.com/pjgm/serverless/issues/7158)) ([53a18cb](https://github.com/pjgm/serverless/commit/53a18cbff6d3d2d6698e98cf0dd8a7eba21fdf58)), closes [#6612](https://github.com/pjgm/serverless/issues/6612) [#5631](https://github.com/pjgm/serverless/issues/5631)
* Ensure consistency in IAM role and policy names ([#7357](https://github.com/pjgm/serverless/issues/7357)) ([9a0aaa8](https://github.com/pjgm/serverless/commit/9a0aaa843b19cb5bc0ddfe9a25b96e3c64d82749))
* Ensure correct payload generation for functions without events ([6674660](https://github.com/pjgm/serverless/commit/6674660b173606d75d8b2ad9bbc11dcef4d684b5))
* Ensure deprecation logs support mute settings from service config ([4e69c76](https://github.com/pjgm/serverless/commit/4e69c76e07a862981e8a9ea9011c98098c9da347))
* Ensure detection of external plugins is multi instance safe ([0f35375](https://github.com/pjgm/serverless/commit/0f353750f16b5befff243221e2c5e3c66376bcb0))
* Ensure deterministic WebSockets deployment id ([#7248](https://github.com/pjgm/serverless/issues/7248)) ([9f0131f](https://github.com/pjgm/serverless/commit/9f0131fedf60e9104f38702d01e103b9a3b0f629))
* Ensure early access to configuration in logDeprecation method ([53b9762](https://github.com/pjgm/serverless/commit/53b97621dccdef8f9f2e15e2f4f31045b46970e2))
* Ensure maximum API gateway timeout ([#11453](https://github.com/pjgm/serverless/issues/11453)) ([c5ca9b7](https://github.com/pjgm/serverless/commit/c5ca9b78faef8bc6c23b215f847dc4383b8165e7))
* Ensure necessary IAM role for handling existing cognito pools ([9500361](https://github.com/pjgm/serverless/commit/950036157dfc9c077a7ba81c887906b44c2ed241)), closes [#6579](https://github.com/pjgm/serverless/issues/6579)
* Ensure not to autocomplete hidden commands ([3f7f532](https://github.com/pjgm/serverless/commit/3f7f532b88c9bdcc25a2b53a93e11484131c28ab))
* Ensure that `list-version` is invoked ([ed60978](https://github.com/pjgm/serverless/commit/ed609781ca3371a2ea3bfda263f093f0f8a7f7f4))
* Ensure to attempt minimal config resolution for plugin commands ([af9a238](https://github.com/pjgm/serverless/commit/af9a238f852fb04fbfcdfa57b9b313426f579bd1))
* Ensure to handle empty func definition with meaningful error ([86e0b6d](https://github.com/pjgm/serverless/commit/86e0b6ddbba7f356989ba7c1617c2a4160e7503a))
* Ensure to inspect configuraiton after it's fully resolved ([f60fb55](https://github.com/pjgm/serverless/commit/f60fb55a0b60603039d92d7467d0b231e247c819))
* Ensure to log deprecation at initialization stage ([1b26075](https://github.com/pjgm/serverless/commit/1b26075fb51c71dd169c4800822842f614465388))
* Ensure to memoize config file resolution by instance ([3177e40](https://github.com/pjgm/serverless/commit/3177e40cee1d91a5b054dd47cdb6f540436cc507))
* Ensure to not add double entries during `plugin install` ([c4ca97d](https://github.com/pjgm/serverless/commit/c4ca97d0100a28d02012b144c1a9ba06f7ac7dc6))
* Ensure to not crash when `~/.serverless` is not accessible ([#11403](https://github.com/pjgm/serverless/issues/11403)) ([b95c749](https://github.com/pjgm/serverless/commit/b95c7496ec4a49aef756692a1ef59b61e2d95d4b))
* Ensure to not create cognito pools marked as 'existing' ([9a2f95b](https://github.com/pjgm/serverless/commit/9a2f95bc03bc3ac3da115c5f4f547a9458e68d5f))
* Ensure to not login back accidentaly on logout operation ([ec9eac4](https://github.com/pjgm/serverless/commit/ec9eac4edc6ebeded0276eeb12c7f77a7a7f7eda))
* Ensure to package CLI script ([a687e91](https://github.com/pjgm/serverless/commit/a687e9190d861f11ec1fc9a194335b3012b246b9))
* Ensure to preserve `undefined` valued propeties as `undefined` ([2e26e07](https://github.com/pjgm/serverless/commit/2e26e07f921575dbb10c049eaa7a864867e696c6))
* Ensure to report validation errors with ServerlessError ([813f7d3](https://github.com/pjgm/serverless/commit/813f7d3dbe714f4e615dd0cfa14aabb973894fd8))
* Ensure to support deprecation settings at early stage of processing ([011e0ce](https://github.com/pjgm/serverless/commit/011e0ce45cec4b1273268fcab4f99e377fae092e))
* Expose remote lambda invocation failure as user error ([8f3d4e4](https://github.com/pjgm/serverless/commit/8f3d4e4bdb1df1e107c5113d013164a2396f0f64))
* Expose template errror with user error ([07b60a6](https://github.com/pjgm/serverless/commit/07b60a6bb42796e6f060730ce4bf22762942b0b8))
* Find origins using domain name and path ([cbb42ce](https://github.com/pjgm/serverless/commit/cbb42ce240cafda946436b2ed862af16f16a5815))
* Fix `functions[]` validation (ignore `null` values) ([922ec00](https://github.com/pjgm/serverless/commit/922ec0093f0d4ab6f2b2055c6e6f2d5ec1f9d06e))
* Fix `projectDir` pattern in config schema ([8954b5f](https://github.com/pjgm/serverless/commit/8954b5f9cc3e2431036ccb876c46fb8cc99dc0d9))
* Fix `sls logs` so it also covers output from aliases ([#7270](https://github.com/pjgm/serverless/issues/7270)) ([4468805](https://github.com/pjgm/serverless/commit/4468805d2a93224b63d99dc04f6c6056226af689)), closes [#7214](https://github.com/pjgm/serverless/issues/7214)
* Fix and improve openwhisk-java-maven templates ([#7164](https://github.com/pjgm/serverless/issues/7164)) ([41d7d0b](https://github.com/pjgm/serverless/commit/41d7d0bf0798188284f38e0f4e3effadad1f8d42))
* Fix AWS missing credentials handling ([7af0cd8](https://github.com/pjgm/serverless/commit/7af0cd8c280e0f4fc374e859c0223bc0c3455f63))
* Fix AWS partition reference in APIGW CloudWatch role setup ([fc74c28](https://github.com/pjgm/serverless/commit/fc74c287f68deb20266d011d9376d13117c11161)), closes [#7100](https://github.com/pjgm/serverless/issues/7100)
* Fix AWS tags validation schema ([#8766](https://github.com/pjgm/serverless/issues/8766)) ([4dff8e5](https://github.com/pjgm/serverless/commit/4dff8e53a64ad38a2b8515ca2543b49c001a779c))
* Fix aws-sdk workaround ([de38640](https://github.com/pjgm/serverless/commit/de386405b206d3ebace105992e9c7eb7ad6d7f94))
* Fix bug introduced with to `.flat()` refactor ([6bc8615](https://github.com/pjgm/serverless/commit/6bc8615df70f32f359b5b465df55d73cfac0571b))
* Fix changes detection when user package artifact is involved ([05499e6](https://github.com/pjgm/serverless/commit/05499e6083d4b36ba9b80b271b2becf4249dbbc6)), closes [#7742](https://github.com/pjgm/serverless/issues/7742)
* Fix CLI params resolution (switch to yargs-parser) ([#7187](https://github.com/pjgm/serverless/issues/7187)) ([780fb46](https://github.com/pjgm/serverless/commit/780fb46e726faf147ba16d190307bf1948ee53b3)), closes [#6083](https://github.com/pjgm/serverless/issues/6083)
* Fix credentials validation in EC2 environment ([#6977](https://github.com/pjgm/serverless/issues/6977)) ([f8ee027](https://github.com/pjgm/serverless/commit/f8ee0279037ba35b4c32f5872fcff4e741898db1))
* Fix custom resource lambda artifact generation ([84b1d1e](https://github.com/pjgm/serverless/commit/84b1d1eb11f876057fc9f243d728bbc61fe1defb))
* Fix function references when represented by alias ([#11788](https://github.com/pjgm/serverless/issues/11788)) ([16dd286](https://github.com/pjgm/serverless/commit/16dd286a1d8aa764003565bcd6d7334be290e9bf))
* Fix function version param handling in `rollback function` command ([03ad56b](https://github.com/pjgm/serverless/commit/03ad56b8e189f236222431856dd43afbebdce417)), closes [#7648](https://github.com/pjgm/serverless/issues/7648)
* Fix handing of removal of custom APIGW resource policy ([#7002](https://github.com/pjgm/serverless/issues/7002)) ([802f81f](https://github.com/pjgm/serverless/commit/802f81fa5c8048e4f8fb0b792594a357928df877)), closes [#6789](https://github.com/pjgm/serverless/issues/6789) [#6789](https://github.com/pjgm/serverless/issues/6789)
* Fix handler resolution (multi . case) for local invocation ([#7398](https://github.com/pjgm/serverless/issues/7398)) ([d84e9e7](https://github.com/pjgm/serverless/commit/d84e9e7d1e440b5bfaae39b4cfefd83f8ac2e8b9))
* Fix handling of `null` value ([#11506](https://github.com/pjgm/serverless/issues/11506)) ([c4902f3](https://github.com/pjgm/serverless/commit/c4902f3b103e3c683eb2a8dd04acc4e217a4d276))
* Fix handling of `redrivePolicy` in SNS events. ([#7277](https://github.com/pjgm/serverless/issues/7277)) ([292b1ca](https://github.com/pjgm/serverless/commit/292b1caf58583a7935673e22fc7f505b9f9871bc))
* Fix handling of invalid range put into `frameworkVersion` ([0d5a480](https://github.com/pjgm/serverless/commit/0d5a480fd0fe7abbc1998b9f72707589541f0639))
* Fix handling of numeric error codes coming from AWS SDK requests ([f2cdbae](https://github.com/pjgm/serverless/commit/f2cdbae1eb6d327935336a38deda099b8f5ffee2))
* Fix handling of pre-releases in frameworkVersion validation ([c0fb04a](https://github.com/pjgm/serverless/commit/c0fb04af3d2ec35436e02778b3a23f75f45ad7bb))
* Fix internal unrecognized command error processing ([a89e36a](https://github.com/pjgm/serverless/commit/a89e36a0e73df141a486b8a151bb2cfb228a9f5d))
* Fix menu for dashboard documentation ([8f266af](https://github.com/pjgm/serverless/commit/8f266af8308fa9b89327792dd037c4fe14bb14af))
* Fix mishandling of cachedCredentials in invokeLocal ([6ad5163](https://github.com/pjgm/serverless/commit/6ad516323b99cadc4ae1ac323d76141b652ac123)), closes [#7050](https://github.com/pjgm/serverless/issues/7050) [#7044](https://github.com/pjgm/serverless/issues/7044)
* Fix packaging logic after regression introduced with [#7742](https://github.com/pjgm/serverless/issues/7742) ([#7743](https://github.com/pjgm/serverless/issues/7743)) ([de4aee3](https://github.com/pjgm/serverless/commit/de4aee3f255fb2676d943364bc34820ae210db01))
* Fix provisioned concurrency support ([3195e5e](https://github.com/pjgm/serverless/commit/3195e5e98fc98dbb0b463f612f0f270569cbf17b)), closes [#7059](https://github.com/pjgm/serverless/issues/7059)
* Fix schema for `Fn::Split` for `vpc` config ([7338358](https://github.com/pjgm/serverless/commit/7338358126ac249374e341b7b19ce83582ecff1d))
* Fix support for relative plugins.localPath ([617b479](https://github.com/pjgm/serverless/commit/617b479fb79d7d765ebcc053cd8ea4f8b95b265f)), closes [#7117](https://github.com/pjgm/serverless/issues/7117)
* fixed regression preventing including files outside working dir ([9c4848b](https://github.com/pjgm/serverless/commit/9c4848bea56592ec323145a13740b81692779f31))
* Follow symlinks when writing a config ([#7374](https://github.com/pjgm/serverless/issues/7374)) ([3e1e1f4](https://github.com/pjgm/serverless/commit/3e1e1f486c4f6e283e172c99d9a38838bfbe2ab6))
* **GITHUB-6525-5172:** Rewrite copyDirContentsSyncAllow to call fs-extra::copySync() on the directories instead of calling it on the files to copy individually. ([5952712](https://github.com/pjgm/serverless/commit/5952712085f2d17cd71de66a5b22e02eb726821e)), closes [#6525](https://github.com/pjgm/serverless/issues/6525) [#5172](https://github.com/pjgm/serverless/issues/5172)
* Handle account being integrated with an existing org ([#12149](https://github.com/pjgm/serverless/issues/12149)) ([561a875](https://github.com/pjgm/serverless/commit/561a875da767a23e6bc1cc314e726ff674ab9df1))
* Handle gently npm response errors ([ab77a11](https://github.com/pjgm/serverless/commit/ab77a11e135ec879b3309205d8bfe010ceb68e9e))
* handle gilab urls with parse-github-url package ([69c7215](https://github.com/pjgm/serverless/commit/69c721567dfd8bc875c1ac19c3dbc07bf2357991))
* Implement context.log function for invoke local command on Python environment. ([0e6423c](https://github.com/pjgm/serverless/commit/0e6423cbc6f6a958413eacea646c3e8422de3add))
* Improve `functions` validation ([3e58d62](https://github.com/pjgm/serverless/commit/3e58d628e7b8f4dbc8e14adf94dd98546099f3be))
* Improve dashboard documentation ([ad8bbf1](https://github.com/pjgm/serverless/commit/ad8bbf1e13d9ba641f65a42ce95d2b0af7e1b4dd))
* Improve dashboard documentation ([f67df7f](https://github.com/pjgm/serverless/commit/f67df7fd1b409df512673ab4a795657a3d90fa6f))
* Improve detection of `tty` ([0c810bf](https://github.com/pjgm/serverless/commit/0c810bf96a9f1000d9dead9459e0db652819ea02))
* Improve error handling in config file resolution ([de2c68d](https://github.com/pjgm/serverless/commit/de2c68d02312f047aa7f83b0b339074b40df7854))
* Improve error message for CLI param validation ([a2ea68d](https://github.com/pjgm/serverless/commit/a2ea68d5be4583f71400db4fa4fc27575c8c664b)), closes [#9846](https://github.com/pjgm/serverless/issues/9846)
* Improve validation of min supported Node version ([bf084f3](https://github.com/pjgm/serverless/commit/bf084f3edd0891bb4947c9727c8d85684c3a423d))
* Limited permission for authorizers ([c05dcb3](https://github.com/pjgm/serverless/commit/c05dcb3432c16fe5cf25bc3c796f9feb92e5421a))
* Local credentials should be resolved in onboarding command ([#12148](https://github.com/pjgm/serverless/issues/12148)) ([307865d](https://github.com/pjgm/serverless/commit/307865d0525d551f188a1c86399533f78d7b15c3))
* **methods:** Add default 200 code if one is not supplied ([27bbbb9](https://github.com/pjgm/serverless/commit/27bbbb912bc38181d6288cf2c6196facf717f9c4))
* **methods:** CORS preflight retains origin and headers per path ([5c0050d](https://github.com/pjgm/serverless/commit/5c0050d1a0740c51f09a3cfe5b7ce6f6622887d4)), closes [#2024](https://github.com/pjgm/serverless/issues/2024) [#1960](https://github.com/pjgm/serverless/issues/1960)
* Minor dashboard doc improvements ([#12177](https://github.com/pjgm/serverless/issues/12177)) ([f1fa19c](https://github.com/pjgm/serverless/commit/f1fa19c7e02a49edaf813aac60e8622486c4b9cc))
* move markdown npm packages to dev deps, not prod deps ([753f640](https://github.com/pjgm/serverless/commit/753f640970b137aee14cd398a22cda81f61853db))
* Packaged files permissions handling ([cae2885](https://github.com/pjgm/serverless/commit/cae28851df435fd9eb0d651fde520862125d5deb))
* **Packaging:**  Do not include local plugins in a bundle ([#10259](https://github.com/pjgm/serverless/issues/10259)) ([62d8da2](https://github.com/pjgm/serverless/commit/62d8da209e28547e48763d15328852ad8e868cf8))
* **Packaging:** Add exec bit for packaged files on Windows ([#8615](https://github.com/pjgm/serverless/issues/8615)) ([c864fbd](https://github.com/pjgm/serverless/commit/c864fbd4826de27d2796e394b0a100c8d3add33e))
* **Packaging:** Allow to disable creation of default bucket policy ([919b95f](https://github.com/pjgm/serverless/commit/919b95f4911b29d5e05fc3adaa097ad7a22b4c18)), closes [#6923](https://github.com/pjgm/serverless/issues/6923)
* **Packaging:** Consider absolute artifact paths ([#8325](https://github.com/pjgm/serverless/issues/8325)) ([#8315](https://github.com/pjgm/serverless/issues/8315)) ([bcbbd47](https://github.com/pjgm/serverless/commit/bcbbd47fa09b7d99d7f8da3f11150215d1203bba))
* **Packaging:** Do not exclude layer paths when packaging a layer ([#8602](https://github.com/pjgm/serverless/issues/8602)) ([86b366a](https://github.com/pjgm/serverless/commit/86b366a5d3b6b0bd00b73c71d0c1a0661ff27ce2))
* **Packaging:** Do not report hashing deprecations for container lambdas ([68c2a08](https://github.com/pjgm/serverless/commit/68c2a084f91b58832bd5417efaaa3fd6a6178d53))
* **Packaging:** Ensure that .env files are excluded from package ([8791cda](https://github.com/pjgm/serverless/commit/8791cdacb75c84a2e08c5639abf769e915968288)), closes [#8566](https://github.com/pjgm/serverless/issues/8566)
* **Packaging:** Ensure to apply dev dependency exclusion ([7d16947](https://github.com/pjgm/serverless/commit/7d16947273da079f4e844b4a62c98863206e848e))
* **packaging:** Ensure to include "aws-sdk" dependency if installed ([#8145](https://github.com/pjgm/serverless/issues/8145)) ([2561ae8](https://github.com/pjgm/serverless/commit/2561ae800e04dd197302d5692cf6eab72185cc11))
* **Packaging:** Ensure to properly exclude when NODE_ENV set ([6e3e21c](https://github.com/pjgm/serverless/commit/6e3e21cafaa053a0f30239513eac5c7a725b7694))
* **Packaging:** Ensure to show deprecation in all cases ([cc71fc9](https://github.com/pjgm/serverless/commit/cc71fc99ffe2e1f2fcc764b29dafa197c665cef1))
* **Packaging:** Exclude .env files only when useDotenv is set ([537fcac](https://github.com/pjgm/serverless/commit/537fcac7597f0c6efbae7a5fc984270a78a2a53a))
* **Packaging:** Expose meaningfully file access errors ([#8582](https://github.com/pjgm/serverless/issues/8582)) ([13c7b7b](https://github.com/pjgm/serverless/commit/13c7b7bc97aab4d70e178fdb25af1b2c3b85ac5b))
* **Packaging:** Fix `package.artifact` validation for S3 urls ([ab3c543](https://github.com/pjgm/serverless/commit/ab3c543089b0fde4107fc0e579c19f85e0a4ee79))
* **Packaging:** Fix artifact generation with temp path on other device ([70fb8b9](https://github.com/pjgm/serverless/commit/70fb8b986133789b38fad93c0abab01eaf9dc0c7)), closes [#9616](https://github.com/pjgm/serverless/issues/9616)
* **Packaging:** Fix compatibility with npm v7.0 ([#8505](https://github.com/pjgm/serverless/issues/8505)) ([fdd962b](https://github.com/pjgm/serverless/commit/fdd962baa53a7471d33ad041e927c705051b343a))
* **Packaging:** Fix merging `DependsOn` from user resources ([#12009](https://github.com/pjgm/serverless/issues/12009)) ([4582913](https://github.com/pjgm/serverless/commit/4582913214e1c9d6f4324ff6a507dd09a2fd4e1b))
* **Packaging:** Fix resolution of files with '.' In their names ([#8130](https://github.com/pjgm/serverless/issues/8130)) ([c620af3](https://github.com/pjgm/serverless/commit/c620af3cd6eb930e39a02aa4537f748854d0f12a))
* **Packaging:** Fix support of the artifact S3 uri with region ([#9411](https://github.com/pjgm/serverless/issues/9411)) ([40e56fc](https://github.com/pjgm/serverless/commit/40e56fc0e9f71f06068d7d4c30178db8b2260357))
* **Packaging:** Proper exclusion of dependencies across platforms ([847aa9c](https://github.com/pjgm/serverless/commit/847aa9ca7f885f126c4a0a0279db30c05a8c9a6f))
* **Packaging:** Properly exclude devDependencies on Windows ([#8803](https://github.com/pjgm/serverless/issues/8803)) ([708f6a7](https://github.com/pjgm/serverless/commit/708f6a7e267e6c0c66da8bd97fdaf735909077d4))
* **Packaging:** Recognize `layers[].package.patterns` ([9793c50](https://github.com/pjgm/serverless/commit/9793c506ec364a4298a97e274c27c6f934749c74))
* **Packaging:** Revert exclusion of local plugins from a bundle ([1608e74](https://github.com/pjgm/serverless/commit/1608e743deaecd925bc445a3a4800f40801553a5))
* **Packaging:** Validate `package.artifact` paths ([21c0fed](https://github.com/pjgm/serverless/commit/21c0fedc507651bb98687acc4145ed667d853589))
* **Plugins:** Ensure to keep `options` as passed to plugins up to date ([e3af1f3](https://github.com/pjgm/serverless/commit/e3af1f3a94253a7900de104afaa1c49aa436965c))
* **Plugins:** Fix resolution of config when installing plugin ([b5dbdaf](https://github.com/pjgm/serverless/commit/b5dbdafe5b4b03608ebb10d024fb6587e1ea7a40)), closes [#7130](https://github.com/pjgm/serverless/issues/7130)
* **Plugins:** Improve error message when a plugin is missing ([#9798](https://github.com/pjgm/serverless/issues/9798)) ([5c9df56](https://github.com/pjgm/serverless/commit/5c9df56f1bc89af1fd929519f3cf8dac967e514d))
* **Plugins:** Prevent variables resolution with "plugin .." command ([8ac2706](https://github.com/pjgm/serverless/commit/8ac27061999a0005d5aab342319cccfe6bbc9d49))
* prettify ([a5480ce](https://github.com/pjgm/serverless/commit/a5480ce483b28eb1dbbd74ae0bf810be76bfbfb9))
* Prevent uncaught exception in case of `open` util issue ([f29d169](https://github.com/pjgm/serverless/commit/f29d1697dd89a418ca4aacac23b64b928e68f643))
* Properly handle error if Java bridge is not present ([11fb141](https://github.com/pjgm/serverless/commit/11fb14115ea47d53a61fa666a94e60d585fb3a4d))
* Properly move directories across filesystems ([d06b64d](https://github.com/pjgm/serverless/commit/d06b64d4b9e8203945ad946495ff300d9852b37c))
* Properly resolve local version ([053bcc7](https://github.com/pjgm/serverless/commit/053bcc7624f5d1ace56c708be5125fc665973a1d))
* Recognize `Fn::Select` in `environment` config schema ([#11114](https://github.com/pjgm/serverless/issues/11114)) ([ed111e0](https://github.com/pjgm/serverless/commit/ed111e021b286eb4a68f9b2fce7fb641e03340bd))
* Recognize accessible configuration parts on validation errors ([b7a6349](https://github.com/pjgm/serverless/commit/b7a634974dc2ee138d85ec58609bf2559c5de9f6))
* recognize ap-south-2 as a valid AWS region ([#12129](https://github.com/pjgm/serverless/issues/12129)) ([b09d0d6](https://github.com/pjgm/serverless/commit/b09d0d62677c09c4905b65bcaf6ba61aa8d8204c))
* Recognize AWS Web Identify Credentials ([#7442](https://github.com/pjgm/serverless/issues/7442)) ([001f56c](https://github.com/pjgm/serverless/commit/001f56cf5a4c8b4ffeb6f9e9fcc27e73d2f10789))
* Recognize falsy values as CLI options defaults ([#7071](https://github.com/pjgm/serverless/issues/7071)) ([7e0e903](https://github.com/pjgm/serverless/commit/7e0e903c798cc6c5370a74048202cd0480e2be3d))
* Recognize final DELETE_COMPLETE event with verbose flag ([#7979](https://github.com/pjgm/serverless/issues/7979)) ([e980625](https://github.com/pjgm/serverless/commit/e980625f586f55da4559b362a9dcd7275e9001bb))
* Reject non normative configuration structure ([8bd4314](https://github.com/pjgm/serverless/commit/8bd431473265d6bc2b536c0f5070f99e1639382d))
* remove `$context.status` from websocket access log format ([d1537f7](https://github.com/pjgm/serverless/commit/d1537f7b4ba9ce0f54819431403ff8e499b9fa08))
* remove credential validation check from sls package command ([381c147](https://github.com/pjgm/serverless/commit/381c147f15c52af4ef72a4807c1ce546cab1b67a))
* Remove hard-coded AWS partitions ([#7175](https://github.com/pjgm/serverless/issues/7175)) ([3236adb](https://github.com/pjgm/serverless/commit/3236adb040f186cd606e5656cf85a05bd183e822))
* Remove outdated information and add new features ([#11892](https://github.com/pjgm/serverless/issues/11892)) ([938e5dd](https://github.com/pjgm/serverless/commit/938e5ddc92597e83cc10d106e1d1f1479a729111))
* remove unneeded validation check ([e8f6026](https://github.com/pjgm/serverless/commit/e8f6026566c01f579c0f1ef57dcdc2fadc769396))
* Report more meaningful strict schema mode error ([e98d699](https://github.com/pjgm/serverless/commit/e98d699e7800780e7d56340d778116e1b3b5b005))
* Revert  `vpc` configuration on custom resources  ([#12001](https://github.com/pjgm/serverless/issues/12001)) ([d0e3056](https://github.com/pjgm/serverless/commit/d0e3056b77ba295adb87ceeca9a49a26b315f083)), closes [#11985](https://github.com/pjgm/serverless/issues/11985)
* Revert fix for handing of removal of custom APIGW policy ([#7048](https://github.com/pjgm/serverless/issues/7048)) ([578c1bc](https://github.com/pjgm/serverless/commit/578c1bc3ba7e91598dc3ab359f0dc0a4676c1f15))
* Revert from `frameworkVersion` requirement ([6dd0596](https://github.com/pjgm/serverless/commit/6dd0596286666b242b921847ffdeb6628baf3b26))
* Separate AWS region and credentials resolution concern ([c7fea34](https://github.com/pjgm/serverless/commit/c7fea34e859fd9b4cd19118a518ae68d140728e5))
* Service state path resolution ([#7388](https://github.com/pjgm/serverless/issues/7388)) ([5017f03](https://github.com/pjgm/serverless/commit/5017f038d6a8f35fc25ec7a239358a30ca15b745))
* Set `versionFunctions` to true only in AWS provider case ([9897120](https://github.com/pjgm/serverless/commit/9897120a8adae59205e5d84d1bdca442621f51b4))
* Slim down Azure Functions template ([14044ed](https://github.com/pjgm/serverless/commit/14044edaae1e89b11fdedc935a60474cd0166547))
* **Standalone:** Chalk is an object, not a method ([1565d03](https://github.com/pjgm/serverless/commit/1565d038313b7939d6c9d9fdf8bfb4f95fd7027e))
* **Standalone:** Ensure dashboard plugin policies are bundled ([4b5f531](https://github.com/pjgm/serverless/commit/4b5f531d9ec293f1f228d572cd265361530135f7))
* **Standalone:** Ensure dashboard wrapper is bundled ([994555d](https://github.com/pjgm/serverless/commit/994555d7d6eb7bf960adceed4a59a4f667a9d92d))
* **Standalone:** Ensure error in China upload don't break GitHub upload ([2b8afac](https://github.com/pjgm/serverless/commit/2b8afac5ecf879a6e979c5a4642ededeca4a5cf7))
* **Standalone:** Ensure local invocation wrappers are accessible ([527233d](https://github.com/pjgm/serverless/commit/527233d2637977544169e6799d9359c86425de18))
* **Standalone:** Ensure pkg bug workaround is applied on WIndows ([8bc6d54](https://github.com/pjgm/serverless/commit/8bc6d542f8b45aee74463ec732272dcf39c14132))
* **Standalone:** Ensure proper `npm` bundling ([cf482f0](https://github.com/pjgm/serverless/commit/cf482f01700ddd0946e71ad5e7d2ca0d06cc49a3))
* **Standalone:** Ensure proper resolution of runtime wrappers ([1833894](https://github.com/pjgm/serverless/commit/1833894856991e98e0d32701217453c413164cf3))
* **Standalone:** Ensure reliable access from China ([6fccede](https://github.com/pjgm/serverless/commit/6fccedea4ac5a3a546d36b19d2e0701defd9ed85))
* **Standalone:** Ensure to bundle local invocation non Node.js artifcats ([506ad86](https://github.com/pjgm/serverless/commit/506ad863da1ceb78d2d8a0573dbc03c0db56f098))
* **Standalone:** Ensure to use proper CLI params parser ([f426ed7](https://github.com/pjgm/serverless/commit/f426ed7077c67eac9785452b312ca1e179c201bf))
* **Standalone:** Fix internal npm installation handling ([5a583a9](https://github.com/pjgm/serverless/commit/5a583a97980117209a614bfd40630b1bb714b744))
* **Standalone:** Fix upgrade command ([f23e50b](https://github.com/pjgm/serverless/commit/f23e50b16e50559596fbd9561dfb4ced82973814))
* **Standalone:** Fix upgrade when temp dir is on other device ([1b8d463](https://github.com/pjgm/serverless/commit/1b8d463a08fb48cca0236874dd1cf68e477ba93d))
* **Standalone:** Recognize Windows as non auto updatable platform ([4fc29a5](https://github.com/pjgm/serverless/commit/4fc29a57c4b675b2751c1e17d47e45904653f658))
* **Standalone:** Support SLS_GEO_LOCATION env var ([474df11](https://github.com/pjgm/serverless/commit/474df11288a0431bb14947c4a08ae34edecb4164))
* **Standalone:** Upgrade npm version to one that supports Node.js v14 ([62d697c](https://github.com/pjgm/serverless/commit/62d697c8615e8103aa07401eef2ebae559cc4a17))
* **Standalone:** Workaournd `fs-extra` v8 bug ([548bd98](https://github.com/pjgm/serverless/commit/548bd986e4dafcae207ae80c3a8c3f956fbce037))
* **Standalone:** Workaround `pkg` [#420](https://github.com/pjgm/serverless/issues/420) bug ([c94a614](https://github.com/pjgm/serverless/commit/c94a6146762a2d50c9d746e70a699ffc9cffd9c8))
* Support `Condition` attribute in `resources.extensions` ([#8217](https://github.com/pjgm/serverless/issues/8217)) ([16bae33](https://github.com/pjgm/serverless/commit/16bae337448e23484dc10262d9a6be845eb1818a))
* Support differet AWS partitions ([8148cf2](https://github.com/pjgm/serverless/commit/8148cf2cacb50edc9f0ad9199d066b17847a0136))
* Support log retention at custom resource lambda log groups ([#8456](https://github.com/pjgm/serverless/issues/8456)) ([4ce9037](https://github.com/pjgm/serverless/commit/4ce9037f8c8416715204f431af65767b3c48e1c7))
* **Telemetry:** Correctly report `outcome` for interactive setup ([0c5b8dd](https://github.com/pjgm/serverless/commit/0c5b8dd831bcde80628c2ac548172ffaa9ce9ca6))
* **Telemetry:** Do not report when `commandSchema` not resolved ([2c2c77f](https://github.com/pjgm/serverless/commit/2c2c77f90518e73921b0f4dd02767b5ad4476db4))
* **Telemetry:** Do not send request when there are no events ([f430224](https://github.com/pjgm/serverless/commit/f4302249a9d9bfba46ca3fb6823cc8da27f20939))
* **Telemetry:** Do not share telemetry cache folder with old versions ([ae9442e](https://github.com/pjgm/serverless/commit/ae9442e53b04648ff5b9c436ef86765d2ad9d872))
* **Telemetry:** Ensure excluding `shouldSendTelemetry` from payload ([9c6423b](https://github.com/pjgm/serverless/commit/9c6423bc5c5d81b977d03d3412b4a2ab05bf4513))
* **Telemetry:** Ensure no doubled telemetry in edge cases ([fd5005e](https://github.com/pjgm/serverless/commit/fd5005e404debe103ca54974ca9aee431554ceb8))
* **Telemetry:** Ensure proper options for generate payload fallback ([b7a113d](https://github.com/pjgm/serverless/commit/b7a113d48d634f89a91a31cd05b8d2e57f540c77))
* **Telemetry:** Ensure telemetry only matches js stacktrace paths ([7361e04](https://github.com/pjgm/serverless/commit/7361e049608d40e4199c797abbad552ea831f5a5))
* **Telemetry:** Ensure that container commands do not trigger telemetry ([85b9e53](https://github.com/pjgm/serverless/commit/85b9e5319df48904664f966e988cc725116ce865))
* **Telemetry:** Ensure to gently handle older globals ([1b90dfb](https://github.com/pjgm/serverless/commit/1b90dfb0659dab3852ace330fd7c497321b80710))
* **Telemetry:** Ensure to not leak `false` as empty value ([167a77e](https://github.com/pjgm/serverless/commit/167a77ecaecc4da92f629d1aa075eb1a62831916))
* **Telemetry:** Ensure to not show backed notification on error ([dce0ff1](https://github.com/pjgm/serverless/commit/dce0ff1a892959b12414f1bff3915fe50b900ba2))
* **Telemetry:** Ensure to pass all steps with configured questions ([b5d3167](https://github.com/pjgm/serverless/commit/b5d3167e9fdd5f08af1389b975322f2146b22507))
* **Telemetry:** Ensure to pass proper config for local fallback ([9b2a111](https://github.com/pjgm/serverless/commit/9b2a1114850914a4ac96b19c7fcb0bf031822ea4))
* **Telemetry:** Fix Console org reporting ([c0aabb4](https://github.com/pjgm/serverless/commit/c0aabb484531c5227f42791cdb9e644c402a5c8d))
* **Telemetry:** For local fallback ensure to report locally used version ([096ed96](https://github.com/pjgm/serverless/commit/096ed9652bff399965c81c9aedb93b42c2b8caf5))
* **Telemetry:** Handle error locations not enclosed in parens ([3ab0628](https://github.com/pjgm/serverless/commit/3ab06282fdc9455f364fd73bd14761bae0c8d289))
* **Telemetry:** If global & local report outcome, report with global ([eeddf9f](https://github.com/pjgm/serverless/commit/eeddf9f518612f6f7ef805eb3ed9b13fb3036114))
* **Telemetry:** Let old versions report telemetry old way ([4d077d1](https://github.com/pjgm/serverless/commit/4d077d1653fcc41e362587e5d13dfa8dd43d3bc3))
* **Telemetry:** Properly handle not in service dir in credentials ([b21c1e4](https://github.com/pjgm/serverless/commit/b21c1e415b67cdc8f1fb0ab14152eaf3c6550894))
* **Telemetry:** Properly resolve location when for only relative paths ([#9418](https://github.com/pjgm/serverless/issues/9418)) ([3ccf6a3](https://github.com/pjgm/serverless/commit/3ccf6a3af3de093fabfa33a966b7a0a922712845))
* **Telemetry:** Split stack lines properly on all OS-es ([bdbf154](https://github.com/pjgm/serverless/commit/bdbf154c97abde6ad2ff807dbea3ad1110ee5fec))
* **Template:** Ensure java wrappers are moved to runtimeWrappers ([#7999](https://github.com/pjgm/serverless/issues/7999)) ([03531d8](https://github.com/pjgm/serverless/commit/03531d8bc6bce44a445e34e5046eaef6d95d0aa1))
* **Templates:** Add `esbuild` to `gitignore` in  `aws-nodejs-typescript` ([865f21f](https://github.com/pjgm/serverless/commit/865f21f970340b45c6fb341d01647721f0fa5682))
* **Templates:** Add aws-lambda-java-events support to Java ([#7986](https://github.com/pjgm/serverless/issues/7986)) ([ab99b65](https://github.com/pjgm/serverless/commit/ab99b657a3c613b3e9ba072e084d159f5ac6c073))
* **Templates:** Add missing property in ruby template ([#8195](https://github.com/pjgm/serverless/issues/8195)) ([8f070d5](https://github.com/pjgm/serverless/commit/8f070d58c46e7c1d5cbe34b31a34387eaccea505))
* **Templates:** Adjust `runtime` for `openwhisk-python` template ([6a020d1](https://github.com/pjgm/serverless/commit/6a020d121ff2dacd6ad62a824964944ae391a662))
* **Templates:** Allow usage of `google-nodejs-typescript` template ([accf5bd](https://github.com/pjgm/serverless/commit/accf5bd082400f654eba5e7d322bcb205c9ae709))
* **Templates:** Compilation target ES2019 in aws-nodejs-typescript ([4469388](https://github.com/pjgm/serverless/commit/4469388669d50193dedc6e2695789d24fe30a238))
* **Templates:** Ensure `esbuild` dependency in `aws-nodejs-typescript` ([452e4d8](https://github.com/pjgm/serverless/commit/452e4d8279802ab2ce1ca300ab2c75ec8588a9e8))
* **Templates:** Ensure ES7+ support in aws-nodejs-ecma-script ([#8064](https://github.com/pjgm/serverless/issues/8064)) ([e7efca4](https://github.com/pjgm/serverless/commit/e7efca4b421f19b65d88b4bfe973ce5a9ab14d3c))
* **Templates:** Ensure missing Kotlin dependencies ([#8010](https://github.com/pjgm/serverless/issues/8010)) ([15fae3b](https://github.com/pjgm/serverless/commit/15fae3bfb286dfdf72b14f7443a5683d0e4db7de))
* **Templates:** Ensure service is renamed in package-lock.json ([#8409](https://github.com/pjgm/serverless/issues/8409)) ([78f159b](https://github.com/pjgm/serverless/commit/78f159b4326f7eb092895bbd11813e470c146dc4))
* **Templates:** Ensure that `.gitignore` is packaged for templates ([e79f906](https://github.com/pjgm/serverless/commit/e79f906b9fd0940e8eb1367cf6ce1ed1095f0c46))
* **Templates:** Ensure that `gradle-wrapper.jar` is not excluded ([deed534](https://github.com/pjgm/serverless/commit/deed53449fb4c302a3fe04f0f2bef19b27d9ef81))
* **Templates:** Fix Azure Functions Python template ([#7452](https://github.com/pjgm/serverless/issues/7452)) ([345b9e6](https://github.com/pjgm/serverless/commit/345b9e654b246ef3186a0f3fdd56901a6316af2b))
* **Templates:** Fix cleanup in `aws-go-mod` template ([#8507](https://github.com/pjgm/serverless/issues/8507)) ([2791c71](https://github.com/pjgm/serverless/commit/2791c7142f795ddab7da1b8cbfa7588f9ae4896d))
* **Templates:** Fix handler path resolution in aws-nodejs-typescript ([b753641](https://github.com/pjgm/serverless/commit/b753641b072485d4764e891b5e90242776bec724))
* **Templates:** Fix incomplete migration into dayjs from moment ([#7961](https://github.com/pjgm/serverless/issues/7961)) ([d5ce246](https://github.com/pjgm/serverless/commit/d5ce24681e3a75eccce290a52e045664878b9387))
* **Templates:** Fix java invoke-bridge build error handling ([#7968](https://github.com/pjgm/serverless/issues/7968)) ([87e7480](https://github.com/pjgm/serverless/commit/87e7480663fe7d3513687e9127fdca8b143cf1d6))
* **Templates:** Fix PackageReference in aws-fsharp template ([#7914](https://github.com/pjgm/serverless/issues/7914)) ([7848b6d](https://github.com/pjgm/serverless/commit/7848b6d033ec4a7c64186e5f2306351128100be4))
* **Templates:** Fix runtime for `azure-nodejs-typescript` ([#9106](https://github.com/pjgm/serverless/issues/9106)) ([3597f45](https://github.com/pjgm/serverless/commit/3597f4539dce1d7185879e7e00e67c64c022de02)), closes [#6998](https://github.com/pjgm/serverless/issues/6998)
* **Templates:** Fix service rename ([8c0d892](https://github.com/pjgm/serverless/commit/8c0d89255e5f3bf2835966fde2f441b828607106))
* **Templates:** Fix statement in `.npmignore` to handle `.gitignore` ([d0c0879](https://github.com/pjgm/serverless/commit/d0c0879032aedca567fef807b7143b7325f43b4d))
* **Templates:** Fix support for `~/..` paths ([#7381](https://github.com/pjgm/serverless/issues/7381)) ([962506b](https://github.com/pjgm/serverless/commit/962506b4356545870e18d570756240e602b5f541))
* **Templates:** Fix SystemTextJson initialization in aws-sharp ([#8092](https://github.com/pjgm/serverless/issues/8092)) ([0490e8b](https://github.com/pjgm/serverless/commit/0490e8be2024cd705bbece379897381b88f87148))
* **Templates:** Fix tooling options ([#8501](https://github.com/pjgm/serverless/issues/8501)) ([cc103f1](https://github.com/pjgm/serverless/commit/cc103f147eddcb29e38937326cc551473925e535))
* **Templates:** Fix types handling in `aws-nodejs-typescript` ([#8929](https://github.com/pjgm/serverless/issues/8929)) ([5302b91](https://github.com/pjgm/serverless/commit/5302b9176097faee4c73d585b63e6bf772b64e43))
* **Templates:** Rename vscode to .vscode folder ([#8168](https://github.com/pjgm/serverless/issues/8168)) ([f308382](https://github.com/pjgm/serverless/commit/f3083828b448d08c98969c2f956248bbce75de57))
* **Templates:** Set ContextClassLoader for groovy and clojure ([#7955](https://github.com/pjgm/serverless/issues/7955)) ([25263fd](https://github.com/pjgm/serverless/commit/25263fd473584e51c81bb3c5cedd4b9005dfd984))
* **Templates:** Update `aws-lambda-java-log4j2` ([#10383](https://github.com/pjgm/serverless/issues/10383)) ([786f5e4](https://github.com/pjgm/serverless/commit/786f5e45d54ae9925649367b0a0e8660eda542e6))
* **Templates:** Update dependencies of `aws-nodejs-typescript` to v3  ([88ac3d0](https://github.com/pjgm/serverless/commit/88ac3d0586b3ed98ee0c1b7c618cbca095ee85d3))
* **Templates:** Upgrade `log4j` in `aws-kotlin-jvm-gradle` ([#10382](https://github.com/pjgm/serverless/issues/10382)) ([7bf8f1b](https://github.com/pjgm/serverless/commit/7bf8f1b723cc4f6624df7be3d27f246b3a826140))
* **Templates:** Upgrade `log4j` to `2.17.1` ([#10430](https://github.com/pjgm/serverless/issues/10430)) ([2c3ab1d](https://github.com/pjgm/serverless/commit/2c3ab1db9aa7c22c315957d1e474568e62e07e37))
* **Templates:** Upgrade Java 3rd party libraries used for invokeLocal ([851b856](https://github.com/pjgm/serverless/commit/851b85629dbff510ceb1865fd9a1a48a75940ebd)), closes [#7930](https://github.com/pjgm/serverless/issues/7930)
* **Templates:** Use `amd64` arch for `aws-go` template ([#9646](https://github.com/pjgm/serverless/issues/9646)) ([cb9f7e2](https://github.com/pjgm/serverless/commit/cb9f7e20eedc1db7bb31671c97449e269e992ded))
* Throw operational error as operational ([f965e44](https://github.com/pjgm/serverless/commit/f965e446946048691889a7f3723c19ac747b8fe2))
* Update pkg config to include axios cjs ([#12261](https://github.com/pjgm/serverless/issues/12261)) ([b21afaf](https://github.com/pjgm/serverless/commit/b21afaf9cf97224d36234b02e3e872bc115f7dc9))
* use normalized maps in zipService.js ([6a91107](https://github.com/pjgm/serverless/commit/6a91107e3db1c66e02196a7dd7a869a87fb3a9a9))
* **Variables:**  Ensure visibility of top level properties resolution ([004c6e2](https://github.com/pjgm/serverless/commit/004c6e26beec98fbfb757aab05f18a623a03cf76))
* **Variables:** Clear escape slashes ([c63244c](https://github.com/pjgm/serverless/commit/c63244ce967c2c424fea50aaab9e19d355003913))
* **Variables:** Ensure necessary resolution interface for plugins ([841e847](https://github.com/pjgm/serverless/commit/841e847c20de989287e36a86c523763dc2b74e8b))
* **Variables:** Ensure no collisions with AWS CloudFormation variables ([2fdeb51](https://github.com/pjgm/serverless/commit/2fdeb51174d8fa55cc2704e8e84297471eadec39)), closes [#8279](https://github.com/pjgm/serverless/issues/8279)
* **Variables:** Ensure no same object instances are shared across config ([4893f7d](https://github.com/pjgm/serverless/commit/4893f7d0c2168d3aa39b04ac040cd1797ed31431)), closes [#7098](https://github.com/pjgm/serverless/issues/7098)
* **Variables:** Ensure proper error handling for resolved value parsing ([df62739](https://github.com/pjgm/serverless/commit/df627394b36c16553a73328850ff722f1063254c))
* **Variables:** Ensure proper resolution in case of errors ([ee66585](https://github.com/pjgm/serverless/commit/ee66585fdcfc32d135ed0cdc6bad8d440c7e9e38))
* **Variables:** Ensure report user error as user error ([a8f4aeb](https://github.com/pjgm/serverless/commit/a8f4aebe5d482a491d86d3427b259db00674cc72))
* **Variables:** Ensure resolution of unrecognized CLI options ([b5668d5](https://github.com/pjgm/serverless/commit/b5668d5be04902437c82b2ccb049f93f82a87ec3))
* **Variables:** Ensure to apply a new resolver in a local version ([14a5275](https://github.com/pjgm/serverless/commit/14a5275c0d6a127e211935b8b8f57a949e1ffad6))
* **Variables:** Ensure to apply intialization patch unconditionally ([d6c7d97](https://github.com/pjgm/serverless/commit/d6c7d97dc6bb6229dd80e443a09f5a741bf1380e))
* **Variables:** Ensure to not share property cache across resolutions ([68f326e](https://github.com/pjgm/serverless/commit/68f326e79f92f8a94ba73352cba40c85e08c10cf))
* **Variables:** Ensure to not share source cache across resolutions ([5ad1c19](https://github.com/pjgm/serverless/commit/5ad1c19cc9a5601184883a916a29172eeb9c3789))
* **Variables:** Ensure to report only unrecognized sources ([98701f3](https://github.com/pjgm/serverless/commit/98701f367907aa4c0ed61de7c3aeb4a7b7eac174))
* **Variables:** Ensure to resolve variables in resolved strings ([480b612](https://github.com/pjgm/serverless/commit/480b61270cfef8f1a4a5aa36cd235db2362c9cfd))
* **Variables:** Ensure to retrieve status code correctly ([bc5bbbe](https://github.com/pjgm/serverless/commit/bc5bbbed3c050eb69262b3f9b6fbd53c563c9fb2)), closes [#7237](https://github.com/pjgm/serverless/issues/7237)
* **Variables:** Ensure to support middle JS function resolved properties ([32ba7c8](https://github.com/pjgm/serverless/commit/32ba7c8b436ab49641fb89028e5b2e53226df3b5))
* **Variables:** Ensure valid region value type in SSM resolution ([83cac53](https://github.com/pjgm/serverless/commit/83cac533a387a216dd6c151307a0dc69f36eef9e))
* **Variables:** Ensure vars are passed in address followed by source ([fb9ce24](https://github.com/pjgm/serverless/commit/fb9ce246b37219b1e3077ea53777f753d0a9205d))
* **Variables:** Error on property access attempt on primitive result ([131516a](https://github.com/pjgm/serverless/commit/131516a6d094ee9b75fbe9b1d975b96d9c358a82))
* **Variables:** Expose source resolution errors as non-user errors ([5e2406b](https://github.com/pjgm/serverless/commit/5e2406bea78b353fea10a45d657ae2a7789531bd))
* **Variables:** Fix file access error message generation ([6dd3996](https://github.com/pjgm/serverless/commit/6dd39968f2c49f3d98139994e320846b082b6005))
* **Variables:** Fix handling of circular object references ([fd451ca](https://github.com/pjgm/serverless/commit/fd451caf901f3bf69a872437643fa38d5eda8924))
* **Variables:** Fix handling of parallel resolution of same variable ([1f9a07f](https://github.com/pjgm/serverless/commit/1f9a07f989fc0b56885edf8a271a0bd63cf8911f))
* **Variables:** Fix nested sources resolution ([99fd907](https://github.com/pjgm/serverless/commit/99fd907abbe3d83f8db7bf3a1924da770bc18be8))
* **Variables:** Fix new sources resolution error message at old resolver ([8dece7f](https://github.com/pjgm/serverless/commit/8dece7f6c6544f91366a2c8f70389be8b4b659c8))
* **Variables:** Fix reporting of unresolved sources ([77e21f9](https://github.com/pjgm/serverless/commit/77e21f904568db00f6e1491dd0dcdfe605fa592d))
* **Variables:** Fix reporting of variable resolution errors ([f6b7cfa](https://github.com/pjgm/serverless/commit/f6b7cfaaaff81b84011f0f6168a651979089e1c9))
* **Variables:** Fix resolution of "false" CLI params ([6c6ada9](https://github.com/pjgm/serverless/commit/6c6ada93e47e994dc5775a65542bedf69ec6d412))
* **Variables:** Fix support for `${self:}` ([ac34110](https://github.com/pjgm/serverless/commit/ac3411085246c112db7aca7c5ea6354a0ab7bd08))
* **Variables:** Fix too eager nested resolution tracking ([#10554](https://github.com/pjgm/serverless/issues/10554)) ([8db03c9](https://github.com/pjgm/serverless/commit/8db03c90ffba68ebda800d2a009452cd09f7bf7f))
* **Variables:** Fix unresolved sources resolver ([53a7872](https://github.com/pjgm/serverless/commit/53a7872f78f51938b409925e052d34f2dc85abbd))
* **Variables:** Fix unterminated variable resolution for some cases ([cc5bfd5](https://github.com/pjgm/serverless/commit/cc5bfd53ae2459e4d7ac1ec6314c030d39997958))
* **Variables:** Fix variables setup for external plugins usage ([25dd575](https://github.com/pjgm/serverless/commit/25dd575a4d597c09078ac8a2c709d834ae85221e))
* **Variables:** Fix when properties are null ([#8165](https://github.com/pjgm/serverless/issues/8165)) ([eb11e6d](https://github.com/pjgm/serverless/commit/eb11e6d92b99687529fed708d3f7f5a28ef1c027))
* **Variables:** Improve JS file resolution error handling ([9ecc108](https://github.com/pjgm/serverless/commit/9ecc1087653edfde9da400f496030dea0d6203ce))
* **Variables:** Improve properties resolution validation ([727d7f4](https://github.com/pjgm/serverless/commit/727d7f4f089051223db88ceb85a62adabf07dc9e))
* **Variables:** Improve resolution of AWS auth related properties ([e66c865](https://github.com/pjgm/serverless/commit/e66c865a26c237273473429eb595295c2d7992af))
* **Variables:** In `ssm` source auto parse only object JSON notation ([8c741d1](https://github.com/pjgm/serverless/commit/8c741d1d97f021995f37a61d7340ddfa749cdab9))
* **Variables:** Meaningfully report misuse of dashboard sources ([cc09c62](https://github.com/pjgm/serverless/commit/cc09c62301f15f89febc50120a7a398640935470))
* **Variables:** Properly resolve vars if `prototype` in path ([496d357](https://github.com/pjgm/serverless/commit/496d3574c6f8df389331ec92fd330efb652f65e6))
* **Variables:** Provide opt-out from forced decryption at`ssm` source ([503c031](https://github.com/pjgm/serverless/commit/503c0319b7e9acc2b674d5d61874dfa3fcfc857e)), closes [#10315](https://github.com/pjgm/serverless/issues/10315)
* **Variables:** Recognize `tenant` setting as it's recognized by plugin ([aa45876](https://github.com/pjgm/serverless/commit/aa4587604476314485a8094bdae04e0148b9e53c))
* **Variables:** Recognize hyphens in types ([21ac1be](https://github.com/pjgm/serverless/commit/21ac1beb225946713665e9d8ad22d6e5c63819a9))
* **Variables:** Relax pattern to allow non-ascii defaults ([#7431](https://github.com/pjgm/serverless/issues/7431)) ([7310782](https://github.com/pjgm/serverless/commit/73107822945a878abbdebe2309e8e9d87cc2858a))
* **Variables:** Report with `null` not existing `file` sources ([3ab81e5](https://github.com/pjgm/serverless/commit/3ab81e5be94c69b90dc8487e321fb4cf7efc2c11))
* **Variables:** Report with meaningful error unresolved "plugins" ([5565047](https://github.com/pjgm/serverless/commit/55650473828eb6df9563687ccf3996b6713da191))
* **Variables:** Resolve plain text for unrecognized extensions ([d2e6a8a](https://github.com/pjgm/serverless/commit/d2e6a8adef5632ddf63581cfacc7cb77bbc634af))
* **Variables:** Resolve variables in resolved address & params values ([63d54e1](https://github.com/pjgm/serverless/commit/63d54e1537e10ae63c171892edd886f6b81e83f6))
* **Variables:** Retry JS function resolvers on unresolved dependencies ([68de8bd](https://github.com/pjgm/serverless/commit/68de8bdeed0545e6868c72806340e96f90f808cf))
* **Variables:** Skip unrecognized sources check with partial resolution ([93b89fc](https://github.com/pjgm/serverless/commit/93b89fcb51759d0fe938a40e7de76b6abd313efd))
* **Variables:** Strip unrecognized legacy instructions ([f61859f](https://github.com/pjgm/serverless/commit/f61859fd25908b13b6d9638c550e88ef4a08392e))
* **Variables:** Support empty string environment variables ([#11629](https://github.com/pjgm/serverless/issues/11629)) ([022db9c](https://github.com/pjgm/serverless/commit/022db9c8a309fcd7cd58bf7d6fc066acd411a679))
* **Variables:** Support resolving "raw" JSON string form of SSM params ([4eba512](https://github.com/pjgm/serverless/commit/4eba512c1529a0d1d6c60e3f9de3bf98d6c23002))
* **Variables:** Unconditionally deprecate old vars engine extensions ([b7f4e08](https://github.com/pjgm/serverless/commit/b7f4e08661cd149a29ae7107241a16928dc606eb))
* **Variables:** Unify error messaging for function resolvers ([bb3b766](https://github.com/pjgm/serverless/commit/bb3b766946311848c707abc0fc7e749393f4527c))
* **Variables:** Unify handling of not existing addresses ([b21dc44](https://github.com/pjgm/serverless/commit/b21dc44048cc1a96e2f772b9c412474b3a687067))
* Websocket route names normalization ([#7294](https://github.com/pjgm/serverless/issues/7294)) ([33291c8](https://github.com/pjgm/serverless/commit/33291c8d08c8edd82e807b8fbe3f1796bcfdb4ac))
* When packaging do not crash on deps with no package.json ([#7368](https://github.com/pjgm/serverless/issues/7368)) ([8518000](https://github.com/pjgm/serverless/commit/8518000d4fbf3a6cf0a6e2f81bd6421e017a1b5f))
* Workaround config schema error on project initialization ([738c52f](https://github.com/pjgm/serverless/commit/738c52f6e544bbf9ae130eac99e676bd22fa29e2)), closes [#8257](https://github.com/pjgm/serverless/issues/8257)
* **zip:** Switch to archivejs to reduce high memory footprint ([7834ca0](https://github.com/pjgm/serverless/commit/7834ca0217af28e711d80732274070dc3bb5b943))


### Performance Improvements

* **AWS Deploy:** Do not re-upload unchanged lambda layers ([#7680](https://github.com/pjgm/serverless/issues/7680)) ([2b9f63e](https://github.com/pjgm/serverless/commit/2b9f63e3329d6e28c0a87d58658b0afde557053e))
* **aws-nodejs-typescript:** reuse http connections ([cf81bca](https://github.com/pjgm/serverless/commit/cf81bcaca3b91cbf579b2a3b7c6b3f3e0fb7375a))
* **CLI:** Integrate CLI triage into this package ([415bdef](https://github.com/pjgm/serverless/commit/415bdefca092e60cacd867006bacddfda231ed94))
* **packaging:** Exclude "aws-sdk" dependency ([#8103](https://github.com/pjgm/serverless/issues/8103)) ([f45da3c](https://github.com/pjgm/serverless/commit/f45da3c7b168d34e7d3c520068dc24364753a74a))
* **Packaging:** Remove aws-sdk installation step ([#8110](https://github.com/pjgm/serverless/issues/8110)) ([258c692](https://github.com/pjgm/serverless/commit/258c692c47c911d77efe880f41134801bdea314a))


* Merge pull request #5571 from exoego/preserver-space-in-fallback ([80f9a25](https://github.com/pjgm/serverless/commit/80f9a2599f17757daf56ffd42ebb0a1224e29e8b)), closes [#5571](https://github.com/pjgm/serverless/issues/5571)


### Maintenance Improvements

*  Abort unnecessary work ([fb86af5](https://github.com/pjgm/serverless/commit/fb86af58804a3beddf27b4280e7f0a673812b8cc))
* Abstract resolution of deployment role  ([#8751](https://github.com/pjgm/serverless/issues/8751)) ([4afdb83](https://github.com/pjgm/serverless/commit/4afdb8314b5c4718e73de733e3c4b30ae62382ba))
* Adapt to rename in `@serverless/dashboard-plugin` ([73b1886](https://github.com/pjgm/serverless/commit/73b18860408ca95b504b0c962dcb6feea14f9acb))
* Add `code` to `ServerlessError` in `./Serverless.js` ([28c5af4](https://github.com/pjgm/serverless/commit/28c5af47f4ae4cf0957390712f72353bf7af3c68))
* Add `code` to `ServerlessError` in `lib/aws` ([8748a78](https://github.com/pjgm/serverless/commit/8748a783ae4e0ca25507c45e1a5619fc7c1520c8))
* Add `code` to `ServerlessError` in `lib/classes` ([82040b4](https://github.com/pjgm/serverless/commit/82040b427e4c292bf9287a668fa46856ba5204e2))
* Add `code` to `ServerlessError` in `lib/configuration` ([395bdc8](https://github.com/pjgm/serverless/commit/395bdc8b23b0fd5a94fee3584df89f30232e6d74))
* Add `code` to `ServerlessError` in `lib/plugins/aws` ([fbf0ed3](https://github.com/pjgm/serverless/commit/fbf0ed30e933755ae86c3d31050cdb0d3b952b82))
* Add `code` to `ServerlessError` in `lib/plugins` ([81f0858](https://github.com/pjgm/serverless/commit/81f0858cc93dfe7eda795380bc2cca5e54115989))
* Add `code` to `ServerlessError` in `lib/utils` ([822a7cf](https://github.com/pjgm/serverless/commit/822a7cf9f527514b53fd8cfc5c172ec5dc53f4ce))
* Add `create-from-local-template` util ([03011ba](https://github.com/pjgm/serverless/commit/03011baf07d262a5b9702b34b75a997e3f525d28))
* Add `resolveRegion` util ([98e3668](https://github.com/pjgm/serverless/commit/98e3668a2cbb701c109e1ff8dd70a0ece1770f7b))
* Add `resolveStage` util ([09bb4fa](https://github.com/pjgm/serverless/commit/09bb4fa12270807702dcc26483dbcb94cf733342))
* Add debug logs ([cf7107c](https://github.com/pjgm/serverless/commit/cf7107cba2a19dedf8cfe2f038076431f4d03ef9))
* Add note about `autoupdate` in postinstall script ([93c88c0](https://github.com/pjgm/serverless/commit/93c88c0b8d1eea6455ca6ecb9a022f814f8e79b3))
* Added warning about dev mode ([#11975](https://github.com/pjgm/serverless/issues/11975)) ([e5cb8ac](https://github.com/pjgm/serverless/commit/e5cb8acbf238d3a31ca6ae98283b6edc1734098e))
* Adjust deprecation logs to reflect warning format ([b0938c7](https://github.com/pjgm/serverless/commit/b0938c7d9bd946c5c9af6bae99ae6f7931242ba6))
* Adjust invalid `code` for `ServerlessError` ([8c37e0a](https://github.com/pjgm/serverless/commit/8c37e0ac6df7a1a010e57ef14702185b2ef07dfa))
* **Analytics:** Alphabetical order ([0d605fa](https://github.com/pjgm/serverless/commit/0d605fa76f4c841cafdd8ab904079d8829527712))
* Automatically align multiline deprecations ([9cb86a4](https://github.com/pjgm/serverless/commit/9cb86a4af2ee0bdda605e5eb4fa14d964e5fe404))
* **AWS Alexa:** Remove obsolete condition ([2b1f6f4](https://github.com/pjgm/serverless/commit/2b1f6f44dde310aeab0a8488f834817433d76e45))
* **AWS API Gateway:** Adjust deprecation for `identitySource` ([0e01d9e](https://github.com/pjgm/serverless/commit/0e01d9e337860b9d1136586fbfaf0c43ac21cde0))
* **AWS API Gateway:** Deprecate default `identitySource` ([378a8f4](https://github.com/pjgm/serverless/commit/378a8f426de1b47a6810d21b90bf4c121d233c9c))
* **AWS APIGW:** Convert trailing arguments into options ([6af76ed](https://github.com/pjgm/serverless/commit/6af76ed23728d72fb0ea3912133870128805dda8))
* **AWS APIGW:** Rely on object destructuring ([388c299](https://github.com/pjgm/serverless/commit/388c2993f06bf884b0e8a671e06c9aa00ed302f2))
* **AWS APIGW:** Secure APIGateway endpoints resolution ([acb3dbb](https://github.com/pjgm/serverless/commit/acb3dbba42f19efb93196fa060f1f53522602aec))
* **AWS CloudFormation:** Improve conditional logic ([48a1685](https://github.com/pjgm/serverless/commit/48a16854a94e15e06a4e54275d1792cfeb8e0586))
* **AWS Credentials:** Remove undocumented `provider.credentials` ([d26e2ae](https://github.com/pjgm/serverless/commit/d26e2ae4b8db944bb6f9de55043b46285f08e726))
* **AWS Deploy:** Add bucket name to exception ([#11389](https://github.com/pjgm/serverless/issues/11389)) ([11b7a05](https://github.com/pjgm/serverless/commit/11b7a05fd3db362003412484245cc55bfab70181))
* **AWS Deploy:** Bump custom resources to `nodejs16.x` runtime ([93ce41e](https://github.com/pjgm/serverless/commit/93ce41e9d8bf29519b043cf3ee2910f02c884eea)), closes [#11367](https://github.com/pjgm/serverless/issues/11367)
* **AWS Deploy:** Convert to async/await ([ea87a73](https://github.com/pjgm/serverless/commit/ea87a73270f55f7b21c5ea94206ec1bf4808077a))
* **AWS Deploy:** Debug logs for check for changes logic ([9f76f19](https://github.com/pjgm/serverless/commit/9f76f19cf3cfe1e3e7e74953d15e5feb9cd875ac))
* **AWS Deploy:** Debug logs for logs subscription check ([895f320](https://github.com/pjgm/serverless/commit/895f320c60da21daf12afaab91e967576294f374))
* **AWS Deploy:** Deprecate `function` option in `deploy` command ([d861d11](https://github.com/pjgm/serverless/commit/d861d119ef94baaaa266934783e00a50182d7434))
* **AWS Deploy:** Ensure no internal dependency on `console` ([2a8ef3e](https://github.com/pjgm/serverless/commit/2a8ef3ed5abc6497b9552e1786586468d66d806a))
* **AWS Deploy:** Follow AWS naming in stack deploy action types ([a238a9b](https://github.com/pjgm/serverless/commit/a238a9bc902a1443007848c65d9a179ec78e5c8f))
* **AWS Deploy:** Generalize `uploadZipFile` logic ([26bc112](https://github.com/pjgm/serverless/commit/26bc112f1f5f34512b9255315b2fab3274d32f74))
* **AWS Deploy:** Handle main progress directly ([e8fd2be](https://github.com/pjgm/serverless/commit/e8fd2bee45b35d9cbd49b4e049769f03c4e42671))
* **AWS Deploy:** Improve custom resource generation log ([521861b](https://github.com/pjgm/serverless/commit/521861b6510fd345c2b596e4ec9e9ef7be01ac10))
* **AWS Deploy:** Improve error message ([d071c5f](https://github.com/pjgm/serverless/commit/d071c5f74d2d1deca71edebc53d072a1c90d8bad))
* **AWS Deploy:** Improve handling of progress message prefix ([1d21f0b](https://github.com/pjgm/serverless/commit/1d21f0bab824266e4628fa7874a7911aa77d2d3d))
* **AWS Deploy:** Improve internal resolution of hashes ([711b643](https://github.com/pjgm/serverless/commit/711b6439e06552d5c2bb411299b851f8f39f8a76))
* **AWS Deploy:** Improve progress logs for rollback ([24c45a0](https://github.com/pjgm/serverless/commit/24c45a08462741bde5e450d9cf6601b7d60ff49c))
* **AWS Deploy:** Minimize try/catch wrap ([a7d2cf0](https://github.com/pjgm/serverless/commit/a7d2cf060514618d9caf48a55dfd56f371f19ca6))
* **AWS Deploy:** Refactor `extendedValidate` to async ([e1d2b82](https://github.com/pjgm/serverless/commit/e1d2b8251ac7e06ca01fc3bb3505531cee459bce))
* **AWS Deploy:** Refactor `getMostRecentObjects` to async/await ([1461860](https://github.com/pjgm/serverless/commit/1461860dabe6f5154ee0d5e69b4c1ed16eb05616))
* **AWS Deploy:** Refactor to async/await ([8bb306b](https://github.com/pjgm/serverless/commit/8bb306b56f763f474e0c5cf32f07724223ca7f2a))
* **AWS Deploy:** Refactor to BbPromise.try ([31ccfe1](https://github.com/pjgm/serverless/commit/31ccfe1a79c8c91206f07986ebc2499d74885318))
* **AWS Deploy:** Refactor to native promises ([c5970e7](https://github.com/pjgm/serverless/commit/c5970e72a3129c349f719009deff017fce430e69))
* **AWS Deploy:** Rely on provider.request for AWS SDK calls ([#8913](https://github.com/pjgm/serverless/issues/8913)) ([4e05995](https://github.com/pjgm/serverless/commit/4e0599571afe11d4bd11aee14fe07be2be48fca0))
* **AWS Deploy:** Remove misleading `-v` shortcut ([#7666](https://github.com/pjgm/serverless/issues/7666)) ([1db8c5e](https://github.com/pjgm/serverless/commit/1db8c5e472287ed3f0893b7c8094866e6d2ec5b3))
* **AWS Deploy:** Remove obsolete check ([acefce9](https://github.com/pjgm/serverless/commit/acefce975552898de9a72e8431995d5eb42820fe))
* **AWS Deploy:** Replace 'async' dependency ([f9bcaae](https://github.com/pjgm/serverless/commit/f9bcaaead90fd8691a85941f4d5216d5357037ad))
* **AWS Deploy:** Simplify internal condition ([9fd9f23](https://github.com/pjgm/serverless/commit/9fd9f2364ede603c9302f3806e86fb19b9a6ba9c))
* **AWS Deploy:** Store resolved state on internal class ([1c00eb2](https://github.com/pjgm/serverless/commit/1c00eb29fe55bccd0fe2ca62fe2c99f93bc4b6db))
* **AWS Deploy:** Upload state file to deployment bucket ([5525a3e](https://github.com/pjgm/serverless/commit/5525a3e6f54209e80db98cb32baadd62aac16da9))
* **AWS Deploy:** Use change sets in CF deployments ([82b373e](https://github.com/pjgm/serverless/commit/82b373e9c7787bad05751bfffdcd30b0173473ae))
* **AWS HTTP API:** Convert "timeout" usage warnings to deprecations ([3b294fb](https://github.com/pjgm/serverless/commit/3b294fb1dbe9f22a6754b64530120a37ab4d16aa))
* **AWS HTTP API:** Ensure function name in a warning message ([dc958ff](https://github.com/pjgm/serverless/commit/dc958ff6bf9d4a69e5bb7b41a14cef0ec18ff00d))
* **AWS HTTP API:** Fix wording of error message ([b6e54f0](https://github.com/pjgm/serverless/commit/b6e54f06e26bffcb69360ad89edb9d07d78c624f))
* **AWS HTTP API:** Improve config resolution ([6a13eee](https://github.com/pjgm/serverless/commit/6a13eee0d4d3349ccb2a99929865feb6092e35dd))
* **AWS HTTP API:** Improve error message for 29s timeout ([08ad5ce](https://github.com/pjgm/serverless/commit/08ad5ce0400e7a9527aa74655d1deca788b5dacc))
* **AWS HTTP API:** Nest routeTargetData in config ([1dcc53b](https://github.com/pjgm/serverless/commit/1dcc53be4c002e56190ad29ee2ab337c516e0c5e))
* **AWS HTTP API:** Unify warning messages ([8d4ed6d](https://github.com/pjgm/serverless/commit/8d4ed6dd2a82bcd2f4db29bddadb724bf6e6184b))
* **AWS Lambda:** Do not deep merge when not necessary ([77b9268](https://github.com/pjgm/serverless/commit/77b92686a714141eeaa07beb7660cd695c955b6d))
* **AWS Lambda:** Do not use capitalized var names ([9877bc5](https://github.com/pjgm/serverless/commit/9877bc5568e983b0839d739ee79937233e09b95f))
* **AWS Lambda:** Ensure natural function reference when no alias ([91f1d2f](https://github.com/pjgm/serverless/commit/91f1d2f203350c456f071889f1553e6b099e2034))
* **AWS Lambda:** Generalize target alias resolution ([3a6865d](https://github.com/pjgm/serverless/commit/3a6865db7f1a8cda074aaea72dd8d938dbab1fd3))
* **AWS Lambda:** Improve function deploy skip message ([#11779](https://github.com/pjgm/serverless/issues/11779)) ([ad8c24e](https://github.com/pjgm/serverless/commit/ad8c24ecfca4ec9dea87d9114ad3f2afcab85ae2)), closes [#11614](https://github.com/pjgm/serverless/issues/11614)
* **AWS Lambda:** Improve var name ([cf54971](https://github.com/pjgm/serverless/commit/cf5497198b8db1a4d278f18361a9fc8df0b0564e))
* **AWS Lambda:** Improve variables naming ([95a397d](https://github.com/pjgm/serverless/commit/95a397d731c9dc785822828f3a08d5db49b42a6c))
* **AWS Lambda:** Introduce reusable lambda ARN resolver ([55a98bd](https://github.com/pjgm/serverless/commit/55a98bdd47a72e88fabbdf76f797a5d4ab4cb66d))
* **AWS Lambda:** Recognize all supported log retention days ([a4d0ad5](https://github.com/pjgm/serverless/commit/a4d0ad530b1c473cdb09ac1428717660b8b9ad5c))
* **AWS Lambda:** Reconfigure condition ([e8d4606](https://github.com/pjgm/serverless/commit/e8d4606a6a4a1b9e6b9951f61ab5e15941b302cb))
* **AWS Lambda:** Refactor to async/await ([0009b96](https://github.com/pjgm/serverless/commit/0009b963cd4dc4dc1a0c42c0d99458a655997870))
* **AWS Lambda:** Rely on more reliable Object.assign ([2714997](https://github.com/pjgm/serverless/commit/271499777db815b66094a9e91f10ec2b642a952a))
* **AWS Lambda:** Remove references to deprecated runtimes ([#11940](https://github.com/pjgm/serverless/issues/11940)) ([fe6e0a6](https://github.com/pjgm/serverless/commit/fe6e0a69ee167f52d036e8fde405184961a04a42))
* **AWS Lambda:** Remove support for async config on destination ([e131f26](https://github.com/pjgm/serverless/commit/e131f2661d9a508505ddf8599fb9ac6876c8ef15)), closes [#8138](https://github.com/pjgm/serverless/issues/8138)
* **AWS Lambda:** Resolve deep value once ([cbf8c74](https://github.com/pjgm/serverless/commit/cbf8c74c6d3c2ab1bfd2c71c938620821574d146))
* **AWS Lambda:** Resolve object once ([3e2f59e](https://github.com/pjgm/serverless/commit/3e2f59e27c92bdebbfb2b25f831293c4bccf133e))
* **AWS Lambda:** Support `provisionedConcurrency` set to `0`  ([e40ba43](https://github.com/pjgm/serverless/commit/e40ba43b84b373a1ef4ac92abc7bf41315ecf955))
* **AWS Local Invocation:** Rely on observable spawn ([6d97496](https://github.com/pjgm/serverless/commit/6d9749699da62a07ae933bd2c9a9ced8ccf877df))
* **AWS Local Invocation:** Remove ignored option ([6cbc83a](https://github.com/pjgm/serverless/commit/6cbc83aff0c922d6b6dc4f371d9b16d81c241433))
* **AWS Local Invocation:** Seclude runtime wrapping logic ([50bfd22](https://github.com/pjgm/serverless/commit/50bfd22096a0d3be58a5e2bac28c17325e2ba9df))
* **AWS S3:** Fix typo in var name ([#8106](https://github.com/pjgm/serverless/issues/8106)) ([37d80cb](https://github.com/pjgm/serverless/commit/37d80cb7cf2937e925034161ea820c15cca329fb))
* **AWS SQS:** Optimize IAM permissions generation ([#11685](https://github.com/pjgm/serverless/issues/11685)) ([99cd9e6](https://github.com/pjgm/serverless/commit/99cd9e69c14583c428c4fdb01496151c9582eb5b))
* **Binary Installer:** Ensure latest stable npm version in bundle ([ac75005](https://github.com/pjgm/serverless/commit/ac750053fd810c17c84ecf51cf066a51c9be3424))
* Bring back `_.flatMap` usage ([0199b0f](https://github.com/pjgm/serverless/commit/0199b0fe8c87d8e72e85ab2490fcfb0bf17af376)), closes [#9948](https://github.com/pjgm/serverless/issues/9948)
* Centralize npm command resolution ([ddf3bf4](https://github.com/pjgm/serverless/commit/ddf3bf40a30f29e29d4e1145fdbe1cfc9d3063d0))
* Change all occurences of succesful to successful ([#10639](https://github.com/pjgm/serverless/issues/10639)) ([77f8e56](https://github.com/pjgm/serverless/commit/77f8e56a6958824a727f8420c3ed1b06448b72f9))
* Cleanup ([95736ce](https://github.com/pjgm/serverless/commit/95736cea54e633aa47348ccb151566093a6ba634))
* Cleanup `remove` tests ([f12c7d8](https://github.com/pjgm/serverless/commit/f12c7d8d3027d4dbaa71af7ba45516e260e6bf82))
* Cleanup condition ([24d45dd](https://github.com/pjgm/serverless/commit/24d45dd2ee7c4bc9df3739d623c3111ed29e571d))
* Cleanup conditional ([006af9e](https://github.com/pjgm/serverless/commit/006af9e8f55def29844b8677aed850692f7a3656))
* Cleanup mergeIamTemplates module ([#8736](https://github.com/pjgm/serverless/issues/8736)) ([77e1a6a](https://github.com/pjgm/serverless/commit/77e1a6a30246f94fcdf8ae26ca2cb8617aa1db2b))
* Cleanup requires order ([54af908](https://github.com/pjgm/serverless/commit/54af90884cca7cee74b7768ba216ae19e851e591))
* Cleanup variables ([9db2e19](https://github.com/pjgm/serverless/commit/9db2e1904d69fc604962b44b64f3721cd4b263ec))
* **CLI:**  Handle "help" with a schema ([d455b23](https://github.com/pjgm/serverless/commit/d455b236cf719778ebaa5048a0941ae906a69cd4))
* **CLI Onboarding:** Add `history` and `stepHistory` to `context` ([9eea885](https://github.com/pjgm/serverless/commit/9eea885b390fc88bb62c1e2a5c3d108444139703))
* **CLI Onboarding:** Adjust summary messages in deploy step ([b751c50](https://github.com/pjgm/serverless/commit/b751c505c8050e229edb77d44016925c4e52a05e))
* **CLI Onboarding:** Adjustments to `deploy` step output ([58d6426](https://github.com/pjgm/serverless/commit/58d64262fedf4349bd21f60f89d644f9225d87ab))
* **CLI Onboarding:** Cleanup regex ([a296af0](https://github.com/pjgm/serverless/commit/a296af06c2c523ad1742d477c674bc68047c9b3b))
* **CLI Onboarding:** Configure debug logs ([83c8fdb](https://github.com/pjgm/serverless/commit/83c8fdb6e45d1ced5925a82f9569a25a3437e978))
* **CLI Onboarding:** Download templates from v2 examples branch ([46d090a](https://github.com/pjgm/serverless/commit/46d090a302b9f7f4a3cf479695489b7ffc46b75b))
* **CLI Onboarding:** Download templates from v3 examples branch ([4dbb496](https://github.com/pjgm/serverless/commit/4dbb496506d8e7937a08176cf9d7e307f4d64157))
* **CLI Onboarding:** Generalize `isConsole` resolution ([caaa3c8](https://github.com/pjgm/serverless/commit/caaa3c811e9f777c84fe91ea73b63eb609032b3b))
* **CLI Onboarding:** Hide not supported templates with console ([79e156f](https://github.com/pjgm/serverless/commit/79e156f7ac70d997093d2b2ca127f0844cab121a))
* **CLI Onboarding:** Improve debug logs ([914d00b](https://github.com/pjgm/serverless/commit/914d00b0a9758b4b799242efad6e66c98e1c7160))
* **CLI Onboarding:** Integrate steps from dashboard plugin ([105807a](https://github.com/pjgm/serverless/commit/105807a674820f2d8501f3b8539c3725fceab215))
* **CLI Onboarding:** Minor wording adjustments ([772a9bb](https://github.com/pjgm/serverless/commit/772a9bb86c4b9b4e65f5f834c39620359cfc7c7a))
* **CLI Onboarding:** Move `dashboard-login` step from plugin ([adef710](https://github.com/pjgm/serverless/commit/adef7102df2958e976445f0c247895f82decebf9))
* **CLI Onboarding:** Move `dashboard-set-org` from plugin ([afdf77c](https://github.com/pjgm/serverless/commit/afdf77c960c990f7daa445532789aebb9dc15a53))
* **CLI Onboarding:** Refactor to async/await ([1060d14](https://github.com/pjgm/serverless/commit/1060d1468ba587519df482e95a54bbc8d199cad8))
* **CLI Onboarding:** Remove `auto-update` step ([519f77e](https://github.com/pjgm/serverless/commit/519f77e1a876cea62843a99e58bab1e011e62fa3))
* **CLI Onboarding:** Reorganize `writeOrgAppAndConsole` input ([fc9dc1d](https://github.com/pjgm/serverless/commit/fc9dc1dc4022163ff6f28f1ee6de2db85fd56202))
* **CLI Onboarding:** Reorganize internal variables ([25d2e7a](https://github.com/pjgm/serverless/commit/25d2e7a2a0932f40ac5114702fce74a0caa9c019))
* **CLI Onboarding:** Seclude from internal Framework logic ([7864f4d](https://github.com/pjgm/serverless/commit/7864f4d28d4c4ed8325e64c8dfca891845edf392))
* **CLI Onboarding:** Simplify tabcompletion support check ([c13586e](https://github.com/pjgm/serverless/commit/c13586ee23614da75d71f40ff24037b9aad46c2c))
* **CLI Onboarding:** Support future object notation for `console` ([2f187a5](https://github.com/pjgm/serverless/commit/2f187a52eb3a14c6e94d00a37ded64ed75914d3f))
* **CLI Onboarding:** Use "Starter" not "Empty" for templates ([2984adb](https://github.com/pjgm/serverless/commit/2984adb0456f7d6e93b0c778a1c588ee20459928))
* **CLI:** `doctor` command for modern handling of deprecations ([452e234](https://github.com/pjgm/serverless/commit/452e234306a3703e95ad349305e1e211c165bf22))
* **CLI:** Adapt `logInfo` to modern logs ([771f99b](https://github.com/pjgm/serverless/commit/771f99b18d76060f030d36b5fa619dd41a7000c8))
* **CLI:** Adapt `logWarning` to modern logs ([d43298d](https://github.com/pjgm/serverless/commit/d43298d25bc9fcf5f5724a800b2693321e88e838))
* **CLI:** Adapt pre-created log style generators ([8c9bd4a](https://github.com/pjgm/serverless/commit/8c9bd4a6eda58d2ed6da08cc3bb806d970df4d17))
* **CLI:** Add Dashboard specific options to commands schema ([ed553a7](https://github.com/pjgm/serverless/commit/ed553a75267de5399809f2e9c848c60537e41fe2))
* **CLI:** Add debug log on unresolved variables meta ([450b793](https://github.com/pjgm/serverless/commit/450b793cc7481e094b71f4e74886dcab5b64b305))
* **CLI:** At schema define "--config" option ([78d0e9e](https://github.com/pjgm/serverless/commit/78d0e9ee454c3c2e38d58fcb8b5768da527f697b))
* **CLI:** Categorize CLI commands in schema ([471e34d](https://github.com/pjgm/serverless/commit/471e34ddc34962486e4bf78b33dbec566b561cf2))
* **CLI:** Change formatting of notifications ([#9807](https://github.com/pjgm/serverless/issues/9807)) ([7c51f55](https://github.com/pjgm/serverless/commit/7c51f55f5b8af6f853560ba5d757c65b1068a7ab))
* **CLI:** Change stack update progress logging method ([8184c01](https://github.com/pjgm/serverless/commit/8184c01c7c519e05ab9f7a1ab0e0484bfce2aafd))
* **CLI:** Cleanup components resolution logic ([cf1d51d](https://github.com/pjgm/serverless/commit/cf1d51dbb9b218dfc1cebfa1bf3c5f6eb1ab248b))
* **CLI:** Comment typo ([f103cbe](https://github.com/pjgm/serverless/commit/f103cbeffb1a0ea31bca759ccb8a1bf8abf2cec5))
* **CLI:** Conditionally apply post dotenv resolution logic ([30465cc](https://github.com/pjgm/serverless/commit/30465ccb0bfd1b56b89833208b3d96dba2ae8119))
* **CLI:** Configure processing flow debug logs ([7af0c8c](https://github.com/pjgm/serverless/commit/7af0c8cb07ee056e0224d35fdcdbac4ead004cee))
* **CLI:** Convert `isLocallyInstalled` to export result directly ([38fe60e](https://github.com/pjgm/serverless/commit/38fe60e04292d2712b957cb3c8374caeb3449bd4))
* **CLI:** Convert custom resoource related log ([0f0b85a](https://github.com/pjgm/serverless/commit/0f0b85a6373dfcd9d21f1668e7fb3e0d20a3b393))
* **CLI:** Cover image building with modern logs ([a2be338](https://github.com/pjgm/serverless/commit/a2be3387b16fdb7324e1342a5f6ee3974e4e34f5))
* **CLI:** Deprecate `-v` as alias for `--verbose` ([53b41eb](https://github.com/pjgm/serverless/commit/53b41eb53aeefe22dc29b785a428f3b184906d2c))
* **CLI:** Do not filter commands by `lifecycleEvents` for help ([6991d66](https://github.com/pjgm/serverless/commit/6991d66987d6276665bff07259bf1ca464ffeab7))
* **CLI:** Do not notify of update when new major is published ([230f34a](https://github.com/pjgm/serverless/commit/230f34aa9905636e53e1e63b769024f934689e6b))
* **CLI:** Do not read service config for service unrelated commands ([e01dfac](https://github.com/pjgm/serverless/commit/e01dfacd834e3c208f4052563dbb536d167d9f4b))
* **CLI:** Do not show deprecation with help command ([a72b681](https://github.com/pjgm/serverless/commit/a72b6816358a721f3957be40a35ae3d945eb80d1))
* **CLI:** Do not show progress bar in `info` command ([6e5c39e](https://github.com/pjgm/serverless/commit/6e5c39ee4c758b239884885ac0267d45f2de1201))
* **CLI:** Do not show resource progress on stack creation ([8dd32e5](https://github.com/pjgm/serverless/commit/8dd32e5542ca8d4dcbbbfa3b38c6158a34a87651))
* **CLI:** Do not throw errors when help command ([d15efd9](https://github.com/pjgm/serverless/commit/d15efd91087183b65201e2eaccbb9719f0b34e4e))
* **CLI:** Document processs flow ([cf43198](https://github.com/pjgm/serverless/commit/cf431984fc45ef1dc01ada33653184ef744fabb2))
* **CLI:** Enhanced modern error reporting for CloudFormation ([cfd828e](https://github.com/pjgm/serverless/commit/cfd828ece872b572cbb46670437e8196f2200903))
* **CLI:** Ensure alphabetical order ([e7edbcd](https://github.com/pjgm/serverless/commit/e7edbcde8cd582871ac7eb57f0531f6b55088c49))
* **CLI:** Ensure empty line prior final status  with progress ([c9f2227](https://github.com/pjgm/serverless/commit/c9f22278b3a8c5fd4d1400ef948ae6b72f333223))
* **CLI:** Ensure no monkey patching by progress override ([e46ce80](https://github.com/pjgm/serverless/commit/e46ce80d99414ff730355efd1636bab71bb1771c))
* **CLI:** Ensure resolved `provider.region` if dashboard ([af0242d](https://github.com/pjgm/serverless/commit/af0242d716613777b2d03b418c9df39e984bb559))
* **CLI:** Ensure telemetry logs are issued at debug level ([7b36038](https://github.com/pjgm/serverless/commit/7b360386eadb9a83af73514ced34bc901af43457))
* **CLI:** Ensure to have up to date commands ([8142515](https://github.com/pjgm/serverless/commit/8142515bfc34fe88fc12f599aff6453217959ba5))
* **CLI:** Export resolved local installation path directly ([c18e1b3](https://github.com/pjgm/serverless/commit/c18e1b308bd4d2f30186d77dc77493cc8c17a4c1))
* **CLI:** Expose "--help" in supported command options ([21cc4cf](https://github.com/pjgm/serverless/commit/21cc4cf8cb1a19a34cd50ab211cb55246f2e6ca6))
* **CLI:** Expose dashboard provider name when starting deployment ([6698fa6](https://github.com/pjgm/serverless/commit/6698fa657e5a5b35908c2b2de0815525f948064f))
* **CLI:** Expose function artifact size in deploy summary ([8746100](https://github.com/pjgm/serverless/commit/87461007f809c67a78b7dd722847efef2e4f72b3))
* **CLI:** Expose resolved string command by `resolveInput` util ([362f5e9](https://github.com/pjgm/serverless/commit/362f5e94e044f51fe6e9b2f9de4de810fb9f8d04))
* **CLI:** Extend `processSpanPromise` span ([350ef12](https://github.com/pjgm/serverless/commit/350ef1257a8573dc81b2aa10fedec471e089908b))
* **CLI:** Fix "config tabcompletion uninstall" usage info ([6752945](https://github.com/pjgm/serverless/commit/6752945eaa0bc7fc3fb677a772168c20859f07cb))
* **CLI:** Fix deprecation message typo ([7f788d2](https://github.com/pjgm/serverless/commit/7f788d29e5b7ba45b9a3648b0b645f17706ac4a4))
* **CLI:** Fix typo in error message ([#10421](https://github.com/pjgm/serverless/issues/10421)) ([fa1d8fd](https://github.com/pjgm/serverless/commit/fa1d8fdb31ef2834f19b64dceca879974d18d9ff))
* **CLI:** Fix typo in error message ([#9682](https://github.com/pjgm/serverless/issues/9682)) ([f16c45f](https://github.com/pjgm/serverless/commit/f16c45f84b8be1e469bfdd92191fc760b8f1631e))
* **CLI:** Fix typos in `create` CLI messages ([#10933](https://github.com/pjgm/serverless/issues/10933)) ([26f79aa](https://github.com/pjgm/serverless/commit/26f79aaf19f39725e81461ee06b79cb00a6d14db))
* **CLI:** Generalize `writeServiceOutputs` ([8aa700d](https://github.com/pjgm/serverless/commit/8aa700dc7947d36aa46bba4b0e475f21fd19ac89))
* **CLI:** Generalize handling of not supported commands ([8b301dc](https://github.com/pjgm/serverless/commit/8b301dce9c06f9ef463f9f3572a02d0de8d3539d))
* **CLI:** Generalize property resolution validation ([59434af](https://github.com/pjgm/serverless/commit/59434afd9519ed41bbb607f5bdb16b1158936798))
* **CLI:** Improve command resolution handling ([0065200](https://github.com/pjgm/serverless/commit/00652005d44886c472c8ca6b0e77a5619e1601c0))
* **CLI:** Improve condition ([8d44a49](https://github.com/pjgm/serverless/commit/8d44a49e597b2f555715818150a5590f71132121))
* **CLI:** Improve error construct ([140990d](https://github.com/pjgm/serverless/commit/140990d150f109c56c2c43e45f3fd4995d70054a))
* **CLI:** Improve file size output in logs ([4448490](https://github.com/pjgm/serverless/commit/44484903b38eaa18c3e3838b8a3f217922a233e5))
* **CLI:** Improve flow documentation ([851c9f4](https://github.com/pjgm/serverless/commit/851c9f4d52a69c3ac0f15f5fb353ae9f7a554530))
* **CLI:** Improve handling of service outputs in modern logs ([7d19ca8](https://github.com/pjgm/serverless/commit/7d19ca857230a56bbe40bda4d6704edd34019e4e))
* **CLI:** Improve help resolution documentation ([3dd915c](https://github.com/pjgm/serverless/commit/3dd915cd3f1af1893c1e600d9c0cf0ab8125d5a3))
* **CLI:** Improve inner flow documentation ([6425e4a](https://github.com/pjgm/serverless/commit/6425e4ae49d6b1e26aeb34f4dd3cb76807ee7e65))
* **CLI:** Improve log spacing ([e0befa4](https://github.com/pjgm/serverless/commit/e0befa48bb47a1cb04f2d293e607a064f66da2db))
* **CLI:** Improve logic ([006cec5](https://github.com/pjgm/serverless/commit/006cec5f2c62c322491e854084fd27438d1e87fc))
* **CLI:** Improve main progress message ([533f709](https://github.com/pjgm/serverless/commit/533f709c5833619d5ce86ec987133ff0f148c8e0))
* **CLI:** Improve modern `info` output ([2828a2c](https://github.com/pjgm/serverless/commit/2828a2c44388d731d4396e0ea11ae48953f20b0a))
* **CLI:** Improve modern error reporting ([a205f88](https://github.com/pjgm/serverless/commit/a205f88310653331c96f51402d148c576dd79db8))
* **CLI:** Improve modern logs for `logs` command ([d1701bf](https://github.com/pjgm/serverless/commit/d1701bf13a7155cce388424964e35ca536b2ce8a))
* **CLI:** Improve module imports order ([dff2799](https://github.com/pjgm/serverless/commit/dff2799941a1da8c2d5fe76144393db241a7637c))
* **CLI:** Improve post install log to reflect modern style ([d0d0161](https://github.com/pjgm/serverless/commit/d0d016168506177ba3a7dcb066607b8685f00f38))
* **CLI:** Improve presentation of multi-line backend notifications ([1abb3c0](https://github.com/pjgm/serverless/commit/1abb3c05b58e744bdfa24879921cdaf91438d6f5))
* **CLI:** Improve progress for CloudFormation updates ([1e77417](https://github.com/pjgm/serverless/commit/1e774170267da496f009c5504136201e86116901))
* **CLI:** Improve setup of resolution flow ([ab1c673](https://github.com/pjgm/serverless/commit/ab1c673bb2f7d4279d0406f355516d616e1f00c8))
* **CLI:** Improve style for local fallback modern notice ([73c071b](https://github.com/pjgm/serverless/commit/73c071b060216d330974a2f98917eba315eb634b))
* **CLI:** Improve timestamp visiblity in `deploy list` output ([55146c4](https://github.com/pjgm/serverless/commit/55146c4595024b0e3702dc2023264af784b906e9))
* **CLI:** Improve user message ([20afe33](https://github.com/pjgm/serverless/commit/20afe339231112e4d5ade9498386ac3c00e37e04))
* **CLI:** Improve validation of resolution state of core config ([9e84423](https://github.com/pjgm/serverless/commit/9e844234133d0b796bdeb2bdcce557da4ca996e3))
* **CLI:** Integrate isHelpRequest into resolveInput util ([a481170](https://github.com/pjgm/serverless/commit/a48117041c3993f5ba969329dd605f6a80efcbad))
* **CLI:** Introduce modern warning about resource limit ([ca705b8](https://github.com/pjgm/serverless/commit/ca705b8cc2854c302158a56294c2507ba5f2038f))
* **CLI:** Minor modern logs updates ([39c09e4](https://github.com/pjgm/serverless/commit/39c09e44b6380ec1a13aa50aca9082cffb0aeca1))
* **CLI:** Moder logs for `logs` command ([cbd2e64](https://github.com/pjgm/serverless/commit/cbd2e64f705e54e37dd9116d0931a3a96bceaa88))
* **CLI:** Modern log for local version fallback ([231095d](https://github.com/pjgm/serverless/commit/231095d28d4e3f137ef0a456692dd5d6a770a5db))
* **CLI:** Modern logs for `config credentials` command ([bcb2408](https://github.com/pjgm/serverless/commit/bcb240893d89127cc1eada7255864b7bfeb88a61))
* **CLI:** Modern logs for `config tabcompletion install` command ([16a7739](https://github.com/pjgm/serverless/commit/16a7739411141487fa33f8a72f88d82db712bfc9))
* **CLI:** Modern logs for `config tabcompletion uninstall` command ([02eebb4](https://github.com/pjgm/serverless/commit/02eebb4643435341235340f5da8c7db903cb12e6))
* **CLI:** Modern logs for `config` command ([7926570](https://github.com/pjgm/serverless/commit/7926570557e5c0a4dd661c069eecc1d4a0cf9b5d))
* **CLI:** Modern logs for `create` command ([05f937f](https://github.com/pjgm/serverless/commit/05f937f2e731e641e93e9db4af4acd58dc117422))
* **CLI:** Modern logs for `install` command ([bd4d215](https://github.com/pjgm/serverless/commit/bd4d215266b16793c26d06a34af8482f00e47844))
* **CLI:** Modern logs for `invoke local` command ([82dd1e4](https://github.com/pjgm/serverless/commit/82dd1e4c70d335cc10485b5ac20467447809941b))
* **CLI:** Modern logs for `invoke` command ([2af95c0](https://github.com/pjgm/serverless/commit/2af95c03865b5b59bacba9e080348dddf11d0bb5))
* **CLI:** Modern logs for `metrics` command ([592596c](https://github.com/pjgm/serverless/commit/592596c73bfe0a9b6ef6bdff5d898ae9ef5e2788))
* **CLI:** Modern logs for `plugin install` command ([8c5f22c](https://github.com/pjgm/serverless/commit/8c5f22ceb67c3a2f4ace3adf8e19cf5e69d4c7b3))
* **CLI:** Modern logs for `plugin list` command ([00e016c](https://github.com/pjgm/serverless/commit/00e016c4bba86095744129d24683343f0cc5129f))
* **CLI:** Modern logs for `plugin search` command ([1463171](https://github.com/pjgm/serverless/commit/1463171cae93e9e050350f6eb272e35cfade0204))
* **CLI:** Modern logs for `plugin uninstall` command ([3094be0](https://github.com/pjgm/serverless/commit/3094be0cf06f916d8cf180036433677ecd73e013))
* **CLI:** Modern logs for `print` command ([4ed34c3](https://github.com/pjgm/serverless/commit/4ed34c3e5e21903a3fe9e512621739ef5bf0bd84))
* **CLI:** Modern logs for `remove` command ([3934cad](https://github.com/pjgm/serverless/commit/3934cadce052b50d76c1dcd49da588cd9f079175))
* **CLI:** Modern logs for `rollback function` command ([4cbc342](https://github.com/pjgm/serverless/commit/4cbc3424dabebb3b533d463b3ead523f2daf4a77))
* **CLI:** Modern logs for `rollback` command ([f0970e0](https://github.com/pjgm/serverless/commit/f0970e04fa31774aa7400b4c620920dadcb3cfa2))
* **CLI:** Modern logs for `slstats` command ([0c9dae1](https://github.com/pjgm/serverless/commit/0c9dae1210b9456ec96bc38a717a901beaa45a7b))
* **CLI:** Modern logs for `uninstall` command ([2787ea0](https://github.com/pjgm/serverless/commit/2787ea07a9a183695e6f7a58bcc0171e086d456b))
* **CLI:** Modern logs for `upgrade` command ([9b5e6b1](https://github.com/pjgm/serverless/commit/9b5e6b12371317356d9cb4600a4a574df305f63f))
* **CLI:** Modern logs for interactive setup ([07aed34](https://github.com/pjgm/serverless/commit/07aed3429c63ed13ad9ca6262c641a907170f4f9))
* **CLI:** Move lifecycles definition to commands schema ([2294a4b](https://github.com/pjgm/serverless/commit/2294a4b4cb938ec34492bb5979da0677ff1d602f))
* **CLI:** Move main help renderer out of internals ([053fea1](https://github.com/pjgm/serverless/commit/053fea18e0295507511881e59350207e60f142be))
* **CLI:** Move to CLI logic required options validation ([afad231](https://github.com/pjgm/serverless/commit/afad2315a52785b0fff2408bb502698f176ff144))
* **CLI:** Move var declaration ([6a84560](https://github.com/pjgm/serverless/commit/6a845604057a3c115a7d7d32ff0ed20e9e3bd311))
* **CLI:** Pass `serverless` instance to `handle-error` ([07a5483](https://github.com/pjgm/serverless/commit/07a5483bb6e989aa5d29b0bba03fd2160be28fb7))
* **CLI:** Pass resolved commands options to local installation ([2d4d05d](https://github.com/pjgm/serverless/commit/2d4d05d425bc686c11b284354f5cc2ccead3814d))
* **CLI:** Prevent superfluous vars resolution with help request ([c2d4f83](https://github.com/pjgm/serverless/commit/c2d4f834e5acccc022cd9769b6fe369b76ebdd4c))
* **CLI:** Proritize `provider.name` validation ([9ab04a6](https://github.com/pjgm/serverless/commit/9ab04a674771e84ec302d7a7783b3b3c09889d26))
* **CLI:** Put least significant options to end of index ([57543a9](https://github.com/pjgm/serverless/commit/57543a9c64181a2474672ce830790dfe3a048250))
* **CLI:** Recalculate options only if external plugins were loaded ([9aa026d](https://github.com/pjgm/serverless/commit/9aa026d8f77020b466730fd16c908c5339943bee))
* **CLI:** Recognize "--version" on command as help request ([23f45a3](https://github.com/pjgm/serverless/commit/23f45a34de244b5d7ead1e300cb0aa2cdd57a372))
* **CLI:** Recognize "app" and "org"  params ([6b1921f](https://github.com/pjgm/serverless/commit/6b1921f59e1105499a329ab3aaf6134e7fb0ff6c))
* **CLI:** Recognize `--help` for `compose` triage ([37b29b0](https://github.com/pjgm/serverless/commit/37b29b029579191e82348afbf855590c2cb37062))
* **CLI:** Recognize `SLS_DISABLE_AUTO_UPDATE` env var ([c939457](https://github.com/pjgm/serverless/commit/c939457ba46232b247a691b23c95f8408eba406f))
* **CLI:** Recognize interactive setup command in commands schema ([b9afc14](https://github.com/pjgm/serverless/commit/b9afc144bf0aea4e20d7996df5d8c52430f39b23))
* **CLI:** Reconfigure dashboard related warning to modern logs ([7c91cde](https://github.com/pjgm/serverless/commit/7c91cde7ac5c8bbe983b213de090bde4326af85a))
* **CLI:** Refactor "-v" handling ([8db64a1](https://github.com/pjgm/serverless/commit/8db64a1f319d2238e71960d57425d2b6e5c9c5d6))
* **CLI:** Refactor flow into IIFE ([32013dc](https://github.com/pjgm/serverless/commit/32013dc9bbe7e708cc2692012b474724e10a6784))
* **CLI:** Refactor main progress event with `isMainEvent` option ([a6553f8](https://github.com/pjgm/serverless/commit/a6553f8668b66e2281626e7e79a3a2042279f92d))
* **CLI:** Refactor to async/await ([adc4e2f](https://github.com/pjgm/serverless/commit/adc4e2f8cfbfc9c56ac44b7206de8930fe6d5682))
* **CLI:** Rely internally on `@serverless/utils/log` ([05588f7](https://github.com/pjgm/serverless/commit/05588f77c0bbc900198ce458099ea2db066f3601))
* **CLI:** Rely on `cli/is-help-request` util ([c9087ec](https://github.com/pjgm/serverless/commit/c9087ec4e659f2d1c894f814f6a0c54d0ddb6dcc))
* **CLI:** Rely on new CLI args parser ([9e059d0](https://github.com/pjgm/serverless/commit/9e059d0f45b083f887bc07f0cbf33a81f5b91ba2))
* **CLI:** Rely on newly introduced log style functions ([e070110](https://github.com/pjgm/serverless/commit/e070110eee0e679694aefd4e6b5f25ecc90793d4))
* **CLI:** Remove deprecated bin/serverless file ([#8142](https://github.com/pjgm/serverless/issues/8142)) ([4ceaca0](https://github.com/pjgm/serverless/commit/4ceaca022a6292b56239a35933499a63ae242479))
* **CLI:** Remove empty line in `info` command ([03b4b3d](https://github.com/pjgm/serverless/commit/03b4b3d47c25b6f98a46699463288c94b051f42c))
* **CLI:** Remove internal CLI arguments parsing ([16950d0](https://github.com/pjgm/serverless/commit/16950d098b0b78e6ad5de35e908c7a1ee91f775b))
* **CLI:** Remove no longer valid comment ([5108b23](https://github.com/pjgm/serverless/commit/5108b23d90b84005544cafcf2536dffaf459b549))
* **CLI:** Remove obsolete `v` postfix when listing global version ([5013af0](https://github.com/pjgm/serverless/commit/5013af01476fb3d13f31775ff4171bc98a35d39d))
* **CLI:** Remove redundant arg ([8451b89](https://github.com/pjgm/serverless/commit/8451b8908c080bcbe839949d0bf1ae4280a5697a))
* **CLI:** Rename load-dotenv util ([b5ad0e4](https://github.com/pjgm/serverless/commit/b5ad0e4a4297e2805c5ee98e360854660aa497d9))
* **CLI:** Rename module to unify convention ([03817c2](https://github.com/pjgm/serverless/commit/03817c23fbd757a6c9ac4599c7d68957881a2c99))
* **CLI:** Render help out of internal context ([2eb61fc](https://github.com/pjgm/serverless/commit/2eb61fc5104f6b9a5b7bd2551283f22606a8d1e8))
* **CLI:** Replace `process.stdout` use with modern logs ([be00a26](https://github.com/pjgm/serverless/commit/be00a2672cbc90fb33dee5e4bd44a1f6a127eb7c))
* **CLI:** Replace warnings with modern counterparts ([4da0899](https://github.com/pjgm/serverless/commit/4da08996736c9a8f2b0a0193f7cca4b24f3fc6f1))
* **CLI:** Report `credentials` source in modern error output ([b4ff87d](https://github.com/pjgm/serverless/commit/b4ff87dc81286b8123830f20bccfb3aa320e4ccd))
* **CLI:** Require variablesResolutionMode to be resolved upfront ([a488000](https://github.com/pjgm/serverless/commit/a488000dc67c10026d010744bb29fca25f72f42b))
* **CLI:** Resolve .env files before intializing Serverless instance ([a9e3a66](https://github.com/pjgm/serverless/commit/a9e3a667355e91af7fb558eb551ed7d59a865527))
* **CLI:** Resolve command and options gradually ([b6382fd](https://github.com/pjgm/serverless/commit/b6382fdb7abcdf42098c57263799ea004bdb1481))
* **CLI:** Resolve commands and options by schema ([fe663ea](https://github.com/pjgm/serverless/commit/fe663ead50ff6925fb09207492a188f5f5bbda7e))
* **CLI:** Return resolved `commandSchema` from `resolveInput` util ([4364acc](https://github.com/pjgm/serverless/commit/4364acca588919c0b3bf69eb0c1cb44a2009d0b4))
* **CLI:** Reuse already imported module ([be441cc](https://github.com/pjgm/serverless/commit/be441ccd9157b351fffe6ea21664624aeeeb4b29))
* **CLI:** Reuse same argv slice ([fffd00c](https://github.com/pjgm/serverless/commit/fffd00cbe8ba7fe66775bb9fe4ac126155b1e316))
* **CLI:** Reuse variable ([734d2e8](https://github.com/pjgm/serverless/commit/734d2e800fb80d75d93918027609c5e1dc7b5c96))
* **CLI:** Schema for `@serverless/enterprise-plugin` commands ([116fe85](https://github.com/pjgm/serverless/commit/116fe85fbeac0408be6c6f5761573d5af340e8f1))
* **CLI:** Seclude `paramRegExp` ([da0e463](https://github.com/pjgm/serverless/commit/da0e4637f31cf69f154f9eb389ab962d504c5361))
* **CLI:** Seclude command help render from internals ([aca3c0d](https://github.com/pjgm/serverless/commit/aca3c0d57d563237aa1c1d8dfb3eccf809536e57))
* **CLI:** Seclude command options render logic out of internals ([41e921a](https://github.com/pjgm/serverless/commit/41e921aa6fa74d07ce7d1757cc1101f09f3e7f47))
* **CLI:** Seclude Framework CLI script ([dc826b4](https://github.com/pjgm/serverless/commit/dc826b4fdd387bfef0cc74a69e0370815011901b))
* **CLI:** Seclude general help render logic from internals ([87b1861](https://github.com/pjgm/serverless/commit/87b186113a3b76c2b8065b3d97f7c8fa0c68984e))
* **CLI:** Seclude interactive setup help render out of internals ([2fd921d](https://github.com/pjgm/serverless/commit/2fd921dbfc613f9064e069d00f1c5d11c8b86879))
* **CLI:** Seclude schema of core commands ([14a2640](https://github.com/pjgm/serverless/commit/14a2640bd9e65e357f606635a15ce0b07625b3aa))
* **CLI:** Seclude service config path resolution out of internals ([b23bfdb](https://github.com/pjgm/serverless/commit/b23bfdbf6ad915ec00fec562f8b75c40c44dd19d))
* **CLI:** Seclude uncaught exception handling ([e142254](https://github.com/pjgm/serverless/commit/e142254056fcfdc94d0642618df72e885bdf07b3))
* **CLI:** Seclude version output functionality out of CLI class ([b61621a](https://github.com/pjgm/serverless/commit/b61621adebb7eb33fd080db3fff13d7e9a32d99b))
* **CLI:** Simplify CF deploy progress ([be60ed4](https://github.com/pjgm/serverless/commit/be60ed4cee15ec0a47be5c08da9e0ce4a3f54136))
* **CLI:** Simplify deploy function args patch ([f51f9a5](https://github.com/pjgm/serverless/commit/f51f9a5fb932b625088d1e4915156afa3673a5cd))
* **CLI:** Split inline strings so code fits 100 width ([b848e39](https://github.com/pjgm/serverless/commit/b848e3951b72e33775f200b9cbd86f27a3872ac7))
* **CLI:** Support `decoratedMessage` on `ServerlessError` ([2217158](https://github.com/pjgm/serverless/commit/2217158764dde8ceee472292b531836ada20d79a))
* **CLI:** Unify argv to commands and options resolution ([ca4d046](https://github.com/pjgm/serverless/commit/ca4d046785e7489110ece9fa8011f8f2dd843ebf))
* **CLI:** Unify finalization of a process handling ([6b26a7d](https://github.com/pjgm/serverless/commit/6b26a7d360d7daf367f45ceef8b75ef53260f301))
* **CLI:** Update link style for modern logs ([6264296](https://github.com/pjgm/serverless/commit/62642964bc38eae77b009ea84d05ba741383570f))
* **CLI:** Upgrade to v7 of `open` library ([80fef65](https://github.com/pjgm/serverless/commit/80fef653974a5b42798cb2fd1a3ccc8dd867fca9))
* **CLI:** Validate service dependency in CLI context ([088088c](https://github.com/pjgm/serverless/commit/088088c1d345ff07e0b098f28d46f325b9e0b4cc))
* **CLI:** Wrap with function for better maintainance ([ab055a3](https://github.com/pjgm/serverless/commit/ab055a3390fb6d0f20c2bc87916ddb19c8d58d7f))
* **Components:** Remove check that was put into components logic ([6eda4aa](https://github.com/pjgm/serverless/commit/6eda4aa4ff2291375591bb211cc0ddca3030730a))
* **Config Schema:** Convert `oneOf` to more optimal `anyOf` ([2c874e2](https://github.com/pjgm/serverless/commit/2c874e22c97fe35290b14736df4b63097d3a9d50))
* **Config Schema:** Define AWS definitions in context of provider ([c79cae2](https://github.com/pjgm/serverless/commit/c79cae2308af0b038ef6fcfcf28be8841493e745))
* **Config Schema:** Do not pass obsolete arguments ([9bec422](https://github.com/pjgm/serverless/commit/9bec4226e5b90e8dd93b44b9be07a5d5fc3187ef))
* **Config Schema:** Do not rely on `ajv-keywords` ([#10490](https://github.com/pjgm/serverless/issues/10490)) ([420d124](https://github.com/pjgm/serverless/commit/420d124fd384b03d7e3e5d74f0b7eb7d263683cc))
* **Config Schema:** Ensure alphabetical order ([734482e](https://github.com/pjgm/serverless/commit/734482eab5be13727684f26fcad2debac6c49032))
* **Config Schema:** Ensure alphabetical order ([b892a97](https://github.com/pjgm/serverless/commit/b892a97d555ea109a7ac4d70114f8008d96acc09))
* **Config Schema:** Explain missing definition ([2b0f157](https://github.com/pjgm/serverless/commit/2b0f157ab2a436534182c50b69daa1302dc0d4f2))
* **Config Schema:** For consistency mark required top level props ([877cbb3](https://github.com/pjgm/serverless/commit/877cbb3fb8ab1f311d190e3697b291885dc1d050))
* **Config Schema:** Improve comments ([c51e293](https://github.com/pjgm/serverless/commit/c51e293ff422c416cc6af506fc3470085d7d7351))
* **Config Schema:** Improve error message and documentation ([a36247b](https://github.com/pjgm/serverless/commit/a36247b7ac1212a27f5e8d671ba39ba4c7e4de18))
* **Config Schema:** Improve error messaging for same type variants ([8ac249b](https://github.com/pjgm/serverless/commit/8ac249b1eadf3173359e02886e71bb89234ebd51))
* **Config Schema:** Improve signal intent comment ([51a10aa](https://github.com/pjgm/serverless/commit/51a10aa262af51c5df76e43a804b74c65bba010c))
* **Config Schema:** List properties in alphabetical order ([e028f5e](https://github.com/pjgm/serverless/commit/e028f5e26987e8e9161e93492a3dde646de46fd7))
* **Config Schema:** Move docs to website page ([c370295](https://github.com/pjgm/serverless/commit/c370295be6a67c5a7c5e2af323b29588cbc1d02e))
* **Config Schema:** No point in creating new object ([9481029](https://github.com/pjgm/serverless/commit/9481029b59007940ef050a8da29b2709741c2bd7))
* **Config Schema:** Remove dead configuration ([ddd8f88](https://github.com/pjgm/serverless/commit/ddd8f883ae7d4afe255206157100e9f70d431937))
* **Config Schema:** Rename `cfImport` definition to `awsCfImport` ([7f04819](https://github.com/pjgm/serverless/commit/7f048199161bb98fed56a054859464d120b765ce))
* **Config Schema:** Run schema validation only in service context ([c271218](https://github.com/pjgm/serverless/commit/c2712183a5dae0726c56456d8b3b790e7c597052))
* **Config Schema:** Treat "resources" as fully provider specific ([6d7e967](https://github.com/pjgm/serverless/commit/6d7e96722721c8a5c614bea2802af7142011d35f))
* **Config Schema:** Unified color scheme ([2c19bf5](https://github.com/pjgm/serverless/commit/2c19bf5eaea876f38cf0fd6fb8c453fbfe8d416a))
* Configure main progress titles through command schema ([9e308bd](https://github.com/pjgm/serverless/commit/9e308bdf041c73eb2d27408ae4e03bc10fe9bf8a))
* Configure promise returning functions as async ([#10309](https://github.com/pjgm/serverless/issues/10309)) ([4d4f863](https://github.com/pjgm/serverless/commit/4d4f8637d830ba9a72806fc127fe3497f7c0f23c))
* **Console:** Add missing `OTEL_RESOURCE_ATTRIBUTES` var ([1f9458b](https://github.com/pjgm/serverless/commit/1f9458b4f11c23f8e7fb0b4f9090dbd089224d1e))
* **Console:** Communicate new token implications with verbose mode ([7e56aa1](https://github.com/pjgm/serverless/commit/7e56aa17939021c920ba4046684386016b8f7a1f))
* **Console:** Configure `login` as standalone command ([fffaf9c](https://github.com/pjgm/serverless/commit/fffaf9cee2da00bdb4f8d13846ad216d4dee13ef))
* **Console:** Configure `logout` as standalone command ([70ca359](https://github.com/pjgm/serverless/commit/70ca3594b6fbc1118b24c2bc4975219f6c00cbd0))
* **Console:** Do not disable dashboard with console ([e6cdc9d](https://github.com/pjgm/serverless/commit/e6cdc9d68bed6bafb78bbb1bf4490e5dc35c4fdd))
* **Console:** Document `--console` with a link to documentation ([23a5ea3](https://github.com/pjgm/serverless/commit/23a5ea3a3a53a2e9fb7f1a65160d22c8868ddbbe))
* **Console:** Dynamically resolve latest version of the extension ([c28c48c](https://github.com/pjgm/serverless/commit/c28c48c6a131201448c6018d6e6951d7d9131eeb))
* **Console:** Ensure to list extension layer in layers output ([14109e8](https://github.com/pjgm/serverless/commit/14109e8ec475c71170215154b8ad92aecdb5f432))
* **Console:** Fix typo in user message ([1305107](https://github.com/pjgm/serverless/commit/13051079ab9e51053daf05b2914b331cde7c2207))
* **Console:** Generalize `bucketName` resolution ([103fc55](https://github.com/pjgm/serverless/commit/103fc554fc21bf7f8f16a634836bfe10d5109446))
* **Console:** Generalize user config handling ([2e889c8](https://github.com/pjgm/serverless/commit/2e889c8666d3fd733cc8703337053bbb7477a9af))
* **Console:** Improve error reporting when layer cannot be added ([ba71dd9](https://github.com/pjgm/serverless/commit/ba71dd9fb527ebac854e4a12b974581f4de6e57e))
* **Console:** Improve user error message ([6748642](https://github.com/pjgm/serverless/commit/67486421235dc8d7a76f760eecb68b1a13b13fb2))
* **Console:** Present url to console UI ([0d9f866](https://github.com/pjgm/serverless/commit/0d9f86620b9c600dfecaf2a194a499b57c5bac0c))
* **Console:** Propagate `disableLogsCollection` to user settings ([4521eb7](https://github.com/pjgm/serverless/commit/4521eb7e3b3eb72af7c535fda9cf6efcb4a1e140))
* **Console:** Rely on generic `apiRequest` for ingestion tokens ([0cecae7](https://github.com/pjgm/serverless/commit/0cecae75ffad4b7b89148b614d0bb82dc3b3501c))
* **Console:** Reorganize env variables setup ([8d947e9](https://github.com/pjgm/serverless/commit/8d947e9b5f7937e9127a4ea044a70300026b1985))
* **Console:** Report command which originated login operation ([8d4bf4f](https://github.com/pjgm/serverless/commit/8d4bf4fbfdf79950e92ad4fbb171f6fa15b11886))
* **Console:** Report logs with opt out option ([ababd90](https://github.com/pjgm/serverless/commit/ababd90f098f922a92a79ca7bdb00a3dfe112c6b))
* **Console:** Report requests and responses to server ([fa8243f](https://github.com/pjgm/serverless/commit/fa8243f960df372b644e791374842f04bfab7857))
* **Console:** Report used layer extension version to telemetry ([db89f20](https://github.com/pjgm/serverless/commit/db89f20f01b66c7dfc81f1571dfb215ba85daa24))
* **Console:** Separate Dashboard & Console login logic ([443fa4b](https://github.com/pjgm/serverless/commit/443fa4b74d1fceeb4798ba2b6acb31281b80756e))
* **Console:** Support `disableRequestResponseMonitoring` setting ([e5c088f](https://github.com/pjgm/serverless/commit/e5c088fe2e2de99e0da464abb36c785741b5b085))
* **Console:** Support login with Console ([4ce1088](https://github.com/pjgm/serverless/commit/4ce10883b5aca692a534be8114733fafc5c02a0e))
* **Console:** Unify headers resolution ([494fb26](https://github.com/pjgm/serverless/commit/494fb2662f910449eb0b7ad3f6caeb1c77486501))
* **Console:** Upgrade `@serverless/aws-lambda-otel-extension` ([5327b70](https://github.com/pjgm/serverless/commit/5327b702f755b13283562337c18051d87805916f))
* **Console:** Upgrade to rely on v0.2 version of extension ([3ccfec1](https://github.com/pjgm/serverless/commit/3ccfec1abdace3abb3e7484d51feb532ad37dda0))
* Construct user errors with ServerlessError ([c563581](https://github.com/pjgm/serverless/commit/c563581ac98764edf653c1a5337d1b7d2b61ea63))
* Convert statusCode to code error parameter ([f6c5179](https://github.com/pjgm/serverless/commit/f6c51796f886573679d3500b2007a314c8e4bd4d))
* Convert to async functions ([#11851](https://github.com/pjgm/serverless/issues/11851)) ([77c91f2](https://github.com/pjgm/serverless/commit/77c91f27d6f3234853550febfb7f14a32a69cc60))
* Convert to async/await ([5a5bb60](https://github.com/pjgm/serverless/commit/5a5bb60e9f8b40946bcf7cd43bec68847037074c))
* Convert to async/await upload and rollback functions ([#9866](https://github.com/pjgm/serverless/issues/9866)) ([0682ba8](https://github.com/pjgm/serverless/commit/0682ba8b6a70d27e74c478d6e5fa5de71b9e0070))
* Convert to native Promise and async/await ([#8593](https://github.com/pjgm/serverless/issues/8593)) ([84d423d](https://github.com/pjgm/serverless/commit/84d423d3be9d89475a22f29f808d506fb4f56d3c))
* corrected spelling errors ([#7218](https://github.com/pjgm/serverless/issues/7218)) ([526b21b](https://github.com/pjgm/serverless/commit/526b21b99425131e00930e6dfc5f8222c17291f3))
* Custom execution role getter ([#8824](https://github.com/pjgm/serverless/issues/8824)) ([12805c3](https://github.com/pjgm/serverless/commit/12805c3d152d85af9dba3dd3ecfa2002a621f6a8))
* **Dashboard:** Provide direct internal access to dashboard plugin ([6292197](https://github.com/pjgm/serverless/commit/6292197ee1dfbe107c3fe98059bd683896678b05))
* **deploy:** Make resource ids camel case to make them easier to read ([6e14a45](https://github.com/pjgm/serverless/commit/6e14a457c2bcb46ca08941af23626c8a4ef7fe1e))
* Deprecate not maintained Node.js versions ([a1f2fdb](https://github.com/pjgm/serverless/commit/a1f2fdb5cf077a51d7427dd7fc803d6f60dd5cc9))
* Do not recognize YAML Exception as user error ([db16df2](https://github.com/pjgm/serverless/commit/db16df2faad9cc63eb8e98ce90829642707546fb))
* Do not rely on serverless.yamlParser ([aa8f7be](https://github.com/pjgm/serverless/commit/aa8f7bec1caed4211adcb87ad0a73cd796f065d5))
* Document need of refactor ([e791e04](https://github.com/pjgm/serverless/commit/e791e046e231a6d49c7cfb32cdeed0cad241fa41))
* Drop old variables engine related deprecation ([5b54ed2](https://github.com/pjgm/serverless/commit/5b54ed2e2685c24439c0f835b50a024dbf9d39a9))
* Drop sentry reporting as it's not used ([e1092af](https://github.com/pjgm/serverless/commit/e1092aff44cc839896c63908f3803f874df63fe8))
* Enable triage process to run `@serverless/compose` ([#10950](https://github.com/pjgm/serverless/issues/10950)) ([401c721](https://github.com/pjgm/serverless/commit/401c721f8e1c59441ba3e5bb44bb2ce34576d99d))
* Ensure alphabetical order ([c95b8d3](https://github.com/pjgm/serverless/commit/c95b8d3594d38932bb9d2b02f7cb6d4f74b57d4a))
* Ensure async function format ([e88d0c5](https://github.com/pjgm/serverless/commit/e88d0c5f0e54630a99eeb74b0e9fe0c3bd58608f))
* Ensure codes for user errors ([6adaa9f](https://github.com/pjgm/serverless/commit/6adaa9f56ed6e9708065767be602f484d0091679))
* Ensure config modifications happen after its validation ([214768b](https://github.com/pjgm/serverless/commit/214768b83ab14495be75ac87f221a31ffd60c88b))
* Ensure constient returns ([d5833f8](https://github.com/pjgm/serverless/commit/d5833f8380b83a0d1d00504099fd2b481136481a))
* Ensure no side effects from config properties ([66f2898](https://github.com/pjgm/serverless/commit/66f289836de20e4c47e9adaaa5f2be9170a409d9))
* Ensure support for `warn` mode for modern deprecations ([82303b3](https://github.com/pjgm/serverless/commit/82303b38942b35fa6cb8ad3f19f2d528a1736587))
* Ensure that `options` are copied in Serverless constructor ([fd97e87](https://github.com/pjgm/serverless/commit/fd97e877cec6397cccf0e2bb2d1bfb5d71bdd798))
* Ensure to pass "isConfigurationResolved" to local instance ([10e1dda](https://github.com/pjgm/serverless/commit/10e1dda23b47cf439624c4602adce41a5c73fa51))
* Ensure to propagate as is stack monitoring error ([a46abe3](https://github.com/pjgm/serverless/commit/a46abe3d56cd667ad436fbceb283dd9e0f747d7b))
* Ensure to remove internal `.env` resolution with next major ([9b83072](https://github.com/pjgm/serverless/commit/9b830728df626683234c548df2e30d72a40d0e8d))
* Ensure to return promise from async function ([5e448e7](https://github.com/pjgm/serverless/commit/5e448e7d1d3cb9c767edeb1da1c98640ded5b849))
* Ensure to use `legacy.log` instead of `cli.log` ([ea05d7c](https://github.com/pjgm/serverless/commit/ea05d7c41e84b0f68017804b06d6435062673d26))
* Expose `isDashboardEnabled` resolver ([ba34c57](https://github.com/pjgm/serverless/commit/ba34c573f4d471bd724fe1a8e77c62e10d7c29c3))
* Expose isStandalone for metrics ([0ad5cd7](https://github.com/pjgm/serverless/commit/0ad5cd7a6333e96b0a041e688bb5eb0a26b98c30))
* Expose serverless.onExitPromise for internal processing ([0ab1283](https://github.com/pjgm/serverless/commit/0ab12832182ab1b34f70d3a5f17d012a4f61b10a)), closes [#8146](https://github.com/pjgm/serverless/issues/8146)
* extract getPluginsList and getExamplesList functions ([832895f](https://github.com/pjgm/serverless/commit/832895f537a27095981ff031647d28d7a4406133))
* extract getReadmeTable function to dedup common code ([c64cf66](https://github.com/pjgm/serverless/commit/c64cf66f1606ef3504c1cc515355d937321d7194))
* extract getTableRow common function ([7cf13aa](https://github.com/pjgm/serverless/commit/7cf13aa464da9299f4b493a0c5d698333ad8a3ef))
* Fix inline comment typo ([#10245](https://github.com/pjgm/serverless/issues/10245)) ([eca599d](https://github.com/pjgm/serverless/commit/eca599d0be3d74650871edde3c3feec63da578d9))
* Fix typo in `lib/classes/Variables.js` ([#10093](https://github.com/pjgm/serverless/issues/10093)) ([49f0913](https://github.com/pjgm/serverless/commit/49f0913466110ac32d89c7c044fc781e524b9ed9))
* Fix typo in `plugin-uninstall` ([17b057a](https://github.com/pjgm/serverless/commit/17b057a04c5b613a6f80601895521667374da090))
* Generalize config object validation ([521d9fe](https://github.com/pjgm/serverless/commit/521d9fe42e84757ec304252767325da81f6f614f))
* Generalize S3 upload dirname handling ([9223b79](https://github.com/pjgm/serverless/commit/9223b793161d3cb8e6075abb1254f1d707adb8ee))
* getStage returns dev as default. ([e694cd1](https://github.com/pjgm/serverless/commit/e694cd1abfa86b309999ffc10c86448f71c07532))
* Gurantee to resolve with promise ([06cf6ab](https://github.com/pjgm/serverless/commit/06cf6ab257431c4055c53c4d9be12745386ea8ed))
* Handle `@serverless/compose` install in non-interactive ([75885cb](https://github.com/pjgm/serverless/commit/75885cbbc5165aa4f27be4aab179e9e2655c1d99))
* Ignore `doctor` in Compose triage ([ef2dcb6](https://github.com/pjgm/serverless/commit/ef2dcb6df7cf5dd4b82a74613d02f22f04b7147a))
* Improve `dev` command ([#11827](https://github.com/pjgm/serverless/issues/11827)) ([2a34b04](https://github.com/pjgm/serverless/commit/2a34b04aae9309eaa23664b26da0a21e491beecc))
* Improve AWS request debug logging ([f9bf818](https://github.com/pjgm/serverless/commit/f9bf81839bb8a7afa909e581143508a78a904989))
* Improve AWS SDK errors reporting ([89b813d](https://github.com/pjgm/serverless/commit/89b813da51cedf80ca66ae4b4ad269edf8614ec0))
* Improve CLI notification border ([027d07c](https://github.com/pjgm/serverless/commit/027d07cdf1aaf27f2a8cff7495b99c982b9c54c0))
* Improve dependencies handling ([e3c64a3](https://github.com/pjgm/serverless/commit/e3c64a3f36d72753b6dea5aa951c60f44251a071))
* Improve deprecation message ([8592bdb](https://github.com/pjgm/serverless/commit/8592bdb1b2ecdbf4dd24700613cc664cbf3ec611))
* Improve error handling scope ([49aabdf](https://github.com/pjgm/serverless/commit/49aabdf13d2ee74380ec2d21f57ffde494a9bf9d))
* Improve generation of EventSourceMapping resource ([89f2368](https://github.com/pjgm/serverless/commit/89f2368450854384b38109cdd7190ffadb54bdff))
* Improve granularity of stack deployment error codes ([a6f4dc3](https://github.com/pjgm/serverless/commit/a6f4dc3b2be2aa9ba2255d57cf9a9d23eae02994))
* Improve module name ([ac1e0db](https://github.com/pjgm/serverless/commit/ac1e0dbfa1f507e1bcdc30163e238bd412274a5d))
* Improve reasoning comment ([7e640a9](https://github.com/pjgm/serverless/commit/7e640a960da1c796bfe503a311443206e720d470))
* Improve setting readability ([e648fea](https://github.com/pjgm/serverless/commit/e648fea9508ccb3fbe77ef087c254d967137f3f1))
* Improve var name ([2d3bfac](https://github.com/pjgm/serverless/commit/2d3bfac374fa6a4a9771c222a5daf05bfe4f08a9))
* Improve var name ([5377368](https://github.com/pjgm/serverless/commit/53773688ab79da4f186cc26162b1bb9814e85bbe))
* Improve var name ([c8c08c4](https://github.com/pjgm/serverless/commit/c8c08c4709663ef14a8a42ccabc9b6d9006d1f3e))
* Improve var naming ([2f7e698](https://github.com/pjgm/serverless/commit/2f7e698e4d312704041c764a4a4ed01caf3dae40))
* Improve var naming ([46c58bf](https://github.com/pjgm/serverless/commit/46c58bfdd2f753265d683b234e15913b61c0e646))
* Improve var naming ([6602013](https://github.com/pjgm/serverless/commit/660201310e68061ccd0bf802b715a4355a56bb77))
* Improve var naming ([8f3481e](https://github.com/pjgm/serverless/commit/8f3481e42a8224cb839c2f1f8ecd81df8aeb1b97))
* Improve var naming ([7136850](https://github.com/pjgm/serverless/commit/71368507e4df5b5582bafb3db9dc8a2e89a8ed8a))
* Improve var naming ([dde9b85](https://github.com/pjgm/serverless/commit/dde9b85965ec37d6574f33b1127d20a7502aa987))
* Improve var naming ([17e5bf7](https://github.com/pjgm/serverless/commit/17e5bf771d86b2f8a40a95b58875f6e060759115))
* Improve variable name ([0c5898b](https://github.com/pjgm/serverless/commit/0c5898bb018932b00a6d1985d80aa9ba0562f958))
* Improve warning message ([2198799](https://github.com/pjgm/serverless/commit/2198799f73e9fdbbdc377c8effcea8f1a933eff7))
* Increase stats request timeout ([9223f30](https://github.com/pjgm/serverless/commit/9223f305f02657de0d37271e39968e8f0d267b78))
* inline underscore-starting private methods since it is linted as error. ([fad655e](https://github.com/pjgm/serverless/commit/fad655eb912fe26476942e5019f28cf712834648))
* Introduce `get-create-stack-params` util ([adb0824](https://github.com/pjgm/serverless/commit/adb08240ecabe44ddde1b3bea4c1eb5e5388c817))
* Introduce `get-shared-stack-action-params` util ([0c89939](https://github.com/pjgm/serverless/commit/0c8993933452527e9257b222d4221783e274e975))
* Introduce `get-update-stack-params` util ([a7db2b9](https://github.com/pjgm/serverless/commit/a7db2b941f3faa9ce8116735448eb6f9d0c04b06))
* Introduce `is-using-local-installation` util ([11e7311](https://github.com/pjgm/serverless/commit/11e7311032824d357888ef615596c40ec1bbf66c))
* Introduce `serviceDir` and `configurationFilename` ([fc3a439](https://github.com/pjgm/serverless/commit/fc3a4391b5411f77a51a84f93a166903c51cb80f))
* Introduce hooks tracking debug logs ([efe1139](https://github.com/pjgm/serverless/commit/efe11396be5c9f34a92b60b5c4217201e2f55a54))
* Isolate `import` invocations ([fe62096](https://github.com/pjgm/serverless/commit/fe620965838b2fce2a0aa3f9c8aaaf47e4faf755))
* Log environment details of error to stderr ([f439201](https://github.com/pjgm/serverless/commit/f439201d7f884ab1994f7691c35abe50d72bf49e))
* Make deprecations default mode internally modifyable ([07a69a8](https://github.com/pjgm/serverless/commit/07a69a836c506e3ab8ab976ef27d4f3b672722f7))
* Mark `saveServiceState` internal function as async ([4f895a2](https://github.com/pjgm/serverless/commit/4f895a2e36f56eb65161af706c0c6f4f2d9a4655))
* Mark deprected lifecycle events for removal ([be16ed5](https://github.com/pjgm/serverless/commit/be16ed57b1bd95c56b65ea45553113360cfbbc70))
* Mark functions `async` in `plugins/aws/remove` ([#9284](https://github.com/pjgm/serverless/issues/9284)) ([0bdb7d8](https://github.com/pjgm/serverless/commit/0bdb7d858c238ffca3c1b1113cbb6af8c39a62e9))
* Mark functions async in `aws/customResources` and `aws/deploy` ([c45f661](https://github.com/pjgm/serverless/commit/c45f66117892e6f5948274288d7dda41f96dfe85))
* Mark intention of improving state file ([98e6107](https://github.com/pjgm/serverless/commit/98e610787c015c59a5f0d62f0339808dcbe443a1))
* **methods:** Request parameters ([3f96c0d](https://github.com/pjgm/serverless/commit/3f96c0d7708440b2c67b2ef3fc01393cf7d5c403))
* Move `isLocalyInstalled` util to CLI context ([fdf25aa](https://github.com/pjgm/serverless/commit/fdf25aab448ec4418beaf2f7701ee9c76c37eca2))
* Move areAnalyticsDisabled to analytics/areDisabled ([38c493f](https://github.com/pjgm/serverless/commit/38c493f1975fb67949d798e2e215dce67f069236))
* Move cachedFilePath resolution into memoized function ([10d0078](https://github.com/pjgm/serverless/commit/10d0078d1921bc5ae6edd65934786a503a356000))
* Move internal configuration resolution to init method ([20e2c00](https://github.com/pjgm/serverless/commit/20e2c00e1d1ef383598b78403ec19b59f42718a7))
* move service validations to Service#validate ([e6599f3](https://github.com/pjgm/serverless/commit/e6599f3953164a6729a6e345c89ed739823182a8))
* Move variables resolution log to debug level ([b0d854a](https://github.com/pjgm/serverless/commit/b0d854af20d46ef9e07e5d4bce26b88e84f4c4f1))
* Nest analytics utils in folder ([7cd44bb](https://github.com/pjgm/serverless/commit/7cd44bbe057a6553a510f5123733609c03eaa53a))
* Normalize module path ([d0beed4](https://github.com/pjgm/serverless/commit/d0beed413e4c6b8eb0be31542e603ac3e2e922c7))
* Normalize module path ([0f214d8](https://github.com/pjgm/serverless/commit/0f214d8aed9502eba9a3b6034f6840048ec6cc39))
* Normalize module path ([1857348](https://github.com/pjgm/serverless/commit/18573483f12de7d0f2e2f802e0f6c14868e85e2e))
* Normalize module path ([04f73ff](https://github.com/pjgm/serverless/commit/04f73ff0d681644d4d5476e7e30b1a8cfc2c2a97))
* Normalize module path ([73239c9](https://github.com/pjgm/serverless/commit/73239c9eda8d28cadd3ae87224fea0808614c943))
* Normalize module path ([1574081](https://github.com/pjgm/serverless/commit/15740814011c8f17e0ef9bcc8a5e5aba713a3738))
* Normalize module path ([bc47fe9](https://github.com/pjgm/serverless/commit/bc47fe98bda574e72264584b9153780b1a2d934f))
* Normalize module path ([ba97cdd](https://github.com/pjgm/serverless/commit/ba97cdd60dd4ad49d0242cfcb106a52947c5f1e5))
* Normalize module path ([1f36b05](https://github.com/pjgm/serverless/commit/1f36b05331f2105fb15488ac0b7f455bdee0e052))
* Normalize module path ([3c7a921](https://github.com/pjgm/serverless/commit/3c7a921a7ead7d230aaf84a92d117012ce4f5e3b))
* Normalize module path ([7fc04d1](https://github.com/pjgm/serverless/commit/7fc04d123bafb627d290a49b9f13eedb9803df62))
* Normalize module path ([a6ce212](https://github.com/pjgm/serverless/commit/a6ce212f3d93dbb58236b17dd4052098b57efe3e))
* Normalize module path ([93114b5](https://github.com/pjgm/serverless/commit/93114b58a97315854d1114b548201bc8d8447aa8))
* Normalize module path ([36da698](https://github.com/pjgm/serverless/commit/36da69866ac06608c9274b84e26edb196659fb51))
* Normalize module path ([0f30564](https://github.com/pjgm/serverless/commit/0f30564451208c6916fdc88e1df371e462edc7b9))
* Normalize module path ([01d8960](https://github.com/pjgm/serverless/commit/01d89600742b77e35d70f058223e90fe35d942a6))
* Normalize module path ([78648e0](https://github.com/pjgm/serverless/commit/78648e0df1ae6554f7635ca4fcc5d1fbdc2c4e5e))
* Normalize module path ([c929de0](https://github.com/pjgm/serverless/commit/c929de083367feea9b19fe2ac9b38dfce50eca8f))
* Normalize module path ([fdcf60f](https://github.com/pjgm/serverless/commit/fdcf60f6b84c31a9a8042a9d51f3f8e4edf52351))
* Normalize module path ([657bdea](https://github.com/pjgm/serverless/commit/657bdea4bd152dafec8fc27606007a6af437156c))
* Normalize module path ([78cdf21](https://github.com/pjgm/serverless/commit/78cdf217b3c2b8f3eaf6c8a3ced89a6ff7247cc6))
* Normalize module path ([a38ed39](https://github.com/pjgm/serverless/commit/a38ed390666cb728bacd285517a7e6560a4ad7f7))
* Normalize module path ([b8798fc](https://github.com/pjgm/serverless/commit/b8798fc542aa69dca890e6784581613f20a60a81))
* Normalize module path ([4996e58](https://github.com/pjgm/serverless/commit/4996e5869661fae598cefcb64dd008d7948db2ca))
* Normalize module path ([c27f39e](https://github.com/pjgm/serverless/commit/c27f39e00783ee03c3f833e84d97781f2483adad))
* Normalize module path ([95a591e](https://github.com/pjgm/serverless/commit/95a591e166e2e5d03cb1edb6d0f69f1f7f2b541d))
* Normalize module path ([f0a726e](https://github.com/pjgm/serverless/commit/f0a726ee5f83a05d80bcbc1586a16ab6c2d8c5b3))
* Normalize module path ([38ee5ee](https://github.com/pjgm/serverless/commit/38ee5eee50fea4bdc0f1e8baf14bfae8419eae9c))
* Normalize module path ([5d584a1](https://github.com/pjgm/serverless/commit/5d584a1cddd2ffcb4af6a2009391547e434d910c))
* Normalize module path ([b074e35](https://github.com/pjgm/serverless/commit/b074e355fca424949484e4811a6be840a4f6c5a2))
* Normalize module path ([2b192c0](https://github.com/pjgm/serverless/commit/2b192c0e0a986024a778b6f090788dc628aef18b))
* Normalize module path ([c16dea3](https://github.com/pjgm/serverless/commit/c16dea3046459af3af858209fdd185a1016cc338))
* Normalize module path ([73c8e6d](https://github.com/pjgm/serverless/commit/73c8e6def53b59bf173b4dfeed6401e8128e6e1c))
* Normalize module path ([f64b4b2](https://github.com/pjgm/serverless/commit/f64b4b25ca799154f69925d35c6d14f3ac2e7e1f))
* Normalize module path ([235989f](https://github.com/pjgm/serverless/commit/235989fb672bdb18a2e5c9ef8e8543633b33c33e))
* Normalize module path ([6f1c977](https://github.com/pjgm/serverless/commit/6f1c97709050e4bbd51a0e14d00990e68eed69e0))
* Normalize module path ([fe75e86](https://github.com/pjgm/serverless/commit/fe75e8622c6947a533b652e498b5652c16c024f2))
* Normalize module path ([f81b128](https://github.com/pjgm/serverless/commit/f81b12824d4ae19ba9181aa2e611de9756c830cb))
* Normalize module path ([ab90afa](https://github.com/pjgm/serverless/commit/ab90afa72d0d6fb26fec69980a0ca93b750da1f5))
* Normalize module path ([8d798e3](https://github.com/pjgm/serverless/commit/8d798e3427c6c22abdd9ae8614b5cf43990c2b24))
* **Packaging:** Convert to async/await ([9380c70](https://github.com/pjgm/serverless/commit/9380c702c94dddad7810b31b9ba4279dd400a639))
* **Packaging:** Refactor to async/await ([7fc7e78](https://github.com/pjgm/serverless/commit/7fc7e78e7fc0633d764c9764ee7af49ddb44bb6e))
* **Packaging:** Refactor to async/await ([b43cf22](https://github.com/pjgm/serverless/commit/b43cf22608b4d7f2022b333024b38e2a450539c1))
* **Packaging:** Warn on inffective `functions[].package` config ([88099ad](https://github.com/pjgm/serverless/commit/88099ad98c33ed97b1cf0471de03247c33928af0)), closes [#11974](https://github.com/pjgm/serverless/issues/11974)
* Pass `__isInvokedByGlobalInstallation` with constructor config ([31f73ce](https://github.com/pjgm/serverless/commit/31f73cead3e9973bca7800e27e53717eb206b710))
* Patch handling of `isInvokedByGlobalInstallation` flag ([21c9f26](https://github.com/pjgm/serverless/commit/21c9f26ea64a7dfc06a96c173c8268d8ad835870))
* **Plugins:** Bulletproof way to recognize external plugins ([1618e23](https://github.com/pjgm/serverless/commit/1618e23c5cac32ee1168c951e5e70a8dfc66c2f9))
* **Plugins:** Expose eventual npm install error ([cd9b823](https://github.com/pjgm/serverless/commit/cd9b8233f9b484060083d79f216d6c51d1cc2907))
* **Plugins:** Fix manual update notice ([0d5884e](https://github.com/pjgm/serverless/commit/0d5884ebbf015332c08cedea7a4359d66c3a2761))
* **Plugins:** Improve error messaging on failed npm install ([6f88c11](https://github.com/pjgm/serverless/commit/6f88c11312c67b628c398105af0ea466642731e7))
* **Plugins:** Seclude `plugin install` standalone command ([#9942](https://github.com/pjgm/serverless/issues/9942)) ([713ac1e](https://github.com/pjgm/serverless/commit/713ac1e2a111426fb501b5fa29588a53efcba9bc))
* **Plugins:** Seclude `plugin uninstall` standalone command ([26ce1c6](https://github.com/pjgm/serverless/commit/26ce1c636be7754584cf47a87f1b92d3b7d98122)), closes [#10015](https://github.com/pjgm/serverless/issues/10015)
* Prefix private property with "_" ([77c7d55](https://github.com/pjgm/serverless/commit/77c7d55f6260118e3541c8c7e45a3282e5c6dfa3))
* Prevent is local detection on locally installed ([7accad6](https://github.com/pjgm/serverless/commit/7accad6eb9ad1d9549c2e0e5c55e11b3f827af6a))
* **Print:** Improve variables handling ([ee3b519](https://github.com/pjgm/serverless/commit/ee3b5194250ae4936dbe77a8079f9a68479e0ad1))
* **Print:** Read provider values from provider ([b53716a](https://github.com/pjgm/serverless/commit/b53716a64c9dacb411690b8b8496adfc8c194ca1))
* Provide room for more SDK requests when gathering stack info ([69afca5](https://github.com/pjgm/serverless/commit/69afca5a02860f63d0d2429ce8c5988c8b698d6b))
* Recognize `logout` as service-aware command ([21c783d](https://github.com/pjgm/serverless/commit/21c783dc16dfd00385c907729a67a2fcccda4498))
* Reconfigure onExitPromise setup ([22a03ce](https://github.com/pjgm/serverless/commit/22a03ce0d7b1581747b121f862d0818f04120958))
* Refactor `aws` provider tests for prefixes ([#9301](https://github.com/pjgm/serverless/issues/9301)) ([196776c](https://github.com/pjgm/serverless/commit/196776c65e3295e3e6e7bf341e000b8ea7ee76b5))
* Refactor `isNpmPackageWritable` to not depend on `serverless` ([b915cc4](https://github.com/pjgm/serverless/commit/b915cc467183d146785466965abbe318c349f0c9))
* Refactor `pluginManager.invoke` to async/await ([15b5a11](https://github.com/pjgm/serverless/commit/15b5a11ecd7cf4b83442ca0df161d74c9bdbc8e2))
* Refactor `pluginManager.spawn` to async/await ([87b8d01](https://github.com/pjgm/serverless/commit/87b8d019c200caebbd0047e15b2e1e9f1faa988f))
* Refactor direct use of `@serverless/utils/log` ([05fb97f](https://github.com/pjgm/serverless/commit/05fb97fdab0c0ddc471ca554e48e09e661f797db))
* Refactor init part to async/await ([763fc34](https://github.com/pjgm/serverless/commit/763fc342f7d82a86db00cbccab2f847d943d3e9e))
* Refactor provider-related tests in compile/functions ([#8623](https://github.com/pjgm/serverless/issues/8623)) ([07d9602](https://github.com/pjgm/serverless/commit/07d9602cd0a2a597a3aa56982cf64d8135b58ee6))
* Refactor Serverless.run to async ([30015ea](https://github.com/pjgm/serverless/commit/30015eafd2fb9d2e82d8f34ee8f10c1fb4e536a0))
* Refactor some functions to native promises ([#8533](https://github.com/pjgm/serverless/issues/8533)) ([06f6c6d](https://github.com/pjgm/serverless/commit/06f6c6d28ee54055ae4a39686ce54e4738d9e8b0))
* Refactor to async functions ([#11809](https://github.com/pjgm/serverless/issues/11809)) ([6426589](https://github.com/pjgm/serverless/commit/6426589e1dcfa4d287a4244091d717d450781d24))
* Refactor to async/await ([ee3dd0a](https://github.com/pjgm/serverless/commit/ee3dd0a6bc6d3f483288cd35420edf1e64012b54))
* Refactor to async/await ([97d544b](https://github.com/pjgm/serverless/commit/97d544be82e12c483d662dec564d860b31cf38c6))
* Refactor to async/await ([0b4b4bb](https://github.com/pjgm/serverless/commit/0b4b4bbc354b841812b77f99758f41eaaccd7895))
* Refactor to async/await ([76ab2ff](https://github.com/pjgm/serverless/commit/76ab2ffbe22472d76b95851330759926c0ab6a68))
* Refactor to async/await ([3df81be](https://github.com/pjgm/serverless/commit/3df81be0cf1d76d60d6d303ab455bfad2d38fc1d))
* Refactor to async/await ([8173a36](https://github.com/pjgm/serverless/commit/8173a36b7c1f96dc3bf670dde27126ba5199f4f6))
* Refactor to async/await ([4431b43](https://github.com/pjgm/serverless/commit/4431b43f17299624462f4d98500674560a9ffe62))
* Refactor to async/await ([18bcc9f](https://github.com/pjgm/serverless/commit/18bcc9f7406e4f1e8bbf8615c9df3458a983710d))
* Refactor to async/await ([861686b](https://github.com/pjgm/serverless/commit/861686bbea5fa97dbffda51a8dc52318a2fb6231))
* Rely on 'essentials' package for process initialization ([acf8a9d](https://github.com/pjgm/serverless/commit/acf8a9d7cb961bda65492cfa6cb42e0e78059e23))
* Rely on `require.resolve` to detect wether module exist ([870a116](https://github.com/pjgm/serverless/commit/870a116bb1e800f5bf64dc53af3b43047c0336c7))
* Rely on external isHelpRequest CLI util ([dc9f180](https://github.com/pjgm/serverless/commit/dc9f1809d1ec6830a6682e7946cb4dfc1c898c72))
* Rely on internal CLI args parser ([4c7e59b](https://github.com/pjgm/serverless/commit/4c7e59bf09773670018941cda4478a925d8581a2))
* Remove _async_ handling from _sync_ function ([5f1a916](https://github.com/pjgm/serverless/commit/5f1a916d4d9c8833755833bc064f51e4f89e50e0))
* Remove "async" mark from sync function ([5ca4b63](https://github.com/pjgm/serverless/commit/5ca4b639fb57766938488a295180f0bf1cd644ae))
* Remove `_.isBoolean` usage ([#7880](https://github.com/pjgm/serverless/issues/7880)) ([57f70f9](https://github.com/pjgm/serverless/commit/57f70f93eb3c24b802c842fb6e395591a70a3270))
* Remove `_.isInteger` ([#7878](https://github.com/pjgm/serverless/issues/7878)) ([3b19a5a](https://github.com/pjgm/serverless/commit/3b19a5a6b191fdb0dac5a81d1244159e0da9e0bd))
* Remove `BbPromise.bind` usage ([#11875](https://github.com/pjgm/serverless/issues/11875)) ([30dd50a](https://github.com/pjgm/serverless/commit/30dd50a90cf5ae32ae87b85aae31c2d29cf464d5))
* Remove `bluebird` from `lib/classes` ([#8943](https://github.com/pjgm/serverless/issues/8943)) ([1a694ae](https://github.com/pjgm/serverless/commit/1a694ae4aab0a347b018380110b9a436f6c43c1e))
* Remove `bluebird` from `lib/plugins/aws` ([#9054](https://github.com/pjgm/serverless/issues/9054)) ([b11171c](https://github.com/pjgm/serverless/commit/b11171c70c8f5597e2644f7ea8ec82a17a9eee29))
* Remove `bluebird` from `lib/plugins/create` ([#8996](https://github.com/pjgm/serverless/issues/8996)) ([258543a](https://github.com/pjgm/serverless/commit/258543ab6e1874ba41be3563346cd7b50993ac58))
* Remove `bluebird` from `lib/plugins/interactiveCli` ([#9029](https://github.com/pjgm/serverless/issues/9029)) ([7c0ceb5](https://github.com/pjgm/serverless/commit/7c0ceb5c4a1171666e381ef9a00c6f133569732b))
* Remove `bluebird` from `lib/plugins/package` ([#9028](https://github.com/pjgm/serverless/issues/9028)) ([0fb0f43](https://github.com/pjgm/serverless/commit/0fb0f43919bd3bd4a9c57b9f33bf96a822ce027c))
* Remove `bluebird` from `lib/plugins/plugin` ([#8984](https://github.com/pjgm/serverless/issues/8984)) ([9e79602](https://github.com/pjgm/serverless/commit/9e7960297227b39f05c2619a80e3cac7cb7be1a5))
* Remove `bluebird` from `lib/utils` ([#8972](https://github.com/pjgm/serverless/issues/8972)) ([820cc1f](https://github.com/pjgm/serverless/commit/820cc1f581bfd502e5452f5c9935301ec86f9d14))
* Remove `bluebird` from top-level `lib/plugins` ([#8973](https://github.com/pjgm/serverless/issues/8973)) ([8fead7f](https://github.com/pjgm/serverless/commit/8fead7f39e3a5649e87a4ceb6e0c0a28e7f61ea5))
* Remove `got` dependency ([#12040](https://github.com/pjgm/serverless/issues/12040)) ([1775c90](https://github.com/pjgm/serverless/commit/1775c90a72ec321af8673bcdd1901cb1e48b9169))
* Remove `legacy` logs ([1cb6a2f](https://github.com/pjgm/serverless/commit/1cb6a2ff2d992239b54b1c298edea353a0b16882))
* Remove `lib/classes/Error.js` ([b587edf](https://github.com/pjgm/serverless/commit/b587edfc6f6beb4f03b3e9de7d50dc0a004e80c0))
* Remove `that = this` pattern ([#8463](https://github.com/pjgm/serverless/issues/8463)) ([4ae192c](https://github.com/pjgm/serverless/commit/4ae192cbfeb534d09af5b29ef7a1ed3f7700332f))
* Remove config.update usage ([7fb55b6](https://github.com/pjgm/serverless/commit/7fb55b64ddd1bd727e48c2baf49f312fb12d03ab))
* Remove evaluation of deprecated lifecycle events ([2746b85](https://github.com/pjgm/serverless/commit/2746b854bbe78444fe0d5fe491646f3a57f7af8d))
* Remove inaccurate comment ([3c9b818](https://github.com/pjgm/serverless/commit/3c9b8189f22a91e2cb1bc137abdcf031a78e9565))
* Remove ineffective ESLint instruction ([81dc349](https://github.com/pjgm/serverless/commit/81dc34961bb2135e6f1664eb4e7b2f8996b443fd))
* Remove injustified "eslint-disable" comments ([2011649](https://github.com/pjgm/serverless/commit/20116495372ff5de837d005868cdd2a3d74e1415))
* Remove internal `suppressLogIfPrintCommand` method ([e61124a](https://github.com/pjgm/serverless/commit/e61124a7d4509bad6f8dd285807f18a6fd4f1f83))
* Remove internal logStat reporter ([a83f06e](https://github.com/pjgm/serverless/commit/a83f06e07fb40cdb84201dd8e9b789c92b0ee78b))
* Remove irrelevant fs modules ([c1907a2](https://github.com/pjgm/serverless/commit/c1907a2dde7531dab8bff665434ee8a72397c2ca))
* Remove left over internal `self:` handling ([#11279](https://github.com/pjgm/serverless/issues/11279)) ([544717e](https://github.com/pjgm/serverless/commit/544717e703c093340b73dcbf94dc40555cda5251))
* Remove no longer applicable comments ([f009679](https://github.com/pjgm/serverless/commit/f009679bdd39cc94fe42cac850a617ab50bc748a))
* Remove no longer applicable setting ([dd5b8f6](https://github.com/pjgm/serverless/commit/dd5b8f61de487d67f0cc15036be754816f7fa234))
* Remove no longger needed deprecation logs supression ([af89ab8](https://github.com/pjgm/serverless/commit/af89ab8994aaaa12e578b2bad72ddc8a948e765c)), closes [#2328](https://github.com/pjgm/serverless/issues/2328)
* Remove not actual TODO comments ([cc905c1](https://github.com/pjgm/serverless/commit/cc905c1e39f36526d570f6df9a73b567e494888a))
* Remove obsolete 'null' assignment ([64814f4](https://github.com/pjgm/serverless/commit/64814f46f25c059d17181f40325f33065201954b))
* Remove obsolete `getLocalAccessKey` util ([6f9824a](https://github.com/pjgm/serverless/commit/6f9824abac780d4725d401c776d80ed658e31d04))
* Remove obsolete comment ([91aff1d](https://github.com/pjgm/serverless/commit/91aff1d1c201c9816b86e85480140fcd4ad9a2e2))
* Remove obsolete conditions ([85997e0](https://github.com/pjgm/serverless/commit/85997e063a24dd36113ae6ad53d042585adb9c03))
* Remove old analytics module ([5234439](https://github.com/pjgm/serverless/commit/5234439fa17b5643c3ec59b4cc13f3301a7095e9))
* Remove support for internal noDeploy option ([688d09b](https://github.com/pjgm/serverless/commit/688d09b1f7f28f8b1656d3f7f31c6c2765a01b9d))
* Remove unneeded `split` in `getHttp` ([#8939](https://github.com/pjgm/serverless/issues/8939)) ([7213d1d](https://github.com/pjgm/serverless/commit/7213d1d4f85c7d1583c0eba531e026d3f7a8e96c))
* Remove unused modules ([#8598](https://github.com/pjgm/serverless/issues/8598)) ([d102a39](https://github.com/pjgm/serverless/commit/d102a3984abfe5c014c4adafa8abf2ea8edfd336))
* Remove update-notifier notifications ([11fb888](https://github.com/pjgm/serverless/commit/11fb8889c8744180919eb3cfae85269a7ff3649f))
* Remove vague comment ([f8b50b7](https://github.com/pjgm/serverless/commit/f8b50b7079968b66f489ae853e80bcce4987c2c9))
* removed instances keyword and replaces this.S to this.serverless ([de86121](https://github.com/pjgm/serverless/commit/de86121170f8cf8c7286fb0537f5dfb17d38bba8))
* Rename `…/aws/package/compile/events/alb/lib/listenerRules.js` ([98e454e](https://github.com/pjgm/serverless/commit/98e454e317148f993358e6fa66facb02d55ac644))
* Rename `…/classes/config-schema-handler/normalizeAjvErrors.js` ([7dacfdf](https://github.com/pjgm/serverless/commit/7dacfdf9958d79eff49fa8a643e7ac03b452a5c2))
* Rename `…/classes/config-schema-handler/resolveAjvValidate.js` ([d0c93f9](https://github.com/pjgm/serverless/commit/d0c93f9d35be4a1e445f4440b2f32cb04f4ee59e))
* Rename `…/events/websockets/lib/pickWebsocketsTemplatePart.js` ([bff4cc7](https://github.com/pjgm/serverless/commit/bff4cc7b137d89149402898b0b0e68d4579ac87b))
* Rename `…/package/compile/events/api-gateway/lib/usagePlan.js` ([3ea8389](https://github.com/pjgm/serverless/commit/3ea83898b7c887afc8f46a1bf2f2f275b7219f7d))
* Rename `…/plugins/aws/package/compile/events/cloudWatchLog.js` ([6eddebe](https://github.com/pjgm/serverless/commit/6eddebe55d911bceb414b5ff10919a85d5918dc8))
* Rename `…b/plugins/aws/package/lib/addExportNameForOutputs.js` ([971c5d3](https://github.com/pjgm/serverless/commit/971c5d355bd97f35126794efaf0c9f2595b8202d))
* Rename `…compile/events/lib/ensureApiGatewayCloudWatchRole.js` ([f2a4f96](https://github.com/pjgm/serverless/commit/f2a4f96f362eaee081d466b3f282738b72ba74fa))
* Rename `…e/compile/events/api-gateway/lib/hack/updateStage.js` ([3f8b1a1](https://github.com/pjgm/serverless/commit/3f8b1a16bde1240bb1c2790b56aa6be60acc9daf))
* Rename `…e/compile/events/api-gateway/lib/requestValidator.js` ([897fdfc](https://github.com/pjgm/serverless/commit/897fdfc48e577987996a5f27a1d7c711bfb86f28))
* Rename `…esources/resources/cognito-user-pool/lib/userPool.js` ([8da0020](https://github.com/pjgm/serverless/commit/8da00202f26e1886de4c7204dc87e32675bcc2f3))
* Rename `…events/api-gateway/lib/hack/disassociateUsagePlan.js` ([93d1c29](https://github.com/pjgm/serverless/commit/93d1c290433d60ca0be21023a6c2ca2f409d8d1d))
* Rename `…gins/aws/package/lib/mergeCustomProviderResources.js` ([2e6c294](https://github.com/pjgm/serverless/commit/2e6c2941eae3dd438ed88e08945fb7a4046f193f))
* Rename `…ins/aws/package/lib/generateArtifactDirectoryName.js` ([ecd0d5d](https://github.com/pjgm/serverless/commit/ecd0d5da2ae6085358fbeb1c156bfa8ce33f95e6))
* Rename `…kage/compile/events/api-gateway/lib/usagePlanKeys.js` ([20b90cb](https://github.com/pjgm/serverless/commit/20b90cb2c64a141fccb393c6af3aad88b2e94778))
* Rename `…kage/compile/events/websockets/lib/routeResponses.js` ([bb70c63](https://github.com/pjgm/serverless/commit/bb70c636563d6d6ea2fae38d105376799351af78))
* Rename `…lugins/aws/customResources/resources/cognitoUserPool` ([227191f](https://github.com/pjgm/serverless/commit/227191f59b14cfa88d31f9f89fbb08ba7b2c11ae))
* Rename `…lugins/aws/package/compile/events/cloudWatchEvent.js` ([d200310](https://github.com/pjgm/serverless/commit/d2003106df6f3d79a3c5c6210e3ac68a958d6583))
* Rename `…lugins/aws/package/compile/events/cognitoUserPool.js` ([04f6318](https://github.com/pjgm/serverless/commit/04f63183d6acad1253588fcde1da64e63a5785f1))
* Rename `…lugins/aws/package/compile/events/s3/configSchema.js` ([72624b0](https://github.com/pjgm/serverless/commit/72624b0b164cd31c3efd4279dd5e7d873e1bd74d))
* Rename `…mResources/resources/event-bridge/lib/eventBridge.js` ([c6300fb](https://github.com/pjgm/serverless/commit/c6300fbc244362e815930192bd894fb6ecf0349e))
* Rename `…nts/api-gateway/lib/method/requestParameters.test.js` ([c150045](https://github.com/pjgm/serverless/commit/c15004519b51b6799e617150ad77c09258715122))
* Rename `…package/compile/events/msk/getMskClusterNameToken.js` ([6ee1a79](https://github.com/pjgm/serverless/commit/6ee1a79cfbac8af886d2aabf1cf4c605195bc894))
* Rename `…plugins/aws/package/compile/events/alexaSmartHome.js` ([c31133c](https://github.com/pjgm/serverless/commit/c31133c3f125f7c68c8e13c020ba03b06b7cc1ab))
* Rename `…s/aws/package/compile/events/alb/lib/targetGroups.js` ([0b542a1](https://github.com/pjgm/serverless/commit/0b542a125988e5d3d0f4c20d25fee14766d18a3c))
* Rename `…s/aws/package/compile/events/iotFleetProvisioning.js` ([ebe4035](https://github.com/pjgm/serverless/commit/ebe4035e759455934c4847eeb4d910f1c26e5b9d))
* Rename `…s/customResources/resources/apiGatewayCloudWatchRole` ([5cc98ca](https://github.com/pjgm/serverless/commit/5cc98ca67666d3e09cb0911a46dc22a5c9dcff0f))
* Rename `…s/package/compile/events/alb/lib/healthCheck.test.js` ([95e308d](https://github.com/pjgm/serverless/commit/95e308dc880908960b41b5fe4950762ca6feb04e))
* Rename `…s/package/lib/stripNullPropsFromTemplateResources.js` ([75879f8](https://github.com/pjgm/serverless/commit/75879f866f4be1e60df5e36f872cd031d71b2f19))
* Rename `…ws/package/compile/events/api-gateway/lib/apiKeys.js` ([44f48f5](https://github.com/pjgm/serverless/commit/44f48f52071e34c43066561b50ca2f9d2cad7219))
* Rename `…ws/package/compile/events/api-gateway/lib/restApi.js` ([04158ea](https://github.com/pjgm/serverless/commit/04158ea6791aa34fe4d3a7745becf13158ea2f46))
* Rename `lib/classes/CLI.js` ([4a97648](https://github.com/pjgm/serverless/commit/4a97648626c01a76fd2708da7e6accd59c31cb6b))
* Rename `lib/classes/config-schema-handler/regexpKeyword.js` ([8dbcc90](https://github.com/pjgm/serverless/commit/8dbcc90495a08a8cd234fc68be95415a89e2164b))
* Rename `lib/classes/Config.js` ([63961a5](https://github.com/pjgm/serverless/commit/63961a537fe2c069d4b894c507c376c359b98acc))
* Rename `lib/classes/ConfigSchemaHandler` ([7818457](https://github.com/pjgm/serverless/commit/78184571b69eaae25c273c9063aafb9150623ac3))
* Rename `lib/classes/PluginManager.js` ([4ffb3a7](https://github.com/pjgm/serverless/commit/4ffb3a7173eb89d01338b1f65c10aa7ebc22c8d7))
* Rename `lib/classes/Service.js` ([bd7dece](https://github.com/pjgm/serverless/commit/bd7dece8cee853379cab3ce76812abe35690da92))
* Rename `lib/classes/Utils.js` ([391acb1](https://github.com/pjgm/serverless/commit/391acb1a74bd6d01049819acbdc788e5535b8c79))
* Rename `lib/classes/YamlParser.js` ([6d67ec2](https://github.com/pjgm/serverless/commit/6d67ec2a0073e41f6bc4dc2fd438da5de7b3f15f))
* Rename `lib/configSchema.js` ([57642f7](https://github.com/pjgm/serverless/commit/57642f73ba628e2fd0d5990c270c7e733b92bdb1))
* Rename `lib/plugins/aws/common/lib/cleanupTempDir.js` ([a18199f](https://github.com/pjgm/serverless/commit/a18199f6c6e679d7205c4f0faddc9ecb82ccf5f9))
* Rename `lib/plugins/aws/configCredentials.js` ([9e2edc2](https://github.com/pjgm/serverless/commit/9e2edc2d9f538dae6666d3ba36dc282493876add))
* Rename `lib/plugins/aws/custom-resources/generateZip.js` ([6e129b2](https://github.com/pjgm/serverless/commit/6e129b28ceb9bc7264c78902dd61a12527767490))
* Rename `lib/plugins/aws/customResources/resources/eventBridge` ([a55a48f](https://github.com/pjgm/serverless/commit/a55a48fdec2c2b09fac93b02c2083f3779c10a0d))
* Rename `lib/plugins/aws/customResources` ([1f30396](https://github.com/pjgm/serverless/commit/1f3039673266a4bd88188ef4c8aa728c8cfeb6c8))
* Rename `lib/plugins/aws/deploy/lib/checkForChanges.js` ([892e50c](https://github.com/pjgm/serverless/commit/892e50cfaaa25eb4a1ff5ba661257577709e46eb))
* Rename `lib/plugins/aws/deploy/lib/cleanupS3Bucket.js` ([c3e42d6](https://github.com/pjgm/serverless/commit/c3e42d6c57f48c5d1cee553227283d0be14b377d))
* Rename `lib/plugins/aws/deploy/lib/createStack.js` ([48fbaed](https://github.com/pjgm/serverless/commit/48fbaedd1b5f947ff2b22b6ff065c4304b563fb9))
* Rename `lib/plugins/aws/deploy/lib/extendedValidate.js` ([ae7bfcf](https://github.com/pjgm/serverless/commit/ae7bfcfa3f1c12de012043026e76174f2b25e7af))
* Rename `lib/plugins/aws/deploy/lib/uploadArtifacts.js` ([9c8bca0](https://github.com/pjgm/serverless/commit/9c8bca0adf2bafdd7a7e41fd08c0ef4149e01f1e))
* Rename `lib/plugins/aws/deploy/lib/validateTemplate.js` ([d1b72eb](https://github.com/pjgm/serverless/commit/d1b72ebd197008205d4236ac9d79df7c95bef399))
* Rename `lib/plugins/aws/deployFunction.js` ([39fd2ae](https://github.com/pjgm/serverless/commit/39fd2aee15c11dec72173c53e14826f04f941e64))
* Rename `lib/plugins/aws/deployList.js` ([85acd60](https://github.com/pjgm/serverless/commit/85acd6036eeb1f3684470f835c8611e4190dc9ff))
* Rename `lib/plugins/aws/info/getApiKeyValues.js` ([a1239eb](https://github.com/pjgm/serverless/commit/a1239ebffe0101cb183312c5410aa08eb071bd58))
* Rename `lib/plugins/aws/info/getResourceCount.js` ([5596746](https://github.com/pjgm/serverless/commit/5596746455850977a26c4f150b63970b7e89a154))
* Rename `lib/plugins/aws/info/getStackInfo.js` ([390bea1](https://github.com/pjgm/serverless/commit/390bea11f5b65bd51244fb985ac197e33117401c))
* Rename `lib/plugins/aws/invokeLocal/runtimeWrappers` ([7207f5d](https://github.com/pjgm/serverless/commit/7207f5dce86f462f650f6515745f18925cb5bdaa))
* Rename `lib/plugins/aws/invokeLocal` ([d3d55df](https://github.com/pjgm/serverless/commit/d3d55dfcfc9494b24d569555bd18250dceb00aa4))
* Rename `lib/plugins/aws/lib/checkIfEcrRepositoryExists.js` ([bece3d2](https://github.com/pjgm/serverless/commit/bece3d2947fd1cbde7b1589152700ef53e9a553b))
* Rename `lib/plugins/aws/lib/getServiceState.js` ([76727ad](https://github.com/pjgm/serverless/commit/76727ad0a5372bbf0b22bbcd01492dbc78310dea))
* Rename `lib/plugins/aws/lib/monitorStack.js` ([3334645](https://github.com/pjgm/serverless/commit/333464514b16793f57b2add35839b87aa18f4e48))
* Rename `lib/plugins/aws/lib/normalizeFiles.js` ([44430c9](https://github.com/pjgm/serverless/commit/44430c9b4b8b2bad3e539a0eea262e0e79c2a5f1))
* Rename `lib/plugins/aws/lib/setBucketName.js` ([1b7d19b](https://github.com/pjgm/serverless/commit/1b7d19b0d3156c6745abbf0fb9af4c6233a73c09))
* Rename `lib/plugins/aws/lib/updateStack.js` ([5f604bb](https://github.com/pjgm/serverless/commit/5f604bb62d325f96a26f4275b3f9a19be7f3ddc6))
* Rename `lib/plugins/aws/package/compile/events/alexaSkill.js` ([407ba0f](https://github.com/pjgm/serverless/commit/407ba0f954134916a51b0a6511c39903595b20ad))
* Rename `lib/plugins/aws/package/compile/events/apiGateway` ([cb3518e](https://github.com/pjgm/serverless/commit/cb3518ee507f792831ba5b4f70bd172df9bd74fa))
* Rename `lib/plugins/aws/package/compile/events/cloudFront.js` ([72d06c3](https://github.com/pjgm/serverless/commit/72d06c339c0caa3e399d53bb31a81d4cb94a28f0))
* Rename `lib/plugins/aws/package/compile/events/eventBridge` ([358a1cf](https://github.com/pjgm/serverless/commit/358a1cf2c76fd3c005fb74995e43dad727c97fa0))
* Rename `lib/plugins/aws/package/compile/events/httpApi.js` ([364e52a](https://github.com/pjgm/serverless/commit/364e52ad7c2795f209c0e5e1ffea6972f8f6a560))
* Rename `lib/plugins/aws/package/lib/generateCoreTemplate.js` ([c1cc41f](https://github.com/pjgm/serverless/commit/c1cc41f27211eef0a81ad2ed6d3241ac4e9462ec))
* Rename `lib/plugins/aws/package/lib/getHashForFilePath.js` ([fbb2e71](https://github.com/pjgm/serverless/commit/fbb2e71cab079337bf724cf2c02723019f838c7c))
* Rename `lib/plugins/aws/package/lib/mergeIamTemplates.js` ([4f47c63](https://github.com/pjgm/serverless/commit/4f47c63ef2d20beeee418c4a0dac7c600d38e23a))
* Rename `lib/plugins/aws/package/lib/saveCompiledTemplate.js` ([e80d0dd](https://github.com/pjgm/serverless/commit/e80d0ddb305371fb3526b03236bfe237cba5a90c))
* Rename `lib/plugins/aws/package/lib/saveServiceState.js` ([9f9cac8](https://github.com/pjgm/serverless/commit/9f9cac8f607bdc9157f2e708eb86b9643639a7a6))
* Rename `lib/plugins/aws/rollbackFunction.js` ([aec7b68](https://github.com/pjgm/serverless/commit/aec7b687b8805d3a4dbd540e5e4b081b20ee1979))
* Rename `lib/plugins/aws/utils/arnRegularExpressions.js` ([975450d](https://github.com/pjgm/serverless/commit/975450d4d7c5f831db000b12bf4da3b4379da93c))
* Rename `lib/plugins/aws/utils/findAndGroupDeployments.js` ([8a2a56c](https://github.com/pjgm/serverless/commit/8a2a56c90ca33d0be7a6536a99e3a82a6fb78ad8))
* Rename `lib/plugins/aws/utils/findReferences.js` ([945937b](https://github.com/pjgm/serverless/commit/945937b7c9dbc2c7e3a1566586876dd184d02b37))
* Rename `lib/plugins/aws/utils/formatLambdaLogEvent.js` ([d2f7d19](https://github.com/pjgm/serverless/commit/d2f7d1985477ebc9ff804a64323d6e63915931f9))
* Rename `lib/plugins/aws/utils/getLambdaLayerArtifactPath.js` ([6c6e3a6](https://github.com/pjgm/serverless/commit/6c6e3a6b233ad8d8da0fbf20adaa84e7cf5298fe))
* Rename `lib/plugins/aws/utils/getS3EndpointForRegion.js` ([ecb4681](https://github.com/pjgm/serverless/commit/ecb4681a6173fa1f42d0fc5057d8c18ddc6690f1))
* Rename `lib/plugins/aws/utils/getS3ObjectsFromStacks.js` ([93c7589](https://github.com/pjgm/serverless/commit/93c75896626023c61b0c423c54feb14c933dafa4))
* Rename `lib/plugins/aws/utils/resolveCfImportValue.js` ([7e5107c](https://github.com/pjgm/serverless/commit/7e5107cda9846756546d9709a5ce6617fa33e318))
* Rename `lib/plugins/aws/utils/resolveCfRefValue.js` ([7ae35f2](https://github.com/pjgm/serverless/commit/7ae35f2bc39e815e8b14e18bdf5a39002268bee8))
* Rename `lib/plugins/aws/utils/resolveLambdaTarget.js` ([fd51305](https://github.com/pjgm/serverless/commit/fd513050de087fba1a2548526532c549386c5184))
* Rename `lib/plugins/package/lib/packageService.js` ([115dfcd](https://github.com/pjgm/serverless/commit/115dfcd4bcadc8b847ecf8784952e6c07355ebcc))
* Rename `lib/plugins/package/lib/zipService.js` ([7624d8b](https://github.com/pjgm/serverless/commit/7624d8b0ca75fe84e3007f8598183c3e93c1f852))
* Rename `lib/Serverless.js` ([7289137](https://github.com/pjgm/serverless/commit/728913707316a18609299d45e077731b3e1317e2))
* Rename `lib/utils/awsSdkPatch.js` ([96202a7](https://github.com/pjgm/serverless/commit/96202a7838dfa67b56616786180d09bacaaa326b))
* Rename `lib/utils/createFromTemplate.js` ([cab3e58](https://github.com/pjgm/serverless/commit/cab3e58839978744babc85648040d06769574ec6))
* Rename `lib/utils/deepSortObjectByKey.js` ([5c1f615](https://github.com/pjgm/serverless/commit/5c1f615ff48b7fd553120d8ab054a1155cdd2400))
* Rename `lib/utils/downloadTemplateFromRepo.js` ([a93a151](https://github.com/pjgm/serverless/commit/a93a1511b7eea27b756777ffc1a519f999e8b666))
* Rename `lib/utils/ensureArtifact.js` ([b7e5f55](https://github.com/pjgm/serverless/commit/b7e5f55bf73d0fe7d4b074a24d213c6431fa77ce))
* Rename `lib/utils/ensureExists.js` ([4bb6ff4](https://github.com/pjgm/serverless/commit/4bb6ff4e237ddd57269775eb12303c30b495f625))
* Rename `lib/utils/eventuallyUpdate.js` ([d8a36fb](https://github.com/pjgm/serverless/commit/d8a36fba4cd17a2c2b5d9fbbf0fbaff32237121e))
* Rename `lib/utils/fs/copyDirContentsSync.js` ([58e22ec](https://github.com/pjgm/serverless/commit/58e22ec54ab5a9047b1f67939017c900d4538736))
* Rename `lib/utils/fs/createZipFile.js` ([7fd6176](https://github.com/pjgm/serverless/commit/7fd6176d720e7a997d83c28e4a2fe08ef5400d56))
* Rename `lib/utils/fs/dirExists.js` ([470b1e9](https://github.com/pjgm/serverless/commit/470b1e96cda04648b54810e4242e9b07b14ca6b7))
* Rename `lib/utils/fs/dirExistsSync.js` ([a8029b1](https://github.com/pjgm/serverless/commit/a8029b101446fc8acdc9acd4c75297765e7b09a8))
* Rename `lib/utils/fs/fileExists.js` ([61527a3](https://github.com/pjgm/serverless/commit/61527a35e89f0be4e65ecfc67f23ed7b02ecefaa))
* Rename `lib/utils/fs/fileExistsSync.js` ([b396619](https://github.com/pjgm/serverless/commit/b3966191b13711f7defc1842c59d7d42f2190e6a))
* Rename `lib/utils/fs/getTmpDirPath.js` ([363ff18](https://github.com/pjgm/serverless/commit/363ff185610f39002cc9bd583901ad8e360b7053))
* Rename `lib/utils/fs/readFile.js` ([5d099f7](https://github.com/pjgm/serverless/commit/5d099f7e39167340e1b53ef0c86589a6ef7de70f))
* Rename `lib/utils/fs/readFileSync.js` ([c284f4a](https://github.com/pjgm/serverless/commit/c284f4a90c0401ca04fdb07108363095c23732f0))
* Rename `lib/utils/fs/safeMoveFile.js` ([ab5ad10](https://github.com/pjgm/serverless/commit/ab5ad10fd8aa084bc56cccf2812de0548c5f0168))
* Rename `lib/utils/fs/walkDirSync.js` ([241f2cd](https://github.com/pjgm/serverless/commit/241f2cdf4ca88e32a4e5a0c7b46f2a3c2883b672))
* Rename `lib/utils/fs/writeFile.js` ([8723cd3](https://github.com/pjgm/serverless/commit/8723cd30260f0e0c0df3097a69dcd6806b6a01de))
* Rename `lib/utils/fs/writeFileSync.js` ([8292f31](https://github.com/pjgm/serverless/commit/8292f31c476b5e834bfd887c0594a65e99546246))
* Rename `lib/utils/getFrameworkId.js` ([ed0ad9e](https://github.com/pjgm/serverless/commit/ed0ad9edcb7ad853408e7ec85cff32fd2c85e1cf))
* Rename `lib/utils/getServerlessDir.js` ([cca54df](https://github.com/pjgm/serverless/commit/cca54df714700a3f13e02f1462b46ba0c9499771))
* Rename `lib/utils/isStandaloneExecutable.js` ([aed6673](https://github.com/pjgm/serverless/commit/aed6673d680cfc158fc680cdf2e53f6281b95d6e))
* Rename `lib/utils/logDeprecation.js` ([2cf86e4](https://github.com/pjgm/serverless/commit/2cf86e4ee90f325e3af741dd7c1fd2292062381b))
* Rename `lib/utils/npm-package/isGlobal.js` ([d899d41](https://github.com/pjgm/serverless/commit/d899d4187dd88da5da7c3751973fa94da93e0306))
* Rename `lib/utils/npm-package/isWritable.js` ([87863b6](https://github.com/pjgm/serverless/commit/87863b6efe61286c8d23edacef7aac1ac21eb311))
* Rename `lib/utils/npmPackage` ([4d18118](https://github.com/pjgm/serverless/commit/4d181187219f014391cfb9c02e73462813c3c495))
* Rename `lib/utils/openBrowser.js` ([2bcc8f3](https://github.com/pjgm/serverless/commit/2bcc8f3b47a126c1cf1ce996e058b1eab99d3af3))
* Rename `lib/utils/processBackendNotificationRequest.js` ([1c2f53d](https://github.com/pjgm/serverless/commit/1c2f53dcbf55acde4057fce91d065386def2bdba))
* Rename `lib/utils/renameService.js` ([49a6af9](https://github.com/pjgm/serverless/commit/49a6af94ce9440cbbe066d2a8a8f1eeda630dfe5))
* Rename `lib/utils/telemetry/areDisabled.js` ([c3e08ca](https://github.com/pjgm/serverless/commit/c3e08ca342cde60a6041e3df99c2779b47cf192d))
* Rename `lib/utils/telemetry/generatePayload.js` ([e9c3502](https://github.com/pjgm/serverless/commit/e9c3502e2ad02c802c5942c12e023fecdf378662))
* Rename `lib/utils/yamlAstParser.js` ([e3cea12](https://github.com/pjgm/serverless/commit/e3cea12a814e36876e37ceca9686db7687b9ef9a))
* Rename `servicePath` vars to `serviceDir` ([e8c8f1c](https://github.com/pjgm/serverless/commit/e8c8f1cfff785017e8e0e55cf8fb81c2dd0040a9))
* Rename `track` to `report` ([4057344](https://github.com/pjgm/serverless/commit/40573444f9dd29855093890b5d6d98b4bbb00d4c))
* Rename internal plugin ([64bca77](https://github.com/pjgm/serverless/commit/64bca770c3a5f51ea5096c7846fbe631a6783150))
* Rename isTrackingDisabled into areAnalyticsDisabled ([8fa1fe1](https://github.com/pjgm/serverless/commit/8fa1fe1b3d7172b0c287593e59d460893cbd69e5))
* Rename tracking.js to analytics.js ([daef9e1](https://github.com/pjgm/serverless/commit/daef9e164f217125359abc0f747ca8db2ef93fc1))
* Reorder init setup ([7548e1d](https://github.com/pjgm/serverless/commit/7548e1d847f70127384400c027de3b6386fde698))
* Reorder requires ([90a9ffe](https://github.com/pjgm/serverless/commit/90a9ffed63136bc855619fb5ec8d83dac23c669d))
* Reorganize and document configuration dependencies ([c86a76c](https://github.com/pjgm/serverless/commit/c86a76cb60038765404c988da13dfc6ffde28fe6))
* Reorganize hooks resolution ([76006ec](https://github.com/pjgm/serverless/commit/76006ec1e80f51e194b51d4c0f2a11c64434158e))
* Replace _.{startsWith,endsWith,includes} with native methods ([8bb5517](https://github.com/pjgm/serverless/commit/8bb55174562c379ae14e5d1b90db3ed2b25038bd)), closes [#7715](https://github.com/pjgm/serverless/issues/7715)
* Replace _.assign and _.extend with Object.assign ([#7766](https://github.com/pjgm/serverless/issues/7766)) ([85e9cd4](https://github.com/pjgm/serverless/commit/85e9cd4455bb631be921a12a37f2174fd50ecec6))
* Replace _.every(array) with array.every ([#7764](https://github.com/pjgm/serverless/issues/7764)) ([d1721cb](https://github.com/pjgm/serverless/commit/d1721cb2b4b5a6b3621eba78dbe27eead21f9164))
* Replace _.filter with array.filter ([#7775](https://github.com/pjgm/serverless/issues/7775)) ([dac7c56](https://github.com/pjgm/serverless/commit/dac7c56b26dbe2b3489e88329dd70e0787c73087))
* Replace _.isArray with native Array.isArray ([#7703](https://github.com/pjgm/serverless/issues/7703)) ([3fe2e98](https://github.com/pjgm/serverless/commit/3fe2e98f15d3a78571b3aa0894be1632e2f5ab51))
* Replace _.keys with Object.keys ([#7784](https://github.com/pjgm/serverless/issues/7784)) ([d43241e](https://github.com/pjgm/serverless/commit/d43241ea8bacc43d3105ba8600674a7564cb6895))
* Replace `_.{entries|entriesIn|toPairs}` with `Object.entries` ([b867df1](https://github.com/pjgm/serverless/commit/b867df147aea5e1f57a9d275e2a389efbbcf38aa)), closes [#8275](https://github.com/pjgm/serverless/issues/8275)
* Replace `_.chain` with native constructs ([#7862](https://github.com/pjgm/serverless/issues/7862)) ([288cb25](https://github.com/pjgm/serverless/commit/288cb255acda29b15e10b10efcddee1b491a9b5d))
* Replace `_.compact` with `array.filter(Boolean)` ([#7858](https://github.com/pjgm/serverless/issues/7858)) ([7e68a0c](https://github.com/pjgm/serverless/commit/7e68a0c90f19ff9d8cfaab8f064628e72db2a054))
* Replace `_.concat` with `array.concat` ([#7851](https://github.com/pjgm/serverless/issues/7851)) ([fce0b18](https://github.com/pjgm/serverless/commit/fce0b1886448d91be21aa64b778c98d95bb47b87))
* Replace `_.entries` with `Object.entries` ([#11793](https://github.com/pjgm/serverless/issues/11793)) ([1181780](https://github.com/pjgm/serverless/commit/11817802654a8bb28e8664ab6d9f346ebaf97e1e))
* Replace `_.find` with `array.find` ([#7782](https://github.com/pjgm/serverless/issues/7782)) ([0036962](https://github.com/pjgm/serverless/commit/003696260c43acf2415fa6b05a212ea57bdec3d4))
* Replace `_.findKey` with `Object.keys(object).find` ([#7881](https://github.com/pjgm/serverless/issues/7881)) ([d6cf036](https://github.com/pjgm/serverless/commit/d6cf036c1647ce68d75b15e831e00f1cec6a97be))
* Replace `_.first`with `array[0]` ([#7816](https://github.com/pjgm/serverless/issues/7816)) ([a527744](https://github.com/pjgm/serverless/commit/a527744606a7dd9dd9caf0a376eb615f0b81a40f))
* Replace `_.flatMap` usage ([#9948](https://github.com/pjgm/serverless/issues/9948)) ([26b8bd5](https://github.com/pjgm/serverless/commit/26b8bd5c5fd2154f47fa12804f1aee140000155f))
* Replace `_.flatMap` with `Array.prototype.flatMap` ([#11272](https://github.com/pjgm/serverless/issues/11272)) ([4f7e129](https://github.com/pjgm/serverless/commit/4f7e12939ced5b269d53624e5643bd5a9173ed7b))
* Replace `_.flatten` with `Array.prototype.flat` ([#11271](https://github.com/pjgm/serverless/issues/11271)) ([b36cdf2](https://github.com/pjgm/serverless/commit/b36cdf2db6ee25f7defe6f2c02dd40e1d5cb65c4))
* Replace `_.forEach` and `_.each`  with array.forEach ([#7748](https://github.com/pjgm/serverless/issues/7748)) ([5e0af21](https://github.com/pjgm/serverless/commit/5e0af21313b1061666b355b2b83737eb5f2dccf0))
* Replace `_.forEach` with `Object.entries().forEach` ([#8280](https://github.com/pjgm/serverless/issues/8280)) ([76e02cc](https://github.com/pjgm/serverless/commit/76e02cc09c74e18abdc1fccbda81676cf2462598))
* Replace `_.forOwn` with `Object.entries().forEach` ([#8284](https://github.com/pjgm/serverless/issues/8284)) ([56c7e44](https://github.com/pjgm/serverless/commit/56c7e443a0350027cd5ccf5d4c94dc06f353306f))
* Replace `_.fromPairs` with `Object.fromEntries` ([#11794](https://github.com/pjgm/serverless/issues/11794)) ([03d3ab3](https://github.com/pjgm/serverless/commit/03d3ab39da1096aae4d797675793523726f6c1b6))
* Replace `_.has` with better counterparts ([#7915](https://github.com/pjgm/serverless/issues/7915)) ([7bbd04a](https://github.com/pjgm/serverless/commit/7bbd04a6933c1631646f16670e3d85c357450e7a))
* Replace `_.head` with `array[0]` ([#7817](https://github.com/pjgm/serverless/issues/7817)) ([8991ceb](https://github.com/pjgm/serverless/commit/8991ceb209884f72beba0ab8b166a258c0af3e1d))
* Replace `_.includes` with `val.includes` ([#7818](https://github.com/pjgm/serverless/issues/7818)) ([77fbb59](https://github.com/pjgm/serverless/commit/77fbb5969b31bdd0d2220019f896df5a9f36e6fe))
* Replace `_.indexOf` with `arr.includes` ([#7825](https://github.com/pjgm/serverless/issues/7825)) ([332524d](https://github.com/pjgm/serverless/commit/332524dae73cb102c244d3b568ec880f9bc816aa))
* Replace `_.isEmpty` with native counterparts ([#7873](https://github.com/pjgm/serverless/issues/7873)) ([4c33476](https://github.com/pjgm/serverless/commit/4c33476210d355b9b822909685a951a4d970f467))
* Replace `_.isFunction` with `typeof value === 'function'` ([e42ab2c](https://github.com/pjgm/serverless/commit/e42ab2cda65d3986ce78f81da10c7149019162a2)), closes [#7810](https://github.com/pjgm/serverless/issues/7810)
* Replace `_.isNil(value)` with `value == null` ([#7809](https://github.com/pjgm/serverless/issues/7809)) ([6cf4901](https://github.com/pjgm/serverless/commit/6cf4901a8907ddfb36dc45ee1e094a7dff401360))
* Replace `_.isString(value)` with `typeof value === 'string'` ([9f3ee94](https://github.com/pjgm/serverless/commit/9f3ee94a74a4d9d80451143a5f212d0b6f790a5f)), closes [#7812](https://github.com/pjgm/serverless/issues/7812)
* Replace `_.isUndefined` with native checks ([#7826](https://github.com/pjgm/serverless/issues/7826)) ([20cef81](https://github.com/pjgm/serverless/commit/20cef81555473311128ed425125d017c1ab6729c))
* Replace `_.join` with `array.join` ([#7805](https://github.com/pjgm/serverless/issues/7805)) ([5cf46bf](https://github.com/pjgm/serverless/commit/5cf46bf109287bcd327e6f45f58b3f392cc345de))
* Replace `_.keyBy` with native constructs ([#7882](https://github.com/pjgm/serverless/issues/7882)) ([e7163ce](https://github.com/pjgm/serverless/commit/e7163ceaaceeb93971350b7ccd9cc618b15e4f9b))
* Replace `_.map` with `array.map` ([#7827](https://github.com/pjgm/serverless/issues/7827)) ([4c6f8be](https://github.com/pjgm/serverless/commit/4c6f8be5ccae88034e19f72a53996208dd4a56d5))
* Replace `_.min` with native constructs ([#7840](https://github.com/pjgm/serverless/issues/7840)) ([ee94dce](https://github.com/pjgm/serverless/commit/ee94dce47ce989c7af2d54fc8c7dc24beab43ee8))
* Replace `_.nth` with `array[index]` ([#7841](https://github.com/pjgm/serverless/issues/7841)) ([d5de0ec](https://github.com/pjgm/serverless/commit/d5de0ec56aabff10ab6de8913b1b68730aa63fcd))
* Replace `_.parseInt` with `Number` ([#7877](https://github.com/pjgm/serverless/issues/7877)) ([f2e1942](https://github.com/pjgm/serverless/commit/f2e19420e9a639b1523958cb406d7bd178571248))
* Replace `_.pick` with native property assignment ([#9937](https://github.com/pjgm/serverless/issues/9937)) ([6087fa3](https://github.com/pjgm/serverless/commit/6087fa3400b508092a5113d40e4b2c4fd8ec22a7))
* Replace `_.pullAllWith` with native constructs ([#7861](https://github.com/pjgm/serverless/issues/7861)) ([f6743e9](https://github.com/pjgm/serverless/commit/f6743e9b35bf821109ffb18039ea9cf419a7ad18))
* Replace `_.reduce` with `array.reduce` ([#7883](https://github.com/pjgm/serverless/issues/7883)) ([297f7d8](https://github.com/pjgm/serverless/commit/297f7d85e07469f8157dfb6befb697f8dc0305d7))
* Replace `_.repeat` with `string.repeat` ([#7842](https://github.com/pjgm/serverless/issues/7842)) ([a549517](https://github.com/pjgm/serverless/commit/a5495174413cead282dc09959ec251ee8444a06a))
* Replace `_.replace` with `string.replace` ([#7843](https://github.com/pjgm/serverless/issues/7843)) ([aaa2f96](https://github.com/pjgm/serverless/commit/aaa2f965a73ade5c691f0f935c5d37283ba7cd8a))
* Replace `_.set` with native assignment ([66aa66f](https://github.com/pjgm/serverless/commit/66aa66fbfe363edeb4123d709890a7c78f74b571))
* Replace `_.size` with native counterparts ([#7798](https://github.com/pjgm/serverless/issues/7798)) ([2b00928](https://github.com/pjgm/serverless/commit/2b00928f87901bfd432f34e181d85aed65837841))
* Replace `_.some` usage with `array.some` ([#7901](https://github.com/pjgm/serverless/issues/7901)) ([75bf185](https://github.com/pjgm/serverless/commit/75bf185785dc2b0a91b6500f353df92990e90f47))
* Replace `_.sortBy` with `array.sort` ([#7823](https://github.com/pjgm/serverless/issues/7823)) ([57e4212](https://github.com/pjgm/serverless/commit/57e4212671ea3027fab9482e6006933e4c5b6c55))
* Replace `_.split` with `string.split` ([#7820](https://github.com/pjgm/serverless/issues/7820)) ([053f5f4](https://github.com/pjgm/serverless/commit/053f5f420b45e9dec794e82d1bc23a2731a077ff))
* Replace `_.takeRight` with `array.slice` ([#7831](https://github.com/pjgm/serverless/issues/7831)) ([3b3db7a](https://github.com/pjgm/serverless/commit/3b3db7ad29996e204bdef605d0c191cd610148d2))
* Replace `_.toString` with native `String` ([#7893](https://github.com/pjgm/serverless/issues/7893)) ([028e467](https://github.com/pjgm/serverless/commit/028e46720251901279b8230cf76deca721ee4ae6))
* Replace `_.toUpper(string)` with `string.toUpperCase` ([#7808](https://github.com/pjgm/serverless/issues/7808)) ([22a4ed2](https://github.com/pjgm/serverless/commit/22a4ed27e262cbf13cb0df14df32a2c4bc2a0c9d))
* Replace `_.unset` with `delete` ([#7813](https://github.com/pjgm/serverless/issues/7813)) ([e39cdfd](https://github.com/pjgm/serverless/commit/e39cdfdf02adba8b83f4bbf83208fdf81e32c1d7))
* Replace `_.values` with `Object.values` ([#8274](https://github.com/pjgm/serverless/issues/8274)) ([57d1ce1](https://github.com/pjgm/serverless/commit/57d1ce1a660a0446c77e9bafb174ae3fe0263516))
* Replace `BbPromise.each` with native counterpart ([#11797](https://github.com/pjgm/serverless/issues/11797)) ([5068516](https://github.com/pjgm/serverless/commit/5068516f0424ab1b8c94f4b698234ace36a674cd))
* Replace `BbPromise.props` with `Promise.all` ([#8414](https://github.com/pjgm/serverless/issues/8414)) ([2d6824c](https://github.com/pjgm/serverless/commit/2d6824cde531ba56758f441b39b5ab018702e866))
* Replace `config.servicePath` with `service.dir` ([87d3802](https://github.com/pjgm/serverless/commit/87d380275bc3102c71daa0f87e8211b90e5d58c4))
* Replace `fse.access` with `fs.promises.access` ([#9915](https://github.com/pjgm/serverless/issues/9915)) ([5155e01](https://github.com/pjgm/serverless/commit/5155e0180e0cd5e3130bc74e308a97c0ea1a5c2b))
* Replace `fse.chmod` with `fs.promises.chmod` ([#9647](https://github.com/pjgm/serverless/issues/9647)) ([83c7726](https://github.com/pjgm/serverless/commit/83c772684d655b233522d1e75128476c29339c83))
* Replace `fse.createWriteStream` with `fs.createWriteStream` ([3500f64](https://github.com/pjgm/serverless/commit/3500f641f5212f196f75081e67d1d1518ac3bb6b))
* Replace `fse.exists` with `fs.promises.access` ([#8788](https://github.com/pjgm/serverless/issues/8788)) ([9abe9db](https://github.com/pjgm/serverless/commit/9abe9db27f26ad9d7fb55ce5fcf5bbbb9235b974))
* Replace `fse.promises.realpath` with `fs.promises.realpath` ([f5174ff](https://github.com/pjgm/serverless/commit/f5174ffa8027392525a7c57ea1fa59627a61bcc1))
* Replace `fse.readdir` with `fs.promises.readdir` ([#9780](https://github.com/pjgm/serverless/issues/9780)) ([1e00f9e](https://github.com/pjgm/serverless/commit/1e00f9edfb5f7618759f9f03d0dad58701a5a27a))
* Replace `fse.readFile` with `fs.promises.readFile` ([#9935](https://github.com/pjgm/serverless/issues/9935)) ([f431218](https://github.com/pjgm/serverless/commit/f431218790ae31efdc4e0a65a5b17a32605ede3e))
* Replace `fse.rename` with `fs.promises.rename` ([#9605](https://github.com/pjgm/serverless/issues/9605)) ([e6ff228](https://github.com/pjgm/serverless/commit/e6ff2286a55d8cb8f82e58d8173b0a386a4b1767))
* Replace `fse.stat` with `fs.promises.stat` ([#9845](https://github.com/pjgm/serverless/issues/9845)) ([bb0484e](https://github.com/pjgm/serverless/commit/bb0484e6b54a3cc6aed46ff23100e08c90c995ce))
* Replace `fse.unlink` with `fs.promises.unlink` ([#9754](https://github.com/pjgm/serverless/issues/9754)) ([daee1d5](https://github.com/pjgm/serverless/commit/daee1d5375efdb748b85b85a2a4675ac3277001f))
* Replace `fse.writeFile` with `fs.promises.writeFile` ([#9870](https://github.com/pjgm/serverless/issues/9870)) ([05fff98](https://github.com/pjgm/serverless/commit/05fff98a0003b22a66e8932c622c0e10c57bf06b))
* Replace `ncjsm/resolve` usage with native `createRequire` ([5fc55c0](https://github.com/pjgm/serverless/commit/5fc55c046497bdfa3d1d895c44fe69ac9de8b3ba))
* Replace inquirer with @serverless/inquirer ([#7729](https://github.com/pjgm/serverless/issues/7729)) ([4724cb8](https://github.com/pjgm/serverless/commit/4724cb8eeb16a35695c1f4b166b81c0cc2e4ddae))
* Replace internal old logging utils with modern interface ([5a451ad](https://github.com/pjgm/serverless/commit/5a451ad0249b6924cd4105e5c372028402517ecd))
* Replace mkdrip with esnureDir from fs-extra ([1beb8d0](https://github.com/pjgm/serverless/commit/1beb8d0246e705d3d724dbd2fb4c6639bc961cba))
* Resolve path to package in `resolveLocalServerlessPath` ([2672047](https://github.com/pjgm/serverless/commit/2672047c2f388b5bb5645571e050269676eeab9a))
* Revert `bluebird` from `lib/plugins/aws` ([55abaaf](https://github.com/pjgm/serverless/commit/55abaaf6d5db17c4824c2d2d3dc3f540c682acea))
* Revert `bluebird` from `lib/plugins/create` ([ae2c92c](https://github.com/pjgm/serverless/commit/ae2c92ced6f25cca6c6243daf90aa23bfe0d6278))
* Revert `bluebird` from `lib/plugins/interactiveCli` ([217b975](https://github.com/pjgm/serverless/commit/217b9751ead901395467b7221f601f955329eb1b))
* Revert `bluebird` from `lib/plugins/package` ([399d91b](https://github.com/pjgm/serverless/commit/399d91b7e4508ae15c4beba1fec66c32c0367386))
* Revert `bluebird` from `lib/plugins/plugin` ([2a9f79f](https://github.com/pjgm/serverless/commit/2a9f79f19e33c83ed4df46ecd305cc49ce1a8c15))
* Revert from `mainProgressTitles` handling ([634b59e](https://github.com/pjgm/serverless/commit/634b59e396004992c9460ad2c3cfaa779efa4fbe))
* Revert removal of `bluebird` from `lib/classes` ([c41bd64](https://github.com/pjgm/serverless/commit/c41bd64bb233b588dc615bc11c513f3e2c486084))
* Revert removal of `bluebird` from `lib/utils` ([f62fc2e](https://github.com/pjgm/serverless/commit/f62fc2ee9c39a15c2b3894c5fae185a530307506))
* Revert remove `bluebird` from `lib/plugins` ([7a012d8](https://github.com/pjgm/serverless/commit/7a012d83b975022e5ee60f5054229398a9424d13))
* Seclude `cli/resolve-local-serverless-path` util ([9d78348](https://github.com/pjgm/serverless/commit/9d783482895d82a1bfdb627c4cc0debb32123d56))
* Seclude `tokenizeException` util ([7743582](https://github.com/pjgm/serverless/commit/774358271e5758fe53aaf8cb32ffe658ca8e24f3))
* Seclude AWS request util from internals ([#8850](https://github.com/pjgm/serverless/issues/8850)) ([5fb85d3](https://github.com/pjgm/serverless/commit/5fb85d36c8ee965df691b8f2dfddeaab8315c77d))
* Seclude configuration parse from internals ([f274cd7](https://github.com/pjgm/serverless/commit/f274cd7637e8171ee04bd174e786c7e07706343a))
* Seclude ensureExists util ([c3f59e4](https://github.com/pjgm/serverless/commit/c3f59e4d785145c2e1ba7c1324f3afedba482479))
* Seclude generic version artifacts handlers ([c872c14](https://github.com/pjgm/serverless/commit/c872c143ba11f58fdc0f77420437f4a6e6205464))
* Seclude IAM role resource name resolution logic ([6d7103d](https://github.com/pjgm/serverless/commit/6d7103da02dcbc4f89949dcebdf4ac6745b91776))
* Seclude ServerlessError into lib/serverless-error.js ([87790e5](https://github.com/pjgm/serverless/commit/87790e50bd9c178aefd4f2ad8793c9c56fb8eb49))
* Seprate internal and plugin output sections ([7bb2520](https://github.com/pjgm/serverless/commit/7bb2520f491d008075eb08be64bdb2e0b60ec5c6))
* Show variables resolution info less frequently ([516603a](https://github.com/pjgm/serverless/commit/516603af90b9e1260433c615f8f8f2ad2c68b41d))
* Simplify condition ([7eeaa10](https://github.com/pjgm/serverless/commit/7eeaa10f3af510b3d5a95a8db4f0478609181e78))
* Simplify condition notation ([ca79cb6](https://github.com/pjgm/serverless/commit/ca79cb6d69f60c843c54dc1946b491134b56bad6))
* Simplify conditional ([112f855](https://github.com/pjgm/serverless/commit/112f8551cd7c1fe7758bbeed6e116af7646ef186))
* Simplify lifecycle event hooks resolution ([8b4498c](https://github.com/pjgm/serverless/commit/8b4498c911e24ef7a46daf66380f1c122f988af3))
* **Standalone:** Convert to async/await ([b114efa](https://github.com/pjgm/serverless/commit/b114efa999a6561ef171e30a75fe8d86d246e912))
* **Standalone:** Fix CLI help ([0b25ce2](https://github.com/pjgm/serverless/commit/0b25ce2efdc18e34e9cbb96875e539a5ad9fd524))
* **Standalone:** Improve upload confirmation logs ([5f5c330](https://github.com/pjgm/serverless/commit/5f5c3307e3624a9490b662b8a69573385842e4a1))
* **Standalone:** Remove dependency to stream-promise ([#8601](https://github.com/pjgm/serverless/issues/8601)) ([ca697f3](https://github.com/pjgm/serverless/commit/ca697f3911aec5a0bb0e02ce5bfdef5bbd4cc00a))
* **Standalone:** Reorder requires ([4275f27](https://github.com/pjgm/serverless/commit/4275f2770a0f14eb7891ca939cc50008222b94c6))
* **Standalone:** Seclude standalone utils ([5fcc54a](https://github.com/pjgm/serverless/commit/5fcc54ae2aae9aea40d0fec8d42a86ebd21b5a76))
* **Standalone:** Split upload script logic ([e2dd9a1](https://github.com/pjgm/serverless/commit/e2dd9a14a7b1ac8d8ea8e19a3da12f6ea521f0e1))
* **Standalone:** Update Tencent CLI standalone download URL ([e26625a](https://github.com/pjgm/serverless/commit/e26625a58ce96776f241037b00a190a89ecd6d45)), closes [#10811](https://github.com/pjgm/serverless/issues/10811)
* Support `conceal` option in modern logs ([0dacf1b](https://github.com/pjgm/serverless/commit/0dacf1bb3bd53da32a24cf2286cf081aecf22806))
* Support custom error message for variables resolution ([f7ffb19](https://github.com/pjgm/serverless/commit/f7ffb1978804ce01fc14d14866529378ebc1c1e2))
* Support relative paths in `import-esm` util ([fcf17a6](https://github.com/pjgm/serverless/commit/fcf17a608d3a24d18cac4705d412366e27a1f2d1))
* Supress AWS SDK v2 deprecation message ([74c3ae0](https://github.com/pjgm/serverless/commit/74c3ae004c7166c76fe5355a778fe1f5f9c401b0))
* Switch to "fastest-levenshtein" ([0cd9cca](https://github.com/pjgm/serverless/commit/0cd9ccaf65a13d01c9e26c9950a6e4dc4a5a53f7))
* Switch to @serverless/util/config ([96afed4](https://github.com/pjgm/serverless/commit/96afed438cde47a9fc75736ba22485ec90c7eb5a))
* **Telemetry:** Add `anonymizeStacktracePaths` util ([f1a9a7b](https://github.com/pjgm/serverless/commit/f1a9a7b76032c312fd83c6dd5e1a332dfffa0b52))
* **Telemetry:** Add `isTelemetryReportedExternally` flag ([78a4a96](https://github.com/pjgm/serverless/commit/78a4a96d74848799b13d273eb25956f4518f5099))
* **Telemetry:** Add `resolveErrorLocation` util ([8860397](https://github.com/pjgm/serverless/commit/8860397798398412d7232d9e4e0001a83efb0424))
* **Telemetry:** Debug log for telemetry payload ([db67962](https://github.com/pjgm/serverless/commit/db6796257f41618ad7da440ca5b2e46fae971fe1))
* **Telemetry:** Do not generate payload if telemetry disabled ([e1b9ba4](https://github.com/pjgm/serverless/commit/e1b9ba46bda28db101f61a53b46a66ab195ad810))
* **Telemetry:** Ensure generation and related utils are sync ([e65199c](https://github.com/pjgm/serverless/commit/e65199c05213e1bac17acedc84cdd6dfd26ff00a))
* **Telemetry:** Ensure local serverless will not run telemetry ([98e6e1e](https://github.com/pjgm/serverless/commit/98e6e1eaf7a58794f51843f75e08fd4a7ceb261a))
* **Telemetry:** Ensure to pass unique id with events ([3bcff79](https://github.com/pjgm/serverless/commit/3bcff796f1046c09c4f7f9c0545f6393a332c4c0))
* **Telemetry:** Ensure to report `projectId` for interactive ([08b5acb](https://github.com/pjgm/serverless/commit/08b5acbaa901c7ce529064c394151e05bdd43aef))
* **Telemetry:** Expose `initialContext.isConsoleEnabled` ([f580883](https://github.com/pjgm/serverless/commit/f580883d48027065e9e9aff77ee49c9c1a61fedd))
* **Telemetry:** Improve AWS stack error codes ([#9510](https://github.com/pjgm/serverless/issues/9510)) ([c265905](https://github.com/pjgm/serverless/commit/c265905f518f8cbea170c5a2774670c60de0e36c))
* **Telemetry:** Improve variable names ([542b691](https://github.com/pjgm/serverless/commit/542b691a6472fc5a559e3c986e3b68eefcb6ad6e))
* **Telemetry:** Include `commandUsage` in case of error ([ac03d83](https://github.com/pjgm/serverless/commit/ac03d832896eec26773e5ce06c22c249d240a9ed))
* **Telemetry:** Include `paramsCount` in telemetry ([ae169f5](https://github.com/pjgm/serverless/commit/ae169f564a0e148a75064cca6b5ca3fff029ff33))
* **Telemetry:** Increase error location coverage ([7264d16](https://github.com/pjgm/serverless/commit/7264d1672e93fdb1046cf7ebe859b607c80e31ca))
* **Telemetry:** Make `generatePayload` `serverless` independent ([4f6a50a](https://github.com/pjgm/serverless/commit/4f6a50a2e145e664405b00661d801b6ad094f418))
* **Telemetry:** Make `getServiceConfig` return only `config` prop ([0f30125](https://github.com/pjgm/serverless/commit/0f3012518939a721dde0e5a2ac396231031af94d))
* **Telemetry:** Make `serverless` optional in `generatePayload` ([ba5f207](https://github.com/pjgm/serverless/commit/ba5f207d0ae83717567a9dad2e74af33eeec905f))
* **Telemetry:** Move telemetry handling to `scripts/serverless.js` ([4cab803](https://github.com/pjgm/serverless/commit/4cab803ccda05bb3834c0ec4df483837ff84802e))
* **Telemetry:** Normalize AWS request error codes ([5a23931](https://github.com/pjgm/serverless/commit/5a23931734ee80b80182008197c92985975f1646))
* **Telemetry:** Only process in `PluginManager` if flag missing ([fac47cf](https://github.com/pjgm/serverless/commit/fac47cfa23c6e0573b0baa9b379d7226654c4dbd))
* **Telemetry:** Optimise error location length ([f3ff6d2](https://github.com/pjgm/serverless/commit/f3ff6d21758b61116c748746cefe8c1a3d6ab776))
* **Telemetry:** Recognize `constructs` ([9e10cea](https://github.com/pjgm/serverless/commit/9e10ceaf81e8b9d13867937fedc9502a1ff4e320))
* **Telemetry:** Recognize `isUsingCompose` ([007c294](https://github.com/pjgm/serverless/commit/007c294211954e3fdb034030eacd1f01e63920bf))
* **Telemetry:** Recognize `notificationsMode` ([00fdba1](https://github.com/pjgm/serverless/commit/00fdba154655b15b5b2de4b9ceca08f8bfce599e))
* **Telemetry:** Reduce length of error location ([f6a7d03](https://github.com/pjgm/serverless/commit/f6a7d03b04bd13f91bc247e518a1ad12496ead8c))
* **Telemetry:** Rely on direct evaluation of `isTtyTerminal` ([e29253f](https://github.com/pjgm/serverless/commit/e29253fbeb17764644ef97c61c0a88892cda4136))
* **Telemetry:** Remove dead path error handling ([91b10ed](https://github.com/pjgm/serverless/commit/91b10ed208f2dee4b690df633f4275f658355044))
* **Telemetry:** Rename `analytics` to `telemetry` ([d667111](https://github.com/pjgm/serverless/commit/d66711108b1e69dd33259e43a0770e78631b9a8a))
* **Telemetry:** Rename `report` to `storeLocally` ([bd4e792](https://github.com/pjgm/serverless/commit/bd4e792594843ab51d1859f1fbc499aa4a4513c1))
* **Telemetry:** Rename `sendPending` to `send` ([7017585](https://github.com/pjgm/serverless/commit/70175857c9442e5c93daadae2039adf7868340c0))
* **Telemetry:** Report `commandUsage` as object ([cc24bc2](https://github.com/pjgm/serverless/commit/cc24bc2ae280237b3d439e1934ab75710e0f259f))
* **Telemetry:** Report all interruption signals ([7354c20](https://github.com/pjgm/serverless/commit/7354c2000f25d526f8c3fd97c6d4d22054388755))
* **Telemetry:** Report error location for non-normative error codes ([07d5b9c](https://github.com/pjgm/serverless/commit/07d5b9c19e9f5365af322a4862b03ccdca05655c))
* **Telemetry:** Report installed `docker` version ([39806d6](https://github.com/pjgm/serverless/commit/39806d622fdc1d8dae7618394ffe12bbe702675d))
* **Telemetry:** Report whether we're in context of TTY terminal ([9cea555](https://github.com/pjgm/serverless/commit/9cea555e88bdaadf717def21b5298a64c7ce79b9))
* **Telemetry:** Send more frequently to avoid big payloads ([889e1b6](https://github.com/pjgm/serverless/commit/889e1b67bf1637e6f78bef83ac036937df50ebce))
* **Telemetry:** Use `prompt-with-history` ([4d56be5](https://github.com/pjgm/serverless/commit/4d56be562a4bdaf2588bdc42227a451d098d1420))
* **Templates:** Fix typo in package.json for template aws-nodejs-typescript ([#8754](https://github.com/pjgm/serverless/issues/8754)) ([37398d0](https://github.com/pjgm/serverless/commit/37398d06c582b1676c2aaa32708cfd515baf65b9))
* **Templates:** Remove unnecessary `fmt.Sprintf` in `tencent-go` ([e798c26](https://github.com/pjgm/serverless/commit/e798c269df6f456bccf6a1e755015ea1e7631117))
* **Templates:** Unify file naming convention ([fc0eb5a](https://github.com/pjgm/serverless/commit/fc0eb5aebc135edc95e345cb30a719b21a14b331))
* **Templates:** Upgrade `frameworkVersion` ([9f5a077](https://github.com/pjgm/serverless/commit/9f5a07793af2270f30f181d2487bed4aeec89551))
* **Templates:** Upgrade `middy` in `aws-nodejs-typescript` ([#10215](https://github.com/pjgm/serverless/issues/10215)) ([ad95e03](https://github.com/pjgm/serverless/commit/ad95e030b3581a65babc8dd175b8bb69f1215534))
* **Templates:** Upgrade to avoid using deprecated functionality ([3c5e497](https://github.com/pjgm/serverless/commit/3c5e497116bec410b16f4a752c30e19b856df898))
* **Templates:** Use non deprecated API in `aws-nodejs-typescript` ([6671d98](https://github.com/pjgm/serverless/commit/6671d98615ab7d003c3c7413c9334b63b2d735e8)), closes [#10214](https://github.com/pjgm/serverless/issues/10214)
* Typos in schema ([#8735](https://github.com/pjgm/serverless/issues/8735)) ([2b7568a](https://github.com/pjgm/serverless/commit/2b7568a960c88dda8ab2bbe1b6c8dd238fa78a51))
* Unconditionally load dasboard plugin ([378768d](https://github.com/pjgm/serverless/commit/378768ddafbe2315b2672b90616e9bd29c7b6513))
* Updated dev mode warning copy ([#11976](https://github.com/pjgm/serverless/issues/11976)) ([4fee5d5](https://github.com/pjgm/serverless/commit/4fee5d54862d5089fe9e589f0c2e2f38d7f17e85))
* Upgrade 'fs-extra' to v8 ([#7719](https://github.com/pjgm/serverless/issues/7719)) ([c106d53](https://github.com/pjgm/serverless/commit/c106d5363830e9dc31a5714f56abfb26b0a5db37))
* Upgrade "@serverless/utils" to v2 ([ef39e95](https://github.com/pjgm/serverless/commit/ef39e958db39b367875af871a7014b4d284f5554))
* Upgrade "ajv" to v7 and "ajv-keywords" to v4 ([#8703](https://github.com/pjgm/serverless/issues/8703)) ([1af73ba](https://github.com/pjgm/serverless/commit/1af73bacdf01e5dc855da59387ab36085b2b78a1))
* Upgrade "js-yaml" to v4 ([b143383](https://github.com/pjgm/serverless/commit/b14338332c86a4461d0e1c564c740c1f6a29fb4a))
* Upgrade `@serverless/utils` to v6 ([6a659f1](https://github.com/pjgm/serverless/commit/6a659f1b201e0e764814cbe2f85ca7a0aa65454f))
* Upgrade `ajv` to `v8` along with related packages ([766b58d](https://github.com/pjgm/serverless/commit/766b58da610d6d22479c4b114bcdfdf5c16e8a41))
* Upgrade `dotenv-expand` to v9 ([c769c1e](https://github.com/pjgm/serverless/commit/c769c1e06dd3529bf7a8a1cda33d54b5a7d12ac7))
* Upgrade `filesize` to v10 ([9ef5fd2](https://github.com/pjgm/serverless/commit/9ef5fd23b123730696d00985988a1bc37a3c10e0))
* Upgrade `filesize` to v8 ([9a2511c](https://github.com/pjgm/serverless/commit/9a2511cf90c60ba5b67ecea81121328c8dd93702))
* Upgrade globby to v9 ([#7750](https://github.com/pjgm/serverless/issues/7750)) ([b245596](https://github.com/pjgm/serverless/commit/b245596dbb76e6cdea081e3c6510976587e7e82f))
* Upgrade json-refs to v3 ([#7763](https://github.com/pjgm/serverless/issues/7763)) ([97e99fc](https://github.com/pjgm/serverless/commit/97e99fc8f09feb45f31d4934c3f5cb1db2e0193a))
* Upgrade to `@serverless/test` in `v10` ([4201b30](https://github.com/pjgm/serverless/commit/4201b304a2b6582e5755944b1c4a0ff89ad2bcc1))
* Upgrade to async/await ([8c7731d](https://github.com/pjgm/serverless/commit/8c7731d4376fb7ae4998a37b2a196e4fb80107ba))
* Use @serverless/utils for cloudformationSchema ([#8705](https://github.com/pjgm/serverless/issues/8705)) ([2efc357](https://github.com/pjgm/serverless/commit/2efc3570c953cff04a22c8690f510532d5650eac))
* Use `async/await` in `analytics` ([b35c28a](https://github.com/pjgm/serverless/commit/b35c28a1946b6677f252d29ad5eb46a5fb7b518c))
* Use `async/await` in `analytics` test ([8c6be15](https://github.com/pjgm/serverless/commit/8c6be158d76a3fb02827ddc77e2a89118b15a5c4))
* Use `async/await` in `events/apiGateway`. ([#8869](https://github.com/pjgm/serverless/issues/8869)) ([c5ba682](https://github.com/pjgm/serverless/commit/c5ba682a6bc4fc96151c75cdf50cff2468d6def5))
* Use `async/await` in `lib/plugins/aws/invokeLocal`. ([#8876](https://github.com/pjgm/serverless/issues/8876)) ([134db21](https://github.com/pjgm/serverless/commit/134db21ed27874ae64db1c8964523b5b5ae6c2bf))
* Use `async/await` in `lib/plugins/aws`. ([#8871](https://github.com/pjgm/serverless/issues/8871)) ([efbaf00](https://github.com/pjgm/serverless/commit/efbaf00b33ca2f51d2f0b18b98466341e51f3052))
* Use `async/await` in `lib/plugins`. ([#8875](https://github.com/pjgm/serverless/issues/8875)) ([f95971d](https://github.com/pjgm/serverless/commit/f95971d22b65c963ab01ac0273abcffb932b2434))
* Use `async/await` in `PluginManager` ([8aa2757](https://github.com/pjgm/serverless/commit/8aa275725becc446fc09cceedf6618d7afbc7770))
* Use `async/await` syntax in `bucket.js` ([39e43b5](https://github.com/pjgm/serverless/commit/39e43b51e5e13c708900e0ccc4d4f25ccf0df61c))
* Use `async` in `aws/package/compile/events` ([#8873](https://github.com/pjgm/serverless/issues/8873)) ([3c93e2a](https://github.com/pjgm/serverless/commit/3c93e2a5347ed700e55d4307b4498e0c49eb8a03))
* Use `async` in `compile/events/websockets` ([#8874](https://github.com/pjgm/serverless/issues/8874)) ([61dd3bd](https://github.com/pjgm/serverless/commit/61dd3bde8d17cdd995fdd27259a689d12bee1e42))
* Use `async` in `lib/plugins/aws/package` ([#8870](https://github.com/pjgm/serverless/issues/8870)) ([6e486b3](https://github.com/pjgm/serverless/commit/6e486b3eb1cbd1755501f00de59b2347e243c100))
* Use `async` in `lib/plugins/create` ([#9683](https://github.com/pjgm/serverless/issues/9683)) ([4b87497](https://github.com/pjgm/serverless/commit/4b87497875a19348e444763eea85671ed2c4f0b7))
* Use `async` in `lib/plugins/package` ([#9644](https://github.com/pjgm/serverless/issues/9644)) ([db67b35](https://github.com/pjgm/serverless/commit/db67b353c9ed578d7dd334d162efa1ec11fbfa18))
* Use `async` in `lib/plugins/plugin` ([#9680](https://github.com/pjgm/serverless/issues/9680)) ([377da09](https://github.com/pjgm/serverless/commit/377da097c564778c8d2c42ffe49e38000c520106))
* Use `async` in `lib/utils` ([#9809](https://github.com/pjgm/serverless/issues/9809)) ([48c3d99](https://github.com/pjgm/serverless/commit/48c3d990beccef7dc3f4b5d29ec5bc4238fd9cf6))
* Use `download` from `@serverless/utils` ([716b312](https://github.com/pjgm/serverless/commit/716b31216e4873bbb986c5a2a54fda708a591cd1))
* Use `getCompiledTemplateS3Suffix` from `provider.naming` ([95d3024](https://github.com/pjgm/serverless/commit/95d3024ef55ce80edf20fe27d9c72ffd15bba2bb))
* Use async in `lib/plugins/aws/lib` ([#8872](https://github.com/pjgm/serverless/issues/8872)) ([489affc](https://github.com/pjgm/serverless/commit/489affcb520d8f50f87c84b932627812f491e66c))
* use gh-repo-to-user npm package instead of parsing url ([521212f](https://github.com/pjgm/serverless/commit/521212f28ef22014f4fbc6b4be5149f5d32e13e0))
* use lodash startCase instead of custom formatPluginName ([34f5ef6](https://github.com/pjgm/serverless/commit/34f5ef660f7c956d5cc093f55cf8afc4fddebd8c))
* use markdown-link npm package to render plugin link in readme ([9f1ec15](https://github.com/pjgm/serverless/commit/9f1ec154f422345fbdec9803ed700e99cc640721))
* use markdown-table npm package instead of string concat ([58ebd2a](https://github.com/pjgm/serverless/commit/58ebd2af7d01b7f767f3302c340b87737579d01b))
* Use object-param for `resolveImageUriAndShaFromPath` ([59fd478](https://github.com/pjgm/serverless/commit/59fd478550549518824704fa6b94f8e027d6b7f5))
* Use set instead of array ([b4e4fda](https://github.com/pjgm/serverless/commit/b4e4fdac71bedbc99a19a37b265ea1d8b17dd1c9))
* Use standalone `ServerlessError`. ([#8897](https://github.com/pjgm/serverless/issues/8897)) ([006557d](https://github.com/pjgm/serverless/commit/006557d8471623af7f6b83c58a14e9e4fe244507))
* Use templates from `examples` in `create` ([76a60ae](https://github.com/pjgm/serverless/commit/76a60ae2b769c73657770392806eb59cfbb4d186))
* **User Config:** Show config save error only with SLS_DEBUG=* ([bc04da5](https://github.com/pjgm/serverless/commit/bc04da5e41dd5f7aab1266340f04e8bb46355ae1)), closes [#7077](https://github.com/pjgm/serverless/issues/7077)
* **Variables:** Cleanup handling of `variableSyntax` default ([582d150](https://github.com/pjgm/serverless/commit/582d150ceb01d3f597a30fcc82201ffa325c4617))
* **Variables:** Cleanup logic ([c0f8459](https://github.com/pjgm/serverless/commit/c0f845968064852fd9f802f197cc41aa9ed801a9))
* **Variables:** Clear ineffective promise functions usage ([304f0ec](https://github.com/pjgm/serverless/commit/304f0ec2b913c0edf040017dbf78881e40887f0e))
* **Variables:** Configure `cf` source in a new resolver ([a60e90f](https://github.com/pjgm/serverless/commit/a60e90f61c93c177ade8a2875e94feb7e886a0e2))
* **Variables:** Configure `s3` source in a new resolver ([12a4cad](https://github.com/pjgm/serverless/commit/12a4cad102c67ecbdc308d35217a6247bd62dcb0))
* **Variables:** Configure `sls` source in a new resolver ([eecd928](https://github.com/pjgm/serverless/commit/eecd9285d51506d9a245b47b9afa6a16ffd64fe0))
* **Variables:** Configure `ssm` source in a new resolver ([3f7f67c](https://github.com/pjgm/serverless/commit/3f7f67ccc155d61ca9e7aa96c858058da55c635a))
* **Variables:** Configure dashboard sources in a new resolver ([385c15b](https://github.com/pjgm/serverless/commit/385c15bc83ca34fdde2da61533a8b163f7bcc33c))
* **Variables:** Do not handle resolution when no vars to resolve ([14ea1af](https://github.com/pjgm/serverless/commit/14ea1af886496fac53d4aaffe009ae78873c81bb))
* **Variables:** Do not run old resolver when no vars to resolve ([7aac480](https://github.com/pjgm/serverless/commit/7aac480fbb15d61a40320f98af4cee6f1b2475b3))
* **Variables:** Do not run old resolver when not needed ([7601e26](https://github.com/pjgm/serverless/commit/7601e26360226e77c4c8d631227a248e7a81afc2))
* **Variables:** Enable early `sls:stage` resolution ([56e9423](https://github.com/pjgm/serverless/commit/56e9423cd74dc05cc85b176bb1f0502f7ce05139))
* **Variables:** Ensure to mark `aws` as fulfilled source ([a4c9392](https://github.com/pjgm/serverless/commit/a4c93920830051ee67bebd0be815f8aa4c2ba234))
* **Variables:** Ensure to not resolve any value with promise ([54da2c2](https://github.com/pjgm/serverless/commit/54da2c23a13aafb7342915419c9a21ffc3705b37))
* **Variables:** Fix inline comment typo ([102d0ba](https://github.com/pjgm/serverless/commit/102d0bafe63c9ad0c824fb0d6e50e74ef5b4b550))
* **Variables:** Improve error message ([4a732e2](https://github.com/pjgm/serverless/commit/4a732e2ebf6c7d81f5e0fbdc2e9bcb4715e4cadf))
* **Variables:** Improve error message grammar ([089405a](https://github.com/pjgm/serverless/commit/089405a7a876e9f684fbb1e79998f3fabadc7eab))
* **Variables:** Improve error message related to JS func resolver ([b90538a](https://github.com/pjgm/serverless/commit/b90538af08a51a5e2a3ec65d6d1bf8c51a54b9c3))
* **Variables:** Improve error messages ([4184c1b](https://github.com/pjgm/serverless/commit/4184c1b1fe41ea44b625e7ddb31e147053bf2d7e))
* **Variables:** Improve error wording ([390e7d5](https://github.com/pjgm/serverless/commit/390e7d5f154efc23c9ca1e0df0b4ca078982c5ab))
* **Variables:** Improve logic order ([5419658](https://github.com/pjgm/serverless/commit/5419658ab25d2040397cbe7892a4a9aded6d650c))
* **Variables:** Improve reliability of tests ([ca045ba](https://github.com/pjgm/serverless/commit/ca045bae3e04f696057642a5a05acb14d7903da0))
* **Variables:** Improve source fulfillment handling ([524c43d](https://github.com/pjgm/serverless/commit/524c43df75606fdda0ec28c3370a0f743a9d1efa))
* **Variables:** Improve tests reliability ([971168d](https://github.com/pjgm/serverless/commit/971168dbe16ed22e216da1abadcd39605c1f9073))
* **Variables:** Make resolution error handler reusable ([452fdc2](https://github.com/pjgm/serverless/commit/452fdc2445e2c69a6c908f6b2b52c0659d87bbc0))
* **Variables:** Make resolverConfiguration reusable ([8e72247](https://github.com/pjgm/serverless/commit/8e722472cc23eac7b342b3e67434977cc69698aa))
* **Variables:** Optimize `provider.name` resolution handling ([6e1f5ed](https://github.com/pjgm/serverless/commit/6e1f5ed3f8fb76c5583b0f6f6bea086bf24ff6b4))
* **Variables:** Recognize only defined CLI options in resolver ([13610cf](https://github.com/pjgm/serverless/commit/13610cf0f0b89dc3061ae10254df291fc38c5e57))
* **Variables:** Reflect if/else logic in async handling ([31987ce](https://github.com/pjgm/serverless/commit/31987ce0722d6f711a031fb5e594d934ff75457a))
* **Variables:** Remove redundancy ([ac7efb1](https://github.com/pjgm/serverless/commit/ac7efb1b7b1a2ae4ba1ab6bb2d47c718dcb62a17))
* **Variables:** Report immediatelly eventual syntax errors ([ee01833](https://github.com/pjgm/serverless/commit/ee01833df80db8bc751f8248f49944738606393f))
* **Variables:** Resolve all env variables with new resolver ([c1d8b58](https://github.com/pjgm/serverless/commit/c1d8b58ed8a5a7a91d9dfa28536a9c0d997b809b))
* **Variables:** Seclude internal logic for reuse ([9c75044](https://github.com/pjgm/serverless/commit/9c75044fd59d8f181c7daee22d53a7bac3786e09))
* **Variables:** Seclude resolution of sources from external plugins ([6efc161](https://github.com/pjgm/serverless/commit/6efc161e5f7892275c798f6003ea5ee557bf3b26))
* **Variables:** Simply Array.from operation ([a867515](https://github.com/pjgm/serverless/commit/a867515bc0c7c0520a3928bf64ec1ec1e15cc564))
* **Variables:** Smarter "is property resolved" validation ([cfe83df](https://github.com/pjgm/serverless/commit/cfe83df1747732532d77d4ed52320aac70892da9))
* **Variables:** Smarter resolution phases ([a537856](https://github.com/pjgm/serverless/commit/a5378566516fd9cb1a9abdfc204c0a8c83841e4b))
* **Variables:** Support custom sources in internal resolver ([365a7f1](https://github.com/pjgm/serverless/commit/365a7f13afaf40e9e2d573b0668159d6dea7aa02))
* **Variables:** Testing purpose variable resolution util ([a2f1808](https://github.com/pjgm/serverless/commit/a2f1808b2f2a2cc7cb18a57ccc81c68e6a16dfc2))
* Wokaround AWS-SDK issue by temporarily pinning v2 version ([cb81085](https://github.com/pjgm/serverless/commit/cb810854a619429b8ec2a4c1dbbd77bb273d015d))

## [3.38.0](https://github.com/serverless/serverless/compare/v3.37.0...v3.38.0) (2023-11-21)

### Features

- Add support for provided.al2023 runtime ([#12263](https://github.com/serverless/serverless/issues/12263)) ([6cdf14e](https://github.com/serverless/serverless/commit/6cdf14e7a81016a69c18d7a1fa6ba293cc3b2a6b))

## [3.37.0](https://github.com/serverless/serverless/compare/v3.36.0...v3.37.0) (2023-11-16)

### Features

- Add support for nodejs20.x runtime ([#12251](https://github.com/serverless/serverless/issues/12251)) ([f3f0af8](https://github.com/serverless/serverless/commit/f3f0af85f0783451b7fdf9216d9ab8536853fa46))

### Bug Fixes

- bump platform-client version for axios ([#12260](https://github.com/serverless/serverless/issues/12260)) ([10980b9](https://github.com/serverless/serverless/commit/10980b9578cb4da6820300b69ae2f001feb1f38e))
- Update pkg config to include axios cjs ([#12261](https://github.com/serverless/serverless/issues/12261)) ([b21afaf](https://github.com/serverless/serverless/commit/b21afaf9cf97224d36234b02e3e872bc115f7dc9))

## [3.36.0](https://github.com/serverless/serverless/compare/v3.35.2...v3.36.0) (2023-10-23)

### Features

- Improved dashboard documentation and gitignore ([#12176](https://github.com/serverless/serverless/issues/12176)) ([eb462ed](https://github.com/serverless/serverless/commit/eb462edc18de633bb0e479423babcbb43d4c3a33))

### Bug Fixes

- Dashboard documentation improvements ([bb4d7c8](https://github.com/serverless/serverless/commit/bb4d7c8938c3eff0b8412137e25c352327650fa5))
- Fix menu for dashboard documentation ([8f266af](https://github.com/serverless/serverless/commit/8f266af8308fa9b89327792dd037c4fe14bb14af))
- Improve dashboard documentation ([ad8bbf1](https://github.com/serverless/serverless/commit/ad8bbf1e13d9ba641f65a42ce95d2b0af7e1b4dd))
- Improve dashboard documentation ([f67df7f](https://github.com/serverless/serverless/commit/f67df7fd1b409df512673ab4a795657a3d90fa6f))
- Minor dashboard doc improvements ([#12177](https://github.com/serverless/serverless/issues/12177)) ([f1fa19c](https://github.com/serverless/serverless/commit/f1fa19c7e02a49edaf813aac60e8622486c4b9cc))

### [3.35.2](https://github.com/serverless/serverless/compare/v3.35.1...v3.35.2) (2023-09-16)

### Bug Fixes

- Adjust copy for clarity ([#12162](https://github.com/serverless/serverless/issues/12162)) ([101ce53](https://github.com/serverless/serverless/commit/101ce53c18bae3709d5cc70a483cce81206752ec))

### [3.35.1](https://github.com/serverless/serverless/compare/v3.35.0...v3.35.1) (2023-09-16)

### Bug Fixes

- Do not use isDashboard in onboarding flow ([#12160](https://github.com/serverless/serverless/issues/12160)) ([1f8d786](https://github.com/serverless/serverless/commit/1f8d786b16d7682912c464d67add589f48666987))

## [3.35.0](https://github.com/serverless/serverless/compare/v3.34.0...v3.35.0) (2023-09-15)

### Features

- Make dashboard monitoring opt-out ([#12138](https://github.com/serverless/serverless/issues/12138)) ([45cbd52](https://github.com/serverless/serverless/commit/45cbd525014ad3bf60aac3d482ec76ce68b51820))
- Post deploy serverless dashboard integration ([#12063](https://github.com/serverless/serverless/issues/12063)) ([66e3107](https://github.com/serverless/serverless/commit/66e31077a71c61854db3246a50ddd2c1c303c110)), closes [#12059](https://github.com/serverless/serverless/issues/12059)
- Remove Console Login ([#12153](https://github.com/serverless/serverless/issues/12153)) ([590bb7e](https://github.com/serverless/serverless/commit/590bb7e17717253bfa37b1b511e5a6610c5657cb))
- Remove Dashboard onboarding from framework ([#12151](https://github.com/serverless/serverless/issues/12151)) ([6ee277d](https://github.com/serverless/serverless/commit/6ee277dfcb0d9055a3b20cbf493b1fd79b524fd2))
- Upgrade to @serverless/dashboard-plugin ([#12157](https://github.com/serverless/serverless/issues/12157)) ([f057629](https://github.com/serverless/serverless/commit/f057629cbebf07f3415ef996ecbc10c7c7b866d4))

### Bug Fixes

- Adjust providers endpoint ([#12154](https://github.com/serverless/serverless/issues/12154)) ([9b770a2](https://github.com/serverless/serverless/commit/9b770a27dc0a093d05d36e58f077b3a527565718)), closes [#12151](https://github.com/serverless/serverless/issues/12151)
- Check for Serverless Dashboard IAM stack prior to creation ([#12147](https://github.com/serverless/serverless/issues/12147)) ([bf518b9](https://github.com/serverless/serverless/commit/bf518b9135997c67ea940ff396af14a4b4b62948))
- Handle account being integrated with an existing org ([#12149](https://github.com/serverless/serverless/issues/12149)) ([561a875](https://github.com/serverless/serverless/commit/561a875da767a23e6bc1cc314e726ff674ab9df1))
- Local credentials should be resolved in onboarding command ([#12148](https://github.com/serverless/serverless/issues/12148)) ([307865d](https://github.com/serverless/serverless/commit/307865d0525d551f188a1c86399533f78d7b15c3))
- recognize ap-south-2 as a valid AWS region ([#12129](https://github.com/serverless/serverless/issues/12129)) ([b09d0d6](https://github.com/serverless/serverless/commit/b09d0d62677c09c4905b65bcaf6ba61aa8d8204c))

### [3.34.0](https://github.com/serverless/serverless/compare/v3.33.0...v3.34.0) (2023-08-03)

### Features

- Python 3.11 support ([#12085](https://github.com/serverless/serverless/issues/12085)) ([f5d143a](https://github.com/serverless/serverless/commit/f5d143ac3935260dc0f647a541f22dbbd583095f))

### Bug Fixes

- **AWS Schedule:** Fix IAM role assignment ([#12030](https://github.com/serverless/serverless/issues/12030)) ([e1039de](https://github.com/serverless/serverless/commit/e1039ded5c5e35595b5d4c59e81d480a16c4dd67))

### Maintenance Improvements

- Remove `got` dependency ([#12040](https://github.com/serverless/serverless/issues/12040)) ([1775c90](https://github.com/serverless/serverless/commit/1775c90a72ec321af8673bcdd1901cb1e48b9169))

## [3.33.0](https://github.com/serverless/serverless/compare/v3.32.2...v3.33.0) (2023-06-26)

### Features

- **AWS Deploy:** Recognize `ruby3.2` runtime ([#12004](https://github.com/serverless/serverless/issues/12004)) ([0a0a4fc](https://github.com/serverless/serverless/commit/0a0a4fc8af4c88a2a2d85401b3fb89341b927f47)) ([Ryan Rickerts](https://github.com/theRocket))
- **AWS MSK:** Support `AT_TIMESTAMP` starting position ([#12034](https://github.com/serverless/serverless/issues/12034)) ([483ea16](https://github.com/serverless/serverless/commit/483ea166fc6af2bed363a2a9ebf3ec8d06900618)) ([Ben](https://github.com/griffithsbs))

### Bug Fixes

- **AWS ALB:** Recognize CIDR format at `ip` configuration ([#11889](https://github.com/serverless/serverless/issues/11889)) ([04db0f0](https://github.com/serverless/serverless/commit/04db0f045c3d6e3772ef9f82ca4d51ac1aa5bbb8)) ([Inqnuam](https://github.com/Inqnuam))
- **AWS Websocket:** Fix internal authorizers handling ([#11871](https://github.com/serverless/serverless/issues/11871)) ([a50773b](https://github.com/serverless/serverless/commit/a50773b60d0c528ad7734dfa4a84cd9dc109f7e1)) ([James Kyburz](https://github.com/JamesKyburz))
- **Packaging:** Fix merging `DependsOn` from user resources ([#12009](https://github.com/serverless/serverless/issues/12009)) ([4582913](https://github.com/serverless/serverless/commit/4582913214e1c9d6f4324ff6a507dd09a2fd4e1b)) ([Kirill Khoroshilov](https://github.com/Hokid))

### [3.32.2](https://github.com/serverless/serverless/compare/v3.32.1...v3.32.2) (2023-06-02)

### Maintenance Improvements

- **Telemetry:** Report installed `docker` version ([39806d6](https://github.com/serverless/serverless/commit/39806d622fdc1d8dae7618394ffe12bbe702675d)) ([Mariusz Nowak](https://github.com/medikoo))

### [3.32.1](https://github.com/serverless/serverless/compare/v3.32.0...v3.32.1) (2023-06-01)

### Bug Fixes

- **AWS Deploy:** Revert broken `vpc` configuration on custom resources ([#12001](https://github.com/serverless/serverless/issues/12001)) ([d0e3056](https://github.com/serverless/serverless/commit/d0e3056b77ba295adb87ceeca9a49a26b315f083)) ([Mariusz Nowak](https://github.com/medikoo))

## [3.32.0](https://github.com/serverless/serverless/compare/v3.31.0...v3.32.0) (2023-05-31)

### Features

- **AWS Lambda:**
  - Response streaming for Lambda URL ([#11907](https://github.com/serverless/serverless/issues/11907)) ([3afb71e](https://github.com/serverless/serverless/commit/3afb71e39d144e8ed6b7634f50a3d8fe8e27daed)) ([Goran Rakic](https://github.com/grakic))
  - Do not recognize dropped `nodejs12.x` runtime ([#11995](https://github.com/serverless/serverless/issues/11995)) ([032e43c](https://github.com/serverless/serverless/commit/032e43c77d935b398b162311fa8c37d79a62b20e)) ([Mariusz Nowak](https://github.com/medikoo))
- **AWS Deploy:** `--minify-template` CLI param ([#11980](https://github.com/serverless/serverless/issues/11980)) ([4d64730](https://github.com/serverless/serverless/commit/4d64730130c44cdfbb872f8a16111df409135dc8)) ([Mieszko Kycermann](https://github.com/Kycermann))

### Bug Fixes

- **AWS ALB:** Allow multiple http-header conditions ([#11888](https://github.com/serverless/serverless/issues/11888)) ([72b27cb](https://github.com/serverless/serverless/commit/72b27cb4fe0e17bf980fcc441808f4db6939e545)) ([Inqnuam](https://github.com/Inqnuam))
- **AWS CloudFront:** Accept CF intrinsic functions in `behavior` ([#11994](https://github.com/serverless/serverless/issues/11994)) ([41e90c3](https://github.com/serverless/serverless/commit/41e90c304306aabca1879ebba542328460bf2133)) ([antoniogomezm](https://github.com/AntonioGM))
- **AWS Deploy:**
  - Ensure `vpc` configuration on custom resources ([#11985](https://github.com/serverless/serverless/issues/11985)) ([f2d1e23](https://github.com/serverless/serverless/commit/f2d1e23f591a8cae2d41a93ca476b135dfcdac68)) ([Lokesh Jawale](https://github.com/Lokesh-Jawale))
  - Fix default runtime resolution ([#11995](https://github.com/serverless/serverless/issues/11995)) ([943bf6d](https://github.com/serverless/serverless/commit/943bf6dfad3750dabd4754708a3649da9798984c)) ([Mariusz Nowak](https://github.com/medikoo))
- **AWS Lambda:** Recognize only valid .NET runtimes ([#11960](https://github.com/serverless/serverless/issues/11960)) ([dd081bb](https://github.com/serverless/serverless/commit/dd081bbc4189e3b4757b8e704d048191e59a932f)) ([Stuart Lang](https://github.com/slang25))

### Maintenance Improvements

- **Telemetry:** Inspect `docker` availability ([#11999](https://github.com/serverless/serverless/issues/11999)) ([83670f9](https://github.com/serverless/serverless/commit/83670f98c54b71670d0f6d677b1f23b0fb5200ce)) ([Mariusz Nowak](https://github.com/medikoo))
- **Console:** Added warning about dev mode ([#11975](https://github.com/serverless/serverless/issues/11975)) ([e5cb8ac](https://github.com/serverless/serverless/commit/e5cb8acbf238d3a31ca6ae98283b6edc1734098e)) ([Dan Jarvis](https://github.com/Danwakeem))
- **Packaging:** Warn on inffective `functions[].package` config ([#11974](https://github.com/serverless/serverless/issues/11974)) ([88099ad](https://github.com/serverless/serverless/commit/88099ad98c33ed97b1cf0471de03247c33928af0)) ([Lokesh Jawale](https://github.com/Lokesh-Jawale))

## [3.31.0](https://github.com/serverless/serverless/compare/v3.30.1...v3.31.0) (2023-05-17)

### Features

- **AWS Schedule:** `AWS::Scheduler::Schedule` based triggers ([#11935](https://github.com/serverless/serverless/issues/11935)) ([34d922d](https://github.com/serverless/serverless/commit/34d922d3d8d33f6e17e697610fdef7f13003a2f3)) ([Tie](https://github.com/tie624))
- **AWS Kinesis:** More reliable consumer naming mode ([#9706](https://github.com/serverless/serverless/issues/9706)) ([9d7b121](https://github.com/serverless/serverless/commit/9d7b121bd1b1ff0f3adcc14bf3dfecf27d589c0f)) ([Peter Reshetin](https://github.com/preshetin))
- **AWS Lambda:**
  - Recognize `java17` runtime ([#11938](https://github.com/serverless/serverless/issues/11938)) ([e1703c8](https://github.com/serverless/serverless/commit/e1703c8551eaa7051274cf83f302de20264f345e)) ([Baerten Dennis](https://github.com/debae))
  - Recognize `python3.10` runtime ([#11922](https://github.com/serverless/serverless/issues/11922)) ([8341d7a](https://github.com/serverless/serverless/commit/8341d7ae736e9e79b83027e5b160307a3641e94a)) ([t3yamoto](https://github.com/t3yamoto))
  - Recognize new .NET runtimes ([#11941](https://github.com/serverless/serverless/issues/11941)) ([314f32c](https://github.com/serverless/serverless/commit/314f32cd2bc249ddeae9e6fe2cd00c59be515796)) ([Graham Campbell](https://github.com/GrahamCampbell))
- **AWS EventBridge:** Recognize `$or` in pattern property ([#11967](https://github.com/serverless/serverless/issues/11967)) ([d6de334](https://github.com/serverless/serverless/commit/d6de3346ce962392c053f7f6480f52dcdb918624)) ([Mitch Dempsey](https://github.com/webdestroya))

### Bug Fixes

- **AWS CloudWatch:** Ensure no circular resource references ([#11893](https://github.com/serverless/serverless/issues/11893)) ([75ce58b](https://github.com/serverless/serverless/commit/75ce58b194f19b4fc5a37a7a437733befefccf06)) ([Rob Nielsen](https://github.com/rnielsen))
- **AWS Deploy:** Fix `provider.layers` support in `deploy function` cmd ([#11972](https://github.com/serverless/serverless/issues/11972)) ([ed15cb2](https://github.com/serverless/serverless/commit/ed15cb27aee68954c93d875da96274914943ad71)) ([Mariusz Nowak](https://github.com/medikoo))

### Maintenance Improvements

- **AWS Lambda:** Remove references to deprecated runtimes ([#11940](https://github.com/serverless/serverless/issues/11940)) ([fe6e0a6](https://github.com/serverless/serverless/commit/fe6e0a69ee167f52d036e8fde405184961a04a42)) ([Bartłomiej Szostek](https://github.com/bartelemi))

### [3.30.1](https://github.com/serverless/serverless/compare/v3.30.0...v3.30.1) (2023-04-06)

### Bug Fixes

- Ensure to not login back accidentaly on logout operation ([#11900](https://github.com/serverless/serverless/issues/11900)) ([ec9eac4](https://github.com/serverless/serverless/commit/ec9eac4edc6ebeded0276eeb12c7f77a7a7f7eda)) ([Mariusz Nowak](https://github.com/medikoo))

## [3.30.0](https://github.com/serverless/serverless/compare/v3.29.0...v3.30.0) (2023-04-05)

### Features

- Console Dev Mode onboarding via `dev` command ([#11896](https://github.com/serverless/serverless/issues/11896)) ([73d0dc6](https://github.com/serverless/serverless/commit/73d0dc6cf4e98d9c27f3fd6edb439d36e030c051))

### Bug Fixes

- **AWS Deploy:** Fix handling of inactive CloudFormation stack state ([0d850fc](https://github.com/serverless/serverless/commit/0d850fcca70d329a0d597d29cb985abd418bd955)), closes [#11863](https://github.com/serverless/serverless/issues/11863)

### Maintenance Improvements

- Remove `BbPromise.bind` usage ([#11875](https://github.com/serverless/serverless/issues/11875)) ([30dd50a](https://github.com/serverless/serverless/commit/30dd50a90cf5ae32ae87b85aae31c2d29cf464d5))

## [3.29.0](https://github.com/serverless/serverless/compare/v3.28.1...v3.29.0) (2023-03-24)

### Features

- **Console:** Retain console properties on function deploy ([#11849](https://github.com/serverless/serverless/issues/11849)) ([4ee5505](https://github.com/serverless/serverless/commit/4ee5505b18bf6ca4ac83f411d76d71c45dc9fb18)) ([](https://github.com/)) ([Dan Jarvis](https://github.com/Danwakeem))
- **AWS CLoudFront:** Recognize `OriginAccessControlId` field ([#11855](https://github.com/serverless/serverless/issues/11855)) ([9339377](https://github.com/serverless/serverless/commit/93393777cb5e170bedb5f1a390a544c300ed4101)) ([Jonathan Keslin](https://github.com/decompil3d))
- **AWS EventBridge:** Support `description` property ([#11821](https://github.com/serverless/serverless/issues/11821)) ([2efe816](https://github.com/serverless/serverless/commit/2efe8169c9abf5f4f3652774f5055e60b21dd721)) ([Anthony Roussel](https://github.com/anthonyroussel))

### Bug Fixes

- **AWS Lambda:**
  - Fix function references when represented by alias ([#11788](https://github.com/serverless/serverless/issues/11788)) ([16dd286](https://github.com/serverless/serverless/commit/16dd286a1d8aa764003565bcd6d7334be290e9bf)) ([Rob Nielsen](https://github.com/rnielsen))
  - Fix `runtimeManagment` handling ([#11778](https://github.com/serverless/serverless/issues/11778)) ([8db2f4c](https://github.com/serverless/serverless/commit/8db2f4cbc56a46110d82e3d36e8a63f50e06d495)) ([Himanshu Pant](https://github.com/KillDozerX2))
- **AWS API Gateway:** Fix support for `provider.apiGateway.stage` ([#11772](https://github.com/serverless/serverless/issues/11772)) ([6fe2ea5](https://github.com/serverless/serverless/commit/6fe2ea5bc84c01434ba6f044d8ab3623dea85574)) ([Charlie Benger-Stevenson](https://github.com/suityou01))
- Do not crash on `null` resource properties input ([#11789](https://github.com/serverless/serverless/issues/11789)) ([86bb67d](https://github.com/serverless/serverless/commit/86bb67d15fe611cdaffb6aea57d25cb0cfc51029)) ([SleepWithCoffee](https://github.com/sleepwithcoffee))

### Maintenance Improvements

- **AWS Lambda:** Improve function deploy skip message ([#11779](https://github.com/serverless/serverless/issues/11779)) ([ad8c24e](https://github.com/serverless/serverless/commit/ad8c24ecfca4ec9dea87d9114ad3f2afcab85ae2)) ([Midhun Rajendran](https://github.com/rmidhun23))
- **`lodash` replacement:**
  - Replace `_.entries` with `Object.entries` ([#11793](https://github.com/serverless/serverless/issues/11793)) ([1181780](https://github.com/serverless/serverless/commit/11817802654a8bb28e8664ab6d9f346ebaf97e1e)) ([SleepWithCoffee](https://github.com/sleepwithcoffee))
  - Replace `_.fromPairs` with `Object.fromEntries` ([#11794](https://github.com/serverless/serverless/issues/11794)) ([03d3ab3](https://github.com/serverless/serverless/commit/03d3ab39da1096aae4d797675793523726f6c1b6)) ([SleepWithCoffee](https://github.com/sleepwithcoffee))
- **`bluebird` replacement:**
  - Replace `BbPromise.each` with native counterpart ([#11797](https://github.com/serverless/serverless/issues/11797)) ([5068516](https://github.com/serverless/serverless/commit/5068516f0424ab1b8c94f4b698234ace36a674cd)) ([SleepWithCoffee](https://github.com/sleepwithcoffee))
- ** `async/await` refactor:**
  - In `lib/classes` convert promise returning functions to async functions ([#11851](https://github.com/serverless/serverless/issues/11851)) ([77c91f2](https://github.com/serverless/serverless/commit/77c91f27d6f3234853550febfb7f14a32a69cc60)) ([SleepWithCoffee](https://github.com/sleepwithcoffee))

### [3.28.1](https://github.com/serverless/serverless/compare/v3.28.0...v3.28.1) (2023-03-02)

### Maintenance Improvements

- Supress AWS SDK v2 deprecation message ([#11769](https://github.com/serverless/serverless/issues/11769)) ([74c3ae0](https://github.com/serverless/serverless/commit/74c3ae004c7166c76fe5355a778fe1f5f9c401b0)) ([Mariusz Nowak](https://github.com/medikoo))

## [3.28.0](https://github.com/serverless/serverless/compare/v3.27.0...v3.28.0) (2023-02-28)

### Features

- **AWS Lambda:**
  - Ensure `logs:TagResource` permission to IAM role ([#11766](https://github.com/serverless/serverless/issues/11766)) ([7410275](https://github.com/serverless/serverless/commit/7410275f66292a67a2d4972d43542f450a687477)) ([Martin Gerlach](https://github.com/mgerlach))
  - Recognize CF functions at `.provisionedConcurrency` ([#11760](https://github.com/serverless/serverless/issues/11760)) ([56d8bec](https://github.com/serverless/serverless/commit/56d8bec84981952497e6db1858af80dd9cf224f1)) ([ROSeaboyer](https://github.com/ROSeaboyer))
  - Support `runtimeManagement` config ([#11715](https://github.com/serverless/serverless/issues/11715)) ([18d4d69](https://github.com/serverless/serverless/commit/18d4d69eb3b1220814ab031690b6ef899280a93a)) ([ROSeaboyer](https://github.com/ROSeaboyer))
- **AWS Schedule:** Support CF instrinsic functions at `.rate` ([#11714](https://github.com/serverless/serverless/issues/11714)) ([fc6bd57](https://github.com/serverless/serverless/commit/fc6bd57bbf18898976f6caa18e310cbd921a7270)) ([ROSeaboyer](https://github.com/ROSeaboyer))

### Bug Fixes

- **CLI Onboarding:** Don't crash if Dashboard server is inaccessible ([#11712](https://github.com/serverless/serverless/issues/11712)) ([983a3b9](https://github.com/serverless/serverless/commit/983a3b9be6af1e156b0793afbf19f1d81282e6d1)) ([Mariusz Nowak](https://github.com/medikoo))

## [3.27.0](https://github.com/serverless/serverless/compare/v3.26.0...v3.27.0) (2023-01-26)

### Features

- **AWS EventBridge:** Support `functions[].events[].eventBridge.name` ([#11690](https://github.com/serverless/serverless/issues/11690)) ([b925c4c](https://github.com/serverless/serverless/commit/b925c4cf9c2f6a2dddf9eae10b0e62a88f40ff41)) ([ROSeaboyer](https://github.com/ROSeaboyer))
- **AWS ActiveMQ:** Support `functions[].events[].filterPatterns` ([#11656](https://github.com/serverless/serverless/issues/11656)) ([1b55710](https://github.com/serverless/serverless/commit/1b55710f0a869aff2b0d5dfc499a487eb62d204d)) ([Shreyance Jain](https://github.com/shreyance-jain))
- **AWS Kafka:** Support `functions[].events[].filterPatterns` ([#11645](https://github.com/serverless/serverless/issues/11645)) ([6a5e8d9](https://github.com/serverless/serverless/commit/6a5e8d9ff3ce3cd526470ef3418f3e08c9d3dc76)) ([Jason Rowsell](https://github.com/jasonrowsell))
- **AWS MSK:** Support `functions[].events[].filterPatterns` ([#11636](https://github.com/serverless/serverless/issues/11636)) ([63584a9](https://github.com/serverless/serverless/commit/63584a9a0d1a9523c23367de47e7fe575c5cf12b)) ([Shreyance Jain](https://github.com/shreyance-jain))
- **AWS RabbitMQ:** Support `functions[].events[].filterPatterns` ([#11659](https://github.com/serverless/serverless/issues/11659)) ([e769570](https://github.com/serverless/serverless/commit/e769570704fee372c2fa849c332d476d38e858be)) ([Shreyance Jain](https://github.com/shreyance-jain))
- **AWS CloudFront:** Recognize `behavior.ResponseHeadersPolicyId` ([#11633](https://github.com/serverless/serverless/issues/11633)) ([906ea31](https://github.com/serverless/serverless/commit/906ea319dd1486f79d6e088a999fd5634526c4bc)) ([Jason Rowsell](https://github.com/jasonrowsell))
- **AWS SNS:** Support `functions[].events[].filterPolicyScope` ([#11644](https://github.com/serverless/serverless/issues/11644)) ([b7d6af6](https://github.com/serverless/serverless/commit/b7d6af6b1309a5b4fbfac54265e7900196416976)) ([Jason Rowsell](https://github.com/jasonrowsell))
- **AWS SQS:** Support `functions[].events[].sqs.maximumConcurrency` ([#11678](https://github.com/serverless/serverless/issues/11678)) ([57f2719](https://github.com/serverless/serverless/commit/57f27193e052b01cd67745c7576f77b2d8988a6f)) ([Jason Rowsell](https://github.com/jasonrowsell))
- **AWS Lambda:** Recognize `ap-southeast-4` Melbourne region ([#11700](https://github.com/serverless/serverless/issues/11700)) ([6591504](https://github.com/serverless/serverless/commit/6591504000f16974f83db1fb0b599fdacf688c52)) ([Sam Chung](https://github.com/samchungy))
- Recognize `Fn::Base64` as CloudFormation instruction ([#11671](https://github.com/serverless/serverless/issues/11671)) ([f020bd8](https://github.com/serverless/serverless/commit/f020bd823905f012d2936a876e0ea841f5688883)) ([Ron Korving](https://github.com/mt-ronkorving))
- Remove support for Serverless Tencent CLI ([#11658](https://github.com/serverless/serverless/issues/11658)) ([0a148b4](https://github.com/serverless/serverless/commit/0a148b444c535df262bf79111066df03216f2f58)) ([Mariusz Nowak](https://github.com/medikoo))

### Maintenance Improvements

- **AWS SQS:** Optimize IAM permissions generation ([#11685](https://github.com/serverless/serverless/issues/11685)) ([99cd9e6](https://github.com/serverless/serverless/commit/99cd9e69c14583c428c4fdb01496151c9582eb5b)) ([ROSeaboyer](https://github.com/ROSeaboyer))
- **Console:** Improve warning message ([#117009](https://github.com/serverless/serverless/issues/11709)) ([2198799](https://github.com/serverless/serverless/commit/2198799f73e9fdbbdc377c8effcea8f1a933eff7)) ([Mariusz Nowak](https://github.com/medikoo))

## [3.26.0](https://github.com/serverless/serverless/compare/v3.25.1...v3.26.0) (2022-12-22)

### Features

- **Plugins:** Support variables in configuration extensions ([#11558](https://github.com/serverless/serverless/issues/11558)) ([968ddd5](https://github.com/serverless/serverless/commit/968ddd5994750a6d1677f195f7a86a823c558d16)) ([Marco Kleinlein](https://github.com/mklenbw))
- **AWS Lambda:** `functions[].snapStart` support ([#11576](https://github.com/serverless/serverless/issues/11576)) ([adf11b7](https://github.com/serverless/serverless/commit/adf11b75e51aefe468005d9daa656377f02ae5ac)) ([Baerten Dennis](https://github.com/debae))
- `provider.logDataProtectionPolicy` and `functions[].logDataProtectionPolicy` ([#11599](https://github.com/serverless/serverless/issues/11599)) ([2a5e11a](https://github.com/serverless/serverless/commit/2a5e11a9977708504e95e011f1cf401a43b94237)) ([timo92](https://github.com/timo92))
- Support `.cjs` and `.mjs` configuration extensions ([#11586](https://github.com/serverless/serverless/issues/11586)) ([9d57933](https://github.com/serverless/serverless/commit/9d579336fadea1080f86f85e3fc304a102ab07f6)) ([Florian Proksch](https://github.com/RianFuro))

### Bug Fixes

- **Variables:** Support empty string environment variables ([#11629](https://github.com/serverless/serverless/issues/11629)) ([022db9c](https://github.com/serverless/serverless/commit/022db9c8a309fcd7cd58bf7d6fc066acd411a679)) ([Jason Rowsell](https://github.com/jasonrowsell))
- **AWS Local Invoke:** Revert breaking jackson-databind upgrade ([#11589](https://github.com/serverless/serverless/issues/11589)) ([f00eb82](https://github.com/serverless/serverless/commit/f00eb824c201a09206337a34aab700500314fe50)) ([Geoff Denning](https://github.com/gdenning))

### Maintenance Improvements

- Isolate `import` invocations ([#11587](https://github.com/serverless/serverless/issues/11587)) ([fe62096](https://github.com/serverless/serverless/commit/fe620965838b2fce2a0aa3f9c8aaaf47e4faf755)) ([Mariusz Nowak](https://github.com/medikoo))
- Remove no longer applicable setting ([#11608](https://github.com/serverless/serverless/issues/11608)) ([dd5b8f6](https://github.com/serverless/serverless/commit/dd5b8f61de487d67f0cc15036be754816f7fa234)) ([Mariusz Nowak](https://github.com/medikoo))
- Support relative paths in `import-esm` util ([#11593](https://github.com/serverless/serverless/issues/11593)) ([fcf17a6](https://github.com/serverless/serverless/commit/fcf17a608d3a24d18cac4705d412366e27a1f2d1)) ([Mariusz Nowak](https://github.com/medikoo))
- Improve module name ([#11587](https://github.com/serverless/serverless/issues/11587)) ([ac1e0db](https://github.com/serverless/serverless/commit/ac1e0dbfa1f507e1bcdc30163e238bd412274a5d)) ([Mariusz Nowak](https://github.com/medikoo))

## [3.25.1](https://github.com/serverless/serverless/compare/v3.25.0...v3.25.1) (2022-11-28)

### Maintenance Improvements

- Wokaround AWS-SDK issue by temporarily pinning v2 version ([cb81085](https://github.com/serverless/serverless/commit/cb810854a619429b8ec2a4c1dbbd77bb273d015d)) ([Mariusz Nowak](https://github.com/medikoo))
- **AWS Local Invocation:** Upgrade Java dependencies ([#11535](https://github.com/serverless/serverless/issues/11535)) ([eb741fe](https://github.com/serverless/serverless/commit/eb741fed22773f6b4b08a67837ab39a518101825)) ([xiaokang](https://github.com/pen4))

## [3.25.0](https://github.com/serverless/serverless/compare/v3.24.1...v3.25.0) (2022-11-21)

### Features

- **AWS Deploy:**
  - Recognize `nodejs.18.x` runtime ([#11526](https://github.com/serverless/serverless/issues/11526)) ([c25f854](https://github.com/serverless/serverless/commit/c25f854f29204d1fb6c6254ae89d020751aa8198)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Recognize `eu-central-2`, `eu-south-1` and `me-central-1` regions ([#11524](https://github.com/serverless/serverless/issues/11524)) ([54f4fc7](https://github.com/serverless/serverless/commit/54f4fc73b4a2277c7485b877e57ec9ced6e66d1a)) ([Umut Uzgur](https://github.com/umutuzgur))
- **AWS API Gateway:** Allow CloudFormation intrinsic functions in `authorizer.scopes` ([#11505](https://github.com/serverless/serverless/issues/11505)) ([4169ae1](https://github.com/serverless/serverless/commit/4169ae183f64c5c580d90e653e23cc3c52a6f971)) ([franzmango](https://github.com/franzmango))
- **AWS Kafka:** Support `startingPositionTimestamp` ([#11479](https://github.com/serverless/serverless/issues/11479)) ([858758e](https://github.com/serverless/serverless/commit/858758ea1efed07f38e491d21ecfd9873f07b4dd)) ([Daniele Iasella](https://github.com/overbit))

### Bug Fixes

- **AWS Deploy:** Respect existing CloudFormation templates in YAML format ([#11521](https://github.com/serverless/serverless/issues/11521)) ([20d79a2](https://github.com/serverless/serverless/commit/20d79a2876875f73755ccae4e1e2c2a9c02c9ad7)) ([Nick Graffis](https://github.com/nickgraffis))
- Do not crash on `null` value ([#11506](https://github.com/serverless/serverless/issues/11506)) ([c4902f3](https://github.com/serverless/serverless/commit/c4902f3b103e3c683eb2a8dd04acc4e217a4d276)) ([Shogo Hida](https://github.com/shogohida))

### [3.24.1](https://github.com/serverless/serverless/compare/v3.24.0...v3.24.1) (2022-11-04)

### Bug Fixes

- **Console:** Ensure errorneus resolution of url to not break deploys ([#11501](https://github.com/serverless/serverless/issues/11501)) ([f72c595](https://github.com/serverless/serverless/commit/f72c5958c354c47123427988f6a48528987c45cb)) ([Mariusz Nowak](https://github.com/medikoo))

## [3.24.0](https://github.com/serverless/serverless/compare/v3.23.0...v3.24.0) (2022-10-31)

### Features

- **Console:** New Serverless Console integration ([#11434](https://github.com/serverless/serverless/issues/11434)) ([9a41468](https://github.com/serverless/serverless/commit/9a414683090cb3edcac61d9a782c4d136f18c6f6)) ([Mariusz Nowak](https://github.com/medikoo))
- **AWS API Gateway:** support `provider.apiGateway.stage` ([#11487](https://github.com/serverless/serverless/issues/11487)) ([0a49c4f](https://github.com/serverless/serverless/commit/0a49c4f5df8ef4942ac4758b62a8de5dfc4bf4d8)) ([Pavan Andhukuri](https://github.com/pavanandhukuri))
- **AWS Kinesis:** Support `AT_TIMESTAMP` starting position ([#11483](https://github.com/serverless/serverless/issues/11483)) ([5d41995](https://github.com/serverless/serverless/commit/5d41995c1939955e48cea0660dac5c32446f7b58)) ([Daniele Iasella](https://github.com/overbit))
- Support `Fn::ToJsonString` in environment variables ([#11461](https://github.com/serverless/serverless/issues/11461)) ([0c186a6](https://github.com/serverless/serverless/commit/0c186a608fd1a754a65abf63e431ad9c2d13534e)) ([Jurriaan Proos](https://github.com/jurriaanpro))

### Bug Fixes

- **AWS HTTP API:** Ensure maximum API gateway timeout ([#11453](https://github.com/serverless/serverless/issues/11453)) ([c5ca9b7](https://github.com/serverless/serverless/commit/c5ca9b78faef8bc6c23b215f847dc4383b8165e7)) ([Jurriaan Proos](https://github.com/jurriaanpro))
- **CLI Onboarding:** Ensure to not show backend notification ([#11434](https://github.com/serverless/serverless/issues/11434)) ([ba831b8](https://github.com/serverless/serverless/commit/ba831b8b3e4a9371091db9e709545adba324d822)) ([Mariusz Nowak](https://github.com/medikoo))

### Maintenance Improvements

- **CLI Onboarding:** Improve debug logs ([#11434](https://github.com/serverless/serverless/issues/11434)) ([914d00b](https://github.com/serverless/serverless/commit/914d00b0a9758b4b799242efad6e66c98e1c7160)) ([Mariusz Nowak](https://github.com/medikoo))

## [3.23.0](https://github.com/serverless/serverless/compare/v3.22.0...v3.23.0) (2022-10-11)

### Features

- **AWS CloudFront:** Allow legacy behavior configuration ([#11411](https://github.com/serverless/serverless/issues/11411)) ([65e9860](https://github.com/serverless/serverless/commit/65e9860838de40c8ef0189c723e09936c8ca71a7)) ([Arthur Weber](https://github.com/godu))
- **AWS Kafka:** Support `consumerGroupId` option ([#11345](https://github.com/serverless/serverless/issues/11345)) ([9bb3f11](https://github.com/serverless/serverless/commit/9bb3f1154151b1e1a4ca24addd034cf59deb2037)) ([Phil-Pinkowski](https://github.com/Phil-Pinkowski))

### Bug Fixes

- Ensure to not crash when `~/.serverless` is not accessible ([#11403](https://github.com/serverless/serverless/issues/11403)) ([b95c749](https://github.com/serverless/serverless/commit/b95c7496ec4a49aef756692a1ef59b61e2d95d4b)) ([Thomas Hamer](https://github.com/THOM-AwS))

### Maintenance Improvements

- **AWS Deploy:** Add bucket name to exception ([#11389](https://github.com/serverless/serverless/issues/11389)) ([11b7a05](https://github.com/serverless/serverless/commit/11b7a05fd3db362003412484245cc55bfab70181)) ([Roberto Aguilar](https://github.com/rca))
- **AWS Deploy:** Bump custom resources to `nodejs16.x` runtime ([#11367](https://github.com/serverless/serverless/issues/11367)) ([93ce41e](https://github.com/serverless/serverless/commit/93ce41e9d8bf29519b043cf3ee2910f02c884eea)) ([Çağrı Atalay](https://github.com/cagriatalay))
- Upgrade `dotenv-expand` to v9 ([#11433](https://github.com/serverless/serverless/issues/11433)) ([c769c1e](https://github.com/serverless/serverless/commit/c769c1e06dd3529bf7a8a1cda33d54b5a7d12ac7)) ([Mariusz Nowak](https://github.com/medikoo))
- Upgrade `filesize` to v10 ([#11433](https://github.com/serverless/serverless/issues/11433)) ([9ef5fd2](https://github.com/serverless/serverless/commit/9ef5fd23b123730696d00985988a1bc37a3c10e0)) ([Mariusz Nowak](https://github.com/medikoo))

## [3.22.0](https://github.com/serverless/serverless/compare/v3.21.0...v3.22.0) (2022-08-16)

### Features

- **AWS Cognito:** Add Support for Custom Sender Triggers ([#11201](https://github.com/serverless/serverless/issues/11201)) ([22802ef](https://github.com/serverless/serverless/commit/22802efde1d1721404b4e0d704f7806938183522)) ([AustinMathuw](https://github.com/AustinMathuw))

### Bug Fixes

- **AWS HTTP API:** Fix API Gateway timeout resolution ([#11223](https://github.com/serverless/serverless/issues/11223)) ([16b0cd6](https://github.com/serverless/serverless/commit/16b0cd60c9914d871eaa3639562ec580c855af43)) ([Corentin Doue](https://github.com/CorentinDoue))
- **Variables:** Fix handling of parallel resolution of same variable ([#11299](https://github.com/serverless/serverless/issues/11299)) ([1f9a07f](https://github.com/serverless/serverless/commit/1f9a07f989fc0b56885edf8a271a0bd63cf8911f)) ([Mariusz Nowak](https://github.com/medikoo))

### Maintenance Improvements

- Remove left over internal `self:` handling ([#11279](https://github.com/serverless/serverless/issues/11279)) ([544717e](https://github.com/serverless/serverless/commit/544717e703c093340b73dcbf94dc40555cda5251)) ([pjmattingly](https://github.com/pjmattingly))
- **`lodash` replacement:**
  - Replace `_.flatMap` with `Array.prototype.flatMap` ([#11272](https://github.com/serverless/serverless/issues/11272)) ([4f7e129](https://github.com/serverless/serverless/commit/4f7e12939ced5b269d53624e5643bd5a9173ed7b)) ([pjmattingly](https://github.com/pjmattingly))
  - Replace `_.flatten` with `Array.prototype.flat` ([#11271](https://github.com/serverless/serverless/issues/11271)) ([b36cdf2](https://github.com/serverless/serverless/commit/b36cdf2db6ee25f7defe6f2c02dd40e1d5cb65c4)) ([pjmattingly](https://github.com/pjmattingly))
- Ignore `doctor` in Compose triage ([#11283](https://github.com/serverless/serverless/issues/11283)) ([ef2dcb6](https://github.com/serverless/serverless/commit/ef2dcb6df7cf5dd4b82a74613d02f22f04b7147a)) ([](https://github.com/)) ([Piotr Grzesik](https://github.com/pgrzesik))

## [3.21.0](https://github.com/serverless/serverless/compare/v3.20.0...v3.21.0) (2022-07-14)

### Features

- **Console:** Rely on Console ready layers published to AWS ([#11236](https://github.com/serverless/serverless/issues/11236)) ([f9bc405](https://github.com/serverless/serverless/commit/f9bc4051844d1d54259216914fd28048d8749409)) ([Mariusz Nowak](https://github.com/medikoo))

### Bug Fixes

- **Console:** Keep currently attached layers with `function deploy` ([#11235](https://github.com/serverless/serverless/issues/11235)) ([198d3b7](https://github.com/serverless/serverless/commit/198d3b7738e36ca1d8e516e257b2be81e04b8e6a)) ([Mariusz Nowak](https://github.com/medikoo))

## [3.20.0](https://github.com/serverless/serverless/compare/v3.19.0...v3.20.0) (2022-07-08)

### Features

- Add `X-Amzn-Trace-Id` to default CORS headers ([#11168](https://github.com/serverless/serverless/issues/11168)) ([9fd56fd](https://github.com/serverless/serverless/commit/9fd56fddbedf85c01d6f4ebd2f63ab26746f6005)) ([Szymon Bartnik](https://github.com/szbartnik))
- **AWS Local Invocation:**
  - Support ESM handlers ([#11212](https://github.com/serverless/serverless/issues/11212)) ([675b1db](https://github.com/serverless/serverless/commit/675b1dbed764f70a7443cdd5e4a53c54315fec36)) ([Børge Bardo](https://github.com/borge-bardo-adsk))
  - Support Node handlers with `.cjs` extension ([#11203](https://github.com/serverless/serverless/pull/11203)) ([688f50d](https://github.com/serverless/serverless/commit/688f50d670b84a1dce097256776651b3138de456)) ([Piotr Grzesik](https://github.com/pgrzesik))

### Bug Fixes

- **AWS Invocation:** Ensure proper log formatting for `invoke` ([#11189](https://github.com/serverless/serverless/pull/11189)) ([c4eb2ad](https://github.com/serverless/serverless/commit/c4eb2ad908cbb4cbf646d9ffc73da31e9db1482f)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **Console:** Fix console url for platform dev stage case ([#11219](https://github.com/serverless/serverless/pull/11219)) ([543612a](https://github.com/serverless/serverless/commit/543612acbec08a76c085f84ff18578c3875810c2)) ([Mariusz Nowak](https://github.com/medikoo))

### Maintenance Improvements

- **AWS Deploy:** Improve vague S3-related access errors ([#11217](https://github.com/serverless/serverless/pull/11217)) ([1b2ac24](https://github.com/serverless/serverless/commit/1b2ac245666fdd5b903a2ffb8ba5376ecfaab182)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **CLI:** Recognize `--help` for `compose` triage ([#11137](https://github.com/serverless/serverless/pull/11137)) ([37b29b0](https://github.com/serverless/serverless/commit/37b29b029579191e82348afbf855590c2cb37062)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **Console:** Report command which originated login operation ([#11220](https://github.com/serverless/serverless/pull/11220)) ([8d4bf4f](https://github.com/serverless/serverless/commit/8d4bf4fbfdf79950e92ad4fbb171f6fa15b11886)) ([Piotr Grzesik](https://github.com/pgrzesik))
- Improve error message for CLI param validation ([#9846](https://github.com/serverless/serverless/issues/9846)) ([a2ea68d](https://github.com/serverless/serverless/commit/a2ea68d5be4583f71400db4fa4fc27575c8c664b)) ([Matthieu Napoli](https://github.com/mnapoli))

## [3.19.0](https://github.com/serverless/serverless/compare/v3.18.2...v3.19.0) (2022-06-02)

### Features

- **Console:** Support new user settings format ([#11115](https://github.com/serverless/serverless/issues/11115)) ([21461b5](https://github.com/serverless/serverless/commit/21461b5581bb759c259e82295fde952d907112b3)) ([Mariusz Nowak](https://github.com/medikoo))
- Recognize `Fn::Select` in `environment` config schema ([#11114](https://github.com/serverless/serverless/issues/11114)) ([ed111e0](https://github.com/serverless/serverless/commit/ed111e021b286eb4a68f9b2fce7fb641e03340bd)) ([John Minns](https://github.com/Johnogram))

### Maintenance Improvements

- Improve CLI messages when onboarding into Console ([#11123](https://github.com/serverless/serverless/issues/11123)) ([cefb762](https://github.com/serverless/serverless/commit/cefb7623355508aab0fdcbeaa8519c61c8bf6291)) ([Matthieu Napoli](https://github.com/mnapoli))

### [3.18.2](https://github.com/serverless/serverless/compare/v3.18.1...v3.18.2) (2022-05-23)

### Bug Fixes

- **AWS Deploy:** Ensure to only remove specific stage deploy artifacts ([#11100](https://github.com/serverless/serverless/pull/11100)) ([9eae965](https://github.com/serverless/serverless/commit/9eae9652bdfca78eeb29bc4e9dfd4f8a12125d56)) ([Ryan Hartkopf](https://github.com/ryanhartkopf))

### Maintenance Improvements

- **Console:** Upgrade `@serverless/aws-lambda-otel-extension` ([#11106](https://github.com/serverless/serverless/pull/11106)) ([5327b70](https://github.com/serverless/serverless/commit/5327b702f755b13283562337c18051d87805916f)) ([Mariusz Nowak](https://github.com/medikoo))
- **Telemetry:** Recognize `isUsingCompose` ([#11105](https://github.com/serverless/serverless/pull/11105)) ([007c294](https://github.com/serverless/serverless/commit/007c294211954e3fdb034030eacd1f01e63920bf)) ([Piotr Grzesik](https://github.com/pgrzesik))

### [3.18.1](https://github.com/serverless/serverless/compare/v3.18.0...v3.18.1) (2022-05-20)

### Bug Fixes

- **CLI Onboarding:**
  - Recognize Dashboard providers for deployment when Dashboard monitoring is turned off ([#11096](https://github.com/serverless/serverless/issues/11096)) ([38ff287](https://github.com/serverless/serverless/commit/38ff287bc79614803b82ada3728c1432381bc59b)) ([Mariusz Nowak](https://github.com/medikoo))
  - Support Dashboard providers with the Console enabled ([#11096](https://github.com/serverless/serverless/issues/11096)) ([8825e86](https://github.com/serverless/serverless/commit/8825e867d833a28ace051047ce17bf3cdc3e7526)) ([Mariusz Nowak](https://github.com/medikoo))

### Maintenance Improvements

- **Console:** Improve user error message ([#11094](https://github.com/serverless/serverless/issues/11094)) ([6748642](https://github.com/serverless/serverless/commit/67486421235dc8d7a76f760eecb68b1a13b13fb2)) ([Mariusz Nowak](https://github.com/medikoo))

## [3.18.0](https://github.com/serverless/serverless/compare/v3.17.0...v3.18.0) (2022-05-19)

### Features

- **Console:**
  - Switch to a new authentication system ([#11060](https://github.com/serverless/serverless/issues/11060)) ([d40866a](https://github.com/serverless/serverless/commit/d40866a0e845123ceecdd5b2b05e96e8dde09b04)) ([Mariusz Nowak](https://github.com/medikoo))
  - In uneven scenario let user decide whether intent is to login into the Dashboard or the Console([#11045](https://github.com/serverless/serverless/issues/11045)) ([0f21362](https://github.com/serverless/serverless/commit/0f2136209199dad43410b0a71b2fa2c211a027a7)) ([Mariusz Nowak](https://github.com/medikoo))
  - Report `org` mismatch with a meaningful error ([#11060](https://github.com/serverless/serverless/issues/11060)) ([ecaeb1f](https://github.com/serverless/serverless/commit/ecaeb1f1bb210e8f6eced3011ce54ab854d23ff8)) ([Mariusz Nowak](https://github.com/medikoo))
  - Support `console.org` setting (so different `org` settings can be used for the Dashboard and the Console) ([#11060](https://github.com/serverless/serverless/issues/11060)) ([3b3cfae](https://github.com/serverless/serverless/commit/3b3cfae4986f0e022b8906ec59743482a5540068)) ([Mariusz Nowak](https://github.com/medikoo))
- **AWS MSK:** Add support for SASL/SCRAM authentication ([#11060](https://github.com/serverless/serverless/issues/11060)) ([184cb03](https://github.com/serverless/serverless/commit/184cb030a87a20d0491ee3d79244ca017d44aabf)) ([Ariel Gordone](https://github.com/Arielgordon123))
- **AWS S3:** Support `forceDeploy` setting ([#11066](https://github.com/serverless/serverless/issues/11066)) ([5af44a4](https://github.com/serverless/serverless/commit/5af44a478e66cb7361dd09a79e9acc1869552f19)) ([Simon Archer](https://github.com/simonarcher99))
- **AWS Lambda:** Recognize all variants of supported log retention days ([#11076](https://github.com/serverless/serverless/issues/11076)) ([a4d0ad5](https://github.com/serverless/serverless/commit/a4d0ad530b1c473cdb09ac1428717660b8b9ad5c)) ([Brian Celenza](https://github.com/bcelenza))

### Bug Fixes

- **AWS Lambda:** Fix support for lambdas with provisioned concurrency on with `url: true` ([#11045](https://github.com/serverless/serverless/issues/11045)) ([2107aec](https://github.com/serverless/serverless/commit/2107aec965e4e1e0cec98c3e2f0ff8dcc534a333)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **CLI:** Fix CLI command validation when using custom providers ([#11080](https://github.com/serverless/serverless/issues/11080)) ([5004fb1](https://github.com/serverless/serverless/commit/5004fb1ea0ba168d6a7ccc0d07070e6b716f78a2)) ([Mariusz Nowak](https://github.com/medikoo))
- **Variables:** Fix reporting of unresolved sources ([#11080](https://github.com/serverless/serverless/issues/11080)) ([77e21f9](https://github.com/serverless/serverless/commit/77e21f904568db00f6e1491dd0dcdfe605fa592d)) ([Mariusz Nowak](https://github.com/medikoo))

### Maintenance Improvements

- **Console:**
  - Rely on generic `apiRequest` for ingestion tokens rotation ([#11060](https://github.com/serverless/serverless/issues/11060)) ([#11060](https://github.com/serverless/serverless/issues/11060)) ([0cecae7](https://github.com/serverless/serverless/commit/0cecae75ffad4b7b89148b614d0bb82dc3b3501c)) ([Mariusz Nowak](https://github.com/medikoo))
  - Separate Dashboard & Console login logic ([#11060](https://github.com/serverless/serverless/issues/11060)) ([443fa4b](https://github.com/serverless/serverless/commit/443fa4b74d1fceeb4798ba2b6acb31281b80756e)) ([Mariusz Nowak](https://github.com/medikoo))
- **CLI Onboarding:** Generalize `isConsole` resolution ([#11060](https://github.com/serverless/serverless/issues/11060)) ([caaa3c8](https://github.com/serverless/serverless/commit/caaa3c811e9f777c84fe91ea73b63eb609032b3b)) ([Mariusz Nowak](https://github.com/medikoo))

## [3.17.0](https://github.com/serverless/serverless/compare/v3.16.0...v3.17.0) (2022-05-10)

### Features

- **AWS Lambda:** Add support for `nodejs16.x` runtime ([#11049](https://github.com/serverless/serverless/issues/11049)) ([719766b](https://github.com/serverless/serverless/commit/719766b03088f6acf4045c83045ec2d220c11819)) ([Hibanka](https://github.com/Hibanka))
- **AWS Websocket:** Allow propagating tags to Websocket APIGW ([#10931](https://github.com/serverless/serverless/issues/10931)) ([22e4842](https://github.com/serverless/serverless/commit/22e4842d97ac3cbc11d8c398e84639af0b6068b8)) ([tjurdzinski](https://github.com/tjurdzinski))

## [3.16.0](https://github.com/serverless/serverless/compare/v3.15.2...v3.16.0) (2022-04-29)

### Features

- **AWS Deploy:** New option to deploy with CloudFormation without using changesets, which is faster. Learn more [in the documentation](https://www.serverless.com/framework/docs/providers/aws/guide/deploying#deployment-method). ([#11016](https://github.com/serverless/serverless/pull/11016)) ([efa3a28](https://github.com/serverless/serverless/commit/efa3a28f0727602b02989c731054697608c22bbc)) ([Piotr Grzesik](https://github.com/pgrzesik))

### Bug Fixes

- **CLI:** Do not run `compose` for non-service commands ([#11017](https://github.com/serverless/serverless/pull/11017)) ([e56bc4b](https://github.com/serverless/serverless/commit/e56bc4be0c5941e76a6433782aa1462b83f5d13f)) ([Piotr Grzesik](https://github.com/pgrzesik))
- Allow S3 event rule prefix and suffix to use CF functions ([#11018](https://github.com/serverless/serverless/issues/11018)) ([0279e1e](https://github.com/serverless/serverless/commit/0279e1eb9d79abce52c595b3cde190ff96599e42)) ([Matthew Crouch](https://github.com/macrouch))
- Ensure to attempt minimal config resolution for plugin commands ([#11005](https://github.com/serverless/serverless/pull/11005)) ([af9a238](https://github.com/serverless/serverless/commit/af9a238f852fb04fbfcdfa57b9b313426f579bd1)) ([Piotr Grzesik](https://github.com/pgrzesik))
- Ensure to not add double entries during `plugin install` ([#11005](https://github.com/serverless/serverless/pull/11005)) ([c4ca97d](https://github.com/serverless/serverless/commit/c4ca97d0100a28d02012b144c1a9ba06f7ac7dc6)) ([Piotr Grzesik](https://github.com/pgrzesik))

### Maintenance Improvements

- **AWS Local Invocation:** Rely on observable spawn ([#11002](https://github.com/serverless/serverless/pull/11002)) ([6d97496](https://github.com/serverless/serverless/commit/6d9749699da62a07ae933bd2c9a9ced8ccf877df)) ([Mariusz Nowak](https://github.com/medikoo))
- **Console:**
  - Configure `login` as standalone command ([#11003](https://github.com/serverless/serverless/pull/11003)) ([fffaf9c](https://github.com/serverless/serverless/commit/fffaf9cee2da00bdb4f8d13846ad216d4dee13ef)) ([Mariusz Nowak](https://github.com/medikoo))
  - Configure `logout` as standalone command ([#11003](https://github.com/serverless/serverless/pull/11003)) ([70ca359](https://github.com/serverless/serverless/commit/70ca3594b6fbc1118b24c2bc4975219f6c00cbd0)) ([Mariusz Nowak](https://github.com/medikoo))

### [3.15.2](https://github.com/serverless/serverless/compare/v3.15.1...v3.15.2) (2022-04-22)

### Maintenance Improvements

- **Console:** Report requests and responses to server ([#10999](https://github.com/serverless/serverless/pull/10999)) ([fa8243f](https://github.com/serverless/serverless/commit/fa8243f960df372b644e791374842f04bfab7857)) ([Mariusz Nowak](https://github.com/medikoo))

### [3.15.1](https://github.com/serverless/serverless/compare/v3.15.0...v3.15.1) (2022-04-22)

### Maintenance Improvements

- **Console:**
  - Propagate `disableLogsCollection` to extension user settings ([#10995](https://github.com/serverless/serverless/pull/10995)) ([4521eb7](https://github.com/serverless/serverless/commit/4521eb7e3b3eb72af7c535fda9cf6efcb4a1e140)) ([Mariusz Nowak](https://github.com/medikoo))
  - Support `disableRequestResponseMonitoring` setting ([#10995](https://github.com/serverless/serverless/pull/10995)) ([e5c088f](https://github.com/serverless/serverless/commit/e5c088fe2e2de99e0da464abb36c785741b5b085)) ([Mariusz Nowak](https://github.com/medikoo))
- **Telemetry:**
  - Fix Console org reporting ([#10995](https://github.com/serverless/serverless/pull/10995)) ([c0aabb4](https://github.com/serverless/serverless/commit/c0aabb484531c5227f42791cdb9e644c402a5c8d)) ([Mariusz Nowak](https://github.com/medikoo))
  - Debug log for telemetry payload ([#10995](https://github.com/serverless/serverless/pull/10995)) ([db67962](https://github.com/serverless/serverless/commit/db6796257f41618ad7da440ca5b2e46fae971fe1)) ([Mariusz Nowak](https://github.com/medikoo))

### [3.15.0](https://github.com/serverless/serverless/compare/v3.14.0...v3.15.0) (2022-04-20)

### Features

- Introduce [Serverless Framework Compose](https://www.serverless.com/framework/docs/guides/compose), a new feature that enables deploying multiple services in one command, in parallel, or ordered by dependencies

### Maintenance Improvements

- Handle `@serverless/compose` install in non-interactive environments ([#10984](https://github.com/serverless/serverless/pull/10984)) ([75885cb](https://github.com/serverless/serverless/commit/75885cbbc5165aa4f27be4aab179e9e2655c1d99)) ([Piotr Grzesik](https://github.com/pgrzesik))
- Support custom error message for variables resolution ([#10985](https://github.com/serverless/serverless/pull/10985)) ([f7ffb19](https://github.com/serverless/serverless/commit/f7ffb1978804ce01fc14d14866529378ebc1c1e2)) ([Piotr Grzesik](https://github.com/pgrzesik))

## [3.14.0](https://github.com/serverless/serverless/compare/v3.13.0...v3.14.0) (2022-04-14)

### Features

- **AWS Websocket:** Add ability to configure log format and types ([#10956](https://github.com/serverless/serverless/pull/10956)) ([82ce1c8](https://github.com/serverless/serverless/commit/82ce1c83d23008a5f7b48d149fcaac828c782871)) ([Ariette](https://github.com/Ariette))

### Maintenance Improvements

- Enable triage process to run `@serverless/compose` ([#10950](https://github.com/serverless/serverless/issues/10950)) ([401c721](https://github.com/serverless/serverless/commit/401c721f8e1c59441ba3e5bb44bb2ce34576d99d)) ([Piotr Grzesik](https://github.com/pgrzesik))

## [3.13.0](https://github.com/serverless/serverless/compare/v3.12.0...v3.13.0) (2022-04-13)

### Features

- **Variables:** Ensure support for promise properties at `file` source ([#10949](https://github.com/serverless/serverless/pull/10949)) ([8dae213](https://github.com/serverless/serverless/commit/8dae21375801be00f24d68d6a3e12854132b7bb9)) ([Mariusz Nowak](https://github.com/medikoo))

### Bug Fixes

- **AWS API Gateway:** Correctly construct resource name for schema ([#10940](https://github.com/serverless/serverless/pull/10940)) ([0a0f6c6](https://github.com/serverless/serverless/commit/0a0f6c6102b3cb8921ef7448d5b3a8f1294b6802)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **AWS Local Invocation:** Ensure environment variables resolution for docker invoke ([#10962](https://github.com/serverless/serverless/issues/10962)) ([1a8e7d9](https://github.com/serverless/serverless/commit/1a8e7d948efe696cd4970f73ac4262cc15ebe977)) ([Sergii Dolgushev](https://github.com/SerheyDolgushev))
- **CLI:** Do not attempt to resolve full config for `login` ([#10942](https://github.com/serverless/serverless/pull/10942)) ([9b62d14](https://github.com/serverless/serverless/commit/9b62d14e691eedafcefc0cc414c82f3f7d13636d)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **Standalone:** Ensure proper `npm` bundling ([#10941](https://github.com/serverless/serverless/pull/10941)) ([cf482f0](https://github.com/serverless/serverless/commit/cf482f01700ddd0946e71ad5e7d2ca0d06cc49a3)) ([Piotr Grzesik](https://github.com/pgrzesik))

### Maintenance Improvements

- **Console:** Document `--console` with a link to documentation ([#10951](https://github.com/serverless/serverless/pull/10951)) ([23a5ea3](https://github.com/serverless/serverless/commit/23a5ea3a3a53a2e9fb7f1a65160d22c8868ddbbe)) ([Mariusz Nowak](https://github.com/medikoo))
- **Telemetry:** Ensure to pass unique id with events ([#10966](https://github.com/serverless/serverless/pull/10966)) ([3bcff79](https://github.com/serverless/serverless/commit/3bcff796f1046c09c4f7f9c0545f6393a332c4c0)) ([Piotr Grzesik](https://github.com/pgrzesik))

## [3.12.0](https://github.com/serverless/serverless/compare/v3.11.0...v3.12.0) (2022-04-06)

### Features

- **AWS Lambda:** Add support for function URLs ([#10936](https://github.com/serverless/serverless/pull/10936)) ([d215517](https://github.com/serverless/serverless/commit/d215517cf009ded63e50cd37e55c0be99bdba754)) ([Piotr Grzesik](https://github.com/pgrzesik))

### Maintenance Improvements

- **CLI:** Fix typos in `create` CLI messages ([#10933](https://github.com/serverless/serverless/issues/10933)) ([26f79aa](https://github.com/serverless/serverless/commit/26f79aaf19f39725e81461ee06b79cb00a6d14db)) ([Petri Partio](https://github.com/peritpatrio))

## [3.11.0](https://github.com/serverless/serverless/compare/v3.10.2...v3.11.0) (2022-04-04)

### Features

- **AWS RabbitMQ:** Support `virtualHost` ([#10814](https://github.com/serverless/serverless/issues/10814)) ([e21fb75](https://github.com/serverless/serverless/commit/e21fb756fc8625c7dc1bfe86137effbcf09f8287)) ([Rudolf Nel](https://github.com/EnterNameHere7))
- **CLI Onboarding:** Support all runtimes for dashboard (with limited functionality) ([#10922](https://github.com/serverless/serverless/pull/10922)) ([0ca0cff](https://github.com/serverless/serverless/commit/0ca0cfffda6dbf5c3179a6d2de4b2dd52e07af59)) ([Piotr Grzesik](https://github.com/pgrzesik))

### [3.10.2](https://github.com/serverless/serverless/compare/v3.10.1...v3.10.2) (2022-03-31)

### Maintenance Improvements

- **Console:** Report logs with opt out option ([#10919](https://github.com/serverless/serverless/issues/10193)) ([ababd90](https://github.com/serverless/serverless/commit/ababd90f098f922a92a79ca7bdb00a3dfe112c6b)) ([Mariusz Nowak](https://github.com/medikoo))

### [3.10.1](https://github.com/serverless/serverless/compare/v3.10.0...v3.10.1) (2022-03-30)

### Bug Fixes

- **AWS Deploy:** Apply stack policy after executing change sets ([#10903](https://github.com/serverless/serverless/issues/10903)) ([2d2cb3e](https://github.com/serverless/serverless/commit/2d2cb3ed11919ccdb5b99e8316906ad5eccd836f)) ([Mark Tse](https://github.com/neverendingqs))
- **AWS Local Invocation:**
  - Ensure proper artifact permissions for `rust` functions ([#10891](https://github.com/serverless/serverless/issues/10891)) ([11dd77e](https://github.com/serverless/serverless/commit/11dd77ecde61b690023067dacdabf759121cd17c)) ([Sergii Dolgushev](https://github.com/SerheyDolgushev))
  - Ensure package before resolving runtime ([#10888](https://github.com/serverless/serverless/pull/10888)) ([80b3e1a](https://github.com/serverless/serverless/commit/80b3e1a9e59746dd795828207a2badf683638df4)) ([Sergii Dolgushev](https://github.com/SerheyDolgushev))

### Maintenance Improvements

- **AWS Deploy:** Ensure no internal dependency on `console` ([#10908](https://github.com/serverless/serverless/pull/10908)) ([2a8ef3e](https://github.com/serverless/serverless/commit/2a8ef3ed5abc6497b9552e1786586468d66d806a)) ([Mariusz Nowak](https://github.com/medikoo))
- **Telemetry:** Send more frequently to avoid too big payloads ([#10909](https://github.com/serverless/serverless/pull/10909)) ([889e1b6](https://github.com/serverless/serverless/commit/889e1b67bf1637e6f78bef83ac036937df50ebce)) ([Piotr Grzesik](https://github.com/pgrzesik))

## [3.10.0](https://github.com/serverless/serverless/compare/v3.9.0...v3.10.0) (2022-03-25)

### Features

- **AWS Lambda:** Support `ephemeralStorageSize` ([#10901](https://github.com/serverless/serverless/pull/10901)) ([d317cff](https://github.com/serverless/serverless/commit/d317cff875535a0de47578e12de395b1d52043a0)) ([Piotr Grzesik](https://github.com/pgrzesik))

## [3.9.0](https://github.com/serverless/serverless/compare/v3.8.0...v3.9.0) (2022-03-24)

### Features

- **AWS Lambda:** Support `Ref` for `destinations` properties ([#10845](https://github.com/serverless/serverless/issues/10845)) ([9e0ca03](https://github.com/serverless/serverless/commit/9e0ca03900feb19be21ebe7498ed0fc592af37e0)) ([ALOHACREPES345](https://github.com/ALOHACREPES345))

### Bug Fixes

- **AWS Deploy:**
  - Fix handling of state file in check for changes logic ([#10885](https://github.com/serverless/serverless/pull/10885)) ([12d95dc](https://github.com/serverless/serverless/commit/12d95dcee1985ff32c02e1ba507a236eceab65ba)) ([Mariusz Nowak](https://github.com/medikoo))
  - Recognize otel extension in check for changes logic ([#10885](https://github.com/serverless/serverless/pull/10885)) ([6da0b65](https://github.com/serverless/serverless/commit/6da0b6554ee1d42dca4f02ac874ff8e992051de0)) ([Mariusz Nowak](https://github.com/medikoo))
- **Console:** Ensure single layer attachment with `package.individually` ([#10895](https://github.com/serverless/serverless/pull/10895)) ([fac8a73](https://github.com/serverless/serverless/commit/fac8a73eec9ed6a6cf7535a1c723da3cb882905a)) ([Mariusz Nowak](https://github.com/medikoo))

### Maintenance Improvements

- **AWS Deploy:**
  - Debug logs for check for changes logic ([#10885](https://github.com/serverless/serverless/pull/10885)) ([9f76f19](https://github.com/serverless/serverless/commit/9f76f19cf3cfe1e3e7e74953d15e5feb9cd875ac)) ([Mariusz Nowak](https://github.com/medikoo))
  - Debug logs for logs subscription check ([#10885](https://github.com/serverless/serverless/pull/10885)) ([895f320](https://github.com/serverless/serverless/commit/895f320c60da21daf12afaab91e967576294f374)) ([Mariusz Nowak](https://github.com/medikoo))
  - Improve internal resolution of hashes ([#10885](https://github.com/serverless/serverless/pull/10885)) ([711b643](https://github.com/serverless/serverless/commit/711b6439e06552d5c2bb411299b851f8f39f8a76)) ([Mariusz Nowak](https://github.com/medikoo))
  - Refactor `getMostRecentObjects` to async/await ([#10885](https://github.com/serverless/serverless/pull/10885)) ([1461860](https://github.com/serverless/serverless/commit/1461860dabe6f5154ee0d5e69b4c1ed16eb05616)) ([Mariusz Nowak](https://github.com/medikoo))
  - Refactor to async/await ([#10885](https://github.com/serverless/serverless/pull/10885)) ([8bb306b](https://github.com/serverless/serverless/commit/8bb306b56f763f474e0c5cf32f07724223ca7f2a)) ([Mariusz Nowak](https://github.com/medikoo))
  - Refactor to native promises ([#10885](https://github.com/serverless/serverless/pull/10885)) ([c5970e7](https://github.com/serverless/serverless/commit/c5970e72a3129c349f719009deff017fce430e69)) ([Mariusz Nowak](https://github.com/medikoo))
- **Console:**
  - Do not disable dashboard with console ([#10895](https://github.com/serverless/serverless/pull/10895)) ([e6cdc9d](https://github.com/serverless/serverless/commit/e6cdc9d68bed6bafb78bbb1bf4490e5dc35c4fdd)) ([Mariusz Nowak](https://github.com/medikoo))
  - Ensure to list extension layer in layers output ([#10895](https://github.com/serverless/serverless/pull/10895)) ([14109e8](https://github.com/serverless/serverless/commit/14109e8ec475c71170215154b8ad92aecdb5f432)) ([Mariusz Nowak](https://github.com/medikoo))
  - Improve error reporting when layer cannot be added ([#10895](https://github.com/serverless/serverless/pull/10895)) ([ba71dd9](https://github.com/serverless/serverless/commit/ba71dd9fb527ebac854e4a12b974581f4de6e57e)) ([Mariusz Nowak](https://github.com/medikoo))

## [3.8.0](https://github.com/serverless/serverless/compare/v3.7.9...v3.8.0) (2022-03-21)

### Features

- **AWS Lambda:**
  - Recognize `Fn::If` for properties of `vpc` ([#10877](https://github.com/serverless/serverless/issues/10877)) ([6a86ed7](https://github.com/serverless/serverless/commit/6a86ed77f8f9702f033b043f47d781d60ab76d4e)) ([ALOHACREPES345](https://github.com/ALOHACREPES345))
  - Support `logRetentionInDays` per function ([#10878](https://github.com/serverless/serverless/issues/10878)) ([4c25184](https://github.com/serverless/serverless/commit/4c25184ca0cffa273c4171f5fccac52ab8ee3413)) ([ALOHACREPES345](https://github.com/ALOHACREPES345))

### [3.7.9](https://github.com/serverless/serverless/compare/v3.7.8...v3.7.9) (2022-03-18)

### Bug Fixes

- **CLI Onboarding:** Ensure to process fully resolved service config ([#10873](https://github.com/serverless/serverless/pull/10873)) ([6a1f083](https://github.com/serverless/serverless/commit/6a1f083ac80aa9ba04e072b55f53ea1a4367fc2a)) ([Mariusz Nowak](https://github.com/medikoo))
- **CLI Onboarding:** Improve fix for initial variables resolution ([#10873](https://github.com/serverless/serverless/pull/10873)) ([1f12b19](https://github.com/serverless/serverless/commit/1f12b19a22bd40ce34c8bf45f090e46074409887)) ([Mariusz Nowak](https://github.com/medikoo))
- **Console:** Prevent AWS region mismatch ([#10873](https://github.com/serverless/serverless/pull/10873)) ([43480ee](https://github.com/serverless/serverless/commit/43480ee872d7d999d398eccdf56172860d40be56)) ([Mariusz Nowak](https://github.com/medikoo))
- Fix internal unrecognized command error processing ([#10873](https://github.com/serverless/serverless/pull/10873)) ([a89e36a](https://github.com/serverless/serverless/commit/a89e36a0e73df141a486b8a151bb2cfb228a9f5d)) ([Mariusz Nowak](https://github.com/medikoo))

### Maintenance Improvements

- **CLI:** Configure processing flow debug logs ([#10873](https://github.com/serverless/serverless/pull/10873)) ([7af0c8c](https://github.com/serverless/serverless/commit/7af0c8cb07ee056e0224d35fdcdbac4ead004cee)) ([Mariusz Nowak](https://github.com/medikoo))
- **Console:** Present url to console UI ([#10873](https://github.com/serverless/serverless/pull/10873)) ([0d9f866](https://github.com/serverless/serverless/commit/0d9f86620b9c600dfecaf2a194a499b57c5bac0c)) ([Mariusz Nowak](https://github.com/medikoo))
- Upgrade to async/await ([#10873](https://github.com/serverless/serverless/pull/10873)) ([8c7731d](https://github.com/serverless/serverless/commit/8c7731d4376fb7ae4998a37b2a196e4fb80107ba)) ([Mariusz Nowak](https://github.com/medikoo))

### [3.7.8](https://github.com/serverless/serverless/compare/v3.7.7...v3.7.8) (2022-03-17)

### Bug Fixes

- **Console:**
  - Fix reference to bucket name in CF template ([#10869](https://github.com/serverless/serverless/pull/10869)) ([fcaa9c2](https://github.com/serverless/serverless/commit/fcaa9c2c4f756b552ba990438df8866e304f3b56)) ([Mariusz Nowak](https://github.com/medikoo))
  - Fix upload of extension to S3 bucket ([#10869](https://github.com/serverless/serverless/pull/10869)) ([23719d8](https://github.com/serverless/serverless/commit/23719d868c0b4270b57ea025a4271c62a58cb65f)) ([Mariusz Nowak](https://github.com/medikoo))

### [3.7.7](https://github.com/serverless/serverless/compare/v3.7.6...v3.7.7) (2022-03-17)

### Bug Fixes

- **Console:** Respect custom deployment bucket configuration ([#10867](https://github.com/serverless/serverless/pull/10867)) ([4d705cc](https://github.com/serverless/serverless/commit/4d705cc96d1bec29c3328879e41a71f907b0696d)) ([Mariusz Nowak](https://github.com/medikoo))

### Maintenance Improvements

- **Console:**
  - Generalize internal `bucketName` resolution ([#10867](https://github.com/serverless/serverless/pull/10867)) ([103fc55](https://github.com/serverless/serverless/commit/103fc554fc21bf7f8f16a634836bfe10d5109446)) ([Mariusz Nowak](https://github.com/medikoo))
  - Report used layer extension version to telemetry ([#10867](https://github.com/serverless/serverless/pull/10867)) ([db89f20](https://github.com/serverless/serverless/commit/db89f20f01b66c7dfc81f1571dfb215ba85daa24)) ([Mariusz Nowak](https://github.com/medikoo))
- **CLI:** Support internally a temporary `SLS_DISABLE_AUTO_UPDATE` env var ([c939457](https://github.com/serverless/serverless/commit/c939457ba46232b247a691b23c95f8408eba406f)) ([Piotr Grzesik](https://github.com/pgrzesik))

### [3.7.6](https://github.com/serverless/serverless/compare/v3.7.5...v3.7.6) (2022-03-17)

### Bug Fixes

- **Standalone:** Ensure error in China upload don't break GitHub upload ([#10853](https://github.com/serverless/serverless/pull/10853)) ([2b8afac](https://github.com/serverless/serverless/commit/2b8afac5ecf879a6e979c5a4642ededeca4a5cf7)) ([Mariusz Nowak](https://github.com/medikoo))
- **Console:** Ensure to package extension without errors ([#10860](https://github.com/serverless/serverless/pull/10860)) ([64ee4a5](https://github.com/serverless/serverless/commit/64ee4a528815354905b1f5c92fb7ba1e1604e4b4)) ([Mariusz Nowak](https://github.com/medikoo))

### Maintenance Improvements

- **Console:** Upgrade to rely on v0.2 version of extension ([#10837](https://github.com/serverless/serverless/pull/10837)) ([3ccfec1](https://github.com/serverless/serverless/commit/3ccfec1abdace3abb3e7484d51feb532ad37dda0)) ([Mariusz Nowak](https://github.com/medikoo))

### [3.7.5](https://github.com/serverless/serverless/compare/v3.7.4...v3.7.5) (2022-03-14)

### Bug Fixes

- **AWS Kafka:** Allow usage of Server Root CA without client TLS auth ([#10837](https://github.com/serverless/serverless/pull/10837)) ([6a6417c](https://github.com/serverless/serverless/commit/6a6417c29fe6c06286562ab7604536004bf62334)) ([Fabian Desoye](https://github.com/fdesoye))
- **CLI:** Ensure proper resolution of options for service commands ([#10846](https://github.com/serverless/serverless/issues/10846)) ([dd421cc](https://github.com/serverless/serverless/commit/dd421cc8a65816c59572c581e275455f9793754e)) ([Piotr Grzesik](https://github.com/pgrzesik))

### Maintenance Improvements

- **Console:** Dynamically resolve latest version of the extension ([#10842](https://github.com/serverless/serverless/pull/10842)) ([c28c48c](https://github.com/serverless/serverless/commit/c28c48c6a131201448c6018d6e6951d7d9131eeb)) ([Mariusz Nowak](https://github.com/medikoo))

### [3.7.4](https://github.com/serverless/serverless/compare/v3.7.3...v3.7.4) (2022-03-10)

### Bug Fixes

- **AWS Local Invocation:** Remove log4j dependency from java wrapper ([#10832](https://github.com/serverless/serverless/pull/10832)) ([8b17338](https://github.com/serverless/serverless/commit/8b1733807fe76b01f03880652111f8085a664e31)) ([Yuji Yamano](https://github.com/yyamano))

### Maintenance Improvements

- **Console:** Communicate new token implications with verbose mode ([#10835](https://github.com/serverless/serverless/pull/10835)) ([7e56aa1](https://github.com/serverless/serverless/commit/7e56aa17939021c920ba4046684386016b8f7a1f)) ([Mariusz Nowak](https://github.com/medikoo))

## [3.7.3](https://github.com/serverless/serverless/compare/v3.7.2...v3.7.3) (2022-03-09)

### Bug Fixes

- **CLI Onboarding:**
  - Enable Console in config, only with `--console` ([#10825](https://github.com/serverless/serverless/pull/10825)) ([b173d90](https://github.com/serverless/serverless/commit/b173d90e643a472817f90c9d9a31d4924d35c56f)) ([Mariusz Nowak](https://github.com/medikoo))
  - Ensure to enable Console when commented out ([#10825](https://github.com/serverless/serverless/pull/10825)) ([f0bff74](https://github.com/serverless/serverless/commit/f0bff7463c29e346dc61aa05db2c6f530b9282fb)) ([Mariusz Nowak](https://github.com/medikoo))
  - Fix `initialContext.isDashboardEnabled` resolution ([#10825](https://github.com/serverless/serverless/pull/10825)) ([10c24f6](https://github.com/serverless/serverless/commit/10c24f6398bf8fc987cb2e79fd33ee70964b7836)) ([Mariusz Nowak](https://github.com/medikoo))
  - Fix `isConsole` resolution in `login` step ([#10825](https://github.com/serverless/serverless/pull/10825)) ([688bfcf](https://github.com/serverless/serverless/commit/688bfcf00d276dcc39dc1b67e9a673ccbdc78512)) ([Mariusz Nowak](https://github.com/medikoo))
  - Fix resolution of onboarding message ([#10825](https://github.com/serverless/serverless/pull/10825)) ([624536f](https://github.com/serverless/serverless/commit/624536f77ebe1a0cd6759cb90ef1cb9a209fb64d)) ([Mariusz Nowak](https://github.com/medikoo))
  - Leave `app` intact with also enabled Dashboard ([#10825](https://github.com/serverless/serverless/pull/10825)) ([a043624](https://github.com/serverless/serverless/commit/a0436248e7b127b56b5444a67870ea2671de0a21)) ([Mariusz Nowak](https://github.com/medikoo))
  - Prevent side-effects of not supported `app` option ([#10825](https://github.com/serverless/serverless/pull/10825)) ([0c65663](https://github.com/serverless/serverless/commit/0c65663861b80a4fbd395018141ed90dd41cbdce)) ([Mariusz Nowak](https://github.com/medikoo))
  - Setup `app` when Console and Dashboard enabled ([#10825](https://github.com/serverless/serverless/pull/10825)) ([bffbfe3](https://github.com/serverless/serverless/commit/bffbfe32fd54f5f1fa01db3fcbb81287be246092)) ([Mariusz Nowak](https://github.com/medikoo))
  - With Console always favor console messaging ([#10825](https://github.com/serverless/serverless/pull/10825)) ([f0d441e](https://github.com/serverless/serverless/commit/f0d441e0d469640e04d880b81e361da539aa5f62)) ([Mariusz Nowak](https://github.com/medikoo))

### Maintenance Improvements

- **CLI Onboarding:**
  - Support joint Console (experimental) & Dashboard configurations ([#10825](https://github.com/serverless/serverless/pull/10825)) ([48609f7](https://github.com/serverless/serverless/commit/48609f72762ffe8eabd9415084eed42e01ea061e)) ([Mariusz Nowak](https://github.com/medikoo))
  - Hide not supported templates with console ([#10825](https://github.com/serverless/serverless/pull/10825)) ([79e156f](https://github.com/serverless/serverless/commit/79e156f7ac70d997093d2b2ca127f0844cab121a)) ([Mariusz Nowak](https://github.com/medikoo))
  - Reorganize `writeOrgAppAndConsole` input ([#10825](https://github.com/serverless/serverless/pull/10825)) ([fc9dc1d](https://github.com/serverless/serverless/commit/fc9dc1dc4022163ff6f28f1ee6de2db85fd56202)) ([Mariusz Nowak](https://github.com/medikoo))
  - Reorganize internal variables ([#10825](https://github.com/serverless/serverless/pull/10825)) ([25d2e7a](https://github.com/serverless/serverless/commit/25d2e7a2a0932f40ac5114702fce74a0caa9c019)) ([Mariusz Nowak](https://github.com/medikoo))
  - Support future object notation for `console` ([#10825](https://github.com/serverless/serverless/pull/10825)) ([2f187a5](https://github.com/serverless/serverless/commit/2f187a52eb3a14c6e94d00a37ded64ed75914d3f)) ([Mariusz Nowak](https://github.com/medikoo))
- **Console:** Unify headers resolution ([#10825](https://github.com/serverless/serverless/pull/10825)) ([494fb26](https://github.com/serverless/serverless/commit/494fb2662f910449eb0b7ad3f6caeb1c77486501)) ([Mariusz Nowak](https://github.com/medikoo))
- **Telemetry:**
  - Expose `initialContext.isConsoleEnabled` ([#10825](https://github.com/serverless/serverless/pull/10825)) ([f580883](https://github.com/serverless/serverless/commit/f580883d48027065e9e9aff77ee49c9c1a61fedd)) ([Mariusz Nowak](https://github.com/medikoo))
  - Ensure to not leak `false` as empty value ([#10825](https://github.com/serverless/serverless/pull/10825)) ([167a77e](https://github.com/serverless/serverless/commit/167a77ecaecc4da92f629d1aa075eb1a62831916)) ([Mariusz Nowak](https://github.com/medikoo))

### [3.7.2](https://github.com/serverless/serverless/compare/v3.7.1...v3.7.2) (2022-03-08)

### Bug Fixes

- Ensure to properly support moving directories across filesystems ([#10796](https://github.com/serverless/serverless/pull/10796)) ([d06b64d](https://github.com/serverless/serverless/commit/d06b64d4b9e8203945ad946495ff300d9852b37c)) ([Piotr Grzesik](https://github.com/pgrzesik))

### Maintenance Improvements

- **AWS Lambda:** Support `provisionedConcurrency` set to `0` ([#10798](https://github.com/serverless/serverless/pull/10798)) ([e40ba43](https://github.com/serverless/serverless/commit/e40ba43b84b373a1ef4ac92abc7bf41315ecf955)) ([Dustin Fay](https://github.com/d-fay))
- **Standalone:** Update Tencent CLI standalone download URL ([#10811](https://github.com/serverless/serverless/issues/10811)) ([e26625a](https://github.com/serverless/serverless/commit/e26625a58ce96776f241037b00a190a89ecd6d45)) ([Tim Qian](https://github.com/timqian))
- **Telemetry:** Ensure excluding `shouldSendTelemetry` from payload ([#10810](https://github.com/serverless/serverless/pull/10810)) ([9c6423b](https://github.com/serverless/serverless/commit/9c6423bc5c5d81b977d03d3412b4a2ab05bf4513)) ([Piotr Grzesik](https://github.com/pgrzesik))

### [3.7.1](https://github.com/serverless/serverless/compare/v3.7.0...v3.7.1) (2022-03-02)

### Bug Fixes

- **CLI Onboarding:** Ensure improved variables resolution for existing templates ([#10784](https://github.com/serverless/serverless/pull/10784)) ([17df292](https://github.com/serverless/serverless/commit/17df2928cfb2efa8eab27e625b4609f8047eab5a)) ([Piotr Grzesik](https://github.com/pgrzesik))

### Maintenance Improvements

- **Telemetry:** Rely on direct evaluation of `isTtyTerminal` ([#10786](https://github.com/serverless/serverless/pull/10786)) ([e29253f](https://github.com/serverless/serverless/commit/e29253fbeb17764644ef97c61c0a88892cda4136)) ([Piotr Grzesik](https://github.com/pgrzesik))
- Recognize `logout` as service-aware command ([#10785](https://github.com/serverless/serverless/pull/10785)) ([21c783d](https://github.com/serverless/serverless/commit/21c783dc16dfd00385c907729a67a2fcccda4498)) ([Piotr Grzesik](https://github.com/pgrzesik))

## [3.7.0](https://github.com/serverless/serverless/compare/v3.6.0...v3.7.0) (2022-03-01)

### Features

- **CLI Onboarding:** Support `--console` flag ([#10779](https://github.com/serverless/serverless/pull/10779)) ([a34d07a](https://github.com/serverless/serverless/commit/a34d07a5c129e21d1a0b902479bcaa4a92c158fb)) ([Piotr Grzesik](https://github.com/pgrzesik))

## [3.6.0](https://github.com/serverless/serverless/compare/v3.5.1...v3.6.0) (2022-03-01)

### Features

- **Variables:** Add support for `csj` in `file` source ([#10776](https://github.com/serverless/serverless/issues/10776)) ([df08283](https://github.com/serverless/serverless/commit/df0828381057b7edb2731f3763c2d60eed126d8a)) ([Julian Grinblat](https://github.com/perrin4869))

### Maintenance Improvements

- **Console:** Support login with Console ([#10777](https://github.com/serverless/serverless/pull/10777)) ([4ce1088](https://github.com/serverless/serverless/commit/4ce10883b5aca692a534be8114733fafc5c02a0e)) ([Piotr Grzesik](https://github.com/pgrzesik))

### [3.5.1](https://github.com/serverless/serverless/compare/v3.5.0...v3.5.1) (2022-02-28)

### Bug Fixes

- **AWS Lambda:** Properly format `logs` with missing init duration ([#10772](https://github.com/serverless/serverless/pull/10772)) ([0bb64e2](https://github.com/serverless/serverless/commit/0bb64e21cbe7250f9b14ccb3fd9537d6dec64c67)) ([Piotr Grzesik](https://github.com/pgrzesik))

## [3.5.0](https://github.com/serverless/serverless/compare/v3.4.0...v3.5.0) (2022-02-28)

### Features

- **AWS Lambda:** Simplify `logs` command output ([#10768](https://github.com/serverless/serverless/pull/10768)) ([d8f251c](https://github.com/serverless/serverless/commit/d8f251cfd4798672aa36e869882df0e24ebddc10)) ([Piotr Grzesik](https://github.com/pgrzesik))

### Maintenance Improvements

- **Console:** Add missing `OTEL_RESOURCE_ATTRIBUTES` var ([#10762](https://github.com/serverless/serverless/pull/10762)) ([1f9458b](https://github.com/serverless/serverless/commit/1f9458b4f11c23f8e7fb0b4f9090dbd089224d1e)) ([Piotr Grzesik](https://github.com/pgrzesik) & [Mariusz Nowak](https://github.com/medikoo))
- Log environment details of error to stderr ([#10769](https://github.com/serverless/serverless/pull/10769)) ([f439201](https://github.com/serverless/serverless/commit/f439201d7f884ab1994f7691c35abe50d72bf49e)) ([Piotr Grzesik](https://github.com/pgrzesik))

## [3.4.0](https://github.com/serverless/serverless/compare/v3.3.0...v3.4.0) (2022-02-25)

### Features

- **AWS Lambda:** Add support for `dotnet6` runtime ([#10757](https://github.com/serverless/serverless/issues/10757)) ([818dda2](https://github.com/serverless/serverless/commit/818dda21a9b97fbc911d9885d71b8b708b7b1ecf)) ([Martin Costello](https://github.com/martincostello))
- **Console:** Initial (experimental) support ([#10752](https://github.com/serverless/serverless/issues/10752)) ([bdaf21e](https://github.com/serverless/serverless/commit/bdaf21e1a1e839b7f2a2575cfeba741305080a92)) ([Mariusz Nowak](https://github.com/medikoo))

### Bug Fixes

- **AWS API Gateway:** Properly apply `description` to REST API ([#10746](https://github.com/serverless/serverless/issues/10746)) ([451def9](https://github.com/serverless/serverless/commit/451def93ae1997df6dde10439bd931d73e926708)) ([ALOHACREPES345](https://github.com/ALOHACREPES345))

### Maintenance Improvements

- **AWS Deploy:** Generalize `uploadZipFile` logic ([#10752](https://github.com/serverless/serverless/issues/10752)) ([26bc112](https://github.com/serverless/serverless/commit/26bc112f1f5f34512b9255315b2fab3274d32f74)) ([Mariusz Nowak](https://github.com/medikoo))
- **AWS Deploy:** Improve progress logs for rollback ([#10752](https://github.com/serverless/serverless/issues/10752)) ([24c45a0](https://github.com/serverless/serverless/commit/24c45a08462741bde5e450d9cf6601b7d60ff49c)) ([Mariusz Nowak](https://github.com/medikoo))
- **AWS Deploy:** Refactor `extendedValidate` to async ([#10752](https://github.com/serverless/serverless/issues/10752)) ([e1d2b82](https://github.com/serverless/serverless/commit/e1d2b8251ac7e06ca01fc3bb3505531cee459bce)) ([Mariusz Nowak](https://github.com/medikoo))
- **AWS Deploy:** Store resolved state on internal class ([#10752](https://github.com/serverless/serverless/issues/10752)) ([1c00eb2](https://github.com/serverless/serverless/commit/1c00eb29fe55bccd0fe2ca62fe2c99f93bc4b6db)) ([Mariusz Nowak](https://github.com/medikoo))
- **AWS Deploy:** Upload state file to deployment bucket ([#10752](https://github.com/serverless/serverless/issues/10752)) ([5525a3e](rverless/serverless/commit/5525a3e6f54209e80db98cb32baadd62aac16da9)) ([Mariusz Nowak](https://github.com/medikoo))
- Expose `isDashboardEnabled` resolver ([#10752](https://github.com/serverless/serverless/issues/10752)) ([ba34c57](https://github.com/serverless/serverless/commit/ba34c573f4d471bd724fe1a8e77c62e10d7c29c3)) ([Mariusz Nowak](https://github.com/medikoo))
- Generalize S3 upload dirname handling ([#10752](https://github.com/serverless/serverless/issues/10752)) ([9223b79](https://github.com/serverless/serverless/commit/9223b793161d3cb8e6075abb1254f1d707adb8ee)) ([Mariusz Nowak](https://github.com/medikoo))
- Introduce hooks tracking debug logs ([#10752](https://github.com/serverless/serverless/issues/10752)) ([efe1139](https://github.com/serverless/serverless/commit/efe11396be5c9f34a92b60b5c4217201e2f55a54)) ([Mariusz Nowak](https://github.com/medikoo))
- Mark `saveServiceState` internal function as async ([#10752](https://github.com/serverless/serverless/issues/10752)) ([4f895a2](https://github.com/serverless/serverless/commit/4f895a2e36f56eb65161af706c0c6f4f2d9a4655)) ([Mariusz Nowak](https://github.com/medikoo))

## [3.3.0](https://github.com/serverless/serverless/compare/v3.2.1...v3.3.0) (2022-02-18)

### Features

- **Variables:** Support for `--param` CLI options ([#10713](https://github.com/serverless/serverless/pull/10713)) ([964b883](https://github.com/serverless/serverless/commit/964b8834554e4607fa68f4460cab995af1352746)) ([Piotr Grzesik](https://github.com/pgrzesik))

### Bug Fixes

- **AWS Local Invocation:** Improve `ruby` context ([#10705](https://github.com/serverless/serverless/issues/10705)) ([ce5bf0b](https://github.com/serverless/serverless/commit/ce5bf0b40f64c087fa5ec114d0d28750b4813aaa)) ([Shalvah](https://github.com/shalvah))

### Maintenance Improvements

- **CLI:** Remove obsolete `v` postfix when listing global version ([#10708](https://github.com/serverless/serverless/pull/10708)) ([5013af0](https://github.com/serverless/serverless/commit/5013af01476fb3d13f31775ff4171bc98a35d39d)) ([Mariusz Nowak](https://github.com/medikoo))

### [3.2.1](https://github.com/serverless/serverless/compare/v3.2.0...v3.2.1) (2022-02-14)

### Bug Fixes

- **CLI:** Ensure to pass through `serverless-tencent` exit code ([#10698](https://github.com/serverless/serverless/pull/10698)) ([4d091b4](https://github.com/serverless/serverless/commit/4d091b42cbcfadf8f8922aba9e46f756ebfe3e88)) ([Mariusz Nowak](https://github.com/medikoo))
- **Config Schema:** Safe generation of standalone AJV validator ([#10680](https://github.com/serverless/serverless/pull/10680)) ([6093ee4](https://github.com/serverless/serverless/commit/6093ee480aceba35d7eb74d7a0ea3c378a596e63)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **Standalone:** Fix upgrade when temp dir is on other device ([#10684](https://github.com/serverless/serverless/pull/10684)) ([1b8d463](https://github.com/serverless/serverless/commit/1b8d463a08fb48cca0236874dd1cf68e477ba93d)) ([Mariusz Nowak](https://github.com/medikoo))

### Maintenance Improvements

- Upgrade to `@serverless/test` in `v10` ([4201b30](https://github.com/serverless/serverless/commit/4201b304a2b6582e5755944b1c4a0ff89ad2bcc1))

## [3.2.0](https://github.com/serverless/serverless/compare/v3.1.1...v3.2.0) (2022-02-10)

### Features

- **Plugins:** Support ESM format for plugins ([#10657](https://github.com/serverless/serverless/issues/10657)) ([ec3271f](https://github.com/serverless/serverless/commit/ec3271f3e8b7e055ad26eec89dfccfd3ca59fd0e)) ([frozenbonito](https://github.com/frozenbonito))

### Bug Fixes

- **AWS Deploy:** Add descriptive error if S3 bucket cant be cleaned ([#10668](https://github.com/serverless/serverless/pull/10668)) ([d4ee656](https://github.com/serverless/serverless/commit/d4ee656de1fd4cb6b2803cb531725a016cc7e428)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **Config Schema:** Recognize `provider.websocketsDescription` ([#10663](https://github.com/serverless/serverless/issues/10663)) ([9778751](https://github.com/serverless/serverless/commit/977875144798d4c1e2e37ecccc7bbab286f4684d)) ([Jérémy Benoist](https://github.com/j0k3r))
- **Variables:** Improve resolution of AWS auth related properties ([#10652](https://github.com/serverless/serverless/pull/10652)) ([e66c865](https://github.com/serverless/serverless/commit/e66c865a26c237273473429eb595295c2d7992af)) ([Mariusz Nowak](https://github.com/medikoo))
- Improve detection of `tty` ([#10662](https://github.com/serverless/serverless/pull/10662)) ([0c810bf](https://github.com/serverless/serverless/commit/0c810bf96a9f1000d9dead9459e0db652819ea02)) ([Piotr Grzesik](https://github.com/pgrzesik))
- Improve validation of min supported Node version ([#10655](https://github.com/serverless/serverless/pull/10655)) ([bf084f3](https://github.com/serverless/serverless/commit/bf084f3edd0891bb4947c9727c8d85684c3a423d)) ([Piotr Grzesik](https://github.com/pgrzesik))

### Maintenance Improvements

- **CLI:** Conditionally apply post dotenv resolution logic ([#10652](https://github.com/serverless/serverless/pull/10652)) ([30465cc](https://github.com/serverless/serverless/commit/30465ccb0bfd1b56b89833208b3d96dba2ae8119)) ([Mariusz Nowak](https://github.com/medikoo))
- **Variables:**
  - Ensure to mark `aws` as fulfilled source ([#10652](https://github.com/serverless/serverless/pull/10652)) ([a4c9392](https://github.com/serverless/serverless/commit/a4c93920830051ee67bebd0be815f8aa4c2ba234)) ([Mariusz Nowak](https://github.com/medikoo))
  - Optimize `provider.name` resolution handling ([#10652](https://github.com/serverless/serverless/pull/10652)) ([6e1f5ed](https://github.com/serverless/serverless/commit/6e1f5ed3f8fb76c5583b0f6f6bea086bf24ff6b4)) ([Mariusz Nowak](https://github.com/medikoo))
- Use templates from `examples` in `create` command ([#10576](https://github.com/serverless/serverless/pull/10576)) ([76a60ae](https://github.com/serverless/serverless/commit/76a60ae2b769c73657770392806eb59cfbb4d186)) ([Piotr Grzesik](https://github.com/pgrzesik))
- Change all occurences of succesful to successful ([#10639](https://github.com/serverless/serverless/issues/10639)) ([77f8e56](https://github.com/serverless/serverless/commit/77f8e56a6958824a727f8420c3ed1b06448b72f9)) ([Rohan Mukherjee](https://github.com/roerohan))

## [3.1.1](https://github.com/serverless/serverless/compare/v3.1.0...v3.1.1) (2022-02-02)

### Bug Fixes

- **AWS Deploy:** Ensure to clear `notificationArns` if needed during changeset deployment ([#10620](https://github.com/serverless/serverless/pull/10620)) ([a2e58cd](https://github.com/serverless/serverless/commit/a2e58cdeae51f7fc034743743354bf75c3817413)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **AWS Deploy:** Handle gently missing template body ([#10622](https://github.com/serverless/serverless/pull/10622)) ([195c3f2](https://github.com/serverless/serverless/commit/195c3f2f15b581ac8f400e091cbf40941a20ff5e)) ([Mariusz Nowak](https://github.com/medikoo))
- **AWS Deploy:** Properly apply `stackPolicy` with changesets ([#10617](https://github.com/serverless/serverless/pull/10617)) ([ee30a7b](https://github.com/serverless/serverless/commit/ee30a7be628de24dfdfe35bfd5ad7df3653891f7)) ([Piotr Grzesik](https://github.com/pgrzesik))

### Maintenance Improvements

- **CLI Onboarding:** Improve deploy messaging ([#10623](https://github.com/serverless/serverless/pull/10623)) ([97fda34](https://github.com/serverless/serverless/commit/97fda34b29ecd3711bcd4b94c741ff9b17663188)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **CLI:** Expose installation type by `serverless-tencent` version info ([#10621](https://github.com/serverless/serverless/pull/10621)) ([4c5f834](https://github.com/serverless/serverless/commit/4c5f8349050cb870f80f210be4f93f7fb55bd71c)) ([Mariusz Nowak](https://github.com/medikoo))
- **Config Schema:** Improve error message for non-function AJV validate ([#10625](https://github.com/serverless/serverless/pull/10625)) ([e4ee0a3](https://github.com/serverless/serverless/commit/e4ee0a39eaffc2b64030856c894a1c5e66270a07)) ([Piotr Grzesik](https://github.com/pgrzesik))

## [3.1.0](https://github.com/serverless/serverless/compare/v3.0.1...v3.1.0) (2022-02-01)

### Features

- **AWS ActiveMQ:** Support `maximumBatchingWindow` ([#10593](https://github.com/serverless/serverless/pull/10593)) ([658dc28](https://github.com/serverless/serverless/commit/658dc28b8b1e087948482553be98b12bd5783c09)) ([Richard Hull](https://github.com/rm-hull))
- **AWS Kafka:** Support `maximumBatchingWindow` ([#10591](https://github.com/serverless/serverless/pull/10591)) ([e90c114](https://github.com/serverless/serverless/commit/e90c114932362d79727800f0787237764ce767c3)) ([Richard Hull](https://github.com/rm-hull))
- **AWS MSK:** Support `maximumBatchingWindow` ([#10580](https://github.com/serverless/serverless/issues/10580)) ([d341b6b](https://github.com/serverless/serverless/commit/d341b6b99d61e44cbb00e18cbfd791e963890bfd)) ([Richard Hull](https://github.com/rm-hull))
- **AWS RabbitMQ:** Support `maximumBatchingWindow` ([#10598](https://github.com/serverless/serverless/pull/10598)) ([d0554b7](https://github.com/serverless/serverless/commit/d0554b738543221e0fe3d9c6fd83d30a15aae79f)) ([Richard Hull](https://github.com/rm-hull))
- Recognize `ap-southeast-3` AWS region ([#10586](https://github.com/serverless/serverless/issues/10586)) ([f77477e](https://github.com/serverless/serverless/commit/f77477e3cc6c0c13749af1352d28b88cbadbeb6b)) ([Jeremy Care](https://github.com/jeremycare))

### Bug Fixes

- **CLI:**
  - Fix support for `-c` (`--config`) shortcut ([#10607](https://github.com/serverless/serverless/pull/10607)) ([06fc4df](https://github.com/serverless/serverless/commit/06fc4df7880e8f03cb0dbd5229b7bd2a92e11a87)) ([Mariusz Nowak](https://github.com/medikoo))
  - Get `serverless-tencent` version from all supported locations ([#10608](https://github.com/serverless/serverless/pull/10608)) ([395ea7d](https://github.com/serverless/serverless/commit/395ea7d2a8d7c6d95417bde8448e6d58c2094125)) ([Mariusz Nowak](https://github.com/medikoo))

### [3.0.1](https://github.com/serverless/serverless/compare/v3.0.0...v3.0.1) (2022-01-28)

### Bug Fixes

- Report more meaningful strict schema mode error ([#10574](https://github.com/serverless/serverless/pull/10574)) ([e98d699](https://github.com/serverless/serverless/commit/e98d699e7800780e7d56340d778116e1b3b5b005)) ([Piotr Grzesik](https://github.com/pgrzesik))

### Maintenance Improvements

- **CLI Onboarding:** Minor wording adjustments ([#10575](https://github.com/serverless/serverless/pull/10575)) ([772a9bb](https://github.com/serverless/serverless/commit/772a9bb86c4b9b4e65f5f834c39620359cfc7c7a)) ([Piotr Grzesik](https://github.com/pgrzesik))

### Templates

- Update dependencies of `aws-nodejs-typescript` to v3 ([#10582](https://github.com/serverless/serverless/pull/10582)) ([88ac3d0](https://github.com/serverless/serverless/commit/88ac3d0586b3ed98ee0c1b7c618cbca095ee85d3)) ([Paul Lessing](https://github.com/paullessing))

## [3.0.0](https://github.com/serverless/serverless/compare/v2.72.2...v3.0.0) (2022-01-27)

We are excited to announce the release of Serverless Framework v3!

This new major version brings **a cleaner and redesigned CLI experience** as well as a brand new feature: **stage parameters**.

Read all about Serverless Framework v3 **[in the official blog post](https://www.serverless.com/blog/serverless-framework-v3-is-live)**.

<a title="Serverless Framework v3 is live!" href="https://www.serverless.com/blog/serverless-framework-v3-is-live"><img src="https://assets-global.website-files.com/60acbb950c4d66d0ab3e2007/6193d4f3300e602de28a56e8_6193d008f4d92d593c0e6fb1_6193c1d7c81caf0fa82bbe65_terminal-light.gif" width="700"></a>

---

### ⚠ BREAKING CHANGES

Read the [**complete v3 Upgrade Guide**](https://www.serverless.com/framework/docs/guides/upgrading-v3).

- **Variables:** Old variables resolver is permanently removed. Any resolution error as approached with current resolver is assumed as final (there's no longer fallback to old resolver)
- **AWS Lambda:**
  - Default lambda hashing algorithm was changed to `20201221`
  - Runtimes `nodejs10.x`, `python2.7`, `ruby2.5` and `dotnetcore2.1` reached end of support on AWS and are no longer recognized in configuration.
  - Default runtime has been changed from `nodejs12.x` to `nodejs14.x`
  - Properties `service.awsKmsKeyArn` and `functions[].awsKmsKeyArn` are no longer supported. Use `provider.kmsKeyArn` and `functions[].kmsKeyArn` instead.
- **CLI:**
  - CLI params put before command tokens are no longer recgonized (e.g. `sls -f <function-name> deploy function` will no longer work). In all cases construct CLI args in `sls <command> <options>` order
  - Unrecognized CLI options will no longer be supported and will result in an error.
  - `enableLocalInstallationFallback` configuration property is no longer supported.
  - Remove `studio` command schema
  - The `--verbose` CLI flag does no longer support `-v` alias
  - Opt-in tab-tab autocompletion feature is removed due to performance and security issues
- **AWS API Gateway:**
  - Enabling logs or tracing for imported API Gateway will now result in an error instead of warning
  - For authorizers with `request` type and caching disabled (`resultTtlInSeconds: 0`), the `identitySource` will no longer be set to `method.request.header.Authorization` by default.
  - Support for `usagePlan`, `resourcePolicy` and `apiKeys` on `provider` level is removed. Use `provider.apiGateway` level instead to set them.
  - Support for `http.request.schema` has been removed and replaced with `http.request.schemas`.
- **AWS HTTP API:** Tags from `provider.tags` are applied by default to HTTP API Gateway.
- **AWS CloudFront:** Support for `MinTTL`, `MaxTTL`, `DefaultTTL` and `ForwardedValues` on `cloudfront.behavior` has been removed.
- **AWS EventBridge:** By default, EventBridge resources now will be deployed using native CloudFormation resources instead of Custom Resources.
- **AWS Alexa:** Support for simple `alexaSkill` event was removed and now `appId` is required for all `alexaSkill` events.- Serverless Components (`@serverless/components`) CLI is no longer integrated with Framework CLI.
- **Dashboard:** `tenant` configuration setting is no longer respected. Ensure to rely on `org` instead
- **AWS Deploy:** Deployment now uses change sets instead of direct stack updates.
- Serverless Components v1 (`@serverless/cli`) CLI is no longer integrated with Framework CLI.
- Custom nested configuration paths will no longer be supported and such usage will result in an error.
- Object notation is no longer supported for `service` property. Set name directly to `service`.
- When creating `Serverless` class instance programatically, both `options` and `commands` have to be passed via `config` to the constructor.
- Duplicate plugin definition in configuration will now result in an error instead of a warning.
- Using `--aws-s3-accelerate` flag will result in an error instead of deprecation when custom S3 bucket is used.
- Removed support for `provider.disableDefaultOutputExportNames`
- Node.js versions lower than v12.13.0 (LTS) is no longer supported
- Lifecycle events marked as deprecated (in context of v1) are no longer evaluated

### Features

- **Variables:** Remove old variables resolver ([#10512](https://github.com/serverless/serverless/issues/10512)) ([9bf6c16](https://github.com/serverless/serverless/commit/9bf6c16cb787ae48092d90bd7613d86a1c8ca075)) ([Mariusz Nowak](https://github.com/medikoo))
- **Packaging:** Deprecate `package.include` and `package.exclude` ([#10348](https://github.com/serverless/serverless/issues/10348)) ([aa4f9e3](https://github.com/serverless/serverless/commit/aa4f9e344e313f1ca64fa7af9475e6b84be8fb56)) ([Mariusz Nowak](https://github.com/medikoo))
- **CLI:**
  - Unconditionally fallback when local installation found ([#10503](https://github.com/serverless/serverless/issues/10503)) ([137554c](https://github.com/serverless/serverless/commit/137554c9d35eb14bf3bba654673b99d343c0a7d1)) ([Mariusz Nowak](https://github.com/medikoo))
  - Simplify `logs` command output ([#10203](https://github.com/serverless/serverless/issues/10203)) ([d4124a3](https://github.com/serverless/serverless/commit/d4124a3ca6d3895289ef605d4dc6e5eb0cd2e3df)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Deprecate support for `deploy -f` alias ([#10346](https://github.com/serverless/serverless/issues/10346)) ([09c9ea3](https://github.com/serverless/serverless/commit/09c9ea3a38afc30c1c15d21c926b8d06dfd81356)) ([Mariusz Nowak](https://github.com/medikoo))
  - Deprecate missing options schema ([#10394](https://github.com/serverless/serverless/issues/10394)) ([0db9c49](https://github.com/serverless/serverless/commit/0db9c49e2d435499e2b836b948e815b4a8839521)) ([Mariusz Nowak](https://github.com/medikoo))
  - Deprecate recognition of `projectDir` configuration setting ([#10511](https://github.com/serverless/serverless/issues/10511)) ([00fcd83](https://github.com/serverless/serverless/commit/00fcd83f49703188f3ddb0317afaa88fbece4801)) ([Mariusz Nowak](https://github.com/medikoo))
  - Global `--debug` flag for debug logging ([#10197](https://github.com/serverless/serverless/issues/10197)) ([3b4f267](https://github.com/serverless/serverless/commit/3b4f2677f8d83fd76a47bfac781bf1b81bfec924)) ([Mariusz Nowak](https://github.com/medikoo))
  - Global `--verbose` flag for verbose logging ([#10197](https://github.com/serverless/serverless/issues/10197)) ([2eef264](https://github.com/serverless/serverless/commit/2eef264bdca3dc7ae270aa09b974f23546425344)) ([Mariusz Nowak](https://github.com/medikoo))
  - Register `-v` as global `--version` alias ([#10332](https://github.com/serverless/serverless/issues/10332)) ([211db81](https://github.com/serverless/serverless/commit/211db8149cad519174490fbb5d2f1f42f859aabb)) ([Mariusz Nowak](https://github.com/medikoo))
  - Remove `-v` alias for `--verbose` flag ([#10153](https://github.com/serverless/serverless/issues/10153)) ([03b77c0](https://github.com/serverless/serverless/commit/03b77c0d2392e74f7d5caf76b9c01675d6d14023)) ([Mariusz Nowak](https://github.com/medikoo))
  - Remove support for unrecognized cli options ([#10172](https://github.com/serverless/serverless/issues/10172)) ([7c2b2ea](https://github.com/serverless/serverless/commit/7c2b2ea6a84c62fcb5c8830c16437376002b2a10)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Simplify CLI args parsing to `<command> <options>` format ([#10332](https://github.com/serverless/serverless/issues/10332)) ([8229812](https://github.com/serverless/serverless/commit/8229812e2bd1632efd9c8c8999236f6dff79171c)) ([Mariusz Nowak](https://github.com/medikoo))
  - Support `serverless-tencent` CLI ([#10305](https://github.com/serverless/serverless/issues/10305)) ([10db944](https://github.com/serverless/serverless/commit/10db944c73357014db20062c70ec666898505b0f)) ([Mariusz Nowak](https://github.com/medikoo))
  - Do not decorate `cli.log` logs ([#10196](https://github.com/serverless/serverless/issues/10196)) ([1f44227](https://github.com/serverless/serverless/commit/1f44227b7feeef30ca2ac151fffe219bde6a8461)) ([Mariusz Nowak](https://github.com/medikoo))
  - Expose `sls doctor` command ([#10504](https://github.com/serverless/serverless/issues/10504)) ([d403bfc](https://github.com/serverless/serverless/commit/d403bfc94eb13490d6a91d3352ae3b163caa6d68)) ([Mariusz Nowak](https://github.com/medikoo))
  - Remove `studio` command schema ([#10191](https://github.com/serverless/serverless/issues/10191)) ([7f1e7e1](https://github.com/serverless/serverless/commit/7f1e7e163b65580a2f0d10cad012f69605f32b18)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Remove tab autocomplete feature ([#10414](https://github.com/serverless/serverless/issues/10414)) ([519ce0c](https://github.com/serverless/serverless/commit/519ce0cb77056ba53be92968958f55f8eb7cc779)) ([Mariusz Nowak](https://github.com/medikoo))
- **AWS Lambda:**
  - Change default hashing algorithm ([#10255](https://github.com/serverless/serverless/issues/10255)) ([775debf](https://github.com/serverless/serverless/commit/775debf5e2bebc51346853d99d109776f9856cee)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Change default runtime to `nodejs14.x` ([#10147](https://github.com/serverless/serverless/issues/10147)) ([30e99fb](https://github.com/serverless/serverless/commit/30e99fb92f72a968f8e1c9a1ddbbb81a6bdc5288)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Remove support for `awsKmsKeyArn` setting ([#10146](https://github.com/serverless/serverless/issues/10146)) ([6de37bf](https://github.com/serverless/serverless/commit/6de37bf3b7c14ca84a32188b377e92dfbd0af473)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Remove support for obsolete runtimes ([#10207](https://github.com/serverless/serverless/issues/10207)) ([23cfb63](https://github.com/serverless/serverless/commit/23cfb63cdf400ac4601f13571554f4d8fc5ee0cd)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **AWS HTTP API:**
  - Always apply `provider.tags` to HTTP API ([#10141](https://github.com/serverless/serverless/issues/10141)) ([b34d549](https://github.com/serverless/serverless/commit/b34d5497b6290635037f6d8f3b65451803ef6027)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Deprecate `provider.httpApi.useProviderTags` ([#105](https://github.com/serverless/serverless/issues/105)) ([fee410a](https://github.com/serverless/serverless/commit/fee410a445b088d4fb86074924604208043934c0)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **AWS API Gateway:**
  - Change default identity source for authorizers ([#10168](https://github.com/serverless/serverless/issues/10168)) ([1139255](https://github.com/serverless/serverless/commit/11392557d2800cdf226bd17bd32407f61a9dba52)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Error on tracing or logs set for external API ([#10198](https://github.com/serverless/serverless/issues/10198)) ([64ea6e5](https://github.com/serverless/serverless/commit/64ea6e59b5bbd1c807a948fd092c5792923e9559)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Remove API specific settings from `provider` ([#10157](https://github.com/serverless/serverless/issues/10157)) ([99941f0](https://github.com/serverless/serverless/commit/99941f0a5723aef0395ea0fb5b059e9ade8321b4)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Remove support for `request.schema` ([#10143](https://github.com/serverless/serverless/issues/10143)) ([b8019d8](https://github.com/serverless/serverless/commit/b8019d82ccabf732a75c2f97c958b84efb1e43ef)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **AWS CloudFront:** Remove support for deprecated `behavior` props ([#10149](https://github.com/serverless/serverless/issues/10149)) ([c22277f](https://github.com/serverless/serverless/commit/c22277f69c327f271ea5cd51c98538c9b4eb7b1b)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **AWS EventBridge:** Change default deployment method to native CF ([#10164](https://github.com/serverless/serverless/issues/10164)) ([46956f3](https://github.com/serverless/serverless/commit/46956f3e9f5dde9367669b0d9c1ca2dc454bfc8e)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **AWS IAM:** Deprecate IAM settings grouped directly at `provider` ([#10348](https://github.com/serverless/serverless/issues/10348)) ([d7fd239](https://github.com/serverless/serverless/commit/d7fd23997f570c868437a5ea0187797403f8fe0a)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **Plugins:** Pass log writers to plugin constructor ([#10140](https://github.com/serverless/serverless/issues/10140)) ([57079b7](https://github.com/serverless/serverless/commit/57079b78a671d7756c768f3136518f6a6f46d8ef)) ([Mariusz Nowak](https://github.com/medikoo))
- **Config Schema:** Deprecate `warn` as a validation mode default ([#10348](https://github.com/serverless/serverless/issues/10348)) ([6e27cc1](https://github.com/serverless/serverless/commit/6e27cc18c6c50fbd3311427e92c9e7f16055ae85)) ([Mariusz Nowak](https://github.com/medikoo))
- **Standalone:** Upgrade `npm` to v8 ([#10349](https://github.com/serverless/serverless/issues/10349)) ([6bfdc0c](https://github.com/serverless/serverless/commit/6bfdc0cda4b2009e4433f2fda45356c5d297c172)) ([Mariusz Nowak](https://github.com/medikoo))
- **Dashboard:** Drop support for `tenant` ([#10525](https://github.com/serverless/serverless/issues/10525)) ([9894875](https://github.com/serverless/serverless/commit/98948750e6cb856c62f1b4f4138a5157da07ae7e)) ([Mariusz Nowak](https://github.com/medikoo))
- **AWS Alexa:** Remove support for alexaSkill without appId ([#10142](https://github.com/serverless/serverless/issues/10142)) ([a9edd06](https://github.com/serverless/serverless/commit/a9edd063039a41fee1679827f7abe0e754036b45)) ([Piotr Grzesik](https://github.com/pgrzesik))
- Disallow custom nested configuration path ([#10205](https://github.com/serverless/serverless/issues/10205)) ([aeb9a57](https://github.com/serverless/serverless/commit/aeb9a57681cc3ff67c6dedbbf051b0c42d8ba6bb)) ([Piotr Grzesik](https://github.com/pgrzesik))
- Error instead of warning when missing `commands` or `options` ([#10158](https://github.com/serverless/serverless/issues/10158)) ([f86f691](https://github.com/serverless/serverless/commit/f86f69131678a3a9be13acaeba0b56b751e6ce57)) ([Piotr Grzesik](https://github.com/pgrzesik))
- Remove `@serverless/cli` CLI integration ([#10462](https://github.com/serverless/serverless/issues/10462)) ([396cfb9](https://github.com/serverless/serverless/commit/396cfb9621a5db211e2853b8105386103f9f097c)) ([Mariusz Nowak](https://github.com/medikoo))
- Remove `@serverless/components` CLI integration ([#10327](https://github.com/serverless/serverless/issues/10327)) ([3395395](https://github.com/serverless/serverless/commit/33953958ae354b240e6d949b889e376dcce09cc8)) ([Mariusz Nowak](https://github.com/medikoo))
- Remove support for `provider.disableDefaultOutputExportNames` ([#10148](https://github.com/serverless/serverless/issues/10148)) ([a9cd331](https://github.com/serverless/serverless/commit/a9cd3317b2e68b1b08c3f7388a2d4d459db1f2d7)) ([Piotr Grzesik](https://github.com/pgrzesik))
- Remove support for Node v10 ([#10186](https://github.com/serverless/serverless/issues/10186)) ([90f00b7](https://github.com/serverless/serverless/commit/90f00b7c02113932034f4e3ee3ef659b1ec0db02)) ([Piotr Grzesik](https://github.com/pgrzesik))
- Remove support for object notation for `service` ([#10156](https://github.com/serverless/serverless/issues/10156)) ([bccd188](https://github.com/serverless/serverless/commit/bccd188a0da7fe335b3e2b573f3ab19ccd0c49f8)) ([Piotr Grzesik](https://github.com/pgrzesik))
- Restrict stage name with pattern ([c8c9f49](https://github.com/serverless/serverless/commit/c8c9f49fd239df723e3841fbfe22abdb90c02dae)) ([Mariusz Nowak](https://github.com/medikoo))
- Support `params` configuration ([#10400](https://github.com/serverless/serverless/issues/10400)) ([4675b57](https://github.com/serverless/serverless/commit/4675b57117e7d850a6015ab97c81938b9f374bf1)) ([Mariusz Nowak](https://github.com/medikoo))
- Throw error on duplicated plugin definition ([#10150](https://github.com/serverless/serverless/issues/10150)) ([d3aca0a](https://github.com/serverless/serverless/commit/d3aca0a7955c48b123720a887e6dd7300475fe03)) ([Piotr Grzesik](https://github.com/pgrzesik))
- Throw for `--aws-s3-accelerate` when custom bucket used ([#10151](https://github.com/serverless/serverless/issues/10151)) ([b7d48e5](https://github.com/serverless/serverless/commit/b7d48e59fdbe2a2056c6352d6ac33d4c43099e53)) ([Piotr Grzesik](https://github.com/pgrzesik))

### Maintenance Improvements

- **AWS Deploy:** Use change sets in CF deployments ([#10390](https://github.com/serverless/serverless/issues/10390)) ([e2c65a2](https://github.com/serverless/serverless/commit/e2c65a2230b9bf9fb78c7445b02d3ee4945ee1aa)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **CLI Onboarding:** Download templates from v3 examples branch ([#10482](https://github.com/serverless/serverless/issues/10482)) ([ded1b0e](https://github.com/serverless/serverless/commit/ded1b0e832c420871ffe37fedff0afe990d1d3e6)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **CLI:**
  - Convert `isLocallyInstalled` to export result directly ([#10503](https://github.com/serverless/serverless/issues/10503)) ([ad0bbb0](https://github.com/serverless/serverless/commit/ad0bbb0a9161bc823d1c542e6dbf993f436f6b5a)) ([Mariusz Nowak](https://github.com/medikoo))
  - Export resolved local installation path directly ([#10503](https://github.com/serverless/serverless/issues/10503)) ([fb3b39a](https://github.com/serverless/serverless/commit/fb3b39a5a9bd35e211600530a30fc5583deec0db)) ([Mariusz Nowak](https://github.com/medikoo))
  - Improve post install log to reflect modern style ([#10418](https://github.com/serverless/serverless/issues/10418)) ([843764b](https://github.com/serverless/serverless/commit/843764baf837f195ec8ee911f103c9f3817f9a10)) ([Mariusz Nowak](https://github.com/medikoo))
  - Improve progress for CloudFormation updates ([#10458](https://github.com/serverless/serverless/issues/10458)) ([14b1443](https://github.com/serverless/serverless/commit/14b14432730c77ca34d41000e9aaaad0c29ffb35)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Seclude `paramRegExp` ([#10346](https://github.com/serverless/serverless/issues/10346)) ([703e40f](https://github.com/serverless/serverless/commit/703e40f0d217d925560ba2c1d43b403bb61d335b)) ([Mariusz Nowak](https://github.com/medikoo))
  - Seclude uncaught exception handling ([#10542](https://github.com/serverless/serverless/issues/10542)) ([b4bd0d4](https://github.com/serverless/serverless/commit/b4bd0d437074a29a972ecdbdc3a026554657817e)) ([Mariusz Nowak](https://github.com/medikoo))
  - Unify finalization of a process handling ([#10542](https://github.com/serverless/serverless/issues/10542)) ([29357f4](https://github.com/serverless/serverless/commit/29357f4e182f102504e5ea841fb95915ccfe6821)) ([Mariusz Nowak](https://github.com/medikoo))
  - Move `isLocalyInstalled` util to CLI context ([#105](https://github.com/serverless/serverless/issues/105)) ([3dc8395](https://github.com/serverless/serverless/commit/3dc8395d88dfebf4742625ec054955c40a4e2499)) ([Mariusz Nowak](https://github.com/medikoo))
- **Config Schema:**
  - Upgrade `ajv` to `v8` along with related packages ([#10440](https://github.com/serverless/serverless/issues/10440)) ([15cd724](https://github.com/serverless/serverless/commit/15cd724f723b55ca73cd0bb00d41d67307ffbed8)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Do not rely on `ajv-keywords` ([#10490](https://github.com/serverless/serverless/issues/10490)) ([#10490](https://github.com/serverless/serverless/issues/10490)) ([4a22a4e](https://github.com/serverless/serverless/commit/4a22a4e58cd8c10d6da34a094a0768b5caafbdb9)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **Telemetry:** Include `paramsCount` in telemetry ([#10460](https://github.com/serverless/serverless/issues/10460)) ([dd721b0](https://github.com/serverless/serverless/commit/dd721b0a2038e4b7256593397b5db19833cef387)) ([Piotr Grzesik](https://github.com/pgrzesik))
- Rely on `require.resolve` to detect wether module exist ([#10503](https://github.com/serverless/serverless/issues/10503)) ([040be5f](https://github.com/serverless/serverless/commit/040be5fe7321e051bb6e5e1aa78458c17d2582bc)) ([Mariusz Nowak](https://github.com/medikoo))
- Remove `legacy` logs ([#10527](https://github.com/serverless/serverless/issues/10527)) ([a92ab91](https://github.com/serverless/serverless/commit/a92ab917128629e4e516d69976fdac1014cb5ebb)) ([Piotr Grzesik](https://github.com/pgrzesik))
- Remove `lib/classes/Error.js` ([#10563](https://github.com/serverless/serverless/issues/10563)) ([44391fa](https://github.com/serverless/serverless/commit/44391fac513c7941447d03bdeae95043590cc52c)) ([Mariusz Nowak](https://github.com/medikoo))
- Remove evaluation of deprecated lifecycle events ([#10345](https://github.com/serverless/serverless/issues/10345)) ([34bb51e](https://github.com/serverless/serverless/commit/34bb51e71d542e31a13cfb0f56443d57b6e0f89a)) ([Mariusz Nowak](https://github.com/medikoo))
- Remove internal `suppressLogIfPrintCommand` method ([#10526](https://github.com/serverless/serverless/issues/10526)) ([584286e](https://github.com/serverless/serverless/commit/584286ec7aba94ac96eb747361f79fafb7c0f32b)) ([Mariusz Nowak](https://github.com/medikoo))
- Unify file naming convention ([#10563](https://github.com/serverless/serverless/issues/10563)) ([Mariusz Nowak](https://github.com/medikoo))
- Replace `ncjsm/resolve` usage with native `createRequire` ([#10503](https://github.com/serverless/serverless/issues/10503)) ([d18efc2](https://github.com/serverless/serverless/commit/d18efc2d43789dc11857d677851ba4b66e09a6a4)) ([Mariusz Nowak](https://github.com/medikoo))
- Adapt to rename in `@serverless/dashboard-plugin` ([#10543](https://github.com/serverless/serverless/issues/10543)) ([88234a5](https://github.com/serverless/serverless/commit/88234a51233e74b3155427a5bf0a4022ec182c04)) ([Mariusz Nowak](https://github.com/medikoo))
- Upgrade `@serverless/utils` to v6 ([74d9c70](https://github.com/serverless/serverless/commit/74d9c70f8abbfab1af4c6440ed93fd163145a597)) ([Mariusz Nowak](https://github.com/medikoo))

### [2.72.3](https://github.com/serverless/serverless/compare/v2.72.2...v2.72.3) (2022-02-22)

### Maintenance Improvements

- Improve CLI options deprecation message ([#10740](https://github.com/serverless/serverless/pull/10740)) ([58ed08c](https://github.com/serverless/serverless/commit/58ed08c9ff5bf4d41256c462a72aad7e580b5551)) ([Piotr Grzesik](https://github.com/pgrzesik))

### [2.72.2](https://github.com/serverless/serverless/compare/v2.72.1...v2.72.2) (2022-01-24)

### Bug Fixes

- **Variables:** Fix too eager nested resolution tracking ([#10554](https://github.com/serverless/serverless/issues/10554)) ([8db03c9](https://github.com/serverless/serverless/commit/8db03c90ffba68ebda800d2a009452cd09f7bf7f)) ([Steven Noorbergen](https://github.com/steven-xaroth))

### [2.72.1](https://github.com/serverless/serverless/compare/v2.72.0...v2.72.1) (2022-01-21)

### Maintenance Improvements

- Refactor direct use of `@serverless/utils/log` ([#10534](https://github.com/serverless/serverless/pull/10534)) ([05fb97f](https://github.com/serverless/serverless/commit/05fb97fdab0c0ddc471ca554e48e09e661f797db)) ([Piotr Grzesik](https://github.com/pgrzesik))

## [2.72.0](https://github.com/serverless/serverless/compare/v2.71.0...v2.72.0) (2022-01-17)

### Features

- **CLI Onboarding:** Auto login if `org` provided or configured ([#10510](https://github.com/serverless/serverless/pull/10510)) ([dcf5273](https://github.com/serverless/serverless/commit/dcf52731ea3920ecf16b2484e2673080acbfe1cd)) ([Piotr Grzesik](https://github.com/pgrzesik))

### Bug Fixes

- **CLI:** Respect old Node.js versions in version detection ([#10499](https://github.com/serverless/serverless/pull/10499)) ([427920e](https://github.com/serverless/serverless/commit/427920ee0fc1c98109c0b673c794baac1cc5caf7)) ([Mariusz Nowak](https://github.com/medikoo))

### Maintenance Improvements

- **AWS Deploy:** Improve custom resource generation log ([#10496](https://github.com/serverless/serverless/pull/10496)) ([521861b](https://github.com/serverless/serverless/commit/521861b6510fd345c2b596e4ec9e9ef7be01ac10)) ([Mariusz Nowak](https://github.com/medikoo))
- **CLI Onboarding:** Improve user message when `app` does not exist ([#10509](https://github.com/serverless/serverless/pull/10509)) ([20afe33](https://github.com/serverless/serverless/commit/20afe339231112e4d5ade9498386ac3c00e37e04)) ([Mariusz Nowak](https://github.com/medikoo))
- Ensure support for `warn` mode for modern deprecations ([#10502](https://github.com/serverless/serverless/pull/10502)) ([82303b3](https://github.com/serverless/serverless/commit/82303b38942b35fa6cb8ad3f19f2d528a1736587)) ([Piotr Grzesik](https://github.com/pgrzesik))
- Support `conceal` option in modern logs ([#10501](https://github.com/serverless/serverless/pull/10501)) ([0dacf1b](https://github.com/serverless/serverless/commit/0dacf1bb3bd53da32a24cf2286cf081aecf22806)) ([Piotr Grzesik](https://github.com/pgrzesik))

### Templates

- Ensure `esbuild` dependency in `aws-nodejs-typescript` ([#10484](https://github.com/serverless/serverless/pull/10484)) ([452e4d8](https://github.com/serverless/serverless/commit/452e4d8279802ab2ce1ca300ab2c75ec8588a9e8)) ([François Farge](https://github.com/fargito))

## [2.71.0](https://github.com/serverless/serverless/compare/v2.70.0...v2.71.0) (2022-01-10)

### Features

- **AWS Cognito:** Support `forceDeploy` setting ([#10435](https://github.com/serverless/serverless/issues/10435)) ([c67a3f1](https://github.com/serverless/serverless/commit/c67a3f1a4fe6c64f2b6c68ef1b184b2642ad2266)) ([TsimpDim](https://github.com/TsimpDim))
- **Variables:** Resign from `projectDir` concept ([#10478](https://github.com/serverless/serverless/pull/10478)) ([5a76437](https://github.com/serverless/serverless/commit/5a764373c49d5fb313f50218ab8166f1638c2c32)) ([Mariusz Nowak](https://github.com/medikoo))

### Bug Fixes

- **CLI:** Fix handling of provider URL handling ([#10461](https://github.com/serverless/serverless/pull/10461)) ([7ebe133](https://github.com/serverless/serverless/commit/7ebe133b35fa9affafd73b61ee4626d8ce5aee1f)) ([Mariusz Nowak](https://github.com/medikoo))
- **Config Schema:** Address invalid schema definitions ([#10452](https://github.com/serverless/serverless/pull/10452)) ([9e1fe0a](https://github.com/serverless/serverless/commit/9e1fe0ad5da8b936ccb238041fb2b452e6309faf)) ([Piotr Grzesik](https://github.com/pgrzesik))

### Maintenance Improvements

- **CLI Onboarding:** Download templates from v2 examples branch ([#10447](https://github.com/serverless/serverless/pull/10447)) ([46d090a](https://github.com/serverless/serverless/commit/46d090a302b9f7f4a3cf479695489b7ffc46b75b)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **CLI:** Ensure telemetry logs are issued at debug level ([#10424](https://github.com/serverless/serverless/pull/10424)) ([7b36038](https://github.com/serverless/serverless/commit/7b360386eadb9a83af73514ced34bc901af43457)) ([Mariusz Nowak](https://github.com/medikoo))

### Templates

- Upgrade `log4j` to `2.17.1` in corresponding templates ([#10430](https://github.com/serverless/serverless/issues/10430)) ([2c3ab1d](https://github.com/serverless/serverless/commit/2c3ab1db9aa7c22c315957d1e474568e62e07e37)) ([Graham Campbell](https://github.com/GrahamCampbell))

## [2.70.0](https://github.com/serverless/serverless/compare/v2.69.1...v2.70.0) (2021-12-27)

### Features

- **AWS API Gateway:** Allow use of custom authorizer with authorizerId ([#10384](https://github.com/serverless/serverless/pull/10384)) ([c0eda27](https://github.com/serverless/serverless/commit/c0eda272901fd91947c6f37589b33f65c804dc9b)) ([Adam Lanners](https://github.com/darksun))
- **AWS Local Invocation:** Upgrade `log4j` to version 2.17.0 ([#10396](https://github.com/serverless/serverless/issues/10396)) ([2782ed4](https://github.com/serverless/serverless/commit/2782ed4221caa410708cbabbbd09d45a6363be29)) ([Vassili Gorshkov](https://github.com/atlasgurus))

### Bug Fixes

- **AWS API Gateway:** Meaningfully reject missing `restApiRootResourceId` ([#10371](https://github.com/serverless/serverless/issues/10371)) ([2c0a962](https://github.com/serverless/serverless/commit/2c0a962c4fc0ad82ecbc6a266d56bfaa81ad8054)) ([Sudipto Das](https://github.com/sdas13))
- **AWS Deploy:** Fix reliability of VPC config change detection in `deploy function` ([#10409](https://github.com/serverless/serverless/issues/10409)) ([0190d0d](https://github.com/serverless/serverless/commit/0190d0df05f4e37c8e965913ef1ceaf6b8a9b525)) ([Piotr Grzesik](https://github.com/pgrzesik))

### Templates

- Upgrade `log4j` in `aws-lambda-java-log4j2` ([#10383](https://github.com/serverless/serverless/issues/10383)) ([786f5e4](https://github.com/serverless/serverless/commit/786f5e45d54ae9925649367b0a0e8660eda542e6)) ([Marina](https://github.com/MarinaMeza))
- Upgrade `log4j` in `aws-kotlin-jvm-gradle` ([#10382](https://github.com/serverless/serverless/issues/10382)) ([7bf8f1b](https://github.com/serverless/serverless/commit/7bf8f1b723cc4f6624df7be3d27f246b3a826140)) ([Varun](https://github.com/varun73))
- Upgrade `log4j` dependencies ([#10392](https://github.com/serverless/serverless/issues/10392)) ([86fa604](https://github.com/serverless/serverless/commit/86fa60445c83cf35f3411ae49c2a1c4fc7fd82f0)) ([Juan Bermúdez](https://github.com/JuanBermudezN))

### Maintenance Improvements

- **Telemetry:**
  - Report `didCreateService` property ([#10406](https://github.com/serverless/serverless/pull/10406)) ([4fa20a5](https://github.com/serverless/serverless/commit/4fa20a56eafcab9d8675baa2f0fe6a9c6ee5e184)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Report `projectId` in remove command ([#10415](https://github.com/serverless/serverless/pull/10415)) ([0de3bc3](https://github.com/serverless/serverless/commit/0de3bc3cb9c1685226ea0c610e030f9279e79e4e)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Ensure to report `projectId` for interactive ([#10406](https://github.com/serverless/serverless/pull/10406)) ([08b5acb](https://github.com/serverless/serverless/commit/08b5acbaa901c7ce529064c394151e05bdd43aef)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **CLI:** Replace internal old logging utils with modern interface ([#10417](https://github.com/serverless/serverless/pull/10417)) ([5a451ad](https://github.com/serverless/serverless/commit/5a451ad0249b6924cd4105e5c372028402517ecd)) ([Mariusz Nowak](https://github.com/medikoo))
- **Variables:** Support custom sources in internal resolver ([#10393](https://github.com/serverless/serverless/pull/10393)) ([365a7f1](https://github.com/serverless/serverless/commit/365a7f13afaf40e9e2d573b0668159d6dea7aa02)) ([Mariusz Nowak](https://github.com/medikoo))

## [2.69.1](https://github.com/serverless/serverless/compare/v2.69.0...v2.69.1) (2021-12-15)

### Bug Fixes

- **AWS Lambda:** Fix event config setup for provisioned lambdas ([#10366](https://github.com/serverless/serverless/pull/10366)) ([3b4e453](https://github.com/serverless/serverless/commit/3b4e4539d8b56de6a7cccb2e9c8455f34a5289f6)) ([Mariusz Nowak](https://github.com/medikoo))
- **CLI:**
  - Do not crash on help request ([#10347](https://github.com/serverless/serverless/pull/10347)) ([f6feb0b](https://github.com/serverless/serverless/commit/f6feb0b7b3b5ceb727119056e44e756a8105ec5b)) ([Mariusz Nowak](https://github.com/medikoo))
  - Improve error handler resolution ([#10367](https://github.com/serverless/serverless/pull/10)) ([0dedd3e](https://github.com/serverless/serverless/commit/0dedd3e8790f568527b8a2444720fe47048ba719)) ([Mariusz Nowak](https://github.com/medikoo))

### Templates

- Upgrade `log4j` in Java based templates ([#10363](https://github.com/serverless/serverless/issues/10363)) ([7de020b](https://github.com/serverless/serverless/commit/7de020bbadad0aed47859f2129c9e58409b9ac65)) ([Vassili Gorshkov](https://github.com/atlasgurus))
- Upgrade `log4j` in Java based templates ([#10339](https://github.com/serverless/serverless/issues/10339)) ([c1df4f8](https://github.com/serverless/serverless/commit/c1df4f860a585ff62c364ac8fd6d8b64b323b156)) ([Vassili Gorshkov](https://github.com/atlasgurus))

## [2.69.0](https://github.com/serverless/serverless/compare/v2.68.0...v2.69.0) (2021-12-13)

### Features

- **AWS Deploy:** Ensure existence of S3 deployment bucket (if possible) ([#10317](https://github.com/serverless/serverless/pull/10317)) ([f358585](https://github.com/serverless/serverless/commit/f35858599ad749b5417c238f510e726615e221dc)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **AWS Kafka:** Add support for `mTLS` access configuration ([#10273](https://github.com/serverless/serverless/issues/10273)) ([9faf37a](https://github.com/serverless/serverless/commit/9faf37aa153a60784ca783b1e2b7364625e8761f)) ([Misha Bruml](https://github.com/mishabruml))
- **Standalone:**
  - Support installation on M1-based Macs ([#10291](https://github.com/serverless/serverless/pull/10291)) ([92ae054](https://github.com/serverless/serverless/commit/92ae054f02dc631c178628492af7049ce2936204)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Use Node 16 as base for binaries ([#10291](https://github.com/serverless/serverless/pull/10291)) ([eb8f474](https://github.com/serverless/serverless/commit/eb8f474940c4cd69f08ec062adfaa15d62d81ee2)) ([Piotr Grzesik](https://github.com/pgrzesik))

### Bug Fixes

- **AWS Deploy:**
  - Allow removal of stack with bucket missing ([#10306](https://github.com/serverless/serverless/pull/10306)) ([1a85a4a](https://github.com/serverless/serverless/commit/1a85a4a901caf4ca05096bf11bfcad31959c8044)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Ensure to strip all `null` properties from CloudFormation template ([#10304](https://github.com/serverless/serverless/issues/10304)) ([1f58760](https://github.com/serverless/serverless/commit/1f58760f467f2dcb960e23c2eb028f4abef23209)) ([GurmeharS](https://github.com/GurmeharS))
  - Recognize all boolean values at `provider.disableRollback` ([#10324](https://github.com/serverless/serverless/pull/10324)) ([2485c7e](https://github.com/serverless/serverless/commit/2485c7efcc4f6f5b1d65b56d4d0d71297d113fa5)) ([François Farge](https://github.com/fargito))
- **Variables:** Provide opt-out from forced decryption at`ssm` source ([#10315](https://github.com/serverless/serverless/issues/10315)) ([503c031](https://github.com/serverless/serverless/commit/503c0319b7e9acc2b674d5d61874dfa3fcfc857e)) ([Omer Shacham](https://github.com/omerinvia))

### Maintenance Improvements

- Configure promise returning functions as async ([#10309](https://github.com/serverless/serverless/issues/10309)) ([4d4f863](https://github.com/serverless/serverless/commit/4d4f8637d830ba9a72806fc127fe3497f7c0f23c)) ([mdanyalkhan](https://github.com/mdanyalkhan))
- Use `async/await` syntax in `bucket.js` ([#10306](https://github.com/serverless/serverless/pull/10306)) ([39e43b5](https://github.com/serverless/serverless/commit/39e43b51e5e13c708900e0ccc4d4f25ccf0df61c)) ([Piotr Grzesik](https://github.com/pgrzesik))

## [2.68.0](https://github.com/serverless/serverless/compare/v2.67.0...v2.68.0) (2021-12-02)

### Features

- **AWS Deploy:**
  - Ensure consistent function state in `deploy function` ([#10288](https://github.com/serverless/serverless/pull/10288)) ([d52526b](https://github.com/serverless/serverless/commit/d52526bb6059ce20eba341c29ad5a2373c238624)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Support all regions from `iso` and `isob` partition ([25eb571](https://github.com/serverless/serverless/commit/25eb571dd3299ac0f61dd1ea40b6b44b355f6898)) ([#10299](https://github.com/serverless/serverless/issues/10299)) ([maafk](https://github.com/maafk))
- **AWS SQS:** Support `filterPatterns` ([#10297](https://github.com/serverless/serverless/pull/10297)) ([3f0a80a](https://github.com/serverless/serverless/commit/3f0a80acd3fcf9eb7768625eb6cfe06cf572afa0)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **AWS Stream:** Support `filterPatterns` ([#10285](https://github.com/serverless/serverless/issues/10285)) ([fc00505](https://github.com/serverless/serverless/commit/fc0050559cd1ee7b8a53a08fae73940177da93cb)) ([Frédéric Barthelet](https://github.com/fredericbarthelet))

### Bug Fixes

- **AWS SQS:** Accept only plain string form in direct ARN assignement ([#10263](https://github.com/serverless/serverless/issues/10263)) ([f7bbd17](https://github.com/serverless/serverless/commit/f7bbd176866b99725dcf1fef1128b0d2194217e0)) ([Sudipto Das](https://github.com/sdas13))
- **Variables:** Resolve variables in resolved address & params values ([#10296](https://github.com/serverless/serverless/pull/10296)) ([63d54e1](https://github.com/serverless/serverless/commit/63d54e1537e10ae63c171892edd886f6b81e83f6)) ([Mariusz Nowak](https://github.com/medikoo))

### Maintenance Improvements

- **Variables:** Seclude internal logic for reuse ([#10296](https://github.com/serverless/serverless/pull/10296)) ([9c75044](https://github.com/serverless/serverless/commit/9c75044fd59d8f181c7daee22d53a7bac3786e09)) ([Mariusz Nowak](https://github.com/medikoo))

### Templates

- Update dependencies in `aws-java-maven` ([#10289](https://github.com/serverless/serverless/issues/10289)) ([0714f7d](https://github.com/serverless/serverless/commit/0714f7df0642d7a900c9d72eb26ae8c5ae1eddd7)) ([burakaktasfe](https://github.com/burakaktasfe))

## [2.67.0](https://github.com/serverless/serverless/compare/v2.66.2...v2.67.0) (2021-11-26)

### Features

- **AWS Deploy:** Support `disableRollback` parameter ([#10236](https://github.com/serverless/serverless/issues/10236)) ([c9fefce](https://github.com/serverless/serverless/commit/c9fefced103e47d5d793d979cbb10072daeabf01)) ([Frédéric Barthelet](https://github.com/fredericbarthelet))
- **AWS Lambda:** Add `platform` option for container images ([#10237](https://github.com/serverless/serverless/issues/10237)) ([5b61b41](https://github.com/serverless/serverless/commit/5b61b415a0f19ce0755924eae969caf02185d8af)) ([Zane Mountcastle](https://github.com/zanemountcastle))
- **AWS S3:** Support `Fn::If` CF function for s3 event ([#10272](https://github.com/serverless/serverless/pull/10272)) ([a4fa498](https://github.com/serverless/serverless/commit/a4fa49844d23afea90f7c9aa4616beedd2a80db8)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **AWS SQS:** Support `functionResponseType` ([#10265](https://github.com/serverless/serverless/issues/10265)) ([44511f3](https://github.com/serverless/serverless/commit/44511f343b1a68ca147e8ba9e8b493143b89c324)) ([nicoeft](https://github.com/nicoeft))

## [2.66.2](https://github.com/serverless/serverless/compare/v2.66.1...v2.67.0) (2021-11-17)

### Bug Fixes

- **CLI:** Fix component template recognition in triage ([#10252](https://github.com/serverless/serverless/issues/10252)) ([4494f77](https://github.com/serverless/serverless/commit/4494f77f6111249d97295923a706883a8910840d)) ([Mariusz Nowak](https://github.com/medikoo))

### Maintenance Improvements

- **CLI:** Expose dashboard provider name when starting deployment ([#10194](https://github.com/serverless/serverless/issues/10194)) ([6698fa6](https://github.com/serverless/serverless/commit/6698fa657e5a5b35908c2b2de0815525f948064f)) ([Mariusz Nowak](https://github.com/medikoo))

### Templates

- Use `iam.role` syntax ([#10227](https://github.com/serverless/serverless/issues/10227)) ([a55d51c](https://github.com/serverless/serverless/commit/a55d51c6a4aa38153f61192d374cb23bf09ff66c)) ([Piotr Grzesik](https://github.com/pgrzesik))
- Update `ts-node` for es2020 and es2021 support in `aws-nodes-typescript` ([#10234](https://github.com/serverless/serverless/issues/10234)) ([e131609](https://github.com/serverless/serverless/commit/e13160902848912a6bb652299d1bc6107cf09eb1)) ([Frédéric Barthelet](https://github.com/fredericbarthelet))

### [2.66.1](https://github.com/serverless/serverless/compare/v2.66.0...v2.66.1) (2021-11-10)

### Bug Fixes

- **AWS API Gateway:** Ensure proper `apiId` resolution ([#10221](https://github.com/serverless/serverless/pull/10221)) ([95f3a56](https://github.com/serverless/serverless/commit/95f3a5603897ad43ba6e008a7ea2a35d21a4eacf)) ([Piotr Grzesik](https://github.com/pgrzesik))

### Maintenance Improvements

- **CLI:** Improve timestamp visiblity in `deploy list` output ([#10211](https://github.com/serverless/serverless/pull/10211)) ([55146c4](https://github.com/serverless/serverless/commit/55146c4595024b0e3702dc2023264af784b906e9)) ([Mariusz Nowak](https://github.com/medikoo))

### Templates

- Upgrade `middy` in `aws-nodejs-typescript` ([#10215](https://github.com/serverless/serverless/issues/10215)) ([ad95e03](https://github.com/serverless/serverless/commit/ad95e030b3581a65babc8dd175b8bb69f1215534)) ([Frédéric Barthelet](https://github.com/fredericbarthelet))
- Use non deprecated API in `aws-nodejs-typescript` ([#10214](https://github.com/serverless/serverless/issues/10214)) ([6671d98](https://github.com/serverless/serverless/commit/6671d98615ab7d003c3c7413c9334b63b2d735e8)) ([Frédéric Barthelet](https://github.com/fredericbarthelet))

## [2.66.0](https://github.com/serverless/serverless/compare/v2.65.0...v2.66.0) (2021-11-09)

### Features

- Introduce `enforce-hash-update` flag to help Lambda hashing version migration ([#10209](https://github.com/serverless/serverless/pull/10209)) ([afd0a5b](https://github.com/serverless/serverless/commit/afd0a5bd6f131c9b12148199d4995e055e5963f0)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **Variables:** Recognize `:` in variable address to support `output` source ([#10208](https://github.com/serverless/serverless/pull/10208)) ([723927f](https://github.com/serverless/serverless/commit/723927f2dcdcc425025da03ac0be5edd3c203dc7)) ([Piotr Grzesik](https://github.com/pgrzesik))

### Bug Fixes

- **AWS API Gateway:** Ensure `shouldStartNameWithService` support ([#10177](https://github.com/serverless/serverless/pull/10177)) ([e8c8d25](https://github.com/serverless/serverless/commit/e8c8d259fb79ae04e33e01af162c6666f0060189)) ([Vicary A.](https://github.com/vicary))
- **CLI:** Do not recommend `frameworkVersion` when running pre release ([#10204](https://github.com/serverless/serverless/pull/10204)) ([53490a5](https://github.com/serverless/serverless/commit/53490a55183db5f304d0e3ef69feadd9a20fa815)) ([Mariusz Nowak](https://github.com/medikoo))

### Maintenance Improvements

- Ensure to use `legacy.log` instead of `cli.log` ([#10206](https://github.com/serverless/serverless/pull/10206)) ([ea05d7c](https://github.com/serverless/serverless/commit/ea05d7c41e84b0f68017804b06d6435062673d26)) ([Mariusz Nowak](https://github.com/medikoo))

## [2.65.0](https://github.com/serverless/serverless/compare/v2.64.1...v2.65.0) (2021-11-03)

### Features

- **AWS Lambda:**
  - Support CF intrinsic functions at `functions[].reservedConcurrency` ([#10129](https://github.com/serverless/serverless/issues/10129)) ([7cfddff](https://github.com/serverless/serverless/commit/7cfddff31433582ac031be0a168eba2d356d7ee9)) ([ROSeaboyer](https://github.com/ROSeaboyer))
  - Allow to stick to current default Lambda hashing version mode with `lambdaHashingVersion: 20200924` setting ([#10173](https://github.com/serverless/serverless/pull/10173)) ([50a8457](https://github.com/serverless/serverless/commit/50a845709eb846ce5ca3b60116c4ec278896a8b3)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **AWS EventBridge:** Adjust deprecation of deployment method and allow to keep using old approach ([#10133](https://github.com/serverless/serverless/pull/10133)) ([bf62b7c](https://github.com/serverless/serverless/commit/bf62b7c4dabbecc892fde4d0d988dc2dd2cb7461)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **AWS Local Invocation:** Support decimal serialization for Python ([#10178](https://github.com/serverless/serverless/pull/10178)) ([9ef46ba](https://github.com/serverless/serverless/commit/9ef46ba05ff033dbf04c451a214bf4ced23c90e8)) ([Shane R. Spencer](https://github.com/whardier))

### Bug Fixes

- **AWS Deploy:** Fix handling of deployment bucket extensions ([#10137](https://github.com/serverless/serverless/issues/10137)) ([39bdea0](https://github.com/serverless/serverless/commit/39bdea07500b8fb814a5cce83ec6f78a0c75006c)) ([Mars Lan](https://github.com/mars-lan))
- **AWS HTTP API:** Recognize max timeout as 30s instead of 29s ([#10119](https://github.com/serverless/serverless/issues/10119)) ([e3e02fe](https://github.com/serverless/serverless/commit/e3e02fe8e2f1bbd236cfa49f80a360fd828c1ead)) ([Caio Fauza](https://github.com/CaioFauza))
- **CLI:**
  - Fix `help` command usage information ([#10175](https://github.com/serverless/serverless/issues/10175)) ([254e70c](https://github.com/serverless/serverless/commit/254e70cd0ad9bb1803d3a5741b966f5807e9d869)) ([Sebastian Bille](https://github.com/TastefulElk))
  - Fix resolution of help for not integrated commands ([#10128](https://github.com/serverless/serverless/pull/10128)) ([204f205](https://github.com/serverless/serverless/commit/204f2051f6a5ca5f046eb905292dfae0c597e33f)) ([Mariusz Nowak](https://github.com/medikoo))
- Recognize accessible configuration parts on validation errors ([#10134](https://github.com/serverless/serverless/pull/10134)) ([b7a6349](https://github.com/serverless/serverless/commit/b7a634974dc2ee138d85ec58609bf2559c5de9f6)) ([Mariusz Nowak](https://github.com/medikoo))

### Performance Improvements

- **CLI:** Integrate CLI triage into this package (no `@serverless/components` and `@serverless/cli` modules are loaded unless their CLI is used)([#10131](https://github.com/serverless/serverless/pull/10131)) ([415bdef](https://github.com/serverless/serverless/commit/415bdefca092e60cacd867006bacddfda231ed94)) ([Mariusz Nowak](https://github.com/medikoo))

### Maintenance Improvements

- **CLI:**
  - Improve file size output in logs ([#10169](https://github.com/serverless/serverless/pull/10169)) ([4448490](https://github.com/serverless/serverless/commit/44484903b38eaa18c3e3838b8a3f217922a233e5)) ([Mariusz Nowak](https://github.com/medikoo))
  - Improve main progress message ([#10183](https://github.com/serverless/serverless/pull/10183)) ([533f709](https://github.com/serverless/serverless/commit/533f709c5833619d5ce86ec987133ff0f148c8e0)) ([Mariusz Nowak](https://github.com/medikoo))
- **Telemetry:** Add `projectId` to payload ([#10180](https://github.com/serverless/serverless/pull/10180)) ([cc7d7e4](https://github.com/serverless/serverless/commit/cc7d7e4d531090e81bf08842433397588d00afce)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **AWS EventBridge:** Address typos in error messages ([#10165](https://github.com/serverless/serverless/issues/10165)) ([ee38f6a](https://github.com/serverless/serverless/commit/ee38f6a3081a3a0f22ee9fea8975f13520ac18ec)) ([Andreas Kohn](https://github.com/ankon))
- Seprate internal and plugin output sections ([#10184](https://github.com/serverless/serverless/pull/10184)) ([7bb2520](https://github.com/serverless/serverless/commit/7bb2520f491d008075eb08be64bdb2e0b60ec5c6)) ([Mariusz Nowak](https://github.com/medikoo))

### Templates

- Package lambdas individually in `aws-nodejs-typescript` ([#10106](https://github.com/serverless/serverless/pull/10106)) ([3aab5f8](https://github.com/serverless/serverless/commit/3aab5f86985598d6bb3135f4ab934092ad467df5)) ([Adrien Cacciaguerra](https://github.com/adriencaccia))
- Upgrade `azure-nodejs-typescript` ([#10163](https://github.com/serverless/serverless/issues/10163)) ([26846d5](https://github.com/serverless/serverless/commit/26846d5879d655ffe299db694a33f1f6d187a941)) ([Giang Nguyen](https://github.com/giangnm))

### [2.64.1](https://github.com/serverless/serverless/compare/v2.64.0...v2.64.1) (2021-10-20)

### Bug Fixes

- **CLI:** Handle gently case where temp folder is on other device ([#10124](https://github.com/serverless/serverless/issues/10124)) ([a030636](https://github.com/serverless/serverless/commit/a0306365fc2c18c04698640723db2f4efeb34e2f)) ([Mariusz Nowak](https://github.com/medikoo))

## [2.64.0](https://github.com/serverless/serverless/compare/v2.63.0...v2.64.0) (2021-10-20)

### Features

- **AWS RabbitMQ:** Support for Amazon MQ RabbitMQ events ([#9919](https://github.com/serverless/serverless/issues/9919)) ([a3edecf](https://github.com/serverless/serverless/commit/a3edecf0c6b4e066bde2de8095582432d9fdd635)) ([Michael](https://github.com/liegeandlief))

### Bug Fixes

- **AWS Deploy:** Recognize `LogicalResourceId` in `stackPolicy` ([#10097](https://github.com/serverless/serverless/pull/10097)) ([1a528c2](https://github.com/serverless/serverless/commit/1a528c2cc0746bfe6a692183f96b0831e3dd92f4)) ([Monsma](https://github.com/jmonsma))
- **AWS EventBridge:** Allow intrinsic functions in `pattern` ([#10120](https://github.com/serverless/serverless/issues/10120)) ([1c105a4](https://github.com/serverless/serverless/commit/1c105a4c16e8bdca9fc66c5eddf12153ebc9a1fb)) ([Benoît Bouré](https://github.com/bboure))
- **CLI:** Ensure command validation for service independent commands ([#10115](https://github.com/serverless/serverless/pull/10115)) ([6022fb9](https://github.com/serverless/serverless/commit/6022fb98331e8f7d8893a28d3dcb20d91d0a1e20)) ([Mariusz Nowak](https://github.com/medikoo))
- **Packaging:** Ensure to show deprecation in all cases ([#10111](https://github.com/serverless/serverless/pull/10111)) ([cc71fc9](https://github.com/serverless/serverless/commit/cc71fc99ffe2e1f2fcc764b29dafa197c665cef1)) ([Mariusz Nowak](https://github.com/medikoo))

### Maintenance Improvements

- **CLI:**
  - Support `decoratedMessage` on `ServerlessError` ([#10112](https://github.com/serverless/serverless/pull/10112)) ([2217158](https://github.com/serverless/serverless/commit/2217158764dde8ceee472292b531836ada20d79a)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Enhanced modern error reporting for CloudFormation ([#10112](https://github.com/serverless/serverless/pull/10112)) ([cfd828e](https://github.com/serverless/serverless/commit/cfd828ece872b572cbb46670437e8196f2200903)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Report `credentials` source in modern error output ([#10114](https://github.com/serverless/serverless/pull/10114)) ([b4ff87d](https://github.com/serverless/serverless/commit/b4ff87dc81286b8123830f20bccfb3aa320e4ccd)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Improve style for local fallback modern notice ([#10111](https://github.com/serverless/serverless/pull/10111)) ([73c071b](https://github.com/serverless/serverless/commit/73c071b060216d330974a2f98917eba315eb634b)) ([Mariusz Nowak](https://github.com/medikoo))
  - Introduce `doctor` command for modern handling of deprecations ([#10115](https://github.com/serverless/serverless/pull/10115)) ([452e234](https://github.com/serverless/serverless/commit/452e234306a3703e95ad349305e1e211c165bf22)) ([Mariusz Nowak](https://github.com/medikoo))
  - Do not filter commands by `lifecycleEvents` for help ([#10115](https://github.com/serverless/serverless/pull/10115)) ([6991d66](https://github.com/serverless/serverless/commit/6991d66987d6276665bff07259bf1ca464ffeab7)) ([Mariusz Nowak](https://github.com/medikoo))

## [2.63.0](https://github.com/serverless/serverless/compare/v2.62.0...v2.63.0) (2021-10-15)

### Features

- **AWS Deploy:** Introduce warning about `deploy -f` alias ([#10078](https://github.com/serverless/serverless/pull/10078)) ([40f574f](https://github.com/serverless/serverless/commit/40f574f946e2f40cba13e18b22ee82c7aaa31d3f)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **AWS Lambda:** Allow overriding provider VPC with no VPC on function level ([#10060](https://github.com/serverless/serverless/pull/10060)) ([44a81fc](https://github.com/serverless/serverless/commit/44a81fcc6a229ac6ff59b8c8e51742a9470eef15)) ([Oliver](https://github.com/HowManyOliversAreThere))
- **AWS S3:** Recognize `ExpirationInDays` property for `s3` events ([#10083](https://github.com/serverless/serverless/pull/10083)) ([8e6dcd1](https://github.com/serverless/serverless/commit/8e6dcd1aaed50007b5b99e18f61dfa849b898cd9)) ([ROSeaboyer](https://github.com/ROSeaboyer))
- **CLI:**
  - Introduce deprecation for duplicate plugin definition ([#10080](https://github.com/serverless/serverless/pull/10080)) ([d2a75ea](https://github.com/serverless/serverless/commit/d2a75ea95e814cd5aaba5eca4c5acebd2aad0bb8)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Introduce deprecation instead of warning on S3 Accelerate for user provided bucket ([#10080](https://github.com/serverless/serverless/pull/10080)) ([04b921a](https://github.com/serverless/serverless/commit/04b921acdc5fd486ffd10fe81fcb2243f37329db)) ([Piotr Grzesik](https://github.com/pgrzesik))
- Opt-in support for deployment bucket versioning ([#9912](https://github.com/serverless/serverless/issues/9912)) ([c4cb0f3](https://github.com/serverless/serverless/commit/c4cb0f30f5f565e2fd34877dfc383f6b81d135fd)) ([Mars Lan](https://github.com/mars-lan))

### Maintenance Improvements

- **CLI: New logs (experimental):**
  - Adapt `logInfo` to modern logs ([#10078](https://github.com/serverless/serverless/pull/10078)) ([771f99b](https://github.com/serverless/serverless/commit/771f99b18d76060f030d36b5fa619dd41a7000c8)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Adapt `logWarning` to modern logs ([#10078](https://github.com/serverless/serverless/pull/10078)) ([d43298d](https://github.com/serverless/serverless/commit/d43298d25bc9fcf5f5724a800b2693321e88e838)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Cover image building with modern logs ([#10070](https://github.com/serverless/serverless/pull/10070)) ([a2be338](https://github.com/serverless/serverless/commit/a2be3387b16fdb7324e1342a5f6ee3974e4e34f5)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Improve handling of service outputs in modern logs ([#10100](https://github.com/serverless/serverless/pull/10100)) ([7d19ca8](https://github.com/serverless/serverless/commit/7d19ca857230a56bbe40bda4d6704edd34019e4e)) ([Mariusz Nowak](https://github.com/medikoo))
  - Introduce modern warning about resource limit ([#10086](https://github.com/serverless/serverless/pull/10086)) ([ca705b8](https://github.com/serverless/serverless/commit/ca705b8cc2854c302158a56294c2507ba5f2038f)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Minor modern logs updates ([#10071](https://github.com/serverless/serverless/pull/10071)) ([39c09e4](https://github.com/serverless/serverless/commit/39c09e44b6380ec1a13aa50aca9082cffb0aeca1)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Remove empty line in `info` command ([#10086](https://github.com/serverless/serverless/pull/10086)) ([03b4b3d](https://github.com/serverless/serverless/commit/03b4b3d47c25b6f98a46699463288c94b051f42c)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Replace `process.stdout` use with modern logs ([#10087](https://github.com/serverless/serverless/pull/10087)) ([be00a26](https://github.com/serverless/serverless/commit/be00a2672cbc90fb33dee5e4bd44a1f6a127eb7c)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Replace warnings with modern counterparts ([#10080](https://github.com/serverless/serverless/pull/10080)) ([4da0899](https://github.com/serverless/serverless/commit/4da08996736c9a8f2b0a0193f7cca4b24f3fc6f1)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Update link style for modern logs ([#10096](https://github.com/serverless/serverless/pull/10096)) ([6264296](https://github.com/serverless/serverless/commit/62642964bc38eae77b009ea84d05ba741383570f)) ([Mariusz Nowak](https://github.com/medikoo))
- Fix typo in `lib/classes/Variables.js` ([#10093](https://github.com/serverless/serverless/issues/10093)) ([49f0913](https://github.com/serverless/serverless/commit/49f0913466110ac32d89c7c044fc781e524b9ed9)) ([Chris Poli](https://github.com/chris-poli))

### Templates

- Add `esbuild` to `gitignore` in `aws-nodejs-typescript` ([#10076](https://github.com/serverless/serverless/pull/10076)) ([865f21f](https://github.com/serverless/serverless/commit/865f21f970340b45c6fb341d01647721f0fa5682)) ([ssshun](https://github.com/ssshun))

## [2.62.0](https://github.com/serverless/serverless/compare/v2.61.0...v2.62.0) (2021-10-08)

### Features

- **AWS Deploy:** Remove `deploy -f` deprecation ([#10063](https://github.com/serverless/serverless/pull/10063)) ([1084251](https://github.com/serverless/serverless/commit/10842513f0c5422f8627b652b6483523e0351a3c)) ([Mariusz Nowak](https://github.com/medikoo))
- **Config Schema:** Remove validation mode related deprecation ([#10063](https://github.com/serverless/serverless/pull/10063)) ([a9bf916](https://github.com/serverless/serverless/commit/a9bf916fbb15140373a54d22c624296b8a1dbe03)) ([Mariusz Nowak](https://github.com/medikoo))
- **Packaging:** Remove `package[include|exclude]` deprecation ([#10063](https://github.com/serverless/serverless/pull/10063)) ([70e2736](https://github.com/serverless/serverless/commit/70e27362260f97b68bb1dfaf52fa3fe7877a2adc)) ([Mariusz Nowak](https://github.com/medikoo))

### Bug Fixes

- **AWS Deploy:** Throw on attempt of extending not existing resource ([#10063](https://github.com/serverless/serverless/pull/10063)) ([02be86c](https://github.com/serverless/serverless/commit/02be86ca4954553388ac70845d8ff3aca205abcd)) ([Mariusz Nowak](https://github.com/medikoo))

### Maintenance Improvements

- **CLI: New logs (experimental):**
  - Simplify CF deploy progress ([#10068](https://github.com/serverless/serverless/pull/10068)) ([be60ed4](https://github.com/serverless/serverless/commit/be60ed4cee15ec0a47be5c08da9e0ce4a3f54136)) ([Mariusz Nowak](https://github.com/medikoo))
  - Expose function artifact size in deploy summary ([#10062](https://github.com/serverless/serverless/pull/10062)) ([8746100](https://github.com/serverless/serverless/commit/87461007f809c67a78b7dd722847efef2e4f72b3)) ([Mariusz Nowak](https://github.com/medikoo))
  - `create` command ([#10066](https://github.com/serverless/serverless/pull/10066)) ([05f937f](https://github.com/serverless/serverless/commit/05f937f2e731e641e93e9db4af4acd58dc117422)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - `invoke local` command ([#10065](https://github.com/serverless/serverless/pull/10065)) ([82dd1e4](https://github.com/serverless/serverless/commit/82dd1e4c70d335cc10485b5ac20467447809941b)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - `invoke` command ([#10052](https://github.com/serverless/serverless/pull/10052)) ([2af95c0](https://github.com/serverless/serverless/commit/2af95c03865b5b59bacba9e080348dddf11d0bb5)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - `metrics` command ([#10051](https://github.com/serverless/serverless/pull/10051)) ([592596c](https://github.com/serverless/serverless/commit/592596c73bfe0a9b6ef6bdff5d898ae9ef5e2788)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - `remove` command ([#10050](https://github.com/serverless/serverless/pull/10050)) ([3934cad](https://github.com/serverless/serverless/commit/3934cadce052b50d76c1dcd49da588cd9f079175)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - `rollback function` command ([#10064](https://github.com/serverless/serverless/pull/10064)) ([4cbc342](https://github.com/serverless/serverless/commit/4cbc3424dabebb3b533d463b3ead523f2daf4a77)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - `rollback` command ([#10064](https://github.com/serverless/serverless/pull/10064)) ([f0970e0](https://github.com/serverless/serverless/commit/f0970e04fa31774aa7400b4c620920dadcb3cfa2)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - `uninstall` command ([#10034](https://github.com/serverless/serverless/pull/10034)) ([2787ea0](https://github.com/serverless/serverless/commit/2787ea07a9a183695e6f7a58bcc0171e086d456b)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - `upgrade` command ([#10034](https://github.com/serverless/serverless/pull/10034)) ([9b5e6b1](https://github.com/serverless/serverless/commit/9b5e6b12371317356d9cb4600a4a574df305f63f)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Ensure empty line prior final status with progress ([#10063](https://github.com/serverless/serverless/pull/10062)) ([#10062](https://github.com/serverless/serverless/pull/10062)) ([c9f2227](https://github.com/serverless/serverless/commit/c9f22278b3a8c5fd4d1400ef948ae6b72f333223)) ([Mariusz Nowak](https://github.com/medikoo))
  - Reconfigure dashboard related warning ([#10053](https://github.com/serverless/serverless/pull/10053)) ([7c91cde](https://github.com/serverless/serverless/commit/7c91cde7ac5c8bbe983b213de090bde4326af85a)) ([Mariusz Nowak](https://github.com/medikoo))
- **AWS Deploy:** Improve error message ([#10063](https://github.com/serverless/serverless/pull/10063)) ([d071c5f](https://github.com/serverless/serverless/commit/d071c5f74d2d1deca71edebc53d072a1c90d8bad)) ([Mariusz Nowak](https://github.com/medikoo))
- Remove _async_ handling from _sync_ function ([#10053](https://github.com/serverless/serverless/pull/10053)) ([5f1a916](https://github.com/serverless/serverless/commit/5f1a916d4d9c8833755833bc064f51e4f89e50e0)) ([Mariusz Nowak](https://github.com/medikoo))

## [2.61.0](https://github.com/serverless/serverless/compare/v2.60.3...v2.61.0) (2021-10-04)

### Features

- **AWS Lambda:** Support 64-bit ARM architecture ([#10049](https://github.com/serverless/serverless/pull/10049)) ([fe655d4](https://github.com/serverless/serverless/commit/fe655d4f15ca789a1e3a46ce49dc7d23ca806c00)) ([Mariusz Nowak](https://github.com/medikoo))

### Bug Fixes

- **AWS Credentials:** Fail when profile is already configured ([#10038](https://github.com/serverless/serverless/pull/10038)) ([f8ad7bc](https://github.com/serverless/serverless/commit/f8ad7bca6a26e39864d139fec4aadddd24b34a5b)) ([Piotr Grzesik](https://github.com/pgrzesik))

### Maintenance Improvements

- **CLI: New logs (experimental):**
  - `config credentials` command ([#10038](https://github.com/serverless/serverless/pull/10038)) ([bcb2408](https://github.com/serverless/serverless/commit/bcb240893d89127cc1eada7255864b7bfeb88a61)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - `config tabcompletion install` command ([#10038](https://github.com/serverless/serverless/pull/10038)) ([16a7739](https://github.com/serverless/serverless/commit/16a7739411141487fa33f8a72f88d82db712bfc9)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - `config tabcompletion uninstall` command ([#10038](https://github.com/serverless/serverless/pull/10038)) ([02eebb4](https://github.com/serverless/serverless/commit/02eebb4643435341235340f5da8c7db903cb12e6)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - `config` command ([#10038](https://github.com/serverless/serverless/pull/10038)) ([7926570](https://github.com/serverless/serverless/commit/7926570557e5c0a4dd661c069eecc1d4a0cf9b5d)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - `slstats` command ([#10036](https://github.com/serverless/serverless/pull/10036)) ([0c9dae1](https://github.com/serverless/serverless/commit/0c9dae1210b9456ec96bc38a717a901beaa45a7b)) ([Piotr Grzesik](https://github.com/pgrzesik))

### [2.60.3](https://github.com/serverless/serverless/compare/v2.60.2...v2.60.3) (2021-10-01)

### Bug Fixes

- **CLI:** Fix resolution of handler in case of local fallback ([#10042](https://github.com/serverless/serverless/pull/10042)) ([7d31410](https://github.com/serverless/serverless/commit/7d31410b74efb4c48c1c1b18ca33733a564268f2)) ([Mariusz Nowak](https://github.com/medikoo))

### Maintenance Improvements

- **CLI:**
  - Improve modern `info` output ([#10037](https://github.com/serverless/serverless/pull/10037)) ([2828a2c](https://github.com/serverless/serverless/commit/2828a2c44388d731d4396e0ea11ae48953f20b0a)) ([Mariusz Nowak](https://github.com/medikoo))
  - Improve modern error reporting ([#10037](https://github.com/serverless/serverless/pull/10037)) ([a205f88](https://github.com/serverless/serverless/commit/a205f88310653331c96f51402d148c576dd79db8)) ([Mariusz Nowak](https://github.com/medikoo))
  - Improve modern logs for `logs` command ([#10037](https://github.com/serverless/serverless/pull/10037)) ([d1701bf](https://github.com/serverless/serverless/commit/d1701bf13a7155cce388424964e35ca536b2ce8a)) ([Mariusz Nowak](https://github.com/medikoo))
  - Modern logs for `install` command ([#10040](https://github.com/serverless/serverless/pull/10040)) ([bd4d215](https://github.com/serverless/serverless/commit/bd4d215266b16793c26d06a34af8482f00e47844)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Modern logs for `print` command ([#10035](https://github.com/serverless/serverless/pull/10035)) ([4ed34c3](https://github.com/serverless/serverless/commit/4ed34c3e5e21903a3fe9e512621739ef5bf0bd84)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Generalize `writeServiceOutputs` ([#10037](https://github.com/serverless/serverless/pull/10037)) ([8aa700d](https://github.com/serverless/serverless/commit/8aa700dc7947d36aa46bba4b0e475f21fd19ac89)) ([Mariusz Nowak](https://github.com/medikoo))

### [2.60.2](https://github.com/serverless/serverless/compare/v2.60.1...v2.60.2) (2021-09-30)

### Bug Fixes

- **AWS EventBridge:** Ensure proper support for `deadLetterQueueArn` (instead of `deadLetterConfig`) ([#10030](https://github.com/serverless/serverless/pull/10030)) ([846cfa1](https://github.com/serverless/serverless/commit/846cfa1bcf678a748678014c6359e5f0907d35ff)) ([Piotr Grzesik](https://github.com/pgrzesik))

### [2.60.1](https://github.com/serverless/serverless/compare/v2.60.0...v2.60.1) (2021-09-29)

### Bug Fixes

- **AWS EventBridge:** Fix `MaximumEventAgeInSecond` template reference ([#10023](https://github.com/serverless/serverless/issues/10023)) ([cd03f55](https://github.com/serverless/serverless/commit/cd03f550ae5307ca44e1e27d4d0822bef6cc9dcf)) ([Mariusz Nowak](https://github.com/medikoo))
- **Standalone:**
  - Fix internal npm installation handling ([#10014](https://github.com/serverless/serverless/issues/10014)) ([5a583a9](https://github.com/serverless/serverless/commit/5a583a97980117209a614bfd40630b1bb714b744)) ([Mariusz Nowak](https://github.com/medikoo))
  - Upgrade `npm` version to one that supports Node.js v14 ([#10014](https://github.com/serverless/serverless/issues/10014)) ([62d697c](https://github.com/serverless/serverless/commit/62d697c8615e8103aa07401eef2ebae559cc4a17)) ([Mariusz Nowak](https://github.com/medikoo))
- **CLI:** Fix handling when local `serverless` is removed in command run ([#10016](https://github.com/serverless/serverless/issues/10016)) ([1a3ccdb](https://github.com/serverless/serverless/commit/1a3ccdbef8cd9c41b87f7fe440ca300970f3e138)) ([Mariusz Nowak](https://github.com/medikoo))

### Maintenance Improvements

- **Plugins:**
  - Seclude `plugin install` standalone command ([#9942](https://github.com/serverless/serverless/issues/9942)) ([713ac1e](https://github.com/serverless/serverless/commit/713ac1e2a111426fb501b5fa29588a53efcba9bc)) ([Seungchan Ahn](https://github.com/issea1015))
  - Seclude `plugin uninstall` standalone command ([#10015](https://github.com/serverless/serverless/issues/10015)) ([26ce1c6](https://github.com/serverless/serverless/commit/26ce1c636be7754584cf47a87f1b92d3b7d98122)) ([Seungchan Ahn](https://github.com/issea1015))
  - Fix manual update notice ([#10016](https://github.com/serverless/serverless/issues/10016)) ([0d5884e](https://github.com/serverless/serverless/commit/0d5884ebbf015332c08cedea7a4359d66c3a2761)) ([Mariusz Nowak](https://github.com/medikoo))
- **CLI: New logs (experimental):**
  - `plugin install` command ([#10016](https://github.com/serverless/serverless/issues/10016)) ([8c5f22c](https://github.com/serverless/serverless/commit/8c5f22ceb67c3a2f4ace3adf8e19cf5e69d4c7b3)) ([Mariusz Nowak](https://github.com/medikoo))
  - `plugin list` command ([#10016](https://github.com/serverless/serverless/issues/10016)) ([00e016c](https://github.com/serverless/serverless/commit/00e016c4bba86095744129d24683343f0cc5129f)) ([Mariusz Nowak](https://github.com/medikoo))
  - `plugin search` command ([#10016](https://github.com/serverless/serverless/issues/10016)) ([1463171](https://github.com/serverless/serverless/commit/1463171cae93e9e050350f6eb272e35cfade0204)) ([Mariusz Nowak](https://github.com/medikoo))
  - `plugin uninstall` command ([#10016](https://github.com/serverless/serverless/issues/10016)) ([3094be0](https://github.com/serverless/serverless/commit/3094be0cf06f916d8cf180036433677ecd73e013)) ([Mariusz Nowak](https://github.com/medikoo))
  - interactive setup ([#10024](https://github.com/serverless/serverless/issues/10024)) ([07aed34](https://github.com/serverless/serverless/commit/07aed3429c63ed13ad9ca6262c641a907170f4f9)) ([Mariusz Nowak](https://github.com/medikoo))
  - Local version fallback ([#10024](https://github.com/serverless/serverless/issues/10024)) ([231095d](https://github.com/serverless/serverless/commit/231095d28d4e3f137ef0a456692dd5d6a770a5db)) ([Mariusz Nowak](https://github.com/medikoo))
  - Rely on newly introduced log style functions ([#10024](https://github.com/serverless/serverless/issues/10024)) ([e070110](https://github.com/serverless/serverless/commit/e070110eee0e679694aefd4e6b5f25ecc90793d4)) ([Mariusz Nowak](https://github.com/medikoo))
  - Move variables resolution log to debug level ([#10016](https://github.com/serverless/serverless/issues/10016)) ([b0d854a](https://github.com/serverless/serverless/commit/b0d854af20d46ef9e07e5d4bce26b88e84f4c4f1)) ([Mariusz Nowak](https://github.com/medikoo))

## [2.60.0](https://github.com/serverless/serverless/compare/v2.59.0...v2.60.0) (2021-09-24)

### Features

- **CLI:**
  - Remove missing CLI options schema deprecation ([#10001](https://github.com/serverless/serverless/issues/10001)) ([5b38232](https://github.com/serverless/serverless/commit/5b38232e631e1fb6d944d5f323f533d7dd7b701f)) ([Mariusz Nowak](https://github.com/medikoo))
  - Revert from unconditional `.env` support announcement ([#10003](https://github.com/serverless/serverless/issues/10003)) ([40cdb4f](https://github.com/serverless/serverless/commit/40cdb4f1a191d330e31ddadc4caaa4b314229e3d)) ([Mariusz Nowak](https://github.com/medikoo))
- **AWS Stream:** Support `tumblingWindowInSeconds` ([#9979](https://github.com/serverless/serverless/issues/9979)) ([af39fc0](https://github.com/serverless/serverless/commit/af39fc016bd6386ea7d5d1ff71a26553a25b7ec5)) ([Guilherme Martins Crocetti](https://github.com/gmcrocetti))
- Support `finalize` hook, triggered on command finalization ([#9956](https://github.com/serverless/serverless/issues/9956)) ([cb4f08a](https://github.com/serverless/serverless/commit/cb4f08ad7dd8eed3da69d61d51c6d5379a486bd0)) ([Mariusz Nowak](https://github.com/medikoo))

### Bug Fixes

- **AWS S3:** Recognize `BucketKeyEnabled` setting ([#9985](https://github.com/serverless/serverless/issues/9985)) ([54bb13b](https://github.com/serverless/serverless/commit/54bb13b6a6d3fd41548615fc23f4ae4d6d663dcc)) ([John Armstrong](https://github.com/jlarmstrongiv))
- **CLI:** Fix general help output when in context of AWS service ([#9994](https://github.com/serverless/serverless/issues/9994)) ([0833fd0](https://github.com/serverless/serverless/commit/0833fd03d17d292bd4393ecec9569328daae68d2)) ([Mariusz Nowak](https://github.com/medikoo))
- **Plugins:** Ensure to keep `options` as passed to plugins up to date ([#9999](https://github.com/serverless/serverless/issues/9999)) ([e3af1f3](https://github.com/serverless/serverless/commit/e3af1f3a94253a7900de104afaa1c49aa436965c)) ([Mariusz Nowak](https://github.com/medikoo))
- **Telemetry:** Ensure to not show backend notification on error ([#9999](https://github.com/serverless/serverless/issues/9999)) ([dce0ff1](https://github.com/serverless/serverless/commit/dce0ff1a892959b12414f1bff3915fe50b900ba2)) ([Mariusz Nowak](https://github.com/medikoo))

### Templates

- Improve source maps handling in `aws-nodejs-typescript` ([#9961](https://github.com/serverless/serverless/issues/9961)) ([28d230f](https://github.com/serverless/serverless/commit/28d230f946df6cbcc8173822494b50cd056ef63c)) ([Adrien Cacciaguerra](https://github.com/adriencaccia))
- Switch to esbuild in `aws-nodejs-typescript` ([#9962](https://github.com/serverless/serverless/issues/9962)) ([aaabb50](https://github.com/serverless/serverless/commit/aaabb50f1beb12683506ca7ab9e93ded75294694)) ([Adrien Cacciaguerra](https://github.com/adriencaccia))

### Maintenance Improvements

- Reorganize hooks resolution ([#9976](https://github.com/serverless/serverless/issues/9976)) ([76006ec](https://github.com/serverless/serverless/commit/76006ec1e80f51e194b51d4c0f2a11c64434158e)) ([Mariusz Nowak](https://github.com/medikoo))
- Simplify lifecycle event hooks resolution ([#9976](https://github.com/serverless/serverless/issues/9976)) ([8b4498c](https://github.com/serverless/serverless/commit/8b4498c911e24ef7a46daf66380f1c122f988af3)) ([Mariusz Nowak](https://github.com/medikoo))
- Replace `_.flatMap` usage ([#9948](https://github.com/serverless/serverless/issues/9948)) ([26b8bd5](https://github.com/serverless/serverless/commit/26b8bd5c5fd2154f47fa12804f1aee140000155f)) ([Jonas Matos](https://github.com/JonasMatos0))
- **CLI: New logs (experimental):**
  - Fix final `deploy` statuses timing ([#9967](https://github.com/serverless/serverless/issues/9967)) ([084a995](https://github.com/serverless/serverless/commit/084a9955f440ee18847df8a3087aba38405883b7)) ([Mariusz Nowak](https://github.com/medikoo))
  - Fix CloudFormation update resources status log in _verbose_ mode ([#9967](https://github.com/serverless/serverless/issues/9967)) ([bcd8a02](https://github.com/serverless/serverless/commit/bcd8a022a1e2e50a5d2708c374f4d5bcc30c80b5)) ([Mariusz Nowak](https://github.com/medikoo))
  - Ensure to strip colors from error messages ([#9967](https://github.com/serverless/serverless/issues/9967)) ([80005aa](https://github.com/serverless/serverless/commit/80005aaf6b57aa8d013fe4cda0be52d494cd4d78)) ([Mariusz Nowak](https://github.com/medikoo))
  - Ensure to write outputs on `info` ([#9991](https://github.com/serverless/serverless/issues/9991)) ([43d17de](https://github.com/serverless/serverless/commit/43d17debee20bfc7ee535fd643df0538f8bee9f8)) ([Mariusz Nowak](https://github.com/medikoo))
  - Present deprecations with single summary log ([#9960](https://github.com/serverless/serverless/issues/9960)) ([7eba95f](https://github.com/serverless/serverless/commit/7eba95fcb7f9b09a8a2aebd50c433f92e15cac97)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Add timer to final `deploy` statuses ([#9959](https://github.com/serverless/serverless/issues/9959)) ([7828cc7](https://github.com/serverless/serverless/commit/7828cc77f1fcea8f901887c12b07f5e18b34dcc8)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - _debug_ (previously _verbose_) `deploy` logs ([#9967](https://github.com/serverless/serverless/issues/9967)) ([655140b](https://github.com/serverless/serverless/commit/655140b764c8f2998188c3d47110494cbd742688)) ([Mariusz Nowak](https://github.com/medikoo))
  - Help output ([#9998](https://github.com/serverless/serverless/issues/9998)) ([b2df3cc](https://github.com/serverless/serverless/commit/b2df3cc0c8cba17c1995d3038e4a2caaca2f47f5)) ([Mariusz Nowak](https://github.com/medikoo))
  - `deploy function` command ([#9990](https://github.com/serverless/serverless/issues/9990)) ([4d42ce3](https://github.com/serverless/serverless/commit/4d42ce3fa4f44f63d68a3841752746021500fe4f)) ([Mariusz Nowak](https://github.com/medikoo))
  - `deploy list functions` command ([#10000](https://github.com/serverless/serverless/issues/10000)) ([ffbdfed](https://github.com/serverless/serverless/commit/ffbdfed292fdc379040052e6ec73107e5fdae5a8)) ([Mariusz Nowak](https://github.com/medikoo))
  - `deploy list` command ([#10000](https://github.com/serverless/serverless/issues/10000)) ([9d6482c](https://github.com/serverless/serverless/commit/9d6482c6710cb2d05c8c03a29e207881efcc0138)) ([Mariusz Nowak](https://github.com/medikoo))
  - `package` command ([#9956](https://github.com/serverless/serverless/issues/9956)) ([fa2507d](https://github.com/serverless/serverless/commit/fa2507dad06b037aa5a24b3392432cefc810a972)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - `deploy function` command ([#9990](https://github.com/serverless/serverless/issues/9990)) ([10df2e5](https://github.com/serverless/serverless/commit/10df2e5300e04ec9d00ebd343d9d8fe30c96afa7)) ([Mariusz Nowak](https://github.com/medikoo))
  - _verbose_ logs for `deploy` operation ([#9967](https://github.com/serverless/serverless/issues/9967)) ([e423404](https://github.com/serverless/serverless/commit/e423404290a757a8adfc97d45e9aef7aa93f1404)) ([Mariusz Nowak](https://github.com/medikoo))
  - dapt pre-created log style generators ([#9998](https://github.com/serverless/serverless/issues/9998)) ([8c9bd4a](https://github.com/serverless/serverless/commit/8c9bd4a6eda58d2ed6da08cc3bb806d970df4d17)) ([Mariusz Nowak](https://github.com/medikoo))
  - Convert custom resource packaging related log ([#9989](https://github.com/serverless/serverless/issues/9989)) ([0f0b85a](https://github.com/serverless/serverless/commit/0f0b85a6373dfcd9d21f1668e7fb3e0d20a3b393)) ([Mariusz Nowak](https://github.com/medikoo))
  - `logs` command ([#9991](https://github.com/serverless/serverless/issues/9991)) ([cbd2e64](https://github.com/serverless/serverless/commit/cbd2e64f705e54e37dd9116d0931a3a96bceaa88)) ([Mariusz Nowak](https://github.com/medikoo))
  - Refactor main progress event with `isMainEvent` option ([#9981](https://github.com/serverless/serverless/issues/9981)) ([a6553f8](https://github.com/serverless/serverless/commit/a6553f8668b66e2281626e7e79a3a2042279f92d)) ([Mariusz Nowak](https://github.com/medikoo))

## [2.59.0](https://github.com/serverless/serverless/compare/v2.58.0...v2.59.0) (2021-09-14)

### Features

- **CLI Onboarding:** Switch to `httpApi`-based templates ([#9954](https://github.com/serverless/serverless/pull/9954)) ([12216db](https://github.com/serverless/serverless/commit/12216db579f7f2d055410f1ea9449825628631b7)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **CLI:** First iteration of support for `verbose` mode in `deploy` with modern logs ([#9952](https://github.com/serverless/serverless/pull/9952)) ([fbdd124](https://github.com/serverless/serverless/commit/fbdd124029d10ef029ee5446777db44f907e026c)) ([Piotr Grzesik](https://github.com/pgrzesik))

### Bug Fixes

- **AWS API Gateway:** Ensure consistent default for `cors` conf ([#9909](https://github.com/serverless/serverless/issues/9909)) ([7cd3966](https://github.com/serverless/serverless/commit/7cd3966897fa4432caf3f2bda0037df0c76e382b)) ([Seungchan Ahn](https://github.com/issea1015))

### Maintenance Improvements

- Replace `_.pick` with native property assignment ([#9937](https://github.com/serverless/serverless/issues/9937)) ([6087fa3](https://github.com/serverless/serverless/commit/6087fa3400b508092a5113d40e4b2c4fd8ec22a7)) ([Jonas Matos](https://github.com/JonasMatos0))

## [2.58.0](https://github.com/serverless/serverless/compare/v2.57.0...v2.58.0) (2021-09-13)

### Features

- **AWS API Gateway:** Support `enabled` for `apiKeys` config ([#9918](https://github.com/serverless/serverless/pull/9918)) ([1107763](https://github.com/serverless/serverless/commit/1107763df8fb07a40ec45529f77d99e5a0f6d4d6)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **AWS CloudFront:** Support `behavior.CachePolicyId` ([#9895](https://github.com/serverless/serverless/issues/9895)) ([3abc2f0](https://github.com/serverless/serverless/commit/3abc2f06428b72d964aa8683c34cdcf1d761d140)) ([Seungchan Ahn](https://github.com/issea1015))
- **AWS EventBridge:** Support `deadLetterQueue` and `retryPolicy` ([#9903](https://github.com/serverless/serverless/pull/9903)) ([130fb38](https://github.com/serverless/serverless/commit/130fb3838fd3ea382caabffad74fde8a4041d4fc)) ([Eve](https://github.com/evemontalvao) & [JP Bochi](https://github.com/jpbochi))
- **AWS ActiveMQ:** Add support for `activemq` event ([#8840](https://github.com/serverless/serverless/issues/8840)) ([cacb529](https://github.com/serverless/serverless/commit/cacb529925ed2b2c591984f48bc52cf31f88e698)) ([lewgordon](https://github.com/lewgordon) & [Piotr Grzesik](https://github.com/pgrzesik))
- **AWS Schedule:** Allow multiple `rate` expressions in single event ([#9892](https://github.com/serverless/serverless/pull/9892)) ([9f0bc68](https://github.com/serverless/serverless/commit/9f0bc689cc2ac3e53b4db665b899e1446ac37456)) ([Federico Jasson](https://github.com/federicojasson))
- **CLI:**
  - Configure log writing with new (experimental) log engine ([#9923](https://github.com/serverless/serverless/pull/9923)) ([ec93174](https://github.com/serverless/serverless/commit/ec93174b8ccfe1715ce3615dcb2223b145ad0f31)) ([Mariusz Nowak](https://github.com/medikoo))
  - Introduce first iteration of modern logs for `deploy` ([#9934](https://github.com/serverless/serverless/issues/9934)) ([171897d](https://github.com/serverless/serverless/commit/171897d60e5adaa590be1f08c99ab2cc76e89ee4)) ([Piotr Grzesik](https://github.com/pgrzesik))
- Do not retry AWS requests if the token has expired ([#9914](https://github.com/serverless/serverless/issues/9914)) ([b0ca237](https://github.com/serverless/serverless/commit/b0ca2376bbfb543d98db1585c3a20a391e1791c6)) ([Mars Lan](https://github.com/mars-lan))
- Support `error` hook to be triggered on command error ([#9936](https://github.com/serverless/serverless/pull/9936)) ([5c9766c](https://github.com/serverless/serverless/commit/5c9766c085531b04e169aa36a552159755029cca)) ([Mariusz Nowak](https://github.com/medikoo))

### Bug Fixes

- **AWS API Gateway:** Ensure proper `RequestValidator` name ([#9910](https://github.com/serverless/serverless/pull/9910)) ([510b1d1](https://github.com/serverless/serverless/commit/510b1d165924d000aa8e81e74e27c69ac1a2e0b6)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **AWS CloudFront:** Recognize `behavior.TrustedKeyGroups` in schema ([#9884](https://github.com/serverless/serverless/pull/9884)) ([da71df6](https://github.com/serverless/serverless/commit/da71df603295397229589c88dd8366426e06e982)) ([Petr Reshetin](https://github.com/preshetin))
- **AWS Lambda:** Recognize `Fn::If` function for `environment` ([#9905](https://github.com/serverless/serverless/pull/9905)) ([63743ad](https://github.com/serverless/serverless/commit/63743ade31207049eee1811203db5622bc510f1a)) ([Piotr Grzesik](https://github.com/pgrzesik))

### Maintenance Improvements

- **CLI:**
  - Ensure no monkey patching by progress override ([#9923](https://github.com/serverless/serverless/pull/9923)) ([e46ce80](https://github.com/serverless/serverless/commit/e46ce80d99414ff730355efd1636bab71bb1771c)) ([Mariusz Nowak](https://github.com/medikoo))
  - Ensure to clear progress in expected time points ([#9928](https://github.com/serverless/serverless/pull/9928)) ([29aec52](https://github.com/serverless/serverless/commit/29aec529b53d7dd10f4ec61db7c0dc3859995d27)) ([Mariusz Nowak](https://github.com/medikoo))
- Replace `fse.access` with `fs.promises.access` ([#9915](https://github.com/serverless/serverless/issues/9915)) ([5155e01](https://github.com/serverless/serverless/commit/5155e0180e0cd5e3130bc74e308a97c0ea1a5c2b)) ([Sudipto Das](https://github.com/sdas13))
- Replace `fse.readFile` with `fs.promises.readFile` ([#9935](https://github.com/serverless/serverless/issues/9935)) ([f431218](https://github.com/serverless/serverless/commit/f431218790ae31efdc4e0a65a5b17a32605ede3e)) ([Sudipto Das](https://github.com/sdas13))
- Use `getCompiledTemplateS3Suffix` from `provider.naming` ([#9926](https://github.com/serverless/serverless/pull/9926)) ([95d3024](https://github.com/serverless/serverless/commit/95d3024ef55ce80edf20fe27d9c72ffd15bba2bb)) ([Andreas Kohn](https://github.com/ankon))
- Internal API to register service outputs ([#9933](https://github.com/serverless/serverless/pull/9933)) ([b425cf1](https://github.com/serverless/serverless/commit/b425cf1582623c1e796ae9f3d33dc060a9492cb5)) ([Mariusz Nowak](https://github.com/medikoo))
- Register service outputs ([#9933](https://github.com/serverless/serverless/pull/9933)) ([312266e](https://github.com/serverless/serverless/commit/312266e90819866199354183641954636bd5a076)) ([Mariusz Nowak](https://github.com/medikoo))

### Templates

- Remove unnecessary `fmt.Sprintf` in `tencent-go` ([#9847](https://github.com/serverless/serverless/pull/9847)) ([e798c26](https://github.com/serverless/serverless/commit/e798c269df6f456bccf6a1e755015ea1e7631117)) ([kou](https://github.com/kou-pg-0131))

## [2.57.0](https://github.com/serverless/serverless/compare/v2.56.0...v2.57.0) (2021-08-31)

### Features

- **Variables:** Enable `env` variables in `provider.stage` property ([#9896](https://github.com/serverless/serverless/issues/9896)) ([bbb6c6c](https://github.com/serverless/serverless/commit/bbb6c6cd7dea9100af3ff84dd490b2cac1e2971e)) ([Mariusz Nowak](https://github.com/medikoo))

### Bug Fixes

- **AWS API Gateway:**
  - Recognize CF functions at `functions[].events[].http.connectionId` ([#9894](https://github.com/serverless/serverless/issues/9894)) ([3e8858b](https://github.com/serverless/serverless/commit/3e8858b1a8cde32a3659498c6dbdc7d8637e86c6)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Recognize CF functions at `functions[].events[].http.request.headers[].mappedValue` ([#9894](https://github.com/serverless/serverless/issues/9894)) ([868ac02](https://github.com/serverless/serverless/commit/868ac02fd4d41a893d23a3f29101e3a3b952597b)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Recognize CF functions at `functions[].events[].http.request.uri` ([#9894](https://github.com/serverless/serverless/issues/9894)) ([13ce56a](https://github.com/serverless/serverless/commit/13ce56ae314dff1c157fc8351fc702bf15573fce)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Fix request validator triage ([#9887](https://github.com/serverless/serverless/issues/9887)) ([cb109dd](https://github.com/serverless/serverless/commit/cb109dd835ec358bfb1af10fe8f82aa283ffbafe)) ([Mariusz Nowak](https://github.com/medikoo))
- **Variables:** Fix new sources resolution error message at old resolver ([#9888](https://github.com/serverless/serverless/issues/9888)) ([8dece7f](https://github.com/serverless/serverless/commit/8dece7f6c6544f91366a2c8f70389be8b4b659c8)) ([Mariusz Nowak](https://github.com/medikoo))

### Maintenance Improvements

- **Variables:** Enable early `sls:stage` resolution ([#9890](https://github.com/serverless/serverless/issues/9890)) ([56e9423](https://github.com/serverless/serverless/commit/56e9423cd74dc05cc85b176bb1f0502f7ce05139)) ([Mariusz Nowak](https://github.com/medikoo))
- Replace `fse.writeFile` with `fs.promises.writeFile` ([#9870](https://github.com/serverless/serverless/issues/9870)) ([05fff98](https://github.com/serverless/serverless/commit/05fff98a0003b22a66e8932c622c0e10c57bf06b)) ([Sudipto Das](https://github.com/sdas13))
- Upgrade `filesize` to v8 ([#9901](https://github.com/serverless/serverless/issues/9901)) ([9a2511c](https://github.com/serverless/serverless/commit/9a2511cf90c60ba5b67ecea81121328c8dd93702)) ([Mariusz Nowak](https://github.com/medikoo))

## [2.56.0](https://github.com/serverless/serverless/compare/v2.55.0...v2.56.0) (2021-08-25)

### Features

- **AWS EventBridge:** Support disabling a rule ([#9865](https://github.com/serverless/serverless/issues/9865)) ([6193d38](https://github.com/serverless/serverless/commit/6193d3867ec826898d4effbd641e49a35d9efbbc)) ([Jake Scott](https://github.com/jakejscott))
- **AWS HTTP API:** Support `shouldStartNameWithService` option ([#9758](https://github.com/serverless/serverless/issues/9758)) ([ef5a8fa](https://github.com/serverless/serverless/commit/ef5a8faf13a8fbf8564e7c0621e88d1ea5357ea5)) ([Thiago Moraes](https://github.com/thiagomr))
- **CLI Onboarding:** Improve onboarding messaging ([#9877](https://github.com/serverless/serverless/pull/9877)) ([f69a19c](https://github.com/serverless/serverless/commit/f69a19c6804366a34324e7cfcbbdb3f247a12b85)) ([Piotr Grzesik](https://github.com/pgrzesik))

### Bug Fixes

- **AWS HTTP API:** Always allow to define catch-all route ([#9840](https://github.com/serverless/serverless/issues/9840)) ([7e9bfd6](https://github.com/serverless/serverless/commit/7e9bfd63fce56f880a3ad0379fd97fdfce89d91b)) ([Karim Kanso](https://github.com/kazkansouh))
- **CLI:** Mark `dashboard` command with optional service dependency ([#9874](https://github.com/serverless/serverless/pull/9874)) ([9a8e7e4](https://github.com/serverless/serverless/commit/9a8e7e44b44fdcf4c43d6e11c5eefa5051782506)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **AWS Local Invocation:** Support `python3.9` runtime ([#9879](https://github.com/serverless/serverless/issues/9879)) ([ee17ee5](https://github.com/serverless/serverless/commit/ee17ee5aca25af152c2720a55199d92dfab3216d)) ([Shane R. Spencer](https://github.com/whardier))
- **AWS Lambda:** Prevent external subscription filter removal for CloudWatch ([#9839](https://github.com/serverless/serverless/issues/9839)) ([afc9a13](https://github.com/serverless/serverless/commit/afc9a13386479f79b4c9ef64b65af5bbcdfaa68b)) ([Han Sang Hoon (한상훈)](https://github.com/poerty))

### Maintenance Improvements

- Convert `upload` and `rollback` to `async/await` ([#9866](https://github.com/serverless/serverless/issues/9866)) ([0682ba8](https://github.com/serverless/serverless/commit/0682ba8b6a70d27e74c478d6e5fa5de71b9e0070)) ([Remigiusz Orłowski](https://github.com/remi00))

## [2.55.0](https://github.com/serverless/serverless/compare/v2.54.0...v2.55.0) (2021-08-18)

### Features

- **AWS Lambda:** Recognize `python3.9` as valid runtime ([#9854](https://github.com/serverless/serverless/pull/9854)) ([1aa24b8](https://github.com/serverless/serverless/commit/1aa24b8991032ba3fe6f2c4b65bf0e70bc4171dd)) ([Piotr Grzesik](https://github.com/pgrzesik))

### Bug Fixes

- **AWS HTTP API:** Properly handle authorizer function with alias (e.g. with `provisionedConcurrency`) ([#9850](https://github.com/serverless/serverless/pull/9850)) ([0ca6aaa](https://github.com/serverless/serverless/commit/0ca6aaae526b16df2039edff5db166a39bb1de10)) ([Piotr Grzesik](https://github.com/pgrzesik))

### Maintenance Improvements

- **CLI Onboarding:** Adjust summary messages in deploy step ([#9835](https://github.com/serverless/serverless/pull/9835)) ([b751c50](https://github.com/serverless/serverless/commit/b751c505c8050e229edb77d44016925c4e52a05e)) ([Piotr Grzesik](https://github.com/pgrzesik))
- Replace `fse.stat` with `fs.promises.stat` ([#9845](https://github.com/serverless/serverless/issues/9845)) ([bb0484e](https://github.com/serverless/serverless/commit/bb0484e6b54a3cc6aed46ff23100e08c90c995ce)) ([Sudipto Das](https://github.com/sdas13))
- **Telemetry:** Recognize `notificationsMode` ([#9851](https://github.com/serverless/serverless/pull/9851)) ([00fdba1](https://github.com/serverless/serverless/commit/00fdba154655b15b5b2de4b9ceca08f8bfce599e)) ([Piotr Grzesik](https://github.com/pgrzesik))

## [2.54.0](https://github.com/serverless/serverless/compare/v2.53.1...v2.54.0) (2021-08-12)

### Features

- **AWS IAM:** Resign from deprecating old format of IAM settings ([#9778](https://github.com/serverless/serverless/pull/9778)) ([847dd8f](https://github.com/serverless/serverless/commit/847dd8f47503ddf03971122e5700110aa3ff77d1)) ([Mariusz Nowak](https://github.com/medikoo))
- **AWS Lambda:** Add support for multiple subscription filters ([#9760](https://github.com/serverless/serverless/issues/9760)) ([5c9ca56](https://github.com/serverless/serverless/commit/5c9ca56d14a90dfd9aa5c064bd15137504336ed7)) ([Han Sang Hoon (한상훈)](https://github.com/poerty))
- **AWS API Gateway:** Deprecate default for `identitySource` for `request` authorizers with disabled caching ([#9825](https://github.com/serverless/serverless/pull/9825)) ([0e01d9e](https://github.com/serverless/serverless/commit/0e01d9e337860b9d1136586fbfaf0c43ac21cde0)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **CLI:** Deprecate `-v` as alias for `--verbose` ([#9811](https://github.com/serverless/serverless/commit/53b41eb53aeefe22dc29b785a428f3b184906d2c)) ([53b41eb](https://github.com/serverless/serverless/commit/53b41eb53aeefe22dc29b785a428f3b184906d2c)) ([Piotr Grzesik](https://github.com/pgrzesik))

### Bug Fixes

- **AWS Deploy:** Ensure right code for `deploy -f` deprecation ([#9833](https://github.com/serverless/serverless/pull/9833)) ([90877d5](https://github.com/serverless/serverless/commit/90877d575ec9436db30a3a16fc90e5190ea30018)) ([Mariusz Nowak](https://github.com/medikoo))
- **AWS Layers:** Support references to external layers ([#9826](https://github.com/serverless/serverless/pull/9826)) ([dc74f41](https://github.com/serverless/serverless/commit/dc74f41470447c1fab0a646c15284a4eb212ecb6)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **Variables:** Unconditionally deprecate old vars engine extensions ([#9827](https://github.com/serverless/serverless/pull/9827)) ([b7f4e08](https://github.com/serverless/serverless/commit/b7f4e08661cd149a29ae7107241a16928dc606eb)) ([Mariusz Nowak](https://github.com/medikoo))

### [2.53.1](https://github.com/serverless/serverless/compare/v2.53.0...v2.53.1) (2021-08-06)

### Bug Fixes

- **AWS API Gateway:** Ensure `MinimumCompressionSize` can be set to 0 ([#9806](https://github.com/serverless/serverless/issues/9806)) ([f0ae032](https://github.com/serverless/serverless/commit/f0ae032252f88d4d864c2bfe526d70064168231a)) ([Lewis Putz](https://github.com/Putzy))

### Maintenance Improvements

- **CLI:** Change formatting of notifications ([#9807](https://github.com/serverless/serverless/issues/9807)) ([7c51f55](https://github.com/serverless/serverless/commit/7c51f55f5b8af6f853560ba5d757c65b1068a7ab)) ([Piotr Grzesik](https://github.com/pgrzesik))
- Use `async` in `lib/utils` ([#9809](https://github.com/serverless/serverless/issues/9809)) ([48c3d99](https://github.com/serverless/serverless/commit/48c3d990beccef7dc3f4b5d29ec5bc4238fd9cf6)) ([Nyambayar Turbat](https://github.com/nyamba))

## [2.53.0](https://github.com/serverless/serverless/compare/v2.52.1...v2.53.0) (2021-08-04)

### Features

- **Variables:** Accept case-insensitive strings in `strToBool` ([#9770](https://github.com/serverless/serverless/issues/9770)) ([612f668](https://github.com/serverless/serverless/commit/612f668c931013bea21b91f47d9cbfd1c7dbb888)) ([Shane R. Spencer](https://github.com/whardier))

### Bug Fixes

- **AWS API Gateway:** Ensure to attach validator when required parameters are defined ([#9793](https://github.com/serverless/serverless/issues/9793)) ([d275459](https://github.com/serverless/serverless/commit/d2754594c462afd39e1576312e361ca57d4f13f2)) ([Karim Kanso](https://github.com/kazkansouh))
- **Plugins:** Improve error message when a plugin is missing ([#9798](https://github.com/serverless/serverless/issues/9798)) ([5c9df56](https://github.com/serverless/serverless/commit/5c9df56f1bc89af1fd929519f3cf8dac967e514d)) ([Matthieu Napoli](https://github.com/mnapoli))

### Maintenance Improvements

- **Telemetry:** Recognize used variable sources ([#9790](https://github.com/serverless/serverless/pull/9790)) ([60d729b](https://github.com/serverless/serverless/commit/60d729b5d42ae32cc418b9578582da3dc8492754)) ([Piotr Grzesik](https://github.com/pgrzesik))
- Replace `fse.readdir` with `fs.promises.readdir` ([#9780](https://github.com/serverless/serverless/issues/9780)) ([1e00f9e](https://github.com/serverless/serverless/commit/1e00f9edfb5f7618759f9f03d0dad58701a5a27a)) ([Sudipto Das](https://github.com/sdas13))
- Use `async` in `lib/plugins/create` ([#9683](https://github.com/serverless/serverless/issues/9683)) ([4b87497](https://github.com/serverless/serverless/commit/4b87497875a19348e444763eea85671ed2c4f0b7)) ([Nyambayar Turbat](https://github.com/nyamba))
- Use `async` in `lib/plugins/plugin` ([#9680](https://github.com/serverless/serverless/issues/9680)) ([377da09](https://github.com/serverless/serverless/commit/377da097c564778c8d2c42ffe49e38000c520106)) ([Nyambayar Turbat](https://github.com/nyamba))

### [2.52.1](https://github.com/serverless/serverless/compare/v2.52.0...v2.52.1) (2021-07-22)

### Bug Fixes

- **CLI Onboarding:** Ensure credentials resolution is always performed before deploy step ([#9761](https://github.com/serverless/serverless/pull/9761)) ([b85f393](https://github.com/serverless/serverless/commit/b85f3934ed87e9c78494e9ad26163ee1d041599e)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **CLI:**
  - Ensure `processedInput` is properly resolved in local fallback ([#9769](https://github.com/serverless/serverless/pull/9769)) ([464467e](https://github.com/serverless/serverless/commit/464467e2bece1bf3f35fe60041fa170f412087d3)) ([Mariusz Nowak](https://github.com/medikoo))
  - Fix validation of `deprecationNotificationMode` config option ([#9762](https://github.com/serverless/serverless/issues/9762)) ([916c76f](https://github.com/serverless/serverless/commit/916c76f48ca86c3e31b719d2bb655c34d0287cec)) ([frozenbonito](https://github.com/frozenbonito))
- Fix `functions[]` validation (ignore `null` values) ([#9756](https://github.com/serverless/serverless/pull/9756)) ([922ec00](https://github.com/serverless/serverless/commit/922ec0093f0d4ab6f2b2055c6e6f2d5ec1f9d06e)) ([Mariusz Nowak](https://github.com/medikoo))

### Maintenance Improvements

- **CLI Onboarding:**
  - Move `dashboard-login` step from `@serverless/dashboard-plugin` ([#9766](https://github.com/serverless/serverless/pull/9766)) ([adef710](https://github.com/serverless/serverless/commit/adef7102df2958e976445f0c247895f82decebf9)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Move `dashboard-set-org` from `@serverless/dashboard-plugin` ([#9766](https://github.com/serverless/serverless/pull/9766)) ([afdf77c](https://github.com/serverless/serverless/commit/afdf77c960c990f7daa445532789aebb9dc15a53)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **Telemetry:** Use `prompt-with-history` for onboarding telemetry ([#9768](https://github.com/serverless/serverless/pull/9768)) ([4d56be5](https://github.com/serverless/serverless/commit/4d56be562a4bdaf2588bdc42227a451d098d1420)) ([Piotr Grzesik](https://github.com/pgrzesik))
- Replace `fse.unlink` with `fs.promises.unlink` ([#9754](https://github.com/serverless/serverless/issues/9754)) ([daee1d5](https://github.com/serverless/serverless/commit/daee1d5375efdb748b85b85a2a4675ac3277001f)) ([Sudipto Das](https://github.com/sdas13))

## [2.52.0](https://github.com/serverless/serverless/compare/v2.51.2...v2.52.0) (2021-07-15)

### Features

- **AWS CloudFormation:** Allow to disable default export names ([#9748](https://github.com/serverless/serverless/pull/9748)) ([6f49488](https://github.com/serverless/serverless/commit/6f494888cc01853894ec33859edbd77a06dc9d76)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **CLI:** Automatically expand loaded env variables from `.env` files ([#9615](https://github.com/serverless/serverless/issues/9615)) ([1864969](https://github.com/serverless/serverless/commit/186496922a0c4d69f3101dde0a9f4a0d89995ad0)) ([David Asensio Cañas](https://github.com/d-asensio))

### Bug Fixes

- **CLI:** Do not validate configuration with `plugin ..` commands ([#9741](https://github.com/serverless/serverless/pull/9741)) ([040036d](https://github.com/serverless/serverless/commit/040036d1869ceb207da6dad53f17e1ee1b6ee20a)) ([Mariusz Nowak](https://github.com/medikoo))
- **Variables:** In `ssm` source auto parse only object JSON notation ([#9747](https://github.com/serverless/serverless/pull/9747)) ([8c741d1](https://github.com/serverless/serverless/commit/8c741d1d97f021995f37a61d7340ddfa749cdab9)) ([Mariusz Nowak](https://github.com/medikoo))
- Improve `functions` validation ([#9741](https://github.com/serverless/serverless/pull/9741)) ([3e58d62](https://github.com/serverless/serverless/commit/3e58d628e7b8f4dbc8e14adf94dd98546099f3be)) ([Mariusz Nowak](https://github.com/medikoo))

### Maintenance Improvements

- **Telemetry:** Record initial context for interactive setup ([#9736](https://github.com/serverless/serverless/pull/9736)) ([560aee5](https://github.com/serverless/serverless/commit/560aee5feb9f143e93933f6536e76edc9a3e56bb)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **CLI:** Reuse already imported module ([#9741](https://github.com/serverless/serverless/pull/9741)) ([be441cc](https://github.com/serverless/serverless/commit/be441ccd9157b351fffe6ea21664624aeeeb4b29)) ([Mariusz Nowak](https://github.com/medikoo))
- Add `has-local-credentials` util ([#9736](https://github.com/serverless/serverless/pull/9736)) ([82a35b3](https://github.com/serverless/serverless/commit/82a35b3903ad5d8f761612105036fc11a37e9e55)) ([Piotr Grzesik](https://github.com/pgrzesik))

### [2.51.2](https://github.com/serverless/serverless/compare/v2.51.1...v2.51.2) (2021-07-08)

### Bug Fixes

- **Packaging:** Fix `package.artifact` validation for S3 urls ([#9725](https://github.com/serverless/serverless/issues/9725)) ([ab3c543](https://github.com/serverless/serverless/commit/ab3c543089b0fde4107fc0e579c19f85e0a4ee79)) ([Mariusz Nowak](https://github.com/medikoo))

### [2.51.1](https://github.com/serverless/serverless/compare/v2.51.0...v2.51.1) (2021-07-08)

### Bug Fixes

- **CLI:** Fix `SIGINT` signal handling ([#9712](https://github.com/serverless/serverless/issues/9712)) ([c5a3f69](https://github.com/serverless/serverless/commit/c5a3f6907a115ea2d511b0aa9905a2e762514867)) ([Mariusz Nowak](https://github.com/medikoo))
- **Packaging:** Validate `package.artifact` paths ([#9721](https://github.com/serverless/serverless/issues/9721)) ([21c0fed](https://github.com/serverless/serverless/commit/21c0fedc507651bb98687acc4145ed667d853589)) ([Mariusz Nowak](https://github.com/medikoo))
- **AWS Local Invocation:** Bump AWS Java pom version to pull in fix ([#9714](https://github.com/serverless/serverless/issues/9714)) ([504b42a](https://github.com/serverless/serverless/commit/504b42ae0fefd04ccfa013746371c49a02d8a4d3)) ([tlloyd-synalogik](https://github.com/tlloyd-synalogik))

### Maintenance Improvements

- **Telemetry:**
  - Report all interruption signals ([#9712](https://github.com/serverless/serverless/issues/9712)) ([7354c20](https://github.com/serverless/serverless/commit/7354c2000f25d526f8c3fd97c6d4d22054388755)) ([Mariusz Nowak](https://github.com/medikoo))
  - Report whether we're in context of TTY terminal ([#9712](https://github.com/serverless/serverless/issues/9712)) ([9cea555](https://github.com/serverless/serverless/commit/9cea555e88bdaadf717def21b5298a64c7ce79b9)) ([Mariusz Nowak](https://github.com/medikoo))
  - Ensure no doubled telemetry in edge cases ([#9716](https://github.com/serverless/serverless/issues/9716)) ([fd5005e](https://github.com/serverless/serverless/commit/fd5005e404debe103ca54974ca9aee431554ceb8)) ([Mariusz Nowak](https://github.com/medikoo))
- **CLI:** Improve module imports order ([#9712](https://github.com/serverless/serverless/issues/9712)) ([dff2799](https://github.com/serverless/serverless/commit/dff2799941a1da8c2d5fe76144393db241a7637c)) ([Mariusz Nowak](https://github.com/medikoo))

## [2.51.0](https://github.com/serverless/serverless/compare/v2.50.0...v2.51.0) (2021-07-06)

### Features

- **AWS Kafka:** Add support for `SASL/PLAIN` auth to `kafka` event ([#9666](https://github.com/serverless/serverless/pull/9666)) ([3e14f06](https://github.com/serverless/serverless/commit/3e14f063052385026425021379bfc883dac5ff74)) ([Daniele Iasella](https://github.com/overbit))
- **CLI:** New `warn:summary` (default) deprecations logging mode ([#9693](https://github.com/serverless/serverless/pull/9693)) ([9b624a5](https://github.com/serverless/serverless/commit/9b624a50677a0363c052b4ea567c050af7863073)) ([Mariusz Nowak](https://github.com/medikoo))

### Bug Fixes

- **CLI:** Recognize `--verbose` option in `info` command ([#9695](https://github.com/serverless/serverless/pull/9695)) ([b124152](https://github.com/serverless/serverless/commit/b1241522ec378f7b7b431050ddc861fef040efc4)) ([Mariusz Nowak](https://github.com/medikoo))

### Maintenance Improvements

- **CLI:** Fix typo in error message ([#9682](https://github.com/serverless/serverless/issues/9682)) ([f16c45f](https://github.com/serverless/serverless/commit/f16c45f84b8be1e469bfdd92191fc760b8f1631e)) ([KIDANI Akito](https://github.com/kdnakt))
- **Telemetry:**
  - Properly handle situation when not in service dir in credentials step ([#9678](https://github.com/serverless/serverless/pull/9678)) ([b21c1e4](https://github.com/serverless/serverless/commit/b21c1e415b67cdc8f1fb0ab14152eaf3c6550894))
  - Ensure to pass all steps with configured questions ([#9701](https://github.com/serverless/serverless/pull/9701)) ([b5d3167](https://github.com/serverless/serverless/commit/b5d3167e9fdd5f08af1389b975322f2146b22507)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Correctly report `outcome` for interactive setup ([#9699](https://github.com/serverless/serverless/pull/9699)) ([0c5b8dd](https://github.com/serverless/serverless/commit/0c5b8dd831bcde80628c2ac548172ffaa9ce9ca6)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Ensure telemetry generation and related utils are sync ([#9692](https://github.com/serverless/serverless/pull/9692)) ([e65199c](https://github.com/serverless/serverless/commit/e65199c05213e1bac17acedc84cdd6dfd26ff00a)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Report `commandUsage` as object ([#9690](https://github.com/serverless/serverless/pull/9690)) ([cc24bc2](https://github.com/serverless/serverless/commit/cc24bc2ae280237b3d439e1934ab75710e0f259f)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Handle interruptions and persist telemetry data ([#9699](https://github.com/serverless/serverless/pull/9699)) ([502f7e7](https://github.com/serverless/serverless/commit/502f7e711f0954c2960fb790b749002aeb1789fc)) ([Piotr Grzesik](https://github.com/pgrzesik))
- Drop old variables engine related deprecation ([#9698](https://github.com/serverless/serverless/pull/9698)) ([5b54ed2](https://github.com/serverless/serverless/commit/5b54ed2e2685c24439c0f835b50a024dbf9d39a9)) ([Mariusz Nowak](https://github.com/medikoo))
- Make deprecations default mode internally modifyable ([#9693](https://github.com/serverless/serverless/pull/9693)) ([07a69a8](https://github.com/serverless/serverless/commit/07a69a836c506e3ab8ab976ef27d4f3b672722f7)) ([Mariusz Nowak](https://github.com/medikoo))
- Replace `fse.createWriteStream` with `fs.createWriteStream` ([#9687](https://github.com/serverless/serverless/pull/9687)) ([3500f64](https://github.com/serverless/serverless/commit/3500f641f5212f196f75081e67d1d1518ac3bb6b)) ([Sudipto Das](https://github.com/sdas13))
- Use `async` in `lib/plugins/package` ([#9644](https://github.com/serverless/serverless/issues/9644)) ([db67b35](https://github.com/serverless/serverless/commit/db67b353c9ed578d7dd334d162efa1ec11fbfa18)) ([Nyambayar Turbat](https://github.com/nyamba))

## [2.50.0](https://github.com/serverless/serverless/compare/v2.49.0...v2.50.0) (2021-07-01)

### Features

- **AWS Lambda:** Support `Fn::If` for `Principal.AWS` ([#9664](https://github.com/serverless/serverless/pull/9664)) ([894ac5b](https://github.com/serverless/serverless/commit/894ac5b6b67eb384dbc29b927161121679afce2d)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **AWS Deploy:** Deprecate `function` option in `deploy` command ([#9364](https://github.com/serverless/serverless/pull/9364)) ([d861d11](https://github.com/serverless/serverless/commit/d861d119ef94baaaa266934783e00a50182d7434)) ([Jaakko Lappalainen](https://github.com/jkklapp) & [Piotr Grzesik](https://github.com/pgrzesik))
- **Variables:**
  - Resolve vars in strings which are subject to be joined ([#9657](https://github.com/serverless/serverless/pull/9657)) ([0e3db01](https://github.com/serverless/serverless/commit/0e3db01db8aeb08b03a98dd7f58a09b66ec8c49e)) ([Mariusz Nowak](https://github.com/medikoo))
  - Support `aws:region` and `aws:accountId` variables ([#9662](https://github.com/serverless/serverless/pull/9662)) ([33794ea](https://github.com/serverless/serverless/commit/33794ea504e714912137796009c29c802f2e24f0)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Support variables across file address resolution ([#9657](https://github.com/serverless/serverless/pull/9657)) ([80b7640](https://github.com/serverless/serverless/commit/80b76406ac305ccb7e55cabd0bd39be6ac7c67c6)) ([Mariusz Nowak](https://github.com/medikoo))

### Bug Fixes

- **AWS Deploy:** Meaningfully report inaccessible file artifacts ([#9668](https://github.com/serverless/serverless/pull/9668)) ([23c290e](https://github.com/serverless/serverless/commit/23c290e4b4049242d62cfb57f4be6aadff6aecf8)) ([Mariusz Nowak](https://github.com/medikoo))
- **AWS Local Invocation:** Fix error handling of invalid file content ([#9667](https://github.com/serverless/serverless/pull/9667)) ([e836722](https://github.com/serverless/serverless/commit/e836722f976af98eb69fc6d3a85781bb7434dfac)) ([Mariusz Nowak](https://github.com/medikoo))
- **CLI Onboarding:**
  - Do not attempt local fallback during onboarding ([#9660](https://github.com/serverless/serverless/pull/9660)) ([ae5be0f](https://github.com/serverless/serverless/commit/ae5be0f5dafaad933000e98142fcb1ec60e04555)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Only call `handleError` if plugin defined ([#9659](https://github.com/serverless/serverless/pull/9659)) ([a80681f](https://github.com/serverless/serverless/commit/a80681ffbf23391cb31d34b8eecaef310d9599a3)) ([Piotr Grzesik](https://github.com/pgrzesik))

### Maintenance Improvements

- **Telemetry:**
  - Include `commandUsage` in case of error ([#9671](https://github.com/serverless/serverless/pull/9671)) ([ac03d83](https://github.com/serverless/serverless/commit/ac03d832896eec26773e5ce06c22c249d240a9ed)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Increase error location coverage ([#9669](https://github.com/serverless/serverless/pull/9669)) ([7264d16](https://github.com/serverless/serverless/commit/7264d1672e93fdb1046cf7ebe859b607c80e31ca)) ([Mariusz Nowak](https://github.com/medikoo))
  - Report `configValidationMode` ([#9669](https://github.com/serverless/serverless/pull/9669)) ([8e2d48f](https://github.com/serverless/serverless/commit/8e2d48fee5a471a960b6a7b55cbd12edc5eb07e6)) ([Mariusz Nowak](https://github.com/medikoo))
  - Report configuration validation result ([#9669](https://github.com/serverless/serverless/pull/9669)) ([01f1586](https://github.com/serverless/serverless/commit/01f158695b22d721320a77a9a0b68b166c63dc3f)) ([Mariusz Nowak](https://github.com/medikoo))

### Templates

- Adjust `runtime` for `openwhisk-python` template ([#9670](https://github.com/serverless/serverless/pull/9670)) ([6a020d1](https://github.com/serverless/serverless/commit/6a020d121ff2dacd6ad62a824964944ae391a662)) ([Piotr Grzesik](https://github.com/pgrzesik))

## [2.49.0](https://github.com/serverless/serverless/compare/v2.48.1...v2.49.0) (2021-06-29)

### Features

- **AWS Lambda:** Support `Fn::FindInMap` for `vpc` config ([#9653](https://github.com/serverless/serverless/pull/9653)) ([34a9d91](https://github.com/serverless/serverless/commit/34a9d91870c36d154427830d3555425b5fd2d14c)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **CLI Onboarding:**
  - Add deploy step ([#9536](https://github.com/serverless/serverless/pull/9536)) ([28a06a0](https://github.com/serverless/serverless/commit/28a06a05aba4306d2f28d26652067b44ed105151)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Allow to setup Dashboard Provider credentials during onboarding ([#9509](https://github.com/serverless/serverless/pull/9509)) ([feb0421](https://github.com/serverless/serverless/commit/feb04219f6be186cc54462906394bbd82f9747b5)) ([Piotr Grzesik](https://github.com/pgrzesik))

### Bug Fixes

- **CLI:** Fix standalone detection on Windows ([#9648](https://github.com/serverless/serverless/pull/9648)) ([4bc8e2e](https://github.com/serverless/serverless/commit/4bc8e2e1944364e2c218cbfc05039c43afa9ab01)) ([Mariusz Nowak](https://github.com/medikoo))
- **Packaging:** Fix artifact generation with temp path on other device ([#9616](https://github.com/serverless/serverless/issues/9616)) ([70fb8b9](https://github.com/serverless/serverless/commit/70fb8b986133789b38fad93c0abab01eaf9dc0c7)) ([Sean Dawson](https://github.com/NoxHarmonium))

### Maintenance Improvements

- Replace `fse.chmod` with `fs.promises.chmod` ([#9647](https://github.com/serverless/serverless/issues/9647)) ([83c7726](https://github.com/serverless/serverless/commit/83c772684d655b233522d1e75128476c29339c83)) ([Sudipto Das](https://github.com/sdas13))
- Add `resolveRegion` util ([#9509](https://github.com/serverless/serverless/pull/9509)) ([98e3668](https://github.com/serverless/serverless/commit/98e3668a2cbb701c109e1ff8dd70a0ece1770f7b)) ([Piotr Grzesik](https://github.com/pgrzesik))
- Add `resolveStage` util ([#9509](https://github.com/serverless/serverless/pull/9509)) ([09bb4fa](https://github.com/serverless/serverless/commit/09bb4fa12270807702dcc26483dbcb94cf733342)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **Telemetry:**
  - Add `hasLocalCredentials` ([#9594](https://github.com/serverless/serverless/pull/9594)) ([5e0d805](https://github.com/serverless/serverless/commit/5e0d80579e857d016fb4db13288b9d81a3859ee1)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Add interactive flow support ([#9594](https://github.com/serverless/serverless/pull/9594)) ([0eba2dc](https://github.com/serverless/serverless/commit/0eba2dcdfeabba58920462ac2cd54d86e3101e05)) ([Piotr Grzesik](https://github.com/pgrzesik))

### Templates

- Use `amd64` arch for `aws-go` template ([#9646](https://github.com/serverless/serverless/issues/9646)) ([cb9f7e2](https://github.com/serverless/serverless/commit/cb9f7e20eedc1db7bb31671c97449e269e992ded)) ([Andrey Kabylin](https://github.com/sysint64))

### [2.48.1](https://github.com/serverless/serverless/compare/v2.48.0...v2.48.1) (2021-06-25)

### Bug Fixes

- **AWS API Gateway:** Ensure that `Method` resource depends on `Permission` resource ([#9609](https://github.com/serverless/serverless/pull/9609)) ([93b9027](https://github.com/serverless/serverless/commit/93b9027f0d48650df50d0a8352d0edaf2bd2e0da)) ([Nyambayar Turbat](https://github.com/nyamba))
- **CLI:**
  - Ensure to list version in case of fallback from some versions ([#9641](https://github.com/serverless/serverless/pull/9641)) ([989cb82](https://github.com/serverless/serverless/commit/989cb82db313177a64e062cc800eb85ba501fab5)) ([Mariusz Nowak](https://github.com/medikoo))
  - Fix standalone detection (case of a fallback from standalone) ([#9641](https://github.com/serverless/serverless/pull/9641)) ([1681af4](https://github.com/serverless/serverless/commit/1681af4897eeec20c1d1af292f9bfde5b1e9ffc3)) ([Mariusz Nowak](https://github.com/medikoo))

### Maintenance Improvements

- **Config Schema:** Improve error message and documentation ([#9639](https://github.com/serverless/serverless/pull/9639)) ([a36247b](https://github.com/serverless/serverless/commit/a36247b7ac1212a27f5e8d671ba39ba4c7e4de18)) ([Mariusz Nowak](https://github.com/medikoo))
- Replace `fse.rename` with `fs.promises.rename` ([#9605](https://github.com/serverless/serverless/issues/9605)) ([e6ff228](https://github.com/serverless/serverless/commit/e6ff2286a55d8cb8f82e58d8173b0a386a4b1767)) ([Sudipto Das](https://github.com/sdas13))

## [2.48.0](https://github.com/serverless/serverless/compare/v2.47.0...v2.48.0) (2021-06-21)

### Features

- Introduce an opt-in "error" deprecation notification mode ([#9623](https://github.com/serverless/serverless/pull/9623)) ([c22a8b9](https://github.com/serverless/serverless/commit/c22a8b99f2f64a76c592e800a8cf698dbff75b9c)) ([Mariusz Nowak](https://github.com/medikoo))

### Bug Fixes

- **Packaging:** Do not report hashing deprecations for container lambdas ([#9623](https://github.com/serverless/serverless/pull/9623)) ([68c2a08](https://github.com/serverless/serverless/commit/68c2a084f91b58832bd5417efaaa3fd6a6178d53)) ([Mariusz Nowak](https://github.com/medikoo))
- Ensure to support deprecation settings at early stage of processing ([#9623](https://github.com/serverless/serverless/pull/9623))([011e0ce](https://github.com/serverless/serverless/commit/011e0ce45cec4b1273268fcab4f99e377fae092e)) ([Mariusz Nowak](https://github.com/medikoo))

### Maintenance Improvements

- **Telemetry:** Recognize `constructs` ([#9628](https://github.com/serverless/serverless/pull/9628)) ([9e10cea](https://github.com/serverless/serverless/commit/9e10ceaf81e8b9d13867937fedc9502a1ff4e320)) ([Piotr Grzesik](https://github.com/pgrzesik))
- Ensure early access to configuration in logDeprecation method ([#9623](https://github.com/serverless/serverless/pull/9623)) ([53b9762](https://github.com/serverless/serverless/commit/53b97621dccdef8f9f2e15e2f4f31045b46970e2)) ([Mariusz Nowak](https://github.com/medikoo))

## [2.47.0](https://github.com/serverless/serverless/compare/v2.46.0...v2.47.0) (2021-06-18)

### Features

- Deprecate Node.js v10 ([#9600](https://github.com/serverless/serverless/issues/9600)) ([e24fdc9](https://github.com/serverless/serverless/commit/e24fdc9f08f9849aad4136261695e44476484b0d)) ([Milind Vaidya](https://github.com/vaidyamilind))
- **AWS HTTP API:** Support `payload` version per function ([#9551](https://github.com/serverless/serverless/issues/9551)) ([87ce28e](https://github.com/serverless/serverless/commit/87ce28ee4ea0e975859b8d32be8f2edd824b4cda)) ([Nyambayar Turbat](https://github.com/nyamba))
- **AWS S3:** Support CloudFormation instrinsic functions at `functions[].events[].s3.bucket` property ([#9617](https://github.com/serverless/serverless/issues/9617)) ([42690a7](https://github.com/serverless/serverless/commit/42690a7352751581a8dbd44a4f776af17ab20da8)) ([Piotr Grzesik](https://github.com/pgrzesik))

### Bug Fixes

- **AWS Cognito:** Fix user pool premission resource logical id normalization ([#9592](https://github.com/serverless/serverless/issues/9592)) ([f4c9b58](https://github.com/serverless/serverless/commit/f4c9b58b10a45ae342934e9a61dcdea0c2ef11e2)) ([arunkc](https://github.com/Arun-kc))
- **AWS Invocation:** Fix resolution of options with non-AWS provider ([#9602](https://github.com/serverless/serverless/issues/9602)) ([54da80e](https://github.com/serverless/serverless/commit/54da80e26497b8f1dbcd3027775628d11e1c6814)) ([Corentin Doue](https://github.com/CorentinDoue))
- **Variables:** Ensure to strip unrecognized legacy `ssm` resolver instructions ([#9601](https://github.com/serverless/serverless/issues/9601)) ([f61859f](https://github.com/serverless/serverless/commit/f61859fd25908b13b6d9638c550e88ef4a08392e)) ([Mariusz Nowak](https://github.com/medikoo))

### Maintenance Improvements

- **Variables:** Improve error message ([#9601](https://github.com/serverless/serverless/issues/9601)) ([4a732e2](https://github.com/serverless/serverless/commit/4a732e2ebf6c7d81f5e0fbdc2e9bcb4715e4cadf)) ([Mariusz Nowak](https://github.com/medikoo))

### [2.46.0](https://github.com/serverless/serverless/compare/v2.45.2...v2.46.0) (2021-06-11)

### Features

- **CLI Onboarding:** Make it service setup specific, remove `auto-update` step ([#9582](https://github.com/serverless/serverless/pull/9582)) ([519f77e](https://github.com/serverless/serverless/commit/519f77e1a876cea62843a99e58bab1e011e62fa3)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **Config Schema:** Improve error messaging for same type variants ([#9588](https://github.com/serverless/serverless/pull/9588)) ([8ac249b](https://github.com/serverless/serverless/commit/8ac249b1eadf3173359e02886e71bb89234ebd51)) ([Mariusz Nowak](https://github.com/medikoo))
- Show information on how to turn on auto updates in postinstall step ([#9582](https://github.com/serverless/serverless/pull/9582)) ([93c88c0](https://github.com/serverless/serverless/commit/93c88c0b8d1eea6455ca6ecb9a022f814f8e79b3)) ([Piotr Grzesik](https://github.com/pgrzesik))

### Bug Fixes

- **Variables:**
  - Fix resolution visibility of top level properties (as `outputs`) ([#9591](https://github.com/serverless/serverless/pull/9591)) ([004c6e2](https://github.com/serverless/serverless/commit/004c6e26beec98fbfb757aab05f18a623a03cf76)) ([Mariusz Nowak](https://github.com/medikoo))
  - Improve required properties resolution validation order ([#9591](https://github.com/serverless/serverless/pull/9591)) ([727d7f4](https://github.com/serverless/serverless/commit/727d7f4f089051223db88ceb85a62adabf07dc9e)) ([Mariusz Nowak](https://github.com/medikoo))
  - Meaningfully report misuse of dashboard sources ([#9591](https://github.com/serverless/serverless/pull/9591)) ([cc09c62](https://github.com/serverless/serverless/commit/cc09c62301f15f89febc50120a7a398640935470)) ([Mariusz Nowak](https://github.com/medikoo))
  - Recognize `tenant` setting (while deprecated it's still recognized by plugin) ([#9591](https://github.com/serverless/serverless/pull/9591)) ([aa45876](https://github.com/serverless/serverless/commit/aa4587604476314485a8094bdae04e0148b9e53c)) ([Mariusz Nowak](https://github.com/medikoo))

### Maintenance Improvements

- Reorganize and document service configuration dependencies ([#9591](https://github.com/serverless/serverless/pull/9591)) ([c86a76c](https://github.com/serverless/serverless/commit/c86a76cb60038765404c988da13dfc6ffde28fe6)) ([Mariusz Nowak](https://github.com/medikoo))
- **Telemetry:** Optimise reported error location length:
  - Remove eventual `/node_modules` prefix ([#9587](https://github.com/serverless/serverless/pull/9587)) ([f3ff6d2](https://github.com/serverless/serverless/commit/f3ff6d21758b61116c748746cefe8c1a3d6ab776)) ([Mariusz Nowak](https://github.com/medikoo))
  - Replace repeated paths with `^` ([#9587](https://github.com/serverless/serverless/pull/9587)) ([f6a7d03](https://github.com/serverless/serverless/commit/f6a7d03b04bd13f91bc247e518a1ad12496ead8c)) ([Mariusz Nowak](https://github.com/medikoo))

### [2.45.2](https://github.com/serverless/serverless/compare/v2.45.1...v2.45.2) (2021-06-09)

### Bug Fixes

- **Variables:**
  - Skip unrecognized sources check with partial resolution ([#9579](https://github.com/serverless/serverless/pull/9579)) ([93b89fc](https://github.com/serverless/serverless/commit/93b89fcb51759d0fe938a40e7de76b6abd313efd)) ([Mariusz Nowak](https://github.com/medikoo))
  - Ensure to report only unrecognized sources ([#9579](https://github.com/serverless/serverless/pull/9579)) ([98701f3](https://github.com/serverless/serverless/commit/98701f367907aa4c0ed61de7c3aeb4a7b7eac174)) ([Mariusz Nowak](https://github.com/medikoo))

### [2.45.1](https://github.com/serverless/serverless/compare/v2.45.0...v2.45.1) (2021-06-08)

### Bug Fixes

- Fix `projectDir` pattern in config schema ([#9574](https://github.com/serverless/serverless/pull/9574)) ([8954b5f](https://github.com/serverless/serverless/commit/8954b5f9cc3e2431036ccb876c46fb8cc99dc0d9)) ([Mariusz Nowak](https://github.com/medikoo))

## [2.45.0](https://github.com/serverless/serverless/compare/v2.44.0...v2.45.0) (2021-06-08)

### Features

- **Variables:** Allow to reference files in scope of a project directory ([#9561](https://github.com/serverless/serverless/pull/9561)) ([8dbb56e](https://github.com/serverless/serverless/commit/8dbb56ecbda2c6b8e8eaccbba7c7842ba8382847)) ([Mariusz Nowak](https://github.com/medikoo))
- Introduce project directory setting, configurable via `projectDir` ([#9561](https://github.com/serverless/serverless/pull/9561)) ([d6e4b49](https://github.com/serverless/serverless/commit/d6e4b49ae28d5898d92b913a0d2c100bd29f4303)) ([Mariusz Nowak](https://github.com/medikoo))

### Bug Fixes

- **AWS API Gateway:** Don't create log group resource if access logs are disabled ([#9560](https://github.com/serverless/serverless/pull/9560)) ([a116dfe](https://github.com/serverless/serverless/commit/a116dfec22697dd0511623c6a1e6d2d829d4ba10)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **Templates:** Allow usage of `google-nodejs-typescript` template ([#9557](https://github.com/serverless/serverless/pull/9557)) ([accf5bd](https://github.com/serverless/serverless/commit/accf5bd082400f654eba5e7d322bcb205c9ae709)) ([Corentin Doue](https://github.com/CorentinDoue))

### Maintenance Improvements

- Upgrade `dotenv` to v10 ([#9569](https://github.com/serverless/serverless/pull/9569)) ([99d1697](https://github.com/serverless/serverless/commit/99d1697050ac2b2ca675794501c08230f2cc3f7b)) ([Mariusz Nowak](https://github.com/medikoo))

## [2.44.0](https://github.com/serverless/serverless/compare/v2.43.1...v2.44.0) (2021-06-02)

### Features

- **CLI Onboarding:** Make it service setup specific:
  - If not in service context, immediately go into project setup questions (skip "Do you want to create a new project" question) ([#9524](https://github.com/serverless/serverless/pull/9524)) ([d5e2baf](https://github.com/serverless/serverless/commit/d5e2baf714958c5718610659887f485f9bd161e4)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Remove `tab-completion` from interactive flow ([#9531](https://github.com/serverless/serverless/pull/9531)) ([3bac0f3](https://github.com/serverless/serverless/commit/3bac0f37f0f23abed387f0952772e3cdf5d47320)) ([Piotr Grzesik](https://github.com/pgrzesik))

### Bug Fixes

- **Variables:**
  - Unify error messaging for function resolvers ([#9545](https://github.com/serverless/serverless/pull/9545)) ([bb3b766](https://github.com/serverless/serverless/commit/bb3b766946311848c707abc0fc7e749393f4527c)) ([Mariusz Nowak](https://github.com/medikoo))
  - Ensure to apply a resolution with a new resolver in case of a fallback to a local version ([#9544](https://github.com/serverless/serverless/pull/9544)) ([14a5275](https://github.com/serverless/serverless/commit/14a5275c0d6a127e211935b8b8f57a949e1ffad6)) ([Mariusz Nowak](https://github.com/medikoo))
- **CLI:**
  - Ensure to gently handle missing data from global installation in case of local fallback ([#9539](https://github.com/serverless/serverless/pull/9539)) ([1b90dfb](https://github.com/serverless/serverless/commit/1b90dfb0659dab3852ace330fd7c497321b80710)) ([Mariusz Nowak](https://github.com/medikoo))
- Fix handling of numeric error codes coming from AWS SDK requests ([#9538](https://github.com/serverless/serverless/pull/9538)) ([f2cdbae](https://github.com/serverless/serverless/commit/f2cdbae1eb6d327935336a38deda099b8f5ffee2)) ([Mariusz Nowak](https://github.com/medikoo))

### Maintenance Improvements

- **Variables:**
  - Cleanup handling of `variableSyntax` default ([#9544](https://github.com/serverless/serverless/pull/9544)) ([582d150](https://github.com/serverless/serverless/commit/582d150ceb01d3f597a30fcc82201ffa325c4617)) ([Mariusz Nowak](https://github.com/medikoo))
  - Seclude resolution of sources from external plugins ([#9544](https://github.com/serverless/serverless/pull/9544)) ([6efc161](https://github.com/serverless/serverless/commit/6efc161e5f7892275c798f6003ea5ee557bf3b26)) ([Mariusz Nowak](https://github.com/medikoo))

### [2.43.1](https://github.com/serverless/serverless/compare/v2.43.0...v2.43.1) (2021-05-25)

### Bug Fixes

- **AWS Local Invocation:** Fix invalid result handling ([#9507](https://github.com/serverless/serverless/pull/9507)) ([bbff029](https://github.com/serverless/serverless/commit/bbff0290db8a56cf599522c5ec0abc901359a0f9)) ([Mariusz Nowak](https://github.com/medikoo))
- **Telemetry:** Ensure to pass proper config for local fallback error handler ([#9519](https://github.com/serverless/serverless/pull/9519)) ([9b2a111](https://github.com/serverless/serverless/commit/9b2a1114850914a4ac96b19c7fcb0bf031822ea4)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **Variables:** Ensure proper resolution of AWS-related variables in case of errors ([#9518](https://github.com/serverless/serverless/pull/9518)) ([ee66585](https://github.com/serverless/serverless/commit/ee66585fdcfc32d135ed0cdc6bad8d440c7e9e38)) ([Piotr Grzesik](https://github.com/pgrzesik))

### Maintenance Improvements

- Use `download` from `@serverless/utils` ([#9513](https://github.com/serverless/serverless/pull/9513)) ([716b312](https://github.com/serverless/serverless/commit/716b31216e4873bbb986c5a2a54fda708a591cd1)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **CLI Onboarding:** Use "Starter" not "Empty" for templates ([#9514](https://github.com/serverless/serverless/pull/9514)) ([2984adb](https://github.com/serverless/serverless/commit/2984adb0456f7d6e93b0c778a1c588ee20459928)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **Telemetry:** Improve AWS stack error codes ([#9510](https://github.com/serverless/serverless/issues/9510)) ([c265905](https://github.com/serverless/serverless/commit/c265905f518f8cbea170c5a2774670c60de0e36c)) ([Mariusz Nowak](https://github.com/medikoo))

## [2.43.0](https://github.com/serverless/serverless/compare/v2.42.0...v2.43.0) (2021-05-20)

### Features

- **CLI Onboarding:** In `service` step, if possible propose a default project name ([#9503](https://github.com/serverless/serverless/pull/9503)) ([dee54ed](https://github.com/serverless/serverless/commit/dee54ed55c0a0697eefdde99d5ec8aee321ce041)) ([Piotr Grzesik](https://github.com/pgrzesik))

### Bug Fixes

- **AWS Deploy:** Fix stack errors processing ([#9505](https://github.com/serverless/serverless/pull/9505)) ([18a9b2b](https://github.com/serverless/serverless/commit/18a9b2b6f5734083de751cf182c6be61736be11f)) ([Mariusz Nowak](https://github.com/medikoo))
- **AWS IAM:** Do not depend on default execution role when custom role provided ([29f0e9c](https://github.com/serverless/serverless/commit/29f0e9c840e4b1ae9949925bc5a2a9d2de742271)) ([Piotr Grzesik](https://github.com/pgrzesik))

### Maintenance Improvements

- Do not recognize YAML Exception as user error ([#9505](https://github.com/serverless/serverless/pull/9505)) ([db16df2](https://github.com/serverless/serverless/commit/db16df2faad9cc63eb8e98ce90829642707546fb)) ([Mariusz Nowak](https://github.com/medikoo))
- Do not rely on `serverless.yamlParser` ([#9505](https://github.com/serverless/serverless/pull/9505)) ([aa8f7be](https://github.com/serverless/serverless/commit/aa8f7bec1caed4211adcb87ad0a73cd796f065d5)) ([Mariusz Nowak](https://github.com/medikoo))
- Ensure codes for user errors ([#9505](https://github.com/serverless/serverless/pull/9505)) ([6adaa9f](https://github.com/serverless/serverless/commit/6adaa9f56ed6e9708065767be602f484d0091679)) ([Mariusz Nowak](https://github.com/medikoo))

## [2.42.0](https://github.com/serverless/serverless/compare/v2.41.2...v2.42.0) (2021-05-19)

### Features

- **CLI Onboarding:**
  - Switch to templates hosted at [`serverless/examples`](https://github.com/serverless/examples/) ([#9484](https://github.com/serverless/serverless/pull/9484)) ([e4ea50d](https://github.com/serverless/serverless/commit/e4ea50d401628cb22612196b7e9b50c4344dab8a)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Support `--name` CLI option for `service` step ([#9471](https://github.com/serverless/serverless/pull/9471)) ([53575dc](https://github.com/serverless/serverless/commit/53575dc36017ded5ff60e5edf18fb7a9fd9d30e9)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Support `template-path` CLI option for `service` step ([#9471](https://github.com/serverless/serverless/pull/9471)) ([98c9700](https://github.com/serverless/serverless/commit/98c9700bcda328552f04116a51549f66e3d7b026)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Support `template` and `template-url` options for `service` step ([#9495](https://github.com/serverless/serverless/pull/9495)) ([f1a288c](https://github.com/serverless/serverless/commit/f1a288ce2c30e1377d8b411a90db3b1b2857d4fb)) ([Piotr Grzesik](https://github.com/pgrzesik))

### Bug Fixes

- **AWS API Gateway:** Fix schema for `apiKeys` and `permissionsBoundary` ([#9489](https://github.com/serverless/serverless/pull/9489)) ([5601025](https://github.com/serverless/serverless/commit/5601025dd8a4075cb463e2dcfb67d6c52984582a)) ([lyndoh](https://github.com/lyndoh))
- **AWS Local Invocation:** Report invalid handler path meaningfully ([#9499](https://github.com/serverless/serverless/pull/9499)) ([a2297ee](https://github.com/serverless/serverless/commit/a2297ee916dd79463d4efcfd6f7fe1f8e0e50d87)) ([Mariusz Nowak](https://github.com/medikoo))
- **Variables:**
  - Fix reporting of variable resolution errors trigger by variable resolution made in JS function resolvers ([#9482](https://github.com/serverless/serverless/pull/9482)) ([f6b7cfa](https://github.com/serverless/serverless/commit/f6b7cfaaaff81b84011f0f6168a651979089e1c9)) ([Mariusz Nowak](https://github.com/medikoo))
  - Ensure report user error as user error ([#9499](https://github.com/serverless/serverless/pull/9499)) ([a8f4aeb](https://github.com/serverless/serverless/commit/a8f4aebe5d482a491d86d3427b259db00674cc72)) ([Mariusz Nowak](https://github.com/medikoo))
- Expose remote lambda invocation failure as user error (([#9499](https://github.com/serverless/serverless/pull/9499)) [8f3d4e4](https://github.com/serverless/serverless/commit/8f3d4e4bdb1df1e107c5113d013164a2396f0f64)) ([Mariusz Nowak](https://github.com/medikoo))
- Expose template error with user error ([#9499](https://github.com/serverless/serverless/pull/9499)) ([07b60a6](https://github.com/serverless/serverless/commit/07b60a6bb42796e6f060730ce4bf22762942b0b8)) ([Mariusz Nowak](https://github.com/medikoo))
- Construct user errors with `ServerlessError` ([#9499](https://github.com/serverless/serverless/pull/9499)) ([c563581](https://github.com/serverless/serverless/commit/c563581ac98764edf653c1a5337d1b7d2b61ea63)) ([Mariusz Nowak](https://github.com/medikoo))
- Do not stumble on missing resource properties ([#9499](https://github.com/serverless/serverless/pull/9499)) ([f87aee2](https://github.com/serverless/serverless/commit/f87aee268dd19f9b90a7018032c77454d2084f12)) ([Mariusz Nowak](https://github.com/medikoo))

### Maintenance Improvements

- **Telemetry:**
  - Report resource types for user configured resources at `resources.Resources` ([#9501](https://github.com/serverless/serverless/pull/9501)) ([8d0ff07](https://github.com/serverless/serverless/commit/8d0ff078f7f0b565c1d35af1319f76a407afeb4b)) ([Mariusz Nowak](https://github.com/medikoo))
  - Normalize AWS request error codes ([#9499](https://github.com/serverless/serverless/pull/9499)) ([5a23931](https://github.com/serverless/serverless/commit/5a23931734ee80b80182008197c92985975f1646)) ([Mariusz Nowak](https://github.com/medikoo))
  - Report error location for non-normative error codes ([#9499](https://github.com/serverless/serverless/pull/9499)) ([07d5b9c](https://github.com/serverless/serverless/commit/07d5b9c19e9f5365af322a4862b03ccdca05655c)) ([Mariusz Nowak](https://github.com/medikoo))
  - Remove dead path error handling ([#9499](https://github.com/serverless/serverless/pull/9499)) ([91b10ed](https://github.com/serverless/serverless/commit/91b10ed208f2dee4b690df633f4275f658355044)) ([Mariusz Nowak](https://github.com/medikoo))
  - Improve granularity of stack deployment error codes ([#9499](https://github.com/serverless/serverless/pull/9499)) ([a6f4dc3](https://github.com/serverless/serverless/commit/a6f4dc3b2be2aa9ba2255d57cf9a9d23eae02994)) ([Mariusz Nowak](https://github.com/medikoo))
- **CLI Onboarding:** Add `history` and `stepHistory` to `context` ([#9481](https://github.com/serverless/serverless/pull/9481)) ([9eea885](https://github.com/serverless/serverless/commit/9eea885b390fc88bb62c1e2a5c3d108444139703)) ([Piotr Grzesik](https://github.com/pgrzesik))
- Add `create-from-local-template` util ([#9471](https://github.com/serverless/serverless/pull/9471)) ([03011ba](https://github.com/serverless/serverless/commit/03011baf07d262a5b9702b34b75a997e3f525d28)) ([Piotr Grzesik](https://github.com/pgrzesik))
- Ensure to propagate as is stack monitoring error ([#9499](https://github.com/serverless/serverless/pull/9499)) ([a46abe3](https://github.com/serverless/serverless/commit/a46abe3d56cd667ad436fbceb283dd9e0f747d7b)) ([Mariusz Nowak](https://github.com/medikoo))

## [2.41.2](https://github.com/serverless/serverless/compare/v2.41.1...v2.41.2) (2021-05-13)

### Bug Fixes

- **CLI:**
  - In error handler fallback to local version only if we're not in its context (fix infinite recursion issue which put `serverless` process on stall) ([#9472](https://github.com/serverless/serverless/pull/9472)) ([7047c34](https://github.com/serverless/serverless/commit/7047c349299ea829b0d43efedd191782dad10219)) ([Mariusz Nowak](https://github.com/medikoo))
  - Ensure resolved CLI params are correct in local fallback ([#9472](https://github.com/serverless/serverless/pull/9472)) ([65a1f38](https://github.com/serverless/serverless/commit/65a1f3875cda7f06d3ab47f21362a630d7d0415f)) ([Mariusz Nowak](https://github.com/medikoo))
- **Telemetry:** If global & local fallback versions are recent enough to report outcome, report with global ([#9472](https://github.com/serverless/serverless/pull/9472)) ([eeddf9f](https://github.com/serverless/serverless/commit/eeddf9f518612f6f7ef805eb3ed9b13fb3036114)) ([Mariusz Nowak](https://github.com/medikoo))

### Templates

- **Templates:** Add `google-nodejs-typescript` template ([#9445](https://github.com/serverless/serverless/issues/9445)) ([9cc05ad](https://github.com/serverless/serverless/commit/9cc05ad2f659709746d1df9811b95118c583db27)) ([Corentin Doue](https://github.com/CorentinDoue))

### Maintenance Improvements

- **CLI Onboarding:**
  - Seclude from internal Framework logic ([#9410](https://github.com/serverless/serverless/pull/9410)) ([7864f4d](https://github.com/serverless/serverless/commit/7864f4d28d4c4ed8325e64c8dfca891845edf392)) ([Mariusz Nowak](https://github.com/medikoo))
  - Integrate steps from dashboard plugin ([#9410](https://github.com/serverless/serverless/pull/9410)) ([105807a](https://github.com/serverless/serverless/commit/105807a674820f2d8501f3b8539c3725fceab215)) ([Mariusz Nowak](https://github.com/medikoo))
  - Refactor to async/await ([#9410](https://github.com/serverless/serverless/pull/9410)) ([1060d14](https://github.com/serverless/serverless/commit/1060d1468ba587519df482e95a54bbc8d199cad8)) ([Mariusz Nowak](https://github.com/medikoo))
  - Simplify tabcompletion support check ([#9410](https://github.com/serverless/serverless/pull/9410)) ([c13586e](https://github.com/serverless/serverless/commit/c13586ee23614da75d71f40ff24037b9aad46c2c)) ([Mariusz Nowak](https://github.com/medikoo))
- **Telemetry:** Make `generatePayload` `serverless` independent ([#9410](https://github.com/serverless/serverless/pull/9410)) ([4f6a50a](https://github.com/serverless/serverless/commit/4f6a50a2e145e664405b00661d801b6ad094f418)) ([Mariusz Nowak](https://github.com/medikoo))
- **CLI:** Rely internally on `@serverless/utils/log` ([#9410](https://github.com/serverless/serverless/pull/9410)) ([05588f7](https://github.com/serverless/serverless/commit/05588f77c0bbc900198ce458099ea2db066f3601)) ([Mariusz Nowak](https://github.com/medikoo))
- Refactor `isNpmPackageWritable` to not depend on `serverless` ([b915cc4](https://github.com/serverless/serverless/commit/b915cc467183d146785466965abbe318c349f0c9)) ([Mariusz Nowak](https://github.com/medikoo))

### [2.41.1](https://github.com/serverless/serverless/compare/v2.41.0...v2.41.1) (2021-05-11)

### Bug Fixes

- **CLI:** Correctly resolve version during local fallback ([#9463](https://github.com/serverless/serverless/pull/9463)) ([bbfe742](https://github.com/serverless/serverless/commit/bbfe742b2458f31254b11128b8ed506a47293abe)) ([Piotr Grzesik](https://github.com/pgrzesik))

## [2.41.0](https://github.com/serverless/serverless/compare/v2.40.0...v2.41.0) (2021-05-11)

### Features

- **AWS API Gateway:** Support disabling default endpoint ([#9404](https://github.com/serverless/serverless/issues/9404)) ([ec90945](https://github.com/serverless/serverless/commit/ec909452b5167e05d892d2c44bc46b4ff7d7470a)) ([lyndoh](https://github.com/lyndoh))
- **AWS Lambda:** Deprecate `nodejs12.x` as default runtime ([#9416](https://github.com/serverless/serverless/issues/9416)) ([9e558ee](https://github.com/serverless/serverless/commit/9e558eefd66e9dafcb16b3636b934d753ade001e)) ([Jaakko Lappalainen](https://github.com/jkklapp))

### Bug Fixes

- **AWS API Gateway:** Support `Fn::Split` for `vpcEndpointIds` schema ([#9455](https://github.com/serverless/serverless/pull/9455)) ([56f8587](https://github.com/serverless/serverless/commit/56f85874c6b9da44b8fbc326dfe3bce33bf8c41e)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **AWS Lambda:** Ensure that docker image is build and pushed only once ([#9446](https://github.com/serverless/serverless/pull/9446)) ([277f4e8](https://github.com/serverless/serverless/commit/277f4e8e9c53c0572981407eb45cecba050462a7)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **CLI:**
  - Ensure to report only unrecognized sources as unrecognized ([#9449](https://github.com/serverless/serverless/pull/9449)) ([27e21e8](https://github.com/serverless/serverless/commit/27e21e8fca560732df3fa5c36c56682ef89b53c5)) ([Mariusz Nowak](https://github.com/medikoo))
  - Fix local installation fallback ([#9454](https://github.com/serverless/serverless/pull/9454)) ([fa8c076](https://github.com/serverless/serverless/commit/fa8c076c564377ec632992a6a156bc4937ec08e1)) ([Mariusz Nowak](https://github.com/medikoo))
- **Packaging:** Fix support of the artifact S3 uri with region ([#9411](https://github.com/serverless/serverless/issues/9411)) ([40e56fc](https://github.com/serverless/serverless/commit/40e56fc0e9f71f06068d7d4c30178db8b2260357)) ([Zach Whaley](https://github.com/zachwhaley))

### Maintenance Improvements

- **Telemetry:**
  - Ensure telemetry only matches js stacktrace paths ([#9447](https://github.com/serverless/serverless/pull/9447)) ([7361e04](https://github.com/serverless/serverless/commit/7361e049608d40e4199c797abbad552ea831f5a5)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - For local fallback ensure to report locally used version ([#9454](https://github.com/serverless/serverless/pull/9454)) ([096ed96](https://github.com/serverless/serverless/commit/096ed9652bff399965c81c9aedb93b42c2b8caf5)) ([Mariusz Nowak](https://github.com/medikoo))
  - Let old versions report telemetry old way ([#9454](https://github.com/serverless/serverless/pull/9454)) ([4d077d1](https://github.com/serverless/serverless/commit/4d077d1653fcc41e362587e5d13dfa8dd43d3bc3)) ([Mariusz Nowak](https://github.com/medikoo))

## [2.40.0](https://github.com/serverless/serverless/compare/v2.39.2...v2.40.0) (2021-05-06)

### Features

- **AWS Lambda:** Add `ecr.scanOnPush` configuration option ([#9379](https://github.com/serverless/serverless/issues/9379)) ([078ec59](https://github.com/serverless/serverless/commit/078ec59058e1c37bd81388c7e81087b48fc2ba24)) ([Nicholas Wehr](https://github.com/wwwehr))

### Bug Fixes

- **CLI:** Do not validate command when falling back to old version ([#9437](https://github.com/serverless/serverless/pull/9437)) ([9624338](https://github.com/serverless/serverless/commit/962433864ff4f52bf178b7afc1b6e54e58e58702)) ([Mariusz Nowak](https://github.com/medikoo))

### [2.39.2](https://github.com/serverless/serverless/compare/v2.39.1...v2.39.2) (2021-05-04)

### Bug Fixes

- **CLI:**
  - Fix internal command resolution in case of a fallback to local version from older global version ([#9429](https://github.com/serverless/serverless/pull/9429)) ([b7a113d](https://github.com/serverless/serverless/commit/b7a113d48d634f89a91a31cd05b8d2e57f540c77)) ([Mariusz Nowak](https://github.com/medikoo))
  - Ensure to support `disableDeprecations` setting when validating not supported options ([#9429](https://github.com/serverless/serverless/pull/9429)) ([da476ad](https://github.com/serverless/serverless/commit/da476ad7ac52b331ae47102e01a9270a18b40833)) ([Mariusz Nowak](https://github.com/medikoo))
- **Telemetry:**
  - Do not attempt to report unrecognized commands ([#9427](https://github.com/serverless/serverless/pull/9427)) ([2c2c77f](https://github.com/serverless/serverless/commit/2c2c77f90518e73921b0f4dd02767b5ad4476db4)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Do not share telemetry cache folder with old versions ([#9429](https://github.com/serverless/serverless/pull/9429)) ([ae9442e](https://github.com/serverless/serverless/commit/ae9442e53b04648ff5b9c436ef86765d2ad9d872)) ([Mariusz Nowak](https://github.com/medikoo))
- **AWS Deploy:** Fix changes detection when VPC with intrinsic CF functions is involved ([#9425](https://github.com/serverless/serverless/pull/9425)) ([2c7f024](https://github.com/serverless/serverless/commit/2c7f024a57dd70c0e05d6ab7f40e530c96f2351a)) ([Piotr Grzesik](https://github.com/pgrzesik))
- Fix `provider.vpc` configuration schema ([#9425](https://github.com/serverless/serverless/pull/9)) ([7338358](https://github.com/serverless/serverless/commit/7338358126ac249374e341b7b19ce83582ecff1d)) ([Piotr Grzesik](https://github.com/pgrzesik))

### [2.39.1](https://github.com/serverless/serverless/compare/v2.39.0...v2.39.1) (2021-05-03)

### Bug Fixes

- **AWS HTTP API:** Ensure to apply tags to stage ([#9407](https://github.com/serverless/serverless/issues/9407)) ([80511a4](https://github.com/serverless/serverless/commit/80511a4b17e77e22cf8b20d1ce50eef7506d4f7f)) ([Filip Golonka](https://github.com/filipgolonka))

### Maintenance Improvements

- **Telemetry:**
  - Handle error locations not enclosed in parens ([#9419](https://github.com/serverless/serverless/pull/9419)) ([3ab0628](https://github.com/serverless/serverless/commit/3ab06282fdc9455f364fd73bd14761bae0c8d289)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Properly resolve location when for only relative paths ([#9418](https://github.com/serverless/serverless/issues/9418)) ([3ccf6a3](https://github.com/serverless/serverless/commit/3ccf6a3af3de093fabfa33a966b7a0a922712845)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Split stack lines properly on all OS-es ([#9419](https://github.com/serverless/serverless/pull/9419)) ([bdbf154](https://github.com/serverless/serverless/commit/bdbf154c97abde6ad2ff807dbea3ad1110ee5fec)) ([Piotr Grzesik](https://github.com/pgrzesik))

## [2.39.0](https://github.com/serverless/serverless/compare/v2.38.0...v2.39.0) (2021-04-30)

### Features

- **AWS IAM:** Support `provider.iam.role.path` ([#9363](https://github.com/serverless/serverless/issues/9363)) ([c8adc0c](https://github.com/serverless/serverless/commit/c8adc0c796a6558c3fe1bc86e3647d3fe711a9ad)) ([Android3000](https://github.com/Android3000))
- **Variables:** Expose variable resolver function to variable sources ([#9368](https://github.com/serverless/serverless/pull/9368)) ([2ff58b1](https://github.com/serverless/serverless/commit/2ff58b16bf3fe766685d5b6c30fd9a2bb6e22f0f)) ([Mariusz Nowak](https://github.com/medikoo))

### Bug Fixes

- **AWS API Gateway:** Ensure unique name for request validator ([#9382](https://github.com/serverless/serverless/pull/9382)) ([a05e88d](https://github.com/serverless/serverless/commit/a05e88d92e010ddfe019d5b5b873547b7d187d6d)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **AWS S3:** Fix parsing of the artifact S3 url ([#9380](https://github.com/serverless/serverless/issues/9380)) ([360925d](https://github.com/serverless/serverless/commit/360925d2e0cddb6fbbbb72ca47495aa71a43d1fc)) ([Stephen](https://github.com/bishtawi))
- **CLI:** Ensure no general help is listed under interactive setup help ([#9406](https://github.com/serverless/serverless/pull/9406)) ([132c830](https://github.com/serverless/serverless/commit/132c830b0a86998efbae1b4984dc9cea85957d61)) ([Mariusz Nowak](https://github.com/medikoo))

### Maintenance Improvements

- **Telemetry:**
  - Report failures via telemetry ([#9396](https://github.com/serverless/serverless/pull/9396)) ([5861d08](https://github.com/serverless/serverless/commit/5861d08768a06e2e88609d0785ce590d3f693683)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Ensure that container commands do not trigger telemetry ([#9397](https://github.com/serverless/serverless/pull/9397)) ([85b9e53](https://github.com/serverless/serverless/commit/85b9e5319df48904664f966e988cc725116ce865)) ([Mariusz Nowak](https://github.com/medikoo))
  - Add `commandDurationMs` to payload ([#9401](https://github.com/serverless/serverless/pull/9401)) ([d647125](https://github.com/serverless/serverless/commit/d647125ff5daa07972675fd28690d42746ab223b)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Add `commandOptionNames` to payload ([#9387](https://github.com/serverless/serverless/pull/9387)) ([f5b2b9b](https://github.com/serverless/serverless/commit/f5b2b9be395c9c2d3de4c4f91f991276bc22dc33)) ([Piotr Grzesik](https://github.com/pgrzesik))
- Ensure `code` to `ServerlessError` instances ([#9357](https://github.com/serverless/serverless/pull/9357)) ([822a7cf](https://github.com/serverless/serverless/commit/822a7cf9f527514b53fd8cfc5c172ec5dc53f4ce)) ([Piotr Grzesik](https://github.com/pgrzesik))

### Templates

- Update dependencies for `cloudflare` template ([#9373](https://github.com/serverless/serverless/issues/9373)) ([543423d](https://github.com/serverless/serverless/commit/543423d869ba35c6866506bb49a8642700214b3a)) ([YErii](https://github.com/YEriin))

## [2.38.0](https://github.com/serverless/serverless/compare/v2.37.2...v2.38.0) (2021-04-23)

### Features

- **AWS CloudFormation:** Add default export names to outputs ([#9313](https://github.com/serverless/serverless/issues/9313)) ([7e139bb](https://github.com/serverless/serverless/commit/7e139bb0136e0d053f4f6f8cb2876480bb2a485e)) ([Joseph Cha](https://github.com/js-cha))

### Bug Fixes

- **AWS API Gateway:** Create one request validator and reuse ([#9319](https://github.com/serverless/serverless/issues/9319)) ([154351f](https://github.com/serverless/serverless/commit/154351f1a5925a745873895014ed31f03b2842b3)) ([Jacques](https://github.com/gambit66))
- **Variables:** Fix unresolved sources notifications ([#9356](https://github.com/serverless/serverless/issues/9356)) ([53a7872](https://github.com/serverless/serverless/commit/53a7872f78f51938b409925e052d34f2dc85abbd)) ([Mariusz Nowak](https://github.com/medikoo))

### [2.37.2](https://github.com/serverless/serverless/compare/v2.37.1...v2.37.2) (2021-04-22)

### Bug Fixes

- **API:** Bring back legacy `service.serviceFilename` for plugins ([#9352](https://github.com/serverless/serverless/pull/9352)) ([6c896a5](https://github.com/serverless/serverless/commit/6c896a5ffdfc067ffded0791a34a943c89ea6136)) ([Mariusz Nowak](https://github.com/medikoo))

## [2.37.1](https://github.com/serverless/serverless/compare/v2.37.0...v2.37.1) (2021-04-21)

### Bug Fixes

- **API:** Ensure `config.servicePath` is `config.serviceDir` live alias ([#9343](https://github.com/serverless/serverless/pull/9343)) ([2967065](https://github.com/serverless/serverless/commit/2967065bc7e45d7b0f0fac4ad9b9c33b977482fa)) ([Mariusz Nowak](https://github.com/medikoo))

### Maintenance Improvements

- **Telemetry:** Allow to disable telemetry via `SLS_TELEMETRY_DISABLED` ([#9338](https://github.com/serverless/serverless/pull/9338)) ([ba7fd2e](https://github.com/serverless/serverless/commit/ba7fd2e1b428b2b76378aa90d0a19e8ec0d12498)) ([Piotr Grzesik](https://github.com/pgrzesik))

## [2.37.0](https://github.com/serverless/serverless/compare/v2.36.0...v2.37.0) (2021-04-20)

### Features

- **Variables:** `sls:stage` variable ([#9296](https://github.com/serverless/serverless/issues/9296)) ([ef91ae1](https://github.com/serverless/serverless/commit/ef91ae1972448fd342aeda6189884f2d8b454756)) ([Matthieu Napoli](https://github.com/mnapoli))

### Bug Fixes

- **API:** Ensure `serverless.config.servicePath` ([#9330](https://github.com/serverless/serverless/pull/9330)) ([ff589ba](https://github.com/serverless/serverless/commit/ff589baef483ecd53d9d4301bf2e846d87d62224)) ([Mariusz Nowak](https://github.com/medikoo))
- **CLI:** Ensure to recognize interactive CLI command properly ([#9332](https://github.com/serverless/serverless/pull/9332)) ([40fddcc](https://github.com/serverless/serverless/commit/40fddcc0eecee0c34310ac36508975fdd58da939)) ([Mariusz Nowak](https://github.com/medikoo))
- **Telemetry:** Do not send request when there are no events ([#9331](https://github.com/serverless/serverless/pull/9331)) ([f430224](https://github.com/serverless/serverless/commit/f4302249a9d9bfba46ca3fb6823cc8da27f20939)) ([Piotr Grzesik](https://github.com/pgrzesik))

## [2.36.0](https://github.com/serverless/serverless/compare/v2.35.0...v2.36.0) (2021-04-20)

### Features

- **AWS ALB:** Support `functions[].events[].alb.targetGroupName` ([#9222](https://github.com/serverless/serverless/issues/9222)) ([2cb8160](https://github.com/serverless/serverless/commit/2cb81608c8cb7dff7d6b9139235f2285b4b76044)) ([Gabriel Plassard](https://github.com/cbm-gplassard))
- Support `Fn::Split` for `vpc` properties ([#9266](https://github.com/serverless/serverless/issues/9266)) ([19805d7](https://github.com/serverless/serverless/commit/19805d71eabb68bd7fd4046aa23090ef85fb1c36)) ([Frédéric Barthelet](https://github.com/fredericbarthelet))

### Bug Fixes

- **AWS API Gateway:**
  - Correctly recognize `type` for `authorizerId` ([#9300](https://github.com/serverless/serverless/pull/9300)) ([ef25d68](https://github.com/serverless/serverless/commit/ef25d681372d1ef16cdba24981a41eb957e59821)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Deprecate invalid `apiGateway` settings ([#9238](https://github.com/serverless/serverless/issues/9238)) ([bca46e5](https://github.com/serverless/serverless/commit/bca46e5ab509065e6b3b2031446593ac23aac261)) ([Jaakko Lappalainen](https://github.com/jkklapp))
- **AWS IAM:** Deprecate `iam.role.permissionBoundary` in favor of `iam.role.permissionsBoundary` ([#9318](https://github.com/serverless/serverless/issues/9318)) ([d1c3b3f](https://github.com/serverless/serverless/commit/d1c3b3fbac0d2c80db7284d3ef4d8b808c33fa03)) ([Android3000](https://github.com/Android3000))
- **AWS Local Invocation:**
  - Allow optional `package.artifact` for `java` ([#9320](https://github.com/serverless/serverless/pull/9320)) ([924a698](https://github.com/serverless/serverless/commit/924a698d2a9d7a663c1fcbb11707ad8d2ed30b6b)) ([Yuji Yamano](https://github.com/yyamano))
  - Do not build Java bridge if `artifact` missing ([#9280](https://github.com/serverless/serverless/issues/9280)) ([5392a7d](https://github.com/serverless/serverless/commit/5392a7dce2a325d3f93d8e8508d63d16d93c6f51)) ([Yuji Yamano](https://github.com/yyamano))
- **CLI:**
  - Ensure to respect `disabledDeprecations` config options ([#9298](https://github.com/serverless/serverless/pull/9298)) ([05635c5](https://github.com/serverless/serverless/commit/05635c5e2df2f63710cac333fa6b2bab4e53c0c7)) ([Mariusz Nowak](https://github.com/medikoo))
  - Recognize `--aws-profile` option by schema ([#9324](https://github.com/serverless/serverless/pull/9324)) ([014ff94](https://github.com/serverless/serverless/commit/014ff949b7a8d62e246fd47f2addc48a37e362e2)) ([Mariusz Nowak](https://github.com/medikoo))
- **Plugins:** Prevent variables resolution with `plugin` command ([#9298](https://github.com/serverless/serverless/pull/9298)) ([8ac2706](https://github.com/serverless/serverless/commit/8ac27061999a0005d5aab342319cccfe6bbc9d49)) ([Mariusz Nowak](https://github.com/medikoo))
- **Variables:**
  - Clear escape slashes ([#9327](https://github.com/serverless/serverless/pull/9327)) ([c63244c](https://github.com/serverless/serverless/commit/c63244ce967c2c424fea50aaab9e19d355003913)) ([Mariusz Nowak](https://github.com/medikoo))
  - Fix file access error message generation ([#9281](https://github.com/serverless/serverless/pull/9281)) ([6dd3996](https://github.com/serverless/serverless/commit/6dd39968f2c49f3d98139994e320846b082b6005)) ([Mariusz Nowak](https://github.com/medikoo))

### Maintenance Improvements

- **AWS Credentials:** Remove undocumented `provider.credentials` ([#9287](https://github.com/serverless/serverless/pull/9287)) ([d26e2ae](https://github.com/serverless/serverless/commit/d26e2ae4b8db944bb6f9de55043b46285f08e726)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **CLI:** Validate service dependency in CLI context ([#9298](https://github.com/serverless/serverless/pull/9298)) ([088088c](https://github.com/serverless/serverless/commit/088088c1d345ff07e0b098f28d46f325b9e0b4cc)) ([Mariusz Nowak](https://github.com/medikoo))
- **Variables:**
  - Use `serviceDir` option as replacement for `servicePath` ([#9307](https://github.com/serverless/serverless/pull/9307)) ([712a569](https://github.com/serverless/serverless/commit/712a569d5258f7770d4c23d8f0803c3d0062b79e)) ([Mariusz Nowak](https://github.com/medikoo))
  - Testing purpose variable resolution util ([#9281](https://github.com/serverless/serverless/pull/9281)) ([a2f1808](https://github.com/serverless/serverless/commit/a2f1808b2f2a2cc7cb18a57ccc81c68e6a16dfc2)) ([Mariusz Nowak](https://github.com/medikoo))
- **Telemetry**:
  - Rename `analytics` to `telemetry` ([#9310](https://github.com/serverless/serverless/pull/9310)) ([d667111](https://github.com/serverless/serverless/commit/d66711108b1e69dd33259e43a0770e78631b9a8a)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Send all payloads with single request ([#9304](https://github.com/serverless/serverless/pull/9304)) ([278935d](https://github.com/serverless/serverless/commit/278935d3f504d040783d508b4f99a132715c751b)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Record all commands and send only on deploy ([#9323](https://github.com/serverless/serverless/pull/9323)) ([d3ecb7c](https://github.com/serverless/serverless/commit/d3ecb7cc3b95853b9ad7c1574a0c8fcbc6d08007)) ([Piotr Grzesik](https://github.com/pgrzesik))
- Introduce `serviceDir` and `configurationFilename` ([#9307](https://github.com/serverless/serverless/pull/9307)) ([fc3a439](https://github.com/serverless/serverless/commit/fc3a4391b5411f77a51a84f93a166903c51cb80f)) ([Mariusz Nowak](https://github.com/medikoo))
- Refactor constructor to accept new service configuration options ([#9307](https://github.com/serverless/serverless/pull/9307)) ([c02cd06](https://github.com/serverless/serverless/commit/c02cd06d907b7e54fb5a36ddbea8df1e4d29d897)) ([Mariusz Nowak](https://github.com/medikoo))
- Mark functions `async` in `plugins/aws/remove` ([#9284](https://github.com/serverless/serverless/issues/9284)) ([0bdb7d8](https://github.com/serverless/serverless/commit/0bdb7d858c238ffca3c1b1113cbb6af8c39a62e9)) ([Jaakko Lappalainen](https://github.com/jkklapp))
- Refactor `aws` provider tests for prefixes ([#9301](https://github.com/serverless/serverless/issues/9301)) ([196776c](https://github.com/serverless/serverless/commit/196776c65e3295e3e6e7bf341e000b8ea7ee76b5)) ([AlinoeDoctari](https://github.com/AlinoeDoctari))
- Remove `config.update` usage ([#9307](https://github.com/serverless/serverless/pull/9307)) ([7fb55b6](https://github.com/serverless/serverless/commit/7fb55b64ddd1bd727e48c2baf49f312fb12d03ab)) ([Mariusz Nowak](https://github.com/medikoo))
- Remove support for internal `noDeploy` option ([#9281](https://github.com/serverless/serverless/pull/9281)) ([688d09b](https://github.com/serverless/serverless/commit/688d09b1f7f28f8b1656d3f7f31c6c2765a01b9d)) ([Mariusz Nowak](https://github.com/medikoo))
- Rename `servicePath` vars to `serviceDir` ([#9307](https://github.com/serverless/serverless/pull/9307)) ([e8c8f1c](https://github.com/serverless/serverless/commit/e8c8f1cfff785017e8e0e55cf8fb81c2dd0040a9)) ([Mariusz Nowak](https://github.com/medikoo))
- Replace `config.servicePath` with `service.dir` ([#9307](https://github.com/serverless/serverless/pull/9307)) ([87d3802](https://github.com/serverless/serverless/commit/87d380275bc3102c71daa0f87e8211b90e5d58c4)) ([Mariusz Nowak](https://github.com/medikoo))

## [2.35.0](https://github.com/serverless/serverless/compare/v2.34.0...v2.35.0) (2021-04-09)

### Features

- **AWS Lambda:** Add support for `cacheFrom` to `images` ([#9251](https://github.com/serverless/serverless/issues/9251)) ([341a886](https://github.com/serverless/serverless/commit/341a886874eb8a6c671f576323e75a77cffa1fd2)) ([Nicholas Wehr](https://github.com/wwwehr))

### Bug Fixes

- **AWS API Gateway:**
  - Do not attempt to remove `aws:` tags during update ([#9265](https://github.com/serverless/serverless/pull/9265)) ([dac06c8](https://github.com/serverless/serverless/commit/dac06c8ce644f0d219329474cb83c644ca61d880)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Proper stage resolution for custom resource ([#9277](https://github.com/serverless/serverless/pull/9277)) ([50e4425](https://github.com/serverless/serverless/commit/50e44258835551523a089714396f12f6b229239c)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **AWS HTTP API:** Correctly accept `identitySource` as single CF intrinsic function value for HTTP API authorizers ([#9275](https://github.com/serverless/serverless/pull/9275)) ([fce73ad](https://github.com/serverless/serverless/commit/fce73ad4df0f776cf950733f9e88c3d390d6fc66)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **AWS Local Invocation:**
  - Adjust `.gitignore` ([#9274](https://github.com/serverless/serverless/issues/9274)) ([ce210f7](https://github.com/serverless/serverless/commit/ce210f785271bf0fb54685ed1ef84fb09ceaf05d)) ([Yuji Yamano](https://github.com/yyamano))
  - Correctly `decompress` artifact ([#9259](https://github.com/serverless/serverless/issues/9259)) ([af8d2a1](https://github.com/serverless/serverless/commit/af8d2a19269bf5480a6a87d91a17609f7f931eac)) ([Yuji Yamano](https://github.com/yyamano))
  - Strip `null` envvars for `invoke local` command ([#9263](https://github.com/serverless/serverless/issues/9263)) ([34d2c2f](https://github.com/serverless/serverless/commit/34d2c2feacc3a19c740cf78e6dbeb0b9a9ad5a74)) ([Yuji Yamano](https://github.com/yyamano))

## [2.34.0](https://github.com/serverless/serverless/compare/v2.33.1...v2.34.0) (2021-04-07)

### Features

- **AWS Lambda:** Add support for `buildArgs` to `images` ([#9198](https://github.com/serverless/serverless/issues/9198)) ([efd32d4](https://github.com/serverless/serverless/commit/efd32d4725cd36e5365aa09f50b75d9ca241d26e)) ([Nicholas Wehr](https://github.com/wwwehr))

### Bug Fixes

- **AWS Deploy:** Correctly identify "no updates" error during deploy ([#9248](https://github.com/serverless/serverless/pull/9248)) ([0e6a1ce](https://github.com/serverless/serverless/commit/0e6a1ce2d4a28a480683192cc6ac639c7bfe0d8b)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **CLI:** Ensure help output with missing `provider.name` ([#9235](https://github.com/serverless/serverless/pull/9235)) ([dae9058](https://github.com/serverless/serverless/commit/dae9058501ecc4ae8ff6b70e2bd1b22e914c241d)) ([Mariusz Nowak](https://github.com/medikoo))
- Avoid re-registration of `ts-node` ([#9254](https://github.com/serverless/serverless/issues/9254)) ([88baf06](https://github.com/serverless/serverless/commit/88baf06b42d4c08f3034965b8a7ffa23455ae3e3)) ([Adam Pancutt](https://github.com/apancutt))

### Maintenance Improvements

- **Analytics**: Account for functions with containers for analytics ([#9216](https://github.com/serverless/serverless/issues/9216)) ([c88a2ea](https://github.com/serverless/serverless/commit/c88a2ea61a2016982cd24050af8cac5989b07f79)) ([Piotr Grzesik](https://github.com/pgrzesik))

### [2.33.1](https://github.com/serverless/serverless/compare/v2.33.0...v2.33.1) (2021-04-03)

### Bug Fixes

- **Variables:** Ensure valid region value type in SSM resolution ([#9236](https://github.com/serverless/serverless/pull/9236)) ([83cac53](https://github.com/serverless/serverless/commit/83cac533a387a216dd6c151307a0dc69f36eef9e)) ([Mariusz Nowak](https://github.com/medikoo))

## [2.33.0](https://github.com/serverless/serverless/compare/v2.32.1...v2.33.0) (2021-04-02)

### Features

- **Plugins:** Announce "type" requirement in CLI option definitions ([#9230](https://github.com/serverless/serverless/pull/9230)) ([959da67](https://github.com/serverless/serverless/commit/959da67a5eb49f2256b4763f5f235537e6253659)) ([Mariusz Nowak](https://github.com/medikoo))

### Bug Fixes

- **CLI:** Do not assume "string" option type, when no type set in definition ([#9230](https://github.com/serverless/serverless/pull/9230)) ([c9be9bc](https://github.com/serverless/serverless/commit/c9be9bcc45d2da606d1660fb60156e56f5912e49)) ([Mariusz Nowak](https://github.com/medikoo))
- **Variables:** Support resolving "raw" JSON string form of SSM params ([#9229](https://github.com/serverless/serverless/pull/9229)) ([4eba512](https://github.com/serverless/serverless/commit/4eba512c1529a0d1d6c60e3f9de3bf98d6c23002)) ([Mariusz Nowak](https://github.com/medikoo))
- **Packaging:**
  - Ensure to apply dev dependency exclusion ([#92ee](https://github.com/serverless/serverless/pull/92ee)) ([7d16947](https://github.com/serverless/serverless/commit/7d16947273da079f4e844b4a62c98863206e848e)) ([Mariusz Nowak](https://github.com/medikoo))
  - Recognize `layers[].package.patterns` ([#9231](https://github.com/serverless/serverless/pull/9231)) ([9793c50](https://github.com/serverless/serverless/commit/9793c506ec364a4298a97e274c27c6f934749c74)) ([Mariusz Nowak](https://github.com/medikoo))
- **AWS CloudFront:** Recognize "?" character in `pathPattern` property ([#9234](https://github.com/serverless/serverless/pull/9234)) ([9d84596](https://github.com/serverless/serverless/commit/9d84596604a7338e82616723fe1a486c09272ae7)) ([Mariusz Nowak](https://github.com/medikoo))

### Maintenance Improvements

- Remove injustified "eslint-disable" comments ([#9232](https://github.com/serverless/serverless/pull/9232)) ([2011649](https://github.com/serverless/serverless/commit/20116495372ff5de837d005868cdd2a3d74e1415)) ([Mariusz Nowak](https://github.com/medikoo))

### [2.32.1](https://github.com/serverless/serverless/compare/v2.32.0...v2.32.1) (2021-03-31)

### Bug Fixes

- **AWS IAM:** Support for CF functions for `provider.iam.role` ([#9206](https://github.com/serverless/serverless/pull/9206)) ([0a84f1c](https://github.com/serverless/serverless/commit/0a84f1c84ee4e7ac32d9b5c247eba7f25da0d14a)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **CLI:** Fix `commands` pass to local installation ([#9207](https://github.com/serverless/serverless/pull/9207)) ([80bddce](https://github.com/serverless/serverless/commit/80bddce66729a82dde488a497e228cc42775a174)) ([Mariusz Nowak](https://github.com/medikoo))
- **Variables:** Ensure resolution of unrecognized CLI options ([#9211](https://github.com/serverless/serverless/pull/9211)) ([b5668d5](https://github.com/serverless/serverless/commit/b5668d5be04902437c82b2ccb049f93f82a87ec3)) ([Mariusz Nowak](https://github.com/medikoo))

### Maintenance Improvements

- **CLI:** Fix deprecation message typo ([#9209](https://github.com/serverless/serverless/pull/9209)) ([7f788d2](https://github.com/serverless/serverless/commit/7f788d29e5b7ba45b9a3648b0b645f17706ac4a4)) ([Mariusz Nowak](https://github.com/medikoo))
- **Variables:**
  - Do not run old resolver when not needed ([#9207](https://github.com/serverless/serverless/pull/9207)) ([7601e26](https://github.com/serverless/serverless/commit/7601e26360226e77c4c8d631227a248e7a81afc2)) ([Mariusz Nowak](https://github.com/medikoo))

## [2.32.0](https://github.com/serverless/serverless/compare/v2.31.0...v2.32.0) (2021-03-30)

### Features

- **AWS HTTP API:**
  - Add support for AWS IAM authorization ([#9195](https://github.com/serverless/serverless/pull/9195)) ([d3c6e43](https://github.com/serverless/serverless/commit/d3c6e4323b9a3345d71ec43e6ac3013c0ffa02b7)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Add support for custom Lambda authorizers ([#9192](https://github.com/serverless/serverless/pull/9192)) ([37d03b6](https://github.com/serverless/serverless/commit/37d03b6888788b2ee0b4a679de30ba94d25d7d53)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **AWS IAM:** Add support for `iam.role.name` definition ([#9166](https://github.com/serverless/serverless/issues/9166)) ([8c3e1be](https://github.com/serverless/serverless/commit/8c3e1be735120f5e49f6850259072c13e175b71f)) ([Sergii Kovalev](https://github.com/Enase))
- **AWS Lambda:** Do not require all `image` properties ([#9177](https://github.com/serverless/serverless/pull/9177)) ([14f5743](https://github.com/serverless/serverless/commit/14f57438467b5d5c9a3dc356ac4a8b0a6021657f)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **CLI:**
  - Validate command and options against resolved schema ([#9171](https://github.com/serverless/serverless/pull/9171)) ([2dacbcc](https://github.com/serverless/serverless/commit/2dacbcce8529378d94abc7a0b0d0039ecee4d790)) ([Mariusz Nowak](https://github.com/medikoo))
  - Recognize CLI command plugin extensions in new resolver ([#9171](https://github.com/serverless/serverless/pull/9171)) ([3422a12](https://github.com/serverless/serverless/commit/3422a121d787fa716f708051f0bfe97644a3c1aa)) ([Mariusz Nowak](https://github.com/medikoo))
- **Packaging:** Deprecate `include` & `exclude` in favor of `patterns` ([#8581](https://github.com/serverless/serverless/issues/8581)) ([e1678fb](https://github.com/serverless/serverless/commit/e1678fb1c65ab0246e60d44857466be6771f889d)) ([Juanjo Diaz](https://github.com/juanjodiaz))
- **Variables:**
  - Report errors on unresolved variables ([#9200](https://github.com/serverless/serverless/pull/9200)) ([f112e4b](https://github.com/serverless/serverless/commit/f112e4b91c140d915cee493b24b66f94b8033d3d)) ([Mariusz Nowak](https://github.com/medikoo))
  - Support source extensions from plugins for new resolver ([#9200](https://github.com/serverless/serverless/pull/9200)) ([ee76876](https://github.com/serverless/serverless/commit/ee7687672557125b68a300f0cb1f7d8ec1785ec4)) ([Mariusz Nowak](https://github.com/medikoo))

### Bug Fixes

- **CLI:**
  - Ensure to expose accurate `commandsSchema` in resolved input ([#9181](https://github.com/serverless/serverless/pull/9181)) ([01b135c](https://github.com/serverless/serverless/commit/01b135c69f731ec6841953491d310d06fd5740c0)) ([Mariusz Nowak](https://github.com/medikoo))
  - Fix `generate-event` and `test` commands schema visibility ([#9181](https://github.com/serverless/serverless/pull/9181)) ([ae645e7](https://github.com/serverless/serverless/commit/ae645e7e8ec165115cfb30fe24790a6741d858aa)) ([Mariusz Nowak](https://github.com/medikoo))
  - Fix handling of container commands ([#9181](https://github.com/serverless/serverless/pull/9181)) ([d9cf52b](https://github.com/serverless/serverless/commit/d9cf52b2c81d9332f7289ef046fa161137ee1d19)) ([Mariusz Nowak](https://github.com/medikoo))
  - Unconditionally crash on unrecognized command ([#9181](https://github.com/serverless/serverless/pull/9181)) ([f1af86a](https://github.com/serverless/serverless/commit/f1af86ab55b873e87a1d6bef2c0b02e133eba4a2)) ([Mariusz Nowak](https://github.com/medikoo))
  - Ensure to copy and not modify preset schemas ([#9181](https://github.com/serverless/serverless/pull/9181)) ([64684f2](https://github.com/serverless/serverless/commit/64684f2ed58e643726e4cea403b80af9844575ab)) ([Mariusz Nowak](https://github.com/medikoo))
- Ensure detection of external plugins is multi instance safe ([#9181](https://github.com/serverless/serverless/pull/9181)) ([0f35375](https://github.com/serverless/serverless/commit/0f353750f16b5befff243221e2c5e3c66376bcb0)) ([Mariusz Nowak](https://github.com/medikoo))

### Maintenance Improvements

- **CLI:**
  - Move to CLI logic required options validation ([#9181](https://github.com/serverless/serverless/pull/9181)) ([afad231](https://github.com/serverless/serverless/commit/afad2315a52785b0fff2408bb502698f176ff144)) ([Mariusz Nowak](https://github.com/medikoo))
  - Ensure resolved `provider.region` if dashboard used ([#9200](https://github.com/serverless/serverless/pull/9200)) ([af0242d](https://github.com/serverless/serverless/commit/af0242d716613777b2d03b418c9df39e984bb559)) ([Mariusz Nowak](https://github.com/medikoo))
  - Ensure to have up to date commands ([#9181](https://github.com/serverless/serverless/pull/9181)) ([8142515](https://github.com/serverless/serverless/commit/8142515bfc34fe88fc12f599aff6453217959ba5)) ([Mariusz Nowak](https://github.com/medikoo))
  - Generalize property resolution validation ([#9171](https://github.com/serverless/serverless/pull/9171)) ([59434af](https://github.com/serverless/serverless/commit/59434afd9519ed41bbb607f5bdb16b1158936798)) ([Mariusz Nowak](https://github.com/medikoo))
  - Improve command resolution handling ([#9200](https://github.com/serverless/serverless/pull/9200)) ([0065200](https://github.com/serverless/serverless/commit/00652005d44886c472c8ca6b0e77a5619e1601c0)) ([Mariusz Nowak](https://github.com/medikoo))
  - Improve validation of resolution state of core config ([#9171](https://github.com/serverless/serverless/pull/9171)) ([9e84423](https://github.com/serverless/serverless/commit/9e844234133d0b796bdeb2bdcce557da4ca996e3)) ([Mariusz Nowak](https://github.com/medikoo))
  - Move lifecycles definition to commands schema ([#9171](https://github.com/serverless/serverless/pull/9171)) ([2294a4b](https://github.com/serverless/serverless/commit/2294a4b4cb938ec34492bb5979da0677ff1d602f)) ([Mariusz Nowak](https://github.com/medikoo))
  - Move main help renderer out of internals ([#9181](https://github.com/serverless/serverless/pull/9181)) ([053fea1](https://github.com/serverless/serverless/commit/053fea18e0295507511881e59350207e60f142be)) ([Mariusz Nowak](https://github.com/medikoo))
  - Pass resolved commands options to local installation ([#9181](https://github.com/serverless/serverless/pull/9181)) ([2d4d05d](https://github.com/serverless/serverless/commit/2d4d05d425bc686c11b284354f5cc2ccead3814d)) ([Mariusz Nowak](https://github.com/medikoo))
  - Prevent superfluous vars resolution with help request ([#9181](https://github.com/serverless/serverless/pull/9181)) ([c2d4f83](https://github.com/serverless/serverless/commit/c2d4f834e5acccc022cd9769b6fe369b76ebdd4c)) ([Mariusz Nowak](https://github.com/medikoo))
  - Recalculate options only if external plugins were loaded ([#9181](https://github.com/serverless/serverless/pull/9181)) ([9aa026d](https://github.com/serverless/serverless/commit/9aa026d8f77020b466730fd16c908c5339943bee)) ([Mariusz Nowak](https://github.com/medikoo))
  - Seclude command help render from internals ([#9181](https://github.com/serverless/serverless/pull/9181)) ([aca3c0d](https://github.com/serverless/serverless/commit/aca3c0d57d563237aa1c1d8dfb3eccf809536e57)) ([Mariusz Nowak](https://github.com/medikoo))
  - Seclude command options render logic out of internals ([#9181](https://github.com/serverless/serverless/pull/9181)) ([41e921a](https://github.com/serverless/serverless/commit/41e921aa6fa74d07ce7d1757cc1101f09f3e7f47)) ([Mariusz Nowak](https://github.com/medikoo))
  - Seclude general help render logic from internals ([#9181](https://github.com/serverless/serverless/pull/9181)) ([87b1861](https://github.com/serverless/serverless/commit/87b186113a3b76c2b8065b3d97f7c8fa0c68984e)) ([Mariusz Nowak](https://github.com/medikoo))
  - Seclude interactive setup help render out of internals ([#9181](https://github.com/serverless/serverless/pull/9181)) ([2fd921d](https://github.com/serverless/serverless/commit/2fd921dbfc613f9064e069d00f1c5d11c8b86879)) ([Mariusz Nowak](https://github.com/medikoo))
- **Variables:**
  - Configure `cf` source in a new resolver ([#9200](https://github.com/serverless/serverless/pull/9200)) ([a60e90f](https://github.com/serverless/serverless/commit/a60e90f61c93c177ade8a2875e94feb7e886a0e2)) ([Mariusz Nowak](https://github.com/medikoo))
  - Configure `s3` source in a new resolver ([#9200](https://github.com/serverless/serverless/pull/9200)) ([12a4cad](https://github.com/serverless/serverless/commit/12a4cad102c67ecbdc308d35217a6247bd62dcb0)) ([Mariusz Nowak](https://github.com/medikoo))
  - Configure `sls` source in a new resolver ([#9200](https://github.com/serverless/serverless/pull/9200)) ([eecd928](https://github.com/serverless/serverless/commit/eecd9285d51506d9a245b47b9afa6a16ffd64fe0)) ([Mariusz Nowak](https://github.com/medikoo))
  - Configure `ssm` source in a new resolver ([#9200](https://github.com/serverless/serverless/pull/9200)) ([3f7f67c](https://github.com/serverless/serverless/commit/3f7f67ccc155d61ca9e7aa96c858058da55c635a)) ([Mariusz Nowak](https://github.com/medikoo))
  - Configure dashboard sources in a new resolver ([#9200](https://github.com/serverless/serverless/pull/9200)) ([385c15b](https://github.com/serverless/serverless/commit/385c15bc83ca34fdde2da61533a8b163f7bcc33c)) ([Mariusz Nowak](https://github.com/medikoo))
- **Dashboard:** Provide direct internal access to dashboard plugin ([#9200](https://github.com/serverless/serverless/pull/9200)) ([6292197](https://github.com/serverless/serverless/commit/6292197ee1dfbe107c3fe98059bd683896678b05)) ([Mariusz Nowak](https://github.com/medikoo))
- **Plugins:** Bulletproof way to recognize external plugins ([#9171](https://github.com/serverless/serverless/pull/9171)) ([1618e23](https://github.com/serverless/serverless/commit/1618e23c5cac32ee1168c951e5e70a8dfc66c2f9)) ([Mariusz Nowak](https://github.com/medikoo))
- **Analytics**: Detect Serverless CI/CD engine for analytics ([#9175](https://github.com/serverless/serverless/pull/9175)) ([e20766c](https://github.com/serverless/serverless/commit/e20766cf25e82442979662e0a415888f1727482a)) ([Piotr Grzesik](https://github.com/pgrzesik))

## [2.31.0](https://github.com/serverless/serverless/compare/v2.30.3...v2.31.0) (2021-03-23)

### Features

- **AWS API Gateway:** Remove deprecation for old naming convention ([#9160](https://github.com/serverless/serverless/pull/9160)) ([b530d6a](https://github.com/serverless/serverless/commit/b530d6a288a9881c12382c8004447b94a80f1847)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **Variables:**
  - Disallow `provider.variableSyntax` with new resolver ([#9140](https://github.com/serverless/serverless/pull/9140)) ([5a2da44](https://github.com/serverless/serverless/commit/5a2da444ea5f896f56cf03e509631d2df548457c)) ([Mariusz Nowak](https://github.com/medikoo))
  - Meaningfully reject not resolvable `provider.name` ([#9140](https://github.com/serverless/serverless/pull/9140)) ([f67d95a](https://github.com/serverless/serverless/commit/f67d95a553be8986b8b21c164f9d292f4fca21cd)) ([Mariusz Nowak](https://github.com/medikoo))

### Bug Fixes

- **Packaging:** Ensure to properly exclude dependencies when `NODE_ENV` set ([#9142](https://github.com/serverless/serverless/pull/9142)) ([6e3e21c](https://github.com/serverless/serverless/commit/6e3e21cafaa053a0f30239513eac5c7a725b7694)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **CLI:**
  - Recognize "--stage" as provider agnostic option ([#9151](https://github.com/serverless/serverless/pull/9151)) ([271ac82](https://github.com/serverless/serverless/commit/271ac8281c10e23ce609165582b3b996b60d5bd1)) ([Mariusz Nowak](https://github.com/medikoo))
  - Do not show options order deprecation info with help request ([#9151](https://github.com/serverless/serverless/pull/9151)) ([ad8f9b0](https://github.com/serverless/serverless/commit/ad8f9b059740bb2581445457b6751e918a57e585)) ([Mariusz Nowak](https://github.com/medikoo))
  - Recognize "--version" option in commands help ([#9151](https://github.com/serverless/serverless/pull/9151)) ([6cefe7a](https://github.com/serverless/serverless/commit/6cefe7a08452586498fe1612daf6f95f5a754925)) ([Mariusz Nowak](https://github.com/medikoo))
- **AWS Deploy:** Fix format of url data as passed to `https-proxy-agent` ([#9147](https://github.com/serverless/serverless/pull/9147)) ([d935dcc](https://github.com/serverless/serverless/commit/d935dccb268ff8e54d9f1fb56beee01115e041c1)) ([Andreas Augustin](https://github.com/AndreasAugustin))
- **Variables:**
  - Ensure necessary resolution interface for plugins ([#9164](https://github.com/serverless/serverless/pull/9164)) ([841e847](https://github.com/serverless/serverless/commit/841e847c20de989287e36a86c523763dc2b74e8b)) ([Mariusz Nowak](https://github.com/medikoo))
  - Ensure to support middle JS function resolved properties ([#9161](https://github.com/serverless/serverless/pull/9161)) ([32ba7c8](https://github.com/serverless/serverless/commit/32ba7c8b436ab49641fb89028e5b2e53226df3b5)) ([Mariusz Nowak](https://github.com/medikoo))
  - Fix resolution of "false" CLI params ([#9151](https://github.com/serverless/serverless/pull/9151)) ([6c6ada9](https://github.com/serverless/serverless/commit/6c6ada93e47e994dc5775a65542bedf69ec6d412)) ([Mariusz Nowak](https://github.com/medikoo))
  - Unify handling of not existing addresses ([#9161](https://github.com/serverless/serverless/pull/9161)) ([b21dc44](https://github.com/serverless/serverless/commit/b21dc44048cc1a96e2f772b9c412474b3a687067)) ([Mariusz Nowak](https://github.com/medikoo))
- Ensure to handle empty func definition with meaningful error ([#9133](https://github.com/serverless/serverless/pull/9133)) ([86e0b6d](https://github.com/serverless/serverless/commit/86e0b6ddbba7f356989ba7c1617c2a4160e7503a)) ([Piotr Grzesik](https://github.com/pgrzesik))

### Maintenance Improvements

- **CLI:**
  - Handle "help" with a schema ([#9151](https://github.com/serverless/serverless/pull/9151)) ([d455b23](https://github.com/serverless/serverless/commit/d455b236cf719778ebaa5048a0941ae906a69cd4)) ([Mariusz Nowak](https://github.com/medikoo))
  - Categorize CLI commands in schema ([#9140](https://github.com/serverless/serverless/pull/9140)) ([471e34d](https://github.com/serverless/serverless/commit/471e34ddc34962486e4bf78b33dbec566b561cf2)) ([Mariusz Nowak](https://github.com/medikoo))
  - Do not show deprecation with help command ([#9140](https://github.com/serverless/serverless/pull/9140)) ([a72b681](https://github.com/serverless/serverless/commit/a72b6816358a721f3957be40a35ae3d945eb80d1)) ([Mariusz Nowak](https://github.com/medikoo))
  - Do not throw errors when help command ([#9140](https://github.com/serverless/serverless/pull/9140)) ([d15efd9](https://github.com/serverless/serverless/commit/d15efd91087183b65201e2eaccbb9719f0b34e4e)) ([Mariusz Nowak](https://github.com/medikoo))
  - Expose resolved string command by `resolveInput` util ([#9151](https://github.com/serverless/serverless/pull/9151)) ([362f5e9](https://github.com/serverless/serverless/commit/362f5e94e044f51fe6e9b2f9de4de810fb9f8d04)) ([Mariusz Nowak](https://github.com/medikoo))
  - Improve flow documentation ([#9140](https://github.com/serverless/serverless/pull/9140)) ([851c9f4](https://github.com/serverless/serverless/commit/851c9f4d52a69c3ac0f15f5fb353ae9f7a554530)) ([Mariusz Nowak](https://github.com/medikoo))
  - Improve setup of resolution flow ([#9140](https://github.com/serverless/serverless/pull/9140)) ([ab1c673](https://github.com/serverless/serverless/commit/ab1c673bb2f7d4279d0406f355516d616e1f00c8)) ([Mariusz Nowak](https://github.com/medikoo))
  - Integrate `isHelpRequest` into `resolveInput` util ([#9140](https://github.com/serverless/serverless/pull/9140)) ([a481170](https://github.com/serverless/serverless/commit/a48117041c3993f5ba969329dd605f6a80efcbad)) ([Mariusz Nowak](https://github.com/medikoo))
  - Proritize `provider.name` validation ([#9151](https://github.com/serverless/serverless/pull/9151)) ([9ab04a6](https://github.com/serverless/serverless/commit/9ab04a674771e84ec302d7a7783b3b3c09889d26)) ([Mariusz Nowak](https://github.com/medikoo))
  - Recognize "--version" on command as help request ([#9151](https://github.com/serverless/serverless/pull/9151)) ([23f45a3](https://github.com/serverless/serverless/commit/23f45a34de244b5d7ead1e300cb0aa2cdd57a372)) ([Mariusz Nowak](https://github.com/medikoo))
  - Resolve command and options gradually ([#9151](https://github.com/serverless/serverless/pull/9151)) ([b6382fd](https://github.com/serverless/serverless/commit/b6382fdb7abcdf42098c57263799ea004bdb1481)) ([Mariusz Nowak](https://github.com/medikoo))
  - Return resolved `commandSchema` from `resolveInput` util ([#9151](https://github.com/serverless/serverless/pull/9151)) ([4364acc](https://github.com/serverless/serverless/commit/4364acca588919c0b3bf69eb0c1cb44a2009d0b4)) ([Mariusz Nowak](https://github.com/medikoo))
  - Wrap with function for better maintainance ([#9140](https://github.com/serverless/serverless/pull/9140)) ([ab055a3](https://github.com/serverless/serverless/commit/ab055a3390fb6d0f20c2bc87916ddb19c8d58d7f)) ([Mariusz Nowak](https://github.com/medikoo))
- **Variables:**
  - Ensure to not resolve any value with promise ([#9140](https://github.com/serverless/serverless/pull/9140)) ([54da2c2](https://github.com/serverless/serverless/commit/54da2c23a13aafb7342915419c9a21ffc3705b37)) ([Mariusz Nowak](https://github.com/medikoo))
  - Recognize only defined CLI options in resolver ([#9151](https://github.com/serverless/serverless/pull/9151)) ([13610cf](https://github.com/serverless/serverless/commit/13610cf0f0b89dc3061ae10254df291fc38c5e57)) ([Mariusz Nowak](https://github.com/medikoo))
  - Report immediatelly eventual syntax errors ([#9140](https://github.com/serverless/serverless/pull/9140)) ([ee01833](https://github.com/serverless/serverless/commit/ee01833df80db8bc751f8248f49944738606393f)) ([Mariusz Nowak](https://github.com/medikoo))
  - Smarter "is property resolved" validation ([#9151](https://github.com/serverless/serverless/pull/9151)) ([cfe83df](https://github.com/serverless/serverless/commit/cfe83df1747732532d77d4ed52320aac70892da9)) ([Mariusz Nowak](https://github.com/medikoo))
  - Smarter resolution phases ([#9140](https://github.com/serverless/serverless/pull/9140)) ([a537856](https://github.com/serverless/serverless/commit/a5378566516fd9cb1a9abdfc204c0a8c83841e4b)) ([Mariusz Nowak](https://github.com/medikoo))
  - For `--help` output resolve just needed properties ([#9140](https://github.com/serverless/serverless/pull/9140)) ([d851914](https://github.com/serverless/serverless/commit/d851914a44cc0f0a7bb6c4bf7dd2454b6f83189c)) ([Mariusz Nowak](https://github.com/medikoo))
- Improve AWS SDK errors reporting ([#9148](https://github.com/serverless/serverless/pull/9148)) ([89b813d](https://github.com/serverless/serverless/commit/89b813da51cedf80ca66ae4b4ad269edf8614ec0)) ([Mariusz Nowak](https://github.com/medikoo))

### [2.30.3](https://github.com/serverless/serverless/compare/v2.30.2...v2.30.3) (2021-03-16)

### Bug Fixes

- **CLI:** Recognize `--env` option for `sls invoke local` as multiple ([#9131](https://github.com/serverless/serverless/issues/9131)) ([a941e87](https://github.com/serverless/serverless/commit/a941e87cbfbd272f27fc6360c7a733b337e83f2d)) ([lewgordon](https://github.com/lewgordon))

### [2.30.2](https://github.com/serverless/serverless/compare/v2.30.1...v2.30.2) (2021-03-16)

### Bug Fixes

- **Plugins:** Bring back `provider.sdk` property, to not break plugins ([#9127](https://github.com/serverless/serverless/pull/9127)) ([3e983f3](https://github.com/serverless/serverless/commit/3e983f347a10601e5dc5b1e6c19ae2822c94f682)) ([Mariusz Nowak](https://github.com/medikoo))

### [2.30.1](https://github.com/serverless/serverless/compare/v2.30.0...v2.30.1) (2021-03-16)

### Bug Fixes

- **AWS Credentials:** Fix credentials resolution ([#9121](https://github.com/serverless/serverless/pull/9121) & [#9124](https://github.com/serverless/serverless/pull/9141)) ([6f8b5b4](https://github.com/serverless/serverless/commit/6f8b5b41ebfd173d33e2ad9717f8727cc0592915) & [41df6fb](https://github.com/serverless/serverless/commit/41df6fbee2705307ad7b44f614d70b5d801e0114)) ([Mariusz Nowak](https://github.com/medikoo))
- **AWS EventBridge:** Clarify CF functions support for `eventBus` ([5183620](https://github.com/serverless/serverless/commit/5183620e9e4795c3ab07d30e7386d9360a2d7eb7)) ([#9118](https://github.com/serverless/serverless/pull/9118)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **AWS Lambda:** Ensure correct schema for `vpc` definition ([#9120](https://github.com/serverless/serverless/pull/9120)) ([4cd629a](https://github.com/serverless/serverless/commit/4cd629ac44f5a1a1442d7245878df6b361a94973)) ([Piotr Grzesik](https://github.com/pgrzesik))

## [2.30.0](https://github.com/serverless/serverless/compare/v2.29.0...v2.30.0) (2021-03-16)

### Features

- **Config Schema:** Announce that crashing on error will become default ([#9066](https://github.com/serverless/serverless/pull/9066)) ([6537a5e](https://github.com/serverless/serverless/commit/6537a5e48dd4f6846f4ba41bb6c4542ea0c0117d)) ([yumei](https://github.com/yumeixox))

### Bug Fixes

- **AWS Deploy:** Fix `deploy function` command error handling ([#9102](https://github.com/serverless/serverless/pull/9102)) ([aa7b66a](https://github.com/serverless/serverless/commit/aa7b66a66c199c236bedfbc3b3aab39acb0eb6ad)) ([Mariusz Nowak](https://github.com/medikoo))
- **AWS IAM:**
  - Accept `arn:${AWS::Partition}` in function roles ([#9103](https://github.com/serverless/serverless/issues/9103)) ([e77a00d](https://github.com/serverless/serverless/commit/e77a00dfff734ccb74a7ca77ef92135c4f4dc06b)) ([coyoteecd](https://github.com/coyoteecd))
  - Allow `iam.role` to use `awsLambdaRole` definition ([#9094](https://github.com/serverless/serverless/issues/9094)) ([82bf35c](https://github.com/serverless/serverless/commit/82bf35c1b9abd81fe52cdc7fd57b63cab4cecc6e)) ([Yahia Kerim](https://github.com/yahiakr))
- **AWS Local Invocation:** Support `env` vars with `=` in value ([#9079](https://github.com/serverless/serverless/issues/9079)) ([ab8529c](https://github.com/serverless/serverless/commit/ab8529cb24d63edba798ea6fba3d783f256d3998)) ([terrybondy](https://github.com/terrybondy) & [lewgordon](https://github.com/lewgordon))
- **Variables:** Retry JS function resolvers on unresolved dependencies ([#9110](https://github.com/serverless/serverless/pull/9110)) ([68de8bd](https://github.com/serverless/serverless/commit/68de8bdeed0545e6868c72806340e96f90f808cf)) ([Mariusz Nowak](https://github.com/medikoo))
- **CLI:**
  - Improve handling of container commands ([#9111](https://github.com/serverless/serverless/pull/9111)) ([6ec463c](https://github.com/serverless/serverless/commit/6ec463cbe7f0bc6a7827a504175f2c3aae9bb8d6)) ([Mariusz Nowak](https://github.com/medikoo))
  - Output "Plugin: " prefix only for external plugin comands ([#9111](https://github.com/serverless/serverless/pull/9111)) ([acf720c](https://github.com/serverless/serverless/commit/acf720cdefd65508fc0e5183271cff03009b7441)) ([Mariusz Nowak](https://github.com/medikoo))
  - Properly report SDK version when handling errors ([#9097](https://github.com/serverless/serverless/pull/9097)) ([a79473d](https://github.com/serverless/serverless/commit/a79473d8b1dac5c4da1473dec4b02ba192e696ca)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Recognize `--stage` & `--region` on every AWS service command ([#9111](https://github.com/serverless/serverless/pull/9111)) ([bfde219](https://github.com/serverless/serverless/commit/bfde21907be3508350bf2487d2ef8bc69be695ad)) ([Mariusz Nowak](https://github.com/medikoo))

### Maintenance Improvements

- **AWS Deploy:** Minimize try/catch wrap ([#9102](https://github.com/serverless/serverless/pull/9102)) ([a7d2cf0](https://github.com/serverless/serverless/commit/a7d2cf060514618d9caf48a55dfd56f371f19ca6)) ([Mariusz Nowak](https://github.com/medikoo))
- **CLI:**
  - Add Dashboard specific options to commands schema ([#9111](https://github.com/serverless/serverless/pull/9111)) ([ed553a7](https://github.com/serverless/serverless/commit/ed553a75267de5399809f2e9c848c60537e41fe2)) ([Mariusz Nowak](https://github.com/medikoo))
  - Generalize handling of not supported commands ([#9111](https://github.com/serverless/serverless/pull/9111)) ([8b301dc](https://github.com/serverless/serverless/commit/8b301dce9c06f9ef463f9f3572a02d0de8d3539d)) ([Mariusz Nowak](https://github.com/medikoo))
  - Recognize interactive setup command in commands schema ([#9111](https://github.com/serverless/serverless/pull/9111)) ([b9afc14](https://github.com/serverless/serverless/commit/b9afc144bf0aea4e20d7996df5d8c52430f39b23)) ([Mariusz Nowak](https://github.com/medikoo))
  - Resolve commands and options by schema ([#9111](https://github.com/serverless/serverless/pull/9111)) ([fe663ea](https://github.com/serverless/serverless/commit/fe663ead50ff6925fb09207492a188f5f5bbda7e)) ([Mariusz Nowak](https://github.com/medikoo))
  - Seclude schema of core commands ([#9111](https://github.com/serverless/serverless/pull/9111)) ([14a2640](https://github.com/serverless/serverless/commit/14a2640bd9e65e357f606635a15ce0b07625b3aa)) ([Mariusz Nowak](https://github.com/medikoo))
  - Schema for `@serverless/enterprise-plugin` commands ([#9111](https://github.com/serverless/serverless/pull/9111)) ([116fe85](https://github.com/serverless/serverless/commit/116fe85fbeac0408be6c6f5761573d5af340e8f1)) ([Mariusz Nowak](https://github.com/medikoo))
- Refactor `pluginManager.invoke` to async/await ([#9111](https://github.com/serverless/serverless/pull/9111)) ([15b5a11](https://github.com/serverless/serverless/commit/15b5a11ecd7cf4b83442ca0df161d74c9bdbc8e2)) ([Mariusz Nowak](https://github.com/medikoo))
- Refactor `pluginManager.spawn` to async/await ([#9111](https://github.com/serverless/serverless/pull/9111)) ([87b8d01](https://github.com/serverless/serverless/commit/87b8d019c200caebbd0047e15b2e1e9f1faa988f)) ([Mariusz Nowak](https://github.com/medikoo))
- Extend `generatePayload` ([#9078](https://github.com/serverless/serverless/pull/9078)) ([f6292b2](https://github.com/serverless/serverless/commit/f6292b2d4912e04ff79b2565fd0a57ced47ca0c1)) ([Piotr Grzesik](https://github.com/pgrzesik))
- Seclude AWS request util from internals ([#8850](https://github.com/serverless/serverless/issues/8850)) ([5fb85d3](https://github.com/serverless/serverless/commit/5fb85d36c8ee965df691b8f2dfddeaab8315c77d)) ([AlinoeDoctari](https://github.com/AlinoeDoctari))

### Templates

- **Templates:** Fix runtime for `azure-nodejs-typescript` ([#9106](https://github.com/serverless/serverless/issues/9106)) ([3597f45](https://github.com/serverless/serverless/commit/3597f4539dce1d7185879e7e00e67c64c022de02)) ([Tony Papousek](https://github.com/tonypapousek))

## [2.29.0](https://github.com/serverless/serverless/compare/v2.28.7...v2.29.0) (2021-03-09)

### Features

- **AWS IAM:**
  - Allow `tags` parameter on lambda execution role ([#9039](https://github.com/serverless/serverless/issues/9039)) ([42a1cdb](https://github.com/serverless/serverless/commit/42a1cdb6f1b4ca90e9e7f43852672897cb9ec1f9)) ([Dmitry Shirokov](https://github.com/runk))
  - Accept `accountId` as IAM policy principal ([#9082](https://github.com/serverless/serverless/pull/9082)) ([0f631f7](https://github.com/serverless/serverless/commit/0f631f7bd17285c89bf73aa7da788186cebb2d05)) ([Sam Lyon](https://github.com/blue-urban-sky))
- **AWS Stream:** Add support for custom checkpoint ([#9056](https://github.com/serverless/serverless/issues/9056)) ([b2188a2](https://github.com/serverless/serverless/commit/b2188a20d935b2ae8fccf594c4bd39eddcb7ef8c)) ([Vishnu Prassad](https://github.com/imewish))

### Bug Fixes

- **AWS Deploy:** Warn when IAM policy does not allow to fetch lambda details ([#9041](https://github.com/serverless/serverless/issues/9041)) ([dea7b5a](https://github.com/serverless/serverless/commit/dea7b5a3c0b5b1208c44c0762566a0fdab298f83)) ([Tristan Rigaut](https://github.com/trigaut))
- **CLI:** Fix dashboard error handler error reporting ([#9084](https://github.com/serverless/serverless/pull/9084)) ([aa9dc0a](https://github.com/serverless/serverless/commit/aa9dc0a8dc46c8dcb51a88c62d6337b8cc68f2b0)) ([Mariusz Nowak](https://github.com/medikoo))
- **AWS IAM:** Support CF functions for managed policies ([#9089](https://github.com/serverless/serverless/issues/9089)) ([5f5d2e5](https://github.com/serverless/serverless/commit/5f5d2e580e267ad8bbd34f29c4613ca751908992)) ([Dave Lowther](https://github.com/DaveLo))
- **Variables:** Expose source resolution errors as non-user errors ([#9088](https://github.com/serverless/serverless/pull/9088)) ([5e2406b](https://github.com/serverless/serverless/commit/5e2406bea78b353fea10a45d657ae2a7789531bd)) ([Mariusz Nowak](https://github.com/medikoo))

### Maintenance Improvements

- **CLI:**
  - Rely on `cli/is-help-request` util ([#9086](https://github.com/serverless/serverless/pull/9086)) ([c9087ec](https://github.com/serverless/serverless/commit/c9087ec4e659f2d1c894f814f6a0c54d0ddb6dcc)) ([Mariusz Nowak](https://github.com/medikoo))
  - Report Platform Client instead of SDK version ([#9092](https://github.com/serverless/serverless/issues/9092)) ([2b857c7](https://github.com/serverless/serverless/commit/2b857c7eb45e6543ca5afb5604542e8f76175910)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **Variables:**
  - Improve error message related to JS func resolver ([#9085](https://github.com/serverless/serverless/pull/9085)) ([b90538a](https://github.com/serverless/serverless/commit/b90538af08a51a5e2a3ec65d6d1bf8c51a54b9c3)) ([Mariusz Nowak](https://github.com/medikoo))
  - Improve source fulfillment handling ([#9088](https://github.com/serverless/serverless/pull/9088)) ([524c43d](https://github.com/serverless/serverless/commit/524c43df75606fdda0ec28c3370a0f743a9d1efa)) ([Mariusz Nowak](https://github.com/medikoo))

### [2.28.7](https://github.com/serverless/serverless/compare/v2.28.6...v2.28.7) (2021-03-04)

### Bug Fixes

- **Packaging:** Fix packaging performance regression and increased number of observed `EMFILE` errors by reverting intensive `bluebird` related refactors as listed below
  - Revert removal of `bluebird` from `lib/plugins/aws` ([#9074](https://github.com/serverless/serverless/pull/9074)) ([55abaaf](https://github.com/serverless/serverless/commit/55abaaf6d5db17c4824c2d2d3dc3f540c682acea)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Revert removal of `bluebird` from `lib/plugins/create` ([#9074](https://github.com/serverless/serverless/pull/9074)) ([ae2c92c](https://github.com/serverless/serverless/commit/ae2c92ced6f25cca6c6243daf90aa23bfe0d6278)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Revert removal of `bluebird` from `lib/plugins/interactiveCli` ([#9074](https://github.com/serverless/serverless/pull/9074)) ([217b975](https://github.com/serverless/serverless/commit/217b9751ead901395467b7221f601f955329eb1b)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Revert removal of `bluebird` from `lib/plugins/package` ([#9074](https://github.com/serverless/serverless/pull/9074)) ([399d91b](https://github.com/serverless/serverless/commit/399d91b7e4508ae15c4beba1fec66c32c0367386)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Revert removal of `bluebird` from `lib/plugins/plugin` ([#9074](https://github.com/serverless/serverless/pull/9074)) ([2a9f79f](https://github.com/serverless/serverless/commit/2a9f79f19e33c83ed4df46ecd305cc49ce1a8c15)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Revert removal of `bluebird` from `lib/classes` ([#9074](https://github.com/serverless/serverless/pull/9074)) ([c41bd64](https://github.com/serverless/serverless/commit/c41bd64bb233b588dc615bc11c513f3e2c486084)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Revert removal of `bluebird` from `lib/utils` ([#9074](https://github.com/serverless/serverless/pull/9074)) ([f62fc2e](https://github.com/serverless/serverless/commit/f62fc2ee9c39a15c2b3894c5fae185a530307506)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Revert removal of `bluebird` from `lib/plugins` ([#9074](https://github.com/serverless/serverless/pull/9074)) ([7a012d8](https://github.com/serverless/serverless/commit/7a012d83b975022e5ee60f5054229398a9424d13)) ([Piotr Grzesik](https://github.com/pgrzesik))

### [2.28.6](https://github.com/serverless/serverless/compare/v2.28.5...v2.28.6) (2021-03-03)

### Bug Fixes

- **Variables:** Ensure to apply intialization patch unconditionally ([#9063](https://github.com/serverless/serverless/issues/9063)) ([d6c7d97](https://github.com/serverless/serverless/commit/d6c7d97dc6bb6229dd80e443a09f5a741bf1380e)) ([Mariusz Nowak](https://github.com/medikoo))

### [2.28.5](https://github.com/serverless/serverless/compare/v2.28.4...v2.28.5) (2021-03-03)

### Bug Fixes

- **Variables:**
  - Fix variables setup for external plugins usage ([#9060](https://github.com/serverless/serverless/issues/9060)) ([25dd575](https://github.com/serverless/serverless/commit/25dd575a4d597c09078ac8a2c709d834ae85221e)) ([Mariusz Nowak](https://github.com/medikoo))
  - Report with meaningful error unresolved `plugins` property ([#9061](https://github.com/serverless/serverless/issues/9061)) ([5565047](https://github.com/serverless/serverless/commit/55650473828eb6df9563687ccf3996b6713da191)) ([Mariusz Nowak](https://github.com/medikoo))

### [2.28.4](https://github.com/serverless/serverless/compare/v2.28.3...v2.28.4) (2021-03-03)

### Bug Fixes

- **Variables:** Ensure to not share property cache across resolutions ([#9057](https://github.com/serverless/serverless/issues/9057)) ([68f326e](https://github.com/serverless/serverless/commit/68f326e79f92f8a94ba73352cba40c85e08c10cf)) ([Mariusz Nowak](https://github.com/medikoo))

### Maintenance Improvements

- **Variables:** Ensure to pass `isConfigurationResolved` to local instance ([#9057](https://github.com/serverless/serverless/issues/9057)) ([10e1dda](https://github.com/serverless/serverless/commit/10e1dda23b47cf439624c4602adce41a5c73fa51)) ([Mariusz Nowak](https://github.com/medikoo))
- Remove `bluebird` from `lib/plugins/aws` ([#9054](https://github.com/serverless/serverless/issues/9054)) ([b11171c](https://github.com/serverless/serverless/commit/b11171c70c8f5597e2644f7ea8ec82a17a9eee29)) ([Juanjo Diaz](https://github.com/juanjodiaz))

### [2.28.3](https://github.com/serverless/serverless/compare/v2.28.2...v2.28.3) (2021-03-02)

### Bug Fixes

- **Variables:**
  - Recognize hyphens in source types ([#9052](https://github.com/serverless/serverless/pull/9052)) ([21ac1be](https://github.com/serverless/serverless/commit/21ac1beb225946713665e9d8ad22d6e5c63819a9)) ([Mariusz Nowak](https://github.com/medikoo))
  - Ensure proper error handling for resolved value parsing([#9052](https://github.com/serverless/serverless/pull/9052)) ([df62739](https://github.com/serverless/serverless/commit/df627394b36c16553a73328850ff722f1063254c)) ([Mariusz Nowak](https://github.com/medikoo))

### [2.28.2](https://github.com/serverless/serverless/compare/v2.28.1...v2.28.2) (2021-03-02)

### Bug Fixes

- **Variables:** Ensure to resolve variables in resolved strings ([#9050](https://github.com/serverless/serverless/pull/9050)) ([480b612](https://github.com/serverless/serverless/commit/480b61270cfef8f1a4a5aa36cd235db2362c9cfd)) ([Mariusz Nowak](https://github.com/medikoo))
- **AWS Credentials:** Fix unrecognized profile error reporting ([#9045](https://github.com/serverless/serverless/pull/9045)) ([6c4beb6](https://github.com/serverless/serverless/commit/6c4beb64ee6fe6722fbb7ca757611807d4025a26)) ([Mariusz Nowak](https://github.com/medikoo))

### [2.28.1](https://github.com/serverless/serverless/compare/v2.28.0...v2.28.1) (2021-03-02)

### Bug Fixes

- **Variables:**
  - Error on property access attempt on primitive result ([#9032](https://github.com/serverless/serverless/pull/9032)) ([131516a](https://github.com/serverless/serverless/commit/131516a6d094ee9b75fbe9b1d975b96d9c358a82)) ([Mariusz Nowak](https://github.com/medikoo))
  - Resolve plain text for unrecognized extensions ([#9032](https://github.com/serverless/serverless/pull/9032)) ([d2e6a8a](https://github.com/serverless/serverless/commit/d2e6a8adef5632ddf63581cfacc7cb77bbc634af)) ([Mariusz Nowak](https://github.com/medikoo))

### Maintenance Improvements

- Improve deprecation message ([#9034](https://github.com/serverless/serverless/pull/9034)) ([8592bdb](https://github.com/serverless/serverless/commit/8592bdb1b2ecdbf4dd24700613cc664cbf3ec611)) ([Mariusz Nowak](https://github.com/medikoo))
- Remove `bluebird` from `lib/plugins/interactiveCli` ([#9029](https://github.com/serverless/serverless/issues/9029)) ([7c0ceb5](https://github.com/serverless/serverless/commit/7c0ceb5c4a1171666e381ef9a00c6f133569732b)) ([Juanjo Diaz](https://github.com/juanjodiaz))
- Remove `bluebird` from `lib/plugins/package` ([#9028](https://github.com/serverless/serverless/issues/9028)) ([0fb0f43](https://github.com/serverless/serverless/commit/0fb0f43919bd3bd4a9c57b9f33bf96a822ce027c)) ([Juanjo Diaz](https://github.com/juanjodiaz))
- Use `async` in `lib/plugins/aws/package` ([#8870](https://github.com/serverless/serverless/issues/8870)) ([6e486b3](https://github.com/serverless/serverless/commit/6e486b3eb1cbd1755501f00de59b2347e243c100)) ([ifitzsimmons](https://github.com/ifitzsimmons))
- **Variables:**
  - Resolve all env variables with new resolver ([#9040](https://github.com/serverless/serverless/pull/9040)) ([c1d8b58](https://github.com/serverless/serverless/commit/c1d8b58ed8a5a7a91d9dfa28536a9c0d997b809b)) ([Mariusz Nowak](https://github.com/medikoo))
  - Do not handle resolution when no vars to resolve ([#9040](https://github.com/serverless/serverless/pull/9040)) ([14ea1af](https://github.com/serverless/serverless/commit/14ea1af886496fac53d4aaffe009ae78873c81bb)) ([Mariusz Nowak](https://github.com/medikoo))
  - Do not run old resolver when no vars to resolve ([#9040](https://github.com/serverless/serverless/pull/9040)) ([7aac480](https://github.com/serverless/serverless/commit/7aac480fbb15d61a40320f98af4cee6f1b2475b3)) ([Mariusz Nowak](https://github.com/medikoo))
  - Make resolution error handler reusable ([#9040](https://github.com/serverless/serverless/pull/9040)) ([452fdc2](https://github.com/serverless/serverless/commit/452fdc2445e2c69a6c908f6b2b52c0659d87bbc0)) ([Mariusz Nowak](https://github.com/medikoo))
  - Make `resolverConfiguration` reusable ([#9040](https://github.com/serverless/serverless/pull/9040)) ([8e72247](https://github.com/serverless/serverless/commit/8e722472cc23eac7b342b3e67434977cc69698aa)) ([Mariusz Nowak](https://github.com/medikoo))

## [2.28.0](https://github.com/serverless/serverless/compare/v2.27.1...v2.28.0) (2021-02-26)

### Features

- **AWS API Gateway:** Allow reuse and customization of schema models ([#7619](https://github.com/serverless/serverless/pull/7619)) ([aeb64fd](https://github.com/serverless/serverless/commit/aeb64fd3cc6d27c495ce19efc3745a16a46b6534)) ([Jeffrey McGuffee](https://github.com/jmcguffee) & [Piotr Grzesik](https://github.com/pgrzesik))

### Bug Fixes

- **CLI:** Do not duplicate variables error information ([#9019](https://github.com/serverless/serverless/pull/9019)) ([2f62bdf](https://github.com/serverless/serverless/commit/2f62bdf2316a76a0dd4b855e178857ecff7c7402)) ([Mariusz Nowak](https://github.com/medikoo))
- **Variables:** Ensure to not share source cache across resolutions ([#9019](https://github.com/serverless/serverless/pull/9019)) ([5ad1c19](https://github.com/serverless/serverless/commit/5ad1c19cc9a5601184883a916a29172eeb9c3789)) ([Mariusz Nowak](https://github.com/medikoo))

### Maintenance Improvements

- **CLI:**
  - Require `variablesResolutionMode` to be resolved upfront ([#9014](https://github.com/serverless/serverless/pull/9014)) ([a488000](https://github.com/serverless/serverless/commit/a488000dc67c10026d010744bb29fca25f72f42b)) ([Mariusz Nowak](https://github.com/medikoo))
  - Resolve `.env` files before intializing `Serverless` instance ([#9014](https://github.com/serverless/serverless/pull/9014)) ([a9e3a66](https://github.com/serverless/serverless/commit/a9e3a667355e91af7fb558eb551ed7d59a865527)) ([Mariusz Nowak](https://github.com/medikoo))
- Remove `bluebird` from `lib/plugins/create` ([#8996](https://github.com/serverless/serverless/issues/8996)) ([258543a](https://github.com/serverless/serverless/commit/258543ab6e1874ba41be3563346cd7b50993ac58)) ([Juanjo Diaz](https://github.com/juanjodiaz))

## [2.27.1](https://github.com/serverless/serverless/compare/v2.27.0...v2.27.1) (2021-02-25)

### Bug Fixes

- **Variables:**
  - Fix nested sources resolution ([#9011](https://github.com/serverless/serverless/issues/9011)) ([99fd907](https://github.com/serverless/serverless/commit/99fd907abbe3d83f8db7bf3a1924da770bc18be8)) ([Mariusz Nowak](https://github.com/medikoo))
  - Report with `null` not existing `file` sources ([#9008](https://github.com/serverless/serverless/issues/9008)) ([3ab81e5](https://github.com/serverless/serverless/commit/3ab81e5be94c69b90dc8487e321fb4cf7efc2c11)) ([Mariusz Nowak](https://github.com/medikoo))
  - Fix unterminated variable resolution for some cases ([#9011](https://github.com/serverless/serverless/issues/9011)) ([cc5bfd5](https://github.com/serverless/serverless/commit/cc5bfd53ae2459e4d7ac1ec6314c030d39997958)) ([Mariusz Nowak](https://github.com/medikoo))
  - Communicate with meaningful error not accessible `provider` properties ([#8992](https://github.com/serverless/serverless/issues/8992)) ([e5307b0](https://github.com/serverless/serverless/commit/e5307b05d31b7a80be80fc72e1829aead8762680)) ([Mariusz Nowak](https://github.com/medikoo))
  - Improve JS file resolution error handling ([#9008](https://github.com/serverless/serverless/issues/9008)) ([9ecc108](https://github.com/serverless/serverless/commit/9ecc1087653edfde9da400f496030dea0d6203ce)) ([Mariusz Nowak](https://github.com/medikoo))

### Maintenance Improvements

- Remove `bluebird` from `lib/plugins/plugin` ([#8984](https://github.com/serverless/serverless/issues/8984)) ([9e79602](https://github.com/serverless/serverless/commit/9e7960297227b39f05c2619a80e3cac7cb7be1a5)) ([Juanjo Diaz](https://github.com/juanjodiaz))

## [2.27.0](https://github.com/serverless/serverless/compare/v2.26.0...v2.27.0) (2021-02-24)

### Features

- **AWS EventBridge:** Native CloudFormation based deployment (turn on via `provider.eventBridge.useCloudFormation: true`) ([#8437](https://github.com/serverless/serverless/issues/8437)) ([13444ca](https://github.com/serverless/serverless/commit/13444caa28a5fdb268599c8fa67f4bfef1dd5e36)) ([stuartforrest-infinity](https://github.com/stuartforrest-infinity) & [Piotr Grzesik](https://github.com/pgrzesik))
- **AWS Deploy:** Support `null` values for properties in CF resources (those properties will be removed for final CF template version) ([#8975](https://github.com/serverless/serverless/issues/8975)) ([9b030ad](https://github.com/serverless/serverless/commit/9b030ad5f4797c31ea37e621c1a3f297a29dfa86)) ([yumei](https://github.com/yumeixox))

### Bug Fixes

- **CLI:** Recognize `-s` as `--stage` alias, when expected ([9ae6045](https://github.com/serverless/serverless/commit/9ae604591dbb7e82aff0668d2055ed9d69bb920a)) ([#8997](https://github.com/serverless/serverless/issues/8997)) ([Mariusz Nowak](https://github.com/medikoo))
- **Variables:** Ensure vars are recognized in address followed by source ([#9000](https://github.com/serverless/serverless/issues/9000)) ([fb9ce24](https://github.com/serverless/serverless/commit/fb9ce246b37219b1e3077ea53777f753d0a9205d)) ([Mariusz Nowak](https://github.com/medikoo))

### Maintenance Improvements

- **AWS Deploy:** Rely on `provider.request` for AWS SDK calls ([#8913](https://github.com/serverless/serverless/issues/8913)) ([4e05995](https://github.com/serverless/serverless/commit/4e0599571afe11d4bd11aee14fe07be2be48fca0)) ([AlinoeDoctari](https://github.com/AlinoeDoctari))
- **CLI:**
  - Recognize `app` and `org` params ([#8997](https://github.com/serverless/serverless/issues/8997)) ([6b1921f](https://github.com/serverless/serverless/commit/6b1921f59e1105499a329ab3aaf6134e7fb0ff6c)) ([Mariusz Nowak](https://github.com/medikoo))
  - Refactor `-v` handling ([#8997](https://github.com/serverless/serverless/issues/8997)) ([8db64a1](https://github.com/serverless/serverless/commit/8db64a1f319d2238e71960d57425d2b6e5c9c5d6)) ([Mariusz Nowak](https://github.com/medikoo))

## [2.26.0](https://github.com/serverless/serverless/compare/v2.25.2...v2.26.0) (2021-02-24)

### Features

- **AWS HTTP API:** Add ability to apply `provider.tags` ([#8938](https://github.com/serverless/serverless/issues/8938)) ([9f5fd61](https://github.com/serverless/serverless/commit/9f5fd6100978a0bda1c300b9429b24b6e586c52f)) ([jayasai470](https://github.com/jayasai470))
- **Variables:** New parser and resolver implementation ([#8987](https://github.com/serverless/serverless/pull/8987)) ([fb2c425](https://github.com/serverless/serverless/commit/fb2c425ed2869d7faab4ae52cb001785aa389a40)) ([Mariusz Nowak](https://github.com/medikoo))

### Bug Fixes

- **AWS ALB:** Conform to CF schema with multiple host header ([#8965](https://github.com/serverless/serverless/issues/8965)) ([36c78c7](https://github.com/serverless/serverless/commit/36c78c70d1cf306556a5a9f8a3c3908e8b4c7d05)) ([Zach Swanson](https://github.com/zswanson))
- **CLI:** Fix resolution of empty valued params as `param=` ([#8978](https://github.com/serverless/serverless/pull/8978)) ([5acdc0a](https://github.com/serverless/serverless/commit/5acdc0a5e03994b6835a3be5411bffb905ca4cc2)) ([Mariusz Nowak](https://github.com/medikoo))
- Display version related deprecations only with functions ([#8980](https://github.com/serverless/serverless/pull/8980)) ([4f64e56](https://github.com/serverless/serverless/commit/4f64e560b9157dc8700328686a778ebd2a78ba9e)) ([Mariusz Nowak](https://github.com/medikoo))

### Maintenance Improvements

- Remove `bluebird` from `lib/classes` ([#8943](https://github.com/serverless/serverless/issues/8943)) ([1a694ae](https://github.com/serverless/serverless/commit/1a694ae4aab0a347b018380110b9a436f6c43c1e)) ([Juanjo Diaz](https://github.com/juanjodiaz))
- Remove `bluebird` from `lib/utils` ([#8972](https://github.com/serverless/serverless/issues/8972)) ([820cc1f](https://github.com/serverless/serverless/commit/820cc1f581bfd502e5452f5c9935301ec86f9d14)) ([Juanjo Diaz](https://github.com/juanjodiaz))
- Remove `bluebird` from top-level `lib/plugins` ([#8973](https://github.com/serverless/serverless/issues/8973)) ([8fead7f](https://github.com/serverless/serverless/commit/8fead7f39e3a5649e87a4ceb6e0c0a28e7f61ea5)) ([Juanjo Diaz](https://github.com/juanjodiaz))

### Templates

- Support TS path mapping in `aws-nodejs-typescript` ([#8968](https://github.com/serverless/serverless/issues/8968)) ([e050440](https://github.com/serverless/serverless/commit/e0504406ea8c70e2c42363bef9da468899a0ca03)) ([Nick Hammond](https://github.com/nhammond101))
- Ensure that `gradle-wrapper.jar` is not excluded ([#8967](https://github.com/serverless/serverless/pull/8967)) ([deed534](https://github.com/serverless/serverless/commit/deed53449fb4c302a3fe04f0f2bef19b27d9ef81)) ([Piotr Grzesik](https://github.com/pgrzesik))

### [2.25.2](https://github.com/serverless/serverless/compare/v2.25.1...v2.25.2) (2021-02-18)

### Bug Fixes

- **CLI:** Ensure to recognize `-v` param as boolean in all cases ([#8964](https://github.com/serverless/serverless/issues/8964)) ([82b95fc](https://github.com/serverless/serverless/commit/82b95fc4924d4e93a7ae79bb741859df3dd464c0)) ([Mariusz Nowak](https://github.com/medikoo))
- **AWS Lambda:** Throw verbose error when referencing invalid layer ([#8961](https://github.com/serverless/serverless/issues/8961)) ([5057f9a](https://github.com/serverless/serverless/commit/5057f9ab865dd62d12e8ff1f673615462470bb74)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **Variables:** Properly resolve vars if `prototype` key is in property path ([#8962](https://github.com/serverless/serverless/issues/8962)) ([496d357](https://github.com/serverless/serverless/commit/496d3574c6f8df389331ec92fd330efb652f65e6)) ([Piotr Grzesik](https://github.com/pgrzesik))

### [2.25.1](https://github.com/serverless/serverless/compare/v2.25.0...v2.25.1) (2021-02-16)

### Bug Fixes

- **CLI:** Ensure support for upper case params ([b17c461](https://github.com/serverless/serverless/commit/b17c461a1291728cda8fe6fbfbc7a9f56ab59d33)) ([Mariusz Nowak](https://github.com/medikoo))

## [2.25.0](https://github.com/serverless/serverless/compare/v2.24.0...v2.25.0) (2021-02-16)

### Features

- **AWS HTTP API:** Support `provider.httpApi.disableDefaultEndpoint` ([#8649](https://github.com/serverless/serverless/issues/8649)) ([bebf343](https://github.com/serverless/serverless/commit/bebf3430b4a22f90497312759e3728a8a233115b)) ([Guillaume Desvé](https://github.com/gdraynz))

### Bug Fixes

- **CLI:** Ensure to support `_` in param names ([#8952](https://github.com/serverless/serverless/issues/8952)) ([7e3e50b](https://github.com/serverless/serverless/commit/7e3e50bca2c038398736eef8d867ff901da0aaae)) ([Mariusz Nowak](https://github.com/medikoo))

## [2.24.0](https://github.com/serverless/serverless/compare/v2.23.0...v2.24.0) (2021-02-16)

### Features

- **AWS IAM:** Group IAM-related settings under `provider.iam` ([#8701](https://github.com/serverless/serverless/issues/8701)) ([9ad4d07](https://github.com/serverless/serverless/commit/9ad4d07886d8bca29cb7c0802c3623defb6c8c3a)) ([Dmitry Shirokov](https://github.com/runk))

### Bug Fixes

- **AWS Deploy:** Ensure to handle artifact stream read errors ([#8948](https://github.com/serverless/serverless/pull/8948)) ([300e3a9](https://github.com/serverless/serverless/commit/300e3a92d5d5d54c4269dd05b6e5d9e2e96b380d)) ([Mariusz Nowak](https://github.com/medikoo))
- **AWS Lambda:** Properly resolve SHA for repo with slashes ([#8918](https://github.com/serverless/serverless/pull/8918)) ([4c74792](https://github.com/serverless/serverless/commit/4c7479283cd2bfb20b2ddb9d21b824b4757234ed)) ([Piotr Grzesik](https://github.com/pgrzesik))
- Reject non normative configuration structure ([#8927](https://github.com/serverless/serverless/pull/8927)) ([8bd4314](https://github.com/serverless/serverless/commit/8bd431473265d6bc2b536c0f5070f99e1639382d)) ([Mariusz Nowak](https://github.com/medikoo))

### Maintenance Improvements

- **CLI**:
  - Rely on new CLI args parser ([#8927](https://github.com/serverless/serverless/pull/8927)) ([9e059d0](https://github.com/serverless/serverless/commit/9e059d0f45b083f887bc07f0cbf33a81f5b91ba2)) ([Mariusz Nowak](https://github.com/medikoo))
  - Remove internal CLI arguments parsing ([#8927](https://github.com/serverless/serverless/pull/8927)) ([16950d0](https://github.com/serverless/serverless/commit/16950d098b0b78e6ad5de35e908c7a1ee91f775b)) ([Mariusz Nowak](https://github.com/medikoo))
  - Move deprecation report to `init` phase ([#8927](https://github.com/serverless/serverless/pull/8927)) ([1eaa626](https://github.com/serverless/serverless/commit/1eaa6260aa9f747d0aa01006ce54d3313e7b7e0f)) ([Mariusz Nowak](https://github.com/medikoo))
- Use `async/await` in `events/apiGateway`. ([#8869](https://github.com/serverless/serverless/issues/8869)) ([c5ba682](https://github.com/serverless/serverless/commit/c5ba682a6bc4fc96151c75cdf50cff2468d6def5)) ([ifitzsimmons](https://github.com/ifitzsimmons))
- Use `async/await` in `lib/plugins/aws/invokeLocal`. ([#8876](https://github.com/serverless/serverless/issues/8876)) ([134db21](https://github.com/serverless/serverless/commit/134db21ed27874ae64db1c8964523b5b5ae6c2bf)) ([ifitzsimmons](https://github.com/ifitzsimmons))
- Remove unneeded `split` in `getHttp` ([#8939](https://github.com/serverless/serverless/issues/8939)) ([7213d1d](https://github.com/serverless/serverless/commit/7213d1d4f85c7d1583c0eba531e026d3f7a8e96c)) ([Gareth Jones](https://github.com/G-Rath))
- Use standalone `ServerlessError`. ([#8897](https://github.com/serverless/serverless/issues/8897)) ([006557d](https://github.com/serverless/serverless/commit/006557d8471623af7f6b83c58a14e9e4fe244507)) ([Juanjo Diaz](https://github.com/juanjodiaz))
- Patch handling of `isInvokedByGlobalInstallation` flag ([#8927](https://github.com/serverless/serverless/pull/8927)) ([21c9f26](https://github.com/serverless/serverless/commit/21c9f26ea64a7dfc06a96c173c8268d8ad835870)) ([Mariusz Nowak](https://github.com/medikoo))

### Templates

- Add `package.json` to `plugin` template ([#8933](https://github.com/serverless/serverless/pull/8933)) ([410f0ec](https://github.com/serverless/serverless/commit/410f0ec3b5f09f9bef22d14fcaccbb8bd6e70460)) ([Piotr Grzesik](https://github.com/pgrzesik))
- Update `aws-nodejs-typescript` for `nodejs14.x` ([#8914](https://github.com/serverless/serverless/pull/8914)) ([5fa51dc](https://github.com/serverless/serverless/commit/5fa51dc53d039814aef80dd2a8c8069015215696)) ([Frédéric Barthelet](https://github.com/fredericbarthelet))
- Fix types handling in `aws-nodejs-typescript` ([#8929](https://github.com/serverless/serverless/issues/8929)) ([5302b91](https://github.com/serverless/serverless/commit/5302b9176097faee4c73d585b63e6bf772b64e43)) ([g-awa](https://github.com/daisuke-awaji))
- Fix statement in `.npmignore` to handle `.gitignore` ([#8947](https://github.com/serverless/serverless/pull/8947)) ([d0c0879](https://github.com/serverless/serverless/commit/d0c0879032aedca567fef807b7143b7325f43b4d)) ([Piotr Grzesik](https://github.com/pgrzesik))

## [2.23.0](https://github.com/serverless/serverless/compare/v2.22.0...v2.23.0) (2021-02-08)

### Features

- **AWS Lambda:** Add support for `nodejs14.x` runtime ([#8894](https://github.com/serverless/serverless/issues/8894)) ([8799cbb](https://github.com/serverless/serverless/commit/8799cbbae76c1e189bd5d576fc68406daf9d9787)) ([Subash Adhikari](https://github.com/adikari))

### Bug Fixes

- **AWS Lambda:** Ensure proper normalization of ECR repository name ([#8908](https://github.com/serverless/serverless/pull/8908)) ([c5639d2](https://github.com/serverless/serverless/commit/c5639d21ea4db9fe7ab9d9f00c8bcf42e4b81ad7)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **AWS Deploy:** Gracefully handle denied access to ECR ([#8901](https://github.com/serverless/serverless/pull/8901)) ([816394c](https://github.com/serverless/serverless/commit/816394c6e5dfc50b332314aef66eeb9ed75d139a)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **AWS Local Invocation**: Properly handle error if Java bridge is not present ([#8868](https://github.com/serverless/serverless/pull/8868)) ([11fb141](https://github.com/serverless/serverless/commit/11fb14115ea47d53a61fa666a94e60d585fb3a4d)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **CLI**:
  - Properly resolve local version ([#8899](https://github.com/serverless/serverless/pull/8899)) ([053bcc7](https://github.com/serverless/serverless/commit/053bcc7624f5d1ace56c708be5125fc665973a1d)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Handle gently npm response errors ([#8900](https://github.com/serverless/serverless/pull/8900)) ([ab77a11](https://github.com/serverless/serverless/commit/ab77a11e135ec879b3309205d8bfe010ceb68e9e)) ([Mariusz Nowak](https://github.com/medikoo))

### Maintenance Improvements

- Use `async/await` in `lib/plugins/aws`. ([#8871](https://github.com/serverless/serverless/issues/8871)) ([efbaf00](https://github.com/serverless/serverless/commit/efbaf00b33ca2f51d2f0b18b98466341e51f3052)) ([ifitzsimmons](https://github.com/ifitzsimmons))
- Use `async/await` in `lib/plugins`. ([#8875](https://github.com/serverless/serverless/issues/8875)) ([f95971d](https://github.com/serverless/serverless/commit/f95971d22b65c963ab01ac0273abcffb932b2434)) ([ifitzsimmons](https://github.com/ifitzsimmons))
- Use `async/await` in `aws/package/compile/events` ([#8873](https://github.com/serverless/serverless/issues/8873)) ([3c93e2a](https://github.com/serverless/serverless/commit/3c93e2a5347ed700e55d4307b4498e0c49eb8a03)) ([ifitzsimmons](https://github.com/ifitzsimmons))
- Use `async/await` in `compile/events/websockets` ([#8874](https://github.com/serverless/serverless/issues/8874)) ([61dd3bd](https://github.com/serverless/serverless/commit/61dd3bde8d17cdd995fdd27259a689d12bee1e42)) ([ifitzsimmons](https://github.com/ifitzsimmons))
- Use `async/await` in `lib/plugins/aws/lib` ([#8872](https://github.com/serverless/serverless/issues/8872)) ([489affc](https://github.com/serverless/serverless/commit/489affcb520d8f50f87c84b932627812f491e66c)) ([ifitzsimmons](https://github.com/ifitzsimmons))

## [2.22.0](https://github.com/serverless/serverless/compare/v2.21.1...v2.22.0) (2021-02-02)

### Features

- **AWS Lambda:** Add ability to customize `file` for Dockerfile ([#8865](https://github.com/serverless/serverless/pull/8865)) ([785f97b](https://github.com/serverless/serverless/commit/785f97b1a9e9b4c9cb24f3cb05a502f2d3ae1680)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **Standalone:** Allow to install specific versions ([#8858](https://github.com/serverless/serverless/issues/8858)) ([019f0bf](https://github.com/serverless/serverless/commit/019f0bf410c5c1c0ff0383221863cca171e1dcc9)) ([alegonz](https://github.com/alegonz))

### Bug Fixes

- **CLI:** Ensure to not display programmatic use deprecation ([#8864](https://github.com/serverless/serverless/pull/8864)) ([fa626a8](https://github.com/serverless/serverless/commit/fa626a8e22870d0e5ad549a9d7eab656e7e664aa)) ([Mariusz Nowak](https://github.com/medikoo))
- **Config Schema:**
  - Add type to `logRetentionInDays` ([#8844](https://github.com/serverless/serverless/issues/8844)) ([ec12a2b](https://github.com/serverless/serverless/commit/ec12a2be0a9510ababca8ffc5fe8836dcef82773)) ([frozenbonito](https://github.com/frozenbonito))
  - Filter out duplicate error messages ([#8849](https://github.com/serverless/serverless/pull/8849)) ([e0bc57a](https://github.com/serverless/serverless/commit/e0bc57ab1fee0a40a9e9278fa00eb2b851df2e55)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Add schema dependencies for `image` config ([#8849](https://github.com/serverless/serverless/pull/8849)) ([297c229](https://github.com/serverless/serverless/commit/297c22972ea7d477a9ced296f591f8ab0a8ac77f)) ([Piotr Grzesik](https://github.com/pgrzesik))

### Maintenance Improvements

- Replace `fse.promises.realpath` with `fs.promises.realpath` ([#8853](https://github.com/serverless/serverless/pull/8853)) ([f5174ff](https://github.com/serverless/serverless/commit/f5174ffa8027392525a7c57ea1fa59627a61bcc1)) ([Sudipto Das](https://github.com/sdas13))

### Templates

- Add `aws-nodejs-docker` template ([#8845](https://github.com/serverless/serverless/pull/8845)) ([1a0390b](https://github.com/serverless/serverless/commit/1a0390b59722d84e87595bc462c83b6baf214da1)) ([Piotr Grzesik](https://github.com/pgrzesik))
- Add `aws-python-docker` template ([#8846](https://github.com/serverless/serverless/pull/8846)) ([fd9b26a](https://github.com/serverless/serverless/commit/fd9b26a9e898685da81663064274250c5771363c)) ([Piotr Grzesik](https://github.com/pgrzesik))
- Fix handler path resolution in `aws-nodejs-typescript` ([#8829](https://github.com/serverless/serverless/pull/8829)) ([b753641](https://github.com/serverless/serverless/commit/b753641b072485d4764e891b5e90242776bec724)) ([Frédéric Barthelet](https://github.com/fredericbarthelet))
- Ensure that `.gitignore` is packaged for templates ([#8829](https://github.com/serverless/serverless/pull/8829)) ([e79f906](https://github.com/serverless/serverless/commit/e79f906b9fd0940e8eb1367cf6ce1ed1095f0c46)) ([Piotr Grzesik](https://github.com/pgrzesik))

### [2.21.1](https://github.com/serverless/serverless/compare/v2.21.0...v2.21.1) (2021-01-26)

### Bug Fixes

- **CLI:** Fix resolution of service path where nested config is involved ([#8835](https://github.com/serverless/serverless/pull/8835)) ([9b7315f](https://github.com/serverless/serverless/commit/9b7315f080d5bbccf2c9e7d618e7a7dbeb9a12b2)) ([Mariusz Nowak](https://github.com/medikoo))
- **AWS CloudFront:**
  - Ensure unique names for cache policy ([#8818](https://github.com/serverless/serverless/issues/8818)) ([a108b76](https://github.com/serverless/serverless/commit/a108b761d05fc72987542588fefa65d7e57ac7ec)) ([Ben Scholzen](https://github.com/DASPRiD))
  - Fix origin object schema ([#8827](https://github.com/serverless/serverless/issues/8827)) ([90d9fc2](https://github.com/serverless/serverless/commit/90d9fc2b5fbf700a6c1b4da60a6f211ca5e43bd4)) ([frozenbonito](https://github.com/frozenbonito))
- Fix AWS tags validation schema ([#8766](https://github.com/serverless/serverless/issues/8766)) ([4dff8e5](https://github.com/serverless/serverless/commit/4dff8e53a64ad38a2b8515ca2543b49c001a779c)) ([Sam Stenvall](https://github.com/Jalle19))

### Maintenance Improvements

- Remove obsolete `getLocalAccessKey` util ([#8834](https://github.com/serverless/serverless/issues/8834)) ([90d9fc2](https://github.com/serverless/serverless/commit/90d9fc2b5fbf700a6c1b4da60a6f211ca5e43bd4))([6f9824a](https://github.com/serverless/serverless/commit/6f9824abac780d4725d401c776d80ed658e31d04)) ([Piotr Grzesik](https://github.com/pgrzesik))
- Upgrade to `@serverless/utils` v3 ([#8834](https://github.com/serverless/serverless/issues/8834)) ([f6c5427](https://github.com/serverless/serverless/commit/f6c5427b0f12925ed4e91e70b6ca0bbfaf95616d)) ([Piotr Grzesik](https://github.com/pgrzesik))

## [2.21.0](https://github.com/serverless/serverless/compare/v2.20.1...v2.21.0) (2021-01-26)

### Features

- **AWS CloudFront:** Support CF functions for origin and domain ([#8828](https://github.com/serverless/serverless/pull/8828)) ([0839b58](https://github.com/serverless/serverless/commit/0839b5862caddb71f31b62493bbb7324d278bd70)) ([frozenbonito](https://github.com/frozenbonito))
- **AWS Lambda:** Add support for self-managed `kafka` event ([#8784](https://github.com/serverless/serverless/pull/8784)) ([ff60501](https://github.com/serverless/serverless/commit/ff605018a70a7156b0ca021adb080a4b4e0f2ede)) ([lewgordon](https://github.com/lewgordon))
- Support `kmsKeyArn` for `deploy function` ([#8697](https://github.com/serverless/serverless/pull/8697)) ([8a92be9](https://github.com/serverless/serverless/commit/8a92be9be37b554c0e1ec95f5d040ecc5b2d63cc)) ([ifitzsimmons](https://github.com/ifitzsimmons))

### Bug Fixes

- **CLI:** Fix resolution of "--config=<configPath>" format ([#8825](https://github.com/serverless/serverless/pull/8825)) ([cd5a739](https://github.com/serverless/serverless/commit/cd5a739265e2fe90f53f900f567eddcb9010b3aa)) ([Mariusz Nowak](https://github.com/medikoo))
- **Packaging:** Proper exclusion of dependencies across platforms ([#8831](https://github.com/serverless/serverless/pull/8831)) ([847aa9c](https://github.com/serverless/serverless/commit/847aa9ca7f885f126c4a0a0279db30c05a8c9a6f)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **Standalone:** Ensure proper resolution of runtime wrappers ([#8809](https://github.com/serverless/serverless/pull/8809)) ([1833894](https://github.com/serverless/serverless/commit/1833894856991e98e0d32701217453c413164cf3)) ([Piotr Grzesik](https://github.com/pgrzesik))

### Maintenance Improvements

- Custom execution role getter ([#8824](https://github.com/serverless/serverless/issues/8824)) ([12805c3](https://github.com/serverless/serverless/commit/12805c3d152d85af9dba3dd3ecfa2002a621f6a8)) ([Dmitry Shirokov](https://github.com/runk))
- Replace `fse.exists` with `fs.promises.access` ([#8788](https://github.com/serverless/serverless/issues/8788)) ([9abe9db](https://github.com/serverless/serverless/commit/9abe9db27f26ad9d7fb55ce5fcf5bbbb9235b974)) ([Sudipto Das](https://github.com/sdas13))
- Seclude configuration parse from internals ([#8801](https://github.com/serverless/serverless/pull/8801)) ([f274cd7](https://github.com/serverless/serverless/commit/f274cd7637e8171ee04bd174e786c7e07706343a)) ([Mariusz Nowak](https://github.com/medikoo))

### [2.20.1](https://github.com/serverless/serverless/compare/v2.20.0...v2.20.1) (2021-01-22)

### Bug Fixes

- **CLI:** Bring back support for referencing nested configurations ([#8804](https://github.com/serverless/serverless/issues/8804)) ([7339351](https://github.com/serverless/serverless/commit/7339351de3b9829750a94bb5a98053da7c0b7bd5)) ([Mariusz Nowak](https://github.com/medikoo))
- **Packaging:** Properly exclude devDependencies on Windows ([#8803](https://github.com/serverless/serverless/issues/8803)) ([708f6a7](https://github.com/serverless/serverless/commit/708f6a7e267e6c0c66da8bd97fdaf735909077d4)) ([Tomás Milar](https://github.com/tmilar))

## [2.20.0](https://github.com/serverless/serverless/compare/v2.19.0...v2.20.0) (2021-01-21)

### Features

- **AWS Lambda:**
  - Add support for building Docker images ([#8725](https://github.com/serverless/serverless/issues/8725)) ([789c2e3](https://github.com/serverless/serverless/commit/789c2e35ab26b7e8dc0679f36110234fb899d57c)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Add support for image config ([#8778](https://github.com/serverless/serverless/issues/8778)) ([9a55537](https://github.com/serverless/serverless/commit/9a5553742a3c3ebee03bfab5663a9183d5c228ba)) ([Piotr Grzesik](https://github.com/pgrzesik))

### Bug Fixes

- **AWS API Gateway:**
  - Correctly set `throttle` when `quota` missing ([#8780](https://github.com/serverless/serverless/pull/8780)) ([4a30bb1](https://github.com/serverless/serverless/commit/4a30bb1e5b36b52207e1bd3f3fc37e12878fb3b3)) ([Cem Enson](https://github.com/cemenson))
  - Silence timeout warning for `async: true` ([#8748](https://github.com/serverless/serverless/issues/8748)) ([0384776](https://github.com/serverless/serverless/commit/03847769cd238824cbe9ea9fdec1889645081b17)) ([Igor Omelchenko](https://github.com/MEGApixel23))
- **AWS Lambda:** Ensure function update works when image used ([#8786](https://github.com/serverless/serverless/issues/8786)) ([420e937](https://github.com/serverless/serverless/commit/420e93740f1e9bffc285559b2567379f550f28af)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **AWS CloudFront:** Fix check for deprecated `CacheBehavior` properties ([#8768](https://github.com/serverless/serverless/pull/8768)) ([c3a61e2](https://github.com/serverless/serverless/commit/c3a61e234bf73429b946e09121b48306e56e0ed5)) ([Ben Scholzen](https://github.com/DASPRiD))
- **CLI Onboarding:**
  - Ensure to not follow with project setup on existing path ([#8770](https://github.com/serverless/serverless/pull/8770)) ([293cd6d](https://github.com/serverless/serverless/commit/293cd6d0e2b595a35031eae1ae1f981a6e51e3f5)) ([Mariusz Nowak](https://github.com/medikoo))
  - Fix configuration of a new service in interactive setup ([#8770](https://github.com/serverless/serverless/pull/8770)) ([76fa62d](https://github.com/serverless/serverless/commit/76fa62da3b050260063f52cb0586f626ff6de018)) ([Mariusz Nowak](https://github.com/medikoo))

### Maintenance Improvements

- **CLI:** Seclude service config path resolution out of internals ([#8770](https://github.com/serverless/serverless/pull/8770)) ([b23bfdb](https://github.com/serverless/serverless/commit/b23bfdbf6ad915ec00fec562f8b75c40c44dd19d)) ([Mariusz Nowak](https://github.com/medikoo))
- Mark functions async in `aws/customResources` and `aws/deploy` ([#8698](https://github.com/serverless/serverless/pull/8698)) ([c45f661](https://github.com/serverless/serverless/commit/c45f66117892e6f5948274288d7dda41f96dfe85)) ([ifitzsimmons](https://github.com/ifitzsimmons))

### Templates

- Add node version constraint to `aws-nodejs-typescript` ([#8776](https://github.com/serverless/serverless/pull/8776)) ([37d5f9e](https://github.com/serverless/serverless/commit/37d5f9e74024b54955eb4d503edfefcaf0b03444)) ([Frédéric Barthelet](https://github.com/fredericbarthelet))
- Compilation target ES2019 in `aws-nodejs-typescript` ([#8774](https://github.com/serverless/serverless/pull/8774)) ([4469388](https://github.com/serverless/serverless/commit/4469388669d50193dedc6e2695789d24fe30a238)) ([Frédéric Barthelet](https://github.com/fredericbarthelet))

## [2.19.0](https://github.com/serverless/serverless/compare/v2.18.0...v2.19.0) (2021-01-15)

### Features

- **Variables:**
  - Introduce unresolvedVariablesNotificationMode ([#8710](https://github.com/serverless/serverless/issues/8710)) ([33cffc3](https://github.com/serverless/serverless/commit/33cffc3509255663c9ab94f3cd38f115d71bd1d2)) ([Gareth Jones](https://github.com/G-Rath))
  - Add support for Terraform state file parsing ([#8755](https://github.com/serverless/serverless/issues/8755)) ([461a396](https://github.com/serverless/serverless/commit/461a3965a52eb9707121700608dc8bdbafc367d1)) ([Brian Dwyer](https://github.com/bdwyertech))

### Bug Fixes

- **AWS CloudFront:** Fix deprecations visibility ([#8759](https://github.com/serverless/serverless/pull/8759)) ([6c67cd7](https://github.com/serverless/serverless/commit/6c67cd7f074ef27c9410f29b368dc7e87b5b6e2d)) ([Mariusz Nowak](https://github.com/medikoo))
- **Config Schema:** Revert to ajv v6 ([#8762](https://github.com/serverless/serverless/issues/8762)) ([d1c6568](https://github.com/serverless/serverless/commit/d1c656838f5d19dd2b1d214c30ea2f292915a5b2)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **Packaging:** Consider absolute artifact paths ([#8325](https://github.com/serverless/serverless/issues/8325)) ([#8315](https://github.com/serverless/serverless/issues/8315)) ([bcbbd47](https://github.com/serverless/serverless/commit/bcbbd47fa09b7d99d7f8da3f11150215d1203bba)) ([Robert Bragg](https://github.com/rib) & [Piotr Grzesik](https://github.com/pgrzesik))

### Maintenance Improvements

- Abstract resolution of deployment role ([#8751](https://github.com/serverless/serverless/issues/8751)) ([4afdb83](https://github.com/serverless/serverless/commit/4afdb8314b5c4718e73de733e3c4b30ae62382ba)) ([Dmitry Shirokov](https://github.com/runk))
- Cleanup `mergeIamTemplates` module ([#8736](https://github.com/serverless/serverless/issues/8736)) ([77e1a6a](https://github.com/serverless/serverless/commit/77e1a6a30246f94fcdf8ae26ca2cb8617aa1db2b)) ([Dmitry Shirokov](https://github.com/runk))
- Improve error handling scope ([#8726](https://github.com/serverless/serverless/pull/8726)) ([49aabdf](https://github.com/serverless/serverless/commit/49aabdf13d2ee74380ec2d21f57ffde494a9bf9d)) ([Mariusz Nowak](https://github.com/medikoo))
- Reconfigure `onExitPromise` setup ([#8726](https://github.com/serverless/serverless/pull/8726)) ([22a03ce](https://github.com/serverless/serverless/commit/22a03ce0d7b1581747b121f862d0818f04120958)) ([Mariusz Nowak](https://github.com/medikoo))
- Refactor `Serverless.run` to async ([#8749](https://github.com/serverless/serverless/pull/8749)) ([30015ea](https://github.com/serverless/serverless/commit/30015eafd2fb9d2e82d8f34ee8f10c1fb4e536a0)) ([Piotr Grzesik](https://github.com/pgrzesik))
- Seclude `cli/resolve-local-serverless-path` util ([#8726](https://github.com/serverless/serverless/pull/8726)) ([9d78348](https://github.com/serverless/serverless/commit/9d783482895d82a1bfdb627c4cc0debb32123d56)) ([Mariusz Nowak](https://github.com/medikoo))
- Seclude `ensureExists` util ([#8744](https://github.com/serverless/serverless/pull/8744)) ([c3f59e4](https://github.com/serverless/serverless/commit/c3f59e4d785145c2e1ba7c1324f3afedba482479)) ([Piotr Grzesik](https://github.com/pgrzesik))
- Seclude `ServerlessError` into `lib/serverless-error.js` ([#8743](https://github.com/serverless/serverless/pull/8743)) ([87790e5](https://github.com/serverless/serverless/commit/87790e50bd9c178aefd4f2ad8793c9c56fb8eb49)) ([Mariusz Nowak](https://github.com/medikoo))
- Typos in schema ([#8735](https://github.com/serverless/serverless/issues/8735)) ([2b7568a](https://github.com/serverless/serverless/commit/2b7568a960c88dda8ab2bbe1b6c8dd238fa78a51)) ([Dmitry Shirokov](https://github.com/runk))
- Seclude main error handler to standalone util ([#8726](https://github.com/serverless/serverless/pull/8726)) ([847fa34](https://github.com/serverless/serverless/commit/847fa3412d221c2ff98ab0cd9165bfc193c8a224)) ([Mariusz Nowak](https://github.com/medikoo))
- **CLI:** Seclude version output functionality out of `CLI` class ([#8741](https://github.com/serverless/serverless/pull/8741)) ([b61621a](https://github.com/serverless/serverless/commit/b61621adebb7eb33fd080db3fff13d7e9a32d99b)) ([Mariusz Nowak](https://github.com/medikoo))

### Templates

- Fix typo in `package.json` for template `aws-nodejs-typescript` ([#8754](https://github.com/serverless/serverless/issues/8754)) ([37398d0](https://github.com/serverless/serverless/commit/37398d06c582b1676c2aaa32708cfd515baf65b9)) ([Alexandre de Boutray](https://github.com/aldebout))

## [2.18.0](https://github.com/serverless/serverless/compare/v2.17.0...v2.18.0) (2021-01-07)

### Features

- **AWS API Gateway:** Move api-specific keys to `provider.apiGateway` ([#8670](https://github.com/serverless/serverless/pull/8670)) ([eacae9a](https://github.com/serverless/serverless/commit/eacae9a64da22ddf0fca8beff580a951e20d4fc0)) ([Frédéric Barthelet](https://github.com/fredericbarthelet))
- AWS `iotFleetProvisioning` event support ([#8324](https://github.com/serverless/serverless/issues/8324)) ([7d80245](https://github.com/serverless/serverless/commit/7d80245839918f10c3f5681e896ef36c657b38cb)) ([Frédéric Barthelet](https://github.com/fredericbarthelet))
- **Standalone:** Update to Node 14 for standalone binaries ([#8723](https://github.com/serverless/serverless/pull/8723)) ([5cc3be1](https://github.com/serverless/serverless/commit/5cc3be15be83b5358b78fccc9ef7e7f2a3bed45d)) ([Piotr Grzesik](https://github.com/pgrzesik))

### Bug Fixes

- **Config Schema:** Improve AWS tags validation ([#8714](https://github.com/serverless/serverless/pull/8714)) ([b093609](https://github.com/serverless/serverless/commit/b093609f7952d5a63c91e6435b6a3a7d7d09cb1a)) ([Rohit Gohri](https://github.com/rohit-gohri))

### Maintenance Improvements

- Replace `_.set` with native assignment ([#8709](https://github.com/serverless/serverless/pull/8709)) ([66aa66f](https://github.com/serverless/serverless/commit/66aa66fbfe363edeb4123d709890a7c78f74b571)) ([Frédéric Barthelet](https://github.com/fredericbarthelet))
- Upgrade "ajv" to v7 and "ajv-keywords" to v4 ([#8703](https://github.com/serverless/serverless/issues/8703)) ([1af73ba](https://github.com/serverless/serverless/commit/1af73bacdf01e5dc855da59387ab36085b2b78a1)) ([Frédéric Barthelet](https://github.com/fredericbarthelet))
- Use ajv formats ([036698c](https://github.com/serverless/serverless/commit/036698ca5b46dc27a2844114813812a83f64813e)) ([Piotr Grzesik](https://github.com/pgrzesik))
- Upgrade "js-yaml" to v4 ([#8708](https://github.com/serverless/serverless/pull/8708)) ([b143383](https://github.com/serverless/serverless/commit/b14338332c86a4461d0e1c564c740c1f6a29fb4a)) ([Mariusz Nowak](https://github.com/medikoo))
- Use @serverless/utils for cloudformationSchema ([#8705](https://github.com/serverless/serverless/issues/8705)) ([2efc357](https://github.com/serverless/serverless/commit/2efc3570c953cff04a22c8690f510532d5650eac)) ([Frédéric Barthelet](https://github.com/fredericbarthelet))

## [2.17.0](https://github.com/serverless/serverless/compare/v2.16.1...v2.17.0) (2020-12-30)

### Features

- **AWS Deploy:** Improve function version hashing algorithm ([#8661](https://github.com/serverless/serverless/issues/8661)) ([ef53050](https://github.com/serverless/serverless/commit/ef530506d5044ab3312c829838bb29cfcd2c889f)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **AWS Lambda:** Support referencing images with tags ([#8683](https://github.com/serverless/serverless/issues/8683)) ([68b7ed5](https://github.com/serverless/serverless/commit/68b7ed5089f9226c1dbe3b992b93afdcf2015736)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **AWS HTTP API:** Expose HTTP API in CloudFormation stack outputs ([#8664](https://github.com/serverless/serverless/issues/8664)) ([f9c8677](https://github.com/serverless/serverless/commit/f9c8677eccdfe14382c7e90079abce9f7bfed866)) ([Santhos Baala, Ramalingam Santhanakrishnan](https://github.com/captainsano))
- **Config Schema:** Validate extensions against collisions with existing properties ([#8655](https://github.com/serverless/serverless/issues/8655)) ([7266599](https://github.com/serverless/serverless/commit/7266599a7dcfcb96cdfcb73a95c3d162fe6f3a1f)) ([Frédéric Barthelet](https://github.com/fredericbarthelet))
- Support `--context` and `--contextPath` at `invoke` command ([#8652](https://github.com/serverless/serverless/issues/8652)) ([ff253e3](https://github.com/serverless/serverless/commit/ff253e32dd5e9c17f46f5a359ebfb9007b6ffa7d)) ([lewgordon](https://github.com/lewgordon))

### Bug Fixes

- **AWS CloudFront:** Ensure to describe resolved stage in comment ([#8685](https://github.com/serverless/serverless/issues/8685)) ([120bfb7](https://github.com/serverless/serverless/commit/120bfb7c0273e2ddd120a4311ee736694568fc53)) ([Mariusz Nowak](https://github.com/medikoo))
- **Variables:** Fix handling of `null` in deep property resolution ([#8165](https://github.com/serverless/serverless/issues/8165)) ([eb11e6d](https://github.com/serverless/serverless/commit/eb11e6d92b99687529fed708d3f7f5a28ef1c027)) ([Antoine Pham](https://github.com/MystK) & [Piotr Grzesik](https://github.com/pgrzesik))
- **AWS Lambda:** Ensure layer permissions are retained with layer itself ([#8688](https://github.com/serverless/serverless/issues/8688)) ([bf418ac](https://github.com/serverless/serverless/commit/bf418ac6ca14f3a5570998f5fecf2bfd8a3d12a6)) ([raym0nd93](https://github.com/raym0nd93) & [Piotr Grzesik](https://github.com/pgrzesik))

### Templates

- Update `aws-nodejs-typescript` template ([#8646](https://github.com/serverless/serverless/issues/8646)) ([c9db035](https://github.com/serverless/serverless/commit/c9db035266db23518011a4b7457319add0c00994)) ([Frédéric Barthelet](https://github.com/fredericbarthelet))
- Upgrade to avoid using deprecated functionality ([#8677](https://github.com/serverless/serverless/issues/8677)) ([3c5e497](https://github.com/serverless/serverless/commit/3c5e497116bec410b16f4a752c30e19b856df898)) ([Piotr Grzesik](https://github.com/pgrzesik))

### [2.16.1](https://github.com/serverless/serverless/compare/v2.16.0...v2.16.1) (2020-12-22)

### Bug Fixes

- **Packaging:** Exclude `.env` files only when `useDotenv` is set ([#8648](https://github.com/serverless/serverless/pull/8648)) ([537fcac](https://github.com/serverless/serverless/commit/537fcac7597f0c6efbae7a5fc984270a78a2a53a)) ([Piotr Grzesik](https://github.com/pgrzesik))

## [2.16.0](https://github.com/serverless/serverless/compare/v2.15.0...v2.16.0) (2020-12-18)

### Features

- **AWS ALB:** Recognize `path` as optional condition ([#8571](https://github.com/serverless/serverless/issues/8571)) ([3632e0e](https://github.com/serverless/serverless/commit/3632e0ee09945ed5f293779a68409cb297c7d0cc)) ([Jin](https://github.com/jinhong-))

### Bug Fixes

- **AWS Deploy:**
  - Fix resolution of first deploy event ([#8632](https://github.com/serverless/serverless/issues/8632)) ([9bc1060](https://github.com/serverless/serverless/commit/9bc1060dceb6a155abdb27364a9d0061b4d95983)) ([Mariusz Nowak](https://github.com/medikoo))
  - Allow to disable creation of default bucket policy ([#6923](https://github.com/serverless/serverless/issues/6923)) ([919b95f](https://github.com/serverless/serverless/commit/919b95f4911b29d5e05fc3adaa097ad7a22b4c18)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **Packaging:**
  - Add exec bit for packaged files on Windows ([#8615](https://github.com/serverless/serverless/issues/8615)) ([c864fbd](https://github.com/serverless/serverless/commit/c864fbd4826de27d2796e394b0a100c8d3add33e)) ([Łukasz Jendrysik](https://github.com/scadu))
  - Do not exclude layer paths when packaging a layer ([#8602](https://github.com/serverless/serverless/issues/8602)) ([86b366a](https://github.com/serverless/serverless/commit/86b366a5d3b6b0bd00b73c71d0c1a0661ff27ce2)) ([Juanjo Diaz](https://github.com/juanjodiaz))
  - Ensure that .env files are excluded from package ([#8566](https://github.com/serverless/serverless/issues/8566)) ([8791cda](https://github.com/serverless/serverless/commit/8791cdacb75c84a2e08c5639abf769e915968288)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Expose meaningfully file access errors ([#8582](https://github.com/serverless/serverless/issues/8582)) ([13c7b7b](https://github.com/serverless/serverless/commit/13c7b7bc97aab4d70e178fdb25af1b2c3b85ac5b)) ([Łukasz Jendrysik](https://github.com/scadu))
- **AWS Lambda:** Improve "image" property validation ([#8639](https://github.com/serverless/serverless/pull/8639)) ([a8be1d1](https://github.com/serverless/serverless/commit/a8be1d1776a26b033d821d70e99ad654a39a4158)) ([Mariusz Nowak](https://github.com/medikoo))
- **Standalone:** Fix upgrade command ([#8608](https://github.com/serverless/serverless/pull/8608)) ([f23e50b](https://github.com/serverless/serverless/commit/f23e50b16e50559596fbd9561dfb4ced82973814)) ([Mariusz Nowak](https://github.com/medikoo))

### Maintenance Improvements

- **AWS Deploy:** Follow AWS naming in stack deploy action types ([#8632](https://github.com/serverless/serverless/issues/8632)) ([a238a9b](https://github.com/serverless/serverless/commit/a238a9bc902a1443007848c65d9a179ec78e5c8f)) ([Mariusz Nowak](https://github.com/medikoo))
- Convert to native Promise and async/await ([#8593](https://github.com/serverless/serverless/issues/8593)) ([84d423d](https://github.com/serverless/serverless/commit/84d423d3be9d89475a22f29f808d506fb4f56d3c)) ([Juanjo Diaz](https://github.com/juanjodiaz))
- Normalize module path ([#8620](https://github.com/serverless/serverless/pull/8620)) ([Mariusz Nowak](https://github.com/medikoo))
- Remove dependency to stream-promise ([#8601](https://github.com/serverless/serverless/issues/8601)) ([ca697f3](https://github.com/serverless/serverless/commit/ca697f3911aec5a0bb0e02ce5bfdef5bbd4cc00a)) ([Juanjo Diaz](https://github.com/juanjodiaz))
- Remove irrelevant fs modules ([#8588](https://github.com/serverless/serverless/issues/8588)) ([c1907a2](https://github.com/serverless/serverless/commit/c1907a2dde7531dab8bff665434ee8a72397c2ca)) ([Mariusz Nowak](https://github.com/medikoo))
- Remove unused modules ([#8598](https://github.com/serverless/serverless/issues/8598)) ([d102a39](https://github.com/serverless/serverless/commit/d102a3984abfe5c014c4adafa8abf2ea8edfd336)) ([Juanjo Diaz](https://github.com/juanjodiaz))

## [2.15.0](https://github.com/serverless/serverless/compare/v2.14.0...v2.15.0) (2020-12-04)

### Features

- **AWS Lambda:**
  - Basic container image support ([#8572](https://github.com/serverless/serverless/issues/8572)) ([c0ea4c1](https://github.com/serverless/serverless/commit/c0ea4c14615f90e93baa1dfccfe5b309680b42b1)) ([Mariusz Nowak](https://github.com/medikoo))
  - Increase memory limits per changes on AWS side ([#8569](https://github.com/serverless/serverless/issues/8569)) ([c5ae979](https://github.com/serverless/serverless/commit/c5ae9798d2feca03cbcf2290661a08442c2f1c7d)) ([Piotr Grzesik](https://github.com/pgrzesik))

### Bug Fixes

- **AWS API Gateway:** Fix `integration` schema ([#8574](https://github.com/serverless/serverless/issues/8574)) ([09231c0](https://github.com/serverless/serverless/commit/09231c059abdbab1f9a6ac371b8dc6e0784e72da)) ([Mariusz Nowak](https://github.com/medikoo))

## [2.14.0](https://github.com/serverless/serverless/compare/v2.13.0...v2.14.0) (2020-12-01)

### Features

- **AWS SQS:** Support `maximumBatchingWindow` ([#8555](https://github.com/serverless/serverless/issues/8555)) ([ffde506](https://github.com/serverless/serverless/commit/ffde506db76b15a873e88aded7cfa32eb3382c6c)) ([Qi Xi](https://github.com/xiqi))

### Bug Fixes

- **AWS IAM:** Prevent function logs write access with disabled logging ([#8561](https://github.com/serverless/serverless/issues/8561)) ([ee18167](https://github.com/serverless/serverless/commit/ee1816772e4d3db8acda779f622904500d8072ec)) ([Ashish Sharma](https://github.com/as19ish))
- **Config Schema:** Fix configuration of common properties in `resources` ([#8553](https://github.com/serverless/serverless/issues/8553)) ([9399f2b](https://github.com/serverless/serverless/commit/9399f2b89c8a841d1d7d96a22a8de640d8214479)) ([Frédéric Barthelet](https://github.com/fredericbarthelet))

## [2.13.0](https://github.com/serverless/serverless/compare/v2.12.0...v2.13.0) (2020-11-25)

### Features

- **CLI:**
  - Conditional support for `.env` files ([#8413](https://github.com/serverless/serverless/issues/8413)) ([d1a22c8](https://github.com/serverless/serverless/commit/d1a22c85f2220a2f4691255fb3b9961aeaa4abcb)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Improve general `--help` and remove `--verbose` option ([#8532](https://github.com/serverless/serverless/issues/8532)) ([4287494](https://github.com/serverless/serverless/commit/42874946fc7ff92323d3ce5643415449122d2f38)) ([Vinod Tahelyani](https://github.com/vinod-tahelyani))

### Bug Fixes

- **AWS Deploy:** Improve S3 bucket policy security ([#8542](https://github.com/serverless/serverless/issues/8542)) ([2a9b57b](https://github.com/serverless/serverless/commit/2a9b57b62074d3e58f987aefb7888e14dfc35dce)) ([Ashish Sharma](https://github.com/as19ish))
- **Config Schema:**
  - Recognize API Gateway resource policy shorthands ([#8506](https://github.com/serverless/serverless/issues/8506)) ([b7901cd](https://github.com/serverless/serverless/commit/b7901cdb77cb2c81dee62cb614d39d5d2fc824ff)) ([Frédéric Barthelet](https://github.com/fredericbarthelet))
  - Recognize string format of `service` ([#8537](https://github.com/serverless/serverless/issues/8537)) ([6c6881c](https://github.com/serverless/serverless/commit/6c6881c853d9a42ed3c99f7c7acaa7cb98bd0a1b)) ([Frédéric Barthelet](https://github.com/fredericbarthelet))

### Templates

- **`aws-nodejs-typescript`:** Import type definitions from [`@serverless/typescript`](https://github.com/serverless/typescript/) project ([#8543](https://github.com/serverless/serverless/issues/8543)) ([fef389b](https://github.com/serverless/serverless/commit/fef389b770a3f09431aa761dc98da8cd384eec3f)) ([Frédéric Barthelet](https://github.com/fredericbarthelet))

### Maintenance Improvements

- Refactor some functions to native promises ([#8533](https://github.com/serverless/serverless/issues/8533)) ([06f6c6d](https://github.com/serverless/serverless/commit/06f6c6d28ee54055ae4a39686ce54e4738d9e8b0)) ([Graham McGregor](https://github.com/Graham42))

## [2.12.0](https://github.com/serverless/serverless/compare/v2.11.1...v2.12.0) (2020-11-20)

### Features

- **AWS HTTP API:** Support metrics ([#8510](https://github.com/serverless/serverless/issues/8510)) ([3feafbc](https://github.com/serverless/serverless/commit/3feafbceb5777904ea19aab1765c85935d5aa904)) ([Baptiste Guerin](https://github.com/BaptistG))8496

### Bug Fixes

- **Packaging:** Fix compatibility with npm v7.0 ([#8505](https://github.com/serverless/serverless/issues/8505)) ([fdd962b](https://github.com/serverless/serverless/commit/fdd962baa53a7471d33ad041e927c705051b343a)) ([Dmitry Gorbash](https://github.com/dgorbash))
- **AWS API Gateway:** Fix `usagePlan.throttle` handling ([#8472](https://github.com/serverless/serverless/issues/8472)) ([04e18cb](https://github.com/serverless/serverless/commit/04e18cbebf70ca6fd0534fcee5544de8f6569ed3)) ([andreizet](https://github.com/andreizet))
- **CLI:** Ensure to not fallback to Framework on components run error ([#8530](https://github.com/serverless/serverless/issues/8530)) ([15332c5](https://github.com/serverless/serverless/commit/15332c55525b91dc0ad11d903789581fb5104b64)) ([Mariusz Nowak](https://github.com/medikoo))

- **Templates:** Fix service rename ([#8508](https://github.com/serverless/serverless/issues/8508)) ([8c0d892](https://github.com/serverless/serverless/commit/8c0d89255e5f3bf2835966fde2f441b828607106)) ([Mariusz Nowak](https://github.com/medikoo))

### Templates

- **`aws-nodejs-typescript`:**
  - Upgrade ([#8496](https://github.com/serverless/serverless/issues/8496)) ([786809e](https://github.com/serverless/serverless/commit/786809e262b56490a78a923b0b031378badb18c0)) ([Chris Schuld](https://github.com/cbschuld))
  - Fix tooling options ([#8501](https://github.com/serverless/serverless/issues/8501)) ([cc103f1](https://github.com/serverless/serverless/commit/cc103f147eddcb29e38937326cc551473925e535)) ([David ALLIX](https://github.com/webda2l))
- **`aws-go-mod`:** Fix cleanup ([#8507](https://github.com/serverless/serverless/issues/8507)) ([2791c71](https://github.com/serverless/serverless/commit/2791c7142f795ddab7da1b8cbfa7588f9ae4896d)) ([Fukaya Temma](https://github.com/Pranc1ngPegasus))

### [2.11.1](https://github.com/serverless/serverless/compare/v2.11.0...v2.11.1) (2020-11-09)

### Bug Fixes

- **Config Schema:** Fix multiple event types support in `defineFunctionEventProperties` schema extension method ([#8486](https://github.com/serverless/serverless/issues/8486)) ([e32b771](https://github.com/serverless/serverless/commit/e32b7714253108f9078d2218e68c5994f20cde64)) ([Frédéric Barthelet](https://github.com/fredericbarthelet))

## [2.11.0](https://github.com/serverless/serverless/compare/v2.10.0...v2.11.0) (2020-11-06)

### Features

- **ConfigSchema:** `defineFuntionEventProperties` schema extension method ([#8471](https://github.com/serverless/serverless/issues/8471)) ([b5abfd8](https://github.com/serverless/serverless/commit/b5abfd8554a2641ca92c16db4cdd20c08be4001e)) ([Frédéric Barthelet](https://github.com/fredericbarthelet))
- Deprecate `service` object notation ([#8466](https://github.com/serverless/serverless/issues/8466)) ([c0a2ecf](https://github.com/serverless/serverless/commit/c0a2ecf453fa82d46bf2fda34708864bc440203d)) ([A. Singh](https://github.com/A-5ingh))
- **Analytics:**
  - Distinguish different standalone installations ([#8474](https://github.com/serverless/serverless/issues/8474)) ([5f81f58](https://github.com/serverless/serverless/commit/5f81f58b3af615205fb7b0d92c3828ad723a1595)) ([Mariusz Nowak](https://github.com/medikoo))
  - Report tabtab autocomplete installations ([#8474](https://github.com/serverless/serverless/issues/8474)) ([04b868f](https://github.com/serverless/serverless/commit/04b868fd3b143c27148e3e1cbbd901c2b19944e1)) ([Mariusz Nowak](https://github.com/medikoo))

### Bug Fixes

- Ensure to inspect configuration after it's fully resolved ([#8482](https://github.com/serverless/serverless/issues/8482)) ([f60fb55](https://github.com/serverless/serverless/commit/f60fb55a0b60603039d92d7467d0b231e247c819)) ([Mariusz Nowak](https://github.com/medikoo))
- **CLI:** Fix handling of command options in help display ([#8476](https://github.com/serverless/serverless/issues/8476)) ([2fffb16](https://github.com/serverless/serverless/commit/2fffb168bc7f957ed9e8e048fd08dfb9669e8eca)) ([Mariusz Nowak](https://github.com/medikoo))
- **Standalone:** Recognize Windows as non auto updatable platform ([#8474](https://github.com/serverless/serverless/issues/8474)) ([4fc29a5](https://github.com/serverless/serverless/commit/4fc29a57c4b675b2751c1e17d47e45904653f658)) ([Mariusz Nowak](https://github.com/medikoo))

## [2.10.0](https://github.com/serverless/serverless/compare/v2.9.0...v2.10.0) (2020-11-03)

### Features

- **Config Schema:**
  - Schema for AWS `s3` event ([#8330](https://github.com/serverless/serverless/issues/8330)) ([61d8ee9](https://github.com/serverless/serverless/commit/61d8ee9884cdee652fae131fed1e753301a351bf)) ([Oz Weiss](https://github.com/thewizarodofoz))
  - `defineFunctionProperties` schema extension method ([#8462](https://github.com/serverless/serverless/issues/8462)) ([5003bbf](https://github.com/serverless/serverless/commit/5003bbf983e7218c673a94a7042ca118aa0ae431)) ([Luis Helder](https://github.com/luislhl))

### Bug Fixes

- **Config Schema:**
  - Support empty string as environment variables ([#8468](https://github.com/serverless/serverless/issues/8468)) ([ff9db3e](https://github.com/serverless/serverless/commit/ff9db3e7bd0e4cd1261984e048373afc843eb053)) ([Mariusz Nowak](https://github.com/medikoo))
  - Ensure schema related config normalization is pursued also with validation turned off ([#8460](https://github.com/serverless/serverless/issues/8460)) ([df1b8a9](https://github.com/serverless/serverless/commit/df1b8a9433615c9c6efdff4dcef1f5477ea46d8a)) ([Mariusz Nowak](https://github.com/medikoo))
- Support log retention at custom resource lambda log groups ([#8456](https://github.com/serverless/serverless/issues/8456)) ([4ce9037](https://github.com/serverless/serverless/commit/4ce9037f8c8416715204f431af65767b3c48e1c7)) ([Filip Pýrek](https://github.com/FilipPyrek))
- **Analytics:** Ensure to send payload when having all meta ([#8467](https://github.com/serverless/serverless/issues/8467)) ([03859c0](https://github.com/serverless/serverless/commit/03859c04720f9071d0590b5d0ad1fa0e2c6770b3)) ([Mariusz Nowak](https://github.com/medikoo))

### Maintenance Improvements

- Remove `that = this` pattern ([#8463](https://github.com/serverless/serverless/issues/8463)) ([4ae192c](https://github.com/serverless/serverless/commit/4ae192cbfeb534d09af5b29ef7a1ed3f7700332f)) ([telenord](https://github.com/telenord))
- **Config Schema:**
  - Run schema validation only in service context (([#8460](https://github.com/serverless/serverless/issues/8460)) ([c271218](https://github.com/serverless/serverless/commit/c2712183a5dae0726c56456d8b3b790e7c597052)) ([Mariusz Nowak](https://github.com/medikoo))
  - Ensure config modifications happen after its validation ([#8460](https://github.com/serverless/serverless/issues/8460)) ([214768b](https://github.com/serverless/serverless/commit/214768b83ab14495be75ac87f221a31ffd60c88b)) ([Mariusz Nowak](https://github.com/medikoo))
- **AWS Alexa:** Ensure to log deprecation at initialization stage ([#8467](https://github.com/serverless/serverless/issues/8467)) ([a5a1a23](https://github.com/serverless/serverless/commit/a5a1a230a5714fc2859773077d57eba6d654af74)) ([Mariusz Nowak](https://github.com/medikoo))
- **AWS API Gateway:** Ensure to log deprecation at initialization stage ([#8467](https://github.com/serverless/serverless/issues/8467)) ([b6d033a](https://github.com/serverless/serverless/commit/b6d033a044e722f9cd0bd751c4067bf05aa50558)) ([Mariusz Nowak](https://github.com/medikoo))
- **AWS CloudFront:** Ensure to log deprecation at initialization stage ([#8467](https://github.com/serverless/serverless/issues/8467)) ([61f90a3](https://github.com/serverless/serverless/commit/61f90a362d33425dc10d4c5bd851132ec5779e8e)) ([Mariusz Nowak](https://github.com/medikoo))
- Ensure to log deprecation at initialization stage ([#8467](https://github.com/serverless/serverless/issues/8467)) ([1b26075](https://github.com/serverless/serverless/commit/1b26075fb51c71dd169c4800822842f614465388)) ([Mariusz Nowak](https://github.com/medikoo))

## [2.9.0](https://github.com/serverless/serverless/compare/v2.8.0...v2.9.0) (2020-10-29)

### Features

- Opt-in auto update feature for global (standalone and npm) installations. Turn on via `sls config --autoupdate` ([#8428](https://github.com/serverless/serverless/issues/8428)) ([e3f4546](https://github.com/serverless/serverless/commit/e3f454680e528e51a61f4e203b5ec72e8947f0b1)) ([Mariusz Nowak](https://github.com/medikoo))
- **AWS API Gateway:** Improve API Gateway API naming, deprecate `{stage}-{service}` format in favor of `{service}-{stage}` with suggestion to opt-in to new way ([#8339](https://github.com/serverless/serverless/issues/8339)) ([8566135](https://github.com/serverless/serverless/commit/85661353410d53a94c1d04f1a5c86f1fa456b3ff)) ([Fabian Schneider](https://github.com/fabsrc))
- **AWS CloudFront:** Switch from `ForwardedValues` to cache policies ([#8381](https://github.com/serverless/serverless/issues/8381)) ([479727e](https://github.com/serverless/serverless/commit/479727e1f4363cef1dd2fa1c20bdb9f7f8493838)) ([Frédéric Barthelet](https://github.com/fredericbarthelet))
- **AWS Deploy:** Update according to shifted CloudFormation limits ([#8433](https://github.com/serverless/serverless/issues/8433)) ([7e9b2ea](https://github.com/serverless/serverless/commit/7e9b2eac74cd9b720ac1aba4e01a31f06476165c)) ([Frédéric Barthelet](https://github.com/fredericbarthelet))
- **Analytics:**
  - Distinguish between npm and other global installation types ([#8428](https://github.com/serverless/serverless/issues/8428)) ([7cc898c](https://github.com/serverless/serverless/commit/7cc898cd0f8ed6cdb63664bed10ecfff74827084))([Mariusz Nowak](https://github.com/medikoo))
  - Report `isAutoUpdateEnabled` ([#8428](https://github.com/serverless/serverless/issues/8428)) ([48a3e11](https://github.com/serverless/serverless/commit/48a3e11f333c4e45a58f6810c1f3137fa953f2b8))([Mariusz Nowak](https://github.com/medikoo))

### Bug Fixes

- **AWS Deploy:** Fix handling of AWS SDK numeric error codes ([#8412](https://github.com/serverless/serverless/issues/8412)) ([6e62e1c](https://github.com/serverless/serverless/commit/6e62e1c5e8f66237e45e83d667e6b50bfb8ea753)) ([Ed Holland](https://github.com/edholland))
- **Config Schema:**
  - Ensure to validate `provider` as set in config file ([#8450](https://github.com/serverless/serverless/issues/8450)) ([b04ab55](https://github.com/serverless/serverless/commit/b04ab55fabd193b879244718ed87047ec961904c))([Mariusz Nowak](https://github.com/medikoo))
  - Fix IAM Policy resource reference schema ([#8453](https://github.com/serverless/serverless/issues/8453)) ([85f823c](https://github.com/serverless/serverless/commit/85f823cf46713b110d0f70892e6130315e1d3972))([Mariusz Nowak](https://github.com/medikoo))
- **Templates:** Ensure service is renamed also in eventual `package-lock.json` ([#8409](https://github.com/serverless/serverless/issues/8409)) ([78f159b](https://github.com/serverless/serverless/commit/78f159b4326f7eb092895bbd11813e470c146dc4)) ([Mark Tse](https://github.com/neverendingqs))

### Maintenance Improvements

- **Standalone:** Seclude standalone utils ([#8428](https://github.com/serverless/serverless/issues/8428)) ([5fcc54a](https://github.com/serverless/serverless/commit/5fcc54ae2aae9aea40d0fec8d42a86ebd21b5a76))([Mariusz Nowak](https://github.com/medikoo))
- **`blluebird` removal:**
  - Replace `BbPromise.props` with `Promise.all` ([#8414](https://github.com/serverless/serverless/issues/8414)) ([2d6824c](https://github.com/serverless/serverless/commit/2d6824cde531ba56758f441b39b5ab018702e866)) ([Piotr Grzesik](https://github.com/pgrzesik))

## [2.8.0](https://github.com/serverless/serverless/compare/v2.7.0...v2.8.0) (2020-10-16)

### Features

- **Config Schema:** Schema for `provider` props of AWS `http` event ([#8383](https://github.com/serverless/serverless/issues/8383)) ([e51e0f2](https://github.com/serverless/serverless/commit/e51e0f22da4625a65e5d7fd7bf3b4b1d5b46dd91)) ([Oz Weiss](https://github.com/thewizarodofoz))

### Bug Fixes

- **Config Schema:** Do not mark `layers[].path` as required ([#8398](https://github.com/serverless/serverless/issues/8398)) (([0394025](https://github.com/serverless/serverless/commit/03940254385e138eb40f2f25bd56fcdbee0c3a22)) ([Mariusz Nowak](https://github.com/medikoo))
- **Config Schema:** Fix AWS `stream` event `consumer` schema([#8405](https://github.com/serverless/serverless/issues/8405)) ([b0fe67d](https://github.com/serverless/serverless/commit/b0fe67d8466c97f0be045d87780e5e78f6611e7b)) ([Mariusz Nowak](https://github.com/medikoo))

### Maintenance Improvements

- **Config Schema:** Convert `oneOf` to more optimal `anyOf` ([#8405](https://github.com/serverless/serverless/issues/8405)) ([2c874e2](https://github.com/serverless/serverless/commit/2c874e22c97fe35290b14736df4b63097d3a9d50)) ([Mariusz Nowak](https://github.com/medikoo))

## [2.7.0](https://github.com/serverless/serverless/compare/v2.6.0...v2.7.0) (2020-10-13)

### Features

- **AWS Websocket:** Support CF intrinsic functions at `arn` ([#8335](https://github.com/serverless/serverless/issues/8335)) ([9303d8e](https://github.com/serverless/serverless/commit/9303d8ecd46059121082c3308e5fe5385e0be38e)) ([Raul Zaldana](https://github.com/zaldanaraul))
- **Config Schema:** Schema for AWS `functions[]` async invocation related properties([#8385](https://github.com/serverless/serverless/issues/8385)) ([719fa3a](https://github.com/serverless/serverless/commit/719fa3a3bf8e5d5dfa135a8225519fc77b719c8e)) ([Frédéric Barthelet](https://github.com/fredericbarthelet))
- **AWS Local Invocation:** Randomize `context.awsRequestId` ([#8380](https://github.com/serverless/serverless/issues/8380)) ([6a81137](https://github.com/serverless/serverless/commit/6a81137406fd2a2283663af93596ba79d23e38ef)) ([Frédéric Barthelet](https://github.com/fredericbarthelet))

### Bug Fixes

- **AWS Deploy:**
  - Fix resolution of CloudFormation error in stack monitoring logic ([#8388](https://github.com/serverless/serverless/issues/8388)) ([4579045](https://github.com/serverless/serverless/commit/4579045ed12ad0ad44c38df7e38f892ebbe5263d)) ([Mariusz Nowak](https://github.com/medikoo))
  - Ensure right handling for overriden (by plugin) `package.artifact` ([#8351](https://github.com/serverless/serverless/issues/8351)) ([661caad](https://github.com/serverless/serverless/commit/661caad22d4d1154aa197bbfc95948ae74bbc1aa)) ([Ryan Roemer](https://github.com/ryan-roemer))
- **AWS Stream:** Fix support for lambdas with provisioned concurrency ([#8342](https://github.com/serverless/serverless/issues/8342)) ([c382d86](https://github.com/serverless/serverless/commit/c382d869a84a5c7c84fd827eb815e0b881737c69)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **AWS S3:** Fix handling of lambda removal permissions ([#8384](https://github.com/serverless/serverless/issues/8384)) ([c2d40ea](https://github.com/serverless/serverless/commit/c2d40ea63baa930dad31bf6950c25852ccd8adf4)) ([Oz Weiss](https://github.com/thewizarodofoz))
- **Config Schema:** Fix API Gateway authorizer schema ([#8389](https://github.com/serverless/serverless/issues/8389)) ([f166546](https://github.com/serverless/serverless/commit/f1665460d4bba7562ad88ecf7a471949bfd1baa4)) ([Mariusz Nowak](https://github.com/medikoo))
- **AWS Local Invocation:** Ensure `IS_LOCAL` env variable in docker ([#8372](https://github.com/serverless/serverless/issues/8372)) ([21babec](https://github.com/serverless/serverless/commit/21babec2ce5d56ecb7ddaad3e89387f6186cc52e)) ([Marek Piotrowski](https://github.com/marekpiotrowski))

## [2.6.0](https://github.com/serverless/serverless/compare/v2.5.0...v2.6.0) (2020-10-09)

### Features

- **Config Schema:** Schema for AWS `http` event ([#8301](https://github.com/serverless/serverless/issues/8301)) ([f235041](https://github.com/serverless/serverless/commit/f235041d0b94e21cf07e11c4b818f44670ff39ae)) ([Oz Weiss](https://github.com/thewizarodofoz))

### Bug Fixes

- **Config Schema:**
  - Revert invalid `oneOf` based validation ([#8376](https://github.com/serverless/serverless/issues/8376)) ([a9b28b6](https://github.com/serverless/serverless/commit/a9b28b6d7f703ce29e92d05fc129a2a3b5fbce2a)) ([Mariusz Nowak](https://github.com/medikoo))
  - Bring back non-array supported variants ([#8366](https://github.com/serverless/serverless/issues/8366)) ([244ae11](https://github.com/serverless/serverless/commit/244ae111c19d6e39b121ac387a38747823af6723)) ([Mariusz Nowak](https://github.com/medikoo))
- Ensure to preserve `undefined` valued service config properties as `undefined` after normalizing for schema ([#8374](https://github.com/serverless/serverless/issues/8374)) ([2e26e07](https://github.com/serverless/serverless/commit/2e26e07f921575dbb10c049eaa7a864867e696c6)) ([Mariusz Nowak](https://github.com/medikoo))

## [2.5.0](https://github.com/serverless/serverless/compare/v2.4.0...v2.5.0) (2020-10-07)

### Features

- **Config Schema:**
  - Schema for AWS `provider` properties ([#8297](https://github.com/serverless/serverless/issues/8297)) ([38c2047](https://github.com/serverless/serverless/commit/38c204762cbe16b00d102fa71409c3c8ba22220b)) ([Frédéric Barthelet](https://github.com/fredericbarthelet))
  - Schema for `layers` ([#8299](https://github.com/serverless/serverless/issues/8299)) ([4168dc1](https://github.com/serverless/serverless/commit/4168dc1f303148012f2027b6fbcbd686749a9357)) ([Oz Weiss](https://github.com/thewizarodofoz))
  - Schema for `provider.logs.restApi` ([#8309](https://github.com/serverless/serverless/issues/8309)) ([dd9a011](https://github.com/serverless/serverless/commit/dd9a011f6073d33db9043f102e0cce84743a8a6b)) ([Frédéric Barthelet](https://github.com/fredericbarthelet))
  - Recognize `Fn::Transport` at `resoures.Resources` ([#8337](https://github.com/serverless/serverless/issues/8337)) ([11a9d37](https://github.com/serverless/serverless/commit/11a9d37f6e89d203b1bced2a30c89d40e9aae041)) ([Raul Zaldana](https://github.com/zaldanaraul))
- Imply a safe primitives coercion on service configuration properties ([#8319](https://github.com/serverless/serverless/issues/8319)) ([6d1ee37](https://github.com/serverless/serverless/commit/6d1ee37004509ccb46737f2a87c6b74799de2cb7)) ([Mariusz Nowak](https://github.com/medikoo))
- Coerce service configuration primitive values to arrays, when array is expected ([#8319](https://github.com/serverless/serverless/issues/8319)) ([a6ff964](https://github.com/serverless/serverless/commit/a6ff964d84834985f485ae657e8fc5ecd6801958)) ([Mariusz Nowak](https://github.com/medikoo))
- **AWS Deploy:** Retry retryable SDK errors in custom resources ([#8338](https://github.com/serverless/serverless/issues/8338)) ([a3ebc01](https://github.com/serverless/serverless/commit/a3ebc01f2bcd6484cfd790bd576bc12962f1b2ff)) ([Pratik Prajapati](https://github.com/pratik-vii))

### Bug Fixes

- **Config Schema:**
  - Fix `cloudFront` event `behavior` schema ([#8308](https://github.com/serverless/serverless/issues/8308)) ([5b740f6](https://github.com/serverless/serverless/commit/5b740f6e1890b105e6aa7d931aed834dd30afb7e)) ([Johannes Edelstam](https://github.com/jede))
  - Fix `Fn::Join` delimiter length ([#8349](https://github.com/serverless/serverless/issues/8349)) ([faa1dce](https://github.com/serverless/serverless/commit/faa1dce9eef4384cda07c8553a0d972c06be0e2f)) ([Geoff Baskwill](https://github.com/glb))
  - Fix `provider.tags` schema ([#8314](https://github.com/serverless/serverless/issues/8314)) ([fc34140](https://github.com/serverless/serverless/commit/fc34140f4ec03958564a5868b339c40056f6b04e)) ([Noel Martin Llevares](https://github.com/dashmug))
  - Recognize `sns` event `displayName` property as optional ([#8323](https://github.com/serverless/serverless/issues/8323)) ([a020a4a](https://github.com/serverless/serverless/commit/a020a4a683f7c5ef3625fc52cb319300b9e302d2)) ([Frédéric Barthelet](https://github.com/fredericbarthelet))
- **Variables:**
  - Fix handling of circular object references ([#8343](https://github.com/serverless/serverless/issues/8343)) ([fd451ca](https://github.com/serverless/serverless/commit/fd451caf901f3bf69a872437643fa38d5eda8924)) ([Mariusz Nowak](https://github.com/medikoo))
  - Fix support for `${self:}` ([#8343](https://github.com/serverless/serverless/issues/8343)) ([ac34110](https://github.com/serverless/serverless/commit/ac3411085246c112db7aca7c5ea6354a0ab7bd08)) ([Mariusz Nowak](https://github.com/medikoo))
- **AWS API Gateway:** Fix resolution of request parameters `required` value ([#8329](https://github.com/serverless/serverless/issues/8329)) ([d2fb696](https://github.com/serverless/serverless/commit/d2fb696ebd25b1b99bd6043523e2c0051bfbac3d)) ([Oz Weiss](https://github.com/thewizarodofoz))
- **AWS Credentials:** Recognize AWS_DEFAULT_PROFILE env variable ([#8354](https://github.com/serverless/serverless/issues/8354)) ([261c16f](https://github.com/serverless/serverless/commit/261c16fc594baf6e7f1884304e722ca23e26286c)) ([Marek Piotrowski](https://github.com/marekpiotrowski))
- **AWS IAM:** Report missing `RoleName` on custom role ([#8219](https://github.com/serverless/serverless/issues/8219)) ([60cfa75](https://github.com/serverless/serverless/commit/60cfa75d6b5ce5b41b70739612d1f128abf05316)) ([David Wells](https://github.com/DavidWells))

## [2.4.0](https://github.com/serverless/serverless/compare/v2.3.0...v2.4.0) (2020-09-30)

### Features

- **Config Schema:**
  - Schema for AWS `alb` event ([#8291](https://github.com/serverless/serverless/issues/8291)) ([c96b429](https://github.com/serverless/serverless/commit/c96b429c6082f203e1cc06c2ae27a40a8a259bcd)) ([Oz Weiss](https://github.com/thewizarodofoz))
  - Schema for AWS `alexaSkill` event ([#8290](https://github.com/serverless/serverless/issues/8290)) ([7f47448](https://github.com/serverless/serverless/commit/7f474481b60c545f3855efc7857474c4277413e0)) ([Piotr Grzesik](https://github.com/pgrzesik))

### Bug Fixes

- **Config Schema:** Recognize deployment valid environment variables format ([#8307](https://github.com/serverless/serverless/issues/8307)) ([eb5e548](https://github.com/serverless/serverless/commit/eb5e54847e6e2f6b89a1b5325df4d8421efe479a)) ([Mariusz Nowak](https://github.com/medikoo))
- **AWS SQS:** Ensure to depend on provisioned alias if needed ([#8298](https://github.com/serverless/serverless/issues/8298)) ([8c4d972](https://github.com/serverless/serverless/commit/8c4d97211aa3dd4c41d9205a3ca0ccaab3564225)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **AWS ALB:** Ensure to treat `provider.alb.authorizers` as optional ([#8295](https://github.com/serverless/serverless/issues/8295)) ([e990c09](https://github.com/serverless/serverless/commit/e990c09edb8fb711152485bed46dfefd827ac92d)) ([Mariusz Nowak](https://github.com/medikoo))

## [2.3.0](https://github.com/serverless/serverless/compare/v2.2.0...v2.3.0) (2020-09-25)

### Features

- **AWS MSK:** Support for MSK through `msk` event ([#8164](https://github.com/serverless/serverless/issues/8164)) ([05d703e](https://github.com/serverless/serverless/commit/05d703e6d5a7b100aaf6203209b0d596a3e70496)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **Config Schema:** Schema for AWS `alexaSmartHome` event ([#8255](https://github.com/serverless/serverless/issues/8255)) ([bd5099e](https://github.com/serverless/serverless/commit/bd5099e15019352ab5ae9b2cd5519eaff50c520e)) ([Oz Weiss](https://github.com/thewizarodofoz))
- Deprecate `awsKmsKeyArn` in favor of `kmsKeyArn` ([#8277](https://github.com/serverless/serverless/issues/8277)) ([a55009e](https://github.com/serverless/serverless/commit/a55009e221de91fee46a343483eb31539352410b)) ([Frédéric Barthelet](https://github.com/fredericbarthelet))

### Bug Fixes

- **AWS Lambda:** Address issues in version hash generation logic, ensure any layer changes influence change of hash ([#8066](https://github.com/serverless/serverless/issues/8066)) ([e43c889](https://github.com/serverless/serverless/commit/e43c889647f45bc93cf3cb1fd45d4a18ad95da58)) ([Patrick Withams](https://github.com/pwithams))
- **Config Schema:** Recognize CF intrinsic functions in vpc config ([#8283](https://github.com/serverless/serverless/issues/8283)) ([e75e998](https://github.com/serverless/serverless/commit/e75e998e9238c8d59653ec2533c9fb7c3f0e546a)) ([Devon Powell](https://github.com/devpow112))
- **Variables:** Ensure no collisions with AWS CloudFormation variables ([#8279](https://github.com/serverless/serverless/issues/8279)) ([2fdeb51](https://github.com/serverless/serverless/commit/2fdeb51174d8fa55cc2704e8e84297471eadec39)) ([Matthieu Napoli](https://github.com/mnapoli))

### Maintenance Improvements

- **`lodash` replacement:**
  - Replace `_.forEach` with `Object.entries().forEach` ([#8280](https://github.com/serverless/serverless/issues/8280)) ([76e02cc](https://github.com/serverless/serverless/commit/76e02cc09c74e18abdc1fccbda81676cf2462598)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Replace `_.forOwn` with `Object.entries().forEach` ([#8284](https://github.com/serverless/serverless/issues/8284)) ([56c7e44](https://github.com/serverless/serverless/commit/56c7e443a0350027cd5ccf5d4c94dc06f353306f)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **Print:** Read provider values from provider ([#8281](https://github.com/serverless/serverless/issues/8281)) ([b53716a](https://github.com/serverless/serverless/commit/b53716a64c9dacb411690b8b8496adfc8c194ca1)) ([Mariusz Nowak](https://github.com/medikoo))

## [2.2.0](https://github.com/serverless/serverless/compare/v2.1.1...v2.2.0) (2020-09-23)

### Features

- **Config Schema:**
  - Schema for AWS `sqs` event ([#8227](https://github.com/serverless/serverless/issues/8227)) ([4f96ce1](https://github.com/serverless/serverless/commit/4f96ce1042079c08578ef70ddbb4c2def32d6663)) ([Oz Weiss](https://github.com/thewizarodofoz))
  - Schema for `functions[]` properties ([#8222](https://github.com/serverless/serverless/issues/8222)) ([feece9a](https://github.com/serverless/serverless/commit/feece9a2ec5be0f49af7147b84bed76e9ba50155)) ([Frédéric Barthelet](https://github.com/fredericbarthelet))
  - Schema for AWS `cloudfront` event ([#8250](https://github.com/serverless/serverless/issues/8250)) ([8943693](https://github.com/serverless/serverless/commit/8943693c33359749d6685d867c01151cfd8000cf)) ([Oz Weiss](https://github.com/thewizarodofoz))
  - Schema for AWS `cloudwatchLog` event ([#8228](https://github.com/serverless/serverless/issues/8228)) ([42676d3](https://github.com/serverless/serverless/commit/42676d34d4cb33cb59fd54c6a78ed07c965146e5)) ([Oz Weiss](https://github.com/thewizarodofoz))
  - Schema for AWS `websocket` event ([#8218](https://github.com/serverless/serverless/issues/8218)) ([e1ca63c](https://github.com/serverless/serverless/commit/e1ca63c06a824e18fdd92f5c6c3efbf7f5f644d2)) ([Raul Zaldana](https://github.com/zaldanaraul))
- **AWS Lambda:** Support CF intrinsic functions in `fileSystemConfig.arn` ([#8265](https://github.com/serverless/serverless/issues/8265)) ([4bf6543](https://github.com/serverless/serverless/commit/4bf654376f9820efbd78876c72dad95d4cc52831)) ([Piotr Grzesik](https://github.com/pgrzesik))
- Deprecate an attempt to extend nonexistent resources ([#8266](https://github.com/serverless/serverless/issues/8266)) ([0ced414](https://github.com/serverless/serverless/commit/0ced414174c8acf7dd70dd9b5e4b7a525cd8320e)) ([Piotr Grzesik](https://github.com/pgrzesik))

### Bug Fixes

- **AWS Lambda:** Recognize function-wide settings for version hashing ([#8212](https://github.com/serverless/serverless/issues/8212)) ([1fceb89](https://github.com/serverless/serverless/commit/1fceb898d0ea10b00bc6759a5204065c81b560e8)) ([Oz Weiss](https://github.com/thewizarodofoz))
- **AWS Local Invocation:** Fix Dockerfile layer path on Windows ([#8273](https://github.com/serverless/serverless/issues/8273)) ([0164327](https://github.com/serverless/serverless/commit/01643273df742239cd020e7d08941c505e540217)) ([Gábor Lipták](https://github.com/gliptak))
- **AWS SNS:** Fix setup of redrive policy ([#8268](https://github.com/serverless/serverless/issues/8268)) ([3e9e6aa](https://github.com/serverless/serverless/commit/3e9e6aacc675cd7bf92499b9494a15ff9b21981b)) ([5up3r20e](https://github.com/5up3r20e))
- **Config Schema:**
  - Recognize enhanced object syntax for plugins ([#8259](https://github.com/serverless/serverless/issues/8259)) ([4b86fa5](https://github.com/serverless/serverless/commit/4b86fa5759a4b52771bb69d3ea50762b87583765)) ([jimjenkins5](https://github.com/jimjenkins5))
  - Treat explicit `null` or `undefined` as no value ([#8272](https://github.com/serverless/serverless/issues/8272)) ([e5e42ba](https://github.com/serverless/serverless/commit/e5e42bab8cec9c508e465ee259ec75aff183168c)) ([Mariusz Nowak](https://github.com/medikoo))

### Maintenance Improvements

- **`lodash` replacement:**
  - Replace `_.{entries|entriesIn|toPairs}` with `Object.entries` ([#8275](https://github.com/serverless/serverless/issues/8275)) ([b867df1](https://github.com/serverless/serverless/commit/b867df147aea5e1f57a9d275e2a389efbbcf38aa)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Replace `_.values` with `Object.values` ([#8274](https://github.com/serverless/serverless/issues/8274)) ([57d1ce1](https://github.com/serverless/serverless/commit/57d1ce1a660a0446c77e9bafb174ae3fe0263516)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **Dependencies:**
  - Upgrade "@serverless/utils" to v2 ([#8278](https://github.com/serverless/serverless/issues/8278)) ([ef39e95](https://github.com/serverless/serverless/commit/ef39e958db39b367875af871a7014b4d284f5554)) ([Mariusz Nowak](https://github.com/medikoo))

### [2.1.1](https://github.com/serverless/serverless/compare/v2.1.0...v2.1.1) (2020-09-17)

### Maintenance Improvements

- Ensure to rely on `@serverless/enterprise-plugin` ^4.0.4

## [2.1.0](https://github.com/serverless/serverless/compare/v2.0.0...v2.1.0) (2020-09-16)

### Features

- **Config Schema:**
  - Schema for AWS `cloudwatch` event ([#8230](https://github.com/serverless/serverless/issues/8230)) ([3730fd4](https://github.com/serverless/serverless/commit/3730fd4fd1ca3610415968e4633a0cba275b2e43)) ([Oz Weiss](https://github.com/thewizarodofoz))
  - Schema for AWS `stream` event ([#8201](https://github.com/serverless/serverless/issues/8201)) ([1fb338b](https://github.com/serverless/serverless/commit/1fb338b184ed770bc5d8d162bf5c54336f3d2ddd)) ([Frédéric Barthelet](https://github.com/fredericbarthelet))

### Bug Fixes

- **Config Schema:**
  - Fix CF template extension `Transform`schema ([#8229](https://github.com/serverless/serverless/issues/8229)) ([6961b62](https://github.com/serverless/serverless/commit/6961b629e72aada33ff5a3a12f1a04f686b58329)) ([Michael Wolfenden](https://github.com/michael-wolfenden))
  - Recognize string value at DependsOn ([#8233](https://github.com/serverless/serverless/issues/8233)) ([4c36753](https://github.com/serverless/serverless/commit/4c367535074f7b82799ed4bd16cd5fcdef445eb5)) ([Mariusz Nowak](https://github.com/medikoo))
  - Support `Condition` attribute in `resources.extensions` ([#8217](https://github.com/serverless/serverless/issues/8217)) ([16bae33](https://github.com/serverless/serverless/commit/16bae337448e23484dc10262d9a6be845eb1818a)) ([Geoff Baskwill](https://github.com/glb))
- **CLI:** Workaround config schema error on project initialization ([#8258](https://github.com/serverless/serverless/issues/8258)) ([738c52f](https://github.com/serverless/serverless/commit/738c52f6e544bbf9ae130eac99e676bd22fa29e2)) ([Mariusz Nowak](https://github.com/medikoo))
- Ensure to memoize config file resolution by instance ([#8231](https://github.com/serverless/serverless/issues/8231)) ([3177e40](https://github.com/serverless/serverless/commit/3177e40cee1d91a5b054dd47cdb6f540436cc507)) ([Mariusz Nowak](https://github.com/medikoo))

### Maintenance Improvements

- **Dependencies:**
  - Switch to `fastest-levenshtein` ([#8238](https://github.com/serverless/serverless/issues/8238)) ([0cd9cca](https://github.com/serverless/serverless/commit/0cd9ccaf65a13d01c9e26c9950a6e4dc4a5a53f7)) ([Mariusz Nowak](https://github.com/medikoo))
  - Register `semver-regex` as dev dependency ([#8245](https://github.com/serverless/serverless/issues/8245)) ([4c46663](https://github.com/serverless/serverless/commit/4c4666327e31d0267fff6cd98667c92d7e654422)) ([Mariusz Nowak](https://github.com/medikoo))
  - **Upgrade:**
    - `archiver` to v5 ([#8235](https://github.com/serverless/serverless/issues/8235)) ([389e3eb](https://github.com/serverless/serverless/commit/389e3eb5fba81177c36d5ee83f39802403b90653)) ([Mariusz Nowak](https://github.com/medikoo))
    - `chalk` to v4 ([#8236](https://github.com/serverless/serverless/issues/8236)) ([26628ff](https://github.com/serverless/serverless/commit/26628ff43588b06e6919a1b8f426129d0c7dcea7)) ([Mariusz Nowak](https://github.com/medikoo))
    - `download` to v8 ([#8237](https://github.com/serverless/serverless/issues/8237)) ([5931c7c](https://github.com/serverless/serverless/commit/5931c7cb3df9a0f16208de422b573da9bca46030)) ([Mariusz Nowak](https://github.com/medikoo))
    - `filesize` to v6 ([#8239](https://github.com/serverless/serverless/issues/8239)) ([5616603](https://github.com/serverless/serverless/commit/5616603ba8d38581e1e24312e4ec908212e01f33)) ([Mariusz Nowak](https://github.com/medikoo))
    - `fs-extra` to v9 ([#8240](https://github.com/serverless/serverless/issues/8240)) ([370c097](https://github.com/serverless/serverless/commit/370c09766d4de37bfe8b473843106440881d1554)) ([Mariusz Nowak](https://github.com/medikoo))
    - `get-stdin` to v8 ([#8241](https://github.com/serverless/serverless/issues/8241)) ([372ce54](https://github.com/serverless/serverless/commit/372ce541cdd7d93bba4eaef44ca596b373740e7a)) ([Mariusz Nowak](https://github.com/medikoo))
    - `is-docker` to v2 ([#8242](https://github.com/serverless/serverless/issues/8242)) ([0c78259](https://github.com/serverless/serverless/commit/0c782599fd49d7dd521ee3282fd65ded9b0803fd)) ([Mariusz Nowak](https://github.com/medikoo))
    - `p-limit` to v3 ([#8243](https://github.com/serverless/serverless/issues/8243)) ([e136d8b](https://github.com/serverless/serverless/commit/e136d8bfd4d299a4faa31cf33dd804d3cc1096bc)) ([Mariusz Nowak](https://github.com/medikoo))
    - `semver` to v7 ([#8244](https://github.com/serverless/serverless/issues/8244)) ([c6c3804](https://github.com/serverless/serverless/commit/c6c38048071fc40c67fb57ff7dadb6cf06c97fd7)) ([Mariusz Nowak](https://github.com/medikoo))
    - `untildify` to v4 ([#8246](https://github.com/serverless/serverless/issues/8246)) ([282b9be](https://github.com/serverless/serverless/commit/282b9bee6028f4fd6417241d59afa8f69061268d)) ([Mariusz Nowak](https://github.com/medikoo))
    - `yargs-parser` to v20 ([#8248](https://github.com/serverless/serverless/issues/8248)) ([ce51c8f](https://github.com/serverless/serverless/commit/ce51c8fb6fea254affd51361b6a1cf551b5d8a36)) ([Mariusz Nowak](https://github.com/medikoo))
    - `uuid` to v8 ([#8234](https://github.com/serverless/serverless/issues/8234)) ([b40b11b](https://github.com/serverless/serverless/commit/b40b11b4e2cdaae3cc4923ee9e74e6fa7912b668)) ([Mariusz Nowak](https://github.com/medikoo))
  - **Remove not used:**
    - `cli-progress-footer` ([#8247](https://github.com/serverless/serverless/issues/8247)) ([08cb86a](https://github.com/serverless/serverless/commit/08cb86afe988058cd588cda36f44699bce1a968c)) ([Mariusz Nowak](https://github.com/medikoo))
    - `jwt-decode` ([#8247](https://github.com/serverless/serverless/issues/8247)) ([f38c7c5](https://github.com/serverless/serverless/commit/f38c7c5a9ecac649da3b9ab5338077df08e30d28)) ([Mariusz Nowak](https://github.com/medikoo))
    - `mocha-lcov-reporter` ([#8247](https://github.com/serverless/serverless/issues/8247)) ([822adbd](https://github.com/serverless/serverless/commit/822adbd2a03cbf0d2fd30222d0372cf28c95c467)) ([Mariusz Nowak](https://github.com/medikoo))
    - `rc` dependency ([#8247](https://github.com/serverless/serverless/issues/8247)) ([4f6e354](https://github.com/serverless/serverless/commit/4f6e35431dd31c48a1a86ebd543e8e1934150201)) ([Mariusz Nowak](https://github.com/medikoo))
    - `write-file-atomic` ([#8247](https://github.com/serverless/serverless/issues/8247)) ([c375120](https://github.com/serverless/serverless/commit/c375120285a3d13144d1cbcd7d11160f2f94c8c4)) ([Mariusz Nowak](https://github.com/medikoo))

## [2.0.0](https://github.com/serverless/serverless/compare/v1.83.0...v2.0.0) (2020-09-10)

### ⚠ BREAKING CHANGES

- Node.js version 10 or later is required (dropped support for v6 and v8)
- **CLI:**
  - Locally installed (in service `node_modules`) CLI will be run instead of global one, when globally installed `serverless` CLI is invoked in a context of a service, which has locally installed `serverless`.
  - `slss` alias for `serverless` CLI command was removed. Rely on `sls` or `serverless` instead
  - `bin/serverless` was removed. If you target CLI script directly, point `bin/serverless.js` instead
- **AWS HTTP API:**
  - Default `payload` was changed from `1.0` to `2.0`
  - `timeout` setting as configured directly for `httpApi` event is no longer supported. Timeout value is now unconditionally resolved from function timeout setting (it's to guarantee that configured endpoint has necessary room to process function invocation)
- **AWS ALB:** Support for `providers.alb.authorizers[].allowUnauthenticated` setting was removed. Rely on `providers.alb.authorizers[].onUnauthenticatedRequest` instead

### Features

- **CLI:** Fallback to service local `serverless` installation by default ([#8180](https://github.com/serverless/serverless/issues/8180)) ([dfc7839](https://github.com/serverless/serverless/commit/dfc78396c7c555887163c5f3f60361568eebbfa4)) ([Mariusz Nowak](https://github.com/medikoo))
- **AWS HTTP API:** Switch default payload mode to 2.0 ([#8133](https://github.com/serverless/serverless/issues/8133)) ([1596738](https://github.com/serverless/serverless/commit/1596738cf919bfb5ed702c40f9d3f2b39d529a81)) ([andreizet](https://github.com/andreizet))

### Bug Fixes

- **Packaging:** Fix resolution of files with `.` In their names ([#8130](https://github.com/serverless/serverless/issues/8130)) ([c620af3](https://github.com/serverless/serverless/commit/c620af3cd6eb930e39a02aa4537f748854d0f12a)) ([Christian Musa](https://github.com/crash7))

### Maintenance Improvements

- Drop support for Node.js versions below v10 ([#8131](https://github.com/serverless/serverless/issues/8131)) ([69dd4b9](https://github.com/serverless/serverless/commit/69dd4b97453a7ca34b541313d1063a1e0c1c7876)) ([Mariusz Nowak](https://github.com/medikoo))
- **CLI:**
  - Remove `slss`, `serverless` command alias ([#8161](https://github.com/serverless/serverless/issues/8161)) ([33eef9f](https://github.com/serverless/serverless/commit/33eef9f06b83b889baaa28cab1eaece275790a52)) ([Christian Musa](https://github.com/crash7))
  - Remove deprecated `bin/serverless` file ([#8142](https://github.com/serverless/serverless/issues/8142)) ([4ceaca0](https://github.com/serverless/serverless/commit/4ceaca022a6292b56239a35933499a63ae242479)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **AWS Lambda:** Remove support for async config on destination ([#8138](https://github.com/serverless/serverless/issues/8138)) ([e131f26](https://github.com/serverless/serverless/commit/e131f2661d9a508505ddf8599fb9ac6876c8ef15)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **AWS ALB:** Remove support for `authorizers[].allowUnauthenticated` ([#8160](https://github.com/serverless/serverless/issues/8160)) ([7c304df](https://github.com/serverless/serverless/commit/7c304df5ffcaaf1dbbd90ccf714f55f4a6cc6a0b)) ([morgan-sam](https://github.com/morgan-sam))
- **AWS HTTP API:** Drop support for `timeout` setting ([#8184](https://github.com/serverless/serverless/issues/8184)) ([1cfd1f2](https://github.com/serverless/serverless/commit/1cfd1f25a278679d94e4cd30baf1b2092ff83d8a)) ([Mariusz Nowak](https://github.com/medikoo))
- Replace `mkdrip` with `esnureDir` from `fs-extra` ([#8183](https://github.com/serverless/serverless/issues/8183)) ([1beb8d0](https://github.com/serverless/serverless/commit/1beb8d0246e705d3d724dbd2fb4c6639bc961cba)) ([Mariusz Nowak](https://github.com/medikoo))

## [1.83.3](https://github.com/serverless/serverless/compare/v1.83.2...v1.83.3) (2021-03-23)

### Maintenance Improvements

- Backport `analyticsUrl` from `@serverless/utils@4.0.0` ([#9162](https://github.com/serverless/serverless/pull/9162)) ([a1f6538](https://github.com/serverless/serverless/commit/a1f6538eb5207669ac108fe8e6cf8d12c6e90f20)) ([Piotr Grzesik](https://github.com/pgrzesik))
- Enrich analytics payload with missing properties ([#9162](https://github.com/serverless/serverless/pull/9162)) ([a7b9498](https://github.com/serverless/serverless/commit/a7b9498a94e1130678b2f7c7ee8d8676cecd1521)) ([Piotr Grzesik](https://github.com/pgrzesik))

### [1.83.2](https://github.com/serverless/serverless/compare/v1.83.1...v1.83.2) (2020-11-06)

### Bug Fixes

- **AWS HTTP API:** Ensure to report deprecation at initialization phase ([#8483](https://github.com/serverless/serverless/issues/8469)) ([61a72c6](https://github.com/serverless/serverless/commit/61a72c69ed488bd8ae10819ff12b7a2f5679b8e3)) ([Mariusz Nowak](https://github.com/medikoo))
- Ensure to inspect configuration once it's fully resolved ([#8483](https://github.com/serverless/serverless/issues/8469)) ([1ea4719](https://github.com/serverless/serverless/commit/1ea47193db3f51a33ecf25ae3ba0aa973530644a)) ([Mariusz Nowak](https://github.com/medikoo))

## [1.83.1](https://github.com/serverless/serverless/compare/v1.83.0...v1.83.1) (2020-11-03)

### Bug Fixes

- **Analytics:** Ensure to send payload when having all meta ([#8469](https://github.com/serverless/serverless/issues/8469)) ([78dce94](https://github.com/serverless/serverless/commit/78dce94571a05d0021d58352bd21b80f90c62883)) ([Mariusz Nowak](https://github.com/medikoo))

### Maintanance Improvements

- **AWS Lambda:** Ensure to log deprecation at initialization stage ([#8469](https://github.com/serverless/serverless/issues/8469)) ([2e3ce12](https://github.com/serverless/serverless/commit/2e3ce128b0e55abf42e9d07cb96af82f3194d60c)) ([Mariusz Nowak](https://github.com/medikoo))
- **AWS ALB:** Ensure to log deprecation at initialization stage ([#8469](https://github.com/serverless/serverless/issues/8469)) ([3cf6449](https://github.com/serverless/serverless/commit/3cf6449b78604434a0292513420d2b90faef37ef)) ([Mariusz Nowak](https://github.com/medikoo))
- **AWS HTTP API:** Ensure to log deprecation at initialization stage ([#8469](https://github.com/serverless/serverless/issues/8469)) ([ecd3084](https://github.com/serverless/serverless/commit/ecd30844fc7a748d0ac56679636741c009b2c630)) ([Mariusz Nowak](https://github.com/medikoo))
- **Standalone:** Support non-latest version builds ([#8469](https://github.com/serverless/serverless/issues/8469)) ([8727044](https://github.com/serverless/serverless/commit/8727044b959ed1bb989d97f7fa178e8dcf36b5a0)) ([Mariusz Nowak](https://github.com/medikoo))

## [1.83.0](https://github.com/serverless/serverless/compare/v1.82.0...v1.83.0) (2020-09-10)

### Features

- **Config Schema:**
  - Schema for AWS `resources` section ([#8139](https://github.com/serverless/serverless/issues/8139)) ([00d6f79](https://github.com/serverless/serverless/commit/00d6f79c5022fd1bf1537d4095769916369d30ea)) ([Geoff Baskwill](https://github.com/glb))
  - Schema for AWS `schedule` event ([#8143](https://github.com/serverless/serverless/issues/8143)) ([d9b91e9](https://github.com/serverless/serverless/commit/d9b91e97fb81b6f19c9f95920b509d623bdca37d)) ([Andy Duncan](https://github.com/andyjduncan))
- **AWS Local Invocation:** Resolve CF Ref in env variables ([#8198](https://github.com/serverless/serverless/issues/8198)) ([72745c9](https://github.com/serverless/serverless/commit/72745c9e77476f65604fdc68e8e3c55feffdf90f)) ([Frédéric Barthelet](https://github.com/fredericbarthelet))
- **AWS HTTP API:** Recognize support for CF instructions in authorizers ([#8200](https://github.com/serverless/serverless/issues/8200)) ([428fc79](https://github.com/serverless/serverless/commit/428fc796c178fc5fcb7478d048ba0b2251ab78e9)) ([Frédéric Barthelet](https://github.com/fredericbarthelet))

### Bug Fixes

- **AWS API Gateway:** Fix model resource name generator ([#8204](https://github.com/serverless/serverless/issues/8204)) ([f727631](https://github.com/serverless/serverless/commit/f7276311008134f57f24d85d2b16730c9ab75574)) ([Cole Mujadzic](https://github.com/colemujadzic))
- **AWS Stream:** Fix support for `batchWindow: 0` ([#8202](https://github.com/serverless/serverless/issues/8202)) ([b0547e6](https://github.com/serverless/serverless/commit/b0547e6e1a673eff956f417110ce6bf40fc32f92)) ([Mariusz Nowak](https://github.com/medikoo))
- **Templates:** Add missing property in ruby template ([#8195](https://github.com/serverless/serverless/issues/8195)) ([8f070d5](https://github.com/serverless/serverless/commit/8f070d58c46e7c1d5cbe34b31a34387eaccea505)) ([jkburges](https://github.com/jkburges))

### Maintenance Improvements

- **Config Schema:**
  - Move docs to dedicated website page ([#8207](https://github.com/serverless/serverless/issues/8207)) ([c370295](https://github.com/serverless/serverless/commit/c370295be6a67c5a7c5e2af323b29588cbc1d02e)) ([Mariusz Nowak](https://github.com/medikoo))
  - Unified warning log color scheme ([#8207](https://github.com/serverless/serverless/issues/8207)) ([2c19bf5](https://github.com/serverless/serverless/commit/2c19bf5eaea876f38cf0fd6fb8c453fbfe8d416a)) ([Mariusz Nowak](https://github.com/medikoo))

## [1.82.0](https://github.com/serverless/serverless/compare/v1.81.1...v1.82.0) (2020-09-04)

### Features

- **Config Schema:** Schema for AWS `iot` event ([#8177](https://github.com/serverless/serverless/issues/8177)) ([e55fc36](https://github.com/serverless/serverless/commit/e55fc36e1a3e78d155cbaaa5517c99ecc74a113f)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **Analytics:** Recognize and report four different installation types ([#8188](https://github.com/serverless/serverless/issues/8188)) ([f9e955c](https://github.com/serverless/serverless/commit/f9e955c8f8ae9c1f8d8f883a052f91d57a7ffa4a)) ([Mariusz Nowak](https://github.com/medikoo))

### Maintenance Improvements

- Remove `update-notifier` notifications (as those are now covered by more accurate backend notifications, which also support notifications for multiple majors) ([#8185](https://github.com/serverless/serverless/issues/8185)) ([11fb888](https://github.com/serverless/serverless/commit/11fb8889c8744180919eb3cfae85269a7ff3649f)) ([Mariusz Nowak](https://github.com/medikoo))
- Prevent _is locally installed_ detection on confirmed local installations ([#8188](https://github.com/serverless/serverless/issues/8188)) ([7accad6](https://github.com/serverless/serverless/commit/7accad6eb9ad1d9549c2e0e5c55e11b3f827af6a)) ([Mariusz Nowak](https://github.com/medikoo))

### [1.81.1](https://github.com/serverless/serverless/compare/v1.81.0...v1.81.1) (2020-09-02)

### Bug Fixes

- Revert from `frameworkVersion` requirement plan ([#8178](https://github.com/serverless/serverless/issues/8178)) ([6dd0596](https://github.com/serverless/serverless/commit/6dd0596286666b242b921847ffdeb6628baf3b26)) ([Mariusz Nowak](https://github.com/medikoo))

## [1.81.0](https://github.com/serverless/serverless/compare/v1.80.0...v1.81.0) (2020-09-02)

### Features

- **CLI:**
  - Optionally fallback to local installation of `serverless` ([#8158](https://github.com/serverless/serverless/issues/8158)) ([9fb62f1](https://github.com/serverless/serverless/commit/9fb62f1138fc36e035993740496336af314171aa)) ([Mariusz Nowak](https://github.com/medikoo))
  - Announce `frameworkVersion` requirement ([#8158](https://github.com/serverless/serverless/issues/8158)) ([9f7f9d3](https://github.com/serverless/serverless/commit/9f7f9d398339d9c8ba09ae3b74d3e7bbbca4dcee)) ([Mariusz Nowak](https://github.com/medikoo))
  - Deprecate `slss` CLI alias ([#8156](https://github.com/serverless/serverless/issues/8156)) ([a2d1031](https://github.com/serverless/serverless/commit/a2d1031fb88ac750685b5940b60c0b241c90e319)) ([Christian Musa](https://github.com/crash7))
- **Config Schema:** Schema for AWS `sns` event ([#8112](https://github.com/serverless/serverless/issues/8112)) ([87fd3c1](https://github.com/serverless/serverless/commit/87fd3c17fb7d975b37c952293480bdc5ea4a8226)) ([Frédéric Barthelet](https://github.com/fredericbarthelet))
- **AWS Local Invocation:** Resolve `Fn::ImportValue` instructions in env vars ([#8157](https://github.com/serverless/serverless/issues/8157)) ([06ed01b](https://github.com/serverless/serverless/commit/06ed01b8742260c01411d5e371ab56a6c02219f6)) ([Frédéric Barthelet](https://github.com/fredericbarthelet))
- **AWS API Gateway:** Allow to opt-out from default request templates ([#8159](https://github.com/serverless/serverless/issues/8159)) ([7aad819](https://github.com/serverless/serverless/commit/7aad8193787f591cd3186b2f86e0f9bec23f4dcf)) ([Joaquín Ormaechea](https://github.com/jormaechea))
- **AWS HTTP API:** Support CF functions at `httpApi.authorizer.id` ([#8171](https://github.com/serverless/serverless/issues/8171)) ([453b802](https://github.com/serverless/serverless/commit/453b8026409e5fdd107fc9cefb7da8ec4b1e8f14)) ([Frédéric Barthelet](https://github.com/fredericbarthelet))
- **Templates:**
  - Ensure `frameworkVersion` in all templates ([#8175](https://github.com/serverless/serverless/issues/8175)) ([3089abc](https://github.com/serverless/serverless/commit/3089abc5c48335375ed8f9a67814e3b4cf82f53d)) ([Mariusz Nowak](https://github.com/medikoo))
  - Upgrade `google-nodejs` template ([#8152](https://github.com/serverless/serverless/issues/8152)) ([40fb8ae](https://github.com/serverless/serverless/commit/40fb8ae1123b4f898ff008602242d5b5bba24b6b)) ([Viacheslav Dobromyslov](https://github.com/dobromyslov))
- **Standalone:** Prevent accidental upgrades to a new major ([#8136](https://github.com/serverless/serverless/issues/8136)) ([56aa5aa](https://github.com/serverless/serverless/commit/56aa5aa15abed64db6758aecd8c27719928b5a14)) ([Mariusz Nowak](https://github.com/medikoo))
- **Analytics:**
  - Introduce `isLocallyInstalled` characteristics ([#8158](https://github.com/serverless/serverless/issues/8158)) ([246e4a6](https://github.com/serverless/serverless/commit/246e4a6756571e00f84b0f0567a305be402d5512)) ([Mariusz Nowak](https://github.com/medikoo))
  - Send info on reported deprecations ([#8136](https://github.com/serverless/serverless/issues/8136)) ([83c4b16](https://github.com/serverless/serverless/commit/83c4b167ee69d4bbd1933e415319a40a27b11daa)) ([Mariusz Nowak](https://github.com/medikoo))

### Bug Fixes

- **Packaging:** Ensure to include eventual `aws-sdk` dependency if installed ([#8145](https://github.com/serverless/serverless/issues/8145)) ([2561ae8](https://github.com/serverless/serverless/commit/2561ae800e04dd197302d5692cf6eab72185cc11)) ([Mariusz Nowak](https://github.com/medikoo))
- **Templates:** Rename folder `vscode` to `.vscode` ([#8168](https://github.com/serverless/serverless/issues/8168)) ([f308382](https://github.com/serverless/serverless/commit/f3083828b448d08c98969c2f956248bbce75de57))([Frédéric Barthelet](https://github.com/fredericbarthelet))
- **Config Schema:** Ensure to validate direct config where applicable ([#8144](https://github.com/serverless/serverless/issues/8144)) ([af60319](https://github.com/serverless/serverless/commit/af603198a1522094ca0607c24e9325657a41e442)) ([Mariusz Nowak](https://github.com/medikoo))
- Fix handling of invalid range put into `frameworkVersion` ([#8175](https://github.com/serverless/serverless/issues/8175)) ([0d5a480](https://github.com/serverless/serverless/commit/0d5a480fd0fe7abbc1998b9f72707589541f0639)) ([Mariusz Nowak](https://github.com/medikoo))
- Fix handling of pre-releases in `frameworkVersion` validation ([#8166](https://github.com/serverless/serverless/issues/8166)) ([c0fb04a](https://github.com/serverless/serverless/commit/c0fb04af3d2ec35436e02778b3a23f75f45ad7bb)) ([Mariusz Nowak](https://github.com/medikoo))

### Maintenance Improvements

- **Config Schema:**
  - Define AWS definitions in context of a provider ([#8144](https://github.com/serverless/serverless/issues/8144)) ([c79cae2](https://github.com/serverless/serverless/commit/c79cae2308af0b038ef6fcfcf28be8841493e745)) ([Mariusz Nowak](https://github.com/medikoo))
  - Treat `resources` as fully provider specific ([#8144](https://github.com/serverless/serverless/issues/8144)) ([6d7e967](https://github.com/serverless/serverless/commit/6d7e96722721c8a5c614bea2802af7142011d35f)) ([Mariusz Nowak](https://github.com/medikoo))
- **CLI:**
  - Do not notify of update when new major is published (as that's in scope of backend notifications) ([#8136](https://github.com/serverless/serverless/issues/8136)) ([230f34a](https://github.com/serverless/serverless/commit/230f34aa9905636e53e1e63b769024f934689e6b)) ([Mariusz Nowak](https://github.com/medikoo))
  - Improve presentation of multi-line backend notifications ([#8136](https://github.com/serverless/serverless/issues/8136)) ([1abb3c0](https://github.com/serverless/serverless/commit/1abb3c05b58e744bdfa24879921cdaf91438d6f5)) ([Mariusz Nowak](https://github.com/medikoo))
- **AWS HTTP API:** Convert `timeout` usage warnings to deprecations ([#8172](https://github.com/serverless/serverless/issues/8172)) ([3b294fb](https://github.com/serverless/serverless/commit/3b294fb1dbe9f22a6754b64530120a37ab4d16aa)) ([Mariusz Nowak](https://github.com/medikoo))
- Seclude IAM role resource name resolution logic ([#8167](https://github.com/serverless/serverless/issues/8167)) ([6d7103d](https://github.com/serverless/serverless/commit/6d7103da02dcbc4f89949dcebdf4ac6745b91776)) ([Mariusz Nowak](https://github.com/medikoo))
- Expose `serverless.onExitPromise` for internal processing ([#8146](https://github.com/serverless/serverless/issues/8146)) ([0ab1283](https://github.com/serverless/serverless/commit/0ab12832182ab1b34f70d3a5f17d012a4f61b10a)) ([Georges Biaux](https://github.com/georgesbiaux))
- Auto align multi-line deprecation messages ([#8158](https://github.com/serverless/serverless/issues/8158)) ([9cb86a4](https://github.com/serverless/serverless/commit/9cb86a4af2ee0bdda605e5eb4fa14d964e5fe404)) ([Mariusz Nowak](https://github.com/medikoo))

## [1.80.0](https://github.com/serverless/serverless/compare/v1.79.0...v1.80.0) (2020-08-26)

### Features

- **AWS Lambda:** Support EFS mounts ([#8042](https://github.com/serverless/serverless/issues/8042)) ([149f64a](https://github.com/serverless/serverless/commit/149f64ad1c8cec41bfc72ceebcb7c8095b2f8c5c)) ([Piotr Grzesik](https://github.com/pgrzesik))
- **Config Schema:**
  - Schema for AWS `eventBridge` event ([#8114](https://github.com/serverless/serverless/issues/8114)) ([796ce0b](https://github.com/serverless/serverless/commit/796ce0b5ddaf893878912b5edeeec54718bf04ad)) ([Frédéric Barthelet](https://github.com/fredericbarthelet))
  - Schema for AWS `cognitoPool` event ([#8105](https://github.com/serverless/serverless/issues/8105)) ([184cb48](https://github.com/serverless/serverless/commit/184cb48033ce92f771188c27c0ad3e541adab528)) ([Frédéric Barthelet](https://github.com/fredericbarthelet))
- **Plugins:** Fallback plugins search to global installation folder ([#8038](https://github.com/serverless/serverless/issues/8038)) ([82f6db7](https://github.com/serverless/serverless/commit/82f6db7a1fcd27cd723b9100538355dd297774d5)) ([Derek Kulinski](https://github.com/takeda))

### Bug Fixes

- **Config Schema:** Fix recognition of some required properties ([#8108](https://github.com/serverless/serverless/issues/8108)) ([1dd42b0](https://github.com/serverless/serverless/commit/1dd42b0c62d6eb0cc6036fe1529e85e05c616a09)) ([Mariusz Nowak](https://github.com/medikoo))

### Performance Improvements

- **Packaging:** Exclude `aws-sdk` dependency (as it's provided in AWS environment unconditionally) ([#8103](https://github.com/serverless/serverless/issues/8103)) ([f45da3c](https://github.com/serverless/serverless/commit/f45da3c7b168d34e7d3c520068dc24364753a74a)) ([Yogendra Sharma](https://github.com/Yogendra0Sharma))
- **Packaging:** Remove `aws-sdk` installation step when packaging custom resource lambda ([#8110](https://github.com/serverless/serverless/issues/8110)) ([258c692](https://github.com/serverless/serverless/commit/258c692c47c911d77efe880f41134801bdea314a)) ([Sedat Can Yalçın](https://github.com/sedat))

### Maintenance Improvements

- **AWS Deploy:** Refactor out `async` dependency in CloudFormation stack deployment monitoring logic ([#8132](https://github.com/serverless/serverless/issues/8132)) ([f9bcaae](https://github.com/serverless/serverless/commit/f9bcaaead90fd8691a85941f4d5216d5357037ad)) ([Mariusz Nowak](https://github.com/medikoo))
- Adjust deprecation logs to reflect warning format ([#8108](https://github.com/serverless/serverless/issues/8108)) ([b0938c7](https://github.com/serverless/serverless/commit/b0938c7d9bd946c5c9af6bae99ae6f7931242ba6)) ([Mariusz Nowak](https://github.com/medikoo))

## [1.79.0](https://github.com/serverless/serverless/compare/v1.78.1...v1.79.0) (2020-08-19)

### Features

- **Config Schema:**
  - AWS HTTP API schema ([#8068](https://github.com/serverless/serverless/issues/8068)) ([f091c07](https://github.com/serverless/serverless/commit/f091c07992a414f2534c9de80caf76faf2744367)) ([Frédéric Barthelet](https://github.com/fredericbarthelet))
  - Schema for AWS API Gateway's `provider.resourcePolicy` ([#8051](https://github.com/serverless/serverless/issues/8051)) ([20d9c64](https://github.com/serverless/serverless/commit/20d9c6414af9a06e2479d203e62aa6427a80f87f)) ([Geoff Baskwill](https://github.com/glb))

### Bug Fixes

- **AWS API Gateway:** Fix referencing provisioned authorizers ([#8059](https://github.com/serverless/serverless/issues/8059)) ([5a691f4](https://github.com/serverless/serverless/commit/5a691f44573180e1dd5a833aeae196b89a24b697)) ([Mariusz Nowak](https://github.com/medikoo))
- **AWS SQS:** Fix referencing lambdas with provisioned concurrency ([#8059](https://github.com/serverless/serverless/issues/8059)) ([2abb9ad](https://github.com/serverless/serverless/commit/2abb9ad8552d4edc77df5fe1c542373997443950)) ([Mariusz Nowak](https://github.com/medikoo))
- **AWS Credentials:** Fix authentication error message resolution ([#8062](https://github.com/serverless/serverless/issues/8062)) ([2faa20e](https://github.com/serverless/serverless/commit/2faa20e8354d65eed767f88f52919e47edd32866)) ([Mariusz Nowak](https://github.com/medikoo))
- **AWS Lambda:** Ensure to respect `maximumRetryAttempts` set to `0` ([#8048](https://github.com/serverless/serverless/issues/8048)) ([bab0d56](https://github.com/serverless/serverless/commit/bab0d56bd9be6ba1afe0eef352c8732dd7fe4f73)) ([Mariusz Nowak](https://github.com/medikoo))
- **Config Schema:**
  - Report configuration errors as warnings (so it's less confusing) ([#8101](https://github.com/serverless/serverless/issues/8101)) ([e1ee0dc](https://github.com/serverless/serverless/commit/e1ee0dc6f9cf03c872e65d1e258e1162e2d6071e)) ([Mariusz Nowak](https://github.com/medikoo))
  - Recognize catch-all pattern in `disabledDeprecations` property ([#8091](https://github.com/serverless/serverless/issues/8091)) ([c9ee6d5](https://github.com/serverless/serverless/commit/c9ee6d53b688561a154b55dc4fd4fca648ff2ab1)) ([Mariusz Nowak](https://github.com/medikoo))
- **CLI:** Mark `help` as command that doesn't depend on external plugins ([#8056](https://github.com/serverless/serverless/issues/8056)) ([4660acd](https://github.com/serverless/serverless/commit/4660acd324cfa6c786245ea581691a23758ce960)) ([Mariusz Nowak](https://github.com/medikoo))
- **Dashboard:** Ensure service independent commands work unconditionally ([#8056](https://github.com/serverless/serverless/issues/8056)) ([d8a73b8](https://github.com/serverless/serverless/commit/d8a73b8326825b3020fa238057072c837d188d3c)) ([Mariusz Nowak](https://github.com/medikoo))
- **Templates:**
  - Ensure ES7+ support in `aws-nodejs-ecma-script` ([#8064](https://github.com/serverless/serverless/issues/8064)) ([e7efca4](https://github.com/serverless/serverless/commit/e7efca4b421f19b65d88b4bfe973ce5a9ab14d3c)) ([Sam Hulick](https://github.com/ffxsam))
  - Fix `SystemTextJson` initialization in `aws-sharp` ([#8092](https://github.com/serverless/serverless/issues/8092)) ([0490e8b](https://github.com/serverless/serverless/commit/0490e8be2024cd705bbece379897381b88f87148)) ([Matt Davis](https://github.com/mattsonlyattack))
- **Variabless:** Show promises resolution status less frequently (to not interfere with eventual MFA input) ([#8062](https://github.com/serverless/serverless/issues/8062)) ([516603a](https://github.com/serverless/serverless/commit/516603af90b9e1260433c615f8f8f2ad2c68b41d)) ([Mariusz Nowak](https://github.com/medikoo))

### [1.78.1](https://github.com/serverless/serverless/compare/v1.78.0...v1.78.1) (2020-08-04)

### Bug Fixes

- **Config Schema:**
  - Ensure schema for core properties (`frameworkVersion` and `disabledDeprecations`) ([#8044](https://github.com/serverless/serverless/issues/8044)) ([a3f624e](https://github.com/serverless/serverless/commit/a3f624e25cb257afc5d8668a8a5e63e6c67d8827)) ([Mariusz Nowak](https://github.com/medikoo))
  - Fix errors normalization for `oneOf` case ([#8044](https://github.com/serverless/serverless/issues/8044)) ([f4803ee](https://github.com/serverless/serverless/commit/f4803ee363253ebefc1c509d8d808db53bcc6e7a)) ([Mariusz Nowak](https://github.com/medikoo))
  - Fix errors normalization with external refs ([#8044](https://github.com/serverless/serverless/issues/8044)) ([d171f54](https://github.com/serverless/serverless/commit/d171f5476d260f90ff0fe9916aed4a0eea49dfde)) ([Mariusz Nowak](https://github.com/medikoo))

### Maintenance Improvements

- Expose `isStandalone` for metrics ([#8045](https://github.com/serverless/serverless/issues/8045)) ([0ad5cd7](https://github.com/serverless/serverless/commit/0ad5cd7a6333e96b0a041e688bb5eb0a26b98c30)) ([Mariusz Nowak](https://github.com/medikoo))

## [1.78.0](https://github.com/serverless/serverless/compare/v1.77.1...v1.78.0) (2020-08-03)

### Features

- Schema based validation of service config ([#7335](https://github.com/serverless/serverless/issues/7335)) ([268f714](https://github.com/serverless/serverless/commit/268f714357ea909e6897d3377331ed7b1a38e5f5)) ([Petr Reshetin](https://github.com/preshetin) & [Mariusz Nowak](https://github.com/medikoo))
- **AWS Lambda:** Support `maximumEventAge` and `maximumRetryAttempts` ([#7987](https://github.com/serverless/serverless/issues/7987)) ([8573ec1](https://github.com/serverless/serverless/commit/8573ec1e50e4d49baf1a5ae178c32851902f073d)) ([Piotr Grzesik](https://github.com/pgrzesik))

### Bug Fixes

- **AWS EventBridge:**
  - Fix handling of events removal ([#8004](https://github.com/serverless/serverless/issues/8004)) ([41d19b3](https://github.com/serverless/serverless/commit/41d19b3834609ae6bf96439df554b99a082ccb0f)) ([Daniil Bratchenko](https://github.com/bratchenko))
  - Fix attaching lambdas to "default" stage ([#7995](https://github.com/serverless/serverless/issues/7995)) ([b53f080](https://github.com/serverless/serverless/commit/b53f080a4dfc8439333090d2a177ac0272b6d1fe)) ([Pavle Portic](https://github.com/TheEdgeOfCat))
- **Templates:** Ensure missing Kotlin dependencies ([#8010](https://github.com/serverless/serverless/issues/8010)) ([15fae3b](https://github.com/serverless/serverless/commit/15fae3bfb286dfdf72b14f7443a5683d0e4db7de)) ([Diego Marzo](https://github.com/diegomarzo))
- Set `versionFunctions` to true only in AWS provider case ([9897120](https://github.com/serverless/serverless/commit/9897120a8adae59205e5d84d1bdca442621f51b4)) ([Mariusz Nowak](https://github.com/medikoo))

### [1.77.1](https://github.com/serverless/serverless/compare/v1.77.0...v1.77.1) (2020-07-28)

### Bug Fixes

- **AWS Local Invocation:** Ensure java wrappers are moved to runtimeWrappers ([#7999](https://github.com/serverless/serverless/issues/7999)) ([03531d8](https://github.com/serverless/serverless/commit/03531d8bc6bce44a445e34e5046eaef6d95d0aa1)) ([Yuji Yamano](https://github.com/yyamano))
- **AWS Credentials:**
  - Improve AWS SDK workaround ([#8002](https://github.com/serverless/serverless/issues/8002)) ([32cde98](https://github.com/serverless/serverless/commit/32cde98750a91449d352187a8e2f042a38eb3f64)) ([Mariusz Nowak](https://github.com/medikoo))
  - Improve credentials error recognition ([#8002](https://github.com/serverless/serverless/issues/8002)) ([863bc51](https://github.com/serverless/serverless/commit/863bc51904778dbfcb984c663517172c8292ff9d)) ([Mariusz Nowak](https://github.com/medikoo))

## [1.77.0](https://github.com/serverless/serverless/compare/v1.76.1...v1.77.0) (2020-07-27)

### Features

- **Templates:** Add `aws-kotlin-jvm-gradle-kts` template ([#7992](https://github.com/serverless/serverless/issues/7992)) ([4727216](https://github.com/serverless/serverless/commit/4727216760e16d5a11402f74fdcf38c70a8634be)) ([Diego Marzo](https://github.com/diegomarzo))

### Bug Fixes

- **Standalone:** Ensure local invocation wrappers are accessible ([#7982](https://github.com/serverless/serverless/issues/7982)) ([527233d](https://github.com/serverless/serverless/commit/527233d2637977544169e6799d9359c86425de18)) ([Mariusz Nowak](https://github.com/medikoo))
- Fix aws-sdk workaround ([#7984](https://github.com/serverless/serverless/issues/7984)) ([de38640](https://github.com/serverless/serverless/commit/de386405b206d3ebace105992e9c7eb7ad6d7f94)) ([Mariusz Nowak](https://github.com/medikoo))
- **Templates:** Add aws-lambda-java-events support to Java ([#7986](https://github.com/serverless/serverless/issues/7986)) ([ab99b65](https://github.com/serverless/serverless/commit/ab99b657a3c613b3e9ba072e084d159f5ac6c073)) ([Yuji Yamano](https://github.com/yyamano))
- Recognize final DELETE_COMPLETE event with verbose flag ([#7979](https://github.com/serverless/serverless/issues/7979)) ([e980625](https://github.com/serverless/serverless/commit/e980625f586f55da4559b362a9dcd7275e9001bb)) ([devops hipster in training.](https://github.com/herebebogans))
- **AWS API Gateway:** Ensure correct type for StatusCode property ([#7977](https://github.com/serverless/serverless/issues/7977)) ([d0edb5d](https://github.com/serverless/serverless/commit/d0edb5d85991bd6563610c768da80e0791735bc8)) ([Lucas Astrada](https://github.com/Undre4m))

### [1.76.1](https://github.com/serverless/serverless/compare/v1.76.0...v1.76.1) (2020-07-23)

### Bug Fixes

- Ensure to package CLI script ([a687e91](https://github.com/serverless/serverless/commit/a687e9190d861f11ec1fc9a194335b3012b246b9)) ([Mariusz Nowak](https://github.com/medikoo))

## [1.76.0](https://github.com/serverless/serverless/compare/v1.75.1...v1.76.0) (2020-07-23)

### Features

- **AWS ALB:** Support health check configuration for target groups ([#7947](https://github.com/serverless/serverless/issues/7947)) ([a2f977c](https://github.com/serverless/serverless/commit/a2f977c8ced67e5002ce5735ce30d44cc36b17be)) ([David Septimus](https://github.com/DavidSeptimus))
- **Templates:** Upgrade `gradle-wrapper` and `gradle` in Java runtime templates ([#7972](https://github.com/serverless/serverless/issues/7972)) ([6da0964](https://github.com/serverless/serverless/commit/6da09649bb6cbc9074d5dec574856acc8eaa388d)) ([Yuji Yamano](https://github.com/yyamano))

### Bug Fixes

- Fix AWS missing credentials handling ([#7963](https://github.com/serverless/serverless/issues/7963)) ([7af0cd8](https://github.com/serverless/serverless/commit/7af0cd8c280e0f4fc374e859c0223bc0c3455f63)) ([Mariusz Nowak](https://github.com/medikoo))
- Fix packaged files permissions ([#7965](https://github.com/serverless/serverless/issues/7965)) ([cae2885](https://github.com/serverless/serverless/commit/cae28851df435fd9eb0d651fde520862125d5deb)) ([Mariusz Nowak](https://github.com/medikoo))
- **AWS Local Invocation:** Add `java11` support. ([#7956](https://github.com/serverless/serverless/issues/7956)) ([dc1edc1](https://github.com/serverless/serverless/commit/dc1edc10c0088f57b104b8296df6f78d6205b4a0)) ([Yuji Yamano](https://github.com/yyamano))
- **Templates:**
  - Fix java `invoke-bridge` build error handling ([#7968](https://github.com/serverless/serverless/issues/7968)) ([87e7480](https://github.com/serverless/serverless/commit/87e7480663fe7d3513687e9127fdca8b143cf1d6)) ([Yuji Yamano](https://github.com/yyamano))
  - Fix incomplete migration into dayjs from moment ([#7961](https://github.com/serverless/serverless/issues/7961)) ([d5ce246](https://github.com/serverless/serverless/commit/d5ce24681e3a75eccce290a52e045664878b9387)) ([Yuji Yamano](https://github.com/yyamano))
  - Set `ContextClassLoader` for `groovy` and `clojure` ([#7955](https://github.com/serverless/serverless/issues/7955)) ([25263fd](https://github.com/serverless/serverless/commit/25263fd473584e51c81bb3c5cedd4b9005dfd984)) ([Yuji Yamano](https://github.com/yyamano))
  - Upgrade Java 3rd party libraries used for invokeLocal([#7930](https://github.com/serverless/serverless/issues/7930)) ([851b856](https://github.com/serverless/serverless/commit/851b85629dbff510ceb1865fd9a1a48a75940ebd)) ([Yuji Yamano](https://github.com/yyamano))

### Maintenance Improvements

- Remove no longger needed Node.js deprecation logs supression ([#7964](https://github.com/serverless/serverless/issues/7964)) ([af89ab8](https://github.com/serverless/serverless/commit/af89ab8994aaaa12e578b2bad72ddc8a948e765c)) ([Mariusz Nowak](https://github.com/medikoo))
- **CLI:**
  - Cleanup components CLI resolution logic ([#7964](https://github.com/serverless/serverless/issues/7964)) ([cf1d51d](https://github.com/serverless/serverless/commit/cf1d51dbb9b218dfc1cebfa1bf3c5f6eb1ab248b))([Mariusz Nowak](https://github.com/medikoo))
  - Seclude Framework CLI script ([#7964](https://github.com/serverless/serverless/issues/7964)) ([dc826b4](https://github.com/serverless/serverless/commit/dc826b4fdd387bfef0cc74a69e0370815011901b))([Mariusz Nowak](https://github.com/medikoo))

### [1.75.1](https://github.com/serverless/serverless/compare/v1.75.0...v1.75.1) (2020-07-16)

### Bug Fixes

- **CLI:** Ensure `--version` is only top level command option ([#7949](https://github.com/serverless/serverless/issues/7949)) ([1f7534c](https://github.com/serverless/serverless/commit/1f7534c4d89a0e37e61a8eea76f6f0241909d265)) ([Mariusz Nowak](https://github.com/medikoo))
- **AWS Deploy:** Fix resolution of SLS_AWS_REQUEST_MAX_RETRIES setting ([da1b75a](https://github.com/serverless/serverless/commit/da1b75ac889f99a82afa5606e4e0f1f7f3ee2bcf)) ([Mariusz Nowak](https://github.com/medikoo))

## [1.75.0](https://github.com/serverless/serverless/compare/v1.74.1...v1.75.0) (2020-07-15)

### Features

- **AWS HTTP API:**
  - Allow use of CF ImportValue for httpApi id ([#7905](https://github.com/serverless/serverless/issues/7905)) ([5a444c4](https://github.com/serverless/serverless/commit/5a444c415ce31b2c219be47390be165a8da233ea)) ([Frédéric Barthelet](https://github.com/fredericbarthelet))
  - Deprecate payload 1.0 default ([#7919](https://github.com/serverless/serverless/issues/7919)) ([ec954f6](https://github.com/serverless/serverless/commit/ec954f61220f48b379bf4903820bdbb7c2352caf)) ([andreizet](https://github.com/andreizet))
- **AWS API Gateway:** Support integration mapping of request headers [#7897](https://github.com/serverless/serverless/issues/7897) ([56b335f](https://github.com/serverless/serverless/commit/56b335f99930aa9c2a35ce28e68dfea6d5bf3b7f)) ([Ben Arena](https://github.com/benarena))
- **AWS Deploy:** Support customization of request retries count ([6c2fabf](https://github.com/serverless/serverless/commit/6c2fabf9b98fea921a497c7ad15f4943e78c9b73)) ([Mariusz Nowak](https://github.com/medikoo))
- **Templates:**
  - Improve TypeScript template ([#7934](https://github.com/serverless/serverless/issues/7934)) ([5e322c8](https://github.com/serverless/serverless/commit/5e322c87358cd33e7c703ae3ab5e9f1cf863c7e1)) ([Frédéric Barthelet](https://github.com/fredericbarthelet))
  - Upgrade azure-nodejs template ([#7918](https://github.com/serverless/serverless/issues/7918)) ([a88cf00](https://github.com/serverless/serverless/commit/a88cf00ae7d306341771d9445f3aba6f06d46fa7)) ([Ian Anderson](https://github.com/getfatday))
- Deprecate not maintained Node.js versions ([#7918](https://github.com/serverless/serverless/issues/7918)) ([a1f2fdb](https://github.com/serverless/serverless/commit/a1f2fdb5cf077a51d7427dd7fc803d6f60dd5cc9)) ([Mariusz Nowak](https://github.com/medikoo))
- Expose `logDeprecation` through which plugins may signal deprecations [#7941](https://github.com/serverless/serverless/issues/7941) ([f444a8d](https://github.com/serverless/serverless/commit/f444a8d0a11434d89f1e2b2df5045850c45664c9)) ([Mariusz Nowak](https://github.com/medikoo))
- Send list of sevice npm dependencies for notifications generator [#7940](https://github.com/serverless/serverless/issues/7940) ([dba0548](https://github.com/serverless/serverless/commit/dba05481d10d0ffbf198990c9b460bb0b0ad24d2)) ([Mariusz Nowak](https://github.com/medikoo))

### Bug Fixes

- **CLI:**
  - Ensure to show help and version in context of invalid service [#7924](https://github.com/serverless/serverless/issues/7924) ([3ffa549](https://github.com/serverless/serverless/commit/3ffa54918342aeb9c334631c6f710aba234ba241)) ([Mariusz Nowak](https://github.com/medikoo))
  - Show interactive help unconditionally on `--help-interactive` [#7924](https://github.com/serverless/serverless/issues/7924) ([ff0af1e](https://github.com/serverless/serverless/commit/ff0af1e6ac8b89b4d610c141c78fe0fea843a5de)) ([Mariusz Nowak](https://github.com/medikoo))
  - Show version info unconditionally on `-v` or `--version` [#7924](https://github.com/serverless/serverless/issues/7924) ([c042dd5](https://github.com/serverless/serverless/commit/c042dd5144e4e283e565da97933d03bc70b3c8e9)) ([Mariusz Nowak](https://github.com/medikoo))
  - Communicate access to Components CLI [#7942](https://github.com/serverless/serverless/issues/7942) ([79b4718](https://github.com/serverless/serverless/commit/79b4718dec5de1d567af25d1abd0e46d87ff1c6e)) ([Mariusz Nowak](https://github.com/medikoo))
  - Ensure deprecation logs support mute settings from service config [#7941](https://github.com/serverless/serverless/issues/7941) ([4e69c76](https://github.com/serverless/serverless/commit/4e69c76e07a862981e8a9ea9011c98098c9da347)) ([Mariusz Nowak](https://github.com/medikoo))
- **Templates:** Fix `PackageReference` in _aws-fsharp_ template ([#7914](https://github.com/serverless/serverless/issues/7914)) ([7848b6d](https://github.com/serverless/serverless/commit/7848b6d033ec4a7c64186e5f2306351128100be4)) ([Matt Davis](https://github.com/mattsonlyattack))
- Improve error handling in config file resolution [#7924](https://github.com/serverless/serverless/issues/7924) ([de2c68d](https://github.com/serverless/serverless/commit/de2c68d02312f047aa7f83b0b339074b40df7854)) ([Mariusz Nowak](https://github.com/medikoo))
- Throw operational error as operational [#7924](https://github.com/serverless/serverless/issues/7924) ([f965e44](https://github.com/serverless/serverless/commit/f965e446946048691889a7f3723c19ac747b8fe2)) ([Mariusz Nowak](https://github.com/medikoo))

### Maintenance Improvements

- **`lodash` replacement:**
  - Replace `_.concat` with `array.concat` ([#7851](https://github.com/serverless/serverless/issues/7851)) ([fce0b18](https://github.com/serverless/serverless/commit/fce0b1886448d91be21aa64b778c98d95bb47b87)) ([RT](https://github.com/RT1918))
  - Replace `_.findKey` with `Object.keys(object).find` ([#7881](https://github.com/serverless/serverless/issues/7881)) ([d6cf036](https://github.com/serverless/serverless/commit/d6cf036c1647ce68d75b15e831e00f1cec6a97be)) ([Duc Nguyen](https://github.com/vietduc01100001))
  - Replace `_.has` with better counterparts ([#7915](https://github.com/serverless/serverless/issues/7915)) ([7bbd04a](https://github.com/serverless/serverless/commit/7bbd04a6933c1631646f16670e3d85c357450e7a)) ([andreizet](https://github.com/andreizet))
  - Replace `_.keyBy` with native constructs ([#7882](https://github.com/serverless/serverless/issues/7882)) ([e7163ce](https://github.com/serverless/serverless/commit/e7163ceaaceeb93971350b7ccd9cc618b15e4f9b)) ([Duc Nguyen](https://github.com/vietduc01100001))
  - Replace `_.some` usage with `array.some` ([#7901](https://github.com/serverless/serverless/issues/7901)) ([75bf185](https://github.com/serverless/serverless/commit/75bf185785dc2b0a91b6500f353df92990e90f47)) ([Piotr Grzesik](https://github.com/pgrzesik))
  - Replace `_.toString` with native `String` ([#7893](https://github.com/serverless/serverless/issues/7893)) ([028e467](https://github.com/serverless/serverless/commit/028e46720251901279b8230cf76deca721ee4ae6)) ([Anh Dev](https://github.com/anhdevit))

### [1.74.1](https://github.com/serverless/serverless/compare/v1.74.0...v1.74.1) (2020-06-29)

### Bug Fixes

- **AWS Deploy:** Ensure no duplicate (case-insensitive) stack tags ([#7887](https://github.com/serverless/serverless/issues/7887)) ([71919f1](https://github.com/serverless/serverless/commit/71919f1d1f34386fa3429e3e47196c849218f82b)) ([MickVanDuijn](https://github.com/MickVanDuijn))
- **Standalone:**
  - Ensure reliable access from China ([#7891](https://github.com/serverless/serverless/issues/7891)) ([6fccede](https://github.com/serverless/serverless/commit/6fccedea4ac5a3a546d36b19d2e0701defd9ed85)) ([Mariusz Nowak](https://github.com/medikoo))
  - Support SLS_GEO_LOCATION env var ([#7891](https://github.com/serverless/serverless/issues/7891)) ([474df11](https://github.com/serverless/serverless/commit/474df11288a0431bb14947c4a08ae34edecb4164)) ([Mariusz Nowak](https://github.com/medikoo))

### Maintenance Improvements

- **`lodash` replacement:**
  - Remove `_.isInteger` ([#7878](https://github.com/serverless/serverless/issues/7878)) ([3b19a5a](https://github.com/serverless/serverless/commit/3b19a5a6b191fdb0dac5a81d1244159e0da9e0bd)) ([Dai Van Nguyen](https://github.com/nvdai2401))

## [1.74.0](https://github.com/serverless/serverless/compare/v1.73.1...v1.74.0) (2020-06-26)

### Features

- **AWS ALB:** Support built-in authentication through `onUnauthenticatedRequest` ([#7780](https://github.com/serverless/serverless/issues/7780)) ([b976677](https://github.com/serverless/serverless/commit/b9766775148b15f8b19fd9d657149813cb5e8bfa)) ([Kamaz](https://github.com/kamaz))

### Bug Fixes

- **AWS HTTP API:** Respect logRetentionInDays setting ([#7856](https://github.com/serverless/serverless/issues/7856)) ([9dad77c](https://github.com/serverless/serverless/commit/9dad77ce1b12218f3c38b62c716d4dbc9d68bb5d)) ([Jonne Deprez](https://github.com/jonnedeprez))
- **AWS Websocket:** Fix resources dependency chain ([9c0f646](https://github.com/serverless/serverless/commit/9c0f6461b73976958ebdd7e2762c6d1fbd469da1)) ([Mariusz Nowak](https://github.com/medikoo))

### Maintenance Improvements

- **`lodash` replacement:**
  - Remove `_.isBoolean` usage ([#7880](https://github.com/serverless/serverless/issues/7880)) ([57f70f9](https://github.com/serverless/serverless/commit/57f70f93eb3c24b802c842fb6e395591a70a3270)) ([Anh Dev](https://github.com/anhdevit))
  - Replace `_.chain` with native constructs ([#7862](https://github.com/serverless/serverless/issues/7862)) ([288cb25](https://github.com/serverless/serverless/commit/288cb255acda29b15e10b10efcddee1b491a9b5d)) ([Nguyễn Việt Đức](https://github.com/vietduc01100001))
  - Replace `_.compact` with `array.filter(Boolean)` ([#7858](https://github.com/serverless/serverless/issues/7858)) ([7e68a0c](https://github.com/serverless/serverless/commit/7e68a0c90f19ff9d8cfaab8f064628e72db2a054)) ([Çalgan Aygün](https://github.com/calganaygun))
  - Replace `_.isEmpty` with native counterparts ([#7873](https://github.com/serverless/serverless/issues/7873)) ([4c33476](https://github.com/serverless/serverless/commit/4c33476210d355b9b822909685a951a4d970f467)) ([Dai Van Nguyen](https://github.com/nvdai2401))
  - Replace `_.min` with native constructs ([#7840](https://github.com/serverless/serverless/issues/7840)) ([ee94dce](https://github.com/serverless/serverless/commit/ee94dce47ce989c7af2d54fc8c7dc24beab43ee8)) ([Nguyễn Việt Đức](https://github.com/vietduc01100001))
  - Replace `_.parseInt` with `Number` ([#7877](https://github.com/serverless/serverless/issues/7877)) ([f2e1942](https://github.com/serverless/serverless/commit/f2e19420e9a639b1523958cb406d7bd178571248)) ([Dai Van Nguyen](https://github.com/nvdai2401))
  - Replace `_.pullAllWith` with native constructs ([#7861](https://github.com/serverless/serverless/issues/7861)) ([f6743e9](https://github.com/serverless/serverless/commit/f6743e9b35bf821109ffb18039ea9cf419a7ad18)) ([Çalgan Aygün](https://github.com/calganaygun))
  - Replace `_.reduce` with `array.reduce` ([#7883](https://github.com/serverless/serverless/issues/7883)) ([297f7d8](https://github.com/serverless/serverless/commit/297f7d85e07469f8157dfb6befb697f8dc0305d7)) ([Dai Van Nguyen](https://github.com/nvdai2401))
  - Replace `_.sortBy` with `array.sort` ([#7823](https://github.com/serverless/serverless/issues/7823)) ([57e4212](https://github.com/serverless/serverless/commit/57e4212671ea3027fab9482e6006933e4c5b6c55)) ([Nguyễn Việt Đức](https://github.com/vietduc01100001))

### [1.73.1](https://github.com/serverless/serverless/compare/v1.73.0...v1.73.1) (2020-06-16)

### Bug Fixes

- **AWS API Gateway:** Fix handling of `usagePlan` array ([85cc447](https://github.com/serverless/serverless/commit/85cc4476b35b144ed28e71302230df2d626a4e60)) ([Mariusz Nowak](https://github.com/medikoo))

## [1.73.0](https://github.com/serverless/serverless/compare/v1.72.0...v1.73.0) (2020-06-16)

### Features

- **AWS Stream:** Add support for `maximumRecordAgeInSeconds` property ([#7833](https://github.com/serverless/serverless/issues/7833)) ([003fcfb](https://github.com/serverless/serverless/commit/003fcfb8fc1b083e01daa2e478086ee89e74c644)) ([Demián Rodriguez](https://github.com/demian85))
- Drop old and support new analytics endpoint, display notifications as returned by backend ([#7811](https://github.com/serverless/serverless/issues/7811)) ([49b5914](https://github.com/serverless/serverless/commit/49b5914378038a9a35433e40233e9f49acd0e964)) ([Mariusz Nowak](https://github.com/medikoo))

### Bug Fixes

- **AWS SQS:** Revert support for `maximumRetryAttempts` option ([#7832](https://github.com/serverless/serverless/issues/7832)) ([5a5a986](https://github.com/serverless/serverless/commit/5a5a9864149e962375bb252adcaf32bbe10662da)) ([Mariusz Nowak](https://github.com/medikoo))
- Ensure `serverless.ts` is handled properly at plugin commands ([#7806](https://github.com/serverless/serverless/issues/7806)) ([dc96b9a](https://github.com/serverless/serverless/commit/dc96b9a876b04e10ced474b7bb32416a204c67a3)) ([Bryan Hunter](https://github.com/bryan-hunter))

### Maintenance Improvements

- **`lodash` replacement:**
  - Replace `_.first`with `array[0]` ([#7816](https://github.com/serverless/serverless/issues/7816)) ([a527744](https://github.com/serverless/serverless/commit/a527744606a7dd9dd9caf0a376eb615f0b81a40f)) ([Chris Villanueva](https://github.com/chrisVillanueva))
  - Replace `_.head` with `array[0]` ([#7817](https://github.com/serverless/serverless/issues/7817)) ([8991ceb](https://github.com/serverless/serverless/commit/8991ceb209884f72beba0ab8b166a258c0af3e1d)) ([Chris Villanueva](https://github.com/chrisVillanueva))
  - Replace `_.includes` with `val.includes` ([#7818](https://github.com/serverless/serverless/issues/7818)) ([77fbb59](https://github.com/serverless/serverless/commit/77fbb5969b31bdd0d2220019f896df5a9f36e6fe)) ([Chris Villanueva](https://github.com/chrisVillanueva))
  - Replace `_.indexOf` with `arr.includes` ([#7825](https://github.com/serverless/serverless/issues/7825)) ([332524d](https://github.com/serverless/serverless/commit/332524dae73cb102c244d3b568ec880f9bc816aa)) ([Nguyễn Việt Đức](https://github.com/vietduc01100001))
  - Replace `_.isFunction` with `typeof value === 'function'` ([#7810](https://github.com/serverless/serverless/issues/7810)) ([e42ab2c](https://github.com/serverless/serverless/commit/e42ab2cda65d3986ce78f81da10c7149019162a2)) ([Wing-Kam](https://github.com/wingkwong))
  - Replace `_.isNil(value)` with `value == null` ([#7809](https://github.com/serverless/serverless/issues/7809)) ([6cf4901](https://github.com/serverless/serverless/commit/6cf4901a8907ddfb36dc45ee1e094a7dff401360)) ([Wing-Kam](https://github.com/wingkwong))
  - Replace `_.isString(value)` with `typeof value === 'string'` ([#7812](https://github.com/serverless/serverless/issues/7812)) ([9f3ee94](https://github.com/serverless/serverless/commit/9f3ee94a74a4d9d80451143a5f212d0b6f790a5f)) ([Wing-Kam](https://github.com/wingkwong))
  - Replace `_.isUndefined` with native checks ([#7826](https://github.com/serverless/serverless/issues/7826)) ([20cef81](https://github.com/serverless/serverless/commit/20cef81555473311128ed425125d017c1ab6729c)) ([Nguyễn Việt Đức](https://github.com/vietduc01100001))
  - Replace `_.join` with `array.join` ([#7805](https://github.com/serverless/serverless/issues/7805)) ([5cf46bf](https://github.com/serverless/serverless/commit/5cf46bf109287bcd327e6f45f58b3f392cc345de)) ([Chris Villanueva](https://github.com/chrisVillanueva))
  - Replace `_.map` with `array.map` ([#7827](https://github.com/serverless/serverless/issues/7827)) ([4c6f8be](https://github.com/serverless/serverless/commit/4c6f8be5ccae88034e19f72a53996208dd4a56d5)) ([Nguyễn Việt Đức](https://github.com/vietduc01100001))
  - Replace `_.nth` with `array[index]` ([#7841](https://github.com/serverless/serverless/issues/7841)) ([d5de0ec](https://github.com/serverless/serverless/commit/d5de0ec56aabff10ab6de8913b1b68730aa63fcd)) ([Nguyễn Việt Đức](https://github.com/vietduc01100001))
  - Replace `_.repeat` with `string.repeat` ([#7842](https://github.com/serverless/serverless/issues/7842)) ([a549517](https://github.com/serverless/serverless/commit/a5495174413cead282dc09959ec251ee8444a06a)) ([Nguyễn Việt Đức](https://github.com/vietduc01100001))
  - Replace `_.replace` with `string.replace` ([#7843](https://github.com/serverless/serverless/issues/7843)) ([aaa2f96](https://github.com/serverless/serverless/commit/aaa2f965a73ade5c691f0f935c5d37283ba7cd8a)) ([Nguyễn Việt Đức](https://github.com/vietduc01100001))
  - Replace `_.split` with `string.split` ([#7820](https://github.com/serverless/serverless/issues/7820)) ([053f5f4](https://github.com/serverless/serverless/commit/053f5f420b45e9dec794e82d1bc23a2731a077ff)) ([srd2014](https://github.com/srd2014))
  - Replace `_.takeRight` with `array.slice` ([#7831](https://github.com/serverless/serverless/issues/7831)) ([3b3db7a](https://github.com/serverless/serverless/commit/3b3db7ad29996e204bdef605d0c191cd610148d2)) ([Jishnu Mohan P R](https://github.com/jishnu-mohan))
  - Replace `_.toUpper(string)` with `string.toUpperCase` ([#7808](https://github.com/serverless/serverless/issues/7808)) ([22a4ed2](https://github.com/serverless/serverless/commit/22a4ed27e262cbf13cb0df14df32a2c4bc2a0c9d)) ([Wing-Kam](https://github.com/wingkwong))
  - Replace `_.unset` with `delete` ([#7813](https://github.com/serverless/serverless/issues/7813)) ([e39cdfd](https://github.com/serverless/serverless/commit/e39cdfdf02adba8b83f4bbf83208fdf81e32c1d7)) ([Chris Villanueva](https://github.com/chrisVillanueva))
- Switch to `@serverless/util/config` ([#7811](https://github.com/serverless/serverless/issues/7811)) ([96afed4](https://github.com/serverless/serverless/commit/96afed438cde47a9fc75736ba22485ec90c7eb5a)) ([Mariusz Nowak](https://github.com/medikoo))

## [1.72.0](https://github.com/serverless/serverless/compare/v1.71.3...v1.72.0) (2020-06-02)

### Features

- **AWS API Gateway:**
  - Simplify referencing local CognitoUserPool ([#7799](https://github.com/serverless/serverless/issues/7799)) ([2e4377e](https://github.com/serverless/serverless/commit/2e4377ecf038401456c3fca29feeab624846a300)) ([Alex DeBrie](https://github.com/alexdebrie))
  - Support `customerId` in API keys ([#7786](https://github.com/serverless/serverless/issues/7786)) ([c6894b5](https://github.com/serverless/serverless/commit/c6894b5129c14a43fce0017187cf69aa1bdc9185)) ([Greg Campion](https://github.com/gcampionpae))
  - Support toggling CloudWatch metrics ([#7754](https://github.com/serverless/serverless/issues/7754)) ([87d40aa](https://github.com/serverless/serverless/commit/87d40aa8a7fea136a9c05d6e3c350b0d24a58183)) ([Satoru Kikuchi](https://github.com/s-kikuchi))
- **AWS HTTP API:** Support externally configured JWT authorizers ([#7789](https://github.com/serverless/serverless/issues/7789)) ([4074739](https://github.com/serverless/serverless/commit/4074739476e22631b0e06a9d23a2e21d8f29c21e)) ([Michał Mrozek](https://github.com/Michsior14))
- **CLI:**
  - Deprecations logger ([#7741](https://github.com/serverless/serverless/issues/7741)) ([6f32f23](https://github.com/serverless/serverless/commit/6f32f236d8c44464b34e8c666e4ecbb3abe287d4)) ([Ahmad Mahmoud Mohammad](https://github.com/AhmedFat7y) & [Mariusz Nowak](https://github.com/medikoo))
  - Deprecate `bin/serverless` binary ([#7759](https://github.com/serverless/serverless/issues/7759)) ([a60d2c7](https://github.com/serverless/serverless/commit/a60d2c7dd8648a17c9ca09c363d3ab88b797a11c)) ([Mariusz Nowak](https://github.com/medikoo))
- **Templates:** Azure C# template ([#7738](https://github.com/serverless/serverless/issues/7738)) ([9611137](https://github.com/serverless/serverless/commit/96111379823fc1fc68835b9bcdb4f0f585ff554e)) ([Tanner Barlow](https://github.com/tbarlow12))
- **Variables:** Support non-function exports in js files ([#7540](https://github.com/serverless/serverless/issues/7540)) ([89ba272](https://github.com/serverless/serverless/commit/89ba272a63a153df0655c85a5d5a2487580c73a1)) ([Steven Rapp](https://github.com/srapp))
- Support `serverless.ts` (TypeScript type) as configuration input ([#7755](https://github.com/serverless/serverless/issues/7755)) ([4db8b63](https://github.com/serverless/serverless/commit/4db8b630a285d40b117d7043f024cb3e036951b4)) ([Bryan Hunter](https://github.com/bryan-hunter))

### Bug Fixes

- **AWS API Gateway:**
  - Fix API key names resolution ([#7804](https://github.com/serverless/serverless/issues/7804)) ([f9f6a3b](https://github.com/serverless/serverless/commit/f9f6a3b560f70b81ce0ab6f802e05596bd700916)) ([Mariusz Nowak](https://github.com/medikoo))
  - Apply contentHandling only to successful responses ([#7757](https://github.com/serverless/serverless/issues/7757)) ([aa48f0a](https://github.com/serverless/serverless/commit/aa48f0a0766fc07e6e3ca4bb7ba4b6ad3427cc03)) ([Thomas Aribart](https://github.com/ThomasAribart))
- Downgrade `uuid` to v3 ([#7778](https://github.com/serverless/serverless/issues/7778)) ([e9be1c8](https://github.com/serverless/serverless/commit/e9be1c8c6f3b6f105f0e6d9f4383e7cbe16e62ff)) ([Mariusz Nowak](https://github.com/medikoo))

### Maintenance Improvements

- **`lodash` replacement:**
  - Replace `_.assign` and `_.extend` with `Object.assign` ([#7766](https://github.com/serverless/serverless/issues/7766)) ([85e9cd4](https://github.com/serverless/serverless/commit/85e9cd4455bb631be921a12a37f2174fd50ecec6)) ([Nguyễn Việt Đức](https://github.com/vietduc01100001))
  - Replace `_.every` with `array.every` ([#7764](https://github.com/serverless/serverless/issues/7764)) ([d1721cb](https://github.com/serverless/serverless/commit/d1721cb2b4b5a6b3621eba78dbe27eead21f9164)) ([Chris Villanueva](https://github.com/chrisVillanueva))
  - Replace `_.filter` with `array.filter` ([#7775](https://github.com/serverless/serverless/issues/7775)) ([dac7c56](https://github.com/serverless/serverless/commit/dac7c56b26dbe2b3489e88329dd70e0787c73087)) ([Midhun Rajendran](https://github.com/rmidhun23))
  - Replace `_.keys` with `Object.keys` ([#7784](https://github.com/serverless/serverless/issues/7784)) ([d43241e](https://github.com/serverless/serverless/commit/d43241ea8bacc43d3105ba8600674a7564cb6895)) ([Chris Villanueva](https://github.com/chrisVillanueva))
  - Replace `_.find` with `array.find` ([#7782](https://github.com/serverless/serverless/issues/7782)) ([0036962](https://github.com/serverless/serverless/commit/003696260c43acf2415fa6b05a212ea57bdec3d4)) ([Chris Villanueva](https://github.com/chrisVillanueva))
  - Replace `_.forEach` and `_.each` with array.forEach ([#7748](https://github.com/serverless/serverless/issues/7748)) ([5e0af21](https://github.com/serverless/serverless/commit/5e0af21313b1061666b355b2b83737eb5f2dccf0)) ([Tatsuno Yasuhiro](https://github.com/exoego))
  - Replace `_.size` with native counterparts ([#7798](https://github.com/serverless/serverless/issues/7798)) ([2b00928](https://github.com/serverless/serverless/commit/2b00928f87901bfd432f34e181d85aed65837841)) ([Chris Villanueva](https://github.com/chrisVillanueva))
- **Dependency upgrades:**
  - Replace `inquirer` with `@serverless/inquirer` ([#7729](https://github.com/serverless/serverless/issues/7729)) ([4724cb8](https://github.com/serverless/serverless/commit/4724cb8eeb16a35695c1f4b166b81c0cc2e4ddae)) ([Ahmad Mahmoud Mohammad](https://github.com/AhmedFat7y))
  - Upgrade `json-refs` to v3 ([#7763](https://github.com/serverless/serverless/issues/7763)) ([97e99fc](https://github.com/serverless/serverless/commit/97e99fc8f09feb45f31d4934c3f5cb1db2e0193a)) ([Frédéric Barthelet](https://github.com/fredericbarthelet))
  - Upgrade `globby` to v9 ([#7750](https://github.com/serverless/serverless/issues/7750)) ([b245596](https://github.com/serverless/serverless/commit/b245596dbb76e6cdea081e3c6510976587e7e82f)) ([Nguyễn Việt Đức](https://github.com/vietduc01100001))

### [1.71.3](https://github.com/serverless/serverless/compare/v1.71.2...v1.71.3) (2020-05-20)

### Bug Fixes

- **AWS Deploy:** Fix packaging logic after regression introduced with [#7742](https://github.com/serverless/serverless/issues/7742) ([b97e2b4](https://github.com/serverless/serverless/commit/b97e2b421138def7131069771fc820e81edafc73)) ([Mariusz Nowak](https://github.com/medikoo))

### [1.71.2](https://github.com/serverless/serverless/compare/v1.71.1...v1.71.2) (2020-05-20)

### Bug Fixes

- **AWS CloudFront:** Fix merge of template configuration ([#7739](https://github.com/serverless/serverless/issues/7739)) ([304a502](https://github.com/serverless/serverless/commit/304a50261dbccfe73b7eb9f6e6210209f63051ad)) ([Antonio Caiazzo](https://github.com/antoniocaiazzo))
- **AWS Local Invocation:** Ensure to mount as read only in docker ([#7622](https://github.com/serverless/serverless/issues/7622)) ([4252422](https://github.com/serverless/serverless/commit/4252422a94857eb3b446562ba3b24188f0116f19)) ([Alex Soto](https://github.com/apsoto))
- **AWS Deploy:** Fix changes detection when user package artifact is involved ([#7742](https://github.com/serverless/serverless/issues/7742)) ([05499e6](https://github.com/serverless/serverless/commit/05499e6083d4b36ba9b80b271b2becf4249dbbc6)) ([Tatsuno Yasuhiro](https://github.com/exoego))

### Performance Improvements

- **AWS Deploy:** Do not re-upload unchanged lambda layers ([#7680](https://github.com/serverless/serverless/issues/7680)) ([2b9f63e](https://github.com/serverless/serverless/commit/2b9f63e3329d6e28c0a87d58658b0afde557053e)) ([Tatsuno Yasuhiro](https://github.com/exoego))

### Maintenance Improvements

- Replace `_.{startsWith,endsWith,includes}` with native methods ([#7715](https://github.com/serverless/serverless/issues/7715)) ([8bb5517](https://github.com/serverless/serverless/commit/8bb55174562c379ae14e5d1b90db3ed2b25038bd)) ([Tatsuno Yasuhiro](https://github.com/exoego))
- Upgrade `globby` to v9 ([#7750](https://github.com/serverless/serverless/issues/7750)) ([b245596](https://github.com/serverless/serverless/commit/b245596dbb76e6cdea081e3c6510976587e7e82f)) ([Nguyễn Việt Đức](https://github.com/vietduc01100001))

### [1.71.1](https://github.com/serverless/serverless/compare/v1.71.0...v1.71.1) (2020-05-15)

### Bug Fixes

- **CLI:** Fix handling of singular `--config` param ([7bcad68](https://github.com/serverless/serverless/commit/7bcad688c515a8c504f8958b7e15f3ac6d90e0d0)) ([Mariusz Nowak](https://github.com/medikoo))
- **Standalone:** Workaround `fs-extra` v8 bug in chocolatey package generation script ([548bd98](https://github.com/serverless/serverless/commit/548bd986e4dafcae207ae80c3a8c3f956fbce037)) ([Mariusz Nowak](https://github.com/medikoo))

## [1.71.0](https://github.com/serverless/serverless/compare/v1.70.1...v1.71.0) (2020-05-15)

### Features

- **AWS Lambda:** Support `disableLogs` setting for functions, to disable generation of log group resources ([#7720](https://github.com/serverless/serverless/issues/7720)) ([3144be8](https://github.com/serverless/serverless/commit/3144be82d1a5cd966ed5fb7851cc481e71fe4608)) ([Ahmad Mahmoud Mohammad](https://github.com/AhmedFat7y))
- Support `provider.stackParameters` for configuring CloudFormation deployment Parameters ([#7677](https://github.com/serverless/serverless/issues/7677)) ([a0a43a6](https://github.com/serverless/serverless/commit/a0a43a68f339f6995937a0743fe042e9e11784f9)) ([Nikody Keating](https://github.com/nkeating-mutualofenumclaw))

### Bug Fixes

- **AWS API Gateway:**
  - Fix handling of stage specific settings when nested stacks are involved ([#7735](https://github.com/serverless/serverless/issues/7735)) ([cf1692f](https://github.com/serverless/serverless/commit/cf1692f1a42c3756619869c7cdba24c660141522)) ([Mariusz Nowak](https://github.com/medikoo))
  - Improve stage settings preliminary configuration and validation ([#7735](https://github.com/serverless/serverless/issues/7735)) ([e472a04](https://github.com/serverless/serverless/commit/e472a0491a720863ab44fb81b6fada0da21507e3)) ([Mariusz Nowak](https://github.com/medikoo))
- **AWS CloudFront:** Ensure Lambda@Edge setup comes with no VPC configuration or environment variables set ([#7721](https://github.com/serverless/serverless/issues/7721)) ([a1472ba](https://github.com/serverless/serverless/commit/a1472ba6f0f10bb801de944661079174fec1a062)) ([Ahmad Mahmoud Mohammad](https://github.com/AhmedFat7y))
- **AWS IAM:** Remove IAM role from function's `DependsOn` section ([#7722](https://github.com/serverless/serverless/issues/7722)) ([d8222fa](https://github.com/serverless/serverless/commit/d8222fa0dc80ac4f6e7c23b3ccfd0d91f80b3e2e)) ([Ahmad Mahmoud Mohammad](https://github.com/AhmedFat7y))
- **CLI:** Reject multitple `--config` params ([#7728](https://github.com/serverless/serverless/issues/7728)) ([ca2a73f](https://github.com/serverless/serverless/commit/ca2a73f91a86ae41b4cf48384177c0fd74ff4f1f)) ([Ahmad Mahmoud Mohammad](https://github.com/AhmedFat7y))

### Maintenance Improvements

- Upgrade `fs-extra` to v8 ([#7719](https://github.com/serverless/serverless/issues/7719)) ([c106d53](https://github.com/serverless/serverless/commit/c106d5363830e9dc31a5714f56abfb26b0a5db37)) ([Kenan Christian Dimas](https://github.com/kenanchristian))

## [1.70.1](https://github.com/serverless/serverless/compare/v1.70.0...v1.70.1) (2020-05-11)

### Bug Fixes

- **AWS IAM:** Fix role and policy name resolution ([#7694](https://github.com/serverless/serverless/pull/7694)) ([08dc745](https://github.com/serverless/serverless/commit/08dc745cbfa403860bc7e08cbaf10cd90f15be05)) ([Mariusz Nowak](https://github.com/medikoo))
- **Standalone:** Ensure pkg bug workaround is applied on WIndows ([#7699](https://github.com/serverless/serverless/pull/7699)) ([8bc6d54](https://github.com/serverless/serverless/commit/8bc6d542f8b45aee74463ec732272dcf39c14132)) ([Mariusz Nowak](https://github.com/medikoo))

### Enhancements

- **Templates:**
  - Update aws-csharp to .NET Core 3.1 ([#7708](https://github.com/serverless/serverless/issues/7708)) ([46df82e](https://github.com/serverless/serverless/commit/46df82ea92ced3ba7542f6de5da6cfda73554ffc)) ([Joseph Woodward](https://github.com/JosephWoodward))
  - Update aws-fsharp to .NET Core 3.1 ([#7709](https://github.com/serverless/serverless/issues/7709)) ([a5a136f](https://github.com/serverless/serverless/commit/a5a136f982f19043cf4cf3236db1ac2d17c8a266)) ([Stuart Lang](https://github.com/slang25))

### Maintenance Improvements

- Replace `_.isArray` with native `Array.isArray` ([#7703](https://github.com/serverless/serverless/issues/7703)) ([3fe2e98](https://github.com/serverless/serverless/commit/3fe2e98f15d3a78571b3aa0894be1632e2f5ab51)) ([Tatsuno Yasuhiro](https://github.com/exoego))
- Upgrade `archiver` to v3 ([#7712](https://github.com/serverless/serverless/issues/7712)) ([dd9bf9](https://github.com/serverless/serverless/commit/dd9bf9a7996af5a3baf003d166ec34e1eb695b2b)) ([Frédéric Barthelet](https://github.com/fredericbarthelet))
- Upgrade `uuid` to v8 ([#7707](https://github.com/serverless/serverless/issues/7707)) ([5b4fd0](https://github.com/serverless/serverless/commit/5b4fd0fd962f84532a9dfa8469f9c76b26d78ecf)) ([Kazuki Takahashi](https://github.com/cuzkop))

## [1.70.0](https://github.com/serverless/serverless/compare/v1.69.0...v1.70.0) (2020-05-07)

### Features

- **Variables:** Support boolean and integer fallbacks ([#7632](https://github.com/serverless/serverless/issues/7632)) ([f22bffc](https://github.com/serverless/serverless/commit/f22bffc2b49e0badef8a3253478337808222964c)) ([Frédéric Barthelet](https://github.com/fredericbarthelet))
- **AWS API Gateway:** Support singular string value for CORS header ([#7668](https://github.com/serverless/serverless/pull/7668)) ([fb4ea15](https://github.com/serverless/serverless/commit/fb4ea153f0a30f18aad5b93456a1b26ed2d189ac)) ([Ahmad Mahmoud Mohammad](https://github.com/AhmedFat7y))

### Bug Fixes

- **AWS API Gateway:**
  - Ensure to update stage only for deployed API's ([#7663](https://github.com/serverless/serverless/pull/7663)) ([81953ef](https://github.com/serverless/serverless/commit/81953ef74c0c80256d8f8235df0bbb4fc8eeb1b9)) ([Mariusz Nowak](https://github.com/medikoo))
  - Fix visibility of ..-Allow-Credentials CORS header ([#7576](https://github.com/serverless/serverless/pull/7576)) ([bd9fbfb](https://github.com/serverless/serverless/commit/bd9fbfb392afc2dc95f7d83864bfdc4dc1602728)) ([Thomas Aribart](https://github.com/ThomasAribart))
- **AWS Stream:** Fix handling of configuration properties ([#7682](https://github.com/serverless/serverless/issues/7682)) ([7e1dd66](https://github.com/serverless/serverless/commit/7e1dd66f8ee72010826a7a56b7cae2479c852a60)) ([Jagdeep Singh](https://github.com/jagdeep-singh))
- **AWS Deploy** Improve logic responsible for generation of custom resource lambda archive ([#7684](https://github.com/serverless/serverless/pull/7684)) ([6b3a78](https://github.com/serverless/serverless/commit/6b3a78950c4d02049b76675a3df093891de4317a)) ([Mariusz Nowak](https://github.com/medikoo))
- **AWS EventBridge:** Ensure no duplicate event bus IAM policies ([#7644](https://github.com/serverless/serverless/issues/7644)) ([a1fde35](https://github.com/serverless/serverless/commit/a1fde35db47db76b18ddcb006e4faab22f58dc73)) ([Thomas Aribart](https://github.com/ThomasAribart))
- Fix function version param handling in `rollback function` command ([#7648](https://github.com/serverless/serverless/pull/)) ([03ad56b](https://github.com/serverless/serverless/commit/03ad56b8e189f236222431856dd43afbebdce417)) ([](https://github.com/)) ([Ahmad Mahmoud Mohammad](https://github.com/AhmedFat7y))

## [1.69.0](https://github.com/serverless/serverless/compare/v1.68.0...v1.69.0) (2020-04-29)

### Features

- **AWS HTTP API:** Support payload format version customization ([#7623](https://github.com/serverless/serverless/issues/7623)) ([4c2a52d](https://github.com/serverless/serverless/commit/4c2a52d1bf8fdb15683c09a8db800aa0e5842950)) ([Eugene Girshov](https://github.com/egirshov))
- **AWS API Gateway:** Support Open API `operationId` setting ([#7617](https://github.com/serverless/serverless/issues/7617)) ([23bbcea](https://github.com/serverless/serverless/commit/23bbcea65c3571798435aefc6d6dc9151814cab8)) ([Ryan Toussaint](https://github.com/ryantoussaint))
- **AWS SQS:** Support `maximumRetryAttempts` option ([#7620](https://github.com/serverless/serverless/issues/7620)) ([9416e72](https://github.com/serverless/serverless/commit/9416e72cba58c0a83b6bad07cdb740d36d131e96)) ([Conrad Kurth](https://github.com/ConradKurth))
- **Variables:** Support region selection on AWS SSM variables ([#7625](https://github.com/serverless/serverless/issues/7625)) ([7d3636f](https://github.com/serverless/serverless/commit/7d3636f9682c7c9929a9061f105ed232d139aa56)) ([Frédéric Barthelet](https://github.com/fredericbarthelet))

### Bug Fixes

- **AWS API Gateway:** Fix origin wildcard handling with `cors: true` ([#7482](https://github.com/serverless/serverless/issues/7482)) ([57fec3f](https://github.com/serverless/serverless/commit/57fec3f3d0429411b19f65d69cac85306b5ef950)) ([Bhuser](https://github.com/Bhuser))
- **AWS HTTP API:** Fix default log format ([#7612](https://github.com/serverless/serverless/issues/7612)) ([90ceecd](https://github.com/serverless/serverless/commit/90ceecd00d2e623f3d8a0aef13aa5a23e496d057)) ([Mariusz Nowak](https://github.com/medikoo))
- **AWS Info:** Fix calculation of resources count ([#7587](https://github.com/serverless/serverless/issues/7587)) ([946d32c](https://github.com/serverless/serverless/commit/946d32cb48dbcdc3f02a8c1521b7f5cabf1eb1f9)) ([herebebogans](https://github.com/herebebogans))
- **AWS S3:** Fix error message generation ([#7564](https://github.com/serverless/serverless/issues/7564)) ([2e56dea](https://github.com/serverless/serverless/commit/2e56dea5652540cf5d82c9d35a999c8c921fa020)) ([John Mortlock](https://github.com/jmortlock))
- **AWS Stream:** Fix configuration of boolean `Enabled` setting ([#7552](https://github.com/serverless/serverless/issues/7552)) ([10c016f](https://github.com/serverless/serverless/commit/10c016f35378e91910ee2cda3df87ddb592e95ab)) ([Clar Charron](https://github.com/clar-cmp))

## [1.68.0](https://github.com/serverless/serverless/compare/v1.67.3...v1.68.0) (2020-04-22)

### Features

- **AWS ALB:** Cognito and Oidc authentication support ([#7372](https://github.com/serverless/serverless/issues/7372)) ([8c644f1](https://github.com/serverless/serverless/commit/8c644f1b07d355544328bd008e831b40aea57af7)) ([Tatenda Chawanzwa](https://github.com/shadrech))
- **AWS Local Invocation:** Support `ruby2.7` runtime ([#7538](https://github.com/serverless/serverless/issues/7538)) ([a6b3154](https://github.com/serverless/serverless/commit/a6b3154deebdcd530afa0c716a6d7efca13de6f2)) ([Yotaro](https://github.com/yotaro-fujii))
- **Templates:** Support SSH format download template urls ([#7588](https://github.com/serverless/serverless/issues/7588)) ([d3bf39a](https://github.com/serverless/serverless/commit/d3bf39aa05f861cc8dc5115b1a7350af3b1916d9)) ([Yuga Sun](https://github.com/yugasun))

### Bug Fixes

- **AWS HTTP API:** Support API name customization ([#7434](https://github.com/serverless/serverless/issues/7434)) ([7479a9a](https://github.com/serverless/serverless/commit/7479a9ae82b44fb06de3ab84094b18e8f72affc4)) ([Eugene Girshov](https://github.com/egirshov))
- **AWS SQS:** Fix resolution of `Enabled` property ([#7532](https://github.com/serverless/serverless/issues/7532)) ([8abae84](https://github.com/serverless/serverless/commit/8abae84b8003567b6cb8affae018245a806a272b)), closes [#7438](https://github.com/serverless/serverless/issues/7438) ([Michael Wolfenden](https://github.com/michael-wolfenden))
- **Templates:** Fix Azure Functions Python template ([#7452](https://github.com/serverless/serverless/issues/7452)) ([345b9e6](https://github.com/serverless/serverless/commit/345b9e654b246ef3186a0f3fdd56901a6316af2b)) ([Tanner Barlow](https://github.com/tbarlow12))

### [1.67.3](https://github.com/serverless/serverless/compare/v1.67.2...v1.67.3) (2020-04-08)

### Bug Fixes

- **Components:** Handle gently initialization errors ([#7556](https://github.com/serverless/serverless/issues/7556)) ([7b0c18e](https://github.com/serverless/serverless/commit/7b0c18ededa149687942fb3318fefb26656e9e9d)) ([Mariusz Nowak](https://github.com/medikoo))

### [1.67.2](https://github.com/serverless/serverless/compare/v1.67.1...v1.67.2) (2020-04-08)

## [1.67.1](https://github.com/serverless/serverless/compare/v1.67.0...v1.67.1) (2020-04-07)

### Bug Fixes

- **Standalone:** Improve performance in China by supporting dedicated mirror for binary downloads ([#7521](https://github.com/serverless/serverless/issues/7521)) ([8e85fe6](https://github.com/serverless/serverless/commit/8e85fe611b4b4d619e0ad4fd347d669af6418634)) ([Mariusz Nowak](https://github.com/medikoo))
- **AWS ALB:** Fix handling of provisioned concurrency ([#7285](https://github.com/serverless/serverless/issues/7285)) ([3138ef1](https://github.com/serverless/serverless/commit/3138ef1771a31a52429777241f67dcf07a69bebd)) ([Edward Goubely](https://github.com/cbm-egoubely))
- Recognize AWS Web Identify Credentials ([#7442](https://github.com/serverless/serverless/issues/7442)) ([001f56c](https://github.com/serverless/serverless/commit/001f56cf5a4c8b4ffeb6f9e9fcc27e73d2f10789)) ([Thomas Schaaf](https://github.com/thomaschaaf))

## [1.67.0](https://github.com/serverless/serverless/compare/v1.66.0...v1.67.0) (2020-03-19)

### Features

- **AWS Websocket:** `routeResponseSelectionExpression` setting ([#7233](https://github.com/serverless/serverless/issues/7233)) ([2d25e67](https://github.com/serverless/serverless/commit/2d25e678cb1390d3cfb8899f424ff4638b239ddc)), closes [#6130](https://github.com/serverless/serverless/issues/6130) ([DougHamil](https://github.com/DougHamil))

### Bug Fixes

- **AWS Lambda:** Respect external IAM role at destinations ([#7476](https://github.com/serverless/serverless/pull/7476)) ([7a3a45f](https://github.com/serverless/serverless/commit/7a3a45f0b3f2b42a0ab68b6f638d3d97fda7cf31)), closes [#7448](https://github.com/serverless/serverless/issues/7448) ([Mariusz Nowak](https://github.com/medikoo))
- **Templates:** Fix support for `~/..` paths ([#7381](https://github.com/serverless/serverless/issues/7381)) ([962506b](https://github.com/serverless/serverless/commit/962506b4356545870e18d570756240e602b5f541)) ([Ada Ye](https://github.com/yyylksdy))
- **AWS HTTP API:** Do not validate timeout when no `httpApi` event ([#7467](https://github.com/serverless/serverless/pull/7467)) ([841aac9](https://github.com/serverless/serverless/commit/841aac941fdfc65f55b321382cfd349bd5caa209)) ([Mariusz Nowak](https://github.com/medikoo))

## [1.66.0](https://github.com/serverless/serverless/compare/v1.65.0...v1.66.0) (2020-03-09)

### Features

- **AWS Lambda:** Support configuration of destinations ([#7261](https://github.com/serverless/serverless/pull/7261)) ([8ed6a6e](https://github.com/serverless/serverless/commit/8ed6a6e7d7efc2857c68acf6e7c641f6ad8fb37c)) ([Mariusz Nowak](https://github.com/medikoo))

### Bug Fixes

- **AWS Cognito:** Fix pool update handling ([#7418](https://github.com/serverless/serverless/pull/7418)) ([0898664](https://github.com/serverless/serverless/commit/0898664c6807a6f0530281be2615d210470420fe)) ([Mariusz Nowak](https://github.com/medikoo))
- **AWS HTTP API:** Ensure function `timeout` setting is respected ([#7420](https://github.com/serverless/serverless/pull/7420)) ([b52a41d](https://github.com/serverless/serverless/commit/b52a41d9ee08efc875815b239c7d25d32b3be92f)) ([Mariusz Nowak](https://github.com/medikoo))
- **AWS Websocket:** Fix AWS partition support ([#7430](https://github.com/serverless/serverless/issues/7430)) ([9b627fb](https://github.com/serverless/serverless/commit/9b627fbf7e69d123f60e31c27289788fed7115ae)) ([Austin J. Alexander](https://github.com/austinjalexander))
- **AWS S3:** Add source account to lambda permissions for S3 events ([#7417](https://github.com/serverless/serverless/issues/7417)) ([7d67f33](https://github.com/serverless/serverless/commit/7d67f33b085c29ce0e57431629e33e657b93c474)) ([Callum Smits](https://github.com/callumsmits))
- **Variables:** Relax pattern to allow non-ascii defaults ([#7431](https://github.com/serverless/serverless/issues/7431)) ([7310782](https://github.com/serverless/serverless/commit/73107822945a878abbdebe2309e8e9d87cc2858a)) ([Arben Bakiu](https://github.com/arbbakbenny))
- **Standalone:** Fix logic responsible for notifications about new versions ([#7412](https://github.com/serverless/serverless/pull/7412)) ([1565d03](https://github.com/serverless/serverless/commit/1565d038313b7939d6c9d9fdf8bfb4f95fd7027e)) ([AJ Stuyvenberg](https://github.com/astuyve))

## [1.65.0](https://github.com/serverless/serverless/compare/v1.64.1...v1.65.0) (2020-02-28)

### Features

- **AWS HTTP API:**
  - Support access logs configuration ([#7385](https://github.com/serverless/serverless/pull/7385)) ([f2cb89a](https://github.com/serverless/serverless/commit/f2cb89a3cadc34235ccd62c35beb165942fb60d6)) ([Mariusz Nowak](https://github.com/medikoo))
  - Support attachment to externally created API ([#7396](https://github.com/serverless/serverless/pull/7396)) ([f47b340](https://github.com/serverless/serverless/commit/f47b340e4fbe5163595225d450e857ae36211d98)) ([Mariusz Nowak](https://github.com/medikoo))
  - Support `timeout` configuration ([#7401](https://github.com/serverless/serverless/pull/7401)) ([df9846d](https://github.com/serverless/serverless/commit/df9846d9afa56bb7d5d8bc07b6a58c2f58eaf59e)) ([Mariusz Nowak](https://github.com/medikoo))
- **Components:** Support Cloud Components ([#7390](https://github.com/serverless/serverless/issues/7390)) ([0ed52f6](https://github.com/serverless/serverless/commit/0ed52f61de98101fd570bc6e7794a74ab7afa0ff)) ([Eslam Hefnawy](https://github.com/eahefnawy))
- **AWS API Gateway:** Support association of VPC endpoint ids ([#7382](https://github.com/serverless/serverless/issues/7382)) ([19012a9](https://github.com/serverless/serverless/commit/19012a9068357f307693823bc56bb2ce1d881a64)) ([Alexandre Tremblay](https://github.com/altrem))
- **AWS CloudFormation:** Support `resource.extensions` for safe resource extensions ([#7352](https://github.com/serverless/serverless/issues/7352)) ([08ec261](https://github.com/serverless/serverless/commit/08ec261a3cd34e7225f471cbeab8cef605ac61fc)) ([Geoff Baskwill](https://github.com/glb))

### Bug Fixes

- **AWS Local Invocation:**
  - Ensure AWS creds resolution for local docker invocation ([#7375](https://github.com/serverless/serverless/issues/7375)) ([90b3a8f](https://github.com/serverless/serverless/commit/90b3a8f81eea8fb27c24b2b05888e7f386ee47bd)) ([frozenbonito](https://github.com/frozenbonito))
  - Ensure AWS env vars in local invocation made with docker ([#7349](https://github.com/serverless/serverless/issues/7349)) ([c09f718](https://github.com/serverless/serverless/commit/c09f71897a67fe8ec98d460075f0f02b397f8ee5)) ([frozenbonito](https://github.com/frozenbonito))
  - Fix handler resolution (multi `.` case) for local invocation ([#7398](https://github.com/serverless/serverless/issues/7398)) ([d84e9e7](https://github.com/serverless/serverless/commit/d84e9e7d1e440b5bfaae39b4cfefd83f8ac2e8b9)) ([Arben Bakiu](https://github.com/arbbakbenny))
- **Standalone:** Ensure to bundle local invocation non Node.js artifcats ([#7409](https://github.com/serverless/serverless/pull/7409)) ([506ad86](https://github.com/serverless/serverless/commit/506ad863da1ceb78d2d8a0573dbc03c0db56f098)) ([Mariusz Nowak](https://github.com/medikoo))
- **AWS EventBridge:** Ensure AWS EventBrigde target ids fit 64 chars limit ([#7359](https://github.com/serverless/serverless/issues/7359)) ([103fdac](https://github.com/serverless/serverless/commit/103fdacc294ab87f4bd079847d05d9448fd4b494)) ([Frédéric Barthelet](https://github.com/fredericbarthelet))
- **AWS IAM:** Ensure consistency in role and policy names ([#7357](https://github.com/serverless/serverless/issues/7357)) ([9a0aaa8](https://github.com/serverless/serverless/commit/9a0aaa843b19cb5bc0ddfe9a25b96e3c64d82749)) ([Thomas Schaaf](https://github.com/thomaschaaf))
- **AWS SNS:** Fix handling of `redrivePolicy` ([#7277](https://github.com/serverless/serverless/issues/7277)) ([292b1ca](https://github.com/serverless/serverless/commit/292b1caf58583a7935673e22fc7f505b9f9871bc)) ([tcastelli](https://github.com/tcastelli))

### [1.64.1](https://github.com/serverless/serverless/compare/v1.64.0...v1.64.1) (2020-02-26)

### Bug Fixes

- **AWS HTTP API:** Configure default stage explicity ([#7383](https://github.com/serverless/serverless/issues/7383)) ([3d79a7a](https://github.com/serverless/serverless/commit/3d79a7a169fdc2c43c86d6b509f9151af32665dc)) ([Mariusz Nowak](https://github.com/medikoo))
- Follow symlinks when writing a config ([#7374](https://github.com/serverless/serverless/issues/7374)) ([3e1e1f4](https://github.com/serverless/serverless/commit/3e1e1f486c4f6e283e172c99d9a38838bfbe2ab6)) ([Neil Locketz](https://github.com/c0d3d))
- Service state path resolution ([#7388](https://github.com/serverless/serverless/issues/7388)) ([5017f03](https://github.com/serverless/serverless/commit/5017f038d6a8f35fc25ec7a239358a30ca15b745)) ([Arben Bakiu](https://github.com/arbbakbenny))
- When packaging do not crash on deps with no package.json ([#7368](https://github.com/serverless/serverless/issues/7368)) ([8518000](https://github.com/serverless/serverless/commit/8518000d4fbf3a6cf0a6e2f81bd6421e017a1b5f)) ([darko1979](https://github.com/darko1979))

## [1.64.0](https://github.com/serverless/serverless/compare/v1.63.0...v1.64.0) (2020-02-18)

### Features

- **AWS HTTP API:**
  - Support CORS configuration ([#7336](https://github.com/serverless/serverless/issues/7336)) ([ca69387](https://github.com/serverless/serverless/commit/ca693872855a59799ec22079d20d048b40ab33a1)) ([Mariusz Nowak](https://github.com/medikoo))
  - Support JWT authorizers ([#7346](https://github.com/serverless/serverless/issues/7346)) ([fbf99fa](https://github.com/serverless/serverless/commit/fbf99fa2abf9ce3bc13fc4a6c8439a650d3eaa4e)) ([Mariusz Nowak](https://github.com/medikoo))
- **AWS API Gateway:**
  - Support `provider.logs.restApi.roleManagedExternally` ([#7333](https://github.com/serverless/serverless/issues/7333)) ([9b701a4](https://github.com/serverless/serverless/commit/9b701a405627273fb54e411eb4e87bc085282c6b)) ([coyoteecd](https://github.com/coyoteecd))  
    (so CloudWatch IAM role access can be handled externally)
  - Support `authorizer.managedExternally` option for `http` event authorizers ([#7327](https://github.com/serverless/serverless/issues/7327)) ([7abb23e](https://github.com/serverless/serverless/commit/7abb23edc8dfbe5005ac716aa137330741759929)) ([Geoff Baskwill](https://github.com/glb))  
    (so permissions for lambda authorizers are handled externally)
- **AWS IAM:** Support `provider.rolePermissionsBoundary` to set IAM boundary ([#7319](https://github.com/serverless/serverless/issues/7319)) ([09466b5](https://github.com/serverless/serverless/commit/09466b5a172a743b1c2d5c1045c08f5c2ad32a2e)) ([Thomas Schaaf](https://github.com/thomaschaaf))
- **AWS ALB:** Support `provider.alb.targetGroupPrefix` setting ([#7322](https://github.com/serverless/serverless/issues/7322)) ([3910df1](https://github.com/serverless/serverless/commit/3910df1ba6a8b39367ce8d51adb90216251be2ba)) ([isen-ng](https://github.com/isen-ng) & [jinhong-](https://github.com/jinhong-))  
  (so ALB target groups are prefixed with common strings, and can be easily referenced externally)
- **AWS Kinesis:** Support Enhanced Fan-out (Consumer) streams ([#7320](https://github.com/serverless/serverless/issues/7320)) ([9eba218](https://github.com/serverless/serverless/commit/9eba2187f9565b39d31e88572c06ea2ccaa4bade)) ([Zac Charles](https://github.com/zaccharles))
- **AWS Local invocation:** Improve performance of invocations in Docker containers ([#7178](https://github.com/serverless/serverless/issues/7178)) ([f6d9bfd](https://github.com/serverless/serverless/commit/f6d9bfd6c6bb5cd49ee67ce20e35e78090c18ab3)) ([Richard Davison](https://github.com/richarddd))
- **AWS Deploy:**
  - Support `deploymentBucket.maxPreviousDeploymentArtifacts` customization ([#7283](https://github.com/serverless/serverless/issues/7283)) ([0241468](https://github.com/serverless/serverless/commit/024146885a913f545ebf8b0f5f6734b7650c64cc)) ([Edmundo Santos](https://github.com/rdsedmundo))
  - Support tweaking max concurrent artifact uploads count ([#7295](https://github.com/serverless/serverless/issues/7295)) ([0592a27](https://github.com/serverless/serverless/commit/0592a27dbc084eb9b96791f24c1ef636395e42dc)) ([Edmundo Santos](https://github.com/rdsedmundo))

### Bug Fixes

- **AWS HTTP API:** (design fix) Instead of creating AWS stage, publish to default stage in all cases ([#7331](https://github.com/serverless/serverless/issues/7331)) ([44c2342](https://github.com/serverless/serverless/commit/44c2342aeba76bd98c097a78be1d762eeccbbfd3)) ([Mariusz Nowak](https://github.com/medikoo))
- **AWS API Gateway:** Limit permission scope of authorizers ([#7300](https://github.com/serverless/serverless/issues/7300)) ([c05dcb3](https://github.com/serverless/serverless/commit/c05dcb3432c16fe5cf25bc3c796f9feb92e5421a)) ([Philipp Muens](https://github.com/pmuens))
- **AWS Websocket:** Fix route names normalization ([#7294](https://github.com/serverless/serverless/issues/7294)) ([33291c8](https://github.com/serverless/serverless/commit/33291c8d08c8edd82e807b8fbe3f1796bcfdb4ac)) ([tom-marsh](https://github.com/tom-marsh))

## [1.63.0](https://github.com/serverless/serverless/compare/v1.62.0...v1.63.0) (2020-02-05)

### Features

- **AWS HTTP API:** Initial basic routes configuration support ([69170d0](https://github.com/serverless/serverless/commit/69170d09a8595605cce9c9c8cafe0d676ea87746))
- Support `destinations` config on stream events ([#7262](https://github.com/serverless/serverless/issues/7262)) ([ea4ac26](https://github.com/serverless/serverless/commit/ea4ac262ea4b9efdebc1fc357ffe906900295823))
- Support rich and reusable S3 buckets configuration ([#7156](https://github.com/serverless/serverless/issues/7156)) ([382c0bf](https://github.com/serverless/serverless/commit/382c0bfc21b98fdadb8ad86340a97f6cc18ce84d))

### Bug Fixes

- Fix `sls logs` so it also covers output from aliases ([#7270](https://github.com/serverless/serverless/issues/7270)) ([4468805](https://github.com/serverless/serverless/commit/4468805d2a93224b63d99dc04f6c6056226af689)), closes [#7214](https://github.com/serverless/serverless/issues/7214)
- **Standalone:** Ensure to use proper CLI params parser ([f426ed7](https://github.com/serverless/serverless/commit/f426ed7077c67eac9785452b312ca1e179c201bf))

### [1.62.0](https://github.com/serverless/serverless/compare/v1.61.3...v1.62.0) (2020-01-29)

### Features

- Support `redrivePolicy` configuration on SNS events ([#7239](https://github.com/serverless/serverless/issues/7239)) ([4f27378](https://github.com/serverless/serverless/commit/4f273785f4b7cceaffd2fb6b9255e4187962d53c))
- Ensure deterministic WebSockets deployment id (so deployments are skipped when no changes are detected) ([#7248](https://github.com/serverless/serverless/issues/7248)) ([9f0131f](https://github.com/serverless/serverless/commit/9f0131fedf60e9104f38702d01e103b9a3b0f629))
- `azure-nodejs-typescript` template ([#7252](https://github.com/serverless/serverless/issues/7252)) ([0549d85](https://github.com/serverless/serverless/commit/0549d85bc0254a10d3314613892e335da2bc3722))

### Bug Fixes

- **Variables:** When resolving SSM parameter, ensure to retrieve status code from AWS error correctly ([bc5bbbe](https://github.com/serverless/serverless/commit/bc5bbbed3c050eb69262b3f9b6fbd53c563c9fb2)), closes [#7237](https://github.com/serverless/serverless/issues/7237)
- Do not overwrite `go.mod` on `make` in Go template ([#7245](https://github.com/serverless/serverless/issues/7245)) ([1793cf8](https://github.com/serverless/serverless/commit/1793cf8d7a55b85fc6505ae493dcca2292e443d2))

### [1.61.3](https://github.com/serverless/serverless/compare/v1.61.2...v1.61.3) (2020-01-21)

### Improvements

- Support `code` parameter on `ServerlessError` ([f6c5179](https://github.com/serverless/serverless/commit/f6c51796f886573679d3500b2007a314c8e4bd4d))

### [1.61.2](https://github.com/serverless/serverless/compare/v1.61.1...v1.61.2) (2020-01-15)

### Bug Fixes

- Separate AWS region and credentials resolution concern ([91525e8](https://github.com/serverless/serverless/commit/91525e889f08eefe0451df65e1207d53978030ef)). Fixes [serverless/enterprise-plugin#340](https://github.com/serverless/enterprise-plugin/issues/340)

### [1.61.1](https://github.com/serverless/serverless/compare/v1.61.0...v1.61.1) (2020-01-14)

### Bug Fixes

- **AWS APIGW:** Fix default resource policy configuration ([8814671](https://github.com/serverless/serverless/commit/8814671435a2b78ec281e527227e1b4a0fbbe093))
  Fixes regression introduced with [#7138](https://github.com/serverless/serverless/issues/7138)
  Closes [#7194](https://github.com/serverless/serverless/issues/7194) and [#7211](https://github.com/serverless/serverless/issues/7211)

## [1.61.0](https://github.com/serverless/serverless/compare/v1.60.5...v1.61.0) (2020-01-13)

### Features

- **Standalone:** Windows Chocolatey PM integration ([85b196f](https://github.com/serverless/serverless/commit/85b196ff4dd9fb64594bc1b362f882ee350dd01e))
- Add support for plain .git template URLs ([3cfa750](https://github.com/serverless/serverless/commit/3cfa7502e233819d060140b356483d9fd8799800))
- Enhance configuration options of cloudFront event ([#7170](https://github.com/serverless/serverless/issues/7170)) ([9591d5a](https://github.com/serverless/serverless/commit/9591d5a232c641155613d23b0f88ca05ea51b436)), closes [#7151](https://github.com/serverless/serverless/issues/7151), addresses [#6843](https://github.com/serverless/serverless/issues/6843) [#6785](https://github.com/serverless/serverless/issues/6785)
- Support `BisectBatchOnFunctionError` option on event streams ([#7105](https://github.com/serverless/serverless/issues/7105)) ([560ceee](https://github.com/serverless/serverless/commit/560ceee5b3abf90999c61074b8a94d5ef31e967b))
- support `RollbackConfiguration` in service config ([#7193](https://github.com/serverless/serverless/issues/7193)) ([5973c9f](https://github.com/serverless/serverless/commit/5973c9fd58631beaea45047345cac8d348e93911))

### Bug Fixes

- Fix CLI params resolution (switch to `yargs-parser`) ([#7187](https://github.com/serverless/serverless/issues/7187)) ([780fb46](https://github.com/serverless/serverless/commit/780fb46e726faf147ba16d190307bf1948ee53b3)), closes [#6083](https://github.com/serverless/serverless/issues/6083)
- **AWS Lambda:** Do not break permission resource ([5e63cee](https://github.com/serverless/serverless/commit/5e63cee340591af5aaa65828a6907fca445d76e4)), closes [#7189](https://github.com/serverless/serverless/issues/7189)
- Ensure CF stacks are deleted on failed creation attempt ([#7158](https://github.com/serverless/serverless/issues/7158)) ([53a18cb](https://github.com/serverless/serverless/commit/53a18cbff6d3d2d6698e98cf0dd8a7eba21fdf58)), closes [#6612](https://github.com/serverless/serverless/issues/6612)
- Fix and improve openwhisk-java-maven templates ([#7164](https://github.com/serverless/serverless/issues/7164)) ([41d7d0b](https://github.com/serverless/serverless/commit/41d7d0bf0798188284f38e0f4e3effadad1f8d42))
- Remove hard-coded AWS partitions ([#7175](https://github.com/serverless/serverless/issues/7175)) ([3236adb](https://github.com/serverless/serverless/commit/3236adb040f186cd606e5656cf85a05bd183e822))

### [1.60.5](https://github.com/serverless/serverless/compare/v1.60.4...v1.60.5) (2020-01-03)

### Bug Fixes

- **Standalone**
  - Ensure dashboard plugin policies are bundled ([4b5f531](https://github.com/serverless/serverless/commit/4b5f531d9ec293f1f228d572cd265361530135f7))
  - Ensure dashboard wrapper is bundled ([994555d](https://github.com/serverless/serverless/commit/994555d7d6eb7bf960adceed4a59a4f667a9d92d))
  - Workaround `pkg` [#420](https://github.com/zeit/pkg/issues/420) bug ([c94a614](https://github.com/serverless/serverless/commit/c94a6146762a2d50c9d746e70a699ffc9cffd9c8))
- **AWS Lambda:** Fix provisioned concurrency setup issues (remove no longer needed AWS issue workaround) ([4821ad2](https://github.com/serverless/serverless/commit/4821ad21a5da5622a5686a7dc6eafdcd90ffe538)), closes [#7137](https://github.com/serverless/serverless/issues/7137)
- **CLI**
  - Fix ambiguity of `-v` option ([074647c](https://github.com/serverless/serverless/commit/074647c50244b11573e5ece1cfd7429da0a9bf2f))
  - Recognize CLI aliases as documented ([7a804e1](https://github.com/serverless/serverless/commit/7a804e1c06b0991e2f9371b3bb794c660e2514d4)), closes [#7106](https://github.com/serverless/serverless/issues/7106)
- **Plugins:** Fix resolution of config when installing plugin ([b5dbdaf](https://github.com/serverless/serverless/commit/b5dbdafe5b4b03608ebb10d024fb6587e1ea7a40)), closes [#7130](https://github.com/serverless/serverless/issues/7130)
- **AWS APIGW:** Fix handling of removal of `resourcePolicy` setting ([e662a91](https://github.com/serverless/serverless/commit/e662a91d92651111c86b6e72eed57075be95decb)), closes [#6789](https://github.com/serverless/serverless/issues/6789)
- **Variables:** Ensure no same object instances are shared across config ([4893f7d](https://github.com/serverless/serverless/commit/4893f7d0c2168d3aa39b04ac040cd1797ed31431)), closes [#7098](https://github.com/serverless/serverless/issues/7098)

### [1.60.4](https://github.com/serverless/serverless/compare/v1.60.3...v1.60.4) (2019-12-23)

### Bug Fixes

- **AWS APIGW:** Fix handling of provisionedConcurrency: 0 setting ([efe6d02](https://github.com/serverless/serverless/commit/efe6d02e1ad9fa760a97f2c24d427e9791bcfd45)), closes [#7133](https://github.com/serverless/serverless/issues/7133)

### [1.60.3](https://github.com/serverless/serverless/compare/v1.60.2...v1.60.3) (2019-12-23)

### Bug Fixes

- **AWS APIGW:** Fix Rest API id detection when no API GW involved ([81096ca](https://github.com/serverless/serverless/commit/81096caf3d8e98932cd4314495a4fc107fab297a)), regression introduced with [#7126](https://github.com/serverless/serverless/issues/7126)

### [1.60.2](https://github.com/serverless/serverless/compare/v1.60.1...v1.60.2) (2019-12-23)

### Bug Fixes

- **AWS Lambda**
  - **Fix provisioned concurrency setup (closes [#7059](https://github.com/serverless/serverless/issues/7059)):**
    - Fix provisioned concurrency configuration. Configure on alias, and not on version. Thanks to that it can work with versioning enabled and changes to provisioned concurrency configuration are not immune to `Internal Failure` ([04a7657](https://github.com/serverless/serverless/commit/04a765715f3bb2cd5a41a9273b0623c2fe900691))
    - Workaround AWS issue related to alias redeployments ([56b9d3d](https://github.com/serverless/serverless/commit/56b9d3d41213f0fc90a48af1bcaf92233854acbb))
    - Ensure API Gateway endpoints point provisioned version ([67d27ed](https://github.com/serverless/serverless/commit/67d27edbfe420e5133d2acf970979bdfaa1d5905)),
  - Fix CloudWatch logs creation access ([a2db989](https://github.com/serverless/serverless/commit/a2db9895398d90c42a613d0b1328f1b124aada0c)), closes [#6241](https://github.com/serverless/serverless/issues/6241) [#6692](https://github.com/serverless/serverless/issues/6692)
- **AWS API Gateway:**
  - Ensure to apply API GW stage settings in case of services having no endpoints configured ([e93e6f4](https://github.com/serverless/serverless/commit/e93e6f4028971b210310dc60dff04bf33ca1d3b9)), closes [#7036](https://github.com/serverless/serverless/issues/7036)
- Fix custom resource lambda artifact generation ([7132af3](https://github.com/serverless/serverless/commit/7132af3217b6b46b5098bf6f2a96c50e27b588ef))

### [1.60.1](https://github.com/serverless/serverless/compare/v1.60.0...v1.60.1) (2019-12-20)

### Bug Fixes

- Ensure necessary IAM role for handling existing cognito pools ([5c6de5c](https://github.com/serverless/serverless/commit/5c6de5c3ace69c1c5b91f1e1698d6e65f7a0e9af)), closes [#6579](https://github.com/serverless/serverless/issues/6579)
- Fix support for relative plugins.localPath ([10ba8cb](https://github.com/serverless/serverless/commit/10ba8cbc46b751a63a7a604140ab28549d491b5c)), closes [#7117](https://github.com/serverless/serverless/issues/7117)
- Support different AWS partitions ([f353144](https://github.com/serverless/serverless/commit/f3531445f82276ba0bc14044452b64d240df47e9))

## [1.60.0](https://github.com/serverless/serverless/compare/v1.59.3...v1.60.0) (2019-12-18)

### Features

- **Binary installer**
  - `uninstall` command for installed binaries ([53e596f](https://github.com/serverless/serverless/commit/53e596fa6708aa1c3a4359c5679a898cfbd406ec))
  - `upgrade` command for installed binaries ([c4efd66](https://github.com/serverless/serverless/commit/c4efd66e4e9a808d8c79511af6cca7bc653bdec4))
  - Configure binaries generation ([49f6e1e](https://github.com/serverless/serverless/commit/49f6e1e8a57929862c79b6fea90c7515469bca7c))
  - Linux & macOS binary installer ([f0f9698](https://github.com/serverless/serverless/commit/f0f96980ee94727177f9306ab5bf31ac8e7e209b))
  - Recognise as standalone ([59bea09](https://github.com/serverless/serverless/commit/59bea09dad12bd8484042e773e5a1c716aaec4a7))
  - Script to upload generated binaries to GitHub release ([5563b28](https://github.com/serverless/serverless/commit/5563b284f265e20db5058922e65e08425e978efc))
- Draw CLI boxes with `boxen` package ([80f9a65](https://github.com/serverless/serverless/commit/80f9a6570fc139da1da7b0e53778d7fdc1ff507b))
- MaximumRetryAttempts config for stream ([998b6fd](https://github.com/serverless/serverless/commit/998b6fd296f54d5a05f1609b29cc09fbc541935f)), closes [#7012](https://github.com/serverless/serverless/issues/7012)
- Memoize resolution of dev deps exclusion paths ([#7091](https://github.com/serverless/serverless/issues/7091)) ([5143c2a](https://github.com/serverless/serverless/commit/5143c2ad3af84e198fb256b8cebf585aac3886e6))
- Support CF instructions in awsKmsKeyArn setting ([#7083](https://github.com/serverless/serverless/issues/7083)) ([f9b6507](https://github.com/serverless/serverless/commit/f9b650782539808e796c1544a9dc7f2d02603db1))
- Unconditionally display browser url ([c900900](https://github.com/serverless/serverless/commit/c90090048847c4280081a7b7fb1a8c3171cc7771))
- Update and improve aws-kotlin-jvm-gradle template ([#7072](https://github.com/serverless/serverless/issues/7072)) ([0b3a08a](https://github.com/serverless/serverless/commit/0b3a08afaaf520fe6c3d4ebaac1a12fbd83c1fe4))

### Bug Fixes

- Ensure not to autocomplete hidden commands ([3f7f532](https://github.com/serverless/serverless/commit/3f7f532b88c9bdcc25a2b53a93e11484131c28ab))
- Fix AWS partition reference in APIGW CloudWatch role setup ([fc74c28](https://github.com/serverless/serverless/commit/fc74c287f68deb20266d011d9376d13117c11161)), closes [#7100](https://github.com/serverless/serverless/issues/7100)
- Fix credentials validation in EC2 environment ([#6977](https://github.com/serverless/serverless/issues/6977)) ([f8ee027](https://github.com/serverless/serverless/commit/f8ee0279037ba35b4c32f5872fcff4e741898db1))
- Prevent uncaught exception in case of `open` util issue ([f29d169](https://github.com/serverless/serverless/commit/f29d1697dd89a418ca4aacac23b64b928e68f643))
- Recognize falsy values as CLI options defaults ([#7071](https://github.com/serverless/serverless/issues/7071)) ([7e0e903](https://github.com/serverless/serverless/commit/7e0e903c798cc6c5370a74048202cd0480e2be3d))

### [1.59.3](https://github.com/serverless/serverless/compare/v1.59.2...v1.59.3) (2019-12-09)

### Bug Fixes

- Do not set optional ParallelizationFactor when not explicitly set ([e74d1a0](https://github.com/serverless/serverless/commit/e74d1a0a6486fba1ca09c5eb54b36fcf552d60f4)), closes [#7049](https://github.com/serverless/serverless/issues/7049)
- Fix provisioned concurrency support ([be0ebb7](https://github.com/serverless/serverless/commit/be0ebb76e7d3860587a986c9da48209870e7990d)), closes [#7059](https://github.com/serverless/serverless/issues/7059)

### [1.59.2](https://github.com/serverless/serverless/compare/v1.59.1...v1.59.2) (2019-12-06)

### Bug Fixes

- Ensure to not create cognito pools marked as 'existing' ([fe546c5](https://github.com/serverless/serverless/commit/fe546c50d35b88b24556257182aacd9e24f07d1b))

### [1.59.1](https://github.com/serverless/serverless/compare/v1.59.0...v1.59.1) (2019-12-05)

### Bug Fixes

- Fix mishandling of cachedCredentials in invokeLocal ([699e78d](https://github.com/serverless/serverless/commit/699e78d251b7cbb3e6553c6d8554c2bf568be1fb)), closes [#7050](https://github.com/serverless/serverless/issues/7050), regression introduced with [#7044](https://github.com/serverless/serverless/issues/7044)

# 1.59.0 (2019-12-04)

- [Fix spelling and typos in docs, code variables and code comments](https://github.com/serverless/serverless/pull/6986)
- [Code cleanup and refactoring](https://github.com/serverless/serverless/pull/6990)
- [Add support for contentHandling - Fixes gh-6949](https://github.com/serverless/serverless/pull/6987)
- [Fix deployment bucket SSE documentation](https://github.com/serverless/serverless/pull/7000)
- [Make authorizer type check from #6150 case insensitive](https://github.com/serverless/serverless/pull/7001)
- [Govcloud custom resource fix](https://github.com/serverless/serverless/pull/6996)
- [Lint and style patches](https://github.com/serverless/serverless/pull/7004)
- [Fix/cors omit access control allow credentials on false](https://github.com/serverless/serverless/pull/6999)
- [Fix: remove `$context.status` from websocket access log format](https://github.com/serverless/serverless/pull/7014)
- [Clarifying Azure setup](https://github.com/serverless/serverless/pull/7015)
- [Expose ParallelizationFactor prop for Kinesis Streams](https://github.com/serverless/serverless/pull/7024)
- [Replace moment with dayjs](https://github.com/serverless/serverless/pull/7025)
- [Update AWS SQS event docs regarding FIFO queue trigger for Lambda](https://github.com/serverless/serverless/pull/7029)
- [Awsprovider - adding support for SDK sub-classes.](https://github.com/serverless/serverless/pull/7031)
- [Provide backoff for retryable aws requests and the option to adjust the cf status check interval via an environment variable](https://github.com/serverless/serverless/pull/6981)
- [Add page for best practices on CI/CD](https://github.com/serverless/serverless/pull/6988)
- [Optimize custom resources generation](https://github.com/serverless/serverless/pull/7032)
- [Update API GW stage settings only when explicitly set](https://github.com/serverless/serverless/pull/7033)
- [Do not apply APIGW wide settings on externally referenced APIGW](https://github.com/serverless/serverless/pull/7034)
- [Enable Content Trust checking when pulling lambci/lambda images](https://github.com/serverless/serverless/pull/6992)
- [Fix resolution of user configured APIGW](https://github.com/serverless/serverless/pull/7039)
- [Add option to change log level for websocket logs](https://github.com/serverless/serverless/pull/7035)
- [Support lambda provisioned concurrency](https://github.com/serverless/serverless/pull/7043)
- [Fix AWS creds handling](https://github.com/serverless/serverless/pull/7044)
- [Fix lambda provisioned concurrency setup](https://github.com/serverless/serverless/pull/7045)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.58.0...v1.59.0)

# 1.58.0 (2019-11-20)

- [Fix missing ALB trigger in console](https://github.com/serverless/serverless/pull/6926)
- [Add support for vpc link integration discussed as part of #5025](https://github.com/serverless/serverless/pull/6051)
- [Setup Codecov](https://github.com/serverless/serverless/pull/6924)
- [Fix handling of China region in S3 bucket policy](https://github.com/serverless/serverless/pull/6934)
- [Fix policy definition](https://github.com/serverless/serverless/pull/6937)
- [Fix typo in Tencent docs](https://github.com/serverless/serverless/pull/6935)
- [Add Knative provider template](https://github.com/serverless/serverless/pull/6936)
- [Add Knative documentation](https://github.com/serverless/serverless/pull/6930)
- [PLAT-1798 - set env vars for AWS creds from cached credentials…](https://github.com/serverless/serverless/pull/6938)
- [Add azure python to cli](https://github.com/serverless/serverless/pull/6945)
- [updated providers menu order in docs](https://github.com/serverless/serverless/pull/6955)
- [Update API Gateway tagging to use partition for deployed region](https://github.com/serverless/serverless/pull/6948)
- [Fix: use normalized maps in zipService.js](https://github.com/serverless/serverless/pull/6705)
- [Add support for multi-value headers in ALB events](https://github.com/serverless/serverless/pull/6940)
- [Improve config error handling](https://github.com/serverless/serverless/pull/6962)
- [sls-flask starter kit](https://github.com/serverless/serverless/pull/6967)
- [Add variable completion report if variable progress was reported](https://github.com/serverless/serverless/pull/6966)
- [Update docs links](https://github.com/serverless/serverless/pull/6975)
- [Update documentation to include information about tags](https://github.com/serverless/serverless/pull/6982)
- [Python3.8 support!](https://github.com/serverless/serverless/pull/6978)
- [Updates to CI/CD settings for the beta](https://github.com/serverless/serverless/pull/6972)
- [rename output variables to outputs](https://github.com/serverless/serverless/pull/6971)
- [Fix Tencent Template and Readme](https://github.com/serverless/serverless/pull/6984)
- [Default to Nodejs12.x runtime](https://github.com/serverless/serverless/pull/6983)
- [#6162: Support multiple schemas, don't overwrite RequestModels for each](https://github.com/serverless/serverless/pull/6954)
- [Support empty deploymentPrefix](https://github.com/serverless/serverless/pull/6941)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.57.0...v1.58.0)

# 1.57.0 (2019-11-06)

- [Note about how to move services to new apps](https://github.com/serverless/serverless/pull/6912)
- [Allow casting to boolean in Serverless variables](https://github.com/serverless/serverless/pull/6869)
- [Create distinct target groups for different ALBs](https://github.com/serverless/serverless/pull/6383)
- [sls create --help improvements](https://github.com/serverless/serverless/pull/6919)
- [Fix race conditions handling in stats requests](https://github.com/serverless/serverless/pull/6920)
- [Update AWS Limits on Lambda@Edge](https://github.com/serverless/serverless/pull/6922)
- [Fixes bug with sns-cross-region definition using psuedo params](https://github.com/serverless/serverless/pull/6879)
- [Add tencent-plugins english version docs](https://github.com/serverless/serverless/pull/6916)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.56.1...v1.57.0)

# 1.56.1 (2019-10-31)

- [Fix deployment bucket policy handling with custom bucket ](https://github.com/serverless/serverless/pull/6909)
- [Feat: aws-nodejs-typescript template improvements](https://github.com/serverless/serverless/pull/6904)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.56.0...v1.56.1)

# 1.56.0 (2019-10-31)

- [AWS - deployment bucket policy for HTTPS only](https://github.com/serverless/serverless/pull/6823)
- [Docs on renamed outputs and expanded support](https://github.com/serverless/serverless/pull/6870)
- [Fix minor typo](https://github.com/serverless/serverless/pull/6877)
- [Added mock integration documentation example](https://github.com/serverless/serverless/pull/6883)
- [Fix region error handling in Lambda@Edge implementation](https://github.com/serverless/serverless/pull/6886)
- [Allow specifying ApiGateway logs role ARN](https://github.com/serverless/serverless/pull/6747)
- [Adds unused memory alert](https://github.com/serverless/serverless/pull/6889)
- [Find origin by domain name and path](https://github.com/serverless/serverless/pull/6880)
- [fix minor typo in kubeless docs](https://github.com/serverless/serverless/pull/6896)
- [Add tencent provider create-template](https://github.com/serverless/serverless/pull/6898)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.55.1...v1.56.0)

# 1.55.1 (2019-10-23)

- [Allow plugins to customize what flags are supported during interactive cli](https://github.com/serverless/serverless/pull/6697)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.55.0...v1.55.1)

# 1.55.0 (2019-10-23)

- [Allow empty arrays in overrides](https://github.com/serverless/serverless/pull/6813)
- [Make question mark available as variables fallback](https://github.com/serverless/serverless/pull/6808)
- [Improve plugins resolution and initialization flow](https://github.com/serverless/serverless/pull/6814)
- [Azure Python template](https://github.com/serverless/serverless/pull/6822)
- [Chore - stop using deprecated 'new Buffer()' method.](https://github.com/serverless/serverless/pull/6829)
- [AWS - adding naming function for S3 compiled template file name.](https://github.com/serverless/serverless/pull/6828)
- [Span docs! and full `serverless_sdk` docs](https://github.com/serverless/serverless/pull/6809)
- [Fix perms with several CloudWatch log subscriptions](https://github.com/serverless/serverless/pull/6827)
- [Fixing an Azure docs broken link](https://github.com/serverless/serverless/pull/6838)
- [Adding note to Azure nodejs template](https://github.com/serverless/serverless/pull/6839)
- [Updated Azure Functions documentation](https://github.com/serverless/serverless/pull/6840)
- [Support for NotAction and NotResource in IAM role statements](https://github.com/serverless/serverless/pull/6842)
- [added frontmatter to sdk docs](https://github.com/serverless/serverless/pull/6845)
- [Setup <tab> completion via CLI command and interactive CLI step](https://github.com/serverless/serverless/pull/6835)
- [Upgrade gradle version](https://github.com/serverless/serverless/pull/6855)
- [Update Google provider documentation for functions](https://github.com/serverless/serverless/pull/6854)
- [SNS integration tests](https://github.com/serverless/serverless/pull/6846)
- [SQS integration tests](https://github.com/serverless/serverless/pull/6847)
- [Streams integration tests](https://github.com/serverless/serverless/pull/6848)
- [Improvements on SQS docs as suggested on #6516](https://github.com/serverless/serverless/pull/6853)
- [Schedule integration tests](https://github.com/serverless/serverless/pull/6851)
- [Update event documentation](https://github.com/serverless/serverless/pull/6857)
- [Upgrade groovy/gradle/plugin versions and dependencies (aws-groovy-gradle)](https://github.com/serverless/serverless/pull/6862)
- [Upgrade gradle/plugins version and dependencies (aws-clojure-gradle)](https://github.com/serverless/serverless/pull/6861)
- [IoT integration tests](https://github.com/serverless/serverless/pull/6837)
- [Update https-proxy-agent dependency](https://github.com/serverless/serverless/pull/6866)
- [Allow to use Ref in stream arn property](https://github.com/serverless/serverless/pull/6856)
- [Add Tests for resolveFilePathsFromPatterns()](https://github.com/serverless/serverless/pull/6825)
- [Integration tests improvements and fixes](https://github.com/serverless/serverless/pull/6867)
- [Honor cfnRole in custom resources](https://github.com/serverless/serverless/pull/6871)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.54.0...v1.55.0)

# 1.54.0 (2019-10-09)

- [Fixing typos in variable names](https://github.com/serverless/serverless/pull/6746)
- [Simplify GitHub Issue / PR templates](https://github.com/serverless/serverless/pull/6753)
- [Capture and span docs](https://github.com/serverless/serverless/pull/6757)
- [Automate keeping the sfe-next branch upto date](https://github.com/serverless/serverless/pull/6743)
- [Update dependencies in aws-scala-sbt template](https://github.com/serverless/serverless/pull/6754)
- [PR Template --> Hide useful scripts in expandable section](https://github.com/serverless/serverless/pull/6763)
- [Doc refactoring and new features](https://github.com/serverless/serverless/pull/6758)
- [doc: add cosmosdb events doc](https://github.com/serverless/serverless/pull/6794)
- [Showcase how to use AWS SDK in sls helpers](https://github.com/serverless/serverless/pull/6788)
- [Issue 4867 - Allowing InvokeBridge to find handleRequest method from super classes](https://github.com/serverless/serverless/pull/6791)
- [Update Azure environment variable documentation](https://github.com/serverless/serverless/pull/6798)
- [Update quick-start.md](https://github.com/serverless/serverless/pull/6802)
- [Add Questions issue template that navigate users to forums](https://github.com/serverless/serverless/pull/6786)
- [Update SLS Deploy Documentation](https://github.com/serverless/serverless/pull/6790)
- [S3 Block Public Access](https://github.com/serverless/serverless/pull/6779)
- [Documentation for CI/CD](https://github.com/serverless/serverless/pull/6767)
- [Added logging Implementation for serverless openwhisk-nodejs template](https://github.com/serverless/serverless/pull/6806)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.53.0...v1.54.0)

# 1.53.0 (2019-09-25)

- [Respect logRetentionInDays in log group for websocket](https://github.com/serverless/serverless/pull/6658)
- [Remove requirement for an existing AWS profile on sls package command](https://github.com/serverless/serverless/pull/6564)
- [Adding docs on using captureError](https://github.com/serverless/serverless/pull/6670)
- [Make minor correction to CONTRIBUTING.md.](https://github.com/serverless/serverless/pull/6682)
- [[Docs] Added clarification on specifying SNS ARN](https://github.com/serverless/serverless/pull/6678)
- [Fix regular expression escaping in aws plugin.](https://github.com/serverless/serverless/pull/6689)
- [Update Azure quickstart and Azure Node.js project README](https://github.com/serverless/serverless/pull/6376)
- [Update Azure CLI Reference Docs](https://github.com/serverless/serverless/pull/6380)
- [Docs: update and clean up hello world app documentation](https://github.com/serverless/serverless/pull/6664)
- [Update Azure provider guide docs](https://github.com/serverless/serverless/pull/6403)
- [Update azure nodejs template](https://github.com/serverless/serverless/pull/6626)
- [Move common test utils to @serverless/test](https://github.com/serverless/serverless/pull/6660)
- [Add testing docs](https://github.com/serverless/serverless/pull/6696)
- [Add aliyun provider](https://github.com/serverless/serverless/pull/4922)
- [Update homepage in package.json to point to the docs](https://github.com/serverless/serverless/pull/6703)
- [Fix typo](https://github.com/serverless/serverless/pull/6712)
- [Truncated aliyun events menuText](https://github.com/serverless/serverless/pull/6708)
- [Added Components Versions](https://github.com/serverless/serverless/pull/6702)
- [Add commas when specifying Google roles for legibility](https://github.com/serverless/serverless/pull/6707)
- [Add Theodo to the consultants section of the README](https://github.com/serverless/serverless/pull/6713)
- [Remove incorrect AWS Access Role test instruction](https://github.com/serverless/serverless/pull/6686)
- [Feat: add qualifier option to invoke command](https://github.com/serverless/serverless/pull/6711)
- [Upgrade @serverless/test to v2](https://github.com/serverless/serverless/pull/6714)
- [Allow plugins not in registry to be installed](https://github.com/serverless/serverless/pull/6719)
- [PLAT-1599 Modularize interactive AWS setup](https://github.com/serverless/serverless/pull/6639)
- [Documented url+zip deploy strategy for serverless-kubeless](https://github.com/serverless/serverless/pull/6721)
- [Improve message for Windows users in AWS credentials setup](https://github.com/serverless/serverless/pull/6728)
- [Fix custom resources install](https://github.com/serverless/serverless/pull/6742)
- [Add support for MaximumBatchingWindowInSeconds property on stream events](https://github.com/serverless/serverless/pull/6741)
- [Alibaba Docs Update](https://github.com/serverless/serverless/pull/6744)
- [Update Jackson versions](https://github.com/serverless/serverless/pull/6748)
- [Improvements to stats handling](https://github.com/serverless/serverless/pull/6749)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.52.2...v1.53.0)

# 1.52.2 (2019-09-20)

- [Lock graceful-fs at 4.2.1](https://github.com/serverless/serverless/pull/6717)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.52.1...v1.52.2)

# 1.52.1 (2019-09-19)

- [Change how enterprise plugin async init is preformed](https://github.com/serverless/serverless/pull/6687)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.52.0...v1.52.1)

# 1.52.0 (2019-09-11)

- [Add initialize lifecycle event](https://github.com/serverless/serverless/pull/6601)
- [Fix API Gateway name not being resolved API Gateway Resource not in main stack](https://github.com/serverless/serverless/pull/6611)
- [Support optional CloudWatch logs writing for custom resource lambdas](https://github.com/serverless/serverless/pull/6608)
- [Ensure inquirer's chalk override works through symlinks](https://github.com/serverless/serverless/pull/6616)
- [Fixes aws partition name in apigateway resourceArn to support GovCloud](https://github.com/serverless/serverless/pull/6615)
- [Do not retry on AWS 403 errors](https://github.com/serverless/serverless/pull/6618)
- [Fix overriding package settings after packaging function](https://github.com/serverless/serverless/pull/6606)
- [null](https://github.com/serverless/serverless/pull/1)
- [Download templates from a Bitbucket Server](https://github.com/serverless/serverless/pull/6604)
- [Update Readme to replace SC5.io with nordcloud.com](https://github.com/serverless/serverless/pull/6622)
- [Add plugin hooks to define config variable getters](https://github.com/serverless/serverless/pull/6566)
- [Allow for tail on GetAtt parsing](https://github.com/serverless/serverless/pull/6624)
- [Resolve empty config object for an empty config file](https://github.com/serverless/serverless/pull/6631)
- [Remove enterprise from upgrade notes](https://github.com/serverless/serverless/pull/6625)
- [Add support for Lambda@Edge](https://github.com/serverless/serverless/pull/6512)
- [Tests for interactive CLI ](https://github.com/serverless/serverless/pull/6635)
- [Support functions without events in CloudFront remove logging](https://github.com/serverless/serverless/pull/6645)
- [Add support for Condition and DependsOn](https://github.com/serverless/serverless/pull/6642)
- [Improve plugin loading error reporting](https://github.com/serverless/serverless/pull/6646)
- [Use hooks to log Lambda@Edge removal reminder](https://github.com/serverless/serverless/pull/6652)
- [Quickfix "too many open files" issue on Windows](https://github.com/serverless/serverless/pull/6653)
- [Bump sfe plugin!](https://github.com/serverless/serverless/pull/6654)
- [replace use of tenant with org in docs & templates](https://github.com/serverless/serverless/pull/6655)
- [Update insights.md](https://github.com/serverless/serverless/pull/6663)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.51.0...v1.52.0)

# 1.51.0 (2019-08-28)

- [AWS API Gateway customize log level](https://github.com/serverless/serverless/pull/6542)
- [Fix retained layer logical id](https://github.com/serverless/serverless/pull/6545)
- [add docs for options misused in #6546](https://github.com/serverless/serverless/pull/6547)
- [Fix: Remove Bluebird promise warning when NODE_ENV=development](https://github.com/serverless/serverless/pull/6556)
- [AWS API Gateway set value of provider.logRetentionInDays for log group expiration](https://github.com/serverless/serverless/pull/6548)
- [Fix support for external websocketApiId](https://github.com/serverless/serverless/pull/6543)
- [Ensure AWS SDK is mocked for tests that call it](https://github.com/serverless/serverless/pull/6571)
- [do not log warnings on empty arrays](https://github.com/serverless/serverless/pull/6554)
- [API Gateway enable/disable access/execution logs](https://github.com/serverless/serverless/pull/6578)
- [Allow unresolved Rest API id with provider.tags setting](https://github.com/serverless/serverless/pull/6586)
- [Improve error reporting](https://github.com/serverless/serverless/pull/6585)
- [Fix exclusion of Yarn logs in Lambda packages](https://github.com/serverless/serverless/pull/6589)
- [Improve Rest API id resolution for SDK updates](https://github.com/serverless/serverless/pull/6587)
- [Fix ServerlessError handling](https://github.com/serverless/serverless/pull/6588)
- [Style updates for docs](https://github.com/serverless/serverless/pull/6596)
- [PLAT-1629 - Fix custom resource lambda naming](https://github.com/serverless/serverless/pull/6599)
- [Ensure API Gateway CloudWatch role is setup via custom resource](https://github.com/serverless/serverless/pull/6591)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.50.1...v1.51.0)

# 1.50.1 (2019-08-26)

- [add `interactiveCli:end lifecycle hook & bump dashboard plugin dep`](https://github.com/serverless/serverless/pull/6549)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.50.0...v1.50.1)

# 1.50.0 (2019-08-14)

- [Render event information in aws-ruby handler template](https://github.com/serverless/serverless/pull/6478)
- [Adding ap-south-1 to supported region list](https://github.com/serverless/serverless/pull/6473)
- [Fix invalid path char in GoLang packaging on Windows](https://github.com/serverless/serverless/pull/6484)
- [Multiple event definitions for existing S3 bucket](https://github.com/serverless/serverless/pull/6477)
- [Remove Enterprise and Platform from log info](https://github.com/serverless/serverless/pull/6501)
- [Allow AWS Subscription Filters to be reordered](https://github.com/serverless/serverless/pull/6471)
- [Check if more than 1 existing bucket is configured](https://github.com/serverless/serverless/pull/6506)
- [Multiple event definitions for existing Cognito User Pools](https://github.com/serverless/serverless/pull/6491)
- [Improve error handling](https://github.com/serverless/serverless/pull/6502)
- [Add PreTokenGeneration & UserMigration Cognito triggers](https://github.com/serverless/serverless/pull/6511)
- [Add Twilio Runtime to create templates](https://github.com/serverless/serverless/pull/6467)
- [Update kubeless guide docs](https://github.com/serverless/serverless/pull/6513)
- [Fix ImportValue handling in existing S3 buckets #6416](https://github.com/serverless/serverless/pull/6417)
- [Improve interactive AWS creds flow](https://github.com/serverless/serverless/pull/6449)
- [Retain existing Cognito User Pool config](https://github.com/serverless/serverless/pull/6519)
- [Switch integration tests runner from Jest to Mocha](https://github.com/serverless/serverless/pull/6517)
- [Change strategy for deciding to deploy new function.](https://github.com/serverless/serverless/pull/6520)
- [Fix support for EventBridge partner event sources](https://github.com/serverless/serverless/pull/6518)
- [fix(GITHUB-6525-5172): Rewrite copyDirContentsSyncAllow to call fs-extra::copySync() on the directories instead of calling it on the files to copy individually](https://github.com/serverless/serverless/pull/6526)
- [Do not crash CI on Coveralls error](https://github.com/serverless/serverless/pull/6535)
- [Only add merged IAM policies for Lambda when they will be used (#6262)](https://github.com/serverless/serverless/pull/6534)
- [Setup APIGW CloudWatch role via custom resource](https://github.com/serverless/serverless/pull/6531)
- [Fix deploy command if package.individually set on a function-level](https://github.com/serverless/serverless/pull/6537)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.49.0...v1.50.0)

# 1.49.0 (2019-07-30)

- [Remove hard coded partition when validating subscription filters](https://github.com/serverless/serverless/pull/6446)
- [Fix cross-account/cross-regions SNS subscriptions to topics with the same name](https://github.com/serverless/serverless/pull/6445)
- [Add EventBridge event source](https://github.com/serverless/serverless/pull/6397)
- [Update invoke-local.md documentation](https://github.com/serverless/serverless/pull/6466)
- [Doc new insights](https://github.com/serverless/serverless/pull/6469)
- [New error insight alert doc update to reflect per execution inspection](https://github.com/serverless/serverless/pull/6472)
- [Existing S3 bucket fixes](https://github.com/serverless/serverless/pull/6456)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.48.4...v1.49.0)

# 1.48.4 (2019-07-25)

- [Add note for supported version of existing bucket feature](https://github.com/serverless/serverless/pull/6435)
- [Support in interactive flow for SFE provided AWS creds](https://github.com/serverless/serverless/pull/6440)
- [Fix sls package regression caused by cred fail fast](https://github.com/serverless/serverless/pull/6447)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.48.3...v1.48.4)

# 1.48.3 (2019-07-23)

- [Issue 6364 request path](https://github.com/serverless/serverless/pull/6422)
- [Remove spaces from Cognito Pool Name](https://github.com/serverless/serverless/pull/6419)
- [Use slss.io for links](https://github.com/serverless/serverless/pull/6428)
- [Fix regression in EC2 & CodeBuild caused by missing creds check](https://github.com/serverless/serverless/pull/6427<Paste>)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.48.2...v1.48.3)

# 1.48.2 (2019-07-19)

- [Fix issues in post install and pre uninstall scripts](https://github.com/serverless/serverless/pull/6415)
-

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.48.1...v1.48.2)

# 1.48.1 (2019-07-19)

- [Use Python3 for Python in interactive setup](https://github.com/serverless/serverless/pull/6406)
- [Fixing broken link for Node install.](https://github.com/serverless/serverless/pull/6405)
- [Added Cloud Build option for serverless deploy guide](https://github.com/serverless/serverless/pull/6401)
- [Changed AWS subscription filters to use function object name](https://github.com/serverless/serverless/pull/6402)
- [Strip trailing comment when renaming a service](https://github.com/serverless/serverless/pull/6408)
- [Improve tracking reliability](https://github.com/serverless/serverless/pull/6410)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.48.0...v1.48.1)

# 1.48.0 (2019-07-18)

- [SFE plugin & sdk version info](https://github.com/serverless/serverless/pull/6344)
- [Allow optionally splitting SSM parameter value for StringList type](https://github.com/serverless/serverless/pull/6365)
- [Cross region SNS Trigger](https://github.com/serverless/serverless/pull/6366)
- [Fix typo](https://github.com/serverless/serverless/pull/6379)
- [Add SLS_NO_WARNINGS env var](https://github.com/serverless/serverless/pull/6345)
- [Fix async S3 test](https://github.com/serverless/serverless/pull/6385)
- [Fix AWS secret access key validation in interactive CLI](https://github.com/serverless/serverless/pull/6387)
- [Improve post install message](https://github.com/serverless/serverless/pull/6388)
- [PLAT-1385 Ensure expected service name in interactively created project](https://github.com/serverless/serverless/pull/6386)
- [Updated gradle and kotlin.js gradle plugin fixing #5598](https://github.com/serverless/serverless/pull/6372)
- [actually update the right aws creds link interactive setup aws](https://github.com/serverless/serverless/pull/6395)
- [Integrating Components](https://github.com/serverless/serverless/pull/6350)
- [Add support for existing Cognito User Pools](https://github.com/serverless/serverless/pull/6362)
- [Add the missing colon](https://github.com/serverless/serverless/pull/6398)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.47.0...v1.48.0)

# 1.47.0 (2019-07-10)

- [Add Onica as a Consultant](https://github.com/serverless/serverless/pull/6300)
- [Correct typo](https://github.com/serverless/serverless/pull/6301)
- [Adapt new ESLint and Prettier configuration](https://github.com/serverless/serverless/pull/6284)
- [Ensure deploy is triggered in CI](https://github.com/serverless/serverless/pull/6306)
- [Remove jsbeautify configuration](https://github.com/serverless/serverless/pull/6309)
- [Improve PR template](https://github.com/serverless/serverless/pull/6308)
- [Allow users to specify API Gateway Access Log format](https://github.com/serverless/serverless/pull/6299)
- [Fix service.provider.region resolution](https://github.com/serverless/serverless/pull/6317)
- [Add null as a consultant](https://github.com/serverless/serverless/pull/6323)
- [Update very minor typo in credentials.md](https://github.com/serverless/serverless/pull/6321)
- [Expose non-errors in informative way](https://github.com/serverless/serverless/pull/6318)
- [Fix async leaks detection conditional](https://github.com/serverless/serverless/pull/6319)
- [Typo fix in AWS ALB event documentation](https://github.com/serverless/serverless/pull/6325)
- [Websockets: fix passing log group ARN](https://github.com/serverless/serverless/pull/6310)
- [Specify invoke local option in the guide](https://github.com/serverless/serverless/pull/6327)
- [Update Webpack version and usage of aws-nodejs-ecma-script template](https://github.com/serverless/serverless/pull/6324)
- [Make ALB event target group names unique](https://github.com/serverless/serverless/pull/6322)
- [Improve Travis CI conf](https://github.com/serverless/serverless/pull/6330)
- [Support for Github Entreprise in sls create](https://github.com/serverless/serverless/pull/6332)
- [Merge patch 1.46.1 release artifacts back into master](https://github.com/serverless/serverless/pull/6343)
- [Add support for existing S3 buckets](https://github.com/serverless/serverless/pull/6290)
- [PLAT-1202 - Interactive `serverless` create](https://github.com/serverless/serverless/pull/6294)
- [PLAT-1091 - message in `npm i` output about the `serverless` quickstart command](https://github.com/serverless/serverless/pull/6238)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.46.1...v1.47.0)

# 1.46.1 (2019-06-28)

- [Fix service.provider.region resolution](https://github.com/serverless/serverless/pull/6317)
- [Ensure deploy is triggered in CI](https://github.com/serverless/serverless/pull/6306)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.46.0...v1.46.1)

# 1.46.0 (2019-06-26)

- [Fix formatting issue with Markdown link](https://github.com/serverless/serverless/pull/6228)
- [Update docs | dont use provider.tags with shared API Gateway](https://github.com/serverless/serverless/pull/6225)
- [Fix: Update azure template](https://github.com/serverless/serverless/pull/6258)
- [Improve user message](https://github.com/serverless/serverless/pull/6254)
- [Reference custom ApiGateway for models and request validators if conf…](https://github.com/serverless/serverless/pull/6231)
- [Ensure integration tests do not fail when run concurrently](https://github.com/serverless/serverless/pull/6256)
- [Improve integration test experience](https://github.com/serverless/serverless/pull/6253)
- [Fix lambda integration timeout response template](https://github.com/serverless/serverless/pull/6255)
- [Fix duplicate packaging issue](https://github.com/serverless/serverless/pull/6244)
- [Fix Travis configuration for branch/tag runs](https://github.com/serverless/serverless/pull/6265)
- [fixed a typo 🖊](https://github.com/serverless/serverless/pull/6275)
- [Fix #6267](https://github.com/serverless/serverless/pull/6268)
- [#6017 Allow to load plugin from path](https://github.com/serverless/serverless/pull/6261)
- [Added correction based on community feedback](https://github.com/serverless/serverless/pull/6286)
- [Remove package-lock.json and shrinkwrap scripts](https://github.com/serverless/serverless/pull/6280)
- [Remove README redundant link](https://github.com/serverless/serverless/pull/6288)
- [Remove default stage value in provider object](https://github.com/serverless/serverless/pull/6200)
- [Use naming to get stackName](https://github.com/serverless/serverless/pull/6285)
- [Fix typo in link to ALB docs](https://github.com/serverless/serverless/pull/6292)
- [Add ip, method, header and query conditions to ALB events](https://github.com/serverless/serverless/pull/6293)
- [Feature/support external websocket api](https://github.com/serverless/serverless/pull/6272)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.45.1...v1.46.0)

# 1.45.1 (2019-06-12)

- [Fix IAM policies setup for functions with custom name](https://github.com/serverless/serverless/pull/6240)
- [Fix Travis CI deploy config](https://github.com/serverless/serverless/pull/6234)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.45.0...v1.45.1)

# 1.45.0 (2019-06-12)

- [Add `--config` option](https://github.com/serverless/serverless/pull/6216)
- [Fix and improve ESlint config](https://github.com/serverless/serverless/pull/6188)
- [Tests: Fix mocha config](https://github.com/serverless/serverless/pull/6187)
- [Thorough integration testing](https://github.com/serverless/serverless/pull/6148)
- [Tests: Isolation improvements](https://github.com/serverless/serverless/pull/6186)
- [Add support for Websocket Logs](https://github.com/serverless/serverless/pull/6088)
- [Cleanup and improve Travis CI configuration](https://github.com/serverless/serverless/pull/6178)
- [Tests: Fix stub configuration](https://github.com/serverless/serverless/pull/6205)
- [Tests: Upgrade Sinon](https://github.com/serverless/serverless/pull/6206)
- [Add Application Load Balancer event source](https://github.com/serverless/serverless/pull/6073)
- [Do not run integration tests for PR's](https://github.com/serverless/serverless/pull/6207)
- [Adding a validation to validation.js script](https://github.com/serverless/serverless/pull/6192)
- [Tests: Upgrade dependencies, improve isolation and experience on Windows](https://github.com/serverless/serverless/pull/6208)
- [Add support for S3 hosted package artifacts](https://github.com/serverless/serverless/pull/6196)
- [Remove root README generator](https://github.com/serverless/serverless/pull/6215)
- [Myho/npm lint fix](https://github.com/serverless/serverless/pull/6217)
- [Use common prefix for log groups permissions at Lambdas' execution roles](https://github.com/serverless/serverless/pull/6212)
- [Update Scala version to 2.13.0 for aws-scala-sbt template](https://github.com/serverless/serverless/pull/6222)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.44.1...v1.45.0)

# 1.44.1 (2019-05-28)

- [Fix enterprise plugin lookup in global yarn installs](https://github.com/serverless/serverless/pull/6183)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.44.0...v1.44.1)

# 1.44.0 (2019-05-28)

- [Built in integration of Serverless Enterprise](https://github.com/serverless/serverless/pull/6074)
- [Setup Travis Windows support / Remove AppVeyor](https://github.com/serverless/serverless/pull/6132)
- [Update required Node.js version / Add version check](https://github.com/serverless/serverless/pull/6077)
- [Add scopes for cognito type APIGW referenced authorizer ](https://github.com/serverless/serverless/pull/6150)
- [Do not throw error if authorizer has empty claims](https://github.com/serverless/serverless/pull/6121)
- [Tests: Patch mocha bugs and fix broken async flow cases](https://github.com/serverless/serverless/pull/6157)
- [Fix tagging API Gateway stage fails if tag contains special characters like space](https://github.com/serverless/serverless/pull/6139)
- [Solve the problem of principal format in China region](https://github.com/serverless/serverless/pull/6127)
- [Upgrade mocha, switch from istanbul to nyc, improve tests configuration](https://github.com/serverless/serverless/pull/6169)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.43.0...v1.44.0)

# 1.43.0 (2019-05-20)

- [Update services.md](https://github.com/serverless/serverless/pull/6138)
- [Azure: exclude development dependency files when packaging functions](https://github.com/serverless/serverless/pull/6137)
- [Update release process docs and toolings](https://github.com/serverless/serverless/pull/6113)
- [Update AWS Node.js runtime to version 10](https://github.com/serverless/serverless/pull/6142)
- [Fix tests setup issues](https://github.com/serverless/serverless/pull/6147)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.42.3...v1.43.0)

# 1.42.3 (2019-05-14)

- [Update deploy.md](https://github.com/serverless/serverless/pull/6110)
- [Adding a more specific example of how to package individually](https://github.com/serverless/serverless/pull/6108)
- [Update Azure Functions Template](https://github.com/serverless/serverless/pull/6106)
- [Update cloudflare documentation](https://github.com/serverless/serverless/pull/6105)
- [Azure template update](https://github.com/serverless/serverless/pull/6122)
- [Remove not used module](https://github.com/serverless/serverless/pull/6095)
- [Support color output in tests](https://github.com/serverless/serverless/pull/6119)
- [Fix validation after API Gateway deployment](https://github.com/serverless/serverless/pull/6128)
- [Improve handling of custom API Gateway options](https://github.com/serverless/serverless/pull/6129)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.42.2...v1.42.3)

# 1.42.2 (2019-05-10)

- [Fix restApiId resolution in post CF deployment phase](https://github.com/serverless/serverless/pull/6111)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.42.1...v1.42.2)

# 1.42.1 (2019-05-09)

- [Fix bug with `cors: true`](https://github.com/serverless/serverless/pull/6104)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.42.0...v1.42.1)

# 1.42.0 (2019-05-09)

- [Update cors.md](https://github.com/serverless/serverless/pull/6027)
- [Add tags to AWS APIGateway Stage](https://github.com/serverless/serverless/pull/5851)
- [Remove safeguards when using API Gateway Stage resource settings](https://github.com/serverless/serverless/pull/6040)
- [Enable Setting Amazon API Gateway API Key Value](https://github.com/serverless/serverless/pull/5982)
- [Add more specific sub command error handling](https://github.com/serverless/serverless/pull/6038)
- [Use region pseudo parameter](https://github.com/serverless/serverless/pull/6026)
- [Add authorization scopes support for cognito user pool integration](https://github.com/serverless/serverless/pull/6000)
- [Merging v1.41.1 changes back into master](https://github.com/serverless/serverless/pull/6042)
- [Support wildcard in API Gateway cors domains](https://github.com/serverless/serverless/pull/6043)
- [Support setting both proxy and ca file for awsprovider AWS config agent](https://github.com/serverless/serverless/pull/5952)
- [Fix doc: How to update serverless](https://github.com/serverless/serverless/pull/6052)
- [Update event.md](https://github.com/serverless/serverless/pull/6061)
- [Allow Fn::Join in stream event arns](https://github.com/serverless/serverless/pull/6064)
- [Fix markup error with Authe1.42.0 (2019-05-09)ntication value](https://github.com/serverless/serverless/pull/6068)
- [Drop duplicate paragraph in aws/guide/credentials](https://github.com/serverless/serverless/pull/6075)
- [Improve integration test of aws-scala-sbt](https://github.com/serverless/serverless/pull/6079)
- [Highlight skipping of deployments](https://github.com/serverless/serverless/pull/6070)
- [Add support for API Gateway REST API Logs](https://github.com/serverless/serverless/pull/6057)
- [Implement logging with Log4j2 for aws-scala-sbt](https://github.com/serverless/serverless/pull/6078)
- [Update serverless.yml.md](https://github.com/serverless/serverless/pull/6085)
- [Fixed three small typos in doc](https://github.com/serverless/serverless/pull/6092)
- [fixed small errors in spotinst docs](https://github.com/serverless/serverless/pull/6093)
- [Add support for API Gateway Binary Media Types](https://github.com/serverless/serverless/pull/6063)
- [SDK based API Gateway Stage updates](https://github.com/serverless/serverless/pull/6084)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.41.1...v1.42.0)

# 1.41.1 (2019-04-23)

- [Remove safeguards when using API Gateway Stage resource settings](https://github.com/serverless/serverless/pull/6040)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.41.0...v1.41.1)

# 1.41.0 (2019-04-18)

- [Add error message when provider does not exist](https://github.com/serverless/serverless/pull/5964)
- [The code for removing comments is easy to read](https://github.com/serverless/serverless/pull/5973)
- [Added rust template for Cloudflare WASM](https://github.com/serverless/serverless/pull/5971)
- [Remove useless variable assignment](https://github.com/serverless/serverless/pull/5991)
- [Merge identical IF-branches](https://github.com/serverless/serverless/pull/5989)
- [eslint: Mark as root config](https://github.com/serverless/serverless/pull/5998)
- [#4750 Java invoke local support for handlers that implement RequestStreamHandler](https://github.com/serverless/serverless/pull/5954)
- [#5993: Ability to pass args for docker run command during invoke local docker](https://github.com/serverless/serverless/pull/5994)
- [Add additional Capability when Transform is detected](https://github.com/serverless/serverless/pull/5997)
- [#5990: Fix layer download caching during invoke local docker](https://github.com/serverless/serverless/pull/5992)
- [#5947: Ensure invoke local docker runs lambda with the dependencies](https://github.com/serverless/serverless/pull/5977)
- [Updating Node.js runtime version](https://github.com/serverless/serverless/pull/6011)
- [Make it easier on the eyes of serverless newcomers](https://github.com/serverless/serverless/pull/6013)
- [Allow specifying a retention policy for lambda layers](https://github.com/serverless/serverless/pull/6010)
- [Update quick-start.md](https://github.com/serverless/serverless/pull/6018)
- [Add AWS x-ray support for API Gateway](https://github.com/serverless/serverless/pull/5692)
- [Add support for multiple usage plans](https://github.com/serverless/serverless/pull/5970)
- [#5945: Invoke local docker to pass env vars to lambda container](https://github.com/serverless/serverless/pull/5988)
- [Update newsletter + enterprise link in readme](https://github.com/serverless/serverless/pull/6023)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.40.0...v1.41.0)

# 1.40.0 (2019-03-28)

- [Align error logging](https://github.com/serverless/serverless/pull/5937)
- [Fixing minor typo](https://github.com/serverless/serverless/pull/5943)
- [Documentation tweak around shared authorizers](https://github.com/serverless/serverless/pull/5944)
- [Support for asynchronous lambda invocation with integration type AWS](https://github.com/serverless/serverless/pull/5898)
- [Add unit tests for getLocalAccessKey function](https://github.com/serverless/serverless/pull/5948)
- [Document changes from #4951](https://github.com/serverless/serverless/pull/5949)
- [Added ability to create custom stack names and API names](https://github.com/serverless/serverless/pull/4951)
- [Fixes #5188 "Failed to fetch the event types list due the error: API …](https://github.com/serverless/serverless/pull/5335)
- [Allow \* in variable string literal defaults](https://github.com/serverless/serverless/pull/5640)
- [Add Serverless instanceId concept](https://github.com/serverless/serverless/pull/5926)
- [Doc: Include that APIGateway status code of async events](https://github.com/serverless/serverless/pull/5957)
- [Update npm dependencies](https://github.com/serverless/serverless/pull/5968)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.39.1...v1.40.0)

# 1.39.1 (2019-03-18)

- [Revert "Fixed #4188 - Package generating incorrect package artifact path in serverless-state.json"](https://github.com/serverless/serverless/pull/5936)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.39.0...v1.39.1)

# 1.39.0 (2019-03-15)

- [Add support for invoke local with docker](https://github.com/serverless/serverless/pull/5863)
- [fix regression with golang check on windows ](https://github.com/serverless/serverless/pull/5899)
- [Support for Cloudwatch Event InputTransformer](https://github.com/serverless/serverless/pull/5912)
- [Allow individual packaging with TypeScript source maps](https://github.com/serverless/serverless/pull/5743)
- [Support API Gateway stage deployment description](https://github.com/serverless/serverless/pull/5509)
- [Allow Fn::Join in SQS arn builder](https://github.com/serverless/serverless/pull/5351)
- [Add AWS x-ray support for Lambda](https://github.com/serverless/serverless/pull/5860)
- [Fix CloudFormation template normalization](https://github.com/serverless/serverless/pull/5885)
- [Fix bug when using websocket events with functions with custom roles](https://github.com/serverless/serverless/pull/5880)
- [Print customized function names correctly in sls info output](https://github.com/serverless/serverless/pull/5883)
- [Added websockets authorizer support](https://github.com/serverless/serverless/pull/5867)
- [Support more route characters for websockets](https://github.com/serverless/serverless/pull/5865)
- [kotlin jvm maven updates](https://github.com/serverless/serverless/pull/5872)
- [Put `Custom Response Headers` into `[Responses]`](https://github.com/serverless/serverless/pull/5862)
- [Packaging exclude only config file being used](https://github.com/serverless/serverless/pull/5840)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.38.0...v1.39.0)

# 1.38.0 (2019-02-20)

- [Set timout & others on context in python invoke local](https://github.com/serverless/serverless/pull/5796)
- [Append in Custom Syntax](https://github.com/serverless/serverless/pull/5799)
- [Don't load config for `config`](https://github.com/serverless/serverless/pull/5798)
- [Replace blocking fs.readFileSync with non blocking fs.readFile in checkForChanges.js](https://github.com/serverless/serverless/pull/5791)
- [Added layer option for deploy function update-config](https://github.com/serverless/serverless/pull/5787)
- [fix makeDeepVariable replacement](https://github.com/serverless/serverless/pull/5809)
- [Make local ruby pry work](https://github.com/serverless/serverless/pull/5718)
- [Replace \ with / in paths on windows before passing to nanomatch](https://github.com/serverless/serverless/pull/5808)
- [Support deploying GoLang to AWS from Windows!](https://github.com/serverless/serverless/pull/5813)
- [Fix windows go rework](https://github.com/serverless/serverless/pull/5816)
- [Make use of join operator first argument in sns docs](https://github.com/serverless/serverless/pull/5826)
- [add support for command type='container'](https://github.com/serverless/serverless/pull/5821)
- [Add Google Python function template](https://github.com/serverless/serverless/pull/5819)
- [Update config-credentials.md](https://github.com/serverless/serverless/pull/5827)
- [Update bucket conf to default AES256 encryption.](https://github.com/serverless/serverless/pull/5800)
- [Fix: override wildcard glob pattern (\*\*) in resolveFilePathsFromPatterns](https://github.com/serverless/serverless/pull/5825)
- [Indicate unused context in aws-nodejs-typescipt](https://github.com/serverless/serverless/pull/5832)
- [Add stack trace to aws/invokeLocal errors](https://github.com/serverless/serverless/pull/5835)
- [Missing underscore](https://github.com/serverless/serverless/pull/5836)
- [Updating cloudformation resource reference url](https://github.com/serverless/serverless/pull/5690)
- [Docs: Replacing "runtimes" with "templates"](https://github.com/serverless/serverless/pull/5843)
- [Add support for websockets event](https://github.com/serverless/serverless/pull/5824)
- [AWS: \${ssm} resolve vairbale as JSON if it is stored as JSON in Secrets Manager](https://github.com/serverless/serverless/pull/5842)
- [Fix service name in template install message](https://github.com/serverless/serverless/pull/5839)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.37.1...v1.38.0)

# 1.37.0 (2019-02-06)

- [Fixes for AWS cors config issues](https://github.com/serverless/serverless/pull/5785)
- [Preserve whitespaces in single-quote literal fallback](https://github.com/serverless/serverless/pull/5775)
- [AWS: Add fallback support in ${cf} and ${s3}](https://github.com/serverless/serverless/pull/5758)
- [Throw an error if plugin is executed outside of a serverless directory](https://github.com/serverless/serverless/pull/5636)
- [Require provider.credentials vars to be resolved before s3/ssm/cf vars](https://github.com/serverless/serverless/pull/5763)
- [Provide multi origin cors values](https://github.com/serverless/serverless/pull/5740)
- [handle layers paths with trailing slash and leading ./ or just .](https://github.com/serverless/serverless/pull/5656)
- [Resolve profile before performing aws-sdk dependent actions](https://github.com/serverless/serverless/pull/5744)
- [Fix assuming a role with an AWS profile](https://github.com/serverless/serverless/pull/5739)
- [Allows Fn::GetAtt with Lambda DLQ-onError](https://github.com/serverless/serverless/pull/5139)
- [Fix #5664 - Rollback fails due to a timestamp parsing error](https://github.com/serverless/serverless/pull/5710)
- [AWS: Tell S3 bucket name and how to recover if deployment bucket does not exist](https://github.com/serverless/serverless/pull/5714)
- [Do not print logs if print command is used.](https://github.com/serverless/serverless/pull/5728)
- [Default to error code if message is non-existent](https://github.com/serverless/serverless/pull/4794)
- [Add resource count and warning to info display](https://github.com/serverless/serverless/pull/4822)
- [Add uploaded file name to log while AWS deploy](https://github.com/serverless/serverless/pull/5495)
- [Enable tab completion for slss shortcut](https://github.com/serverless/serverless/pull/4712)
- [Upgrade google-cloudfunctions to v2 and set defaults to node8 etc](https://github.com/serverless/serverless/pull/5311)
- [Convert reservedConcurrency to integer to allow use env var](https://github.com/serverless/serverless/pull/5705)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.36.3...v1.37.0)

# 1.36.3 (2019-01-23)

- [AWS: Consolidates Lambda::Permission objects for cloudwatchLog events](https://github.com/serverless/serverless/pull/5531)
- [Suppress confusing warning "A valid undefined..." ](https://github.com/serverless/serverless/pull/5723)
- [Add google go template](https://github.com/serverless/serverless/pull/5726)
- [Provide AWS_PROFILE from configuration for invoke local](https://github.com/serverless/serverless/pull/5662)
- [Test that CLI does not convert numeric option to number](https://github.com/serverless/serverless/pull/5727)
- [Remove duplicate-handler warnings based on community feedback.](https://github.com/serverless/serverless/pull/5733)
- [Enable download template from a private github repo using personal access token](https://github.com/serverless/serverless/pull/5715)
- [Fix sls plugin install -n @scoped/package](https://github.com/serverless/serverless/pull/5736)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.36.2...v1.36.3)

# 1.36.2 (2019-01-21)

- [AWS: Request cache should add region as key to prevent cross-region cache collision](https://github.com/serverless/serverless/pull/5694)
- [Fixed a link](https://github.com/serverless/serverless/pull/5707)
- [Clarify docs for the http key for GCF](https://github.com/serverless/serverless/pull/5680)
- [Fix awsProvider.js : "Cannot use 'in' operator to search for '0'](https://github.com/serverless/serverless/pull/5688)
- [Fix array notation in stream ARN](https://github.com/serverless/serverless/pull/5702)
- [Remove platform code](https://github.com/serverless/serverless/pull/5687)
- [Increase @types/aws-lambda version in aws-nodejs-typescript template](https://github.com/serverless/serverless/pull/5695)
- [Update aws-scala-sbt template](https://github.com/serverless/serverless/pull/5725)
- [docs: Kubeless secrets](https://github.com/serverless/serverless/pull/5130)
- [docs menu sidebar - added [Getting Started] above [Providers]](https://github.com/serverless/serverless/pull/5721)
- [Fix layer doc reference to functions (should be layers)](https://github.com/serverless/serverless/pull/5697)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.36.1...v1.36.2)

# 1.36.1 (2019-01-14)

- [Update layers.md](https://github.com/serverless/serverless/pull/5678)
- [AWS: Fix stage name validation timing and allow hyphen](https://github.com/serverless/serverless/pull/5686)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.36.0...v1.36.1)

# 1.36.0 (2019-01-10)

- [Log AWS SDK calls in debug mode](https://github.com/serverless/serverless/pull/5604)
- [Added currently supported regions for GCP functions](https://github.com/serverless/serverless/pull/5601)
- [Update Cloudflare Templates](https://github.com/serverless/serverless/pull/5620)
- [AWS: Validate rate/cron syntax before Deploy](https://github.com/serverless/serverless/pull/5635)
- [Fix error log output](https://github.com/serverless/serverless/pull/5378)
- [Support for native async/await in AWS Lambda for aws-nodejs-typescript template ](https://github.com/serverless/serverless/pull/5607)
- [aws-csharp create template uses handler-specific artifact](https://github.com/serverless/serverless/pull/5411)
- [change behaviour on initial stack create failed](https://github.com/serverless/serverless/pull/5631)
- [Add warning for multiple functions having same handler](https://github.com/serverless/serverless/pull/5638)
- [AWS: Add API Gateway stage name validation.](https://github.com/serverless/serverless/pull/5639)
- [fix Cloudflare template config](https://github.com/serverless/serverless/pull/5651)
- [AWS: Fix \${cf.REGION} syntax causes deployment in wrong region](https://github.com/serverless/serverless/pull/5650)
- [support for @ symbol in \${file()} variables paths](https://github.com/serverless/serverless/pull/5312)
- [Fix ResourceLimitExceeded for cloudwatchLog event](https://github.com/serverless/serverless/pull/5554)
- various documentation updates (#5625, #5613, #5628, #5659, #5618, #5437, #5623, #5627, #5665)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.35.1...v1.36.0)

# 1.35.1 (2018-12-18)

- [fixed regression preventing including files outside working dir](https://github.com/serverless/serverless/pull/5602)
- [Update ruby template gitignore](https://github.com/serverless/serverless/pull/5599)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.35.0...v1.35.1)

# 1.35.0 (2018-12-13)

- [Fix logRetentionInDays regression in AWS](https://github.com/serverless/serverless/pull/5562)
- [`invoke local` support for Ruby lambdas](https://github.com/serverless/serverless/pull/5559)
- [Set reserved concurrency in cfn template even if zero](https://github.com/serverless/serverless/pull/5566)
- [Fix `--env` being shadowed when using `sls invoke local`](https://github.com/serverless/serverless/pull/5565)
- [Preserve whitespace in variable literal defaults](https://github.com/serverless/serverless/pull/5571)
- [Drastically improved dev dependency exclusion performance](https://github.com/serverless/serverless/pull/5574)
- [Extend \${cf} syntax to get output from another region](https://github.com/serverless/serverless/pull/5579)
- [Upgrade aws-sdk dep to fix issues with using AWS Profiles](https://github.com/serverless/serverless/pull/5587)
- Documentation updates

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.34.1...v1.35.0)

# 1.34.1 (2018-11-30)

- [Add aws-ruby template](https://github.com/serverless/serverless/pull/5546)
- [Add support for API Gateway payload compression](https://github.com/serverless/serverless/pull/5529)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.34.0...v1.34.1)

# 1.34.0 (2018-11-29)

- [Lambda Layers support](https://github.com/serverless/serverless/pull/5538)
- [Python3.7 support](https://github.com/serverless/serverless/pull/5505)
- [Updating roles requirement for GCF deployment](https://github.com/serverless/serverless/pull/5490)
- [Support returning promises from serverless.js](https://github.com/serverless/serverless/pull/4827)
- [update CloudFlare worker docs to new more consistent config](https://github.com/serverless/serverless/pull/5521)
- [fix --aws-profile so it overrides profile defined in serverless.yml](https://github.com/serverless/serverless/pull/5516)
- [Fix invoke local when using a callback in nodejs](https://github.com/serverless/serverless/pull/5525)
- [Fix parsing of --data & --context option with invoke local](https://github.com/serverless/serverless/pull/5512)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.33.2...v1.34.0)

# 1.33.2 (2018-11-18)

- [fix `invoke local` with python2.7 projects](https://github.com/serverless/serverless/pull/5500)
- [fix `logs --tail`](https://github.com/serverless/serverless/pull/5503)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.33.1...v1.33.2)

# 1.33.1 (2018-11-15)

- [fix issue with `sls deploy --verbose --stage foobar`](https://github.com/serverless/serverless/pull/5492)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.33.0...v1.33.1)

# 1.33.0 (2018-11-15)

- [2116 consistent errors missing config](https://github.com/serverless/serverless/pull/5298)
- [Update plugin version of google-nodejs template](https://github.com/serverless/serverless/pull/5473)
- [insert line break to suppress warning](https://github.com/serverless/serverless/pull/5445)
- [Fix wrong example function name.](https://github.com/serverless/serverless/pull/5477)
- [Removed errant apostrophe](https://github.com/serverless/serverless/pull/5471)
- [Wrong error when S3 bucket name starts with an upper-case character](https://github.com/serverless/serverless/pull/5409)
- [Fix integration test](https://github.com/serverless/serverless/pull/5440)
- [Use pythonX instead of pythonX.Y in invoke local(take 3)](https://github.com/serverless/serverless/pull/5210)
- [update python invokeLocal to detect tty](https://github.com/serverless/serverless/pull/5355)
- [Fix typo in Google workflow](https://github.com/serverless/serverless/pull/5433)
- [Updating services.md > Invoking Serverless locally](https://github.com/serverless/serverless/pull/5425)
- [Assume role and MFA support for Serverless CLI](https://github.com/serverless/serverless/pull/5432)
- [Fix build error caused by new docs PR ](https://github.com/serverless/serverless/pull/5435)
- [Adding Ruby support for OpenWhisk provider plugin.](https://github.com/serverless/serverless/pull/5427)
- [Update Cloudflare Workers documentation](https://github.com/serverless/serverless/pull/5419)
- [break single general issue template into two specialized templates](https://github.com/serverless/serverless/pull/5405)
- [Improve language in alexa-skill documentation](https://github.com/serverless/serverless/pull/5408)
- [APIG ApiKeySourceType support.](https://github.com/serverless/serverless/pull/5395)
- [Revert "Update cognito-user-pool.md"](https://github.com/serverless/serverless/pull/5399)
- [Let function package.individually config override service artifact](https://github.com/serverless/serverless/pull/5364)
- [Added CloudWatch Proxy to examples](https://github.com/serverless/serverless/pull/5270)
- [Multiple cloudformation resources](https://github.com/serverless/serverless/pull/5250)
- [Added possibility to specify custom S3 key prefix instead of the stan…](https://github.com/serverless/serverless/pull/5299)
- [Doc update for openwhisk package name](https://github.com/serverless/serverless/pull/5375)
- [add aws-go-mod](https://github.com/serverless/serverless/pull/5393)
- [Fix bin process not always exiting](https://github.com/serverless/serverless/pull/5349)
- [Avoid args being rounded and converted to numbers](https://github.com/serverless/serverless/pull/5361)
- [Add CacheControl headers on the OPTIONS response in AWS API Gateway](https://github.com/serverless/serverless/pull/5328)
- [fix Makefile style for Go template](https://github.com/serverless/serverless/pull/5389)
- [Update handler name when deploy a single function](https://github.com/serverless/serverless/pull/5301)
- [fix: Implement context.log function for invoke local command on Python environment.](https://github.com/serverless/serverless/pull/5391)
- [validate if serverless.yml exists when running sls info command](https://github.com/serverless/serverless/pull/5390)
- [Update documentation, README.md](https://github.com/serverless/serverless/pull/5388)
- [Remove invalid log](https://github.com/serverless/serverless/pull/5377)
- [fix 3916 ](https://github.com/serverless/serverless/pull/5387)
- [Update cognito-user-pool.md](https://github.com/serverless/serverless/pull/5384)
- [add gitignore setting to Go template](https://github.com/serverless/serverless/pull/5386)
- [fixed anchor links in aws/guide/variables.md file](https://github.com/serverless/serverless/pull/5370)
- [Serverless Pipeline](https://github.com/serverless/serverless/pull/5360)
- [add Serverless Line Bot example](https://github.com/serverless/serverless/pull/5359)
- [Update invoke-local.md](https://github.com/serverless/serverless/pull/5362)
- [Webtask Deprecation](https://github.com/serverless/serverless/pull/5263)
- [Add Support for Shorthand CloudFormation Syntax](https://github.com/serverless/serverless/pull/5327)
- [Provide Consistent Service Path (Fix #5242)](https://github.com/serverless/serverless/pull/5314)
- [Add Cloudflare to docs/getting-started page.](https://github.com/serverless/serverless/pull/5342)
- [Invoke local override env](https://github.com/serverless/serverless/pull/5313)
- [more faithfully represent aws lambda python runtime context](https://github.com/serverless/serverless/pull/5291)
- [Update AWS TypeScript handler template](https://github.com/serverless/serverless/pull/5309)
- [add untildify package to handle create paths with a ~](https://github.com/serverless/serverless/pull/5062)
- [[Docs] - Add support information for AWS lambda and SQS](https://github.com/serverless/serverless/pull/5305)
- [Update README.md](https://github.com/serverless/serverless/pull/5294)
- [Add information on invoking Workers.](https://github.com/serverless/serverless/pull/5310)
- [Update quick-start.md](https://github.com/serverless/serverless/pull/5308)
- [Cloudflare: Specify config under provider property](https://github.com/serverless/serverless/pull/5289)
- [Create an HttpsProxyAgent for plugin list if necessary](https://github.com/serverless/serverless/pull/5481)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.32.0...v1.33.0)

# 1.32.0 (2018-09-17)

- [Update quick-start.md](https://github.com/serverless/serverless/pull/5290)
- [Backend state item generation and multi-region support](https://github.com/serverless/serverless/pull/5265)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.31.0...v1.32.0)

# 1.31.0 (2018-09-11)

- [Add support for Cloudflare Workers](https://github.com/serverless/serverless/pull/5258)
- [docs: Fix mismatch in AWS Metrics](https://github.com/serverless/serverless/pull/5276)
- [Add new template for AWS Alexa Typescript](https://github.com/serverless/serverless/pull/5266)
- [Remove `/tmp/node-dependencies*`](https://github.com/serverless/serverless/pull/5079)
- [Adds FilterPolicy to SNS event](https://github.com/serverless/serverless/pull/5229)
- [Update API Gateway Default Request Templates](https://github.com/serverless/serverless/pull/5222)
- [Update serverless.yml.md](https://github.com/serverless/serverless/pull/5236)
- [Fix for #3069 - Failing to handle schedule event body params](https://github.com/serverless/serverless/pull/5268)
- [Remove redundant link to same docs page](https://github.com/serverless/serverless/pull/5243)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.30.3...v1.31.0)

# 1.30.3 (2018-08-28)

- [Fix CORS race condition](https://github.com/serverless/serverless/pull/5256)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.30.2...v1.30.3)

# 1.30.2 (2018-08-28)

- [Fixed a bug when using DynamoDB events with Serverless Platform](https://github.com/serverless/serverless/pull/5237)
- [Fixed a bug when using deep variable references](https://github.com/serverless/serverless/pull/5224)
- [Fixed an issue with Makefile of the aws-go-dep template](https://github.com/serverless/serverless/pull/5227)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.30.1...v1.30.2)

# 1.30.1 (2018-08-16)

- [Fix CI deployment to Serverless Platform](https://github.com/serverless/serverless/issues/5182)
- [Fix a minor resources ID issue on Serverless Platform](https://github.com/serverless/serverless/pull/5208)
- [Update nodejs template to 8.10](https://github.com/serverless/serverless/pull/5088)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.30.0...v1.30.1)

# 1.30.0 (2018-08-09)

- [Added support for multiple access keys for multiple tenants](https://github.com/serverless/serverless/pull/5189)
- [Fixed a publishing bug when having more than 100 resources](https://github.com/serverless/serverless/pull/5189)
- [Add Windows support for spawning mvn](https://github.com/serverless/serverless/pull/5028)
- [Update spawn API with {shell=true}](https://github.com/serverless/serverless/pull/5192)
- [AWS Clojurescript Gradle Template](https://github.com/serverless/serverless/pull/5147)
- [Use latest dotnet runtime in AWS Lambda](https://github.com/serverless/serverless/pull/5107)
- [Ignore null errors to allow resolution instead of rejection on undefined SSM variables](https://github.com/serverless/serverless/pull/5119)
- [Fixed a bug when using deep variable references](https://github.com/serverless/serverless/pull/5156)
- [Add support for installing templates and boilerplates from GitLab](https://github.com/serverless/serverless/pull/5116)
- [Fixed that create command didn't use the service name given as -n option](https://github.com/serverless/serverless/pull/5082)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.29.2...v1.30.0)

# 1.29.2 (2018-07-29)

- [Fixed a bug when using APIG lambda integration with Serverless Dashboard](https://github.com/serverless/serverless/pull/5174)
- [Fixed a bug by transforming env var to string when setting num value](https://github.com/serverless/serverless/pull/5166)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.29.1...v1.29.2)

# 1.29.1 (2018-07-28)

- [Fixed a bug when using APIG root path with Serverless Dashboard](https://github.com/serverless/serverless/pull/5170)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.29.0...v1.29.1)

# 1.29.0 (2018-07-26)

- [Fixes issue with Node 10.7.0](https://github.com/serverless/serverless/issues/5133)
- [Serverless Dashboard Updates: Subscriptions, Resources, Deploys and Refresh Tokens](https://github.com/serverless/serverless/pull/5127)
- [Support `invoke local` of AWS Lambda Async Functions](https://github.com/serverless/serverless/pull/4912)
- [Improve aws-scala-sbt template](https://github.com/serverless/serverless/pull/5086)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.28.0...v1.29.0)

# 1.28.0 (2018-07-04)

- [Add SQS event integration](https://github.com/serverless/serverless/pull/5074)
- [Integration with the Serverless Dashboard](https://github.com/serverless/serverless/pull/5043)
- [Add APIG resource policy](https://github.com/serverless/serverless/pull/5071)
- [Add PRIVATE endpoint type](https://github.com/serverless/serverless/pull/5080)
- [Added ability to create custom stack names and API names](https://github.com/serverless/serverless/pull/4951)
- [Add print options to allow digging, transforming and formatting](https://github.com/serverless/serverless/pull/5036)
- [only use json-cycles when opt-in, for state serialization](https://github.com/serverless/serverless/pull/5029)
- [Make function tags inherit provider tags](https://github.com/serverless/serverless/pull/5007)
- [Make local plugins folder configurable](https://github.com/serverless/serverless/pull/4892)
- [More flexible version constraint for AWS Lambda Go library](https://github.com/serverless/serverless/pull/5045)
- [Update aws-java-maven template to use Log4J2 as recommended by AWS](https://github.com/serverless/serverless/pull/5032)
- [Fix binary support for pre-flight requests (OPTIONS method)](https://github.com/serverless/serverless/pull/4895)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.27.0...v1.28.0)

# 1.27.0 (2018-05-02)

- [Add maxAge option for CORS](https://github.com/serverless/serverless/pull/4639)
- [Add fn integration](https://github.com/serverless/serverless/pull/4934)
- [iamManagedPolicies merging with Vpc config](https://github.com/serverless/serverless/pull/4879)
- [Support arrays in function definition too](https://github.com/serverless/serverless/pull/4847)
- [Add iam managed policies](https://github.com/serverless/serverless/pull/4793)
- [Pass authorizer custom context to target lambda](https://github.com/serverless/serverless/pull/4773)
- [Allow UsagePlan's to be created without ApiKeys defined](https://github.com/serverless/serverless/pull/4768)
- [Added name property to cloudwatchEvent CF template](https://github.com/serverless/serverless/pull/4763)
- [Java maven templates for OpenWhisk](https://github.com/serverless/serverless/pull/4758)
- [Pass serverless variable when calling function in referenced file](https://github.com/serverless/serverless/pull/4743)
- [Eliminate/Report Hung Promises, Prepopulate Stage and Region, Handle Quoted Strings](https://github.com/serverless/serverless/pull/4713)
- [Restricting alexaSkill functions to specific Alexa skills](https://github.com/serverless/serverless/pull/4701)
- [Add support for concurrency option in AWS Lambda](https://github.com/serverless/serverless/pull/4694)
- [Fix concurrency upload](https://github.com/serverless/serverless/pull/4677)
- [Support AWS GovCloud and China region deployments](https://github.com/serverless/serverless/pull/4665)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.26.1...v1.27.0)

# 1.26.1 (2018-02-27)

- [Fix lambda integration regression](https://github.com/serverless/serverless/pull/4775)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.26.0...v1.26.1)

# 1.26.0 (2018-01-29)

- [AWS Go support](https://github.com/serverless/serverless/pull/4669)
- [Support for using an existing ApiGateway and Resources](https://github.com/serverless/serverless/pull/4247)
- [Add logRetentionInDays config](https://github.com/serverless/serverless/pull/4591)
- [Add support of `serverless.js` configuration file](https://github.com/serverless/serverless/pull/4590)
- [Add "did you mean..." CLI suggestions](https://github.com/serverless/serverless/pull/4586)
- [Add `--template-path` option to `serverless create`](https://github.com/serverless/serverless/pull/4576)
- [Add support POJO input support for Java invoke local](https://github.com/serverless/serverless/pull/4596)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.25.0...v1.26.0)

# 1.25.0 (2017-12-20)

- [Improve Stage and Region Usage](https://github.com/serverless/serverless/pull/4560)
- [Add API Gateway endpoint configuration](https://github.com/serverless/serverless/pull/4531)
- [Add cache to Variables class](https://github.com/serverless/serverless/pull/4499)
- [Added support for circular references in the variable system](https://github.com/serverless/serverless/pull/4144)
- [Circular Vars Fix](https://github.com/serverless/serverless/pull/4478)
- [Ignore the check whether deploymentBucket exists when using "package"](https://github.com/serverless/serverless/pull/4474)
- [Template / AWS Kotlin JVM Gradle](https://github.com/serverless/serverless/pull/4433)
- [Basic logging for python invoke local](https://github.com/serverless/serverless/pull/4429)
- [Add Amazon S3 Transfer Acceleration support](https://github.com/serverless/serverless/pull/4293)
- [Updated awsProvider to allow manual specification of certificate auth](https://github.com/serverless/serverless/pull/4118)
- [Fix lambda version generation when only function config changes](https://github.com/serverless/serverless/pull/4510)
- [Added request cache and queue to AWS provider and use it from variable resolution](https://github.com/serverless/serverless/pull/4518)
- [Add significant variable usage corner cases](https://github.com/serverless/serverless/pull/4529)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.24.1...v1.25.0)

# 1.24.1 (2017-11-07)

- [Fix this.userStats.track is not a function error when tailing function logs](https://github.com/serverless/serverless/pull/4441)
- [Improve variables test](https://github.com/serverless/serverless/pull/4450)
- [Error when file referenced in serverless.yml does not exist](https://github.com/serverless/serverless/pull/4448)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.24.0...v1.24.1)

# 1.24.0 (2017-11-01)

- [Run "serverless deploy list" if timestamp is not specified in rollback command](https://github.com/serverless/serverless/pull/4297)
- [Add alexaSmartHome event](https://github.com/serverless/serverless/pull/4238)
- [Distinguish plugin initialization error from plugin not found error](https://github.com/serverless/serverless/pull/4322)
- [Removing private: true from function does not change it's state](https://github.com/serverless/serverless/pull/4302)
- [Change packaging order in zipFiles function](https://github.com/serverless/serverless/pull/4299)
- [Enable bluebird long stack traces only in SLS_DEBUG mode](https://github.com/serverless/serverless/pull/4333)
- [Create service using template from an external repository](https://github.com/serverless/serverless/pull/4133)
- [API Gateway timeout hardcap](https://github.com/serverless/serverless/pull/4348)
- [Set stdin to a TTY in invoke.py to allow PDB use](https://github.com/serverless/serverless/pull/4360)
- [Add function attached to API Gateway effective timeout warning](https://github.com/serverless/serverless/pull/4373)
- [Exclude dev dependency .bin executables](https://github.com/serverless/serverless/pull/4383)
- [Fix "deploy function" command by normalizing role](https://github.com/serverless/serverless/pull/4320)
- [Add print command to generate output of computed serverless.yml](https://github.com/serverless/serverless/pull/4169)
- [Print message if Serverless Framework update is available](https://github.com/serverless/serverless/pull/4301)
- [Allow symlinks as custom variable files in serverless.yml](https://github.com/serverless/serverless/pull/4389)
- [Provide option to conceal API Gateway key values from the output](https://github.com/serverless/serverless/pull/4382)
- [Configurable Authorizer Type](https://github.com/serverless/serverless/pull/4372)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.23.0...v1.24.0)

# 1.23.0 (2017-09-21)

- [Obey VIRTUAL_ENV on Windows](https://github.com/serverless/serverless/pull/4286)
- [Implement pinging for the CLI login](https://github.com/serverless/serverless/pull/4206)
- [Fixed a bug with deploy function not inheriting provider config](https://github.com/serverless/serverless/pull/4262)
- [Added Auth0 Webtasks Provider Template for Nodejs](https://github.com/serverless/serverless/pull/4283)
- [Added Java support for invoke local](https://github.com/serverless/serverless/pull/4199)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.22.0...v1.23.0)

# 1.22.0 (2017-09-13)

- [Serverless now fails if provided profile is not valid](https://github.com/serverless/serverless/pull/4245)
- [Removed escaping of double quotes around string values in Serverless Variables](https://github.com/serverless/serverless/pull/4224)
- [Added 4 new plugin commands](https://github.com/serverless/serverless/pull/4046)
- [Added aws-kotlin-jvm-marven template](https://github.com/serverless/serverless/pull/4220)
- [Added --update-config option to deploy function command](https://github.com/serverless/serverless/pull/4173)
- [Added description to CloudWatch Events](https://github.com/serverless/serverless/pull/4221)
- [Added support for aliasing commands](https://github.com/serverless/serverless/pull/4198)
- [Added --function option to deploy command](https://github.com/serverless/serverless/pull/4192)
- [Fixed a bug with Kinesis events](https://github.com/serverless/serverless/pull/4084)
- [Fixed a bug with packaging](https://github.com/serverless/serverless/pull/4189)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.21.1...v1.22.0)

# 1.21.1 (2017-09-06)

- [Preserve file encoding during packaging process](https://github.com/serverless/serverless/pull/4189)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.21.0...v1.21.1)

# 1.21.0 (2017-08-30)

- [Allow custom CLI class instances](https://github.com/serverless/serverless/pull/4160)
- [Add support in Spotinst Functions](https://github.com/serverless/serverless/pull/4127)
- [Add PHP support for OpenWhisk](https://github.com/serverless/serverless/pull/4153)
- [Fixed a bug with stack deletion monitoring](https://github.com/serverless/serverless/pull/4132)
- [Allow AWS Profile CLI option to overwrite config and env](https://github.com/serverless/serverless/pull/3980)
- [Improve performance of the package plugin](https://github.com/serverless/serverless/pull/3924)
- [Add support for custom context with Invoke Local](https://github.com/serverless/serverless/pull/4126)
- [Add aws-nodejs-typescript template](https://github.com/serverless/serverless/pull/4058)
- [Add aws-nodejs-ecma-script template](https://github.com/serverless/serverless/pull/4056)
- [Allow updates for AWS profiles](https://github.com/serverless/serverless/pull/3866)
- [Fixed a bug in Invoke Local when using Python in Windows](https://github.com/serverless/serverless/pull/3832)
- [Fixed a bug with the Variable System overwrites](https://github.com/serverless/serverless/pull/4097)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.20.2...v1.21.0)

# 1.20.2 (2017-08-17)

- [Bump event-gateway version to 0.5.15](https://github.com/serverless/serverless/pull/4116)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.20.1...v1.20.2)

# 1.20.1 (2017-08-17)

- [Rethrow original plugin error in debug mode](https://github.com/serverless/serverless/pull/4091)
- [Add platform gate to serverless run / emit](https://github.com/serverless/serverless/pull/4103)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.20.0...v1.20.1)

# 1.20.0 (2017-08-16)

- [Add Serverless Run plugin](https://github.com/serverless/serverless/pull/4034)
- [Add Serverless Emit plugin](https://github.com/serverless/serverless/pull/4038)
- [Kubeless template for python and nodejs](https://github.com/serverless/serverless/pull/3970)
- [Improve deprecation hook message](https://github.com/serverless/serverless/pull/4011)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.19.0...v1.20.0)

# 1.19.0 (2017-08-02)

- [Removed provider name validation](https://github.com/serverless/serverless/pull/3941)
- [Fixed a bug with dev dependencies exclusion](https://github.com/serverless/serverless/pull/3975)
- [Fixed a bug with "deploy list functions"](https://github.com/serverless/serverless/pull/3971)
- [Fixed a bug with Serverless Plugins loading](https://github.com/serverless/serverless/pull/3960)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.18.1...v1.19.0)

# 1.18.1 (2017-07-28)

- [Fixed a bug with Serverless Variables](https://github.com/serverless/serverless/pull/3996)
- [Fixed a bug with dev dependencies exclusion](https://github.com/serverless/serverless/pull/3975)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.18.0...v1.18.1)

# 1.18.0 (2017-07-20)

- [Added support for a new "default" property for Plugins CLI options](https://github.com/serverless/serverless/pull/3808)
- [Fixed a bug with dev dependencies exclusion](https://github.com/serverless/serverless/pull/3889)
- [Added support for a new "publish" property to opt-out from Platform publishing](https://github.com/serverless/serverless/pull/3950)
- [Fixed a bug with "sls remove" when the stack includes Exports](https://github.com/serverless/serverless/pull/3935)
- [Added support for request parameter configuration with lambda-proxy integration](https://github.com/serverless/serverless/pull/3722)
- [Enhanced the environment variables for invoke local to include AWS_REGION](https://github.com/serverless/serverless/pull/3908)
- [Updated the deploy command to ignore custom plugins in service directory during deployment](https://github.com/serverless/serverless/pull/3910)
- [Fixed a bug with function packaging](https://github.com/serverless/serverless/pull/3856)
- [Updated the package command to ignore function packaging if a custom artifact is specified](https://github.com/serverless/serverless/pull/3876)
- [Added support for absolute paths when using Serverless Variables file references](https://github.com/serverless/serverless/pull/3888)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.17.0...v1.18.0)

# 1.17.0 (2017-07-05)

- Cleanup F# build template output on macOS - #3897
- Add disable flag for OpenWhisk functions - #3830
- Only redeploy when the code/config changes - #3838
- Add opt-out config for dev dependency exclusion - #3877
- Add infinite stack trace for errors - #3839
- Fixed a bug with autocomplete - #3798

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.16.1...v1.17.0)

# 1.16.1 (2017-06-26)

- CI/CD fix for the Serverless Platform - #3829

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.16.0...v1.16.1)

# 1.16.0 (2017-06-21)

- Added support for usage plans to APIG - #3819
- Optmizied packaging to exclude dev dependencies - #3737
- Added support for S3 server side encryption - #3804
- Improved HTTP error handling - #3752
- Throw an error when requsted CF variable doesn't exist - #3739
- Throw an error if an individual package is empty - #3729

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.15.0...v1.16.0)

# 1.15.3 (2017-06-12)

- Fixed autocomplete bug with help option - #3781

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.15.2...v1.15.3)

# 1.15.2 (2017-06-10)

- Fixed installation error - #3763

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.15.0...v1.15.2)

# 1.15.0 (2017-06-08)

- Added autocomplete support to the CLI - #3753
- Added KMS key support - #3672
- Added Cognito User pool support - #3657
- Added serverless.json support - #3647
- Added aws-profile support - #3701
- Added CloudFormation validation support - #3668
- Fixed S3 event race condition bug - #3705
- Fixed CORS origin config bug - #3692

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.14.0...v1.15.0)

# 1.14.0 (2017-05-24)

- Added login command - #3558
- Added support for DeadLetter Config with SNS - #3609
- Added support for S3 variables - #3592
- Added rollback function command - #3571
- Added `X-Amz-User-Agent` to list of allowed headers in CORS - #3614
- Added support for HTTP_PROXY API Gateway integration - #3534
- Added IS_LOCAL environment variable with invoke local command - #3642
- Removed package.json in exclude rules - #3644

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.13.2...v1.14.0)

# 1.13.2 (2017-05-15)

- Fixed a bug when using dot notation in YAML keys (#3620)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.13.1...v1.13.2)

# 1.13.1 (2017-05-12)

- Fixed bug when referencing variables from other variable object values (#3604)
- Fixed bug when packaging a functions-free service (#3598)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.13.0...v1.13.1)

# 1.13.0 (2017-05-10)

- Added support for cross service communication via CloudFormation outputs (#3575)
- Add Lambda tagging functionality (#3548)
- Added support for Promises in the variable system (#3554)
- Added hello-world template (#3445)
- Improved Info plugins lifecylce events for plugin authors (#3507)
- Allow service to be specified as object in serverless.yml (#3521)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.12.0...v1.13.0)

# 1.12.1 (2017-04-27)

- Fix bug when using the package command with the variable system (#3527)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.12.0...v1.12.1)

# 1.12.0 (2017-04-26)

- Separated packaging and deployment with a new package command (#3344)
- Extend OpenWhisk runtime support (#3454)
- Upgrade gradle wrapper to 3.5 (#3466)
- Fixed bug when using event streams with custom roles (#3457)
- Fixed bug with SNS events (#3443)
- Fixed bug when using custom deployment bucket (#3479)
- Added support for Python 3.6 for Lambda (#3483)
- Added new syntax to specify ARN for SNS events (#3505)

# 1.11.0 (2017-04-12)

- Add CloudWatch Logs Event Source (#3407)
- Add version description from function (#3429)
- Add support for packaging functions individually (#3433)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.10.2...v1.11.0)

# 1.10.2 (3.04.2017)

- Add support for packaging functions individually at the function level (#3433)

# 1.10.1 (2017-03-30)

- Update serverless-alpha detection (#3423)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.10.0...v1.10.1)

# 1.10.0 (2017-03-29)

- Fixed bug with ANY http method (#3304)
- Reduced unit test time significantly (#3359)
- Added AWS Groovy Gradle Template (#3353)
- Reduce dependency tree depth between IAM & Log Groups (#3360)
- Added entrypoints for plugins (#3327)
- Removed pre-install script (#3385)
- Expose plugin hooks (#2985)
- Add support for Node 6 runtime in invoke local (#3403)
- Updated Node.js templates to include Node 6 runtime by default (#3406)
- Removed breaking changes warnings (#3418)
- Auto loading serverless-alpha plugin (#3373)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.9.0...v1.10.0)

# 1.9.0 (2017-03-14)

- Fixed bug with serverless plugins lookup (#3180)
- Fixed bug with `serverless create` generated .gitignore (#3355)
- Fixed bug with authorizer claims (#3187)
- Added support for CloudFormation service roles (#3147)
- Improvements for invoke local plugin (#3037)
- Added Azure Functions Node.js template in `serverless create` (#3334)
- Allow DynamoDB and Kinesis streams to use GetAtt/ImportValue (#3111)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.8.0...v1.9.0)

# 1.8.0 (2017-02-28)

## Non-Breaking Changes

- Fixed bug with deployment progress monitoring (#3297)
- Fixed "too many open files" error (#3310)
- Fixed bug with functions lists loaded from a separate file using Serverless Variables (#3186)

## Breaking Changes

#### Removed IamPolicyLambdaExecution Resource

We've removed the `IamPolicyLambdaExecution` resource template and replaced it with inline policy within the role as it's been causing issues with VPC and bloating the CF template. This is a breaking change only for users who are depending on that resource with `Ref` or similar CF intrinsic functions.

#### Changed displayed function name for `sls info`

The function name displayed when you run `sls info` is now the short function name as found in `serverless.yml` rather than the actual lambda name to keep it more provider agnostic. This could be breaking for any user who is depending or parsing the CLI output.

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.7.0...v1.8.0)

# 1.7.0 (2017-02-14)

- Added CloudWatch event source (#3102)
- Fixed average functions duration calculation in "sls metrics" output (#3067)
- Added SLS_IGNORE_WARNINGS flag and logging upcoming breaking changes (#3217)
- Reduced memory consumption during zipping process (#3220)
- Fixed bug when using LogGroup resources with custom roles (#3213)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.6.1...v1.7.0)

# 1.6.1 (2017-01-31)

A minimal patch release that fixes an issue with rendering README.md on npm registry.

# 1.6.0 (2017-01-30)

**Important Note:** This release includes breaking changes. If your services stopped working after upgrading to v1.6.0, please read the following section.

## Breaking Changes

### CloudWatch logs are created explicitly

Up until this release, CloudWatch log groups were created implicitly by AWS/Lambda by default and were not included in your service stack. However, some users were able to easily reach the CloudWatch log group limits (currently at 500 log groups), and it wasn't an easy task to clear them all. Because of that we decided to explicitly create the log groups using CloudFormation so that you can easily remove them with `sls remove`. This was also optionally possible with the `cfLogs: true` config option.

If your service doesn't have the `cfLogs: true` set, and one of the function has been invoked at least once (hence the log groups were created implicitly by AWS), then it's very likely that you'll receive a "log group already exists" error after upgrading to v1.6.0. That's because CF is now trying to create the already created log groups from scratch to include it in the stack resources. **To fix this breaking change,** simply delete the old log group, or rename your service if you **must** keep the old logs.

### Removed function Arns from CloudFormation outputs

Up until this release, the output section of the generated CloudFormation template included an output resource for each function Arn. This caused deploying big services to fail because users were hitting the 60 outputs per stack limit. This effectively means that you can't have a service that has more than 60 functions. To avoid this AWS limit, we decided to remove those function output resources completely, to keep the stack clean. This also means removing the function Arns from the `sls info` command, and at the end of the deployment command.

This is a breaking change for your project if you're depending on those function output resources in anyway, or if you're depending on function arn outputs from the deploy or info commands. Otherwise, your project shouldn't be affected by this change. Fixing this issue depends on your needs, but just remember that you can always create your own CF outputs in `serverless.yml`.

### Moved `getStackName()` method

This is a breaking change for plugin authors only. If your plugin used the `provider.getStackName()` method, it has been moved to `naming.js`, and should be referenced with `provider.naming.getStackName()` instead.

### Removed the `defaults` property from `serverless.yml`

We've finally dropped support for the `defaults` property which we introduced in v1. All child properties should now be moved to the `provider` object instead.

## Non-breaking changes

- Reduce memory consumption on deploy by at least 50% (#3145)
- Added openwhisk template to `sls create` command (#3122)
- Allow Role 'Fn::GetAtt' for Lambda `role` (#3083)
- Added Access-Control-Allow-Credentials for CORS settings (#2736)
- add Support for SNS Subscription to existing topics (#2796)
- Function version resources are now optional. (#3042)
- Invoke local now supports python runtime. (#2937)
- Fixed "deployment bucket doesn't exist" error (#3107)
- Allowed function events value to be variables (#2434)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.5.1...v1.6.0)

# 1.5.1 (2017-01-19)

## Bug Fixes

- Fix bug with multi line values is given in IoT events (#3095)
- Add support of numeric template creation path (#3064)
- Fix deployment bucket bug when using eu-west-1 (#3107)

## Meta

- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.5.0...v1.5.1)

# 1.5.0 (2017-01-05)

## Features

- [Added IoT event source support](https://github.com/serverless/serverless/blob/master/docs/providers/aws/events/iot.md) (#2954)
- [Cognito user pool authorizer](https://serverless.com/framework/docs/providers/aws/events/apigateway/#http-endpoints-with-custom-authorizers) (#2141)
- Service installation with a name (#2616)

## Bug Fixes

- Fix VTL string escaping (#2993)
- Scheduled events are enabled by default (#2940)
- Update status code regex to match newlines (#2991)
- Add check for preexistent service directory (#3014)
- Deployment monitoring fixes (#2906)
- Credential handling fixes (#2820)
- Reduced policy statement size significantly (#2952)

## Meta

- [Github Milestone](https://github.com/serverless/serverless/milestone/20?closed=1)
- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.4.0...v1.5.0)

# 1.4.0 (2016-12-15)

## Features

- [Alexa event support](https://github.com/serverless/serverless/issues/2875) (#2875)
- [New C# service template](https://github.com/serverless/serverless/tree/master/docs/providers/aws/examples/hello-world/csharp) (#2858)
- [Local Invoke Improvements](https://github.com/serverless/serverless/pull/2865) (#2865)
- [Service wide metrics](https://github.com/serverless/serverless/blob/master/docs/providers/aws/cli-reference/metrics.md) (#2846)
- [Install service by pointing to a Github directory](https://github.com/serverless/serverless/issues/2721) (#2721)
- [Add support for stdin for invoke & invoke local](https://github.com/serverless/serverless/blob/master/docs/providers/aws/cli-reference/invoke.md#function-invocation-with-data-from-standard-input) (#2894)

## Bug Fixes

- Fixed exit code for failed function invocations (#2836)
- Stricter validation for custom IAM statements (#2132)
- Fixed bug in credentials setup (#2878)
- Removed unnecessary warnings during Serverless installation (#2811)
- Removed request and response config when using proxy integration (#2799)
- Internal refactoring

## Meta

- [Github Milestone](https://github.com/serverless/serverless/milestone/18?closed=1)
- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.3.0...v1.4.0)

# 1.3.0 (2016-12-02)

## Features

- [Metrics support](https://serverless.com/framework/docs/providers/aws/cli-reference/metrics/) (#1650)
- [AWS credential setup command](https://serverless.com/framework/docs/providers/aws/cli-reference/config/) (#2623)
- Lambda versioning on each deploy (#2676)

## Improvements

- Documentation improvements with `serverless.yml` file reference (#2703)
- Display info how to use SLS_DEBUG (#2690)
- Drop `event.json` file on service creation (#2786)
- Refactored test structure (#2464)
- Automatic test detection (#1337)

## Bug Fixes

- Add DependsOn for Lamda functions and IamPolicyLambdaExecution (#2743)
- Add JSON data parsing for invoke command (#2685)
- Internal refactoring

## Meta

- [Github Milestone](https://github.com/serverless/serverless/milestone/17?closed=1)
- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.2.1...v1.3.0)

# 1.2.0 (2016-11-22)

## Features

- [Lambda environment variables support](https://serverless.com/framework/docs/providers/aws/guide/functions#environment-variables) (#2748)
- [Load Serverless variables from javascript files](https://serverless.com/framework/docs/providers/aws/guide/variables#reference-variables-in-javascript-files) (#2495)
- [Add support for setting custom IAM roles for functions](https://serverless.com/framework/docs/providers/aws/guide/iam#custom-iam-roles-for-each-function) (#1807)
- Lambda environment variables support in Invoke Local (#2757)
- Tighter and secure permissions for event sources (#2023)

## Bug Fixes

- Fix `--noDeploy` flag to generate deployment files offline without needing internet connection (#2648)
- Bring back the `include` packaging feature with the help of globs (#2460)
- Internal refactoring

## Meta

- [Github Milestone](https://github.com/serverless/serverless/milestone/16?closed=1)
- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.1.0...v1.2.0)

# 1.1.0 (2016-11-02)

## Future breaking changes

We will include the LogGroup for your Lambda function in the CloudFormation template in the future. This will break deployments to existing applications because the log group was already created. You will get a warning about this if you deploy currently. We will force this behaviour in a future release, for now you can set it through the `cfLogs: true` parameter in your provider config. This change will also limit the logging rights to only this LogGroup, which should have no impact on your environment. You can read more in [our docs](https://serverless.com/framework/docs/providers/aws/guide/functions#log-group-resources).

## Features

- [Rollback Support](https://serverless.com/framework/docs/providers/aws/cli-reference/rollback/) (#2495)
- [Log Groups in Cloudformation](https://serverless.com/framework/docs/providers/aws/guide/functions#log-group-resources) (#2520)
- [Allow Services without functions](https://github.com/serverless/serverless/pull/2499) (#2499)
- [Clean up S3 Deployment bucket only after successful deployment](https://github.com/serverless/serverless/pull/2564) (#2564)
- [Allow Inclusion after Exclusion using ! Globs](https://serverless.com/framework/docs/providers/aws/guide/packaging/) (#2266)
- [Version Pinning for Serverless Services to only deploy with specified versions](https://serverless.com/framework/docs/providers/aws/guide/version/) (#2505)
- [Invoke local plugin](https://serverless.com/framework/docs/providers/aws/cli-reference/invoke/) (#2533)
- [Plugin template](https://serverless.com/framework/docs/providers/aws/cli-reference/create/) (#2581)
- [Simple Plugins are now installable in subfolder of the service](https://serverless.com/framework/docs/providers/aws/guide/plugins#service-local-plugin) (#2581)

## Bugs

- Fix variable syntax fallback if the file doesn't exist (#2565)
- Fix overwriting undefined variables (#2541)
- Fix CF deployment issue (#2576)
- Correctly package symlinks (#2266)

## Other

- [Large documentation refactoring](https://serverless.com/framework/docs/) (#2527)

## Meta

- [Github Milestone](https://github.com/serverless/serverless/milestone/15)
- [Comparison since last release](https://github.com/serverless/serverless/compare/v1.0.3...v1.1.0)

# 1.0.3 (2016-10-21)

Following is a selection of features, bug fixes and other changes we did since 1.0.2.
You can also check out all changes in the [Github Compare View](https://github.com/serverless/serverless/compare/v1.0.2...v1.0.3)

## Features

- [Stack Tags and Policy](https://serverless.com/framework/docs/providers/aws/) (#2158)
- [CF Stack Output Variables in Verbose deploy output](https://serverless.com/framework/docs/cli-reference/deploy/) (#2253)
- [Custom Status code for non-proxy APIG integration](https://serverless.com/framework/docs/providers/aws/events/apigateway/) (#2014)
- [Function Runtime can now be configured per function](https://serverless.com/framework/docs/providers/aws/) (#2425)
- [Allow absolute path for invoke command event file](https://serverless.com/framework/docs/cli-reference/invoke/) (#2443)
- [Add list deployments command to show last deployments stored in S3 bucket](https://serverless.com/framework/docs/cli-reference/deploy/) (#2439)

## Bugs

- Fix not thrown error after failed ResourceStatus bug (#2367)
- Fix overwrite resources and custom resource merge bug (#2385)
- Clean up after deployment works correctly now (#2436)

## Other

- Migrate Integration tests into main repository (#2438)

# 1.0.2 (2016-10-13)

- Clean up NPM package (#2352)
- Clean up Stats functionality (#2345)

# 1.0.1 (2016-10-12)

Accidentally released 1.0.1 to NPM, so we have to skip this version (added here to remove confusion)

# 1.0.0 (2016-10-12)

## Breaking Changes

- The HTTP Event now uses the [recently released Lambda Proxy](http://docs.aws.amazon.com/apigateway/latest/developerguide/api-gateway-set-up-simple-proxy.html#api-gateway-proxy-integration-types) by default. This requires you to change your handler result to fit the new proxy integration. You can also switch back to the old integration type.
- The Cloudformation Name of APIG paths that have a variable have changed, so if you have a variable in a path and redeploy CF will throw an error. To fix this remove the path and readd it a second deployment.

## Release Highlights

Following is a selection of the most important Features of the 1.0.0 since 1.0.0-rc.1.

You can see all features of 1.0.0-rc.1 in the [release blogpost](https://serverless.com/blog/serverless-v1-0-rc-1/)

### Documentation

- New documentation website https://serverless.com/framework/docs

### Events

- API Gateway Improvements
  - [Supporting API Gateway Lambda Proxy](https://serverless.com/framework/docs/providers/aws/events/apigateway/) (#2185)
  - [Support HTTP request parameters](https://serverless.com/framework/docs/providers/aws/events/apigateway/) (#2056)
- [S3 Event Rules](https://serverless.com/framework/docs/providers/aws/events/s3/) (#2068)
- [Built-in Stream Event support (Dynamo & Kinesis)](https://serverless.com/framework/docs/providers/aws/events/streams/) (#2250)

### Other

- [Configurable deployment bucket outside of CF stack](https://github.com/serverless/serverless/pull/2189) (#2189)
- [Install command to get services from Github](https://serverless.com/framework/docs/cli-reference/install/) (#2161)
- [Extended AWS credentials support](https://serverless.com/framework/docs/providers/aws/setup/) (#2229)
- [Extended the Serverless integration test suite](https://github.com/serverless/integration-test-suite)
