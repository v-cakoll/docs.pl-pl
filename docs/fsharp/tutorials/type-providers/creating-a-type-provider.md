---
title: "Samouczek: tworzenie dostawcy typów (F#)"
description: "Dowiedz się, jak utworzyć własne dostawcy typów F # w F # 3.0, sprawdzając wielu dostawców typu prostego w celu zilustrowania koncepcji podstawowe."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 82bec076-19d4-470c-979f-6c3a14b7c70a
ms.openlocfilehash: a1d6315c2546de12e85efdd06cf2520605cb6e91
ms.sourcegitcommit: a19548e5167cbe7e9e58df4ffd8c3b23f17d5c7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2017
---
# <a name="tutorial-creating-a-type-provider"></a>Samouczek: Tworzenie dostawcy typów

> [!NOTE]
Ten przewodnik został napisany w języku F # 3.0 i zostanie zaktualizowany.

Mechanizm dostawcy typów F # 3.0 jest znaczną część jego obsługę programowania zaawansowanych informacji. Ten samouczek wyjaśnia sposób tworzenia własnych dostawców typu przez Instruktaż rozwoju wielu dostawców typu prostego w celu zilustrowania koncepcji podstawowe. Aby uzyskać więcej informacji na temat mechanizm dostawcy typów F #, zobacz [dostawców typów](index.md).

F # 3.0 zawiera kilka dostawców wbudowanych typów dla często używanych usług danych Internet i enterprise. Tych dostawców typów Udostępnij proste i regularnego relacyjnych baz danych i sieci usługi OData i WSDL. Ci dostawcy obsługują również kwerend LINQ F # dla tych źródeł danych.

W przypadku, gdy to konieczne, można utworzyć typu niestandardowego dostawcy, lub możesz odwoływać się do dostawców typów, utworzonych przez innych użytkowników. Na przykład organizacja może mieć usłudze danych, która udostępnia duży i rosnącym wiele nazwanych zestawów danych, każdy ze schematem stabilna danych. Można utworzyć dostawcy typów odczytujący schematów i przedstawia bieżący zestawów danych dla programisty w jednoznaczny sposób.


## <a name="before-you-start"></a>Przed rozpoczęciem
Typ mechanizmu dostawcy jest przeznaczony głównie do wstrzykiwania stabilna danych i informacji użytkowych do środowiska programowania w języku F #.

Ten mechanizm nie jest przeznaczona dla wstrzyknięcie spacje informacje o zmianie którego schematu podczas wykonywania programu w sposób, w którym mają zastosowanie w logice programu. Ponadto mechanizm nie jest przeznaczona dla meta-programowania wewnątrz języka nawet tej domeny zawiera niektóre prawidłowego użycia. Ten mechanizm należy używać tylko w razie potrzeby i gdzie tworzenie dostawcy typów zwraca bardzo wysokiej wartości.

Należy unikać pisania typ dostawcy, gdzie schemat jest niedostępna. Podobnie, należy unikać pisania dostawcy typów w przypadku, gdy zwykłych (lub nawet istniejące) biblioteki .NET będą wystarczające.

Przed rozpoczęciem, użytkownik może na następujące pytania:


- Czy masz schematu źródła informacji? Jeśli tak, co to jest mapowanie w F # i system typów .NET?

- Można użyć istniejącego interfejsu API (typach określanych dynamicznie) jako punkt początkowy implementacji?

- I całych organizacji ma za mało używa dostawcy typów, aby jej pisania zastanowić? Czy normalne biblioteki .NET potrzeb?

- Ile zmieni schemat?

- Zostanie ona zmieniona podczas kodowania?

- Będzie on zmienić między kodowania sesji?

- Zostanie ona zmieniona podczas wykonywania programu?

Typ dostawcy są najlepiej sprawdza się w sytuacjach, gdy schemat jest stabilna w czasie wykonywania, a okres istnienia skompilowanego kodu.


## <a name="a-simple-type-provider"></a>Dostawca typu prostego
Ten przykład jest Samples.HelloWorldTypeProvider w `SampleProviders\Providers` katalog [F # 3.0 przykładowy pakiet](http://fsharp3sample.codeplex.com) w witrynie Codeplex. Dostawca udostępnia "przestrzeń typu", która zawiera 100 typy wymazywania, jak przedstawiono na poniższym kodem przy użyciu składni podpisu F #, a pomijając szczegóły dla wszystkich oprócz `Type1`. Aby uzyskać więcej informacji dotyczących skasowany typów, zobacz [szczegółowe informacje o wymazane podane typy](#details-about-erased-provided-types) dalszej części tego tematu.

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

Należy zwrócić uwagę, czy zestaw typów i członków podane statycznie jest znany. W tym przykładzie nie korzystać z możliwości dostawców typów, które są zależne od schematu. Implementacja dostawcy typów przedstawiono w poniższym kodzie i szczegóły są przedstawione w kolejnych sekcjach tego tematu.


>[!WARNING] 
Może to być pewne niewielkie różnice nazewnictwa między ten kod i przykłady online.

```fsharp
namespace Samples.FSharp.HelloWorldTypeProvider

open System
open System.Reflection
open Samples.FSharp.ProvidedTypes
open Microsoft.FSharp.Core.CompilerServices
open Microsoft.FSharp.Quotations

// This type defines the type provider. When compiled to a DLL, it can be added
// as a reference to an F# command-line compilation, script, or project.
[<TypeProvider>]
type SampleTypeProvider(config: TypeProviderConfig) as this = 

  // Inheriting from this type provides implementations of ITypeProvider 
  // in terms of the provided types below.
  inherit TypeProviderForNamespaces()

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

Aby użyć tego dostawcy, otwórz osobnego wystąpienia programu Visual Studio 2012, utworzyć skrypt F #, a następnie dodaj odwołanie do dostawcy ze skryptu za pomocą #r, jak przedstawiono na poniższym kodem:

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

Poszukaj typów w obszarze `Samples.HelloWorldTypeProvider` przestrzeni nazw, która wygenerowany typ dostawcy.

Przed skompiluj dostawcy, upewnij się, że zamknięciu wszystkich wystąpień programu Visual Studio i F # Interactive, korzystających z biblioteki DLL dostawcy. W przeciwnym razie błąd kompilacji nastąpi, ponieważ dane wyjściowe biblioteki DLL zostanie zablokowane.

Do debugowania tego dostawcę przy użyciu instrukcji drukowania, wprowadź skrypt, który opisuje problem z dostawcą, a następnie użyć poniższego kodu:

```fsharp
fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

Aby debugować ten dostawca przy użyciu programu Visual Studio, otwórz wiersz polecenia programu Visual Studio przy użyciu poświadczeń administracyjnych, a następnie uruchom następujące polecenie:

```fsharp
devenv.exe /debugexe fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

Alternatywnie, Otwórz program Visual Studio, otwórz menu debugowanie, wybierz pozycję `Debug/Attach to process…`i Dołącz do innego `devenv` proces, w którym edycji skryptu. Za pomocą tej metody, można łatwiej kierować konkretnej logiki w dostawcy typów interaktywnie wpisując wyrażenia do drugiego wystąpienia (z pełną IntelliSense i inne funkcje).

Można wyłączyć opcję tylko mój kod debugowanie, aby łatwiej odróżnić błędy w wygenerowanym kodzie. Aby dowiedzieć się, jak włączyć lub wyłączyć tę funkcję, zobacz [nawigowanie po kodzie za pomocą debugera](https://msdn.microsoft.com/library/y740d9d3.aspx). Ponadto można również ustawić wyjątkach pierwszej szansy Przechwytywanie otwierając `Debug` menu, a następnie wybierając `Exceptions` lub wybierając klawisze Ctrl + Alt + E, aby otworzyć `Exceptions` okno dialogowe. W tym oknie dialogowym w obszarze `Common Language Runtime Exceptions`, wybierz pozycję `Thrown` pole wyboru.


### <a name="implementation-of-the-type-provider"></a>Implementacja dostawcy typów
W tej sekcji przedstawiono główne części typ implementacji dostawcy. Najpierw należy zdefiniować typu dla samej siebie dostawcy niestandardowego typu:

```fsharp
[<TypeProvider>]
type SampleTypeProvider(config: TypeProviderConfig) as this =
```

Ten typ musi być publiczny i należy oznaczyć go przy użyciu [TypeProvider](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947) atrybutu, aby kompilator rozpoznawał typ dostawcy, gdy oddzielny projekt F # odwołuje się do zestawu zawierającego typ. *Config* parametr jest opcjonalny i, jeśli jest obecny, zawiera informacje o konfiguracji kontekstowych dla wystąpienia dostawcy typu, który tworzy kompilator języka F #.

Następnie należy zaimplementować [itypeprovider —](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f) interfejsu. W takim przypadku należy użyć `TypeProviderForNamespaces` typu z `ProvidedTypes` interfejsu API jako typu podstawowego. Ten typ pomocnika zapewniają skończoną kolekcję dzielenia na pod warunkiem przestrzeni nazw, z których każdy bezpośrednio zawiera skończoną liczbę stałej, dzielenia na podane typy. W tym kontekście, dostawca *dzielenia na* generuje typów, nawet jeśli nie są one potrzebne lub używane.

```fsharp
inherit TypeProviderForNamespaces()
```

Następnie zdefiniuj lokalnego wartości prywatne, które określają przestrzeń nazw dla udostępnionych typów i Znajdź zestawu typu dostawcy. Ten zestaw jest później używany jako typ logiczny obiekt nadrzędny wymazanej typów, które są udostępniane.

```fsharp
let namespaceName = "Samples.HelloWorldTypeProvider"
let thisAssembly = Assembly.GetExecutingAssembly()
```

Następnie należy utworzyć funkcji poszczególnych typów Type1... Type100. Ta funkcja jest szczegółowo w dalszej części tego tematu.

```fsharp
let makeOneProvidedType (n:int) = …
```

Następnie można wygenerować 100 podane typy:

```fsharp
let types = [ for i in 1 .. 100 -> makeOneProvidedType i ]
```

Następnie dodaj typy w postaci podanego obszaru nazw:

```fsharp
do this.AddNamespace(namespaceName, types)
```

Na koniec należy dodać atrybut zestawu, który wskazuje tworzenia biblioteki DLL dostawcy typów:

```fsharp
[<assembly:TypeProviderAssembly>] 
do()
```

### <a name="providing-one-type-and-its-members"></a>Jeden typ i jej elementów członkowskich
`makeOneProvidedType` Funkcja wykonuje rzeczywistą pracę udostępniania jednego z typów.

```fsharp
let makeOneProvidedType (n:int) = 
…
```

W tym kroku opisano stosowania tej funkcji. Najpierw utwórz udostępnionego typu (na przykład Type1, gdy n = 1 lub Type57, gdy n = 57).

```fsharp
// This is the provided type. It is an erased provided type and, in compiled code, 
// will appear as type 'obj'.
let t = ProvidedTypeDefinition(thisAssembly,namespaceName,
"Type" + string n,
baseType = Some typeof<obj>)
```

Należy zwrócić uwagę następujące kwestie:


- To pod warunkiem, że typ jest usunięte.  Ponieważ wskazują, że typ podstawowy jest `obj`, wystąpień będą wyświetlane jako wartości typu [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) w skompilowany kod.
<br />

- Po określeniu typu niezagnieżdżonego, należy określić zestaw i przestrzeni nazw. Dla typów wymazanej zestawu powinna być zestawu typu dostawcy.
<br />

Następnie dodaj plik dokumentacji XML do typu. W tej dokumentacji jest opóźnione, oznacza to, obliczane na żądanie, jeśli kompilator hosta musi on.

```fsharp
t.AddXmlDocDelayed (fun () -> sprintf "This provided type %s" ("Type" + string n))
```

Następnie dodaj Podana właściwość statyczna do typu:

```fsharp
let staticProp = ProvidedProperty(propertyName = "StaticProperty", 
propertyType = typeof<string>, 
IsStatic=true,
GetterCode= (fun args -> <@@ "Hello!" @@>))
```

Pobieranie ta właściwość zawsze da się ciąg "Hello!". `GetterCode` Dla właściwości używa F # oferty, który reprezentuje kod, który generuje kompilatora hosta dla pobierania właściwości. Aby uzyskać więcej informacji o ofertach, zobacz [cytaty kodu (F #)](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155).

Dodaj plik dokumentacji XML dla właściwości.

```fsharp
staticProp.AddXmlDocDelayed(fun () -> "This is a static property")
```

Teraz należy dołączyć podane właściwości do podanego typu. Należy dołączyć jeden i tylko jeden typ podanego elementu członkowskiego. W przeciwnym razie element członkowski nigdy nie będzie dostępny.

```fsharp
t.AddMember staticProp
```

Utwórz podanych konstruktora, który nie przyjmuje żadnych parametrów.

```fsharp
let ctor = ProvidedConstructor(parameters = [ ], 
InvokeCode= (fun args -> <@@ "The object data" :> obj @@>))
```

`InvokeCode` Dla konstruktora zwraca F # oferty, który reprezentuje kod, który generuje kompilatora hosta podczas wywołania konstruktora. Można na przykład użyć konstruktora następujące:

```fsharp
new Type10()
```

Wystąpienie podanego typu zostanie utworzony z danymi źródłowymi "Dane obiektu". Kod ujętego w cudzysłów zawiera konwersji do [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) ponieważ tego typu jest skasowanie to udostępniony typ (jak określono podczas zadeklarowany udostępnionego typu).

Dodaj plik dokumentacji XML do konstruktora i Dodaj dostarczonego konstruktora do udostępnionego typu:

```fsharp
ctor.AddXmlDocDelayed(fun () -> "This is a constructor")

t.AddMember ctor
```

Utwórz drugi Konstruktor udostępnionego, który przyjmuje jeden parametr:

```fsharp
let ctor2 = 
ProvidedConstructor(parameters = [ ProvidedParameter("data",typeof<string>) ], 
InvokeCode= (fun args -> <@@ (%%(args.[0]) : string) :> obj @@>))
```

`InvokeCode` Dla konstruktora ponownie zwraca F # oferty, który reprezentuje kod wygenerowany przez kompilator hosta dla wywołania metody. Można na przykład użyć konstruktora następujące:

```fsharp
new Type10("ten")
```

Z danymi źródłowymi "10" jest tworzone wystąpienie podanego typu. Można już zauważyć, że `InvokeCode` funkcja zwraca oferty. Dane wejściowe do funkcji znajduje się lista wyrażeń, po jednym dla każdego parametru konstruktora. W takim przypadku wyrażenie, które odpowiada wartości jeden parametr jest dostępna w `args.[0]`. Kod dla wywołania konstruktora przekształca wynik dane wartości zwracanej typu wymazanej `obj`. Po dodaniu drugiego dostarczonego konstruktora do typu, możesz utworzyć właściwość udostępnionego wystąpienia:

```fsharp
let instanceProp = 
ProvidedProperty(propertyName = "InstanceProperty", 
propertyType = typeof<int>, 
GetterCode= (fun args -> 
<@@ ((%%(args.[0]) : obj) :?> string).Length @@>))
instanceProp.AddXmlDocDelayed(fun () -> "This is an instance property")
t.AddMember instanceProp
```

Pobieranie tej właściwości będzie zwracać długość ciągu, który jest obiektem reprezentacji. `GetterCode` Właściwość zwraca oferty F #, który określa kod, który generuje kompilatora hosta do pobrania właściwości. Podobnie jak `InvokeCode`, `GetterCode` funkcja zwraca oferty. Kompilator hosta wywołuje tę funkcję z listy argumentów. W takim przypadku argumenty zawierają tylko pojedyncze wyrażenie reprezentuje wystąpienie, na którym jest wywoływana metoda pobierająca, mogą korzystać za pomocą `args.[0]`. Implementacja `GetterCode` następnie splices do oferty wyników na typ wymazywania `obj`, i rzutowanie jest używana do zaspokojenia mechanizm przez kompilator do sprawdzania typów, że obiekt jest ciągiem. Następna część `makeOneProvidedType` udostępnia metodę wystąpienia z jednym parametrem.

```fsharp
let instanceMeth = 
ProvidedMethod(methodName = "InstanceMethod", 
parameters = [ProvidedParameter("x",typeof<int>)], 
returnType = typeof<char>, 
InvokeCode = (fun args -> 
<@@ ((%%(args.[0]) : obj) :?> string).Chars(%%(args.[1]) : int) @@>))

instanceMeth.AddXmlDocDelayed(fun () -> "This is an instance method")
// Add the instance method to the type.
t.AddMember instanceMeth
```

Na koniec Utwórz typu zagnieżdżonego, która zawiera 100 właściwości zagnieżdżonych. Tworzenie to zagnieżdżony typ i jego właściwości jest opóźnione, oznacza to, obliczone na żądanie.

```fsharp
t.AddMembersDelayed(fun () -> 
let nestedType = ProvidedTypeDefinition("NestedType",
Some typeof<obj>

)

nestedType.AddMembersDelayed (fun () -> 
let staticPropsInNestedType = 
[ for i in 1 .. 100 do
let valueOfTheProperty = "I am string "  + string i

let p = ProvidedProperty(propertyName = "StaticProperty" + string i, 
propertyType = typeof<string>, 
IsStatic=true,
GetterCode= (fun args -> <@@ valueOfTheProperty @@>))

p.AddXmlDocDelayed(fun () -> 
sprintf "This is StaticProperty%d on NestedType" i)

yield p ]
staticPropsInNestedType)

[nestedType])

// The result of makeOneProvidedType is the type.
t
```

### <a name="details-about-erased-provided-types"></a>Szczegółowe informacje o wymazanych podanych typów
W przykładzie w tej sekcji przedstawiono tylko *wymazane udostępnionych typów*, które są szczególnie przydatne w następujących sytuacjach:


- Podczas pisania dostawcy przestrzeni informacji zawierającego tylko dane i metody.
<br />

- Podczas pisania dostawcy, gdzie semantyki dokładne typ środowiska uruchomieniowego nie są krytyczne dla praktyczne wykorzystanie miejsca informacji.
<br />

- Podczas pisania dostawcy przestrzeni informacji tak dużej i wzajemnie połączone, że nie jest technicznie możliwe do generowania rzeczywistych typów .NET do obszaru informacji.
<br />

W tym przykładzie każdy z podanych usunięciem typu na typ `obj`, i wszystkich używa tego typu będą wyświetlane jako typ `obj` w skompilowany kod. W rzeczywistości obiektów w tym przykładzie są ciągami, ale typ będzie wyświetlany jako `System.Object` w .NET skompilowany kod. Jak z wszystkich zastosowań usunięcia typu, możesz użyć jawnego pakującej, Rozpakowywanie i rzutowanie do mógł wykorzystać wymazane typów. W takim przypadku wyjątek rzutowania, który nie jest prawidłową może spowodować, jeśli obiekt jest używany. Środowisko uruchomieniowe dostawcy można zdefiniować własny typ reprezentacji prywatnych, aby zapewnić ochronę przed reprezentacje wartość false. Nie można zdefiniować wymazanej typów w języku F # samej siebie. Tylko podane typy mogą zostać utracone. Należy poznać konsekwencje, zarówno praktyczne i semantyczne dowolną wymazanej typów dla typu dostawcy lub dostawcę, który zapewnia usunięte typów. Typ wymazywania nie ma rzeczywistego .NET typu. W związku z tym nie można dokładnie odzwierciedla za pośrednictwem typu i może mógł wykorzystać wymazanej typów środowiska wykonawczego rzutowania i innych technik, które opierają się na semantykę typu dokładne środowiska uruchomieniowego za pomocą. Podwersją wymazanej typów często skutkuje typu rzutowania wyjątków w czasie wykonywania.


### <a name="choosing-representations-for-erased-provided-types"></a>Wybieranie oświadczenia dla wymazane podane typy
Dla niektórych zastosowaniach wymazanych podanych typów nie jest wymagana. Na przykład wymazanej dostarczono typu może zawierać tylko właściwości statycznych i elementów członkowskich i ma konstruktorów oraz żadnych metod ani właściwości zwróci wystąpienia typu. Dostęp można uzyskać wystąpień wymazanej podany typ, należy wziąć pod uwagę następujące kwestie:


- Co to jest skasowanie udostępnionego typu?
<br />
  - Skasowanie udostępnionego typu jest sposób wyświetlania typu skompilowanego kodu .NET.
<br />

  - Skasowanie typu klasy wymazanej podany jest zawsze pierwszy-wymazane typu podstawowego w łańcuch dziedziczenia tego typu.
<br />

  - Skasowanie tego typu interfejsu wymazanej podany jest zawsze `System.Object`.
<br />

- Co to są oświadczenia udostępnionego typu?
<br />
  - Zestaw obiektów możliwych do wymazanej podany typ są nazywane oświadczeń. W tym przykładzie w tym dokumencie typy oświadczeń wszystkich wymazanej podany `Type1..Type100` są zawsze obiektów typu string.
<br />

Wszystkie oświadczenia udostępnionego typu muszą być zgodne z skasowanie podanego typu. (W przeciwnym razie kompilator języka F # zapewni Błąd stosowania typ dostawcy lub zostanie wygenerowany zweryfikowanie kodu platformy .NET, który nie jest prawidłowy. Typ dostawcy nie jest prawidłowy, jeśli zwróci ona kod, który udostępnia reprezentację, który nie jest prawidłowy.)

Możesz wybrać reprezentację podanych obiektów przy użyciu jednej z następujących metod, które są często:


- Jeśli po prostu jednoznacznie otoki przez istniejący typ architektury .NET, często warto dla danego typu wymazać dla tego typu, należy użyć wystąpienia tego typu jako oświadczenia lub oba. Ta metoda jest odpowiednie, gdy większość istniejących metod tego typu nadal sensu, korzystając z silnie typizowaną wersję.
<br />

- Jeśli chcesz utworzyć interfejs API, który różni się znacząco od wszystkich istniejących API .NET, warto do tworzenia typów środowiska uruchomieniowego, które będą usunięcia typu i oświadczenia dla udostępnionych typów.
<br />

W przykładzie w niniejszym dokumencie użyto ciągi jako reprezentacje podanych obiektów. Często może być stosowanie reprezentacje inne obiekty. Na przykład może użyć słownika jako zbiór właściwości:

```fsharp
ProvidedConstructor(parameters = [], 
InvokeCode= (fun args -> <@@ (new Dictionary<string,obj>()) :> obj @@>))
```

Alternatywnie może zdefiniować typu w dostawcy typu, który będzie używany w czasie wykonywania do utworzenia reprezentacji, wraz z co najmniej jedną operację środowiska uruchomieniowego:

```fsharp
type DataObject() =
let data = Dictionary<string,obj>()
member x.RuntimeOperation() = data.Count
```

Podane elementy członkowskie następnie można utworzyć wystąpień tego typu obiektu:

```fsharp
ProvidedConstructor(parameters = [], 
InvokeCode= (fun args -> <@@ (new DataObject()) :> obj @@>))
```

W takim przypadku może (opcjonalnie) używasz tego typu jako typ wymazywania, określając tego typu jako `baseType` podczas konstruowania `ProvidedTypeDefinition`:

```fsharp
ProvidedTypeDefinition(…, baseType = Some typeof<DataObject> )
…
ProvidedConstructor(…, InvokeCode = (fun args -> <@@ new DataObject() @@>), …)
```

`Key Lessons`

W poprzedniej sekcji objaśniono sposób tworzenia prostego wymazywanie dostawcy typu, który udostępnia szereg typów, właściwości i metod. W tej sekcji również wyjaśniono pojęcie usunięcia typu, w tym niektóre zalety i wady udostępnia typy wymazanej od dostawcy typów i opisem reprezentacje wymazanej typów.


## <a name="a-type-provider-that-uses-static-parameters"></a>Typ dostawcy, która używa parametrów statycznych
Możliwość parametryzacja dostawców typu na statycznych danych umożliwia wielu scenariuszy interesujące, nawet w przypadku dostawcy nie potrzebuje dostępu do żadnych danych lokalnych lub zdalnych. W tej sekcji omówiono niektóre podstawowe techniki zestawienie takiego dostawcy.


### <a name="type-checked-regex-provider"></a>Typ zaznaczone dostawcy wyrażeń regularnych
Wyobraź sobie chcesz implementowania dostawcy typu dla wyrażeń regularnych, który opakowuje .NET `System.Text.RegularExpressions.Regex` bibliotek interfejs, który udostępnia następujące gwarancje kompilacji:


- Sprawdzanie, czy wyrażenie regularne jest nieprawidłowy.
<br />

- Udostępnia właściwości o nazwie na dopasowań, które są oparte na wszystkie nazwy grup w wyrażeniu regularnym.
<br />

W tej sekcji przedstawiono sposób umożliwia tworzenie dostawcy typów `RegExProviderType` wpisz, że wzorzec wyrażenia regularnego parameterizes umożliwia uzyskiwanie tych korzyści. Kompilator będzie zgłaszać błąd, jeśli dostarczonym wzorcem nie jest prawidłowa, a dostawca typów można wyodrębnić grup z wzorzec, dzięki czemu będą dostępne za pomocą o nazwie właściwości dopasowań. Podczas projektowania dostawcy typów, należy rozważyć wygląd jego narażonych interfejsu API do użytkowników końcowych i jak przekształci ten projekt w kodu platformy .NET. Poniższy przykład przedstawia sposób użycia interfejsu API na pobranie składników numer kierunkowy:

```fsharp
type T = RegexTyped< @"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)">
let reg = T()
let result = T.IsMatch("425-555-2345")
let r = reg.Match("425-555-2345").Group_AreaCode.Value //r equals "425"
```

W poniższym przykładzie pokazano, jak typ dostawcy tłumaczy tych wywołań:

```fsharp
let reg = new Regex(@"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)")
let result = reg.IsMatch("425-123-2345")
let r = reg.Match("425-123-2345").Groups.["AreaCode"].Value //r equals "425"
```

Należy uwzględnić następujące kwestie:


- Standardowy typ wyrażenia regularnego reprezentuje sparametryzowane `RegexTyped` typu.
<br />

- `RegexTyped` Konstruktor powoduje wywołanie konstruktora wyrażeń regularnych, przekazując argument typu statycznego dla wzorca.
<br />

- Wyniki `Match` metody są reprezentowane przez standardowe `System.Text.RegularExpressions.Match` typu.
<br />

- Każda grupa o nazwie powoduje podane właściwości i uzyskiwania dostępu do właściwości powoduje użycie indeksatora w przypadku dopasowania `Groups` kolekcji.
<br />

Następujący kod jest podstawową logikę do wykonania takiego dostawcy, a w tym przykładzie są pomijane przez dodanie wszystkich elementów członkowskich do udostępnionego typu. Informacje o każdym dodano element członkowski Zobacz odpowiedniej sekcji w dalszej części tego tematu. Dla pełnego kodu, Pobierz przykład z [F # 3.0 przykładowy pakiet](http://fsharp3sample.codeplex.com) w witrynie Codeplex.

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
let ty = ProvidedTypeDefinition(
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

Należy uwzględnić następujące kwestie:


- Typ dostawcy przyjmuje dwa parametry statyczne: `pattern`, który jest obowiązkowy oraz `options`, które są opcjonalne (ponieważ podano wartość domyślna).
<br />

- Po argumentów statycznych są dostarczane, można utworzyć wystąpienia wyrażenia regularnego. Tego wystąpienia spowoduje zgłoszenie wyjątku, jeśli wyrażenia regularnego jest nieprawidłowo sformułowany, a ten błąd będzie zgłaszany użytkownikom.
<br />

- W ramach `DefineStaticParameters` wywołania zwrotnego, zdefiniuj typ, który zostanie zwrócona po podano argumenty.
<br />

- Ten kod ustawia `HideObjectMethods` na wartość true, aby w środowisku IntelliSense pozostanie prostsze. Powoduje, że ten atrybut `Equals`, `GetHashCode`, `Finalize`, i `GetType` elementów członkowskich mają zostać pominięte z list IntelliSense dla podanego obiektu.
<br />

- Możesz użyć `obj` jako typ bazowy metody, ale będzie użyj `Regex` obiektu jako środowiska uruchomieniowego reprezentacja tego typu, jak w następnym przykładzie.
<br />

- Wywołanie `Regex` zgłasza konstruktora `System.ArgumentException` po wyrażenie regularne jest nieprawidłowy. Kompilator przechwytuje tego wyjątku i raporty komunikat o błędzie do użytkownika w czasie kompilacji lub w edytorze programu Visual Studio. Ten wyjątek umożliwia wyrażeń regularnych do sprawdzenia poprawności bez uruchamiania aplikacji.
<br />

Typ zdefiniowany powyżej jest bezużyteczne jeszcze ponieważ nie zawiera ona właściwości lub metody łatwy do rozpoznania. Najpierw dodaj statycznego `IsMatch` metody:

```fsharp
let isMatch = ProvidedMethod(
methodName = "IsMatch", 
parameters = [ProvidedParameter("input", typeof<string>)], 
returnType = typeof<bool>, 
IsStaticMethod = true,
InvokeCode = fun args -> <@@ Regex.IsMatch(%%args.[0], pattern) @@>) 

isMatch.AddXmlDoc "Indicates whether the regular expression finds a match in the specified input string." 
ty.AddMember isMatch
```

Poprzedni kod definiuje metodę `IsMatch`, która przyjmuje ciągu na wejściu i zwraca `bool`. Tylko wymagana jest użycie `args` argument w `InvokeCode` definicji. W tym przykładzie `args` znajduje się lista ofert reprezentujący argumenty do tej metody. Jeśli metoda jest metodą wystąpienia, pierwszy argument reprezentuje `this` argumentu. Dla metody statycznej, argumenty są wszystkie tylko jawne argumenty metody. Należy pamiętać, że typ cudzysłowie wartości powinna być zgodna określony zwracany typ (w tym przypadku `bool`). Należy także zauważyć, że używa tego kodu `AddXmlDoc` metody, aby upewnić się, że podana metoda ma również przydatne dokumentacji, której można zapewnić za pomocą funkcji IntelliSense.

Następnie dodaj wystąpienia metody Match. Jednak ta metoda powinna zwrócić wartość podana `Match` wpisz, aby grupy jest możliwy w sposób jednoznaczny. W związku z tym najpierw zadeklarować `Match` typu. Ponieważ ten typ zależy od wzorca, który został dostarczony jako argument statyczny, tego typu musi być zagnieżdżony w definicji typu sparametryzowane:

```fsharp
let matchTy = ProvidedTypeDefinition(
"MatchType", 
baseType = Some baseTy, 
HideObjectMethods = true)

ty.AddMember matchTy
```

Można następnie dodać jedną właściwość na typ dopasowania dla każdej grupy. W czasie wykonywania, dopasowanie jest reprezentowany jako `System.Text.RegularExpressions.Match` wartości, należy użyć cudzysłowów, który definiuje właściwość `System.Text.RegularExpressions.Match.Groups` indeksowane właściwości, aby uzyskać odpowiednie grupy.

```fsharp
for group in r.GetGroupNames() do
// Ignore the group named 0, which represents all input.
if group <> "0" then
let prop = ProvidedProperty(
propertyName = group, 
propertyType = typeof<Group>, 
GetterCode = fun args -> <@@ ((%%args.[0]:obj) :?> Match).Groups.[group] @@>)
prop.AddXmlDoc(sprintf @"Gets the ""%s"" group from this match" group)
matchTy.AddMember prop
```

Ponownie należy pamiętać, podane właściwości dodajesz dokumentacji XML. Należy także zauważyć, że właściwość może zostać odczytany, jeśli `GetterCode` funkcja zapewnia i właściwości mogą być zapisywane, jeśli `SetterCode` podano funkcji, aby wynikowych właściwość jest tylko do odczytu.

Teraz można utworzyć metody wystąpienia, która zwraca wartość tego `Match` typu:

```fsharp
let matchMethod = 
ProvidedMethod(
methodName = "Match", 
parameters = [ProvidedParameter("input", typeof<string>)], 
returnType = matchTy, 
InvokeCode = fun args -> <@@ ((%%args.[0]:obj) :?> Regex).Match(%%args.[1]) :> obj @@>)
matchMeth.AddXmlDoc "Searches the specified input string for the first ocurrence of this regular expression" 

ty.AddMember matchMeth
```

Ponieważ tworzysz metodą wystąpienia `args.[0]` reprezentuje `RegexTyped` wystąpienia, na którym jest wywoływana metoda, i `args.[1]` jest argument wejściowy.

Na koniec należy umożliwić konstruktora, dzięki czemu można utworzyć wystąpienia podanego typu.

```fsharp
let ctor = ProvidedConstructor(
parameters = [], 
InvokeCode = fun args -> <@@ Regex(pattern, options) :> obj @@>)
ctor.AddXmlDoc("Initializes a regular expression instance.")

ty.AddMember ctor
```

Konstruktor powoduje usunięcie tylko do utworzenia standardowe wystąpienia wyrażenie regularne .NET, która jest opakowany ponownie do obiektu, ponieważ `obj` jest skasowanie podanego typu. Z tą zmianą Przykładowe użycie interfejsu API, który określony wcześniej w temacie działa zgodnie z oczekiwaniami. Następujący kod jest pełny i końcowe:

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



let ty = ProvidedTypeDefinition(
thisAssembly, 
rootNamespace, 
typeName, 
baseType = Some baseTy)

ty.AddXmlDoc "A strongly typed interface to the regular expression '%s'"

// Provide strongly typed version of Regex.IsMatch static method.
let isMatch = ProvidedMethod(
methodName = "IsMatch", 
parameters = [ProvidedParameter("input", typeof<string>)], 
returnType = typeof<bool>, 
IsStaticMethod = true,
InvokeCode = fun args -> <@@ Regex.IsMatch(%%args.[0], pattern) @@>) 

isMatch.AddXmlDoc "Indicates whether the regular expression finds a match in the specified input string"

ty.AddMember isMatch

// Provided type for matches
// Again, erase to obj even though the representation will always be a Match
let matchTy = ProvidedTypeDefinition(
"MatchType", 
baseType = Some baseTy, 
HideObjectMethods = true)

// Nest the match type within parameterized Regex type.
ty.AddMember matchTy

// Add group properties to match type
for group in r.GetGroupNames() do
// Ignore the group named 0, which represents all input.
if group <> "0" then
let prop = ProvidedProperty(
propertyName = group, 
propertyType = typeof<Group>, 
GetterCode = fun args -> <@@ ((%%args.[0]:obj) :?> Match).Groups.[group] @@>)
prop.AddXmlDoc(sprintf @"Gets the ""%s"" group from this match" group)
matchTy.AddMember(prop)

// Provide strongly typed version of Regex.Match instance method.
let matchMeth = ProvidedMethod(
methodName = "Match", 
parameters = [ProvidedParameter("input", typeof<string>)], 
returnType = matchTy, 
InvokeCode = fun args -> <@@ ((%%args.[0]:obj) :?> Regex).Match(%%args.[1]) :> obj @@>)
matchMeth.AddXmlDoc "Searches the specified input string for the first occurence of this regular expression"

ty.AddMember matchMeth

// Declare a constructor.
let ctor = ProvidedConstructor(
parameters = [], 
InvokeCode = fun args -> <@@ Regex(pattern) :> obj @@>)

// Add documentation to the constructor.
ctor.AddXmlDoc "Initializes a regular expression instance"

ty.AddMember ctor

ty
| _ -> failwith "unexpected parameter values")) 

do this.AddNamespace(rootNamespace, [regexTy])

[<TypeProviderAssembly>]
do ()
```

`Key Lessons`

W tej sekcji wyjaśniono, jak utworzyć typ dostawcy, który działa na jego parametrów statycznych. Dostawca sprawdza parametr statyczny i udostępnia operacje na podstawie jego wartości.


## <a name="a-type-provider-that-is-backed-by-local-data"></a>Typ dostawcy, który nie jest obsługiwana przez dane lokalne
Często może być typ dostawcy do prezentowania interfejsów API oparte na nie tylko parametrów statycznych, ale także informacje z systemów lokalnych lub zdalnych. W tej sekcji omówiono dostawców typów, które są oparte na danych lokalnych, takich jak pliki danych lokalnych.


### <a name="simple-csv-file-provider"></a>Dostawca plików CSV proste
Jako przykład prostego należy wziąć pod uwagę typ dostawcy do uzyskiwania dostępu do danych naukowych w formacie wartości rozdzielanych przecinkami (CSV). W tej sekcji założono, że pliki CSV zawiera wiersz nagłówka następuje ruchomy punkt danych, jak pokazano w poniższej tabeli:



|Odległość (licznik)|Czas (sekundy)|
|----------------|-------------|
|50.0|3.7|
|100.0|5.2|
|150.0|6.4|
W tej sekcji przedstawiono sposób zapewniają typu, który można pobrać wiersze z `Distance` właściwości typu `float<meter>` i `Time` właściwości typu `float<second>`. Dla uproszczenia zostały wprowadzone następujące założenia:


- Nazwy nagłówków są albo bez jednostki lub mieć formę "Nazwa (jednostka)" i nie mogą zawierać przecinków.
<br />

- Jednostki są wszystkie jednostki Systeme międzynarodowych (SI) jako [Microsoft.FSharp.Data.UnitSystems.SI.UnitNames — moduł (F #)](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b) definiuje modułu.
<br />

- Jednostki są wszystkie proste (na przykład pomiaru) zamiast złożony (na przykład, zliczania na sekundę).
<br />

- Wszystkie kolumny zawiera przestawne punktu danych.
<br />

Bardziej szczegółowy dostawcy czy Poluzuj te ograniczenia.

Pierwszym krokiem jest ponownie należy wziąć pod uwagę, jak powinna wyglądać interfejsu API. Podane `info.csv` plik z zawartością z powyższej tabeli (w formacie rozdzielone przecinkami), użytkownicy dostawcy powinni mieć do pisania kodu, który podobnego do następującego:

```fsharp
let info = new MiniCsv<"info.csv">()
for row in info.Data do
let time = row.Time
printfn "%f" (float time)
```

W takim przypadku kompilator powinien konwertować te wywołania coś jak w następującym przykładzie:

```fsharp
let info = new MiniCsvFile("info.csv")
for row in info.Data do
let (time:float) = row.[1]
printfn "%f" (float time)
```

Optymalne tłumaczenia będzie wymagać typ dostawcy do definiowania rzeczywistych `CsvFile` typu w zestawie typ dostawcy. Dostawcy typów często polegają na kilka typów pomocnika i metod do opakowywania logiki ważne. Ponieważ miary są usuwane w czasie wykonywania, można użyć `float[]` jako typ wymazywania wiersza. Kompilator będzie traktować różnych kolumn jako mający miary różnych typów. Na przykład pierwsza kolumna w naszym przykładzie ma typ `float<meter>`, a druga `float<second>`. Reprezentacja wymazanej można nadal bardzo proste.

Poniższy kod przedstawia podstawowe implementacji.

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
inherit TypeProviderForNamespaces()

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

let prop = ProvidedProperty(fieldName, fieldTy, 
GetterCode = fun [row] -> <@@ (%%row:float[]).[i] @@>)

// Add metadata that defines the property's location in the referenced file.
prop.AddDefinitionLocation(1, headers.[i].Index + 1, filename)
rowTy.AddMember(prop) 

// Define the provided type, erasing to CsvFile.
let ty = ProvidedTypeDefinition(asm, ns, tyName, Some(typeof<CsvFile>))

// Add a parameterless constructor that loads the file that was used to define the schema.
let ctor0 = ProvidedConstructor([], 
InvokeCode = fun [] -> <@@ CsvFile(resolvedFilename) @@>)
ty.AddMember ctor0

// Add a constructor that takes the file name to load.
let ctor1 = ProvidedConstructor([ProvidedParameter("filename", typeof<string>)], 
InvokeCode = fun [filename] -> <@@ CsvFile(%%filename) @@>)
ty.AddMember ctor1

// Add a more strongly typed Data property, which uses the existing property at runtime.
let prop = ProvidedProperty("Data", typedefof<seq<_>>.MakeGenericType(rowTy), 
GetterCode = fun [csvFile] -> <@@ (%%csvFile:CsvFile).Data @@>)
ty.AddMember prop

// Add the row type as a nested type.
ty.AddMember rowTy
ty)

// Add the type to the namespace.
do this.AddNamespace(ns, [csvTy])
```

Należy uwzględnić następujące kwestie dotyczące implementacji:


- Przeciążone konstruktory Zezwalaj oryginalny plik lub klucz, który ma taki sam schemat do odczytu. Ten wzorzec jest wspólne, gdy zapis dostawcy typów źródeł danych lokalnych lub zdalnych, a ten wzorzec umożliwia pliku lokalnego do użycia jako szablon dla danych zdalnych.
<br />  Można użyć [TypeProviderConfig](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44) wartość, która jest przekazywany do konstruktora typu dostawcy do rozpoznawania względnych nazw plików.
<br />

- Można użyć `AddDefinitionLocation` metodę, aby określić lokalizację podana. Dlatego jeśli używasz `Go To Definition` podane właściwości pliku CSV zostanie otwarty w programie Visual Studio.
<br />

- Można użyć `ProvidedMeasureBuilder` typu do wyszukiwania jednostki SI oraz do generowania odpowiednich `float<_>` typów.
<br />

`Key Lessons`

W tej sekcji wyjaśniono sposób tworzenia ze schematem proste, który jest zawarty w źródle danych sam typ dostawcy do lokalnego źródła danych.


## <a name="going-further"></a>Kontynuowanie
W poniższych sekcjach zawarto sugestie dotyczące dalszych badań.


### <a name="a-look-at-the-compiled-code-for-erased-types"></a>Szukaj w kompilowanym kodzie Wymazanej typów
Aby dać wstępnym sposób korzystania z dostawcy typu odnosi się do kodu, który jest emitowany, obejrzyj następująca funkcja przy użyciu `HelloWorldTypeProvider` używany we wcześniejszej części tego tematu.

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

Jak przedstawiono na przykład wszystkie wystąpienia typu `Type1` i `InstanceProperty` właściwości zostały wymazane, pozostawiając związane tylko operacje na typów środowiska wykonawczego.


### <a name="design-and-naming-conventions-for-type-providers"></a>Projektowanie i konwencje nazewnictwa dla dostawców typów
Podczas tworzenia dostawców typów, należy przestrzegać następujących konwencji.


- `Providers for Connectivity Protocols`
<br />  Ogólnie rzecz biorąc, nazwy dostawcy większości biblioteki DLL dla danych i usługi łączności protokołów, takich jak połączenia OData lub SQL, należy zakończyć w `TypeProvider` lub `TypeProviders`. Na przykład użyj nazwy biblioteki DLL podobny następujący ciąg:
<br />

```
  Fabrikam.Management.BasicTypeProviders.dll
```

  Sprawdź, czy Twojego podanych typów są członkami odpowiedniej przestrzeni nazw i wskazywać, w której można zaimplementować protokół łączności:
<br />

```
  Fabrikam.Management.BasicTypeProviders.WmiConnection<…>
  Fabrikam.Management.BasicTypeProviders.DataProtocolConnection<…>
```

- `Utility Providers for General Coding`
<br />  Narzędzie typu dostawcy takim jak dla wyrażeń regularnych dostawca typów może być częścią podstawowej biblioteki, jak przedstawiono na poniższym przykładzie:
<br />

```fsharp
  #r "Fabrikam.Core.Text.Utilities.dll"
```

  W takim przypadku podanego typu pojawią się w odpowiednich punkcie zgodnie z normalnym konwencje projekt .NET:
<br />

```fsharp
  open Fabrikam.Core.Text.RegexTyped
  
  let regex = new RegexTyped<"a+b+a+b+">()
```

- `Singleton Data Sources`
<br />  Niektórzy dostawcy typu połączyć się z jednego dedykowanych źródła danych i podaj tylko dane. W takim przypadku należy usunąć `TypeProvider` sufiks i użyj normalnej konwencji nazewnictwa platformy .NET:
<br />

```fsharp
  #r "Fabrikam.Data.Freebase.dll"
  
  let data = Fabrikam.Data.Freebase.Astronomy.Asteroids
```

  Aby uzyskać więcej informacji, zobacz `GetConnection` projektowania Konwencji, które jest opisane w dalszej części tego tematu.
<br />


### <a name="design-patterns-for-type-providers"></a>Wzorce projektowe dla dostawców typów
W poniższych sekcjach opisano wzorce projektowe, używanego podczas tworzenia typu dostawcy.


#### <a name="the-getconnection-design-pattern"></a>Wzorzec projektowy GetConnection
Większość dostawców typów mają być zapisywane do użycia `GetConnection` wzorca, który jest używany przez dostawców typów w FSharp.Data.TypeProviders.dll, jak przedstawiono na poniższym przykładzie:

```fsharp
#r "Fabrikam.Data.WebDataStore.dll"

type Service = Fabrikam.Data.WebDataStore<…static connection parameters…>

let connection = Service.GetConnection(…dynamic connection parameters…)

let data = connection.Astronomy.Asteroids
```

#### <a name="type-providers-backed-by-remote-data-and-services"></a>Dostawcy typów kopii danych zdalnych i usługi
Przed utworzeniem typ dostawcy, który nie jest obsługiwana przez zdalnych danych i usług, należy wziąć pod uwagę szereg problemów, które są związane z połączonych programowania. Te problemy obejmują następujące zagadnienia:


- Mapowanie schematu
<br />

- liveness i unieważniania obecności zmiany schematu
<br />

- buforowanie schematu
<br />

- asynchroniczne implementacje operacji uzyskiwania dostępu do danych
<br />

- Obsługa zapytania, łącznie z zapytań LINQ
<br />

- poświadczeń i uwierzytelniania
<br />

W tym temacie nie Poznaj dodatkowe tych problemów.


### <a name="additional-authoring-techniques"></a>Innych technik tworzenia pakietów administracyjnych
Podczas pisania własnych dostawców typów, można korzystać z następujących metod dodatkowe.


- `Creating Types and Members On-Demand`
<br />  Interfejs API ProvidedType ma opóźnione wersji Dodawanie członka.
<br />

```fsharp
  type ProvidedType =
  member AddMemberDelayed  : (unit -> MemberInfo)      -> unit
  member AddMembersDelayed : (unit -> MemberInfo list) -> unit
```

  Te wersje są używane do tworzenia spacje na żądanie typów.
<br />

- `Providing Array, ByRef, and Pointer types`
<br />  Tworzenie podanych elementów członkowskich (których podpisów obejmują typy tablic, typów byref i wystąpień typów ogólnych) przy użyciu normalnych `MakeArrayType`, `MakePointerType`, i `MakeGenericType` na dowolne wystąpienie System.Type, łącznie z `ProvidedTypeDefinitions`.
<br />

- `Providing Unit of Measure Annotations`
<br />  Interfejs API ProvidedTypes zapewnia pomocników zapewniające adnotacje miary. Na przykład Podaj typ `float<kg>`, użyj następującego kodu:
<br />

```fsharp
  let measures = ProvidedMeasureBuilder.Default
  let kg = measures.SI "kilogram"
  let m = measures.SI "meter"
  let float_kg = measures.AnnotateType(typeof<float>,[kg])
```

  Aby zapewnić typ `Nullable<decimal<kg/m^2>>`, użyj następującego kodu:
<br />

```fsharp
  let kgpm2 = measures.Ratio(kg, measures.Square m)
  let dkgpm2 = measures.AnnotateType(typeof<decimal>,[kgpm2])
  let nullableDecimal_kgpm2 = typedefof<System.Nullable<_>>.MakeGenericType [|dkgpm2 |]
```

- `Accessing Project-Local or Script-Local Resources`
<br />  Każde wystąpienie dostawcy typów można przydzielić `TypeProviderConfig` wartości podczas konstruowania. Ta wartość zawiera "folder rozwiązania" dla dostawcy (oznacza to, że folder projektu dla kompilacji lub katalog, który zawiera skrypt), na liście zestawów występujących w odwołaniach i inne informacje.
<br />

- `Invalidation`
<br />  Dostawców może wiązać się z sygnałów unieważniania powiadomić usługi języka F #, który mógł ulec zmianie założeń schematu. W przypadku unieważniania typecheck jest ponownie wykonać, jeśli dostawca jest obsługiwana w programie Visual Studio. Sygnał ten zostanie zignorowany, gdy dostawca jest obsługiwane w F # Interactive lub przez kompilator języka F # (fsc.exe).
<br />

- `Caching Schema Information`
<br />  Dostawców, często pamięci podręcznej dostęp do informacji o schemacie. Buforowane dane powinny być przechowywane przy użyciu podanej nazwy pliku, jako parametr statyczny lub dane użytkownika. Na przykład z pamięci podręcznej schematu `LocalSchemaFile` parametru w pomocy dostawcy typów w `FSharp.Data.TypeProviders` zestawu. W celu wykonania tych dostawców ten parametr statyczny kieruje typ dostawcy do użycia informacji o schemacie w określonym pliku lokalnego zamiast dostępu do źródła danych za pośrednictwem sieci. Aby użyć buforowanych informacji o schemacie, należy także ustawić parametr statyczny `ForceUpdate` do `false`. Aby włączyć dostęp do danych w trybie online i jest w trybie offline, można użyć technika podobne.
<br />

- `Backing Assembly`
<br />  Podczas kompilowania pliku .dll lub .exe statycznie połączonej plik .dll zapasowy wygenerowane typy do wynikowego zestawu. Ten link jest tworzony przez skopiowanie definicje typów języku pośrednim (IL) i wszystkie zarządzane zasoby z zestawu zapasowy w zestawie końcowym. Korzystając z narzędzia F # Interactive, tworzenie kopii pliku dll nie jest kopiowana i zamiast tego zostanie załadowana bezpośrednio do proces narzędzia F # Interactive.
<br />

- `Exceptions and Diagnostics from Type Providers`
<br />  Wszystkie używa wszystkich elementów członkowskich z udostępnionych typów może zgłaszać wyjątków. We wszystkich przypadkach Jeśli typ dostawcy zgłasza wyjątek, kompilator hosta atrybutów błąd do określonego typu dostawcy.
<br />
  - Typ dostawcy wyjątki nigdy nie powinno spowodować wewnętrzne błędy kompilatora.
<br />

  - Dostawcy typów nie może zaraportować ostrzeżenia.
<br />

  - Gdy dostawca typów znajduje się w kompilator języka F # środowiska deweloperskiego F # i F # Interactive, wszystkie wyjątki od tego dostawcy są przechwytywane. Właściwości wiadomości jest zawsze tekst błędu, i pojawi się śladów stosu. Jeśli zamierzasz zgłosić wyjątek, może zgłosić następujące przykłady:
<br />
    - `System.NotSupportedException`
<br />

    - `System.IO.IOException`
<br />

    - `System.Exception`
<br />


#### <a name="providing-generated-types"></a>Zapewnianie wygenerowane typy
Do tej pory ten dokument ma wyjaśniono sposób Określ typy wymazany. Umożliwia także mechanizm dostawcy typu w języku F # zapewnienie wygenerowane typy, które są dodawane jako rzeczywiste definicje typów .NET do użytkowników programu. Użytkownik musi odwoływać się do wygenerowanego podane typy przy użyciu definicji typu.

```fsharp
open Microsoft.FSharp.TypeProviders 

type Service = ODataService<" http://services.odata.org/Northwind/Northwind.svc/">
```

Kod pomocnika 0,2 ProvidedTypes, który wchodzi w skład wersji języka F # 3.0 ma tylko ograniczoną obsługę dostarczanie wygenerowane typy. Poniższe instrukcje musi mieć wartość true dla definicji wygenerowanego typu:


- Musi mieć ustawioną IsErased `false`.
<br />

- Dostawca musi mieć zestawu, który ma zapasowy rzeczywisty plik dll .NET z odpowiedniego pliku dll na dysku.
<br />

Musisz również wywołać `ConvertToGenerated` typu głównego pod warunkiem, którego zagnieżdżone typy tworzą zamkniętego zestawu wygenerowanych typów. To wywołanie emituje definicji danego udostępnionego typu i jego definicje typu zagnieżdżonego w zestawie i dostosowuje `Assembly` właściwości wszystkich definicji udostępnionego typu, aby powrócić do tego zestawu. Zestaw jest emitowany tylko wtedy, gdy właściwość zestawu dla typu głównego jest dostępny po raz pierwszy. Kompilator języka F # hosta dostępu do tej właściwości podczas przetwarzania deklaracji generative typu dla typu.


## <a name="rules-and-limitations"></a>Reguły i ograniczenia
Podczas pisania dostawców typów pamiętać poniższe reguły i ograniczenia.


- `Provided types must be reachable.`
<br />  Wszystkie pod warunkiem, że typy, powinny być dostępne z typów-nested. Zagnieżdżone typy są podane w wywołaniu `TypeProviderForNamespaces` konstruktora lub wywołanie `AddNamespace`. Na przykład, jeśli dostawca miejsce na wpisanie `StaticClass.P : T`, należy upewnić się czy T jest typu niezagnieżdżonego lub zagnieżdżona pod jedną.
<br />  Na przykład niektóre dostawców ma klasie statycznej takich jak `DataTypes` zawierających te `T1, T2, T3, ...` typów. W przeciwnym razie błąd mówi, że odwołanie do typu T w zestawie A został znaleziony, ale nie można znaleźć typu w tym zestawie. Jeśli ten błąd pojawia się, sprawdź, czy wszystkie Twoje podtypy jest osiągalna z dostawcy typów. Uwaga: Te `T1, T2, T3...` typy są określane jako *na bieżąco* typów. Pamiętaj, aby umieścić je w dostępny obszar nazw lub typ nadrzędny.
<br />

- `Limitations of the Type Provider Mechanism`
<br />  Mechanizm dostawcy typów F # ma następujące ograniczenia:
<br />
  - Podstawowa architektura dla dostawców typów w języku F # nie obsługuje pod warunkiem ogólne typy lub podać metody ogólne.
<br />

  - Mechanizm nie obsługuje zagnieżdżonych typów z parametrów statycznych.
<br />

- `Limitations of the ProvidedTypes Support Code`
<br />  `ProvidedTypes` Kod obsługi ma następujące reguły i ograniczenia:
<br />
  1. Podana właściwości z ustawiających i pobierających indeksowane nie są zaimplementowane.
<br />

  2. Podana zdarzeń nie jest zaimplementowana.
<br />

  3. Podane typy i obiekty informacji powinny być używane tylko w przypadku mechanizm dostawcy typów F #. Nie są ogólnie można używać jako obiekty System.Type.
<br />

  4. Konstrukcji, których można użyć w cudzysłowach, które definiują implementacje metod ma kilka ograniczeń. Może się odwoływać do kodu źródłowego ProvidedTypes-*wersji* aby zobaczyć, które konstrukcje są obsługiwane w cudzysłowach.
<br />

- `Type providers must generate output assemblies that are .dll files, not .exe files.`
<br />


## <a name="development-tips"></a>Porady dotyczące projektowania
Poniższe porady mogą przyda podczas procesu projektowania.


- `Run Two Instances of Visual Studio.`Mogą tworzyć dostawca typów w jednym wystąpieniu i test dostawcy w innym, ponieważ testów IDE zajmie blokady na plik .dll, który uniemożliwia typ dostawcy zostanie odbudowany. W związku z tym należy zamknąć drugie wystąpienie programu Visual Studio, gdy dostawca jest wbudowana w pierwszej kolejności, a następnie po utworzeniu dostawcy musi Otwórz drugie wystąpienie.
<br />

- `Debug type providers by using invocations of fsc.exe.`Dostawcy typów można wywołać za pomocą następujących narzędzi:
<br />
  - FSC.exe (F # wiersza polecenia kompilatora)
<br />

  - fsi.exe (kompilator F # Interactive)
<br />

  - Devenv.exe (Visual Studio)
<br />

  Dostawcy typów można debugować często najłatwiej przy użyciu fsc.exe w pliku skryptu testu (na przykład script.fsx). Można uruchomić debugera z wiersza polecenia.
<br />

```
  devenv /debugexe fsc.exe script.fsx
```

  Możesz użyć rejestrowania drukowania do stdout.
<br />


## <a name="see-also"></a>Zobacz też
[Dostawcy typów](index.md)
