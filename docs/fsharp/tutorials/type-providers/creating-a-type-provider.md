---
title: 'Samouczek: Tworzenie dostawcy typów (F #)'
description: 'Dowiedz się, jak utworzyć własne dostawcy typów F # w F # 3.0, sprawdzając kilku dostawców typu prostego, w celu zilustrowania podstawowych koncepcji.'
ms.date: 05/16/2016
ms.openlocfilehash: 3c998377b2c3a408d536ef416f3799bf7f04b6bd
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43745729"
---
# <a name="tutorial-create-a-type-provider"></a><span data-ttu-id="ae76e-103">Samouczek: Tworzenie dostawcy typów</span><span class="sxs-lookup"><span data-stu-id="ae76e-103">Tutorial: Create a Type Provider</span></span>

<span data-ttu-id="ae76e-104">Mechanizm dostawcy typu F # jest znaczna część jej obsługę programowania zaawansowanych informacji.</span><span class="sxs-lookup"><span data-stu-id="ae76e-104">The type provider mechanism in F# is a significant part of its support for information rich programming.</span></span> <span data-ttu-id="ae76e-105">W tym samouczku opisano sposób tworzenia własnych dostawców typów, prowadzące przez proces tworzenia kilku dostawców typu prostego, w celu zilustrowania podstawowych koncepcji.</span><span class="sxs-lookup"><span data-stu-id="ae76e-105">This tutorial explains how to create your own type providers by walking you through the development of several simple type providers to illustrate the basic concepts.</span></span> <span data-ttu-id="ae76e-106">Aby uzyskać więcej informacji na temat mechanizmu dostawcy typu F #, zobacz [dostawców typów](index.md).</span><span class="sxs-lookup"><span data-stu-id="ae76e-106">For more information about the type provider mechanism in F#, see [Type Providers](index.md).</span></span>

<span data-ttu-id="ae76e-107">Ekosystem F # zawiera szeroką gamę dostawców typów dla często używanych internetowych i firmowych usług danych.</span><span class="sxs-lookup"><span data-stu-id="ae76e-107">The F# ecosystem contains a range of type providers for commonly used Internet and enterprise data services.</span></span> <span data-ttu-id="ae76e-108">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="ae76e-108">For example:</span></span>

- <span data-ttu-id="ae76e-109">[FSharp.Data](https://fsharp.github.io/FSharp.Data/) obejmuje dostawców typów dla formatu JSON, XML, CSV i HTML dokumentu formatów.</span><span class="sxs-lookup"><span data-stu-id="ae76e-109">[FSharp.Data](https://fsharp.github.io/FSharp.Data/) includes type providers for JSON, XML, CSV and HTML document formats.</span></span>

- <span data-ttu-id="ae76e-110">[SQLProvider](https://fsprojects.github.io/SQLProvider/) udostępnia silnie typizowane baz danych SQL za pomocą mapowanie obiektów i LINQ języka F # zapytań dotyczących tych źródeł danych.</span><span class="sxs-lookup"><span data-stu-id="ae76e-110">[SQLProvider](https://fsprojects.github.io/SQLProvider/) provides strongly-typed access to SQL databases through a object mapping and F# LINQ queries against these data sources.</span></span>

- <span data-ttu-id="ae76e-111">[FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) zestaw dostawców typów dla kompilacji zaewidencjonowanego osadzania T-SQL w języku F #.</span><span class="sxs-lookup"><span data-stu-id="ae76e-111">[FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) has a set of type providers for compile-time checked embedding of T-SQL in F#.</span></span>

- <span data-ttu-id="ae76e-112">[FSharp.Data.TypeProviders](https://fsprojects.github.io/FSharp.Data.TypeProviders/) to starszy zestaw dostawców typów do użycia tylko w programowaniu .NET Framework do uzyskiwania dostępu do usługi danych SQL, platformy Entity Framework, OData i WSDL.</span><span class="sxs-lookup"><span data-stu-id="ae76e-112">[FSharp.Data.TypeProviders](https://fsprojects.github.io/FSharp.Data.TypeProviders/) is an older set of type providers for use only with .NET Framework programming for accessing SQL, Entity Framework, OData and WSDL data services.</span></span>

<span data-ttu-id="ae76e-113">W przypadku, gdy to konieczne, można tworzyć niestandardowych dostawców typów, lub możesz odwoływać się do dostawców typów, utworzone przez innych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="ae76e-113">Where necessary, you can create custom type providers, or you can reference type providers that others have created.</span></span> <span data-ttu-id="ae76e-114">Na przykład organizacja może mieć usługi danych, która zapewnia duży i rosnący liczbę nazwanych zestawów danych, każdy z swój własny stabilny schemat danych.</span><span class="sxs-lookup"><span data-stu-id="ae76e-114">For example, your organization could have a data service that provides a large and growing number of named data sets, each with its own stable data schema.</span></span> <span data-ttu-id="ae76e-115">Możesz utworzyć dostawcę typów, który odczytuje te schematy i przedstawia informacje o bieżącym zestawów danych do programisty należy w silnie typizowany sposób.</span><span class="sxs-lookup"><span data-stu-id="ae76e-115">You can create a type provider that reads the schemas and presents the current data sets to the programmer in a strongly typed way.</span></span>

## <a name="before-you-start"></a><span data-ttu-id="ae76e-116">Przed rozpoczęciem</span><span class="sxs-lookup"><span data-stu-id="ae76e-116">Before You Start</span></span>

<span data-ttu-id="ae76e-117">Mechanizm dostawcy typu jest przeznaczony głównie do wprowadza stabilnych danych i miejsca do magazynowania usługi informacji do programowania środowiska F #.</span><span class="sxs-lookup"><span data-stu-id="ae76e-117">The type provider mechanism is primarily designed for injecting stable data and service information spaces into the F# programming experience.</span></span>

<span data-ttu-id="ae76e-118">Ten mechanizm nie jest przeznaczona dla wprowadzanie informacji miejsca do magazynowania, którego schemat zmienia się podczas wykonywania programu, w sposób, które mają zastosowanie do logiki programu.</span><span class="sxs-lookup"><span data-stu-id="ae76e-118">This mechanism isn’t designed for injecting information spaces whose schema changes during program execution in ways that are relevant to program logic.</span></span> <span data-ttu-id="ae76e-119">Również mechanizm nie jest przeznaczona dla meta-programowania wewnątrz języka, mimo że tej domeny zawiera niektóre prawidłowego użycia.</span><span class="sxs-lookup"><span data-stu-id="ae76e-119">Also, the mechanism isn't designed for intra-language meta-programming, even though that domain contains some valid uses.</span></span> <span data-ttu-id="ae76e-120">Ten mechanizm należy używać tylko wtedy, gdy jest to konieczne, i gdzie tworzenie dostawcy typów daje bardzo duża wartość.</span><span class="sxs-lookup"><span data-stu-id="ae76e-120">You should use this mechanism only where necessary and where the development of a type provider yields very high value.</span></span>

<span data-ttu-id="ae76e-121">Należy unikać pisania dostawcy typów, których schemat jest niedostępna.</span><span class="sxs-lookup"><span data-stu-id="ae76e-121">You should avoid writing a type provider where a schema isn't available.</span></span> <span data-ttu-id="ae76e-122">Podobnie, należy unikać pisania dostawcę typów, w przypadku, gdy zwykłej (lub nawet istniejącego) biblioteki .NET będą wystarczające.</span><span class="sxs-lookup"><span data-stu-id="ae76e-122">Likewise, you should avoid writing a type provider where an ordinary (or even an existing) .NET library would suffice.</span></span>

<span data-ttu-id="ae76e-123">Przed rozpoczęciem może odpowiedzieć na następujące pytania:</span><span class="sxs-lookup"><span data-stu-id="ae76e-123">Before you start, you might ask the following questions:</span></span>

- <span data-ttu-id="ae76e-124">Czy masz schematu dla źródła informacji?</span><span class="sxs-lookup"><span data-stu-id="ae76e-124">Do you have a schema for your information source?</span></span> <span data-ttu-id="ae76e-125">Jeśli tak, co to jest mapowanie języka F # i .NET typu systemu?</span><span class="sxs-lookup"><span data-stu-id="ae76e-125">If so, what’s the mapping into the F# and .NET type system?</span></span>

- <span data-ttu-id="ae76e-126">Można użyć istniejącego interfejsu API (o typach określanych dynamicznie) jako punktu wyjścia dla wdrożenia?</span><span class="sxs-lookup"><span data-stu-id="ae76e-126">Can you use an existing (dynamically typed) API as a starting point for your implementation?</span></span>

- <span data-ttu-id="ae76e-127">Ty i Twoja organizacja ma wystarczającą ilość użycia dostawcy typów, które umożliwiają zapisywanie zwiększonej?</span><span class="sxs-lookup"><span data-stu-id="ae76e-127">Will you and your organization have enough uses of the type provider to make writing it worthwhile?</span></span> <span data-ttu-id="ae76e-128">Czy normalne biblioteki .NET potrzeb?</span><span class="sxs-lookup"><span data-stu-id="ae76e-128">Would a normal .NET library meet your needs?</span></span>

- <span data-ttu-id="ae76e-129">Ile zmieni się schematu</span><span class="sxs-lookup"><span data-stu-id="ae76e-129">How much will your schema change?</span></span>

- <span data-ttu-id="ae76e-130">Zostanie ona zmieniona podczas kodowania?</span><span class="sxs-lookup"><span data-stu-id="ae76e-130">Will it change during coding?</span></span>

- <span data-ttu-id="ae76e-131">Ją zmieni się między sesjami kodowania?</span><span class="sxs-lookup"><span data-stu-id="ae76e-131">Will it change between coding sessions?</span></span>

- <span data-ttu-id="ae76e-132">Zostanie ona zmieniona podczas wykonywania programu?</span><span class="sxs-lookup"><span data-stu-id="ae76e-132">Will it change during program execution?</span></span>

<span data-ttu-id="ae76e-133">Dostawcy typów są najlepiej sprawdza się w sytuacjach, gdy schemat jest stabilna, w czasie wykonywania, jak i w okresie istnienia skompilowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="ae76e-133">Type providers are best suited to situations where the schema is stable at runtime and during the lifetime of compiled code.</span></span>

## <a name="a-simple-type-provider"></a><span data-ttu-id="ae76e-134">Dostawca typu prostego</span><span class="sxs-lookup"><span data-stu-id="ae76e-134">A Simple Type Provider</span></span>

<span data-ttu-id="ae76e-135">Te przykładowe dane stanowią Samples.HelloWorldTypeProvider podobne do próbek w `examples` katalogu [SDK dostawcy typu F #](https://github.com/fsprojects/FSharp.TypeProviders.SDK/).</span><span class="sxs-lookup"><span data-stu-id="ae76e-135">This sample is Samples.HelloWorldTypeProvider, similar to the samples in the `examples` directory of the [F# Type Provider SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK/).</span></span> <span data-ttu-id="ae76e-136">Dostawca udostępnia "przestrzenią typu", która zawiera 100 typów wymazane, co ilustruje poniższy kod, używając składni Sygnatura F # i pomijanie szczegóły wszystkie z wyjątkiem `Type1`.</span><span class="sxs-lookup"><span data-stu-id="ae76e-136">The provider makes available a "type space" that contains 100 erased types, as the following code shows by using F# signature syntax and omitting the details for all except `Type1`.</span></span> <span data-ttu-id="ae76e-137">Aby uzyskać więcej informacji na temat typów wymazane, zobacz [szczegółowe informacje o wymazane podane typy](#details-about-erased-provided-types) w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="ae76e-137">For more information about erased types, see [Details About Erased Provided Types](#details-about-erased-provided-types) later in this topic.</span></span>

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

<span data-ttu-id="ae76e-138">Należy pamiętać, że zestaw typów i członków, pod warunkiem jest znany statycznie.</span><span class="sxs-lookup"><span data-stu-id="ae76e-138">Note that the set of types and members provided is statically known.</span></span> <span data-ttu-id="ae76e-139">W tym przykładzie nie korzystać z możliwości dostawców typów, które są zależne od schematu.</span><span class="sxs-lookup"><span data-stu-id="ae76e-139">This example doesn't leverage the ability of providers to provide types that depend on a schema.</span></span> <span data-ttu-id="ae76e-140">Implementacja dostawcy typów jest opisany w następującym kodzie i szczegółowe informacje znajdują się w kolejnych sekcjach tego tematu.</span><span class="sxs-lookup"><span data-stu-id="ae76e-140">The implementation of the type provider is outlined in the following code, and the details are covered in later sections of this topic.</span></span>

>[!WARNING]
<span data-ttu-id="ae76e-141">Może to być różnice między tym kodem i przykładów online.</span><span class="sxs-lookup"><span data-stu-id="ae76e-141">There may be differences between this code and the online samples.</span></span>

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

<span data-ttu-id="ae76e-142">Użyj tego dostawcy, otwórz osobnego wystąpienia programu Visual Studio, utworzyć skrypt F #, a następnie dodaj odwołanie do dostawcy ze skryptu przy użyciu #r, co ilustruje poniższy kod:</span><span class="sxs-lookup"><span data-stu-id="ae76e-142">To use this provider, open a separate instance of Visual Studio, create an F# script, and then add a reference to the provider from your script by using #r as the following code shows:</span></span>

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

<span data-ttu-id="ae76e-143">Następnie poszukaj typów pod `Samples.HelloWorldTypeProvider` przestrzeni nazw, który wygenerował dostawcy typów.</span><span class="sxs-lookup"><span data-stu-id="ae76e-143">Then look for the types under the `Samples.HelloWorldTypeProvider` namespace that the type provider generated.</span></span>

<span data-ttu-id="ae76e-144">Przed ponownym skompilowaniem dostawcy, upewnij się, zamknęli wszystkie wystąpienia programu Visual Studio i F # Interactive, które korzystają z biblioteki DLL dostawcy.</span><span class="sxs-lookup"><span data-stu-id="ae76e-144">Before you recompile the provider, make sure that you have closed all instances of Visual Studio and F# Interactive that are using the provider DLL.</span></span> <span data-ttu-id="ae76e-145">W przeciwnym razie wystąpi błąd kompilacji ponieważ dane wyjściowe biblioteki DLL będzie zablokowany.</span><span class="sxs-lookup"><span data-stu-id="ae76e-145">Otherwise, a build error will occur because the output DLL will be locked.</span></span>

<span data-ttu-id="ae76e-146">Aby debugować ten dostawca za pomocą instrukcji drukowania, wprowadź skrypt, który opisuje problem z dostawcą, a następnie użyj poniższego kodu:</span><span class="sxs-lookup"><span data-stu-id="ae76e-146">To debug this provider by using print statements, make a script that exposes a problem with the provider, and then use the following code:</span></span>

```fsharp
fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

<span data-ttu-id="ae76e-147">Aby debugować tego dostawcę przy użyciu programu Visual Studio, otwórz wiersz polecenia programu Visual Studio przy użyciu poświadczeń administracyjnych i uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="ae76e-147">To debug this provider by using Visual Studio, open the Visual Studio command prompt with administrative credentials, and run the following command:</span></span>

```fsharp
devenv.exe /debugexe fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

<span data-ttu-id="ae76e-148">Jako alternatywę, Otwórz program Visual Studio, otwórz menu debugowanie, wybierz polecenie `Debug/Attach to process…`i Dołącz do innego `devenv` proces, w którym edycji skrypt.</span><span class="sxs-lookup"><span data-stu-id="ae76e-148">As an alternative, open Visual Studio, open the Debug menu, choose `Debug/Attach to process…`, and attach to another `devenv` process where you’re editing your script.</span></span> <span data-ttu-id="ae76e-149">Za pomocą tej metody, można łatwiej wskazać konkretnego węzła logicznego w dostawcy typów interaktywnie wpisując wyrażenia do drugiego wystąpienia (z pełną obsługą technologii IntelliSense i inne funkcje).</span><span class="sxs-lookup"><span data-stu-id="ae76e-149">By using this method, you can more easily target particular logic in the type provider by interactively typing expressions into the second instance (with full IntelliSense and other features).</span></span>

<span data-ttu-id="ae76e-150">Można wyłączyć opcję tylko mój kod, debugowanie, aby lepiej identyfikację błędów występujących w wygenerowanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="ae76e-150">You can disable Just My Code debugging to better identify errors in generated code.</span></span> <span data-ttu-id="ae76e-151">Aby dowiedzieć się, jak włączyć lub wyłączyć tę funkcję, zobacz [nawigowanie po kodzie za pomocą debugera za](/visualstudio/debugger/navigating-through-code-with-the-debugger).</span><span class="sxs-lookup"><span data-stu-id="ae76e-151">For information about how to enable or disable this feature, see [Navigating through Code with the Debugger](/visualstudio/debugger/navigating-through-code-with-the-debugger).</span></span> <span data-ttu-id="ae76e-152">Ponadto można również ustawić wyjątku pierwszej szansy przechwytywanie, otwierając `Debug` menu, a następnie wybierając `Exceptions` lub wybierając klawisze Ctrl + Alt + E, aby otworzyć `Exceptions` okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="ae76e-152">Also, you can also set first-chance exception catching by opening the `Debug` menu and then choosing `Exceptions` or by choosing the Ctrl+Alt+E keys to open the `Exceptions` dialog box.</span></span> <span data-ttu-id="ae76e-153">W tym oknie dialogowym w obszarze `Common Language Runtime Exceptions`, wybierz opcję `Thrown` pole wyboru.</span><span class="sxs-lookup"><span data-stu-id="ae76e-153">In that dialog box, under `Common Language Runtime Exceptions`, select the `Thrown` check box.</span></span>

### <a name="implementation-of-the-type-provider"></a><span data-ttu-id="ae76e-154">Implementacja dostawcy typów</span><span class="sxs-lookup"><span data-stu-id="ae76e-154">Implementation of the Type Provider</span></span>

<span data-ttu-id="ae76e-155">Ta sekcja przeprowadzi Cię przez główne sekcji implementacja dostawcy typu.</span><span class="sxs-lookup"><span data-stu-id="ae76e-155">This section walks you through the principal sections of the type provider implementation.</span></span> <span data-ttu-id="ae76e-156">Najpierw należy zdefiniować typ dostawcy niestandardowego typu, samego programu:</span><span class="sxs-lookup"><span data-stu-id="ae76e-156">First, you define the type for the custom type provider itself:</span></span>

```fsharp
[<TypeProvider>]
type SampleTypeProvider(config: TypeProviderConfig) as this =
```

<span data-ttu-id="ae76e-157">Tego typu muszą być publiczne i należy go oznaczyć [TypeProvider](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947) atrybutu, aby kompilator, rozpoznawał dostawcę typów, gdy oddzielny projekt języka F # odwołuje się do zestawu, który zawiera typu.</span><span class="sxs-lookup"><span data-stu-id="ae76e-157">This type must be public, and you must mark it with the [TypeProvider](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947) attribute so that the compiler will recognize the type provider when a separate F# project references the assembly that contains the type.</span></span> <span data-ttu-id="ae76e-158">*Config* parametr jest opcjonalny i, jeśli jest obecny, zawiera informacje o konfiguracji kontekstowych wystąpienia dostawcy typu, który tworzy kompilatora języka F #.</span><span class="sxs-lookup"><span data-stu-id="ae76e-158">The *config* parameter is optional, and, if present, contains contextual configuration information for the type provider instance that the F# compiler creates.</span></span>

<span data-ttu-id="ae76e-159">Następnie możesz wdrożyć [itypeprovider —](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="ae76e-159">Next, you implement the [ITypeProvider](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f) interface.</span></span> <span data-ttu-id="ae76e-160">W tym przypadku używasz `TypeProviderForNamespaces` typ z `ProvidedTypes` API jako typu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="ae76e-160">In this case, you use the `TypeProviderForNamespaces` type from the `ProvidedTypes` API as a base type.</span></span> <span data-ttu-id="ae76e-161">Tego typu pomocnika zapewniają skończoną zbiór eagerly, pod warunkiem przestrzeni nazw, z których każdy bezpośrednio zawiera skończoną liczbę stałej, eagerly dostarczone typy.</span><span class="sxs-lookup"><span data-stu-id="ae76e-161">This helper type can provide a finite collection of eagerly provided namespaces, each of which directly contains a finite number of fixed, eagerly provided types.</span></span> <span data-ttu-id="ae76e-162">W tym kontekście, dostawca *eagerly* generuje typy, nawet jeśli nie są potrzebne lub używane.</span><span class="sxs-lookup"><span data-stu-id="ae76e-162">In this context, the provider *eagerly* generates types even if they aren't needed or used.</span></span>

```fsharp
inherit TypeProviderForNamespaces(config)
```

<span data-ttu-id="ae76e-163">Następnie zdefiniuj lokalnego wartości prywatne, które określają przestrzeń nazw dla podane typy i Znajdź samego montażu dostawcy typu.</span><span class="sxs-lookup"><span data-stu-id="ae76e-163">Next, define local private values that specify the namespace for the provided types, and find the type provider assembly itself.</span></span> <span data-ttu-id="ae76e-164">Ten zestaw jest później używany jako typ logiczny nadrzędnego wymazane typów, które są dostarczane.</span><span class="sxs-lookup"><span data-stu-id="ae76e-164">This assembly is used later as the logical parent type of the erased types that are provided.</span></span>

```fsharp
let namespaceName = "Samples.HelloWorldTypeProvider"
let thisAssembly = Assembly.GetExecutingAssembly()
```

<span data-ttu-id="ae76e-165">Następnie należy utworzyć funkcję, aby zapewnić każdego typu Type1... Type100.</span><span class="sxs-lookup"><span data-stu-id="ae76e-165">Next, create a function to provide each of the types Type1…Type100.</span></span> <span data-ttu-id="ae76e-166">Ta funkcja jest omówione bardziej szczegółowo w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="ae76e-166">This function is explained in more detail later in this topic.</span></span>

```fsharp
let makeOneProvidedType (n:int) = …
```

<span data-ttu-id="ae76e-167">Kolejny krok to Generowanie 100 podane typy:</span><span class="sxs-lookup"><span data-stu-id="ae76e-167">Next, generate the 100 provided types:</span></span>

```fsharp
let types = [ for i in 1 .. 100 -> makeOneProvidedType i ]
```

<span data-ttu-id="ae76e-168">Następnie dodaj typy podanej przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="ae76e-168">Next, add the types as a provided namespace:</span></span>

```fsharp
do this.AddNamespace(namespaceName, types)
```

<span data-ttu-id="ae76e-169">Na koniec należy dodać atrybut zestawu, który wskazuje, tworzysz dostawcę wpisz biblioteki DLL:</span><span class="sxs-lookup"><span data-stu-id="ae76e-169">Finally, add an assembly attribute that indicates that you are creating a type provider DLL:</span></span>

```fsharp
[<assembly:TypeProviderAssembly>] 
do()
```

### <a name="providing-one-type-and-its-members"></a><span data-ttu-id="ae76e-170">Zapewnienie jednego typu i jej elementów członkowskich</span><span class="sxs-lookup"><span data-stu-id="ae76e-170">Providing One Type And Its Members</span></span>

<span data-ttu-id="ae76e-171">`makeOneProvidedType` Funkcja wykonuje rzeczywistą pracę, zapewniając jeden z typów.</span><span class="sxs-lookup"><span data-stu-id="ae76e-171">The `makeOneProvidedType` function does the real work of providing one of the types.</span></span>

```fsharp
let makeOneProvidedType (n:int) = 
…
```

<span data-ttu-id="ae76e-172">W tym kroku opisano stosowania tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="ae76e-172">This step explains the implementation of this function.</span></span> <span data-ttu-id="ae76e-173">Najpierw utwórz podany typ (na przykład Type1, gdy n = 1 lub Type57, gdy jest to n = 57).</span><span class="sxs-lookup"><span data-stu-id="ae76e-173">First, create the provided type (for example, Type1, when n = 1, or Type57, when n = 57).</span></span>

```fsharp
// This is the provided type. It is an erased provided type and, in compiled code, 
// will appear as type 'obj'.
let t = ProvidedTypeDefinition(thisAssembly, namespaceName,
                               "Type" + string n,
                               baseType = Some typeof<obj>)
```

<span data-ttu-id="ae76e-174">Należy zauważyć następujące kwestie:</span><span class="sxs-lookup"><span data-stu-id="ae76e-174">You should note the following points:</span></span>

- <span data-ttu-id="ae76e-175">To pod warunkiem, że typ są usuwane.</span><span class="sxs-lookup"><span data-stu-id="ae76e-175">This provided type is erased.</span></span>  <span data-ttu-id="ae76e-176">Ponieważ wskazywać, że typ podstawowy jest `obj`, wystąpienia będą wyświetlane jako wartości typu [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) w skompilowany kod.</span><span class="sxs-lookup"><span data-stu-id="ae76e-176">Because you indicate that the base type is `obj`, instances will appear as values of type [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) in compiled code.</span></span>

- <span data-ttu-id="ae76e-177">Po określeniu typu niezagnieżdżonego, należy określić zestawu i przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="ae76e-177">When you specify a non-nested type, you must specify the assembly and namespace.</span></span> <span data-ttu-id="ae76e-178">W przypadku typów wymazane zestawu powinna być samego montażu dostawcy typu.</span><span class="sxs-lookup"><span data-stu-id="ae76e-178">For erased types, the assembly should be the type provider assembly itself.</span></span>

<span data-ttu-id="ae76e-179">Następnie dodaj dokumentacji XML do typu.</span><span class="sxs-lookup"><span data-stu-id="ae76e-179">Next, add XML documentation to the type.</span></span> <span data-ttu-id="ae76e-180">Ta dokumentacja została opóźniona, oznacza to, obliczane na żądanie, jeśli ich potrzebuje kompilatora hosta.</span><span class="sxs-lookup"><span data-stu-id="ae76e-180">This documentation is delayed, that is, computed on-demand if the host compiler needs it.</span></span>

```fsharp
t.AddXmlDocDelayed (fun () -> sprintf "This provided type %s" ("Type" + string n))
```

<span data-ttu-id="ae76e-181">Następnie dodaj podanej właściwości statycznej do typu:</span><span class="sxs-lookup"><span data-stu-id="ae76e-181">Next you add a provided static property to the type:</span></span>

```fsharp
let staticProp = ProvidedProperty(propertyName = "StaticProperty", 
                                  propertyType = typeof<string>, 
                                  isStatic = true,
                                  getterCode = (fun args -> <@@ "Hello!" @@>))
```

<span data-ttu-id="ae76e-182">Wprowadzenie tej właściwości będzie zawsze przyjmowało ciąg "Hello!".</span><span class="sxs-lookup"><span data-stu-id="ae76e-182">Getting this property will always evaluate to the string "Hello!".</span></span> <span data-ttu-id="ae76e-183">`GetterCode` Dla właściwości używa F # oferty, który reprezentuje kod generowany przez kompilator hosta w celu uzyskania właściwości.</span><span class="sxs-lookup"><span data-stu-id="ae76e-183">The `GetterCode` for the property uses an F# quotation, which represents the code that the host compiler generates for getting the property.</span></span> <span data-ttu-id="ae76e-184">Aby uzyskać więcej informacji na temat ofert zobacz [cytaty kodu (F #)](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155).</span><span class="sxs-lookup"><span data-stu-id="ae76e-184">For more information about quotations, see [Code Quotations (F#)](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155).</span></span>

<span data-ttu-id="ae76e-185">Dodaj dokumentacji XML do właściwości.</span><span class="sxs-lookup"><span data-stu-id="ae76e-185">Add XML documentation to the property.</span></span>

```fsharp
staticProp.AddXmlDocDelayed(fun () -> "This is a static property")
```

<span data-ttu-id="ae76e-186">Podane właściwości teraz zostać dołączony do podanego typu.</span><span class="sxs-lookup"><span data-stu-id="ae76e-186">Now attach the provided property to the provided type.</span></span> <span data-ttu-id="ae76e-187">Jeden i tylko jeden typ, należy dołączyć podanego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="ae76e-187">You must attach a provided member to one and only one type.</span></span> <span data-ttu-id="ae76e-188">W przeciwnym razie należy nigdy nie będzie dostępny.</span><span class="sxs-lookup"><span data-stu-id="ae76e-188">Otherwise, the member will never be accessible.</span></span>

```fsharp
t.AddMember staticProp
```

<span data-ttu-id="ae76e-189">Teraz utworzyć podanej Konstruktor, który nie przyjmuje żadnych parametrów.</span><span class="sxs-lookup"><span data-stu-id="ae76e-189">Now create a provided constructor that takes no parameters.</span></span>

```fsharp
let ctor = ProvidedConstructor(parameters = [ ], 
                               invokeCode = (fun args -> <@@ "The object data" :> obj @@>))
```

<span data-ttu-id="ae76e-190">`InvokeCode` Dla konstruktora zwraca F # oferty, który reprezentuje kod, który kompilator hosta generuje podczas wywołania konstruktora.</span><span class="sxs-lookup"><span data-stu-id="ae76e-190">The `InvokeCode` for the constructor returns an F# quotation, which represents the code that the host compiler generates when the constructor is called.</span></span> <span data-ttu-id="ae76e-191">Na przykład można użyć następującego konstruktora:</span><span class="sxs-lookup"><span data-stu-id="ae76e-191">For example, you can use the following constructor:</span></span>

```fsharp
new Type10()
```

<span data-ttu-id="ae76e-192">Wystąpienie podanego typu zostanie utworzony przy użyciu danych bazowych "Dane obiektu".</span><span class="sxs-lookup"><span data-stu-id="ae76e-192">An instance of the provided type will be created with underlying data "The object data".</span></span> <span data-ttu-id="ae76e-193">Cudzysłowie kod zawiera konwersję [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) ponieważ ten typ jest skasowanie to podany typ (jak określić, kiedy zadeklarowana podany typ).</span><span class="sxs-lookup"><span data-stu-id="ae76e-193">The quoted code includes a conversion to [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) because that type is the erasure of this provided type (as you specified when you declared the provided type).</span></span>

<span data-ttu-id="ae76e-194">Dodaj dokumentacji XML do konstruktora i Dodaj Konstruktor podany do podany typ:</span><span class="sxs-lookup"><span data-stu-id="ae76e-194">Add XML documentation to the constructor, and add the provided constructor to the provided type:</span></span>

```fsharp
ctor.AddXmlDocDelayed(fun () -> "This is a constructor")

t.AddMember ctor
```

<span data-ttu-id="ae76e-195">Utwórz drugi Konstruktor podana, który przyjmuje jeden parametr:</span><span class="sxs-lookup"><span data-stu-id="ae76e-195">Create a second provided constructor that takes one parameter:</span></span>

```fsharp
let ctor2 = 
ProvidedConstructor(parameters = [ ProvidedParameter("data",typeof<string>) ], 
                    invokeCode = (fun args -> <@@ (%%(args.[0]) : string) :> obj @@>))
```

<span data-ttu-id="ae76e-196">`InvokeCode` Dla konstruktora ponownie zwraca F # oferty, który reprezentuje kod, który dla wywołania do metody generowane przez kompilator hosta.</span><span class="sxs-lookup"><span data-stu-id="ae76e-196">The `InvokeCode` for the constructor again returns an F# quotation, which represents the code that the host compiler generated for a call to the method.</span></span> <span data-ttu-id="ae76e-197">Na przykład można użyć następującego konstruktora:</span><span class="sxs-lookup"><span data-stu-id="ae76e-197">For example, you can use the following constructor:</span></span>

```fsharp
new Type10("ten")
```

<span data-ttu-id="ae76e-198">Wystąpienie podanego typu jest tworzony przy użyciu danych bazowych "10".</span><span class="sxs-lookup"><span data-stu-id="ae76e-198">An instance of the provided type is created with underlying data "ten".</span></span> <span data-ttu-id="ae76e-199">Być może już zauważono, że `InvokeCode` :: gettotalsize() zwróciło oferty.</span><span class="sxs-lookup"><span data-stu-id="ae76e-199">You may have already noticed that the `InvokeCode` function returns a quotation.</span></span> <span data-ttu-id="ae76e-200">Dane wejściowe do tej funkcji znajduje się lista wyrażeń, jeden na parametr konstruktora.</span><span class="sxs-lookup"><span data-stu-id="ae76e-200">The input to this function is a list of expressions, one per constructor parameter.</span></span> <span data-ttu-id="ae76e-201">W tym przypadku wyrażenia, która reprezentuje wartość jeden parametr jest dostępny w `args.[0]`.</span><span class="sxs-lookup"><span data-stu-id="ae76e-201">In this case, an expression that represents the single parameter value is available in `args.[0]`.</span></span> <span data-ttu-id="ae76e-202">Kod na wywołanie konstruktora przekształca wynik dane wymazane typ wartości zwróconej `obj`.</span><span class="sxs-lookup"><span data-stu-id="ae76e-202">The code for a call to the constructor coerces the return value to the erased type `obj`.</span></span> <span data-ttu-id="ae76e-203">Po dodaniu podana drugi Konstruktor do typu, utworzysz właściwość udostępnionego wystąpienia:</span><span class="sxs-lookup"><span data-stu-id="ae76e-203">After you add the second provided constructor to the type, you create a provided instance property:</span></span>

```fsharp
let instanceProp = 
    ProvidedProperty(propertyName = "InstanceProperty", 
                     propertyType = typeof<int>, 
                     getterCode= (fun args -> 
                        <@@ ((%%(args.[0]) : obj) :?> string).Length @@>))
instanceProp.AddXmlDocDelayed(fun () -> "This is an instance property")
t.AddMember instanceProp
```

<span data-ttu-id="ae76e-204">Wprowadzenie tej właściwości zostanie zwrócona długość ciągu, który jest obiektem reprezentacji.</span><span class="sxs-lookup"><span data-stu-id="ae76e-204">Getting this property will return the length of the string, which is the representation object.</span></span> <span data-ttu-id="ae76e-205">`GetterCode` Właściwość zwraca oferty F #, który określa kod, który kompilator hosta generuje pobrać właściwości.</span><span class="sxs-lookup"><span data-stu-id="ae76e-205">The `GetterCode` property returns an F# quotation that specifies the code that the host compiler generates to get the property.</span></span> <span data-ttu-id="ae76e-206">Podobnie jak `InvokeCode`, `GetterCode` :: gettotalsize() zwróciło oferty.</span><span class="sxs-lookup"><span data-stu-id="ae76e-206">Like `InvokeCode`, the `GetterCode` function returns a quotation.</span></span> <span data-ttu-id="ae76e-207">Kompilator hosta wywołuje tę funkcję z listy argumentów.</span><span class="sxs-lookup"><span data-stu-id="ae76e-207">The host compiler calls this function with a list of arguments.</span></span> <span data-ttu-id="ae76e-208">W tym przypadku argumenty zawierają tylko pojedyncze wyrażenie, który reprezentuje wystąpienie, na którym jest wywoływana metoda pobierająca, możesz uzyskać dostęp za pomocą `args.[0]`. Implementacja `GetterCode` następnie splices do oferty wynik wymazane wpisz `obj`, i używane jest rzutowanie do zaspokojenia kompilatora mechanizmu sprawdzania typów, że obiekt jest ciągiem.</span><span class="sxs-lookup"><span data-stu-id="ae76e-208">In this case, the arguments include just the single expression that represents the instance upon which the getter is being called, which you can access by using `args.[0]`.The implementation of `GetterCode` then splices into the result quotation at the erased type `obj`, and a cast is used to satisfy the compiler's mechanism for checking types that the object is a string.</span></span> <span data-ttu-id="ae76e-209">Kolejnym etapem `makeOneProvidedType` zawiera metodę instancji za pomocą jednego parametru.</span><span class="sxs-lookup"><span data-stu-id="ae76e-209">The next part of `makeOneProvidedType` provides an instance method with one parameter.</span></span>

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

<span data-ttu-id="ae76e-210">Na koniec Utwórz typu zagnieżdżonego, która zawiera 100 zagnieżdżonych właściwości.</span><span class="sxs-lookup"><span data-stu-id="ae76e-210">Finally, create a nested type that contains 100 nested properties.</span></span> <span data-ttu-id="ae76e-211">To tworzenie zagnieżdżonych typu i jego właściwości zostanie opóźnione, to znaczy, obliczona na żądanie.</span><span class="sxs-lookup"><span data-stu-id="ae76e-211">The creation of this nested type and its properties is delayed, that is, computed on-demand.</span></span>

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

### <a name="details-about-erased-provided-types"></a><span data-ttu-id="ae76e-212">Szczegółowe informacje o wymazane podane typy</span><span class="sxs-lookup"><span data-stu-id="ae76e-212">Details about Erased Provided Types</span></span>

<span data-ttu-id="ae76e-213">W przykładzie, w tej sekcji przedstawiono jedynie *wymazane podane typy*, które są szczególnie przydatne w następujących sytuacjach:</span><span class="sxs-lookup"><span data-stu-id="ae76e-213">The example in this section provides only *erased provided types*, which are particularly useful in the following situations:</span></span>

- <span data-ttu-id="ae76e-214">Kiedy piszesz dostawcę dla przestrzeń informacji, która zawiera tylko danych i metod.</span><span class="sxs-lookup"><span data-stu-id="ae76e-214">When you are writing a provider for an information space that contains only data and methods.</span></span>

- <span data-ttu-id="ae76e-215">Kiedy piszesz dostawcy, gdzie semantyka dokładne typ środowiska uruchomieniowego nie są istotne dla praktyczne wykorzystanie miejsca informacji.</span><span class="sxs-lookup"><span data-stu-id="ae76e-215">When you are writing a provider where accurate runtime-type semantics aren't critical for practical use of the information space.</span></span>

- <span data-ttu-id="ae76e-216">Kiedy piszesz dostawcę dla przestrzeń informacji, więc dużej i wzajemnie połączonych, że nie jest technicznie możliwe, można wygenerować rzeczywistych typów .NET do przestrzeń informacji.</span><span class="sxs-lookup"><span data-stu-id="ae76e-216">When you are writing a provider for an information space that is so large and interconnected that it isn’t technically feasible to generate real .NET types for the information space.</span></span>

<span data-ttu-id="ae76e-217">W tym przykładzie każdy z podanych typu są usuwane na typ `obj`, a wszystkie przypadki użycia typu pojawi się jako typ `obj` w skompilowany kod.</span><span class="sxs-lookup"><span data-stu-id="ae76e-217">In this example, each provided type is erased to type `obj`, and all uses of the type will appear as type `obj` in compiled code.</span></span> <span data-ttu-id="ae76e-218">W rzeczywistości obiektów w tych przykładach są ciągami, ale typ będą wyświetlane jako `System.Object` na platformie .NET skompilowany kod.</span><span class="sxs-lookup"><span data-stu-id="ae76e-218">In fact, the underlying objects in these examples are strings, but the type will appear as `System.Object` in .NET compiled code.</span></span> <span data-ttu-id="ae76e-219">Ponieważ wszystkie przypadki użycia wymazywania typie, będzie można użyć jawne pakowanie, Rozpakowywanie i rzutowania można złamać usuwane typów.</span><span class="sxs-lookup"><span data-stu-id="ae76e-219">As with all uses of type erasure, you can use explicit boxing, unboxing, and casting to subvert erased types.</span></span> <span data-ttu-id="ae76e-220">W tym przypadku wyjątek rzutowania, który nie jest prawidłową może spowodować, jeśli obiekt jest używany.</span><span class="sxs-lookup"><span data-stu-id="ae76e-220">In this case, a cast exception that isn’t valid may result when the object is used.</span></span> <span data-ttu-id="ae76e-221">Dostawca środowiska uruchomieniowego, można zdefiniować swój własny typ reprezentujący prywatnych w celu zabezpieczenia przed reprezentacje false.</span><span class="sxs-lookup"><span data-stu-id="ae76e-221">A provider runtime can define its own private representation type to help protect against false representations.</span></span> <span data-ttu-id="ae76e-222">Nie można zdefiniować typy wymazane w języku F # sam.</span><span class="sxs-lookup"><span data-stu-id="ae76e-222">You can’t define erased types in F# itself.</span></span> <span data-ttu-id="ae76e-223">Tylko podane typy mogą zostać wymazane.</span><span class="sxs-lookup"><span data-stu-id="ae76e-223">Only provided types may be erased.</span></span> <span data-ttu-id="ae76e-224">Musisz rozumieć konsekwencje, zarówno praktyczne, i semantyczne, albo korzystania z wymazanej typy dla dostawcy typu lub dostawcę, który zawiera usunięte typów.</span><span class="sxs-lookup"><span data-stu-id="ae76e-224">You must understand the ramifications, both practical and semantic, of using either erased types for your type provider or a provider that provides erased types.</span></span> <span data-ttu-id="ae76e-225">Typem wymazane nie ma rzeczywistych .NET typu.</span><span class="sxs-lookup"><span data-stu-id="ae76e-225">An erased type has no real .NET type.</span></span> <span data-ttu-id="ae76e-226">W związku z tym nie można wykonać dokładne odbicie nad typem i może złamać wymazane typy rzutowania środowiska uruchomieniowego i innych technik, które opierają się na semantyce typu dokładnego czasu wykonywania za pomocą.</span><span class="sxs-lookup"><span data-stu-id="ae76e-226">Therefore, you cannot do accurate reflection over the type, and you might subvert erased types if you use runtime casts and other techniques that rely on exact runtime type semantics.</span></span> <span data-ttu-id="ae76e-227">Subversion typów wymazane często skutkuje wyjątki rzutowanie typu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="ae76e-227">Subversion of erased types frequently results in type cast exceptions at runtime.</span></span>

### <a name="choosing-representations-for-erased-provided-types"></a><span data-ttu-id="ae76e-228">Wybieranie oświadczenia dla wymazane dostarczone typy</span><span class="sxs-lookup"><span data-stu-id="ae76e-228">Choosing Representations for Erased Provided Types</span></span>

<span data-ttu-id="ae76e-229">Do niektórych zastosowań wymazane podane typy nie jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="ae76e-229">For some uses of erased provided types, no representation is required.</span></span> <span data-ttu-id="ae76e-230">Na przykład wymazane dostarczane typ może zawierać tylko właściwości statycznych i elementów członkowskich i konstruktorów, a żadnych metod ani właściwości zwróci wystąpienia tego typu.</span><span class="sxs-lookup"><span data-stu-id="ae76e-230">For example, the erased provided type might contain only static properties and members and no constructors, and no methods or properties would return an instance of the type.</span></span> <span data-ttu-id="ae76e-231">Możesz uzyskiwać dostęp wystąpień wymazane podany typ, należy wziąć pod uwagę następujące kwestie:</span><span class="sxs-lookup"><span data-stu-id="ae76e-231">If you can reach instances of an erased provided type, you must consider the following questions:</span></span>

<span data-ttu-id="ae76e-232">**Co to jest wymazywanie podany typ?**</span><span class="sxs-lookup"><span data-stu-id="ae76e-232">**What is the erasure of a provided type?**</span></span>

- <span data-ttu-id="ae76e-233">Wymazywanie podany typ jest, jak typ pojawia się w skompilowanego kodu .NET.</span><span class="sxs-lookup"><span data-stu-id="ae76e-233">The erasure of a provided type is how the type appears in compiled .NET code.</span></span>

- <span data-ttu-id="ae76e-234">Wymazywanie typu podanej klasy wymazane jest zawsze pierwszej-wymazane typem podstawowym w łańcuchu dziedziczenia tego typu.</span><span class="sxs-lookup"><span data-stu-id="ae76e-234">The erasure of a provided erased class type is always the first non-erased base type in the inheritance chain of the type.</span></span>

- <span data-ttu-id="ae76e-235">Wymazywanie typu interfejsem dostarczanym wymazane jest zawsze `System.Object`.</span><span class="sxs-lookup"><span data-stu-id="ae76e-235">The erasure of a provided erased interface type is always `System.Object`.</span></span>

<span data-ttu-id="ae76e-236">**Co to są liczbami w postaci podany typ?**</span><span class="sxs-lookup"><span data-stu-id="ae76e-236">**What are the representations of a provided type?**</span></span>

- <span data-ttu-id="ae76e-237">Zestaw obiektów możliwych do wymazane, podany typ są nazywane oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="ae76e-237">The set of possible objects for an erased provided type are called its representations.</span></span> <span data-ttu-id="ae76e-238">W przykładzie w tym dokumencie reprezentacje wszystkich wymazane podane typy `Type1..Type100` są zawsze obiektów w postaci ciągów.</span><span class="sxs-lookup"><span data-stu-id="ae76e-238">In the example in this document, the representations of all the erased provided types `Type1..Type100` are always string objects.</span></span>

<span data-ttu-id="ae76e-239">Reprezentacje wszystkich podany typ musi być zgodny z wymazywania podanego typu.</span><span class="sxs-lookup"><span data-stu-id="ae76e-239">All representations of a provided type must be compatible with the erasure of the provided type.</span></span> <span data-ttu-id="ae76e-240">(W przeciwnym razie kompilator F # błąd uniemożliwiający do użycia dostawcy typów lub zweryfikowanie kodu platformy .NET, który nie jest prawidłowy, zostanie wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="ae76e-240">(Otherwise, either the F# compiler will give an error for a use of the type provider, or unverifiable .NET code that isn't valid will be generated.</span></span> <span data-ttu-id="ae76e-241">Dostawcy typów nie jest prawidłowy, jeśli zwróci ona kod, który zawiera reprezentację, który nie jest prawidłowy).</span><span class="sxs-lookup"><span data-stu-id="ae76e-241">A type provider isn’t valid if it returns code that gives a  representation that isn't valid.)</span></span>

<span data-ttu-id="ae76e-242">Możesz wybrać reprezentację podanych obiektów przy użyciu jednej z poniższych metod, które są bardzo popularne:</span><span class="sxs-lookup"><span data-stu-id="ae76e-242">You can choose a representation for provided objects by using either of the following approaches, both of which are very common:</span></span>

- <span data-ttu-id="ae76e-243">Jeśli po prostu silnie typizowaną otokę za pośrednictwem istniejącego typu .NET, często warto wymazać do tego typu, należy użyć wystąpienia tego typu jako oświadczenia i / lub z danym typem.</span><span class="sxs-lookup"><span data-stu-id="ae76e-243">If you're simply providing a strongly typed wrapper over an existing .NET type, it often makes sense for your type to erase to that type, use instances of that type as representations, or both.</span></span> <span data-ttu-id="ae76e-244">To podejście jest odpowiednie, jeśli większość istniejących metod tego typu nadal mieć sens, gdy za pomocą silnie typizowanej wersji.</span><span class="sxs-lookup"><span data-stu-id="ae76e-244">This approach is appropriate when most of the existing methods on that type still make sense when using the strongly typed version.</span></span>

- <span data-ttu-id="ae76e-245">Jeśli chcesz utworzyć interfejs API, który różni się znacznie z dowolnym istniejącym interfejsem API platformy .NET, dobrym pomysłem do tworzenia typów środowiska wykonawczego, które będą wymazywania typie i reprezentacji dla podanego typu.</span><span class="sxs-lookup"><span data-stu-id="ae76e-245">If you want to create an API that differs significantly from any existing .NET API, it makes sense to create runtime types that will be the type erasure and representations for the provided types.</span></span>

<span data-ttu-id="ae76e-246">W przykładzie w tym dokumencie używa ciągów jako oświadczenia podanych obiektów.</span><span class="sxs-lookup"><span data-stu-id="ae76e-246">The example in this document uses strings as representations of provided objects.</span></span> <span data-ttu-id="ae76e-247">Często może być odpowiednie na potrzeby innych obiektów reprezentacji.</span><span class="sxs-lookup"><span data-stu-id="ae76e-247">Frequently, it may be appropriate to use other objects for representations.</span></span> <span data-ttu-id="ae76e-248">Na przykład może użyć słownika jako zbiór właściwości:</span><span class="sxs-lookup"><span data-stu-id="ae76e-248">For example, you may use a dictionary as a property bag:</span></span>

```fsharp
ProvidedConstructor(parameters = [], 
    invokeCode= (fun args -> <@@ (new Dictionary<string,obj>()) :> obj @@>))
```

<span data-ttu-id="ae76e-249">Jako alternatywę może zdefiniować typ u Twojego dostawcy typu, który będzie używany w czasie wykonywania w celu utworzenia reprezentacji, wraz z co najmniej jednej operacji środowiska uruchomieniowego:</span><span class="sxs-lookup"><span data-stu-id="ae76e-249">As an alternative, you may define a type in your type provider that will be used at runtime to form the representation, along with one or more runtime operations:</span></span>

```fsharp
type DataObject() =
    let data = Dictionary<string,obj>()
    member x.RuntimeOperation() = data.Count
```

<span data-ttu-id="ae76e-250">Podane elementy członkowskie można następnie konstruować wystąpień tego typu obiektu:</span><span class="sxs-lookup"><span data-stu-id="ae76e-250">Provided members can then construct instances of this object type:</span></span>

```fsharp
ProvidedConstructor(parameters = [], 
    invokeCode= (fun args -> <@@ (new DataObject()) :> obj @@>))
```

<span data-ttu-id="ae76e-251">W takim przypadku może (opcjonalnie) używasz tego typu jako wymazywania typie, określając tego typu jako `baseType` przy konstruowaniu `ProvidedTypeDefinition`:</span><span class="sxs-lookup"><span data-stu-id="ae76e-251">In this case, you may (optionally) use this type as the type erasure by specifying this type as the `baseType` when constructing the `ProvidedTypeDefinition`:</span></span>

```fsharp
ProvidedTypeDefinition(…, baseType = Some typeof<DataObject> )
…
ProvidedConstructor(…, InvokeCode = (fun args -> <@@ new DataObject() @@>), …)
```

### <a name="key-lessons"></a><span data-ttu-id="ae76e-252">Lekcje klucza</span><span class="sxs-lookup"><span data-stu-id="ae76e-252">Key Lessons</span></span>

<span data-ttu-id="ae76e-253">W poprzedniej sekcji objaśniono sposób tworzenia prostego wymazywanie dostawcę typów, który udostępnia szereg typów, właściwości i metody.</span><span class="sxs-lookup"><span data-stu-id="ae76e-253">The previous section explained how to create a simple erasing type provider that provides a range of types, properties, and methods.</span></span> <span data-ttu-id="ae76e-254">W tej sekcji również wyjaśniono pojęcie wymazywania typu, w tym niektóre zalety i wady związanych z udostępnianiem typy wymazane z dostawcy typów i omówiono reprezentujących typy wymazane.</span><span class="sxs-lookup"><span data-stu-id="ae76e-254">This section also explained the concept of type erasure, including some of the advantages and disadvantages of providing erased types from a type provider, and discussed representations of erased types.</span></span>

## <a name="a-type-provider-that-uses-static-parameters"></a><span data-ttu-id="ae76e-255">Dostawcy typów, który używa statycznych parametrów</span><span class="sxs-lookup"><span data-stu-id="ae76e-255">A Type Provider That Uses Static Parameters</span></span>

<span data-ttu-id="ae76e-256">Możliwość parametryzacja dostawców typów statycznych danych umożliwia wiele ciekawych scenariuszy, nawet w przypadkach, gdy dostawca nie potrzebuje dostępu do żadnych danych lokalnych lub zdalnych.</span><span class="sxs-lookup"><span data-stu-id="ae76e-256">The ability to parameterize type providers by static data enables many interesting scenarios, even in cases when the provider doesn't need to access any local or remote data.</span></span> <span data-ttu-id="ae76e-257">W tej sekcji dowiesz się kilka podstawowych technik dla zestawiania takiego dostawcy.</span><span class="sxs-lookup"><span data-stu-id="ae76e-257">In this section, you’ll learn some basic techniques for putting together such a provider.</span></span>

### <a name="type-checked-regex-provider"></a><span data-ttu-id="ae76e-258">Typ zaznaczone dostawcy wyrażeń regularnych</span><span class="sxs-lookup"><span data-stu-id="ae76e-258">Type Checked Regex Provider</span></span>

<span data-ttu-id="ae76e-259">Wyobraź sobie chcesz zaimplementować dostawcę typów dla wyrażeń regularnych, który otacza .NET <xref:System.Text.RegularExpressions.Regex> bibliotek interfejsu, który zapewnia następujące gwarancje w czasie kompilacji:</span><span class="sxs-lookup"><span data-stu-id="ae76e-259">Imagine that you want to implement a type provider for regular expressions that wraps the .NET <xref:System.Text.RegularExpressions.Regex> libraries in an interface that provides the following compile-time guarantees:</span></span>

- <span data-ttu-id="ae76e-260">Sprawdzanie, czy wyrażenie regularne jest prawidłowa.</span><span class="sxs-lookup"><span data-stu-id="ae76e-260">Verifying whether a regular expression is valid.</span></span>

- <span data-ttu-id="ae76e-261">Materiały nazwane właściwości na dopasowania, które są oparte na wszystkie nazwy grup w wyrażeniu regularnym.</span><span class="sxs-lookup"><span data-stu-id="ae76e-261">Providing named properties on matches that are based on any group names in the regular expression.</span></span>

<span data-ttu-id="ae76e-262">W tej sekcji dowiesz się, jak utworzyć za pomocą dostawców typów `RegexTyped` wpisz, że wzorzec wyrażenia regularnego parametryzuje dane umożliwia uzyskiwanie tych korzyści.</span><span class="sxs-lookup"><span data-stu-id="ae76e-262">This section shows you how to use type providers to create a `RegexTyped` type that the regular expression pattern parameterizes to provide these benefits.</span></span> <span data-ttu-id="ae76e-263">Kompilator zgłosi błąd, jeśli podany wzorzec nie jest prawidłowa, a dostawca typów może wyodrębnić grupy od wzorca, tak, aby mogli je przy użyciu nazwanych właściwości dopasowań.</span><span class="sxs-lookup"><span data-stu-id="ae76e-263">The compiler will report an error if the supplied pattern isn't valid, and the type provider can extract the groups from the pattern so that you can access them by using named properties on matches.</span></span> <span data-ttu-id="ae76e-264">Podczas projektowania dostawcy typów należy rozważyć, jak powinna wyglądać jego narażonych interfejsu API dla użytkowników końcowych i jak ten projekt przekształci się w kodzie .NET.</span><span class="sxs-lookup"><span data-stu-id="ae76e-264">When you design a type provider, you should consider how its exposed API should look to end users and how this design will translate to .NET code.</span></span> <span data-ttu-id="ae76e-265">Poniższy przykład pokazuje, jak używać interfejsu API na pobranie składników numer kierunkowy:</span><span class="sxs-lookup"><span data-stu-id="ae76e-265">The following example shows how to use such an API to get the components of the area code:</span></span>

```fsharp
type T = RegexTyped< @"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)">
let reg = T()
let result = T.IsMatch("425-555-2345")
let r = reg.Match("425-555-2345").Group_AreaCode.Value //r equals "425"
```

<span data-ttu-id="ae76e-266">Poniższy przykład pokazuje, jak dostawca typów przekształca te wywołania:</span><span class="sxs-lookup"><span data-stu-id="ae76e-266">The following example shows how the type provider translates these calls:</span></span>

```fsharp
let reg = new Regex(@"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)")
let result = reg.IsMatch("425-123-2345")
let r = reg.Match("425-123-2345").Groups.["AreaCode"].Value //r equals "425"
```

<span data-ttu-id="ae76e-267">Pamiętaj o następujących kwestiach:</span><span class="sxs-lookup"><span data-stu-id="ae76e-267">Note the following points:</span></span>

- <span data-ttu-id="ae76e-268">Standardowy typ wyrażenia regularnego reprezentuje sparametryzowane `RegexTyped` typu.</span><span class="sxs-lookup"><span data-stu-id="ae76e-268">The standard Regex type represents the parameterized `RegexTyped` type.</span></span>

- <span data-ttu-id="ae76e-269">`RegexTyped` Konstruktor powoduje wywołanie konstruktora wyrażeń regularnych, przekazywanie argumentu typu statycznego dla wzorca.</span><span class="sxs-lookup"><span data-stu-id="ae76e-269">The `RegexTyped` constructor results in a call to the Regex constructor, passing in the static type argument for the pattern.</span></span>

- <span data-ttu-id="ae76e-270">Wyniki `Match` metody są reprezentowane przez standard <xref:System.Text.RegularExpressions.Match> typu.</span><span class="sxs-lookup"><span data-stu-id="ae76e-270">The results of the `Match` method are represented by the standard <xref:System.Text.RegularExpressions.Match> type.</span></span>

- <span data-ttu-id="ae76e-271">Każda grupa o nazwie wyników w podanej właściwości i uzyskiwania dostępu do właściwości powoduje użycie indeksatora w przypadku dopasowania `Groups` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="ae76e-271">Each named group results in a provided property, and accessing the property results in a use of an indexer on a match’s `Groups` collection.</span></span>

<span data-ttu-id="ae76e-272">Poniższy kod stanowi podstawę logiki do zaimplementowania takich dostawcy, a w tym przykładzie pomija dodanie wszystkich elementów członkowskich do podanego typu.</span><span class="sxs-lookup"><span data-stu-id="ae76e-272">The following code is the core of the logic to implement such a provider, and this example omits the addition of all members to the provided type.</span></span> <span data-ttu-id="ae76e-273">Informacje dla każdego członka dodano zobacz odpowiednią sekcję w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="ae76e-273">For information about each added member, see the appropriate section later in this topic.</span></span> <span data-ttu-id="ae76e-274">Aby uzyskać pełny kod pobrać przykład z [F # 3.0 przykładowy pakiet](https://fsharp3sample.codeplex.com) w witrynie Codeplex.</span><span class="sxs-lookup"><span data-stu-id="ae76e-274">For the full code, download the sample from the [F# 3.0 Sample Pack](https://fsharp3sample.codeplex.com) on the Codeplex website.</span></span>

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

<span data-ttu-id="ae76e-275">Pamiętaj o następujących kwestiach:</span><span class="sxs-lookup"><span data-stu-id="ae76e-275">Note the following points:</span></span>

- <span data-ttu-id="ae76e-276">Dostawcy typów przyjmuje dwa parametry statyczne: `pattern`, który jest obowiązkowe, a `options`, które są opcjonalne (ponieważ podana jest wartość domyślna).</span><span class="sxs-lookup"><span data-stu-id="ae76e-276">The type provider takes two static parameters: the `pattern`, which is mandatory, and the `options`, which are optional (because a default value is provided).</span></span>

- <span data-ttu-id="ae76e-277">Po argumenty statyczne są dostarczane, Utwórz wystąpienie wyrażenia regularnego.</span><span class="sxs-lookup"><span data-stu-id="ae76e-277">After the static arguments are supplied, you create an instance of the regular expression.</span></span> <span data-ttu-id="ae76e-278">To wystąpienie spowoduje zgłoszenie wyjątku, jeśli wyrażenie regularne jest źle sformułowany, a ten błąd będzie zgłaszany dla użytkowników.</span><span class="sxs-lookup"><span data-stu-id="ae76e-278">This instance will throw an exception if the Regex is malformed, and this error will be reported to users.</span></span>

- <span data-ttu-id="ae76e-279">W ramach `DefineStaticParameters` wywołanie zwrotne, zdefiniuj typ, który będzie zwracany po argumenty są dostarczane.</span><span class="sxs-lookup"><span data-stu-id="ae76e-279">Within the `DefineStaticParameters` callback, you define the type that will be returned after the arguments are supplied.</span></span>

- <span data-ttu-id="ae76e-280">Ten kod ustawia `HideObjectMethods` na wartość true, dzięki czemu środowisko IntelliSense pozostanie prostsze.</span><span class="sxs-lookup"><span data-stu-id="ae76e-280">This code sets `HideObjectMethods` to true so that the IntelliSense experience will remain streamlined.</span></span> <span data-ttu-id="ae76e-281">Powoduje, że ten atrybut `Equals`, `GetHashCode`, `Finalize`, i `GetType` składowe, które mają zostać pominięte z listy technologii IntelliSense dla podanego obiektu.</span><span class="sxs-lookup"><span data-stu-id="ae76e-281">This attribute causes the `Equals`, `GetHashCode`, `Finalize`, and `GetType` members to be suppressed from IntelliSense lists for a provided object.</span></span>

- <span data-ttu-id="ae76e-282">Możesz użyć `obj` jako typ bazowy metody, ale użyjemy `Regex` obiektu jako reprezentacja środowiska uruchomieniowego tego typu, jak pokazano w następnym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="ae76e-282">You use `obj` as the base type of the method, but you’ll use a `Regex` object as the runtime representation of this type, as the next example shows.</span></span>

- <span data-ttu-id="ae76e-283">Wywołanie `Regex` Konstruktor wyrzuca <xref:System.ArgumentException> kiedy wyrażenie regularne jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="ae76e-283">The call to the `Regex` constructor throws a <xref:System.ArgumentException> when a regular expression isn’t valid.</span></span> <span data-ttu-id="ae76e-284">Kompilator przechwytuje ten wyjątek i zgłasza komunikat o błędzie dla użytkownika, w czasie kompilacji lub w edytorze programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ae76e-284">The compiler catches this exception and reports an error message to the user at compile time or in the Visual Studio editor.</span></span> <span data-ttu-id="ae76e-285">Ten wyjątek umożliwia wyrażeń regularnych zostać uwierzytelnionym bez uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ae76e-285">This exception enables regular expressions to be validated without running an application.</span></span>

<span data-ttu-id="ae76e-286">Określone powyżej nie jest przydatne jeszcze, ponieważ nie zawiera żadnych istotnych metody lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="ae76e-286">The type defined above isn't useful yet because it doesn’t contain any meaningful methods or properties.</span></span> <span data-ttu-id="ae76e-287">Najpierw dodaj statyczną `IsMatch` metody:</span><span class="sxs-lookup"><span data-stu-id="ae76e-287">First, add a static `IsMatch` method:</span></span>

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

<span data-ttu-id="ae76e-288">Powyższy kod definiuje metodę `IsMatch`, który przyjmuje ciąg jako dane wejściowe i zwraca `bool`.</span><span class="sxs-lookup"><span data-stu-id="ae76e-288">The previous code defines a method `IsMatch`, which takes a string as input and returns a `bool`.</span></span> <span data-ttu-id="ae76e-289">Tylko wymagana polega na użyciu `args` argumentu w ciągu `InvokeCode` definicji.</span><span class="sxs-lookup"><span data-stu-id="ae76e-289">The only tricky part is the use of the `args` argument within the `InvokeCode` definition.</span></span> <span data-ttu-id="ae76e-290">W tym przykładzie `args` znajduje się lista ofert, która reprezentuje argumenty tej metody.</span><span class="sxs-lookup"><span data-stu-id="ae76e-290">In this example, `args` is a list of quotations that represents the arguments to this method.</span></span> <span data-ttu-id="ae76e-291">Jeśli metoda jest metodą wystąpienia, pierwszy argument reprezentuje `this` argumentu.</span><span class="sxs-lookup"><span data-stu-id="ae76e-291">If the method is an instance method, the first argument represents the `this` argument.</span></span> <span data-ttu-id="ae76e-292">W przypadku statycznej metody argumenty są wszystkie tylko jawnych argumentów do metody.</span><span class="sxs-lookup"><span data-stu-id="ae76e-292">However, for a static method, the arguments are all just the explicit arguments to the method.</span></span> <span data-ttu-id="ae76e-293">Należy pamiętać, że typ wartości oferowanej powinien pasuje do określonego typu zwracanego (w tym przypadku `bool`).</span><span class="sxs-lookup"><span data-stu-id="ae76e-293">Note that the type of the quoted value should match the specified return type (in this case, `bool`).</span></span> <span data-ttu-id="ae76e-294">Należy także zauważyć, że ten kod używa `AddXmlDoc` metody, aby upewnić się, że podana metoda ma również przydatna dokumentacji, które można podać za pomocą funkcji IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="ae76e-294">Also note that this code uses the `AddXmlDoc` method to make sure that the provided method also has useful documentation, which you can supply through IntelliSense.</span></span>

<span data-ttu-id="ae76e-295">Następnie dodaj wystąpienie metody Match.</span><span class="sxs-lookup"><span data-stu-id="ae76e-295">Next, add an instance Match method.</span></span> <span data-ttu-id="ae76e-296">Jednak ta metoda powinna zwrócić wartość podana `Match` wpisz, aby grupy jest możliwy w silnie typizowany sposób.</span><span class="sxs-lookup"><span data-stu-id="ae76e-296">However, this method should return a value of a provided `Match` type so that the groups can be accessed in a strongly typed fashion.</span></span> <span data-ttu-id="ae76e-297">Tak więc pierwszym zdeklarowaniu `Match` typu.</span><span class="sxs-lookup"><span data-stu-id="ae76e-297">Thus, you first declare the `Match` type.</span></span> <span data-ttu-id="ae76e-298">Ponieważ ten typ jest zależny od wzorzec, który został dostarczony jako argument statyczne, ten typ musi być zagnieżdżony w ramach definicji typ sparametryzowany:</span><span class="sxs-lookup"><span data-stu-id="ae76e-298">Because this type depends on the pattern that was supplied as a static argument, this type must be nested within the parameterized type definition:</span></span>

```fsharp
let matchTy = 
    ProvidedTypeDefinition(
        "MatchType", 
        baseType = Some baseTy, 
        hideObjectMethods = true)

ty.AddMember matchTy
```

<span data-ttu-id="ae76e-299">Następnie dodasz jedną właściwość na typ dopasowania dla każdej grupy.</span><span class="sxs-lookup"><span data-stu-id="ae76e-299">You then add one property to the Match type for each group.</span></span> <span data-ttu-id="ae76e-300">W czasie wykonywania, dopasowanie jest reprezentowany jako <xref:System.Text.RegularExpressions.Match> wartości, więc należy użyć cudzysłowu, który definiuje właściwość <xref:System.Text.RegularExpressions.Match.Groups> indeksowana właściwość, aby uzyskać odpowiednie grupy.</span><span class="sxs-lookup"><span data-stu-id="ae76e-300">At runtime, a match is represented as a <xref:System.Text.RegularExpressions.Match> value, so the quotation that defines the property must use the <xref:System.Text.RegularExpressions.Match.Groups> indexed property to get the relevant group.</span></span>

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

<span data-ttu-id="ae76e-301">Ponownie należy pamiętać, podana wartość właściwości dodajesz dokumentacji XML.</span><span class="sxs-lookup"><span data-stu-id="ae76e-301">Again, note that you’re adding XML documentation to the provided property.</span></span> <span data-ttu-id="ae76e-302">Też pamiętać, że właściwość może zostać odczytany, jeśli `GetterCode` dostarczono funkcji i właściwości mogą być zapisywane, jeśli `SetterCode` funkcji zostanie podany, dzięki czemu wynikowy właściwość jest tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="ae76e-302">Also note that a property can be read if a `GetterCode` function is provided, and the property can be written if a `SetterCode` function is provided, so the resulting property is read only.</span></span>

<span data-ttu-id="ae76e-303">Teraz możesz utworzyć metodę wystąpienia, która zwraca wartość tego `Match` typu:</span><span class="sxs-lookup"><span data-stu-id="ae76e-303">Now you can create an instance method that returns a value of this `Match` type:</span></span>

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

<span data-ttu-id="ae76e-304">Ponieważ tworzysz metodę wystąpienia `args.[0]` reprezentuje `RegexTyped` wystąpienia, na którym jest wywoływana metoda, i `args.[1]` jest argument wejściowy.</span><span class="sxs-lookup"><span data-stu-id="ae76e-304">Because you are creating an instance method, `args.[0]` represents the `RegexTyped` instance on which the method is being called, and `args.[1]` is the input argument.</span></span>

<span data-ttu-id="ae76e-305">Na koniec należy dostarczyć konstruktora, tak że można utworzyć jedno wystąpienie podanego typu.</span><span class="sxs-lookup"><span data-stu-id="ae76e-305">Finally, provide a constructor so that instances of the provided type can be created.</span></span>

```fsharp
let ctor = 
    ProvidedConstructor(
        parameters = [], 
        invokeCode = fun args -> <@@ Regex(pattern, options) :> obj @@>)

ctor.AddXmlDoc("Initializes a regular expression instance.")

ty.AddMember ctor
```

<span data-ttu-id="ae76e-306">Konstruktor jedynie na partycje powoduje usunięcie do utworzenia standardowego wystąpienia wyrażenie regularne .NET, co jest spakowany ponownie do obiektu, ponieważ `obj` jest wymazywania podanego typu.</span><span class="sxs-lookup"><span data-stu-id="ae76e-306">The constructor merely erases to the creation of a standard .NET Regex instance, which is again boxed to an object because `obj` is the erasure of the provided type.</span></span> <span data-ttu-id="ae76e-307">Dzięki temu przykładowe zastosowanie interfejsu API, który określono wcześniej w temacie działa zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="ae76e-307">With that change, the sample API usage that specified earlier in the topic works as expected.</span></span> <span data-ttu-id="ae76e-308">Poniższy kod jest pełny i końcowe:</span><span class="sxs-lookup"><span data-stu-id="ae76e-308">The following code is complete and final:</span></span>

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

### <a name="key-lessons"></a><span data-ttu-id="ae76e-309">Lekcje klucza</span><span class="sxs-lookup"><span data-stu-id="ae76e-309">Key Lessons</span></span>

<span data-ttu-id="ae76e-310">W tej sekcji wyjaśniono, jak utworzyć dostawcę typów, który działa na jego parametry statyczne.</span><span class="sxs-lookup"><span data-stu-id="ae76e-310">This section explained how to create a type provider that operates on its static parameters.</span></span> <span data-ttu-id="ae76e-311">Dostawca sprawdza, czy parametr static i udostępnia operacje na podstawie jej wartości.</span><span class="sxs-lookup"><span data-stu-id="ae76e-311">The provider checks the static parameter and provides operations based on its value.</span></span>

## <a name="a-type-provider-that-is-backed-by-local-data"></a><span data-ttu-id="ae76e-312">Dostawcy typów, która jest wspierana przez dane lokalne</span><span class="sxs-lookup"><span data-stu-id="ae76e-312">A Type Provider That Is Backed By Local Data</span></span>

<span data-ttu-id="ae76e-313">Często można dostawców typów, aby przedstawić interfejsów API opartych na nie tylko parametry statyczne, ale także informacje z systemów lokalnych lub zdalnych.</span><span class="sxs-lookup"><span data-stu-id="ae76e-313">Frequently you might want type providers to present APIs based on not only static parameters but also information from local or remote systems.</span></span> <span data-ttu-id="ae76e-314">W tej sekcji omówiono dostawców typów, które są oparte na danych lokalnych, takich jak pliki danych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="ae76e-314">This section discusses type providers that are based on local data, such as local data files.</span></span>

### <a name="simple-csv-file-provider"></a><span data-ttu-id="ae76e-315">Dostawcy plików CSV prosty</span><span class="sxs-lookup"><span data-stu-id="ae76e-315">Simple CSV File Provider</span></span>

<span data-ttu-id="ae76e-316">Prostym przykładem należy wziąć pod uwagę dostawcy typów do uzyskiwania dostępu do danych naukowych, w formacie wartości rozdzielanych przecinkami (CSV).</span><span class="sxs-lookup"><span data-stu-id="ae76e-316">As a simple example, consider a type provider for accessing scientific data in Comma Separated Value (CSV) format.</span></span> <span data-ttu-id="ae76e-317">W tej sekcji założono, że pliki CSV zawiera wiersz nagłówka, następuje ruchomy punkt danych, tak jak pokazano w poniższej tabeli:</span><span class="sxs-lookup"><span data-stu-id="ae76e-317">This section assumes that the CSV files contain a header row followed by floating point data, as the following table illustrates:</span></span>

|<span data-ttu-id="ae76e-318">Distance (licznik)</span><span class="sxs-lookup"><span data-stu-id="ae76e-318">Distance (meter)</span></span>|<span data-ttu-id="ae76e-319">Czas (s)</span><span class="sxs-lookup"><span data-stu-id="ae76e-319">Time (second)</span></span>|
|----------------|-------------|
|<span data-ttu-id="ae76e-320">50.0</span><span class="sxs-lookup"><span data-stu-id="ae76e-320">50.0</span></span>|<span data-ttu-id="ae76e-321">3.7</span><span class="sxs-lookup"><span data-stu-id="ae76e-321">3.7</span></span>|
|<span data-ttu-id="ae76e-322">100.0</span><span class="sxs-lookup"><span data-stu-id="ae76e-322">100.0</span></span>|<span data-ttu-id="ae76e-323">5.2</span><span class="sxs-lookup"><span data-stu-id="ae76e-323">5.2</span></span>|
|<span data-ttu-id="ae76e-324">150.0</span><span class="sxs-lookup"><span data-stu-id="ae76e-324">150.0</span></span>|<span data-ttu-id="ae76e-325">6.4</span><span class="sxs-lookup"><span data-stu-id="ae76e-325">6.4</span></span>|

<span data-ttu-id="ae76e-326">W tej sekcji pokazano, jak Podaj typ, który służy do Pobierz wiersze z `Distance` właściwości typu `float<meter>` i `Time` właściwości typu `float<second>`.</span><span class="sxs-lookup"><span data-stu-id="ae76e-326">This section shows how to provide a type that you can use to get rows with a `Distance` property of type `float<meter>` and a `Time` property of type `float<second>`.</span></span> <span data-ttu-id="ae76e-327">Dla uproszczenia składają się następujące założenia:</span><span class="sxs-lookup"><span data-stu-id="ae76e-327">For simplicity, the following assumptions are made:</span></span>

- <span data-ttu-id="ae76e-328">Nazwy nagłówków są mniej jednostek lub mieć postać "Name (jednostka)" i nie zawierać przecinków.</span><span class="sxs-lookup"><span data-stu-id="ae76e-328">Header names are either unit-less or have the form "Name (unit)" and don't contain commas.</span></span>

- <span data-ttu-id="ae76e-329">Jednostki są wszystkie jednostki Systeme międzynarodowy (SI) jako [Microsoft.FSharp.Data.UnitSystems.SI.UnitNames — moduł (F #)](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b) definiuje moduł.</span><span class="sxs-lookup"><span data-stu-id="ae76e-329">Units are all Systeme International (SI) units as the [Microsoft.FSharp.Data.UnitSystems.SI.UnitNames Module (F#)](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b) module defines.</span></span>

- <span data-ttu-id="ae76e-330">Jednostki są wszystkie proste (na przykład pomiaru), a nie złożone (na przykład, licznik na sekundę).</span><span class="sxs-lookup"><span data-stu-id="ae76e-330">Units are all simple (for example, meter) rather than compound (for example, meter/second).</span></span>

- <span data-ttu-id="ae76e-331">Wszystkie kolumny zawierają dane punktu zmiennoprzecinkowego.</span><span class="sxs-lookup"><span data-stu-id="ae76e-331">All columns contain floating point data.</span></span>

<span data-ttu-id="ae76e-332">Bardziej kompletny dostawca będzie Poluzuj te ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="ae76e-332">A more complete provider would loosen these restrictions.</span></span>

<span data-ttu-id="ae76e-333">Pierwszym krokiem jest ponownie należy wziąć pod uwagę, jak powinna wyglądać interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="ae76e-333">Again the first step is to consider how the API should look.</span></span> <span data-ttu-id="ae76e-334">Biorąc pod uwagę `info.csv` plik z zawartością z powyższej tabeli (w formacie rozdzielonych przecinkami), użytkownicy dostawcy powinno być możliwe do pisania kodu, który przypomina poniższy przykład:</span><span class="sxs-lookup"><span data-stu-id="ae76e-334">Given an `info.csv` file with the contents from the previous table (in comma-separated format), users of the provider should be able to write code that resembles the following example:</span></span>

```fsharp
let info = new MiniCsv<"info.csv">()
for row in info.Data do
let time = row.Time
printfn "%f" (float time)
```

<span data-ttu-id="ae76e-335">W tym przypadku kompilator należy konwertować te wywołania coś tak jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="ae76e-335">In this case, the compiler should convert these calls into something like the following example:</span></span>

```fsharp
let info = new CsvFile("info.csv")
for row in info.Data do
let (time:float) = row.[1]
printfn "%f" (float time)
```

<span data-ttu-id="ae76e-336">Optymalne tłumaczenie wymaga dostawcy typu do zdefiniowania rzeczywistych `CsvFile` typu w zestawie dostawcy typów.</span><span class="sxs-lookup"><span data-stu-id="ae76e-336">The optimal translation will require the type provider to define a real `CsvFile` type in the type provider's assembly.</span></span> <span data-ttu-id="ae76e-337">Dostawcy typów często zależy od kilku pomocnicze typy i metody, opakowywać logiki ważne.</span><span class="sxs-lookup"><span data-stu-id="ae76e-337">Type providers often rely on a few helper types and methods to wrap important logic.</span></span> <span data-ttu-id="ae76e-338">Ponieważ miary są usuwane w czasie wykonywania, można użyć `float[]` jako typ wymazane, na podstawie wiersza.</span><span class="sxs-lookup"><span data-stu-id="ae76e-338">Because measures are erased at runtime, you can use a `float[]` as the erased type for a row.</span></span> <span data-ttu-id="ae76e-339">Kompilator będzie traktować różnych kolumn jako posiadające miary różnych typów.</span><span class="sxs-lookup"><span data-stu-id="ae76e-339">The compiler will treat different columns as having different measure types.</span></span> <span data-ttu-id="ae76e-340">Na przykład pierwszej kolumny, w tym przykładzie ma typ `float<meter>`, a druga ma `float<second>`.</span><span class="sxs-lookup"><span data-stu-id="ae76e-340">For example, the first column in our example has type `float<meter>`, and the second has `float<second>`.</span></span> <span data-ttu-id="ae76e-341">Jednak wymazane reprezentacji mogą w dalszym ciągu bardzo proste.</span><span class="sxs-lookup"><span data-stu-id="ae76e-341">However, the erased representation can remain quite simple.</span></span>

<span data-ttu-id="ae76e-342">Poniższy kod przedstawia podstawowe wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="ae76e-342">The following code shows the core of the implementation.</span></span>

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

<span data-ttu-id="ae76e-343">Należy pamiętać o następujących kwestiach dotyczących implementacji:</span><span class="sxs-lookup"><span data-stu-id="ae76e-343">Note the following points about the implementation:</span></span>

- <span data-ttu-id="ae76e-344">Przeciążenia konstruktorów umożliwiają oryginalnego pliku lub taki, który ma identyczne schematu do odczytu.</span><span class="sxs-lookup"><span data-stu-id="ae76e-344">Overloaded constructors allow either the original file or one that has an identical schema to be read.</span></span> <span data-ttu-id="ae76e-345">Ten wzorzec jest typowa, gdy zapis dostawcy typów źródeł danych lokalnych lub zdalnych, a ten wzorzec umożliwia użycie pliku lokalnego ma być używany jako szablon dla danych zdalnych.</span><span class="sxs-lookup"><span data-stu-id="ae76e-345">This pattern is common when you write a type provider for local or remote data sources, and this pattern allows a local file to be used as the template for remote data.</span></span>

- <span data-ttu-id="ae76e-346">Możesz użyć [typeproviderconfig —](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44) wartość, która jest przekazywana do konstruktora typu dostawcy do rozpoznawania nazw względna do pliku.</span><span class="sxs-lookup"><span data-stu-id="ae76e-346">You can use the [TypeProviderConfig](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44) value that’s passed in to the type provider constructor to resolve relative file names.</span></span>

- <span data-ttu-id="ae76e-347">Możesz użyć `AddDefinitionLocation` metodę, aby określić lokalizację obiektu podanej właściwości.</span><span class="sxs-lookup"><span data-stu-id="ae76e-347">You can use the `AddDefinitionLocation` method to define the location of the provided properties.</span></span> <span data-ttu-id="ae76e-348">W związku z tym Jeśli używasz `Go To Definition` podanej właściwości, plik CSV zostanie otwarty w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ae76e-348">Therefore, if you use `Go To Definition` on a provided property, the CSV file will open in Visual Studio.</span></span>

- <span data-ttu-id="ae76e-349">Możesz użyć `ProvidedMeasureBuilder` typu wyszukiwać jednostki SI i wygenerowania odpowiedniego `float<_>` typów.</span><span class="sxs-lookup"><span data-stu-id="ae76e-349">You can use the `ProvidedMeasureBuilder` type to look up the SI units and to generate the relevant `float<_>` types.</span></span>

### <a name="key-lessons"></a><span data-ttu-id="ae76e-350">Lekcje klucza</span><span class="sxs-lookup"><span data-stu-id="ae76e-350">Key Lessons</span></span>

<span data-ttu-id="ae76e-351">W tej sekcji wyjaśniono, jak utworzyć dostawcę typów dla źródła danych lokalnych przy użyciu prosty schemat, który jest zawarty w źródło danych.</span><span class="sxs-lookup"><span data-stu-id="ae76e-351">This section explained how to create a type provider for a local data source with a simple schema that's contained in the data source itself.</span></span>

## <a name="going-further"></a><span data-ttu-id="ae76e-352">Kontynuowanie</span><span class="sxs-lookup"><span data-stu-id="ae76e-352">Going Further</span></span>

<span data-ttu-id="ae76e-353">Poniższe sekcje zawierają sugestie dotyczące dalszych badań.</span><span class="sxs-lookup"><span data-stu-id="ae76e-353">The following sections include suggestions for further study.</span></span>

### <a name="a-look-at-the-compiled-code-for-erased-types"></a><span data-ttu-id="ae76e-354">Przyjrzeć się skompilowany kod dla typów wymazane</span><span class="sxs-lookup"><span data-stu-id="ae76e-354">A Look at the Compiled Code for Erased Types</span></span>

<span data-ttu-id="ae76e-355">Aby dać niektóre informacje o tym, jak użycie dostawcy typów odnosi się do kodu, który jest emitowane, Przyjrzyj się następującą funkcję za pomocą `HelloWorldTypeProvider` używany we wcześniejszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="ae76e-355">To give you some idea of how the use of the type provider corresponds to the code that's emitted, look at the following function by using the `HelloWorldTypeProvider` that's used earlier in this topic.</span></span>

```fsharp
let function1 () = 
    let obj1 = Samples.HelloWorldTypeProvider.Type1("some data")
    obj1.InstanceProperty
```

<span data-ttu-id="ae76e-356">Oto obraz wynikowy kod decompiled przy użyciu ildasm.exe:</span><span class="sxs-lookup"><span data-stu-id="ae76e-356">Here’s an image of the resulting code decompiled by using ildasm.exe:</span></span>

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

<span data-ttu-id="ae76e-357">Jak pokazano w przykładzie, wszystkie wystąpienia typu `Type1` i `InstanceProperty` właściwości zostały wymazane, pozostawiając tylko operacje na typów środowiska wykonawczego związane.</span><span class="sxs-lookup"><span data-stu-id="ae76e-357">As the example shows, all mentions of the type `Type1` and the `InstanceProperty` property have been erased, leaving only operations on the runtime types involved.</span></span>

### <a name="design-and-naming-conventions-for-type-providers"></a><span data-ttu-id="ae76e-358">Projektowanie i konwencje nazewnictwa dla dostawców typów</span><span class="sxs-lookup"><span data-stu-id="ae76e-358">Design and Naming Conventions for Type Providers</span></span>

<span data-ttu-id="ae76e-359">Podczas tworzenia dostawców typów, należy przestrzegać następujących konwencji.</span><span class="sxs-lookup"><span data-stu-id="ae76e-359">Observe the following conventions when authoring type providers.</span></span>

<span data-ttu-id="ae76e-360">**Dostawców łączności protokołów** ogólnie rzecz biorąc, nazwy dostawcy większość bibliotek DLL dla protokołów łączności danych i usługi, takie jak w przypadku połączeń protokołu OData lub SQL powinno zakończyć `TypeProvider` lub `TypeProviders`.</span><span class="sxs-lookup"><span data-stu-id="ae76e-360">**Providers for Connectivity Protocols** In general, names of most provider DLLs for data and service connectivity protocols, such as OData or SQL connections, should end in `TypeProvider` or `TypeProviders`.</span></span> <span data-ttu-id="ae76e-361">Na przykład użyj nazwy biblioteki DLL, który przypomina następujący ciąg:</span><span class="sxs-lookup"><span data-stu-id="ae76e-361">For example, use a DLL name that resembles the following string:</span></span>

```
  Fabrikam.Management.BasicTypeProviders.dll
```

<span data-ttu-id="ae76e-362">Należy upewnić się, że Twoje podane typy są elementami członkowskimi odpowiedniej przestrzeni nazw i wskazują protokołu łączności, które można zaimplementować:</span><span class="sxs-lookup"><span data-stu-id="ae76e-362">Ensure that your provided types are members of the corresponding namespace, and indicate the connectivity protocol that you implemented:</span></span>

```
  Fabrikam.Management.BasicTypeProviders.WmiConnection<…>
  Fabrikam.Management.BasicTypeProviders.DataProtocolConnection<…>
```

<span data-ttu-id="ae76e-363">**Narzędzie do dostawców na potrzeby programowania ogólnego**.</span><span class="sxs-lookup"><span data-stu-id="ae76e-363">**Utility Providers for General Coding**.</span></span>  <span data-ttu-id="ae76e-364">Narzędzie typu dostawcy takim dla wyrażeń regularnych dostawca typów może być częścią podstawowej biblioteki, jak w poniższym przykładzie pokazano:</span><span class="sxs-lookup"><span data-stu-id="ae76e-364">For a utility type provider such as that for regular expressions, the type provider may be part of a base library, as the following example shows:</span></span>

```fsharp
  #r "Fabrikam.Core.Text.Utilities.dll"
```

<span data-ttu-id="ae76e-365">W tym przypadku podany typ pojawią się w momencie odpowiednie zgodnie z normalnym konwencjami projektu platformy .NET:</span><span class="sxs-lookup"><span data-stu-id="ae76e-365">In this case, the provided type would appear at an appropriate point according to normal .NET design conventions:</span></span>

```fsharp
  open Fabrikam.Core.Text.RegexTyped
  
  let regex = new RegexTyped<"a+b+a+b+">()
```

<span data-ttu-id="ae76e-366">**Źródła danych pojedyncze**.</span><span class="sxs-lookup"><span data-stu-id="ae76e-366">**Singleton Data Sources**.</span></span> <span data-ttu-id="ae76e-367">Niektórzy dostawcy typu do pojedynczego dedykowanego źródła danych i zapewniają tylko dane.</span><span class="sxs-lookup"><span data-stu-id="ae76e-367">Some type providers connect to a single dedicated data source and provide only data.</span></span> <span data-ttu-id="ae76e-368">W takim przypadku należy porzucić `TypeProvider` sufiks i użyj normalnej konwencji nazewnictwa platformy .NET:</span><span class="sxs-lookup"><span data-stu-id="ae76e-368">In this case, you should drop the `TypeProvider` suffix and use normal conventions for .NET naming:</span></span>

```fsharp
#r "Fabrikam.Data.Freebase.dll"
  
let data = Fabrikam.Data.Freebase.Astronomy.Asteroids
```

<span data-ttu-id="ae76e-369">Aby uzyskać więcej informacji, zobacz `GetConnection` projektowania Konwencji, który jest opisany w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="ae76e-369">For more information, see the `GetConnection` design convention that's described later in this topic.</span></span>

### <a name="design-patterns-for-type-providers"></a><span data-ttu-id="ae76e-370">Wzorce projektowe dla dostawców typów</span><span class="sxs-lookup"><span data-stu-id="ae76e-370">Design Patterns for Type Providers</span></span>

<span data-ttu-id="ae76e-371">Wzorce projektowe, których można użyć podczas tworzenia dostawców typów można znaleźć w poniższych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="ae76e-371">The following sections describe design patterns you can use when authoring type providers.</span></span>

#### <a name="the-getconnection-design-pattern"></a><span data-ttu-id="ae76e-372">Wzorzec projektowy GetConnection</span><span class="sxs-lookup"><span data-stu-id="ae76e-372">The GetConnection Design Pattern</span></span>

<span data-ttu-id="ae76e-373">Większość dostawców typów, powinny być zapisywane do użycia `GetConnection` wzorzec, który jest używany przez dostawców typu w FSharp.Data.TypeProviders.dll, co ilustruje poniższy przykład:</span><span class="sxs-lookup"><span data-stu-id="ae76e-373">Most type providers should be written to use the `GetConnection` pattern that's used by the type providers in FSharp.Data.TypeProviders.dll, as the following example shows:</span></span>

```fsharp
#r "Fabrikam.Data.WebDataStore.dll"

type Service = Fabrikam.Data.WebDataStore<…static connection parameters…>

let connection = Service.GetConnection(…dynamic connection parameters…)

let data = connection.Astronomy.Asteroids
```

#### <a name="type-providers-backed-by-remote-data-and-services"></a><span data-ttu-id="ae76e-374">Dostawcy typów objęta zdalnych danych i usług</span><span class="sxs-lookup"><span data-stu-id="ae76e-374">Type Providers Backed By Remote Data and Services</span></span>

<span data-ttu-id="ae76e-375">Przed utworzeniem dostawcy typów, która jest wspierana przez zdalne dane i usługi, należy wziąć pod uwagę szereg problemów, które są integralną częścią podłączonych programowania.</span><span class="sxs-lookup"><span data-stu-id="ae76e-375">Before you create a type provider that's backed by remote data and services, you must consider a range of issues that are inherent in connected programming.</span></span> <span data-ttu-id="ae76e-376">Te problemy obejmują następujące kwestie:</span><span class="sxs-lookup"><span data-stu-id="ae76e-376">These issues include the following considerations:</span></span>

- <span data-ttu-id="ae76e-377">mapowanie schematu</span><span class="sxs-lookup"><span data-stu-id="ae76e-377">schema mapping</span></span>

- <span data-ttu-id="ae76e-378">żywotności oraz unieważniania obecności zmiany schematu</span><span class="sxs-lookup"><span data-stu-id="ae76e-378">liveness and invalidation in the presence of schema change</span></span>

- <span data-ttu-id="ae76e-379">pamięć podręczna schematów</span><span class="sxs-lookup"><span data-stu-id="ae76e-379">schema caching</span></span>

- <span data-ttu-id="ae76e-380">implementacje asynchroniczne operacje dostępu do danych</span><span class="sxs-lookup"><span data-stu-id="ae76e-380">asynchronous implementations of data access operations</span></span>

- <span data-ttu-id="ae76e-381">Obsługa zapytań, takich jak zapytania LINQ</span><span class="sxs-lookup"><span data-stu-id="ae76e-381">supporting queries, including LINQ queries</span></span>

- <span data-ttu-id="ae76e-382">poświadczeń i uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="ae76e-382">credentials and authentication</span></span>

<span data-ttu-id="ae76e-383">W tym temacie nie zbadania tych problemów w dalszych.</span><span class="sxs-lookup"><span data-stu-id="ae76e-383">This topic doesn't explore these issues further.</span></span>

### <a name="additional-authoring-techniques"></a><span data-ttu-id="ae76e-384">Innych technik tworzenia pakietów administracyjnych</span><span class="sxs-lookup"><span data-stu-id="ae76e-384">Additional Authoring Techniques</span></span>

<span data-ttu-id="ae76e-385">Podczas pisania własnych dostawców typów, można użyć następujących dodatkowych technik.</span><span class="sxs-lookup"><span data-stu-id="ae76e-385">When you write your own type providers, you might want to use the following additional techniques.</span></span>

### <a name="creating-types-and-members-on-demand"></a><span data-ttu-id="ae76e-386">Tworzenie typów i elementów członkowskich na żądanie</span><span class="sxs-lookup"><span data-stu-id="ae76e-386">Creating Types and Members On-Demand</span></span>

<span data-ttu-id="ae76e-387">Interfejs API ProvidedType ma opóźnione wersje Dodawanie członka.</span><span class="sxs-lookup"><span data-stu-id="ae76e-387">The ProvidedType API has delayed versions of AddMember.</span></span>

```fsharp
  type ProvidedType =
      member AddMemberDelayed  : (unit -> MemberInfo)      -> unit
      member AddMembersDelayed : (unit -> MemberInfo list) -> unit
```

<span data-ttu-id="ae76e-388">Te wersje są używane do tworzenia miejsca do magazynowania na żądanie, typów.</span><span class="sxs-lookup"><span data-stu-id="ae76e-388">These versions are used to create on-demand spaces of types.</span></span>

### <a name="providing-array-types-and-generic-type-instantiations"></a><span data-ttu-id="ae76e-389">Typy tablic i ogólnych instancji typu</span><span class="sxs-lookup"><span data-stu-id="ae76e-389">Providing Array types and Generic Type Instantiations</span></span>

<span data-ttu-id="ae76e-390">Podane elementy członkowskie (których podpisów obejmują typy tablicowe, typami byref i wystąpień typów ogólnych) należy tworzyć przy użyciu normalnych `MakeArrayType`, `MakePointerType`, i `MakeGenericType` na dowolne wystąpienie <xref:System.Type>, w tym `ProvidedTypeDefinitions`.</span><span class="sxs-lookup"><span data-stu-id="ae76e-390">You make provided members (whose signatures include array types, byref types, and instantiations of generic types) by using the normal `MakeArrayType`, `MakePointerType`, and `MakeGenericType` on any instance of <xref:System.Type>, including `ProvidedTypeDefinitions`.</span></span>

> [!NOTE]
> <span data-ttu-id="ae76e-391">W niektórych przypadkach może być konieczne Pomocnik w `ProvidedTypeBuilder.MakeGenericType`.</span><span class="sxs-lookup"><span data-stu-id="ae76e-391">In some cases you may have to use the helper in `ProvidedTypeBuilder.MakeGenericType`.</span></span>  <span data-ttu-id="ae76e-392">Zobacz [dokumentacji zestawu SDK dostawcy typu](https://github.com/fsprojects/FSharp.TypeProviders.SDK/blob/master/README.md#explicit-construction-of-code-makegenerictype-makegenericmethod-and-uncheckedquotations) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="ae76e-392">See the [Type Provider SDK documentation](https://github.com/fsprojects/FSharp.TypeProviders.SDK/blob/master/README.md#explicit-construction-of-code-makegenerictype-makegenericmethod-and-uncheckedquotations) for more details.</span></span>

### <a name="providing-unit-of-measure-annotations"></a><span data-ttu-id="ae76e-393">Zapewnianie jednostka miary adnotacji</span><span class="sxs-lookup"><span data-stu-id="ae76e-393">Providing Unit of Measure Annotations</span></span>

<span data-ttu-id="ae76e-394">Interfejs API ProvidedTypes zapewnia pomocników, zapewniające środek adnotacji.</span><span class="sxs-lookup"><span data-stu-id="ae76e-394">The ProvidedTypes API provides helpers for providing measure annotations.</span></span> <span data-ttu-id="ae76e-395">Na przykład, aby zapewnić typ `float<kg>`, użyj następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="ae76e-395">For example, to provide the type `float<kg>`, use the following code:</span></span>

```fsharp
  let measures = ProvidedMeasureBuilder.Default
  let kg = measures.SI "kilogram"
  let m = measures.SI "meter"
  let float_kg = measures.AnnotateType(typeof<float>,[kg])
```

  <span data-ttu-id="ae76e-396">Aby zapewnić typ `Nullable<decimal<kg/m^2>>`, użyj następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="ae76e-396">To provide the type `Nullable<decimal<kg/m^2>>`, use the following code:</span></span>

```fsharp
  let kgpm2 = measures.Ratio(kg, measures.Square m)
  let dkgpm2 = measures.AnnotateType(typeof<decimal>,[kgpm2])
  let nullableDecimal_kgpm2 = typedefof<System.Nullable<_>>.MakeGenericType [|dkgpm2 |]
```

### <a name="accessing-project-local-or-script-local-resources"></a><span data-ttu-id="ae76e-397">Uzyskiwanie dostępu do lokalnego projektu lub skryptów lokalnych zasobów</span><span class="sxs-lookup"><span data-stu-id="ae76e-397">Accessing Project-Local or Script-Local Resources</span></span>

<span data-ttu-id="ae76e-398">Każde wystąpienie dostawcy typów można podać `TypeProviderConfig` wartości w trakcie konstruowania.</span><span class="sxs-lookup"><span data-stu-id="ae76e-398">Each instance of a type provider can be given a `TypeProviderConfig` value during construction.</span></span> <span data-ttu-id="ae76e-399">Ta wartość zawiera "folder rozwiązania" dla dostawcy (czyli folderu projektu dla kompilacji lub katalogu, który zawiera skrypt), listę przywoływanych zestawów i inne informacje.</span><span class="sxs-lookup"><span data-stu-id="ae76e-399">This value contains the "resolution folder" for the provider (that is, the project folder for the compilation or the directory that contains a script), the list of referenced assemblies, and other information.</span></span>

### <a name="invalidation"></a><span data-ttu-id="ae76e-400">Unieważnieniu</span><span class="sxs-lookup"><span data-stu-id="ae76e-400">Invalidation</span></span>

<span data-ttu-id="ae76e-401">Dostawców może zgłosić sygnały unieważniania powiadomić usługi języka F #, która założeń schematu mógł ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="ae76e-401">Providers can raise invalidation signals to notify the F# language service that the schema assumptions may have changed.</span></span> <span data-ttu-id="ae76e-402">W przypadku unieważniania typecheck jest dokonania, jeśli dostawca jest hostowany w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ae76e-402">When invalidation occurs, a typecheck is redone if the provider is being hosted in Visual Studio.</span></span> <span data-ttu-id="ae76e-403">Sygnał ten zostanie zignorowany, gdy dostawca jest hostowana w F # Interactive lub przez kompilator F # (fsc.exe).</span><span class="sxs-lookup"><span data-stu-id="ae76e-403">This signal will be ignored when the provider is hosted in F# Interactive or by the F# Compiler (fsc.exe).</span></span>

### <a name="caching-schema-information"></a><span data-ttu-id="ae76e-404">Buforowanie informacji o schemacie</span><span class="sxs-lookup"><span data-stu-id="ae76e-404">Caching Schema Information</span></span>

<span data-ttu-id="ae76e-405">Dostawców często pamięci podręcznej dostęp do informacji o schemacie.</span><span class="sxs-lookup"><span data-stu-id="ae76e-405">Providers must often cache access to schema information.</span></span> <span data-ttu-id="ae76e-406">Powinny być przechowywane dane w pamięci podręcznej przy użyciu nazwy pliku, który znajduje się jako statyczne parametru lub danych użytkownika.</span><span class="sxs-lookup"><span data-stu-id="ae76e-406">The cached data should be stored by using a file name that's given as a static parameter or as user data.</span></span> <span data-ttu-id="ae76e-407">Na przykład pamięci podręcznej schematu `LocalSchemaFile` parametru w dostawcy typów w `FSharp.Data.TypeProviders` zestawu.</span><span class="sxs-lookup"><span data-stu-id="ae76e-407">An example of schema caching is the `LocalSchemaFile` parameter in the type providers in the `FSharp.Data.TypeProviders` assembly.</span></span> <span data-ttu-id="ae76e-408">W celu wykonania tych dostawców ten parametr statyczne poleca dostawcę typów, które mają być używane informacje schematu w określonym pliku lokalnego zamiast uzyskiwanie dostępu do źródła danych za pośrednictwem sieci.</span><span class="sxs-lookup"><span data-stu-id="ae76e-408">In the implementation of these providers, this static parameter directs the type provider to use the schema information in the specified local file instead of accessing the data source over the network.</span></span> <span data-ttu-id="ae76e-409">Aby korzystać z buforowanych informacji o schemacie, można również ustawić parametr static `ForceUpdate` do `false`.</span><span class="sxs-lookup"><span data-stu-id="ae76e-409">To use cached schema information, you must also set the static parameter `ForceUpdate` to `false`.</span></span> <span data-ttu-id="ae76e-410">Można użyć podobne techniki umożliwiające dostęp do danych w trybie online i offline.</span><span class="sxs-lookup"><span data-stu-id="ae76e-410">You could use a similar technique to enable online and offline data access.</span></span>

### <a name="backing-assembly"></a><span data-ttu-id="ae76e-411">Tworzenie kopii zestawu</span><span class="sxs-lookup"><span data-stu-id="ae76e-411">Backing Assembly</span></span>

<span data-ttu-id="ae76e-412">Gdy kompilujesz `.dll` lub `.exe` pliku, plik .dll zapasowy wygenerowane typy są łączone statycznie do wynikowego zestawu.</span><span class="sxs-lookup"><span data-stu-id="ae76e-412">When you compile a `.dll` or `.exe` file, the backing .dll file for generated types is statically linked into the resulting assembly.</span></span> <span data-ttu-id="ae76e-413">Ten link jest tworzony przez skopiowanie definicje typów języka pośredniego (IL) i wszelkie zarządzane zasoby z zestawu zapasowy w końcowym zestawie.</span><span class="sxs-lookup"><span data-stu-id="ae76e-413">This link is created by copying the Intermediate Language (IL) type definitions and any managed resources from the backing assembly into the final assembly.</span></span> <span data-ttu-id="ae76e-414">Podczas korzystania z F # Interactive, tworzenie kopii pliku .dll nie zostaną skopiowane i zamiast tego są ładowane bezpośrednio do procesu F # Interactive.</span><span class="sxs-lookup"><span data-stu-id="ae76e-414">When you use F# Interactive, the backing .dll file isn't copied and is instead loaded directly into the F# Interactive process.</span></span>

### <a name="exceptions-and-diagnostics-from-type-providers"></a><span data-ttu-id="ae76e-415">Wyjątki i Diagnostyka z dostawcami typów</span><span class="sxs-lookup"><span data-stu-id="ae76e-415">Exceptions and Diagnostics from Type Providers</span></span>

<span data-ttu-id="ae76e-416">Wszystkie przypadki użycia wszystkich członków z podane typy może zgłaszać wyjątki.</span><span class="sxs-lookup"><span data-stu-id="ae76e-416">All uses of all members from provided types may throw exceptions.</span></span> <span data-ttu-id="ae76e-417">We wszystkich przypadkach jeśli dostawca typów zgłasza wyjątek, kompilator hosta atrybutów błąd dostawcy określonego typu.</span><span class="sxs-lookup"><span data-stu-id="ae76e-417">In all cases, if a type provider throws an exception, the host compiler attributes the error to a specific type provider.</span></span>

- <span data-ttu-id="ae76e-418">Typ dostawcy wyjątki nigdy nie powinno spowodować wewnętrzne błędy kompilatora.</span><span class="sxs-lookup"><span data-stu-id="ae76e-418">Type provider exceptions should never result in internal compiler errors.</span></span>

- <span data-ttu-id="ae76e-419">Dostawcy typów nie można zgłosić ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="ae76e-419">Type providers can't report warnings.</span></span>

- <span data-ttu-id="ae76e-420">Gdy dostawca typów znajduje się w kompilatorze F #, środowiska deweloperskiego F # lub F # Interactive, wszystkie wyjątki z tego dostawcy są przechwytywane.</span><span class="sxs-lookup"><span data-stu-id="ae76e-420">When a type provider is hosted in the F# compiler, an F# development environment, or F# Interactive, all exceptions from that provider are caught.</span></span> <span data-ttu-id="ae76e-421">Właściwości wiadomości, zawsze jest tekst błędu i zostanie wyświetlone nie ślad stosu.</span><span class="sxs-lookup"><span data-stu-id="ae76e-421">The Message property is always the error text, and no stack trace appears.</span></span> <span data-ttu-id="ae76e-422">Jeśli zamierzasz zgłosić wyjątek, może zgłosić następujące przykłady: `System.NotSupportedException`, `System.IO.IOException`, `System.Exception`.</span><span class="sxs-lookup"><span data-stu-id="ae76e-422">If you’re going to throw an exception, you can throw the following examples: `System.NotSupportedException`, `System.IO.IOException`, `System.Exception`.</span></span>

#### <a name="providing-generated-types"></a><span data-ttu-id="ae76e-423">Zapewnianie wygenerowane typy</span><span class="sxs-lookup"><span data-stu-id="ae76e-423">Providing Generated Types</span></span>

<span data-ttu-id="ae76e-424">Do tej pory ten dokument ma wyjaśniono, jak zawierają typy wymazane.</span><span class="sxs-lookup"><span data-stu-id="ae76e-424">So far, this document has explained how to provide erased types.</span></span> <span data-ttu-id="ae76e-425">Umożliwia także mechanizm dostawcy typu F # zapewnienie wygenerowane typy, które są dodawane jako rzeczywiste definicje typów .NET do użytkowników programu.</span><span class="sxs-lookup"><span data-stu-id="ae76e-425">You can also use the type provider mechanism in F# to provide generated types, which are added as real .NET type definitions into the users' program.</span></span> <span data-ttu-id="ae76e-426">Użytkownik musi odwoływać się do wygenerowanego dostarczone typy przy użyciu definicji typu.</span><span class="sxs-lookup"><span data-stu-id="ae76e-426">You must refer to generated provided types by using a type definition.</span></span>

```fsharp
open Microsoft.FSharp.TypeProviders 

type Service = ODataService<"http://services.odata.org/Northwind/Northwind.svc/">
```

<span data-ttu-id="ae76e-427">Kod pomocniczy ProvidedTypes 0.2, który jest częścią wersji języka F # 3.0 tylko ma ograniczoną obsługę zapewniające wygenerowane typy.</span><span class="sxs-lookup"><span data-stu-id="ae76e-427">The ProvidedTypes-0.2 helper code that is part of the F# 3.0 release has only limited support for providing generated types.</span></span> <span data-ttu-id="ae76e-428">Poniższe instrukcje muszą być spełnione dla definicji wygenerowany typ:</span><span class="sxs-lookup"><span data-stu-id="ae76e-428">The following statements must be true for a generated type definition:</span></span>

- <span data-ttu-id="ae76e-429">`isErased` musi być równa `false`.</span><span class="sxs-lookup"><span data-stu-id="ae76e-429">`isErased` must be set to `false`.</span></span>

- <span data-ttu-id="ae76e-430">Wygenerowany typ musi zostać dodany do nowo skonstruowany `ProvidedAssembly()`, który reprezentuje kontener dla fragmentów wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="ae76e-430">The generated type must be added to a newly constructed `ProvidedAssembly()`, which represents a container for generated code fragments.</span></span>

- <span data-ttu-id="ae76e-431">Dostawca musi mieć zestaw, który ma plik .dll .NET zapasowy rzeczywiste z pliku .dll pasujące na dysku.</span><span class="sxs-lookup"><span data-stu-id="ae76e-431">The provider must have an assembly that has an actual backing .NET .dll file with a matching .dll file on disk.</span></span>

## <a name="rules-and-limitations"></a><span data-ttu-id="ae76e-432">Reguły i ograniczenia</span><span class="sxs-lookup"><span data-stu-id="ae76e-432">Rules and Limitations</span></span>

<span data-ttu-id="ae76e-433">Podczas pisania dostawców typów pamiętać o następujących reguł i ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="ae76e-433">When you write type providers, keep the following rules and limitations in mind.</span></span>

### <a name="provided-types-must-be-reachable"></a><span data-ttu-id="ae76e-434">Podane typy musi być dostępny</span><span class="sxs-lookup"><span data-stu-id="ae76e-434">Provided types must be reachable</span></span>

<span data-ttu-id="ae76e-435">Wszystko pod warunkiem, że typy powinny być dostępne z typami-nested.</span><span class="sxs-lookup"><span data-stu-id="ae76e-435">All provided types should be reachable from the non-nested types.</span></span> <span data-ttu-id="ae76e-436">Zagnieżdżone typy są podane w wywołaniu `TypeProviderForNamespaces` konstruktora lub wywołanie `AddNamespace`.</span><span class="sxs-lookup"><span data-stu-id="ae76e-436">The non-nested types are given in the call to the `TypeProviderForNamespaces` constructor or a call to `AddNamespace`.</span></span> <span data-ttu-id="ae76e-437">Na przykład, jeśli dostawca zawiera typ `StaticClass.P : T`, należy upewnić się, że T jest typem-nested lub zagnieżdżony w ramach jednego.</span><span class="sxs-lookup"><span data-stu-id="ae76e-437">For example, if the provider provides a type `StaticClass.P : T`, you must ensure that T is either a non-nested type or nested under one.</span></span>

<span data-ttu-id="ae76e-438">Na przykład niektórzy dostawcy udostępniają statyczne klasy takie jak `DataTypes` zawierają te `T1, T2, T3, ...` typów.</span><span class="sxs-lookup"><span data-stu-id="ae76e-438">For example, some providers have a static class such as `DataTypes` that contain these `T1, T2, T3, ...` types.</span></span> <span data-ttu-id="ae76e-439">W przeciwnym razie błąd mówi, że odwołanie do typu T w zestawie, A został znaleziony, ale nie można odnaleźć typu, w tym zestawie.</span><span class="sxs-lookup"><span data-stu-id="ae76e-439">Otherwise, the error says that a reference to type T in assembly A was found, but the type couldn't be found in that assembly.</span></span> <span data-ttu-id="ae76e-440">Jeśli ten błąd występuje, sprawdź, czy wszystkie swoje podtypy można można połączyć się z dostawcą typów.</span><span class="sxs-lookup"><span data-stu-id="ae76e-440">If this error appears, verify that all your subtypes can be reached from the provider types.</span></span> <span data-ttu-id="ae76e-441">Uwaga: Te `T1, T2, T3...` typy są nazywane *na bieżąco* typów.</span><span class="sxs-lookup"><span data-stu-id="ae76e-441">Note: These `T1, T2, T3...` types are referred to as the *on-the-fly* types.</span></span> <span data-ttu-id="ae76e-442">Pamiętaj, aby umieścić je w przestrzeni nazw usługi dostępne lub w typie elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="ae76e-442">Remember to put them in an accessible namespace or a parent type.</span></span>

### <a name="limitations-of-the-type-provider-mechanism"></a><span data-ttu-id="ae76e-443">Ograniczenia dotyczące mechanizmu dostawcy typów</span><span class="sxs-lookup"><span data-stu-id="ae76e-443">Limitations of the Type Provider Mechanism</span></span>

<span data-ttu-id="ae76e-444">Mechanizm dostawcy typu F # ma następujące ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="ae76e-444">The type provider mechanism in F# has the following limitations:</span></span>

- <span data-ttu-id="ae76e-445">Podstawowej infrastruktury dla dostawców typów języka F # nie obsługuje, pod warunkiem ogólnych typów lub podano metod ogólnych.</span><span class="sxs-lookup"><span data-stu-id="ae76e-445">The underlying infrastructure for type providers in F# doesn't support provided generic types or provided generic methods.</span></span>

- <span data-ttu-id="ae76e-446">Mechanizm nie obsługuje zagnieżdżone typy z parametry statyczne.</span><span class="sxs-lookup"><span data-stu-id="ae76e-446">The mechanism doesn't support nested types with static parameters.</span></span>

## <a name="development-tips"></a><span data-ttu-id="ae76e-447">Porady dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="ae76e-447">Development Tips</span></span>

<span data-ttu-id="ae76e-448">Poniższe porady mogą być przydatne podczas procesu projektowania.</span><span class="sxs-lookup"><span data-stu-id="ae76e-448">You might find the following tips helpful during the development process.</span></span>

### <a name="run-two-instances-of-visual-studio"></a><span data-ttu-id="ae76e-449">Uruchom dwa wystąpienia programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ae76e-449">Run Two Instances of Visual Studio</span></span>

<span data-ttu-id="ae76e-450">Można tworzyć dostawcy typów w jednym wystąpieniu i test dostawcy w innym, ponieważ test IDE zajmie blokadę na plik .dll, który uniemożliwia dostawcy typów była ponownie kompilowana.</span><span class="sxs-lookup"><span data-stu-id="ae76e-450">You can develop the type provider in one instance and test the provider in the other because the test IDE will take a lock on the .dll file that prevents the type provider from being rebuilt.</span></span> <span data-ttu-id="ae76e-451">W związku z tym należy zamknąć drugiego wystąpienia programu Visual Studio podczas dostawcy jest wbudowana w pierwszej kolejności, a następnie po utworzeniu dostawcy należy ponownie drugie wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="ae76e-451">Thus, you must close the second instance of Visual Studio while the provider is built in the first instance, and then you must reopen the second instance after the provider is built.</span></span>

### <a name="debug-type-providers-by-using-invocations-of-fscexe"></a><span data-ttu-id="ae76e-452">Debugowanie dostawców typów za pomocą wywołania fsc.exe</span><span class="sxs-lookup"><span data-stu-id="ae76e-452">Debug type providers by using invocations of fsc.exe</span></span>

<span data-ttu-id="ae76e-453">Dostawcy typów można wywołać za pomocą następujących narzędzi:</span><span class="sxs-lookup"><span data-stu-id="ae76e-453">You can invoke type providers by using the following tools:</span></span>

- <span data-ttu-id="ae76e-454">FSC.exe (kompilator F # wiersza polecenia)</span><span class="sxs-lookup"><span data-stu-id="ae76e-454">fsc.exe (The F# command line compiler)</span></span>

- <span data-ttu-id="ae76e-455">fsi.exe (kompilator F # Interactive)</span><span class="sxs-lookup"><span data-stu-id="ae76e-455">fsi.exe (The F# Interactive compiler)</span></span>

- <span data-ttu-id="ae76e-456">Devenv.exe (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="ae76e-456">devenv.exe (Visual Studio)</span></span>

<span data-ttu-id="ae76e-457">Dostawcy typów można debugować często najłatwiej przy użyciu fsc.exe w pliku skryptu testu (na przykład script.fsx).</span><span class="sxs-lookup"><span data-stu-id="ae76e-457">You can often debug type providers most easily by using fsc.exe on a test script file (for example, script.fsx).</span></span> <span data-ttu-id="ae76e-458">Można uruchomić debugera z poziomu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="ae76e-458">You can launch a debugger from a command prompt.</span></span>

```
  devenv /debugexe fsc.exe script.fsx
```

  <span data-ttu-id="ae76e-459">Możesz użyć rejestrowania drukowania do strumienia wyjściowego stdout.</span><span class="sxs-lookup"><span data-stu-id="ae76e-459">You can use print-to-stdout logging.</span></span>

## <a name="see-also"></a><span data-ttu-id="ae76e-460">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ae76e-460">See also</span></span>

- [<span data-ttu-id="ae76e-461">Dostawcy typów</span><span class="sxs-lookup"><span data-stu-id="ae76e-461">Type Providers</span></span>](index.md)
- [<span data-ttu-id="ae76e-462">Dostawcy typów zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="ae76e-462">The Type Provider SDK</span></span>](https://github.com/fsprojects/FSharp.TypeProviders.SDK)
