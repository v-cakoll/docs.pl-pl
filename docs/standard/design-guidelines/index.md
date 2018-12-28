---
title: Framework — zalecenia dotyczące projektowania
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- libraries, .NET Framework class library
- class library design guidelines [.NET Framework], about
- class library design guidelines [.NET Framework]
ms.assetid: 5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b
author: KrzysztofCwalina
ms.openlocfilehash: 2317ed0dbe8a6e69452ac0721ffed1b9da50a907
ms.sourcegitcommit: 49af435bfdd41faf26d38c20c5b0cc07e87bea60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53396932"
---
# <a name="framework-design-guidelines"></a><span data-ttu-id="380e8-102">Framework — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="380e8-102">Framework Design Guidelines</span></span>
<span data-ttu-id="380e8-103">Ta sekcja zawiera wskazówki dotyczące projektowania bibliotek, które rozszerzają i wchodzić w interakcje z programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="380e8-103">This section provides guidelines for designing libraries that extend and interact with the .NET Framework.</span></span> <span data-ttu-id="380e8-104">Celem jest pomoc projektantów Biblioteka zapewnia spójność interfejsu API i łatwość użycia, udostępniając ujednolicony model programowania, który jest niezależny od języka programowania, używany do tworzenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="380e8-104">The goal is to help library designers ensure API consistency and ease of use by providing a unified programming model that is independent of the programming language used for development.</span></span> <span data-ttu-id="380e8-105">Zaleca się przestrzegać następujących wytycznych projektowania, podczas tworzenia klas i składników, które rozszerzają programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="380e8-105">We recommend that you follow these design guidelines when developing classes and components that extend the .NET Framework.</span></span> <span data-ttu-id="380e8-106">Biblioteka niespójne projektu niekorzystnie wpływa na wydajność pracy deweloperskiej i zniechęca do przyjęcia.</span><span class="sxs-lookup"><span data-stu-id="380e8-106">Inconsistent library design adversely affects developer productivity and discourages adoption.</span></span>  
  
 <span data-ttu-id="380e8-107">Wytyczne są uporządkowane jako prosty zalecenia prefiksem warunki `Do`, `Consider`, `Avoid`, i `Do not`.</span><span class="sxs-lookup"><span data-stu-id="380e8-107">The guidelines are organized as simple recommendations prefixed with the terms `Do`, `Consider`, `Avoid`, and `Do not`.</span></span> <span data-ttu-id="380e8-108">Te wytyczne są celem projektantów biblioteki klasy zrozumieć wad i zalet różnych rozwiązań.</span><span class="sxs-lookup"><span data-stu-id="380e8-108">These guidelines are intended to help class library designers understand the trade-offs between different solutions.</span></span> <span data-ttu-id="380e8-109">Może to być sytuacje, w których projekt biblioteki w dobrej wymaga, że naruszają te wytyczne dotyczące projektowania.</span><span class="sxs-lookup"><span data-stu-id="380e8-109">There might be situations where good library design requires that you violate these design guidelines.</span></span> <span data-ttu-id="380e8-110">Takiej sytuacji należy rzadkich i jest ważne, czy masz czytelne i atrakcyjne przyczynę swojej decyzji.</span><span class="sxs-lookup"><span data-stu-id="380e8-110">Such cases should be rare, and it is important that you have a clear and compelling reason for your decision.</span></span>  
  
 <span data-ttu-id="380e8-111">Te wytyczne pochodzą z książki *wytyczne dotyczące projektowania Framework: Konwencje, Idiomy i wzorców dla bibliotek .NET wielokrotnego użytku, wydanie 2*, Krzysztof Cwalina i Brad Abrams.</span><span class="sxs-lookup"><span data-stu-id="380e8-111">These guidelines are excerpted from the book *Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition*, by Krzysztof Cwalina and Brad Abrams.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="380e8-112">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="380e8-112">In This Section</span></span>  
 [<span data-ttu-id="380e8-113">Wskazówki dotyczące nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="380e8-113">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)  
 <span data-ttu-id="380e8-114">Zawiera wskazówki dotyczące nazewnictwa zestawów, przestrzeni nazw, typów i członków w bibliotekach klas.</span><span class="sxs-lookup"><span data-stu-id="380e8-114">Provides guidelines for naming assemblies, namespaces, types, and members in class libraries.</span></span>  
  
 [<span data-ttu-id="380e8-115">Typy — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="380e8-115">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
 <span data-ttu-id="380e8-116">Wskazówki dotyczące używania klas statycznych i abstrakcyjny, interfejsy, wyliczenia, struktur i innych typów.</span><span class="sxs-lookup"><span data-stu-id="380e8-116">Provides guidelines for using static and abstract classes, interfaces, enumerations, structures, and other types.</span></span>  
  
 [<span data-ttu-id="380e8-117">Element członkowski — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="380e8-117">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
 <span data-ttu-id="380e8-118">Wskazówki dotyczące projektowania i używania właściwości, metody, konstruktory, pola, zdarzenia, operatorów i parametry.</span><span class="sxs-lookup"><span data-stu-id="380e8-118">Provides guidelines for designing and using properties, methods, constructors, fields, events, operators, and parameters.</span></span>  
  
 [<span data-ttu-id="380e8-119">Projektowanie pod kątem rozszerzalności</span><span class="sxs-lookup"><span data-stu-id="380e8-119">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 <span data-ttu-id="380e8-120">W tym artykule omówiono rozszerzalności mechanizmów, takich jak podklasy, za pomocą zdarzeń, wirtualne elementy członkowskie i wywołania zwrotne i wyjaśnia, jak wybrać mechanizmów, które najlepiej spełniają wymagania preferowanej struktury.</span><span class="sxs-lookup"><span data-stu-id="380e8-120">Discusses extensibility mechanisms such as subclassing, using events, virtual members, and callbacks, and explains how to choose the mechanisms that best meet your framework's requirements.</span></span>  
  
 [<span data-ttu-id="380e8-121">Wyjątki — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="380e8-121">Design Guidelines for Exceptions</span></span>](../../../docs/standard/design-guidelines/exceptions.md)  
 <span data-ttu-id="380e8-122">W tym artykule opisano wytyczne dotyczące projektowania dla projektowania, zgłaszanie i połowowe wyjątków.</span><span class="sxs-lookup"><span data-stu-id="380e8-122">Describes design guidelines for designing, throwing, and catching exceptions.</span></span>  
  
 [<span data-ttu-id="380e8-123">Zalecenia dotyczące użytkowania</span><span class="sxs-lookup"><span data-stu-id="380e8-123">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)  
 <span data-ttu-id="380e8-124">W tym artykule opisano wskazówki dotyczące przy użyciu popularnych typów, takich jak tablice, atrybuty i kolekcje, obsługa serializacji i przeciążanie operatorów równości.</span><span class="sxs-lookup"><span data-stu-id="380e8-124">Describes guidelines for using common types such as arrays, attributes, and collections, supporting serialization, and overloading equality operators.</span></span>  
  
 [<span data-ttu-id="380e8-125">Często używane wzorce projektowe</span><span class="sxs-lookup"><span data-stu-id="380e8-125">Common Design Patterns</span></span>](../../../docs/standard/design-guidelines/common-design-patterns.md)  
 <span data-ttu-id="380e8-126">Zawiera wskazówki dotyczące wybierania i implementowanie właściwości zależności.</span><span class="sxs-lookup"><span data-stu-id="380e8-126">Provides guidelines for choosing and implementing dependency properties.</span></span>  
  
 <span data-ttu-id="380e8-127">*Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="380e8-127">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="380e8-128">*Przedrukowano za uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: Konwencje, Idiomy i wzorców dla wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams publikowane 22 Oct 2008 przez Addison Wesley Professional w ramach serii rozwoju Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="380e8-128">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="380e8-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="380e8-129">See also</span></span>

- [<span data-ttu-id="380e8-130">Omówienie</span><span class="sxs-lookup"><span data-stu-id="380e8-130">Overview</span></span>](../../../docs/framework/get-started/overview.md)  
- [<span data-ttu-id="380e8-131">Harmonogram działania dla platformy .NET Framework</span><span class="sxs-lookup"><span data-stu-id="380e8-131">Roadmap for the .NET Framework</span></span>](https://msdn.microsoft.com/library/0b46b7c6-9163-4f99-8e58-0d1ee7da8c67)  
- [<span data-ttu-id="380e8-132">Podręcznik programowania</span><span class="sxs-lookup"><span data-stu-id="380e8-132">Development Guide</span></span>](../../../docs/framework/development-guide.md)
