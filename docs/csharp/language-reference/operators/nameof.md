---
title: wyrażenie nameof — odwołanie w C#
ms.date: 04/23/2020
f1_keywords:
- nameof_CSharpKeyword
- nameof
helpviewer_keywords:
- nameof expression [C#]
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: d71acf0cf7d5cdcfa5310455af2120fa1f82d567
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135922"
---
# <a name="nameof-expression-c-reference"></a><span data-ttu-id="e154f-102">wyrażenie nameof (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="e154f-102">nameof expression (C# reference)</span></span>

<span data-ttu-id="e154f-103">`nameof` Wyrażenie tworzy nazwę zmiennej, typu lub składowej jako stałą typu String:</span><span class="sxs-lookup"><span data-stu-id="e154f-103">A `nameof` expression produces the name of a variable, type, or member as the string constant:</span></span>

[!code-csharp-interactive[nameof expression](snippets/NameOfOperator.cs#Examples)]

<span data-ttu-id="e154f-104">Jak pokazano w powyższym przykładzie, w przypadku typu i przestrzeni nazw, wygenerowana nazwa zazwyczaj nie jest w [pełni kwalifikowana](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span><span class="sxs-lookup"><span data-stu-id="e154f-104">As the preceding example shows, in the case of a type and a namespace, the produced name is usually not [fully qualified](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span></span>

<span data-ttu-id="e154f-105">W przypadku [identyfikatorów Verbatim](../tokens/verbatim.md) `@` znak nie jest częścią nazwy, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="e154f-105">In the case of [verbatim identifiers](../tokens/verbatim.md), the `@` character is not the part of a name, as the following example shows:</span></span>

[!code-csharp-interactive[nameof verbatim](snippets/NameOfOperator.cs#Verbatim)]

<span data-ttu-id="e154f-106">`nameof` Wyrażenie jest oceniane w czasie kompilacji i nie ma wpływu na czas wykonywania.</span><span class="sxs-lookup"><span data-stu-id="e154f-106">A `nameof` expression is evaluated at compile time and has no effect at run time.</span></span>

<span data-ttu-id="e154f-107">Możesz użyć `nameof` wyrażenia, aby zwiększyć łatwość obsługi kodu sprawdzania argumentów:</span><span class="sxs-lookup"><span data-stu-id="e154f-107">You can use a `nameof` expression to make the argument-checking code more maintainable:</span></span>

[!code-csharp[nameof and argument check](snippets/NameOfOperator.cs#ExceptionMessage)]

<span data-ttu-id="e154f-108">`nameof` Wyrażenie jest dostępne w języku C# 6 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="e154f-108">A `nameof` expression is available in C# 6 and later.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e154f-109">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="e154f-109">C# language specification</span></span>

<span data-ttu-id="e154f-110">Aby uzyskać więcej informacji, zobacz sekcję [wyrażenia nameof](~/_csharplang/spec/expressions.md#nameof-expressions) w [specyfikacji języka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="e154f-110">For more information, see the [Nameof expressions](~/_csharplang/spec/expressions.md#nameof-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e154f-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e154f-111">See also</span></span>

- [<span data-ttu-id="e154f-112">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="e154f-112">C# reference</span></span>](../index.md)
- [<span data-ttu-id="e154f-113">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="e154f-113">C# operators</span></span>](index.md)
