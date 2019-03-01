---
title: Dopasowanie wzorca — Przewodnik po języku C#
description: Dowiedz się więcej o wyrażeniach w języku C# dopasowania do wzorca
ms.date: 01/24/2017
ms.assetid: 1e575c32-2e2b-4425-9dca-7d118f3ed15b
ms.openlocfilehash: eccc982c94a1f124d7250e1795a44d696e43a53c
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56969985"
---
# <a name="pattern-matching"></a>Dopasowanie wzorca

Wzorce testowania, czy wartość nie ma określonej *kształt*i może *wyodrębnić* informacji z wartości, gdy ma ona odpowiedniego kształtu. Dopasowanie wzorca zapewnia bardziej zwięzły widok składni dla algorytmów używanych już dziś. Można już utworzyć algorytmami przy użyciu istniejących Składnia dopasowania do wzorca. Piszesz `if` lub `switch` instrukcji, które testują wartości. Następnie gdy te wyrażenia są zgodne, wyodrębnić i korzystać z tej wartości. Nowe elementy składni są rozszerzeniami do instrukcji, które znasz już: `is` i `switch`. Te nowe rozszerzenia łączyć testowania wartość i wyodrębnianie informacji.

W tym temacie omówimy nowej składni, aby pokazać, jak umożliwia stosowanie kodu czytelne i zwięzłe. Dopasowanie wzorca umożliwia idiomy, w którym dane i kodu są rozdzielone, w przeciwieństwie do projektów zorientowana obiektowo, gdzie danych i metod, które manipulować nimi są ściśle powiązane.

Aby zilustrować te nowe idiomy, Użyjmy struktur, które reprezentują kształty geometryczne, przy użyciu instrukcji dopasowania do wzorca. Znasz prawdopodobnie tworzenia hierarchii klas i tworzenie [metod wirtualnych i przesłonięte metody](methods.md#inherited) do dostosowywania zachowania obiektu na podstawie typu środowiska uruchomieniowego obiektu.

Techniki te nie są możliwe dla danych, które nie jest umieszczonymi w hierarchii klas. Danych i metod są oddzielone, należy się inne narzędzia. Nowy *dopasowywania do wzorca* konstrukcji Włącz oczyszczarki składni do badania danych i manipulowania przepływ sterowania w oparciu o dowolny warunek tych danych. Już zapisu `if` instrukcji i `switch` testu, wartość zmiennej. Piszesz `is` instrukcji, które testują typ zmiennej. *Dopasowanie wzorca* dodaje nowe możliwości do tych instrukcji.

W tym temacie będziesz tworzyć metodę, która oblicza obszaru różnych kształtów geometrycznych. Jednak wykonasz bez konieczności uciekania się do technik zorientowana obiektowo i tworzenie hierarchii klas dla różnych kształtów.
Użyjesz *dopasowywania do wzorca* zamiast tego.
Podczas wykonywania kroków w tym przykładzie, natomiast ten kod przy użyciu jak będzie mieć strukturę jako hierarchię obiektów. Gdy danych należy zapytań i manipulowania nimi nie jest hierarchii klas, dopasowywania do wzorca umożliwia bardzo elegancki projekty.

Zamiast począwszy od definicji interfejsu abstrakcyjne kształtu, a następnie dodawania innego kształtu określonych klas, Zacznijmy zamiast prostych danych tylko definicje dla każdego z kształtów geometrycznych:

[!code-csharp[ShapeDefinitions](../../samples/csharp/PatternMatching/Shapes.cs#01_ShapeDefinitions "Shape definitions")]

Z tych struktur Napiszmy metodę, która oblicza obszaru niektóre kształtu.

## <a name="the-is-type-pattern-expression"></a>`is` Wpisz wyrażenie wzorca

Przed C# 7.0, będziesz potrzebować w celu przetestowania każdego typu w szeregu `if` i `is` instrukcji:

[!code-csharp[ClassicIsExpression](../../samples/csharp/PatternMatching/GeometricUtilities.cs#02_ClassicIsExpression "Classic type pattern using is")]

Powyższy kod to wyrażenie klasycznego *wpisz wzór*: Jesteś badania zmiennej, aby określić jej typ i wykonywania różnych akcji, na podstawie tego typu.

Ten kod staje się prostszy przy użyciu rozszerzeń `is` wyrażenie można przypisać zmiennej Jeśli test zakończy się pomyślnie:

[!code-csharp[IsPatternExpression](../../samples/csharp/PatternMatching/GeometricUtilities.cs#03_IsPatternExpression "is pattern expression")]

W tej wersji zaktualizowano `is` wyrażenie sprawdza zmienną i przypisuje go do nowej zmiennej odpowiedniego typu. Ponadto Zwróć uwagę, że ta wersja zawiera `Rectangle` typ, który jest `struct`. Nowy `is` wyrażenie współpracuje z typów wartości, a także typy odwołań.

Język reguł w wyrażeniach dopasowania wzorca pomóc w uniknięciu niewłaściwie wyniki wyrażenia dopasowania. W przykładzie powyżej zmiennych `s`, `c`, i `r` znajdują się tylko w zakresie i zdecydowanie przypisana, gdy wyrażenia dopasowania wzorca odpowiednich `true` wyników. Jeśli spróbujesz użyć jednej zmiennej w innej lokalizacji, kod generuje błędy kompilatora.

Przeanalizujmy oba te zasady szczegółowo, począwszy od zakresu. Zmienna `c` znajduje się w zakresie tylko w `else` gałęzi pierwszego `if` instrukcji. Zmienna `s` znajduje się w zasięgu w metodzie `ComputeAreaModernIs`. To dlatego, że każda gałąź `if` instrukcji ustanawia oddzielny zakres zmiennych. Jednak `if` instrukcji, sama nie jest. Oznacza to, że zmienne zadeklarowane w `if` instrukcji znajdują się w tym samym zakresie co `if` — instrukcja (metoda w tym przypadku.) To zachowanie nie jest specyficzna dla dopasowywania do wzorca, ale jest zdefiniowany zachowanie dla zmiennej zakresów i `if` i `else` instrukcji.

Zmienne `c` i `s` są przypisane, kiedy odpowiednie `if` instrukcje są spełnione z powodu zdecydowanie przypisany podczas true mechanizm.

> [!TIP]
> Przykłady w tym temacie Użyj zalecanych konstrukcji, którego dopasowania do wzorca `is` wyrażenie zdecydowanie przypisuje zmiennej dopasowania w `true` gałęzi `if` instrukcji.
> Logika może odtworzyć mówiąc `if (!(shape is Square s))` , a zmienna `s` mogłoby być zdecydowanie przypisywany tylko w `false` gałęzi. Gdy ta operacja jest nieprawidłowa C#, nie zaleca się ponieważ jest bardziej skomplikowane wykonać logikę.

Te reguły oznacza, że masz mało prawdopodobne, aby przypadkowo dostęp wynik wyrażenia dopasowania wzorca, gdy ten wzorzec nie zostało spełnione.

## <a name="using-pattern-matching-switch-statements"></a>Za pomocą dopasowywania do wzorca `switch` instrukcji

Gdy czasie, może być konieczne obsługuje inne typy kształtów. Wraz z rozwojem liczbę warunków, które testujesz znajdziesz w tym za pomocą `is` wyrażeniach dopasowania do wzorca może stać się zbyt skomplikowana. Oprócz wymagające `if` instrukcji dla każdego typu, którego chcesz sprawdzić, `is` wyrażenia są ograniczone do testowania, jeśli wartość wejściowa pasuje do jednego typu. W tym przypadku będzie zauważysz, że `switch` wyrażenia dopasowania wzorca, staje się lepszym rozwiązaniem. 

Tradycyjne `switch` instrukcja została wyrażenia wzorca: ono obsługiwane wzór stałej.
Można porównać zmienną dowolną stałą używane w `case` instrukcji:

[!code-csharp[ClassicSwitch](../../samples/csharp/PatternMatching/GeometricUtilities.cs#04_ClassicSwitch "Classic switch statement")]

Z wzorcem jedynym obsługiwanym przez `switch` instrukcja została wzór stałej. Dodatkowo została ograniczona do liczbowych typów i `string` typu.
Te ograniczenia zostały usunięte, a teraz możesz zapisać `switch` instrukcji przy użyciu wzorca typu:

[!code-csharp[Switch Type Pattern](../../samples/csharp/PatternMatching/GeometricUtilities.cs#05_SwitchTypePattern "Compute with `switch` expression")]

Dopasowanie wzorca `switch` instrukcja używa dobrze znanej składni dla deweloperów, którzy korzystali z tradycyjnych stylu C `switch` instrukcji. Każdy `case` jest obliczane i wykonywany jest kod, pod warunkiem, że zmienna wejściowa pasuje. Wykonywanie kodu nie może "przechodzić" od jednego wyrażenia case dalej; Składnia `case` instrukcja wymaga każdy `case` kończyć `break`, `return`, lub `goto`.

> [!NOTE]
> `goto` Instrukcji, aby przejść do innej etykiety są prawidłowe tylko dla wzór stałej (instrukcja switch klasycznego).

Istnieją istotne nowe zasady `switch` instrukcji. Ograniczenia dotyczące typu zmiennej w `switch` wyrażenia zostały usunięte.
Dowolny typ, taki jak `object` w tym przykładzie, może być używany. Wyrażenia case nie są już ograniczona do wartości stałych. Usunięcie tego ograniczenia oznacza, że zmiana kolejności `switch` sekcje mogą zmienić zachowanie programu.

Gdy ograniczony do wartości stałych, ma więcej niż jeden `case` etykieta może być zgodna z wartością `switch` wyrażenia. Połączenie z regułą, co `switch` sekcji nie należy przechodzić do następnej sekcji, a a następnie, który `switch` sekcje mogą być nieco inaczej rozmieszczone w dowolnej kolejności bez wywierania wpływu na zachowanie.
Obecnie z bardziej powszechny `switch` wyrażeń, kolejność, w każdej sekcji dla Ciebie ważne. `switch` Wyrażenia są obliczane w kolejności tekstową. Wykonanie przenoszone jest do pierwszego `switch` etykietę, która odpowiada `switch` wyrażenia.  
Należy pamiętać, że `default` przypadku tylko zostaną wykonane, jeśli pasuje inne etykiety wielkości liter. `default` Przypadek jest oceniany ostatnio, niezależnie od ich kolejność tekstową. W przypadku nie `default` wielkość liter i żaden z innych `case` instrukcje są zgodne, wykonywanie jest kontynuowane po instrukcja po słowie `switch` instrukcji. Żaden z `case` etykiety Kod jest wykonywany.

## <a name="when-clauses-in-case-expressions"></a>`when` klauzule `case` wyrażeń

Możesz wprowadzić specjalne przypadki te kształty, które mają obszaru 0 za pomocą `when` klauzuli w `case` etykiety. Kwadratu o długości boku 0 lub koła o promieniu 0 ma obszar 0. Określasz, przy użyciu warunku `when` klauzuli w `case` etykiety:  

[!code-csharp[ComputeDegenerateShapes](../../samples/csharp/PatternMatching/GeometricUtilities.cs#07_ComputeDegenerateShapes "Compute shapes with 0 area")]

Ta zmiana pokazuje kilka ważnych punktów o nowej składni. Po pierwsze, wiele `case` etykiety mogą być stosowane do jednej `switch` sekcji. Blok instrukcji jest wykonywana po jest dowolny z tych etykiet `true`. W tym wypadku Jeśli `switch` wyrażenie jest okrąg lub pole z obszaru 0, metoda zwraca wartość stała 0.

W tym przykładzie przedstawiono dwie różne zmienne w dwóch `case` etykiet w pierwszym `switch` bloku. Należy zauważyć, że instrukcje w tym `switch` bloku nie należy używać zmiennych albo `c` (dla okręgu) lub `s` (w przypadku kwadrat).
Żadna z tych zmiennych jest zdecydowanie przypisana w tym `switch` bloku.
Jeśli jeden z tych przypadków są zgodne, wyraźnie zmiennych zostały przypisane.
Jednak nie jest możliwe Poinformuj *który* ma przypisane w czasie kompilacji, ponieważ w obu przypadkach może być zgodny w czasie wykonywania. Z tego powodu większości przypadków Jeśli używanych jest wiele `case` etykiety dla tego samego bloku, nie będzie wprowadzenie nowej zmiennej w `case` instrukcji lub możesz tylko używać zmiennej w `when` klauzuli.

O dodaniu te kształty z obszaru 0 Dodajmy kilka większą liczbę typów kształtu: prostokąt i trójkąta:

[!code-csharp[AddRectangleAndTriangle](../../samples/csharp/PatternMatching/GeometricUtilities.cs#09_AddRectangleAndTriangle "Add rectangle and triangle")]

 Dodaje ten zestaw zmian `case` etykiet w przypadku wymiaru degeneracji i etykiet oraz bloków dla każdego nowe kształty. 

Na koniec możesz dodać `null` przypadek, aby upewnić się, argument nie jest `null`:

[!code-csharp[NullCase](../../samples/csharp/PatternMatching/GeometricUtilities.cs#10_NullCase "Add null case")]

Specjalnego zachowania w przypadku `null` wzorzec jest interesująca ponieważ stała `null` we wzorcu nie ma typu, ale mogą być konwertowane na dowolnym typem referencyjnym lub typ dopuszczający wartość null. Zamiast przekonwertować `null` do dowolnego typu, języka definiuje, które `null` wartości nie będą zgodne wpisz wzór, niezależnie od typu zmiennej w czasie kompilacji. To zachowanie sprawia, że nowe `switch` na podstawie typu wzorzec zgodny z `is` instrukcji: `is` instrukcji zawsze zwracają `false` gdy wartość sprawdzany jest `null`. Również jest prostsza: po sprawdzeniu typ, nie potrzebujesz dodatkowe sprawdzanie wartości null. Widać, że z faktu, że nie istnieją żadne null sprawdza, czy w żadnym przypadku bloków powyższe przykłady: nie są konieczne, ponieważ pasujących do wzorca typu gwarantuje wartości innej niż null.

## <a name="var-declarations-in-case-expressions"></a>`var` deklaracje w `case` wyrażeń

Wprowadzenie `var` jako jedno z wyrażeń dopasowanie wprowadza nowe reguły do dopasowania do wzorca.

Pierwsza reguła jest to, że `var` znajduje się za deklaracją typ reguły wnioskowania: Typ jest wnioskowany być typu statycznego wyrażenia switch. Od tej zasady zawsze zgodny typ.

Druga reguła jest to, że `var` deklaracja nie ma sprawdzanie wartości null, który zawiera inne typu wzorzec wyrażenia. Oznacza to, zmienna może mieć wartości null i sprawdzanie wartości null jest to konieczne w takiej sytuacji.

Te dwie reguły oznaczają, że w wielu przypadkach `var` deklaracji w `case` wyrażenie jest zgodne z warunkami tej samej jako `default` wyrażenia.
Ponieważ każdy przypadek, inny niż domyślny jest preferowana względem `default` przypadku `default` przypadek nigdy nie zostanie wykonana.

> [!NOTE]
> Kompilator nie emituje ostrzeżenia w przypadkach, gdzie `default` przypadek został zapisany, ale nigdy nie zostanie wykonana. Jest to zgodne z bieżącą `switch` zachowanie instrukcji, gdzie zostały wymienione wszystkich możliwych przypadków.

Trzecia reguła wprowadza używa gdzie `var` przypadków mogą być przydatne. Wyobraź sobie robią dopasowania do wzorca, w którym dane wejściowe to ciąg i wyszukiwanie wartości znane polecenie. Można napisać mniej więcej tak:

[!code-csharp[VarCaseExpression](../../samples/csharp/PatternMatching/Program.cs#VarCaseExpression "use a var case expression to filter white space")]

`var` Zamierzone, Zapisz dopasowania `null`, ciągiem pustym ani dowolny ciąg, który zawiera tylko znak odstępu. Należy zauważyć, że w poprzednim kodzie użyto `?.` operatora, aby upewnić się, że nie zostanie przypadkowo zgłoszony <xref:System.NullReferenceException>. `default` Przypadek obsługuje inne wartości ciągu, które nie są zrozumiałe analizatora tego polecenia.

Jest jednym z przykładów których warto wziąć pod uwagę `var` zamierzone, Zapisz wyrażenie, które różni się od `default` wyrażenia.

## <a name="conclusions"></a>Wnioski

*Konstrukcje dopasowywania do wzorca* umożliwiają łatwe zarządzanie przepływ sterowania między różne zmienne i typy, które nie są powiązane przez hierarchię dziedziczenia. Można też sterować logikę w celu użycia dowolny warunek, który można przetestować na zmiennej. Umożliwia on wzorce i idiomy, które będziesz potrzebować więcej często, jak tworzyć więcej aplikacji rozproszonych, w którym dane i metody manipulujące te dane są oddzielone. Można zauważyć, strukturach kształtu, używane w tym przykładzie nie zawierają żadnych metod właściwości tylko do odczytu.
Dopasowywanie wzorca działa z dowolnego typu danych. Pisanie wyrażeń, które zbadać obiektu i decyzje dotyczące kontroli przepływu na podstawie tych warunków.

Porównać kod z tego przykładu z projekt, który z tworzenia hierarchii klas dla abstrakcyjną `Shape` i określonych pochodne kształty o zapewniali własną implementację metody wirtualnej do obliczenia. Często okazuje wzorzec dopasowania wyrażenia może być bardzo przydatne narzędzie podczas pracy z danymi i chcesz oddzielić dotyczy magazynu danych od wątpliwości zachowanie.

