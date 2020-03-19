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
# <a name="tutorial-create-a-type-provider"></a>Samouczek: Tworzenie dostawcy typów

Mechanizm dostawcy typu w języku F# jest istotną częścią jego obsługi programowania bogatego w informacje. W tym samouczku wyjaśniono, jak utworzyć własne dostawców typów, przechodząc przez rozwój kilku dostawców typów prostych, aby zilustrować podstawowe pojęcia. Aby uzyskać więcej informacji na temat mechanizmu dostawcy typu w języku F#, zobacz [Typ providers](index.md).

Ekosystem F# zawiera szereg dostawców typów dla powszechnie używanych usług danych internetowych i korporacyjnych. Przykład:

- [FSharp.Data](https://fsharp.github.io/FSharp.Data/) obejmuje dostawców typów dla formatów dokumentów JSON, XML, CSV i HTML.

- [SQLProvider](https://fsprojects.github.io/SQLProvider/) zapewnia silnie typiwany dostęp do baz danych SQL za pośrednictwem mapowania obiektów i F# LINQ kwerendy dla tych źródeł danych.

- [FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) ma zestaw dostawców typów do skompilowania w czasie sprawdzane osadzanie T-SQL w języku F#.

- [FSharp.Data.TypeProviders](https://fsprojects.github.io/FSharp.Data.TypeProviders/) jest starszym zestawem dostawców typów do użytku tylko z programowaniem .NET Framework w celu uzyskania dostępu do usług danych SQL, Entity Framework, OData i WSDL.

W razie potrzeby można utworzyć dostawców typów niestandardowych lub odwoływać się do dostawców typów utworzonych przez inne osoby. Na przykład organizacja może mieć usługę danych, która zapewnia dużą i rosnącą liczbę nazwanych zestawów danych, z których każdy ma własny schemat danych stabilnych. Można utworzyć dostawcę typów, który odczytuje schematy i przedstawia bieżące zestawy danych programisty w sposób silnie typiwany.

## <a name="before-you-start"></a>Przed rozpoczęciem

Mechanizm dostawcy typu jest przeznaczony przede wszystkim do wstrzykiwania stabilnych przestrzeni informacji o danych i usługach do środowiska programowania Języka F#.

Ten mechanizm nie jest przeznaczony do wstrzykiwania przestrzeni informacyjnych, których schemat zmienia się podczas wykonywania programu w sposób, który jest odpowiedni dla logiki programu. Ponadto mechanizm nie jest przeznaczony do metaprogramowanie wewnątrz języka, mimo że ta domena zawiera kilka prawidłowych zastosowań. Należy użyć tego mechanizmu tylko wtedy, gdy jest to konieczne i gdy rozwój dostawcy typu daje bardzo wysoką wartość.

Należy unikać pisania dostawcy typu, gdzie schemat nie jest dostępny. Podobnie należy unikać pisania dostawcy typu, gdzie wystarczy zwykła (lub nawet istniejąca) biblioteka .NET.

Przed rozpoczęciem można zadawać następujące pytania:

- Czy masz schemat dla źródła informacji? Jeśli tak, co to jest mapowanie do systemu typu F# i .NET?

- Czy można użyć istniejącego (dynamicznie wpisywany) interfejsu API jako punktu wyjścia dla implementacji?

- Czy ty i Twoja organizacja będziecie mieli wystarczająco dużo zastosowań dostawcy typu, aby pisanie było opłacalne? Czy normalna biblioteka .NET spełni Twoje potrzeby?

- Jak bardzo zmieni się schemat?

- Czy zmieni się podczas kodowania?

- Czy zmieni się między sesjami kodowania?

- Czy zmieni się podczas wykonywania programu?

Dostawcy typów najlepiej nadają się do sytuacji, w których schemat jest stabilny w czasie wykonywania i w okresie istnienia skompilowanego kodu.

## <a name="a-simple-type-provider"></a>Prosty dostawca typów

Ten przykład jest Samples.HelloWorldTypeProvider, podobne do `examples` przykładów w katalogu [SDK dostawcy typu F#](https://github.com/fsprojects/FSharp.TypeProviders.SDK/). Dostawca udostępnia "przestrzeń typu", która zawiera 100 wymazanych typów, jak pokazano w poniższym kodzie przy użyciu składni podpisu F# i pomijając szczegóły dla wszystkich z wyjątkiem `Type1`. Aby uzyskać więcej informacji na temat typów wymazanych, zobacz [Szczegółowe informacje o wymazanych podana typy](#details-about-erased-provided-types) w dalszej części tego tematu.

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

Należy zauważyć, że zestaw typów i elementów członkowskich pod warunkiem jest statycznie znane. W tym przykładzie nie wykorzystuje możliwości dostawców do zapewnienia typów, które zależą od schematu. Implementacja dostawcy typu jest opisana w poniższym kodzie, a szczegóły są omówione w kolejnych sekcjach tego tematu.

> [!WARNING]
> Mogą występować różnice między tym kodem a próbkami online.

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

Aby użyć tego dostawcy, otwórz oddzielne wystąpienie programu Visual Studio, utwórz skrypt Języka F#, a następnie dodaj odwołanie do dostawcy ze skryptu przy użyciu #r, jak pokazuje następujący kod:

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

Następnie poszukaj `Samples.HelloWorldTypeProvider` typów w obszarze nazw, który wygenerował dostawca typu.

Przed ponownym skompiluj dostawcę, upewnij się, że zostały zamknięte wszystkie wystąpienia programu Visual Studio i F# Interactive, które są przy użyciu biblioteki DLL dostawcy. W przeciwnym razie wystąpi błąd kompilacji, ponieważ wyjściowa biblioteka DLL zostanie zablokowana.

Aby debugować tego dostawcę przy użyciu instrukcji drukowania, należy wykonać skrypt, który udostępnia problem z dostawcą, a następnie użyć następującego kodu:

```console
fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

Aby debugować tego dostawcę przy użyciu programu Visual Studio, otwórz wiersz polecenia dewelopera dla programu Visual Studio z poświadczeniami administracyjnymi i uruchom następujące polecenie:

```console
devenv.exe /debugexe fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

Alternatywnie otwórz program Visual Studio, otwórz menu `Debug/Attach to process…`debugowania, `devenv` wybierz opcję i dołącz do innego procesu, w którym edytujesz skrypt. Za pomocą tej metody, można łatwiej kierować określonej logiki w dostawcy typu przez interaktywne wpisywanie wyrażeń w drugim wystąpieniu (z pełnym IntelliSense i innych funkcji).

Można wyłączyć debugowanie tylko mój kod, aby lepiej zidentyfikować błędy w wygenerowanym kodzie. Aby uzyskać informacje dotyczące włączania lub wyłączania tej funkcji, zobacz [Nawigowanie po kodzie za pomocą debugera](/visualstudio/debugger/navigating-through-code-with-the-debugger). Można również ustawić przechwytywanie wyjątków pierwszej `Debug` szansy, `Exceptions` otwierając menu, a następnie wybierając lub wybierając `Exceptions` klawisze Ctrl+Alt+E, aby otworzyć okno dialogowe. W tym oknie `Common Language Runtime Exceptions`dialogowym `Thrown` w obszarze zaznacz pole wyboru.

### <a name="implementation-of-the-type-provider"></a>Implementacja dostawcy typu

W tej sekcji przeprowadzi Cię przez główne sekcje implementacji dostawcy typu. Najpierw należy zdefiniować typ dla samego dostawcy typu niestandardowego:

```fsharp
[<TypeProvider>]
type SampleTypeProvider(config: TypeProviderConfig) as this =
```

Ten typ musi być publiczny i należy oznaczyć go atrybutem [TypeProvider,](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947) aby kompilator rozpoznał dostawcę typu, gdy oddzielny projekt F# odwołuje się do zestawu zawierającego typ. Parametr *config* jest opcjonalny, a jeśli jest obecny, zawiera informacje o konfiguracji kontekstowej dla wystąpienia dostawcy typu tworzonego przez kompilator języka F#.

Następnie zaimplementujesz interfejs [ITypeProvider.](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f) W takim przypadku należy `TypeProviderForNamespaces` użyć `ProvidedTypes` typu z interfejsu API jako typu podstawowego. Ten typ pomocnika może zapewnić skończoną kolekcję chętnie podanych obszarów nazw, z których każdy bezpośrednio zawiera skończoną liczbę stałych, chętnie dostarczonych typów. W tym kontekście dostawca *chętnie* generuje typy, nawet jeśli nie są one potrzebne lub używane.

```fsharp
inherit TypeProviderForNamespaces(config)
```

Następnie zdefiniuj lokalne wartości prywatne, które określają obszar nazw dla podanych typów, i znajdź sam zestaw dostawcy typu. Ten zestaw jest później używany jako logiczny typ nadrzędny wymazanych typów, które są dostarczane.

```fsharp
let namespaceName = "Samples.HelloWorldTypeProvider"
let thisAssembly = Assembly.GetExecutingAssembly()
```

Następnie utwórz funkcję, aby zapewnić każdy z typów Type1... Typ100. Ta funkcja jest wyjaśniona bardziej szczegółowo w dalszej części tego tematu.

```fsharp
let makeOneProvidedType (n:int) = …
```

Następnie wygeneruj 100 dostarczonych typów:

```fsharp
let types = [ for i in 1 .. 100 -> makeOneProvidedType i ]
```

Następnie dodaj typy jako dostarczoną przestrzeń nazw:

```fsharp
do this.AddNamespace(namespaceName, types)
```

Na koniec dodaj atrybut zestawu, który wskazuje, że tworzysz bibliotekę DLL dostawcy typów:

```fsharp
[<assembly:TypeProviderAssembly>]
do()
```

### <a name="providing-one-type-and-its-members"></a>Zapewnienie jednego typu i jego członków

Funkcja `makeOneProvidedType` wykonuje rzeczywistą pracę dostarczania jednego z typów.

```fsharp
let makeOneProvidedType (n:int) =
…
```

Ten krok wyjaśnia implementację tej funkcji. Najpierw należy utworzyć podany typ (na przykład Typ1, gdy n = 1 lub Type57, gdy n = 57).

```fsharp
// This is the provided type. It is an erased provided type and, in compiled code,
// will appear as type 'obj'.
let t = ProvidedTypeDefinition(thisAssembly, namespaceName,
                               "Type" + string n,
                               baseType = Some typeof<obj>)
```

Należy zwrócić uwagę na następujące punkty:

- Ten podany typ jest usuwany.  Ponieważ wskazujesz, że `obj`typem podstawowym jest , wystąpienia będą wyświetlane jako wartości typu [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) w skompilowanym kodzie.

- Po określeniu typu niezagnieżdżonego należy określić zestaw i obszar nazw. W przypadku typów wymazanych zestaw powinien być samym zestawem dostawcy typu.

Następnie dodaj dokumentację XML do typu. Ta dokumentacja jest opóźniona, czyli obliczana na żądanie, jeśli kompilator hosta jej potrzebuje.

```fsharp
t.AddXmlDocDelayed (fun () -> sprintf "This provided type %s" ("Type" + string n))
```

Następnie należy dodać podana właściwość statyczną do typu:

```fsharp
let staticProp = ProvidedProperty(propertyName = "StaticProperty",
                                  propertyType = typeof<string>,
                                  isStatic = true,
                                  getterCode = (fun args -> <@@ "Hello!" @@>))
```

Pierwsze tej właściwości zawsze oceni ciąg "Hello!". Dla `GetterCode` właściwości używa oferty F#, która reprezentuje kod, który kompilator hosta generuje do uzyskania właściwości. Aby uzyskać więcej informacji na temat ofert, zobacz [Oferty kodowe (F#)](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155).

Dodaj dokumentację XML do właściwości.

```fsharp
staticProp.AddXmlDocDelayed(fun () -> "This is a static property")
```

Teraz dołącz dostarczoną właściwość do podanego typu. Należy dołączyć dostarczony element członkowski do jednego i tylko jednego typu. W przeciwnym razie element członkowski nigdy nie będzie dostępny.

```fsharp
t.AddMember staticProp
```

Teraz utwórz dostarczony konstruktor, który nie przyjmuje żadnych parametrów.

```fsharp
let ctor = ProvidedConstructor(parameters = [ ],
                               invokeCode = (fun args -> <@@ "The object data" :> obj @@>))
```

Dla `InvokeCode` konstruktora zwraca ofertę F#, która reprezentuje kod, który generuje kompilator hosta, gdy konstruktor jest wywoływany. Na przykład można użyć następującego konstruktora:

```fsharp
new Type10()
```

Wystąpienie podanego typu zostanie utworzone z danymi źródłowymi "Dane obiektu". Cytowany kod zawiera konwersję do [obj,](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) ponieważ ten typ jest wymazaniem tego typu pod warunkiem (jak określono podczas deklarowania podanego typu).

Dodaj dokumentację XML do konstruktora i dodaj dostarczony konstruktor do podanego typu:

```fsharp
ctor.AddXmlDocDelayed(fun () -> "This is a constructor")

t.AddMember ctor
```

Utwórz drugi dostarczony konstruktor, który przyjmuje jeden parametr:

```fsharp
let ctor2 =
ProvidedConstructor(parameters = [ ProvidedParameter("data",typeof<string>) ],
                    invokeCode = (fun args -> <@@ (%%(args.[0]) : string) :> obj @@>))
```

Dla `InvokeCode` konstruktora ponownie zwraca ofertę Języka F#, która reprezentuje kod, który kompilator hosta generowane dla wywołania metody. Na przykład można użyć następującego konstruktora:

```fsharp
new Type10("ten")
```

Wystąpienie podanego typu jest tworzony z podstawowych danych "dziesięć". Być może zauważyłeś już, że `InvokeCode` funkcja zwraca ofertę. Dane wejściowe do tej funkcji to lista wyrażeń, jeden na parametr konstruktora. W takim przypadku wyrażenie reprezentujące wartość pojedynczego `args.[0]`parametru jest dostępne w pliku . Kod wywołania konstruktora powoduje wymuszanie wartości zwracanej do typu `obj`wymazanego. Po dodaniu drugiego dostarczonego konstruktora do typu należy utworzyć dostarczoną właściwość wystąpienia:

```fsharp
let instanceProp =
    ProvidedProperty(propertyName = "InstanceProperty",
                     propertyType = typeof<int>,
                     getterCode= (fun args ->
                        <@@ ((%%(args.[0]) : obj) :?> string).Length @@>))
instanceProp.AddXmlDocDelayed(fun () -> "This is an instance property")
t.AddMember instanceProp
```

Pierwsze tej właściwości zwróci długość ciągu, który jest obiektem reprezentacji. Właściwość `GetterCode` zwraca ofertę Języka F#, która określa kod, który kompilator hosta generuje, aby uzyskać właściwość. Like `InvokeCode`, `GetterCode` funkcja zwraca ofertę. Kompilator hosta wywołuje tę funkcję z listą argumentów. W takim przypadku argumenty obejmują tylko pojedyncze wyrażenie, które reprezentuje wystąpienie, na którym `args.[0]`wywoływane jest wywoływane wywoływane wywoływane przez getter, do którego można uzyskać dostęp za pomocą programu . Implementacja `GetterCode` następnie splices do cytatu wynik na `obj`typ wymazane , a rzutowanie jest używany do spełnienia mechanizm kompilatora do sprawdzania typów, że obiekt jest ciągiem. Następna część `makeOneProvidedType` zawiera metodę wystąpienia z jednym parametrem.

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

Na koniec utwórz typ zagnieżdżony, który zawiera 100 właściwości zagnieżdżonych. Tworzenie tego typu zagnieżdżonego i jego właściwości jest opóźnione, czyli obliczane na żądanie.

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

### <a name="details-about-erased-provided-types"></a>Szczegółowe informacje o wymazanych typach dostarczonych

Przykład w tej sekcji zawiera tylko *wymazane podane typy,* które są szczególnie przydatne w następujących sytuacjach:

- Podczas pisania dostawcy dla przestrzeni informacyjnej, która zawiera tylko dane i metody.

- Podczas pisania dostawcy, gdzie dokładne semantyka typu środowiska uruchomieniowego nie są krytyczne dla praktycznego wykorzystania przestrzeni informacyjnej.

- Podczas pisania dostawcy dla przestrzeni informacyjnej, która jest tak duża i wzajemnie połączona, że nie jest technicznie wykonalne do generowania rzeczywistych typów .NET dla przestrzeni informacyjnej.

W tym przykładzie każdy podany typ `obj`jest kasowany, aby wpisać `obj` , a wszystkie zastosowania tego typu będą wyświetlane jako typ w skompilowanym kodzie. W rzeczywistości podstawowe obiekty w tych przykładach są ciągi, `System.Object` ale typ pojawi się jak w .NET skompilowany kod. Podobnie jak w przypadku wszystkich zastosowań usuwania typu, można użyć jawnego boksu, rozpakowywania i rzucania w celu obalenia wymazanych typów. W takim przypadku wyjątek rzutu, który nie jest prawidłowy może spowodować, gdy obiekt jest używany. Środowisko uruchomieniowe dostawcy można zdefiniować swój własny typ reprezentacji prywatnej, aby chronić przed fałszywymi oświadczeniami. Nie można zdefiniować wymazane typy w języku F# się. Tylko podane typy mogą zostać wymazane. Należy zrozumieć konsekwencje, zarówno praktyczne i semantyczne, przy użyciu albo wymazane typy dla dostawcy typu lub dostawcy, który udostępnia usunięte typy. Typ wymazany nie ma prawdziwego typu .NET. W związku z tym nie można wykonać dokładne odbicie nad typem i może obalić wymazane typy, jeśli używasz rzutowania środowiska uruchomieniowego i innych technik, które opierają się na semantyki typu dokładnego środowiska uruchomieniowego. Subversion usuniętych typów często powoduje typu rzutowania wyjątków w czasie wykonywania.

### <a name="choosing-representations-for-erased-provided-types"></a>Wybieranie reprezentacji dla wymazanych typów

W przypadku niektórych zastosowań wymazanych typów dostarczonych nie jest wymagana reprezentacja. Na przykład wymazany pod warunkiem typu może zawierać tylko właściwości statyczne i elementy członkowskie i nie konstruktorów i żadnych metod lub właściwości zwróci wystąpienie typu. Jeśli można dotrzeć do wystąpień wymazanego typu dostarczonego, należy wziąć pod uwagę następujące pytania:

**Co to jest usuwanie podanego typu?**

- Usunięcie podanego typu jest sposób, w jaki typ pojawia się w skompilowanym kodzie .NET.

- Usunięcie podanego typu klasy wymazanej jest zawsze pierwszym nieskażonym typem podstawowym w łańcuchu dziedziczenia typu.

- Usunięcie podanego typu usuniętego interfejsu jest `System.Object`zawsze .

**Jakie są reprezentacje podanego typu?**

- Zestaw możliwych obiektów dla wymazanego typu są nazywane jego reprezentacje. W przykładzie w tym dokumencie reprezentacje wszystkich wymazanych typów `Type1..Type100` dostarczonych są zawsze obiektami ciągów.

Wszystkie reprezentacje dostarczonego typu muszą być zgodne z usunięciem podanego typu. (W przeciwnym razie kompilator Języka F# poda błąd podczas korzystania z dostawcy typu lub zostanie wygenerowany nieweryfikowalny kod .NET, który nie jest prawidłowy. Dostawca typu nie jest prawidłowy, jeśli zwraca kod, który daje reprezentację, która nie jest prawidłowa.)

Można wybrać reprezentację dla podanych obiektów przy użyciu jednego z następujących podejść, z których oba są bardzo powszechne:

- Jeśli po prostu udostępniasz silnie wpisane otoki nad istniejącym typem .NET, często ma sens, aby typ został wymazany do tego typu, użyj wystąpień tego typu jako reprezentacji lub obu. Takie podejście jest właściwe, gdy większość istniejących metod na tego typu nadal mają sens podczas korzystania z wersji silnie typizowane.

- Jeśli chcesz utworzyć interfejs API, który znacznie różni się od istniejącego interfejsu API platformy .NET, warto utworzyć typy środowiska uruchomieniowego, które będą wymazywaniem typu i reprezentacjami dla podanych typów.

W tym dokumencie użyto ciągów jako reprezentacji podanych obiektów. Często może być właściwe użycie innych obiektów do reprezentacji. Na przykład można użyć słownika jako worka właściwości:

```fsharp
ProvidedConstructor(parameters = [],
    invokeCode= (fun args -> <@@ (new Dictionary<string,obj>()) :> obj @@>))
```

Alternatywnie można zdefiniować typ w dostawcy typu, który będzie używany w czasie wykonywania do tworzenia reprezentacji, wraz z jedną lub kilkoma operacjami środowiska uruchomieniowego:

```fsharp
type DataObject() =
    let data = Dictionary<string,obj>()
    member x.RuntimeOperation() = data.Count
```

Pod warunkiem, że członkowie mogą następnie konstruować wystąpienia tego typu obiektu:

```fsharp
ProvidedConstructor(parameters = [],
    invokeCode= (fun args -> <@@ (new DataObject()) :> obj @@>))
```

W takim przypadku można (opcjonalnie) użyć tego typu jako usunięcia typu, `baseType` określając ten `ProvidedTypeDefinition`typ jako podczas konstruowania:

```fsharp
ProvidedTypeDefinition(…, baseType = Some typeof<DataObject> )
…
ProvidedConstructor(…, InvokeCode = (fun args -> <@@ new DataObject() @@>), …)
```

### <a name="key-lessons"></a>Kluczowe lekcje

W poprzedniej sekcji wyjaśniono, jak utworzyć prosty dostawca typów wymazywania, który udostępnia szereg typów, właściwości i metod. W tej sekcji wyjaśniono również pojęcie usuwania typu, w tym niektóre zalety i wady dostarczania wymazanych typów od dostawcy typu i omówione reprezentacje usuniętych typów.

## <a name="a-type-provider-that-uses-static-parameters"></a>Dostawca typów, który używa parametrów statycznych

Możliwość parametryzacji dostawców typów przez dane statyczne umożliwia wiele interesujących scenariuszy, nawet w przypadkach, gdy dostawca nie musi uzyskiwać dostępu do żadnych danych lokalnych lub zdalnych. W tej sekcji dowiesz się kilka podstawowych technik łączenia takiego dostawcy.

### <a name="type-checked-regex-provider"></a>Typ sprawdzonego dostawcy programu Regex

Wyobraź sobie, że chcesz zaimplementować dostawcę typów <xref:System.Text.RegularExpressions.Regex> dla wyrażeń regularnych, który otacza biblioteki .NET w interfejsie, który zapewnia następujące gwarancje czasu kompilacji:

- Sprawdzanie, czy wyrażenie regularne jest prawidłowe.

- Dostarczanie nazwanych właściwości na dopasowania, które są oparte na nazwach grup w wyrażeniu regularnym.

W tej sekcji pokazano, jak używać `RegexTyped` dostawców typów do tworzenia typu, który wzorzec wyrażenia regularnego parametryzuje, aby zapewnić te korzyści. Kompilator zgłosi błąd, jeśli dostarczony wzorzec nie jest prawidłowy, a dostawca typów może wyodrębnić grupy ze wzorca, dzięki czemu można uzyskać do nich dostęp przy użyciu nazwanych właściwości w dopasowaniach. Podczas projektowania dostawcy typu, należy wziąć pod uwagę, jak jego narażony interfejs API powinien wyglądać dla użytkowników końcowych i jak ten projekt przełoży się na kod .NET. W poniższym przykładzie pokazano, jak użyć takiego interfejsu API, aby uzyskać składniki kodu kierunkowego:

```fsharp
type T = RegexTyped< @"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)">
let reg = T()
let result = T.IsMatch("425-555-2345")
let r = reg.Match("425-555-2345").Group_AreaCode.Value //r equals "425"
```

W poniższym przykładzie pokazano, jak dostawca typów tłumaczy te wywołania:

```fsharp
let reg = new Regex(@"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)")
let result = reg.IsMatch("425-123-2345")
let r = reg.Match("425-123-2345").Groups.["AreaCode"].Value //r equals "425"
```

Pamiętaj o następujących kwestiach:

- Standardowy typ Regex reprezentuje `RegexTyped` typ sparametryzowany.

- Konstruktor `RegexTyped` powoduje wywołanie konstruktora Regex, przekazując w statycznym argumentem typu dla wzorca.

- Wyniki `Match` metody są reprezentowane przez <xref:System.Text.RegularExpressions.Match> typ standardowy.

- Każda nazwana grupa powoduje podaną właściwość, a dostęp do właściwości powoduje `Groups` użycie indeksatora w kolekcji dopasowania.

Poniższy kod jest rdzeniem logiki do zaimplementowania takiego dostawcy, a w tym przykładzie pomija dodanie wszystkich elementów członkowskich do podanego typu. Aby uzyskać informacje o każdym dodanym człoponiewędowym, zobacz odpowiednią sekcję w dalszej części tego tematu. Aby uzyskać pełny kod, pobierz przykład z [pakietu próbki F# 3.0](https://archive.codeplex.com/?p=fsharp3sample) w witrynie codeplex.

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

Pamiętaj o następujących kwestiach:

- Dostawca typu przyjmuje dwa parametry `pattern`statyczne: , który `options`jest obowiązkowy i , które są opcjonalne (ponieważ podano wartość domyślną).

- Po podasz argumenty statyczne, należy utworzyć wystąpienie wyrażenia regularnego. To wystąpienie zgłosi wyjątek, jeśli program Regex jest nieprawidłowo sformułowany, a ten błąd zostanie zgłoszony użytkownikom.

- W `DefineStaticParameters` ramach wywołania zwrotnego można zdefiniować typ, który zostanie zwrócony po podasz argumenty.

- Ten kod `HideObjectMethods` ustawia się na prawdziwe, dzięki czemu środowisko IntelliSense pozostanie usprawnione. Ten atrybut powoduje `Equals` `GetHashCode`, `Finalize`, `GetType` i elementy członkowskie mają być pomijane z list IntelliSense dla podanego obiektu.

- Używasz `obj` jako typ podstawowy metody, ale użyjesz `Regex` obiektu jako reprezentacji środowiska uruchomieniowego tego typu, jak pokazano w następnym przykładzie.

- Wywołanie konstruktora `Regex` <xref:System.ArgumentException> zgłasza, gdy wyrażenie regularne nie jest prawidłowe. Kompilator przechwytuje ten wyjątek i zgłasza komunikat o błędzie do użytkownika w czasie kompilacji lub w edytorze programu Visual Studio. Ten wyjątek umożliwia weryfikacji wyrażeń regularnych bez uruchamiania aplikacji.

Typ zdefiniowany powyżej nie jest jeszcze przydatne, ponieważ nie zawiera żadnych znaczących metod lub właściwości. Najpierw dodaj metodę `IsMatch` statyczną:

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

Poprzedni kod definiuje metodę `IsMatch`, która przyjmuje ciąg jako `bool`dane wejściowe i zwraca . Jedyną trudną częścią jest `args` użycie argumentu w `InvokeCode` definicji. W tym `args` przykładzie znajduje się lista cytatów, która reprezentuje argumenty tej metody. Jeśli metoda jest metodą wystąpienia, pierwszy `this` argument reprezentuje argument. Jednak dla metody statycznej argumenty są tylko jawne argumenty do metody. Należy zauważyć, że typ wartości cytowanej powinien być zgodny `bool`z określonym typem zwracanym (w tym przypadku). Należy również zauważyć, że `AddXmlDoc` ten kod używa metody, aby upewnić się, że podana metoda ma również użyteczną dokumentację, którą można dostarczyć za pośrednictwem intellisense.

Następnie dodaj wystąpienie Match metody. Jednak ta metoda powinna zwracać `Match` wartość podanego typu, dzięki czemu grupy są dostępne w sposób silnie typiwany. W związku z `Match` tym najpierw zadeklarować typ. Ponieważ ten typ zależy od wzorca, który został dostarczony jako argument statyczny, ten typ musi być zagnieżdżony w definicji typu sparametryzowanego:

```fsharp
let matchTy =
    ProvidedTypeDefinition(
        "MatchType",
        baseType = Some baseTy,
        hideObjectMethods = true)

ty.AddMember matchTy
```

Następnie należy dodać jedną właściwość do typu Dopasuj dla każdej grupy. W czasie wykonywania dopasowanie jest reprezentowana jako <xref:System.Text.RegularExpressions.Match> wartość, więc cytat, który <xref:System.Text.RegularExpressions.Match.Groups> definiuje właściwość musi użyć właściwości indeksowane, aby uzyskać odpowiednią grupę.

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

Ponownie należy zauważyć, że dodajesz dokumentację XML do dostarczonej właściwości. Należy również zauważyć, że właściwość może być odczytywana, jeśli `GetterCode` `SetterCode` funkcja jest dostępna, a właściwość może być zapisywana, jeśli funkcja jest dostępna, więc wynikowa właściwość jest tylko do odczytu.

Teraz można utworzyć metodę wystąpienia, która `Match` zwraca wartość tego typu:

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

Ponieważ tworzysz metodę wystąpienia, `args.[0]` reprezentuje `RegexTyped` wystąpienie, w którym metoda `args.[1]` jest wywoływana i jest argumentem wejściowym.

Na koniec podaj konstruktora, aby można było utworzyć wystąpienia podanego typu.

```fsharp
let ctor =
    ProvidedConstructor(
        parameters = [],
        invokeCode = fun args -> <@@ Regex(pattern, options) :> obj @@>)

ctor.AddXmlDoc("Initializes a regular expression instance.")

ty.AddMember ctor
```

Konstruktor tylko wymazuje do tworzenia standardowego wystąpienia regex .NET, który `obj` jest ponownie zapakowane do obiektu, ponieważ jest usunięcie podanego typu. Z tej zmiany, użycie przykładowego interfejsu API, który określony wcześniej w temacie działa zgodnie z oczekiwaniami. Poniższy kod jest kompletny i ostateczny:

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

### <a name="key-lessons"></a>Kluczowe lekcje

W tej sekcji wyjaśniono, jak utworzyć dostawcę typów, który działa na jego parametrów statycznych. Dostawca sprawdza parametr statyczny i udostępnia operacje na podstawie jego wartości.

## <a name="a-type-provider-that-is-backed-by-local-data"></a>Dostawca typów, który jest wspierany przez dane lokalne

Często można chcieć, aby dostawcy typów prezentują interfejsy API na podstawie nie tylko parametrów statycznych, ale także informacji z systemów lokalnych lub zdalnych. W tej sekcji omówiono dostawców typów, które są oparte na danych lokalnych, takich jak pliki danych lokalnych.

### <a name="simple-csv-file-provider"></a>Prosty dostawca plików CSV

Na przykład należy wziąć pod uwagę dostawcę typów dostępu do danych naukowych w formacie CSV (Comma Separated Value). W tej sekcji przyjęto założenie, że pliki CSV zawierają wiersz nagłówka, po którym następują dane zmiennoprzecinkowa, jak pokazano w poniższej tabeli:

|Odległość (metr)|Czas (drugi)|
|----------------|-------------|
|50.0|3.7|
|100.0|5.2|
|150.0|6.4|

W tej sekcji pokazano, jak podać typ, którego `Distance` można użyć, aby uzyskać wiersze z właściwością typu `float<meter>` i właściwością `Time` typu `float<second>`. Dla uproszczenia, następujące założenia są następujące:

- Nazwy nagłówków są bezeszli lub mają formę "Nazwa (jednostka)" i nie zawierają przecinków.

- Wszystkie jednostki są jednostkami System International (SI) zgodnie z definicją [modułu microsoft.FSharp.Data.UnitSystems.SI.UnitNames Module (F#).](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b)

- Jednostki są proste (na przykład miernik) zamiast związku (na przykład metr / sekundę).

- Wszystkie kolumny zawierają dane zmiennoprzecinkowe.

Bardziej kompletny dostawca poluzowałby te ograniczenia.

Ponownie pierwszym krokiem jest rozważenie, jak powinien wyglądać interfejs API. Biorąc `info.csv` pod uwagę plik z zawartością z poprzedniej tabeli (w formacie oddzielonym przecinkami), użytkownicy dostawcy powinni mieć możliwość pisania kodu podobnego do następującego przykładu:

```fsharp
let info = new MiniCsv<"info.csv">()
for row in info.Data do
let time = row.Time
printfn "%f" (float time)
```

W takim przypadku kompilator należy przekonwertować te wywołania na coś podobnego do następującego przykładu:

```fsharp
let info = new CsvFile("info.csv")
for row in info.Data do
let (time:float) = row.[1]
printfn "%f" (float time)
```

Optymalne tłumaczenie będzie wymagać dostawcy `CsvFile` typu do zdefiniowania typu rzeczywistego w zestawie dostawcy typu. Dostawcy typów często polegają na kilku typach i metodach pomocnika, aby zawinąć ważną logikę. Ponieważ miary są usuwane w czasie wykonywania, można użyć `float[]` jako typ wymazane dla wiersza. Kompilator będzie traktować różne kolumny jako posiadające różne typy miar. Na przykład pierwsza kolumna w `float<meter>`naszym przykładzie `float<second>`ma typ , a druga ma . Jednak wymazana reprezentacja może pozostać dość prosta.

Poniższy kod przedstawia rdzeń implementacji.

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

Należy zwrócić uwagę na następujące punkty dotyczące implementacji:

- Przeciążone konstruktory umożliwiają odczytanie oryginalnego pliku lub pliku, który ma identyczny schemat. Ten wzorzec jest typowy podczas pisania dostawcy typów dla lokalnych lub zdalnych źródeł danych, a ten wzorzec umożliwia użycie pliku lokalnego jako szablonu dla danych zdalnych.

- Można użyć [TypeProviderConfig](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44) wartość, która jest przekazywana do konstruktora dostawcy typu, aby rozpoznać względne nazwy plików.

- Za pomocą `AddDefinitionLocation` tej metody można zdefiniować lokalizację podanych właściwości. W związku z `Go To Definition` tym jeśli używasz na dostarczonej właściwości, plik CSV otworzy się w programie Visual Studio.

- Można użyć `ProvidedMeasureBuilder` tego typu, aby wyszukać jednostki `float<_>` SI i wygenerować odpowiednie typy.

### <a name="key-lessons"></a>Kluczowe lekcje

W tej sekcji wyjaśniono, jak utworzyć dostawcę typów dla lokalnego źródła danych z prostym schematem, który znajduje się w samym źródle danych.

## <a name="going-further"></a>Idąc dalej

Poniższe sekcje zawierają sugestie dotyczące dalszych badań.

### <a name="a-look-at-the-compiled-code-for-erased-types"></a>Spojrzenie na skompilowany kod dla usuniętych typów

Aby dać ci pewne pojęcie o tym, jak użycie dostawcy typu odpowiada emitowanemu kodowi, `HelloWorldTypeProvider` przyjrzyj się następującej funkcji przy użyciu używanej wcześniej w tym temacie.

```fsharp
let function1 () =
    let obj1 = Samples.HelloWorldTypeProvider.Type1("some data")
    obj1.InstanceProperty
```

Oto obraz wynikowego kodu dekompilowanego przy użyciu pliku ildasm.exe:

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

Jak pokazano w przykładzie, wszystkie `Type1` wzmianki o typie i `InstanceProperty` właściwości zostały usunięte, pozostawiając tylko operacje na typy środowiska wykonawczego zaangażowanych.

### <a name="design-and-naming-conventions-for-type-providers"></a>Konwencje projektowania i nazewnictwa dla dostawców typów

Należy przestrzegać następujących konwencji podczas tworzenia dostawców typów.

**Dostawcy protokołów łączności** Ogólnie rzecz biorąc, nazwy większości bibliotek DLL dostawców dla protokołów łączności danych i usług, `TypeProvider` takich `TypeProviders`jak OData lub połączenia SQL, powinny kończyć się w programie lub . Na przykład należy użyć nazwy biblioteki DLL, która przypomina następujący ciąg:

`Fabrikam.Management.BasicTypeProviders.dll`

Upewnij się, że podane typy są członkami odpowiedniego obszaru nazw i wskaż zaimplementowany protokół łączności:

```fsharp
  Fabrikam.Management.BasicTypeProviders.WmiConnection<…>
  Fabrikam.Management.BasicTypeProviders.DataProtocolConnection<…>
```

**Dostawcy narzędzi do ogólnego kodowania**.  W przypadku dostawcy typu narzędzia, takiego jak dla wyrażeń regularnych, dostawca typów może być częścią biblioteki podstawowej, jak pokazano w poniższym przykładzie:

```fsharp
#r "Fabrikam.Core.Text.Utilities.dll"
```

W takim przypadku podany typ pojawi się w odpowiednim punkcie zgodnie z normalnymi konwencjami projektowania .NET:

```fsharp
  open Fabrikam.Core.Text.RegexTyped

  let regex = new RegexTyped<"a+b+a+b+">()
```

**Źródła danych Singleton**. Niektórzy dostawcy typów łączą się z jednym dedykowanym źródłem danych i dostarczają tylko dane. W takim przypadku należy `TypeProvider` upuścić sufiks i użyć normalnych konwencji dla nazewnictwa .NET:

```fsharp
#r "Fabrikam.Data.Freebase.dll"

let data = Fabrikam.Data.Freebase.Astronomy.Asteroids
```

Aby uzyskać więcej `GetConnection` informacji, zobacz konwencję projektowania, która jest opisana w dalszej części tego tematu.

### <a name="design-patterns-for-type-providers"></a>Wzorce projektowe dla dostawców typów

W poniższych sekcjach opisano wzorce projektu, których można używać podczas tworzenia dostawców typów.

#### <a name="the-getconnection-design-pattern"></a>Wzór projektu GetConnection

Większość dostawców typów powinny być `GetConnection` zapisywane do korzystania z wzorca, który jest używany przez dostawców typów w FSharp.Data.TypeProviders.dll, jak pokazano w poniższym przykładzie:

```fsharp
#r "Fabrikam.Data.WebDataStore.dll"

type Service = Fabrikam.Data.WebDataStore<…static connection parameters…>

let connection = Service.GetConnection(…dynamic connection parameters…)

let data = connection.Astronomy.Asteroids
```

#### <a name="type-providers-backed-by-remote-data-and-services"></a>Dostawcy typów wspierani przez zdalne dane i usługi

Przed utworzeniem dostawcy typu, który jest wspierany przez zdalne dane i usługi, należy wziąć pod uwagę szereg problemów, które są związane z programowaniem połączonym. Kwestie te obejmują następujące zagadnienia:

- Mapowanie schematu

- żywotność i unieważnienie w obecności zmiany schematu

- buforowanie schematu

- asynchroniczne implementacje operacji dostępu do danych

- obsługa zapytań, w tym zapytań LINQ

- poświadczenia i uwierzytelnianie

W tym temacie nie należy dalej badać tych problemów.

### <a name="additional-authoring-techniques"></a>Dodatkowe techniki tworzenia

Podczas pisania własnych dostawców typów, można użyć następujących dodatkowych technik.

### <a name="creating-types-and-members-on-demand"></a>Tworzenie typów i członków na żądanie

Interfejs API ProvidedType ma opóźnione wersje AddMember.

```fsharp
  type ProvidedType =
      member AddMemberDelayed  : (unit -> MemberInfo)      -> unit
      member AddMembersDelayed : (unit -> MemberInfo list) -> unit
```

Te wersje są używane do tworzenia przestrzeni na żądanie typów.

### <a name="providing-array-types-and-generic-type-instantiations"></a>Dostarczanie typów macierzy i ogólnych wystąpienia typów

Należy utworzyć pod warunkiem członków (których podpisy obejmują typy tablic, typy byref `MakePointerType`i `MakeGenericType` wystąpienia typów <xref:System.Type>ogólnych) przy użyciu normalnych `ProvidedTypeDefinitions` `MakeArrayType`, i na każdym wystąpieniu , w tym .

> [!NOTE]
> W niektórych przypadkach może być trzeba `ProvidedTypeBuilder.MakeGenericType`użyć pomocnika w pliku .  Aby uzyskać więcej informacji, zapoznaj [się z dokumentacją SDK dostawcy typów.](https://github.com/fsprojects/FSharp.TypeProviders.SDK/blob/master/README.md#explicit-construction-of-code-makegenerictype-makegenericmethod-and-uncheckedquotations)

### <a name="providing-unit-of-measure-annotations"></a>Dostarczanie adnotacji jednostki miary

Interfejs API ProvidedTypes zapewnia pomocników do dostarczania adnotacji miar. Na przykład, aby `float<kg>`podać typ, użyj następującego kodu:

```fsharp
  let measures = ProvidedMeasureBuilder.Default
  let kg = measures.SI "kilogram"
  let m = measures.SI "meter"
  let float_kg = measures.AnnotateType(typeof<float>,[kg])
```

  Aby podać `Nullable<decimal<kg/m^2>>`typ, użyj następującego kodu:

```fsharp
  let kgpm2 = measures.Ratio(kg, measures.Square m)
  let dkgpm2 = measures.AnnotateType(typeof<decimal>,[kgpm2])
  let nullableDecimal_kgpm2 = typedefof<System.Nullable<_>>.MakeGenericType [|dkgpm2 |]
```

### <a name="accessing-project-local-or-script-local-resources"></a>Uzyskiwanie dostępu do zasobów lokalnych lub lokalnych w programie Project

Każde wystąpienie dostawcy typu może `TypeProviderConfig` mieć wartość podczas budowy. Ta wartość zawiera "folder rozpoznawania" dla dostawcy (czyli folderu projektu kompilacji lub katalogu zawierającego skrypt), listę zestawów, do których istnieją odwołania, i inne informacje.

### <a name="invalidation"></a>Unieważnienie

Dostawcy mogą zgłaszać sygnały unieważnienia, aby powiadomić usługę języka F#, że założenia schematu mogły ulec zmianie. W przypadku wystąpienia unieważnienia sprawdzanie typu jest ponownie, jeśli dostawca jest obsługiwany w programie Visual Studio. Ten sygnał zostanie zignorowany, gdy dostawca jest obsługiwany w języku F# Interactive lub przez kompilator F# (fsc.exe).

### <a name="caching-schema-information"></a>Informacje o schemacie buforowania

Dostawcy muszą często buforować dostęp do informacji o schemacie. Buforowane dane powinny być przechowywane przy użyciu nazwy pliku, który jest podany jako parametr statyczny lub jako dane użytkownika. Przykładem buforowania schematu `LocalSchemaFile` jest parametr w dostawcach `FSharp.Data.TypeProviders` typów w zestawie. W implementacji tych dostawców ten parametr statyczny nakazuje dostawcy typów używać informacji o schemacie w określonym pliku lokalnym zamiast uzyskiwać dostęp do źródła danych za pośrednictwem sieci. Aby użyć buforowanych informacji o schemacie, `ForceUpdate` należy `false`również ustawić parametr statyczny na . Można użyć podobnej techniki, aby włączyć dostęp do danych w trybie online i offline.

### <a name="backing-assembly"></a>Montaż podkładowy

Podczas kompilowania `.dll` `.exe` pliku lub pliku, kopii zapasowej pliku dll dla wygenerowanych typów jest statycznie połączone z wynikowego zestawu. To łącze jest tworzone przez skopiowanie definicji typu języka pośredniego (IL) i wszelkich zarządzanych zasobów z zestawu zapasowego do zestawu końcowego. Korzystając z języka F# Interactive, zapasowy plik dll nie jest kopiowany i zamiast tego jest ładowany bezpośrednio do procesu F# Interactive.

### <a name="exceptions-and-diagnostics-from-type-providers"></a>Wyjątki i diagnostyka od dostawców typów

Wszystkie zastosowania wszystkich elementów członkowskich z podanych typów mogą zgłaszać wyjątki. We wszystkich przypadkach, jeśli dostawca typu zgłasza wyjątek, kompilator hosta przypisuje ten błąd dostawcy określonego typu.

- Wyjątki dostawcy typu nigdy nie powinny powodować błędów kompilatora wewnętrznego.

- Dostawcy typów nie mogą zgłaszać ostrzeżeń.

- Gdy dostawca typu jest hostowany w kompilatorze Języka F#, środowisku programistycznym F# lub F# Interactive, wszystkie wyjątki od tego dostawcy są przechwytywane. Message Właściwość jest zawsze tekst błędu i nie ma śledzenia stosu. Jeśli zamierzasz zgłosić wyjątek, możesz zgłosić następujące `System.NotSupportedException` `System.IO.IOException`przykłady: , , `System.Exception`.

#### <a name="providing-generated-types"></a>Dostarczanie wygenerowanych typów

Do tej pory w tym dokumencie wyjaśniono, jak zapewnić usunięte typy. Można również użyć mechanizmu dostawcy typu w języku F#, aby zapewnić wygenerowane typy, które są dodawane jako rzeczywiste definicje typu .NET do programu użytkowników. Należy odwołać się do wygenerowanych typów dostarczonych przy użyciu definicji typu.

```fsharp
open Microsoft.FSharp.TypeProviders

type Service = ODataService<"http://services.odata.org/Northwind/Northwind.svc/">
```

Kod pomocnika ProvidedTypes-0.2, który jest częścią wersji F# 3.0 ma ograniczoną obsługę dostarczania wygenerowanych typów. Następujące instrukcje muszą być prawdziwe dla wygenerowanej definicji typu:

- `isErased`musi być `false`ustawiona na .

- Wygenerowany typ musi zostać dodany `ProvidedAssembly()`do nowo skonstruowanego , który reprezentuje kontener dla wygenerowanych fragmentów kodu.

- Dostawca musi mieć zestaw, który ma rzeczywisty zapas pliku .NET .dll z pasującym plikiem dll na dysku.

## <a name="rules-and-limitations"></a>Zasady i ograniczenia

Podczas pisania dostawców typów należy pamiętać o następujących regułach i ograniczeniach.

### <a name="provided-types-must-be-reachable"></a>Pod warunkiem, że typy muszą być osiągalne

Wszystkie podane typy powinny być dostępne z typów niezagnieżdżonych. Typy niezagnieżdżone są podane `TypeProviderForNamespaces` w wywołaniu `AddNamespace`do konstruktora lub wywołaniu . Na przykład jeśli dostawca udostępnia `StaticClass.P : T`typ, należy upewnić się, że T jest typem niezagnieżdżonego lub zagnieżdżone w jednym.

Na przykład niektórzy dostawcy mają klasę `DataTypes` statyczną, `T1, T2, T3, ...` taką jak te typy. W przeciwnym razie błąd mówi, że znaleziono odwołanie do typu T w zestawie A, ale nie można odnaleźć typu w tym zestawie. Jeśli ten błąd zostanie wyświetlony, sprawdź, czy wszystkie podtypy można uzyskać z typów dostawców. Uwaga: `T1, T2, T3...` Te typy są określane jako typy *w locie.* Pamiętaj, aby umieścić je w dostępnej przestrzeni nazw lub typu nadrzędnego.

### <a name="limitations-of-the-type-provider-mechanism"></a>Ograniczenia mechanizmu dostawcy typu

Mechanizm dostawcy typu w języku F# ma następujące ograniczenia:

- Podstawowa infrastruktura dla dostawców typów w języku F# nie obsługuje pod warunkiem typy ogólne lub pod warunkiem metod ogólnych.

- Mechanizm nie obsługuje typów zagnieżdżonych z parametrami statycznymi.

## <a name="development-tips"></a>Porady dotyczące projektowania

Następujące wskazówki mogą okazać się pomocne podczas procesu tworzenia:

### <a name="run-two-instances-of-visual-studio"></a>Uruchamianie dwóch wystąpień programu Visual Studio

Można opracować dostawcę typu w jednym wystąpieniu i przetestować dostawcę w innym, ponieważ ide testowy podejmie blokadę pliku .dll, która uniemożliwia przebudowę dostawcy typu. W związku z tym należy zamknąć drugie wystąpienie programu Visual Studio, gdy dostawca jest zbudowany w pierwszej instancji, a następnie należy ponownie otworzyć drugie wystąpienie po zbudowaniu dostawcy.

### <a name="debug-type-providers-by-using-invocations-of-fscexe"></a>Dostawców typów debugowania przy użyciu wywołań fsc.exe

Dostawców typów można wywoływać przy użyciu następujących narzędzi:

- fsc.exe (kompilator wiersza polecenia F#)

- fsi.exe (Kompilator F# Interactive)

- devenv.exe (Visual Studio)

Często można debugować dostawców typów najłatwiej za pomocą fsc.exe na pliku skryptu testowego (na przykład script.fsx). Debugera można uruchomić z wiersza polecenia.

```console
devenv /debugexe fsc.exe script.fsx
```

  Można użyć rejestrowania wydruku do stdout.

## <a name="see-also"></a>Zobacz też

- [Dostawcy typów](index.md)
- [SDK dostawcy typu](https://github.com/fsprojects/FSharp.TypeProviders.SDK)
