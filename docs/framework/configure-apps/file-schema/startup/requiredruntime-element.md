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
ms.openlocfilehash: fe96673b95f48cb75d36662a680bf56a59363f9f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "71697485"
---
# <a name="requiredruntime-element"></a>\<requiredRuntime>, element

Określa, że aplikacja obsługuje tylko wersję 1,0 środowiska uruchomieniowego języka wspólnego. Ten element jest przestarzały i nie powinien już być używany. [`supportedRuntime`](supportedruntime-element.md)Zamiast tego należy użyć elementu.

[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<startup>**](startup-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<requiredRuntime>**  

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
|`version`|Atrybut opcjonalny.<br /><br /> Wartość ciągu określająca wersję .NET Framework obsługiwanej przez tę aplikację. Wartość ciągu musi być zgodna z nazwą katalogu znajdującą się w katalogu głównym instalacji .NET Framework. Zawartość ciągu nie jest analizowana.|
|`safemode`|Atrybut opcjonalny.<br /><br /> Określa, czy kod uruchomienia środowiska uruchomieniowego przeszukuje rejestr w celu określenia wersji środowiska uruchomieniowego.|

## <a name="safemode-attribute"></a>safemode — atrybut

|Wartość|Opis|
|-----------|-----------------|
|`false`|Kod uruchomienia środowiska uruchomieniowego przeszukuje rejestr. Jest to wartość domyślna.|
|`true`|Kod uruchomienia środowiska uruchomieniowego nie przeszukuje rejestru.|

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|
|`startup`|Zawiera `<requiredRuntime>` element.|

## <a name="remarks"></a>Uwagi
 Aplikacje skompilowane do obsługi tylko wersji 1,0 środowiska uruchomieniowego muszą używać `<requiredRuntime>` elementu. Aplikacje skompilowane przy użyciu wersji 1,1 lub nowszej środowiska uruchomieniowego muszą używać `<supportedRuntime>` elementu.

> [!NOTE]
> Jeśli używasz funkcji [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) do określenia pliku konfiguracji, musisz użyć `<requiredRuntime>` elementu dla wszystkich wersji środowiska uruchomieniowego. `<supportedRuntime>`Element jest ignorowany w przypadku korzystania z [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md).

 `version`Ciąg atrybutu musi być zgodny z nazwą folderu instalacji określonej wersji .NET Framework. Ten ciąg nie jest interpretowany. Jeśli kod uruchomienia środowiska uruchomieniowego nie odnajdzie pasującego folderu, środowisko uruchomieniowe nie zostanie załadowane; kod uruchamiania pokazuje komunikat o błędzie i kończy pracę.

> [!NOTE]
> Kod uruchamiania aplikacji hostowanej w programie Microsoft Internet Explorer ignoruje `<requiredRuntime>` element.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak określić wersję środowiska uruchomieniowego w pliku konfiguracji.

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
- [Instrukcje: Konfigurowanie aplikacji do obsługi .NET Framework 4 lub nowszej wersji](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
