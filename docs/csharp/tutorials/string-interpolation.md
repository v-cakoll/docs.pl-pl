---
title: Interpolacja ciągów w języku C#
description: Dowiedz się, jak obejmują wyrażenie sformatowane wyniki w ciągu wynikowym w języku C# przy użyciu interpolacji ciągu.
author: pkulikov
ms.date: 05/09/2018
ms.openlocfilehash: 2990298821fddc8a69430a4cf4bb5e3dd9df314d
ms.sourcegitcommit: 26f4a7697c32978f6a328c89dc4ea87034065989
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/28/2019
ms.locfileid: "66251031"
---
# <a name="string-interpolation-in-c"></a>Interpolacja ciągów w języku C\#

W tym samouczku dowiesz się, jak używać [Interpolacja ciągów](../language-reference/tokens/interpolated.md) do formatu i Dołącz wyniki wyrażenia w ciągu wynikowym. W przykładach założono, że znasz podstawowe pojęcia języka C# i .NET typu formatowania. Jeśli jesteś nowym użytkownikiem Interpolacja ciągów lub formatowanie typu .NET, zapoznaj się z [samouczek interpolacji ciągu interaktywne](exploration/interpolated-strings.yml) pierwszy. Aby uzyskać więcej informacji na temat typy formatowania w programie .NET, zobacz [typy formatowania na platformie .NET](../../standard/base-types/formatting-types.md) tematu.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

## <a name="introduction"></a>Wprowadzenie

[Interpolacja ciągów](../language-reference/tokens/interpolated.md) funkcja jest wbudowana w górnej części [formatowania złożonego](../../standard/base-types/composite-formatting.md) funkcji i zapewnia bardziej czytelne i wygodne składni obejmujący wyrażenie sformatowane wyniki w ciągu wynikowym.

Aby zidentyfikować literał ciągu zgodny z ciągu interpolowanego, dodaj ją za pomocą `$` symboli. Możesz osadzić dowolne prawidłowe C# wyrażenie zwracające wartość w ciągu interpolowanym. W poniższym przykładzie tak szybko, jak wyrażenie jest obliczane, wynik jest konwertowana na ciąg i zawarte w ciągu wynikowym:

[!code-csharp-interactive[string interpolation example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#1)]

Jak pokazano w przykładzie, dołączysz wyrażenia w ciągu interpolowanym umieszczając go w nawiasy klamrowe:

```
{<interpolationExpression>}
```

Ciągi interpolowane obsługują wszystkie funkcje [ciągu formatowania złożonego](../../standard/base-types/composite-formatting.md) funkcji. Dzięki temu ich czytelność alternatywą do korzystania z <xref:System.String.Format%2A?displayProperty=nameWithType> metody.

## <a name="how-to-specify-a-format-string-for-an-interpolation-expression"></a>Jak określić wyrażenie interpolacji ciągu formatu

Należy określić ciąg formatu, który jest obsługiwany przez typ wyniku wyrażenia, postępując zgodnie z wyrażenia interpolacji z dwukropkiem (":") i ciąg formatu:

```
{<interpolationExpression>:<formatString>}
```

Poniższy przykład pokazuje, jak określić ciągi formatów standardowych i niestandardowych wyrażeń, które tworzą daty i godziny lub wyników liczbowych:

[!code-csharp-interactive[format string example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#2)]

Aby uzyskać więcej informacji, zobacz [element ciągu formatującego](../../standard/base-types/composite-formatting.md#format-string-component) części [formatowania złożonego](../../standard/base-types/composite-formatting.md) tematu. Tę sekcję zawiera łącza do tematów opisujących ciągów formatu standardowego i niestandardowego obsługiwanych przez typów podstawowych platformy .NET.

## <a name="how-to-control-the-field-width-and-alignment-of-the-formatted-interpolation-expression"></a>Jak kontrolować szerokość pola i wyrównania wyrażeń interpolacji sformatowany

Określ szerokość minimalna pola i wyrównanie wyniku wyrażenia sformatowane wykonując wyrażenie interpolacji za pomocą przecinka (",") i wyrażenie stałe:

```
{<interpolationExpression>,<alignment>}
```

Jeśli *wyrównanie* wartość jest dodatnia, wynik wyrażenia sformatowane jest wyrównany do prawej; Jeśli jest negatywny, jest wyrównany do lewej.

Jeśli musisz określić wyrównania i ciąg formatu, rozpoczynać składnik wyrównania:

```
{<interpolationExpression>,<alignment>:<formatString>}
```

Poniższy przykład pokazuje, jak określić wyrównania i używa potoku znaków ("|") do rozdzielenia pól tekstowych:

[!code-csharp-interactive[alignment example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#3)]

Jako przykład przedstawiono dane wyjściowe, jeśli długość wyniku wyrażenia sformatowane przekracza określony szerokość pola *wyrównanie* wartość jest ignorowana.

Aby uzyskać więcej informacji, zobacz [składnik wyrównania](../../standard/base-types/composite-formatting.md#alignment-component) części [formatowania złożonego](../../standard/base-types/composite-formatting.md) tematu.

## <a name="how-to-use-escape-sequences-in-an-interpolated-string"></a>Jak używać sekwencje ucieczki w ciągu interpolowanym

Ciągi interpolowane obsługuje wszystkie sekwencje unikowe, które mogą być używane w literałach ciągu zwykłego. Aby uzyskać więcej informacji, zobacz [sekwencje ucieczki w ciągu](../programming-guide/strings/index.md#string-escape-sequences).

Aby interpretowany dosłownie sekwencje ucieczki, należy użyć [verbatim](../language-reference/tokens/verbatim.md) literału ciągu. Ciąg verbatim interpolowane zaczyna się od `$` następuje znak `@` znaków.

Aby uwzględnić nawiasu klamrowego, "{" lub "}", w ciągu wynikowym, użyj dwóch nawiasów klamrowych, "{{" lub "}}". Aby uzyskać więcej informacji, zobacz [anulowania zapewnianego element nawiasów klamrowych](../../standard/base-types/composite-formatting.md#escaping-braces) części [formatowania złożonego](../../standard/base-types/composite-formatting.md) tematu.

Poniższy przykład pokazuje, jak dołączyć nawiasy klamrowe w ciągu wynikowym i konstruowania verbatim ciągu interpolowanego:

[!code-csharp-interactive[escape sequence example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#4)]

## <a name="how-to-use-a-ternary-conditional-operator--in-an-interpolation-expression"></a>Jak używać trójargumentowy operator warunkowy `?:` w wyrażeniu interpolacji

Jako dwukropkiem (":") ma specjalne znaczenie w elemencie z wyrażeniem interpolacji, aby można było używać [operator warunkowy](../language-reference/operators/conditional-operator.md) w wyrażeniu, należy ją ująć w nawiasy, co ilustruje poniższy przykład:

[!code-csharp-interactive[conditional operator example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#5)]

## <a name="how-to-create-a-culture-specific-result-string-with-string-interpolation"></a>Jak utworzyć ciąg wynikowy specyficzne dla kultury za pomocą Interpolacja ciągów

Domyślnie ciągu interpolowanego używa bieżącej kultury, które są definiowane przez <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType> właściwości dla wszystkich operacji formatowania. Użyj niejawnej konwersji ciągu interpolowanego do <xref:System.FormattableString?displayProperty=nameWithType> wystąpienie i wywołania jego <xref:System.FormattableString.ToString(System.IFormatProvider)> metodę, aby utworzyć ciąg wynikowy specyficzne dla kultury. Poniższy przykład pokazuje, jak to zrobić:

[!code-csharp-interactive[specify different cultures](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#6)]

Jak pokazano w przykładzie, możesz użyć jednego <xref:System.FormattableString> wystąpienia do generowania wielu ciągi wyników dla różnych kultur.

## <a name="how-to-create-a-result-string-using-the-invariant-culture"></a>Jak utworzyć ciąg wynikowy, przy użyciu niezmiennej kultury

Wraz z <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> metody, można użyć statycznej <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> metodą rozwiązania ciągu interpolowanego na ciąg wyniku do <xref:System.Globalization.CultureInfo.InvariantCulture>. Poniższy przykład pokazuje, jak to zrobić:

[!code-csharp-interactive[format with invariant culture](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#7)]

## <a name="conclusion"></a>Wniosek

W tym samouczku opisano typowe scenariusze użycia interpolacji ciągu. Aby uzyskać więcej informacji na temat Interpolacja ciągów, zobacz [Interpolacja ciągów](../language-reference/tokens/interpolated.md) tematu. Aby uzyskać więcej informacji na temat typy formatowania w programie .NET, zobacz [typy formatowania na platformie .NET](../../standard/base-types/formatting-types.md) i [formatowania złożonego](../../standard/base-types/composite-formatting.md) tematów.

## <a name="see-also"></a>Zobacz także

- <xref:System.String.Format%2A?displayProperty=nameWithType>
- <xref:System.FormattableString?displayProperty=nameWithType>
- <xref:System.IFormattable?displayProperty=nameWithType>
- [Ciągi](../programming-guide/strings/index.md)
