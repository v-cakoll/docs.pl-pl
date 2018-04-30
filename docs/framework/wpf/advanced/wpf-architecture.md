---
title: Architektura WPF
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 29c8e2d632c37a299389b1bdc7f3f19f7df2f7e7
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="wpf-architecture"></a>Architektura WPF
Ten temat zawiera przewodnik hierarchii klas Windows Presentation Foundation (WPF). Obejmuje on większość głównych podsystemami [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]i opisano sposób ich interakcji. Szczegóły także niektóre wybory dokonane przez architektów z [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  
  
  
<a name="System_Object"></a>   
## <a name="systemobject"></a>System.Object  
 Podstawowy [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] model programowania jest uwidaczniany za pomocą kodu zarządzanego. Na początku fazy projektowania [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] wiele debatach o gdzie wiersz ma być rysowany między składnikami zarządzane systemu i niezarządzane te. [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] Oferuje następujące funkcje ułatwiające projektowanie i bardziej wydajna niezawodne (np. Zarządzanie pamięcią: obsługa błędów, wspólny system typów, itp.), ale zaczynają się to kosztem.  
  
 Głównych składników [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] przedstawiono na poniższej ilustracji. Czerwony sekcje diagramu (PresentationFramework PresentationCore i milcore) są fragmenty kodu głównych [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Niezarządzane składnika — milcore jest tylko jeden z nich. Milcore jest zapisywane w kodzie niezarządzanych w celu umożliwienia ścisłej integracji z [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)]. Wszystkie wyświetlenia w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] odbywa się za pośrednictwem [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] aparatu, co pozwala na efektywne sprzętu i oprogramowania renderowania. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] wymagane jest również szczegółową kontrolę pamięci i wykonywanie. Aparat kompozycji w milcore jest bardzo wydajności poufne i wymagane zwiększanie wiele zalet [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] uzyskanie wydajności.  
  
 ![Pozycja WPF w programie .NET Framework. ] (../../../../docs/framework/wpf/advanced/media/wpf-architect1.PNG "wpf_architect1")  
  
 Komunikacja między częściami zarządzane i niezarządzane [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] omówione w dalszej części tego tematu. Poniżej opisano w pozostałej części zarządzanego modelu programowania.  
  
<a name="System_Threading_DispatcherObject"></a>   
## <a name="systemthreadingdispatcherobject"></a>System.Threading.DispatcherObject  
 Większość obiektów w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] pochodzi od <xref:System.Windows.Threading.DispatcherObject>, co umożliwia podstawowe konstrukcje zajmujących się współbieżności i wątków. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] jest oparta na system obsługi wiadomości implementowane przez Dyspozytor. Działa to podobne jak w przypadku znanych [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] przekazywanie komunikatów; w rzeczywistości [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] dyspozytora używa komunikatów User32 umożliwiające wykonywanie wywołań między wątku.  
  
 Istnieją dwa naprawdę podstawowych pojęć Omawiając współbieżność w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] — koligacja dyspozytora i wątku.  
  
 W fazie projektowania [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], celem było przenieść do pojedynczego wątku wykonywania, ale nie wątku "skoligowanych" modelu. Koligacji wątku się stanie, jeśli składnik tożsamość wykonywania wątku będzie używana do przechowywania pewien typ stanu. Jest najczęściej używana forma na potrzeby przechowywania stanu lokalny magazyn wątków (TLS). Koligacji wątku wymaga, aby tylko jeden wątek fizycznych w systemie operacyjnym, który może stać się pamięci, być własnością w każdej logicznego wątku do wykonania. W końcu model wątkowości w WPF został zsynchronizowany z istniejący model wątkowy User32 pojedynczego jednowątkowego wykonywania koligacji wątku. — Głównej przyczyny to została współdziałania systemów, takich jak [!INCLUDE[TLA2#tla_ole2.0](../../../../includes/tla2sharptla-ole2-0-md.md)], Schowka i Internet Explorer wszystkie wymagają pojedynczego wątku wykonania koligacji (STA).  
  
 Biorąc pod uwagę, że masz obiekty o wątki STA, należy w sposób komunikacji między wątkami i zweryfikować znajdujące się na zorganizuj poprawny wątek. Poniżej znajduje się rola Dyspozytor. Dyspozytor jest podstawowe komunikat wysyłki systemu z wielu kolejek priorytetem. Komunikaty przykłady raw powiadomienia wejściowych (myszy przeniesiona), funkcje framework (układ) lub polecenia użytkownika (wykonać tę metodę). Przez pochodny <xref:System.Windows.Threading.DispatcherObject>, możesz utworzyć [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] obiekt, który zachowanie jest STA i będzie mógł skorzystać z wskaźnik do dyspozytora w czasie tworzenia.  
  
<a name="System_Windows_DependencyObject"></a>   
## <a name="systemwindowsdependencyobject"></a>System.Windows.DependencyObject  
 Jeden z podstawowej architektury filozofiami używane w budynku [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] został preferencji właściwości za pośrednictwem metody lub zdarzenia. Właściwości deklaratywne i zezwala na bardziej łatwo określić zamiar zamiast akcji. Obsługiwany również modelu zmiennych lub danych obsługiwanego systemu w celu wyświetlania zawartości interfejsu użytkownika. Tej zasady klas w efekcie zamierzone tworzenia więcej właściwości, które można powiązać, aby lepiej kontrolować zachowanie aplikacji.  
  
 Aby uzyskać więcej systemu regulowane przez właściwości, bardziej zaawansowane funkcje systemu właściwość niż co [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] zapewnia było wymagane. Prosty przykład tego siłę jest powiadomienia o zmianie. Aby włączyć dwie wiążących, należy obie strony powiązania obsługuje powiadomienie o zmianie. W celu zachowania związana z wartości właściwości, musisz otrzymać powiadomienie, gdy wartość właściwości. [!INCLUDE[TLA#tla_netframewk](../../../../includes/tlasharptla-netframewk-md.md)] Ma interfejs **INotifyPropertyChange**, obiekt, aby opublikować powiadomienia o zmianie, co pozwala jednak jest to pozycja opcjonalna.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zapewnia bardziej rozbudowane system właściwość pochodnych <xref:System.Windows.DependencyObject> typu. Właściwości systemu to naprawdę system właściwości "zależności", ponieważ śledzi zależności między wyrażeń właściwości i automatycznie revalidates wartości właściwości zależności zmiany. Na przykład, jeśli właściwość, która dziedziczy (takie jak <xref:System.Windows.Controls.Control.FontSize%2A>), system jest automatycznie aktualizowany, jeśli właściwość zmieni się na element nadrzędny elementu, który dziedziczy wartości.  
  
 Podstawę [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] system właściwości to pojęcie wyrażenia właściwości. W tej wersji pierwszy [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]systemu wyrażenie właściwości zostanie zamknięty i wyrażenia są dostarczane jako część platformy. Wyrażenia są dlaczego systemu właściwość nie ma powiązania danych, style, lub dziedziczenia twardych kodowanych, ale raczej udostępniane przez nowszy warstw w ramach.  
  
 Zawiera także właściwości systemu do magazynu rozrzedzonego w wartości właściwości. Ponieważ obiekty mogą mieć dziesiątki (Jeśli nie setki) właściwości, a większość wartości jest w stanie domyślne (dziedziczone, ustawione przez style, itp.), musi mieć pełną wagę dla każdej właściwości zdefiniowane w nim nie każde wystąpienie obiektu.  
  
 Końcowe nową funkcją systemu właściwość jest pojęcie dołączone właściwości. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] elementy są tworzone na zasadzie kompozycji i ponowne użycie składnika. Często jest to to niektóre zawierającego element (takich jak <xref:System.Windows.Controls.Grid> elementu układu) wymaga dodatkowych danych na elementy podrzędne kontrolowanie swojego zachowania (na przykład informacje o wierszy i kolumn). Zamiast kojarzenie wszystkie te właściwości z każdym elementem, dowolny obiekt może zapewnić definicji właściwości dla innego obiektu. Jest to podobne do funkcji "expando" języka JavaScript.  
  
<a name="System_Windows_Media_Visual"></a>   
## <a name="systemwindowsmediavisual"></a>System.Windows.Media.Visual  
 W systemie zdefiniowane następnym krokiem jest pobieranie pikseli na ekranie. <xref:System.Windows.Media.Visual> Udostępnia klasy do tworzenia drzewa obiektów visual każdy opcjonalnie zawiera instrukcje rysowania i metadane dotyczące sposób renderowania tych instrukcji (wycinka, przekształcania, itp.). <xref:System.Windows.Media.Visual> została zaprojektowana jako bardzo uproszczonego i elastyczna, dlatego większość funkcji nie ma żadnego elementu publicznego public [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] zagrożeń i silnie polegać na funkcje chronionych wywołania zwrotnego.  
  
 <xref:System.Windows.Media.Visual> to naprawdę punktu wejścia do [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] kompozycji systemu. <xref:System.Windows.Media.Visual> punkt połączenia między tych dwóch podsystemów zarządzanej [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] i milcore niezarządzane.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Wyświetla dane przez przeglądanie struktur niezarządzanych danych zarządzanych przez milcore. Tych struktur, nazywane węzłami kompozycji reprezentują drzewa hierarchiczną z instrukcjami renderowania w każdym węźle. Tego drzewa zilustrowane na po prawej stronie rysunku poniżej, jest dostępny tylko za pośrednictwem protokołu obsługi wiadomości.  
  
 Programowania [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], możesz utworzyć <xref:System.Windows.Media.Visual> elementów i typów pochodnych, które wewnętrznie komunikują się z drzewa kompozycji za pomocą tej obsługi wiadomości protokołu. Każdy <xref:System.Windows.Media.Visual> w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] może utworzyć jedną, none lub kilka węzłów kompozycji.  
  
 ![Windows Presentation Foundation drzewa wizualnego. ] (../../../../docs/framework/wpf/advanced/media/wpf-architecture2.PNG "wpf_architecture2")  
  
 Jest bardzo ważne szczegółów architektury Zauważ — całe drzewo elementów wizualnych i instrukcji rysowania są buforowane. W warunkach grafiki [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] korzysta z zachowanej renderowania systemu. Dzięki temu system do odświeżenia wysokich częstotliwości odświeżania bez kompozycji systemu blokowania na wywołania zwrotne do kodu użytkownika. Pomaga to zapobiec wyglądu aplikacji nie odpowiada.  
  
 Inny ważne szczegółów, które nie są naprawdę widoczne na diagramie jest jak system faktycznie wykonuje kompozycji.  
  
 W User32 i [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)], system działa w trybie natychmiastowym systemie wycinka. Gdy składnik musi być renderowane, system ustanawia granice wycinka, poza tym, które touch pikseli składnika nie może, a następnie składnika jest proszony o malowanie pikseli w tym polu. Ten system dobrze działa w systemach ograniczone przez ilość pamięci po każdej zmianie ma się touch składnik — nie dwa składniki kiedykolwiek współtworzyć kolor pojedynczego piksela.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] używa "algorytmu dla malarza" Malowanie modelu. Oznacza to, że zamiast wycinka każdego składnika, każdy składnik jest proszony o renderowania z tyłu na początku wyświetlania. Dzięki temu namalować za pośrednictwem poprzedni składnik wyświetlania każdego składnika. Zaletą tego modelu jest mają kształtów złożonych, częściowo przezroczysty. Ze sprzętem nowoczesnych grafiki współczesnych, ten model jest stosunkowo szybkie (który nie jest wielkość liter podczas User32 / [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] zostały utworzone).  
  
 Jak wspomniano wcześniej, podstawowych założeń [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] jest, aby przejść do bardziej deklaratywne "właściwość na" model programowania w języku. W programie visual system to zostaną wyświetlone w kilku miejscach interesujące.  
  
 Najpierw, jeśli sądzisz o systemie graficzne zachowanych tryb, to jest naprawdę przenoszenie imperatywnych modelu typu DrawLine/DrawLine, do modelu danych obiektowe — nowego wiersza () / nowy Line(). To przeniesienie do opartych na danych renderowania umożliwia złożone operacje na rysunku instrukcjami, aby można wyrazić przy użyciu właściwości. Typ pochodny <xref:System.Windows.Media.Drawing> są wydajnie model obiektów dla renderowania.  
  
 Po drugie Jeśli oceny systemu animacji, zostanie wyświetlone jest prawie całkowicie deklaratywne. Zamiast konieczności developer do obliczenia następnej lokalizacji lub kolor dalej, można wyrazić animacji jako zbiór właściwości obiektu animacji. Animacje te można następnie express celem dewelopera lub designer (przenieść ten przycisk, w tym miejscu tam w ciągu 5 sekund), a system może określić najbardziej efektywny sposób znajdują się.  
  
<a name="System_Windows_UIElement"></a>   
## <a name="systemwindowsuielement"></a>System.Windows.UIElement  
 <xref:System.Windows.UIElement> Definiuje podsystemów core w tym układ, dane wejściowe i zdarzeń.  
  
 Układ jest kluczową ideą w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. W wielu systemach jest ustalony zestaw modeli układu (HTML obsługuje trzy modele układu; przepływ absolute i tabele) lub bez modelu dla układu (User32 naprawdę tylko obsługuje pozycjonowanie bezwzględne). [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Rozpoczęto przy założeniu, że deweloperów i projektantów chciał modelu elastyczny i rozszerzalny układu można regulowane przez wartości właściwości, a nie imperatywnych logiki. W <xref:System.Windows.UIElement> poziomu podstawowego kontraktu dla układu wprowadzono — dwie fazy modelu z <xref:System.Windows.UIElement.Measure%2A> i <xref:System.Windows.UIElement.Arrange%2A> przekazuje.  
  
 <xref:System.Windows.UIElement.Measure%2A> Umożliwia składnik, aby określić, ile rozmiar chcesz wykonać. Jest to osobne fazy z <xref:System.Windows.UIElement.Arrange%2A> , ponieważ istnieje wiele sytuacji, gdy element nadrzędny poprosi podrzędnych do mierzenia kilka razy, aby ustalić jego optymalnej położenie i rozmiar. Fakt, że elementy nadrzędne poproś elementów podrzędnych do mierzenia pokazuje innego kluczowych założeń [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] — rozmiar do zawartości. Wszystkie formanty w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] obsługuje możliwość rozmiar do fizycznych rozmiar ich zawartości. To znacznie ułatwia lokalizacji i umożliwia dynamiczne układu elementów, jak rozmiar elementów. <xref:System.Windows.UIElement.Arrange%2A> Faza umożliwia nadrzędnej to pozycjonowania i określenia rozmiaru końcowego każdego elementu podrzędnego.  
  
 Mnóstwo czasu jest często poświęconego omówieniu z danych wyjściowych strony [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] — <xref:System.Windows.Media.Visual> i powiązane obiekty. Jednak jest bardzo dużą innowacji na strony wejściowej. Prawdopodobnie najbardziej podstawowych zmianę wejściowych modelu dla [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] jest spójny model, przez który zdarzenia wejściowe są wysyłane za pośrednictwem systemu.  
  
 Dane wejściowe pochodzi jako sterownik urządzenia trybu jądra na sygnał i kierowania korygowania procesu i wątku w procesie skomplikowanych obejmująca jądra systemu Windows i User32. Po komunikat User32 odpowiadający danych wejściowych jest kierowany do [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], jest konwertowany na [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] raw wejściowy wiadomości i wysłanych do dyspozytora. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Umożliwia nieprzetworzone zdarzenia wejściowe ma zostać przekonwertowane na wiele zdarzeń rzeczywiste, włączenie funkcji, takich jak "MouseEnter" wdrażane na niskim poziomie systemu o dostarczenie.  
  
 Każde zdarzenie wejściowych jest konwertowana na co najmniej dwóch zdarzeń — zdarzenie "w wersji zapoznawczej" i rzeczywistego zdarzenia. Wszystkie zdarzenia w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ma pojęcie routingu za pomocą elementu drzewa. Zdarzenia są określane jako "Bąbelkowy", jeśli przechodzenia z miejsca docelowego w górę drzewa do katalogu głównego i są określane jako "tunelowania", który uruchamiania w katalogu głównym i przechodzenia do elementu docelowego. Wprowadź Podgląd zdarzeń tunelu, włączanie dowolnego elementu w drzewie możliwość filtrowania lub wykonania akcji na zdarzenia. Regularne zdarzenia (z systemem innym niż wersja zapoznawcza) jest następnie bąbelkowy element docelowy do katalogu głównego.  
  
 Tego podziału między fazy tunelu i bąbelków sprawia, że implementacja funkcji, takich jak klawiaturowymi działać w spójny sposób w świecie złożonego. W User32 czy implementuje klawiaturowymi dzięki użyciu pojedynczego globalne tabelę zawierającą wszystkie akceleratorów, które mają zostać obsługuje (Ctrl + N mapowania "Nowy"). W dyspozytorze aplikacji należy wywołać **TranslateAccelerator** co czy wyśledzić komunikaty wejściowe w User32 i ustalić, jeśli pasuje żadnego zarejestrowanego akceleratora. W [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] to nie pomoże, ponieważ system jest w pełni "zezwala na składanie" — dowolny element obsługi i używać żadnych skrótów klawiaturowych. Ten model dwie fazy dla danych wejściowych o umożliwia składników do zaimplementowania własnych "TranslateAccelerator".  
  
 Podejmowanie jednym kroku, <xref:System.Windows.UIElement> również wprowadza pojęcia CommandBindings. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Polecenia systemu umożliwia deweloperom coś zdefiniuj funkcji pod względem punktu końcowego polecenia — tym implementuje <xref:System.Windows.Input.ICommand>. Polecenie powiązania włączyć element, aby określić mapowanie między gestu wejściowych (Ctrl + N) i polecenia (nowy). Zarówno gestów wejściowych, jak i definicji polecenia można rozszerzać i być połączone ze sobą w chwili użycia. Ułatwia to prosta, na przykład, aby umożliwić użytkownikom końcowym dostosowywanie powiązań klucza, które mają być użyte w aplikacji.  
  
 W tym punkcie w temacie "podstawowe" funkcje [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] — funkcji w zestawie PresentationCore zostały fokus. Podczas kompilowania [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], wyczyść separacji między podstawowym (kontrakt dla układu, takich jak **miary** i **Rozmieść**) i części framework (na przykład wykonania określonej Układ, takich jak <xref:System.Windows.Controls.Grid>) została żądanego wyniku. Celem było zapewnienie punkcie rozszerzenia niskiego na stosie, która umożliwiałaby zewnętrznych deweloperom tworzenie własnych struktur, jeśli jest wymagane.  
  
<a name="System_Windows_FrameworkElement"></a>   
## <a name="systemwindowsframeworkelement"></a>System.Windows.FrameworkElement  
 <xref:System.Windows.FrameworkElement> może być czyszczone na dwa różne sposoby. Podaj zestaw zasad i dostosowania dla podsystemów wprowadzone w niższych warstwach [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Podaj zestaw podsystemów nowe.  
  
 Podstawowe zasady wprowadzone przez <xref:System.Windows.FrameworkElement> jest wokół układ aplikacji. <xref:System.Windows.FrameworkElement> opiera się na kontrakt podstawowego układu wprowadzone przez <xref:System.Windows.UIElement> i dodaje pojęcie układu "miejsca", który ułatwia autorom układu ma spójny zestaw właściwości zmiennych semantyki układu. Właściwości, takie jak <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>, <xref:System.Windows.FrameworkElement.MinWidth%2A>, i <xref:System.Windows.FrameworkElement.Margin%2A> (o nazwanie kilka) zapewniają wszystkie składniki pochodną <xref:System.Windows.FrameworkElement> zachowanie spójności wewnątrz kontenery układów.  
  
 <xref:System.Windows.FrameworkElement> dostępne są także łatwiej [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] narażenia na wiele funkcji znaleziono w warstwie podstawowej [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Na przykład <xref:System.Windows.FrameworkElement> zapewnia bezpośredni dostęp do animacji <xref:System.Windows.FrameworkElement.BeginStoryboard%2A> metody. A <xref:System.Windows.Media.Animation.Storyboard> umożliwia wielu animacji względem zbioru właściwości skryptu.  
  
 Dwie najważniejsze czynności który <xref:System.Windows.FrameworkElement> wprowadza wiązania z danymi i style.  
  
 Podsystem powiązania danych w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] powinna być stosunkowo znana każdy użytkownik, który został użyty [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] lub [!INCLUDE[TLA#tla_aspnet](../../../../includes/tlasharptla-aspnet-md.md)] dotyczących tworzenia aplikacji [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. W każdym z tych systemów jest prosty sposób express, które mają co najmniej jednej właściwości z danego elementu może być powiązane z elementu danych. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zawiera pełną obsługę powiązania właściwości, przekształcania i powiązanie z listy.  
  
 Jedną z najbardziej interesujących funkcji wiązania z danymi w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] jest wprowadzenie danych szablonów. Szablony danych umożliwiają deklaratywnie Określ, jak można wywołać elementu danych. Zamiast tworzenia niestandardowego interfejsu użytkownika może być powiązana z danymi, możesz zamiast tego włączyć problem i umożliwić danych określić wyświetlania, która zostanie utworzona.  
  
 Style jest w rzeczywistości lekkie formę wiązania z danymi. Przy użyciu stylów, możesz można powiązać zestaw właściwości z definicji udostępnionego co najmniej jedno wystąpienie elementu. Zastosowane do elementu Style albo przez jawne odwołanie (przez ustawienie <xref:System.Windows.FrameworkElement.Style%2A> właściwości) lub niejawnie, kojarząc styl o [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] typ elementu.  
  
<a name="System_Windows_Controls_Control"></a>   
## <a name="systemwindowscontrolscontrol"></a>System.Windows.Controls.Control  
 Funkcja najważniejszych formantu jest tworzenia szablonów. Jeśli myślisz o WPF w skład systemu jako system zachowanych tryb renderowania, tworzenia szablonów umożliwia kontrolce opisano w sposób sparametryzowane, deklaratywne renderowania. A <xref:System.Windows.Controls.ControlTemplate> to naprawdę nic więcej niż skrypt, aby utworzyć zbiór podrzędnych elementów z powiązaniami do właściwości oferowane przez formant.  
  
 <xref:System.Windows.Controls.Control> zawiera zestaw właściwości standardowych <xref:System.Windows.Controls.Control.Foreground%2A>, <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Padding%2A>, kilka, które autorom następnie użyć, aby dostosować wyświetlanie formantu. Implementacja formant zawiera model danych i modelu interakcji. Model interakcji definiuje zestaw poleceń (np. Zamknij okno) i powiązania danych wejściowych gestów (np. Kliknięcie czerwonym symbolem X w górnym rogu okna). Model danych zapewnia zbiór właściwości, aby dostosować wyświetlanie (określoną w szablonie) albo dostosować modelu interakcji.  
  
 Tego podziału między modelu danych (właściwości), modelu interakcji (poleceń i zdarzeń) i wyświetlania modelu (szablonów) umożliwia procesu dostosowywania wyglądu i zachowania formantu.  
  
 Elementem wspólnego modelu danych formantów jest modelu zawartości. Jeśli przyjrzymy się formantu, takich jak <xref:System.Windows.Controls.Button>, zobaczysz, że ma właściwości o nazwie "Zawartość" typu <xref:System.Object>. W [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] i [!INCLUDE[TLA#tla_aspnet](../../../../includes/tlasharptla-aspnet-md.md)], ta właściwość będzie zazwyczaj ciąg — jednak typu zawartości, która ogranicza można umieścić w przycisku. Zawartości dla przycisku może być prosty ciąg, obiekt danych złożony lub drzewo całego elementu. W przypadku obiektu danych szablonu danych służy do tworzenia ekranu.  
  
<a name="Summary"></a>   
## <a name="summary"></a>Podsumowanie  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Służy do umożliwiają tworzenie dynamicznych, prezentacji systemów opartych na danych. Każdej części systemu jest przeznaczone do tworzenia obiektów za pomocą zestawów właściwości tego zachowania dysku. Powiązanie danych jest częścią podstawowych systemu i jest zintegrowana w każdej warstwie.  
  
 Tradycyjne aplikacje Tworzenie ekranu, a następnie powiązać z niektórych danych. W [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], wszystkie informacje o formancie, każdego aspektu działania ekranu, jest generowany przez pewien typ wiązania z danymi. Tekst wewnątrz przycisku jest wyświetlany przez tworzenie składa kontrolki wewnątrz przycisku i powiązania jej wyświetlania właściwości zawartości przycisku.  
  
 Kiedy rozpocząć tworzenie [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacje, należy możesz zapoznać się bardzo. Można ustawić właściwości, użyj obiektów i danych powiązania w taki sam sposób można za pomocą [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] lub [!INCLUDE[TLA#tla_aspnet](../../../../includes/tlasharptla-aspnet-md.md)]. Z głębsza analiza do architektury [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], można znaleźć istnienie możliwość tworzenia znacznie bardziej rozbudowane aplikacje, które zasadniczo traktować danych jako sterownik core aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.Visual>  
 <xref:System.Windows.UIElement>  
 <xref:System.Windows.Input.ICommand>  
 <xref:System.Windows.FrameworkElement>  
 <xref:System.Windows.Threading.DispatcherObject>  
 <xref:System.Windows.Input.CommandBinding>  
 <xref:System.Windows.Controls.Control>  
 [Powiązanie danych — omówienie](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Układ](../../../../docs/framework/wpf/advanced/layout.md)  
 [Animacja — przegląd](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
