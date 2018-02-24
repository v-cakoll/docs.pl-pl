---
title: "Porady: łączenie wielu ciągów (Przewodnik C#)"
description: "Istnieje wiele sposobów łączenia ciągów w języku C#. Poznaj opcje i przyczynami różne opcje."
ms.date: 02/20/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- joining strings [C#]
- concatenating strings [C#]
- strings [C#], concatenation
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 978f631a130f9ec2d450779f2a6296a6ce3af356
ms.sourcegitcommit: cec0525b2121c36198379525e69aa5388266db5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="how-to-concatenate-multiple-strings-c-guide"></a>Porady: łączenie wielu ciągów (Przewodnik C#)

*Łączenie* to proces dołączania jeden ciąg do końca ciągu innego. Łączenie ciągów za pomocą `+` operatora. Literały ciągu i stałe typu string łączenia wystąpi w czasie kompilacji; występuje, nie łączenia czasu wykonywania. Dla zmiennych ciągu łączenia występuje tylko w czasie wykonywania.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

W poniższym przykładzie użyto łączenia, aby podzielić ciąg literału na mniejsze ciągów w celu zwiększenia czytelności w kodzie źródłowym. Te elementy są połączone w jeden ciąg w czasie kompilacji. Nie ma żadnych kosztów wydajności w czasie wykonywania, niezależnie od liczby ciągów związane.  
  
 [!code-csharp-interactive[Combining strings at compile time](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#1)]  
  

Aby połączyć zmiennych ciągu można użyć `+` lub `+=` operatorów, [ciągu interpolacji](../tutorials/string-interpolation.md) lub <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Format%2A?displayProperty=nameWithType>, <xref:System.String.Join%2A?displayProperty=nameWithType> lub <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> metody. `+` Operator jest łatwy w użyciu i sprawia, że dla intuicyjne kodu. Nawet jeśli użyć kilku `+` operatory w jednej instrukcji, ciąg zawartości jest kopiowany tylko raz. Poniższy kod przedstawia dwa przykłady użycia `+` operatora łączenia ciągów:

[!code-csharp-interactive[combining strings using +](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#2)]  

W niektórych wyrażeniach łatwiej ciągów za pomocą ciągu interpolacji, jak przedstawiono na poniższym kodem:
  
[!code-csharp-interactive[building strings using string interpolation](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#3)]  
  
> [!NOTE]
>  W operacji łączenia ciągu kompilator języka C# traktuje pusty ciąg takie same jako ciąg pusty.

Innej metody do ciągów jest <xref:System.String.Format%2A?displayProperty=nameWithType>. Ta metoda działa również w przypadku, gdy tworzysz ciąg z małą liczbą ciągów składnika. Ta metoda jest również doskonałym wyborem, gdy wiesz liczba ciągów, które składają się z połączony ciąg.

W innych przypadkach może być łączenie ciągów w pętli, których nie wiadomo, ile parametry źródła są łączenie i rzeczywistą liczbę ciągów źródło może być dość duży. <xref:System.Text.StringBuilder> Klasy zostało zaprojektowane na potrzeby tych scenariuszy. Poniższy kod używa <xref:System.Text.StringBuilder.Append%2A> metody <xref:System.Text.StringBuilder> klasy do ciągów.  
  
[!code-csharp-interactive[string concatenation using string builder](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#4)]  

Możesz przeczytać dodatkowe informacje [powodów przemawiających ciągów lub `StringBuilder` — klasa](xref:System.Text.StringBuilder#StringAndSB)

Inną opcją sprzęgać ciągów z kolekcji jest użycie <xref:System.String.Concat%2A?displayProperty=nameWithType> metody. Użyj <xref:System.String.Join%2A?displayProperty=nameWithType> metodę, jeśli ciągi powinny być oddzielone delimeter. Poniższy kod łączy tablicę wyrazy przy użyciu obu metod:

[!code-csharp-interactive[concatenation of string collection](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#5)]

Ostatnio, można użyć [LINQ](../programming-guide/concepts/linq/index.md) i <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> metody przyłączania ciągów z kolekcji. Ta metoda łączy ciągów źródło, za pomocą wyrażenia lambda. Wyrażenia lambda wykonuje pracę można dodać każdego ciągu do gromadzenia istniejących. Poniższy przykład łączy Tablica słów przez dodanie odstępów między wyrazami w tablicy:

[!code-csharp-interactive[string concatenation using LINQ expressions](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#6)]  


## <a name="see-also"></a>Zobacz też  
 <xref:System.String>  
 <xref:System.Text.StringBuilder>  
 [Przewodnik programowania w języku C#](../programming-guide/index.md)  
 [Ciągi](../programming-guide/strings/index.md)
