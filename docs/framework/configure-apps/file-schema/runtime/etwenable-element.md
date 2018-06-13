---
title: '&lt;etwenable —&gt; — Element'
ms.date: 03/30/2017
helpviewer_keywords:
- etwEnable element
- <etwEnable> element
ms.assetid: 29dde982-6d8b-4099-8867-ad0d7733f6dc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 267a4a29282881d18201d0cb2062e91b4ff974a9
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32745178"
---
# <a name="ltetwenablegt-element"></a>&lt;etwenable —&gt; — Element
Określa, czy włączyć śledzenie zdarzeń systemu Windows (ETW) dla zdarzenia środowiska uruchomieniowego języka wspólnego.  
  
 \<Konfiguracja > — Element  
\<środowisko uruchomieniowe > — Element  
\<etwEnabled >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<etwEnable enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|włączone|Atrybut wymagany.<br /><br /> Określa, czy powinno być włączone ETW.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|true|Włączanie funkcji ETW. Jest to wartość domyślna dla wersji systemu Windows, począwszy od systemów operacyjnych Windows Vista i Windows Server 2008.|  
|false|Wyłączanie funkcji ETW. Jest to wartość domyślna dla wcześniejszych wersji systemu Windows.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
 Począwszy od systemu Windows Vista, ETW jest domyślnie włączona. Ten element służy do wyłączenia funkcji ETW dla aplikacji. We wcześniejszych wersjach systemu Windows użyj tego elementu, aby włączyć ETW dla aplikacji.  
  
> [!NOTE]
>  ETW można włączać lub globalnie wyłączone na serwerze za pomocą ustawienia rejestru. Zobacz [kontrolowanie .NET Framework rejestrowania](../../../../../docs/framework/performance/controlling-logging.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak włączyć śledzenie zdarzeń systemu Windows dla aplikacji.  
  
```xml  
<configuration>  
   <runtime>  
      <etwEnable enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Kontrolowanie logowania w programie .NET Framework](../../../../../docs/framework/performance/controlling-logging.md)
