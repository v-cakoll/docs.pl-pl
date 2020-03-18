---
title: Typy zagnieżdżone — przewodnik programowania C#
ms.date: 02/08/2020
helpviewer_keywords:
- nested types [C#]
ms.assetid: f2e1b315-e3d1-48ce-977f-7bae0960ba99
ms.openlocfilehash: 12e44ccc1254424c152a238c8390f133550fa54c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77626493"
---
# <a name="nested-types-c-programming-guide"></a>Zagnieżdżone typy (Przewodnik programowania w języku C#)

Typ zdefiniowany w [klasie,](../../language-reference/keywords/class.md) [strukturze](../../language-reference/builtin-types/struct.md)lub [interfejsie](../../language-reference/keywords/interface.md) jest nazywany typem zagnieżdżonym. Na przykład:

[!code-csharp[DeclareNestedClass](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#DeclareNestedClass)]

Niezależnie od tego, czy typ zewnętrzny jest klasą, interfejsem czy strukturą, typy zagnieżdżone domyślnie [są prywatne;](../../language-reference/keywords/private.md) są one dostępne tylko z ich typu zawierającego. W poprzednim przykładzie `Nested` klasa jest niedostępna dla typów zewnętrznych.

Można również określić [modyfikator dostępu,](../../language-reference/keywords/access-modifiers.md) aby zdefiniować dostępność typu zagnieżdżonego w następujący sposób:

- Zagnieżdżone typy **klasy** mogą być [chronione publicznie,](../../language-reference/keywords/public.md) [chronione,](../../language-reference/keywords/protected.md) [wewnętrzne,](../../language-reference/keywords/internal.md) [chronione wewnętrzne,](../../language-reference/keywords/protected-internal.md) [prywatne](../../language-reference/keywords/private.md) lub [prywatne chronione.](../../language-reference/keywords/private-protected.md)

   `protected`Jednak zdefiniowanie `protected internal` `private protected` klasy lub zagnieżdżonej wewnątrz [zapieczętowanej klasy](../../language-reference/keywords/sealed.md) generuje ostrzeżenie kompilatora [CS0628](../../misc/cs0628.md), "nowy chroniony element członkowski zadeklarowany w klasie zapieczętowanej"
  
- Zagnieżdżone typy **struktury** mogą być [publiczne,](../../language-reference/keywords/public.md) [wewnętrzne](../../language-reference/keywords/internal.md)lub [prywatne.](../../language-reference/keywords/private.md)

Poniższy przykład upublicznia `Nested` klasę:

[!code-csharp[PublicNestedClass](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#PublicNestedClass)]

Zagnieżdżony lub wewnętrzny typ może uzyskać dostęp do typu zawierającego lub zewnętrznego. Aby uzyskać dostęp do typu zawierającego, przekazać go jako argument do konstruktora typu zagnieżdżonego. Przykład:

[!code-csharp[DeclareNestedInstance](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#DeclareNestedInstance)]

Typ zagnieżdżony ma dostęp do wszystkich elementów członkowskich, które są dostępne dla jego typu zawierającego. Może uzyskać dostęp do prywatnych i chronionych elementów członkowskich typu zawierającego, w tym wszelkich dziedziczonych chronionych elementów członkowskich.

W poprzedniej deklaracji pełna nazwa `Nested` `Container.Nested`klasy to . Jest to nazwa używana do tworzenia nowego wystąpienia klasy zagnieżdżonej w następujący sposób:

[!code-csharp[UseNestedInstance](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#UseNestedInstance)]

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Klasy i struktury](./index.md)
- [Modyfikatory dostępu](./access-modifiers.md)
- [Konstruktory](./constructors.md)
