---
title: Ciąg interpolacji w języku C#
description: Dowiedz się, jak zawiera wyrażenie sformatowane wyniki w wyniku ciąg w języku C# z interpolacji ciągu.
author: pkulikov
ms.date: 05/09/2018
ms.openlocfilehash: 3e463ceb0902658107280559b7fb57849beb8153
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
---
# <a name="string-interpolation-in-c"></a>Ciąg interpolacji w języku C# #

Ten samouczek przedstawia sposób użycia [ciągu interpolacji](../language-reference/tokens/interpolated.md) sformatowanie i dołączyć wyniki wyrażenia ciągu wynik. Przykładów założono, że czytelnik zna podstawowe pojęcia języka C# i formatowanie typu .NET. Jeśli jesteś nowym użytkownikiem interpolacji ciąg lub formatowania typu .NET, zapoznaj się [szybkiego startu interpolacji interakcyjne ciąg](../quick-starts/interpolated-strings.yml) pierwszy. Aby uzyskać więcej informacji na temat typy formatowania w .NET, zobacz [typy formatowania w .NET](../../standard/base-types/formatting-types.md) tematu.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

## <a name="introduction"></a>Wprowadzenie

[Ciągu interpolacji](../language-reference/tokens/interpolated.md) funkcji jest oparty na [złożone formatowanie](../../standard/base-types/composite-formatting.md) funkcji i zapewnia bardziej czytelny i wygodne składni zawiera wyrażenie sformatowane wyniki w ciągu wynik.

Aby zidentyfikować ciąg literału jako ciągu interpolowanym, dołączenie wartości za pomocą `$` symbolu. Można osadzić dowolne prawidłowe C# wyrażenie zwracające wartość w ciągu interpolowanym. W poniższym przykładzie, jak Obliczanie wyrażenia jego wynik jest konwertowana na ciąg i uwzględniona w parametrach wyników:

[!code-csharp-interactive[string interpolation example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#1)]

Co w przykładzie powyżej przedstawiono można użyć wyrażenia w ciągu interpolowanym należy ująć w nawiasy klamrowe:

```
{<interpolatedExpression>}
```

W czasie kompilacji ciągu interpolowanym zwykle jest przekształcana na <xref:System.String.Format%2A?displayProperty=nameWithType> wywołania metody. Dzięki temu wszystkie możliwości [ciągu formatowania złożonego](../../standard/base-types/composite-formatting.md) dostępne do użycia z również ciągi interpolowane funkcji.

## <a name="how-to-specify-a-format-string-for-an-interpolated-expression"></a>Jak określać ciągu formatu dla interpolowanego wyrażenia

Określ ciąg formatu, który jest obsługiwany przez typ wyniku wyrażenia wykonując interpolowanego wyrażenia dwukropka (":"), a ciąg formatu:

```
{<interpolatedExpression>:<formatString>}
```

Poniższy przykład przedstawia sposób określić format standardowe i niestandardowe ciągi dla wyrażeń, które powodują powstanie daty i godziny lub wyników liczbowych:

[!code-csharp-interactive[format string example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#2)]

Aby uzyskać więcej informacji, zobacz [składnika ciąg formatu](../../standard/base-types/composite-formatting.md#format-string-component) sekcji [złożone formatowanie](../../standard/base-types/composite-formatting.md) tematu. Tej sekcji zamieszczono linki do tematów opisujących ciągi formatujące standardowe i niestandardowe obsługiwane przez typy podstawowe .NET.

## <a name="how-to-control-the-field-width-and-alignment-of-the-formatted-interpolated-expression"></a>Sterowanie pola szerokości i wyrównania sformatowany interpolowanego wyrażenia

Określ szerokość pola minimalna i wyrównanie do wyniku wyrażenia sformatowany wykonując interpolowanego wyrażenia za pomocą przecinka (",") i wyrażenie stałe:

```
{<interpolatedExpression>,<alignment>}
```

Jeśli *wyrównanie* wartość jest dodatnia, wyniku wyrażenia sformatowany jest wyrównany do prawej; Jeśli ujemną, jest wyrównany.

Jeśli trzeba określić wyrównanie i ciąg formatu, uruchom za pomocą składnika wyrównania:

```
{<interpolatedExpression>,<alignment>:<formatString>}
```

Poniższy przykład przedstawia sposób Określanie wyrównania i używa potoku znaków ("|") do rozdzielenia pól tekstowych:

[!code-csharp-interactive[alignment example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#3)]

Jako przykład przedstawiono dane wyjściowe, jeśli długość wyniku wyrażenia sformatowany przekracza określony szerokość pola *wyrównanie* wartość jest ignorowana.

Aby uzyskać więcej informacji, zobacz [składnika wyrównanie](../../standard/base-types/composite-formatting.md#alignment-component) sekcji [złożone formatowanie](../../standard/base-types/composite-formatting.md) tematu.

## <a name="how-to-use-escape-sequences-in-an-interpolated-string"></a>Jak używać sekwencji unikowych w ciągu interpolowanym

Ciągi interpolowane obsługuje wszystkie sekwencje specjalne, które mogą być używane w literałach ciągu zwykłego. Aby uzyskać więcej informacji, zobacz [sekwencji unikowych ciąg](../programming-guide/strings/index.md#string-escape-sequences).

Aby zinterpretować sekwencji unikowych jako literału, należy użyć [dosłownego wyrażenia](../language-reference/tokens/verbatim.md) literału ciągu. Rozpoczyna się od ciągu dosłownego wyrażenia interpolowane `$` następuje znak `@` znaków.

Uwzględnienie nawias klamrowy "{" lub "}", w wyniku ciągu, użyj dwa nawiasy klamrowe, "{{" lub "}}". Aby uzyskać więcej informacji, zobacz [anulowanie nawiasów klamrowych](../../standard/base-types/composite-formatting.md#escaping-braces) sekcji [złożone formatowanie](../../standard/base-types/composite-formatting.md) tematu.

Poniższy przykład pokazuje, jak dołączyć nawiasy klamrowe w ciągu wynik i utworzyć dosłownego wyrażenia ciągu interpolowanym:

[!code-csharp-interactive[escape sequence example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#4)]

## <a name="how-to-use-a-ternary-conditional-operator--in-an-interpolated-expression"></a>Jak używać trójargumentowy operator warunkowy `?:` w wyrażeniu interpolowane

Jako dwukropkiem (":") ma specjalne znaczenie w elemencie z interpolowanego wyrażenia, aby można było używać [operator warunkowy](../language-reference/operators/conditional-operator.md) w wyrażeniu, należy ująć go w nawiasy, jak przedstawiono na poniższym przykładzie:

[!code-csharp-interactive[conditional operator example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#5)]

## <a name="how-to-create-a-culture-specific-result-string-with-string-interpolation"></a>Jak utworzyć ciąg specyficzne dla kultury wynik z interpolacji ciągu

Domyślnie ciągu interpolowanym używa bieżącej kultury, zdefiniowane przez <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType> właściwości dla wszystkich operacji formatowania. Użyj niejawna konwersja ciągu interpolowanym do <xref:System.FormattableString?displayProperty=nameWithType> wystąpienia i wywołanie jego <xref:System.FormattableString.ToString(System.IFormatProvider)> metodę, aby utworzyć parametry specyficzne dla kultury wynik. Poniższy przykład pokazuje, jak to zrobić:

[!code-csharp-interactive[specify different cultures](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#6)]

Jak pokazano na przykładzie, można użyć jednego <xref:System.FormattableString> wystąpienie do generowania wielu ciągów wynik dla różnych kultur.

## <a name="how-to-create-a-result-string-using-the-invariant-culture"></a>Jak utworzyć ciąg wynik użyta Niezmienna kultura

Wraz z programem <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> metody, można użyć statycznych <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> metody rozpoznać ciągu interpolowanym jako ciąg wynik <xref:System.Globalization.CultureInfo.InvariantCulture>. Poniższy przykład pokazuje, jak to zrobić:

[!code-csharp-interactive[format with invariant culture](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#7)]

## <a name="conclusion"></a>Wniosek

W tym samouczku opisano typowe scenariusze użycia interpolacji ciągu. Aby uzyskać więcej informacji na temat interpolacji ciągu, zobacz [ciągu interpolacji](../language-reference/tokens/interpolated.md) tematu. Aby uzyskać więcej informacji na temat typy formatowania w .NET, zobacz [typy formatowania w .NET](../../standard/base-types/formatting-types.md) i [złożone formatowanie](../../standard/base-types/composite-formatting.md) tematów.

## <a name="see-also"></a>Zobacz także

<xref:System.String.Format%2A?displayProperty=nameWithType>  
<xref:System.FormattableString?displayProperty=nameWithType>  
<xref:System.IFormattable?displayProperty=nameWithType>  
[Ciągi](../programming-guide/strings/index.md)  
