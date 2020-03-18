---
title: metoda częściowa — odwołanie do języka C#
ms.date: 07/20/2015
f1_keywords:
- partialmethod_CSharpKeyword
helpviewer_keywords:
- partial methods [C#]
ms.assetid: 43f40242-17e0-4452-8573-090503ad3137
ms.openlocfilehash: 62efd8b47fb565316b417a65e1b0fe37e40786c8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713225"
---
# <a name="partial-method-c-reference"></a>metoda częściowa (odwołanie do języka C#)

Metoda częściowa ma swój podpis zdefiniowany w jednej części typu częściowego, a jej implementacja zdefiniowana w innej części typu. Metody częściowe umożliwiają projektantom klas zapewnienie haków metody, podobnie jak programy obsługi zdarzeń, które deweloperzy mogą zdecydować się zaimplementować, czy nie. Jeśli deweloper nie dostarcza implementacji, kompilator usuwa podpis w czasie kompilacji. Następujące warunki mają zastosowanie do metod częściowych:

- Podpisy w obu częściach typu częściowego muszą być zgodne.

- Metoda musi zwracać void.

- Modyfikatory dostępu nie są dozwolone. Metody częściowe są niejawnie prywatne.

W poniższym przykładzie przedstawiono metodę częściową zdefiniowaną w dwóch częściach klasy częściowej:

[!code-csharp[csrefKeywordsContextual#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#9)]

Aby uzyskać więcej informacji, zobacz [Klasy częściowe i metody](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [typ częściowy](partial-type.md)
