---
title: <supportedRuntime> element konfiguracji — platforma .NET
ms.date: 04/02/2019
ms.custom: updateeachrelease
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#supportedRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/supportedRuntime
helpviewer_keywords:
- supportedRuntime element
- <supportedRuntime> element
ms.assetid: 1ae16e23-afbe-4de4-b413-bc457f37b69f
ms.openlocfilehash: 5e7fc5f81468ff7c4eba8145ee42a4c7cf8bc0b8
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697522"
---
# <a name="supportedruntime-element"></a>\<element > supportedRuntime

Określa, która wersja środowiska uruchomieniowego języka wspólnego i, opcjonalnie, .NET Framework wersji aplikacji.  

[> konfiguracji \<](../configuration-element.md)  
&nbsp;&nbsp;[\<startup>](startup-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp; **\<supportedRuntime >**  

## <a name="syntax"></a>Składnia

```xml
<supportedRuntime version="runtime version" sku="sku id"/>
```

## <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|**version**|Atrybut opcjonalny.<br /><br /> Wartość ciągu określająca wersję środowiska uruchomieniowego języka wspólnego (CLR), którą obsługuje ta aplikacja. Prawidłowe wartości atrybutu `version` można znaleźć w sekcji [wartości "wersja środowiska uruchomieniowego"](#version) . **Uwaga:**  W .NET Framework 3,5 wartość "*wersja środowiska uruchomieniowego*" przyjmuje postać *główną*. *pomocnicze*. *kompilacja*. Począwszy od .NET Framework 4, wymagane są tylko główne i pomocnicze numery wersji (czyli "v 4.0" zamiast "v 4.0.30319"). Zalecane jest użycie krótszego ciągu.|
|**sku**|Atrybut opcjonalny.<br /><br /> Wartość ciągu określająca jednostkę magazynową (SKU), która z kolei określa, która .NET Framework wersja obsługiwana przez tę aplikację.<br /><br /> Począwszy od .NET Framework 4,0 zaleca się użycie atrybutu `sku`.  Gdy jest obecny, wskazuje wersję .NET Framework, do której odwołuje się aplikacja.<br /><br /> Prawidłowe wartości atrybutu SKU można znaleźć w sekcji [wartości "identyfikator jednostki SKU"](#sku) .|

## <a name="remarks"></a>Uwagi

Jeśli w pliku konfiguracji aplikacji nie ma elementu **\<supportedRuntime >** , używana jest wersja środowiska uruchomieniowego użyta do skompilowania aplikacji.

Element **\<supportedRuntime >** powinien być używany przez wszystkie aplikacje skompilowane przy użyciu wersji 1,1 lub nowszej środowiska uruchomieniowego. Aplikacje skompilowane w celu obsługi tylko wersji 1,0 środowiska uruchomieniowego muszą używać elementu [\<requiredRuntime >](../startup/requiredruntime-element.md) .

> [!NOTE]
> W przypadku użycia funkcji [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) w celu określenia pliku konfiguracji należy użyć elementu `<requiredRuntime>` dla wszystkich wersji środowiska uruchomieniowego. Element `<supportedRuntime>` jest ignorowany w przypadku korzystania z [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md).  
  
W przypadku aplikacji, które obsługują wersje środowiska uruchomieniowego z .NET Framework 1,1 do 3,5, gdy obsługiwane są wiele wersji środowiska uruchomieniowego, pierwszy element powinien określać najbardziej preferowaną wersję środowiska uruchomieniowego, a ostatni powinien określać najmniejszy preferowana wersja. W przypadku aplikacji, które obsługują .NET Framework 4,0 lub nowsze wersje, atrybut `version` wskazuje wersję środowiska CLR, która jest wspólna dla .NET Framework 4 i nowszych wersji, a atrybut `sku` wskazuje na jedną .NET Framework wersję, która jest przeznaczona dla aplikacji. 

Jeśli element **\<supportedRuntime >** z atrybutem `sku` jest obecny w pliku konfiguracji, a zainstalowana wersja .NET Framework jest niższa niż określona obsługiwana wersja, aplikacja nie zostanie uruchomiona, a zamiast tego zostanie wyświetlony komunikat z prośbą o zainstalowanie obsługiwanej wersji. W przeciwnym razie aplikacja próbuje uruchomić się w dowolnej zainstalowanej wersji, ale może zachowywać się nieoczekiwanie, jeśli nie jest w pełni zgodna z tą wersją. (Aby uzyskać różnice zgodności między wersjami .NET Framework, zobacz [zgodność aplikacji w .NET Framework](https://docs.microsoft.com/dotnet/framework/migration-guide/application-compatibility)). W związku z tym zaleca się dołączenie tego elementu w pliku konfiguracji aplikacji w celu ułatwienia diagnostyki błędów. (Plik konfiguracji jest generowany automatycznie przez program Visual Studio podczas tworzenia nowego projektu.)
  
> [!NOTE]
> Jeśli aplikacja używa starszych ścieżek aktywacji, takich jak [Funkcja CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), i chcesz, aby te ścieżki uaktywniali wersję 4 środowiska CLR zamiast wcześniejszej wersji, lub jeśli aplikacja została skompilowana przy użyciu .NET Framework 4, ale ma zależność od zestawu w trybie mieszanym skompilowanego z wcześniejszą wersją .NET Framework, nie wystarczy określić .NET Framework 4 na liście obsługiwanych środowisk uruchomieniowych. Ponadto w pliku konfiguracji [\<> uruchamiania](../startup/startup-element.md) , należy ustawić atrybut `useLegacyV2RuntimeActivationPolicy` na `true`. Jednak ustawienie tego atrybutu na `true` oznacza, że wszystkie składniki skompilowane ze starszymi wersjami .NET Framework są uruchamiane przy użyciu .NET Framework 4 zamiast środowisk uruchomieniowych, z których zostały skompilowane.

Zalecane jest, aby testować aplikacje z każdą wersją programu .NET Framework, za pomocą której mogą być uruchamiane.

<a name="version"></a> 
## <a name="runtime-version-values"></a>wartości "wersja środowiska uruchomieniowego"
Atrybut `runtime` określa wersję środowiska uruchomieniowego języka wspólnego (CLR), która jest wymagana dla danej aplikacji. Należy pamiętać, że wszystkie wersje .NET Framework v4. x określają `v4.0` CLR. W poniższej tabeli wymieniono prawidłowe wartości dla wartości *wersja środowiska uruchomieniowego* atrybutu `version`.

|Wersja programu .NET Framework|atrybut `version`|
|----------------------------|-------------------------|
|1.0|"v1.0.3705"|
|1.1|"v1.1.4322"|
|2.0|"v2.0.50727"|
|3.0|"v2.0.50727"|
|3.5|"v2.0.50727"|
|4.0 — 4.8|"v4.0"|

## <a name="sku"></a>wartości "identyfikator jednostki SKU"

Atrybut `sku` używa monikera platformy docelowej (TFM) w celu wskazania wersji .NET Framework, której aplikacja jest przeznaczona do uruchomienia. W poniższej tabeli wymieniono prawidłowe wartości, które są obsługiwane przez atrybut `sku`, począwszy od .NET Framework 4.

|Wersja programu .NET Framework|atrybut `sku`|
|----------------------------|---------------------|
|4.0|". NETFramework, wersja = v 4.0 "|
|4,0, profil klienta|".NETFramework,Version=v4.0,Profile=Client"|
|4,0, Aktualizacja platformy 1|". NETFramework, Version = v 4.0.1 "|
|4,0, profil klienta, aktualizacja 1|". NETFramework, Version = v 4.0.1, profil = klient "|
|4,0, Aktualizacja platformy 2|". NETFramework, Version = v 4.0.2 "|
|4,0, profil klienta, aktualizacja 2|". NETFramework, Version = v 4.0.2, profil = klient "|
|4,0, Aktualizacja platformy 3|". NETFramework, Version = v 4.0.3 "|
|4,0, profil klienta, Aktualizacja Update 3|". NETFramework, Version = v 4.0.3, profil = klient "|
|4.5|". NETFramework, wersja = v 4.5|
|4.5.1|".NETFramework,Version=v4.5.1"|
|4.5.2|". NETFramework, wersja = v 4.5.2|
|4.6|". NETFramework, Version = v 4.6|
|4.6.1|". NETFramework, wersja = v 4.6.1|
|4.6.2|". NETFramework, Version = v 4.6.2 "|
|4.7|". NETFramework, wersja = v 4.7|
|4.7.1|".NETFramework,Version=v4.7.1"|
|4.7.2|". NETFramework, Version = v 4.7.2 "|
|4.8|". NETFramework, wersja = v 4.8|

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak określić obsługiwaną wersję środowiska uruchomieniowego w pliku konfiguracji. Plik konfiguracji wskazuje, że aplikacja jest przeznaczona dla .NET Framework 4,7.

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

- [Schemat ustawień uruchamiania](../startup/index.md)
- [Schemat pliku konfiguracji](../index.md)
- [Wykonywanie równoczesne i wewnątrzprocesowe](../../../deployment/in-process-side-by-side-execution.md)
