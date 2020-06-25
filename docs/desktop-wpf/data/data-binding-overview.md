---
title: Omówienie powiązań danych
description: Dowiedz się więcej o różnych źródłach danych, które można dodać do projektu w Windows Presentation Foundation dla platformy .NET Core. Źródła danych mogą być powiązane z elementami XAML w celu tworzenia aplikacji dynamicznych.
author: adegeo
ms.date: 09/19/2019
ms.author: adegeo
dev_langs:
- csharp
- vb
ms.openlocfilehash: 829c93e97990b87e6e568614236de9708ef080d9
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325749"
---
# <a name="data-binding-overview-in-wpf"></a>Omówienie powiązań danych w WPF

Powiązanie danych w Windows Presentation Foundation (WPF) zapewnia prostą i spójność aplikacji do prezentowania i korzystania z danych. Elementy mogą być powiązane z danymi z różnych źródeł danych w postaci obiektów .NET i XML. <xref:System.Windows.Controls.ContentControl>Takie jak <xref:System.Windows.Controls.Button> i dowolne <xref:System.Windows.Controls.ItemsControl> , takie jak <xref:System.Windows.Controls.ListBox> i <xref:System.Windows.Controls.ListView> , mają wbudowaną funkcję do włączania elastycznego stylu pojedynczych elementów danych lub kolekcji elementów danych. Widoki sortowania, filtrowania i grupowania mogą być generowane na podstawie danych.

Funkcje wiązania danych w programie WPF mają kilka korzyści w porównaniu z tradycyjnymi modelami, w tym nieodłączną obsługę powiązań danych przez szeroki zakres właściwości, elastyczną reprezentację danych interfejsu użytkownika i czyste rozdzielenie logiki biznesowej z poziomu interfejsu użytkownika.

W tym artykule najpierw omówiono koncepcje podstawowe dla powiązania danych WPF, a następnie omówiono użycie <xref:System.Windows.Data.Binding> klasy i innych funkcji powiązania danych.

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="what-is-data-binding"></a>Co to jest powiązanie danych?

Powiązanie danych to proces, który nawiązuje połączenie między interfejsem użytkownika aplikacji i wyświetlanymi danymi. Jeśli powiązanie ma poprawne ustawienia, a dane udostępniają odpowiednie powiadomienia, gdy zmieniają się dane, elementy, które są powiązane z danymi, odzwierciedlają zmiany automatycznie. Powiązanie danych może również oznaczać, że jeśli zewnętrzna reprezentacja danych w elemencie ulegnie zmianie, dane bazowe można automatycznie zaktualizować, aby odzwierciedlały zmianę. Na przykład, jeśli użytkownik edytuje wartość w `TextBox` elemencie, wartość danych źródłowych zostanie automatycznie zaktualizowana w celu odzwierciedlenia tej zmiany.

Typowym zastosowaniem wiązania danych jest umieszczenie danych konfiguracji serwera lub lokalnego w postaci formularzy lub innych formantów interfejsu użytkownika. W WPF, pojęcie to jest rozwinięte w celu uwzględnienia powiązania szerokiej gamy właściwości z różnymi źródłami danych. W WPF właściwości zależności elementów mogą być powiązane z obiektami .NET (w tym obiektami ADO.NET lub obiektami skojarzonymi z usługami sieci Web i właściwościami sieci Web) oraz danymi XML.

Aby zapoznać się z przykładem powiązania danych, zapoznaj się z następującym interfejsem użytkownika aplikacji z [pokazu powiązania danych][data-binding-demo], który wyświetla listę elementów aukcji.

![Zrzut ekranu przykładowego powiązania danych](./media/data-binding-overview/demo.png "DataBinding_DataBindingDemo")

Aplikacja prezentuje następujące funkcje powiązania danych:

- Zawartość pola listy jest powiązana z kolekcją obiektów *AuctionItem* . Obiekt *AuctionItem* ma właściwości, takie jak *Description*, *StartPrice*, *StartDate*, *Category*, *SpecialFeatures*i tak dalej.

- Dane (obiekty*AuctionItem* ) wyświetlane w programie `ListBox` są szablonem, dzięki czemu dla każdego elementu są pokazywane opisy i bieżące ceny. Szablon jest tworzony przy użyciu <xref:System.Windows.DataTemplate> . Ponadto wygląd każdego elementu zależy od wartości *SpecialFeatures* wyświetlanej *AuctionItem* . Jeśli *SpecialFeatures* wartość *AuctionItem* jest *kolorem*, element ma niebieskie obramowanie. Jeśli zostanie *wyświetlona*wartość, element ma pomarańczowy obramowanie i gwiazdkę. Sekcja [tworzenia szablonów danych](#data-templating) zawiera informacje na temat tworzenia szablonów danych.

- Użytkownik może grupować, filtrować lub sortować dane przy użyciu `CheckBoxes` dostarczonego elementu. Na powyższym obrazie są zaznaczone pozycje **Grupuj według kategorii** i **Sortuj według kategorii i daty** `CheckBoxes` . Być może zauważono, że dane są pogrupowane na podstawie kategorii produktu, a nazwa kategorii jest w kolejności alfabetycznej. Trudno jest zauważyć z obrazu, ale elementy są również sortowane według daty rozpoczęcia w każdej kategorii. Sortowanie jest wykonywane przy użyciu *widoku kolekcji*. Sekcja [powiązanie z kolekcjami](#binding-to-collections) omawia widoki kolekcji.

- Gdy użytkownik wybierze element, <xref:System.Windows.Controls.ContentControl> wyświetla szczegóły wybranego elementu. To środowisko jest nazywane *scenariuszem dla szczegółów głównych*. Sekcja [scenariusz główny-szczegóły](#master-detail-binding-scenario) zawiera informacje na temat tego typu powiązania.

- Typ właściwości *StartDate* to <xref:System.DateTime> , która zwraca datę, która zawiera czas do milisekundy. W tej aplikacji użyto niestandardowego konwertera, aby wyświetlić krótszy ciąg daty. Sekcja [Konwersja danych](#data-conversion) zawiera informacje na temat konwerterów.

Gdy użytkownik wybierze przycisk *Dodaj produkt* , zostanie wyświetlony następujący formularz.

![Strona dodawania listy produktów](./media/data-binding-overview/demo-addproductlisting.png "DataBinding_Demo_AddProductListing")

Użytkownik może edytować pola w formularzu, przeglądać listę produktów przy użyciu krótkich lub szczegółowych okienek podglądu, a następnie wybrać opcję `Submit` dodania nowej listy produktów. Wszystkie istniejące ustawienia grupowania, filtrowania i sortowania zostaną zastosowane do nowego wpisu. W tym konkretnym przypadku element wprowadzony w powyższym obrazie będzie wyświetlany jako drugi element w kategorii *komputer* .

Nie pokazane w tym obrazie jest logiką walidacji podaną w *dacie rozpoczęcia* <xref:System.Windows.Controls.TextBox> . Jeśli użytkownik wprowadzi nieprawidłową datę (nieprawidłowe formatowanie lub datę przeszłą), użytkownik zostanie powiadomiony z <xref:System.Windows.Controls.ToolTip> i czerwonym wykrzyknikiem obok <xref:System.Windows.Controls.TextBox> . W sekcji [walidacja danych](#data-validation) omówiono sposób tworzenia logiki walidacji.

Przed przystąpieniem do różnych funkcji powiązania danych przedstawionych powyżej należy najpierw omówić podstawowe koncepcje, które są niezbędne do poznania powiązań danych WPF.

## <a name="basic-data-binding-concepts"></a>Podstawowe pojęcia dotyczące powiązań danych

Niezależnie od tego, jaki element jest powiązany, i charakter źródła danych, każde powiązanie zawsze jest zgodne z modelem przedstawionym na poniższej ilustracji.

![Diagram przedstawiający podstawowy model powiązań danych.](./media/data-binding-overview/basic-data-binding-diagram.png)

Jak widać na ilustracji, powiązanie danych jest zasadniczo mostkiem między obiektem docelowym powiązania a źródłem powiązania. Na rysunku przedstawiono następujące podstawowe koncepcje dotyczące powiązań danych WPF:

- Zwykle każde powiązanie ma cztery składniki:

  - Obiekt docelowy powiązania.
  - Właściwość docelowa.
  - Źródło powiązania.
  - Ścieżka do wartości w źródle powiązania do użycia.
  
  > Na przykład jeśli chcesz powiązać zawartość elementu z `TextBox` `Employee.Name` właściwością, obiektem docelowym jest `TextBox` , właściwość target jest <xref:System.Windows.Controls.TextBox.Text%2A> właściwością, wartość, która ma zostać użyta, jest *nazwą*, a obiektem źródłowym jest obiekt *Employee* .

- Właściwość Target musi być właściwością zależności. Większość <xref:System.Windows.UIElement> Właściwości to właściwości zależności i większość właściwości zależności, z wyjątkiem tych, które domyślnie obsługują powiązanie danych. (Tylko typy pochodne przez <xref:System.Windows.DependencyObject> mogą definiować właściwości zależności, a wszystkie <xref:System.Windows.UIElement> typy pochodzą od `DependencyObject` .)

- Chociaż nie pokazano na rysunku, należy zauważyć, że obiekt źródłowy powiązania nie jest ograniczony do niestandardowego obiektu .NET. Powiązanie danych WPF obsługuje dane w postaci obiektów .NET i XML. Aby udostępnić przykłady, Źródło powiązania może być obiektem <xref:System.Windows.UIElement> dowolnego obiektu listy, ADO.NET lub usługami sieci Web lub elementem XmlNode, który zawiera dane XML. Aby uzyskać więcej informacji, zobacz [Omówienie źródeł powiązań](../../framework/wpf/data/binding-sources-overview.md).

Należy pamiętać, że podczas ustanawiania powiązania, powiązanie celu powiązania *ze* źródłem powiązania. Na przykład, jeśli są wyświetlane pewne bazowe dane XML przy <xref:System.Windows.Controls.ListBox> użyciu powiązania danych, tworzysz powiązanie `ListBox` do danych XML.

Aby ustanowić powiązanie, należy użyć <xref:System.Windows.Data.Binding> obiektu. Pozostała część tego artykułu omawia wiele koncepcji skojarzonych z i niektórych właściwości i użycia `Binding` obiektu.

### <a name="direction-of-the-data-flow"></a>Kierunek przepływu danych

Jak wskazano strzałka na poprzednim rysunku, przepływ danych powiązania może przejść od celu powiązania do źródła powiązania (na przykład wartość źródłowa zmienia się, gdy użytkownik edytuje wartość `TextBox` ) i/lub ze źródła powiązania do obiektu docelowego powiązania (na przykład `TextBox` zawartość jest aktualizowana przy użyciu zmian w źródle powiązania), jeśli źródło powiązania udostępnia odpowiednie powiadomienia.

Możesz chcieć, aby aplikacja mogła umożliwić użytkownikom zmianę danych i propagowanie jej z powrotem do obiektu źródłowego. Możesz też nie chcieć, aby użytkownicy mogli aktualizować dane źródłowe. Przepływ danych można kontrolować, ustawiając <xref:System.Windows.Data.Binding.Mode?displayProperty=nameWithType> .

Na rysunku przedstawiono różne typy przepływów danych:

![Przepływ danych powiązań danych](./media/data-binding-overview/databinding-dataflow.png "DataBinding_DataFlow")

- <xref:System.Windows.Data.BindingMode.OneWay>powiązanie powoduje, że zmiany właściwości source mają automatycznie aktualizować właściwość target, ale zmiany właściwości target nie są propagowane do właściwości source. Ten typ powiązania jest odpowiedni, Jeśli powiązanie formantu jest niejawnie tylko do odczytu. Na przykład można powiązać ze źródłem danych, takim jak Giełda, lub być może Właściwość docelowa nie ma interfejsu sterującego do wprowadzania zmian, takich jak kolor tła związany z danymi tabeli. Jeśli nie ma potrzeby monitorowania zmian właściwości docelowej, użycie <xref:System.Windows.Data.BindingMode.OneWay> trybu powiązania pozwala uniknąć narzutu na <xref:System.Windows.Data.BindingMode.TwoWay> tryb powiązania.

- <xref:System.Windows.Data.BindingMode.TwoWay>powiązanie powoduje, że zmiany właściwości source lub Target mają być automatycznie aktualizowane. Ten typ powiązania jest odpowiedni do edytowalnych formularzy lub innych w pełni interaktywnych scenariuszy interfejsu użytkownika. Większość właściwości jest domyślnie <xref:System.Windows.Data.BindingMode.OneWay> powiązana, ale niektóre właściwości zależności (zazwyczaj właściwości kontrolek edytowalnych przez użytkownika, takich jak <xref:System.Windows.Controls.TextBox.Text?displayProperty=nameWithType> [pole wyboru i. IsChecked](xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked) domyślnie to <xref:System.Windows.Data.BindingMode.TwoWay> Binding. Programistyczny sposób, aby określić, czy właściwość zależności jest domyślnie wiążąca lub dwukierunkowo, ma uzyskać metadane właściwości <xref:System.Windows.DependencyProperty.GetMetadata%2A?displayProperty=nameWithType> , a następnie sprawdzić wartość logiczną <xref:System.Windows.FrameworkPropertyMetadata.BindsTwoWayByDefault%2A?displayProperty=nameWithType> właściwości.

- <xref:System.Windows.Data.BindingMode.OneWayToSource>jest odwrotnym <xref:System.Windows.Data.BindingMode.OneWay> powiązaniem; aktualizuje właściwość source po zmianie właściwości docelowej. Przykładowy scenariusz polega na tym, że wystarczy ponownie oszacować wartość źródłową z interfejsu użytkownika.

- Niezilustrowane na rysunku jest <xref:System.Windows.Data.BindingMode.OneTime> powiązanie, co powoduje, że Właściwość Source inicjuje właściwość docelową, ale nie propaguje kolejnych zmian. Jeśli zmieni się kontekst danych lub obiekt w kontekście danych ulegnie zmianie, zmiana *nie* zostanie odzwierciedlona we właściwości target. Ten typ powiązania jest odpowiedni, Jeśli migawka bieżącego stanu jest odpowiednia lub dane są rzeczywiście statyczne. Ten typ powiązania jest również przydatny, jeśli chcesz zainicjować właściwość docelową z jakąś wartością z właściwości source, a kontekst danych nie jest znany z góry. Ten tryb jest zasadniczo prostszym elementem <xref:System.Windows.Data.BindingMode.OneWay> powiązania, który zapewnia lepszą wydajność w przypadkach, gdy wartość źródłowa nie jest zmieniana.

Aby wykryć zmiany źródła (odpowiednie dla <xref:System.Windows.Data.BindingMode.OneWay> i <xref:System.Windows.Data.BindingMode.TwoWay> powiązania), Źródło musi zaimplementować odpowiedni mechanizm powiadamiania o zmianach właściwości, taki jak <xref:System.ComponentModel.INotifyPropertyChanged> . Zobacz [jak: implementowanie powiadomienia o zmianie właściwości](../../framework/wpf/data/how-to-implement-property-change-notification.md) dla przykładu <xref:System.ComponentModel.INotifyPropertyChanged> implementacji.

<xref:System.Windows.Data.Binding.Mode?displayProperty=nameWithType>Właściwość zawiera więcej informacji na temat trybów powiązań oraz przykład sposobu określania kierunku powiązania.

### <a name="what-triggers-source-updates"></a>Jakie aktualizacje źródła wyzwalaczy

Powiązania, które są <xref:System.Windows.Data.BindingMode.TwoWay> lub <xref:System.Windows.Data.BindingMode.OneWayToSource> nasłuchują zmian we właściwości docelowej i propagują je z powrotem do źródła, nazywanego aktualizacją źródła. Na przykład można edytować tekst pola tekstowego, aby zmienić źródłową wartość źródłową.

Jednak czy wartość źródłowa jest aktualizowana podczas edytowania tekstu lub po zakończeniu edycji tekstu, a kontrolka traci fokus? <xref:System.Windows.Data.Binding.UpdateSourceTrigger?displayProperty=nameWithType>Właściwość określa, jakie są wyzwalacze aktualizacji źródła. Punkty strzałki w prawo na poniższej ilustracji ilustrują rolę <xref:System.Windows.Data.Binding.UpdateSourceTrigger?displayProperty=nameWithType> właściwości.

![Diagram, który pokazuje rolę właściwości UpdateSourceTrigger.](./media/data-binding-overview/data-binding-updatesource-trigger.png)

Jeśli `UpdateSourceTrigger` wartość to <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged?displayProperty=nameWithType> , wówczas wartość wskazywana przez strzałkę w prawo <xref:System.Windows.Data.BindingMode.TwoWay> lub <xref:System.Windows.Data.BindingMode.OneWayToSource> powiązania jest aktualizowana zaraz po zmianie właściwości docelowej. Jeśli jednak `UpdateSourceTrigger` wartość jest, wówczas <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus> Ta wartość jest aktualizowana tylko przy użyciu nowej wartości, gdy właściwość target utraci fokus.

Podobnie jak w przypadku <xref:System.Windows.Data.Binding.Mode%2A> Właściwości różne właściwości zależności mają różne <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> wartości domyślne. Wartością domyślną dla większości właściwości zależności jest <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged> , podczas gdy `TextBox.Text` Właściwość ma wartość domyślną <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus> . `PropertyChanged`oznacza, że aktualizacje źródłowe są zwykle wykonywane za każdym razem, gdy zmienia się Właściwość docelowa. Natychmiastowe zmiany są odpowiednie dla pól wyboru i innych formantów prostych. Jednak w przypadku pól tekstowych aktualizowanie po każdym naciśnięciu klawisza może spowodować obniżenie wydajności i odmówić użytkownikowi zwykłej szansy w odniesieniu do wolnego miejsca i naprawić błędy pisowni przed zatwierdzeniem nowej wartości.

<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>Aby uzyskać informacje o tym, jak znaleźć wartość domyślną właściwości zależności, zobacz stronę właściwości.

W poniższej tabeli przedstawiono przykładowy scenariusz dla każdej <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> wartości przy użyciu <xref:System.Windows.Controls.TextBox> przykładu.

| UpdateSourceTrigger wartość | Po zaktualizowaniu wartości źródłowej | Przykładowy scenariusz dla pola tekstowego |
| ------------------------- | ---------------------------------- | ---------------------------- |
| `LostFocus`(domyślnie dla <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> ) | Gdy kontrolka TextBox utraci fokus. | Pole tekstowe, które jest skojarzone z logiką walidacji (zobacz [walidacja danych](#data-validation) poniżej). |
| `PropertyChanged` | Podczas wpisywania do <xref:System.Windows.Controls.TextBox> . | Kontrolki TextBox w oknie pokoju rozmowy. |
| `Explicit` | Gdy aplikacja jest wywoływana <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> . | Kontrolki TextBox w formularzu edytowalnym (aktualizuje wartości źródłowe tylko wtedy, gdy użytkownik kliknie przycisk Prześlij). |

Aby zapoznać się z przykładem, zobacz [How to: Control, kiedy tekst TextBox aktualizuje Źródło](../../framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md).

## <a name="creating-a-binding"></a>Tworzenie powiązania

Aby ponownie przeznaczyć niektóre koncepcje omówione w poprzednich sekcjach, należy ustanowić powiązanie przy użyciu <xref:System.Windows.Data.Binding> obiektu, a każde powiązanie ma zazwyczaj cztery składniki: obiekt docelowy powiązania, właściwość docelowa, Źródło powiązania i ścieżka do wartości źródłowej do użycia. W tej sekcji omówiono sposób konfigurowania powiązania.

Rozważmy następujący przykład, w którym obiekt źródłowy powiązania jest klasą o nazwie Moje *dane* , która jest zdefiniowana w przestrzeni nazw *SDKSample* . W celach demonstracyjnych Właściwość *właściwości ma nazwę* *ColorName* , której wartość jest równa "Red". W ten sposób ten przykład generuje przycisk z czerwonym tłem.

[!code-xaml[BindNonTextProperty](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/AutoConvertPropertyToColor.xaml#BindAutoConvertColor)]

Aby uzyskać więcej informacji na temat składni deklaracji powiązania i Przykłady sposobu konfigurowania powiązania w kodzie, zobacz temat [Omówienie deklaracji powiązań](../../framework/wpf/data/binding-declarations-overview.md).

Jeśli stosujemy ten przykład do naszego diagramu podstawowego, wynikowy rysunek wygląda następująco. Ten rysunek zawiera opis <xref:System.Windows.Data.BindingMode.OneWay> powiązania, ponieważ właściwość Background obsługuje <xref:System.Windows.Data.BindingMode.OneWay> powiązanie domyślnie.

![Diagram przedstawiający Właściwość tła powiązania danych.](./media/data-binding-overview/data-binding-button-background-example.png)

Możesz się zastanawiać, dlaczego to powiązanie działa, mimo że właściwość *ColorName* jest typu String, podczas gdy <xref:System.Windows.Controls.Control.Background%2A> Właściwość jest typu <xref:System.Windows.Media.Brush> . To powiązanie używa domyślnej konwersji typów, która została omówiona w sekcji [Konwersja danych](#data-conversion) .

### <a name="specifying-the-binding-source"></a>Określanie źródła powiązania

Zwróć uwagę, że w poprzednim przykładzie Źródło powiązania jest określone przez ustawienie właściwości [DockPanel. DataContext](xref:System.Windows.FrameworkElement.DataContext) . <xref:System.Windows.Controls.Button>Następnie dziedziczy <xref:System.Windows.FrameworkElement.DataContext%2A> wartość z <xref:System.Windows.Controls.DockPanel> elementu, który jest jego elementem nadrzędnym. Aby ponownie wykonać iterację, obiekt źródłowy powiązania jest jednym z czterech niezbędnych składników powiązania. W związku z tym bez określonego obiektu źródłowego powiązania, powiązanie nie będzie niczego robić.

Istnieje kilka sposobów, aby określić obiekt źródłowy powiązania. Używanie <xref:System.Windows.FrameworkElement.DataContext%2A> właściwości w elemencie nadrzędnym jest przydatne w przypadku powiązania wielu właściwości z tym samym źródłem. Jednak czasami może być bardziej odpowiednie, aby określić źródło powiązania dla poszczególnych deklaracji powiązań. W poprzednim przykładzie, zamiast używać <xref:System.Windows.FrameworkElement.DataContext%2A> właściwości, można określić źródło powiązania przez ustawienie <xref:System.Windows.Data.Binding.Source%2A?displayProperty=nameWithType> właściwości bezpośrednio w deklaracji powiązania przycisku, jak w poniższym przykładzie.

[!code-xaml[BindNonTextPropertyCompactBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/AutoConvertPropertyToColor.xaml#BindAutoConvertColorCompactBinding)]

Oprócz ustawiania <xref:System.Windows.FrameworkElement.DataContext%2A> właściwości elementu bezpośrednio, dziedziczenie <xref:System.Windows.FrameworkElement.DataContext%2A> wartości z elementu nadrzędnego (takiego jak przycisk w pierwszym przykładzie) i jawne określenie źródła powiązania przez ustawienie <xref:System.Windows.Data.Binding.Source%2A?displayProperty=nameWithType> Właściwości powiązania (na przykład przycisku w ostatnim przykładzie), można także użyć <xref:System.Windows.Data.Binding.ElementName?displayProperty=nameWithType> właściwości lub <xref:System.Windows.Data.Binding.RelativeSource?displayProperty=nameWithType> właściwości, aby określić źródło powiązania. <xref:System.Windows.Data.Binding.ElementName%2A>Właściwość jest przydatna w przypadku powiązania z innymi elementami w aplikacji, na przykład w przypadku używania suwaka do dostosowywania szerokości przycisku. <xref:System.Windows.Data.Binding.RelativeSource%2A>Właściwość jest przydatna, gdy powiązanie jest określone w <xref:System.Windows.Controls.ControlTemplate> lub <xref:System.Windows.Style> . Aby uzyskać więcej informacji, zobacz [How to: Określanie źródła powiązania](../../framework/wpf/data/how-to-specify-the-binding-source.md).

### <a name="specifying-the-path-to-the-value"></a>Określanie ścieżki do wartości

Jeśli źródło powiązania jest obiektem, należy użyć właściwości, <xref:System.Windows.Data.Binding.Path?displayProperty=nameWithType> Aby określić wartość do użycia dla powiązania. Jeśli tworzysz powiązanie z danymi XML, użyj <xref:System.Windows.Data.Binding.XPath?displayProperty=nameWithType> właściwości, aby określić wartość. W niektórych przypadkach może być stosowane do użycia <xref:System.Windows.Data.Binding.Path%2A> właściwości nawet wtedy, gdy dane są w formacie XML. Na przykład jeśli chcesz uzyskać dostęp do właściwości Nazwa zwróconego obiektu XmlNode (w wyniku zapytania XPath), należy użyć <xref:System.Windows.Data.Binding.Path%2A> właściwości oprócz <xref:System.Windows.Data.Binding.XPath%2A> właściwości.

Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Data.Binding.Path%2A> <xref:System.Windows.Data.Binding.XPath%2A> właściwości i.

Chociaż zostały wyróżnione, że <xref:System.Windows.Data.Binding.Path%2A> do wartości do użycia jest jeden z czterech niezbędnych składników powiązania, w scenariuszach, które chcesz powiązać z całym obiektem, wartość do użycia byłaby taka sama jak obiekt źródłowy powiązania. W takich przypadkach ma zastosowanie do nieokreślenia <xref:System.Windows.Data.Binding.Path%2A> . Rozważmy następujący przykład.

[!code-xaml[EmptyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/EmptyBinding.xaml#EmptyBinding)]

W powyższym przykładzie użyto składni pustego powiązania: {Binding}. W takim przypadku <xref:System.Windows.Controls.ListBox> dziedziczy element DataContext z nadrzędnego elementu DockPanel (nie pokazano w tym przykładzie). Jeśli ścieżka nie zostanie określona, wartością domyślną jest powiązanie z całym obiektem. Inaczej mówiąc, w tym przykładzie ścieżka została pozostawiona, ponieważ właściwość jest powiązana z <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> całym obiektem. (Zapoznaj się z sekcją [Powiązywanie z kolekcjami](#binding-to-collections) , aby uzyskać szczegółowe omówienie).

Oprócz powiązania z kolekcją, ten scenariusz jest również przydatny, gdy chcesz powiązać z całym obiektem, a nie tylko jedną właściwością obiektu. Na przykład jeśli obiekt źródłowy jest typu <xref:System.String> , można po prostu utworzyć powiązanie z samym ciągiem. Inny typowy scenariusz występuje, gdy chcesz powiązać element z obiektem z kilkoma właściwościami.

Może być konieczne zastosowanie logiki niestandardowej, aby dane były zrozumiałe dla powiązanej właściwości docelowej. Niestandardowa logika może mieć postać niestandardowego konwertera, jeśli konwersja typu domyślnego nie istnieje. Aby uzyskać informacje na temat konwerterów, zobacz [Konwersja danych](#data-conversion) .

### <a name="binding-and-bindingexpression"></a>Powiązywanie i BindingExpression

Przed zainstalowaniem innych funkcji i użycia powiązań danych warto wprowadzić <xref:System.Windows.Data.BindingExpression> klasę. Jak widać w poprzednich sekcjach, <xref:System.Windows.Data.Binding> Klasa jest klasą wysokiego poziomu dla deklaracji powiązania; zawiera wiele właściwości, które umożliwiają określenie charakterystyki powiązania. Klasa pokrewna, <xref:System.Windows.Data.BindingExpression> , jest obiektem źródłowym, który utrzymuje połączenie między źródłem a obiektem docelowym. Powiązanie zawiera wszystkie informacje, które mogą być współużytkowane przez kilka wyrażeń powiązań. A <xref:System.Windows.Data.BindingExpression> jest wyrażeniem wystąpienia, które nie może być współużytkowane i zawiera wszystkie informacje o wystąpieniu <xref:System.Windows.Data.Binding> .

Rozważmy poniższy przykład, gdzie `myDataObject` to wystąpienie `MyData` klasy, `myBinding` jest <xref:System.Windows.Data.Binding> obiektem źródłowym i `MyData` jest klasą zdefiniowaną, która zawiera właściwość ciągu o nazwie `MyDataProperty` . Ten przykład wiąże się z zawartością tekstową `myText` , wystąpieniem <xref:System.Windows.Controls.TextBlock> do `MyDataProperty` .

[!code-csharp[CodeOnlyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/ManualBinding.cs#CodeOnlyBinding)]
[!code-vb[CodeOnlyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/ManualBinding.vb#CodeOnlyBinding)]

Możesz użyć tego samego obiektu *powiązania* , aby utworzyć inne powiązania. Na przykład można użyć obiektu *powiązania* , aby powiązać zawartość tekstową pola wyboru z *MyDataProperty*. W tym scenariuszu będą dostępne dwa wystąpienia <xref:System.Windows.Data.BindingExpression> udostępniania obiektu *powiązania* .

<xref:System.Windows.Data.BindingExpression>Obiekt jest zwracany przez wywołanie <xref:System.Windows.Data.BindingOperations.GetBindingExpression%2A> obiektu powiązanego z danymi. W poniższych artykułach przedstawiono niektóre zastosowania <xref:System.Windows.Data.BindingExpression> klasy:

- [Pobieranie obiektu wiążącego z powiązanej własności docelowej](../../framework/wpf/data/how-to-get-the-binding-object-from-a-bound-target-property.md)

- [Określ, kiedy tekst TextBox aktualizuje Źródło](../../framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md)

## <a name="data-conversion"></a>Konwersja danych

W sekcji [Tworzenie powiązania](#creating-a-binding) przycisk ma kolor czerwony, ponieważ jego <xref:System.Windows.Controls.Control.Background%2A> Właściwość jest powiązana z właściwością ciągu o wartości "Red". Ta wartość ciągu działa, ponieważ w typie jest obecny konwerter typów służący <xref:System.Windows.Media.Brush> do konwersji wartości ciągu na <xref:System.Windows.Media.Brush> .

Dodanie tych informacji do rysunku w sekcji [Tworzenie powiązania](#creating-a-binding) wygląda następująco.

![Diagram, który pokazuje domyślną właściwość powiązania danych.](./media/data-binding-overview/data-binding-button-default-conversion.png)

Jednak co zrobić, jeśli zamiast posiadania właściwości typu String obiekt źródłowy powiązania ma właściwość *Color* typu <xref:System.Windows.Media.Color> ? W takim przypadku aby wiązanie działało, należy najpierw włączyć wartość właściwości *Color* do elementu, który <xref:System.Windows.Controls.Control.Background%2A> akceptuje właściwość. Należy utworzyć konwerter niestandardowy <xref:System.Windows.Data.IValueConverter> , implementując interfejs, jak w poniższym przykładzie.

[!code-csharp[CodeOnlyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/ColorBrushConverter.cs#ColorBrushConverter)]
[!code-vb[CodeOnlyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/ColorBrushConverter.vb#ColorBrushConverter)]

Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Data.IValueConverter>.

Teraz jest używany konwerter niestandardowy zamiast konwersji domyślnej. nasz diagram wygląda następująco.

![Diagram przedstawiający niestandardowy konwerter powiązań danych.](./media/data-binding-overview/data-binding-converter-color-example.png)

Aby przeprowadzić ponownie iterację, konwersje domyślne mogą być dostępne ze względu na konwertery typów, które są obecne w typie, z którym jest powiązany. Takie zachowanie będzie zależeć od tego, które konwertery typów są dostępne w miejscu docelowym. W razie wątpliwości Utwórz własny konwerter.

Poniżej przedstawiono niektóre typowe scenariusze, w których warto wdrożyć konwerter danych:

- Dane powinny być wyświetlane inaczej, w zależności od kultury. Na przykład możesz chcieć zaimplementować konwerter waluty lub konwerter daty/czasu kalendarza na podstawie Konwencji używanych w określonej kulturze.

- Używane dane nie muszą mieć potrzeby zmiany wartości tekstowej właściwości, ale zamiast tego należy zmienić inną wartość, na przykład źródło obrazu lub kolor lub styl wyświetlanego tekstu. Konwertery mogą być używane w tym wystąpieniu przez konwersję powiązania właściwości, która prawdopodobnie nie jest odpowiednia, na przykład wiązanie pola tekstowego z właściwością Background komórki tabeli.

- Więcej niż jeden formant lub wiele właściwości formantów są powiązane z tymi samymi danymi. W takim przypadku podstawowe powiązanie może po prostu wyświetlić tekst, podczas gdy inne powiązania obsługują konkretne problemy z wyświetlaniem, ale nadal używają tego samego powiązania jako informacji źródłowych.

- Właściwość docelowa ma kolekcję powiązań, które są określane <xref:System.Windows.Data.MultiBinding> . W przypadku programu należy <xref:System.Windows.Data.MultiBinding> użyć niestandardowych <xref:System.Windows.Data.IMultiValueConverter> do utworzenia końcowej wartości z wartości powiązań. Na przykład kolor może być obliczany na podstawie wartości czerwony, niebieski i zielony, które mogą być wartościami z tego samego lub różnych obiektów źródłowych powiązań. Zobacz <xref:System.Windows.Data.MultiBinding> , aby uzyskać przykłady i informacje.

## <a name="binding-to-collections"></a>Powiązanie z kolekcjami

Obiekt źródłowy powiązania może być traktowany jako pojedynczy obiekt, którego właściwości zawierają dane lub jako gromadzenie danych obiektów polimorficznych, które są często zgrupowane razem (na przykład wynik zapytania do bazy danych). Do tej pory omawiamy tylko powiązanie z pojedynczymi obiektami. Jednak powiązanie z kolekcją danych jest typowym scenariuszem. Na przykład typowym scenariuszem jest użycie <xref:System.Windows.Controls.ItemsControl> takich jak <xref:System.Windows.Controls.ListBox> , <xref:System.Windows.Controls.ListView> , lub <xref:System.Windows.Controls.TreeView> do wyświetlania kolekcji danych, na przykład w aplikacji pokazanej w sekcji [co to jest powiązanie danych](#what-is-data-binding) .

Na szczęście nadal obowiązuje nasz diagram podstawowy. Jeśli tworzysz powiązanie <xref:System.Windows.Controls.ItemsControl> do kolekcji, diagram wygląda następująco.

![Diagram, który pokazuje obiekt ItemsControl powiązań danych.](./media/data-binding-overview/data-binding-itemscontrol.png)

Jak pokazano na tym diagramie, aby powiązać <xref:System.Windows.Controls.ItemsControl> obiekt kolekcji, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A?displayProperty=nameWithType> Właściwość jest właściwością do użycia. Możesz traktować `ItemsSource` jako zawartość <xref:System.Windows.Controls.ItemsControl> . Powiązanie wynika z <xref:System.Windows.Data.BindingMode.OneWay> faktu, że `ItemsSource` Właściwość obsługuje `OneWay` powiązanie domyślnie.

### <a name="how-to-implement-collections"></a>Jak zaimplementować Kolekcje

Można wyliczyć wszystkie kolekcje, które implementują <xref:System.Collections.IEnumerable> interfejs. Jednak aby skonfigurować powiązania dynamiczne, tak aby wstawienia lub usunięcia w kolekcji automatycznie aktualizować interfejs użytkownika, kolekcja musi implementować <xref:System.Collections.Specialized.INotifyCollectionChanged> interfejs. Ten interfejs uwidacznia zdarzenie, które powinno być wywoływane za każdym razem, gdy źródłowa kolekcja ulegnie zmianie.

WPF udostępnia <xref:System.Collections.ObjectModel.ObservableCollection%601> klasę, która jest wbudowaną implementacją zbierania danych, która uwidacznia <xref:System.Collections.Specialized.INotifyCollectionChanged> interfejs. Aby w pełni obsługiwać transfer wartości danych z obiektów źródłowych do obiektów docelowych, każdy obiekt w kolekcji, który obsługuje właściwości możliwe do powiązania, musi również implementować <xref:System.ComponentModel.INotifyPropertyChanged> interfejs. Aby uzyskać więcej informacji, zobacz [Omówienie źródeł powiązań](../../framework/wpf/data/binding-sources-overview.md).

Przed zaimplementowaniem własnej kolekcji należy rozważyć użycie <xref:System.Collections.ObjectModel.ObservableCollection%601> lub jedną z istniejących klas kolekcji, takich jak <xref:System.Collections.Generic.List%601> , <xref:System.Collections.ObjectModel.Collection%601> , i <xref:System.ComponentModel.BindingList%601> , między innymi. Jeśli masz zaawansowany scenariusz i chcesz zaimplementować swoją własną kolekcję, rozważ użycie <xref:System.Collections.IList> , która zapewnia nieogólną kolekcję obiektów, do których można uzyskać dostęp za pomocą indeksu, i w ten sposób zapewnia najlepszą wydajność.

### <a name="collection-views"></a>Widoki kolekcji

Gdy <xref:System.Windows.Controls.ItemsControl> obiekt jest powiązany z kolekcją danych, można sortować, filtrować lub grupować dane. W tym celu należy użyć widoków kolekcji, które są klasami, które implementują <xref:System.ComponentModel.ICollectionView> interfejs.

#### <a name="what-are-collection-views"></a>Co to są widoki kolekcji?

Widok kolekcji to warstwa znajdująca się na początku kolekcji źródłowej powiązania, która umożliwia nawigowanie i wyświetlanie kolekcji źródłowej w oparciu o zapytania sortowania, filtrowania i grup, bez konieczności zmiany samej źródłowej kolekcji. Widok kolekcji utrzymuje również wskaźnik do bieżącego elementu w kolekcji. Jeśli kolekcja źródłowa implementuje <xref:System.Collections.Specialized.INotifyCollectionChanged> interfejs, zmiany zgłoszone przez <xref:System.Collections.Specialized.INotifyCollectionChanged.CollectionChanged> zdarzenie są propagowane do widoków.

Ponieważ widoki nie zmieniają źródłowej kolekcji źródłowej, do każdej kolekcji źródłowej można skojarzyć wiele widoków. Na przykład może istnieć Kolekcja obiektów *zadań* . Korzystając z widoków, można wyświetlać te same dane na różne sposoby. Na przykład po lewej stronie strony możesz chcieć pokazać zadania posortowane według priorytetu i po prawej stronie pogrupowane według obszaru.

#### <a name="how-to-create-a-view"></a>Jak utworzyć widok

Jednym ze sposobów tworzenia i używania widoku jest bezpośrednie utworzenie wystąpienia obiektu widoku, a następnie użycie go jako źródła powiązania. Rozważmy na przykład aplikację [demonstracyjną powiązania danych][data-binding-demo] pokazaną w sekcji [co to jest powiązanie danych](#what-is-data-binding) . Aplikacja została zaimplementowana w taki sposób, że <xref:System.Windows.Controls.ListBox> tworzy powiązania do widoku nad zbieraniem danych, a nie bezpośrednio z kolekcją danych. Poniższy przykład jest wyodrębniany z aplikacji [demonstracyjnej powiązania danych][data-binding-demo] . <xref:System.Windows.Data.CollectionViewSource>Klasa jest serwerem proxy XAML klasy, która dziedziczy z <xref:System.Windows.Data.CollectionView> . W tym konkretnym przykładzie <xref:System.Windows.Data.CollectionViewSource.Source%2A> Widok jest powiązany z kolekcją *AuctionItems* (typu <xref:System.Collections.ObjectModel.ObservableCollection%601> ) bieżącego obiektu aplikacji.

[!code-xaml[CollectionView](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml#CollectionView)]

*ListingDataView* zasobów następnie służy jako źródło powiązań dla elementów w aplikacji, takich jak <xref:System.Windows.Controls.ListBox> .

[!code-xaml[ListBoxCollectionView](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml#ListBoxCollectionView)]

Aby utworzyć inny widok dla tej samej kolekcji, można utworzyć inne <xref:System.Windows.Data.CollectionViewSource> wystąpienie i nadać mu inną `x:Key` nazwę.

W poniższej tabeli przedstawiono typy danych widoku, które są tworzone jako domyślny widok kolekcji lub <xref:System.Windows.Data.CollectionViewSource> na podstawie typu kolekcji źródłowej.

| Typ kolekcji źródłowej                    | Typ widoku kolekcji | Uwagi |
| ----------------------------------------- | -------------------- | ----- |
| <xref:System.Collections.IEnumerable>     | Typ wewnętrzny oparty na<xref:System.Windows.Data.CollectionView> | Nie można grupować elementów. |
| <xref:System.Collections.IList>           | <xref:System.Windows.Data.ListCollectionView> | Najlepszy. |
| <xref:System.ComponentModel.IBindingList> | <xref:System.Windows.Data.BindingListCollectionView> | |

#### <a name="using-a-default-view"></a>Korzystanie z widoku domyślnego

Określanie widoku kolekcji jako źródła powiązania jest jednym ze sposobów tworzenia i używania widoku kolekcji. WPF tworzy również domyślny widok kolekcji dla każdej kolekcji używanej jako źródło powiązania. Jeśli powiążesz bezpośrednio z kolekcją, program WPF tworzy powiązanie z widokiem domyślnym. Ten domyślny widok jest współużytkowany przez wszystkie powiązania z tą samą kolekcją, więc zmiana została wprowadzona w widoku domyślnym przez jedną kontrolkę powiązaną lub kod (na przykład sortowanie lub zmiana w bieżącym wskaźniku elementu, omówiona później) jest odzwierciedlona we wszystkich innych powiązaniach z tą samą kolekcją.

Aby uzyskać widok domyślny, należy użyć <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> metody. Aby zapoznać się z przykładem, zobacz temat [pobieranie widoku domyślnego kolekcji danych](../../framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md).

#### <a name="collection-views-with-adonet-datatables"></a>Widoki kolekcji z ADO.NET DataTables

Aby zwiększyć wydajność, widoki kolekcji dla ADO.NET <xref:System.Data.DataTable> lub <xref:System.Data.DataView> obiektów delegowane sortowanie i filtrowanie do <xref:System.Data.DataView> , co powoduje, że sortowanie i filtrowanie ma być współużytkowane przez wszystkie widoki kolekcji źródła danych. Aby umożliwić każdemu widokowi kolekcji sortowanie i filtrowanie niezależnie, zainicjuj każdy widok kolekcji własnym <xref:System.Data.DataView> obiektem.

#### <a name="sorting"></a>Sortowanie

Jak wspomniano wcześniej, widoki mogą zastosować porządek sortowania do kolekcji. Ponieważ istnieje w źródłowej kolekcji, dane mogą lub nie mieć odpowiedniej, powiązanej kolejności. Widok nad kolekcją pozwala na nakładanie zamówienia lub zmianę kolejności domyślnej na podstawie podanych kryteriów porównania. Ponieważ jest to oparty na kliencie widok danych, typowym scenariuszem jest to, że użytkownik może chcieć sortować kolumny danych tabelarycznych według wartości, do której odnosi się kolumna. Korzystając z widoków, można zastosować takie sortowanie oparte na użytkowniku, ponownie bez wprowadzania jakichkolwiek zmian w źródłowej kolekcji, a nawet w przypadku ponowienia kwerendy zawartości kolekcji. Aby zapoznać się z przykładem, zobacz [Sortuj kolumnę GridView po kliknięciu nagłówka](../../framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md).

Poniższy przykład przedstawia logikę sortowania "Sortuj według kategorii i daty" <xref:System.Windows.Controls.CheckBox> w interfejsie użytkownika aplikacji w sekcji [co to jest powiązanie danych](#what-is-data-binding) .

[!code-csharp[AddSortChecked](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml.cs#AddSortChecked)]
[!code-vb[AddSortChecked](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/CollectionView.xaml.vb#AddSortChecked)]

#### <a name="filtering"></a>Filtrowanie

Widoki mogą również stosować filtr do kolekcji, aby widok pokazywał tylko określony podzestaw pełnej kolekcji. Można filtrować warunek w danych. Na przykład w przypadku działania aplikacji w sekcji [co to jest powiązanie danych](#what-is-data-binding) "Pokaż tylko opłaty" <xref:System.Windows.Controls.CheckBox> zawiera logikę umożliwiającą odfiltrowanie elementów, które mają koszt $25 lub więcej. Poniższy kod jest wykonywany, aby ustawić *ShowOnlyBargainsFilter* jako <xref:System.Windows.Data.CollectionViewSource.Filter> program obsługi zdarzeń, gdy <xref:System.Windows.Controls.CheckBox> jest wybrany.

[!code-csharp[ListingViewFilter](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml.cs#ListingViewFilter)]
[!code-vb[ListingViewFilter](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/CollectionView.xaml.vb#ListingViewFilter)]

Program obsługi zdarzeń *ShowOnlyBargainsFilter* ma następującą implementację.

[!code-csharp[FilterEvent](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml.cs#FilterEvent)]
[!code-vb[FilterEvent](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/CollectionView.xaml.vb#FilterEvent)]

Jeśli używasz jednej z <xref:System.Windows.Data.CollectionView> klas bezpośrednio zamiast <xref:System.Windows.Data.CollectionViewSource> , użyj <xref:System.Windows.Data.CollectionView.Filter%2A> właściwości, aby określić wywołanie zwrotne. Aby zapoznać się z przykładem, zobacz [filtrowanie danych w widoku](../../framework/wpf/data/how-to-filter-data-in-a-view.md).

#### <a name="grouping"></a>Grupowanie

Z wyjątkiem wewnętrznej klasy, która przegląda <xref:System.Collections.IEnumerable> kolekcję, wszystkie widoki kolekcji obsługują *grupowanie*, dzięki czemu użytkownik może podzielić kolekcję w widoku kolekcji na grupy logiczne. Grupy mogą być jawne, gdzie użytkownik dostarcza listę grup lub niejawną, w której grupy są generowane dynamicznie w zależności od danych.

Poniższy przykład przedstawia logikę "Grupuj według kategorii" <xref:System.Windows.Controls.CheckBox> .

[!code-csharp[ListingGroupCheck](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml.cs#ListingGroupCheck)]
[!code-vb[ListingGroupCheck](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/CollectionView.xaml.vb#ListingGroupCheck)]

Aby poznać inny przykład grupowania, zobacz [Grupuj elementy w ListView, który implementuje GridView](../../framework/wpf/controls/how-to-group-items-in-a-listview-that-implements-a-gridview.md).

#### <a name="current-item-pointers"></a>Wskaźniki bieżącego elementu

Widoki obsługują również koncepcję bieżącego elementu. Możesz nawigować przez obiekty w widoku kolekcji. Podczas nawigowania, przenosisz wskaźnik elementu, który umożliwia pobranie obiektu, który istnieje w danej lokalizacji w kolekcji. Aby zapoznać się z przykładem, zobacz [nawigowanie po obiektach w CollectionView danych](../../framework/wpf/data/how-to-navigate-through-the-objects-in-a-data-collectionview.md).

Ponieważ WPF tworzy powiązanie z kolekcją tylko przy użyciu widoku (określony przez Ciebie widok lub widok domyślny kolekcji), wszystkie powiązania z kolekcjami mają aktualny wskaźnik elementu. Po powiązaniu do widoku znak ukośnika ("/") w `Path` wartości wyznacza bieżący element widoku. W poniższym przykładzie kontekst danych jest widokiem kolekcji. Pierwszy wiersz wiąże się z kolekcją. Drugi wiersz tworzy powiązanie z bieżącym elementem w kolekcji. Trzeci wiersz wiąże się z `Description` właściwością bieżącego elementu w kolekcji.

```xaml
<Button Content="{Binding }" />
<Button Content="{Binding Path=/}" />
<Button Content="{Binding Path=/Description}" />
```

Składnia ukośnika i właściwości może być również skumulowana w celu przechodzenia do hierarchii kolekcji. Poniższy przykład tworzy powiązanie z bieżącym elementem kolekcji o nazwie `Offices` , która jest właściwością bieżącego elementu kolekcji źródłowej.

```xaml
<Button Content="{Binding /Offices/}" />
```

Na wskaźnik bieżącego elementu może mieć wpływ każde sortowanie lub filtrowanie, które jest stosowane do kolekcji. Sortowanie zachowuje bieżący wskaźnik elementu na ostatnim wybranym elemencie, ale widok kolekcji jest teraz restrukturyzacją. (Prawdopodobnie wybrany element znajdował się na początku listy, ale teraz wybrany element może znajdować się w środku). Filtrowanie zachowuje wybrany element, jeśli zaznaczenie pozostanie w widoku po filtrowaniu. W przeciwnym razie wskaźnik bieżącego elementu jest ustawiany na pierwszy element filtrowanego widoku kolekcji.

#### <a name="master-detail-binding-scenario"></a>Scenariusz powiązań wzorzec-szczegóły

Pojęcie bieżącego elementu jest przydatne nie tylko w przypadku nawigacji elementów w kolekcji, ale również dla scenariusza powiązania szczegółów wzorca. Rozważ ponowne użycie interfejsu użytkownika aplikacji w sekcji [co to jest powiązanie danych](#what-is-data-binding) . W tej aplikacji wybór w obszarze <xref:System.Windows.Controls.ListBox> określa zawartość wyświetlaną w <xref:System.Windows.Controls.ContentControl> . Aby umieścić ją w inny sposób, gdy <xref:System.Windows.Controls.ListBox> element jest zaznaczony, <xref:System.Windows.Controls.ContentControl> pokazuje szczegóły wybranego elementu.

Scenariusz wzorzec-szczegóły można zaimplementować po prostu, mając co najmniej dwie kontrolki powiązane z tym samym widokiem. Poniższy przykład z [pokazu powiązania danych][data-binding-demo] pokazuje adiustację <xref:System.Windows.Controls.ListBox> i są <xref:System.Windows.Controls.ContentControl> widoczne w interfejsie użytkownika aplikacji w sekcji [co to jest powiązanie danych](#what-is-data-binding) .

[!code-xaml[ListBoxContentControl](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml#ListBoxContentControl)]

Zwróć uwagę, że obie kontrolki są powiązane z tym samym źródłem, *listingDataView* zasób statyczny (Zobacz definicję tego zasobu w [sekcji Jak utworzyć widok](#how-to-create-a-view)). To powiązanie działa, ponieważ gdy pojedynczy obiekt ( <xref:System.Windows.Controls.ContentControl> w tym przypadku) jest powiązany z widokiem kolekcji, automatycznie wiąże się z <xref:System.Windows.Data.CollectionView.CurrentItem%2A> widokiem. <xref:System.Windows.Data.CollectionViewSource>Obiekty automatycznie synchronizują walutę i zaznaczenie. Jeśli formant listy nie jest powiązany z <xref:System.Windows.Data.CollectionViewSource> obiektem, jak w tym przykładzie, należy ustawić jego właściwość na, aby <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> `true` to działało.

Aby zapoznać się z innymi przykładami, zobacz [Powiązywanie z kolekcją i wyświetlanie informacji na podstawie wyboru](../../framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md) i [Używanie wzorca-szczegóły wzorca z danymi hierarchicznymi](../../framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md).

Być może zauważono, że powyższy przykład używa szablonu. W rzeczywistości dane nie są wyświetlane w żądany sposób bez użycia szablonów (jawnie używany przez <xref:System.Windows.Controls.ContentControl> i jeden niejawnie używany przez <xref:System.Windows.Controls.ListBox> ). Teraz przejdźmy do tworzenia szablonów danych w następnej sekcji.

## <a name="data-templating"></a>Tworzenie szablonów danych

Bez korzystania z szablonów danych nasz interfejs użytkownika aplikacji w sekcji [co to jest powiązanie danych](#what-is-data-binding) będzie wyglądać następująco.

![Demonstracja powiązania danych bez szablonów danych](./media/data-binding-overview/demo-no-template.png)

Jak pokazano w przykładzie w poprzedniej sekcji, zarówno <xref:System.Windows.Controls.ListBox> formant, jak i <xref:System.Windows.Controls.ContentControl> są powiązane z całymi obiektami kolekcji (lub dokładniej, widok nad obiektem kolekcji) *AuctionItem*s. Bez określonych instrukcji dotyczących sposobu wyświetlania zbierania danych program <xref:System.Windows.Controls.ListBox> wyświetla ciąg reprezentujący każdy obiekt w kolekcji źródłowej, a następnie <xref:System.Windows.Controls.ContentControl> wyświetla ciąg reprezentujący obiekt, z którym jest powiązany.

Aby rozwiązać ten problem, aplikacja definiuje <xref:System.Windows.DataTemplate?text=DataTemplates> . Jak pokazano w przykładzie w poprzedniej sekcji, <xref:System.Windows.Controls.ContentControl> jawnie używa szablonu danych *detailsProductListingTemplate* . <xref:System.Windows.Controls.ListBox>Formant niejawnie używa następującego szablonu danych podczas wyświetlania obiektów *AuctionItem* w kolekcji.

[!code-xaml[AuctionItemDataTemplate](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml#AuctionItemDataTemplate)]

Korzystając z tych dwóch szablonów danych, wynikowy interfejs użytkownika jest wyświetlany w sekcji [co to jest powiązanie danych](#what-is-data-binding) . Jak widać na tym zrzucie ekranu, poza umożliwieniem umieszczania danych w kontrolkach, szablony danych umożliwiają definiowanie atrakcyjnych wizualizacji na potrzeby Twoich potrzeb. Na przykład <xref:System.Windows.DataTrigger> s są używane w powyższych, <xref:System.Windows.DataTemplate> dzięki czemu *AuctionItem*s z wartością *SpecialFeatures* z *wyróżnieniem* będzie wyświetlana z pomarańczowym obramowaniem i gwiazdką.

Aby uzyskać więcej informacji na temat szablonów danych, zobacz [Omówienie tworzenia szablonów danych](../../framework/wpf/data/data-templating-overview.md).

## <a name="data-validation"></a>Walidacja danych

Większość aplikacji, które wprowadzają dane wejściowe użytkownika, musi mieć logikę sprawdzania poprawności, aby upewnić się, że użytkownik wprowadził oczekiwane informacje. Sprawdzanie poprawności może opierać się na typie, zakresie, formacie lub innych wymaganiach specyficznych dla aplikacji. W tej sekcji omówiono sposób działania walidacji danych w WPF.

### <a name="associating-validation-rules-with-a-binding"></a>Kojarzenie reguł walidacji z powiązaniem

Model powiązania danych WPF umożliwia skojarzenie <xref:System.Windows.Data.Binding.ValidationRules%2A> z <xref:System.Windows.Data.Binding> obiektem. Na przykład poniższy przykład tworzy powiązanie z <xref:System.Windows.Controls.TextBox> właściwością o nazwie `StartPrice` i dodaje <xref:System.Windows.Controls.ExceptionValidationRule> obiekt do <xref:System.Windows.Data.Binding.ValidationRules%2A?displayProperty=nameWithType> właściwości.

[!code-xaml[TextboxStartPrice](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/DataValidation.xaml#TextboxStartPrice)]

<xref:System.Windows.Controls.ValidationRule>Obiekt sprawdza, czy wartość właściwości jest prawidłowa. WPF ma dwa typy wbudowanych <xref:System.Windows.Controls.ValidationRule> obiektów:

- <xref:System.Windows.Controls.ExceptionValidationRule>Sprawdza wyjątki zgłoszone podczas aktualizacji właściwości źródła powiązania. W poprzednim przykładzie `StartPrice` jest typu Integer. Gdy użytkownik wprowadzi wartość, której nie można przekonwertować na liczbę całkowitą, zostanie zgłoszony wyjątek, co spowoduje oznaczenie powiązania jako nieprawidłowy. Alternatywna składnia służąca do ustawienia <xref:System.Windows.Controls.ExceptionValidationRule> jawnie polega na ustawieniu <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> właściwości na `true` <xref:System.Windows.Data.Binding> <xref:System.Windows.Data.MultiBinding> obiekt lub.

- <xref:System.Windows.Controls.DataErrorValidationRule>Obiekt sprawdza błędy zgłaszane przez obiekty, które implementują <xref:System.ComponentModel.IDataErrorInfo> interfejs. Aby zapoznać się z przykładem użycia tej reguły walidacji, zobacz <xref:System.Windows.Controls.DataErrorValidationRule> . Alternatywna składnia służąca do ustawienia <xref:System.Windows.Controls.DataErrorValidationRule> jawnie polega na ustawieniu <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> właściwości na `true` <xref:System.Windows.Data.Binding> <xref:System.Windows.Data.MultiBinding> obiekt lub.

Możesz również utworzyć własną regułę walidacji, wyprowadzając ją z <xref:System.Windows.Controls.ValidationRule> klasy i implementując <xref:System.Windows.Controls.ValidationRule.Validate%2A> metodę. W poniższym przykładzie przedstawiono regułę używaną przez *listę Dodaj produkt* "Data rozpoczęcia" <xref:System.Windows.Controls.TextBox> z sekcji [co to jest powiązanie danych](#what-is-data-binding) .

[!code-csharp[FutureDateRule](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/FutureDateRule.cs#FutureDateRule)]
[!code-vb[FutureDateRule](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/FutureDateRule.vb#FutureDateRule)]

*StartDateEntryForm* <xref:System.Windows.Controls.TextBox> używa tego *FutureDateRule*, jak pokazano w poniższym przykładzie.

[!code-xaml[TextboxStartDate](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/DataValidation.xaml#TextboxStartDate)]

Ponieważ <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> wartość to <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged> , aparat powiązań aktualizuje wartość źródłową przy każdym naciśnięciu klawisza, co oznacza, że sprawdza wszystkie reguły w <xref:System.Windows.Data.Binding.ValidationRules%2A> kolekcji przy każdym naciśnięciu klawisza. Omawiamy tę procedurę w sekcji proces walidacji.

### <a name="providing-visual-feedback"></a>Zapewnianie opinii wizualnych

Jeśli użytkownik wprowadzi nieprawidłową wartość, może być konieczne podanie pewnych informacji zwrotnych dotyczących błędu w interfejsie użytkownika aplikacji. Jednym ze sposobów zapewnienia takiej opinii jest ustawienie <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType> Właściwości dołączonej na niestandardową <xref:System.Windows.Controls.ControlTemplate> . Jak pokazano w poprzedniej podsekcji, *StartDateEntryForm* <xref:System.Windows.Controls.TextBox> używa <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> metody o nazwie *validationTemplate*. W poniższym przykładzie przedstawiono definicję *validationTemplate*.

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/DataValidation.xaml#ControlTemplate)]

<xref:System.Windows.Controls.AdornedElementPlaceholder>Element określa, gdzie powinna zostać umieszczona kontrolka.

Ponadto można również użyć, <xref:System.Windows.Controls.ToolTip> Aby wyświetlić komunikat o błędzie. Zarówno *StartDateEntryForm* , jak i *StartPriceEntryForm* <xref:System.Windows.Controls.TextBox> es używają stylu *textStyleTextBox*, który tworzy, <xref:System.Windows.Controls.ToolTip> który wyświetla komunikat o błędzie. W poniższym przykładzie przedstawiono definicję *textStyleTextBox*. Dołączona właściwość <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true` wtedy, gdy co najmniej jedno powiązanie we właściwościach elementu powiązanego jest w błędzie.

[!code-xaml[TextBoxStyle](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/DataValidation.xaml#TextBoxStyle)]

Przy użyciu niestandardowych <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> i <xref:System.Windows.Controls.ToolTip> , *StartDateEntryForm* wygląda następująco, <xref:System.Windows.Controls.TextBox> gdy występuje błąd walidacji.

![Błąd walidacji powiązania danych](./media/data-binding-overview/demo-validation-date.png "DataBindingDemo_Validation")

Jeśli masz <xref:System.Windows.Data.Binding> skojarzone reguły walidacji, ale nie określisz <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> w kontrolce powiązanej, <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> zostanie użyta wartość domyślna do powiadomienia użytkowników o błędzie walidacji. Wartość domyślna <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> to szablon kontrolki, który definiuje czerwone obramowanie w warstwie modułu definiowania układu. Przy użyciu wartości domyślnej <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> i <xref:System.Windows.Controls.ToolTip> , interfejs użytkownika *StartPriceEntryForm* wygląda następująco, <xref:System.Windows.Controls.TextBox> gdy występuje błąd walidacji.

![Błąd walidacji powiązania danych](./media/data-binding-overview/demo-validation-price.png "DataBindingDemo_ValidationDefault")

Aby zapoznać się z przykładem sposobu zapewnienia logiki do sprawdzania poprawności wszystkich kontrolek w oknie dialogowym, zobacz sekcję niestandardowe okna dialogowe w oknach dialogowych [Przegląd](../../framework/wpf/app-development/dialog-boxes-overview.md).

### <a name="validation-process"></a>Proces weryfikacji

Walidacja zwykle odbywa się, gdy wartość docelowa jest transferowana do właściwości source powiązania. Ten transfer jest realizowany <xref:System.Windows.Data.BindingMode.TwoWay> i <xref:System.Windows.Data.BindingMode.OneWayToSource> powiązania. Aby ponownie wykonać iterację, co powoduje, że aktualizacja źródłowa zależy od wartości <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> właściwości, zgodnie z opisem w sekcji [co to są aktualizacje źródła wyzwalaczy](#what-triggers-source-updates) .

Poniższe elementy opisują proces *sprawdzania poprawności* . Jeśli w dowolnym momencie w trakcie tego procesu wystąpi błąd walidacji lub inny typ błędu, proces zostanie zatrzymany:

1. Aparat powiązań sprawdza, czy istnieją jakieś obiekty niestandardowe <xref:System.Windows.Controls.ValidationRule> zdefiniowane <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> <xref:System.Windows.Controls.ValidationStep.RawProposedValue> dla tego elementu <xref:System.Windows.Data.Binding> , w takim przypadku wywołuje <xref:System.Windows.Controls.ValidationRule.Validate%2A> metodę na każdym <xref:System.Windows.Controls.ValidationRule> z nich do momentu, gdy jeden z nich zostanie uruchomiony w wystąpieniu błędu lub do momentu, aż wszystkie z nich zakończą się powodzeniem.

2. Aparat powiązań następnie wywołuje konwerter, jeśli taki istnieje.

3. Jeśli konwerter zakończy się pomyślnie, aparat powiązań sprawdza, czy istnieją jakieś <xref:System.Windows.Controls.ValidationRule> obiekty niestandardowe zdefiniowane dla <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> <xref:System.Windows.Controls.ValidationStep.ConvertedProposedValue> tego elementu <xref:System.Windows.Data.Binding> , w takim przypadku wywołuje metodę dla <xref:System.Windows.Controls.ValidationRule.Validate%2A> każdej <xref:System.Windows.Controls.ValidationRule> z nich, która została <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> ustawiona na wartość do <xref:System.Windows.Controls.ValidationStep.ConvertedProposedValue> momentu, gdy jeden z nich zostanie uruchomiony w wystąpieniu błędu lub do momentu, aż wszystkie z nich zakończą się powodzeniem.

4. Aparat powiązań ustawia właściwość source.

5. Aparat powiązań sprawdza, czy istnieją jakieś obiekty niestandardowe <xref:System.Windows.Controls.ValidationRule> zdefiniowane dla <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> <xref:System.Windows.Controls.ValidationStep.UpdatedValue> tego elementu <xref:System.Windows.Data.Binding> , w takim przypadku wywołuje metodę dla każdej z nich, <xref:System.Windows.Controls.ValidationRule.Validate%2A> <xref:System.Windows.Controls.ValidationRule> która ma <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> ustawioną wartość, <xref:System.Windows.Controls.ValidationStep.UpdatedValue> dopóki jedna z nich nie zostanie uruchomiona w wystąpieniu błędu lub do momentu, aż wszystkie z nich zakończą się powodzeniem. Jeśli obiekt <xref:System.Windows.Controls.DataErrorValidationRule> jest skojarzony z powiązaniem i <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> ma ustawioną wartość domyślną, <xref:System.Windows.Controls.ValidationStep.UpdatedValue> program <xref:System.Windows.Controls.DataErrorValidationRule> jest sprawdzany w tym punkcie. W tym momencie każde powiązanie z <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> ustawionym ustawieniem `true` jest zaznaczone.

6. Aparat powiązań sprawdza, czy istnieją jakieś obiekty niestandardowe <xref:System.Windows.Controls.ValidationRule> zdefiniowane dla <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> <xref:System.Windows.Controls.ValidationStep.CommittedValue> tego elementu <xref:System.Windows.Data.Binding> , w takim przypadku wywołuje metodę dla każdej z nich, <xref:System.Windows.Controls.ValidationRule.Validate%2A> <xref:System.Windows.Controls.ValidationRule> która ma <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> ustawioną wartość, <xref:System.Windows.Controls.ValidationStep.CommittedValue> dopóki jedna z nich nie zostanie uruchomiona w wystąpieniu błędu lub do momentu, aż wszystkie z nich zakończą się powodzeniem.

Jeśli w <xref:System.Windows.Controls.ValidationRule> dowolnym momencie w trakcie tego procesu nie zostanie przekazany, aparat powiązań tworzy <xref:System.Windows.Controls.ValidationError> obiekt i dodaje go do <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> kolekcji powiązanego elementu. Przed uruchomieniem przez aparat powiązań <xref:System.Windows.Controls.ValidationRule> obiektów w którymkolwiek z powyższych kroków usuwa on wszystkie <xref:System.Windows.Controls.ValidationError> elementy, które zostały dodane do <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> dołączonej właściwości elementu powiązanego w tym kroku. Na przykład jeśli dla <xref:System.Windows.Controls.ValidationRule> którego <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> jest ustawiona wartość <xref:System.Windows.Controls.ValidationStep.UpdatedValue> Niepowodzenie, podczas następnego procesu walidacji aparat powiązań usunie ten <xref:System.Windows.Controls.ValidationError> element bezpośrednio przed wywołaniem, <xref:System.Windows.Controls.ValidationRule> który ma <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> ustawioną wartość <xref:System.Windows.Controls.ValidationStep.UpdatedValue> .

Gdy <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> nie jest pusty, <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> dołączona właściwość elementu jest ustawiona na `true` . Ponadto, jeśli <xref:System.Windows.Data.Binding.NotifyOnValidationError%2A> Właściwość <xref:System.Windows.Data.Binding> jest ustawiona na `true` , aparat powiązań wywołuje <xref:System.Windows.Controls.Validation.Error?displayProperty=nameWithType> dołączone zdarzenie w elemencie.

Należy również zauważyć, że prawidłowy transfer wartości w obu kierunkach (element docelowy ze źródłem lub źródłem do lokalizacji docelowej) czyści <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> załączoną właściwość.

Jeśli powiązanie jest <xref:System.Windows.Controls.ExceptionValidationRule> skojarzone z nim lub miało <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> ustawioną właściwość, `true` a wyjątek jest zgłaszany, gdy aparat powiązań ustawia źródło, aparat powiązań sprawdzi, czy istnieje <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A> . Możesz użyć <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A> wywołania zwrotnego, aby zapewnić niestandardową procedurę obsługi wyjątków. Jeśli element <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A> nie jest określony w <xref:System.Windows.Data.Binding> , aparat powiązań tworzy <xref:System.Windows.Controls.ValidationError> wyjątek z wyjątkiem i dodaje go do <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> kolekcji powiązanego elementu.

## <a name="debugging-mechanism"></a>Mechanizm debugowania

Można ustawić przyłączoną Właściwość <xref:System.Diagnostics.PresentationTraceSources.TraceLevel%2A?displayProperty=nameWithType> obiektu powiązanego z powiązaniem, aby otrzymywać informacje o stanie określonego powiązania.

## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Controls.DataErrorValidationRule>
- [Powiąż z wynikami zapytania LINQ](../../framework/wpf/data/how-to-bind-to-the-results-of-a-linq-query.md)
- [Powiązanie danych](../../framework/wpf/advanced/optimizing-performance-data-binding.md)
- [Pokaz powiązania danych][data-binding-demo]
- [Artykuły z poradami](../../framework/wpf/data/data-binding-how-to-topics.md)
- [Wiązanie ze źródłem danych ADO.NET](../../framework/wpf/data/how-to-bind-to-an-ado-net-data-source.md)

[data-binding-demo]: https://github.com/microsoft/WPF-Samples/tree/master/Sample%20Applications/DataBindingDemo "Aplikacja demonstracyjna powiązania danych"
