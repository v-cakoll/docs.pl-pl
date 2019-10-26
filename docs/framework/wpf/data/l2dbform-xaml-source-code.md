---
title: Kod źródłowy L2DBForm.xaml
ms.date: 10/22/2019
ms.topic: sample
ms.openlocfilehash: 290b00e136f0c49e1b27d4fa1bca7321eebe936e
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920945"
---
# <a name="l2dbformxaml-source-code"></a><span data-ttu-id="3a9f4-102">Kod źródłowy L2DBForm.xaml</span><span class="sxs-lookup"><span data-stu-id="3a9f4-102">L2DBForm.xaml source code</span></span>

<span data-ttu-id="3a9f4-103">Ta strona zawiera i opisuje plik źródłowy XAML dla [powiązania danych WPF przy użyciu przykładu LINQ to XML](linq-to-xml-data-binding-sample.md).</span><span class="sxs-lookup"><span data-stu-id="3a9f4-103">This page contains and describes the XAML source file for the [WPF data binding using LINQ to XML example](linq-to-xml-data-binding-sample.md).</span></span>

## <a name="overall-ui-structure"></a><span data-ttu-id="3a9f4-104">Ogólna struktura interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="3a9f4-104">Overall UI structure</span></span>

<span data-ttu-id="3a9f4-105">Podobnie jak w przypadku projektu WPF, ten plik zawiera jeden element nadrzędny, <xref:System.Windows.Window> element XML, który jest skojarzony z klasą pochodną `L2XDBFrom` w przestrzeni nazw `LinqToXmlDataBinding`.</span><span class="sxs-lookup"><span data-stu-id="3a9f4-105">As is typical for a WPF project, this file contains one parent element, a <xref:System.Windows.Window> XML element that's associated with the derived class `L2XDBFrom` in the `LinqToXmlDataBinding` namespace.</span></span>

<span data-ttu-id="3a9f4-106">Obszar klienta jest zawarty w <xref:System.Windows.Controls.StackPanel>, który ma jasnoniebieskie niebieskie tło.</span><span class="sxs-lookup"><span data-stu-id="3a9f4-106">The client area is contained within a <xref:System.Windows.Controls.StackPanel> that's given a light blue background.</span></span> <span data-ttu-id="3a9f4-107">Ten panel zawiera cztery <xref:System.Windows.Controls.DockPanel> sekcje interfejsu użytkownika oddzielone <xref:System.Windows.Controls.Separator> słupków.</span><span class="sxs-lookup"><span data-stu-id="3a9f4-107">This panel contains four <xref:System.Windows.Controls.DockPanel> UI sections separated by <xref:System.Windows.Controls.Separator> bars.</span></span> <span data-ttu-id="3a9f4-108">Celem tych sekcji opisano [tutaj](linq-to-xml-data-binding-sample.md#overview).</span><span class="sxs-lookup"><span data-stu-id="3a9f4-108">The purpose of these sections is described [here](linq-to-xml-data-binding-sample.md#overview).</span></span>

<span data-ttu-id="3a9f4-109">Każda sekcja zawiera etykietę identyfikującą ją.</span><span class="sxs-lookup"><span data-stu-id="3a9f4-109">Each section contains a label that identifies it.</span></span> <span data-ttu-id="3a9f4-110">W pierwszych dwóch sekcjach Ta etykieta jest obracana o 90 stopni przy użyciu <xref:System.Windows.FrameworkElement.LayoutTransform%2A>.</span><span class="sxs-lookup"><span data-stu-id="3a9f4-110">In the first two sections, this label is rotated 90 degrees through the use of a <xref:System.Windows.FrameworkElement.LayoutTransform%2A>.</span></span> <span data-ttu-id="3a9f4-111">Pozostała część sekcji zawiera elementy interfejsu użytkownika odpowiednie do przeznaczenia tej sekcji, na przykład bloki tekstu, pola tekstowe i przyciski.</span><span class="sxs-lookup"><span data-stu-id="3a9f4-111">The rest of the section contains UI elements appropriate to the purpose of that section, for example, text blocks, text boxes, and buttons.</span></span> <span data-ttu-id="3a9f4-112">Czasami podrzędny <xref:System.Windows.Controls.StackPanel> jest używany do wyrównywania tych formantów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="3a9f4-112">Sometimes a child <xref:System.Windows.Controls.StackPanel> is used to align these child controls.</span></span>

## <a name="window-resource-section"></a><span data-ttu-id="3a9f4-113">Sekcja zasobów okna</span><span class="sxs-lookup"><span data-stu-id="3a9f4-113">Window resource section</span></span>

<span data-ttu-id="3a9f4-114">Otwierając tag `<Window.Resources>` w wierszu 9 wskazuje początek sekcji zasobów okna.</span><span class="sxs-lookup"><span data-stu-id="3a9f4-114">The opening `<Window.Resources>` tag on line 9 indicates the start of the window resource section.</span></span> <span data-ttu-id="3a9f4-115">Jest ona kończąca się tagiem zamykającym w wierszu 35.</span><span class="sxs-lookup"><span data-stu-id="3a9f4-115">It ends with the closing tag on line 35.</span></span>

<span data-ttu-id="3a9f4-116">Znacznik `<ObjectDataProvider>`, który obejmuje wiersze od 11 do 25, deklaruje <xref:System.Windows.Data.ObjectDataProvider> o nazwie `LoadedBooks`, który używa <xref:System.Xml.Linq.XElement> jako źródła.</span><span class="sxs-lookup"><span data-stu-id="3a9f4-116">The `<ObjectDataProvider>` tag, which spans lines 11 through 25, declares a <xref:System.Windows.Data.ObjectDataProvider>, named `LoadedBooks`, that uses an <xref:System.Xml.Linq.XElement> as the source.</span></span> <span data-ttu-id="3a9f4-117"><xref:System.Xml.Linq.XElement> jest inicjowany przez analizowanie osadzonego dokumentu XML (`CDATA` elementu).</span><span class="sxs-lookup"><span data-stu-id="3a9f4-117">The <xref:System.Xml.Linq.XElement> is initialized by parsing an embedded XML document (a `CDATA` element).</span></span> <span data-ttu-id="3a9f4-118">Należy zauważyć, że biały znak jest zachowywany podczas deklarowania osadzonego dokumentu XML, a także podczas analizy.</span><span class="sxs-lookup"><span data-stu-id="3a9f4-118">Notice that white space is preserved when declaring the embedded XML document and also when it's parsed.</span></span> <span data-ttu-id="3a9f4-119">Biały znak jest zachowywany, ponieważ kontrolka <xref:System.Windows.Controls.TextBlock>, która jest używana do wyświetlania nieprzetworzonego kodu XML, nie ma specjalnych funkcji formatowania XML.</span><span class="sxs-lookup"><span data-stu-id="3a9f4-119">White space is preserved because the <xref:System.Windows.Controls.TextBlock> control, which is used to display the raw XML, has no special XML formatting capabilities.</span></span>

<span data-ttu-id="3a9f4-120">Na koniec <xref:System.Windows.DataTemplate> o nazwie `BookTemplate` jest zdefiniowany w wierszach od 28 do 34.</span><span class="sxs-lookup"><span data-stu-id="3a9f4-120">Lastly, a <xref:System.Windows.DataTemplate> named `BookTemplate` is defined on lines 28 through 34.</span></span> <span data-ttu-id="3a9f4-121">Ten szablon służy do wyświetlania wpisów w sekcji interfejsu użytkownika **listy książek** .</span><span class="sxs-lookup"><span data-stu-id="3a9f4-121">This template is used to display the entries in the **Book List** UI section.</span></span> <span data-ttu-id="3a9f4-122">Używa on powiązań danych i LINQ to XML właściwości dynamiczne, aby pobrać identyfikator i nazwę książki przy użyciu następujących przypisań:</span><span class="sxs-lookup"><span data-stu-id="3a9f4-122">It uses data binding and LINQ to XML dynamic properties to retrieve the book ID and book name through the following assignments:</span></span>

```xaml
Text="{Binding Path=Attribute[id].Value}"Text="{Binding Path=Value}"
```

## <a name="data-binding-code"></a><span data-ttu-id="3a9f4-123">Kod powiązania danych</span><span class="sxs-lookup"><span data-stu-id="3a9f4-123">Data binding code</span></span>

<span data-ttu-id="3a9f4-124">Oprócz elementu <xref:System.Windows.DataTemplate>, powiązanie danych jest używane w wielu innych miejscach w tym pliku.</span><span class="sxs-lookup"><span data-stu-id="3a9f4-124">In addition to the <xref:System.Windows.DataTemplate> element, data binding is used in a number of other places in this file.</span></span>

<span data-ttu-id="3a9f4-125">W tagu `<StackPanel>` otwierającym w wierszu 38 Właściwość <xref:System.Windows.FrameworkElement.DataContext%2A> tego panelu jest ustawiona na dostawcę danych `LoadedBooks`.</span><span class="sxs-lookup"><span data-stu-id="3a9f4-125">In the opening `<StackPanel>` tag on line 38, the <xref:System.Windows.FrameworkElement.DataContext%2A> property of this panel is set to the `LoadedBooks` data provider.</span></span>

```xaml
DataContext="{Binding Source={StaticResource LoadedBooks}}
```

<span data-ttu-id="3a9f4-126">Ustawienie kontekstu danych sprawia, że jest to możliwe (w wierszu 46) dla <xref:System.Windows.Controls.TextBlock> o nazwie `tbRawXml` do wyświetlania nieprzetworzonego kodu XML przez powiązanie z właściwością `Xml` tego dostawcy danych:</span><span class="sxs-lookup"><span data-stu-id="3a9f4-126">Setting the data context makes it possible (on line 46) for the <xref:System.Windows.Controls.TextBlock> named `tbRawXml` to display the raw XML by binding to this data provider's `Xml` property:</span></span>

```xaml
Text="{Binding Path=Xml}"
```

<span data-ttu-id="3a9f4-127"><xref:System.Windows.Controls.ListBox> w sekcji interfejsu użytkownika **listy książek** , w wierszach od 58 do 62, ustawia szablon dla elementów wyświetlanych na `BookTemplate` zdefiniowany w sekcji zasobów okna:</span><span class="sxs-lookup"><span data-stu-id="3a9f4-127">The <xref:System.Windows.Controls.ListBox> in the **Book List** UI section, on lines 58 through 62, sets the template for its display items to the `BookTemplate` defined in the window resource section:</span></span>

```xaml
ItemTemplate ="{StaticResource BookTemplate}"
```

<span data-ttu-id="3a9f4-128">Następnie w wierszach od 59 do 62 rzeczywiste wartości ksiąg są powiązane z tym polem listy:</span><span class="sxs-lookup"><span data-stu-id="3a9f4-128">Then, on lines 59 through 62, the actual values of the books are bound to this list box:</span></span>

```xaml
<ListBox.ItemsSource>
    <Binding Path="Elements[{http://www.mybooks.com}book]"/>
</ListBox.ItemsSource>
```

<span data-ttu-id="3a9f4-129">Trzecia sekcja interfejsu użytkownika, **Edytuj wybraną książkę**, najpierw wiąże <xref:System.Windows.FrameworkElement.DataContext%2A> nadrzędnej <xref:System.Windows.Controls.StackPanel> z aktualnie wybranym elementem w sekcji z poziomu interfejsu użytkownika **listy książek** (wiersz 82):</span><span class="sxs-lookup"><span data-stu-id="3a9f4-129">The third UI section, **Edit Selected Book**, first binds the <xref:System.Windows.FrameworkElement.DataContext%2A> of the parent <xref:System.Windows.Controls.StackPanel> to the currently selected item in from the **Book List** UI section (line 82):</span></span>

```xaml
DataContext="{Binding ElementName=lbBooks, Path=SelectedItem}"
```

<span data-ttu-id="3a9f4-130">Następnie używa dwukierunkowego wiązania danych, dzięki czemu bieżące wartości elementów książki są wyświetlane do i aktualizowane z, dwa pola tekstowe na tym panelu.</span><span class="sxs-lookup"><span data-stu-id="3a9f4-130">It then uses two-way data binding, so that the current values of the book elements are displayed to, and updated from, the two text boxes in this panel.</span></span> <span data-ttu-id="3a9f4-131">Powiązanie danych z właściwościami dynamicznymi jest podobne do powiązania danych używanego w szablonie danych `BookTemplate`:</span><span class="sxs-lookup"><span data-stu-id="3a9f4-131">Data binding to dynamic properties is similar to the data binding used in the `BookTemplate` data template:</span></span>

```xaml
Text="{Binding Path=Attribute[id].Value}"...Text="{Binding Path=Value}"
```

<span data-ttu-id="3a9f4-132">Ostatnia sekcja interfejsu użytkownika, **Dodaj nową książkę**, nie używa powiązania danych w kodzie XAML.</span><span class="sxs-lookup"><span data-stu-id="3a9f4-132">The last UI section, **Add New Book**, doesn't use data binding in its XAML code.</span></span> <span data-ttu-id="3a9f4-133">Zamiast tego powiązanie danych znajduje się w kodzie obsługi zdarzeń w pliku *L2DBForm.XAML.cs*.</span><span class="sxs-lookup"><span data-stu-id="3a9f4-133">Instead, data binding is in its event handling code in the file *L2DBForm.xaml.cs*.</span></span>

## <a name="example"></a><span data-ttu-id="3a9f4-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="3a9f4-134">Example</span></span>

### <a name="description"></a><span data-ttu-id="3a9f4-135">Opis</span><span class="sxs-lookup"><span data-stu-id="3a9f4-135">Description</span></span>

> [!NOTE]
> <span data-ttu-id="3a9f4-136">Zalecamy skopiowanie poniższego kodu do edytora kodu, takiego jak edytor kodu C# źródłowego w programie Visual Studio, dzięki czemu numery wierszy będą łatwiejsze do śledzenia.</span><span class="sxs-lookup"><span data-stu-id="3a9f4-136">We recommend that you copy the following code below into a code editor, such as the C# source code editor in Visual Studio, so that line numbers will be easier to track.</span></span>

### <a name="code"></a><span data-ttu-id="3a9f4-137">Kod</span><span class="sxs-lookup"><span data-stu-id="3a9f4-137">Code</span></span>

```xml
<Window x:Class="LinqToXmlDataBinding.L2XDBForm"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:system="clr-namespace:System;assembly=mscorlib"
    xmlns:xlinq="clr-namespace:System.Xml.Linq;assembly=System.Xml.Linq"
    xmlns:local="clr-namespace:LinqToXmlDataBinding"
    Title="WPF Data Binding using LINQ-to-XML" Height="665" Width="500" ResizeMode="NoResize">

    <Window.Resources>
        <!-- Books provider and inline data -->
        <ObjectDataProvider x:Key="LoadedBooks" ObjectType="{x:Type xlinq:XElement}" MethodName="Parse">
            <ObjectDataProvider.MethodParameters>
                <system:String xml:space="preserve">
<![CDATA[
<books xmlns="http://www.mybooks.com">
  <book id="0">book zero</book>
  <book id="1">book one</book>
  <book id="2">book two</book>
  <book id="3">book three</book>
</books>
]]>
                </system:String>
                <xlinq:LoadOptions>PreserveWhitespace</xlinq:LoadOptions>
            </ObjectDataProvider.MethodParameters>
        </ObjectDataProvider>

        <!-- Template for use in Books List listbox. -->
        <DataTemplate x:Key="BookTemplate">
            <StackPanel Orientation="Horizontal">
                <TextBlock Margin="3" Text="{Binding Path=Attribute[id].Value}"/>
                <TextBlock Margin="3" Text="-"/>
                <TextBlock Margin="3" Text="{Binding Path=Value}"/>
            </StackPanel>
        </DataTemplate>
    </Window.Resources>

    <!-- Main visual content container -->
    <StackPanel Background="lightblue" DataContext="{Binding Source={StaticResource LoadedBooks}}">
        <!-- Raw XML display section -->
        <DockPanel Margin="5">
            <Label  Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" FontWeight="Bold">XML
            <Label.LayoutTransform>
                <RotateTransform Angle="90"/>
            </Label.LayoutTransform>
            </Label>
            <TextBlock Name="tbRawXml" Height="200" Background="LightGray" Text="{Binding Path=Xml}" TextTrimming="CharacterEllipsis" />
        </DockPanel>

        <Separator Height="4" Margin="5" />

        <!-- List box to display all books section -->
        <DockPanel Margin="5">
            <Label  Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" FontWeight="Bold">Book List
                <Label.LayoutTransform>
                    <RotateTransform Angle="90"/>
                </Label.LayoutTransform>
            </Label>
            <ListBox Name="lbBooks" Height="200" Width="415" ItemTemplate ="{StaticResource BookTemplate}">
                <ListBox.ItemsSource>
                    <Binding Path="Elements[{http://www.mybooks.com}book]"/>
                </ListBox.ItemsSource>
            </ListBox>
            <Button Margin="5" DockPanel.Dock="Right" Height="30" Width ="130" Content="Remove Selected Book" Click="OnRemoveBook">
            <Button.LayoutTransform>
                <RotateTransform Angle="90"/>
            </Button.LayoutTransform>
            </Button>
        </DockPanel>

        <Separator Height="4" Margin="5" />

        <!-- Edit current selection section -->
        <DockPanel Margin="5">
            <TextBlock Margin="5" Height="30" Width="65" DockPanel.Dock="Right" Background="LightGray" TextWrapping="Wrap" TextAlignment="Center">
                    Changes are live!
                <TextBlock.LayoutTransform>
                    <RotateTransform Angle="90"/>
                </TextBlock.LayoutTransform>
            </TextBlock>
            <StackPanel>
                <Label Width="450" Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" HorizontalAlignment="Left" FontWeight="Bold">Edit Selected Book</Label>
                <StackPanel Margin="1" DataContext="{Binding ElementName=lbBooks, Path=SelectedItem}">
                    <StackPanel Orientation="Horizontal">
                        <Label Width="40">ID:</Label>
                        <TextBox Name="editAttributeTextBox" Width="410" Text="{Binding Path=Attribute[id].Value}">
                            <TextBox.ToolTip>
                                <TextBlock FontWeight="Bold" TextAlignment="Center">
                                    <Label>Edit the selected book ID and see it changed.</Label>
                                </TextBlock>
                            </TextBox.ToolTip>
                        </TextBox>
                    </StackPanel>
                    <StackPanel Orientation="Horizontal">
                        <Label Width="40">Value:</Label>
                        <TextBox Name="editValueTextBox" Width="410" Text="{Binding Path=Value}" Height="25">
                            <TextBox.ToolTip>
                                <TextBlock FontWeight="Bold" TextAlignment="Center">
                                    <Label>Edit the selected book Value and see it changed.</Label>
                                </TextBlock>
                            </TextBox.ToolTip>
                        </TextBox>
                    </StackPanel>
                </StackPanel>
            </StackPanel>
        </DockPanel>

        <Separator Height="4" Margin="5" />

        <!-- Add new book section -->
        <DockPanel Margin="5">
            <Button Margin="5" Height="30" DockPanel.Dock="Right" Click ="OnAddBook">Add Book
                <Button.LayoutTransform>
                    <RotateTransform Angle="90"/>
                </Button.LayoutTransform>
            </Button>
            <StackPanel>
                <Label Width="450" Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" HorizontalAlignment="Left" FontWeight="Bold">Add New Book</Label>
                <StackPanel Margin="1">
                    <StackPanel Orientation="Horizontal">
                        <Label Width="40">ID:</Label>
                        <TextBox Name="tbAddID" Width="410">
                            <TextBox.ToolTip>
                                <TextBlock FontWeight="Bold" TextAlignment="Center">
                                    <Label>Enter a book ID and Value pair, then click Add Book.</Label>
                                </TextBlock>
                            </TextBox.ToolTip>
                        </TextBox>
                    </StackPanel>
                    <StackPanel Orientation="Horizontal">
                        <Label Width="40">Value:</Label>
                        <TextBox Name="tbAddValue" Width="410" Height="25">
                            <TextBox.ToolTip>
                                <TextBlock FontWeight="UltraBold" TextAlignment="Center">
                                    <Label>Enter a book ID and Value pair, then click Add Book.</Label>
                                </TextBlock>
                            </TextBox.ToolTip>
                        </TextBox>
                    </StackPanel>
                </StackPanel>
            </StackPanel>
        </DockPanel>
    </StackPanel>
</Window>
```

### <a name="comments"></a><span data-ttu-id="3a9f4-138">Komentarze</span><span class="sxs-lookup"><span data-stu-id="3a9f4-138">Comments</span></span>

<span data-ttu-id="3a9f4-139">W przypadku C# kodu źródłowego dla programów obsługi zdarzeń skojarzonych z elementami interfejsu użytkownika WPF zobacz [kod źródłowy L2DBForm.XAML.cs](l2dbform-xaml-cs-source-code.md).</span><span class="sxs-lookup"><span data-stu-id="3a9f4-139">For the C# source code for the event handlers associated with the WPF UI elements, see [L2DBForm.xaml.cs source code](l2dbform-xaml-cs-source-code.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3a9f4-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3a9f4-140">See also</span></span>

- [<span data-ttu-id="3a9f4-141">Przewodnik: elementu LinqToXmlDataBinding — przykład</span><span class="sxs-lookup"><span data-stu-id="3a9f4-141">Walkthrough: LinqToXmlDataBinding example</span></span>](linq-to-xml-data-binding-sample.md)
- [<span data-ttu-id="3a9f4-142">Kod źródłowy L2DBForm.xaml.cs</span><span class="sxs-lookup"><span data-stu-id="3a9f4-142">L2DBForm.xaml.cs source code</span></span>](l2dbform-xaml-cs-source-code.md)
