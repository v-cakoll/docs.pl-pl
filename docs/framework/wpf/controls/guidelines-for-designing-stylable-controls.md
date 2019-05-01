---
title: Wytyczne do projektowania kontrolek w określonych stylach
ms.date: 03/30/2017
helpviewer_keywords:
- style design for controls [WPF]
- controls [WPF], style design
ms.assetid: c52dde45-a311-4531-af4c-853371c4d5f4
ms.openlocfilehash: 756cc821b1a9fe20741e390a1fe6e84d12cc6363
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62009971"
---
# <a name="guidelines-for-designing-stylable-controls"></a>Wytyczne do projektowania kontrolek w określonych stylach
W tym dokumencie przedstawiono podsumowanie zestaw najlepszych rozwiązań, aby wziąć pod uwagę podczas projektowania formantu, który ma być łatwe w określonych stylach i templatable. Zdecydowaliśmy się ten zestaw najlepszych rozwiązań za pośrednictwem wiele prób i błędów podczas pracy nad style kontrolki motyw wbudowanych [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zestaw formantów. Dowiedzieliśmy się, że pomyślnie stylów jest tak dużej ilości funkcją modelu obiektu dobrze zaprojektowanego się stylu samego. Odbiorców dla tego dokumentu jest autorem formantu, nie Autor stylu.  
  
  <a name="Terminology"></a>   
## <a name="terminology"></a>Terminologia  
 "Tworzenie szablonów i stylów" odnoszą się do zestawu technologii, które umożliwiają Autor kontroli, które mają być odroczone visual aspektów kontrolki stylu i szablonu kontrolki. Obejmuje to zestaw technologii:  
  
- Style (w tym metod ustawiających właściwości, wyzwalacze i scenorysów).  
  
- Zasoby.  
  
- Szablony kontrolek.  
  
- Szablony danych.  
  
 Wprowadzenie do tworzenia szablonów i stylów, zobacz [Tworzenie szablonów i stylów](styling-and-templating.md).  
  
<a name="Before_You_Start__Understanding_Your_Control"></a>   
## <a name="before-you-start-understanding-your-control"></a>Przed rozpoczęciem: Omówienie formantu  
 Zanim przejdziesz do poniższych wskazówek jest ważne, aby zrozumieć i zdefiniowano wspólne użycie kontrolki. Style udostępnia często niesfornych zbiór możliwości. Formanty, które są zapisywane do użycia szeroko (w wielu aplikacjach przez wielu deweloperów) stają że stylów może służyć do Week zmiany wyglądu formantu. W rzeczywistości formant ze stylem, nie może nawet przypominają zamiarach Autor kontroli. Ponieważ elastyczności oferowanej przez stylów jest zasadniczo pakiet, można użyć pomysł wspólne użycie ułatwiające zakresu decyzje.  
  
 Aby poznać wspólne użycie kontroli nad, dobrze jest myśleć o korzyści formantu. Co to formant przenieść do tabeli, która może oferować żadne inne formanty? Wspólne użycie pociąga za sobą żadnych szczególnych wyglądu, ale raczej filozofia formantu i uzasadnione zestaw oczekiwania dotyczące jej użycie. Tę wiedzę pozwala wprowadzić kilka założeń dotyczących modelu kompozycji i zachowania zdefiniowane w stylu formantu w Często spotykana. W przypadku właściwości <xref:System.Windows.Controls.ComboBox>, na przykład zrozumienie wspólnej wykorzystania nie daje żadnych szczegółowe informacje o czy określonego <xref:System.Windows.Controls.ComboBox> ma zaokrąglone narożniki, ale uzyskasz wgląd w działania, <xref:System.Windows.Controls.ComboBox> prawdopodobnie musi okno podręczne i jakiś sposób przełączania, czy jest on otwarty.  
  
<a name="General_Guidelines"></a>   
## <a name="general-guidelines"></a>Ogólne wskazówki  
  
- **Nie Wymuszaj ściśle kontraktów szablonu.** Kontrakt szablonu kontrolki może składać się z elementów, poleceń, powiązania, wyzwalaczy i ustawień nawet właściwości, które są wymagane lub oczekiwana dla formantu, który ma działać prawidłowo.  
  
    - Minimalizuj możliwie umów.  
  
    - Projekt na założeniu, że podczas projektowania czasu (to znaczy, gdy przy użyciu narzędzia do projektowania) jest typowe dla szablonu kontrolki, być niekompletna. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nie oferuje "Tworzenie" infrastruktury stanu, więc kontrolki ma zostać utworzony przy założeniu, że taki stan może być nieprawidłowa.  
  
    - Nie zgłaszają wyjątki, gdy nie występuje każdego aspektu kontrakt szablonu. Wzdłuż tych wierszy panele nie powinna zgłaszać wyjątków, ma zbyt wiele lub zbyt mało elementów podrzędnych.  
  
- **Współczynnik dodatkowa funkcjonalność na elementy pomocnika szablonu.** Każdy formant powinien być koncentruje się na jej podstawowe funkcje i korzyści true i zdefiniowane przez wspólne użycie formantu. W tym celu, za pomocą elementów kompozycji i pomocnicze w ramach szablonu Aby włączyć peryferyjne zachowań i wizualizacje, oznacza to, te zachowania i wizualizacje, które nie przyczyniają się do podstawowych funkcji formantu. Pomocnik elementy można podzielić na trzy kategorie:  
  
    - **Autonomiczny** pomocnika typy są formanty wielokrotnego użytku, jak i publicznych lub podstawowych, które są używane "anonimowo" w szablonie, co oznacza, że element pomocnika ani formant ze stylem pamiętać innych. Technicznie rzecz biorąc każdy element może być typu anonimowego, ale w tym kontekście pojęcie zawiera opis tych typów, które hermetyzują wyspecjalizowane funkcje określonych scenariuszach.  
  
    - **Na podstawie typu** pomocnika elementy są nowe typy, które hermetyzują funkcje specjalne. Te elementy zazwyczaj są skonstruowane z mniejszego zakresu funkcji niż wspólnych formantów albo pierwotnych. W odróżnieniu od elementów pomocnika autonomicznych elementy na podstawie typu pomocnika świadomość kontekst, w którym są używane i zazwyczaj musi udostępniać dane za pomocą kontrolki, do którego szablon należą.  
  
    - **O nazwie** pomocnika elementy są wspólnych formantów lub elementów podstawowych, które kontrolki spodziewa się znaleźć w jej szablonie w według nazwy. Te elementy są podane dobrze znaną nazwą w szablonie, dzięki czemu można kontrolki można znaleźć elementu i korzystać z niego programowo. Może istnieć tylko jeden element o podanej nazwie w szablonie.  
  
     W poniższej tabeli przedstawiono elementy pomocnika przez style kontrolki już dziś (Ta lista nie jest wyczerpująca):  
  
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
  
- **Minimalizuj wymaganych powiązań określone przez użytkownika lub ustawień właściwości dla elementów Pomocnika**. Bardzo często element pomocnika wymagać pewnych powiązania lub ustawień właściwości, aby działać prawidłowo w szablonie kontrolki. Element pomocnika i formant z szablonem w miarę możliwości, ustanowić te ustawienia. Podczas ustawiania właściwości lub ustanawiania powiązań, należy z rozwagą do nie zastępują wartości ustawione przez użytkownika. Najlepsze rozwiązania specyficzne są następujące:  
  
    - Elementy o nazwie pomocnika byli definiowani przez nadrzędne i element nadrzędny, należy określić wszystkie wymagane ustawienia w elemencie pomocnika.  
  
    - Elementy na podstawie typu pomocnika należy określić wszystkie wymagane ustawienia bezpośrednio na siebie. W ten sposób mogą wymagać od element pomocnika do wykonywania zapytań w kontekście informacji, w którym jest on używany, łącznie z jego `TemplatedParent` (typu formantu szablonu, w którym jest używana). Na przykład <xref:System.Windows.Controls.ContentPresenter> automatycznie wiąże `Content` właściwość jego `TemplatedParent` do jego <xref:System.Windows.Controls.ContentPresenter.Content%2A> właściwości, gdy są używane w <xref:System.Windows.Controls.ContentControl> typu pochodnego.  
  
    - Nie można zoptymalizować autonomiczny pomocnika elementów w ten sposób, ponieważ, zgodnie z definicją, element pomocnika ani element nadrzędny nie wie o innych.  
  
- **Użyj właściwości nazwy elementów flagi w szablonie**. Należy to zrobić formant, który musi znaleźć elementu w jego styl, aby programowo uzyskać dostęp za pomocą `Name` właściwości i `FindName` modelu. Kontrolki nie powinien zgłosić wyjątek, jeśli element nie zostanie znaleziony, ale dyskretnie i bez problemu zmieniała wyłączać funkcje, które wymagane tego elementu.  
  
- **Należy stosować najlepsze rozwiązania dla wyrażania stan formantu i zachowanie w stylu.** Oto najlepsze rozwiązania dotyczące wyrażające kontroli zmian stanu i zachowanie w stylu listy uporządkowanej. Należy użyć pierwszego elementu na liście, która umożliwia Twojemu scenariuszowi.  
  
    1. Powiązania właściwości. Przykład: powiązanie między <xref:System.Windows.Controls.ComboBox.IsDropDownOpen%2A?displayProperty=nameWithType> i <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A?displayProperty=nameWithType>.  
  
    2. Wyzwalane, zmiany właściwości lub animacje tej właściwości. Przykład: Umieść stan <xref:System.Windows.Controls.Button>.  
  
    3. polecenie. Przykład: <xref:System.Windows.Controls.Primitives.ScrollBar.LineUpCommand>  /  <xref:System.Windows.Controls.Primitives.ScrollBar.LineDownCommand> w <xref:System.Windows.Controls.Primitives.ScrollBar>.  
  
    4. Elementy pomocnika autonomicznych. Przykład: <xref:System.Windows.Controls.Primitives.TabPanel> w <xref:System.Windows.Controls.TabControl>.  
  
    5. Typy na podstawie typu pomocnika. Przykład: <xref:System.Windows.Controls.ContentPresenter> w <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Primitives.TickBar> w <xref:System.Windows.Controls.Slider>.  
  
    6. Elementy o nazwie pomocnika. Przykład: <xref:System.Windows.Controls.TextBox> w <xref:System.Windows.Controls.ComboBox>.  
  
    7. Przetwarzane zdarzenia z typów o nazwie pomocnika. Nasłuchiwania przetwarzane zdarzenia z elementu stylu należy wymagać, że element generowania zdarzenia można unikatowo zidentyfikować. Przykład: <xref:System.Windows.Controls.Primitives.Thumb> w <xref:System.Windows.Controls.ToolBar>.  
  
    8. Niestandardowe `OnRender` zachowanie. Przykład: <xref:Microsoft.Windows.Themes.ButtonChrome> w <xref:System.Windows.Controls.Button>.  
  
- **Oszczędnie korzystać styl Wyzwalacze (w przeciwieństwie do wyzwalaczy szablonu)**. Wyzwalacze, które mają wpływ na właściwości elementów w szablonie musi być zadeklarowany w szablonie. Wyzwalacze, które mają wpływ na właściwości kontrolki (nie `TargetName`) może być zadeklarowana w stylu, jeśli nie masz pewności, że zmiana szablonu powinny również zniszczyć wyzwalacza.  
  
- **Być zgodne z istniejących wzorców stylów.** Wiele razy, istnieje wiele sposobów, aby rozwiązać problem. Należy pamiętać o, a gdy możliwe, zgodnie z istniejącymi kontrolować wzorców stylów. Jest to szczególnie ważne dla formantów, które wynikają z tego samego typu podstawowego (na przykład <xref:System.Windows.Controls.ContentControl>, <xref:System.Windows.Controls.ItemsControl>, <xref:System.Windows.Controls.Primitives.RangeBase>i tak dalej).  
  
- **Udostępnianie właściwości w celu włączenia typowych scenariuszy dostosowywania bez retemplating**. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nie obsługuje podłączanych/dostosowywalne części, więc użytkownik pozostanie za pomocą dwóch metod dostosowywania: Ustawianie właściwości bezpośrednio lub ustawianie właściwości przy użyciu stylów. Mając to na uwadze należy do ograniczonej liczby właściwości przeznaczona dla scenariuszy dostosowywania bardzo popularne, o wysokim priorytecie, które w przeciwnym razie wymagałoby retemplating powierzchni. Poniżej przedstawiono najlepsze rozwiązania dotyczące czasu i sposobu dostosowywania scenariuszy:  
  
    - Bardzo często dostosowania powinien być widoczne jako właściwości kontrolki i używane przez szablon.  
  
    - Dostosowania mniej typowe (choć nie rzadkiego) powinien być widoczne jako dołączone właściwości i używane przez szablon.  
  
    - Jest możliwa do dostosowania znane, ale rzadko wymagają retemplating.  
  
<a name="Theme_Considerations"></a>   
## <a name="theme-considerations"></a>Zagadnienia dotyczące motywu  
  
- **Style motyw powinien próbować mieć właściwość spójną semantykę we wszystkie motywy, ale także wprowadzać żadnej gwarancji**. W ramach jego dokumentacji formant powinien mieć dokument z opisem semantyki właściwości formantu, czyli "rozumieniu" właściwości kontrolki. Na przykład <xref:System.Windows.Controls.ComboBox> kontroli należy zdefiniować znaczenia <xref:System.Windows.Controls.Control.Background%2A> właściwość w ramach <xref:System.Windows.Controls.ComboBox>. Domyślne style kontrolki powinien próbować postępuj zgodnie z semantyką zdefiniowane w tym dokumencie, we wszystkich tematów. Użytkownicy sterowania z drugiej strony, warto wiedzieć, semantyka właściwość można zmienić motyw motywu. W niektórych przypadkach dana właściwość nie może być można wyrazić w obszarze visual ograniczenia wymagane przez wybranego motywu. (Na przykład na klasyczny, nie ma pojedynczego obramowania, do którego `Thickness` może odnosić się do wielu formantów.)  
  
- **Style motyw nie trzeba mieć wyzwalacz spójną semantykę we wszystkie motywy**. Zachowanie udostępnianych przez stylu formantu, za pomocą wyzwalaczy lub animacje mogą się różnić motyw motywu. Kontroli użytkowników należy pamiętać, że formantu nie zawsze przydają się ten sam mechanizm do osiągnięcia określone zachowanie we wszystkie motywy. Jeden motywu, na przykład, może używać animacji do wyrażenia zachowania po wskazaniu wskaźnikiem gdzie innego motywu używa wyzwalacza. Może to spowodować niespójności w konserwacji zachowanie kontrolek niestandardowych. (Zmiana wartości właściwości w tle, na przykład nie wpływać na stan aktywowanego kontrolki Jeśli ten stan jest wyrażany za pomocą wyzwalacza. Jednak jeśli stan aktywowanego jest wdrażane za pomocą animacji, zmiana w tle może nieodwracalnemu spowodować przerwanie animacji i dlatego przejście stanu.)  
  
- **Style motyw musi mieć semantyki spójnego "układu" między wszystkie motywy**. Na przykład domyślny styl nie musi zagwarantować, że kontrolka będzie zajmować tego samego rozmiaru w wszystkie motywy lub gwarantuje, że kontrolka będzie miała ten sam marginesy zawartości / dopełnienie we wszystkich tematów.  
  
## <a name="see-also"></a>Zobacz także

- [Tworzenie szablonów i stylów](styling-and-templating.md)
- [Tworzenie kontrolek — omówienie](control-authoring-overview.md)
