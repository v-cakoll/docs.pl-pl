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
# <a name="nested-types-c-programming-guide"></a><span data-ttu-id="76e52-102">Zagnieżdżone typy (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="76e52-102">Nested Types (C# Programming Guide)</span></span>

<span data-ttu-id="76e52-103">Typ zdefiniowany w [klasie,](../../language-reference/keywords/class.md) [strukturze](../../language-reference/builtin-types/struct.md)lub [interfejsie](../../language-reference/keywords/interface.md) jest nazywany typem zagnieżdżonym.</span><span class="sxs-lookup"><span data-stu-id="76e52-103">A type defined within a [class](../../language-reference/keywords/class.md), [struct](../../language-reference/builtin-types/struct.md), or [interface](../../language-reference/keywords/interface.md) is called a nested type.</span></span> <span data-ttu-id="76e52-104">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="76e52-104">For example</span></span>

[!code-csharp[DeclareNestedClass](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#DeclareNestedClass)]

<span data-ttu-id="76e52-105">Niezależnie od tego, czy typ zewnętrzny jest klasą, interfejsem czy strukturą, typy zagnieżdżone domyślnie [są prywatne;](../../language-reference/keywords/private.md) są one dostępne tylko z ich typu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="76e52-105">Regardless of whether the outer type is a class, interface, or struct, nested types default to [private](../../language-reference/keywords/private.md); they are accessible only from their containing type.</span></span> <span data-ttu-id="76e52-106">W poprzednim przykładzie `Nested` klasa jest niedostępna dla typów zewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="76e52-106">In the previous example, the `Nested` class is inaccessible to external types.</span></span>

<span data-ttu-id="76e52-107">Można również określić [modyfikator dostępu,](../../language-reference/keywords/access-modifiers.md) aby zdefiniować dostępność typu zagnieżdżonego w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="76e52-107">You can also specify an [access modifier](../../language-reference/keywords/access-modifiers.md) to define the accessibility of a nested type, as follows:</span></span>

- <span data-ttu-id="76e52-108">Zagnieżdżone typy **klasy** mogą być [chronione publicznie,](../../language-reference/keywords/public.md) [chronione,](../../language-reference/keywords/protected.md) [wewnętrzne,](../../language-reference/keywords/internal.md) [chronione wewnętrzne,](../../language-reference/keywords/protected-internal.md) [prywatne](../../language-reference/keywords/private.md) lub [prywatne chronione.](../../language-reference/keywords/private-protected.md)</span><span class="sxs-lookup"><span data-stu-id="76e52-108">Nested types of a **class** can be [public](../../language-reference/keywords/public.md), [protected](../../language-reference/keywords/protected.md), [internal](../../language-reference/keywords/internal.md), [protected internal](../../language-reference/keywords/protected-internal.md), [private](../../language-reference/keywords/private.md) or [private protected](../../language-reference/keywords/private-protected.md).</span></span>

   <span data-ttu-id="76e52-109">`protected`Jednak zdefiniowanie `protected internal` `private protected` klasy lub zagnieżdżonej wewnątrz [zapieczętowanej klasy](../../language-reference/keywords/sealed.md) generuje ostrzeżenie kompilatora [CS0628](../../misc/cs0628.md), "nowy chroniony element członkowski zadeklarowany w klasie zapieczętowanej"</span><span class="sxs-lookup"><span data-stu-id="76e52-109">However, defining a `protected`, `protected internal` or `private protected` nested class inside a [sealed class](../../language-reference/keywords/sealed.md) generates compiler warning [CS0628](../../misc/cs0628.md), "new protected member declared in sealed class."</span></span>
  
- <span data-ttu-id="76e52-110">Zagnieżdżone typy **struktury** mogą być [publiczne,](../../language-reference/keywords/public.md) [wewnętrzne](../../language-reference/keywords/internal.md)lub [prywatne.](../../language-reference/keywords/private.md)</span><span class="sxs-lookup"><span data-stu-id="76e52-110">Nested types of a **struct** can be [public](../../language-reference/keywords/public.md), [internal](../../language-reference/keywords/internal.md), or [private](../../language-reference/keywords/private.md).</span></span>

<span data-ttu-id="76e52-111">Poniższy przykład upublicznia `Nested` klasę:</span><span class="sxs-lookup"><span data-stu-id="76e52-111">The following example makes the `Nested` class public:</span></span>

[!code-csharp[PublicNestedClass](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#PublicNestedClass)]

<span data-ttu-id="76e52-112">Zagnieżdżony lub wewnętrzny typ może uzyskać dostęp do typu zawierającego lub zewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="76e52-112">The nested, or inner, type can access the containing, or outer, type.</span></span> <span data-ttu-id="76e52-113">Aby uzyskać dostęp do typu zawierającego, przekazać go jako argument do konstruktora typu zagnieżdżonego.</span><span class="sxs-lookup"><span data-stu-id="76e52-113">To access the containing type, pass it as an argument to the constructor of the nested type.</span></span> <span data-ttu-id="76e52-114">Przykład:</span><span class="sxs-lookup"><span data-stu-id="76e52-114">For example:</span></span>

[!code-csharp[DeclareNestedInstance](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#DeclareNestedInstance)]

<span data-ttu-id="76e52-115">Typ zagnieżdżony ma dostęp do wszystkich elementów członkowskich, które są dostępne dla jego typu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="76e52-115">A nested type has access to all of the members that are accessible to its containing type.</span></span> <span data-ttu-id="76e52-116">Może uzyskać dostęp do prywatnych i chronionych elementów członkowskich typu zawierającego, w tym wszelkich dziedziczonych chronionych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="76e52-116">It can access private and protected members of the containing type, including any inherited protected members.</span></span>

<span data-ttu-id="76e52-117">W poprzedniej deklaracji pełna nazwa `Nested` `Container.Nested`klasy to .</span><span class="sxs-lookup"><span data-stu-id="76e52-117">In the previous declaration, the full name of class `Nested` is `Container.Nested`.</span></span> <span data-ttu-id="76e52-118">Jest to nazwa używana do tworzenia nowego wystąpienia klasy zagnieżdżonej w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="76e52-118">This is the name used to create a new instance of the nested class, as follows:</span></span>

[!code-csharp[UseNestedInstance](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#UseNestedInstance)]

## <a name="see-also"></a><span data-ttu-id="76e52-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="76e52-119">See also</span></span>

- [<span data-ttu-id="76e52-120">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="76e52-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="76e52-121">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="76e52-121">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="76e52-122">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="76e52-122">Access Modifiers</span></span>](./access-modifiers.md)
- [<span data-ttu-id="76e52-123">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="76e52-123">Constructors</span></span>](./constructors.md)
