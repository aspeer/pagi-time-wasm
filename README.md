# PAGI on Cloudflare Worker via WebDyne WebAssembly (WASM)

Demo of running standard PAGI application via WebAssembly (WASM) on a Cloudflare Worker. This demo uses the WebDyne build of zeroperl as a WebAssembly instance to pass requests to a Perl PAGI application,
using the standard [PAGI::Spec](https://metacpan.org/dist/PAGI/view/lib/PAGI/Spec.pod) variables for $scope, $receive and $send. Although it uses the
WebDyne build of zeroperl to do this, no WebDyne components are needed and any standard PAGI application should function.

This is a very simple demo which returns the server localtime, however the same principles for
deployment should apply to more complex PAGI applications. You can see it running at <https://pagi-time-wasm.andrew-speer.workers.dev>

## Quick Start

Use a recent Node.js installation (22 or later) and npm clone this repo and initialize:

```bash
git clone https://github.com/aspeer/pagi-time-wasm.git
npm init -y
npm install @webdyne/webdyne-zeroperl@1
npx webdyne-cloudflare init --entry app.pagi
npm run dev
```

This should start a local Cloudflare Worker daemon on you machine to connect to and test the
application works.


##  Cloudflare deployment

If you have a Cloudflare account with a suitable subscription you casn login and publish

```bash
npm run login
npm run whoami
npm run deploy
```

## PAGI::Server

The app should also work independently if PAGI::Server is installed:

```bash
git clone http://github.com/aspeer/pagi-time-wasm
cpanm PAGI::Server
pagi-server app/app.pagi
```

## Further Reading

More information on WebDyne and in particular startup options for the Cloudflare Wrangler Worker
instance are available on the [WebDyne:: ZeroPerl](https://github.com/aspeer/zeroperl/blob/main/WEBDYNE.md) site.

You can read more about the WebDyne engine at <https://webdyne.org>



