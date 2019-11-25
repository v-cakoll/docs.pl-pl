---
title: gcServer, element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcServer
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcServer
helpviewer_keywords:
- gcServer element
- <gcServer> element
ms.assetid: 8d25b80e-2581-4803-bd87-a59528e3cb03
ms.openlocfilehash: 8eab5e36bab90510aff4f1a3e15328197ac59ed7
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73968948"
---
# <a name="gcserver-element"></a>\<element > gcServer

Określa, czy środowisko uruchomieniowe języka wspólnego uruchamia odzyskiwanie pamięci serwera.

[\<> konfiguracji](../configuration-element.md)\
&nbsp;&nbsp;[\<środowiska uruchomieniowego >](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<gcServer >

## <a name="syntax"></a>Składnia

```xml
<gcServer
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|`enabled`|Atrybut wymagany.<br /><br />Określa, czy środowisko uruchomieniowe uruchamia odzyskiwanie pamięci serwera.|

#### <a name="enabled-attribute"></a>włączony atrybut

|Wartość|Opis|
|-----------|-----------------|
|`false`|Nie uruchamia odzyskiwania pamięci serwera. Domyślnie włączone.|
|`true`|Uruchamia odzyskiwanie pamięci serwera.|

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|

## <a name="remarks"></a>Uwagi

Środowisko uruchomieniowe języka wspólnego (CLR) obsługuje dwa typy wyrzucania elementów bezużytecznych: odzyskiwanie pamięci stacji roboczej, które jest dostępne we wszystkich systemach i wyrzucanie elementów bezużytecznych serwera, które jest dostępne w systemach wieloprocesorowych. Użyj elementu **gcServer** , aby kontrolować typ wyrzucania elementów bezużytecznych wykonywanych przez środowisko CLR. Użyj właściwości <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>, aby określić, czy jest włączone odzyskiwanie pamięci serwera.

W przypadku komputerów z jednym procesorem domyślna opcja wyrzucania elementów bezużytecznych stacji roboczej powinna być najszybszą opcją. Stacja robocza lub serwer może być używana w przypadku komputerów dwuprocesorowych. Wyrzucanie elementów bezużytecznych serwera powinno być najszybszą opcją dla więcej niż dwóch procesorów. Najczęściej systemy serwerów wieloprocesorowych wyłączą serwer GC i używają stacji roboczej GC zamiast tego, gdy wiele wystąpień aplikacji serwerowych działa na tym samym komputerze.

Tego elementu można używać tylko w pliku konfiguracji aplikacji; jest on ignorowany, jeśli znajduje się w pliku konfiguracji komputera.

> [!NOTE]
> W .NET Framework 4 i starszych wersjach współbieżne wyrzucanie elementów bezużytecznych nie jest dostępne po włączeniu odzyskiwania pamięci serwera. Począwszy od .NET Framework 4,5, wyrzucanie elementów bezużytecznych serwera jest współbieżne. Aby użyć niewspółbieżnego wyrzucania elementów bezużytecznych serwera, Ustaw element **gcServer** na `true` i [element gcConcurrent](gcconcurrent-element.md) , aby `false`.

Począwszy od .NET Framework 4.6.2 można również skonfigurować serwer GC przy użyciu następujących elementów:

- [GCNoAffinitize](gcnoaffinitize-element.md), który określa, czy istnieje koligacja między stertą i procesorami serwera GC. Domyślnie dla każdego procesora istnieje jedna sterta serwera GC.

- [GCHeapCount](gcheapcount-element.md), który ogranicza liczbę sterty używanych przez proces.

- [GCHeapAffinitizeMask](gcheapaffinitizemask-element.md), który definiuje koligację między dostępnymi stertami GC serwera a indywidualnymi procesorami.

## <a name="example"></a>Przykład

Poniższy przykład umożliwia wyrzucanie elementów bezużytecznych serwera:

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [Schemat ustawień środowiska uruchomieniowego](index.md)
- [Schemat pliku konfiguracji](../index.md)
- [Aby wyłączyć współbieżne wyrzucanie elementów bezużytecznych](gcconcurrent-element.md#to-disable-background-garbage-collection)
