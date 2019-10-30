---
title: Dopasowanie wzorca — C# Przewodnik
description: Dowiedz się więcej na temat wyrażeń dopasowania wzorców wC#
ms.date: 04/10/2019
ms.technology: csharp-fundamentals
ms.assetid: 1e575c32-2e2b-4425-9dca-7d118f3ed15b
ms.openlocfilehash: ff84ddd4f07fb77dc9fe648a495a441ed8f9198b
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039369"
---
# <a name="pattern-matching"></a>Dopasowanie wzorca

Wzorzec testuje, że wartość ma określony *kształt*i może *wyodrębnić* informacje z wartości, gdy ma pasujący kształt. Dopasowanie wzorca zawiera bardziej zwięzłą składnię dla algorytmów, które już dzisiaj używały. Można już tworzyć algorytmy dopasowywania wzorców przy użyciu istniejącej składni. Należy napisać `if` lub `switch` instrukcji, które testują wartości. Następnie, gdy te instrukcje są zgodne, wyodrębnisz i użyjesz informacji z tej wartości. Nowe elementy składni są rozszerzeniami do instrukcji, które są już znane: `is` i `switch`. Te nowe rozszerzenia łączą testowanie wartości i wyodrębniają te informacje.

W tym artykule poznasz nową składnię, aby pokazać, jak to umożliwia czytelny, zwięzły kod. Dopasowywanie wzorców umożliwia idiomy, w których dane i kod są oddzielane, w przeciwieństwie do projektów zorientowanych obiektowo, w przypadku których dane i metody manipulowania nimi są ściśle sprzężone.

Aby zilustrować te nowe idiomy, przyjrzyjmy się strukturom, które reprezentują kształty geometryczne przy użyciu instrukcji dopasowania do wzorca. Prawdopodobnie wiesz już, jak tworzyć hierarchie klas i tworzyć [metody wirtualne i zastąpione metody,](methods.md#inherited) aby dostosować zachowanie obiektów na podstawie typu środowiska uruchomieniowego obiektu.

Te techniki nie są możliwe w przypadku danych, które nie są strukturalne w hierarchii klas. Gdy dane i metody są oddzielone, potrzebne są inne narzędzia. Nowe konstrukcje *dopasowania wzorców* umożliwiają oczyszczarkę składnię do badania danych i manipulowania przepływem sterowania na podstawie dowolnego warunku tych danych. Należy już napisać `if` instrukcji i `switch`, które testują wartość zmiennej. Należy napisać `is` instrukcji, które testują typ zmiennej. *Dopasowanie wzorca* dodaje nowe możliwości do tych instrukcji.

W tym artykule utworzysz metodę, która oblicza obszar różnych kształtów geometrycznych. Jednak należy to zrobić bez konieczności wykonywania technik zorientowanych obiektowo i tworzenia hierarchii klas dla różnych kształtów.
Zamiast tego użyjesz *dopasowania do wzorca* .
Korzystając z tego przykładu, należy pokontraście ten kod, tak aby był on strukturalny jako hierarchia obiektów. Gdy dane, które należy wykonać podczas wykonywania zapytania i manipulowania, nie są hierarchią klas, dopasowanie wzorców umożliwia tworzenie eleganckich projektów.

Zamiast rozpoczynać się od definicji kształtu abstrakcyjnego i dodawać różne klasy kształtów, zacznijmy zamiast od prostych definicji zawierających tylko dane dla każdego z kształtów geometrycznych:

[!code-csharp[ShapeDefinitions](../../samples/csharp/PatternMatching/Shapes.cs#01_ShapeDefinitions "Shape definitions")]

Z tych struktur Napiszmy metodę, która oblicza obszar pewnego kształtu.

## <a name="the-is-type-pattern-expression"></a>Wyrażenie wzorca typu `is`

Przed C# 7,0 należy przetestować każdy typ w serii`if`i`is`instrukcji:

[!code-csharp[ClassicIsExpression](../../samples/csharp/PatternMatching/GeometricUtilities.cs#02_ClassicIsExpression "Classic type pattern using is")]

Ten kod powyżej jest wyrażeniem klasycznym *wzorca typu*: testujesz zmienną, aby określić jej typ i wykonując inną akcję na podstawie tego typu.

Ten kod będzie prostszy przy użyciu rozszerzeń wyrażenia `is`, aby przypisać zmienną, jeśli test zakończy się pomyślnie:

[!code-csharp[IsPatternExpression](../../samples/csharp/PatternMatching/GeometricUtilities.cs#03_IsPatternExpression "is pattern expression")]

W tej zaktualizowanej wersji wyrażenie `is` obydwu testuje zmienną i przypisuje ją do nowej zmiennej odpowiedniego typu. Należy również zauważyć, że ta wersja zawiera typ `Rectangle`, który jest `struct`. Nowe wyrażenie `is` działa z typami wartości, a także typami referencyjnymi.

Reguły języka dla wyrażeń dopasowania wzorców pomagają uniknąć nieprawidłowych wyników wyrażenia dopasowania. W powyższym przykładzie zmienne `s`, `c`i `r` są tylko w zakresie i ostatecznie przypisane, gdy odpowiednie wyrażenia dopasowania wzorców mają `true` wyniki. Jeśli spróbujesz użyć dowolnej zmiennej w innej lokalizacji, kod generuje błędy kompilatora.

Sprawdźmy szczegóły obu tych reguł, rozpoczynając od zakresu. Zmienna `c` jest w zakresie tylko w gałęzi `else` pierwszej instrukcji `if`. Zmienna `s` znajduje się w zakresie `ComputeAreaModernIs`metody. Jest to spowodowane tym, że każda gałąź instrukcji `if` ustanawia oddzielny zakres dla zmiennych. Jednak sama instrukcja `if` nie jest. Oznacza to, że zmienne zadeklarowane w instrukcji `if` są w tym samym zakresie co instrukcja `if` (metoda w tym przypadku). To zachowanie nie jest specyficzne dla dopasowania do wzorca, ale jest zachowaniem zdefiniowanym dla zakresów zmiennych i instrukcji `if` i `else`.

Zmienne `c` i `s` są przypisywane, gdy odpowiednie instrukcje `if` są prawdziwe ze względu na to, że jest on w nieskończony sposób przypisany.

> [!TIP]
> W przykładach w tym temacie użyto zalecanej konstrukcji, w której wyrażenie `is`e zgodne ze wzorcem ostatecznie przypisuje zmienną Match w gałęzi `true` instrukcji `if`.
> Można wycofać logikę, wypowiadając `if (!(shape is Square s))`, a zmienna `s` będzie ostatecznie przypisana tylko w gałęzi `false`. Chociaż jest to prawidłowe C#, nie jest to zalecane, ponieważ jest bardziej trudne do przestrzegania logiki.

Te reguły oznaczają, że nie jest możliwe przypadkowe uzyskanie dostępu do wyniku wyrażenia dopasowania do wzorca, gdy ten wzorzec nie został spełniony.

## <a name="using-pattern-matching-switch-statements"></a>Używanie instrukcji `switch` zgodnych ze wzorcem

Gdy przejdzie czas, może być konieczne obsługę innych typów kształtów. W miarę zwiększania się liczby testowanych warunków można się dowiedzieć, że użycie wyrażeń dopasowania wzorca `is` może być kłopotliwe. Oprócz wymagania `if` instrukcji dla każdego typu, który chcesz sprawdzić, wyrażenia `is` są ograniczone do testowania, jeśli dane wejściowe są zgodne z pojedynczym typem. W tym przypadku zobaczysz, że wyrażenia dopasowania wzorca `switch` staną się lepszym wyborem. 

Tradycyjna instrukcja `switch` była wyrażeniem wzorca: obsługuje stałe wzorce.
Można porównać zmienną z dowolną stałą używaną w instrukcji `case`:

[!code-csharp[ClassicSwitch](../../samples/csharp/PatternMatching/GeometricUtilities.cs#04_ClassicSwitch "Classic switch statement")]

Jedynym wzorcem obsługiwanym przez instrukcję `switch` była stała wzorca. Jest on bardziej ograniczony do typów liczbowych i typu `string`.
Te ograniczenia zostały usunięte i można teraz napisać instrukcję `switch` przy użyciu wzorca typu:

[!code-csharp[Switch Type Pattern](../../samples/csharp/PatternMatching/GeometricUtilities.cs#05_SwitchTypePattern "Compute with `switch` expression")]

Składnia zgodna ze wzorcem `switch` używa znanej składni dla deweloperów, którzy używali tradycyjnej instrukcji `switch` języka C. Poszczególne `case` są oceniane i kod pod warunkiem, który pasuje do zmiennej wejściowej jest wykonywany. Wykonanie kodu nie może "przechodzenie" z jednego wyrażenia case do następnego; Składnia instrukcji `case` wymaga, aby każdy `case` kończyć się `break`, `return`lub `goto`.

> [!NOTE]
> Instrukcje `goto`, aby przejść do innej etykiety, są prawidłowe tylko dla wzorca stałej (instrukcji switch klasycznego).

Istnieją ważne nowe reguły dotyczące `switch` instrukcji. Ograniczenia dotyczące typu zmiennej w wyrażeniu `switch` zostały usunięte.
Można użyć dowolnego typu, takiego jak `object` w tym przykładzie. Wyrażenia case nie są już ograniczone do wartości stałych. Usunięcie tego ograniczenia oznacza, że zmiany kolejności `switch` mogą zmienić zachowanie programu.

Gdy są ograniczone do wartości stałych, nie więcej niż jedna etykieta `case` może pasować do wartości wyrażenia `switch`. Połącz z regułą, że każda sekcja `switch` nie może przechodzić do kolejnej sekcji, a następnie, gdy sekcje `switch` można zmienić w dowolnej kolejności bez wpływu na zachowanie.
Teraz, mając bardziej uogólnione wyrażenia `switch`, kolejność każdej sekcji jest ważna. Wyrażenia `switch` są oceniane w kolejności tekstowej. Wykonanie przenosi do pierwszej etykiety `switch`, która pasuje do wyrażenia `switch`.  
Przypadek `default` będzie wykonywany tylko wtedy, gdy żadne inne etykiety case nie pasują do siebie. Wielkość liter `default` jest szacowana jako Ostatnia, niezależnie od kolejności tekstu. Jeśli nie ma `default` przypadku i żadna z innych instrukcji `case` nie jest zgodna, wykonanie kontynuuje się zgodnie z instrukcją podaną w instrukcji `switch`. Żaden z kodów etykiet `case` nie jest wykonywany.

## <a name="when-clauses-in-case-expressions"></a>klauzule `when` w wyrażeniach `case`

Można tworzyć specjalne przypadki dla tych kształtów, które mają 0 obszarów, używając klauzuli `when` w etykiecie `case`. Kwadrat o długości bocznej 0 lub Okręg o promieniu 0 ma powierzchnię 0. Należy określić warunek przy użyciu klauzuli `when` w etykiecie `case`:  

[!code-csharp[ComputeDegenerateShapes](../../samples/csharp/PatternMatching/GeometricUtilities.cs#07_ComputeDegenerateShapes "Compute shapes with 0 area")]

Ta zmiana pokazuje kilka ważnych punktów dotyczących nowej składni. Najpierw do jednej sekcji `switch` można zastosować wiele etykiet `case`. Blok instrukcji jest wykonywany, gdy dowolna z tych etykiet jest `true`. W tym przypadku, jeśli wyrażenie `switch` jest okrąg lub kwadrat z 0 obszaru, metoda zwraca stałą 0.

W tym przykładzie wprowadzono dwie różne zmienne w dwóch `case` etykietach dla pierwszego bloku `switch`. Należy zauważyć, że instrukcje w tym bloku `switch` nie używają zmiennych `c` (dla okręgu) lub `s` (dla kwadratu).
Żadna z tych zmiennych nie jest ostatecznie przypisana w tym bloku `switch`.
Jeśli jeden z tych przypadków jest zgodny, wyraźnie jedna ze zmiennych została przypisana.
Nie jest jednak możliwe informowanie, *które* zostało przypisane w czasie kompilacji, ponieważ każdy przypadek może być zgodny w czasie wykonywania. Z tego powodu najczęściej w przypadku używania wielu `case` etykiet dla tego samego bloku nie zostanie wprowadzona nowa zmienna w instrukcji `case` lub w klauzuli `when` będzie używana tylko zmienna.

Po dodaniu tych kształtów w obszarze 0 Dodajmy kilka typów kształtów: prostokąt i Trójkąt:

[!code-csharp[AddRectangleAndTriangle](../../samples/csharp/PatternMatching/GeometricUtilities.cs#09_AddRectangleAndTriangle "Add rectangle and triangle")]

 Ten zestaw zmian dodaje `case` etykiety dla przypadku degeneracji, a następnie etykiety i bloki dla każdego nowego kształtu. 

Na koniec możesz dodać przypadek `null`, aby upewnić się, że argument nie jest `null`:

[!code-csharp[NullCase](../../samples/csharp/PatternMatching/GeometricUtilities.cs#10_NullCase "Add null case")]

Specjalne zachowanie wzorca `null` jest interesujące, ponieważ stała `null` we wzorcu nie ma typu, ale można ją przekonwertować na dowolny typ referencyjny lub typ dopuszczający wartość null. Zamiast konwersji `null` do dowolnego typu, język definiuje, że `null` wartość nie będzie zgodna ze wzorcem typu, niezależnie od typu czasu kompilowania zmiennej. To zachowanie powoduje, że nowy wzorzec typu oparty na `switch` jest spójny z instrukcją `is`: instrukcje `is` zawsze zwracają `false`, gdy sprawdzana wartość jest `null`. Jest również prostsze: po sprawdzeniu typu nie jest wymagane dodatkowe sprawdzenie wartości null. Można sprawdzić, czy nie ma żadnych testów null w żadnym z bloków Case powyższych przykładów: nie jest to konieczne, ponieważ dopasowanie wzorca typu gwarantuje wartość różną od null.

## <a name="var-declarations-in-case-expressions"></a>deklaracje `var` w wyrażeniach `case`

Wprowadzenie `var` jako jednego z wyrażeń dopasowania wprowadza nowe reguły do dopasowania do wzorca.

Pierwsza reguła polega na tym, że deklaracja `var` jest zgodna z regułami wnioskowania o typie normalnym: typ jest wywnioskowany jako typ statyczny wyrażenia Switch. W tej regule typ zawsze jest zgodny.

Druga reguła polega na tym, że deklaracja `var` nie ma sprawdzenia wartości null, ponieważ inne wyrażenia wzorca typu obejmują. Oznacza to, że zmienna może mieć wartość null, a w takim przypadku konieczne jest sprawdzenie wartości null.

Te dwie reguły oznaczają, że w wielu przypadkach deklaracja `var` w wyrażeniu `case` dopasowuje te same warunki co `default` wyrażenie.
Ze względu na to, że przypadek inny niż domyślny jest preferowany w przypadku `default` przypadku, przypadek `default` nigdy nie zostanie wykonany.

> [!NOTE]
> Kompilator nie emituje ostrzeżenia w tych przypadkach, w których zapisano przypadek `default`, ale nigdy nie będzie wykonywany. Jest to zgodne z obecnym zachowaniem instrukcji `switch` w przypadku, gdy wszystkie możliwe przypadki zostały wymienione.

Trzecia reguła wprowadza użycie w przypadku, gdy `var` może być przydatne. Załóżmy, że wykonujesz dopasowanie do wzorca, gdzie dane wejściowe są ciągiem i wyszukujesz znane wartości poleceń. Można napisać coś takiego jak:

[!code-csharp[VarCaseExpression](../../samples/csharp/PatternMatching/Program.cs#VarCaseExpression "use a var case expression to filter white space")]

Wielkość liter `var` jest zgodna z `null`, ciągiem pustym lub dowolnym ciągiem zawierającym tylko biały znak. Zwróć uwagę, że poprzedni kod używa operatora `?.`, aby upewnić się, że nie przypadkowo zgłosił <xref:System.NullReferenceException>. Przypadek `default` obsługuje wszelkie inne wartości ciągów, które nie są zrozumiałe dla tego analizatora poleceń.

Jest to jeden przykład, w którym warto rozważyć wyrażenie CASE `var`, które różni się od wyrażenia `default`.

## <a name="conclusions"></a>Wnioski

*Konstrukcje dopasowania wzorców* umożliwiają łatwe zarządzanie przepływem sterowania między różnymi zmiennymi i typami, które nie są powiązane z hierarchią dziedziczenia. Możesz również sterować logiką, aby używać dowolnego warunku, który można testować na zmiennej. Umożliwia ona wzorce i idiomy, które będą potrzebne częściej, podczas tworzenia bardziej rozproszonych aplikacji, w przypadku których dane i metody manipulowania nimi są osobne. Zauważ, że struktury kształtu używane w tym przykładzie nie zawierają żadnych metod, tylko właściwości tylko do odczytu.
Dopasowanie wzorca współdziała z dowolnym typem danych. Można pisać wyrażenia, które badają obiekt, i podejmować decyzje dotyczące przepływu sterowania na podstawie tych warunków.

Porównaj kod z tego przykładu z projektem, który byłby następujący po utworzeniu hierarchii klas dla abstrakcyjnej `Shape` i określonych kształtów pochodnych z własnym implementacją metody wirtualnej w celu obliczenia obszaru. Często należy zauważyć, że wyrażenia dopasowania wzorców mogą być bardzo użytecznym narzędziem podczas pracy z danymi i chcą oddzielić problemy związane z przechowywaniem danych od problemów z zachowaniem.
