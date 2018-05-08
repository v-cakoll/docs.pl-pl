---
title: decimal (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- decimal_CSharpKeyword
- decimal
helpviewer_keywords:
- decimal keyword [C#]
ms.assetid: b6522132-b5ee-4be3-ad13-3adfdb7de7a1
ms.openlocfilehash: 590bd3c6347271f9c4e2c6fd6223db608e010b69
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="decimal-c-reference"></a>decimal (odwołanie w C#)
`decimal` — Słowo kluczowe wskazuje typ danych 128-bitowego. W porównaniu do innych typów zmiennoprzecinkowych `decimal` typ ma więcej precision i mniejszy zakres, dzięki czemu odpowiedni do obliczeń finansowych i finansowe. Zakresie i dokładność `decimal` typu przedstawiono w poniższej tabeli.  
  
|Typ|Przybliżony zakres|Dokładność|Typ programu .NET Framework|  
|----------|-----------------------|---------------|-------------------------|  
|`decimal`|(-7.9 x 10<sup>28</sup> 7,9 x 10<sup>28</sup>) / (10<sup>0</sup> 10<sup>28</sup>)|28–29 cyfr znaczących|<xref:System.Decimal?displayProperty=nameWithType>|  

Domyślna wartość `decimal` jest 0 m.
  
## <a name="literals"></a>Literały  
 Jeśli chcesz, aby rzeczywista literałem powinien być traktowany jako `decimal`, należy użyć sufiksu m lub M, na przykład:  
  
```csharp
decimal myMoney = 300.5m;  
```  
  
 Sufiksu m, numer jest traktowany jako [podwójne](../../../csharp/language-reference/keywords/double.md) i generuje błąd kompilatora.  
  
## <a name="conversions"></a>Konwersje  
 Typy całkowite są niejawnie konwertowane `decimal` i daje w wyniku wynik `decimal`. Dlatego można zainicjować zmienną typu decimal, używając literału typu integer, bez konieczności użycia sufiksu, tak jak pokazano poniżej:  
  
```csharp
decimal myMoney = 300;  
```  
  
 Nie jest niejawna konwersja między innych typów zmiennoprzecinkowych i `decimal` typu; w związku z tym rzutowanie musi być używany do konwersji między tymi dwoma rodzajami. Na przykład:  
  
```csharp
decimal myMoney = 99.9m;  
double x = (double)myMoney;  
myMoney = (decimal)x;  
```  
  
 Możesz łączyć `decimal` całkowite typy liczbowe w tym samym wyrażeniu. Jednak mieszanie `decimal` i innych typów zmiennoprzecinkowych bez rzutowanie powoduje błąd kompilacji.  
  
 Aby uzyskać więcej informacji na temat niejawne konwersje liczbowe, zobacz [niejawne numeryczne Tabela konwersji](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
 Aby uzyskać więcej informacji na temat jawnych konwersji liczbowych, zobacz [jawne numeryczne Tabela konwersji](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md).  
  
## <a name="formatting-decimal-output"></a>Formatowanie danych wyjściowych typu decimal  
 Wyniki można sformatować przy użyciu `String.Format` metody, lub za pomocą <xref:System.Console.Write%2A?displayProperty=nameWithType> metodę, która wywołuje `String.Format()`. Format waluty jest określany przy użyciu standardowego ciągu formatu walutowego (C lub c), tak jak pokazano w drugim przykładzie w dalszej części tego artykułu. Aby uzyskać więcej informacji na temat `String.Format` metody, zobacz <xref:System.String.Format%2A?displayProperty=nameWithType>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład powoduje błąd kompilatora przy próbie dodania [podwójne](../../../csharp/language-reference/keywords/double.md) i `decimal` zmiennych.  
  
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
  
 W tym przykładzie `decimal` i [int](../../../csharp/language-reference/keywords/int.md) mieszane w tym samym wyrażeniu. Wynik daje w wyniku `decimal` typu.  
  
 [!code-csharp[csrefKeywordsTypes#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/decimal_1.cs)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie dane wyjściowe są formatowane przy użyciu ciągu formatu walutowego. Zwróć uwagę, że `x` jest zaokrąglana ponieważ $0,99 przekracza miejsc dziesiętnych. Zmienna `y`, reprezentuje maksymalną cyfr dokładne, zostanie wyświetlony dokładnie w poprawnym formacie.  
  
 [!code-csharp[csrefKeywordsTypes#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/decimal_2.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Decimal>  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Tabela typów całkowitych](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [Tabela typów wbudowanych](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [Tabela niejawnych konwersji liczbowych](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [Tabela jawnych konwersji liczbowych](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  
 [Standardowe ciągi formatujące liczby](../../../standard/base-types/standard-numeric-format-strings.md)
