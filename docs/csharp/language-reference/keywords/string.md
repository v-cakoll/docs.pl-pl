---
title: string (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- string
- string_CSharpKeyword
helpviewer_keywords:
- strings [C#], reference
- '@ string literal'
- string literals [C#]
- string keyword [C#]
ms.assetid: 3037e558-fb22-494d-bca1-a15ade11b11a
ms.openlocfilehash: 66b1729363878f69f868b8b8fd6e9e7011426f27
ms.sourcegitcommit: 7f7664837d35320a0bad3f7e4ecd68d6624633b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/30/2018
ms.locfileid: "52672007"
---
# <a name="string-c-reference"></a>string (odwołanie w C#)

`string` Typu reprezentuje sekwencję zero lub więcej znaków Unicode. `string` jest aliasem dla <xref:System.String> na platformie .NET.

Mimo że `string` jest typem referencyjnym, operatory równości (`==` i `!=`) są zdefiniowane w celu porównania wartości `string` obiektów, nie odwołuje się. To sprawia, że testowanie dla równości ciągu bardziej intuicyjne. Na przykład:

```csharp
string a = "hello";
string b = "h";
// Append to contents of 'b'
b += "ello";
Console.WriteLine(a == b);
Console.WriteLine((object)a == (object)b);
```

Spowoduje to wyświetlenie "True" i następnie "False", ponieważ zawartość ciągi są równoważne, ale `a` i `b` odwołuje się do tego samego wystąpienia ciągu.

+ — Operator łączy ciągi:

```csharp
string a = "good " + "morning";
```

Spowoduje to utworzenie obiekt ciągu zawierający "good morning".

Ciągi są *niezmienne*— nie można zmienić zawartość obiekt ciągu, po utworzeniu obiektu, mimo że składnia sprawia, że wyświetlane tak, jakby można to zrobić. Na przykład kiedy piszesz kod, kompilator tworzy obiekt ciągu do przechowywania nowej sekwencji znaków, a nowy obiekt jest przypisany do b. Ciąg "h" jest uprawniona do wyrzucania elementów bezużytecznych.

```csharp
string b = "h";
b += "ello";
```

[] — Operator może służyć do dostępu tylko do odczytu do pojedynczych znaków z `string`:

```csharp
string str = "test";
char x = str[2];  // x = 's';
```

Literały ciągów są typu `string` i mogą być zapisywane w dwóch formach, w cudzysłowach i @-quoted. Jako ciąg, który literały są ujęte w podwójny cudzysłów ("):

```csharp
"good morning"  // a string literal
```

Literały ciągu może zawierać dowolny znak literału. Sekwencje unikowe są uwzględniane. W poniższym przykładzie użyto sekwencja unikowa `\\` dla ukośnikiem, po którym `\u0066` literę f, i `\n` dla nowego wiersza.

```csharp
string a = "\\\u0066\n";
Console.WriteLine(a);
```

> [!NOTE]
> Kod escape `\udddd` (gdzie `dddd` jest liczbę czterocyfrową) reprezentuje znak Unicode U +`dddd`. Kodów wyjścia Unicode ośmiu cyfr, również są rozpoznawane: `\Udddddddd`.

Ciąg Verbatim literały rozpoczynać `@` i również są ujęte w podwójny cudzysłów. Na przykład:

```csharp
@"good morning"  // a string literal
```

Zaletą ciągi verbatim jest, że sekwencje ucieczki to *nie* przetwarzany, która ułatwia zapisu, na przykład w pełni kwalifikowaną nazwą pliku:

```csharp
@"c:\Docs\Source\a.txt"  // rather than "c:\\Docs\\Source\\a.txt"
```

Aby uwzględnić znak podwójnego cudzysłowu w @-quoted ciąg, podwój go:

```csharp
@"""Ahoy!"" cried the captain." // "Ahoy!" cried the captain.
```

Inne zastosowania `@` znaki specjalne, zobacz [@ — identyfikator dosłownego wyrażenia](../tokens/verbatim.md).

Aby uzyskać więcej informacji na temat ciągów w języku C#, zobacz [ciągi](../../programming-guide/strings/index.md).

## <a name="example"></a>Przykład

[!code-csharp[csrefKeywordsTypes#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#17)]  

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Najlepsze rozwiązania dotyczące używania ciągów](../../../standard/base-types/best-practices-strings.md)
- [Słowa kluczowe języka C#](index.md)
- [Typy odwołań](reference-types.md)
- [Typy wartości](value-types.md)
- [Podstawowe operacje na ciągach](../../../standard/base-types/basic-string-operations.md)
- [Tworzenie nowych ciągów](../../../standard/base-types/creating-new.md)
- [Formatowanie tabeli wyników liczbowych](formatting-numeric-results-table.md)
