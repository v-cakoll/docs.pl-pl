---
title: "Przegląd Wiązanie danych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data conversion for binding [WPF]
- binding data [WPF], about data binding
- data binding [WPF], about data binding
- conversion for data binding [WPF]
ms.assetid: c707c95f-7811-401d-956e-2fffd019a211
caps.latest.revision: "78"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fbf731504022cb25e0cdeff5e0a557b67b987fd4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="data-binding-overview"></a>Przegląd Wiązanie danych
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]Powiązanie danych zapewnia prosty i spójny sposób dla aplikacji przedstawić i interakcji z danymi. Elementy mogą być powiązane z danych z różnych źródeł danych w formie [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] obiektów i [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]. <xref:System.Windows.Controls.ContentControl>s, takich jak <xref:System.Windows.Controls.Button> i <xref:System.Windows.Controls.ItemsControl>s, takich jak <xref:System.Windows.Controls.ListBox> i <xref:System.Windows.Controls.ListView> ma wbudowanej funkcji, aby umożliwić elastyczne style elementów danych jednego lub kolekcje elementów danych. Sortowanie, filtrów i widoki grup można wygenerować na podstawie danych.  
  
 Funkcje powiązania danych w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ma kilka zalet w porównaniu do tradycyjnego modeli, łącznie z szeroką gamę właściwości, które z założenia obsługuje powiązanie danych, elastyczne [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] reprezentację danych i czyste rozdzielenie biznesowa logiki [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
 W tym temacie omówiono najpierw do podstawowych pojęć [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wiązania z danymi, a następnie przechodzi w użycie <xref:System.Windows.Data.Binding> klasy i innych funkcji, powiązania danych.  
  
  
<a name="what_is_data_binding"></a>   
## <a name="what-is-data-binding"></a>Co to jest wiązanie danych?  
 Powiązanie danych to proces, który nawiązuje połączenie między aplikacją [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] i logiki biznesowej. Jeśli powiązanie ma poprawne ustawienia i dane zawiera odpowiednie powiadomienia, następnie, po zmianie danych jego wartości elementów, które są powiązane z danymi odzwierciedlenia zmian automatycznie. Powiązanie danych można także oznaczać, że zmiana zewnętrznej reprezentacji danych w elemencie danych może automatycznie zaktualizowane w celu odzwierciedlenia zmian. Na przykład, jeśli użytkownik edytuje wartość <xref:System.Windows.Controls.TextBox> elementu, odpowiednia wartość danych zostanie automatycznie zaktualizowana w celu odzwierciedlenia tej zmiany.  
  
 Typowy sposób użycia powiązania danych jest umieszczenie serwera lub danych konfiguracji lokalnej w formularzach lub inne [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] kontrolki. W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], to pojęcie jest rozszerzona w celu uwzględnienia powiązania szeroka gama właściwości z różnych źródeł danych. W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], można powiązać właściwości zależności elementów [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] obiekty (w tym [!INCLUDE[TLA#tla_adonet](../../../../includes/tlasharptla-adonet-md.md)] obiektów lub obiekty skojarzone z właściwości sieci Web i usług sieci Web) i [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] danych.  
  
 Na przykład powiązanie danych Spójrz na następującej aplikacji [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] z [pokaz powiązania danych](http://go.microsoft.com/fwlink/?LinkID=163703):  
  
 ![Zrzut ekranu przedstawiający przykład powiązania danych](../../../../docs/framework/wpf/data/media/databinding-databindingdemo.png "DataBinding_DataBindingDemo")  
  
 Powyższe [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] aplikacji, która zostanie wyświetlona lista licytacją. Aplikacja przedstawiono następujące funkcje wiązania z danymi:  
  
-   Zawartość <xref:System.Windows.Controls.ListBox> jest powiązana z kolekcją *AuctionItem* obiektów. *AuctionItem* obiekt ma właściwości *opis*, *StartPrice*, *data_rozpoczęcia*, *kategorii*, *SpecialFeatures*itp.  
  
-   Dane (*AuctionItem* obiektów) wyświetlany w <xref:System.Windows.Controls.ListBox> jest szablonem, aby pokazać opis i bieżącej ceny dla każdego elementu. Jest to realizowane przy użyciu <xref:System.Windows.DataTemplate>. Ponadto wygląd każdego elementu zależy od *SpecialFeatures* wartość *AuctionItem* będzie wyświetlany. Jeśli *SpecialFeatures* wartość *AuctionItem* jest *kolor*, element ma obramowanie niebieski. Jeśli wartość jest *zaznacz*, element ma pomarańczowe krawędzie i gwiazdy. [Tworzenia szablonów danych](#data_templating) sekcja zawiera informacje dotyczące tworzenia szablonów danych.  
  
-   Użytkownika można grupować, filtrować i sortować danych przy użyciu <xref:System.Windows.Controls.CheckBox>es podane. W obrazie powyżej "Grupuj według kategorii" i "Sortowanie według kategorii i daty" <xref:System.Windows.Controls.CheckBox>es są wybrane. Można zauważyć, że dane są grupowane w oparciu o kategorię produktu i nazwa kategorii jest w porządku alfabetycznym. Trudno zauważyć z obrazu, ale elementy są również sortowane według daty rozpoczęcia w każdej kategorii. Jest to realizowane przy użyciu *widok kolekcji*. [Powiązanie z kolekcji](#binding_to_collections) sekcji omówiono widoki kolekcji.  
  
-   Po wybraniu elementu <xref:System.Windows.Controls.ContentControl> Wyświetla szczegóły wybranego elementu. Ta metoda jest wywoływana *scenariusza główny-szczegółowy*. [Scenariusza główny-szczegółowy](#master_detail_scenario) sekcja zawiera informacje o tym typie scenariusz wiązania.  
  
-   Typ *data_rozpoczęcia* jest właściwość <xref:System.DateTime>, która zwraca datę, która zawiera czas potrzebny do milisekund. W tej aplikacji niestandardowych konwertera został użyty, aby były wyświetlane krótszego ciągu daty. [Konwersja danych](#data_conversion) sekcja zawiera informacje o konwertery.  
  
 Po kliknięciu przez użytkownika *Dodaj produkt* przycisku funkcjonuje następującą postać:  
  
 ![Strona dodawania listy produktów](../../../../docs/framework/wpf/data/media/databinding-demo-addproductlisting.png "DataBinding_Demo_AddProductListing")  
  
 Użytkownik może edytować pola w formularzu, podglądu listę produktu przy użyciu krótkich Podgląd i bardziej szczegółowe okienka podglądu, a następnie kliknij *przesłać* Aby dodać nową ofertę produktu. Wszelkie istniejące grupowania filtrowanie i sortowanie funkcje będą stosowane do nowego wpisu. W tym przypadku element wprowadzony na powyższej ilustracji będzie wyświetlany jako drugiego elementu w obrębie *komputera* kategorii.  
  
 Nie pokazano tego obrazu jest logikę weryfikacji w *Data rozpoczęcia* <xref:System.Windows.Controls.TextBox>. Jeśli użytkownik wprowadzi nieprawidłowe Data (nieprawidłowe formatowanie lub datą przeszłą), użytkownik zostanie powiadomiony o <xref:System.Windows.Controls.ToolTip> i czerwonego wykrzyknika dalej, aby <xref:System.Windows.Controls.TextBox>. [Sprawdzanie poprawności danych](#data_validation) sekcji omówiono sposób tworzenia logiki sprawdzania poprawności.  
  
 Przed przejściem do różnych funkcji wiązania danych opisanych powyżej, najpierw omówimy w następnej sekcji podstawowe pojęcia, które są krytyczne dla zrozumienia [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wiązania z danymi.  
  
## <a name="basic-data-binding-concepts"></a>Pojęcia dotyczące powiązania danych podstawowych  
  
 Niezależnie od tego, jaki element powiązania i rodzaj źródła danych, zawsze każdego powiązania jest zgodna z modelem pokazano na poniższej ilustracji:  
  
 ![Diagram podstawowego powiązania danych](../../../../docs/framework/wpf/data/media/databindingmostbasic.png "DataBindingMostBasic")  
  
 Jak pokazano na rysunku powyżej, powiązanie danych jest zasadniczo mostka między urządzenie docelowe powiązania i źródła powiązania. Na rysunku pokazano następujące podstawowe [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pojęcia dotyczące powiązania danych:  
  
-   Zazwyczaj każdego powiązania ma następujące cztery składniki: powiązania obiektu docelowego, właściwość target źródle powiązania i ścieżkę do wartości w źródle powiązania do użycia. Na przykład, jeśli chcesz powiązać zawartość <xref:System.Windows.Controls.TextBox> do *nazwa* właściwość *pracownika* obiektu, obiekt docelowy jest <xref:System.Windows.Controls.TextBox>, właściwość docelowa jest <xref:System.Windows.Controls.TextBox.Text%2A> Właściwość, wartość jest *nazwa*, a obiekt źródłowy *pracownika* obiektu.  
  
-   Właściwość target musi być właściwością zależności. Większość <xref:System.Windows.UIElement> właściwości są właściwości zależności i większość właściwości zależności, z wyjątkiem sieci tylko do odczytu, obsługuje powiązanie danych domyślnie. (Tylko <xref:System.Windows.DependencyObject> typów można zdefiniować właściwości zależności i wszystkie <xref:System.Windows.UIElement>s pochodzi od <xref:System.Windows.DependencyObject>.)  
  
-   Mimo że nie jest określona na ilustracji, należy zauważyć, że powiązania obiektu źródłowego nie jest ograniczona do niestandardowego jest [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] obiektu. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Powiązanie danych obsługuje dane w postaci [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] obiektów i [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]. Aby podać kilka przykładów, może być źródle powiązania <xref:System.Windows.UIElement>, dowolnego obiektu listy [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] obiektu, z którym skojarzony jest [!INCLUDE[TLA#tla_adonet](../../../../includes/tlasharptla-adonet-md.md)] danych lub usługi sieci Web lub element XmlNode, który zawiera z [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] danych. Aby uzyskać więcej informacji, zobacz [powiązanie Przegląd źródeł](../../../../docs/framework/wpf/data/binding-sources-overview.md).  
  
 Omówione w innych [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)] tematy, ważne jest, aby należy pamiętać, że podczas ustanawiania powiązania są powiązanie cel wiązania *do* źródle powiązania. Na przykład w przypadku wyświetlania niektórych podstawowych [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] danych w <xref:System.Windows.Controls.ListBox> używanie powiązania danych, której dokonywane jest wiązanie z <xref:System.Windows.Controls.ListBox> do [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] danych.  
  
 Aby ustanowić powiązanie, należy użyć <xref:System.Windows.Data.Binding> obiektu. Pozostała część tego tematu opisano wiele pojęć związanych z oraz niektórych właściwości i użycie <xref:System.Windows.Data.Binding> obiektu.  
  
<a name="direction_of_data_flow"></a>   
### <a name="direction-of-the-data-flow"></a>Kierunek przepływu danych  
 Jak wspomniano wcześniej, a wskazany strzałką na powyższej ilustracji, przepływ danych powiązania może przejść od cel wiązania ze źródłem powiązanie (na przykład wartość źródłowa zostanie zmieniona, gdy użytkownik edytuje wartość <xref:System.Windows.Controls.TextBox>) i/lub w źródle powiązania do obiektu docelowego powiązanie (na przykład z <xref:System.Windows.Controls.TextBox> zawartości jest aktualizowana ze zmianami w źródle powiązania) Jeśli Wyświetla właściwego powiadomienia w źródle powiązania.  
  
 Możesz aplikacji w taki sposób, aby użytkownicy mogli zmieniać dane i obejmie go z obiektem źródłowym. Lub może nie chcesz zezwolić użytkownikom na aktualizowanie źródła danych. Można to kontrolowane przez ustawienie <xref:System.Windows.Data.Binding.Mode%2A> właściwości użytkownika <xref:System.Windows.Data.Binding> obiektu. Na poniższym rysunku przedstawiono różne typy przepływu danych:  
  
 ![Powiązanie danych przepływu danych](../../../../docs/framework/wpf/data/media/databinding-dataflow.png "DataBinding_DataFlow")  
  
-   <xref:System.Windows.Data.BindingMode.OneWay>Powiązanie powoduje, że zmiany właściwości źródła można automatycznie zaktualizować właściwość target, ale zmiany do właściwości target nie są propagowane do właściwości source. Ten typ powiązania jest odpowiednie, jeśli formant jest powiązany jest niejawnie tylko do odczytu. Na przykład może powiązać ze źródłem, takich jak giełdowych lub prawdopodobnie Twoje właściwość target nie ma kontroli interfejsu przewidzianych wprowadzania zmian, takich jak kolory tła powiązane z danymi w tabeli. Nie jest konieczne do monitorowania zmian właściwości target, za pomocą <xref:System.Windows.Data.BindingMode.OneWay> tryb wiązania pozwala uniknąć ponoszenia dodatkowych nakładów na <xref:System.Windows.Data.BindingMode.TwoWay> tryb wiązania.  
  
-   <xref:System.Windows.Data.BindingMode.TwoWay>Powiązanie powoduje, że zmiany właściwości source lub właściwość target można automatycznie zaktualizować innych. Ten typ powiązania jest odpowiedni dla formularzy można edytować lub innych pełni nieinterakcyjnego [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] scenariuszy. Domyślnie większość właściwości <xref:System.Windows.Data.BindingMode.OneWay> powiązania, ale niektóre właściwości zależności (zazwyczaj właściwości można edytować użytkownika formantów, takich jak <xref:System.Windows.Controls.TextBox.Text%2A> właściwość <xref:System.Windows.Controls.TextBox> i <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> właściwość <xref:System.Windows.Controls.CheckBox>) domyślnie <xref:System.Windows.Data.BindingMode.TwoWay> powiązania. Programowy sposób określenia, czy właściwość zależności wiąże- lub dwukierunkowo domyślnie jest można pobrać metadanych właściwości modelu przy użyciu właściwości <xref:System.Windows.DependencyProperty.GetMetadata%2A> , a następnie sprawdź wartość logiczna <xref:System.Windows.FrameworkPropertyMetadata.BindsTwoWayByDefault%2A> właściwości.  
  
-   <xref:System.Windows.Data.BindingMode.OneWayToSource>jest odwrotnej <xref:System.Windows.Data.BindingMode.OneWay> wiązanie; aktualizuje właściwości source po zmianie właściwości target. Przykładowy scenariusz jest Jeśli należy ponownej oceny wartości źródłowej z [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
-   Nie zostało to przedstawione na rysunku jest <xref:System.Windows.Data.BindingMode.OneTime> powiązanie, co powoduje, że właściwość source zainicjować właściwość target, ale nie propagację kolejne zmiany. Oznacza to, że jeśli kontekst danych ulega zmianie lub obiekt w zmiany kontekstu danych, następnie zmiany nie zostaną uwzględnione w właściwość target. Ten typ powiązania jest odpowiednie, jeśli używasz danych gdzie albo migawka bieżącego stanu jest odpowiednie do użycia lub dane są naprawdę statycznych. Ten typ powiązania jest również przydatne, jeśli chcesz zainicjować z właściwości target o niektórych wartości z właściwości source i kontekstu danych nie jest znany wcześniej. To zasadniczo prostsze formularza <xref:System.Windows.Data.BindingMode.OneWay> powiązania, który zapewnia lepszą wydajność w przypadku, gdy nie zmienia wartość źródła.  
  
 Należy pamiętać, że aby wykryć zmiany źródła (dotyczy <xref:System.Windows.Data.BindingMode.OneWay> i <xref:System.Windows.Data.BindingMode.TwoWay> powiązań), źródło musi implementować mechanizm powiadamiania Zmień odpowiednie właściwości takich jak <xref:System.ComponentModel.INotifyPropertyChanged>. Zobacz [powiadomienia o zmianie właściwości wdrożenie](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md) przykład <xref:System.ComponentModel.INotifyPropertyChanged> implementacji.  
  
 <xref:System.Windows.Data.Binding.Mode%2A> Strony właściwości zawiera więcej informacji na temat wiązania tryby i przykładem określić kierunek powiązania.  
  
<a name="what_triggers_source_updates"></a>   
### <a name="what-triggers-source-updates"></a>Wyzwalacze źródła aktualizacji  
 Powiązania, które są <xref:System.Windows.Data.BindingMode.TwoWay> lub <xref:System.Windows.Data.BindingMode.OneWayToSource> nasłuchiwania zmian we właściwości docelowej i obejmie ich źródła. Jest to nazywane aktualizowanie źródła. Na przykład można edytować tekst pola tekstowego, aby zmienić podstawową wartość źródła. Zgodnie z opisem w ostatniej sekcji, kierunek przepływu danych jest określana przez wartość <xref:System.Windows.Data.Binding.Mode%2A> właściwości powiązania.  
  
 Jednak wartość źródła aktualizowany podczas edytowania tekstu lub po Zakończ edycję tekstu i wskaż przy użyciu myszy poza pole tekstowe? <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> Właściwość powiązania Określa, jakie wyzwala aktualizacji źródła. Kropki prawo strzałek na poniższej ilustracji ilustrują roli <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> właściwości:  
  
 ![UpdateSourceTrigger diagram](../../../../docs/framework/wpf/data/media/databindingupdatesourcetrigger.png "DataBindingUpdateSourceTrigger")  
  
 Jeśli <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> wartość jest <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>, następnie wartość wskazywana przez strzałkę w prawo <xref:System.Windows.Data.BindingMode.TwoWay> lub <xref:System.Windows.Data.BindingMode.OneWayToSource> powiązania jest aktualizowana tak szybko, jak zmiany właściwości docelowej. Jednak jeśli <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> wartość jest <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>, a następnie tę wartość tylko zostanie zaktualizowany przy użyciu nowej wartości, gdy właściwość target utraci fokus.  
  
 Podobnie jak <xref:System.Windows.Data.Binding.Mode%2A> właściwości zależności różnych właściwości mają różne domyślne <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> wartości. Wartość domyślna dla większości właściwości zależności to <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>, podczas gdy <xref:System.Windows.Controls.TextBox.Text%2A> właściwość ma wartość domyślną równą <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>. Oznacza to, że aktualizacji źródła zazwyczaj się zdarzyć, gdy zmiany właściwości docelowych, które jest poprawne dla <xref:System.Windows.Controls.CheckBox>es i innych kontrolek proste. Jednak dla pól tekstowych aktualizacji po każdym naciśnięciu klawisza może obniżyć wydajność i wyklucza zwykle możliwość backspace i napraw błędy przed zatwierdzeniem do nowej wartości. Dlatego <xref:System.Windows.Controls.TextBox.Text%2A> właściwość ma wartość domyślną równą <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus> zamiast <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.  
  
 Zobacz <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> stronę właściwości informacji o sposobach znajdowania domyślnie <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> wartość właściwości zależności.  
  
 W poniższej tabeli przedstawiono przykładowy scenariusz dla każdego <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> wartości przy użyciu <xref:System.Windows.Controls.TextBox> na przykład:  
  
|Wartość UpdateSourceTrigger|Gdy zaktualizowano pobiera wartość źródła|Przykładowy scenariusz dla pola tekstowego|  
|-------------------------------|----------------------------------------|----------------------------------|  
|LostFocus (domyślne dla <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType>)|Gdy TextBox — formant utraci fokus|A <xref:System.Windows.Controls.TextBox> skojarzonego z logiki sprawdzania poprawności (patrz sekcja sprawdzanie poprawności danych)|  
|PropertyChanged|Podczas pisania w<xref:System.Windows.Controls.TextBox>|<xref:System.Windows.Controls.TextBox>kontrolki w oknie pokoju rozmów|  
|Jawne|Gdy aplikacja wywołuje<xref:System.Windows.Data.BindingExpression.UpdateSource%2A>|<xref:System.Windows.Controls.TextBox>formantów w formularzu można edytować (aktualizacje wartości źródła tylko wtedy, gdy użytkownik kliknie przycisk przesyłania)|  
  
 Na przykład zobacz [kontroli, gdy tekst pola tekstowego aktualizuje źródła](../../../../docs/framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md).  
  
<a name="creating_a_binding"></a>   
## <a name="creating-a-binding"></a>Tworzenie powiązania  
  
 Do recapitulate niektóre kwestie omówione w poprzednich sekcjach, możesz udostępnić za pomocą powiązania <xref:System.Windows.Data.Binding> obiekt i każdego powiązania zwykle zawiera cztery składniki: powiązanie docelowej, właściwość target źródle powiązania i ścieżki z wartość źródła do użycia. W tej sekcji omówiono sposób skonfigurować powiązanie.  
  
 Rozważmy następujący przykład, w którym obiekt źródłowy powiązania jest klasa o nazwie *Moje_Dane* zdefiniowanego w *SDKSample* przestrzeni nazw. Dla celów demonstracyjnych *Moje_Dane* klasa ma właściwości ciągu o nazwie *ColorName*, z którego wartość jest równa "Red". W związku z tym w tym przykładzie generuje przycisk czerwonym tle.  
  
 [!code-xaml[BindNonTextProperty#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindNonTextProperty/CS/Page1.xaml#1)]  
  
 Aby uzyskać więcej informacji o składni deklaracji powiązania oraz przykłady sposobu konfigurowania powiązania w kodzie, zobacz [— wiązanie deklaracje omówienie](../../../../docs/framework/wpf/data/binding-declarations-overview.md).  
  
 Jeśli Trwa stosowanie w tym przykładzie do naszej diagram podstawowy, wynikowy rysunek wygląda następująco. Jest to <xref:System.Windows.Data.BindingMode.OneWay> powiązania, ponieważ właściwość tła obsługuje <xref:System.Windows.Data.BindingMode.OneWay> powiązanie domyślnie.  
  
 ![Diagram powiązania danych](../../../../docs/framework/wpf/data/media/databindingbuttonbackgroundexample.png "DataBindingButtonBackgroundExample")  
  
 Może zastanawiasz się, dlaczego dzieje się tak nawet jeśli *ColorName* właściwość jest typu String podczas <xref:System.Windows.Controls.Control.Background%2A> właściwość jest typu <xref:System.Windows.Media.Brush>. To jest domyślny typ konwersji w miejscu pracy co opisano [Konwersja danych](#data_conversion) sekcji.  
  
<a name="specifying_the_binding_source"></a>   
### <a name="specifying-the-binding-source"></a>Określanie powiązania źródła  
 Zwróć uwagę, że w poprzednim przykładzie źródle powiązania jest określany przez ustawienie <xref:System.Windows.FrameworkElement.DataContext%2A> właściwość <xref:System.Windows.Controls.DockPanel> elementu. <xref:System.Windows.Controls.Button> Następnie dziedziczy <xref:System.Windows.FrameworkElement.DataContext%2A> wartość z <xref:System.Windows.Controls.DockPanel>, który jest elementem nadrzędnym elementu. Można powtórzyć, obiekt źródłowy powiązania jest jednym z czterech niezbędne składniki powiązania. W związku z tym nie jest określony obiekt źródłowy powiązanie powiązanie będzie nic nie rób.  
  
 Istnieje kilka sposobów, aby określić powiązanie obiektu źródłowego. Przy użyciu <xref:System.Windows.FrameworkElement.DataContext%2A> właściwości elementu nadrzędnego jest przydatne, gdy wiele właściwości są powiązanie z tego samego źródła. Jednak czasami może być bardziej odpowiednie określić źródło powiązania w deklaracjach poszczególnych powiązania. W poprzednim przykładzie, zamiast <xref:System.Windows.FrameworkElement.DataContext%2A> właściwości, można określić źródło powiązania, ustawiając <xref:System.Windows.Data.Binding.Source%2A> właściwości bezpośrednio w deklaracji powiązanie przycisku, jak w poniższym przykładzie:  
  
 [!code-xaml[BindNonTextProperty#BackgroundBindingCompact](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindNonTextProperty/CS/Page2.xaml#backgroundbindingcompact)]  
  
 Inne niż ustawienie <xref:System.Windows.FrameworkElement.DataContext%2A> właściwości w elemencie bezpośrednio, dziedziczenie <xref:System.Windows.FrameworkElement.DataContext%2A> wartości z elementu nadrzędnego (na przykład przycisk w pierwszym przykładzie) i jawne określenie przez ustawienie źródło powiązania <xref:System.Windows.Data.Binding.Source%2A> właściwość <xref:System.Windows.Data.Binding> (na przykład przycisk ostatnim przykładzie), można również użyć <xref:System.Windows.Data.Binding.ElementName%2A> właściwości lub <xref:System.Windows.Data.Binding.RelativeSource%2A> właściwości w celu określenia powiązania źródła. <xref:System.Windows.Data.Binding.ElementName%2A> Właściwość jest przydatna podczas tworzenia wiązania z innymi elementami w aplikacji, takich jak w przypadku korzystania suwaka Szerokość przycisku. <xref:System.Windows.Data.Binding.RelativeSource%2A> Właściwość jest przydatna, gdy określono powiązanie w <xref:System.Windows.Controls.ControlTemplate> lub <xref:System.Windows.Style>. Aby uzyskać więcej informacji, zobacz [określone źródło powiązania](../../../../docs/framework/wpf/data/how-to-specify-the-binding-source.md).  
  
<a name="specifying_the_path_to_the_value"></a>   
### <a name="specifying-the-path-to-the-value"></a>Określanie ścieżki do wartości  
 Jeśli źródło powiązania jest obiektem, użyj <xref:System.Windows.Data.Binding.Path%2A> właściwości w celu określenia wartości dla wiązania. Są wiązane [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] danych, użyj <xref:System.Windows.Data.Binding.XPath%2A> właściwości w celu określenia wartości. W niektórych przypadkach może być stosowane do użycia <xref:System.Windows.Data.Binding.Path%2A> właściwości nawet wtedy, gdy dane są [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]. Na przykład, jeśli chcesz uzyskać dostępu do właściwości Name zwrócony element XmlNode (w wyniku kwerendy XPath), należy użyć <xref:System.Windows.Data.Binding.Path%2A> właściwość oprócz <xref:System.Windows.Data.Binding.XPath%2A> właściwości.  
  
 Aby uzyskać informacje o składni i przykłady, zobacz <xref:System.Windows.Data.Binding.Path%2A> i <xref:System.Windows.Data.Binding.XPath%2A> strony właściwości.  
  
 Należy pamiętać, że chociaż firma Microsoft ma wyróżniony, który <xref:System.Windows.Data.Binding.Path%2A> wartości do użycia jest jednym z czterech niezbędne składniki powiązania w scenariuszach, które chcesz powiązać z całego obiektu, wartość będzie taki sam, jak obiekt źródłowy powiązania. W takich przypadkach nie ma zastosowania do Określa <xref:System.Windows.Data.Binding.Path%2A>. Rozważmy następujący przykład:  
  
 [!code-xaml[MasterDetail#EmptyBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MasterDetail/CSharp/Page1.xaml#emptybinding)]  
  
 Powyższy przykład używa składni powiązanie pusta: {powiązania}. W takim przypadku <xref:System.Windows.Controls.ListBox> dziedziczy DataContext z nadrzędnego elementu DockPanel (tego nie pokazano w tym przykładzie). Jeśli ścieżka nie jest określona, wartością domyślną jest powiązać całego obiektu. Innymi słowy, w tym przykładzie ścieżka została pozostawiona się, ponieważ firma Microsoft dokonywane jest wiązanie <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> właściwości do całego obiektu. (Zobacz [powiązanie z kolekcji](#binding_to_collections) sekcji szczegółowe omówienie.)  
  
 Inne niż powiązanie do kolekcji, w tym scenariuszu jest również przydatny podczas chcesz powiązać z całego obiektu zamiast jednej właściwości obiektu. Na przykład jeśli obiekt źródłowy jest typu string, a po prostu chcesz powiązać sam ciąg. Inny typowy scenariusz polega, jeśli chcesz powiązać element do obiektu z kilku właściwości.  
  
 Należy pamiętać, że może być konieczne zastosowanie niestandardowej logiki tak, aby dane były zrozumiałą dla użytkownika właściwość target powiązane. Niestandardowej logiki może być w formie konwertera niestandardowe (Jeśli nie istnieje konwersja typu domyślnego). Zobacz [Konwersja danych](#data_conversion) informacji o konwertery.  
  
<a name="binding_bindingexpression"></a>   
### <a name="binding-and-bindingexpression"></a>Powiązanie i operację BindingExpression  
 Przed przejściem do innych funkcji i użycia powiązania danych, warto byłoby wprowadzenie <xref:System.Windows.Data.BindingExpression> klasy. Jak już wspomniano w poprzedniej sekcji, <xref:System.Windows.Data.Binding> klasa jest klasą wysokiego poziomu dla deklaracji powiązanie; <xref:System.Windows.Data.Binding> klasy zawiera wiele właściwości, które umożliwiają określenie właściwości powiązania. Klasy pokrewne, <xref:System.Windows.Data.BindingExpression>, jest obiekt, który obsługuje połączenie między serwerem źródłowym a docelowym. Powiązanie zawiera wszystkie informacje, które mogą być współużytkowane przez kilka wyrażenia wiązania. A <xref:System.Windows.Data.BindingExpression> jest wyrażenie wystąpienia, które nie mogą być udostępniane i zawiera wszystkie wystąpienia informacje <xref:System.Windows.Data.Binding>.  
  
 Rozważmy na przykład następujące polecenie, gdzie *myDataObject* jest wystąpieniem *Moje_Dane* klasy *myBinding* jest źródłem <xref:System.Windows.Data.Binding> obiekt i *Moje_Dane* klasa jest klasą zdefiniowanych, który zawiera właściwości ciągu o nazwie *MyDataProperty*. W tym przykładzie wiąże zawartości tekstu *tekst*, wystąpienie <xref:System.Windows.Controls.TextBlock>, do *MyDataProperty*.  
  
 [!code-csharp[CodeOnlyBinding#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#1)]
 [!code-vb[CodeOnlyBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#1)]  
  
 Można używać tego samego *myBinding* obiekt, aby utworzyć inne powiązania. Na przykład może użyć *myBinding* do powiązania zawartości tekstowej pola wyboru obiektu *MyDataProperty*. W takim scenariuszu będzie dwa wystąpienia <xref:System.Windows.Data.BindingExpression> udostępnianie *myBinding* obiektu.  
  
 A <xref:System.Windows.Data.BindingExpression> obiektu można uzyskać za pomocą wartości zwrotnej wywołania <xref:System.Windows.Data.BindingOperations.GetBindingExpression%2A> w obiekcie powiązanym z danymi. Poniższe tematy przedstawiają niektóre z sposobów użycia <xref:System.Windows.Data.BindingExpression> klasy:  
  
-   [Pobieranie obiektu powiązania z właściwości powiązanej docelowego](../../../../docs/framework/wpf/data/how-to-get-the-binding-object-from-a-bound-target-property.md)  
  
-   [Formant, gdy tekst pola tekstowego aktualizuje źródła](../../../../docs/framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md)  
  
<a name="data_conversion"></a>   
## <a name="data-conversion"></a>Konwersja danych  
 W poprzednim przykładzie jest czerwony przycisk ponieważ jego <xref:System.Windows.Controls.Control.Background%2A> właściwość jest powiązana z właściwością ciągu o wartości "Red". To działa, ponieważ konwerter typów znajduje się na <xref:System.Windows.Media.Brush> typu można przekonwertować wartości ciągu na <xref:System.Windows.Media.Brush>.  
  
 Aby dodać te informacje do rysunku w [tworzenie powiązania](#creating_a_binding) sekcji diagramu wygląda podobnie do następującej:  
  
 ![Diagram powiązania danych](../../../../docs/framework/wpf/data/media/databindingbuttondefaultconversion.png "DataBindingButtonDefaultConversion")  
  
 Jednakże, co zrobić, jeśli zamiast właściwości typu ciąg, obiekt źródłowy powiązania jest *kolor* właściwości typu <xref:System.Windows.Media.Color>? W takim przypadku aby powiązanie działało konieczne będzie pierwszy Włącz *kolor* wartość właściwości na coś który <xref:System.Windows.Controls.Control.Background%2A> akceptuje właściwości. Należy utworzyć niestandardowe konwertera zaimplementowanie <xref:System.Windows.Data.IValueConverter> interfejsu, jak w poniższym przykładzie:  
  
 [!code-csharp[ColorPicker_snip#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ColorPicker_snip/CSharp/ColorPickerLib/ColorPicker.cs#16)]
 [!code-vb[ColorPicker_snip#16](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ColorPicker_snip/visualbasic/colorpickerlib/colorpicker.vb#16)]  
  
 <xref:System.Windows.Data.IValueConverter> Strona referencyjna zawiera więcej informacji.  
  
 Teraz konwertera niestandardowy jest używany zamiast domyślnego konwersji i naszych diagram wygląda następująco:  
  
 ![Diagram powiązania danych](../../../../docs/framework/wpf/data/media/databindingconvertercolorexample.png "DataBindingConverterColorExample")  
  
 Przywołują, konwersje domyślnego mogą być dostępne z powodu konwertery typu, które znajdują się w typie związany. To zachowanie będzie zależeć od konwertery typu, które są dostępne w miejscu docelowym. W razie wątpliwości, należy utworzyć własny konwertera.  
  
 Poniżej przedstawiono niektóre typowe scenariusze, w których warto wdrożyć konwertera danych:  
  
-   Dane powinny być wyświetlane w różny sposób, w zależności od kultury. Na przykład można zaimplementować Konwerter waluty lub kalendarza konwertera daty/godziny na podstawie wartości lub norm stosowanych w określonej kultury.  
  
-   Dane używane nie ma zawsze można zmienić wartości tekstowej właściwości, ale zamiast tego jest przeznaczona do zmiany innych wartość, na przykład źródło obrazu lub kolor lub styl tekstu. Konwertery można w tym wystąpieniu konwertując powiązania właściwości, które nie mogą wydawać się potrzebami, na przykład powiązanie pola tekstowego z właściwością tła w komórce tabeli.  
  
-   Więcej niż jeden formant lub na wiele właściwości formantów powiązanych z tymi samymi danymi. W takim przypadku głównej powiązanie właśnie może być wyświetlany tekst, pozostałych powiązaniach obsługi wyświetlania określonych problemów, ale nadal używać tego samego powiązania jako źródła informacji.  
  
-   Do tej pory nie jeszcze Omówiliśmy <xref:System.Windows.Data.MultiBinding>, gdy właściwość docelowa ma kolekcję powiązań. W przypadku liczby <xref:System.Windows.Data.MultiBinding>, użyć niestandardowego <xref:System.Windows.Data.IMultiValueConverter> do uzyskiwania wartości końcowe z wartości powiązania. Na przykład kolor może być obliczana na podstawie czerwona, niebieska i zielony wartości, które mogą być wartościami z tego samego lub innego powiązania obiekty źródła. Zobacz <xref:System.Windows.Data.MultiBinding> strony klasy przykłady i informacje.  
  
<a name="binding_to_collections"></a>   
## <a name="binding-to-collections"></a>Powiązanie z kolekcji  
  
 Obiekt źródłowy powiązania może być traktowana jako pojedynczy obiekt, którego właściwości zawierają dane lub kolekcji danych polimorficznych obiektów, które są często grupowane razem (na przykład wynik zapytania do bazy danych). Do tej pory tylko Wiemy już powiązania do pojedynczych obiektów, jednak powiązania do zbierania danych jest typowym scenariuszem. Na przykład typowy scenariusz jest użycie <xref:System.Windows.Controls.ItemsControl> takich jak <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.ListView>, lub <xref:System.Windows.Controls.TreeView> do wyświetlenia zbierania danych, takie jak w aplikacji [co to jest powiązanie danych?](#what_is_data_binding) sekcji.  
  
 Na szczęście naszych diagram podstawowy nadal istnieje. Są wiązane <xref:System.Windows.Controls.ItemsControl> do kolekcji, diagram wygląda następująco:  
  
 ![Diagram ItemsControl powiązania danych](../../../../docs/framework/wpf/data/media/databindingitemscontrol.png "DataBindingItemsControl")  
  
 Jak pokazano na tym diagramie, aby powiązać <xref:System.Windows.Controls.ItemsControl> do obiektu kolekcji <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> właściwość jest właściwością do użycia. Można potraktować <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> właściwość jako zawartość <xref:System.Windows.Controls.ItemsControl>. Należy zauważyć, że powiązanie <xref:System.Windows.Data.BindingMode.OneWay> ponieważ <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> obsługuje właściwość <xref:System.Windows.Data.BindingMode.OneWay> powiązanie domyślnie.  
  
<a name="how_to_implement_collections"></a>   
### <a name="how-to-implement-collections"></a>Jak zaimplementować kolekcje  
 Można wyliczać za pośrednictwem kolekcji, która implementuje <xref:System.Collections.IEnumerable> interfejsu. Jednak aby skonfigurować dynamiczne powiązania, aby zaktualizować wstawienia lub usunięć w kolekcji [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] automatycznie, Kolekcja musi zawierać <xref:System.Collections.Specialized.INotifyCollectionChanged> interfejsu. Ten interfejs przedstawia zdarzenia, które powinien być wywoływany przy każdej zmianie kolekcji źródłowej.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]udostępnia <xref:System.Collections.ObjectModel.ObservableCollection%601> klasy, która jest wbudowana implementacji zbierania danych, który ujawnia <xref:System.Collections.Specialized.INotifyCollectionChanged> interfejsu. Należy pamiętać, że do zapewnienia pełnej obsługi przesyłania wartości z obiekty źródła danych do obiektów docelowych, każdy obiekt w kolekcji, który obsługuje właściwości musi implementować też <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu. Aby uzyskać więcej informacji, zobacz [powiązanie Przegląd źródeł](../../../../docs/framework/wpf/data/binding-sources-overview.md).  
  
 Przed wdrożeniem swojej kolekcji, należy rozważyć użycie <xref:System.Collections.ObjectModel.ObservableCollection%601> lub jeden z istniejącą kolekcję klas, takich jak <xref:System.Collections.Generic.List%601>, <xref:System.Collections.ObjectModel.Collection%601>, i <xref:System.ComponentModel.BindingList%601>, wśród wielu innych. Jeśli masz zaawansowanego scenariusza i zaimplementować swojej kolekcji, należy rozważyć użycie <xref:System.Collections.IList>, co umożliwia kolekcja nierodzajową obiektów, które można można indywidualnie uzyskać dostęp przez indeks i w związku z tym najlepszą wydajność.  
  
<a name="collection_views"></a>   
### <a name="collection-views"></a>Kolekcja widoków  
 Raz z <xref:System.Windows.Controls.ItemsControl> jest powiązany z zbierania danych, może zajść potrzeba sortowania, filtr lub grupy danych. Aby to zrobić, użyj widoków kolekcji, które są klas implementujących <xref:System.ComponentModel.ICollectionView> interfejsu.  
  
  
#### <a name="what-are-collection-views"></a>Co to są widoki kolekcji?  
 Widok kolekcji jest warstwą kolekcję źródło powiązania, która umożliwia nawigacji i wyświetlania kolekcji źródłowej na podstawie sortowania, filtrów i grupy zapytań, bez konieczności zmiany podstawowego źródła kolekcji. Widok kolekcji zachowuje również wskaźnik do bieżącego elementu w kolekcji. Jeśli implementuje kolekcji źródłowej <xref:System.Collections.Specialized.INotifyCollectionChanged> interfejsu zmiany zgłoszone przez <xref:System.Collections.Specialized.INotifyCollectionChanged.CollectionChanged> zdarzenia są propagowane do widoków.  
  
 Ponieważ widoki nie należy zmieniać podstawowej kolekcji źródłowej, każda kolekcja źródła może mieć wiele widoków skojarzonych z nim. Na przykład może być kolekcją *zadań* obiektów. Podczas korzystania z widoków można wyświetlić danych tego samego na różne sposoby. Na przykład w lewej części strony można wyświetlić zadania sortowane według priorytetu i po prawej stronie, pogrupowane według obszaru.  
  
<a name="how_to_create_a_view"></a>   
#### <a name="how-to-create-a-view"></a>Jak utworzyć widok  
 Jednym ze sposobów tworzenia i używania widoku jest bezpośrednio utworzyć wystąpienia obiektu widoku, a następnie użyć jej jako źródła powiązania. Rozważmy na przykład [pokaz powiązania danych](http://go.microsoft.com/fwlink/?LinkID=163703) wyświetlany w aplikacji [co to jest powiązanie danych?](#what_is_data_binding) sekcji. Zaimplementowano aplikacji tak, aby <xref:System.Windows.Controls.ListBox> wiąże widoku i kolekcji danych zamiast zbierania danych. Poniższy przykład jest wyodrębniana z [pokaz powiązania danych](http://go.microsoft.com/fwlink/?LinkID=163703) aplikacji. <xref:System.Windows.Data.CollectionViewSource> Jest klasa [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] serwera proxy, który dziedziczy z klasy <xref:System.Windows.Data.CollectionView>. W tym przykładzie <xref:System.Windows.Data.CollectionViewSource.Source%2A> widoku jest powiązany z *AuctionItems* kolekcji (typu <xref:System.Collections.ObjectModel.ObservableCollection%601>) bieżącego obiektu aplikacji.  
  
 [!code-xaml[DataBindingLab#WindowResources1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#windowresources1)]  
[!code-xaml[DataBindingLab#CollectionViewSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#collectionviewsource)]  
[!code-xaml[DataBindingLab#WindowResources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#windowresources2)]  
  
 Zasób *listingDataView* następnie służy jako źródło powiązania dla elementów w aplikacji, takich jak <xref:System.Windows.Controls.ListBox>:  
  
 [!code-xaml[DataBindingLab#Master1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master1)]  
[!code-xaml[DataBindingLab#Master2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master2)]  
  
 Aby utworzyć inny widok dla danej kolekcji, należy utworzyć inny <xref:System.Windows.Data.CollectionViewSource> wystąpienia i nadaj mu inną `x:Key` nazwy.  
  
 W poniższej tabeli przedstawiono typy danych widoku są tworzone jako domyślny widok kolekcji lub przez <xref:System.Windows.Data.CollectionViewSource> na podstawie typu kolekcji źródłowej.  
  
|Typ kolekcji źródła|Typ widoku kolekcji|Uwagi|  
|----------------------------|--------------------------|-----------|  
|<xref:System.Collections.IEnumerable>|Wewnętrzny typ na podstawie<xref:System.Windows.Data.CollectionView>|Nie można grupować elementy.|  
|<xref:System.Collections.IList>|<xref:System.Windows.Data.ListCollectionView>|Najszybszym.|  
|<xref:System.ComponentModel.IBindingList>|<xref:System.Windows.Data.BindingListCollectionView>||  
  
##### <a name="using-a-default-view"></a>Przy użyciu widok domyślny  
 Określenie widok kolekcji jako źródło powiązania jest jednym ze sposobów tworzenia i używania widok kolekcji. WPF tworzy również domyślny widok kolekcji dla każdej kolekcji używany jako źródło powiązania. Jeśli możesz powiązać bezpośrednio do kolekcji WPF wiąże się z jego widok domyślny. Należy pamiętać, że ten widok domyślny jest współużytkowana przez wszystkie powiązania do tej samej kolekcji, więc zmiany wprowadzone do widoku domyślnego przez jeden formant związany lub kodu (na przykład sortowania lub zmianę na wskaźnik bieżącego elementu, omówiono w dalszej części) jest widoczny w pozostałych powiązaniach do tej samej kolekcji.  
  
 Aby uzyskać widok domyślny, należy użyć <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> metody. Na przykład zobacz [uzyskać widok domyślny zbierania danych](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md).  
  
##### <a name="collection-views-with-adonet-datatables"></a>Widoki kolekcji z ADO.NET DataTables  
 Aby zwiększyć wydajność, Kolekcja widoków dla ADO.NET <xref:System.Data.DataTable> lub <xref:System.Data.DataView> obiektów delegata, sortowanie i filtrowanie <xref:System.Data.DataView>. Powoduje to sortowanie i filtrowanie jest współużytkowana przez wszystkie widoki kolekcji źródła danych. Aby włączyć widok każdej kolekcji można sortować i filtrować niezależnie, zainicjować każdego widoku kolekcji własny <xref:System.Data.DataView> obiektu.  
  
#### <a name="sorting"></a>Sortowanie  
 Jak wspomniano wcześniej, widoki, można zastosować kolejność sortowania do kolekcji. Ponieważ istnieje w kolekcji źródłowej, dane mogą lub może nie mieć kolejność istotne, związanego z używaniem. Widok w kolekcji umożliwia nałożyć kolejności lub zmienić domyślną kolejność, na podstawie kryteriów porównanie, które należy podać. Typowy scenariusz, ponieważ widok danych opartą na kliencie, jest, użytkownik może chcesz sortować kolumny danych tabelarycznych na wartość, która odpowiada kolumnie. Korzystanie z widoków, tego rodzaju oparte na użytkownika można zastosować, ponownie bez wprowadzania jakichkolwiek zmian w źródłowej kolekcji lub nawet do requery zawartości kolekcji. Na przykład zobacz [sortowania w widoku GridView kolumny po kliknięciu nagłówka](../../../../docs/framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md).  
  
 W poniższym przykładzie przedstawiono sortowania logiki "Sortowania według kategorii i daty" <xref:System.Windows.Controls.CheckBox> aplikacji [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] w [co to jest powiązanie danych?](#what_is_data_binding) sekcji:  
  
 [!code-csharp[DataBindingLab#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#8)]
 [!code-vb[DataBindingLab#8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#8)]  
  
#### <a name="filtering"></a>Filtrowanie  
 Widoki można również zastosować filtr do kolekcji. Oznacza to, że chociaż elementu może istnieć w kolekcji, tego widoku jest przeznaczona do Pokaż tylko niektórych podzbiór pełnej kolekcji. Można filtrować pod warunkiem w danych. Na przykład, jak odbywa się przez aplikację w [co to jest powiązanie danych?](#what_is_data_binding) sekcji "Pokaż tylko okazje" <xref:System.Windows.Controls.CheckBox> zawiera logikę do filtrowania elementów, których koszt 25 lub więcej. Poniższy kod jest wykonywany w celu ustawić *ShowOnlyBargainsFilter* jako <xref:System.Windows.Data.CollectionViewSource.Filter> obsługi zdarzeń podczas która <xref:System.Windows.Controls.CheckBox> wybrano:  
  
 [!code-csharp[DataBindingLab#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#10)]
 [!code-vb[DataBindingLab#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#10)]  
  
 *ShowOnlyBargainsFilter* obsługi zdarzeń ma następujące wdrożenia:  
  
 [!code-csharp[DataBindingLab#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#5)]
 [!code-vb[DataBindingLab#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#5)]  
  
 Jeśli używasz jednego z <xref:System.Windows.Data.CollectionView> klasy bezpośrednio zamiast z <xref:System.Windows.Data.CollectionViewSource>, należy użyć <xref:System.Windows.Data.CollectionView.Filter%2A> właściwości w celu określenia wywołania zwrotnego. Na przykład zobacz [filtrowanie danych w widoku](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md).  
  
#### <a name="grouping"></a>Grupowanie  
 Z wyjątkiem wewnętrznych klasy, która wyświetla <xref:System.Collections.IEnumerable> kolekcji, wszystkie widoki kolekcji obsługi funkcji grupowania, który umożliwia użytkownikowi partycji kolekcji w widoku kolekcji w grupy logiczne. Grupy można w przypadku, gdy użytkownik podaje listę grup, bezpośrednie lub pośrednie, których grup są generowane dynamicznie w zależności od danych.  
  
 W poniższym przykładzie pokazano logikę "Grupuj według kategorii" <xref:System.Windows.Controls.CheckBox>:  
  
 [!code-csharp[DataBindingLab#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#6)]
 [!code-vb[DataBindingLab#6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#6)]  
  
 Na przykład innego grupowania, zobacz [grupy elementów w implementuje czy ListView Element GridView](../../../../docs/framework/wpf/controls/how-to-group-items-in-a-listview-that-implements-a-gridview.md).  
  
#### <a name="current-item-pointers"></a>Bieżący element wskaźników  
 Widoki obsługuje również podstawowe pojęcie w zakresie bieżącego elementu. Obiekty w widoku kolekcji można nawigować. Podczas nawigacji, który przenosisz wskaźnik elementu, który pozwala na pobieranie obiektu, który istnieje w tej lokalizacji określonej w kolekcji. Na przykład zobacz [przejdź do obiektów w CollectionView danych](../../../../docs/framework/wpf/data/how-to-navigate-through-the-objects-in-a-data-collectionview.md).  
  
 Ponieważ WPF wiąże się z kolekcji wszystkie powiązania z kolekcji mają tylko przy użyciu widoku (widok, do którego należy określić albo kolekcji domyślny widok), bieżący wskaźnik elementu. Podczas wiązania z widoku, ukośnika ("/") znaków w `Path` wartość Określa bieżący element w widoku. W poniższym przykładzie kontekst danych jest widokiem kolekcji. Pierwszy wiersz wiąże się z kolekcji. Drugi wiersz tworzy powiązanie z bieżącego elementu w kolekcji. Trzeci wiersz wiąże `Description` właściwości bieżącego elementu w kolekcji.  
  
```xaml  
<Button Content="{Binding }" />  
<Button Content="{Binding Path=/}" />  
<Button Content="{Binding Path=/Description}" />   
```  
  
 Składnia ukośnika i właściwości można też skumulowany przechodzenie hierarchii kolekcji. Poniższy przykład tworzy powiązanie z bieżącego elementu kolekcji o nazwie `Offices`, czyli właściwości bieżącego elementu kolekcji źródłowej.  
  
```xaml  
<Button Content="{Binding /Offices/}" />  
```  
  
 Bieżący wskaźnik elementu mogą mieć wpływ wszelkie sortowanie lub filtrowanie są stosowane do kolekcji. Sortowanie zachowuje bieżący wskaźnik elementu na ostatniego elementu wybrane, ale teraz restrukturyzacji widok kolekcji wokół niego. (Być może został wybrany element na początku listy przed, ale wybrany element może być teraz gdzieś w środku). Filtrowanie zachowuje wybranego elementu, jeśli Wybieranie pozostaje w widoku po filtrowania. W przeciwnym razie bieżący wskaźnik elementu ma ustawioną wartość pierwszego elementu w widoku filtrowanego kolekcji.  
  
<a name="master_detail_scenario"></a>   
#### <a name="master-detail-binding-scenario"></a>Scenariusz wiązania główny szczegółowy  
 Podstawowe pojęcie w zakresie bieżącego elementu przydaje się nie tylko dla nawigacji elementów w kolekcji, ale również scenariusz wiązania główny szczegółowy. Należy wziąć pod uwagę aplikacji [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] w [co to jest powiązanie danych?](#what_is_data_binding) sekcji ponownie. W tej aplikacji, wybór w <xref:System.Windows.Controls.ListBox> określa zawartość wyświetlaną <xref:System.Windows.Controls.ContentControl>. Go umieścić w inny sposób, gdy <xref:System.Windows.Controls.ListBox> element jest wybrany, <xref:System.Windows.Controls.ContentControl> szczegóły wybranego elementu.  
  
 Scenariusz główny szczegółowy można zaimplementować po prostu, konfigurując dwa lub więcej formanty powiązane z tego samego widoku. Poniższy przykład z [pokaz powiązania danych](http://go.microsoft.com/fwlink/?LinkID=163703) przedstawia użycie znaczników z <xref:System.Windows.Controls.ListBox> i <xref:System.Windows.Controls.ContentControl> zostanie wyświetlony w aplikacji [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] w [co to jest powiązanie danych?](#what_is_data_binding) sekcji:  
  
 [!code-xaml[DataBindingLab#Master1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master1)]  
[!code-xaml[DataBindingLab#Master2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master2)]  
[!code-xaml[DataBindingLab#Detail](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#detail)]  
  
 Zwróć uwagę, zarówno z formantów powiązanych z tym samym źródłem *listingDataView* zasobów statyczne (patrz definicja tego zasobu w [sposób tworzenia widoku sekcji](#how_to_create_a_view)). To działa, ponieważ podczas pojedynczego obiektu ( <xref:System.Windows.Controls.ContentControl> w takim przypadku) jest powiązana do widoku kolekcji, jest on automatycznie powiązany z <xref:System.Windows.Data.CollectionView.CurrentItem%2A> widoku. Należy pamiętać, że <xref:System.Windows.Data.CollectionViewSource> obiektów automatycznie synchronizować waluty i zaznaczenia. Jeśli nie jest powiązany z formantu listy <xref:System.Windows.Data.CollectionViewSource> obiekt jak w poniższym przykładzie, a następnie należy ustawić jego <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> właściwości `true` Aby to zrobić.  
  
 Inne przykłady można znaleźć [powiązania w kolekcji i wyświetlania informacji na podstawie zaznaczenia](../../../../docs/framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md) i [Użyj wzorca wzorzec-szczegół z danymi hierarchicznymi](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md).  
  
 Można zauważyć, że powyższy przykład używa szablonu. W rzeczywistości, danych czy nie można wyświetlić sposób Życzymy bez korzystania z szablonów (jawnie używany przez <xref:System.Windows.Controls.ContentControl> niejawnie stosowana przez <xref:System.Windows.Controls.ListBox>). Włącz możemy teraz do tworzenia szablonów danych w następnej sekcji.  
  
<a name="data_templating"></a>   
## <a name="data-templating"></a>Tworzenia szablonów danych  
 Bez użycia szablonów danych, aplikacji [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] w [co to jest powiązanie danych?](#what_is_data_binding) sekcji będzie wyglądać podobnie do następującej:  
  
 ![Pokaz bez użycia szablonów danych tworzenia powiązania danych](../../../../docs/framework/wpf/data/media/databindingdemotemplates.png "DataBindingDemoTemplates")  
  
 Jak pokazano w przykładzie w poprzedniej sekcji, zarówno <xref:System.Windows.Controls.ListBox> kontroli i <xref:System.Windows.Controls.ContentControl> są powiązane z obiektu całą kolekcję lub dokładniej, widok na obiekt kolekcji *AuctionItem*s. Bez szczegółowe instrukcje sposobu wyświetlania zbierania danych <xref:System.Windows.Controls.ListBox> są wyświetlane reprezentację ciągu każdego obiektu w kolekcji źródłowej i <xref:System.Windows.Controls.ContentControl> są wyświetlane reprezentację ciągu obiektu jest powiązany.  
  
 Aby rozwiązać ten problem, aplikacji definiuje <xref:System.Windows.DataTemplate>s. Jak pokazano w przykładzie w poprzedniej sekcji, <xref:System.Windows.Controls.ContentControl> jawnie używa *detailsProductListingTemplate*<xref:System.Windows.DataTemplate>. <xref:System.Windows.Controls.ListBox> Formant niejawnie wykorzystuje następujące <xref:System.Windows.DataTemplate> podczas wyświetlania *AuctionItem* obiektów w kolekcji:  
  
 [!code-xaml[DataBindingLab#AuctionItemDataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#auctionitemdatatemplate)]  
  
 Podczas korzystania z tych dwóch <xref:System.Windows.DataTemplate>, wynikowy interfejsu użytkownika jest wskazano [co to jest powiązanie danych?](#what_is_data_binding) sekcji. Jak widać w tym zrzut ekranu, oprócz wynajmowanie umieszczeniu danych w Twoich formantów <xref:System.Windows.DataTemplate>s umożliwiają definiowanie atrakcyjnych elementy wizualne dla danych. Na przykład <xref:System.Windows.DataTrigger>s używanych w powyższych <xref:System.Windows.DataTemplate> , aby *AuctionItem*s *SpecialFeatures* wartość *zaznacz* będzie wyświetlana z pomarańczowy obramowania i gwiazdy.  
  
 Aby uzyskać więcej informacji na temat szablonów danych, zobacz [omówienie tworzenia szablonów danych](../../../../docs/framework/wpf/data/data-templating-overview.md).  
  
<a name="data_validation"></a>   
## <a name="data-validation"></a>Sprawdzanie poprawności danych  
  
 Większość aplikacji, które przyjmują dane wejściowe użytkownika musi być logikę weryfikacji, aby upewnić się, że użytkownik wprowadził oczekiwane informacje. Sprawdzanie poprawności może bazować na typ, zakres, format lub innych wymagań specyficznych dla aplikacji. W tej sekcji opisano, jak działa sprawdzanie poprawności danych w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### <a name="associating-validation-rules-with-a-binding"></a>Kojarzenie z powiązaniem reguły walidacji  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Modelu powiązania danych umożliwia skojarzenie <xref:System.Windows.Data.Binding.ValidationRules%2A> z Twojej <xref:System.Windows.Data.Binding> obiektu. Na przykład poniższy przykład wiąże <xref:System.Windows.Controls.TextBox> do właściwości o nazwie `StartPrice` i dodaje <xref:System.Windows.Controls.ExceptionValidationRule> do obiektu <xref:System.Windows.Data.Binding.ValidationRules%2A?displayProperty=nameWithType> właściwości.  
  
 [!code-xaml[DataBindingLab#DefaultValidation](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/AddProductWindow.xaml#defaultvalidation)]  
  
 A <xref:System.Windows.Controls.ValidationRule> obiektu sprawdza, czy wartość właściwości jest nieprawidłowa. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ma następujące dwa typy wbudowane <xref:System.Windows.Controls.ValidationRule> obiektów:  
  
-   A <xref:System.Windows.Controls.ExceptionValidationRule> sprawdza, czy wyjątki zgłaszane podczas aktualizacji powiązania właściwości source. W poprzednim przykładzie `StartPrice` jest typu integer. Kiedy użytkownik wprowadzi wartość, której nie można przekonwertować na liczbę całkowitą, jest zgłaszany wyjątek, powodując powiązania może być oznaczony jako nieprawidłowy. Alternatywne składni ustawienie <xref:System.Windows.Controls.ExceptionValidationRule> jawnie jest skonfigurowanie <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> właściwości `true` na Twojej <xref:System.Windows.Data.Binding> lub <xref:System.Windows.Data.MultiBinding> obiektu.  
  
-   A <xref:System.Windows.Controls.DataErrorValidationRule> obiektu sprawdza, czy błędy, które zostały zgłoszone przez obiekty, które implementują <xref:System.ComponentModel.IDataErrorInfo> interfejsu. Przykład użycia tej reguły sprawdzania poprawności, zobacz <xref:System.Windows.Controls.DataErrorValidationRule>. Alternatywne składni ustawienie <xref:System.Windows.Controls.DataErrorValidationRule> jawnie jest skonfigurowanie <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> właściwości `true` na Twojej <xref:System.Windows.Data.Binding> lub <xref:System.Windows.Data.MultiBinding> obiektu.  
  
 Można również utworzyć własne reguły weryfikacji przez wynikających z <xref:System.Windows.Controls.ValidationRule> klasy i wdrażanie <xref:System.Windows.Controls.ValidationRule.Validate%2A> metody. W poniższym przykładzie przedstawiono regułą używaną przez *Dodaj listę produktów* "Data rozpoczęcia" <xref:System.Windows.Controls.TextBox> z [co to jest powiązanie danych?](#what_is_data_binding) sekcji:  
  
 [!code-csharp[DataBindingLab#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/FutureDateRule.cs#2)]
 [!code-vb[DataBindingLab#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/FutureDateRule.vb#2)]  
  
 *StartDateEntryForm* <xref:System.Windows.Controls.TextBox> używa to *FutureDateRule*, jak pokazano w poniższym przykładzie:  
  
 [!code-xaml[DataBindingLab#CustomValidation](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/AddProductWindow.xaml#customvalidation)]  
  
 Należy pamiętać, że ponieważ <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> wartość jest <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>, aparat wiązania aktualizuje wartość źródła po każdym naciśnięciu klawisza, oznacza ona również kontrole każda reguła w <xref:System.Windows.Data.Binding.ValidationRules%2A> kolekcji po każdym naciśnięciu klawisza. Omówiono to w dalszej części procesu weryfikacji.  
  
<a name="invalidation_feedback"></a>   
### <a name="providing-visual-feedback"></a>Przekazywanie opinii Visual  
 Jeśli użytkownik wprowadzi wartość jest nieprawidłowa, można podać niektóre swoją opinię na temat błędu w aplikacji [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Jednym ze sposobów zapewnienia takiego opinii jest skonfigurowanie <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType> dołączonych właściwości do niestandardowego <xref:System.Windows.Controls.ControlTemplate>. Jak pokazano w poprzednim podsekcji *StartDateEntryForm* <xref:System.Windows.Controls.TextBox> używa <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> o nazwie *validationTemplate*. W poniższym przykładzie przedstawiono definicję *validationTemplate*:  
  
 [!code-xaml[DataBindingLab#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/AddProductWindow.xaml#1)]  
  
 <xref:System.Windows.Controls.AdornedElementPlaceholder> Element określa rozmieszczenia jest adorned formantu.  
  
 Ponadto można także użyć <xref:System.Windows.Controls.ToolTip> wyświetlenie komunikatu o błędzie. Zarówno *StartDateEntryForm* i *StartPriceEntryForm*<xref:System.Windows.Controls.TextBox>es użyć stylu *textStyleTextBox*, co powoduje <xref:System.Windows.Controls.ToolTip> który Wyświetla komunikat o błędzie. W poniższym przykładzie przedstawiono definicję *textStyleTextBox*. Dołączona właściwość <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true` kiedy są co najmniej jednego powiązania we właściwościach elementu powiązania błędu.  
  
 [!code-xaml[DataBindingLab#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#14)]  
  
 Z niestandardowym <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> i <xref:System.Windows.Controls.ToolTip>, *StartDateEntryForm* <xref:System.Windows.Controls.TextBox> wygląda podobnie do następującego po błąd sprawdzania poprawności:  
  
 ![Błąd sprawdzania poprawności powiązania danych](../../../../docs/framework/wpf/data/media/databindingdemo-validation.PNG "DataBindingDemo_Validation")  
  
 Jeśli Twoje <xref:System.Windows.Data.Binding> skojarzone reguły sprawdzania poprawności, ale nie określono <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> na powiązanej kontrolki, domyślny <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> będzie służyć do Powiadamiaj użytkowników, gdy występuje błąd weryfikacji. Wartość domyślna <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> jest to szablon formantu, który definiuje czerwonym obramowaniem w warstwie modułu definiowania układu kodu. Przy użyciu domyślnego <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> i <xref:System.Windows.Controls.ToolTip>, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] z *StartPriceEntryForm* <xref:System.Windows.Controls.TextBox> wygląda podobnie do następującego po błąd sprawdzania poprawności:  
  
 ![Błąd sprawdzania poprawności powiązania danych](../../../../docs/framework/wpf/data/media/databindingdemo-validationdefault.PNG "DataBindingDemo_ValidationDefault")  
  
 Na przykład jak zapewnić logiki, aby sprawdzić poprawność wszystkich kontrolek w oknie dialogowym, zobacz sekcję niestandardowych okien dialogowych w [omówienie pola dialogowe](../../../../docs/framework/wpf/app-development/dialog-boxes-overview.md).  
  
### <a name="validation-process"></a>Proces weryfikacji  
 Sprawdzanie poprawności zwykle występuje, gdy wartość elementu docelowego jest przenoszona do powiązania właściwości source. Dzieje się tak na <xref:System.Windows.Data.BindingMode.TwoWay> i <xref:System.Windows.Data.BindingMode.OneWayToSource> powiązania. Przywołują, co powoduje, że aktualizacja źródeł zależy od wartości <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> właściwości, zgodnie z opisem w [co wyzwalaczy źródła aktualizacji](#what_triggers_source_updates) sekcji.  
  
 Poniżej opisano *weryfikacji* procesu. Należy pamiętać, że jeśli wystąpi błąd sprawdzania poprawności lub inny typ błędu w dowolnym momencie w trakcie tego procesu, proces jest zatrzymany.  
  
1.  Aparat wiązania sprawdza, czy istnieją niestandardowe <xref:System.Windows.Controls.ValidationRule> zdefiniowanych obiektów, których <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> ustawiono <xref:System.Windows.Controls.ValidationStep.RawProposedValue> tego <xref:System.Windows.Data.Binding>, w takim przypadku wywołania <xref:System.Windows.Controls.ValidationRule.Validate%2A> metody na każdym <xref:System.Windows.Controls.ValidationRule> dopóki jeden z nich działa wystąpił błąd lub do momentu przekazania ich wszystkich.  
  
2.  Aparat wiązania wywołuje konwerter, jeśli taka istnieje.  
  
3.  Jeśli konwerter zakończy się powodzeniem, aparat wiązania sprawdza, czy istnieją niestandardowe <xref:System.Windows.Controls.ValidationRule> zdefiniowanych obiektów, których <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> ustawiono <xref:System.Windows.Controls.ValidationStep.ConvertedProposedValue> tego <xref:System.Windows.Data.Binding>, w takim przypadku wywołania <xref:System.Windows.Controls.ValidationRule.Validate%2A> metody na każdym <xref:System.Windows.Controls.ValidationRule> mający <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> ustawioną <xref:System.Windows.Controls.ValidationStep.ConvertedProposedValue> do momentu jeden z nich jest uruchamiana w błąd lub przekaż je wszystkie.  
  
4.  Aparat wiązania ustawia właściwości source.  
  
5.  Aparat wiązania sprawdza, czy istnieją niestandardowe <xref:System.Windows.Controls.ValidationRule> zdefiniowanych obiektów, których <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> ustawiono <xref:System.Windows.Controls.ValidationStep.UpdatedValue> tego <xref:System.Windows.Data.Binding>, w takim przypadku wywołania <xref:System.Windows.Controls.ValidationRule.Validate%2A> metody na każdym <xref:System.Windows.Controls.ValidationRule> mający <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> ustawioną <xref:System.Windows.Controls.ValidationStep.UpdatedValue> do momentu jeden z nich jest uruchamiana w błąd lub przekaż je wszystkie. Jeśli <xref:System.Windows.Controls.DataErrorValidationRule> jest skojarzony z powiązaniem i jego <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> ma ustawioną wartość domyślną, <xref:System.Windows.Controls.ValidationStep.UpdatedValue>, <xref:System.Windows.Controls.DataErrorValidationRule> zaznaczono w tym momencie. Jest to punkt podczas powiązania, które mają <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> ustawioną `true` są sprawdzane.  
  
6.  Aparat wiązania sprawdza, czy istnieją niestandardowe <xref:System.Windows.Controls.ValidationRule> zdefiniowanych obiektów, których <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> ustawiono <xref:System.Windows.Controls.ValidationStep.CommittedValue> tego <xref:System.Windows.Data.Binding>, w takim przypadku wywołania <xref:System.Windows.Controls.ValidationRule.Validate%2A> metody na każdym <xref:System.Windows.Controls.ValidationRule> mający <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> ustawioną <xref:System.Windows.Controls.ValidationStep.CommittedValue> do momentu jeden z nich jest uruchamiana w błąd lub przekaż je wszystkie.  
  
 Jeśli <xref:System.Windows.Controls.ValidationRule> nie zostały spełnione w dowolnym momencie w trakcie tego procesu aparat wiązania tworzy <xref:System.Windows.Controls.ValidationError> obiektu i dodaje go do <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> kolekcji elementu powiązania. Przed rozpoczęciem powiązania uruchamia aparat <xref:System.Windows.Controls.ValidationRule> obiektów na dowolnym etapie danego, usuwa wszelkie <xref:System.Windows.Controls.ValidationError> do dodano <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> dołączona właściwość elementu powiązania w tym kroku. Na przykład jeśli <xref:System.Windows.Controls.ValidationRule> których <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> ustawiono <xref:System.Windows.Controls.ValidationStep.UpdatedValue> nie powiodło się, przy następnym odbywa się proces sprawdzania poprawności, usuwa aparat wiązania, które <xref:System.Windows.Controls.ValidationError> bezpośrednio przed wywołaniem dowolnej <xref:System.Windows.Controls.ValidationRule> mający <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> ustawioną <xref:System.Windows.Controls.ValidationStep.UpdatedValue>.  
  
 Gdy <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> nie jest pusta, <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> dołączona właściwość elementu ma wartość `true`. Ponadto jeśli <xref:System.Windows.Data.Binding.NotifyOnValidationError%2A> właściwość <xref:System.Windows.Data.Binding> ma ustawioną wartość `true`, a następnie wywołuje aparat wiązania <xref:System.Windows.Controls.Validation.Error?displayProperty=nameWithType> dołączony zdarzeń dla elementu.  
  
 Należy także zauważyć, że czyści przeniesienia prawidłową wartość w obu kierunkach (docelowy źródło lub źródłowego do docelowego) <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> dołączona właściwość.  
  
 Jeśli ma powiązanie <xref:System.Windows.Controls.ExceptionValidationRule> skojarzonych z nim lub miała <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> właściwość jest ustawiona na `true` i gdy aparat wiązania ustawia źródło, jest zgłaszany wyjątek, aparat wiązania sprawdza, czy jest <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>. Istnieje możliwość użycia <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A> wywołania zwrotnego w celu zapewnienia obsługi niestandardowych do obsługi wyjątków. Jeśli <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A> nie jest określona w <xref:System.Windows.Data.Binding>, tworzy aparat wiązania <xref:System.Windows.Controls.ValidationError> z wyjątkiem i dodaje go do <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> kolekcji elementu powiązania.  
  
## <a name="debugging-mechanism"></a>Mechanizm debugowania  
 Dołączona właściwość można ustawić <xref:System.Diagnostics.PresentationTraceSources.TraceLevel%2A?displayProperty=nameWithType> w obiekcie związanych z powiązania do odbierania informacji o stanie określonego powiązania.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.DataErrorValidationRule>  
 [Nowości w wersji WPF 4.5](../../../../docs/framework/wpf/getting-started/whats-new.md)  
 [Powiązać wyników zapytania LINQ](../../../../docs/framework/wpf/data/how-to-bind-to-the-results-of-a-linq-query.md)  
 [Powiązanie danych](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [Wersja demonstracyjna dla powiązania danych](http://go.microsoft.com/fwlink/?LinkID=163703)  
 [Tematy porad](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)  
 [Powiązanie ze źródłem danych ADO.NET](../../../../docs/framework/wpf/data/how-to-bind-to-an-ado-net-data-source.md)
