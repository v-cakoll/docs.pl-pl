---
title: Metoda częściowa C# — odwołanie
ms.date: 07/20/2015
f1_keywords:
- partialmethod_CSharpKeyword
helpviewer_keywords:
- partial methods [C#]
ms.assetid: 43f40242-17e0-4452-8573-090503ad3137
ms.openlocfilehash: 62efd8b47fb565316b417a65e1b0fe37e40786c8
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713225"
---
# <a name="partial-method-c-reference"></a>Metoda częściowaC# (odwołanie)

Metoda częściowa ma swój podpis zdefiniowany w jednej części typu częściowego i jego implementacja zdefiniowana w innej części typu. Metody częściowe umożliwiają projektantom klas dostarczanie punktów zaczepienia metody, podobnie jak procedury obsługi zdarzeń, które deweloperzy mogą zdecydować się na wdrożenie lub nie. Jeśli deweloper nie poda implementacji, kompilator usuwa sygnaturę w czasie kompilacji. Poniższe warunki dotyczą metod częściowych:

- Sygnatury w obu częściach typu częściowego muszą być zgodne.

- Metoda musi zwracać typ void.

- Modyfikatory dostępu nie są dozwolone. Metody częściowe są niejawnie prywatne.

Poniższy przykład przedstawia metodę częściową zdefiniowaną w dwóch częściach klasy częściowej:

[!code-csharp[csrefKeywordsContextual#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#9)]

Aby uzyskać więcej informacji, zobacz [częściowe klasy i metody](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Typ częściowy](partial-type.md)
