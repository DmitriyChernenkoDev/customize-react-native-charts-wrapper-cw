# React Native Charts Wrapper

## Link to original library 

https://github.com/wuxudong/react-native-charts-wrapper

## Classes wich where changed

1. Add cutomized library Charts
file customize-react-native-charts-wrapper/android/build.gradle
-----

        apply plugin: 'com.android.library'

	android {
    		compileSdkVersion 27
    		buildToolsVersion "27.0.3"

    	defaultConfig {
        		minSdkVersion 16
        		targetSdkVersion 27
        		versionCode 1
        		versionName "1.0"
    		}
	}

	dependencies {
    		implementation fileTree(dir: 'libs', include: ['*.jar'])
    		implementation 'com.facebook.react:react-native:0.20.+'
    		implementation 'com.github.DmitriyChernenkoDev:CustomizeCharts:v1.0.6'
	}
            
-----
2. Remove previus line 
file customize-react-native-charts-wrapper/android/src/main/java/com/github/wuxudong/rncharts/charts/BarLineChartBaseManager.java
-----

change method <b>setCommonAxisConfig</b>, add ti line 358

        ReadableArray limitLines = propMap.getArray("limitLines");
    
-----
3. ### Set one indicator line
Android - in file \node_modules\node_modules\react-native-charts-wrapper\android\src\main\java\com\github\wuxudong\rncharts\charts\ChartBaseManager.java
		add to method setCommonAxisConfig(Chart chart, AxisBase axis, ReadableMap propMap) function  -axis.removeAllLimitLines();- wich delete all current lines

		--Example---
		// limit lines
        if (BridgeUtils.validate(propMap, ReadableType.Array, "limitLines")) {
            ReadableArray limitLines = propMap.getArray("limitLines");
            axis.removeAllLimitLines();

iOS - in file \node_modules\node_modules\react-native-charts-wrapper\ios\ReactNativeCharts\RNChartViewBase.swift
		add to method setCommonAxisConfig(Chart chart, AxisBase axis, ReadableMap propMap) function  -axis.removeAllLimitLines();- wich delete all current lines

		--Example---
		// limit lines
        // limit lines
        if config["limitLines"].array != nil {
            let limitLinesConfig = config["limitLines"].arrayValue
	    axis.removeAllLimitLines();
----
4. Changes fields: shalowH, shalowL, close, open  to H, L, O, C

in files:
- CandleDataExtract.java;
- CandleDataExtract.swift;  
- ChartDataConfig.js;
- docs.md;
in lib react-native-charts-wrapper 
