---
title: Jak przeanalizować ciągi przy użyciu String.Split (Przewodnik c#)
description: String.Split zwraca tablicę ciągów podzielonych z zestawu ograniczników. Jest to łatwy sposób na analizę ciągów.
ms.date: 01/03/2018
helpviewer_keywords:
- splitting strings [C#]
- Split method [C#]
- strings [C#], splitting
- parse strings
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
ms.custom: mvc
ms.openlocfilehash: fb11ff59705188f9425beedfbbbf3c244d21f587
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121507"
---
# <a name="how-to-parse-strings-using-stringsplit-c-guide"></a>Jak przeanalizować ciągi przy użyciu String.Split (Przewodnik c#)

Metoda <xref:System.String.Split%2A?displayProperty=nameWithType> tworzy tablicę podciągów przez podzielenie ciągu wejściowego na podstawie jednego lub więcej ograniczników. Często jest to najprostszy sposób na oddzielenie ciągu od granic wyrazu. Jest również używany do dzielenia ciągów na inne określone znaki lub ciągi.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Poniższy kod dzieli wspólną frazę na tablicę ciągów dla każdego wyrazu.

[!code-csharp-interactive[split strings on word boundaries](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#1)]

Każde wystąpienie znaku separatora tworzy wartość w zwróconej tablicy. Kolejne znaki separatora tworzą pusty ciąg jako wartość w zwróconej tablicy.  Można to zobaczyć w poniższym przykładzie, który używa spacji jako separatora:

[!code-csharp-interactive[split strings with repeated separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#2)]

To zachowanie ułatwia formatom, takim jak pliki wartości oddzielonych przecinkami (CSV) reprezentujące dane tabelaryczne. Kolejne przecinki reprezentują pustą kolumnę.

Można przekazać parametr <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> opcjonalny, aby wykluczyć wszelkie puste ciągi w zwróconej tablicy. Dla bardziej skomplikowanego przetwarzania zwróconej kolekcji, można użyć [LINQ](../programming-guide/concepts/linq/index.md) do manipulowania sekwencji wyników.

<xref:System.String.Split%2A?displayProperty=nameWithType>można użyć wielu znaków separatora.
W poniższym przykładzie użyto spacji, przecinków, kropek, dwukropków i kart, wszystkie przekazywane w tablicy zawierającej te znaki oddzielające do <xref:System.String.Split%2A>.
Pętla w dolnej części kodu wyświetla każdy ze słów w zwróconej tablicy.  

[!code-csharp-interactive[split strings using multiple separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#3)]

Kolejne wystąpienia dowolnego separatora wytwarzają pusty ciąg w tablicy wyjściowej:

[!code-csharp-interactive[split strings using multiple consecutive separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#4)]

<xref:System.String.Split%2A?displayProperty=nameWithType>może przyjmować tablicę ciągów (sekwencje znaków, które działają jako separatory do analizowania ciągu docelowego, zamiast pojedynczych znaków).  
  
[!code-csharp-interactive[split strings using strings as separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#5)]

Możesz wypróbować te przykłady, patrząc na kod w naszym [repozytorium GitHub](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings). Możesz też pobrać próbki [jako plik zip](../../../samples/snippets/csharp/how-to/strings.zip).

## <a name="see-also"></a>Zobacz też

- [C# Przewodnik programowania](../programming-guide/index.md)
- [Ciągi](../programming-guide/strings/index.md)
- [Wyrażenia regularne platformy .NET](../../standard/base-types/regular-expressions.md)
