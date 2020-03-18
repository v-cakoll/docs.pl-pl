---
title: 'Interpolacja ciągów w C #'
description: Dowiedz się, jak dołączyć sformatowane wyniki wyrażenia w ciągu wyników w języku C# z interpolacją ciągów.
author: pkulikov
ms.technology: csharp-fundamentals
ms.date: 09/02/2019
ms.openlocfilehash: b901ae661ebd4af625d9f3c999b0eb50dda1990d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "73039212"
---
# <a name="string-interpolation-in-c"></a>Interpolacja ciągów w C\#

W tym samouczku pokazano, jak używać [interpolacji ciągów](../language-reference/tokens/interpolated.md) do formatowania i uwzględniania wyników wyrażeń w ciągu wyników. W przykładach przyjęto założenie, że znasz podstawowe pojęcia języka C# i formatowanie typu .NET. Jeśli dopiero powszawisz się interpolacją ciągów lub formatowaniem typu .NET, najpierw zapoznaj się z [interaktywnym samouczkiem interpolacji ciągów.](exploration/interpolated-strings.yml) Aby uzyskać więcej informacji na temat typów formatowania w .NET, zobacz [temat Typy formatowania w .NET.](../../standard/base-types/formatting-types.md)

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

## <a name="introduction"></a>Wprowadzenie

Funkcja [interpolacji ciągów](../language-reference/tokens/interpolated.md) jest zbudowana na złożonej funkcji [formatowania](../../standard/base-types/composite-formatting.md) i zapewnia bardziej czytelną i wygodną składnię w celu uwzględnienia sformatowanych wyników wyrażeń w ciągu wyników.

Aby zidentyfikować literał ciągu jako interpolowany ciąg, `$` należy go potoczyć symbolem. Można osadzić dowolne prawidłowe wyrażenie C#, które zwraca wartość w interpolowanym ciągu. W poniższym przykładzie, jak tylko wyrażenie jest oceniane, jego wynik jest konwertowany na ciąg i zawarte w ciągu wyników:

[!code-csharp-interactive[string interpolation example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#1)]

Jak pokazano w przykładzie, należy dołączyć wyrażenie do interpolowanego ciągu, załączając je nawiasami klamrowym:

```csharp
{<interpolationExpression>}
```

Interpolowane ciągi obsługują wszystkie możliwości funkcji [formatowania złożonego ciągu.](../../standard/base-types/composite-formatting.md) To czyni je bardziej czytelną alternatywą <xref:System.String.Format%2A?displayProperty=nameWithType> dla stosowania metody.

## <a name="how-to-specify-a-format-string-for-an-interpolation-expression"></a>Jak określić ciąg formatu dla wyrażenia interpolacji

Należy określić ciąg formatu, który jest obsługiwany przez typ wyniku wyrażenia, wykonując wyrażenie interpolacji z dwukropkiem (":") i ciągformatu:

```csharp
{<interpolationExpression>:<formatString>}
```

W poniższym przykładzie pokazano, jak określić standardowe i niestandardowe ciągi formatu dla wyrażeń, które generują datę i godzinę lub wyniki liczbowe:

[!code-csharp-interactive[format string example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#2)]

Aby uzyskać więcej informacji, zobacz sekcję [Formatowanie składników ciągów](../../standard/base-types/composite-formatting.md#format-string-component) w temacie [Formatowanie kompozytowe.](../../standard/base-types/composite-formatting.md) Ta sekcja zawiera łącza do tematów, które opisują standardowe i niestandardowe ciągi formatu obsługiwane przez typy podstawowe .NET.

## <a name="how-to-control-the-field-width-and-alignment-of-the-formatted-interpolation-expression"></a>Jak kontrolować szerokość pola i wyrównanie sformatowanego wyrażenia interpolacji

Minimalną szerokość pola i wyrównanie sformatowanego wyniku wyrażenia należy określić, wykonując wyrażenie interpolacji przecinkiem (""),) i wyrażeniem stałym:

```csharp
{<interpolationExpression>,<alignment>}
```

Jeśli wartość *wyrównania* jest dodatnia, wynik sformatowanego wyrażenia jest wyrównany do prawej; jeśli jest ujemna, jest wyrównana do lewej.

Jeśli konieczne jest określenie zarówno linii trasowania, jak i ciągu formatu, zacznij od komponentu wyrównania:

```csharp
{<interpolationExpression>,<alignment>:<formatString>}
```

W poniższym przykładzie pokazano, jak określić wyrównanie i używa znaków potoku ("|") do rozgraniczania pól tekstowych:

[!code-csharp-interactive[alignment example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#3)]

Jak pokazuje przykładowe dane wyjściowe, jeśli długość sformatowanego wyniku wyrażenia przekracza określoną szerokość pola, wartość *wyrównania* jest ignorowana.

Aby uzyskać więcej informacji, zobacz sekcję [Komponent wyrównanie](../../standard/base-types/composite-formatting.md#alignment-component) w temacie [Formatowanie kompozytowe.](../../standard/base-types/composite-formatting.md)

## <a name="how-to-use-escape-sequences-in-an-interpolated-string"></a>Jak używać sekwencji ucieczki w interpolowanym ciągu

Interpolowane ciągi obsługują wszystkie sekwencje ucieczki, które mogą być używane w zwykłych literałach ciągów. Aby uzyskać więcej informacji, zobacz [Sekwencje ucieczki ciągów](../programming-guide/strings/index.md#string-escape-sequences).

Aby interpretować sekwencje ucieczki dosłownie, należy użyć [dosłownego ciągu literał.](../language-reference/tokens/verbatim.md) Interpolowany ciąg dosłowny zaczyna `$` się od `@` znaku, po którym następuje znak. Począwszy od Języka C# 8.0, można użyć `$` i `$@"..."` `@$"..."` `@` tokeny w dowolnej kolejności: oba i są prawidłowe interpolowane ciągi dosłowne.

Aby dołączyć nawias klamrowy"{" lub "}", w ciągu wynikowym, należy użyć dwóch nawiasów klamrowych: "{{" lub "}}". Aby uzyskać więcej informacji, zobacz [sekcję Uciekanie nawiasów klamrowych](../../standard/base-types/composite-formatting.md#escaping-braces) w temacie [Formatowanie złożone.](../../standard/base-types/composite-formatting.md)

W poniższym przykładzie pokazano, jak uwzględnić nawiasy klamrowe w ciągu wyników i skonstruować dosłowny interpolowany ciąg:

[!code-csharp-interactive[escape sequence example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#4)]

## <a name="how-to-use-a-ternary-conditional-operator--in-an-interpolation-expression"></a>Jak używać operatora `?:` warunkowego ternary w wyrażeniu interpolacji

Jak dwukropek (":") ma szczególne znaczenie w elemencie z wyrażeniem interpolacji, w celu użycia [operatora warunkowego](../language-reference/operators/conditional-operator.md) w wyrażeniu, ujmować go w nawiasy, jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[conditional operator example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#5)]

## <a name="how-to-create-a-culture-specific-result-string-with-string-interpolation"></a>Jak utworzyć ciąg wyniku specyficzny dla kultury z interpolacją ciągu

Domyślnie interpolowany ciąg używa bieżącej kultury zdefiniowanej <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType> przez właściwość dla wszystkich operacji formatowania. Użyj niejawnej konwersji interpolowany <xref:System.FormattableString?displayProperty=nameWithType> ciąg do <xref:System.FormattableString.ToString(System.IFormatProvider)> wystąpienia i wywołać jego metodę, aby utworzyć ciąg wynik specyficzny dla kultury. W poniższym przykładzie pokazano, jak to zrobić:

[!code-csharp-interactive[specify different cultures](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#6)]

Jak pokazano w przykładzie, <xref:System.FormattableString> można użyć jednego wystąpienia do generowania wielu ciągów wyników dla różnych kultur.

## <a name="how-to-create-a-result-string-using-the-invariant-culture"></a>Jak utworzyć ciąg wynikowy przy użyciu kultury niezmiennej

Wraz z <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> metodą można użyć <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> metody statycznej, aby rozpoznać interpolowany ciąg <xref:System.Globalization.CultureInfo.InvariantCulture>do ciągu wynikowego dla . W poniższym przykładzie pokazano, jak to zrobić:

[!code-csharp-interactive[format with invariant culture](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#7)]

## <a name="conclusion"></a>Podsumowanie

W tym samouczku opisano typowe scenariusze użycia interpolacji ciągów. Aby uzyskać więcej informacji na temat interpolacji ciągów, zobacz [temat Interpolacji ciągów.](../language-reference/tokens/interpolated.md) Aby uzyskać więcej informacji na temat typów formatowania w .NET, zobacz [Tematy formatowania formatowania w .NET](../../standard/base-types/formatting-types.md) i composite tematów [formatowania.](../../standard/base-types/composite-formatting.md)

## <a name="see-also"></a>Zobacz też

- <xref:System.String.Format%2A?displayProperty=nameWithType>
- <xref:System.FormattableString?displayProperty=nameWithType>
- <xref:System.IFormattable?displayProperty=nameWithType>
- [Ciągi](../programming-guide/strings/index.md)
