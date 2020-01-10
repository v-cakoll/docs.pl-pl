---
title: Wskazówki dotyczące nazewnictwa
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], about naming guidelines
- naming guidelines [.NET Framework]
- class library design guidelines [.NET Framework], names
- formatting [.NET Framework], names
- identifiers, class library element names
- names [.NET Framework]
- format naming guidelines [.NET Framework]
ms.assetid: fc076d66-9b5f-42d3-aa65-61d970c794a3
ms.openlocfilehash: ad98c0f3b02bdc81e6348493b4e0a02f9cb20ed4
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709195"
---
# <a name="naming-guidelines"></a><span data-ttu-id="9cd89-102">Wskazówki dotyczące nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="9cd89-102">Naming Guidelines</span></span>
<span data-ttu-id="9cd89-103">Zgodnie ze spójnym zestawem konwencji nazewnictwa w rozwoju struktury może być istotnym udziałem w zakresie użyteczności platformy.</span><span class="sxs-lookup"><span data-stu-id="9cd89-103">Following a consistent set of naming conventions in the development of a framework can be a major contribution to the framework’s usability.</span></span> <span data-ttu-id="9cd89-104">Pozwala ona na użycie platformy przez wielu deweloperów w oddzielnym projekcie.</span><span class="sxs-lookup"><span data-stu-id="9cd89-104">It allows the framework to be used by many developers on widely separated projects.</span></span> <span data-ttu-id="9cd89-105">Poza spójnością formy nazwy elementów struktury muszą być łatwo zrozumiałe i muszą przekazywać funkcję każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="9cd89-105">Beyond consistency of form, names of framework elements must be easily understood and must convey the function of each element.</span></span>  
  
 <span data-ttu-id="9cd89-106">Celem tego rozdziału jest zapewnienie spójnego zestawu konwencji nazewnictwa, które są wynikiem nazw, które sprawiają, że deweloperzy.</span><span class="sxs-lookup"><span data-stu-id="9cd89-106">The goal of this chapter is to provide a consistent set of naming conventions that results in names that make immediate sense to developers.</span></span>  
  
 <span data-ttu-id="9cd89-107">Chociaż stosowanie tych konwencji nazewnictwa jako ogólnych wytycznych dotyczących programowania kodu spowoduje bardziej spójne nazewnictwo w całym kodzie, wymagane jest tylko ich zastosowanie do interfejsów API, które są publicznie uwidocznione (typy publiczne lub chronione i składowe, i jawnie zaimplementowane interfejsy).</span><span class="sxs-lookup"><span data-stu-id="9cd89-107">Although adopting these naming conventions as general code development guidelines would result in more consistent naming throughout your code, you are required only to apply them to APIs that are publicly exposed (public or protected types and members, and explicitly implemented interfaces).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9cd89-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="9cd89-108">In This Section</span></span>  
 [<span data-ttu-id="9cd89-109">Konwencje dotyczące wielkości liter</span><span class="sxs-lookup"><span data-stu-id="9cd89-109">Capitalization Conventions</span></span>](../../../docs/standard/design-guidelines/capitalization-conventions.md)  
 [<span data-ttu-id="9cd89-110">Ogólne konwencje nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="9cd89-110">General Naming Conventions</span></span>](../../../docs/standard/design-guidelines/general-naming-conventions.md)  
 [<span data-ttu-id="9cd89-111">Nazwy zestawów i bibliotek DLL</span><span class="sxs-lookup"><span data-stu-id="9cd89-111">Names of Assemblies and DLLs</span></span>](../../../docs/standard/design-guidelines/names-of-assemblies-and-dlls.md)  
 [<span data-ttu-id="9cd89-112">Nazwy przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="9cd89-112">Names of Namespaces</span></span>](../../../docs/standard/design-guidelines/names-of-namespaces.md)  
 [<span data-ttu-id="9cd89-113">Nazwy klas, struktur i interfejsów</span><span class="sxs-lookup"><span data-stu-id="9cd89-113">Names of Classes, Structs, and Interfaces</span></span>](../../../docs/standard/design-guidelines/names-of-classes-structs-and-interfaces.md)  
 [<span data-ttu-id="9cd89-114">Nazwy elementów członkowskich typu</span><span class="sxs-lookup"><span data-stu-id="9cd89-114">Names of Type Members</span></span>](../../../docs/standard/design-guidelines/names-of-type-members.md)  
 [<span data-ttu-id="9cd89-115">Nazewnictwo parametrów</span><span class="sxs-lookup"><span data-stu-id="9cd89-115">Naming Parameters</span></span>](../../../docs/standard/design-guidelines/naming-parameters.md)  
 [<span data-ttu-id="9cd89-116">Nazewnictwo zasobów</span><span class="sxs-lookup"><span data-stu-id="9cd89-116">Naming Resources</span></span>](../../../docs/standard/design-guidelines/naming-resources.md)  
 <span data-ttu-id="9cd89-117">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="9cd89-117">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="9cd89-118">*Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="9cd89-118">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cd89-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9cd89-119">See also</span></span>

- [<span data-ttu-id="9cd89-120">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="9cd89-120">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
