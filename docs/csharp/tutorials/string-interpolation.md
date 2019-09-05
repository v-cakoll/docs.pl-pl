---
title: Interpolacja ciągów wC#
description: Dowiedz się, jak dołączać sformatowane wyniki wyrażenia w C# ciągu wynikowym przy użyciu interpolacji ciągów.
author: pkulikov
ms.date: 09/02/2019
ms.openlocfilehash: d3a3a08d5911b5323aa61c571f05318d10380339
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252926"
---
# <a name="string-interpolation-in-c"></a>Interpolacja ciągów w języku C\#

W tym samouczku pokazano, jak używać [interpolacji ciągów](../language-reference/tokens/interpolated.md) do formatowania i dołączania wyników wyrażenia w ciągu wynikowym. W przykładach założono, że znasz podstawowe C# pojęcia i formatowanie typów .NET. Jeśli jesteś nowym programem do interpolacji ciągów lub formatowania typu .NET, najpierw zapoznaj się z [samouczkiem Interpolacja ciągów interaktywnych](exploration/interpolated-strings.yml) . Aby uzyskać więcej informacji na temat formatowania typów w programie .NET, zobacz [Typy formatowania w temacie .NET](../../standard/base-types/formatting-types.md) .

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

## <a name="introduction"></a>Wprowadzenie

Funkcja [interpolacji ciągu](../language-reference/tokens/interpolated.md) jest tworzona na podstawie funkcji [formatowania złożonego](../../standard/base-types/composite-formatting.md) i zapewnia bardziej czytelną i wygodną składnię, aby dołączać sformatowane wyniki wyrażeń do ciągu wynikowego.

Aby zidentyfikować literał ciągu jako ciąg interpolowany, poprzedź go `$` symbolem. Można osadzić dowolne prawidłowe C# Wyrażenie zwracające wartość w ciągu interpolowanym. W poniższym przykładzie, zaraz po obliczeniu wyrażenia, jego wynik jest konwertowany na ciąg i uwzględniony w ciągu wynikowym:

[!code-csharp-interactive[string interpolation example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#1)]

Jak pokazano w przykładzie, można uwzględnić wyrażenie w ciągu interpolowanym, umieszczając je w nawiasach klamrowych:

```csharp
{<interpolationExpression>}
```

Ciągi interpolowane obsługują wszystkie możliwości funkcji [formatowania złożonego w ciągu](../../standard/base-types/composite-formatting.md) . Sprawia, że są one bardziej czytelną alternatywą dla użycia <xref:System.String.Format%2A?displayProperty=nameWithType> metody.

## <a name="how-to-specify-a-format-string-for-an-interpolation-expression"></a>Jak określić ciąg formatu dla wyrażenia interpolacji

Należy określić ciąg formatu, który jest obsługiwany przez typ wyniku wyrażenia, wykonując wyrażenie interpolacji z dwukropkiem (":") i ciągiem formatu:

```csharp
{<interpolationExpression>:<formatString>}
```

Poniższy przykład ilustruje sposób określania standardowych i niestandardowych ciągów formatu dla wyrażeń, które tworzą datę i godzinę lub wyniki liczbowe:

[!code-csharp-interactive[format string example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#2)]

Aby uzyskać więcej informacji, zobacz sekcję [Format składnika ciągu](../../standard/base-types/composite-formatting.md#format-string-component) w temacie [formatowanie złożone](../../standard/base-types/composite-formatting.md) . Ta sekcja zawiera linki do tematów, które opisują standardowe i niestandardowe ciągi formatujące obsługiwane przez typy podstawowe programu .NET.

## <a name="how-to-control-the-field-width-and-alignment-of-the-formatted-interpolation-expression"></a>Kontrolowanie szerokości pola i wyrównania sformatowanego wyrażenia interpolacji

Należy określić minimalną szerokość pola i wyrównanie sformatowanego wyniku wyrażenia, wykonując wyrażenie interpolacji z przecinkiem (",") i wyrażeniem stałym:

```csharp
{<interpolationExpression>,<alignment>}
```

Jeśli wartość *wyrównania* jest dodatnia, wynik sformatowanego wyrażenia jest wyrównany do prawej; Jeśli wartość jest ujemna, jest wyrównana do lewej.

Jeśli musisz określić zarówno wyrównanie, jak i ciąg formatu, Rozpocznij od składnika wyrównania:

```csharp
{<interpolationExpression>,<alignment>:<formatString>}
```

Poniższy przykład pokazuje, jak określić wyrównanie i używa znaków potoku ("|") do rozgraniczania pól tekstowych:

[!code-csharp-interactive[alignment example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#3)]

Jak przykładowe dane wyjściowe są wyświetlane, jeśli długość sformatowanego wyniku wyrażenia przekroczy określoną szerokość pola, wartość *wyrównania* jest ignorowana.

Aby uzyskać więcej informacji, zobacz sekcję [wyrównania składnika](../../standard/base-types/composite-formatting.md#alignment-component) w temacie [formatowanie złożone](../../standard/base-types/composite-formatting.md) .

## <a name="how-to-use-escape-sequences-in-an-interpolated-string"></a>Jak używać sekwencji unikowych w ciągu interpolowanym

Ciągi interpolowane obsługują wszystkie sekwencje unikowe, które mogą być używane w zwykłych literałach ciągu. Aby uzyskać więcej informacji, zobacz [Sekwencje ucieczki ciągów](../programming-guide/strings/index.md#string-escape-sequences).

Aby interpretować sekwencje ucieczki dosłownie, użyj literału ciągu [Verbatim](../language-reference/tokens/verbatim.md) . Interpolowany ciąg Verbatim rozpoczyna się od znaku `$` , po którym następuje `@` znak. Począwszy od C# 8,0, można użyć `$` tokenów i `@` w dowolnej kolejności: oba `$@"..."` i `@$"..."` są prawidłowymi interpolowanymi ciągami Verbatim.

Aby dołączyć nawias klamrowy "{" lub "}" w ciągu wynikowym, użyj dwóch nawiasów klamrowych "{{" lub "}}". Aby uzyskać więcej informacji, zobacz sekcję [ucieczki nawiasów klamrowych](../../standard/base-types/composite-formatting.md#escaping-braces) tematu [formatowanie złożone](../../standard/base-types/composite-formatting.md) .

Poniższy przykład pokazuje, jak uwzględnić nawiasy klamrowe w ciągu wynikowym i utworzyć ciąg interpolowany Verbatim:

[!code-csharp-interactive[escape sequence example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#4)]

## <a name="how-to-use-a-ternary-conditional-operator--in-an-interpolation-expression"></a>Jak używać operatora `?:` warunkowego Trzyelementowy w wyrażeniu interpolacji

Ponieważ dwukropek (":") ma specjalne znaczenie w elemencie z wyrażeniem interpolacji, aby użyć [operatora warunkowego](../language-reference/operators/conditional-operator.md) w wyrażeniu, należy ująć go w nawiasy, jak pokazano na poniższym przykładzie:

[!code-csharp-interactive[conditional operator example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#5)]

## <a name="how-to-create-a-culture-specific-result-string-with-string-interpolation"></a>Jak utworzyć ciąg wyniku specyficzny dla kultury przy użyciu interpolacji ciągów

Domyślnie ciąg interpolowany używa bieżącej kultury zdefiniowanej przez <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType> właściwość dla wszystkich operacji formatowania. Użyj niejawnej konwersji ciągu interpolowanego na <xref:System.FormattableString?displayProperty=nameWithType> wystąpienie i <xref:System.FormattableString.ToString(System.IFormatProvider)> Wywołaj metodę, aby utworzyć ciąg wyniku specyficzny dla kultury. Poniższy przykład pokazuje, jak to zrobić:

[!code-csharp-interactive[specify different cultures](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#6)]

Jak pokazano w przykładzie, można użyć jednego <xref:System.FormattableString> wystąpienia do generowania wielu ciągów wynikowych dla różnych kultur.

## <a name="how-to-create-a-result-string-using-the-invariant-culture"></a>Jak utworzyć ciąg wynikowy przy użyciu niezmiennej kultury

Wraz z <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> metodą można użyć statycznej <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> metody do rozpoznawania ciągu interpolowanego do ciągu wynikowego dla <xref:System.Globalization.CultureInfo.InvariantCulture>. Poniższy przykład pokazuje, jak to zrobić:

[!code-csharp-interactive[format with invariant culture](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#7)]

## <a name="conclusion"></a>Wniosek

W tym samouczku opisano typowe scenariusze użycia interpolacji ciągów. Aby uzyskać więcej informacji na temat interpolacji ciągów, zobacz temat [Interpolacja ciągów](../language-reference/tokens/interpolated.md) . Aby uzyskać więcej informacji na temat formatowania typów w programie .NET, zobacz [Typy formatowania w temacie .NET](../../standard/base-types/formatting-types.md) i [formatowanie złożone](../../standard/base-types/composite-formatting.md) .

## <a name="see-also"></a>Zobacz także

- <xref:System.String.Format%2A?displayProperty=nameWithType>
- <xref:System.FormattableString?displayProperty=nameWithType>
- <xref:System.IFormattable?displayProperty=nameWithType>
- [Ciągi](../programming-guide/strings/index.md)
