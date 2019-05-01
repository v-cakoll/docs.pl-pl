---
title: Projekt konstruktora
ms.date: 10/22/2008
ms.technology: dotnet-standard
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
author: KrzysztofCwalina
ms.openlocfilehash: 68192e3b75a120c73b82c34005d4dee650540bf3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61925466"
---
# <a name="constructor-design"></a><span data-ttu-id="a592e-102">Projekt konstruktora</span><span class="sxs-lookup"><span data-stu-id="a592e-102">Constructor Design</span></span>
<span data-ttu-id="a592e-103">Istnieją dwa rodzaje konstruktorów: wpisz konstruktorów i konstruktorów wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="a592e-103">There are two kinds of constructors: type constructors and instance constructors.</span></span>  
  
 <span data-ttu-id="a592e-104">Konstruktorzy typów są statyczne i są uruchamiane przez środowisko CLR, zanim typ jest używany.</span><span class="sxs-lookup"><span data-stu-id="a592e-104">Type constructors are static and are run by the CLR before the type is used.</span></span> <span data-ttu-id="a592e-105">Konstruktory wystąpień uruchamiane, gdy tworzone jest wystąpienie typu.</span><span class="sxs-lookup"><span data-stu-id="a592e-105">Instance constructors run when an instance of a type is created.</span></span>  
  
 <span data-ttu-id="a592e-106">Konstruktorzy typów nie przyjmuje żadnych parametrów.</span><span class="sxs-lookup"><span data-stu-id="a592e-106">Type constructors cannot take any parameters.</span></span> <span data-ttu-id="a592e-107">Konstruktory wystąpień może.</span><span class="sxs-lookup"><span data-stu-id="a592e-107">Instance constructors can.</span></span> <span data-ttu-id="a592e-108">Konstruktory wystąpień, które nie przyjmuje żadnych parametrów są często nazywane domyślnych konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="a592e-108">Instance constructors that don’t take any parameters are often called default constructors.</span></span>  
  
 <span data-ttu-id="a592e-109">Konstruktory są najbardziej naturalny sposób tworzenia wystąpień tego typu.</span><span class="sxs-lookup"><span data-stu-id="a592e-109">Constructors are the most natural way to create instances of a type.</span></span> <span data-ttu-id="a592e-110">Większość programistów poszuka i spróbuj użyć konstruktora, zanim rozważa alternatywne sposoby tworzenia wystąpień (takie jak metodach fabryki).</span><span class="sxs-lookup"><span data-stu-id="a592e-110">Most developers will search and try to use a constructor before they consider alternative ways of creating instances (such as factory methods).</span></span>  
  
 <span data-ttu-id="a592e-111">**✓ CONSIDER** udostępnia prostą, najlepiej domyślne, konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="a592e-111">**✓ CONSIDER** providing simple, ideally default, constructors.</span></span>  
  
 <span data-ttu-id="a592e-112">Proste Konstruktor ma bardzo niewielkiej liczby parametrów, a wszystkie parametry są w nim elementów podstawowych lub wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="a592e-112">A simple constructor has a very small number of parameters, and all parameters are primitives or enums.</span></span> <span data-ttu-id="a592e-113">Takie proste konstruktory zwiększyć użyteczność Framework.</span><span class="sxs-lookup"><span data-stu-id="a592e-113">Such simple constructors increase usability of the framework.</span></span>  
  
 <span data-ttu-id="a592e-114">**✓ CONSIDER** przy użyciu metody statycznej fabryki zamiast konstruktora semantykę Żądana operacja nie mapują bezpośrednio do tworzenia nowego wystąpienia, lub zgodnie z wytycznymi projektowania konstruktora tak nienaturalnej.</span><span class="sxs-lookup"><span data-stu-id="a592e-114">**✓ CONSIDER** using a static factory method instead of a constructor if the semantics of the desired operation do not map directly to the construction of a new instance, or if following the constructor design guidelines feels unnatural.</span></span>  
  
 <span data-ttu-id="a592e-115">**✓ DO** parametry konstruktora jako skróty do ustawiania właściwości głównego.</span><span class="sxs-lookup"><span data-stu-id="a592e-115">**✓ DO** use constructor parameters as shortcuts for setting main properties.</span></span>  
  
 <span data-ttu-id="a592e-116">Powinna istnieć nie różnice w semantyce między za pomocą pustego konstruktora, następuje niektórych zestawów właściwości i za pomocą konstruktora z wielu argumentów.</span><span class="sxs-lookup"><span data-stu-id="a592e-116">There should be no difference in semantics between using the empty constructor followed by some property sets and using a constructor with multiple arguments.</span></span>  
  
 <span data-ttu-id="a592e-117">**✓ DO** Użyj takiej samej nazwy dla parametrami konstruktora a właściwością, jeśli używane są parametry konstruktora wystarczy ustawić właściwości.</span><span class="sxs-lookup"><span data-stu-id="a592e-117">**✓ DO** use the same name for constructor parameters and a property if the constructor parameters are used to simply set the property.</span></span>  
  
 <span data-ttu-id="a592e-118">Jedyną różnicą między takie parametry i właściwości powinny być wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="a592e-118">The only difference between such parameters and the properties should be casing.</span></span>  
  
 <span data-ttu-id="a592e-119">**✓ DO** minimalnego pracy w konstruktorze.</span><span class="sxs-lookup"><span data-stu-id="a592e-119">**✓ DO** minimal work in the constructor.</span></span>  
  
 <span data-ttu-id="a592e-120">Konstruktory nie powinien wykonać dużo pracy innych niż przechwytywania parametry konstruktora.</span><span class="sxs-lookup"><span data-stu-id="a592e-120">Constructors should not do much work other than capture the constructor parameters.</span></span> <span data-ttu-id="a592e-121">Koszt dowolne inne procesy przetwarzania powinno zostać opóźnione, dopóki nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="a592e-121">The cost of any other processing should be delayed until required.</span></span>  
  
 <span data-ttu-id="a592e-122">**✓ DO** zgłaszanie wyjątków z konstruktorów wystąpienia, w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="a592e-122">**✓ DO** throw exceptions from instance constructors, if appropriate.</span></span>  
  
 <span data-ttu-id="a592e-123">**✓ DO** jawnie deklarować publicznego konstruktora domyślnego w klasach, jeśli takie Konstruktor jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="a592e-123">**✓ DO** explicitly declare the public default constructor in classes, if such a constructor is required.</span></span>  
  
 <span data-ttu-id="a592e-124">Jeśli w danym typie, nie jawnie deklarować żadnych konstruktorów, wielu języków (takich jak C#) spowoduje automatyczne dodanie publicznego konstruktora domyślnego.</span><span class="sxs-lookup"><span data-stu-id="a592e-124">If you don’t explicitly declare any constructors on a type, many languages (such as C#) will automatically add a public default constructor.</span></span> <span data-ttu-id="a592e-125">(Klasy abstrakcyjne uzyskać Konstruktor chroniony).</span><span class="sxs-lookup"><span data-stu-id="a592e-125">(Abstract classes get a protected constructor.)</span></span>  
  
 <span data-ttu-id="a592e-126">Dodawanie sparametryzowania konstruktora do klasy zapobiega dodawaniu konstruktora domyślnego przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="a592e-126">Adding a parameterized constructor to a class prevents the compiler from adding the default constructor.</span></span> <span data-ttu-id="a592e-127">To często powoduje, że przypadkowe przełomowe zmiany.</span><span class="sxs-lookup"><span data-stu-id="a592e-127">This often causes accidental breaking changes.</span></span>  
  
 <span data-ttu-id="a592e-128">**X AVOID** jawnie Definiowanie domyślnych konstruktorów w strukturach.</span><span class="sxs-lookup"><span data-stu-id="a592e-128">**X AVOID** explicitly defining default constructors on structs.</span></span>  
  
 <span data-ttu-id="a592e-129">Ułatwia to utworzenie tablicy szybciej, ponieważ jeśli nie zdefiniowano domyślnego konstruktora, nie ma być uruchamiane na każdego miejsca, w tablicy.</span><span class="sxs-lookup"><span data-stu-id="a592e-129">This makes array creation faster, because if the default constructor is not defined, it does not have to be run on every slot in the array.</span></span> <span data-ttu-id="a592e-130">Należy pamiętać, że wiele kompilatorów, w tym C#, nie zezwalaj na zwracanie struktur mieć konstruktory bez parametrów, dlatego.</span><span class="sxs-lookup"><span data-stu-id="a592e-130">Note that many compilers, including C#, don’t allow structs to have parameterless constructors for this reason.</span></span>  
  
 <span data-ttu-id="a592e-131">**X AVOID** wywoływania wirtualne elementy członkowskie dla obiekt wewnątrz jego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="a592e-131">**X AVOID** calling virtual members on an object inside its constructor.</span></span>  
  
 <span data-ttu-id="a592e-132">Wywołanie wirtualna elementu członkowskiego spowoduje zastąpienie najbardziej pochodnej, można wywołać, nawet wtedy, gdy Konstruktor typu najbardziej pochodnego nie został w pełni uruchomiony jeszcze.</span><span class="sxs-lookup"><span data-stu-id="a592e-132">Calling a virtual member will cause the most derived override to be called, even if the constructor of the most derived type has not been fully run yet.</span></span>  
  
### <a name="type-constructor-guidelines"></a><span data-ttu-id="a592e-133">Wytyczne dotyczące konstruktora typu</span><span class="sxs-lookup"><span data-stu-id="a592e-133">Type Constructor Guidelines</span></span>  
 <span data-ttu-id="a592e-134">**✓ DO** Oznacz jako prywatne konstruktory statyczne.</span><span class="sxs-lookup"><span data-stu-id="a592e-134">**✓ DO** make static constructors private.</span></span>  
  
 <span data-ttu-id="a592e-135">Statyczny Konstruktor, nazywany również konstruktora klasy jest używany do inicjowania typu.</span><span class="sxs-lookup"><span data-stu-id="a592e-135">A static constructor, also called a class constructor, is used to initialize a type.</span></span> <span data-ttu-id="a592e-136">Środowisko CLR wywołuje statyczny Konstruktor przed utworzeniu pierwszego wystąpienia tego typu lub wszelkich statyczne elementy członkowskie tego typu są wywoływane.</span><span class="sxs-lookup"><span data-stu-id="a592e-136">The CLR calls the static constructor before the first instance of the type is created or any static members on that type are called.</span></span> <span data-ttu-id="a592e-137">Użytkownik nie ma kontroli nad kiedy wywoływany jest konstruktor statyczny.</span><span class="sxs-lookup"><span data-stu-id="a592e-137">The user has no control over when the static constructor is called.</span></span> <span data-ttu-id="a592e-138">Jeśli Konstruktor statyczny nie jest prywatny, może ona zostać wywołana przez kod inny niż środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="a592e-138">If a static constructor is not private, it can be called by code other than the CLR.</span></span> <span data-ttu-id="a592e-139">W zależności od operacje wykonywane w Konstruktorze może to spowodować nieoczekiwane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="a592e-139">Depending on the operations performed in the constructor, this can cause unexpected behavior.</span></span> <span data-ttu-id="a592e-140">Kompilator języka C# wymusza konstruktorów statycznych jako prywatne.</span><span class="sxs-lookup"><span data-stu-id="a592e-140">The C# compiler forces static constructors to be private.</span></span>  
  
 <span data-ttu-id="a592e-141">**X DO NOT** zgłaszanie wyjątków z konstruktorów statycznych.</span><span class="sxs-lookup"><span data-stu-id="a592e-141">**X DO NOT** throw exceptions from static constructors.</span></span>  
  
 <span data-ttu-id="a592e-142">Jeśli wyjątek jest zgłaszany z konstruktora typu, typ nie jest użyteczny w bieżącej domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a592e-142">If an exception is thrown from a type constructor, the type is not usable in the current application domain.</span></span>  
  
 <span data-ttu-id="a592e-143">**✓ CONSIDER** inicjowanie pól statycznych zamiast jawnie konstruktory statyczne, ponieważ środowisko uruchomieniowe jest w stanie zoptymalizować wydajność typy, które nie mają jawnie zdefiniowanych Konstruktor statyczny.</span><span class="sxs-lookup"><span data-stu-id="a592e-143">**✓ CONSIDER** initializing static fields inline rather than explicitly using static constructors, because the runtime is able to optimize the performance of types that don’t have an explicitly defined static constructor.</span></span>  
  
 <span data-ttu-id="a592e-144">*Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="a592e-144">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="a592e-145">*Przedrukowano za uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: Konwencje, Idiomy i wzorców dla wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams publikowane 22 Oct 2008 przez Addison Wesley Professional w ramach serii rozwoju Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="a592e-145">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a592e-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a592e-146">See also</span></span>

- [<span data-ttu-id="a592e-147">Element członkowski — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="a592e-147">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)
- [<span data-ttu-id="a592e-148">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="a592e-148">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
