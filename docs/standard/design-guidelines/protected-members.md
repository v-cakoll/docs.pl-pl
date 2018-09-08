---
title: Chronione elementy członkowskie
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- members [.NET Framework], protected
- protected members
- classes [.NET Framework], unsealed
- classes [.NET Framework], protected members
- unsealed classes
- customizing class behavior
ms.assetid: aa0b58ee-3956-494d-ab48-471ae5db8740
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4574dffc3f9dd1b60d655bfde33a4ddc1a81d350
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44199742"
---
# <a name="protected-members"></a><span data-ttu-id="ea9ba-102">Chronione elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="ea9ba-102">Protected Members</span></span>
<span data-ttu-id="ea9ba-103">Chronione elementy członkowskie samodzielnie nie oferuje żadnych rozszerzeń, ale mogą robić więjsze rozszerzona funkcjonalność dzięki podklasy bardziej wydajne.</span><span class="sxs-lookup"><span data-stu-id="ea9ba-103">Protected members by themselves do not provide any extensibility, but they can make extensibility through subclassing more powerful.</span></span> <span data-ttu-id="ea9ba-104">One może służyć do udostępnienia Dostosowywanie zaawansowane opcje bez niepotrzebnego komplikowania kodu języka głównego interfejsu publicznego.</span><span class="sxs-lookup"><span data-stu-id="ea9ba-104">They can be used to expose advanced customization options without unnecessarily complicating the main public interface.</span></span>  
  
 <span data-ttu-id="ea9ba-105">Projektanci Framework, należy być ostrożnym z chronionych elementów członkowskich, ponieważ nazwa "protected" można nadać fałszywe poczucie bezpieczeństwa.</span><span class="sxs-lookup"><span data-stu-id="ea9ba-105">Framework designers need to be careful with protected members because the name "protected" can give a false sense of security.</span></span> <span data-ttu-id="ea9ba-106">Każda osoba ma możliwość podklasy niezapieczętowane klasy i dostęp do chronionych elementów członkowskich, a więc ten sam bezpiecznego kodowania, używane do publicznych elementów członkowskich dotyczą chronionych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="ea9ba-106">Anyone is able to subclass an unsealed class and access protected members, and so all the same defensive coding practices used for public members apply to protected members.</span></span>  
  
 <span data-ttu-id="ea9ba-107">**✓ CONSIDER** przy użyciu chronione elementy członkowskie dostosowania zaawansowanego.</span><span class="sxs-lookup"><span data-stu-id="ea9ba-107">**✓ CONSIDER** using protected members for advanced customization.</span></span>  
  
 <span data-ttu-id="ea9ba-108">**✓ DO** Traktuj chronionych elementów członkowskich w klasach otwarty jako public na potrzeby analizy zabezpieczeń, dokumentacji i zgodności.</span><span class="sxs-lookup"><span data-stu-id="ea9ba-108">**✓ DO** treat protected members in unsealed classes as public for the purpose of security, documentation, and compatibility analysis.</span></span>  
  
 <span data-ttu-id="ea9ba-109">Każdy może dziedziczyć z klasy i dostęp do chronionych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="ea9ba-109">Anyone can inherit from a class and access the protected members.</span></span>  
  
 <span data-ttu-id="ea9ba-110">*Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="ea9ba-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="ea9ba-111">*Przedrukowano przez uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: konwencje Idiomy i wzorce wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams opublikowane 22 Oct 2008 przez Professional Addison Wesley jako część serii rozwoju Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="ea9ba-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea9ba-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ea9ba-112">See also</span></span>

- [<span data-ttu-id="ea9ba-113">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="ea9ba-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
- [<span data-ttu-id="ea9ba-114">Projektowanie pod kątem rozszerzalności</span><span class="sxs-lookup"><span data-stu-id="ea9ba-114">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
