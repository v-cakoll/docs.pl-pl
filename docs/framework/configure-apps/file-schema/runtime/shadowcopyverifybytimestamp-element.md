---
title: <shadowCopyVerifyByTimestamp>, element
ms.date: 03/30/2017
helpviewer_keywords:
- <shadowCopyTimeStampVerification> element
- shadowCopyTimeStampVerification element
ms.assetid: 2f1648e5-997b-435e-a4f9-d236c574c66c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 902ed07264615e91721d92861b9d974ea10f0d1e
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55273887"
---
# <a name="shadowcopyverifybytimestamp-element"></a>\<shadowCopyVerifyByTimestamp > Element
Określa, czy kopiowanie w tle używa domyślne zachowanie uruchamiania wprowadzona w [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], lub powraca do zachowania uruchamiania wcześniejszych wersji programu .NET Framework.  
  
 \<Konfiguracja > Element  
\<środowisko uruchomieniowe > Element  
\<shadowCopyVerifyByTimestamp > Element  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<shadowCopyVerifyByTimestamp enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|Włączone|Atrybut wymagany.<br /><br /> Określa, czy domen aplikacji, które używają kopiowania w tle porównania sygnatury czasowe zestawów podczas uruchamiania, aby ustalić, czy zestaw został zaktualizowany przed Kopiowanie zestawów w tle.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|true|Podczas uruchamiania kopiuje tylko zestawy, które zostały zaktualizowane, ponieważ ich ostatniego zostały skopiowane do katalogu kopii w tle. Jest to flaga domyślna dla [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].|  
|false|Zostanie przywrócony zachowanie uruchamiania poprzednich wersji programu .NET Framework, który został do skopiowania wszystkich plików podczas uruchamiania.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
 Począwszy od [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], zestawy są kopie w tle woluminów tylko wtedy, gdy ich sygnatury czasowe wskazują, że zostały zmienione od czasu ich ostatniego zostały skopiowane do katalogu kopii w tle. Poprawia czasy uruchamiania wielu aplikacji, które używają kopiowania w tle, zgodnie z opisem w [Kopiowanie zestawów w tle](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md). Aplikacje, które mają wysoki procent i częstotliwość aktualizacji zestawu nie mogą korzystać z tej zmiany w zachowaniu. W takim przypadku można użyć tego elementu, aby przywrócić zachowanie z poprzednich wersji programu .NET Framework.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak wyłączyć domyślne zachowanie uruchamiania kopiowania w tle w [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]i przywrócenie zachowania uruchamiania poprzednich wersji programu .NET Framework.  
  
```xml  
<configuration>  
   <runtime>  
      <shadowCopyVerifyByTimestamp enabled="false" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także
- [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [Kopiowanie zestawów w tle](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md)
