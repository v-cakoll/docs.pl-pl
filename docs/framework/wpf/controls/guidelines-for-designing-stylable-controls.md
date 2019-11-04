---
title: Wytyczne do projektowania kontrolek w określonych stylach
ms.date: 03/30/2017
helpviewer_keywords:
- style design for controls [WPF]
- controls [WPF], style design
ms.assetid: c52dde45-a311-4531-af4c-853371c4d5f4
ms.openlocfilehash: 0fbb515afbeac05168ced6f0a99f50eb29a5c848
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459652"
---
# <a name="guidelines-for-designing-stylable-controls"></a>Wytyczne do projektowania kontrolek w określonych stylach

Ten dokument zawiera podsumowanie zestawu najlepszych rozwiązań, które należy wziąć pod uwagę podczas projektowania kontrolki, która ma być łatwo określonych stylach i templatable. Mamy do tego zestaw najlepszych rozwiązań dzięki dużej liczbie prób i błędom podczas pracy nad stylami kontrolki dla wbudowanego zestawu kontrolki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Wiemy, że pomyślne style są tak duże jak funkcja dobrze zaprojektowanego modelu obiektów, tak samo jak w stylu. Zaznaczeni odbiorcy tego dokumentu jest autorem kontrolki, a nie autorem stylu.

<a name="Terminology"></a>

## <a name="terminology"></a>Terminologia

"Style i tworzenia szablonów" odnoszą się do pakietu technologii, które umożliwiają autorowi formantu odroczenie wizualnych aspektów formantu do stylu i szablonu kontrolki. Ten pakiet technologii obejmuje:

- Style (w tym metody ustawiające właściwości, wyzwalacze i Scenorysy).

- Produkcyjnych.

- Szablony kontrolek.

- Szablony danych.

Aby zapoznać się z wprowadzeniem do stylów i tworzenia szablonów, zobacz [Style i tworzenia szablonów](../../../desktop-wpf/fundamentals/styles-templates-overview.md).

<a name="Before_You_Start__Understanding_Your_Control"></a>

## <a name="before-you-start-understanding-your-control"></a>Przed rozpoczęciem: zrozumienie Twojego formantu

Przed przejściem do tych wskazówek należy zrozumieć i zdefiniować wspólne użycie formantu. Style uwidaczniają często unruly zestaw możliwości. Kontrolki, które są zapisywane w szerokim stopniu (w wielu aplikacjach, przez wielu deweloperów) stanowią wyzwanie dla wyzwania, którego style mogą być używane do osiągnięcia atrakcyjnych zmian wyglądu kontrolki. W rzeczywistości kontrolka z stylem może nie być jeszcze podobna do intencji autora kontrolki. Ponieważ elastyczność oferowana przez style jest zasadniczo niezależna, można użyć pomysłu typowego użycia, aby ułatwić zakres decyzji.

Aby zrozumieć typowe użycie kontrolki, warto zastanowić się nad wartością jej pozycji. Co formant przeniesie do tabeli, która nie może oferować żadnej innej kontrolki? Typowy sposób użycia nie implikuje żadnego konkretnego wyglądu wizualizacji, ale raczej charakteru informacji o kontroli i rozsądnego zestawu oczekiwań dotyczących użycia. Dzięki temu można dokonać pewnych założeń dotyczących modelu kompozycji oraz zachowań zdefiniowanych w stylu kontrolki w typowym przypadku. W przypadku <xref:System.Windows.Controls.ComboBox>, na przykład zrozumienie typowego użycia nie zapewnia żadnych szczegółowych informacji o tym, czy konkretna <xref:System.Windows.Controls.ComboBox> ma zaokrąglone rogi, ale zapewni wgląd w fakt, że <xref:System.Windows.Controls.ComboBox> prawdopodobnie wymaga okna podręcznego i niektórych sposobów trwa przełączanie tego, czy jest otwarte.

<a name="General_Guidelines"></a>

## <a name="general-guidelines"></a>Ogólne wskazówki

- **Nie Wymuszaj ściśle kontraktów szablonów.** Kontrakt szablonu kontrolki może składać się z elementów, poleceń, powiązań, wyzwalaczy lub ustawień właściwości, które są wymagane lub oczekiwane do poprawnego działania formantu.

  - Zminimalizuj kontrakty tak długo, jak to możliwe.

  - Zaprojektowanie wokół oczekiwań, które w czasie projektowania (czyli w przypadku korzystania z narzędzia do projektowania) jest wspólne dla szablonu formantu, który ma być w stanie niekompletnym. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nie oferuje infrastruktury stanu "redagowania", dlatego kontrolki muszą być kompilowane z oczekiwaniami, że taki stan może być prawidłowy.

  - Nie zgłaszaj wyjątków, gdy nie jest przestrzegany żaden aspekt kontraktu szablonu. W tych wierszach panele nie powinny zgłaszać wyjątków, jeśli mają zbyt wiele lub zbyt mało elementów podrzędnych.

- **Funkcje peryferyjne wskaźnika do elementów pomocnika szablonu.** Każda kontrolka powinna być ukierunkowana na podstawowe funkcje i wartość PRAWDA i zdefiniowana przez typowe użycie formantu. W tym celu użyj elementów składowych i pomocniczych w ramach szablonu, aby włączyć zachowania i wizualizacje urządzenia peryferyjnego, czyli te zachowania i wizualizacje, które nie przyczyniają się do podstawowych funkcji formantu. Elementy pomocnika dzielą się na trzy kategorie:

  - **Autonomiczne** typy pomocników to publiczne i wielokrotnego użytku kontrolki lub elementy pierwotne, które są używane "anonimowo" w szablonie, co oznacza, że ani element pomocnika, ani styl kontrolki nie są świadome innych. Technicznie każdy element może być typem anonimowym, ale w tym kontekście pojęcie opisuje te typy, które hermetyzują wyspecjalizowane funkcje, aby umożliwić obsługę scenariuszy strategicznych.

  - Elementy pomocnika **oparte na typie** to nowe typy, które hermetyzują wyspecjalizowane funkcje. Te elementy są zwykle zaprojektowane z wąskim zakresem funkcjonalności niż typowe kontrolki lub elementy pierwotne. W przeciwieństwie do autonomicznych elementów pomocniczych, elementy pomocników opartych na typach są świadome kontekstu, w którym są używane, a zwykle muszą udostępniać dane kontrolce, do której należy.

  - **Nazwane** elementy pomocnika są typowymi kontrolkami lub elementami podstawowymi, które formant oczekuje na znalezienie w ramach szablonu według nazwy. Te elementy uzyskują dobrze znaną nazwę w ramach szablonu, co umożliwia formantowi znalezienie elementu i programistyczne współdziałanie z nim. W każdym szablonie może istnieć tylko jeden element o danej nazwie.

  W poniższej tabeli przedstawiono elementy pomocnika, które zostały już dzisiaj wykorzystane przez style formantów (Ta lista nie jest wyczerpująca):

  |Element|Typ|Używane przez|
  |-------------|----------|-------------|
  |<xref:System.Windows.Controls.ContentPresenter>|Oparty na typie|<xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.RadioButton>, <xref:System.Windows.Controls.Frame>itd. (wszystkie typy <xref:System.Windows.Controls.ContentControl>)|
  |<xref:System.Windows.Controls.ItemsPresenter>|Oparty na typie|<xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.Menu>itd. (wszystkie typy <xref:System.Windows.Controls.ItemsControl>)|
  |<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|Nazywany|<xref:System.Windows.Controls.ToolBar>|
  |<xref:System.Windows.Controls.Primitives.Popup>|Autonomicznej|<xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.ToolBar>, <xref:System.Windows.Controls.Menu>, <xref:System.Windows.Controls.ToolTip>itd.|
  |<xref:System.Windows.Controls.Primitives.RepeatButton>|Nazywany|<xref:System.Windows.Controls.Slider>, <xref:System.Windows.Controls.Primitives.ScrollBar>itd.|
  |<xref:System.Windows.Controls.Primitives.ScrollBar>|Nazywany|<xref:System.Windows.Controls.ScrollViewer>|
  |<xref:System.Windows.Controls.ScrollViewer>|Autonomicznej|<xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.Menu>, <xref:System.Windows.Controls.Frame>itd.|
  |<xref:System.Windows.Controls.Primitives.TabPanel>|Autonomicznej|<xref:System.Windows.Controls.TabControl>|
  |<xref:System.Windows.Controls.TextBox>|Nazywany|<xref:System.Windows.Controls.ComboBox>|
  |<xref:System.Windows.Controls.Primitives.TickBar>|Oparty na typie|<xref:System.Windows.Controls.Slider>|

- **Zminimalizuj wymagane powiązania określone przez użytkownika lub ustawienia właściwości dla elementów pomocnika**. Element pomocnika często wymaga pewnych powiązań lub ustawień właściwości, aby można było prawidłowo działać w szablonie kontrolki. Element pomocnika i kontrolka z szablonem powinny, jak to możliwe, ustalić te ustawienia. Podczas ustawiania właściwości lub ustanawiania powiązań należy zachować ostrożność, aby nie przesłaniać wartości ustawionych przez użytkownika. Poniżej przedstawiono następujące najlepsze rozwiązania:

  - Nazwane elementy pomocnika powinny być identyfikowane przez element nadrzędny, a element nadrzędny powinien określić wymagane ustawienia dla elementu pomocnika.

  - Elementy pomocnika oparte na typie powinny określić wymagane ustawienia bezpośrednio dla siebie. W ten sposób może być wymagane, aby element pomocnik mógł wysyłać zapytania dotyczące kontekstu informacji, w którym jest używany, łącznie z jego `TemplatedParent` (typ formantu szablonu, w którym jest używany). Na przykład <xref:System.Windows.Controls.ContentPresenter> automatycznie wiąże Właściwość `Content` `TemplatedParent` z właściwością <xref:System.Windows.Controls.ContentPresenter.Content%2A>, gdy jest używany w <xref:System.Windows.Controls.ContentControl> typie pochodnym.

  - Autonomiczne elementy pomocnika nie mogą być zoptymalizowane w ten sposób, ponieważ z definicji nie ma ani elementu pomocnika, ani elementu nadrzędnego.

- **Użyj właściwości Name, aby oflagować elementy w ramach szablonu**. Kontrolka, która musi znaleźć element w jego stylu, aby można było programowo uzyskać do niego dostęp, przy użyciu właściwości `Name` i modelu `FindName`. Kontrolka nie powinna zgłaszać wyjątku, gdy element nie zostanie znaleziony, ale dyskretnie i bezpiecznie wyłączyć funkcję, która wymaga tego elementu.

- **Korzystaj z najlepszych rozwiązań dotyczących stanu i zachowania kontroli w stylu.** Poniżej znajduje się uporządkowana lista najlepszych rozwiązań dotyczących zmian stanu kontroli i zachowań w stylu. Należy użyć pierwszego elementu na liście, który umożliwia scenariusz.

  1. Powiązanie właściwości. Przykład: powiązanie między <xref:System.Windows.Controls.ComboBox.IsDropDownOpen%2A?displayProperty=nameWithType> i <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A?displayProperty=nameWithType>.

  2. Wyzwalane zmiany właściwości lub animacje właściwości. Przykład: stan aktywowany <xref:System.Windows.Controls.Button>.

  3. Dotyczące. Przykład: <xref:System.Windows.Controls.Primitives.ScrollBar.LineUpCommand> / <xref:System.Windows.Controls.Primitives.ScrollBar.LineDownCommand> w <xref:System.Windows.Controls.Primitives.ScrollBar>.

  4. Autonomiczne elementy pomocnika. Przykład: <xref:System.Windows.Controls.Primitives.TabPanel> w <xref:System.Windows.Controls.TabControl>.

  5. Typy pomocników oparte na typach. Przykład: <xref:System.Windows.Controls.ContentPresenter> w <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Primitives.TickBar> w <xref:System.Windows.Controls.Slider>.

  6. Nazwane elementy pomocnika. Przykład: <xref:System.Windows.Controls.TextBox> w <xref:System.Windows.Controls.ComboBox>.

  7. Zdarzenia bąbelkowe z nazwanych typów pomocników. Jeśli nasłuchuje zdarzeń bąbelkowych z elementu style, należy wymagać jednoznacznego zidentyfikowania elementu generującego zdarzenie. Przykład: <xref:System.Windows.Controls.Primitives.Thumb> w <xref:System.Windows.Controls.ToolBar>.

  8. Niestandardowe zachowanie `OnRender`. Przykład: <xref:Microsoft.Windows.Themes.ButtonChrome> w <xref:System.Windows.Controls.Button>.

- **Używaj wyzwalaczy stylu (w przeciwieństwie do wyzwalaczy szablonów) oszczędnie**. Wyzwalacze, które mają wpływ na właściwości elementów w szablonie, muszą być zadeklarowane w szablonie. Wyzwalacze wpływające na właściwości kontrolki (No `TargetName`) mogą być deklarowane w stylu, chyba że wiadomo, że zmiana tego szablonu również powinna zniszczyć wyzwalacz.

- **Być spójne z istniejącymi wzorcami stylów.** Wiele razy istnieje wiele sposobów rozwiązania problemu. Należy pamiętać o i, jeśli to możliwe, spójnie z istniejącymi wzorcami stylów kontrolek. Jest to szczególnie ważne w przypadku formantów, które pochodzą z tego samego typu podstawowego (na przykład <xref:System.Windows.Controls.ContentControl>, <xref:System.Windows.Controls.ItemsControl>, <xref:System.Windows.Controls.Primitives.RangeBase>itd.).

- **Uwidaczniaj właściwości, aby włączyć typowe scenariusze dostosowywania bez retemplating**. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nie obsługuje części podłączanych/dostosowywalnych, dlatego użytkownik kontrolny jest pozostawiany tylko na dwie metody dostosowywania: ustawienie właściwości bezpośrednio lub ustawienia właściwości za pomocą stylów. Z tego względu należy wziąć pod uwagę ograniczoną liczbę właściwości, które są przeznaczone dla bardzo typowych scenariuszy dostosowywania o wysokim priorytecie, które w przeciwnym razie wymagają retemplating. Poniżej przedstawiono najlepsze rozwiązania dotyczące czasu i sposobu włączania scenariuszy dostosowywania:

  - Bardzo typowe dostosowania powinny być ujawniane jako właściwości kontrolki i używane przez szablon.

  - Mniej typowe (choć rzadko) dostosowania powinny być uwidaczniane jako dołączone właściwości i używane przez szablon.

  - Jest akceptowalny dla znanych, ale rzadkich dostosowań, aby wymagać retemplating.

<a name="Theme_Considerations"></a>

## <a name="theme-considerations"></a>Zagadnienia dotyczące motywu

- **Style motywów powinny próbować mieć spójną semantykę właściwości we wszystkich motywach, ale nie muszą mieć gwarancji**. W ramach swojej dokumentacji formant powinien mieć dokument opisujący semantykę właściwości kontrolki, czyli "znaczenie" właściwości formantu. Na przykład kontrolka <xref:System.Windows.Controls.ComboBox> powinna definiować znaczenie właściwości <xref:System.Windows.Controls.Control.Background%2A> w <xref:System.Windows.Controls.ComboBox>. Domyślne style kontrolki powinny być zgodne z semantyką zdefiniowaną w tym dokumencie dla wszystkich motywów. Z drugiej strony należy pamiętać, że semantyka właściwości może ulec zmianie z motywu na motyw. W niektórych przypadkach dana właściwość nie może być można wyrazić elementu w ramach ograniczeń wizualnych wymaganych przez określony motyw. (Na przykład motyw klasyczny nie ma pojedynczego obramowania, do którego `Thickness` można zastosować dla wielu kontrolek).

- **Style motywów nie muszą mieć spójnej semantyki wyzwalacza dla wszystkich motywów**. Zachowanie uwidocznione według stylu kontrolki przez wyzwalacze lub animacje może się różnić od motywu do motywu. Użytkownicy kontroli powinni mieć świadomość, że kontrolka niekoniecznie zastosuje ten sam mechanizm do osiągnięcia określonego zachowania dla wszystkich motywów. Jeden z motywów, na przykład, może używać animacji w celu wyszukania, gdy inny motyw używa wyzwalacza. Może to spowodować niespójności w zachowaniu zachowania na niestandardowych kontrolkach. (Zmiana właściwości tła może na przykład nie wpłynąć na stan aktywowany kontrolki, jeśli ten stan jest wyrażony przy użyciu wyzwalacza. Jeśli jednak stan aktywowany jest zaimplementowany przy użyciu animacji, zmiana na tło może nieodwracalnie przerwać animację i w związku z tym przechodzenie stanu.)

- **Style motywów nie muszą mieć spójnej semantyki "Layout" we wszystkich motywach**. Na przykład styl domyślny nie musi gwarantować, że kontrolka będzie zajmować ten sam rozmiar we wszystkich motywach lub gwarantuje, że formant będzie miał te same marginesy zawartości/uzupełnienie wszystkich motywów.

## <a name="see-also"></a>Zobacz także

- [Tworzenie szablonów i stylów](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Tworzenie kontrolek — omówienie](control-authoring-overview.md)
