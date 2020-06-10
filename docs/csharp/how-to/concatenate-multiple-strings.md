---
title: Jak połączyć wiele ciągów (Przewodnik C#)
description: Istnieje wiele sposobów łączenia ciągów w języku C#. Zapoznaj się z opcjami i przyczynami związanymi z różnymi opcjami.
ms.date: 02/20/2018
helpviewer_keywords:
- joining strings [C#]
- concatenating strings [C#]
- strings [C#], concatenation
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
ms.openlocfilehash: ef3d79c5b40d08cb76e58eba1c8831c468fd1fc0
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2020
ms.locfileid: "84663021"
---
# <a name="how-to-concatenate-multiple-strings-c-guide"></a>Jak połączyć wiele ciągów (Przewodnik C#)

*Łączenie* jest procesem dołączania jednego ciągu do końca innego ciągu. Parametry są łączone za pomocą `+` operatora. W przypadku literałów ciągów i stałych ciągów łączenie odbywa się w czasie kompilacji; Brak łączenia w czasie wykonywania. W przypadku zmiennych ciągów łączenie odbywa się tylko w czasie wykonywania.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Poniższy przykład używa łączenia do dzielenia długiego literału ciągu na mniejsze ciągi w celu zwiększenia czytelności w kodzie źródłowym. Te części są łączone w jeden ciąg w czasie kompilacji. Nie ma kosztu wydajności w czasie wykonywania niezależnie od liczby używanych ciągów.

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/Concatenate.cs" id="Snippet1":::

Aby połączyć zmienne ciągów, można użyć `+` `+=` operatorów or, [interpolacji ciągów](../language-reference/tokens/interpolated.md) lub <xref:System.String.Format%2A?displayProperty=nameWithType> <xref:System.String.Concat%2A?displayProperty=nameWithType> <xref:System.String.Join%2A?displayProperty=nameWithType> <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> metod. `+`Operator jest łatwy w użyciu i pozwala na intuicyjny kod. Nawet jeśli używasz kilku `+` operatorów w jednej instrukcji, zawartość ciągu jest kopiowana tylko raz. Poniższy kod przedstawia przykłady użycia `+` `+=` operatorów i do łączenia ciągów:

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/Concatenate.cs" id="Snippet2":::

W niektórych wyrażeniach łatwiej jest łączyć ciągi przy użyciu interpolacji ciągów, jak pokazano w poniższym kodzie:

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/Concatenate.cs" id="Snippet3":::

> [!NOTE]
> W operacjach łączenia ciągów kompilator języka C# traktuje ciąg o wartości null tak samo jak pusty ciąg.

Inną metodą łączenia ciągów jest <xref:System.String.Format%2A?displayProperty=nameWithType> . Ta metoda dobrze sprawdza się w przypadku kompilowania ciągu z niewielkiej liczby ciągów komponentów.

W innych przypadkach można łączyć ciągi w pętli, w której nie wiadomo, ile łączonych parametrów źródłowych, a rzeczywista liczba ciągów źródłowych może być duża. <xref:System.Text.StringBuilder>Klasa została zaprojektowana dla tych scenariuszy. Poniższy kod używa <xref:System.Text.StringBuilder.Append%2A> metody <xref:System.Text.StringBuilder> klasy do łączenia ciągów.

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/Concatenate.cs" id="Snippet4":::

Więcej informacji na temat [przyczyn wyboru łączenia ciągów lub `StringBuilder` klasy](https://docs.microsoft.com/dotnet/api/system.text.stringbuilder#the-string-and-stringbuilder-types).

Kolejną opcją dołączenia ciągów do kolekcji jest użycie <xref:System.String.Concat%2A?displayProperty=nameWithType> metody. Użyj <xref:System.String.Join%2A?displayProperty=nameWithType> metody, jeśli ciągi źródłowe powinny być oddzielone ogranicznikiem. Poniższy kod łączy tablicę wyrazów przy użyciu obu metod:

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/Concatenate.cs" id="Snippet5":::

Na koniec można użyć [LINQ](../programming-guide/concepts/linq/index.md) i <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> metody do przyłączania ciągów do kolekcji. Ta metoda łączy parametry źródłowe za pomocą wyrażenia lambda. Wyrażenie lambda wykonuje pracy, aby dodać każdy ciąg do istniejącego akumulacji. Poniższy przykład łączy tablicę wyrazów przez dodanie odstępu między każdym słowem w tablicy:

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/Concatenate.cs" id="Snippet6":::

## <a name="see-also"></a>Zobacz także

- <xref:System.String>
- <xref:System.Text.StringBuilder>
- [Przewodnik programowania w języku C#](../programming-guide/index.md)
- [Ciągi](../programming-guide/strings/index.md)
