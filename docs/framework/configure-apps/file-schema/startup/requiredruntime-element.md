---
title: '&lt;requiredRuntime&gt; — Element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requiredRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/requiredRuntime
helpviewer_keywords:
- requiredRuntime element
- <requiredRuntime> element
- container tags, <requiredRuntime> element
ms.assetid: 9fa1639e-beb8-43be-b7a4-12f7b229c34b
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: ac1e1f7bc36d8d2b12b99de2794bb0ba31ddbd7a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43518650"
---
# <a name="ltrequiredruntimegt-element"></a>&lt;requiredRuntime&gt; — Element
Określa, że aplikacja obsługuje tylko wersję 1.0 środowiska uruchomieniowego języka wspólnego. Ten element jest przestarzała i nie powinna być używana. [ `supportedRuntime` ](supportedruntime-element.md) Zamiast tego należy użyć elementu.
  
 \<Konfiguracja >  
\<startup>  
\<requiredRuntime >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
   <requiredRuntime    
version="runtime version"  
safemode="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`version`|Atrybut opcjonalny.<br /><br /> Wartość ciągu określająca wersję programu .NET Framework, którą obsługuje ta aplikacja. Wartość ciągu musi odpowiadać nazwa katalogu znajdują się w katalogu głównym instalacji .NET Framework. Zawartość wartości ciągu nie są analizowane.|  
|`safemode`|Atrybut opcjonalny.<br /><br /> Określa, czy kod uruchamiający środowisko uruchomieniowe wyszukuje rejestr w celu ustalenia wersji środowiska uruchomieniowego.|  
  
## <a name="safemode-attribute"></a>safemode — atrybut  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`false`|Kod uruchamiający środowisko uruchomieniowe wyszukuje w rejestrze. Jest to wartość domyślna.|  
|`true`|Kod startowy środowiska uruchomieniowego nie znajduje się w rejestrze.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`startup`|Zawiera `<requiredRuntime>` elementu.|  
  
## <a name="remarks"></a>Uwagi  
 Aplikacje stworzone z myślą o obsługiwały tylko wersję 1.0 środowiska uruchomieniowego muszą używać `<requiredRuntime>` elementu. Aplikacje utworzone przy użyciu wersji 1.1 lub nowszej środowiska uruchomieniowego muszą używać `<supportedRuntime>` elementu.  
  
> [!NOTE]
>  Jeśli używasz [CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md) funkcji, aby określić plik konfiguracji, należy użyć `<requiredRuntime>` elementu dla wszystkich wersji środowiska uruchomieniowego. `<supportedRuntime>` Element jest ignorowany, gdy używasz [CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md).  
  
 `version` Ciągu atrybutu musi odpowiadać nazwie folder instalacji dla określonej wersji programu .NET Framework. Ten ciąg nie jest interpretowany. Jeśli kod startowy środowiska uruchomieniowego nie znajdzie folderem dopasowania, środowisko uruchomieniowe nie jest załadowany; kod startowy pokazuje komunikat o błędzie i kończy działanie.  
  
> [!NOTE]
>  Ignoruje kodu startowego dla aplikacji, która jest obsługiwana w programie Internet Explorer `<requiredRuntime>` elementu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak określić wersji środowiska uruchomieniowego w pliku konfiguracji.  
  
```xml  
<configuration>  
   <startup>  
      <requiredRuntime version="v1.0.3705" safemode="true"/>  
   </startup>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Schemat ustawień uruchamiania](../../../../../docs/framework/configure-apps/file-schema/startup/index.md)  
 [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<PaveOver > Określanie wersji środowiska uruchomieniowego, które ma być używana](https://msdn.microsoft.com/library/c376208d-980d-42b4-865b-fbe0d9cc97c2)
