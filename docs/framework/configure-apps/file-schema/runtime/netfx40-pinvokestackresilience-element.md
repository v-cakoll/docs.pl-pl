---
title: <NetFx40_PInvokeStackResilience>, element
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_PInvokeStackResilience> element
- NetFx40_PInvokeStackResilience element
ms.assetid: 39fb1588-72a4-4479-af74-0605233b68bd
ms.openlocfilehash: 86f50aafe0b21d5080288e09ac7118ca1e4c939a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73116157"
---
# <a name="netfx40_pinvokestackresilience-element"></a>\<NetFx40_PInvokeStackResilience> Element

Określa, czy środowisko uruchomieniowe automatycznie naprawia nieprawidłowe deklaracje wywołania platformy w czasie wykonywania, kosztem wolniejszych przejść między zarządzanym i niezarządzanym kodem.

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<NetFx40_PInvokeStackResilience>**  

## <a name="syntax"></a>Składnia

```xml
<NetFx40_PInvokeStackResilience  enabled="1|0"/>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|`enabled`|Atrybut wymagany.<br /><br /> Określa, czy środowisko uruchomieniowe wykrywa nieprawidłowe deklaracje wywołania platformy i automatycznie naprawia stos w czasie wykonywania na platformach 32-bitowych.|

## <a name="enabled-attribute"></a>Atrybut włączony

|Wartość|Opis|
|-----------|-----------------|
|`0`|Środowisko uruchomieniowe używa szybszej architektury organizowania międzyoperacyjnego wprowadzonej w .NET Framework 4, która nie wykrywa i nie naprawia niepoprawnych deklaracji wywołania platformy. Domyślnie włączone.|
|`1`|Środowisko uruchomieniowe używa wolniejszych przejść, które wykrywają i rozwiązują nieprawidłowe deklaracje wywołania platformy.|

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|
|`runtime`|Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.|

## <a name="remarks"></a>Uwagi

Ten element umożliwia wymianę między nieprawidłowymi deklaracjami wywołania platformy w celu uzyskania odporności w czasie wykonywania.

Począwszy od .NET Framework 4, ulepszona architektura organizowania międzyoperacyjności zapewnia znaczącą poprawę wydajności dla przejść z kodu zarządzanego do kodu niezarządzanego. We wcześniejszych wersjach .NET Framework warstwa marshaler wykryła nieprawidłowe deklaracje wywołania platformy na 32-bitowych platformach i automatycznie naprawi stos. Nowa architektura organizowania eliminuje ten krok. W związku z tym przejścia są bardzo szybkie, ale nieprawidłowa deklaracja wywołania platformy może spowodować błąd programu.

Aby ułatwić wykrywanie niepoprawnych deklaracji podczas opracowywania, udoskonalono środowisko debugowania programu Visual Studio. Asystent debugowania zarządzanego [pInvokeStackImbalance](../../../debug-trace-profile/pinvokestackimbalance-mda.md) (MDA) powiadamia o nieprawidłowej deklaracji wywołania platformy, gdy aplikacja jest uruchomiona z dołączonym debugerem.

Aby rozwiązać scenariusze, w których aplikacja używa składników, których nie można ponownie skompilować, i które mają nieprawidłowe deklaracje wywołania platformy, można użyć `NetFx40_PInvokeStackResilience` elementu. Dodanie tego elementu do pliku konfiguracji aplikacji z opcją załączanie `enabled="1"` do trybu zgodności z zachowaniem wcześniejszych wersji .NET Framework, kosztem wolniejszych przejść. Zestawy, które zostały skompilowane pod kątem wcześniejszych wersji .NET Framework są automatycznie zaznaczane w tym trybie zgodności i nie potrzebują tego elementu.

## <a name="configuration-file"></a>Plik konfiguracji

Tego elementu można używać tylko w pliku konfiguracji aplikacji.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak zrezygnować z zwiększonej elastyczności względem nieprawidłowych deklaracji wywołania platformy dla aplikacji, kosztem wolniejszych przejść między kodem zarządzanym i niezarządzanym.

```xml
<configuration>
   <runtime>
      <NetFx40_PInvokeStackResilience enabled="1"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Zobacz także

- [Schemat ustawień środowiska uruchomieniowego](index.md)
- [Schemat pliku konfiguracji](../index.md)
- [pInvokeStackImbalance](../../../debug-trace-profile/pinvokestackimbalance-mda.md)
