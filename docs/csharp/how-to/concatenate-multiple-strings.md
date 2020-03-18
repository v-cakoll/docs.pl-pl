---
title: Jak połączyć wiele ciągów (Przewodnik C#)
description: Istnieje wiele sposobów łączenia ciągów w języku C#. Poznaj opcje i przyczyny różnych wyborów.
ms.date: 02/20/2018
helpviewer_keywords:
- joining strings [C#]
- concatenating strings [C#]
- strings [C#], concatenation
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
ms.openlocfilehash: 9a0640a7ce73fa8454442cd301157bf5c265f9de
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713896"
---
# <a name="how-to-concatenate-multiple-strings-c-guide"></a>Jak połączyć wiele ciągów (Przewodnik C#)

*Łączenie* jest procesem dołączania jednego ciągu na końcu innego ciągu. Ciągi łączysz za pomocą `+` operatora. W przypadku literału ciągów i stałych ciągów łączenie odbywa się w czasie kompilacji; nie występuje konkanację w czasie wykonywania. W przypadku zmiennych ciągów łączenie występuje tylko w czasie wykonywania.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

W poniższym przykładzie użyto konkatenacji, aby podzielić literał długiego ciągu na mniejsze ciągi w celu zwiększenia czytelności w kodzie źródłowym. Te części są łączone w jeden ciąg w czasie kompilacji. Nie ma żadnych kosztów wydajności w czasie wykonywania, niezależnie od liczby ciągów zaangażowanych.  
  
 [!code-csharp-interactive[Combining strings at compile time](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#1)]  

Aby połączyć zmienne ciągów, można użyć `+` `+=` lub operatorów, [interpolacji ciągów](../language-reference/tokens/interpolated.md) <xref:System.String.Format%2A?displayProperty=nameWithType>lub <xref:System.String.Concat%2A?displayProperty=nameWithType>, lub <xref:System.String.Join%2A?displayProperty=nameWithType> <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> metod. Operator `+` jest łatwy w obsłudze i zapewnia intuicyjny kod. Nawet jeśli używasz `+` kilku operatorów w jednej instrukcji, zawartość ciągu jest kopiowany tylko raz. Poniższy kod przedstawia przykłady używania `+` `+=` i operatorów do łączenia ciągów:

[!code-csharp-interactive[combining strings using +](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#2)]  

W niektórych wyrażeniach łatwiej jest połączyć ciągi za pomocą interpolacji ciągów, jak pokazano w poniższym kodzie:
  
[!code-csharp-interactive[building strings using string interpolation](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#3)]  
  
> [!NOTE]
> W operacjach łączenia ciągów kompilator C# traktuje ciąg zerowy taki sam jak pusty ciąg.

Inną metodą łączenia ciągów jest <xref:System.String.Format%2A?displayProperty=nameWithType>. Ta metoda działa dobrze podczas tworzenia ciągu z niewielkiej liczby ciągów składników.

W innych przypadkach może być łączenie ciągów w pętli, gdzie nie wiesz, ile ciągów źródłowych są łączące, a rzeczywista liczba ciągów źródłowych może być dość duża. Klasa <xref:System.Text.StringBuilder> została zaprojektowana dla tych scenariuszy. Poniższy kod używa <xref:System.Text.StringBuilder.Append%2A> metody <xref:System.Text.StringBuilder> klasy do łączenia ciągów.  
  
[!code-csharp-interactive[string concatenation using string builder](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#4)]  

Możesz przeczytać więcej o [powodach, dla których `StringBuilder` należy wybrać łączenie ciągów lub klasę](xref:System.Text.StringBuilder#StringAndSB).

Inną opcją łączenia ciągów z <xref:System.String.Concat%2A?displayProperty=nameWithType> kolekcji jest użycie metody. Użyj <xref:System.String.Join%2A?displayProperty=nameWithType> metody, jeśli ciągi źródłowe powinny być oddzielone delimeter. Poniższy kod łączy tablicę wyrazów przy użyciu obu metod:

[!code-csharp-interactive[concatenation of string collection](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#5)]

W końcu można użyć [LINQ](../programming-guide/concepts/linq/index.md) i <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> metody do łączenia ciągów z kolekcji. Ta metoda łączy ciągi źródłowe przy użyciu wyrażenia lambda. Wyrażenie lambda wykonuje pracę, aby dodać każdy ciąg do istniejącej akumulacji. Poniższy przykład łączy tablicę wyrazów, dodając odstęp między każdym wyrazem w tablicy:

[!code-csharp-interactive[string concatenation using LINQ expressions](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#6)]  

Możesz wypróbować te przykłady, patrząc na kod w naszym [repozytorium GitHub](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings). Możesz też pobrać próbki [jako plik zip](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).

## <a name="see-also"></a>Zobacz też

- <xref:System.String>
- <xref:System.Text.StringBuilder>
- [Przewodnik programowania języka C#](../programming-guide/index.md)
- [Ciągi](../programming-guide/strings/index.md)
