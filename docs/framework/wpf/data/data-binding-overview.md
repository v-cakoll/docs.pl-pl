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
ms.openlocfilehash: 44a35131273c6f191ab5da5bc1639d97bd961ff1
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/17/2019
ms.locfileid: "69567512"
---
# <a name="data-binding-overview"></a>Przegląd Wiązanie danych
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]powiązanie danych zapewnia prosty i spójny sposób, w jaki aplikacje mogą być obecne i współpracujące z danymi. Elementy mogą być powiązane z danymi z różnych źródeł danych w postaci obiektów środowiska uruchomieniowego języka wspólnego (CLR) i [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]. <xref:System.Windows.Controls.ContentControl>s takie jak <xref:System.Windows.Controls.Button> i <xref:System.Windows.Controls.ItemsControl>s, takie <xref:System.Windows.Controls.ListBox> jak <xref:System.Windows.Controls.ListView> i, mają wbudowaną funkcję do włączania elastycznego stylu pojedynczych elementów danych lub kolekcji elementów danych. Widoki sortowania, filtrowania i grupowania mogą być generowane na podstawie danych.  
  
 Funkcje wiązania danych w programie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mają kilka korzyści w porównaniu z tradycyjnymi modelami, w tym szeroką gamę właściwości, które z własnej [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] natury obsługują powiązanie danych, elastyczną reprezentację danych i czyste rozdzielenie firmy Logika [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]z.  
  
 Ten temat najpierw omawia koncepcje podstawowe [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] względem powiązań danych, a następnie przechodzi do użycia <xref:System.Windows.Data.Binding> klasy i innych funkcji powiązania danych.  

<a name="what_is_data_binding"></a>   
## <a name="what-is-data-binding"></a>Co to jest powiązanie danych?  
 Powiązanie danych to proces, który ustanawia połączenie między aplikacją [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] a logiką biznesową. Jeśli powiązanie ma poprawne ustawienia, a dane zawierają odpowiednie powiadomienia, a następnie, gdy dane zmienią swoją wartość, elementy, które są powiązane z danymi, odzwierciedlają zmiany automatycznie. Powiązanie danych może również oznaczać, że jeśli zewnętrzna reprezentacja danych w elemencie ulegnie zmianie, dane bazowe można automatycznie zaktualizować, aby odzwierciedlały zmianę. Na przykład, jeśli użytkownik edytuje wartość w <xref:System.Windows.Controls.TextBox> elemencie, wartość danych źródłowych zostanie automatycznie zaktualizowana w celu odzwierciedlenia tej zmiany.  
  
 Typowym zastosowaniem wiązania danych jest umieszczenie danych konfiguracji serwera lub lokalnego w formie formularzy lub innych [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] kontrolek. W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]programie pojęcie to jest rozwinięte w celu uwzględnienia powiązania szerokiej gamy właściwości z wieloma źródłami danych. W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]programie właściwości zależności elementów mogą być powiązane z obiektami CLR (w tym ADO.NET obiektów lub obiektów skojarzonych z usługami sieci Web i właściwościami sieci [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] Web) i danymi.  
  
 Aby zapoznać się z przykładem powiązania danych, zapoznaj się z następującą [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] aplikacją w [pokazie powiązania danych](https://go.microsoft.com/fwlink/?LinkID=163703):  
  
 ![Zrzut ekranu przykładowego powiązania danych](./media/databinding-databindingdemo.png "DataBinding_DataBindingDemo")  
  
 Powyżej znajduje [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] się aplikacja, która wyświetla listę elementów aukcji. Aplikacja prezentuje następujące funkcje powiązania danych:  
  
- Zawartość <xref:System.Windows.Controls.ListBox> jest powiązana z kolekcją obiektów *AuctionItem* . Obiekt *AuctionItem* ma właściwości, takie jak *Description*, *StartPrice*, *StartDate*, *Category*, *SpecialFeatures*itp.  
  
- Dane (obiekty*AuctionItem* ) wyświetlane w programie <xref:System.Windows.Controls.ListBox> są szablonem, dzięki czemu dla każdego elementu są pokazywane opisy i bieżące ceny. Jest to wykonywane przy użyciu <xref:System.Windows.DataTemplate>. Ponadto wygląd każdego elementu zależy od wartości *SpecialFeatures* wyświetlanej *AuctionItem* . Jeśli *SpecialFeatures* wartość *AuctionItem* jest *kolorem*, element ma niebieskie obramowanie. Jeśli zostanie *wyświetlona* wartość, element ma pomarańczowy obramowanie i gwiazdkę. Sekcja [tworzenia szablonów danych](#data_templating) zawiera informacje na temat tworzenia szablonów danych.  
  
- Użytkownik może grupować, filtrować lub sortować dane przy użyciu dostarczonego programu <xref:System.Windows.Controls.CheckBox>es. Na powyższym obrazie są wybrane pozycje "Grupuj według kategorii" i "Sortuj według kategorii <xref:System.Windows.Controls.CheckBox>i daty". Być może zauważono, że dane są pogrupowane na podstawie kategorii produktu, a nazwa kategorii jest w kolejności alfabetycznej. Trudno jest zauważyć z obrazu, ale elementy są również sortowane według daty rozpoczęcia w każdej kategorii. Odbywa się to przy użyciu *widoku kolekcji*. Sekcja [powiązanie z kolekcjami](#binding_to_collections) omawia widoki kolekcji.  
  
- Gdy użytkownik wybierze element, <xref:System.Windows.Controls.ContentControl> wyświetla szczegóły wybranego elementu. Jest to tzw. *scenariusz wzorzec-szczegóły*. Sekcja [scenariusz główny-szczegóły](#master_detail_scenario) zawiera informacje na temat tego typu scenariusza powiązania.  
  
- Typ właściwości *StartDate* to <xref:System.DateTime>, która zwraca datę, która zawiera czas do milisekundy. W tej aplikacji użyto niestandardowego konwertera, aby był wyświetlany krótszy ciąg daty. Sekcja [Konwersja danych](#data_conversion) zawiera informacje na temat konwerterów.  
  
 Gdy użytkownik kliknie przycisk *Dodaj produkt* , zostanie wyświetlony następujący formularz:  
  
 ![Strona dodawania listy produktów](./media/databinding-demo-addproductlisting.png "DataBinding_Demo_AddProductListing")  
  
 Użytkownik może edytować pola w formularzu, przeglądać listę produktów przy użyciu krótkiej wersji zapoznawczej i bardziej szczegółowych okienek podglądu, a następnie kliknąć pozycję *Prześlij* , aby dodać nową listę produktów. Wszystkie istniejące funkcje grupowania, filtrowania i sortowania będą stosowane do nowego wpisu. W tym konkretnym przypadku element wprowadzony w powyższym obrazie będzie wyświetlany jako drugi element w kategorii *komputer* .  
  
 Nie pokazane w tym obrazie jest logiką walidacji podaną w *dacie* <xref:System.Windows.Controls.TextBox>rozpoczęcia. Jeśli użytkownik wprowadzi nieprawidłową datę (nieprawidłowe formatowanie lub datę przeszłą), użytkownik zostanie powiadomiony z <xref:System.Windows.Controls.ToolTip> i czerwonym wykrzyknikiem obok. <xref:System.Windows.Controls.TextBox> W sekcji [walidacja danych](#data_validation) omówiono sposób tworzenia logiki walidacji.  
  
 Przed przystąpieniem do różnych funkcji powiązania danych wymienionych powyżej należy najpierw omówić w następnej sekcji podstawowe pojęcia, które mają kluczowe znaczenie dla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tworzenia powiązań danych.  
  
## <a name="basic-data-binding-concepts"></a>Podstawowe pojęcia dotyczące powiązań danych  
  
 Niezależnie od tego, jaki element jest powiązany, i istoty źródła danych, każde powiązanie zawsze jest zgodne z modelem przedstawionym na poniższej ilustracji:  
  
 ![Diagram przedstawiający podstawowy model powiązań danych.](./media/data-binding-overview/basic-data-binding-diagram.png)  
  
 Jak pokazano na powyższym rysunku, powiązanie danych jest zasadniczo mostkiem między obiektem docelowym powiązania a źródłem powiązania. Na rysunku przedstawiono następujące podstawowe [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] koncepcje dotyczące powiązań danych:  
  
- Zwykle każde powiązanie ma te cztery składniki: obiekt docelowy powiązania, właściwość docelowa, Źródło powiązania i ścieżka do wartości w źródle powiązania do użycia. Na przykład jeśli chcesz powiązać zawartość elementu <xref:System.Windows.Controls.TextBox> z właściwością *Nazwa* obiektu *Employee* <xref:System.Windows.Controls.TextBox>, obiektem docelowym jest, właściwość target jest <xref:System.Windows.Controls.TextBox.Text%2A> właściwością, wartość, która ma zostać użyta, to *Nazwa*, a obiektem źródłowym jest obiekt *Employee* .  
  
- Właściwość Target musi być właściwością zależności. Większość <xref:System.Windows.UIElement> właściwości to właściwości zależności i większość właściwości zależności, z wyjątkiem tych, które domyślnie obsługują powiązanie danych. (Tylko <xref:System.Windows.DependencyObject> typy mogą definiować właściwości zależności i wszystkie <xref:System.Windows.UIElement>elementy pochodne z <xref:System.Windows.DependencyObject>.)  
  
- Chociaż nie jest określony na rysunku, należy zauważyć, że obiekt źródłowy powiązania nie jest ograniczony do niestandardowego obiektu CLR. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]powiązanie danych obsługuje dane w postaci obiektów CLR i [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]. Aby udostępnić przykłady, Źródło powiązania może być obiektem dowolnego <xref:System.Windows.UIElement>elementu listy, obiektem CLR skojarzonym z danymi ADO.NET lub usługami sieci Web lub elementem XmlNode, który [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] zawiera dane. Aby uzyskać więcej informacji, zobacz [Omówienie źródeł powiązań](binding-sources-overview.md).  
  
 Podczas odczytywania informacji w innych tematach zestawu SDK należy pamiętać, że podczas ustanawiania powiązania, powiązanie celu powiązania *ze* źródłem powiązań. [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] Na przykład jeśli dane <xref:System.Windows.Controls.ListBox> podstawowe są wyświetlane przy użyciu powiązania danych <xref:System.Windows.Controls.ListBox> , można powiązać [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dane.  
  
 Aby ustanowić powiązanie, należy użyć <xref:System.Windows.Data.Binding> obiektu. Pozostała część tego tematu omawia wiele koncepcji skojarzonych z i niektórych właściwości i użycia <xref:System.Windows.Data.Binding> obiektu.  
  
<a name="direction_of_data_flow"></a>   
### <a name="direction-of-the-data-flow"></a>Kierunek przepływu danych  
 Jak wspomniano wcześniej i wskazane przez strzałkę na powyższym rysunku, przepływ danych powiązania może przejść od celu powiązania do źródła powiązania (na przykład wartość źródłowa zmienia się, gdy użytkownik edytuje wartość <xref:System.Windows.Controls.TextBox>) i/lub ze źródła powiązania do celu powiązania (na przykład <xref:System.Windows.Controls.TextBox> zawartość zostaje zaktualizowana o zmiany w źródle powiązania), jeśli źródło powiązania udostępnia odpowiednie powiadomienia.  
  
 Możesz chcieć, aby aplikacja umożliwiała użytkownikom zmianę danych i propagowanie jej z powrotem do obiektu źródłowego. Możesz też nie chcieć, aby użytkownicy mogli aktualizować dane źródłowe. Można to kontrolować przez ustawienie <xref:System.Windows.Data.Binding.Mode%2A> właściwości <xref:System.Windows.Data.Binding> obiektu. Na poniższej ilustracji przedstawiono różne typy przepływów danych:  
  
 ![Przepływ danych powiązań danych](./media/databinding-dataflow.png "DataBinding_DataFlow")  
  
- <xref:System.Windows.Data.BindingMode.OneWay>powiązanie powoduje, że zmiany właściwości source mają automatycznie aktualizować właściwość target, ale zmiany właściwości target nie są propagowane do właściwości source. Ten typ powiązania jest odpowiedni, Jeśli powiązanie formantu jest niejawnie tylko do odczytu. Na przykład można powiązać ze źródłem danych, takim jak takt giełdowy lub być może Właściwość docelowa nie ma interfejsu sterującego do wprowadzania zmian, takich jak kolor tła związany z danymi tabeli. Jeśli nie ma potrzeby monitorowania zmian właściwości docelowej, użycie <xref:System.Windows.Data.BindingMode.OneWay> trybu powiązania pozwala uniknąć narzutu <xref:System.Windows.Data.BindingMode.TwoWay> na tryb powiązania.  
  
- <xref:System.Windows.Data.BindingMode.TwoWay>powiązanie powoduje, że zmiany właściwości source lub Target mają być automatycznie aktualizowane. Ten typ powiązania jest odpowiedni dla formularzy edytowalnych lub innych scenariuszy w pełni [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] interaktywnych. Większość właściwości jest domyślnie <xref:System.Windows.Data.BindingMode.OneWay> powiązana, ale niektóre właściwości zależności (zazwyczaj właściwości kontrolek edytowalnych przez użytkownika, <xref:System.Windows.Controls.TextBox.Text%2A> takich jak <xref:System.Windows.Controls.TextBox> Właściwość i <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> Właściwość <xref:System.Windows.Controls.CheckBox>) domyślnie <xref:System.Windows.Data.BindingMode.TwoWay> powiązanie. Programistyczny sposób, aby określić, czy właściwość zależności jest domyślnie wiążąca lub dwukierunkowo, polega na pobieraniu metadanych właściwości przy użyciu <xref:System.Windows.DependencyProperty.GetMetadata%2A> , a następnie sprawdzaniu wartości <xref:System.Windows.FrameworkPropertyMetadata.BindsTwoWayByDefault%2A> logicznej właściwości.  
  
- <xref:System.Windows.Data.BindingMode.OneWayToSource>jest odwrotnym <xref:System.Windows.Data.BindingMode.OneWay> powiązaniem; aktualizuje właściwość source po zmianie właściwości docelowej. Przykładowy scenariusz polega na ponownym ocenie wartości źródłowej z [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
- Niezilustrowane na rysunku jest <xref:System.Windows.Data.BindingMode.OneTime> powiązanie, co powoduje, że Właściwość Source inicjuje właściwość docelową, ale kolejne zmiany nie są propagowane. Oznacza to, że jeśli kontekst danych przekroczy zmianę lub obiekt w kontekście danych ulegnie zmianie, zmiana nie zostanie odzwierciedlona we właściwości target. Ten typ powiązania jest odpowiedni, jeśli są używane dane, w których można użyć migawki bieżącego stanu lub dane są rzeczywiście statyczne. Ten typ powiązania jest również przydatny, jeśli chcesz zainicjować właściwość docelową z jakąś wartością z właściwości source, a kontekst danych nie jest znany z góry. Jest to zasadniczo prostszy sposób tworzenia <xref:System.Windows.Data.BindingMode.OneWay> powiązań, który zapewnia lepszą wydajność w przypadkach, gdy wartość źródłowa nie jest zmieniana.  
  
 Należy pamiętać, że aby wykrywać zmiany źródła <xref:System.Windows.Data.BindingMode.OneWay> ( <xref:System.Windows.Data.BindingMode.TwoWay> odpowiednie dla i powiązania), Źródło musi zaimplementować odpowiedni mechanizm powiadamiania o zmianach właściwości, taki jak <xref:System.ComponentModel.INotifyPropertyChanged>. Aby zapoznać się z <xref:System.ComponentModel.INotifyPropertyChanged> przykładem implementacji, zobacz [implementacja powiadomienia o zmianie właściwości](how-to-implement-property-change-notification.md) .  
  
 Strona <xref:System.Windows.Data.Binding.Mode%2A> właściwości zawiera więcej informacji na temat trybów powiązań oraz przykład sposobu określania kierunku powiązania.  
  
<a name="what_triggers_source_updates"></a>   
### <a name="what-triggers-source-updates"></a>Jakie aktualizacje źródła wyzwalaczy  
 Powiązania, które <xref:System.Windows.Data.BindingMode.TwoWay> są <xref:System.Windows.Data.BindingMode.OneWayToSource> lub nasłuchują zmian we właściwości docelowej i propagują je z powrotem do źródła. Jest to nazywane aktualizacją źródła. Na przykład można edytować tekst pola tekstowego, aby zmienić źródłową wartość źródłową. Zgodnie z opisem w ostatniej sekcji kierunek przepływu danych zależy od wartości <xref:System.Windows.Data.Binding.Mode%2A> właściwości powiązania.  
  
 Jednak czy wartość źródłowa jest aktualizowana podczas edytowania tekstu, czy po zakończeniu edycji tekstu i wskazaniu wskaźnika myszy poza polem tekstowym? <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> Właściwość powiązania określa, co wyzwala aktualizację źródła. Punkty strzałki w prawo na poniższej ilustracji ilustrują rolę <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> właściwości:  
  
 ![Diagram, który pokazuje rolę właściwości UpdateSourceTrigger.](./media/data-binding-overview/data-binding-updatesource-trigger.png)  
  
 Jeśli wartość to, <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>wówczas wartość wskazywana <xref:System.Windows.Data.BindingMode.TwoWay> przez strzałkę w <xref:System.Windows.Data.BindingMode.OneWayToSource> prawo lub powiązania zostaje zaktualizowana zaraz po zmianie właściwości docelowej. <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> Jeśli <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> jednak wartość jest, to <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>wartość jest aktualizowana tylko przy użyciu nowej wartości, gdy właściwość target utraci fokus.  
  
 Podobnie jak w <xref:System.Windows.Data.Binding.Mode%2A> przypadku właściwości różne właściwości zależności mają różne wartości <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> domyślne. Wartością domyślną dla większości właściwości zależności jest <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>, <xref:System.Windows.Controls.TextBox.Text%2A> podczas gdy właściwość <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>ma wartość domyślną. Oznacza to, że aktualizacje źródłowe są zwykle wykonywane zawsze wtedy, gdy zmieniana jest <xref:System.Windows.Controls.CheckBox>Właściwość docelowa, która jest przeznaczona dla programu es i innych prostych kontrolek. Jednak w przypadku pól tekstowych aktualizowanie po każdym naciśnięciu klawisza może spowodować obniżenie wydajności i odmówić użytkownikowi zwykłej szansy w odniesieniu do wolnego miejsca i naprawić błędy pisowni przed zatwierdzeniem nowej wartości. Dlatego <xref:System.Windows.Controls.TextBox.Text%2A> , że właściwość ma <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus> wartość domyślną zamiast <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.  
  
 Aby uzyskać informacje o tym, jak znaleźć wartość domyślną <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> właściwości zależności, zobacz stronę właściwości.<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>  
  
 W poniższej tabeli przedstawiono przykładowy scenariusz dla każdej <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> wartości <xref:System.Windows.Controls.TextBox> przy użyciu przykładu:  
  
|UpdateSourceTrigger wartość|Po zaktualizowaniu wartości źródłowej|Przykładowy scenariusz dla pola tekstowego|  
|-------------------------------|----------------------------------------|----------------------------------|  
|LostFocus (domyślnie dla <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType>)|Gdy kontrolka TextBox utraci fokus|<xref:System.Windows.Controls.TextBox> Skojarzony z logiką walidacji (patrz sekcja walidacja danych)|  
|PropertyChanged|Podczas wpisywania do<xref:System.Windows.Controls.TextBox>|<xref:System.Windows.Controls.TextBox>kontrolki w oknie pokoju rozmów|  
|Wprost|Gdy aplikacja wywołuje<xref:System.Windows.Data.BindingExpression.UpdateSource%2A>|<xref:System.Windows.Controls.TextBox>kontrolki w formularzu edytowalnym (aktualizuje wartości źródłowe tylko wtedy, gdy użytkownik kliknie przycisk Prześlij)|  
  
 Aby zapoznać się z przykładem, zobacz Kontrolowanie, [Kiedy tekst TextBox aktualizuje Źródło](how-to-control-when-the-textbox-text-updates-the-source.md).  
  
<a name="creating_a_binding"></a>   
## <a name="creating-a-binding"></a>Tworzenie powiązania  
  
 Aby recapitulate niektóre koncepcje omówione w poprzednich sekcjach, należy ustanowić powiązanie przy użyciu <xref:System.Windows.Data.Binding> obiektu, a każde powiązanie ma zazwyczaj cztery składniki: element docelowy powiązania, właściwość docelowa, Źródło powiązania i ścieżka do wartości źródłowej do użycia. W tej sekcji omówiono sposób konfigurowania powiązania.  
  
 Rozważmy następujący przykład, w którym obiekt źródłowy powiązania jest klasą o nazwie Moje *dane* , która jest zdefiniowana w przestrzeni nazw *SDKSample* . W celach demonstracyjnych Klasa obiektu *webdata* ma właściwość ciągu o nazwie *ColorName*, której wartość jest równa "Red". W ten sposób ten przykład generuje przycisk z czerwonym tłem.  
  
 [!code-xaml[BindNonTextProperty#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindNonTextProperty/CS/Page1.xaml#1)]  
  
 Aby uzyskać więcej szczegółowych informacji na temat składni deklaracji powiązania i Przykłady sposobu konfigurowania powiązania w kodzie, zobacz temat [Omówienie deklaracji powiązań](binding-declarations-overview.md).  
  
 Jeśli stosujemy ten przykład do naszego diagramu podstawowego, wynikowy rysunek wygląda następująco. To jest <xref:System.Windows.Data.BindingMode.OneWay> powiązanie, ponieważ właściwość Background domyślnie obsługuje <xref:System.Windows.Data.BindingMode.OneWay> powiązania.  
  
 ![Diagram przedstawiający Właściwość tła powiązania danych.](./media/data-binding-overview/data-binding-button-background-example.png)  
  
 Możesz się zastanawiać, dlaczego to działa, mimo że właściwość *ColorName* jest typu String, <xref:System.Windows.Controls.Control.Background%2A> podczas gdy właściwość jest <xref:System.Windows.Media.Brush>typu. Jest to domyślna konwersja typu w pracy i została omówiona w sekcji [Konwersja danych](#data_conversion) .  
  
<a name="specifying_the_binding_source"></a>   
### <a name="specifying-the-binding-source"></a>Określanie źródła powiązania  
 Zwróć uwagę, że w poprzednim przykładzie Źródło powiązania jest określone przez ustawienie <xref:System.Windows.FrameworkElement.DataContext%2A> właściwości <xref:System.Windows.Controls.DockPanel> w elemencie. Następnie dziedziczy wartość z<xref:System.Windows.Controls.DockPanel>elementu, który jest jego elementem nadrzędnym. <xref:System.Windows.FrameworkElement.DataContext%2A> <xref:System.Windows.Controls.Button> Aby ponownie wykonać iterację, obiekt źródłowy powiązania jest jednym z czterech niezbędnych składników powiązania. W związku z tym bez określonego obiektu źródłowego powiązania, powiązanie nie będzie niczego robić.  
  
 Istnieje kilka sposobów, aby określić obiekt źródłowy powiązania. <xref:System.Windows.FrameworkElement.DataContext%2A> Używanie właściwości w elemencie nadrzędnym jest przydatne w przypadku powiązania wielu właściwości z tym samym źródłem. Jednak czasami może być bardziej odpowiednie, aby określić źródło powiązania dla poszczególnych deklaracji powiązań. W poprzednim przykładzie, zamiast używać <xref:System.Windows.FrameworkElement.DataContext%2A> właściwości, można określić źródło powiązania przez <xref:System.Windows.Data.Binding.Source%2A> ustawienie właściwości bezpośrednio w deklaracji powiązania przycisku, jak w poniższym przykładzie:  
  
 [!code-xaml[BindNonTextProperty#BackgroundBindingCompact](~/samples/snippets/csharp/VS_Snippets_Wpf/BindNonTextProperty/CS/Page2.xaml#backgroundbindingcompact)]  
  
 Oprócz ustawiania <xref:System.Windows.FrameworkElement.DataContext%2A> właściwości elementu bezpośrednio, dziedziczenie <xref:System.Windows.FrameworkElement.DataContext%2A> wartości z elementu nadrzędnego (takiego jak przycisk w pierwszym przykładzie) i jawne określenie źródła <xref:System.Windows.Data.Binding.Source%2A> powiązania przez ustawienie właściwości w <xref:System.Windows.Data.Binding> (na przykład w ostatnim przykładzie) można również użyć <xref:System.Windows.Data.Binding.ElementName%2A> właściwości <xref:System.Windows.Data.Binding.RelativeSource%2A> lub właściwości, aby określić źródło powiązania. <xref:System.Windows.Data.Binding.ElementName%2A> Właściwość jest przydatna w przypadku powiązania z innymi elementami w aplikacji, na przykład w przypadku używania suwaka do dostosowywania szerokości przycisku. Właściwość jest przydatna, gdy powiązanie jest określone <xref:System.Windows.Controls.ControlTemplate> w lub <xref:System.Windows.Style>. <xref:System.Windows.Data.Binding.RelativeSource%2A> Aby uzyskać więcej informacji, zobacz [Określanie źródła powiązania](how-to-specify-the-binding-source.md).  
  
<a name="specifying_the_path_to_the_value"></a>   
### <a name="specifying-the-path-to-the-value"></a>Określanie ścieżki do wartości  
 Jeśli źródło powiązania jest obiektem, należy użyć <xref:System.Windows.Data.Binding.Path%2A> właściwości, aby określić wartość do użycia dla powiązania. Jeśli tworzysz powiązanie z [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] danymi, <xref:System.Windows.Data.Binding.XPath%2A> Użyj właściwości, aby określić wartość. W niektórych przypadkach może być stosowane do użycia <xref:System.Windows.Data.Binding.Path%2A> właściwości nawet wtedy, gdy dane są. [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] Na przykład jeśli chcesz uzyskać dostęp do właściwości Nazwa zwróconego obiektu XmlNode (w wyniku zapytania XPath), należy użyć <xref:System.Windows.Data.Binding.Path%2A> właściwości oprócz <xref:System.Windows.Data.Binding.XPath%2A> właściwości.  
  
 Aby uzyskać informacje o składni i przykłady, <xref:System.Windows.Data.Binding.Path%2A> zobacz <xref:System.Windows.Data.Binding.XPath%2A> i strony właściwości.  
  
 Należy zauważyć, że chociaż zostały wyróżnione, <xref:System.Windows.Data.Binding.Path%2A> że do wartości, która ma zostać użyta, jest jednym z czterech niezbędnych składników powiązania, w scenariuszach, które mają być powiązane z całym obiektem, wartość do użycia byłaby taka sama jak obiekt źródłowy powiązania. W takich przypadkach ma zastosowanie do nieokreślenia <xref:System.Windows.Data.Binding.Path%2A>. Rozważmy następujący przykład:  
  
 [!code-xaml[MasterDetail#EmptyBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/MasterDetail/CSharp/Page1.xaml#emptybinding)]  
  
 W powyższym przykładzie użyto składni pustego powiązania: {Binding}. W takim przypadku <xref:System.Windows.Controls.ListBox> dziedziczy element DataContext z nadrzędnego elementu DockPanel (nie pokazano w tym przykładzie). Jeśli ścieżka nie zostanie określona, wartością domyślną jest powiązanie z całym obiektem. Inaczej mówiąc, w tym przykładzie ścieżka została pozostawiona, ponieważ <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> właściwość jest powiązana z całym obiektem. (Zapoznaj się z sekcją [Powiązywanie z kolekcjami](#binding_to_collections) , aby uzyskać szczegółowe omówienie).  
  
 Oprócz powiązania z kolekcją, ten scenariusz jest również przydatny, gdy chcesz powiązać z całym obiektem, a nie tylko jedną właściwością obiektu. Na przykład, jeśli obiekt źródłowy jest typu String i po prostu chcesz powiązać z samym ciągiem. Inny typowy scenariusz występuje, gdy chcesz powiązać element z obiektem z kilkoma właściwościami.  
  
 Należy pamiętać, że może być konieczne zastosowanie logiki niestandardowej, aby dane były zrozumiałe dla powiązanej właściwości docelowej. Logika niestandardowa może mieć postać niestandardowego konwertera (jeśli konwersja typu domyślnego nie istnieje). Aby uzyskać informacje na temat konwerterów, zobacz [Konwersja danych](#data_conversion) .  
  
<a name="binding_bindingexpression"></a>   
### <a name="binding-and-bindingexpression"></a>Powiązywanie i BindingExpression  
 Przed zainstalowaniem innych funkcji i użycia powiązań danych warto wprowadzić <xref:System.Windows.Data.BindingExpression> klasę. Jak widać w poprzednich sekcjach, <xref:System.Windows.Data.Binding> Klasa jest klasą wysokiego poziomu dla deklaracji powiązania <xref:System.Windows.Data.Binding> ; Klasa zawiera wiele właściwości, które umożliwiają określenie charakterystyki powiązania. Klasa pokrewna <xref:System.Windows.Data.BindingExpression>,, jest obiektem źródłowym, który utrzymuje połączenie między źródłem a obiektem docelowym. Powiązanie zawiera wszystkie informacje, które mogą być współużytkowane przez kilka wyrażeń powiązań. A <xref:System.Windows.Data.BindingExpression> jest wyrażeniem wystąpienia, które nie może być współużytkowane i zawiera wszystkie informacje <xref:System.Windows.Data.Binding>o wystąpieniu.  
  
 Rozważmy na przykład następujące kwestie, w których obiekt jest wystąpieniem klasy webdata, *powiązanie* to obiektu źródłowego <xref:System.Windows.Data.Binding> , a Klasa obiektowa jest klasą zdefiniowaną, która zawiera właściwość ciągu o nazwie  *MyDataProperty*. Ten przykład wiąże zawartość tekstową elementu *webtext*, wystąpienie elementu <xref:System.Windows.Controls.TextBlock>, do *MyDataProperty*.  
  
 [!code-csharp[CodeOnlyBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#1)]
 [!code-vb[CodeOnlyBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#1)]  
  
 Możesz użyć tego samego obiektu *powiązania* , aby utworzyć inne powiązania. Na przykład można użyć obiektu *powiązania* , aby powiązać zawartość tekstową pola wyboru z *MyDataProperty*. W tym scenariuszu będą dostępne dwa wystąpienia <xref:System.Windows.Data.BindingExpression> udostępniania obiektu *powiązania* .  
  
 Obiekt można uzyskać za pomocą zwracanej wartości wywołania <xref:System.Windows.Data.BindingOperations.GetBindingExpression%2A> obiektu powiązanego z danymi. <xref:System.Windows.Data.BindingExpression> W poniższych tematach przedstawiono niektóre zastosowania <xref:System.Windows.Data.BindingExpression> klasy:  
  
- [Pobieranie obiektu wiążącego z powiązanej własności docelowej](how-to-get-the-binding-object-from-a-bound-target-property.md)  
  
- [Kontrolowanie momentu aktualizowania źródła tekstu kontrolki TextBox](how-to-control-when-the-textbox-text-updates-the-source.md)  
  
<a name="data_conversion"></a>   
## <a name="data-conversion"></a>Konwersja danych  
 W poprzednim przykładzie przycisk ma kolor czerwony, ponieważ jego <xref:System.Windows.Controls.Control.Background%2A> właściwość jest powiązana z właściwością ciągu o wartości "Red". Dzieje się tak, ponieważ typ jest obecny w typie <xref:System.Windows.Media.Brush> , aby przekonwertować wartość ciągu <xref:System.Windows.Media.Brush>na.  
  
 Aby dodać te informacje do rysunku w sekcji [Tworzenie powiązania](#creating_a_binding) , diagram wygląda następująco:  
  
 ![Diagram, który pokazuje domyślną właściwość powiązania danych.](./media/data-binding-overview/data-binding-button-default-conversion.png)  
  
 Jednak co zrobić, jeśli zamiast posiadania właściwości typu String obiekt źródłowy powiązania ma właściwość *Color* typu <xref:System.Windows.Media.Color>? W takim przypadku aby wiązanie działało, należy najpierw włączyć wartość właściwości *Color* do elementu, który <xref:System.Windows.Controls.Control.Background%2A> akceptuje właściwość. Należy utworzyć konwerter niestandardowy, implementując <xref:System.Windows.Data.IValueConverter> interfejs, tak jak w poniższym przykładzie:  
  
 [!code-csharp[ColorPicker_snip#16](~/samples/snippets/csharp/VS_Snippets_Wpf/ColorPicker_snip/CSharp/ColorPickerLib/ColorPicker.cs#16)]
 [!code-vb[ColorPicker_snip#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ColorPicker_snip/visualbasic/colorpickerlib/colorpicker.vb#16)]  
  
 Strona <xref:System.Windows.Data.IValueConverter> referencyjna zawiera więcej informacji.  
  
 Teraz jest używany konwerter niestandardowy zamiast konwersji domyślnej. nasz diagram wygląda następująco:  
  
 ![Diagram przedstawiający niestandardowy konwerter powiązań danych.](./media/data-binding-overview/data-binding-converter-color-example.png)  
  
 Aby przeprowadzić ponownie iterację, konwersje domyślne mogą być dostępne ze względu na konwertery typów, które są obecne w typie, z którym jest powiązany. Takie zachowanie będzie zależeć od tego, które konwertery typów są dostępne w miejscu docelowym. W razie wątpliwości Utwórz własny konwerter.  
  
 Poniżej przedstawiono niektóre typowe scenariusze, w których warto wdrożyć konwerter danych:  
  
- Dane powinny być wyświetlane inaczej, w zależności od kultury. Na przykład możesz chcieć zaimplementować konwerter waluty lub konwerter daty/czasu kalendarza na podstawie wartości lub standardów używanych w określonej kulturze.  
  
- Używane dane nie muszą mieć potrzeby zmiany wartości tekstowej właściwości, ale zamiast tego należy zmienić inną wartość, na przykład źródło obrazu lub kolor lub styl wyświetlanego tekstu. Konwertery mogą być używane w tym wystąpieniu przez konwersję powiązania właściwości, która prawdopodobnie nie jest odpowiednia, na przykład wiązanie pola tekstowego z właściwością Background komórki tabeli.  
  
- Więcej niż jedna kontrolka lub wiele właściwości kontrolek są powiązane z tymi samymi danymi. W takim przypadku podstawowe powiązanie może po prostu wyświetlić tekst, podczas gdy inne powiązania obsługują konkretne problemy z wyświetlaniem, ale nadal używają tego samego powiązania jako informacji źródłowych.  
  
- Jeszcze dotąd nie omówiono <xref:System.Windows.Data.MultiBinding>, gdzie Właściwość docelowa ma kolekcję powiązań. W przypadku a <xref:System.Windows.Data.MultiBinding>, używasz niestandardowych <xref:System.Windows.Data.IMultiValueConverter> do tworzenia wartości końcowej z wartości powiązań. Na przykład kolor może być obliczany na podstawie wartości czerwony, niebieski i zielony, które mogą być wartościami z tego samego lub różnych obiektów źródłowych powiązań. Przykłady i informacje można znaleźć na stronie klasy.<xref:System.Windows.Data.MultiBinding>  
  
<a name="binding_to_collections"></a>   
## <a name="binding-to-collections"></a>Powiązanie z kolekcjami  
  
 Obiekt źródłowy powiązania może być traktowany jako pojedynczy obiekt, którego właściwości zawierają dane lub jako gromadzenie danych obiektów polimorficznych, które są często zgrupowane razem (na przykład wynik zapytania do bazy danych). Do tej pory omawiamy tylko powiązanie z pojedynczymi obiektami, jednak powiązanie z kolekcją danych jest typowym scenariuszem. Na przykład typowym scenariuszem <xref:System.Windows.Controls.ItemsControl> jest użycie takich <xref:System.Windows.Controls.ListBox>jak, <xref:System.Windows.Controls.ListView>, lub <xref:System.Windows.Controls.TreeView> do wyświetlania kolekcji danych, na przykład w aplikacji pokazanej w sekcji [co to jest powiązanie danych?](#what_is_data_binding)  
  
 Na szczęście nadal obowiązuje nasz diagram podstawowy. Jeśli tworzysz powiązanie <xref:System.Windows.Controls.ItemsControl> do kolekcji, diagram wygląda następująco:  
  
 ![Diagram, który pokazuje obiekt ItemsControl powiązań danych.](./media/data-binding-overview/data-binding-itemscontrol.png)  
  
 Jak pokazano na tym diagramie, aby powiązać <xref:System.Windows.Controls.ItemsControl> obiekt kolekcji, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> właściwość jest właściwością do użycia. <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> Właściwość można traktować jako zawartość <xref:System.Windows.Controls.ItemsControl>. Należy zauważyć, że powiązanie <xref:System.Windows.Data.BindingMode.OneWay> jest <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> spowodowane tym, <xref:System.Windows.Data.BindingMode.OneWay> że właściwość obsługuje powiązanie domyślnie.  
  
<a name="how_to_implement_collections"></a>   
### <a name="how-to-implement-collections"></a>Jak zaimplementować Kolekcje  
 Można wyliczyć wszystkie kolekcje, które implementują <xref:System.Collections.IEnumerable> interfejs. Jednak aby skonfigurować powiązania dynamiczne, tak aby wstawienia lub usunięcia w kolekcji były aktualizowane [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] automatycznie, kolekcja musi <xref:System.Collections.Specialized.INotifyCollectionChanged> implementować interfejs. Ten interfejs uwidacznia zdarzenie, które powinno być wywoływane za każdym razem, gdy źródłowa kolekcja ulegnie zmianie.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]udostępnia klasę, która jest wbudowaną implementacją zbierania danych, która <xref:System.Collections.Specialized.INotifyCollectionChanged> uwidacznia interfejs. <xref:System.Collections.ObjectModel.ObservableCollection%601> Należy pamiętać, że aby w pełni obsługiwał transfer wartości danych z obiektów źródłowych do obiektów docelowych, każdy obiekt w kolekcji, który obsługuje właściwości możliwe do <xref:System.ComponentModel.INotifyPropertyChanged> powiązania, musi również zaimplementować interfejs. Aby uzyskać więcej informacji, zobacz [Omówienie źródeł powiązań](binding-sources-overview.md).  
  
 Przed zaimplementowaniem własnej kolekcji należy rozważyć <xref:System.Collections.ObjectModel.ObservableCollection%601> użycie lub jedną z istniejących klas kolekcji, takich jak <xref:System.Collections.Generic.List%601>, <xref:System.Collections.ObjectModel.Collection%601>, i <xref:System.ComponentModel.BindingList%601>, między innymi. Jeśli masz zaawansowany scenariusz i chcesz zaimplementować swoją własną kolekcję, rozważ użycie <xref:System.Collections.IList>, która zapewnia nieogólną kolekcję obiektów, do których można uzyskać dostęp za pomocą indeksu, i w ten sposób najlepszą wydajność.  
  
<a name="collection_views"></a>   
### <a name="collection-views"></a>Widoki kolekcji  
 Gdy obiekt <xref:System.Windows.Controls.ItemsControl> jest powiązany z kolekcją danych, można sortować, filtrować lub grupować dane. W tym celu należy użyć widoków kolekcji, które są klasami, które implementują <xref:System.ComponentModel.ICollectionView> interfejs.  

#### <a name="what-are-collection-views"></a>Co to są widoki kolekcji?  
 Widok kolekcji to warstwa znajdująca się na początku kolekcji źródłowej powiązania, która umożliwia nawigowanie i wyświetlanie kolekcji źródłowej w oparciu o zapytania sortowania, filtrowania i grup, bez konieczności zmiany samej źródłowej kolekcji. Widok kolekcji utrzymuje również wskaźnik do bieżącego elementu w kolekcji. Jeśli kolekcja źródłowa implementuje <xref:System.Collections.Specialized.INotifyCollectionChanged> interfejs, zmiany zgłoszone <xref:System.Collections.Specialized.INotifyCollectionChanged.CollectionChanged> przez zdarzenie są propagowane do widoków.  
  
 Ponieważ widoki nie zmieniają źródłowej kolekcji źródłowej, do każdej kolekcji źródłowej można skojarzyć wiele widoków. Na przykład może istnieć Kolekcja obiektów *zadań* . Korzystając z widoków, można wyświetlać te same dane na różne sposoby. Na przykład po lewej stronie strony możesz chcieć pokazać zadania posortowane według priorytetu i po prawej stronie pogrupowane według obszaru.  
  
<a name="how_to_create_a_view"></a>   
#### <a name="how-to-create-a-view"></a>Jak utworzyć widok  
 Jednym ze sposobów tworzenia i używania widoku jest bezpośrednie utworzenie wystąpienia obiektu widoku, a następnie użycie go jako źródła powiązania. Rozważmy na przykład aplikację [demonstracyjną wiązania danych](https://go.microsoft.com/fwlink/?LinkID=163703) pokazaną w sekcji [co to jest powiązanie danych](#what_is_data_binding) . Aplikacja jest zaimplementowana w taki <xref:System.Windows.Controls.ListBox> sposób, że tworzy powiązania z widokiem w kolekcji danych zamiast bezpośrednio kolekcji danych. Poniższy przykład jest wyodrębniany z aplikacji [demonstracyjnej powiązania danych](https://go.microsoft.com/fwlink/?LinkID=163703) . Klasa jest serwerem proxy klasy, która dziedziczy z <xref:System.Windows.Data.CollectionView>. <xref:System.Windows.Data.CollectionViewSource> [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] W tym konkretnym przykładzie <xref:System.Windows.Data.CollectionViewSource.Source%2A> widok jest powiązany z kolekcją *AuctionItems* (typu <xref:System.Collections.ObjectModel.ObservableCollection%601>) bieżącego obiektu aplikacji.  
  
 [!code-xaml[DataBindingLab#WindowResources1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#windowresources1)]  
[!code-xaml[DataBindingLab#CollectionViewSource](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#collectionviewsource)]  
[!code-xaml[DataBindingLab#WindowResources2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#windowresources2)]  
  
 *ListingDataView* zasobów następnie służy jako źródło powiązań dla elementów w aplikacji, takich jak <xref:System.Windows.Controls.ListBox>:  
  
 [!code-xaml[DataBindingLab#Master1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master1)]  
[!code-xaml[DataBindingLab#Master2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master2)]  
  
 Aby utworzyć inny widok dla tej samej kolekcji, można utworzyć inne <xref:System.Windows.Data.CollectionViewSource> wystąpienie i nadać mu inną `x:Key` nazwę.  
  
 W poniższej tabeli przedstawiono, które typy danych widoku są tworzone jako domyślny widok kolekcji lub <xref:System.Windows.Data.CollectionViewSource> na podstawie typu kolekcji źródłowej.  
  
|Typ kolekcji źródłowej|Typ widoku kolekcji|Uwagi|  
|----------------------------|--------------------------|-----------|  
|<xref:System.Collections.IEnumerable>|Typ wewnętrzny oparty na<xref:System.Windows.Data.CollectionView>|Nie można grupować elementów.|  
|<xref:System.Collections.IList>|<xref:System.Windows.Data.ListCollectionView>|Najlepszy.|  
|<xref:System.ComponentModel.IBindingList>|<xref:System.Windows.Data.BindingListCollectionView>||  
  
##### <a name="using-a-default-view"></a>Korzystanie z widoku domyślnego  
 Określanie widoku kolekcji jako źródła powiązania jest jednym ze sposobów tworzenia i używania widoku kolekcji. WPF tworzy również domyślny widok kolekcji dla każdej kolekcji używanej jako źródło powiązania. Jeśli powiążesz bezpośrednio z kolekcją, program WPF tworzy powiązanie z widokiem domyślnym. Należy zauważyć, że ten widok domyślny jest współużytkowany przez wszystkie powiązania z tą samą kolekcją, więc zmiana została wprowadzona w widoku domyślnym przez jedną kontrolkę powiązaną lub kod (na przykład sortowanie lub zmiana w bieżącym wskaźniku elementu, omówiona później) jest odzwierciedlona we wszystkich innych powiązaniach z tą samą kolekcją.  
  
 Aby uzyskać widok domyślny, należy użyć <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> metody. Aby zapoznać się z przykładem, zobacz temat [pobieranie widoku domyślnego kolekcji danych](how-to-get-the-default-view-of-a-data-collection.md).  
  
##### <a name="collection-views-with-adonet-datatables"></a>Widoki kolekcji z ADO.NET DataTables  
 Aby zwiększyć wydajność, widoki kolekcji dla ADO.NET <xref:System.Data.DataTable> lub <xref:System.Data.DataView> obiektów delegatów <xref:System.Data.DataView>sortowania i filtrowania do. Powoduje to, że sortowanie i filtrowanie ma być współużytkowane przez wszystkie widoki kolekcji źródła danych. Aby umożliwić każdemu widokowi kolekcji sortowanie i filtrowanie niezależnie, zainicjuj każdy widok kolekcji własnym <xref:System.Data.DataView> obiektem.  
  
#### <a name="sorting"></a>Sortowanie  
 Jak wspomniano wcześniej, widoki mogą zastosować porządek sortowania do kolekcji. Ponieważ istnieje w źródłowej kolekcji, dane mogą lub nie mieć odpowiedniej, powiązanej kolejności. Widok nad kolekcją pozwala na nakładanie zamówienia lub zmianę kolejności domyślnej na podstawie podanych kryteriów porównania. Ponieważ jest to oparty na kliencie widok danych, typowym scenariuszem jest to, że użytkownik może chcieć sortować kolumny danych tabelarycznych według wartości, do której odnosi się kolumna. Korzystając z widoków, można zastosować takie sortowanie oparte na użytkowniku, ponownie bez wprowadzania jakichkolwiek zmian w źródłowej kolekcji, a nawet w przypadku ponowienia kwerendy zawartości kolekcji. Aby zapoznać się z przykładem, zobacz [Sortuj kolumnę GridView po kliknięciu nagłówka](../controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md).  
  
 W poniższym przykładzie przedstawiono logikę sortowania "Sortuj według kategorii i daty" <xref:System.Windows.Controls.CheckBox> aplikacji [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] w sekcji [co to jest powiązanie danych](#what_is_data_binding) :  
  
 [!code-csharp[DataBindingLab#8](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#8)]
 [!code-vb[DataBindingLab#8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#8)]  
  
#### <a name="filtering"></a>Filtrowanie  
 Widoki mogą również stosować filtr do kolekcji. Oznacza to, że mimo że element może istnieć w kolekcji, ten konkretny widok jest przeznaczony do wyświetlania tylko pewnego podzestawu pełnej kolekcji. Można filtrować warunek w danych. Na przykład, tak jak w przypadku aplikacji w sekcji [co to jest powiązanie danych?](#what_is_data_binding) "Pokaż tylko opłaty" <xref:System.Windows.Controls.CheckBox> zawiera logikę do odfiltrowania elementów, które mają koszt $25 lub więcej. Poniższy kod jest wykonywany w celu ustawienia *ShowOnlyBargainsFilter* jako <xref:System.Windows.Data.CollectionViewSource.Filter> programu obsługi <xref:System.Windows.Controls.CheckBox> zdarzeń, gdy jest wybrany:  
  
 [!code-csharp[DataBindingLab#10](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#10)]
 [!code-vb[DataBindingLab#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#10)]  
  
 Program obsługi zdarzeń *ShowOnlyBargainsFilter* ma następującą implementację:  
  
 [!code-csharp[DataBindingLab#5](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#5)]
 [!code-vb[DataBindingLab#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#5)]  
  
 Jeśli używasz jednej z <xref:System.Windows.Data.CollectionView> klas bezpośrednio <xref:System.Windows.Data.CollectionViewSource>zamiast <xref:System.Windows.Data.CollectionView.Filter%2A> , użyj właściwości, aby określić wywołanie zwrotne. Aby zapoznać się z przykładem, zobacz [filtrowanie danych w widoku](how-to-filter-data-in-a-view.md).  
  
#### <a name="grouping"></a>Grupowanie  
 Z wyjątkiem wewnętrznej klasy, która przegląda <xref:System.Collections.IEnumerable> kolekcję, wszystkie widoki kolekcji obsługują funkcje grupowania, co umożliwia użytkownikowi partycjonowanie kolekcji w widoku kolekcji w grupach logicznych. Grupy mogą być jawne, gdzie użytkownik dostarcza listę grup lub niejawną, w której grupy są generowane dynamicznie w zależności od danych.  
  
 Poniższy przykład przedstawia logikę "Grupuj według kategorii" <xref:System.Windows.Controls.CheckBox>:  
  
 [!code-csharp[DataBindingLab#6](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#6)]
 [!code-vb[DataBindingLab#6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#6)]  
  
 Aby poznać inny przykład grupowania, zobacz [Grupuj elementy w ListView, który implementuje GridView](../controls/how-to-group-items-in-a-listview-that-implements-a-gridview.md).  
  
#### <a name="current-item-pointers"></a>Wskaźniki bieżącego elementu  
 Widoki obsługują również koncepcję bieżącego elementu. Możesz nawigować przez obiekty w widoku kolekcji. Podczas nawigowania, przenosisz wskaźnik elementu, który umożliwia pobranie obiektu, który istnieje w danej lokalizacji w kolekcji. Aby zapoznać się z przykładem, zobacz [nawigowanie po obiektach w CollectionView danych](how-to-navigate-through-the-objects-in-a-data-collectionview.md).  
  
 Ponieważ WPF tworzy powiązanie z kolekcją tylko przy użyciu widoku (określony przez Ciebie widok lub widok domyślny kolekcji), wszystkie powiązania z kolekcjami mają aktualny wskaźnik elementu. Po powiązaniu do widoku znak ukośnika ("/") w `Path` wartości wyznacza bieżący element widoku. W poniższym przykładzie kontekst danych jest widokiem kolekcji. Pierwszy wiersz wiąże się z kolekcją. Drugi wiersz tworzy powiązanie z bieżącym elementem w kolekcji. Trzeci wiersz wiąże się `Description` z właściwością bieżącego elementu w kolekcji.  
  
```xaml  
<Button Content="{Binding }" />  
<Button Content="{Binding Path=/}" />  
<Button Content="{Binding Path=/Description}" />   
```  
  
 Składnia ukośnika i właściwości może być również skumulowana w celu przechodzenia do hierarchii kolekcji. Poniższy przykład tworzy powiązanie z bieżącym elementem kolekcji o nazwie `Offices`, która jest właściwością bieżącego elementu kolekcji źródłowej.  
  
```xaml  
<Button Content="{Binding /Offices/}" />  
```  
  
 Na wskaźnik bieżącego elementu może mieć wpływ każde sortowanie lub filtrowanie, które jest stosowane do kolekcji. Sortowanie zachowuje bieżący wskaźnik elementu na ostatnim wybranym elemencie, ale widok kolekcji jest teraz restrukturyzacją. (Prawdopodobnie wybrany element znajdował się na początku listy, ale teraz wybrany element może znajdować się w środku). Filtrowanie zachowuje wybrany element, jeśli zaznaczenie pozostanie w widoku po filtrowaniu. W przeciwnym razie wskaźnik bieżącego elementu jest ustawiany na pierwszy element filtrowanego widoku kolekcji.  
  
<a name="master_detail_scenario"></a>   
#### <a name="master-detail-binding-scenario"></a>Scenariusz powiązań wzorzec-szczegóły  
 Pojęcie bieżącego elementu jest przydatne nie tylko w przypadku nawigacji elementów w kolekcji, ale również dla scenariusza powiązania szczegółów wzorca. Rozważ ponowne użycie [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] aplikacji w sekcji [co to jest powiązanie danych](#what_is_data_binding) . W tej aplikacji wybór w <xref:System.Windows.Controls.ListBox> obszarze określa zawartość wyświetlaną <xref:System.Windows.Controls.ContentControl>w. Aby umieścić ją w inny sposób, gdy <xref:System.Windows.Controls.ListBox> element jest zaznaczony <xref:System.Windows.Controls.ContentControl> , pokazuje szczegóły wybranego elementu.  
  
 Scenariusz wzorzec-szczegóły można zaimplementować po prostu, mając co najmniej dwie kontrolki powiązane z tym samym widokiem. Poniższy przykład z pokazu [powiązania danych](https://go.microsoft.com/fwlink/?LinkID=163703) <xref:System.Windows.Controls.ListBox> przedstawia znaczniki i są <xref:System.Windows.Controls.ContentControl> wyświetlane w aplikacji [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] w sekcji [co to jest powiązanie danych?](#what_is_data_binding)  
  
 [!code-xaml[DataBindingLab#Master1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master1)]  
[!code-xaml[DataBindingLab#Master2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master2)]  
[!code-xaml[DataBindingLab#Detail](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#detail)]  
  
 Zwróć uwagę, że obie kontrolki są powiązane z tym samym źródłem, *listingDataView* zasób statyczny (Zobacz definicję tego zasobu w [sekcji Jak utworzyć widok](#how_to_create_a_view)). Dzieje się tak, ponieważ gdy pojedynczy obiekt ( <xref:System.Windows.Controls.ContentControl> w tym przypadku) jest powiązany z widokiem kolekcji, automatycznie wiąże <xref:System.Windows.Data.CollectionView.CurrentItem%2A> się z widokiem. Należy zauważyć <xref:System.Windows.Data.CollectionViewSource> , że obiekty automatycznie synchronizują walutę i zaznaczenie. Jeśli formant listy nie jest powiązany z <xref:System.Windows.Data.CollectionViewSource> obiektem, jak w tym przykładzie, należy ustawić jego <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> Właściwość `true` na, aby to działało.  
  
 Aby zapoznać się z innymi przykładami, zobacz [Powiązywanie z kolekcją i wyświetlanie informacji na podstawie wyboru](how-to-bind-to-a-collection-and-display-information-based-on-selection.md) i [Używanie wzorca-szczegóły wzorca z danymi hierarchicznymi](how-to-use-the-master-detail-pattern-with-hierarchical-data.md).  
  
 Być może zauważono, że powyższy przykład używa szablonu. W rzeczywistości dane nie są wyświetlane w żądany sposób bez użycia szablonów (jawnie używany przez <xref:System.Windows.Controls.ContentControl> i jeden niejawnie używany <xref:System.Windows.Controls.ListBox>przez). Teraz przejdźmy do tworzenia szablonów danych w następnej sekcji.  
  
<a name="data_templating"></a>   
## <a name="data-templating"></a>Tworzenia szablonów danych  
 Bez użycia szablonów danych Nasza aplikacja [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] w sekcji [co to jest powiązanie danych?](#what_is_data_binding) będzie wyglądać następująco:  
  
 ![Demonstracja powiązania danych bez szablonów danych](./media/data-binding-overview/data-binding-demo-templates.png)  
  
 Jak pokazano w przykładzie w poprzedniej sekcji, zarówno <xref:System.Windows.Controls.ListBox> formant, <xref:System.Windows.Controls.ContentControl> jak i są powiązane z całymi obiektami kolekcji (lub dokładniej, widok nad obiektem kolekcji) *AuctionItem*s. Bez określonych instrukcji dotyczących sposobu wyświetlania zbierania danych program <xref:System.Windows.Controls.ListBox> Wyświetla reprezentację ciągu dla każdego obiektu w źródłowej kolekcji <xref:System.Windows.Controls.ContentControl> i wyświetla ciąg reprezentujący obiekt, z którym jest powiązany.  
  
 Aby rozwiązać ten problem, aplikacja definiuje <xref:System.Windows.DataTemplate>s. Jak pokazano w przykładzie w poprzedniej sekcji, <xref:System.Windows.Controls.ContentControl> jawnie używa *detailsProductListingTemplate*<xref:System.Windows.DataTemplate>. Kontrolka niejawnie używa następujących <xref:System.Windows.DataTemplate> danych podczas wyświetlania obiektów *AuctionItem* w kolekcji: <xref:System.Windows.Controls.ListBox>  
  
 [!code-xaml[DataBindingLab#AuctionItemDataTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#auctionitemdatatemplate)]  
  
 Korzystając z tych dwóch <xref:System.Windows.DataTemplate>s, wynikowy interfejs użytkownika jest wyświetlany w sekcji [co to jest powiązanie danych](#what_is_data_binding) . Jak widać na tym zrzucie ekranu, poza umożliwieniem umieszczania danych w kontrolkach, <xref:System.Windows.DataTemplate>można definiować atrakcyjne wizualizacje danych. Na <xref:System.Windows.DataTrigger>przykład s są używane w powyższych <xref:System.Windows.DataTemplate> , dzięki czemu *AuctionItem*s z wartością *SpecialFeatures* z wyróżnieniem będzie *wyświetlana* z pomarańczowym obramowaniem i gwiazdką.  
  
 Aby uzyskać więcej informacji na temat szablonów danych, zobacz [Omówienie tworzenia szablonów danych](data-templating-overview.md).  
  
<a name="data_validation"></a>   
## <a name="data-validation"></a>Sprawdzanie poprawności danych  
  
 Większość aplikacji, które wprowadzają dane wejściowe użytkownika, musi mieć logikę sprawdzania poprawności, aby upewnić się, że użytkownik wprowadził oczekiwane informacje. Sprawdzenia poprawności mogą opierać się na typie, zakresie, formacie lub innych wymaganiach specyficznych dla aplikacji. W tej sekcji omówiono sposób działania walidacji danych [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]w programie.  
  
### <a name="associating-validation-rules-with-a-binding"></a>Kojarzenie reguł walidacji z powiązaniem  
 Model powiązania <xref:System.Windows.Data.Binding.ValidationRules%2A> <xref:System.Windows.Data.Binding> danych umożliwia skojarzenie z obiektem. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Na przykład poniższy <xref:System.Windows.Controls.TextBox> przykład tworzy powiązanie z właściwością o nazwie `StartPrice` i <xref:System.Windows.Data.Binding.ValidationRules%2A?displayProperty=nameWithType> dodaje <xref:System.Windows.Controls.ExceptionValidationRule> obiekt do właściwości.  
  
 [!code-xaml[DataBindingLab#DefaultValidation](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/AddProductWindow.xaml#defaultvalidation)]  
  
 <xref:System.Windows.Controls.ValidationRule> Obiekt sprawdza, czy wartość właściwości jest prawidłowa. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ma następujące dwa typy wbudowanych <xref:System.Windows.Controls.ValidationRule> obiektów:  
  
- <xref:System.Windows.Controls.ExceptionValidationRule> Sprawdza wyjątki zgłoszone podczas aktualizacji właściwości źródła powiązania. W poprzednim przykładzie `StartPrice` jest typu Integer. Gdy użytkownik wprowadzi wartość, której nie można przekonwertować na liczbę całkowitą, zostanie zgłoszony wyjątek, co spowoduje oznaczenie powiązania jako nieprawidłowy. Alternatywna składnia służąca do <xref:System.Windows.Controls.ExceptionValidationRule> ustawienia jawnie polega na <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> ustawieniu właściwości `true` <xref:System.Windows.Data.Binding> na obiekt lub <xref:System.Windows.Data.MultiBinding> .  
  
- Obiekt sprawdza błędy zgłaszane przez obiekty, które <xref:System.ComponentModel.IDataErrorInfo> implementują interfejs. <xref:System.Windows.Controls.DataErrorValidationRule> Aby zapoznać się z przykładem użycia tej reguły walidacji, zobacz <xref:System.Windows.Controls.DataErrorValidationRule>. Alternatywna składnia służąca do <xref:System.Windows.Controls.DataErrorValidationRule> ustawienia jawnie polega na <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> ustawieniu właściwości `true` <xref:System.Windows.Data.Binding> na obiekt lub <xref:System.Windows.Data.MultiBinding> .  
  
 Możesz również utworzyć własną regułę walidacji, wyprowadzając ją <xref:System.Windows.Controls.ValidationRule> z klasy i <xref:System.Windows.Controls.ValidationRule.Validate%2A> implementując metodę. W poniższym przykładzie przedstawiono regułę używaną przez *listę Dodaj produkt* "Data rozpoczęcia" <xref:System.Windows.Controls.TextBox> z sekcji [co to jest powiązanie danych](#what_is_data_binding) :  
  
 [!code-csharp[DataBindingLab#2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/FutureDateRule.cs#2)]
 [!code-vb[DataBindingLab#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/FutureDateRule.vb#2)]  
  
 *StartDateEntryForm*<xref:System.Windows.Controls.TextBox> używa tego *FutureDateRule*, jak pokazano w następującym przykładzie:  
  
 [!code-xaml[DataBindingLab#CustomValidation](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/AddProductWindow.xaml#customvalidation)]  
  
 Należy pamiętać, że <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> ponieważ wartość <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>to, aparat powiązań aktualizuje wartość źródłową przy każdym naciśnięciu klawisza, co oznacza, że <xref:System.Windows.Data.Binding.ValidationRules%2A> sprawdza wszystkie reguły w kolekcji przy każdym naciśnięciu klawisza. Omawiamy tę procedurę w sekcji proces walidacji.  
  
<a name="invalidation_feedback"></a>   
### <a name="providing-visual-feedback"></a>Zapewnianie opinii wizualnych  
 Jeśli użytkownik wprowadzi nieprawidłową wartość, może być konieczne podanie pewnych informacji zwrotnych dotyczących błędu w aplikacji [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Jednym ze sposobów zapewnienia takiej opinii jest ustawienie <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType> właściwości dołączonej na niestandardową. <xref:System.Windows.Controls.ControlTemplate> Jak pokazano w poprzedniej podsekcji, *StartDateEntryForm* <xref:System.Windows.Controls.TextBox> używa <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> metody o nazwie *validationTemplate*. W poniższym przykładzie przedstawiono definicję elementu *validationTemplate*:  
  
 [!code-xaml[DataBindingLab#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/AddProductWindow.xaml#1)]  
  
 <xref:System.Windows.Controls.AdornedElementPlaceholder> Element określa, gdzie powinna zostać umieszczona kontrolka.  
  
 Ponadto można również użyć <xref:System.Windows.Controls.ToolTip> , aby wyświetlić komunikat o błędzie. Zarówno *StartDateEntryForm* , jak i *StartPriceEntryForm*<xref:System.Windows.Controls.TextBox>es używają <xref:System.Windows.Controls.ToolTip> stylu *textStyleTextBox*, który tworzy, który wyświetla komunikat o błędzie. W poniższym przykładzie przedstawiono definicję *textStyleTextBox*. Dołączona właściwość <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true` wtedy, gdy co najmniej jedno powiązanie we właściwościach elementu powiązanego jest w błędzie.  
  
 [!code-xaml[DataBindingLab#14](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#14)]  
  
 Przy użyciu niestandardowych <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> <xref:System.Windows.Controls.ToolTip>i, *StartDateEntryForm* <xref:System.Windows.Controls.TextBox> wygląda następująco, gdy występuje błąd walidacji:  
  
 ![Błąd walidacji powiązania danych](./media/databindingdemo-validation.PNG "DataBindingDemo_Validation")  
  
 Jeśli masz skojarzone reguły walidacji, ale nie <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> określisz w kontrolce powiązanej, zostanie użyta wartość domyślna <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> do powiadomienia użytkowników o błędzie walidacji. <xref:System.Windows.Data.Binding> Wartość domyślna <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> to szablon kontrolki, który definiuje czerwone obramowanie w warstwie modułu definiowania układu. Przy użyciu wartości <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> domyślnej <xref:System.Windows.Controls.ToolTip>i, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] *StartPriceEntryForm* <xref:System.Windows.Controls.TextBox> wygląda następująco, gdy występuje błąd walidacji:  
  
 ![Błąd walidacji powiązania danych](./media/databindingdemo-validationdefault.PNG "DataBindingDemo_ValidationDefault")  
  
 Aby zapoznać się z przykładem sposobu zapewnienia logiki do sprawdzania poprawności wszystkich kontrolek w oknie dialogowym, zobacz sekcję niestandardowe okna dialogowe w oknach dialogowych [Przegląd](../app-development/dialog-boxes-overview.md).  
  
### <a name="validation-process"></a>Proces weryfikacji  
 Walidacja zwykle odbywa się, gdy wartość docelowa jest transferowana do właściwości source powiązania. Ma to miejsce <xref:System.Windows.Data.BindingMode.TwoWay> i <xref:System.Windows.Data.BindingMode.OneWayToSource> powiązania. Aby ponownie wykonać iterację, co powoduje, że aktualizacja źródłowa zależy od wartości <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> właściwości, zgodnie z opisem w sekcji [co to są aktualizacje źródła wyzwalaczy](#what_triggers_source_updates) .  
  
 Poniżej opisano proces *sprawdzania poprawności* . Należy pamiętać, że jeśli w dowolnym momencie w trakcie tego procesu wystąpi błąd walidacji lub inny typ błędu, proces zostanie zatrzymany.  
  
1. Aparat powiązań sprawdza, czy istnieją jakieś obiekty niestandardowe <xref:System.Windows.Controls.ValidationRule> <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> zdefiniowane <xref:System.Windows.Controls.ValidationStep.RawProposedValue> dla <xref:System.Windows.Controls.ValidationRule.Validate%2A> tego <xref:System.Windows.Data.Binding>elementu, w takim przypadku wywołuje metodę na każdym <xref:System.Windows.Controls.ValidationRule> z nich do momentu, gdy jeden z nich zostanie uruchomiony w wystąpieniu błędu lub dopóki wszystkie z nich zakończą się powodzeniem.  
  
2. Aparat powiązań następnie wywołuje konwerter, jeśli taki istnieje.  
  
3. Jeśli konwerter zakończy się pomyślnie, aparat powiązań sprawdza, czy istnieją jakieś obiekty <xref:System.Windows.Controls.ValidationRule> niestandardowe <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> zdefiniowane <xref:System.Windows.Controls.ValidationStep.ConvertedProposedValue> dla <xref:System.Windows.Controls.ValidationRule.Validate%2A> tego <xref:System.Windows.Data.Binding>elementu, w takim przypadku wywołuje metodę dla każdej z nich <xref:System.Windows.Controls.ValidationRule> . Ustawia do <xref:System.Windows.Controls.ValidationStep.ConvertedProposedValue> momentu, aż jeden z nich zostanie uruchomiony w błąd lub do momentu, aż wszystkie z nich zakończą się powodzeniem. <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A>  
  
4. Aparat powiązań ustawia właściwość source.  
  
5. Aparat powiązań sprawdza, czy istnieją jakieś obiekty niestandardowe <xref:System.Windows.Controls.ValidationRule> <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> zdefiniowane <xref:System.Windows.Controls.ValidationStep.UpdatedValue> dla <xref:System.Windows.Controls.ValidationRule.Validate%2A> tego <xref:System.Windows.Data.Binding>elementu, w takim przypadku wywołuje metodę dla każdej <xref:System.Windows.Controls.ValidationRule> , która ma <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> ustawioną wartość <xref:System.Windows.Controls.ValidationStep.UpdatedValue> do momentu, gdy jeden z nich zostanie uruchomiony w błąd lub do momentu, aż wszystkie z nich zostaną zakończone. Jeśli obiekt <xref:System.Windows.Controls.DataErrorValidationRule> jest skojarzony z powiązaniem <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> i ma ustawioną wartość domyślną, <xref:System.Windows.Controls.ValidationStep.UpdatedValue>program <xref:System.Windows.Controls.DataErrorValidationRule> jest sprawdzany w tym punkcie. Jest to również punkt, gdy <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> `true` są zaznaczone powiązania, które mają ustawioną wartość.  
  
6. Aparat powiązań sprawdza, czy istnieją jakieś obiekty niestandardowe <xref:System.Windows.Controls.ValidationRule> <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> zdefiniowane <xref:System.Windows.Controls.ValidationStep.CommittedValue> dla <xref:System.Windows.Controls.ValidationRule.Validate%2A> tego <xref:System.Windows.Data.Binding>elementu, w takim przypadku wywołuje metodę dla każdej <xref:System.Windows.Controls.ValidationRule> , która ma <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> ustawioną wartość <xref:System.Windows.Controls.ValidationStep.CommittedValue> do momentu, gdy jeden z nich zostanie uruchomiony w błąd lub do momentu, aż wszystkie z nich zostaną zakończone.  
  
 Jeśli w <xref:System.Windows.Controls.ValidationRule> dowolnym momencie w trakcie tego procesu nie zostanie przekazany, aparat powiązań <xref:System.Windows.Controls.ValidationError> tworzy obiekt <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> i dodaje go do kolekcji powiązanego elementu. Przed uruchomieniem <xref:System.Windows.Controls.ValidationRule> przez aparat powiązań obiektów w którymkolwiek z powyższych kroków usuwa on wszystkie <xref:System.Windows.Controls.ValidationError> elementy <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> , które zostały dodane do dołączonej właściwości elementu powiązanego w tym kroku. Na <xref:System.Windows.Controls.ValidationRule> przykład jeśli dla którego <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> jest ustawiona wartość <xref:System.Windows.Controls.ValidationStep.UpdatedValue> niepowodzenie, podczas następnego procesu walidacji <xref:System.Windows.Controls.ValidationRule> aparat powiązań usunie ten <xref:System.Windows.Controls.ValidationError> element bezpośrednio przed wywołaniem, który ma <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> ustawioną wartość <xref:System.Windows.Controls.ValidationStep.UpdatedValue>.  
  
 Gdy <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> nie jest pusty <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> , dołączona właściwość elementu jest ustawiona na `true`. Ponadto, jeśli <xref:System.Windows.Data.Binding.NotifyOnValidationError%2A> Właściwość <xref:System.Windows.Data.Binding> jest ustawiona na `true`, aparat powiązań wywołuje <xref:System.Windows.Controls.Validation.Error?displayProperty=nameWithType> dołączone zdarzenie w elemencie.  
  
 Należy również zauważyć, że prawidłowy transfer wartości w obu kierunkach (element docelowy ze źródłem lub źródłem do lokalizacji docelowej <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> ) czyści załączoną właściwość.  
  
 Jeśli powiązanie <xref:System.Windows.Controls.ExceptionValidationRule> jest skojarzone z nim lub <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> miało ustawioną `true` właściwość, a wyjątek jest zgłaszany, gdy aparat powiązań ustawia źródło, <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>aparat powiązań sprawdzi, czy istnieje. Możesz użyć <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A> wywołania zwrotnego, aby zapewnić niestandardową procedurę obsługi wyjątków. Jeśli element nie <xref:System.Windows.Data.Binding> <xref:System.Windows.Controls.ValidationError> <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> jest określony w, aparat powiązań tworzy wyjątek z wyjątkiem i dodaje go do kolekcji powiązanego elementu. <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>  
  
## <a name="debugging-mechanism"></a>Mechanizm debugowania  
 Można ustawić przyłączoną Właściwość <xref:System.Diagnostics.PresentationTraceSources.TraceLevel%2A?displayProperty=nameWithType> obiektu powiązanego z powiązaniem, aby otrzymywać informacje o stanie określonego powiązania.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.DataErrorValidationRule>
- [Nowości w WPF w wersji 4.5](../getting-started/whats-new.md)
- [Powiązywanie z wynikami zapytania LINQ](how-to-bind-to-the-results-of-a-linq-query.md)
- [Powiązanie danych](../advanced/optimizing-performance-data-binding.md)
- [Pokaz powiązania danych](https://go.microsoft.com/fwlink/?LinkID=163703)
- [Tematy z instrukcjami](data-binding-how-to-topics.md)
- [Powiązywanie ze źródłem danych ADO.NET](how-to-bind-to-an-ado-net-data-source.md)
