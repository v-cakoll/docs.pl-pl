---
title: nazwa wyrażenia — odwołanie do języka C#
ms.date: 07/12/2019
f1_keywords:
- nameof_CSharpKeyword
- nameof
helpviewer_keywords:
- nameof expression [C#]
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: 5a68161be7bb03122d2a63ccef4365c5853862b2
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507142"
---
# <a name="nameof-expression-c-reference"></a><span data-ttu-id="2b0c4-102">nazwa wyrażenia (odwołanie do języka C#)</span><span class="sxs-lookup"><span data-stu-id="2b0c4-102">nameof expression (C# reference)</span></span>

<span data-ttu-id="2b0c4-103">Wyrażenie `nameof` tworzy nazwę zmiennej, typu lub elementu członkowskiego jako stałą ciągu:</span><span class="sxs-lookup"><span data-stu-id="2b0c4-103">A `nameof` expression produces the name of a variable, type, or member as the string constant:</span></span>

[!code-csharp-interactive[nameof expression](snippets/NameOfOperator.cs#Examples)]

<span data-ttu-id="2b0c4-104">Jak pokazano w poprzednim przykładzie, w przypadku typu i obszaru nazw powstała nazwa zwykle nie jest [w pełni kwalifikowana.](~/_csharplang/spec/basic-concepts.md#fully-qualified-names)</span><span class="sxs-lookup"><span data-stu-id="2b0c4-104">As the preceding example shows, in the case of a type and a namespace, the produced name is usually not [fully qualified](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span></span>

<span data-ttu-id="2b0c4-105">Wyrażenie `nameof` jest oceniane w czasie kompilacji i nie ma wpływu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="2b0c4-105">A `nameof` expression is evaluated at compile time and has no effect at run time.</span></span>

<span data-ttu-id="2b0c4-106">Można użyć `nameof` wyrażenia, aby kod sprawdzania argumentów był bardziej sprawny:</span><span class="sxs-lookup"><span data-stu-id="2b0c4-106">You can use a `nameof` expression to make the argument-checking code more maintainable:</span></span>

[!code-csharp[nameof and argument check](snippets/NameOfOperator.cs#ExceptionMessage)]

<span data-ttu-id="2b0c4-107">Wyrażenie `nameof` jest dostępne w języku C# 6 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="2b0c4-107">A `nameof` expression is available in C# 6 and later.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="2b0c4-108">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="2b0c4-108">C# language specification</span></span>

<span data-ttu-id="2b0c4-109">Aby uzyskać więcej informacji, zobacz sekcję [Nameof expressions](~/_csharplang/spec/expressions.md#nameof-expressions) [w specyfikacji języka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="2b0c4-109">For more information, see the [Nameof expressions](~/_csharplang/spec/expressions.md#nameof-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2b0c4-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2b0c4-110">See also</span></span>

- [<span data-ttu-id="2b0c4-111">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="2b0c4-111">C# reference</span></span>](../index.md)
- [<span data-ttu-id="2b0c4-112">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="2b0c4-112">C# operators</span></span>](index.md)
