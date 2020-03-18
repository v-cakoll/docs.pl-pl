---
title: nameof operator - odwołanie do języka C#
ms.date: 07/12/2019
f1_keywords:
- nameof_CSharpKeyword
- nameof
helpviewer_keywords:
- nameof operator [C#]
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: ffbc801acf61bf72db1c88912dc2142a478fa280
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846275"
---
# <a name="nameof-operator-c-reference"></a><span data-ttu-id="a9a98-102">operator nameof (odwołanie do języka C#)</span><span class="sxs-lookup"><span data-stu-id="a9a98-102">nameof operator (C# reference)</span></span>

<span data-ttu-id="a9a98-103">Operator `nameof` uzyskuje nazwę zmiennej, typu lub elementu członkowskiego jako stałą ciągu:</span><span class="sxs-lookup"><span data-stu-id="a9a98-103">The `nameof` operator obtains the name of a variable, type, or member as the string constant:</span></span>

[!code-csharp-interactive[nameof operator](snippets/NameOfOperator.cs#Examples)]

<span data-ttu-id="a9a98-104">Jak pokazano w poprzednim przykładzie, w przypadku typu i obszaru nazw, nazwa wyprodukowana zwykle nie jest [w pełni kwalifikowana.](~/_csharplang/spec/basic-concepts.md#fully-qualified-names)</span><span class="sxs-lookup"><span data-stu-id="a9a98-104">As the preceding example shows, in the case of a type and a namespace, the produced name is usually not [fully qualified](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span></span>

<span data-ttu-id="a9a98-105">Operator `nameof` jest oceniany w czasie kompilacji i nie ma wpływu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="a9a98-105">The `nameof` operator is evaluated at compile time and has no effect at run time.</span></span>

<span data-ttu-id="a9a98-106">Operator służy `nameof` do tworzenia kodu sprawdzania argumentów bardziej wykonalne:</span><span class="sxs-lookup"><span data-stu-id="a9a98-106">You can use the `nameof` operator to make the argument-checking code more maintainable:</span></span>

[!code-csharp[nameof and argument check](snippets/NameOfOperator.cs#ExceptionMessage)]

<span data-ttu-id="a9a98-107">Operator `nameof` jest dostępny w języku C# 6 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="a9a98-107">The `nameof` operator is available in C# 6 and later.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="a9a98-108">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="a9a98-108">C# language specification</span></span>

<span data-ttu-id="a9a98-109">Aby uzyskać więcej informacji, zobacz [Nameof wyrażeń](~/_csharplang/spec/expressions.md#nameof-expressions) sekcji [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="a9a98-109">For more information, see the [Nameof expressions](~/_csharplang/spec/expressions.md#nameof-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a9a98-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a9a98-110">See also</span></span>

- [<span data-ttu-id="a9a98-111">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="a9a98-111">C# reference</span></span>](../index.md)
- [<span data-ttu-id="a9a98-112">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="a9a98-112">C# operators</span></span>](index.md)
