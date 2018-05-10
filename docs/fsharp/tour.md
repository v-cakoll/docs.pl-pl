---
title: 'Samouczek języka F #'
description: 'Sprawdź, czy niektóre główne funkcje programowania ten samouczek z przykładów kodu języka F #.'
ms.date: 02/28/2018
ms.openlocfilehash: 2ce251b90d5c202996e0b1673e8f7f378a38af5f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="tour-of-f"></a>Samouczek języka F # #

Najlepszym sposobem, aby dowiedzieć się więcej o języku F # jest do odczytu i zapisu w kodzie języka F #.  W tym artykule będzie działać jako samouczek niektóre z kluczowych funkcji usługi języka F # i podamy niektórych wstawki kodu, które mogą być wykonywane na tym komputerze.  Aby dowiedzieć się więcej o konfigurowaniu Środowisko deweloperskie, zapoznaj się [wprowadzenie](tutorials/getting-started/index.md).

Istnieją dwa podstawowe pojęcia języka F #: funkcji i typów.  Ten samouczek zostanie wyróżnianie funkcji języka, które należą do tych dwóch pojęć.

## <a name="functions-and-modules"></a>Funkcje i modułów

Większość podstawowych części programu F # ***funkcje*** podzielone na ***modułów***.  [Funkcje](language-reference/functions/index.md) wykonywania pracy na dane wejściowe, aby tworzyć dane wyjściowe i są zorganizowane w obszarze [moduły](language-reference/modules.md), które są podstawowy sposób grupowania elementów w F #.  Są definiowane przy użyciu [ `let` powiązania](language-reference/functions/let-bindings.md), którego nazwę funkcji i określić argumenty.

[!code-fsharp[BasicFunctions](../../samples/snippets/fsharp/tour.fs#L101-L133)]

`let` powiązania są również, jak można powiązać wartości nazwy, podobne do zmiennych w innych językach.  `let` powiązania są ***niezmienne*** domyślnie, co oznacza, że po wartości lub funkcji jest powiązany z nazwą, nie można zmienić w miejscu.  Jest to w przeciwieństwie do zmiennych w innych językach, które są ***modyfikowalną***, co oznacza ich wartości można zmienić w dowolnym momencie w czasie.  Jeśli potrzebujesz modyfikowalną powiązanie, możesz użyć `let mutable ...` składni.

[!code-fsharp[Immutability](../../samples/snippets/fsharp/tour.fs#L75-L94)]

## <a name="numbers-booleans-and-strings"></a>Liczb, wartości logiczne i ciągi

Jako języka .NET, F # obsługuje tego samego podstawowego [typów pierwotnych](language-reference/primitive-types.md) występujące w .NET.

Oto, jak różne typy liczbowe są reprezentowane w języku F #:

[!code-fsharp[Numbers](../../samples/snippets/fsharp/tour.fs#L49-L68)]

Oto, jakie wartości logiczne i wykonywania podstawowych logikę warunkową wygląda następująco:

[!code-fsharp[Bools](../../samples/snippets/fsharp/tour.fs#L142-L152)]

A Oto jakie basic [ciąg](language-reference/strings.md) manipulowania wygląda następująco:

[!code-fsharp[Strings](../../samples/snippets/fsharp/tour.fs#L158-L180)]

## <a name="tuples"></a>Krotki

[Krotki](language-reference/tuples.md) są nowego kontraktu w języku F #.  Są one grupowania bez nazwy, ale uporządkowanych wartości, które mogą być traktowane jako same wartości.  Należy traktować ich jako wartości, które są agregowane z innych wartości.  Mają wiele zastosowań, takich jak wygodnie zwracanie wartości wielu z funkcją lub grupowanie wartości dla niektórych wygody ad hoc.

[!code-fsharp[Tuples](../../samples/snippets/fsharp/tour.fs#L186-L203)]

Począwszy od F # 4.1, można również utworzyć `struct` spójnych kolekcji.  Te również współdziałać pełni C# 7/Visual Basic 15 krotek, które są również `struct` spójnych kolekcji:

[!code-fsharp[Tuples](../../samples/snippets/fsharp/tour.fs#L205-L218)]

Należy zauważyć, że ponieważ `struct` krotek są typy wartości, nie można niejawnie przekonwertować na odwołania krotek, albo na odwrót.  Należy jawnie przekonwertować między krotka odwołanie i struktury.

## <a name="pipelines-and-composition"></a>Potoki i kompozycji

Przekaż w potoku operatory (`|>`, `<|`, `||>`, `<||`, `|||>`, `<|||`) i operatory kompozycji (`>>` i `<<`) są często używane podczas przetwarzania danych w języku F #.  Są to funkcje, które pozwalają na wprowadzenie "potoki" funkcji w sposób elastyczny.  Poniższym przykładzie przedstawiono sposób użytkownik może skorzystać z tych operatorów, aby utworzyć prosty potoku funkcjonalności.

[!code-fsharp[Pipelines](../../samples/snippets/fsharp/tour.fs#L227-L300)]

Powyższym przykładzie wprowadzone korzystanie z wielu funkcji języka F #, łącznie z funkcji przetwarzania listy, funkcje najwyższej jakości i [aplikacja częściowa](language-reference/functions/index.md#partial-application-of-arguments).  Chociaż głębokie opis każdego z tych pojęć może stać się nieco zaawansowanych, powinno być jasne, jak łatwo można używać funkcji do przetwarzania danych, tworząc potoków.

## <a name="lists-arrays-and-sequences"></a>List, tablic i sekwencji

List, tablic i sekwencji są trzy typy kolekcji podstawowej biblioteki podstawowej F #.

[Wyświetla listę](language-reference/lists.md) są uporządkowane, niezmienne kolekcje elementów tego samego typu.  Są one pojedynczo połączone list, co oznacza, że są przeznaczone dla wyliczenia, ale niską wyborem w przypadku dostęp losowy i łączenia, gdy są one duże.  To w przeciwieństwie do listy w innych popularnych języków, które zwykle nie używać listy pojedynczo połączony do reprezentowania list.

[!code-fsharp[Lists](../../samples/snippets/fsharp/tour.fs#L309-L359)]

[Tablice](language-reference/arrays.md) są stałym rozmiarze, *modyfikowalną* kolekcji elementów tego samego typu.  Obsługuje szybkiego losowego dostępu do elementów i szybsze niż F # listy, ponieważ są one tylko ciągłych bloków pamięci.

[!code-fsharp[Arrays](../../samples/snippets/fsharp/tour.fs#L368-L407)]

[Sekwencje](language-reference/sequences.md) logicznej serii elementów, wszystkie tego samego typu.  Są to typu bardziej ogólne niż list i tablic, może być "Widok" w ciągu logicznych elementów.  One również wyróżniające ponieważ może on być ***opóźnieniem***, co oznacza, że elementy można obliczyć tylko wtedy, gdy są potrzebne.

[!code-fsharp[Sequences](../../samples/snippets/fsharp/tour.fs#L418-L452)]

## <a name="recursive-functions"></a>Funkcje rekursywne

Przetwarzanie kolekcji lub sekwencje elementów jest zazwyczaj wykonywane z [rekursji](language-reference/functions/index.md#recursive-functions) w języku F #.  Mimo że F # obsługuje dla pętli i imperatywnych programowania, rekursji jest preferowana, ponieważ możliwe jest łatwiejsze zagwarantować poprawne.

>[!NOTE]
Poniższy przykład korzysta z dopasowywania do wzorca za pomocą `match` wyrażenia.  Ta konstrukcja podstawowych jest uwzględnione w dalszej części tego artykułu.

[!code-fsharp[RecursiveFunctions](../../samples/snippets/fsharp/tour.fs#L461-L500)]

F # ma również pełną obsługę optymalizację wywołania Tail, czyli sposób, aby zoptymalizować wywołania cykliczne, dzięki czemu są one tak szybko jak konstrukcji pętli.

## <a name="record-and-discriminated-union-types"></a>Rekord i typy Unii rozłącznych

Rekord złożenia typów są dwa typy podstawowe dane używane w kodzie języka F # i są zazwyczaj najlepszym sposobem do reprezentowania danych w programie F #.  Mimo że z tego powodu są podobne do klas w innych językach, jednym z ich podstawowe różnice jest czy mają one semantykę równości strukturalnej.  To oznacza, że są one "natywnie" można porównać i równości jest proste — wystarczy Sprawdź, czy jeden taki sam jak inny.

[Rejestruje](language-reference/records.md) są agregacji nazwanych wartości członkom opcjonalne (takie jak metody).  Jeśli znasz języka C# lub języka Java, następnie te powinny możesz podobny do POCOs lub Pojo — tak w przypadku równości strukturalnej i mniej procedury.

[!code-fsharp[Records](../../samples/snippets/fsharp/tour.fs#L507-L559)]

Począwszy od F # 4.1, może także reprezentować rekordów jako `struct`s.  Jest to zrobić za pomocą `[<Struct>]` atrybutu:

[!code-fsharp[Records](../../samples/snippets/fsharp/tour.fs#L561-L568)]

[Suma rozłączna unie (DUs)](language-reference/discriminated-unions.md) wartości, które mogą być liczba nazwanych formularze lub przypadków.  Dane przechowywane w typie może być jednym z kilku odrębnych wartości.

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L575-L631)]

Można również użyć DUs jako *jeden przypadek Unii Suma rozłączna*, aby pomóc w domenie modelowania w typach pierwotnych.  Często, ciągi i innych typów pierwotnych są używane do reprezentowania coś, a w związku z tym są podane w szczególności znaczenie.  Jednak przy użyciu pierwotnych reprezentację danych może spowodować przez pomyłkę przypisywanie niepoprawną wartość!  Reprezentujących poszczególnych typów informacji jako różne jeden przypadek Unii mogą wymusić poprawności w tym scenariuszu.

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L633-L654)]

Zgodnie z powyższym przykładzie pokazano, można pobrać wartości podstawowej w pojedynczym przypadku Suma rozłączna Unii, należy je jawnie odkodowania.

Ponadto DUs obsługują także cykliczne definicje umożliwia łatwe reprezentują drzewa i z założenia cykliczne danych.  Na przykład poniżej przedstawiono sposób reprezentują drzewa binarnego wyszukiwania z `exists` i `insert` funkcji.

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L656-L683)]

Ponieważ DUs umożliwiają reprezentują strukturze cyklicznej drzewa w typie danych, korzysta z tej strukturze cyklicznej jest proste i gwarantuje poprawności.  Jest też obsługiwana w wzorca dopasowania, jak pokazano poniżej.

Ponadto może reprezentować DUs jako `struct`s `[<Struct>]` atrybutu:

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L685-L696)]

Istnieją dwie rzeczy, należy wziąć pod uwagę, gdy w ten sposób:

1. Struktura DU nie mogą być zdefiniowane cyklicznie.
2. Struktura DU muszą mieć unikatowe nazwy dla każdego z jego przypadków.

Nieprzestrzeganie powyższych spowoduje błąd kompilacji.

## <a name="pattern-matching"></a>Dopasowanie wzorca

[Wzorzec dopasowywania](language-reference/pattern-matching.md) jest funkcją języka F #, dzięki czemu poprawność obsługi typów F #.  W powyższych przykładach można zauważyć dość nieco `match x with ...` składni.  Ta konstrukcja umożliwia kompilatora, w którym można poznać "kształtu" typy danych, aby wymusić na konta dla wszystkich możliwych przypadków, w przypadku używania typu danych, przez co to jest znany jako wyczerpujący dopasowanie wzorca.  Jest bardzo zaawansowaną pod kątem poprawności i sprytnie służy do "Podnieś" co byłby wątpliwości dotyczących środowiska uruchomieniowego w czasie kompilacji.

[!code-fsharp[PatternMatching](../../samples/snippets/fsharp/tour.fs#L705-L739)]

Można również użyć skrótu `function` konstrukcja dopasowywanie do wzorców, który jest przydatny podczas pisania funkcje, które powodują, że użycie [aplikacja częściowa](language-reference/functions/index.md#partial-application-of-arguments):

[!code-fsharp[PatternMatching](../../samples/snippets/fsharp/tour.fs#L741-L759)]

Coś można zauważyć jest użycie `_` wzorca.  Jest to nazywane [wzorzec wieloznaczny](language-reference/pattern-matching.md#wildcard-pattern), czyli sposób zawierający komunikat "I nie zależy dany element jest".  Mimo że jest to wygodny, możesz przypadkowo obejścia wyczerpujący dopasowanie wzorca i nie korzystają z enforcements kompilacji, jeśli nie masz uważać za pomocą `_`.  Najlepiej jest używany podczas nie interesujących niektórych części rozkładany typu podczas wzorca dopasowania ani w klauzuli końcowego podczas ma wyliczyć wszystkich przypadków znaczący wzorca zgodnego wyrażeniem.

[Wzorce aktywne](language-reference/active-patterns.md) są innego zaawansowanych konstrukcji do użycia z dopasowywania do wzorca.  Umożliwiają one do partycjonowania danych wejściowych do niestandardowych formularzy decomposing je w witrynie wywołania dopasowania wzorca.  Ich można również ustawiać parametry, dzięki czemu do definiowania funkcji partycji.  Rozszerzanie w poprzednim przykładzie do obsługi aktywne wzorce wygląda następująco:

[!code-fsharp[ActivePatterns](../../samples/snippets/fsharp/tour.fs#L761-L783)]

## <a name="optional-types"></a>Opcjonalne typy

Jeden przypadek specjalnych typów złożenia Suma rozłączna jest typ opcji, który jest bardzo przydatny, że jest częścią biblioteki podstawowej F #.

[Typ opcji](language-reference/options.md) jest typem, a to stanowi jeden z dwóch przypadków: wartość lub nic wcale.  Jest on używany w żadnym scenariuszu, gdzie wartość mogą lub nie mogą wynikać z określonej operacji.  Następnie wymusza do konta w obu przypadkach co dotyczą kompilacji, a nie dotyczą środowiska wykonawczego.  Często służą one interfejsów API gdzie `null` używany do reprezentowania "nothing", eliminując konieczność martwić się o `NullReferenceException` w wielu sytuacjach.

[!code-fsharp[Options](../../samples/snippets/fsharp/tour.fs#L791-L811)]

## <a name="units-of-measure"></a>Jednostki miary

Jeden unikatowy funkcja system typów F # w jest możliwość zapewnienia kontekst dla literałów liczbowych za pośrednictwem jednostki miary.

[Jednostki miary](language-reference/units-of-measure.md) umożliwiają skojarzenia typu liczbowego do jednostki, takich jak liczników, i mieć funkcje wykonywania pracy na jednostki, a nie w literałach numerycznych.  Dzięki temu kompilator, aby sprawdzić, czy typy literałów numerycznych przekazano sensu w kontekście niektórych, eliminując błędy czasu wykonywania skojarzony z tego rodzaju pracy.

[!code-fsharp[UnitsOfMeasure](../../samples/snippets/fsharp/tour.fs#L818-L839)]

Biblioteki podstawowej F # definiuje wiele SI typy jednostek i konwersje jednostek.  Aby dowiedzieć się więcej, zapoznaj się [Namespace Microsoft.fsharp.Data.unitsystems.SI —](https://msdn.microsoft.com/visualfsharpdocs/conceptual/microsoft.fsharp.data.unitsystems.si-namespace-%5bfsharp%5d).

## <a name="classes-and-interfaces"></a>Klasy i interfejsy

F # ma także pełną obsługę klasy .NET, [interfejsów](language-reference/interfaces.md), [klas abstrakcyjnych](language-reference/abstract-classes.md), [dziedziczenia](language-reference/inheritance.md)i tak dalej.

[Klasy](language-reference/classes.md) są typy, które reprezentują obiekty .NET, która może zawierać właściwości, metod i zdarzeń jako jego [członków](language-reference/members/index.md).

[!code-fsharp[Classes](../../samples/snippets/fsharp/tour.fs#L848-L877)]

Definiowanie klas rodzajowych również jest bardzo proste.

[!code-fsharp[Classes](../../samples/snippets/fsharp/tour.fs#L884-L905)]

Aby zaimplementować interfejs, możesz użyć dowolnej `interface ... with` składni lub [wyrażenia obiektu](language-reference/object-expressions.md).

[!code-fsharp[Classes](../../samples/snippets/fsharp/tour.fs#L912-L931)]

## <a name="which-types-to-use"></a>Jakie typy do użycia

Obecność klas, rekordów, Unii Suma rozłączna i krotek prowadzi do ważne pytania: czego należy używać?  Większość podobny sposób jak w cyklu życia odpowiedź zależy od okoliczności.

Krotki jest wspaniała zwracanie wartości wielu z funkcją i przy użyciu agregacji ad hoc wartości jako wartości samej siebie.

Rekordy są "krok zapasowej" z krotek o o nazwie etykiety i obsługę opcjonalnych elementów członkowskich.  Są one doskonałe rozwiązanie dla małej procedury reprezentację danych podczas przesyłania danych za pośrednictwem programu.  Ponieważ mają one równości strukturalnej, są one łatwe w użyciu z porównania.

Rozłączne mają wiele zastosowań korzyści core jest jednak aby można było z nich korzystają w połączeniu z wzorzec dopasowany do konta dla wszystkich możliwych "kształtów" mające dane.  

Klasy są doskonałe rozwiązanie dla wielu powodów, takich jak konieczność reprezentują informacje, a także powiązać te informacje do funkcji.  Jako zasadą Jeśli masz funkcji, który jest koncepcyjnie związany z niektórych danych przy użyciu klas i zasad programowania Object-Oriented jest duże korzyści.  Klasy są również preferowany typ danych używany podczas współpracy z C# i Visual Basic w tych językach używania klas dla prawie wszystkich.

## <a name="next-steps"></a>Następne kroki

Teraz, przedstawiono niektóre główne funkcje języka, możesz przystąpić do zapisania pierwszej programy F #!  Zapoznaj się z [wprowadzenie](tutorials/getting-started/index.md) więcej informacji na temat konfigurowania środowiska deweloperskiego i pisania kodu.

Następne kroki, aby uzyskać więcej informacji może być dowolne, ale zaleca się [działa jako wartości pierwszej klasy](introduction-to-functional-programming/functions-as-first-class-values.md) <!--[Introduction to Functional Programming in F#](introduction-to-functional-programming/index.md)--> uzyskać doświadczenia z podstawowe koncepcje programowania funkcjonalności.  Będą one niezbędne w kompilowanie niezawodnych programów w języku F #.

Sprawdź również, [dokumentację języka F #](language-reference/index.md) aby zobaczyć kompleksowe zbiór koncepcyjnej zawartości w F #.
