---
title: Chronione składowe
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
ms.openlocfilehash: 44d342662e1aaeb51f14470f354f2dadd9a6f18d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743644"
---
# <a name="protected-members"></a><span data-ttu-id="7a53f-102">Chronione składowe</span><span class="sxs-lookup"><span data-stu-id="7a53f-102">Protected Members</span></span>
<span data-ttu-id="7a53f-103">Chronione elementy członkowskie nie zapewniają żadnych rozszerzalności, ale mogą zwiększyć możliwości rozszerzania za pomocą podklas.</span><span class="sxs-lookup"><span data-stu-id="7a53f-103">Protected members by themselves do not provide any extensibility, but they can make extensibility through subclassing more powerful.</span></span> <span data-ttu-id="7a53f-104">Mogą one służyć do udostępnienia zaawansowanych opcji dostosowania bez niepotrzebnego skomplikowania głównego interfejsu publicznego.</span><span class="sxs-lookup"><span data-stu-id="7a53f-104">They can be used to expose advanced customization options without unnecessarily complicating the main public interface.</span></span>

 <span data-ttu-id="7a53f-105">Projektantom struktury należy zachować ostrożność z chronionymi elementami członkowskimi, ponieważ nazwa "Protected" może mieć fałszywe znaczenie dla zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="7a53f-105">Framework designers need to be careful with protected members because the name "protected" can give a false sense of security.</span></span> <span data-ttu-id="7a53f-106">Każda osoba może poddawać podklasie niezapieczętowanej klasie i uzyskać dostęp do chronionych elementów członkowskich, dzięki czemu wszystkie takie same praktyki dotyczące kodowania, które są używane dla publicznych członków, mają zastosowanie do chronionych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="7a53f-106">Anyone is able to subclass an unsealed class and access protected members, and so all the same defensive coding practices used for public members apply to protected members.</span></span>

 <span data-ttu-id="7a53f-107">✔️ ROZWAŻYĆ użycie chronionych elementów członkowskich do dostosowania zaawansowanego.</span><span class="sxs-lookup"><span data-stu-id="7a53f-107">✔️ CONSIDER using protected members for advanced customization.</span></span>

 <span data-ttu-id="7a53f-108">✔️ Traktuj chronione elementy członkowskie z niezapieczętowanych klas jako publiczne na potrzeby analizy zabezpieczeń, dokumentacji i zgodności.</span><span class="sxs-lookup"><span data-stu-id="7a53f-108">✔️ DO treat protected members in unsealed classes as public for the purpose of security, documentation, and compatibility analysis.</span></span>

 <span data-ttu-id="7a53f-109">Każdy może dziedziczyć z klasy i uzyskiwać dostęp do chronionych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="7a53f-109">Anyone can inherit from a class and access the protected members.</span></span>

 <span data-ttu-id="7a53f-110">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="7a53f-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="7a53f-111">*Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="7a53f-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="7a53f-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7a53f-112">See also</span></span>

- [<span data-ttu-id="7a53f-113">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="7a53f-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="7a53f-114">Projektowanie pod kątem rozszerzalności</span><span class="sxs-lookup"><span data-stu-id="7a53f-114">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
