---
title: Pieczętowanie
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- limiting extensibility
- classes [.NET Framework], sealing
- preventing customization
- sealed classes
ms.assetid: cc42267f-bb7a-427a-845e-df97408528d4
caps.latest.revision: 10
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8a9ea7fd4f5df08631231db08ba7943a9c131012
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="sealing"></a><span data-ttu-id="43942-102">Pieczętowanie</span><span class="sxs-lookup"><span data-stu-id="43942-102">Sealing</span></span>
<span data-ttu-id="43942-103">Jedną z funkcji zorientowane obiektowo struktury jest deweloperzy może rozszerzyć i dostosować je w sposób nieprzewidziane przez projektantów framework.</span><span class="sxs-lookup"><span data-stu-id="43942-103">One of the features of object-oriented frameworks is that developers can extend and customize them in ways unanticipated by the framework designers.</span></span> <span data-ttu-id="43942-104">Jest to możliwości i zagrożenia extensible projektu.</span><span class="sxs-lookup"><span data-stu-id="43942-104">This is both the power and danger of extensible design.</span></span> <span data-ttu-id="43942-105">Podczas projektowania sieci framework, dlatego też jest bardzo ważne, dokładnie projektować pod kątem rozszerzalności, gdy wymagane jest i ograniczyć rozszerzalności, gdy jest niebezpieczne.</span><span class="sxs-lookup"><span data-stu-id="43942-105">When you design your framework, it is, therefore, very important to carefully design for extensibility when it is desired, and to limit extensibility when it is dangerous.</span></span>  
  
 <span data-ttu-id="43942-106">Pieczętowanie jest zaawansowanym mechanizmem, który uniemożliwia rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="43942-106">A powerful mechanism that prevents extensibility is sealing.</span></span> <span data-ttu-id="43942-107">Można Zapieczętuj klasę lub poszczególne elementy.</span><span class="sxs-lookup"><span data-stu-id="43942-107">You can seal either the class or individual members.</span></span> <span data-ttu-id="43942-108">Klasa pieczętowania uniemożliwia użytkownikom dziedziczenia z klasy.</span><span class="sxs-lookup"><span data-stu-id="43942-108">Sealing a class prevents users from inheriting from the class.</span></span> <span data-ttu-id="43942-109">Element członkowski pieczętowania uniemożliwia użytkownikom zastępowania określonego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="43942-109">Sealing a member prevents users from overriding a particular member.</span></span>  
  
 <span data-ttu-id="43942-110">**X nie** zapieczętować klasy bez konieczności powody, aby to zrobić.</span><span class="sxs-lookup"><span data-stu-id="43942-110">**X DO NOT** seal classes without having a good reason to do so.</span></span>  
  
 <span data-ttu-id="43942-111">Pieczętowania klasy, ponieważ nie można traktować scenariusza rozszerzalności nie jest dobrym przyczyny.</span><span class="sxs-lookup"><span data-stu-id="43942-111">Sealing a class because you cannot think of an extensibility scenario is not a good reason.</span></span> <span data-ttu-id="43942-112">Dziedziczenie z klasy z różnych powodów nonobvious, takich jak dodawanie członków wygody, takich jak użytkownicy Framework.</span><span class="sxs-lookup"><span data-stu-id="43942-112">Framework users like to inherit from classes for various nonobvious reasons, like adding convenience members.</span></span> <span data-ttu-id="43942-113">Zobacz [niezapieczętowanych klas](../../../docs/standard/design-guidelines/unsealed-classes.md) przykłady nonobvious powodów użytkownik chce dziedziczyć po typie.</span><span class="sxs-lookup"><span data-stu-id="43942-113">See [Unsealed Classes](../../../docs/standard/design-guidelines/unsealed-classes.md) for examples of nonobvious reasons users want to inherit from a type.</span></span>  
  
 <span data-ttu-id="43942-114">Powody do zamykania klasy są następujące:</span><span class="sxs-lookup"><span data-stu-id="43942-114">Good reasons for sealing a class include the following:</span></span>  
  
-   <span data-ttu-id="43942-115">Klasa jest klasie statycznej.</span><span class="sxs-lookup"><span data-stu-id="43942-115">The class is a static class.</span></span> <span data-ttu-id="43942-116">Zobacz [projekt klasy statycznej](../../../docs/standard/design-guidelines/static-class.md).</span><span class="sxs-lookup"><span data-stu-id="43942-116">See [Static Class Design](../../../docs/standard/design-guidelines/static-class.md).</span></span>  
  
-   <span data-ttu-id="43942-117">Klasa przechowuje klucze tajne istotnych dla zabezpieczeń w dziedziczonych chronionych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="43942-117">The class stores security-sensitive secrets in inherited protected members.</span></span>  
  
-   <span data-ttu-id="43942-118">Klasa dziedziczy wiele wirtualnych elementów członkowskich i koszt pieczętowania je pojedynczo czy przeważają korzyści opuszczania klasy niezapieczętowane.</span><span class="sxs-lookup"><span data-stu-id="43942-118">The class inherits many virtual members and the cost of sealing them individually would outweigh the benefits of leaving the class unsealed.</span></span>  
  
-   <span data-ttu-id="43942-119">Klasa jest atrybut, który wymaga środowiska uruchomieniowego bardzo szybko wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="43942-119">The class is an attribute that requires very fast runtime look-up.</span></span> <span data-ttu-id="43942-120">Atrybuty zapieczętowanego mają nieco wyższego poziomu wydajności niż niezapieczętowany z nich.</span><span class="sxs-lookup"><span data-stu-id="43942-120">Sealed attributes have slightly higher performance levels than unsealed ones.</span></span> <span data-ttu-id="43942-121">Zobacz [atrybutów](../../../docs/standard/design-guidelines/attributes.md).</span><span class="sxs-lookup"><span data-stu-id="43942-121">See [Attributes](../../../docs/standard/design-guidelines/attributes.md).</span></span>  
  
 <span data-ttu-id="43942-122">**X nie** deklaruj chronionych i wirtualnych elementów członkowskich w typach zapieczętowanych.</span><span class="sxs-lookup"><span data-stu-id="43942-122">**X DO NOT** declare protected or virtual members on sealed types.</span></span>  
  
 <span data-ttu-id="43942-123">Zgodnie z definicją typów zapieczętowanych nie może być dziedziczona z.</span><span class="sxs-lookup"><span data-stu-id="43942-123">By definition, sealed types cannot be inherited from.</span></span> <span data-ttu-id="43942-124">To oznacza, że nie można wywołać chronionych elementów członkowskich w typach zapieczętowanych i wirtualnych metod w typach zapieczętowanych nie można zastąpić.</span><span class="sxs-lookup"><span data-stu-id="43942-124">This means that protected members on sealed types cannot be called, and virtual methods on sealed types cannot be overridden.</span></span>  
  
 <span data-ttu-id="43942-125">**ROZWAŻ ✓** pieczętowania elementów członkowskich, które można zastąpić.</span><span class="sxs-lookup"><span data-stu-id="43942-125">**✓ CONSIDER** sealing members that you override.</span></span>  
  
 <span data-ttu-id="43942-126">Problemy, które mogą być wynikiem wprowadzenie wirtualnych elementów członkowskich (omówiona w [wirtualne elementy członkowskie](../../../docs/standard/design-guidelines/virtual-members.md)) dotyczą również zastąpienia chociaż nieco mniejszym stopniu.</span><span class="sxs-lookup"><span data-stu-id="43942-126">Problems that can result from introducing virtual members (discussed in [Virtual Members](../../../docs/standard/design-guidelines/virtual-members.md)) apply to overrides as well, although to a slightly lesser degree.</span></span> <span data-ttu-id="43942-127">Pieczętowanie zastąpienia osłony można z tych problemów, począwszy od tego momentu w hierarchii dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="43942-127">Sealing an override shields you from these problems starting from that point in the inheritance hierarchy.</span></span>  
  
 <span data-ttu-id="43942-128">*Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="43942-128">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="43942-129">*Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="43942-129">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43942-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="43942-130">See Also</span></span>  
 [<span data-ttu-id="43942-131">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="43942-131">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="43942-132">Projektowanie pod kątem rozszerzalności</span><span class="sxs-lookup"><span data-stu-id="43942-132">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 [<span data-ttu-id="43942-133">Niezapieczętowane klasy</span><span class="sxs-lookup"><span data-stu-id="43942-133">Unsealed Classes</span></span>](../../../docs/standard/design-guidelines/unsealed-classes.md)
