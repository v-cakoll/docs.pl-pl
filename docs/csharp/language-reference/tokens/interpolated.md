---
title: $ - interpolacja ciągu - odwołanie do języka C#
description: Interpolacja ciągów zapewnia bardziej czytelną i wygodną składnię formatowania danych wyjściowych ciągu niż tradycyjne formatowanie kompozytowe ciągów.
ms.date: 09/02/2019
f1_keywords:
- $_CSharpKeyword
- $
helpviewer_keywords:
- $ special character [C#]
- string interpolation [C#]
- interpolated string [C#]
author: pkulikov
ms.openlocfilehash: 2b95fa5fe5cecd4825e8c17a33f7795c6c9480c6
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738375"
---
# <a name="---string-interpolation-c-reference"></a>$ - interpolacja ciągu (odwołanie do języka C#)

Znak `$` specjalny identyfikuje literał ciągu jako *interpolowany ciąg*. Interpolowany ciąg jest literałem ciągu, który może zawierać *wyrażenia interpolacji*. Gdy interpolowany ciąg jest rozpoznawany do ciągu wynikowego, elementy z wyrażeniami interpolacji są zastępowane przez reprezentacje ciągu wyników wyrażenia. Ta funkcja jest dostępna począwszy od języka C# 6.

Interpolacja ciągów zapewnia bardziej czytelną i wygodną składnię do tworzenia sformatowanych ciągów niż funkcja [formatowania złożonego ciągu.](../../../standard/base-types/composite-formatting.md) W poniższym przykładzie użyto obu funkcji do uzyskania tego samego wyjścia:

[!code-csharp-interactive[compare with composite formatting](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#1)]

## <a name="structure-of-an-interpolated-string"></a>Struktura interpolowanego ciągu

Aby zidentyfikować literał ciągu jako interpolowany ciąg, `$` należy dołączyć go do symbolu. Nie można mieć żadnych `$` odstępów `"` między i który uruchamia literał ciągu.

Struktura elementu z wyrażeniem interpolacji jest następująca:

```csharp
{<interpolationExpression>[,<alignment>][:<formatString>]}
```

Elementy w nawiasach kwadratowych są opcjonalne. W poniższej tabeli opisano każdy element:

|Element|Opis|
|-------------|-----------------|
|`interpolationExpression`|Wyrażenie, które daje wynik do sformatowania. Reprezentacja `null` ciągów jest <xref:System.String.Empty?displayProperty=nameWithType>.|
|`alignment`|Wyrażenie stałe, którego wartość definiuje minimalną liczbę znaków w reprezentacji ciągu wyniku wyrażenia. Jeśli jest dodatnia, reprezentacja ciągu jest wyrównana do prawej; jeśli jest ujemna, jest wyrównana do lewej. Aby uzyskać więcej informacji, zobacz [Komponent wyrównania](../../../standard/base-types/composite-formatting.md#alignment-component).|
|`formatString`|Ciąg formatu, który jest obsługiwany przez typ wyniku wyrażenia. Aby uzyskać więcej informacji, zobacz [Formatowanie składnika ciągów](../../../standard/base-types/composite-formatting.md#format-string-component).|

W poniższym przykładzie użyto opisanych powyżej składników formatowania opcjonalnego:

[!code-csharp-interactive[specify alignment and format string](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#2)]

## <a name="special-characters"></a>Znaki specjalne

Aby uwzględnić nawias klamrowy "{" lub "}", w tekście wywoływanym przez interpolowany ciąg, użyj dwóch nawiasów klamrowych, "{{" lub "}}". Aby uzyskać więcej informacji, zobacz [Ucieczka szelki](../../../standard/base-types/composite-formatting.md#escaping-braces).

Ponieważ dwukropek (":") ma specjalne znaczenie w elemencie interpolacji, aby użyć [operatora warunkowego](../operators/conditional-operator.md) w wyrażeniu interpolacji, ująć to wyrażenie w nawiasy.

W poniższym przykładzie pokazano, jak dołączyć nawias klamrowy w ciągu wynikowym i jak używać operatora warunkowego w wyrażeniu interpolacji:

[!code-csharp-interactive[example with ternary conditional operator](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#3)]

Interpolowany ciąg dosłowny zaczyna `$` się od `@` znaku, po którym następuje znak. Aby uzyskać więcej informacji na temat ciągów dosłownie, zobacz [ciąg](../builtin-types/reference-types.md) i dosłownie tematów [identyfikatora.](verbatim.md)

> [!NOTE]
> Począwszy od języka C# 8.0, można użyć `$` i `$@"..."` `@$"..."` `@` tokeny w dowolnej kolejności: zarówno i są prawidłowe interpolowane ciągi dosłownie. We wcześniejszych wersjach `$` języka C# `@` token musi pojawić się przed tokenem.

## <a name="implicit-conversions-and-how-to-specify-iformatprovider-implementation"></a>Konwersje niejawne `IFormatProvider` i sposób określania implementacji

Istnieją trzy niejawne konwersje z interpolowanego ciągu:

1. Konwersja interpolowanego ciągu <xref:System.String> na wystąpienie, które jest wynikiem interpolowanej rozdzielczości ciągu z elementami wyrażenia interpolacji, które są zastępowane prawidłowo sformatowanymi reprezentacjami ciągów ich wyników. Ta konwersja <xref:System.Globalization.CultureInfo.CurrentCulture> używa do formatowania wyników wyrażeń.

1. Konwersja interpolowanego ciągu <xref:System.FormattableString> do wystąpienia reprezentującego ciąg formatu złożonego wraz z wynikami wyrażenia, które mają być sformatowane. Dzięki temu można utworzyć wiele ciągów wyników z <xref:System.FormattableString> zawartością specyficzne dla kultury z jednego wystąpienia. Aby to zrobić, należy wywołać jedną z następujących metod:

      - Przeciążenie, <xref:System.FormattableString.ToString> które tworzy ciąg <xref:System.Globalization.CultureInfo.CurrentCulture>wyników dla .
      - Metoda, <xref:System.FormattableString.Invariant%2A> która tworzy ciąg wyników <xref:System.Globalization.CultureInfo.InvariantCulture>dla .
      - Metoda, <xref:System.FormattableString.ToString(System.IFormatProvider)> która tworzy ciąg wyników dla określonej kultury.

    Można również użyć <xref:System.FormattableString.ToString(System.IFormatProvider)> tej metody, aby zapewnić <xref:System.IFormatProvider> implementację zdefiniowaną przez użytkownika interfejsu, który obsługuje formatowanie niestandardowe. Aby uzyskać więcej informacji, zobacz sekcję [Formatowanie niestandardowe za pomocą formatowania ICustomformatter](../../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter) typów formatowania w artykule [.NET.](../../../standard/base-types/formatting-types.md)

1. Konwersja interpolowanego ciągu <xref:System.IFormattable> do wystąpienia, które umożliwia również tworzenie wielu ciągów wyników <xref:System.IFormattable> z zawartością specyficzną dla kultury z jednego wystąpienia.

W poniższym przykładzie <xref:System.FormattableString> użyto konwersji niejawnej w celu utworzenia ciągów wyników specyficznych dla kultury:

[!code-csharp-interactive[create culture-specific result strings](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#4)]

## <a name="additional-resources"></a>Dodatkowe zasoby

Jeśli jesteś nowy do interpolacji ciągów, zobacz [Interpolacji ciągów w języku C#](../../tutorials/exploration/interpolated-strings.yml) interaktywny samouczek. Można również sprawdzić inną [interpolację ciągów w](../../tutorials/string-interpolation.md) samouczku języka C#, który pokazuje, jak używać interpolowanych ciągów do tworzenia sformatowanych ciągów.

## <a name="compilation-of-interpolated-strings"></a>Kompilacja interpolowanych ciągów

Jeśli interpolowany ciąg ma `string`typ , zazwyczaj jest <xref:System.String.Format%2A?displayProperty=nameWithType> przekształcany w wywołanie metody. Kompilator może <xref:System.String.Format%2A?displayProperty=nameWithType> <xref:System.String.Concat%2A?displayProperty=nameWithType> zastąpić, jeśli analizowane zachowanie byłoby równoważne łączenia.

Jeśli interpolowany ciąg ma <xref:System.IFormattable> <xref:System.FormattableString>typ lub kompilator generuje <xref:System.Runtime.CompilerServices.FormattableStringFactory.Create%2A?displayProperty=nameWithType> wywołanie metody.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [interpolowane ciągi](~/_csharplang/spec/expressions.md#interpolated-strings) sekcji [specyfikacji języka C#.](~/_csharplang/spec/introduction.md)

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Znaki specjalne języka C#](index.md)
- [Ciągi](../../programming-guide/strings/index.md)
- [Standardowe ciągi formatujące liczby](../../../standard/base-types/standard-numeric-format-strings.md)
- [Złożone formatowanie](../../../standard/base-types/composite-formatting.md)
- <xref:System.String.Format%2A?displayProperty=nameWithType>
