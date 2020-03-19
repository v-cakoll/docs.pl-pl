---
title: 'Samouczek: Tworzenie dostawcy typów'
description: Dowiedz się, jak utworzyć własne dostawców typu F# w F# 3.0, sprawdzając kilku prostych dostawców typów, aby zilustrować podstawowe pojęcia.
ms.date: 11/04/2019
ms.openlocfilehash: 3b8145d4c2d8bf96b6dcf66de02e9f2d83927d74
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186125"
---
# <a name="tutorial-create-a-type-provider"></a><span data-ttu-id="ed997-103">Samouczek: Tworzenie dostawcy typów</span><span class="sxs-lookup"><span data-stu-id="ed997-103">Tutorial: Create a Type Provider</span></span>

<span data-ttu-id="ed997-104">Mechanizm dostawcy typu w języku F# jest istotną częścią jego obsługi programowania bogatego w informacje.</span><span class="sxs-lookup"><span data-stu-id="ed997-104">The type provider mechanism in F# is a significant part of its support for information rich programming.</span></span> <span data-ttu-id="ed997-105">W tym samouczku wyjaśniono, jak utworzyć własne dostawców typów, przechodząc przez rozwój kilku dostawców typów prostych, aby zilustrować podstawowe pojęcia.</span><span class="sxs-lookup"><span data-stu-id="ed997-105">This tutorial explains how to create your own type providers by walking you through the development of several simple type providers to illustrate the basic concepts.</span></span> <span data-ttu-id="ed997-106">Aby uzyskać więcej informacji na temat mechanizmu dostawcy typu w języku F#, zobacz [Typ providers](index.md).</span><span class="sxs-lookup"><span data-stu-id="ed997-106">For more information about the type provider mechanism in F#, see [Type Providers](index.md).</span></span>

<span data-ttu-id="ed997-107">Ekosystem F# zawiera szereg dostawców typów dla powszechnie używanych usług danych internetowych i korporacyjnych.</span><span class="sxs-lookup"><span data-stu-id="ed997-107">The F# ecosystem contains a range of type providers for commonly used Internet and enterprise data services.</span></span> <span data-ttu-id="ed997-108">Przykład:</span><span class="sxs-lookup"><span data-stu-id="ed997-108">For example:</span></span>

- <span data-ttu-id="ed997-109">[FSharp.Data](https://fsharp.github.io/FSharp.Data/) obejmuje dostawców typów dla formatów dokumentów JSON, XML, CSV i HTML.</span><span class="sxs-lookup"><span data-stu-id="ed997-109">[FSharp.Data](https://fsharp.github.io/FSharp.Data/) includes type providers for JSON, XML, CSV and HTML document formats.</span></span>

- <span data-ttu-id="ed997-110">[SQLProvider](https://fsprojects.github.io/SQLProvider/) zapewnia silnie typiwany dostęp do baz danych SQL za pośrednictwem mapowania obiektów i F# LINQ kwerendy dla tych źródeł danych.</span><span class="sxs-lookup"><span data-stu-id="ed997-110">[SQLProvider](https://fsprojects.github.io/SQLProvider/) provides strongly-typed access to SQL databases through a object mapping and F# LINQ queries against these data sources.</span></span>

- <span data-ttu-id="ed997-111">[FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) ma zestaw dostawców typów do skompilowania w czasie sprawdzane osadzanie T-SQL w języku F#.</span><span class="sxs-lookup"><span data-stu-id="ed997-111">[FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) has a set of type providers for compile-time checked embedding of T-SQL in F#.</span></span>

- <span data-ttu-id="ed997-112">[FSharp.Data.TypeProviders](https://fsprojects.github.io/FSharp.Data.TypeProviders/) jest starszym zestawem dostawców typów do użytku tylko z programowaniem .NET Framework w celu uzyskania dostępu do usług danych SQL, Entity Framework, OData i WSDL.</span><span class="sxs-lookup"><span data-stu-id="ed997-112">[FSharp.Data.TypeProviders](https://fsprojects.github.io/FSharp.Data.TypeProviders/) is an older set of type providers for use only with .NET Framework programming for accessing SQL, Entity Framework, OData and WSDL data services.</span></span>

<span data-ttu-id="ed997-113">W razie potrzeby można utworzyć dostawców typów niestandardowych lub odwoływać się do dostawców typów utworzonych przez inne osoby.</span><span class="sxs-lookup"><span data-stu-id="ed997-113">Where necessary, you can create custom type providers, or you can reference type providers that others have created.</span></span> <span data-ttu-id="ed997-114">Na przykład organizacja może mieć usługę danych, która zapewnia dużą i rosnącą liczbę nazwanych zestawów danych, z których każdy ma własny schemat danych stabilnych.</span><span class="sxs-lookup"><span data-stu-id="ed997-114">For example, your organization could have a data service that provides a large and growing number of named data sets, each with its own stable data schema.</span></span> <span data-ttu-id="ed997-115">Można utworzyć dostawcę typów, który odczytuje schematy i przedstawia bieżące zestawy danych programisty w sposób silnie typiwany.</span><span class="sxs-lookup"><span data-stu-id="ed997-115">You can create a type provider that reads the schemas and presents the current data sets to the programmer in a strongly typed way.</span></span>

## <a name="before-you-start"></a><span data-ttu-id="ed997-116">Przed rozpoczęciem</span><span class="sxs-lookup"><span data-stu-id="ed997-116">Before You Start</span></span>

<span data-ttu-id="ed997-117">Mechanizm dostawcy typu jest przeznaczony przede wszystkim do wstrzykiwania stabilnych przestrzeni informacji o danych i usługach do środowiska programowania Języka F#.</span><span class="sxs-lookup"><span data-stu-id="ed997-117">The type provider mechanism is primarily designed for injecting stable data and service information spaces into the F# programming experience.</span></span>

<span data-ttu-id="ed997-118">Ten mechanizm nie jest przeznaczony do wstrzykiwania przestrzeni informacyjnych, których schemat zmienia się podczas wykonywania programu w sposób, który jest odpowiedni dla logiki programu.</span><span class="sxs-lookup"><span data-stu-id="ed997-118">This mechanism isn’t designed for injecting information spaces whose schema changes during program execution in ways that are relevant to program logic.</span></span> <span data-ttu-id="ed997-119">Ponadto mechanizm nie jest przeznaczony do metaprogramowanie wewnątrz języka, mimo że ta domena zawiera kilka prawidłowych zastosowań.</span><span class="sxs-lookup"><span data-stu-id="ed997-119">Also, the mechanism isn't designed for intra-language meta-programming, even though that domain contains some valid uses.</span></span> <span data-ttu-id="ed997-120">Należy użyć tego mechanizmu tylko wtedy, gdy jest to konieczne i gdy rozwój dostawcy typu daje bardzo wysoką wartość.</span><span class="sxs-lookup"><span data-stu-id="ed997-120">You should use this mechanism only where necessary and where the development of a type provider yields very high value.</span></span>

<span data-ttu-id="ed997-121">Należy unikać pisania dostawcy typu, gdzie schemat nie jest dostępny.</span><span class="sxs-lookup"><span data-stu-id="ed997-121">You should avoid writing a type provider where a schema isn't available.</span></span> <span data-ttu-id="ed997-122">Podobnie należy unikać pisania dostawcy typu, gdzie wystarczy zwykła (lub nawet istniejąca) biblioteka .NET.</span><span class="sxs-lookup"><span data-stu-id="ed997-122">Likewise, you should avoid writing a type provider where an ordinary (or even an existing) .NET library would suffice.</span></span>

<span data-ttu-id="ed997-123">Przed rozpoczęciem można zadawać następujące pytania:</span><span class="sxs-lookup"><span data-stu-id="ed997-123">Before you start, you might ask the following questions:</span></span>

- <span data-ttu-id="ed997-124">Czy masz schemat dla źródła informacji?</span><span class="sxs-lookup"><span data-stu-id="ed997-124">Do you have a schema for your information source?</span></span> <span data-ttu-id="ed997-125">Jeśli tak, co to jest mapowanie do systemu typu F# i .NET?</span><span class="sxs-lookup"><span data-stu-id="ed997-125">If so, what’s the mapping into the F# and .NET type system?</span></span>

- <span data-ttu-id="ed997-126">Czy można użyć istniejącego (dynamicznie wpisywany) interfejsu API jako punktu wyjścia dla implementacji?</span><span class="sxs-lookup"><span data-stu-id="ed997-126">Can you use an existing (dynamically typed) API as a starting point for your implementation?</span></span>

- <span data-ttu-id="ed997-127">Czy ty i Twoja organizacja będziecie mieli wystarczająco dużo zastosowań dostawcy typu, aby pisanie było opłacalne?</span><span class="sxs-lookup"><span data-stu-id="ed997-127">Will you and your organization have enough uses of the type provider to make writing it worthwhile?</span></span> <span data-ttu-id="ed997-128">Czy normalna biblioteka .NET spełni Twoje potrzeby?</span><span class="sxs-lookup"><span data-stu-id="ed997-128">Would a normal .NET library meet your needs?</span></span>

- <span data-ttu-id="ed997-129">Jak bardzo zmieni się schemat?</span><span class="sxs-lookup"><span data-stu-id="ed997-129">How much will your schema change?</span></span>

- <span data-ttu-id="ed997-130">Czy zmieni się podczas kodowania?</span><span class="sxs-lookup"><span data-stu-id="ed997-130">Will it change during coding?</span></span>

- <span data-ttu-id="ed997-131">Czy zmieni się między sesjami kodowania?</span><span class="sxs-lookup"><span data-stu-id="ed997-131">Will it change between coding sessions?</span></span>

- <span data-ttu-id="ed997-132">Czy zmieni się podczas wykonywania programu?</span><span class="sxs-lookup"><span data-stu-id="ed997-132">Will it change during program execution?</span></span>

<span data-ttu-id="ed997-133">Dostawcy typów najlepiej nadają się do sytuacji, w których schemat jest stabilny w czasie wykonywania i w okresie istnienia skompilowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="ed997-133">Type providers are best suited to situations where the schema is stable at runtime and during the lifetime of compiled code.</span></span>

## <a name="a-simple-type-provider"></a><span data-ttu-id="ed997-134">Prosty dostawca typów</span><span class="sxs-lookup"><span data-stu-id="ed997-134">A Simple Type Provider</span></span>

<span data-ttu-id="ed997-135">Ten przykład jest Samples.HelloWorldTypeProvider, podobne do `examples` przykładów w katalogu [SDK dostawcy typu F#](https://github.com/fsprojects/FSharp.TypeProviders.SDK/).</span><span class="sxs-lookup"><span data-stu-id="ed997-135">This sample is Samples.HelloWorldTypeProvider, similar to the samples in the `examples` directory of the [F# Type Provider SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK/).</span></span> <span data-ttu-id="ed997-136">Dostawca udostępnia "przestrzeń typu", która zawiera 100 wymazanych typów, jak pokazano w poniższym kodzie przy użyciu składni podpisu F# i pomijając szczegóły dla wszystkich z wyjątkiem `Type1`.</span><span class="sxs-lookup"><span data-stu-id="ed997-136">The provider makes available a "type space" that contains 100 erased types, as the following code shows by using F# signature syntax and omitting the details for all except `Type1`.</span></span> <span data-ttu-id="ed997-137">Aby uzyskać więcej informacji na temat typów wymazanych, zobacz [Szczegółowe informacje o wymazanych podana typy](#details-about-erased-provided-types) w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="ed997-137">For more information about erased types, see [Details About Erased Provided Types](#details-about-erased-provided-types) later in this topic.</span></span>

```fsharp
namespace Samples.HelloWorldTypeProvider

type Type1 =
    /// This is a static property.
    static member StaticProperty : string

    /// This constructor takes no arguments.
    new : unit -> Type1

    /// This constructor takes one argument.
    new : data:string -> Type1

    /// This is an instance property.
    member InstanceProperty : int

    /// This is an instance method.
    member InstanceMethod : x:int -> char

    nested type NestedType =
        /// This is StaticProperty1 on NestedType.
        static member StaticProperty1 : string
        …
        /// This is StaticProperty100 on NestedType.
        static member StaticProperty100 : string

type Type2 =
…
…

type Type100 =
…
```

<span data-ttu-id="ed997-138">Należy zauważyć, że zestaw typów i elementów członkowskich pod warunkiem jest statycznie znane.</span><span class="sxs-lookup"><span data-stu-id="ed997-138">Note that the set of types and members provided is statically known.</span></span> <span data-ttu-id="ed997-139">W tym przykładzie nie wykorzystuje możliwości dostawców do zapewnienia typów, które zależą od schematu.</span><span class="sxs-lookup"><span data-stu-id="ed997-139">This example doesn't leverage the ability of providers to provide types that depend on a schema.</span></span> <span data-ttu-id="ed997-140">Implementacja dostawcy typu jest opisana w poniższym kodzie, a szczegóły są omówione w kolejnych sekcjach tego tematu.</span><span class="sxs-lookup"><span data-stu-id="ed997-140">The implementation of the type provider is outlined in the following code, and the details are covered in later sections of this topic.</span></span>

> [!WARNING]
> <span data-ttu-id="ed997-141">Mogą występować różnice między tym kodem a próbkami online.</span><span class="sxs-lookup"><span data-stu-id="ed997-141">There may be differences between this code and the online samples.</span></span>

```fsharp
namespace Samples.FSharp.HelloWorldTypeProvider

open System
open System.Reflection
open ProviderImplementation.ProvidedTypes
open FSharp.Core.CompilerServices
open FSharp.Quotations

// This type defines the type provider. When compiled to a DLL, it can be added
// as a reference to an F# command-line compilation, script, or project.
[<TypeProvider>]
type SampleTypeProvider(config: TypeProviderConfig) as this =

  // Inheriting from this type provides implementations of ITypeProvider
  // in terms of the provided types below.
  inherit TypeProviderForNamespaces(config)

  let namespaceName = "Samples.HelloWorldTypeProvider"
  let thisAssembly = Assembly.GetExecutingAssembly()

  // Make one provided type, called TypeN.
  let makeOneProvidedType (n:int) =
  …
  // Now generate 100 types
  let types = [ for i in 1 .. 100 -> makeOneProvidedType i ]

  // And add them to the namespace
  do this.AddNamespace(namespaceName, types)

[<assembly:TypeProviderAssembly>]
do()
```

<span data-ttu-id="ed997-142">Aby użyć tego dostawcy, otwórz oddzielne wystąpienie programu Visual Studio, utwórz skrypt Języka F#, a następnie dodaj odwołanie do dostawcy ze skryptu przy użyciu #r, jak pokazuje następujący kod:</span><span class="sxs-lookup"><span data-stu-id="ed997-142">To use this provider, open a separate instance of Visual Studio, create an F# script, and then add a reference to the provider from your script by using #r as the following code shows:</span></span>

```fsharp
#r @".\bin\Debug\Samples.HelloWorldTypeProvider.dll"

let obj1 = Samples.HelloWorldTypeProvider.Type1("some data")

let obj2 = Samples.HelloWorldTypeProvider.Type1("some other data")

obj1.InstanceProperty
obj2.InstanceProperty

[ for index in 0 .. obj1.InstanceProperty-1 -> obj1.InstanceMethod(index) ]
[ for index in 0 .. obj2.InstanceProperty-1 -> obj2.InstanceMethod(index) ]

let data1 = Samples.HelloWorldTypeProvider.Type1.NestedType.StaticProperty35
```

<span data-ttu-id="ed997-143">Następnie poszukaj `Samples.HelloWorldTypeProvider` typów w obszarze nazw, który wygenerował dostawca typu.</span><span class="sxs-lookup"><span data-stu-id="ed997-143">Then look for the types under the `Samples.HelloWorldTypeProvider` namespace that the type provider generated.</span></span>

<span data-ttu-id="ed997-144">Przed ponownym skompiluj dostawcę, upewnij się, że zostały zamknięte wszystkie wystąpienia programu Visual Studio i F# Interactive, które są przy użyciu biblioteki DLL dostawcy.</span><span class="sxs-lookup"><span data-stu-id="ed997-144">Before you recompile the provider, make sure that you have closed all instances of Visual Studio and F# Interactive that are using the provider DLL.</span></span> <span data-ttu-id="ed997-145">W przeciwnym razie wystąpi błąd kompilacji, ponieważ wyjściowa biblioteka DLL zostanie zablokowana.</span><span class="sxs-lookup"><span data-stu-id="ed997-145">Otherwise, a build error will occur because the output DLL will be locked.</span></span>

<span data-ttu-id="ed997-146">Aby debugować tego dostawcę przy użyciu instrukcji drukowania, należy wykonać skrypt, który udostępnia problem z dostawcą, a następnie użyć następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="ed997-146">To debug this provider by using print statements, make a script that exposes a problem with the provider, and then use the following code:</span></span>

```console
fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

<span data-ttu-id="ed997-147">Aby debugować tego dostawcę przy użyciu programu Visual Studio, otwórz wiersz polecenia dewelopera dla programu Visual Studio z poświadczeniami administracyjnymi i uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="ed997-147">To debug this provider by using Visual Studio, open the Developer Command Prompt for Visual Studio with administrative credentials, and run the following command:</span></span>

```console
devenv.exe /debugexe fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

<span data-ttu-id="ed997-148">Alternatywnie otwórz program Visual Studio, otwórz menu `Debug/Attach to process…`debugowania, `devenv` wybierz opcję i dołącz do innego procesu, w którym edytujesz skrypt.</span><span class="sxs-lookup"><span data-stu-id="ed997-148">As an alternative, open Visual Studio, open the Debug menu, choose `Debug/Attach to process…`, and attach to another `devenv` process where you’re editing your script.</span></span> <span data-ttu-id="ed997-149">Za pomocą tej metody, można łatwiej kierować określonej logiki w dostawcy typu przez interaktywne wpisywanie wyrażeń w drugim wystąpieniu (z pełnym IntelliSense i innych funkcji).</span><span class="sxs-lookup"><span data-stu-id="ed997-149">By using this method, you can more easily target particular logic in the type provider by interactively typing expressions into the second instance (with full IntelliSense and other features).</span></span>

<span data-ttu-id="ed997-150">Można wyłączyć debugowanie tylko mój kod, aby lepiej zidentyfikować błędy w wygenerowanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="ed997-150">You can disable Just My Code debugging to better identify errors in generated code.</span></span> <span data-ttu-id="ed997-151">Aby uzyskać informacje dotyczące włączania lub wyłączania tej funkcji, zobacz [Nawigowanie po kodzie za pomocą debugera](/visualstudio/debugger/navigating-through-code-with-the-debugger).</span><span class="sxs-lookup"><span data-stu-id="ed997-151">For information about how to enable or disable this feature, see [Navigating through Code with the Debugger](/visualstudio/debugger/navigating-through-code-with-the-debugger).</span></span> <span data-ttu-id="ed997-152">Można również ustawić przechwytywanie wyjątków pierwszej `Debug` szansy, `Exceptions` otwierając menu, a następnie wybierając lub wybierając `Exceptions` klawisze Ctrl+Alt+E, aby otworzyć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="ed997-152">Also, you can also set first-chance exception catching by opening the `Debug` menu and then choosing `Exceptions` or by choosing the Ctrl+Alt+E keys to open the `Exceptions` dialog box.</span></span> <span data-ttu-id="ed997-153">W tym oknie `Common Language Runtime Exceptions`dialogowym `Thrown` w obszarze zaznacz pole wyboru.</span><span class="sxs-lookup"><span data-stu-id="ed997-153">In that dialog box, under `Common Language Runtime Exceptions`, select the `Thrown` check box.</span></span>

### <a name="implementation-of-the-type-provider"></a><span data-ttu-id="ed997-154">Implementacja dostawcy typu</span><span class="sxs-lookup"><span data-stu-id="ed997-154">Implementation of the Type Provider</span></span>

<span data-ttu-id="ed997-155">W tej sekcji przeprowadzi Cię przez główne sekcje implementacji dostawcy typu.</span><span class="sxs-lookup"><span data-stu-id="ed997-155">This section walks you through the principal sections of the type provider implementation.</span></span> <span data-ttu-id="ed997-156">Najpierw należy zdefiniować typ dla samego dostawcy typu niestandardowego:</span><span class="sxs-lookup"><span data-stu-id="ed997-156">First, you define the type for the custom type provider itself:</span></span>

```fsharp
[<TypeProvider>]
type SampleTypeProvider(config: TypeProviderConfig) as this =
```

<span data-ttu-id="ed997-157">Ten typ musi być publiczny i należy oznaczyć go atrybutem [TypeProvider,](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947) aby kompilator rozpoznał dostawcę typu, gdy oddzielny projekt F# odwołuje się do zestawu zawierającego typ.</span><span class="sxs-lookup"><span data-stu-id="ed997-157">This type must be public, and you must mark it with the [TypeProvider](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947) attribute so that the compiler will recognize the type provider when a separate F# project references the assembly that contains the type.</span></span> <span data-ttu-id="ed997-158">Parametr *config* jest opcjonalny, a jeśli jest obecny, zawiera informacje o konfiguracji kontekstowej dla wystąpienia dostawcy typu tworzonego przez kompilator języka F#.</span><span class="sxs-lookup"><span data-stu-id="ed997-158">The *config* parameter is optional, and, if present, contains contextual configuration information for the type provider instance that the F# compiler creates.</span></span>

<span data-ttu-id="ed997-159">Następnie zaimplementujesz interfejs [ITypeProvider.](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f)</span><span class="sxs-lookup"><span data-stu-id="ed997-159">Next, you implement the [ITypeProvider](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f) interface.</span></span> <span data-ttu-id="ed997-160">W takim przypadku należy `TypeProviderForNamespaces` użyć `ProvidedTypes` typu z interfejsu API jako typu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="ed997-160">In this case, you use the `TypeProviderForNamespaces` type from the `ProvidedTypes` API as a base type.</span></span> <span data-ttu-id="ed997-161">Ten typ pomocnika może zapewnić skończoną kolekcję chętnie podanych obszarów nazw, z których każdy bezpośrednio zawiera skończoną liczbę stałych, chętnie dostarczonych typów.</span><span class="sxs-lookup"><span data-stu-id="ed997-161">This helper type can provide a finite collection of eagerly provided namespaces, each of which directly contains a finite number of fixed, eagerly provided types.</span></span> <span data-ttu-id="ed997-162">W tym kontekście dostawca *chętnie* generuje typy, nawet jeśli nie są one potrzebne lub używane.</span><span class="sxs-lookup"><span data-stu-id="ed997-162">In this context, the provider *eagerly* generates types even if they aren't needed or used.</span></span>

```fsharp
inherit TypeProviderForNamespaces(config)
```

<span data-ttu-id="ed997-163">Następnie zdefiniuj lokalne wartości prywatne, które określają obszar nazw dla podanych typów, i znajdź sam zestaw dostawcy typu.</span><span class="sxs-lookup"><span data-stu-id="ed997-163">Next, define local private values that specify the namespace for the provided types, and find the type provider assembly itself.</span></span> <span data-ttu-id="ed997-164">Ten zestaw jest później używany jako logiczny typ nadrzędny wymazanych typów, które są dostarczane.</span><span class="sxs-lookup"><span data-stu-id="ed997-164">This assembly is used later as the logical parent type of the erased types that are provided.</span></span>

```fsharp
let namespaceName = "Samples.HelloWorldTypeProvider"
let thisAssembly = Assembly.GetExecutingAssembly()
```

<span data-ttu-id="ed997-165">Następnie utwórz funkcję, aby zapewnić każdy z typów Type1... Typ100.</span><span class="sxs-lookup"><span data-stu-id="ed997-165">Next, create a function to provide each of the types Type1…Type100.</span></span> <span data-ttu-id="ed997-166">Ta funkcja jest wyjaśniona bardziej szczegółowo w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="ed997-166">This function is explained in more detail later in this topic.</span></span>

```fsharp
let makeOneProvidedType (n:int) = …
```

<span data-ttu-id="ed997-167">Następnie wygeneruj 100 dostarczonych typów:</span><span class="sxs-lookup"><span data-stu-id="ed997-167">Next, generate the 100 provided types:</span></span>

```fsharp
let types = [ for i in 1 .. 100 -> makeOneProvidedType i ]
```

<span data-ttu-id="ed997-168">Następnie dodaj typy jako dostarczoną przestrzeń nazw:</span><span class="sxs-lookup"><span data-stu-id="ed997-168">Next, add the types as a provided namespace:</span></span>

```fsharp
do this.AddNamespace(namespaceName, types)
```

<span data-ttu-id="ed997-169">Na koniec dodaj atrybut zestawu, który wskazuje, że tworzysz bibliotekę DLL dostawcy typów:</span><span class="sxs-lookup"><span data-stu-id="ed997-169">Finally, add an assembly attribute that indicates that you are creating a type provider DLL:</span></span>

```fsharp
[<assembly:TypeProviderAssembly>]
do()
```

### <a name="providing-one-type-and-its-members"></a><span data-ttu-id="ed997-170">Zapewnienie jednego typu i jego członków</span><span class="sxs-lookup"><span data-stu-id="ed997-170">Providing One Type And Its Members</span></span>

<span data-ttu-id="ed997-171">Funkcja `makeOneProvidedType` wykonuje rzeczywistą pracę dostarczania jednego z typów.</span><span class="sxs-lookup"><span data-stu-id="ed997-171">The `makeOneProvidedType` function does the real work of providing one of the types.</span></span>

```fsharp
let makeOneProvidedType (n:int) =
…
```

<span data-ttu-id="ed997-172">Ten krok wyjaśnia implementację tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="ed997-172">This step explains the implementation of this function.</span></span> <span data-ttu-id="ed997-173">Najpierw należy utworzyć podany typ (na przykład Typ1, gdy n = 1 lub Type57, gdy n = 57).</span><span class="sxs-lookup"><span data-stu-id="ed997-173">First, create the provided type (for example, Type1, when n = 1, or Type57, when n = 57).</span></span>

```fsharp
// This is the provided type. It is an erased provided type and, in compiled code,
// will appear as type 'obj'.
let t = ProvidedTypeDefinition(thisAssembly, namespaceName,
                               "Type" + string n,
                               baseType = Some typeof<obj>)
```

<span data-ttu-id="ed997-174">Należy zwrócić uwagę na następujące punkty:</span><span class="sxs-lookup"><span data-stu-id="ed997-174">You should note the following points:</span></span>

- <span data-ttu-id="ed997-175">Ten podany typ jest usuwany.</span><span class="sxs-lookup"><span data-stu-id="ed997-175">This provided type is erased.</span></span>  <span data-ttu-id="ed997-176">Ponieważ wskazujesz, że `obj`typem podstawowym jest , wystąpienia będą wyświetlane jako wartości typu [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) w skompilowanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="ed997-176">Because you indicate that the base type is `obj`, instances will appear as values of type [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) in compiled code.</span></span>

- <span data-ttu-id="ed997-177">Po określeniu typu niezagnieżdżonego należy określić zestaw i obszar nazw.</span><span class="sxs-lookup"><span data-stu-id="ed997-177">When you specify a non-nested type, you must specify the assembly and namespace.</span></span> <span data-ttu-id="ed997-178">W przypadku typów wymazanych zestaw powinien być samym zestawem dostawcy typu.</span><span class="sxs-lookup"><span data-stu-id="ed997-178">For erased types, the assembly should be the type provider assembly itself.</span></span>

<span data-ttu-id="ed997-179">Następnie dodaj dokumentację XML do typu.</span><span class="sxs-lookup"><span data-stu-id="ed997-179">Next, add XML documentation to the type.</span></span> <span data-ttu-id="ed997-180">Ta dokumentacja jest opóźniona, czyli obliczana na żądanie, jeśli kompilator hosta jej potrzebuje.</span><span class="sxs-lookup"><span data-stu-id="ed997-180">This documentation is delayed, that is, computed on-demand if the host compiler needs it.</span></span>

```fsharp
t.AddXmlDocDelayed (fun () -> sprintf "This provided type %s" ("Type" + string n))
```

<span data-ttu-id="ed997-181">Następnie należy dodać podana właściwość statyczną do typu:</span><span class="sxs-lookup"><span data-stu-id="ed997-181">Next you add a provided static property to the type:</span></span>

```fsharp
let staticProp = ProvidedProperty(propertyName = "StaticProperty",
                                  propertyType = typeof<string>,
                                  isStatic = true,
                                  getterCode = (fun args -> <@@ "Hello!" @@>))
```

<span data-ttu-id="ed997-182">Pierwsze tej właściwości zawsze oceni ciąg "Hello!".</span><span class="sxs-lookup"><span data-stu-id="ed997-182">Getting this property will always evaluate to the string "Hello!".</span></span> <span data-ttu-id="ed997-183">Dla `GetterCode` właściwości używa oferty F#, która reprezentuje kod, który kompilator hosta generuje do uzyskania właściwości.</span><span class="sxs-lookup"><span data-stu-id="ed997-183">The `GetterCode` for the property uses an F# quotation, which represents the code that the host compiler generates for getting the property.</span></span> <span data-ttu-id="ed997-184">Aby uzyskać więcej informacji na temat ofert, zobacz [Oferty kodowe (F#)](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155).</span><span class="sxs-lookup"><span data-stu-id="ed997-184">For more information about quotations, see [Code Quotations (F#)](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155).</span></span>

<span data-ttu-id="ed997-185">Dodaj dokumentację XML do właściwości.</span><span class="sxs-lookup"><span data-stu-id="ed997-185">Add XML documentation to the property.</span></span>

```fsharp
staticProp.AddXmlDocDelayed(fun () -> "This is a static property")
```

<span data-ttu-id="ed997-186">Teraz dołącz dostarczoną właściwość do podanego typu.</span><span class="sxs-lookup"><span data-stu-id="ed997-186">Now attach the provided property to the provided type.</span></span> <span data-ttu-id="ed997-187">Należy dołączyć dostarczony element członkowski do jednego i tylko jednego typu.</span><span class="sxs-lookup"><span data-stu-id="ed997-187">You must attach a provided member to one and only one type.</span></span> <span data-ttu-id="ed997-188">W przeciwnym razie element członkowski nigdy nie będzie dostępny.</span><span class="sxs-lookup"><span data-stu-id="ed997-188">Otherwise, the member will never be accessible.</span></span>

```fsharp
t.AddMember staticProp
```

<span data-ttu-id="ed997-189">Teraz utwórz dostarczony konstruktor, który nie przyjmuje żadnych parametrów.</span><span class="sxs-lookup"><span data-stu-id="ed997-189">Now create a provided constructor that takes no parameters.</span></span>

```fsharp
let ctor = ProvidedConstructor(parameters = [ ],
                               invokeCode = (fun args -> <@@ "The object data" :> obj @@>))
```

<span data-ttu-id="ed997-190">Dla `InvokeCode` konstruktora zwraca ofertę F#, która reprezentuje kod, który generuje kompilator hosta, gdy konstruktor jest wywoływany.</span><span class="sxs-lookup"><span data-stu-id="ed997-190">The `InvokeCode` for the constructor returns an F# quotation, which represents the code that the host compiler generates when the constructor is called.</span></span> <span data-ttu-id="ed997-191">Na przykład można użyć następującego konstruktora:</span><span class="sxs-lookup"><span data-stu-id="ed997-191">For example, you can use the following constructor:</span></span>

```fsharp
new Type10()
```

<span data-ttu-id="ed997-192">Wystąpienie podanego typu zostanie utworzone z danymi źródłowymi "Dane obiektu".</span><span class="sxs-lookup"><span data-stu-id="ed997-192">An instance of the provided type will be created with underlying data "The object data".</span></span> <span data-ttu-id="ed997-193">Cytowany kod zawiera konwersję do [obj,](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) ponieważ ten typ jest wymazaniem tego typu pod warunkiem (jak określono podczas deklarowania podanego typu).</span><span class="sxs-lookup"><span data-stu-id="ed997-193">The quoted code includes a conversion to [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) because that type is the erasure of this provided type (as you specified when you declared the provided type).</span></span>

<span data-ttu-id="ed997-194">Dodaj dokumentację XML do konstruktora i dodaj dostarczony konstruktor do podanego typu:</span><span class="sxs-lookup"><span data-stu-id="ed997-194">Add XML documentation to the constructor, and add the provided constructor to the provided type:</span></span>

```fsharp
ctor.AddXmlDocDelayed(fun () -> "This is a constructor")

t.AddMember ctor
```

<span data-ttu-id="ed997-195">Utwórz drugi dostarczony konstruktor, który przyjmuje jeden parametr:</span><span class="sxs-lookup"><span data-stu-id="ed997-195">Create a second provided constructor that takes one parameter:</span></span>

```fsharp
let ctor2 =
ProvidedConstructor(parameters = [ ProvidedParameter("data",typeof<string>) ],
                    invokeCode = (fun args -> <@@ (%%(args.[0]) : string) :> obj @@>))
```

<span data-ttu-id="ed997-196">Dla `InvokeCode` konstruktora ponownie zwraca ofertę Języka F#, która reprezentuje kod, który kompilator hosta generowane dla wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="ed997-196">The `InvokeCode` for the constructor again returns an F# quotation, which represents the code that the host compiler generated for a call to the method.</span></span> <span data-ttu-id="ed997-197">Na przykład można użyć następującego konstruktora:</span><span class="sxs-lookup"><span data-stu-id="ed997-197">For example, you can use the following constructor:</span></span>

```fsharp
new Type10("ten")
```

<span data-ttu-id="ed997-198">Wystąpienie podanego typu jest tworzony z podstawowych danych "dziesięć".</span><span class="sxs-lookup"><span data-stu-id="ed997-198">An instance of the provided type is created with underlying data "ten".</span></span> <span data-ttu-id="ed997-199">Być może zauważyłeś już, że `InvokeCode` funkcja zwraca ofertę.</span><span class="sxs-lookup"><span data-stu-id="ed997-199">You may have already noticed that the `InvokeCode` function returns a quotation.</span></span> <span data-ttu-id="ed997-200">Dane wejściowe do tej funkcji to lista wyrażeń, jeden na parametr konstruktora.</span><span class="sxs-lookup"><span data-stu-id="ed997-200">The input to this function is a list of expressions, one per constructor parameter.</span></span> <span data-ttu-id="ed997-201">W takim przypadku wyrażenie reprezentujące wartość pojedynczego `args.[0]`parametru jest dostępne w pliku .</span><span class="sxs-lookup"><span data-stu-id="ed997-201">In this case, an expression that represents the single parameter value is available in `args.[0]`.</span></span> <span data-ttu-id="ed997-202">Kod wywołania konstruktora powoduje wymuszanie wartości zwracanej do typu `obj`wymazanego.</span><span class="sxs-lookup"><span data-stu-id="ed997-202">The code for a call to the constructor coerces the return value to the erased type `obj`.</span></span> <span data-ttu-id="ed997-203">Po dodaniu drugiego dostarczonego konstruktora do typu należy utworzyć dostarczoną właściwość wystąpienia:</span><span class="sxs-lookup"><span data-stu-id="ed997-203">After you add the second provided constructor to the type, you create a provided instance property:</span></span>

```fsharp
let instanceProp =
    ProvidedProperty(propertyName = "InstanceProperty",
                     propertyType = typeof<int>,
                     getterCode= (fun args ->
                        <@@ ((%%(args.[0]) : obj) :?> string).Length @@>))
instanceProp.AddXmlDocDelayed(fun () -> "This is an instance property")
t.AddMember instanceProp
```

<span data-ttu-id="ed997-204">Pierwsze tej właściwości zwróci długość ciągu, który jest obiektem reprezentacji.</span><span class="sxs-lookup"><span data-stu-id="ed997-204">Getting this property will return the length of the string, which is the representation object.</span></span> <span data-ttu-id="ed997-205">Właściwość `GetterCode` zwraca ofertę Języka F#, która określa kod, który kompilator hosta generuje, aby uzyskać właściwość.</span><span class="sxs-lookup"><span data-stu-id="ed997-205">The `GetterCode` property returns an F# quotation that specifies the code that the host compiler generates to get the property.</span></span> <span data-ttu-id="ed997-206">Like `InvokeCode`, `GetterCode` funkcja zwraca ofertę.</span><span class="sxs-lookup"><span data-stu-id="ed997-206">Like `InvokeCode`, the `GetterCode` function returns a quotation.</span></span> <span data-ttu-id="ed997-207">Kompilator hosta wywołuje tę funkcję z listą argumentów.</span><span class="sxs-lookup"><span data-stu-id="ed997-207">The host compiler calls this function with a list of arguments.</span></span> <span data-ttu-id="ed997-208">W takim przypadku argumenty obejmują tylko pojedyncze wyrażenie, które reprezentuje wystąpienie, na którym `args.[0]`wywoływane jest wywoływane wywoływane wywoływane przez getter, do którego można uzyskać dostęp za pomocą programu .</span><span class="sxs-lookup"><span data-stu-id="ed997-208">In this case, the arguments include just the single expression that represents the instance upon which the getter is being called, which you can access by using `args.[0]`.</span></span> <span data-ttu-id="ed997-209">Implementacja `GetterCode` następnie splices do cytatu wynik na `obj`typ wymazane , a rzutowanie jest używany do spełnienia mechanizm kompilatora do sprawdzania typów, że obiekt jest ciągiem.</span><span class="sxs-lookup"><span data-stu-id="ed997-209">The implementation of `GetterCode` then splices into the result quotation at the erased type `obj`, and a cast is used to satisfy the compiler's mechanism for checking types that the object is a string.</span></span> <span data-ttu-id="ed997-210">Następna część `makeOneProvidedType` zawiera metodę wystąpienia z jednym parametrem.</span><span class="sxs-lookup"><span data-stu-id="ed997-210">The next part of `makeOneProvidedType` provides an instance method with one parameter.</span></span>

```fsharp
let instanceMeth =
    ProvidedMethod(methodName = "InstanceMethod",
                   parameters = [ProvidedParameter("x",typeof<int>)],
                   returnType = typeof<char>,
                   invokeCode = (fun args ->
                       <@@ ((%%(args.[0]) : obj) :?> string).Chars(%%(args.[1]) : int) @@>))

instanceMeth.AddXmlDocDelayed(fun () -> "This is an instance method")
// Add the instance method to the type.
t.AddMember instanceMeth
```

<span data-ttu-id="ed997-211">Na koniec utwórz typ zagnieżdżony, który zawiera 100 właściwości zagnieżdżonych.</span><span class="sxs-lookup"><span data-stu-id="ed997-211">Finally, create a nested type that contains 100 nested properties.</span></span> <span data-ttu-id="ed997-212">Tworzenie tego typu zagnieżdżonego i jego właściwości jest opóźnione, czyli obliczane na żądanie.</span><span class="sxs-lookup"><span data-stu-id="ed997-212">The creation of this nested type and its properties is delayed, that is, computed on-demand.</span></span>

```fsharp
t.AddMembersDelayed(fun () ->
  let nestedType = ProvidedTypeDefinition("NestedType", Some typeof<obj>)

  nestedType.AddMembersDelayed (fun () ->
    let staticPropsInNestedType =
      [
          for i in 1 .. 100 ->
              let valueOfTheProperty = "I am string "  + string i

              let p =
                ProvidedProperty(propertyName = "StaticProperty" + string i,
                  propertyType = typeof<string>,
                  isStatic = true,
                  getterCode= (fun args -> <@@ valueOfTheProperty @@>))

              p.AddXmlDocDelayed(fun () ->
                  sprintf "This is StaticProperty%d on NestedType" i)

              p
      ]

    staticPropsInNestedType)

  [nestedType])
```

### <a name="details-about-erased-provided-types"></a><span data-ttu-id="ed997-213">Szczegółowe informacje o wymazanych typach dostarczonych</span><span class="sxs-lookup"><span data-stu-id="ed997-213">Details about Erased Provided Types</span></span>

<span data-ttu-id="ed997-214">Przykład w tej sekcji zawiera tylko *wymazane podane typy,* które są szczególnie przydatne w następujących sytuacjach:</span><span class="sxs-lookup"><span data-stu-id="ed997-214">The example in this section provides only *erased provided types*, which are particularly useful in the following situations:</span></span>

- <span data-ttu-id="ed997-215">Podczas pisania dostawcy dla przestrzeni informacyjnej, która zawiera tylko dane i metody.</span><span class="sxs-lookup"><span data-stu-id="ed997-215">When you are writing a provider for an information space that contains only data and methods.</span></span>

- <span data-ttu-id="ed997-216">Podczas pisania dostawcy, gdzie dokładne semantyka typu środowiska uruchomieniowego nie są krytyczne dla praktycznego wykorzystania przestrzeni informacyjnej.</span><span class="sxs-lookup"><span data-stu-id="ed997-216">When you are writing a provider where accurate runtime-type semantics aren't critical for practical use of the information space.</span></span>

- <span data-ttu-id="ed997-217">Podczas pisania dostawcy dla przestrzeni informacyjnej, która jest tak duża i wzajemnie połączona, że nie jest technicznie wykonalne do generowania rzeczywistych typów .NET dla przestrzeni informacyjnej.</span><span class="sxs-lookup"><span data-stu-id="ed997-217">When you are writing a provider for an information space that is so large and interconnected that it isn’t technically feasible to generate real .NET types for the information space.</span></span>

<span data-ttu-id="ed997-218">W tym przykładzie każdy podany typ `obj`jest kasowany, aby wpisać `obj` , a wszystkie zastosowania tego typu będą wyświetlane jako typ w skompilowanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="ed997-218">In this example, each provided type is erased to type `obj`, and all uses of the type will appear as type `obj` in compiled code.</span></span> <span data-ttu-id="ed997-219">W rzeczywistości podstawowe obiekty w tych przykładach są ciągi, `System.Object` ale typ pojawi się jak w .NET skompilowany kod.</span><span class="sxs-lookup"><span data-stu-id="ed997-219">In fact, the underlying objects in these examples are strings, but the type will appear as `System.Object` in .NET compiled code.</span></span> <span data-ttu-id="ed997-220">Podobnie jak w przypadku wszystkich zastosowań usuwania typu, można użyć jawnego boksu, rozpakowywania i rzucania w celu obalenia wymazanych typów.</span><span class="sxs-lookup"><span data-stu-id="ed997-220">As with all uses of type erasure, you can use explicit boxing, unboxing, and casting to subvert erased types.</span></span> <span data-ttu-id="ed997-221">W takim przypadku wyjątek rzutu, który nie jest prawidłowy może spowodować, gdy obiekt jest używany.</span><span class="sxs-lookup"><span data-stu-id="ed997-221">In this case, a cast exception that isn’t valid may result when the object is used.</span></span> <span data-ttu-id="ed997-222">Środowisko uruchomieniowe dostawcy można zdefiniować swój własny typ reprezentacji prywatnej, aby chronić przed fałszywymi oświadczeniami.</span><span class="sxs-lookup"><span data-stu-id="ed997-222">A provider runtime can define its own private representation type to help protect against false representations.</span></span> <span data-ttu-id="ed997-223">Nie można zdefiniować wymazane typy w języku F# się.</span><span class="sxs-lookup"><span data-stu-id="ed997-223">You can’t define erased types in F# itself.</span></span> <span data-ttu-id="ed997-224">Tylko podane typy mogą zostać wymazane.</span><span class="sxs-lookup"><span data-stu-id="ed997-224">Only provided types may be erased.</span></span> <span data-ttu-id="ed997-225">Należy zrozumieć konsekwencje, zarówno praktyczne i semantyczne, przy użyciu albo wymazane typy dla dostawcy typu lub dostawcy, który udostępnia usunięte typy.</span><span class="sxs-lookup"><span data-stu-id="ed997-225">You must understand the ramifications, both practical and semantic, of using either erased types for your type provider or a provider that provides erased types.</span></span> <span data-ttu-id="ed997-226">Typ wymazany nie ma prawdziwego typu .NET.</span><span class="sxs-lookup"><span data-stu-id="ed997-226">An erased type has no real .NET type.</span></span> <span data-ttu-id="ed997-227">W związku z tym nie można wykonać dokładne odbicie nad typem i może obalić wymazane typy, jeśli używasz rzutowania środowiska uruchomieniowego i innych technik, które opierają się na semantyki typu dokładnego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="ed997-227">Therefore, you cannot do accurate reflection over the type, and you might subvert erased types if you use runtime casts and other techniques that rely on exact runtime type semantics.</span></span> <span data-ttu-id="ed997-228">Subversion usuniętych typów często powoduje typu rzutowania wyjątków w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="ed997-228">Subversion of erased types frequently results in type cast exceptions at runtime.</span></span>

### <a name="choosing-representations-for-erased-provided-types"></a><span data-ttu-id="ed997-229">Wybieranie reprezentacji dla wymazanych typów</span><span class="sxs-lookup"><span data-stu-id="ed997-229">Choosing Representations for Erased Provided Types</span></span>

<span data-ttu-id="ed997-230">W przypadku niektórych zastosowań wymazanych typów dostarczonych nie jest wymagana reprezentacja.</span><span class="sxs-lookup"><span data-stu-id="ed997-230">For some uses of erased provided types, no representation is required.</span></span> <span data-ttu-id="ed997-231">Na przykład wymazany pod warunkiem typu może zawierać tylko właściwości statyczne i elementy członkowskie i nie konstruktorów i żadnych metod lub właściwości zwróci wystąpienie typu.</span><span class="sxs-lookup"><span data-stu-id="ed997-231">For example, the erased provided type might contain only static properties and members and no constructors, and no methods or properties would return an instance of the type.</span></span> <span data-ttu-id="ed997-232">Jeśli można dotrzeć do wystąpień wymazanego typu dostarczonego, należy wziąć pod uwagę następujące pytania:</span><span class="sxs-lookup"><span data-stu-id="ed997-232">If you can reach instances of an erased provided type, you must consider the following questions:</span></span>

<span data-ttu-id="ed997-233">**Co to jest usuwanie podanego typu?**</span><span class="sxs-lookup"><span data-stu-id="ed997-233">**What is the erasure of a provided type?**</span></span>

- <span data-ttu-id="ed997-234">Usunięcie podanego typu jest sposób, w jaki typ pojawia się w skompilowanym kodzie .NET.</span><span class="sxs-lookup"><span data-stu-id="ed997-234">The erasure of a provided type is how the type appears in compiled .NET code.</span></span>

- <span data-ttu-id="ed997-235">Usunięcie podanego typu klasy wymazanej jest zawsze pierwszym nieskażonym typem podstawowym w łańcuchu dziedziczenia typu.</span><span class="sxs-lookup"><span data-stu-id="ed997-235">The erasure of a provided erased class type is always the first non-erased base type in the inheritance chain of the type.</span></span>

- <span data-ttu-id="ed997-236">Usunięcie podanego typu usuniętego interfejsu jest `System.Object`zawsze .</span><span class="sxs-lookup"><span data-stu-id="ed997-236">The erasure of a provided erased interface type is always `System.Object`.</span></span>

<span data-ttu-id="ed997-237">**Jakie są reprezentacje podanego typu?**</span><span class="sxs-lookup"><span data-stu-id="ed997-237">**What are the representations of a provided type?**</span></span>

- <span data-ttu-id="ed997-238">Zestaw możliwych obiektów dla wymazanego typu są nazywane jego reprezentacje.</span><span class="sxs-lookup"><span data-stu-id="ed997-238">The set of possible objects for an erased provided type are called its representations.</span></span> <span data-ttu-id="ed997-239">W przykładzie w tym dokumencie reprezentacje wszystkich wymazanych typów `Type1..Type100` dostarczonych są zawsze obiektami ciągów.</span><span class="sxs-lookup"><span data-stu-id="ed997-239">In the example in this document, the representations of all the erased provided types `Type1..Type100` are always string objects.</span></span>

<span data-ttu-id="ed997-240">Wszystkie reprezentacje dostarczonego typu muszą być zgodne z usunięciem podanego typu.</span><span class="sxs-lookup"><span data-stu-id="ed997-240">All representations of a provided type must be compatible with the erasure of the provided type.</span></span> <span data-ttu-id="ed997-241">(W przeciwnym razie kompilator Języka F# poda błąd podczas korzystania z dostawcy typu lub zostanie wygenerowany nieweryfikowalny kod .NET, który nie jest prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="ed997-241">(Otherwise, either the F# compiler will give an error for a use of the type provider, or unverifiable .NET code that isn't valid will be generated.</span></span> <span data-ttu-id="ed997-242">Dostawca typu nie jest prawidłowy, jeśli zwraca kod, który daje reprezentację, która nie jest prawidłowa.)</span><span class="sxs-lookup"><span data-stu-id="ed997-242">A type provider isn’t valid if it returns code that gives a  representation that isn't valid.)</span></span>

<span data-ttu-id="ed997-243">Można wybrać reprezentację dla podanych obiektów przy użyciu jednego z następujących podejść, z których oba są bardzo powszechne:</span><span class="sxs-lookup"><span data-stu-id="ed997-243">You can choose a representation for provided objects by using either of the following approaches, both of which are very common:</span></span>

- <span data-ttu-id="ed997-244">Jeśli po prostu udostępniasz silnie wpisane otoki nad istniejącym typem .NET, często ma sens, aby typ został wymazany do tego typu, użyj wystąpień tego typu jako reprezentacji lub obu.</span><span class="sxs-lookup"><span data-stu-id="ed997-244">If you're simply providing a strongly typed wrapper over an existing .NET type, it often makes sense for your type to erase to that type, use instances of that type as representations, or both.</span></span> <span data-ttu-id="ed997-245">Takie podejście jest właściwe, gdy większość istniejących metod na tego typu nadal mają sens podczas korzystania z wersji silnie typizowane.</span><span class="sxs-lookup"><span data-stu-id="ed997-245">This approach is appropriate when most of the existing methods on that type still make sense when using the strongly typed version.</span></span>

- <span data-ttu-id="ed997-246">Jeśli chcesz utworzyć interfejs API, który znacznie różni się od istniejącego interfejsu API platformy .NET, warto utworzyć typy środowiska uruchomieniowego, które będą wymazywaniem typu i reprezentacjami dla podanych typów.</span><span class="sxs-lookup"><span data-stu-id="ed997-246">If you want to create an API that differs significantly from any existing .NET API, it makes sense to create runtime types that will be the type erasure and representations for the provided types.</span></span>

<span data-ttu-id="ed997-247">W tym dokumencie użyto ciągów jako reprezentacji podanych obiektów.</span><span class="sxs-lookup"><span data-stu-id="ed997-247">The example in this document uses strings as representations of provided objects.</span></span> <span data-ttu-id="ed997-248">Często może być właściwe użycie innych obiektów do reprezentacji.</span><span class="sxs-lookup"><span data-stu-id="ed997-248">Frequently, it may be appropriate to use other objects for representations.</span></span> <span data-ttu-id="ed997-249">Na przykład można użyć słownika jako worka właściwości:</span><span class="sxs-lookup"><span data-stu-id="ed997-249">For example, you may use a dictionary as a property bag:</span></span>

```fsharp
ProvidedConstructor(parameters = [],
    invokeCode= (fun args -> <@@ (new Dictionary<string,obj>()) :> obj @@>))
```

<span data-ttu-id="ed997-250">Alternatywnie można zdefiniować typ w dostawcy typu, który będzie używany w czasie wykonywania do tworzenia reprezentacji, wraz z jedną lub kilkoma operacjami środowiska uruchomieniowego:</span><span class="sxs-lookup"><span data-stu-id="ed997-250">As an alternative, you may define a type in your type provider that will be used at runtime to form the representation, along with one or more runtime operations:</span></span>

```fsharp
type DataObject() =
    let data = Dictionary<string,obj>()
    member x.RuntimeOperation() = data.Count
```

<span data-ttu-id="ed997-251">Pod warunkiem, że członkowie mogą następnie konstruować wystąpienia tego typu obiektu:</span><span class="sxs-lookup"><span data-stu-id="ed997-251">Provided members can then construct instances of this object type:</span></span>

```fsharp
ProvidedConstructor(parameters = [],
    invokeCode= (fun args -> <@@ (new DataObject()) :> obj @@>))
```

<span data-ttu-id="ed997-252">W takim przypadku można (opcjonalnie) użyć tego typu jako usunięcia typu, `baseType` określając ten `ProvidedTypeDefinition`typ jako podczas konstruowania:</span><span class="sxs-lookup"><span data-stu-id="ed997-252">In this case, you may (optionally) use this type as the type erasure by specifying this type as the `baseType` when constructing the `ProvidedTypeDefinition`:</span></span>

```fsharp
ProvidedTypeDefinition(…, baseType = Some typeof<DataObject> )
…
ProvidedConstructor(…, InvokeCode = (fun args -> <@@ new DataObject() @@>), …)
```

### <a name="key-lessons"></a><span data-ttu-id="ed997-253">Kluczowe lekcje</span><span class="sxs-lookup"><span data-stu-id="ed997-253">Key Lessons</span></span>

<span data-ttu-id="ed997-254">W poprzedniej sekcji wyjaśniono, jak utworzyć prosty dostawca typów wymazywania, który udostępnia szereg typów, właściwości i metod.</span><span class="sxs-lookup"><span data-stu-id="ed997-254">The previous section explained how to create a simple erasing type provider that provides a range of types, properties, and methods.</span></span> <span data-ttu-id="ed997-255">W tej sekcji wyjaśniono również pojęcie usuwania typu, w tym niektóre zalety i wady dostarczania wymazanych typów od dostawcy typu i omówione reprezentacje usuniętych typów.</span><span class="sxs-lookup"><span data-stu-id="ed997-255">This section also explained the concept of type erasure, including some of the advantages and disadvantages of providing erased types from a type provider, and discussed representations of erased types.</span></span>

## <a name="a-type-provider-that-uses-static-parameters"></a><span data-ttu-id="ed997-256">Dostawca typów, który używa parametrów statycznych</span><span class="sxs-lookup"><span data-stu-id="ed997-256">A Type Provider That Uses Static Parameters</span></span>

<span data-ttu-id="ed997-257">Możliwość parametryzacji dostawców typów przez dane statyczne umożliwia wiele interesujących scenariuszy, nawet w przypadkach, gdy dostawca nie musi uzyskiwać dostępu do żadnych danych lokalnych lub zdalnych.</span><span class="sxs-lookup"><span data-stu-id="ed997-257">The ability to parameterize type providers by static data enables many interesting scenarios, even in cases when the provider doesn't need to access any local or remote data.</span></span> <span data-ttu-id="ed997-258">W tej sekcji dowiesz się kilka podstawowych technik łączenia takiego dostawcy.</span><span class="sxs-lookup"><span data-stu-id="ed997-258">In this section, you’ll learn some basic techniques for putting together such a provider.</span></span>

### <a name="type-checked-regex-provider"></a><span data-ttu-id="ed997-259">Typ sprawdzonego dostawcy programu Regex</span><span class="sxs-lookup"><span data-stu-id="ed997-259">Type Checked Regex Provider</span></span>

<span data-ttu-id="ed997-260">Wyobraź sobie, że chcesz zaimplementować dostawcę typów <xref:System.Text.RegularExpressions.Regex> dla wyrażeń regularnych, który otacza biblioteki .NET w interfejsie, który zapewnia następujące gwarancje czasu kompilacji:</span><span class="sxs-lookup"><span data-stu-id="ed997-260">Imagine that you want to implement a type provider for regular expressions that wraps the .NET <xref:System.Text.RegularExpressions.Regex> libraries in an interface that provides the following compile-time guarantees:</span></span>

- <span data-ttu-id="ed997-261">Sprawdzanie, czy wyrażenie regularne jest prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="ed997-261">Verifying whether a regular expression is valid.</span></span>

- <span data-ttu-id="ed997-262">Dostarczanie nazwanych właściwości na dopasowania, które są oparte na nazwach grup w wyrażeniu regularnym.</span><span class="sxs-lookup"><span data-stu-id="ed997-262">Providing named properties on matches that are based on any group names in the regular expression.</span></span>

<span data-ttu-id="ed997-263">W tej sekcji pokazano, jak używać `RegexTyped` dostawców typów do tworzenia typu, który wzorzec wyrażenia regularnego parametryzuje, aby zapewnić te korzyści.</span><span class="sxs-lookup"><span data-stu-id="ed997-263">This section shows you how to use type providers to create a `RegexTyped` type that the regular expression pattern parameterizes to provide these benefits.</span></span> <span data-ttu-id="ed997-264">Kompilator zgłosi błąd, jeśli dostarczony wzorzec nie jest prawidłowy, a dostawca typów może wyodrębnić grupy ze wzorca, dzięki czemu można uzyskać do nich dostęp przy użyciu nazwanych właściwości w dopasowaniach.</span><span class="sxs-lookup"><span data-stu-id="ed997-264">The compiler will report an error if the supplied pattern isn't valid, and the type provider can extract the groups from the pattern so that you can access them by using named properties on matches.</span></span> <span data-ttu-id="ed997-265">Podczas projektowania dostawcy typu, należy wziąć pod uwagę, jak jego narażony interfejs API powinien wyglądać dla użytkowników końcowych i jak ten projekt przełoży się na kod .NET.</span><span class="sxs-lookup"><span data-stu-id="ed997-265">When you design a type provider, you should consider how its exposed API should look to end users and how this design will translate to .NET code.</span></span> <span data-ttu-id="ed997-266">W poniższym przykładzie pokazano, jak użyć takiego interfejsu API, aby uzyskać składniki kodu kierunkowego:</span><span class="sxs-lookup"><span data-stu-id="ed997-266">The following example shows how to use such an API to get the components of the area code:</span></span>

```fsharp
type T = RegexTyped< @"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)">
let reg = T()
let result = T.IsMatch("425-555-2345")
let r = reg.Match("425-555-2345").Group_AreaCode.Value //r equals "425"
```

<span data-ttu-id="ed997-267">W poniższym przykładzie pokazano, jak dostawca typów tłumaczy te wywołania:</span><span class="sxs-lookup"><span data-stu-id="ed997-267">The following example shows how the type provider translates these calls:</span></span>

```fsharp
let reg = new Regex(@"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)")
let result = reg.IsMatch("425-123-2345")
let r = reg.Match("425-123-2345").Groups.["AreaCode"].Value //r equals "425"
```

<span data-ttu-id="ed997-268">Pamiętaj o następujących kwestiach:</span><span class="sxs-lookup"><span data-stu-id="ed997-268">Note the following points:</span></span>

- <span data-ttu-id="ed997-269">Standardowy typ Regex reprezentuje `RegexTyped` typ sparametryzowany.</span><span class="sxs-lookup"><span data-stu-id="ed997-269">The standard Regex type represents the parameterized `RegexTyped` type.</span></span>

- <span data-ttu-id="ed997-270">Konstruktor `RegexTyped` powoduje wywołanie konstruktora Regex, przekazując w statycznym argumentem typu dla wzorca.</span><span class="sxs-lookup"><span data-stu-id="ed997-270">The `RegexTyped` constructor results in a call to the Regex constructor, passing in the static type argument for the pattern.</span></span>

- <span data-ttu-id="ed997-271">Wyniki `Match` metody są reprezentowane przez <xref:System.Text.RegularExpressions.Match> typ standardowy.</span><span class="sxs-lookup"><span data-stu-id="ed997-271">The results of the `Match` method are represented by the standard <xref:System.Text.RegularExpressions.Match> type.</span></span>

- <span data-ttu-id="ed997-272">Każda nazwana grupa powoduje podaną właściwość, a dostęp do właściwości powoduje `Groups` użycie indeksatora w kolekcji dopasowania.</span><span class="sxs-lookup"><span data-stu-id="ed997-272">Each named group results in a provided property, and accessing the property results in a use of an indexer on a match’s `Groups` collection.</span></span>

<span data-ttu-id="ed997-273">Poniższy kod jest rdzeniem logiki do zaimplementowania takiego dostawcy, a w tym przykładzie pomija dodanie wszystkich elementów członkowskich do podanego typu.</span><span class="sxs-lookup"><span data-stu-id="ed997-273">The following code is the core of the logic to implement such a provider, and this example omits the addition of all members to the provided type.</span></span> <span data-ttu-id="ed997-274">Aby uzyskać informacje o każdym dodanym człoponiewędowym, zobacz odpowiednią sekcję w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="ed997-274">For information about each added member, see the appropriate section later in this topic.</span></span> <span data-ttu-id="ed997-275">Aby uzyskać pełny kod, pobierz przykład z [pakietu próbki F# 3.0](https://archive.codeplex.com/?p=fsharp3sample) w witrynie codeplex.</span><span class="sxs-lookup"><span data-stu-id="ed997-275">For the full code, download the sample from the [F# 3.0 Sample Pack](https://archive.codeplex.com/?p=fsharp3sample) on the CodePlex website.</span></span>

```fsharp
namespace Samples.FSharp.RegexTypeProvider

open System.Reflection
open Microsoft.FSharp.Core.CompilerServices
open Samples.FSharp.ProvidedTypes
open System.Text.RegularExpressions

[<TypeProvider>]
type public CheckedRegexProvider() as this =
    inherit TypeProviderForNamespaces()

    // Get the assembly and namespace used to house the provided types
    let thisAssembly = Assembly.GetExecutingAssembly()
    let rootNamespace = "Samples.FSharp.RegexTypeProvider"
    let baseTy = typeof<obj>
    let staticParams = [ProvidedStaticParameter("pattern", typeof<string>)]

    let regexTy = ProvidedTypeDefinition(thisAssembly, rootNamespace, "RegexTyped", Some baseTy)

    do regexTy.DefineStaticParameters(
        parameters=staticParams,
        instantiationFunction=(fun typeName parameterValues ->

          match parameterValues with
          | [| :? string as pattern|] ->

            // Create an instance of the regular expression.
            //
            // This will fail with System.ArgumentException if the regular expression is not valid.
            // The exception will escape the type provider and be reported in client code.
            let r = System.Text.RegularExpressions.Regex(pattern)

            // Declare the typed regex provided type.
            // The type erasure of this type is 'obj', even though the representation will always be a Regex
            // This, combined with hiding the object methods, makes the IntelliSense experience simpler.
            let ty =
              ProvidedTypeDefinition(
                thisAssembly,
                rootNamespace,
                typeName,
                baseType = Some baseTy)

            ...

            ty
          | _ -> failwith "unexpected parameter values"))

    do this.AddNamespace(rootNamespace, [regexTy])

[<TypeProviderAssembly>]
do ()
```

<span data-ttu-id="ed997-276">Pamiętaj o następujących kwestiach:</span><span class="sxs-lookup"><span data-stu-id="ed997-276">Note the following points:</span></span>

- <span data-ttu-id="ed997-277">Dostawca typu przyjmuje dwa parametry `pattern`statyczne: , który `options`jest obowiązkowy i , które są opcjonalne (ponieważ podano wartość domyślną).</span><span class="sxs-lookup"><span data-stu-id="ed997-277">The type provider takes two static parameters: the `pattern`, which is mandatory, and the `options`, which are optional (because a default value is provided).</span></span>

- <span data-ttu-id="ed997-278">Po podasz argumenty statyczne, należy utworzyć wystąpienie wyrażenia regularnego.</span><span class="sxs-lookup"><span data-stu-id="ed997-278">After the static arguments are supplied, you create an instance of the regular expression.</span></span> <span data-ttu-id="ed997-279">To wystąpienie zgłosi wyjątek, jeśli program Regex jest nieprawidłowo sformułowany, a ten błąd zostanie zgłoszony użytkownikom.</span><span class="sxs-lookup"><span data-stu-id="ed997-279">This instance will throw an exception if the Regex is malformed, and this error will be reported to users.</span></span>

- <span data-ttu-id="ed997-280">W `DefineStaticParameters` ramach wywołania zwrotnego można zdefiniować typ, który zostanie zwrócony po podasz argumenty.</span><span class="sxs-lookup"><span data-stu-id="ed997-280">Within the `DefineStaticParameters` callback, you define the type that will be returned after the arguments are supplied.</span></span>

- <span data-ttu-id="ed997-281">Ten kod `HideObjectMethods` ustawia się na prawdziwe, dzięki czemu środowisko IntelliSense pozostanie usprawnione.</span><span class="sxs-lookup"><span data-stu-id="ed997-281">This code sets `HideObjectMethods` to true so that the IntelliSense experience will remain streamlined.</span></span> <span data-ttu-id="ed997-282">Ten atrybut powoduje `Equals` `GetHashCode`, `Finalize`, `GetType` i elementy członkowskie mają być pomijane z list IntelliSense dla podanego obiektu.</span><span class="sxs-lookup"><span data-stu-id="ed997-282">This attribute causes the `Equals`, `GetHashCode`, `Finalize`, and `GetType` members to be suppressed from IntelliSense lists for a provided object.</span></span>

- <span data-ttu-id="ed997-283">Używasz `obj` jako typ podstawowy metody, ale użyjesz `Regex` obiektu jako reprezentacji środowiska uruchomieniowego tego typu, jak pokazano w następnym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="ed997-283">You use `obj` as the base type of the method, but you’ll use a `Regex` object as the runtime representation of this type, as the next example shows.</span></span>

- <span data-ttu-id="ed997-284">Wywołanie konstruktora `Regex` <xref:System.ArgumentException> zgłasza, gdy wyrażenie regularne nie jest prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="ed997-284">The call to the `Regex` constructor throws a <xref:System.ArgumentException> when a regular expression isn’t valid.</span></span> <span data-ttu-id="ed997-285">Kompilator przechwytuje ten wyjątek i zgłasza komunikat o błędzie do użytkownika w czasie kompilacji lub w edytorze programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ed997-285">The compiler catches this exception and reports an error message to the user at compile time or in the Visual Studio editor.</span></span> <span data-ttu-id="ed997-286">Ten wyjątek umożliwia weryfikacji wyrażeń regularnych bez uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ed997-286">This exception enables regular expressions to be validated without running an application.</span></span>

<span data-ttu-id="ed997-287">Typ zdefiniowany powyżej nie jest jeszcze przydatne, ponieważ nie zawiera żadnych znaczących metod lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="ed997-287">The type defined above isn't useful yet because it doesn’t contain any meaningful methods or properties.</span></span> <span data-ttu-id="ed997-288">Najpierw dodaj metodę `IsMatch` statyczną:</span><span class="sxs-lookup"><span data-stu-id="ed997-288">First, add a static `IsMatch` method:</span></span>

```fsharp
let isMatch =
    ProvidedMethod(
        methodName = "IsMatch",
        parameters = [ProvidedParameter("input", typeof<string>)],
        returnType = typeof<bool>,
        isStatic = true,
        invokeCode = fun args -> <@@ Regex.IsMatch(%%args.[0], pattern) @@>)

isMatch.AddXmlDoc "Indicates whether the regular expression finds a match in the specified input string."
ty.AddMember isMatch
```

<span data-ttu-id="ed997-289">Poprzedni kod definiuje metodę `IsMatch`, która przyjmuje ciąg jako `bool`dane wejściowe i zwraca .</span><span class="sxs-lookup"><span data-stu-id="ed997-289">The previous code defines a method `IsMatch`, which takes a string as input and returns a `bool`.</span></span> <span data-ttu-id="ed997-290">Jedyną trudną częścią jest `args` użycie argumentu w `InvokeCode` definicji.</span><span class="sxs-lookup"><span data-stu-id="ed997-290">The only tricky part is the use of the `args` argument within the `InvokeCode` definition.</span></span> <span data-ttu-id="ed997-291">W tym `args` przykładzie znajduje się lista cytatów, która reprezentuje argumenty tej metody.</span><span class="sxs-lookup"><span data-stu-id="ed997-291">In this example, `args` is a list of quotations that represents the arguments to this method.</span></span> <span data-ttu-id="ed997-292">Jeśli metoda jest metodą wystąpienia, pierwszy `this` argument reprezentuje argument.</span><span class="sxs-lookup"><span data-stu-id="ed997-292">If the method is an instance method, the first argument represents the `this` argument.</span></span> <span data-ttu-id="ed997-293">Jednak dla metody statycznej argumenty są tylko jawne argumenty do metody.</span><span class="sxs-lookup"><span data-stu-id="ed997-293">However, for a static method, the arguments are all just the explicit arguments to the method.</span></span> <span data-ttu-id="ed997-294">Należy zauważyć, że typ wartości cytowanej powinien być zgodny `bool`z określonym typem zwracanym (w tym przypadku).</span><span class="sxs-lookup"><span data-stu-id="ed997-294">Note that the type of the quoted value should match the specified return type (in this case, `bool`).</span></span> <span data-ttu-id="ed997-295">Należy również zauważyć, że `AddXmlDoc` ten kod używa metody, aby upewnić się, że podana metoda ma również użyteczną dokumentację, którą można dostarczyć za pośrednictwem intellisense.</span><span class="sxs-lookup"><span data-stu-id="ed997-295">Also note that this code uses the `AddXmlDoc` method to make sure that the provided method also has useful documentation, which you can supply through IntelliSense.</span></span>

<span data-ttu-id="ed997-296">Następnie dodaj wystąpienie Match metody.</span><span class="sxs-lookup"><span data-stu-id="ed997-296">Next, add an instance Match method.</span></span> <span data-ttu-id="ed997-297">Jednak ta metoda powinna zwracać `Match` wartość podanego typu, dzięki czemu grupy są dostępne w sposób silnie typiwany.</span><span class="sxs-lookup"><span data-stu-id="ed997-297">However, this method should return a value of a provided `Match` type so that the groups can be accessed in a strongly typed fashion.</span></span> <span data-ttu-id="ed997-298">W związku z `Match` tym najpierw zadeklarować typ.</span><span class="sxs-lookup"><span data-stu-id="ed997-298">Thus, you first declare the `Match` type.</span></span> <span data-ttu-id="ed997-299">Ponieważ ten typ zależy od wzorca, który został dostarczony jako argument statyczny, ten typ musi być zagnieżdżony w definicji typu sparametryzowanego:</span><span class="sxs-lookup"><span data-stu-id="ed997-299">Because this type depends on the pattern that was supplied as a static argument, this type must be nested within the parameterized type definition:</span></span>

```fsharp
let matchTy =
    ProvidedTypeDefinition(
        "MatchType",
        baseType = Some baseTy,
        hideObjectMethods = true)

ty.AddMember matchTy
```

<span data-ttu-id="ed997-300">Następnie należy dodać jedną właściwość do typu Dopasuj dla każdej grupy.</span><span class="sxs-lookup"><span data-stu-id="ed997-300">You then add one property to the Match type for each group.</span></span> <span data-ttu-id="ed997-301">W czasie wykonywania dopasowanie jest reprezentowana jako <xref:System.Text.RegularExpressions.Match> wartość, więc cytat, który <xref:System.Text.RegularExpressions.Match.Groups> definiuje właściwość musi użyć właściwości indeksowane, aby uzyskać odpowiednią grupę.</span><span class="sxs-lookup"><span data-stu-id="ed997-301">At runtime, a match is represented as a <xref:System.Text.RegularExpressions.Match> value, so the quotation that defines the property must use the <xref:System.Text.RegularExpressions.Match.Groups> indexed property to get the relevant group.</span></span>

```fsharp
for group in r.GetGroupNames() do
    // Ignore the group named 0, which represents all input.
    if group <> "0" then
    let prop =
      ProvidedProperty(
        propertyName = group,
        propertyType = typeof<Group>,
        getterCode = fun args -> <@@ ((%%args.[0]:obj) :?> Match).Groups.[group] @@>)
        prop.AddXmlDoc(sprintf @"Gets the ""%s"" group from this match" group)
    matchTy.AddMember prop
```

<span data-ttu-id="ed997-302">Ponownie należy zauważyć, że dodajesz dokumentację XML do dostarczonej właściwości.</span><span class="sxs-lookup"><span data-stu-id="ed997-302">Again, note that you’re adding XML documentation to the provided property.</span></span> <span data-ttu-id="ed997-303">Należy również zauważyć, że właściwość może być odczytywana, jeśli `GetterCode` `SetterCode` funkcja jest dostępna, a właściwość może być zapisywana, jeśli funkcja jest dostępna, więc wynikowa właściwość jest tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="ed997-303">Also note that a property can be read if a `GetterCode` function is provided, and the property can be written if a `SetterCode` function is provided, so the resulting property is read only.</span></span>

<span data-ttu-id="ed997-304">Teraz można utworzyć metodę wystąpienia, która `Match` zwraca wartość tego typu:</span><span class="sxs-lookup"><span data-stu-id="ed997-304">Now you can create an instance method that returns a value of this `Match` type:</span></span>

```fsharp
let matchMethod =
    ProvidedMethod(
        methodName = "Match",
        parameters = [ProvidedParameter("input", typeof<string>)],
        returnType = matchTy,
        invokeCode = fun args -> <@@ ((%%args.[0]:obj) :?> Regex).Match(%%args.[1]) :> obj @@>)

matchMeth.AddXmlDoc "Searches the specified input string for the first occurrence of this regular expression"

ty.AddMember matchMeth
```

<span data-ttu-id="ed997-305">Ponieważ tworzysz metodę wystąpienia, `args.[0]` reprezentuje `RegexTyped` wystąpienie, w którym metoda `args.[1]` jest wywoływana i jest argumentem wejściowym.</span><span class="sxs-lookup"><span data-stu-id="ed997-305">Because you are creating an instance method, `args.[0]` represents the `RegexTyped` instance on which the method is being called, and `args.[1]` is the input argument.</span></span>

<span data-ttu-id="ed997-306">Na koniec podaj konstruktora, aby można było utworzyć wystąpienia podanego typu.</span><span class="sxs-lookup"><span data-stu-id="ed997-306">Finally, provide a constructor so that instances of the provided type can be created.</span></span>

```fsharp
let ctor =
    ProvidedConstructor(
        parameters = [],
        invokeCode = fun args -> <@@ Regex(pattern, options) :> obj @@>)

ctor.AddXmlDoc("Initializes a regular expression instance.")

ty.AddMember ctor
```

<span data-ttu-id="ed997-307">Konstruktor tylko wymazuje do tworzenia standardowego wystąpienia regex .NET, który `obj` jest ponownie zapakowane do obiektu, ponieważ jest usunięcie podanego typu.</span><span class="sxs-lookup"><span data-stu-id="ed997-307">The constructor merely erases to the creation of a standard .NET Regex instance, which is again boxed to an object because `obj` is the erasure of the provided type.</span></span> <span data-ttu-id="ed997-308">Z tej zmiany, użycie przykładowego interfejsu API, który określony wcześniej w temacie działa zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="ed997-308">With that change, the sample API usage that specified earlier in the topic works as expected.</span></span> <span data-ttu-id="ed997-309">Poniższy kod jest kompletny i ostateczny:</span><span class="sxs-lookup"><span data-stu-id="ed997-309">The following code is complete and final:</span></span>

```fsharp
namespace Samples.FSharp.RegexTypeProvider

open System.Reflection
open Microsoft.FSharp.Core.CompilerServices
open Samples.FSharp.ProvidedTypes
open System.Text.RegularExpressions

[<TypeProvider>]
type public CheckedRegexProvider() as this =
    inherit TypeProviderForNamespaces()

    // Get the assembly and namespace used to house the provided types.
    let thisAssembly = Assembly.GetExecutingAssembly()
    let rootNamespace = "Samples.FSharp.RegexTypeProvider"
    let baseTy = typeof<obj>
    let staticParams = [ProvidedStaticParameter("pattern", typeof<string>)]

    let regexTy = ProvidedTypeDefinition(thisAssembly, rootNamespace, "RegexTyped", Some baseTy)

    do regexTy.DefineStaticParameters(
        parameters=staticParams,
        instantiationFunction=(fun typeName parameterValues ->

            match parameterValues with
            | [| :? string as pattern|] ->

                // Create an instance of the regular expression.

                let r = System.Text.RegularExpressions.Regex(pattern)

                // Declare the typed regex provided type.

                let ty =
                    ProvidedTypeDefinition(
                        thisAssembly,
                        rootNamespace,
                        typeName,
                        baseType = Some baseTy)

                ty.AddXmlDoc "A strongly typed interface to the regular expression '%s'"

                // Provide strongly typed version of Regex.IsMatch static method.
                let isMatch =
                    ProvidedMethod(
                        methodName = "IsMatch",
                        parameters = [ProvidedParameter("input", typeof<string>)],
                        returnType = typeof<bool>,
                        isStatic = true,
                        invokeCode = fun args -> <@@ Regex.IsMatch(%%args.[0], pattern) @@>)

                isMatch.AddXmlDoc "Indicates whether the regular expression finds a match in the specified input string"

                ty.AddMember isMatch

                // Provided type for matches
                // Again, erase to obj even though the representation will always be a Match
                let matchTy =
                    ProvidedTypeDefinition(
                        "MatchType",
                        baseType = Some baseTy,
                        hideObjectMethods = true)

                // Nest the match type within parameterized Regex type.
                ty.AddMember matchTy

                // Add group properties to match type
                for group in r.GetGroupNames() do
                    // Ignore the group named 0, which represents all input.
                    if group <> "0" then
                        let prop =
                          ProvidedProperty(
                            propertyName = group,
                            propertyType = typeof<Group>,
                            getterCode = fun args -> <@@ ((%%args.[0]:obj) :?> Match).Groups.[group] @@>)
                        prop.AddXmlDoc(sprintf @"Gets the ""%s"" group from this match" group)
                        matchTy.AddMember(prop)

                // Provide strongly typed version of Regex.Match instance method.
                let matchMeth =
                  ProvidedMethod(
                    methodName = "Match",
                    parameters = [ProvidedParameter("input", typeof<string>)],
                    returnType = matchTy,
                    invokeCode = fun args -> <@@ ((%%args.[0]:obj) :?> Regex).Match(%%args.[1]) :> obj @@>)
                matchMeth.AddXmlDoc "Searches the specified input string for the first occurrence of this regular expression"

                ty.AddMember matchMeth

                // Declare a constructor.
                let ctor =
                  ProvidedConstructor(
                    parameters = [],
                    invokeCode = fun args -> <@@ Regex(pattern) :> obj @@>)

                // Add documentation to the constructor.
                ctor.AddXmlDoc "Initializes a regular expression instance"

                ty.AddMember ctor

                ty
            | _ -> failwith "unexpected parameter values"))

    do this.AddNamespace(rootNamespace, [regexTy])

[<TypeProviderAssembly>]
do ()
```

### <a name="key-lessons"></a><span data-ttu-id="ed997-310">Kluczowe lekcje</span><span class="sxs-lookup"><span data-stu-id="ed997-310">Key Lessons</span></span>

<span data-ttu-id="ed997-311">W tej sekcji wyjaśniono, jak utworzyć dostawcę typów, który działa na jego parametrów statycznych.</span><span class="sxs-lookup"><span data-stu-id="ed997-311">This section explained how to create a type provider that operates on its static parameters.</span></span> <span data-ttu-id="ed997-312">Dostawca sprawdza parametr statyczny i udostępnia operacje na podstawie jego wartości.</span><span class="sxs-lookup"><span data-stu-id="ed997-312">The provider checks the static parameter and provides operations based on its value.</span></span>

## <a name="a-type-provider-that-is-backed-by-local-data"></a><span data-ttu-id="ed997-313">Dostawca typów, który jest wspierany przez dane lokalne</span><span class="sxs-lookup"><span data-stu-id="ed997-313">A Type Provider That Is Backed By Local Data</span></span>

<span data-ttu-id="ed997-314">Często można chcieć, aby dostawcy typów prezentują interfejsy API na podstawie nie tylko parametrów statycznych, ale także informacji z systemów lokalnych lub zdalnych.</span><span class="sxs-lookup"><span data-stu-id="ed997-314">Frequently you might want type providers to present APIs based on not only static parameters but also information from local or remote systems.</span></span> <span data-ttu-id="ed997-315">W tej sekcji omówiono dostawców typów, które są oparte na danych lokalnych, takich jak pliki danych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="ed997-315">This section discusses type providers that are based on local data, such as local data files.</span></span>

### <a name="simple-csv-file-provider"></a><span data-ttu-id="ed997-316">Prosty dostawca plików CSV</span><span class="sxs-lookup"><span data-stu-id="ed997-316">Simple CSV File Provider</span></span>

<span data-ttu-id="ed997-317">Na przykład należy wziąć pod uwagę dostawcę typów dostępu do danych naukowych w formacie CSV (Comma Separated Value).</span><span class="sxs-lookup"><span data-stu-id="ed997-317">As a simple example, consider a type provider for accessing scientific data in Comma Separated Value (CSV) format.</span></span> <span data-ttu-id="ed997-318">W tej sekcji przyjęto założenie, że pliki CSV zawierają wiersz nagłówka, po którym następują dane zmiennoprzecinkowa, jak pokazano w poniższej tabeli:</span><span class="sxs-lookup"><span data-stu-id="ed997-318">This section assumes that the CSV files contain a header row followed by floating point data, as the following table illustrates:</span></span>

|<span data-ttu-id="ed997-319">Odległość (metr)</span><span class="sxs-lookup"><span data-stu-id="ed997-319">Distance (meter)</span></span>|<span data-ttu-id="ed997-320">Czas (drugi)</span><span class="sxs-lookup"><span data-stu-id="ed997-320">Time (second)</span></span>|
|----------------|-------------|
|<span data-ttu-id="ed997-321">50.0</span><span class="sxs-lookup"><span data-stu-id="ed997-321">50.0</span></span>|<span data-ttu-id="ed997-322">3.7</span><span class="sxs-lookup"><span data-stu-id="ed997-322">3.7</span></span>|
|<span data-ttu-id="ed997-323">100.0</span><span class="sxs-lookup"><span data-stu-id="ed997-323">100.0</span></span>|<span data-ttu-id="ed997-324">5.2</span><span class="sxs-lookup"><span data-stu-id="ed997-324">5.2</span></span>|
|<span data-ttu-id="ed997-325">150.0</span><span class="sxs-lookup"><span data-stu-id="ed997-325">150.0</span></span>|<span data-ttu-id="ed997-326">6.4</span><span class="sxs-lookup"><span data-stu-id="ed997-326">6.4</span></span>|

<span data-ttu-id="ed997-327">W tej sekcji pokazano, jak podać typ, którego `Distance` można użyć, aby uzyskać wiersze z właściwością typu `float<meter>` i właściwością `Time` typu `float<second>`.</span><span class="sxs-lookup"><span data-stu-id="ed997-327">This section shows how to provide a type that you can use to get rows with a `Distance` property of type `float<meter>` and a `Time` property of type `float<second>`.</span></span> <span data-ttu-id="ed997-328">Dla uproszczenia, następujące założenia są następujące:</span><span class="sxs-lookup"><span data-stu-id="ed997-328">For simplicity, the following assumptions are made:</span></span>

- <span data-ttu-id="ed997-329">Nazwy nagłówków są bezeszli lub mają formę "Nazwa (jednostka)" i nie zawierają przecinków.</span><span class="sxs-lookup"><span data-stu-id="ed997-329">Header names are either unit-less or have the form "Name (unit)" and don't contain commas.</span></span>

- <span data-ttu-id="ed997-330">Wszystkie jednostki są jednostkami System International (SI) zgodnie z definicją [modułu microsoft.FSharp.Data.UnitSystems.SI.UnitNames Module (F#).](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b)</span><span class="sxs-lookup"><span data-stu-id="ed997-330">Units are all System International (SI) units as the [Microsoft.FSharp.Data.UnitSystems.SI.UnitNames Module (F#)](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b) module defines.</span></span>

- <span data-ttu-id="ed997-331">Jednostki są proste (na przykład miernik) zamiast związku (na przykład metr / sekundę).</span><span class="sxs-lookup"><span data-stu-id="ed997-331">Units are all simple (for example, meter) rather than compound (for example, meter/second).</span></span>

- <span data-ttu-id="ed997-332">Wszystkie kolumny zawierają dane zmiennoprzecinkowe.</span><span class="sxs-lookup"><span data-stu-id="ed997-332">All columns contain floating point data.</span></span>

<span data-ttu-id="ed997-333">Bardziej kompletny dostawca poluzowałby te ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="ed997-333">A more complete provider would loosen these restrictions.</span></span>

<span data-ttu-id="ed997-334">Ponownie pierwszym krokiem jest rozważenie, jak powinien wyglądać interfejs API.</span><span class="sxs-lookup"><span data-stu-id="ed997-334">Again the first step is to consider how the API should look.</span></span> <span data-ttu-id="ed997-335">Biorąc `info.csv` pod uwagę plik z zawartością z poprzedniej tabeli (w formacie oddzielonym przecinkami), użytkownicy dostawcy powinni mieć możliwość pisania kodu podobnego do następującego przykładu:</span><span class="sxs-lookup"><span data-stu-id="ed997-335">Given an `info.csv` file with the contents from the previous table (in comma-separated format), users of the provider should be able to write code that resembles the following example:</span></span>

```fsharp
let info = new MiniCsv<"info.csv">()
for row in info.Data do
let time = row.Time
printfn "%f" (float time)
```

<span data-ttu-id="ed997-336">W takim przypadku kompilator należy przekonwertować te wywołania na coś podobnego do następującego przykładu:</span><span class="sxs-lookup"><span data-stu-id="ed997-336">In this case, the compiler should convert these calls into something like the following example:</span></span>

```fsharp
let info = new CsvFile("info.csv")
for row in info.Data do
let (time:float) = row.[1]
printfn "%f" (float time)
```

<span data-ttu-id="ed997-337">Optymalne tłumaczenie będzie wymagać dostawcy `CsvFile` typu do zdefiniowania typu rzeczywistego w zestawie dostawcy typu.</span><span class="sxs-lookup"><span data-stu-id="ed997-337">The optimal translation will require the type provider to define a real `CsvFile` type in the type provider's assembly.</span></span> <span data-ttu-id="ed997-338">Dostawcy typów często polegają na kilku typach i metodach pomocnika, aby zawinąć ważną logikę.</span><span class="sxs-lookup"><span data-stu-id="ed997-338">Type providers often rely on a few helper types and methods to wrap important logic.</span></span> <span data-ttu-id="ed997-339">Ponieważ miary są usuwane w czasie wykonywania, można użyć `float[]` jako typ wymazane dla wiersza.</span><span class="sxs-lookup"><span data-stu-id="ed997-339">Because measures are erased at runtime, you can use a `float[]` as the erased type for a row.</span></span> <span data-ttu-id="ed997-340">Kompilator będzie traktować różne kolumny jako posiadające różne typy miar.</span><span class="sxs-lookup"><span data-stu-id="ed997-340">The compiler will treat different columns as having different measure types.</span></span> <span data-ttu-id="ed997-341">Na przykład pierwsza kolumna w `float<meter>`naszym przykładzie `float<second>`ma typ , a druga ma .</span><span class="sxs-lookup"><span data-stu-id="ed997-341">For example, the first column in our example has type `float<meter>`, and the second has `float<second>`.</span></span> <span data-ttu-id="ed997-342">Jednak wymazana reprezentacja może pozostać dość prosta.</span><span class="sxs-lookup"><span data-stu-id="ed997-342">However, the erased representation can remain quite simple.</span></span>

<span data-ttu-id="ed997-343">Poniższy kod przedstawia rdzeń implementacji.</span><span class="sxs-lookup"><span data-stu-id="ed997-343">The following code shows the core of the implementation.</span></span>

```fsharp
// Simple type wrapping CSV data
type CsvFile(filename) =
    // Cache the sequence of all data lines (all lines but the first)
    let data =
        seq {
            for line in File.ReadAllLines(filename) |> Seq.skip 1 ->
                line.Split(',') |> Array.map float
        }
        |> Seq.cache
    member _.Data = data

[<TypeProvider>]
type public MiniCsvProvider(cfg:TypeProviderConfig) as this =
    inherit TypeProviderForNamespaces(cfg)

    // Get the assembly and namespace used to house the provided types.
    let asm = System.Reflection.Assembly.GetExecutingAssembly()
    let ns = "Samples.FSharp.MiniCsvProvider"

    // Create the main provided type.
    let csvTy = ProvidedTypeDefinition(asm, ns, "MiniCsv", Some(typeof<obj>))

    // Parameterize the type by the file to use as a template.
    let filename = ProvidedStaticParameter("filename", typeof<string>)
    do csvTy.DefineStaticParameters([filename], fun tyName [| :? string as filename |] ->

        // Resolve the filename relative to the resolution folder.
        let resolvedFilename = Path.Combine(cfg.ResolutionFolder, filename)

        // Get the first line from the file.
        let headerLine = File.ReadLines(resolvedFilename) |> Seq.head

        // Define a provided type for each row, erasing to a float[].
        let rowTy = ProvidedTypeDefinition("Row", Some(typeof<float[]>))

        // Extract header names from the file, splitting on commas.
        // use Regex matching to get the position in the row at which the field occurs
        let headers = Regex.Matches(headerLine, "[^,]+")

        // Add one property per CSV field.
        for i in 0 .. headers.Count - 1 do
            let headerText = headers.[i].Value

            // Try to decompose this header into a name and unit.
            let fieldName, fieldTy =
                let m = Regex.Match(headerText, @"(?<field>.+) \((?<unit>.+)\)")
                if m.Success then

                    let unitName = m.Groups.["unit"].Value
                    let units = ProvidedMeasureBuilder.Default.SI unitName
                    m.Groups.["field"].Value, ProvidedMeasureBuilder.Default.AnnotateType(typeof<float>,[units])

                else
                    // no units, just treat it as a normal float
                    headerText, typeof<float>

            let prop =
                ProvidedProperty(fieldName, fieldTy,
                    getterCode = fun [row] -> <@@ (%%row:float[]).[i] @@>)

            // Add metadata that defines the property's location in the referenced file.
            prop.AddDefinitionLocation(1, headers.[i].Index + 1, filename)
            rowTy.AddMember(prop)

        // Define the provided type, erasing to CsvFile.
        let ty = ProvidedTypeDefinition(asm, ns, tyName, Some(typeof<CsvFile>))

        // Add a parameterless constructor that loads the file that was used to define the schema.
        let ctor0 =
            ProvidedConstructor([],
                invokeCode = fun [] -> <@@ CsvFile(resolvedFilename) @@>)
        ty.AddMember ctor0

        // Add a constructor that takes the file name to load.
        let ctor1 = ProvidedConstructor([ProvidedParameter("filename", typeof<string>)],
            invokeCode = fun [filename] -> <@@ CsvFile(%%filename) @@>)
        ty.AddMember ctor1

        // Add a more strongly typed Data property, which uses the existing property at runtime.
        let prop =
            ProvidedProperty("Data", typedefof<seq<_>>.MakeGenericType(rowTy),
                getterCode = fun [csvFile] -> <@@ (%%csvFile:CsvFile).Data @@>)
        ty.AddMember prop

        // Add the row type as a nested type.
        ty.AddMember rowTy
        ty)

    // Add the type to the namespace.
    do this.AddNamespace(ns, [csvTy])
```

<span data-ttu-id="ed997-344">Należy zwrócić uwagę na następujące punkty dotyczące implementacji:</span><span class="sxs-lookup"><span data-stu-id="ed997-344">Note the following points about the implementation:</span></span>

- <span data-ttu-id="ed997-345">Przeciążone konstruktory umożliwiają odczytanie oryginalnego pliku lub pliku, który ma identyczny schemat.</span><span class="sxs-lookup"><span data-stu-id="ed997-345">Overloaded constructors allow either the original file or one that has an identical schema to be read.</span></span> <span data-ttu-id="ed997-346">Ten wzorzec jest typowy podczas pisania dostawcy typów dla lokalnych lub zdalnych źródeł danych, a ten wzorzec umożliwia użycie pliku lokalnego jako szablonu dla danych zdalnych.</span><span class="sxs-lookup"><span data-stu-id="ed997-346">This pattern is common when you write a type provider for local or remote data sources, and this pattern allows a local file to be used as the template for remote data.</span></span>

- <span data-ttu-id="ed997-347">Można użyć [TypeProviderConfig](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44) wartość, która jest przekazywana do konstruktora dostawcy typu, aby rozpoznać względne nazwy plików.</span><span class="sxs-lookup"><span data-stu-id="ed997-347">You can use the [TypeProviderConfig](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44) value that’s passed in to the type provider constructor to resolve relative file names.</span></span>

- <span data-ttu-id="ed997-348">Za pomocą `AddDefinitionLocation` tej metody można zdefiniować lokalizację podanych właściwości.</span><span class="sxs-lookup"><span data-stu-id="ed997-348">You can use the `AddDefinitionLocation` method to define the location of the provided properties.</span></span> <span data-ttu-id="ed997-349">W związku z `Go To Definition` tym jeśli używasz na dostarczonej właściwości, plik CSV otworzy się w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ed997-349">Therefore, if you use `Go To Definition` on a provided property, the CSV file will open in Visual Studio.</span></span>

- <span data-ttu-id="ed997-350">Można użyć `ProvidedMeasureBuilder` tego typu, aby wyszukać jednostki `float<_>` SI i wygenerować odpowiednie typy.</span><span class="sxs-lookup"><span data-stu-id="ed997-350">You can use the `ProvidedMeasureBuilder` type to look up the SI units and to generate the relevant `float<_>` types.</span></span>

### <a name="key-lessons"></a><span data-ttu-id="ed997-351">Kluczowe lekcje</span><span class="sxs-lookup"><span data-stu-id="ed997-351">Key Lessons</span></span>

<span data-ttu-id="ed997-352">W tej sekcji wyjaśniono, jak utworzyć dostawcę typów dla lokalnego źródła danych z prostym schematem, który znajduje się w samym źródle danych.</span><span class="sxs-lookup"><span data-stu-id="ed997-352">This section explained how to create a type provider for a local data source with a simple schema that's contained in the data source itself.</span></span>

## <a name="going-further"></a><span data-ttu-id="ed997-353">Idąc dalej</span><span class="sxs-lookup"><span data-stu-id="ed997-353">Going Further</span></span>

<span data-ttu-id="ed997-354">Poniższe sekcje zawierają sugestie dotyczące dalszych badań.</span><span class="sxs-lookup"><span data-stu-id="ed997-354">The following sections include suggestions for further study.</span></span>

### <a name="a-look-at-the-compiled-code-for-erased-types"></a><span data-ttu-id="ed997-355">Spojrzenie na skompilowany kod dla usuniętych typów</span><span class="sxs-lookup"><span data-stu-id="ed997-355">A Look at the Compiled Code for Erased Types</span></span>

<span data-ttu-id="ed997-356">Aby dać ci pewne pojęcie o tym, jak użycie dostawcy typu odpowiada emitowanemu kodowi, `HelloWorldTypeProvider` przyjrzyj się następującej funkcji przy użyciu używanej wcześniej w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="ed997-356">To give you some idea of how the use of the type provider corresponds to the code that's emitted, look at the following function by using the `HelloWorldTypeProvider` that's used earlier in this topic.</span></span>

```fsharp
let function1 () =
    let obj1 = Samples.HelloWorldTypeProvider.Type1("some data")
    obj1.InstanceProperty
```

<span data-ttu-id="ed997-357">Oto obraz wynikowego kodu dekompilowanego przy użyciu pliku ildasm.exe:</span><span class="sxs-lookup"><span data-stu-id="ed997-357">Here’s an image of the resulting code decompiled by using ildasm.exe:</span></span>

```il
.class public abstract auto ansi sealed Module1
extends [mscorlib]System.Object
{
.custom instance void [FSharp.Core]Microsoft.FSharp.Core.CompilationMappingAtt
ribute::.ctor(valuetype [FSharp.Core]Microsoft.FSharp.Core.SourceConstructFlags)
= ( 01 00 07 00 00 00 00 00 )
.method public static int32  function1() cil managed
{
// Code size       24 (0x18)
.maxstack  3
.locals init ([0] object obj1)
IL_0000:  nop
IL_0001:  ldstr      "some data"
IL_0006:  unbox.any  [mscorlib]System.Object
IL_000b:  stloc.0
IL_000c:  ldloc.0
IL_000d:  call       !!0 [FSharp.Core_2]Microsoft.FSharp.Core.LanguagePrimit
ives/IntrinsicFunctions::UnboxGeneric<string>(object)
IL_0012:  callvirt   instance int32 [mscorlib_3]System.String::get_Length()
IL_0017:  ret
} // end of method Module1::function1

} // end of class Module1
```

<span data-ttu-id="ed997-358">Jak pokazano w przykładzie, wszystkie `Type1` wzmianki o typie i `InstanceProperty` właściwości zostały usunięte, pozostawiając tylko operacje na typy środowiska wykonawczego zaangażowanych.</span><span class="sxs-lookup"><span data-stu-id="ed997-358">As the example shows, all mentions of the type `Type1` and the `InstanceProperty` property have been erased, leaving only operations on the runtime types involved.</span></span>

### <a name="design-and-naming-conventions-for-type-providers"></a><span data-ttu-id="ed997-359">Konwencje projektowania i nazewnictwa dla dostawców typów</span><span class="sxs-lookup"><span data-stu-id="ed997-359">Design and Naming Conventions for Type Providers</span></span>

<span data-ttu-id="ed997-360">Należy przestrzegać następujących konwencji podczas tworzenia dostawców typów.</span><span class="sxs-lookup"><span data-stu-id="ed997-360">Observe the following conventions when authoring type providers.</span></span>

<span data-ttu-id="ed997-361">**Dostawcy protokołów łączności** Ogólnie rzecz biorąc, nazwy większości bibliotek DLL dostawców dla protokołów łączności danych i usług, `TypeProvider` takich `TypeProviders`jak OData lub połączenia SQL, powinny kończyć się w programie lub .</span><span class="sxs-lookup"><span data-stu-id="ed997-361">**Providers for Connectivity Protocols** In general, names of most provider DLLs for data and service connectivity protocols, such as OData or SQL connections, should end in `TypeProvider` or `TypeProviders`.</span></span> <span data-ttu-id="ed997-362">Na przykład należy użyć nazwy biblioteki DLL, która przypomina następujący ciąg:</span><span class="sxs-lookup"><span data-stu-id="ed997-362">For example, use a DLL name that resembles the following string:</span></span>

`Fabrikam.Management.BasicTypeProviders.dll`

<span data-ttu-id="ed997-363">Upewnij się, że podane typy są członkami odpowiedniego obszaru nazw i wskaż zaimplementowany protokół łączności:</span><span class="sxs-lookup"><span data-stu-id="ed997-363">Ensure that your provided types are members of the corresponding namespace, and indicate the connectivity protocol that you implemented:</span></span>

```fsharp
  Fabrikam.Management.BasicTypeProviders.WmiConnection<…>
  Fabrikam.Management.BasicTypeProviders.DataProtocolConnection<…>
```

<span data-ttu-id="ed997-364">**Dostawcy narzędzi do ogólnego kodowania**.</span><span class="sxs-lookup"><span data-stu-id="ed997-364">**Utility Providers for General Coding**.</span></span>  <span data-ttu-id="ed997-365">W przypadku dostawcy typu narzędzia, takiego jak dla wyrażeń regularnych, dostawca typów może być częścią biblioteki podstawowej, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="ed997-365">For a utility type provider such as that for regular expressions, the type provider may be part of a base library, as the following example shows:</span></span>

```fsharp
#r "Fabrikam.Core.Text.Utilities.dll"
```

<span data-ttu-id="ed997-366">W takim przypadku podany typ pojawi się w odpowiednim punkcie zgodnie z normalnymi konwencjami projektowania .NET:</span><span class="sxs-lookup"><span data-stu-id="ed997-366">In this case, the provided type would appear at an appropriate point according to normal .NET design conventions:</span></span>

```fsharp
  open Fabrikam.Core.Text.RegexTyped

  let regex = new RegexTyped<"a+b+a+b+">()
```

<span data-ttu-id="ed997-367">**Źródła danych Singleton**.</span><span class="sxs-lookup"><span data-stu-id="ed997-367">**Singleton Data Sources**.</span></span> <span data-ttu-id="ed997-368">Niektórzy dostawcy typów łączą się z jednym dedykowanym źródłem danych i dostarczają tylko dane.</span><span class="sxs-lookup"><span data-stu-id="ed997-368">Some type providers connect to a single dedicated data source and provide only data.</span></span> <span data-ttu-id="ed997-369">W takim przypadku należy `TypeProvider` upuścić sufiks i użyć normalnych konwencji dla nazewnictwa .NET:</span><span class="sxs-lookup"><span data-stu-id="ed997-369">In this case, you should drop the `TypeProvider` suffix and use normal conventions for .NET naming:</span></span>

```fsharp
#r "Fabrikam.Data.Freebase.dll"

let data = Fabrikam.Data.Freebase.Astronomy.Asteroids
```

<span data-ttu-id="ed997-370">Aby uzyskać więcej `GetConnection` informacji, zobacz konwencję projektowania, która jest opisana w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="ed997-370">For more information, see the `GetConnection` design convention that's described later in this topic.</span></span>

### <a name="design-patterns-for-type-providers"></a><span data-ttu-id="ed997-371">Wzorce projektowe dla dostawców typów</span><span class="sxs-lookup"><span data-stu-id="ed997-371">Design Patterns for Type Providers</span></span>

<span data-ttu-id="ed997-372">W poniższych sekcjach opisano wzorce projektu, których można używać podczas tworzenia dostawców typów.</span><span class="sxs-lookup"><span data-stu-id="ed997-372">The following sections describe design patterns you can use when authoring type providers.</span></span>

#### <a name="the-getconnection-design-pattern"></a><span data-ttu-id="ed997-373">Wzór projektu GetConnection</span><span class="sxs-lookup"><span data-stu-id="ed997-373">The GetConnection Design Pattern</span></span>

<span data-ttu-id="ed997-374">Większość dostawców typów powinny być `GetConnection` zapisywane do korzystania z wzorca, który jest używany przez dostawców typów w FSharp.Data.TypeProviders.dll, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="ed997-374">Most type providers should be written to use the `GetConnection` pattern that's used by the type providers in FSharp.Data.TypeProviders.dll, as the following example shows:</span></span>

```fsharp
#r "Fabrikam.Data.WebDataStore.dll"

type Service = Fabrikam.Data.WebDataStore<…static connection parameters…>

let connection = Service.GetConnection(…dynamic connection parameters…)

let data = connection.Astronomy.Asteroids
```

#### <a name="type-providers-backed-by-remote-data-and-services"></a><span data-ttu-id="ed997-375">Dostawcy typów wspierani przez zdalne dane i usługi</span><span class="sxs-lookup"><span data-stu-id="ed997-375">Type Providers Backed By Remote Data and Services</span></span>

<span data-ttu-id="ed997-376">Przed utworzeniem dostawcy typu, który jest wspierany przez zdalne dane i usługi, należy wziąć pod uwagę szereg problemów, które są związane z programowaniem połączonym.</span><span class="sxs-lookup"><span data-stu-id="ed997-376">Before you create a type provider that's backed by remote data and services, you must consider a range of issues that are inherent in connected programming.</span></span> <span data-ttu-id="ed997-377">Kwestie te obejmują następujące zagadnienia:</span><span class="sxs-lookup"><span data-stu-id="ed997-377">These issues include the following considerations:</span></span>

- <span data-ttu-id="ed997-378">Mapowanie schematu</span><span class="sxs-lookup"><span data-stu-id="ed997-378">schema mapping</span></span>

- <span data-ttu-id="ed997-379">żywotność i unieważnienie w obecności zmiany schematu</span><span class="sxs-lookup"><span data-stu-id="ed997-379">liveness and invalidation in the presence of schema change</span></span>

- <span data-ttu-id="ed997-380">buforowanie schematu</span><span class="sxs-lookup"><span data-stu-id="ed997-380">schema caching</span></span>

- <span data-ttu-id="ed997-381">asynchroniczne implementacje operacji dostępu do danych</span><span class="sxs-lookup"><span data-stu-id="ed997-381">asynchronous implementations of data access operations</span></span>

- <span data-ttu-id="ed997-382">obsługa zapytań, w tym zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="ed997-382">supporting queries, including LINQ queries</span></span>

- <span data-ttu-id="ed997-383">poświadczenia i uwierzytelnianie</span><span class="sxs-lookup"><span data-stu-id="ed997-383">credentials and authentication</span></span>

<span data-ttu-id="ed997-384">W tym temacie nie należy dalej badać tych problemów.</span><span class="sxs-lookup"><span data-stu-id="ed997-384">This topic doesn't explore these issues further.</span></span>

### <a name="additional-authoring-techniques"></a><span data-ttu-id="ed997-385">Dodatkowe techniki tworzenia</span><span class="sxs-lookup"><span data-stu-id="ed997-385">Additional Authoring Techniques</span></span>

<span data-ttu-id="ed997-386">Podczas pisania własnych dostawców typów, można użyć następujących dodatkowych technik.</span><span class="sxs-lookup"><span data-stu-id="ed997-386">When you write your own type providers, you might want to use the following additional techniques.</span></span>

### <a name="creating-types-and-members-on-demand"></a><span data-ttu-id="ed997-387">Tworzenie typów i członków na żądanie</span><span class="sxs-lookup"><span data-stu-id="ed997-387">Creating Types and Members On-Demand</span></span>

<span data-ttu-id="ed997-388">Interfejs API ProvidedType ma opóźnione wersje AddMember.</span><span class="sxs-lookup"><span data-stu-id="ed997-388">The ProvidedType API has delayed versions of AddMember.</span></span>

```fsharp
  type ProvidedType =
      member AddMemberDelayed  : (unit -> MemberInfo)      -> unit
      member AddMembersDelayed : (unit -> MemberInfo list) -> unit
```

<span data-ttu-id="ed997-389">Te wersje są używane do tworzenia przestrzeni na żądanie typów.</span><span class="sxs-lookup"><span data-stu-id="ed997-389">These versions are used to create on-demand spaces of types.</span></span>

### <a name="providing-array-types-and-generic-type-instantiations"></a><span data-ttu-id="ed997-390">Dostarczanie typów macierzy i ogólnych wystąpienia typów</span><span class="sxs-lookup"><span data-stu-id="ed997-390">Providing Array types and Generic Type Instantiations</span></span>

<span data-ttu-id="ed997-391">Należy utworzyć pod warunkiem członków (których podpisy obejmują typy tablic, typy byref `MakePointerType`i `MakeGenericType` wystąpienia typów <xref:System.Type>ogólnych) przy użyciu normalnych `ProvidedTypeDefinitions` `MakeArrayType`, i na każdym wystąpieniu , w tym .</span><span class="sxs-lookup"><span data-stu-id="ed997-391">You make provided members (whose signatures include array types, byref types, and instantiations of generic types) by using the normal `MakeArrayType`, `MakePointerType`, and `MakeGenericType` on any instance of <xref:System.Type>, including `ProvidedTypeDefinitions`.</span></span>

> [!NOTE]
> <span data-ttu-id="ed997-392">W niektórych przypadkach może być trzeba `ProvidedTypeBuilder.MakeGenericType`użyć pomocnika w pliku .</span><span class="sxs-lookup"><span data-stu-id="ed997-392">In some cases you may have to use the helper in `ProvidedTypeBuilder.MakeGenericType`.</span></span>  <span data-ttu-id="ed997-393">Aby uzyskać więcej informacji, zapoznaj [się z dokumentacją SDK dostawcy typów.](https://github.com/fsprojects/FSharp.TypeProviders.SDK/blob/master/README.md#explicit-construction-of-code-makegenerictype-makegenericmethod-and-uncheckedquotations)</span><span class="sxs-lookup"><span data-stu-id="ed997-393">See the [Type Provider SDK documentation](https://github.com/fsprojects/FSharp.TypeProviders.SDK/blob/master/README.md#explicit-construction-of-code-makegenerictype-makegenericmethod-and-uncheckedquotations) for more details.</span></span>

### <a name="providing-unit-of-measure-annotations"></a><span data-ttu-id="ed997-394">Dostarczanie adnotacji jednostki miary</span><span class="sxs-lookup"><span data-stu-id="ed997-394">Providing Unit of Measure Annotations</span></span>

<span data-ttu-id="ed997-395">Interfejs API ProvidedTypes zapewnia pomocników do dostarczania adnotacji miar.</span><span class="sxs-lookup"><span data-stu-id="ed997-395">The ProvidedTypes API provides helpers for providing measure annotations.</span></span> <span data-ttu-id="ed997-396">Na przykład, aby `float<kg>`podać typ, użyj następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="ed997-396">For example, to provide the type `float<kg>`, use the following code:</span></span>

```fsharp
  let measures = ProvidedMeasureBuilder.Default
  let kg = measures.SI "kilogram"
  let m = measures.SI "meter"
  let float_kg = measures.AnnotateType(typeof<float>,[kg])
```

  <span data-ttu-id="ed997-397">Aby podać `Nullable<decimal<kg/m^2>>`typ, użyj następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="ed997-397">To provide the type `Nullable<decimal<kg/m^2>>`, use the following code:</span></span>

```fsharp
  let kgpm2 = measures.Ratio(kg, measures.Square m)
  let dkgpm2 = measures.AnnotateType(typeof<decimal>,[kgpm2])
  let nullableDecimal_kgpm2 = typedefof<System.Nullable<_>>.MakeGenericType [|dkgpm2 |]
```

### <a name="accessing-project-local-or-script-local-resources"></a><span data-ttu-id="ed997-398">Uzyskiwanie dostępu do zasobów lokalnych lub lokalnych w programie Project</span><span class="sxs-lookup"><span data-stu-id="ed997-398">Accessing Project-Local or Script-Local Resources</span></span>

<span data-ttu-id="ed997-399">Każde wystąpienie dostawcy typu może `TypeProviderConfig` mieć wartość podczas budowy.</span><span class="sxs-lookup"><span data-stu-id="ed997-399">Each instance of a type provider can be given a `TypeProviderConfig` value during construction.</span></span> <span data-ttu-id="ed997-400">Ta wartość zawiera "folder rozpoznawania" dla dostawcy (czyli folderu projektu kompilacji lub katalogu zawierającego skrypt), listę zestawów, do których istnieją odwołania, i inne informacje.</span><span class="sxs-lookup"><span data-stu-id="ed997-400">This value contains the "resolution folder" for the provider (that is, the project folder for the compilation or the directory that contains a script), the list of referenced assemblies, and other information.</span></span>

### <a name="invalidation"></a><span data-ttu-id="ed997-401">Unieważnienie</span><span class="sxs-lookup"><span data-stu-id="ed997-401">Invalidation</span></span>

<span data-ttu-id="ed997-402">Dostawcy mogą zgłaszać sygnały unieważnienia, aby powiadomić usługę języka F#, że założenia schematu mogły ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="ed997-402">Providers can raise invalidation signals to notify the F# language service that the schema assumptions may have changed.</span></span> <span data-ttu-id="ed997-403">W przypadku wystąpienia unieważnienia sprawdzanie typu jest ponownie, jeśli dostawca jest obsługiwany w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ed997-403">When invalidation occurs, a typecheck is redone if the provider is being hosted in Visual Studio.</span></span> <span data-ttu-id="ed997-404">Ten sygnał zostanie zignorowany, gdy dostawca jest obsługiwany w języku F# Interactive lub przez kompilator F# (fsc.exe).</span><span class="sxs-lookup"><span data-stu-id="ed997-404">This signal will be ignored when the provider is hosted in F# Interactive or by the F# Compiler (fsc.exe).</span></span>

### <a name="caching-schema-information"></a><span data-ttu-id="ed997-405">Informacje o schemacie buforowania</span><span class="sxs-lookup"><span data-stu-id="ed997-405">Caching Schema Information</span></span>

<span data-ttu-id="ed997-406">Dostawcy muszą często buforować dostęp do informacji o schemacie.</span><span class="sxs-lookup"><span data-stu-id="ed997-406">Providers must often cache access to schema information.</span></span> <span data-ttu-id="ed997-407">Buforowane dane powinny być przechowywane przy użyciu nazwy pliku, który jest podany jako parametr statyczny lub jako dane użytkownika.</span><span class="sxs-lookup"><span data-stu-id="ed997-407">The cached data should be stored by using a file name that's given as a static parameter or as user data.</span></span> <span data-ttu-id="ed997-408">Przykładem buforowania schematu `LocalSchemaFile` jest parametr w dostawcach `FSharp.Data.TypeProviders` typów w zestawie.</span><span class="sxs-lookup"><span data-stu-id="ed997-408">An example of schema caching is the `LocalSchemaFile` parameter in the type providers in the `FSharp.Data.TypeProviders` assembly.</span></span> <span data-ttu-id="ed997-409">W implementacji tych dostawców ten parametr statyczny nakazuje dostawcy typów używać informacji o schemacie w określonym pliku lokalnym zamiast uzyskiwać dostęp do źródła danych za pośrednictwem sieci.</span><span class="sxs-lookup"><span data-stu-id="ed997-409">In the implementation of these providers, this static parameter directs the type provider to use the schema information in the specified local file instead of accessing the data source over the network.</span></span> <span data-ttu-id="ed997-410">Aby użyć buforowanych informacji o schemacie, `ForceUpdate` należy `false`również ustawić parametr statyczny na .</span><span class="sxs-lookup"><span data-stu-id="ed997-410">To use cached schema information, you must also set the static parameter `ForceUpdate` to `false`.</span></span> <span data-ttu-id="ed997-411">Można użyć podobnej techniki, aby włączyć dostęp do danych w trybie online i offline.</span><span class="sxs-lookup"><span data-stu-id="ed997-411">You could use a similar technique to enable online and offline data access.</span></span>

### <a name="backing-assembly"></a><span data-ttu-id="ed997-412">Montaż podkładowy</span><span class="sxs-lookup"><span data-stu-id="ed997-412">Backing Assembly</span></span>

<span data-ttu-id="ed997-413">Podczas kompilowania `.dll` `.exe` pliku lub pliku, kopii zapasowej pliku dll dla wygenerowanych typów jest statycznie połączone z wynikowego zestawu.</span><span class="sxs-lookup"><span data-stu-id="ed997-413">When you compile a `.dll` or `.exe` file, the backing .dll file for generated types is statically linked into the resulting assembly.</span></span> <span data-ttu-id="ed997-414">To łącze jest tworzone przez skopiowanie definicji typu języka pośredniego (IL) i wszelkich zarządzanych zasobów z zestawu zapasowego do zestawu końcowego.</span><span class="sxs-lookup"><span data-stu-id="ed997-414">This link is created by copying the Intermediate Language (IL) type definitions and any managed resources from the backing assembly into the final assembly.</span></span> <span data-ttu-id="ed997-415">Korzystając z języka F# Interactive, zapasowy plik dll nie jest kopiowany i zamiast tego jest ładowany bezpośrednio do procesu F# Interactive.</span><span class="sxs-lookup"><span data-stu-id="ed997-415">When you use F# Interactive, the backing .dll file isn't copied and is instead loaded directly into the F# Interactive process.</span></span>

### <a name="exceptions-and-diagnostics-from-type-providers"></a><span data-ttu-id="ed997-416">Wyjątki i diagnostyka od dostawców typów</span><span class="sxs-lookup"><span data-stu-id="ed997-416">Exceptions and Diagnostics from Type Providers</span></span>

<span data-ttu-id="ed997-417">Wszystkie zastosowania wszystkich elementów członkowskich z podanych typów mogą zgłaszać wyjątki.</span><span class="sxs-lookup"><span data-stu-id="ed997-417">All uses of all members from provided types may throw exceptions.</span></span> <span data-ttu-id="ed997-418">We wszystkich przypadkach, jeśli dostawca typu zgłasza wyjątek, kompilator hosta przypisuje ten błąd dostawcy określonego typu.</span><span class="sxs-lookup"><span data-stu-id="ed997-418">In all cases, if a type provider throws an exception, the host compiler attributes the error to a specific type provider.</span></span>

- <span data-ttu-id="ed997-419">Wyjątki dostawcy typu nigdy nie powinny powodować błędów kompilatora wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="ed997-419">Type provider exceptions should never result in internal compiler errors.</span></span>

- <span data-ttu-id="ed997-420">Dostawcy typów nie mogą zgłaszać ostrzeżeń.</span><span class="sxs-lookup"><span data-stu-id="ed997-420">Type providers can't report warnings.</span></span>

- <span data-ttu-id="ed997-421">Gdy dostawca typu jest hostowany w kompilatorze Języka F#, środowisku programistycznym F# lub F# Interactive, wszystkie wyjątki od tego dostawcy są przechwytywane.</span><span class="sxs-lookup"><span data-stu-id="ed997-421">When a type provider is hosted in the F# compiler, an F# development environment, or F# Interactive, all exceptions from that provider are caught.</span></span> <span data-ttu-id="ed997-422">Message Właściwość jest zawsze tekst błędu i nie ma śledzenia stosu.</span><span class="sxs-lookup"><span data-stu-id="ed997-422">The Message property is always the error text, and no stack trace appears.</span></span> <span data-ttu-id="ed997-423">Jeśli zamierzasz zgłosić wyjątek, możesz zgłosić następujące `System.NotSupportedException` `System.IO.IOException`przykłady: , , `System.Exception`.</span><span class="sxs-lookup"><span data-stu-id="ed997-423">If you’re going to throw an exception, you can throw the following examples: `System.NotSupportedException`, `System.IO.IOException`, `System.Exception`.</span></span>

#### <a name="providing-generated-types"></a><span data-ttu-id="ed997-424">Dostarczanie wygenerowanych typów</span><span class="sxs-lookup"><span data-stu-id="ed997-424">Providing Generated Types</span></span>

<span data-ttu-id="ed997-425">Do tej pory w tym dokumencie wyjaśniono, jak zapewnić usunięte typy.</span><span class="sxs-lookup"><span data-stu-id="ed997-425">So far, this document has explained how to provide erased types.</span></span> <span data-ttu-id="ed997-426">Można również użyć mechanizmu dostawcy typu w języku F#, aby zapewnić wygenerowane typy, które są dodawane jako rzeczywiste definicje typu .NET do programu użytkowników.</span><span class="sxs-lookup"><span data-stu-id="ed997-426">You can also use the type provider mechanism in F# to provide generated types, which are added as real .NET type definitions into the users' program.</span></span> <span data-ttu-id="ed997-427">Należy odwołać się do wygenerowanych typów dostarczonych przy użyciu definicji typu.</span><span class="sxs-lookup"><span data-stu-id="ed997-427">You must refer to generated provided types by using a type definition.</span></span>

```fsharp
open Microsoft.FSharp.TypeProviders

type Service = ODataService<"http://services.odata.org/Northwind/Northwind.svc/">
```

<span data-ttu-id="ed997-428">Kod pomocnika ProvidedTypes-0.2, który jest częścią wersji F# 3.0 ma ograniczoną obsługę dostarczania wygenerowanych typów.</span><span class="sxs-lookup"><span data-stu-id="ed997-428">The ProvidedTypes-0.2 helper code that is part of the F# 3.0 release has only limited support for providing generated types.</span></span> <span data-ttu-id="ed997-429">Następujące instrukcje muszą być prawdziwe dla wygenerowanej definicji typu:</span><span class="sxs-lookup"><span data-stu-id="ed997-429">The following statements must be true for a generated type definition:</span></span>

- <span data-ttu-id="ed997-430">`isErased`musi być `false`ustawiona na .</span><span class="sxs-lookup"><span data-stu-id="ed997-430">`isErased` must be set to `false`.</span></span>

- <span data-ttu-id="ed997-431">Wygenerowany typ musi zostać dodany `ProvidedAssembly()`do nowo skonstruowanego , który reprezentuje kontener dla wygenerowanych fragmentów kodu.</span><span class="sxs-lookup"><span data-stu-id="ed997-431">The generated type must be added to a newly constructed `ProvidedAssembly()`, which represents a container for generated code fragments.</span></span>

- <span data-ttu-id="ed997-432">Dostawca musi mieć zestaw, który ma rzeczywisty zapas pliku .NET .dll z pasującym plikiem dll na dysku.</span><span class="sxs-lookup"><span data-stu-id="ed997-432">The provider must have an assembly that has an actual backing .NET .dll file with a matching .dll file on disk.</span></span>

## <a name="rules-and-limitations"></a><span data-ttu-id="ed997-433">Zasady i ograniczenia</span><span class="sxs-lookup"><span data-stu-id="ed997-433">Rules and Limitations</span></span>

<span data-ttu-id="ed997-434">Podczas pisania dostawców typów należy pamiętać o następujących regułach i ograniczeniach.</span><span class="sxs-lookup"><span data-stu-id="ed997-434">When you write type providers, keep the following rules and limitations in mind.</span></span>

### <a name="provided-types-must-be-reachable"></a><span data-ttu-id="ed997-435">Pod warunkiem, że typy muszą być osiągalne</span><span class="sxs-lookup"><span data-stu-id="ed997-435">Provided types must be reachable</span></span>

<span data-ttu-id="ed997-436">Wszystkie podane typy powinny być dostępne z typów niezagnieżdżonych.</span><span class="sxs-lookup"><span data-stu-id="ed997-436">All provided types should be reachable from the non-nested types.</span></span> <span data-ttu-id="ed997-437">Typy niezagnieżdżone są podane `TypeProviderForNamespaces` w wywołaniu `AddNamespace`do konstruktora lub wywołaniu .</span><span class="sxs-lookup"><span data-stu-id="ed997-437">The non-nested types are given in the call to the `TypeProviderForNamespaces` constructor or a call to `AddNamespace`.</span></span> <span data-ttu-id="ed997-438">Na przykład jeśli dostawca udostępnia `StaticClass.P : T`typ, należy upewnić się, że T jest typem niezagnieżdżonego lub zagnieżdżone w jednym.</span><span class="sxs-lookup"><span data-stu-id="ed997-438">For example, if the provider provides a type `StaticClass.P : T`, you must ensure that T is either a non-nested type or nested under one.</span></span>

<span data-ttu-id="ed997-439">Na przykład niektórzy dostawcy mają klasę `DataTypes` statyczną, `T1, T2, T3, ...` taką jak te typy.</span><span class="sxs-lookup"><span data-stu-id="ed997-439">For example, some providers have a static class such as `DataTypes` that contain these `T1, T2, T3, ...` types.</span></span> <span data-ttu-id="ed997-440">W przeciwnym razie błąd mówi, że znaleziono odwołanie do typu T w zestawie A, ale nie można odnaleźć typu w tym zestawie.</span><span class="sxs-lookup"><span data-stu-id="ed997-440">Otherwise, the error says that a reference to type T in assembly A was found, but the type couldn't be found in that assembly.</span></span> <span data-ttu-id="ed997-441">Jeśli ten błąd zostanie wyświetlony, sprawdź, czy wszystkie podtypy można uzyskać z typów dostawców.</span><span class="sxs-lookup"><span data-stu-id="ed997-441">If this error appears, verify that all your subtypes can be reached from the provider types.</span></span> <span data-ttu-id="ed997-442">Uwaga: `T1, T2, T3...` Te typy są określane jako typy *w locie.*</span><span class="sxs-lookup"><span data-stu-id="ed997-442">Note: These `T1, T2, T3...` types are referred to as the *on-the-fly* types.</span></span> <span data-ttu-id="ed997-443">Pamiętaj, aby umieścić je w dostępnej przestrzeni nazw lub typu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="ed997-443">Remember to put them in an accessible namespace or a parent type.</span></span>

### <a name="limitations-of-the-type-provider-mechanism"></a><span data-ttu-id="ed997-444">Ograniczenia mechanizmu dostawcy typu</span><span class="sxs-lookup"><span data-stu-id="ed997-444">Limitations of the Type Provider Mechanism</span></span>

<span data-ttu-id="ed997-445">Mechanizm dostawcy typu w języku F# ma następujące ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="ed997-445">The type provider mechanism in F# has the following limitations:</span></span>

- <span data-ttu-id="ed997-446">Podstawowa infrastruktura dla dostawców typów w języku F# nie obsługuje pod warunkiem typy ogólne lub pod warunkiem metod ogólnych.</span><span class="sxs-lookup"><span data-stu-id="ed997-446">The underlying infrastructure for type providers in F# doesn't support provided generic types or provided generic methods.</span></span>

- <span data-ttu-id="ed997-447">Mechanizm nie obsługuje typów zagnieżdżonych z parametrami statycznymi.</span><span class="sxs-lookup"><span data-stu-id="ed997-447">The mechanism doesn't support nested types with static parameters.</span></span>

## <a name="development-tips"></a><span data-ttu-id="ed997-448">Porady dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="ed997-448">Development Tips</span></span>

<span data-ttu-id="ed997-449">Następujące wskazówki mogą okazać się pomocne podczas procesu tworzenia:</span><span class="sxs-lookup"><span data-stu-id="ed997-449">You might find the following tips helpful during the development process:</span></span>

### <a name="run-two-instances-of-visual-studio"></a><span data-ttu-id="ed997-450">Uruchamianie dwóch wystąpień programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ed997-450">Run two instances of Visual Studio</span></span>

<span data-ttu-id="ed997-451">Można opracować dostawcę typu w jednym wystąpieniu i przetestować dostawcę w innym, ponieważ ide testowy podejmie blokadę pliku .dll, która uniemożliwia przebudowę dostawcy typu.</span><span class="sxs-lookup"><span data-stu-id="ed997-451">You can develop the type provider in one instance and test the provider in the other because the test IDE will take a lock on the .dll file that prevents the type provider from being rebuilt.</span></span> <span data-ttu-id="ed997-452">W związku z tym należy zamknąć drugie wystąpienie programu Visual Studio, gdy dostawca jest zbudowany w pierwszej instancji, a następnie należy ponownie otworzyć drugie wystąpienie po zbudowaniu dostawcy.</span><span class="sxs-lookup"><span data-stu-id="ed997-452">Thus, you must close the second instance of Visual Studio while the provider is built in the first instance, and then you must reopen the second instance after the provider is built.</span></span>

### <a name="debug-type-providers-by-using-invocations-of-fscexe"></a><span data-ttu-id="ed997-453">Dostawców typów debugowania przy użyciu wywołań fsc.exe</span><span class="sxs-lookup"><span data-stu-id="ed997-453">Debug type providers by using invocations of fsc.exe</span></span>

<span data-ttu-id="ed997-454">Dostawców typów można wywoływać przy użyciu następujących narzędzi:</span><span class="sxs-lookup"><span data-stu-id="ed997-454">You can invoke type providers by using the following tools:</span></span>

- <span data-ttu-id="ed997-455">fsc.exe (kompilator wiersza polecenia F#)</span><span class="sxs-lookup"><span data-stu-id="ed997-455">fsc.exe (The F# command line compiler)</span></span>

- <span data-ttu-id="ed997-456">fsi.exe (Kompilator F# Interactive)</span><span class="sxs-lookup"><span data-stu-id="ed997-456">fsi.exe (The F# Interactive compiler)</span></span>

- <span data-ttu-id="ed997-457">devenv.exe (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="ed997-457">devenv.exe (Visual Studio)</span></span>

<span data-ttu-id="ed997-458">Często można debugować dostawców typów najłatwiej za pomocą fsc.exe na pliku skryptu testowego (na przykład script.fsx).</span><span class="sxs-lookup"><span data-stu-id="ed997-458">You can often debug type providers most easily by using fsc.exe on a test script file (for example, script.fsx).</span></span> <span data-ttu-id="ed997-459">Debugera można uruchomić z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="ed997-459">You can launch a debugger from a command prompt.</span></span>

```console
devenv /debugexe fsc.exe script.fsx
```

  <span data-ttu-id="ed997-460">Można użyć rejestrowania wydruku do stdout.</span><span class="sxs-lookup"><span data-stu-id="ed997-460">You can use print-to-stdout logging.</span></span>

## <a name="see-also"></a><span data-ttu-id="ed997-461">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ed997-461">See also</span></span>

- [<span data-ttu-id="ed997-462">Dostawcy typów</span><span class="sxs-lookup"><span data-stu-id="ed997-462">Type Providers</span></span>](index.md)
- [<span data-ttu-id="ed997-463">SDK dostawcy typu</span><span class="sxs-lookup"><span data-stu-id="ed997-463">The Type Provider SDK</span></span>](https://github.com/fsprojects/FSharp.TypeProviders.SDK)
