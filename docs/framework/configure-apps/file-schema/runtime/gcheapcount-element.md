---
title: GCHeapCount, element
ms.date: 11/08/2019
helpviewer_keywords:
- gcHeapCount element
- <gcHeapCount> element
ms.openlocfilehash: 3d6cac4185af182758cb82e6bfd9d96ed24869b4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283071"
---
# <a name="gcheapcount-element"></a>\<element > GCHeapCount

Określa liczbę stert/wątków, które mają być używane do wyrzucania elementów bezużytecznych serwera.

\<Konfiguracja > \
&nbsp;&nbsp;\<Runtime > \
&nbsp;&nbsp;&nbsp;&nbsp;\<GCHeapCount >

## <a name="syntax"></a>Składnia

```xml
<GCHeapCount
   enabled="nn"/>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|`enabled`|Atrybut wymagany.<br /><br />Określa liczbę stert, która ma być używana do wyrzucania elementów bezużytecznych serwera. Rzeczywista liczba stert jest minimalnym określoną liczbą stert i liczbą procesorów, które mogą być używane przez proces. |

#### <a name="enabled-attribute"></a>włączony atrybut

|Wartość|Opis|
|-----------|-----------------|
|`nn`|Liczba stert, które mają być używane na potrzeby serwera GC.|

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|

## <a name="remarks"></a>Uwagi

Domyślnie wątki serwera GC są trudne do koligacji z odpowiednim procesorem CPU, dzięki czemu istnieje jedna sterta GC, jeden wątek serwera GC i jeden wątek serwera w tle dla każdego procesora. Począwszy od .NET Framework 4.6.2, można użyć elementu **GCHeapCount** , aby ograniczyć liczbę stert używanych przez aplikację dla serwera GC. Ograniczenie liczby stert używanych na serwerze GC jest szczególnie przydatne w przypadku systemów, w których działa wiele wystąpień aplikacji serwera.

**GCHeapCount** jest zazwyczaj używany wraz z dwiema innymi flagami:

- [GCNoAffinitize](gcnoaffinitize-element.md), która kontroluje, czy wątki/sterty serwera GC są koligacją z procesorami CPU.

- [GCHeapAffinitizeMask](gcheapaffinitizemask-element.md), która kontroluje koligację wątków/sterty GC z procesorami CPU.

Jeśli ustawiono wartość **GCHeapCount** , **a GCNoAffinitize** jest wyłączona (ustawienie domyślne), istnieje koligacja między liczbami wątków i sterty *GC i* pierwszą *NN* procesorów. Można użyć elementu **GCHeapAffinitizeMask** , aby określić, które procesory są używane przez sterty GC serwera procesu. W przeciwnym razie, jeśli w systemie działa wiele procesów serwera, ich użycie procesora nastąpi.

Jeśli **GCHeapCount** jest ustawiony i **GCNoAffinitize** jest włączona, moduł zbierający elementy bezużyteczne ogranicza liczbę procesorów używanych przez serwer GC, ale nie KOLIGACJI stert i procesorów GC.

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

Poniższy przykład nie koligacji wątków serwera GC i ogranicza liczbę stert/wątków GC do 10.

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCNoAffinitize enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [GCNoAffinitize, element](gcnoaffinitize-element.md)
- [GCHeapAffinitizeMask, element](gcheapaffinitizemask-element.md)
- [Podstawowe informacje dotyczące wyrzucania elementów bezużytecznych](../../../../standard/garbage-collection/fundamentals.md)
- [Schemat ustawień środowiska uruchomieniowego](index.md)
- [Schemat pliku konfiguracji](../index.md)
