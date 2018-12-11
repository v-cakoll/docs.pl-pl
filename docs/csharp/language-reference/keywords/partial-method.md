---
title: Metoda częściowa - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- partialmethod_CSharpKeyword
helpviewer_keywords:
- partial methods [C#]
ms.assetid: 43f40242-17e0-4452-8573-090503ad3137
ms.openlocfilehash: 742d6ca744ac723179718f1400e600411712dd40
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53238289"
---
# <a name="partial-method-c-reference"></a>Metoda częściowa (odwołanie w C#)

Metoda częściowa ma jeho signatura zdefiniowane w jednej części typu częściowego, a jego implementacja zdefiniowane w innej części tego typu. Metody częściowe umożliwiają klasy projektantów zapewnić punkty zaczepienia metody, podobny do programów obsługi zdarzeń, które deweloperzy mogą zdecydować się na implementacji, czy nie. Jeśli deweloper nie dostarcza implementację, kompilator usuwa podpisu w czasie kompilacji. Do metod częściowych mają zastosowanie następujące warunki:

- Podpisy w obie części typu częściowego muszą być zgodne.

- Metoda musi zwracać typ void.

- Brak modyfikatorów dostępu są dozwolone. Metody częściowe są niejawnie prywatne.

Metoda częściowa definicja z dwóch części klasy częściowej można znaleźć w poniższym przykładzie:

[!code-csharp[csrefKeywordsContextual#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#9)]

Aby uzyskać więcej informacji, zobacz [klasy częściowe i metody](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [typu częściowego](partial-type.md)