---
title: 'Samouczek: Tworzenie dostawcy typów (F #)'
description: 'Dowiedz się, jak utworzyć własne dostawcy typów F # w F # 3.0, sprawdzając wielu dostawców typu prostego w celu zilustrowania koncepcji podstawowe.'
keywords: 'Visual f #, f #, funkcjonalności programowania'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 82bec076-19d4-470c-979f-6c3a14b7c70a
ms.openlocfilehash: b2e83218184bd1aef8258378485b99697cc8cf8d
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="tutorial-create-a-type-provider"></a><span data-ttu-id="35f20-104">Samouczek: Tworzenie dostawcy typów</span><span class="sxs-lookup"><span data-stu-id="35f20-104">Tutorial: Create a Type Provider</span></span>

<span data-ttu-id="35f20-105">Mechanizm dostawcy typów F # jest znaczną część jego obsługę programowania zaawansowanych informacji.</span><span class="sxs-lookup"><span data-stu-id="35f20-105">The type provider mechanism in F# is a significant part of its support for information rich programming.</span></span> <span data-ttu-id="35f20-106">Ten samouczek wyjaśnia sposób tworzenia własnych dostawców typu przez Instruktaż rozwoju wielu dostawców typu prostego w celu zilustrowania koncepcji podstawowe.</span><span class="sxs-lookup"><span data-stu-id="35f20-106">This tutorial explains how to create your own type providers by walking you through the development of several simple type providers to illustrate the basic concepts.</span></span> <span data-ttu-id="35f20-107">Aby uzyskać więcej informacji na temat mechanizm dostawcy typów F #, zobacz [dostawców typów](index.md).</span><span class="sxs-lookup"><span data-stu-id="35f20-107">For more information about the type provider mechanism in F#, see [Type Providers](index.md).</span></span>

<span data-ttu-id="35f20-108">Ekosystem F # zawiera szereg dostawców typów dla często używanych usług danych Internet i enterprise.</span><span class="sxs-lookup"><span data-stu-id="35f20-108">The F# ecosystem contains a range of type providers for commonly used Internet and enterprise data services.</span></span> <span data-ttu-id="35f20-109">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="35f20-109">For example:</span></span>

- <span data-ttu-id="35f20-110">[FSharp.Data](https://fsharp.github.io/FSharp.Data/) zawiera dostawców typów JSON, XML, CSV i HTML dokumentów formatów.</span><span class="sxs-lookup"><span data-stu-id="35f20-110">[FSharp.Data](https://fsharp.github.io/FSharp.Data/) includes type providers for JSON, XML, CSV and HTML document formats.</span></span>

- <span data-ttu-id="35f20-111">[SQLProvider](https://fsprojects.github.io/SQLProvider/) udostępnia silnie typizowane dostęp do bazy danych SQL za pomocą mapowania obiektu i F # LINQ zapytań dotyczących tych źródeł danych.</span><span class="sxs-lookup"><span data-stu-id="35f20-111">[SQLProvider](https://fsprojects.github.io/SQLProvider/) provides strongly-typed access to SQL databases through a object mapping and F# LINQ queries against these data sources.</span></span>

- <span data-ttu-id="35f20-112">[FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) zestaw dostawców typów dla kompilacji sprawdził osadzania T-SQL w języku F #.</span><span class="sxs-lookup"><span data-stu-id="35f20-112">[FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) has a set of type providers for compile-time checked embedding of T-SQL in F#.</span></span>

- <span data-ttu-id="35f20-113">[FSharp.Data.TypeProviders](https://fsprojects.github.io/FSharp.Data.TypeProviders/) jest starsza zbiór typ dostawcy do użycia tylko w przypadku programowania .NET Framework do uzyskiwania dostępu do usług danych SQL, Entity Framework, OData i WSDL.</span><span class="sxs-lookup"><span data-stu-id="35f20-113">[FSharp.Data.TypeProviders](https://fsprojects.github.io/FSharp.Data.TypeProviders/) is an older set of type providers for use only with .NET Framework programming for accessing SQL, Entity Framework, OData and WSDL data services.</span></span>

<span data-ttu-id="35f20-114">W przypadku, gdy to konieczne, można utworzyć typu niestandardowego dostawcy, lub możesz odwoływać się do dostawców typów, utworzonych przez innych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="35f20-114">Where necessary, you can create custom type providers, or you can reference type providers that others have created.</span></span> <span data-ttu-id="35f20-115">Na przykład organizacja może mieć usłudze danych, która udostępnia duży i rosnącym wiele nazwanych zestawów danych, każdy ze schematem stabilna danych.</span><span class="sxs-lookup"><span data-stu-id="35f20-115">For example, your organization could have a data service that provides a large and growing number of named data sets, each with its own stable data schema.</span></span> <span data-ttu-id="35f20-116">Można utworzyć dostawcy typów odczytujący schematów i przedstawia bieżący zestawów danych dla programisty w jednoznaczny sposób.</span><span class="sxs-lookup"><span data-stu-id="35f20-116">You can create a type provider that reads the schemas and presents the current data sets to the programmer in a strongly typed way.</span></span>


## <a name="before-you-start"></a><span data-ttu-id="35f20-117">Przed rozpoczęciem</span><span class="sxs-lookup"><span data-stu-id="35f20-117">Before You Start</span></span>

<span data-ttu-id="35f20-118">Typ mechanizmu dostawcy jest przeznaczony głównie do wstrzykiwania stabilna danych i informacji użytkowych do środowiska programowania w języku F #.</span><span class="sxs-lookup"><span data-stu-id="35f20-118">The type provider mechanism is primarily designed for injecting stable data and service information spaces into the F# programming experience.</span></span>

<span data-ttu-id="35f20-119">Ten mechanizm nie jest przeznaczona dla wstrzyknięcie spacje informacje o zmianie którego schematu podczas wykonywania programu w sposób, w którym mają zastosowanie w logice programu.</span><span class="sxs-lookup"><span data-stu-id="35f20-119">This mechanism isn’t designed for injecting information spaces whose schema changes during program execution in ways that are relevant to program logic.</span></span> <span data-ttu-id="35f20-120">Ponadto mechanizm nie jest przeznaczona dla meta-programowania wewnątrz języka nawet tej domeny zawiera niektóre prawidłowego użycia.</span><span class="sxs-lookup"><span data-stu-id="35f20-120">Also, the mechanism isn't designed for intra-language meta-programming, even though that domain contains some valid uses.</span></span> <span data-ttu-id="35f20-121">Ten mechanizm należy używać tylko w razie potrzeby i gdzie tworzenie dostawcy typów zwraca bardzo wysokiej wartości.</span><span class="sxs-lookup"><span data-stu-id="35f20-121">You should use this mechanism only where necessary and where the development of a type provider yields very high value.</span></span>

<span data-ttu-id="35f20-122">Należy unikać pisania typ dostawcy, gdzie schemat jest niedostępna.</span><span class="sxs-lookup"><span data-stu-id="35f20-122">You should avoid writing a type provider where a schema isn't available.</span></span> <span data-ttu-id="35f20-123">Podobnie, należy unikać pisania dostawcy typów w przypadku, gdy zwykłych (lub nawet istniejące) biblioteki .NET będą wystarczające.</span><span class="sxs-lookup"><span data-stu-id="35f20-123">Likewise, you should avoid writing a type provider where an ordinary (or even an existing) .NET library would suffice.</span></span>

<span data-ttu-id="35f20-124">Przed rozpoczęciem, użytkownik może na następujące pytania:</span><span class="sxs-lookup"><span data-stu-id="35f20-124">Before you start, you might ask the following questions:</span></span>

- <span data-ttu-id="35f20-125">Czy masz schematu źródła informacji?</span><span class="sxs-lookup"><span data-stu-id="35f20-125">Do you have a schema for your information source?</span></span> <span data-ttu-id="35f20-126">Jeśli tak, co to jest mapowanie w F # i system typów .NET?</span><span class="sxs-lookup"><span data-stu-id="35f20-126">If so, what’s the mapping into the F# and .NET type system?</span></span>

- <span data-ttu-id="35f20-127">Można użyć istniejącego interfejsu API (typach określanych dynamicznie) jako punkt początkowy implementacji?</span><span class="sxs-lookup"><span data-stu-id="35f20-127">Can you use an existing (dynamically typed) API as a starting point for your implementation?</span></span>

- <span data-ttu-id="35f20-128">I całych organizacji ma za mało używa dostawcy typów, aby jej pisania zastanowić?</span><span class="sxs-lookup"><span data-stu-id="35f20-128">Will you and your organization have enough uses of the type provider to make writing it worthwhile?</span></span> <span data-ttu-id="35f20-129">Czy normalne biblioteki .NET potrzeb?</span><span class="sxs-lookup"><span data-stu-id="35f20-129">Would a normal .NET library meet your needs?</span></span>

- <span data-ttu-id="35f20-130">Ile zmieni schemat?</span><span class="sxs-lookup"><span data-stu-id="35f20-130">How much will your schema change?</span></span>

- <span data-ttu-id="35f20-131">Zostanie ona zmieniona podczas kodowania?</span><span class="sxs-lookup"><span data-stu-id="35f20-131">Will it change during coding?</span></span>

- <span data-ttu-id="35f20-132">Będzie on zmienić między kodowania sesji?</span><span class="sxs-lookup"><span data-stu-id="35f20-132">Will it change between coding sessions?</span></span>

- <span data-ttu-id="35f20-133">Zostanie ona zmieniona podczas wykonywania programu?</span><span class="sxs-lookup"><span data-stu-id="35f20-133">Will it change during program execution?</span></span>

<span data-ttu-id="35f20-134">Typ dostawcy są najlepiej sprawdza się w sytuacjach, gdy schemat jest stabilna w czasie wykonywania, a okres istnienia skompilowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="35f20-134">Type providers are best suited to situations where the schema is stable at runtime and during the lifetime of compiled code.</span></span>


## <a name="a-simple-type-provider"></a><span data-ttu-id="35f20-135">Dostawca typu prostego</span><span class="sxs-lookup"><span data-stu-id="35f20-135">A Simple Type Provider</span></span>

<span data-ttu-id="35f20-136">Ten przykład jest Samples.HelloWorldTypeProvider, podobnie jak próbek w `examples` katalog [SDK dostawcy typów F #](https://github.com/fsprojects/FSharp.TypeProviders.SDK/).</span><span class="sxs-lookup"><span data-stu-id="35f20-136">This sample is Samples.HelloWorldTypeProvider, similar to the samples in the `examples` directory of the [F# Type Provider SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK/).</span></span> <span data-ttu-id="35f20-137">Dostawca udostępnia "przestrzeń typu", która zawiera 100 typy wymazywania, jak przedstawiono na poniższym kodem przy użyciu składni podpisu F #, a pomijając szczegóły dla wszystkich oprócz `Type1`.</span><span class="sxs-lookup"><span data-stu-id="35f20-137">The provider makes available a "type space" that contains 100 erased types, as the following code shows by using F# signature syntax and omitting the details for all except `Type1`.</span></span> <span data-ttu-id="35f20-138">Aby uzyskać więcej informacji dotyczących skasowany typów, zobacz [szczegółowe informacje o wymazane podane typy](#details-about-erased-provided-types) dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="35f20-138">For more information about erased types, see [Details About Erased Provided Types](#details-about-erased-provided-types) later in this topic.</span></span>

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

    /// This is an instance property.
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

<span data-ttu-id="35f20-139">Należy zwrócić uwagę, czy zestaw typów i członków podane statycznie jest znany.</span><span class="sxs-lookup"><span data-stu-id="35f20-139">Note that the set of types and members provided is statically known.</span></span> <span data-ttu-id="35f20-140">W tym przykładzie nie korzystać z możliwości dostawców typów, które są zależne od schematu.</span><span class="sxs-lookup"><span data-stu-id="35f20-140">This example doesn't leverage the ability of providers to provide types that depend on a schema.</span></span> <span data-ttu-id="35f20-141">Implementacja dostawcy typów przedstawiono w poniższym kodzie i szczegóły są przedstawione w kolejnych sekcjach tego tematu.</span><span class="sxs-lookup"><span data-stu-id="35f20-141">The implementation of the type provider is outlined in the following code, and the details are covered in later sections of this topic.</span></span>


>[!WARNING] 
<span data-ttu-id="35f20-142">Może to być różnice między ten kod i przykłady online.</span><span class="sxs-lookup"><span data-stu-id="35f20-142">There may be differences between this code and the online samples.</span></span>

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

<span data-ttu-id="35f20-143">Aby użyć tego dostawcy, otwórz osobnego wystąpienia programu Visual Studio, utworzyć skrypt F #, a następnie dodaj odwołanie do dostawcy ze skryptu za pomocą #r, jak przedstawiono na poniższym kodem:</span><span class="sxs-lookup"><span data-stu-id="35f20-143">To use this provider, open a separate instance of Visual Studio, create an F# script, and then add a reference to the provider from your script by using #r as the following code shows:</span></span>

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

<span data-ttu-id="35f20-144">Poszukaj typów w obszarze `Samples.HelloWorldTypeProvider` przestrzeni nazw, która wygenerowany typ dostawcy.</span><span class="sxs-lookup"><span data-stu-id="35f20-144">Then look for the types under the `Samples.HelloWorldTypeProvider` namespace that the type provider generated.</span></span>

<span data-ttu-id="35f20-145">Przed skompiluj dostawcy, upewnij się, że zamknięciu wszystkich wystąpień programu Visual Studio i F # Interactive, korzystających z biblioteki DLL dostawcy.</span><span class="sxs-lookup"><span data-stu-id="35f20-145">Before you recompile the provider, make sure that you have closed all instances of Visual Studio and F# Interactive that are using the provider DLL.</span></span> <span data-ttu-id="35f20-146">W przeciwnym razie błąd kompilacji nastąpi, ponieważ dane wyjściowe biblioteki DLL zostanie zablokowane.</span><span class="sxs-lookup"><span data-stu-id="35f20-146">Otherwise, a build error will occur because the output DLL will be locked.</span></span>

<span data-ttu-id="35f20-147">Do debugowania tego dostawcę przy użyciu instrukcji drukowania, wprowadź skrypt, który opisuje problem z dostawcą, a następnie użyć poniższego kodu:</span><span class="sxs-lookup"><span data-stu-id="35f20-147">To debug this provider by using print statements, make a script that exposes a problem with the provider, and then use the following code:</span></span>

```fsharp
fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

<span data-ttu-id="35f20-148">Aby debugować ten dostawca przy użyciu programu Visual Studio, otwórz wiersz polecenia programu Visual Studio przy użyciu poświadczeń administracyjnych, a następnie uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="35f20-148">To debug this provider by using Visual Studio, open the Visual Studio command prompt with administrative credentials, and run the following command:</span></span>

```fsharp
devenv.exe /debugexe fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

<span data-ttu-id="35f20-149">Alternatywnie, Otwórz program Visual Studio, otwórz menu debugowanie, wybierz pozycję `Debug/Attach to process…`i Dołącz do innego `devenv` proces, w którym edycji skryptu.</span><span class="sxs-lookup"><span data-stu-id="35f20-149">As an alternative, open Visual Studio, open the Debug menu, choose `Debug/Attach to process…`, and attach to another `devenv` process where you’re editing your script.</span></span> <span data-ttu-id="35f20-150">Za pomocą tej metody, można łatwiej kierować konkretnej logiki w dostawcy typów interaktywnie wpisując wyrażenia do drugiego wystąpienia (z pełną IntelliSense i inne funkcje).</span><span class="sxs-lookup"><span data-stu-id="35f20-150">By using this method, you can more easily target particular logic in the type provider by interactively typing expressions into the second instance (with full IntelliSense and other features).</span></span>

<span data-ttu-id="35f20-151">Można wyłączyć opcję tylko mój kod debugowanie, aby łatwiej odróżnić błędy w wygenerowanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="35f20-151">You can disable Just My Code debugging to better identify errors in generated code.</span></span> <span data-ttu-id="35f20-152">Aby dowiedzieć się, jak włączyć lub wyłączyć tę funkcję, zobacz [nawigowanie po kodzie za pomocą debugera](/visualstudio/debugger/navigating-through-code-with-the-debugger).</span><span class="sxs-lookup"><span data-stu-id="35f20-152">For information about how to enable or disable this feature, see [Navigating through Code with the Debugger](/visualstudio/debugger/navigating-through-code-with-the-debugger).</span></span> <span data-ttu-id="35f20-153">Ponadto można również ustawić wyjątkach pierwszej szansy Przechwytywanie otwierając `Debug` menu, a następnie wybierając `Exceptions` lub wybierając klawisze Ctrl + Alt + E, aby otworzyć `Exceptions` okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="35f20-153">Also, you can also set first-chance exception catching by opening the `Debug` menu and then choosing `Exceptions` or by choosing the Ctrl+Alt+E keys to open the `Exceptions` dialog box.</span></span> <span data-ttu-id="35f20-154">W tym oknie dialogowym w obszarze `Common Language Runtime Exceptions`, wybierz pozycję `Thrown` pole wyboru.</span><span class="sxs-lookup"><span data-stu-id="35f20-154">In that dialog box, under `Common Language Runtime Exceptions`, select the `Thrown` check box.</span></span>


### <a name="implementation-of-the-type-provider"></a><span data-ttu-id="35f20-155">Implementacja dostawcy typów</span><span class="sxs-lookup"><span data-stu-id="35f20-155">Implementation of the Type Provider</span></span>

<span data-ttu-id="35f20-156">W tej sekcji przedstawiono główne części typ implementacji dostawcy.</span><span class="sxs-lookup"><span data-stu-id="35f20-156">This section walks you through the principal sections of the type provider implementation.</span></span> <span data-ttu-id="35f20-157">Najpierw należy zdefiniować typu dla samej siebie dostawcy niestandardowego typu:</span><span class="sxs-lookup"><span data-stu-id="35f20-157">First, you define the type for the custom type provider itself:</span></span>

```fsharp
[<TypeProvider>]
type SampleTypeProvider(config: TypeProviderConfig) as this =
```

<span data-ttu-id="35f20-158">Ten typ musi być publiczny i należy oznaczyć go przy użyciu [TypeProvider](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947) atrybutu, aby kompilator rozpoznawał typ dostawcy, gdy oddzielny projekt F # odwołuje się do zestawu zawierającego typ.</span><span class="sxs-lookup"><span data-stu-id="35f20-158">This type must be public, and you must mark it with the [TypeProvider](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947) attribute so that the compiler will recognize the type provider when a separate F# project references the assembly that contains the type.</span></span> <span data-ttu-id="35f20-159">*Config* parametr jest opcjonalny i, jeśli jest obecny, zawiera informacje o konfiguracji kontekstowych dla wystąpienia dostawcy typu, który tworzy kompilator języka F #.</span><span class="sxs-lookup"><span data-stu-id="35f20-159">The *config* parameter is optional, and, if present, contains contextual configuration information for the type provider instance that the F# compiler creates.</span></span>

<span data-ttu-id="35f20-160">Następnie należy zaimplementować [itypeprovider —](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="35f20-160">Next, you implement the [ITypeProvider](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f) interface.</span></span> <span data-ttu-id="35f20-161">W takim przypadku należy użyć `TypeProviderForNamespaces` typu z `ProvidedTypes` interfejsu API jako typu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="35f20-161">In this case, you use the `TypeProviderForNamespaces` type from the `ProvidedTypes` API as a base type.</span></span> <span data-ttu-id="35f20-162">Ten typ pomocnika zapewniają skończoną kolekcję dzielenia na pod warunkiem przestrzeni nazw, z których każdy bezpośrednio zawiera skończoną liczbę stałej, dzielenia na podane typy.</span><span class="sxs-lookup"><span data-stu-id="35f20-162">This helper type can provide a finite collection of eagerly provided namespaces, each of which directly contains a finite number of fixed, eagerly provided types.</span></span> <span data-ttu-id="35f20-163">W tym kontekście, dostawca *dzielenia na* generuje typów, nawet jeśli nie są one potrzebne lub używane.</span><span class="sxs-lookup"><span data-stu-id="35f20-163">In this context, the provider *eagerly* generates types even if they aren't needed or used.</span></span>

```fsharp
inherit TypeProviderForNamespaces(config)
```

<span data-ttu-id="35f20-164">Następnie zdefiniuj lokalnego wartości prywatne, które określają przestrzeń nazw dla udostępnionych typów i Znajdź zestawu typu dostawcy.</span><span class="sxs-lookup"><span data-stu-id="35f20-164">Next, define local private values that specify the namespace for the provided types, and find the type provider assembly itself.</span></span> <span data-ttu-id="35f20-165">Ten zestaw jest później używany jako typ logiczny obiekt nadrzędny wymazanej typów, które są udostępniane.</span><span class="sxs-lookup"><span data-stu-id="35f20-165">This assembly is used later as the logical parent type of the erased types that are provided.</span></span>

```fsharp
let namespaceName = "Samples.HelloWorldTypeProvider"
let thisAssembly = Assembly.GetExecutingAssembly()
```

<span data-ttu-id="35f20-166">Następnie należy utworzyć funkcji poszczególnych typów Type1... Type100.</span><span class="sxs-lookup"><span data-stu-id="35f20-166">Next, create a function to provide each of the types Type1…Type100.</span></span> <span data-ttu-id="35f20-167">Ta funkcja jest szczegółowo w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="35f20-167">This function is explained in more detail later in this topic.</span></span>

```fsharp
let makeOneProvidedType (n:int) = …
```

<span data-ttu-id="35f20-168">Następnie można wygenerować 100 podane typy:</span><span class="sxs-lookup"><span data-stu-id="35f20-168">Next, generate the 100 provided types:</span></span>

```fsharp
let types = [ for i in 1 .. 100 -> makeOneProvidedType i ]
```

<span data-ttu-id="35f20-169">Następnie dodaj typy w postaci podanego obszaru nazw:</span><span class="sxs-lookup"><span data-stu-id="35f20-169">Next, add the types as a provided namespace:</span></span>

```fsharp
do this.AddNamespace(namespaceName, types)
```

<span data-ttu-id="35f20-170">Na koniec należy dodać atrybut zestawu, który wskazuje tworzenia biblioteki DLL dostawcy typów:</span><span class="sxs-lookup"><span data-stu-id="35f20-170">Finally, add an assembly attribute that indicates that you are creating a type provider DLL:</span></span>

```fsharp
[<assembly:TypeProviderAssembly>] 
do()
```

### <a name="providing-one-type-and-its-members"></a><span data-ttu-id="35f20-171">Jeden typ i jej elementów członkowskich</span><span class="sxs-lookup"><span data-stu-id="35f20-171">Providing One Type And Its Members</span></span>

<span data-ttu-id="35f20-172">`makeOneProvidedType` Funkcja wykonuje rzeczywistą pracę udostępniania jednego z typów.</span><span class="sxs-lookup"><span data-stu-id="35f20-172">The `makeOneProvidedType` function does the real work of providing one of the types.</span></span>

```fsharp
let makeOneProvidedType (n:int) = 
…
```

<span data-ttu-id="35f20-173">W tym kroku opisano stosowania tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="35f20-173">This step explains the implementation of this function.</span></span> <span data-ttu-id="35f20-174">Najpierw utwórz udostępnionego typu (na przykład Type1, gdy n = 1 lub Type57, gdy n = 57).</span><span class="sxs-lookup"><span data-stu-id="35f20-174">First, create the provided type (for example, Type1, when n = 1, or Type57, when n = 57).</span></span>

```fsharp
// This is the provided type. It is an erased provided type and, in compiled code, 
// will appear as type 'obj'.
let t = ProvidedTypeDefinition(thisAssembly, namespaceName,
                               "Type" + string n,
                               baseType = Some typeof<obj>)
```

<span data-ttu-id="35f20-175">Należy zwrócić uwagę następujące kwestie:</span><span class="sxs-lookup"><span data-stu-id="35f20-175">You should note the following points:</span></span>

- <span data-ttu-id="35f20-176">To pod warunkiem, że typ jest usunięte.</span><span class="sxs-lookup"><span data-stu-id="35f20-176">This provided type is erased.</span></span>  <span data-ttu-id="35f20-177">Ponieważ wskazują, że typ podstawowy jest `obj`, wystąpień będą wyświetlane jako wartości typu [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) w skompilowany kod.</span><span class="sxs-lookup"><span data-stu-id="35f20-177">Because you indicate that the base type is `obj`, instances will appear as values of type [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) in compiled code.</span></span>

- <span data-ttu-id="35f20-178">Po określeniu typu niezagnieżdżonego, należy określić zestaw i przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="35f20-178">When you specify a non-nested type, you must specify the assembly and namespace.</span></span> <span data-ttu-id="35f20-179">Dla typów wymazanej zestawu powinna być zestawu typu dostawcy.</span><span class="sxs-lookup"><span data-stu-id="35f20-179">For erased types, the assembly should be the type provider assembly itself.</span></span>

<span data-ttu-id="35f20-180">Następnie dodaj plik dokumentacji XML do typu.</span><span class="sxs-lookup"><span data-stu-id="35f20-180">Next, add XML documentation to the type.</span></span> <span data-ttu-id="35f20-181">W tej dokumentacji jest opóźnione, oznacza to, obliczane na żądanie, jeśli kompilator hosta musi on.</span><span class="sxs-lookup"><span data-stu-id="35f20-181">This documentation is delayed, that is, computed on-demand if the host compiler needs it.</span></span>

```fsharp
t.AddXmlDocDelayed (fun () -> sprintf "This provided type %s" ("Type" + string n))
```

<span data-ttu-id="35f20-182">Następnie dodaj Podana właściwość statyczna do typu:</span><span class="sxs-lookup"><span data-stu-id="35f20-182">Next you add a provided static property to the type:</span></span>

```fsharp
let staticProp = ProvidedProperty(propertyName = "StaticProperty", 
                                  propertyType = typeof<string>, 
                                  isStatic = true,
                                  getterCode = (fun args -> <@@ "Hello!" @@>))
```

<span data-ttu-id="35f20-183">Pobieranie ta właściwość zawsze da się ciąg "Hello!".</span><span class="sxs-lookup"><span data-stu-id="35f20-183">Getting this property will always evaluate to the string "Hello!".</span></span> <span data-ttu-id="35f20-184">`GetterCode` Dla właściwości używa F # oferty, który reprezentuje kod, który generuje kompilatora hosta dla pobierania właściwości.</span><span class="sxs-lookup"><span data-stu-id="35f20-184">The `GetterCode` for the property uses an F# quotation, which represents the code that the host compiler generates for getting the property.</span></span> <span data-ttu-id="35f20-185">Aby uzyskać więcej informacji o ofertach, zobacz [cytaty kodu (F #)](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155).</span><span class="sxs-lookup"><span data-stu-id="35f20-185">For more information about quotations, see [Code Quotations (F#)](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155).</span></span>

<span data-ttu-id="35f20-186">Dodaj plik dokumentacji XML dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="35f20-186">Add XML documentation to the property.</span></span>

```fsharp
staticProp.AddXmlDocDelayed(fun () -> "This is a static property")
```

<span data-ttu-id="35f20-187">Teraz należy dołączyć podane właściwości do podanego typu.</span><span class="sxs-lookup"><span data-stu-id="35f20-187">Now attach the provided property to the provided type.</span></span> <span data-ttu-id="35f20-188">Należy dołączyć jeden i tylko jeden typ podanego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="35f20-188">You must attach a provided member to one and only one type.</span></span> <span data-ttu-id="35f20-189">W przeciwnym razie element członkowski nigdy nie będzie dostępny.</span><span class="sxs-lookup"><span data-stu-id="35f20-189">Otherwise, the member will never be accessible.</span></span>

```fsharp
t.AddMember staticProp
```

<span data-ttu-id="35f20-190">Utwórz podanych konstruktora, który nie przyjmuje żadnych parametrów.</span><span class="sxs-lookup"><span data-stu-id="35f20-190">Now create a provided constructor that takes no parameters.</span></span>

```fsharp
let ctor = ProvidedConstructor(parameters = [ ], 
                               invokeCode = (fun args -> <@@ "The object data" :> obj @@>))
```

<span data-ttu-id="35f20-191">`InvokeCode` Dla konstruktora zwraca F # oferty, który reprezentuje kod, który generuje kompilatora hosta podczas wywołania konstruktora.</span><span class="sxs-lookup"><span data-stu-id="35f20-191">The `InvokeCode` for the constructor returns an F# quotation, which represents the code that the host compiler generates when the constructor is called.</span></span> <span data-ttu-id="35f20-192">Można na przykład użyć konstruktora następujące:</span><span class="sxs-lookup"><span data-stu-id="35f20-192">For example, you can use the following constructor:</span></span>

```fsharp
new Type10()
```

<span data-ttu-id="35f20-193">Wystąpienie podanego typu zostanie utworzony z danymi źródłowymi "Dane obiektu".</span><span class="sxs-lookup"><span data-stu-id="35f20-193">An instance of the provided type will be created with underlying data "The object data".</span></span> <span data-ttu-id="35f20-194">Kod ujętego w cudzysłów zawiera konwersji do [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) ponieważ tego typu jest skasowanie to udostępniony typ (jak określono podczas zadeklarowany udostępnionego typu).</span><span class="sxs-lookup"><span data-stu-id="35f20-194">The quoted code includes a conversion to [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) because that type is the erasure of this provided type (as you specified when you declared the provided type).</span></span>

<span data-ttu-id="35f20-195">Dodaj plik dokumentacji XML do konstruktora i Dodaj dostarczonego konstruktora do udostępnionego typu:</span><span class="sxs-lookup"><span data-stu-id="35f20-195">Add XML documentation to the constructor, and add the provided constructor to the provided type:</span></span>

```fsharp
ctor.AddXmlDocDelayed(fun () -> "This is a constructor")

t.AddMember ctor
```

<span data-ttu-id="35f20-196">Utwórz drugi Konstruktor udostępnionego, który przyjmuje jeden parametr:</span><span class="sxs-lookup"><span data-stu-id="35f20-196">Create a second provided constructor that takes one parameter:</span></span>

```fsharp
let ctor2 = 
ProvidedConstructor(parameters = [ ProvidedParameter("data",typeof<string>) ], 
                    invokeCode = (fun args -> <@@ (%%(args.[0]) : string) :> obj @@>))
```

<span data-ttu-id="35f20-197">`InvokeCode` Dla konstruktora ponownie zwraca F # oferty, który reprezentuje kod wygenerowany przez kompilator hosta dla wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="35f20-197">The `InvokeCode` for the constructor again returns an F# quotation, which represents the code that the host compiler generated for a call to the method.</span></span> <span data-ttu-id="35f20-198">Można na przykład użyć konstruktora następujące:</span><span class="sxs-lookup"><span data-stu-id="35f20-198">For example, you can use the following constructor:</span></span>

```fsharp
new Type10("ten")
```

<span data-ttu-id="35f20-199">Z danymi źródłowymi "10" jest tworzone wystąpienie podanego typu.</span><span class="sxs-lookup"><span data-stu-id="35f20-199">An instance of the provided type is created with underlying data "ten".</span></span> <span data-ttu-id="35f20-200">Można już zauważyć, że `InvokeCode` funkcja zwraca oferty.</span><span class="sxs-lookup"><span data-stu-id="35f20-200">You may have already noticed that the `InvokeCode` function returns a quotation.</span></span> <span data-ttu-id="35f20-201">Dane wejściowe do funkcji znajduje się lista wyrażeń, po jednym dla każdego parametru konstruktora.</span><span class="sxs-lookup"><span data-stu-id="35f20-201">The input to this function is a list of expressions, one per constructor parameter.</span></span> <span data-ttu-id="35f20-202">W takim przypadku wyrażenie, które odpowiada wartości jeden parametr jest dostępna w `args.[0]`.</span><span class="sxs-lookup"><span data-stu-id="35f20-202">In this case, an expression that represents the single parameter value is available in `args.[0]`.</span></span> <span data-ttu-id="35f20-203">Kod dla wywołania konstruktora przekształca wynik dane wartości zwracanej typu wymazanej `obj`.</span><span class="sxs-lookup"><span data-stu-id="35f20-203">The code for a call to the constructor coerces the return value to the erased type `obj`.</span></span> <span data-ttu-id="35f20-204">Po dodaniu drugiego dostarczonego konstruktora do typu, możesz utworzyć właściwość udostępnionego wystąpienia:</span><span class="sxs-lookup"><span data-stu-id="35f20-204">After you add the second provided constructor to the type, you create a provided instance property:</span></span>

```fsharp
let instanceProp = 
    ProvidedProperty(propertyName = "InstanceProperty", 
                     propertyType = typeof<int>, 
                     getterCode= (fun args -> 
                        <@@ ((%%(args.[0]) : obj) :?> string).Length @@>))
instanceProp.AddXmlDocDelayed(fun () -> "This is an instance property")
t.AddMember instanceProp
```

<span data-ttu-id="35f20-205">Pobieranie tej właściwości będzie zwracać długość ciągu, który jest obiektem reprezentacji.</span><span class="sxs-lookup"><span data-stu-id="35f20-205">Getting this property will return the length of the string, which is the representation object.</span></span> <span data-ttu-id="35f20-206">`GetterCode` Właściwość zwraca oferty F #, który określa kod, który generuje kompilatora hosta do pobrania właściwości.</span><span class="sxs-lookup"><span data-stu-id="35f20-206">The `GetterCode` property returns an F# quotation that specifies the code that the host compiler generates to get the property.</span></span> <span data-ttu-id="35f20-207">Podobnie jak `InvokeCode`, `GetterCode` funkcja zwraca oferty.</span><span class="sxs-lookup"><span data-stu-id="35f20-207">Like `InvokeCode`, the `GetterCode` function returns a quotation.</span></span> <span data-ttu-id="35f20-208">Kompilator hosta wywołuje tę funkcję z listy argumentów.</span><span class="sxs-lookup"><span data-stu-id="35f20-208">The host compiler calls this function with a list of arguments.</span></span> <span data-ttu-id="35f20-209">W takim przypadku argumenty zawierają tylko pojedyncze wyrażenie reprezentuje wystąpienie, na którym jest wywoływana metoda pobierająca, mogą korzystać za pomocą `args.[0]`. Implementacja `GetterCode` następnie splices do oferty wyników na typ wymazywania `obj`, i rzutowanie jest używana do zaspokojenia mechanizm przez kompilator do sprawdzania typów, że obiekt jest ciągiem.</span><span class="sxs-lookup"><span data-stu-id="35f20-209">In this case, the arguments include just the single expression that represents the instance upon which the getter is being called, which you can access by using `args.[0]`.The implementation of `GetterCode` then splices into the result quotation at the erased type `obj`, and a cast is used to satisfy the compiler's mechanism for checking types that the object is a string.</span></span> <span data-ttu-id="35f20-210">Następna część `makeOneProvidedType` udostępnia metodę wystąpienia z jednym parametrem.</span><span class="sxs-lookup"><span data-stu-id="35f20-210">The next part of `makeOneProvidedType` provides an instance method with one parameter.</span></span>

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

<span data-ttu-id="35f20-211">Na koniec Utwórz typu zagnieżdżonego, która zawiera 100 właściwości zagnieżdżonych.</span><span class="sxs-lookup"><span data-stu-id="35f20-211">Finally, create a nested type that contains 100 nested properties.</span></span> <span data-ttu-id="35f20-212">Tworzenie to zagnieżdżony typ i jego właściwości jest opóźnione, oznacza to, obliczone na żądanie.</span><span class="sxs-lookup"><span data-stu-id="35f20-212">The creation of this nested type and its properties is delayed, that is, computed on-demand.</span></span>

```fsharp
t.AddMembersDelayed(fun () -> 
  let nestedType = ProvidedTypeDefinition("NestedType", Some typeof<obj>)

  nestedType.AddMembersDelayed (fun () -> 
    let staticPropsInNestedType = 
      [ for i in 1 .. 100 do
          let valueOfTheProperty = "I am string "  + string i

          let p = 
            ProvidedProperty(propertyName = "StaticProperty" + string i, 
              propertyType = typeof<string>, 
              isStatic = true,
              getterCode= (fun args -> <@@ valueOfTheProperty @@>))

          p.AddXmlDocDelayed(fun () -> 
              sprintf "This is StaticProperty%d on NestedType" i)

          yield p ]

    staticPropsInNestedType)

  [nestedType])
```

### <a name="details-about-erased-provided-types"></a><span data-ttu-id="35f20-213">Szczegółowe informacje o wymazanych podanych typów</span><span class="sxs-lookup"><span data-stu-id="35f20-213">Details about Erased Provided Types</span></span>

<span data-ttu-id="35f20-214">W przykładzie w tej sekcji przedstawiono tylko *wymazane udostępnionych typów*, które są szczególnie przydatne w następujących sytuacjach:</span><span class="sxs-lookup"><span data-stu-id="35f20-214">The example in this section provides only *erased provided types*, which are particularly useful in the following situations:</span></span>

- <span data-ttu-id="35f20-215">Podczas pisania dostawcy przestrzeni informacji zawierającego tylko dane i metody.</span><span class="sxs-lookup"><span data-stu-id="35f20-215">When you are writing a provider for an information space that contains only data and methods.</span></span>

- <span data-ttu-id="35f20-216">Podczas pisania dostawcy, gdzie semantyki dokładne typ środowiska uruchomieniowego nie są krytyczne dla praktyczne wykorzystanie miejsca informacji.</span><span class="sxs-lookup"><span data-stu-id="35f20-216">When you are writing a provider where accurate runtime-type semantics aren't critical for practical use of the information space.</span></span>

- <span data-ttu-id="35f20-217">Podczas pisania dostawcy przestrzeni informacji tak dużej i wzajemnie połączone, że nie jest technicznie możliwe do generowania rzeczywistych typów .NET do obszaru informacji.</span><span class="sxs-lookup"><span data-stu-id="35f20-217">When you are writing a provider for an information space that is so large and interconnected that it isn’t technically feasible to generate real .NET types for the information space.</span></span>

<span data-ttu-id="35f20-218">W tym przykładzie każdy z podanych usunięciem typu na typ `obj`, i wszystkich używa tego typu będą wyświetlane jako typ `obj` w skompilowany kod.</span><span class="sxs-lookup"><span data-stu-id="35f20-218">In this example, each provided type is erased to type `obj`, and all uses of the type will appear as type `obj` in compiled code.</span></span> <span data-ttu-id="35f20-219">W rzeczywistości obiektów w tym przykładzie są ciągami, ale typ będzie wyświetlany jako `System.Object` w .NET skompilowany kod.</span><span class="sxs-lookup"><span data-stu-id="35f20-219">In fact, the underlying objects in these examples are strings, but the type will appear as `System.Object` in .NET compiled code.</span></span> <span data-ttu-id="35f20-220">Jak z wszystkich zastosowań usunięcia typu, możesz użyć jawnego pakującej, Rozpakowywanie i rzutowanie do mógł wykorzystać wymazane typów.</span><span class="sxs-lookup"><span data-stu-id="35f20-220">As with all uses of type erasure, you can use explicit boxing, unboxing, and casting to subvert erased types.</span></span> <span data-ttu-id="35f20-221">W takim przypadku wyjątek rzutowania, który nie jest prawidłową może spowodować, jeśli obiekt jest używany.</span><span class="sxs-lookup"><span data-stu-id="35f20-221">In this case, a cast exception that isn’t valid may result when the object is used.</span></span> <span data-ttu-id="35f20-222">Środowisko uruchomieniowe dostawcy można zdefiniować własny typ reprezentacji prywatnych, aby zapewnić ochronę przed reprezentacje wartość false.</span><span class="sxs-lookup"><span data-stu-id="35f20-222">A provider runtime can define its own private representation type to help protect against false representations.</span></span> <span data-ttu-id="35f20-223">Nie można zdefiniować wymazanej typów w języku F # samej siebie.</span><span class="sxs-lookup"><span data-stu-id="35f20-223">You can’t define erased types in F# itself.</span></span> <span data-ttu-id="35f20-224">Tylko podane typy mogą zostać utracone.</span><span class="sxs-lookup"><span data-stu-id="35f20-224">Only provided types may be erased.</span></span> <span data-ttu-id="35f20-225">Należy poznać konsekwencje, zarówno praktyczne i semantyczne dowolną wymazanej typów dla typu dostawcy lub dostawcę, który zapewnia usunięte typów.</span><span class="sxs-lookup"><span data-stu-id="35f20-225">You must understand the ramifications, both practical and semantic, of using either erased types for your type provider or a provider that provides erased types.</span></span> <span data-ttu-id="35f20-226">Typ wymazywania nie ma rzeczywistego .NET typu.</span><span class="sxs-lookup"><span data-stu-id="35f20-226">An erased type has no real .NET type.</span></span> <span data-ttu-id="35f20-227">W związku z tym nie można dokładnie odzwierciedla za pośrednictwem typu i może mógł wykorzystać wymazanej typów środowiska wykonawczego rzutowania i innych technik, które opierają się na semantykę typu dokładne środowiska uruchomieniowego za pomocą.</span><span class="sxs-lookup"><span data-stu-id="35f20-227">Therefore, you cannot do accurate reflection over the type, and you might subvert erased types if you use runtime casts and other techniques that rely on exact runtime type semantics.</span></span> <span data-ttu-id="35f20-228">Podwersją wymazanej typów często skutkuje typu rzutowania wyjątków w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="35f20-228">Subversion of erased types frequently results in type cast exceptions at runtime.</span></span>


### <a name="choosing-representations-for-erased-provided-types"></a><span data-ttu-id="35f20-229">Wybieranie oświadczenia dla wymazane podane typy</span><span class="sxs-lookup"><span data-stu-id="35f20-229">Choosing Representations for Erased Provided Types</span></span>

<span data-ttu-id="35f20-230">Dla niektórych zastosowaniach wymazanych podanych typów nie jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="35f20-230">For some uses of erased provided types, no representation is required.</span></span> <span data-ttu-id="35f20-231">Na przykład wymazanej dostarczono typu może zawierać tylko właściwości statycznych i elementów członkowskich i ma konstruktorów oraz żadnych metod ani właściwości zwróci wystąpienia typu.</span><span class="sxs-lookup"><span data-stu-id="35f20-231">For example, the erased provided type might contain only static properties and members and no constructors, and no methods or properties would return an instance of the type.</span></span> <span data-ttu-id="35f20-232">Dostęp można uzyskać wystąpień wymazanej podany typ, należy wziąć pod uwagę następujące kwestie:</span><span class="sxs-lookup"><span data-stu-id="35f20-232">If you can reach instances of an erased provided type, you must consider the following questions:</span></span>

<span data-ttu-id="35f20-233">**Co to jest skasowanie udostępnionego typu?**</span><span class="sxs-lookup"><span data-stu-id="35f20-233">**What is the erasure of a provided type?**</span></span>

- <span data-ttu-id="35f20-234">Skasowanie udostępnionego typu jest sposób wyświetlania typu skompilowanego kodu .NET.</span><span class="sxs-lookup"><span data-stu-id="35f20-234">The erasure of a provided type is how the type appears in compiled .NET code.</span></span>

- <span data-ttu-id="35f20-235">Skasowanie typu klasy wymazanej podany jest zawsze pierwszy-wymazane typu podstawowego w łańcuch dziedziczenia tego typu.</span><span class="sxs-lookup"><span data-stu-id="35f20-235">The erasure of a provided erased class type is always the first non-erased base type in the inheritance chain of the type.</span></span>

- <span data-ttu-id="35f20-236">Skasowanie tego typu interfejsu wymazanej podany jest zawsze `System.Object`.</span><span class="sxs-lookup"><span data-stu-id="35f20-236">The erasure of a provided erased interface type is always `System.Object`.</span></span>

<span data-ttu-id="35f20-237">**Co to są oświadczenia udostępnionego typu?**</span><span class="sxs-lookup"><span data-stu-id="35f20-237">**What are the representations of a provided type?**</span></span>

- <span data-ttu-id="35f20-238">Zestaw obiektów możliwych do wymazanej podany typ są nazywane oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="35f20-238">The set of possible objects for an erased provided type are called its representations.</span></span> <span data-ttu-id="35f20-239">W tym przykładzie w tym dokumencie typy oświadczeń wszystkich wymazanej podany `Type1.Type100` są zawsze obiektów typu string.</span><span class="sxs-lookup"><span data-stu-id="35f20-239">In the example in this document, the representations of all the erased provided types `Type1..Type100` are always string objects.</span></span>

<span data-ttu-id="35f20-240">Wszystkie oświadczenia udostępnionego typu muszą być zgodne z skasowanie podanego typu.</span><span class="sxs-lookup"><span data-stu-id="35f20-240">All representations of a provided type must be compatible with the erasure of the provided type.</span></span> <span data-ttu-id="35f20-241">(W przeciwnym razie kompilator języka F # zapewni Błąd stosowania typ dostawcy lub zostanie wygenerowany zweryfikowanie kodu platformy .NET, który nie jest prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="35f20-241">(Otherwise, either the F# compiler will give an error for a use of the type provider, or unverifiable .NET code that isn't valid will be generated.</span></span> <span data-ttu-id="35f20-242">Typ dostawcy nie jest prawidłowy, jeśli zwróci ona kod, który udostępnia reprezentację, który nie jest prawidłowy.)</span><span class="sxs-lookup"><span data-stu-id="35f20-242">A type provider isn’t valid if it returns code that gives a  representation that isn't valid.)</span></span>

<span data-ttu-id="35f20-243">Możesz wybrać reprezentację podanych obiektów przy użyciu jednej z następujących metod, które są często:</span><span class="sxs-lookup"><span data-stu-id="35f20-243">You can choose a representation for provided objects by using either of the following approaches, both of which are very common:</span></span>

- <span data-ttu-id="35f20-244">Jeśli po prostu jednoznacznie otoki przez istniejący typ architektury .NET, często warto dla danego typu wymazać dla tego typu, należy użyć wystąpienia tego typu jako oświadczenia lub oba.</span><span class="sxs-lookup"><span data-stu-id="35f20-244">If you're simply providing a strongly typed wrapper over an existing .NET type, it often makes sense for your type to erase to that type, use instances of that type as representations, or both.</span></span> <span data-ttu-id="35f20-245">Ta metoda jest odpowiednie, gdy większość istniejących metod tego typu nadal sensu, korzystając z silnie typizowaną wersję.</span><span class="sxs-lookup"><span data-stu-id="35f20-245">This approach is appropriate when most of the existing methods on that type still make sense when using the strongly typed version.</span></span>

- <span data-ttu-id="35f20-246">Jeśli chcesz utworzyć interfejs API, który różni się znacząco od wszystkich istniejących API .NET, warto do tworzenia typów środowiska uruchomieniowego, które będą usunięcia typu i oświadczenia dla udostępnionych typów.</span><span class="sxs-lookup"><span data-stu-id="35f20-246">If you want to create an API that differs significantly from any existing .NET API, it makes sense to create runtime types that will be the type erasure and representations for the provided types.</span></span>

<span data-ttu-id="35f20-247">W przykładzie w niniejszym dokumencie użyto ciągi jako reprezentacje podanych obiektów.</span><span class="sxs-lookup"><span data-stu-id="35f20-247">The example in this document uses strings as representations of provided objects.</span></span> <span data-ttu-id="35f20-248">Często może być stosowanie reprezentacje inne obiekty.</span><span class="sxs-lookup"><span data-stu-id="35f20-248">Frequently, it may be appropriate to use other objects for representations.</span></span> <span data-ttu-id="35f20-249">Na przykład może użyć słownika jako zbiór właściwości:</span><span class="sxs-lookup"><span data-stu-id="35f20-249">For example, you may use a dictionary as a property bag:</span></span>

```fsharp
ProvidedConstructor(parameters = [], 
    invokeCode= (fun args -> <@@ (new Dictionary<string,obj>()) :> obj @@>))
```

<span data-ttu-id="35f20-250">Alternatywnie może zdefiniować typu w dostawcy typu, który będzie używany w czasie wykonywania do utworzenia reprezentacji, wraz z co najmniej jedną operację środowiska uruchomieniowego:</span><span class="sxs-lookup"><span data-stu-id="35f20-250">As an alternative, you may define a type in your type provider that will be used at runtime to form the representation, along with one or more runtime operations:</span></span>

```fsharp
type DataObject() =
    let data = Dictionary<string,obj>()
    member x.RuntimeOperation() = data.Count
```

<span data-ttu-id="35f20-251">Podane elementy członkowskie następnie można utworzyć wystąpień tego typu obiektu:</span><span class="sxs-lookup"><span data-stu-id="35f20-251">Provided members can then construct instances of this object type:</span></span>

```fsharp
ProvidedConstructor(parameters = [], 
    invokeCode= (fun args -> <@@ (new DataObject()) :> obj @@>))
```

<span data-ttu-id="35f20-252">W takim przypadku może (opcjonalnie) używasz tego typu jako typ wymazywania, określając tego typu jako `baseType` podczas konstruowania `ProvidedTypeDefinition`:</span><span class="sxs-lookup"><span data-stu-id="35f20-252">In this case, you may (optionally) use this type as the type erasure by specifying this type as the `baseType` when constructing the `ProvidedTypeDefinition`:</span></span>

```fsharp
ProvidedTypeDefinition(…, baseType = Some typeof<DataObject> )
…
ProvidedConstructor(…, InvokeCode = (fun args -> <@@ new DataObject() @@>), …)
```

### <a name="key-lessons"></a><span data-ttu-id="35f20-253">Klucza — lekcje</span><span class="sxs-lookup"><span data-stu-id="35f20-253">Key Lessons</span></span>

<span data-ttu-id="35f20-254">W poprzedniej sekcji objaśniono sposób tworzenia prostego wymazywanie dostawcy typu, który udostępnia szereg typów, właściwości i metod.</span><span class="sxs-lookup"><span data-stu-id="35f20-254">The previous section explained how to create a simple erasing type provider that provides a range of types, properties, and methods.</span></span> <span data-ttu-id="35f20-255">W tej sekcji również wyjaśniono pojęcie usunięcia typu, w tym niektóre zalety i wady udostępnia typy wymazanej od dostawcy typów i opisem reprezentacje wymazanej typów.</span><span class="sxs-lookup"><span data-stu-id="35f20-255">This section also explained the concept of type erasure, including some of the advantages and disadvantages of providing erased types from a type provider, and discussed representations of erased types.</span></span>


## <a name="a-type-provider-that-uses-static-parameters"></a><span data-ttu-id="35f20-256">Typ dostawcy, która używa parametrów statycznych</span><span class="sxs-lookup"><span data-stu-id="35f20-256">A Type Provider That Uses Static Parameters</span></span>

<span data-ttu-id="35f20-257">Możliwość parametryzacja dostawców typu na statycznych danych umożliwia wielu scenariuszy interesujące, nawet w przypadku dostawcy nie potrzebuje dostępu do żadnych danych lokalnych lub zdalnych.</span><span class="sxs-lookup"><span data-stu-id="35f20-257">The ability to parameterize type providers by static data enables many interesting scenarios, even in cases when the provider doesn't need to access any local or remote data.</span></span> <span data-ttu-id="35f20-258">W tej sekcji omówiono niektóre podstawowe techniki zestawienie takiego dostawcy.</span><span class="sxs-lookup"><span data-stu-id="35f20-258">In this section, you’ll learn some basic techniques for putting together such a provider.</span></span>


### <a name="type-checked-regex-provider"></a><span data-ttu-id="35f20-259">Typ zaznaczone dostawcy wyrażeń regularnych</span><span class="sxs-lookup"><span data-stu-id="35f20-259">Type Checked Regex Provider</span></span>

<span data-ttu-id="35f20-260">Wyobraź sobie chcesz implementowania dostawcy typu dla wyrażeń regularnych, który opakowuje .NET <xref:System.Text.RegularExpressions.Regex> bibliotek interfejs, który udostępnia następujące gwarancje kompilacji:</span><span class="sxs-lookup"><span data-stu-id="35f20-260">Imagine that you want to implement a type provider for regular expressions that wraps the .NET <xref:System.Text.RegularExpressions.Regex> libraries in an interface that provides the following compile-time guarantees:</span></span>

- <span data-ttu-id="35f20-261">Sprawdzanie, czy wyrażenie regularne jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="35f20-261">Verifying whether a regular expression is valid.</span></span>

- <span data-ttu-id="35f20-262">Udostępnia właściwości o nazwie na dopasowań, które są oparte na wszystkie nazwy grup w wyrażeniu regularnym.</span><span class="sxs-lookup"><span data-stu-id="35f20-262">Providing named properties on matches that are based on any group names in the regular expression.</span></span>

<span data-ttu-id="35f20-263">W tej sekcji przedstawiono sposób umożliwia tworzenie dostawcy typów `RegexTyped` wpisz, że wzorzec wyrażenia regularnego parameterizes umożliwia uzyskiwanie tych korzyści.</span><span class="sxs-lookup"><span data-stu-id="35f20-263">This section shows you how to use type providers to create a `RegexTyped` type that the regular expression pattern parameterizes to provide these benefits.</span></span> <span data-ttu-id="35f20-264">Kompilator będzie zgłaszać błąd, jeśli dostarczonym wzorcem nie jest prawidłowa, a dostawca typów można wyodrębnić grup z wzorzec, dzięki czemu będą dostępne za pomocą o nazwie właściwości dopasowań.</span><span class="sxs-lookup"><span data-stu-id="35f20-264">The compiler will report an error if the supplied pattern isn't valid, and the type provider can extract the groups from the pattern so that you can access them by using named properties on matches.</span></span> <span data-ttu-id="35f20-265">Podczas projektowania dostawcy typów, należy rozważyć wygląd jego narażonych interfejsu API do użytkowników końcowych i jak przekształci ten projekt w kodu platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="35f20-265">When you design a type provider, you should consider how its exposed API should look to end users and how this design will translate to .NET code.</span></span> <span data-ttu-id="35f20-266">Poniższy przykład przedstawia sposób użycia interfejsu API na pobranie składników numer kierunkowy:</span><span class="sxs-lookup"><span data-stu-id="35f20-266">The following example shows how to use such an API to get the components of the area code:</span></span>

```fsharp
type T = RegexTyped< @"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)">
let reg = T()
let result = T.IsMatch("425-555-2345")
let r = reg.Match("425-555-2345").Group_AreaCode.Value //r equals "425"
```

<span data-ttu-id="35f20-267">W poniższym przykładzie pokazano, jak typ dostawcy tłumaczy tych wywołań:</span><span class="sxs-lookup"><span data-stu-id="35f20-267">The following example shows how the type provider translates these calls:</span></span>

```fsharp
let reg = new Regex(@"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)")
let result = reg.IsMatch("425-123-2345")
let r = reg.Match("425-123-2345").Groups.["AreaCode"].Value //r equals "425"
```

<span data-ttu-id="35f20-268">Należy uwzględnić następujące kwestie:</span><span class="sxs-lookup"><span data-stu-id="35f20-268">Note the following points:</span></span>

- <span data-ttu-id="35f20-269">Standardowy typ wyrażenia regularnego reprezentuje sparametryzowane `RegexTyped` typu.</span><span class="sxs-lookup"><span data-stu-id="35f20-269">The standard Regex type represents the parameterized `RegexTyped` type.</span></span>

- <span data-ttu-id="35f20-270">`RegexTyped` Konstruktor powoduje wywołanie konstruktora wyrażeń regularnych, przekazując argument typu statycznego dla wzorca.</span><span class="sxs-lookup"><span data-stu-id="35f20-270">The `RegexTyped` constructor results in a call to the Regex constructor, passing in the static type argument for the pattern.</span></span>

- <span data-ttu-id="35f20-271">Wyniki `Match` metody są reprezentowane przez standardowe <xref:System.Text.RegularExpressions.Match> typu.</span><span class="sxs-lookup"><span data-stu-id="35f20-271">The results of the `Match` method are represented by the standard <xref:System.Text.RegularExpressions.Match> type.</span></span>

- <span data-ttu-id="35f20-272">Każda grupa o nazwie powoduje podane właściwości i uzyskiwania dostępu do właściwości powoduje użycie indeksatora w przypadku dopasowania `Groups` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="35f20-272">Each named group results in a provided property, and accessing the property results in a use of an indexer on a match’s `Groups` collection.</span></span>

<span data-ttu-id="35f20-273">Następujący kod jest podstawową logikę do wykonania takiego dostawcy, a w tym przykładzie są pomijane przez dodanie wszystkich elementów członkowskich do udostępnionego typu.</span><span class="sxs-lookup"><span data-stu-id="35f20-273">The following code is the core of the logic to implement such a provider, and this example omits the addition of all members to the provided type.</span></span> <span data-ttu-id="35f20-274">Informacje o każdym dodano element członkowski Zobacz odpowiedniej sekcji w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="35f20-274">For information about each added member, see the appropriate section later in this topic.</span></span> <span data-ttu-id="35f20-275">Dla pełnego kodu, Pobierz przykład z [F # 3.0 przykładowy pakiet](https://fsharp3sample.codeplex.com) w witrynie Codeplex.</span><span class="sxs-lookup"><span data-stu-id="35f20-275">For the full code, download the sample from the [F# 3.0 Sample Pack](https://fsharp3sample.codeplex.com) on the Codeplex website.</span></span>

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

<span data-ttu-id="35f20-276">Należy uwzględnić następujące kwestie:</span><span class="sxs-lookup"><span data-stu-id="35f20-276">Note the following points:</span></span>

- <span data-ttu-id="35f20-277">Typ dostawcy przyjmuje dwa parametry statyczne: `pattern`, który jest obowiązkowy oraz `options`, które są opcjonalne (ponieważ podano wartość domyślna).</span><span class="sxs-lookup"><span data-stu-id="35f20-277">The type provider takes two static parameters: the `pattern`, which is mandatory, and the `options`, which are optional (because a default value is provided).</span></span>

- <span data-ttu-id="35f20-278">Po argumentów statycznych są dostarczane, można utworzyć wystąpienia wyrażenia regularnego.</span><span class="sxs-lookup"><span data-stu-id="35f20-278">After the static arguments are supplied, you create an instance of the regular expression.</span></span> <span data-ttu-id="35f20-279">Tego wystąpienia spowoduje zgłoszenie wyjątku, jeśli wyrażenia regularnego jest nieprawidłowo sformułowany, a ten błąd będzie zgłaszany użytkownikom.</span><span class="sxs-lookup"><span data-stu-id="35f20-279">This instance will throw an exception if the Regex is malformed, and this error will be reported to users.</span></span>

- <span data-ttu-id="35f20-280">W ramach `DefineStaticParameters` wywołania zwrotnego, zdefiniuj typ, który zostanie zwrócona po podano argumenty.</span><span class="sxs-lookup"><span data-stu-id="35f20-280">Within the `DefineStaticParameters` callback, you define the type that will be returned after the arguments are supplied.</span></span>

- <span data-ttu-id="35f20-281">Ten kod ustawia `HideObjectMethods` na wartość true, aby w środowisku IntelliSense pozostanie prostsze.</span><span class="sxs-lookup"><span data-stu-id="35f20-281">This code sets `HideObjectMethods` to true so that the IntelliSense experience will remain streamlined.</span></span> <span data-ttu-id="35f20-282">Powoduje, że ten atrybut `Equals`, `GetHashCode`, `Finalize`, i `GetType` elementów członkowskich mają zostać pominięte z list IntelliSense dla podanego obiektu.</span><span class="sxs-lookup"><span data-stu-id="35f20-282">This attribute causes the `Equals`, `GetHashCode`, `Finalize`, and `GetType` members to be suppressed from IntelliSense lists for a provided object.</span></span>

- <span data-ttu-id="35f20-283">Możesz użyć `obj` jako typ bazowy metody, ale będzie użyj `Regex` obiektu jako środowiska uruchomieniowego reprezentacja tego typu, jak w następnym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="35f20-283">You use `obj` as the base type of the method, but you’ll use a `Regex` object as the runtime representation of this type, as the next example shows.</span></span>

- <span data-ttu-id="35f20-284">Wywołanie `Regex` zgłasza konstruktora <xref:System.ArgumentException> po wyrażenie regularne jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="35f20-284">The call to the `Regex` constructor throws a <xref:System.ArgumentException> when a regular expression isn’t valid.</span></span> <span data-ttu-id="35f20-285">Kompilator przechwytuje tego wyjątku i raporty komunikat o błędzie do użytkownika w czasie kompilacji lub w edytorze programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="35f20-285">The compiler catches this exception and reports an error message to the user at compile time or in the Visual Studio editor.</span></span> <span data-ttu-id="35f20-286">Ten wyjątek umożliwia wyrażeń regularnych do sprawdzenia poprawności bez uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="35f20-286">This exception enables regular expressions to be validated without running an application.</span></span>

<span data-ttu-id="35f20-287">Typ zdefiniowany powyżej jest bezużyteczne jeszcze ponieważ nie zawiera ona właściwości lub metody łatwy do rozpoznania.</span><span class="sxs-lookup"><span data-stu-id="35f20-287">The type defined above isn't useful yet because it doesn’t contain any meaningful methods or properties.</span></span> <span data-ttu-id="35f20-288">Najpierw dodaj statycznego `IsMatch` metody:</span><span class="sxs-lookup"><span data-stu-id="35f20-288">First, add a static `IsMatch` method:</span></span>

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

<span data-ttu-id="35f20-289">Poprzedni kod definiuje metodę `IsMatch`, która przyjmuje ciągu na wejściu i zwraca `bool`.</span><span class="sxs-lookup"><span data-stu-id="35f20-289">The previous code defines a method `IsMatch`, which takes a string as input and returns a `bool`.</span></span> <span data-ttu-id="35f20-290">Tylko wymagana jest użycie `args` argument w `InvokeCode` definicji.</span><span class="sxs-lookup"><span data-stu-id="35f20-290">The only tricky part is the use of the `args` argument within the `InvokeCode` definition.</span></span> <span data-ttu-id="35f20-291">W tym przykładzie `args` znajduje się lista ofert reprezentujący argumenty do tej metody.</span><span class="sxs-lookup"><span data-stu-id="35f20-291">In this example, `args` is a list of quotations that represents the arguments to this method.</span></span> <span data-ttu-id="35f20-292">Jeśli metoda jest metodą wystąpienia, pierwszy argument reprezentuje `this` argumentu.</span><span class="sxs-lookup"><span data-stu-id="35f20-292">If the method is an instance method, the first argument represents the `this` argument.</span></span> <span data-ttu-id="35f20-293">Dla metody statycznej, argumenty są wszystkie tylko jawne argumenty metody.</span><span class="sxs-lookup"><span data-stu-id="35f20-293">However, for a static method, the arguments are all just the explicit arguments to the method.</span></span> <span data-ttu-id="35f20-294">Należy pamiętać, że typ cudzysłowie wartości powinna być zgodna określony zwracany typ (w tym przypadku `bool`).</span><span class="sxs-lookup"><span data-stu-id="35f20-294">Note that the type of the quoted value should match the specified return type (in this case, `bool`).</span></span> <span data-ttu-id="35f20-295">Należy także zauważyć, że używa tego kodu `AddXmlDoc` metody, aby upewnić się, że podana metoda ma również przydatne dokumentacji, której można zapewnić za pomocą funkcji IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="35f20-295">Also note that this code uses the `AddXmlDoc` method to make sure that the provided method also has useful documentation, which you can supply through IntelliSense.</span></span>

<span data-ttu-id="35f20-296">Następnie dodaj wystąpienia metody Match.</span><span class="sxs-lookup"><span data-stu-id="35f20-296">Next, add an instance Match method.</span></span> <span data-ttu-id="35f20-297">Jednak ta metoda powinna zwrócić wartość podana `Match` wpisz, aby grupy jest możliwy w sposób jednoznaczny.</span><span class="sxs-lookup"><span data-stu-id="35f20-297">However, this method should return a value of a provided `Match` type so that the groups can be accessed in a strongly typed fashion.</span></span> <span data-ttu-id="35f20-298">W związku z tym najpierw zadeklarować `Match` typu.</span><span class="sxs-lookup"><span data-stu-id="35f20-298">Thus, you first declare the `Match` type.</span></span> <span data-ttu-id="35f20-299">Ponieważ ten typ zależy od wzorca, który został dostarczony jako argument statyczny, tego typu musi być zagnieżdżony w definicji typu sparametryzowane:</span><span class="sxs-lookup"><span data-stu-id="35f20-299">Because this type depends on the pattern that was supplied as a static argument, this type must be nested within the parameterized type definition:</span></span>

```fsharp
let matchTy = 
    ProvidedTypeDefinition(
        "MatchType", 
        baseType = Some baseTy, 
        hideObjectMethods = true)

ty.AddMember matchTy
```

<span data-ttu-id="35f20-300">Można następnie dodać jedną właściwość na typ dopasowania dla każdej grupy.</span><span class="sxs-lookup"><span data-stu-id="35f20-300">You then add one property to the Match type for each group.</span></span> <span data-ttu-id="35f20-301">W czasie wykonywania, dopasowanie jest reprezentowany jako <xref:System.Text.RegularExpressions.Match> wartości, należy użyć cudzysłowów, który definiuje właściwość <xref:System.Text.RegularExpressions.Match.Groups> indeksowane właściwości, aby uzyskać odpowiednie grupy.</span><span class="sxs-lookup"><span data-stu-id="35f20-301">At runtime, a match is represented as a <xref:System.Text.RegularExpressions.Match> value, so the quotation that defines the property must use the <xref:System.Text.RegularExpressions.Match.Groups> indexed property to get the relevant group.</span></span>

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

<span data-ttu-id="35f20-302">Ponownie należy pamiętać, podane właściwości dodajesz dokumentacji XML.</span><span class="sxs-lookup"><span data-stu-id="35f20-302">Again, note that you’re adding XML documentation to the provided property.</span></span> <span data-ttu-id="35f20-303">Należy także zauważyć, że właściwość może zostać odczytany, jeśli `GetterCode` funkcja zapewnia i właściwości mogą być zapisywane, jeśli `SetterCode` podano funkcji, aby wynikowych właściwość jest tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="35f20-303">Also note that a property can be read if a `GetterCode` function is provided, and the property can be written if a `SetterCode` function is provided, so the resulting property is read only.</span></span>

<span data-ttu-id="35f20-304">Teraz można utworzyć metody wystąpienia, która zwraca wartość tego `Match` typu:</span><span class="sxs-lookup"><span data-stu-id="35f20-304">Now you can create an instance method that returns a value of this `Match` type:</span></span>

```fsharp
let matchMethod = 
    ProvidedMethod(
        methodName = "Match", 
        parameters = [ProvidedParameter("input", typeof<string>)], 
        returnType = matchTy, 
        invokeCode = fun args -> <@@ ((%%args.[0]:obj) :?> Regex).Match(%%args.[1]) :> obj @@>)

matchMeth.AddXmlDoc "Searches the specified input string for the first ocurrence of this regular expression" 

ty.AddMember matchMeth
```

<span data-ttu-id="35f20-305">Ponieważ tworzysz metodą wystąpienia `args.[0]` reprezentuje `RegexTyped` wystąpienia, na którym jest wywoływana metoda, i `args.[1]` jest argument wejściowy.</span><span class="sxs-lookup"><span data-stu-id="35f20-305">Because you are creating an instance method, `args.[0]` represents the `RegexTyped` instance on which the method is being called, and `args.[1]` is the input argument.</span></span>

<span data-ttu-id="35f20-306">Na koniec należy umożliwić konstruktora, dzięki czemu można utworzyć wystąpienia podanego typu.</span><span class="sxs-lookup"><span data-stu-id="35f20-306">Finally, provide a constructor so that instances of the provided type can be created.</span></span>

```fsharp
let ctor = 
    ProvidedConstructor(
        parameters = [], 
        invokeCode = fun args -> <@@ Regex(pattern, options) :> obj @@>)

ctor.AddXmlDoc("Initializes a regular expression instance.")

ty.AddMember ctor
```

<span data-ttu-id="35f20-307">Konstruktor powoduje usunięcie tylko do utworzenia standardowe wystąpienia wyrażenie regularne .NET, która jest opakowany ponownie do obiektu, ponieważ `obj` jest skasowanie podanego typu.</span><span class="sxs-lookup"><span data-stu-id="35f20-307">The constructor merely erases to the creation of a standard .NET Regex instance, which is again boxed to an object because `obj` is the erasure of the provided type.</span></span> <span data-ttu-id="35f20-308">Z tą zmianą Przykładowe użycie interfejsu API, który określony wcześniej w temacie działa zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="35f20-308">With that change, the sample API usage that specified earlier in the topic works as expected.</span></span> <span data-ttu-id="35f20-309">Następujący kod jest pełny i końcowe:</span><span class="sxs-lookup"><span data-stu-id="35f20-309">The following code is complete and final:</span></span>

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
                matchMeth.AddXmlDoc "Searches the specified input string for the first occurence of this regular expression"

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

### <a name="key-lessons"></a><span data-ttu-id="35f20-310">Klucza — lekcje</span><span class="sxs-lookup"><span data-stu-id="35f20-310">Key Lessons</span></span>

<span data-ttu-id="35f20-311">W tej sekcji wyjaśniono, jak utworzyć typ dostawcy, który działa na jego parametrów statycznych.</span><span class="sxs-lookup"><span data-stu-id="35f20-311">This section explained how to create a type provider that operates on its static parameters.</span></span> <span data-ttu-id="35f20-312">Dostawca sprawdza parametr statyczny i udostępnia operacje na podstawie jego wartości.</span><span class="sxs-lookup"><span data-stu-id="35f20-312">The provider checks the static parameter and provides operations based on its value.</span></span>


## <a name="a-type-provider-that-is-backed-by-local-data"></a><span data-ttu-id="35f20-313">Typ dostawcy, który nie jest obsługiwana przez dane lokalne</span><span class="sxs-lookup"><span data-stu-id="35f20-313">A Type Provider That Is Backed By Local Data</span></span>

<span data-ttu-id="35f20-314">Często może być typ dostawcy do prezentowania interfejsów API oparte na nie tylko parametrów statycznych, ale także informacje z systemów lokalnych lub zdalnych.</span><span class="sxs-lookup"><span data-stu-id="35f20-314">Frequently you might want type providers to present APIs based on not only static parameters but also information from local or remote systems.</span></span> <span data-ttu-id="35f20-315">W tej sekcji omówiono dostawców typów, które są oparte na danych lokalnych, takich jak pliki danych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="35f20-315">This section discusses type providers that are based on local data, such as local data files.</span></span>


### <a name="simple-csv-file-provider"></a><span data-ttu-id="35f20-316">Dostawca plików CSV proste</span><span class="sxs-lookup"><span data-stu-id="35f20-316">Simple CSV File Provider</span></span>

<span data-ttu-id="35f20-317">Jako przykład prostego należy wziąć pod uwagę typ dostawcy do uzyskiwania dostępu do danych naukowych w formacie wartości rozdzielanych przecinkami (CSV).</span><span class="sxs-lookup"><span data-stu-id="35f20-317">As a simple example, consider a type provider for accessing scientific data in Comma Separated Value (CSV) format.</span></span> <span data-ttu-id="35f20-318">W tej sekcji założono, że pliki CSV zawiera wiersz nagłówka następuje ruchomy punkt danych, jak pokazano w poniższej tabeli:</span><span class="sxs-lookup"><span data-stu-id="35f20-318">This section assumes that the CSV files contain a header row followed by floating point data, as the following table illustrates:</span></span>


|<span data-ttu-id="35f20-319">Odległość (licznik)</span><span class="sxs-lookup"><span data-stu-id="35f20-319">Distance (meter)</span></span>|<span data-ttu-id="35f20-320">Czas (sekundy)</span><span class="sxs-lookup"><span data-stu-id="35f20-320">Time (second)</span></span>|
|----------------|-------------|
|<span data-ttu-id="35f20-321">50.0</span><span class="sxs-lookup"><span data-stu-id="35f20-321">50.0</span></span>|<span data-ttu-id="35f20-322">3.7</span><span class="sxs-lookup"><span data-stu-id="35f20-322">3.7</span></span>|
|<span data-ttu-id="35f20-323">100.0</span><span class="sxs-lookup"><span data-stu-id="35f20-323">100.0</span></span>|<span data-ttu-id="35f20-324">5.2</span><span class="sxs-lookup"><span data-stu-id="35f20-324">5.2</span></span>|
|<span data-ttu-id="35f20-325">150.0</span><span class="sxs-lookup"><span data-stu-id="35f20-325">150.0</span></span>|<span data-ttu-id="35f20-326">6.4</span><span class="sxs-lookup"><span data-stu-id="35f20-326">6.4</span></span>|

<span data-ttu-id="35f20-327">W tej sekcji przedstawiono sposób zapewniają typu, który można pobrać wiersze z `Distance` właściwości typu `float<meter>` i `Time` właściwości typu `float<second>`.</span><span class="sxs-lookup"><span data-stu-id="35f20-327">This section shows how to provide a type that you can use to get rows with a `Distance` property of type `float<meter>` and a `Time` property of type `float<second>`.</span></span> <span data-ttu-id="35f20-328">Dla uproszczenia zostały wprowadzone następujące założenia:</span><span class="sxs-lookup"><span data-stu-id="35f20-328">For simplicity, the following assumptions are made:</span></span>

- <span data-ttu-id="35f20-329">Nazwy nagłówków są albo bez jednostki lub mieć formę "Nazwa (jednostka)" i nie mogą zawierać przecinków.</span><span class="sxs-lookup"><span data-stu-id="35f20-329">Header names are either unit-less or have the form "Name (unit)" and don't contain commas.</span></span>

- <span data-ttu-id="35f20-330">Jednostki są wszystkie jednostki Systeme międzynarodowych (SI) jako [Microsoft.FSharp.Data.UnitSystems.SI.UnitNames — moduł (F #)](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b) definiuje modułu.</span><span class="sxs-lookup"><span data-stu-id="35f20-330">Units are all Systeme International (SI) units as the [Microsoft.FSharp.Data.UnitSystems.SI.UnitNames Module (F#)](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b) module defines.</span></span>

- <span data-ttu-id="35f20-331">Jednostki są wszystkie proste (na przykład pomiaru) zamiast złożony (na przykład, zliczania na sekundę).</span><span class="sxs-lookup"><span data-stu-id="35f20-331">Units are all simple (for example, meter) rather than compound (for example, meter/second).</span></span>

- <span data-ttu-id="35f20-332">Wszystkie kolumny zawiera przestawne punktu danych.</span><span class="sxs-lookup"><span data-stu-id="35f20-332">All columns contain floating point data.</span></span>

<span data-ttu-id="35f20-333">Bardziej szczegółowy dostawcy czy Poluzuj te ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="35f20-333">A more complete provider would loosen these restrictions.</span></span>

<span data-ttu-id="35f20-334">Pierwszym krokiem jest ponownie należy wziąć pod uwagę, jak powinna wyglądać interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="35f20-334">Again the first step is to consider how the API should look.</span></span> <span data-ttu-id="35f20-335">Podane `info.csv` plik z zawartością z powyższej tabeli (w formacie rozdzielone przecinkami), użytkownicy dostawcy powinni mieć do pisania kodu, który podobnego do następującego:</span><span class="sxs-lookup"><span data-stu-id="35f20-335">Given an `info.csv` file with the contents from the previous table (in comma-separated format), users of the provider should be able to write code that resembles the following example:</span></span>

```fsharp
let info = new MiniCsv<"info.csv">()
for row in info.Data do
let time = row.Time
printfn "%f" (float time)
```

<span data-ttu-id="35f20-336">W takim przypadku kompilator powinien konwertować te wywołania coś jak w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="35f20-336">In this case, the compiler should convert these calls into something like the following example:</span></span>

```fsharp
let info = new CsvFile("info.csv")
for row in info.Data do
let (time:float) = row.[1]
printfn "%f" (float time)
```

<span data-ttu-id="35f20-337">Optymalne tłumaczenia będzie wymagać typ dostawcy do definiowania rzeczywistych `CsvFile` typu w zestawie typ dostawcy.</span><span class="sxs-lookup"><span data-stu-id="35f20-337">The optimal translation will require the type provider to define a real `CsvFile` type in the type provider's assembly.</span></span> <span data-ttu-id="35f20-338">Dostawcy typów często polegają na kilka typów pomocnika i metod do opakowywania logiki ważne.</span><span class="sxs-lookup"><span data-stu-id="35f20-338">Type providers often rely on a few helper types and methods to wrap important logic.</span></span> <span data-ttu-id="35f20-339">Ponieważ miary są usuwane w czasie wykonywania, można użyć `float[]` jako typ wymazywania wiersza.</span><span class="sxs-lookup"><span data-stu-id="35f20-339">Because measures are erased at runtime, you can use a `float[]` as the erased type for a row.</span></span> <span data-ttu-id="35f20-340">Kompilator będzie traktować różnych kolumn jako mający miary różnych typów.</span><span class="sxs-lookup"><span data-stu-id="35f20-340">The compiler will treat different columns as having different measure types.</span></span> <span data-ttu-id="35f20-341">Na przykład pierwsza kolumna w naszym przykładzie ma typ `float<meter>`, a druga `float<second>`.</span><span class="sxs-lookup"><span data-stu-id="35f20-341">For example, the first column in our example has type `float<meter>`, and the second has `float<second>`.</span></span> <span data-ttu-id="35f20-342">Reprezentacja wymazanej można nadal bardzo proste.</span><span class="sxs-lookup"><span data-stu-id="35f20-342">However, the erased representation can remain quite simple.</span></span>

<span data-ttu-id="35f20-343">Poniższy kod przedstawia podstawowe implementacji.</span><span class="sxs-lookup"><span data-stu-id="35f20-343">The following code shows the core of the implementation.</span></span>

```fsharp
// Simple type wrapping CSV data
type CsvFile(filename) =
    // Cache the sequence of all data lines (all lines but the first)
    let data = 
        seq { for line in File.ReadAllLines(filename) |> Seq.skip 1 do
                 yield line.Split(',') |> Array.map float }
        |> Seq.cache
    member __.Data = data

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

<span data-ttu-id="35f20-344">Należy uwzględnić następujące kwestie dotyczące implementacji:</span><span class="sxs-lookup"><span data-stu-id="35f20-344">Note the following points about the implementation:</span></span>

- <span data-ttu-id="35f20-345">Przeciążone konstruktory Zezwalaj oryginalny plik lub klucz, który ma taki sam schemat do odczytu.</span><span class="sxs-lookup"><span data-stu-id="35f20-345">Overloaded constructors allow either the original file or one that has an identical schema to be read.</span></span> <span data-ttu-id="35f20-346">Ten wzorzec jest wspólne, gdy zapis dostawcy typów źródeł danych lokalnych lub zdalnych, a ten wzorzec umożliwia pliku lokalnego do użycia jako szablon dla danych zdalnych.</span><span class="sxs-lookup"><span data-stu-id="35f20-346">This pattern is common when you write a type provider for local or remote data sources, and this pattern allows a local file to be used as the template for remote data.</span></span>

- <span data-ttu-id="35f20-347">Można użyć [TypeProviderConfig](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44) wartość, która jest przekazywany do konstruktora typu dostawcy do rozpoznawania względnych nazw plików.</span><span class="sxs-lookup"><span data-stu-id="35f20-347">You can use the [TypeProviderConfig](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44) value that’s passed in to the type provider constructor to resolve relative file names.</span></span>

- <span data-ttu-id="35f20-348">Można użyć `AddDefinitionLocation` metodę, aby określić lokalizację podana.</span><span class="sxs-lookup"><span data-stu-id="35f20-348">You can use the `AddDefinitionLocation` method to define the location of the provided properties.</span></span> <span data-ttu-id="35f20-349">Dlatego jeśli używasz `Go To Definition` podane właściwości pliku CSV zostanie otwarty w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="35f20-349">Therefore, if you use `Go To Definition` on a provided property, the CSV file will open in Visual Studio.</span></span>

- <span data-ttu-id="35f20-350">Można użyć `ProvidedMeasureBuilder` typu do wyszukiwania jednostki SI oraz do generowania odpowiednich `float<_>` typów.</span><span class="sxs-lookup"><span data-stu-id="35f20-350">You can use the `ProvidedMeasureBuilder` type to look up the SI units and to generate the relevant `float<_>` types.</span></span>

### <a name="key-lessons"></a><span data-ttu-id="35f20-351">Klucza — lekcje</span><span class="sxs-lookup"><span data-stu-id="35f20-351">Key Lessons</span></span>

<span data-ttu-id="35f20-352">W tej sekcji wyjaśniono sposób tworzenia ze schematem proste, który jest zawarty w źródle danych sam typ dostawcy do lokalnego źródła danych.</span><span class="sxs-lookup"><span data-stu-id="35f20-352">This section explained how to create a type provider for a local data source with a simple schema that's contained in the data source itself.</span></span>


## <a name="going-further"></a><span data-ttu-id="35f20-353">Kontynuowanie</span><span class="sxs-lookup"><span data-stu-id="35f20-353">Going Further</span></span>

<span data-ttu-id="35f20-354">W poniższych sekcjach zawarto sugestie dotyczące dalszych badań.</span><span class="sxs-lookup"><span data-stu-id="35f20-354">The following sections include suggestions for further study.</span></span>


### <a name="a-look-at-the-compiled-code-for-erased-types"></a><span data-ttu-id="35f20-355">Szukaj w kompilowanym kodzie Wymazanej typów</span><span class="sxs-lookup"><span data-stu-id="35f20-355">A Look at the Compiled Code for Erased Types</span></span>

<span data-ttu-id="35f20-356">Aby dać wstępnym sposób korzystania z dostawcy typu odnosi się do kodu, który jest emitowany, obejrzyj następująca funkcja przy użyciu `HelloWorldTypeProvider` używany we wcześniejszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="35f20-356">To give you some idea of how the use of the type provider corresponds to the code that's emitted, look at the following function by using the `HelloWorldTypeProvider` that's used earlier in this topic.</span></span>

```fsharp
let function1 () = 
    let obj1 = Samples.HelloWorldTypeProvider.Type1("some data")
    obj1.InstanceProperty
```

<span data-ttu-id="35f20-357">Oto obraz wynikowy kod decompiled przy użyciu ildasm.exe:</span><span class="sxs-lookup"><span data-stu-id="35f20-357">Here’s an image of the resulting code decompiled by using ildasm.exe:</span></span>

```
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

<span data-ttu-id="35f20-358">Jak przedstawiono na przykład wszystkie wystąpienia typu `Type1` i `InstanceProperty` właściwości zostały wymazane, pozostawiając związane tylko operacje na typów środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="35f20-358">As the example shows, all mentions of the type `Type1` and the `InstanceProperty` property have been erased, leaving only operations on the runtime types involved.</span></span>


### <a name="design-and-naming-conventions-for-type-providers"></a><span data-ttu-id="35f20-359">Projektowanie i konwencje nazewnictwa dla dostawców typów</span><span class="sxs-lookup"><span data-stu-id="35f20-359">Design and Naming Conventions for Type Providers</span></span>
<span data-ttu-id="35f20-360">Podczas tworzenia dostawców typów, należy przestrzegać następujących konwencji.</span><span class="sxs-lookup"><span data-stu-id="35f20-360">Observe the following conventions when authoring type providers.</span></span>

<span data-ttu-id="35f20-361">**Dostawców dla protokołów łączności** ogólnie rzecz biorąc, nazwy dostawcy większości biblioteki DLL dla danych i usługi łączności protokołów, takich jak połączenia OData lub SQL, należy zakończyć w `TypeProvider` lub `TypeProviders`.</span><span class="sxs-lookup"><span data-stu-id="35f20-361">**Providers for Connectivity Protocols** In general, names of most provider DLLs for data and service connectivity protocols, such as OData or SQL connections, should end in `TypeProvider` or `TypeProviders`.</span></span> <span data-ttu-id="35f20-362">Na przykład użyj nazwy biblioteki DLL podobny następujący ciąg:</span><span class="sxs-lookup"><span data-stu-id="35f20-362">For example, use a DLL name that resembles the following string:</span></span>

```
  Fabrikam.Management.BasicTypeProviders.dll
```

<span data-ttu-id="35f20-363">Sprawdź, czy Twojego podanych typów są członkami odpowiedniej przestrzeni nazw i wskazywać, w której można zaimplementować protokół łączności:</span><span class="sxs-lookup"><span data-stu-id="35f20-363">Ensure that your provided types are members of the corresponding namespace, and indicate the connectivity protocol that you implemented:</span></span>

```
  Fabrikam.Management.BasicTypeProviders.WmiConnection<…>
  Fabrikam.Management.BasicTypeProviders.DataProtocolConnection<…>
```

<span data-ttu-id="35f20-364">**Narzędzie dostawców ogólne kodowania**.</span><span class="sxs-lookup"><span data-stu-id="35f20-364">**Utility Providers for General Coding**.</span></span>  <span data-ttu-id="35f20-365">Narzędzie typu dostawcy takim jak dla wyrażeń regularnych dostawca typów może być częścią podstawowej biblioteki, jak przedstawiono na poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="35f20-365">For a utility type provider such as that for regular expressions, the type provider may be part of a base library, as the following example shows:</span></span>

```fsharp
  #r "Fabrikam.Core.Text.Utilities.dll"
```

<span data-ttu-id="35f20-366">W takim przypadku podanego typu pojawią się w odpowiednich punkcie zgodnie z normalnym konwencje projekt .NET:</span><span class="sxs-lookup"><span data-stu-id="35f20-366">In this case, the provided type would appear at an appropriate point according to normal .NET design conventions:</span></span>

```fsharp
  open Fabrikam.Core.Text.RegexTyped
  
  let regex = new RegexTyped<"a+b+a+b+">()
```

<span data-ttu-id="35f20-367">**Źródła danych Singleton**.</span><span class="sxs-lookup"><span data-stu-id="35f20-367">**Singleton Data Sources**.</span></span> <span data-ttu-id="35f20-368">Niektórzy dostawcy typu połączyć się z jednego dedykowanych źródła danych i podaj tylko dane.</span><span class="sxs-lookup"><span data-stu-id="35f20-368">Some type providers connect to a single dedicated data source and provide only data.</span></span> <span data-ttu-id="35f20-369">W takim przypadku należy usunąć `TypeProvider` sufiks i użyj normalnej konwencji nazewnictwa platformy .NET:</span><span class="sxs-lookup"><span data-stu-id="35f20-369">In this case, you should drop the `TypeProvider` suffix and use normal conventions for .NET naming:</span></span>

```fsharp
#r "Fabrikam.Data.Freebase.dll"
  
let data = Fabrikam.Data.Freebase.Astronomy.Asteroids
```

<span data-ttu-id="35f20-370">Aby uzyskać więcej informacji, zobacz `GetConnection` projektowania Konwencji, które jest opisane w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="35f20-370">For more information, see the `GetConnection` design convention that's described later in this topic.</span></span>


### <a name="design-patterns-for-type-providers"></a><span data-ttu-id="35f20-371">Wzorce projektowe dla dostawców typów</span><span class="sxs-lookup"><span data-stu-id="35f20-371">Design Patterns for Type Providers</span></span>

<span data-ttu-id="35f20-372">W poniższych sekcjach opisano wzorce projektowe, używanego podczas tworzenia typu dostawcy.</span><span class="sxs-lookup"><span data-stu-id="35f20-372">The following sections describe design patterns you can use when authoring type providers.</span></span>


#### <a name="the-getconnection-design-pattern"></a><span data-ttu-id="35f20-373">Wzorzec projektowy GetConnection</span><span class="sxs-lookup"><span data-stu-id="35f20-373">The GetConnection Design Pattern</span></span>
<span data-ttu-id="35f20-374">Większość dostawców typów mają być zapisywane do użycia `GetConnection` wzorca, który jest używany przez dostawców typów w FSharp.Data.TypeProviders.dll, jak przedstawiono na poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="35f20-374">Most type providers should be written to use the `GetConnection` pattern that's used by the type providers in FSharp.Data.TypeProviders.dll, as the following example shows:</span></span>

```fsharp
#r "Fabrikam.Data.WebDataStore.dll"

type Service = Fabrikam.Data.WebDataStore<…static connection parameters…>

let connection = Service.GetConnection(…dynamic connection parameters…)

let data = connection.Astronomy.Asteroids
```

#### <a name="type-providers-backed-by-remote-data-and-services"></a><span data-ttu-id="35f20-375">Dostawcy typów kopii danych zdalnych i usługi</span><span class="sxs-lookup"><span data-stu-id="35f20-375">Type Providers Backed By Remote Data and Services</span></span>

<span data-ttu-id="35f20-376">Przed utworzeniem typ dostawcy, który nie jest obsługiwana przez zdalnych danych i usług, należy wziąć pod uwagę szereg problemów, które są związane z połączonych programowania.</span><span class="sxs-lookup"><span data-stu-id="35f20-376">Before you create a type provider that's backed by remote data and services, you must consider a range of issues that are inherent in connected programming.</span></span> <span data-ttu-id="35f20-377">Te problemy obejmują następujące zagadnienia:</span><span class="sxs-lookup"><span data-stu-id="35f20-377">These issues include the following considerations:</span></span>

- <span data-ttu-id="35f20-378">Mapowanie schematu</span><span class="sxs-lookup"><span data-stu-id="35f20-378">schema mapping</span></span>

- <span data-ttu-id="35f20-379">liveness i unieważniania obecności zmiany schematu</span><span class="sxs-lookup"><span data-stu-id="35f20-379">liveness and invalidation in the presence of schema change</span></span>

- <span data-ttu-id="35f20-380">buforowanie schematu</span><span class="sxs-lookup"><span data-stu-id="35f20-380">schema caching</span></span>

- <span data-ttu-id="35f20-381">asynchroniczne implementacje operacji uzyskiwania dostępu do danych</span><span class="sxs-lookup"><span data-stu-id="35f20-381">asynchronous implementations of data access operations</span></span>

- <span data-ttu-id="35f20-382">Obsługa zapytania, łącznie z zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="35f20-382">supporting queries, including LINQ queries</span></span>

- <span data-ttu-id="35f20-383">poświadczeń i uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="35f20-383">credentials and authentication</span></span>

<span data-ttu-id="35f20-384">W tym temacie nie Poznaj dodatkowe tych problemów.</span><span class="sxs-lookup"><span data-stu-id="35f20-384">This topic doesn't explore these issues further.</span></span>

### <a name="additional-authoring-techniques"></a><span data-ttu-id="35f20-385">Innych technik tworzenia pakietów administracyjnych</span><span class="sxs-lookup"><span data-stu-id="35f20-385">Additional Authoring Techniques</span></span>

<span data-ttu-id="35f20-386">Podczas pisania własnych dostawców typów, można korzystać z następujących metod dodatkowe.</span><span class="sxs-lookup"><span data-stu-id="35f20-386">When you write your own type providers, you might want to use the following additional techniques.</span></span>

### <a name="creating-types-and-members-on-demand"></a><span data-ttu-id="35f20-387">Tworzenie typów i członków na żądanie</span><span class="sxs-lookup"><span data-stu-id="35f20-387">Creating Types and Members On-Demand</span></span>

<span data-ttu-id="35f20-388">Interfejs API ProvidedType ma opóźnione wersji Dodawanie członka.</span><span class="sxs-lookup"><span data-stu-id="35f20-388">The ProvidedType API has delayed versions of AddMember.</span></span>

```fsharp
  type ProvidedType =
      member AddMemberDelayed  : (unit -> MemberInfo)      -> unit
      member AddMembersDelayed : (unit -> MemberInfo list) -> unit
```

<span data-ttu-id="35f20-389">Te wersje są używane do tworzenia spacje na żądanie typów.</span><span class="sxs-lookup"><span data-stu-id="35f20-389">These versions are used to create on-demand spaces of types.</span></span>

### <a name="providing-array-types-and-generic-type-instantiations"></a><span data-ttu-id="35f20-390">Typy tablic i rodzajowy wystąpień typu</span><span class="sxs-lookup"><span data-stu-id="35f20-390">Providing Array types and Generic Type Instantiations</span></span>

<span data-ttu-id="35f20-391">Tworzenie podanych elementów członkowskich (których podpisów obejmują typy tablic, typów byref i wystąpień typów ogólnych) przy użyciu normalnych `MakeArrayType`, `MakePointerType`, i `MakeGenericType` na dowolne wystąpienie <xref:System.Type>, takie jak `ProvidedTypeDefinitions`.</span><span class="sxs-lookup"><span data-stu-id="35f20-391">You make provided members (whose signatures include array types, byref types, and instantiations of generic types) by using the normal `MakeArrayType`, `MakePointerType`, and `MakeGenericType` on any instance of <xref:System.Type>, including `ProvidedTypeDefinitions`.</span></span>

> [!NOTE]
> <span data-ttu-id="35f20-392">W niektórych przypadkach może być konieczne przy użyciu pomocnika w `ProvidedTypeBuilder.MakeGenericType`.</span><span class="sxs-lookup"><span data-stu-id="35f20-392">In some cases you may have to use the helper in `ProvidedTypeBuilder.MakeGenericType`.</span></span>  <span data-ttu-id="35f20-393">Zobacz [dokumentacji zestawu SDK dostawcy typu](https://github.com/fsprojects/FSharp.TypeProviders.SDK/blob/master/README.md#explicit-construction-of-code-makegenerictype-makegenericmethod-and-uncheckedquotations) więcej szczegółów.</span><span class="sxs-lookup"><span data-stu-id="35f20-393">See the [Type Provider SDK documentation](https://github.com/fsprojects/FSharp.TypeProviders.SDK/blob/master/README.md#explicit-construction-of-code-makegenerictype-makegenericmethod-and-uncheckedquotations) for more details.</span></span>

### <a name="providing-unit-of-measure-annotations"></a><span data-ttu-id="35f20-394">Zapewnianie jednostki miary adnotacji</span><span class="sxs-lookup"><span data-stu-id="35f20-394">Providing Unit of Measure Annotations</span></span>

<span data-ttu-id="35f20-395">Interfejs API ProvidedTypes zapewnia pomocników zapewniające adnotacje miary.</span><span class="sxs-lookup"><span data-stu-id="35f20-395">The ProvidedTypes API provides helpers for providing measure annotations.</span></span> <span data-ttu-id="35f20-396">Na przykład Podaj typ `float<kg>`, użyj następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="35f20-396">For example, to provide the type `float<kg>`, use the following code:</span></span>

```fsharp
  let measures = ProvidedMeasureBuilder.Default
  let kg = measures.SI "kilogram"
  let m = measures.SI "meter"
  let float_kg = measures.AnnotateType(typeof<float>,[kg])
```

  <span data-ttu-id="35f20-397">Aby zapewnić typ `Nullable<decimal<kg/m^2>>`, użyj następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="35f20-397">To provide the type `Nullable<decimal<kg/m^2>>`, use the following code:</span></span>

```fsharp
  let kgpm2 = measures.Ratio(kg, measures.Square m)
  let dkgpm2 = measures.AnnotateType(typeof<decimal>,[kgpm2])
  let nullableDecimal_kgpm2 = typedefof<System.Nullable<_>>.MakeGenericType [|dkgpm2 |]
```

### <a name="accessing-project-local-or-script-local-resources"></a><span data-ttu-id="35f20-398">Uzyskiwanie dostępu do zasobów lokalnych projektu lub lokalnego skryptu</span><span class="sxs-lookup"><span data-stu-id="35f20-398">Accessing Project-Local or Script-Local Resources</span></span>

<span data-ttu-id="35f20-399">Każde wystąpienie dostawcy typów można przydzielić `TypeProviderConfig` wartości podczas konstruowania.</span><span class="sxs-lookup"><span data-stu-id="35f20-399">Each instance of a type provider can be given a `TypeProviderConfig` value during construction.</span></span> <span data-ttu-id="35f20-400">Ta wartość zawiera "folder rozwiązania" dla dostawcy (oznacza to, że folder projektu dla kompilacji lub katalog, który zawiera skrypt), na liście zestawów występujących w odwołaniach i inne informacje.</span><span class="sxs-lookup"><span data-stu-id="35f20-400">This value contains the "resolution folder" for the provider (that is, the project folder for the compilation or the directory that contains a script), the list of referenced assemblies, and other information.</span></span>

### <a name="invalidation"></a><span data-ttu-id="35f20-401">Unieważnienie</span><span class="sxs-lookup"><span data-stu-id="35f20-401">Invalidation</span></span>

<span data-ttu-id="35f20-402">Dostawców może wiązać się z sygnałów unieważniania powiadomić usługi języka F #, który mógł ulec zmianie założeń schematu.</span><span class="sxs-lookup"><span data-stu-id="35f20-402">Providers can raise invalidation signals to notify the F# language service that the schema assumptions may have changed.</span></span> <span data-ttu-id="35f20-403">W przypadku unieważniania typecheck jest ponownie wykonać, jeśli dostawca jest obsługiwana w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="35f20-403">When invalidation occurs, a typecheck is redone if the provider is being hosted in Visual Studio.</span></span> <span data-ttu-id="35f20-404">Sygnał ten zostanie zignorowany, gdy dostawca jest obsługiwane w F # Interactive lub przez kompilator języka F # (fsc.exe).</span><span class="sxs-lookup"><span data-stu-id="35f20-404">This signal will be ignored when the provider is hosted in F# Interactive or by the F# Compiler (fsc.exe).</span></span>

### <a name="caching-schema-information"></a><span data-ttu-id="35f20-405">Buforowanie informacji o schemacie</span><span class="sxs-lookup"><span data-stu-id="35f20-405">Caching Schema Information</span></span>

<span data-ttu-id="35f20-406">Dostawców, często pamięci podręcznej dostęp do informacji o schemacie.</span><span class="sxs-lookup"><span data-stu-id="35f20-406">Providers must often cache access to schema information.</span></span> <span data-ttu-id="35f20-407">Buforowane dane powinny być przechowywane przy użyciu podanej nazwy pliku, jako parametr statyczny lub dane użytkownika.</span><span class="sxs-lookup"><span data-stu-id="35f20-407">The cached data should be stored by using a file name that's given as a static parameter or as user data.</span></span> <span data-ttu-id="35f20-408">Na przykład z pamięci podręcznej schematu `LocalSchemaFile` parametru w pomocy dostawcy typów w `FSharp.Data.TypeProviders` zestawu.</span><span class="sxs-lookup"><span data-stu-id="35f20-408">An example of schema caching is the `LocalSchemaFile` parameter in the type providers in the `FSharp.Data.TypeProviders` assembly.</span></span> <span data-ttu-id="35f20-409">W celu wykonania tych dostawców ten parametr statyczny kieruje typ dostawcy do użycia informacji o schemacie w określonym pliku lokalnego zamiast dostępu do źródła danych za pośrednictwem sieci.</span><span class="sxs-lookup"><span data-stu-id="35f20-409">In the implementation of these providers, this static parameter directs the type provider to use the schema information in the specified local file instead of accessing the data source over the network.</span></span> <span data-ttu-id="35f20-410">Aby użyć buforowanych informacji o schemacie, należy także ustawić parametr statyczny `ForceUpdate` do `false`.</span><span class="sxs-lookup"><span data-stu-id="35f20-410">To use cached schema information, you must also set the static parameter `ForceUpdate` to `false`.</span></span> <span data-ttu-id="35f20-411">Aby włączyć dostęp do danych w trybie online i jest w trybie offline, można użyć technika podobne.</span><span class="sxs-lookup"><span data-stu-id="35f20-411">You could use a similar technique to enable online and offline data access.</span></span>

### <a name="backing-assembly"></a><span data-ttu-id="35f20-412">Tworzenie kopii zestawu</span><span class="sxs-lookup"><span data-stu-id="35f20-412">Backing Assembly</span></span>

<span data-ttu-id="35f20-413">Podczas kompilowania `.dll` lub `.exe` plik, tworzenie kopii pliku dll statycznie połączonej wygenerowane typy do wynikowego zestawu.</span><span class="sxs-lookup"><span data-stu-id="35f20-413">When you compile a `.dll` or `.exe` file, the backing .dll file for generated types is statically linked into the resulting assembly.</span></span> <span data-ttu-id="35f20-414">Ten link jest tworzony przez skopiowanie definicje typów języku pośrednim (IL) i wszystkie zarządzane zasoby z zestawu zapasowy w zestawie końcowym.</span><span class="sxs-lookup"><span data-stu-id="35f20-414">This link is created by copying the Intermediate Language (IL) type definitions and any managed resources from the backing assembly into the final assembly.</span></span> <span data-ttu-id="35f20-415">Korzystając z narzędzia F # Interactive, tworzenie kopii pliku dll nie jest kopiowana i zamiast tego zostanie załadowana bezpośrednio do proces narzędzia F # Interactive.</span><span class="sxs-lookup"><span data-stu-id="35f20-415">When you use F# Interactive, the backing .dll file isn't copied and is instead loaded directly into the F# Interactive process.</span></span>

### <a name="exceptions-and-diagnostics-from-type-providers"></a><span data-ttu-id="35f20-416">Wyjątki i Diagnostyka z dostawcami typów</span><span class="sxs-lookup"><span data-stu-id="35f20-416">Exceptions and Diagnostics from Type Providers</span></span>

<span data-ttu-id="35f20-417">Wszystkie używa wszystkich elementów członkowskich z udostępnionych typów może zgłaszać wyjątków.</span><span class="sxs-lookup"><span data-stu-id="35f20-417">All uses of all members from provided types may throw exceptions.</span></span> <span data-ttu-id="35f20-418">We wszystkich przypadkach Jeśli typ dostawcy zgłasza wyjątek, kompilator hosta atrybutów błąd do określonego typu dostawcy.</span><span class="sxs-lookup"><span data-stu-id="35f20-418">In all cases, if a type provider throws an exception, the host compiler attributes the error to a specific type provider.</span></span>

- <span data-ttu-id="35f20-419">Typ dostawcy wyjątki nigdy nie powinno spowodować wewnętrzne błędy kompilatora.</span><span class="sxs-lookup"><span data-stu-id="35f20-419">Type provider exceptions should never result in internal compiler errors.</span></span>

- <span data-ttu-id="35f20-420">Dostawcy typów nie może zaraportować ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="35f20-420">Type providers can't report warnings.</span></span>

- <span data-ttu-id="35f20-421">Gdy dostawca typów znajduje się w kompilator języka F # środowiska deweloperskiego F # i F # Interactive, wszystkie wyjątki od tego dostawcy są przechwytywane.</span><span class="sxs-lookup"><span data-stu-id="35f20-421">When a type provider is hosted in the F# compiler, an F# development environment, or F# Interactive, all exceptions from that provider are caught.</span></span> <span data-ttu-id="35f20-422">Właściwości wiadomości jest zawsze tekst błędu, i pojawi się śladów stosu.</span><span class="sxs-lookup"><span data-stu-id="35f20-422">The Message property is always the error text, and no stack trace appears.</span></span> <span data-ttu-id="35f20-423">Jeśli zamierzasz zgłosić wyjątek, może zgłosić następujące przykłady: `System.NotSupportedException`, `System.IO.IOException`, `System.Exception`.</span><span class="sxs-lookup"><span data-stu-id="35f20-423">If you’re going to throw an exception, you can throw the following examples: `System.NotSupportedException`, `System.IO.IOException`, `System.Exception`.</span></span>

#### <a name="providing-generated-types"></a><span data-ttu-id="35f20-424">Zapewnianie wygenerowane typy</span><span class="sxs-lookup"><span data-stu-id="35f20-424">Providing Generated Types</span></span>

<span data-ttu-id="35f20-425">Do tej pory ten dokument ma wyjaśniono, jak zapewnić wymazanej typów.</span><span class="sxs-lookup"><span data-stu-id="35f20-425">So far, this document has explained how to provide erased types.</span></span> <span data-ttu-id="35f20-426">Umożliwia także mechanizm dostawcy typu w języku F # zapewnienie wygenerowane typy, które są dodawane jako rzeczywiste definicje typów .NET do użytkowników programu.</span><span class="sxs-lookup"><span data-stu-id="35f20-426">You can also use the type provider mechanism in F# to provide generated types, which are added as real .NET type definitions into the users' program.</span></span> <span data-ttu-id="35f20-427">Użytkownik musi odwoływać się do wygenerowanego podane typy przy użyciu definicji typu.</span><span class="sxs-lookup"><span data-stu-id="35f20-427">You must refer to generated provided types by using a type definition.</span></span>

```fsharp
open Microsoft.FSharp.TypeProviders 

type Service = ODataService<"http://services.odata.org/Northwind/Northwind.svc/">
```

<span data-ttu-id="35f20-428">Kod pomocnika 0,2 ProvidedTypes, który wchodzi w skład wersji języka F # 3.0 ma tylko ograniczoną obsługę dostarczanie wygenerowane typy.</span><span class="sxs-lookup"><span data-stu-id="35f20-428">The ProvidedTypes-0.2 helper code that is part of the F# 3.0 release has only limited support for providing generated types.</span></span> <span data-ttu-id="35f20-429">Poniższe instrukcje musi mieć wartość true dla definicji wygenerowanego typu:</span><span class="sxs-lookup"><span data-stu-id="35f20-429">The following statements must be true for a generated type definition:</span></span>

- <span data-ttu-id="35f20-430">`isErased` należy wybrać opcję `false`.</span><span class="sxs-lookup"><span data-stu-id="35f20-430">`isErased` must be set to `false`.</span></span>

- <span data-ttu-id="35f20-431">Wygenerowanego typu musi zostać dodany do nowo utworzone `ProvidedAssembly()`, który reprezentuje kontener dla wygenerowanego kodu fragmentów.</span><span class="sxs-lookup"><span data-stu-id="35f20-431">The generated type must be added to a newly constructed `ProvidedAssembly()`, which represents a container for generated code fragments.</span></span>

- <span data-ttu-id="35f20-432">Dostawca musi mieć zestawu, który ma zapasowy rzeczywisty plik dll .NET z odpowiedniego pliku dll na dysku.</span><span class="sxs-lookup"><span data-stu-id="35f20-432">The provider must have an assembly that has an actual backing .NET .dll file with a matching .dll file on disk.</span></span>


## <a name="rules-and-limitations"></a><span data-ttu-id="35f20-433">Reguły i ograniczenia</span><span class="sxs-lookup"><span data-stu-id="35f20-433">Rules and Limitations</span></span>

<span data-ttu-id="35f20-434">Podczas pisania dostawców typów pamiętać poniższe reguły i ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="35f20-434">When you write type providers, keep the following rules and limitations in mind.</span></span>


### <a name="provided-types-must-be-reachable"></a><span data-ttu-id="35f20-435">Podane typy muszą być dostępny</span><span class="sxs-lookup"><span data-stu-id="35f20-435">Provided types must be reachable</span></span>

<span data-ttu-id="35f20-436">Wszystkie pod warunkiem, że typy, powinny być dostępne z typów-nested.</span><span class="sxs-lookup"><span data-stu-id="35f20-436">All provided types should be reachable from the non-nested types.</span></span> <span data-ttu-id="35f20-437">Zagnieżdżone typy są podane w wywołaniu `TypeProviderForNamespaces` konstruktora lub wywołanie `AddNamespace`.</span><span class="sxs-lookup"><span data-stu-id="35f20-437">The non-nested types are given in the call to the `TypeProviderForNamespaces` constructor or a call to `AddNamespace`.</span></span> <span data-ttu-id="35f20-438">Na przykład, jeśli dostawca miejsce na wpisanie `StaticClass.P : T`, należy upewnić się czy T jest typu niezagnieżdżonego lub zagnieżdżona pod jedną.</span><span class="sxs-lookup"><span data-stu-id="35f20-438">For example, if the provider provides a type `StaticClass.P : T`, you must ensure that T is either a non-nested type or nested under one.</span></span>

<span data-ttu-id="35f20-439">Na przykład niektóre dostawców ma klasie statycznej takich jak `DataTypes` zawierających te `T1, T2, T3, ...` typów.</span><span class="sxs-lookup"><span data-stu-id="35f20-439">For example, some providers have a static class such as `DataTypes` that contain these `T1, T2, T3, ...` types.</span></span> <span data-ttu-id="35f20-440">W przeciwnym razie błąd mówi, że odwołanie do typu T w zestawie A został znaleziony, ale nie można znaleźć typu w tym zestawie.</span><span class="sxs-lookup"><span data-stu-id="35f20-440">Otherwise, the error says that a reference to type T in assembly A was found, but the type couldn't be found in that assembly.</span></span> <span data-ttu-id="35f20-441">Jeśli ten błąd pojawia się, sprawdź, czy wszystkie Twoje podtypy jest osiągalna z dostawcy typów.</span><span class="sxs-lookup"><span data-stu-id="35f20-441">If this error appears, verify that all your subtypes can be reached from the provider types.</span></span> <span data-ttu-id="35f20-442">Uwaga: Te `T1, T2, T3...` typy są określane jako *na bieżąco* typów.</span><span class="sxs-lookup"><span data-stu-id="35f20-442">Note: These `T1, T2, T3...` types are referred to as the *on-the-fly* types.</span></span> <span data-ttu-id="35f20-443">Pamiętaj, aby umieścić je w dostępny obszar nazw lub typ nadrzędny.</span><span class="sxs-lookup"><span data-stu-id="35f20-443">Remember to put them in an accessible namespace or a parent type.</span></span>

### <a name="limitations-of-the-type-provider-mechanism"></a><span data-ttu-id="35f20-444">Ograniczenia mechanizmu typ dostawcy</span><span class="sxs-lookup"><span data-stu-id="35f20-444">Limitations of the Type Provider Mechanism</span></span>

<span data-ttu-id="35f20-445">Mechanizm dostawcy typów F # ma następujące ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="35f20-445">The type provider mechanism in F# has the following limitations:</span></span>

- <span data-ttu-id="35f20-446">Podstawowa architektura dla dostawców typów w języku F # nie obsługuje pod warunkiem ogólne typy lub podać metody ogólne.</span><span class="sxs-lookup"><span data-stu-id="35f20-446">The underlying infrastructure for type providers in F# doesn't support provided generic types or provided generic methods.</span></span>

- <span data-ttu-id="35f20-447">Mechanizm nie obsługuje zagnieżdżonych typów z parametrów statycznych.</span><span class="sxs-lookup"><span data-stu-id="35f20-447">The mechanism doesn't support nested types with static parameters.</span></span>

## <a name="development-tips"></a><span data-ttu-id="35f20-448">Porady dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="35f20-448">Development Tips</span></span>

<span data-ttu-id="35f20-449">Poniższe porady mogą przyda podczas procesu projektowania.</span><span class="sxs-lookup"><span data-stu-id="35f20-449">You might find the following tips helpful during the development process.</span></span>

### <a name="run-two-instances-of-visual-studio"></a><span data-ttu-id="35f20-450">Uruchom dwa wystąpienia programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="35f20-450">Run Two Instances of Visual Studio</span></span>

<span data-ttu-id="35f20-451">Mogą tworzyć dostawca typów w jednym wystąpieniu i test dostawcy w innym, ponieważ testów IDE zajmie blokady na plik .dll, który uniemożliwia typ dostawcy zostanie odbudowany.</span><span class="sxs-lookup"><span data-stu-id="35f20-451">You can develop the type provider in one instance and test the provider in the other because the test IDE will take a lock on the .dll file that prevents the type provider from being rebuilt.</span></span> <span data-ttu-id="35f20-452">W związku z tym należy zamknąć drugie wystąpienie programu Visual Studio, gdy dostawca jest wbudowana w pierwszej kolejności, a następnie po utworzeniu dostawcy musi Otwórz drugie wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="35f20-452">Thus, you must close the second instance of Visual Studio while the provider is built in the first instance, and then you must reopen the second instance after the provider is built.</span></span>

### <a name="debug-type-providers-by-using-invocations-of-fscexe"></a><span data-ttu-id="35f20-453">Debugowanie za pomocą wywołania fsc.exe dostawców typów</span><span class="sxs-lookup"><span data-stu-id="35f20-453">Debug type providers by using invocations of fsc.exe</span></span>

<span data-ttu-id="35f20-454">Dostawcy typów można wywołać za pomocą następujących narzędzi:</span><span class="sxs-lookup"><span data-stu-id="35f20-454">You can invoke type providers by using the following tools:</span></span>

- <span data-ttu-id="35f20-455">FSC.exe (F # wiersza polecenia kompilatora)</span><span class="sxs-lookup"><span data-stu-id="35f20-455">fsc.exe (The F# command line compiler)</span></span>

- <span data-ttu-id="35f20-456">fsi.exe (kompilator F # Interactive)</span><span class="sxs-lookup"><span data-stu-id="35f20-456">fsi.exe (The F# Interactive compiler)</span></span>

- <span data-ttu-id="35f20-457">Devenv.exe (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="35f20-457">devenv.exe (Visual Studio)</span></span>

<span data-ttu-id="35f20-458">Dostawcy typów można debugować często najłatwiej przy użyciu fsc.exe w pliku skryptu testu (na przykład script.fsx).</span><span class="sxs-lookup"><span data-stu-id="35f20-458">You can often debug type providers most easily by using fsc.exe on a test script file (for example, script.fsx).</span></span> <span data-ttu-id="35f20-459">Można uruchomić debugera z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="35f20-459">You can launch a debugger from a command prompt.</span></span>

```
  devenv /debugexe fsc.exe script.fsx
```

  <span data-ttu-id="35f20-460">Możesz użyć rejestrowania drukowania do stdout.</span><span class="sxs-lookup"><span data-stu-id="35f20-460">You can use print-to-stdout logging.</span></span>


## <a name="see-also"></a><span data-ttu-id="35f20-461">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="35f20-461">See Also</span></span>

* [<span data-ttu-id="35f20-462">Dostawcy typów</span><span class="sxs-lookup"><span data-stu-id="35f20-462">Type Providers</span></span>](index.md)

* [<span data-ttu-id="35f20-463">Typ dostawcy zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="35f20-463">The Type Provider SDK</span></span>](https://github.com/fsprojects/FSharp.TypeProviders.SDK)

