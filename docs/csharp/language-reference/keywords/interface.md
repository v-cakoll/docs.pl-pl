---
title: interface (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- interface_CSharpKeyword
helpviewer_keywords:
- interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
ms.openlocfilehash: 0320b1e287f8c7a3eb7751b68b40120f74e8f61c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="interface-c-reference"></a>interface (odwołanie w C#)
Interfejs zawiera tylko sygnatur [metody](../../../csharp/programming-guide/classes-and-structs/methods.md), [właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md), [zdarzenia](../../../csharp/programming-guide/events/index.md) lub [indeksatory](../../../csharp/programming-guide/indexers/index.md). Klasy lub struktury, która implementuje interfejs musi implementować członków interfejsu, które są określone w definicji interfejsu. W poniższym przykładzie klasa `ImplementationClass` musi implementować metodę o nazwie `SampleMethod` czy nie ma parametrów i zwraca `void`.  
  
 Aby uzyskać dodatkowe informacje i przykłady, zobacz [interfejsów](../../../csharp/programming-guide/interfaces/index.md).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csrefKeywordsTypes#14](../../../csharp/language-reference/keywords/codesnippet/CSharp/interface_1.cs)]  
  
 Interfejs może być elementem członkowskim przestrzeni nazw lub klasy i może zawierać podpisów następujące elementy:  
  
-   [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
-   [Właściwości](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
  
-   [Indeksatory](../../../csharp/programming-guide/indexers/using-indexers.md)  
  
-   [Zdarzenia](../../../csharp/language-reference/keywords/event.md)  
  
 Interfejs może dziedziczyć z jednego lub więcej interfejsach podstawowych.  
  
 Gdy listy Typ podstawowy zawiera klasę podstawową i interfejsy, klasy podstawowej musi występować pierwsze na liście.  
  
 Klasy, która implementuje interfejs jawnie można implementować członków interfejsu. Jawnie implementowane elementu członkowskiego nie jest dostępny za pośrednictwem wystąpienia klasy, ale tylko za pośrednictwem wystąpienia interfejsu.  
  
 Aby uzyskać bardziej szczegółowe informacje i przykłady kodu w jawnej implementacji interfejsu, zobacz [jawnej implementacji interfejsu](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano implementacji interfejsu. W tym przykładzie interfejs zawiera deklaracji właściwości i klasa zawiera implementację. Wszystkie wystąpienia klasy, która implementuje `IPoint` ma właściwości całkowitą `x` i `y`.  
  
 [!code-csharp[csrefKeywordsTypes#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/interface_2.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Typy odwołań](../../../csharp/language-reference/keywords/reference-types.md)  
 [Interfejsy](../../../csharp/programming-guide/interfaces/index.md)  
 [Używanie właściwości](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
 [Używanie indeksatorów](../../../csharp/programming-guide/indexers/using-indexers.md)  
 [class](../../../csharp/language-reference/keywords/class.md)  
 [struct](../../../csharp/language-reference/keywords/struct.md)  
 [Interfejsy](../../../csharp/programming-guide/interfaces/index.md)
