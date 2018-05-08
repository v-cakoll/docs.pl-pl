---
title: $ - ciąg interpolacji (odwołanie w C#)
description: Ciąg interpolacji zapewnia bardziej czytelny i wygodne składni do formatowania danych wyjściowych ciąg niż tradycyjne ciąg złożone formatowanie.
ms.date: 03/26/2018
f1_keywords:
- $_CSharpKeyword
- $
helpviewer_keywords:
- $ special character [C#]
- $ language element [C#]
- string interpolation [C#]
- interpolated string [C#]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c6915e49c442c80459dae85ac2598a0fa5ed3182
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="---string-interpolation-c-reference"></a>$ - ciąg interpolacji (odwołanie w C#)

`$` Znak specjalny identyfikuje ciąg literału jako *interpolowane ciąg*. Interpolowane ciąg wygląda jak ciąg szablonu, który zawiera *interpolowane wyrażenia*. Po usunięciu ciągu interpolowanym ciąg wyniku, elementów z wyrażenia interpolowane zastępuje reprezentacji ciągu wyników wyrażenia. Ta funkcja jest dostępna w C# 6 i nowsze wersje.

Ciąg interpolacji zapewnia bardziej czytelny i wygodne składni utworzyć ciągi sformatowane niż [ciągu formatowania złożonego](../../../standard/base-types/composite-formatting.md) funkcji. W poniższym przykładzie użyto obie funkcje do tworzenia tych samych danych wyjściowych:

[!code-csharp-interactive[compare with composite formatting](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#1)]

> [!NOTE]
> Nie może zawierać żadnego odstępu między `$` i `"` zaczynającym się ciąg. To powoduje błąd kompilacji.

Struktura element o interpolowanego wyrażenia jest następujący:

```
{<interpolatedExpression>[,<alignment>][:<formatString>]}
```

Elementy w nawiasach kwadratowych są opcjonalne. W tabeli poniżej opisano każdy element.

|Element|Opis|
|-------------|-----------------|
|`interpolatedExpression`|Wyrażenie do oceny, aby uzyskać wynik formatowania. Reprezentacja ciągu `null` wynik jest <xref:System.String.Empty?displayProperty=nameWithType>.|
|`alignment`|Wyrażenie stałe, którego wartość określa minimalną liczbę znaków w reprezentację ciągu wynik interpolowanego wyrażenia. Jeśli jest dodatnia, reprezentacja tekstowa jest wyrównany do prawej; Jeśli ujemną, jest wyrównany. Aby uzyskać więcej informacji, zobacz [składnika wyrównanie](../../../standard/base-types/composite-formatting.md#alignment-component).|
|`formatString`|Ciąg formatu standardowych lub niestandardowych, który jest obsługiwany przez ten typ wyniku wyrażenia. Aby uzyskać więcej informacji, zobacz [składnika ciąg formatu](../../../standard/base-types/composite-formatting.md#format-string-component).|

W poniższym przykładzie użyto opcjonalnych składników formatowania opisane powyżej:

[!code-csharp-interactive[specify alignment and format string](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#2)]

Aby uwzględnić nawiasu klamrowego ("{" lub "}") w tekście utworzonego przez ciągu interpolowanym, użyj dwóch nawiasów klamrowych, "{{" lub "}}". Aby uzyskać więcej informacji, zobacz [anulowanie nawiasów klamrowych](../../../standard/base-types/composite-formatting.md#escaping-braces).

Jako dwukropka (:) ma specjalne znaczenie w elemencie interpolowanego wyrażenia, aby można było używać [operator warunkowy](../operators/conditional-operator.md) w wyrażeniu interpolowane ujmij tego wyrażenia w nawiasach.

W poniższym przykładzie pokazano, jak dołączyć nawiasu klamrowego na ciąg wyniku i sposobu użycia operator warunkowy w wyrażeniu interpolowane:

[!code-csharp-interactive[example with ternary conditional operator](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#3)]

Użyj ciągi interpolowane z Verbatim `$` następuje znak `@` znaków. Aby uzyskać więcej informacji na temat ciągi verbatim zobacz [ciąg](../keywords/string.md) tematu.

> [!NOTE]
> `$` Token musi występować przed `@` token w ciągu interpolowanym dosłownego wyrażenia.

Istnieją trzy niejawną konwersję z ciągu interpolowanym:

1. Konwersja ciągu interpolowanym do <xref:System.String> wystąpienie, które jest wynikiem rozdzielczość ciągu interpolowanym interpolowanego wyrażenia elementów zastępowane z reprezentacji ciągu prawidłowo sformatowane ich wyników. Ta konwersja używa bieżącej kultury.

1. Konwersja ciągu interpolowanym do <xref:System.FormattableString> wystąpienie, które reprezentuje ciąg formatu złożonego wraz z wynikiem wyrażenia do sformatowania. Który umożliwia tworzenie wielu ciągów wyników z specyficzne dla kultury zawartości z jednej <xref:System.FormattableString> wystąpienia. Robić, które wywołują jedną z następujących metod:

      - A <xref:System.FormattableString.ToString> przeciążenia, które tworzy ciąg wynik <xref:System.Globalization.CultureInfo.CurrentCulture>.
      - A <xref:System.FormattableString.Invariant%2A> metodę, która tworzy ciąg wynik <xref:System.Globalization.CultureInfo.InvariantCulture>.
      - A <xref:System.FormattableString.ToString(System.IFormatProvider)> metodę, która tworzy ciąg wynik określonej kultury.

1. Konwersja ciągu interpolowanym do <xref:System.IFormattable> ciągi wystąpienie, które umożliwia tworzenie wielu wyników z zawartością specyficzne dla kultury z jednej <xref:System.IFormattable> wystąpienia.

W poniższym przykładzie użyto niejawnej konwersji <xref:System.FormattableString> można utworzyć ciągów wynikowych specyficzne dla kultury:

[!code-csharp-interactive[create culture-specific result strings](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#4)]

Jeśli jesteś nowym użytkownikiem interpolacji ciągu, sprawdź [ciągu interpolacji w języku C#](../../quick-starts/interpolated-strings.yml) Szybki Start. Aby uzyskać więcej przykładów, zobacz [samouczek interpolacji ciąg](../../tutorials/string-interpolation.md).

## <a name="see-also"></a>Zobacz także  
 <xref:System.String.Format%2A?displayProperty=nameWithType>  
 <xref:System.FormattableString?displayProperty=nameWithType>  
 <xref:System.IFormattable?displayProperty=nameWithType>  
 [Złożone formatowanie](../../../standard/base-types/composite-formatting.md)  
 [Ciągi](../../../csharp/programming-guide/strings/index.md)  
 [Znaki specjalne języka C#](../../../csharp/language-reference/tokens/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  