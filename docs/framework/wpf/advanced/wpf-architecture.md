---
title: Architektura
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
ms.openlocfilehash: b16be8470a47f3e8e362feb0b13e10aa901baacb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187130"
---
# <a name="wpf-architecture"></a>Architektura WPF
Ten temat zawiera przewodnik po hierarchii klas Programu Windows Presentation Foundation (WPF). Obejmuje większość głównych podsystemów WPF I opisuje, jak współdziałają. Zawiera również szczegółowe informacje na temat niektórych wyborów dokonanych przez architektów WPF.  

<a name="System_Object"></a>
## <a name="systemobject"></a>System.Object  
 Podstawowy model programowania WPF jest udostępniane za pośrednictwem kodu zarządzanego. Na początku fazy projektowania WPF było wiele dyskusji na temat tego, gdzie linia powinna być rysowana między zarządzanymi składnikami systemu a niezarządzanymi. Środowisko CLR zapewnia szereg funkcji, które sprawiają, że rozwój jest bardziej produktywny i niezawodny (w tym zarządzanie pamięcią, obsługa błędów, system typowych typów itp.), ale są one kosztowne.  
  
 Główne składniki WPF są zilustrowane na poniższym rysunku. Czerwone sekcje diagramu (PresentationFramework, PresentationCore i milcore) są głównymi częściami kodu WPF. Z nich tylko jeden jest niezarządzanym składnikiem – milcore. Milcore jest napisany w niezarządzanym kodzie w celu umożliwienia ścisłej integracji z DirectX. Wszystkie wyświetlacze w WPF odbywa się za pośrednictwem silnika DirectX, co pozwala na wydajne renderowanie sprzętu i oprogramowania. WPF WPF również wymaga precyzyjnej kontroli nad pamięcią i wykonaniem. Silnik kompozycji w milicore jest niezwykle czuły na wydajność i wymaga rezygnacji z wielu zalet CLR, aby uzyskać wydajność.  
  
 ![Pozycja WPF WPF w ramach .NET Framework.](./media/wpf-architect1.PNG "wpf_architect1")  
  
 Komunikacja między zarządzanych i niezarządzanych części WPF WPF jest omówione w dalszej części tego tematu. Pozostała część modelu programowania zarządzanego jest opisana poniżej.  
  
<a name="System_Threading_DispatcherObject"></a>
## <a name="systemthreadingdispatcherobject"></a>System.Threading.DispatcherObject  
 Większość obiektów w WPF <xref:System.Windows.Threading.DispatcherObject>pochodzą od , który zapewnia podstawowe konstrukcje do czynienia z współbieżności i wątkowości. WPF WPF jest oparty na systemie obsługi wiadomości zaimplementowanym przez dyspozytora. To działa podobnie jak znane Pompy wiadomości Win32; w rzeczywistości dyspozytor WPF używa user32 wiadomości do wykonywania wywołań wątku krzyżowego.  
  
 Istnieją naprawdę dwa podstawowe pojęcia do zrozumienia podczas omawiania współbieżności w WPF — dyspozytora i koligacji wątku.  
  
 W fazie projektowania WPF, celem było przejście do pojedynczego wątku wykonywania, ale nie wątku "affinitized" modelu. Koligacja wątku dzieje się, gdy składnik używa tożsamości wątku wykonującego do przechowywania pewnego typu stanu. Najczęstszą formą tego jest użycie magazynu lokalnego wątku (TLS) do przechowywania stanu. Koligacja wątku wymaga, aby każdy logiczny wątek wykonywania był własnością tylko jednego wątku fizycznego w systemie operacyjnym, który może stać się intensywnie korzystający z pamięci. W końcu model wątkowości WPF był zsynchronizowany z istniejącym modelem wątkowości User32 wykonywania jednowtowego z koligacją wątku. Głównym powodem tego było współdziałanie — systemy takie jak OLE 2.0, schowek i program Internet Explorer wymagają wykonywania koligacji pojedynczego wątku (STA).  
  
 Biorąc pod uwagę, że masz obiekty z wątków STA, należy sposób komunikowania się między wątkami i sprawdź, czy jesteś na poprawny wątek. Tutaj leży rola dyspozytora. Dyspozytor jest podstawowym systemem dyspozytora wiadomości, z wieloma priorytetowymi kolejkami. Przykłady komunikatów obejmują nieprzetworzone powiadomienia wejściowe (przenoszone myszą), funkcje struktury (układ) lub polecenia użytkownika (wykonaj tę metodę). Wywodząc <xref:System.Windows.Threading.DispatcherObject>się z obiektu CLR, który ma zachowanie STA i zostanie podany wskaźnik do dyspozytora w czasie tworzenia.  
  
<a name="System_Windows_DependencyObject"></a>
## <a name="systemwindowsdependencyobject"></a>System.Windows.DependencyObject  
 Jedną z podstawowych filozofii architektonicznych stosowanych w budowaniu WPF było preferowanie właściwości nad metodami lub zdarzeniami. Właściwości są deklaratywne i umożliwiają łatwiejsze określenie intencji zamiast akcji. Obsługa modelu opartego na modelu lub opartego na danych systemu do wyświetlania zawartości interfejsu użytkownika. Ta filozofia miała zamierzony efekt tworzenia większej liczby właściwości, które można powiązać, w celu lepszego kontrolowania zachowania aplikacji.  
  
 Aby mieć więcej systemu napędzanego przez właściwości, potrzebny był bogatszy system właściwości niż to, co zapewnia CLR. Prostym przykładem tego bogactwa są powiadomienia o zmianach. Aby włączyć dwukierunkowe powiązanie, potrzebujesz obu stron powiązania do obsługi powiadomienia o zmianie. Aby zachowanie było powiązane z wartościami właściwości, należy otrzymywać powiadomienia o zmianie wartości właściwości. Microsoft .NET Framework ma interfejs **INotifyPropertyChange**, który umożliwia obiektowi publikowanie powiadomień o zmianie, jednak jest to opcjonalne.  
  
 WPF WPF zapewnia bogatszy system <xref:System.Windows.DependencyObject> właściwości, pochodzące od typu. System właściwości jest naprawdę "zależności" system właściwości, w tym śledzi zależności między wyrażeniami właściwości i automatycznie ponownie zmienia waloryzuje wartości właściwości po zmianie zależności. Na przykład jeśli masz właściwość, która <xref:System.Windows.Controls.Control.FontSize%2A>dziedziczy (jak ), system jest automatycznie aktualizowany, jeśli właściwość zmienia się na element nadrzędny elementu, który dziedziczy wartość.  
  
 Podstawą systemu właściwości WPF jest pojęcie wyrażenia właściwości. W tej pierwszej wersji WPF WPF system wyrażeń właściwości jest zamknięty, a wyrażenia są dostarczane jako część struktury. Wyrażenia są dlaczego system właściwości nie ma powiązania danych, stylizacji lub dziedziczenia zakodowane na czas, ale raczej dostarczane przez późniejsze warstwy w ramach.  
  
 System właściwości zapewnia również rozrzedzone przechowywanie wartości właściwości. Ponieważ obiekty mogą mieć dziesiątki (jeśli nie setki) właściwości, a większość wartości jest w stanie domyślnym (dziedziczona, ustawiana przez style itp.), nie każde wystąpienie obiektu musi mieć pełną wagę każdej właściwości zdefiniowanej na nim.  
  
 Ostatnią nową cechą systemu nieruchomości jest pojęcie dołączonych właściwości. Elementy WPF są zbudowane na zasadzie składu i ponownego użycia komponentu. Często jest tak, że niektóre zawierające <xref:System.Windows.Controls.Grid> element (jak element układu) potrzebuje dodatkowych danych na elementy podrzędne do kontrolowania jego zachowanie (jak wiersz/kolumna informacji). Zamiast kojarzenia wszystkich tych właściwości z każdym elementem, każdy obiekt może podać definicje właściwości dla dowolnego innego obiektu. Jest to podobne do funkcji "expando" języka JavaScript.  
  
<a name="System_Windows_Media_Visual"></a>
## <a name="systemwindowsmediavisual"></a>System.Windows.Media.Visual  
 Po zdefiniowaeniu systemu następnym krokiem jest rysowanie pikseli na ekranie. Klasa <xref:System.Windows.Media.Visual> umożliwia tworzenie drzewa obiektów wizualnych, z których każdy opcjonalnie zawiera instrukcje rysowania i metadane dotyczące sposobu renderowania tych instrukcji (przycinanie, transformacja itp.). <xref:System.Windows.Media.Visual>został zaprojektowany tak, aby był niezwykle lekki i elastyczny, więc większość funkcji nie ma publicznego interfejsu API i w dużym stopniu polega na chronionych funkcjach wywołania zwrotnego.  
  
 <xref:System.Windows.Media.Visual>jest naprawdę punktem wejścia do systemu kompozycji WPF. <xref:System.Windows.Media.Visual>jest punktem połączenia między tymi dwoma podsystemami, zarządzanym interfejsem API i niezarządzanym milcore.  
  
 WPF WPF wyświetla dane przez przechodzenie przez struktury danych niezarządzanych zarządzanych przez milcore. Te struktury, zwane węzłami kompozycji, reprezentują hierarchiczne drzewo wyświetlania z instrukcjami renderowania w każdym węźle. To drzewo, zilustrowane po prawej stronie poniższego rysunku, jest dostępne tylko za pośrednictwem protokołu wiadomości.  
  
 Podczas programowania WPF, <xref:System.Windows.Media.Visual> można utworzyć elementy i typy pochodne, które wewnętrznie komunikują się z drzewa kompozycji za pośrednictwem tego protokołu obsługi wiadomości. Każdy <xref:System.Windows.Media.Visual> w WPF może utworzyć jeden, brak lub kilka węzłów kompozycji.  
  
 ![Drzewo wizualne programu Windows Presentation Foundation Foundation.](./media/wpf-architecture2.PNG "wpf_architecture2")  
  
 Jest tu bardzo ważny szczegół architektoniczny - całe drzewo wizualizacji i instrukcji rysowania jest buforowane. Pod względem graficznym WPF WPF używa zachowanego systemu renderowania. Dzięki temu system do odświeżania z dużą szybkością odświeżania bez blokowania systemu kompozycji na wywołania zwrotne do kodu użytkownika. Pomaga to zapobiec pojawianiu się aplikacji, która nie odpowiada.  
  
 Innym ważnym szczegółem, który nie jest tak naprawdę zauważalny na diagramie, jest to, jak system faktycznie wykonuje kompozycję.  
  
 W User32 i GDI system działa w systemie przycinania trybu natychmiastowego. Gdy komponent musi być renderowany, system ustanawia granice przycinania, poza którymi składnik nie może dotykać pikseli, a następnie komponent jest proszony o malowanie pikseli w tym polu. System ten działa bardzo dobrze w systemach o ograniczonej pamięci, ponieważ gdy coś się zmienia, wystarczy dotknąć dotkniętego komponentu - żadne dwa składniki nigdy nie przyczyniają się do koloru pojedynczego piksela.  
  
 WPF używa modelu malarskiego "algorytm malarza". Oznacza to, że zamiast przycinania każdego komponentu, każdy komponent jest proszony o renderowanie od tyłu do przodu wyświetlacza. Dzięki temu każdy komponent może malować na wyświetlaczu poprzedniego komponentu. Zaletą tego modelu jest to, że można mieć złożone, częściowo przezroczyste kształty. Dzięki dzisiejszemu nowoczesnemu sprzętowi graficznemu model ten jest stosunkowo szybki (co nie miało miejsca w przypadku tworzenia User32/ GDI).  
  
 Jak wspomniano wcześniej, podstawową filozofią WPF jest przejście do bardziej deklaratywnego, "zorientowanego na właściwości" modelu programowania. W systemie wizualnym pojawia się to w kilku ciekawych miejscach.  
  
 Po pierwsze, jeśli myślisz o systemie graficznym trybu zachowanego, jest to naprawdę odejście od imperatywu DrawLine / DrawLine modelu typu, do modelu zorientowanego na dane - nowy Line()/new Line(). To przejście do renderowania opartego na danych umożliwia złożone operacje na instrukcjach rysowania, które mają być wyrażone przy użyciu właściwości. Typy pochodzące <xref:System.Windows.Media.Drawing> z są skutecznie modelu obiektu do renderowania.  
  
 Po drugie, jeśli ocenisz system animacji, zobaczysz, że jest prawie całkowicie deklaratywny. Zamiast wymagać od dewelopera obliczenia następnej lokalizacji lub następnego koloru, można wyrazić animacje jako zestaw właściwości obiektu animacji. Animacje te można następnie wyrazić intencji dewelopera lub projektanta (przenieść ten przycisk z tego miejsca w tym miejscu w 5 sekund), a system może określić najbardziej efektywny sposób, aby to osiągnąć.  
  
<a name="System_Windows_UIElement"></a>
## <a name="systemwindowsuielement"></a>System.Windows.UIElement  
 <xref:System.Windows.UIElement>definiuje podstawowe podsystemy, w tym Układ, Dane wejściowe i Zdarzenia.  
  
 Układ jest podstawową koncepcją w WPF. W wielu systemach istnieje albo stały zestaw modeli układu (HTML obsługuje trzy modele układu; przepływ, bezwzględny i tabele) lub brak modelu układu (User32 naprawdę obsługuje tylko pozycjonowanie bezwzględne). WPF WPF rozpoczął się od założenia, że deweloperzy i projektanci chcieli elastyczny, rozszerzalny model układu, który może być napędzany przez wartości właściwości, a nie logiki imperatywnej. Na <xref:System.Windows.UIElement> poziomie wprowadza się podstawowy kontrakt na układ – <xref:System.Windows.UIElement.Measure%2A> <xref:System.Windows.UIElement.Arrange%2A> model dwufazowy z i przechodzi.  
  
 <xref:System.Windows.UIElement.Measure%2A>umożliwia składnikowi określenie, ile rozmiaru chciałby podjąć. Jest to oddzielna <xref:System.Windows.UIElement.Arrange%2A> faza, ponieważ istnieje wiele sytuacji, w których element nadrzędny poprosi element podrzędny o kilka razy zmierzyć, aby określić jego optymalną pozycję i rozmiar. Fakt, że elementy nadrzędne poprosić elementy podrzędne do pomiaru pokazuje inną kluczową filozofię WPF — rozmiar do zawartości. Wszystkie formanty w WPF obsługują możliwość rozmiaru do naturalnego rozmiaru ich zawartości. Dzięki temu lokalizacja znacznie łatwiejsze i pozwala na dynamiczny układ elementów, jak rzeczy zmienić rozmiar. Faza <xref:System.Windows.UIElement.Arrange%2A> umożliwia elementowi nadrzędnemu położenie i określenie ostatecznego rozmiaru każdego dziecka.  
  
 Dużo czasu jest często spędzane na rozmowach <xref:System.Windows.Media.Visual> o stronie wyjściowej WPF — i powiązanych obiektów. Jednak po stronie nakładów jest jednak również ogromna ilość innowacji. Prawdopodobnie najbardziej podstawową zmianą w modelu wejściowym dla WPF jest spójny model, za pomocą którego zdarzenia wejściowe są kierowane przez system.  
  
 Dane wejściowe pochodzą jako sygnał na sterowniku urządzenia trybu jądra i pobiera kierowane do prawidłowego procesu i wątku przez skomplikowany proces z udziałem jądra systemu Windows i User32. Gdy user32 komunikat odpowiadający dane wejściowe jest kierowany do WPF, jest konwertowany na WPF nieprzetworzony komunikat wejściowy i wysyłane do dyspozytora. WPF WPF umożliwia raw zdarzenia wejściowe mają być konwertowane na wiele rzeczywistych zdarzeń, dzięki czemu funkcje, takie jak "MouseEnter" mają być implementowane na niskim poziomie systemu z gwarantowaną dostawą.  
  
 Każde zdarzenie wejściowe jest konwertowane na co najmniej dwa zdarzenia — zdarzenie "podgląd" i rzeczywiste zdarzenie. Wszystkie zdarzenia w WPF mają pojęcie routingu za pośrednictwem drzewa elementów. Zdarzenia są mówi się , że "bańka", jeśli przechodzenie od celu w górę drzewa do katalogu głównego, i mówi się, że "tunel", jeśli zaczynają się od katalogu głównego i przechodzenie w dół do celu. Tunel zdarzeń podglądu wejściowego, włączając dowolny element w drzewie możliwość filtrowania lub podjęcia działań w przypadku. Zdarzenia regularne (nie podgląd) następnie bańki od obiektu docelowego do katalogu głównego.  
  
 Ten podział między fazą tunelu i bąbelkową sprawia, że implementacja funkcji, takich jak akceleratory klawiatury, działa w spójny sposób w świecie kompozytowym. W user32 można zaimplementować akceleratory klawiatury, mając jedną globalną tabelę zawierającą wszystkie akceleratory, które chcesz obsługiwać (Ctrl + N mapowanie do "Nowy"). W dyspozytorze dla aplikacji należy **wywołać TranslateAccelerator,** który wąchać komunikaty wejściowe w User32 i określić, czy którykolwiek z nich dopasowane zarejestrowany akcelerator. W WPF nie będzie działać, ponieważ system jest w pełni "composable" - każdy element może obsługiwać i używać dowolnego akceleratora klawiatury. Posiadanie tego dwufazowego modelu wprowadzania umożliwia komponentom implementowanie własnego "TranslateAccelerator".  
  
 Aby zrobić ten krok <xref:System.Windows.UIElement> dalej, wprowadza również pojęcie CommandBindings. System poleceń WPF umożliwia deweloperom definiowanie funkcji w kategoriach <xref:System.Windows.Input.ICommand>punktu końcowego polecenia – czegoś, co implementuje. Powiązania poleceń umożliwiają elementowi zdefiniowanie mapowania między gestem wejściowym (Ctrl+N) a poleceniem (Nowy). Gesty wejściowe i definicje poleceń są rozszerzalne i mogą być połączone ze sobą w czasie użytkowania. To sprawia, że trywialne, na przykład, aby umożliwić użytkownikowi końcowemu dostosować powiązania klucza, które mają być używane w aplikacji.  
  
 Do tego punktu w temacie, "core" funkcje WPF — funkcje zaimplementowane w PresentationCore zestawu, były w centrum uwagi. Podczas tworzenia WPF, czyste oddzielenie elementów fundamentowych (jak umowa na układ z **Measure** i **Arrange)** <xref:System.Windows.Controls.Grid>i elementy ramowe (jak implementacja określonego układu, jak) był pożądany wynik. Celem było zapewnienie punktu rozszerzalności niski w stosie, który pozwoliłby zewnętrznym deweloperom na tworzenie własnych struktur w razie potrzeby.  
  
<a name="System_Windows_FrameworkElement"></a>
## <a name="systemwindowsframeworkelement"></a>System.Windows.FrameworkElement  
 <xref:System.Windows.FrameworkElement>można przyjrzeć się na dwa różne sposoby. Wprowadza zestaw zasad i dostosowań w podsystemach wprowadzonych w niższych warstwach WPF. Wprowadza również zestaw nowych podsystemów.  
  
 Podstawowe zasady wprowadzone <xref:System.Windows.FrameworkElement> przez jest wokół układu aplikacji. <xref:System.Windows.FrameworkElement>opiera się na podstawowym kontrakcie układu wprowadzonym przez <xref:System.Windows.UIElement> i dodaje pojęcie układu "slot", który ułatwia autorom układu mieć spójny zestaw semantyki układu opartego na właściwościach. Właściwości, <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>takie <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> <xref:System.Windows.FrameworkElement.MinWidth%2A>jak <xref:System.Windows.FrameworkElement.Margin%2A> , , i (aby wymienić <xref:System.Windows.FrameworkElement> tylko kilka) dają wszystkie składniki pochodzące ze spójnego zachowania wewnątrz kontenerów układu.  
  
 <xref:System.Windows.FrameworkElement>zapewnia również łatwiejsze narażenie interfejsu API na wiele funkcji znalezionych w podstawowych warstwach WPF. Na przykład <xref:System.Windows.FrameworkElement> zapewnia bezpośredni dostęp <xref:System.Windows.FrameworkElement.BeginStoryboard%2A> do animacji za pomocą metody. A <xref:System.Windows.Media.Animation.Storyboard> umożliwia skrypt wiele animacji względem zestawu właściwości.  
  
 Dwie najważniejsze rzeczy, <xref:System.Windows.FrameworkElement> które wprowadza są powiązania danych i style.  
  
 Podsystem wiązania danych w WPF powinien być względnie znany każdemu, kto używał formularzy systemu Windows lub ASP.NET do tworzenia aplikacji [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. W każdym z tych systemów istnieje prosty sposób, aby wyrazić, że chcesz, aby jedna lub więcej właściwości z danego elementu były powiązane z fragmentem danych. WPF WPF ma pełną obsługę powiązania właściwości, transformacji i powiązania listy.  
  
 Jedną z najbardziej interesujących funkcji powiązania danych w WPF jest wprowadzenie szablonów danych. Szablony danych umożliwiają deklaratywnie określić, jak fragment danych powinny być wizualizowane. Zamiast tworzyć niestandardowy interfejs użytkownika, który może być powiązany z danymi, można zamiast tego obrócić problem i pozwolić danym określić wyświetlanie, które zostaną utworzone.  
  
 Stylizacja jest naprawdę lekką formą wiązania danych. Za pomocą stylizacji można powiązać zestaw właściwości z definicji udostępnionej do jednego lub więcej wystąpień elementu. Style są stosowane do elementu przez jawne odwołanie <xref:System.Windows.FrameworkElement.Style%2A> (przez ustawienie właściwości) lub niejawnie, kojarząc styl z typem CLR elementu.  
  
<a name="System_Windows_Controls_Control"></a>
## <a name="systemwindowscontrolscontrol"></a>System.Windows.Controls.Control  
 Najważniejszą cechą formantu jest tworzenie szablonów. Jeśli myślisz o systemie kompozycji WPF jako system renderowania trybu zachowanego, templating umożliwia formantowi opisanie jego renderowania w sposób sparametryzowany, deklaratywny. A <xref:System.Windows.Controls.ControlTemplate> jest naprawdę nic więcej niż skrypt do tworzenia zestawu elementów podrzędnych, z powiązań do właściwości oferowanych przez formant.  
  
 <xref:System.Windows.Controls.Control>udostępnia zestaw właściwości <xref:System.Windows.Controls.Control.Foreground%2A>zapasów, <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Control.Padding%2A>, , aby wymienić tylko kilka, których autorów szablonów można następnie użyć do dostosowania wyświetlania formantu. Implementacja formantu zapewnia model danych i model interakcji. Model interakcji definiuje zestaw poleceń (takich jak Zamknij dla okna) i powiązania z gestami wejściowymi (na przykład kliknięcie czerwonego X w górnym rogu okna). Model danych udostępnia zestaw właściwości, aby dostosować model interakcji lub dostosować wyświetlanie (określone przez szablon).  
  
 Ten podział między model danych (właściwości), model interakcji (polecenia i zdarzenia) i model wyświetlania (szablony) umożliwia pełne dostosowanie wyglądu i zachowania formantu.  
  
 Typowym aspektem modelu danych formantów jest model zawartości. Jeśli spojrzysz na <xref:System.Windows.Controls.Button>formant jak , zobaczysz, że ma właściwość o nazwie "Zawartość" typu <xref:System.Object>. W formularzach systemu Windows i ASP.NET ta właściwość zazwyczaj będzie ciągiem znaków — jednak ogranicza typ zawartości, którą można umieścić w przycisku. Zawartość przycisku może być prostym ciągiem, złożonym obiektem danych lub całym drzewem elementów. W przypadku obiektu danych szablon danych jest używany do konstruowania wyświetlania.  
  
<a name="Summary"></a>
## <a name="summary"></a>Podsumowanie  
 WPF WPF jest przeznaczony do tworzenia dynamicznych, opartych na danych systemów prezentacji. Każda część systemu jest przeznaczona do tworzenia obiektów za pomocą zestawów właściwości, które napędzają zachowanie. Powiązanie danych jest podstawową częścią systemu i jest zintegrowane w każdej warstwie.  
  
 Tradycyjne aplikacje tworzą wyświetlanie, a następnie wiążą się z niektórymi danymi. W WPF WPF wszystko o formancie, każdy aspekt wyświetlania, jest generowany przez jakiś typ powiązania danych. Tekst znajdujący się wewnątrz przycisku jest wyświetlany przez utworzenie skomponowanego formantu wewnątrz przycisku i powiązanie jego wyświetlania z właściwością zawartości przycisku.  
  
 Po rozpoczęciu tworzenia aplikacji opartych na WPF, powinno czuć się bardzo znane. Właściwości, obiekty i powiązania danych można ustawić w taki sam sposób, jak za pomocą formularzy systemu Windows lub ASP.NET. Dzięki głębszemu badaniu architektury WPF, przekonasz się, że istnieje możliwość tworzenia znacznie bogatszych aplikacji, które zasadniczo traktują dane jako podstawowy sterownik aplikacji.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Media.Visual>
- <xref:System.Windows.UIElement>
- <xref:System.Windows.Input.ICommand>
- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.Threading.DispatcherObject>
- <xref:System.Windows.Input.CommandBinding>
- <xref:System.Windows.Controls.Control>
- [Przegląd Wiązanie danych](../../../desktop-wpf/data/data-binding-overview.md)
- [Układ](layout.md)
- [Przegląd Animacja](../graphics-multimedia/animation-overview.md)
