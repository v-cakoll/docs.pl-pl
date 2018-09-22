---
title: Wskazówki dotyczące nazewnictwa
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 70888e068782add5ebe5ae1c7da3bdee842faea8
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2018
ms.locfileid: "46695358"
---
# <a name="naming-guidelines"></a><span data-ttu-id="6211b-102">Wskazówki dotyczące nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="6211b-102">Naming Guidelines</span></span>
<span data-ttu-id="6211b-103">Następujące spójny zestaw konwencji nazewnictwa do tworzenia struktury może być duży wkład do kwestii użyteczności struktury.</span><span class="sxs-lookup"><span data-stu-id="6211b-103">Following a consistent set of naming conventions in the development of a framework can be a major contribution to the framework’s usability.</span></span> <span data-ttu-id="6211b-104">Umożliwia ona framework, który będzie używany przez wielu deweloperów na powszechnie oddzielnych projektów.</span><span class="sxs-lookup"><span data-stu-id="6211b-104">It allows the framework to be used by many developers on widely separated projects.</span></span> <span data-ttu-id="6211b-105">Poza spójność formularza nazwy elementów w ramach łatwo zrozumiałe i musi przekazać funkcji każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="6211b-105">Beyond consistency of form, names of framework elements must be easily understood and must convey the function of each element.</span></span>  
  
 <span data-ttu-id="6211b-106">Celem tego rozdziału jest aby zapewnić spójny zestaw konwencji nazewnictwa, powstałego w nazwach, które mają sens natychmiastowego dla deweloperów.</span><span class="sxs-lookup"><span data-stu-id="6211b-106">The goal of this chapter is to provide a consistent set of naming conventions that results in names that make immediate sense to developers.</span></span>  
  
 <span data-ttu-id="6211b-107">Mimo że wdrażanie tych konwencji nazewnictwa jak wskazówki dotyczące programowania ogólnego kodu mogłyby spowodować bardziej spójne nazewnictwo w całym kodzie, musisz tylko zastosować je do interfejsów API, które są publicznie widoczne (publiczny lub chroniony typów i członków, i jawnie implementowane interfejsy).</span><span class="sxs-lookup"><span data-stu-id="6211b-107">Although adopting these naming conventions as general code development guidelines would result in more consistent naming throughout your code, you are required only to apply them to APIs that are publicly exposed (public or protected types and members, and explicitly implemented interfaces).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6211b-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="6211b-108">In This Section</span></span>  
 [<span data-ttu-id="6211b-109">Konwencje dotyczące wielkości liter</span><span class="sxs-lookup"><span data-stu-id="6211b-109">Capitalization Conventions</span></span>](../../../docs/standard/design-guidelines/capitalization-conventions.md)  
 [<span data-ttu-id="6211b-110">Ogólne konwencje nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="6211b-110">General Naming Conventions</span></span>](../../../docs/standard/design-guidelines/general-naming-conventions.md)  
 [<span data-ttu-id="6211b-111">Nazwy zestawów i bibliotek DLL</span><span class="sxs-lookup"><span data-stu-id="6211b-111">Names of Assemblies and DLLs</span></span>](../../../docs/standard/design-guidelines/names-of-assemblies-and-dlls.md)  
 [<span data-ttu-id="6211b-112">Nazwy przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="6211b-112">Names of Namespaces</span></span>](../../../docs/standard/design-guidelines/names-of-namespaces.md)  
 [<span data-ttu-id="6211b-113">Nazwy klas, struktur i interfejsów</span><span class="sxs-lookup"><span data-stu-id="6211b-113">Names of Classes, Structs, and Interfaces</span></span>](../../../docs/standard/design-guidelines/names-of-classes-structs-and-interfaces.md)  
 [<span data-ttu-id="6211b-114">Nazwy elementów członkowskich typu</span><span class="sxs-lookup"><span data-stu-id="6211b-114">Names of Type Members</span></span>](../../../docs/standard/design-guidelines/names-of-type-members.md)  
 [<span data-ttu-id="6211b-115">Nazewnictwo parametrów</span><span class="sxs-lookup"><span data-stu-id="6211b-115">Naming Parameters</span></span>](../../../docs/standard/design-guidelines/naming-parameters.md)  
 [<span data-ttu-id="6211b-116">Nazewnictwo zasobów</span><span class="sxs-lookup"><span data-stu-id="6211b-116">Naming Resources</span></span>](../../../docs/standard/design-guidelines/naming-resources.md)  
 <span data-ttu-id="6211b-117">*Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="6211b-117">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="6211b-118">*Przedrukowano przez uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: konwencje Idiomy i wzorce wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams opublikowane 22 Oct 2008 przez Professional Addison Wesley jako część serii rozwoju Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="6211b-118">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6211b-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6211b-119">See also</span></span>

- [<span data-ttu-id="6211b-120">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="6211b-120">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
