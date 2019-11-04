---
title: Private — słowo C# kluczowe — odwołanie
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- private_CSharpKeyword
- private
helpviewer_keywords:
- private keyword [C#]
ms.assetid: 654c0bb8-e6ac-4086-bf96-7474fa6aa1c8
ms.openlocfilehash: 19e2925cd65cc9c68ff50d370398a4f401275940
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422591"
---
# <a name="private-c-reference"></a><span data-ttu-id="c0fd4-102">private (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="c0fd4-102">private (C# Reference)</span></span>

<span data-ttu-id="c0fd4-103">Słowo kluczowe `private` jest modyfikatorem dostępu składowej.</span><span class="sxs-lookup"><span data-stu-id="c0fd4-103">The `private` keyword is a member access modifier.</span></span>

> <span data-ttu-id="c0fd4-104">Ta strona obejmuje `private` dostępu.</span><span class="sxs-lookup"><span data-stu-id="c0fd4-104">This page covers `private` access.</span></span> <span data-ttu-id="c0fd4-105">Słowo kluczowe `private` jest również częścią modyfikatora dostępu [`private protected`](./private-protected.md) .</span><span class="sxs-lookup"><span data-stu-id="c0fd4-105">The `private` keyword is also part of the [`private protected`](./private-protected.md) access modifier.</span></span>

<span data-ttu-id="c0fd4-106">Dostęp prywatny to najmniejszy poziom dostępu.</span><span class="sxs-lookup"><span data-stu-id="c0fd4-106">Private access is the least permissive access level.</span></span> <span data-ttu-id="c0fd4-107">Prywatne elementy członkowskie są dostępne tylko w treści klasy lub struktury, w której są zadeklarowane, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="c0fd4-107">Private members are accessible only within the body of the class or the struct in which they are declared, as in this example:</span></span>

```csharp
class Employee
{
    private int i;
    double d;   // private access by default
}
```

<span data-ttu-id="c0fd4-108">Typy zagnieżdżone w tej samej treści mogą również uzyskiwać dostęp do tych prywatnych członków.</span><span class="sxs-lookup"><span data-stu-id="c0fd4-108">Nested types in the same body can also access those private members.</span></span>

<span data-ttu-id="c0fd4-109">Jest to błąd czasu kompilacji, który odwołuje się do prywatnego elementu członkowskiego spoza klasy lub struktury, w której jest zadeklarowany.</span><span class="sxs-lookup"><span data-stu-id="c0fd4-109">It is a compile-time error to reference a private member outside the class or the struct in which it is declared.</span></span>

<span data-ttu-id="c0fd4-110">Aby uzyskać porównanie `private` z innymi modyfikatorami dostępu, zobacz [poziomy ułatwień](accessibility-levels.md) dostępu i [Modyfikatory dostęp](../../programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="c0fd4-110">For a comparison of `private` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md) and [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md).</span></span>

## <a name="example"></a><span data-ttu-id="c0fd4-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="c0fd4-111">Example</span></span>

<span data-ttu-id="c0fd4-112">W tym przykładzie Klasa `Employee` zawiera dwa prywatne elementy członkowskie danych, `name` i `salary`.</span><span class="sxs-lookup"><span data-stu-id="c0fd4-112">In this example, the `Employee` class contains two private data members, `name` and `salary`.</span></span> <span data-ttu-id="c0fd4-113">Jako prywatne elementy członkowskie nie są dostępne z wyjątkiem metod składowych.</span><span class="sxs-lookup"><span data-stu-id="c0fd4-113">As private members, they cannot be accessed except by member methods.</span></span> <span data-ttu-id="c0fd4-114">Metody publiczne o nazwie `GetName` i `Salary` są dodawane w celu umożliwienia kontrolowanego dostępu do prywatnych członków.</span><span class="sxs-lookup"><span data-stu-id="c0fd4-114">Public methods named `GetName` and `Salary` are added to allow controlled access to the private members.</span></span> <span data-ttu-id="c0fd4-115">Członek `name` jest dostępny w postaci metody publicznej, a członek `salary` jest dostępny w postaci publicznej właściwości tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="c0fd4-115">The `name` member is accessed by way of a public method, and the `salary` member is accessed by way of a public read-only property.</span></span> <span data-ttu-id="c0fd4-116">(Zobacz [Właściwości](../../programming-guide/classes-and-structs/properties.md) , aby uzyskać więcej informacji).</span><span class="sxs-lookup"><span data-stu-id="c0fd4-116">(See [Properties](../../programming-guide/classes-and-structs/properties.md) for more information.)</span></span>

[!code-csharp[csrefKeywordsModifiers#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#10)]

## <a name="c-language-specification"></a><span data-ttu-id="c0fd4-117">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="c0fd4-117">C# language specification</span></span>  

<span data-ttu-id="c0fd4-118">Aby uzyskać więcej informacji, zobacz [zadeklarowane ułatwienia dostępu](~/_csharplang/spec/basic-concepts.md#declared-accessibility) w [ C# specyfikacji języka](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="c0fd4-118">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="c0fd4-119">Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="c0fd4-119">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="c0fd4-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c0fd4-120">See also</span></span>

- [<span data-ttu-id="c0fd4-121">C#Odwoła</span><span class="sxs-lookup"><span data-stu-id="c0fd4-121">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c0fd4-122">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="c0fd4-122">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c0fd4-123">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="c0fd4-123">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="c0fd4-124">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="c0fd4-124">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="c0fd4-125">Poziomy ułatwień dostępu</span><span class="sxs-lookup"><span data-stu-id="c0fd4-125">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="c0fd4-126">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="c0fd4-126">Modifiers</span></span>](index.md)
- [<span data-ttu-id="c0fd4-127">public</span><span class="sxs-lookup"><span data-stu-id="c0fd4-127">public</span></span>](public.md)
- [<span data-ttu-id="c0fd4-128">protected</span><span class="sxs-lookup"><span data-stu-id="c0fd4-128">protected</span></span>](protected.md)
- [<span data-ttu-id="c0fd4-129">internal</span><span class="sxs-lookup"><span data-stu-id="c0fd4-129">internal</span></span>](internal.md)
