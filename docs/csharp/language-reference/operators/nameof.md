---
title: operator nameof — C# odwołanie
ms.date: 07/12/2019
f1_keywords:
- nameof_CSharpKeyword
- nameof
helpviewer_keywords:
- nameof operator [C#]
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: a734cae8fbb944774a4bd1bda9194a548b3d82bc
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239225"
---
# <a name="nameof-operator-c-reference"></a><span data-ttu-id="ae86e-102">nameof — operatorC# (odwołanie)</span><span class="sxs-lookup"><span data-stu-id="ae86e-102">nameof operator (C# reference)</span></span>

<span data-ttu-id="ae86e-103">Operator `nameof` uzyskuje nazwę zmiennej, typu lub składowej jako stałą typu String:</span><span class="sxs-lookup"><span data-stu-id="ae86e-103">The `nameof` operator obtains the name of a variable, type, or member as the string constant:</span></span>

[!code-csharp-interactive[nameof operator](~/samples/snippets/csharp/language-reference/operators/NameOfOperator.cs#Examples)]

<span data-ttu-id="ae86e-104">Jak pokazano w powyższym przykładzie, w przypadku typu i przestrzeni nazw, wygenerowana nazwa zazwyczaj nie jest w [pełni kwalifikowana](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span><span class="sxs-lookup"><span data-stu-id="ae86e-104">As the preceding example shows, in the case of a type and a namespace, the produced name is usually not [fully qualified](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span></span>

<span data-ttu-id="ae86e-105">Operator `nameof` jest oceniany w czasie kompilacji i nie ma wpływu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="ae86e-105">The `nameof` operator is evaluated at compile time and has no effect at run time.</span></span>

<span data-ttu-id="ae86e-106">Możesz użyć operatora `nameof`, aby kod sprawdzania argumentów był bardziej konserwowany:</span><span class="sxs-lookup"><span data-stu-id="ae86e-106">You can use the `nameof` operator to make the argument-checking code more maintainable:</span></span>

[!code-csharp[nameof and argument check](~/samples/snippets/csharp/language-reference/operators/NameOfOperator.cs#ExceptionMessage)]

<span data-ttu-id="ae86e-107">Operator `nameof` jest dostępny w C# 6 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="ae86e-107">The `nameof` operator is available in C# 6 and later.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="ae86e-108">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="ae86e-108">C# language specification</span></span>

<span data-ttu-id="ae86e-109">Aby uzyskać więcej informacji, zobacz sekcję [wyrażenia nameof](~/_csharplang/spec/expressions.md#nameof-expressions) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="ae86e-109">For more information, see the [Nameof expressions](~/_csharplang/spec/expressions.md#nameof-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ae86e-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ae86e-110">See also</span></span>

- [<span data-ttu-id="ae86e-111">C#odwoła</span><span class="sxs-lookup"><span data-stu-id="ae86e-111">C# reference</span></span>](../index.md)
- [<span data-ttu-id="ae86e-112">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="ae86e-112">C# operators</span></span>](index.md)
