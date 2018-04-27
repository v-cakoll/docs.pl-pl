---
title: Chronione elementy członkowskie
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- members [.NET Framework], protected
- protected members
- classes [.NET Framework], unsealed
- classes [.NET Framework], protected members
- unsealed classes
- customizing class behavior
ms.assetid: aa0b58ee-3956-494d-ab48-471ae5db8740
caps.latest.revision: 9
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 00701ed1497587c5d436c869c119c7123dbc3f80
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="protected-members"></a><span data-ttu-id="5d08c-102">Chronione elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="5d08c-102">Protected Members</span></span>
<span data-ttu-id="5d08c-103">Chronione elementy członkowskie samodzielnie nie dostarcza żadnych rozszerzalności, ale może wprowadzić bardziej zaawansowanych rozszerzeń przez podklasy.</span><span class="sxs-lookup"><span data-stu-id="5d08c-103">Protected members by themselves do not provide any extensibility, but they can make extensibility through subclassing more powerful.</span></span> <span data-ttu-id="5d08c-104">One może służyć do udostępnienia opcje zaawansowane dostosowywanie bez niepotrzebnie komplikując głównego interfejs publiczny.</span><span class="sxs-lookup"><span data-stu-id="5d08c-104">They can be used to expose advanced customization options without unnecessarily complicating the main public interface.</span></span>  
  
 <span data-ttu-id="5d08c-105">Projektanci Framework konieczne należy zachować ostrożność przy chronionych elementów członkowskich, ponieważ nazwa "protected", który pozwala false rozumieniu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="5d08c-105">Framework designers need to be careful with protected members because the name "protected" can give a false sense of security.</span></span> <span data-ttu-id="5d08c-106">Każda osoba, która jest w stanie podklasą klasy niezapieczętowany i dostęp do chronionych elementów członkowskich, a więc te same obrony praktyk kodowania elementów publicznych dotyczą chronionych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="5d08c-106">Anyone is able to subclass an unsealed class and access protected members, and so all the same defensive coding practices used for public members apply to protected members.</span></span>  
  
 <span data-ttu-id="5d08c-107">**ROZWAŻ ✓** przy użyciu chronione elementy członkowskie dostosowania zaawansowanego.</span><span class="sxs-lookup"><span data-stu-id="5d08c-107">**✓ CONSIDER** using protected members for advanced customization.</span></span>  
  
 <span data-ttu-id="5d08c-108">**CZY ✓** Traktuj chronionych elementów członkowskich w klasach otwarty jako public na potrzeby analizy zabezpieczeń, dokumentacji i zgodności.</span><span class="sxs-lookup"><span data-stu-id="5d08c-108">**✓ DO** treat protected members in unsealed classes as public for the purpose of security, documentation, and compatibility analysis.</span></span>  
  
 <span data-ttu-id="5d08c-109">Każda osoba, która dziedziczy z klasy, a dostęp do chronionych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="5d08c-109">Anyone can inherit from a class and access the protected members.</span></span>  
  
 <span data-ttu-id="5d08c-110">*Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="5d08c-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="5d08c-111">*Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="5d08c-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d08c-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5d08c-112">See Also</span></span>  
 [<span data-ttu-id="5d08c-113">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="5d08c-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="5d08c-114">Projektowanie pod kątem rozszerzalności</span><span class="sxs-lookup"><span data-stu-id="5d08c-114">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
