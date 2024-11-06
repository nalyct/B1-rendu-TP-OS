# TP1 : Plip plap votre OS



## Sommaire

- [TP1 : Plip plap votre OS](#tp1--plip-plap-votre-os)
  - [Sommaire](#sommaire)
- [I. Ressources de l'OS](#i-ressources-de-los)
  - [1. Programme, service, processus](#1-programme-service-processus)
  - [2. Mémoire et CPU](#2-mémoire-et-cpu)
  - [3. Stockage](#3-stockage)
  - [4. Réseau](#4-réseau)
  - [5. Utilisateurs](#5-utilisateurs)
  - [6. Random](#6-random)
  - [7. Ptit amusement](#7-ptit-amusement)


# I. Ressources de l'OS

Toutes les étapes sont à faire depuis le terminal.

## 1. Programme, service, processus

Un *programme* est une suite d'instructions à exécuter pour le processeur.

Un *processus* est un *programme* en cours d'exécution.

Un *service* est un *processus* lancé par l'OS.

🌞 **Lister tous les processus en cours d'exécution sur votre machine**

```
PS C:\> Get-Process

Handles  NPM(K)    PM(K)      WS(K)     CPU(s)     Id  SI ProcessName
-------  ------    -----      -----     ------     --  -- -----------
    142       9     2100       2964              6432   0 AggregatorHost
    520      24    12132      11724       4,50   5308   1 ApplicationFrameHost
    141      10     1668       6824             18188   0 armsvc
    428      33    35660      48516   2 134,92   1036   1 chrome
    491      36   118100     163212      18,27   1788   1 chrome
    310      25    37084      35836     211,80   3496   1 chrome
    263      23    32380      53736       3,95   3652   1 chrome
   2904      60   338872     146760   4 453,88   3708   1 chrome
    403      31    98272     159728      12,23   6648   1 chrome
    607      27    43804      13884      25,28   7352   1 chrome
    257      10     2104       2368       1,13   8748   1 chrome
    381      49   525268       6744      15,73  10336   1 chrome
    215      15    10704       9596      40,95  12304   1 chrome
   5049      86   228132     220324   8 615,59  12392   1 chrome
    263      25   123708     157184       8,39  12668   1 chrome
    274      18    13360       9628      22,30  13732   1 chrome
    228      19    14200      28816       0,14  14868   1 chrome
    487      41   183444     188540      29,55  17328   1 chrome
    318      24    40456      13776       5,45  19632   1 chrome
    338      30    66296      73768       4,25  19708   1 chrome
    314      23    26208      42532       1,08  20912   1 chrome
    552      44   216124     281660      18,38  21688   1 chrome
    179      14     8232      16856       0,03  21880   1 chrome
    321      26    38600      69488       2,09  22232   1 chrome
     87       8     2376       2972       0,06   4320   1 cmd
     87       8     2372       4408       0,08   5688   1 cmd
     87       8     2384       2016       0,09  11240   1 cmd
     87       8     2368       2956       0,03  19176   1 cmd
     87       8     2392       2976       0,09  19440   1 cmd
     93       7     5244       1824              4056   0 conhost
    310      16    13056      18672       2,36  13728   1 conhost
    137      10     5836       8296       0,19  14028   1 conhost
    137      10     5828       5900       0,27  15892   1 conhost
    137      10     5844       5924       0,16  17636   1 conhost
    137      10     5848       5908       0,09  17792   1 conhost
    137      10     5840       5908       0,19  21812   1 conhost
    185      11     2424       2132       0,59  11876   1 CredentialEnrollmentManager
    698      89    22668      46192      27,25  10408   1 CrossDeviceService
    818      29     2364       2596               820   0 csrss
    840      28     3200       3956               944   1 csrss
    845      24    29200      20196     680,34  11504   1 ctfmon
    628      26    17464      10512      10,30   3004   1 DataExchangeHost
    245      11     3260       3536              1564   1 DAX3API
    594      17     8732       4768              4272   0 DAX3API
    280      16    13344      81380       0,36  11136   1 Discord
   1217      32   299012     336888      20,30  11388   1 Discord
   1160      48    98636     133660      10,56  13704   1 Discord
    207      12    11388      33432       0,03  14940   1 Discord
    355      20    16444      55740       2,30  16944   1 Discord
   1358      97   293320     330496      41,02  18184   1 Discord
    131       8     1516       3976       0,31   9064   1 dllhost
   1419      25     7468      11784      13,52   9684   1 dllhost
    252      12     3212       6528       3,02  13244   1 dllhost
   2681      79   253092     108852              1600   1 dwm
    452      16     7320       3056       2,30   3100   1 ETDCtrl
    160      10     2024       1232              4292   0 ETDService
  21801     629   924868     403024   2 432,03   7768   1 explorer
  53104       9    18660       3624              4324   0 FbMAService
    189      13    23624       2116       8,84   1648   1 FnHotkeyCapsLKNumLK
    514      25    36212      10636      47,91   7792   1 FnHotkeyUtility
     42      10     5652       6704              1168   1 fontdrvhost
     42       7     2396       1388              1172   0 fontdrvhost
    177      10     1916       1760              4360   0 FwSwitchService
    815      26    11088      20560              5932   0 gamingservices
    144       7     1168        720              5924   0 gamingservicesnet
      0       0       60          8                 0   0 Idle
    137       8     1256       1544              1868   0 IntelCpHDCPSvc
    176      11     2036       2916     191,50   4212   1 ipf_helper
    148       9     1896       1868              4544   0 ipf_uf
    138      12     1572       1784              4344   0 ipfsvc
    147       9     1308        984              4532   0 jhi_service
   1014      61    32604      19592              4508   0 Lenovo.Modern.ImController
    294      13    20464       4892              4620   0 LenovoUtilityService
    757      49    33784       4596       4,20  22260   1 LenovoVantage-(GenericMessagingAddin)
    671      46    35880       9284             10940   0 LenovoVantage-(VantageCoreAddin)
   2582      53    50752      57908             22416   0 LenovoVantageService
    640      93   127052      23432     610,72  12772   1 Lively
    240      17     8340       2708       0,91  14296   1 Lively.Watchdog
    614      29    48812      37444       6,70  17184   1 LockApp
     65      27     2544       1092               856   0 LsaIso
   1625      32    12332      17032               824   0 lsass
      0       0     3672      74612              3300   0 Memory Compression
    435      19    27508      17620              4352   0 MoUsoCoreWorker
    510      19    12524      19924              5448   0 MpDefenderCoreService
    365      31   121924      40792   9 333,59  10648   1 mpv
   1001     214   290524     213452             15388   0 MsMpEng
    226      15     4852      11828             23340   0 NisSrv
    577      46    25576      13680              4440   0 OneApp.IGCC.WinService
    180      12     2172       1588              4652   0 pdf24
    336      18     4524      14076      11,70  12272   1 pdf24
    863      97    80700      61100       2,20  10908   1 PhoneExperienceHost
    732      36   141460     139440       3,11   6064   1 powershell
      0      19    15720      30912               116   0 Registry
    521      21   442636       8772              4696   0 RtkAudUService64
    413      15     4992       4032       1,41  12148   1 RtkAudUService64
    388      18     4792       7404       3,52   3832   1 RuntimeBroker
    163      11     2208       2484       0,39   7772   1 RuntimeBroker
    270      11     2268       2472       0,95   8408   1 RuntimeBroker
    384      22     8132      20988      16,75   9232   1 RuntimeBroker
   1213      47    19440      34148      36,55   9280   1 RuntimeBroker
    164      11     2272       2524       0,69  14300   1 RuntimeBroker
    655      25     8352      19276      12,45  16244   1 RuntimeBroker
    481      24    10612      20812      35,14  17360   1 RuntimeBroker
   1806     158   265704      75212     184,16   5204   1 SearchHost
    789      23    26268      33168             15752   0 SearchIndexer
      0       0      184      29720                76   0 Secure System
    586      23     8348      11508             12088   0 SecurityHealthService
    188      10     1880       3336       0,66  12068   1 SecurityHealthSystray
    962      19     7020       8252              1000   0 services
   1125      50    83352      38604      28,38  18084   1 ShellExperienceHost
    744      22     8000      22784      70,86   7240   1 sihost
     58       4     1144        352               552   0 smss
    451      23     7204       4184              3156   0 spoolsv
    498      43   196540     224508     134,42   2760   1 Spotify
    422      24    22484      55472       9,59   5816   1 Spotify
   1789      88   162284     123468      50,67   8596   1 Spotify
    980      28   219528     141876      11,69   8880   1 Spotify
    277      17    16988      26984       0,48  13288   1 Spotify
    271      17    70460      35296      18,66  18844   1 Spotify
    262      15    15384      38340       0,17  19788   1 Spotify
    333      19    16288      45688       1,06  22176   1 Spotify
   1008      48    93740      66484      73,88   6524   1 StartMenuExperienceHost
   1869      27    16852      28760              1140   0 svchost
   1850      20    14708      16468              1264   0 svchost
    311      12     3084       3992              1356   0 svchost
    298      11     2908       7024              1400   0 svchost
    110       9     1204       1444              1452   0 svchost
    244      11     1940       2468              1524   0 svchost
    194      13     3168       4596              1532   0 svchost
    221      13     3260       5540              1592   0 svchost
    259      13     3032       5064              1632   0 svchost
    245      10     1976       4564              1716   0 svchost
    157      27     7756       4072              1812   0 svchost
    193      11     2308       4484              1924   0 svchost
    533      13     3144       4028              1940   0 svchost
   1029      24     9220      12928              1968   0 svchost
    240      14     2912       3232              2028   0 svchost
    163      11     2036       3172              2040   0 svchost
    208      12     2292       2852              2072   0 svchost
    211      12     2280       3624              2184   0 svchost
    300       8     2396       3008              2260   0 svchost
    177      10     1588       2608              2268   0 svchost
    274      14     3700       8492              2304   0 svchost
    251      13     2480       3592              2484   0 svchost
    223      14     3116       5256              2520   0 svchost
    332      18     5800       6872              2624   0 svchost
    215      11     1988       2244              2636   0 svchost
    317      12    18516      17248              2864   0 svchost
    514      37    15588      13292              2880   0 svchost
    436      22     6840       8680              2896   0 svchost
    122       8     1292       1464              3052   0 svchost
    480      17    19792      12276              3120   0 svchost
    179      10     2044       3744              3184   0 svchost
    250      14     2816       5932              3192   0 svchost
    253       8     1288       1656              3200   0 svchost
    231      15     2224       4836              3316   0 svchost
    151       9     2316       3276              3336   0 svchost
    242      11     2136       3528              3380   0 svchost
    198      13     2280       4868              3408   0 svchost
    624      16     4728      10068              3536   0 svchost
    246      12     3412       3832              3604   0 svchost
    218      12     2240       5396              3612   0 svchost
    467      15     3060       5396              3632   0 svchost
    186      10     2000       3744              3792   0 svchost
    632      29     9308      10932              3904   0 svchost
    259      17     3528       8232              3928   0 svchost
    185      11     1724       2488              4148   0 svchost
    768      30    28392      28808              4236   0 svchost
    326      30     8988      12792              4248   0 svchost
    430      32    39496      30736              4256   0 svchost
    370      22     2860       5416              4500   0 svchost
    205      12     2108       5660              4828   0 svchost
    136       8     1316       1432              4844   0 svchost
    516      19    10164      14020              4860   0 svchost
    208      12     2276       3684              4988   0 svchost
    415      20     5112      12496              5036   0 svchost
    639      19     6708      11500              5776   0 svchost
    266      12     2504       3920              5976   0 svchost
    351      20     4752       8288              6000   0 svchost
    454      42    51512      47888              6016   0 svchost
     94       6      968       2228              6472   0 svchost
    214      16     6888       3432              6628   0 svchost
    311      14     3064       5728              6856   0 svchost
    426      23    22108      16164              6956   0 svchost
   1909      24    16372      21188              7076   0 svchost
    230      13     3092       6652              7108   0 svchost
    150      10     1976       3212       2,50   7272   1 svchost
    359      16     7396      14968      20,25   7280   1 svchost
    180      10     1828       2368       1,92   7288   1 svchost
    206      13     4128       5192       0,59   7356   1 svchost
   1788      24    12280      21472      29,17   7440   1 svchost
    153      11     1980       3628              7688   0 svchost
    266      14     4144      12324              7700   0 svchost
    209      13     2484       5144              8308   0 svchost
    375      14     2788       9888              8528   0 svchost
    146       9     1704       3132       0,48   8536   1 svchost
    203      13     1688       7524              8736   0 svchost
    352      17     4224      13172      13,67   8868   1 svchost
    272      15     3432       8240       3,38   9344   1 svchost
    225      17     2248       3460              9916   0 svchost
    325      16     4756      12140             10008   0 svchost
    308      15     3704      11768      43,97  12312   1 svchost
    427      26     5364       9552       2,70  12420   1 svchost
    159      42     1688       1272             12916   0 svchost
    424      24     3500       5136             13096   0 svchost
    286      15     2748       6312             13132   0 svchost
    256      16     3664       7320             13260   0 svchost
    176      11     1896       3468             14192   0 svchost
    404      18     7100       3748             14444   0 svchost
    121       8     1348       1376             14644   0 svchost
    443      14     7336      16124             17896   0 svchost
    746      22     6068      15732             18212   0 svchost
    174      10     1784       7704             18252   0 svchost
    210      13     2892       4548             20972   0 svchost
    123       8     1372       5620             21444   0 svchost
   5682       0       76       7060                 4   0 System
   1155      52    68380        596       1,80  11248   1 SystemSettings
    533      26     6912      17764      14,69   6584   1 SystemSettingsBroker
    640      32   116300      15540     234,80  11516   1 TabTip
    317      34     8048      11576      16,25   7676   1 taskhostw
    412      25    10604      13252       5,86  17404   1 taskhostw
   1805      89   140728      94548     401,59   1988   1 TextInputHost
    197      13     3708      12600              7468   0 TiWorker
    139       9     1928       8148             13532   0 TrustedInstaller
    146       9     1820       4156              4448   0 unsecapp
    130       9     1464       2956       1,58   4456   1 unsecapp
    134       9     1488       6308       0,09  13272   1 unsecapp
    133      10     1840       1544       0,20   8828   1 UserOOBEBroker
    195      11     2112       5396      50,95  12008   1 vgtray
    426      36    14796       5728       0,91   3588   1 Windows.Media.BackgroundPlayback
    145      12     1504        784               920   0 wininit
    286      14     2788       5144               484   1 winlogon
    134       8     1396       2136              4048   0 wlanext
    276      17    20124       8268              4616   0 WmiPrvSE
    271      14     2776       1800              4920   0 WMIRegistrationService
    559      30    23564      10236              1308   0 WUDFHost
    283      15     4624       6444              1464   0 WUDFHost
    537      17     4840      10068              1848   0 WUDFHost
    226       8     1592       1764              2104   0 WUDFHost
    201      11     2132       4212              2684   0 YMC
```

🌞 **Trouver les 3 processus qui ont le plus petit identifiant**

```
PS C:\> Get-Process | Sort-Object Id | Select-Object -First 3

Handles  NPM(K)    PM(K)      WS(K)     CPU(s)     Id  SI ProcessName
-------  ------    -----      -----     ------     --  -- -----------
      0       0       60          8                 0   0 Idle
   5679       0       76       7080                 4   0 System
      0       0      184      29720                76   0 Secure System
```

🌞 **Lister tous les services de la machine...**

```
PS C:\> Get-Service | Where-Object { $_.Status -eq 'Running' }
>>

Status   Name               DisplayName
------   ----               -----------
Running  AdobeARMservice    Adobe Acrobat Update Service
Running  Appinfo            Informations d’application
Running  AppMgmt            Gestion d’applications
Running  AppXSvc            Service de déploiement AppX (AppXSVC)
Running  AudioEndpointBu... Générateur de points de terminaison...
Running  Audiosrv           Audio Windows
Running  BDESVC             Service de chiffrement de lecteur B...
Running  BFE                Moteur de filtrage de base
Running  BluetoothUserSe... Service de support des utilisateurs...
Running  BrokerInfrastru... Service d’infrastructure des tâches...
Running  BTAGService        Service de passerelle audio Bluetooth
Running  BthAvctpSvc        Service AVCTP
Running  bthserv            Service de prise en charge Bluetooth
Running  camsvc             Service Gestionnaire d’accès aux fo...
Running  cbdhsvc_12f18a     Service utilisateur du Presse-papie...
Running  CDPSvc             Service de plateforme des appareils...
Running  CDPUserSvc_12f18a  Service pour utilisateur de platefo...
Running  CoreMessagingRe... CoreMessaging
Running  cplspcon           Intel(R) Content Protection HDCP Se...
Running  CredentialEnrol... CredentialEnrollmentManagerUserSvc_...
Running  CryptSvc           Services de chiffrement
Running  DcomLaunch         Lanceur de processus serveur DCOM
Running  DeviceAssociati... Service d’association de périphérique
Running  DeviceInstall      Service d’installation de périphérique
Running  DevicesFlowUser... Flux d’appareils_12f18a
Running  DevQueryBroker     Service Broker de découverte en arr...
Running  Dhcp               Client DHCP
Running  DiagTrack          Expériences des utilisateurs connec...
Running  DispBrokerDeskt... Service de stratégie d'affichage
Running  DisplayEnhancem... Service d'amélioration de l'affichage
Running  Dnscache           Client DNS
Running  DolbyDAXAPI        Dolby DAX API Service
Running  DoSvc              Optimisation de livraison
Running  DPS                Service de stratégie de diagnostic
Running  dptftcs            Intel(R) Dynamic Tuning Technology ...
Running  DsSvc              Service de partage des données
Running  DusmSvc            Consommation des données
Running  EapHost            Protocole EAP (Extensible Authentic...
Running  ETDService         ELAN Service
Running  EventLog           Journal d’événements Windows
Running  EventSystem        Système d’événement COM+
Running  FbMAService        Fibocom WWAN MAService
Running  Fibocom WWAN Fl... Fibocom WWAN Flash Service
Running  FontCache          Service de cache de police Windows
Running  FrameServer        Serveur de trame de la Caméra Windows
Running  GamingServices     Gaming Services
Running  GamingServicesNet  Gaming Services
Running  gpsvc              Client de stratégie de groupe
Running  HvHost             Service d'hôte HV
Running  igccservice        Intel(R) Graphics Command Center Se...
Running  ImControllerSer... System Interface Foundation Service
Running  InstallService     Installation du service Microsoft S...
Running  InventorySvc       Service d’Appraisal inventaire et c...
Running  ipfsvc             Intel(R) Innovation Platform Framew...
Running  iphlpsvc           Assistance IP
Running  jhi_service        Intel(R) Dynamic Application Loader...
Running  KeyIso             Isolation de clé CNG
Running  LanmanServer       Serveur
Running  LanmanWorkstation  Station de travail
Running  LenovoFnAndFunc... Lenovo Fn and function keys service
Running  LenovoVantageSe... Critical Service for Lenovo Vantage
Running  lfsvc              Service de géolocalisation
Running  LicenseManager     Serveur Gestionnaire de licences Wi...
Running  lmhosts            Assistance NetBIOS sur TCP/IP
Running  LSM                Gestionnaire de session locale
Running  MDCoreSvc          Microsoft Defender Service de base
Running  mpssvc             Pare-feu Windows Defender
Running  NcbService         Service Broker pour les connexions ...
Running  Netman             Connexions réseau
Running  netprofm           Service Liste des réseaux
Running  NgcCtnrSvc         Conteneur Microsoft Passport
Running  NgcSvc             Microsoft Passport
Running  NPSMSvc_12f18a     NPSMSvc_12f18a
Running  nsi                Service Interface du magasin réseau
Running  OneSyncSvc_12f18a  Hôte de synchronisation_12f18a
Running  PcaSvc             Service de l’Assistant Compatibilit...
Running  PDF24              PDF24
Running  PenService_12f18a  PenService_12f18a
Running  PhoneSvc           Service téléphonique
Running  PimIndexMainten... Données de contacts_12f18a
Running  PlugPlay           Plug-and-Play
Running  Power              Alimentation
Running  ProfSvc            Service de profil utilisateur
Running  RasMan             Gestionnaire des connexions d’accès...
Running  RmSvc              Service de gestion radio
Running  RpcEptMapper       Mappeur de point de terminaison RPC
Running  RpcSs              Appel de procédure distante (RPC)
Running  RtkAudioUnivers... Realtek Audio Universal Service
Running  SamSs              Gestionnaire de comptes de sécurité
Running  Schedule           Planificateur de tâches
Running  SecurityHealthS... Service Sécurité Windows
Running  SENS               Service de notification d’événement...
Running  SensorService      Service de capteur
Running  SensrSvc           Service de surveillance des capteurs
Running  ShellHWDetection   Détection matériel noyau
Running  Spooler            Spouleur d’impression
Running  SSDPSRV            Découverte SSDP
Running  SstpSvc            Service SSTP (Secure Socket Tunneli...
Running  StateRepository    Service State Repository (StateRepo...
Running  StiSvc             Acquisition d’image Windows (WIA)
Running  StorSvc            Service de stockage
Running  SysMain            SysMain
Running  SystemEventsBroker Service Broker des événements système
Running  TextInputManage... Service de gestion des entrées de t...
Running  Themes             Thèmes
Running  TimeBrokerSvc      Service Broker pour les événements ...
Running  TokenBroker        Gestionnaire de comptes web
Running  TrkWks             Client de suivi de lien distribué
Running  UdkUserSvc_12f18a  Service utilisateur du kit de dével...
Running  UnistoreSvc_12f18a Stockage des données utilisateur_12...
Running  UserDataSvc_12f18a Accès aux données utilisateur_12f18a
Running  UserManager        Gestionnaire des utilisateurs
Running  UsoSvc             Mettre à jour le service Orchestrator
Running  VaultSvc           Gestionnaire d’informations d’ident...
Running  W32Time            Temps Windows
Running  Wcmsvc             Gestionnaire des connexions Windows
Running  WdiSystemHost      Hôte système de diagnostics
Running  WdNisSvc           Service d’inspection réseau de l’an...
Running  webthreatdefsvc    Service Web Threat Defense
Running  webthreatdefuse... Service d’utilisateur Web Threat De...
Running  WinDefend          Service antivirus Microsoft Defender
Running  WinHttpAutoProx... Service de découverte automatique d...
Running  Winmgmt            Infrastructure de gestion Windows
Running  WlanSvc            Service de configuration automatiqu...
Running  WMIRegistration... Intel(R) Management Engine WMI Prov...
Running  WpnService         Service du système de notifications...
Running  WpnUserService_... Service utilisateur de notification...
Running  wscsvc             Centre de sécurité
Running  WSearch            Windows Search
Running  YMC                YMC
```
```
PS C:\> Get-Service | Where-Object { $_.Status -eq 'Stopped' }
>>

Status   Name               DisplayName
------   ----               -----------
Stopped  AarSvc_12f18a      Agent Activation Runtime_12f18a
Stopped  AJRouter           Service de routeur AllJoyn
Stopped  ALG                Service de la passerelle de la couc...
Stopped  AppIDSvc           Identité de l’application
Stopped  AppReadiness       Préparation des applications
Stopped  AppVClient         Microsoft App-V Client
Stopped  AssignedAccessM... Service AssignedAccessManager
Stopped  autotimesvc        Heure cellulaire
Stopped  AxInstSV           Programme d’installation ActiveX (A...
Stopped  BcastDVRUserSer... Service utilisateur de diffusion et...
Stopped  BITS               Service de transfert intelligent en...
Stopped  CaptureService_... CaptureService_12f18a
Stopped  CertPropSvc        Propagation du certificat
Stopped  ClipSVC            Service de licences de client (Clip...
Stopped  CloudBackupRest... Service de restauration et de sauve...
Stopped  cloudidsvc         Service d’identité de Microsoft Cloud
Stopped  COMSysApp          Application système COM+
Stopped  ConsentUxUserSv... Service utilisateur ConsentUX_12f18a
Stopped  CscService         Fichiers hors connexion
Stopped  dcsvc              Service de configuration (DC) déclaré
Stopped  defragsvc          Optimiser les lecteurs
Stopped  DeviceAssociati... DeviceAssociationBroker_12f18a
Stopped  DevicePickerUse... DevicePicker_12f18a
Stopped  diagnosticshub.... Service Collecteur standard du conc...
Stopped  diagsvc            Diagnostic Execution Service
Stopped  DialogBlockingS... DialogBlockingService
Stopped  DmEnrollmentSvc    Service d'inscription de la gestion...
Stopped  DmicService        Dual DMIC Auto-Select Service
Stopped  dmwappushservice   Service de routage de messages Push...
Stopped  dot3svc            Configuration automatique de réseau...
Stopped  DsmSvc             Gestionnaire d’installation de péri...
Stopped  EABackgroundSer... EABackgroundService
Stopped  edgeupdate         Microsoft Edge Update Service (edge...
Stopped  edgeupdatem        Microsoft Edge Update Service (edge...
Stopped  EFS                Système de fichiers EFS (Encrypting...
Stopped  embeddedmode       Mode incorporé
Stopped  EntAppSvc          Service de gestion des applications...
Stopped  fdPHost            Hôte du fournisseur de découverte d...
Stopped  FDResPub           Publication des ressources de décou...
Stopped  fhsvc              Service d’historique des fichiers
Stopped  FontCache3.0.0.0   Cache de police de Windows Presenta...
Stopped  FrameServerMonitor Moniteur de serveur de trame Caméra...
Stopped  GameInputSvc       GameInput Service
Stopped  GoogleChromeEle... Google Chrome Elevation Service (Go...
Stopped  GoogleUpdaterIn... Service interne de mise à jour Goog...
Stopped  GoogleUpdaterSe... Service de mise à jour Google (Goog...
Stopped  GraphicsPerfSvc    GraphicsPerfSvc
Stopped  gupdate            Service Google Update (gupdate)
Stopped  gupdatem           Service Google Update (gupdatem)
Stopped  hidserv            Service du périphérique d’interface...
Stopped  icssvc             Service Point d'accès sans fil mobi...
Stopped  IKEEXT             Modules de génération de clés IKE e...
Stopped  Intel(R) Platfo... Intel(R) Platform License Manager S...
Stopped  IpxlatCfgSvc       Service de configuration de convers...
Stopped  KtmRm              Service KtmRm pour Distributed Tran...
Stopped  lltdsvc            Mappage de découverte de topologie ...
Stopped  LxpSvc             Service d'expérience linguistique
Stopped  MapsBroker         Gestionnaire des cartes téléchargées
Stopped  McpManagementSe... McpManagementService
Stopped  MessagingServic... MessagingService_12f18a
Stopped  MicrosoftEdgeEl... Microsoft Edge Elevation Service (M...
Stopped  MixedRealityOpe... Service Windows Mixed Reality OpenXR
Stopped  MSDTC              Coordinateur de transactions distri...
Stopped  MSiSCSI            Service Initiateur iSCSI de Microsoft
Stopped  msiserver          Windows Installer
Stopped  MsKeyboardFilter   Filtre clavier Microsoft
Stopped  NaturalAuthenti... Authentification naturelle
Stopped  NcaSvc             Assistant Connectivité réseau
Stopped  NcdAutoSetup       Configuration automatique des périp...
Stopped  Netlogon           Netlogon
Stopped  NetSetupSvc        Service Configuration du réseau
Stopped  NetTcpPortSharing  Service de partage de ports Net.Tcp
Stopped  NlaSvc             Connaissance des emplacements réseau
Stopped  p2pimsvc           Gestionnaire d’identité réseau homo...
Stopped  p2psvc             Groupement de mise en réseau de pairs
Stopped  P9RdrService_12... P9RdrService_12f18a
Stopped  PeerDistSvc        BranchCache
Stopped  perceptionsimul... Service de simulation de perception...
Stopped  PerfHost           Hôte de DLL de compteur de performance
Stopped  pla                Journaux & alertes de performance
Stopped  PNRPAutoReg        Service de publication des noms d’o...
Stopped  PNRPsvc            Protocole PNRP
Stopped  PolicyAgent        Agent de stratégie IPsec
Stopped  PrintNotify        Extensions et notifications d’impri...
Stopped  PrintWorkflowUs... PrintWorkflow_12f18a
Stopped  PushToInstall      Service PushToInstall de Windows
Stopped  QWAVE              Expérience audio-vidéo haute qualit...
Stopped  RasAuto            Gestionnaire des connexions automat...
Stopped  RemoteAccess       Routage et accès distant
Stopped  RemoteRegistry     Registre à distance
Stopped  RetailDemo         Service de démo du magasin
Stopped  RpcLocator         Localisateur d’appels de procédure ...
Stopped  SCardSvr           Carte à puce
Stopped  ScDeviceEnum       Service d’énumération de périphériq...
Stopped  SCPolicySvc        Stratégie de retrait de la carte à ...
Stopped  SDRSVC             Sauvegarde Windows
Stopped  seclogon           Ouverture de session secondaire
Stopped  SEMgrSvc           Gestionnaires des paiements et des ...
Stopped  Sense              Service Protection avancée contre l...
Stopped  SensorDataService  Service Données de capteur
Stopped  SessionEnv         Configuration des services Bureau à...
Stopped  SgrmBroker         Service Broker du moniteur d'exécut...
Stopped  SharedAccess       Partage de connexion Internet (ICS)
Stopped  SharedRealitySvc   Service de données spatiales
Stopped  shpamsvc           Shared PC Account Manager
Stopped  smphost            SMP de l’Espace de stockages Microsoft
Stopped  SmsRouter          Service Routeur SMS Microsoft Windows.
Stopped  SNMPTrap           Interruption SNMP
Stopped  spectrum           Service de perception Windows
Stopped  sppsvc             Protection logicielle
Stopped  ssh-agent          OpenSSH Authentication Agent
Stopped  Steam Client Se... Steam Client Service
Stopped  svsvc              Vérificateur de points
Stopped  swprv              Fournisseur de cliché instantané de...
Stopped  TapiSrv            Téléphonie
Stopped  TermService        Services Bureau à distance
Stopped  TieringEngineSe... Gestion des niveaux de stockage
Stopped  TroubleshootingSvc Service de résolution des problèmes...
Stopped  TrustedInstaller   Programme d’installation pour les m...
Stopped  tzautoupdate       Programme de mise à jour automatiqu...
Stopped  UevAgentService    Service User Experience Virtualization
Stopped  uhssvc             Microsoft Update Health Service
Stopped  UmRdpService       Redirecteur de port du mode utilisa...
Stopped  upnphost           Hôte de périphérique UPnP
Stopped  VacSvc             Service de composition audio volumé...
Stopped  vds                Disque virtuel
Stopped  vgc                vgc
Stopped  vmicguestinterface Interface de services d’invité Hyper-V
Stopped  vmicheartbeat      Service Pulsation Microsoft Hyper-V
Stopped  vmickvpexchange    Service Échange de données Microsof...
Stopped  vmicrdv            Service de virtualisation Bureau à ...
Stopped  vmicshutdown       Service Arrêt de l’invité Microsoft...
Stopped  vmictimesync       Service Synchronisation date/heure ...
Stopped  vmicvmsession      Service Hyper-V PowerShell Direct
Stopped  vmicvss            Requête du service VSS Hyper-V
Stopped  VSS                Cliché instantané des volumes
Stopped  WaaSMedicSvc       WaaSMedicSvc
Stopped  WalletService      WalletService
Stopped  WarpJITSvc         Warp JIT Service
Stopped  wbengine           Service de moteur de sauvegarde en ...
Stopped  WbioSrvc           Service de biométrie Windows
Stopped  wcncsvc            Windows Connect Now - Registre de c...
Stopped  WdiServiceHost     Service hôte WDIServiceHost
Stopped  WebClient          WebClient
Stopped  Wecsvc             Collecteur d’événements de Windows
Stopped  WEPHOSTSVC         Service hôte du fournisseur de chif...
Stopped  wercplsupport      Prise en charge du Panneau de confi...
Stopped  WerSvc             Service de rapport d’erreurs Windows
Stopped  WFDSConMgrSvc      Service Wi-Fi Direct Service de ges...
Stopped  WiaRpc             Événements d’acquisition d’images f...
Stopped  WinRM              Gestion à distance de Windows (Gest...
Stopped  wisvc              Service Windows Insider
Stopped  wlidsvc            Assistant Connexion avec un compte ...
Stopped  wlpasvc            Service de l’Assistant de profil local
Stopped  WManSvc            Service de gestion de Windows
Stopped  wmiApSrv           Carte de performance WMI
Stopped  WMPNetworkSvc      Service de partage réseau du Lecteu...
Stopped  workfolderssvc     Dossiers de travail
Stopped  WpcMonSvc          Contrôle parental
Stopped  WPDBusEnum         Service Énumérateur d’appareil mobile
Stopped  wuauserv           Windows Update
Stopped  WwanSvc            Service de configuration automatiqu...
Stopped  XblAuthManager     Gestionnaire d'authentification Xbo...
Stopped  XblGameSave        Jeu sauvegardé sur Xbox Live
Stopped  XboxGipSvc         Xbox Accessory Management Service
Stopped  XboxNetApiSvc      Service de mise en réseau Xbox Live
```

## 2. Mémoire et CPU

La *mémoire* c'est la *mémoire vive* ou *RAM*. Le terme *mémoire* ne fera **jamais** référence à votre disque dur ou quoi. *Mémoire*, c'est la RAM.

🌞 **RAM**

```
PS C:\> Get-CimInstance -ClassName Win32_OperatingSystem | Select-Object TotalVisibleMemorySize, FreePhysicalMemory
>>

TotalVisibleMemorySize FreePhysicalMemory
---------------------- ------------------
               7914772            1014224
```

🌞 **CPU**

```
PS C:\> Get-CimInstance -ClassName Win32_Processor | Select-Object -Property LoadPercentage
>>

LoadPercentage
--------------
             9
```

## 3. Stockage

Le *stockage* c'est tout les périphériques qui permettent de stocker des données sur le long terme : clés USB, disque dur (HDD ou SSD), etc.

🌞 **Périphériques**

```
PS C:\> Get-Disk | Select-Object -Property Model, Size
>>

Model                        Size
-----                        ----
Micron MTFDKCD256TFK 256060514304
```

🌞 **Partitions**

```
PS C:\> Get-Partition | Select-Object -Property DriveLetter, PartitionNumber, Size, Type, IsHidden
>>


DriveLetter     :
PartitionNumber : 1
Size            : 272629760
Type            : System
IsHidden        : True

DriveLetter     :
PartitionNumber : 2
Size            : 134217728
Type            : Reserved
IsHidden        : True

DriveLetter     : C
PartitionNumber : 3
Size            : 222030938112
Type            : Basic
IsHidden        : False

DriveLetter     :
PartitionNumber : 4
Size            : 33621540864
Type            : Recovery
IsHidden        : True
```

🌞 **Espace disque**

```
PS C:\> Get-PSDrive -Name C | Select-Object -Property Used, Free, @{Name="Total";Expression={[math]::round($_.Used + $_.Free, 2)}}
>>

        Used         Free        Total
        ----         ----        -----
120732246016 101298688000 222030934016
```

## 4. Réseau

Le *réseau* fait référence à la gestion des *cartes réseau* de votre PC. Ca fait aussi référence à la gestion des *connexions* réseau.

Une *carte réseau* c'est un périphérique qui permet d'envoyer et recevoir des octets avec un câble (ou des ondes WiFi). L'OS se charge d'attribuer une *adresse IP* sur chaque *carte réseau*.

Une *connexion réseau* c'est quand tu lances un programme qui a besoin de se connecter à un *service réseau*. Genre quand tu joues à LoL ou Minecraft, ou que t'es sur Youtube, tu te connectes à un serveur : tu fais une *connexion réseau*.

🌞 **Cartes réseau**
```
PS C:\> Get-NetAdapter | Select-Object Name, Status, @{Name="IPAddress";Expression={(Get-NetIPAddress -InterfaceAlias $_.Name).IPAddress}}
>>

Name  Status IPAddress
----  ------ ---------
Wi-Fi Up     {fe80::4733:6f94:6df:6dd2%5, 10.3.214.3}
```

> Une adresse IP est toujours de la forme `xxx.xxx.xxx.xxx` où les `xxx` sont uniquement des nombres compris entre 0 et 255.

🌞 **Connexions réseau**

```
PS C:\> Get-NetTCPConnection | Where-Object { $_.State -eq 'Established' } | Select-Object LocalAddress, LocalPort, RemoteAddress, RemotePort, @{Name='ProcessName';Expression={(Get-Process -Id $_.OwningProcess).Name}}
>>


LocalAddress  : 10.3.214.3
LocalPort     : 56128
RemoteAddress : 52.112.100.74
RemotePort    : 443
ProcessName   : chrome

LocalAddress  : 10.3.214.3
LocalPort     : 56109
RemoteAddress : 52.112.120.222
RemotePort    : 443
ProcessName   : chrome

LocalAddress  : 10.3.214.3
LocalPort     : 55943
RemoteAddress : 35.186.224.45
RemotePort    : 443
ProcessName   : Discord

LocalAddress  : 10.3.214.3
LocalPort     : 55941
RemoteAddress : 162.159.134.234
RemotePort    : 443
ProcessName   : Discord

LocalAddress  : 10.3.214.3
LocalPort     : 55559
RemoteAddress : 35.186.224.45
RemotePort    : 443
ProcessName   : Spotify

LocalAddress  : 10.3.214.3
LocalPort     : 55538
RemoteAddress : 74.125.71.188
RemotePort    : 5228
ProcessName   : chrome

LocalAddress  : 10.3.214.3
LocalPort     : 55535
RemoteAddress : 20.199.120.151
RemotePort    : 443
ProcessName   : svchost

LocalAddress  : 10.3.214.3
LocalPort     : 55521
RemoteAddress : 35.186.224.41
RemotePort    : 443
ProcessName   : Spotify

LocalAddress  : 10.3.214.3
LocalPort     : 55518
RemoteAddress : 104.199.65.9
RemotePort    : 4070
ProcessName   : Spotify

LocalAddress  : 10.3.214.3
LocalPort     : 55085
RemoteAddress : 20.223.35.26
RemotePort    : 443
ProcessName   : StartMenuExperienceHost

LocalAddress  : 127.0.0.1
LocalPort     : 49706
RemoteAddress : 127.0.0.1
RemotePort    : 49705
ProcessName   : WUDFHost

LocalAddress  : 127.0.0.1
LocalPort     : 49705
RemoteAddress : 127.0.0.1
RemotePort    : 49706
ProcessName   : WUDFHost

LocalAddress  : 127.0.0.1
LocalPort     : 49704
RemoteAddress : 127.0.0.1
RemotePort    : 49703
ProcessName   : ipfsvc

LocalAddress  : 127.0.0.1
LocalPort     : 49703
RemoteAddress : 127.0.0.1
RemotePort    : 49704
ProcessName   : ipfsvc

LocalAddress  : 127.0.0.1
LocalPort     : 49702
RemoteAddress : 127.0.0.1
RemotePort    : 49701
ProcessName   : WUDFHost

LocalAddress  : 127.0.0.1
LocalPort     : 49701
RemoteAddress : 127.0.0.1
RemotePort    : 49702
ProcessName   : WUDFHost
```
> *Il s'agit de lister les connexions de type **TCP** en réalité, si ça peut vous aider dans vos recherches :)*

## 5. Utilisateurs

**Un *utilisateur*, sur un OS, c'est une identité qui peut lancer des programmes.**

Un *processus* s'exécute **toujours** sous l'identité d'un certain utilisateur. Genre si tu te connectes avec l'utilisateur "meooow" quand tu ouvres ton PC, et bien tous les programmes que tu lances seront exécutés sous l'identité de "meooow".

Chaque *utilisateur* a des privilèges particuliers sur la machine, et en particulier sur les fichiers : chaque *utilisateur* a le droit (ou non) de lire tel ou tel fichier, de le modifier, ou de l'exécuter comme un programme.

**Choisir l'*utilisateur* qui lance un *programme* c'est donc choisir les *droits* du *processus* pendant son exécution.**

A chaque fois qu'un *programme* essaie d'accéder à un fichier, l'OS vérifie si le *programme* a le droit ou non de faire ça.

> *Il est donc potentiellement très dangereux d'exécuter des programmes en tant qu'administrateur, car ces processus auront des privilèges très élevés pendant qu'ils s'exécutent.*

🌞 **Lister les *utilisateurs* de la machine**

```
PS C:\> Get-LocalUser | Select-Object Name, Enabled
>>

Name               Enabled
----               -------
Administrateur       False
DefaultAccount       False
Invité               False
Naly                  True
WDAGUtilityAccount   False
```

🌞 **Heure de login**

```
PS C:\> Get-CimInstance -ClassName ‘Win32_LogonSession’ | Where {$_.LogonType -eq ‘2’}
>>

LogonId Name LogonType StartTime           Status AuthenticationPackage
------- ---- --------- ---------           ------ ---------------------
1199840      2         11/10/2024 11:47:20        NTLM
1199729      2         11/10/2024 11:47:20        NTLM
```

🌞 **Lister les *processus* en cours d'exécution**

```
PS C:\> Get-Process | Select-Object Name, Id, @{Name='UserName';Expression={(Get-WmiObject Win32_ComputerSystem).UserName}}
>>

Name                    Id UserName
----                    -- --------
AggregatorHost        6432 LORDI-F6EIS5EVF\Naly
ApplicationFrameHost  5308 LORDI-F6EIS5EVF\Naly
armsvc               18188 LORDI-F6EIS5EVF\Naly
chrome                1036 LORDI-F6EIS5EVF\Naly
chrome                1788 LORDI-F6EIS5EVF\Naly
chrome                2156 LORDI-F6EIS5EVF\Naly
chrome                3496 LORDI-F6EIS5EVF\Naly
chrome                3652 LORDI-F6EIS5EVF\Naly
chrome                3708 LORDI-F6EIS5EVF\Naly
chrome                6648 LORDI-F6EIS5EVF\Naly
chrome                7352 LORDI-F6EIS5EVF\Naly
chrome                7624 LORDI-F6EIS5EVF\Naly
chrome                8748 LORDI-F6EIS5EVF\Naly
chrome               10336 LORDI-F6EIS5EVF\Naly
chrome               12304 LORDI-F6EIS5EVF\Naly
chrome               12392 LORDI-F6EIS5EVF\Naly
chrome               12948 LORDI-F6EIS5EVF\Naly
chrome               13732 LORDI-F6EIS5EVF\Naly
chrome               14948 LORDI-F6EIS5EVF\Naly
chrome               15952 LORDI-F6EIS5EVF\Naly
chrome               17328 LORDI-F6EIS5EVF\Naly
chrome               17768 LORDI-F6EIS5EVF\Naly
chrome               19632 LORDI-F6EIS5EVF\Naly
chrome               19708 LORDI-F6EIS5EVF\Naly
chrome               20912 LORDI-F6EIS5EVF\Naly
chrome               21688 LORDI-F6EIS5EVF\Naly
chrome               22012 LORDI-F6EIS5EVF\Naly
chrome               22232 LORDI-F6EIS5EVF\Naly
cmd                   4320 LORDI-F6EIS5EVF\Naly
cmd                   5688 LORDI-F6EIS5EVF\Naly
cmd                  11240 LORDI-F6EIS5EVF\Naly
cmd                  19176 LORDI-F6EIS5EVF\Naly
cmd                  19440 LORDI-F6EIS5EVF\Naly
conhost               4056 LORDI-F6EIS5EVF\Naly
conhost              13728 LORDI-F6EIS5EVF\Naly
conhost              14028 LORDI-F6EIS5EVF\Naly
conhost              15892 LORDI-F6EIS5EVF\Naly
conhost              17636 LORDI-F6EIS5EVF\Naly
conhost              17792 LORDI-F6EIS5EVF\Naly
conhost              21812 LORDI-F6EIS5EVF\Naly
CredentialEnrollm... 11876 LORDI-F6EIS5EVF\Naly
CrossDeviceService   10408 LORDI-F6EIS5EVF\Naly
csrss                  820 LORDI-F6EIS5EVF\Naly
csrss                  944 LORDI-F6EIS5EVF\Naly
ctfmon               11504 LORDI-F6EIS5EVF\Naly
DataExchangeHost      3004 LORDI-F6EIS5EVF\Naly
DAX3API               1564 LORDI-F6EIS5EVF\Naly
DAX3API               4272 LORDI-F6EIS5EVF\Naly
Discord              11136 LORDI-F6EIS5EVF\Naly
Discord              11388 LORDI-F6EIS5EVF\Naly
Discord              13704 LORDI-F6EIS5EVF\Naly
Discord              14940 LORDI-F6EIS5EVF\Naly
Discord              16944 LORDI-F6EIS5EVF\Naly
Discord              18184 LORDI-F6EIS5EVF\Naly
dllhost               9064 LORDI-F6EIS5EVF\Naly
dllhost               9684 LORDI-F6EIS5EVF\Naly
dllhost              13244 LORDI-F6EIS5EVF\Naly
dwm                   1600 LORDI-F6EIS5EVF\Naly
ETDCtrl               3100 LORDI-F6EIS5EVF\Naly
ETDService            4292 LORDI-F6EIS5EVF\Naly
explorer              7768 LORDI-F6EIS5EVF\Naly
FbMAService           4324 LORDI-F6EIS5EVF\Naly
FnHotkeyCapsLKNumLK   1648 LORDI-F6EIS5EVF\Naly
FnHotkeyUtility       7792 LORDI-F6EIS5EVF\Naly
fontdrvhost           1168 LORDI-F6EIS5EVF\Naly
fontdrvhost           1172 LORDI-F6EIS5EVF\Naly
FwSwitchService       4360 LORDI-F6EIS5EVF\Naly
gamingservices        5932 LORDI-F6EIS5EVF\Naly
gamingservicesnet     5924 LORDI-F6EIS5EVF\Naly
Idle                     0 LORDI-F6EIS5EVF\Naly
IntelCpHDCPSvc        1868 LORDI-F6EIS5EVF\Naly
ipf_helper            4212 LORDI-F6EIS5EVF\Naly
ipf_uf                4544 LORDI-F6EIS5EVF\Naly
ipfsvc                4344 LORDI-F6EIS5EVF\Naly
jhi_service           4532 LORDI-F6EIS5EVF\Naly
Lenovo.Modern.ImC...  4508 LORDI-F6EIS5EVF\Naly
LenovoUtilityService  4620 LORDI-F6EIS5EVF\Naly
LenovoVantage-(Ge... 22260 LORDI-F6EIS5EVF\Naly
LenovoVantage-(Va... 10940 LORDI-F6EIS5EVF\Naly
LenovoVantageService 22416 LORDI-F6EIS5EVF\Naly
Lively               12772 LORDI-F6EIS5EVF\Naly
Lively.Watchdog      14296 LORDI-F6EIS5EVF\Naly
LockApp              17184 LORDI-F6EIS5EVF\Naly
LsaIso                 856 LORDI-F6EIS5EVF\Naly
lsass                  824 LORDI-F6EIS5EVF\Naly
Memory Compression    3300 LORDI-F6EIS5EVF\Naly
MoUsoCoreWorker       4352 LORDI-F6EIS5EVF\Naly
MpDefenderCoreSer...  5448 LORDI-F6EIS5EVF\Naly
mpv                  10648 LORDI-F6EIS5EVF\Naly
MsMpEng              15388 LORDI-F6EIS5EVF\Naly
NisSrv               23340 LORDI-F6EIS5EVF\Naly
OneApp.IGCC.WinSe...  4440 LORDI-F6EIS5EVF\Naly
pdf24                 4652 LORDI-F6EIS5EVF\Naly
pdf24                12272 LORDI-F6EIS5EVF\Naly
PhoneExperienceHost  10908 LORDI-F6EIS5EVF\Naly
powershell            6064 LORDI-F6EIS5EVF\Naly
Registry               116 LORDI-F6EIS5EVF\Naly
RtkAudUService64      4696 LORDI-F6EIS5EVF\Naly
RtkAudUService64     12148 LORDI-F6EIS5EVF\Naly
RuntimeBroker         3832 LORDI-F6EIS5EVF\Naly
RuntimeBroker         7772 LORDI-F6EIS5EVF\Naly
RuntimeBroker         8408 LORDI-F6EIS5EVF\Naly
RuntimeBroker         9232 LORDI-F6EIS5EVF\Naly
RuntimeBroker         9280 LORDI-F6EIS5EVF\Naly
RuntimeBroker        14300 LORDI-F6EIS5EVF\Naly
RuntimeBroker        16244 LORDI-F6EIS5EVF\Naly
RuntimeBroker        17360 LORDI-F6EIS5EVF\Naly
SearchHost            5204 LORDI-F6EIS5EVF\Naly
SearchIndexer        15752 LORDI-F6EIS5EVF\Naly
Secure System           76 LORDI-F6EIS5EVF\Naly
SecurityHealthSer... 12088 LORDI-F6EIS5EVF\Naly
SecurityHealthSys... 12068 LORDI-F6EIS5EVF\Naly
services              1000 LORDI-F6EIS5EVF\Naly
ShellExperienceHost  18084 LORDI-F6EIS5EVF\Naly
sihost                7240 LORDI-F6EIS5EVF\Naly
smss                   552 LORDI-F6EIS5EVF\Naly
spoolsv               3156 LORDI-F6EIS5EVF\Naly
Spotify               2760 LORDI-F6EIS5EVF\Naly
Spotify               5816 LORDI-F6EIS5EVF\Naly
Spotify               8596 LORDI-F6EIS5EVF\Naly
Spotify               8880 LORDI-F6EIS5EVF\Naly
Spotify              13288 LORDI-F6EIS5EVF\Naly
Spotify              18844 LORDI-F6EIS5EVF\Naly
Spotify              19788 LORDI-F6EIS5EVF\Naly
Spotify              22176 LORDI-F6EIS5EVF\Naly
StartMenuExperien...  6524 LORDI-F6EIS5EVF\Naly
svchost               1140 LORDI-F6EIS5EVF\Naly
svchost               1264 LORDI-F6EIS5EVF\Naly
svchost               1356 LORDI-F6EIS5EVF\Naly
svchost               1400 LORDI-F6EIS5EVF\Naly
svchost               1452 LORDI-F6EIS5EVF\Naly
svchost               1524 LORDI-F6EIS5EVF\Naly
svchost               1532 LORDI-F6EIS5EVF\Naly
svchost               1592 LORDI-F6EIS5EVF\Naly
svchost               1632 LORDI-F6EIS5EVF\Naly
svchost               1716 LORDI-F6EIS5EVF\Naly
svchost               1812 LORDI-F6EIS5EVF\Naly
svchost               1924 LORDI-F6EIS5EVF\Naly
svchost               1940 LORDI-F6EIS5EVF\Naly
svchost               1968 LORDI-F6EIS5EVF\Naly
svchost               2028 LORDI-F6EIS5EVF\Naly
svchost               2040 LORDI-F6EIS5EVF\Naly
svchost               2072 LORDI-F6EIS5EVF\Naly
svchost               2184 LORDI-F6EIS5EVF\Naly
svchost               2260 LORDI-F6EIS5EVF\Naly
svchost               2268 LORDI-F6EIS5EVF\Naly
svchost               2304 LORDI-F6EIS5EVF\Naly
svchost               2484 LORDI-F6EIS5EVF\Naly
svchost               2520 LORDI-F6EIS5EVF\Naly
svchost               2624 LORDI-F6EIS5EVF\Naly
svchost               2636 LORDI-F6EIS5EVF\Naly
svchost               2864 LORDI-F6EIS5EVF\Naly
svchost               2880 LORDI-F6EIS5EVF\Naly
svchost               2896 LORDI-F6EIS5EVF\Naly
svchost               3052 LORDI-F6EIS5EVF\Naly
svchost               3120 LORDI-F6EIS5EVF\Naly
svchost               3184 LORDI-F6EIS5EVF\Naly
svchost               3192 LORDI-F6EIS5EVF\Naly
svchost               3200 LORDI-F6EIS5EVF\Naly
svchost               3316 LORDI-F6EIS5EVF\Naly
svchost               3336 LORDI-F6EIS5EVF\Naly
svchost               3380 LORDI-F6EIS5EVF\Naly
svchost               3408 LORDI-F6EIS5EVF\Naly
svchost               3536 LORDI-F6EIS5EVF\Naly
svchost               3604 LORDI-F6EIS5EVF\Naly
svchost               3612 LORDI-F6EIS5EVF\Naly
svchost               3632 LORDI-F6EIS5EVF\Naly
svchost               3792 LORDI-F6EIS5EVF\Naly
svchost               3904 LORDI-F6EIS5EVF\Naly
svchost               3928 LORDI-F6EIS5EVF\Naly
svchost               4148 LORDI-F6EIS5EVF\Naly
svchost               4236 LORDI-F6EIS5EVF\Naly
svchost               4248 LORDI-F6EIS5EVF\Naly
svchost               4256 LORDI-F6EIS5EVF\Naly
svchost               4500 LORDI-F6EIS5EVF\Naly
svchost               4828 LORDI-F6EIS5EVF\Naly
svchost               4844 LORDI-F6EIS5EVF\Naly
svchost               4860 LORDI-F6EIS5EVF\Naly
svchost               4988 LORDI-F6EIS5EVF\Naly
svchost               5036 LORDI-F6EIS5EVF\Naly
svchost               5776 LORDI-F6EIS5EVF\Naly
svchost               5976 LORDI-F6EIS5EVF\Naly
svchost               6000 LORDI-F6EIS5EVF\Naly
svchost               6016 LORDI-F6EIS5EVF\Naly
svchost               6472 LORDI-F6EIS5EVF\Naly
svchost               6628 LORDI-F6EIS5EVF\Naly
svchost               6856 LORDI-F6EIS5EVF\Naly
svchost               6956 LORDI-F6EIS5EVF\Naly
svchost               7076 LORDI-F6EIS5EVF\Naly
svchost               7108 LORDI-F6EIS5EVF\Naly
svchost               7272 LORDI-F6EIS5EVF\Naly
svchost               7280 LORDI-F6EIS5EVF\Naly
svchost               7288 LORDI-F6EIS5EVF\Naly
svchost               7356 LORDI-F6EIS5EVF\Naly
svchost               7440 LORDI-F6EIS5EVF\Naly
svchost               7688 LORDI-F6EIS5EVF\Naly
svchost               7700 LORDI-F6EIS5EVF\Naly
svchost               8308 LORDI-F6EIS5EVF\Naly
svchost               8528 LORDI-F6EIS5EVF\Naly
svchost               8536 LORDI-F6EIS5EVF\Naly
svchost               8736 LORDI-F6EIS5EVF\Naly
svchost               8868 LORDI-F6EIS5EVF\Naly
svchost               9344 LORDI-F6EIS5EVF\Naly
svchost               9916 LORDI-F6EIS5EVF\Naly
svchost              10008 LORDI-F6EIS5EVF\Naly
svchost              12312 LORDI-F6EIS5EVF\Naly
svchost              12420 LORDI-F6EIS5EVF\Naly
svchost              12916 LORDI-F6EIS5EVF\Naly
svchost              13096 LORDI-F6EIS5EVF\Naly
svchost              13132 LORDI-F6EIS5EVF\Naly
svchost              13260 LORDI-F6EIS5EVF\Naly
svchost              13416 LORDI-F6EIS5EVF\Naly
svchost              14192 LORDI-F6EIS5EVF\Naly
svchost              14444 LORDI-F6EIS5EVF\Naly
svchost              14644 LORDI-F6EIS5EVF\Naly
svchost              17896 LORDI-F6EIS5EVF\Naly
svchost              18212 LORDI-F6EIS5EVF\Naly
svchost              21444 LORDI-F6EIS5EVF\Naly
svchost              22904 LORDI-F6EIS5EVF\Naly
System                   4 LORDI-F6EIS5EVF\Naly
SystemSettings       11248 LORDI-F6EIS5EVF\Naly
SystemSettingsBroker  6584 LORDI-F6EIS5EVF\Naly
TabTip               11516 LORDI-F6EIS5EVF\Naly
taskhostw             7676 LORDI-F6EIS5EVF\Naly
taskhostw            17404 LORDI-F6EIS5EVF\Naly
TextInputHost         1988 LORDI-F6EIS5EVF\Naly
unsecapp              4448 LORDI-F6EIS5EVF\Naly
unsecapp              4456 LORDI-F6EIS5EVF\Naly
unsecapp             13272 LORDI-F6EIS5EVF\Naly
UserOOBEBroker        8828 LORDI-F6EIS5EVF\Naly
vgtray               12008 LORDI-F6EIS5EVF\Naly
Windows.Media.Bac...  3588 LORDI-F6EIS5EVF\Naly
wininit                920 LORDI-F6EIS5EVF\Naly
winlogon               484 LORDI-F6EIS5EVF\Naly
wlanext               4048 LORDI-F6EIS5EVF\Naly
WmiPrvSE              4616 LORDI-F6EIS5EVF\Naly
WMIRegistrationSe...  4920 LORDI-F6EIS5EVF\Naly
WUDFHost              1308 LORDI-F6EIS5EVF\Naly
WUDFHost              1464 LORDI-F6EIS5EVF\Naly
WUDFHost              1848 LORDI-F6EIS5EVF\Naly
WUDFHost              2104 LORDI-F6EIS5EVF\Naly
YMC                   2684 LORDI-F6EIS5EVF\Naly
```


🌞 **Sur un fichier random qui se trouve dans votre dossier `Téléchargements/`**

```
PS C:\> Get-Acl "C:\Users\$env:USERNAME\Downloads\form2.jpg" | Select-Object Owner
>>

Owner
-----
LORDI-F6EIS5EVF\Naly
```

## 6. Random

🌞 **Uptime**

```
PS C:\> Get-CimInstance -ClassName Win32_OperatingSystem | Select-Object LastBootUpTime
>>

LastBootUpTime
--------------
11/10/2024 11:45:49
```

🌞 **Device**

```
PS C:\> Get-CimInstance -ClassName Win32_Processor | Select-Object Name
>>

Name
----
Intel(R) N100
```

🌞 **Version**

```
PS C:\> Get-CimInstance -ClassName Win32_OperatingSystem | Select-Object Caption, Version
>>

Caption                                      Version
-------                                      -------
Microsoft Windows 11 Professionnel Éducation 10.0.22631
```

🌞 **Mise à jour**

```
PS C:\> Get-WmiObject -Class Win32_QuickFixEngineering | Select-Object -First 1 InstalledOn
>>

InstalledOn
-----------
11/10/2024 00:00:00
```

## 7. Ptit amusement

Mise en situation réelle d'une petite investigation sur votre PC, avec le terminal, liés aux notions qu'on a vu.

🌞 **Lister les *connexions active*s**

- **choisir l'une des lignes comme cible**, une sur laquelle vous souhaiterez obtenir plus d'infos
- notez en particulier :
  - l'adresse IP que vous avez utilisé pour vous connecter à ce serveur (dans une colonne)
  - l'adresse IP du serveur auquel vous êtes connectés (dans l'autre colonne :d)
  - le nom/l'identifiant du *programme* qui fait cette connexion

> Ne choissisez **pas** une connexion qui utilise l'adresse IP `127.0.0.1`, n'importe quelle autre fera l'affaire.

🌞 **En apprendre + sur le *processus* en cours d'exécution**

```
PS C:\Program Files\Google\Chrome\Application> $chromePath = "C:\Program Files\Google\Chrome\Application\chrome.exe"
>> $owner = (Get-Acl $chromePath).Owner
>> Write-Output "Propriétaire du programme : $owner"
>>
Propriétaire du programme : BUILTIN\Administrateurs
PS C:\Program Files\Google\Chrome\Application>
```

🌞 **En apprendre + sur le *programme***

```
PS C:\> cd "C:\Program Files\Google\Chrome\Application" 
```

 ```
PS C:\Program Files\Google\Chrome\Application> ./chrome
``` 

```
PS C:\Program Files\Google\Chrome\Application>
```



🌞 **En apprendre + sur l'adresse IP**

- utilise ma commande magique pour ça :

```bash
# Sur Windows
Invoke-RestMethod -Method Get -Uri http://ip-api.com/json/<ADRESSE IP ICI>
# Par exemple
Invoke-RestMethod -Method Get -Uri http://ip-api.com/json/13.37.13.37

# Sur Linux/MacOS
curl http://ip-api.com/json/<ADRESSE IP ICI>
# Par exemple
curl http://ip-api.com/json/13.37.13.37
```

```

PS C:\> Invoke-RestMethod -Method Get -Uri http://ip-api.com/json/13.37.13.37


status      : success
country     : France
countryCode : FR
region      : IDF
regionName  : Île-de-France
city        : Paris
zip         : 75000
lat         : 48,8566
lon         : 2,35222
timezone    : Europe/Paris
isp         : Amazon Technologies Inc.
org         : AWS EC2 (eu-west-3)
as          : AS16509 Amazon.com, Inc.
query       : 13.37.13.37
```

```
PS C:\> curl http://ip-api.com/json/13.37.13.37


StatusCode        : 200
StatusDescription : OK
Content           : {"status":"success","country":"France","countryCode":"FR","region":"IDF","regionName":"Île-de-France","city":"Paris","zip":"75000","lat":48.8566,"lon":2.35222,"timezone":"Europe/Paris","isp"
                    :"Amazon T...
RawContent        : HTTP/1.1 200 OK
                    Access-Control-Allow-Origin: *
                    X-Ttl: 38
                    X-Rl: 43
                    Content-Length: 301
                    Content-Type: application/json; charset=utf-8
                    Date: Mon, 04 Nov 2024 17:23:09 GMT

                    {"status":"success","co...
Forms             : {}
Headers           : {[Access-Control-Allow-Origin, *], [X-Ttl, 38], [X-Rl, 43], [Content-Length, 301]...}
Images            : {}
InputFields       : {}
Links             : {}
ParsedHtml        : System.__ComObject
RawContentLength  : 301
```

🌞 **Délai**

- mesurer la latence entre vous et ce serveur
- ça se fait en utilisant la commande `ping` : `ping <ADRESSE IP>`
- par exemple, pour envoyer des ptits *Pings* vers l'adresse IP `13.37.13.37` : `ping 13.37.13.37`
- généralement vous avez une valeur en millisecondes : le temps qu'un message *Ping* fasse l'aller-retour entre vous et le serveur

> *Ping* est un message extrêmement simpliste, le plus simpliste qu'on peut faire en fait. On veut juste un ptit message pour tester le temps d'aller-retour vers un serveur.

![Ping](./img/high.jpg)

```
PS C:\Users\Naly>  ping 13.37.13.37

Envoi d’une requête 'Ping'  13.37.13.37 avec 32 octets de données :
Délai d’attente de la demande dépassé.
Délai d’attente de la demande dépassé.
Délai d’attente de la demande dépassé.
Délai d’attente de la demande dépassé.

Statistiques Ping pour 13.37.13.37:
    Paquets : envoyés = 4, reçus = 0, perdus = 4 (perte 100%),


```
