(Sensitivity-detection-and-COB-sensitivity-detection)=

# 敏感度偵測

## 敏感度演算法

目前我們有三種敏感度偵測模型：

* 敏感度 AAPS
* 敏感度 加權平均
* 敏感度 Oref1

### 敏感度 AAPS

敏感度計算與 Oref1 相同，但你可以指定追溯的時間範圍。 最小碳水化合物吸收是從偏好設定中的最大碳水吸收時間計算得出。

### 敏感度 加權平均

敏感度是從偏差資料中計算的加權平均值。 你可以指定過去的時間。 較新的偏差資料會有更高的權重。 最小碳水吸收是從偏好設定中的最大碳水吸收時間計算得出。 該算法在跟蹤敏感度變化方面最快。

(SensitivityDetectionAndCob-sensitivity-oref1)=

### 敏感度 Oref1

敏感度是根據過去8小時的資料計算，或是從最近的注射點更換時間開始計算（如果更換時間少於8小時）。 碳水化合物（如果尚未被吸收）會在偏好設定中指定的時間後被取消計算。 只有 Oref1 算法支援未宣佈的餐食（UAM）。 這意味著，偵測到 UAM 的時間將被排除在敏感度計算之外。 因此，如果你使用 SMB 並搭配 UAM，必須選擇 Oref1 算法才能正確運作。 欲了解更多資訊，請參閱[OpenAPS Oref1 文件](https://openaps.readthedocs.io/en/latest/docs/Customize-Iterate/oref1.html)。

Oref1 是推薦的選擇：它是唯一可以檢測 UAM 並與 [OpenAps SMB](#Open-APS-features-super-micro-bolus-smb) 此較新算法一起運作的方案。

## 同時進行碳水化合物處理

在使用 AAPS、加權平均與 Oref1 時有顯著差異。 Oref 外掛僅預期一次處理一餐的碳水化合物。 這意味著第二餐的消耗會在第一餐完全消耗後才開始。 AAPS+加權平均會在你輸入碳水化合物時立即開始消耗。 如果有多餐在消耗，最小碳水消耗會根據餐食大小和最大吸收時間進行調整。 與 Oref 外掛相比，最小吸收量將相對較高。