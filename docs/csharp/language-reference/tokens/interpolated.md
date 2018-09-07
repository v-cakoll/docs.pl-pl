---
title: $ — Interpolacja ciągów (odwołanie w C#)
description: Interpolacja ciągów pozwala bardziej czytelne i wygodne składni do formatowania danych wyjściowych ciąg znaków, niż tradycyjne ciągu formatowania złożonego.
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
ms.openlocfilehash: 2009b3620bc4874520221a4ea847222feafca01b
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44065412"
---
# <a name="---string-interpolation-c-reference"></a>$ — Interpolacja ciągów (odwołanie w C#)

`$` Znak specjalny identyfikuje literał ciągu zgodny z *ciągiem interpolowanym*. Ciągu interpolowanego jest ciągiem literału, który może zawierać *wyrażeń interpolowanych*. Po usunięciu ciągu interpolowanego do ciągu wynikowego, elementy z wyrażeń interpolowanych są zastępowane przez ciągów reprezentujących wyniki wyrażenia. Ta funkcja jest dostępna w języku C# 6 i nowsze wersje języka.

Interpolacja ciągów pozwala bardziej czytelne i wygodne składni utworzyć sformatowane ciągi niż [ciągu formatowania złożonego](../../../standard/base-types/composite-formatting.md) funkcji. W poniższym przykładzie użyto obu funkcji, aby utworzyć ten sam wynik:

[!code-csharp-interactive[compare with composite formatting](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#1)]

## <a name="structure-of-an-interpolated-string"></a>Struktura ciągu interpolowanego

Aby zidentyfikować literał ciągu zgodny z ciągu interpolowanego, dodaj ją za pomocą `$` symboli. Nie może mieć dowolny biały obszar między `$` i `"` którego początkowe literału ciągu. Ten sposób powoduje błąd kompilacji.

Struktura element na wyrażenie interpolowane jest następująca:

```
{<interpolatedExpression>[,<alignment>][:<formatString>]}
```

Elementy w nawiasach kwadratowych są opcjonalne. W poniższej tabeli opisano każdy element:

|Element|Opis|
|-------------|-----------------|
|`interpolatedExpression`|Wyrażenie, które daje wynik do sformatowania. Ciąg reprezentujący `null` wynik jest <xref:System.String.Empty?displayProperty=nameWithType>.|
|`alignment`|Wyrażenie stałe, którego wartość określa minimalną liczbę znaków w ciągu reprezentującego wynik wyrażenia interpolowane. Jeśli jest to dodatnia, reprezentacji w postaci ciągu jest wyrównany do prawej; Jeśli jest negatywny, jest wyrównany do lewej. Aby uzyskać więcej informacji, zobacz [składnik wyrównania](../../../standard/base-types/composite-formatting.md#alignment-component).|
|`formatString`|Ciąg formatu, który jest obsługiwany przez typ wyniku wyrażenia. Aby uzyskać więcej informacji, zobacz [element ciągu formatującego](../../../standard/base-types/composite-formatting.md#format-string-component).|

W poniższym przykładzie użyto opcjonalne składniki formatowania opisane powyżej:

[!code-csharp-interactive[specify alignment and format string](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#2)]

## <a name="special-characters"></a>Znaki specjalne

Aby uwzględnić nawiasu klamrowego, "{" lub "}", w tekście, generowane przez ciągu interpolowanego, użyj dwóch nawiasów klamrowych, "{{" lub "}}". Aby uzyskać więcej informacji, zobacz [anulowania zapewnianego element nawiasów klamrowych](../../../standard/base-types/composite-formatting.md#escaping-braces).

Jako dwukropkiem (":") ma specjalne znaczenie w elemencie wyrażenie interpolowane, aby można było używać [operator warunkowy](../operators/conditional-operator.md) w wyrażenie interpolowane ująć to wyrażenie w nawiasach.

Poniższy przykład pokazuje, jak dołączyć nawiasu klamrowego w ciągu wynikowym i sposobu użycia operatora warunkowego w wyrażenie interpolowane:

[!code-csharp-interactive[example with ternary conditional operator](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#3)]

Ciąg verbatim interpolowane zaczyna się od `$` następuje znak `@` znaków. Aby uzyskać więcej informacji na temat ciągi verbatim zobacz [ciąg](../keywords/string.md) i [identyfikator dosłownego wyrażenia](verbatim.md) tematów.

> [!NOTE]
> `$` Tokenu musi występować przed `@` tokenu w verbatim ciągu interpolowanym.

## <a name="implicit-conversions-and-specifying-iformatprovider-implementation"></a>Niejawne konwersje i określając `IFormatProvider` implementacji

Istnieją trzy niejawną konwersję z ciągu interpolowanego:

1. Konwersja ciągu interpolowanego do <xref:System.String> wystąpienia, która jest wynikiem rozdzielczość ciąg interpolowany z wyrażenia interpolowanego elementy zastępowane poprawnie sformatowanych ciągów reprezentujących ich wyniki. Ta konwersja skorzysta z bieżącej kultury.

1. Konwersja ciągu interpolowanego do <xref:System.FormattableString> wystąpienia, która reprezentuje ciąg formatu złożonego wraz z wynikami wyrażenia do sformatowania. Pozwala to do utworzenia wielu ciągów wynik z specyficzne dla kultury zawartości z jednego <xref:System.FormattableString> wystąpienia. Który wywołać jedną z następujących metod:

      - A <xref:System.FormattableString.ToString> przeciążenia, które tworzy ciąg wyniku <xref:System.Globalization.CultureInfo.CurrentCulture>.
      - <xref:System.FormattableString.Invariant%2A> Metodę, która tworzy ciąg wyniku <xref:System.Globalization.CultureInfo.InvariantCulture>.
      - A <xref:System.FormattableString.ToString(System.IFormatProvider)> metodę, która daje ciąg wynikowy dla określonej kultury.

    Możesz również użyć <xref:System.FormattableString.ToString(System.IFormatProvider)> metodę, aby udostępnić implementację zdefiniowanych przez użytkownika z <xref:System.IFormatProvider> interfejsu, który obsługuje formatowanie niestandardowe. Aby uzyskać więcej informacji, zobacz [niestandardowe formatowanie z ICustomFormatter](../../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter).

1. Konwersja ciągu interpolowanego do <xref:System.IFormattable> ciągi specyficzne dla kultury zawartości z jednego wystąpienia, które umożliwia również tworzenie wielu wyników <xref:System.IFormattable> wystąpienia.

W poniższym przykładzie użyto niejawnej konwersji <xref:System.FormattableString> utworzyć ciągi wynikowe charakterystyczne dla kultury:

[!code-csharp-interactive[create culture-specific result strings](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#4)]

## <a name="additional-resources"></a>Dodatkowe zasoby

Jeśli jesteś nowym użytkownikiem Interpolacja ciągów, zobacz [Interpolacja w języku C# ciągów](../../quick-starts/interpolated-strings.yml) Szybki Start. Aby uzyskać więcej przykładów, zobacz [Interpolacja w języku C# ciągów](../../tutorials/string-interpolation.md) samouczka.

## <a name="see-also"></a>Zobacz także

- <xref:System.String.Format%2A?displayProperty=nameWithType>
- <xref:System.FormattableString?displayProperty=nameWithType>
- <xref:System.IFormattable?displayProperty=nameWithType>
- [Złożone formatowanie](../../../standard/base-types/composite-formatting.md)
- [Ciągi](../../programming-guide/strings/index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Znaki specjalne języka C#](index.md)
- [Dokumentacja języka C#](../index.md)
