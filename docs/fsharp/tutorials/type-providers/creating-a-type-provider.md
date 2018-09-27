---
title: 'Samouczek: Tworzenie dostawcy typów (F #)'
description: 'Dowiedz się, jak utworzyć własne dostawcy typów F # w F # 3.0, sprawdzając kilku dostawców typu prostego, w celu zilustrowania podstawowych koncepcji.'
ms.date: 05/16/2016
ms.openlocfilehash: 3c998377b2c3a408d536ef416f3799bf7f04b6bd
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2018
ms.locfileid: "47397962"
---
# <a name="tutorial-create-a-type-provider"></a>Samouczek: Tworzenie dostawcy typów

Mechanizm dostawcy typu F # jest znaczna część jej obsługę programowania zaawansowanych informacji. W tym samouczku opisano sposób tworzenia własnych dostawców typów, prowadzące przez proces tworzenia kilku dostawców typu prostego, w celu zilustrowania podstawowych koncepcji. Aby uzyskać więcej informacji na temat mechanizmu dostawcy typu F #, zobacz [dostawców typów](index.md).

Ekosystem F # zawiera szeroką gamę dostawców typów dla często używanych internetowych i firmowych usług danych. Na przykład:

- [FSharp.Data](https://fsharp.github.io/FSharp.Data/) obejmuje dostawców typów dla formatu JSON, XML, CSV i HTML dokumentu formatów.

- [SQLProvider](https://fsprojects.github.io/SQLProvider/) udostępnia silnie typizowane baz danych SQL za pomocą mapowanie obiektów i LINQ języka F # zapytań dotyczących tych źródeł danych.

- [FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) zestaw dostawców typów dla kompilacji zaewidencjonowanego osadzania T-SQL w języku F #.

- [FSharp.Data.TypeProviders](https://fsprojects.github.io/FSharp.Data.TypeProviders/) to starszy zestaw dostawców typów do użycia tylko w programowaniu .NET Framework do uzyskiwania dostępu do usługi danych SQL, platformy Entity Framework, OData i WSDL.

W przypadku, gdy to konieczne, można tworzyć niestandardowych dostawców typów, lub możesz odwoływać się do dostawców typów, utworzone przez innych użytkowników. Na przykład organizacja może mieć usługi danych, która zapewnia duży i rosnący liczbę nazwanych zestawów danych, każdy z swój własny stabilny schemat danych. Możesz utworzyć dostawcę typów, który odczytuje te schematy i przedstawia informacje o bieżącym zestawów danych do programisty należy w silnie typizowany sposób.

## <a name="before-you-start"></a>Przed rozpoczęciem

Mechanizm dostawcy typu jest przeznaczony głównie do wprowadza stabilnych danych i miejsca do magazynowania usługi informacji do programowania środowiska F #.

Ten mechanizm nie jest przeznaczona dla wprowadzanie informacji miejsca do magazynowania, którego schemat zmienia się podczas wykonywania programu, w sposób, które mają zastosowanie do logiki programu. Również mechanizm nie jest przeznaczona dla meta-programowania wewnątrz języka, mimo że tej domeny zawiera niektóre prawidłowego użycia. Ten mechanizm należy używać tylko wtedy, gdy jest to konieczne, i gdzie tworzenie dostawcy typów daje bardzo duża wartość.

Należy unikać pisania dostawcy typów, których schemat jest niedostępna. Podobnie, należy unikać pisania dostawcę typów, w przypadku, gdy zwykłej (lub nawet istniejącego) biblioteki .NET będą wystarczające.

Przed rozpoczęciem może odpowiedzieć na następujące pytania:

- Czy masz schematu dla źródła informacji? Jeśli tak, co to jest mapowanie języka F # i .NET typu systemu?

- Można użyć istniejącego interfejsu API (o typach określanych dynamicznie) jako punktu wyjścia dla wdrożenia?

- Ty i Twoja organizacja ma wystarczającą ilość użycia dostawcy typów, które umożliwiają zapisywanie zwiększonej? Czy normalne biblioteki .NET potrzeb?

- Ile zmieni się schematu

- Zostanie ona zmieniona podczas kodowania?

- Ją zmieni się między sesjami kodowania?

- Zostanie ona zmieniona podczas wykonywania programu?

Dostawcy typów są najlepiej sprawdza się w sytuacjach, gdy schemat jest stabilna, w czasie wykonywania, jak i w okresie istnienia skompilowanego kodu.

## <a name="a-simple-type-provider"></a>Dostawca typu prostego

Te przykładowe dane stanowią Samples.HelloWorldTypeProvider podobne do próbek w `examples` katalogu [SDK dostawcy typu F #](https://github.com/fsprojects/FSharp.TypeProviders.SDK/). Dostawca udostępnia "przestrzenią typu", która zawiera 100 typów wymazane, co ilustruje poniższy kod, używając składni Sygnatura F # i pomijanie szczegóły wszystkie z wyjątkiem `Type1`. Aby uzyskać więcej informacji na temat typów wymazane, zobacz [szczegółowe informacje o wymazane podane typy](#details-about-erased-provided-types) w dalszej części tego tematu.

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

Należy pamiętać, że zestaw typów i członków, pod warunkiem jest znany statycznie. W tym przykładzie nie korzystać z możliwości dostawców typów, które są zależne od schematu. Implementacja dostawcy typów jest opisany w następującym kodzie i szczegółowe informacje znajdują się w kolejnych sekcjach tego tematu.

>[!WARNING]
Może to być różnice między tym kodem i przykładów online.

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

Użyj tego dostawcy, otwórz osobnego wystąpienia programu Visual Studio, utworzyć skrypt F #, a następnie dodaj odwołanie do dostawcy ze skryptu przy użyciu #r, co ilustruje poniższy kod:

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

Następnie poszukaj typów pod `Samples.HelloWorldTypeProvider` przestrzeni nazw, który wygenerował dostawcy typów.

Przed ponownym skompilowaniem dostawcy, upewnij się, zamknęli wszystkie wystąpienia programu Visual Studio i F # Interactive, które korzystają z biblioteki DLL dostawcy. W przeciwnym razie wystąpi błąd kompilacji ponieważ dane wyjściowe biblioteki DLL będzie zablokowany.

Aby debugować ten dostawca za pomocą instrukcji drukowania, wprowadź skrypt, który opisuje problem z dostawcą, a następnie użyj poniższego kodu:

```fsharp
fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

Aby debugować tego dostawcę przy użyciu programu Visual Studio, otwórz wiersz polecenia programu Visual Studio przy użyciu poświadczeń administracyjnych i uruchom następujące polecenie:

```fsharp
devenv.exe /debugexe fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

Jako alternatywę, Otwórz program Visual Studio, otwórz menu debugowanie, wybierz polecenie `Debug/Attach to process…`i Dołącz do innego `devenv` proces, w którym edycji skrypt. Za pomocą tej metody, można łatwiej wskazać konkretnego węzła logicznego w dostawcy typów interaktywnie wpisując wyrażenia do drugiego wystąpienia (z pełną obsługą technologii IntelliSense i inne funkcje).

Można wyłączyć opcję tylko mój kod, debugowanie, aby lepiej identyfikację błędów występujących w wygenerowanym kodzie. Aby dowiedzieć się, jak włączyć lub wyłączyć tę funkcję, zobacz [nawigowanie po kodzie za pomocą debugera za](/visualstudio/debugger/navigating-through-code-with-the-debugger). Ponadto można również ustawić wyjątku pierwszej szansy przechwytywanie, otwierając `Debug` menu, a następnie wybierając `Exceptions` lub wybierając klawisze Ctrl + Alt + E, aby otworzyć `Exceptions` okno dialogowe. W tym oknie dialogowym w obszarze `Common Language Runtime Exceptions`, wybierz opcję `Thrown` pole wyboru.

### <a name="implementation-of-the-type-provider"></a>Implementacja dostawcy typów

Ta sekcja przeprowadzi Cię przez główne sekcji implementacja dostawcy typu. Najpierw należy zdefiniować typ dostawcy niestandardowego typu, samego programu:

```fsharp
[<TypeProvider>]
type SampleTypeProvider(config: TypeProviderConfig) as this =
```

Tego typu muszą być publiczne i należy go oznaczyć [TypeProvider](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947) atrybutu, aby kompilator, rozpoznawał dostawcę typów, gdy oddzielny projekt języka F # odwołuje się do zestawu, który zawiera typu. *Config* parametr jest opcjonalny i, jeśli jest obecny, zawiera informacje o konfiguracji kontekstowych wystąpienia dostawcy typu, który tworzy kompilatora języka F #.

Następnie możesz wdrożyć [itypeprovider —](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f) interfejsu. W tym przypadku używasz `TypeProviderForNamespaces` typ z `ProvidedTypes` API jako typu podstawowego. Tego typu pomocnika zapewniają skończoną zbiór eagerly, pod warunkiem przestrzeni nazw, z których każdy bezpośrednio zawiera skończoną liczbę stałej, eagerly dostarczone typy. W tym kontekście, dostawca *eagerly* generuje typy, nawet jeśli nie są potrzebne lub używane.

```fsharp
inherit TypeProviderForNamespaces(config)
```

Następnie zdefiniuj lokalnego wartości prywatne, które określają przestrzeń nazw dla podane typy i Znajdź samego montażu dostawcy typu. Ten zestaw jest później używany jako typ logiczny nadrzędnego wymazane typów, które są dostarczane.

```fsharp
let namespaceName = "Samples.HelloWorldTypeProvider"
let thisAssembly = Assembly.GetExecutingAssembly()
```

Następnie należy utworzyć funkcję, aby zapewnić każdego typu Type1... Type100. Ta funkcja jest omówione bardziej szczegółowo w dalszej części tego tematu.

```fsharp
let makeOneProvidedType (n:int) = …
```

Kolejny krok to Generowanie 100 podane typy:

```fsharp
let types = [ for i in 1 .. 100 -> makeOneProvidedType i ]
```

Następnie dodaj typy podanej przestrzeni nazw:

```fsharp
do this.AddNamespace(namespaceName, types)
```

Na koniec należy dodać atrybut zestawu, który wskazuje, tworzysz dostawcę wpisz biblioteki DLL:

```fsharp
[<assembly:TypeProviderAssembly>] 
do()
```

### <a name="providing-one-type-and-its-members"></a>Zapewnienie jednego typu i jej elementów członkowskich

`makeOneProvidedType` Funkcja wykonuje rzeczywistą pracę, zapewniając jeden z typów.

```fsharp
let makeOneProvidedType (n:int) = 
…
```

W tym kroku opisano stosowania tej funkcji. Najpierw utwórz podany typ (na przykład Type1, gdy n = 1 lub Type57, gdy jest to n = 57).

```fsharp
// This is the provided type. It is an erased provided type and, in compiled code, 
// will appear as type 'obj'.
let t = ProvidedTypeDefinition(thisAssembly, namespaceName,
                               "Type" + string n,
                               baseType = Some typeof<obj>)
```

Należy zauważyć następujące kwestie:

- To pod warunkiem, że typ są usuwane.  Ponieważ wskazywać, że typ podstawowy jest `obj`, wystąpienia będą wyświetlane jako wartości typu [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) w skompilowany kod.

- Po określeniu typu niezagnieżdżonego, należy określić zestawu i przestrzeni nazw. W przypadku typów wymazane zestawu powinna być samego montażu dostawcy typu.

Następnie dodaj dokumentacji XML do typu. Ta dokumentacja została opóźniona, oznacza to, obliczane na żądanie, jeśli ich potrzebuje kompilatora hosta.

```fsharp
t.AddXmlDocDelayed (fun () -> sprintf "This provided type %s" ("Type" + string n))
```

Następnie dodaj podanej właściwości statycznej do typu:

```fsharp
let staticProp = ProvidedProperty(propertyName = "StaticProperty", 
                                  propertyType = typeof<string>, 
                                  isStatic = true,
                                  getterCode = (fun args -> <@@ "Hello!" @@>))
```

Wprowadzenie tej właściwości będzie zawsze przyjmowało ciąg "Hello!". `GetterCode` Dla właściwości używa F # oferty, który reprezentuje kod generowany przez kompilator hosta w celu uzyskania właściwości. Aby uzyskać więcej informacji na temat ofert zobacz [cytaty kodu (F #)](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155).

Dodaj dokumentacji XML do właściwości.

```fsharp
staticProp.AddXmlDocDelayed(fun () -> "This is a static property")
```

Podane właściwości teraz zostać dołączony do podanego typu. Jeden i tylko jeden typ, należy dołączyć podanego elementu członkowskiego. W przeciwnym razie należy nigdy nie będzie dostępny.

```fsharp
t.AddMember staticProp
```

Teraz utworzyć podanej Konstruktor, który nie przyjmuje żadnych parametrów.

```fsharp
let ctor = ProvidedConstructor(parameters = [ ], 
                               invokeCode = (fun args -> <@@ "The object data" :> obj @@>))
```

`InvokeCode` Dla konstruktora zwraca F # oferty, który reprezentuje kod, który kompilator hosta generuje podczas wywołania konstruktora. Na przykład można użyć następującego konstruktora:

```fsharp
new Type10()
```

Wystąpienie podanego typu zostanie utworzony przy użyciu danych bazowych "Dane obiektu". Cudzysłowie kod zawiera konwersję [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) ponieważ ten typ jest skasowanie to podany typ (jak określić, kiedy zadeklarowana podany typ).

Dodaj dokumentacji XML do konstruktora i Dodaj Konstruktor podany do podany typ:

```fsharp
ctor.AddXmlDocDelayed(fun () -> "This is a constructor")

t.AddMember ctor
```

Utwórz drugi Konstruktor podana, który przyjmuje jeden parametr:

```fsharp
let ctor2 = 
ProvidedConstructor(parameters = [ ProvidedParameter("data",typeof<string>) ], 
                    invokeCode = (fun args -> <@@ (%%(args.[0]) : string) :> obj @@>))
```

`InvokeCode` Dla konstruktora ponownie zwraca F # oferty, który reprezentuje kod, który dla wywołania do metody generowane przez kompilator hosta. Na przykład można użyć następującego konstruktora:

```fsharp
new Type10("ten")
```

Wystąpienie podanego typu jest tworzony przy użyciu danych bazowych "10". Być może już zauważono, że `InvokeCode` :: gettotalsize() zwróciło oferty. Dane wejściowe do tej funkcji znajduje się lista wyrażeń, jeden na parametr konstruktora. W tym przypadku wyrażenia, która reprezentuje wartość jeden parametr jest dostępny w `args.[0]`. Kod na wywołanie konstruktora przekształca wynik dane wymazane typ wartości zwróconej `obj`. Po dodaniu podana drugi Konstruktor do typu, utworzysz właściwość udostępnionego wystąpienia:

```fsharp
let instanceProp = 
    ProvidedProperty(propertyName = "InstanceProperty", 
                     propertyType = typeof<int>, 
                     getterCode= (fun args -> 
                        <@@ ((%%(args.[0]) : obj) :?> string).Length @@>))
instanceProp.AddXmlDocDelayed(fun () -> "This is an instance property")
t.AddMember instanceProp
```

Wprowadzenie tej właściwości zostanie zwrócona długość ciągu, który jest obiektem reprezentacji. `GetterCode` Właściwość zwraca oferty F #, który określa kod, który kompilator hosta generuje pobrać właściwości. Podobnie jak `InvokeCode`, `GetterCode` :: gettotalsize() zwróciło oferty. Kompilator hosta wywołuje tę funkcję z listy argumentów. W tym przypadku argumenty zawierają tylko pojedyncze wyrażenie, który reprezentuje wystąpienie, na którym jest wywoływana metoda pobierająca, możesz uzyskać dostęp za pomocą `args.[0]`. Implementacja `GetterCode` następnie splices do oferty wynik wymazane wpisz `obj`, i używane jest rzutowanie do zaspokojenia kompilatora mechanizmu sprawdzania typów, że obiekt jest ciągiem. Kolejnym etapem `makeOneProvidedType` zawiera metodę instancji za pomocą jednego parametru.

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

Na koniec Utwórz typu zagnieżdżonego, która zawiera 100 zagnieżdżonych właściwości. To tworzenie zagnieżdżonych typu i jego właściwości zostanie opóźnione, to znaczy, obliczona na żądanie.

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

### <a name="details-about-erased-provided-types"></a>Szczegółowe informacje o wymazane podane typy

W przykładzie, w tej sekcji przedstawiono jedynie *wymazane podane typy*, które są szczególnie przydatne w następujących sytuacjach:

- Kiedy piszesz dostawcę dla przestrzeń informacji, która zawiera tylko danych i metod.

- Kiedy piszesz dostawcy, gdzie semantyka dokładne typ środowiska uruchomieniowego nie są istotne dla praktyczne wykorzystanie miejsca informacji.

- Kiedy piszesz dostawcę dla przestrzeń informacji, więc dużej i wzajemnie połączonych, że nie jest technicznie możliwe, można wygenerować rzeczywistych typów .NET do przestrzeń informacji.

W tym przykładzie każdy z podanych typu są usuwane na typ `obj`, a wszystkie przypadki użycia typu pojawi się jako typ `obj` w skompilowany kod. W rzeczywistości obiektów w tych przykładach są ciągami, ale typ będą wyświetlane jako `System.Object` na platformie .NET skompilowany kod. Ponieważ wszystkie przypadki użycia wymazywania typie, będzie można użyć jawne pakowanie, Rozpakowywanie i rzutowania można złamać usuwane typów. W tym przypadku wyjątek rzutowania, który nie jest prawidłową może spowodować, jeśli obiekt jest używany. Dostawca środowiska uruchomieniowego, można zdefiniować swój własny typ reprezentujący prywatnych w celu zabezpieczenia przed reprezentacje false. Nie można zdefiniować typy wymazane w języku F # sam. Tylko podane typy mogą zostać wymazane. Musisz rozumieć konsekwencje, zarówno praktyczne, i semantyczne, albo korzystania z wymazanej typy dla dostawcy typu lub dostawcę, który zawiera usunięte typów. Typem wymazane nie ma rzeczywistych .NET typu. W związku z tym nie można wykonać dokładne odbicie nad typem i może złamać wymazane typy rzutowania środowiska uruchomieniowego i innych technik, które opierają się na semantyce typu dokładnego czasu wykonywania za pomocą. Subversion typów wymazane często skutkuje wyjątki rzutowanie typu w czasie wykonywania.

### <a name="choosing-representations-for-erased-provided-types"></a>Wybieranie oświadczenia dla wymazane dostarczone typy

Do niektórych zastosowań wymazane podane typy nie jest wymagana. Na przykład wymazane dostarczane typ może zawierać tylko właściwości statycznych i elementów członkowskich i konstruktorów, a żadnych metod ani właściwości zwróci wystąpienia tego typu. Możesz uzyskiwać dostęp wystąpień wymazane podany typ, należy wziąć pod uwagę następujące kwestie:

**Co to jest wymazywanie podany typ?**

- Wymazywanie podany typ jest, jak typ pojawia się w skompilowanego kodu .NET.

- Wymazywanie typu podanej klasy wymazane jest zawsze pierwszej-wymazane typem podstawowym w łańcuchu dziedziczenia tego typu.

- Wymazywanie typu interfejsem dostarczanym wymazane jest zawsze `System.Object`.

**Co to są liczbami w postaci podany typ?**

- Zestaw obiektów możliwych do wymazane, podany typ są nazywane oświadczeń. W przykładzie w tym dokumencie reprezentacje wszystkich wymazane podane typy `Type1..Type100` są zawsze obiektów w postaci ciągów.

Reprezentacje wszystkich podany typ musi być zgodny z wymazywania podanego typu. (W przeciwnym razie kompilator F # błąd uniemożliwiający do użycia dostawcy typów lub zweryfikowanie kodu platformy .NET, który nie jest prawidłowy, zostanie wygenerowany. Dostawcy typów nie jest prawidłowy, jeśli zwróci ona kod, który zawiera reprezentację, który nie jest prawidłowy).

Możesz wybrać reprezentację podanych obiektów przy użyciu jednej z poniższych metod, które są bardzo popularne:

- Jeśli po prostu silnie typizowaną otokę za pośrednictwem istniejącego typu .NET, często warto wymazać do tego typu, należy użyć wystąpienia tego typu jako oświadczenia i / lub z danym typem. To podejście jest odpowiednie, jeśli większość istniejących metod tego typu nadal mieć sens, gdy za pomocą silnie typizowanej wersji.

- Jeśli chcesz utworzyć interfejs API, który różni się znacznie z dowolnym istniejącym interfejsem API platformy .NET, dobrym pomysłem do tworzenia typów środowiska wykonawczego, które będą wymazywania typie i reprezentacji dla podanego typu.

W przykładzie w tym dokumencie używa ciągów jako oświadczenia podanych obiektów. Często może być odpowiednie na potrzeby innych obiektów reprezentacji. Na przykład może użyć słownika jako zbiór właściwości:

```fsharp
ProvidedConstructor(parameters = [], 
    invokeCode= (fun args -> <@@ (new Dictionary<string,obj>()) :> obj @@>))
```

Jako alternatywę może zdefiniować typ u Twojego dostawcy typu, który będzie używany w czasie wykonywania w celu utworzenia reprezentacji, wraz z co najmniej jednej operacji środowiska uruchomieniowego:

```fsharp
type DataObject() =
    let data = Dictionary<string,obj>()
    member x.RuntimeOperation() = data.Count
```

Podane elementy członkowskie można następnie konstruować wystąpień tego typu obiektu:

```fsharp
ProvidedConstructor(parameters = [], 
    invokeCode= (fun args -> <@@ (new DataObject()) :> obj @@>))
```

W takim przypadku może (opcjonalnie) używasz tego typu jako wymazywania typie, określając tego typu jako `baseType` przy konstruowaniu `ProvidedTypeDefinition`:

```fsharp
ProvidedTypeDefinition(…, baseType = Some typeof<DataObject> )
…
ProvidedConstructor(…, InvokeCode = (fun args -> <@@ new DataObject() @@>), …)
```

### <a name="key-lessons"></a>Lekcje klucza

W poprzedniej sekcji objaśniono sposób tworzenia prostego wymazywanie dostawcę typów, który udostępnia szereg typów, właściwości i metody. W tej sekcji również wyjaśniono pojęcie wymazywania typu, w tym niektóre zalety i wady związanych z udostępnianiem typy wymazane z dostawcy typów i omówiono reprezentujących typy wymazane.

## <a name="a-type-provider-that-uses-static-parameters"></a>Dostawcy typów, który używa statycznych parametrów

Możliwość parametryzacja dostawców typów statycznych danych umożliwia wiele ciekawych scenariuszy, nawet w przypadkach, gdy dostawca nie potrzebuje dostępu do żadnych danych lokalnych lub zdalnych. W tej sekcji dowiesz się kilka podstawowych technik dla zestawiania takiego dostawcy.

### <a name="type-checked-regex-provider"></a>Typ zaznaczone dostawcy wyrażeń regularnych

Wyobraź sobie chcesz zaimplementować dostawcę typów dla wyrażeń regularnych, który otacza .NET <xref:System.Text.RegularExpressions.Regex> bibliotek interfejsu, który zapewnia następujące gwarancje w czasie kompilacji:

- Sprawdzanie, czy wyrażenie regularne jest prawidłowa.

- Materiały nazwane właściwości na dopasowania, które są oparte na wszystkie nazwy grup w wyrażeniu regularnym.

W tej sekcji dowiesz się, jak utworzyć za pomocą dostawców typów `RegexTyped` wpisz, że wzorzec wyrażenia regularnego parametryzuje dane umożliwia uzyskiwanie tych korzyści. Kompilator zgłosi błąd, jeśli podany wzorzec nie jest prawidłowa, a dostawca typów może wyodrębnić grupy od wzorca, tak, aby mogli je przy użyciu nazwanych właściwości dopasowań. Podczas projektowania dostawcy typów należy rozważyć, jak powinna wyglądać jego narażonych interfejsu API dla użytkowników końcowych i jak ten projekt przekształci się w kodzie .NET. Poniższy przykład pokazuje, jak używać interfejsu API na pobranie składników numer kierunkowy:

```fsharp
type T = RegexTyped< @"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)">
let reg = T()
let result = T.IsMatch("425-555-2345")
let r = reg.Match("425-555-2345").Group_AreaCode.Value //r equals "425"
```

Poniższy przykład pokazuje, jak dostawca typów przekształca te wywołania:

```fsharp
let reg = new Regex(@"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)")
let result = reg.IsMatch("425-123-2345")
let r = reg.Match("425-123-2345").Groups.["AreaCode"].Value //r equals "425"
```

Pamiętaj o następujących kwestiach:

- Standardowy typ wyrażenia regularnego reprezentuje sparametryzowane `RegexTyped` typu.

- `RegexTyped` Konstruktor powoduje wywołanie konstruktora wyrażeń regularnych, przekazywanie argumentu typu statycznego dla wzorca.

- Wyniki `Match` metody są reprezentowane przez standard <xref:System.Text.RegularExpressions.Match> typu.

- Każda grupa o nazwie wyników w podanej właściwości i uzyskiwania dostępu do właściwości powoduje użycie indeksatora w przypadku dopasowania `Groups` kolekcji.

Poniższy kod stanowi podstawę logiki do zaimplementowania takich dostawcy, a w tym przykładzie pomija dodanie wszystkich elementów członkowskich do podanego typu. Informacje dla każdego członka dodano zobacz odpowiednią sekcję w dalszej części tego tematu. Aby uzyskać pełny kod pobrać przykład z [F # 3.0 przykładowy pakiet](https://fsharp3sample.codeplex.com) w witrynie Codeplex.

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

- Dostawcy typów przyjmuje dwa parametry statyczne: `pattern`, który jest obowiązkowe, a `options`, które są opcjonalne (ponieważ podana jest wartość domyślna).

- Po argumenty statyczne są dostarczane, Utwórz wystąpienie wyrażenia regularnego. To wystąpienie spowoduje zgłoszenie wyjątku, jeśli wyrażenie regularne jest źle sformułowany, a ten błąd będzie zgłaszany dla użytkowników.

- W ramach `DefineStaticParameters` wywołanie zwrotne, zdefiniuj typ, który będzie zwracany po argumenty są dostarczane.

- Ten kod ustawia `HideObjectMethods` na wartość true, dzięki czemu środowisko IntelliSense pozostanie prostsze. Powoduje, że ten atrybut `Equals`, `GetHashCode`, `Finalize`, i `GetType` składowe, które mają zostać pominięte z listy technologii IntelliSense dla podanego obiektu.

- Możesz użyć `obj` jako typ bazowy metody, ale użyjemy `Regex` obiektu jako reprezentacja środowiska uruchomieniowego tego typu, jak pokazano w następnym przykładzie.

- Wywołanie `Regex` Konstruktor wyrzuca <xref:System.ArgumentException> kiedy wyrażenie regularne jest nieprawidłowy. Kompilator przechwytuje ten wyjątek i zgłasza komunikat o błędzie dla użytkownika, w czasie kompilacji lub w edytorze programu Visual Studio. Ten wyjątek umożliwia wyrażeń regularnych zostać uwierzytelnionym bez uruchamiania aplikacji.

Określone powyżej nie jest przydatne jeszcze, ponieważ nie zawiera żadnych istotnych metody lub właściwości. Najpierw dodaj statyczną `IsMatch` metody:

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

Powyższy kod definiuje metodę `IsMatch`, który przyjmuje ciąg jako dane wejściowe i zwraca `bool`. Tylko wymagana polega na użyciu `args` argumentu w ciągu `InvokeCode` definicji. W tym przykładzie `args` znajduje się lista ofert, która reprezentuje argumenty tej metody. Jeśli metoda jest metodą wystąpienia, pierwszy argument reprezentuje `this` argumentu. W przypadku statycznej metody argumenty są wszystkie tylko jawnych argumentów do metody. Należy pamiętać, że typ wartości oferowanej powinien pasuje do określonego typu zwracanego (w tym przypadku `bool`). Należy także zauważyć, że ten kod używa `AddXmlDoc` metody, aby upewnić się, że podana metoda ma również przydatna dokumentacji, które można podać za pomocą funkcji IntelliSense.

Następnie dodaj wystąpienie metody Match. Jednak ta metoda powinna zwrócić wartość podana `Match` wpisz, aby grupy jest możliwy w silnie typizowany sposób. Tak więc pierwszym zdeklarowaniu `Match` typu. Ponieważ ten typ jest zależny od wzorzec, który został dostarczony jako argument statyczne, ten typ musi być zagnieżdżony w ramach definicji typ sparametryzowany:

```fsharp
let matchTy = 
    ProvidedTypeDefinition(
        "MatchType", 
        baseType = Some baseTy, 
        hideObjectMethods = true)

ty.AddMember matchTy
```

Następnie dodasz jedną właściwość na typ dopasowania dla każdej grupy. W czasie wykonywania, dopasowanie jest reprezentowany jako <xref:System.Text.RegularExpressions.Match> wartości, więc należy użyć cudzysłowu, który definiuje właściwość <xref:System.Text.RegularExpressions.Match.Groups> indeksowana właściwość, aby uzyskać odpowiednie grupy.

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

Ponownie należy pamiętać, podana wartość właściwości dodajesz dokumentacji XML. Też pamiętać, że właściwość może zostać odczytany, jeśli `GetterCode` dostarczono funkcji i właściwości mogą być zapisywane, jeśli `SetterCode` funkcji zostanie podany, dzięki czemu wynikowy właściwość jest tylko do odczytu.

Teraz możesz utworzyć metodę wystąpienia, która zwraca wartość tego `Match` typu:

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

Ponieważ tworzysz metodę wystąpienia `args.[0]` reprezentuje `RegexTyped` wystąpienia, na którym jest wywoływana metoda, i `args.[1]` jest argument wejściowy.

Na koniec należy dostarczyć konstruktora, tak że można utworzyć jedno wystąpienie podanego typu.

```fsharp
let ctor = 
    ProvidedConstructor(
        parameters = [], 
        invokeCode = fun args -> <@@ Regex(pattern, options) :> obj @@>)

ctor.AddXmlDoc("Initializes a regular expression instance.")

ty.AddMember ctor
```

Konstruktor jedynie na partycje powoduje usunięcie do utworzenia standardowego wystąpienia wyrażenie regularne .NET, co jest spakowany ponownie do obiektu, ponieważ `obj` jest wymazywania podanego typu. Dzięki temu przykładowe zastosowanie interfejsu API, który określono wcześniej w temacie działa zgodnie z oczekiwaniami. Poniższy kod jest pełny i końcowe:

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

### <a name="key-lessons"></a>Lekcje klucza

W tej sekcji wyjaśniono, jak utworzyć dostawcę typów, który działa na jego parametry statyczne. Dostawca sprawdza, czy parametr static i udostępnia operacje na podstawie jej wartości.

## <a name="a-type-provider-that-is-backed-by-local-data"></a>Dostawcy typów, która jest wspierana przez dane lokalne

Często można dostawców typów, aby przedstawić interfejsów API opartych na nie tylko parametry statyczne, ale także informacje z systemów lokalnych lub zdalnych. W tej sekcji omówiono dostawców typów, które są oparte na danych lokalnych, takich jak pliki danych lokalnych.

### <a name="simple-csv-file-provider"></a>Dostawcy plików CSV prosty

Prostym przykładem należy wziąć pod uwagę dostawcy typów do uzyskiwania dostępu do danych naukowych, w formacie wartości rozdzielanych przecinkami (CSV). W tej sekcji założono, że pliki CSV zawiera wiersz nagłówka, następuje ruchomy punkt danych, tak jak pokazano w poniższej tabeli:

|Distance (licznik)|Czas (s)|
|----------------|-------------|
|50.0|3.7|
|100.0|5.2|
|150.0|6.4|

W tej sekcji pokazano, jak Podaj typ, który służy do Pobierz wiersze z `Distance` właściwości typu `float<meter>` i `Time` właściwości typu `float<second>`. Dla uproszczenia składają się następujące założenia:

- Nazwy nagłówków są mniej jednostek lub mieć postać "Name (jednostka)" i nie zawierać przecinków.

- Jednostki są wszystkie jednostki Systeme międzynarodowy (SI) jako [Microsoft.FSharp.Data.UnitSystems.SI.UnitNames — moduł (F #)](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b) definiuje moduł.

- Jednostki są wszystkie proste (na przykład pomiaru), a nie złożone (na przykład, licznik na sekundę).

- Wszystkie kolumny zawierają dane punktu zmiennoprzecinkowego.

Bardziej kompletny dostawca będzie Poluzuj te ograniczenia.

Pierwszym krokiem jest ponownie należy wziąć pod uwagę, jak powinna wyglądać interfejsu API. Biorąc pod uwagę `info.csv` plik z zawartością z powyższej tabeli (w formacie rozdzielonych przecinkami), użytkownicy dostawcy powinno być możliwe do pisania kodu, który przypomina poniższy przykład:

```fsharp
let info = new MiniCsv<"info.csv">()
for row in info.Data do
let time = row.Time
printfn "%f" (float time)
```

W tym przypadku kompilator należy konwertować te wywołania coś tak jak w poniższym przykładzie:

```fsharp
let info = new CsvFile("info.csv")
for row in info.Data do
let (time:float) = row.[1]
printfn "%f" (float time)
```

Optymalne tłumaczenie wymaga dostawcy typu do zdefiniowania rzeczywistych `CsvFile` typu w zestawie dostawcy typów. Dostawcy typów często zależy od kilku pomocnicze typy i metody, opakowywać logiki ważne. Ponieważ miary są usuwane w czasie wykonywania, można użyć `float[]` jako typ wymazane, na podstawie wiersza. Kompilator będzie traktować różnych kolumn jako posiadające miary różnych typów. Na przykład pierwszej kolumny, w tym przykładzie ma typ `float<meter>`, a druga ma `float<second>`. Jednak wymazane reprezentacji mogą w dalszym ciągu bardzo proste.

Poniższy kod przedstawia podstawowe wdrożenia.

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

Należy pamiętać o następujących kwestiach dotyczących implementacji:

- Przeciążenia konstruktorów umożliwiają oryginalnego pliku lub taki, który ma identyczne schematu do odczytu. Ten wzorzec jest typowa, gdy zapis dostawcy typów źródeł danych lokalnych lub zdalnych, a ten wzorzec umożliwia użycie pliku lokalnego ma być używany jako szablon dla danych zdalnych.

- Możesz użyć [typeproviderconfig —](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44) wartość, która jest przekazywana do konstruktora typu dostawcy do rozpoznawania nazw względna do pliku.

- Możesz użyć `AddDefinitionLocation` metodę, aby określić lokalizację obiektu podanej właściwości. W związku z tym Jeśli używasz `Go To Definition` podanej właściwości, plik CSV zostanie otwarty w programie Visual Studio.

- Możesz użyć `ProvidedMeasureBuilder` typu wyszukiwać jednostki SI i wygenerowania odpowiedniego `float<_>` typów.

### <a name="key-lessons"></a>Lekcje klucza

W tej sekcji wyjaśniono, jak utworzyć dostawcę typów dla źródła danych lokalnych przy użyciu prosty schemat, który jest zawarty w źródło danych.

## <a name="going-further"></a>Kontynuowanie

Poniższe sekcje zawierają sugestie dotyczące dalszych badań.

### <a name="a-look-at-the-compiled-code-for-erased-types"></a>Przyjrzeć się skompilowany kod dla typów wymazane

Aby dać niektóre informacje o tym, jak użycie dostawcy typów odnosi się do kodu, który jest emitowane, Przyjrzyj się następującą funkcję za pomocą `HelloWorldTypeProvider` używany we wcześniejszej części tego tematu.

```fsharp
let function1 () = 
    let obj1 = Samples.HelloWorldTypeProvider.Type1("some data")
    obj1.InstanceProperty
```

Oto obraz wynikowy kod decompiled przy użyciu ildasm.exe:

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

Jak pokazano w przykładzie, wszystkie wystąpienia typu `Type1` i `InstanceProperty` właściwości zostały wymazane, pozostawiając tylko operacje na typów środowiska wykonawczego związane.

### <a name="design-and-naming-conventions-for-type-providers"></a>Projektowanie i konwencje nazewnictwa dla dostawców typów

Podczas tworzenia dostawców typów, należy przestrzegać następujących konwencji.

**Dostawców łączności protokołów** ogólnie rzecz biorąc, nazwy dostawcy większość bibliotek DLL dla protokołów łączności danych i usługi, takie jak w przypadku połączeń protokołu OData lub SQL powinno zakończyć `TypeProvider` lub `TypeProviders`. Na przykład użyj nazwy biblioteki DLL, który przypomina następujący ciąg:

```
  Fabrikam.Management.BasicTypeProviders.dll
```

Należy upewnić się, że Twoje podane typy są elementami członkowskimi odpowiedniej przestrzeni nazw i wskazują protokołu łączności, które można zaimplementować:

```
  Fabrikam.Management.BasicTypeProviders.WmiConnection<…>
  Fabrikam.Management.BasicTypeProviders.DataProtocolConnection<…>
```

**Narzędzie do dostawców na potrzeby programowania ogólnego**.  Narzędzie typu dostawcy takim dla wyrażeń regularnych dostawca typów może być częścią podstawowej biblioteki, jak w poniższym przykładzie pokazano:

```fsharp
  #r "Fabrikam.Core.Text.Utilities.dll"
```

W tym przypadku podany typ pojawią się w momencie odpowiednie zgodnie z normalnym konwencjami projektu platformy .NET:

```fsharp
  open Fabrikam.Core.Text.RegexTyped
  
  let regex = new RegexTyped<"a+b+a+b+">()
```

**Źródła danych pojedyncze**. Niektórzy dostawcy typu do pojedynczego dedykowanego źródła danych i zapewniają tylko dane. W takim przypadku należy porzucić `TypeProvider` sufiks i użyj normalnej konwencji nazewnictwa platformy .NET:

```fsharp
#r "Fabrikam.Data.Freebase.dll"
  
let data = Fabrikam.Data.Freebase.Astronomy.Asteroids
```

Aby uzyskać więcej informacji, zobacz `GetConnection` projektowania Konwencji, który jest opisany w dalszej części tego tematu.

### <a name="design-patterns-for-type-providers"></a>Wzorce projektowe dla dostawców typów

Wzorce projektowe, których można użyć podczas tworzenia dostawców typów można znaleźć w poniższych sekcjach.

#### <a name="the-getconnection-design-pattern"></a>Wzorzec projektowy GetConnection

Większość dostawców typów, powinny być zapisywane do użycia `GetConnection` wzorzec, który jest używany przez dostawców typu w FSharp.Data.TypeProviders.dll, co ilustruje poniższy przykład:

```fsharp
#r "Fabrikam.Data.WebDataStore.dll"

type Service = Fabrikam.Data.WebDataStore<…static connection parameters…>

let connection = Service.GetConnection(…dynamic connection parameters…)

let data = connection.Astronomy.Asteroids
```

#### <a name="type-providers-backed-by-remote-data-and-services"></a>Dostawcy typów objęta zdalnych danych i usług

Przed utworzeniem dostawcy typów, która jest wspierana przez zdalne dane i usługi, należy wziąć pod uwagę szereg problemów, które są integralną częścią podłączonych programowania. Te problemy obejmują następujące kwestie:

- mapowanie schematu

- żywotności oraz unieważniania obecności zmiany schematu

- pamięć podręczna schematów

- implementacje asynchroniczne operacje dostępu do danych

- Obsługa zapytań, takich jak zapytania LINQ

- poświadczeń i uwierzytelniania

W tym temacie nie zbadania tych problemów w dalszych.

### <a name="additional-authoring-techniques"></a>Innych technik tworzenia pakietów administracyjnych

Podczas pisania własnych dostawców typów, można użyć następujących dodatkowych technik.

### <a name="creating-types-and-members-on-demand"></a>Tworzenie typów i elementów członkowskich na żądanie

Interfejs API ProvidedType ma opóźnione wersje Dodawanie członka.

```fsharp
  type ProvidedType =
      member AddMemberDelayed  : (unit -> MemberInfo)      -> unit
      member AddMembersDelayed : (unit -> MemberInfo list) -> unit
```

Te wersje są używane do tworzenia miejsca do magazynowania na żądanie, typów.

### <a name="providing-array-types-and-generic-type-instantiations"></a>Typy tablic i ogólnych instancji typu

Podane elementy członkowskie (których podpisów obejmują typy tablicowe, typami byref i wystąpień typów ogólnych) należy tworzyć przy użyciu normalnych `MakeArrayType`, `MakePointerType`, i `MakeGenericType` na dowolne wystąpienie <xref:System.Type>, w tym `ProvidedTypeDefinitions`.

> [!NOTE]
> W niektórych przypadkach może być konieczne Pomocnik w `ProvidedTypeBuilder.MakeGenericType`.  Zobacz [dokumentacji zestawu SDK dostawcy typu](https://github.com/fsprojects/FSharp.TypeProviders.SDK/blob/master/README.md#explicit-construction-of-code-makegenerictype-makegenericmethod-and-uncheckedquotations) Aby uzyskać więcej informacji.

### <a name="providing-unit-of-measure-annotations"></a>Zapewnianie jednostka miary adnotacji

Interfejs API ProvidedTypes zapewnia pomocników, zapewniające środek adnotacji. Na przykład, aby zapewnić typ `float<kg>`, użyj następującego kodu:

```fsharp
  let measures = ProvidedMeasureBuilder.Default
  let kg = measures.SI "kilogram"
  let m = measures.SI "meter"
  let float_kg = measures.AnnotateType(typeof<float>,[kg])
```

  Aby zapewnić typ `Nullable<decimal<kg/m^2>>`, użyj następującego kodu:

```fsharp
  let kgpm2 = measures.Ratio(kg, measures.Square m)
  let dkgpm2 = measures.AnnotateType(typeof<decimal>,[kgpm2])
  let nullableDecimal_kgpm2 = typedefof<System.Nullable<_>>.MakeGenericType [|dkgpm2 |]
```

### <a name="accessing-project-local-or-script-local-resources"></a>Uzyskiwanie dostępu do lokalnego projektu lub skryptów lokalnych zasobów

Każde wystąpienie dostawcy typów można podać `TypeProviderConfig` wartości w trakcie konstruowania. Ta wartość zawiera "folder rozwiązania" dla dostawcy (czyli folderu projektu dla kompilacji lub katalogu, który zawiera skrypt), listę przywoływanych zestawów i inne informacje.

### <a name="invalidation"></a>Unieważnieniu

Dostawców może zgłosić sygnały unieważniania powiadomić usługi języka F #, która założeń schematu mógł ulec zmianie. W przypadku unieważniania typecheck jest dokonania, jeśli dostawca jest hostowany w programie Visual Studio. Sygnał ten zostanie zignorowany, gdy dostawca jest hostowana w F # Interactive lub przez kompilator F # (fsc.exe).

### <a name="caching-schema-information"></a>Buforowanie informacji o schemacie

Dostawców często pamięci podręcznej dostęp do informacji o schemacie. Powinny być przechowywane dane w pamięci podręcznej przy użyciu nazwy pliku, który znajduje się jako statyczne parametru lub danych użytkownika. Na przykład pamięci podręcznej schematu `LocalSchemaFile` parametru w dostawcy typów w `FSharp.Data.TypeProviders` zestawu. W celu wykonania tych dostawców ten parametr statyczne poleca dostawcę typów, które mają być używane informacje schematu w określonym pliku lokalnego zamiast uzyskiwanie dostępu do źródła danych za pośrednictwem sieci. Aby korzystać z buforowanych informacji o schemacie, można również ustawić parametr static `ForceUpdate` do `false`. Można użyć podobne techniki umożliwiające dostęp do danych w trybie online i offline.

### <a name="backing-assembly"></a>Tworzenie kopii zestawu

Gdy kompilujesz `.dll` lub `.exe` pliku, plik .dll zapasowy wygenerowane typy są łączone statycznie do wynikowego zestawu. Ten link jest tworzony przez skopiowanie definicje typów języka pośredniego (IL) i wszelkie zarządzane zasoby z zestawu zapasowy w końcowym zestawie. Podczas korzystania z F # Interactive, tworzenie kopii pliku .dll nie zostaną skopiowane i zamiast tego są ładowane bezpośrednio do procesu F # Interactive.

### <a name="exceptions-and-diagnostics-from-type-providers"></a>Wyjątki i Diagnostyka z dostawcami typów

Wszystkie przypadki użycia wszystkich członków z podane typy może zgłaszać wyjątki. We wszystkich przypadkach jeśli dostawca typów zgłasza wyjątek, kompilator hosta atrybutów błąd dostawcy określonego typu.

- Typ dostawcy wyjątki nigdy nie powinno spowodować wewnętrzne błędy kompilatora.

- Dostawcy typów nie można zgłosić ostrzeżenia.

- Gdy dostawca typów znajduje się w kompilatorze F #, środowiska deweloperskiego F # lub F # Interactive, wszystkie wyjątki z tego dostawcy są przechwytywane. Właściwości wiadomości, zawsze jest tekst błędu i zostanie wyświetlone nie ślad stosu. Jeśli zamierzasz zgłosić wyjątek, może zgłosić następujące przykłady: `System.NotSupportedException`, `System.IO.IOException`, `System.Exception`.

#### <a name="providing-generated-types"></a>Zapewnianie wygenerowane typy

Do tej pory ten dokument ma wyjaśniono, jak zawierają typy wymazane. Umożliwia także mechanizm dostawcy typu F # zapewnienie wygenerowane typy, które są dodawane jako rzeczywiste definicje typów .NET do użytkowników programu. Użytkownik musi odwoływać się do wygenerowanego dostarczone typy przy użyciu definicji typu.

```fsharp
open Microsoft.FSharp.TypeProviders 

type Service = ODataService<"http://services.odata.org/Northwind/Northwind.svc/">
```

Kod pomocniczy ProvidedTypes 0.2, który jest częścią wersji języka F # 3.0 tylko ma ograniczoną obsługę zapewniające wygenerowane typy. Poniższe instrukcje muszą być spełnione dla definicji wygenerowany typ:

- `isErased` musi być równa `false`.

- Wygenerowany typ musi zostać dodany do nowo skonstruowany `ProvidedAssembly()`, który reprezentuje kontener dla fragmentów wygenerowanego kodu.

- Dostawca musi mieć zestaw, który ma plik .dll .NET zapasowy rzeczywiste z pliku .dll pasujące na dysku.

## <a name="rules-and-limitations"></a>Reguły i ograniczenia

Podczas pisania dostawców typów pamiętać o następujących reguł i ograniczeń.

### <a name="provided-types-must-be-reachable"></a>Podane typy musi być dostępny

Wszystko pod warunkiem, że typy powinny być dostępne z typami-nested. Zagnieżdżone typy są podane w wywołaniu `TypeProviderForNamespaces` konstruktora lub wywołanie `AddNamespace`. Na przykład, jeśli dostawca zawiera typ `StaticClass.P : T`, należy upewnić się, że T jest typem-nested lub zagnieżdżony w ramach jednego.

Na przykład niektórzy dostawcy udostępniają statyczne klasy takie jak `DataTypes` zawierają te `T1, T2, T3, ...` typów. W przeciwnym razie błąd mówi, że odwołanie do typu T w zestawie, A został znaleziony, ale nie można odnaleźć typu, w tym zestawie. Jeśli ten błąd występuje, sprawdź, czy wszystkie swoje podtypy można można połączyć się z dostawcą typów. Uwaga: Te `T1, T2, T3...` typy są nazywane *na bieżąco* typów. Pamiętaj, aby umieścić je w przestrzeni nazw usługi dostępne lub w typie elementu nadrzędnego.

### <a name="limitations-of-the-type-provider-mechanism"></a>Ograniczenia dotyczące mechanizmu dostawcy typów

Mechanizm dostawcy typu F # ma następujące ograniczenia:

- Podstawowej infrastruktury dla dostawców typów języka F # nie obsługuje, pod warunkiem ogólnych typów lub podano metod ogólnych.

- Mechanizm nie obsługuje zagnieżdżone typy z parametry statyczne.

## <a name="development-tips"></a>Porady dotyczące projektowania

Poniższe porady mogą być przydatne podczas procesu projektowania.

### <a name="run-two-instances-of-visual-studio"></a>Uruchom dwa wystąpienia programu Visual Studio

Można tworzyć dostawcy typów w jednym wystąpieniu i test dostawcy w innym, ponieważ test IDE zajmie blokadę na plik .dll, który uniemożliwia dostawcy typów była ponownie kompilowana. W związku z tym należy zamknąć drugiego wystąpienia programu Visual Studio podczas dostawcy jest wbudowana w pierwszej kolejności, a następnie po utworzeniu dostawcy należy ponownie drugie wystąpienie.

### <a name="debug-type-providers-by-using-invocations-of-fscexe"></a>Debugowanie dostawców typów za pomocą wywołania fsc.exe

Dostawcy typów można wywołać za pomocą następujących narzędzi:

- FSC.exe (kompilator F # wiersza polecenia)

- fsi.exe (kompilator F # Interactive)

- Devenv.exe (Visual Studio)

Dostawcy typów można debugować często najłatwiej przy użyciu fsc.exe w pliku skryptu testu (na przykład script.fsx). Można uruchomić debugera z poziomu wiersza polecenia.

```
  devenv /debugexe fsc.exe script.fsx
```

  Możesz użyć rejestrowania drukowania do strumienia wyjściowego stdout.

## <a name="see-also"></a>Zobacz także

- [Dostawcy typów](index.md)
- [Dostawcy typów zestawu SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK)
