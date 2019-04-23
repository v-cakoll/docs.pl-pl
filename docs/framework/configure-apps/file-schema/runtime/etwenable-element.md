---
title: <etwEnable>, element
ms.date: 03/30/2017
helpviewer_keywords:
- etwEnable element
- <etwEnable> element
ms.assetid: 29dde982-6d8b-4099-8867-ad0d7733f6dc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6ba411114bfb853e06c83adb42713d43f1452d9c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59135073"
---
# <a name="etwenable-element"></a>\<etwenable — > Element
Określa, czy włączyć śledzenie zdarzeń dla Windows (ETW) dla typowych zdarzeń środowiska wykonawczego języka.  
  
 \<Konfiguracja > Element  
\<środowisko uruchomieniowe > Element  
\<etwEnabled>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<etwEnable enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|Włączone|Atrybut wymagany.<br /><br /> Określa, czy powinien być włączony funkcji ETW.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|true|Włączanie funkcji ETW. Jest to wartość domyślna dla wersji systemu Windows począwszy od systemów operacyjnych Windows Vista i Windows Server 2008.|  
|false|Wyłączenie funkcji ETW. Jest to wartość domyślna dla wcześniejszych wersji systemu Windows.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
 Począwszy od systemów Windows Vista, ETW jest domyślnie włączona. Ten element służy do wyłączania funkcji ETW dla aplikacji. We wcześniejszych wersjach systemu Windows, ten element umożliwia włączenie funkcji ETW dla aplikacji.  
  
> [!NOTE]
>  ETW można włączać lub globalnie wyłączone na serwerze za pomocą ustawienia rejestru. Zobacz [Kontrolowanie logowania w programie .NET Framework](../../../../../docs/framework/performance/controlling-logging.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak włączyć śledzenie zdarzeń systemu Windows dla aplikacji.  
  
```xml  
<configuration>  
   <runtime>  
      <etwEnable enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [Kontrolowanie logowania w programie .NET Framework](../../../../../docs/framework/performance/controlling-logging.md)
