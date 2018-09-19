---
title: '@ (Odwołanie w C#)'
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
ms.openlocfilehash: 6d6da87159e3ec9184eaa76ad069102204e2fcfc
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46009378"
---
# <a name="-c-reference"></a><span data-ttu-id="eb539-102">@ (Odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="eb539-102">@ (C# Reference)</span></span>

<span data-ttu-id="eb539-103">`@` Znak specjalny służy jako identyfikator dosłownego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="eb539-103">The `@` special character serves as a verbatim identifier.</span></span> <span data-ttu-id="eb539-104">Mogą być używane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="eb539-104">It can be used in the following ways:</span></span>

1. <span data-ttu-id="eb539-105">Aby włączyć słowa kluczowe języka C#, aby można używać jako identyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="eb539-105">To enable C# keywords to be used as identifiers.</span></span> <span data-ttu-id="eb539-106">`@` Znak prefiksy element kodu, który kompilator ma interpretować jako identyfikator zamiast słowa kluczowego języka C#.</span><span class="sxs-lookup"><span data-stu-id="eb539-106">The `@` character prefixes a code element that the compiler is to interpret as an identifier rather than a C# keyword.</span></span> <span data-ttu-id="eb539-107">W poniższym przykładzie użyto `@` znak definiują identyfikatora o nazwie `for` używającej w `for` pętli.</span><span class="sxs-lookup"><span data-stu-id="eb539-107">The following example uses the `@` character to define an identifier named `for` that it uses in a `for` loop.</span></span>

   [!code-csharp[verbatim1](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#1)]

1. <span data-ttu-id="eb539-108">Aby wskazać, że literał ciągu ma być interpretowany dosłownie.</span><span class="sxs-lookup"><span data-stu-id="eb539-108">To indicate that a string literal is to be interpreted verbatim.</span></span> <span data-ttu-id="eb539-109">`@` Definiuje znak, w tym wystąpieniu *verbatim literału ciągu*.</span><span class="sxs-lookup"><span data-stu-id="eb539-109">The `@` character in this instance defines a *verbatim string literal*.</span></span> <span data-ttu-id="eb539-110">Proste sekwencje ucieczki (takich jak `"\\"` dla ukośnik odwrotny) szesnastkową sekwencje unikowe (takich jak `"\x0041"` a wielkie litery) i sekwencje unikowe Unicode (takich jak `"\u0041"` wielkie litery a) jest interpretowany dosłownie.</span><span class="sxs-lookup"><span data-stu-id="eb539-110">Simple escape sequences (such as `"\\"` for a backslash), hexadecimal escape sequences (such as `"\x0041"` for an uppercase A), and Unicode escape sequences (such as `"\u0041"` for an uppercase A) are interpreted literally.</span></span> <span data-ttu-id="eb539-111">Tylko sekwencja unikowa oferty (`""`) nie jest interpretowany dosłownie; generuje pojedynczy znak cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="eb539-111">Only a quote escape sequence (`""`) is not interpreted literally; it produces a single quotation mark.</span></span> <span data-ttu-id="eb539-112">Ponadto w przypadku verbatim [ciągiem interpolowanym](interpolated.md) sekwencje unikowe nawiasu klamrowego (`{{` i `}}`) nie jest interpretowany dosłownie; produkują znaki pojedynczy nawias klamrowy.</span><span class="sxs-lookup"><span data-stu-id="eb539-112">Additionally, in case of a verbatim [interpolated string](interpolated.md) brace escape sequences (`{{` and `}}`) are not interpreted literally; they produce single brace characters.</span></span> <span data-ttu-id="eb539-113">W poniższym przykładzie zdefiniowano dwie ścieżki identyczny plik za pomocą literału ciągu regularnych, a druga za pomocą literału ciągu verbatim.</span><span class="sxs-lookup"><span data-stu-id="eb539-113">The following example defines two identical file paths, one by using a regular string literal and the other by using a verbatim string literal.</span></span> <span data-ttu-id="eb539-114">Jest to jedna z bardziej powszechne zastosowania verbatim literałów.</span><span class="sxs-lookup"><span data-stu-id="eb539-114">This is one of the more common uses of verbatim string literals.</span></span>

   [!code-csharp[verbatim2](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#2)]

   <span data-ttu-id="eb539-115">Poniższy przykład ilustruje efekt Definiowanie regularne literału ciągu i ciąg verbatim literał, która zawiera sekwencje znaków identyczne.</span><span class="sxs-lookup"><span data-stu-id="eb539-115">The following example illustrates the effect of defining a regular string literal and a verbatim string literal that contain identical character sequences.</span></span>

   [!code-csharp[verbatim3](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#3)]

1. <span data-ttu-id="eb539-116">Aby umożliwić kompilatorowi rozróżnienie między atrybutami w przypadku konfliktu nazw.</span><span class="sxs-lookup"><span data-stu-id="eb539-116">To enable the compiler to distinguish between attributes in cases of a naming conflict.</span></span> <span data-ttu-id="eb539-117">Atrybut jest klasa, która pochodzi od klasy <xref:System.Attribute>.</span><span class="sxs-lookup"><span data-stu-id="eb539-117">An attribute is a class that derives from <xref:System.Attribute>.</span></span> <span data-ttu-id="eb539-118">Nazwa jej typu obejmują zazwyczaj sufiks **atrybutu**, mimo że kompilator nie wymusza tę Konwencję.</span><span class="sxs-lookup"><span data-stu-id="eb539-118">Its type name typically includes the suffix **Attribute**, although the compiler does not enforce this convention.</span></span> <span data-ttu-id="eb539-119">Ten atrybut może odwoływać w kodzie przez jego pełna nazwa typu (na przykład `[InfoAttribute]` lub jego skróconą nazwę (na przykład `[Info]`).</span><span class="sxs-lookup"><span data-stu-id="eb539-119">The attribute can then be referenced in code either by its full type name (for example, `[InfoAttribute]` or its shortened name (for example, `[Info]`).</span></span> <span data-ttu-id="eb539-120">Jednak konflikt nazw występuje, jeśli dwa skrócone nazwy typu atrybutu są identyczne, i zawiera jedną nazwę typu **atrybut** sufiks, ale innych nie.</span><span class="sxs-lookup"><span data-stu-id="eb539-120">However, a naming conflict occurs if two shortened attribute type names are identical, and one type name includes the **Attribute** suffix but the other does not.</span></span> <span data-ttu-id="eb539-121">Na przykład, poniższy kod nie zostanie skompilowany, ponieważ kompilator nie może określić czy `Info` lub `InfoAttribute` atrybut jest stosowany do `Example` klasy.</span><span class="sxs-lookup"><span data-stu-id="eb539-121">For example, the following code fails to compile because the compiler cannot determine whether the `Info` or `InfoAttribute` attribute is applied to the `Example` class.</span></span> <span data-ttu-id="eb539-122">Zobacz [CS1614](../compiler-messages/cs1614.md) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="eb539-122">See [CS1614](../compiler-messages/cs1614.md) for more information.</span></span>

   [!code-csharp[verbatim4](../../../../samples/snippets/csharp/language-reference/keywords/verbatim2.cs#1)]

## <a name="see-also"></a><span data-ttu-id="eb539-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="eb539-123">See Also</span></span>

- [<span data-ttu-id="eb539-124">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="eb539-124">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="eb539-125">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="eb539-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="eb539-126">Znaki specjalne języka C#</span><span class="sxs-lookup"><span data-stu-id="eb539-126">C# Special Characters</span></span>](../../../csharp/language-reference/tokens/index.md)
