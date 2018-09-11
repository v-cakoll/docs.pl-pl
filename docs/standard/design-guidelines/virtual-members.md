---
title: Wirtualne elementy członkowskie
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- overridable members
- virtual members
- members [.NET Framework], virtual
ms.assetid: 8ff4eb97-0364-43ec-8a02-934b5cd94d19
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b92b648e7886fb0214238e32eacae2870b470340
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44262623"
---
# <a name="virtual-members"></a><span data-ttu-id="8cec1-102">Wirtualne elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="8cec1-102">Virtual Members</span></span>
<span data-ttu-id="8cec1-103">Wirtualne elementy członkowskie można zastąpić, zmieniając w ten sposób zachowanie podklasy.</span><span class="sxs-lookup"><span data-stu-id="8cec1-103">Virtual members can be overridden, thus changing the behavior of the subclass.</span></span> <span data-ttu-id="8cec1-104">Są bardzo podobne do wywołania zwrotne pod kątem rozszerzalności, które zapewniają one, ale są one lepsze pod względem wydajności wykonywania i zużycie pamięci.</span><span class="sxs-lookup"><span data-stu-id="8cec1-104">They are quite similar to callbacks in terms of the extensibility they provide, but they are better in terms of execution performance and memory consumption.</span></span> <span data-ttu-id="8cec1-105">Ponadto wirtualnych elementów członkowskich czuć się bardziej naturalne w scenariuszach wymagających tworzenia specjalnego rodzaju istniejącego typu (Specjalizacja).</span><span class="sxs-lookup"><span data-stu-id="8cec1-105">Also, virtual members feel more natural in scenarios that require creating a special kind of an existing type (specialization).</span></span>  
  
 <span data-ttu-id="8cec1-106">Wirtualne elementy członkowskie mają lepszą wydajność niż wywołania zwrotne i zdarzenia, ale nie mają lepszą wydajność niż metod niewirtualnych.</span><span class="sxs-lookup"><span data-stu-id="8cec1-106">Virtual members perform better than callbacks and events, but do not perform better than non-virtual methods.</span></span>  
  
 <span data-ttu-id="8cec1-107">Główną wadą wirtualnych elementów członkowskich jest, że zachowanie wirtualny element członkowski może być modyfikowane tylko w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="8cec1-107">The main disadvantage of virtual members is that the behavior of a virtual member can only be modified at the time of compilation.</span></span> <span data-ttu-id="8cec1-108">Można zmodyfikować zachowanie wywołanie zwrotne w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="8cec1-108">The behavior of a callback can be modified at runtime.</span></span>  
  
 <span data-ttu-id="8cec1-109">Wirtualne elementy członkowskie, takie jak wywołania zwrotne i może być większa niż wywołań zwrotnych, są kosztowne do projektowania, testowania i obsługi, ponieważ każde wywołanie wirtualny element członkowski może zostać przesłonięta w sposób nieprzewidziany i może wykonywać dowolny kod.</span><span class="sxs-lookup"><span data-stu-id="8cec1-109">Virtual members, like callbacks (and maybe more than callbacks), are costly to design, test, and maintain because any call to a virtual member can be overridden in unpredictable ways and can execute arbitrary code.</span></span> <span data-ttu-id="8cec1-110">Ponadto znacznie więcej nakładu pracy zwykle jest wymagany do jasno zdefiniować kontrakt wirtualnych elementów członkowskich, więc koszt projektowania i dokumentowanie ich jest wyższy.</span><span class="sxs-lookup"><span data-stu-id="8cec1-110">Also, much more effort is usually required to clearly define the contract of virtual members, so the cost of designing and documenting them is higher.</span></span>  
  
 <span data-ttu-id="8cec1-111">**X DO NOT** tworzenie elementów członkowskich wirtualnego, chyba że masz powód, dla zrobić i poznać wszystkich kosztów związanych z projektowania i testowania oraz Obsługa wirtualnych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="8cec1-111">**X DO NOT** make members virtual unless you have a good reason to do so and you are aware of all the costs related to designing, testing, and maintaining virtual members.</span></span>  
  
 <span data-ttu-id="8cec1-112">Wirtualne elementy członkowskie są mniej forgiving pod względem zmiany wprowadzone do nich w bez przerywania zgodność.</span><span class="sxs-lookup"><span data-stu-id="8cec1-112">Virtual members are less forgiving in terms of changes that can be made to them without breaking compatibility.</span></span> <span data-ttu-id="8cec1-113">Ponadto są wolniejsze niż niewirtualną członków, przede wszystkim, ponieważ wywołania wirtualne elementy członkowskie nie są śródwierszowych.</span><span class="sxs-lookup"><span data-stu-id="8cec1-113">Also, they are slower than non-virtual members, mostly because calls to virtual members are not inlined.</span></span>  
  
 <span data-ttu-id="8cec1-114">**✓ CONSIDER** ograniczanie rozszerzalności tylko co to jest bezwzględnie konieczne.</span><span class="sxs-lookup"><span data-stu-id="8cec1-114">**✓ CONSIDER** limiting extensibility to only what is absolutely necessary.</span></span>  
  
 <span data-ttu-id="8cec1-115">**✓ DO** Preferuj dostępności chronione przed powszechnej dostępności dla wirtualnych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="8cec1-115">**✓ DO** prefer protected accessibility over public accessibility for virtual members.</span></span> <span data-ttu-id="8cec1-116">Publiczne elementy Członkowskie powinny rozszerzalność (jeśli jest to wymagane) przez wywołanie chronionych wirtualna elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="8cec1-116">Public members should provide extensibility (if required) by calling into a protected virtual member.</span></span>  
  
 <span data-ttu-id="8cec1-117">Publiczne elementy członkowskie klasy dostarczają właściwy zestaw funkcji dla bezpośrednich klientów tej klasy.</span><span class="sxs-lookup"><span data-stu-id="8cec1-117">The public members of a class should provide the right set of functionality for direct consumers of that class.</span></span> <span data-ttu-id="8cec1-118">Wirtualne elementy członkowskie są przeznaczone do zastąpienia w podklasy i chronionych ułatwień dostępu jest to doskonały sposób, aby ograniczyć zakres wszystkie punkty rozszerzalności wirtualny, gdzie mogą być używane do.</span><span class="sxs-lookup"><span data-stu-id="8cec1-118">Virtual members are designed to be overridden in subclasses, and protected accessibility is a great way to scope all virtual extensibility points to where they can be used.</span></span>  
  
 <span data-ttu-id="8cec1-119">*Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="8cec1-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="8cec1-120">*Przedrukowano przez uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: konwencje Idiomy i wzorce wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams opublikowane 22 Oct 2008 przez Professional Addison Wesley jako część serii rozwoju Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="8cec1-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cec1-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8cec1-121">See also</span></span>

- [<span data-ttu-id="8cec1-122">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="8cec1-122">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
- [<span data-ttu-id="8cec1-123">Projektowanie pod kątem rozszerzalności</span><span class="sxs-lookup"><span data-stu-id="8cec1-123">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
