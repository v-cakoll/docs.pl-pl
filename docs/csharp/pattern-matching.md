---
title: Dopasowanie wzoru - Przewodnik C#
description: 'Dowiedz się więcej o wyrażeniach dopasowywania wzorców w języku C #'
ms.date: 04/10/2019
ms.technology: csharp-fundamentals
ms.assetid: 1e575c32-2e2b-4425-9dca-7d118f3ed15b
ms.openlocfilehash: bb6baf3771024d02b2027f81fd35b8be4872cf6e
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249236"
---
# <a name="pattern-matching"></a>Dopasowanie wzorca

Wzorce testują, czy wartość ma określony *kształt*i mogą *wyodrębniać* informacje z wartości, gdy ma pasujący kształt. Dopasowywanie wzorców zapewnia bardziej zwięzłą składnię dla algorytmów, które są już używane dzisiaj. Algorytmy dopasowywania wzorców są już tworzą przy użyciu istniejącej składni. Piszesz `if` `switch` lub instrukcje, które testują wartości. Następnie, gdy te instrukcje są zgodne, wyodrębnić i użyć informacji z tej wartości. Nowe elementy składni są rozszerzeniami instrukcji, które znasz `is` `switch`już: i . Te nowe rozszerzenia łączą testowanie wartości i wyodrębnianie tych informacji.

W tym artykule przyjrzymy się nowej składni, aby pokazać, jak umożliwia czytelny, zwięzły kod. Dopasowywanie wzorców umożliwia idiomy, w których dane i kod są oddzielone, w przeciwieństwie do projektów obiektowych, w których dane i metody, które nimi manipulują, są ściśle powiązane.

Aby zilustrować te nowe idiomy, pracujmy ze strukturami reprezentującymi kształty geometryczne przy użyciu instrukcji dopasowywania szyku. Prawdopodobnie znasz hierarchie klas i tworzenie [metod wirtualnych i zastąpione metody](methods.md#inherited) dostosowywania zachowania obiektu na podstawie typu środowiska wykonawczego obiektu.

Te techniki nie są możliwe dla danych, które nie są zorganizowane w hierarchii klas. Gdy dane i metody są oddzielne, potrzebne są inne narzędzia. Nowe konstrukcje *dopasowywania wzorców* umożliwiają czystsze składni do badania danych i manipulowania przepływem sterowania na podstawie dowolnego warunku tych danych. Już piszesz `if` `switch` instrukcje i testuje wartość zmiennej. Piszesz `is` instrukcje, które testują typ zmiennej. *Dopasowanie wzorca* dodaje nowe możliwości do tych instrukcji.

W tym artykule zostanie zbudowana metoda obliczania obszaru o różnych kształtach geometrycznych. Ale zrobisz to bez uciekania się do technik obiektowych i tworzenia hierarchii klas dla różnych kształtów.
Zamiast tego użyjesz *dopasowania wzorca.*
Podczas przechodzenia przez ten przykład, kontrast ten kod z jak będzie on zorganizowany jako hierarchii obiektów. Gdy dane, które należy zbadać i manipulować nie jest hierarchią klas, dopasowywanie wzorców umożliwia eleganckie projekty.

Zamiast zaczynać od abstrakcyjnej definicji kształtu i dodawać różne określone klasy kształtów, zacznijmy od prostych definicji tylko danych dla każdego z kształtów geometrycznych:

[!code-csharp[ShapeDefinitions](../../samples/snippets/csharp/PatternMatching/Shapes.cs#01_ShapeDefinitions "Shape definitions")]

Z tych struktur napiszmy metodę, która oblicza obszar pewnego kształtu.

## <a name="the-is-type-pattern-expression"></a>Wyrażenie `is` wzorca typu

Przed C# 7.0, należy przetestować każdy typ `if` w `is` serii i instrukcji:

[!code-csharp[ClassicIsExpression](../../samples/snippets/csharp/PatternMatching/GeometricUtilities.cs#02_ClassicIsExpression "Classic type pattern using is")]

Ten kod powyżej jest klasycznym *wyrażeniem wzorca typu:* Testujesz zmienną, aby określić jej typ i podejmujesz inną akcję na podstawie tego typu.

Ten kod staje się prostszy przy użyciu rozszerzeń do wyrażenia, `is` aby przypisać zmienną, jeśli test zakończy się pomyślnie:

[!code-csharp[IsPatternExpression](../../samples/snippets/csharp/PatternMatching/GeometricUtilities.cs#03_IsPatternExpression "is pattern expression")]

W tej zaktualizowanej `is` wersji wyrażenie testuje zmienną i przypisuje ją do nowej zmiennej odpowiedniego typu. Należy również zauważyć, że `Rectangle` ta wersja `struct`zawiera typ, który jest . Nowe `is` wyrażenie działa z typami wartości, a także typami odwołań.

Reguły języka dla wyrażeń dopasowywania wzorców pomagają uniknąć nadużywania wyników wyrażenia dopasowania. W powyższym przykładzie `s`zmienne `c` `r` , i są tylko w zakresie i zdecydowanie `true` przypisane, gdy odpowiednie wyrażenia dopasowania wzorca mają wyniki. Jeśli spróbujesz użyć jednej zmiennej w innej lokalizacji, kod generuje błędy kompilatora.

Przeanalizujmy obie te reguły szczegółowo, począwszy od zakresu. Zmienna `c` jest w zakresie `else` tylko w `if` gałęzi pierwszej instrukcji. Zmienna `s` jest w zakresie `ComputeAreaModernIs`w metodzie . Dzieje się tak, ponieważ `if` każda gałąź instrukcji ustanawia oddzielny zakres dla zmiennych. Jednak sama `if` instrukcja nie. Oznacza to, że `if` zmienne zadeklarowane w `if` instrukcji znajdują się w tym samym zakresie co instrukcja (metoda w tym przypadku). To zachowanie nie jest specyficzne dla dopasowania wzorca, ale `if` jest `else` zdefiniowane zachowanie dla zakresów zmiennych i instrukcji.

Zmienne `c` i `s` są przypisywane, `if` gdy odpowiednie instrukcje są prawdziwe ze względu na zdecydowanie przypisany, gdy true mechanizmu.

> [!TIP]
> Przykłady w tym temacie używają zalecanej `is` konstrukcji, w której wyrażenie `true` dopasowania wzorca zdecydowanie przypisuje zmienną dopasowania w gałęzi `if` instrukcji.
> Można odwrócić logikę, mówiąc, `if (!(shape is Square s))` a zmienna `s` będzie `false` zdecydowanie przypisany tylko w gałęzi. Chociaż jest to prawidłowe C#, nie jest zalecane, ponieważ jest bardziej mylące, aby postępować zgodnie z logiką.

Te reguły oznaczają, że jest mało prawdopodobne, aby przypadkowo uzyskać dostęp do wyniku wyrażenia dopasowania wzorca, gdy ten wzorzec nie został spełniony.

## <a name="using-pattern-matching-switch-statements"></a>Używanie instrukcji `switch` dopasowywania wzorców

W miarę upływu czasu może być konieczne obsługiwanie innych typów kształtów. Wraz ze wzrostem liczby testujących warunków, okaże się, `is` że używanie wyrażeń dopasowywania wzorców może stać się uciążliwe. Oprócz wymagania `if` instrukcji dla każdego typu, który `is` chcesz sprawdzić, wyrażenia są ograniczone do testowania, jeśli dane wejściowe pasuje do jednego typu. W takim przypadku okaże się, `switch` że wyrażenia dopasowania wzorca staje się lepszym wyborem.

Tradycyjna `switch` instrukcja była wyrażeniem wzorca: obsługiwała stały wzorzec.
Można porównać zmienną z dowolną `case` stałą używaną w instrukcji:

[!code-csharp[ClassicSwitch](../../samples/snippets/csharp/PatternMatching/GeometricUtilities.cs#04_ClassicSwitch "Classic switch statement")]

Jedynym wzorcem obsługiwanym przez instrukcję `switch` był stały wzorzec. Ponadto był ograniczony do typów `string` liczbowych i typu.
Te ograniczenia zostały usunięte i można teraz `switch` napisać instrukcję przy użyciu wzorca typu:

[!code-csharp[Switch Type Pattern](../../samples/snippets/csharp/PatternMatching/GeometricUtilities.cs#05_SwitchTypePattern "Compute with `switch` expression")]

Instrukcja `switch` dopasowywania wzorców używa znanej składni dla deweloperów, którzy używali tradycyjnej instrukcji w stylu `switch` C. Każdy `case` jest oceniany i kod poniżej warunku, który pasuje do zmiennej wejściowej jest wykonywany. Wykonanie kodu nie może "przepaść" z jednego wyrażenia sprawy do następnego; składnia `case` instrukcji wymaga, aby `case` każdy koniec `break` `return`z `goto`, , lub .

> [!NOTE]
> Instrukcje, `goto` aby przejść do innej etykiety są prawidłowe tylko dla wzorca stałego (instrukcja classic switch).

Istnieją ważne nowe zasady `switch` regulujące oświadczenie. Ograniczenia dotyczące typu zmiennej w `switch` wyrażeniu zostały usunięte.
Każdy typ, `object` takich jak w tym przykładzie, mogą być używane. Wyrażenia sprawy nie są już ograniczone do wartości stałych. Usunięcie tego ograniczenia oznacza, że `switch` zmiana kolejności sekcji może zmienić zachowanie programu.

Gdy jest ograniczona do wartości `case` stałych, nie więcej `switch` niż jedna etykieta może odpowiadać wartości wyrażenia. Połącz to z `switch` regułą, że każda sekcja nie może przechodzić do następnej sekcji, a następnie, że `switch` sekcje mogą być zmieniane w dowolnej kolejności bez wpływu na zachowanie.
Teraz, z bardziej `switch` uogólnionymi wyrażeniami, liczy się kolejność każdej sekcji. Wyrażenia `switch` są oceniane w kolejności tekstowej. Wykonanie przenosi się `switch` do pierwszej `switch` etykiety, która pasuje do wyrażenia.  
Sprawa `default` zostanie wykonana tylko wtedy, gdy żadne inne etykiety przypadków nie są zgodne. Sprawa `default` jest oceniana jako ostatnia, niezależnie od kolejności tekstowej. Jeśli nie ma `default` przypadku, a żadna z innych `case` instrukcji dopasowania, `switch` wykonanie jest kontynuowane w instrukcji po instrukcji. Żaden z `case` kodów etykiet nie jest wykonywany.

## <a name="when-clauses-in-case-expressions"></a>`when`klauzule `case` w wyrażeniach

Dla tych kształtów, które mają obszar 0, `when` można `case` tworzyć specjalne przypadki, używając klauzuli na etykiecie. Kwadrat o długości bocznej 0 lub okrąg o promieniu 0 ma obszar 0. Można określić ten `when` warunek `case` przy użyciu klauzuli na etykiecie:  

[!code-csharp[ComputeDegenerateShapes](../../samples/snippets/csharp/PatternMatching/GeometricUtilities.cs#07_ComputeDegenerateShapes "Compute shapes with 0 area")]

Ta zmiana pokazuje kilka ważnych punktów dotyczących nowej składni. Po pierwsze, wiele `case` etykiet można `switch` zastosować do jednej sekcji. Blok instrukcji jest wykonywany, gdy `true`którykolwiek z tych etykiet jest . W tym przypadku, `switch` jeśli wyrażenie jest okrąg lub kwadrat z 0 obszar, metoda zwraca stałą 0.

W tym przykładzie wprowadzono dwie `case` różne zmienne `switch` w dwóch etykiet dla pierwszego bloku. Należy zauważyć, że `switch` instrukcje w tym bloku `c` nie używają zmiennych `s` (dla okręgu) lub (dla kwadratu).
Żadna z tych zmiennych nie `switch` jest zdecydowanie przypisana w tym bloku.
Jeśli którykolwiek z tych przypadków są zgodne, wyraźnie jedna ze zmiennych została przypisana.
Jednak nie można stwierdzić, *który* został przypisany w czasie kompilacji, ponieważ każdy przypadek może być zgodny w czasie wykonywania. Z tego powodu w większości `case` razy, gdy używasz wielu etykiet dla tego `case` samego bloku, nie wprowadzisz nowej `when` zmiennej w instrukcji lub użyjesz tylko zmiennej w klauzuli.

Po dodaniu tych kształtów o obszarze 0 dodajmy jeszcze kilka typów kształtów: prostokąt i trójkąt:

[!code-csharp[AddRectangleAndTriangle](../../samples/snippets/csharp/PatternMatching/GeometricUtilities.cs#09_AddRectangleAndTriangle "Add rectangle and triangle")]

 Ten zestaw zmian `case` dodaje etykiety dla zdegenerowanych przypadków oraz etykiety i bloki dla każdego z nowych kształtów.

Na koniec możesz dodać `null` sprawę, aby upewnić `null`się, że argument nie jest:

[!code-csharp[NullCase](../../samples/snippets/csharp/PatternMatching/GeometricUtilities.cs#10_NullCase "Add null case")]

Specjalne zachowanie `null` dla wzorca jest `null` interesujące, ponieważ stała we wzorcu nie ma typu, ale może być konwertowana na dowolny typ odwołania lub typ wartości nullable. Zamiast konwertować a `null` do dowolnego typu, `null` język definiuje, że wartość nie będzie pasować do wzorca typu, niezależnie od typu skompilowania zmiennej. To zachowanie sprawia, że `switch` nowy `is` wzorzec typu opartego jest zgodny z instrukcją: `is` instrukcje zawsze zwracają, `false` gdy sprawdzana wartość jest `null`. Jest to również prostsze: po sprawdzeniu typu nie trzeba dodatkowego sprawdzania wartości null. Widać, że z faktu, że nie ma żadnych null kontroli w każdym z bloków sprawy powyżej: nie są one konieczne, ponieważ dopasowanie wzorca typu gwarantuje wartość inną niż null.

## <a name="var-declarations-in-case-expressions"></a>`var`deklaracje `case` w wyrażeniach

Wprowadzenie `var` jako jedno z wyrażeń dopasowania wprowadza nowe reguły do dopasowania wzorca.

Pierwsza reguła jest, że deklaracja `var` jest zgodna z regułami wnioskowania o typie normalnym: Typ jest wywnioskowany jako typ statyczny wyrażenia switch. Z tej reguły typ zawsze pasuje.

Druga reguła jest, że deklaracja `var` nie ma null sprawdzić, że inne wyrażenia wzorca typu obejmują. Oznacza to, że zmienna może mieć wartość null, a w takim przypadku konieczne jest sprawdzenie wartości null.

Te dwie reguły oznaczają, że `var` w `case` wielu przypadkach deklaracja `default` w wyrażeniu spełnia te same warunki co wyrażenie.
Ponieważ każda sprawa nie domyślna `default` jest `default` preferowana w przypadku, sprawa nigdy nie zostanie wykonana.

> [!NOTE]
> Kompilator nie emituje ostrzeżenie w `default` tych przypadkach, gdy sprawa została napisana, ale nigdy nie zostanie wykonana. Jest to zgodne `switch` z bieżącym zachowaniem instrukcji, w którym wymieniono wszystkie możliwe przypadki.

Trzecia reguła wprowadza zastosowania, `var` w których przypadek może być przydatny. Wyobraź sobie, że robisz dopasowanie wzorca, gdzie dane wejściowe jest ciągiem i szukasz znanych wartości poleceń. Możesz napisać coś takiego:

[!code-csharp[VarCaseExpression](../../samples/snippets/csharp/PatternMatching/Program.cs#VarCaseExpression "use a var case expression to filter white space")]

Przypadek `var` jest `null`zgodny, pusty ciąg lub dowolny ciąg, który zawiera tylko biały znak. Należy zauważyć, że poprzedni `?.` kod używa operatora, aby upewnić <xref:System.NullReferenceException>się, że nie przypadkowo zgłosić . Sprawa `default` obsługuje wszelkie inne wartości ciągu, które nie są zrozumiałe przez tego parsera polecenia.

Jest to jeden z przykładów, `var` w którym można `default` rozważyć wyrażenie sprawy, które różni się od wyrażenia.

## <a name="conclusions"></a>Wnioski

*Konstrukcje dopasowywania wzorców* umożliwiają łatwe zarządzanie przepływem sterowania między różnymi zmiennymi i typami, które nie są powiązane z hierarchią dziedziczenia. Można również kontrolować logikę, aby użyć dowolnego warunku testowego na zmiennej. Umożliwia wzorce i idiomy, które będą potrzebne częściej podczas tworzenia większej liczby aplikacji rozproszonych, gdzie dane i metody, które manipulują tymi danymi są oddzielne. Można zauważyć, że struktury kształtu używane w tym przykładzie nie zawierają żadnych metod, tylko właściwości tylko do odczytu.
Dopasowanie wzorca działa z dowolnym typem danych. Piszesz wyrażenia, które badają obiekt i podejmujesz decyzje przepływu sterowania na podstawie tych warunków.

Porównaj kod z tego przykładu z projektem, który wynika `Shape` z tworzenia hierarchii klas dla abstrakcyjnych i specyficznych kształtów pochodnych, z których każdy ma własną implementację metody wirtualnej do obliczania obszaru. Często okaże się, że wyrażenia dopasowywania wzorców może być bardzo przydatne narzędzie podczas pracy z danymi i chcesz oddzielić obawy dotyczące magazynu danych od problemów zachowania.

## <a name="see-also"></a>Zobacz też

- [Samouczek: Rozszerzanie typów danych za pomocą funkcji dopasowywania wzorców](tutorials/pattern-matching.md)
