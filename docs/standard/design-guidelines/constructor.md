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
- parameterless constructors
- static constructors
ms.assetid: b4496afe-5fa7-4bb0-85ca-70b0ef21e6fc
ms.openlocfilehash: 7ab795cd4c6e0ff5e1451c05987848c41bd69577
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400604"
---
# <a name="constructor-design"></a><span data-ttu-id="eac7a-102">Projekt konstruktora</span><span class="sxs-lookup"><span data-stu-id="eac7a-102">Constructor Design</span></span>

<span data-ttu-id="eac7a-103">Istnieją dwa rodzaje konstruktorów: konstruktory typu i konstruktory wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="eac7a-103">There are two kinds of constructors: type constructors and instance constructors.</span></span>

<span data-ttu-id="eac7a-104">Konstruktory typu są statyczne i są uruchamiane przez CLR przed typem jest używany.</span><span class="sxs-lookup"><span data-stu-id="eac7a-104">Type constructors are static and are run by the CLR before the type is used.</span></span> <span data-ttu-id="eac7a-105">Konstruktory wystąpienia są uruchamiane po utworzeniu wystąpienia typu.</span><span class="sxs-lookup"><span data-stu-id="eac7a-105">Instance constructors run when an instance of a type is created.</span></span>

<span data-ttu-id="eac7a-106">Konstruktory typu nie mogą przyjmować żadnych parametrów.</span><span class="sxs-lookup"><span data-stu-id="eac7a-106">Type constructors cannot take any parameters.</span></span> <span data-ttu-id="eac7a-107">Konstruktory wystąpienia może.</span><span class="sxs-lookup"><span data-stu-id="eac7a-107">Instance constructors can.</span></span> <span data-ttu-id="eac7a-108">Konstruktory wystąpienia, które nie przyjmują żadnych parametrów są często nazywane konstruktorów bezparametrów.</span><span class="sxs-lookup"><span data-stu-id="eac7a-108">Instance constructors that don’t take any parameters are often called parameterless constructors.</span></span>

<span data-ttu-id="eac7a-109">Konstruktory są najbardziej naturalny sposób tworzenia wystąpień typu.</span><span class="sxs-lookup"><span data-stu-id="eac7a-109">Constructors are the most natural way to create instances of a type.</span></span> <span data-ttu-id="eac7a-110">Większość deweloperów będzie wyszukiwać i próbować użyć konstruktora, zanim rozważyalternatywne sposoby tworzenia wystąpień (takich jak metody fabryczne).</span><span class="sxs-lookup"><span data-stu-id="eac7a-110">Most developers will search and try to use a constructor before they consider alternative ways of creating instances (such as factory methods).</span></span>

<span data-ttu-id="eac7a-111">✔️ ROZWAŻ zapewnienie prostych, najlepiej domyślnych konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="eac7a-111">✔️ CONSIDER providing simple, ideally default, constructors.</span></span>

<span data-ttu-id="eac7a-112">Prosty konstruktor ma bardzo małą liczbę parametrów, a wszystkie parametry są prymitywami lub wyliczeniami.</span><span class="sxs-lookup"><span data-stu-id="eac7a-112">A simple constructor has a very small number of parameters, and all parameters are primitives or enums.</span></span> <span data-ttu-id="eac7a-113">Takie proste konstruktory zwiększają użyteczność struktury.</span><span class="sxs-lookup"><span data-stu-id="eac7a-113">Such simple constructors increase usability of the framework.</span></span>

<span data-ttu-id="eac7a-114">✔️ ZASTANÓW SIĘ przy użyciu statycznej metody fabryki zamiast konstruktora, jeśli semantyka żądanej operacji nie mapuje bezpośrednio do budowy nowego wystąpienia lub jeśli zgodnie z wytycznymi projektowymi konstruktora czuje się nienaturalne.</span><span class="sxs-lookup"><span data-stu-id="eac7a-114">✔️ CONSIDER using a static factory method instead of a constructor if the semantics of the desired operation do not map directly to the construction of a new instance, or if following the constructor design guidelines feels unnatural.</span></span>

<span data-ttu-id="eac7a-115">✔️ UŻYWAĆ parametrów konstruktora jako skrótów do ustawiania właściwości głównych.</span><span class="sxs-lookup"><span data-stu-id="eac7a-115">✔️ DO use constructor parameters as shortcuts for setting main properties.</span></span>

<span data-ttu-id="eac7a-116">Nie powinno być żadnej różnicy w semantyce między użyciem pustego konstruktora, a następnie niektóre zestawy właściwości i przy użyciu konstruktora z wieloma argumentami.</span><span class="sxs-lookup"><span data-stu-id="eac7a-116">There should be no difference in semantics between using the empty constructor followed by some property sets and using a constructor with multiple arguments.</span></span>

<span data-ttu-id="eac7a-117">✔️ należy użyć tej samej nazwy dla parametrów konstruktora i właściwości, jeśli parametry konstruktora są używane do prostego ustawienia właściwości.</span><span class="sxs-lookup"><span data-stu-id="eac7a-117">✔️ DO use the same name for constructor parameters and a property if the constructor parameters are used to simply set the property.</span></span>

<span data-ttu-id="eac7a-118">Jedyną różnicą między takimi parametrami a właściwościami powinna być obudowa.</span><span class="sxs-lookup"><span data-stu-id="eac7a-118">The only difference between such parameters and the properties should be casing.</span></span>

<span data-ttu-id="eac7a-119">✔️ zrobić minimalną pracę w konstruktorze.</span><span class="sxs-lookup"><span data-stu-id="eac7a-119">✔️ DO minimal work in the constructor.</span></span>

<span data-ttu-id="eac7a-120">Konstruktory nie należy wykonywać wiele pracy innych niż przechwytywanie parametrów konstruktora.</span><span class="sxs-lookup"><span data-stu-id="eac7a-120">Constructors should not do much work other than capture the constructor parameters.</span></span> <span data-ttu-id="eac7a-121">Koszt każdego innego przetwarzania powinien być opóźniony do momentu, gdy będzie to wymagane.</span><span class="sxs-lookup"><span data-stu-id="eac7a-121">The cost of any other processing should be delayed until required.</span></span>

<span data-ttu-id="eac7a-122">✔️ do zgłaszać wyjątki od konstruktorów instancji, jeśli jest to właściwe.</span><span class="sxs-lookup"><span data-stu-id="eac7a-122">✔️ DO throw exceptions from instance constructors, if appropriate.</span></span>

<span data-ttu-id="eac7a-123">✔️ do jawnie zadeklarować konstruktora parametrów publicznych w klasach, jeśli taki konstruktor jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="eac7a-123">✔️ DO explicitly declare the public parameterless constructor in classes, if such a constructor is required.</span></span>

<span data-ttu-id="eac7a-124">Jeśli nie jawnie zadeklarować żadnych konstruktorów na typ, wiele języków (takich jak C#) automatycznie doda konstruktora public parameterless.</span><span class="sxs-lookup"><span data-stu-id="eac7a-124">If you don’t explicitly declare any constructors on a type, many languages (such as C#) will automatically add a public parameterless constructor.</span></span> <span data-ttu-id="eac7a-125">(Klasy abstrakcyjne uzyskać chroniony konstruktora.)</span><span class="sxs-lookup"><span data-stu-id="eac7a-125">(Abstract classes get a protected constructor.)</span></span>

<span data-ttu-id="eac7a-126">Dodanie konstruktora sparametryzowanego do klasy uniemożliwia kompilatorowi dodawanie konstruktora bezparametrowego.</span><span class="sxs-lookup"><span data-stu-id="eac7a-126">Adding a parameterized constructor to a class prevents the compiler from adding the parameterless constructor.</span></span> <span data-ttu-id="eac7a-127">Często powoduje to przypadkowe zmiany.</span><span class="sxs-lookup"><span data-stu-id="eac7a-127">This often causes accidental breaking changes.</span></span>

<span data-ttu-id="eac7a-128">❌UNIKAJ jawnie definiowania konstruktorów bezparametrów na strukturach.</span><span class="sxs-lookup"><span data-stu-id="eac7a-128">❌ AVOID explicitly defining parameterless constructors on structs.</span></span>

<span data-ttu-id="eac7a-129">Dzięki temu tworzenie tablicy szybciej, ponieważ jeśli konstruktor bezparametrów nie jest zdefiniowany, nie musi być uruchamiany na każdym gnieździe w tablicy.</span><span class="sxs-lookup"><span data-stu-id="eac7a-129">This makes array creation faster, because if the parameterless constructor is not defined, it does not have to be run on every slot in the array.</span></span> <span data-ttu-id="eac7a-130">Należy zauważyć, że wiele kompilatorów, w tym C#, nie zezwalają structs mieć konstruktorów bezparametrów z tego powodu.</span><span class="sxs-lookup"><span data-stu-id="eac7a-130">Note that many compilers, including C#, don’t allow structs to have parameterless constructors for this reason.</span></span>

<span data-ttu-id="eac7a-131">❌UNIKAJ wywoływania wirtualnych elementów członkowskich na obiekcie wewnątrz jego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="eac7a-131">❌ AVOID calling virtual members on an object inside its constructor.</span></span>

<span data-ttu-id="eac7a-132">Wywołanie elementu członkowskiego wirtualnego spowoduje, że najbardziej pochodne zastąpić być wywoływane, nawet jeśli konstruktor typu najbardziej pochodnych nie został jeszcze w pełni uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="eac7a-132">Calling a virtual member will cause the most derived override to be called, even if the constructor of the most derived type has not been fully run yet.</span></span>

## <a name="type-constructor-guidelines"></a><span data-ttu-id="eac7a-133">Wskazówki dotyczące konstruktora tekstu</span><span class="sxs-lookup"><span data-stu-id="eac7a-133">Type Constructor Guidelines</span></span>

<span data-ttu-id="eac7a-134">✔️ zrobić statyczne konstruktory prywatne.</span><span class="sxs-lookup"><span data-stu-id="eac7a-134">✔️ DO make static constructors private.</span></span>

<span data-ttu-id="eac7a-135">Konstruktora statycznego, zwany także konstruktora klasy, jest używany do inicjowania typu.</span><span class="sxs-lookup"><span data-stu-id="eac7a-135">A static constructor, also called a class constructor, is used to initialize a type.</span></span> <span data-ttu-id="eac7a-136">CLR wywołuje konstruktora statycznego przed pierwszym wystąpieniem typu jest tworzony lub wszystkie elementy statyczne na tym typie są wywoływane.</span><span class="sxs-lookup"><span data-stu-id="eac7a-136">The CLR calls the static constructor before the first instance of the type is created or any static members on that type are called.</span></span> <span data-ttu-id="eac7a-137">Użytkownik nie ma kontroli nad, gdy konstruktor statyczny jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="eac7a-137">The user has no control over when the static constructor is called.</span></span> <span data-ttu-id="eac7a-138">Jeśli konstruktor statyczny nie jest prywatny, może być wywoływany przez kod inny niż CLR.</span><span class="sxs-lookup"><span data-stu-id="eac7a-138">If a static constructor is not private, it can be called by code other than the CLR.</span></span> <span data-ttu-id="eac7a-139">W zależności od operacji wykonywanych w konstruktorze może to spowodować nieoczekiwane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="eac7a-139">Depending on the operations performed in the constructor, this can cause unexpected behavior.</span></span> <span data-ttu-id="eac7a-140">Kompilator C# wymusza konstruktory statyczne jako prywatne.</span><span class="sxs-lookup"><span data-stu-id="eac7a-140">The C# compiler forces static constructors to be private.</span></span>

<span data-ttu-id="eac7a-141">❌NIE zgłaszaj wyjątków od konstruktorów statycznych.</span><span class="sxs-lookup"><span data-stu-id="eac7a-141">❌ DO NOT throw exceptions from static constructors.</span></span>

<span data-ttu-id="eac7a-142">Jeśli wyjątek jest generowany z konstruktora typu, typ nie jest użyteczny w bieżącej domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="eac7a-142">If an exception is thrown from a type constructor, the type is not usable in the current application domain.</span></span>

<span data-ttu-id="eac7a-143">✔️ NALEŻY WZIĄĆ POD UWAGĘ inicjowanie pól statycznych w wierszu, a nie jawnie przy użyciu konstruktorów statycznych, ponieważ czas wykonywania jest w stanie zoptymalizować wydajność typów, które nie mają jawnie zdefiniowane static konstruktora.</span><span class="sxs-lookup"><span data-stu-id="eac7a-143">✔️ CONSIDER initializing static fields inline rather than explicitly using static constructors, because the runtime is able to optimize the performance of types that don’t have an explicitly defined static constructor.</span></span>

<span data-ttu-id="eac7a-144">*Części © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="eac7a-144">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

<span data-ttu-id="eac7a-145">*Przedruk za zgodą Pearson Education, Inc. z [Framework Design Guidelines: Conventions, Idioms i Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) autorstwa Krzysztofa Cwaliny i Brada Abramsa, opublikowane 22 października 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="eac7a-145">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="eac7a-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="eac7a-146">See also</span></span>

- [<span data-ttu-id="eac7a-147">Element członkowski — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="eac7a-147">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)
- [<span data-ttu-id="eac7a-148">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="eac7a-148">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
