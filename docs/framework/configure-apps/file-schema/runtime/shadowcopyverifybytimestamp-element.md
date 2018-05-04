---
title: '&lt;shadowCopyVerifyByTimestamp&gt; — Element'
ms.date: 03/30/2017
helpviewer_keywords:
- <shadowCopyTimeStampVerification> element
- shadowCopyTimeStampVerification element
ms.assetid: 2f1648e5-997b-435e-a4f9-d236c574c66c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2439a4812163562a73bd3520e65b9973e666a863
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltshadowcopyverifybytimestampgt-element"></a>&lt;shadowCopyVerifyByTimestamp&gt; — Element
Określa, czy kopiowanie w tle używa domyślne zachowanie uruchamiania wprowadzone w systemie [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], lub wraca do zachowania uruchamiania wcześniejszych wersji programu .NET Framework.  
  
 \<Konfiguracja > — Element  
\<środowisko uruchomieniowe > — Element  
\<shadowCopyVerifyByTimestamp > — Element  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<shadowCopyVerifyByTimestamp enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|włączone|Atrybut wymagany.<br /><br /> Określa, czy domeny aplikacji, które używają kopiowanie w tle porównania sygnatury czasowe zestawów podczas uruchamiania, aby określić, czy zestaw został zaktualizowany przed Kopiowanie zestawów w tle.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|true|Podczas uruchamiania kopiuje tylko zestawy, które zostały zaktualizowane od czasu ostatniego zostały one kopiowane do katalogu kopii w tle. Jest to wartość domyślna dla [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].|  
|false|Przywraca zachowanie uruchamiania poprzednich wersji programu .NET Framework, na który został do skopiowania wszystkich plików podczas uruchamiania.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
 Począwszy od [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], zestawy są kopie tylko wtedy, gdy ich sygnatury czasowe wskazują, że zostały zmienione od czasu ostatniego zostały one kopiowane do katalogu kopii w tle w tle. Zwiększa to czasy uruchamiania dla wielu aplikacji, które używają kopiowanie w tle, zgodnie z opisem w [Kopiowanie zestawów w tle](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md). Aplikacje, które mają wysoki procent i częstotliwość aktualizacji zestawu nie mogą korzystać z tej zmiany w zachowaniu. W takim przypadku służy tego elementu. Aby przywrócić zachowanie z poprzednich wersji programu .NET Framework.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak można wyłączyć domyślnego zachowania uruchamiania kopiowanie w tle w [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]i przywrócenie zachowania uruchamiania poprzednich wersji programu .NET Framework.  
  
```xml  
<configuration>  
   <runtime>  
      <shadowCopyVerifyByTimestamp enabled="false" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Kopiowanie zestawów w tle](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md)
