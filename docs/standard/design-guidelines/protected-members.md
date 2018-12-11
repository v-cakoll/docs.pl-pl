---
title: Chronione elementy członkowskie
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- members [.NET Framework], protected
- protected members
- classes [.NET Framework], unsealed
- classes [.NET Framework], protected members
- unsealed classes
- customizing class behavior
ms.assetid: aa0b58ee-3956-494d-ab48-471ae5db8740
author: KrzysztofCwalina
ms.openlocfilehash: f0ad21f0a5b869332223d96991dd0a7bebeba420
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53149357"
---
# <a name="protected-members"></a><span data-ttu-id="26da1-102">Chronione elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="26da1-102">Protected Members</span></span>
<span data-ttu-id="26da1-103">Chronione elementy członkowskie samodzielnie nie oferuje żadnych rozszerzeń, ale mogą robić więjsze rozszerzona funkcjonalność dzięki podklasy bardziej wydajne.</span><span class="sxs-lookup"><span data-stu-id="26da1-103">Protected members by themselves do not provide any extensibility, but they can make extensibility through subclassing more powerful.</span></span> <span data-ttu-id="26da1-104">One może służyć do udostępnienia Dostosowywanie zaawansowane opcje bez niepotrzebnego komplikowania kodu języka głównego interfejsu publicznego.</span><span class="sxs-lookup"><span data-stu-id="26da1-104">They can be used to expose advanced customization options without unnecessarily complicating the main public interface.</span></span>  
  
 <span data-ttu-id="26da1-105">Projektanci Framework, należy być ostrożnym z chronionych elementów członkowskich, ponieważ nazwa "protected" można nadać fałszywe poczucie bezpieczeństwa.</span><span class="sxs-lookup"><span data-stu-id="26da1-105">Framework designers need to be careful with protected members because the name "protected" can give a false sense of security.</span></span> <span data-ttu-id="26da1-106">Każda osoba ma możliwość podklasy niezapieczętowane klasy i dostęp do chronionych elementów członkowskich, a więc ten sam bezpiecznego kodowania, używane do publicznych elementów członkowskich dotyczą chronionych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="26da1-106">Anyone is able to subclass an unsealed class and access protected members, and so all the same defensive coding practices used for public members apply to protected members.</span></span>  
  
 <span data-ttu-id="26da1-107">**✓ CONSIDER** przy użyciu chronione elementy członkowskie dostosowania zaawansowanego.</span><span class="sxs-lookup"><span data-stu-id="26da1-107">**✓ CONSIDER** using protected members for advanced customization.</span></span>  
  
 <span data-ttu-id="26da1-108">**✓ DO** Traktuj chronionych elementów członkowskich w klasach otwarty jako public na potrzeby analizy zabezpieczeń, dokumentacji i zgodności.</span><span class="sxs-lookup"><span data-stu-id="26da1-108">**✓ DO** treat protected members in unsealed classes as public for the purpose of security, documentation, and compatibility analysis.</span></span>  
  
 <span data-ttu-id="26da1-109">Każdy może dziedziczyć z klasy i dostęp do chronionych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="26da1-109">Anyone can inherit from a class and access the protected members.</span></span>  
  
 <span data-ttu-id="26da1-110">*Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="26da1-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="26da1-111">*Przedrukowano za uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: Konwencje, Idiomy i wzorców dla wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams publikowane 22 Oct 2008 przez Addison Wesley Professional w ramach serii rozwoju Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="26da1-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26da1-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="26da1-112">See also</span></span>

- [<span data-ttu-id="26da1-113">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="26da1-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
- [<span data-ttu-id="26da1-114">Projektowanie pod kątem rozszerzalności</span><span class="sxs-lookup"><span data-stu-id="26da1-114">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
