---
title: Projektowanie pod kątem rozszerzalności
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- extending class libraries
- extensibility with class libraries in .NET Framework
- class library design guidelines [.NET Framework], extensibility
- class library extensibility [.NET Framework]
ms.assetid: 1cdb8740-871a-456c-9bd9-db96ca8d79b3
caps.latest.revision: 11
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b643c33a1418839c8aabf06d681083232e61553a
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="designing-for-extensibility"></a><span data-ttu-id="0ccc8-102">Projektowanie pod kątem rozszerzalności</span><span class="sxs-lookup"><span data-stu-id="0ccc8-102">Designing for Extensibility</span></span>
<span data-ttu-id="0ccc8-103">Ważnym aspektem Projektowanie struktury jest sprawdzanie, czy starannie przemyślane extensibility Framework.</span><span class="sxs-lookup"><span data-stu-id="0ccc8-103">One important aspect of designing a framework is making sure the extensibility of the framework has been carefully considered.</span></span> <span data-ttu-id="0ccc8-104">Wymaga to, że rozumiesz kosztów i korzyści związanych z różne mechanizmy rozszerzania.</span><span class="sxs-lookup"><span data-stu-id="0ccc8-104">This requires that you understand the costs and benefits associated with various extensibility mechanisms.</span></span> <span data-ttu-id="0ccc8-105">Ten rozdział pomaga w podjęciu decyzji, które mechanizmy rozszerzania — podklasy, zdarzenia wirtualne elementy członkowskie, wywołania zwrotne i tak dalej — mogą najlepiej spełnić wymagania Twojej platformy.</span><span class="sxs-lookup"><span data-stu-id="0ccc8-105">This chapter helps you decide which of the extensibility mechanisms—subclassing, events, virtual members, callbacks, and so on—can best meet the requirements of your framework.</span></span>  
  
 <span data-ttu-id="0ccc8-106">Istnieje wiele sposobów dozwolonych rozszerzalności w struktury.</span><span class="sxs-lookup"><span data-stu-id="0ccc8-106">There are many ways to allow extensibility in frameworks.</span></span> <span data-ttu-id="0ccc8-107">One należeć do zakresu od mniej wydajne, ale mniej kosztowne do bardzo zaawansowane, ale kosztowne.</span><span class="sxs-lookup"><span data-stu-id="0ccc8-107">They range from less powerful but less costly to very powerful but expensive.</span></span> <span data-ttu-id="0ccc8-108">Wszystkie wymagania danego rozszerzalności należy wybrać najmniej kosztowne mechanizm rozszerzalności, która spełnia wymagania.</span><span class="sxs-lookup"><span data-stu-id="0ccc8-108">For any given extensibility requirement, you should choose the least costly extensibility mechanism that meets the requirements.</span></span> <span data-ttu-id="0ccc8-109">Należy pamiętać, że jest zazwyczaj można później dodać więcej rozszerzeń, ale użytkownik może nigdy nie zabrać ją bez wprowadzania zmian, które psuły.</span><span class="sxs-lookup"><span data-stu-id="0ccc8-109">Keep in mind that it’s usually possible to add more extensibility later, but you can never take it away without introducing breaking changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0ccc8-110">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="0ccc8-110">In This Section</span></span>  
 [<span data-ttu-id="0ccc8-111">Niezapieczętowane klasy</span><span class="sxs-lookup"><span data-stu-id="0ccc8-111">Unsealed Classes</span></span>](../../../docs/standard/design-guidelines/unsealed-classes.md)  
 [<span data-ttu-id="0ccc8-112">Chronione elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="0ccc8-112">Protected Members</span></span>](../../../docs/standard/design-guidelines/protected-members.md)  
 [<span data-ttu-id="0ccc8-113">Zdarzenia i wywołania zwrotne</span><span class="sxs-lookup"><span data-stu-id="0ccc8-113">Events and Callbacks</span></span>](../../../docs/standard/design-guidelines/events-and-callbacks.md)  
 [<span data-ttu-id="0ccc8-114">Wirtualne elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="0ccc8-114">Virtual Members</span></span>](../../../docs/standard/design-guidelines/virtual-members.md)  
 [<span data-ttu-id="0ccc8-115">Abstrakcje (typy abstrakcyjne i interfejsy)</span><span class="sxs-lookup"><span data-stu-id="0ccc8-115">Abstractions (Abstract Types and Interfaces)</span></span>](../../../docs/standard/design-guidelines/abstractions-abstract-types-and-interfaces.md)  
 [<span data-ttu-id="0ccc8-116">Klasy bazowe na potrzeby implementowania abstrakcji</span><span class="sxs-lookup"><span data-stu-id="0ccc8-116">Base Classes for Implementing Abstractions</span></span>](../../../docs/standard/design-guidelines/base-classes-for-implementing-abstractions.md)  
 [<span data-ttu-id="0ccc8-117">Pieczętowanie</span><span class="sxs-lookup"><span data-stu-id="0ccc8-117">Sealing</span></span>](../../../docs/standard/design-guidelines/sealing.md)  
 <span data-ttu-id="0ccc8-118">*Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="0ccc8-118">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="0ccc8-119">*Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="0ccc8-119">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ccc8-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0ccc8-120">See Also</span></span>  
 [<span data-ttu-id="0ccc8-121">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="0ccc8-121">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
