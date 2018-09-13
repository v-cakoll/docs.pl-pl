---
title: 'Porady: analizowanie ciągów za pomocą funkcji String.Split (Przewodnik C#)'
description: Funkcji String.Split zwraca tablicę ciągów podzielona z zestawu ograniczników. To łatwe analizowanie ciągów.
ms.date: 01/03/2018
helpviewer_keywords:
- splitting strings [C#]
- Split method [C#]
- strings [C#], splitting
- parse strings
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
ms.custom: mvc
ms.openlocfilehash: b6170be2dbb3f11906bbaa6e5c3be3e48a976246
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44708078"
---
# <a name="how-to-parse-strings-using-stringsplit-c-guide"></a>Porady: analizowanie ciągów za pomocą funkcji String.Split (Przewodnik C#)

<xref:System.String.Split%2A?displayProperty=nameWithType> Metoda tworzy tablicę podciągów, dzieląc oparte na co najmniej jeden ograniczników ciągu wejściowego. Często jest najłatwiejszym sposobem rozdzielenia ciągu na granicach słów. Również służy do dzielenia ciągów na inne określone znaki lub ciągi znaków.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Poniższy kod dzieli popularnych na tablicę ciągów dla każdego wyrazu.

[!code-csharp-interactive[split strings on word boundaries](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#1)]

Każde wystąpienie znak separatora tworzy wartości zwróconej tablicy. Następujące po sobie separatory dawać pusty ciąg jako wartość zwracana tablica.  Widać to w poniższym przykładzie, wykorzystuje miejsce jako separatora:

[!code-csharp-interactive[split strings with repeated separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#2)]

To zachowanie ułatwia w przypadku formatów takich jak pliki wartości (CSV) rozdzielonych przecinkami reprezentująca dane tabelaryczne. Kolejne przecinkami reprezentują pustej kolumnie.

Możesz przekazać opcjonalny <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> parametru, aby wykluczyć wszelkie puste ciągi w zwróconej tablicy. W przypadku bardziej skomplikowanych przetwarzania zwrócona kolekcja, można użyć [LINQ](../programming-guide/concepts/linq/index.md) do manipulowania sekwencji wynik.

<xref:System.String.Split%2A?displayProperty=nameWithType> można użyć wielu znaków separatora.
W poniższym przykładzie użyto miejsca do magazynowania, przecinki, kropki, dwukropki i kartach wszystkich przekazanych tablicę zawierającą je do oddzielania znaków, <xref:System.String.Split%2A>.
Pętla w dolnej części kodu wyświetla poszczególnych wyrazów w zwróconej tablicy.  

[!code-csharp-interactive[split strings using multiple separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#3)]

Kolejne wystąpienia dowolnego separator dawać pusty ciąg w tablicy danych wyjściowych:

[!code-csharp-interactive[split strings using multiple consecutive separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#4)]

<xref:System.String.Split%2A?displayProperty=nameWithType> może to potrwać tablicę ciągów (sekwencje znaków, które działają jako separatorów podczas analizowania ciągu docelowego, a nie pojedyncze znaki).  
  
[!code-csharp-interactive[split strings using strings as separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#5)]

Możesz wypróbować te przykłady, patrząc na kod w naszym [repozytorium GitHub](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings). Można również pobrać przykłady [jako plik zip](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../programming-guide/index.md)  
- [Ciągi](../programming-guide/strings/index.md)  
- [Wyrażeń regularnych programu .NET](../../standard/base-types/regular-expressions.md)
