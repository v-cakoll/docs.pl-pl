---
title: operator nameof — C# odwołanie
ms.custom: seodec18
ms.date: 07/12/2019
f1_keywords:
- nameof_CSharpKeyword
- nameof
helpviewer_keywords:
- nameof operator [C#]
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: 965b3e96a20906187df4c8693f050c550a747091
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/19/2019
ms.locfileid: "68331440"
---
# <a name="nameof-operator-c-reference"></a><span data-ttu-id="d0094-102">nameof — operatorC# (odwołanie)</span><span class="sxs-lookup"><span data-stu-id="d0094-102">nameof operator (C# reference)</span></span>

<span data-ttu-id="d0094-103">`nameof` Operator uzyskuje nazwę zmiennej, typu lub składowej jako stałą typu String:</span><span class="sxs-lookup"><span data-stu-id="d0094-103">The `nameof` operator obtains the name of a variable, type, or member as the string constant:</span></span>

[!code-csharp-interactive[nameof operator](~/samples/csharp/language-reference/operators/NameOfOperator.cs#Examples)]

<span data-ttu-id="d0094-104">Jak pokazano w powyższym przykładzie, w przypadku typu i przestrzeni nazw, wygenerowana nazwa zazwyczaj nie jest w [pełni kwalifikowana](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span><span class="sxs-lookup"><span data-stu-id="d0094-104">As the preceding example shows, in the case of a type and a namespace, the produced name is usually not [fully qualified](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span></span>

<span data-ttu-id="d0094-105">`nameof` Operator jest oceniany w czasie kompilacji i nie ma wpływu na czas wykonywania.</span><span class="sxs-lookup"><span data-stu-id="d0094-105">The `nameof` operator is evaluated at compile time, and has no effect at run time.</span></span>

<span data-ttu-id="d0094-106">Możesz użyć `nameof` operatora, aby kod sprawdzania argumentów był bardziej konserwowany:</span><span class="sxs-lookup"><span data-stu-id="d0094-106">You can use the `nameof` operator to make the argument-checking code more maintainable:</span></span>

[!code-csharp[nameof and argument check](~/samples/csharp/language-reference/operators/NameOfOperator.cs#ExceptionMessage)]

<span data-ttu-id="d0094-107">Operator jest dostępny w C# 6 i nowszych. `nameof`</span><span class="sxs-lookup"><span data-stu-id="d0094-107">The `nameof` operator is available in C# 6 and later.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="d0094-108">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="d0094-108">C# language specification</span></span>

<span data-ttu-id="d0094-109">Aby uzyskać więcej informacji, zobacz sekcję [wyrażenia nameof](~/_csharplang/spec/expressions.md#nameof-expressions) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="d0094-109">For more information, see the [Nameof expressions](~/_csharplang/spec/expressions.md#nameof-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d0094-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d0094-110">See also</span></span>

- [<span data-ttu-id="d0094-111">C#odwoła</span><span class="sxs-lookup"><span data-stu-id="d0094-111">C# reference</span></span>](../index.md)
- [<span data-ttu-id="d0094-112">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="d0094-112">C# operators</span></span>](index.md)
