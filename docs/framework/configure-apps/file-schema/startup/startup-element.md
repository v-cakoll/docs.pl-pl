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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153737"
---
# <a name="startup-element"></a>\<startup>, element

Określa informacje uruchamiania środowiska uruchomieniowego języka wspólnego.

[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<startup>**  

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
|`useLegacyV2RuntimeActivationPolicy`|Atrybut opcjonalny.<br /><br /> Określa, czy włączyć zasady aktywacji środowiska uruchomieniowego .NET Framework 2,0 lub użyć zasad aktywacji .NET Framework 4.|

## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a>useLegacyV2RuntimeActivationPolicy — atrybut

|Wartość|Opis|
|-----------|-----------------|
|`true`|Włącz zasady aktywacji środowiska uruchomieniowego .NET Framework 2,0 dla wybranego środowiska uruchomieniowego, czyli powiązać starsze techniki aktywacji w środowisku uruchomieniowym (takie jak [Funkcja CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)) w środowisku uruchomieniowym wybranym z pliku konfiguracji zamiast przeznaczyć je na środowisko CLR w wersji 2,0. W takim przypadku, jeśli środowisko CLR w wersji 4 lub nowszej zostanie wybrane z pliku konfiguracji, zestawy w trybie mieszanym utworzone przy użyciu wcześniejszych wersji .NET Framework są ładowane z wybraną wersją środowiska CLR. Ustawienie tej wartości uniemożliwia załadowanie środowiska CLR w wersji 1,1 lub 2,0 CLR w ramach tego samego procesu, co skutecznie wyłącza funkcję równoczesną w procesie.|
|`false`|Użyj domyślnych zasad aktywacji dla .NET Framework 4 i nowszych, co umożliwia stosowanie starszych technik aktywacji środowiska uruchomieniowego w celu załadowania środowiska CLR w wersji 1,1 lub 2,0 do procesu. Ustawienie tej wartości uniemożliwia ładowanie zestawów w trybie mieszanym do .NET Framework 4 lub nowszego, chyba że zostały skompilowane przy użyciu .NET Framework 4 lub nowszego. Ta wartość jest domyślna.|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[\<requiredRuntime>](requiredruntime-element.md)|Określa, że aplikacja obsługuje tylko wersję 1,0 środowiska uruchomieniowego języka wspólnego. Aplikacje skompilowane przy użyciu środowiska uruchomieniowego w wersji 1,1 lub nowszej powinny używać **\<supportedRuntime>** elementu.|
|[\<supportedRuntime>](supportedruntime-element.md)|Określa wersje środowiska uruchomieniowego języka wspólnego, które obsługuje aplikacja.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|

## <a name="remarks"></a>Uwagi

 **\<supportedRuntime>** Element powinien być używany przez wszystkie aplikacje skompilowane przy użyciu wersji 1,1 lub nowszej środowiska uruchomieniowego. Aplikacje skompilowane do obsługi tylko wersji 1,0 środowiska uruchomieniowego muszą używać **\<requiredRuntime>** elementu.

 Kod uruchamiania aplikacji hostowanej w programie Microsoft Internet Explorer ignoruje **\<startup>** element i jego elementy podrzędne.

## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a>Atrybut useLegacyV2RuntimeActivationPolicy

 Ten atrybut jest przydatny, jeśli aplikacja używa starszych ścieżek aktywacji, takich jak [Funkcja CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), i chcesz, aby te ścieżki uaktywniali wersję 4 środowiska CLR zamiast wcześniejszej wersji, lub jeśli aplikacja została skompilowana przy użyciu .NET Framework 4, ale ma zależność od zestawu w trybie mieszanym skompilowanego z wcześniejszą wersją .NET Framework. W tych scenariuszach należy ustawić atrybut na `true` .

> [!NOTE]
> Ustawienie atrybutu w celu `true` uniemożliwienia załadowania środowiska CLR w wersji 1,1 lub CLR w wersji 2,0 do tego samego procesu, co skutecznie wyłącza wbudowane funkcje równoległe (zobacz [Wykonywanie równoczesne dla międzyoperacyjności modelu COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))).

## <a name="example"></a>Przykład

 Poniższy przykład pokazuje, jak określić wersję środowiska uruchomieniowego w pliku konfiguracji.

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

## <a name="see-also"></a>Zobacz także

- [Schemat ustawień uruchamiania](index.md)
- [Schemat pliku konfiguracji](../index.md)
- [Instrukcje: Konfigurowanie aplikacji do obsługi .NET Framework 4 lub nowszej wersji](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- [Wykonywanie równoczesne dla współdziałania z modelem COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))
- [Wykonywanie równoczesne i wewnątrzprocesowe](../../../deployment/in-process-side-by-side-execution.md)
