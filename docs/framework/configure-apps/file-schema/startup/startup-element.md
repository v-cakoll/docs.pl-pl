---
title: '&lt;uruchamianie&gt; — element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup
- http://schemas.microsoft.com/.NetConfiguration/v2.0#startup
helpviewer_keywords:
- container tags, <startup> element
- <startup> element
- startup element
ms.assetid: 536acfd8-f827-452f-838a-e14fa3b87621
ms.openlocfilehash: 9fc5a555085369cdec249eb9b5b247f403bd12ed
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/26/2019
ms.locfileid: "55083720"
---
# <a name="ltstartupgt-element"></a>&lt;uruchamianie&gt; — element

Określa informacje o uruchamianiu środowisko uruchomieniowe wspólnego języka.

 \<Konfiguracja > \<uruchamiania >

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
|`true`|Włącz [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] środowiska uruchomieniowego zasad aktywacji dla wybranego środowiska uruchomieniowego, czyli można powiązać technik aktywacji starszej wersji środowiska uruchomieniowego (takie jak [corbindtoruntimeex — funkcja](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)) do środowiska uruchomieniowego, wybrana z pliku konfiguracji zamiast Ograniczanie je na wersji CLR 2.0. W związku z tym Jeśli wersja środowiska CLR 4 lub nowszego jest wybierany z pliku konfiguracji, zestawy mieszane utworzonych w starszych wersjach programu .NET Framework są ładowane z wybranej wersji środowiska CLR. Ustawienie tej wartości zapobiega środowisko CLR w wersji 1.1 lub środowisko CLR w wersji 2.0 ładowanie do tego samego procesu i efektywne wyłączenie funkcji side-by-side w procesie.|
|`false`|Użyj domyślnych zasad aktywacji dla [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] i nowszy, która umożliwia starszej wersji środowiska uruchomieniowego technik aktywacji można załadować środowiska CLR w wersji 1.1 lub 2.0 do procesu. Ta wartość zapobiega zestawy mieszane ładowanie do programu .NET Framework 4 lub nowszy, chyba że zostały skompilowane przy użyciu programu .NET Framework 4 lub nowszej. Ta wartość jest domyślna.|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[\<requiredRuntime>](requiredruntime-element.md)|Określa, że aplikacja obsługuje tylko wersję 1.0 środowiska uruchomieniowego języka wspólnego. Skorzystaj z aplikacji utworzonych za pomocą środowiska uruchomieniowego wersji 1.1 lub nowszej  **\<supportedRuntime >** elementu.|
|[\<supportedRuntime>](supportedruntime-element.md)|Określa wersje środowiska uruchomieniowego języka wspólnego, które obsługuje aplikacja.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|

## <a name="remarks"></a>Uwagi

  **\<SupportedRuntime >** element powinien być używany przez wszystkie aplikacje kompilowane przy użyciu wersji 1.1 lub nowszej środowiska uruchomieniowego. Aplikacje stworzone z myślą o obsługiwały tylko wersję 1.0 środowiska uruchomieniowego muszą używać  **\<requiredRuntime >** elementu.

 Ignoruje kodu startowego dla aplikacji hostowanej w programie Internet Explorer  **\<uruchamiania >** elementu i jego elementy podrzędne.

## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a>Atrybut useLegacyV2RuntimeActivationPolicy

 Ten atrybut jest przydatna, jeśli aplikacja używa ścieżki aktywacji starszych [corbindtoruntimeex — funkcja](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), i potrzebujesz tych ścieżek do aktywacji w wersji 4 środowiska CLR zamiast wcześniejszej wersji, czy aplikacja jest utworzonych za pomocą [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] ale ma zależność od zestawu trybu mieszanego, skompilowanych przy użyciu wcześniejszej wersji programu .NET Framework. W tych scenariuszach atrybut na `true`.

> [!NOTE]
> Ustawienie atrybutu `true` uniemożliwia ładowanie do tego samego procesu i efektywne wyłączenie funkcji side-by-side w trakcie środowisko CLR w wersji 1.1 lub środowisko CLR w wersji 2.0 (zobacz [Side-by-Side wykonywania COM Interop](https://msdn.microsoft.com/library/4302318c-3586-49bf-8620-b9a39cdf4a32)).

## <a name="example"></a>Przykład

 Poniższy przykład pokazuje, jak określić wersji środowiska uruchomieniowego w pliku konfiguracji.

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
- [Instrukcje: Konfigurowanie aplikacji do obsługi w programie .NET Framework 4 lub nowszy](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- [Wykonanie Side-by-Side dla współdziałania z modelem COM](https://msdn.microsoft.com/library/4302318c-3586-49bf-8620-b9a39cdf4a32)
- [Wykonywanie równoczesne i wewnątrzprocesowe](../../../deployment/in-process-side-by-side-execution.md)