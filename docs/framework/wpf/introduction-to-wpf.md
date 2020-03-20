---
title: Wprowadzenie do WPF
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b8d7cf43-d1f2-4f3d-adb0-4f3a6428edc0
dev_langs:
- csharp
- vb
ms.openlocfilehash: 511ea04a522804b4b2ea2ff173d6cdd738e5c7bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186218"
---
# <a name="wpf-overview"></a>Omówienie podsystemu WPF

Program Windows Presentation Foundation (WPF) umożliwia tworzenie aplikacji klienckich dla systemu Windows z oszałamiającymi wizualnie środowiskami użytkownika.

![Przykład interfejsu użytkownika usługi Contoso Healthcare](media/introduction-to-wpf/wpfintrofigure24.png)

Rdzeń WPF jest niezależny od rozdzielczości i wektorowy aparat renderowania, który jest zbudowany w celu skorzystania z nowoczesnego sprzętu graficznego. WPF WPF rozszerza rdzeń o kompleksowy zestaw funkcji tworzenia aplikacji, które obejmują rozszerzalny język znaczników aplikacji (XAML), formanty, powiązanie danych, układ, grafikę 2D i 3D, animację, style, szablony, dokumenty, media, tekst i Typografia. WPF WPF jest częścią platformy .NET, dzięki czemu można tworzyć aplikacje, które zawierają inne elementy interfejsu API platformy .NET.

Ten przegląd jest przeznaczony dla początkujących i obejmuje kluczowe możliwości i pojęcia WPF.

## <a name="program-with-wpf"></a>Program z WPF

WPF WPF istnieje jako podzbiór typów .NET, które <xref:System.Windows> są (w przeważającej części) znajduje się w obszarze nazw. Jeśli wcześniej utworzyłeś aplikacje z platformy .NET przy użyciu zarządzanych technologii, takich jak ASP.NET i Windows Forms, podstawowe środowisko programowania WPF powinno być znane; tworzenie wystąpienia klas, ustawianie właściwości, metody wywołania i obsługi zdarzeń przy użyciu ulubionego języka programowania .NET, takiego jak C# lub Visual Basic.

WPF WPF zawiera dodatkowe konstrukcje programowania, które zwiększają właściwości i zdarzenia: [właściwości zależności](advanced/dependency-properties-overview.md) i [kierowane zdarzenia.](advanced/routed-events-overview.md)

## <a name="markup-and-code-behind"></a>Znaczniki i kod

WPF WPF umożliwia tworzenie aplikacji przy użyciu *znaczników* i *związane z kodem*, doświadczenie, z którym ASP.NET deweloperzy powinni być zaznajomieni. Zazwyczaj używasz znaczników XAML do implementowania wyglądu aplikacji podczas korzystania z zarządzanych języków programowania (związanych z kodem) w celu zaimplementowania jej zachowania. To oddzielenie wyglądu i zachowania ma następujące zalety:

- Koszty rozwoju i konserwacji są zmniejszone, ponieważ znaczniki specyficzne dla wyglądu nie są ściśle powiązane z kodem specyficznym dla zachowania.

- Programowanie jest bardziej wydajne, ponieważ projektanci mogą implementować wygląd aplikacji jednocześnie z deweloperami, którzy implementują zachowanie aplikacji.

- [Globalizacja i lokalizacja](advanced/wpf-globalization-and-localization-overview.md) dla aplikacji WPF jest uproszczona.

### <a name="markup"></a>Znaczniki

XAML to język znaczników oparty na języku XML, który implementuje wygląd aplikacji deklaratywnie. Zazwyczaj służy do tworzenia okien, okien dialogowych, stron i formantów użytkownika oraz do wypełniania ich formantami, kształtami i grafiką.

W poniższym przykładzie użyto xaml do zaimplementowania wygląd okna, które zawiera jeden przycisk:

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    Title="Window with Button"
    Width="250" Height="100">

  <!-- Add button to window -->
  <Button Name="button">Click Me!</Button>

</Window>
```

W szczególności ten kod XAML definiuje okno i `Window` `Button` przycisk przy użyciu i elementów, odpowiednio. Każdy element jest skonfigurowany z `Window` atrybutami, `Title` takimi jak atrybut elementu, aby określić tekst paska tytułu okna. W czasie wykonywania WPF WPF konwertuje elementy i atrybuty, które są zdefiniowane w znacznikach do wystąpień klas WPF. Na przykład `Window` element jest konwertowany <xref:System.Windows.Window> na <xref:System.Windows.Window.Title%2A> wystąpienie klasy, `Title` której właściwość jest wartością atrybutu.

Na poniższym rysunku przedstawiono interfejs użytkownika (UI), który jest zdefiniowany przez kod XAML w poprzednim przykładzie:

![Okno zawierające przycisk](media/introduction-to-wpf/wpfintrofigure10.png)

Ponieważ kod XAML jest oparty na języku XML, interfejs użytkownika, który jest z nim redagowany, jest zestawiony w hierarchii zagnieżdżonych elementów zwanych [drzewem elementów.](advanced/trees-in-wpf.md) Drzewo elementów zapewnia logiczny i intuicyjny sposób tworzenia interfejsów użytkownika i zarządzania nimi.

### <a name="code-behind"></a>Zakodowane

Głównym zachowaniem aplikacji jest zaimplementowanie funkcji, która odpowiada na interakcje użytkownika, w tym obsługi zdarzeń (na przykład kliknięcie menu, pasek narzędzi lub przycisk) i wywołanie logiki biznesowej i logiki dostępu do danych w odpowiedzi. W WPF WPF to zachowanie jest implementowane w kodzie, który jest skojarzony z znaczników. Ten typ kodu jest znany jako związany z kodem. Poniższy przykład pokazuje zaktualizowane znaczniki z poprzedniego przykładu i związany z kodem:

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.AWindow"
    Title="Window with Button"
    Width="250" Height="100">

  <!-- Add button to window -->
  <Button Name="button" Click="button_Click">Click Me!</Button>

</Window>
```

```csharp
using System.Windows; // Window, RoutedEventArgs, MessageBox

namespace SDKSample
{
    public partial class AWindow : Window
    {
        public AWindow()
        {
            // InitializeComponent call is required to merge the UI
            // that is defined in markup with this class, including  
            // setting properties and registering event handlers
            InitializeComponent();
        }

        void button_Click(object sender, RoutedEventArgs e)
        {
            // Show message box when button is clicked.
            MessageBox.Show("Hello, Windows Presentation Foundation!");
        }
    }
}
```

```vb
Namespace SDKSample

    Partial Public Class AWindow
        Inherits System.Windows.Window

        Public Sub New()

            ' InitializeComponent call is required to merge the UI
            ' that is defined in markup with this class, including  
            ' setting properties and registering event handlers
            InitializeComponent()

        End Sub

        Private Sub button_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)

            ' Show message box when button is clicked.
            MessageBox.Show("Hello, Windows Presentation Foundation!")

        End Sub

    End Class

End Namespace
```

W tym przykładzie związany z kodem implementuje <xref:System.Windows.Window> klasę, która pochodzi z klasy. Atrybut `x:Class` jest używany do skojarzenia znaczników z klasą zakodującą kod. `InitializeComponent`jest wywoływana z konstruktora klasy związanej z kodem, aby scalić interfejs użytkownika, który jest zdefiniowany w znacznikach z klasą zakodową. (`InitializeComponent` jest generowany dla Ciebie, gdy aplikacja jest zbudowana, dlatego nie trzeba go zaimplementować ręcznie.) Połączenie `x:Class` i `InitializeComponent` upewnij się, że implementacja jest poprawnie inicjowane, gdy jest tworzony. Klasa bez kodu implementuje również program obsługi zdarzeń <xref:System.Windows.Controls.Primitives.ButtonBase.Click> dla zdarzenia przycisku. Po kliknięciu przycisku program obsługi zdarzeń wyświetla okno <xref:System.Windows.MessageBox.Show%2A?displayProperty=fullName> komunikatu, wywołując metodę.

Na poniższej ilustracji przedstawiono wynik po kliknięciu przycisku:

![Skrzynka z wiadomościami](media/introduction-to-wpf/wpfintrofigure25.png)

## <a name="controls"></a>Kontrolki

Środowiska użytkownika, które są dostarczane przez model aplikacji są skonstruowane formanty. W WPF WPF *formantu* jest terminem parasola, który ma zastosowanie do kategorii klas WPF, które są hostowane w oknie lub na stronie, mają interfejs użytkownika i implementują pewne zachowanie.

Aby uzyskać więcej informacji, zobacz [Formanty](controls/index.md).

### <a name="wpf-controls-by-function"></a>WPF kontroluje według funkcji

Wbudowane formanty WPF są wymienione w tym miejscu:

- **Przyciski** <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Primitives.RepeatButton>: i .

- **Wyświetlanie**danych <xref:System.Windows.Controls.DataGrid> <xref:System.Windows.Controls.ListView>: <xref:System.Windows.Controls.TreeView>, , i .

- **Data wyświetlania i zaznaczania**: <xref:System.Windows.Controls.Calendar> i <xref:System.Windows.Controls.DatePicker>.

- **Okna dialogowe**: <xref:Microsoft.Win32.OpenFileDialog>, <xref:System.Windows.Controls.PrintDialog>i <xref:Microsoft.Win32.SaveFileDialog>.

- **Atrament cyfrowy** <xref:System.Windows.Controls.InkCanvas> : <xref:System.Windows.Controls.InkPresenter>i .

- **Dokumenty** <xref:System.Windows.Controls.DocumentViewer>: <xref:System.Windows.Controls.FlowDocumentPageViewer> <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentScrollViewer>, <xref:System.Windows.Controls.StickyNoteControl>, , i .

- **Wejście** <xref:System.Windows.Controls.TextBox>: <xref:System.Windows.Controls.RichTextBox>, <xref:System.Windows.Controls.PasswordBox>i .

- **Układ** <xref:System.Windows.Controls.Border>: <xref:System.Windows.Controls.Primitives.BulletDecorator> <xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Controls.Expander>, <xref:System.Windows.Controls.Grid> <xref:System.Windows.Controls.GridView>, <xref:System.Windows.Controls.GridSplitter> <xref:System.Windows.Controls.GroupBox>, <xref:System.Windows.Controls.Panel> <xref:System.Windows.Controls.Primitives.ResizeGrip>, <xref:System.Windows.Controls.Separator> <xref:System.Windows.Controls.Primitives.ScrollBar>, <xref:System.Windows.Controls.ScrollViewer> <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.Primitives.Thumb> <xref:System.Windows.Controls.Viewbox>, <xref:System.Windows.Controls.VirtualizingStackPanel> <xref:System.Windows.Window>, <xref:System.Windows.Controls.WrapPanel>, , , , , , , , , , , i .

- **Media** <xref:System.Windows.Controls.Image>: <xref:System.Windows.Controls.MediaElement>, <xref:System.Windows.Controls.SoundPlayerAction>i .

- **Menu**: <xref:System.Windows.Controls.ContextMenu> <xref:System.Windows.Controls.Menu>, <xref:System.Windows.Controls.ToolBar>i .

- **Nawigacja** <xref:System.Windows.Controls.Frame> <xref:System.Windows.Documents.Hyperlink>: <xref:System.Windows.Controls.Page> <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.TabControl>, , i .

- **Wybór** <xref:System.Windows.Controls.CheckBox>: <xref:System.Windows.Controls.ComboBox> <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.RadioButton>, <xref:System.Windows.Controls.Slider>, , i .

- **Informacje o użytkowniku** <xref:System.Windows.Controls.AccessText>: <xref:System.Windows.Controls.TextBlock>, <xref:System.Windows.Controls.ToolTip> <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.ProgressBar>, <xref:System.Windows.Controls.Primitives.StatusBar>, , , i .

## <a name="input-and-commands"></a>Dane wejściowe i polecenia

Formanty najczęściej wykrywają i reagują na dane wejściowe użytkownika. [System wejściowy WPF](advanced/input-overview.md) używa zdarzeń bezpośrednich i kierowanych do obsługi wprowadzania tekstu, zarządzania fokusem i pozycjonowania myszy.

Aplikacje często mają złożone wymagania wejściowe. WPF WPF udostępnia [system poleceń,](advanced/commanding-overview.md) który oddziela akcje wprowadzania danych użytkownika z kodu, który odpowiada na te akcje.

## <a name="layout"></a>Układ

Podczas tworzenia interfejsu użytkownika można rozmieścić formanty według lokalizacji i rozmiaru, aby utworzyć układ. Kluczowym wymaganiem każdego układu jest dostosowanie się do zmian w rozmiarze okna i ustawieniach wyświetlania. Zamiast zmuszać do pisania kodu, aby dostosować układ w tych okolicznościach, WPF WPF zapewnia pierwszej klasy, rozszerzalny system układu dla Ciebie.

Kamieniem węgielnym układu jest względne pozycjonowanie, co zwiększa możliwość dostosowania się do zmieniających się warunków okiennych i wyświetlania. Ponadto system układu zarządza negocjacji między formantami w celu określenia układu. Negocjacja jest procesem dwuetapowym: po pierwsze, formant informuje rodzica, jakiej lokalizacji i rozmiaru wymaga; po drugie, rodzic informuje formant, jaką przestrzeń może mieć.

System układu jest narażony na formanty podrzędne za pośrednictwem podstawowych klas WPF. W przypadku typowych układów, takich jak siatki, układanie i dokowanie, WPF zawiera kilka formantów układu:

- <xref:System.Windows.Controls.Canvas>: Formanty podrzędne zapewniają własny układ.

- <xref:System.Windows.Controls.DockPanel>: Elementy sterujące podrzędne są wyrównane do krawędzi panelu.

- <xref:System.Windows.Controls.Grid>: Formanty podrzędne są umieszczane według wierszy i kolumn.

- <xref:System.Windows.Controls.StackPanel>: Formanty podrzędne są ułożone pionowo lub poziomo.

- <xref:System.Windows.Controls.VirtualizingStackPanel>: Formanty podrzędne są zwirtualizowane i rozmieszczone w jednej linii, która jest zorientowana poziomo lub pionowo.

- <xref:System.Windows.Controls.WrapPanel>: Formanty podrzędne są umieszczane w kolejności od lewej do prawej i zawijane do następnego wiersza, gdy w bieżącym wierszu jest więcej formantów niż pozwala na to miejsce.

W poniższym przykładzie użyto a <xref:System.Windows.Controls.DockPanel> do rozłąki kilku <xref:System.Windows.Controls.TextBox> formantów:

[!code-xaml[IntroToWPFSnippets#LayoutMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_1.xaml)]

Umożliwia <xref:System.Windows.Controls.DockPanel> formanty podrzędne, <xref:System.Windows.Controls.TextBox> aby powiedzieć, jak je rozmieścić. Aby to zrobić, <xref:System.Windows.Controls.DockPanel> implementuje `Dock` dołączone właściwości, która jest narażona na formanty podrzędne, aby umożliwić każdemu z nich określić styl dokowania.

> [!NOTE]
> Właściwość, która jest implementowana przez formant nadrzędny do użytku przez formanty podrzędne jest WPF konstrukcji o nazwie [dołączonej właściwości.](advanced/attached-properties-overview.md)

Na poniższym rysunku przedstawiono wynik znaczników XAML w poprzednim przykładzie:

![Strona DockPanel](media/introduction-to-wpf/wpfintrofigure11.png)

## <a name="data-binding"></a>Powiązanie danych

Większość aplikacji jest tworzona w celu zapewnienia użytkownikom środków do wyświetlania i edytowania danych. W przypadku aplikacji WPF praca przechowywania i uzyskiwania dostępu do danych jest już przewidziana przez technologie, takie jak SQL Server i ADO .NET. Po dostęp do danych i załadowany do obiektów zarządzanych aplikacji rozpoczyna się ciężka praca dla aplikacji WPF. Zasadniczo wiąże się to z dwiema rzeczami:

1. Kopiowanie danych z obiektów zarządzanych do formantów, w których dane mogą być wyświetlane i edytowane.

2. Upewniając się, że zmiany wprowadzone do danych przy użyciu formantów są kopiowane z powrotem do obiektów zarządzanych.

Aby uprościć tworzenie aplikacji, WPF WPF udostępnia aparat wiązania danych, aby automatycznie wykonać te kroki. Podstawową jednostką aparatu wiązania <xref:System.Windows.Data.Binding> danych jest klasa, której zadaniem jest powiązanie formantu (docelowego powiązania) z obiektem danych (źródłem powiązania). Związek ten ilustruje poniższy rysunek:

![Diagram wiązania danych podstawowych](media/introduction-to-wpf/databindingmostbasic.png)

W następnym przykładzie pokazano, <xref:System.Windows.Controls.TextBox> jak powiązać `Person` z wystąpieniem obiektu niestandardowego. Implementacja `Person` jest pokazana w następującym kodzie:

[!code-vb[SimpleDataBindingSnippets#PersonClassCODE](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_2.vb)]
[!code-csharp[SimpleDataBindingSnippets#PersonClassCODE](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_2.cs)]

Następujące znaczniki wiąże <xref:System.Windows.Controls.TextBox> się z wystąpieniem `Person` obiektu niestandardowego:

```xaml
 <Window
     xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
     xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
     x:Class="SDKSample.DataBindingWindow">

   <!-- Bind the TextBox to the data source (TextBox.Text to Person.Name) -->
   <TextBox Name="personNameTextBox" Text="{Binding Path=Name}" />

 </Window>
```

[!code-vb[SimpleDataBindingSnippets#DataBindingCODEBEHIND](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_6.vb)]
[!code-csharp[SimpleDataBindingSnippets#DataBindingCODEBEHIND](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_6.cs)]

W tym przykładzie `Person` klasa jest tworzone w kodzie i jest ustawiona jako kontekst danych dla . `DataBindingWindow` <xref:System.Windows.Controls.TextBox.Text%2A> W znacznikach właściwość <xref:System.Windows.Controls.TextBox> jest powiązana `Person.Name` z właściwością`{Binding ... }`(przy użyciu " " składni XAML). Ten XAML mówi WPF <xref:System.Windows.Controls.TextBox> do `Person` powiązania formantu <xref:System.Windows.FrameworkElement.DataContext%2A> do obiektu, który jest przechowywany we właściwości okna.

Aparat wiązania danych WPF zapewnia dodatkową obsługę, która obejmuje sprawdzanie poprawności, sortowanie, filtrowanie i grupowanie. Ponadto powiązanie danych obsługuje użycie szablonów danych do tworzenia niestandardowego interfejsu użytkownika dla danych powiązanych, gdy interfejs użytkownika wyświetlany przez standardowe formanty WPF nie jest odpowiedni.

Aby uzyskać więcej informacji, zobacz [Omówienie powiązania danych](../../desktop-wpf/data/data-binding-overview.md).

## <a name="graphics"></a>Grafika

WPF WPF wprowadza obszerny, skalowalny i elastyczny zestaw funkcji graficznych, które mają następujące zalety:

- **Grafika niezależna od rozdzielczości i niezależna od urządzenia**. Podstawową jednostką miary w systemie graficznym WPF jest piksel niezależny od urządzenia, który jest 1/96 cala, niezależnie od rzeczywistej rozdzielczości ekranu i stanowi podstawę do renderowania niezależnego od rozdzielczości i niezależnego od urządzenia. Każdy piksel niezależny od urządzenia jest automatycznie skalowany w celu dopasowania ustawienia punktów na cal (dpi) systemu, na który renderuje.

- **Poprawiono precyzję**. Układ współrzędnych WPF jest mierzony za pomocą liczb zmiennoprzecinkowych o podwójnej precyzji, a nie z pojedynczą precyzją. Przekształcenia i wartości krycia są również wyrażone jako podwójna precyzja. WPF WPF obsługuje również szeroką gamę kolorów (scRGB) i zapewnia zintegrowaną obsługę zarządzania wejściami z różnych przestrzeni kolorów.

- **Zaawansowana obsługa grafiki i animacji**. WPF WPF upraszcza programowanie grafiki, zarządzając scenami animacji; nie ma potrzeby martwić się o przetwarzanie sceny, renderowanie pętli i interpolacji dwuliniowej. Ponadto WPF WPF zapewnia obsługę testowania trafień i pełną obsługę kompozycji alfa.

- **Akceleracja sprzętowa**. System graficzny WPF wykorzystuje sprzęt graficzny, aby zminimalizować użycie procesora.

### <a name="2d-shapes"></a>Kształty 2D

WPF WPF udostępnia bibliotekę typowych kształtów 2D rysowane wektorami, takich jak prostokąty i elipsy, które są wyświetlane na poniższej ilustracji:

![Elipsy i prostokąty](media/introduction-to-wpf/wpfintrofigure4.PNG)

Ciekawą możliwością kształtów jest to, że nie są one przeznaczone tylko do wyświetlania; kształty implementują wiele funkcji, których oczekujesz od formantów, w tym klawiatury i myszy. Poniższy przykład <xref:System.Windows.UIElement.MouseUp> przedstawia zdarzenie <xref:System.Windows.Shapes.Ellipse> obsługiwanej:

[!code-xaml[IntroToWPFSnippets#HandleEllipseMouseUpEventMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_7.xaml)]

[!code-vb[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_8.vb)]
[!code-csharp[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_8.cs)]

Na poniższej ilustracji przedstawiono, co jest produkowane przez poprzedni kod:

![Okno z tekstem "kliknąłeś&#33; elipsy"](media/introduction-to-wpf/wpfintrofigure12.png)

Aby uzyskać więcej informacji, zobacz [Kształty i rysunek podstawowy w przeglądzie WPF](../../desktop-wpf/data/data-binding-overview.md).

### <a name="2d-geometries"></a>Geometrie 2D

Kształty 2D dostarczane przez WPF obejmują standardowy zestaw podstawowych kształtów. Jednak może być konieczne utworzenie kształtów niestandardowych, aby ułatwić projektowanie dostosowanego interfejsu użytkownika. W tym celu WPF WPF zapewnia geometrie. Na poniższym rysunku przedstawiono użycie geometrii do utworzenia niestandardowego kształtu, który może być rysowany bezpośrednio, używany jako pędzel lub używany do przycinania innych kształtów i formantów.

<xref:System.Windows.Shapes.Path>obiekty mogą być używane do rysowania zamkniętych lub otwartych kształtów, wielu kształtów, a nawet zakrzywionych kształtów.

<xref:System.Windows.Media.Geometry>obiekty mogą być używane do przycinania, testowania trafień i renderowania danych graficznych 2D.

![Różne zastosowania ścieżki](media/introduction-to-wpf/wpfintrofigure5.png)

Aby uzyskać więcej informacji, zobacz [Omówienie geometrii](graphics-multimedia/geometry-overview.md).

### <a name="2d-effects"></a>Efekty 2D

Podzbiór funkcji WPF 2D zawiera efekty wizualne, takie jak gradienty, mapy bitowe, rysunki, malowanie klipami wideo, obrót, skalowanie i pochylanie. Wszystkie te są osiągane za pomocą pędzli; na poniższym rysunku przedstawiono kilka przykładów:

![Ilustracja różnych pędzli](media/introduction-to-wpf/wpfintrofigure6.png)

Aby uzyskać więcej informacji, zobacz [omówienie pędzli WPF](graphics-multimedia/wpf-brushes-overview.md).

### <a name="3d-rendering"></a>Renderowanie 3D

WPF WPF zawiera również funkcje renderowania 3D, które integrują się z grafiką 2-w, aby umożliwić tworzenie bardziej ekscytujących i interesujących interfejsów użytkownika. Na przykład na poniższej ilustracji przedstawiono obrazy 2D renderowane na kształtach 3D:

![Zrzut ekranu przykładowy Visual3D](media/introduction-to-wpf/wpfintrofigure13.png)

Aby uzyskać więcej informacji, zobacz [omówienie grafiki 3D](graphics-multimedia/3-d-graphics-overview.md).

## <a name="animation"></a>Animacja

Obsługa animacji WPF umożliwia tworzenie formantów, powiększanie, obracanie i zanikanie, tworzenie interesujących przejść stron i nie tylko. Można animować większość klas WPF, nawet klas niestandardowych. Na poniższej ilustracji przedstawiono prostą animację w akcji:

![Obrazy animowanego sześcianu](media/introduction-to-wpf/wpfintrofigure7.png)

Aby uzyskać więcej informacji, zobacz [Omówienie animacji](graphics-multimedia/animation-overview.md).

## <a name="media"></a>Multimedia

Jednym ze sposobów przekazywania bogatych treści jest wykorzystanie mediów audiowizualnych. WPF WPF zapewnia specjalną obsługę obrazów, wideo i audio.

### <a name="images"></a>Obrazy

Obrazy są wspólne dla większości aplikacji i WPF WPF udostępnia kilka sposobów ich używania. Na poniższej ilustracji przedstawiono interfejs użytkownika z polem listy zawierającym miniatury obrazów. Po wybraniu miniatury obraz jest wyświetlany w pełnym rozmiarze.

![Miniatury obrazów i obrazu o pełnym rozmiarze&#45;](media/introduction-to-wpf/wpfintrofigure8.png)

Aby uzyskać więcej informacji, zobacz [Omówienie obrazowania](graphics-multimedia/imaging-overview.md).

### <a name="video-and-audio"></a>Wideo i audio

Sterowanie <xref:System.Windows.Controls.MediaElement> jest w stanie odtwarzać zarówno wideo, jak i audio i jest wystarczająco elastyczne, aby stanowić podstawę niestandardowego odtwarzacza multimedialnego. Następujące znaczniki XAML implementują odtwarzacz multimedialny:

[!code-xaml[IntroToWPFSnippets#MediaElementMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_9.xaml)]

Okno na poniższej ilustracji pokazuje formant <xref:System.Windows.Controls.MediaElement> w akcji:

![Sterowanie MediaElement z dźwiękiem i wideo](media/introduction-to-wpf/wpfintrofigure1.png)

Aby uzyskać więcej informacji, zobacz [Grafika i multimedia](graphics-multimedia/index.md).

## <a name="text-and-typography"></a>Tekst i typografia

Aby ułatwić renderowanie tekstu wysokiej jakości, WPF WPF oferuje następujące funkcje:

- Obsługa czcionek OpenType.

- Ulepszenia ClearType.

- Wysoka wydajność, która wykorzystuje akcelerację sprzętową.

- Integracja tekstu z multimediami, grafiką i animacją.

- Międzynarodowa obsługa czcionek i mechanizmy rezerwowe.

Jako demonstracja integracji tekstu z grafiką, na poniższej ilustracji przedstawiono zastosowanie dekoracji tekstowych:

![Tekst z różnymi dekoracjami tekstowymi](media/introduction-to-wpf/wpfintrofigure23.png)

Aby uzyskać więcej informacji, zobacz [Typografia w programie Windows Presentation Foundation](advanced/typography-in-wpf.md).

## <a name="customize-wpf-apps"></a>Dostosowywanie aplikacji WPF

Do tego momentu widzieliśmy podstawowe bloki konstrukcyjne WPF do tworzenia aplikacji. Model aplikacji służy do hostowania i dostarczania zawartości aplikacji, która składa się głównie z formantów. Aby uprościć rozmieszczenie formantów w interfejsie użytkownika i upewnić się, że układ jest utrzymywany w obliczu zmian w ustawieniach rozmiaru okna i wyświetlania, należy użyć systemu układu WPF. Ponieważ większość aplikacji umożliwiają użytkownikom interakcję z danymi, można użyć powiązania danych, aby zmniejszyć pracę integracji interfejsu użytkownika z danymi. Aby poprawić wygląd aplikacji, należy użyć kompleksowego zakresu grafiki, animacji i obsługi multimediów zapewnianych przez WPF.

Często jednak podstawy nie wystarczą do tworzenia i zarządzania naprawdę odrębnym i oszałamiającym wizualnie doświadczeniem użytkownika. Standardowe formanty WPF może nie zintegrować z żądanym wyglądem aplikacji. Dane mogą nie być wyświetlane w najbardziej efektywny sposób. Ogólne środowisko użytkownika aplikacji może nie być dostosowane do domyślnego wyglądu i działanie motywów systemu Windows. Pod wieloma względami technologia prezentacji wymaga rozszerzalności wizualnej tak samo, jak każdy inny rodzaj rozszerzalności.

Z tego powodu WPF WPF udostępnia wiele mechanizmów do tworzenia unikatowych środowisk użytkownika, w tym model zawartości bogatej dla formantów, wyzwalaczy, szablonów kontroli i danych, style, zasoby interfejsu użytkownika i motywy i karnacje.

### <a name="content-model"></a>Model zawartości

Głównym celem większości formantów WPF jest wyświetlanie zawartości. W WPF WPF, typ i liczba elementów, które mogą stanowić zawartość formantu jest określany jako *model zawartości*formantu . Niektóre formanty mogą zawierać pojedynczy element i typ zawartości; na przykład zawartość jest <xref:System.Windows.Controls.TextBox> wartość ciągu, który jest <xref:System.Windows.Controls.TextBox.Text%2A> przypisany do właściwości. Poniższy przykład określa zawartość <xref:System.Windows.Controls.TextBox>:

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.TextBoxContentWindow"
    Title="TextBox Content">

    <TextBox Text="This is the content of a TextBox." />
</Window>
```

Na poniższej ilustracji przedstawiono wynik:

![Formant pola tekstowego zawierający tekst](media/introduction-to-wpf/wpfintrofigure21.png)

Inne formanty mogą jednak zawierać wiele elementów o różnych typach zawartości; zawartość , <xref:System.Windows.Controls.Button>określona przez <xref:System.Windows.Controls.ContentControl.Content%2A> właściwość, może zawierać wiele elementów, w tym formantów układu, tekst, obrazy i kształty. Poniższy przykład <xref:System.Windows.Controls.Button> przedstawia zawartość z <xref:System.Windows.Controls.DockPanel>zawartością, <xref:System.Windows.Controls.Border>która <xref:System.Windows.Controls.MediaElement>zawiera , a <xref:System.Windows.Controls.Label>, a i :

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.ButtonContentWindow"
    Title="Button Content">

  <Button Margin="20">
    <!-- Button Content -->
    <DockPanel Width="200" Height="180">
      <Label DockPanel.Dock="Top" HorizontalAlignment="Center">Click Me!</Label>
      <Border Background="Black" BorderBrush="Yellow" BorderThickness="2"
        CornerRadius="2" Margin="5">
        <MediaElement Source="media/wpf.wmv" Stretch="Fill" />
      </Border>
    </DockPanel>
  </Button>
</Window>
```

Na poniższej ilustracji przedstawiono zawartość tego przycisku:

![Przycisk zawierający wiele typów zawartości](media/introduction-to-wpf/wpfintrofigure22.png)

Aby uzyskać więcej informacji na temat rodzajów zawartości, która jest obsługiwana przez różne formanty, zobacz [Model zawartości WPF](controls/wpf-content-model.md).

### <a name="triggers"></a>Wyzwalacze

Chociaż głównym celem znaczników XAML jest zaimplementowanie wyglądu aplikacji, można również użyć XAML do zaimplementowania niektórych aspektów zachowania aplikacji. Jednym z przykładów jest użycie wyzwalaczy, aby zmienić wygląd aplikacji na podstawie interakcji użytkownika. Aby uzyskać więcej informacji, zobacz [Style i szablony](../../desktop-wpf/fundamentals/styles-templates-overview.md).

### <a name="control-templates"></a>Szablony formantów

Domyślne interfejsy użytkownika dla formantów WPF są zazwyczaj konstruowane z innych formantów i kształtów. Na przykład <xref:System.Windows.Controls.Button> a składa <xref:Microsoft.Windows.Themes.ButtonChrome> się <xref:System.Windows.Controls.ContentPresenter> z obu i formantów. Zapewnia <xref:Microsoft.Windows.Themes.ButtonChrome> standardowy wygląd przycisku, podczas gdy <xref:System.Windows.Controls.ContentPresenter> wyświetla zawartość przycisku, zgodnie z określoną <xref:System.Windows.Controls.ContentControl.Content%2A> przez właściwość.

Czasami domyślny wygląd formantu może być niezgodny z ogólnym wyglądem aplikacji. W takim przypadku można <xref:System.Windows.Controls.ControlTemplate> użyć a, aby zmienić wygląd interfejsu użytkownika formantu bez zmiany jego zawartości i zachowania.

W poniższym przykładzie pokazano, <xref:System.Windows.Controls.Button> jak zmienić wygląd a za pomocą <xref:System.Windows.Controls.ControlTemplate>:

[!code-xaml[IntroToWPFSnippets#ButtonControlTemplateWindowMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_16.xaml)]

[!code-csharp[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_17.cs)]
[!code-vb[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_17.vb)]

W tym przykładzie domyślny interfejs użytkownika <xref:System.Windows.Shapes.Ellipse> przycisku został zastąpiony, który ma <xref:System.Windows.Media.RadialGradientBrush>ciemnoniebieskie obramowanie i jest wypełniony za pomocą pliku . Formant <xref:System.Windows.Controls.ContentPresenter> wyświetla zawartość <xref:System.Windows.Controls.Button>przycisku "Kliknij mnie!" Po <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Primitives.ButtonBase.Click> kliknięciu, zdarzenie jest nadal wywoływane <xref:System.Windows.Controls.Button> jako część domyślnego zachowania formantu. Wynik jest pokazany na poniższym rysunku:

![Przycisk eliptyczny i drugie okno](media/introduction-to-wpf/wpfintrofigure2.png)

### <a name="data-templates"></a>Szablony danych

Podczas gdy szablon formantu umożliwia określenie wyglądu formantu, szablon danych umożliwia określenie wyglądu zawartości formantu. Szablony danych są często używane w celu zwiększenia sposobu wyświetlania danych powiązanych. Na poniższej ilustracji przedstawiono domyślny <xref:System.Windows.Controls.ListBox> wygląd `Task` dla kolekcji obiektów, gdzie każde zadanie ma nazwę, opis i priorytet:

![Pole listy z wyglądem domyślnym](media/introduction-to-wpf/wpfintrofigure18.png)

Domyślny wygląd jest to, <xref:System.Windows.Controls.ListBox>czego można oczekiwać od . Jednak domyślny wygląd każdego zadania zawiera tylko nazwę zadania. Aby wyświetlić nazwę zadania, opis i priorytet, <xref:System.Windows.Controls.ListBox> domyślny wygląd elementów listy związanej formantu musi zostać zmieniony za pomocą pliku <xref:System.Windows.DataTemplate>. Następujący kod XAML definiuje <xref:System.Windows.DataTemplate>takie , które jest stosowane <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> do każdego zadania przy użyciu atrybutu:

```xaml
<Window
  xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
  x:Class="SDKSample.DataTemplateWindow"
  Title="With a Data Template">
  <Window.Resources>
    <!-- Data Template (applied to each bound task item in the task collection) -->
    <DataTemplate x:Key="myTaskTemplate">
      <Border Name="border" BorderBrush="DarkSlateBlue" BorderThickness="2"
        CornerRadius="2" Padding="5" Margin="5">
        <Grid>
          <Grid.RowDefinitions>
            <RowDefinition/>
            <RowDefinition/>
            <RowDefinition/>
          </Grid.RowDefinitions>
          <Grid.ColumnDefinitions>
            <ColumnDefinition Width="Auto" />
            <ColumnDefinition />
          </Grid.ColumnDefinitions>
          <TextBlock Grid.Row="0" Grid.Column="0" Padding="0,0,5,0" Text="Task Name:"/>
          <TextBlock Grid.Row="0" Grid.Column="1" Text="{Binding Path=TaskName}"/>
          <TextBlock Grid.Row="1" Grid.Column="0" Padding="0,0,5,0" Text="Description:"/>
          <TextBlock Grid.Row="1" Grid.Column="1" Text="{Binding Path=Description}"/>
          <TextBlock Grid.Row="2" Grid.Column="0" Padding="0,0,5,0" Text="Priority:"/>
          <TextBlock Grid.Row="2" Grid.Column="1" Text="{Binding Path=Priority}"/>
        </Grid>
      </Border>
    </DataTemplate>
  </Window.Resources>

  <!-- UI -->
  <DockPanel>
    <!-- Title -->
    <Label DockPanel.Dock="Top" FontSize="18" Margin="5" Content="My Task List:"/>

    <!-- Data template is specified by the ItemTemplate attribute -->
    <ListBox
      ItemsSource="{Binding}"
      ItemTemplate="{StaticResource myTaskTemplate}"
      HorizontalContentAlignment="Stretch"
      IsSynchronizedWithCurrentItem="True"
      Margin="5,0,5,5" />

 </DockPanel>
</Window>
```

Na poniższej ilustracji przedstawiono efekt tego kodu:

![Pole listy z szablonem danych](media/introduction-to-wpf/wpfintrofigure19.png)

Należy zauważyć, że <xref:System.Windows.Controls.ListBox> zachował swoje zachowanie i ogólny wygląd; zmienił się tylko wygląd zawartości wyświetlanej w polu listy.

Aby uzyskać więcej informacji, zobacz [Omówienie tworzenia szablonów danych](data/data-templating-overview.md).

### <a name="styles"></a>Style

Style umożliwiają deweloperom i projektantom standaryzację określonego wyglądu dla ich produktu. WPF WPF zapewnia model silnego stylu, <xref:System.Windows.Style> którego podstawą jest element. Poniższy przykład tworzy styl, który ustawia <xref:System.Windows.Controls.Button> kolor tła dla każdego okna na: `Orange`

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.StyleWindow"
    Title="Styles">
  <!-- Style that will be applied to all buttons -->
  <Style TargetType="{x:Type Button}">
    <Setter Property="Background" Value="Orange" />
    <Setter Property="BorderBrush" Value="Crimson" />
    <Setter Property="FontSize" Value="20" />
    <Setter Property="FontWeight" Value="Bold" />
    <Setter Property="Margin" Value="5" />
  </Style>
  <!-- This button will have the style applied to it -->
  <Button>Click Me!</Button>

  <!-- This label will not have the style applied to it -->
  <Label>Don't Click Me!</Label>

  <!-- This button will have the style applied to it -->
  <Button>Click Me!</Button>
</Window>
```

Ponieważ ten styl <xref:System.Windows.Controls.Button> jest przeznaczony dla wszystkich formantów, styl jest automatycznie stosowany do wszystkich przycisków w oknie, jak pokazano na poniższym rysunku:

![Dwa pomarańczowe przyciski](media/introduction-to-wpf/wpfintrofigure20.png)

Aby uzyskać więcej informacji, zobacz [Style i szablony](../../desktop-wpf/fundamentals/styles-templates-overview.md).

### <a name="resources"></a>Zasoby

Formanty w aplikacji powinny mieć ten sam wygląd, który może zawierać wszystko, od czcionek i kolorów tła do sterowania szablonami, szablonami danych i stylami. Można użyć obsługi WPF dla zasobów interfejsu użytkownika do hermetyzacji tych zasobów w jednej lokalizacji do ponownego użycia.

Poniższy przykład definiuje wspólny kolor tła, <xref:System.Windows.Controls.Button> który <xref:System.Windows.Controls.Label>jest współużytkowane przez a i a:

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.ResourcesWindow"
    Title="Resources Window">

  <!-- Define window-scoped background color resource -->
  <Window.Resources>
    <SolidColorBrush x:Key="defaultBackground" Color="Red" />
  </Window.Resources>

  <!-- Button background is defined by window-scoped resource -->
  <Button Background="{StaticResource defaultBackground}">One Button</Button>

  <!-- Label background is defined by window-scoped resource -->
  <Label Background="{StaticResource defaultBackground}">One Label</Label>
</Window>
```

W tym przykładzie implementuje zasób koloru tła przy użyciu elementu `Window.Resources` właściwości. Ten zasób jest dostępny <xref:System.Windows.Window>dla wszystkich dzieni . Istnieje wiele zakresów zasobów, w tym następujące, wymienione w kolejności, w jakiej są one rozwiązywane:

1. Indywidualny formant (przy <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> użyciu właściwości dziedziczonej).

2. A <xref:System.Windows.Window> lub <xref:System.Windows.Controls.Page> a (również <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> przy użyciu właściwości dziedziczonej).

3. An <xref:System.Windows.Application> (przy <xref:System.Windows.Application.Resources%2A?displayProperty=fullName> użyciu właściwości).

Różnorodność zakresów zapewnia elastyczność w odniesieniu do sposobu definiowania i udostępniania zasobów.

Jako alternatywę dla bezpośredniego kojarzenia zasobów z określonym zakresem, można spakować <xref:System.Windows.ResourceDictionary> jeden lub więcej zasobów przy użyciu oddzielnego, do którego można się odwoływać w innych częściach aplikacji. Na przykład w poniższym przykładzie zdefiniowano domyślny kolor tła w słowniku zasobów:

```xaml
<ResourceDictionary
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">

  <!-- Define background color resource -->
  <SolidColorBrush x:Key="defaultBackground" Color="Red" />

  <!-- Define other resources -->
</ResourceDictionary>
```

Poniższy przykład odwołuje się do słownika zasobów zdefiniowanego w poprzednim przykładzie, tak aby był współużytkowany przez aplikację:

```xaml
<Application
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.App">

  <Application.Resources>
    <ResourceDictionary>
      <ResourceDictionary.MergedDictionaries>
        <ResourceDictionary Source="BackgroundColorResources.xaml"/>
      </ResourceDictionary.MergedDictionaries>
    </ResourceDictionary>
  </Application.Resources>
</Application>
```

Zasoby i słowniki zasobów są podstawą obsługi WPF dla tematów i karnacji.

Aby uzyskać więcej informacji, zobacz [Zasoby](../../desktop-wpf/fundamentals/xaml-resources-define.md).

### <a name="custom-controls"></a>Kontrolki niestandardowe

Mimo że WPF zapewnia wiele obsługi dostosowywania, mogą wystąpić sytuacje, w których istniejące formanty WPF nie spełniają potrzeb aplikacji lub jej użytkowników. Może to nastąpić, gdy:

- Interfejs użytkownika, który jest wymagany nie można utworzyć przez dostosowanie wygląd i działanie istniejących implementacji WPF.

- Zachowanie, które są wymagane nie jest obsługiwane (lub nie łatwo obsługiwane) przez istniejące implementacje WPF.

W tym momencie można jednak skorzystać z jednego z trzech modeli WPF, aby utworzyć nowy formant. Każdy model jest przeznaczony dla określonego scenariusza i wymaga formantu niestandardowego, aby pochodzić z określonej klasy podstawowej WPF. Trzy modele są wymienione tutaj:

- **Model sterowania użytkownikiem**. Formant niestandardowy <xref:System.Windows.Controls.UserControl> pochodzi z i składa się z jednego lub więcej innych formantów.

- **Model sterowania**. Formant niestandardowy <xref:System.Windows.Controls.Control> pochodzi z i jest używany do tworzenia implementacji, które oddzielają ich zachowanie od ich wygląd przy użyciu szablonów, podobnie jak większość formantów WPF. Wyprowadzenie z <xref:System.Windows.Controls.Control> pozwala na większą swobodę tworzenia niestandardowego interfejsu użytkownika niż formanty użytkownika, ale może wymagać więcej wysiłku.

- **Model elementu framework .** Formant niestandardowy <xref:System.Windows.FrameworkElement> wywodzi się z tego, kiedy jego wygląd jest zdefiniowany przez niestandardową logikę renderowania (nie szablony).

W poniższym przykładzie pokazano niestandardową kontrolkę <xref:System.Windows.Controls.UserControl>numeryczną w górę/w dół, która wywodzi się z:

[!code-xaml[IntroToWPFSnippets#UserControlMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_33.xaml)]

[!code-csharp[IntroToWPFSnippets#UserControlCODEBEHIND1](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_34.cs)]
[!code-vb[IntroToWPFSnippets#UserControlCODEBEHIND1](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_34.vb)]

Poniższy przykład ilustruje kod XAML, który jest wymagany <xref:System.Windows.Window>do włączenia formantu użytkownika do:

[!code-xaml[IntroToWPFSnippets#UserControlWindowMARKUP1](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_37.xaml)]

Na poniższej `NumericUpDown` ilustracji przedstawiono <xref:System.Windows.Window>formant hostowany w:

![Niestandardowa kontrola użytkownika](media/introduction-to-wpf/wpfintrofigure3.png)

Aby uzyskać więcej informacji na temat formantów niestandardowych, zobacz [Omówienie tworzenia formantu .](controls/control-authoring-overview.md)

## <a name="wpf-best-practices"></a>Najlepsze rozwiązania WPF

Podobnie jak w przypadku każdej platformy programistycznej, WPF WPF może służyć na wiele sposobów, aby osiągnąć pożądany wynik. W celu zapewnienia, że aplikacje WPF zapewniają wymagane środowisko użytkownika i spełniają wymagania odbiorców w ogóle, istnieją zalecane najlepsze rozwiązania dotyczące dostępności, globalizacji i lokalizacji i wydajności. Aby uzyskać więcej informacji, zobacz:

- [Ułatwienia dostępu](../ui-automation/accessibility-best-practices.md)
- [Globalizacja i lokalizacja WPF](advanced/wpf-globalization-and-localization-overview.md)
- [Wydajność aplikacji WPF](advanced/optimizing-wpf-application-performance.md)
- [Zabezpieczenia WPF](security-wpf.md)

## <a name="next-steps"></a>Następne kroki

Przyjrzeliśmy się kluczowym cechom WPF. Teraz nadszedł czas, aby zbudować swoją pierwszą aplikację WPF.

> [!div class="nextstepaction"]
> [Instruktaż: Moja pierwsza aplikacja komputerowa WPF](getting-started/walkthrough-my-first-wpf-desktop-application.md)

## <a name="see-also"></a>Zobacz też

- [Rozpoczynanie pracy z aparatem WPF](getting-started/index.md)
- [Windows Presentation Foundation](index.md)
- [Zasoby społeczności WPF](getting-started/community-feedback.md)
