---
title: Projektowanie pod kątem rozszerzalności
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- extending class libraries
- extensibility with class libraries in .NET Framework
- class library design guidelines [.NET Framework], extensibility
- class library extensibility [.NET Framework]
ms.assetid: 1cdb8740-871a-456c-9bd9-db96ca8d79b3
ms.openlocfilehash: cd5db2d1e299df1b3d0f706ebc507e6855b72505
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709468"
---
# <a name="designing-for-extensibility"></a><span data-ttu-id="596c6-102">Projektowanie pod kątem rozszerzalności</span><span class="sxs-lookup"><span data-stu-id="596c6-102">Designing for Extensibility</span></span>
<span data-ttu-id="596c6-103">Jednym z ważniejszych aspektów projektowania struktury jest upewnienie się, że rozszerzalność struktury jest starannie rozpatrywana.</span><span class="sxs-lookup"><span data-stu-id="596c6-103">One important aspect of designing a framework is making sure the extensibility of the framework has been carefully considered.</span></span> <span data-ttu-id="596c6-104">Wymaga to zrozumienia kosztów i korzyści związanych z różnymi mechanizmami rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="596c6-104">This requires that you understand the costs and benefits associated with various extensibility mechanisms.</span></span> <span data-ttu-id="596c6-105">Ten rozdział ułatwia podjęcie decyzji, które mechanizmy rozszerzalności — podklasy, zdarzenia, wirtualne elementy członkowskie, wywołania zwrotne i tak dalej — mogą najlepiej spełniać wymagania platformy.</span><span class="sxs-lookup"><span data-stu-id="596c6-105">This chapter helps you decide which of the extensibility mechanisms—subclassing, events, virtual members, callbacks, and so on—can best meet the requirements of your framework.</span></span>  
  
 <span data-ttu-id="596c6-106">Istnieje wiele sposobów na umożliwienie rozszerzalności w strukturach.</span><span class="sxs-lookup"><span data-stu-id="596c6-106">There are many ways to allow extensibility in frameworks.</span></span> <span data-ttu-id="596c6-107">Są one większe niż tańsze, ale tańsze, ale kosztowne.</span><span class="sxs-lookup"><span data-stu-id="596c6-107">They range from less powerful but less costly to very powerful but expensive.</span></span> <span data-ttu-id="596c6-108">W przypadku danego wymagania dotyczącego rozszerzalności należy wybrać najniższy, kosztowny mechanizm rozszerzania spełniający wymagania.</span><span class="sxs-lookup"><span data-stu-id="596c6-108">For any given extensibility requirement, you should choose the least costly extensibility mechanism that meets the requirements.</span></span> <span data-ttu-id="596c6-109">Należy pamiętać, że jest zwykle możliwe dodanie większej liczby rozszerzeń później, ale nigdy nie należy wprowadzać zmian.</span><span class="sxs-lookup"><span data-stu-id="596c6-109">Keep in mind that it’s usually possible to add more extensibility later, but you can never take it away without introducing breaking changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="596c6-110">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="596c6-110">In This Section</span></span>  
 [<span data-ttu-id="596c6-111">Niezapieczętowane klasy</span><span class="sxs-lookup"><span data-stu-id="596c6-111">Unsealed Classes</span></span>](../../../docs/standard/design-guidelines/unsealed-classes.md)  
 [<span data-ttu-id="596c6-112">Chronione elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="596c6-112">Protected Members</span></span>](../../../docs/standard/design-guidelines/protected-members.md)  
 [<span data-ttu-id="596c6-113">Zdarzenia i wywołania zwrotne</span><span class="sxs-lookup"><span data-stu-id="596c6-113">Events and Callbacks</span></span>](../../../docs/standard/design-guidelines/events-and-callbacks.md)  
 [<span data-ttu-id="596c6-114">Wirtualne elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="596c6-114">Virtual Members</span></span>](../../../docs/standard/design-guidelines/virtual-members.md)  
 [<span data-ttu-id="596c6-115">Abstrakcje (typy abstrakcyjne i interfejsy)</span><span class="sxs-lookup"><span data-stu-id="596c6-115">Abstractions (Abstract Types and Interfaces)</span></span>](../../../docs/standard/design-guidelines/abstractions-abstract-types-and-interfaces.md)  
 [<span data-ttu-id="596c6-116">Klasy bazowe na potrzeby implementowania abstrakcji</span><span class="sxs-lookup"><span data-stu-id="596c6-116">Base Classes for Implementing Abstractions</span></span>](../../../docs/standard/design-guidelines/base-classes-for-implementing-abstractions.md)  
 [<span data-ttu-id="596c6-117">Pieczętowanie</span><span class="sxs-lookup"><span data-stu-id="596c6-117">Sealing</span></span>](../../../docs/standard/design-guidelines/sealing.md)  
 <span data-ttu-id="596c6-118">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="596c6-118">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="596c6-119">*Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="596c6-119">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="596c6-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="596c6-120">See also</span></span>

- [<span data-ttu-id="596c6-121">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="596c6-121">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
