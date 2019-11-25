---
title: GCHeapAffinitizeMask, element
ms.date: 11/08/2019
helpviewer_keywords:
- gcHeapCount element
- <gcHeapCount> element
ms.openlocfilehash: 09d6523fb10692dd3617a3827d5bccf112bc632b
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73978383"
---
# <a name="gcheapaffinitizemask-element"></a>\<element > GCHeapAffinitizeMask

Definiuje koligację między stertami GC i procesorami indywidualnymi.

\<Konfiguracja > \
&nbsp;&nbsp;\<Runtime > \
&nbsp;&nbsp;&nbsp;&nbsp;\<GCHeapAffinitizeMask >

## <a name="syntax"></a>Składnia

```xml
<GCHeapAffinitizeMask
   enabled="nnnn"/>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|`enabled`|Atrybut wymagany.<br /><br />Określa koligację między stertami GC i procesorami indywidualnymi. |

#### <a name="enabled-attribute"></a>włączony atrybut

|Wartość|Opis|
|-----------|-----------------|
|`nnnn`|Wartość dziesiętna, która tworzy maskę bitowej definiującą koligację między sterty serwera GC a procesorami indywidualnymi. |

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|

## <a name="remarks"></a>Uwagi

Domyślnie wątki serwera GC są trudne do koligacji z odpowiednim procesorem CPU, dzięki czemu istnieje jedna sterta GC, jeden wątek serwera GC i jeden wątek serwera w tle dla każdego procesora. Począwszy od .NET Framework 4.6.2, można użyć elementu **GCHeapAffinitizeMask** do kontrolowania koligacji między stertami i procesorami serwera GC, gdy Liczba stert jest ograniczona przez element **GCHeapCount** .

**GCHeapAffinitizeMask** jest zazwyczaj używany wraz z dwiema innymi flagami:

- [GCNoAffinitize](gcnoaffinitize-element.md), która kontroluje, czy wątki/sterty serwera GC są koligacją z procesorami CPU. Atrybut `enabled` elementu [GCNoAffinitize](gcnoaffinitize-element.md) musi być `false` (jego wartość domyślna) dla ustawienia **GCHeapAffinitizeMask** , które ma być używane.

- [GCHeapCount](gcheapcount-element.md), który ogranicza liczbę stert używany przez proces dla serwera GC. Domyślnie istnieje jedna sterta dla każdego procesora.

**nnnn** jest maską bitową wyrażoną jako wartość dziesiętną. Bit 0 z bajtem 0 reprezentuje procesor 0, bit 1 bajt 0 reprezentuje procesor 1 i tak dalej. Na przykład:

```xml
<GCHeapAffinitizeMask enabled="1023"/>
```

Wartość 1023 to 0x3FF lub 0011 1111 1111b. Proces używa 10 procesorów, od 0 do procesor 9.

## <a name="example"></a>Przykład

Poniższy przykład wskazuje, że aplikacja używa serwera GC z 10 stert/wątków. Ponieważ nie chcesz, aby te sterty pokrywały się ze stertami z innych aplikacji uruchomionych w systemie, użyj **GCHeapAffinitizeMask** , aby określić, że proces ma używać procesorów od 0 do 9.

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCHeapAffinitizeMask enabled="1023"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [GCNoAffinitize, element](gcnoaffinitize-element.md)
- [GCHeapCount, element](gcheapcount-element.md)
- [Podstawowe informacje dotyczące wyrzucania elementów bezużytecznych](../../../../standard/garbage-collection/fundamentals.md)
- [Schemat ustawień środowiska uruchomieniowego](index.md)
- [Schemat pliku konfiguracji](../index.md)
