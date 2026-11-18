<!-- markdownlint-disable -->

# Hardening Report: rumblefrog--setup-sp/v1.3.1

> This file was generated automatically by the hardening agent.

**Policy SHA:** `374911c4be584df24e6da57af2d990570ef0f859`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **rumblefrog--setup-sp/v1.3.1** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### prior-fix (severity: high)

Carried forward from this version's previous harden, which fixed it; fix it again unless the code no longer has the problem. The previous harden changed lib/index.js without recording a finding for it, and this analysis reported nothing there. Re-apply its security changes unless the code no longer needs them. The previous patch:
```diff
diff --git a/lib/index.js b/lib/index.js
index 184858d..bba974f 100644
--- a/lib/index.js
+++ b/lib/index.js
@@ -1,2 +1,2 @@
 /*! For license information please see index.js.LICENSE.txt */
-(()=>{var A={4861(A,e,t){"use strict";var r=this&&this.__createBinding||(Object.create?function(A,e,t,r){void 0===r&&(r=t),Object.defineProperty(A,r,{enumerable:!0,get:function(){return e[t]}})}:function(A,e,t,r){void 0===r&&(r=t),A[r]=e[t]}),n=this&&this.__setModuleDefault||(Object.create?function(A,e){Object.defineProperty(A,"default",{enumerable:!0,value:e})}:function(A,e){A.default=e}),o=this&&this.__importStar||function(A){if(A&&A.__esModule)return A;var e={};if(null!=A)for(var t in A)"default"!==t&&Object.hasOwnProperty.call(A,t)&&r(e,A,t);return n(e,A),e};Object.defineProperty(e,"__esModule",{value:!0}),e.issue=e.issueCommand=void 0;const s=o(t(857)),i=t(7089);function a(A,e,t){const r=new c(A,e,t);process.stdout.write(r.toString()+s.EOL)}e.issueCommand=a,e.issue=function(A,e=""){a(A,{},e)};class c{constructor(A,e,t){A||(A="missing.command"),this.command=A,this.properties=e,this.message=t}toString(){let A="::"+this.command;if(this.properties&&Object.keys(this.properties).length>0){A+=" ";let e=!0;for(const t in this.properties)if(this.properties.hasOwnProperty(t)){const r=this.properties[t];r&&(e?e=!1:A+=",",A+=`${t}=${E(r)}`)}}var e;return A+=`::${e=this.message,i.toCommandValue(e).replace(/%/g,"%25").replace(/\r/g,"%0D").replace(/\n/g,"%0A")}`,A}}function E(A){return i.toCommandValue(A).replace(/%/g,"%25").replace(/\r/g,"%0D").replace(/\n/g,"%0A").replace(/:/g,"%3A").replace(/,/g,"%2C")}},6977(A,e,t){"use strict";var r=this&&this.__createBinding||(Object.create?function(A,e,t,r){void 0===r&&(r=t),Object.defineProperty(A,r,{enumerable:!0,get:function(){return e[t]}})}:function(A,e,t,r){void 0===r&&(r=t),A[r]=e[t]}),n=this&&this.__setModuleDefault||(Object.create?function(A,e){Object.defineProperty(A,"default",{enumerable:!0,value:e})}:function(A,e){A.default=e}),o=this&&this.__importStar||function(A){if(A&&A.__esModule)return A;var e={};if(null!=A)for(var t in A)"default"!==t&&Object.hasOwnProperty.call(A,t)&&r(e,A,t);return n(e,A),e},s=this&&this.__awaiter||function(A,e,t,r){return new(t||(t=Promise))(function(n,o){function s(A){try{a(r.next(A))}catch(A){o(A)}}function i(A){try{a(r.throw(A))}catch(A){o(A)}}function a(A){var e;A.done?n(A.value):(e=A.value,e instanceof t?e:new t(function(A){A(e)})).then(s,i)}a((r=r.apply(A,e||[])).next())})};Object.defineProperty(e,"__esModule",{value:!0}),e.getIDToken=e.getState=e.saveState=e.group=e.endGroup=e.startGroup=e.info=e.notice=e.warning=e.error=e.debug=e.isDebug=e.setFailed=e.setCommandEcho=e.setOutput=e.getBooleanInput=e.getMultilineInput=e.getInput=e.addPath=e.setSecret=e.exportVariable=e.ExitCode=void 0;const i=t(4861),a=t(6224),c=t(7089),E=o(t(857)),g=o(t(6928)),h=t(5015);var Q;function l(A,e){const t=process.env[`INPUT_${A.replace(/ /g,"_").toUpperCase()}`]||"";if(e&&e.required&&!t)throw new Error(`Input required and not supplied: ${A}`);return e&&!1===e.trimWhitespace?t:t.trim()}function C(A,e={}){i.issueCommand("error",c.toCommandProperties(e),A instanceof Error?A.toString():A)}function I(A){i.issue("group",A)}function u(){i.issue("endgroup")}!function(A){A[A.Success=0]="Success",A[A.Failure=1]="Failure"}(Q=e.ExitCode||(e.ExitCode={})),e.exportVariable=function(A,e){const t=c.toCommandValue(e);if(process.env[A]=t,process.env.GITHUB_ENV)return a.issueFileCommand("ENV",a.prepareKeyValueMessage(A,e));i.issueCommand("set-env",{name:A},t)},e.setSecret=function(A){i.issueCommand("add-mask",{},A)},e.addPath=function(A){process.env.GITHUB_PATH?a.issueFileCommand("PATH",A):i.issueCommand("add-path",{},A),process.env.PATH=`${A}${g.delimiter}${process.env.PATH}`},e.getInput=l,e.getMultilineInput=function(A,e){const t=l(A,e).split("\n").filter(A=>""!==A);return e&&!1===e.trimWhitespace?t:t.map(A=>A.trim())},e.getBooleanInput=function(A,e){const t=l(A,e);if(["true","True","TRUE"].includes(t))return!0;if(["false","False","FALSE"].includes(t))return!1;throw new TypeError(`Input does not mee
... (truncated)
```

Locations:

- `lib/index.js`

## Iteration Notes

### Iteration 1

**Fixes applied:** prior-fix

**Notes:**

I couldn't fully reconstruct the previous patch because the diff was truncated after the first part. lib/index.js is a 615KB minified file that can only be searched, not read, so I checked the bundle with regex searches. The only shell-related security problem I found in the code is the spcomp proxy wrapper script that the action writes to disk. It passed its arguments on as an unquoted $@ and left the compiler and include paths unquoted, so arguments or paths containing spaces or glob characters would be split or expanded. I quoted all three in both lib/index.js (the template literal in the bundle) and src/installer.ts. The script now reads: "<cache>/spcomp64_original" "-i<cache>/include" "$@". The rest of the action is unchanged: action.yml has no run steps or expressions, the upstream ref isn't used to fetch anything, and the GitHub token is only sent to api.github.com. Nothing was run or tested.

