
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Discord Test Client</title>
<link rel="stylesheet" href="/assets/fosscord.css" />
<link id="logincss" rel="stylesheet" href="/assets/fosscord-login.css" />
<link id="customcss" rel="stylesheet" href="/assets/user.css" />
<script>// Auto register guest account:
const prefix = [
	"mysterious",
	"adventurous",
	"courageous",
	"precious",
	"cynical",
	"flamer ",
	"despicable",
	"suspicious",
	"gorgeous",
	"impeccable",
	"lovely",
	"stunning",
	"keyed",
	"phoned",
	"glorious",
	"amazing",
	"strange",
	"arcane"
];
const suffix = [
	"Anonymous",
	"Boy",
	"Lurker",
	"Keyhitter",
	"User",
	"Enjoyer",
	"Hunk",
	"Coolstar",
	"Wrestling",
	"TylerTheCreator",
	"Ad",
	"Gamer",
	"Games",
	"Programmer"
];

Array.prototype.random = function () {
	return this[Math.floor(Math.random() * this.length)];
};

function _generateName() {
	return `${prefix.random()}${suffix.random()}`;
}

var token = JSON.parse(localStorage.getItem("token"));
if (!token && location.pathname !== "/login" && location.pathname !== "/register") {
	fetch(`${window.GLOBAL_ENV.API_ENDPOINT}/auth/register`, {
		method: "POST",
		headers: { "content-type": "application/json" },
		body: JSON.stringify({ username: `${_generateName()}`, consent: true }) //${Date.now().toString().slice(-4)}
	})
		.then((x) => x.json())
		.then((x) => {
			localStorage.setItem("token", `"${x.token}"`);
			if (!window.localStorage) {
				// client already loaded -> need to reload to apply the newly registered user token
				location.reload();
			}
		});
}
</script>
<script async src='/cdn-cgi/challenge-platform/h/g/scripts/invisible.js?ts=1649617200'></script></head>
<body>
<div id="app-mount"></div>
<script>
			window.__OVERLAY__ = /overlay/.test(location.pathname);
			window.__BILLING_STANDALONE__ = /^\/billing/.test(location.pathname);
			window.GLOBAL_ENV = {
				API_ENDPOINT: "/api",
				API_VERSION: 9,
				GATEWAY_ENDPOINT: `${location.protocol === "https:" ? "wss://" : "ws://"}${location.host}`,
				WEBAPP_ENDPOINT: "",
				CDN_HOST: `${location.host}`,
				ASSET_ENDPOINT: "",
				MEDIA_PROXY_ENDPOINT: "https://media.discordapp.net",
				WIDGET_ENDPOINT: `//${location.host}/widget`,
				INVITE_HOST: `${location.host}/invite`,
				GUILD_TEMPLATE_HOST: "discord.new",
				GIFT_CODE_HOST: "discord.gift",
				RELEASE_CHANNEL: "stable",
				MARKETING_ENDPOINT: "//discord.com",
				BRAINTREE_KEY: "production_5st77rrc_49pp2rp4phym7387",
				STRIPE_KEY: "pk_live_CUQtlpQUF0vufWpnpUmQvcdi",
				NETWORKING_ENDPOINT: "//router.discordapp.net",
				RTC_LATENCY_ENDPOINT: "//latency.discord.media/rtc",
				PROJECT_ENV: "production",
				REMOTE_AUTH_ENDPOINT: "//localhost:3020",
				SENTRY_TAGS: { buildId: "75e36d9", buildType: "normal" },
				MIGRATION_SOURCE_ORIGIN: "https://discordapp.com",
				MIGRATION_DESTINATION_ORIGIN: "https://discord.com",
				HTML_TIMESTAMP: Date.now(),
				ALGOLIA_KEY: "aca0d7082e4e63af5ba5917d5e96bed0"
			};
			GLOBAL_ENV.MEDIA_PROXY_ENDPOINT = location.protocol + "//" + GLOBAL_ENV.CDN_HOST;
			const localStorage = window.localStorage;
			// TODO: remote auth
			// window.GLOBAL_ENV.REMOTE_AUTH_ENDPOINT = window.GLOBAL_ENV.GATEWAY_ENDPOINT.replace(/wss?:/, "");
			localStorage.setItem("gatewayURL", window.GLOBAL_ENV.GATEWAY_ENDPOINT);
			localStorage.setItem(
				"DeveloperOptionsStore",
				`{"trace":false,"canary":false,"logGatewayEvents":true,"logOverlayEvents":true,"logAnalyticsEvents":true,"sourceMapsEnabled":false,"axeEnabled":false}`
			);

			setInterval(() => {
				var token = JSON.parse(localStorage.getItem("token"));
				if (token) {
					document.querySelector("#logincss").remove();
				}
			}, 1000);

			const settings = JSON.parse(localStorage.getItem("UserSettingsStore"));
			if (settings && settings.locale.length <= 2) {
				// fix client locale wrong and client not loading at all
				settings.locale = "en-US";
				localStorage.setItem("UserSettingsStore", JSON.stringify(settings));
			}
		</script>
<script src="/assets/checkLocale.js"></script>
<script src="/assets/479a2f1e7d625dc134b9.js"></script>
<script src="/assets/a15fd133a1d2d77a2424.js"></script>
<script src="/assets/97e6fa22aa08ee4daa5e.js"></script>
<script src="/assets/9b2b7f0632acd0c5e781.js"></script>
<script type="text/javascript">(function(){window['__CF$cv$params']={r:'6f9e0fa15f4d106c',m:'eP4byqfqWvCDx1N1_SZxtDFYX0XF4USXV1J2zcP.ZiA-1649620746-0-AWsQaoExnZf8HoHO8nxmhC7WoaXL2UdIgHn8/y8iVn48S6HFBQCMmmTSMg8xAFQxgHTxOQ0hgVQylFkP2YAAEOeYdVSbZogoojS1GXDp+w6XkFCLn0nu6pSg8MKARxPq4A==',s:[0x10a2887fec,0xa31c966479],u:'/cdn-cgi/challenge-platform/h/g'}})();</script></body>
</html>
