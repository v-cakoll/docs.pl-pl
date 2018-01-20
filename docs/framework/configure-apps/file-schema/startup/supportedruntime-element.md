---
title: "&lt;supportedRuntime&gt; — Element"
ms.date: 10/17/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
ms.custom: updateeachrelease
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#supportedRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/supportedRuntime
helpviewer_keywords:
- supportedRuntime element
- <supportedRuntime> element
ms.assetid: 1ae16e23-afbe-4de4-b413-bc457f37b69f
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 4b0967790f2bbf8fa9a889c56fa9c5168f7523bd
ms.sourcegitcommit: 8bde7a3432f30fc771079744955c75c58c4eb393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/20/2018
---
# <a name="ltsupportedruntimegt-element"></a>&lt;supportedRuntime&gt; — Element

Określa wersje środowiska uruchomieniowego języka wspólnego, które obsługuje aplikacja. Ten element powinien być używany przez wszystkie aplikacje kompilowane przy użyciu programu .NET Framework w wersji 1.1 i nowszych.  
  
[\<Konfiguracja >](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
&nbsp;&nbsp;[\<startup>](../../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<supportedRuntime >**  
  
## <a name="syntax"></a>Składnia
  
```xml  
<supportedRuntime version="runtime version" sku="sku id"/>  
```  
  
## <a name="attributes"></a>Atrybuty
  
|Atrybut|Opis|  
|---------------|-----------------|  
|**Wersja**|Atrybut opcjonalny.<br /><br /> Wartość ciągu określająca wersję środowiska uruchomieniowego języka wspólnego (CLR), którą obsługuje ta aplikacja. Aby uzyskać prawidłowe wartości `version` atrybutów, zobacz [wartości "wersja środowiska uruchomieniowego"](#version) sekcji. **Uwaga:** za pomocą programu .NET Framework 3.5, "*wersja środowiska uruchomieniowego*" wartość ma postać *głównych*. *drobne*. *Tworzenie*. Począwszy od [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], tylko wymagane numery wersji głównej i pomocniczej (to znaczy "v4.0" zamiast "4.0.30319"). Zalecane jest użycie krótszego ciągu.|  
|**sku**|Atrybut opcjonalny.<br /><br /> Wartość ciągu, która określa jednostka magazynowa (SKU), który z kolei określa wersji .NET Framework, które obsługuje tę aplikację.<br /><br /> Począwszy od programu .NET Framework 4.0, użycie `sku` atrybutu jest zalecane.  Jeśli jest obecny, wskazuje wersję systemu .NET Framework który celów aplikacji.<br /><br /> Prawidłowe wartości atrybutu wersji, zobacz [wartości "identyfikator jednostki sku"](#sku) sekcji.|  
  
## <a name="remarks"></a>Uwagi

Jeśli  **\<supportedRuntime >** element nie jest obecny w pliku konfiguracji aplikacji, używana wersja środowiska uruchomieniowego, używany do tworzenia aplikacji.  

**\<SupportedRuntime >** element powinna być używana przez wszystkie aplikacje utworzone przy użyciu wersji 1.1 lub nowszej środowiska uruchomieniowego. Aplikacje przeznaczone do obsługi tylko wersję 1.0 środowiska uruchomieniowego musi używać [ \<requiredRuntime >](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md) elementu.  
  
> [!NOTE]
>  Jeśli używasz [CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md) funkcji, aby określić plik konfiguracji, należy użyć `<requiredRuntime>` elementu dla wszystkich wersji środowiska uruchomieniowego. `<supportedRuntime>` Element jest ignorowana, korzystając z [CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md).  
  
Dla aplikacji, które obsługuje wersje środowiska uruchomieniowego z za pośrednictwem 3.5, .NET Framework 1.1, gdy wiele wersji środowiska uruchomieniowego są obsługiwane, pierwszy element należy określić najlepszy możliwy wersję środowiska uruchomieniowego i ostatni element powinien określać najmniej Preferowana wersja. Dla aplikacji, które obsługuje programu .NET Framework 4.0 lub nowszy `version` atrybut wskazuje wersji środowiska CLR, który jest wspólny dla platformy .NET Framework 4 i nowsze wersje, i `sku` atrybut wskazuje jednej wersji .NET Framework który aplikacji obiekty docelowe.  
  
> [!NOTE]
>  Jeśli aplikacja używa aktywacji starszych wersji ścieżek, takich jak [CorBindToRuntimeEx — funkcja](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), i chcesz tych ścieżek do aktywowania zamiast starszej wersji środowiska CLR w wersji 4 lub jeśli aplikacja jest zbudowany z [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], ale ma zależność w zestawie trybu mieszanego skompilowanej za pomocą starszej wersji programu .NET Framework nie jest wystarczające, aby określić [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] na liście obsługiwanych środowisk uruchomieniowych. Ponadto w [ \<uruchamiania > element](../../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) w pliku konfiguracji, należy ustawić `useLegacyV2RuntimeActivationPolicy` atrybutu `true`. Jednak ustawienie tego atrybutu na `true` oznacza, że wszystkie składniki skompilowane z wcześniejszymi wersjami programu .NET Framework są uruchamiane przy użyciu [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] zamiast runtimes zostały skompilowane.  
  
Zalecane jest, aby testować aplikacje z każdą wersją programu .NET Framework, za pomocą której mogą być uruchamiane.  
  
<a name="version"></a>   
## <a name="runtime-version-values"></a>"wersja środowiska uruchomieniowego" wartości  
`runtime` Atrybut określa wersję środowiska uruchomieniowego języka wspólnego (CLR), która jest wymagana dla danej aplikacji. Należy pamiętać, że wszystkie wersje v4.x .NET Framework określ `v4.0` CLR. Poniższa tabela zawiera listę prawidłowych wartości dla *wersja środowiska uruchomieniowego* wartość `version` atrybutu.  

|Wersja programu .NET Framework|`version`atrybut|  
|----------------------------|-------------------------|  
|1.0|"v1.0.3705"|  
|1.1|"v1.1.4322"|  
|2.0|"v2.0.50727"|  
|3.0|"v2.0.50727"|  
|3.5|"v2.0.50727"|  
|4.0-4.7.1|"v4.0"|  

<a name="sku"></a>   
## <a name="sku-id-values"></a>wartości "identyfikator jednostki sku"

`sku` Atrybut używa moniker platformy docelowej (TFM) w celu wskazania wersji programu .NET Framework, która dotyczy i wymaga do uruchomienia aplikacji. W poniższej tabeli przedstawiono prawidłowe wartości, które są obsługiwane przez `sku` atrybutu, począwszy od programu .NET Framework 4.
  
|Wersja programu .NET Framework|`sku`atrybut|  
|----------------------------|---------------------|  
|4.0|".NETFramework,Version=v4.0"|  
|4.0, profil klienta|".NETFramework,Version=v4.0,Profile=Client"|  
|4.0, platform update 1|.NETFramework,Version=v4.0.1|  
|4.0, profil klienta, aktualizacja 1|.NETFramework,Version=v4.0.1,Profile=Client|  
|4.0, platform update 2|.NETFramework,Version=v4.0.2|  
|4.0, profil klienta, aktualizacja 2|.NETFramework,Version=v4.0.2,Profile=Client|  
|4.0, platform update 3|.NETFramework,Version=v4.0.3|  
|4.0, profil klienta, aktualizacja 3|.NETFramework,Version=v4.0.3,Profile=Client|  
|4.5|".NETFramework,Version=v4.5"|  
|4.5.1|".NETFramework,Version=v4.5.1"|  
|4.5.2|".NETFramework,Version=v4.5.2"|  
|4.6|". NETFramework, Version = 4.6 "|  
|4.6.1|". NETFramework, Version = v4.6.1 "|  
|4.6.2|". NETFramework, Version = v4.6.2 "|  
|4.7|". NETFramework, Version = v4.7 "|
|4.7.1|".NETFramework,Version=v4.7.1"|

## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak do określania wersji środowiska uruchomieniowego obsługiwanych w pliku konfiguracji. Plik konfiguracji wskazuje, że aplikacja jest przeznaczony dla .NET Framework 4.7.  
  
```xml  
<configuration>  
   <startup>  
      <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7" />  
   </startup>  
</configuration>  
```  
  
## <a name="configuration-file"></a>Plik konfiguracji

Tego elementu można użyć w pliku konfiguracji aplikacji.

## <a name="see-also"></a>Zobacz także

 [Schemat ustawień uruchamiania](../../../../../docs/framework/configure-apps/file-schema/startup/index.md)  
 [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Wykonywanie równoczesne i wewnątrzprocesowe](../../../../../docs/framework/deployment/in-process-side-by-side-execution.md)  
