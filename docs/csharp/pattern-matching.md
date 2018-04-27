---
title: Dopasowanie wzorca — przewodnik C#
description: Dowiedz się więcej o wzorzec dopasowany wyrażenia w języku C#
keywords: .NET, .NET Core, C#
ms.date: 01/24/2017
ms.author: wiwagn
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 1e575c32-2e2b-4425-9dca-7d118f3ed15b
ms.openlocfilehash: a0f80fc2c019cefa81506d9dcdeabc57a1e98c2b
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="pattern-matching"></a>Dopasowanie wzorca #

Wzorce przetestować, czy wartość ma określony *kształtu*i można je *wyodrębnić* informacji z wartości, jeśli ma odpowiedniego kształtu. Dopasowanie wzorca zapewnia bardziej zwięzły składni algorytmów używanych już dzisiaj. Już tworzyć przy użyciu składni istniejące algorytmy dopasowywania do wzorca. Możesz zapisać `if` lub `switch` instrukcji, które wartości testowe. Następnie gdy te instrukcje są zgodne, można wyodrębnić i używać informacji z tej wartości. Nowe elementy składni są rozszerzenia instrukcje znasz już: `is` i `switch`. Testowanie wartości i wyodrębniania informacji łączyć tych nowych rozszerzeń.

W tym temacie wyjaśniono, nowej składni, aby pokazać, jak umożliwia do odczytu i zwięzłe kodu. Dopasowanie wzorca umożliwia idioms, w którym dane i kod są rozdzielone, w przeciwieństwie do projektów obiektowej gdzie danych i metod, które manipulować nimi są bezpośrednio powiązane.

Aby zilustrować te nowe idioms, teraz współpracować z struktur reprezentujących geometrycznych kształtów za pomocą instrukcji dopasowywania do wzorca. Znasz prawdopodobnie Tworzenie klasy hierarchie i tworzenie [metody wirtualne i przesłoniętej metody](methods.md#inherited) Aby dostosować zachowanie obiektu na podstawie typu środowiska uruchomieniowego obiektu.

Te techniki nie są możliwe w dla danych, który nie jest strukturę hierarchii klas. Gdy dane i metody są oddzielone, należy innych narzędzi. Nowy *dopasowanie wzorca* konstrukcji włączyć składni czyszczący do badania danych i manipulowania przepływu sterowania na podstawie warunku żadnych danych. Już zapisu `if` instrukcje i `switch` test który wartość zmiennej. Możesz zapisać `is` instrukcji, które test typ zmiennej. *Dopasowanie wzorca* dodaje nowe funkcje do tych instrukcji.

W tym temacie będzie kompilacji metodę, która oblicza obszaru różnych kształtów geometrycznych. Jednak należy go to zrobić bez konieczności techniki obiektowej i tworzenie hierarchii klas dla różnych kształtów.
Użyjesz *dopasowanie wzorca* zamiast tego. Do dalszego podkreślić, że firma Microsoft nie korzysta z dziedziczenia, należy podjąć każdego kształtu `struct` zamiast klasy. Należy pamiętać, że różne `struct` typów nie można określić typowe typu zdefiniowanego przez użytkownika podstawowego, dlatego dziedziczenia nie jest możliwe projektu.
Podczas wykonywania kroków w tym przykładzie, natomiast ten kod z jak może być struktura jako hierarchię obiektów. Po danych należy zbadać i manipulowania nie jest hierarchia klas, dopasowanie wzorca umożliwia bardzo atrakcyjny projektów.

Zamiast rozpoczyna się od definicji kształtu abstrakcyjna i dodawanie klas inny kształt, Zacznijmy zamiast tego proste danych tylko definicje dla wszystkich kształtów:

[!code-csharp[ShapeDefinitions](../../samples/csharp/PatternMatching/Shapes.cs#01_ShapeDefinitions "Shape definitions")]

Z tych struktur Napisz metodę, która oblicza obszaru niektórych kształtu.

## <a name="the-is-type-pattern-expression"></a>`is` Wpisz wyrażenie wzorca

Przed C# 7.0, konieczne będzie przetestuj poszczególne typy w szeregu `if` i `is` instrukcji:

[!code-csharp[ClassicIsExpression](../../samples/csharp/PatternMatching/GeometricUtilities.cs#02_ClassicIsExpression "Classic type pattern using is")]

Czy powyższy kod jest wyrażeniem klasycznego *wzorzec typu*: w przypadku testowania zmiennej do określenia jej typu i wykonywania różnych akcji, na podstawie tego typu.

Ten kod staje się prostsze przy użyciu rozszerzeń `is` wyrażenie, które można przypisać zmiennej Jeśli test zakończy się pomyślnie:

[!code-csharp[IsPatternExpression](../../samples/csharp/PatternMatching/GeometricUtilities.cs#03_IsPatternExpression "is pattern expression")]

W tym zaktualizowaną wersję `is` wyrażenie testów zmiennej i przypisuje go do nowej zmiennej prawidłowego typu. Ponadto zawiadomienia, które ta wersja zawiera `Rectangle` typu, który jest `struct`. Nowe `is` wyrażenie współpracuje z typów wartości, a także typy referencyjne.

Reguły języka wyrażeń dopasowania wzorca pomóc w uniknięciu niewłaściwie korzysta z wyników wyrażenie dopasowania. W przykładzie przedstawionym powyżej zmienne `s`, `c`, i `r` tylko w zakresie i ostatecznie przypisane przypadku wyrażenia dopasowania wzorca odpowiednich `true` wyników. Jeśli spróbujesz użyć zmiennej albo w innym miejscu kodu generuje błędy kompilatora.

Przeanalizujmy oba te reguły szczegółowo, począwszy od zakresu. Zmienna `c` znajduje się w zakresie tylko w `else` gałęzi pierwszego `if` instrukcji. Zmienna `s` znajduje się w zakresie w metodzie `ComputeArea`. Wynika to z każdej gałęzi `if` instrukcji ustanawia oddzielnymi zakresami zmiennych. Jednak `if` nie obsługuje instrukcji sam. Oznacza to, że zmienne zadeklarowane w `if` instrukcji znajdują się w tym samym zakresie co `if` instrukcji (metoda w tym przypadku.) To zachowanie nie jest specyficzne dla dopasowania wzorca, ale jest zdefiniowane zachowanie dla zmiennej zakresów i `if` i `else` instrukcje.

Zmienne `c` i `s` są przypisane, kiedy odpowiednio `if` instrukcje są spełnione ze względu na przypisane ostatecznie gdy true mechanizmu.

> [!TIP]
> Przykłady w tym temacie Użyj zalecanych konstrukcji, którego dopasowania wzorca `is` wyrażenie ostatecznie przypisuje zmiennej dopasowania w `true` gałęzi `if` instrukcji.
> Logika może odtworzyć mówiąc `if (!(shape is Square s))` i zmienna `s` będzie można zdecydowanie przypisać tylko w `false` gałęzi. Jest to prawidłowy C#, nie zaleca się, ponieważ jest bardziej skomplikowane, postępuj zgodnie z logiką.

Te reguły oznacza, że jesteś w stanie przypadkowo uzyskiwać dostęp do wyniku wyrażenia dopasowania wzorca w przypadku tego wzorca nie zostało spełnione.

## <a name="using-pattern-matching-switch-statements"></a>Za pomocą dopasowywania do wzorca `switch` — instrukcje

Zgodnie z upływem czasu, konieczne może być obsługuje inne typy kształtu. Wraz z rozwojem liczbę warunków podczas testowania, znajdują się to przy użyciu `is` wzorzec dopasowany wyrażenia może być skomplikowane. Oprócz wymagające `if` instrukcje dla każdego typu, aby sprawdzić, `is` wyrażenia są ograniczone do testowania, jeśli pasuje do jednego typu danych wejściowych. W takim przypadku znajdziesz który `switch` wyrażenia dopasowania wzorca staje się lepszym rozwiązaniem. 

Tradycyjne `switch` instrukcja została wyrażenia wzorca: on obsługiwany wzorzec stałej.
Można porównać zmienną do dowolnego stała używane w `case` instrukcji:

[!code-csharp[ClassicSwitch](../../samples/csharp/PatternMatching/GeometricUtilities.cs#04_ClassicSwitch "Classic switch statement")]

Tylko wzorca obsługiwane przez `switch` instrukcja została stałe wzorzec. Dalsze została ograniczona do liczbowych typów i `string` typu.
Te ograniczenia zostały usunięte, a teraz zapisać `switch` instrukcję, używając ze wzorcem typu:

[!code-csharp[Switch Type Pattern](../../samples/csharp/PatternMatching/GeometricUtilities.cs#05_SwitchTypePattern "Compute with `switch` expression")]

Dopasowanie wzorca `switch` używana składnia znane deweloperom, którzy użyli tradycyjnych stylu języka C `switch` instrukcji. Każdy `case` jest obliczane i wykonywany jest kod poniżej warunek, który odpowiada zmiennej wejściowego. Wykonanie kodu nie może "przechodzić" z jednego wyrażenia case do następnego; Składnia `case` instrukcji wymaga, aby każdy `case` kończyć `break`, `return`, lub `goto`.

> [!NOTE]
> `goto` Instrukcje, aby przejść do innej etykiety są prawidłowe tylko w wzorcu stałej instrukcji switch klasycznego.

Brak ważnych nowe zasady `switch` instrukcji. Ograniczenia dotyczące typu zmiennej w `switch` wyrażenia zostały usunięte.
Dowolny typ, takich jak `object` w tym przykładzie, może być używany. Wyrażenia case nie są ograniczone do wartości stałych. Usunięcie tego ograniczenia oznacza, że zmiana kolejności `switch` sekcje mogą zmienić zachowanie programu.

Gdy ograniczone do wartości stałej ma więcej niż jeden `case` etykiety może być zgodna z wartością `switch` wyrażenia. Połączenie wyniku z regułą który co `switch` sekcji nie musi przechodzić do następnej sekcji i zostały wykonane, który `switch` sekcje można zmieniać w dowolnej kolejności bez wpływu na zachowanie.
Teraz z więcej uogólniony `switch` wyrażenia, kolejność każdej sekcji ma znaczenie. `switch` Wyrażenia są przetwarzane w kolejności tekstową. Wykonanie przenoszone jest do pierwszej `switch` etykiety, który odpowiada `switch` wyrażenia.  
Należy pamiętać, że `default` przypadku będą wykonywane tylko, jeśli innych przypadków etykiety nie są zgodne. `default` Przypadek jest obliczane, niezależnie od ich kolejność tekstową. W przypadku nie `default` sprawy i brak innych `case` instrukcje są zgodne, wykonanie jest kontynuowane od następujących instrukcji `switch` instrukcji. Żadna z `case` wykonywany jest kod etykiety.

## <a name="when-clauses-in-case-expressions"></a>`when` klauzule `case` wyrażenia

Możesz wprowadzić specjalne przypadki tych kształty, których obszaru 0 za pomocą `when` klauzuli na `case` etykiety. Kwadrat o długości boku 0 lub koło z protokołem radius 0 ma obszar 0. Można ją określić za pomocą tego warunku `when` klauzuli na `case` etykiety:  

[!code-csharp[ComputeDegenerateShapes](../../samples/csharp/PatternMatching/GeometricUtilities.cs#07_ComputeDegenerateShapes "Compute shapes with 0 area")]

Ta zmiana przedstawiono kilka ważnych kwestii o nowej składni. Najpierw wielu `case` etykiety może odnosić się do jednego `switch` sekcji. Blok instrukcji jest wykonywana po jest dowolny z tych etykiet `true`. W tym przypadku jeśli `switch` wyrażenie jest koło lub kwadrat z obszaru 0, metoda zwraca stała 0.

W tym przykładzie przedstawiono dwie różne zmienne w dwóch `case` etykiet w pierwszym `switch` bloku. Należy zauważyć, że instrukcje w tym `switch` bloku nie należy używać albo zmienne `c` (dla okręgu) lub `s` (dla wartości kwadratu).
Zdecydowanie nie żadna z tych zmiennych nie przypisano w tym `switch` bloku.
Jeśli jeden z tych przypadkach są zgodne, wyraźnie zmiennych zostały przypisane.
Jednak nie można sprawdzić *którego* przypisano w czasie kompilacji, ponieważ w obu przypadkach można dopasować w czasie wykonywania. Z tego powodu większość czasu kiedy używanych jest wiele `case` etykiety dla tego samego bloku, nie będzie powodować nową zmienną w `case` instrukcji, lub tylko użyć zmiennej w `when` klauzuli.

Mające dodać te kształty z obszaru 0, możemy dodać kilka typów więcej kształtów: prostokąt i trójkąt:

[!code-csharp[AddRectangleAndTriangle](../../samples/csharp/PatternMatching/GeometricUtilities.cs#09_AddRectangleAndTriangle "Add rectangle and triangle")]

 Dodaje ten zestaw zmian `case` etykiet w przypadku degeneracji i etykiety i bloków dla wszystkich nowych kształtów. 

Na koniec można dodać `null` wielkości liter, aby zapewnić argument nie jest `null`:

[!code-csharp[NullCase](../../samples/csharp/PatternMatching/GeometricUtilities.cs#10_NullCase "Add null case")]

Specjalnego zachowania w przypadku `null` wzorzec jest ciekawe ponieważ stała `null` we wzorcu nie ma typu, ale mogą być konwertowane do dowolnego typu odwołanie lub typ dopuszczający wartość null. Zamiast przekonwertować `null` do dowolnego typu język definiuje, które `null` wartość będzie zgodny z żadnym wzorcem typu, niezależnie od typu zmienną kompilacji. To zachowanie sprawia, że nowe `switch` na podstawie typu wzorzec zgodne z `is` instrukcji: `is` instrukcje zawsze zwracają `false` gdy wartość sprawdzany jest `null`. Jest również prostsze: po sprawdzeniu typ nie jest potrzebny dodatkowy sprawdzania wartości null. Widać, że z faktu, że nie istnieją żadne null sprawdza w żadnym przypadku bloków powyższe przykłady: nie są niezbędne, ponieważ pasujących do wzorca typu gwarantuje wartość inną niż null.

## <a name="var-declarations-in-case-expressions"></a>`var` deklaracje w `case` wyrażenia

Wprowadzenie `var` jako jednego z wyrażeń dopasowania wprowadzono nowe reguły do dopasowania wzorca.

Pierwsza reguła jest to, że `var` zasady wnioskowania typu normalne znajduje się za deklaracją: typu jest wywnioskowany do statycznego typu wyrażenia switch. Od tej zasady zawsze zgodny typ.

Jest drugą regułę, która `var` deklaracji nie ma wartości null Sprawdź, czy zawierają inne wyrażenia wzorca typu. Oznacza to, zmienna może mieć wartości null, a w takim przypadku sprawdzania wartości null jest to konieczne.

Te dwie reguły oznaczają, że w wielu przypadkach `var` deklaracji w `case` wyrażenie dopasowuje z. `default` wyrażenia.
Ponieważ w przypadku wszelkich innych niż domyślne jest preferowana względem `default` przypadku `default` przypadku nigdy nie będą wykonywane.

> [!NOTE]
> Kompilator nie Emituj ostrzeżenie w przypadkach, gdy `default` przypadku została zapisana, ale nigdy nie będą wykonywane. Jest to zgodne z bieżącą `switch` zachowaniem instrukcji, gdzie zostały wymienione wszystkich możliwych przypadków.

Trzeci regułę wprowadzono używa gdzie `var` przypadku mogą być użyteczne. Wyobraź sobie robią dopasowania wzorca, gdy dane wejściowe jest ciągiem i szukasz polecenia znane wartości. Można napisać wyglądać mniej więcej tak:

[!code-csharp[VarCaseExpression](../../samples/csharp/PatternMatching/Program.cs#VarCaseExpression "use a var case expression to filter white space")]

`var` Przypadek dopasowań `null`, ciągiem pustym lub dowolny ciąg, który zawiera tylko biały znak. Należy zauważyć, że w poprzednim kodzie użyto `?.` operatora, aby upewnić się, że jej nie przypadkowo zgłasza <xref:System.NullReferenceException>. `default` Przypadku obsługuje innych wartości ciągu, które nie jest rozpoznawany przez parser tego polecenia.

To jest przykład których warto wziąć pod uwagę `var` przypadek wyrażenie, które różni się od `default` wyrażenia.

## <a name="conclusions"></a>Wnioski

*Konstrukcje dopasowywania do wzorca* umożliwiają łatwe zarządzanie przepływu sterowania spośród różnych zmiennych i typy, które nie są powiązane przez hierarchię dziedziczenia. Można też kontrolować logiki używać żadnych warunek, który należy przetestować w zmiennej. Umożliwia wzorców i idioms, które należy częściej podczas tworzenia więcej aplikacji rozproszonych, w którym dane i metody, które manipulowania danych są oddzielone. Można zauważyć struktury kształtu używany w tym przykładzie nie zawierają żadnych metod, właściwości tylko do odczytu.
Dopasowywanie do wzorca współpracuje z dowolnego typu danych. Napisz wyrażeń, które badają obiekt, a następnie podjąć decyzje dotyczące przepływu sterowania na podstawie tych warunków.

Porównanie kodu z tego przykładu z projektu, który w wyniku tworzenia hierarchii klas dla abstrakcyjnego `Shape` i określonych pochodnych kształty z własnych implementacji metody wirtualnej do obliczenia. Często okazuje się wyrażenia dopasowania wzorca może być bardzo przydatne narzędzie podczas pracy z danych, aby oddzielić od problemów zachowanie dotyczy magazynu danych.

