---
title: '&lt;supportedRuntime&gt; — Element'
ms.date: 04/10/2018
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
ms.openlocfilehash: b6303f765d1cc4a17fe19261c7326d8961ac1080
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53129250"
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
|**version**|Atrybut opcjonalny.<br /><br /> Wartość ciągu określająca wersję środowiska uruchomieniowego języka wspólnego (CLR), którą obsługuje ta aplikacja. Aby uzyskać prawidłowe wartości `version` atrybutów, zobacz [wartości "wersja środowiska uruchomieniowego"](#version) sekcji. **Uwaga:**  Za pomocą programu .NET Framework 3.5 "*wersji środowiska uruchomieniowego*" wartość ma postać *głównych*. *drobne*. *Tworzenie*. Począwszy od [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], tylko wymagane numery wersji głównych i pomocniczych (to znaczy "v4.0" zamiast "v4.0.30319"). Zalecane jest użycie krótszego ciągu.|  
|**sku**|Atrybut opcjonalny.<br /><br /> Wartość ciągu określająca jednostkę magazynową (SKU), który z kolei określa wersji .NET Framework, które obsługuje tę aplikację.<br /><br /> Począwszy od programu .NET Framework 4.0, użycie `sku` atrybutu jest zalecane.  Jeśli jest obecny, oznacza to, wersji systemu .NET Framework, aplikacji jest przeznaczony dla.<br /><br /> Aby uzyskać prawidłowe wartości atrybutu jednostki sku, zobacz [wartości "identyfikatorem jednostki sku"](#sku) sekcji.|  
  
## <a name="remarks"></a>Uwagi

Jeśli  **\<supportedRuntime >** element nie jest obecny w pliku konfiguracyjnym aplikacji, jest używana wersja środowiska uruchomieniowego użytego do skompilowania aplikacji.  

**\<SupportedRuntime >** element powinien być używany przez wszystkie aplikacje kompilowane przy użyciu wersji 1.1 lub nowszej środowiska uruchomieniowego. Aplikacje stworzone z myślą o obsługiwały tylko wersję 1.0 środowiska uruchomieniowego muszą używać [ \<requiredRuntime >](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md) elementu.  
  
> [!NOTE]
>  Jeśli używasz [CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md) funkcji, aby określić plik konfiguracji, należy użyć `<requiredRuntime>` elementu dla wszystkich wersji środowiska uruchomieniowego. `<supportedRuntime>` Element jest ignorowany, gdy używasz [CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md).  
  
W przypadku aplikacji, które obsługują wersje środowiska uruchomieniowego w .NET Framework 1.1 za pośrednictwem 3.5, gdy obsługiwanych wiele wersji środowiska uruchomieniowego, pierwszy element musi określać najbardziej preferowaną wersję środowiska uruchomieniowego i ostatni element musi określać najmniejszej preferowaną wersję. W przypadku aplikacji, które obsługują program .NET Framework 4.0 lub nowszej wersji `version` atrybut wskazuje wersję środowiska CLR, który jest wspólny dla .NET Framework 4 i nowsze wersje, i `sku` atrybut wskazuje jednej wersji .NET Framework, aplikacji obiekty docelowe.  
  
> [!NOTE]
>  Jeśli aplikacja używa ścieżki aktywacji starszej wersji, takich jak [corbindtoruntimeex — funkcja](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), i potrzebujesz tych ścieżek do aktywacji w wersji 4 środowiska CLR zamiast wcześniejszej wersji, czy aplikacja jest kompilowany [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], ale ma zależność od zestawu trybu mieszanego, skompilowanych przy użyciu wcześniejszej wersji programu .NET Framework, nie jest wystarczające, aby określić [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] na liście obsługiwanych środowisk uruchomieniowych. Ponadto w programie [ \<uruchamiania > element](../../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) w pliku konfiguracji, należy ustawić `useLegacyV2RuntimeActivationPolicy` atrybutu `true`. Jednak ustawienie tego atrybutu na `true` oznacza, że wszystkie składniki skompilowane z wcześniejszymi wersjami programu .NET Framework są uruchamiane przy użyciu [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] zamiast zostały skompilowane przy użyciu środowiska uruchomieniowego.  
  
Zalecane jest, aby testować aplikacje z każdą wersją programu .NET Framework, za pomocą której mogą być uruchamiane.  
  
<a name="version"></a>   
## <a name="runtime-version-values"></a>wartości "wersja środowiska uruchomieniowego"  
`runtime` Atrybut określa wersję środowiska uruchomieniowego języka wspólnego (CLR), która jest wymagana dla danej aplikacji. Należy zauważyć, że wszystkie wersje programu .NET Framework v4.x określ `v4.0` CLR. W poniższej tabeli wymieniono prawidłowe wartości dla *wersji środowiska uruchomieniowego* wartość `version` atrybutu.  

|Wersja programu .NET Framework|`version` Atrybut|  
|----------------------------|-------------------------|  
|1.0|"v1.0.3705"|  
|1.1|"v1.1.4322"|  
|2.0|"v2.0.50727"|  
|3.0|"v2.0.50727"|  
|3.5|"v2.0.50727"|  
|4.0 4.7.2|"v4.0"|  

<a name="sku"></a>   
## <a name="sku-id-values"></a>wartości "identyfikatorem jednostki sku"

`sku` Atrybutu używa monikerem platformy docelowej (TFM), aby wskazać wersję programu .NET Framework, który jest przeznaczony dla i wymaga do uruchomienia aplikacji. W poniższej tabeli wymieniono prawidłowe wartości, które są obsługiwane przez `sku` atrybutu, począwszy od programu .NET Framework 4.
  
|Wersja programu .NET Framework|`sku` Atrybut|  
|----------------------------|---------------------|  
|4.0|". NETFramework, Version = v4.0 "|  
|4.0, client Profile|".NETFramework,Version=v4.0,Profile=Client"|  
|Aktualizacja platformy 4.0, 1|". NETFramework, Version = v4.0.1 "|  
|4.0, client Profile, aktualizacja 1|". NETFramework, Version = v4.0.1, profilu klienta = "|  
|4.0, platformy, aktualizacja 2|". NETFramework, Version = v4.0.2 "|  
|4.0, client Profile, aktualizacja 2|". NETFramework, Version = v4.0.2, profilu klienta = "|  
|4.0, platforma update 3|". NETFramework, Version = verze 4.0.3 "|  
|4.0, client Profile, aktualizacja 3|". NETFramework, Version = verze 4.0.3, profilu klienta = "|  
|4.5|". NETFramework, Version = 4.5 "|  
|4.5.1|".NETFramework,Version=v4.5.1"|  
|4.5.2|". NETFramework, Version = v4.5.2 "|  
|4.6|". NETFramework, Version = wersje 4.6 "|  
|4.6.1|". NETFramework, Version = v4.6.1 "|  
|4.6.2|". NETFramework, Version = v4.6.2 "|  
|4.7|". NETFramework, Version = v4.7 na "|
|4.7.1|".NETFramework,Version=v4.7.1"|
|4.7.2|". NETFramework, Version = v4.7.2 "|

## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak określić obsługiwana wersja środowiska uruchomieniowego w pliku konfiguracji. Plik konfiguracyjny wskazuje, że aplikacja jest przeznaczony dla .NET Framework 4.7.  
  
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
