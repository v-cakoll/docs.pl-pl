---
title: '@ - C# Odniesienie'
ms.date: 02/09/2017
f1_keywords:
- '@_CSharpKeyword'
- '@'
helpviewer_keywords:
- '@ special character [C#]'
- '@ language element [C#]'
ms.assetid: 89bc7e53-85f5-478a-866d-1cca003c4e8c
ms.openlocfilehash: a3446eceb0d3c415e36ea1d2c7d8d6d34f65350d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712419"
---
# <a name="-c-reference"></a><span data-ttu-id="544a4-102">@ (Odwołanie C#)</span><span class="sxs-lookup"><span data-stu-id="544a4-102">@ (C# Reference)</span></span>

<span data-ttu-id="544a4-103">Znak `@` specjalny służy jako dosłowny identyfikator.</span><span class="sxs-lookup"><span data-stu-id="544a4-103">The `@` special character serves as a verbatim identifier.</span></span> <span data-ttu-id="544a4-104">Może być stosowany w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="544a4-104">It can be used in the following ways:</span></span>

1. <span data-ttu-id="544a4-105">Aby włączyć słowa kluczowe języka C#, które mają być używane jako identyfikatory.</span><span class="sxs-lookup"><span data-stu-id="544a4-105">To enable C# keywords to be used as identifiers.</span></span> <span data-ttu-id="544a4-106">Znak `@` prefiksuje element kodu, który kompilator ma interpretować jako identyfikator, a nie słowa kluczowego C#.</span><span class="sxs-lookup"><span data-stu-id="544a4-106">The `@` character prefixes a code element that the compiler is to interpret as an identifier rather than a C# keyword.</span></span> <span data-ttu-id="544a4-107">Poniższy przykład używa `@` znaku do definiowania identyfikatora o nazwie, `for` który używa w `for` pętli.</span><span class="sxs-lookup"><span data-stu-id="544a4-107">The following example uses the `@` character to define an identifier named `for` that it uses in a `for` loop.</span></span>

   [!code-csharp[verbatim1](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#1)]

1. <span data-ttu-id="544a4-108">Aby wskazać, że literał ciągu ma być interpretowany dosłownie.</span><span class="sxs-lookup"><span data-stu-id="544a4-108">To indicate that a string literal is to be interpreted verbatim.</span></span> <span data-ttu-id="544a4-109">Znak `@` w tym wystąpieniu definiuje *dosłowny ciąg literany*.</span><span class="sxs-lookup"><span data-stu-id="544a4-109">The `@` character in this instance defines a *verbatim string literal*.</span></span> <span data-ttu-id="544a4-110">Sekwencje prostych ucieczek `"\\"` (na przykład dla ukośnika odwrotnego), `"\x0041"` sekwencje ucieczki szesnastkowej (na `"\u0041"` przykład dla sekwencji ucieczki wielkimi literami A) i sekwencje ucieczki Unicode (takie jak wielkie litery A) są interpretowane dosłownie.</span><span class="sxs-lookup"><span data-stu-id="544a4-110">Simple escape sequences (such as `"\\"` for a backslash), hexadecimal escape sequences (such as `"\x0041"` for an uppercase A), and Unicode escape sequences (such as `"\u0041"` for an uppercase A) are interpreted literally.</span></span> <span data-ttu-id="544a4-111">Tylko sekwencja ucieczki`""`cudzysłowu ( ) nie jest interpretowana dosłownie; tworzy jeden cudzysłów.</span><span class="sxs-lookup"><span data-stu-id="544a4-111">Only a quote escape sequence (`""`) is not interpreted literally; it produces a single quotation mark.</span></span> <span data-ttu-id="544a4-112">Ponadto w przypadku dosłownego [interpolacji](interpolated.md) sekwencji ucieczki nawiasu klamrowego (`{{` i `}}`) nie są interpretowane dosłownie; tworzą pojedyncze znaki klamry.</span><span class="sxs-lookup"><span data-stu-id="544a4-112">Additionally, in case of a verbatim [interpolated string](interpolated.md) brace escape sequences (`{{` and `}}`) are not interpreted literally; they produce single brace characters.</span></span> <span data-ttu-id="544a4-113">Poniższy przykład definiuje dwie identyczne ścieżki plików, jeden przy użyciu zwykłego literału ciągu, a drugi przy użyciu dosłownego literału ciągu.</span><span class="sxs-lookup"><span data-stu-id="544a4-113">The following example defines two identical file paths, one by using a regular string literal and the other by using a verbatim string literal.</span></span> <span data-ttu-id="544a4-114">Jest to jedno z najczęstszych zastosowań dosłownych literałstów ciągów.</span><span class="sxs-lookup"><span data-stu-id="544a4-114">This is one of the more common uses of verbatim string literals.</span></span>

   [!code-csharp[verbatim2](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#2)]

   <span data-ttu-id="544a4-115">Poniższy przykład ilustruje efekt definiowania zwykłego literału ciągu i dosłownego literału ciągu, które zawierają identyczne sekwencje znaków.</span><span class="sxs-lookup"><span data-stu-id="544a4-115">The following example illustrates the effect of defining a regular string literal and a verbatim string literal that contain identical character sequences.</span></span>

   [!code-csharp[verbatim3](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#3)]

1. <span data-ttu-id="544a4-116">Aby włączyć kompilator do rozróżniania atrybutów w przypadku konfliktu nazewnictwa.</span><span class="sxs-lookup"><span data-stu-id="544a4-116">To enable the compiler to distinguish between attributes in cases of a naming conflict.</span></span> <span data-ttu-id="544a4-117">Atrybut jest klasą, która <xref:System.Attribute>pochodzi od .</span><span class="sxs-lookup"><span data-stu-id="544a4-117">An attribute is a class that derives from <xref:System.Attribute>.</span></span> <span data-ttu-id="544a4-118">Jego nazwa typu zazwyczaj zawiera **atrybut**sufiksu , chociaż kompilator nie wymusza tej konwencji.</span><span class="sxs-lookup"><span data-stu-id="544a4-118">Its type name typically includes the suffix **Attribute**, although the compiler does not enforce this convention.</span></span> <span data-ttu-id="544a4-119">Atrybut może być następnie odwołuje się w kodzie albo `[InfoAttribute]` przez jego pełną nazwę `[Info]`typu (na przykład lub jego skróconej nazwy (na przykład).</span><span class="sxs-lookup"><span data-stu-id="544a4-119">The attribute can then be referenced in code either by its full type name (for example, `[InfoAttribute]` or its shortened name (for example, `[Info]`).</span></span> <span data-ttu-id="544a4-120">Jednak konflikt nazewnictwa występuje, jeśli dwie skrócone nazwy typów atrybutów są identyczne, a jedna nazwa typu zawiera sufiks **atrybutu,** ale druga nie.</span><span class="sxs-lookup"><span data-stu-id="544a4-120">However, a naming conflict occurs if two shortened attribute type names are identical, and one type name includes the **Attribute** suffix but the other does not.</span></span> <span data-ttu-id="544a4-121">Na przykład następujący kod nie może skompilować, ponieważ `Info` `InfoAttribute` kompilator nie `Example` może określić, czy lub atrybut jest stosowany do klasy.</span><span class="sxs-lookup"><span data-stu-id="544a4-121">For example, the following code fails to compile because the compiler cannot determine whether the `Info` or `InfoAttribute` attribute is applied to the `Example` class.</span></span> <span data-ttu-id="544a4-122">Więcej informacji można znaleźć w [systemie CS1614.](../compiler-messages/cs1614.md)</span><span class="sxs-lookup"><span data-stu-id="544a4-122">See [CS1614](../compiler-messages/cs1614.md) for more information.</span></span>

   [!code-csharp[verbatim4](../../../../samples/snippets/csharp/language-reference/keywords/verbatim2.cs#1)]

## <a name="see-also"></a><span data-ttu-id="544a4-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="544a4-123">See also</span></span>

- [<span data-ttu-id="544a4-124">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="544a4-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="544a4-125">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="544a4-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="544a4-126">Znaki specjalne języka C#</span><span class="sxs-lookup"><span data-stu-id="544a4-126">C# Special Characters</span></span>](./index.md)
