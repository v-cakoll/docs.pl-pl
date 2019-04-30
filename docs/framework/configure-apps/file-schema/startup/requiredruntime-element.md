---
title: <requiredRuntime>, element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requiredRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/requiredRuntime
helpviewer_keywords:
- requiredRuntime element
- <requiredRuntime> element
- container tags, <requiredRuntime> element
ms.assetid: 9fa1639e-beb8-43be-b7a4-12f7b229c34b
ms.openlocfilehash: 5e528a8b81fa3d9abc4f345d18f01e33f483a4a9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673845"
---
# <a name="requiredruntime-element"></a>\<requiredRuntime > element

Określa, że aplikacja obsługuje tylko wersję 1.0 środowiska uruchomieniowego języka wspólnego. Ten element jest przestarzała i nie powinna być używana. [ `supportedRuntime` ](supportedruntime-element.md) Zamiast tego należy użyć elementu.

\<Konfiguracja > \<uruchamiania > \<requiredRuntime >

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
> Jeśli używasz [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) funkcji, aby określić plik konfiguracji, należy użyć `<requiredRuntime>` elementu dla wszystkich wersji środowiska uruchomieniowego. `<supportedRuntime>` Element jest ignorowany, gdy używasz [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md).

 `version` Ciągu atrybutu musi odpowiadać nazwie folder instalacji dla określonej wersji programu .NET Framework. Ten ciąg nie jest interpretowany. Jeśli kod startowy środowiska uruchomieniowego nie znajdzie folderem dopasowania, środowisko uruchomieniowe nie jest załadowany; kod startowy pokazuje komunikat o błędzie i kończy działanie.

> [!NOTE]
> Ignoruje kodu startowego dla aplikacji, która jest obsługiwana w programie Internet Explorer `<requiredRuntime>` elementu.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak określić wersji środowiska uruchomieniowego w pliku konfiguracji.

```xml
<configuration>
   <startup>
      <requiredRuntime version="v1.0.3705" safemode="true"/>
   </startup>
</configuration>
```

## <a name="see-also"></a>Zobacz także

- [Schemat ustawień uruchamiania](index.md)
- [Schemat pliku konfiguracji](../index.md)
- [Instrukcje: Konfigurowanie aplikacji do obsługi w programie .NET Framework 4 lub nowszy](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)