---
title: $ - interpolacja ciągów - odwołanie do języka C#
description: Interpolacja ciągów zapewnia bardziej czytelną i wygodną składnię do formatowania danych wyjściowych ciągu niż tradycyjne formatowanie złożone ciągów.
ms.date: 09/02/2019
f1_keywords:
- $_CSharpKeyword
- $
helpviewer_keywords:
- $ special character [C#]
- string interpolation [C#]
- interpolated string [C#]
author: pkulikov
ms.openlocfilehash: 97bc606569b83bd14cd3b32495deb8e529747e9c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76980122"
---
# <a name="---string-interpolation-c-reference"></a>$ - interpolacja ciągów (odwołanie do Języka C#)

Znak `$` specjalny identyfikuje literał ciągu jako *interpolowany ciąg*. Interpolowany ciąg jest literałem ciągu, który może zawierać *wyrażenia interpolacji*. Gdy interpolowany ciąg jest rozpoznawany do ciągu wynikowego, elementy z wyrażeniami interpolacji są zastępowane przez reprezentacje ciągu wyników wyrażenia. Ta funkcja jest dostępna od języka C# 6.

Interpolacja ciągów zapewnia bardziej czytelną i wygodną składnię do tworzenia sformatowanych ciągów niż funkcja [formatowania złożonego ciągu.](../../../standard/base-types/composite-formatting.md) W poniższym przykładzie użyto obu funkcji do uzyskania tego samego wyjścia:

[!code-csharp-interactive[compare with composite formatting](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#1)]

## <a name="structure-of-an-interpolated-string"></a>Struktura interpolowany ciąg

Aby zidentyfikować literał ciągu jako interpolowany ciąg, `$` należy go potoczyć symbolem. Nie można mieć żadnych `$` odstępów `"` między i, który rozpoczyna literał ciągu.

Struktura elementu z wyrażeniem interpolacji jest następująca:

```csharp
{<interpolationExpression>[,<alignment>][:<formatString>]}
```

Elementy w nawiasach kwadratowych są opcjonalne. W poniższej tabeli opisano każdy element:

|Element|Opis|
|-------------|-----------------|
|`interpolationExpression`|Wyrażenie, które daje wynik do sformatowania. Reprezentacja `null` ciągu <xref:System.String.Empty?displayProperty=nameWithType>jest .|
|`alignment`|Wyrażenie stałe, którego wartość definiuje minimalną liczbę znaków w reprezentacji ciągu wyniku wyrażenia. Jeśli dodatnie, reprezentacja ciągu jest wyrównany do prawej; jeśli jest ujemna, jest wyrównana do lewej. Aby uzyskać więcej informacji, zobacz [Komponent wyrównanie](../../../standard/base-types/composite-formatting.md#alignment-component).|
|`formatString`|Ciąg formatu, który jest obsługiwany przez typ wyniku wyrażenia. Aby uzyskać więcej informacji, zobacz [Formatowanie składnika ciągów](../../../standard/base-types/composite-formatting.md#format-string-component).|

W poniższym przykładzie użyto opcjonalnych składników formatowania opisanych powyżej:

[!code-csharp-interactive[specify alignment and format string](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#2)]

## <a name="special-characters"></a>Znaki specjalne

Aby dołączyć nawias klamrowy,{" lub "}", w tekście wyprodukowanym przez interpolowany ciąg, należy użyć dwóch nawiasów klamrowych: "{{" lub "}}". Aby uzyskać więcej informacji, zobacz [Ucieczka nawiasów klamrowych](../../../standard/base-types/composite-formatting.md#escaping-braces).

Jako dwukropek (":") ma szczególne znaczenie w elemencie wyrażenia interpolacji, aby użyć [operatora warunkowego](../operators/conditional-operator.md) w wyrażeniu interpolacji, ujmij to wyrażenie w nawiasach.

W poniższym przykładzie pokazano, jak uwzględnić nawias klamrowy w ciągu wyników i jak używać operatora warunkowego w wyrażeniu interpolacji:

[!code-csharp-interactive[example with ternary conditional operator](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#3)]

Interpolowany ciąg dosłowny zaczyna `$` się od `@` znaku, po którym następuje znak. Aby uzyskać więcej informacji na temat ciągów dosłownych, zobacz [ciąg i](../builtin-types/reference-types.md) dosłowne tematy [identyfikatora.](verbatim.md)

> [!NOTE]
> Począwszy od Języka C# 8.0, można użyć `$` i `$@"..."` `@$"..."` `@` tokeny w dowolnej kolejności: oba i są prawidłowe interpolowane ciągi dosłowne. We wcześniejszych wersjach `$` języka C# `@` token musi pojawić się przed tokenem.

## <a name="implicit-conversions-and-how-to-specify-iformatprovider-implementation"></a>Konwersje niejawne `IFormatProvider` i sposób określania implementacji

Istnieją trzy niejawne konwersje z interpolowany ciąg:

1. Konwersja interpolowanego ciągu na <xref:System.String> wystąpienie, które jest wynikiem interpolowanej rozdzielczości ciągu z elementami wyrażenia interpolacji zastępowanymi prawidłowo sformatowanymi reprezentacjami ciągów ich wyników. Ta konwersja <xref:System.Globalization.CultureInfo.CurrentCulture> używa do formatowania wyników wyrażeń.

1. Konwersja interpolowanego ciągu na <xref:System.FormattableString> wystąpienie reprezentujące ciąg formatu złożonego wraz z wynikami wyrażenia, które mają zostać sformatowane. Dzięki temu można utworzyć wiele ciągów wyników z <xref:System.FormattableString> zawartością specyficzne dla kultury z jednego wystąpienia. Aby to zrobić, należy wywołać jedną z następujących metod:

      - Przeciążenie, <xref:System.FormattableString.ToString> które tworzy ciąg <xref:System.Globalization.CultureInfo.CurrentCulture>wynikowy dla .
      - Metoda, <xref:System.FormattableString.Invariant%2A> która tworzy ciąg wynikowy dla <xref:System.Globalization.CultureInfo.InvariantCulture>.
      - Metoda, <xref:System.FormattableString.ToString(System.IFormatProvider)> która tworzy ciąg wynik dla określonej kultury.

    Można również użyć <xref:System.FormattableString.ToString(System.IFormatProvider)> tej metody, aby zapewnić implementację zdefiniowaną przez użytkownika <xref:System.IFormatProvider> interfejsu, który obsługuje formatowanie niestandardowe. Aby uzyskać więcej informacji, zobacz [niestandardowe formatowanie za pomocą iCustomFormatter](../../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter) w artykule Formatowanie w artykule [.NET.](../../../standard/base-types/formatting-types.md)

1. Konwersja interpolowany ciąg do <xref:System.IFormattable> wystąpienia, który pozwala również na tworzenie wielu ciągów <xref:System.IFormattable> wynik z zawartością specyficzne dla kultury z jednego wystąpienia.

W poniższym przykładzie <xref:System.FormattableString> użyto niejawnej konwersji do tworzenia ciągów wyników specyficznych dla kultury:

[!code-csharp-interactive[create culture-specific result strings](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#4)]

## <a name="additional-resources"></a>Zasoby dodatkowe

Jeśli jesteś nowym do interpolacji ciągów, zobacz [String interpolacji w języku interaktywnym Języka C#.](../../tutorials/exploration/interpolated-strings.yml) Można również sprawdzić inny [ciąg interpolacji w samouczku Języka C#,](../../tutorials/string-interpolation.md) który pokazuje, jak używać interpolowanych ciągów do tworzenia sformatowanych ciągów.

## <a name="compilation-of-interpolated-strings"></a>Kompilacja interpolowanych ciągów

Jeśli interpolowany ciąg ma `string`typ , zazwyczaj jest przekształcany <xref:System.String.Format%2A?displayProperty=nameWithType> w wywołanie metody. Kompilator <xref:System.String.Format%2A?displayProperty=nameWithType> może <xref:System.String.Concat%2A?displayProperty=nameWithType> zastąpić, jeśli analizowane zachowanie będzie równoważne konkatenacji.

Jeśli interpolowany ciąg ma <xref:System.IFormattable> typ <xref:System.FormattableString>lub , kompilator <xref:System.Runtime.CompilerServices.FormattableStringFactory.Create%2A?displayProperty=nameWithType> generuje wywołanie metody.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [Interpolowane ciągi](~/_csharplang/spec/expressions.md#interpolated-strings) sekcji [specyfikacji języka C#.](~/_csharplang/spec/introduction.md)

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Znaki specjalne języka C#](index.md)
- [Ciągi](../../programming-guide/strings/index.md)
- [Standardowe ciągi formatu numerycznego](../../../standard/base-types/standard-numeric-format-strings.md)
- [Formatowanie kompozytowe](../../../standard/base-types/composite-formatting.md)
- <xref:System.String.Format%2A?displayProperty=nameWithType>
