---
title: Wskazówki dotyczące nazewnictwa
description: W tym omówieniu Przeczytaj informacje o konwencjach nazewnictwa, które mają być używane w środowisku programistycznym. Przejdź do artykułów obejmujących wielkie litery, ogólne nazewnictwo i inne wskazówki.
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
ms.openlocfilehash: fbcf5ef5eb02a5e45b5c981b4247ffe1c9c2631b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2020
ms.locfileid: "84447150"
---
# <a name="naming-guidelines"></a><span data-ttu-id="af8cb-104">Wskazówki dotyczące nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="af8cb-104">Naming Guidelines</span></span>
<span data-ttu-id="af8cb-105">Zgodnie ze spójnym zestawem konwencji nazewnictwa w rozwoju struktury może być istotnym udziałem w zakresie użyteczności platformy.</span><span class="sxs-lookup"><span data-stu-id="af8cb-105">Following a consistent set of naming conventions in the development of a framework can be a major contribution to the framework’s usability.</span></span> <span data-ttu-id="af8cb-106">Pozwala ona na użycie platformy przez wielu deweloperów w oddzielnym projekcie.</span><span class="sxs-lookup"><span data-stu-id="af8cb-106">It allows the framework to be used by many developers on widely separated projects.</span></span> <span data-ttu-id="af8cb-107">Poza spójnością formy nazwy elementów struktury muszą być łatwo zrozumiałe i muszą przekazywać funkcję każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="af8cb-107">Beyond consistency of form, names of framework elements must be easily understood and must convey the function of each element.</span></span>  
  
 <span data-ttu-id="af8cb-108">Celem tego rozdziału jest zapewnienie spójnego zestawu konwencji nazewnictwa, które są wynikiem nazw, które sprawiają, że deweloperzy.</span><span class="sxs-lookup"><span data-stu-id="af8cb-108">The goal of this chapter is to provide a consistent set of naming conventions that results in names that make immediate sense to developers.</span></span>  
  
 <span data-ttu-id="af8cb-109">Chociaż stosowanie tych konwencji nazewnictwa jako ogólnych wytycznych dotyczących programowania kodu spowoduje bardziej spójne nazewnictwo w całym kodzie, wymagane jest tylko ich zastosowanie do interfejsów API, które są publicznie uwidocznione (typy publiczne lub chronione oraz członkowie i jawnie zaimplementowane interfejsy).</span><span class="sxs-lookup"><span data-stu-id="af8cb-109">Although adopting these naming conventions as general code development guidelines would result in more consistent naming throughout your code, you are required only to apply them to APIs that are publicly exposed (public or protected types and members, and explicitly implemented interfaces).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="af8cb-110">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="af8cb-110">In This Section</span></span>  
 [<span data-ttu-id="af8cb-111">Konwencje kapitalizacji</span><span class="sxs-lookup"><span data-stu-id="af8cb-111">Capitalization Conventions</span></span>](capitalization-conventions.md)  
 [<span data-ttu-id="af8cb-112">Ogólne konwencje nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="af8cb-112">General Naming Conventions</span></span>](general-naming-conventions.md)  
 [<span data-ttu-id="af8cb-113">Nazwy zestawów i bibliotek DLL</span><span class="sxs-lookup"><span data-stu-id="af8cb-113">Names of Assemblies and DLLs</span></span>](names-of-assemblies-and-dlls.md)  
 [<span data-ttu-id="af8cb-114">Nazwy przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="af8cb-114">Names of Namespaces</span></span>](names-of-namespaces.md)  
 [<span data-ttu-id="af8cb-115">Nazwy klas, struktur i interfejsów</span><span class="sxs-lookup"><span data-stu-id="af8cb-115">Names of Classes, Structs, and Interfaces</span></span>](names-of-classes-structs-and-interfaces.md)  
 [<span data-ttu-id="af8cb-116">Nazwy elementów członkowskich typu</span><span class="sxs-lookup"><span data-stu-id="af8cb-116">Names of Type Members</span></span>](names-of-type-members.md)  
 [<span data-ttu-id="af8cb-117">Parametry nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="af8cb-117">Naming Parameters</span></span>](naming-parameters.md)  
 [<span data-ttu-id="af8cb-118">Określanie nazw zasobów</span><span class="sxs-lookup"><span data-stu-id="af8cb-118">Naming Resources</span></span>](naming-resources.md)  
 <span data-ttu-id="af8cb-119">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="af8cb-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="af8cb-120">*Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="af8cb-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af8cb-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="af8cb-121">See also</span></span>

- [<span data-ttu-id="af8cb-122">Wskazówki dotyczące projektowania struktury</span><span class="sxs-lookup"><span data-stu-id="af8cb-122">Framework Design Guidelines</span></span>](index.md)
