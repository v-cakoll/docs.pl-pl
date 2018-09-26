---
title: Projektowanie pod kątem rozszerzalności
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- extending class libraries
- extensibility with class libraries in .NET Framework
- class library design guidelines [.NET Framework], extensibility
- class library extensibility [.NET Framework]
ms.assetid: 1cdb8740-871a-456c-9bd9-db96ca8d79b3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9c1690d0cdf1f57eaf0a794d6e71babfa4fa6425
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47157457"
---
# <a name="designing-for-extensibility"></a><span data-ttu-id="ec8bc-102">Projektowanie pod kątem rozszerzalności</span><span class="sxs-lookup"><span data-stu-id="ec8bc-102">Designing for Extensibility</span></span>
<span data-ttu-id="ec8bc-103">Ważnym aspektem projektowania struktury jest upewnienie się, że starannie przemyślane extensibility Framework.</span><span class="sxs-lookup"><span data-stu-id="ec8bc-103">One important aspect of designing a framework is making sure the extensibility of the framework has been carefully considered.</span></span> <span data-ttu-id="ec8bc-104">Wymaga to, że rozumiesz, koszty i korzyści związanych z różnych mechanizmów rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="ec8bc-104">This requires that you understand the costs and benefits associated with various extensibility mechanisms.</span></span> <span data-ttu-id="ec8bc-105">Ten rozdział pomaga w podjęciu decyzji, które mechanizmy rozszerzania — podklasy, zdarzenia, wirtualnych elementów członkowskich, wywołania zwrotne i tak dalej, mogą najlepiej spełnić wymagania dotyczące platformy.</span><span class="sxs-lookup"><span data-stu-id="ec8bc-105">This chapter helps you decide which of the extensibility mechanisms—subclassing, events, virtual members, callbacks, and so on—can best meet the requirements of your framework.</span></span>  
  
 <span data-ttu-id="ec8bc-106">Istnieje wiele sposobów, aby umożliwić rozszerzalność w struktur.</span><span class="sxs-lookup"><span data-stu-id="ec8bc-106">There are many ways to allow extensibility in frameworks.</span></span> <span data-ttu-id="ec8bc-107">One w zakresie od mniej zaawansowane, ale mniej kosztowne do bardzo zaawansowanych, ale kosztowne.</span><span class="sxs-lookup"><span data-stu-id="ec8bc-107">They range from less powerful but less costly to very powerful but expensive.</span></span> <span data-ttu-id="ec8bc-108">Wszystkie wymagania danego rozszerzalności należy wybrać najtańsze mechanizm rozszerzalności, która spełnia wymagania.</span><span class="sxs-lookup"><span data-stu-id="ec8bc-108">For any given extensibility requirement, you should choose the least costly extensibility mechanism that meets the requirements.</span></span> <span data-ttu-id="ec8bc-109">Należy pamiętać, że zazwyczaj można później dodać więcej rozszerzeń, ale użytkownik może nigdy nie zabrać ją bez wprowadzania istotnych zmian.</span><span class="sxs-lookup"><span data-stu-id="ec8bc-109">Keep in mind that it’s usually possible to add more extensibility later, but you can never take it away without introducing breaking changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ec8bc-110">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="ec8bc-110">In This Section</span></span>  
 [<span data-ttu-id="ec8bc-111">Niezapieczętowane klasy</span><span class="sxs-lookup"><span data-stu-id="ec8bc-111">Unsealed Classes</span></span>](../../../docs/standard/design-guidelines/unsealed-classes.md)  
 [<span data-ttu-id="ec8bc-112">Chronione elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="ec8bc-112">Protected Members</span></span>](../../../docs/standard/design-guidelines/protected-members.md)  
 [<span data-ttu-id="ec8bc-113">Zdarzenia i wywołania zwrotne</span><span class="sxs-lookup"><span data-stu-id="ec8bc-113">Events and Callbacks</span></span>](../../../docs/standard/design-guidelines/events-and-callbacks.md)  
 [<span data-ttu-id="ec8bc-114">Wirtualne elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="ec8bc-114">Virtual Members</span></span>](../../../docs/standard/design-guidelines/virtual-members.md)  
 [<span data-ttu-id="ec8bc-115">Abstrakcje (typy abstrakcyjne i interfejsy)</span><span class="sxs-lookup"><span data-stu-id="ec8bc-115">Abstractions (Abstract Types and Interfaces)</span></span>](../../../docs/standard/design-guidelines/abstractions-abstract-types-and-interfaces.md)  
 [<span data-ttu-id="ec8bc-116">Klasy bazowe na potrzeby implementowania abstrakcji</span><span class="sxs-lookup"><span data-stu-id="ec8bc-116">Base Classes for Implementing Abstractions</span></span>](../../../docs/standard/design-guidelines/base-classes-for-implementing-abstractions.md)  
 [<span data-ttu-id="ec8bc-117">Pieczętowanie</span><span class="sxs-lookup"><span data-stu-id="ec8bc-117">Sealing</span></span>](../../../docs/standard/design-guidelines/sealing.md)  
 <span data-ttu-id="ec8bc-118">*Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="ec8bc-118">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="ec8bc-119">*Przedrukowano przez uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: konwencje Idiomy i wzorce wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams opublikowane 22 Oct 2008 przez Professional Addison Wesley jako część serii rozwoju Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="ec8bc-119">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec8bc-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ec8bc-120">See also</span></span>

- [<span data-ttu-id="ec8bc-121">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="ec8bc-121">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
