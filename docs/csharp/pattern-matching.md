---
title: Dopasowywanie wzorców — przewodnik po językach C#
description: 'Dowiedz się więcej o wyrażeniach dopasowywania wzorców w c #'
ms.date: 04/10/2019
ms.technology: csharp-fundamentals
ms.assetid: 1e575c32-2e2b-4425-9dca-7d118f3ed15b
ms.openlocfilehash: 0c302499543c90bd01427e2791435968d580f644
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170387"
---
# <a name="pattern-matching"></a>Dopasowanie wzorca

Wzorce testują, że wartość ma określony *kształt*i może *wyodrębnić* informacje z wartości, gdy ma pasujący kształt. Dopasowanie wzorców zapewnia bardziej zwięzłą składnię dla algorytmów, których już używasz dzisiaj. Algorytmy dopasowywania wzorców są już tworzone przy użyciu istniejącej składni. `if` Piszesz `switch` lub instrukcje, które testują wartości. Następnie, gdy te instrukcje są zgodne, wyodrębnić i używać informacji z tej wartości. Nowe elementy składni są rozszerzeniami instrukcji, które `is` już `switch`znasz: i . Te nowe rozszerzenia łączą testowanie wartości i wyodrębnianie tych informacji.

W tym artykule przyjrzymy się nowej składni, aby pokazać, jak umożliwia czytelny, zwięzły kod. Dopasowywanie wzorców umożliwia idiomy, w których dane i kod są oddzielone, w przeciwieństwie do projektów obiektowych, w których dane i metody, które nimi manipulują, są ściśle powiązane.

Aby zilustrować te nowe idiomy, pracujmy ze strukturami reprezentującymi kształty geometryczne przy użyciu instrukcji dopasowywania wzorców. Prawdopodobnie znasz hierarchie klas i tworzenie [metod wirtualnych i przesłoniętych metod](methods.md#inherited) dostosowywania zachowania obiektu na podstawie typu środowiska uruchomieniowego obiektu.

Te techniki nie są możliwe dla danych, które nie są zorganizowane w hierarchii klas. Gdy dane i metody są oddzielne, potrzebne są inne narzędzia. Nowe konstrukcje *dopasowywania wzorców* umożliwiają czystsze składni do zbadania danych i manipulować przepływem sterowania na podstawie dowolnego warunku tych danych. Już `if` piszesz `switch` instrukcje i że test wartości zmiennej. Piszesz `is` instrukcje, które testują typ zmiennej. *Dopasowanie wzorca* dodaje nowe możliwości do tych instrukcji.

W tym artykule stworzysz metodę, która oblicza obszar różnych kształtów geometrycznych. Ale zrobisz to bez uciekania się do technik obiektowych i budowania hierarchii klas dla różnych kształtów.
Zamiast tego *użyjesz dopasowania wzorców.*
Podczas przechodzenia przez ten przykład, kontrast ten kod z jak będzie zorganizowany jako hierarchii obiektów. Gdy dane, które należy zbadać i manipulować nie jest hierarchii klas, dopasowanie wzorca umożliwia eleganckie projekty.

Zamiast zaczynać od abstrakcyjnej definicji kształtu i dodawać różne klasy kształtów, zacznijmy od prostych definicji danych tylko dla każdego z kształtów geometrycznych:

[!code-csharp[ShapeDefinitions](../../samples/snippets/csharp/PatternMatching/Shapes.cs#01_ShapeDefinitions "Shape definitions")]

Z tych struktur napiszmy metodę, która oblicza obszar pewnego kształtu.

## <a name="the-is-type-pattern-expression"></a>Wyrażenie `is` wzorca typu

Przed C# 7.0, należy przetestować każdy typ `if` w `is` serii i instrukcje:

[!code-csharp[ClassicIsExpression](../../samples/snippets/csharp/PatternMatching/GeometricUtilities.cs#02_ClassicIsExpression "Classic type pattern using is")]

Ten powyższy kod jest klasycznym wyrażeniem *wzorca typu:* Testujesz zmienną, aby określić jej typ i podjąć inną akcję na podstawie tego typu.

Ten kod staje się prostszy `is` przy użyciu rozszerzeń do wyrażenia, aby przypisać zmienną, jeśli test zakończy się pomyślnie:

[!code-csharp[IsPatternExpression](../../samples/snippets/csharp/PatternMatching/GeometricUtilities.cs#03_IsPatternExpression "is pattern expression")]

W tej zaktualizowanej `is` wersji wyrażenie testuje zmienną i przypisuje ją do nowej zmiennej właściwego typu. Należy również zauważyć, że `Rectangle` ta wersja `struct`zawiera typ, który jest . Nowe `is` wyrażenie działa z typami wartości, a także typami odwołań.

Reguły języka dla wyrażeń dopasowywania wzorców ułatwiają unikanie nadużywania wyników wyrażenia dopasowania. W powyższym przykładzie zmienne `s` `c`, `r` i są tylko w zakresie i zdecydowanie przypisane, `true` gdy odpowiednie wyrażenia dopasowania wzorca mają wyniki. Jeśli spróbujesz użyć jednej ze zmiennych w innej lokalizacji, kod generuje błędy kompilatora.

Przeanalizujmy szczegółowo obie te reguły, zaczynając od zakresu. Zmienna `c` znajduje się w `else` zakresie tylko `if` w gałęzi pierwszej instrukcji. Zmienna `s` znajduje się w `ComputeAreaModernIs`zakresie w metodzie . Dzieje się tak, ponieważ `if` każda gałąź instrukcji ustanawia osobny zakres zmiennych. Jednak samo `if` stwierdzenie nie. Oznacza to, że `if` zmienne zadeklarowane w instrukcji `if` znajdują się w tym samym zakresie co instrukcja (metoda w tym przypadku). To zachowanie nie jest specyficzne dla dopasowania wzorca, ale jest `if` `else` zdefiniowane zachowanie dla zmiennych zakresów i instrukcji.

Zmienne `c` i `s` są przypisane, gdy `if` odpowiednie instrukcje są prawdziwe ze względu na zdecydowanie przypisane, gdy mechanizm true.

> [!TIP]
> Przykłady w tym temacie użyć zalecanej konstrukcji, gdzie wyrażenie dopasowania `is` wzorca zdecydowanie przypisuje zmienną dopasowania w `true` gałęzi `if` instrukcji.
> Można odwrócić logikę, `if (!(shape is Square s))` mówiąc, `s` a zmienna będzie `false` zdecydowanie przypisana tylko w gałęzi. Chociaż jest to prawidłowy C#, nie jest zalecane, ponieważ jest bardziej mylące, aby postępować zgodnie z logiką.

Te reguły oznaczają, że jest mało prawdopodobne, aby przypadkowo uzyskać dostęp do wyniku wyrażenia dopasowania wzorca, gdy ten wzorzec nie został spełniony.

## <a name="using-pattern-matching-switch-statements"></a>Korzystanie z `switch` instrukcji dopasowywania wzorców

W miarę upływu czasu może być konieczne wsparcie innych typów kształtów. Wraz ze wzrostem liczby testów, które testujesz, `is` przekonasz się, że użycie wyrażenia pasującego do wzorca może stać się kłopotliwe. Oprócz wymagających `if` instrukcji dla każdego typu, który `is` chcesz sprawdzić, wyrażenia są ograniczone do testowania, jeśli dane wejściowe pasuje do pojedynczego typu. W takim przypadku przekonasz `switch` się, że wyrażenia pasujące do wzorca stają się lepszym wyborem.

Tradycyjna `switch` instrukcja była wyrażeniewzorcem: obsługiwała wzorzec stały.
Można porównać zmienną z dowolną `case` stałą używaną w instrukcji:

[!code-csharp[ClassicSwitch](../../samples/snippets/csharp/PatternMatching/GeometricUtilities.cs#04_ClassicSwitch "Classic switch statement")]

Jedynym wzorcem obsługiwanym `switch` przez instrukcję był stały wzorzec. Był on ponadto ograniczony do `string` typów liczbowych i typu.
Te ograniczenia zostały usunięte, a teraz `switch` można napisać instrukcję przy użyciu wzorca typu:

[!code-csharp[Switch Type Pattern](../../samples/snippets/csharp/PatternMatching/GeometricUtilities.cs#05_SwitchTypePattern "Compute with `switch` expression")]

Instrukcja `switch` dopasowania wzorca używa znanej składni deweloperom, `switch` którzy używali tradycyjnej instrukcji w stylu C. Każdy `case` jest oceniany, a kod poniżej warunku, który pasuje do zmiennej wejściowej jest wykonywany. Wykonanie kodu nie może "wpaść" z jednego wyrażenia sprawy do następnego; `case` składnia instrukcji wymaga, aby `case` każdy `break`koniec `return`z `goto`, lub .

> [!NOTE]
> Instrukcje, `goto` aby przejść do innej etykiety są prawidłowe tylko dla wzorca stałego (instrukcja przełącznika klasycznego).

Istnieją ważne nowe zasady `switch` regulujące oświadczenie. Ograniczenia dotyczące typu zmiennej w `switch` wyrażeniu zostały usunięte.
Można użyć dowolnego `object` typu, takiego jak w tym przykładzie. Wyrażenia przypadków nie są już ograniczone do wartości stałych. Usunięcie tego ograniczenia oznacza, `switch` że zmiana kolejności sekcji może zmienić zachowanie programu.

Gdy ograniczone do wartości stałych, `case` nie więcej niż `switch` jedna etykieta może odpowiadać wartości wyrażenia. Połącz to z `switch` regułą, że każda sekcja nie może przechodzić do następnej sekcji, a następnie, że `switch` sekcje mogą być rozmieszczone w dowolnej kolejności bez wpływu na zachowanie.
Teraz, z bardziej `switch` uogólnionym wyrażeniami, kolejność każdej sekcji ma znaczenie. Wyrażenia `switch` są obliczane w kolejności tekstowej. Wykonywanie przenosi do `switch` pierwszej `switch` etykiety, która pasuje do wyrażenia.  
Sprawa `default` zostanie wykonana tylko wtedy, gdy nie są zgodne żadne inne etykiety przypadków. Sprawa `default` jest oceniana jako ostatnia, niezależnie od kolejności tekstowej. Jeśli nie ma `default` żadnego przypadku i `case` żadna z pozostałych instrukcji nie `switch` jest zgodna, wykonanie jest kontynuowane w instrukcji następującej po instrukcji. Żaden z `case` etykiet kod jest wykonywany.

## <a name="when-clauses-in-case-expressions"></a>`when`klauzule `case` w wyrażeniach

Można tworzyć specjalne przypadki dla tych kształtów, `when` które mają `case` obszar 0, używając klauzuli na etykiecie. Kwadrat o długości bocznej 0 lub okrąg o promieniu 0 ma obszar 0. Należy określić ten `when` warunek `case` przy użyciu klauzuli na etykiecie:  

[!code-csharp[ComputeDegenerateShapes](../../samples/snippets/csharp/PatternMatching/GeometricUtilities.cs#07_ComputeDegenerateShapes "Compute shapes with 0 area")]

Ta zmiana pokazuje kilka ważnych punktów dotyczących nowej składni. Najpierw można `case` zastosować wiele etykiet `switch` do jednej sekcji. Blok instrukcji jest wykonywany, gdy `true`dowolna z tych etykiet jest . W tym przypadku `switch` jeśli wyrażenie jest okrąg lub kwadrat z obszaru 0, metoda zwraca stałą 0.

W tym przykładzie przedstawiono dwie różne `case` zmienne w `switch` dwóch etykietach dla pierwszego bloku. Należy zauważyć, że `switch` instrukcje w tym bloku `c` nie używają zmiennych `s` (dla okręgu) lub (dla kwadratu).
Żadna z tych zmiennych nie jest `switch` zdecydowanie przypisana w tym bloku.
Jeśli którykolwiek z tych przypadków są zgodne, wyraźnie jedna ze zmiennych została przypisana.
Jednak nie można powiedzieć, *który* został przypisany w czasie kompilacji, ponieważ w obu przypadkach może być dopasowywany w czasie wykonywania. Z tego powodu większość razy, `case` gdy używasz wielu etykiet dla tego samego bloku, `case` nie będzie wprowadzać nową zmienną `when` w instrukcji lub będzie używać tylko zmiennej w klauzuli.

Po dodaniu tych kształtów z obszarem 0 dodajmy jeszcze kilka typów kształtów: prostokąt i trójkąt:

[!code-csharp[AddRectangleAndTriangle](../../samples/snippets/csharp/PatternMatching/GeometricUtilities.cs#09_AddRectangleAndTriangle "Add rectangle and triangle")]

 Ten zestaw zmian `case` dodaje etykiety dla zdegenerowanego przypadku oraz etykiety i bloki dla każdego z nowych kształtów.

Na koniec można `null` dodać sprawę, aby upewnić `null`się, że argument nie jest:

[!code-csharp[NullCase](../../samples/snippets/csharp/PatternMatching/GeometricUtilities.cs#10_NullCase "Add null case")]

Specjalne zachowanie wzorca `null` jest interesujące, `null` ponieważ stała we wzorcu nie ma typu, ale można przekonwertować na dowolny typ odwołania lub typ nullable. Zamiast konwertować `null` na dowolny typ, język `null` definiuje, że wartość nie będzie zgodna z żadnym wzorcem typu, niezależnie od typu kompilacji zmiennej. To zachowanie sprawia, że nowy `switch` `is` wzorzec typu na podstawie zgodne z instrukcją: `is` instrukcje zawsze zwracają, `false` gdy sprawdzana wartość jest `null`. Jest to również prostsze: po sprawdzeniu typu nie potrzebujesz dodatkowego sprawdzania wartości null. Widać, że z faktu, że nie ma żadnych kontroli null w każdym z bloków sprawy poszczególnych przykładów: nie są one konieczne, ponieważ dopasowanie wzorca typu gwarantuje wartość nienull.

## <a name="var-declarations-in-case-expressions"></a>`var`deklaracje `case` w wyrażeniach

Wprowadzenie `var` jako jedno z wyrażeń dopasowania wprowadza nowe reguły do dopasowania wzorca.

Pierwsza reguła jest, że `var` deklaracja jest zgodna z regułami wnioskowania normalnego typu: Typ jest wywnioskować, aby być statyczny typ wyrażenia przełącznika. Z tej reguły typ zawsze pasuje.

Druga reguła jest, że `var` deklaracja nie ma sprawdzania wartości null, które zawierają inne wyrażenia wzorca typu. Oznacza to, że zmienna może mieć wartość null, a w takim przypadku konieczne jest sprawdzenie zerowe.

Te dwie reguły oznaczają, że `var` w wielu `case` przypadkach deklaracja w `default` wyrażeniu odpowiada tym samym warunkom co wyrażenie.
Ponieważ każda sprawa niedomyślna `default` jest preferowana w przypadku, `default` sprawa nigdy nie zostanie wykonana.

> [!NOTE]
> Kompilator nie emituje ostrzeżenie w tych `default` przypadkach, gdy sprawa została napisana, ale nigdy nie zostanie wykonana. Jest to zgodne `switch` z zachowaniem bieżącej instrukcji, gdzie wszystkie możliwe przypadki zostały wymienione.

Trzecia reguła wprowadza zastosowania, w `var` których przypadek może być przydatny. Wyobraź sobie, że robisz dopasowanie wzorca, gdzie dane wejściowe jest ciąg iem i szukasz znanych wartości poleceń. Możesz napisać coś takiego:

[!code-csharp[VarCaseExpression](../../samples/snippets/csharp/PatternMatching/Program.cs#VarCaseExpression "use a var case expression to filter white space")]

Sprawa `var` pasuje `null`, pusty ciąg lub dowolny ciąg, który zawiera tylko biały znak. Należy zauważyć, że poprzedni `?.` kod używa operatora, aby upewnić <xref:System.NullReferenceException>się, że nie przypadkowo throw . Sprawa `default` obsługuje inne wartości ciągu, które nie są rozumiane przez ten analizator poleceń.

Jest to jeden przykład, w `var` którym warto rozważyć `default` wyrażenie sprawy, które różni się od wyrażenia.

## <a name="conclusions"></a>Wnioski

*Konstrukcje dopasowywania wzorców* umożliwiają łatwe zarządzanie przepływem sterowania między różnymi zmiennymi i typami, które nie są powiązane przez hierarchię dziedziczenia. Można również kontrolować logikę, aby użyć dowolnego warunku, który testujesz na zmiennej. Umożliwia wzorce i idiomy, które będą potrzebne częściej podczas tworzenia bardziej rozproszonych aplikacji, gdzie dane i metody, które manipulują tymi danymi są oddzielne. Można zauważyć, że struktury kształtu używane w tym przykładzie nie zawierają żadnych metod, tylko właściwości tylko do odczytu.
Dopasowanie wzorca działa z dowolnym typem danych. Piszesz wyrażenia, które sprawdzają obiekt i podejmują decyzje dotyczące przepływu sterowania na podstawie tych warunków.

Porównaj kod z tego przykładu z projektem, który `Shape` będzie wynikać z tworzenia hierarchii klas dla abstrakcyjnych i określonych kształtów pochodnych każdy z własną implementację metody wirtualnej do obliczania obszaru. Często okazuje się, że wyrażenia dopasowywania wzorców może być bardzo przydatne narzędzie podczas pracy z danymi i chcesz oddzielić problemy przechowywania danych od problemów zachowania.

## <a name="see-also"></a>Zobacz też

- [Samouczek: Korzystanie z funkcji dopasowywania wzorców w celu rozszerzenia typów danych](tutorials/pattern-matching.md)
