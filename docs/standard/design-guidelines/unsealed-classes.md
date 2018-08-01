---
title: Niezapieczętowanych klas
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- classes [.NET Framework], unsealed
- unsealed classes
- inheritance, classes
ms.assetid: 9a3bd505-90f5-4053-9f0d-3cf5fa3d3ebf
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 672d36c6b888ee9a89a76d5d417a7a7e92dd8f36
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571664"
---
# <a name="unsealed-classes"></a><span data-ttu-id="444da-102">Niezapieczętowanych klas</span><span class="sxs-lookup"><span data-stu-id="444da-102">Unsealed Classes</span></span>
<span data-ttu-id="444da-103">Zapieczętowane klasy nie może być dziedziczona z i uniemożliwić ich rozszerzeń.</span><span class="sxs-lookup"><span data-stu-id="444da-103">Sealed classes cannot be inherited from, and they prevent extensibility.</span></span> <span data-ttu-id="444da-104">Z kolei klasy, które mogą być dziedziczone z są nazywane niezapieczętowanych klas.</span><span class="sxs-lookup"><span data-stu-id="444da-104">In contrast, classes that can be inherited from are called unsealed classes.</span></span>  
  
 <span data-ttu-id="444da-105">**✓ CONSIDER** przy użyciu niezapieczętowanych klas bez dodać wirtualnych lub chronionych elementów członkowskich, ponieważ doskonałym sposobem zapewnienia niedrogich jeszcze znacznie zwiększyć elastyczność w ramach.</span><span class="sxs-lookup"><span data-stu-id="444da-105">**✓ CONSIDER** using unsealed classes with no added virtual or protected members as a great way to provide inexpensive yet much appreciated extensibility to a framework.</span></span>  
  
 <span data-ttu-id="444da-106">Deweloperzy często ma być dziedziczona z klasy niezapieczętowany tak, aby dodawać członków wygody, takie jak niestandardowe konstruktorów, nowych metod lub przeciążenia metody.</span><span class="sxs-lookup"><span data-stu-id="444da-106">Developers often want to inherit from unsealed classes so as to add convenience members such as custom constructors, new methods, or method overloads.</span></span> <span data-ttu-id="444da-107">Na przykład `System.Messaging.MessageQueue` jest otwarty i w związku z tym umożliwia użytkownikom tworzenie niestandardowych kolejek domyślną wartość tego ścieżką określonej kolejki lub dodawanie metod niestandardowych, które upraszczają interfejsu API dla konkretnych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="444da-107">For example,  `System.Messaging.MessageQueue` is unsealed and thus allows users to create custom queues that default to a particular queue path or to add custom methods that simplify the API for specific scenarios.</span></span>  
  
 <span data-ttu-id="444da-108">Klasy niezapieczętowanego są domyślnie w językach programowania najbardziej i jest zalecane ustawienia domyślne dla większości klas struktury.</span><span class="sxs-lookup"><span data-stu-id="444da-108">Classes are unsealed by default in most programming languages, and this is also the recommended default for most classes in frameworks.</span></span> <span data-ttu-id="444da-109">Rozszerzalność zapewnianej przez typy niezapieczętowany jest znacznie zwiększyć przez użytkowników w ramach i dość niedrogich zapewnienie ze względu na małą testu kosztów związanych z niezapieczętowane typy.</span><span class="sxs-lookup"><span data-stu-id="444da-109">The extensibility afforded by unsealed types is much appreciated by framework users and quite inexpensive to provide because of relatively low test costs associated with unsealed types.</span></span>  
  
 <span data-ttu-id="444da-110">*Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="444da-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="444da-111">*Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="444da-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="444da-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="444da-112">See Also</span></span>  
 [<span data-ttu-id="444da-113">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="444da-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="444da-114">Projektowanie pod kątem rozszerzalności</span><span class="sxs-lookup"><span data-stu-id="444da-114">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 [<span data-ttu-id="444da-115">Pieczętowanie</span><span class="sxs-lookup"><span data-stu-id="444da-115">Sealing</span></span>](../../../docs/standard/design-guidelines/sealing.md)
