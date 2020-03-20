---
title: <supportedRuntime>element konfiguracyjny - .NET
ms.date: 04/02/2019
ms.custom: updateeachrelease
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#supportedRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/supportedRuntime
helpviewer_keywords:
- supportedRuntime element
- <supportedRuntime> element
ms.assetid: 1ae16e23-afbe-4de4-b413-bc457f37b69f
ms.openlocfilehash: e16eb098db4bce115a5f1e043829eb272c952860
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153701"
---
# <a name="supportedruntime-element"></a>\<supportedRuntime> element

Określa, która wersja wspólnego środowiska wykonawczego języka i opcjonalnie wersja programu .NET Framework jest dostępna dla aplikacji.  

[\<>konfiguracyjne](../configuration-element.md)  
&nbsp;&nbsp;[\<>uruchamiania](startup-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<obsługiwaneRuntime>**  

## <a name="syntax"></a>Składnia

```xml
<supportedRuntime version="runtime version" sku="sku id"/>
```

## <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|**Wersja**|Atrybut opcjonalny.<br /><br /> Wartość ciągu określająca wersję środowiska uruchomieniowego języka wspólnego (CLR), którą obsługuje ta aplikacja. Aby uzyskać prawidłowe wartości atrybutu, `version` zobacz sekcję wartości ["wersja środowiska wykonawczego".](#version) **Uwaga:**  Za pośrednictwem programu .NET Framework 3.5 wartość "*runtime version*" przyjmuje *główną*formę . *drobne*. *budować*. Począwszy od programu .NET Framework 4 wymagane są tylko główne i pomocnicze numery wersji (czyli "v4.0" zamiast "v4.0.30319"). Zalecane jest użycie krótszego ciągu.|
|**Numer jednostki magazynowej**|Atrybut opcjonalny.<br /><br /> Wartość ciągu, która określa jednostkę przechowywania zapasów (SKU), która z kolei określa, które .NET Framework wersji tej aplikacji obsługuje.<br /><br /> Począwszy od programu .NET Framework 4.0, zaleca się użycie atrybutu. `sku`  Gdy jest obecny, wskazuje wersję programu .NET Framework, który jest przeznaczony dla aplikacji.<br /><br /> Prawidłowe wartości atrybutu sku można znaleźć w sekcji [wartości "sku id".](#sku)|

## <a name="remarks"></a>Uwagi

Jeśli ** \<obsługiwanyruntime>** element nie jest obecny w pliku konfiguracji aplikacji, używana jest wersja środowiska wykonawczego używanego do tworzenia aplikacji.

** \<Obsługiwanyruntime>** element powinien być używany przez wszystkie aplikacje utworzone przy użyciu wersji 1.1 lub nowszej środowiska wykonawczego. Aplikacje utworzone w celu obsługi tylko wersji 1.0 środowiska wykonawczego należy użyć [ \<wymaganeRuntime>](../startup/requiredruntime-element.md) element.

> [!NOTE]
> Jeśli używasz [Funkcji CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) do określenia pliku konfiguracji, należy użyć `<requiredRuntime>` elementu dla wszystkich wersji środowiska wykonawczego. Element `<supportedRuntime>` jest ignorowany podczas korzystania z [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md).  
  
W przypadku aplikacji obsługujących wersje środowiska wykonawczego z platformy .NET Framework od 1.1 do 3.5, gdy obsługiwanych jest wiele wersji środowiska wykonawczego, pierwszy element powinien określać najbardziej preferowaną wersję środowiska wykonawczego, a ostatni element powinien określać najmniej preferowanej wersji. W przypadku aplikacji obsługujących wersje .NET Framework 4.0 lub nowszych `version` atrybut wskazuje wersję programu CLR, która `sku` jest wspólna dla wersji .NET Framework 4 i nowszych, a atrybut wskazuje pojedynczą wersję programu .NET Framework, która jest przeznaczona dla aplikacji.

Jeśli ** \<obsługiwany element>runtime** z `sku` atrybutem jest obecny w pliku konfiguracyjnym, a zainstalowana wersja programu .NET Framework jest niższa niż określona obsługiwana wersja, aplikacja nie może uruchomić i zamiast tego wyświetla komunikat z prośbą o zainstalowanie obsługiwanej wersji. W przeciwnym razie aplikacja próbuje uruchomić na dowolnej zainstalowanej wersji, ale może zachowywać się nieoczekiwanie, jeśli nie jest w pełni zgodna z tą wersją. (Aby uzyskać różnice w zgodności między wersjami programu .NET Framework, zobacz [Zgodność aplikacji w programie .NET Framework).](https://docs.microsoft.com/dotnet/framework/migration-guide/application-compatibility) W związku z tym zaleca się dołączenie tego elementu do pliku konfiguracji aplikacji dla łatwiejszej diagnostyki błędów. (Plik konfiguracyjny generowany automatycznie przez program Visual Studio podczas tworzenia nowego projektu już go zawiera).
  
> [!NOTE]
> Jeśli aplikacja używa starszych ścieżek aktywacji, takich jak [CorBindToRuntimeEx,](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)i chcesz, aby te ścieżki aktywowały wersję 4 programu CLR zamiast wcześniejszej wersji lub jeśli aplikacja jest zbudowana za pomocą programu .NET Framework 4, ale ma zależność od zestawu trybu mieszanego zbudowanego z wcześniejszą wersją programu .NET Framework, nie wystarczy określić .NET Framework 4 na liście obsługiwanych środowiskach uruchomieniowych. Ponadto w [ \<elemencie> uruchamiania](../startup/startup-element.md) w pliku konfiguracyjnym `useLegacyV2RuntimeActivationPolicy` należy ustawić atrybut na `true`. Jednak ustawienie tego atrybutu oznacza, `true` że wszystkie składniki utworzone z wcześniejszych wersji programu .NET Framework są uruchamiane przy użyciu programu .NET Framework 4 zamiast środowiska wykonawczego, z których zostały zbudowane.

Zalecane jest, aby testować aplikacje z każdą wersją programu .NET Framework, za pomocą której mogą być uruchamiane.

<a name="version"></a>
## <a name="runtime-version-values"></a>"wersja wykonawcza" wartości
Atrybut `runtime` określa wersję środowiska wykonawczego języka wspólnego (CLR), która jest wymagana dla danej aplikacji. Należy zauważyć, że wszystkie wersje programu `v4.0` .NET Framework v4.x określają wartość CLR. W poniższej tabeli wymieniono prawidłowe `version` wartości dla wartości wersji środowiska *wykonawczego* atrybutu.

|Wersja programu .NET Framework|Atrybut `version`|
|----------------------------|-------------------------|
|1.0|"v1.0.3705"|
|1.1|"v1.1.4322"|
|2.0|"v2.0.50727"|
|3.0|"v2.0.50727"|
|3,5|"v2.0.50727"|
|4.0-4.8|"v4.0"|

## <a name="sku-id-values"></a><a name="sku"></a>"sku id" wartości

Atrybut `sku` używa moniker struktury docelowej (TFM), aby wskazać wersję programu .NET Framework, który jest przeznaczony dla aplikacji i wymaga uruchomienia. W poniższej tabeli wymieniono prawidłowe wartości, które są obsługiwane przez `sku` atrybut, począwszy od programu .NET Framework 4.

|Wersja programu .NET Framework|Atrybut `sku`|
|----------------------------|---------------------|
|4.0|". NETFramework,Version=v4.0"|
|4.0, Profil klienta|". NETFramework,Version=v4.0,Profil=Klient"|
|4.0, aktualizacja platformy 1|". NETFramework,Version=v4.0.1"|
|4.0, Profil klienta, aktualizacja 1|". NETFramework,Version=v4.0.1,Profil=Klient"|
|4.0, aktualizacja platformy 2|". NETFramework,Version=v4.0.2"|
|4.0, Profil klienta, aktualizacja 2|". NETFramework,Version=v4.0.2,Profil=Klient"|
|4.0, aktualizacja platformy 3|". NETFramework,Version=v4.0.3"|
|4.0, Profil klienta, aktualizacja 3|". NETFramework,Version=v4.0.3,Profil=Klient"|
|4.5|". NETFramework,Version=v4.5"|
|4.5.1|". NETFramework,Version=v4.5.1"|
|4.5.2|". NETFramework,Version=v4.5.2"|
|4.6|". NETFramework,Version=v4.6"|
|4.6.1|". NETFramework,Version=v4.6.1"|
|4.6.2|". NETFramework,Version=v4.6.2"|
|4.7|". NETFramework,Version=v4.7"|
|4.7.1|". NETFramework,Version=v4.7.1"|
|4.7.2|". NETFramework,Version=v4.7.2"|
|4.8|". NETFramework,Version=v4.8"|

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak określić obsługiwaną wersję środowiska uruchomieniowego w pliku konfiguracyjnym. Plik konfiguracji wskazuje, że aplikacja jest przeznaczona dla programu .NET Framework 4.7.

```xml
<configuration>
   <startup>
      <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7" />
   </startup>
</configuration>
```

## <a name="configuration-file"></a>Plik konfiguracji

Tego elementu można użyć w pliku konfiguracji aplikacji.

## <a name="see-also"></a>Zobacz też

- [Schemat ustawień uruchamiania](../startup/index.md)
- [Schemat pliku konfiguracji](../index.md)
- [Wykonywanie równoczesne i wewnątrzprocesowe](../../../deployment/in-process-side-by-side-execution.md)
