---
title: Pieczętowanie
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- limiting extensibility
- classes [.NET Framework], sealing
- preventing customization
- sealed classes
ms.assetid: cc42267f-bb7a-427a-845e-df97408528d4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6d8c445de44a69f6c0cb1eaefa0e59d682288318
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45614011"
---
# <a name="sealing"></a><span data-ttu-id="8eb5e-102">Pieczętowanie</span><span class="sxs-lookup"><span data-stu-id="8eb5e-102">Sealing</span></span>
<span data-ttu-id="8eb5e-103">Jest jedną z funkcji struktury zorientowane obiektowo, deweloperzy mogą rozszerzać i dostosowywać je w sposób nieoczekiwany przez projektantów framework.</span><span class="sxs-lookup"><span data-stu-id="8eb5e-103">One of the features of object-oriented frameworks is that developers can extend and customize them in ways unanticipated by the framework designers.</span></span> <span data-ttu-id="8eb5e-104">Jest to, możliwości i zagrożenia extensible projektu.</span><span class="sxs-lookup"><span data-stu-id="8eb5e-104">This is both the power and danger of extensible design.</span></span> <span data-ttu-id="8eb5e-105">Podczas projektowania preferowanej struktury, dlatego też jest bardzo ważne, uważnie projektować pod kątem rozszerzalności, jeśli pożądane jest i ograniczyć rozszerzalności, gdy jest niebezpieczne.</span><span class="sxs-lookup"><span data-stu-id="8eb5e-105">When you design your framework, it is, therefore, very important to carefully design for extensibility when it is desired, and to limit extensibility when it is dangerous.</span></span>  
  
 <span data-ttu-id="8eb5e-106">Pieczętowanie jest zaawansowany mechanizm, który uniemożliwia rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="8eb5e-106">A powerful mechanism that prevents extensibility is sealing.</span></span> <span data-ttu-id="8eb5e-107">Można Zapieczętuj klasę lub poszczególnych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="8eb5e-107">You can seal either the class or individual members.</span></span> <span data-ttu-id="8eb5e-108">Pieczętowanie klasę uniemożliwia użytkownikom dziedziczy z klasy.</span><span class="sxs-lookup"><span data-stu-id="8eb5e-108">Sealing a class prevents users from inheriting from the class.</span></span> <span data-ttu-id="8eb5e-109">Pieczętowanie członka uniemożliwia użytkownikom zastępowanie określonego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="8eb5e-109">Sealing a member prevents users from overriding a particular member.</span></span>  
  
 <span data-ttu-id="8eb5e-110">**X DO NOT** zapieczętować klasy bez konieczności powody, aby to zrobić.</span><span class="sxs-lookup"><span data-stu-id="8eb5e-110">**X DO NOT** seal classes without having a good reason to do so.</span></span>  
  
 <span data-ttu-id="8eb5e-111">Pieczętowanie klasy, ponieważ nie można traktować scenariusza rozszerzalności nie jest dobrze przemyślane.</span><span class="sxs-lookup"><span data-stu-id="8eb5e-111">Sealing a class because you cannot think of an extensibility scenario is not a good reason.</span></span> <span data-ttu-id="8eb5e-112">Użytkownicy Framework, takich jak dziedziczyć z klas z różnych powodów nonobvious, takich jak dodawanie członków wygody.</span><span class="sxs-lookup"><span data-stu-id="8eb5e-112">Framework users like to inherit from classes for various nonobvious reasons, like adding convenience members.</span></span> <span data-ttu-id="8eb5e-113">Zobacz [Niezapieczętowane klasy](../../../docs/standard/design-guidelines/unsealed-classes.md) przykładów dotyczących powodów nonobvious użytkownicy chcą dziedziczyć z typu.</span><span class="sxs-lookup"><span data-stu-id="8eb5e-113">See [Unsealed Classes](../../../docs/standard/design-guidelines/unsealed-classes.md) for examples of nonobvious reasons users want to inherit from a type.</span></span>  
  
 <span data-ttu-id="8eb5e-114">Powody do zamykania klasy są następujące:</span><span class="sxs-lookup"><span data-stu-id="8eb5e-114">Good reasons for sealing a class include the following:</span></span>  
  
-   <span data-ttu-id="8eb5e-115">Klasa jest klasą statyczną.</span><span class="sxs-lookup"><span data-stu-id="8eb5e-115">The class is a static class.</span></span> <span data-ttu-id="8eb5e-116">Zobacz [projekt klasy statycznej](../../../docs/standard/design-guidelines/static-class.md).</span><span class="sxs-lookup"><span data-stu-id="8eb5e-116">See [Static Class Design](../../../docs/standard/design-guidelines/static-class.md).</span></span>  
  
-   <span data-ttu-id="8eb5e-117">Klasa przechowuje wpisy tajne z istotnymi dla zabezpieczeń w elementy chronione dziedziczone.</span><span class="sxs-lookup"><span data-stu-id="8eb5e-117">The class stores security-sensitive secrets in inherited protected members.</span></span>  
  
-   <span data-ttu-id="8eb5e-118">Klasa dziedziczy wielu wirtualnych elementów członkowskich, a koszt pieczętowania je pojedynczo może przeważyć zalety opuszczania klasy niezapieczętowane.</span><span class="sxs-lookup"><span data-stu-id="8eb5e-118">The class inherits many virtual members and the cost of sealing them individually would outweigh the benefits of leaving the class unsealed.</span></span>  
  
-   <span data-ttu-id="8eb5e-119">Klasa jest atrybut, który wymaga bardzo szybkie środowiska uruchomieniowego wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="8eb5e-119">The class is an attribute that requires very fast runtime look-up.</span></span> <span data-ttu-id="8eb5e-120">Zapieczętowane atrybuty mają nieznacznie wyższe poziomy wydajności niż te niezapieczętowany.</span><span class="sxs-lookup"><span data-stu-id="8eb5e-120">Sealed attributes have slightly higher performance levels than unsealed ones.</span></span> <span data-ttu-id="8eb5e-121">zobacz [atrybuty](../../../docs/standard/design-guidelines/attributes.md).</span><span class="sxs-lookup"><span data-stu-id="8eb5e-121">See [Attributes](../../../docs/standard/design-guidelines/attributes.md).</span></span>  
  
 <span data-ttu-id="8eb5e-122">**X DO NOT** deklaruj chronionych i wirtualnych elementów członkowskich w typach zapieczętowanych.</span><span class="sxs-lookup"><span data-stu-id="8eb5e-122">**X DO NOT** declare protected or virtual members on sealed types.</span></span>  
  
 <span data-ttu-id="8eb5e-123">Z definicji po typach zapieczętowanych nie można dziedziczyć z.</span><span class="sxs-lookup"><span data-stu-id="8eb5e-123">By definition, sealed types cannot be inherited from.</span></span> <span data-ttu-id="8eb5e-124">Oznacza to, że chronionych elementów członkowskich w typach zapieczętowanych nie można wywołać metody, a wirtualne metody w typach zapieczętowanych nie można zastąpić.</span><span class="sxs-lookup"><span data-stu-id="8eb5e-124">This means that protected members on sealed types cannot be called, and virtual methods on sealed types cannot be overridden.</span></span>  
  
 <span data-ttu-id="8eb5e-125">**✓ CONSIDER** pieczętowania elementów członkowskich, które można zastąpić.</span><span class="sxs-lookup"><span data-stu-id="8eb5e-125">**✓ CONSIDER** sealing members that you override.</span></span>  
  
 <span data-ttu-id="8eb5e-126">Problemy, które mogą wynikać z jej poziomu wprowadzać wirtualnych elementów członkowskich (omówionych w [wirtualnych elementów członkowskich](../../../docs/standard/design-guidelines/virtual-members.md)) dotyczą przesłonięć, mimo że trochę mniejszym stopniu.</span><span class="sxs-lookup"><span data-stu-id="8eb5e-126">Problems that can result from introducing virtual members (discussed in [Virtual Members](../../../docs/standard/design-guidelines/virtual-members.md)) apply to overrides as well, although to a slightly lesser degree.</span></span> <span data-ttu-id="8eb5e-127">Pieczętowanie zastąpienia ochronnym możesz z tych problemów, począwszy od tego momentu w hierarchii dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="8eb5e-127">Sealing an override shields you from these problems starting from that point in the inheritance hierarchy.</span></span>  
  
 <span data-ttu-id="8eb5e-128">*Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="8eb5e-128">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="8eb5e-129">*Przedrukowano przez uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: konwencje Idiomy i wzorce wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams opublikowane 22 Oct 2008 przez Professional Addison Wesley jako część serii rozwoju Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="8eb5e-129">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8eb5e-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8eb5e-130">See also</span></span>

- [<span data-ttu-id="8eb5e-131">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="8eb5e-131">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
- [<span data-ttu-id="8eb5e-132">Projektowanie pod kątem rozszerzalności</span><span class="sxs-lookup"><span data-stu-id="8eb5e-132">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
- [<span data-ttu-id="8eb5e-133">Niezapieczętowane klasy</span><span class="sxs-lookup"><span data-stu-id="8eb5e-133">Unsealed Classes</span></span>](../../../docs/standard/design-guidelines/unsealed-classes.md)
