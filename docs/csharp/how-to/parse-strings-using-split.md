---
title: Jak analizować ciągi za pomocą String.Split (Przewodnik C#)
description: String.Split zwraca tablicę ciągów podzielonych z zestawu ograniczników. Jest to łatwy sposób na analizę ciągów.
ms.date: 01/03/2018
helpviewer_keywords:
- splitting strings [C#]
- Split method [C#]
- strings [C#], splitting
- parse strings
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
ms.custom: mvc
ms.openlocfilehash: b46429f3b55658e1f2a7d21eed714c1d02236c57
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "73973232"
---
# <a name="how-to-parse-strings-using-stringsplit-c-guide"></a>Jak analizować ciągi za pomocą String.Split (Przewodnik C#)

Metoda <xref:System.String.Split%2A?displayProperty=nameWithType> tworzy tablicę podciągów, dzieląc ciąg wejściowy na podstawie jednego lub więcej ograniczników. Często jest to najprostszy sposób, aby oddzielić ciąg na granicach wyrazu. Jest również używany do dzielenia ciągów na inne określone znaki lub ciągi.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Poniższy kod dzieli wspólną frazę na tablicę ciągów dla każdego wyrazu.

[!code-csharp-interactive[split strings on word boundaries](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#1)]

Każde wystąpienie znaku separatora tworzy wartość w zwracanej tablicy. Kolejne znaki separatora wytwarzają pusty ciąg jako wartość w zwracanej tablicy.  Można to zobaczyć w poniższym przykładzie, który używa spacji jako separatora:

[!code-csharp-interactive[split strings with repeated separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#2)]

To zachowanie ułatwia formaty, takie jak pliki wartości oddzielonych przecinkami (CSV) reprezentujące dane tabelaryczne. Kolejne przecinki reprezentują pustą kolumnę.

Można przekazać <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> parametr opcjonalny, aby wykluczyć puste ciągi w zwracanej tablicy. Dla bardziej skomplikowanego przetwarzania zwróconej kolekcji, można użyć [LINQ](../programming-guide/concepts/linq/index.md) do manipulowania sekwencji wyników.

<xref:System.String.Split%2A?displayProperty=nameWithType>można użyć wielu znaków separatora.
W poniższym przykładzie użyto spacji, przecinków, okresów, dwukropków i kart, wszystkie przekazywane w tablicy zawierającej te znaki oddzielające, do <xref:System.String.Split%2A>.
Pętla u dołu kodu wyświetla każdy ze słów w zwróconej tablicy.  

[!code-csharp-interactive[split strings using multiple separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#3)]

Kolejne wystąpienia dowolnego separatora wytwarzają pusty ciąg w tablicy wyjściowej:

[!code-csharp-interactive[split strings using multiple consecutive separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#4)]

<xref:System.String.Split%2A?displayProperty=nameWithType>może przyjmować tablicę ciągów znaków (sekwencje znaków, które działają jako separatory do analizowania ciągu docelowego, zamiast pojedynczych znaków).  
  
[!code-csharp-interactive[split strings using strings as separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#5)]

Możesz wypróbować te przykłady, patrząc na kod w naszym [repozytorium GitHub](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings). Możesz też pobrać próbki [jako plik zip](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../programming-guide/index.md)
- [Ciągi](../programming-guide/strings/index.md)
- [Wyrażenia regularne .NET](../../standard/base-types/regular-expressions.md)
