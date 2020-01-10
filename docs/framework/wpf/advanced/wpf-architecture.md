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
ms.openlocfilehash: 382facef15e79c4ce49fdedaeb1a072b7591e4a0
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740210"
---
# <a name="wpf-architecture"></a>Architektura WPF
Ten temat zawiera Przewodnik dotyczący hierarchii klas Windows Presentation Foundation (WPF). Obejmuje to większość głównych podsystemów WPF i opisuje sposób ich działania. Zawiera również szczegóły niektórych opcji wykonanych przez architektów WPF.  

<a name="System_Object"></a>   
## <a name="systemobject"></a>System.Object  
 Podstawowy model programowania WPF jest udostępniany za pomocą kodu zarządzanego. Wcześniej w fazie projektowania platformy WPF istniały wiele debat dotyczących miejsca, w którym należy narysować linię między zarządzanymi składnikami systemu i niezarządzanymi elementami. Środowisko CLR udostępnia wiele funkcji, które zwiększają produktywność i niezawodne programowanie (w tym zarządzanie pamięcią, obsługę błędów, wspólny system typów itp.), ale uzyskują koszt.  
  
 Główne składniki platformy WPF przedstawiono na poniższej ilustracji. Czerwona sekcja diagramu (platformie docelowej, 'Presentationcore i milcore) to główne fragmenty kodu WPF. Z nich tylko jeden jest składnikiem niezarządzanym — milcore. Milcore jest zapisywana w kodzie niezarządzanym w celu zapewnienia ścisłej integracji z DirectX. Wszystkie wyświetlacze w WPF odbywają się za pomocą aparatu DirectX, co umożliwia wydajne renderowanie sprzętu i oprogramowania. WPF wymaga również precyzyjnej kontroli nad pamięcią i wykonywaniem. Aparat kompozycji w milcore jest bardzo wrażliwy na wydajność i wymaga podania wielu zalet środowiska CLR w celu uzyskania wydajności.  
  
 ![Pozycja WPF w .NET Framework.](./media/wpf-architect1.PNG "wpf_architect1")  
  
 Komunikacja między częściami zarządzanymi i niezarządzanymi w programie WPF została omówiona dalej w tym temacie. Pozostała część zarządzanego modelu programowania została opisana poniżej.  
  
<a name="System_Threading_DispatcherObject"></a>   
## <a name="systemthreadingdispatcherobject"></a>System.Threading.DispatcherObject  
 Większość obiektów w WPF pochodzi od <xref:System.Windows.Threading.DispatcherObject>, który zapewnia podstawowe konstrukcje do obsługi współbieżności i wątkowości. WPF bazuje na systemie obsługi komunikatów zaimplementowanym przez dyspozytora. Działa to podobnie jak znana pompa komunikatów Win32; w rzeczywistości Dyspozytor WPF używa komunikatów User32 do wykonywania wywołań między wątkami.  
  
 Istnieją naprawdę dwa podstawowe koncepcje, które należy zrozumieć podczas omawiania współbieżności w WPF — dla dyspozytora i koligacji wątku.  
  
 W fazie projektowania platformy WPF celem było przechodzenie do pojedynczego wątku wykonywania, ale model "koligacja" bez wątku. Koligacja wątku występuje, gdy składnik używa tożsamości wykonywanego wątku do przechowywania pewnego typu stanu. Najbardziej powszechną formą jest użycie lokalnego magazynu wątków (TLS) do przechowywania stanu. Koligacja wątku wymaga, aby każdy logiczny wątek wykonywania należał do samego jednego wątku fizycznego w systemie operacyjnym, co może stać się intensywnym użyciem pamięci. Na końcu model wątkowości WPF został zsynchronizowany z istniejącym modelem wątkowości User32 z koligacją wątku. Główną przyczyną takiego działania była współdziałanie — systemy, takie jak OLE 2,0, schowek i Internet Explorer, wymagają wykonania pojedynczego wątku koligacji (STA).  
  
 Mając na względzie, że masz obiekty z wątkami STA, musisz mieć możliwość komunikacji między wątkami i sprawdzić, czy jesteś w prawidłowym wątku. W tym dokumencie leży rola dyspozytora. Dyspozytor to podstawowy system wysyłania komunikatów z wieloma kolejkami o określonym priorytetyzacji. Przykłady komunikatów to nieprzetworzone powiadomienia wejściowe (przenoszone przez mysz), funkcje platformy (układ) lub polecenia użytkownika (wykonaj tę metodę). Dzięki wykorzystaniu z <xref:System.Windows.Threading.DispatcherObject>należy utworzyć obiekt CLR, który ma zachowanie STA i będzie miał wskaźnik do dyspozytora podczas tworzenia.  
  
<a name="System_Windows_DependencyObject"></a>   
## <a name="systemwindowsdependencyobject"></a>System.Windows.DependencyObject  
 Jednym z podstawowych filozofiami architektury używanych podczas tworzenia WPF była Preferencja dla właściwości za pośrednictwem metod lub zdarzeń. Właściwości są deklaratywne i umożliwiają łatwiejsze Określanie zamiaru zamiast akcji. Jest to również obsługiwane przez model lub oparty na danych system do wyświetlania zawartości interfejsu użytkownika. Ta funkcja ma zamierzony efekt tworzenia większej liczby właściwości, które można powiązać z, aby lepiej kontrolować zachowanie aplikacji.  
  
 W celu uzyskania większej liczby systemów, które są oparte na właściwościach, jest to bogatszy system właściwości, który jest wymagany przez środowisko CLR. Prosty przykład tego rozbudowanego programu to powiadomienia o zmianach. Aby włączyć powiązanie dwukierunkowe, potrzebne są obie strony powiązania do obsługi powiadomień o zmianach. Aby można było mieć zachowanie związane z wartościami właściwości, należy otrzymywać powiadomienia o zmianie wartości właściwości. Struktura Microsoft .NET ma interfejs **INotifyPropertyChange**, który umożliwia obiektowi publikowanie powiadomień o zmianach, ale jest to opcjonalne.  
  
 WPF udostępnia bogatszy system właściwości, pochodzący od typu <xref:System.Windows.DependencyObject>. System właściwości jest naprawdę systemem właściwości "zależność" w tym, że śledzi zależności między wyrażeniami właściwości i automatycznie ponownie weryfikuje wartości właściwości, gdy zależności zmienią się. Na przykład jeśli masz właściwość, która dziedziczy (jak <xref:System.Windows.Controls.Control.FontSize%2A>), system jest automatycznie aktualizowany, jeśli właściwość zmieni się na element nadrzędny elementu, który dziedziczy wartość.  
  
 Podstawą systemu właściwości WPF jest koncepcja wyrażenia właściwości. W tej pierwszej wersji platformy WPF System wyrażeń właściwości jest zamknięty, a wyrażenia są dostarczane jako część struktury. Wyrażenia są powody, dla których system właściwości nie ma zakodowanego powiązania danych, stylu ani trwałego kodowania, ale jest udostępniany przez późniejsze warstwy w ramach struktury.  
  
 System właściwości zapewnia również rozrzedzony magazyn wartości właściwości. Ponieważ obiekty mogą mieć dziesiątki (jeśli nie setki) właściwości, a większość wartości jest w ich domyślnym stanie (dziedziczonym, ustawionym przez style itp.), a nie każde wystąpienie obiektu musi mieć pełną wagę każdej zdefiniowanej właściwości.  
  
 Ostatnia Nowa funkcja systemu właściwości jest pojęciem dołączonych właściwości. Elementy WPF są oparte na zasadzie tworzenia kompozycji i składników. Często zdarza się, że niektóre elementy zawierające (takie jak <xref:System.Windows.Controls.Grid> elementu układu) wymagają dodatkowych danych na elementach podrzędnych, aby kontrolować jego zachowanie (na przykład informacje o wierszu/kolumnie). Zamiast kojarzenia wszystkich tych właściwości z każdym elementem, każdy obiekt może zapewnić definicje właściwości dla dowolnego innego obiektu. Jest to podobne do funkcji "expand" języka JavaScript.  
  
<a name="System_Windows_Media_Visual"></a>   
## <a name="systemwindowsmediavisual"></a>System.Windows.Media.Visual  
 Po zdefiniowaniu systemu, następnym krokiem jest uzyskanie pikseli rysowanych na ekranie. Klasa <xref:System.Windows.Media.Visual> zapewnia Tworzenie drzewa obiektów wizualnych, z których każdy opcjonalnie zawiera instrukcje rysowania i metadane dotyczące sposobu renderowania tych instrukcji (przycinanie, przekształcanie itp.). <xref:System.Windows.Media.Visual> został zaprojektowany jako niezwykle lekki i elastyczny, dlatego większość funkcji nie ma publicznego narażenia na interfejs API i polega na użyciu funkcji wywołania zwrotnego.  
  
 <xref:System.Windows.Media.Visual> jest w rzeczywistości punktem wejścia do systemu kompozycji WPF. <xref:System.Windows.Media.Visual> jest punktem połączenia między tymi dwoma podsystemami, zarządzanym interfejsem API i niezarządzanym milcore.  
  
 WPF wyświetla dane, przechodząc do niezarządzanych struktur danych zarządzanych przez milcore. Struktury te, nazywane węzłami kompozycji, reprezentują hierarchiczne drzewo wyświetlania z instrukcjami renderowania w każdym węźle. To drzewo, zilustrowane po prawej stronie poniższego rysunku, jest dostępne tylko za pomocą protokołu obsługi komunikatów.  
  
 Podczas programowania WPF, tworzysz elementy <xref:System.Windows.Media.Visual> i typy pochodne, które wewnętrznie komunikują się z drzewem kompozycji za pomocą tego protokołu obsługi komunikatów. Każdy <xref:System.Windows.Media.Visual> w WPF może utworzyć jeden, brak lub kilka węzłów kompozycji.  
  
 ![Drzewo wizualne Windows Presentation Foundation.](./media/wpf-architecture2.PNG "wpf_architecture2")  
  
 Istnieje bardzo ważne szczegółowe informacje dotyczące architektury, które należy zauważyć — wszystkie drzewa wizualizacji i instrukcje rysowania są buforowane. W terminologii graficznej WPF używa zachowanego systemu renderowania. Dzięki temu system może być odświeżany o wysokim stopniu odświeżania bez blokowania systemu kompozycji na wywołania zwrotne do kodu użytkownika. Pozwala to uniknąć wyglądu nieodpowiadających aplikacji.  
  
 Inne ważne szczegóły, które nie są naprawdę zauważalne na diagramie, to sposób rzeczywistego wykonywania kompozycji przez system.  
  
 W systemach User32 i GDI system działa w trybie natychmiastowego przycinania. Gdy składnik musi być renderowany, system ustanawia granice przycinające poza tym, że składnik nie może dotykać pikseli, a następnie składnik jest proszony o malowanie pikseli w tym polu. Ten system działa bardzo dobrze w systemach z ograniczoną ilością pamięci, ponieważ w przypadku, gdy tylko zmiany muszą być dotknięciem składnika, którego dotyczy problem — żadne dwa składniki nigdy nie współtworzyją koloru jednego piksela.  
  
 WPF używa modelu rysowania "algorytmu malarza". Oznacza to, że zamiast przycinania każdego składnika każdy składnik jest proszony o renderowanie od tyłu do przodu ekranu. Pozwala to każdemu składnikowi na malowanie na ekranie poprzedniego składnika. Zaletą tego modelu jest to, że możesz mieć złożone, częściowo przezroczyste kształty. Dzięki współczesnemu, nowoczesnemu sprzętowi graficznemu model ten jest stosunkowo szybki (w przypadku utworzenia User32/GDI).  
  
 Jak wspomniano wcześniej, podstawową zasadą WPF jest przejście do bardziej deklaracyjnego modelu programowania "właściwości". W systemie wizualnym pokazuje to w kilku interesujących miejscach.  
  
 Najpierw Jeśli sądzisz o systemie grafiki trybu zachowanego, jest to naprawdę przenoszone z nieprawidłowego modelu typu DrawLine/DrawLine do modelu zorientowanego na dane — nowy wiersz ()/New liniowy (). To przechodzenie do renderowania opartego na danych umożliwia wykonywanie złożonych operacji na instrukcjach rysowania przy użyciu właściwości. Typy pochodne na podstawie <xref:System.Windows.Media.Drawing> są efektywnie modelem obiektów do renderowania.  
  
 W drugim przypadku w przypadku szacowania systemu animacji zobaczysz, że jest niemal całkowicie deklaratywny. Zamiast wymagać od programisty obliczenia następnej lokalizacji lub następnego koloru, można przedstawić animacje jako zestaw właściwości obiektu animacji. Te animacje mogą następnie wyrazić intencję dewelopera lub projektanta (Przenieś ten przycisk z tego miejsca do 5 sekund), a system może określić najbardziej wydajny sposób osiągnięcia tego działania.  
  
<a name="System_Windows_UIElement"></a>   
## <a name="systemwindowsuielement"></a>System.Windows.UIElement  
 <xref:System.Windows.UIElement> definiuje podstawowe podsystemy, w tym układ, dane wejściowe i zdarzenia.  
  
 Układ jest podstawową koncepcją w WPF. W wielu systemach jest dostępny stały zestaw modeli układu (HTML obsługuje trzy modele układu, przepływu, bezwzględnego i tabel) lub nie ma modelu układu (User32 naprawdę obsługuje pozycjonowanie bezwzględne). Funkcja WPF została zainicjowana z założeniem, że deweloperzy i projektanci chcieli mieć elastyczny, rozszerzalny model układu, który może być oparty na wartościach właściwości, a nie na podstawie logiki. Na poziomie <xref:System.Windows.UIElement> zostanie wprowadzony kontrakt podstawowy do układu — dwufazowy model z <xref:System.Windows.UIElement.Measure%2A> i <xref:System.Windows.UIElement.Arrange%2A> przebiegów.  
  
 <xref:System.Windows.UIElement.Measure%2A> umożliwia składnikowi określenie rozmiaru, który ma zostać uwzględniony. Jest to oddzielna faza od <xref:System.Windows.UIElement.Arrange%2A>, ponieważ istnieje wiele sytuacji, w których element nadrzędny będzie pytał kilka razy, aby określić optymalną pozycję i rozmiar. Fakt, że elementy nadrzędne zwracają elementy potomne do miary ilustruje kolejną jednokluczową metodę dla WPF — rozmiar do zawartości. Wszystkie kontrolki w WPF obsługują możliwość rozmiaru do naturalnego rozmiaru zawartości. Sprawia to, że lokalizacja jest znacznie łatwiejsza i umożliwia dynamiczne układ elementów w miarę zmieniania rozmiaru. Faza <xref:System.Windows.UIElement.Arrange%2A> pozwala elementom nadrzędnym na umieszczenie i określenie końcowego rozmiaru każdego elementu podrzędnego.  
  
 Dużo czasu często poświęcasz mówić na temat danych wyjściowych WPF — <xref:System.Windows.Media.Visual> i pokrewnych obiektów. Istnieje jednak ogromne ilości innowacji na stronie wejściowej. Prawdopodobnie najbardziej fundamentalną zmianą w modelu wejścia dla WPF jest spójny model, za pomocą którego zdarzenia wejściowe są kierowane przez system.  
  
 Dane wejściowe pochodzą ze sygnału w sterowniku urządzenia trybu jądra i są kierowane do poprawnego procesu i wątku za pomocą procesu Intricate obejmującego jądro systemu Windows i User32. Gdy komunikat User32 odpowiadający danemu wejściu jest kierowany do platformy WPF, jest konwertowany na nieprzetworzony komunikat wejściowy WPF i wysyłany do dyspozytora. WPF umożliwia konwertowanie nieprzetworzonych zdarzeń wejściowych na wiele rzeczywistych zdarzeń, co pozwala na zaimplementowanie funkcji takich jak "MouseEnter" na niskim poziomie systemu przy użyciu gwarantowanej dostawy.  
  
 Każde zdarzenie wejściowe jest konwertowane na co najmniej dwa zdarzenia — zdarzenie "wersja zapoznawcza" i rzeczywiste zdarzenie. Wszystkie zdarzenia w WPF mają koncepcję routingu za pomocą drzewa elementów. Zdarzenia są określane jako "bąbelki", jeśli przechodzą z elementu docelowego drzewa do katalogu głównego i są określane jako "Tunnel", jeśli zaczynają się w katalogu głównym i przechodzą do obiektu docelowego. Tunel zdarzeń wejściowych w wersji zapoznawczej, co umożliwia dowolnemu elementowi w drzewie możliwość filtrowania lub podejmowania akcji dla zdarzenia. Regularne zdarzenia (niewyświetlające wersji zapoznawczej) następnie bąbelki z elementu docelowego do katalogu głównego.  
  
 Ten podział między fazą tunelu i bąbelka sprawia, że implementacja funkcji, takich jak akceleratory klawiatury, działa w spójny sposób na świecie złożonym. W User32 należy zaimplementować akceleratory klawiatury, mając pojedynczą globalną tabelę zawierającą wszystkie akceleratory, które miały być obsługiwane (mapowanie CTRL + N na "nowe"). W dyspozytorze dla aplikacji należy wywołać **TranslateAccelerator** , co spowoduje wyciąganie komunikatów wejściowych w User32 i określenie, czy dowolny pasujący zarejestrowany akcelerator. W WPF to nie działa, ponieważ system jest w pełni "możliwe do redagowania" — każdy element może obsłużyć dowolny akcelerator klawiatury i korzystać z niego. Dwufazowy model dla danych wejściowych umożliwia składnikom implementowanie własnych "TranslateAccelerator".  
  
 Aby wykonać ten krok jeszcze bardziej, <xref:System.Windows.UIElement> wprowadza również pojęcie CommandBindings. System poleceń WPF pozwala deweloperom definiować funkcje w warunkach punktu końcowego polecenia — coś, który implementuje <xref:System.Windows.Input.ICommand>. Powiązania poleceń umożliwiają elementu Definiowanie mapowania między gestem wejściowym (CTRL + N) i poleceniem (New). Zarówno gesty wejściowe, jak i definicje poleceń są rozszerzalne i mogą być połączone ze sobą w czasie użytkowania. Dzięki temu można na przykład zezwolić użytkownikowi końcowemu na dostosowanie kluczowych powiązań, których chcą używać w aplikacji.  
  
 Do tego punktu w temacie "podstawowe" funkcje WPF — funkcje zaimplementowane w zestawie 'Presentationcore. Podczas kompilowania WPF, czyste rozdzielenie między częściami fundamentów (takie jak kontrakt do układu z **miarą** i **rozmieszczeniem**) oraz elementy struktury (takie jak implementacja określonego układu, takiego jak <xref:System.Windows.Controls.Grid>) było pożądanym wynikiem. Celem było zapewnienie niskich punktów rozszerzalności na stosie, które umożliwią deweloperom zewnętrznym tworzenie własnych platform w razie potrzeby.  
  
<a name="System_Windows_FrameworkElement"></a>   
## <a name="systemwindowsframeworkelement"></a>System.Windows.FrameworkElement  
 <xref:System.Windows.FrameworkElement> można wyszukiwać na dwa różne sposoby. Wprowadza zestaw zasad i dostosowań do podsystemów wprowadzonych w niższych warstwach WPF. Wprowadza również zestaw nowych podsystemów.  
  
 Podstawowe zasady wprowadzane przez <xref:System.Windows.FrameworkElement> to wokół układu aplikacji. <xref:System.Windows.FrameworkElement> kompiluje na podstawowym kontrakcie układu wprowadzonym przez <xref:System.Windows.UIElement> i dodaje pojęcie "gniazdo" układu, które ułatwia autorom układu spójny zestaw semantyki układu opartego na właściwościach. Właściwości, takie jak <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>, <xref:System.Windows.FrameworkElement.MinWidth%2A>i <xref:System.Windows.FrameworkElement.Margin%2A> (aby nazwać kilka), dają wszystkie składniki pochodzące z <xref:System.Windows.FrameworkElement> spójne zachowanie wewnątrz kontenerów układu.  
  
 <xref:System.Windows.FrameworkElement> zapewnia również łatwiejszy ekspozycja interfejsów API na wiele funkcji dostępnych w podstawowych warstwach WPF. Na przykład <xref:System.Windows.FrameworkElement> zapewnia bezpośredni dostęp do animacji za pośrednictwem metody <xref:System.Windows.FrameworkElement.BeginStoryboard%2A>. <xref:System.Windows.Media.Animation.Storyboard> zapewnia sposób skryptu wielu animacji względem zestawu właściwości.  
  
 Dwie najbardziej krytyczne elementy, które <xref:System.Windows.FrameworkElement> wprowadzają, to powiązanie danych i style.  
  
 Podsystem powiązań danych w platformie WPF powinien być relatywnie zaznajomiony z każdą osobą, która używa [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] lub ASP.NET do tworzenia [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]aplikacji. W każdym z tych systemów istnieje prosty sposób na określenie, że co najmniej jedna właściwość z danego elementu ma zostać powiązana z fragmentem danych. WPF ma pełną obsługę powiązań właściwości, transformacji i powiązania listy.  
  
 Jedną z najbardziej interesujących funkcji powiązań danych w WPF jest wprowadzenie szablonów danych. Szablony danych umożliwiają deklaratywne Określanie sposobu wizualizacji danych. Zamiast tworzyć niestandardowy interfejs użytkownika, który można powiązać z danymi, możesz zamiast tego zmienić ten problem i pozwolić, aby dane mogły zostać utworzone.  
  
 Style to w rzeczywistości uproszczona forma powiązań danych. Za pomocą stylów można powiązać zestaw właściwości z definicji udostępnionej z co najmniej jednym wystąpieniem elementu. Style są stosowane do elementu przez jawne odwołanie (przez ustawienie właściwości <xref:System.Windows.FrameworkElement.Style%2A>) lub niejawnie przez skojarzenie stylu z typem CLR elementu.  
  
<a name="System_Windows_Controls_Control"></a>   
## <a name="systemwindowscontrolscontrol"></a>System.Windows.Controls.Control  
 Najbardziej znacząca funkcja kontrolki to tworzenia szablonów. Jeśli myślisz o systemie kompozycji WPF jako systemu renderowania w trybie zachowanym, tworzenia szablonów umożliwia kontrolce opisywanie renderowania w sparametryzowanej, deklaratywnej sposób. W tym <xref:System.Windows.Controls.ControlTemplate> nie ma więcej więcej niż skrypt do utworzenia zestawu elementów podrzędnych z powiązaniami z właściwościami oferowanymi przez formant.  
  
 <xref:System.Windows.Controls.Control> zawiera zestaw właściwości podstawowych, <xref:System.Windows.Controls.Control.Foreground%2A>, <xref:System.Windows.Controls.Control.Background%2A><xref:System.Windows.Controls.Control.Padding%2A>, aby nazwać kilka, których autorów szablonów może użyć do dostosowania wyświetlania kontrolki. Implementacja kontrolki zawiera model danych i model interakcji. Model interakcji definiuje zestaw poleceń (takich jak zamknięcie okna) i powiązania z gestami wejściowymi (na przykład klikając czerwony symbol X w górnym rogu okna). Model danych zawiera zestaw właściwości, które umożliwiają dostosowanie modelu interakcji lub dostosowanie ekranu (określony przez szablon).  
  
 Ten podział między modelem danych (właściwościami), modelem interakcji (poleceniami i zdarzeniami) oraz modelem wyświetlania (szablony) umożliwia pełne dostosowanie wyglądu i zachowania kontrolki.  
  
 Typowym aspektem modelu danych formantów jest model zawartości. Jeśli zobaczysz kontrolkę taką jak <xref:System.Windows.Controls.Button>, zobaczysz, że ma ona właściwość o nazwie "Content" typu <xref:System.Object>. W [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] i ASP.NET ta właściwość zwykle jest ciągiem, ale ogranicza typ zawartości, którą można umieścić w przycisku. Zawartość przycisku może być prostym ciągiem, złożonym obiektem danych lub całym drzewem elementu. W przypadku obiektu danych szablon danych służy do konstruowania wyświetlania.  
  
<a name="Summary"></a>   
## <a name="summary"></a>Podsumowanie  
 Program WPF został zaprojektowany tak, aby umożliwić tworzenie dynamicznych, opartych na danych systemów prezentacji. Każda część systemu jest przeznaczona do tworzenia obiektów za pomocą zestawów właściwości, które mają zachowanie. Powiązanie danych jest podstawową częścią systemu i jest zintegrowane z każdą warstwą.  
  
 Tradycyjne aplikacje tworzą ekran, a następnie wiążą się z danymi. W WPF wszystkie elementy dotyczące formantu są generowane przez niektóre typy powiązań danych. Tekst znaleziony wewnątrz przycisku jest wyświetlany przez utworzenie kontrolki złożonej wewnątrz przycisku i powiązanie jego wyświetlania z właściwością zawartość przycisku.  
  
 Po rozpoczęciu opracowywania aplikacji opartych na platformie WPF powinny one być bardzo znane. Można ustawić właściwości, używać obiektów i powiązania danych w taki sam sposób, w jaki można używać [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] lub ASP.NET. Dzięki szczegółowej analizie architektury WPF można się dowiedzieć, że istnieje możliwość tworzenia znacznie rozbudowanych aplikacji, które zasadniczo traktują dane jako podstawowy sterownik aplikacji.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media.Visual>
- <xref:System.Windows.UIElement>
- <xref:System.Windows.Input.ICommand>
- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.Threading.DispatcherObject>
- <xref:System.Windows.Input.CommandBinding>
- <xref:System.Windows.Controls.Control>
- [Powiązanie danych — omówienie](../../../desktop-wpf/data/data-binding-overview.md)
- [Układ](layout.md)
- [Animacja — przegląd](../graphics-multimedia/animation-overview.md)
