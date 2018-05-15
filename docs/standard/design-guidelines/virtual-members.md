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
ms.openlocfilehash: fa4227fc4476b86f07216650b22fccc25af7dd98
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="virtual-members"></a><span data-ttu-id="bed66-102">Wirtualne elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="bed66-102">Virtual Members</span></span>
<span data-ttu-id="bed66-103">Wirtualne elementy Członkowskie mogą zostać zastąpione, w związku z tym zmiany zachowania podklasy.</span><span class="sxs-lookup"><span data-stu-id="bed66-103">Virtual members can be overridden, thus changing the behavior of the subclass.</span></span> <span data-ttu-id="bed66-104">Są bardzo podobne do wywołania zwrotne pod względem rozszerzania, które zapewniają, ale są one lepsze pod względem wydajności wykonywania i zmniejszenie zużycia pamięci.</span><span class="sxs-lookup"><span data-stu-id="bed66-104">They are quite similar to callbacks in terms of the extensibility they provide, but they are better in terms of execution performance and memory consumption.</span></span> <span data-ttu-id="bed66-105">Ponadto wirtualne elementy członkowskie możesz bardziej naturalne w scenariuszach wymagających tworzenie specjalny rodzaj istniejącego typu (Specjalizacja).</span><span class="sxs-lookup"><span data-stu-id="bed66-105">Also, virtual members feel more natural in scenarios that require creating a special kind of an existing type (specialization).</span></span>  
  
 <span data-ttu-id="bed66-106">Wirtualne elementy członkowskie lepiej niż wywołania zwrotne i zdarzeń, ale nie wykonuj lepiej niż metody-virtual.</span><span class="sxs-lookup"><span data-stu-id="bed66-106">Virtual members perform better than callbacks and events, but do not perform better than non-virtual methods.</span></span>  
  
 <span data-ttu-id="bed66-107">Główną wadą wirtualnych elementów członkowskich jest, że zachowanie elementu członkowskiego wirtualnego można modyfikować tylko w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="bed66-107">The main disadvantage of virtual members is that the behavior of a virtual member can only be modified at the time of compilation.</span></span> <span data-ttu-id="bed66-108">Zachowanie wywołania zwrotnego może być modyfikowany w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="bed66-108">The behavior of a callback can be modified at runtime.</span></span>  
  
 <span data-ttu-id="bed66-109">Wirtualne elementy członkowskie, takie jak wywołania zwrotne i może być większa niż wywołań zwrotnych, są kosztowne do projektowania, testowania i konserwacji, ponieważ jakiekolwiek odwołania do elementu członkowskiego wirtualnego może zostać zastąpiona w sposób nieprzewidziany i może zostać uruchomiony dowolny kod.</span><span class="sxs-lookup"><span data-stu-id="bed66-109">Virtual members, like callbacks (and maybe more than callbacks), are costly to design, test, and maintain because any call to a virtual member can be overridden in unpredictable ways and can execute arbitrary code.</span></span> <span data-ttu-id="bed66-110">Ponadto znacznie więcej wysiłku jest zazwyczaj wymagane jasno zdefiniować kontrakt wirtualne elementy członkowskie, więc koszt projektowanie i dokumentowanie ich jest wyższy.</span><span class="sxs-lookup"><span data-stu-id="bed66-110">Also, much more effort is usually required to clearly define the contract of virtual members, so the cost of designing and documenting them is higher.</span></span>  
  
 <span data-ttu-id="bed66-111">**X nie** tworzenie elementów członkowskich wirtualnego, chyba że masz powód, dla zrobić i poznać wszystkich kosztów związanych z projektowania i testowania oraz Obsługa wirtualnych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="bed66-111">**X DO NOT** make members virtual unless you have a good reason to do so and you are aware of all the costs related to designing, testing, and maintaining virtual members.</span></span>  
  
 <span data-ttu-id="bed66-112">Wirtualne elementy członkowskie są mniej forgiving pod względem zmiany wprowadzone do nich w bez przerywania zgodności.</span><span class="sxs-lookup"><span data-stu-id="bed66-112">Virtual members are less forgiving in terms of changes that can be made to them without breaking compatibility.</span></span> <span data-ttu-id="bed66-113">Ponadto są one wolniej niż członków-virtual, przede wszystkim, ponieważ wywołania wirtualne elementy członkowskie nie są wbudowane.</span><span class="sxs-lookup"><span data-stu-id="bed66-113">Also, they are slower than non-virtual members, mostly because calls to virtual members are not inlined.</span></span>  
  
 <span data-ttu-id="bed66-114">**ROZWAŻ ✓** ograniczanie rozszerzalności tylko co to jest bezwzględnie konieczne.</span><span class="sxs-lookup"><span data-stu-id="bed66-114">**✓ CONSIDER** limiting extensibility to only what is absolutely necessary.</span></span>  
  
 <span data-ttu-id="bed66-115">**CZY ✓** Preferuj dostępności chronione przed powszechnej dostępności dla wirtualnych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="bed66-115">**✓ DO** prefer protected accessibility over public accessibility for virtual members.</span></span> <span data-ttu-id="bed66-116">Publiczne elementy Członkowskie powinny rozszerzalność (jeśli jest to wymagane) przez wywołanie do chronionego członka wirtualnego.</span><span class="sxs-lookup"><span data-stu-id="bed66-116">Public members should provide extensibility (if required) by calling into a protected virtual member.</span></span>  
  
 <span data-ttu-id="bed66-117">Publiczne elementy członkowskie klasy powinien zapewnić prawidłowego zestawu funkcji do bezpośredniego konsumentów tej klasy.</span><span class="sxs-lookup"><span data-stu-id="bed66-117">The public members of a class should provide the right set of functionality for direct consumers of that class.</span></span> <span data-ttu-id="bed66-118">Wirtualne elementy członkowskie zaprojektowano do zastąpienia w podklasach i dostępność chronionych jest to dobry sposób na zakres wszystkie punkty rozszerzalności wirtualnego, gdzie mogą być używane.</span><span class="sxs-lookup"><span data-stu-id="bed66-118">Virtual members are designed to be overridden in subclasses, and protected accessibility is a great way to scope all virtual extensibility points to where they can be used.</span></span>  
  
 <span data-ttu-id="bed66-119">*Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="bed66-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="bed66-120">*Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="bed66-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bed66-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bed66-121">See Also</span></span>  
 [<span data-ttu-id="bed66-122">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="bed66-122">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="bed66-123">Projektowanie pod kątem rozszerzalności</span><span class="sxs-lookup"><span data-stu-id="bed66-123">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
