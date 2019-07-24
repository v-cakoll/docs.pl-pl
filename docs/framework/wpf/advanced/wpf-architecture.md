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
ms.openlocfilehash: 987e48f163d35d27f6736464d7497451cca82c0c
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2019
ms.locfileid: "68400860"
---
# <a name="wpf-architecture"></a>Architektura WPF
Ten temat zawiera Przewodnik dotyczący hierarchii klas Windows Presentation Foundation (WPF). Obejmuje to większość głównych podsystemów [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]i opisuje sposób ich działania. Zawiera również szczegóły niektórych opcji dokonywanych przez architektów [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  

<a name="System_Object"></a>   
## <a name="systemobject"></a>System.Object  
 Podstawowy [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] model programowania jest udostępniany za pomocą kodu zarządzanego. Wcześniej w fazie [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] projektowania istniały wiele debat, w których linia powinna być narysowana między zarządzanymi składnikami systemu i niezarządzanymi. Środowisko CLR udostępnia wiele funkcji, które zwiększają produktywność i niezawodne programowanie (w tym zarządzanie pamięcią, obsługę błędów, wspólny system typów itp.), ale uzyskują koszt.  
  
 Główne składniki programu [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] przedstawiono na poniższej ilustracji. Czerwona sekcja diagramu (platformie docelowej, 'Presentationcore i milcore) to główne fragmenty [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]kodu. Z nich tylko jeden jest składnikiem niezarządzanym — milcore. Milcore jest zapisywana w kodzie niezarządzanym w celu zapewnienia ścisłej integracji z programem [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)]. Wszystkie wyświetlacze [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] w programie są wykonywane [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] przez aparat, co pozwala na wydajne renderowanie sprzętu i oprogramowania. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]wymaga to również precyzyjnej kontroli nad pamięcią i wykonywaniem. Aparat kompozycji w milcore jest bardzo wrażliwy na wydajność i wymaga podania wielu zalet środowiska CLR w celu uzyskania wydajności.  
  
 ![Pozycja WPF w .NET Framework.](./media/wpf-architect1.PNG "wpf_architect1")  
  
 Komunikacja między częściami [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zarządzanymi i niezarządzanymi została omówiona dalej w tym temacie. Pozostała część zarządzanego modelu programowania została opisana poniżej.  
  
<a name="System_Threading_DispatcherObject"></a>   
## <a name="systemthreadingdispatcherobject"></a>System.Threading.DispatcherObject  
 Większość obiektów [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] pochodzących z <xref:System.Windows.Threading.DispatcherObject>, która zapewnia podstawowe konstrukcje do obsługi współbieżności i wątkowości. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]jest oparta na systemie obsługi komunikatów zaimplementowanym przez dyspozytora. Działa to podobnie jak znana [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] pompa komunikatów; w rzeczywistości [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Dyspozytor używa komunikatów User32 do wykonywania wywołań między wątkami.  
  
 Istnieją naprawdę dwa podstawowe koncepcje, które należy zrozumieć podczas omawiania [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] współbieżności w programie — dla dyspozytora i koligacji wątku.  
  
 W fazie [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]projektowania, cel miał zostać przeniesiony do pojedynczego wątku wykonywania, ale model "koligacja" bez wątku. Koligacja wątku występuje, gdy składnik używa tożsamości wykonywanego wątku do przechowywania pewnego typu stanu. Najbardziej powszechną formą jest użycie lokalnego magazynu wątków (TLS) do przechowywania stanu. Koligacja wątku wymaga, aby każdy logiczny wątek wykonywania należał do samego jednego wątku fizycznego w systemie operacyjnym, co może stać się intensywnym użyciem pamięci. Na końcu model wątkowości WPF został zsynchronizowany z istniejącym modelem wątkowości User32 z koligacją wątku. Podstawową przyczyną jest współdziałanie — systemy takie jak [!INCLUDE[TLA2#tla_ole2.0](../../../../includes/tla2sharptla-ole2-0-md.md)], schowek i Internet Explorer wszystkie wymagają wykonywania koligacji pojedynczego wątku (STA).  
  
 Mając na względzie, że masz obiekty z wątkami STA, musisz mieć możliwość komunikacji między wątkami i sprawdzić, czy jesteś w prawidłowym wątku. W tym dokumencie leży rola dyspozytora. Dyspozytor to podstawowy system wysyłania komunikatów z wieloma kolejkami o określonym priorytetyzacji. Przykłady komunikatów to nieprzetworzone powiadomienia wejściowe (przenoszone przez mysz), funkcje platformy (układ) lub polecenia użytkownika (wykonaj tę metodę). Począwszy od <xref:System.Windows.Threading.DispatcherObject>, należy utworzyć obiekt CLR, który ma zachowanie sta i będzie miał wskaźnik do dyspozytora podczas tworzenia.  
  
<a name="System_Windows_DependencyObject"></a>   
## <a name="systemwindowsdependencyobject"></a>System.Windows.DependencyObject  
 Jeden z podstawowych filozofiami architektury użytych podczas tworzenia [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] był preferencją dla właściwości za pośrednictwem metod lub zdarzeń. Właściwości są deklaratywne i umożliwiają łatwiejsze Określanie zamiaru zamiast akcji. Jest to również obsługiwane przez model lub oparty na danych system do wyświetlania zawartości interfejsu użytkownika. Ta funkcja ma zamierzony efekt tworzenia większej liczby właściwości, które można powiązać z, aby lepiej kontrolować zachowanie aplikacji.  
  
 W celu uzyskania większej liczby systemów, które są oparte na właściwościach, jest to bogatszy system właściwości, który jest wymagany przez środowisko CLR. Prosty przykład tego rozbudowanego programu to powiadomienia o zmianach. Aby włączyć powiązanie dwukierunkowe, potrzebne są obie strony powiązania do obsługi powiadomień o zmianach. Aby można było mieć zachowanie związane z wartościami właściwości, należy otrzymywać powiadomienia o zmianie wartości właściwości. Struktura Microsoft .NET ma interfejs **INotifyPropertyChange**, który umożliwia obiektowi publikowanie powiadomień o zmianach, ale jest to opcjonalne.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]zapewnia bogatszy system właściwości pochodzący od <xref:System.Windows.DependencyObject> typu. System właściwości jest naprawdę systemem właściwości "zależność" w tym, że śledzi zależności między wyrażeniami właściwości i automatycznie ponownie weryfikuje wartości właściwości, gdy zależności zmienią się. Na przykład jeśli masz właściwość, która dziedziczy (jak <xref:System.Windows.Controls.Control.FontSize%2A>), system jest automatycznie aktualizowany, jeśli właściwość zmieni się na element nadrzędny elementu, który dziedziczy wartość.  
  
 Podstawą [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] systemu właściwości jest koncepcja wyrażenia właściwości. W tej pierwszej wersji [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]system wyrażeń właściwości jest zamknięty, a wszystkie wyrażenia są dostarczane jako część struktury. Wyrażenia są powody, dla których system właściwości nie ma zakodowanego powiązania danych, stylu ani trwałego kodowania, ale jest udostępniany przez późniejsze warstwy w ramach struktury.  
  
 System właściwości zapewnia również rozrzedzony magazyn wartości właściwości. Ponieważ obiekty mogą mieć dziesiątki (jeśli nie setki) właściwości, a większość wartości jest w ich domyślnym stanie (dziedziczonym, ustawionym przez style itp.), a nie każde wystąpienie obiektu musi mieć pełną wagę każdej zdefiniowanej właściwości.  
  
 Ostatnia Nowa funkcja systemu właściwości jest pojęciem dołączonych właściwości. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]elementy są zbudowane na zasadzie tworzenia kompozycji i składników. Często zdarza się, że niektóre elementy zawierające element (na <xref:System.Windows.Controls.Grid> przykład element Layout) wymagają dodatkowych danych na elementach podrzędnych, aby kontrolować jego zachowanie (na przykład informacje o wierszu/kolumnie). Zamiast kojarzenia wszystkich tych właściwości z każdym elementem, każdy obiekt może zapewnić definicje właściwości dla dowolnego innego obiektu. Jest to podobne do funkcji "expand" języka JavaScript.  
  
<a name="System_Windows_Media_Visual"></a>   
## <a name="systemwindowsmediavisual"></a>System.Windows.Media.Visual  
 Po zdefiniowaniu systemu, następnym krokiem jest uzyskanie pikseli rysowanych na ekranie. <xref:System.Windows.Media.Visual> Klasa umożliwia tworzenie drzewa obiektów wizualnych, z których każdy opcjonalnie zawiera instrukcje rysowania i metadane dotyczące sposobu renderowania tych instrukcji (wycinków, transformacji itp.). <xref:System.Windows.Media.Visual>została zaprojektowana tak, aby była niezwykle uproszczona i elastyczna, dlatego większość funkcji nie ma publicznego narażenia na interfejs API i nie opiera się na chronionych funkcjach wywołania zwrotnego.  
  
 <xref:System.Windows.Media.Visual>jest w rzeczywistości punktem wejścia do [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] systemu kompozycji. <xref:System.Windows.Media.Visual>jest punktem połączenia między tymi dwoma podsystemami, zarządzanym interfejsem API i niezarządzanym milcore.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]Wyświetla dane, przechodząc do niezarządzanych struktur danych zarządzanych przez milcore. Struktury te, nazywane węzłami kompozycji, reprezentują hierarchiczne drzewo wyświetlania z instrukcjami renderowania w każdym węźle. To drzewo, zilustrowane po prawej stronie poniższego rysunku, jest dostępne tylko za pomocą protokołu obsługi komunikatów.  
  
 Podczas programowania [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], <xref:System.Windows.Media.Visual> tworzysz elementy i typy pochodne, które wewnętrznie komunikują się z drzewem kompozycji za pomocą tego protokołu obsługi komunikatów. Każdy <xref:System.Windows.Media.Visual> z[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] nich może utworzyć jeden, brak lub kilka węzłów kompozycji.  
  
 ![Drzewo wizualne Windows Presentation Foundation.](./media/wpf-architecture2.PNG "wpf_architecture2")  
  
 Istnieje bardzo ważne szczegółowe informacje dotyczące architektury, które należy zauważyć — wszystkie drzewa wizualizacji i instrukcje rysowania są buforowane. W obszarze terminy grafiki [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] program używa zachowanego systemu renderowania. Dzięki temu system może być odświeżany o wysokim stopniu odświeżania bez blokowania systemu kompozycji na wywołania zwrotne do kodu użytkownika. Pozwala to uniknąć wyglądu nieodpowiadających aplikacji.  
  
 Inne ważne szczegóły, które nie są naprawdę zauważalne na diagramie, to sposób rzeczywistego wykonywania kompozycji przez system.  
  
 W User32 i [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)]system działa w trybie natychmiastowego przycinania. Gdy składnik musi być renderowany, system ustanawia granice przycinające poza tym, że składnik nie może dotykać pikseli, a następnie składnik jest proszony o malowanie pikseli w tym polu. Ten system działa bardzo dobrze w systemach z ograniczoną ilością pamięci, ponieważ w przypadku, gdy tylko zmiany muszą być dotknięciem składnika, którego dotyczy problem — żadne dwa składniki nigdy nie współtworzyją koloru jednego piksela.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]używa modelu rysowania "algorytmu malarza". Oznacza to, że zamiast przycinania każdego składnika każdy składnik jest proszony o renderowanie od tyłu do przodu ekranu. Pozwala to każdemu składnikowi na malowanie na ekranie poprzedniego składnika. Zaletą tego modelu jest to, że możesz mieć złożone, częściowo przezroczyste kształty. Dzięki współczesnemu, nowoczesnemu sprzętowi graficznemu model ten jest stosunkowo szybki (w przypadku gdy User32 [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] /zostały utworzone).  
  
 Jak wspomniano wcześniej, podstawową [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zasadą jest przejście do bardziej deklaracyjnego modelu programowania "właściwości". W systemie wizualnym pokazuje to w kilku interesujących miejscach.  
  
 Najpierw Jeśli sądzisz o systemie grafiki trybu zachowanego, jest to naprawdę przenoszone z nieprawidłowego modelu typu DrawLine/DrawLine do modelu zorientowanego na dane — nowy wiersz ()/New liniowy (). To przechodzenie do renderowania opartego na danych umożliwia wykonywanie złożonych operacji na instrukcjach rysowania przy użyciu właściwości. Typy pochodne od <xref:System.Windows.Media.Drawing> są efektywnie modelem obiektów do renderowania.  
  
 W drugim przypadku w przypadku szacowania systemu animacji zobaczysz, że jest niemal całkowicie deklaratywny. Zamiast wymagać od programisty obliczenia następnej lokalizacji lub następnego koloru, można przedstawić animacje jako zestaw właściwości obiektu animacji. Te animacje mogą następnie wyrazić intencję dewelopera lub projektanta (Przenieś ten przycisk z tego miejsca do 5 sekund), a system może określić najbardziej wydajny sposób osiągnięcia tego działania.  
  
<a name="System_Windows_UIElement"></a>   
## <a name="systemwindowsuielement"></a>System.Windows.UIElement  
 <xref:System.Windows.UIElement>Definiuje podstawowe podsystemy, w tym układ, dane wejściowe i zdarzenia.  
  
 Układ jest podstawową koncepcją w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. W wielu systemach jest dostępny stały zestaw modeli układu (HTML obsługuje trzy modele układu, przepływu, bezwzględnego i tabel) lub nie ma modelu układu (User32 naprawdę obsługuje pozycjonowanie bezwzględne). [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]rozpoczęto z założeniem, że deweloperzy i projektanci chcieli mieć elastyczny, rozszerzalny model układu, który może być sterowany przez wartości właściwości, a nie jako logikę bezwzględną. Na poziomie jest wprowadzany kontrakt podstawowy do układu — dwufazowy model z <xref:System.Windows.UIElement.Measure%2A> i <xref:System.Windows.UIElement.Arrange%2A> passs. <xref:System.Windows.UIElement>  
  
 <xref:System.Windows.UIElement.Measure%2A>umożliwia składnikowi określenie rozmiaru, który ma zostać uwzględniony. Jest to oddzielna faza <xref:System.Windows.UIElement.Arrange%2A> od, ponieważ istnieje wiele sytuacji, w których element nadrzędny będzie pytał kilka razy, aby określić optymalną pozycję i rozmiar. Fakt, że elementy nadrzędne zwracają elementy potomne do miary ilustruje inną istotną [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] informację o wielkości do zawartości. Wszystkie kontrolki [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] w programie obsługują możliwość rozmiaru do naturalnego rozmiaru zawartości. Sprawia to, że lokalizacja jest znacznie łatwiejsza i umożliwia dynamiczne układ elementów w miarę zmieniania rozmiaru. <xref:System.Windows.UIElement.Arrange%2A> Faza umożliwia nadrzędne położenie i określanie końcowego rozmiaru każdego elementu podrzędnego.  
  
 Dużo czasu często poświęcasz mówić na temat danych wyjściowych [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] — <xref:System.Windows.Media.Visual> i powiązanych z nimi obiektów. Istnieje jednak ogromne ilości innowacji na stronie wejściowej. Prawdopodobnie najbardziej fundamentalną zmianą w modelu [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] danych wejściowych jest spójny model, za pomocą którego zdarzenia wejściowe są kierowane przez system.  
  
 Dane wejściowe pochodzą ze sygnału w sterowniku urządzenia trybu jądra i są kierowane do poprawnego procesu i wątku za pomocą procesu Intricate obejmującego jądro systemu Windows i User32. Gdy komunikat User32 odpowiadający danemu wejściu jest kierowany [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]do, jest konwertowany [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] na nieprzetworzony komunikat wejściowy i wysyłany do dyspozytora. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]umożliwia konwertowanie nieprzetworzonych zdarzeń wejściowych na wiele rzeczywistych zdarzeń, co pozwala na zaimplementowanie funkcji takich jak "MouseEnter" na niskim poziomie systemu przy użyciu gwarantowanej dostawy.  
  
 Każde zdarzenie wejściowe jest konwertowane na co najmniej dwa zdarzenia — zdarzenie "wersja zapoznawcza" i rzeczywiste zdarzenie. Wszystkie zdarzenia w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] programie mają koncepcję routingu za pomocą drzewa elementów. Zdarzenia są określane jako "bąbelki", jeśli przechodzą z elementu docelowego drzewa do katalogu głównego i są określane jako "Tunnel", jeśli zaczynają się w katalogu głównym i przechodzą do obiektu docelowego. Tunel zdarzeń wejściowych w wersji zapoznawczej, co umożliwia dowolnemu elementowi w drzewie możliwość filtrowania lub podejmowania akcji dla zdarzenia. Regularne zdarzenia (niewyświetlające wersji zapoznawczej) następnie bąbelki z elementu docelowego do katalogu głównego.  
  
 Ten podział między fazą tunelu i bąbelka sprawia, że implementacja funkcji, takich jak akceleratory klawiatury, działa w spójny sposób na świecie złożonym. W User32 należy zaimplementować akceleratory klawiatury, mając pojedynczą globalną tabelę zawierającą wszystkie akceleratory, które miały być obsługiwane (mapowanie CTRL + N na "nowe"). W dyspozytorze dla aplikacji należy wywołać **TranslateAccelerator** , co spowoduje wyciąganie komunikatów wejściowych w User32 i określenie, czy dowolny pasujący zarejestrowany akcelerator. W [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] tym celu nie działa, ponieważ system jest w pełni "możliwe do redagowania" — każdy element może obsłużyć dowolny akcelerator klawiatury i korzystać z niego. Dwufazowy model dla danych wejściowych umożliwia składnikom implementowanie własnych "TranslateAccelerator".  
  
 Aby to zrobić, <xref:System.Windows.UIElement> należy również wprowadzić pojęcie CommandBindings. System poleceń umożliwia deweloperom Definiowanie funkcji w postaci punktu końcowego polecenia — elementu, który implementuje <xref:System.Windows.Input.ICommand>. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Powiązania poleceń umożliwiają elementu Definiowanie mapowania między gestem wejściowym (CTRL + N) i poleceniem (New). Zarówno gesty wejściowe, jak i definicje poleceń są rozszerzalne i mogą być połączone ze sobą w czasie użytkowania. Dzięki temu można na przykład zezwolić użytkownikowi końcowemu na dostosowanie kluczowych powiązań, których chcą używać w aplikacji.  
  
 Do tego punktu w temacie "podstawowe" funkcje [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] funkcji — funkcje zaimplementowane w zestawie 'presentationcore. Podczas [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]kompilowania, czyste rozdzielenie między częściami fundamentów (takie jak kontrakt do  układu z miarą i rozmieszczeniem) oraz elementy struktury (takie jak implementacja <xref:System.Windows.Controls.Grid>określonego układu, np.) było odpowiednie  wynikiem. Celem było zapewnienie niskich punktów rozszerzalności na stosie, które umożliwią deweloperom zewnętrznym tworzenie własnych platform w razie potrzeby.  
  
<a name="System_Windows_FrameworkElement"></a>   
## <a name="systemwindowsframeworkelement"></a>System.Windows.FrameworkElement  
 <xref:System.Windows.FrameworkElement>można je przejrzeć na dwa różne sposoby. Wprowadza zestaw zasad i dostosowań do podsystemów wprowadzonych w niższych warstwach [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Wprowadza również zestaw nowych podsystemów.  
  
 Zasady podstawowe wprowadzone przez <xref:System.Windows.FrameworkElement> program to wokół układu aplikacji. <xref:System.Windows.FrameworkElement>Program tworzy na podstawie kontraktu podstawowego układu wprowadzonego przez <xref:System.Windows.UIElement> i dodaje pojęcie "gniazdo" układu, które ułatwia autorom układu spójny zestaw semantyki układu opartego na właściwościach. <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>Właściwości <xref:System.Windows.FrameworkElement.Margin%2A> ,takie<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>jak,, i (w celu nazwy kilku), <xref:System.Windows.FrameworkElement> dająwszystkieskładnikipochodzącezespójnegozachowaniawewnątrzkontenerówukładu.<xref:System.Windows.FrameworkElement.MinWidth%2A>  
  
 <xref:System.Windows.FrameworkElement>zapewnia również łatwiejszy ekspozycja interfejsu API na wiele funkcji dostępnych w podstawowych warstwach [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Na przykład program <xref:System.Windows.FrameworkElement> zapewnia bezpośredni dostęp do animacji <xref:System.Windows.FrameworkElement.BeginStoryboard%2A> za pośrednictwem metody. A <xref:System.Windows.Media.Animation.Storyboard> umożliwia wykonywanie skryptów wielu animacji względem zestawu właściwości.  
  
 Poniżej przedstawiono dwie najważniejsze elementy, <xref:System.Windows.FrameworkElement> które wprowadzają dane i style.  
  
 Podsystem powiązań danych w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] systemie powinien być relatywnie zaznajomiony z każdą osobą, która była używana [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] lub ASP.NET [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]do tworzenia aplikacji. W każdym z tych systemów istnieje prosty sposób na określenie, że co najmniej jedna właściwość z danego elementu ma zostać powiązana z fragmentem danych. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]ma pełną obsługę powiązań właściwości, transformacji i powiązania listy.  
  
 Jedną z najbardziej interesujących funkcji wiązania danych w programie [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] jest wprowadzenie szablonów danych. Szablony danych umożliwiają deklaratywne Określanie sposobu wizualizacji danych. Zamiast tworzyć niestandardowy interfejs użytkownika, który można powiązać z danymi, możesz zamiast tego zmienić ten problem i pozwolić, aby dane mogły zostać utworzone.  
  
 Style to w rzeczywistości uproszczona forma powiązań danych. Za pomocą stylów można powiązać zestaw właściwości z definicji udostępnionej z co najmniej jednym wystąpieniem elementu. Style są stosowane do elementu przez jawne odwołanie (przez ustawienie <xref:System.Windows.FrameworkElement.Style%2A> właściwości) lub niejawnie przez skojarzenie stylu z typem CLR elementu.  
  
<a name="System_Windows_Controls_Control"></a>   
## <a name="systemwindowscontrolscontrol"></a>System.Windows.Controls.Control  
 Najbardziej znacząca funkcja kontrolki to tworzenia szablonów. Jeśli myślisz o systemie kompozycji WPF jako systemu renderowania w trybie zachowanym, tworzenia szablonów umożliwia kontrolce opisywanie renderowania w sparametryzowanej, deklaratywnej sposób. W <xref:System.Windows.Controls.ControlTemplate> rzeczywistości nie ma więcej niż skrypt do utworzenia zestawu elementów podrzędnych z powiązaniami z właściwościami oferowanymi przez formant.  
  
 <xref:System.Windows.Controls.Control>zawiera zestaw właściwości <xref:System.Windows.Controls.Control.Foreground%2A> <xref:System.Windows.Controls.Control.Background%2A>giełdowych,,,,, aby nazwać kilka, których autorów szablonów może użyć do dostosowania wyświetlania kontrolki. <xref:System.Windows.Controls.Control.Padding%2A> Implementacja kontrolki zawiera model danych i model interakcji. Model interakcji definiuje zestaw poleceń (takich jak zamknięcie okna) i powiązania z gestami wejściowymi (na przykład klikając czerwony symbol X w górnym rogu okna). Model danych zawiera zestaw właściwości, które umożliwiają dostosowanie modelu interakcji lub dostosowanie ekranu (określony przez szablon).  
  
 Ten podział między modelem danych (właściwościami), modelem interakcji (poleceniami i zdarzeniami) oraz modelem wyświetlania (szablony) umożliwia pełne dostosowanie wyglądu i zachowania kontrolki.  
  
 Typowym aspektem modelu danych formantów jest model zawartości. Jeśli przyjrzyjsz się kontrolce <xref:System.Windows.Controls.Button>do, zobaczysz, że ma ona właściwość o nazwie "Content" typu <xref:System.Object>. W [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] i ASP.NET ta właściwość zwykle jest ciągiem, ale ogranicza typ zawartości, którą można umieścić w przycisku. Zawartość przycisku może być prostym ciągiem, złożonym obiektem danych lub całym drzewem elementu. W przypadku obiektu danych szablon danych służy do konstruowania wyświetlania.  
  
<a name="Summary"></a>   
## <a name="summary"></a>Podsumowanie  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]Program został zaprojektowany tak, aby umożliwić tworzenie dynamicznych, opartych na danych systemów prezentacji. Każda część systemu jest przeznaczona do tworzenia obiektów za pomocą zestawów właściwości, które mają zachowanie. Powiązanie danych jest podstawową częścią systemu i jest zintegrowane z każdą warstwą.  
  
 Tradycyjne aplikacje tworzą ekran, a następnie wiążą się z danymi. W [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]programie wszystkie elementy dotyczące formantu są generowane przez niektóre typy powiązań danych. Tekst znaleziony wewnątrz przycisku jest wyświetlany przez utworzenie kontrolki złożonej wewnątrz przycisku i powiązanie jego wyświetlania z właściwością zawartość przycisku.  
  
 Po rozpoczęciu [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] tworzenia aplikacji opartych na programie powinno być bardzo znane. Można ustawić właściwości, używać obiektów i powiązania danych w taki sam sposób, w jaki można [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] używać lub ASP.NET. Dzięki szczegółowej analizie architektury programu [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]można stwierdzić, że istnieje możliwość tworzenia znacznie rozbudowanych aplikacji, które zasadniczo traktują dane jako podstawowy sterownik aplikacji.  
  
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
