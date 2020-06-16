---
title: Framework — zalecenia dotyczące projektowania
description: Zapoznaj się z tematem wskazówki dotyczące projektowania struktury dotyczące projektowania bibliotek, które poszerzają i współpracują z platformą .NET, aby zapewnić spójność interfejsu API i łatwość
titleSuffix: ''
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- libraries, .NET Framework class library
- class library design guidelines [.NET Framework], about
- class library design guidelines [.NET Framework]
ms.assetid: 5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b
ms.openlocfilehash: 17998adb1d18579f6763a80a82944e742e284e4e
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769070"
---
# <a name="framework-design-guidelines"></a><span data-ttu-id="ebaea-103">Framework — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="ebaea-103">Framework Design Guidelines</span></span>
<span data-ttu-id="ebaea-104">Ta sekcja zawiera wskazówki dotyczące projektowania bibliotek, które zwiększają i współpracują z .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ebaea-104">This section provides guidelines for designing libraries that extend and interact with the .NET Framework.</span></span> <span data-ttu-id="ebaea-105">Celem jest ułatwienie projektantom biblioteki zapewnienia spójności interfejsu API i prostoty użycia przez zapewnienie ujednoliconego modelu programowania, który jest niezależny od języka programowania używanego do programowania.</span><span class="sxs-lookup"><span data-stu-id="ebaea-105">The goal is to help library designers ensure API consistency and ease of use by providing a unified programming model that is independent of the programming language used for development.</span></span> <span data-ttu-id="ebaea-106">Zalecamy przestrzeganie tych wytycznych dotyczących projektowania podczas tworzenia klas i składników, które zwiększają .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ebaea-106">We recommend that you follow these design guidelines when developing classes and components that extend the .NET Framework.</span></span> <span data-ttu-id="ebaea-107">Niespójny projekt biblioteki niekorzystnie wpływa na produktywność deweloperów i odradza wdrażanie.</span><span class="sxs-lookup"><span data-stu-id="ebaea-107">Inconsistent library design adversely affects developer productivity and discourages adoption.</span></span>  
  
 <span data-ttu-id="ebaea-108">Wytyczne są zorganizowane jako proste zalecenia poprzedzone postanowieniami,, `Do` `Consider` `Avoid` i `Do not` .</span><span class="sxs-lookup"><span data-stu-id="ebaea-108">The guidelines are organized as simple recommendations prefixed with the terms `Do`, `Consider`, `Avoid`, and `Do not`.</span></span> <span data-ttu-id="ebaea-109">Te wytyczne mają na celu ułatwienie projektantom biblioteki klas zrozumienia zalet różnych rozwiązań.</span><span class="sxs-lookup"><span data-stu-id="ebaea-109">These guidelines are intended to help class library designers understand the trade-offs between different solutions.</span></span> <span data-ttu-id="ebaea-110">Mogą wystąpić sytuacje, w których dobry projekt biblioteki wymaga naruszenia tych wytycznych projektowych.</span><span class="sxs-lookup"><span data-stu-id="ebaea-110">There might be situations where good library design requires that you violate these design guidelines.</span></span> <span data-ttu-id="ebaea-111">Takie przypadki powinny być rzadkie i ważne jest, aby użytkownik miał jasno i atrakcyjny powód podjęcia decyzji.</span><span class="sxs-lookup"><span data-stu-id="ebaea-111">Such cases should be rare, and it is important that you have a clear and compelling reason for your decision.</span></span>  
  
 <span data-ttu-id="ebaea-112">Wytyczne te są przedstawione na podstawie *wytycznych dotyczących projektowania struktury książki: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, wydanie 2*, Krzysztof Cwalina i Brad Abrams.</span><span class="sxs-lookup"><span data-stu-id="ebaea-112">These guidelines are excerpted from the book *Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition*, by Krzysztof Cwalina and Brad Abrams.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ebaea-113">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="ebaea-113">In This Section</span></span>  
 [<span data-ttu-id="ebaea-114">Wskazówki dotyczące nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="ebaea-114">Naming Guidelines</span></span>](naming-guidelines.md)  
 <span data-ttu-id="ebaea-115">Zawiera wskazówki dotyczące nazewnictwa zestawów, przestrzeni nazw, typów i elementów członkowskich w bibliotekach klas.</span><span class="sxs-lookup"><span data-stu-id="ebaea-115">Provides guidelines for naming assemblies, namespaces, types, and members in class libraries.</span></span>  
  
 [<span data-ttu-id="ebaea-116">Wskazówki dotyczące projektowania typów</span><span class="sxs-lookup"><span data-stu-id="ebaea-116">Type Design Guidelines</span></span>](type.md)  
 <span data-ttu-id="ebaea-117">Zawiera wytyczne dotyczące używania klas statycznych i abstrakcyjnych, interfejsów, wyliczeń, struktur i innych typów.</span><span class="sxs-lookup"><span data-stu-id="ebaea-117">Provides guidelines for using static and abstract classes, interfaces, enumerations, structures, and other types.</span></span>  
  
 [<span data-ttu-id="ebaea-118">Wskazówki dotyczące projektowania elementów członkowskich</span><span class="sxs-lookup"><span data-stu-id="ebaea-118">Member Design Guidelines</span></span>](member.md)  
 <span data-ttu-id="ebaea-119">Zawiera wytyczne dotyczące projektowania i używania właściwości, metod, konstruktorów, pól, zdarzeń, operatorów i parametrów.</span><span class="sxs-lookup"><span data-stu-id="ebaea-119">Provides guidelines for designing and using properties, methods, constructors, fields, events, operators, and parameters.</span></span>  
  
 [<span data-ttu-id="ebaea-120">Projektowanie pod kątem rozszerzalności</span><span class="sxs-lookup"><span data-stu-id="ebaea-120">Designing for Extensibility</span></span>](designing-for-extensibility.md)  
 <span data-ttu-id="ebaea-121">Omawia mechanizmy rozszerzalności, takie jak podklasa, korzystanie z zdarzeń, wirtualne elementy członkowskie i wywołania zwrotne, oraz wyjaśnia, jak wybrać mechanizmy najlepiej spełniające wymagania platformy.</span><span class="sxs-lookup"><span data-stu-id="ebaea-121">Discusses extensibility mechanisms such as subclassing, using events, virtual members, and callbacks, and explains how to choose the mechanisms that best meet your framework's requirements.</span></span>  
  
 [<span data-ttu-id="ebaea-122">Wyjątki — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="ebaea-122">Design Guidelines for Exceptions</span></span>](exceptions.md)  
 <span data-ttu-id="ebaea-123">Zawiera opis wytycznych dotyczących projektowania, zgłaszania i przechwytywania wyjątków.</span><span class="sxs-lookup"><span data-stu-id="ebaea-123">Describes design guidelines for designing, throwing, and catching exceptions.</span></span>  
  
 [<span data-ttu-id="ebaea-124">Wskazówki dotyczące użycia</span><span class="sxs-lookup"><span data-stu-id="ebaea-124">Usage Guidelines</span></span>](usage-guidelines.md)  
 <span data-ttu-id="ebaea-125">Opisuje wskazówki dotyczące używania typów wspólnych, takich jak tablice, atrybuty i kolekcje, Obsługa serializacji i przeciążanie operatorów równości.</span><span class="sxs-lookup"><span data-stu-id="ebaea-125">Describes guidelines for using common types such as arrays, attributes, and collections, supporting serialization, and overloading equality operators.</span></span>  
  
 [<span data-ttu-id="ebaea-126">Typowe wzorce projektowe</span><span class="sxs-lookup"><span data-stu-id="ebaea-126">Common Design Patterns</span></span>](common-design-patterns.md)  
 <span data-ttu-id="ebaea-127">Zawiera wskazówki dotyczące wybierania i implementowania właściwości zależności.</span><span class="sxs-lookup"><span data-stu-id="ebaea-127">Provides guidelines for choosing and implementing dependency properties.</span></span>  
  
 <span data-ttu-id="ebaea-128">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="ebaea-128">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="ebaea-129">*Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="ebaea-129">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebaea-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ebaea-130">See also</span></span>

- [<span data-ttu-id="ebaea-131">Omówienie</span><span class="sxs-lookup"><span data-stu-id="ebaea-131">Overview</span></span>](../../framework/get-started/overview.md)
- [<span data-ttu-id="ebaea-132">Przewodnik programowania</span><span class="sxs-lookup"><span data-stu-id="ebaea-132">Development Guide</span></span>](../../framework/development-guide.md)
