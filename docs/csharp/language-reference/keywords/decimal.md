---
title: decimal — słowo kluczowe - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- decimal_CSharpKeyword
- decimal
helpviewer_keywords:
- decimal keyword [C#]
ms.assetid: b6522132-b5ee-4be3-ad13-3adfdb7de7a1
ms.openlocfilehash: f26d812d8f4da8fae73ebbaee15441cd88860d04
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239462"
---
# <a name="decimal-c-reference"></a>decimal (odwołanie w C#)

`decimal` — Słowo kluczowe wskazuje typ danych 128-bitowych. W porównaniu do innych typów zmiennoprzecinkowych `decimal` typ ma większą dokładność i mniejszy zakres, który sprawia, że odpowiedni do obliczeń finansowych i walutowych. Przybliżony zakres i dokładność `decimal` typu są wyświetlane w poniższej tabeli.

|Typ|Przybliżony zakres|Dokładność|Typ architektury .NET|
|----------|-----------------------|---------------|-------------------------|
|`decimal`|±1.0 x 10<sup>-28</sup> do ±7.9228 x 10<sup>28</sup>|28–29 cyfr znaczących|<xref:System.Decimal?displayProperty=nameWithType>|

Wartość domyślna `decimal` wynosi 0, m.

## <a name="literals"></a>Literały

Jeśli chcesz, aby rzeczywistych literał liczbowy powinien być traktowany jako `decimal`, należy użyć sufiksu m lub M, na przykład:

```csharp
decimal myMoney = 300.5m;
```

Bez sufiksu m liczba jest traktowana [double](../../../csharp/language-reference/keywords/double.md) i generuje błąd kompilatora.

## <a name="conversions"></a>Konwersje

Typy całkowite są niejawnie konwertowane na `decimal` i wynik daje w wyniku `decimal`. Dlatego można zainicjować zmienną typu decimal, używając literału typu integer, bez konieczności użycia sufiksu, tak jak pokazano poniżej:

```csharp
decimal myMoney = 300;
```

Istnieje niejawna konwersja między innymi typami zmiennoprzecinkowymi a `decimal` typu; w związku z tym, należy użyć rzutowania, aby przekonwertować między tymi dwoma typami. Na przykład:

```csharp
decimal myMoney = 99.9m;
double x = (double)myMoney;
myMoney = (decimal)x;
```

Można także łączyć `decimal` całkowite typy liczbowe w jednym wyrażeniu. Jednak jednoczesne użycie typu `decimal` i innych typów zmiennoprzecinkowych bez rzutowania spowoduje błąd kompilacji.

Aby uzyskać więcej informacji dotyczących niejawnych konwersji liczbowych, zobacz [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).

Aby uzyskać więcej informacji dotyczących jawnych konwersji liczbowych, zobacz [Explicit Numeric Conversions Table](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md).

## <a name="formatting-decimal-output"></a>Formatowanie danych wyjściowych typu decimal

Wyniki można formatować, przy użyciu `String.Format` metodę, lub za pomocą <xref:System.Console.Write%2A?displayProperty=nameWithType> metody, która wywołuje `String.Format()`. Format waluty jest określany przy użyciu standardowego ciągu formatu walutowego (C lub c), tak jak pokazano w drugim przykładzie w dalszej części tego artykułu. Aby uzyskać więcej informacji na temat `String.Format` metody, zobacz <xref:System.String.Format%2A?displayProperty=nameWithType>.

## <a name="example"></a>Przykład

Poniższy przykład powoduje błąd kompilatora spowodowany próbą dodania [double](../../../csharp/language-reference/keywords/double.md) i `decimal` zmiennych.

```csharp
decimal dec = 0m;
double dub = 9;
// The following line causes an error that reads "Operator '+' cannot be applied to
// operands of type 'double' and 'decimal'"
Console.WriteLine(dec + dub);

// You can fix the error by using explicit casting of either operand.
Console.WriteLine(dec + (decimal)dub);
Console.WriteLine((double)dec + dub);
```

Wynikiem jest następujący błąd:

`Operator '+' cannot be applied to operands of type 'double' and 'decimal'`

W tym przykładzie `decimal` i [int](../../../csharp/language-reference/keywords/int.md) są używane razem w jednym wyrażeniu. Wynik daje w wyniku `decimal` typu.

[!code-csharp[csrefKeywordsTypes#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#6)]

## <a name="example"></a>Przykład

W tym przykładzie dane wyjściowe są formatowane przy użyciu ciągu formatu walutowego. Należy zauważyć, że `x` jest zaokrąglana, ponieważ liczba miejsc dziesiętnych przekracza wartość 0,99. Zmienna `y`, która przedstawia maksymalną dokładną liczbę cyfr, jest wyświetlana dokładnie w poprawnym formacie.

[!code-csharp[csrefKeywordsTypes#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#7)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- <xref:System.Decimal>  
- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
- [Tabela typów całkowitych](../../../csharp/language-reference/keywords/integral-types-table.md)  
- [Tabela typów wbudowanych](../../../csharp/language-reference/keywords/built-in-types-table.md)  
- [Tabela niejawnych konwersji liczbowych](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
- [Tabela jawnych konwersji liczbowych](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  
- [Standardowe ciągi formatujące liczby](../../../standard/base-types/standard-numeric-format-strings.md)