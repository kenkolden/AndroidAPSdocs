# 相容的 CGM

本節提供所有與**AAPS**相容的**CGMs/FGMs**的簡要總覽。

*提示*: 如果你能在 xDrip+ 應用中顯示你的血糖資料，可以在**AAPS**中選擇 xDrip+ 作為**血糖** 資料來源。

* [一般建議](../CompatibleCgms/GeneralCGMRecommendation.md)
* [資料平滑](../CompatibleCgms/SmoothingBloodGlucoseData.md)
* [xDrip+設定](../CompatibleCgms/xDrip.md)
* [Nightscout 作為血糖資料來源](../CompatibleCgms/CgmNightscoutUpload.md): 儘管可以使用 Nightscout 作為閉環胰島素給藥的血糖資料來源，但**這種方法不推薦**，因為其依賴穩定的行動網路或 Wi-Fi 連接。 這意味著你的**CGM**資料只有在與你的 Nightscout 網站保持在線連接時，才會被**AAPS**接收。 為了更加穩定的設置，使用具有接收器的本地廣播的 CGM（如下所列）到**AAPS**，是一個更好的選擇。

| CGM                                                  | 可用的[血糖資料來源](../SettingUpAaps/ConfigBuilder.md#bg-source)                                            |
| ---------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| [Dexcom G7](../CompatibleCgms/DexcomG7.md)           | xDrip+、DiaKEM App 或 [Juggluco](https://www.juggluco.nl/Jugglucohelp/introhelp.html)                 |
| [Dexcom ONE+ 和 Stelo](../CompatibleCgms/DexcomG7.md) | xDrip+                                                                                              |
| [Dexcom G6](../CompatibleCgms/DexcomG6.md)           | xDrip+ 或 BYODA                                                                                      |
| [Dexcom ONE](../CompatibleCgms/DexcomG6.md)          | xDrip+                                                                                              |
| [Dexcom G5](../CompatibleCgms/DexcomG5.md)           | xDrip+                                                                                              |
| [Libre 3/3+](../CompatibleCgms/Libre3.md)            | [Juggluco](https://www.juggluco.nl/Juggluco/libre3/)（可搭配或不搭配 xDrip+ 使用）                             |
| [Libre 2/2+](../CompatibleCgms/Libre2.md)            | 僅限歐盟地區的 xDrip+，或 [Juggluco](https://www.juggluco.nl/Jugglucohelp/introhelp.html)（可搭配或不搭配 xDrip+ 使用） |
| [Libre 1](../CompatibleCgms/Libre1.md)               | xDrip+、Glimp、Tomato 或 Diabox。 需要發射器                                                                 |
| [Eversense](../CompatibleCgms/Eversense.md)          | xDrip+ 或 ESEL/Eversense 修補的應用程式                                                                     |
| [Enlite（MM640G/MM630G）](../CompatibleCgms/MM640g.md) | xDrip+ 或 MM640g + 600系列 Android 上傳程式                                                                |
| [PocTech](../CompatibleCgms/PocTech.md)              | PocTech                                                                                             |
| [歐態（Ottai）](../CompatibleCgms/OttaiM8.md)            | 歐態（Ottai）                                                                                           |
| [Syai Tag](../CompatibleCgms/SyaiTagX1.md)           | Syai Tag                                                                                            |
| Sibionics CGM                                        | [Juggluco](https://www.juggluco.nl/Jugglucohelp/introhelp.html)                                     |

(GettingStarted-TrustedBGSource)=

## 可信的血糖來源

獲得監管批准的**CGM**用於商業混合閉環系統，視為可信的**血糖**來源。

為了讓**AAPS**正確識別它們，發送**血糖**讀取的應用程式必須能提供感測器資訊。

可信的資料來源允許**SMB**隨時傳送。

| 傳感器                   |              CGM 應用程式              |
| --------------------- |:----------------------------------:|
| Dexcom G5/G6          |       BYODA, xDrip+ (直接, 原生)       |
| Dexcom G7             |   DiaKEM、xDrip+（直連、原生）、Juggluco    |
| Dexcom ONE/ONE+/Stelo |          xDrip+ (直接, 原生)           |
| Libre 2/2+ (歐盟)       | xDrip+、Juggluco（可搭配或不搭配 xDrip+ 使用） |
| Libre 2/2+/3/3+       |    Juggluco（可搭配或不搭配 xDrip+ 使用）     |

注意：xDrip+ 配套應用程式(Companion app)和追蹤者不是可信的資料來源。
