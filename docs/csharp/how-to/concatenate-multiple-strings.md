---
title: Jak połączyć wiele ciągów (C# przewodnik)
description: Istnieje wiele sposobów łączenia ciągów w C#. Zapoznaj się z opcjami i przyczynami związanymi z różnymi opcjami.
ms.date: 02/20/2018
helpviewer_keywords:
- joining strings [C#]
- concatenating strings [C#]
- strings [C#], concatenation
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
ms.openlocfilehash: 2e443030445d2817c8f53a044a261edd22eeb26e
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73973274"
---
# <a name="how-to-concatenate-multiple-strings-c-guide"></a>Jak połączyć wiele ciągów (C# przewodnik)

*Łączenie* jest procesem dołączania jednego ciągu do końca innego ciągu. Parametry są łączone za pomocą operatora `+`. W przypadku literałów ciągów i stałych ciągów łączenie odbywa się w czasie kompilacji; Brak łączenia w czasie wykonywania. W przypadku zmiennych ciągów łączenie odbywa się tylko w czasie wykonywania.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Poniższy przykład używa łączenia do dzielenia długiego literału ciągu na mniejsze ciągi w celu zwiększenia czytelności w kodzie źródłowym. Te części są łączone w jeden ciąg w czasie kompilacji. Nie ma kosztu wydajności w czasie wykonywania niezależnie od liczby używanych ciągów.  
  
 [!code-csharp-interactive[Combining strings at compile time](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#1)]  

Aby połączyć zmienne ciągów, można użyć operatorów `+` lub `+=`, [interpolacji ciągów](../language-reference/tokens/interpolated.md) lub <xref:System.String.Format%2A?displayProperty=nameWithType>, <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Join%2A?displayProperty=nameWithType> lub metod <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType>. Operator `+` jest łatwy w użyciu i umożliwia korzystanie z intuicyjnego kodu. Nawet jeśli używasz kilku operatorów `+` w jednej instrukcji, zawartość ciągu jest kopiowana tylko raz. Poniższy kod przedstawia przykłady użycia operatorów `+` i `+=` do łączenia ciągów:

[!code-csharp-interactive[combining strings using +](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#2)]  

W niektórych wyrażeniach łatwiej jest łączyć ciągi przy użyciu interpolacji ciągów, jak pokazano w poniższym kodzie:
  
[!code-csharp-interactive[building strings using string interpolation](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#3)]  
  
> [!NOTE]
> W operacjach łączenia ciągów C# kompilator traktuje ciąg o wartości null tak samo jak pusty ciąg.

Inna metoda łączenia ciągów jest <xref:System.String.Format%2A?displayProperty=nameWithType>. Ta metoda dobrze sprawdza się w przypadku kompilowania ciągu z niewielkiej liczby ciągów komponentów.

W innych przypadkach można łączyć ciągi w pętli, gdzie nie wiadomo, ile łączonych parametrów źródłowych, a rzeczywista liczba ciągów źródłowych może być dość duża. Klasa <xref:System.Text.StringBuilder> została zaprojektowana dla tych scenariuszy. Poniższy kod używa metody <xref:System.Text.StringBuilder.Append%2A> klasy <xref:System.Text.StringBuilder> do łączenia ciągów.  
  
[!code-csharp-interactive[string concatenation using string builder](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#4)]  

Więcej informacji na temat [przyczyn wyboru łączenia ciągów lub klasy `StringBuilder`](xref:System.Text.StringBuilder#StringAndSB)

Kolejną opcją dołączenia ciągów do kolekcji jest użycie metody <xref:System.String.Concat%2A?displayProperty=nameWithType>. Użyj metody <xref:System.String.Join%2A?displayProperty=nameWithType>, jeśli ciągi źródłowe powinny być oddzielone ogranicznik. Poniższy kod łączy tablicę wyrazów przy użyciu obu metod:

[!code-csharp-interactive[concatenation of string collection](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#5)]

Na koniec można użyć [LINQ](../programming-guide/concepts/linq/index.md) i metody <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType>, aby dołączyć ciągi z kolekcji. Ta metoda łączy parametry źródłowe za pomocą wyrażenia lambda. Wyrażenie lambda wykonuje pracy, aby dodać każdy ciąg do istniejącego akumulacji. Poniższy przykład łączy tablicę wyrazów przez dodanie odstępu między każdym słowem w tablicy:

[!code-csharp-interactive[string concatenation using LINQ expressions](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#6)]  

Możesz wypróbować te przykłady, przeglądając kod w naszym [repozytorium GitHub](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings). Możesz też pobrać przykłady [jako plik zip](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).

## <a name="see-also"></a>Zobacz także

- <xref:System.String>
- <xref:System.Text.StringBuilder>
- [Przewodnik programowania w języku C#](../programming-guide/index.md)
- [Ciągi](../programming-guide/strings/index.md)
