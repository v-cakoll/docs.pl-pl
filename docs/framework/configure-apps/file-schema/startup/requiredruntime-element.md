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
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697485"
---
# <a name="requiredruntime-element"></a>\<element > requiredRuntime

Określa, że aplikacja obsługuje tylko wersję 1,0 środowiska uruchomieniowego języka wspólnego. Ten element jest przestarzały i nie powinien już być używany. Zamiast tego należy użyć elementu [`supportedRuntime`](supportedruntime-element.md) .

[ **> konfiguracji \<** ](../configuration-element.md)  
&nbsp;&nbsp;[ **> uruchamiania\<** ](startup-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp; **\<requiredRuntime >**  

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

|Value|Opis|
|-----------|-----------------|
|`false`|Kod uruchomienia środowiska uruchomieniowego przeszukuje rejestr. Jest to wartość domyślna.|
|`true`|Kod uruchomienia środowiska uruchomieniowego nie przeszukuje rejestru.|

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|
|`startup`|Zawiera element `<requiredRuntime>`.|

## <a name="remarks"></a>Uwagi
 Aplikacje skompilowane do obsługi tylko wersji 1,0 środowiska uruchomieniowego muszą używać elementu `<requiredRuntime>`. Aplikacje skompilowane przy użyciu wersji 1,1 lub nowszej środowiska uruchomieniowego muszą używać elementu `<supportedRuntime>`.

> [!NOTE]
> W przypadku użycia funkcji [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) w celu określenia pliku konfiguracji należy użyć elementu `<requiredRuntime>` dla wszystkich wersji środowiska uruchomieniowego. Element `<supportedRuntime>` jest ignorowany w przypadku korzystania z [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md).

 Ciąg atrybutu `version` musi być zgodny z nazwą folderu instalacji określonej wersji .NET Framework. Ten ciąg nie jest interpretowany. Jeśli kod uruchomienia środowiska uruchomieniowego nie odnajdzie pasującego folderu, środowisko uruchomieniowe nie zostanie załadowane; kod uruchamiania pokazuje komunikat o błędzie i kończy pracę.

> [!NOTE]
> Kod uruchamiania aplikacji hostowanej w programie Microsoft Internet Explorer ignoruje `<requiredRuntime>` elementu.

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
