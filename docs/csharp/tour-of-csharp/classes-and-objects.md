---
title: Klasy i obiekty w języku C# — zwiedzanie języka Języka C#
description: Nowy w C#? Przeczytaj ten przegląd klas, obiektów i dziedziczenia
ms.date: 02/27/2020
ms.assetid: 63a89bde-0f05-4bc4-b0cd-4f693854f0cd
ms.openlocfilehash: c178e11b5667905f75538555c8a309e2fdb4a9ef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78159185"
---
# <a name="classes-and-objects"></a>Klasy i obiekty

*Klasy* są najbardziej podstawowe typy C#. Klasa jest strukturą danych, która łączy stan (pola) i akcje (metody i inne elementy członkowskie funkcji) w jednej jednostce. Klasa zawiera definicję dynamicznie *utworzonych wystąpień* klasy, znanych również jako *obiekty*. Klasy obsługują *dziedziczenie* i *polimorfizm*, mechanizmy, dzięki którym *klasy pochodne* mogą rozszerzać i specjalizować *klasy podstawowe.*

Nowe klasy są tworzone przy użyciu deklaracji klas. Deklaracja klasy rozpoczyna się od nagłówka, który określa atrybuty i modyfikatory klasy, nazwę klasy, klasę podstawową (jeśli podano) i interfejsy implementowane przez klasę. Po nagłówku następuje treść klasy, która składa się z listy deklaracji `{` `}`członkowskich napisanych między ogranicznikami i .

Poniższy kod przedstawia deklarację prostej klasy `Point`o nazwie:

[!code-csharp[PointClass](~/samples/snippets/csharp/tour/classes-and-objects/Point.cs#L3-L11)]

Wystąpienia klas są tworzone przy `new` użyciu operatora, który przydziela pamięć dla nowego wystąpienia, wywołuje konstruktora zainicjować wystąpienie i zwraca odwołanie do wystąpienia. Następujące instrukcje utworzyć dwa Point obiektów i przechowywać odwołania do tych obiektów w dwóch zmiennych:

[!code-csharp[PointExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L9-L10)]

Pamięć zajmowana przez obiekt jest automatycznie odzyskiwana, gdy obiekt nie jest już osiągalny. Nie jest konieczne ani możliwe jawnie calokacji obiektów w języku C#.

## <a name="members"></a>Elementy członkowskie

Członkowie klasy są statycznych elementów członkowskich lub elementów członkowskich wystąpienia. Elementy członkowskie statyczne należą do klas, a elementy członkowskie wystąpienia należą do obiektów (wystąpienia klas).

Poniższa lista zawiera przegląd rodzajów elementów członkowskich, które może zawierać klasa.

- Stałe
  - Stałe wartości skojarzone z klasą
- Pola
  - Zmienne klasy
- Metody
  - Obliczenia i akcje, które mogą być wykonywane przez klasę
- Właściwości
  - Akcje skojarzone z odczytywaniem i zapisywaniem nazwanych właściwości klasy
- Indexers (Indeksatory)
  - Akcje skojarzone z indeksowaniem wystąpień klasy, takich jak tablica
- Zdarzenia
  - Powiadomienia, które mogą być generowane przez klasę
- Operatory
  - Konwersje i operatory wyrażeń obsługiwane przez klasę
- Konstruktorów
  - Akcje wymagane do zainicjowania wystąpień klasy lub samej klasy
- Finalizatory
  - Akcje do wykonania przed wystąpieniem klasy są trwale odrzucane
- Typy
  - Typy zagnieżdżone zadeklarowane przez klasę

## <a name="accessibility"></a>Ułatwienia dostępu

Każdy element członkowski klasy ma skojarzoną dostępność, która kontroluje regiony tekstu programu, który może uzyskać dostęp do elementu członkowskiego. Istnieje sześć możliwych form dostępności. Modyfikatory dostępu są podsumowane poniżej.

- `public`
  - Dostęp nie jest ograniczony.
- `protected`
  - Dostęp jest ograniczony do tej klasy lub klas pochodzących z tej klasy.
- `internal`
  - Dostęp jest ograniczony do bieżącego zestawu (.exe, .dll itd.).
- `protected internal`
  - Dostęp jest ograniczony do klasy zawierającej, klas pochodzących z klasy zawierającej lub klas w ramach tego samego zestawu.
- `private`
  - Dostęp jest ograniczony do tej klasy.
- `private protected`
  - Dostęp jest ograniczony do klasy zawierającej lub klas pochodzących z typu zawierającego w ramach tego samego zestawu.

## <a name="type-parameters"></a>Parametry typu

Definicja klasy może określać zestaw parametrów typu, postępując zgodnie z nazwą klasy z nawiasami kątowymi otaczającymi listę nazw parametrów typu. Parametry typu mogą być następnie używane w treści deklaracji klas do definiowania elementów członkowskich klasy. W poniższym przykładzie parametry typu `Pair` `TFirst` są `TSecond`i:

[!code-csharp[Pair](~/samples/snippets/csharp/tour/classes-and-objects/Pair.cs#L3-L7)]

Typ klasy, który jest zadeklarowany do podjęcia parametrów typu jest nazywany *typem klasy ogólnej*. Typy struktury, interfejsu i delegata mogą być również ogólne.
Gdy używana jest klasa ogólna, argumenty typu muszą być podane dla każdego z parametrów typu:

[!code-csharp[PairExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L15-L17)]

Typ ogólny z podanymi `Pair<int,string>` argumentami typu, jak powyżej, jest nazywany *typem konstruowanym.*

## <a name="base-classes"></a>Klas podstawowych

Deklaracja klasy może określić klasę podstawową, wykonując parametry nazwy klasy i typu z dwukropkiem i nazwą klasy podstawowej. Pominięcie specyfikacji klasy podstawowej jest taka `object`sama jak wynikająca z typu . W poniższym przykładzie klasa `Point3D` podstawowa jest `Point`, `Point` a `object`klasa podstawowa jest:

[!code-csharp[Point3DClass](~/samples/snippets/csharp/tour/classes-and-objects/Point.cs#L3-L20)]

Klasa dziedziczy członków swojej klasy podstawowej. Dziedziczenie oznacza, że klasa niejawnie zawiera wszystkie elementy członkowskie swojej klasy podstawowej, z wyjątkiem wystąpienia i konstruktorów statycznych i finalizatorów klasy podstawowej. Klasa pochodna można dodać nowe elementy członkowskie do tych elementów członkowskich dziedziczy, ale nie można usunąć definicję dziedziczonego elementu członkowskiego. W poprzednim przykładzie `Point3D` dziedziczy `x` pola i `y` z `Point`, a każde `Point3D` wystąpienie zawiera trzy pola, `x`, `y`, i `z`.

Niejawna konwersja istnieje z typu klasy do dowolnego z jego typów klasy podstawowej. Zmienna typu klasy może odwoływać się do wystąpienia tej klasy lub wystąpienia dowolnej klasy pochodnej. Na przykład, biorąc pod uwagę poprzednie deklaracje klasy, zmienna typu `Point` może odwoływać się `Point` `Point3D`do:

[!code-csharp[Point3DExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L22-L23)]

## <a name="fields"></a>Pola

*Pole* jest zmienną skojarzoną z klasą lub wystąpieniem klasy.

Pole zadeklarowane za pomocą modyfikatora statycznego definiuje pole statyczne. Pole statyczne identyfikuje dokładnie jedną lokalizację magazynu. Bez względu na to, ile wystąpień klasy są tworzone, istnieje tylko jedna kopia pola statycznego.

Pole zadeklarowane bez modyfikatora statycznego definiuje pole wystąpienia. Każde wystąpienie klasy zawiera oddzielną kopię wszystkich pól wystąpienia tej klasy.

W poniższym przykładzie każde `Color` wystąpienie klasy ma oddzielną `g`kopię `b` pól `r`, i wystąpienia, ale `Black`istnieje `White` `Red`tylko `Green`jedna `Blue` kopia pól , , , , i statyczne:

[!code-csharp[ColorClass](~/samples/snippets/csharp/tour/classes-and-objects/Color.cs#L3-L17)]

Jak pokazano w poprzednim *przykładzie, pola tylko do odczytu* mogą być deklarowane za pomocą modyfikatora. `readonly` Przypisanie `readonly` do pola może nastąpić tylko jako część deklaracji pola lub w konstruktorze w tej samej klasie.

## <a name="methods"></a>Metody

*Metoda* jest elementem członkowskim, który implementuje obliczeń lub akcji, które mogą być wykonywane przez obiekt lub klasę. *Metody statyczne* są dostępne za pośrednictwem klasy. *Metody wystąpienia* są dostępne za pośrednictwem wystąpień klasy.

Metody mogą mieć listę *parametrów*, które reprezentują wartości lub odwołania zmiennych przekazywane do metody, oraz *typ zwracany*, który określa typ wartości obliczonej i zwróconej przez metodę. Typ zwracany metody `void` jest, jeśli nie zwraca wartość.

Podobnie jak typy, metody mogą mieć również zestaw parametrów typu, dla których argumenty typu muszą być określone, gdy metoda jest wywoływana. W przeciwieństwie do typów argumenty typu często można wywnioskować z argumentów wywołania metody i nie muszą być jawnie podane.

*Podpis* metody musi być unikatowy w klasie, w której metoda jest zadeklarowana. Podpis metody składa się z nazwy metody, liczby parametrów typu i liczby, modyfikatorów i typów jej parametrów. Podpis metody nie zawiera typu zwracanego.

### <a name="parameters"></a>Parametry

Parametry są używane do przekazywania wartości lub zmiennych odniesień do metod. Parametry metody uzyskać ich rzeczywiste wartości z *argumentów,* które są określone podczas wywoływania metody. Istnieją cztery rodzaje parametrów: parametry wartości, parametry odniesienia, parametry wyjściowe i tablice parametrów.

*Parametr wartości* jest używany do przekazywania argumentów wejściowych. Parametr wartości odpowiada zmiennej lokalnej, która pobiera jego wartość początkową z argumentu, który został przekazany dla parametru. Modyfikacje parametru value nie mają wpływu na argument, który został przekazany dla parametru.

Parametry wartości mogą być opcjonalne, określając wartość domyślną, dzięki czemu można pominąć odpowiednie argumenty.

*Parametr referencyjny* jest używany do przekazywania argumentów przez odwołanie. Argument przekazany dla parametru odwołania musi być zmienną o określonej wartości, a podczas wykonywania metody parametr referencyjny reprezentuje tę samą lokalizację magazynu co zmienna argumentu. Parametr referencyjny jest `ref` zadeklarowany za pomocą modyfikatora. W poniższym przykładzie `ref` przedstawiono użycie parametrów.

[!code-csharp[swapExample](~/samples/snippets/csharp/tour/classes-and-objects/RefExample.cs#L3-L18)]

*Parametr wyjściowy* jest używany do przekazywania argumentów przez odwołanie. Jest podobny do parametru odwołania, z tą różnicą, że nie wymaga jawnie przypisać wartość do argumentu dostarczonego przez obiekt wywołujący. Parametr wyjściowy jest zadeklarowany za pomocą modyfikatora. `out` W poniższym przykładzie `out` przedstawiono użycie parametrów przy użyciu składni wprowadzone w języku C# 7.

[!code-csharp[OutExample](~/samples/snippets/csharp/tour/classes-and-objects/OutExample.cs#L3-L17)]

Tablica *parametrów* umożliwia zmienną liczbę argumentów, które mają być przekazywane do metody. Tablica parametrów jest `params` zadeklarowana za pomocą modyfikatora. Tylko ostatni parametr metody może być tablicą parametrów, a typ tablicy parametrów musi być jednowymiarowym typem tablicy. Metody Write i WriteLine <xref:System.Console?displayProperty=nameWithType> klasy są dobrymi przykładami użycia tablicy parametrów. Są one zadeklarowane w następujący sposób.

[!code-csharp[ConsoleExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L78-L83)]

W ramach metody, która używa tablicy parametrów, tablica parametrów zachowuje się dokładnie tak, jak zwykły parametr typu tablicy. Jednak w wywołaniu metody z tablicą parametrów można przekazać pojedynczy argument typu tablicy parametrów lub dowolną liczbę argumentów typu elementu tablicy parametrów. W tym ostatnim przypadku wystąpienie tablicy jest automatycznie tworzone i inicjowane z podanymi argumentami. W tym przykładzie

[!code-csharp[StringFormat](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L55-L55)]

jest odpowiednikiem pisania następujących czynności.

[!code-csharp[StringFormat2](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L30-L35)]

### <a name="method-body-and-local-variables"></a>Treść metody i zmienne lokalne

Treść metody określa instrukcje do wykonania, gdy metoda jest wywoływana.

Treść metody może zadeklarować zmienne, które są specyficzne dla wywołania metody. Takie zmienne są nazywane *zmiennymi lokalnymi*. Deklaracja zmiennej lokalnej określa nazwę typu, nazwę zmiennej i prawdopodobnie wartość początkową. W poniższym przykładzie zadeklarowano zmienną `i` lokalną o `j` wartości początkowej zero i zmiennej lokalnej bez wartości początkowej.

[!code-csharp[Squares](~/samples/snippets/csharp/tour/classes-and-objects/Squares.cs#L3-L17)]

C# wymaga zmiennej *lokalnej,* aby zdecydowanie przypisać przed jego wartość można uzyskać. Na przykład jeśli deklaracja `i` poprzedniego nie zawiera wartości początkowej, kompilator zgłosi `i` błąd `i` dla kolejnych użycia, ponieważ nie będzie zdecydowanie przypisany w tych punktach w programie.

Metoda może `return` używać instrukcji, aby przywrócić kontrolę do obiektu wywołującego. W zwracanej `void`metodzie `return` instrukcje nie mogą określić wyrażenia. W metodzie zwracającej nieunieważnione `return` instrukcje muszą zawierać wyrażenie obliczające wartość zwracaną.

### <a name="static-and-instance-methods"></a>Metody statyczne i instancjowe

Metoda zadeklarowana za pomocą modyfikatora statycznego jest *metodą statyczną.* Metoda statyczna nie działa w określonym wystąpieniu i może uzyskać bezpośredni dostęp tylko do elementów statycznych.

Metoda zadeklarowana bez statycznego modyfikatora jest *metodą instancji*. Metoda wystąpienia działa w określonym wystąpieniu i może uzyskać dostęp zarówno statyczne i wystąpienia elementów członkowskich. Wystąpienie, na którym wywołana została metoda wystąpienia, `this`można jawnie uzyskać dostęp jako . Jest to błąd, do `this` wyniku do niego w metodzie statycznej.

Następująca `Entity` klasa ma elementy członkowskie statyczne i wystąpienia.

[!code-csharp[Entity](~/samples/snippets/csharp/tour/classes-and-objects/Entity.cs#L16-L36)]

Każde `Entity` wystąpienie zawiera numer seryjny (i prawdopodobnie inne informacje, które nie są wyświetlane w tym miejscu). Konstruktor `Entity` (który jest jak metoda wystąpienia) inicjuje nowe wystąpienie z następnego dostępnego numeru seryjnego. Ponieważ konstruktor jest elementem członkowskim wystąpienia, może `serialNo` uzyskać dostęp `nextSerialNo` zarówno do pola wystąpienia, jak i pola statycznego.

Metody `GetNextSerialNo` `SetNextSerialNo` statyczne i statyczne `nextSerialNo` mogą uzyskiwać dostęp do pola statycznego, `serialNo` ale byłoby błędem, aby uzyskać bezpośredni dostęp do pola wystąpienia.

W poniższym przykładzie przedstawiono użycie klasy Entity.

[!code-csharp[EntityExample](~/samples/snippets/csharp/tour/classes-and-objects/Entity.cs#L3-L15)]

Metody `SetNextSerialNo` `GetNextSerialNo` statyczne i statyczne są wywoływane w `GetSerialNo` klasie, podczas gdy metoda wystąpienia jest wywoływana na wystąpieniach klasy.

### <a name="virtual-override-and-abstract-methods"></a>Metody wirtualne, zastępowane i abstrakcyjne

Gdy deklaracja metody `virtual` wystąpienia zawiera modyfikator, metoda jest uważana za *metodę wirtualną*. Gdy nie ma wirtualnego modyfikatora jest obecny, metoda jest uważana za *metodę niewirtualną*.

Gdy metoda wirtualna jest wywoływana, *typ czasu wykonywania* wystąpienia, dla którego odbywa się to wywołanie określa implementację metody rzeczywistej do wywołania. W wywołaniu metody niewirtualnej *typ czasu kompilacji* wystąpienia jest czynnikiem decydującym.

Metoda wirtualna może zostać *zastąpiona* w klasie pochodnej. Gdy deklaracja metody wystąpienia zawiera modyfikator zastępowania, metoda zastępuje dziedziczoną metodę wirtualną o tym samym podpisie. Podczas gdy deklaracja metody wirtualnej wprowadza nową metodę, deklaracja metody zastępowania specjalizuje się w istniejącej dziedziczonej metodzie wirtualnej, zapewniając nową implementację tej metody.

*Metoda abstrakcyjna* jest metodą wirtualną bez implementacji. Metoda abstrakcyjna jest zadeklarowana za pomocą modyfikatora abstrakcyjnego i jest dozwolona tylko w klasie, która jest również zadeklarowana jako abstrakcyjna. Metoda abstrakcyjna musi zostać zastąpiona w każdej nieabstrakcyjnej klasie pochodnej.

W poniższym przykładzie deklaruje `Expression`klasę abstrakcyjną, która reprezentuje węzeł drzewa wyrażeń i trzy klasy pochodne , `Constant`, `VariableReference`i `Operation`, które implementują węzły drzewa wyrażeń dla stałych, odwołań zmiennych i operacji arytmetycznych. (Ten przykład jest podobny do, ale nie należy mylić z typami drzewa wyrażeń).

[!code-csharp[ExpressionClass](~/samples/snippets/csharp/tour/classes-and-objects/Expressions.cs#L3-L61)]

Poprzednie cztery klasy mogą służyć do modelowania wyrażeń arytmetycznych. Na przykład przy użyciu wystąpień tych `x + 3` klas wyrażenie może być reprezentowane w następujący sposób.

[!code-csharp[ExpressionExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L40-L43)]

Metoda `Evaluate` wystąpienia `Expression` jest wywoływana do oceny danego wyrażenia `double` i wygenerować wartość. Metoda przyjmuje `Dictionary` argument, który zawiera nazwy zmiennych (jako klucze wpisów) i wartości (jako wartości wpisów). Ponieważ `Evaluate` jest metodą abstrakcyjną, klasy nieabstrakcyjne pochodzące z `Expression` musi zastąpić `Evaluate`.

Implementacja `Constant` `Evaluate` po prostu zwraca przechowywane stałej. Implementacja `VariableReference`'s wyszbędzie nazwę zmiennej w słowniku i zwraca wynikową wartość. Implementacja `Operation`najpierw ocenia lewe i prawe argumenty (rekurencyjne wywoływanie ich `Evaluate` metod), a następnie wykonuje daną operację arytmetyczną.

Poniższy program używa `Expression` klas do `x * (y + 2)` oceny wyrażenia `x` dla `y`różnych wartości i .

[!code-csharp[ExpressionUsage](~/samples/snippets/csharp/tour/classes-and-objects/Expressions.cs#L66-L89)]

### <a name="method-overloading"></a>Przeciążenie metody

*Przeciążenie* metody pozwala wielu metod w tej samej klasie mają taką samą nazwę, tak długo, jak mają unikatowe podpisy. Podczas kompilowania wywołania przeciążonej metody kompilator używa *rozpoznawania przeciążenia* w celu określenia określonej metody do wywołania. Rozpoznawanie przeciążenia znajduje jedną metodę, która najlepiej pasuje do argumentów lub zgłasza błąd, jeśli nie można znaleźć najlepszego dopasowania. W poniższym przykładzie przedstawiono rozdzielczość przeciążenia w życie. Komentarz dla każdego wywołania `UsageExample` w metodzie pokazuje, która metoda jest wywoływana.

[!code-csharp[OverloadUsage](~/samples/snippets/csharp/tour/classes-and-objects/Overloading.cs#L3-L41)]

Jak pokazano w przykładzie, określonej metody zawsze można wybrać przez jawne rzutowanie argumentów do dokładnych typów parametrów i/lub jawnie podając argumenty typu.

## <a name="other-function-members"></a>Inne elementy członkowskie funkcji

Elementy członkowskie, które zawierają kod wykonywalny są zbiorczo nazywane *członkami funkcji* klasy. W powyższej sekcji opisano metody, które są podstawowymi typami elementów członkowskich funkcji. W tej sekcji opisano inne rodzaje elementów członkowskich funkcji obsługiwanych przez konstruktory C#: właściwości, indeksatory, zdarzenia, operatory i finalizatory.

W poniższym przykładzie przedstawiono `MyList<T>`klasę rodzajową o nazwie , która implementuje rozwijaną listę obiektów. Klasa zawiera kilka przykładów najbardziej typowych rodzajów elementów członkowskich funkcji.

> [!NOTE]
> W tym `MyList` przykładzie tworzy klasę, która nie jest <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>taka sama jak standard .NET . Ilustruje pojęcia potrzebne do tej trasy, ale nie zastępuje tej klasy.

[!code-csharp[ListClass](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L4-L89)]

### <a name="constructors"></a>Konstruktorów

C# obsługuje zarówno wystąpienia i statycznych konstruktorów. *Konstruktor wystąpienia* jest elementem członkowskim, który implementuje akcje wymagane do zainicjowania wystąpienia klasy. *Konstruktora statycznego* jest elementem członkowskim, który implementuje akcje wymagane do zainicjowania samej klasy, gdy jest po raz pierwszy załadowany.

Konstruktor jest zadeklarowany jako metoda bez typu zwracanego i tej samej nazwy co klasa zawierająca. Jeśli deklaracja konstruktora zawiera modyfikator statyczny, deklaruje konstruktora statycznego. W przeciwnym razie deklaruje konstruktora wystąpienia.

Konstruktory wystąpienia mogą być przeciążone i mogą mieć parametry opcjonalne. Na przykład `MyList<T>` klasa deklaruje jeden konstruktor `int` wystąpienia z jednym parametrem opcjonalnym. Konstruktory wystąpienia są `new` wywoływane przy użyciu operatora. Następujące instrukcje przydzielić dwa `MyList<string>` wystąpienia przy `MyList` użyciu konstruktora klasy z i bez argumentu opcjonalnego.

[!code-csharp[ListExample1](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L95-L96)]

W przeciwieństwie do innych elementów członkowskich konstruktory wystąpienia nie są dziedziczone, a klasa nie ma konstruktorów wystąpienia innych niż te konstruktory faktycznie zadeklarowane w klasie. Jeśli nie konstruktora wystąpienia jest dostarczany dla klasy, a następnie pusty jeden bez parametrów jest automatycznie dostarczane.

### <a name="properties"></a>Właściwości

*Właściwości* są naturalnym rozszerzeniem pól. Oba są nazwane elementy członkowskie z skojarzonymi typami, a składnia dostępu do pól i właściwości jest taka sama. Jednak w przeciwieństwie do pól właściwości nie oznaczają lokalizacji magazynu. Zamiast tego właściwości mają *akcesorów,* które określają instrukcje do wykonania, gdy ich wartości są odczytywane lub zapisywane.

Właściwość jest zadeklarowana jako pole, z tą różnicą, że deklaracja kończy się get `{` akcesor i/lub set akcesor napisany między ogranicznikami i `}` zamiast kończyć się średnikiem. Właściwość, która ma zarówno get akcesor i set akcesor jest *właściwością odczytu i zapisu,* właściwość, która ma tylko get akcesor jest *właściwością tylko do odczytu,* a właściwość, która ma tylko set akcesor jest *tylko do zapisu właściwości*.

A get akcesor odpowiada metody bezparametrów z wartością zwracaną typu właściwości. Z wyjątkiem jako miejsce docelowe przypisania, gdy właściwość odwołuje się w wyrażeniu, get akcesor właściwości jest wywoływana w celu obliczenia wartości właściwości.

Set akcesor odpowiada metody z jednego parametru o nazwie wartości i bez zwracanego typu. Gdy właściwość jest wywoływana jako miejsce docelowe przypisania lub jako operand ++ lub --, set akcesor jest wywoływana z argumentem, który zapewnia nową wartość.

Klasa `MyList<T>` deklaruje dwie właściwości `Count` i `Capacity`, które są tylko do odczytu i odczytu i zapisu, odpowiednio. Poniższy kod jest przykładem użycia tych właściwości:

[!code-csharp[ListExample2](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L101-L104)]

Podobnie jak pola i metody C# obsługuje zarówno właściwości wystąpienia, jak i właściwości statyczne. Właściwości statyczne są deklarowane za pomocą modyfikatora statycznego, a właściwości wystąpienia są deklarowane bez niego.

Akcesor(y) właściwości może być wirtualny. Gdy deklaracja właściwości `virtual` `abstract`zawiera `override` , lub modyfikator, ma zastosowanie do akcesor(-ów) właściwości.

### <a name="indexers"></a>Indexers (Indeksatory)

*Indeksator* jest elementem członkowskim, który umożliwia obiekty do indeksowania w taki sam sposób jak tablicy. Indeksator jest zadeklarowany jako właściwość, z `this` tą różnicą, że po nazwie `[` `]`elementu członkowskiego następuje lista parametrów zapisana między ogranicznikami i . Parametry są dostępne w akcesor(-ach) indeksatora. Podobnie jak właściwości indeksatory mogą być odczytu i zapisu, tylko do odczytu i tylko do zapisu, a akcesor (s) indeksatora może być wirtualny.

Klasa `MyList<T>` deklaruje jeden indeksator odczytu i `int` zapisu, który przyjmuje parametr. Indeksator umożliwia indeksowanie `MyList<T>` wystąpień `int` z wartościami. Przykład:

[!code-csharp[ListExample3](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L109-L117)]

Indeksatory mogą być przeciążone, co oznacza, że klasa może zadeklarować wiele indeksatorów, o ile różnią się liczby lub typów ich parametrów.

### <a name="events"></a>Zdarzenia

*Zdarzenie* jest elementem członkowskim, który umożliwia klasy lub obiektu do dostarczania powiadomień. Zdarzenie jest zadeklarowane jako pole, z tą różnicą, że deklaracja zawiera słowo kluczowe zdarzenia, a typ musi być typem delegata.

W ramach klasy, która deklaruje element członkowski zdarzenia, zdarzenie zachowuje się jak pole typu delegata (pod warunkiem, że zdarzenie nie jest abstrakcyjne i nie deklaruje akcesorów). Pole przechowuje odwołanie do pełnomocnika, który reprezentuje programy obsługi zdarzeń, które zostały dodane do zdarzenia. Jeśli nie występują żadne programy obsługi `null`zdarzeń, pole to jest .

Klasa `MyList<T>` deklaruje jeden element członkowski zdarzenia o nazwie `Changed`, co wskazuje, że nowy element został dodany do listy. Changed Zdarzenie jest wywoływane przez metodę wirtualną, `OnChanged` `null` która najpierw sprawdza, czy zdarzenie jest (co oznacza, że nie są dostępne programy obsługi). Pojęcie wywoływania zdarzenia jest dokładnie równoważne wywołanie delegata reprezentowanego przez zdarzenie — w związku z tym nie ma żadnych specjalnych konstrukcji języka do wywoływania zdarzeń.

Klienci reagują na zdarzenia za pomocą *programów obsługi zdarzeń*. Programy obsługi zdarzeń `+=` są dołączone za `-=` pomocą operatora i usunięte za pomocą operatora. Poniższy przykład dołącza program obsługi `Changed` zdarzeń `MyList<string>`do zdarzenia .

[!code-csharp[EventExample](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L132-L148)]

W przypadku zaawansowanych scenariuszy, w których kontrola podstawowego magazynu zdarzenia `add` jest `remove` pożądane, deklaracja zdarzenia `set` może jawnie zapewnić i akcesorów, które są podobne do akcesora właściwości.

### <a name="operators"></a>Operatory

*Operator* jest elementem członkowskim, który definiuje znaczenie stosowania określonego operatora wyrażenia do wystąpień klasy. Można zdefiniować trzy rodzaje operatorów: operatory nieukładane, operatory binarne i operatory konwersji. Wszystkie podmioty gospodarcze `public` `static`muszą być zadeklarowane jako i .

Klasa `MyList<T>` deklaruje dwa operatory, `operator ==` a `operator !=`tym samym nadaje nowe znaczenie `MyList` wyrażeń, które stosują te operatory do wystąpień. W szczególności operatory zdefiniować `MyList<T>` równość dwóch wystąpień jako porównanie każdego z zawartych obiektów przy użyciu ich Equals metody. W poniższym `==` przykładzie użyto `MyList<int>` operatora do porównania dwóch wystąpień.

[!code-csharp[OperatorExample](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L121-L129)]

Pierwsze `Console.WriteLine` dane `True` wyjściowe, ponieważ dwie listy zawierają taką samą liczbę obiektów o tych samych wartościach w tej samej kolejności. Gdyby `MyList<T>` nie `operator ==` `Console.WriteLine` zdefiniowano, pierwszy `False` `a` miałby dane wyjściowe, ponieważ i `b` odwoływać się do różnych `MyList<int>` wystąpień.

### <a name="finalizers"></a>Finalizatory

*Finalizator* jest elementem członkowskim, który implementuje akcje wymagane do sfinalizowania wystąpienia klasy. Finalizatory nie mogą mieć parametrów, nie mogą mieć modyfikatorów ułatwień dostępu i nie można ich wywołać jawnie. Finalizator dla wystąpienia jest wywoływany automatycznie podczas wyrzucania elementów bezużytecznych.

Moduł zbierający elementy bezużyteczne może szeroki zakres swobody przy podejmowaniu decyzji, kiedy zbierać obiekty i uruchomić finalizatorów. W szczególności czas wywołań finalizatora nie jest deterministyczny i finalizatorów mogą być wykonywane w dowolnym wątku. Z tych i innych powodów klasy należy zaimplementować finalizatorów tylko wtedy, gdy nie inne rozwiązania są możliwe.

Instrukcja `using` zapewnia lepsze podejście do niszczenia obiektów.

> [!div class="step-by-step"]
> [Poprzedni](statements.md)
> [następny](arrays.md)
