---
title: "Porady: analizowanie ciągów za pomocą String.Split (Przewodnik C#)"
description: "String.Split zwraca tablicę ciągów podzielić z zestawu ograniczników. Jest łatwy sposób analizowanie ciągów."
ms.date: 01/03/2018
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- splitting strings [C#]
- Split method [C#]
- strings [C#], splitting
- parse strings
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
author: BillWagner
ms.author: wiwagn
ms.custom: mvc
ms.openlocfilehash: fc1032f2cdf6706ec933323643dbf6ecff3e9f6f
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-parse-strings-using-stringsplit-c-guide"></a>Porady: analizowanie ciągów za pomocą String.Split (Przewodnik C#)

<xref:System.String.Split%2A?displayProperty=nameWithType> Metoda tworzy tablicę podciągów dzieląc oparte na co najmniej jeden Ogranicznik ciągu wejściowego. Często jest najprostszym sposobem oddzielnych ciąg na granice programu word. Służy również do dzielenie ciągów na inne określonych znaków lub ciągów.

Poniższy kod dzieli popularnych na tablicę ciągów dla każdego wyrazu.
Wypróbuj ją samodzielnie, naciskając klawisz *Uruchom* przycisku.

[!code-csharp-interactive[split strings on word boundaries](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#1)]

Każde wystąpienie znak separatora daje wartość zwracana tablica. Kolejne separatory utworzyć pusty ciąg jako wartość zwracana tablica.  W poniższym przykładzie, który używa miejsca jako separator można wyświetlić to:

[!code-csharp-interactive[split strings with repeated separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#2)]

To zachowanie ułatwia formatów takich jak pliki wartości (CSV) rozdzielonych przecinkami reprezentująca danych tabelarycznych. Kolejne przecinkami reprezentuje pustą kolumnę.

Można przekazać opcjonalnie <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=fullName> parametr, aby wykluczyć wszystkie puste ciągi w zwróconej tablicy. W przypadku bardziej skomplikowanych przetwarzania zwracana kolekcja, można użyć [LINQ](../programming-guide/concepts/linq/index.md) do manipulowania sekwencji wynik.    

<xref:System.String.Split%2A?displayProperty=nameWithType>można użyć wielu znaków separatora. W poniższym przykładzie użyto spacji, przecinków okresów, dwukropki i karty, wszystkie przekazano tablicę zawierającą je do oddzielania znaków, <xref:System.String.Split%2A>.  Pętla w dolnej części kodu wyświetla poszczególnych wyrazów w zwróconej tablicy.  

[!code-csharp-interactive[split strings using multiple separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#3)]

Kolejne wystąpienia dowolnego separatora utworzyć pusty ciąg na tablicę danych wyjściowych:

[!code-csharp-interactive[split strings using multiple consecutive separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#4)]

<xref:System.String.Split%2A?displayProperty=nameWithType>możliwe jest tablicą ciągów (sekwencji znaków, które działają jako separatorów do analizowania parametrów docelowej, zamiast pojedynczy znaki).  
  
[!code-csharp-interactive[split strings using strings as separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#5)]

Możesz spróbować te przykłady, sprawdzając kod w naszym [repozytorium GitHub](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings)

## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../programming-guide/index.md)  
 [Ciągi](../programming-guide/strings/index.md)  
 [.NET framework — nieprawidłowe wyrażenia](https://msdn.microsoft.com/library/hs600312)
