---
title: Interpolacja $-String- C# odwołanie
description: Interpolacja ciągów zapewnia bardziej czytelną i wygodną składnię formatu ciągu wyjściowego niż tradycyjne formatowanie złożone ciągu.
ms.date: 09/02/2019
f1_keywords:
- $_CSharpKeyword
- $
helpviewer_keywords:
- $ special character [C#]
- string interpolation [C#]
- interpolated string [C#]
author: pkulikov
ms.openlocfilehash: b32bbbb0bd99878822d7ca5abdba80b46539846a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715084"
---
# <a name="---string-interpolation-c-reference"></a>Interpolacja $-String (C# odwołanie)

`$` znak specjalny identyfikuje literał ciągu jako *ciąg interpolowany*. Ciąg interpolowany jest literałem ciągu, która może zawierać *wyrażenia interpolacji*. Gdy ciąg interpolowany jest rozpoznawany jako ciąg wynikowy, elementy z wyrażeniami interpolacji są zastępowane ciągami reprezentującymi wyniki wyrażenia. Ta funkcja jest dostępna od C# 6.

Interpolacja ciągów zapewnia bardziej czytelną i wygodną składnię do tworzenia ciągów sformatowanych niż funkcja [formatowania złożonego w postaci ciągu](../../../standard/base-types/composite-formatting.md) . Poniższy przykład używa obu funkcji do wygenerowania tych samych danych wyjściowych:

[!code-csharp-interactive[compare with composite formatting](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#1)]

## <a name="structure-of-an-interpolated-string"></a>Struktura ciągu interpolowanego

Aby zidentyfikować literał ciągu jako ciąg interpolowany, poprzedź go symbolem `$`. Między `$` i `"`, które zaczynają literał ciągu znaków, nie może być odstępy.

Struktura elementu z wyrażeniem interpolacji jest następująca:

```csharp
{<interpolationExpression>[,<alignment>][:<formatString>]}
```

Elementy w nawiasach kwadratowych są opcjonalne. W poniższej tabeli opisano każdy element:

|Element|Opis|
|-------------|-----------------|
|`interpolationExpression`|Wyrażenie, które generuje wynik do sformatowania. Reprezentacja ciągu `null` jest <xref:System.String.Empty?displayProperty=nameWithType>.|
|`alignment`|Wyrażenie stałe, którego wartość definiuje minimalną liczbę znaków w ciągu reprezentującym wynik wyrażenia. W przypadku wartości pozytywnej Reprezentacja ciągu jest wyrównana do prawej; Jeśli wartość jest ujemna, jest wyrównana do lewej. Aby uzyskać więcej informacji, zobacz [składnik wyrównania](../../../standard/base-types/composite-formatting.md#alignment-component).|
|`formatString`|Ciąg formatu, który jest obsługiwany przez typ wyniku wyrażenia. Aby uzyskać więcej informacji, zobacz [Formatowanie składnika ciągu](../../../standard/base-types/composite-formatting.md#format-string-component).|

W poniższym przykładzie zastosowano opcjonalne składniki formatowania opisane powyżej:

[!code-csharp-interactive[specify alignment and format string](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#2)]

## <a name="special-characters"></a>Znaki specjalne

Aby dołączyć nawias klamrowy "{" lub "}" w tekście wytworzonym przez ciąg interpolowany, użyj dwóch nawiasów klamrowych "{{" lub "}}". Aby uzyskać więcej informacji, zobacz [nawiasy klamrowe](../../../standard/base-types/composite-formatting.md#escaping-braces).

Ponieważ dwukropek (":") ma specjalne znaczenie w elemencie wyrażenia interpolacji, aby użyć [operatora warunkowego](../operators/conditional-operator.md) w wyrażeniu interpolacji, należy ująć to wyrażenie w nawiasy.

Poniższy przykład pokazuje, jak uwzględnić nawias klamrowy w ciągu wynikowym oraz jak używać operatora warunkowego w wyrażeniu interpolacji:

[!code-csharp-interactive[example with ternary conditional operator](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#3)]

Interpolacja Verbatim ciąg rozpoczyna się od znaku `$`, po którym następuje znak `@`. Aby uzyskać więcej informacji na temat ciągów Verbatim, zobacz temat [identyfikatory](verbatim.md) [ciągów](../builtin-types/reference-types.md) i Verbatim.

> [!NOTE]
> Począwszy od C# 8,0, można użyć tokenów `$` i `@` w dowolnej kolejności: zarówno `$@"..."`, jak i `@$"..."` są prawidłowymi interpolowanymi ciągami Verbatim. We wcześniejszych C# wersjach token `$` musi znajdować się przed tokenem `@`.

## <a name="implicit-conversions-and-how-to-specify-iformatprovider-implementation"></a>Niejawne konwersje i sposób określania implementacji `IFormatProvider`

Istnieją trzy niejawne konwersje z ciągu interpolowanego:

1. Konwersja ciągu interpolowanego na wystąpienie <xref:System.String>, które jest wynikiem interpolowanej rozdzielczości ciągu z elementami wyrażenia interpolacji, które są zastępowane poprawnie sformatowanymi reprezentacjami ciągu wyników. Ta konwersja używa <xref:System.Globalization.CultureInfo.CurrentCulture> do formatowania wyników wyrażenia.

1. Konwersja ciągu interpolowanego na wystąpienie <xref:System.FormattableString>, które reprezentuje ciąg formatu złożonego wraz z wynikami wyrażenia do sformatowania. Pozwala to na tworzenie wielu ciągów wynikowych z zawartością specyficzną dla kultury z jednego wystąpienia <xref:System.FormattableString>. W tym celu należy wywołać jedną z następujących metod:

      - Przeciążenie <xref:System.FormattableString.ToString>, które tworzy ciąg wynikowy dla <xref:System.Globalization.CultureInfo.CurrentCulture>.
      - Metoda <xref:System.FormattableString.Invariant%2A>, która generuje ciąg wynikowy dla <xref:System.Globalization.CultureInfo.InvariantCulture>.
      - Metoda <xref:System.FormattableString.ToString(System.IFormatProvider)>, która generuje ciąg wynikowy dla określonej kultury.

    Można również użyć metody <xref:System.FormattableString.ToString(System.IFormatProvider)>, aby zapewnić zdefiniowaną przez użytkownika implementację interfejsu <xref:System.IFormatProvider>, która obsługuje niestandardowe formatowanie. Aby uzyskać więcej informacji, zobacz sekcję [formatowanie niestandardowe przy użyciu ICustomFormatter](../../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter) [typów formatowania w artykule .NET](../../../standard/base-types/formatting-types.md) .

1. Konwersja ciągu interpolowanego na wystąpienie <xref:System.IFormattable>, które również umożliwia tworzenie wielu ciągów wynikowych z zawartością specyficzną dla kultury z jednego wystąpienia <xref:System.IFormattable>.

W poniższym przykładzie zastosowano niejawną konwersję w celu <xref:System.FormattableString> tworzenia ciągów wynikowych specyficznych dla kultury:

[!code-csharp-interactive[create culture-specific result strings](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#4)]

## <a name="additional-resources"></a>Dodatkowe zasoby

Jeśli dopiero zaczynasz interpolację ciągów, zobacz [Interpolacja ciągów w C# ](../../tutorials/exploration/interpolated-strings.yml) samouczku interaktywnym. Możesz również sprawdzić inne [interpolacje ciągów w C# ](../../tutorials/string-interpolation.md) samouczku, w którym pokazano, jak używać interpolowanych ciągów do tworzenia sformatowanych ciągów.

## <a name="compilation-of-interpolated-strings"></a>Kompilacja ciągów interpolowanych

Jeśli ciąg interpolowany ma typ `string`, zazwyczaj jest przekształcany do wywołania metody <xref:System.String.Format%2A?displayProperty=nameWithType>. Kompilator może zastąpić <xref:System.String.Format%2A?displayProperty=nameWithType> z <xref:System.String.Concat%2A?displayProperty=nameWithType>, jeśli przeanalizowane zachowanie byłoby równoważne z konkatenacją.

Jeśli ciąg interpolowany ma typ <xref:System.IFormattable> lub <xref:System.FormattableString>, kompilator generuje wywołanie metody <xref:System.Runtime.CompilerServices.FormattableStringFactory.Create%2A?displayProperty=nameWithType>.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [interpolowane ciągi](~/_csharplang/spec/expressions.md#interpolated-strings) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Zobacz także

- [C#odwoła](../index.md)
- [Znaki specjalne języka C#](index.md)
- [Ciągi](../../programming-guide/strings/index.md)
- [Formatowanie tabeli wyników liczbowych](../keywords/formatting-numeric-results-table.md)
- [Formatowanie złożone](../../../standard/base-types/composite-formatting.md)
- <xref:System.String.Format%2A?displayProperty=nameWithType>
