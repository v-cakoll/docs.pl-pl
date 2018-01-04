---
title: "Projekt — Konstruktor"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- member design guidelines, constructors
- constructors, design guidelines
- instance constructors
- type constructors
- virtual members
- constructors, types
- default constructors
- static constructors
ms.assetid: b4496afe-5fa7-4bb0-85ca-70b0ef21e6fc
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 66a297ed035f5afde06913b89f1f92dee5745f48
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="constructor-design"></a><span data-ttu-id="637d7-102">Projekt — Konstruktor</span><span class="sxs-lookup"><span data-stu-id="637d7-102">Constructor Design</span></span>
<span data-ttu-id="637d7-103">Istnieją dwa rodzaje konstruktory: wpisz konstruktorów i konstruktorów wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="637d7-103">There are two kinds of constructors: type constructors and instance constructors.</span></span>  
  
 <span data-ttu-id="637d7-104">Konstruktory typu są statyczne i są uruchamiane przez środowisko CLR, zanim będzie można użyć tego typu.</span><span class="sxs-lookup"><span data-stu-id="637d7-104">Type constructors are static and are run by the CLR before the type is used.</span></span> <span data-ttu-id="637d7-105">Konstruktory wystąpień uruchamiany po utworzeniu wystąpienia typu.</span><span class="sxs-lookup"><span data-stu-id="637d7-105">Instance constructors run when an instance of a type is created.</span></span>  
  
 <span data-ttu-id="637d7-106">Konstruktorów typów nie przyjmuje żadnych parametrów.</span><span class="sxs-lookup"><span data-stu-id="637d7-106">Type constructors cannot take any parameters.</span></span> <span data-ttu-id="637d7-107">Konstruktory wystąpień może.</span><span class="sxs-lookup"><span data-stu-id="637d7-107">Instance constructors can.</span></span> <span data-ttu-id="637d7-108">Konstruktory wystąpień, które nie przyjmuje żadnych parametrów są często nazywane domyślnych konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="637d7-108">Instance constructors that don’t take any parameters are often called default constructors.</span></span>  
  
 <span data-ttu-id="637d7-109">Konstruktory są najbardziej naturalny sposób można utworzyć wystąpienia typu.</span><span class="sxs-lookup"><span data-stu-id="637d7-109">Constructors are the most natural way to create instances of a type.</span></span> <span data-ttu-id="637d7-110">Większość deweloperów będzie wyszukiwanie i spróbuj użyć konstruktora przed uznają alternatywnych sposobów tworzenia wystąpień (na przykład metodami factory).</span><span class="sxs-lookup"><span data-stu-id="637d7-110">Most developers will search and try to use a constructor before they consider alternative ways of creating instances (such as factory methods).</span></span>  
  
 <span data-ttu-id="637d7-111">**ROZWAŻ ✓** udostępnia prostą, najlepiej domyślne, konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="637d7-111">**✓ CONSIDER** providing simple, ideally default, constructors.</span></span>  
  
 <span data-ttu-id="637d7-112">Prosty konstruktor ma bardzo małą liczbę parametrów, a wszystkie parametry są pierwotnych lub wyliczeń.</span><span class="sxs-lookup"><span data-stu-id="637d7-112">A simple constructor has a very small number of parameters, and all parameters are primitives or enums.</span></span> <span data-ttu-id="637d7-113">Takie proste konstruktorów zwiększyć użyteczność platformy.</span><span class="sxs-lookup"><span data-stu-id="637d7-113">Such simple constructors increase usability of the framework.</span></span>  
  
 <span data-ttu-id="637d7-114">**ROZWAŻ ✓** przy użyciu metody statycznej fabryki zamiast konstruktora semantykę Żądana operacja nie mapują bezpośrednio do tworzenia nowego wystąpienia, lub zgodnie z wytycznymi projektowania konstruktora tak nienaturalnej.</span><span class="sxs-lookup"><span data-stu-id="637d7-114">**✓ CONSIDER** using a static factory method instead of a constructor if the semantics of the desired operation do not map directly to the construction of a new instance, or if following the constructor design guidelines feels unnatural.</span></span>  
  
 <span data-ttu-id="637d7-115">**CZY ✓** parametry konstruktora jako skróty do ustawiania właściwości głównego.</span><span class="sxs-lookup"><span data-stu-id="637d7-115">**✓ DO** use constructor parameters as shortcuts for setting main properties.</span></span>  
  
 <span data-ttu-id="637d7-116">Nie powinna istnieć różnicy w semantyki między przy użyciu pustego konstruktora następuje niektóre zestawy właściwości i konstruktora z wieloma argumentami.</span><span class="sxs-lookup"><span data-stu-id="637d7-116">There should be no difference in semantics between using the empty constructor followed by some property sets and using a constructor with multiple arguments.</span></span>  
  
 <span data-ttu-id="637d7-117">**CZY ✓** Użyj takiej samej nazwy dla parametrami konstruktora a właściwością, jeśli używane są parametry konstruktora wystarczy ustawić właściwości.</span><span class="sxs-lookup"><span data-stu-id="637d7-117">**✓ DO** use the same name for constructor parameters and a property if the constructor parameters are used to simply set the property.</span></span>  
  
 <span data-ttu-id="637d7-118">Jedyną różnicą między tych parametrów i właściwości powinny być wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="637d7-118">The only difference between such parameters and the properties should be casing.</span></span>  
  
 <span data-ttu-id="637d7-119">**CZY ✓** minimalnego pracy w konstruktorze.</span><span class="sxs-lookup"><span data-stu-id="637d7-119">**✓ DO** minimal work in the constructor.</span></span>  
  
 <span data-ttu-id="637d7-120">Konstruktory należy wykonać dużo pracy innych niż przechwytywania parametrami konstruktora.</span><span class="sxs-lookup"><span data-stu-id="637d7-120">Constructors should not do much work other than capture the constructor parameters.</span></span> <span data-ttu-id="637d7-121">Powinno zostać opóźnione koszt żadnych innych operacji, dopóki wymagane.</span><span class="sxs-lookup"><span data-stu-id="637d7-121">The cost of any other processing should be delayed until required.</span></span>  
  
 <span data-ttu-id="637d7-122">**CZY ✓** zgłaszanie wyjątków z konstruktorów wystąpienia, w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="637d7-122">**✓ DO** throw exceptions from instance constructors, if appropriate.</span></span>  
  
 <span data-ttu-id="637d7-123">**CZY ✓** jawnie deklarować publicznego konstruktora domyślnego w klasach, jeśli takie Konstruktor jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="637d7-123">**✓ DO** explicitly declare the public default constructor in classes, if such a constructor is required.</span></span>  
  
 <span data-ttu-id="637d7-124">Wszystkie konstruktory nie jawnie zadeklarowana w typie, wiele języków (na przykład C#) automatycznie doda publiczny konstruktor domyślny.</span><span class="sxs-lookup"><span data-stu-id="637d7-124">If you don’t explicitly declare any constructors on a type, many languages (such as C#) will automatically add a public default constructor.</span></span> <span data-ttu-id="637d7-125">(Klas abstrakcyjnych get Konstruktor chroniony).</span><span class="sxs-lookup"><span data-stu-id="637d7-125">(Abstract classes get a protected constructor.)</span></span>  
  
 <span data-ttu-id="637d7-126">Dodawanie sparametryzowanym konstruktorze do klasy uniemożliwia kompilator Dodawanie domyślnego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="637d7-126">Adding a parameterized constructor to a class prevents the compiler from adding the default constructor.</span></span> <span data-ttu-id="637d7-127">Powoduje to często przypadkowemu najważniejszych zmian.</span><span class="sxs-lookup"><span data-stu-id="637d7-127">This often causes accidental breaking changes.</span></span>  
  
 <span data-ttu-id="637d7-128">**X należy UNIKAĆ** jawnie Definiowanie domyślnych konstruktorów w strukturach.</span><span class="sxs-lookup"><span data-stu-id="637d7-128">**X AVOID** explicitly defining default constructors on structs.</span></span>  
  
 <span data-ttu-id="637d7-129">Dzięki temu utworzenia tablicy szybciej, ponieważ jeśli nie zdefiniowano domyślnego konstruktora, ma być uruchamiane na każdym miejsca w tablicy.</span><span class="sxs-lookup"><span data-stu-id="637d7-129">This makes array creation faster, because if the default constructor is not defined, it does not have to be run on every slot in the array.</span></span> <span data-ttu-id="637d7-130">Należy pamiętać, że struktury mieć konstruktorów bez parametrów z tego powodu nie zezwalaj na wiele kompilatorów, w tym C#.</span><span class="sxs-lookup"><span data-stu-id="637d7-130">Note that many compilers, including C#, don’t allow structs to have parameterless constructors for this reason.</span></span>  
  
 <span data-ttu-id="637d7-131">**X należy UNIKAĆ** wywoływania wirtualne elementy członkowskie dla obiekt wewnątrz jego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="637d7-131">**X AVOID** calling virtual members on an object inside its constructor.</span></span>  
  
 <span data-ttu-id="637d7-132">Wywołanie elementu członkowskiego wirtualnego spowoduje najdalszych pochodnych zastąpienie do wywołania, nawet wtedy, gdy Konstruktor typu najbardziej pochodnej nie pełni uruchomiono jeszcze.</span><span class="sxs-lookup"><span data-stu-id="637d7-132">Calling a virtual member will cause the most derived override to be called, even if the constructor of the most derived type has not been fully run yet.</span></span>  
  
### <a name="type-constructor-guidelines"></a><span data-ttu-id="637d7-133">Wskazówki dotyczące konstruktora typu</span><span class="sxs-lookup"><span data-stu-id="637d7-133">Type Constructor Guidelines</span></span>  
 <span data-ttu-id="637d7-134">**CZY ✓** Oznacz jako prywatne konstruktory statyczne.</span><span class="sxs-lookup"><span data-stu-id="637d7-134">**✓ DO** make static constructors private.</span></span>  
  
 <span data-ttu-id="637d7-135">Konstruktor statyczny, nazywany również konstruktora klasy służy do inicjowania typu.</span><span class="sxs-lookup"><span data-stu-id="637d7-135">A static constructor, also called a class constructor, is used to initialize a type.</span></span> <span data-ttu-id="637d7-136">Środowisko CLR wywołuje konstruktor statyczny przed utworzeniu pierwszego wystąpienia typu lub są nazywane żadnych statycznych elementów członkowskich tego typu.</span><span class="sxs-lookup"><span data-stu-id="637d7-136">The CLR calls the static constructor before the first instance of the type is created or any static members on that type are called.</span></span> <span data-ttu-id="637d7-137">Użytkownik nie ma kontroli nad podczas wywołania konstruktora statycznego.</span><span class="sxs-lookup"><span data-stu-id="637d7-137">The user has no control over when the static constructor is called.</span></span> <span data-ttu-id="637d7-138">Jeśli Konstruktor statyczny nie jest prywatne, może być wywoływany przez kod innych niż środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="637d7-138">If a static constructor is not private, it can be called by code other than the CLR.</span></span> <span data-ttu-id="637d7-139">W zależności od operacji wykonywanych w Konstruktorze może to spowodować nieoczekiwane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="637d7-139">Depending on the operations performed in the constructor, this can cause unexpected behavior.</span></span> <span data-ttu-id="637d7-140">Kompilator języka C# wymusza konstruktory statyczne ma charakter prywatny.</span><span class="sxs-lookup"><span data-stu-id="637d7-140">The C# compiler forces static constructors to be private.</span></span>  
  
 <span data-ttu-id="637d7-141">**X nie** zgłaszanie wyjątków z konstruktorów statycznych.</span><span class="sxs-lookup"><span data-stu-id="637d7-141">**X DO NOT** throw exceptions from static constructors.</span></span>  
  
 <span data-ttu-id="637d7-142">Jeśli z konstruktora typu jest zgłaszany wyjątek, typ nie jest użyteczne w bieżącej domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="637d7-142">If an exception is thrown from a type constructor, the type is not usable in the current application domain.</span></span>  
  
 <span data-ttu-id="637d7-143">**ROZWAŻ ✓** inicjowanie pól statycznych zamiast jawnie konstruktory statyczne, ponieważ środowisko uruchomieniowe jest w stanie zoptymalizować wydajność typy, które nie mają jawnie zdefiniowanych Konstruktor statyczny.</span><span class="sxs-lookup"><span data-stu-id="637d7-143">**✓ CONSIDER** initializing static fields inline rather than explicitly using static constructors, because the runtime is able to optimize the performance of types that don’t have an explicitly defined static constructor.</span></span>  
  
 <span data-ttu-id="637d7-144">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="637d7-144">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="637d7-145">*Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="637d7-145">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="637d7-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="637d7-146">See Also</span></span>  
 [<span data-ttu-id="637d7-147">Element członkowski — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="637d7-147">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
 [<span data-ttu-id="637d7-148">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="637d7-148">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
