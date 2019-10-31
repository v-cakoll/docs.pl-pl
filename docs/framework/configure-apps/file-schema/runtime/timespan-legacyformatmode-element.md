---
title: <TimeSpan_LegacyFormatMode>, element
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- <TimeSpan_LegacyFormatMode> element
- TimeSpan_LegacyFormatMode element
ms.assetid: 865e7207-d050-4442-b574-57ea29d5e2d6
ms.openlocfilehash: c835e1bcef7bbfdc990c8db177eafed4ec6bb30c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115211"
---
# <a name="timespan_legacyformatmode-element"></a>\<element > TimeSpan_LegacyFormatMode

Określa, czy środowisko uruchomieniowe zachowuje starsze zachowanie w operacjach formatowania przy użyciu wartości <xref:System.TimeSpan?displayProperty=nameWithType>.

[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<środowiska uruchomieniowego >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<TimeSpan_LegacyFormatMode >**  

## <a name="syntax"></a>Składnia

```xml
<TimeSpan_LegacyFormatMode
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|`enabled`|Atrybut wymagany.<br /><br /> Określa, czy środowisko uruchomieniowe korzysta ze starszego zachowania formatowania z wartościami <xref:System.TimeSpan?displayProperty=nameWithType>.|

## <a name="enabled-attribute"></a>Atrybut włączony

|Wartość|Opis|
|-----------|-----------------|
|`false`|Środowisko uruchomieniowe nie przywraca starszego zachowania formatowania.|
|`true`|Środowisko uruchomieniowe przywraca starsze zachowanie podczas formatowania.|

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|
|`runtime`|Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.|

## <a name="remarks"></a>Uwagi

Począwszy od .NET Framework 4, struktura <xref:System.TimeSpan?displayProperty=nameWithType> implementuje interfejs <xref:System.IFormattable> i obsługuje operacje formatowania przy użyciu standardowych i niestandardowych ciągów formatu. Jeśli metoda analizy napotka nieobsługiwany specyfikator formatu lub ciąg formatu, zgłasza <xref:System.FormatException>.

W poprzednich wersjach .NET Framework struktura <xref:System.TimeSpan> nie została zaimplementowana <xref:System.IFormattable> i nie obsługiwała ciągów formatowania. Jednak wielu programistów założono, że <xref:System.TimeSpan> obsłużył zestaw ciągów formatu i używały ich w [operacjach formatowania złożonego](../../../../standard/base-types/composite-formatting.md) z metodami takimi jak <xref:System.String.Format%2A?displayProperty=nameWithType>. Zwykle, jeśli typ implementuje <xref:System.IFormattable> i obsługuje ciągi formatu, wywołania metod formatowania z nieobsługiwanymi ciągami formatu zwykle generują <xref:System.FormatException>. Jednak ponieważ <xref:System.TimeSpan> nie zaimplementował <xref:System.IFormattable>, środowisko uruchomieniowe zignorował ciąg formatu i zamiast tego nazywa metodę <xref:System.TimeSpan.ToString?displayProperty=nameWithType>. Oznacza to, że chociaż ciągi formatu nie miały wpływu na operację formatowania, ich obecność nie powodowała <xref:System.FormatException>.

W przypadkach, w których starszy kod przekazuje metodę formatowania złożonego i nieprawidłowy ciąg formatu, i nie można ponownie skompilować tego kodu, można użyć elementu `<TimeSpan_LegacyFormatMode>`, aby przywrócić zachowanie starszej <xref:System.TimeSpan>. Po ustawieniu atrybutu `enabled` tego elementu na `true`, Metoda formatowania złożonego spowoduje wywołanie <xref:System.TimeSpan.ToString?displayProperty=nameWithType> zamiast <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>i <xref:System.FormatException> nie zostanie zgłoszony.

## <a name="example"></a>Przykład

Poniższy przykład tworzy wystąpienie obiektu <xref:System.TimeSpan> i próbuje sformatować go za pomocą metody <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> za pomocą nieobsługiwanego ciągu formatu standardowego.

[!code-csharp[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/timespan.breakingchanges/cs/legacyformatmode1.cs#1)]
[!code-vb[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/timespan.breakingchanges/vb/legacyformatmode1.vb#1)]

Po uruchomieniu przykładu w .NET Framework 3,5 lub we wcześniejszej wersji zostaną wyświetlone następujące dane wyjściowe:

```
12:30:45
```

Różni się to od danych wyjściowych w przypadku uruchomienia przykładu w .NET Framework 4 lub jego nowszej wersji:

```
Invalid Format
```

Jeśli jednak dodasz następujący plik konfiguracji do katalogu przykładu, a następnie uruchomisz przykład w .NET Framework 4 lub nowszej wersji, dane wyjściowe są identyczne z tym, które zostały utworzone przez przykład w przypadku uruchomienia na .NET Framework 3,5.

```xml
<?xml version ="1.0"?>
<configuration>
   <runtime>
      <TimeSpan_LegacyFormatMode enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Zobacz także

- [Schemat ustawień środowiska uruchomieniowego](index.md)
- [Schemat pliku konfiguracji](../index.md)
