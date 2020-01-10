---
title: '@- C# Reference'
ms.date: 02/09/2017
f1_keywords:
- '@_CSharpKeyword'
- '@'
helpviewer_keywords:
- '@ special character [C#]'
- '@ language element [C#]'
ms.assetid: 89bc7e53-85f5-478a-866d-1cca003c4e8c
ms.openlocfilehash: a3446eceb0d3c415e36ea1d2c7d8d6d34f65350d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712419"
---
# <a name="-c-reference"></a><span data-ttu-id="ce16f-102">@ (C# Odwołanie)</span><span class="sxs-lookup"><span data-stu-id="ce16f-102">@ (C# Reference)</span></span>

<span data-ttu-id="ce16f-103">`@` znak specjalny służy jako identyfikator Verbatim.</span><span class="sxs-lookup"><span data-stu-id="ce16f-103">The `@` special character serves as a verbatim identifier.</span></span> <span data-ttu-id="ce16f-104">Może być używana w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="ce16f-104">It can be used in the following ways:</span></span>

1. <span data-ttu-id="ce16f-105">Aby włączyć C# używanie słów kluczowych jako identyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="ce16f-105">To enable C# keywords to be used as identifiers.</span></span> <span data-ttu-id="ce16f-106">`@` znak prefiksu elementu kodu, który kompilator ma interpretować jako identyfikator zamiast C# słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="ce16f-106">The `@` character prefixes a code element that the compiler is to interpret as an identifier rather than a C# keyword.</span></span> <span data-ttu-id="ce16f-107">Poniższy przykład używa znaku `@` do definiowania identyfikatora o nazwie `for`, który używa w pętli `for`.</span><span class="sxs-lookup"><span data-stu-id="ce16f-107">The following example uses the `@` character to define an identifier named `for` that it uses in a `for` loop.</span></span>

   [!code-csharp[verbatim1](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#1)]

1. <span data-ttu-id="ce16f-108">Aby wskazać, że literał ciągu ma być interpretowany Verbatim.</span><span class="sxs-lookup"><span data-stu-id="ce16f-108">To indicate that a string literal is to be interpreted verbatim.</span></span> <span data-ttu-id="ce16f-109">Znak `@` w tym wystąpieniu definiuje *literał ciągu Verbatim*.</span><span class="sxs-lookup"><span data-stu-id="ce16f-109">The `@` character in this instance defines a *verbatim string literal*.</span></span> <span data-ttu-id="ce16f-110">Proste sekwencje ucieczki (takie jak `"\\"` dla ukośnika odwrotnego), szesnastkowe sekwencje ucieczki (takie jak `"\x0041"` dla Wielkiej litery A) oraz sekwencje znaków Unicode (takie jak `"\u0041"` dla Wielkiej litery A) są interpretowane dosłownie.</span><span class="sxs-lookup"><span data-stu-id="ce16f-110">Simple escape sequences (such as `"\\"` for a backslash), hexadecimal escape sequences (such as `"\x0041"` for an uppercase A), and Unicode escape sequences (such as `"\u0041"` for an uppercase A) are interpreted literally.</span></span> <span data-ttu-id="ce16f-111">Tylko sekwencja ucieczki oferty (`""`) nie jest interpretowana dosłownie; tworzy pojedynczy cudzysłów.</span><span class="sxs-lookup"><span data-stu-id="ce16f-111">Only a quote escape sequence (`""`) is not interpreted literally; it produces a single quotation mark.</span></span> <span data-ttu-id="ce16f-112">Ponadto w przypadku Verbatim [interpolowanego](interpolated.md) nawiasu klamrowego sekwencje unikowe (`{{` i `}}`) nie są interpretowane dosłownie; generują one pojedyncze nawiasy klamrowe.</span><span class="sxs-lookup"><span data-stu-id="ce16f-112">Additionally, in case of a verbatim [interpolated string](interpolated.md) brace escape sequences (`{{` and `}}`) are not interpreted literally; they produce single brace characters.</span></span> <span data-ttu-id="ce16f-113">W poniższym przykładzie zdefiniowano dwie identyczne ścieżki plików, jeden przy użyciu zwykłego literału ciągu, a drugi przy użyciu literału ciągu Verbatim.</span><span class="sxs-lookup"><span data-stu-id="ce16f-113">The following example defines two identical file paths, one by using a regular string literal and the other by using a verbatim string literal.</span></span> <span data-ttu-id="ce16f-114">Jest to jeden z najczęściej używanych Verbatim literałów ciągów.</span><span class="sxs-lookup"><span data-stu-id="ce16f-114">This is one of the more common uses of verbatim string literals.</span></span>

   [!code-csharp[verbatim2](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#2)]

   <span data-ttu-id="ce16f-115">Poniższy przykład ilustruje efekt definiowania zwykłego literału ciągu i literału ciągu Verbatim, który zawiera identyczne sekwencje znaków.</span><span class="sxs-lookup"><span data-stu-id="ce16f-115">The following example illustrates the effect of defining a regular string literal and a verbatim string literal that contain identical character sequences.</span></span>

   [!code-csharp[verbatim3](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#3)]

1. <span data-ttu-id="ce16f-116">Aby umożliwić kompilatorowi rozróżnienie atrybutów w przypadkach konfliktu nazw.</span><span class="sxs-lookup"><span data-stu-id="ce16f-116">To enable the compiler to distinguish between attributes in cases of a naming conflict.</span></span> <span data-ttu-id="ce16f-117">Atrybut jest klasą, która pochodzi od <xref:System.Attribute>.</span><span class="sxs-lookup"><span data-stu-id="ce16f-117">An attribute is a class that derives from <xref:System.Attribute>.</span></span> <span data-ttu-id="ce16f-118">Nazwa typu zwykle zawiera **atrybut**sufiksu, chociaż kompilator nie wymusza tej Konwencji.</span><span class="sxs-lookup"><span data-stu-id="ce16f-118">Its type name typically includes the suffix **Attribute**, although the compiler does not enforce this convention.</span></span> <span data-ttu-id="ce16f-119">Ten atrybut może być następnie przywoływany w kodzie według jego pełnej nazwy typu (na przykład `[InfoAttribute]` lub jego skróconej nazwy (na przykład `[Info]`).</span><span class="sxs-lookup"><span data-stu-id="ce16f-119">The attribute can then be referenced in code either by its full type name (for example, `[InfoAttribute]` or its shortened name (for example, `[Info]`).</span></span> <span data-ttu-id="ce16f-120">Jednak konflikt nazewnictwa występuje, jeśli dwa skrócone nazwy typów atrybutów są identyczne, a jedna nazwa typu zawiera sufiks **atrybutu** , ale drugi nie.</span><span class="sxs-lookup"><span data-stu-id="ce16f-120">However, a naming conflict occurs if two shortened attribute type names are identical, and one type name includes the **Attribute** suffix but the other does not.</span></span> <span data-ttu-id="ce16f-121">Na przykład następujący kod nie zostanie skompilowany, ponieważ kompilator nie może określić, czy atrybut `Info` lub `InfoAttribute` jest stosowany do klasy `Example`.</span><span class="sxs-lookup"><span data-stu-id="ce16f-121">For example, the following code fails to compile because the compiler cannot determine whether the `Info` or `InfoAttribute` attribute is applied to the `Example` class.</span></span> <span data-ttu-id="ce16f-122">Aby uzyskać więcej informacji, zobacz [CS1614](../compiler-messages/cs1614.md) .</span><span class="sxs-lookup"><span data-stu-id="ce16f-122">See [CS1614](../compiler-messages/cs1614.md) for more information.</span></span>

   [!code-csharp[verbatim4](../../../../samples/snippets/csharp/language-reference/keywords/verbatim2.cs#1)]

## <a name="see-also"></a><span data-ttu-id="ce16f-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ce16f-123">See also</span></span>

- [<span data-ttu-id="ce16f-124">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="ce16f-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ce16f-125">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="ce16f-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ce16f-126">Znaki specjalne języka C#</span><span class="sxs-lookup"><span data-stu-id="ce16f-126">C# Special Characters</span></span>](./index.md)
