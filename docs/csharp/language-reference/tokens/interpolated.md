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
author: pkulikov
ms.author: ronpet
ms.openlocfilehash: 407ca9e4744ea9be45867a08e87c502821226472
ms.sourcegitcommit: ff1d40507b3eb6e2185478e37c66c66be6de46f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/11/2018
---
# <a name="---string-interpolation-c-reference"></a>$ - ciąg interpolacji (odwołanie w C#)

`$` Znak specjalny identyfikuje ciąg literału jako *interpolowane ciąg*. Ciągu interpolowanym jest ciągiem literału, który może zawierać *interpolowane wyrażenia*. Po usunięciu ciągu interpolowanym ciąg wyniku, elementów z wyrażenia interpolowane zastępuje reprezentacji ciągu wyników wyrażenia. Ta funkcja jest dostępna w C# 6 i nowsze wersje języka.

Ciąg interpolacji zapewnia bardziej czytelny i wygodne składni utworzyć ciągi sformatowane niż [ciągu formatowania złożonego](../../../standard/base-types/composite-formatting.md) funkcji. W poniższym przykładzie użyto obie funkcje do tworzenia tych samych danych wyjściowych:

[!code-csharp-interactive[compare with composite formatting](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#1)]

## <a name="structure-of-an-interpolated-string"></a>Struktura ciągu interpolowanym

Aby zidentyfikować ciąg literału jako ciągu interpolowanym, dołączenie wartości za pomocą `$` symbolu. Nie może zawierać żadnego odstępu między `$` i `"` zaczynającym się literału ciągu. To powoduje błąd kompilacji.

Struktura element o interpolowanego wyrażenia jest następujący:

```
{<interpolatedExpression>[,<alignment>][:<formatString>]}
```

Elementy w nawiasach kwadratowych są opcjonalne. W poniższej tabeli opisano każdy element:

|Element|Opis|
|-------------|-----------------|
|`interpolatedExpression`|Wyrażenie, które daje wynik formatowania. Reprezentacja ciągu `null` wynik jest <xref:System.String.Empty?displayProperty=nameWithType>.|
|`alignment`|Wyrażenie stałe, którego wartość określa minimalną liczbę znaków w reprezentację ciągu wynik interpolowanego wyrażenia. Jeśli jest dodatnia, reprezentacja tekstowa jest wyrównany do prawej; Jeśli ujemną, jest wyrównany. Aby uzyskać więcej informacji, zobacz [składnika wyrównanie](../../../standard/base-types/composite-formatting.md#alignment-component).|
|`formatString`|Ciąg formatu, który jest obsługiwany przez ten typ wyniku wyrażenia. Aby uzyskać więcej informacji, zobacz [składnika ciąg formatu](../../../standard/base-types/composite-formatting.md#format-string-component).|

W poniższym przykładzie użyto opcjonalnych składników formatowania opisane powyżej:

[!code-csharp-interactive[specify alignment and format string](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#2)]

## <a name="special-characters"></a>Znaki specjalne

Uwzględnienie nawias klamrowy "{" lub "}", w tekście utworzonego przez ciągu interpolowanym, użyj dwóch nawiasów klamrowych, "{{" lub "}}". Aby uzyskać więcej informacji, zobacz [anulowanie nawiasów klamrowych](../../../standard/base-types/composite-formatting.md#escaping-braces).

Jako dwukropkiem (":") ma specjalne znaczenie w elemencie interpolowanego wyrażenia, aby można było używać [operator warunkowy](../operators/conditional-operator.md) w wyrażeniu interpolowane ujmij tego wyrażenia w nawiasach.

W poniższym przykładzie pokazano, jak dołączyć nawiasu klamrowego ciągu wynik i sposobu użycia operator warunkowy w wyrażeniu interpolowane:

[!code-csharp-interactive[example with ternary conditional operator](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#3)]

Rozpoczyna się od ciągu dosłownego wyrażenia interpolowane `$` następuje znak `@` znaków. Aby uzyskać więcej informacji na temat ciągi verbatim zobacz [ciąg](../keywords/string.md) i [dosłownego wyrażenia identyfikator](verbatim.md) tematów.

> [!NOTE]
> `$` Token musi występować przed `@` token w ciągu interpolowanym dosłownego wyrażenia.

## <a name="implicit-conversions-and-specifying-iformatprovider-implementation"></a>Niejawne konwersje i określając `IFormatProvider` implementacji

Istnieją trzy niejawną konwersję z ciągu interpolowanym:

1. Konwersja ciągu interpolowanym do <xref:System.String> wystąpienie, które jest wynikiem rozdzielczość ciągu interpolowanym interpolowanego wyrażenia elementów zastępowane z reprezentacji ciągu prawidłowo sformatowane ich wyników. Ta konwersja używa bieżącej kultury.

1. Konwersja ciągu interpolowanym do <xref:System.FormattableString> wystąpienie, które reprezentuje ciąg formatu złożonego wraz z wynikiem wyrażenia do sformatowania. Który umożliwia tworzenie wielu ciągów wyników z specyficzne dla kultury zawartości z jednej <xref:System.FormattableString> wystąpienia. Robić, które wywołują jedną z następujących metod:

      - A <xref:System.FormattableString.ToString> przeciążenia, które tworzy ciąg wynik <xref:System.Globalization.CultureInfo.CurrentCulture>.
      - <xref:System.FormattableString.Invariant%2A> Metodę, która tworzy ciąg wynik <xref:System.Globalization.CultureInfo.InvariantCulture>.
      - A <xref:System.FormattableString.ToString(System.IFormatProvider)> metodę, która tworzy ciąg wynik określonej kultury.

    Można też użyć <xref:System.FormattableString.ToString(System.IFormatProvider)> metodę, aby udostępnić implementację użytkownika <xref:System.IFormatProvider> interfejsu, który obsługuje niestandardowe formatowanie. Aby uzyskać więcej informacji, zobacz [niestandardowe formatowanie ICustomFormatter](../../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter).

1. Konwersja ciągu interpolowanym do <xref:System.IFormattable> ciągi wystąpienie, które umożliwia tworzenie wielu wyników z zawartością specyficzne dla kultury z jednej <xref:System.IFormattable> wystąpienia.

W poniższym przykładzie użyto niejawnej konwersji <xref:System.FormattableString> można utworzyć ciągów wynikowych specyficzne dla kultury:

[!code-csharp-interactive[create culture-specific result strings](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#4)]

## <a name="additional-resources"></a>Dodatkowe zasoby

Jeśli jesteś nowym użytkownikiem interpolacji ciągu, zobacz [ciągu interpolacji w języku C#](../../quick-starts/interpolated-strings.yml) Szybki Start. Aby uzyskać więcej przykładów, zobacz [ciągu interpolacji w języku C#](../../tutorials/string-interpolation.md) samouczka.

## <a name="see-also"></a>Zobacz także  
 <xref:System.String.Format%2A?displayProperty=nameWithType>  
 <xref:System.FormattableString?displayProperty=nameWithType>  
 <xref:System.IFormattable?displayProperty=nameWithType>  
 [Złożone formatowanie](../../../standard/base-types/composite-formatting.md)  
 [Ciągi](../../programming-guide/strings/index.md)  
 [Przewodnik programowania w języku C#](../../programming-guide/index.md)  
 [Znaki specjalne języka C#](index.md)  
 [Odwołanie w C#](../index.md)  