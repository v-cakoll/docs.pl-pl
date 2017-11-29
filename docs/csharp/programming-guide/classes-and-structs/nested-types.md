---
title: "Zagnieżdżone typy (Przewodnik programowania w języku C#)"
ms.date: 07/10/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: nested types [C#]
ms.assetid: f2e1b315-e3d1-48ce-977f-7bae0960ba99
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ab13c68b638062ab89c90dbfc51b51b8d72d3bde
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="nested-types-c-programming-guide"></a>Zagnieżdżone typy (Przewodnik programowania w języku C#)
Typ zdefiniowany w ramach [klasy](../../../csharp/language-reference/keywords/class.md) lub [struktury](../../../csharp/language-reference/keywords/struct.md) nosi nazwę typu zagnieżdżonego. Na przykład:  
  
[!code-csharp[csProgGuideObjects#68](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_1.cs)]  
  
Niezależnie od tego, czy zewnętrznego typu klasy lub struktury, domyślnie zagnieżdżone typy [prywatnego](../../../csharp/language-reference/keywords/private.md); są one dostępne tylko z ich typu zawierającego. W poprzednim przykładzie `Nested` klasy jest niedostępna dla typów zewnętrznych. 

Można również określić [modyfikator dostępu](../../language-reference/keywords/access-modifiers.md) do definiowania ułatwień dostępu typu zagnieżdżonego w następujący sposób:

- Zagnieżdżone typy **klasy** może być [publicznego](../../../csharp/language-reference/keywords/public.md), [chronione](../../../csharp/language-reference/keywords/protected.md), [wewnętrzny](../../../csharp/language-reference/keywords/internal.md), [chronionych wewnętrznych](../../../csharp/language-reference/keywords/protected-internal.md), [prywatnej](../../../csharp/language-reference/keywords/private.md) lub [prywatne chronione](../../../csharp/language-reference/keywords/private-protected.md). 

   Jednak definiowanie `protected`, `protected internal` lub `private protected` zagnieżdżona klasa wewnątrz [zapieczętowane klasy](../../language-reference/keywords/sealed.md) generuje ostrzeżenie kompilatora [CS0628](../../misc/cs0628.md), "w klasie zapieczętowanej zadeklarowano nowy chroniony element członkowski."
  
- Zagnieżdżone typy **struktury** może być [publicznego](../../../csharp/language-reference/keywords/public.md), [wewnętrzny](../../../csharp/language-reference/keywords/internal.md), lub [prywatnej](../../../csharp/language-reference/keywords/private.md).
  
Poniższy przykład powoduje, że `Nested` publicznej klasy:
  
[!code-csharp[csProgGuideObjects#69](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_2.cs)]  
  
 Typ zagnieżdżony lub wewnętrznej, ma dostęp do typu zawierającego lub zewnętrzne. Aby uzyskać dostęp do typu zawierającego, przekaż go jako argument do konstruktora typu zagnieżdżonego. Na przykład:  
  
 [!code-csharp[csProgGuideObjects#70](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_3.cs)]  
  
 Zagnieżdżony typ ma dostęp do wszystkich elementów członkowskich, które są dostępne dla jego typu zawierającego. Dostęp można uzyskać prywatnych i chronionych elementów członkowskich typu zawierającego tym dziedziczone chronionych elementów członkowskich.  
  
 W poprzedniej deklaracji, pełna nazwa klasy `Nested` jest `Container.Nested`. Jest to nazwa użyty do utworzenia nowego wystąpienia klasy zagnieżdżone w następujący sposób:  
  
 [!code-csharp[csProgGuideObjects#71](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_4.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Klasy i struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Modyfikatory dostępu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)
