---
title: 'Porady: łączenie wielu ciągów (Przewodnik C#)'
description: Istnieje wiele sposobów łączenia ciągów w języku C#. Poznaj opcje i powodów różne opcje.
ms.date: 02/20/2018
helpviewer_keywords:
- joining strings [C#]
- concatenating strings [C#]
- strings [C#], concatenation
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
ms.openlocfilehash: 355e56acf36b6212ee4563f34722b10b56a0fb47
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2018
ms.locfileid: "43468657"
---
# <a name="how-to-concatenate-multiple-strings-c-guide"></a>Porady: łączenie wielu ciągów (Przewodnik C#)

*Łączenie* to proces dołączania jednego ciągu do końca ciągu w innym. Łączenie ciągów za pomocą `+` operatora. Literały ciągu i stałych ciągów łączenie wystąpi w czasie kompilacji; występuje, nie łączenia czasu wykonywania. W przypadku zmiennych ciągu łączenia jest wykonywane tylko w czasie wykonywania.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

W poniższym przykładzie użyto łączenia, aby podzielić ciąg literału mniejszych ciągów w celu poprawienia czytelności w kodzie źródłowym. Te elementy są łączone w pojedynczy ciąg w czasie kompilacji. Nie ma żadnych kosztów wydajności w czasie wykonywania, bez względu na liczbę ciągów zaangażowane.  
  
 [!code-csharp-interactive[Combining strings at compile time](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#1)]  

Aby połączyć zmiennych ciągu, można użyć `+` lub `+=` operatorów, [Interpolacja ciągów](../language-reference/tokens/interpolated.md) lub <xref:System.String.Format%2A?displayProperty=nameWithType>, <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Join%2A?displayProperty=nameWithType> lub <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> metody. `+` Operator jest łatwa w użyciu i sprawia, że kod intuicyjne. Nawet w przypadku używania kilku `+` operatorów w jednej instrukcji, ciąg zawartości jest kopiowany tylko raz. Poniższy kod pokazuje przykłady stosowania `+` i `+=` operatory łączenia ciągów:

[!code-csharp-interactive[combining strings using +](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#2)]  

W niektórych wyrażeniach łatwiej jest łączenie ciągów przy użyciu interpolacji ciągu, co ilustruje poniższy kod:
  
[!code-csharp-interactive[building strings using string interpolation](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#3)]  
  
> [!NOTE]
> W ramach operacji łączenia ciągu kompilator języka C# traktuje pusty ciąg takie same jako pusty ciąg.

Druga metoda łączenia ciągów jest <xref:System.String.Format%2A?displayProperty=nameWithType>. Ta metoda działa dobrze w przypadku, gdy tworzysz ciąg z małą liczbą składników ciągów.

W innych przypadkach może być łączenie ciągów w pętli, w którym nie wiesz, ile ciągi źródłowe są połączenie, a rzeczywista liczba ciągi źródłowe może być dość duży. <xref:System.Text.StringBuilder> Klasa została zaprojektowana dla tych scenariuszy. Poniższy kod używa <xref:System.Text.StringBuilder.Append%2A> metody <xref:System.Text.StringBuilder> klasy do łączenia ciągów.  
  
[!code-csharp-interactive[string concatenation using string builder](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#4)]  

Przeczytaj więcej o [powodów przemawiających ciągów lub `StringBuilder` klasy](xref:System.Text.StringBuilder#StringAndSB)

Inną opcję, aby dołączyć ciągi z kolekcji jest użycie <xref:System.String.Concat%2A?displayProperty=nameWithType> metody. Użyj <xref:System.String.Join%2A?displayProperty=nameWithType> metodę, jeżeli ciągi źródłowe powinien być oddzielony przecinkiem ogranicznik. Poniższy kod łączy tablicę wyrazów za pomocą obu tych metod:

[!code-csharp-interactive[concatenation of string collection](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#5)]

Ostatnio, możesz użyć [LINQ](../programming-guide/concepts/linq/index.md) i <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> metodę, aby dołączyć ciągi z kolekcji. Ta metoda łączy ciągi źródłowe użycie wyrażenia lambda. Wyrażenie lambda wykonuje pracę można dodać każdego ciągu do gromadzenia istniejących. Poniższy przykład obejmuje szereg słów przez dodanie miejsca między każdego wyrazu w tablicy:

[!code-csharp-interactive[string concatenation using LINQ expressions](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#6)]  

Możesz wypróbować te przykłady, patrząc na kod w naszym [repozytorium GitHub](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings). Można również pobrać przykłady [jako plik zip](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).

## <a name="see-also"></a>Zobacz też

- <xref:System.String>  
- <xref:System.Text.StringBuilder>  
- [Przewodnik programowania w języku C#](../programming-guide/index.md)  
- [Ciągi](../programming-guide/strings/index.md)
