---
title: partial — Metoda (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- partialmethod_CSharpKeyword
helpviewer_keywords:
- partial methods [C#]
ms.assetid: 43f40242-17e0-4452-8573-090503ad3137
ms.openlocfilehash: 29b5d442a1aa33babc24aee987e749c93a5ec727
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33269044"
---
# <a name="partial-method-c-reference"></a>partial — Metoda (odwołanie w C#)
Metoda częściowa ma podpis zdefiniowane w jednej części typu częściowego, a jej implementacja zdefiniowany w innej części typu. Metody częściowe umożliwia projektantom klasy Podaj punkty zaczepienia metody, podobny do programów obsługi zdarzeń, które deweloperzy mogą zdecydować się na implementacji lub nie. Jeśli projektanta nie dostarcza implementację, kompilator usuwa podpisu w czasie kompilacji. Do metody częściowe mają zastosowanie następujące warunki:  
  
-   Podpisy obie części typu częściowego muszą być zgodne.  
  
-   Metoda musi zwracać typ void.  
  
-   Modyfikatory dostępu, nie są dozwolone. Metody częściowe są domyślnie prywatne.  
  
 W poniższym przykładzie przedstawiono metody częściowej zdefiniowane w dwóch częściach częściowej klasy:  
  
 [!code-csharp[csrefKeywordsContextual#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-method_1.cs)]  
  
 Aby uzyskać więcej informacji, zobacz [klasy częściowe i metody](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [partial (typ)](../../../csharp/language-reference/keywords/partial-type.md)
