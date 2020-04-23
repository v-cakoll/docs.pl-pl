---
title: Omówienie powiązań danych
description: Dowiedz się więcej o różnych źródłach danych, które można dodać do projektu w programie Windows Presentation Foundation for .NET Core. Źródła danych mogą być powiązane z elementami XAML w celu tworzenia aplikacji dynamicznych.
author: thraka
ms.date: 09/19/2019
ms.author: adegeo
dev_langs:
- csharp
- vb
ms.openlocfilehash: 7f17ff094a35c04ba880c87c6966d7d249817516
ms.sourcegitcommit: b75a45f0cfe012b71b45dd9bf723adf32369d40c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "82072012"
---
# <a name="data-binding-overview-in-wpf"></a>Omówienie powiązania danych w wyw.

Powiązanie danych w programie Windows Presentation Foundation (WPF) zapewnia prosty i spójny sposób prezentowania danych i interakcji z nimi. Elementy mogą być powiązane z danymi z różnych źródeł danych w postaci obiektów .NET i XML. Wszelkie <xref:System.Windows.Controls.ContentControl> takie <xref:System.Windows.Controls.Button> jak <xref:System.Windows.Controls.ItemsControl>i <xref:System.Windows.Controls.ListBox> wszelkie <xref:System.Windows.Controls.ListView>, takie jak i , mają wbudowaną funkcjonalność, aby umożliwić elastyczne stylizacje pojedynczych elementów danych lub kolekcji elementów danych. Widoki sortowania, filtrowania i grup mogą być generowane na podstawie danych.

Funkcja wiązania danych w WPF WPF ma kilka zalet w stosunku do tradycyjnych modeli, w tym nieodłączne wsparcie dla powiązania danych przez szeroki zakres właściwości, elastyczne reprezentacji interfejsu użytkownika danych i czyste oddzielenie logiki biznesowej od interfejsu użytkownika.

W tym artykule najpierw omówiono pojęcia podstawowe do powiązania <xref:System.Windows.Data.Binding> danych WPF, a następnie obejmuje użycie klasy i innych funkcji powiązania danych.

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="what-is-data-binding"></a>Co to jest powiązanie danych?

Powiązanie danych to proces, który ustanawia połączenie między interfejsem użytkownika aplikacji a wyświetlanymi danymi. Jeśli powiązanie ma poprawne ustawienia, a dane zapewniają odpowiednie powiadomienia, gdy dane zmienią swoją wartość, elementy, które są powiązane z danymi, automatycznie odzwierciedlają zmiany. Powiązanie danych może również oznaczać, że jeśli zewnętrzna reprezentacja danych w elemencie ulegnie zmianie, dane bazowe mogą być automatycznie aktualizowane w celu odzwierciedlenia zmiany. Na przykład jeśli użytkownik edytuje wartość `TextBox` w elemencie, wartość danych bazowych jest automatycznie aktualizowana w celu odzwierciedlenia tej zmiany.

Typowym użyciem powiązania danych jest umieszczenie danych serwera lub konfiguracji lokalnej w formularzach lub innych formantach interfejsu użytkownika. W WPF WPF ta koncepcja jest rozwijana w celu włączenia wiązania szeroki zakres właściwości do różnych źródeł danych. W WPF WPF właściwości zależności elementów mogą być powiązane z obiektami .NET (w tym ADO.NET obiektów lub obiektów skojarzonych z usługami sieci Web i właściwości sieci Web) i danych XML.

Na przykład powiązania danych, spójrz na następującej aplikacji interfejsu użytkownika z [demo powiązania danych][data-binding-demo], który wyświetla listę przedmiotów aukcji.

![Przykładowy zrzut ekranu wiązania danych](./media/data-binding-overview/demo.png "DataBinding_DataBindingDemo")

Aplikacja pokazuje następujące funkcje powiązania danych:

- Zawartość ListBox jest powiązana z kolekcją *obiektów AuctionItem.* Obiekt *Elementu aukcji* ma właściwości, takie jak *Opis*, *StartPrice*, *StartDate*, *Category*, *SpecialFeatures*, i tak dalej.

- Dane *(Obiekty AuctionItem)* wyświetlane `ListBox` w szablonie jest szablon, tak aby opis i bieżąca cena są wyświetlane dla każdego elementu. Szablon jest tworzony przy <xref:System.Windows.DataTemplate>użyciu pliku . Ponadto wygląd każdego przedmiotu zależy od wartości *specialfeatures* *elementu aukcji.* Jeśli wartością *funkcji specjalnych* *elementu aukcji* jest *Kolor,* element ma niebieskie obramowanie. Jeśli wartością jest *Podświetl,* element ma pomarańczowe obramowanie i gwiazdkę. Sekcja [Szablony danych](#data-templating) zawiera informacje o szablonowaniu danych.

- Użytkownik może grupować, filtrować lub `CheckBoxes` sortować dane przy użyciu podanych. Na powyższym obrazku wybierane są **ustawienia Grupy według kategorii** i **Sortuj według kategorii i daty.** `CheckBoxes` Być może zauważyłeś, że dane są pogrupowane na podstawie kategorii produktu, a nazwa kategorii jest w kolejności alfabetycznej. Trudno zauważyć z obrazu, ale elementy są również sortowane według daty rozpoczęcia w każdej kategorii. Sortowanie odbywa się za pomocą *widoku kolekcji*. W sekcji [Binding to collections](#binding-to-collections) omówiono widoki kolekcji.

- Gdy użytkownik wybierze element, <xref:System.Windows.Controls.ContentControl> wyświetli szczegóły wybranego elementu. To doświadczenie jest nazywane *scenariuszem master-detail*. Sekcja [Scenariusz szczegółów wzoru](#master-detail-binding-scenario) zawiera informacje na temat tego typu powiązania.

- Typ właściwości *StartDate* to <xref:System.DateTime>, która zwraca datę zawierającą godzinę do milisekundy. W tej aplikacji użyto niestandardowego konwertera, aby wyświetlić krótszy ciąg daty. Sekcja [Konwersja danych](#data-conversion) zawiera informacje o konwerterach.

Gdy użytkownik wybierze przycisk *Dodaj produkt,* pojawi się następujący formularz.

![Strona Dodaj listę produktów](./media/data-binding-overview/demo-addproductlisting.png "DataBinding_Demo_AddProductListing")

Użytkownik może edytować pola w formularzu, wyświetlić podgląd listy produktów za `Submit` pomocą krótkich lub szczegółowych okienek podglądu i wybrać, aby dodać nową listę produktów. Do nowego wpisu zostaną zastosowane wszystkie istniejące ustawienia grupowania, filtrowania i sortowania. W tym konkretnym przypadku element wprowadzony na powyższym obrazie zostanie wyświetlony jako drugi element w kategorii *Komputer.*

Nie pokazano na tym obrazie jest logika sprawdzania poprawności podana w *daty* <xref:System.Windows.Controls.TextBox>rozpoczęcia . Jeśli użytkownik wprowadzi nieprawidłową datę (nieprawidłowe formatowanie lub datę przeszłą), użytkownik zostanie powiadomiony czerwonym wykrzyknikiem <xref:System.Windows.Controls.ToolTip> obok <xref:System.Windows.Controls.TextBox>pliku . Sekcja [Sprawdzanie poprawności danych](#data-validation) omówiono sposób tworzenia logiki sprawdzania poprawności.

Przed przejściem do różnych funkcji powiązania danych opisane powyżej, najpierw omówimy podstawowe pojęcia, które są krytyczne dla zrozumienia powiązania danych WPF.

## <a name="basic-data-binding-concepts"></a>Podstawowe pojęcia dotyczące wiązań danych

Niezależnie od tego, jaki element są wiążące i charakter źródła danych, każde powiązanie zawsze następuje modelu zilustrowane przez poniższy rysunek.

![Diagram przedstawiający podstawowy model wiązania danych.](./media/data-binding-overview/basic-data-binding-diagram.png)

Jak pokazano na rysunku, powiązanie danych jest zasadniczo pomost między docelowego powiązania i źródła powiązania. Rysunek przedstawia następujące podstawowe pojęcia powiązania danych WPF:

- Zazwyczaj każde powiązanie ma cztery składniki:

  - Obiekt docelowy powiązania.
  - Właściwość docelowa.
  - Źródło powiązania.
  - Ścieżka do wartości w źródle wiązania do użycia.
  
  > Na przykład, jeśli chcesz powiązać `TextBox` zawartość `Employee.Name` a z właściwością, `TextBox`obiekt docelowy <xref:System.Windows.Controls.TextBox.Text%2A> jest , właściwość docelowa jest właściwość, wartość do użycia jest *Name*, a obiekt źródłowy jest *Employee* obiektu.

- Właściwość docelowa musi być właściwością zależności. Większość <xref:System.Windows.UIElement> właściwości są właściwości zależności i większość właściwości zależności, z wyjątkiem tylko do odczytu, domyślnie obsługuje powiązanie danych. (Tylko typy <xref:System.Windows.DependencyObject> uzyskane z może zdefiniować <xref:System.Windows.UIElement> właściwości zależności; `DependencyObject`i wszystkie typy pochodzą od .)

- Chociaż nie pokazano na rysunku, należy zauważyć, że obiekt źródłowy powiązania nie jest ograniczony do niestandardowego obiektu .NET. Powiązanie danych WPF obsługuje dane w postaci obiektów .NET i XML. Aby podać kilka przykładów, źródłem <xref:System.Windows.UIElement>powiązania może być obiekt listy, obiekt ADO.NET lub usługi sieci Web lub XmlNode zawierający dane XML. Aby uzyskać więcej informacji, zobacz [Omówienie źródeł powiązania](../../framework/wpf/data/binding-sources-overview.md).

Należy pamiętać, że podczas ustanawiania powiązania, są wiążące powiązanie obiektu docelowego *do* źródła powiązania. Na przykład jeśli są wyświetlane niektóre podstawowe dane <xref:System.Windows.Controls.ListBox> XML w użyciu `ListBox` powiązania danych, są wiążące z danymi XML.

Aby ustanowić powiązanie, <xref:System.Windows.Data.Binding> należy użyć obiektu. W dalszej części tego artykułu omówiono wiele pojęć skojarzonych z `Binding` i niektóre właściwości i użycie obiektu.

### <a name="direction-of-the-data-flow"></a>Kierunek przepływu danych

Jak wskazano w strzałce na poprzednim rysunku, przepływ danych powiązania może przejść od obiektu docelowego powiązania do źródła powiązania (na przykład wartość źródło zmienia się, gdy użytkownik edytuje wartość a) `TextBox`i/lub ze źródła powiązania do obiektu docelowego powiązania (na przykład `TextBox` zawartość jest aktualizowana o zmiany w źródle powiązania), jeśli źródło powiązania udostępnia odpowiednie powiadomienia.

Aplikacja może umożliwić użytkownikom zmianę danych i propagowanie ich z powrotem do obiektu źródłowego. Możesz też nie chcieć umożliwić użytkownikom aktualizowania danych źródłowych. Przepływ danych można kontrolować, ustawiając plik <xref:System.Windows.Data.Binding.Mode?displayProperty=nameWithType>.

Rysunek ten ilustruje różne typy przepływu danych:

![Przepływ danych wiązania danych](./media/data-binding-overview/databinding-dataflow.png "DataBinding_DataFlow")

- <xref:System.Windows.Data.BindingMode.OneWay>powiązanie powoduje zmiany właściwości źródłowej, aby automatycznie aktualizować właściwość docelową, ale zmiany właściwości docelowej nie są propagowane z powrotem do właściwości źródłowej. Ten typ powiązania jest odpowiedni, jeśli formant jest powiązany jest niejawnie tylko do odczytu. Na przykład można powiązać ze źródłem, takim jak giełdowy znacznik, a może właściwość docelowa nie ma interfejsu sterowania przewidzianego do wprowadzania zmian, takich jak kolor tła powiązany z danymi tabeli. Jeśli nie ma potrzeby monitorowania zmian właściwości docelowej, przy użyciu trybu <xref:System.Windows.Data.BindingMode.OneWay> <xref:System.Windows.Data.BindingMode.TwoWay> wiązania pozwala uniknąć narzutu trybu wiązania.

- <xref:System.Windows.Data.BindingMode.TwoWay>powiązanie powoduje zmiany właściwości źródłowej lub właściwości docelowej, aby automatycznie zaktualizować drugą. Ten typ powiązania jest odpowiedni dla edytowalnych formularzy lub innych w pełni interaktywnych scenariuszy interfejsu użytkownika. Większość właściwości <xref:System.Windows.Data.BindingMode.OneWay> domyślnie powiązania, ale niektóre właściwości zależności (zazwyczaj właściwości formantów <xref:System.Windows.Controls.TextBox.Text?displayProperty=nameWithType> edytowalnych przez użytkownika, takich jak i [CheckBox.IsChecked](xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked) domyślnie do <xref:System.Windows.Data.BindingMode.TwoWay> powiązania. Programowy sposób, aby ustalić, czy właściwość zależności wiąże jednokierunkowe lub dwukierunkowe <xref:System.Windows.DependencyProperty.GetMetadata%2A?displayProperty=nameWithType> domyślnie jest uzyskanie metadanych właściwości z, a następnie sprawdzić wartość logiczną <xref:System.Windows.FrameworkPropertyMetadata.BindsTwoWayByDefault%2A?displayProperty=nameWithType> właściwości.

- <xref:System.Windows.Data.BindingMode.OneWayToSource>jest odwrotnością <xref:System.Windows.Data.BindingMode.OneWay> wiązania; aktualizuje właściwość źródło, gdy zmienia się właściwość docelowa. Jednym z przykładowych scenariuszy jest, jeśli wystarczy tylko ponownie ocenić wartość źródłową z interfejsu użytkownika.

- Nie pokazano na rysunku jest <xref:System.Windows.Data.BindingMode.OneTime> powiązanie, co powoduje, że właściwość źródło do inicjowania właściwości docelowej, ale nie propaguje kolejne zmiany. Jeśli kontekst danych zmieni się lub obiekt w kontekście danych ulegnie zmianie, zmiana *nie* zostanie odzwierciedlona we właściwości docelowej. Ten typ powiązania jest odpowiedni, jeśli migawka bieżącego stanu jest odpowiednia lub dane są naprawdę statyczne. Ten typ powiązania jest również przydatne, jeśli chcesz zainicjować właściwość docelową z pewną wartość z właściwości źródłowej i kontekst danych nie jest znany z wyprzedzeniem. Ten tryb jest zasadniczo <xref:System.Windows.Data.BindingMode.OneWay> prostszą formą powiązania, która zapewnia lepszą wydajność w przypadkach, gdy wartość źródło nie zmienia.

Aby wykryć zmiany <xref:System.Windows.Data.BindingMode.OneWay> <xref:System.Windows.Data.BindingMode.TwoWay> źródła (mające zastosowanie do i powiązania), źródło <xref:System.ComponentModel.INotifyPropertyChanged>musi wdrożyć odpowiedni mechanizm powiadamiania o zmianie właściwości, taki jak . Zobacz [Jak: Implementowanie powiadomienia o zmianie właściwości](../../framework/wpf/data/how-to-implement-property-change-notification.md) na przykład <xref:System.ComponentModel.INotifyPropertyChanged> implementacji.

Właściwość <xref:System.Windows.Data.Binding.Mode?displayProperty=nameWithType> zawiera więcej informacji na temat trybów wiązania i przykład sposobu określania kierunku powiązania.

### <a name="what-triggers-source-updates"></a>Co wyzwala aktualizacje źródeł

Powiązania, które <xref:System.Windows.Data.BindingMode.TwoWay> <xref:System.Windows.Data.BindingMode.OneWayToSource> są lub nasłuchują zmian we właściwości docelowej i propagują je z powrotem do źródła, znany jako aktualizowanie źródła. Na przykład można edytować tekst textbox, aby zmienić podstawową wartość źródła.

Czy jednak wartość źródłowa jest aktualizowana podczas edytowania tekstu lub po zakończeniu edycji tekstu, a formant traci fokus? Właściwość <xref:System.Windows.Data.Binding.UpdateSourceTrigger?displayProperty=nameWithType> określa, co wyzwala aktualizację źródła. Kropki strzałek w prawo na poniższym rysunku <xref:System.Windows.Data.Binding.UpdateSourceTrigger?displayProperty=nameWithType> ilustrują rolę właściwości.

![Diagram, który pokazuje rolę UpdateSourceTrigger właściwości.](./media/data-binding-overview/data-binding-updatesource-trigger.png)

Jeśli `UpdateSourceTrigger` wartość <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged?displayProperty=nameWithType>jest , a następnie wartość wskazywała strzałką w prawo <xref:System.Windows.Data.BindingMode.TwoWay> lub <xref:System.Windows.Data.BindingMode.OneWayToSource> powiązania jest aktualizowana, jak tylko zmieni właściwość docelowa. Jednak jeśli `UpdateSourceTrigger` wartość <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>jest , a następnie ta wartość jest aktualizowana tylko o nową wartość, gdy właściwość docelowa traci fokus.

Podobnie jak <xref:System.Windows.Data.Binding.Mode%2A> właściwość, różne właściwości zależności <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> mają różne wartości domyślne. Wartością domyślną dla większości <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>właściwości zależności `TextBox.Text` jest , podczas <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>gdy właściwość ma wartość domyślną . `PropertyChanged`oznacza, że aktualizacje źródłowe zwykle zdarzają się za każdym razem, gdy zmienia się właściwość docelowa. Natychmiastowe zmiany są w porządku dla CheckBoxes i innych prostych formantów. Jednak w przypadku pól tekstowych aktualizowanie po każdym naciśnięciu klawisza może zmniejszyć wydajność i pozbawia użytkownika zwykłej możliwości tworzenia backspace i naprawiania błędów podczas pisania przed zatwierdzeniem nowej wartości.

Zobacz <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> stronę właściwości, aby uzyskać informacje na temat znajdowania wartości domyślnej właściwości zależności.

Poniższa tabela zawiera przykładowy scenariusz dla każdej <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> wartości przy użyciu <xref:System.Windows.Controls.TextBox> jako przykład.

| UpdateSourceTrigger wartość | Po zaktualizowaniu wartości źródła | Przykładowy scenariusz dla textbox |
| ------------------------- | ---------------------------------- | ---------------------------- |
| `LostFocus`(domyślnie <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType>dla) | Gdy formant TextBox traci fokus. | Pole tekstowe skojarzone z logiką sprawdzania poprawności (zobacz [sprawdzanie poprawności danych](#data-validation) poniżej). |
| `PropertyChanged` | Podczas wpisywać <xref:System.Windows.Controls.TextBox>do pliku . | TextBox kontroluje w oknie pokoju rozmów. |
| `Explicit` | Gdy aplikacja <xref:System.Windows.Data.BindingExpression.UpdateSource%2A>wywołuje . | TextBox formanty w edytowalnym formularzu (aktualizuje wartości źródłowe tylko wtedy, gdy użytkownik kliknie przycisk prześlij). |

Na przykład zobacz [Jak: Sterowanie, gdy tekst textbox aktualizuje źródło](../../framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md).

## <a name="creating-a-binding"></a>Tworzenie powiązania

Aby znowelić niektóre pojęcia omówione w poprzednich sekcjach, <xref:System.Windows.Data.Binding> należy ustanowić powiązanie przy użyciu obiektu, a każde powiązanie zwykle ma cztery składniki: obiekt docelowy powiązania, właściwość docelową, źródło powiązania i ścieżkę do wartości źródłowej do użycia. W tej sekcji omówiono sposób konfigurowania powiązania.

Rozważmy poniższy przykład, w którym obiekt źródłowy powiązania jest klasą o nazwie *MyData,* która jest zdefiniowana w obszarze nazw *SDKSample.* W celach demonstracyjnych *MyData* ma właściwość ciągu o nazwie *ColorName,* której wartość jest ustawiona na "Czerwony". W ten sposób w tym przykładzie generuje przycisk z czerwonym tłem.

[!code-xaml[BindNonTextProperty](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/AutoConvertPropertyToColor.xaml#BindAutoConvertColor)]

Aby uzyskać więcej informacji na temat składni deklaracji wiązania i przykładów konfigurowania powiązania w kodzie, zobacz [Omówienie deklaracji wiążących](../../framework/wpf/data/binding-declarations-overview.md).

Jeśli zastosujemy ten przykład do naszego diagramu podstawowego, wynikowa liczba wygląda następująco. Na rysunku <xref:System.Windows.Data.BindingMode.OneWay> opisano powiązanie, <xref:System.Windows.Data.BindingMode.OneWay> ponieważ Background właściwość obsługuje powiązanie domyślnie.

![Diagram, który pokazuje powiązanie danych Background właściwości.](./media/data-binding-overview/data-binding-button-background-example.png)

Można się zastanawiać, dlaczego to powiązanie działa, mimo że *ColorName* właściwość jest typu string, podczas gdy <xref:System.Windows.Controls.Control.Background%2A> właściwość jest typu. <xref:System.Windows.Media.Brush> To powiązanie używa domyślnej konwersji typu, co zostało omówione w sekcji [Konwersja danych.](#data-conversion)

### <a name="specifying-the-binding-source"></a>Określanie źródła powiązania

Należy zauważyć, że w poprzednim przykładzie źródło powiązania jest określony przez ustawienie [DockPanel.DataContext](xref:System.Windows.FrameworkElement.DataContext) właściwości. Następnie <xref:System.Windows.Controls.Button> dziedziczy <xref:System.Windows.FrameworkElement.DataContext%2A> wartość z <xref:System.Windows.Controls.DockPanel>elementu nadrzędnego , który jest jego elementem nadrzędnym. Aby powtórzyć, obiekt źródłowy powiązania jest jednym z czterech niezbędnych składników powiązania. W związku z tym bez obiektu źródła powiązania jest określony, powiązanie nie zrobi nic.

Istnieje kilka sposobów, aby określić obiekt źródłowy powiązania. Korzystanie <xref:System.Windows.FrameworkElement.DataContext%2A> z właściwości na element nadrzędny jest przydatne, gdy są wiążące wiele właściwości do tego samego źródła. Jednak czasami może być bardziej odpowiednie do określenia źródła wiązania dla poszczególnych deklaracji wiązania. W poprzednim przykładzie zamiast używać <xref:System.Windows.FrameworkElement.DataContext%2A> właściwości, można określić źródło <xref:System.Windows.Data.Binding.Source%2A?displayProperty=nameWithType> powiązania, ustawiając właściwość bezpośrednio na deklaracji powiązania przycisku, jak w poniższym przykładzie.

[!code-xaml[BindNonTextPropertyCompactBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/AutoConvertPropertyToColor.xaml#BindAutoConvertColorCompactBinding)]

Inne niż <xref:System.Windows.FrameworkElement.DataContext%2A> ustawienie właściwości na element bezpośrednio, <xref:System.Windows.FrameworkElement.DataContext%2A> dziedzicząc wartość z elementu nadrzędnego (na przykład przycisk w pierwszym przykładzie) i jawnie określając źródło powiązania przez ustawienie <xref:System.Windows.Data.Binding.Source%2A?displayProperty=nameWithType> <xref:System.Windows.Data.Binding.ElementName?displayProperty=nameWithType> właściwości na <xref:System.Windows.Data.Binding.RelativeSource?displayProperty=nameWithType> powiązanie (na przykład przycisk ostatni przykład), można również użyć właściwości lub właściwości, aby określić źródło powiązania. Właściwość <xref:System.Windows.Data.Binding.ElementName%2A> jest przydatna, gdy są wiązaniem z innymi elementami w aplikacji, na przykład podczas korzystania z suwaka, aby dostosować szerokość przycisku. Właściwość <xref:System.Windows.Data.Binding.RelativeSource%2A> jest przydatna, gdy powiązanie jest określone w a <xref:System.Windows.Controls.ControlTemplate> lub a <xref:System.Windows.Style>. Aby uzyskać więcej informacji, zobacz [Jak: Określanie źródła powiązania](../../framework/wpf/data/how-to-specify-the-binding-source.md).

### <a name="specifying-the-path-to-the-value"></a>Określanie ścieżki do wartości

Jeśli źródło powiązania jest obiektem, <xref:System.Windows.Data.Binding.Path?displayProperty=nameWithType> należy użyć właściwości, aby określić wartość do użycia dla powiązania. Jeśli są wiążące z danymi XML, należy użyć właściwości, <xref:System.Windows.Data.Binding.XPath?displayProperty=nameWithType> aby określić wartość. W niektórych przypadkach może mieć <xref:System.Windows.Data.Binding.Path%2A> zastosowanie do korzystania z właściwości, nawet wtedy, gdy dane są XML. Na przykład, jeśli chcesz uzyskać dostęp do Name właściwości zwracanego XmlNode (w wyniku <xref:System.Windows.Data.Binding.Path%2A> kwerendy XPath), należy użyć właściwości oprócz <xref:System.Windows.Data.Binding.XPath%2A> właściwości.

Aby uzyskać więcej <xref:System.Windows.Data.Binding.Path%2A> informacji, zobacz i <xref:System.Windows.Data.Binding.XPath%2A> właściwości.

Mimo, że podkreśliliśmy, że <xref:System.Windows.Data.Binding.Path%2A> do wartości do użycia jest jednym z czterech niezbędnych składników powiązania, w scenariuszach, które mają być powiązane z całym obiektem, wartość do użycia będzie taka sama jak obiekt źródłowy powiązania. W takich przypadkach ma zastosowanie, <xref:System.Windows.Data.Binding.Path%2A>aby nie określać pliku . Rozważmy następujący przykład.

[!code-xaml[EmptyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/EmptyBinding.xaml#EmptyBinding)]

W powyższym przykładzie użyto pustej składni wiązania: {Binding}. W takim przypadku <xref:System.Windows.Controls.ListBox> dziedziczy DataContext z nadrzędnego DockPanel element (nie pokazano w tym przykładzie). Jeśli ścieżka nie jest określona, domyślnie jest powiązanie z całym obiektem. Innymi słowy w tym przykładzie ścieżka została pominięta, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> ponieważ jesteśmy wiążące właściwości do całego obiektu. (Zobacz [Powiązanie do kolekcji](#binding-to-collections) sekcji pogłębionej dyskusji.)

Inne niż powiązanie z kolekcji, ten scenariusz jest również przydatne, gdy chcesz powiązać z całego obiektu, a nie tylko pojedynczą właściwość obiektu. Na przykład, jeśli obiekt źródłowy jest typu, <xref:System.String>można po prostu powiązać z samym ciągiem. Innym typowym scenariuszem jest, gdy chcesz powiązać element z obiektem o kilku właściwościach.

Może być konieczne zastosowanie logiki niestandardowej, tak aby dane mają znaczenie dla powiązanej właściwości docelowej. Logika niestandardowa może mieć postać konwertera niestandardowego, jeśli domyślna konwersja typu nie istnieje. Zobacz [Konwersja danych,](#data-conversion) aby uzyskać informacje o konwerterach.

### <a name="binding-and-bindingexpression"></a>Wiązanie i wiązanieWydanie

Przed uzyskaniem do innych funkcji i użycia powiązania danych, warto wprowadzić <xref:System.Windows.Data.BindingExpression> klasę. Jak widzieliście w poprzednich sekcjach, <xref:System.Windows.Data.Binding> klasa jest klasą wysokiego poziomu dla deklaracji wiązania; zapewnia wiele właściwości, które umożliwiają określenie właściwości powiązania. Klasa pokrewna , jest podstawowym obiektem, <xref:System.Windows.Data.BindingExpression>który utrzymuje połączenie między źródłem a obiektem docelowym. Powiązanie zawiera wszystkie informacje, które mogą być współużytkowane przez kilka wyrażeń wiązania. A <xref:System.Windows.Data.BindingExpression> jest wyrażeniem wystąpienia, które nie może być <xref:System.Windows.Data.Binding>udostępnione i zawiera wszystkie informacje o wystąpieniu pliku .

Rozważmy poniższy `myDataObject` przykład, gdzie `MyData` jest `myBinding` wystąpieniem <xref:System.Windows.Data.Binding> klasy, `MyData` jest obiektem źródłowym i `MyDataProperty`jest zdefiniowaną klasą, która zawiera właściwość string o nazwie . W tym przykładzie powiązana zawartość <xref:System.Windows.Controls.TextBlock>tekstową `MyDataProperty` `myText`, wystąpienie , do .

[!code-csharp[CodeOnlyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/ManualBinding.cs#CodeOnlyBinding)]
[!code-vb[CodeOnlyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/ManualBinding.vb#CodeOnlyBinding)]

Do utworzenia innych powiązań można użyć tego samego obiektu *myBinding.* Na przykład można użyć obiektu *myBinding* do powiązania zawartości tekstowej pola wyboru z *mydataproperty*. W tym scenariuszu będą dwa <xref:System.Windows.Data.BindingExpression> wystąpienia udostępniania *obiektu myBinding.*

Obiekt <xref:System.Windows.Data.BindingExpression> jest zwracany <xref:System.Windows.Data.BindingOperations.GetBindingExpression%2A> przez wywołanie obiektu powiązanego z danymi. Następujące artykuły pokazują niektóre użycia <xref:System.Windows.Data.BindingExpression> klasy:

- [Pobieranie obiektu wiążącego z powiązanej własności docelowej](../../framework/wpf/data/how-to-get-the-binding-object-from-a-bound-target-property.md)

- [Sterowanie, gdy tekst textbox aktualizuje źródło](../../framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md)

## <a name="data-conversion"></a>Konwersja danych

W [sekcji Tworzenie powiązania](#creating-a-binding) przycisk jest czerwony, <xref:System.Windows.Controls.Control.Background%2A> ponieważ jego właściwość jest powiązana z właściwością string o wartości "Czerwony". Ta wartość ciągu działa, ponieważ konwerter typów jest obecny na typie, <xref:System.Windows.Media.Brush> aby przekonwertować wartość ciągu na <xref:System.Windows.Media.Brush>.

Dodawanie tych informacji do rysunku [Tworzenie powiązanie](#creating-a-binding) sekcji wygląda następująco.

![Diagram, który pokazuje powiązanie danych Default właściwości.](./media/data-binding-overview/data-binding-button-default-conversion.png)

Jednak co zrobić, jeśli zamiast właściwości typu ciąg znak *Color* powiązania obiekt <xref:System.Windows.Media.Color>źródłowy ma Color właściwości typu? W takim przypadku, aby powiązanie do pracy należy najpierw włączyć *Color* wartość <xref:System.Windows.Controls.Control.Background%2A> właściwości do czegoś, co właściwość akceptuje. Należy utworzyć konwerter niestandardowy przez <xref:System.Windows.Data.IValueConverter> implementowanie interfejsu, jak w poniższym przykładzie.

[!code-csharp[CodeOnlyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/ColorBrushConverter.cs#ColorBrushConverter)]
[!code-vb[CodeOnlyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/ColorBrushConverter.vb#ColorBrushConverter)]

Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Data.IValueConverter>.

Teraz niestandardowy konwerter jest używany zamiast domyślnej konwersji, a nasz diagram wygląda tak.

![Diagram, który pokazuje niestandardowy konwerter wiązania danych.](./media/data-binding-overview/data-binding-converter-color-example.png)

Aby powtórzyć, konwersje domyślne mogą być dostępne ze względu na konwertery typów, które są obecne w typie, z którymi jest powiązany. To zachowanie będzie zależeć od tego, które konwertery typu są dostępne w docelowych. W razie wątpliwości utwórz własny konwerter.

Oto niektóre typowe scenariusze, w których warto zaimplementować konwerter danych:

- Dane powinny być wyświetlane w różny sposób, w zależności od kultury. Na przykład można zaimplementować konwerter walut lub konwerter daty/godziny kalendarza na podstawie konwencji używanych w określonej kulturze.

- Używane dane nie muszą być przeznaczone do zmiany wartości tekstowej właściwości, ale zamiast tego mają na celu zmianę innej wartości, takiej jak źródło obrazu lub kolor lub styl wyświetlanego tekstu. Konwertery mogą być używane w tym wystąpieniu przez konwersję powiązania właściwości, która może nie wydawać się odpowiednia, takich jak powiązanie pola tekstowego z Background właściwości komórki tabeli.

- Więcej niż jeden formant lub wiele właściwości formantów są powiązane z tymi samymi danymi. W takim przypadku wiązanie podstawowe może po prostu wyświetlić tekst, podczas gdy inne powiązania obsługi określonych problemów wyświetlania, ale nadal używać tego samego powiązania jako informacje źródłowe.

- Właściwość docelowa ma kolekcję powiązań, <xref:System.Windows.Data.MultiBinding>która jest nazywana . For <xref:System.Windows.Data.MultiBinding>, służysz <xref:System.Windows.Data.IMultiValueConverter> niestandardowe do tworzenia wartości końcowej z wartości powiązań. Na przykład kolor może być obliczany z wartości czerwony, niebieski i zielony, które mogą być wartości z tego samego lub różnych obiektów źródłowych powiązania. Zobacz <xref:System.Windows.Data.MultiBinding> przykłady i informacje.

## <a name="binding-to-collections"></a>Powiązanie z kolekcjami

Obiekt źródłowy powiązania może być traktowany jako pojedynczy obiekt, którego właściwości zawierają dane lub jako zbiór danych obiektów polimorficznych, które często są zgrupowane razem (na przykład wynik kwerendy do bazy danych). Do tej pory omówiliśmy tylko powiązanie z pojedynczymi obiektami. Jednak powiązanie z gromadzeniem danych jest typowym scenariuszem. Na przykład typowym scenariuszem <xref:System.Windows.Controls.ItemsControl> jest użycie <xref:System.Windows.Controls.ListBox> <xref:System.Windows.Controls.ListView>takiego <xref:System.Windows.Controls.TreeView> programu, jak i wyświetlenie kolekcji danych, na przykład w aplikacji pokazanej w sekcji [Powiązanie danych Co to jest.](#what-is-data-binding)

Na szczęście nasz podstawowy schemat nadal ma zastosowanie. Jeśli są wiążące <xref:System.Windows.Controls.ItemsControl> do kolekcji, diagram wygląda następująco.

![Diagram, który pokazuje obiekt ItemsControl wiązania danych.](./media/data-binding-overview/data-binding-itemscontrol.png)

Jak pokazano na tym diagramie, aby powiązać <xref:System.Windows.Controls.ItemsControl> do obiektu kolekcji, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A?displayProperty=nameWithType> właściwość jest właściwość do użycia. Możesz myśleć `ItemsSource` jako o treści <xref:System.Windows.Controls.ItemsControl>. Powiązanie <xref:System.Windows.Data.BindingMode.OneWay> jest, `ItemsSource` ponieważ `OneWay` właściwość obsługuje powiązanie domyślnie.

### <a name="how-to-implement-collections"></a>Jak zaimplementować kolekcje

Można wyliczyć za każdym kolekcji, która implementuje <xref:System.Collections.IEnumerable> interfejs. Jednak aby skonfigurować powiązania dynamiczne, tak aby wstawienia lub usunięcia w kolekcji <xref:System.Collections.Specialized.INotifyCollectionChanged> zaktualizować interfejsu użytkownika automatycznie, kolekcja musi implementować interfejs. Ten interfejs udostępnia zdarzenie, które powinny być wywoływane za każdym razem, gdy zmienia się podstawowa kolekcja.

WPF WPF zapewnia <xref:System.Collections.ObjectModel.ObservableCollection%601> klasę, która jest wbudowana implementacja <xref:System.Collections.Specialized.INotifyCollectionChanged> kolekcji danych, która udostępnia interfejs. Aby w pełni obsługiwać przesyłanie wartości danych z obiektów źródłowych do obiektów docelowych, każdy obiekt w kolekcji, który obsługuje właściwości, które można powiązać, musi również implementować <xref:System.ComponentModel.INotifyPropertyChanged> interfejs. Aby uzyskać więcej informacji, zobacz [Omówienie źródeł powiązania](../../framework/wpf/data/binding-sources-overview.md).

Przed wdrożeniem własnej kolekcji <xref:System.Collections.ObjectModel.ObservableCollection%601> należy rozważyć użycie lub jedną <xref:System.Collections.Generic.List%601> <xref:System.Collections.ObjectModel.Collection%601>z <xref:System.ComponentModel.BindingList%601>istniejących klas kolekcji, takich jak , i , wśród wielu innych. Jeśli masz zaawansowany scenariusz i chcesz zaimplementować własną kolekcję, należy rozważyć użycie <xref:System.Collections.IList>, który zapewnia niegeneryczną kolekcję obiektów, które mogą być indywidualnie dostępne przez indeks, a tym samym zapewnia najlepszą wydajność.

### <a name="collection-views"></a>Widoki kolekcji

Po <xref:System.Windows.Controls.ItemsControl> powiązaniu z gromadzeniem danych można sortować, filtrować lub grupować dane. Aby to zrobić, należy użyć widoków kolekcji, które są klasy, które implementują <xref:System.ComponentModel.ICollectionView> interfejs.

#### <a name="what-are-collection-views"></a>Co to są widoki kolekcji?

Widok kolekcji to warstwa na górze kolekcji źródła powiązania, która umożliwia nawigację i wyświetlanie kolekcji źródłowej na podstawie zapytań sortowania, filtrowania i grupowania, bez konieczności zmiany samej kolekcji źródłowej. Widok kolekcji utrzymuje również wskaźnik do bieżącego elementu w kolekcji. Jeśli kolekcja źródło implementuje <xref:System.Collections.Specialized.INotifyCollectionChanged> interfejs, zmiany <xref:System.Collections.Specialized.INotifyCollectionChanged.CollectionChanged> wywoływane przez zdarzenie są propagowane do widoków.

Ponieważ widoki nie zmieniają podstawowych kolekcji źródłowych, każda kolekcja źródłowa może mieć skojarzone z nią wiele widoków. Na przykład może mieć kolekcję *Task* obiektów. Korzystając z widoków, można wyświetlać te same dane na różne sposoby. Na przykład po lewej stronie strony można wyświetlić zadania posortowane według priorytetu, a po prawej stronie pogrupowane według obszaru.

#### <a name="how-to-create-a-view"></a>Jak utworzyć widok

Jednym ze sposobów tworzenia i używania widoku jest utworzenie wystąpienia obiektu widoku bezpośrednio, a następnie użycie go jako źródła powiązania. Na przykład należy wziąć pod uwagę [aplikacja demonstracyjna powiązania danych][data-binding-demo] wyświetlane w what is data [binding](#what-is-data-binding) sekcji. Aplikacja jest implementowana w <xref:System.Windows.Controls.ListBox> taki sposób, że wiąże się z widokiem za pobraniem danych zamiast zbierania danych bezpośrednio. Poniższy przykład jest wyodrębniany z aplikacji [demo powiązania danych.][data-binding-demo] Klasa <xref:System.Windows.Data.CollectionViewSource> jest serwerem proxy XAML klasy, <xref:System.Windows.Data.CollectionView>która dziedziczy po . W tym konkretnym <xref:System.Windows.Data.CollectionViewSource.Source%2A> przykładzie widoku jest powiązany z *AuctionItems* kolekcji (typu) <xref:System.Collections.ObjectModel.ObservableCollection%601>bieżącego obiektu aplikacji.

[!code-xaml[CollectionView](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml#CollectionView)]

Resource *listingDataView* służy następnie jako źródło powiązania elementów w <xref:System.Windows.Controls.ListBox>aplikacji, takich jak .

[!code-xaml[ListBoxCollectionView](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml#ListBoxCollectionView)]

Aby utworzyć inny widok dla tej samej kolekcji, można utworzyć inne <xref:System.Windows.Data.CollectionViewSource> wystąpienie i nadać mu inną `x:Key` nazwę.

W poniższej tabeli przedstawiono, jakie typy <xref:System.Windows.Data.CollectionViewSource> danych widoku są tworzone jako domyślny widok kolekcji lub na podstawie typu kolekcji źródłowej.

| Typ kolekcji źródłowych                    | Typ widoku kolekcji | Uwagi |
| ----------------------------------------- | -------------------- | ----- |
| <xref:System.Collections.IEnumerable>     | Typ wewnętrzny oparty na<xref:System.Windows.Data.CollectionView> | Nie można grupuj elementów. |
| <xref:System.Collections.IList>           | <xref:System.Windows.Data.ListCollectionView> | Najszybszy. |
| <xref:System.ComponentModel.IBindingList> | <xref:System.Windows.Data.BindingListCollectionView> | |

#### <a name="using-a-default-view"></a>Korzystanie z widoku domyślnego

Określanie widoku kolekcji jako źródła powiązania jest jednym ze sposobów tworzenia i używania widoku kolekcji. WPF WPF tworzy również domyślny widok kolekcji dla każdej kolekcji używane jako źródło powiązania. Jeśli wiąże się bezpośrednio z kolekcji, WPF wiąże się z jego widoku domyślnego. Ten widok domyślny jest współużytkowany przez wszystkie powiązania do tej samej kolekcji, więc zmiana włączona do widoku domyślnego przez jeden powiązany formant lub kod (na przykład sortowanie lub zmiana bieżącego wskaźnika elementu, omówione później) jest odzwierciedlana we wszystkich innych powiązaniach do tej samej kolekcji.

Aby uzyskać widok domyślny, <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> należy użyć metody. Na przykład zobacz [Pobieranie domyślnego widoku zbierania danych](../../framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md).

#### <a name="collection-views-with-adonet-datatables"></a>Widoki kolekcji z ADO.NET datatables

Aby zwiększyć wydajność, widoki kolekcji <xref:System.Data.DataTable> <xref:System.Data.DataView> dla ADO.NET lub obiekty delegować sortowanie i filtrowanie do <xref:System.Data.DataView>, co powoduje, sortowanie i filtrowanie mają być współużytkowane we wszystkich widokach kolekcji źródła danych. Aby włączyć każdy widok kolekcji, aby sortować i filtrować niezależnie, zainicjować każdy widok kolekcji z własnym <xref:System.Data.DataView> obiektem.

#### <a name="sorting"></a>Sortowanie

Jak wspomniano wcześniej, widoki można zastosować kolejność sortowania do kolekcji. W miarę jak istnieje w kolekcji podstawowej, dane mogą lub nie mogą mieć odpowiedniego, nieodłącznego porządku. Widok na kolekcji pozwala narzucić zamówienie lub zmienić kolejność domyślną, na podstawie kryteriów porównania, które dostarczasz. Ponieważ jest to widok oparty na kliencie danych, typowym scenariuszem jest to, że użytkownik może chcieć sortować kolumny danych tabelaryczne według wartości, która odpowiada kolumnie. Za pomocą widoków, to sortowanie oparte na użytkowniku można zastosować ponownie, bez wprowadzania żadnych zmian w podstawowej kolekcji lub nawet konieczności ponownego zapytania dla zawartości kolekcji. Na przykład zobacz [Sortowanie kolumny GridView po kliknięciu nagłówka](../../framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md).

Poniższy przykład przedstawia logikę sortowania "Sortuj <xref:System.Windows.Controls.CheckBox> według kategorii i daty" interfejsu użytkownika aplikacji w sekcji [Powiązanie danych Co to jest.](#what-is-data-binding)

[!code-csharp[AddSortChecked](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml.cs#AddSortChecked)]
[!code-vb[AddSortChecked](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/CollectionView.xaml.vb#AddSortChecked)]

#### <a name="filtering"></a>Filtrowanie

Widoki można również zastosować filtr do kolekcji, dzięki czemu widok pokazuje tylko określony podzbiór pełnej kolekcji. Można filtrować warunek w danych. Na przykład, jak to się robi przez aplikację w what is data <xref:System.Windows.Controls.CheckBox> [binding](#what-is-data-binding) sekcji, "Pokaż tylko okazje" zawiera logikę, aby odfiltrować elementy, które kosztują $25 lub więcej. Poniższy kod jest wykonywany, aby ustawić *ShowOnlyBargainsFilter* jako program obsługi <xref:System.Windows.Data.CollectionViewSource.Filter> zdarzeń, <xref:System.Windows.Controls.CheckBox> gdy jest zaznaczona.

[!code-csharp[ListingViewFilter](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml.cs#ListingViewFilter)]
[!code-vb[ListingViewFilter](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/CollectionView.xaml.vb#ListingViewFilter)]

Program obsługi zdarzeń *ShowOnlyBargainsFilter* ma następującą implementację.

[!code-csharp[FilterEvent](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml.cs#FilterEvent)]
[!code-vb[FilterEvent](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/CollectionView.xaml.vb#FilterEvent)]

Jeśli używasz jednej <xref:System.Windows.Data.CollectionView> z klas bezpośrednio <xref:System.Windows.Data.CollectionViewSource>zamiast , należy <xref:System.Windows.Data.CollectionView.Filter%2A> użyć właściwości, aby określić wywołanie zwrotne. Na przykład zobacz [Filtrowanie danych w widoku](../../framework/wpf/data/how-to-filter-data-in-a-view.md).

#### <a name="grouping"></a>Grupowanie

Z wyjątkiem klasy wewnętrznej, <xref:System.Collections.IEnumerable> która wyświetla kolekcję, wszystkie widoki kolekcji obsługują *grupowanie,* co umożliwia użytkownikowi partycjonowanie kolekcji w widoku kolekcji na grupy logiczne. Grupy mogą być jawne, gdzie użytkownik dostarcza listę grup lub niejawne, gdzie grupy są generowane dynamicznie w zależności od danych.

W poniższym przykładzie przedstawiono logikę <xref:System.Windows.Controls.CheckBox>"Grupa według kategorii" .

[!code-csharp[ListingGroupCheck](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml.cs#ListingGroupCheck)]
[!code-vb[ListingGroupCheck](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/CollectionView.xaml.vb#ListingGroupCheck)]

W innym przykładzie grupowania zobacz [Elementy grupy w widoku ListView, który implementuje widok gridview](../../framework/wpf/controls/how-to-group-items-in-a-listview-that-implements-a-gridview.md).

#### <a name="current-item-pointers"></a>Bieżące wskaźniki elementów

Widoki obsługują również pojęcie bieżącego elementu. Można poruszać się po obiektach w widoku kolekcji. Podczas nawigacji są przenoszenia wskaźnik elementu, który umożliwia pobieranie obiektu, który istnieje w tej określonej lokalizacji w kolekcji. Na przykład zobacz [Nawiguj po obiektach w widoku CollectionView danych](../../framework/wpf/data/how-to-navigate-through-the-objects-in-a-data-collectionview.md).

Ponieważ WPF wiąże się z kolekcji tylko przy użyciu widoku (widok określony lub widoku domyślnego kolekcji), wszystkie powiązania do kolekcji mają wskaźnik bieżącego elementu. Podczas wiązania z widokiem znak ukośnika ("/") w `Path` wartości oznacza bieżący element widoku. W poniższym przykładzie kontekst danych jest widokiem kolekcji. Pierwszy wiersz wiąże się z kolekcji. Drugi wiersz wiąże się z bieżącym elementem w kolekcji. Trzeci wiersz wiąże się `Description` z właściwością bieżącego elementu w kolekcji.

```xaml
<Button Content="{Binding }" />
<Button Content="{Binding Path=/}" />
<Button Content="{Binding Path=/Description}" />
```

Ukośnik i składnia właściwości można również układać w stos, aby przechodzić przez hierarchię kolekcji. Poniższy przykład wiąże się z bieżącym `Offices`elementem kolekcji o nazwie , która jest właściwością bieżącego elementu kolekcji źródłowej.

```xaml
<Button Content="{Binding /Offices/}" />
```

Na bieżący wskaźnik elementu może mieć wpływ dowolne sortowanie lub filtrowanie, które jest stosowane do kolekcji. Sortowanie zachowuje bieżący wskaźnik elementu na ostatnim wybranym elemencie, ale widok kolekcji jest teraz zrestrukturyzowany wokół niego. (Być może wybrany element był na początku listy wcześniej, ale teraz wybrany element może znajdować się gdzieś w środku.) Filtrowanie zachowuje zaznaczony element, jeśli zaznaczenie to pozostaje widoczne po filtrowaniu. W przeciwnym razie wskaźnik bieżącego elementu jest ustawiony na pierwszy element filtrowanego widoku kolekcji.

#### <a name="master-detail-binding-scenario"></a>Scenariusz wiązania master-detail

Pojęcie bieżącego elementu jest przydatne nie tylko do nawigacji elementów w kolekcji, ale także dla scenariusza wiązania szczegóły wzorca. Należy ponownie wziąć pod uwagę interfejs użytkownika aplikacji w sekcji [Co to jest powiązanie danych.](#what-is-data-binding) W tej aplikacji zaznaczenie <xref:System.Windows.Controls.ListBox> w obrębie określa <xref:System.Windows.Controls.ContentControl>zawartość wyświetlaną w pliku . Aby umieścić go w inny <xref:System.Windows.Controls.ListBox> sposób, gdy <xref:System.Windows.Controls.ContentControl> element jest zaznaczony, pokazuje szczegóły wybranego elementu.

Można zaimplementować scenariusz szczegółów wzorcowych po prostu o dwa lub więcej formantów powiązanych z tym samym widoku. Poniższy przykład z [demo powiązania danych][data-binding-demo] pokazuje <xref:System.Windows.Controls.ListBox> znaczników i <xref:System.Windows.Controls.ContentControl> widać w interfejsie użytkownika aplikacji w What is data [binding](#what-is-data-binding) sekcji.

[!code-xaml[ListBoxContentControl](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml#ListBoxContentControl)]

Należy zauważyć, że oba formanty są powiązane z tym samym źródłem, *a listingDataView* zasób statyczny (zobacz definicję tego zasobu w [sekcji Jak utworzyć widok](#how-to-create-a-view)). To powiązanie działa, ponieważ gdy <xref:System.Windows.Controls.ContentControl> obiekt singleton (w tym przypadku) jest powiązany <xref:System.Windows.Data.CollectionView.CurrentItem%2A> z widokiem kolekcji, automatycznie wiąże się z widoku. Obiekty <xref:System.Windows.Data.CollectionViewSource> automatycznie synchronizują walutę i zaznaczenie. Jeśli formant listy nie <xref:System.Windows.Data.CollectionViewSource> jest powiązany z obiektem, jak <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> w `true` tym przykładzie, należy ustawić jego właściwość, aby to działało.

Aby uzyskać więcej przykładów, zobacz [Powiązanie z kolekcją i wyświetlają informacje na podstawie zaznaczenia](../../framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md) i [Użyj wzorca szczegółów wzorca z danymi hierarchicznymi](../../framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md).

Być może zauważyłeś, że w powyższym przykładzie użyto szablonu. W rzeczywistości dane nie byłyby wyświetlane tak, jak chcemy bez użycia szablonów <xref:System.Windows.Controls.ContentControl> (ten wyraźnie używany przez <xref:System.Windows.Controls.ListBox>i ten, który jest w sposób dorozumiany używany przez ). Teraz zwracamy się do tworzenia szablonów danych w następnej sekcji.

## <a name="data-templating"></a>Tworzenie szablonów danych

Bez użycia szablonów danych nasz interfejs użytkownika aplikacji w sekcji [Powiązanie danych Co oznacza,](#what-is-data-binding) będzie wyglądać następująco.

![Demonstracja powiązania danych bez szablonów danych](./media/data-binding-overview/demo-no-template.png)

Jak pokazano w przykładzie w poprzedniej <xref:System.Windows.Controls.ListBox> sekcji, <xref:System.Windows.Controls.ContentControl> formant i są powiązane z całego obiektu kolekcji (a dokładniej widok nad obiektem kolekcji) *AuctionItem*s. Bez szczegółowych instrukcji, jak wyświetlić kolekcji danych, <xref:System.Windows.Controls.ListBox> wyświetla reprezentację ciągu każdego <xref:System.Windows.Controls.ContentControl> obiektu w kolekcji podstawowej i wyświetla reprezentację ciągu obiektu, który jest powiązany.

Aby rozwiązać ten problem, <xref:System.Windows.DataTemplate?text=DataTemplates>aplikacja definiuje . Jak pokazano w przykładzie w <xref:System.Windows.Controls.ContentControl> poprzedniej sekcji jawnie używa szablonu danych *detailsProductListingTemplate.* Formant <xref:System.Windows.Controls.ListBox> niejawnie używa następującego szablonu danych podczas wyświetlania *Obiektów AuctionItem* w kolekcji.

[!code-xaml[AuctionItemDataTemplate](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml#AuctionItemDataTemplate)]

Przy użyciu tych dwóch DataTemplates wynikowego interfejsu użytkownika jest wyświetlany w [What is data binding](#what-is-data-binding) sekcji. Jak widać na tym zrzucie ekranu, oprócz umożliwienia umieszczania danych w formantach, tablice danych umożliwiają definiowanie atrakcyjnych wizualizacji danych. Na przykład <xref:System.Windows.DataTrigger>s są używane <xref:System.Windows.DataTemplate> w powyższym tak, że *AuctionItem*s z *SpecialFeatures* wartość *HighLight* będzie wyświetlany z pomarańczową obramowania i gwiazdki.

Aby uzyskać więcej informacji na temat szablonów danych, zobacz [omówienie tworzenia szablonów danych](../../framework/wpf/data/data-templating-overview.md).

## <a name="data-validation"></a>Walidacja danych

Większość aplikacji, które wymagają danych wejściowych użytkownika, musi mieć logikę sprawdzania poprawności, aby upewnić się, że użytkownik wprowadził oczekiwane informacje. Sprawdzanie poprawności może być oparte na typie, zakresie, formacie lub innych wymaganiach specyficznych dla aplikacji. W tej sekcji omówiono sposób sprawdzania poprawności danych w WPF.

### <a name="associating-validation-rules-with-a-binding"></a>Kojarzenie reguł sprawdzania poprawności z powiązaniem

Model wiązania danych WPF umożliwia <xref:System.Windows.Data.Binding.ValidationRules%2A> skojarzenie z obiektem. <xref:System.Windows.Data.Binding> Na przykład w poniższym <xref:System.Windows.Controls.TextBox> przykładzie wiąże `StartPrice` się <xref:System.Windows.Controls.ExceptionValidationRule> z właściwością o nazwie i dodaje obiekt do <xref:System.Windows.Data.Binding.ValidationRules%2A?displayProperty=nameWithType> właściwości.

[!code-xaml[TextboxStartPrice](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/DataValidation.xaml#TextboxStartPrice)]

Obiekt <xref:System.Windows.Controls.ValidationRule> sprawdza, czy wartość właściwości jest prawidłowa. WPF WPF ma dwa <xref:System.Windows.Controls.ValidationRule> typy wbudowanych obiektów:

- A <xref:System.Windows.Controls.ExceptionValidationRule> sprawdza wyjątki zgłaszane podczas aktualizacji właściwości źródła powiązania. W poprzednim przykładzie `StartPrice` jest typu liczby całkowitej. Gdy użytkownik wprowadzi wartość, która nie może być przekonwertowana na całkowitą, zgłaszany jest wyjątek, co powoduje, że powiązanie jest oznaczone jako nieprawidłowe. Alternatywną <xref:System.Windows.Controls.ExceptionValidationRule> składnią do ustawienia jawnie <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> jest `true` ustawienie <xref:System.Windows.Data.Binding> właściwości <xref:System.Windows.Data.MultiBinding> na lub obiektu.

- Obiekt <xref:System.Windows.Controls.DataErrorValidationRule> sprawdza błędy, które są wywoływane <xref:System.ComponentModel.IDataErrorInfo> przez obiekty, które implementują interfejs. Na przykład użycia tej reguły <xref:System.Windows.Controls.DataErrorValidationRule>sprawdzania poprawności zobacz . Alternatywną <xref:System.Windows.Controls.DataErrorValidationRule> składnią do ustawienia jawnie <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> jest `true` ustawienie <xref:System.Windows.Data.Binding> właściwości <xref:System.Windows.Data.MultiBinding> na lub obiektu.

Można również utworzyć własną regułę sprawdzania <xref:System.Windows.Controls.ValidationRule> poprawności, wyprowadzając <xref:System.Windows.Controls.ValidationRule.Validate%2A> z klasy i implementując metodę. W poniższym przykładzie przedstawiono regułę używaną <xref:System.Windows.Controls.TextBox> przez dodaj listę *produktów* "Data rozpoczęcia" z sekcji Co to jest [powiązanie danych.](#what-is-data-binding)

[!code-csharp[FutureDateRule](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/FutureDateRule.cs#FutureDateRule)]
[!code-vb[FutureDateRule](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/FutureDateRule.vb#FutureDateRule)]

*StartDateEntryForm* <xref:System.Windows.Controls.TextBox> używa tego *FutureDateRule*, jak pokazano w poniższym przykładzie.

[!code-xaml[TextboxStartDate](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/DataValidation.xaml#TextboxStartDate)]

Ponieważ <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> wartość <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>jest , aparat wiązania aktualizuje wartość źródłową na każdym naciśnięciu <xref:System.Windows.Data.Binding.ValidationRules%2A> klawisza, co oznacza, że sprawdza również każdą regułę w kolekcji przy każdym naciśnięciu klawisza. Omówimy to dalej w sekcji Proces sprawdzania poprawności.

### <a name="providing-visual-feedback"></a>Dostarczanie wizualnych informacji zwrotnych

Jeśli użytkownik wprowadzi nieprawidłową wartość, można przekazać opinię na temat błędu w interfejsie użytkownika aplikacji. Jednym ze sposobów przekazywania takich <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType> opinii jest ustawienie <xref:System.Windows.Controls.ControlTemplate>dołączonej właściwości na niestandardową . Jak pokazano w poprzedniej podsekcji, *StartDateEntryForm* <xref:System.Windows.Controls.TextBox> używa <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> o nazwie *validationTemplate*. W poniższym przykładzie przedstawiono definicję *validationTemplate*.

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/DataValidation.xaml#ControlTemplate)]

Element <xref:System.Windows.Controls.AdornedElementPlaceholder> określa, gdzie formant jest ozdobiony powinny być umieszczone.

Ponadto można również użyć <xref:System.Windows.Controls.ToolTip> a, aby wyświetlić komunikat o błędzie. Zarówno *StartDateEntryForm* i *StartPriceEntryForm*<xref:System.Windows.Controls.TextBox>es używać stylu *textStyleTextBox*, który <xref:System.Windows.Controls.ToolTip> tworzy, który wyświetla komunikat o błędzie. W poniższym przykładzie przedstawiono definicję *textStyleTextBox*. Dołączona <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> właściwość `true` jest, gdy jeden lub więcej powiązań na właściwości elementu powiązanego są w błędzie.

[!code-xaml[TextBoxStyle](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/DataValidation.xaml#TextBoxStyle)]

<xref:System.Windows.Controls.Validation.ErrorTemplate%2A> Z niestandardowych <xref:System.Windows.Controls.ToolTip>i , *StartDateEntryForm* <xref:System.Windows.Controls.TextBox> wygląda następująco, gdy występuje błąd sprawdzania poprawności.

![Błąd sprawdzania poprawności powiązania danych](./media/data-binding-overview/demo-validation-date.png "DataBindingDemo_Validation")

Jeśli <xref:System.Windows.Data.Binding> masz skojarzone reguły sprawdzania poprawności, ale nie określisz formantu powiązanego, <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> zostanie użyty domyślny <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> do powiadamiania użytkowników o błędzie sprawdzania poprawności. Wartość <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> domyślna to szablon formantu definiujący czerwone obramowanie w warstwie adorner. <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> Z domyślnym <xref:System.Windows.Controls.ToolTip>i , Interfejs użytkownika *StartPriceEntryForm* <xref:System.Windows.Controls.TextBox> wygląda następująco, gdy występuje błąd sprawdzania poprawności.

![Błąd sprawdzania poprawności powiązania danych](./media/data-binding-overview/demo-validation-price.png "DataBindingDemo_ValidationDefault")

Aby uzyskać przykład sposobu dostarczania logiki sprawdzania poprawności wszystkich kontrolek w oknie dialogowym, zobacz sekcję Niestandardowe okna dialogowe w [omówieniu okien dialogowych](../../framework/wpf/app-development/dialog-boxes-overview.md).

### <a name="validation-process"></a>Proces sprawdzania poprawności

Sprawdzanie poprawności zwykle występuje, gdy wartość obiektu docelowego jest przenoszona do właściwości źródła powiązania. Ten transfer <xref:System.Windows.Data.BindingMode.TwoWay> występuje <xref:System.Windows.Data.BindingMode.OneWayToSource> na i powiązania. Aby powtórzyć, co powoduje, że aktualizacja źródła <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> zależy od wartości właściwości, zgodnie z opisem w [What wyzwala źródła aktualizacji](#what-triggers-source-updates) sekcji.

Następujące elementy opisują proces *sprawdzania poprawności.* Jeśli błąd sprawdzania poprawności lub inny typ błędu występuje w dowolnym momencie podczas tego procesu, proces jest zatrzymany:

1. Aparat powiązania sprawdza, czy <xref:System.Windows.Controls.ValidationRule> istnieją jakieś <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> obiekty <xref:System.Windows.Controls.ValidationStep.RawProposedValue> niestandardowe <xref:System.Windows.Data.Binding>zdefiniowane, których <xref:System.Windows.Controls.ValidationRule.Validate%2A> jest ustawiona na to, w którym to przypadku wywołuje metodę na każdym, <xref:System.Windows.Controls.ValidationRule> dopóki jeden z nich nie wpadnie w błąd lub dopóki wszystkie z nich nie przejdą.

2. Aparat wiązania następnie wywołuje konwerter, jeśli istnieje.

3. Jeśli konwerter powiedzie się, aparat powiązania <xref:System.Windows.Controls.ValidationRule> sprawdza, <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> czy istnieją <xref:System.Windows.Controls.ValidationStep.ConvertedProposedValue> jakieś <xref:System.Windows.Data.Binding>obiekty niestandardowe zdefiniowane, którego jest ustawiona na <xref:System.Windows.Controls.ValidationRule.Validate%2A> to, w którym to przypadku wywołuje metodę na każdym, <xref:System.Windows.Controls.ValidationRule> który ma <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> ustawiony, <xref:System.Windows.Controls.ValidationStep.ConvertedProposedValue> dopóki jeden z nich nie wpadnie na błąd lub dopóki wszystkie z nich przekazać.

4. Aparat wiązania ustawia właściwość źródło.

5. Aparat powiązania sprawdza, czy <xref:System.Windows.Controls.ValidationRule> istnieją jakieś <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> obiekty <xref:System.Windows.Controls.ValidationStep.UpdatedValue> niestandardowe <xref:System.Windows.Data.Binding>zdefiniowane, którego <xref:System.Windows.Controls.ValidationRule.Validate%2A> jest ustawiona na to, w którym to przypadku wywołuje metodę na każdym, <xref:System.Windows.Controls.ValidationRule> który ma <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> ustawiony, <xref:System.Windows.Controls.ValidationStep.UpdatedValue> dopóki jeden z nich nie wpadnie na błąd lub dopóki wszystkie z nich przechodzą. Jeśli <xref:System.Windows.Controls.DataErrorValidationRule> a jest skojarzony z <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> powiązaniem i <xref:System.Windows.Controls.ValidationStep.UpdatedValue>jego <xref:System.Windows.Controls.DataErrorValidationRule> jest ustawiona na wartość domyślną, jest sprawdzana w tym momencie. W tym momencie jest <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> sprawdzane wszelkie powiązania, które ma ustawioną. `true`

6. Aparat powiązania sprawdza, czy <xref:System.Windows.Controls.ValidationRule> istnieją jakieś <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> obiekty <xref:System.Windows.Controls.ValidationStep.CommittedValue> niestandardowe <xref:System.Windows.Data.Binding>zdefiniowane, którego <xref:System.Windows.Controls.ValidationRule.Validate%2A> jest ustawiona na to, w którym to przypadku wywołuje metodę na każdym, <xref:System.Windows.Controls.ValidationRule> który ma <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> ustawiony, <xref:System.Windows.Controls.ValidationStep.CommittedValue> dopóki jeden z nich nie wpadnie na błąd lub dopóki wszystkie z nich przechodzą.

Jeśli <xref:System.Windows.Controls.ValidationRule> a nie przechodzi w dowolnym momencie w całym <xref:System.Windows.Controls.ValidationError> tym procesie, <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> aparat wiązania tworzy obiekt i dodaje go do kolekcji elementu powiązanego. Przed aparat wiązania <xref:System.Windows.Controls.ValidationRule> uruchamia obiekty w dowolnym kroku, <xref:System.Windows.Controls.ValidationError> usuwa wszelkie, <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> które zostały dodane do dołączonej właściwości elementu powiązanego podczas tego kroku. Na <xref:System.Windows.Controls.ValidationRule> przykład jeśli, <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> którego <xref:System.Windows.Controls.ValidationStep.UpdatedValue> jest ustawiona na niepowodzenie, następnym razem proces sprawdzania <xref:System.Windows.Controls.ValidationError> poprawności występuje, <xref:System.Windows.Controls.ValidationRule> aparat <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> wiązania <xref:System.Windows.Controls.ValidationStep.UpdatedValue>usuwa, że bezpośrednio przed wywołuje dowolny, który ma ustawione na .

Gdy <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> nie jest <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> pusty, dołączona właściwość `true`elementu jest ustawiona na . Ponadto jeśli <xref:System.Windows.Data.Binding.NotifyOnValidationError%2A> właściwość <xref:System.Windows.Data.Binding> jest ustawiona na `true`, a <xref:System.Windows.Controls.Validation.Error?displayProperty=nameWithType> następnie aparat wiązania podnosi dołączone zdarzenie na elemencie.

Należy również zauważyć, że prawidłowy transfer wartości w obu kierunkach (cel do źródła lub źródła do docelowego) czyści dołączoną <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> właściwość.

Jeśli powiązanie albo <xref:System.Windows.Controls.ExceptionValidationRule> ma skojarzone z nim <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> lub miał `true` właściwość jest ustawiona i wyjątek jest zgłaszany, gdy aparat <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>powiązania ustawia źródło, aparat powiązania sprawdza, czy istnieje . Można użyć wywołania <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A> zwrotnego, aby zapewnić niestandardowy program obsługi wyjątków. Jeśli <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A> nie jest określony <xref:System.Windows.Data.Binding>na , aparat <xref:System.Windows.Controls.ValidationError> wiązania tworzy z wyjątkiem <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> i dodaje go do kolekcji elementu powiązanego.

## <a name="debugging-mechanism"></a>Mechanizm debugowania

Można ustawić dołączone właściwości <xref:System.Diagnostics.PresentationTraceSources.TraceLevel%2A?displayProperty=nameWithType> na obiekt związany z powiązaniem, aby otrzymywać informacje o stanie określonego powiązania.

## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Controls.DataErrorValidationRule>
- [Powiązanie z wynikami kwerendy LINQ](../../framework/wpf/data/how-to-bind-to-the-results-of-a-linq-query.md)
- [Powiązanie danych](../../framework/wpf/advanced/optimizing-performance-data-binding.md)
- [Demonstracja powiązania danych][data-binding-demo]
- [Artykuły do artykułów](../../framework/wpf/data/data-binding-how-to-topics.md)
- [Wiązanie ze źródłem danych ADO.NET](../../framework/wpf/data/how-to-bind-to-an-ado-net-data-source.md)

[data-binding-demo]: https://github.com/microsoft/WPF-Samples/tree/master/Sample%20Applications/DataBindingDemo "aplikacja demonstracyjna wiązania danych"
