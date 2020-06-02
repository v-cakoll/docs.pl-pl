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
ms.openlocfilehash: bd36b98af25db2921c164ac359188997d379a270
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84280053"
---
# <a name="equality-operators"></a><span data-ttu-id="e20f0-102">Operatory równości</span><span class="sxs-lookup"><span data-stu-id="e20f0-102">Equality Operators</span></span>
<span data-ttu-id="e20f0-103">W tej sekcji omówiono przeciążanie operatorów równości i odwołuje się do nich `operator==` `operator!=` operator równości i.</span><span class="sxs-lookup"><span data-stu-id="e20f0-103">This section discusses overloading equality operators and refers to `operator==` and `operator!=` as equality operators.</span></span>

 <span data-ttu-id="e20f0-104">❌Nie należy przeciążać jednego z operatorów równości, a nie innych.</span><span class="sxs-lookup"><span data-stu-id="e20f0-104">❌ DO NOT overload one of the equality operators and not the other.</span></span>

 <span data-ttu-id="e20f0-105">✔️ Upewnij się, że <xref:System.Object.Equals%2A?displayProperty=nameWithType> Operatory równości mają dokładnie taką samą semantykę i podobną charakterystykę wydajności.</span><span class="sxs-lookup"><span data-stu-id="e20f0-105">✔️ DO ensure that <xref:System.Object.Equals%2A?displayProperty=nameWithType> and the equality operators have exactly the same semantics and similar performance characteristics.</span></span>

 <span data-ttu-id="e20f0-106">Często oznacza to, że należy `Object.Equals` je zastąpić, gdy operatory równości są przeciążone.</span><span class="sxs-lookup"><span data-stu-id="e20f0-106">This often means that `Object.Equals` needs to be overridden when the equality operators are overloaded.</span></span>

 <span data-ttu-id="e20f0-107">❌UNIKAj zgłaszania wyjątków od operatorów równości.</span><span class="sxs-lookup"><span data-stu-id="e20f0-107">❌ AVOID throwing exceptions from equality operators.</span></span>

 <span data-ttu-id="e20f0-108">Na przykład Zwróć wartość false, jeśli jeden z argumentów ma wartość null, a nie Przerzucanie `NullReferenceException` .</span><span class="sxs-lookup"><span data-stu-id="e20f0-108">For example, return false if one of the arguments is null instead of throwing `NullReferenceException`.</span></span>

## <a name="equality-operators-on-value-types"></a><span data-ttu-id="e20f0-109">Operatory równości w typach wartości</span><span class="sxs-lookup"><span data-stu-id="e20f0-109">Equality Operators on Value Types</span></span>
 <span data-ttu-id="e20f0-110">✔️ przeciążać operatory równości dla typów wartości, jeśli równość jest istotna.</span><span class="sxs-lookup"><span data-stu-id="e20f0-110">✔️ DO overload the equality operators on value types, if equality is meaningful.</span></span>

 <span data-ttu-id="e20f0-111">W większości języków programowania nie istnieje domyślna implementacja `operator==` dla typów wartości.</span><span class="sxs-lookup"><span data-stu-id="e20f0-111">In most programming languages, there is no default implementation of `operator==` for value types.</span></span>

## <a name="equality-operators-on-reference-types"></a><span data-ttu-id="e20f0-112">Operatory równości w typach referencyjnych</span><span class="sxs-lookup"><span data-stu-id="e20f0-112">Equality Operators on Reference Types</span></span>
 <span data-ttu-id="e20f0-113">❌UNIKAj przeciążania operatorów równości dla modyfikowalnych typów odwołań.</span><span class="sxs-lookup"><span data-stu-id="e20f0-113">❌ AVOID overloading equality operators on mutable reference types.</span></span>

 <span data-ttu-id="e20f0-114">Wiele języków ma wbudowane operatory równości dla typów referencyjnych.</span><span class="sxs-lookup"><span data-stu-id="e20f0-114">Many languages have built-in equality operators for reference types.</span></span> <span data-ttu-id="e20f0-115">Operatory wbudowane zwykle implementują równość odwołań, a wielu deweloperów jest przeważnie, gdy domyślne zachowanie zostanie zmienione na równość wartości.</span><span class="sxs-lookup"><span data-stu-id="e20f0-115">The built-in operators usually implement the reference equality, and many developers are surprised when the default behavior is changed to the value equality.</span></span>

 <span data-ttu-id="e20f0-116">Ten problem został skorygowany dla niezmiennego typu referencyjnego, ponieważ niezmienności znacznie trudniejsze do zauważenia różnicy między równośćmi referencyjnymi i równość wartości.</span><span class="sxs-lookup"><span data-stu-id="e20f0-116">This problem is mitigated for immutable reference types because immutability makes it much harder to notice the difference between reference equality and value equality.</span></span>

 <span data-ttu-id="e20f0-117">❌UNIKAj przeciążania operatorów równości w typach referencyjnych, jeśli implementacja będzie znacznie wolniejsza niż równość odwołania.</span><span class="sxs-lookup"><span data-stu-id="e20f0-117">❌ AVOID overloading equality operators on reference types if the implementation would be significantly slower than that of reference equality.</span></span>

 <span data-ttu-id="e20f0-118">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="e20f0-118">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="e20f0-119">*Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="e20f0-119">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="e20f0-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e20f0-120">See also</span></span>

- [<span data-ttu-id="e20f0-121">Wskazówki dotyczące projektowania struktury</span><span class="sxs-lookup"><span data-stu-id="e20f0-121">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="e20f0-122">Wskazówki dotyczące użycia</span><span class="sxs-lookup"><span data-stu-id="e20f0-122">Usage Guidelines</span></span>](usage-guidelines.md)
