---
title: Pieczętowanie
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- limiting extensibility
- classes [.NET Framework], sealing
- preventing customization
- sealed classes
ms.assetid: cc42267f-bb7a-427a-845e-df97408528d4
ms.openlocfilehash: ddf463e98fb6a9c5ccaae90e9cfc74b5691b13a9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743628"
---
# <a name="sealing"></a><span data-ttu-id="23d12-102">Pieczętowanie</span><span class="sxs-lookup"><span data-stu-id="23d12-102">Sealing</span></span>
<span data-ttu-id="23d12-103">Jedną z funkcji platform zorientowanych na obiektach jest to, że deweloperzy mogą je rozwijać i dostosowywać w sposób nieoczekiwany przez projektantów struktury.</span><span class="sxs-lookup"><span data-stu-id="23d12-103">One of the features of object-oriented frameworks is that developers can extend and customize them in ways unanticipated by the framework designers.</span></span> <span data-ttu-id="23d12-104">Jest to zarówno moc, jak i niebezpieczeństwo rozszerzalnego projektu.</span><span class="sxs-lookup"><span data-stu-id="23d12-104">This is both the power and danger of extensible design.</span></span> <span data-ttu-id="23d12-105">Podczas projektowania platformy, dlatego bardzo ważne jest staranne projektowanie pod kątem rozszerzalności, gdy jest to potrzebne, i ograniczanie rozszerzalności, gdy jest to niebezpieczne.</span><span class="sxs-lookup"><span data-stu-id="23d12-105">When you design your framework, it is, therefore, very important to carefully design for extensibility when it is desired, and to limit extensibility when it is dangerous.</span></span>

 <span data-ttu-id="23d12-106">Zaawansowany mechanizm, który uniemożliwia rozszerzanie rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="23d12-106">A powerful mechanism that prevents extensibility is sealing.</span></span> <span data-ttu-id="23d12-107">Możesz zapieczętować klasę lub poszczególnych członków.</span><span class="sxs-lookup"><span data-stu-id="23d12-107">You can seal either the class or individual members.</span></span> <span data-ttu-id="23d12-108">Opieczętowanie klasy uniemożliwia użytkownikom dziedziczenie z klasy.</span><span class="sxs-lookup"><span data-stu-id="23d12-108">Sealing a class prevents users from inheriting from the class.</span></span> <span data-ttu-id="23d12-109">Zapieczętowania elementu członkowskiego uniemożliwia użytkownikom zastępowanie określonego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="23d12-109">Sealing a member prevents users from overriding a particular member.</span></span>

 <span data-ttu-id="23d12-110">❌ nie zapieczętować klas bez dobrego powodu.</span><span class="sxs-lookup"><span data-stu-id="23d12-110">❌ DO NOT seal classes without having a good reason to do so.</span></span>

 <span data-ttu-id="23d12-111">Pieczętowanie klasy, ponieważ nie można myśleć, że scenariusz rozszerzalności nie jest dobrym powodem.</span><span class="sxs-lookup"><span data-stu-id="23d12-111">Sealing a class because you cannot think of an extensibility scenario is not a good reason.</span></span> <span data-ttu-id="23d12-112">Użytkownicy platformy, którzy mają dziedziczyć z klas z różnych nieoczywistych powodów, takich jak dodawanie wygodnych członków.</span><span class="sxs-lookup"><span data-stu-id="23d12-112">Framework users like to inherit from classes for various nonobvious reasons, like adding convenience members.</span></span> <span data-ttu-id="23d12-113">Zobacz [niezapieczętowane klasy](../../../docs/standard/design-guidelines/unsealed-classes.md) , aby poznać przykłady nieoczywistych przyczyn, które użytkownicy chcą dziedziczyć z typu.</span><span class="sxs-lookup"><span data-stu-id="23d12-113">See [Unsealed Classes](../../../docs/standard/design-guidelines/unsealed-classes.md) for examples of nonobvious reasons users want to inherit from a type.</span></span>

 <span data-ttu-id="23d12-114">Dobrym przyczynami zapieczętowania klasy są następujące:</span><span class="sxs-lookup"><span data-stu-id="23d12-114">Good reasons for sealing a class include the following:</span></span>

- <span data-ttu-id="23d12-115">Klasa jest klasą statyczną.</span><span class="sxs-lookup"><span data-stu-id="23d12-115">The class is a static class.</span></span> <span data-ttu-id="23d12-116">Zobacz [projekt klasy statycznej](../../../docs/standard/design-guidelines/static-class.md).</span><span class="sxs-lookup"><span data-stu-id="23d12-116">See [Static Class Design](../../../docs/standard/design-guidelines/static-class.md).</span></span>

- <span data-ttu-id="23d12-117">Klasa przechowuje wpisy tajne z uwzględnieniem zabezpieczeń w dziedziczonych chronionych składowych.</span><span class="sxs-lookup"><span data-stu-id="23d12-117">The class stores security-sensitive secrets in inherited protected members.</span></span>

- <span data-ttu-id="23d12-118">Klasa dziedziczy wiele wirtualnych elementów członkowskich, a koszt ich pieczętowania jest większa niż korzyści wynikające z pozostawienia niezapieczętowanej klasy.</span><span class="sxs-lookup"><span data-stu-id="23d12-118">The class inherits many virtual members and the cost of sealing them individually would outweigh the benefits of leaving the class unsealed.</span></span>

- <span data-ttu-id="23d12-119">Klasa jest atrybutem, który wymaga bardzo szybkiego wyszukiwania w środowisku uruchomieniowym.</span><span class="sxs-lookup"><span data-stu-id="23d12-119">The class is an attribute that requires very fast runtime look-up.</span></span> <span data-ttu-id="23d12-120">Zapieczętowane atrybuty mają nieco wyższy poziom wydajności niż niezapieczętowany.</span><span class="sxs-lookup"><span data-stu-id="23d12-120">Sealed attributes have slightly higher performance levels than unsealed ones.</span></span> <span data-ttu-id="23d12-121">Zobacz [atrybuty](../../../docs/standard/design-guidelines/attributes.md).</span><span class="sxs-lookup"><span data-stu-id="23d12-121">See [Attributes](../../../docs/standard/design-guidelines/attributes.md).</span></span>

 <span data-ttu-id="23d12-122">❌ nie deklaruj chronionych lub wirtualnych elementów członkowskich w typach zapieczętowanych.</span><span class="sxs-lookup"><span data-stu-id="23d12-122">❌ DO NOT declare protected or virtual members on sealed types.</span></span>

 <span data-ttu-id="23d12-123">Z definicji typy zapieczętowane nie mogą być dziedziczone z.</span><span class="sxs-lookup"><span data-stu-id="23d12-123">By definition, sealed types cannot be inherited from.</span></span> <span data-ttu-id="23d12-124">Oznacza to, że nie można wywoływać chronionych elementów członkowskich w typach zapieczętowanych, a metody wirtualne w typach zapieczętowanych nie mogą zostać zastąpione.</span><span class="sxs-lookup"><span data-stu-id="23d12-124">This means that protected members on sealed types cannot be called, and virtual methods on sealed types cannot be overridden.</span></span>

 <span data-ttu-id="23d12-125">✔️ ROZWAŻYĆ zastępowanie zastąpień elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="23d12-125">✔️ CONSIDER sealing members that you override.</span></span>

 <span data-ttu-id="23d12-126">Problemy, które mogą skutkować wprowadzeniem wirtualnych elementów członkowskich (omówione w [wirtualnych elementach członkowskich](../../../docs/standard/design-guidelines/virtual-members.md)), są również stosowane do zastąpień, chociaż mają nieco mniejszy stopień.</span><span class="sxs-lookup"><span data-stu-id="23d12-126">Problems that can result from introducing virtual members (discussed in [Virtual Members](../../../docs/standard/design-guidelines/virtual-members.md)) apply to overrides as well, although to a slightly lesser degree.</span></span> <span data-ttu-id="23d12-127">Nałożenie przesłonięcia osłony przed tymi problemami rozpoczyna się od tego momentu w hierarchii dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="23d12-127">Sealing an override shields you from these problems starting from that point in the inheritance hierarchy.</span></span>

 <span data-ttu-id="23d12-128">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="23d12-128">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="23d12-129">*Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="23d12-129">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="23d12-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="23d12-130">See also</span></span>

- [<span data-ttu-id="23d12-131">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="23d12-131">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="23d12-132">Projektowanie pod kątem rozszerzalności</span><span class="sxs-lookup"><span data-stu-id="23d12-132">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
- [<span data-ttu-id="23d12-133">Niezapieczętowane klasy</span><span class="sxs-lookup"><span data-stu-id="23d12-133">Unsealed Classes</span></span>](../../../docs/standard/design-guidelines/unsealed-classes.md)
