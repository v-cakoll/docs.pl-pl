---
title: Typy zagnieżdżone — Przewodnik programowania w języku C#
description: Typ zdefiniowany w klasie, strukturze lub interfejsie jest nazywany typem zagnieżdżonym w języku C#.
ms.date: 02/08/2020
helpviewer_keywords:
- nested types [C#]
ms.assetid: f2e1b315-e3d1-48ce-977f-7bae0960ba99
ms.openlocfilehash: 9e1c6c1e8b22b5447d43915ab02984aa13146301
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864946"
---
# <a name="nested-types-c-programming-guide"></a><span data-ttu-id="7fb2b-103">Zagnieżdżone typy (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="7fb2b-103">Nested Types (C# Programming Guide)</span></span>

<span data-ttu-id="7fb2b-104">Typ zdefiniowany w [klasie](../../language-reference/keywords/class.md), [strukturze](../../language-reference/builtin-types/struct.md)lub [interfejsie](../../language-reference/keywords/interface.md) nazywa się typem zagnieżdżonym.</span><span class="sxs-lookup"><span data-stu-id="7fb2b-104">A type defined within a [class](../../language-reference/keywords/class.md), [struct](../../language-reference/builtin-types/struct.md), or [interface](../../language-reference/keywords/interface.md) is called a nested type.</span></span> <span data-ttu-id="7fb2b-105">Na przykład</span><span class="sxs-lookup"><span data-stu-id="7fb2b-105">For example</span></span>

[!code-csharp[DeclareNestedClass](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#DeclareNestedClass)]

<span data-ttu-id="7fb2b-106">Niezależnie od tego, czy typ zewnętrzny jest klasą, interfejsem lub strukturą, zagnieżdżone typy domyślne to [Private](../../language-reference/keywords/private.md); są one dostępne tylko z tego typu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="7fb2b-106">Regardless of whether the outer type is a class, interface, or struct, nested types default to [private](../../language-reference/keywords/private.md); they are accessible only from their containing type.</span></span> <span data-ttu-id="7fb2b-107">W poprzednim przykładzie `Nested` Klasa jest niedostępna dla typów zewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="7fb2b-107">In the previous example, the `Nested` class is inaccessible to external types.</span></span>

<span data-ttu-id="7fb2b-108">Można również określić [modyfikator dostępu](../../language-reference/keywords/access-modifiers.md) , aby zdefiniować dostępność typu zagnieżdżonego w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7fb2b-108">You can also specify an [access modifier](../../language-reference/keywords/access-modifiers.md) to define the accessibility of a nested type, as follows:</span></span>

- <span data-ttu-id="7fb2b-109">Zagnieżdżone typy **klasy** mogą być [publiczne](../../language-reference/keywords/public.md), [chronione](../../language-reference/keywords/protected.md), [wewnętrzne](../../language-reference/keywords/internal.md), [chronione wewnętrznie](../../language-reference/keywords/protected-internal.md), [prywatne](../../language-reference/keywords/private.md) i [prywatne](../../language-reference/keywords/private-protected.md).</span><span class="sxs-lookup"><span data-stu-id="7fb2b-109">Nested types of a **class** can be [public](../../language-reference/keywords/public.md), [protected](../../language-reference/keywords/protected.md), [internal](../../language-reference/keywords/internal.md), [protected internal](../../language-reference/keywords/protected-internal.md), [private](../../language-reference/keywords/private.md) or [private protected](../../language-reference/keywords/private-protected.md).</span></span>

   <span data-ttu-id="7fb2b-110">Jednak zdefiniowanie `protected` klasy, `protected internal` lub `private protected` Klasa zagnieżdżona wewnątrz [klasy zapieczętowanej](../../language-reference/keywords/sealed.md) generuje ostrzeżenie kompilatora [CS0628](../../misc/cs0628.md), "Nowa chroniona składowa zadeklarowana w klasie zapieczętowanej".</span><span class="sxs-lookup"><span data-stu-id="7fb2b-110">However, defining a `protected`, `protected internal` or `private protected` nested class inside a [sealed class](../../language-reference/keywords/sealed.md) generates compiler warning [CS0628](../../misc/cs0628.md), "new protected member declared in sealed class."</span></span>
  
- <span data-ttu-id="7fb2b-111">Zagnieżdżone typy **struktury** mogą być [publiczne](../../language-reference/keywords/public.md), [wewnętrzne](../../language-reference/keywords/internal.md)lub [prywatne](../../language-reference/keywords/private.md).</span><span class="sxs-lookup"><span data-stu-id="7fb2b-111">Nested types of a **struct** can be [public](../../language-reference/keywords/public.md), [internal](../../language-reference/keywords/internal.md), or [private](../../language-reference/keywords/private.md).</span></span>

<span data-ttu-id="7fb2b-112">W poniższym przykładzie Klasa jest `Nested` publiczna:</span><span class="sxs-lookup"><span data-stu-id="7fb2b-112">The following example makes the `Nested` class public:</span></span>

[!code-csharp[PublicNestedClass](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#PublicNestedClass)]

<span data-ttu-id="7fb2b-113">Zagnieżdżony, lub wewnętrzny, typ może uzyskać dostęp do typu zawierającego lub zewnątrz.</span><span class="sxs-lookup"><span data-stu-id="7fb2b-113">The nested, or inner, type can access the containing, or outer, type.</span></span> <span data-ttu-id="7fb2b-114">Aby uzyskać dostęp do typu zawierającego, przekaż go jako argument do konstruktora typu zagnieżdżonego.</span><span class="sxs-lookup"><span data-stu-id="7fb2b-114">To access the containing type, pass it as an argument to the constructor of the nested type.</span></span> <span data-ttu-id="7fb2b-115">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="7fb2b-115">For example:</span></span>

[!code-csharp[DeclareNestedInstance](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#DeclareNestedInstance)]

<span data-ttu-id="7fb2b-116">Typ zagnieżdżony ma dostęp do wszystkich elementów członkowskich, które są dostępne dla typu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="7fb2b-116">A nested type has access to all of the members that are accessible to its containing type.</span></span> <span data-ttu-id="7fb2b-117">Może uzyskiwać dostęp do prywatnych i chronionych składowych typu zawierającego, w tym wszystkich dziedziczonych chronionych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="7fb2b-117">It can access private and protected members of the containing type, including any inherited protected members.</span></span>

<span data-ttu-id="7fb2b-118">W poprzedniej deklaracji, pełna nazwa klasy `Nested` to `Container.Nested` .</span><span class="sxs-lookup"><span data-stu-id="7fb2b-118">In the previous declaration, the full name of class `Nested` is `Container.Nested`.</span></span> <span data-ttu-id="7fb2b-119">Jest to nazwa używana do tworzenia nowego wystąpienia klasy zagnieżdżonej w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7fb2b-119">This is the name used to create a new instance of the nested class, as follows:</span></span>

[!code-csharp[UseNestedInstance](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#UseNestedInstance)]

## <a name="see-also"></a><span data-ttu-id="7fb2b-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7fb2b-120">See also</span></span>

- [<span data-ttu-id="7fb2b-121">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="7fb2b-121">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="7fb2b-122">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="7fb2b-122">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="7fb2b-123">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="7fb2b-123">Access Modifiers</span></span>](./access-modifiers.md)
- [<span data-ttu-id="7fb2b-124">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="7fb2b-124">Constructors</span></span>](./constructors.md)
