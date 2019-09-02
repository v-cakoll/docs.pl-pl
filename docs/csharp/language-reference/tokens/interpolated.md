---
title: Interpolacja $-String- C# odwołanie
ms.custom: seodec18
description: Interpolacja ciągów zapewnia bardziej czytelną i wygodną składnię formatu ciągu wyjściowego niż tradycyjne formatowanie złożone ciągu.
ms.date: 04/29/2019
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
ms.openlocfilehash: 1f0d63a549daa9fecd0cce3a7e5a6496929c37d2
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202961"
---
# <a name="---string-interpolation-c-reference"></a>Interpolacja $-String (C# odwołanie)

Znak specjalny identyfikuje literał ciągu jako *ciąg interpolowany.* `$` Ciąg interpolowany jest literałem ciągu, która może zawierać *wyrażenia interpolacji*. Gdy ciąg interpolowany jest rozpoznawany jako ciąg wynikowy, elementy z wyrażeniami interpolacji są zastępowane ciągami reprezentującymi wyniki wyrażenia. Ta funkcja jest dostępna w C# 6 i nowszych wersjach języka.

Interpolacja ciągów zapewnia bardziej czytelną i wygodną składnię do tworzenia ciągów sformatowanych niż funkcja [formatowania złożonego w postaci ciągu](../../../standard/base-types/composite-formatting.md) . Poniższy przykład używa obu funkcji do wygenerowania tych samych danych wyjściowych:

[!code-csharp-interactive[compare with composite formatting](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#1)]

## <a name="structure-of-an-interpolated-string"></a>Struktura ciągu interpolowanego

Aby zidentyfikować literał ciągu jako ciąg interpolowany, poprzedź go `$` symbolem. `$` Między`"` i, które zaczyna się literałem ciągu znaków, nie może zawierać żadnego odstępu. Powoduje to błąd czasu kompilacji.

Struktura elementu z wyrażeniem interpolacji jest następująca:

```csharp
{<interpolationExpression>[,<alignment>][:<formatString>]}
```

Elementy w nawiasach kwadratowych są opcjonalne. W poniższej tabeli opisano każdy element:

|Element|Opis|
|-------------|-----------------|
|`interpolationExpression`|Wyrażenie, które generuje wynik do sformatowania. Ciąg reprezentujący `null` wynik to <xref:System.String.Empty?displayProperty=nameWithType>.|
|`alignment`|Wyrażenie stałe, którego wartość definiuje minimalną liczbę znaków w ciągu reprezentującym wynik wyrażenia interpolacji. W przypadku wartości pozytywnej Reprezentacja ciągu jest wyrównana do prawej; Jeśli wartość jest ujemna, jest wyrównana do lewej. Aby uzyskać więcej informacji, zobacz [składnik wyrównania](../../../standard/base-types/composite-formatting.md#alignment-component).|
|`formatString`|Ciąg formatu, który jest obsługiwany przez typ wyniku wyrażenia. Aby uzyskać więcej informacji, zobacz [Formatowanie składnika ciągu](../../../standard/base-types/composite-formatting.md#format-string-component).|

W poniższym przykładzie zastosowano opcjonalne składniki formatowania opisane powyżej:

[!code-csharp-interactive[specify alignment and format string](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#2)]

## <a name="special-characters"></a>Znaki specjalne

Aby dołączyć nawias klamrowy "{" lub "}" w tekście wytworzonym przez ciąg interpolowany, użyj dwóch nawiasów klamrowych "{{" lub "}}". Aby uzyskać więcej informacji, [](../../../standard/base-types/composite-formatting.md#escaping-braces)Zobacz nawiasy klamrowe.

Ponieważ dwukropek (":") ma specjalne znaczenie w elemencie wyrażenia interpolacji, aby użyć [operatora warunkowego](../operators/conditional-operator.md) w wyrażeniu interpolacji, należy ująć to wyrażenie w nawiasy.

Poniższy przykład pokazuje, jak uwzględnić nawias klamrowy w ciągu wynikowym oraz jak używać operatora warunkowego w wyrażeniu interpolacji:

[!code-csharp-interactive[example with ternary conditional operator](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#3)]

Ciąg interpolowany Verbatim rozpoczyna się od znaku `$` , po którym następuje `@` znak. Aby uzyskać więcej informacji na temat ciągów Verbatim, zobacz temat [identyfikatory](verbatim.md) [ciągów](../keywords/string.md) i Verbatim.

> [!NOTE]
> Token musi występować `@` przed tokenem w ciągu interpolowanym Verbatim. `$`

## <a name="implicit-conversions-and-specifying-iformatprovider-implementation"></a>Konwersje niejawne `IFormatProvider` i określanie implementacji

Istnieją trzy niejawne konwersje z ciągu interpolowanego:

1. Konwersja ciągu interpolowanego na <xref:System.String> wystąpienie, które jest wynikiem interpolowanej rozdzielczości ciągu z elementami wyrażenia interpolacji, które są zastępowane poprawnie sformatowanymi reprezentacjami ciągu wyników. Ta konwersja używa bieżącej kultury.

1. Konwersja ciągu interpolowanego na <xref:System.FormattableString> wystąpienie, które reprezentuje ciąg formatu złożonego wraz z wynikami wyrażenia do sformatowania. Pozwala to na tworzenie wielu ciągów wynikowych z zawartością specyficzną dla kultury z jednego <xref:System.FormattableString> wystąpienia. Aby to wywołać, należy wykonać jedną z następujących metod:

      - Przeciążenie generujące ciąg wynikowy <xref:System.Globalization.CultureInfo.CurrentCulture>dla. <xref:System.FormattableString.ToString>
      - Metoda, która generuje ciąg wynikowy <xref:System.Globalization.CultureInfo.InvariantCulture>dla. <xref:System.FormattableString.Invariant%2A>
      - <xref:System.FormattableString.ToString(System.IFormatProvider)> Metoda, która tworzy ciąg wynikowy dla określonej kultury.

    Można również użyć <xref:System.FormattableString.ToString(System.IFormatProvider)> metody, aby zapewnić zdefiniowaną przez użytkownika implementację <xref:System.IFormatProvider> interfejsu, która obsługuje niestandardowe formatowanie. Aby uzyskać więcej informacji, zobacz [niestandardowe formatowanie za pomocą ICustomFormatter](../../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter).

1. Konwersja ciągu interpolowanego na <xref:System.IFormattable> wystąpienie, które również umożliwia tworzenie wielu ciągów wynikowych przy użyciu zawartości specyficznej dla kultury z jednego <xref:System.IFormattable> wystąpienia.

W poniższym przykładzie zastosowano niejawną konwersję do <xref:System.FormattableString> , aby utworzyć charakterystyczne dla kultury ciągi wynikowe:

[!code-csharp-interactive[create culture-specific result strings](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#4)]

## <a name="additional-resources"></a>Dodatkowe zasoby

Jeśli dopiero zaczynasz interpolację ciągów, zobacz Interpolacja [ciągów w C# ](../../tutorials/exploration/interpolated-strings.yml) samouczku interaktywnym. Możesz również sprawdzić inne [interpolacje ciągów w C# ](../../tutorials/string-interpolation.md) samouczku, w którym pokazano, jak używać interpolowanych ciągów do tworzenia sformatowanych ciągów.

## <a name="compilation-of-interpolated-strings"></a>Kompilacja ciągów interpolowanych

Jeśli ciąg interpolowany ma typ `string`, zazwyczaj jest przekształcany <xref:System.String.Format%2A?displayProperty=nameWithType> do wywołania metody. Kompilator może zastępować <xref:System.String.Format%2A?displayProperty=nameWithType> w <xref:System.String.Concat%2A?displayProperty=nameWithType> przypadku, gdy przeanalizowane zachowanie byłoby równoważne konkatenacji.

Jeśli ciąg interpolowany ma typ <xref:System.IFormattable> lub <xref:System.FormattableString>, kompilator <xref:System.Runtime.CompilerServices.FormattableStringFactory.Create%2A?displayProperty=nameWithType> generuje wywołanie metody.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [interpolowane ciągi](~/_csharplang/spec/expressions.md#interpolated-strings) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Zobacz także

- <xref:System.String.Format%2A?displayProperty=nameWithType>
- <xref:System.FormattableString?displayProperty=nameWithType>
- <xref:System.IFormattable?displayProperty=nameWithType>
- [Formatowanie złożone](../../../standard/base-types/composite-formatting.md)
- [Formatowanie tabeli wyników liczbowych](../keywords/formatting-numeric-results-table.md)
- [Ciągi](../../programming-guide/strings/index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Znaki specjalne języka C#](index.md)
- [Dokumentacja języka C#](../index.md)
