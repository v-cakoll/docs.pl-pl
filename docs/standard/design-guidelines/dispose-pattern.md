---
title: Wzorzec Dispose
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- Dispose method
- class library design guidelines [.NET Framework], Dispose method
- class library design guidelines [.NET Framework], Finalize method
- customizing Dispose method name
- Finalize method
ms.assetid: 31a6c13b-d6a2-492b-9a9f-e5238c983bcb
author: KrzysztofCwalina
ms.openlocfilehash: ee6e9898ae93e2e6628eadec150a3c9c05f5d9c5
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53147720"
---
# <a name="dispose-pattern"></a><span data-ttu-id="9d7f5-102">Wzorzec Dispose</span><span class="sxs-lookup"><span data-stu-id="9d7f5-102">Dispose Pattern</span></span>
<span data-ttu-id="9d7f5-103">Wszystkie programy uzyskuje jeden lub więcej zasobów systemowych, takich jak pamięć, systemu lub połączenia z bazą danych w trakcie ich wykonywania.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-103">All programs acquire one or more system resources, such as memory, system handles, or database connections, during the course of their execution.</span></span> <span data-ttu-id="9d7f5-104">Deweloperzy muszą należy zachować ostrożność, korzystając z takich zasobów systemowych, ponieważ muszą zostać zwolnione po zostały nabyte i używane.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-104">Developers have to be careful when using such system resources, because they must be released after they have been acquired and used.</span></span>  
  
 <span data-ttu-id="9d7f5-105">Środowisko CLR zapewnia obsługę automatyczne zarządzanie pamięcią.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-105">The CLR provides support for automatic memory management.</span></span> <span data-ttu-id="9d7f5-106">Pamięci zarządzanej (pamięci przydzielonej za pomocą operatora C# `new`) nie należy jawnie zwolnić.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-106">Managed memory (memory allocated using the C# operator `new`) does not need to be explicitly released.</span></span> <span data-ttu-id="9d7f5-107">Jest on zwalniany automatycznie przez moduł odśmiecania pamięci (GC).</span><span class="sxs-lookup"><span data-stu-id="9d7f5-107">It is released automatically by the garbage collector (GC).</span></span> <span data-ttu-id="9d7f5-108">To ułatwia deweloperom z żmudnym i trudne zadanie zwalnianie pamięci i był jednym z głównych powodów wyjątkowej produktywności zapewnianej przez program .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-108">This frees developers from the tedious and difficult task of releasing memory and has been one of the main reasons for the unprecedented productivity afforded by the .NET Framework.</span></span>  
  
 <span data-ttu-id="9d7f5-109">Niestety pamięci zarządzanej jest tylko jeden z wielu typów zasobów systemowych.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-109">Unfortunately, managed memory is just one of many types of system resources.</span></span> <span data-ttu-id="9d7f5-110">Zasobów innych niż pamięci zarządzanej nadal należy jawnie zwolnić i są określane jako niezarządzane zasoby.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-110">Resources other than managed memory still need to be released explicitly and are referred to as unmanaged resources.</span></span> <span data-ttu-id="9d7f5-111">Wykaz Globalny specjalnie nie jest przeznaczone do zarządzania takich niezarządzanych zasobów, co oznacza, że odpowiedzialność za zarządzanie niezarządzane zasoby znajdujące się w rękach deweloperów.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-111">The GC was specifically not designed to manage such unmanaged resources, which means that the responsibility for managing unmanaged resources lies in the hands of the developers.</span></span>  
  
 <span data-ttu-id="9d7f5-112">Środowisko CLR oferuje pomoc podczas zwalniania niezarządzanych zasobów.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-112">The CLR provides some help in releasing unmanaged resources.</span></span> <span data-ttu-id="9d7f5-113"><xref:System.Object?displayProperty=nameWithType> deklaruje metodę wirtualną <xref:System.Object.Finalize%2A> (nazywane również finalizatora) który jest wywoływany przez GC przed pamięci obiektu jest odzyskiwane w ramach odzyskiwania pamięci i może zostać zastąpiona w celu zwolnienia zasobów niezarządzanych.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-113"><xref:System.Object?displayProperty=nameWithType> declares a virtual method <xref:System.Object.Finalize%2A> (also called the finalizer) that is called by the GC before the object’s memory is reclaimed by the GC and can be overridden to release unmanaged resources.</span></span> <span data-ttu-id="9d7f5-114">Typy, które zastępują finalizator są określane jako typy sfinalizowania.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-114">Types that override the finalizer are referred to as finalizable types.</span></span>  
  
 <span data-ttu-id="9d7f5-115">Mimo że finalizatory są efektywne w niektórych scenariuszach oczyszczania, mają dwie istotne wady:</span><span class="sxs-lookup"><span data-stu-id="9d7f5-115">Although finalizers are effective in some cleanup scenarios, they have two significant drawbacks:</span></span>  
  
-   <span data-ttu-id="9d7f5-116">Finalizator jest wywoływana, gdy GC wykryje, że obiekt jest kwalifikuje się do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-116">The finalizer is called when the GC detects that an object is eligible for collection.</span></span> <span data-ttu-id="9d7f5-117">Dzieje się pewnego okresu nieokreślony czas po zasobu nie jest już potrzebna.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-117">This happens at some undetermined period of time after the resource is not needed anymore.</span></span> <span data-ttu-id="9d7f5-118">Opóźnienie między gdy deweloper można lub uzyskać dostęp do zwolnienia zasobu i czasu, gdy zasób jest faktycznie wydane przez finalizator może być niedopuszczalne w programach, które pobierać wiele ograniczonych zasobów (zasoby, które można łatwo wyczerpane) lub w przypadki, w których zasoby są kosztowne zachować używane (np. buforów dużych niezarządzanej pamięci).</span><span class="sxs-lookup"><span data-stu-id="9d7f5-118">The delay between when the developer could or would like to release the resource and the time when the resource is actually released by the finalizer might be unacceptable in programs that acquire many scarce resources (resources that can be easily exhausted) or in cases in which resources are costly to keep in use (e.g., large unmanaged memory buffers).</span></span>  
  
-   <span data-ttu-id="9d7f5-119">Gdy środowisko CLR musi wywołać finalizatora, należy odłożyć kolekcji pamięci obiektu, do czasu następnego zaokrąglanie wyrzucania elementów bezużytecznych (finalizatory Uruchom między operacjami).</span><span class="sxs-lookup"><span data-stu-id="9d7f5-119">When the CLR needs to call a finalizer, it must postpone collection of the object’s memory until the next round of garbage collection (the finalizers run between collections).</span></span> <span data-ttu-id="9d7f5-120">Oznacza to, że obiekt pamięci (i wszystkich obiektów, odwołuje się do) nie zostanie zwolnione przez dłuższy czas.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-120">This means that the object’s memory (and all objects it refers to) will not be released for a longer period of time.</span></span>  
  
 <span data-ttu-id="9d7f5-121">W związku z tym, opierając się wyłącznie na finalizatory mogą nie być odpowiednie w wielu scenariuszach, gdy ważne jest, aby odzyskać niezarządzane zasoby tak szybko, jak to możliwe, podczas pracy z ograniczonych zasobów lub w wysoce wydajnych scenariuszach, w którym dodano obciążenie GC Finalizacja jest nie do przyjęcia.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-121">Therefore, relying exclusively on finalizers might not be appropriate in many scenarios when it is important to reclaim unmanaged resources as quickly as possible, when dealing with scarce resources, or in highly performant scenarios in which the added GC overhead of finalization is unacceptable.</span></span>  
  
 <span data-ttu-id="9d7f5-122">Udostępnia platformę <xref:System.IDisposable?displayProperty=nameWithType> interfejs, który należy wdrożyć umożliwiają deweloperowi ręcznie zwolnić niezarządzane zasoby, jak tylko nie są wymagane.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-122">The Framework provides the <xref:System.IDisposable?displayProperty=nameWithType> interface that should be implemented to provide the developer a manual way to release unmanaged resources as soon as they are not needed.</span></span> <span data-ttu-id="9d7f5-123">Zapewnia także <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> metodę, która może sprawdzić GC został ręcznie usunięty z obiektu i nie trzeba można sfinalizować, w którym to przypadku obiektu można odzyskać pamięci wcześniej.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-123">It also provides the <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> method that can tell the GC that an object was manually disposed of and does not need to be finalized anymore, in which case the object’s memory can be reclaimed earlier.</span></span> <span data-ttu-id="9d7f5-124">Typami, które implementują `IDisposable` interfejsu są określane jako typy możliwe do likwidacji.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-124">Types that implement the `IDisposable` interface are referred to as disposable types.</span></span>  
  
 <span data-ttu-id="9d7f5-125">Wzorzec usuwania ma na celu standaryzacji użycie i wdrożenie finalizatory i `IDisposable` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-125">The Dispose Pattern is intended to standardize the usage and implementation of finalizers and the `IDisposable` interface.</span></span>  
  
 <span data-ttu-id="9d7f5-126">Głównym celem dla wzorca ma złożoność wdrożenia <xref:System.Object.Finalize%2A> i <xref:System.IDisposable.Dispose%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-126">The main motivation for the pattern is to reduce the complexity of the implementation of the <xref:System.Object.Finalize%2A> and the <xref:System.IDisposable.Dispose%2A> methods.</span></span> <span data-ttu-id="9d7f5-127">Złożoność wynika z faktu, że metody udostępniania niektórych, ale nie wszystkie ścieżki kodu (różnice są opisane w dalszej części rozdziału).</span><span class="sxs-lookup"><span data-stu-id="9d7f5-127">The complexity stems from the fact that the methods share some but not all code paths (the differences are described later in the chapter).</span></span> <span data-ttu-id="9d7f5-128">Ponadto istnieją historycznych przyczyny niektóre elementy wzorzec związanymi z ewolucją Obsługa języka dla funkcji zarządzania zasobami deterministyczna.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-128">In addition, there are historical reasons for some elements of the pattern related to the evolution of language support for deterministic resource management.</span></span>  
  
 <span data-ttu-id="9d7f5-129">**✓ DO** zaimplementować podstawowy wzorzec Dispose w typach zawierający wystąpienia typów, możliwe do rozporządzania.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-129">**✓ DO** implement the Basic Dispose Pattern on types containing instances of disposable types.</span></span> <span data-ttu-id="9d7f5-130">Zobacz [podstawowy wzorzec Dispose](#basic_pattern) sekcji, aby uzyskać szczegółowe informacje na temat podstawowy wzorzec.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-130">See the [Basic Dispose Pattern](#basic_pattern) section for details on the basic pattern.</span></span>  
  
 <span data-ttu-id="9d7f5-131">Jeśli typ jest odpowiedzialny za okres istnienia inne obiekty możliwe do rozporządzania, deweloperzy muszą mieć do rozporządzania, zbyt.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-131">If a type is responsible for the lifetime of other disposable objects, developers need a way to dispose of them, too.</span></span> <span data-ttu-id="9d7f5-132">Za pomocą kontenera `Dispose` metodą jest wygodny sposób, aby było to możliwe.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-132">Using the container’s `Dispose` method is a convenient way to make this possible.</span></span>  
  
 <span data-ttu-id="9d7f5-133">**✓ DO** wdrożenia podstawowy wzorzec Dispose i zapewnić finalizator typów zawierający zasoby, które mają zostać zwolniony jawnie i które nie mają finalizatory.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-133">**✓ DO** implement the Basic Dispose Pattern and provide a finalizer on types holding resources that need to be freed explicitly and that do not have finalizers.</span></span>  
  
 <span data-ttu-id="9d7f5-134">Na przykład wzorzec powinny zostać wdrożone na typach niezarządzanej pamięci, buforów przechowywania.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-134">For example, the pattern should be implemented on types storing unmanaged memory buffers.</span></span> <span data-ttu-id="9d7f5-135">[Sfinalizowania typy](#finalizable_types) sekcji omówiono wskazówki związane z implementacją finalizatorów.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-135">The [Finalizable Types](#finalizable_types) section discusses guidelines related to implementing finalizers.</span></span>  
  
 <span data-ttu-id="9d7f5-136">**✓ CONSIDER** implementacja podstawowe wzorca Dispose klasy się nie przytrzymaj niezarządzane zasoby lub obiekty możliwe do rozporządzania ale prawdopodobnie podtypów, które wykonują.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-136">**✓ CONSIDER** implementing the Basic Dispose Pattern on classes that themselves don’t hold unmanaged resources or disposable objects but are likely to have subtypes that do.</span></span>  
  
 <span data-ttu-id="9d7f5-137">Doskonałe przykładem jest <xref:System.IO.Stream?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-137">A great example of this is the <xref:System.IO.Stream?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="9d7f5-138">Abstrakcyjna klasa bazowa, która nie ma żadnych zasobów, ale większość jej podklasach czy i w związku z tym implementuje ten wzorzec.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-138">Although it is an abstract base class that doesn’t hold any resources, most of its subclasses do and because of this, it implements this pattern.</span></span>  
  
<a name="basic_pattern"></a>   
## <a name="basic-dispose-pattern"></a><span data-ttu-id="9d7f5-139">Wzorzec usuwania podstawowe</span><span class="sxs-lookup"><span data-stu-id="9d7f5-139">Basic Dispose Pattern</span></span>  
 <span data-ttu-id="9d7f5-140">Podstawową implementację wzorca obejmuje wdrażanie `System.IDisposable` interfejsu i deklarowanie `Dispose(bool)` metody, która implementuje całą logikę Oczyszczanie zasobów, aby współdzielić je między `Dispose` metody i opcjonalnie finalizatora.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-140">The basic implementation of the pattern involves implementing the `System.IDisposable` interface and declaring the `Dispose(bool)` method that implements all resource cleanup logic to be shared between the `Dispose` method and the optional finalizer.</span></span>  
  
 <span data-ttu-id="9d7f5-141">Proste wdrażanie wzorca podstawowego można znaleźć w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9d7f5-141">The following example shows a simple implementation of the basic pattern:</span></span>  
  
```csharp
public class DisposableResourceHolder : IDisposable {  
  
    private SafeHandle resource; // handle to a resource  
  
    public DisposableResourceHolder() {  
        this.resource = ... // allocates the resource  
    }  
  
    public void Dispose() {  
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
  
    protected virtual void Dispose(bool disposing) {  
        if (disposing) {  
            if (resource!= null) resource.Dispose();  
        }  
    }  
}  
```  
  
 <span data-ttu-id="9d7f5-142">Parametr logiczny `disposing` wskazuje, czy metoda została wywołana z `IDisposable.Dispose` implementacji lub finalizatora.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-142">The Boolean parameter `disposing` indicates whether the method was invoked from the `IDisposable.Dispose` implementation or from the finalizer.</span></span> <span data-ttu-id="9d7f5-143">`Dispose(bool)` Implementacji należy sprawdzić parametr przed uzyskaniem dostępu do innych obiektów odwołania (np. pole zasobu w poprzednim przykładzie).</span><span class="sxs-lookup"><span data-stu-id="9d7f5-143">The `Dispose(bool)` implementation should check the parameter before accessing other reference objects (e.g., the resource field in the preceding sample).</span></span> <span data-ttu-id="9d7f5-144">Takie obiekty powinny zostać oceniony jedynie, gdy metoda jest wywoływana z `IDisposable.Dispose` wdrożenia (gdy `disposing` parametr jest równa true).</span><span class="sxs-lookup"><span data-stu-id="9d7f5-144">Such objects should only be accessed when the method is called from the `IDisposable.Dispose` implementation (when the `disposing` parameter is equal to true).</span></span> <span data-ttu-id="9d7f5-145">Jeśli metoda jest wywoływana z finalizatora (`disposing` ma wartość false), nie powinien być dostępny innych obiektów.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-145">If the method is invoked from the finalizer (`disposing` is false), other objects should not be accessed.</span></span> <span data-ttu-id="9d7f5-146">Przyczyną jest, że obiekty sfinalizowaniu w kolejności nieprzewidywalne i dlatego ich lub dowolnej ich zależności mogą już mieć sfinalizowany.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-146">The reason is that objects are finalized in an unpredictable order and so they, or any of their dependencies, might already have been finalized.</span></span>  
  
 <span data-ttu-id="9d7f5-147">Ponadto w tej sekcji dotyczy klasach z atrybutem podstawowy, który już nie implementuje wzorzec Dispose.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-147">Also, this section applies to classes with a base that does not already implement the Dispose Pattern.</span></span> <span data-ttu-id="9d7f5-148">Jeśli dziedziczą z klasy, która już implementuje wzorzec, po prostu zastąpić `Dispose(bool)` metodę, aby zapewnić logikę oczyszczania dodatkowych zasobów.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-148">If you are inheriting from a class that already implements the pattern, simply override the `Dispose(bool)` method to provide additional resource cleanup logic.</span></span>  
  
 <span data-ttu-id="9d7f5-149">**✓ DO** zadeklarować `protected virtual void Dispose(bool disposing)` metody, można scentralizować całą logikę związany ze zwalnianiem zasoby niezarządzane.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-149">**✓ DO** declare a `protected virtual void Dispose(bool disposing)` method to centralize all logic related to releasing unmanaged resources.</span></span>  
  
 <span data-ttu-id="9d7f5-150">Czyszczenie wszystkich zasobów powinien wystąpić w przypadku tej metody.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-150">All resource cleanup should occur in this method.</span></span> <span data-ttu-id="9d7f5-151">Metoda jest wywoływana z obu finalizator i `IDisposable.Dispose` metody.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-151">The method is called from both the finalizer and the `IDisposable.Dispose` method.</span></span> <span data-ttu-id="9d7f5-152">Parametr nie będzie miał wartość false, jeśli jest wywoływany z wewnątrz finalizatora.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-152">The parameter will be false if being invoked from inside a finalizer.</span></span> <span data-ttu-id="9d7f5-153">Stosuje się do upewnij się, że każdy kod uruchomiony podczas finalizacji nie uzyskuje dostęp do innych obiektów sfinalizowania.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-153">It should be used to ensure any code running during finalization is not accessing other finalizable objects.</span></span> <span data-ttu-id="9d7f5-154">Szczegóły dotyczące implementowania finalizatory są opisane w następnej sekcji.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-154">Details of implementing finalizers are described in the next section.</span></span>  
  
```csharp
protected virtual void Dispose(bool disposing) {  
    if (disposing) {  
        if (resource!= null) resource.Dispose();  
    }  
}  
```  
  
 <span data-ttu-id="9d7f5-155">**✓ DO** zaimplementować `IDisposable` interfejsu, wywołując po prostu `Dispose(true)` następuje `GC.SuppressFinalize(this)`.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-155">**✓ DO** implement the `IDisposable` interface by simply calling `Dispose(true)` followed by `GC.SuppressFinalize(this)`.</span></span>  
  
 <span data-ttu-id="9d7f5-156">Wywołanie `SuppressFinalize` powinna występować tylko w przypadku `Dispose(true)` wykonuje z powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-156">The call to `SuppressFinalize` should only occur if `Dispose(true)` executes successfully.</span></span>  
  
```csharp
public void Dispose(){  
    Dispose(true);  
    GC.SuppressFinalize(this);  
}  
```  
  
 <span data-ttu-id="9d7f5-157">**X DO NOT** upewnij bez parametrów `Dispose` metody wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-157">**X DO NOT** make the parameterless `Dispose` method virtual.</span></span>  
  
 <span data-ttu-id="9d7f5-158">`Dispose(bool)` Metody jest tą, która powinna zostać zastąpiona przez podklasy.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-158">The `Dispose(bool)` method is the one that should be overridden by subclasses.</span></span>  
  
```csharp
// bad design  
public class DisposableResourceHolder : IDisposable {  
    public virtual void Dispose() { ... }  
    protected virtual void Dispose(bool disposing) { ... }  
}  
  
// good design  
public class DisposableResourceHolder : IDisposable {  
    public void Dispose() { ... }  
    protected virtual void Dispose(bool disposing) { ... }  
}  
```  
  
 <span data-ttu-id="9d7f5-159">**X DO NOT** zadeklarować wszystkie przeciążenia `Dispose` metody inne niż `Dispose()` i `Dispose(bool)`.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-159">**X DO NOT** declare any overloads of the `Dispose` method other than `Dispose()` and `Dispose(bool)`.</span></span>  
  
 <span data-ttu-id="9d7f5-160">`Dispose` należy rozważyć słowem zastrzeżonym, ułatwiające skodyfikować tego wzorca i uniknąć nieporozumień wśród implementacje, użytkowników i kompilatory.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-160">`Dispose` should be considered a reserved word to help codify this pattern and prevent confusion among implementers, users, and compilers.</span></span> <span data-ttu-id="9d7f5-161">W przypadku niektórych języków może wybrać automatycznie implementacja tego wzorca od niektórych typów.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-161">Some languages might choose to automatically implement this pattern on certain types.</span></span>  
  
 <span data-ttu-id="9d7f5-162">**✓ DO** Zezwalaj `Dispose(bool)` metodę można wywołać więcej niż raz.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-162">**✓ DO** allow the `Dispose(bool)` method to be called more than once.</span></span> <span data-ttu-id="9d7f5-163">Metoda może wybrać nic nie rób po pierwszym wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-163">The method might choose to do nothing after the first call.</span></span>  
  
```csharp
public class DisposableResourceHolder : IDisposable {  
  
    bool disposed = false;  
  
    protected virtual void Dispose(bool disposing) {  
        if (disposed) return;  
        // cleanup  
        ...  
        disposed = true;  
    }  
}  
```  
  
 <span data-ttu-id="9d7f5-164">**X AVOID** Zgłaszanie wyjątku z poziomu `Dispose(bool)` z wyjątkiem sytuacji krytycznych gdzie zawierającego proces został uszkodzony (przecieków, niespójna udostępnionego itp.).</span><span class="sxs-lookup"><span data-stu-id="9d7f5-164">**X AVOID** throwing an exception from within `Dispose(bool)` except under critical situations where the containing process has been corrupted (leaks, inconsistent shared state, etc.).</span></span>  
  
 <span data-ttu-id="9d7f5-165">Użytkownicy oczekują, że wywołanie `Dispose` nie zgłosi wyjątek.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-165">Users expect that a call to `Dispose` will not raise an exception.</span></span>  
  
 <span data-ttu-id="9d7f5-166">Jeśli `Dispose` może zgłosić wyjątek, dalsze logiki oczyszczania blok finally nie zostanie wykonany.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-166">If `Dispose` could raise an exception, further finally-block cleanup logic will not execute.</span></span> <span data-ttu-id="9d7f5-167">Aby obejść ten problem, użytkownik będzie musiał opakować każde wywołanie `Dispose` (w ramach bloku finally!) w bloku try, co prowadzi do obsługi bardzo złożonych oczyszczania.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-167">To work around this, the user would need to wrap every call to `Dispose` (within the finally block!) in a try block, which leads to very complex cleanup handlers.</span></span> <span data-ttu-id="9d7f5-168">Jeśli wykonywane `Dispose(bool disposing)` metody, nigdy nie throw wyjątek, jeśli disposing ma wartość false, który.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-168">If executing a `Dispose(bool disposing)` method, never throw an exception if disposing is false.</span></span> <span data-ttu-id="9d7f5-169">To zakończenie procesu jeśli wykonywane w kontekście finalizatora.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-169">Doing so will terminate the process if executing inside a finalizer context.</span></span>  
  
 <span data-ttu-id="9d7f5-170">**✓ DO** throw <xref:System.ObjectDisposedException> z dowolnego elementu członkowskiego, który nie może zostać użyty obiekt został usunięty z.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-170">**✓ DO** throw an <xref:System.ObjectDisposedException> from any member that cannot be used after the object has been disposed of.</span></span>  
  
```csharp
public class DisposableResourceHolder : IDisposable {  
    bool disposed = false;  
    SafeHandle resource; // handle to a resource  
  
    public void DoSomething() {  
        if (disposed) throw new ObjectDisposedException(...);  
        // now call some native methods using the resource   
        ...  
    }  
    protected virtual void Dispose(bool disposing) {  
        if (disposed) return;  
        // cleanup  
        ...  
        disposed = true;  
    }  
}  
```  
  
 <span data-ttu-id="9d7f5-171">**✓ CONSIDER** udostępnia metody `Close()`, oprócz `Dispose()`, jeśli jest blisko terminologii w obszarze.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-171">**✓ CONSIDER** providing method `Close()`, in addition to the `Dispose()`, if close is standard terminology in the area.</span></span>  
  
 <span data-ttu-id="9d7f5-172">Po wykonaniu tej czynności jest ważne, `Close` taka sama jak implementacja `Dispose` i rozważ zaimplementowanie `IDisposable.Dispose` metoda jawnie.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-172">When doing so, it is important that you make the `Close` implementation identical to `Dispose` and consider implementing the `IDisposable.Dispose` method explicitly.</span></span>  
  
```csharp
public class Stream : IDisposable {  
    IDisposable.Dispose() {  
        Close();  
    }  
    public void Close() {  
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
}  
```  
  
<a name="finalizable_types"></a>   
## <a name="finalizable-types"></a><span data-ttu-id="9d7f5-173">Typy sfinalizowania</span><span class="sxs-lookup"><span data-stu-id="9d7f5-173">Finalizable Types</span></span>  
 <span data-ttu-id="9d7f5-174">Typy sfinalizowania są typy, które rozszerzają podstawowy wzorzec Dispose zastępowanie finalizator i podając ścieżkę kodu finalizacji w `Dispose(bool)` metody.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-174">Finalizable types are types that extend the Basic Dispose Pattern by overriding the finalizer and providing finalization code path in the `Dispose(bool)` method.</span></span>  
  
 <span data-ttu-id="9d7f5-175">Finalizatory są bardzo trudne do zaimplementowania poprawnie, przede wszystkim, ponieważ niektóre (zwykle jest to ważny) założeń dotyczących stanu systemu nie może wprowadzać podczas ich wykonywania.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-175">Finalizers are notoriously difficult to implement correctly, primarily because you cannot make certain (normally valid) assumptions about the state of the system during their execution.</span></span> <span data-ttu-id="9d7f5-176">Szczególną uwagę należy uwzględnić poniższe zalecenia.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-176">The following guidelines should be taken into careful consideration.</span></span>  
  
 <span data-ttu-id="9d7f5-177">Należy pamiętać, że niektóre wytyczne mają zastosowanie nie tylko do `Finalize` metody, ale na wszelki kod wywołuje z finalizatora.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-177">Note that some of the guidelines apply not just to the `Finalize` method, but to any code called from a finalizer.</span></span> <span data-ttu-id="9d7f5-178">W przypadku podstawowy Dispose wzorzec uprzednio zdefiniowany, oznacza to, że logika, która wykonuje wewnątrz `Dispose(bool disposing)` podczas `disposing` parametr ma wartość false.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-178">In the case of the Basic Dispose Pattern previously defined, this means logic that executes inside `Dispose(bool disposing)` when the `disposing` parameter is false.</span></span>  
  
 <span data-ttu-id="9d7f5-179">Jeśli klasa bazowa już jest sfinalizowania, implementuje podstawowy wzorzec Dispose nie powinna zostać przesłonięta `Finalize` ponownie.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-179">If the base class already is finalizable and implements the Basic Dispose Pattern, you should not override `Finalize` again.</span></span> <span data-ttu-id="9d7f5-180">Zamiast tego należy po prostu zastąpić `Dispose(bool)` metodę, aby zapewnić logikę oczyszczania dodatkowych zasobów.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-180">You should instead just override the `Dispose(bool)` method to provide additional resource cleanup logic.</span></span>  
  
 <span data-ttu-id="9d7f5-181">Poniższy kod przedstawia przykład sfinalizowania typu:</span><span class="sxs-lookup"><span data-stu-id="9d7f5-181">The following code shows an example of a finalizable type:</span></span>  
  
```csharp
public class ComplexResourceHolder : IDisposable {  
  
    private IntPtr buffer; // unmanaged memory buffer  
    private SafeHandle resource; // disposable handle to a resource  
  
    public ComplexResourceHolder() {  
        this.buffer = ... // allocates memory  
        this.resource = ... // allocates the resource  
    }  
  
    protected virtual void Dispose(bool disposing) {  
        ReleaseBuffer(buffer); // release unmanaged memory  
        if (disposing) { // release other disposable objects  
            if (resource!= null) resource.Dispose();  
        }  
    }  
  
    ~ComplexResourceHolder() {
        Dispose(false);  
    }  
  
    public void Dispose() {
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
}  
```  
  
 <span data-ttu-id="9d7f5-182">**X AVOID** wprowadzania finalizable typów.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-182">**X AVOID** making types finalizable.</span></span>  
  
 <span data-ttu-id="9d7f5-183">Zastanów się uważnie każdy przypadek, w którym uważasz, że finalizator jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-183">Carefully consider any case in which you think a finalizer is needed.</span></span> <span data-ttu-id="9d7f5-184">Ma faktycznego koszt związany z wystąpień finalizatory z punktu widzenia złożoności wydajności i kodu.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-184">There is a real cost associated with instances with finalizers, from both a performance and code complexity standpoint.</span></span> <span data-ttu-id="9d7f5-185">Preferuj przy użyciu otoki zasobów, takich jak <xref:System.Runtime.InteropServices.SafeHandle> celu hermetyzowania niezarządzanych zasobów, jeśli jest to możliwe, w którym to przypadku finalizatora staje się niepotrzebne ponieważ otoki jest odpowiedzialny za własne czyszczenie zasobów.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-185">Prefer using resource wrappers such as <xref:System.Runtime.InteropServices.SafeHandle> to encapsulate unmanaged resources where possible, in which case a finalizer becomes unnecessary because the wrapper is responsible for its own resource cleanup.</span></span>  
  
 <span data-ttu-id="9d7f5-186">**X DO NOT** tworzenie finalizable typów wartości.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-186">**X DO NOT** make value types finalizable.</span></span>  
  
 <span data-ttu-id="9d7f5-187">Tylko typy odwołań Pobierz faktycznie zatwierdzony przez środowisko CLR i zignorowana każda próba umieścić finalizatora dla typu wartości.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-187">Only reference types actually get finalized by the CLR, and thus any attempt to place a finalizer on a value type will be ignored.</span></span> <span data-ttu-id="9d7f5-188">Kompilatory C# i C++ wymuszają tę regułę.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-188">The C# and C++ compilers enforce this rule.</span></span>  
  
 <span data-ttu-id="9d7f5-189">**✓ DO** upewnij typu finalizable, jeśli typ jest odpowiedzialny za zwolnienie niezarządzanego zasobu, który nie ma własną finalizatora.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-189">**✓ DO** make a type finalizable if the type is responsible for releasing an unmanaged resource that does not have its own finalizer.</span></span>  
  
 <span data-ttu-id="9d7f5-190">Podczas implementowania finalizator, wystarczy wywołać `Dispose(false)` i umieść całą logikę Oczyszczanie zasobów wewnątrz `Dispose(bool disposing)` metody.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-190">When implementing the finalizer, simply call `Dispose(false)` and place all resource cleanup logic inside the `Dispose(bool disposing)` method.</span></span>  
  
```csharp
public class ComplexResourceHolder : IDisposable {  
  
    ~ComplexResourceHolder() {
        Dispose(false);  
    }  
  
    protected virtual void Dispose(bool disposing) {
        ...  
    }  
}  
```  
  
 <span data-ttu-id="9d7f5-191">**✓ DO** wdrożenia dla każdego typu finalizable podstawowy wzorzec Dispose.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-191">**✓ DO** implement the Basic Dispose Pattern on every finalizable type.</span></span>  
  
 <span data-ttu-id="9d7f5-192">Dzięki temu użytkownicy typu oznacza jawnie Przeprowadź czyszczenie deterministyczne tych samych zasobów, za które odpowiada finalizator.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-192">This gives users of the type a means to explicitly perform deterministic cleanup of those same resources for which the finalizer is responsible.</span></span>  
  
 <span data-ttu-id="9d7f5-193">**X DO NOT** uzyskać dostępu do żadnych obiektów finalizable w ścieżce kodu finalizator, ponieważ istnieje duże ryzyko, że ich będzie mieć już sfinalizowany.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-193">**X DO NOT** access any finalizable objects in the finalizer code path, because there is significant risk that they will have already been finalized.</span></span>  
  
 <span data-ttu-id="9d7f5-194">Na przykład, które można sfinalizować obiekt A, który odwołuje się do innego obiektu sfinalizowania B niezawodnie nie można użyć B w A finalizatora, lub na odwrót.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-194">For example, a finalizable object A that has a reference to another finalizable object B cannot reliably use B in A’s finalizer, or vice versa.</span></span> <span data-ttu-id="9d7f5-195">Finalizatory są wywoływane w kolejności losowej (ograniczony słabe gwarancja szeregowania krytyczna finalizacja).</span><span class="sxs-lookup"><span data-stu-id="9d7f5-195">Finalizers are called in a random order (short of a weak ordering guarantee for critical finalization).</span></span>  
  
 <span data-ttu-id="9d7f5-196">Ponadto należy pamiętać, że obiekty przechowywane w zmiennych statycznych będą Pobierz zbierane w niektórych punktach podczas zwalniania domeny aplikacji lub w trakcie proces zostanie zakończony.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-196">Also, be aware that objects stored in static variables will get collected at certain points during an application domain unload or while exiting the process.</span></span> <span data-ttu-id="9d7f5-197">Uzyskiwanie dostępu do zmienną statyczną, która odwołuje się do sfinalizowania obiektu (lub wywoływania statycznej metody, która może korzystać wartości przechowywane w zmiennych statycznych) może nie być bezpieczne, jeśli <xref:System.Environment.HasShutdownStarted%2A?displayProperty=nameWithType> zwraca wartość true.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-197">Accessing a static variable that refers to a finalizable object (or calling a static method that might use values stored in static variables) might not be safe if <xref:System.Environment.HasShutdownStarted%2A?displayProperty=nameWithType> returns true.</span></span>  
  
 <span data-ttu-id="9d7f5-198">**✓ DO** upewnij Twojej `Finalize` metody chronione.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-198">**✓ DO** make your `Finalize` method protected.</span></span>  
  
 <span data-ttu-id="9d7f5-199">Programiści języka C#, C++ i VB.NET nie są już martwić się o to, ponieważ kompilatory pomóc wymusić niniejszych wytycznych.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-199">C#, C++, and VB.NET developers do not need to worry about this, because the compilers help to enforce this guideline.</span></span>  
  
 <span data-ttu-id="9d7f5-200">**X DO NOT** escape let wyjątki od logiki finalizator, z wyjątkiem błędy krytyczne systemu.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-200">**X DO NOT** let exceptions escape from the finalizer logic, except for system-critical failures.</span></span>  
  
 <span data-ttu-id="9d7f5-201">Jeśli wyjątek jest zgłaszany z finalizatora, środowisko CLR spowoduje wyłączenie całego procesu (począwszy od .NET Framework w wersji 2.0), inne finalizatory uniemożliwia wykonywanie i zasoby z udostępniane w sposób kontrolowany.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-201">If an exception is thrown from a finalizer, the CLR will shut down the entire process (as of .NET Framework version 2.0), preventing other finalizers from executing and resources from being released in a controlled manner.</span></span>  
  
 <span data-ttu-id="9d7f5-202">**✓ CONSIDER** tworzenie i używanie obiektu finalizable krytycznego (typ z hierarchii typów, który zawiera <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject>) w sytuacjach, w których finalizator bezwzględnie wykonać nawet w wypadku zwalnia domeny wymuszone aplikacji i wątków przerywa.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-202">**✓ CONSIDER** creating and using a critical finalizable object (a type with a type hierarchy that contains <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject>) for situations in which a finalizer absolutely must execute even in the face of forced application domain unloads and thread aborts.</span></span>  
  
 <span data-ttu-id="9d7f5-203">*Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="9d7f5-203">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="9d7f5-204">*Przedrukowano za uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: Konwencje, Idiomy i wzorców dla wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams publikowane 22 Oct 2008 przez Addison Wesley Professional w ramach serii rozwoju Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="9d7f5-204">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d7f5-205">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9d7f5-205">See also</span></span>

- <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>  
- <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="9d7f5-206">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="9d7f5-206">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
- [<span data-ttu-id="9d7f5-207">Często używane wzorce projektowe</span><span class="sxs-lookup"><span data-stu-id="9d7f5-207">Common Design Patterns</span></span>](../../../docs/standard/design-guidelines/common-design-patterns.md)  
- [<span data-ttu-id="9d7f5-208">Odzyskiwanie pamięci</span><span class="sxs-lookup"><span data-stu-id="9d7f5-208">Garbage Collection</span></span>](../../../docs/standard/garbage-collection/index.md)
