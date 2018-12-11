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
author: KrzysztofCwalina
ms.openlocfilehash: ae188fc7cd55dd843e93afccbe1ea05575a9c36d
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53129080"
---
# <a name="equality-operators"></a><span data-ttu-id="aca50-102">Operatory równości</span><span class="sxs-lookup"><span data-stu-id="aca50-102">Equality Operators</span></span>
<span data-ttu-id="aca50-103">W tej sekcji omówiono przeciążania operacji równości operatorów i odwołuje się do `operator==` i `operator!=` jako operatory równości.</span><span class="sxs-lookup"><span data-stu-id="aca50-103">This section discusses overloading equality operators and refers to `operator==` and `operator!=` as equality operators.</span></span>  
  
 <span data-ttu-id="aca50-104">**X DO NOT** jedną Operatory równości i nie inne przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="aca50-104">**X DO NOT** overload one of the equality operators and not the other.</span></span>  
  
 <span data-ttu-id="aca50-105">**✓ DO** upewnij się, że <xref:System.Object.Equals%2A?displayProperty=nameWithType> i operatory porównania ma dokładnie tej samej semantyki i podobne charakterystyki wydajności.</span><span class="sxs-lookup"><span data-stu-id="aca50-105">**✓ DO** ensure that <xref:System.Object.Equals%2A?displayProperty=nameWithType> and the equality operators have exactly the same semantics and similar performance characteristics.</span></span>  
  
 <span data-ttu-id="aca50-106">Często oznacza to, że `Object.Equals` musi zostać zastąpiona, gdy są przeciążone operatory równości.</span><span class="sxs-lookup"><span data-stu-id="aca50-106">This often means that `Object.Equals` needs to be overridden when the equality operators are overloaded.</span></span>  
  
 <span data-ttu-id="aca50-107">**X AVOID** zgłaszanie wyjątków z Operatory równości.</span><span class="sxs-lookup"><span data-stu-id="aca50-107">**X AVOID** throwing exceptions from equality operators.</span></span>  
  
 <span data-ttu-id="aca50-108">Na przykład, zwróci wartość false, jeśli jeden z argumentów ma wartość null, zamiast zgłaszać `NullReferenceException`.</span><span class="sxs-lookup"><span data-stu-id="aca50-108">For example, return false if one of the arguments is null instead of throwing `NullReferenceException`.</span></span>  
  
## <a name="equality-operators-on-value-types"></a><span data-ttu-id="aca50-109">Operatory równości dla typów wartości</span><span class="sxs-lookup"><span data-stu-id="aca50-109">Equality Operators on Value Types</span></span>  
 <span data-ttu-id="aca50-110">**✓ DO** przeciążać Operatory równości w typach wartości, jeśli równości jest łatwy do rozpoznania.</span><span class="sxs-lookup"><span data-stu-id="aca50-110">**✓ DO** overload the equality operators on value types, if equality is meaningful.</span></span>  
  
 <span data-ttu-id="aca50-111">W większości języków programowania, jest nie domyślną implementację elementu `operator==` dla typów wartości.</span><span class="sxs-lookup"><span data-stu-id="aca50-111">In most programming languages, there is no default implementation of `operator==` for value types.</span></span>  
  
## <a name="equality-operators-on-reference-types"></a><span data-ttu-id="aca50-112">Operatory równości w typach referencyjnych</span><span class="sxs-lookup"><span data-stu-id="aca50-112">Equality Operators on Reference Types</span></span>  
 <span data-ttu-id="aca50-113">**X AVOID** przeładowanie operatorów równości w typach referencyjnych.</span><span class="sxs-lookup"><span data-stu-id="aca50-113">**X AVOID** overloading equality operators on mutable reference types.</span></span>  
  
 <span data-ttu-id="aca50-114">Wiele języków mają wbudowane równości operatorów dla typów odwołań.</span><span class="sxs-lookup"><span data-stu-id="aca50-114">Many languages have built-in equality operators for reference types.</span></span> <span data-ttu-id="aca50-115">Wbudowane operatory zwykle implementuje równości odwołań i wielu deweloperów są Zaskoczenie, w przypadku zmiany domyślnego zachowania na równość wartości.</span><span class="sxs-lookup"><span data-stu-id="aca50-115">The built-in operators usually implement the reference equality, and many developers are surprised when the default behavior is changed to the value equality.</span></span>  
  
 <span data-ttu-id="aca50-116">Ten problem jest zmniejszany dla typów odwołań niezmienne, ponieważ niezmienności sprawia, że znacznie trudniejsze, zwróć uwagę na różnicę między równości odwołań i równości wartości.</span><span class="sxs-lookup"><span data-stu-id="aca50-116">This problem is mitigated for immutable reference types because immutability makes it much harder to notice the difference between reference equality and value equality.</span></span>  
  
 <span data-ttu-id="aca50-117">**X AVOID** przeładowanie operatorów równości w typach referencyjnych, jeśli implementacja będzie znacznie mniejsza niż w przypadku równości odwołań.</span><span class="sxs-lookup"><span data-stu-id="aca50-117">**X AVOID** overloading equality operators on reference types if the implementation would be significantly slower than that of reference equality.</span></span>  
  
 <span data-ttu-id="aca50-118">*Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="aca50-118">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="aca50-119">*Przedrukowano za uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: Konwencje, Idiomy i wzorców dla wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams publikowane 22 Oct 2008 przez Addison Wesley Professional w ramach serii rozwoju Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="aca50-119">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aca50-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aca50-120">See also</span></span>

- [<span data-ttu-id="aca50-121">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="aca50-121">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
- [<span data-ttu-id="aca50-122">Zalecenia dotyczące użytkowania</span><span class="sxs-lookup"><span data-stu-id="aca50-122">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)
