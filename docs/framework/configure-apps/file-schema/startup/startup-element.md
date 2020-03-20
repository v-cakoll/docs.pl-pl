---
title: <startup>, element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup
- http://schemas.microsoft.com/.NetConfiguration/v2.0#startup
helpviewer_keywords:
- container tags, <startup> element
- <startup> element
- startup element
ms.assetid: 536acfd8-f827-452f-838a-e14fa3b87621
ms.openlocfilehash: e936c069275bfa9f7ac81ef1c6fc6228828182a8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153737"
---
# <a name="startup-element"></a>\<element> uruchamiania

Określa informacje o uruchamianiu środowiska wykonawczego języka wspólnego.

[**\<>konfiguracyjne**](../configuration-element.md)  
&nbsp;&nbsp;**\<>uruchamiania**  

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
|`useLegacyV2RuntimeActivationPolicy`|Atrybut opcjonalny.<br /><br /> Określa, czy włączyć zasady aktywacji środowiska uruchomieniowego programu .NET Framework 2.0, czy użyć zasad aktywacji programu .NET Framework 4.|

## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a>useLegacyV2RuntimeActivationPolicy atrybut

|Wartość|Opis|
|-----------|-----------------|
|`true`|Włącz zasady aktywacji środowiska uruchomieniowego .NET Framework 2.0 dla wybranego środowiska uruchomieniowego, które mają powiązać starsze techniki aktywacji środowiska uruchomieniowego (takie jak [funkcja CorBindToRuntimeEx)](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)ze środowiska wykonawczego wybranego z pliku konfiguracyjnego zamiast ograniczać je w wersji CLR 2.0. W związku z tym jeśli clr w wersji 4 lub nowszej jest wybrany z pliku konfiguracji, zestawy w trybie mieszanym utworzone z wcześniejszych wersji programu .NET Framework są ładowane z wybraną wersją CLR. Ustawienie tej wartości zapobiega wczytywanie clr w wersji 1.1 lub CLR w wersji 2.0 do tego samego procesu, skutecznie wyłączając funkcję w procesie obok siebie.|
|`false`|Użyj domyślnych zasad aktywacji dla programu .NET Framework 4 lub nowszych, które umożliwiają starsze techniki aktywacji środowiska uruchomieniowego w celu załadowania do procesu programu CLR w wersji 1.1 lub 2.0. Ustawienie tej wartości zapobiega zestawom w trybie mieszanym ładowania do programu .NET Framework 4 lub nowszego, chyba że zostały one utworzone za pomocą programu .NET Framework 4 lub nowszego. Ta wartość jest domyślna.|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[\<wymaganeRuntime>](requiredruntime-element.md)|Określa, że aplikacja obsługuje tylko wersję 1.0 środowiska wykonawczego języka wspólnego. Aplikacje utworzone w wersji 1.1 lub ** \<** nowszej powinny używać obsługiwanego elementu>.|
|[\<obsługiwaneRuntime>](supportedruntime-element.md)|Określa wersje środowiska uruchomieniowego języka wspólnego, które obsługuje aplikacja.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|

## <a name="remarks"></a>Uwagi

 ** \<Obsługiwanyruntime>** element powinien być używany przez wszystkie aplikacje utworzone przy użyciu wersji 1.1 lub nowszej środowiska wykonawczego. Aplikacje utworzone w celu obsługi tylko wersji 1.0 środowiska wykonawczego należy użyć ** \<wymaganeRuntime>** element.

 Kod startowy aplikacji hostowanego w programie Microsoft Internet Explorer ignoruje element ** \<>uruchamiania** i jego elementy podrzędne.

## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a>Atrybut useLegacyV2RuntimeActivationPolicy

 Ten atrybut jest przydatny, jeśli aplikacja używa starszych ścieżek aktywacji, takich jak [Funkcja CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), i chcesz, aby te ścieżki aktywować wersję 4 programu CLR zamiast wcześniejszej wersji lub jeśli aplikacja jest zbudowana za pomocą programu .NET Framework 4, ale ma zależność od zestawu trybu mieszanego utworzonego z wcześniejszą wersją programu .NET Framework. W tych scenariuszach ustaw atrybut `true`na .

> [!NOTE]
> Ustawienie atrybutu `true` zapobiega ładowaniu clr w wersji 1.1 lub CLR w wersji 2.0 do tego samego procesu, skutecznie wyłączając funkcję side-by-side w procesie (patrz [Wykonanie side-by-Side dla COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))).

## <a name="example"></a>Przykład

 W poniższym przykładzie pokazano, jak określić wersję środowiska wykonawczego w pliku konfiguracyjnym.

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

- [Schemat ustawień uruchamiania](index.md)
- [Schemat pliku konfiguracji](../index.md)
- [Jak: Konfigurowanie aplikacji do obsługi wersji programu .NET Framework 4 lub nowszych](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- [Wykonanie side-by-side dla com interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))
- [Wykonywanie równoczesne i wewnątrzprocesowe](../../../deployment/in-process-side-by-side-execution.md)
