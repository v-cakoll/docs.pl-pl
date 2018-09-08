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
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44196923"
---
# <a name="naming-guidelines"></a><span data-ttu-id="791c1-102">Wskazówki dotyczące nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="791c1-102">Naming Guidelines</span></span>
<span data-ttu-id="791c1-103">Następujące spójny zestaw konwencji nazewnictwa do tworzenia struktury może być duży wkład do kwestii użyteczności struktury.</span><span class="sxs-lookup"><span data-stu-id="791c1-103">Following a consistent set of naming conventions in the development of a framework can be a major contribution to the framework’s usability.</span></span> <span data-ttu-id="791c1-104">Umożliwia ona framework, który będzie używany przez wielu deweloperów na powszechnie oddzielnych projektów.</span><span class="sxs-lookup"><span data-stu-id="791c1-104">It allows the framework to be used by many developers on widely separated projects.</span></span> <span data-ttu-id="791c1-105">Poza spójność formularza nazwy elementów w ramach łatwo zrozumiałe i musi przekazać funkcji każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="791c1-105">Beyond consistency of form, names of framework elements must be easily understood and must convey the function of each element.</span></span>  
  
 <span data-ttu-id="791c1-106">Celem tego rozdziału jest aby zapewnić spójny zestaw konwencji nazewnictwa, powstałego w nazwach, które mają sens natychmiastowego dla deweloperów.</span><span class="sxs-lookup"><span data-stu-id="791c1-106">The goal of this chapter is to provide a consistent set of naming conventions that results in names that make immediate sense to developers.</span></span>  
  
 <span data-ttu-id="791c1-107">Mimo że wdrażanie tych konwencji nazewnictwa jak wskazówki dotyczące programowania ogólnego kodu mogłyby spowodować bardziej spójne nazewnictwo w całym kodzie, musisz tylko zastosować je do interfejsów API, które są publicznie widoczne (publiczny lub chroniony typów i członków, i jawnie implementowane interfejsy).</span><span class="sxs-lookup"><span data-stu-id="791c1-107">Although adopting these naming conventions as general code development guidelines would result in more consistent naming throughout your code, you are required only to apply them to APIs that are publicly exposed (public or protected types and members, and explicitly implemented interfaces).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="791c1-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="791c1-108">In This Section</span></span>  
 [<span data-ttu-id="791c1-109">Konwencje dotyczące wielkości liter</span><span class="sxs-lookup"><span data-stu-id="791c1-109">Capitalization Conventions</span></span>](../../../docs/standard/design-guidelines/capitalization-conventions.md)  
 [<span data-ttu-id="791c1-110">Ogólne konwencje nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="791c1-110">General Naming Conventions</span></span>](../../../docs/standard/design-guidelines/general-naming-conventions.md)  
 [<span data-ttu-id="791c1-111">Nazwy zestawów i bibliotek DLL</span><span class="sxs-lookup"><span data-stu-id="791c1-111">Names of Assemblies and DLLs</span></span>](../../../docs/standard/design-guidelines/names-of-assemblies-and-dlls.md)  
 [<span data-ttu-id="791c1-112">Nazwy przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="791c1-112">Names of Namespaces</span></span>](../../../docs/standard/design-guidelines/names-of-namespaces.md)  
 [<span data-ttu-id="791c1-113">Nazwy klas, struktur i interfejsów</span><span class="sxs-lookup"><span data-stu-id="791c1-113">Names of Classes, Structs, and Interfaces</span></span>](../../../docs/standard/design-guidelines/names-of-classes-structs-and-interfaces.md)  
 [<span data-ttu-id="791c1-114">Nazwy elementów członkowskich typu</span><span class="sxs-lookup"><span data-stu-id="791c1-114">Names of Type Members</span></span>](../../../docs/standard/design-guidelines/names-of-type-members.md)  
 [<span data-ttu-id="791c1-115">Nazewnictwo parametrów</span><span class="sxs-lookup"><span data-stu-id="791c1-115">Naming Parameters</span></span>](../../../docs/standard/design-guidelines/naming-parameters.md)  
 [<span data-ttu-id="791c1-116">Nazewnictwo zasobów</span><span class="sxs-lookup"><span data-stu-id="791c1-116">Naming Resources</span></span>](../../../docs/standard/design-guidelines/naming-resources.md)  
 <span data-ttu-id="791c1-117">*Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="791c1-117">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="791c1-118">*Przedrukowano przez uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: konwencje Idiomy i wzorce wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams opublikowane 22 Oct 2008 przez Professional Addison Wesley jako część serii rozwoju Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="791c1-118">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="791c1-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="791c1-119">See also</span></span>

- [<span data-ttu-id="791c1-120">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="791c1-120">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
