---
title: Zagnieżdżone typy - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/10/2017
helpviewer_keywords:
- nested types [C#]
ms.assetid: f2e1b315-e3d1-48ce-977f-7bae0960ba99
ms.openlocfilehash: 7269f925b3fc78eea04249984697899b1997c3fb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61682302"
---
# <a name="nested-types-c-programming-guide"></a>Zagnieżdżone typy (Przewodnik programowania w języku C#)
Typ zdefiniowany w [klasy](../../../csharp/language-reference/keywords/class.md) lub [struktury](../../../csharp/language-reference/keywords/struct.md) nosi nazwę typu zagnieżdżonego. Na przykład:  
  
 [!code-csharp[csProgGuideObjects#68](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#68)]  
  
Niezależnie od tego, czy zewnętrzny typ jest klasą lub strukturą, zagnieżdżone typy domyślnie [prywatnej](../../../csharp/language-reference/keywords/private.md); są one dostępne tylko z ich typem zawierającym. W poprzednim przykładzie `Nested` klasa jest niedostępna dla typów zewnętrznych. 

Można również określić [modyfikator dostępu](../../language-reference/keywords/access-modifiers.md) do definiowania dostępności typu zagnieżdżonego w następujący sposób:

- Zagnieżdżone typy **klasy** może być [publicznych](../../../csharp/language-reference/keywords/public.md), [chronione](../../../csharp/language-reference/keywords/protected.md), [wewnętrzny](../../../csharp/language-reference/keywords/internal.md), [chronionych wewnętrznych](../../../csharp/language-reference/keywords/protected-internal.md), [prywatnej](../../../csharp/language-reference/keywords/private.md) lub [prywatny chroniony](../../../csharp/language-reference/keywords/private-protected.md). 

   Jednak definiowanie `protected`, `protected internal` lub `private protected` klasy wewnątrz zagnieżdżonej [zapieczętowane klasy](../../language-reference/keywords/sealed.md) generuje ostrzeżenie kompilatora [CS0628](../../misc/cs0628.md), "w klasie zapieczętowanej została zadeklarowana nowa chroniona składowa."
  
- Zagnieżdżone typy **struktury** może być [publicznych](../../../csharp/language-reference/keywords/public.md), [wewnętrzny](../../../csharp/language-reference/keywords/internal.md), lub [prywatnej](../../../csharp/language-reference/keywords/private.md).
  
Poniższy przykład wykonuje `Nested` publiczne klasy:
  
 [!code-csharp[csProgGuideObjects#69](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#69)]  
  
 Typ zagnieżdżony lub wewnętrzny, można uzyskać dostęp do typu zawierającego lub zewnętrznego. Aby uzyskać dostęp zgodny z typem, przekaż go jako argumentu do konstruktora typu zagnieżdżonego. Na przykład:  
  
 [!code-csharp[csProgGuideObjects#70](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#70)]  
  
 Zagnieżdżony typ ma dostęp do wszystkich elementów członkowskich, które są dostępne dla zawierającego ją typu. Będzie miał dostęp do prywatnych i chronionych członków typu zawierającego, włączając wszelkie elementy chronione dziedziczone.  
  
 W poprzedniej deklaracji pełną nazwą klasy `Nested` jest `Container.Nested`. Jest to nazwa, użyty do utworzenia nowego wystąpienia klasy zagnieżdżonej, w następujący sposób:  
  
 [!code-csharp[csProgGuideObjects#71](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#71)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Klasy i struktury](../../../csharp/programming-guide/classes-and-structs/index.md)
- [Modyfikatory dostępu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)
- [Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)
