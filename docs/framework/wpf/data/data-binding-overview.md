---
title: Przegląd Wiązanie danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data conversion for binding [WPF]
- binding data [WPF], about data binding
- data binding [WPF], about data binding
- conversion for data binding [WPF]
ms.assetid: c707c95f-7811-401d-956e-2fffd019a211
ms.openlocfilehash: 1b34b3369e5a045f45251d3285f10bf74b6f0d33
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "45990079"
---
# <a name="data-binding-overview"></a>Przegląd Wiązanie danych
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Powiązanie danych zapewnia prosty i spójny sposób w przypadku aplikacji, umożliwiające zaprezentowanie i interakcję z danymi. Elementy może być powiązana z danymi z różnych źródeł danych w formie [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] obiektów i [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]. <xref:System.Windows.Controls.ContentControl>s, takie jak <xref:System.Windows.Controls.Button> i <xref:System.Windows.Controls.ItemsControl>s, takie jak <xref:System.Windows.Controls.ListBox> i <xref:System.Windows.Controls.ListView> posiada wbudowanej funkcji, aby umożliwić elastyczne stylu pojedynczymi elementami danych lub kolekcje elementów danych. Sortowanie, filtrowanie i widoki grup mogą być generowane na podstawie danych.  
  
 Funkcji wiązania danych w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ma kilka zalet w stosunku do tradycyjnych modeli, w tym szerokiej gamy właściwości, które standardowo obsługuje powiązanie danych, elastyczne [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] reprezentacja danych i czystą separacji działalności biznesowej logiki [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
 W tym temacie omówiono najpierw koncepcje podstawowe znaczenie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] powiązanie danych i następnie zbliża się do użycia <xref:System.Windows.Data.Binding> klasy i inne funkcje powiązanie danych.  
  
  
<a name="what_is_data_binding"></a>   
## <a name="what-is-data-binding"></a>Co to jest wiązanie danych?  
 Powiązanie danych to proces, który nawiązuje połączenie między aplikacją [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] i logiki biznesowej. Jeśli wiązanie ma poprawne ustawienia i dane zapewnia właściwe powiadomienia, następnie, po zmianie danych jego wartości, elementy, które są powiązane z danymi odzwierciedlać zmiany, automatycznie. Powiązanie danych również może oznaczać, że jeśli zmieni się zewnętrznej reprezentacji danych w elemencie danych bazowych można automatycznie zaktualizowane w celu odzwierciedlenia zmiany. Na przykład, jeśli użytkownik edytuje wartość <xref:System.Windows.Controls.TextBox> elementu podstawową wartość danych jest automatycznie aktualizowana w celu odzwierciedlenia tej zmiany.  
  
 Typowym zastosowaniem wiązanie danych jest umieszczenie serwera lub dane konfiguracji lokalnej do formularzy i innych [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] kontrolki. W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], takie podejście jest rozwinięta i obejmuje powiązanie szerokiej gamy właściwości do różnych źródeł danych. W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], można powiązać właściwości zależności elementów [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] obiektów (w tym [!INCLUDE[TLA#tla_adonet](../../../../includes/tlasharptla-adonet-md.md)] obiektów lub obiekty skojarzone z właściwości sieci Web i usług sieci Web) i [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] danych.  
  
 Na przykład powiązanie danych zapoznaj się z następującej aplikacji [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] z [pokaz powiązania danych](https://go.microsoft.com/fwlink/?LinkID=163703):  
  
 ![Zrzut ekranu przedstawiający przykładowe powiązania danych](../../../../docs/framework/wpf/data/media/databinding-databindingdemo.png "DataBinding_DataBindingDemo")  
  
 Powyższa procedura jest [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] aplikacji, która wyświetla listę licytacją. Aplikacja ilustruje następujące funkcje powiązanie danych:  
  
-   Zawartość <xref:System.Windows.Controls.ListBox> jest powiązana z kolekcją *AuctionItem* obiektów. *AuctionItem* obiekt ma właściwości *opis*, *StartPrice*, *StartDate*, *kategorii*, *SpecialFeatures*itp.  
  
-   Dane (*AuctionItem* obiektów) wyświetlanych w <xref:System.Windows.Controls.ListBox> jest oparte na szablonach, aby pokazać opis i bieżąca cena dla każdego elementu. Odbywa się przy użyciu <xref:System.Windows.DataTemplate>. Ponadto wygląd każdego elementu zależy od *SpecialFeatures* wartość *AuctionItem* są wyświetlane. Jeśli *SpecialFeatures* wartość *AuctionItem* jest *kolor*, element posiada niebieskim obramowaniem. Jeśli wartość jest *wyróżnić*, element posiada pomarańczowe krawędzie i gwiazdkę. [Szablonowanie danych](#data_templating) sekcja zawiera informacje dotyczące tworzenia szablonów danych.  
  
-   Użytkownik może grupy, filtrowania lub sortowania danych przy użyciu <xref:System.Windows.Controls.CheckBox>es podane. Na ilustracji powyżej, "Grupuj według kategorii" i "Sortuj według kategorii i daty" <xref:System.Windows.Controls.CheckBox>es są zaznaczone. Być może zauważono, że dane są pogrupowane w oparciu o kategorię lub produkt, a nazwa kategorii jest w porządku alfabetycznym. Jest trudne, należy zwrócić uwagę na podstawie obrazu, ale elementy są również sortowane według daty rozpoczęcia w ramach każdej kategorii. Odbywa się przy użyciu *widok kolekcji*. [Powiązanie z kolekcjami](#binding_to_collections) sekcji omówiono widoki kolekcji.  
  
-   Gdy użytkownik wybierze element <xref:System.Windows.Controls.ContentControl> Wyświetla szczegóły wybranego elementu. Jest to nazywane *scenariuszu wzorzec / szczegół*. [Scenariuszu wzorzec / szczegół](#master_detail_scenario) sekcja zawiera informacje dotyczące tego rodzaju scenariusza powiązania.  
  
-   Typ *StartDate* właściwość <xref:System.DateTime>, która zwraca datę, która zawiera czas potrzebny do milisekundy. W tej aplikacji niestandardowych konwertera została użyta, aby były wyświetlane krótszy ciąg daty. [Konwersja danych](#data_conversion) sekcja zawiera informacje o konwerterów.  
  
 Kiedy użytkownik kliknie *Dodaj produkt* przycisku funkcjonuje następującą postać:  
  
 ![Strona dodawania listy produktów](../../../../docs/framework/wpf/data/media/databinding-demo-addproductlisting.png "DataBinding_Demo_AddProductListing")  
  
 Użytkownik może edytować pola w formularzu, lista produktów, przy użyciu (krótka wersja zapoznawcza) i uzyskać bardziej szczegółowy okienka (wersja zapoznawcza) w wersji zapoznawczej, a następnie kliknij *przesłać* Aby dodać nową listę produktów. Wszelkie istniejące grupowanie, filtrowanie i sortowanie funkcje będą dotyczyć nowy wpis. W tym przypadku element, który został wprowadzony na powyższym obrazie będą wyświetlane jako drugi element w obrębie *komputera* kategorii.  
  
 Nie są wyświetlane na tej ilustracji jest logikę weryfikacji w *Data rozpoczęcia* <xref:System.Windows.Controls.TextBox>. Jeśli użytkownik wprowadzi nieprawidłowe Data (nieprawidłowe formatowanie lub datę przeszłą), użytkownik będzie powiadamiany z <xref:System.Windows.Controls.ToolTip> oraz czerwonego wykrzyknika obok <xref:System.Windows.Controls.TextBox>. [Sprawdzanie poprawności danych](#data_validation) sekcji omówiono sposób tworzenia logikę weryfikacji.  
  
 Przed przejściem do różnych funkcji wiązania danych opisanych powyżej, najpierw omówimy w następnej sekcji podstawowe pojęcia, które mają kluczowe znaczenie dla zrozumienia [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] powiązanie danych.  
  
## <a name="basic-data-binding-concepts"></a>Pojęcia dotyczące powiązania danych podstawowych  
  
 Niezależnie od tego, jaki element powiązania i rodzaj źródła danych każdego powiązania zawsze korzysta z modelu zilustrowane na poniższym rysunku:  
  
 ![Diagram podstawowego powiązania danych](../../../../docs/framework/wpf/data/media/databindingmostbasic.png "DataBindingMostBasic")  
  
 Jak pokazano na rysunku powyżej, wiązanie danych jest zasadniczo Most między urządzenie docelowe powiązania i źródła powiązania. Rysunek przedstawia następujące podstawowe [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] koncepcji powiązań danych:  
  
-   Zazwyczaj każde powiązanie ma te cztery składniki: powiązanie obiektu docelowego, właściwość docelowa, źródło wiążące i ścieżkę do wartości w źródle powiązania do użycia. Na przykład, jeśli chcesz powiązać zawartość <xref:System.Windows.Controls.TextBox> do *nazwa* właściwość *pracowników* obiektu, obiekt docelowy jest <xref:System.Windows.Controls.TextBox>, właściwość docelowa jest <xref:System.Windows.Controls.TextBox.Text%2A> Właściwość, jest wartość używaną *nazwa*, oraz obiekt źródłowy jest *pracowników* obiektu.  
  
-   Właściwość docelowa musi być właściwość zależności. Większość <xref:System.Windows.UIElement> właściwości są właściwości zależności i większość właściwości zależności, z wyjątkiem sieci tylko do odczytu, obsługuje powiązanie danych domyślnie. (Tylko <xref:System.Windows.DependencyObject> typów można zdefiniować właściwości zależności i wszystkie <xref:System.Windows.UIElement>s pochodzić od <xref:System.Windows.DependencyObject>.)  
  
-   Chociaż nie jest określony na rysunku, należy zauważyć, obiektu źródłowego powiązania nie jest ograniczony do bycia niestandardowego [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] obiektu. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Powiązanie danych obsługuje dane w postaci [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] obiektów i [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]. Aby podać kilka przykładów, może być Twoje źródło wiążące <xref:System.Windows.UIElement>, dowolnego obiektu listy [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] obiekt, który jest skojarzony z [!INCLUDE[TLA#tla_adonet](../../../../includes/tlasharptla-adonet-md.md)] danych lub usługi sieci Web lub element XmlNode, który zawiera Twoje [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] danych. Aby uzyskać więcej informacji, zobacz [Przegląd wiązanie źródeł](../../../../docs/framework/wpf/data/binding-sources-overview.md).  
  
 Omówione w innych [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)] tematy, ważne jest, aby pamiętać, że podczas ustanawiania powiązania są powiązania cel wiążący *do* źródło wiążące. Na przykład, jeśli są wyświetlane niektóre podstawowe [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dane w <xref:System.Windows.Controls.ListBox> używanie powiązania danych, której dokonywane jest wiązanie swoje <xref:System.Windows.Controls.ListBox> do [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] danych.  
  
 Aby ustanowić powiązanie, należy użyć <xref:System.Windows.Data.Binding> obiektu. Pozostała część tego tematu omawia wiele pojęć związanych z i niektóre właściwości i użycie <xref:System.Windows.Data.Binding> obiektu.  
  
<a name="direction_of_data_flow"></a>   
### <a name="direction-of-the-data-flow"></a>Kierunek przepływu danych  
 Jak wspomniano wcześniej, a wskazany strzałką na powyższej ilustracji, przepływ danych powiązanie może przejść od wiązanie docelowe w źródle powiązania (na przykład wartość źródłowa zmienia, gdy użytkownik edytuje wartość <xref:System.Windows.Controls.TextBox>) i/lub z źródło wiążące do obiektu docelowego powiązania (na przykład Twoje <xref:System.Windows.Controls.TextBox> zawartości jest aktualizowany ze zmianami w źródle powiązania) Jeśli źródło wiążące udostępnia odpowiednie powiadomienia.  
  
 Możesz chcieć aplikacji w taki sposób, aby użytkownicy mogli zmieniać dane i propagowania go z obiektem źródłowym. Lub może nie chcesz zezwolić użytkownikom na aktualizowanie źródła danych. Możesz to kontrolować przez ustawienie <xref:System.Windows.Data.Binding.Mode%2A> właściwości usługi <xref:System.Windows.Data.Binding> obiektu. Na poniższym rysunku przedstawiono różne rodzaje przepływu danych:  
  
 ![Powiązanie danych przepływu danych](../../../../docs/framework/wpf/data/media/databinding-dataflow.png "DataBinding_DataFlow")  
  
-   <xref:System.Windows.Data.BindingMode.OneWay> Powiązanie powoduje, że zmiany wprowadzone do właściwości źródła do automatycznego aktualizowania właściwość target, ale zmiany wprowadzone do właściwości docelowej nie są propagowane do właściwości source. Ten typ powiązania jest odpowiednie, jeśli formant związany, jest niejawnie tylko do odczytu. Na przykład może powiązać ze źródłem, takich jak giełdowej lub może być Twoje właściwość docelowa nie ma kontroli interfejsu przewidziane do wprowadzania zmian, takich jak kolor tła powiązanych z danymi z tabeli. W przypadku nie trzeba monitorować zmiany właściwości docelowej przy użyciu <xref:System.Windows.Data.BindingMode.OneWay> tryb powiązania eliminuje koszty związane z <xref:System.Windows.Data.BindingMode.TwoWay> tryb wiązania.  
  
-   <xref:System.Windows.Data.BindingMode.TwoWay> Powiązanie powoduje, że zmiany właściwości source lub właściwość target do automatycznego aktualizowania drugiego. Ten typ powiązania jest przeznaczona dla edytowalne formularze i innych pełni interaktywnych [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] scenariuszy. Domyślnie większość właściwości <xref:System.Windows.Data.BindingMode.OneWay> powiązania, ale niektóre właściwości zależności (zazwyczaj właściwości można edytować użytkownika kontrolki, takie jak <xref:System.Windows.Controls.TextBox.Text%2A> właściwość <xref:System.Windows.Controls.TextBox> i <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> właściwość <xref:System.Windows.Controls.CheckBox>) domyślnie <xref:System.Windows.Data.BindingMode.TwoWay> powiązania. Programowy sposób, aby ustalić, czy właściwość zależności wiąże- lub dwukierunkowo domyślnie jest można pobrać metadanych właściwości modelu używając właściwości <xref:System.Windows.DependencyProperty.GetMetadata%2A> , a następnie sprawdź wartość logiczna <xref:System.Windows.FrameworkPropertyMetadata.BindsTwoWayByDefault%2A> właściwości.  
  
-   <xref:System.Windows.Data.BindingMode.OneWayToSource> jest odwrotnej <xref:System.Windows.Data.BindingMode.OneWay> powiązanie; powoduje zaktualizowanie właściwości źródła po zmianie właściwości docelowej. Jeden przykładowy scenariusz jest, jeśli potrzebujesz ponownej oceny wartości źródłowej z [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
-   Nie jest przedstawione na rysunku jest <xref:System.Windows.Data.BindingMode.OneTime> powiązania, co powoduje, że właściwość źródła w celu zainicjowania właściwość target, ale kolejne zmiany propagowanie nie. Oznacza to, że jeśli kontekst danych ulega zmianę lub obiektu w zmiany kontekstu danych, następnie zmiany nie zostaną uwzględnione we właściwości docelowej. Ten typ powiązania jest odpowiednie, jeśli używasz danych gdzie migawką bieżącego stanu jest odpowiednie do użycia lub danych jest naprawdę statyczny. Ten typ powiązania jest również przydatne, jeśli chcesz zainicjować usługi właściwość target o niektórych wartości z właściwości źródła i kontekst danych nie jest znana z wyprzedzeniem. To jest zasadniczo prostsze formą <xref:System.Windows.Data.BindingMode.OneWay> powiązania, który zapewnia lepszą wydajność w przypadkach, w którym nie zmienia wartość źródła.  
  
 Należy pamiętać, że aby wykryć zmiany źródłowego (dotyczy <xref:System.Windows.Data.BindingMode.OneWay> i <xref:System.Windows.Data.BindingMode.TwoWay> powiązania), źródło musi zaimplementować mechanizm powiadamiania Zmień odpowiednie właściwości takich jak <xref:System.ComponentModel.INotifyPropertyChanged>. Zobacz [powiadomienie o zmianie właściwości Implementowanie](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md) przykład <xref:System.ComponentModel.INotifyPropertyChanged> implementacji.  
  
 <xref:System.Windows.Data.Binding.Mode%2A> Strona właściwości zawiera więcej informacji na temat trybów i przykład sposobu określania kierunku powiązania.  
  
<a name="what_triggers_source_updates"></a>   
### <a name="what-triggers-source-updates"></a>Wyzwalacze źródła aktualizacji  
 Powiązania, które są <xref:System.Windows.Data.BindingMode.TwoWay> lub <xref:System.Windows.Data.BindingMode.OneWayToSource> nasłuchiwania zmian we właściwości docelowej i propagowania ich do źródła. Jest to nazywane aktualizowania źródła. Na przykład może edytować tekst pola tekstowego, aby zmienić wartość bazowego źródła. Zgodnie z opisem w ostatniej sekcji, kierunek przepływu danych jest określana przez wartość <xref:System.Windows.Data.Binding.Mode%2A> właściwości powiązania.  
  
 Jednak wartość źródła aktualizowany podczas edytowania tekstu lub po Zakończ edycję tekstu i wskaż przy użyciu myszy poza pole tekstowe? <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> Właściwości powiązania Określa, co wyzwala aktualizacji źródła. Kropki prawo strzałki na poniższej ilustracji ilustrują rolę <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> właściwości:  
  
 ![Diagram obiektu UpdateSourceTrigger](../../../../docs/framework/wpf/data/media/databindingupdatesourcetrigger.png "DataBindingUpdateSourceTrigger")  
  
 Jeśli <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> wartość <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>, następnie wartość wskazywana przez strzałki w prawo działania <xref:System.Windows.Data.BindingMode.TwoWay> lub <xref:System.Windows.Data.BindingMode.OneWayToSource> powiązania jest aktualizowany tak szybko, jak zmiany właściwości docelowej. Jednak jeśli <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> wartość <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>, a następnie ta wartość tylko jest aktualizowany przy użyciu nowej wartości po utracie fokusu przez właściwość docelowa.  
  
 Podobnie jak <xref:System.Windows.Data.Binding.Mode%2A> właściwości zależności różne właściwości mają różne domyślne <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> wartości. Jest wartością domyślną dla większości właściwości zależności <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>, podczas gdy <xref:System.Windows.Controls.TextBox.Text%2A> właściwość ma wartość domyślną <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>. Oznacza to, że aktualizacji źródła zwykle się zdarzyć, gdy zmiany właściwości docelowych, które jest dobrym rozwiązaniem dla <xref:System.Windows.Controls.CheckBox>es i innymi prostych kontrolek. Jednak dla pól tekstowych aktualizacji po każdym naciśnięciu klawisza może obniżyć wydajność i wyklucza zwykle możliwość backspace i naprawić błędy przed zatwierdzeniem na nową wartość. Dlatego <xref:System.Windows.Controls.TextBox.Text%2A> właściwość ma wartość domyślną <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus> zamiast <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.  
  
 Zobacz <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> stronę właściwości dla informacji o sposobach znajdowania domyślnie <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> wartość właściwości zależności.  
  
 W poniższej tabeli przedstawiono przykładowy scenariusz dla każdego <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> wartości przy użyciu <xref:System.Windows.Controls.TextBox> jako przykładu:  
  
|Wartość obiektu UpdateSourceTrigger|Jeśli wartości źródłowej jest aktualizowany|Przykładowy scenariusz TextBox|  
|-------------------------------|----------------------------------------|----------------------------------|  
|LostFocus (domyślne dla <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType>)|Gdy formant pola tekstowego traci fokus|A <xref:System.Windows.Controls.TextBox> skojarzonego z logikę weryfikacji (patrz sekcja sprawdzanie poprawności danych)|  
|PropertyChanged|Podczas wpisywania w <xref:System.Windows.Controls.TextBox>|<xref:System.Windows.Controls.TextBox> kontrolki w oknie pokoju rozmów|  
|jawne|Gdy aplikacja wywołuje <xref:System.Windows.Data.BindingExpression.UpdateSource%2A>|<xref:System.Windows.Controls.TextBox> formanty w formularzu edycji (aktualizuje wartości źródła tylko wtedy, gdy użytkownik kliknie przycisk przesyłania)|  
  
 Aby uzyskać przykład, zobacz [kontrolować kiedy tekst TextBox aktualizuje źródło](../../../../docs/framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md).  
  
<a name="creating_a_binding"></a>   
## <a name="creating-a-binding"></a>Tworzenie powiązania  
  
 Aby recapitulate niektóre kwestie omówione w poprzednich sekcjach, jest nawiązywane przy użyciu powiązania <xref:System.Windows.Data.Binding> obiektu i zazwyczaj każdego powiązania ma cztery składniki: powiązanie docelowego, właściwość docelowa, źródło wiążące i ścieżki do źródła wartości do użycia. W tej sekcji omówiono sposób konfigurowania powiązania.  
  
 Rozważmy następujący przykład, w którym obiektu źródłowego powiązania jest klasę o nazwie *MyData* zdefiniowanego w *SDKSample* przestrzeni nazw. Dla celów demonstracyjnych *MyData* klasa ma właściwość ciągu o nazwie *ColorName*, z którego wartość jest równa "Red". W związku z tym ten przykład generuje przycisk z czerwonym tle.  
  
 [!code-xaml[BindNonTextProperty#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindNonTextProperty/CS/Page1.xaml#1)]  
  
 Aby uzyskać szczegółowe informacje na temat składni deklaracji powiązania i przykłady sposobu konfigurowania powiązania w kodzie, zobacz [powiązanie deklaracji — omówienie](../../../../docs/framework/wpf/data/binding-declarations-overview.md).  
  
 Jeśli zastosujemy w tym przykładzie do naszych diagram podstawowy, wynikowy ilustracja wygląda podobnie do poniższego. Jest to <xref:System.Windows.Data.BindingMode.OneWay> powiązania, ponieważ właściwość tła obsługuje <xref:System.Windows.Data.BindingMode.OneWay> powiązanie domyślnie.  
  
 ![Diagram powiązania danych](../../../../docs/framework/wpf/data/media/databindingbuttonbackgroundexample.png "DataBindingButtonBackgroundExample")  
  
 Możesz się zastanawiać, dlaczego to działa, nawet jeśli *ColorName* właściwość jest typu String podczas <xref:System.Windows.Controls.Control.Background%2A> właściwość jest typu <xref:System.Windows.Media.Brush>. To jest domyślne konwersji typów w miejscu pracy i został omówiony w [Konwersja danych](#data_conversion) sekcji.  
  
<a name="specifying_the_binding_source"></a>   
### <a name="specifying-the-binding-source"></a>Określanie źródła powiązania  
 Należy zauważyć, że w poprzednim przykładzie źródło powiązania jest określany przez ustawienie <xref:System.Windows.FrameworkElement.DataContext%2A> właściwość <xref:System.Windows.Controls.DockPanel> elementu. <xref:System.Windows.Controls.Button> Następnie dziedziczy <xref:System.Windows.FrameworkElement.DataContext%2A> wartość z <xref:System.Windows.Controls.DockPanel>, który jest elementem nadrzędnym elementu. Przypomnę obiektu źródłowego powiązania jest jedną z czterech niezbędne składniki powiązania. W związku z tym bez określania obiektu źródłowego powiązania powiązanie będzie nic nie rób.  
  
 Istnieje kilka sposobów na określenie obiektu źródłowego powiązania. Za pomocą <xref:System.Windows.FrameworkElement.DataContext%2A> właściwości elementu nadrzędnego jest przydatne w przypadku, gdy wiele właściwości są powiązania z tym samym źródłem. Jednak czasami może być bardziej odpowiednie określić źródło wiążące na poszczególnych powiązanie deklaracji. W poprzednim przykładzie, zamiast <xref:System.Windows.FrameworkElement.DataContext%2A> właściwości, można określić źródło wiążące, ustawiając <xref:System.Windows.Data.Binding.Source%2A> właściwość bezpośrednio w deklaracji powiązania przycisku, jak w poniższym przykładzie:  
  
 [!code-xaml[BindNonTextProperty#BackgroundBindingCompact](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindNonTextProperty/CS/Page2.xaml#backgroundbindingcompact)]  
  
 Inne niż ustawienie <xref:System.Windows.FrameworkElement.DataContext%2A> właściwości w elemencie bezpośrednio, dziedziczenie <xref:System.Windows.FrameworkElement.DataContext%2A> wartość z elementem nadrzędnym (na przykład przycisk w pierwszym przykładzie), a jawnym określaniem źródło powiązania, ustawiając <xref:System.Windows.Data.Binding.Source%2A> właściwość <xref:System.Windows.Data.Binding> (na przykład przycisk ostatnim przykładzie), można również użyć <xref:System.Windows.Data.Binding.ElementName%2A> właściwości lub <xref:System.Windows.Data.Binding.RelativeSource%2A> właściwość, aby określić źródło wiążące. <xref:System.Windows.Data.Binding.ElementName%2A> Właściwość jest przydatna podczas tworzenia wiązania do innych elementów w aplikacji, takich jak w przypadku korzystania suwaka Szerokość przycisku. <xref:System.Windows.Data.Binding.RelativeSource%2A> Właściwość jest przydatna, gdy określono powiązanie w <xref:System.Windows.Controls.ControlTemplate> lub <xref:System.Windows.Style>. Aby uzyskać więcej informacji, zobacz [określić źródło wiążące](../../../../docs/framework/wpf/data/how-to-specify-the-binding-source.md).  
  
<a name="specifying_the_path_to_the_value"></a>   
### <a name="specifying-the-path-to-the-value"></a>Określanie ścieżki do wartości  
 Jeśli Twoje źródło powiązania jest obiektem, możesz użyć <xref:System.Windows.Data.Binding.Path%2A> właściwości w celu określenia wartości dla wiązania. Jeśli dokonywane jest wiązanie [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] danych, możesz użyć <xref:System.Windows.Data.Binding.XPath%2A> właściwości w celu określenia wartości. W niektórych przypadkach może być stosowane do użycia <xref:System.Windows.Data.Binding.Path%2A> właściwość nawet wtedy, gdy dane są [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]. Na przykład jeśli chcesz uzyskać dostęp właściwości Name obiektu zwróconego XmlNode (w wyniku kwerendy XPath), należy użyć <xref:System.Windows.Data.Binding.Path%2A> właściwość oprócz <xref:System.Windows.Data.Binding.XPath%2A> właściwości.  
  
 Aby uzyskać informacje o składni i przykłady, zobacz <xref:System.Windows.Data.Binding.Path%2A> i <xref:System.Windows.Data.Binding.XPath%2A> strony właściwości.  
  
 Należy zauważyć, że firma Microsoft ma zostać, <xref:System.Windows.Data.Binding.Path%2A> z wartością w celu użycia jednej z czterech wymagane składniki klasy powiązanie, w scenariuszach, które chcesz powiązać z całego obiektu, wartość używana będzie taka sama jak obiektu źródłowego powiązania. W takich przypadkach jest stosowane, aby nie określać <xref:System.Windows.Data.Binding.Path%2A>. Rozważmy następujący przykład:  
  
 [!code-xaml[MasterDetail#EmptyBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MasterDetail/CSharp/Page1.xaml#emptybinding)]  
  
 Powyższy przykład używa składni powiązania pusty: {Binding}. W tym przypadku <xref:System.Windows.Controls.ListBox> dziedziczy kontekstu danych elementu DockPanel nadrzędnej (nie pokazane w tym przykładzie). Jeśli ścieżka nie zostanie określony, wartość domyślna to, aby powiązać cały obiekt. Innymi słowy, w tym przykładzie ścieżki została pozostawiona się, ponieważ firma Microsoft dokonywane jest wiązanie <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> właściwości do całego obiektu. (Zobacz [powiązanie z kolekcjami](#binding_to_collections) sekcja zawiera szczegółowe omówienie.)  
  
 Inne niż powiązanie do kolekcji, w tym scenariuszu jest również przydatne powiązać cały obiekt zamiast pojedynczej właściwości obiektu. Na przykład jeśli obiekt źródłowy jest typu ciąg i po prostu chcesz powiązać sam ciąg. Innym typowym scenariuszem jest, gdy chcesz powiązać element do obiektu z wieloma właściwościami.  
  
 Należy pamiętać, że może być konieczne stosowanie logiki niestandardowej tak, aby dane były zrozumiałe dla z powiązanej własności docelowej. Niestandardowej logiki może być w formie konwertera niestandardowych (Jeśli nie ma domyślnej konwersji typów). Zobacz [Konwersja danych](#data_conversion) uzyskać informacji na temat konwerterów.  
  
<a name="binding_bindingexpression"></a>   
### <a name="binding-and-bindingexpression"></a>Powiązanie i BindingExpression  
 Przed przejściem do innych funkcjach i użycia powiązania danych, powinien być przydatny dla wprowadzają <xref:System.Windows.Data.BindingExpression> klasy. Ponieważ jak już wspomniano w poprzednich sekcjach <xref:System.Windows.Data.Binding> klasa jest klasą wysokiego poziomu dla deklaracji powiązania; <xref:System.Windows.Data.Binding> klasy zawiera wiele właściwości, które pozwalają na określenie właściwości powiązania. Klasy pokrewne, <xref:System.Windows.Data.BindingExpression>, jest to podstawowy obiekt, który umożliwia utrzymywanie połączenia między źródłowym a docelowym. Powiązanie zawiera wszystkie informacje, które mogą być współużytkowane przez kilka wyrażenia wiązania. A <xref:System.Windows.Data.BindingExpression> jest wyrażenie wystąpienia, które nie mogą być udostępniane i zawiera wszystkie wystąpienia informacje <xref:System.Windows.Data.Binding>.  
  
 Rozważmy na przykład następujące polecenie, gdzie *myDataObject* jest wystąpieniem *MyData* klasy *myBinding* jest źródłem <xref:System.Windows.Data.Binding> obiektu i *MyData* klasa jest zdefiniowana klasa, która zawiera właściwości ciągu o nazwie *MyDataProperty*. W tym przykładzie jest powiązana zawartość tekstu *kwerend*, wystąpienie <xref:System.Windows.Controls.TextBlock>, *MyDataProperty*.  
  
 [!code-csharp[CodeOnlyBinding#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#1)]
 [!code-vb[CodeOnlyBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#1)]  
  
 Można używać tego samego *myBinding* obiekt, aby utworzyć inne powiązania. Na przykład, może użyć *myBinding* obiektu zawartości tekstowej pole wyboru, aby powiązać *MyDataProperty*. W tym scenariuszu będą dwa wystąpienia <xref:System.Windows.Data.BindingExpression> udostępnianie *myBinding* obiektu.  
  
 A <xref:System.Windows.Data.BindingExpression> obiektu można uzyskać przez wartość zwracaną przez wywołanie <xref:System.Windows.Data.BindingOperations.GetBindingExpression%2A> w obiekcie powiązanym z danymi. W poniższych tematach pokazano niektóre sposoby użycia <xref:System.Windows.Data.BindingExpression> klasy:  
  
-   [Pobieranie obiektu wiążącego z powiązanej własności docelowej](../../../../docs/framework/wpf/data/how-to-get-the-binding-object-from-a-bound-target-property.md)  
  
-   [Kontrolowanie momentu aktualizowania źródła tekstu kontrolki TextBox](../../../../docs/framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md)  
  
<a name="data_conversion"></a>   
## <a name="data-conversion"></a>Konwersja danych  
 W poprzednim przykładzie ma kolor czerwony przycisk ponieważ jej <xref:System.Windows.Controls.Control.Background%2A> właściwość jest powiązana z właściwością ciągu z wartością "Red". To działa, ponieważ konwertera typów znajduje się na <xref:System.Windows.Media.Brush> typu można przekonwertować na wartość ciągu <xref:System.Windows.Media.Brush>.  
  
 Aby dodać te informacje do rysunku w [tworzenia powiązania](#creating_a_binding) sekcji diagramu wygląda podobnie do następującej:  
  
 ![Diagram powiązania danych](../../../../docs/framework/wpf/data/media/databindingbuttondefaultconversion.png "DataBindingButtonDefaultConversion")  
  
 Jednakże, co się stanie, jeśli zamiast właściwość typu String obiektu źródłowego powiązania ma *kolor* właściwości typu <xref:System.Windows.Media.Color>? W takim przypadku w kolejności dla powiązania do pracy będziesz potrzebować do pierwszego Włącz *kolor* wartość właściwości na coś, <xref:System.Windows.Controls.Control.Background%2A> właściwość przyjmuje. Będziesz potrzebować do tworzenia niestandardowych konwerter implementując <xref:System.Windows.Data.IValueConverter> interfejsu, jak w poniższym przykładzie:  
  
 [!code-csharp[ColorPicker_snip#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ColorPicker_snip/CSharp/ColorPickerLib/ColorPicker.cs#16)]
 [!code-vb[ColorPicker_snip#16](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ColorPicker_snip/visualbasic/colorpickerlib/colorpicker.vb#16)]  
  
 <xref:System.Windows.Data.IValueConverter> Strona referencyjna zawiera więcej informacji.  
  
 Teraz konwerter niestandardowy jest używany zamiast domyślnej konwersji, a nasze diagram wygląda następująco:  
  
 ![Diagram powiązania danych](../../../../docs/framework/wpf/data/media/databindingconvertercolorexample.png "DataBindingConverterColorExample")  
  
 Do przypomnę konwersje domyślne mogą być dostępne ze względu na konwertery typu, które znajdują się w typie związania z. To zachowanie będzie zależeć od konwerterów typów, które są dostępne w elemencie docelowym. W razie wątpliwości należy utworzyć własny konwertera.  
  
 Poniżej przedstawiono niektóre typowe scenariusze, w których warto wdrożyć konwertera danych:  
  
-   Dane powinny być wyświetlane w różny sposób, w zależności od kultury. Na przykład można zaimplementować Konwerter waluty lub kalendarza konwertera daty/godziny na podstawie wartości lub norm stosowanych w danej kultury.  
  
-   Dane używane nie ma zawsze można zmienić wartości tekstowej, właściwości, ale zamiast tego jest przeznaczone do zmiany innej wartości, takie jak źródło dla obrazu, lub kolor lub style tekstu. Konwertery może służyć w tym wystąpieniu konwertując powiązania właściwości, które nie mogą wydawać się odpowiednie, na przykład powiązanie pole tekstowe do właściwości tła komórek tabeli.  
  
-   Więcej niż jeden formant lub na wiele właściwości kontrolki są powiązane z tych samych danych. W tym przypadku powiązania podstawowy może być wyświetlają tylko tekst, pozostałych powiązaniach obsługi problemów z wyświetlaniem określonych, ale nadal używać tego samego powiązania jako źródła informacji.  
  
-   Do tej pory nie jeszcze Omówiliśmy <xref:System.Windows.Data.MultiBinding>, której właściwość docelowa ma kolekcję powiązań. W przypadku właściwości <xref:System.Windows.Data.MultiBinding>, używać niestandardowego <xref:System.Windows.Data.IMultiValueConverter> utworzenia końcowej wartości z wartości wiązania. Na przykład kolor mogą być obliczone wartości czerwony, niebieski i zielony, co może mieć wartości z tych samych lub różnych powiązania obiekty źródła. Zobacz <xref:System.Windows.Data.MultiBinding> klasy strony, przykłady i informacje.  
  
<a name="binding_to_collections"></a>   
## <a name="binding-to-collections"></a>Powiązanie z kolekcjami  
  
 Obiekt źródłowy powiązań mogą być traktowane jako pojedynczy obiekt, którego właściwości zawierają dane lub kolekcji danych polimorficznych obiektów, które są często grupowane razem (np. wynik zapytania do bazy danych). Do tej pory tylko Wiemy już powiązania do pojedynczych obiektów, jednak jest to typowy scenariusz w powiązania do zbierania danych. Na przykład typowym scenariuszem jest użycie <xref:System.Windows.Controls.ItemsControl> takich jak <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.ListView>, lub <xref:System.Windows.Controls.TreeView> do wyświetlenia zbierania danych, takie jak w aplikacji w [co to jest powiązanie danych?](#what_is_data_binding) sekcji.  
  
 Na szczęście naszych diagram podstawowy nadal istnieje. Jeśli dokonywane jest wiązanie <xref:System.Windows.Controls.ItemsControl> do kolekcji, diagram wygląda następująco:  
  
 ![Powiązanie danych elementu ItemsControl diagram](../../../../docs/framework/wpf/data/media/databindingitemscontrol.png "DataBindingItemsControl")  
  
 Jak pokazano na poniższym diagramie można powiązać <xref:System.Windows.Controls.ItemsControl> do obiektu kolekcji <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> właściwość jest właściwością do użycia. Można potraktować <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> właściwość jako zawartość <xref:System.Windows.Controls.ItemsControl>. Należy zauważyć, że powiązanie <xref:System.Windows.Data.BindingMode.OneWay> ponieważ <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> obsługuje właściwość <xref:System.Windows.Data.BindingMode.OneWay> powiązanie domyślnie.  
  
<a name="how_to_implement_collections"></a>   
### <a name="how-to-implement-collections"></a>Jak zaimplementować kolekcji  
 Można wyliczyć za pośrednictwem kolekcji, która implementuje <xref:System.Collections.IEnumerable> interfejsu. Jednak aby skonfigurować dynamiczne powiązania tak, aby zaktualizować wstawienia i usunięcia w kolekcji [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] automatycznie, Kolekcja musi implementować <xref:System.Collections.Specialized.INotifyCollectionChanged> interfejsu. Ten interfejs przedstawia zdarzenie, które powinien być wywoływany w każdym przypadku, gdy zmienia się kolekcja bazowego.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia <xref:System.Collections.ObjectModel.ObservableCollection%601> klasy, która jest wbudowana implementacji zbierania danych, która udostępnia <xref:System.Collections.Specialized.INotifyCollectionChanged> interfejsu. Należy pamiętać, że do zapewnienia pełnej obsługi przesyłania wartości z obiekty źródła danych do celów, każdy obiekt w kolekcji, obsługującej właściwości możliwej do wiązania musi implementować też <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu. Aby uzyskać więcej informacji, zobacz [Przegląd wiązanie źródeł](../../../../docs/framework/wpf/data/binding-sources-overview.md).  
  
 Przed wdrożeniem własną kolekcję, należy wziąć pod uwagę przy użyciu <xref:System.Collections.ObjectModel.ObservableCollection%601> lub jeden z istniejących kolekcji klasy takie jak <xref:System.Collections.Generic.List%601>, <xref:System.Collections.ObjectModel.Collection%601>, i <xref:System.ComponentModel.BindingList%601>, wiele innych. Jeśli masz zaawansowanego scenariusza i zaimplementować własną kolekcję, rozważ użycie <xref:System.Collections.IList>, która zapewnia nieogólna kolekcja obiektów, które mogą być indywidualnie udostępniane przez indeks i w związku z tym najlepszą wydajność.  
  
<a name="collection_views"></a>   
### <a name="collection-views"></a>Widoki kolekcji  
 Raz swoje <xref:System.Windows.Controls.ItemsControl> jest powiązany do zbierania danych, możesz chcieć sortowanie, filtrowanie lub grupy danych. Aby to zrobić, użyj widoków kolekcji, które są klasami, które implementują <xref:System.ComponentModel.ICollectionView> interfejsu.  
  
  
#### <a name="what-are-collection-views"></a>Co to są widoki kolekcji?  
 Widok kolekcji jest warstwą powiązania kolekcji źródłowej, która pozwala na nawigacji i wyświetlania kolekcji źródłowej, na podstawie sortowania, filtrowania i grupy zapytań, bez konieczności zmiany podstawowego kolekcji źródłowej, sam. Widok kolekcji przechowuje także wskaźnik do bieżącego elementu w kolekcji. Jeśli kolekcja źródłowa implementuje <xref:System.Collections.Specialized.INotifyCollectionChanged> interfejsu zmiany wygenerowane przez <xref:System.Collections.Specialized.INotifyCollectionChanged.CollectionChanged> zdarzeń są propagowane do widoków.  
  
 Ponieważ widoki nie zmieniaj podstawowej kolekcji źródłowej, każda kolekcja źródłowa może mieć wiele widoków skojarzonych z nim. Na przykład masz kolekcję *zadań* obiektów. Przy użyciu widoków możesz wyświetlić tych samych danych na różne sposoby. Na przykład w lewej części strony usługi można wyświetlić zadania, posortowane według priorytetu, a po prawej stronie, pogrupowane według obszaru.  
  
<a name="how_to_create_a_view"></a>   
#### <a name="how-to-create-a-view"></a>Jak utworzyć widok  
 Jednym ze sposobów tworzenia i używania widoku jest bezpośrednie tworzenie wystąpień obiektów widoku, a następnie użyć go jako źródło wiążące. Na przykład, rozważmy [powiązanie danych w wersji demonstracyjnej](https://go.microsoft.com/fwlink/?LinkID=163703) aplikacji pokazanej na [co to jest powiązanie danych?](#what_is_data_binding) sekcji. Aplikacja została zaimplementowana tak, aby <xref:System.Windows.Controls.ListBox> wiąże widok nad kolekcją danych, zamiast zbieranie danych bezpośrednio. Poniższy przykład są wyodrębniane z [powiązanie danych w wersji demonstracyjnej](https://go.microsoft.com/fwlink/?LinkID=163703) aplikacji. <xref:System.Windows.Data.CollectionViewSource> Klasa jest [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] serwera proxy, który dziedziczy z klasy <xref:System.Windows.Data.CollectionView>. W tym konkretnym przykładzie <xref:System.Windows.Data.CollectionViewSource.Source%2A> widoku jest powiązany z *AuctionItems* kolekcji (typu <xref:System.Collections.ObjectModel.ObservableCollection%601>) bieżącego obiektu aplikacji.  
  
 [!code-xaml[DataBindingLab#WindowResources1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#windowresources1)]  
[!code-xaml[DataBindingLab#CollectionViewSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#collectionviewsource)]  
[!code-xaml[DataBindingLab#WindowResources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#windowresources2)]  
  
 Zasób *listingDataView* następnie służy jako źródło wiążące dla elementów w aplikacji, takich jak <xref:System.Windows.Controls.ListBox>:  
  
 [!code-xaml[DataBindingLab#Master1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master1)]  
[!code-xaml[DataBindingLab#Master2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master2)]  
  
 Aby utworzyć inny widok dla tej samej kolekcji, należy utworzyć inny <xref:System.Windows.Data.CollectionViewSource> wystąpienia i nadać mu inną `x:Key` nazwy.  
  
 W poniższej tabeli przedstawiono typy danych Widok są tworzone jako domyślny widok kolekcji lub przez <xref:System.Windows.Data.CollectionViewSource> na podstawie typu kolekcji źródłowej.  
  
|Typ kolekcji źródłowej|Typ widoku kolekcji|Uwagi|  
|----------------------------|--------------------------|-----------|  
|<xref:System.Collections.IEnumerable>|Wewnętrzny typ, na podstawie <xref:System.Windows.Data.CollectionView>|Nie można grupować elementy.|  
|<xref:System.Collections.IList>|<xref:System.Windows.Data.ListCollectionView>|Najszybszy.|  
|<xref:System.ComponentModel.IBindingList>|<xref:System.Windows.Data.BindingListCollectionView>||  
  
##### <a name="using-a-default-view"></a>Przy użyciu widoku domyślnego  
 Określanie widoku kolekcji jako źródło powiązania jest jednym ze sposobów tworzenia i używania widoku kolekcji. WPF tworzy również domyślny widok kolekcji dla każdej kolekcji, używane jako źródło wiążące. Jeżeli powiążesz bezpośrednio do kolekcji WPF wiąże się do widoku domyślnego. Należy pamiętać, że ten widok domyślny jest współużytkowany przez wszystkie powiązania z tej samej kolekcji, więc wprowadzona zmiana w widoku domyślnego według jedną kontrolkę powiązanej lub kodu (na przykład sortowania lub zmień bieżący wskaźnik elementów, omówiono w dalszej części) jest widoczny w pozostałych powiązaniach do tej samej kolekcji.  
  
 Aby uzyskać widok domyślny, należy użyć <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> metody. Aby uzyskać przykład, zobacz [widok domyślny zbiór danych](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md).  
  
##### <a name="collection-views-with-adonet-datatables"></a>Widoki kolekcji z tabel danych ADO.NET  
 Aby zwiększyć wydajność, Kolekcja widoków dla ADO.NET <xref:System.Data.DataTable> lub <xref:System.Data.DataView> obiektów delegowanie, sortowanie i filtrowanie <xref:System.Data.DataView>. Powoduje to, sortowanie i filtrowanie, aby być współużytkowane przez wszystkie widoki kolekcji źródła danych. Aby włączyć każdego widoku kolekcji do sortowania i filtrowania niezależnie, zainicjować każdego widoku kolekcji za pomocą własnego <xref:System.Data.DataView> obiektu.  
  
#### <a name="sorting"></a>Sortowanie  
 Jak wspomniano wcześniej, widoki, można zastosować kolejność sortowania w kolekcji. Zgodnie z jego lokalizacją w źródłowej kolekcji danych może być lub może nie mieć kolejności istotne, nieprzerwaną pracę. Widok nad kolekcją umożliwia nakłada zamówienie lub zmienić domyślną kolejność, w oparciu o kryteria porównania, które należy podać. Ponieważ jest oparte na kliencie widok danych, typowym scenariuszem jest, użytkownik może chcieć sortowanie kolumn dane tabelaryczne na wartość, która odpowiada kolumnie. Korzystanie z widoków, tego rodzaju oparte na użytkownika mogą być stosowane, ponownie bez wprowadzania żadnych zmian do podstawowej kolekcji lub nawet do requery zawartości kolekcji. Aby uzyskać przykład, zobacz [sortowania GridView kolumny po kliknięciu nagłówka](../../../../docs/framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md).  
  
 W poniższym przykładzie pokazano sortowania logikę "Sortuj według kategorii i daty" <xref:System.Windows.Controls.CheckBox> aplikacji [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] w [co to jest powiązanie danych?](#what_is_data_binding) sekcji:  
  
 [!code-csharp[DataBindingLab#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#8)]
 [!code-vb[DataBindingLab#8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#8)]  
  
#### <a name="filtering"></a>Filtrowanie  
 Widoki można także zastosować filtr do kolekcji. Oznacza to, że chociaż element może istnieć w kolekcji, tego widoku jest przeznaczona do Pokaż niektórych podzbiorem pełnego. Można filtrować pod warunkiem w danych. Na przykład, jak odbywa się przez aplikację w [co to jest powiązanie danych?](#what_is_data_binding) sekcji "Pokaż tylko okazje" <xref:System.Windows.Controls.CheckBox> zawiera logikę, aby odfiltrować elementy, które koszt 25 USD lub więcej. Poniższy kod jest wykonywany można ustawić *ShowOnlyBargainsFilter* jako <xref:System.Windows.Data.CollectionViewSource.Filter> programu obsługi zdarzeń podczas który <xref:System.Windows.Controls.CheckBox> wybrano:  
  
 [!code-csharp[DataBindingLab#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#10)]
 [!code-vb[DataBindingLab#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#10)]  
  
 *ShowOnlyBargainsFilter* programu obsługi zdarzeń ma następującą implementacją:  
  
 [!code-csharp[DataBindingLab#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#5)]
 [!code-vb[DataBindingLab#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#5)]  
  
 Jeśli używasz jednego z <xref:System.Windows.Data.CollectionView> klasy bezpośrednio zamiast z <xref:System.Windows.Data.CollectionViewSource>, należy użyć <xref:System.Windows.Data.CollectionView.Filter%2A> właściwości w celu określenia wywołania zwrotnego. Aby uzyskać przykład, zobacz [filtrować dane w widoku](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md).  
  
#### <a name="grouping"></a>Grupowanie  
 Z wyjątkiem Klasa wewnętrzna, która wyświetla <xref:System.Collections.IEnumerable> kolekcji, wszystkie widoki kolekcji obsługują funkcje grupowania, co pozwala użytkownikowi na partycje kolekcji w widoku kolekcji w logiczne grupy. Grup można w przypadku, gdy użytkownik podaje listę grup, bezpośrednie lub pośrednie, których grup są generowane dynamicznie w zależności od danych.  
  
 W poniższym przykładzie pokazano logikę "Grupuj według kategorii" <xref:System.Windows.Controls.CheckBox>:  
  
 [!code-csharp[DataBindingLab#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#6)]
 [!code-vb[DataBindingLab#6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#6)]  
  
 Inny przykład grupowania, zobacz [grupy elementy w ListView implementuje czy GridView](../../../../docs/framework/wpf/controls/how-to-group-items-in-a-listview-that-implements-a-gridview.md).  
  
#### <a name="current-item-pointers"></a>Bieżący element wskaźników  
 Widoki obsługują również pojęcie bieżącego elementu. Możesz przejść przez obiekty w widoku kolekcji. Jak przejść, są przenoszone wskaźnika elementu, który pozwala pobrać obiekt, który istnieje w tej lokalizacji określonej w kolekcji. Aby uzyskać przykład, zobacz [przejdź do obiektów w danych CollectionView](../../../../docs/framework/wpf/data/how-to-navigate-through-the-objects-in-a-data-collectionview.md).  
  
 Ponieważ WPF tworzy powiązanie z kolekcji wszystkie powiązania z kolekcji tylko przy użyciu widoku (widok, do którego należy określić albo widoku domyślnego kolekcji), mają wskaźnik bieżącego elementu. Podczas tworzenia wiązania do widoku, ukośnika ("/"), znaków w `Path` wartość wyznacza bieżącego elementu widoku. W poniższym przykładzie kontekst danych jest widokiem kolekcji. Pierwszy wiersz tworzy powiązanie z kolekcji. Drugi wiersz tworzy powiązanie z aktualnym elementem w kolekcji. Trzeci wiersz tworzy powiązanie z `Description` właściwości bieżącego elementu w kolekcji.  
  
```xaml  
<Button Content="{Binding }" />  
<Button Content="{Binding Path=/}" />  
<Button Content="{Binding Path=/Description}" />   
```  
  
 Składnia ułamkową i właściwości mogą być także skumulowany na przechodzenie przez hierarchię kolekcji. Poniższy przykład tworzy powiązanie z aktualnym elementem kolekcję o nazwie `Offices`, który jest właściwością bieżącego elementu kolekcji źródłowej.  
  
```xaml  
<Button Content="{Binding /Offices/}" />  
```  
  
 Bieżący wskaźnik elementów mogą mieć wpływ wszelkie sortowanie lub filtrowanie jest stosowane do kolekcji. Sortowanie zachowuje bieżący wskaźnik elementów na ostatni element wybrany, ale widok kolekcji jest teraz modyfikować danych wokół niej. (Może być zaznaczony element: na początku listy przed, ale obecnie wybranego elementu może być zawarty w środku). Filtrowanie zachowuje wybrany element, jeśli Wybieranie pozostaje w widoku po zakończeniu filtrowania. W przeciwnym razie do pierwszego elementu w widoku filtrowanego kolekcji ustawiono bieżącego wskaźnika elementu.  
  
<a name="master_detail_scenario"></a>   
#### <a name="master-detail-binding-scenario"></a>Scenariusz powiązania wzorzec / szczegół  
 Pojęcie bieżący element jest przydatne, nie tylko dla nawigacji elementów w kolekcji, ale także w scenariuszu wzorzec / szczegół powiązania. Należy wziąć pod uwagę aplikację [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] w [co to jest powiązanie danych?](#what_is_data_binding) sekcji ponownie. W tej aplikacji, wybór w ramach <xref:System.Windows.Controls.ListBox> określa zawartość wyświetlaną na <xref:System.Windows.Controls.ContentControl>. Aby umieścić ją w inny sposób, gdy <xref:System.Windows.Controls.ListBox> element jest wybrany, <xref:System.Windows.Controls.ContentControl> pokazuje szczegóły wybranego elementu.  
  
 Można implementować scenariusza wzorzec / szczegół poprzez posiadanie co najmniej dwóch formanty powiązane z tym samym widoku. Poniższy przykład z [pokaz powiązania danych](https://go.microsoft.com/fwlink/?LinkID=163703) pokazuje oznakowanie <xref:System.Windows.Controls.ListBox> i <xref:System.Windows.Controls.ContentControl> zostanie wyświetlony w aplikacji [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] w [co to jest powiązanie danych?](#what_is_data_binding) sekcji:  
  
 [!code-xaml[DataBindingLab#Master1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master1)]  
[!code-xaml[DataBindingLab#Master2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master2)]  
[!code-xaml[DataBindingLab#Detail](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#detail)]  
  
 Zwróć uwagę, oba formanty są powiązane z tym samym źródłem *listingDataView* zasób statyczny (zobacz definicję tego zasobu w [sposób tworzenia sekcji widoku](#how_to_create_a_view)). To działa, ponieważ gdy pojedynczego obiektu ( <xref:System.Windows.Controls.ContentControl> w tym przypadku) jest powiązany do widoku kolekcji automatycznie powiąże <xref:System.Windows.Data.CollectionView.CurrentItem%2A> widoku. Należy pamiętać, że <xref:System.Windows.Data.CollectionViewSource> obiektów automatyczną synchronizację, waluty i wybór. Jeśli nie jest powiązany z formantu listy <xref:System.Windows.Data.CollectionViewSource> obiektu jak w poniższym przykładzie, należy ustawić jego <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> właściwość `true` Aby to działało.  
  
 Inne przykłady, zobacz [powiązania z kolekcją i wyświetlanie informacji na podstawie wybranych](../../../../docs/framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md) i [Użyj wzorca szczegółowego z danymi hierarchicznymi](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md).  
  
 Być może zauważono, że powyższy przykład używa szablonu. W rzeczywistości danych może być niewidoczne na sposób przywołamy bez korzystania z szablonów (jawnie używaną przez <xref:System.Windows.Controls.ContentControl> i jeden niejawnie używane przez <xref:System.Windows.Controls.ListBox>). Przejdziemy teraz do obsługi danych szablonów w następnej sekcji.  
  
<a name="data_templating"></a>   
## <a name="data-templating"></a>Szablonowanie danych  
 Bez użycia szablonów danych, nasza aplikacja [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] w [co to jest powiązanie danych?](#what_is_data_binding) sekcji będzie wyglądać podobnie do poniższego:  
  
 ![Pokaz bez użycia szablonów danych tworzenia powiązania danych](../../../../docs/framework/wpf/data/media/databindingdemotemplates.png "DataBindingDemoTemplates")  
  
 Jak pokazano w przykładzie w poprzedniej sekcji, zarówno <xref:System.Windows.Controls.ListBox> kontroli i <xref:System.Windows.Controls.ContentControl> są powiązane z obiektu całą kolekcję (lub dokładniej, widok za pośrednictwem obiektu kolekcji) *AuctionItem*s. Bez szczegółowych instrukcji sposób wyświetlania zbierania danych <xref:System.Windows.Controls.ListBox> Wyświetla reprezentację ciągu każdego obiektu w kolekcji źródłowej i <xref:System.Windows.Controls.ContentControl> wyświetla ciąg reprezentujący obiekt jest powiązana.  
  
 Aby rozwiązać ten problem, aplikacji zdefiniowano <xref:System.Windows.DataTemplate>s. Jak pokazano w przykładzie w poprzedniej sekcji <xref:System.Windows.Controls.ContentControl> jawnie używa *detailsProductListingTemplate*<xref:System.Windows.DataTemplate>. <xref:System.Windows.Controls.ListBox> Formant niejawnie wykorzystuje następujące <xref:System.Windows.DataTemplate> przy wyświetlaniu *AuctionItem* obiektów w kolekcji:  
  
 [!code-xaml[DataBindingLab#AuctionItemDataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#auctionitemdatatemplate)]  
  
 Przy użyciu tych dwóch <xref:System.Windows.DataTemplate>, wynikowy interfejsu użytkownika jest architekturze pokazanej w [co to jest powiązanie danych?](#what_is_data_binding) sekcji. Jak widać na tym zrzucie ekranu, oprócz wynajmowanie umieszczenia danych w swojej kontrolki <xref:System.Windows.DataTemplate>s umożliwiają definiowanie atrakcyjnych wizualizacji danych. Na przykład <xref:System.Windows.DataTrigger>s są używane w powyższych <xref:System.Windows.DataTemplate> tak, aby *AuctionItem*s *SpecialFeatures* wartość *wyróżnić* będzie można wyświetlić za pomocą pomarańczowy obramowanie i gwiazdkę.  
  
 Aby uzyskać więcej informacji na temat szablonów danych zobacz [Przegląd Szablonowanie danych](../../../../docs/framework/wpf/data/data-templating-overview.md).  
  
<a name="data_validation"></a>   
## <a name="data-validation"></a>Sprawdzanie poprawności danych  
  
 Większość aplikacji, które akceptują dane wejściowe użytkownika konieczne logikę weryfikacji, aby upewnić się, że użytkownik wprowadził oczekiwane informacje. Sprawdzanie poprawności mogą opierać się na typ, zakres, format lub inne wymagania specyficzne dla aplikacji. W tej sekcji opisano, jak sprawdzanie poprawności danych działa w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### <a name="associating-validation-rules-with-a-binding"></a>Kojarzenie reguł sprawdzania poprawności z powiązaniem  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Modelu powiązania danych umożliwia kojarzenie <xref:System.Windows.Data.Binding.ValidationRules%2A> za pomocą usługi <xref:System.Windows.Data.Binding> obiektu. Na przykład, poniższy przykład tworzy powiązanie <xref:System.Windows.Controls.TextBox> z właściwością o nazwie `StartPrice` i dodaje <xref:System.Windows.Controls.ExceptionValidationRule> obiekt <xref:System.Windows.Data.Binding.ValidationRules%2A?displayProperty=nameWithType> właściwości.  
  
 [!code-xaml[DataBindingLab#DefaultValidation](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/AddProductWindow.xaml#defaultvalidation)]  
  
 Element <xref:System.Windows.Controls.ValidationRule> obiektu sprawdza, czy wartość właściwości jest nieprawidłowa. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia następujące dwa typy wbudowane <xref:System.Windows.Controls.ValidationRule> obiektów:  
  
-   A <xref:System.Windows.Controls.ExceptionValidationRule> sprawdza, czy wyjątki generowane podczas aktualizacji właściwości źródła powiązania. W poprzednim przykładzie `StartPrice` jest typu Integer. Po użytkownik wprowadza wartość, której nie można przekonwertować na liczbę całkowitą, jest zwracany wyjątek, powodując powiązania był oznaczony jako nieprawidłowy. Składni alternatywne ustawienia <xref:System.Windows.Controls.ExceptionValidationRule> jawnie polega na ustawieniu <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> właściwości `true` na Twoje <xref:System.Windows.Data.Binding> lub <xref:System.Windows.Data.MultiBinding> obiektu.  
  
-   A <xref:System.Windows.Controls.DataErrorValidationRule> obiektu sprawdza, czy błędy, które są wywoływane przez obiekty, które implementują <xref:System.ComponentModel.IDataErrorInfo> interfejsu. Przykład przy użyciu tej reguły sprawdzania poprawności, zobacz <xref:System.Windows.Controls.DataErrorValidationRule>. Składni alternatywne ustawienia <xref:System.Windows.Controls.DataErrorValidationRule> jawnie polega na ustawieniu <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> właściwości `true` na Twoje <xref:System.Windows.Data.Binding> lub <xref:System.Windows.Data.MultiBinding> obiektu.  
  
 Można również utworzyć własne reguły sprawdzania poprawności przez pochodząca od <xref:System.Windows.Controls.ValidationRule> klasy i wdrażanie <xref:System.Windows.Controls.ValidationRule.Validate%2A> metody. W poniższym przykładzie pokazano regułą używaną przez *Dodaj listę produktów* "Data rozpoczęcia" <xref:System.Windows.Controls.TextBox> z [co to jest powiązanie danych?](#what_is_data_binding) sekcji:  
  
 [!code-csharp[DataBindingLab#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/FutureDateRule.cs#2)]
 [!code-vb[DataBindingLab#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/FutureDateRule.vb#2)]  
  
 *StartDateEntryForm* <xref:System.Windows.Controls.TextBox> używa tej wartości *FutureDateRule*, jak pokazano w poniższym przykładzie:  
  
 [!code-xaml[DataBindingLab#CustomValidation](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/AddProductWindow.xaml#customvalidation)]  
  
 Należy pamiętać, że ponieważ <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> wartość <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>, aparat powiązania aktualizuje wartość źródła po każdym naciśnięciu klawisza oznacza, że również kontroli każda reguła w <xref:System.Windows.Data.Binding.ValidationRules%2A> kolekcji po każdym naciśnięciu klawisza. Omówimy to w dalszej części procesu weryfikacji.  
  
<a name="invalidation_feedback"></a>   
### <a name="providing-visual-feedback"></a>Przekazywanie opinii Visual  
 Jeśli użytkownik wprowadzi nieprawidłową wartość, warto podać opinię o błędzie aplikacji [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Jednym sposobem, aby podać te opinie polega na ustawieniu <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType> dołączonych właściwości do niestandardowego <xref:System.Windows.Controls.ControlTemplate>. Jak pokazano w poprzednim podsekcji *StartDateEntryForm* <xref:System.Windows.Controls.TextBox> używa <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> o nazwie *validationTemplate*. W poniższym przykładzie pokazano definicję *validationTemplate*:  
  
 [!code-xaml[DataBindingLab#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/AddProductWindow.xaml#1)]  
  
 <xref:System.Windows.Controls.AdornedElementPlaceholder> Element określa, gdzie ma zostać umieszczony formant jest powiązany.  
  
 Ponadto można także użyć <xref:System.Windows.Controls.ToolTip> do wyświetlania komunikatu o błędzie. Zarówno *StartDateEntryForm* i *StartPriceEntryForm*<xref:System.Windows.Controls.TextBox>es użyć stylu *textStyleTextBox*, co powoduje utworzenie <xref:System.Windows.Controls.ToolTip> , Wyświetla komunikat o błędzie. W poniższym przykładzie pokazano definicję *textStyleTextBox*. Dołączona właściwość <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true` po co najmniej jeden z powiązania właściwości elementu powiązania znajdują się w błędzie.  
  
 [!code-xaml[DataBindingLab#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#14)]  
  
 Za pomocą niestandardowej <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> i <xref:System.Windows.Controls.ToolTip>, *StartDateEntryForm* <xref:System.Windows.Controls.TextBox> wygląda podobnie do następującego po błędzie sprawdzania poprawności:  
  
 ![Błąd sprawdzania poprawności powiązania danych](../../../../docs/framework/wpf/data/media/databindingdemo-validation.PNG "DataBindingDemo_Validation")  
  
 Jeśli Twoje <xref:System.Windows.Data.Binding> skojarzone reguły sprawdzania poprawności, ale nie określisz <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> na formant związany domyślny <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> będzie służyć do powiadamiania użytkowników, gdy występuje błąd weryfikacji. Wartość domyślna <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> jest szablon kontrolki, który definiuje czerwone obramowanie w warstwie moduł definiowania układu kodu. Przy użyciu domyślnego <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> i <xref:System.Windows.Controls.ToolTip>, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] z *StartPriceEntryForm* <xref:System.Windows.Controls.TextBox> wygląda podobnie do następującego po błędzie sprawdzania poprawności:  
  
 ![Błąd sprawdzania poprawności powiązania danych](../../../../docs/framework/wpf/data/media/databindingdemo-validationdefault.PNG "DataBindingDemo_ValidationDefault")  
  
 Na przykład jak zapewnić logikę do weryfikowania wszystkich kontrolek w oknie dialogowym, zobacz sekcję niestandardowych okien dialogowych w [Przegląd okien dialogowych](../../../../docs/framework/wpf/app-development/dialog-boxes-overview.md).  
  
### <a name="validation-process"></a>Proces weryfikacji  
 Sprawdzanie poprawności zwykle występuje, gdy wartość elementu docelowego jest przesyłany do właściwości źródła powiązania. Dzieje się tak na <xref:System.Windows.Data.BindingMode.TwoWay> i <xref:System.Windows.Data.BindingMode.OneWayToSource> powiązania. Dobrze, co powoduje, że aktualizacja źródeł zależy od wartości <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> właściwości, zgodnie z opisem w [wyzwalaczy źródła aktualizacji co](#what_triggers_source_updates) sekcji.  
  
 Poniżej opisano *weryfikacji* procesu. Należy pamiętać, że jeśli w dowolnym momencie w trakcie tego procesu wystąpi błąd sprawdzania poprawności lub inny rodzaj błędu, proces jest zatrzymywane.  
  
1.  Aparat powiązania sprawdza, czy istnieją niestandardowe <xref:System.Windows.Controls.ValidationRule> zdefiniowane obiekty, których <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> jest ustawiona na <xref:System.Windows.Controls.ValidationStep.RawProposedValue> tego <xref:System.Windows.Data.Binding>, w którym to przypadku wywoływanych przez nią <xref:System.Windows.Controls.ValidationRule.Validate%2A> metody na każdym <xref:System.Windows.Controls.ValidationRule> aż jeden z nich działa na błąd lub do momentu przekazania wszystkich z nich.  
  
2.  Aparat powiązania wywołuje konwertera, jeśli taka istnieje.  
  
3.  Jeśli konwerter zakończy się powodzeniem, aparat powiązania sprawdza, czy istnieją niestandardowe <xref:System.Windows.Controls.ValidationRule> zdefiniowane obiekty, których <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> jest ustawiona na <xref:System.Windows.Controls.ValidationStep.ConvertedProposedValue> tego <xref:System.Windows.Data.Binding>, w którym to przypadku wywoływanych przez nią <xref:System.Windows.Controls.ValidationRule.Validate%2A> metody na każdym <xref:System.Windows.Controls.ValidationRule> zawierający <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> równa <xref:System.Windows.Controls.ValidationStep.ConvertedProposedValue> aż do jednego z nich działa na błąd lub przekazać je wszystkie.  
  
4.  Aparat powiązania ustawia właściwość source.  
  
5.  Aparat powiązania sprawdza, czy istnieją niestandardowe <xref:System.Windows.Controls.ValidationRule> zdefiniowane obiekty, których <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> jest ustawiona na <xref:System.Windows.Controls.ValidationStep.UpdatedValue> tego <xref:System.Windows.Data.Binding>, w którym to przypadku wywoływanych przez nią <xref:System.Windows.Controls.ValidationRule.Validate%2A> metody na każdym <xref:System.Windows.Controls.ValidationRule> zawierający <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> równa <xref:System.Windows.Controls.ValidationStep.UpdatedValue> aż do jednego z nich działa na błąd lub przekazać je wszystkie. Jeśli <xref:System.Windows.Controls.DataErrorValidationRule> jest skojarzony z powiązaniem i jego <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> jest ustawiona na wartość domyślna <xref:System.Windows.Controls.ValidationStep.UpdatedValue>, <xref:System.Windows.Controls.DataErrorValidationRule> zaznaczono w tym momencie. Jest to punkt podczas powiązań, które mają <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> równa `true` są sprawdzane.  
  
6.  Aparat powiązania sprawdza, czy istnieją niestandardowe <xref:System.Windows.Controls.ValidationRule> zdefiniowane obiekty, których <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> jest ustawiona na <xref:System.Windows.Controls.ValidationStep.CommittedValue> tego <xref:System.Windows.Data.Binding>, w którym to przypadku wywoływanych przez nią <xref:System.Windows.Controls.ValidationRule.Validate%2A> metody na każdym <xref:System.Windows.Controls.ValidationRule> zawierający <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> równa <xref:System.Windows.Controls.ValidationStep.CommittedValue> aż do jednego z nich działa na błąd lub przekazać je wszystkie.  
  
 Jeśli <xref:System.Windows.Controls.ValidationRule> nie zostały spełnione w dowolnym momencie w trakcie tego procesu aparat powiązania tworzy <xref:System.Windows.Controls.ValidationError> obiektu i dodaje go do <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> kolekcji elementu powiązania. Przed rozpoczęciem powiązania aparatu uruchamia <xref:System.Windows.Controls.ValidationRule> obiekty na wszelkie danego kroku spowoduje usunięcie dowolnego <xref:System.Windows.Controls.ValidationError> który został dodany do <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> dołączonych właściwości elementu powiązania podczas tego etapu. Na przykład jeśli <xref:System.Windows.Controls.ValidationRule> którego <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> jest ustawiona na <xref:System.Windows.Controls.ValidationStep.UpdatedValue> nie powiodło się podczas następnego występuje proces sprawdzania poprawności, usuwa aparatu powiązania, który <xref:System.Windows.Controls.ValidationError> natychmiast przed wywoływanych przez nią dowolne <xref:System.Windows.Controls.ValidationRule> zawierający <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> równa <xref:System.Windows.Controls.ValidationStep.UpdatedValue>.  
  
 Gdy <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> nie jest pusta, <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> dołączonych właściwości elementu ustawiono `true`. Ponadto jeśli <xref:System.Windows.Data.Binding.NotifyOnValidationError%2A> właściwość <xref:System.Windows.Data.Binding> jest ustawiona na `true`, wywołuje aparat powiązania, a następnie <xref:System.Windows.Controls.Validation.Error?displayProperty=nameWithType> dołączone zdarzenie w elemencie.  
  
 Też pamiętać, że transfer prawidłową wartość, w dowolnym kierunku (obiekt docelowy źródło lub źródła do docelowego) Czyści <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> dołączona właściwość.  
  
 Jeśli ma powiązanie <xref:System.Windows.Controls.ExceptionValidationRule> skojarzonych z nim lub miał <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> właściwość jest ustawiona na `true` i wyjątek jest zgłaszany, gdy aparat powiązania ustawia źródło, aparat powiązania sprawdza, czy <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>. Masz możliwość użycia <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A> wywołanie zwrotne w celu zapewnienia obsługi niestandardowej obsługi wyjątków. Jeśli <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A> nie jest określona w <xref:System.Windows.Data.Binding>, aparat powiązania tworzy <xref:System.Windows.Controls.ValidationError> z wyjątkiem i dodaje go do <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> kolekcji elementu powiązania.  
  
## <a name="debugging-mechanism"></a>Mechanizm debugowania  
 Dołączona właściwość można ustawić <xref:System.Diagnostics.PresentationTraceSources.TraceLevel%2A?displayProperty=nameWithType> na obiekt powiązane powiązanie, aby otrzymywać informacje na temat stanu określonego powiązania.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.DataErrorValidationRule>  
 [Nowości w WPF w wersji 4.5](../../../../docs/framework/wpf/getting-started/whats-new.md)  
 [Powiązywanie z wynikami zapytania LINQ](../../../../docs/framework/wpf/data/how-to-bind-to-the-results-of-a-linq-query.md)  
 [Powiązanie danych](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [Pokaz powiązania danych](https://go.microsoft.com/fwlink/?LinkID=163703)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)  
 [Powiązywanie ze źródłem danych ADO.NET](../../../../docs/framework/wpf/data/how-to-bind-to-an-ado-net-data-source.md)
