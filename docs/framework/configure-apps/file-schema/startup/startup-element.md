---
title: "&lt;uruchamianie&gt; — Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup
- http://schemas.microsoft.com/.NetConfiguration/v2.0#startup
helpviewer_keywords:
- container tags, <startup> element
- <startup> element
- startup element
ms.assetid: 536acfd8-f827-452f-838a-e14fa3b87621
caps.latest.revision: "19"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: bd2356845c76e81ce2efe87bdf247de293d6115d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltstartupgt-element"></a>&lt;uruchamianie&gt; — Element
Określa uruchamiania informacje CLR.  
  
 \<Konfiguracja >  
\<Uruchamianie >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<startup useLegacyV2RuntimeActivationPolicy="true|false" >   
</startup>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`useLegacyV2RuntimeActivationPolicy`|Atrybut opcjonalny.<br /><br /> Określa, czy włączyć [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] zasad aktywacji środowiska uruchomieniowego lub użyć [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] zasad aktywacji.|  
  
## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a>Atrybut useLegacyV2RuntimeActivationPolicy  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`true`|Włącz [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] zasad wykonywania aktywacji dla wybranego środowiska uruchomieniowego, czyli powiązać techniki aktywacji starszej wersji środowiska uruchomieniowego (takich jak [CorBindToRuntimeEx — funkcja](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)) do środowiska wykonawczego wybrane z pliku konfiguracji zamiast ograniczanie ich w CLR w wersji 2.0. W związku z tym jeśli CLR w wersji 4 lub nowszej jest wybierany z pliku konfiguracji, trybu mieszanego zestawów utworzonych w starszych wersjach programu .NET Framework są ładowane z wybranej wersji środowiska CLR. Ta wartość uniemożliwia CLR w wersji 1.1 lub CLR w wersji 2.0 ładowania do tego samego procesu, efektywne wyłączenie funkcji side-by-side w procesie.|  
|`false`|Użyj domyślnych zasad aktywacji dla [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] i później, która umożliwia starszej wersji środowiska uruchomieniowego techniki aktywacji można załadować w procesie CLR w wersji 1.1 lub 2.0. Ustawienie tej wartości zapobiega zestawy trybu mieszanego ładowania do programu .NET Framework 4 lub nowszy, chyba że zostały one skompilowane z programu .NET Framework 4 lub nowszym. Ta wartość jest ustawieniem domyślnym.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<requiredRuntime >](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md)|Określa, czy aplikacja obsługuje tylko wersję 1.0 środowisko uruchomieniowe języka wspólnego. Należy użyć aplikacji skompilowanej za pomocą środowiska wykonawczego w wersji 1.1 lub nowszej  **\<supportedRuntime >** elementu.|  
|[\<supportedRuntime >](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)|Określa wersje środowiska uruchomieniowego języka wspólnego, które obsługuje aplikacja.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
  
## <a name="remarks"></a>Uwagi  
 **\<SupportedRuntime >** element powinna być używana przez wszystkie aplikacje utworzone przy użyciu wersji 1.1 lub nowszej środowiska uruchomieniowego. Aplikacje przeznaczone do obsługi tylko wersję 1.0 środowiska uruchomieniowego musi używać  **\<requiredRuntime >** elementu.  
  
 Kod uruchomienia dla aplikacji hostowanej w programie Internet Explorer ignoruje  **\<uruchamiania >** elementu i jego elementów podrzędnych.  
  
## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a>Atrybut useLegacyV2RuntimeActivationPolicy  
 Ten atrybut jest przydatne, jeśli aplikacja używa ścieżek aktywacji starszych wersji [CorBindToRuntimeEx — funkcja](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), i chcesz tych ścieżek do aktywowania zamiast starszej wersji środowiska CLR w wersji 4 lub w przypadku aplikacji zbudowany z [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] ale ma zależność w zestawie trybu mieszanego skompilowanej za pomocą starszej wersji programu .NET Framework. W tych scenariuszach, ustaw dla atrybutu `true`.  
  
> [!NOTE]
>  Ustawienie atrybutu `true` uniemożliwia ładowanie do tego samego procesu, efektywne wyłączenie funkcji side-by-side w trakcie CLR w wersji 1.1 lub CLR w wersji 2.0 (zobacz [Side-by-Side wykonywanie COM Interop](http://msdn.microsoft.com/en-us/4302318c-3586-49bf-8620-b9a39cdf4a32)).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak do określania wersji środowiska uruchomieniowego w pliku konfiguracji.  
  
```xml  
<!-- When used with version 1.0 of the .NET Framework runtime -->  
<configuration>  
   <startup>  
      <requiredRuntime version="v1.0.3705" safemode="true"/>  
   </startup>  
</configuration>  
<!-- When used with version 1.1 (or later) of the runtime -->  
<configuration>  
   <startup>  
      <supportedRuntime version="v1.1.4322"/>  
      <supportedRuntime version="v1.0.3705"/>  
   </startup>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Schemat ustawień uruchamiania](../../../../../docs/framework/configure-apps/file-schema/startup/index.md)  
 [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<PaveOver > Określanie wersji środowiska uruchomieniowego do użycia](http://msdn.microsoft.com/en-us/c376208d-980d-42b4-865b-fbe0d9cc97c2)  
 [Wykonanie Side-by-Side dla międzyoperacyjności z modelem COM](http://msdn.microsoft.com/en-us/4302318c-3586-49bf-8620-b9a39cdf4a32)  
 [W trakcie wykonywania Side-by-Side](../../../../../docs/framework/deployment/in-process-side-by-side-execution.md)
