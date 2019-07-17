---
title: operator nameof — C# odwołania
ms.custom: seodec18
ms.date: 07/12/2019
f1_keywords:
- nameof_CSharpKeyword
- nameof
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: 945a8a8ff6d96cb505fa10e85c21a93347661a23
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68238691"
---
# <a name="nameof-operator-c-reference"></a><span data-ttu-id="5d9ef-102">nameof operator (C# odwołania)</span><span class="sxs-lookup"><span data-stu-id="5d9ef-102">nameof operator (C# reference)</span></span>

<span data-ttu-id="5d9ef-103">`nameof` Operator uzyskuje nazwę zmiennej, typu lub składowej jako stała typu string:</span><span class="sxs-lookup"><span data-stu-id="5d9ef-103">The `nameof` operator obtains the name of a variable, type, or member as the string constant:</span></span>

[!code-csharp-interactive[nameof operator](~/samples/csharp/language-reference/operators/NameOfOperator.cs#Examples)]

<span data-ttu-id="5d9ef-104">Zgodnie z poprzednim przykładzie pokazano, w przypadku typu i przestrzeni nazw, nazwę utworzone zazwyczaj nie jest [w pełni kwalifikowana](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span><span class="sxs-lookup"><span data-stu-id="5d9ef-104">As the preceding example shows, in the case of a type and a namespace, the produced name is usually not [fully qualified](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span></span>

<span data-ttu-id="5d9ef-105">`nameof` Operator jest obliczane w czasie kompilacji i nie ma wpływu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="5d9ef-105">The `nameof` operator is evaluated at compile time, and has no effect at run time.</span></span>

<span data-ttu-id="5d9ef-106">Możesz użyć `nameof` operator się będzie łatwiejszy w utrzymaniu kod sprawdzania argumentu:</span><span class="sxs-lookup"><span data-stu-id="5d9ef-106">You can use the `nameof` operator to make the argument-checking code more maintainable:</span></span>

[!code-csharp[nameof and argument check](~/samples/csharp/language-reference/operators/NameOfOperator.cs#ExceptionMessage)]

<span data-ttu-id="5d9ef-107">`nameof` Operator jest dostępna w C# 6 i nowsze.</span><span class="sxs-lookup"><span data-stu-id="5d9ef-107">The `nameof` operator is available in C# 6 and later.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="5d9ef-108">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="5d9ef-108">C# language specification</span></span>

<span data-ttu-id="5d9ef-109">Aby uzyskać więcej informacji, zobacz [wyrażeń Nameof](~/_csharplang/spec/expressions.md#nameof-expressions) części [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="5d9ef-109">For more information, see the [Nameof expressions](~/_csharplang/spec/expressions.md#nameof-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5d9ef-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5d9ef-110">See also</span></span>

- [<span data-ttu-id="5d9ef-111">C#Odwołanie</span><span class="sxs-lookup"><span data-stu-id="5d9ef-111">C# reference</span></span>](../index.md)
- [<span data-ttu-id="5d9ef-112">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="5d9ef-112">C# operators</span></span>](index.md)
