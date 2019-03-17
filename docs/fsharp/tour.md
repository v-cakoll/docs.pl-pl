---
title: Przewodnik po F#
description: Sprawdź, niektóre najważniejsze funkcje w języku programowania w ten samouczek przy użyciu przykładów kodu F#.
ms.date: 11/06/2018
ms.openlocfilehash: 4b3ec7fd2c42712440ea7d7045c560ab20390b45
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58125580"
---
# <a name="tour-of-f"></a>Przewodnik po F\#

Najlepszym sposobem, aby dowiedzieć się więcej na temat języka F# jest do odczytu i zapisu w kodzie języka F#. Ten artykuł będzie pełnić rolę przez samouczek prowadzący przez niektóre kluczowe funkcje języka F# i zapewniają fragmenty kodu, które mogą być wykonywane na komputerze. Aby dowiedzieć się więcej na temat konfigurowania środowiska deweloperskiego, zapoznaj się z [wprowadzenie](tutorials/getting-started/index.md).

Istnieją dwa podstawowe pojęcia języka F#: funkcji i typów.  Ten samouczek będzie podkreślić funkcji języka, które dzielą się na tych dwóch koncepcji.

## <a name="executing-the-code-online"></a>Wykonywanie kodu w trybie online

Jeśli nie masz F# zainstalowany na komputerze, można wykonywać wszystkie przykłady online za pomocą [Fable REPL](https://fable.io/repl/). Fable jest dialekt F# , który jest wykonywany bezpośrednio w przeglądarce. Aby wyświetlić przykłady, które należy wykonać w rozwiązaniu REPL, zapoznaj się z **przykłady > Dowiedz się więcej > Przewodnik po przykładzie F#**  na pasku menu po lewej stronie replikacja Fable

## <a name="functions-and-modules"></a>Funkcje i modułów

Większość podstawowych rodzajów dowolnego programu F# są ***funkcje*** zorganizowane w ***modułów***.  [Funkcje](language-reference/functions/index.md) wykonują prace na dane wejściowe w celu wygenerowania danych wyjściowych i są zorganizowane w obszarze [modułów](language-reference/modules.md), które są podstawowym sposobem grupowania elementów w języku F#.  Są one definiowane za pomocą [ `let` powiązania](language-reference/functions/let-bindings.md), który nadaj nazwę funkcji i definiowanie jej argumentów.

[!code-fsharp[BasicFunctions](../../samples/snippets/fsharp/tour.fs#L101-L133)]

`let` powiązania są również, jak powiązać wartości nazwy, podobne do zmiennych w innych językach.  `let` powiązania są ***niezmienne*** domyślnie, co oznacza, że po wartości lub funkcja jest powiązana z nazwą, nie można zmienić w miejscu.  Jest to w przeciwieństwie do zmiennych w innych językach, które są ***mutable***, co oznacza, ich wartości można zmienić w dowolnym momencie w czasie.  Jeśli potrzebujesz mutable powiązania, możesz użyć `let mutable ...` składni.

[!code-fsharp[Immutability](../../samples/snippets/fsharp/tour.fs#L75-L94)]

## <a name="numbers-booleans-and-strings"></a>Liczby, wartości logicznych i ciągi

Jako języka .NET, język F# obsługuje tych samych podstawowych [typów pierwotnych](language-reference/primitive-types.md) znajdujące się na platformie .NET.

Poniżej przedstawiono, jak różne typy liczbowe są reprezentowane w języku F#:

[!code-fsharp[Numbers](../../samples/snippets/fsharp/tour.fs#L49-L68)]

Oto, jakie wartości logiczne i wykonywania podstawowych logikę warunkową wygląda następująco:

[!code-fsharp[Bools](../../samples/snippets/fsharp/tour.fs#L142-L152)]

A Oto, jakie basic [ciąg](language-reference/strings.md) manipulowania wygląda następująco:

[!code-fsharp[Strings](../../samples/snippets/fsharp/tour.fs#L158-L180)]

## <a name="tuples"></a>Krotki

[Krotek](language-reference/tuples.md) są to ważne wydarzenie w języku F#.  Są to zbiór wartości bez nazwy, ale uporządkowanym, które mogą być traktowane jako wartości.  Pełnią one wartości, które są agregowane na podstawie innych wartości.  Mają wiele zastosowań, takich jak wygodnie zwracanie wielu wartości z funkcją lub grupowania wartości dla wygody niektórych zapytań ad-hoc.

[!code-fsharp[Tuples](../../samples/snippets/fsharp/tour.fs#L186-L203)]

Począwszy od F# 4.1, można również utworzyć `struct` krotek.  Są także współpracować w pełni przy użyciu języka C# 7/Visual Basic 15 krotek, które są również `struct` spójnych kolekcji:

[!code-fsharp[Tuples](../../samples/snippets/fsharp/tour.fs#L205-L218)]

Należy zauważyć, że ponieważ `struct` krotek są typami wartości, nie może być niejawnie konwertowane na odwołania krotek, lub na odwrót.  Należy jawnie konwertowanie odwołań i strukturą spójnej kolekcji.

## <a name="pipelines-and-composition"></a>Między potokami i kompozycji

Potok operatorów, takich jak `|>` są często używane podczas przetwarzania danych w języku F#. Te operatory są funkcje, które pozwalają na wprowadzenie "potoki" funkcji w sposób elastyczny. Poniższy przykład przeprowadzi od tego, jak można było korzystać z tych operatorów, aby utworzyć prosty potok funkcjonalności:

[!code-fsharp[Pipelines](../../samples/snippets/fsharp/tour.fs#L227-L282)]

Poprzedni przykład wprowadzonych korzystania z wielu funkcji języka F#, łącznie z funkcjami przetwarzania listy, najwyższej klasy funkcje i [aplikacja częściowa](language-reference/functions/index.md#partial-application-of-arguments). Mimo że dogłębnej każdego z tych koncepcji może stać się nieco zaawansowane, powinno być jasne, jak łatwo można używać funkcji do przetwarzania danych, podczas tworzenia potoków.

## <a name="lists-arrays-and-sequences"></a>List, tablic i sekwencji

Są trzy typy kolekcji głównej w podstawowej biblioteki języka F#, list, tablic i sekwencji.

[Wyświetla listę](language-reference/lists.md) są uporządkowane, niezmienne kolekcje elementów tego samego typu.  Są one połączone pojedynczo list, co oznacza, że są przeznaczone dla wyliczenia, ale zły wybór kątem dostępu losowego i łączenia, gdy są one duże.  To w przeciwieństwie do listy w innych popularnych języków, które zwykle nie należy używać pojedynczo połączoną listę do reprezentowania list.

[!code-fsharp[Lists](../../samples/snippets/fsharp/tour.fs#L309-L359)]

[Tablice](language-reference/arrays.md) są stałym rozmiarze, *mutable* kolekcji elementów tego samego typu.  Obsługa szybkiego losowego dostępu do elementów i są realizowane szybciej, niż listy języka F#, ponieważ są one po prostu ciągłych bloków pamięci.

[!code-fsharp[Arrays](../../samples/snippets/fsharp/tour.fs#L368-L407)]

[Sekwencje](language-reference/sequences.md) to zbiór logiczny elementów, wszystkie tego samego typu.  Są to typu bardziej ogólny niż list i tablic, które można w dowolnym logicznej serii elementów "widoku".  Mogą również wyróżnić ponieważ może on być ***z opóźnieniem***, co oznacza, że elementy może zostać obliczony, tylko wtedy, gdy są potrzebne.

[!code-fsharp[Sequences](../../samples/snippets/fsharp/tour.fs#L418-L452)]

## <a name="recursive-functions"></a>Funkcje rekursywne

Przetwarzanie kolekcji lub sekwencji elementów odbywa się zwykle z [rekursji](language-reference/functions/index.md#recursive-functions) w języku F#.  Mimo że F# obsługuje pętle for i programowanie imperatywne, rekursja jest preferowana, ponieważ jest łatwiejsza w celu zagwarantowania poprawności.

> [!NOTE]
> Poniższy przykład wykorzystuje dopasowanie wzorca za pośrednictwem `match` wyrażenia.  Ta konstrukcja podstawowe zostało omówione w dalszej części tego artykułu.

[!code-fsharp[RecursiveFunctions](../../samples/snippets/fsharp/tour.fs#L461-L500)]

F# ma również pełną obsługę optymalizację wywołania Tail, czyli sposób na optymalizację wywołania cykliczne, aby były one po prostu tak szybko, jak konstrukcję pętli.

## <a name="record-and-discriminated-union-types"></a>Rejestrowanie i typy Unii rozłącznej

Rekord i typy Unii są dwa typy danych podstawowych używane w kodzie języka F# i ogólnie najlepszym sposobem reprezentowania danych w programie F#.  Mimo że to sprawia, że ich podobny do klasy w innych językach, jednym z podstawowe różnice między nimi jest mają semantykę porównania strukturalnego.  Oznacza to, czy są one "natywnie" porównywalne i równości jest bardzo proste — wystarczy Sprawdź, czy jeden równe.

[Rekordy](language-reference/records.md) są agregacją nazwanych wartości członkom opcjonalne (takie jak metody).  Jeśli znasz języka C# lub języka Java, następnie te powinny czuć się podobnie POCOs lub obiektów typu Pojo — tak w przypadku równości strukturalnych i mniej procedury.

[!code-fsharp[Records](../../samples/snippets/fsharp/tour.fs#L507-L559)]

Począwszy od F# 4.1, może również reprezentować rekordy jako `struct`s.  Jest to zrobić za pomocą `[<Struct>]` atrybutu:

[!code-fsharp[Records](../../samples/snippets/fsharp/tour.fs#L561-L568)]

[Rekord z wariantami (DUs)](language-reference/discriminated-unions.md) są wartościami, które mogą być liczbę nazwanych formularze lub przypadków.  Dane przechowywane w typie może być jednym z kilku odrębnych wartości.

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L575-L631)]

Możesz również użyć DUs jako *pojedynczym przypadku sumy rozłączne*, aby pomóc w domenie modelowania za pośrednictwem typów pierwotnych.  Często, ciągi i inne typy pierwotne, są używane do reprezentowania coś, a zatem otrzymują określonego znaczenie.  Jednak przy użyciu pierwotnych reprezentacja danych może spowodować przez pomyłkę przypisywanie niepoprawną wartość!  Reprezentujących poszczególnych typów informacji jako odrębne złożenie pojedynczym przypadku można wymusić poprawność, w tym scenariuszu.

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L633-L654)]

Tak jak pokazano w powyższym przykładzie, aby uzyskać podstawową wartość w pojedynczym przypadku Unii rozłącznej, należy je jawnie odkodowania.

Ponadto DUs również obsługuje definicje cykliczne, co pozwala łatwo reprezentują drzew natury cyklicznego danych i.  Na przykład Oto, jak może reprezentować drzewa binarnego wyszukiwania z `exists` i `insert` funkcji.

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L656-L683)]

Ponieważ DUs umożliwiają reprezentują struktura cyklicznego drzewa w typie danych, korzysta z tej struktury cyklicznego jest proste i gwarantuje poprawność.  Jest też obsługiwana w dopasowywania do wzorca, jak pokazano poniżej.

Ponadto może reprezentować DUs jako `struct`s `[<Struct>]` atrybutu:

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L685-L696)]

Istnieją dwie ważne informacje, które należy pamiętać podczas w ten sposób:

1. Struktura jednostka bazy danych nie może być zdefiniowana cyklicznie.
2. Struktura DU nazwy muszą być unikatowe dla każdego z jego przypadków.

Nie można wykonać powyższego spowoduje błąd kompilacji.

## <a name="pattern-matching"></a>Dopasowanie wzorca

[Wzorzec dopasowywania](language-reference/pattern-matching.md) to funkcja języka F#, co umożliwia poprawność dla korzysta z typów F#.  W powyższych przykładach można zauważyć znacznej liczby `match x with ...` składni.  Ta konstrukcja umożliwia kompilatora, który może zrozumieć "kształt" typy danych, aby wymusić konta dla wszystkich przypadków możliwe, korzystając z typu danych, przez co to jest znany jako wyczerpujący dopasowywania do wzorca.  To ogromne możliwości pod kątem poprawności i może służyć sprytnie "kiwnięcia" jaki byłyby zwykle dotyczą środowiska uruchomieniowego, w czasie kompilacji.

[!code-fsharp[PatternMatching](../../samples/snippets/fsharp/tour.fs#L705-L742)]

Coś, co można zauważyć polega na użyciu `_` wzorca.  Jest to nazywane [wzór symboli wieloznacznych](language-reference/pattern-matching.md#wildcard-pattern), która określa sposób powiedzenie "I nie zależy coś, co jest".  Mimo że jest to wygodne, możesz przypadkowo obejścia wyczerpujący dopasowywania do wzorca i nie korzystają z enforcements kompilacji, jeśli nie chcesz zachować ostrożność przy użyciu `_`.  Najlepiej jest używany podczas nie dba o niektórych rodzajów rozkładany typu podczas wzorca dopasowania lub końcowego klauzuli, gdy masz wyliczyć wszystkich istotnych przypadkach w wyrażeniu dopasowania do wzorca.

[Wzorce aktywne](language-reference/active-patterns.md) czy innej konstrukcji zaawansowane do użycia z dopasowaniem wzorca.  Umożliwiają one podzielić dane wejściowe na niestandardowych formularzy, podzielenie je w witrynie wywołania dopasowania wzorca.  One mogą również zostać sparametryzowane, co pozwala zdefiniować partycji w funkcji.  Rozszerzając poprzedni przykład do obsługi wzorców wygląda następująco:

[!code-fsharp[ActivePatterns](../../samples/snippets/fsharp/tour.fs#L764-L786)]

## <a name="optional-types"></a>Opcjonalne typy

Jeden przypadek specjalne typy Unii rozłącznej jest typ opcji, co jest przydatne w tak, że jest częścią podstawowej biblioteki języka F#.

[Typ opcji](language-reference/options.md) jest typem, który stanowi jeden z dwóch przypadków: wartość lub nic w ogóle.  Jest on używany w każdym scenariuszu, w którym wartości mogą lub nie mogą wynikać z określonej operacji.  To następnie wymusza dla obu przypadków, dzięki czemu kwestią w czasie kompilacji, a nie dotyczą środowiska uruchomieniowego.  Są one często używane w interfejsach API gdzie `null` służy do reprezentowania "nothing" zamiast niego, eliminując konieczność zajmowania `NullReferenceException` w wielu sytuacjach.

[!code-fsharp[Options](../../samples/snippets/fsharp/tour.fs#L789-L814)]

## <a name="units-of-measure"></a>Jednostki miary

Jedna z unikatowych funkcji F# w systemie typów jest możliwość zapewnienia kontekstu literały numeryczne, za pośrednictwem jednostki miary.

[Jednostki miary](language-reference/units-of-measure.md) umożliwiają skojarzenie typu liczbowego do jednostki, takie jak liczniki, oraz mają funkcje wykonują prace na jednostki, a nie w literałach numerycznych.  Dzięki temu kompilator, aby sprawdzić, czy typy przekazywane w literałach numerycznych mają sens w pewnym kontekście, eliminując błędy czasu wykonywania skojarzony z tego rodzaju pracy.

[!code-fsharp[UnitsOfMeasure](../../samples/snippets/fsharp/tour.fs#L817-L842)]

Biblioteki podstawowej F# definiuje wiele typów jednostki SI i konwersje jednostek.  Aby dowiedzieć się więcej, zapoznaj się z [Namespace Microsoft.fsharp.Data.unitsystems.SI —](https://msdn.microsoft.com/visualfsharpdocs/conceptual/microsoft.fsharp.data.unitsystems.si-namespace-%5bfsharp%5d).

## <a name="classes-and-interfaces"></a>Klasy i interfejsy

F# ma również pełną pomoc techniczną dla klas .NET [interfejsów](language-reference/interfaces.md), [klasy abstrakcyjne](language-reference/abstract-classes.md), [dziedziczenia](language-reference/inheritance.md)i tak dalej.

[Klasy](language-reference/classes.md) są typy, które reprezentują obiektów platformy .NET, która może zawierać właściwości, metody i zdarzenia jako jego [członków](language-reference/members/index.md).

[!code-fsharp[Classes](../../samples/snippets/fsharp/tour.fs#L845-L880)]

Definiowanie klas ogólnych również jest bardzo proste.

[!code-fsharp[Classes](../../samples/snippets/fsharp/tour.fs#L883-L908)]

Aby zaimplementować interfejs, można użyć albo `interface ... with` składni lub [wyrażenie obiektu](language-reference/object-expressions.md).

[!code-fsharp[Classes](../../samples/snippets/fsharp/tour.fs#L911-L934)]

## <a name="which-types-to-use"></a>Jakie typy do użycia

Obecność klas, rekordy i sumy rozłączne oraz krotek prowadzi do ważnym pytaniem: czego należy używać?  Większość podobny sposób jak w życie odpowiedź zależy od okoliczności.

Kolekcje są doskonale w przypadku zwracania wielu wartości z funkcji i przy użyciu zapytań ad-hoc wartość zagregowana wartości jako wartość sam.

Rekordy są "krok zapasowej" z krotek, o nazwie etykiety i pomoc techniczna dla opcjonalne elementy członkowskie.  Są one bardzo przydatne na potrzeby nieoficjalne reprezentacja danych podczas przesyłania przy użyciu programu.  Ponieważ mają one strukturalnych równości, są one łatwe w użyciu z funkcją porównania.

Sumy rozłączne mają wiele zastosowań korzyści core jest jednak aby można było z nich korzystają w połączeniu z dopasowaniem wzorca, aby uwzględnić wszystkie możliwe "kształty", które mogą mieć danych.  

Klasy to idealne rozwiązanie dla wielu powodów, na przykład gdy trzeba reprezentują informacje, a także powiązać te informacje do funkcji.  Jako ogólną regułę można przyjąć w przypadku funkcji, które pod względem koncepcyjnym jest powiązany do niektórych danych przy użyciu klas i zasad programowania Object-Oriented jest dużą korzyścią.  Klasy są również preferowany typ danych używany podczas współpracy z C# i Visual Basic, zgodnie z tych języków na użytek klasy prawie wszystko.

## <a name="next-steps"></a>Następne kroki

Teraz, gdy wiesz, niektóre z podstawowych funkcji języka, powinno być gotowe do pisania pierwszego programów F#!  Zapoznaj się z [wprowadzenie](tutorials/getting-started/index.md) informacje na temat konfigurowania środowiska deweloperskiego i pisanie kodu.

Następne kroki zawierające więcej może być dowolną, ale zalecamy [wprowadzenie do programowania funkcyjnego w F# ](introduction-to-functional-programming/index.md) do przyzwyczaić się podstawowe pojęcia programowania funkcyjnego.  Będą one niezbędne do tworzenia niezawodnych programów w języku F#.

Ponadto zapoznaj się z [dokumentacja języka F#](language-reference/index.md) wyświetlić obszerna kolekcja zawartości koncepcyjnej F#.
