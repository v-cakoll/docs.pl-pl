---
title: <NetFx45_CultureAwareComparerGetHashCode_LongStrings>, element
ms.date: 03/30/2017
helpviewer_keywords:
- NetFx45_CultureAwareComparerGetHashCode_LongStrings element
- <NetFx45_CultureAwareComparerGetHashCode_LongStrings> element
- GetHashCode method
- hash codes, calculating
ms.assetid: 3a5f38d1-ebc8-44de-aaeb-2929f6e6b48f
ms.openlocfilehash: 413eb6c6e61b509135601c65cf045eabd849e8b3
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802112"
---
# <a name="netfx45_cultureawarecomparergethashcode_longstrings-element"></a>\<NetFx45_CultureAwareComparerGetHashCode_LongStrings> Element

Określa, czy środowisko uruchomieniowe używa stałej ilości pamięci do obliczenia kodów skrótów dla metody <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>.

[ **\<> konfiguracji**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<środowiska uruchomieniowego >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<** NetFx45_CultureAwareComparerGetHashCode_LongStrings >  

## <a name="syntax"></a>Składnia

```xml
<NetFx45_CultureAwareComparerGetHashCode_LongStrings enabled="0|1">
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>{1&gt;{2&gt;Atrybuty&lt;2}&lt;1}

|Atrybut|Opis|
|---------------|-----------------|
|`enabled`|Atrybut wymagany.<br /><br /> Określa, czy środowisko uruchomieniowe języka wspólnego przydziela stałą ilość pamięci podczas obliczania kodów wartości skrótu.|

## <a name="enabled-attribute"></a>Atrybut włączony

|Wartość|Opis|
|-----------|-----------------|
|0|Środowisko uruchomieniowe języka wspólnego przydziela zmienną ilość pamięci dla metody <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>, aby obliczyć kody skrótów. Jest to domyślne ustawienie.|
|1|Środowisko uruchomieniowe języka wspólnego przydziela stałą ilość pamięci dla metody <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>, aby obliczyć kody skrótów.|

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|
|`runtime`|Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.|

## <a name="remarks"></a>Uwagi

Domyślnie środowisko uruchomieniowe języka wspólnego przydziela zmienną ilość pamięci dla metody <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> i <xref:System.ArgumentException> może być zgłaszane, gdy metoda próbuje obliczyć kod skrótu bardzo dużych ciągów (ponad kilka milionów znaków). Dodając ten element do pliku konfiguracji aplikacji i ustawiając jego atrybut `enabled` na wartość "1", można określić, że metoda <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> użyć alternatywnego algorytmu, który przydziela stałą ilość pamięci do obliczeń kodów skrótów.

> [!IMPORTANT]
> Element `<NetFx45_CultureAwareComparerGetHashCode_LongStrings>` nie jest używany w systemie Windows 8 i nowszych wersjach.

## <a name="see-also"></a>Zobacz także

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- [Schemat ustawień środowiska uruchomieniowego](index.md)
- [Schemat pliku konfiguracji](../index.md)
