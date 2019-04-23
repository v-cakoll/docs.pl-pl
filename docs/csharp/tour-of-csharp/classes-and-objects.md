---
title: Klasy i obiekty w C# — Przewodnik po przykładzie C# języka
description: Jesteś nowym użytkownikiem C#? Przeczytaj omówienie klas, obiektów i dziedziczenie
ms.date: 08/10/2016
ms.assetid: 63a89bde-0f05-4bc4-b0cd-4f693854f0cd
ms.openlocfilehash: 36def74888f67dfa216cea7c093d80724e452c7b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59976407"
---
# <a name="classes-and-objects"></a>Klasy i obiekty

*Klasy* są zasadnicze znaczenie dla C#firmy typów. Klasa jest strukturą danych, która łączy stanu (pola) i akcje (metody i innych funkcji elementów członkowskich) w pojedynczą jednostkę. Klasa zawiera definicję dla tworzone dynamicznie *wystąpień* klasy, nazywana również *obiektów*. Klasy obsługi *dziedziczenia* i *polimorfizm*, mechanizmów zgodnie z którą *klasy pochodne* pozwalają rozszerzyć i specjalizują się *klasbazowych*.

Nowe klasy są tworzone za pomocą deklaracji klasy. Deklaracja klasy rozpoczyna się od nagłówka, określający, atrybuty i modyfikatorów klasy, nazwa klasy, klasy podstawowej (jeśli) i interfejsy implementowane przez klasy. Nagłówek następuje treści klasy, która składa się z listy deklaracji elementu członkowskiego zapisywane między ogranicznikami `{` i `}`.

Poniżej przedstawiono deklarację klasie proste o nazwie `Point`:

[!code-csharp[PointClass](~/samples/snippets/csharp/tour/classes-and-objects/Point.cs#L3-L11)]

Wystąpienia klas są tworzone przy użyciu `new` operatora, który przydziela pamięć dla nowego wystąpienia, wywołuje konstruktor do inicjowania wystąpienia i zwraca odwołanie do wystąpienia. Poniższe instrukcje utworzenie dwóch obiektów punktów i przechowuje odwołania do tych obiektów w dwóch zmiennych:

[!code-csharp[PointExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L9-L10)]

Pamięć zajęta przez obiekt jest automatycznie odzyskana, gdy obiekt nie jest już dostępny. Go nie ma potrzeby ani można jawnie cofnięcie przydziału obiektów w języku C#.

## <a name="members"></a>Elementy członkowskie

Elementy członkowskie klasy są statyczne elementy Członkowskie lub elementy członkowskie wystąpień. Statyczne elementy członkowskie należą do klas i składowych wystąpienia należą do obiektów (wystąpienia klasy).

Poniżej omówiono rodzajów elementów członkowskich, który może zawierać klasę.

* Stałe
  - Skojarzony z klasą wartości stałych
* Pola
  - Zmienne klasy
* Metody
  - Obliczeń i akcji, które mogą być wykonywane przez klasę
* Właściwości
  - Akcje skojarzone z odczytywaniem i zapisywaniem nazwane właściwości klasy
* Indeksatory
  - Akcje skojarzone z indeksowania wystąpienia klasy, jak tablica
* Zdarzenia
  - Powiadomienia, które mogą być generowane przez klasę
* Operatory
  - Konwersje i operatory wyrażeń obsługiwany przez klasę
* Konstruktorów
  - Działania wymagane w celu zainicjowania wystąpienia klasy lub samej klasy
* Finalizatory
  - Akcje do wykonania przed wystąpienia klasy stałe są odrzucane.
* Types
  - Zagnieżdżone typy zadeklarowane w klasie

## <a name="accessibility"></a>Ułatwienia dostępu

Każdy członek klasy ma skojarzone ułatwień dostępu, który kontroluje regionach tekst programu, które mogą uzyskiwać dostęp do elementu członkowskiego do. Istnieje sześć możliwe formy ułatwień dostępu. Ich podsumowanie można znaleźć poniżej.

* `public`
  - Nie ograniczając dostęp
* `protected`
  - Dostęp ograniczony do tej klasy lub klas pochodzących z tej klasy
* `internal`
  - Dostęp ograniczony do bieżącego zestawu (.exe, .dll, itp.)
* `protected internal`
  - Dostęp ograniczony do klasy, klasy pochodne klasy zawierającej lub klas w obrębie tego samego zestawu zawierającego
* `private`
  - Dostęp ograniczony do klasy
* `private protected`
  - Dostęp ograniczony do klasy lub klas zawierającego pochodzi od typu zawierającego w obrębie tego samego zestawu

## <a name="type-parameters"></a>Parametry typu

Definicja klasy mogą określać zestaw parametrów typu wykonując nazwę klasy za pomocą nawias ostry otaczający listę nazwy parametrów typu. Następnie można użyć parametrów typu w treści deklaracji klasy do definiowania elementów członkowskich klasy. W poniższym przykładzie parametry typu `Pair` są `TFirst` i `TSecond`:

[!code-csharp[Pair](~/samples/snippets/csharp/tour/classes-and-objects/Pair.cs#L3-L7)]

Nosi nazwę typu klasy, która jest zadeklarowana, aby przyjmują parametry typu *typu klasy ogólnej*. Ogólny może być również typy struktury, interfejsów i delegatów.
W przypadku klasy ogólnej argumentów typu należy określić dla każdego z parametrów typu:

[!code-csharp[PairExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L15-L17)]

Typ ogólny z argumentami typu pod warunkiem, takie jak `Pair<int,string>` powyżej, jest nazywany *skonstruowany typ*.

## <a name="base-classes"></a>Klas podstawowych

Deklaracji klasy może określać klasy bazowej, postępując zgodnie z parametrów nazwy i typu klasy, dwukropek i nazwą klasy bazowej. Pominięcie specyfikacji klasy bazowej jest taka sama jak pochodząca z typu `object`. W poniższym przykładzie klasa bazowa `Point3D` jest `Point`i klasę bazową `Point` jest `object`:

[!code-csharp[Point3DClass](~/samples/snippets/csharp/tour/classes-and-objects/Point.cs#L3-L20)]

Klasa dziedziczy członków klasy podstawowej. Dziedziczenie oznacza, że klasa niejawnie zawiera wszystkie elementy członkowskie klasy podstawowej, z wyjątkiem wystąpienia i konstruktorów statycznych i finalizatory klasy bazowej. Klasy pochodne mogą dodawać nowych członków do tych, które dziedziczy, ale go nie można usunąć definicji dziedziczonego członka. W poprzednim przykładzie `Point3D` dziedziczy `x` i `y` pola z `Point`, a następnie co `Point3D` wystąpienie zawiera trzy pola `x`, `y`, i `z`.

Istnieje niejawna konwersja z typu klasy dowolny z jej typów klasy bazowej. W związku z tym zmienna typu klasy mogą odwoływać się do wystąpienia tej klasy lub wystąpienia klasy pochodnej. Na przykład, biorąc pod uwagę poprzedniej deklaracji klasy, zmienna typu `Point` może odwoływać się albo `Point` lub `Point3D`:

[!code-csharp[Point3DExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L22-L23)]

## <a name="fields"></a>Pola

A *pola* to zmienna, która jest skojarzona z klasą lub przy użyciu wystąpienia klasy.

Pole zadeklarowane za pomocą modyfikator static — definiuje pole statyczne. Pole statyczne identyfikuje dokładnie jednej lokalizacji magazynu. Niezależnie od tego, jak wiele wystąpień klasy są tworzone istnieje tylko kiedykolwiek jedną kopię pole statyczne.

Pole zadeklarowana bez modyfikator static — definiuje pola wystąpienia. Każde wystąpienie klasy zawiera osobną kopię wszystkie pola wystąpienia tej klasy.

W poniższym przykładzie, każde wystąpienie `Color` klasa ma osobną kopię `r`, `g`, i `b` wystąpienia pól, ale istnieje tylko jedna kopia `Black`, `White`, `Red`, `Green`, i `Blue` pola statyczne:

[!code-csharp[ColorClass](~/samples/snippets/csharp/tour/classes-and-objects/Color.cs#L3-L17)]

Jak pokazano w poprzednim przykładzie *pola tylko do odczytu* może być zadeklarowana z `readonly` modyfikator. Przypisanie do `readonly` pola mogą występować wyłącznie jako część deklaracji pola lub za pomocą konstruktora w tej samej klasy.

## <a name="methods"></a>Metody

A *metoda* jest elementem członkowskim, który implementuje obliczenia lub akcji, które mogą być wykonywane przez obiekt lub klasa. *Metody statyczne* są dostępne za pośrednictwem klasy. *Wystąpienie metody* są dostępne za pośrednictwem wystąpienia klasy.

Metody może mieć listę *parametry*, które reprezentują wartości i odwołań do zmiennych przekazywany do metody i *zwracany typ*, określający typ wartości, obliczana i zwracany przez metodę. Typ zwracany metody jest `void` Jeśli nie zwraca wartości.

Podobnie jak typy metody mogą również mieć zestaw parametrów typu, dla których należy określić argumenty typu, gdy wywoływana jest metoda. W przeciwieństwie do typów argumentów typu często można wywnioskować z argumentów wywołania metody i nie jest jawnie konieczne.

*Podpisu* metody muszą być unikatowe w klasie, w którym zadeklarowany jest metoda. Podpis metody zawiera nazwę metody, liczba parametrów typu i liczby, Modyfikatory i typy parametrów. Podpis metody nie ma typ zwracany.

### <a name="parameters"></a>Parametry

Parametry są używane do przekazywania wartości lub odwołania zmiennej do metody. Parametry metody uzyskać wartości rzeczywiste z *argumenty* które są określone, gdy metoda jest wywoływana. Istnieją cztery rodzaje parametrów: wartości parametrów, parametrów w formie odwołań, parametry wyjściowe i tablice parametrów.

A *wartość parametru* służy do przekazywania argumentów wejściowych. Wartość parametru odnosi się do zmiennej lokalnej, która pobiera jej wartość początkową z argumentem, która została przekazana dla parametru. Modyfikacje parametr wartości nie wpływają na argumentu, która została przekazana dla parametru.

Wartości parametrów można opcjonalnie, określając wartość domyślną, dzięki czemu można pominąć odpowiednie argumenty.

A *odwołać się do parametru* służy do przekazywania argumentów przez odwołanie. Argument przekazana dla parametru odwołania musi być zmienną o określonej wartości, a w czasie wykonywania metody parametr odniesienia reprezentuje tę samą lokalizację magazynu zmiennej argumentu. Parametr przekazany przez odwołanie jest zadeklarowana za pomocą `ref` modyfikator. Poniższy przykład pokazuje użycie `ref` parametrów.

[!code-csharp[swapExample](~/samples/snippets/csharp/tour/classes-and-objects/RefExample.cs#L3-L18)]

*Parametr wyjściowy* służy do przekazywania argumentów przez odwołanie. Jest on podobny do parametru odwołania, chyba że jawnie przypisać wartość do argumentu dostarczane przez obiekt wywołujący nie wymaga. Parametr wyjściowy jest zadeklarowana za pomocą `out` modyfikator. Poniższy przykład pokazuje użycie `out` parametrów przy użyciu składni, wprowadzona w C# 7.

[!code-csharp[OutExample](~/samples/snippets/csharp/tour/classes-and-objects/OutExample.cs#L3-L17)]

A *tablicy parametrów* zezwala na zmienną liczbę argumentów, które zostaną przekazane do metody. Tablica parametrów jest zadeklarowana za pomocą `params` modyfikator. Ostatni parametr metody może być tablicą parametrów i typ tablicy parametrów musi być typem tablicy jednowymiarowej. Metody zapisu i WriteLine <xref:System.Console?displayProperty=nameWithType> klasy są dobrym przykładem użycia tablicy parametrów. Są deklarowane w następujący sposób.

[!code-csharp[ConsoleExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L78-L83)]

W metodzie, która korzysta z tablicy parametrów Tablica parametrów zachowuje się tak samo jak parametru regularnego typu tablicowego. Jednak w wywołaniu metody z tablicą parametrów, istnieje możliwość przekazania pojedynczy argument typu tablicy parametrów albo dowolnej liczby argumentów typu elementu tablicy parametrów. W tym ostatnim przypadku wystąpienie tablicy jest automatycznie tworzone i inicjowane z danego argumentów. W tym przykładzie

[!code-csharp[StringFormat](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L55-L55)]

jest odpowiednikiem pisania poniżej.

[!code-csharp[StringFormat2](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L30-L35)]

### <a name="method-body-and-local-variables"></a>Treść metody i zmienne lokalne

Treść metody określa instrukcji do wykonania, gdy metoda jest wywoływana.

Treść metody można zadeklarować zmienne, które są specyficzne dla wywołania metody. Tych zmiennych są nazywane *zmienne lokalne*. Deklaracji zmiennej lokalnej Określa nazwę typu, nazwa zmiennej i prawdopodobnie wartość początkową. Poniższy przykład deklaruje zmienną lokalną `i` o wartości początkowej zero i zmienna lokalna `j` bez wartości początkowej.

[!code-csharp[Squares](~/samples/snippets/csharp/tour/classes-and-objects/Squares.cs#L3-L17)]

Język C# wymaga lokalnej zmiennej jako *zdecydowanie przypisywany* przed jej wartość można uzyskać. Na przykład jeśli deklaracja poprzedniego `i` nie zawiera wartości początkowej, kompilator może zgłosić błąd do późniejszego użycia `i` ponieważ `i` nie może zostać zdecydowanie przypisany w tych punktach w programie.

Można użyć metody `return` instrukcje, aby zwrócić sterowanie do obiektu wywołującego. W metodzie, zwracając `void`, `return` instrukcji nie można określić wyrażenie. W metodzie, zwracając niż void `return` instrukcje mogą zawierać wyrażenie, które oblicza wartość zwracaną.

### <a name="static-and-instance-methods"></a>Metody statyczne i wystąpienia

Metoda zadeklarowane za pomocą modyfikator statyczny jest *statycznej metody*. Metoda statyczna nie będzie działać na określonym wystąpieniu i można uzyskać tylko bezpośredni dostęp do statycznych elementów członkowskich.

Metoda zadeklarowana bez modyfikator statyczny jest *metodę wystąpienia*. Metoda wystąpienia działa na określonym wystąpieniu i można dostęp do statycznych i wystąpieniami elementów członkowskich. Wystąpienia, na której wywołano metodę wystąpienia, które może być jawnie dostępna jako `this`. Jest to błąd do odwoływania się do `this` w metodzie statycznej.

Następujące `Entity` klasa ma statycznych i elementów członkowskich wystąpienia.

[!code-csharp[Entity](~/samples/snippets/csharp/tour/classes-and-objects/Entity.cs#L16-L36)]

Każdy `Entity` wystąpienie zawiera numer seryjny (i prawdopodobnie niektóre inne informacje, które nie został tutaj pokazany). `Entity` Konstruktora (co przypomina metodą wystąpienia) inicjuje nowe wystąpienie następny dostępny numer seryjny. Ponieważ Konstruktor nie jest składową wystąpienia, jest dozwolony dostęp zarówno do `serialNo` pola wystąpienia i `nextSerialNo` pole statyczne.

`GetNextSerialNo` i `SetNextSerialNo` mogą uzyskiwać dostęp do metod statycznych `nextSerialNo` pole statyczne, ale będzie błąd dla nich bezpośredni dostęp `serialNo` pole wystąpienia.

Poniższy przykład pokazuje użycie klasy jednostki.

[!code-csharp[EntityExample](~/samples/snippets/csharp/tour/classes-and-objects/Entity.cs#L3-L15)]

Należy pamiętać, że `SetNextSerialNo` i `GetNextSerialNo` są wywoływane metody statyczne klasy, natomiast `GetSerialNo` metoda wystąpienia jest wywoływane na wystąpienia klasy.

### <a name="virtual-override-and-abstract-methods"></a>Wirtualne zastąpienia i metody abstrakcyjne

Po deklaracji metody wystąpienia obejmuje `virtual` modyfikator, metoda jest nazywany *metodę wirtualną*. Nie modyfikator wirtualnego jest obecny, metoda jest określane jako *metody niewirtualnej*.

Po wywołaniu metody wirtualnej *typu run-time* wystąpienia, dla którego tego wywołania ma miejsce określa rzeczywista implementacja metody do wywołania. W wywołaniu metody niewirtualnej *typów w czasie kompilacji* wystąpienia jest czynnikiem decydującym.

Metoda wirtualna może być *zastąpione* w klasie pochodnej. W przypadku wystąpienia deklaracji metody zawiera modyfikator zastąpienie, metoda zastępuje dziedziczoną metodę wirtualną z tym samym podpisie. Dlatego deklaracja metody wirtualnej wprowadzono nowe metody, deklaracji metody zastąpienie specjalizuje się istniejących dziedziczoną metodę wirtualną, podając nową metodę implementacji tej metody.

*Metody abstrakcyjnej* jest metodą wirtualną bez wdrażania. Metody abstrakcyjnej jest zadeklarowany za pomocą modyfikatora abstrakcyjnej i jest dozwolona tylko w klasie, która także jest zadeklarowany jako abstrakcyjny. Metoda abstrakcyjna musi zostać zastąpiona w każdym nieabstrakcyjnej klasie pochodnej.

Poniższy przykład deklaruje klasę abstrakcyjną, `Expression`, który reprezentuje węzeł drzewa wyrażeń i trzy klasy, pochodne `Constant`, `VariableReference`, i `Operation`, który implementuje węzły drzewa wyrażeń stałych zmiennych odwołania, a operacje arytmetyczne. (Jest to podobne, ale nie należy mylić z typami drzewa wyrażenia).

[!code-csharp[ExpressionClass](~/samples/snippets/csharp/tour/classes-and-objects/Expressions.cs#L3-L61)]

Poprzednie cztery klasy może służyć do modelowania wyrażeniach arytmetycznych. Na przykład za pomocą wystąpień tych klas, wyrażenie `x + 3` mogą być reprezentowane w następujący sposób.

[!code-csharp[ExpressionExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L40-L43)]

`Evaluate` Metody `Expression` wystąpienia jest wywoływane w celu oceny danemu wyrażeniu i generować `double` wartość. Ta metoda przyjmuje `Dictionary` argument, który zawiera nazwy zmiennych (jako klucze, wpisy) i wartości (jako wartości wpisów). Ponieważ `Evaluate` jest metoda abstrakcyjna, klasy pochodne klasy nieabstrakcyjnej `Expression` przesłonięcie `Evaluate`.

A `Constant`przez implementację `Evaluate` po prostu zwraca przechowywaną stała. A `VariableReference`jego implementacja wyszukuje nazwę zmiennej w słowniku i zwraca wartość wynikową. `Operation`w implementacji najpierw ocenia operandy lewy i prawy (cyklicznie, wywołanie ich `Evaluate` metod), a następnie wykonuje danej operacji arytmetycznej.

Następujący program używa `Expression` klasy można oszacować wyrażenia `x * (y + 2)` zależności od wartości `x` i `y`.

[!code-csharp[ExpressionUsage](~/samples/snippets/csharp/tour/classes-and-objects/Expressions.cs#L66-L89)]

### <a name="method-overloading"></a>Przeciążenie metody

Metoda *przeciążenie* zezwala na wiele sposobów w tej samej klasie w celu mają taką samą nazwę, tak długo, jak długo mają unikatowe podpisów. Podczas kompilowania wywołanie metody przeciążonej, kompilator używa *Rozpoznanie przeciążenia* ustalenie określonej metody do wywołania. Rozpoznanie przeciążenia umożliwia znalezienie jednej metody, najlepiej odpowiada argumenty lub zgłasza błąd, jeśli można znaleźć nie pojedyncze najlepsze dopasowanie. Poniższy kod przedstawia obowiązuje przeciążeniu rozdzielczości. Komentarz dla każdego wywołania w `UsageExample` metoda ma pokazać, jakiej metody faktycznie jest wywoływana.

[!code-csharp[OverloadUsage](~/samples/snippets/csharp/tour/classes-and-objects/Overloading.cs#L3-L41)]

Jak pokazano na przykładzie, zawsze można wybrać określoną metodę przez jawne rzutowanie argumentów do typów parametru dokładne i/lub jawnie podanie argumentów typu.

## <a name="other-function-members"></a>Inni członkowie — funkcja

Elementy członkowskie, które zawierają kod wykonywalny są nazywane zbiorczo *funkcji elementów członkowskich* klasy. W poprzedniej sekcji opisano metody, które są podstawowym typem funkcji elementów członkowskich. W tej sekcji opisano inne rodzaje elementów członkowskich funkcji obsługiwanych przez C#: konstruktory, właściwości, indeksatory, zdarzenia, operatorów i finalizatorów.

Poniżej pokazano klasę ogólną o nazwie `MyList<T>`, który implementuje growable listy obiektów. Klasa zawiera kilka przykładów typowych rodzajów funkcji elementów członkowskich.

> [!NOTE]
> Ten przykład tworzy `MyList` klasy, która nie jest taka sama jak .NET standard <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>. Przedstawiają pojęcia są potrzebne w tym samouczku, ale nie zastępuje tej klasy.

[!code-csharp[ListClass](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L4-L89)]

### <a name="constructors"></a>Konstruktorów

C# obsługuje zarówno wystąpienia i konstruktorów statycznych. *Konstruktora wystąpienia* jest elementem członkowskim implementujący działania wymagane w celu zainicjowania wystąpienia klasy. A *statyczny Konstruktor* jest elementem członkowskim, który implementuje działania wymagane w celu zainicjowania samej klasy po pierwszym załadowaniu.

Konstruktor jest zadeklarowany jak metody bez zwrotu typu i taką samą nazwę jak klasa zawierająca. Jeśli deklaracja konstruktora zawiera modyfikator statyczny, deklaruje Konstruktor statyczny. W przeciwnym razie deklaruje konstruktora wystąpień.

Konstruktory wystąpień mogą być przeciążone i może mieć następujące parametry opcjonalne. Na przykład `MyList<T>` klasa deklaruje dwa konstruktory wystąpienia, jedno z bez parametrów, a ta, która przyjmuje `int` parametru. Konstruktory wystąpień są wywoływane przy użyciu `new` operatora. Poniższe instrukcje przydzielić dwie `MyList<string>` wystąpień przy użyciu konstruktora `MyList` klasy z lub bez opcjonalny argument.

[!code-csharp[ListExample1](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L95-L96)]

W przeciwieństwie do innych członków konstruktorów wystąpienia nie są dziedziczone, a klasa nie ma konstruktorów wystąpienia innych niż rzeczywiście zgłoszonymi w klasie. Jeśli żaden konstruktor wystąpienia zostanie podany dla klasy, następnie pustą bez parametrów jest dostarczana automatycznie.

### <a name="properties"></a>Właściwości

*Właściwości* to naturalne rozszerzenie pola. Nazwanych elementów członkowskich skojarzonych typów i składnia do uzyskiwania dostępu do pola i właściwości jest taka sama. Jednak w przeciwieństwie do pola, właściwości określa lokalizacji przechowywania. Właściwości mają *Akcesory* określające instrukcji do wykonania, gdy ich wartości są odczytu lub zapisu.

Właściwość deklarowany jest jak pola, chyba że deklaracja kończy się ona metody dostępu get i/lub metody dostępu set zapisywane między ogranicznikami `{` i `}` zamiast kończy się średnikiem. Właściwość, która ma zarówno metodę dostępu get i SET *odczytu i zapisu właściwości*, właściwość, która ma tylko akcesor pobierania jest *właściwość tylko do odczytu*, i właściwość, która ma tylko akcesor zestawu jest *właściwość tylko do zapisu*.

Akcesor pobierania odnosi się do metody bez parametrów, z wartością zwracaną z typem właściwości. Z wyjątkiem jako element docelowy przypisania, gdy właściwość jest przywoływany w wyrażeniu, metody dostępu get właściwości wywoływana w celu obliczenia wartości właściwości.

Ustawiania odnosi się do metody z pojedynczym parametrem o nazwie wartość i bez zwrotu typu. Gdy właściwość odwołuje się do jako element docelowy przypisania lub argument operacji ++ lub--, metody dostępu set zostanie wywołana z nieprawidłowym argumentem, który zawiera nową wartość.

`MyList<T>` Klasa deklaruje dwie właściwości `Count` i `Capacity`, które są tylko do odczytu i odczytu / zapisu, odpowiednio. Oto przykład użycia tych właściwości:

[!code-csharp[ListExample2](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L101-L104)]

Podobnie jak pola i metody, C# obsługuje zarówno właściwości wystąpienia i właściwości statyczne. Właściwości statyczne są zadeklarowane za pomocą modyfikatora statycznych i właściwości instancji są zadeklarowane bez niego.

Accessor(s) właściwości mogą być wirtualne. Jeśli deklaracja właściwości zawiera `virtual`, `abstract`, lub `override` modyfikator, dotyczy ona accessor(s) właściwości.

### <a name="indexers"></a>Indeksatory

*Indeksatora* jest element członkowski, który umożliwia obiekty, które mają być indeksowane w taki sam sposób, w postaci tablicy. Indeksator deklarowany jest jak właściwości, z tą różnicą, że nazwa elementu członkowskiego to następuje lista parametrów, zapisywane między ogranicznikami `[` i `]`. Parametry są dostępne w accessor(s) indeksatora. Podobnie jak właściwości, indeksatory można odczytu i zapisu, tylko do odczytu i tylko do zapisu, a accessor(s) indeksatora mogą być wirtualne.

`MyList<T>` Klasa deklaruje pojedynczego indeksatora odczytu i zapisu, która przyjmuje `int` parametru. Indeksator umożliwia indeksu `MyList<T>` wystąpień z `int` wartości. Na przykład:

[!code-csharp[ListExample3](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L109-L117)]

Indeksatory mogą być przeciążone, co oznacza, że klasy można zadeklarować wiele indeksatorów, tak długo, jak liczba lub rodzaju ich parametrów różnią się.

### <a name="events"></a>Zdarzenia

*Zdarzeń* jest elementem członkowskim, który umożliwia klasa lub obiekt, do udostępniania powiadomień o. Zdarzenie deklarowany jest jak pola, z tą różnicą, że deklaracja zawiera słowo kluczowe zdarzeń i typ musi być typem delegowanym.

W obrębie klasy, która deklaruje element członkowski zdarzenia zdarzenie zachowuje się tak samo jak pola typu delegata (pod warunkiem zdarzenie nie jest abstrakcyjna i nie deklaruje metody dostępu). Pole zawiera odwołanie do delegata reprezentującego procedury obsługi zdarzeń, które zostały dodane do zdarzenia. Jeśli nie programów obsługi zdarzeń są obecne, pole jest `null`.

`MyList<T>` Klasa deklaruje składową pojedyncze zdarzenie o nazwie `Changed`, co oznacza, że dodano nowy element do listy. Zdarzenie zmieniono zostanie wywołane przez `OnChanged` metody wirtualnej, który po raz pierwszy sprawdza, czy zdarzenie jest `null` (co oznacza, że nie programów obsługi istnieje). Pojęcie podnoszenie zdarzenia odpowiada dokładnie wywoływania delegata reprezentowanej przez zdarzenie — tak więc nie istnieją żadne konstrukcje specjalny język przeznaczony dla podnoszonego zdarzenia.

Klienci reagowania na zdarzenia za pośrednictwem *procedury obsługi zdarzeń*. Programy obsługi zdarzeń dołączonych przy użyciu `+=` operatora i usunięte przy użyciu `-=` operatora. Poniższy przykład dołącza program obsługi zdarzeń do `Changed` zdarzenia `MyList<string>`.

[!code-csharp[EventExample](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L132-L148)]

W przypadku zaawansowanych scenariuszy, w którym pożądane jest formantu powiązanego magazynu zdarzenie, jawnie określić deklaracji zdarzenia `add` i `remove` metod dostępu, które są nieco podobne do `set` metody dostępu właściwości.

### <a name="operators"></a>Operatory

*Operator* jest element członkowski, który definiuje znaczenie zastosowania operatora poszczególnych wyrażeń do wystąpienia klasy. Można zdefiniować trzy rodzaje operatory: jednoargumentowe operatory, operatory binarne i operatory konwersji. Wszystkie operatory musi być zadeklarowany jako `public` i `static`.

`MyList<T>` Klasa deklaruje dwa operatory `operator ==` i `operator !=`i dlatego zapewnia nowe znaczenie wyrażenia, które są stosowane te operatory, aby `MyList` wystąpień. W szczególności operatorów definiowania równości dwóch `MyList<T>` wystąpienia jako porównując każdej zawartych obiektów za pomocą metody Equals. W poniższym przykładzie użyto `==` operatora do porównywania dwóch `MyList<int>` wystąpień.

[!code-csharp[OperatorExample](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L121-L129)]

Pierwszy `Console.WriteLine` generuje `True` ponieważ dwie listy zawiera taką samą liczbę obiektów o tej samej wartości w tej samej kolejności. Gdyby `MyList<T>` Niezdefiniowany `operator ==`, pierwszy `Console.WriteLine` będzie mieć danych wyjściowych `False` ponieważ `a` i `b` odwołanie do innego `MyList<int>` wystąpień.

### <a name="finalizers"></a>Finalizatory

A *finalizator* jest elementem członkowskim, który implementuje działania wymagane w celu sfinalizowania wystąpienia klasy. Finalizatory nie może mieć parametrów, nie mają modyfikatory dostępności i nie można wywołać jawnie. Finalizator dla wystąpienia jest wywoływana automatycznie podczas wyrzucania elementów bezużytecznych.

Moduł odśmiecania pamięci jest dozwolona szerokiego szerokości przy podejmowaniu decyzji, kiedy należy zebrać obiektów i uruchamianie finalizatorów. Czas wywołania finalizatora nie jest jednoznaczny i finalizatory mogą być wykonywane na żadnym z wątków. Dla tych i innych powodów klasy należy zaimplementować finalizatory tylko wtedy, gdy nie inne rozwiązania są niewykonalne.

`using` Instrukcja oferuje lepszym rozwiązaniem do zniszczenia obiektu.

> [!div class="step-by-step"]
> [Poprzednie](statements.md)
> [dalej](structs.md)
