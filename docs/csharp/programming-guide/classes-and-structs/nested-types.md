---
title: Zagnieżdżone typy - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/10/2017
helpviewer_keywords:
- nested types [C#]
ms.assetid: f2e1b315-e3d1-48ce-977f-7bae0960ba99
ms.openlocfilehash: b08a7e95e3ddf7e2392be30f2e69c4ec8f425107
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53244014"
---
# <a name="nested-types-c-programming-guide"></a>Zagnieżdżone typy (Przewodnik programowania w języku C#)
Typ zdefiniowany w [klasy](../../../csharp/language-reference/keywords/class.md) lub [struktury](../../../csharp/language-reference/keywords/struct.md) nosi nazwę typu zagnieżdżonego. Na przykład:  
  
[!code-csharp[csProgGuideObjects#68](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_1.cs)]  
  
Niezależnie od tego, czy zewnętrzny typ jest klasą lub strukturą, zagnieżdżone typy domyślnie [prywatnej](../../../csharp/language-reference/keywords/private.md); są one dostępne tylko z ich typem zawierającym. W poprzednim przykładzie `Nested` klasa jest niedostępna dla typów zewnętrznych. 

Można również określić [modyfikator dostępu](../../language-reference/keywords/access-modifiers.md) do definiowania dostępności typu zagnieżdżonego w następujący sposób:

- Zagnieżdżone typy **klasy** może być [publicznych](../../../csharp/language-reference/keywords/public.md), [chronione](../../../csharp/language-reference/keywords/protected.md), [wewnętrzny](../../../csharp/language-reference/keywords/internal.md), [chronionych wewnętrznych](../../../csharp/language-reference/keywords/protected-internal.md), [prywatnej](../../../csharp/language-reference/keywords/private.md) lub [prywatny chroniony](../../../csharp/language-reference/keywords/private-protected.md). 

   Jednak definiowanie `protected`, `protected internal` lub `private protected` klasy wewnątrz zagnieżdżonej [zapieczętowane klasy](../../language-reference/keywords/sealed.md) generuje ostrzeżenie kompilatora [CS0628](../../misc/cs0628.md), "w klasie zapieczętowanej została zadeklarowana nowa chroniona składowa."
  
- Zagnieżdżone typy **struktury** może być [publicznych](../../../csharp/language-reference/keywords/public.md), [wewnętrzny](../../../csharp/language-reference/keywords/internal.md), lub [prywatnej](../../../csharp/language-reference/keywords/private.md).
  
Poniższy przykład wykonuje `Nested` publiczne klasy:
  
[!code-csharp[csProgGuideObjects#69](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_2.cs)]  
  
 Typ zagnieżdżony lub wewnętrzny, można uzyskać dostęp do typu zawierającego lub zewnętrznego. Aby uzyskać dostęp zgodny z typem, przekaż go jako argumentu do konstruktora typu zagnieżdżonego. Na przykład:  
  
 [!code-csharp[csProgGuideObjects#70](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_3.cs)]  
  
 Zagnieżdżony typ ma dostęp do wszystkich elementów członkowskich, które są dostępne dla zawierającego ją typu. Będzie miał dostęp do prywatnych i chronionych członków typu zawierającego, włączając wszelkie elementy chronione dziedziczone.  
  
 W poprzedniej deklaracji pełną nazwą klasy `Nested` jest `Container.Nested`. Jest to nazwa, użyty do utworzenia nowego wystąpienia klasy zagnieżdżonej, w następujący sposób:  
  
 [!code-csharp[csProgGuideObjects#71](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_4.cs)]  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Klasy i struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [Modyfikatory dostępu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
- [Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)
