---
title: Typy zagnieżdżone — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/10/2017
helpviewer_keywords:
- nested types [C#]
ms.assetid: f2e1b315-e3d1-48ce-977f-7bae0960ba99
ms.openlocfilehash: de2e369702c48047835bc49b98df8f48fbd13480
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596527"
---
# <a name="nested-types-c-programming-guide"></a><span data-ttu-id="d9b0c-102">Zagnieżdżone typy (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="d9b0c-102">Nested Types (C# Programming Guide)</span></span>
<span data-ttu-id="d9b0c-103">Typ zdefiniowany w [klasie](../../language-reference/keywords/class.md) lub [strukturze](../../language-reference/keywords/struct.md) nazywa się typem zagnieżdżonym.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-103">A type defined within a [class](../../language-reference/keywords/class.md) or [struct](../../language-reference/keywords/struct.md) is called a nested type.</span></span> <span data-ttu-id="d9b0c-104">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="d9b0c-104">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#68](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#68)]  
  
<span data-ttu-id="d9b0c-105">Niezależnie od tego, czy typ zewnętrzny jest klasą, czy strukturą, zagnieżdżone typy domyślne to [Private](../../language-reference/keywords/private.md); są one dostępne tylko z tego typu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-105">Regardless of whether the outer type is a class or a struct, nested types default to [private](../../language-reference/keywords/private.md); they are accessible only from their containing type.</span></span> <span data-ttu-id="d9b0c-106">W poprzednim przykładzie `Nested` Klasa jest niedostępna dla typów zewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-106">In the previous example, the `Nested` class is inaccessible to external types.</span></span> 

<span data-ttu-id="d9b0c-107">Można również określić [modyfikator dostępu](../../language-reference/keywords/access-modifiers.md) , aby zdefiniować dostępność typu zagnieżdżonego w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="d9b0c-107">You can also specify an [access modifier](../../language-reference/keywords/access-modifiers.md) to define the accessibility of a nested type, as follows:</span></span>

- <span data-ttu-id="d9b0c-108">Zagnieżdżone typy **klasy** mogą być [publiczne](../../language-reference/keywords/public.md), [chronione](../../language-reference/keywords/protected.md), [wewnętrzne](../../language-reference/keywords/internal.md), [chronione wewnętrznie](../../language-reference/keywords/protected-internal.md), [prywatne](../../language-reference/keywords/private.md) i [prywatne](../../language-reference/keywords/private-protected.md).</span><span class="sxs-lookup"><span data-stu-id="d9b0c-108">Nested types of a **class** can be [public](../../language-reference/keywords/public.md), [protected](../../language-reference/keywords/protected.md), [internal](../../language-reference/keywords/internal.md), [protected internal](../../language-reference/keywords/protected-internal.md), [private](../../language-reference/keywords/private.md) or [private protected](../../language-reference/keywords/private-protected.md).</span></span> 

   <span data-ttu-id="d9b0c-109">`protected`Jednak zdefiniowanie klasy, `protected internal` lub `private protected` Klasa zagnieżdżona wewnątrz [klasy zapieczętowanej](../../language-reference/keywords/sealed.md) generuje ostrzeżenie kompilatora [CS0628](../../misc/cs0628.md), "Nowa chroniona składowa zadeklarowana w klasie zapieczętowanej".</span><span class="sxs-lookup"><span data-stu-id="d9b0c-109">However, defining a `protected`, `protected internal` or `private protected` nested class inside a [sealed class](../../language-reference/keywords/sealed.md) generates compiler warning [CS0628](../../misc/cs0628.md), "new protected member declared in sealed class."</span></span>
  
- <span data-ttu-id="d9b0c-110">Zagnieżdżone typy **struktury** mogą być [publiczne](../../language-reference/keywords/public.md), [wewnętrzne](../../language-reference/keywords/internal.md)lub [prywatne](../../language-reference/keywords/private.md).</span><span class="sxs-lookup"><span data-stu-id="d9b0c-110">Nested types of a **struct** can be [public](../../language-reference/keywords/public.md), [internal](../../language-reference/keywords/internal.md), or [private](../../language-reference/keywords/private.md).</span></span>
  
<span data-ttu-id="d9b0c-111">W poniższym przykładzie Klasa jest `Nested` publiczna:</span><span class="sxs-lookup"><span data-stu-id="d9b0c-111">The following example makes the `Nested` class public:</span></span>
  
 [!code-csharp[csProgGuideObjects#69](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#69)]  
  
 <span data-ttu-id="d9b0c-112">Zagnieżdżony, lub wewnętrzny, typ może uzyskać dostęp do typu zawierającego lub zewnątrz.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-112">The nested, or inner, type can access the containing, or outer, type.</span></span> <span data-ttu-id="d9b0c-113">Aby uzyskać dostęp do typu zawierającego, przekaż go jako argument do konstruktora typu zagnieżdżonego.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-113">To access the containing type, pass it as an argument to the constructor of the nested type.</span></span> <span data-ttu-id="d9b0c-114">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="d9b0c-114">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#70](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#70)]  
  
 <span data-ttu-id="d9b0c-115">Typ zagnieżdżony ma dostęp do wszystkich elementów członkowskich, które są dostępne dla typu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-115">A nested type has access to all of the members that are accessible to its containing type.</span></span> <span data-ttu-id="d9b0c-116">Może uzyskiwać dostęp do prywatnych i chronionych składowych typu zawierającego, w tym wszystkich dziedziczonych chronionych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-116">It can access private and protected members of the containing type, including any inherited protected members.</span></span>  
  
 <span data-ttu-id="d9b0c-117">W poprzedniej deklaracji, pełna nazwa klasy `Nested` to. `Container.Nested`</span><span class="sxs-lookup"><span data-stu-id="d9b0c-117">In the previous declaration, the full name of class `Nested` is `Container.Nested`.</span></span> <span data-ttu-id="d9b0c-118">Jest to nazwa używana do tworzenia nowego wystąpienia klasy zagnieżdżonej w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="d9b0c-118">This is the name used to create a new instance of the nested class, as follows:</span></span>  
  
 [!code-csharp[csProgGuideObjects#71](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#71)]  
  
## <a name="see-also"></a><span data-ttu-id="d9b0c-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d9b0c-119">See also</span></span>

- [<span data-ttu-id="d9b0c-120">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="d9b0c-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="d9b0c-121">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="d9b0c-121">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="d9b0c-122">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="d9b0c-122">Access Modifiers</span></span>](./access-modifiers.md)
- [<span data-ttu-id="d9b0c-123">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="d9b0c-123">Constructors</span></span>](./constructors.md)
