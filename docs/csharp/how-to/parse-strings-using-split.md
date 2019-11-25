---
title: Jak analizować ciągi przy użyciu ciągu. Split (C# przewodnik)
description: Ciąg. Split zwraca tablicę ciągów podzieloną z zestawu ograniczników. Jest to prosty sposób, aby przeanalizować ciągi.
ms.date: 01/03/2018
helpviewer_keywords:
- splitting strings [C#]
- Split method [C#]
- strings [C#], splitting
- parse strings
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
ms.custom: mvc
ms.openlocfilehash: b46429f3b55658e1f2a7d21eed714c1d02236c57
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73973232"
---
# <a name="how-to-parse-strings-using-stringsplit-c-guide"></a>Jak analizować ciągi przy użyciu ciągu. Split (C# przewodnik)

Metoda <xref:System.String.Split%2A?displayProperty=nameWithType> tworzy tablicę podciągów, dzieląc ciąg wejściowy na podstawie co najmniej jednego ogranicznika. Często najprostszym sposobem jest oddzielenie ciągu od granic wyrazów. Jest on również używany do dzielenia ciągów dla innych określonych znaków lub ciągów.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Poniższy kod dzieli wspólną frazę na tablicę ciągów dla każdego wyrazu.

[!code-csharp-interactive[split strings on word boundaries](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#1)]

Każde wystąpienie znaku separatora generuje wartość w tablicy zwracanej. Kolejne znaki separatora tworzą pusty ciąg jako wartość w zwróconej tablicy.  Można to zobaczyć w poniższym przykładzie, który używa spacji jako separatora:

[!code-csharp-interactive[split strings with repeated separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#2)]

Takie zachowanie ułatwia korzystanie z formatów, takich jak pliki z wartościami rozdzielanymi przecinkami (CSV) reprezentujące dane tabelaryczne. Kolejne przecinki reprezentują pustą kolumnę.

Można przekazać opcjonalny parametr <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType>, aby wykluczyć wszelkie puste ciągi w zwróconej tablicy. Aby bardziej skomplikowane przetwarzanie zwróconej kolekcji było możliwe, można użyć [LINQ](../programming-guide/concepts/linq/index.md) do manipulowania sekwencją wyników.

<xref:System.String.Split%2A?displayProperty=nameWithType> może używać wielu znaków separatora.
W poniższym przykładzie są wykorzystywane spacje, przecinki, kropki, dwukropki i karty, wszystkie przechodzą do tablicy zawierającej te oddzielane znaki, do <xref:System.String.Split%2A>.
Pętla u dołu kodu wyświetla każdy wyraz w zwracanej tablicy.  

[!code-csharp-interactive[split strings using multiple separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#3)]

Kolejne wystąpienia dowolnego separatora tworzą pusty ciąg w tablicy wyjściowej:

[!code-csharp-interactive[split strings using multiple consecutive separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#4)]

<xref:System.String.Split%2A?displayProperty=nameWithType> może pobrać tablicę ciągów (sekwencje znaków, które działają jako separatory do analizowania ciągu docelowego, zamiast pojedynczych znaków).  
  
[!code-csharp-interactive[split strings using strings as separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#5)]

Możesz wypróbować te przykłady, przeglądając kod w naszym [repozytorium GitHub](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings). Możesz też pobrać przykłady [jako plik zip](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../programming-guide/index.md)
- [Ciągi](../programming-guide/strings/index.md)
- [Wyrażenia regularne .NET](../../standard/base-types/regular-expressions.md)
