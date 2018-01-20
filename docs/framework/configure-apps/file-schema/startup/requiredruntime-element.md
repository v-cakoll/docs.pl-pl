---
title: "&lt;requiredRuntime&gt; — Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requiredRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/requiredRuntime
helpviewer_keywords:
- requiredRuntime element
- <requiredRuntime> element
- container tags, <requiredRuntime> element
ms.assetid: 9fa1639e-beb8-43be-b7a4-12f7b229c34b
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 2e864eec2ddf51d5cc88110654f6c23f146938d5
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="ltrequiredruntimegt-element"></a>&lt;requiredRuntime&gt; — Element
Określa, czy aplikacja obsługuje tylko wersję 1.0 środowisko uruchomieniowe języka wspólnego. Ten element jest przestarzały i nie będzie można użyć. [ `supportedRuntime` ](supportedruntime-element.md) Elementu należy użyć.
  
 \<configuration>  
\<startup>  
\<requiredRuntime>  
  
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
|`version`|Atrybut opcjonalny.<br /><br /> Wartość ciągu, który określa wersję programu .NET Framework, która obsługuje tę aplikację. Wartość ciągu musi odpowiadać nazwie katalogu znajdują się w katalogu instalacji platformy .NET Framework. Zawartość wartości ciągu nie są przeanalizować.|  
|`safemode`|Atrybut opcjonalny.<br /><br /> Określa, czy kod uruchomienia środowiska uruchomieniowego wyszukuje rejestru można ustalić wersji środowiska wykonawczego.|  
  
## <a name="safemode-attribute"></a>Tryb awaryjny atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`false`|Kod uruchomienia środowiska uruchomieniowego wyszukuje w rejestrze. Jest to wartość domyślna.|  
|`true`|Kod uruchomienia środowiska uruchomieniowego wygląda w rejestrze.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`startup`|Zawiera `<requiredRuntime>` elementu.|  
  
## <a name="remarks"></a>Uwagi  
 Aplikacje przeznaczone do obsługi tylko wersję 1.0 środowiska uruchomieniowego musi używać `<requiredRuntime>` elementu. Należy użyć aplikacji utworzony za pomocą wersji 1.1 lub nowszej środowiska uruchomieniowego `<supportedRuntime>` elementu.  
  
> [!NOTE]
>  Jeśli używasz [CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md) funkcji, aby określić plik konfiguracji, należy użyć `<requiredRuntime>` elementu dla wszystkich wersji środowiska uruchomieniowego. `<supportedRuntime>` Element jest ignorowana, korzystając z [CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md).  
  
 `version` Ciąg atrybutu musi odpowiadać nazwie folder instalacji dla określonej wersji programu .NET Framework. Ten ciąg nie jest interpretowany. Jeśli kod uruchomienia środowiska uruchomieniowego nie może znaleźć pasujących folderu, nie załadowano środowiska uruchomieniowego; Kod uruchomienia zawiera komunikat o błędzie i kończy działanie.  
  
> [!NOTE]
>  Kod uruchomienia dla aplikacji, która jest obsługiwana w programie Internet Explorer ignoruje `<requiredRuntime>` elementu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak do określania wersji środowiska uruchomieniowego w pliku konfiguracji.  
  
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
 [\<PaveOver > Określanie wersji środowiska uruchomieniowego do użycia](http://msdn.microsoft.com/library/c376208d-980d-42b4-865b-fbe0d9cc97c2)
