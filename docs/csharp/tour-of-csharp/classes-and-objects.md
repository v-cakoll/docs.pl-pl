---
title: Klasy i obiekty w C# przewodniku dotyczące C# języka
description: Jesteś nowym C#? Przeczytaj ten przegląd klas, obiektów i dziedziczenia
ms.date: 08/10/2016
ms.assetid: 63a89bde-0f05-4bc4-b0cd-4f693854f0cd
ms.openlocfilehash: ff83a3198c6c9fb4c4a438d2486614a211c913ec
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971456"
---
# <a name="classes-and-objects"></a>Klasy i obiekty

*Klasy* są najbardziej zasadniczymi C#typami. Klasa jest strukturą danych, która łączy stan (pola) i akcje (metody i inne elementy członkowskie funkcji) w jednej jednostce. Klasa zawiera definicję dla dynamicznie utworzonych *wystąpień* klasy, znanych również jako *obiekty*. Klasy obsługują *dziedziczenie* i *polimorfizm*, natomiast mechanizmy, w których *klasy pochodne* mogą poszerzać i specjalizację *klas bazowych*.

Nowe klasy są tworzone za pomocą deklaracji klasy. Deklaracja klasy rozpoczyna się od nagłówka, który określa atrybuty i Modyfikatory klasy, nazwę klasy, klasę bazową (jeśli ma to zastosowanie) i interfejsy zaimplementowane przez klasę. Po tym nagłówku następuje treść klasy, która składa się z listy deklaracji elementów członkowskich, które są zapisywane między `{` ogranicznikami `}`i.

Poniżej znajduje się deklaracja klasy prostej o nazwie `Point`:

[!code-csharp[PointClass](~/samples/snippets/csharp/tour/classes-and-objects/Point.cs#L3-L11)]

Wystąpienia klas są tworzone przy użyciu `new` operatora, który przydziela pamięć dla nowego wystąpienia, wywołuje konstruktora w celu zainicjowania wystąpienia i zwraca odwołanie do wystąpienia. Poniższe instrukcje tworzą dwa obiekty punktu i przechowują odwołania do tych obiektów w dwóch zmiennych:

[!code-csharp[PointExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L9-L10)]

Pamięć zajęta przez obiekt jest automatycznie odzyskiwana, gdy obiekt nie jest już dostępny. Nie jest to konieczne ani możliwe, aby jawnie cofnąć alokację obiektów w programie C#.

## <a name="members"></a>Elementy członkowskie

Elementy członkowskie klasy są statycznymi elementami członkowskimi lub wystąpieniami. Statyczne składowe należą do klas, a elementy członkowskie wystąpienia należą do obiektów (wystąpień klas).

Poniżej przedstawiono omówienie rodzajów elementów członkowskich, które może zawierać Klasa.

* Stałe
  - Wartości stałe skojarzone z klasą
* Pola
  - Zmienne klasy
* Metody
  - Obliczenia i akcje, które mogą być wykonywane przez klasę
* Właściwości
  - Akcje skojarzone z odczytem i pisaniem nazwanych właściwości klasy
* Indeksatory
  - Akcje skojarzone z wystąpieniami indeksowania klasy, takimi jak tablica
* Zdarzenia
  - Powiadomienia, które mogą zostać wygenerowane przez klasę
* Operatory
  - Konwersje i operatory wyrażeń obsługiwane przez klasę
* Konstruktorów
  - Akcje wymagane do zainicjowania wystąpień klasy lub samej klasy
* Finalizatory
  - Akcje do wykonania przed trwałe odrzuceniem wystąpień klasy
* Types
  - Zagnieżdżone typy zadeklarowane przez klasę

## <a name="accessibility"></a>Ułatwienia dostępu

Każdy element członkowski klasy ma skojarzoną dostępność, która kontroluje regiony tekstu programu, które mogą uzyskać dostęp do elementu członkowskiego. Istnieje sześć możliwych form ułatwień dostępu. Poniżej przedstawiono podsumowanie tych informacji.

* `public`
  - Dostęp nie jest ograniczony
* `protected`
  - Dostęp ograniczony do tej klasy lub klas pochodnych od tej klasy
* `internal`
  - Dostęp ograniczony do bieżącego zestawu (. exe,. dll itp.)
* `protected internal`
  - Dostęp ograniczony do klasy zawierającej, klasy pochodne z klasą zawierającą lub klasy w tym samym zestawie
* `private`
  - Dostęp ograniczony do tej klasy
* `private protected`
  - Dostęp ograniczony do zawierającej klasy lub klas pochodnych z typu zawierającego w tym samym zestawie

## <a name="type-parameters"></a>Parametry typu

Definicja klasy może określać zestaw parametrów typu przez poniższą nazwę klasy z nawiasami kątowymi zawierającymi listę nazw parametrów typu. Parametry typu mogą być następnie używane w treści deklaracji klasy do definiowania elementów członkowskich klasy. W poniższym przykładzie parametry `Pair` typu są `TFirst` i `TSecond`:

[!code-csharp[Pair](~/samples/snippets/csharp/tour/classes-and-objects/Pair.cs#L3-L7)]

Typ klasy zadeklarowanej do wykonania parametrów typu jest nazywany *typem klasy generycznej*. Typy struktur, interfejsów i delegatów mogą być również rodzajowe.
Gdy używana jest Klasa generyczna, należy podać argumenty typu dla każdego z parametrów typu:

[!code-csharp[PairExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L15-L17)]

Typ ogólny z podanymi argumentami typu, `Pair<int,string>` jak powyżej, jest nazywany *typem skonstruowanym*.

## <a name="base-classes"></a>Klas podstawowych

Deklaracja klasy może określać klasę bazową, postępując według nazwy klasy i parametrów typu z dwukropkiem i nazwą klasy bazowej. Pominięcie specyfikacji klasy bazowej jest taka sama jak pochodna typu `object`. `Point3D` W poniższym przykładzie klasą bazową jest `Point`, `Point` a klasą bazową jest `object`:

[!code-csharp[Point3DClass](~/samples/snippets/csharp/tour/classes-and-objects/Point.cs#L3-L20)]

Klasa dziedziczy elementy członkowskie swojej klasy bazowej. Dziedziczenie oznacza, że Klasa niejawnie zawiera wszystkie elementy członkowskie swojej klasy podstawowej, z wyjątkiem dla wystąpienia i konstruktorów statycznych i finalizatorów klasy bazowej. Klasa pochodna może dodawać nowych członków do tych, które dziedziczy, ale nie może usunąć definicji dziedziczonego elementu członkowskiego. W poprzednim przykładzie `Point3D` `x` dziedziczy pola i `y` z `Point`, i każde `Point3D` wystąpienie zawiera trzy pola, `x`, `y`, i `z`.

Niejawna konwersja istnieje z typu klasy do dowolnego z jego typów klas podstawowych. W związku z tym zmienna typu klasy może odwoływać się do wystąpienia tej klasy lub wystąpienia dowolnej klasy pochodnej. Na przykład uwzględniając poprzednie deklaracje klas, zmienna typu `Point` może odwoływać się do `Point` lub `Point3D`:

[!code-csharp[Point3DExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L22-L23)]

## <a name="fields"></a>Pola

*Pole* jest zmienną, która jest skojarzona z klasą lub wystąpieniem klasy.

Pole zadeklarowane ze modyfikatorem static definiuje pole statyczne. Pole statyczne identyfikuje dokładnie jedną lokalizację magazynu. Niezależnie od tego, ile wystąpień klasy zostało utworzonych, istnieje tylko jedna kopia pola statycznego.

Pole zadeklarowane bez modyfikatora static definiuje pole wystąpienia. Każde wystąpienie klasy zawiera oddzielną kopię wszystkich pól wystąpienia tej klasy.

W `Color` poniższym przykładzie każde wystąpienie klasy ma oddzielną kopię `r` `g` `White`pól,, i `b` `Black`wystąpienia `Red`, ale istnieje tylko jedna kopia,,, `Green` i`Blue` pola statyczne:

[!code-csharp[ColorClass](~/samples/snippets/csharp/tour/classes-and-objects/Color.cs#L3-L17)]

Jak pokazano w poprzednim przykładzie *pola tylko do odczytu* mogą być zadeklarowane za pomocą `readonly` modyfikatora. Przypisanie do `readonly` pola może wystąpić tylko jako część deklaracji pola lub konstruktora w tej samej klasie.

## <a name="methods"></a>Metody

*Metoda* to element członkowski implementujący obliczenia lub akcję, które mogą być wykonywane przez obiekt lub klasę. *Metody statyczne* są dostępne za pomocą klasy. *Metody wystąpienia* są dostępne za pomocą wystąpień klasy.

Metody mogą mieć listę *parametrów*reprezentujących wartości lub odwołania do zmiennych, które są przenoszone do metody, oraz *Typ zwracany*, który określa typ wartości obliczanej i zwracanej przez metodę. Zwracany typ metody to `void` , jeśli nie zwraca wartości.

Podobnie jak typy, metody mogą także mieć zestaw parametrów typu, dla których argumenty typu muszą być określone, gdy wywoływana jest metoda. W przeciwieństwie do typów, argumenty typu często można wywnioskować na podstawie argumentów wywołania metody i nie muszą być jawnie określone.

*Sygnatura* metody musi być unikatowa w klasie, w której metoda jest zadeklarowana. Podpis metody składa się z nazwy metody, liczby parametrów typu oraz liczby, modyfikatorów i typów jego parametrów. Sygnatura metody nie zawiera typu zwracanego.

### <a name="parameters"></a>Parametry

Parametry służą do przekazywania wartości lub odwołań do zmiennych do metod. Parametry metody pobierają rzeczywiste wartości z *argumentów* , które są określone podczas wywoływania metody. Istnieją cztery rodzaje parametrów: parametry wartości, parametry odwołania, parametry wyjściowe i tablice parametrów.

*Parametr value* jest używany do przekazywania argumentów wejściowych. Parametr value odnosi się do zmiennej lokalnej, która pobiera jej wartość początkową z argumentu, który został przesłany dla parametru. Modyfikacje parametru value nie wpływają na argument, który został przesłany dla parametru.

Parametry wartości mogą być opcjonalne, określając wartość domyślną, aby można było pominąć odpowiednie argumenty.

*Parametr Reference* służy do przekazywania argumentów przez odwołanie. Argument przesłany dla parametru odwołania musi być zmienną z określoną wartością, a podczas wykonywania metody parametr Reference reprezentuje tę samą lokalizację magazynu co zmienna argumentu. Parametr odwołania jest zadeklarowany z `ref` modyfikatorem. W poniższym przykładzie pokazano sposób użycia `ref` parametrów.

[!code-csharp[swapExample](~/samples/snippets/csharp/tour/classes-and-objects/RefExample.cs#L3-L18)]

*Parametr wyjściowy* jest używany do przekazywania argumentów przez odwołanie. Jest on podobny do parametru Reference, z tą różnicą, że nie wymaga jawnie przypisywania wartości do argumentu dostarczonego przez wywołującego. Parametr wyjściowy jest zadeklarowany z `out` modyfikatorem. W poniższym przykładzie pokazano użycie `out` parametrów przy użyciu składni wprowadzonej w C# 7.

[!code-csharp[OutExample](~/samples/snippets/csharp/tour/classes-and-objects/OutExample.cs#L3-L17)]

*Tablica parametrów* umożliwia przekazanie zmiennej liczbie argumentów do metody. Tablica parametrów jest zadeklarowana z `params` modyfikatorem. Tylko ostatni parametr metody może być tablicą parametrów, a typ tablicy parametrów musi być typem tablicy jednowymiarowej. Metody zapisu i WriteLine <xref:System.Console?displayProperty=nameWithType> klasy są dobrymi przykładami użycia tablicy parametrów. Są one deklarowane w następujący sposób.

[!code-csharp[ConsoleExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L78-L83)]

W metodzie, która używa tablicy parametrów, tablica parametrów zachowuje się dokładnie tak jak zwykły parametr typu tablicy. Jednak w wywołaniu metody z tablicą parametrów możliwe jest przekazanie jednego argumentu typu tablicy parametrów lub dowolnej liczby argumentów typu elementu tablicy parametrów w parametrze. W tym drugim przypadku wystąpienie tablicy jest automatycznie tworzone i inicjowane z podanym argumentami. Ten przykład

[!code-csharp[StringFormat](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L55-L55)]

jest równoznaczny z zapisem poniżej.

[!code-csharp[StringFormat2](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L30-L35)]

### <a name="method-body-and-local-variables"></a>Treść metody i zmienne lokalne

Treść metody Określa instrukcje do wykonania, gdy metoda jest wywoływana.

Treść metody może deklarować zmienne, które są specyficzne dla wywołania metody. Takie zmienne są nazywane *zmiennymi lokalnymi*. Deklaracja zmiennej lokalnej określa nazwę typu, nazwę zmiennej i prawdopodobnie wartość początkową. Poniższy przykład deklaruje zmienną `i` lokalną z początkową wartością zero i zmienną `j` lokalną bez wartości początkowej.

[!code-csharp[Squares](~/samples/snippets/csharp/tour/classes-and-objects/Squares.cs#L3-L17)]

C#wymaga, aby zmienna lokalna była *przypisana ostatecznie* przed uzyskaniem jej wartości. Na przykład jeśli deklaracja poprzedniej `i` nie zawierała wartości początkowej, kompilator zgłosi błąd dla kolejnych zastosowań `i` , ponieważ `i` nie zostanie on ostatecznie przypisany w tych punktach w programie.

Metoda może użyć `return` instrukcji do zwrócenia kontroli do obiektu wywołującego. W wyniku zwrócenia `void` `return` metody instrukcje nie mogą określać wyrażenia. W metodzie zwracającej wartości inne niż `return` void instrukcje muszą zawierać wyrażenie, które oblicza wartość zwracaną.

### <a name="static-and-instance-methods"></a>Metody static i instance

Metoda zadeklarowana za pomocą modyfikatora static jest *metodą statyczną*. Metoda statyczna nie działa w konkretnym wystąpieniu i może bezpośrednio uzyskiwać dostęp do statycznych elementów członkowskich.

Metoda zadeklarowana bez modyfikatora static jest *metodą wystąpienia*. Metoda wystąpienia działa w konkretnym wystąpieniu i może uzyskiwać dostęp do elementów członkowskich static i instance. Wystąpienie, na którym wywołano metodę wystąpienia, można jawnie uzyskać do niego `this`dostęp. Wystąpił błąd podczas odwoływania się `this` do w metodzie statycznej.

Następująca `Entity` Klasa zawiera elementy członkowskie statyczne i wystąpienia.

[!code-csharp[Entity](~/samples/snippets/csharp/tour/classes-and-objects/Entity.cs#L16-L36)]

Każde `Entity` wystąpienie zawiera numer seryjny (i najprawdopodobniej inne informacje, które nie są wyświetlane w tym miejscu). `Entity` Konstruktor (który przypomina metodę wystąpienia) Inicjuje nowe wystąpienie przy użyciu następnego dostępnego numeru seryjnego. Ponieważ Konstruktor jest członkiem wystąpienia, może uzyskać dostęp zarówno `serialNo` do pola wystąpienia, `nextSerialNo` jak i pola statycznego.

Metody `GetNextSerialNo` `serialNo` i `SetNextSerialNo`staticmogą uzyskać dostęp do pola statycznego,alemożetobyćbłąd,abyuzyskaćbezpośrednidostępdopolawystąpienia.`nextSerialNo`

Poniższy przykład pokazuje użycie klasy Entity.

[!code-csharp[EntityExample](~/samples/snippets/csharp/tour/classes-and-objects/Entity.cs#L3-L15)]

Należy zauważyć, `SetNextSerialNo` że `GetNextSerialNo` metody i są wywoływane `GetSerialNo` dla klasy, podczas gdy metoda wystąpienia jest wywoływana w wystąpieniach klasy.

### <a name="virtual-override-and-abstract-methods"></a>Metody wirtualne, przesłonięcia i abstrakcyjne

Gdy deklaracja metody wystąpienia zawiera `virtual` modyfikator, metoda jest uznawana za *metodę wirtualną*. Gdy nie jest dostępny żaden modyfikator wirtualny, metoda jest uznawana za *metodę niewirtualną*.

Gdy wywoływana jest metoda wirtualna, *typem czasu wykonywania* wystąpienia, dla którego odbywa się wywołanie określa rzeczywistą implementację metody do wywołania. W wywołaniu metody niewirtualnej *Typ czasu kompilacji* wystąpienia jest czynnikiem decydującym.

Metoda wirtualna może zostać przesłonięta w klasie pochodnej. Gdy deklaracja metody wystąpienia zawiera modyfikator przesłonięcia, metoda zastępuje dziedziczonej metody wirtualnej tą samą sygnaturą. Podczas gdy deklaracja metody wirtualnej wprowadza nową metodę, Deklaracja metody przesłonięcia specjalizacji istniejącej dziedziczonej metody wirtualnej, dostarczając nową implementację tej metody.

*Metoda abstrakcyjna* jest metodą wirtualną bez implementacji. Metoda abstrakcyjna jest zadeklarowana przy użyciu modyfikatora abstract i jest dozwolona tylko w klasie, która również jest zadeklarowana jako abstract. Metoda abstrakcyjna musi zostać przesłonięta w każdej nieabstrakcyjnej klasie pochodnej.

Poniższy przykład deklaruje klasę `Expression`abstrakcyjną, która reprezentuje węzeł drzewa wyrażenia i trzy `Constant`klasy pochodne,, `VariableReference`i `Operation`, które implementują węzły drzewa wyrażeń dla stałych, zmienna odwołania i operacje arytmetyczne. (Jest to podobne do, ale nie należy mylić z typami drzewa wyrażeń).

[!code-csharp[ExpressionClass](~/samples/snippets/csharp/tour/classes-and-objects/Expressions.cs#L3-L61)]

Poprzednie cztery klasy mogą służyć do modelowania wyrażeń arytmetycznych. Na przykład przy użyciu wystąpień tych klas wyrażenie `x + 3` może być reprezentowane w następujący sposób.

[!code-csharp[ExpressionExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L40-L43)]

Metoda wystąpienia jest wywoływana w celu obliczenia `double` danego wyrażenia i utworzenia wartości. `Expression` `Evaluate` Metoda przyjmuje `Dictionary` argument, który zawiera nazwy zmiennych (jako klucze wpisów) i wartości (jako wartości wpisów). Ponieważ `Evaluate` jest to metoda abstrakcyjna, klasy nieabstrakcyjne `Expression` pochodne muszą zostać `Evaluate`przesłonięte.

`Constant` Implementacjapoprostu`Evaluate` zwraca przechowywaną stałą. Implementacja `VariableReference`programu wyszukuje nazwę zmiennej w słowniku i zwraca wartość wynikową. Implementacja najpierw szacuje lewy i prawy operand (cyklicznie wywołując ich `Evaluate` metody), a następnie wykonuje daną operację arytmetyczną. `Operation`

Poniższy program używa `Expression` klas do obliczenia wyrażenia `x * (y + 2)` pod kątem różnych wartości `x` i `y`.

[!code-csharp[ExpressionUsage](~/samples/snippets/csharp/tour/classes-and-objects/Expressions.cs#L66-L89)]

### <a name="method-overloading"></a>Przeciążanie metody

Przeciążanie metod pozwala wielu metodom w tej samej klasie mieć taką samą nazwę, o ile mają unikatowe podpisy. Podczas kompilowania wywołania przeciążonej metody kompilator używa *rozdzielczości przeciążenia* do określenia konkretnej metody do wywołania. Rozpoznanie przeciążenia umożliwia znalezienie jednej metody, która najlepiej pasuje do argumentów lub zgłasza błąd, jeśli nie można znaleźć pojedynczego najlepszego dopasowania. W poniższym przykładzie przedstawiono sposób rozwiązywania przeciążenia. Komentarz dla każdego wywołania `UsageExample` metody pokazuje, która metoda jest faktycznie wywoływana.

[!code-csharp[OverloadUsage](~/samples/snippets/csharp/tour/classes-and-objects/Overloading.cs#L3-L41)]

Jak pokazano w przykładzie, dana metoda może być zawsze wybierana przez jawne rzutowanie argumentów na dokładne typy parametrów i/lub jawne dostarczenie argumentów typu.

## <a name="other-function-members"></a>Inne elementy członkowskie funkcji

Elementy członkowskie, które zawierają kod wykonywalny, są określane zbiorczo jako *elementy członkowskie* klasy. W poprzedniej sekcji opisano metody, które są podstawowym rodzajem elementów członkowskich funkcji. W tej sekcji opisano inne rodzaje składowych funkcji obsługiwane przez C#: konstruktory, właściwości, indeksatory, zdarzenia, operatory i finalizatory.

Poniżej przedstawiono klasę generyczną o nazwie `MyList<T>`, która implementuje rozwijaną listę obiektów. Klasa zawiera kilka przykładów typowych rodzajów elementów członkowskich funkcji.

> [!NOTE]
> Ten przykład tworzy `MyList` klasę, która nie jest taka sama jak .NET standard <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>. Przedstawia koncepcje niezbędne do tego samouczka, ale nie zastępuje tej klasy.

[!code-csharp[ListClass](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L4-L89)]

### <a name="constructors"></a>Konstruktorów

C#obsługuje zarówno konstruktory wystąpienia, jak i statyczne. *Konstruktor wystąpienia* jest członkiem, który implementuje akcje wymagane do zainicjowania wystąpienia klasy. *Statyczny Konstruktor* jest członkiem, który implementuje akcje wymagane do zainicjowania samej klasy podczas pierwszego ładowania.

Konstruktor jest zadeklarowany jak metoda bez zwracanego typu i o takiej samej nazwie jak zawierająca klasy. Jeśli deklaracja konstruktora zawiera modyfikator statyczny, deklaruje Konstruktor statyczny. W przeciwnym razie deklaruje Konstruktor wystąpienia.

Konstruktory wystąpień mogą być przeciążone i mogą mieć parametry opcjonalne. Na przykład `MyList<T>` Klasa deklaruje jeden Konstruktor wystąpienia z jednym opcjonalnym `int` parametrem. Konstruktory wystąpień są wywoływane przy `new` użyciu operatora. Poniższe instrukcje przydzielą `MyList<string>` dwa wystąpienia przy użyciu konstruktora `MyList` klasy z argumentem opcjonalnym i bez niego.

[!code-csharp[ListExample1](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L95-L96)]

W przeciwieństwie do innych elementów członkowskich, konstruktory wystąpień nie są dziedziczone, a Klasa nie ma konstruktorów wystąpień innych niż zadeklarowane w klasie. Jeśli nie podano konstruktora wystąpienia dla klasy, zostanie automatycznie podana pusta wartość bez parametrów.

### <a name="properties"></a>Właściwości

*Właściwości* są naturalnym rozszerzeniem pól. Oba są nazwanymi członkami ze skojarzonymi typami, a składnia dostępu do pól i właściwości jest taka sama. Jednak w przeciwieństwie do pól właściwości nie oznacza lokalizacji magazynu. Zamiast tego właściwości mają metody *dostępu* określające instrukcje, które mają być wykonywane, gdy ich wartości są odczytywane lub zapisywane.

Właściwość jest zadeklarowana jako pole, z tą różnicą, że deklaracja kończy się metodą dostępu get i/lub zestawem metoda dostępu, która jest `{` zapisywana między ogranicznikami i `}` zamiast kończyć się średnikiem. Właściwość, która ma zarówno metodę dostępu get, jak i zestaw akcesora zestawu jest właściwością do *odczytu i zapisu*, właściwość, która ma tylko metodę dostępu get, jest właściwością *tylko do odczytu*, a właściwość, która ma tylko metodę dostępu zestawu, jest właściwością *tylko do zapisu*.

Metoda dostępu get odpowiada metodzie bez parametrów z wartością zwracaną typu właściwości. Poza elementem docelowym przypisania, gdy właściwość jest przywoływana w wyrażeniu, metoda dostępu get właściwości jest wywoływana, aby obliczyć wartość właściwości.

Metoda dostępu zestawu odpowiada metodzie z pojedynczym parametrem o nazwie Value i bez zwracanego typu. Gdy właściwość jest przywoływana jako element docelowy przypisania lub jako operand + + lub--, metoda dostępu set jest wywoływana z argumentem, który udostępnia nową wartość.

Klasa deklaruje dwie `Count` właściwości i `Capacity`, które są tylko do odczytu i odczytu i zapisu. `MyList<T>` Poniżej przedstawiono przykład zastosowania tych właściwości:

[!code-csharp[ListExample2](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L101-L104)]

Podobnie jak pola i metody, C# obsługuje zarówno właściwości wystąpienia, jak i właściwości statyczne. Właściwości statyczne są zadeklarowane za pomocą modyfikatora static, a właściwości wystąpienia są deklarowane bez użycia.

Metody dostępu właściwości mogą być wirtualne. Gdy Deklaracja właściwości zawiera `virtual`modyfikator, `abstract`lub `override` , ma zastosowanie do akcesorów właściwości.

### <a name="indexers"></a>Indeksatory

*Indeksator* jest członkiem, który umożliwia indeksowanie obiektów w taki sam sposób jak w przypadku tablicy. Indeksator jest zadeklarowany jak właściwość, z tą różnicą, że `this` po nazwie składowej następuje lista parametrów zapisywana między `[` ogranicznikami i `]`. Parametry są dostępne w metodach dostępu indeksatora. Podobnie jak w przypadku właściwości, indeksatory mogą być tylko do odczytu i zapisu, tylko do odczytu i do zapisu, a Akcesory dla indeksatora mogą być wirtualne.

Klasa deklaruje pojedynczy indeksator do odczytu i zapisu, który `int` pobiera parametr. `MyList<T>` Indeksator umożliwia indeksowanie `MyList<T>` wystąpień z `int` wartościami. Na przykład:

[!code-csharp[ListExample3](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L109-L117)]

Indeksatory mogą być przeciążone, co oznacza, że Klasa może deklarować wiele indeksatorów, o ile liczba lub typy ich parametrów różnią się.

### <a name="events"></a>Zdarzenia

*Zdarzenie* jest członkiem, który umożliwia klasy lub obiektowi dostarczanie powiadomień. Zdarzenie jest zadeklarowane jak pole, z tą różnicą, że deklaracja zawiera słowo kluczowe zdarzenia, a typem musi być typ delegata.

W obrębie klasy, która deklaruje element członkowski zdarzenia, zdarzenie zachowuje się podobnie jak pole typu delegata (pod warunkiem, że zdarzenie nie jest abstrakcyjne i nie deklaruje metod dostępu). W polu jest przechowywane odwołanie do delegata, który reprezentuje programy obsługi zdarzeń, które zostały dodane do zdarzenia. Jeśli nie ma żadnych programów obsługi zdarzeń, pole jest `null`.

Klasa deklaruje pojedynczy element członkowski zdarzenia o `Changed`nazwie, który wskazuje, że dodano nowy element do listy. `MyList<T>` Zmienione zdarzenie jest wywoływane przez `OnChanged` metodę wirtualną, która najpierw sprawdza, czy zdarzenie jest `null` (oznacza, że nie ma żadnych programów obsługi). Pojęcie związane z wywoływaniem zdarzenia jest dokładnie równoważne do wywołania delegata reprezentowanego przez zdarzenie, co oznacza, że nie istnieją żadne specjalne konstrukcje języka do wywoływania zdarzeń.

Klienci reagują na zdarzenia za poorednictwem *programów obsługi zdarzeń*. Procedury obsługi zdarzeń są dołączane `+=` przy użyciu operatora i usuwane `-=` przy użyciu operatora. Poniższy przykład dołącza procedurę obsługi zdarzeń do `Changed` zdarzenia. `MyList<string>`

[!code-csharp[EventExample](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L132-L148)]

W przypadku zaawansowanych scenariuszy, w których wymagana jest kontrola bazowego magazynu zdarzenia, deklaracja zdarzenia może jawnie dostarczyć `add` i `remove` akcesorów, które `set` są nieco podobne do metody dostępu do właściwości.

### <a name="operators"></a>Operatory

*Operator* jest członkiem, który definiuje znaczenie zastosowania określonego operatora wyrażenia do wystąpienia klasy. Można zdefiniować trzy rodzaje operatorów: operatory jednoargumentowe, operatory binarne i operatory konwersji. Wszystkie operatory muszą być zadeklarowane `public` jako `static`i.

Klasa deklaruje dwa `operator ==` operatory i `operator !=`i w ten sposób daje nowe znaczenie dla wyrażeń, które stosują te `MyList` operatory do wystąpień. `MyList<T>` W zależności od tego operatory definiują równość `MyList<T>` dwóch wystąpień, porównując każdy z zawartych obiektów przy użyciu metod równych. Poniższy przykład używa `==` operatora do porównywania dwóch `MyList<int>` wystąpień.

[!code-csharp[OperatorExample](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L121-L129)]

Pierwsze `Console.WriteLine` dane wyjściowe `True` , ponieważ dwie listy zawierają tę samą liczbę obiektów z tymi samymi wartościami w tej samej kolejności. `Console.WriteLine` `False` `MyList<int>` Nie zdefiniowano `operator ==`, pierwsze miałoby wynik, ponieważ `a` i odwołuje się do `b` różnych wystąpień. `MyList<T>`

### <a name="finalizers"></a>Finalizatory

*Finalizator* jest członkiem, który implementuje akcje wymagane do sfinalizowania wystąpienia klasy. Finalizatory nie mogą mieć parametrów, nie mogą mieć modyfikatorów dostępności i nie mogą być wywoływane jawnie. Finalizator dla wystąpienia jest wywoływany automatycznie podczas wyrzucania elementów bezużytecznych.

Moduł wyrzucania elementów bezużytecznych jest dozwolony w przypadku podejmowania decyzji podczas zbierania obiektów i uruchamiania finalizatorów. W odróżnieniu od chronometrażu wywołań finalizatora nie jest deterministyczna, a finalizatory mogą być wykonywane na dowolnym wątku. Z tych i innych powodów klasy powinny implementować finalizatory tylko wtedy, gdy żadne inne rozwiązania nie są możliwe.

`using` Instrukcja zawiera lepsze podejście do niszczenia obiektów.

> [!div class="step-by-step"]
> [Poprzedni](statements.md)Następny
> [](structs.md)
