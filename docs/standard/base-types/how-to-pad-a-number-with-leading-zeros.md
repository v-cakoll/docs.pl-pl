---
title: 'Instrukcje: Uzupełnianie liczby zerami wiodącymi'
ms.date: 02/25/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- numeric format strings [.NET Framework]
- formatting [.NET Framework], numbers
- number formatting [.NET Framework]
- numbers [.NET Framework], format strings
ms.assetid: 0b2c2cb5-c580-4891-8d81-cb632f5ec384
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 54c3eb734184adf5168607cfc8bcbf6c17ea493a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61860649"
---
# <a name="how-to-pad-a-number-with-leading-zeros"></a>Instrukcje: Uzupełnianie liczby zerami wiodącymi

Można dodać zer wiodących na liczbę całkowitą, za pomocą "D" [standardowy Ciąg formatujący](../../../docs/standard/base-types/standard-numeric-format-strings.md) przy użyciu specyfikatora dokładności. Można dodać zer wiodących zarówno liczba całkowita, jak i liczb zmiennoprzecinkowych za pomocą [ciąg niestandardowego formatu liczb](../../../docs/standard/base-types/custom-numeric-format-strings.md). W tym artykule pokazano, jak uzupełnianie liczby zerami wiodącymi za pomocą obu metod.

## <a name="to-pad-an-integer-with-leading-zeros-to-a-specific-length"></a>Aby uzupełnić liczbą całkowitą z wiodącymi zerami w celu określonej długości

1. Określ minimalną liczbę cyfr, ma wartość całkowitą, aby wyświetlić. Uwzględnij wszystkie wiodące cyfry w tej liczby.

1. Określ, czy chcesz wyświetlić liczbę całkowitą jako wartość dziesiętną lub wartości szesnastkowej.

    - Aby wyświetlić liczbę całkowitą jako wartość dziesiętną, należy wywołać jej `ToString(String)` metody i przekazać ciągu "D*n*" jako wartości `format` parametru, gdzie *n* reprezentuje minimalna długość ciągu.

    - Aby wyświetlić liczbę całkowitą jako wartość szesnastkową, należy wywołać jej `ToString(String)` metody i przekazać ciągu "X*n*" jako wartości parametru formatu, gdzie *n* reprezentuje minimalna długość ciągu.

Umożliwia również ciąg formatu w ciągu interpolowanym zarówno [ C# ](../../csharp/language-reference/tokens/interpolated.md) i [języka Visual Basic](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md), lub można wywołać metodę, takich jak <xref:System.String.Format%2A?displayProperty=nameWithType> lub <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, używającej [ Formatowanie złożone](../../../docs/standard/base-types/composite-formatting.md).

Poniższy przykład formatuje kilka wartości całkowitych zerami wiodącymi, tak aby łączna długość sformatowany numer jest co najmniej osiem znaków.

[!code-csharp[Formatting.HowTo.PadNumber#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#1)]
[!code-vb[Formatting.HowTo.PadNumber#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#1)]

## <a name="to-pad-an-integer-with-a-specific-number-of-leading-zeros"></a>Aby uzupełnić liczbą całkowitą z określonej liczby zer wiodących

1. Określ, ile zer wiodących wartość całkowitą, aby wyświetlić.

1. Określ, czy chcesz wyświetlić liczbę całkowitą jako wartość dziesiętną lub wartości szesnastkowej.

    - Formatowanie ją jako wartość dziesiętną wymaga, że używasz specyfikator formatu standardowego "D".

    - Formatowania w postaci szesnastkowej wymaga, że używasz specyfikator formatu standardowego "X".

1. Określają długość unpadded ciągu numerycznego, wywołując wartość całkowitą `ToString("D").Length` lub `ToString("X").Length` metody.

1. Dodaj numer zer wiodących, które chcesz uwzględnić w sformatowanym ciągu do długości unpadded ciągów liczbowych. Dodanie liczby zer wiodących definiuje całkowita długość ciągu wypełniony.

1. Wywołania na wartość całkowitą `ToString(String)` metody i przekazać ciągu "D*n*" dziesiętnych ciągów i "X*n*" dla ciągów szesnastkowych, gdzie *n* reprezentuje sumę długość ciągu wypełniony. Można również użyć "D*n*" lub "X*n*" sformatować ciąg w metodzie, która obsługuje formatowanie złożone.

Poniższy przykład dopełnia wartość całkowitą z pięciu zer wiodących.

[!code-csharp[Formatting.HowTo.PadNumber#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#2)]
[!code-vb[Formatting.HowTo.PadNumber#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#2)]

## <a name="to-pad-a-numeric-value-with-leading-zeros-to-a-specific-length"></a>Aby uzupełnić wartość liczbową z wiodącymi zerami w celu określonej długości

1. Określ liczbę cyfr na lewo od separatora dziesiętnego ciąg reprezentujący liczbę, aby mieć. Obejmują wszystkie zera wiodące w tym łącznej liczby cyfr.

1. Zdefiniuj ciąg niestandardowego formatu liczb, który używa symbol zastępczy zero "0", który reprezentuje minimalnej liczby zerami.

1. Zadzwoń na numer `ToString(String)` metody i przekazać ją w ciągu formatu niestandardowego. Umożliwia także ciągu formatu niestandardowego Interpolacja ciągów lub z metodą, która obsługuje formatowanie złożone.

W poniższym przykładzie sformatowano kilka wartości liczbowych z zerami. Dlatego całkowita długość sformatowany numer jest co najmniej ośmiu cyfr na lewo od separatora dziesiętnego.

[!code-csharp[Formatting.HowTo.PadNumber#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#3)]
[!code-vb[Formatting.HowTo.PadNumber#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#3)]

## <a name="to-pad-a-numeric-value-with-a-specific-number-of-leading-zeros"></a>Aby uzupełnić wartość liczbową z określonej liczby zer wiodących

1. Określ, ile zer wiodących ma wartość liczbowa.

1. Określ liczbę cyfr na lewo od separatora dziesiętnego w ciągu numerycznego unpadded:

    1. Ustal, czy ciąg reprezentujący liczbę zawiera symbol dziesiętny.

    1. Jeśli posiada symbol punktu dziesiętnego, należy określić liczbę znaków z lewej strony punktu dziesiętnego.

         —lub—

         Jeśli nie zawiera symbol punktu dziesiętnego, należy określić długość ciągu.

1. Utwórz ciąg formatu niestandardowego, który używa:

    - Symbol zastępczy zero "0" dla każdego z zer wiodących pojawią się w ciągu.

    - Symbol zastępczy zero albo symbol zastępczy cyfry "#" do reprezentowania każdej cyfry w domyślnego ciągu.

1. Dostarczyć ciąg formatu niestandardowego jako parametr, albo numeru `ToString(String)` metodę lub metodę, która obsługuje formatowanie złożone.

Poniższy przykład dopełnia dwa <xref:System.Double> wartości z pięciu zer wiodących.

[!code-csharp[Formatting.HowTo.PadNumber#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#4)]
[!code-vb[Formatting.HowTo.PadNumber#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#4)]

## <a name="see-also"></a>Zobacz także

- [Niestandardowe ciągi formatujące liczby](../../../docs/standard/base-types/custom-numeric-format-strings.md)
- [Standardowe ciągi formatujące liczby](../../../docs/standard/base-types/standard-numeric-format-strings.md)
- [Złożone formatowanie](../../../docs/standard/base-types/composite-formatting.md)
