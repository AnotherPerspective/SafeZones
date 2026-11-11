<a id="english"></a>

# Safe Zones by Another Perspective Pictures — v4.2 (October 2026)

**English** · [Italiano](#italiano)

> **v4.2**: new graphics inside the plugin. Icons, text in real fonts, gradients, shadows, border and the "Powered by" line are drawn by the DCTL as vectors, sharp at any resolution. Measurements and controls are the same as v4.0. The package no longer contains PNG images.

Overlays for vertical 9:16 video in DaVinci Resolve. For installation see **INSTALL.txt**. SafeZones is free and experimental and comes without any warranty: read **AVVERTENZE.md** (English and Italian) in the main folder.

## DCTL controls
Inside Resolve the controls still have Italian names: here they are with their English meaning.
- **Piattaforma** (Platform): TikTok (feed and full screen), Instagram Reels / Stories, Facebook Reels / Stories, YouTube Shorts, LinkedIn (9:16 and 4:5), Snapchat Spotlight / from profile / Stories, Pinterest (9:16 and 1:2 pins). Plus *Tutte le piattaforme* (all platforms: the outlines on top of each other) and *Area comune feed verticali* (common area of vertical feeds: the area that works everywhere).
- **Modalita** (Mode):
  - *Safe area organica* (organic safe area): the area the interface does not cover, for normal posts.
  - *Safe area ads ufficiale* (official ads safe area): the margins the platforms state for ads. They are more cautious.
  - *Mockup interfaccia* (interface mockup): icons, names, caption, counters and app bars, drawn by the plugin.
  - *Mockup e safe area*: both together.
- **Telefono** (Phone): *Telefono moderno* (modern phone: iPhone X and later, recent Android, 19.5:9 screens and taller) or *Telefono 16:9* (iPhone SE / 8 and older Android). It does not change the video format, which stays 1080×1920: it shows how much interface falls on the video on that kind of screen. On 16:9 screens the app bar sits over the video and the whole bottom block moves up, so on TikTok, Instagram Reels and Stories, YouTube Shorts and Snapchat Spotlight the safe area gets smaller (see the table below).
- **Elementi occasionali** (Occasional elements): widens the safe area to also cover things that appear only sometimes: the mute button of Facebook Stories (top 178 → 321) and the friends-activity bubble of Instagram Reels (bottom 345 → 443). Off by default: those elements are still drawn in the mockup but do not penalise the whole band.
- **Safezone**: how much to darken the unsafe area (0 = none).
- **Mockup**: opacity of the interface mockup.
- **Margin px**: how much breathing room to leave between the app graphics and the edge of the safe area. 16 px by default, which gives the values written below; raising it shrinks the safe area by the same amount (sides included), lowering it brings it flush with the icons. It does not affect ads mode, which uses the official margins.
- **Border**: thickness in px of the outline.
- **Crop griglia profilo 3x4** (3x4 profile grid crop), **Crop feed 4x5** (4x5 feed crop), **Croce centrale** (centre cross): extra guides.
- **Correggi se capovolto** (fix if upside down): use it only if the overlay comes out flipped vertically.
- **Powered by Another Perspective Pictures**: the line at the bottom, can be switched off.

## Why v1 was too pessimistic
Online guides mix two different measurements:
1. the official **ads** margins. For example Meta says to leave the bottom 35% free = 672 px, because that is where the CTA button of a sponsored post appears;
2. the real space taken by the **organic** interface on a modern phone, which at the bottom is about 290–380 px.

**Where the numbers come from**: all measurements are taken from real screenshots of an **iPhone 13 Pro** (1170×2532, 19.5:9 screen), in September 2026. So they are real-world values, not official specifications. On Android, on iPhone Max models and especially on tablets the screen proportions change and the interface is laid out differently: use these values as a solid reference for the most common vertical format.

Since v2 the organic safe area is **not estimated by eye**: the generator calculates it from the position of every element of the mockup, plus the breathing room set with **Margin** (16 px by default). This is why safe area and mockup always match.

## Which phones these numbers apply to
The reference is an iPhone 13 Pro (19.5:9). Comparing the proportions of other devices:

| Device | Screen format | Difference from the reference |
|---|---|---|
| iPhone 15 / 16, Pro Max | 19.5:9 | practically identical (within ~10 px); on Max models the margins are actually smaller |
| Android 20:9 (the most common) | 20:9 | ~60 px **more** free space under the video; on full-screen apps the margins grow by about 5% |
| Sony and similar 21:9 | 21:9 | ~180 px more free space: safer |
| Open foldables, tablets | from 4:3 to 1:1 | the video is shown whole with bars: safer |
| iPhone SE, older Android | 16:9 | the interface falls entirely on the video: it covers more |

Among tall phones the most restrictive is exactly the one used for the measurements, and anything taller or bigger is more permissive: that is why there is a single *Telefono moderno* (modern phone) option. 16:9 screens are the only really different case: since v4.0 you choose them from the **Telefono** (Phone) menu.

## Export format: always 1080×1920
You upload one file and every phone sees it: the apps adapt it to the screen. We checked this with a **1080×2400** calibration video (a ruler every 20 px) posted as a Reel on an iPhone 13 Pro, on 22/09/2026:
- Instagram showed **only rows 240–2160**, that is the central 9:16: the 240 rows above and the 240 below disappeared. The extra height is thrown away.
- Those 1920 rows fill the screen from y 0 to y 2283 (enlarged 1.19 times) and **about 48 px are lost on each side**.

So always export **1080×1920**: a taller video does not show more, it only loses what is at the top and bottom. On tall phones, full-screen apps crop the sides of your 1080×1920 a little; the plugin takes this into account in the side margins:

| App (iPhone 13 Pro) | Video area on screen | Crop on each side of the 1080×1920 | Safe-area sides (crop + 16) |
|---|---|---|---|
| Instagram Reels | y 0–2283 (under status bar and header) | ~48 px (measured with the test) | 64 |
| TikTok full screen | y 0–2283 | ~48 px | 64 |
| YouTube Shorts | y 0–2286 | ~49 px | 65 |
| Facebook Reels | y 0–2297 | ~51 px | 67 |
| Snapchat Spotlight | y 0–2220 | ~34 px | 56 / 50 |
| TikTok (feed) | y 141–2283 | ~16 px | 50 / 40 |
| IG / FB Stories, Snapchat Stories, LinkedIn, Pinterest | card or video shown whole | 0 | 40 |

## 16:9 phone: how the values change
| Platform | Modern phone: bottom / column | 16:9 phone: bottom / column |
|---|---|---|
| TikTok | 286 / from y 833 | 436 / from y 683 |
| Instagram Reels | 345 / from y 961 | 554 / from y 752 |
| Instagram Stories | 40 | 164 (the reply field falls on the video) |
| YouTube Shorts | 394 / from y 1015 | 534 / from y 875 |
| Snapchat Spotlight | 356 / from y 764 | 506 / from y 614 |
| TikTok full screen | 269 / from y 899 | 419 / from y 749 |

The other platforms do not change. The 16:9 values are obtained by moving the interface anchored to the bottom of the screen: *medium* reliability.

## Values (px on 1080×1920) — tall phone (19.5:9 and taller)
| Platform | Top | Bottom | Left/right sides | Right icon column | Official ads T/B/L/R | Reliability |
|---|---|---|---|---|---|---|
| TikTok | 131 | 286 | 50/40 | 174 px from y 833 | 240/660/120/120 (+300 right below the middle) | **high (measured on screenshots)** |
| Instagram Reels | 227 with the "For you / Friends" header | 345 with the "Followed by" line | 64/64 | 191 px from y 961 | 269/672/65/65 | **high (7 screenshots, recalibrated with the v4.0 calibration test)** |
| Instagram Stories | 152 (with the music / "Watch Full Reel" line under the name) | 40 (message field under the video) | 40/40 | — | 269/384/65/65 | **high (measured on 4 screenshots)** |
| Facebook Reels | 231 | 216 | 67/67 | 181 px from y 977 | 269/672/65/65 | **high (measured on 4 screenshots)** |
| Facebook Stories | 178 (the mute button, only with music, takes the top-left corner down to y 306) | 40 (message field under the video) | 40/40 | — | 269/384/65/65 | **high (measured on 5 screenshots)** |
| YouTube Shorts | 226 (search and menu top right) | 394 with "Buy Super Thanks" + linked video (297 linked video only, 301 Super Thanks only, 202 without) | 65/65 | 194 px from y 1015 | 192/480/0/108 | **high (measured on 6 screenshots)** |
| LinkedIn | 40 (no UI on the video: the back arrow is above it) | 288 with the job title under the name (275 without) | 40/40 | 141 px from y 1024 | no official spec | **high (measured on 2 screenshots)** |
| LinkedIn 4:5 (1080×1350 timeline) | 40 | 40 (name and caption are under the video) | 40/40 | 141 px from y 732 | no official spec | **high (measured on 2 screenshots)** |
| TikTok full screen | 242 | 269 | 64/64 | 198 px from y 899 | 240/660/120/120 | medium (derived from TikTok + 1 screenshot of the dataset) |
| Pinterest 1:2 pin (1080×2160 timeline) | 163 | 168 | 40/40 | 162 px from y 2007 | 270/790/65/195 | **high (same interface as the 9:16 pin)** |
| Snapchat Spotlight | 259 | 356 (245 without comment preview) | 56/50 | 188 px from y 764 | 150/330 | **high (measured on 5 screenshots)** |
| Snapchat from profile | 40 | 282 (with comment preview; ~240 without) | 40/40 | 156 px from y 817 | 150/330 | **high (measured on 5 screenshots)** |
| Snapchat Snap/Story | 118 (top-right corner only) | 40 | 40/40 | — | 150/330 | **high (measured on screenshots)** |
| Pinterest | 163 (corners only: back and menu) | 168 (Remix button; without it, the "AI modified" label stops at 120) | 40/40 | 162 px from y 1767 (visual search) | 270/790/65/195 (official ads) | **high (measured on screenshots)** |

Notes:
- Snapchat Spotlight crops the video by about 34 px per side (already included). From the profile and in Stories the video sits in a card with rounded corners, without cropping; the reply button and "View Profile" are under the video.
- YouTube Shorts crops the video by about 58 px per side (already included); the app bar is under the video.
- Facebook Stories: with music, a line with the song appears under the name (already included) and an 84 px mute button at the top left (x 35–119, y 221–305), shown in the mockup but left out of the rectangle so as not to penalise the whole top band.
- Instagram Reels (new interface with floating app bar): **fixed in v4.0**. Up to v3.9 the video was assumed to be 82% of the screen tall (down to y 2080), with a blurred extension below. The calibration test showed instead that the 9:16 runs from y 0 to y 2283, enlarged 1.19 times and cropped ~48 px per side: name, Follow, caption and "Followed by…" are on the video. So the bottom margin goes from 189 to 345 and the sides from 40 to 64. As soon as you open the Reels tab there is the "For you / Friends" header at the top (down to y 238): the plugin includes it. The friends-activity bubble (bottom left, occasional) is in the mockup but not in the rectangle. The right column moves up about 70 px when there are comment and repost counts: the plugin uses that case. On a 16:9 phone (estimate) the whole interface moves up onto the video.
- LinkedIn (video opened full screen from the feed): the 9:16 video is shown whole, without cropping; back arrow and progress bar are outside the video. The right column and the name block move up one line when there is a job title under the name: the plugin uses that case.
- TikTok full screen: some videos start under the status bar instead of under the tabs. In that case the interface covers more at the top (242 instead of 131). The values come from the same interface projected onto the tighter framing and are confirmed by the dataset of 60 screenshots.
- Pinterest 1:2 pin: same interface as the 9:16 pin on a card twice as tall (1080×2160 timeline).
- LinkedIn 4:5: choose "LinkedIn 4:5" on a 1080×1350 timeline: the plugin uses a 4:5 frame (on timelines of other formats it centres it). Only the right column is on the video; its height depends on the phone (it is anchored to the bottom of the screen) and varies by ~35 px between videos: the plugin uses the highest case.
- Pinterest (open pin): like, comments, share and "Save" are under the video card, so only the corner buttons remain on the content. The official 790 px applies to ads.

**Real measurements:** TikTok, Facebook Reels and Stories, Pinterest and all Snapchat views (Spotlight, from profile, Snap/Story) were measured on iPhone screenshots (19/09/2026): the position of every icon, text and bar, checked by laying the mockup over the screenshot.

**Note:** the platforms do not publish the position of individual icons. All positions in this plugin come from real screenshots, measured one by one; to measure them again, one full-screen screenshot per app is enough.

## Contents
- `AnotherPerspective_SafeZones.dctl`: the plugin, with the "Powered by Another Perspective Pictures" line at the bottom (checkbox to switch it off).
- `INSTALL.txt`: where to copy the file and how to use it.
- `Anteprima_Safe_Zones.jpg`: all platforms at a glance.

## Main sources
- [Solid Labs – Social Safe Zones](https://www.solidlabs.com/social-safe-zones) (reports the official guidance of Meta, TikTok and Google)
- [Pinterest – Review Pin specs](https://help.pinterest.com/en/article/review-pin-specs)
- [TikTok Ads – In-Feed Ads](https://ads.tiktok.com/help/article/tiktok-auction-in-feed-ads)
- [Google – Shorts ads](https://business.google.com/us/ad-solutions/youtube-ads/shorts-ads/)
- [Snapchat – ads practices, via RecruitmentAds](https://recruitmentads.com/free-tools/ad-mockup/snapchat)
- [PostPlanify](https://postplanify.com/blog/social-media-safe-zones-2026-complete-guide), [AdChecklab](https://adchecklab.com/articles/tiktok-safe-zone-dimensions-2026), [AIcarousels LinkedIn](https://www.aicarousels.com/free-tools/linkedin-safe-zone-checker)

---

<a id="italiano"></a>

# Safe Zones by Another Perspective Pictures — v4.2 (ottobre 2026)

[English](#english) · **Italiano**

> **v4.2**: grafica nuova dentro il plugin: icone, scritte con i font veri, sfumature, ombre, bordo e scritta "Powered by" sono disegnati dal DCTL in vettoriale, nitidi a qualsiasi risoluzione. Misure e controlli sono quelli della v4.0. Il pacchetto non contiene piu' immagini PNG.

Overlay per video verticali 9:16 in DaVinci Resolve. Per l'installazione vedi **INSTALL.txt**. SafeZones è gratuito e sperimentale ed è fornito senza garanzie: leggi **AVVERTENZE.md** (in inglese e in italiano) nella cartella principale.

## Controlli del DCTL
- **Piattaforma**: TikTok (feed e schermo pieno), Instagram Reels / Stories, Facebook Reels / Stories, YouTube Shorts, LinkedIn (9:16 e 4:5), Snapchat Spotlight / da profilo / Stories, Pinterest (pin 9:16 e 1:2). In più *Tutte le piattaforme* (i contorni sovrapposti) e *Area comune feed verticali* (l'area che va bene ovunque).
- **Modalità**:
  - *Safe area organica*: l'area che l'interfaccia non copre, per i post normali.
  - *Safe area ads ufficiale*: i margini dichiarati dalle piattaforme per le inserzioni. Sono più prudenti.
  - *Mockup interfaccia*: icone, nomi, didascalia, contatori e barre dell'app, disegnati dal plugin.
  - *Mockup e safe area*: le due cose insieme.
- **Telefono**: *Telefono moderno* (iPhone X e successivi, Android recenti: schermi 19,5:9 e più alti) oppure *Telefono 16:9* (iPhone SE / 8 e Android vecchi). Non cambia il formato del video, che resta 1080×1920: mostra quanta interfaccia cade sul video su quel tipo di schermo. Sui 16:9 la barra dell'app finisce sopra il video e tutto il blocco in basso sale, quindi su TikTok, Instagram Reels e Stories, YouTube Shorts e Snapchat Spotlight la safe area si restringe (vedi la tabella più sotto).
- **Elementi occasionali**: allarga la safe area fino a coprire anche quello che compare solo a volte: il tasto muto delle storie Facebook (alto 178 → 321) e la bolla dell'attività amici di Instagram Reels (basso 345 → 443). Di base è spento: quegli elementi restano disegnati nel mockup ma non penalizzano tutta la fascia.
- **Safezone**: quanto scurire la zona non sicura (0 = niente).
- **Mockup**: opacità del mockup dell'interfaccia.
- **Margin**: quanto respiro lasciare fra le grafiche dell'app e il bordo della safe area. Di serie 16 px, cioè i valori scritti qui sotto; alzandolo la safe area si stringe di altrettanto (anche ai lati), abbassandolo arriva a filo delle icone. Non tocca la modalità ads, che usa i margini ufficiali.
- **Border**: spessore in px della linea di contorno.
- **Crop griglia profilo 3x4**, **Crop feed 4x5**, **Croce centrale**: guide aggiuntive.
- **Correggi se capovolto**: da usare solo se l'overlay esce specchiato in verticale.
- **Powered by Another Perspective Pictures**: la scritta in basso, disattivabile.

## Perché la v1 era troppo pessimista
Le guide online mescolano due misure diverse:
1. i margini **ads** ufficiali. Per esempio Meta indica di lasciare libero il 35% in basso = 672 px, perché lì compare il pulsante CTA della sponsorizzata;
2. l'ingombro reale dell'interfaccia **organica** su un telefono moderno, che in basso è di circa 290–380 px.

**Da dove vengono i numeri**: tutte le misure sono prese da screenshot reali di un **iPhone 13 Pro** (1170×2532, schermo 19.5:9), a settembre 2026. Sono quindi parametri del mondo reale, non specifiche ufficiali. Su Android, su iPhone Max e soprattutto su tablet le proporzioni dello schermo cambiano e l'interfaccia si dispone in modo diverso: usa questi valori come riferimento solido per il formato verticale più diffuso.

Nella v2 la safe area organica **non è stimata a occhio**: il generatore la calcola dalla posizione di ogni elemento del mockup, più il respiro impostato con **Margin** (16 px di serie). Per questo safe area e mockup sono sempre coerenti.

## Su quali telefoni valgono questi numeri
Il riferimento è un iPhone 13 Pro (19.5:9). Confrontando le proporzioni degli altri dispositivi:

| Dispositivo | Formato schermo | Differenza rispetto al riferimento |
|---|---|---|
| iPhone 15 / 16, Pro Max | 19.5:9 | praticamente identico (entro ~10 px); sui Max i margini sono anzi più piccoli |
| Android 20:9 (il più diffuso) | 20:9 | ~60 px **in più** di spazio libero sotto il video; sulle app a schermo pieno i margini crescono del 5% circa |
| Sony e simili 21:9 | 21:9 | ~180 px in più di spazio libero: più sicuro |
| Pieghevoli aperti, tablet | da 4:3 a 1:1 | il video viene mostrato intero con bande: più sicuro |
| iPhone SE, Android vecchi | 16:9 | l'interfaccia finisce tutta sul video: copre di più |

Fra i telefoni alti il più penalizzante è proprio quello usato per le misure, e tutto ciò che è più alto o più grande è più permissivo: per questo c'è una sola voce *Telefono moderno*. Gli schermi 16:9 sono l'unico caso davvero diverso: nella v4.0 si scelgono dal menu **Telefono**.

## Formato di export: sempre 1080×1920
Il file che carichi è uno solo e lo vedono tutti i telefoni: sono le app ad adattarlo allo schermo. Lo abbiamo verificato con un video di taratura **1080×2400** (righello ogni 20 px) pubblicato come Reel su iPhone 13 Pro, il 22/09/2026:
- Instagram ha mostrato **solo le righe 240–2160**, cioè il 9:16 centrale: le 240 righe sopra e le 240 sotto sono sparite. L'altezza in più viene buttata.
- Quelle 1920 righe riempiono lo schermo da y 0 a y 2283 (ingrandite 1,19 volte) e **ai lati si perdono ~48 px per parte**.

Quindi esporta sempre **1080×1920**: un video più alto non fa vedere di più, fa solo perdere quello che c'è in cima e in fondo. Sui telefoni alti le app a schermo pieno tagliano un po' i lati del tuo 1080×1920; il plugin ne tiene conto nei margini laterali:

| App (iPhone 13 Pro) | Area del video sullo schermo | Taglio su ogni lato del 1080×1920 | Lati safe area (taglio + 16) |
|---|---|---|---|
| Instagram Reels | y 0–2283 (sotto barra di stato e intestazione) | ~48 px (misurato col test) | 64 |
| TikTok schermo pieno | y 0–2283 | ~48 px | 64 |
| YouTube Shorts | y 0–2286 | ~49 px | 65 |
| Facebook Reels | y 0–2297 | ~51 px | 67 |
| Snapchat Spotlight | y 0–2220 | ~34 px | 56 / 50 |
| TikTok (feed) | y 141–2283 | ~16 px | 50 / 40 |
| Stories IG / FB, Snapchat Storie, LinkedIn, Pinterest | scheda o video mostrato intero | 0 | 40 |

## Telefono 16:9: come cambiano i valori
| Piattaforma | Telefono moderno: bottom / colonna | Telefono 16:9: bottom / colonna |
|---|---|---|
| TikTok | 286 / da y 833 | 436 / da y 683 |
| Instagram Reels | 345 / da y 961 | 554 / da y 752 |
| Instagram Stories | 40 | 164 (il campo risposta finisce sul video) |
| YouTube Shorts | 394 / da y 1015 | 534 / da y 875 |
| Snapchat Spotlight | 356 / da y 764 | 506 / da y 614 |
| TikTok schermo pieno | 269 / da y 899 | 419 / da y 749 |

Le altre piattaforme non cambiano. I valori 16:9 sono ricavati spostando l'interfaccia ancorata al fondo dello schermo: affidabilità *media*.

## Valori (px su 1080×1920) — telefono alto (19.5:9 e oltre)
| Piattaforma | Top | Bottom | Lati sx/dx | Colonna icone dx | Ads ufficiale T/B/L/R | Affidabilità |
|---|---|---|---|---|---|---|
| TikTok | 131 | 286 | 50/40 | 174 px da y 833 | 240/660/120/120 (+300 dx sotto metà) | **alta (misurata su screenshot)** |
| Instagram Reels | 227 con intestazione "For you / Friends" | 345 con riga "Followed by" | 64/64 | 191 px da y 961 | 269/672/65/65 | **alta (7 screenshot, ricalibrata col test di taratura v4.0)** |
| Instagram Stories | 152 (con riga musica / "Watch Full Reel" sotto il nome) | 40 (campo messaggio sotto il video) | 40/40 | — | 269/384/65/65 | **alta (misurata su 4 screenshot)** |
| Facebook Reels | 231 | 216 | 67/67 | 181 px da y 977 | 269/672/65/65 | **alta (misurata su 4 screenshot)** |
| Facebook Stories | 178 (il tasto muto, solo con musica, occupa l'angolo sx fino a y 306) | 40 (campo messaggio sotto il video) | 40/40 | — | 269/384/65/65 | **alta (misurata su 5 screenshot)** |
| YouTube Shorts | 226 (cerca e menu in alto a dx) | 394 con "Buy Super Thanks" + video collegato (297 solo video collegato, 301 solo Super Thanks, 202 senza) | 65/65 | 194 px da y 1015 | 192/480/0/108 | **alta (misurata su 6 screenshot)** |
| LinkedIn | 40 (nessuna UI sul video: la freccia indietro sta sopra) | 288 con titolo professionale sotto il nome (275 senza) | 40/40 | 141 px da y 1024 | nessuna spec ufficiale | **alta (misurata su 2 screenshot)** |
| LinkedIn 4:5 (timeline 1080×1350) | 40 | 40 (nome e didascalia stanno sotto il video) | 40/40 | 141 px da y 732 | nessuna spec ufficiale | **alta (misurata su 2 screenshot)** |
| TikTok schermo pieno | 242 | 269 | 64/64 | 198 px da y 899 | 240/660/120/120 | media (derivata da TikTok + 1 screenshot del dataset) |
| Pinterest pin 1:2 (timeline 1080×2160) | 163 | 168 | 40/40 | 162 px da y 2007 | 270/790/65/195 | **alta (stessa interfaccia del pin 9:16)** |
| Snapchat Spotlight | 259 | 356 (245 senza anteprima commenti) | 56/50 | 188 px da y 764 | 150/330 | **alta (misurata su 5 screenshot)** |
| Snapchat da profilo | 40 | 282 (con anteprima commenti; ~240 senza) | 40/40 | 156 px da y 817 | 150/330 | **alta (misurata su 5 screenshot)** |
| Snapchat Snap/Storia | 118 (solo angolo in alto a destra) | 40 | 40/40 | — | 150/330 | **alta (misurata su screenshot)** |
| Pinterest | 163 (solo angoli: indietro e menu) | 168 (pulsante Remix; senza, l'etichetta "AI modified" si ferma a 120) | 40/40 | 162 px da y 1767 (ricerca visiva) | 270/790/65/195 (ufficiale ads) | **alta (misurata su screenshot)** |

Note:
- Snapchat Spotlight ritaglia il video di circa 34 px per lato (già incluso). Da profilo e nelle Storie il video sta in una scheda con angoli arrotondati, senza ritaglio; il tasto risposta e "View Profile" stanno sotto il video.
- YouTube Shorts ritaglia il video di circa 58 px per lato (già incluso); la barra dell'app sta sotto il video.
- Facebook Stories: con musica compare una riga col brano sotto il nome (già inclusa) e un tasto muto Ø84 in alto a sinistra (x 35–119, y 221–305), mostrato nel mockup ma lasciato fuori dal rettangolo per non penalizzare tutta la fascia alta.
- Instagram Reels (nuova interfaccia con barra app flottante): **corretto nella v4.0**. Fino alla v3.9 il video era considerato alto l'82% dello schermo (fino a y 2080), con sotto un'estensione sfocata. Il test di taratura ha mostrato invece che il 9:16 va da y 0 a y 2283, ingrandito 1,19 volte e tagliato ~48 px per lato: nome, Follow, didascalia e "Followed by…" stanno sopra il video. Il margine basso passa quindi da 189 a 345, i lati da 40 a 64. Appena si apre la scheda Reels in alto c'è l'intestazione "For you / Friends" (fino a y 238): il plugin la include. La bolla dell'attività degli amici (in basso a sinistra, occasionale) è nel mockup ma non nel rettangolo. La colonna a destra sale di circa 70 px quando ci sono i numeri di commenti e repost: il plugin usa quel caso. Su telefono 16:9 (stima) tutta l'interfaccia sale sopra il video.
- LinkedIn (video aperto a schermo intero dal feed): il video 9:16 è mostrato intero, senza ritaglio; freccia indietro e barra di avanzamento stanno fuori dal video. La colonna a destra e il blocco nome salgono di una riga quando sotto il nome c'è il titolo professionale: il plugin usa quel caso.
- TikTok schermo pieno: alcuni video partono da sotto la barra di stato invece che sotto le tab. In quel caso l'interfaccia copre di più in alto (242 invece di 131). I valori sono ricavati dalla stessa interfaccia riproiettata sull'inquadratura più stretta e confermati dal dataset di 60 screenshot.
- Pinterest pin 1:2: stessa interfaccia del pin 9:16 su una scheda alta il doppio (timeline 1080×2160).
- LinkedIn 4:5: scegli "LinkedIn 4:5" su una timeline 1080×1350: il plugin usa un riquadro 4:5 (su timeline di altro formato lo centra). Sul video c'è solo la colonna a destra; la sua altezza dipende dal telefono (è ancorata al fondo dello schermo) e varia di ~35 px tra un video e l'altro: il plugin usa il caso più alto.
- Pinterest (pin aperto): like, commenti, condividi e "Save" stanno sotto la scheda del video, quindi sul contenuto restano solo i pulsanti agli angoli. I 790 px ufficiali valgono per le inserzioni.

**Misure reali:** TikTok, Facebook Reels e Stories, Pinterest e tutte le viste di Snapchat (Spotlight, da profilo, Snap/Storia) sono stati misurati su screenshot iPhone (19/09/2026): posizione di ogni icona, testo e barra, verificata sovrapponendo il mockup allo screenshot.

**Nota:** le piattaforme non pubblicano la posizione delle singole icone. Tutte le posizioni di questo plugin vengono da screenshot reali, misurati uno per uno; per rimisurarle basta uno screenshot a schermo intero per app.

## Contenuto
- `AnotherPerspective_SafeZones.dctl`: il plugin, con la scritta "Powered by Another Perspective Pictures" in basso (casella per spegnerla).
- `INSTALL.txt`: dove copiare il file e come usarlo.
- `Anteprima_Safe_Zones.jpg`: tutte le piattaforme in un colpo d'occhio.

## Fonti principali
- [Solid Labs – Social Safe Zones](https://www.solidlabs.com/social-safe-zones) (riporta le indicazioni ufficiali di Meta, TikTok e Google)
- [Pinterest – Review Pin specs](https://help.pinterest.com/en/article/review-pin-specs)
- [TikTok Ads – In-Feed Ads](https://ads.tiktok.com/help/article/tiktok-auction-in-feed-ads)
- [Google – Shorts ads](https://business.google.com/us/ad-solutions/youtube-ads/shorts-ads/)
- [Snapchat – ads practices, via RecruitmentAds](https://recruitmentads.com/free-tools/ad-mockup/snapchat)
- [PostPlanify](https://postplanify.com/blog/social-media-safe-zones-2026-complete-guide), [AdChecklab](https://adchecklab.com/articles/tiktok-safe-zone-dimensions-2026), [AIcarousels LinkedIn](https://www.aicarousels.com/free-tools/linkedin-safe-zone-checker)
