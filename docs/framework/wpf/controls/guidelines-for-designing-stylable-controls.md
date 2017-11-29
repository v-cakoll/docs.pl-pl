---
title: "Wytyczne do projektowania kontrolek w określonych stylach"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- style design for controls [WPF]
- controls [WPF], style design
ms.assetid: c52dde45-a311-4531-af4c-853371c4d5f4
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 80edbd452be52e77a464ab29347dbe5d4067d0e1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="guidelines-for-designing-stylable-controls"></a>Wytyczne do projektowania kontrolek w określonych stylach
Ten dokument zawiera podsumowanie zestawu najlepszych rozwiązań, które należy rozważyć podczas projektowania formantu, który ma zostać łatwo stylable i templatable. Zdecydowaliśmy się do tego zestawu najlepszych rozwiązań za pomocą wielu prób i błędów podczas pracy nad stylów formantu motywu wbudowanych [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolować zestawu. Dowiedzieliśmy się, że pomyślnie stylów jest tyle funkcją modelu obiektu dobrze zaprojektowanego się sam stylu. Docelowa grupa odbiorców dla tego dokumentu jest autorem formantu nie autora stylu.  
  
  <a name="Terminology"></a>   
## <a name="terminology"></a>Terminologia  
 "Style i tworzenia szablonów" odwołują się do zestawu technologii, które umożliwiają kontroli autorowi odroczenie visual aspektów formant na szablon formantu i styl. Obejmuje to zestaw technologii:  
  
-   Style (w tym metody ustawiające właściwości, wyzwalaczy i scenorys).  
  
-   Zasoby.  
  
-   Szablony formantu.  
  
-   Szablony danych.  
  
 Aby obejrzeć wprowadzenie do stylów i tworzenia szablonów, zobacz [stylami i tworzenia szablonów](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
<a name="Before_You_Start__Understanding_Your_Control"></a>   
## <a name="before-you-start-understanding-your-control"></a>Przed rozpoczęciem: Opis formantu  
 Przed możesz przejść do poniższych wskazówek, ważne jest zrozumienie i zdefiniowanych typowe użycie formantu. Style przedstawia często niesfornych zestaw możliwości. Formanty, które są zapisywane do użycia (w wiele aplikacji przez wielu deweloperów) stają przed wyzwaniem czy style może służyć do dalekosiężną zmienić wygląd formantu. W rzeczywistości formantu nie wygląda nawet zamiarach autora formantu. Ponieważ elastyczność oferowane przez stylów jest zasadniczo nieograniczone, umożliwia pomysł typowe obciążenie można zakres swoje decyzje dotyczące.  
  
 Aby określić sposób użycia wspólnych formantu, warto pomyśleć o wartości oferty formantu. Co powoduje formantu do tabeli, która kontrolka nie mogą oferować? Użycie wspólnej nie oznacza żadnych szczególnych wygląd, ale raczej zasady klas formantu i uzasadnione zbiór oczekiwania dotyczące jego użytkowania. Ten opis pozwala na zapewnienie niektóre założenia dotyczące modelu kompozycji i zachowania zdefiniowany styl formantu w typowych przypadkach. W przypadku liczby <xref:System.Windows.Controls.ComboBox>, na przykład opis użycie wspólnej nie zapewniają wszelkie szczegółowe informacje o o czy określonego <xref:System.Windows.Controls.ComboBox> ma zaokrąglonymi narożnikami, ale podaje wgląd w fakcie który <xref:System.Windows.Controls.ComboBox> prawdopodobnie będzie konieczne okno podręczne i Niektóre sposób przełączania, czy jest on otwarty.  
  
<a name="General_Guidelines"></a>   
## <a name="general-guidelines"></a>Ogólne wskazówki  
  
-   **Nie Wymuszaj ściśle szablonu kontrakty.** Kontrakt szablonu formantu może składać się z elementów, poleceń, powiązania, wyzwalaczy i ustawień nawet właściwości, które są wymagane lub oczekiwano kontrolki do poprawnego.  
  
    -   Minimalizowanie możliwie umów.  
  
    -   Projekt wokół założenie, iż podczas projektowania czas (podczas przy użyciu narzędzia projektowe) jest typowe dla szablonu formantu być niekompletna. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]nie oferuje infrastrukturze stanu "Tworzenie", więc formantów ma zostać utworzony przy założeniu, że taki stan może być nieprawidłowy.  
  
    -   Nie zgłaszają wyjątki, gdy dowolnego aspektu kontrakt szablonu nie jest zakończony. Wzdłuż te wiersze panele nie powinien zgłosić wyjątków, jeśli ma zbyt wiele lub zbyt mało elementów podrzędnych.  
  
-   **Współczynnik funkcji urządzeń peryferyjnych do elementów pomocnika szablonu.** Każdej kontrolki powinny być koncentruje się na jego podstawową funkcjonalność i wartości true oferty i zdefiniowanych przez użycie wspólnej formantu. W tym celu, użyj elementy kompozycja i pomocnika w ramach szablonu, aby włączyć peryferyjne zachowania i wizualizacji, oznacza to, te zachowania i wizualizacje, które nie przyczyniają się do podstawowych funkcji formantu. Elementy pomocnika dzielą się na trzy kategorie:  
  
    -   **Autonomiczny** pomocnika typy publiczne i wielokrotnego użytku formantów lub podstawowych, które są używane "anonimowo" w szablonie, co oznacza, że element pomocnika ani formantu nie są znane innych. Z technicznego punktu widzenia dowolny element może być typu anonimowego, ale w tym kontekście termin opisano te typy, które hermetyzują funkcje specjalne na potrzeby scenariuszy z docelowej.  
  
    -   **Na podstawie typu** pomocnika elementy są nowe typy, które zapewniają funkcje specjalne. Elementy te są zwykle projektowane mniejszego zakresu funkcji niż typowych formantów lub w nim elementów podstawowych. W odróżnieniu od elementów pomocnika autonomiczny na podstawie typu pomocnika elementy są znane kontekst, w którym są używane i zwykle musi udostępniać dane kontroli, do których szablon należą.  
  
    -   **O nazwie** pomocnika elementy są typowe formanty lub podstawowych, które oczekuje formantu można znaleźć w jego szablonu na podstawie nazwy. Te elementy znajdują się dobrze znanej nazwy w szablonie, umożliwiając formantu można znaleźć elementu i korzystać z niego programowo. Może istnieć tylko jeden element o podanej nazwie w szablonie.  
  
     W poniższej tabeli przedstawiono elementy pomocnika zatrudnieni przez stylów formantu dzisiaj (Ta lista nie jest wyczerpująca):  
  
    |Element|Typ|Używane przez|  
    |-------------|----------|-------------|  
    |<xref:System.Windows.Controls.ContentPresenter>|Na podstawie typu|<xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.RadioButton>, <xref:System.Windows.Controls.Frame>i tak dalej (wszystkie <xref:System.Windows.Controls.ContentControl> typów)|  
    |<xref:System.Windows.Controls.ItemsPresenter>|Na podstawie typu|<xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.Menu>i tak dalej (wszystkie <xref:System.Windows.Controls.ItemsControl> typów)|  
    |<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|o nazwie|<xref:System.Windows.Controls.ToolBar>|  
    |<xref:System.Windows.Controls.Primitives.Popup>|Autonomiczny|<xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.ToolBar>, <xref:System.Windows.Controls.Menu>, <xref:System.Windows.Controls.ToolTip>i tak dalej|  
    |<xref:System.Windows.Controls.Primitives.RepeatButton>|o nazwie|<xref:System.Windows.Controls.Slider>, <xref:System.Windows.Controls.Primitives.ScrollBar>i tak dalej|  
    |<xref:System.Windows.Controls.Primitives.ScrollBar>|o nazwie|<xref:System.Windows.Controls.ScrollViewer>|  
    |<xref:System.Windows.Controls.ScrollViewer>|Autonomiczny|<xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.Menu>, <xref:System.Windows.Controls.Frame>i tak dalej|  
    |<xref:System.Windows.Controls.Primitives.TabPanel>|Autonomiczny|<xref:System.Windows.Controls.TabControl>|  
    |<xref:System.Windows.Controls.TextBox>|o nazwie|<xref:System.Windows.Controls.ComboBox>|  
    |<xref:System.Windows.Controls.Primitives.TickBar>|Na podstawie typu|<xref:System.Windows.Controls.Slider>|  
  
-   **Minimalizowanie wymaganych powiązań określone przez użytkownika lub ustawienia właściwości w elementach Pomocnika**. Jest typowe dla elementu pomocnika wymagające prawidłowego działania w szablonie kontroli niektórych powiązań lub ustawienia właściwości. Element pomocnika i kontrolki z szablonem ile to możliwe, należy ustanowić te ustawienia. Podczas ustawiania właściwości lub ustanawiania powiązań, ostrożność nie zastąpić wartościami ustawionymi przez użytkownika. Najlepsze rozwiązania w zakresie określonym są następujące:  
  
    -   Pomocnik nazwanych elementów powinny zostać zidentyfikowane na podstawie nadrzędnego i nadrzędnego należy określić wszystkie wymagane ustawienia w elemencie pomocnika.  
  
    -   Elementy na podstawie typu pomocnika należy określić wszystkie wymagane ustawienia bezpośrednio na siebie. W ten sposób mogą wymagać element pomocnika do zapytania informacje kontekstu, w którym jest on używany, łącznie z jej `TemplatedParent` (typu formantu szablon, w którym jest używany). Na przykład <xref:System.Windows.Controls.ContentPresenter> automatycznie wiąże `Content` właściwość jego `TemplatedParent` do jego <xref:System.Windows.Controls.ContentPresenter.Content%2A> właściwości, gdy są używane w <xref:System.Windows.Controls.ContentControl> typu pochodnego.  
  
    -   Nie można zoptymalizować autonomiczny pomocnika elementów w ten sposób, ponieważ, zgodnie z definicją element pomocnika ani nadrzędnego nie wie o innych.  
  
-   **Użyj właściwości Name elementy flagi w ramach szablonu**. Należy to zrobić formant, który musi znaleźć elementu w jego styl celu programowy dostęp przy użyciu `Name` właściwości i `FindName` modelu. Formant nie powinien zgłosić wyjątek, jeśli element nie został znaleziony, lecz dyskretnie i bezpiecznie wyłączyć funkcję, która wymagane tego elementu.  
  
-   **Należy stosować najlepsze rozwiązania dla wyrażania stanu kontroli i zachowanie w stylu.** Oto uporządkowaną listę najlepsze rozwiązania dotyczące wyrażanie kontroli zmian stanu i zachowanie w stylu. Należy użyć pierwszego elementu listy, która umożliwia danego scenariusza.  
  
    1.  Powiązania właściwości. Przykład: powiązanie między <xref:System.Windows.Controls.ComboBox.IsDropDownOpen%2A?displayProperty=nameWithType> i <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A?displayProperty=nameWithType>.  
  
    2.  Zmiany właściwości wyzwalanych lub właściwości animacji. Przykład: hover stan <xref:System.Windows.Controls.Button>.  
  
    3.  Polecenie. Przykład: <xref:System.Windows.Controls.Primitives.ScrollBar.LineUpCommand>  /  <xref:System.Windows.Controls.Primitives.ScrollBar.LineDownCommand> w <xref:System.Windows.Controls.Primitives.ScrollBar>.  
  
    4.  Elementy pomocnika autonomicznych. Przykład: <xref:System.Windows.Controls.Primitives.TabPanel> w <xref:System.Windows.Controls.TabControl>.  
  
    5.  Typy oparte na typie pomocnika. Przykład: <xref:System.Windows.Controls.ContentPresenter> w <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Primitives.TickBar> w <xref:System.Windows.Controls.Slider>.  
  
    6.  Nazwy elementów pomocnika. Przykład: <xref:System.Windows.Controls.TextBox> w <xref:System.Windows.Controls.ComboBox>.  
  
    7.  Przepuszcza zdarzenia z typów o nazwie pomocnika. Nasłuchiwać przepuszcza zdarzeń z elementu style, należy wymagać, aby element generowania zdarzenia można unikatowo zidentyfikować. Przykład: <xref:System.Windows.Controls.Primitives.Thumb> w <xref:System.Windows.Controls.ToolBar>.  
  
    8.  Niestandardowe `OnRender` zachowanie. Przykład: <xref:Microsoft.Windows.Themes.ButtonChrome> w <xref:System.Windows.Controls.Button>.  
  
-   **Oszczędnie korzystać wyzwalaczy styl (w przeciwieństwie do szablonu usługi wyzwalaczy)**. Wyzwalacze, które mają wpływ na właściwości elementów w szablonie musi zostać zadeklarowany w szablonie. Wyzwalacze, które mają wpływ na właściwości formantu (nie `TargetName`) może zadeklarowany w stylu, jeśli nie wiadomo, że zmiana szablonu należy także zniszczyć wyzwalacza.  
  
-   **Być zgodne z istniejących wzorców style.** Wiele razy istnieje wiele sposobów, aby rozwiązać problem. Należy pamiętać o i, jeśli możliwe, zgodnie z istniejącym Kontrola Wzorce style. Jest to szczególnie ważne dla formantów, które pochodzą z tego samego typu podstawowego (na przykład <xref:System.Windows.Controls.ContentControl>, <xref:System.Windows.Controls.ItemsControl>, <xref:System.Windows.Controls.Primitives.RangeBase>i tak dalej).  
  
-   **Udostępnianie właściwości, aby umożliwić typowe scenariusze dostosowywania bez retemplating**. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]nie obsługuje części podłączany/dostosowania, więc użytkownik formantu pozostaje tylko dwóch metod dostosowywania: Ustawianie właściwości bezpośrednio lub ustawiania właściwości za pomocą stylów. Z tym pamiętać należy do ograniczonej liczby właściwości celem scenariusze dostosowywania często, o wysokim priorytecie, które w przeciwnym razie będzie wymagać retemplating powierzchni. Poniżej przedstawiono najlepsze rozwiązania dotyczące kiedy i jak włączyć Dostosowywanie scenariusze:  
  
    -   Często dostosowania powinny być widoczne jako właściwości w formancie i używane przez szablon.  
  
    -   Dostosowywanie mniej typowe (choć nie rzadki przypadek) powinny być widoczne jako dołączone właściwości i używane przez szablon.  
  
    -   Jest możliwa do dostosowania znane, ale rzadko wymagają retemplating.  
  
<a name="Theme_Considerations"></a>   
## <a name="theme-considerations"></a>Zagadnienia dotyczące motywu  
  
-   **Style kompozycji powinien próbować ma semantyki właściwości spójna we wszystkich tematów, ale wprowadzać żadnej gwarancji**. W ramach jego dokumentacji formantu powinna mieć opisujący semantyki właściwości formantu, czyli "znaczenie" właściwości formantu. Na przykład <xref:System.Windows.Controls.ComboBox> kontroli należy zdefiniować znaczenie <xref:System.Windows.Controls.Control.Background%2A> właściwości <xref:System.Windows.Controls.ComboBox>. Domyślne style dla formantu powinien próbować wykonaj semantyki zdefiniowane w tym dokumencie we wszystkich tematów. Z drugiej strony, użytkownicy sterowania należy zwrócić uwagę, że semantyki właściwość można zmienić motyw motywu. W niektórych przypadkach dana właściwość nie może być można wyrazić w obszarze ograniczenia visual wymagane przez wybranego motywu. (Na przykład klasyczny, nie ma obramowanie jeden do którego `Thickness` można zastosować wiele formantów.)  
  
-   **Style kompozycji nie trzeba ma semantyki wyzwalacza spójna we wszystkich tematów**. Zachowanie udostępnione przez styl formantu za pomocą wyzwalaczy lub animacje mogą się różnić motywu motywu. Użytkownicy sterowania należy zwrócić uwagę, że formant może będzie zawiera ten sam mechanizm do osiągnięcia określone zachowanie we wszystkich tematów. Jeden motywu, na przykład może używać animacji Express zachowanie hover których innego motywu używa wyzwalacza. Może to spowodować niespójności w zachowywania zachowanie dla kontrolek niestandardowych. (Zmiana właściwości tła na przykład może nie mieć wpływ na stan aktywowanego formantu Jeśli ten stan jest wyrażona za pomocą wyzwalacza. Jednak jeśli stan aktywowanego jest implementowane za pomocą animacji, zmiana na tle może nieodwracalnemu spowodować przerwanie animacji i dlatego zmiany stanu.)  
  
-   **Style kompozycji nie trzeba ma semantykę spójnego "układu" we wszystkich tematów**. Na przykład domyślny styl nie trzeba zagwarantować, czy formant będzie zajmować tego samego rozmiaru w wszystkich tematów lub gwarantuje, że formant tej samej zawartości marginesy / dopełnienie we wszystkich tematów.  
  
## <a name="see-also"></a>Zobacz też  
 [Style i tworzenia szablonów](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Formant tworzenia — omówienie](../../../../docs/framework/wpf/controls/control-authoring-overview.md)
