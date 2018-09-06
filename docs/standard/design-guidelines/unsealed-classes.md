---
title: Niezapieczętowane klasy
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- classes [.NET Framework], unsealed
- unsealed classes
- inheritance, classes
ms.assetid: 9a3bd505-90f5-4053-9f0d-3cf5fa3d3ebf
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ef0f1c4c9b2d1928d6f96d62ab12df9786756498
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43891380"
---
# <a name="unsealed-classes"></a><span data-ttu-id="f4093-102">Niezapieczętowane klasy</span><span class="sxs-lookup"><span data-stu-id="f4093-102">Unsealed Classes</span></span>
<span data-ttu-id="f4093-103">Zapieczętowane klasy nie może być dziedziczona z i zapobiegają one rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="f4093-103">Sealed classes cannot be inherited from, and they prevent extensibility.</span></span> <span data-ttu-id="f4093-104">Z kolei klas, które mogą być dziedziczone z są nazywane niezapieczętowane klasy.</span><span class="sxs-lookup"><span data-stu-id="f4093-104">In contrast, classes that can be inherited from are called unsealed classes.</span></span>  
  
 <span data-ttu-id="f4093-105">**✓ CONSIDER** przy użyciu niezapieczętowanych klas bez dodać wirtualnych lub chronionych elementów członkowskich, ponieważ doskonałym sposobem zapewnienia niedrogich jeszcze znacznie zwiększyć elastyczność w ramach.</span><span class="sxs-lookup"><span data-stu-id="f4093-105">**✓ CONSIDER** using unsealed classes with no added virtual or protected members as a great way to provide inexpensive yet much appreciated extensibility to a framework.</span></span>  
  
 <span data-ttu-id="f4093-106">Deweloperzy często ma być dziedziczona z niezapieczętowane klasy tak, aby dodać członków jako udogodnienie, takie jak niestandardowe konstruktorów, nowych metod lub przeciążenia metody.</span><span class="sxs-lookup"><span data-stu-id="f4093-106">Developers often want to inherit from unsealed classes so as to add convenience members such as custom constructors, new methods, or method overloads.</span></span> <span data-ttu-id="f4093-107">Na przykład `System.Messaging.MessageQueue` jest niezapieczętowany, dlatego. Umożliwia ono użytkownikom tworzenie niestandardowych kolejek tej wartości domyślnej ścieżki określonej kolejki lub dodawanie metod niestandardowych, które upraszczają interfejs API dla konkretnych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="f4093-107">For example,  `System.Messaging.MessageQueue` is unsealed and thus allows users to create custom queues that default to a particular queue path or to add custom methods that simplify the API for specific scenarios.</span></span>  
  
 <span data-ttu-id="f4093-108">Klasy są niezapieczętowany domyślnie w językach programowania najbardziej i jest zalecana domyślna dla większości klas w struktur.</span><span class="sxs-lookup"><span data-stu-id="f4093-108">Classes are unsealed by default in most programming languages, and this is also the recommended default for most classes in frameworks.</span></span> <span data-ttu-id="f4093-109">Rozszerzalność udostępnianych przez niezapieczętowane typy jest znacznie zwiększyć przez użytkowników w ramach dość niedrogie zapewnienie ze względu na koszty stosunkowo niska testów związane z niezapieczętowane typy.</span><span class="sxs-lookup"><span data-stu-id="f4093-109">The extensibility afforded by unsealed types is much appreciated by framework users and quite inexpensive to provide because of relatively low test costs associated with unsealed types.</span></span>  
  
 <span data-ttu-id="f4093-110">*Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="f4093-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="f4093-111">*Przedrukowano przez uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: konwencje Idiomy i wzorce wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams opublikowane 22 Oct 2008 przez Professional Addison Wesley jako część serii rozwoju Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="f4093-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4093-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f4093-112">See also</span></span>

- [<span data-ttu-id="f4093-113">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="f4093-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
- [<span data-ttu-id="f4093-114">Projektowanie pod kątem rozszerzalności</span><span class="sxs-lookup"><span data-stu-id="f4093-114">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
- [<span data-ttu-id="f4093-115">Pieczętowanie</span><span class="sxs-lookup"><span data-stu-id="f4093-115">Sealing</span></span>](../../../docs/standard/design-guidelines/sealing.md)
