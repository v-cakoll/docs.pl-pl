---
title: prywatne słowo kluczowe - Odwołanie do języka C#
ms.date: 07/20/2015
f1_keywords:
- private_CSharpKeyword
- private
helpviewer_keywords:
- private keyword [C#]
ms.assetid: 654c0bb8-e6ac-4086-bf96-7474fa6aa1c8
ms.openlocfilehash: a13e9ef18b0f6452c3ff1497dc97110bc21c433d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715200"
---
# <a name="private-c-reference"></a><span data-ttu-id="6dbfc-102">private (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="6dbfc-102">private (C# Reference)</span></span>

<span data-ttu-id="6dbfc-103">Słowo `private` kluczowe jest modyfikatorem dostępu do elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="6dbfc-103">The `private` keyword is a member access modifier.</span></span>

> <span data-ttu-id="6dbfc-104">Ta strona `private` obejmuje dostęp.</span><span class="sxs-lookup"><span data-stu-id="6dbfc-104">This page covers `private` access.</span></span> <span data-ttu-id="6dbfc-105">Słowo `private` kluczowe jest również [`private protected`](./private-protected.md) częścią modyfikatora dostępu.</span><span class="sxs-lookup"><span data-stu-id="6dbfc-105">The `private` keyword is also part of the [`private protected`](./private-protected.md) access modifier.</span></span>

<span data-ttu-id="6dbfc-106">Dostęp prywatny jest najmniej liberalnym poziomem dostępu.</span><span class="sxs-lookup"><span data-stu-id="6dbfc-106">Private access is the least permissive access level.</span></span> <span data-ttu-id="6dbfc-107">Elementy członkowskie prywatne są dostępne tylko w treści klasy lub struktury, w której są zadeklarowane, jak w tym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="6dbfc-107">Private members are accessible only within the body of the class or the struct in which they are declared, as in this example:</span></span>

```csharp
class Employee
{
    private int i;
    double d;   // private access by default
}
```

<span data-ttu-id="6dbfc-108">Zagnieżdżone typy w tym samym treści można również uzyskać dostęp do tych prywatnych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="6dbfc-108">Nested types in the same body can also access those private members.</span></span>

<span data-ttu-id="6dbfc-109">Jest to błąd w czasie kompilacji, aby odwołać się do prywatnego elementu członkowskiego poza klasą lub struktury, w którym jest zadeklarowany.</span><span class="sxs-lookup"><span data-stu-id="6dbfc-109">It is a compile-time error to reference a private member outside the class or the struct in which it is declared.</span></span>

<span data-ttu-id="6dbfc-110">Aby porównać `private` z innymi modyfikatorami dostępu, zobacz [Poziomy ułatwień dostępu](accessibility-levels.md) i [modyfikatory dostępu](../../programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="6dbfc-110">For a comparison of `private` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md) and [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md).</span></span>

## <a name="example"></a><span data-ttu-id="6dbfc-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="6dbfc-111">Example</span></span>

<span data-ttu-id="6dbfc-112">W tym przykładzie `Employee` klasa zawiera dwa `name` prywatne `salary`elementy członkowskie danych i .</span><span class="sxs-lookup"><span data-stu-id="6dbfc-112">In this example, the `Employee` class contains two private data members, `name` and `salary`.</span></span> <span data-ttu-id="6dbfc-113">Jako członkowie prywatni nie można uzyskać dostępu z wyjątkiem metod członkowskich.</span><span class="sxs-lookup"><span data-stu-id="6dbfc-113">As private members, they cannot be accessed except by member methods.</span></span> <span data-ttu-id="6dbfc-114">Metody publiczne `GetName` o `Salary` nazwie i są dodawane w celu umożliwienia kontrolowanego dostępu do prywatnych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="6dbfc-114">Public methods named `GetName` and `Salary` are added to allow controlled access to the private members.</span></span> <span data-ttu-id="6dbfc-115">Element `name` członkowski jest dostępny za pomocą `salary` metody publicznej, a element członkowski jest dostępny za pomocą publicznej właściwości tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="6dbfc-115">The `name` member is accessed by way of a public method, and the `salary` member is accessed by way of a public read-only property.</span></span> <span data-ttu-id="6dbfc-116">(Zobacz [właściwości,](../../programming-guide/classes-and-structs/properties.md) aby uzyskać więcej informacji.)</span><span class="sxs-lookup"><span data-stu-id="6dbfc-116">(See [Properties](../../programming-guide/classes-and-structs/properties.md) for more information.)</span></span>

[!code-csharp[csrefKeywordsModifiers#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#10)]

## <a name="c-language-specification"></a><span data-ttu-id="6dbfc-117">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="6dbfc-117">C# language specification</span></span>  

<span data-ttu-id="6dbfc-118">Aby uzyskać więcej informacji, zobacz [Zadeklarowana dostępność](~/_csharplang/spec/basic-concepts.md#declared-accessibility) w [specyfikacji języka Języka C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="6dbfc-118">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="6dbfc-119">Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="6dbfc-119">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="6dbfc-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6dbfc-120">See also</span></span>

- [<span data-ttu-id="6dbfc-121">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="6dbfc-121">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6dbfc-122">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="6dbfc-122">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="6dbfc-123">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="6dbfc-123">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="6dbfc-124">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="6dbfc-124">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="6dbfc-125">Poziomy ułatwień dostępu</span><span class="sxs-lookup"><span data-stu-id="6dbfc-125">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="6dbfc-126">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="6dbfc-126">Modifiers</span></span>](index.md)
- [<span data-ttu-id="6dbfc-127">Publicznego</span><span class="sxs-lookup"><span data-stu-id="6dbfc-127">public</span></span>](public.md)
- [<span data-ttu-id="6dbfc-128">protected</span><span class="sxs-lookup"><span data-stu-id="6dbfc-128">protected</span></span>](protected.md)
- [<span data-ttu-id="6dbfc-129">Wewnętrznego</span><span class="sxs-lookup"><span data-stu-id="6dbfc-129">internal</span></span>](internal.md)
