---
title: Operatory równości
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], Equals method
- class library design guidelines [.NET Framework], equality operator
- equality operator (==) [.NET Framework]
- Equals method
- == operator (equality) [.NET Framework]
ms.assetid: bc496a91-fefb-4ce0-ab4c-61f09964119a
ms.openlocfilehash: 34fc8eef5270369419b76899f0dbe1ace106caf6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741692"
---
# <a name="equality-operators"></a><span data-ttu-id="7f806-102">Operatory równości</span><span class="sxs-lookup"><span data-stu-id="7f806-102">Equality Operators</span></span>
<span data-ttu-id="7f806-103">W tej sekcji omówiono przeciążanie operatorów równości i odwołuje się do `operator==` i `operator!=` jako operatory równości.</span><span class="sxs-lookup"><span data-stu-id="7f806-103">This section discusses overloading equality operators and refers to `operator==` and `operator!=` as equality operators.</span></span>

 <span data-ttu-id="7f806-104">❌ nie przeciążać jednego z operatorów równości, a nie innych.</span><span class="sxs-lookup"><span data-stu-id="7f806-104">❌ DO NOT overload one of the equality operators and not the other.</span></span>

 <span data-ttu-id="7f806-105">✔️ Upewnij się, że <xref:System.Object.Equals%2A?displayProperty=nameWithType> i operatory równości mają dokładnie tę samą semantykę i podobną charakterystykę wydajności.</span><span class="sxs-lookup"><span data-stu-id="7f806-105">✔️ DO ensure that <xref:System.Object.Equals%2A?displayProperty=nameWithType> and the equality operators have exactly the same semantics and similar performance characteristics.</span></span>

 <span data-ttu-id="7f806-106">Często oznacza to, że `Object.Equals` należy przesłonić, gdy operatory równości są przeciążone.</span><span class="sxs-lookup"><span data-stu-id="7f806-106">This often means that `Object.Equals` needs to be overridden when the equality operators are overloaded.</span></span>

 <span data-ttu-id="7f806-107">❌ UNIKAj zgłaszania wyjątków od operatorów równości.</span><span class="sxs-lookup"><span data-stu-id="7f806-107">❌ AVOID throwing exceptions from equality operators.</span></span>

 <span data-ttu-id="7f806-108">Na przykład Zwróć wartość false, jeśli jeden z argumentów ma wartość null zamiast zgłaszać `NullReferenceException`.</span><span class="sxs-lookup"><span data-stu-id="7f806-108">For example, return false if one of the arguments is null instead of throwing `NullReferenceException`.</span></span>

## <a name="equality-operators-on-value-types"></a><span data-ttu-id="7f806-109">Operatory równości w typach wartości</span><span class="sxs-lookup"><span data-stu-id="7f806-109">Equality Operators on Value Types</span></span>
 <span data-ttu-id="7f806-110">✔️ przeciążać operatory równości dla typów wartości, jeśli równość jest istotna.</span><span class="sxs-lookup"><span data-stu-id="7f806-110">✔️ DO overload the equality operators on value types, if equality is meaningful.</span></span>

 <span data-ttu-id="7f806-111">W większości języków programowania nie istnieje domyślna implementacja `operator==` dla typów wartości.</span><span class="sxs-lookup"><span data-stu-id="7f806-111">In most programming languages, there is no default implementation of `operator==` for value types.</span></span>

## <a name="equality-operators-on-reference-types"></a><span data-ttu-id="7f806-112">Operatory równości w typach referencyjnych</span><span class="sxs-lookup"><span data-stu-id="7f806-112">Equality Operators on Reference Types</span></span>
 <span data-ttu-id="7f806-113">❌ uniknąć przeciążania operatorów równości dla modyfikowalnych typów odwołań.</span><span class="sxs-lookup"><span data-stu-id="7f806-113">❌ AVOID overloading equality operators on mutable reference types.</span></span>

 <span data-ttu-id="7f806-114">Wiele języków ma wbudowane operatory równości dla typów referencyjnych.</span><span class="sxs-lookup"><span data-stu-id="7f806-114">Many languages have built-in equality operators for reference types.</span></span> <span data-ttu-id="7f806-115">Operatory wbudowane zwykle implementują równość odwołań, a wielu deweloperów jest przeważnie, gdy domyślne zachowanie zostanie zmienione na równość wartości.</span><span class="sxs-lookup"><span data-stu-id="7f806-115">The built-in operators usually implement the reference equality, and many developers are surprised when the default behavior is changed to the value equality.</span></span>

 <span data-ttu-id="7f806-116">Ten problem został skorygowany dla niezmiennego typu referencyjnego, ponieważ niezmienności znacznie trudniejsze do zauważenia różnicy między równośćmi referencyjnymi i równość wartości.</span><span class="sxs-lookup"><span data-stu-id="7f806-116">This problem is mitigated for immutable reference types because immutability makes it much harder to notice the difference between reference equality and value equality.</span></span>

 <span data-ttu-id="7f806-117">❌ unikać przeciążania operatorów równości w typach referencyjnych, jeśli implementacja będzie znacznie mniejsza niż wartość równości odwołań.</span><span class="sxs-lookup"><span data-stu-id="7f806-117">❌ AVOID overloading equality operators on reference types if the implementation would be significantly slower than that of reference equality.</span></span>

 <span data-ttu-id="7f806-118">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="7f806-118">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="7f806-119">*Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="7f806-119">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="7f806-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7f806-120">See also</span></span>

- [<span data-ttu-id="7f806-121">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="7f806-121">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="7f806-122">Zalecenia dotyczące użytkowania</span><span class="sxs-lookup"><span data-stu-id="7f806-122">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)
