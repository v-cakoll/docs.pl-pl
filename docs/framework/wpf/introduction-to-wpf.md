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
# <a name="wpf-overview"></a><span data-ttu-id="2e1b9-102">Omówienie podsystemu WPF</span><span class="sxs-lookup"><span data-stu-id="2e1b9-102">WPF overview</span></span>

<span data-ttu-id="2e1b9-103">Program Windows Presentation Foundation (WPF) umożliwia tworzenie aplikacji klienckich dla systemu Windows z oszałamiającymi wizualnie środowiskami użytkownika.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-103">Windows Presentation Foundation (WPF) lets you create desktop client applications for Windows with visually stunning user experiences.</span></span>

![Przykład interfejsu użytkownika usługi Contoso Healthcare](media/introduction-to-wpf/wpfintrofigure24.png)

<span data-ttu-id="2e1b9-105">Rdzeń WPF jest niezależny od rozdzielczości i wektorowy aparat renderowania, który jest zbudowany w celu skorzystania z nowoczesnego sprzętu graficznego.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-105">The core of WPF is a resolution-independent and vector-based rendering engine that is built to take advantage of modern graphics hardware.</span></span> <span data-ttu-id="2e1b9-106">WPF WPF rozszerza rdzeń o kompleksowy zestaw funkcji tworzenia aplikacji, które obejmują rozszerzalny język znaczników aplikacji (XAML), formanty, powiązanie danych, układ, grafikę 2D i 3D, animację, style, szablony, dokumenty, media, tekst i Typografia.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-106">WPF extends the core with a comprehensive set of application-development features that include Extensible Application Markup Language (XAML), controls, data binding, layout, 2D and 3D graphics, animation, styles, templates, documents, media, text, and typography.</span></span> <span data-ttu-id="2e1b9-107">WPF WPF jest częścią platformy .NET, dzięki czemu można tworzyć aplikacje, które zawierają inne elementy interfejsu API platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-107">WPF is part of .NET, so you can build applications that incorporate other elements of the .NET API.</span></span>

<span data-ttu-id="2e1b9-108">Ten przegląd jest przeznaczony dla początkujących i obejmuje kluczowe możliwości i pojęcia WPF.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-108">This overview is intended for newcomers and covers the key capabilities and concepts of WPF.</span></span>

## <a name="program-with-wpf"></a><span data-ttu-id="2e1b9-109">Program z WPF</span><span class="sxs-lookup"><span data-stu-id="2e1b9-109">Program with WPF</span></span>

<span data-ttu-id="2e1b9-110">WPF WPF istnieje jako podzbiór typów .NET, które <xref:System.Windows> są (w przeważającej części) znajduje się w obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-110">WPF exists as a subset of .NET types that are (for the most part) located in the <xref:System.Windows> namespace.</span></span> <span data-ttu-id="2e1b9-111">Jeśli wcześniej utworzyłeś aplikacje z platformy .NET przy użyciu zarządzanych technologii, takich jak ASP.NET i Windows Forms, podstawowe środowisko programowania WPF powinno być znane; tworzenie wystąpienia klas, ustawianie właściwości, metody wywołania i obsługi zdarzeń przy użyciu ulubionego języka programowania .NET, takiego jak C# lub Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-111">If you have previously built applications with .NET using managed technologies like ASP.NET and Windows Forms, the fundamental WPF programming experience should be familiar; you instantiate classes, set properties, call methods, and handle events, using your favorite .NET programming language, such as C# or Visual Basic.</span></span>

<span data-ttu-id="2e1b9-112">WPF WPF zawiera dodatkowe konstrukcje programowania, które zwiększają właściwości i zdarzenia: [właściwości zależności](advanced/dependency-properties-overview.md) i [kierowane zdarzenia.](advanced/routed-events-overview.md)</span><span class="sxs-lookup"><span data-stu-id="2e1b9-112">WPF includes additional programming constructs that enhance properties and events: [dependency properties](advanced/dependency-properties-overview.md) and [routed events](advanced/routed-events-overview.md).</span></span>

## <a name="markup-and-code-behind"></a><span data-ttu-id="2e1b9-113">Znaczniki i kod</span><span class="sxs-lookup"><span data-stu-id="2e1b9-113">Markup and code-behind</span></span>

<span data-ttu-id="2e1b9-114">WPF WPF umożliwia tworzenie aplikacji przy użyciu *znaczników* i *związane z kodem*, doświadczenie, z którym ASP.NET deweloperzy powinni być zaznajomieni.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-114">WPF lets you develop an application using both *markup* and *code-behind*, an experience with which ASP.NET developers should be familiar.</span></span> <span data-ttu-id="2e1b9-115">Zazwyczaj używasz znaczników XAML do implementowania wyglądu aplikacji podczas korzystania z zarządzanych języków programowania (związanych z kodem) w celu zaimplementowania jej zachowania.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-115">You generally use XAML markup to implement the appearance of an application while using managed programming languages (code-behind) to implement its behavior.</span></span> <span data-ttu-id="2e1b9-116">To oddzielenie wyglądu i zachowania ma następujące zalety:</span><span class="sxs-lookup"><span data-stu-id="2e1b9-116">This separation of appearance and behavior has the following benefits:</span></span>

- <span data-ttu-id="2e1b9-117">Koszty rozwoju i konserwacji są zmniejszone, ponieważ znaczniki specyficzne dla wyglądu nie są ściśle powiązane z kodem specyficznym dla zachowania.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-117">Development and maintenance costs are reduced because appearance-specific markup is not tightly coupled with behavior-specific code.</span></span>

- <span data-ttu-id="2e1b9-118">Programowanie jest bardziej wydajne, ponieważ projektanci mogą implementować wygląd aplikacji jednocześnie z deweloperami, którzy implementują zachowanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-118">Development is more efficient because designers can implement an application's appearance simultaneously with developers who are implementing the application's behavior.</span></span>

- <span data-ttu-id="2e1b9-119">[Globalizacja i lokalizacja](advanced/wpf-globalization-and-localization-overview.md) dla aplikacji WPF jest uproszczona.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-119">[Globalization and localization](advanced/wpf-globalization-and-localization-overview.md) for WPF applications is simplified.</span></span>

### <a name="markup"></a><span data-ttu-id="2e1b9-120">Znaczniki</span><span class="sxs-lookup"><span data-stu-id="2e1b9-120">Markup</span></span>

<span data-ttu-id="2e1b9-121">XAML to język znaczników oparty na języku XML, który implementuje wygląd aplikacji deklaratywnie.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-121">XAML is an XML-based markup language that implements an application's appearance declaratively.</span></span> <span data-ttu-id="2e1b9-122">Zazwyczaj służy do tworzenia okien, okien dialogowych, stron i formantów użytkownika oraz do wypełniania ich formantami, kształtami i grafiką.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-122">You typically use it to create windows, dialog boxes, pages, and user controls, and to fill them with controls, shapes, and graphics.</span></span>

<span data-ttu-id="2e1b9-123">W poniższym przykładzie użyto xaml do zaimplementowania wygląd okna, które zawiera jeden przycisk:</span><span class="sxs-lookup"><span data-stu-id="2e1b9-123">The following example uses XAML to implement the appearance of a window that contains a single button:</span></span>

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    Title="Window with Button"
    Width="250" Height="100">

  <!-- Add button to window -->
  <Button Name="button">Click Me!</Button>

</Window>
```

<span data-ttu-id="2e1b9-124">W szczególności ten kod XAML definiuje okno i `Window` `Button` przycisk przy użyciu i elementów, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-124">Specifically, this XAML defines a window and a button by using the `Window` and `Button` elements, respectively.</span></span> <span data-ttu-id="2e1b9-125">Każdy element jest skonfigurowany z `Window` atrybutami, `Title` takimi jak atrybut elementu, aby określić tekst paska tytułu okna.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-125">Each element is configured with attributes, such as the `Window` element's `Title` attribute to specify the window's title-bar text.</span></span> <span data-ttu-id="2e1b9-126">W czasie wykonywania WPF WPF konwertuje elementy i atrybuty, które są zdefiniowane w znacznikach do wystąpień klas WPF.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-126">At run time, WPF converts the elements and attributes that are defined in markup to instances of WPF classes.</span></span> <span data-ttu-id="2e1b9-127">Na przykład `Window` element jest konwertowany <xref:System.Windows.Window> na <xref:System.Windows.Window.Title%2A> wystąpienie klasy, `Title` której właściwość jest wartością atrybutu.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-127">For example, the `Window` element is converted to an instance of the <xref:System.Windows.Window> class whose <xref:System.Windows.Window.Title%2A> property is the value of the `Title` attribute.</span></span>

<span data-ttu-id="2e1b9-128">Na poniższym rysunku przedstawiono interfejs użytkownika (UI), który jest zdefiniowany przez kod XAML w poprzednim przykładzie:</span><span class="sxs-lookup"><span data-stu-id="2e1b9-128">The following figure shows the user interface (UI) that is defined by the XAML in the previous example:</span></span>

![Okno zawierające przycisk](media/introduction-to-wpf/wpfintrofigure10.png)

<span data-ttu-id="2e1b9-130">Ponieważ kod XAML jest oparty na języku XML, interfejs użytkownika, który jest z nim redagowany, jest zestawiony w hierarchii zagnieżdżonych elementów zwanych [drzewem elementów.](advanced/trees-in-wpf.md)</span><span class="sxs-lookup"><span data-stu-id="2e1b9-130">Since XAML is XML-based, the UI that you compose with it is assembled in a hierarchy of nested elements known as an [element tree](advanced/trees-in-wpf.md).</span></span> <span data-ttu-id="2e1b9-131">Drzewo elementów zapewnia logiczny i intuicyjny sposób tworzenia interfejsów użytkownika i zarządzania nimi.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-131">The element tree provides a logical and intuitive way to create and manage UIs.</span></span>

### <a name="code-behind"></a><span data-ttu-id="2e1b9-132">Zakodowane</span><span class="sxs-lookup"><span data-stu-id="2e1b9-132">Code-behind</span></span>

<span data-ttu-id="2e1b9-133">Głównym zachowaniem aplikacji jest zaimplementowanie funkcji, która odpowiada na interakcje użytkownika, w tym obsługi zdarzeń (na przykład kliknięcie menu, pasek narzędzi lub przycisk) i wywołanie logiki biznesowej i logiki dostępu do danych w odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-133">The main behavior of an application is to implement the functionality that responds to user interactions, including handling events (for example, clicking a menu, tool bar, or button) and calling business logic and data access logic in response.</span></span> <span data-ttu-id="2e1b9-134">W WPF WPF to zachowanie jest implementowane w kodzie, który jest skojarzony z znaczników.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-134">In WPF, this behavior is implemented in code that is associated with markup.</span></span> <span data-ttu-id="2e1b9-135">Ten typ kodu jest znany jako związany z kodem.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-135">This type of code is known as code-behind.</span></span> <span data-ttu-id="2e1b9-136">Poniższy przykład pokazuje zaktualizowane znaczniki z poprzedniego przykładu i związany z kodem:</span><span class="sxs-lookup"><span data-stu-id="2e1b9-136">The following example shows the updated markup from the previous example and the code-behind:</span></span>

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

<span data-ttu-id="2e1b9-137">W tym przykładzie związany z kodem implementuje <xref:System.Windows.Window> klasę, która pochodzi z klasy.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-137">In this example, the code-behind implements a class that derives from the <xref:System.Windows.Window> class.</span></span> <span data-ttu-id="2e1b9-138">Atrybut `x:Class` jest używany do skojarzenia znaczników z klasą zakodującą kod.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-138">The `x:Class` attribute is used to associate the markup with the code-behind class.</span></span> <span data-ttu-id="2e1b9-139">`InitializeComponent`jest wywoływana z konstruktora klasy związanej z kodem, aby scalić interfejs użytkownika, który jest zdefiniowany w znacznikach z klasą zakodową.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-139">`InitializeComponent` is called from the code-behind class's constructor to merge the UI that is defined in markup with the code-behind class.</span></span> <span data-ttu-id="2e1b9-140">(`InitializeComponent` jest generowany dla Ciebie, gdy aplikacja jest zbudowana, dlatego nie trzeba go zaimplementować ręcznie.) Połączenie `x:Class` i `InitializeComponent` upewnij się, że implementacja jest poprawnie inicjowane, gdy jest tworzony.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-140">(`InitializeComponent` is generated for you when your application is built, which is why you don't need to implement it manually.) The combination of `x:Class` and `InitializeComponent` ensure that your implementation is correctly initialized whenever it is created.</span></span> <span data-ttu-id="2e1b9-141">Klasa bez kodu implementuje również program obsługi zdarzeń <xref:System.Windows.Controls.Primitives.ButtonBase.Click> dla zdarzenia przycisku.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-141">The code-behind class also implements an event handler for the button's <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event.</span></span> <span data-ttu-id="2e1b9-142">Po kliknięciu przycisku program obsługi zdarzeń wyświetla okno <xref:System.Windows.MessageBox.Show%2A?displayProperty=fullName> komunikatu, wywołując metodę.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-142">When the button is clicked, the event handler shows a message box by calling the <xref:System.Windows.MessageBox.Show%2A?displayProperty=fullName> method.</span></span>

<span data-ttu-id="2e1b9-143">Na poniższej ilustracji przedstawiono wynik po kliknięciu przycisku:</span><span class="sxs-lookup"><span data-stu-id="2e1b9-143">The following figure shows the result when the button is clicked:</span></span>

![Skrzynka z wiadomościami](media/introduction-to-wpf/wpfintrofigure25.png)

## <a name="controls"></a><span data-ttu-id="2e1b9-145">Kontrolki</span><span class="sxs-lookup"><span data-stu-id="2e1b9-145">Controls</span></span>

<span data-ttu-id="2e1b9-146">Środowiska użytkownika, które są dostarczane przez model aplikacji są skonstruowane formanty.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-146">The user experiences that are delivered by the application model are constructed controls.</span></span> <span data-ttu-id="2e1b9-147">W WPF WPF *formantu* jest terminem parasola, który ma zastosowanie do kategorii klas WPF, które są hostowane w oknie lub na stronie, mają interfejs użytkownika i implementują pewne zachowanie.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-147">In WPF, *control* is an umbrella term that applies to a category of WPF classes that are hosted in either a window or a page, have a user interface, and implement some behavior.</span></span>

<span data-ttu-id="2e1b9-148">Aby uzyskać więcej informacji, zobacz [Formanty](controls/index.md).</span><span class="sxs-lookup"><span data-stu-id="2e1b9-148">For more information, see [Controls](controls/index.md).</span></span>

### <a name="wpf-controls-by-function"></a><span data-ttu-id="2e1b9-149">WPF kontroluje według funkcji</span><span class="sxs-lookup"><span data-stu-id="2e1b9-149">WPF controls by function</span></span>

<span data-ttu-id="2e1b9-150">Wbudowane formanty WPF są wymienione w tym miejscu:</span><span class="sxs-lookup"><span data-stu-id="2e1b9-150">The built-in WPF controls are listed here:</span></span>

- <span data-ttu-id="2e1b9-151">**Przyciski** <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Primitives.RepeatButton>: i .</span><span class="sxs-lookup"><span data-stu-id="2e1b9-151">**Buttons**: <xref:System.Windows.Controls.Button> and <xref:System.Windows.Controls.Primitives.RepeatButton>.</span></span>

- <span data-ttu-id="2e1b9-152">**Wyświetlanie**danych <xref:System.Windows.Controls.DataGrid> <xref:System.Windows.Controls.ListView>: <xref:System.Windows.Controls.TreeView>, , i .</span><span class="sxs-lookup"><span data-stu-id="2e1b9-152">**Data Display**: <xref:System.Windows.Controls.DataGrid>, <xref:System.Windows.Controls.ListView>, and <xref:System.Windows.Controls.TreeView>.</span></span>

- <span data-ttu-id="2e1b9-153">**Data wyświetlania i zaznaczania**: <xref:System.Windows.Controls.Calendar> i <xref:System.Windows.Controls.DatePicker>.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-153">**Date Display and Selection**: <xref:System.Windows.Controls.Calendar> and <xref:System.Windows.Controls.DatePicker>.</span></span>

- <span data-ttu-id="2e1b9-154">**Okna dialogowe**: <xref:Microsoft.Win32.OpenFileDialog>, <xref:System.Windows.Controls.PrintDialog>i <xref:Microsoft.Win32.SaveFileDialog>.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-154">**Dialog Boxes**: <xref:Microsoft.Win32.OpenFileDialog>, <xref:System.Windows.Controls.PrintDialog>, and <xref:Microsoft.Win32.SaveFileDialog>.</span></span>

- <span data-ttu-id="2e1b9-155">**Atrament cyfrowy** <xref:System.Windows.Controls.InkCanvas> : <xref:System.Windows.Controls.InkPresenter>i .</span><span class="sxs-lookup"><span data-stu-id="2e1b9-155">**Digital Ink**: <xref:System.Windows.Controls.InkCanvas> and <xref:System.Windows.Controls.InkPresenter>.</span></span>

- <span data-ttu-id="2e1b9-156">**Dokumenty** <xref:System.Windows.Controls.DocumentViewer>: <xref:System.Windows.Controls.FlowDocumentPageViewer> <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentScrollViewer>, <xref:System.Windows.Controls.StickyNoteControl>, , i .</span><span class="sxs-lookup"><span data-stu-id="2e1b9-156">**Documents**: <xref:System.Windows.Controls.DocumentViewer>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentScrollViewer>, and <xref:System.Windows.Controls.StickyNoteControl>.</span></span>

- <span data-ttu-id="2e1b9-157">**Wejście** <xref:System.Windows.Controls.TextBox>: <xref:System.Windows.Controls.RichTextBox>, <xref:System.Windows.Controls.PasswordBox>i .</span><span class="sxs-lookup"><span data-stu-id="2e1b9-157">**Input**: <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.RichTextBox>, and <xref:System.Windows.Controls.PasswordBox>.</span></span>

- <span data-ttu-id="2e1b9-158">**Układ** <xref:System.Windows.Controls.Border>: <xref:System.Windows.Controls.Primitives.BulletDecorator> <xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Controls.Expander>, <xref:System.Windows.Controls.Grid> <xref:System.Windows.Controls.GridView>, <xref:System.Windows.Controls.GridSplitter> <xref:System.Windows.Controls.GroupBox>, <xref:System.Windows.Controls.Panel> <xref:System.Windows.Controls.Primitives.ResizeGrip>, <xref:System.Windows.Controls.Separator> <xref:System.Windows.Controls.Primitives.ScrollBar>, <xref:System.Windows.Controls.ScrollViewer> <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.Primitives.Thumb> <xref:System.Windows.Controls.Viewbox>, <xref:System.Windows.Controls.VirtualizingStackPanel> <xref:System.Windows.Window>, <xref:System.Windows.Controls.WrapPanel>, , , , , , , , , , , i .</span><span class="sxs-lookup"><span data-stu-id="2e1b9-158">**Layout**: <xref:System.Windows.Controls.Border>, <xref:System.Windows.Controls.Primitives.BulletDecorator>, <xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Expander>, <xref:System.Windows.Controls.Grid>, <xref:System.Windows.Controls.GridView>, <xref:System.Windows.Controls.GridSplitter>, <xref:System.Windows.Controls.GroupBox>, <xref:System.Windows.Controls.Panel>, <xref:System.Windows.Controls.Primitives.ResizeGrip>, <xref:System.Windows.Controls.Separator>, <xref:System.Windows.Controls.Primitives.ScrollBar>, <xref:System.Windows.Controls.ScrollViewer>, <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.Primitives.Thumb>, <xref:System.Windows.Controls.Viewbox>, <xref:System.Windows.Controls.VirtualizingStackPanel>, <xref:System.Windows.Window>, and <xref:System.Windows.Controls.WrapPanel>.</span></span>

- <span data-ttu-id="2e1b9-159">**Media** <xref:System.Windows.Controls.Image>: <xref:System.Windows.Controls.MediaElement>, <xref:System.Windows.Controls.SoundPlayerAction>i .</span><span class="sxs-lookup"><span data-stu-id="2e1b9-159">**Media**: <xref:System.Windows.Controls.Image>, <xref:System.Windows.Controls.MediaElement>, and <xref:System.Windows.Controls.SoundPlayerAction>.</span></span>

- <span data-ttu-id="2e1b9-160">**Menu**: <xref:System.Windows.Controls.ContextMenu> <xref:System.Windows.Controls.Menu>, <xref:System.Windows.Controls.ToolBar>i .</span><span class="sxs-lookup"><span data-stu-id="2e1b9-160">**Menus**: <xref:System.Windows.Controls.ContextMenu>, <xref:System.Windows.Controls.Menu>, and <xref:System.Windows.Controls.ToolBar>.</span></span>

- <span data-ttu-id="2e1b9-161">**Nawigacja** <xref:System.Windows.Controls.Frame> <xref:System.Windows.Documents.Hyperlink>: <xref:System.Windows.Controls.Page> <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.TabControl>, , i .</span><span class="sxs-lookup"><span data-stu-id="2e1b9-161">**Navigation**: <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow>, and <xref:System.Windows.Controls.TabControl>.</span></span>

- <span data-ttu-id="2e1b9-162">**Wybór** <xref:System.Windows.Controls.CheckBox>: <xref:System.Windows.Controls.ComboBox> <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.RadioButton>, <xref:System.Windows.Controls.Slider>, , i .</span><span class="sxs-lookup"><span data-stu-id="2e1b9-162">**Selection**: <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.RadioButton>, and <xref:System.Windows.Controls.Slider>.</span></span>

- <span data-ttu-id="2e1b9-163">**Informacje o użytkowniku** <xref:System.Windows.Controls.AccessText>: <xref:System.Windows.Controls.TextBlock>, <xref:System.Windows.Controls.ToolTip> <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.ProgressBar>, <xref:System.Windows.Controls.Primitives.StatusBar>, , , i .</span><span class="sxs-lookup"><span data-stu-id="2e1b9-163">**User Information**: <xref:System.Windows.Controls.AccessText>, <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Primitives.Popup>, <xref:System.Windows.Controls.ProgressBar>, <xref:System.Windows.Controls.Primitives.StatusBar>, <xref:System.Windows.Controls.TextBlock>, and <xref:System.Windows.Controls.ToolTip>.</span></span>

## <a name="input-and-commands"></a><span data-ttu-id="2e1b9-164">Dane wejściowe i polecenia</span><span class="sxs-lookup"><span data-stu-id="2e1b9-164">Input and commands</span></span>

<span data-ttu-id="2e1b9-165">Formanty najczęściej wykrywają i reagują na dane wejściowe użytkownika.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-165">Controls most often detect and respond to user input.</span></span> <span data-ttu-id="2e1b9-166">[System wejściowy WPF](advanced/input-overview.md) używa zdarzeń bezpośrednich i kierowanych do obsługi wprowadzania tekstu, zarządzania fokusem i pozycjonowania myszy.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-166">The [WPF input system](advanced/input-overview.md) uses both direct and routed events to support text input, focus management, and mouse positioning.</span></span>

<span data-ttu-id="2e1b9-167">Aplikacje często mają złożone wymagania wejściowe.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-167">Applications often have complex input requirements.</span></span> <span data-ttu-id="2e1b9-168">WPF WPF udostępnia [system poleceń,](advanced/commanding-overview.md) który oddziela akcje wprowadzania danych użytkownika z kodu, który odpowiada na te akcje.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-168">WPF provides a [command system](advanced/commanding-overview.md) that separates user-input actions from the code that responds to those actions.</span></span>

## <a name="layout"></a><span data-ttu-id="2e1b9-169">Układ</span><span class="sxs-lookup"><span data-stu-id="2e1b9-169">Layout</span></span>

<span data-ttu-id="2e1b9-170">Podczas tworzenia interfejsu użytkownika można rozmieścić formanty według lokalizacji i rozmiaru, aby utworzyć układ.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-170">When you create a user interface, you arrange your controls by location and size to form a layout.</span></span> <span data-ttu-id="2e1b9-171">Kluczowym wymaganiem każdego układu jest dostosowanie się do zmian w rozmiarze okna i ustawieniach wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-171">A key requirement of any layout is to adapt to changes in window size and display settings.</span></span> <span data-ttu-id="2e1b9-172">Zamiast zmuszać do pisania kodu, aby dostosować układ w tych okolicznościach, WPF WPF zapewnia pierwszej klasy, rozszerzalny system układu dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-172">Rather than forcing you to write the code to adapt a layout in these circumstances, WPF provides a first-class, extensible layout system for you.</span></span>

<span data-ttu-id="2e1b9-173">Kamieniem węgielnym układu jest względne pozycjonowanie, co zwiększa możliwość dostosowania się do zmieniających się warunków okiennych i wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-173">The cornerstone of the layout system is relative positioning, which increases the ability to adapt to changing window and display conditions.</span></span> <span data-ttu-id="2e1b9-174">Ponadto system układu zarządza negocjacji między formantami w celu określenia układu.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-174">In addition, the layout system manages the negotiation between controls to determine the layout.</span></span> <span data-ttu-id="2e1b9-175">Negocjacja jest procesem dwuetapowym: po pierwsze, formant informuje rodzica, jakiej lokalizacji i rozmiaru wymaga; po drugie, rodzic informuje formant, jaką przestrzeń może mieć.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-175">The negotiation is a two-step process: first, a control tells its parent what location and size it requires; second, the parent tells the control what space it can have.</span></span>

<span data-ttu-id="2e1b9-176">System układu jest narażony na formanty podrzędne za pośrednictwem podstawowych klas WPF.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-176">The layout system is exposed to child controls through base WPF classes.</span></span> <span data-ttu-id="2e1b9-177">W przypadku typowych układów, takich jak siatki, układanie i dokowanie, WPF zawiera kilka formantów układu:</span><span class="sxs-lookup"><span data-stu-id="2e1b9-177">For common layouts such as grids, stacking, and docking, WPF includes several layout controls:</span></span>

- <span data-ttu-id="2e1b9-178"><xref:System.Windows.Controls.Canvas>: Formanty podrzędne zapewniają własny układ.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-178"><xref:System.Windows.Controls.Canvas>: Child controls provide their own layout.</span></span>

- <span data-ttu-id="2e1b9-179"><xref:System.Windows.Controls.DockPanel>: Elementy sterujące podrzędne są wyrównane do krawędzi panelu.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-179"><xref:System.Windows.Controls.DockPanel>: Child controls are aligned to the edges of the panel.</span></span>

- <span data-ttu-id="2e1b9-180"><xref:System.Windows.Controls.Grid>: Formanty podrzędne są umieszczane według wierszy i kolumn.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-180"><xref:System.Windows.Controls.Grid>: Child controls are positioned by rows and columns.</span></span>

- <span data-ttu-id="2e1b9-181"><xref:System.Windows.Controls.StackPanel>: Formanty podrzędne są ułożone pionowo lub poziomo.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-181"><xref:System.Windows.Controls.StackPanel>: Child controls are stacked either vertically or horizontally.</span></span>

- <span data-ttu-id="2e1b9-182"><xref:System.Windows.Controls.VirtualizingStackPanel>: Formanty podrzędne są zwirtualizowane i rozmieszczone w jednej linii, która jest zorientowana poziomo lub pionowo.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-182"><xref:System.Windows.Controls.VirtualizingStackPanel>: Child controls are virtualized and arranged on a single line that is either horizontally or vertically oriented.</span></span>

- <span data-ttu-id="2e1b9-183"><xref:System.Windows.Controls.WrapPanel>: Formanty podrzędne są umieszczane w kolejności od lewej do prawej i zawijane do następnego wiersza, gdy w bieżącym wierszu jest więcej formantów niż pozwala na to miejsce.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-183"><xref:System.Windows.Controls.WrapPanel>: Child controls are positioned in left-to-right order and wrapped to the next line when there are more controls on the current line than space allows.</span></span>

<span data-ttu-id="2e1b9-184">W poniższym przykładzie użyto a <xref:System.Windows.Controls.DockPanel> do rozłąki kilku <xref:System.Windows.Controls.TextBox> formantów:</span><span class="sxs-lookup"><span data-stu-id="2e1b9-184">The following example uses a <xref:System.Windows.Controls.DockPanel> to lay out several <xref:System.Windows.Controls.TextBox> controls:</span></span>

[!code-xaml[IntroToWPFSnippets#LayoutMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_1.xaml)]

<span data-ttu-id="2e1b9-185">Umożliwia <xref:System.Windows.Controls.DockPanel> formanty podrzędne, <xref:System.Windows.Controls.TextBox> aby powiedzieć, jak je rozmieścić.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-185">The <xref:System.Windows.Controls.DockPanel> allows the child <xref:System.Windows.Controls.TextBox> controls to tell it how to arrange them.</span></span> <span data-ttu-id="2e1b9-186">Aby to zrobić, <xref:System.Windows.Controls.DockPanel> implementuje `Dock` dołączone właściwości, która jest narażona na formanty podrzędne, aby umożliwić każdemu z nich określić styl dokowania.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-186">To do this, the <xref:System.Windows.Controls.DockPanel> implements a `Dock` attached property that is exposed to the child controls to allow each of them to specify a dock style.</span></span>

> [!NOTE]
> <span data-ttu-id="2e1b9-187">Właściwość, która jest implementowana przez formant nadrzędny do użytku przez formanty podrzędne jest WPF konstrukcji o nazwie [dołączonej właściwości.](advanced/attached-properties-overview.md)</span><span class="sxs-lookup"><span data-stu-id="2e1b9-187">A property that's implemented by a parent control for use by child controls is a WPF construct called an [attached property](advanced/attached-properties-overview.md).</span></span>

<span data-ttu-id="2e1b9-188">Na poniższym rysunku przedstawiono wynik znaczników XAML w poprzednim przykładzie:</span><span class="sxs-lookup"><span data-stu-id="2e1b9-188">The following figure shows the result of the XAML markup in the preceding example:</span></span>

![Strona DockPanel](media/introduction-to-wpf/wpfintrofigure11.png)

## <a name="data-binding"></a><span data-ttu-id="2e1b9-190">Powiązanie danych</span><span class="sxs-lookup"><span data-stu-id="2e1b9-190">Data binding</span></span>

<span data-ttu-id="2e1b9-191">Większość aplikacji jest tworzona w celu zapewnienia użytkownikom środków do wyświetlania i edytowania danych.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-191">Most applications are created to provide users with the means to view and edit data.</span></span> <span data-ttu-id="2e1b9-192">W przypadku aplikacji WPF praca przechowywania i uzyskiwania dostępu do danych jest już przewidziana przez technologie, takie jak SQL Server i ADO .NET.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-192">For WPF applications, the work of storing and accessing data is already provided for by technologies such as SQL Server and ADO .NET.</span></span> <span data-ttu-id="2e1b9-193">Po dostęp do danych i załadowany do obiektów zarządzanych aplikacji rozpoczyna się ciężka praca dla aplikacji WPF.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-193">After the data is accessed and loaded into an application's managed objects, the hard work for WPF applications begins.</span></span> <span data-ttu-id="2e1b9-194">Zasadniczo wiąże się to z dwiema rzeczami:</span><span class="sxs-lookup"><span data-stu-id="2e1b9-194">Essentially, this involves two things:</span></span>

1. <span data-ttu-id="2e1b9-195">Kopiowanie danych z obiektów zarządzanych do formantów, w których dane mogą być wyświetlane i edytowane.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-195">Copying the data from the managed objects into controls, where the data can be displayed and edited.</span></span>

2. <span data-ttu-id="2e1b9-196">Upewniając się, że zmiany wprowadzone do danych przy użyciu formantów są kopiowane z powrotem do obiektów zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-196">Ensuring that changes made to data by using controls are copied back to the managed objects.</span></span>

<span data-ttu-id="2e1b9-197">Aby uprościć tworzenie aplikacji, WPF WPF udostępnia aparat wiązania danych, aby automatycznie wykonać te kroki.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-197">To simplify application development, WPF provides a data binding engine to automatically perform these steps.</span></span> <span data-ttu-id="2e1b9-198">Podstawową jednostką aparatu wiązania <xref:System.Windows.Data.Binding> danych jest klasa, której zadaniem jest powiązanie formantu (docelowego powiązania) z obiektem danych (źródłem powiązania).</span><span class="sxs-lookup"><span data-stu-id="2e1b9-198">The core unit of the data binding engine is the <xref:System.Windows.Data.Binding> class, whose job is to bind a control (the binding target) to a data object (the binding source).</span></span> <span data-ttu-id="2e1b9-199">Związek ten ilustruje poniższy rysunek:</span><span class="sxs-lookup"><span data-stu-id="2e1b9-199">This relationship is illustrated by the following figure:</span></span>

![Diagram wiązania danych podstawowych](media/introduction-to-wpf/databindingmostbasic.png)

<span data-ttu-id="2e1b9-201">W następnym przykładzie pokazano, <xref:System.Windows.Controls.TextBox> jak powiązać `Person` z wystąpieniem obiektu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-201">The next example demonstrates how to bind a <xref:System.Windows.Controls.TextBox> to an instance of a custom `Person` object.</span></span> <span data-ttu-id="2e1b9-202">Implementacja `Person` jest pokazana w następującym kodzie:</span><span class="sxs-lookup"><span data-stu-id="2e1b9-202">The `Person` implementation is shown in the following code:</span></span>

[!code-vb[SimpleDataBindingSnippets#PersonClassCODE](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_2.vb)]
[!code-csharp[SimpleDataBindingSnippets#PersonClassCODE](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_2.cs)]

<span data-ttu-id="2e1b9-203">Następujące znaczniki wiąże <xref:System.Windows.Controls.TextBox> się z wystąpieniem `Person` obiektu niestandardowego:</span><span class="sxs-lookup"><span data-stu-id="2e1b9-203">The following markup binds the <xref:System.Windows.Controls.TextBox> to an instance of a custom `Person` object:</span></span>

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

<span data-ttu-id="2e1b9-204">W tym przykładzie `Person` klasa jest tworzone w kodzie i jest ustawiona jako kontekst danych dla . `DataBindingWindow`</span><span class="sxs-lookup"><span data-stu-id="2e1b9-204">In this example, the `Person` class is instantiated in code-behind and is set as the data context for the `DataBindingWindow`.</span></span> <span data-ttu-id="2e1b9-205"><xref:System.Windows.Controls.TextBox.Text%2A> W znacznikach właściwość <xref:System.Windows.Controls.TextBox> jest powiązana `Person.Name` z właściwością`{Binding ... }`(przy użyciu " " składni XAML).</span><span class="sxs-lookup"><span data-stu-id="2e1b9-205">In markup, the <xref:System.Windows.Controls.TextBox.Text%2A> property of the <xref:System.Windows.Controls.TextBox> is bound to the `Person.Name` property (using the "`{Binding ... }`" XAML syntax).</span></span> <span data-ttu-id="2e1b9-206">Ten XAML mówi WPF <xref:System.Windows.Controls.TextBox> do `Person` powiązania formantu <xref:System.Windows.FrameworkElement.DataContext%2A> do obiektu, który jest przechowywany we właściwości okna.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-206">This XAML tells WPF to bind the <xref:System.Windows.Controls.TextBox> control to the `Person` object that is stored in the <xref:System.Windows.FrameworkElement.DataContext%2A> property of the window.</span></span>

<span data-ttu-id="2e1b9-207">Aparat wiązania danych WPF zapewnia dodatkową obsługę, która obejmuje sprawdzanie poprawności, sortowanie, filtrowanie i grupowanie.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-207">The WPF data binding engine provides additional support that includes validation, sorting, filtering, and grouping.</span></span> <span data-ttu-id="2e1b9-208">Ponadto powiązanie danych obsługuje użycie szablonów danych do tworzenia niestandardowego interfejsu użytkownika dla danych powiązanych, gdy interfejs użytkownika wyświetlany przez standardowe formanty WPF nie jest odpowiedni.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-208">Furthermore, data binding supports the use of data templates to create custom user interface for bound data when the user interface displayed by the standard WPF controls is not appropriate.</span></span>

<span data-ttu-id="2e1b9-209">Aby uzyskać więcej informacji, zobacz [Omówienie powiązania danych](../../desktop-wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2e1b9-209">For more information, see [Data binding overview](../../desktop-wpf/data/data-binding-overview.md).</span></span>

## <a name="graphics"></a><span data-ttu-id="2e1b9-210">Grafika</span><span class="sxs-lookup"><span data-stu-id="2e1b9-210">Graphics</span></span>

<span data-ttu-id="2e1b9-211">WPF WPF wprowadza obszerny, skalowalny i elastyczny zestaw funkcji graficznych, które mają następujące zalety:</span><span class="sxs-lookup"><span data-stu-id="2e1b9-211">WPF introduces an extensive, scalable, and flexible set of graphics features that have the following benefits:</span></span>

- <span data-ttu-id="2e1b9-212">**Grafika niezależna od rozdzielczości i niezależna od urządzenia**.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-212">**Resolution-independent and device-independent graphics**.</span></span> <span data-ttu-id="2e1b9-213">Podstawową jednostką miary w systemie graficznym WPF jest piksel niezależny od urządzenia, który jest 1/96 cala, niezależnie od rzeczywistej rozdzielczości ekranu i stanowi podstawę do renderowania niezależnego od rozdzielczości i niezależnego od urządzenia.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-213">The basic unit of measurement in the WPF graphics system is the device-independent pixel, which is 1/96th of an inch, regardless of actual screen resolution, and provides the foundation for resolution-independent and device-independent rendering.</span></span> <span data-ttu-id="2e1b9-214">Każdy piksel niezależny od urządzenia jest automatycznie skalowany w celu dopasowania ustawienia punktów na cal (dpi) systemu, na który renderuje.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-214">Each device-independent pixel automatically scales to match the dots-per-inch (dpi) setting of the system it renders on.</span></span>

- <span data-ttu-id="2e1b9-215">**Poprawiono precyzję**.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-215">**Improved precision**.</span></span> <span data-ttu-id="2e1b9-216">Układ współrzędnych WPF jest mierzony za pomocą liczb zmiennoprzecinkowych o podwójnej precyzji, a nie z pojedynczą precyzją.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-216">The WPF coordinate system is measured with double-precision floating-point numbers rather than single-precision.</span></span> <span data-ttu-id="2e1b9-217">Przekształcenia i wartości krycia są również wyrażone jako podwójna precyzja.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-217">Transformations and opacity values are also expressed as double-precision.</span></span> <span data-ttu-id="2e1b9-218">WPF WPF obsługuje również szeroką gamę kolorów (scRGB) i zapewnia zintegrowaną obsługę zarządzania wejściami z różnych przestrzeni kolorów.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-218">WPF also supports a wide color gamut (scRGB) and provides integrated support for managing inputs from different color spaces.</span></span>

- <span data-ttu-id="2e1b9-219">**Zaawansowana obsługa grafiki i animacji**.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-219">**Advanced graphics and animation support**.</span></span> <span data-ttu-id="2e1b9-220">WPF WPF upraszcza programowanie grafiki, zarządzając scenami animacji; nie ma potrzeby martwić się o przetwarzanie sceny, renderowanie pętli i interpolacji dwuliniowej.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-220">WPF simplifies graphics programming by managing animation scenes for you; there is no need to worry about scene processing, rendering loops, and bilinear interpolation.</span></span> <span data-ttu-id="2e1b9-221">Ponadto WPF WPF zapewnia obsługę testowania trafień i pełną obsługę kompozycji alfa.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-221">Additionally, WPF provides hit-testing support and full alpha-compositing support.</span></span>

- <span data-ttu-id="2e1b9-222">**Akceleracja sprzętowa**.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-222">**Hardware acceleration**.</span></span> <span data-ttu-id="2e1b9-223">System graficzny WPF wykorzystuje sprzęt graficzny, aby zminimalizować użycie procesora.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-223">The WPF graphics system takes advantage of graphics hardware to minimize CPU usage.</span></span>

### <a name="2d-shapes"></a><span data-ttu-id="2e1b9-224">Kształty 2D</span><span class="sxs-lookup"><span data-stu-id="2e1b9-224">2D shapes</span></span>

<span data-ttu-id="2e1b9-225">WPF WPF udostępnia bibliotekę typowych kształtów 2D rysowane wektorami, takich jak prostokąty i elipsy, które są wyświetlane na poniższej ilustracji:</span><span class="sxs-lookup"><span data-stu-id="2e1b9-225">WPF provides a library of common vector-drawn 2D shapes, such as the rectangles and ellipses that are shown in the following illustration:</span></span>

![Elipsy i prostokąty](media/introduction-to-wpf/wpfintrofigure4.PNG)

<span data-ttu-id="2e1b9-227">Ciekawą możliwością kształtów jest to, że nie są one przeznaczone tylko do wyświetlania; kształty implementują wiele funkcji, których oczekujesz od formantów, w tym klawiatury i myszy.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-227">An interesting capability of shapes is that they are not just for display; shapes implement many of the features that you expect from controls, including keyboard and mouse input.</span></span> <span data-ttu-id="2e1b9-228">Poniższy przykład <xref:System.Windows.UIElement.MouseUp> przedstawia zdarzenie <xref:System.Windows.Shapes.Ellipse> obsługiwanej:</span><span class="sxs-lookup"><span data-stu-id="2e1b9-228">The following example shows the <xref:System.Windows.UIElement.MouseUp> event of an <xref:System.Windows.Shapes.Ellipse> being handled:</span></span>

[!code-xaml[IntroToWPFSnippets#HandleEllipseMouseUpEventMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_7.xaml)]

[!code-vb[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_8.vb)]
[!code-csharp[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_8.cs)]

<span data-ttu-id="2e1b9-229">Na poniższej ilustracji przedstawiono, co jest produkowane przez poprzedni kod:</span><span class="sxs-lookup"><span data-stu-id="2e1b9-229">The following figure shows what is produced by the preceding code:</span></span>

![Okno z tekstem "kliknąłeś&#33; elipsy"](media/introduction-to-wpf/wpfintrofigure12.png)

<span data-ttu-id="2e1b9-231">Aby uzyskać więcej informacji, zobacz [Kształty i rysunek podstawowy w przeglądzie WPF](../../desktop-wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2e1b9-231">For more information, see [Shapes and basic drawing in WPF overview](../../desktop-wpf/data/data-binding-overview.md).</span></span>

### <a name="2d-geometries"></a><span data-ttu-id="2e1b9-232">Geometrie 2D</span><span class="sxs-lookup"><span data-stu-id="2e1b9-232">2D geometries</span></span>

<span data-ttu-id="2e1b9-233">Kształty 2D dostarczane przez WPF obejmują standardowy zestaw podstawowych kształtów.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-233">The 2D shapes provided by WPF cover the standard set of basic shapes.</span></span> <span data-ttu-id="2e1b9-234">Jednak może być konieczne utworzenie kształtów niestandardowych, aby ułatwić projektowanie dostosowanego interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-234">However, you may need to create custom shapes to facilitate the design of a customized user interface.</span></span> <span data-ttu-id="2e1b9-235">W tym celu WPF WPF zapewnia geometrie.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-235">For this purpose, WPF provides geometries.</span></span> <span data-ttu-id="2e1b9-236">Na poniższym rysunku przedstawiono użycie geometrii do utworzenia niestandardowego kształtu, który może być rysowany bezpośrednio, używany jako pędzel lub używany do przycinania innych kształtów i formantów.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-236">The following figure demonstrates the use of geometries to create a custom shape that can be drawn directly, used as a brush, or used to clip other shapes and controls.</span></span>

<span data-ttu-id="2e1b9-237"><xref:System.Windows.Shapes.Path>obiekty mogą być używane do rysowania zamkniętych lub otwartych kształtów, wielu kształtów, a nawet zakrzywionych kształtów.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-237"><xref:System.Windows.Shapes.Path> objects can be used to draw closed or open shapes, multiple shapes, and even curved shapes.</span></span>

<span data-ttu-id="2e1b9-238"><xref:System.Windows.Media.Geometry>obiekty mogą być używane do przycinania, testowania trafień i renderowania danych graficznych 2D.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-238"><xref:System.Windows.Media.Geometry> objects can be used for clipping, hit-testing, and rendering 2D graphic data.</span></span>

![Różne zastosowania ścieżki](media/introduction-to-wpf/wpfintrofigure5.png)

<span data-ttu-id="2e1b9-240">Aby uzyskać więcej informacji, zobacz [Omówienie geometrii](graphics-multimedia/geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2e1b9-240">For more information, see [Geometry overview](graphics-multimedia/geometry-overview.md).</span></span>

### <a name="2d-effects"></a><span data-ttu-id="2e1b9-241">Efekty 2D</span><span class="sxs-lookup"><span data-stu-id="2e1b9-241">2D effects</span></span>

<span data-ttu-id="2e1b9-242">Podzbiór funkcji WPF 2D zawiera efekty wizualne, takie jak gradienty, mapy bitowe, rysunki, malowanie klipami wideo, obrót, skalowanie i pochylanie.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-242">A subset of WPF 2D capabilities includes visual effects, such as gradients, bitmaps, drawings, painting with videos, rotation, scaling, and skewing.</span></span> <span data-ttu-id="2e1b9-243">Wszystkie te są osiągane za pomocą pędzli; na poniższym rysunku przedstawiono kilka przykładów:</span><span class="sxs-lookup"><span data-stu-id="2e1b9-243">These are all achieved with brushes; the following figure shows some examples:</span></span>

![Ilustracja różnych pędzli](media/introduction-to-wpf/wpfintrofigure6.png)

<span data-ttu-id="2e1b9-245">Aby uzyskać więcej informacji, zobacz [omówienie pędzli WPF](graphics-multimedia/wpf-brushes-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2e1b9-245">For more information, see [WPF brushes overview](graphics-multimedia/wpf-brushes-overview.md).</span></span>

### <a name="3d-rendering"></a><span data-ttu-id="2e1b9-246">Renderowanie 3D</span><span class="sxs-lookup"><span data-stu-id="2e1b9-246">3D rendering</span></span>

<span data-ttu-id="2e1b9-247">WPF WPF zawiera również funkcje renderowania 3D, które integrują się z grafiką 2-w, aby umożliwić tworzenie bardziej ekscytujących i interesujących interfejsów użytkownika.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-247">WPF also includes 3D rendering capabilities that integrate with 2-d graphics to allow the creation of more exciting and interesting user interfaces.</span></span> <span data-ttu-id="2e1b9-248">Na przykład na poniższej ilustracji przedstawiono obrazy 2D renderowane na kształtach 3D:</span><span class="sxs-lookup"><span data-stu-id="2e1b9-248">For example, the following figure shows 2D images rendered onto 3D shapes:</span></span>

![Zrzut ekranu przykładowy Visual3D](media/introduction-to-wpf/wpfintrofigure13.png)

<span data-ttu-id="2e1b9-250">Aby uzyskać więcej informacji, zobacz [omówienie grafiki 3D](graphics-multimedia/3-d-graphics-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2e1b9-250">For more information, see [3D graphics overview](graphics-multimedia/3-d-graphics-overview.md).</span></span>

## <a name="animation"></a><span data-ttu-id="2e1b9-251">Animacja</span><span class="sxs-lookup"><span data-stu-id="2e1b9-251">Animation</span></span>

<span data-ttu-id="2e1b9-252">Obsługa animacji WPF umożliwia tworzenie formantów, powiększanie, obracanie i zanikanie, tworzenie interesujących przejść stron i nie tylko.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-252">WPF animation support lets you make controls grow, shake, spin, and fade, to create interesting page transitions, and more.</span></span> <span data-ttu-id="2e1b9-253">Można animować większość klas WPF, nawet klas niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-253">You can animate most WPF classes, even custom classes.</span></span> <span data-ttu-id="2e1b9-254">Na poniższej ilustracji przedstawiono prostą animację w akcji:</span><span class="sxs-lookup"><span data-stu-id="2e1b9-254">The following figure shows a simple animation in action:</span></span>

![Obrazy animowanego sześcianu](media/introduction-to-wpf/wpfintrofigure7.png)

<span data-ttu-id="2e1b9-256">Aby uzyskać więcej informacji, zobacz [Omówienie animacji](graphics-multimedia/animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2e1b9-256">For more information, see [Animation overview](graphics-multimedia/animation-overview.md).</span></span>

## <a name="media"></a><span data-ttu-id="2e1b9-257">Multimedia</span><span class="sxs-lookup"><span data-stu-id="2e1b9-257">Media</span></span>

<span data-ttu-id="2e1b9-258">Jednym ze sposobów przekazywania bogatych treści jest wykorzystanie mediów audiowizualnych.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-258">One way to convey rich content is through the use of audiovisual media.</span></span> <span data-ttu-id="2e1b9-259">WPF WPF zapewnia specjalną obsługę obrazów, wideo i audio.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-259">WPF provides special support for images, video, and audio.</span></span>

### <a name="images"></a><span data-ttu-id="2e1b9-260">Obrazy</span><span class="sxs-lookup"><span data-stu-id="2e1b9-260">Images</span></span>

<span data-ttu-id="2e1b9-261">Obrazy są wspólne dla większości aplikacji i WPF WPF udostępnia kilka sposobów ich używania.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-261">Images are common to most applications, and WPF provides several ways to use them.</span></span> <span data-ttu-id="2e1b9-262">Na poniższej ilustracji przedstawiono interfejs użytkownika z polem listy zawierającym miniatury obrazów.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-262">The following figure shows a user interface with a list box that contains thumbnail images.</span></span> <span data-ttu-id="2e1b9-263">Po wybraniu miniatury obraz jest wyświetlany w pełnym rozmiarze.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-263">When a thumbnail is selected, the image is shown full-size.</span></span>

![Miniatury obrazów i obrazu o pełnym rozmiarze&#45;](media/introduction-to-wpf/wpfintrofigure8.png)

<span data-ttu-id="2e1b9-265">Aby uzyskać więcej informacji, zobacz [Omówienie obrazowania](graphics-multimedia/imaging-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2e1b9-265">For more information, see [Imaging overview](graphics-multimedia/imaging-overview.md).</span></span>

### <a name="video-and-audio"></a><span data-ttu-id="2e1b9-266">Wideo i audio</span><span class="sxs-lookup"><span data-stu-id="2e1b9-266">Video and audio</span></span>

<span data-ttu-id="2e1b9-267">Sterowanie <xref:System.Windows.Controls.MediaElement> jest w stanie odtwarzać zarówno wideo, jak i audio i jest wystarczająco elastyczne, aby stanowić podstawę niestandardowego odtwarzacza multimedialnego.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-267">The <xref:System.Windows.Controls.MediaElement> control is capable of playing both video and audio, and it is flexible enough to be the basis for a custom media player.</span></span> <span data-ttu-id="2e1b9-268">Następujące znaczniki XAML implementują odtwarzacz multimedialny:</span><span class="sxs-lookup"><span data-stu-id="2e1b9-268">The following XAML markup implements a media player:</span></span>

[!code-xaml[IntroToWPFSnippets#MediaElementMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_9.xaml)]

<span data-ttu-id="2e1b9-269">Okno na poniższej ilustracji pokazuje formant <xref:System.Windows.Controls.MediaElement> w akcji:</span><span class="sxs-lookup"><span data-stu-id="2e1b9-269">The window in the following figure shows the <xref:System.Windows.Controls.MediaElement> control in action:</span></span>

![Sterowanie MediaElement z dźwiękiem i wideo](media/introduction-to-wpf/wpfintrofigure1.png)

<span data-ttu-id="2e1b9-271">Aby uzyskać więcej informacji, zobacz [Grafika i multimedia](graphics-multimedia/index.md).</span><span class="sxs-lookup"><span data-stu-id="2e1b9-271">For more information, see [Graphics and multimedia](graphics-multimedia/index.md).</span></span>

## <a name="text-and-typography"></a><span data-ttu-id="2e1b9-272">Tekst i typografia</span><span class="sxs-lookup"><span data-stu-id="2e1b9-272">Text and typography</span></span>

<span data-ttu-id="2e1b9-273">Aby ułatwić renderowanie tekstu wysokiej jakości, WPF WPF oferuje następujące funkcje:</span><span class="sxs-lookup"><span data-stu-id="2e1b9-273">To facilitate high-quality text rendering, WPF offers the following features:</span></span>

- <span data-ttu-id="2e1b9-274">Obsługa czcionek OpenType.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-274">OpenType font support.</span></span>

- <span data-ttu-id="2e1b9-275">Ulepszenia ClearType.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-275">ClearType enhancements.</span></span>

- <span data-ttu-id="2e1b9-276">Wysoka wydajność, która wykorzystuje akcelerację sprzętową.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-276">High performance that takes advantage of hardware acceleration.</span></span>

- <span data-ttu-id="2e1b9-277">Integracja tekstu z multimediami, grafiką i animacją.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-277">Integration of text with media, graphics, and animation.</span></span>

- <span data-ttu-id="2e1b9-278">Międzynarodowa obsługa czcionek i mechanizmy rezerwowe.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-278">International font support and fallback mechanisms.</span></span>

<span data-ttu-id="2e1b9-279">Jako demonstracja integracji tekstu z grafiką, na poniższej ilustracji przedstawiono zastosowanie dekoracji tekstowych:</span><span class="sxs-lookup"><span data-stu-id="2e1b9-279">As a demonstration of text integration with graphics, the following figure shows the application of text decorations:</span></span>

![Tekst z różnymi dekoracjami tekstowymi](media/introduction-to-wpf/wpfintrofigure23.png)

<span data-ttu-id="2e1b9-281">Aby uzyskać więcej informacji, zobacz [Typografia w programie Windows Presentation Foundation](advanced/typography-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="2e1b9-281">For more information, see [Typography in Windows Presentation Foundation](advanced/typography-in-wpf.md).</span></span>

## <a name="customize-wpf-apps"></a><span data-ttu-id="2e1b9-282">Dostosowywanie aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="2e1b9-282">Customize WPF apps</span></span>

<span data-ttu-id="2e1b9-283">Do tego momentu widzieliśmy podstawowe bloki konstrukcyjne WPF do tworzenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-283">Up to this point, you've seen the core WPF building blocks for developing applications.</span></span> <span data-ttu-id="2e1b9-284">Model aplikacji służy do hostowania i dostarczania zawartości aplikacji, która składa się głównie z formantów.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-284">You use the application model to host and deliver application content, which consists mainly of controls.</span></span> <span data-ttu-id="2e1b9-285">Aby uprościć rozmieszczenie formantów w interfejsie użytkownika i upewnić się, że układ jest utrzymywany w obliczu zmian w ustawieniach rozmiaru okna i wyświetlania, należy użyć systemu układu WPF.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-285">To simplify the arrangement of controls in a user interface, and to ensure the arrangement is maintained in the face of changes to window size and display settings, you use the WPF layout system.</span></span> <span data-ttu-id="2e1b9-286">Ponieważ większość aplikacji umożliwiają użytkownikom interakcję z danymi, można użyć powiązania danych, aby zmniejszyć pracę integracji interfejsu użytkownika z danymi.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-286">Because most applications let users interact with data, you use data binding to reduce the work of integrating your user interface with data.</span></span> <span data-ttu-id="2e1b9-287">Aby poprawić wygląd aplikacji, należy użyć kompleksowego zakresu grafiki, animacji i obsługi multimediów zapewnianych przez WPF.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-287">To enhance the visual appearance of your application, you use the comprehensive range of graphics, animation, and media support provided by WPF.</span></span>

<span data-ttu-id="2e1b9-288">Często jednak podstawy nie wystarczą do tworzenia i zarządzania naprawdę odrębnym i oszałamiającym wizualnie doświadczeniem użytkownika.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-288">Often, though, the basics are not enough for creating and managing a truly distinct and visually stunning user experience.</span></span> <span data-ttu-id="2e1b9-289">Standardowe formanty WPF może nie zintegrować z żądanym wyglądem aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-289">The standard WPF controls might not integrate with the desired appearance of your application.</span></span> <span data-ttu-id="2e1b9-290">Dane mogą nie być wyświetlane w najbardziej efektywny sposób.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-290">Data might not be displayed in the most effective way.</span></span> <span data-ttu-id="2e1b9-291">Ogólne środowisko użytkownika aplikacji może nie być dostosowane do domyślnego wyglądu i działanie motywów systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-291">Your application's overall user experience may not be suited to the default look and feel of Windows themes.</span></span> <span data-ttu-id="2e1b9-292">Pod wieloma względami technologia prezentacji wymaga rozszerzalności wizualnej tak samo, jak każdy inny rodzaj rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-292">In many ways, a presentation technology needs visual extensibility as much as any other type of extensibility.</span></span>

<span data-ttu-id="2e1b9-293">Z tego powodu WPF WPF udostępnia wiele mechanizmów do tworzenia unikatowych środowisk użytkownika, w tym model zawartości bogatej dla formantów, wyzwalaczy, szablonów kontroli i danych, style, zasoby interfejsu użytkownika i motywy i karnacje.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-293">For this reason, WPF provides a variety of mechanisms for creating unique user experiences, including a rich content model for controls, triggers, control and data templates, styles, user interface resources, and themes and skins.</span></span>

### <a name="content-model"></a><span data-ttu-id="2e1b9-294">Model zawartości</span><span class="sxs-lookup"><span data-stu-id="2e1b9-294">Content model</span></span>

<span data-ttu-id="2e1b9-295">Głównym celem większości formantów WPF jest wyświetlanie zawartości.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-295">The main purpose of a majority of the WPF controls is to display content.</span></span> <span data-ttu-id="2e1b9-296">W WPF WPF, typ i liczba elementów, które mogą stanowić zawartość formantu jest określany jako *model zawartości*formantu .</span><span class="sxs-lookup"><span data-stu-id="2e1b9-296">In WPF, the type and number of items that can constitute the content of a control is referred to as the control's *content model*.</span></span> <span data-ttu-id="2e1b9-297">Niektóre formanty mogą zawierać pojedynczy element i typ zawartości; na przykład zawartość jest <xref:System.Windows.Controls.TextBox> wartość ciągu, który jest <xref:System.Windows.Controls.TextBox.Text%2A> przypisany do właściwości.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-297">Some controls can contain a single item and type of content; for example, the content of a <xref:System.Windows.Controls.TextBox> is a string value that is assigned to the <xref:System.Windows.Controls.TextBox.Text%2A> property.</span></span> <span data-ttu-id="2e1b9-298">Poniższy przykład określa zawartość <xref:System.Windows.Controls.TextBox>:</span><span class="sxs-lookup"><span data-stu-id="2e1b9-298">The following example sets the content of a <xref:System.Windows.Controls.TextBox>:</span></span>

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.TextBoxContentWindow"
    Title="TextBox Content">

    <TextBox Text="This is the content of a TextBox." />
</Window>
```

<span data-ttu-id="2e1b9-299">Na poniższej ilustracji przedstawiono wynik:</span><span class="sxs-lookup"><span data-stu-id="2e1b9-299">The following figure shows the result:</span></span>

![Formant pola tekstowego zawierający tekst](media/introduction-to-wpf/wpfintrofigure21.png)

<span data-ttu-id="2e1b9-301">Inne formanty mogą jednak zawierać wiele elementów o różnych typach zawartości; zawartość , <xref:System.Windows.Controls.Button>określona przez <xref:System.Windows.Controls.ContentControl.Content%2A> właściwość, może zawierać wiele elementów, w tym formantów układu, tekst, obrazy i kształty.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-301">Other controls, however, can contain multiple items of different types of content; the content of a <xref:System.Windows.Controls.Button>, specified by the <xref:System.Windows.Controls.ContentControl.Content%2A> property, can contain a variety of items including layout controls, text, images, and shapes.</span></span> <span data-ttu-id="2e1b9-302">Poniższy przykład <xref:System.Windows.Controls.Button> przedstawia zawartość z <xref:System.Windows.Controls.DockPanel>zawartością, <xref:System.Windows.Controls.Border>która <xref:System.Windows.Controls.MediaElement>zawiera , a <xref:System.Windows.Controls.Label>, a i :</span><span class="sxs-lookup"><span data-stu-id="2e1b9-302">The following example shows a <xref:System.Windows.Controls.Button> with content that includes a <xref:System.Windows.Controls.DockPanel>, a <xref:System.Windows.Controls.Label>, a <xref:System.Windows.Controls.Border>, and a <xref:System.Windows.Controls.MediaElement>:</span></span>

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

<span data-ttu-id="2e1b9-303">Na poniższej ilustracji przedstawiono zawartość tego przycisku:</span><span class="sxs-lookup"><span data-stu-id="2e1b9-303">The following figure shows the content of this button:</span></span>

![Przycisk zawierający wiele typów zawartości](media/introduction-to-wpf/wpfintrofigure22.png)

<span data-ttu-id="2e1b9-305">Aby uzyskać więcej informacji na temat rodzajów zawartości, która jest obsługiwana przez różne formanty, zobacz [Model zawartości WPF](controls/wpf-content-model.md).</span><span class="sxs-lookup"><span data-stu-id="2e1b9-305">For more information on the kinds of content that is supported by various controls, see [WPF content model](controls/wpf-content-model.md).</span></span>

### <a name="triggers"></a><span data-ttu-id="2e1b9-306">Wyzwalacze</span><span class="sxs-lookup"><span data-stu-id="2e1b9-306">Triggers</span></span>

<span data-ttu-id="2e1b9-307">Chociaż głównym celem znaczników XAML jest zaimplementowanie wyglądu aplikacji, można również użyć XAML do zaimplementowania niektórych aspektów zachowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-307">Although the main purpose of XAML markup is to implement an application's appearance, you can also use XAML to implement some aspects of an application's behavior.</span></span> <span data-ttu-id="2e1b9-308">Jednym z przykładów jest użycie wyzwalaczy, aby zmienić wygląd aplikacji na podstawie interakcji użytkownika.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-308">One example is the use of triggers to change an application's appearance based on user interactions.</span></span> <span data-ttu-id="2e1b9-309">Aby uzyskać więcej informacji, zobacz [Style i szablony](../../desktop-wpf/fundamentals/styles-templates-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2e1b9-309">For more information, see [Styles and templates](../../desktop-wpf/fundamentals/styles-templates-overview.md).</span></span>

### <a name="control-templates"></a><span data-ttu-id="2e1b9-310">Szablony formantów</span><span class="sxs-lookup"><span data-stu-id="2e1b9-310">Control templates</span></span>

<span data-ttu-id="2e1b9-311">Domyślne interfejsy użytkownika dla formantów WPF są zazwyczaj konstruowane z innych formantów i kształtów.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-311">The default user interfaces for WPF controls are typically constructed from other controls and shapes.</span></span> <span data-ttu-id="2e1b9-312">Na przykład <xref:System.Windows.Controls.Button> a składa <xref:Microsoft.Windows.Themes.ButtonChrome> się <xref:System.Windows.Controls.ContentPresenter> z obu i formantów.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-312">For example, a <xref:System.Windows.Controls.Button> is composed of both <xref:Microsoft.Windows.Themes.ButtonChrome> and <xref:System.Windows.Controls.ContentPresenter> controls.</span></span> <span data-ttu-id="2e1b9-313">Zapewnia <xref:Microsoft.Windows.Themes.ButtonChrome> standardowy wygląd przycisku, podczas gdy <xref:System.Windows.Controls.ContentPresenter> wyświetla zawartość przycisku, zgodnie z określoną <xref:System.Windows.Controls.ContentControl.Content%2A> przez właściwość.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-313">The <xref:Microsoft.Windows.Themes.ButtonChrome> provides the standard button appearance, while the <xref:System.Windows.Controls.ContentPresenter> displays the button's content, as specified by the <xref:System.Windows.Controls.ContentControl.Content%2A> property.</span></span>

<span data-ttu-id="2e1b9-314">Czasami domyślny wygląd formantu może być niezgodny z ogólnym wyglądem aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-314">Sometimes the default appearance of a control may be incongruent with the overall appearance of an application.</span></span> <span data-ttu-id="2e1b9-315">W takim przypadku można <xref:System.Windows.Controls.ControlTemplate> użyć a, aby zmienić wygląd interfejsu użytkownika formantu bez zmiany jego zawartości i zachowania.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-315">In this case, you can use a <xref:System.Windows.Controls.ControlTemplate> to change the appearance of the control's user interface without changing its content and behavior.</span></span>

<span data-ttu-id="2e1b9-316">W poniższym przykładzie pokazano, <xref:System.Windows.Controls.Button> jak zmienić wygląd a za pomocą <xref:System.Windows.Controls.ControlTemplate>:</span><span class="sxs-lookup"><span data-stu-id="2e1b9-316">The following example shows how to change the appearance of a <xref:System.Windows.Controls.Button> by using a <xref:System.Windows.Controls.ControlTemplate>:</span></span>

[!code-xaml[IntroToWPFSnippets#ButtonControlTemplateWindowMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_16.xaml)]

[!code-csharp[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_17.cs)]
[!code-vb[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_17.vb)]

<span data-ttu-id="2e1b9-317">W tym przykładzie domyślny interfejs użytkownika <xref:System.Windows.Shapes.Ellipse> przycisku został zastąpiony, który ma <xref:System.Windows.Media.RadialGradientBrush>ciemnoniebieskie obramowanie i jest wypełniony za pomocą pliku .</span><span class="sxs-lookup"><span data-stu-id="2e1b9-317">In this example, the default button user interface has been replaced with an <xref:System.Windows.Shapes.Ellipse> that has a dark blue border and is filled using a <xref:System.Windows.Media.RadialGradientBrush>.</span></span> <span data-ttu-id="2e1b9-318">Formant <xref:System.Windows.Controls.ContentPresenter> wyświetla zawartość <xref:System.Windows.Controls.Button>przycisku "Kliknij mnie!"</span><span class="sxs-lookup"><span data-stu-id="2e1b9-318">The <xref:System.Windows.Controls.ContentPresenter> control displays the content of the <xref:System.Windows.Controls.Button>, "Click Me!"</span></span> <span data-ttu-id="2e1b9-319">Po <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Primitives.ButtonBase.Click> kliknięciu, zdarzenie jest nadal wywoływane <xref:System.Windows.Controls.Button> jako część domyślnego zachowania formantu.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-319">When the <xref:System.Windows.Controls.Button> is clicked, the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event is still raised as part of the <xref:System.Windows.Controls.Button> control's default behavior.</span></span> <span data-ttu-id="2e1b9-320">Wynik jest pokazany na poniższym rysunku:</span><span class="sxs-lookup"><span data-stu-id="2e1b9-320">The result is shown in the following figure:</span></span>

![Przycisk eliptyczny i drugie okno](media/introduction-to-wpf/wpfintrofigure2.png)

### <a name="data-templates"></a><span data-ttu-id="2e1b9-322">Szablony danych</span><span class="sxs-lookup"><span data-stu-id="2e1b9-322">Data templates</span></span>

<span data-ttu-id="2e1b9-323">Podczas gdy szablon formantu umożliwia określenie wyglądu formantu, szablon danych umożliwia określenie wyglądu zawartości formantu.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-323">Whereas a control template lets you specify the appearance of a control, a data template lets you specify the appearance of a control's content.</span></span> <span data-ttu-id="2e1b9-324">Szablony danych są często używane w celu zwiększenia sposobu wyświetlania danych powiązanych.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-324">Data templates are frequently used to enhance how bound data is displayed.</span></span> <span data-ttu-id="2e1b9-325">Na poniższej ilustracji przedstawiono domyślny <xref:System.Windows.Controls.ListBox> wygląd `Task` dla kolekcji obiektów, gdzie każde zadanie ma nazwę, opis i priorytet:</span><span class="sxs-lookup"><span data-stu-id="2e1b9-325">The following figure shows the default appearance for a <xref:System.Windows.Controls.ListBox> that is bound to a collection of `Task` objects, where each task has a name, description, and priority:</span></span>

![Pole listy z wyglądem domyślnym](media/introduction-to-wpf/wpfintrofigure18.png)

<span data-ttu-id="2e1b9-327">Domyślny wygląd jest to, <xref:System.Windows.Controls.ListBox>czego można oczekiwać od .</span><span class="sxs-lookup"><span data-stu-id="2e1b9-327">The default appearance is what you would expect from a <xref:System.Windows.Controls.ListBox>.</span></span> <span data-ttu-id="2e1b9-328">Jednak domyślny wygląd każdego zadania zawiera tylko nazwę zadania.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-328">However, the default appearance of each task contains only the task name.</span></span> <span data-ttu-id="2e1b9-329">Aby wyświetlić nazwę zadania, opis i priorytet, <xref:System.Windows.Controls.ListBox> domyślny wygląd elementów listy związanej formantu musi zostać zmieniony za pomocą pliku <xref:System.Windows.DataTemplate>.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-329">To show the task name, description, and priority, the default appearance of the <xref:System.Windows.Controls.ListBox> control's bound list items must be changed by using a <xref:System.Windows.DataTemplate>.</span></span> <span data-ttu-id="2e1b9-330">Następujący kod XAML definiuje <xref:System.Windows.DataTemplate>takie , które jest stosowane <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> do każdego zadania przy użyciu atrybutu:</span><span class="sxs-lookup"><span data-stu-id="2e1b9-330">The following XAML defines such a <xref:System.Windows.DataTemplate>, which is applied to each task by using the <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> attribute:</span></span>

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

<span data-ttu-id="2e1b9-331">Na poniższej ilustracji przedstawiono efekt tego kodu:</span><span class="sxs-lookup"><span data-stu-id="2e1b9-331">The following figure shows the effect of this code:</span></span>

![Pole listy z szablonem danych](media/introduction-to-wpf/wpfintrofigure19.png)

<span data-ttu-id="2e1b9-333">Należy zauważyć, że <xref:System.Windows.Controls.ListBox> zachował swoje zachowanie i ogólny wygląd; zmienił się tylko wygląd zawartości wyświetlanej w polu listy.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-333">Note that the <xref:System.Windows.Controls.ListBox> has retained its behavior and overall appearance; only the appearance of the content being displayed by the list box has changed.</span></span>

<span data-ttu-id="2e1b9-334">Aby uzyskać więcej informacji, zobacz [Omówienie tworzenia szablonów danych](data/data-templating-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2e1b9-334">For more information, see [Data templating overview](data/data-templating-overview.md).</span></span>

### <a name="styles"></a><span data-ttu-id="2e1b9-335">Style</span><span class="sxs-lookup"><span data-stu-id="2e1b9-335">Styles</span></span>

<span data-ttu-id="2e1b9-336">Style umożliwiają deweloperom i projektantom standaryzację określonego wyglądu dla ich produktu.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-336">Styles enable developers and designers to standardize on a particular appearance for their product.</span></span> <span data-ttu-id="2e1b9-337">WPF WPF zapewnia model silnego stylu, <xref:System.Windows.Style> którego podstawą jest element.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-337">WPF provides a strong style model, the foundation of which is the <xref:System.Windows.Style> element.</span></span> <span data-ttu-id="2e1b9-338">Poniższy przykład tworzy styl, który ustawia <xref:System.Windows.Controls.Button> kolor tła dla każdego okna na: `Orange`</span><span class="sxs-lookup"><span data-stu-id="2e1b9-338">The following example creates a style that sets the background color for every <xref:System.Windows.Controls.Button> on a window to `Orange`:</span></span>

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

<span data-ttu-id="2e1b9-339">Ponieważ ten styl <xref:System.Windows.Controls.Button> jest przeznaczony dla wszystkich formantów, styl jest automatycznie stosowany do wszystkich przycisków w oknie, jak pokazano na poniższym rysunku:</span><span class="sxs-lookup"><span data-stu-id="2e1b9-339">Because this style targets all <xref:System.Windows.Controls.Button> controls, the style is automatically applied to all the buttons in the window, as shown in the following figure:</span></span>

![Dwa pomarańczowe przyciski](media/introduction-to-wpf/wpfintrofigure20.png)

<span data-ttu-id="2e1b9-341">Aby uzyskać więcej informacji, zobacz [Style i szablony](../../desktop-wpf/fundamentals/styles-templates-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2e1b9-341">For more information, see [Styles and templates](../../desktop-wpf/fundamentals/styles-templates-overview.md).</span></span>

### <a name="resources"></a><span data-ttu-id="2e1b9-342">Zasoby</span><span class="sxs-lookup"><span data-stu-id="2e1b9-342">Resources</span></span>

<span data-ttu-id="2e1b9-343">Formanty w aplikacji powinny mieć ten sam wygląd, który może zawierać wszystko, od czcionek i kolorów tła do sterowania szablonami, szablonami danych i stylami.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-343">Controls in an application should share the same appearance, which can include anything from fonts and background colors to control templates, data templates, and styles.</span></span> <span data-ttu-id="2e1b9-344">Można użyć obsługi WPF dla zasobów interfejsu użytkownika do hermetyzacji tych zasobów w jednej lokalizacji do ponownego użycia.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-344">You can use WPF's support for user interface resources to encapsulate these resources in a single location for reuse.</span></span>

<span data-ttu-id="2e1b9-345">Poniższy przykład definiuje wspólny kolor tła, <xref:System.Windows.Controls.Button> który <xref:System.Windows.Controls.Label>jest współużytkowane przez a i a:</span><span class="sxs-lookup"><span data-stu-id="2e1b9-345">The following example defines a common background color that is shared by a <xref:System.Windows.Controls.Button> and a <xref:System.Windows.Controls.Label>:</span></span>

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

<span data-ttu-id="2e1b9-346">W tym przykładzie implementuje zasób koloru tła przy użyciu elementu `Window.Resources` właściwości.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-346">This example implements a background color resource by using the `Window.Resources` property element.</span></span> <span data-ttu-id="2e1b9-347">Ten zasób jest dostępny <xref:System.Windows.Window>dla wszystkich dzieni .</span><span class="sxs-lookup"><span data-stu-id="2e1b9-347">This resource is available to all children of the <xref:System.Windows.Window>.</span></span> <span data-ttu-id="2e1b9-348">Istnieje wiele zakresów zasobów, w tym następujące, wymienione w kolejności, w jakiej są one rozwiązywane:</span><span class="sxs-lookup"><span data-stu-id="2e1b9-348">There are a variety of resource scopes, including the following, listed in the order in which they are resolved:</span></span>

1. <span data-ttu-id="2e1b9-349">Indywidualny formant (przy <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> użyciu właściwości dziedziczonej).</span><span class="sxs-lookup"><span data-stu-id="2e1b9-349">An individual control (using the inherited <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> property).</span></span>

2. <span data-ttu-id="2e1b9-350">A <xref:System.Windows.Window> lub <xref:System.Windows.Controls.Page> a (również <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> przy użyciu właściwości dziedziczonej).</span><span class="sxs-lookup"><span data-stu-id="2e1b9-350">A <xref:System.Windows.Window> or a <xref:System.Windows.Controls.Page> (also using the inherited <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> property).</span></span>

3. <span data-ttu-id="2e1b9-351">An <xref:System.Windows.Application> (przy <xref:System.Windows.Application.Resources%2A?displayProperty=fullName> użyciu właściwości).</span><span class="sxs-lookup"><span data-stu-id="2e1b9-351">An <xref:System.Windows.Application> (using the <xref:System.Windows.Application.Resources%2A?displayProperty=fullName> property).</span></span>

<span data-ttu-id="2e1b9-352">Różnorodność zakresów zapewnia elastyczność w odniesieniu do sposobu definiowania i udostępniania zasobów.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-352">The variety of scopes gives you flexibility with respect to the way in which you define and share your resources.</span></span>

<span data-ttu-id="2e1b9-353">Jako alternatywę dla bezpośredniego kojarzenia zasobów z określonym zakresem, można spakować <xref:System.Windows.ResourceDictionary> jeden lub więcej zasobów przy użyciu oddzielnego, do którego można się odwoływać w innych częściach aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-353">As an alternative to directly associating your resources with a particular scope, you can package one or more resources by using a separate <xref:System.Windows.ResourceDictionary> that can be referenced in other parts of an application.</span></span> <span data-ttu-id="2e1b9-354">Na przykład w poniższym przykładzie zdefiniowano domyślny kolor tła w słowniku zasobów:</span><span class="sxs-lookup"><span data-stu-id="2e1b9-354">For example, the following example defines a default background color in a resource dictionary:</span></span>

```xaml
<ResourceDictionary
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">

  <!-- Define background color resource -->
  <SolidColorBrush x:Key="defaultBackground" Color="Red" />

  <!-- Define other resources -->
</ResourceDictionary>
```

<span data-ttu-id="2e1b9-355">Poniższy przykład odwołuje się do słownika zasobów zdefiniowanego w poprzednim przykładzie, tak aby był współużytkowany przez aplikację:</span><span class="sxs-lookup"><span data-stu-id="2e1b9-355">The following example references the resource dictionary defined in the previous example so that it is shared across an application:</span></span>

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

<span data-ttu-id="2e1b9-356">Zasoby i słowniki zasobów są podstawą obsługi WPF dla tematów i karnacji.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-356">Resources and resource dictionaries are the foundation of WPF support for themes and skins.</span></span>

<span data-ttu-id="2e1b9-357">Aby uzyskać więcej informacji, zobacz [Zasoby](../../desktop-wpf/fundamentals/xaml-resources-define.md).</span><span class="sxs-lookup"><span data-stu-id="2e1b9-357">For more information, see [Resources](../../desktop-wpf/fundamentals/xaml-resources-define.md).</span></span>

### <a name="custom-controls"></a><span data-ttu-id="2e1b9-358">Kontrolki niestandardowe</span><span class="sxs-lookup"><span data-stu-id="2e1b9-358">Custom controls</span></span>

<span data-ttu-id="2e1b9-359">Mimo że WPF zapewnia wiele obsługi dostosowywania, mogą wystąpić sytuacje, w których istniejące formanty WPF nie spełniają potrzeb aplikacji lub jej użytkowników.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-359">Although WPF provides a host of customization support, you may encounter situations where existing WPF controls do not meet the needs of either your application or its users.</span></span> <span data-ttu-id="2e1b9-360">Może to nastąpić, gdy:</span><span class="sxs-lookup"><span data-stu-id="2e1b9-360">This can occur when:</span></span>

- <span data-ttu-id="2e1b9-361">Interfejs użytkownika, który jest wymagany nie można utworzyć przez dostosowanie wygląd i działanie istniejących implementacji WPF.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-361">The user interface that you require cannot be created by customizing the look and feel of existing WPF implementations.</span></span>

- <span data-ttu-id="2e1b9-362">Zachowanie, które są wymagane nie jest obsługiwane (lub nie łatwo obsługiwane) przez istniejące implementacje WPF.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-362">The behavior that you require is not supported (or not easily supported) by existing WPF implementations.</span></span>

<span data-ttu-id="2e1b9-363">W tym momencie można jednak skorzystać z jednego z trzech modeli WPF, aby utworzyć nowy formant.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-363">At this point, however, you can take advantage of one of three WPF models to create a new control.</span></span> <span data-ttu-id="2e1b9-364">Każdy model jest przeznaczony dla określonego scenariusza i wymaga formantu niestandardowego, aby pochodzić z określonej klasy podstawowej WPF.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-364">Each model targets a specific scenario and requires your custom control to derive from a particular WPF base class.</span></span> <span data-ttu-id="2e1b9-365">Trzy modele są wymienione tutaj:</span><span class="sxs-lookup"><span data-stu-id="2e1b9-365">The three models are listed here:</span></span>

- <span data-ttu-id="2e1b9-366">**Model sterowania użytkownikiem**.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-366">**User Control Model**.</span></span> <span data-ttu-id="2e1b9-367">Formant niestandardowy <xref:System.Windows.Controls.UserControl> pochodzi z i składa się z jednego lub więcej innych formantów.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-367">A custom control derives from <xref:System.Windows.Controls.UserControl> and is composed of one or more other controls.</span></span>

- <span data-ttu-id="2e1b9-368">**Model sterowania**.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-368">**Control Model**.</span></span> <span data-ttu-id="2e1b9-369">Formant niestandardowy <xref:System.Windows.Controls.Control> pochodzi z i jest używany do tworzenia implementacji, które oddzielają ich zachowanie od ich wygląd przy użyciu szablonów, podobnie jak większość formantów WPF.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-369">A custom control derives from <xref:System.Windows.Controls.Control> and is used to build implementations that separate their behavior from their appearance using templates, much like the majority of WPF controls.</span></span> <span data-ttu-id="2e1b9-370">Wyprowadzenie z <xref:System.Windows.Controls.Control> pozwala na większą swobodę tworzenia niestandardowego interfejsu użytkownika niż formanty użytkownika, ale może wymagać więcej wysiłku.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-370">Deriving from <xref:System.Windows.Controls.Control> allows you more freedom for creating a custom user interface than user controls, but it may require more effort.</span></span>

- <span data-ttu-id="2e1b9-371">**Model elementu framework .**</span><span class="sxs-lookup"><span data-stu-id="2e1b9-371">**Framework Element Model**.</span></span> <span data-ttu-id="2e1b9-372">Formant niestandardowy <xref:System.Windows.FrameworkElement> wywodzi się z tego, kiedy jego wygląd jest zdefiniowany przez niestandardową logikę renderowania (nie szablony).</span><span class="sxs-lookup"><span data-stu-id="2e1b9-372">A custom control derives from <xref:System.Windows.FrameworkElement> when its appearance is defined by custom rendering logic (not templates).</span></span>

<span data-ttu-id="2e1b9-373">W poniższym przykładzie pokazano niestandardową kontrolkę <xref:System.Windows.Controls.UserControl>numeryczną w górę/w dół, która wywodzi się z:</span><span class="sxs-lookup"><span data-stu-id="2e1b9-373">The following example shows a custom numeric up/down control that derives from <xref:System.Windows.Controls.UserControl>:</span></span>

[!code-xaml[IntroToWPFSnippets#UserControlMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_33.xaml)]

[!code-csharp[IntroToWPFSnippets#UserControlCODEBEHIND1](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_34.cs)]
[!code-vb[IntroToWPFSnippets#UserControlCODEBEHIND1](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_34.vb)]

<span data-ttu-id="2e1b9-374">Poniższy przykład ilustruje kod XAML, który jest wymagany <xref:System.Windows.Window>do włączenia formantu użytkownika do:</span><span class="sxs-lookup"><span data-stu-id="2e1b9-374">The following example illustrates the XAML that is required to incorporate the user control into a <xref:System.Windows.Window>:</span></span>

[!code-xaml[IntroToWPFSnippets#UserControlWindowMARKUP1](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_37.xaml)]

<span data-ttu-id="2e1b9-375">Na poniższej `NumericUpDown` ilustracji przedstawiono <xref:System.Windows.Window>formant hostowany w:</span><span class="sxs-lookup"><span data-stu-id="2e1b9-375">The following figure shows the `NumericUpDown` control hosted in a <xref:System.Windows.Window>:</span></span>

![Niestandardowa kontrola użytkownika](media/introduction-to-wpf/wpfintrofigure3.png)

<span data-ttu-id="2e1b9-377">Aby uzyskać więcej informacji na temat formantów niestandardowych, zobacz [Omówienie tworzenia formantu .](controls/control-authoring-overview.md)</span><span class="sxs-lookup"><span data-stu-id="2e1b9-377">For more information on custom controls, see [Control authoring overview](controls/control-authoring-overview.md).</span></span>

## <a name="wpf-best-practices"></a><span data-ttu-id="2e1b9-378">Najlepsze rozwiązania WPF</span><span class="sxs-lookup"><span data-stu-id="2e1b9-378">WPF best practices</span></span>

<span data-ttu-id="2e1b9-379">Podobnie jak w przypadku każdej platformy programistycznej, WPF WPF może służyć na wiele sposobów, aby osiągnąć pożądany wynik.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-379">As with any development platform, WPF can be used in a variety of ways to achieve the desired result.</span></span> <span data-ttu-id="2e1b9-380">W celu zapewnienia, że aplikacje WPF zapewniają wymagane środowisko użytkownika i spełniają wymagania odbiorców w ogóle, istnieją zalecane najlepsze rozwiązania dotyczące dostępności, globalizacji i lokalizacji i wydajności.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-380">As a way of ensuring that your WPF applications provide the required user experience and meet the demands of the audience in general, there are recommended best practices for accessibility, globalization and localization, and performance.</span></span> <span data-ttu-id="2e1b9-381">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="2e1b9-381">For more information, see:</span></span>

- [<span data-ttu-id="2e1b9-382">Ułatwienia dostępu</span><span class="sxs-lookup"><span data-stu-id="2e1b9-382">Accessibility</span></span>](../ui-automation/accessibility-best-practices.md)
- [<span data-ttu-id="2e1b9-383">Globalizacja i lokalizacja WPF</span><span class="sxs-lookup"><span data-stu-id="2e1b9-383">WPF globalization and localization</span></span>](advanced/wpf-globalization-and-localization-overview.md)
- [<span data-ttu-id="2e1b9-384">Wydajność aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="2e1b9-384">WPF app performance</span></span>](advanced/optimizing-wpf-application-performance.md)
- [<span data-ttu-id="2e1b9-385">Zabezpieczenia WPF</span><span class="sxs-lookup"><span data-stu-id="2e1b9-385">WPF security</span></span>](security-wpf.md)

## <a name="next-steps"></a><span data-ttu-id="2e1b9-386">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="2e1b9-386">Next steps</span></span>

<span data-ttu-id="2e1b9-387">Przyjrzeliśmy się kluczowym cechom WPF.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-387">We've looked at the key features of WPF.</span></span> <span data-ttu-id="2e1b9-388">Teraz nadszedł czas, aby zbudować swoją pierwszą aplikację WPF.</span><span class="sxs-lookup"><span data-stu-id="2e1b9-388">Now it's time to build your first WPF app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2e1b9-389">Instruktaż: Moja pierwsza aplikacja komputerowa WPF</span><span class="sxs-lookup"><span data-stu-id="2e1b9-389">Walkthrough: My first WPF desktop app</span></span>](getting-started/walkthrough-my-first-wpf-desktop-application.md)

## <a name="see-also"></a><span data-ttu-id="2e1b9-390">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2e1b9-390">See also</span></span>

- [<span data-ttu-id="2e1b9-391">Rozpoczynanie pracy z aparatem WPF</span><span class="sxs-lookup"><span data-stu-id="2e1b9-391">Get started with WPF</span></span>](getting-started/index.md)
- [<span data-ttu-id="2e1b9-392">Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="2e1b9-392">Windows Presentation Foundation</span></span>](index.md)
- [<span data-ttu-id="2e1b9-393">Zasoby społeczności WPF</span><span class="sxs-lookup"><span data-stu-id="2e1b9-393">WPF community resources</span></span>](getting-started/community-feedback.md)
