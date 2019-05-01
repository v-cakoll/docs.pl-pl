---
title: Niezapieczętowane klasy
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- classes [.NET Framework], unsealed
- unsealed classes
- inheritance, classes
ms.assetid: 9a3bd505-90f5-4053-9f0d-3cf5fa3d3ebf
author: KrzysztofCwalina
ms.openlocfilehash: d7174de7ddf062b829672e04952c1010fcb74058
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61778797"
---
# <a name="unsealed-classes"></a><span data-ttu-id="995b1-102">Niezapieczętowane klasy</span><span class="sxs-lookup"><span data-stu-id="995b1-102">Unsealed Classes</span></span>
<span data-ttu-id="995b1-103">Zapieczętowane klasy nie może być dziedziczona z i zapobiegają one rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="995b1-103">Sealed classes cannot be inherited from, and they prevent extensibility.</span></span> <span data-ttu-id="995b1-104">Z kolei klas, które mogą być dziedziczone z są nazywane niezapieczętowane klasy.</span><span class="sxs-lookup"><span data-stu-id="995b1-104">In contrast, classes that can be inherited from are called unsealed classes.</span></span>  
  
 <span data-ttu-id="995b1-105">**✓ CONSIDER** przy użyciu niezapieczętowanych klas bez dodać wirtualnych lub chronionych elementów członkowskich, ponieważ doskonałym sposobem zapewnienia niedrogich jeszcze znacznie zwiększyć elastyczność w ramach.</span><span class="sxs-lookup"><span data-stu-id="995b1-105">**✓ CONSIDER** using unsealed classes with no added virtual or protected members as a great way to provide inexpensive yet much appreciated extensibility to a framework.</span></span>  
  
 <span data-ttu-id="995b1-106">Deweloperzy często ma być dziedziczona z niezapieczętowane klasy tak, aby dodać członków jako udogodnienie, takie jak niestandardowe konstruktorów, nowych metod lub przeciążenia metody.</span><span class="sxs-lookup"><span data-stu-id="995b1-106">Developers often want to inherit from unsealed classes so as to add convenience members such as custom constructors, new methods, or method overloads.</span></span> <span data-ttu-id="995b1-107">Na przykład `System.Messaging.MessageQueue` jest niezapieczętowany, dlatego. Umożliwia ono użytkownikom tworzenie niestandardowych kolejek tej wartości domyślnej ścieżki określonej kolejki lub dodawanie metod niestandardowych, które upraszczają interfejs API dla konkretnych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="995b1-107">For example,  `System.Messaging.MessageQueue` is unsealed and thus allows users to create custom queues that default to a particular queue path or to add custom methods that simplify the API for specific scenarios.</span></span>  
  
 <span data-ttu-id="995b1-108">Klasy są niezapieczętowany domyślnie w językach programowania najbardziej i jest zalecana domyślna dla większości klas w struktur.</span><span class="sxs-lookup"><span data-stu-id="995b1-108">Classes are unsealed by default in most programming languages, and this is also the recommended default for most classes in frameworks.</span></span> <span data-ttu-id="995b1-109">Rozszerzalność udostępnianych przez niezapieczętowane typy jest znacznie zwiększyć przez użytkowników w ramach dość niedrogie zapewnienie ze względu na koszty stosunkowo niska testów związane z niezapieczętowane typy.</span><span class="sxs-lookup"><span data-stu-id="995b1-109">The extensibility afforded by unsealed types is much appreciated by framework users and quite inexpensive to provide because of relatively low test costs associated with unsealed types.</span></span>  
  
 <span data-ttu-id="995b1-110">*Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="995b1-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="995b1-111">*Przedrukowano za uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: Konwencje, Idiomy i wzorców dla wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams publikowane 22 Oct 2008 przez Addison Wesley Professional w ramach serii rozwoju Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="995b1-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="995b1-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="995b1-112">See also</span></span>

- [<span data-ttu-id="995b1-113">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="995b1-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="995b1-114">Projektowanie pod kątem rozszerzalności</span><span class="sxs-lookup"><span data-stu-id="995b1-114">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
- [<span data-ttu-id="995b1-115">Pieczętowanie</span><span class="sxs-lookup"><span data-stu-id="995b1-115">Sealing</span></span>](../../../docs/standard/design-guidelines/sealing.md)
