---
title: Wirtualne składowe
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- overridable members
- virtual members
- members [.NET Framework], virtual
ms.assetid: 8ff4eb97-0364-43ec-8a02-934b5cd94d19
ms.openlocfilehash: 918208bb44f84988b7fe903c589e82c7bf1f59e3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620771"
---
# <a name="virtual-members"></a><span data-ttu-id="a63a1-102">Wirtualne składowe</span><span class="sxs-lookup"><span data-stu-id="a63a1-102">Virtual Members</span></span>
<span data-ttu-id="a63a1-103">Wirtualne elementy członkowskie można przesłonić, zmieniając zachowanie podklasy.</span><span class="sxs-lookup"><span data-stu-id="a63a1-103">Virtual members can be overridden, thus changing the behavior of the subclass.</span></span> <span data-ttu-id="a63a1-104">Są one bardzo podobne do wywołania zwrotnego pod względem rozszerzalności, które zapewnia, ale są lepsze pod względem wydajności i zużycia pamięci.</span><span class="sxs-lookup"><span data-stu-id="a63a1-104">They are quite similar to callbacks in terms of the extensibility they provide, but they are better in terms of execution performance and memory consumption.</span></span> <span data-ttu-id="a63a1-105">Ponadto wirtualne elementy członkowskie działają bardziej naturalnie w scenariuszach, które wymagają utworzenia specjalnego rodzaju istniejącego typu (specjalizacji).</span><span class="sxs-lookup"><span data-stu-id="a63a1-105">Also, virtual members feel more natural in scenarios that require creating a special kind of an existing type (specialization).</span></span>

 <span data-ttu-id="a63a1-106">Wirtualne elementy członkowskie działają lepiej niż wywołania zwrotne i zdarzenia, ale nie wykonują lepszych możliwości niż w przypadku metod innych niż wirtualne.</span><span class="sxs-lookup"><span data-stu-id="a63a1-106">Virtual members perform better than callbacks and events, but do not perform better than non-virtual methods.</span></span>

 <span data-ttu-id="a63a1-107">Główna wada wirtualnych elementów członkowskich polega na tym, że zachowanie wirtualnej składowej może być modyfikowane tylko w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="a63a1-107">The main disadvantage of virtual members is that the behavior of a virtual member can only be modified at the time of compilation.</span></span> <span data-ttu-id="a63a1-108">Zachowanie wywołania zwrotnego można modyfikować w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="a63a1-108">The behavior of a callback can be modified at runtime.</span></span>

 <span data-ttu-id="a63a1-109">Wirtualne elementy członkowskie, takie jak wywołania zwrotne (i mogą być większe niż wywołania zwrotne), są kosztowne do projektowania, testowania i konserwowania, ponieważ każde wywołanie elementu wirtualnego można przesłonić w sposób nieprzewidywalny i można wykonać dowolny kod.</span><span class="sxs-lookup"><span data-stu-id="a63a1-109">Virtual members, like callbacks (and maybe more than callbacks), are costly to design, test, and maintain because any call to a virtual member can be overridden in unpredictable ways and can execute arbitrary code.</span></span> <span data-ttu-id="a63a1-110">Ponadto zwykle wymagane jest wyraźne określenie kontraktu wirtualnych elementów członkowskich, dzięki czemu koszt projektowania i dokumentowania jest wyższy.</span><span class="sxs-lookup"><span data-stu-id="a63a1-110">Also, much more effort is usually required to clearly define the contract of virtual members, so the cost of designing and documenting them is higher.</span></span>

 <span data-ttu-id="a63a1-111">❌NIE należy tworzyć elementów członkowskich wirtualnych, chyba że jest to dobry powód i masz świadomość wszystkich kosztów związanych z projektowaniem, testowaniem i utrzymywaniem wirtualnych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="a63a1-111">❌ DO NOT make members virtual unless you have a good reason to do so and you are aware of all the costs related to designing, testing, and maintaining virtual members.</span></span>

 <span data-ttu-id="a63a1-112">Wirtualne elementy członkowskie są mniej łagodniejszej pod względem zmian, które mogą być w nich przeznaczone bez przerywania zgodności.</span><span class="sxs-lookup"><span data-stu-id="a63a1-112">Virtual members are less forgiving in terms of changes that can be made to them without breaking compatibility.</span></span> <span data-ttu-id="a63a1-113">Ponadto są one wolniejsze niż wirtualne elementy członkowskie, głównie ponieważ wywołania wirtualnych elementów członkowskich nie są wbudowane.</span><span class="sxs-lookup"><span data-stu-id="a63a1-113">Also, they are slower than non-virtual members, mostly because calls to virtual members are not inlined.</span></span>

 <span data-ttu-id="a63a1-114">✔️ ROZWAŻYĆ ograniczenie rozszerzalności tylko do tego, co jest absolutnie niezbędne.</span><span class="sxs-lookup"><span data-stu-id="a63a1-114">✔️ CONSIDER limiting extensibility to only what is absolutely necessary.</span></span>

 <span data-ttu-id="a63a1-115">✔️ Preferuj ochronę chronioną za pośrednictwem publicznej dostępności dla wirtualnych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="a63a1-115">✔️ DO prefer protected accessibility over public accessibility for virtual members.</span></span> <span data-ttu-id="a63a1-116">Publiczne składowe powinny zapewnić rozszerzalność (jeśli jest to wymagane), wywołując do chronionej wirtualnej składowej.</span><span class="sxs-lookup"><span data-stu-id="a63a1-116">Public members should provide extensibility (if required) by calling into a protected virtual member.</span></span>

 <span data-ttu-id="a63a1-117">Publiczne składowe klasy powinny zapewnić odpowiedni zestaw funkcji dla bezpośrednich odbiorców tej klasy.</span><span class="sxs-lookup"><span data-stu-id="a63a1-117">The public members of a class should provide the right set of functionality for direct consumers of that class.</span></span> <span data-ttu-id="a63a1-118">Wirtualne elementy członkowskie zostały zaprojektowane do przesłania w podklasach, a funkcja chronionej dostępności to świetny sposób określania zakresu wszystkich wirtualnych punktów rozszerzalności, gdzie mogą być używane.</span><span class="sxs-lookup"><span data-stu-id="a63a1-118">Virtual members are designed to be overridden in subclasses, and protected accessibility is a great way to scope all virtual extensibility points to where they can be used.</span></span>

 <span data-ttu-id="a63a1-119">*Fragmenty &copy; 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="a63a1-119">*Portions &copy; 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="a63a1-120">*Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="a63a1-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="a63a1-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a63a1-121">See also</span></span>

- [<span data-ttu-id="a63a1-122">Wskazówki dotyczące projektowania struktury</span><span class="sxs-lookup"><span data-stu-id="a63a1-122">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="a63a1-123">Projektowanie pod kątem rozszerzalności</span><span class="sxs-lookup"><span data-stu-id="a63a1-123">Designing for Extensibility</span></span>](designing-for-extensibility.md)
