---
title: Architektura WPF
ms.date: 03/30/2017
helpviewer_keywords:
- properties [WPF], attached
- attached properties [WPF]
- architecture [WPF]
- unmanaged components [WPF]
- affinity thread [WPF]
- Storyboards [WPF]
- milcore [WPF]
- components [WPF], unmanaged
- painter's algorithm
- interfaces [WPF], INotifyPropertyChange
- CommandBindings [WPF]
- data templates [WPF]
- thread [WPF], affinity
ms.assetid: 8579c10b-76ab-4c52-9691-195ce02333c8
ms.openlocfilehash: f4a6e6c2a63e58c40e0cca9c67b12d1f65af0d2e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59199430"
---
# <a name="wpf-architecture"></a>Architektura WPF
Ten temat zawiera przewodnik po hierarchii klas Windows Presentation Foundation (WPF). Obejmuje większość najważniejszych podsystemów [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]oraz opis sposobu interakcji. Szczegóły również niektóre wybory dokonane przez architektów z [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  

<a name="System_Object"></a>   
## <a name="systemobject"></a>System.Object  
 Podstawowy [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] model programowania jest dostępna za pośrednictwem kodu zarządzanego. Na wczesnym etapie fazy projektowania [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] wiele debatach o gdzie wiersz ma być rysowany między składniki zarządzane systemu i te niezarządzane. [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] Oferuje pewną liczbę funkcji, które dzięki niej programowanie i bardziej wydajna niezawodna (w tym zarządzanie pamięcią, obsługa błędów, wspólny system typów, itp.), ale wiąże się to kosztem.  
  
 Główne składniki [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zostały przedstawione na poniższej ilustracji. Czerwony części diagramu (PresentationFramework PresentationCore i milcore) są kodu głównych części [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Z tych opcji niezarządzanych składnika — milcore jest tylko jeden. Milcore są zapisywane w niezarządzanym kodzie w celu umożliwienia ścisłej integracji z programem [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)]. Wszystkie wyświetlane w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] odbywa się za pośrednictwem [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] aparatu, co umożliwia wydajne sprzętu i oprogramowania renderowania. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] wymagane jest także szczegółową kontrolę pamięci i wykonania. Aparat kompozycji w milcore jest bardzo poufnych i wymagane rezygnacji z wielu zalet wydajności [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] na wydajność.  
  
 ![Pozycja WPF w programie .NET Framework. ](./media/wpf-architect1.PNG "wpf_architect1")  
  
 Komunikacja między zarządzanymi i niezarządzanymi części [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] jest omówione w dalszej części tego tematu. Poniżej opisano w pozostałej części zarządzanego modelu programowania.  
  
<a name="System_Threading_DispatcherObject"></a>   
## <a name="systemthreadingdispatcherobject"></a>System.Threading.DispatcherObject  
 Większość obiektów w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] dziedziczyć <xref:System.Windows.Threading.DispatcherObject>, co umożliwia podstawowymi konstrukcjami zajmujących się współbieżności, wątki. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] opiera się na system obsługi komunikatów implementowany przez Dyspozytor. Ta funkcja działa podobnie do znanej [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] "pompy komunikatów"; w rzeczywistości [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] dyspozytora używa komunikatów User32 umożliwiające wykonywanie wywołań wielu wątków.  
  
 Ma naprawdę dwóch głównych pojęć Omawiając współbieżności w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] — koligacja dyspozytora i wątku.  
  
 W fazie projektowania [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], celem było przenieść do pojedynczego wątku wykonywania, ale non-thread "skoligaconym" model. Koligacja wątku występuje, gdy składnik używa tożsamość wątku wykonującego do przechowywania stanu określonego typu. Jest to najczęściej używany typ tego na potrzeby przechowywania stanu magazynu lokalnego wątku (TLS). Koligacja wątku wymaga każdego wątku logiczne wykonywania być własnością tylko jednego wątku fizycznych w systemie operacyjnym, który może stać się o znacznym wykorzystaniu pamięci. Na koniec model wątkowości w WPF został zsynchronizowany z istniejącego modelu wątkowości User32 pojedynczego wykonywania wątków z użyciem koligacji wątku. — To główny powód została współdziałanie systemów, takich jak [!INCLUDE[TLA2#tla_ole2.0](../../../../includes/tla2sharptla-ole2-0-md.md)], Schowka i Internet Explorer wszystkie wymagają wykonania koligacji (STA) jednego wątku.  
  
 Biorąc pod uwagę, że masz obiektów z wątkowości STA, potrzebujesz sposobu do komunikacji między wątkami, a sprawdzanie poprawności, które są poprawne wątku. Tu znajduje się rola Dyspozytor. Dyspozytor jest basic komunikat wysyła system z wieloma kolejkami priorytetami. Komunikaty przykłady powiadomienia nieprzetworzone danych wejściowych (przeniesione mysz), funkcje framework (układ) lub polecenia użytkownika (wykonywania tej metody). Przez pochodząca od <xref:System.Windows.Threading.DispatcherObject>, możesz utworzyć [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] obiekt zawierający zachowanie STA i zostanie przydzielony wskaźnik do dyspozytora w czasie jego tworzenia.  
  
<a name="System_Windows_DependencyObject"></a>   
## <a name="systemwindowsdependencyobject"></a>System.Windows.DependencyObject  
 Jedną z podstawowego filozofię architektury używane w budynku [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] został preferencji dla właściwości, za pośrednictwem metody lub zdarzenia. Właściwości deklaracyjne i Zezwalaj, aby łatwo określić przeznaczenie zamiast akcji. Obsługiwane też opartych na modelu lub danych opartych na systemie do wyświetlania zawartości interfejsu użytkownika. To podejście ma zamierzony efekt tworzenia innych właściwości, które można powiązać, aby można było skuteczniej kontrolować zachowanie aplikacji.  
  
 Aby uzyskać więcej systemu prowadzona przez właściwości, bogatszy system właściwości niż co [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] zapewnia był potrzebny. Prosty przykład tego bogactwa jest powiadomienia o zmianach. Aby włączyć dwie wiążących, konieczne będzie obie strony powiązania do obsługi powiadomień o zmianach. Aby mogła mieć problem związany z wartości właściwości, należy być powiadamiany po zmianie wartości właściwości. Microsoft .NET Framework ma interfejs **inotifypropertychange —**, co pozwala obiektu do opublikowania powiadomienia o zmianach, jednak jest to opcjonalne.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] udostępnia bogatszy system właściwości pochodną <xref:System.Windows.DependencyObject> typu. System właściwości jest naprawdę system właściwości "zależności", ponieważ śledzi zależności między wyrażeniami właściwości i wartości właściwości revalidates automatycznie, gdy zmienią się zależności. Na przykład, jeśli właściwość, która dziedziczy (takich jak <xref:System.Windows.Controls.Control.FontSize%2A>), system jest automatycznie aktualizowana, jeśli właściwość zmieni się na element nadrzędny elementu, który dziedziczy wartości.  
  
 Podstawą [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] system właściwość to pojęcie wyrażenie właściwości. W pierwszej wersji programu [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], system wyrażenie właściwości jest zamknięty i wyrażenia są dostarczane jako część RAM. Wyrażenia są Dlaczego system właściwość nie ma powiązania danych, style, lub dziedziczenia twardych kodowane, ale raczej dostarczone przez nowszy warstwy w ramach.  
  
 System właściwości udostępnia także magazynu rozrzedzonego w wartości właściwości. Ponieważ obiekty mogą mieć dziesiątek, jak (Jeśli nie setki) właściwości, a większość wartości jest w stanie domyślne (dziedziczone, ustawiane przez style, itp.), nie każde wystąpienie obiektu musi mieć pełne wagę dla każdej właściwości zdefiniowane w nim.  
  
 Końcowe nowa funkcja systemu właściwość to podstawowe pojęcie dołączone właściwości. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] elementy są tworzone na zasadzie kompozycji i ponowne użycie składnika. Często jest przypadek niektórych zawierającego element (takich jak <xref:System.Windows.Controls.Grid> elementu układu) będzie potrzebowała dodatkowych danych na elementy podrzędne, aby kontrolować swoje zachowanie (np. informacje wiersza/kolumny). Zamiast skojarzenie wszystkich właściwości z każdego elementu, każdy obiekt może zapewnić definicji właściwości dla jakiegokolwiek innego obiektu. Jest to podobne do funkcji "expando" języka JavaScript.  
  
<a name="System_Windows_Media_Visual"></a>   
## <a name="systemwindowsmediavisual"></a>System.Windows.Media.Visual  
 W systemie zdefiniowane następnym krokiem będzie niedługo pikseli na ekranie. <xref:System.Windows.Media.Visual> Klasa oferuje do tworzenia drzewa obiektów wizualnych, każdy opcjonalnie zawiera instrukcje rysowania oraz metadane dotyczące sposób renderowania tych instrukcji (wycinka, przekształcania, itp.). <xref:System.Windows.Media.Visual> została zaprojektowana jako bardzo lekka i elastyczne, więc większość funkcji bez publicznego [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] zagrożeń i dużym stopniu polegają na funkcjach wywołania zwrotnego chronionych.  
  
 <xref:System.Windows.Media.Visual> to naprawdę punkt wejścia do [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] kompozycji systemu. <xref:System.Windows.Media.Visual> punkt połączenia między tych dwóch podsystemów zarządzanej [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] i milcore niezarządzanych.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Wyświetla dane przez przeglądanie struktur niezarządzanych danych zarządzanych przez milcore. Te struktury, nazywane węzłami kompozycji reprezentuje drzewo hierarchiczną o renderowania instrukcje w każdym węźle. Tego drzewa zilustrowane na po prawej stronie rysunku poniżej, jest dostępny tylko za pośrednictwem protokołu obsługi komunikatów.  
  
 Podczas programowania [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], możesz utworzyć <xref:System.Windows.Media.Visual> elementów i typy pochodne, które wewnętrznie komunikacji z drzewa kompozycji za pośrednictwem protokołu obsługi komunikatów. Każdy <xref:System.Windows.Media.Visual> w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] może utworzyć jeden, żaden lub kilka węzłów kompozycji.  
  
 ![Windows Presentation Foundation drzewa wizualnego. ](./media/wpf-architecture2.PNG "wpf_architecture2")  
  
 Jest bardzo ważne szczegóły architektury, należy zwrócić uwagę tutaj — całe drzewo elementów wizualnych i instrukcji rysowania są buforowane. W warunkach grafiki [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] korzysta z zachowanej renderowania systemu. Dzięki temu system do odświeżenia wysokich częstotliwości odświeżania bez systemu kompozycji blokowania na wywołania zwrotne do kodu użytkownika. Pozwala to zapobiec wyglądu aplikacji nie odpowiada.  
  
 Inny ważnych szczegółów, który nie jest tak naprawdę można wyraźnie dostrzec w diagramie to, jak system wykonuje kompozycji.  
  
 W User32 i [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)], system działa w trybie natychmiastowym systemie wycinka. Gdy składnik musi być renderowana, system ustanawia granice wycinka, poza tym, które składnik nie jest dozwolona na dotyk pikseli i proszeni składnik do malowania pikseli, w tym polu. Ten system działa bardzo dobrze w systemach ograniczone przez ilość pamięci, gdy zmieni się coś, co ma się touch składnik — nie dwa składniki nigdy nie przyczynić się do koloru jednego piksela.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] używa "algorytm malowania" Malowanie modelu. Oznacza to, że zamiast przycinania każdego składnika, każdy składnik otrzyma monit o renderowanie z tyłu do przodu wyświetlanie. Dzięki temu każdy składnik do malowania za pośrednictwem poprzedniemu składnikowi wyświetlania. Zaletą tego modelu to, że może mieć kształty złożone, częściowo przezroczyste. Za pomocą nowoczesnego sprzętu grafiki nowoczesne, ten model jest stosunkowo krótkie (co nie jest wymagane podczas User32 / [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] zostały utworzone).  
  
 Jak wspomniano wcześniej, filozofią core [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] jest, aby przejść do bardziej deklaratywny model "property skoncentrowane na" programowania. W systemie visual to pojawia się na kilka ciekawych miejsc.  
  
 Po pierwsze, jeśli Twoim zdaniem o systemie grafiki zachowanej trybu, to naprawdę przechodzi od modelu typu imperatywne DrawLine/DrawLine do zorientowane na obiekty modelu danych — nowy wiersz () / Nowa Line(). To przeniesienie do opartych na danych, renderowanie umożliwia wykonywanie złożonych operacji na rysunku instrukcje można wyrazić za pomocą właściwości. Typy pochodzące od <xref:System.Windows.Media.Drawing> są faktycznymi modelu obiektów do renderowania.  
  
 Po drugie Jeśli system animacji, pojawi się, jest prawie całkowicie deklaratywnego. Zamiast konieczności dewelopera do obliczenia następnej lokalizacji lub następny kolor, można wyrazić animacji jako zbiór właściwości dla obiektu animacji. Animacje te można następnie wyrazić celem dewelopera lub Projektant (przenieść ten przycisk, w tym miejscu do miejsca w ciągu 5 sekund), a system może określić najbardziej efektywny sposób, aby to zrobić.  
  
<a name="System_Windows_UIElement"></a>   
## <a name="systemwindowsuielement"></a>System.Windows.UIElement  
 <xref:System.Windows.UIElement> Definiuje podstawowych podsystemów tym układ, dane wejściowe i zdarzenia.  
  
 Układ jest podstawowa koncepcja w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. W wielu systemach jest stały zestaw modeli układu (HTML obsługuje trzy modele dla układu; przepływu, ścieżką bezwzględną i tabele) lub bez modelu dla układu (User32 zaledwie obsługuje pozycjonowanie absolutne). [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] pracę, przy założeniu, że deweloperów i projektantów potrzebowała modelu układ elastyczny i rozszerzalny, który może być prowadzone przez wartości właściwości, a nie z logiką imperatywną. W <xref:System.Windows.UIElement> poziomu podstawowego kontraktu dla układu wprowadzono — dwa fazy modelu za pomocą <xref:System.Windows.UIElement.Measure%2A> i <xref:System.Windows.UIElement.Arrange%2A> przekazuje.  
  
 <xref:System.Windows.UIElement.Measure%2A> Umożliwia składnik, aby określić rozmiar, ile chcesz wykonać. Jest to osobne fazy z <xref:System.Windows.UIElement.Arrange%2A> ponieważ istnieje wiele sytuacji, w których element nadrzędny poprosi element podrzędny do mierzenia kilka razy, aby ustalić jego optymalnej położenie i rozmiar. Fakt, że elementy nadrzędne poproś elementów podrzędnych do mierzenia pokazuje innego klucza filozofią [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] — rozmiar do zawartości. Wszystkie formanty w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] umożliwiamy rozmiaru do naturalnym rozmiaru ich zawartości. To sprawia, że lokalizacja jest znacznie łatwiejsze i umożliwia dynamiczne układu elementów, jak zmienić rozmiar elementów. <xref:System.Windows.UIElement.Arrange%2A> Fazy umożliwia rodziców, aby ustawić położenie i rozmiar jest określany na ostateczny każdego elementu podrzędnego.  
  
 Mnóstwo czasu, często odbywa się komunikować informacje z danych wyjściowych strony [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] — <xref:System.Windows.Media.Visual> i powiązane obiekty. Jednak jest potężną innowacje na strony wejściowej. Prawdopodobnie zasadnicze znaczenie zmiany w modelu wejściowym dla [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] jest spójny model za pomocą którego zdarzenia wejściowe są kierowane przez system.  
  
 Dane wejściowe pochodzi jako sygnał na sterownik urządzenia trybu jądra i kierowana do korygowania procesu i wątku, proces skomplikowanych obejmujących jądra Windows i User32. Po wiadomości User32 odpowiadający danych wejściowych jest kierowany do [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], jest konwertowany na [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] pierwotnych danych wejściowych wiadomości i wysyłane do dyspozytora. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Umożliwia nieprzetworzone zdarzenia wejściowe są konwertowane na wielu rzeczywiste zdarzenia, włączenie funkcji, takich jak "MouseEnter" do zaimplementowania na niskim poziomie system gwarantowanego dostarczania.  
  
 Każde zdarzenie w danych wejściowych jest konwertowana na co najmniej dwóch zdarzeń — zdarzenie "preview" i rzeczywistego zdarzenia. Wszystkie zdarzenia w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] mają pojęcie routingu przez drzewo elementów. Zdarzenia są określane jako "będą się pojawiać", jeśli przechodzenie od celu w górę drzewa w katalogu głównym i są określane jako "tunelowania", gdyby rozpoczynają się od katalogu głównego i przechodzenie do elementu docelowego. Wprowadź tunelu zdarzenia (wersja zapoznawcza), włączenie dowolnego elementu w drzewie, możliwość filtrowania lub podejmowanie akcji na zdarzenie. Regularne zdarzenia (inne niż wersja zapoznawcza) pojawiać się następnie z celu do katalogu głównego.  
  
 Tego podziału między tunel i bąbelkowych fazy sprawia, że implementacja funkcje, takie jak klawiszy skrótów działać w spójny sposób w świecie złożonego. W User32 umożliwi wdrożenie klawiszy skrótów, dzięki pojedynczej tabeli globalny zawierający akceleratorów, które chce się obsługiwać (Ctrl + N mapowanie "Nowy"). W przypadku dispatcher dla danej aplikacji możesz wywołać **TranslateAccelerator** który wyśledzić komunikaty wejściowe w User32 i ustalają Jeśli dopasować dowolny zarejestrowanych akceleratora. W [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] to nie działa, ponieważ system jest w pełni "konfigurowalna" — dowolnego elementu można obsługiwać i korzystać z dowolnej skrótów klawiaturowych. Ten model fazy dwa dla danych wejściowych o umożliwia składnikom implementacji własnych "TranslateAccelerator".  
  
 Aby sprawy, wykonaj następujący krok jedną <xref:System.Windows.UIElement> wprowadza również pojęcie CommandBindings. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Systemu polecenia umożliwia deweloperom Definiowanie funkcji pod względem punktu końcowego polecenie — w coś, który implementuje <xref:System.Windows.Input.ICommand>. Polecenie powiązania włączyć element zdefiniować mapowanie między (nowy) poleceń i gestów w danych wejściowych (Ctrl + N). Wejściowy gestów i definicje polecenia można rozszerzać, a być połączone ze sobą w momencie użycia. Dzięki temu prosta, na przykład, aby umożliwić użytkownikowi końcowemu na dostosowywanie powiązania kluczy, które mają być użyte w obrębie aplikacji.  
  
 Do tego punktu w temacie "podstawowe" funkcje [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] — funkcje zaimplementowanych w zestawie PresentationCore zostały fokus. Podczas kompilowania [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], wyczyść separacji między fragmentami podstawowe (kontrakt dla układu, takich jak **miary** i **Rozmieść**) i części framework (na przykład implementacji określonego Układ, takich jak <xref:System.Windows.Controls.Grid>) została pożądanego rezultatu. Celem było zapewnienie punkt rozszerzalności niski w stosie, które pozwoliłoby zewnętrznych deweloperom tworzenie własnych struktur, jeśli potrzebne.  
  
<a name="System_Windows_FrameworkElement"></a>   
## <a name="systemwindowsframeworkelement"></a>System.Windows.FrameworkElement  
 <xref:System.Windows.FrameworkElement> mogą być czyszczone na dwa różne sposoby. Wprowadza zestaw zasad i dostosowania podsystemach, wprowadzona w niższych warstwach [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Przedstawia on także zestaw nowych podsystemy.  
  
 Podstawowe zasady, wynikające z <xref:System.Windows.FrameworkElement> wokół układ aplikacji. <xref:System.Windows.FrameworkElement> opiera się na kontrakt podstawowy układ wynikające z <xref:System.Windows.UIElement> i dodaje pojęcie układu "miejsce", który ułatwia autorom układ ma spójny zestaw właściwości opartych na semantykę układu. Właściwości, takie jak <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>, <xref:System.Windows.FrameworkElement.MinWidth%2A>, i <xref:System.Windows.FrameworkElement.Margin%2A> (Aby nazwać kilka) zapewniają wszystkie składniki pochodzące z <xref:System.Windows.FrameworkElement> spójne zachowanie w kontenery układów.  
  
 <xref:System.Windows.FrameworkElement> zapewnia także łatwiej [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] narażenia na wiele funkcji, znaleziono w warstwach podstawowej [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Na przykład <xref:System.Windows.FrameworkElement> zapewnia bezpośredni dostęp do animacji przy użyciu <xref:System.Windows.FrameworkElement.BeginStoryboard%2A> metody. A <xref:System.Windows.Media.Animation.Storyboard> zapewnia sposób skryptu wielu animacji z zestawem właściwości.  
  
 Dwie rzeczy najważniejszych, <xref:System.Windows.FrameworkElement> wprowadza to powiązanie danych i stylów.  
  
 Podsystem powiązanie danych w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] powinien być stosunkowo znany wszystkim osobom, który został użyty [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] lub [!INCLUDE[TLA#tla_aspnet](../../../../includes/tlasharptla-aspnet-md.md)] do tworzenia aplikacji [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. W każdym z tych systemów jest to prosty sposób express ma jedną lub więcej właściwości z danego elementu może być powiązane z elementu danych. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ma pełne wsparcie dla powiązania właściwości, przekształcania i powiązania listy.  
  
 Jedną z najbardziej interesujących funkcji powiązanie danych w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] jest wprowadzenie szablonów danych. Szablony danych umożliwiają deklaratywne określenie, jak można wywołać elementu danych. Zamiast tworzenia niestandardowego interfejsu użytkownika może być powiązana z danymi, możesz zamiast tego niewyłącznej problemu i pozwól danym określić ekran, który zostanie utworzony.  
  
 Style naprawdę jest uproszczone formą powiązanie danych. Za pomocą style możesz można powiązać zbiór właściwości z definicji udostępnionego co najmniej jedno wystąpienie elementu. Style zastosowane do elementu albo przez jawną odwołanie (przez ustawienie <xref:System.Windows.FrameworkElement.Style%2A> właściwości) lub niejawnie, kojarząc styl z [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] typ elementu.  
  
<a name="System_Windows_Controls_Control"></a>   
## <a name="systemwindowscontrolscontrol"></a>System.Windows.Controls.Control  
 Funkcja najbardziej znaczące kontrolki jest szablonów. Jeśli myślisz o WPF w skład systemu jako system zachowanej tryb renderowania, szablonów umożliwia kontrolce opisano jego renderowania w sposób sparametryzowane, deklaratywnego. A <xref:System.Windows.Controls.ControlTemplate> to naprawdę nic więcej niż skryptu, aby utworzyć zbiór podrzędnych elementów, z powiązaniami do właściwości oferowane przez kontrolkę.  
  
 <xref:System.Windows.Controls.Control> zawiera zestaw właściwości standardowych <xref:System.Windows.Controls.Control.Foreground%2A>, <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Padding%2A>, kilka, które autorom następnie można użyć do dostosowania wyświetlania kontrolki. Implementacja kontrolki zawiera model danych i interakcji z modelu. Model interakcji definiuje zestaw poleceń (np. Zamknij okna) i powiązania danych wejściowych gestów (np. Kliknięcie czerwony znak X w prawym górnym rogu okna). Model danych zawiera zbiór właściwości, aby dostosować model interakcji lub dostosować wyświetlanie (określoną w szablonie).  
  
 Ten podział między modelem danych (właściwości), model interakcji (poleceń i zdarzeń) i wyświetlanie modelu (szablonów) pozwala dostosować wygląd i zachowanie kontrolki.  
  
 Typowych aspektów modelu danych kontrolki jest modelu zawartości. Jeśli spojrzysz na kontrolki, takie jak <xref:System.Windows.Controls.Button>, zobaczysz, że ma właściwość o nazwie "Treści" o typie <xref:System.Object>. W [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] i [!INCLUDE[TLA#tla_aspnet](../../../../includes/tlasharptla-aspnet-md.md)], ta właściwość będzie zazwyczaj ciąg — jednak typ zawartości, która ogranicza można umieścić w przycisku. Zawartość dla przycisku może być prosty ciąg, obiekt danych złożony lub drzewo całego elementu. W przypadku obiektu danych szablonu danych służy do konstruowania wyświetlania.  
  
<a name="Summary"></a>   
## <a name="summary"></a>Podsumowanie  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] jest przeznaczona do umożliwiają tworzenie dynamicznych, opartych na systemach prezentacji danych. Każdej części systemu jest przeznaczone do tworzenia obiektów za pomocą zestawów właściwości tego zachowania dysków. Powiązanie danych stanowi podstawową część systemu i jest zintegrowana w każdej warstwie.  
  
 Tradycyjnych aplikacji do tworzenia, wyświetlania, a następnie wiążą się do niektórych danych. W [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], wszystkie informacje o formancie, każdy aspekt wyświetlacza, jest generowany przez pewien rodzaj powiązanie danych. Tekst wewnątrz przycisku jest wyświetlana, tworząc złożone kontrolki w przycisku i powiązanie jej wyświetlana właściwość zawartości przycisku.  
  
 Po rozpoczęciu tworzenia [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacje, powinien czuć się bardzo podobnie do funkcji. Można ustawić właściwości, użyj obiektów i powiązanie danych w taki sam sposób można utworzyć za pomocą [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] lub [!INCLUDE[TLA#tla_aspnet](../../../../includes/tlasharptla-aspnet-md.md)]. Za pomocą głębszego zbadania do architektury [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], przekonasz się, że możliwość istnieje do tworzenia aplikacji znacznie bogatsze całkowicie traktować dane ponieważ sterownik podstawowych aplikacji.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media.Visual>
- <xref:System.Windows.UIElement>
- <xref:System.Windows.Input.ICommand>
- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.Threading.DispatcherObject>
- <xref:System.Windows.Input.CommandBinding>
- <xref:System.Windows.Controls.Control>
- [Powiązanie danych — omówienie](../data/data-binding-overview.md)
- [Układ](layout.md)
- [Animacja — przegląd](../graphics-multimedia/animation-overview.md)
