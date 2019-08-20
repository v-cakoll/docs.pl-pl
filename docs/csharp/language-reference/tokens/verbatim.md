---
title: '@- C# Reference'
ms.custom: seodec18
ms.date: 02/09/2017
f1_keywords:
- '@_CSharpKeyword'
- '@'
helpviewer_keywords:
- '@ special character [C#]'
- '@ language element [C#]'
ms.assetid: 89bc7e53-85f5-478a-866d-1cca003c4e8c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b2290c87f7d4d2ba8da122d4f5ddb9ea423852ec
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608732"
---
# <a name="-c-reference"></a><span data-ttu-id="4df4a-102">@ (C# Odwołanie)</span><span class="sxs-lookup"><span data-stu-id="4df4a-102">@ (C# Reference)</span></span>

<span data-ttu-id="4df4a-103">Znak `@` specjalny służy jako identyfikator Verbatim.</span><span class="sxs-lookup"><span data-stu-id="4df4a-103">The `@` special character serves as a verbatim identifier.</span></span> <span data-ttu-id="4df4a-104">Może być używana w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="4df4a-104">It can be used in the following ways:</span></span>

1. <span data-ttu-id="4df4a-105">Aby włączyć C# używanie słów kluczowych jako identyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="4df4a-105">To enable C# keywords to be used as identifiers.</span></span> <span data-ttu-id="4df4a-106">Znak prefiksu elementu kodu, który kompilator ma interpretować jako identyfikator zamiast C# słowa kluczowego. `@`</span><span class="sxs-lookup"><span data-stu-id="4df4a-106">The `@` character prefixes a code element that the compiler is to interpret as an identifier rather than a C# keyword.</span></span> <span data-ttu-id="4df4a-107">Poniższy przykład używa `@` znaku do definiowania identyfikatora o nazwie `for` `for` , który używa w pętli.</span><span class="sxs-lookup"><span data-stu-id="4df4a-107">The following example uses the `@` character to define an identifier named `for` that it uses in a `for` loop.</span></span>

   [!code-csharp[verbatim1](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#1)]

1. <span data-ttu-id="4df4a-108">Aby wskazać, że literał ciągu ma być interpretowany Verbatim.</span><span class="sxs-lookup"><span data-stu-id="4df4a-108">To indicate that a string literal is to be interpreted verbatim.</span></span> <span data-ttu-id="4df4a-109">Znak w tym wystąpieniu definiuje *literał ciągu Verbatim.* `@`</span><span class="sxs-lookup"><span data-stu-id="4df4a-109">The `@` character in this instance defines a *verbatim string literal*.</span></span> <span data-ttu-id="4df4a-110">Proste sekwencje ucieczki ( `"\\"` takie jak dla ukośnika odwrotnego), szesnastkowe sekwencje ucieczki ( `"\x0041"` na przykład dla Wielkiej litery a) i sekwencje znaków Unicode ( `"\u0041"` na przykład dla Wielkiej litery a) są interpretowane dosłownie.</span><span class="sxs-lookup"><span data-stu-id="4df4a-110">Simple escape sequences (such as `"\\"` for a backslash), hexadecimal escape sequences (such as `"\x0041"` for an uppercase A), and Unicode escape sequences (such as `"\u0041"` for an uppercase A) are interpreted literally.</span></span> <span data-ttu-id="4df4a-111">Tylko sekwencja ucieczki oferty (`""`) nie jest interpretowana dosłownie; tworzy pojedynczy znak cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="4df4a-111">Only a quote escape sequence (`""`) is not interpreted literally; it produces a single quotation mark.</span></span> <span data-ttu-id="4df4a-112">Ponadto w przypadku Verbatim [interpolowanego](interpolated.md) nawiasu klamrowego sekwencje ucieczki (`{{` i `}}`) nie są interpretowane dosłownie; tworzą one pojedyncze nawiasy klamrowe.</span><span class="sxs-lookup"><span data-stu-id="4df4a-112">Additionally, in case of a verbatim [interpolated string](interpolated.md) brace escape sequences (`{{` and `}}`) are not interpreted literally; they produce single brace characters.</span></span> <span data-ttu-id="4df4a-113">W poniższym przykładzie zdefiniowano dwie identyczne ścieżki plików, jeden przy użyciu zwykłego literału ciągu, a drugi przy użyciu literału ciągu Verbatim.</span><span class="sxs-lookup"><span data-stu-id="4df4a-113">The following example defines two identical file paths, one by using a regular string literal and the other by using a verbatim string literal.</span></span> <span data-ttu-id="4df4a-114">Jest to jeden z najczęściej używanych Verbatim literałów ciągów.</span><span class="sxs-lookup"><span data-stu-id="4df4a-114">This is one of the more common uses of verbatim string literals.</span></span>

   [!code-csharp[verbatim2](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#2)]

   <span data-ttu-id="4df4a-115">Poniższy przykład ilustruje efekt definiowania zwykłego literału ciągu i literału ciągu Verbatim, który zawiera identyczne sekwencje znaków.</span><span class="sxs-lookup"><span data-stu-id="4df4a-115">The following example illustrates the effect of defining a regular string literal and a verbatim string literal that contain identical character sequences.</span></span>

   [!code-csharp[verbatim3](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#3)]

1. <span data-ttu-id="4df4a-116">Aby umożliwić kompilatorowi rozróżnienie atrybutów w przypadkach konfliktu nazw.</span><span class="sxs-lookup"><span data-stu-id="4df4a-116">To enable the compiler to distinguish between attributes in cases of a naming conflict.</span></span> <span data-ttu-id="4df4a-117">Atrybut jest klasą, która pochodzi od <xref:System.Attribute>.</span><span class="sxs-lookup"><span data-stu-id="4df4a-117">An attribute is a class that derives from <xref:System.Attribute>.</span></span> <span data-ttu-id="4df4a-118">Nazwa typu zwykle zawiera **atrybut**sufiksu, chociaż kompilator nie wymusza tej Konwencji.</span><span class="sxs-lookup"><span data-stu-id="4df4a-118">Its type name typically includes the suffix **Attribute**, although the compiler does not enforce this convention.</span></span> <span data-ttu-id="4df4a-119">Atrybut może następnie być przywoływany w kodzie według jego pełnej nazwy typu (na przykład `[InfoAttribute]` lub jego skróconej nazwy (na `[Info]`przykład).</span><span class="sxs-lookup"><span data-stu-id="4df4a-119">The attribute can then be referenced in code either by its full type name (for example, `[InfoAttribute]` or its shortened name (for example, `[Info]`).</span></span> <span data-ttu-id="4df4a-120">Jednak konflikt nazewnictwa występuje, jeśli dwa skrócone nazwy typów atrybutów są identyczne, a jedna nazwa typu zawiera sufiks **atrybutu** , ale drugi nie.</span><span class="sxs-lookup"><span data-stu-id="4df4a-120">However, a naming conflict occurs if two shortened attribute type names are identical, and one type name includes the **Attribute** suffix but the other does not.</span></span> <span data-ttu-id="4df4a-121">Na przykład następujący kod nie zostanie skompilowany, ponieważ kompilator nie może określić, `Info` czy `Example` atrybut lub `InfoAttribute` jest stosowany do klasy.</span><span class="sxs-lookup"><span data-stu-id="4df4a-121">For example, the following code fails to compile because the compiler cannot determine whether the `Info` or `InfoAttribute` attribute is applied to the `Example` class.</span></span> <span data-ttu-id="4df4a-122">Aby uzyskać więcej informacji, zobacz [CS1614](../compiler-messages/cs1614.md) .</span><span class="sxs-lookup"><span data-stu-id="4df4a-122">See [CS1614](../compiler-messages/cs1614.md) for more information.</span></span>

   [!code-csharp[verbatim4](../../../../samples/snippets/csharp/language-reference/keywords/verbatim2.cs#1)]

## <a name="see-also"></a><span data-ttu-id="4df4a-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4df4a-123">See also</span></span>

- [<span data-ttu-id="4df4a-124">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="4df4a-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="4df4a-125">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="4df4a-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="4df4a-126">Znaki specjalne języka C#</span><span class="sxs-lookup"><span data-stu-id="4df4a-126">C# Special Characters</span></span>](./index.md)
