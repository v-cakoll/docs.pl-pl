---
title: Wprowadzenie do WPF
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b8d7cf43-d1f2-4f3d-adb0-4f3a6428edc0
dev_langs:
- csharp
- vb
ms.openlocfilehash: ecdd3b3c24b71917efb0d982d1f23737673622f9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744711"
---
# <a name="wpf-overview"></a><span data-ttu-id="5d07c-102">Omówienie podsystemu WPF</span><span class="sxs-lookup"><span data-stu-id="5d07c-102">WPF overview</span></span>

<span data-ttu-id="5d07c-103">Windows Presentation Foundation (WPF) umożliwia tworzenie aplikacji klienckich dla komputerów z systemem Windows przy użyciu wizualnie atrakcyjnych środowisk użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5d07c-103">Windows Presentation Foundation (WPF) lets you create desktop client applications for Windows with visually stunning user experiences.</span></span>

![Przykład interfejsu użytkownika dla opieki zdrowotnej firmy Contoso](media/introduction-to-wpf/wpfintrofigure24.png)

<span data-ttu-id="5d07c-105">Rdzeń WPF to mechanizm renderowania niezależny od rozdzielczości i oparty na wektorach, który jest zbudowany w celu wykorzystania nowoczesnego sprzętu graficznego.</span><span class="sxs-lookup"><span data-stu-id="5d07c-105">The core of WPF is a resolution-independent and vector-based rendering engine that is built to take advantage of modern graphics hardware.</span></span> <span data-ttu-id="5d07c-106">WPF rozszerza rdzeń z kompleksowym zestawem funkcji programistycznych dla aplikacji, które obejmują Extensible Application Markup Language (XAML), kontrolki, powiązanie danych, układ, grafiki 2D i 3D, animacje, style, szablony, dokumenty, multimedia, tekst i typografii.</span><span class="sxs-lookup"><span data-stu-id="5d07c-106">WPF extends the core with a comprehensive set of application-development features that include Extensible Application Markup Language (XAML), controls, data binding, layout, 2D and 3D graphics, animation, styles, templates, documents, media, text, and typography.</span></span> <span data-ttu-id="5d07c-107">WPF jest częścią platformy .NET, dzięki czemu można tworzyć aplikacje, które zawierają inne elementy interfejsu API platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="5d07c-107">WPF is part of .NET, so you can build applications that incorporate other elements of the .NET API.</span></span>

<span data-ttu-id="5d07c-108">Ten przegląd jest przeznaczony dla nowych elementów i obejmuje kluczowe możliwości i koncepcje WPF.</span><span class="sxs-lookup"><span data-stu-id="5d07c-108">This overview is intended for newcomers and covers the key capabilities and concepts of WPF.</span></span>

## <a name="program-with-wpf"></a><span data-ttu-id="5d07c-109">Program z WPF</span><span class="sxs-lookup"><span data-stu-id="5d07c-109">Program with WPF</span></span>

<span data-ttu-id="5d07c-110">WPF istnieje jako podzbiór typów .NET, które są (w większości części) znajdujących się w przestrzeni nazw <xref:System.Windows>.</span><span class="sxs-lookup"><span data-stu-id="5d07c-110">WPF exists as a subset of .NET types that are (for the most part) located in the <xref:System.Windows> namespace.</span></span> <span data-ttu-id="5d07c-111">Jeśli wcześniej skompilowano aplikacje z platformą .NET przy użyciu technologii zarządzanych, takich jak ASP.NET i Windows Forms, podstawowe środowisko programistyczne WPF powinno być znane. Tworzenie wystąpień klas, Ustawianie właściwości, metody wywoływania i obsługa zdarzeń przy użyciu ulubionego języka programowania .NET, takiego jak C# lub Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5d07c-111">If you have previously built applications with .NET using managed technologies like ASP.NET and Windows Forms, the fundamental WPF programming experience should be familiar; you instantiate classes, set properties, call methods, and handle events, using your favorite .NET programming language, such as C# or Visual Basic.</span></span>

<span data-ttu-id="5d07c-112">WPF zawiera dodatkowe konstrukcje programistyczne, które rozszerzają właściwości i zdarzenia: [właściwości zależności](advanced/dependency-properties-overview.md) i [zdarzenia kierowane](advanced/routed-events-overview.md).</span><span class="sxs-lookup"><span data-stu-id="5d07c-112">WPF includes additional programming constructs that enhance properties and events: [dependency properties](advanced/dependency-properties-overview.md) and [routed events](advanced/routed-events-overview.md).</span></span>

## <a name="markup-and-code-behind"></a><span data-ttu-id="5d07c-113">Znaczniki i kod w tle</span><span class="sxs-lookup"><span data-stu-id="5d07c-113">Markup and code-behind</span></span>

<span data-ttu-id="5d07c-114">WPF umożliwia tworzenie aplikacji przy użyciu zarówno *znaczników* , jak i *kodu*, dzięki czemu deweloperzy ASP.NET powinni znać.</span><span class="sxs-lookup"><span data-stu-id="5d07c-114">WPF lets you develop an application using both *markup* and *code-behind*, an experience with which ASP.NET developers should be familiar.</span></span> <span data-ttu-id="5d07c-115">Zwykle używasz znacznika XAML do zaimplementowania wyglądu aplikacji przy użyciu zarządzanych języków programowania (związanych z kodem), aby zaimplementować jego zachowanie.</span><span class="sxs-lookup"><span data-stu-id="5d07c-115">You generally use XAML markup to implement the appearance of an application while using managed programming languages (code-behind) to implement its behavior.</span></span> <span data-ttu-id="5d07c-116">Takie rozdzielenie wyglądu i zachowania ma następujące zalety:</span><span class="sxs-lookup"><span data-stu-id="5d07c-116">This separation of appearance and behavior has the following benefits:</span></span>

- <span data-ttu-id="5d07c-117">Koszty związane z programowaniem i konserwacją są ograniczone, ponieważ znaczniki specyficzne dla wyglądu nie są ściśle powiązane z kodem specyficznym dla zachowania.</span><span class="sxs-lookup"><span data-stu-id="5d07c-117">Development and maintenance costs are reduced because appearance-specific markup is not tightly coupled with behavior-specific code.</span></span>

- <span data-ttu-id="5d07c-118">Programowanie jest wydajniejsze, ponieważ projektanci mogą zaimplementować wygląd aplikacji jednocześnie dla deweloperów, którzy implementują zachowanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5d07c-118">Development is more efficient because designers can implement an application's appearance simultaneously with developers who are implementing the application's behavior.</span></span>

- <span data-ttu-id="5d07c-119">[Globalizacja i lokalizacja](advanced/wpf-globalization-and-localization-overview.md) dla aplikacji WPF jest uproszczona.</span><span class="sxs-lookup"><span data-stu-id="5d07c-119">[Globalization and localization](advanced/wpf-globalization-and-localization-overview.md) for WPF applications is simplified.</span></span>

### <a name="markup"></a><span data-ttu-id="5d07c-120">Komórka</span><span class="sxs-lookup"><span data-stu-id="5d07c-120">Markup</span></span>

<span data-ttu-id="5d07c-121">XAML jest językiem znaczników opartym na języku XML, który implementuje wygląd aplikacji deklaratywnie.</span><span class="sxs-lookup"><span data-stu-id="5d07c-121">XAML is an XML-based markup language that implements an application's appearance declaratively.</span></span> <span data-ttu-id="5d07c-122">Zwykle jest ona używana do tworzenia okien, okien dialogowych, stron i kontrolek użytkownika oraz do wypełniania formantów, kształtów i grafiki.</span><span class="sxs-lookup"><span data-stu-id="5d07c-122">You typically use it to create windows, dialog boxes, pages, and user controls, and to fill them with controls, shapes, and graphics.</span></span>

<span data-ttu-id="5d07c-123">Poniższy przykład używa języka XAML do zaimplementowania wyglądu okna zawierającego pojedynczy przycisk:</span><span class="sxs-lookup"><span data-stu-id="5d07c-123">The following example uses XAML to implement the appearance of a window that contains a single button:</span></span>

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    Title="Window with Button"
    Width="250" Height="100">

  <!-- Add button to window -->
  <Button Name="button">Click Me!</Button>

</Window>
```

<span data-ttu-id="5d07c-124">W każdym przypadku ten kod XAML definiuje okno i przycisk przy użyciu odpowiednio elementów `Window` i `Button`.</span><span class="sxs-lookup"><span data-stu-id="5d07c-124">Specifically, this XAML defines a window and a button by using the `Window` and `Button` elements, respectively.</span></span> <span data-ttu-id="5d07c-125">Każdy element jest skonfigurowany z atrybutami, takimi jak atrybut `Title` elementu `Window`, aby określić tekst paska tytułu okna.</span><span class="sxs-lookup"><span data-stu-id="5d07c-125">Each element is configured with attributes, such as the `Window` element's `Title` attribute to specify the window's title-bar text.</span></span> <span data-ttu-id="5d07c-126">W czasie wykonywania WPF konwertuje elementy i atrybuty, które są zdefiniowane w znacznikach do wystąpień klas WPF.</span><span class="sxs-lookup"><span data-stu-id="5d07c-126">At run time, WPF converts the elements and attributes that are defined in markup to instances of WPF classes.</span></span> <span data-ttu-id="5d07c-127">Na przykład element `Window` jest konwertowany na wystąpienie klasy <xref:System.Windows.Window>, której Właściwość <xref:System.Windows.Window.Title%2A> jest wartością atrybutu `Title`.</span><span class="sxs-lookup"><span data-stu-id="5d07c-127">For example, the `Window` element is converted to an instance of the <xref:System.Windows.Window> class whose <xref:System.Windows.Window.Title%2A> property is the value of the `Title` attribute.</span></span>

<span data-ttu-id="5d07c-128">Na poniższej ilustracji przedstawiono interfejs użytkownika, który jest definiowany przez kod XAML w poprzednim przykładzie:</span><span class="sxs-lookup"><span data-stu-id="5d07c-128">The following figure shows the user interface (UI) that is defined by the XAML in the previous example:</span></span>

![Okno zawierające przycisk](media/introduction-to-wpf/wpfintrofigure10.png)

<span data-ttu-id="5d07c-130">Ponieważ XAML jest oparty na języku XML, tworzony przez siebie interfejs użytkownika jest montowany w hierarchii elementów zagnieżdżonych znanych jako [drzewo elementów](advanced/trees-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="5d07c-130">Since XAML is XML-based, the UI that you compose with it is assembled in a hierarchy of nested elements known as an [element tree](advanced/trees-in-wpf.md).</span></span> <span data-ttu-id="5d07c-131">Drzewo elementu zawiera logiczny i intuicyjny sposób tworzenia interfejsów użytkownika i zarządzania nimi.</span><span class="sxs-lookup"><span data-stu-id="5d07c-131">The element tree provides a logical and intuitive way to create and manage UIs.</span></span>

### <a name="code-behind"></a><span data-ttu-id="5d07c-132">Związane z kodem</span><span class="sxs-lookup"><span data-stu-id="5d07c-132">Code-behind</span></span>

<span data-ttu-id="5d07c-133">Głównym zachowaniem aplikacji jest zaimplementowanie funkcji, która reaguje na interakcje użytkowników, w tym obsługę zdarzeń (na przykład kliknięcie menu, paska narzędzi lub przycisku) i wywołanie logiki biznesowej i logiki dostępu do danych w odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="5d07c-133">The main behavior of an application is to implement the functionality that responds to user interactions, including handling events (for example, clicking a menu, tool bar, or button) and calling business logic and data access logic in response.</span></span> <span data-ttu-id="5d07c-134">W WPF to zachowanie jest zaimplementowane w kodzie, który jest skojarzony ze znacznikiem.</span><span class="sxs-lookup"><span data-stu-id="5d07c-134">In WPF, this behavior is implemented in code that is associated with markup.</span></span> <span data-ttu-id="5d07c-135">Ten typ kodu jest znany jako kod.</span><span class="sxs-lookup"><span data-stu-id="5d07c-135">This type of code is known as code-behind.</span></span> <span data-ttu-id="5d07c-136">Poniższy przykład pokazuje zaktualizowany znacznik z poprzedniego przykładu i powiązane z nim kod:</span><span class="sxs-lookup"><span data-stu-id="5d07c-136">The following example shows the updated markup from the previous example and the code-behind:</span></span>

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

<span data-ttu-id="5d07c-137">W tym przykładzie w kodzie jest implementowana Klasa, która dziedziczy z klasy <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="5d07c-137">In this example, the code-behind implements a class that derives from the <xref:System.Windows.Window> class.</span></span> <span data-ttu-id="5d07c-138">Atrybut `x:Class` jest używany do kojarzenia znaczników z klasą związaną z kodem.</span><span class="sxs-lookup"><span data-stu-id="5d07c-138">The `x:Class` attribute is used to associate the markup with the code-behind class.</span></span> <span data-ttu-id="5d07c-139">`InitializeComponent` jest wywoływana z konstruktora klasy związanej z kodem, aby scalić interfejs użytkownika, który jest zdefiniowany w adjustacji z klasą powiązanymi z kodem.</span><span class="sxs-lookup"><span data-stu-id="5d07c-139">`InitializeComponent` is called from the code-behind class's constructor to merge the UI that is defined in markup with the code-behind class.</span></span> <span data-ttu-id="5d07c-140">(`InitializeComponent` jest generowany podczas kompilowania aplikacji, co oznacza, że nie trzeba wdrażać jej ręcznie). Kombinacja `x:Class` i `InitializeComponent` upewnij się, że implementacja została prawidłowo zainicjowana za każdym razem, gdy zostanie utworzona.</span><span class="sxs-lookup"><span data-stu-id="5d07c-140">(`InitializeComponent` is generated for you when your application is built, which is why you don't need to implement it manually.) The combination of `x:Class` and `InitializeComponent` ensure that your implementation is correctly initialized whenever it is created.</span></span> <span data-ttu-id="5d07c-141">Klasa związany z kodem również implementuje procedurę obsługi zdarzeń dla zdarzenia <xref:System.Windows.Controls.Primitives.ButtonBase.Click> przycisku.</span><span class="sxs-lookup"><span data-stu-id="5d07c-141">The code-behind class also implements an event handler for the button's <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event.</span></span> <span data-ttu-id="5d07c-142">Gdy przycisk zostanie kliknięty, program obsługi zdarzeń wyświetli okno komunikatu, wywołując metodę <xref:System.Windows.MessageBox.Show%2A?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="5d07c-142">When the button is clicked, the event handler shows a message box by calling the <xref:System.Windows.MessageBox.Show%2A?displayProperty=fullName> method.</span></span>

<span data-ttu-id="5d07c-143">Poniższy rysunek przedstawia wynik po kliknięciu przycisku:</span><span class="sxs-lookup"><span data-stu-id="5d07c-143">The following figure shows the result when the button is clicked:</span></span>

![Element MessageBox](media/introduction-to-wpf/wpfintrofigure25.png)

## <a name="controls"></a><span data-ttu-id="5d07c-145">Formanty</span><span class="sxs-lookup"><span data-stu-id="5d07c-145">Controls</span></span>

<span data-ttu-id="5d07c-146">Środowiska użytkownika, które są dostarczane przez model aplikacji, są konstruowanymi kontrolkami.</span><span class="sxs-lookup"><span data-stu-id="5d07c-146">The user experiences that are delivered by the application model are constructed controls.</span></span> <span data-ttu-id="5d07c-147">W WPF *Kontrola* jest terminem parasol, który ma zastosowanie do kategorii klas WPF, które są hostowane w oknie lub na stronie, mają interfejs użytkownika i implementuje pewne zachowanie.</span><span class="sxs-lookup"><span data-stu-id="5d07c-147">In WPF, *control* is an umbrella term that applies to a category of WPF classes that are hosted in either a window or a page, have a user interface, and implement some behavior.</span></span>

<span data-ttu-id="5d07c-148">Aby uzyskać więcej informacji, zobacz [Controls](controls/index.md).</span><span class="sxs-lookup"><span data-stu-id="5d07c-148">For more information, see [Controls](controls/index.md).</span></span>

### <a name="wpf-controls-by-function"></a><span data-ttu-id="5d07c-149">Formanty WPF według funkcji</span><span class="sxs-lookup"><span data-stu-id="5d07c-149">WPF controls by function</span></span>

<span data-ttu-id="5d07c-150">Wbudowane formanty WPF są wymienione tutaj:</span><span class="sxs-lookup"><span data-stu-id="5d07c-150">The built-in WPF controls are listed here:</span></span>

- <span data-ttu-id="5d07c-151">**Przyciski**: <xref:System.Windows.Controls.Button> i <xref:System.Windows.Controls.Primitives.RepeatButton>.</span><span class="sxs-lookup"><span data-stu-id="5d07c-151">**Buttons**: <xref:System.Windows.Controls.Button> and <xref:System.Windows.Controls.Primitives.RepeatButton>.</span></span>

- <span data-ttu-id="5d07c-152">**Wyświetlanie danych**: <xref:System.Windows.Controls.DataGrid>, <xref:System.Windows.Controls.ListView>i <xref:System.Windows.Controls.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="5d07c-152">**Data Display**: <xref:System.Windows.Controls.DataGrid>, <xref:System.Windows.Controls.ListView>, and <xref:System.Windows.Controls.TreeView>.</span></span>

- <span data-ttu-id="5d07c-153">**Wyświetlanie i wybór daty**: <xref:System.Windows.Controls.Calendar> i <xref:System.Windows.Controls.DatePicker>.</span><span class="sxs-lookup"><span data-stu-id="5d07c-153">**Date Display and Selection**: <xref:System.Windows.Controls.Calendar> and <xref:System.Windows.Controls.DatePicker>.</span></span>

- <span data-ttu-id="5d07c-154">**Okna dialogowe**: <xref:Microsoft.Win32.OpenFileDialog>, <xref:System.Windows.Controls.PrintDialog>i <xref:Microsoft.Win32.SaveFileDialog>.</span><span class="sxs-lookup"><span data-stu-id="5d07c-154">**Dialog Boxes**: <xref:Microsoft.Win32.OpenFileDialog>, <xref:System.Windows.Controls.PrintDialog>, and <xref:Microsoft.Win32.SaveFileDialog>.</span></span>

- <span data-ttu-id="5d07c-155">**Cyfrowy atrament**: <xref:System.Windows.Controls.InkCanvas> i <xref:System.Windows.Controls.InkPresenter>.</span><span class="sxs-lookup"><span data-stu-id="5d07c-155">**Digital Ink**: <xref:System.Windows.Controls.InkCanvas> and <xref:System.Windows.Controls.InkPresenter>.</span></span>

- <span data-ttu-id="5d07c-156">**Dokumenty**: <xref:System.Windows.Controls.DocumentViewer>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentScrollViewer>i <xref:System.Windows.Controls.StickyNoteControl>.</span><span class="sxs-lookup"><span data-stu-id="5d07c-156">**Documents**: <xref:System.Windows.Controls.DocumentViewer>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentScrollViewer>, and <xref:System.Windows.Controls.StickyNoteControl>.</span></span>

- <span data-ttu-id="5d07c-157">**Dane wejściowe**: <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.RichTextBox>i <xref:System.Windows.Controls.PasswordBox>.</span><span class="sxs-lookup"><span data-stu-id="5d07c-157">**Input**: <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.RichTextBox>, and <xref:System.Windows.Controls.PasswordBox>.</span></span>

- <span data-ttu-id="5d07c-158">**Układ**: <xref:System.Windows.Controls.Border>, <xref:System.Windows.Controls.Primitives.BulletDecorator>, <xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Expander>, <xref:System.Windows.Controls.Grid>, <xref:System.Windows.Controls.GridView>, <xref:System.Windows.Controls.GridSplitter>, <xref:System.Windows.Controls.GroupBox>, <xref:System.Windows.Controls.Panel>, <xref:System.Windows.Controls.Primitives.ResizeGrip>, <xref:System.Windows.Controls.Separator>, <xref:System.Windows.Controls.Primitives.ScrollBar>, <xref:System.Windows.Controls.ScrollViewer>, <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.Primitives.Thumb>, <xref:System.Windows.Controls.Viewbox>, <xref:System.Windows.Controls.VirtualizingStackPanel>, <xref:System.Windows.Window>i <xref:System.Windows.Controls.WrapPanel>.</span><span class="sxs-lookup"><span data-stu-id="5d07c-158">**Layout**: <xref:System.Windows.Controls.Border>, <xref:System.Windows.Controls.Primitives.BulletDecorator>, <xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Expander>, <xref:System.Windows.Controls.Grid>, <xref:System.Windows.Controls.GridView>, <xref:System.Windows.Controls.GridSplitter>, <xref:System.Windows.Controls.GroupBox>, <xref:System.Windows.Controls.Panel>, <xref:System.Windows.Controls.Primitives.ResizeGrip>, <xref:System.Windows.Controls.Separator>, <xref:System.Windows.Controls.Primitives.ScrollBar>, <xref:System.Windows.Controls.ScrollViewer>, <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.Primitives.Thumb>, <xref:System.Windows.Controls.Viewbox>, <xref:System.Windows.Controls.VirtualizingStackPanel>, <xref:System.Windows.Window>, and <xref:System.Windows.Controls.WrapPanel>.</span></span>

- <span data-ttu-id="5d07c-159">**Multimedia**: <xref:System.Windows.Controls.Image>, <xref:System.Windows.Controls.MediaElement>i <xref:System.Windows.Controls.SoundPlayerAction>.</span><span class="sxs-lookup"><span data-stu-id="5d07c-159">**Media**: <xref:System.Windows.Controls.Image>, <xref:System.Windows.Controls.MediaElement>, and <xref:System.Windows.Controls.SoundPlayerAction>.</span></span>

- <span data-ttu-id="5d07c-160">**Menu**: <xref:System.Windows.Controls.ContextMenu>, <xref:System.Windows.Controls.Menu>i <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="5d07c-160">**Menus**: <xref:System.Windows.Controls.ContextMenu>, <xref:System.Windows.Controls.Menu>, and <xref:System.Windows.Controls.ToolBar>.</span></span>

- <span data-ttu-id="5d07c-161">**Nawigacja**: <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow>i <xref:System.Windows.Controls.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="5d07c-161">**Navigation**: <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow>, and <xref:System.Windows.Controls.TabControl>.</span></span>

- <span data-ttu-id="5d07c-162">**Wybór**: <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.RadioButton>i <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="5d07c-162">**Selection**: <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.RadioButton>, and <xref:System.Windows.Controls.Slider>.</span></span>

- <span data-ttu-id="5d07c-163">**Informacje o użytkowniku**: <xref:System.Windows.Controls.AccessText>, <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Primitives.Popup>, <xref:System.Windows.Controls.ProgressBar>, <xref:System.Windows.Controls.Primitives.StatusBar>, <xref:System.Windows.Controls.TextBlock>i <xref:System.Windows.Controls.ToolTip>.</span><span class="sxs-lookup"><span data-stu-id="5d07c-163">**User Information**: <xref:System.Windows.Controls.AccessText>, <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Primitives.Popup>, <xref:System.Windows.Controls.ProgressBar>, <xref:System.Windows.Controls.Primitives.StatusBar>, <xref:System.Windows.Controls.TextBlock>, and <xref:System.Windows.Controls.ToolTip>.</span></span>

## <a name="input-and-commands"></a><span data-ttu-id="5d07c-164">Dane wejściowe i polecenia</span><span class="sxs-lookup"><span data-stu-id="5d07c-164">Input and commands</span></span>

<span data-ttu-id="5d07c-165">Kontrolki najczęściej wykrywają dane wejściowe użytkownika i reagują na nie.</span><span class="sxs-lookup"><span data-stu-id="5d07c-165">Controls most often detect and respond to user input.</span></span> <span data-ttu-id="5d07c-166">[System wprowadzania WPF](advanced/input-overview.md) używa zdarzeń bezpośrednich i kierowanych do obsługi wprowadzania tekstu, zarządzania fokusem i pozycjonowania myszy.</span><span class="sxs-lookup"><span data-stu-id="5d07c-166">The [WPF input system](advanced/input-overview.md) uses both direct and routed events to support text input, focus management, and mouse positioning.</span></span>

<span data-ttu-id="5d07c-167">Aplikacje często mają złożone wymagania wejściowe.</span><span class="sxs-lookup"><span data-stu-id="5d07c-167">Applications often have complex input requirements.</span></span> <span data-ttu-id="5d07c-168">WPF udostępnia [system poleceń](advanced/commanding-overview.md) , który oddziela działania wprowadzane przez użytkownika od kodu, który odpowiada na te akcje.</span><span class="sxs-lookup"><span data-stu-id="5d07c-168">WPF provides a [command system](advanced/commanding-overview.md) that separates user-input actions from the code that responds to those actions.</span></span>

## <a name="layout"></a><span data-ttu-id="5d07c-169">Układ</span><span class="sxs-lookup"><span data-stu-id="5d07c-169">Layout</span></span>

<span data-ttu-id="5d07c-170">Podczas tworzenia interfejsu użytkownika można rozmieścić kontrolki według lokalizacji i rozmiaru w celu utworzenia układu.</span><span class="sxs-lookup"><span data-stu-id="5d07c-170">When you create a user interface, you arrange your controls by location and size to form a layout.</span></span> <span data-ttu-id="5d07c-171">Kluczowym wymaganiem dowolnego układu jest dostosowanie do zmian rozmiaru okna i ustawień wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="5d07c-171">A key requirement of any layout is to adapt to changes in window size and display settings.</span></span> <span data-ttu-id="5d07c-172">Zamiast wymuszania pisania kodu w celu dostosowania układu w tych okolicznościach, WPF udostępnia system układu pierwszej klasy.</span><span class="sxs-lookup"><span data-stu-id="5d07c-172">Rather than forcing you to write the code to adapt a layout in these circumstances, WPF provides a first-class, extensible layout system for you.</span></span>

<span data-ttu-id="5d07c-173">Podstawą układu systemu jest Pozycjonowanie względne, które zwiększa możliwość dostosowania do zmieniania okna i warunków wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="5d07c-173">The cornerstone of the layout system is relative positioning, which increases the ability to adapt to changing window and display conditions.</span></span> <span data-ttu-id="5d07c-174">Ponadto system układu zarządza negocjacją między kontrolkami w celu określenia układu.</span><span class="sxs-lookup"><span data-stu-id="5d07c-174">In addition, the layout system manages the negotiation between controls to determine the layout.</span></span> <span data-ttu-id="5d07c-175">Negocjowanie jest procesem dwuetapowym: najpierw formant informuje swój element nadrzędny o lokalizacji i rozmiarze wymaganym przez program. następnie element nadrzędny informuje o tym, jakie miejsce może mieć.</span><span class="sxs-lookup"><span data-stu-id="5d07c-175">The negotiation is a two-step process: first, a control tells its parent what location and size it requires; second, the parent tells the control what space it can have.</span></span>

<span data-ttu-id="5d07c-176">System układu jest narażony na kontrolki podrzędne za pomocą podstawowych klas WPF.</span><span class="sxs-lookup"><span data-stu-id="5d07c-176">The layout system is exposed to child controls through base WPF classes.</span></span> <span data-ttu-id="5d07c-177">W przypadku typowych układów, takich jak siatki, układania i dokowania, WPF zawiera kilka kontrolek układu:</span><span class="sxs-lookup"><span data-stu-id="5d07c-177">For common layouts such as grids, stacking, and docking, WPF includes several layout controls:</span></span>

- <span data-ttu-id="5d07c-178"><xref:System.Windows.Controls.Canvas>: formanty podrzędne zapewniają własny układ.</span><span class="sxs-lookup"><span data-stu-id="5d07c-178"><xref:System.Windows.Controls.Canvas>: Child controls provide their own layout.</span></span>

- <span data-ttu-id="5d07c-179"><xref:System.Windows.Controls.DockPanel>: kontrolki podrzędne są wyrównane do krawędzi panelu.</span><span class="sxs-lookup"><span data-stu-id="5d07c-179"><xref:System.Windows.Controls.DockPanel>: Child controls are aligned to the edges of the panel.</span></span>

- <span data-ttu-id="5d07c-180"><xref:System.Windows.Controls.Grid>: kontrolki podrzędne są pozycjonowane według wierszy i kolumn.</span><span class="sxs-lookup"><span data-stu-id="5d07c-180"><xref:System.Windows.Controls.Grid>: Child controls are positioned by rows and columns.</span></span>

- <span data-ttu-id="5d07c-181"><xref:System.Windows.Controls.StackPanel>: kontrolki podrzędne są ułożone pionowo lub poziomo.</span><span class="sxs-lookup"><span data-stu-id="5d07c-181"><xref:System.Windows.Controls.StackPanel>: Child controls are stacked either vertically or horizontally.</span></span>

- <span data-ttu-id="5d07c-182"><xref:System.Windows.Controls.VirtualizingStackPanel>: formanty podrzędne są zwirtualizowane i ułożone w jednym wierszu, który jest w poziomie lub w pionie.</span><span class="sxs-lookup"><span data-stu-id="5d07c-182"><xref:System.Windows.Controls.VirtualizingStackPanel>: Child controls are virtualized and arranged on a single line that is either horizontally or vertically oriented.</span></span>

- <span data-ttu-id="5d07c-183"><xref:System.Windows.Controls.WrapPanel>: formanty podrzędne są umieszczane w kolejności od lewej do prawej i zawijane do następnego wiersza, gdy istnieje więcej kontrolek w bieżącym wierszu niż zezwala na miejsce.</span><span class="sxs-lookup"><span data-stu-id="5d07c-183"><xref:System.Windows.Controls.WrapPanel>: Child controls are positioned in left-to-right order and wrapped to the next line when there are more controls on the current line than space allows.</span></span>

<span data-ttu-id="5d07c-184">Poniższy przykład używa <xref:System.Windows.Controls.DockPanel> do układania kilku kontrolek <xref:System.Windows.Controls.TextBox>:</span><span class="sxs-lookup"><span data-stu-id="5d07c-184">The following example uses a <xref:System.Windows.Controls.DockPanel> to lay out several <xref:System.Windows.Controls.TextBox> controls:</span></span>

[!code-xaml[IntroToWPFSnippets#LayoutMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_1.xaml)]

<span data-ttu-id="5d07c-185"><xref:System.Windows.Controls.DockPanel> umożliwia kontrolowanie <xref:System.Windows.Controls.TextBox> podrzędnych w celu poinformowania o tym, jak je rozmieścić.</span><span class="sxs-lookup"><span data-stu-id="5d07c-185">The <xref:System.Windows.Controls.DockPanel> allows the child <xref:System.Windows.Controls.TextBox> controls to tell it how to arrange them.</span></span> <span data-ttu-id="5d07c-186">W tym celu <xref:System.Windows.Controls.DockPanel> implementuje przyłączoną Właściwość `Dock`, która jest udostępniona kontrolkom podrzędnym, aby umożliwić każdemu z nich Określanie stylu dokowania.</span><span class="sxs-lookup"><span data-stu-id="5d07c-186">To do this, the <xref:System.Windows.Controls.DockPanel> implements a `Dock` attached property that is exposed to the child controls to allow each of them to specify a dock style.</span></span>

> [!NOTE]
> <span data-ttu-id="5d07c-187">Właściwość, która jest implementowana przez formant nadrzędny do użycia przez formanty podrzędne, jest konstrukcja WPF o nazwie [dołączona właściwość](advanced/attached-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="5d07c-187">A property that's implemented by a parent control for use by child controls is a WPF construct called an [attached property](advanced/attached-properties-overview.md).</span></span>

<span data-ttu-id="5d07c-188">Poniższy rysunek przedstawia wynik znacznika XAML w poprzednim przykładzie:</span><span class="sxs-lookup"><span data-stu-id="5d07c-188">The following figure shows the result of the XAML markup in the preceding example:</span></span>

![Strona DockPanel](media/introduction-to-wpf/wpfintrofigure11.png)

## <a name="data-binding"></a><span data-ttu-id="5d07c-190">Powiązanie danych</span><span class="sxs-lookup"><span data-stu-id="5d07c-190">Data binding</span></span>

<span data-ttu-id="5d07c-191">Większość aplikacji jest tworzonych w celu zapewnienia użytkownikom możliwości wyświetlania i edytowania danych.</span><span class="sxs-lookup"><span data-stu-id="5d07c-191">Most applications are created to provide users with the means to view and edit data.</span></span> <span data-ttu-id="5d07c-192">W przypadku aplikacji WPF można przechowywać dane i uzyskiwać do nich dostęp za pomocą technologii, takich jak SQL Server i ADO .NET.</span><span class="sxs-lookup"><span data-stu-id="5d07c-192">For WPF applications, the work of storing and accessing data is already provided for by technologies such as SQL Server and ADO .NET.</span></span> <span data-ttu-id="5d07c-193">Po uzyskaniu dostępu do danych i załadowaniu ich do zarządzanych obiektów aplikacji, rozpocznie się działanie dla aplikacji WPF.</span><span class="sxs-lookup"><span data-stu-id="5d07c-193">After the data is accessed and loaded into an application's managed objects, the hard work for WPF applications begins.</span></span> <span data-ttu-id="5d07c-194">Zasadniczo obejmuje to dwie rzeczy:</span><span class="sxs-lookup"><span data-stu-id="5d07c-194">Essentially, this involves two things:</span></span>

1. <span data-ttu-id="5d07c-195">Kopiowanie danych z zarządzanych obiektów do kontrolek, w których można wyświetlać i edytować dane.</span><span class="sxs-lookup"><span data-stu-id="5d07c-195">Copying the data from the managed objects into controls, where the data can be displayed and edited.</span></span>

2. <span data-ttu-id="5d07c-196">Zagwarantowanie, że zmiany wprowadzone do danych za pomocą kontrolek są kopiowane z powrotem do obiektów zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="5d07c-196">Ensuring that changes made to data by using controls are copied back to the managed objects.</span></span>

<span data-ttu-id="5d07c-197">Aby uprościć tworzenie aplikacji, funkcja WPF udostępnia aparat powiązań danych w celu automatycznego wykonania tych kroków.</span><span class="sxs-lookup"><span data-stu-id="5d07c-197">To simplify application development, WPF provides a data binding engine to automatically perform these steps.</span></span> <span data-ttu-id="5d07c-198">Jednostką podstawową aparatu powiązań danych jest Klasa <xref:System.Windows.Data.Binding>, której zadanie ma powiązać formant (obiekt docelowy powiązania) z obiektem danych (Źródło powiązania).</span><span class="sxs-lookup"><span data-stu-id="5d07c-198">The core unit of the data binding engine is the <xref:System.Windows.Data.Binding> class, whose job is to bind a control (the binding target) to a data object (the binding source).</span></span> <span data-ttu-id="5d07c-199">Ta relacja jest zilustrowana na poniższej ilustracji:</span><span class="sxs-lookup"><span data-stu-id="5d07c-199">This relationship is illustrated by the following figure:</span></span>

![Podstawowy diagram powiązań danych](media/introduction-to-wpf/databindingmostbasic.png)

<span data-ttu-id="5d07c-201">W następnym przykładzie pokazano, jak powiązać <xref:System.Windows.Controls.TextBox> z wystąpieniem niestandardowego obiektu `Person`.</span><span class="sxs-lookup"><span data-stu-id="5d07c-201">The next example demonstrates how to bind a <xref:System.Windows.Controls.TextBox> to an instance of a custom `Person` object.</span></span> <span data-ttu-id="5d07c-202">Implementacja `Person` jest pokazana w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="5d07c-202">The `Person` implementation is shown in the following code:</span></span>

[!code-vb[SimpleDataBindingSnippets#PersonClassCODE](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_2.vb)]
[!code-csharp[SimpleDataBindingSnippets#PersonClassCODE](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_2.cs)]

<span data-ttu-id="5d07c-203">Poniższy znacznik wiąże <xref:System.Windows.Controls.TextBox> z wystąpieniem niestandardowego obiektu `Person`:</span><span class="sxs-lookup"><span data-stu-id="5d07c-203">The following markup binds the <xref:System.Windows.Controls.TextBox> to an instance of a custom `Person` object:</span></span>

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

<span data-ttu-id="5d07c-204">W tym przykładzie Klasa `Person` jest tworzona w kodzie w tle i ustawiana jako kontekst danych dla `DataBindingWindow`.</span><span class="sxs-lookup"><span data-stu-id="5d07c-204">In this example, the `Person` class is instantiated in code-behind and is set as the data context for the `DataBindingWindow`.</span></span> <span data-ttu-id="5d07c-205">W znaczniku Właściwość <xref:System.Windows.Controls.TextBox.Text%2A> <xref:System.Windows.Controls.TextBox> jest powiązana z właściwością `Person.Name` (przy użyciu składni XAML "`{Binding ... }`").</span><span class="sxs-lookup"><span data-stu-id="5d07c-205">In markup, the <xref:System.Windows.Controls.TextBox.Text%2A> property of the <xref:System.Windows.Controls.TextBox> is bound to the `Person.Name` property (using the "`{Binding ... }`" XAML syntax).</span></span> <span data-ttu-id="5d07c-206">Ten kod XAML mówi WPF, aby powiązać formant <xref:System.Windows.Controls.TextBox> z obiektem `Person`, który jest przechowywany we właściwości <xref:System.Windows.FrameworkElement.DataContext%2A> okna.</span><span class="sxs-lookup"><span data-stu-id="5d07c-206">This XAML tells WPF to bind the <xref:System.Windows.Controls.TextBox> control to the `Person` object that is stored in the <xref:System.Windows.FrameworkElement.DataContext%2A> property of the window.</span></span>

<span data-ttu-id="5d07c-207">Aparat powiązań danych WPF zapewnia dodatkową pomoc techniczną, która obejmuje walidację, sortowanie, filtrowanie i grupowanie.</span><span class="sxs-lookup"><span data-stu-id="5d07c-207">The WPF data binding engine provides additional support that includes validation, sorting, filtering, and grouping.</span></span> <span data-ttu-id="5d07c-208">Ponadto powiązanie danych obsługuje używanie szablonów danych do tworzenia niestandardowego interfejsu użytkownika dla powiązanych danych, gdy interfejs użytkownika wyświetlany przez standardowe formanty WPF nie jest odpowiedni.</span><span class="sxs-lookup"><span data-stu-id="5d07c-208">Furthermore, data binding supports the use of data templates to create custom user interface for bound data when the user interface displayed by the standard WPF controls is not appropriate.</span></span>

<span data-ttu-id="5d07c-209">Aby uzyskać więcej informacji, zobacz temat [powiązanie danych — omówienie](../../desktop-wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="5d07c-209">For more information, see [Data binding overview](../../desktop-wpf/data/data-binding-overview.md).</span></span>

## <a name="graphics"></a><span data-ttu-id="5d07c-210">Grafika</span><span class="sxs-lookup"><span data-stu-id="5d07c-210">Graphics</span></span>

<span data-ttu-id="5d07c-211">WPF wprowadza bogaty, skalowalny i elastyczny zestaw funkcji graficznych, które mają następujące zalety:</span><span class="sxs-lookup"><span data-stu-id="5d07c-211">WPF introduces an extensive, scalable, and flexible set of graphics features that have the following benefits:</span></span>

- <span data-ttu-id="5d07c-212">**Niezależna od rozdzielczości i grafika niezależna od urządzenia**.</span><span class="sxs-lookup"><span data-stu-id="5d07c-212">**Resolution-independent and device-independent graphics**.</span></span> <span data-ttu-id="5d07c-213">Podstawowa jednostka miary w systemie grafiki WPF to piksel niezależny od urządzenia, czyli 1/1/96 cala, niezależnie od rzeczywistej rozdzielczości ekranu, a także podstawą renderowania niezależną od rozdzielczości i niezależną od urządzenia.</span><span class="sxs-lookup"><span data-stu-id="5d07c-213">The basic unit of measurement in the WPF graphics system is the device-independent pixel, which is 1/96th of an inch, regardless of actual screen resolution, and provides the foundation for resolution-independent and device-independent rendering.</span></span> <span data-ttu-id="5d07c-214">Każdy piksel niezależny od urządzenia automatycznie skaluje się w celu dopasowania do ustawienia DPI systemu, w którym jest renderowane.</span><span class="sxs-lookup"><span data-stu-id="5d07c-214">Each device-independent pixel automatically scales to match the dots-per-inch (dpi) setting of the system it renders on.</span></span>

- <span data-ttu-id="5d07c-215">**Ulepszona precyzja**.</span><span class="sxs-lookup"><span data-stu-id="5d07c-215">**Improved precision**.</span></span> <span data-ttu-id="5d07c-216">System współrzędnych WPF jest mierzony przy użyciu liczb zmiennoprzecinkowych o podwójnej precyzji, a nie pojedynczej precyzji.</span><span class="sxs-lookup"><span data-stu-id="5d07c-216">The WPF coordinate system is measured with double-precision floating-point numbers rather than single-precision.</span></span> <span data-ttu-id="5d07c-217">Przekształcenia i wartości przejrzystości są również wyrażone jako podwójne precyzja.</span><span class="sxs-lookup"><span data-stu-id="5d07c-217">Transformations and opacity values are also expressed as double-precision.</span></span> <span data-ttu-id="5d07c-218">WPF obsługuje również szeroką gamę kolorów (scRGB) i zapewnia zintegrowaną obsługę zarządzania danymi wejściowymi z różnych przestrzeni kolorów.</span><span class="sxs-lookup"><span data-stu-id="5d07c-218">WPF also supports a wide color gamut (scRGB) and provides integrated support for managing inputs from different color spaces.</span></span>

- <span data-ttu-id="5d07c-219">**Zaawansowana obsługa grafiki i animacji**.</span><span class="sxs-lookup"><span data-stu-id="5d07c-219">**Advanced graphics and animation support**.</span></span> <span data-ttu-id="5d07c-220">WPF upraszcza programowanie grafiki przez zarządzanie scenami animacji. nie trzeba martwić się o przetwarzanie sceny, pętle renderowania i interpolację liniową.</span><span class="sxs-lookup"><span data-stu-id="5d07c-220">WPF simplifies graphics programming by managing animation scenes for you; there is no need to worry about scene processing, rendering loops, and bilinear interpolation.</span></span> <span data-ttu-id="5d07c-221">Ponadto WPF zapewnia obsługę testowania trafień i pełną obsługę składania Alpha.</span><span class="sxs-lookup"><span data-stu-id="5d07c-221">Additionally, WPF provides hit-testing support and full alpha-compositing support.</span></span>

- <span data-ttu-id="5d07c-222">**Przyspieszenie sprzętowe**.</span><span class="sxs-lookup"><span data-stu-id="5d07c-222">**Hardware acceleration**.</span></span> <span data-ttu-id="5d07c-223">System grafiki WPF wykorzystuje sprzęt graficzny do zminimalizowania użycia procesora CPU.</span><span class="sxs-lookup"><span data-stu-id="5d07c-223">The WPF graphics system takes advantage of graphics hardware to minimize CPU usage.</span></span>

### <a name="2d-shapes"></a><span data-ttu-id="5d07c-224">kształty 2D</span><span class="sxs-lookup"><span data-stu-id="5d07c-224">2D shapes</span></span>

<span data-ttu-id="5d07c-225">WPF udostępnia bibliotekę wspólnych kształtów 2D rysowanych za pomocą wektorów, takich jak prostokąty i wielokropek, które są wyświetlane na poniższej ilustracji:</span><span class="sxs-lookup"><span data-stu-id="5d07c-225">WPF provides a library of common vector-drawn 2D shapes, such as the rectangles and ellipses that are shown in the following illustration:</span></span>

![Wielokropek i prostokąty](media/introduction-to-wpf/wpfintrofigure4.PNG)

<span data-ttu-id="5d07c-227">Interesująca możliwość tworzenia kształtów to nie tylko do wyświetlania; kształty implementują wiele funkcji, których oczekujesz od kontrolek, w tym dane wejściowe z klawiatury i myszy.</span><span class="sxs-lookup"><span data-stu-id="5d07c-227">An interesting capability of shapes is that they are not just for display; shapes implement many of the features that you expect from controls, including keyboard and mouse input.</span></span> <span data-ttu-id="5d07c-228">W poniższym przykładzie pokazano zdarzenie <xref:System.Windows.UIElement.MouseUp> obsługiwanego <xref:System.Windows.Shapes.Ellipse>:</span><span class="sxs-lookup"><span data-stu-id="5d07c-228">The following example shows the <xref:System.Windows.UIElement.MouseUp> event of an <xref:System.Windows.Shapes.Ellipse> being handled:</span></span>

[!code-xaml[IntroToWPFSnippets#HandleEllipseMouseUpEventMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_7.xaml)]

[!code-vb[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_8.vb)]
[!code-csharp[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_8.cs)]

<span data-ttu-id="5d07c-229">Na poniższej ilustracji przedstawiono, co jest tworzone przez poprzedni kod:</span><span class="sxs-lookup"><span data-stu-id="5d07c-229">The following figure shows what is produced by the preceding code:</span></span>

![Okno z tekstem "wielokropek&#33;"](media/introduction-to-wpf/wpfintrofigure12.png)

<span data-ttu-id="5d07c-231">Aby uzyskać więcej informacji, zobacz temat [kształty i podstawowe Rysowanie w programie WPF — Omówienie](../../desktop-wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="5d07c-231">For more information, see [Shapes and basic drawing in WPF overview](../../desktop-wpf/data/data-binding-overview.md).</span></span>

### <a name="2d-geometries"></a><span data-ttu-id="5d07c-232">2D geometrie</span><span class="sxs-lookup"><span data-stu-id="5d07c-232">2D geometries</span></span>

<span data-ttu-id="5d07c-233">Kształty 2D udostępniane przez WPF obejmują standardowy zestaw kształtów podstawowych.</span><span class="sxs-lookup"><span data-stu-id="5d07c-233">The 2D shapes provided by WPF cover the standard set of basic shapes.</span></span> <span data-ttu-id="5d07c-234">Jednak może być konieczne utworzenie niestandardowych kształtów w celu ułatwienia projektowania dostosowanego interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5d07c-234">However, you may need to create custom shapes to facilitate the design of a customized user interface.</span></span> <span data-ttu-id="5d07c-235">W tym celu WPF udostępnia geometrie.</span><span class="sxs-lookup"><span data-stu-id="5d07c-235">For this purpose, WPF provides geometries.</span></span> <span data-ttu-id="5d07c-236">Na poniższej ilustracji przedstawiono użycie geometrie do utworzenia niestandardowego kształtu, który może być rysowany bezpośrednio, używany jako pędzel lub używany do wycinania innych kształtów i kontrolek.</span><span class="sxs-lookup"><span data-stu-id="5d07c-236">The following figure demonstrates the use of geometries to create a custom shape that can be drawn directly, used as a brush, or used to clip other shapes and controls.</span></span>

<span data-ttu-id="5d07c-237">obiekty <xref:System.Windows.Shapes.Path> mogą służyć do rysowania zamkniętych lub otwartych kształtów, wielu kształtów, a nawet kształtów zakrzywionych.</span><span class="sxs-lookup"><span data-stu-id="5d07c-237"><xref:System.Windows.Shapes.Path> objects can be used to draw closed or open shapes, multiple shapes, and even curved shapes.</span></span>

<span data-ttu-id="5d07c-238">obiekty <xref:System.Windows.Media.Geometry> mogą służyć do przycinania, testowania trafień i renderowania danych graficznych 2D.</span><span class="sxs-lookup"><span data-stu-id="5d07c-238"><xref:System.Windows.Media.Geometry> objects can be used for clipping, hit-testing, and rendering 2D graphic data.</span></span>

![Różne zastosowania ścieżki](media/introduction-to-wpf/wpfintrofigure5.png)

<span data-ttu-id="5d07c-240">Aby uzyskać więcej informacji, zobacz [Omówienie geometrii](graphics-multimedia/geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="5d07c-240">For more information, see [Geometry overview](graphics-multimedia/geometry-overview.md).</span></span>

### <a name="2d-effects"></a><span data-ttu-id="5d07c-241">efekty 2D</span><span class="sxs-lookup"><span data-stu-id="5d07c-241">2D effects</span></span>

<span data-ttu-id="5d07c-242">Podzbiór możliwości WPF 2D obejmuje efekty wizualne, takie jak gradienty, mapy bitowe, rysunki, malowanie przy użyciu filmów wideo, obracanie, skalowanie i pochylanie.</span><span class="sxs-lookup"><span data-stu-id="5d07c-242">A subset of WPF 2D capabilities includes visual effects, such as gradients, bitmaps, drawings, painting with videos, rotation, scaling, and skewing.</span></span> <span data-ttu-id="5d07c-243">Są one osiągane przy użyciu pędzli; na poniższej ilustracji przedstawiono kilka przykładów:</span><span class="sxs-lookup"><span data-stu-id="5d07c-243">These are all achieved with brushes; the following figure shows some examples:</span></span>

![Ilustracja przedstawiająca różne pędzle](media/introduction-to-wpf/wpfintrofigure6.png)

<span data-ttu-id="5d07c-245">Aby uzyskać więcej informacji, zobacz [Omówienie pędzli WPF](graphics-multimedia/wpf-brushes-overview.md).</span><span class="sxs-lookup"><span data-stu-id="5d07c-245">For more information, see [WPF brushes overview](graphics-multimedia/wpf-brushes-overview.md).</span></span>

### <a name="3d-rendering"></a><span data-ttu-id="5d07c-246">Renderowanie 3W</span><span class="sxs-lookup"><span data-stu-id="5d07c-246">3D rendering</span></span>

<span data-ttu-id="5d07c-247">WPF obejmuje również funkcje renderowania 3W, które integrują się z grafikami 2-d, umożliwiając tworzenie bardziej atrakcyjnych i interesujących interfejsów użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5d07c-247">WPF also includes 3D rendering capabilities that integrate with 2-d graphics to allow the creation of more exciting and interesting user interfaces.</span></span> <span data-ttu-id="5d07c-248">Na przykład na poniższej ilustracji przedstawiono obrazy 2D renderowane na kształtach 3D:</span><span class="sxs-lookup"><span data-stu-id="5d07c-248">For example, the following figure shows 2D images rendered onto 3D shapes:</span></span>

![Zrzut ekranu przedstawiający przykładowy Visual3D](media/introduction-to-wpf/wpfintrofigure13.png)

<span data-ttu-id="5d07c-250">Aby uzyskać więcej informacji, zobacz [grafika 3D — Omówienie](graphics-multimedia/3-d-graphics-overview.md).</span><span class="sxs-lookup"><span data-stu-id="5d07c-250">For more information, see [3D graphics overview](graphics-multimedia/3-d-graphics-overview.md).</span></span>

## <a name="animation"></a><span data-ttu-id="5d07c-251">Animacja</span><span class="sxs-lookup"><span data-stu-id="5d07c-251">Animation</span></span>

<span data-ttu-id="5d07c-252">Obsługa animacji WPF pozwala zwiększyć, wstrząsać, obracać i zanikać kontrolki, aby tworzyć interesujące przejścia stron i nie tylko.</span><span class="sxs-lookup"><span data-stu-id="5d07c-252">WPF animation support lets you make controls grow, shake, spin, and fade, to create interesting page transitions, and more.</span></span> <span data-ttu-id="5d07c-253">Można animować większość klas WPF, nawet klas niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="5d07c-253">You can animate most WPF classes, even custom classes.</span></span> <span data-ttu-id="5d07c-254">Na poniższej ilustracji przedstawiono prostą animację w działaniu:</span><span class="sxs-lookup"><span data-stu-id="5d07c-254">The following figure shows a simple animation in action:</span></span>

![Obrazy animowanego modułu](media/introduction-to-wpf/wpfintrofigure7.png)

<span data-ttu-id="5d07c-256">Aby uzyskać więcej informacji, zobacz [Omówienie animacji](graphics-multimedia/animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="5d07c-256">For more information, see [Animation overview](graphics-multimedia/animation-overview.md).</span></span>

## <a name="media"></a><span data-ttu-id="5d07c-257">Nośnik</span><span class="sxs-lookup"><span data-stu-id="5d07c-257">Media</span></span>

<span data-ttu-id="5d07c-258">Jednym ze sposobów przekazywania rozbudowanej zawartości jest użycie multimediów audiowizualnych.</span><span class="sxs-lookup"><span data-stu-id="5d07c-258">One way to convey rich content is through the use of audiovisual media.</span></span> <span data-ttu-id="5d07c-259">WPF zapewnia specjalną obsługę obrazów, wideo i audio.</span><span class="sxs-lookup"><span data-stu-id="5d07c-259">WPF provides special support for images, video, and audio.</span></span>

### <a name="images"></a><span data-ttu-id="5d07c-260">Obrazy</span><span class="sxs-lookup"><span data-stu-id="5d07c-260">Images</span></span>

<span data-ttu-id="5d07c-261">Obrazy są wspólne dla większości aplikacji, a WPF oferuje kilka sposobów ich używania.</span><span class="sxs-lookup"><span data-stu-id="5d07c-261">Images are common to most applications, and WPF provides several ways to use them.</span></span> <span data-ttu-id="5d07c-262">Na poniższej ilustracji przedstawiono interfejs użytkownika z polem listy zawierającym obrazy miniatur.</span><span class="sxs-lookup"><span data-stu-id="5d07c-262">The following figure shows a user interface with a list box that contains thumbnail images.</span></span> <span data-ttu-id="5d07c-263">Po wybraniu miniatury obraz zostanie wyświetlony w pełnym rozmiarze.</span><span class="sxs-lookup"><span data-stu-id="5d07c-263">When a thumbnail is selected, the image is shown full-size.</span></span>

![Obrazy miniatur i obraz o&#45;pełnym rozmiarze](media/introduction-to-wpf/wpfintrofigure8.png)

<span data-ttu-id="5d07c-265">Aby uzyskać więcej informacji, zobacz [Omówienie tworzenia obrazu](graphics-multimedia/imaging-overview.md).</span><span class="sxs-lookup"><span data-stu-id="5d07c-265">For more information, see [Imaging overview](graphics-multimedia/imaging-overview.md).</span></span>

### <a name="video-and-audio"></a><span data-ttu-id="5d07c-266">Wideo i audio</span><span class="sxs-lookup"><span data-stu-id="5d07c-266">Video and audio</span></span>

<span data-ttu-id="5d07c-267">Kontrolka <xref:System.Windows.Controls.MediaElement> jest w stanie odtwarzać wideo i dźwięk, a jest wystarczająco elastyczna, aby była podstawą dla niestandardowego odtwarzacza multimedialnego.</span><span class="sxs-lookup"><span data-stu-id="5d07c-267">The <xref:System.Windows.Controls.MediaElement> control is capable of playing both video and audio, and it is flexible enough to be the basis for a custom media player.</span></span> <span data-ttu-id="5d07c-268">Następujące oznakowanie XAML implementuje odtwarzacz multimedialny:</span><span class="sxs-lookup"><span data-stu-id="5d07c-268">The following XAML markup implements a media player:</span></span>

[!code-xaml[IntroToWPFSnippets#MediaElementMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_9.xaml)]

<span data-ttu-id="5d07c-269">Okno na poniższej ilustracji przedstawia kontrolkę <xref:System.Windows.Controls.MediaElement> w akcji:</span><span class="sxs-lookup"><span data-stu-id="5d07c-269">The window in the following figure shows the <xref:System.Windows.Controls.MediaElement> control in action:</span></span>

![Kontrolka MediaElement z dźwiękiem i wideo](media/introduction-to-wpf/wpfintrofigure1.png)

<span data-ttu-id="5d07c-271">Aby uzyskać więcej informacji, zobacz [grafika i multimedia](graphics-multimedia/index.md).</span><span class="sxs-lookup"><span data-stu-id="5d07c-271">For more information, see [Graphics and multimedia](graphics-multimedia/index.md).</span></span>

## <a name="text-and-typography"></a><span data-ttu-id="5d07c-272">Tekst i Typografia</span><span class="sxs-lookup"><span data-stu-id="5d07c-272">Text and typography</span></span>

<span data-ttu-id="5d07c-273">Aby ułatwić renderowanie tekstu o wysokiej jakości, WPF oferuje następujące funkcje:</span><span class="sxs-lookup"><span data-stu-id="5d07c-273">To facilitate high-quality text rendering, WPF offers the following features:</span></span>

- <span data-ttu-id="5d07c-274">Obsługa czcionek OpenType.</span><span class="sxs-lookup"><span data-stu-id="5d07c-274">OpenType font support.</span></span>

- <span data-ttu-id="5d07c-275">Ulepszenia technologii ClearType.</span><span class="sxs-lookup"><span data-stu-id="5d07c-275">ClearType enhancements.</span></span>

- <span data-ttu-id="5d07c-276">Wysoka wydajność, która wykorzystuje przyspieszenie sprzętowe.</span><span class="sxs-lookup"><span data-stu-id="5d07c-276">High performance that takes advantage of hardware acceleration.</span></span>

- <span data-ttu-id="5d07c-277">Integracja tekstu z multimediami, grafiką i animacją.</span><span class="sxs-lookup"><span data-stu-id="5d07c-277">Integration of text with media, graphics, and animation.</span></span>

- <span data-ttu-id="5d07c-278">Obsługa czcionek międzynarodowych i mechanizmów powrotu.</span><span class="sxs-lookup"><span data-stu-id="5d07c-278">International font support and fallback mechanisms.</span></span>

<span data-ttu-id="5d07c-279">Na poniższej ilustracji przedstawiono sposób integracji tekstu z grafiką:</span><span class="sxs-lookup"><span data-stu-id="5d07c-279">As a demonstration of text integration with graphics, the following figure shows the application of text decorations:</span></span>

![Tekst z różnymi dekoracjami tekstu](media/introduction-to-wpf/wpfintrofigure23.png)

<span data-ttu-id="5d07c-281">Aby uzyskać więcej informacji, zobacz [Typografia w Windows Presentation Foundation](advanced/typography-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="5d07c-281">For more information, see [Typography in Windows Presentation Foundation](advanced/typography-in-wpf.md).</span></span>

## <a name="customize-wpf-apps"></a><span data-ttu-id="5d07c-282">Dostosuj aplikacje WPF</span><span class="sxs-lookup"><span data-stu-id="5d07c-282">Customize WPF apps</span></span>

<span data-ttu-id="5d07c-283">Do tego momentu zaobserwowano podstawowe bloki konstrukcyjne WPF na potrzeby tworzenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5d07c-283">Up to this point, you've seen the core WPF building blocks for developing applications.</span></span> <span data-ttu-id="5d07c-284">Model aplikacji jest używany do hostowania i dostarczania zawartości aplikacji, która składa się głównie z kontrolek.</span><span class="sxs-lookup"><span data-stu-id="5d07c-284">You use the application model to host and deliver application content, which consists mainly of controls.</span></span> <span data-ttu-id="5d07c-285">Aby uprościć rozmieszczenie formantów w interfejsie użytkownika i upewnić się, że rozmieszczenie jest zachowywane na początku zmian rozmiaru okna i ustawień wyświetlania, należy użyć systemu układu WPF.</span><span class="sxs-lookup"><span data-stu-id="5d07c-285">To simplify the arrangement of controls in a user interface, and to ensure the arrangement is maintained in the face of changes to window size and display settings, you use the WPF layout system.</span></span> <span data-ttu-id="5d07c-286">Ze względu na to, że większość aplikacji pozwala użytkownikom na współdziałanie z danymi, należy użyć powiązania danych, aby ograniczyć pracę integracji interfejsu użytkownika z danymi.</span><span class="sxs-lookup"><span data-stu-id="5d07c-286">Because most applications let users interact with data, you use data binding to reduce the work of integrating your user interface with data.</span></span> <span data-ttu-id="5d07c-287">Aby wzmocnić wygląd aplikacji, należy użyć kompleksowego zakresu grafiki, animacji i pomocy technicznej multimedialnej zapewnianej przez WPF.</span><span class="sxs-lookup"><span data-stu-id="5d07c-287">To enhance the visual appearance of your application, you use the comprehensive range of graphics, animation, and media support provided by WPF.</span></span>

<span data-ttu-id="5d07c-288">Często jednak podstawowe informacje nie są wystarczające do tworzenia naprawdę odrębnego i wizualnego środowiska użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5d07c-288">Often, though, the basics are not enough for creating and managing a truly distinct and visually stunning user experience.</span></span> <span data-ttu-id="5d07c-289">Standardowe formanty WPF mogą nie zostać zintegrowane z żądanym wyglądem aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5d07c-289">The standard WPF controls might not integrate with the desired appearance of your application.</span></span> <span data-ttu-id="5d07c-290">Dane mogą nie być wyświetlane w najbardziej efektywny sposób.</span><span class="sxs-lookup"><span data-stu-id="5d07c-290">Data might not be displayed in the most effective way.</span></span> <span data-ttu-id="5d07c-291">Ogólne środowisko użytkownika aplikacji może nie być odpowiednie dla domyślnego wyglądu i sposobu działania motywów systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="5d07c-291">Your application's overall user experience may not be suited to the default look and feel of Windows themes.</span></span> <span data-ttu-id="5d07c-292">Na wiele sposobów Technologia prezentacji wymaga rozszerzalności wizualizacji tak samo, jak każdy inny typ rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="5d07c-292">In many ways, a presentation technology needs visual extensibility as much as any other type of extensibility.</span></span>

<span data-ttu-id="5d07c-293">Z tego powodu WPF oferuje różne mechanizmy tworzenia unikatowych środowisk użytkowników, w tym bogaty model zawartości dla formantów, wyzwalaczy, szablonów formantów i danych, stylów, zasobów interfejsu użytkownika i motywów i karnacji.</span><span class="sxs-lookup"><span data-stu-id="5d07c-293">For this reason, WPF provides a variety of mechanisms for creating unique user experiences, including a rich content model for controls, triggers, control and data templates, styles, user interface resources, and themes and skins.</span></span>

### <a name="content-model"></a><span data-ttu-id="5d07c-294">Model zawartości</span><span class="sxs-lookup"><span data-stu-id="5d07c-294">Content model</span></span>

<span data-ttu-id="5d07c-295">Głównym celem większości formantów WPF jest wyświetlenie zawartości.</span><span class="sxs-lookup"><span data-stu-id="5d07c-295">The main purpose of a majority of the WPF controls is to display content.</span></span> <span data-ttu-id="5d07c-296">W WPF typ i liczba elementów, które mogą stanowić zawartość kontrolki, jest określany jako *model zawartości*kontrolki.</span><span class="sxs-lookup"><span data-stu-id="5d07c-296">In WPF, the type and number of items that can constitute the content of a control is referred to as the control's *content model*.</span></span> <span data-ttu-id="5d07c-297">Niektóre kontrolki mogą zawierać pojedynczy element i typ zawartości; na przykład zawartość <xref:System.Windows.Controls.TextBox> jest wartością ciągu, która jest przypisana do właściwości <xref:System.Windows.Controls.TextBox.Text%2A>.</span><span class="sxs-lookup"><span data-stu-id="5d07c-297">Some controls can contain a single item and type of content; for example, the content of a <xref:System.Windows.Controls.TextBox> is a string value that is assigned to the <xref:System.Windows.Controls.TextBox.Text%2A> property.</span></span> <span data-ttu-id="5d07c-298">Poniższy przykład ustawia zawartość <xref:System.Windows.Controls.TextBox>:</span><span class="sxs-lookup"><span data-stu-id="5d07c-298">The following example sets the content of a <xref:System.Windows.Controls.TextBox>:</span></span>

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.TextBoxContentWindow"
    Title="TextBox Content">

    <TextBox Text="This is the content of a TextBox." />
</Window>
```

<span data-ttu-id="5d07c-299">Poniższy rysunek przedstawia wynik:</span><span class="sxs-lookup"><span data-stu-id="5d07c-299">The following figure shows the result:</span></span>

![Formant TextBox zawierający tekst.](media/introduction-to-wpf/wpfintrofigure21.png)

<span data-ttu-id="5d07c-301">Inne kontrolki, jednak mogą zawierać wiele elementów różnych typów zawartości; zawartość <xref:System.Windows.Controls.Button>, określona przez właściwość <xref:System.Windows.Controls.ContentControl.Content%2A>, może zawierać różne elementy, takie jak kontrolki układu, tekst, obrazy i kształty.</span><span class="sxs-lookup"><span data-stu-id="5d07c-301">Other controls, however, can contain multiple items of different types of content; the content of a <xref:System.Windows.Controls.Button>, specified by the <xref:System.Windows.Controls.ContentControl.Content%2A> property, can contain a variety of items including layout controls, text, images, and shapes.</span></span> <span data-ttu-id="5d07c-302">Poniższy przykład pokazuje <xref:System.Windows.Controls.Button> z zawartością obejmującą <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Border>i <xref:System.Windows.Controls.MediaElement>:</span><span class="sxs-lookup"><span data-stu-id="5d07c-302">The following example shows a <xref:System.Windows.Controls.Button> with content that includes a <xref:System.Windows.Controls.DockPanel>, a <xref:System.Windows.Controls.Label>, a <xref:System.Windows.Controls.Border>, and a <xref:System.Windows.Controls.MediaElement>:</span></span>

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

<span data-ttu-id="5d07c-303">Na poniższej ilustracji przedstawiono zawartość tego przycisku:</span><span class="sxs-lookup"><span data-stu-id="5d07c-303">The following figure shows the content of this button:</span></span>

![Przycisk, który zawiera wiele typów zawartości](media/introduction-to-wpf/wpfintrofigure22.png)

<span data-ttu-id="5d07c-305">Aby uzyskać więcej informacji o rodzaju zawartości obsługiwanej przez różne kontrolki, zobacz artykuł [model zawartości WPF](controls/wpf-content-model.md).</span><span class="sxs-lookup"><span data-stu-id="5d07c-305">For more information on the kinds of content that is supported by various controls, see [WPF content model](controls/wpf-content-model.md).</span></span>

### <a name="triggers"></a><span data-ttu-id="5d07c-306">Wyzwalacze</span><span class="sxs-lookup"><span data-stu-id="5d07c-306">Triggers</span></span>

<span data-ttu-id="5d07c-307">Chociaż głównym celem znacznika języka XAML jest zaimplementowanie wyglądu aplikacji, można również użyć języka XAML do implementacji niektórych aspektów zachowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5d07c-307">Although the main purpose of XAML markup is to implement an application's appearance, you can also use XAML to implement some aspects of an application's behavior.</span></span> <span data-ttu-id="5d07c-308">Przykładem jest użycie wyzwalaczy do zmiany wyglądu aplikacji w oparciu o Interakcje użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5d07c-308">One example is the use of triggers to change an application's appearance based on user interactions.</span></span> <span data-ttu-id="5d07c-309">Aby uzyskać więcej informacji, zobacz [Style i szablony](../../desktop-wpf/fundamentals/styles-templates-overview.md).</span><span class="sxs-lookup"><span data-stu-id="5d07c-309">For more information, see [Styles and templates](../../desktop-wpf/fundamentals/styles-templates-overview.md).</span></span>

### <a name="control-templates"></a><span data-ttu-id="5d07c-310">Szablony kontrolek</span><span class="sxs-lookup"><span data-stu-id="5d07c-310">Control templates</span></span>

<span data-ttu-id="5d07c-311">Domyślne interfejsy użytkownika dla formantów WPF są zwykle zbudowane z innych formantów i kształtów.</span><span class="sxs-lookup"><span data-stu-id="5d07c-311">The default user interfaces for WPF controls are typically constructed from other controls and shapes.</span></span> <span data-ttu-id="5d07c-312">Na przykład <xref:System.Windows.Controls.Button> składa się z formantów <xref:Microsoft.Windows.Themes.ButtonChrome> i <xref:System.Windows.Controls.ContentPresenter>.</span><span class="sxs-lookup"><span data-stu-id="5d07c-312">For example, a <xref:System.Windows.Controls.Button> is composed of both <xref:Microsoft.Windows.Themes.ButtonChrome> and <xref:System.Windows.Controls.ContentPresenter> controls.</span></span> <span data-ttu-id="5d07c-313"><xref:Microsoft.Windows.Themes.ButtonChrome> zapewnia standardowy wygląd przycisku, podczas gdy <xref:System.Windows.Controls.ContentPresenter> wyświetla zawartość przycisku, jak określono przez właściwość <xref:System.Windows.Controls.ContentControl.Content%2A>.</span><span class="sxs-lookup"><span data-stu-id="5d07c-313">The <xref:Microsoft.Windows.Themes.ButtonChrome> provides the standard button appearance, while the <xref:System.Windows.Controls.ContentPresenter> displays the button's content, as specified by the <xref:System.Windows.Controls.ContentControl.Content%2A> property.</span></span>

<span data-ttu-id="5d07c-314">Czasami domyślny wygląd formantu może być incongruent z ogólnym wyglądem aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5d07c-314">Sometimes the default appearance of a control may be incongruent with the overall appearance of an application.</span></span> <span data-ttu-id="5d07c-315">W takim przypadku można użyć <xref:System.Windows.Controls.ControlTemplate>, aby zmienić wygląd interfejsu użytkownika kontrolki bez zmiany jego zawartości i zachowania.</span><span class="sxs-lookup"><span data-stu-id="5d07c-315">In this case, you can use a <xref:System.Windows.Controls.ControlTemplate> to change the appearance of the control's user interface without changing its content and behavior.</span></span>

<span data-ttu-id="5d07c-316">Poniższy przykład pokazuje, jak zmienić wygląd <xref:System.Windows.Controls.Button> przy użyciu <xref:System.Windows.Controls.ControlTemplate>:</span><span class="sxs-lookup"><span data-stu-id="5d07c-316">The following example shows how to change the appearance of a <xref:System.Windows.Controls.Button> by using a <xref:System.Windows.Controls.ControlTemplate>:</span></span>

[!code-xaml[IntroToWPFSnippets#ButtonControlTemplateWindowMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_16.xaml)]

[!code-csharp[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_17.cs)]
[!code-vb[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_17.vb)]

<span data-ttu-id="5d07c-317">W tym przykładzie interfejs użytkownika przycisku domyślnego został zastąpiony <xref:System.Windows.Shapes.Ellipse>, który ma ciemne niebieskie obramowanie i jest wypełniany przy użyciu <xref:System.Windows.Media.RadialGradientBrush>.</span><span class="sxs-lookup"><span data-stu-id="5d07c-317">In this example, the default button user interface has been replaced with an <xref:System.Windows.Shapes.Ellipse> that has a dark blue border and is filled using a <xref:System.Windows.Media.RadialGradientBrush>.</span></span> <span data-ttu-id="5d07c-318">Kontrolka <xref:System.Windows.Controls.ContentPresenter> wyświetla zawartość <xref:System.Windows.Controls.Button>"kliknij mnie!"</span><span class="sxs-lookup"><span data-stu-id="5d07c-318">The <xref:System.Windows.Controls.ContentPresenter> control displays the content of the <xref:System.Windows.Controls.Button>, "Click Me!"</span></span> <span data-ttu-id="5d07c-319">Po kliknięciu <xref:System.Windows.Controls.Button> zdarzenie <xref:System.Windows.Controls.Primitives.ButtonBase.Click> jest nadal zgłaszane jako część domyślnego zachowania <xref:System.Windows.Controls.Button> formantu.</span><span class="sxs-lookup"><span data-stu-id="5d07c-319">When the <xref:System.Windows.Controls.Button> is clicked, the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event is still raised as part of the <xref:System.Windows.Controls.Button> control's default behavior.</span></span> <span data-ttu-id="5d07c-320">Wyniki są pokazane na poniższym rysunku:</span><span class="sxs-lookup"><span data-stu-id="5d07c-320">The result is shown in the following figure:</span></span>

![Przycisk eliptyczne i drugie okno](media/introduction-to-wpf/wpfintrofigure2.png)

### <a name="data-templates"></a><span data-ttu-id="5d07c-322">Szablony danych</span><span class="sxs-lookup"><span data-stu-id="5d07c-322">Data templates</span></span>

<span data-ttu-id="5d07c-323">Natomiast szablon kontrolki umożliwia określenie wyglądu kontrolki, szablon danych pozwala określić wygląd zawartości kontrolki.</span><span class="sxs-lookup"><span data-stu-id="5d07c-323">Whereas a control template lets you specify the appearance of a control, a data template lets you specify the appearance of a control's content.</span></span> <span data-ttu-id="5d07c-324">Szablony danych są często używane do ulepszania sposobu wyświetlania powiązanych danych.</span><span class="sxs-lookup"><span data-stu-id="5d07c-324">Data templates are frequently used to enhance how bound data is displayed.</span></span> <span data-ttu-id="5d07c-325">Na poniższej ilustracji przedstawiono domyślny wygląd <xref:System.Windows.Controls.ListBox>, który jest powiązany z kolekcją obiektów `Task`, gdzie każde zadanie ma nazwę, opis i priorytet:</span><span class="sxs-lookup"><span data-stu-id="5d07c-325">The following figure shows the default appearance for a <xref:System.Windows.Controls.ListBox> that is bound to a collection of `Task` objects, where each task has a name, description, and priority:</span></span>

![Pole listy z wyglądem domyślnym](media/introduction-to-wpf/wpfintrofigure18.png)

<span data-ttu-id="5d07c-327">Domyślnym wyglądem jest oczekiwanie od <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="5d07c-327">The default appearance is what you would expect from a <xref:System.Windows.Controls.ListBox>.</span></span> <span data-ttu-id="5d07c-328">Jednak domyślny wygląd każdego zadania zawiera tylko nazwę zadania.</span><span class="sxs-lookup"><span data-stu-id="5d07c-328">However, the default appearance of each task contains only the task name.</span></span> <span data-ttu-id="5d07c-329">Aby wyświetlić nazwę, opis i priorytet zadania, domyślny wygląd elementów listy powiązanej kontrolki <xref:System.Windows.Controls.ListBox> należy zmienić przy użyciu <xref:System.Windows.DataTemplate>.</span><span class="sxs-lookup"><span data-stu-id="5d07c-329">To show the task name, description, and priority, the default appearance of the <xref:System.Windows.Controls.ListBox> control's bound list items must be changed by using a <xref:System.Windows.DataTemplate>.</span></span> <span data-ttu-id="5d07c-330">Poniższy kod XAML definiuje takie <xref:System.Windows.DataTemplate>, które są stosowane do każdego zadania przy użyciu atrybutu <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>:</span><span class="sxs-lookup"><span data-stu-id="5d07c-330">The following XAML defines such a <xref:System.Windows.DataTemplate>, which is applied to each task by using the <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> attribute:</span></span>

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

<span data-ttu-id="5d07c-331">Poniższy rysunek przedstawia efekt tego kodu:</span><span class="sxs-lookup"><span data-stu-id="5d07c-331">The following figure shows the effect of this code:</span></span>

![Pole listy, które używa szablonu danych](media/introduction-to-wpf/wpfintrofigure19.png)

<span data-ttu-id="5d07c-333">Należy zauważyć, że <xref:System.Windows.Controls.ListBox> zachował zachowanie i ogólny wygląd; Zmieniono tylko wygląd zawartości wyświetlanej w polu listy.</span><span class="sxs-lookup"><span data-stu-id="5d07c-333">Note that the <xref:System.Windows.Controls.ListBox> has retained its behavior and overall appearance; only the appearance of the content being displayed by the list box has changed.</span></span>

<span data-ttu-id="5d07c-334">Aby uzyskać więcej informacji, zobacz [tworzenia szablonów danych — omówienie](data/data-templating-overview.md).</span><span class="sxs-lookup"><span data-stu-id="5d07c-334">For more information, see [Data templating overview](data/data-templating-overview.md).</span></span>

### <a name="styles"></a><span data-ttu-id="5d07c-335">Style</span><span class="sxs-lookup"><span data-stu-id="5d07c-335">Styles</span></span>

<span data-ttu-id="5d07c-336">Style umożliwiają deweloperom i projektantom ujednolicenie się z konkretnym wyglądem produktu.</span><span class="sxs-lookup"><span data-stu-id="5d07c-336">Styles enable developers and designers to standardize on a particular appearance for their product.</span></span> <span data-ttu-id="5d07c-337">WPF oferuje model silnego stylu, podstawę, która jest elementem <xref:System.Windows.Style>.</span><span class="sxs-lookup"><span data-stu-id="5d07c-337">WPF provides a strong style model, the foundation of which is the <xref:System.Windows.Style> element.</span></span> <span data-ttu-id="5d07c-338">Poniższy przykład tworzy styl, który ustawia kolor tła dla każdego <xref:System.Windows.Controls.Button> w oknie do `Orange`:</span><span class="sxs-lookup"><span data-stu-id="5d07c-338">The following example creates a style that sets the background color for every <xref:System.Windows.Controls.Button> on a window to `Orange`:</span></span>

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

<span data-ttu-id="5d07c-339">Ponieważ ten styl jest przeznaczony dla wszystkich kontrolek <xref:System.Windows.Controls.Button>, styl jest automatycznie stosowany do wszystkich przycisków w oknie, jak pokazano na poniższej ilustracji:</span><span class="sxs-lookup"><span data-stu-id="5d07c-339">Because this style targets all <xref:System.Windows.Controls.Button> controls, the style is automatically applied to all the buttons in the window, as shown in the following figure:</span></span>

![Dwa pomarańczowe przyciski](media/introduction-to-wpf/wpfintrofigure20.png)

<span data-ttu-id="5d07c-341">Aby uzyskać więcej informacji, zobacz [Style i szablony](../../desktop-wpf/fundamentals/styles-templates-overview.md).</span><span class="sxs-lookup"><span data-stu-id="5d07c-341">For more information, see [Styles and templates](../../desktop-wpf/fundamentals/styles-templates-overview.md).</span></span>

### <a name="resources"></a><span data-ttu-id="5d07c-342">Resources</span><span class="sxs-lookup"><span data-stu-id="5d07c-342">Resources</span></span>

<span data-ttu-id="5d07c-343">Kontrolki w aplikacji powinny korzystać z tego samego wyglądu, które mogą zawierać dowolne elementy z czcionek i kolorów tła, które umożliwiają kontrolowanie szablonów, szablonów danych i stylów.</span><span class="sxs-lookup"><span data-stu-id="5d07c-343">Controls in an application should share the same appearance, which can include anything from fonts and background colors to control templates, data templates, and styles.</span></span> <span data-ttu-id="5d07c-344">Możesz użyć obsługi platformy WPF do zasobów interfejsu użytkownika, aby hermetyzować te zasoby w jednej lokalizacji do ponownego użycia.</span><span class="sxs-lookup"><span data-stu-id="5d07c-344">You can use WPF's support for user interface resources to encapsulate these resources in a single location for reuse.</span></span>

<span data-ttu-id="5d07c-345">W poniższym przykładzie zdefiniowano typowy kolor tła, który jest współużytkowany przez <xref:System.Windows.Controls.Button> i <xref:System.Windows.Controls.Label>:</span><span class="sxs-lookup"><span data-stu-id="5d07c-345">The following example defines a common background color that is shared by a <xref:System.Windows.Controls.Button> and a <xref:System.Windows.Controls.Label>:</span></span>

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

<span data-ttu-id="5d07c-346">Ten przykład implementuje zasób koloru tła za pomocą elementu właściwości `Window.Resources`.</span><span class="sxs-lookup"><span data-stu-id="5d07c-346">This example implements a background color resource by using the `Window.Resources` property element.</span></span> <span data-ttu-id="5d07c-347">Ten zasób jest dostępny dla wszystkich elementów podrzędnych <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="5d07c-347">This resource is available to all children of the <xref:System.Windows.Window>.</span></span> <span data-ttu-id="5d07c-348">Istnieje wiele zakresów zasobów, w tym następujące, wymienione w kolejności, w jakiej zostały rozwiązane:</span><span class="sxs-lookup"><span data-stu-id="5d07c-348">There are a variety of resource scopes, including the following, listed in the order in which they are resolved:</span></span>

1. <span data-ttu-id="5d07c-349">Indywidualny formant (przy użyciu odziedziczonej właściwości <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName>).</span><span class="sxs-lookup"><span data-stu-id="5d07c-349">An individual control (using the inherited <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> property).</span></span>

2. <span data-ttu-id="5d07c-350"><xref:System.Windows.Window> lub <xref:System.Windows.Controls.Page> (również przy użyciu odziedziczonej właściwości <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName>).</span><span class="sxs-lookup"><span data-stu-id="5d07c-350">A <xref:System.Windows.Window> or a <xref:System.Windows.Controls.Page> (also using the inherited <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> property).</span></span>

3. <span data-ttu-id="5d07c-351"><xref:System.Windows.Application> (przy użyciu właściwości <xref:System.Windows.Application.Resources%2A?displayProperty=fullName>).</span><span class="sxs-lookup"><span data-stu-id="5d07c-351">An <xref:System.Windows.Application> (using the <xref:System.Windows.Application.Resources%2A?displayProperty=fullName> property).</span></span>

<span data-ttu-id="5d07c-352">Różne zakresy zapewniają elastyczność w odniesieniu do sposobu definiowania i udostępniania zasobów.</span><span class="sxs-lookup"><span data-stu-id="5d07c-352">The variety of scopes gives you flexibility with respect to the way in which you define and share your resources.</span></span>

<span data-ttu-id="5d07c-353">Alternatywnie do bezpośredniego kojarzenia zasobów z określonym zakresem, można spakować jeden lub więcej zasobów przy użyciu oddzielnych <xref:System.Windows.ResourceDictionary>, do których można odwoływać się w innych częściach aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5d07c-353">As an alternative to directly associating your resources with a particular scope, you can package one or more resources by using a separate <xref:System.Windows.ResourceDictionary> that can be referenced in other parts of an application.</span></span> <span data-ttu-id="5d07c-354">Na przykład w poniższym przykładzie zdefiniowano domyślny kolor tła w słowniku zasobów:</span><span class="sxs-lookup"><span data-stu-id="5d07c-354">For example, the following example defines a default background color in a resource dictionary:</span></span>

```xaml
<ResourceDictionary
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">

  <!-- Define background color resource -->
  <SolidColorBrush x:Key="defaultBackground" Color="Red" />

  <!-- Define other resources -->
</ResourceDictionary>
```

<span data-ttu-id="5d07c-355">Poniższy przykład odwołuje się do słownika zasobów zdefiniowanego w poprzednim przykładzie, tak aby był współużytkowany przez aplikację:</span><span class="sxs-lookup"><span data-stu-id="5d07c-355">The following example references the resource dictionary defined in the previous example so that it is shared across an application:</span></span>

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

<span data-ttu-id="5d07c-356">Zasoby i słowniki zasobów są podstawą obsługi technologii WPF dla motywów i skórek.</span><span class="sxs-lookup"><span data-stu-id="5d07c-356">Resources and resource dictionaries are the foundation of WPF support for themes and skins.</span></span>

<span data-ttu-id="5d07c-357">Aby uzyskać więcej informacji, zobacz [zasoby](../../desktop-wpf/fundamentals/xaml-resources-define.md).</span><span class="sxs-lookup"><span data-stu-id="5d07c-357">For more information, see [Resources](../../desktop-wpf/fundamentals/xaml-resources-define.md).</span></span>

### <a name="custom-controls"></a><span data-ttu-id="5d07c-358">Kontrolki niestandardowe</span><span class="sxs-lookup"><span data-stu-id="5d07c-358">Custom controls</span></span>

<span data-ttu-id="5d07c-359">Mimo że WPF udostępnia obsługę dostosowywania, można napotkać sytuacje, w których istniejące formanty WPF nie spełniają wymagań aplikacji lub użytkowników.</span><span class="sxs-lookup"><span data-stu-id="5d07c-359">Although WPF provides a host of customization support, you may encounter situations where existing WPF controls do not meet the needs of either your application or its users.</span></span> <span data-ttu-id="5d07c-360">Może się tak zdarzyć, gdy:</span><span class="sxs-lookup"><span data-stu-id="5d07c-360">This can occur when:</span></span>

- <span data-ttu-id="5d07c-361">Nie można utworzyć wymaganego interfejsu użytkownika przez dostosowanie wyglądu i sposobu działania istniejących implementacji WPF.</span><span class="sxs-lookup"><span data-stu-id="5d07c-361">The user interface that you require cannot be created by customizing the look and feel of existing WPF implementations.</span></span>

- <span data-ttu-id="5d07c-362">Wymagane zachowanie nie jest obsługiwane (lub nie jest obsługiwane w łatwy sposób) przez istniejące implementacje WPF.</span><span class="sxs-lookup"><span data-stu-id="5d07c-362">The behavior that you require is not supported (or not easily supported) by existing WPF implementations.</span></span>

<span data-ttu-id="5d07c-363">W tym momencie można jednak skorzystać z jednego z trzech modeli WPF, aby utworzyć nową kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="5d07c-363">At this point, however, you can take advantage of one of three WPF models to create a new control.</span></span> <span data-ttu-id="5d07c-364">Każdy model jest przeznaczony dla określonego scenariusza i wymaga, aby formant niestandardowy dziedziczył od określonej klasy bazowej WPF.</span><span class="sxs-lookup"><span data-stu-id="5d07c-364">Each model targets a specific scenario and requires your custom control to derive from a particular WPF base class.</span></span> <span data-ttu-id="5d07c-365">Trzy modele są wymienione tutaj:</span><span class="sxs-lookup"><span data-stu-id="5d07c-365">The three models are listed here:</span></span>

- <span data-ttu-id="5d07c-366">**Model kontroli użytkownika**.</span><span class="sxs-lookup"><span data-stu-id="5d07c-366">**User Control Model**.</span></span> <span data-ttu-id="5d07c-367">Kontrolka niestandardowa pochodzi z <xref:System.Windows.Controls.UserControl> i składa się z co najmniej jednej innej kontrolki.</span><span class="sxs-lookup"><span data-stu-id="5d07c-367">A custom control derives from <xref:System.Windows.Controls.UserControl> and is composed of one or more other controls.</span></span>

- <span data-ttu-id="5d07c-368">**Model sterowania**.</span><span class="sxs-lookup"><span data-stu-id="5d07c-368">**Control Model**.</span></span> <span data-ttu-id="5d07c-369">Kontrolka niestandardowa pochodzi z <xref:System.Windows.Controls.Control> i służy do kompilowania implementacji, które oddzielają ich zachowanie od ich wyglądu przy użyciu szablonów, podobnie jak większość formantów WPF.</span><span class="sxs-lookup"><span data-stu-id="5d07c-369">A custom control derives from <xref:System.Windows.Controls.Control> and is used to build implementations that separate their behavior from their appearance using templates, much like the majority of WPF controls.</span></span> <span data-ttu-id="5d07c-370">Wyprowadzanie z <xref:System.Windows.Controls.Control> pozwala na większą swobodę tworzenia niestandardowego interfejsu użytkownika niż kontrolki użytkownika, ale może to wymagać większej nakładu pracy.</span><span class="sxs-lookup"><span data-stu-id="5d07c-370">Deriving from <xref:System.Windows.Controls.Control> allows you more freedom for creating a custom user interface than user controls, but it may require more effort.</span></span>

- <span data-ttu-id="5d07c-371">**Model elementu struktury**.</span><span class="sxs-lookup"><span data-stu-id="5d07c-371">**Framework Element Model**.</span></span> <span data-ttu-id="5d07c-372">Kontrolka niestandardowa dziedziczy po <xref:System.Windows.FrameworkElement>, gdy jego wygląd jest zdefiniowany przez logikę renderowania niestandardowego (nie szablony).</span><span class="sxs-lookup"><span data-stu-id="5d07c-372">A custom control derives from <xref:System.Windows.FrameworkElement> when its appearance is defined by custom rendering logic (not templates).</span></span>

<span data-ttu-id="5d07c-373">Poniższy przykład przedstawia niestandardową kontrolkę Up/Down, która pochodzi od <xref:System.Windows.Controls.UserControl>:</span><span class="sxs-lookup"><span data-stu-id="5d07c-373">The following example shows a custom numeric up/down control that derives from <xref:System.Windows.Controls.UserControl>:</span></span>

[!code-xaml[IntroToWPFSnippets#UserControlMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_33.xaml)]

[!code-csharp[IntroToWPFSnippets#UserControlCODEBEHIND1](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_34.cs)]
[!code-vb[IntroToWPFSnippets#UserControlCODEBEHIND1](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_34.vb)]

<span data-ttu-id="5d07c-374">Poniższy przykład ilustruje kod XAML, który jest wymagany do uwzględnienia kontrolki użytkownika w <xref:System.Windows.Window>:</span><span class="sxs-lookup"><span data-stu-id="5d07c-374">The following example illustrates the XAML that is required to incorporate the user control into a <xref:System.Windows.Window>:</span></span>

[!code-xaml[IntroToWPFSnippets#UserControlWindowMARKUP1](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_37.xaml)]

<span data-ttu-id="5d07c-375">Na poniższej ilustracji przedstawiono kontrolkę `NumericUpDown` hostowaną w <xref:System.Windows.Window>:</span><span class="sxs-lookup"><span data-stu-id="5d07c-375">The following figure shows the `NumericUpDown` control hosted in a <xref:System.Windows.Window>:</span></span>

![Niestandardowy element UserControl](media/introduction-to-wpf/wpfintrofigure3.png)

<span data-ttu-id="5d07c-377">Aby uzyskać więcej informacji na temat kontrolek niestandardowych, zobacz temat [Tworzenie kontroli — Omówienie](controls/control-authoring-overview.md).</span><span class="sxs-lookup"><span data-stu-id="5d07c-377">For more information on custom controls, see [Control authoring overview](controls/control-authoring-overview.md).</span></span>

## <a name="wpf-best-practices"></a><span data-ttu-id="5d07c-378">Najlepsze rozwiązania dotyczące WPF</span><span class="sxs-lookup"><span data-stu-id="5d07c-378">WPF best practices</span></span>

<span data-ttu-id="5d07c-379">Podobnie jak w przypadku dowolnej platformy programistycznej, WPF można używać na wiele sposobów w celu osiągnięcia żądanego wyniku.</span><span class="sxs-lookup"><span data-stu-id="5d07c-379">As with any development platform, WPF can be used in a variety of ways to achieve the desired result.</span></span> <span data-ttu-id="5d07c-380">W celu upewnienia się, że aplikacje WPF zapewniają wymagane środowisko użytkownika i są ogólnie zgodne z wymaganiami odbiorców, zalecane są najlepsze rozwiązania dotyczące ułatwień dostępu, globalizacji i lokalizacji oraz wydajności.</span><span class="sxs-lookup"><span data-stu-id="5d07c-380">As a way of ensuring that your WPF applications provide the required user experience and meet the demands of the audience in general, there are recommended best practices for accessibility, globalization and localization, and performance.</span></span> <span data-ttu-id="5d07c-381">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="5d07c-381">For more information, see:</span></span>

- [<span data-ttu-id="5d07c-382">Ułatwienia dostępu</span><span class="sxs-lookup"><span data-stu-id="5d07c-382">Accessibility</span></span>](../ui-automation/accessibility-best-practices.md)
- [<span data-ttu-id="5d07c-383">Globalizacja i lokalizacja WPF</span><span class="sxs-lookup"><span data-stu-id="5d07c-383">WPF globalization and localization</span></span>](advanced/wpf-globalization-and-localization-overview.md)
- [<span data-ttu-id="5d07c-384">Wydajność aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="5d07c-384">WPF app performance</span></span>](advanced/optimizing-wpf-application-performance.md)
- [<span data-ttu-id="5d07c-385">Zabezpieczenia WPF</span><span class="sxs-lookup"><span data-stu-id="5d07c-385">WPF security</span></span>](security-wpf.md)

## <a name="next-steps"></a><span data-ttu-id="5d07c-386">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="5d07c-386">Next steps</span></span>

<span data-ttu-id="5d07c-387">Przeglądamy najważniejsze funkcje platformy WPF.</span><span class="sxs-lookup"><span data-stu-id="5d07c-387">We've looked at the key features of WPF.</span></span> <span data-ttu-id="5d07c-388">Teraz czas na skompilowanie pierwszej aplikacji WPF.</span><span class="sxs-lookup"><span data-stu-id="5d07c-388">Now it's time to build your first WPF app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5d07c-389">Przewodnik: moja pierwsza aplikacja klasyczna WPF</span><span class="sxs-lookup"><span data-stu-id="5d07c-389">Walkthrough: My first WPF desktop app</span></span>](getting-started/walkthrough-my-first-wpf-desktop-application.md)

## <a name="see-also"></a><span data-ttu-id="5d07c-390">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5d07c-390">See also</span></span>

- [<span data-ttu-id="5d07c-391">Rozpoczynanie pracy z aparatem WPF</span><span class="sxs-lookup"><span data-stu-id="5d07c-391">Get started with WPF</span></span>](getting-started/index.md)
- [<span data-ttu-id="5d07c-392">Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="5d07c-392">Windows Presentation Foundation</span></span>](index.md)
- [<span data-ttu-id="5d07c-393">Zasoby społeczności WPF</span><span class="sxs-lookup"><span data-stu-id="5d07c-393">WPF community resources</span></span>](getting-started/community-feedback.md)
