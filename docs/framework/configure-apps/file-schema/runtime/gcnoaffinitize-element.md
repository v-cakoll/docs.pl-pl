---
title: GCNoAffinitize, element
ms.date: 11/08/2019
helpviewer_keywords:
- gcNoAffinitize element
- <gcNoAffinitize> element
ms.openlocfilehash: 16d6e5adefe2b632d7251669650058d7df7cea70
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "84004741"
---
# <a name="gcnoaffinitize-element"></a>\<GCNoAffinitize>, element

Określa, czy koligacji wątki serwera GC z procesorami CPU.

\<configuration>\
&nbsp;&nbsp;\<runtime>\
&nbsp;&nbsp;&nbsp;&nbsp;\<GCNoAffinitize>

## <a name="syntax"></a>Składnia

```xml
<GCNoAffinitize
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|`enabled`|Atrybut wymagany.<br /><br />Określa, czy wątki/sterty serwera GC są koligacją z procesorami dostępnymi na komputerze.|

#### <a name="enabled-attribute"></a>włączony atrybut

|Wartość|Opis|
|-----------|-----------------|
|`false`|Skoligacony Server GC wątki z procesorami CPU. Domyślnie włączone.|
|`true`|Nie koligacji wątków serwera GC z procesorami CPU.|

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|

## <a name="remarks"></a>Uwagi

Domyślnie wątki serwera GC są trudne do koligacji z odpowiednimi procesorami CPU. Każdy z dostępnych procesorów systemu ma własną stertę i wątek GC. Jest to zazwyczaj preferowane ustawienie, ponieważ optymalizuje użycie pamięci podręcznej. Rozpoczynając od .NET Framework 4.6.2, ustawiając atrybut **GCNoAffinitize** elementu `enabled` na `true` , można określić, że wątki i procesory serwera GC nie powinny być ściśle sprzężone.

Można określić **GCNoAffinitize** element konfiguracji, aby nie koligacji wątki serwera GC z procesorami CPU. Można go również użyć wraz z elementem [GCHeapCount](gcheapcount-element.md) , aby kontrolować liczbę stert i wątków GC używanych przez aplikację.

Jeśli `enabled` atrybut elementu **GCNoAffinitize** jest `false` (jego wartość domyślna), można również użyć elementu [GCHeapCount](gcheapcount-element.md) , aby określić liczbę wątków i sterty GC, wraz z elementem [GCHeapAffinitizeMask](gcheapaffinitizemask-element.md) , aby określić procesory, do których są koligacje wątki i sterty GC.

## <a name="example"></a>Przykład

W poniższym przykładzie nie są twarde koligacji Server GC wątki:

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCNoAffinitize enabled="true"/>
   </runtime>
</configuration>
```

Poniższy przykład nie koligacji wątków serwera GC i ogranicza liczbę stert/wątków GC do 10:

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
- [GCHeapAffinitizeMask, element](gcheapaffinitizemask-element.md)
- [GCHeapCount, element](gcheapcount-element.md)
- [Podstawowe informacje dotyczące wyrzucania elementów bezużytecznych](../../../../standard/garbage-collection/fundamentals.md)
- [Schemat ustawień środowiska uruchomieniowego](index.md)
- [Schemat pliku konfiguracji](../index.md)
