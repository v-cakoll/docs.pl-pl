---
title: "Klas i obiektów w języku C# — samouczek języka C#"
description: "Jesteś nowym użytkownikiem C#? Przeczytaj ten przegląd klas, obiektów i dziedziczenie"
keywords: ".NET, csharp, klasy, wystąpienie, obiekt, dziedziczenia, polimorfizm"
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 63a89bde-0f05-4bc4-b0cd-4f693854f0cd
ms.openlocfilehash: 97559a6e7b24f4a61b49dd4f050747a6d0ccbda0
ms.sourcegitcommit: d95a91d685565f4d95c8773b558752864a6a3d7e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2018
---
# <a name="classes-and-objects"></a>Klasy i obiekty

*Klasy* są najbardziej podstawowe C# dla typów. Klasa jest strukturą danych, łączącą stanu (pól) i akcje (metod i innych funkcji elementów członkowskich) w pojedynczą jednostkę. Klasa zawiera definicję dla tworzone dynamicznie *wystąpień* klasy, nazywany również *obiektów*. Klasy obsługi *dziedziczenia* i *polimorfizm*, mechanizmów zgodnie z którymi *klas pochodnych* można rozszerzyć i dostosować ją *podstawowa klasy*.

Nowe klasy są tworzone za pomocą deklaracji klasy. Deklaracja klasy rozpoczyna się od nagłówek, który określa atrybuty i Modyfikatory klasy, nazwy klasy, klasy podstawowej (jeśli istnieje) i interfejsów implementowanych przez klasę. Nagłówek następuje treści klasy, która składa się z listą deklaracji elementu członkowskiego, zapisane między ograniczniki `{` i `}`.

Poniżej przedstawiono deklaracji prostą klasę o nazwie `Point`:

[!code-csharp[PointClass](../../../samples/snippets/csharp/tour/classes-and-objects/Point.cs#L3-L11)]

Wystąpienia klas są tworzone przy użyciu `new` operatora, który przydziela pamięć dla nowego wystąpienia, wywołuje konstruktor do inicjowania wystąpienia i zwraca odwołanie do wystąpienia. Poniższe instrukcje utworzenie dwóch obiektów punktu i przechowuje odwołania do tych obiektów w dwóch zmiennych:

[!code-csharp[PointExample](../../../samples/snippets/csharp/tour/classes-and-objects/Program.cs#L9-L10)]

Pamięć zajmowane przez obiekt jest automatycznie odzyskana, gdy obiekt nie jest już dostępny. Go nie ma potrzeby ani można jawnie deallocate obiektów w języku C#.

## <a name="members"></a>Elementy członkowskie

Elementy członkowskie klasy są statyczne elementy Członkowskie lub elementy członkowskie wystąpień. Statyczne elementy członkowskie należą do klasy, i elementów członkowskich wystąpienia muszą należeć do obiektów (wystąpienia klasy).

Poniżej omówiono określonych rodzajów członków klasy może zawierać.

* Stałe
    - Wartości stałe skojarzonego z klasą
* Pola
    - Zmienne klasy
* Metody
    - Obliczenia i akcje, które mogą być wykonywane przez klasę
* Właściwości
    - Akcje skojarzone z odczytywanie i zapisywanie właściwości o nazwie klasy
* Indeksatory
    - Akcje skojarzone z indeksowania wystąpień klasy, jak tablicy
* Zdarzenia
    - Powiadomienia, które mogą być generowane przez klasę
* Operatory
    - Konwersje i wyrażenie operatory obsługiwane przez klasę
* Konstruktorów
    - Akcje wymagane do zainicjowania wystąpienia klasy lub samej klasy
* Finalizatory
    - Akcje do wykonania przed wystąpień klasy trwale zostaną odrzucone.
* Types
    - Zagnieżdżone typy zadeklarowane przez klasę

## <a name="accessibility"></a>Ułatwienia dostępu

Każdy element członkowski klasy ma skojarzone ułatwień dostępu, który kontroluje regionów tekst programu, które są w stanie uzyskać dostępu do elementu członkowskiego. Istnieje pięć możliwych form ułatwień dostępu. Te są podsumowywane poniżej.

* `public`
    - Nie ograniczając dostęp
* `protected`
    - Dostęp ograniczony do tej klasy lub klas pochodzących z tej klasy
* `internal`
    - Dostęp ograniczony do bieżącego zestawu (.exe, .dll itp.)
* `protected internal`
    - Dostęp ograniczony do zawierający klasy lub klas pochodnych klasa zawierająca
* `private`
    - Dostęp ograniczony do tej klasy
* `private protected`
    - Dostęp ograniczony do zawierający klasy lub klas pochodnych typu zawierającego w ramach tego samego zestawu

## <a name="type-parameters"></a>Parametry typu

Definicję klasy mogą określać zestaw parametrów typu przez po nazwie klasy z nawiasy otaczającej listę nazw parametrów typu. Następnie można użyć parametrów typu w treści deklaracji klasy można zdefiniować elementów członkowskich klasy. W poniższym przykładzie parametrów typu `Pair` są `TFirst` i `TSecond`:

[!code-csharp[Pair](../../../samples/snippets/csharp/tour/classes-and-objects/Pair.cs#L3-L7)]

Nosi nazwę typu klasy, który jest zadeklarowana, aby wykonać parametrów typu *typu klasy ogólnej*. Można też ogólnego typu struktury, interfejsu i delegata.
W przypadku klasy ogólnej należy podać argumentów typu dla każdego z parametrów typu:

[!code-csharp[PairExample](../../../samples/snippets/csharp/tour/classes-and-objects/Program.cs#L15-L17)]

Typem ogólnym z argumentami typu pod warunkiem, takie jak `Pair<int,string>` powyżej, jest nazywany *skonstruować typu*.

## <a name="base-classes"></a>Klas podstawowych

Deklaracja klasy mogą określać klasy podstawowej przez następujące parametry nazwę i typ klasy z dwukropkiem i nazwy klasy podstawowej. Pominięcie specyfikacji klasa podstawowa jest taka sama jak pochodny typ `object`. W poniższym przykładzie klasa podstawowa `Point3D` jest `Point`, a klasa podstawowa `Point` jest `object`:

[!code-csharp[Point3DClass](../../../samples/snippets/csharp/tour/classes-and-objects/Point.cs#L3-L20)]

Klasa dziedziczy elementów członkowskich klasy podstawowej. Dziedziczenie oznacza, że klasa niejawnie zawiera wszystkie elementy członkowskie w swojej klasie podstawowej, z wyjątkiem wystąpienie i konstruktorów statycznych i finalizatory klasy podstawowej. Klasy pochodne mogą dodawać nowych członków do tych, które dziedziczy, ale nie można usunąć definicji dziedziczonego elementu członkowskiego. W poprzednim przykładzie `Point3D` dziedziczy `x` i `y` pola z `Point`, a następnie co `Point3D` wystąpienie zawiera trzy pola `x`, `y`, i `z`.

Niejawna konwersja istnieje z typem klasy do dowolnego z jego typów klasy podstawowej. W związku z tym zmiennej typu klasy można odwoływać się wystąpienia tej klasy lub wystąpienia klasy pochodnej. Na przykład, dla danego poprzedniej deklaracji klasy, zmiennej typu `Point` może odwoływać się albo `Point` lub `Point3D`:

[!code-csharp[Point3DExample](../../../samples/snippets/csharp/tour/classes-and-objects/Program.cs#L22-L23)]

## <a name="fields"></a>Pola

A *pola* jest zmienna, która jest skojarzona z klasy lub wystąpienia klasy.

Zadeklarowana z modyfikatorem statycznego pola definiuje pola statycznego. Statyczne pole identyfikuje dokładnie jedną lokalizację magazynu. Niezależnie od tego, jak wiele wystąpień klasy są tworzone jest tylko kiedykolwiek jedną kopię pola statycznego.

Pole zadeklarowana bez modyfikator statyczny definiuje pole wystąpienia. Każde wystąpienie klasy zawiera osobną kopię wszystkie pola wystąpienia tej klasy.

W poniższym przykładzie, każde wystąpienie `Color` klasa ma osobną kopię `r`, `g`, i `b` wystąpienia pól, ale istnieje tylko jedna kopia `Black`, `White`, `Red`, `Green`, i `Blue` pola statyczne:

[!code-csharp[ColorClass](../../../samples/snippets/csharp/tour/classes-and-objects/Color.cs#L3-L17)]

Jak pokazano w poprzednim przykładzie *pola tylko do odczytu* mogą być deklarowane z `readonly` modyfikator. Przypisanie do `readonly` pola mogą występować tylko jako część deklaracja pola lub w Konstruktorze w tej samej klasy.

## <a name="methods"></a>Metody

A *metoda* jest elementem członkowskim, który implementuje obliczenia lub akcji, które mogą być wykonywane przez obiekt lub klasa. *Metody statyczne* są dostępne za pośrednictwem klasy. *Wystąpienie metody* są dostępne za pośrednictwem wystąpienia klasy.

Metody może mieć listy *parametry*, które reprezentują wartości lub odwołań do zmiennych przekazywany do metody i *zwracany typ*, który określa typ wartości obliczana i zwracany przez metodę. Zwracany typ metody jest `void` Jeśli nie zwraca wartości.

Jak typy metody może mieć zestaw parametrów typu, dla których należy określić argumenty typu podczas wywoływania metody. W przeciwieństwie do typów argumentów typu często można wywnioskować na podstawie argumenty wywołania metody i nie można jawnie konieczne.

*Podpisu* metody muszą być unikatowe w klasie, w którym zadeklarowany jest metoda. Podpis metody składa się z nazwy metody, liczba parametrów typu i liczbę, Modyfikatory i typy parametrów. Podpis metody nie ma zwracanego typu.

### <a name="parameters"></a>Parametry

Parametry są używane do przekazania wartości lub zmiennej odwołania do metody. Parametry metody get swoje rzeczywiste wartości z *argumenty* podano po wywołaniu metody. Istnieją cztery rodzaje parametry: wartości parametrów, parametry odwołanie parametrów wyjściowych i tablice parametrów.

A *wartość parametru* służy do przekazywania argumentów wejściowych. Wartość parametru odnosi się do zmiennej lokalnej, która pobiera swojej wartości początkowej w argumencie, która została przekazana dla parametru. Modyfikacje parametru wartości nie wpływają na argumentu, która została przekazana dla parametru. 

Wartości parametrów mogą być opcjonalne, przez określenie wartości domyślnej, dzięki czemu można pominąć odpowiednie argumenty.

A *odwołać się do parametru* służy do przekazywania argumentów przez odwołanie. Argumentu przekazanego do parametru odwołania musi być zmienną z określoną wartością, a podczas wykonywania metody, parametr odwołania reprezentuje tej samej lokalizacji magazynu jako argumentu zmiennej. Parametr odwołanie jest zadeklarowane ze `ref` modyfikator. W poniższym przykładzie przedstawiono użycie `ref` parametrów.

[!code-csharp[swapExample](../../../samples/snippets/csharp/tour/classes-and-objects/RefExample.cs#L3-L18)]

*Parametru wyjściowego* służy do przekazywania argumentów przez odwołanie. Jest on podobny do parametru odwołanie, z tą różnicą, że nie wymaga jawnie przypisać wartości do argumentu dostarczane przez obiekt wywołujący. Parametr wyjściowy jest zadeklarowany za pomocą `out` modyfikator. W poniższym przykładzie przedstawiono użycie `out` parametry, używając składni wprowadzono w języku C# 7.

[!code-csharp[OutExample](../../../samples/snippets/csharp/tour/classes-and-objects/OutExample.cs#L3-L17)]

A *tablicy parametrów* pozwala na zmienną liczbę argumentów, które mają być przekazane do metody. Tablica parametrów jest zadeklarowany za pomocą `params` modyfikator. Ostatni parametr metody może być tablicą parametrów, a typ tablicy parametrów musi być typem tablicy jednowymiarowej. Metody zapisu i WriteLine <xref:System.Console?displayProperty=nameWithType> klasy są dobrym przykładem użycia tablicy parametrów. Są one zgłoszone w następujący sposób.

[!code-csharp[ConsoleExample](../../../samples/snippets/csharp/tour/classes-and-objects/Program.cs#L78-L83)]

W ramach metody, która używa tablicy parametrów tablicy parametrów zachowuje się tak samo jak regularne parametru typu tablicowego. Jednak w wywołaniu metody z tablicą parametrów, istnieje możliwość przekazania jeden argument typu Tablica parametru albo dowolną liczbę argumentów typu elementu tablicy parametrów. W drugim przypadku wystąpienia tablicy jest automatycznie tworzone i zainicjować przy użyciu danego argumentów. W tym przykładzie

[!code-csharp[StringFormat](../../../samples/snippets/csharp/tour/classes-and-objects/Program.cs#L55-L55)]

odpowiada to pisanie poniżej.

[!code-csharp[StringFormat2](../../../samples/snippets/csharp/tour/classes-and-objects/Program.cs#L30-L35)]

### <a name="method-body-and-local-variables"></a>Treść metody i zmienne lokalne

Treść metody Określa instrukcje do wykonania, gdy jest wywoływana metoda.

Treść metody mogą zadeklarować zmienne, które są specyficzne dla wywołania metody. Takie zmienne są nazywane *zmiennych lokalnych*. Deklaracji zmiennej lokalnej Określa nazwę typu, nazwę zmiennej, prawdopodobnie wartość początkową. Poniższy przykład deklaruje zmienną lokalną `i` o początkowej wartości zero i zmiennej lokalnej `j` bez wartości początkowej.

[!code-csharp[Squares](../../../samples/snippets/csharp/tour/classes-and-objects/Squares.cs#L3-L17)]

C# wymaga zmiennej lokalnej jako *ostatecznie przypisane* przed jego wartość. Na przykład jeśli deklaracja poprzedniego `i` nie zawiera wartości początkowej, kompilator rozpoczną przesyłanie raportów wystąpił błąd dla kolejnych użycia `i` ponieważ `i` nie będzie można zdecydowanie przypisane w tych punktach w programie.

Można użyć metody `return` instrukcje, aby zwrócić kontrolkę do swojego obiektu wywołującego. W metodach zwracających `void`, `return` instrukcji nie można określić wyrażenie. W metodach zwracających inny niż void `return` instrukcje musi zawierać wyrażenie, które oblicza wartość zwracaną.

### <a name="static-and-instance-methods"></a>Metody statyczne i wystąpienia

Metoda zadeklarowana z modyfikatorem statycznego jest *metody statycznej*. Metody statycznej nie będzie działać na określonym wystąpieniu i tylko bezpośrednio dostęp do statycznych elementów członkowskich.

Metody zadeklarowane bez jest modyfikator statyczny *metody wystąpienia*. Metody wystąpienia działa na określonym wystąpieniu i można dostępu obu statyczna i wystąpienia elementów członkowskich. Wystąpienie, w którym wywołano metodę wystąpienia są jawnie dostępne `this`. Błąd w odwołaniu do `this` w metodzie statycznej.

Następujące `Entity` klasa ma obu statyczna i wystąpienia elementów członkowskich.

[!code-csharp[Entity](../../../samples/snippets/csharp/tour/classes-and-objects/Entity.cs#L16-L36)]

Każdy `Entity` wystąpienie zawiera numery seryjne (i prawdopodobnie niektóre inne informacje, które nie są wyświetlane tutaj). `Entity` — Konstruktor (czyli takie jak metody wystąpienia) inicjuje nowe wystąpienie z najbliższy dostępny numer seryjny. Ponieważ Konstruktor elementu członkowskiego wystąpienia, jest dozwolony dostęp zarówno do `serialNo` pole wystąpienia i `nextSerialNo` pola statycznego.

`GetNextSerialNo` i `SetNextSerialNo` metody statyczne mogą uzyskiwać dostęp do `nextSerialNo` pole statyczne, ale będzie błąd dla nich bezpośrednio `serialNo` pole wystąpienia.

Poniższy przykład przedstawia użycie klasy jednostka.

[!code-csharp[EntityExample](../../../samples/snippets/csharp/tour/classes-and-objects/Entity.cs#L3-L15)]

Należy pamiętać, że `SetNextSerialNo` i `GetNextSerialNo` metody statyczne są wywoływane w klasie, podczas gdy `GetSerialNo` wywołaniu metody wystąpienia na wystąpienia klasy.

### <a name="virtual-override-and-abstract-methods"></a>Wirtualne, zastępowanie i metody abstrakcyjne

Po deklaracji metody wystąpienia obejmuje `virtual` , modyfikator metody jest określany jako *metody wirtualnej*. Nie modyfikatora wirtualnego jest obecny, metoda jest określane jako *Niewirtualna metoda*.

Po wywołaniu metody wirtualnej *typu run-time* wystąpienia, dla którego tego wywołania ma miejsce określa rzeczywista implementacja metody do wywołania. W wywołaniu metody niewirtualne *typu kompilacji* wystąpienia jest czynnikiem decydującym.

Może być metodą wirtualną *przesłonięcia* w klasie pochodnej. Po deklaracji metody wystąpienia zawiera modyfikator zastąpienie, metoda zastępuje dziedziczonej metody wirtualnej o tej samej sygnaturze. Deklaracja metody wirtualnej wprowadza nową metodę, deklaracji metody zastąpienie specjalizuje się istniejących dziedziczonej metody wirtualnej dostarczając nową implementacją tej metody.

*Metody abstrakcyjnej* jest metodą wirtualną z żadnej implementacji. Metoda abstrakcyjna jest zadeklarowany jako abstrakcyjny modyfikatorem i jest dozwolone tylko w klasie, który również został zadeklarowany jako abstrakcyjny. Metoda abstrakcyjna musi zostać zastąpiona w każdej pochodnej klasy nieabstrakcyjnej.

Poniższy przykład deklaruje klasę abstrakcyjną `Expression`, który reprezentuje węzeł drzewa wyrażenia i trzy pochodzi z klasy, `Constant`, `VariableReference`, i `Operation`, który implementuje węzły drzewa wyrażenia stałych i zmiennych odwołania, a operacje arytmetyczne. (To jest podobny, ale nie należy mylić z typami wyrażenia drzewa).

[!code-csharp[ExpressionClass](../../../samples/snippets/csharp/tour/classes-and-objects/Expressions.cs#L3-L61)]

Poprzednie cztery klasy może służyć do modelu w wyrażeniach arytmetycznych. Na przykład za pomocą wystąpień tych klas, wyrażenie `x + 3` można przedstawić w następujący sposób.

[!code-csharp[ExpressionExample](../../../samples/snippets/csharp/tour/classes-and-objects/Program.cs#L40-L43)]

`Evaluate` Metody `Expression` wystąpienia jest wywoływane w celu oceny danego wyrażenia i tworzy `double` wartość. Metoda korzysta z `Dictionary` argumentu, który zawiera wartości (jako wartości wpisy) i nazwy zmiennych (jako klucze wpisy). Ponieważ `Evaluate` jest metoda abstrakcyjna, pochodzi z klasy nieabstrakcyjnej `Expression` przesłonięcie `Evaluate`.

A `Constant`w implementacji `Evaluate` po prostu zwraca przechowywanych stała. A `VariableReference`na implementacji wyszukuje nazwę zmiennej w słowniku i zwraca wartość wynikową. `Operation`w implementacji najpierw ocenia lewy i prawy argumentów operacji (wywołując rekursywnie ich `Evaluate` metody), a następnie wykonuje danej operacji arytmetycznej.

Następujące program używa `Expression` klasy można oszacować wyrażenia `x * (y + 2)` dla różnych wartości `x` i `y`.

[!code-csharp[ExpressionUsage](../../../samples/snippets/csharp/tour/classes-and-objects/Expressions.cs#L66-L89)]

### <a name="method-overloading"></a>Przeciążenie metody

Metoda *przeładowanie* zezwala na wiele metod w tej samej klasy mają taką samą nazwę jak długo mają unikatowe sygnatury. W przypadku kompilowania kodu wywołanie przeciążonej metody, kompilator używa *przeciążenia* ustalenie określonej metody do wywołania. Rozpoznanie przeciążenia znajduje jedną metodę czy najlepiej do argumentów nie pasuje lub zgłasza błąd, jeśli można znaleźć nie pojedynczego najlepsze dopasowanie. W poniższym przykładzie przedstawiono Rozpoznanie przeciążenia obowiązywać. Komentarz dla każdego wywołania w `Main` — metoda zawiera, którego metoda faktycznie jest wywoływany.

[!code-csharp[OverloadUsage](../../../samples/snippets/csharp/tour/classes-and-objects/Overloading.cs#L3-L41)]

Jak to przedstawiono w przykładzie, zawsze można wybrać konkretnej metody przez jawne rzutowanie argumentów do typów parametru dokładne i/lub jawne określenie argumentów typu.

## <a name="other-function-members"></a>O innych elementach członkowskich — funkcja

Elementy członkowskie, które zawierają kod wykonywalny są nazywane zbiorczo *funkcji elementów członkowskich* klasy. Poprzedniej sekcji opisano metody, które są podstawowym typem funkcji elementów członkowskich. W tej sekcji opisano inne rodzaje elementy funkcja obsługiwane w języku C#: konstruktorów, właściwości, indeksatorów, zdarzenia, Operatorzy i finalizatory.

Oto ogólny klasy o nazwie listy<T>, który implementuje growable listy obiektów. Klasa zawiera kilka przykładów typowych rodzajów członków funkcji.

[!code-csharp[ListClass](../../../samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L4-L89)]

### <a name="constructors"></a>Konstruktorów

C# obsługuje zarówno wystąpienia i konstruktorów statycznych. *Konstruktora wystąpienia* jest element członkowski, który implementuje czynności wymagane do zainicjowania wystąpienia klasy. A *Konstruktor statyczny* jest element członkowski, który implementuje czynności wymagane do zainicjowania samej klasy po pierwszym załadowaniu.

Konstruktor jest zadeklarowana jak metody z nie zwracany typ i taką samą nazwę jak klasa zawierająca. Jeśli w deklaracji konstruktora zawiera modyfikator statyczny, deklaruje Konstruktor statyczny. W przeciwnym razie deklaruje być konstruktorem wystąpień.

Konstruktory wystąpień może zostać przeciążony i może mieć następujące parametry opcjonalne. Na przykład `List<T>` klasy deklaruje dwa konstruktory wystąpień z żadnych parametrów i jedną, która przyjmuje `int` parametru. Konstruktory wystąpień są wywoływane przy użyciu `new` operatora. Poniższe instrukcje przydzielić dwie `List<string>` wystąpienia przy użyciu konstruktora `List` klasy z włączonymi i wyłączonymi opcjonalny argument.

[!code-csharp[ListExample1](../../../samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L95-L96)]

W przeciwieństwie do innych członków konstruktory wystąpień nie są dziedziczone, a klasa nie ma konstruktorów wystąpienia innych niż rzeczywiście zgłoszonymi w klasie. Jeśli żaden konstruktor wystąpienia nie jest dostarczony dla klasy, następnie pustą bez parametrów jest teraz udostępniana automatycznie.

### <a name="properties"></a>Właściwości

*Właściwości* są stanowi naturalne rozszerzenie pola. Elementy członkowskie o związane z nimi typy są nazwanych, i składnia do uzyskiwania dostępu do pola i właściwości jest taka sama. Jednak w przeciwieństwie do pola, właściwości oznacza lokalizacji przechowywania. Właściwości mają *akcesorów* określające instrukcje, które ma być wykonywana w przypadku ich wartości są odczytywane lub zapisywane.

Właściwość zadeklarowana takich jak pole, z wyjątkiem, że deklaracja kończy metody dostępu get i/lub metody dostępu set zapisywane między ograniczniki `{` i `}` zamiast kończy się średnikiem. Właściwość, która ma zarówno metodę dostępu get i SET jest *odczytu i zapisu właściwości*, właściwości, która ma metodę dostępu get jest *właściwości tylko do odczytu*, i właściwości, która zawiera tylko metodą dostępu set jest *właściwości tylko do zapisu*.

Metody dostępu get odnosi się do metody bez parametrów, zwracając wartość typu właściwości. Z wyjątkiem jako elementem docelowym przypisania, gdy to wyrażenie odwołuje się do właściwości metody dostępu get właściwości jest wywoływane w celu obliczenia wartości właściwości.

Metodą dostępu set odnosi się do metody z pojedynczym parametrem o nazwie wartość i nie zwracanego typu. Gdy właściwość odwołuje się do jako elementem docelowym przypisania lub argument operacji ++ lub--, metody dostępu set jest wywoływana z argumentem, który udostępnia nową wartość.

`List<T>` Klasy deklaruje dwie właściwości Liczba i pojemności, które są tylko do odczytu i odczytu i zapisu, odpowiednio. Oto przykład korzystanie z tych właściwości.

[!code-csharp[ListExample2](../../../samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L101-L104)]

Podobnie jak pól i metod, C# obsługuje zarówno właściwości wystąpienia i właściwości statycznej. Właściwości statyczne są deklarowane jako statyczne modyfikatorem, a właściwości obiektu są deklarowane jako bez niego.

Accessor(s) właściwości mogą być wirtualne. Po deklaracji właściwości obejmuje `virtual`, `abstract`, lub `override` , modyfikator dotyczy ona accessor(s) właściwości.

### <a name="indexers"></a>Indeksatory

*Indeksatora* jest element członkowski, który umożliwia obiektów do zindeksowania w taki sam sposób jak tablicy. Indeksator zadeklarowano jak właściwości z wyjątkiem, że nazwa elementu członkowskiego jest to następuje listy parametrów zapisywane między ograniczniki `[` i `]`. Parametry są dostępne w accessor(s) indeksatora. Podobnie jak właściwości, indeksatorów mogą być do odczytu / zapisu, tylko do odczytu i tylko do zapisu, a accessor(s) indeksatora mogą być wirtualne.

`List` Klasy deklaruje pojedynczego indeksatora odczytu i zapisu, który przyjmuje `int` parametru. Indeksator umożliwia indeksu `List` wystąpień z `int` wartości. Na przykład:

[!code-csharp[ListExample3](../../../samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L109-L117)]

Można przeciążać indeksatorów, co oznacza klasy można zadeklarować indeksatorów wielu tak długo, jak liczby lub typów ich parametry są różne.

### <a name="events"></a>Zdarzenia

*Zdarzeń* jest element członkowski, który umożliwia klasy lub obiekt, aby zapewnić powiadomienia. Zdarzenie zadeklarowano takich jak pole z tą różnicą, że deklaracja zawiera słowo kluczowe zdarzeń i typ musi być typem obiektu delegowanego.

W obrębie klasy, który deklaruje element członkowski zdarzeń zdarzenie zachowuje się jak pole typu delegata (zakładając, że zdarzenie nie jest abstrakcyjna i nie deklaruje metody dostępu). Pole zawiera odwołanie do delegata, który reprezentuje obsługi zdarzeń, które zostały dodane do zdarzenia. Jeśli istnieją nie obsługi zdarzeń, to pole jest `null`.

`List<T>` Klasy deklaruje element członkowski pojedyncze zdarzenie o nazwie `Changed`, co oznacza, że dodano nowy element do listy. Zmienione zdarzenie zostanie wywołane przez `OnChanged` metody wirtualnej, która najpierw sprawdza, czy zdarzenie `null` (to znaczy czy nie obsługi znajdują się). Pojęcia wywołaniem zdarzenia jest dokładnie odpowiednikiem wywołania delegata reprezentowany przez zdarzenie, w związku z tym nie istnieją żadne specjalne języka konstrukcje wywoływanie zdarzeń.

Klienci reagowania na zdarzenia za pośrednictwem *procedury obsługi zdarzeń*. Programy obsługi zdarzeń są dołączone przy użyciu `+=` operatora i usunięty przy użyciu `-=` operatora. Poniższy przykład dołącza program obsługi zdarzeń do `Changed` zdarzenie `List<string>`.

[!code-csharp[EventExample](../../../samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L132-L148)]

Dla zaawansowanych scenariuszy, w których formant powiązany magazyn zdarzenia jest potrzebne, można jawnie Podaj deklaracji zdarzenia `add` i `remove` metod dostępu, które są nieco podobne do `set` metody dostępu właściwości.

### <a name="operators"></a>Operatory

*Operator* jest element członkowski, który definiuje znaczenie zastosowanie operatora określonego wyrażenia do wystąpienia klasy. Można zdefiniować trzy rodzaje operatory: jednoargumentowe operatory operatorów binarnych i operatory konwersji. Wszystkie operatory musi być zadeklarowany jako `public` i `static`.

`List<T>` Klasy deklaruje dwa operatory `operator ==` i `operator !=`i w związku z tym udostępnia nowe znaczenie wyrażeń, które są stosowane te operatorom `List` wystąpień. W szczególności operatorów Definiowanie równości dwóch `List<T>` wystąpienia jako porównanie każdego zawarte obiekty metodami równości. W poniższym przykładzie użyto `==` operatora, aby porównać dwa `List<int>` wystąpień.

[!code-csharp[OperatorExample](../../../samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L121-L129)]

Pierwszy `Console.WriteLine` generuje `True` ponieważ dwie listy zawierać taką samą liczbę obiektów o tej samej wartości w tej samej kolejności. Ma `List<T>` nie zdefiniowano `operator ==`, pierwszy `Console.WriteLine` będzie mieć output `False` ponieważ `a` i `b` odwołania różnych `List<int>` wystąpień.

### <a name="finalizers"></a>Finalizatory

A *finalizator* jest element członkowski, który implementuje czynności wymagane do zakończenia wystąpienia klasy. Finalizatory nie mogą mieć parametrów, modyfikatory dostępności nie mogą jednak mieć i nie można wywołać bezpośrednio. Finalizator dla wystąpienia jest wywoływana automatycznie podczas wyrzucanie elementów bezużytecznych.

Moduł zbierający elementy bezużyteczne jest dozwolone szerokości szerokości geograficznej w decydowanie o czasie zbierania obiektów i uruchom finalizatory. Czas wywołania finalizatora nie jest deterministyczna i finalizatory mogą być wykonywane w którymkolwiek wątku. Tych i innych przyczyn klasy należy zaimplementować finalizatory tylko wtedy, gdy żadne inne rozwiązania nie są możliwe.

`using` Instrukcji zapewnia lepszym rozwiązaniem do zniszczenia obiektu.

>[!div class="step-by-step"]
[Poprzednie](statements.md)
[dalej](structs.md)
