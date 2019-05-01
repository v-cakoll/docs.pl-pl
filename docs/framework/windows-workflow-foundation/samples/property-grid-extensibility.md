---
title: Rozszerzalność siatki właściwości — przykładowe WF
ms.date: 03/30/2017
ms.assetid: 3530c3a3-756d-4712-9f10-fb2897414d3a
ms.openlocfilehash: f1cb64cb10e8d88359e8f94b57602ab127314cff
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62004877"
---
# <a name="property-grid-extensibility"></a><span data-ttu-id="48bda-102">Rozszerzalność siatki właściwości</span><span class="sxs-lookup"><span data-stu-id="48bda-102">Property grid extensibility</span></span>

<span data-ttu-id="48bda-103">Deweloper może dostosować siatki właściwości, wyświetlanego po wybraniu danego działania w projektancie.</span><span class="sxs-lookup"><span data-stu-id="48bda-103">A developer can customize the property grid that is displayed when a given activity is selected within the designer.</span></span> <span data-ttu-id="48bda-104">Można to zrobić, aby utworzyć zaawansowane środowisko edycji.</span><span class="sxs-lookup"><span data-stu-id="48bda-104">This can be done to create a rich editing experience.</span></span> <span data-ttu-id="48bda-105">Niniejszy przykład pokazuje, jak można to zrobić.</span><span class="sxs-lookup"><span data-stu-id="48bda-105">This sample shows how this can be done.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="48bda-106">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="48bda-106">Demonstrates</span></span>

<span data-ttu-id="48bda-107">Rozszerzalność siatki właściwości projektanta przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="48bda-107">Workflow designer property grid extensibility.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="48bda-108">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="48bda-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="48bda-109">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="48bda-109">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="48bda-110">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="48bda-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="48bda-111">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="48bda-111">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\PropertyGridExtensibility`

## <a name="discussion"></a><span data-ttu-id="48bda-112">Dyskusja</span><span class="sxs-lookup"><span data-stu-id="48bda-112">Discussion</span></span>

<span data-ttu-id="48bda-113">Aby rozszerzyć siatki właściwości, deweloper ma opcje dostosowania wyglądu wbudowanego edytora siatki właściwości lub okno dialogowe, które pojawia się dla bardziej zaawansowanych powierzchni edycji.</span><span class="sxs-lookup"><span data-stu-id="48bda-113">To extend the property grid, a developer has options to customize the inline appearance of a property grid editor or provide a dialog that appears for a more advanced editing surface.</span></span> <span data-ttu-id="48bda-114">Istnieją dwa różne edytory przedstawiona w tym przykładzie; Edytor wbudowane i Edytor okien dialogowych.</span><span class="sxs-lookup"><span data-stu-id="48bda-114">There are two different editors demonstrated in this sample; an inline editor and a dialog editor.</span></span>

## <a name="inline-editor"></a><span data-ttu-id="48bda-115">Edytor wbudowane</span><span class="sxs-lookup"><span data-stu-id="48bda-115">Inline editor</span></span>

<span data-ttu-id="48bda-116">Przykład edytora wbudowane pokazuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="48bda-116">The inline editor sample demonstrates the following:</span></span>

- <span data-ttu-id="48bda-117">Tworzy typ, który pochodzi od klasy <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor>.</span><span class="sxs-lookup"><span data-stu-id="48bda-117">Creates a type that derives from <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor>.</span></span>

- <span data-ttu-id="48bda-118">W Konstruktorze <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> wartość została ustawiona za pomocą szablonu danych Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="48bda-118">In the constructor, the <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> value is set with a Windows Presentation Foundation (WPF) data template.</span></span> <span data-ttu-id="48bda-119">To może być powiązana z szablonem XAML, ale w tym przykładzie kodu służy do inicjowania powiązanie danych.</span><span class="sxs-lookup"><span data-stu-id="48bda-119">This can be bound to a XAML template, but in this sample, code is used to initialize data binding.</span></span>

- <span data-ttu-id="48bda-120">Szablon danych ma kontekstu danych <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> elementu renderowane w siatce właściwości.</span><span class="sxs-lookup"><span data-stu-id="48bda-120">The data template has a data context of the <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> of the item rendered in the property grid.</span></span> <span data-ttu-id="48bda-121">Uwaga w poniższym kodzie (z CustomInlineEditor.cs), który następnie powiąże tego kontekstu `Value` właściwości.</span><span class="sxs-lookup"><span data-stu-id="48bda-121">Note in the following code (from CustomInlineEditor.cs) that this context then binds to the `Value` property.</span></span>

    ```csharp
    FrameworkElementFactory stack = new FrameworkElementFactory(typeof(StackPanel));
    FrameworkElementFactory slider = new FrameworkElementFactory(typeof(Slider));
    Binding sliderBinding = new Binding("Value");
    sliderBinding.Mode = BindingMode.TwoWay;
    slider.SetValue(Slider.MinimumProperty, 0.0);
    slider.SetValue(Slider.MaximumProperty, 100.0);
    slider.SetValue(Slider.ValueProperty, sliderBinding);
    stack.AppendChild(slider);
    ```

- <span data-ttu-id="48bda-122">Ponieważ działania i Projektant znajdują się w tym samym zestawie, rejestracja atrybuty projektanta działań są realizowane w konstruktorze statycznym działania, jak pokazano w następującym przykładzie SimpleCodeActivity.cs.</span><span class="sxs-lookup"><span data-stu-id="48bda-122">Because the activity and the designer are in the same assembly, registration of the activity designer attributes are accomplished in the static constructor of the activity itself, as shown in the following example from SimpleCodeActivity.cs.</span></span>

    ```csharp
    static SimpleCodeActivity()
    {
        AttributeTableBuilder builder = new AttributeTableBuilder();
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "RepeatCount", new EditorAttribute(typeof(CustomInlineEditor), typeof(PropertyValueEditor)));
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "FileName", new EditorAttribute(typeof(FilePickerEditor), typeof(DialogPropertyValueEditor)));
        MetadataStore.AddAttributeTable(builder.CreateTable());
    }
    ```

## <a name="dialog-editor"></a><span data-ttu-id="48bda-123">edytor okien dialogowych</span><span class="sxs-lookup"><span data-stu-id="48bda-123">Dialog editor</span></span>

<span data-ttu-id="48bda-124">Przykład edytora okna dialogowego pokazuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="48bda-124">The dialog editor sample demonstrates the following:</span></span>

1. <span data-ttu-id="48bda-125">Tworzy typ, który pochodzi od klasy <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor>.</span><span class="sxs-lookup"><span data-stu-id="48bda-125">Creates a type that derives from <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor>.</span></span>

2. <span data-ttu-id="48bda-126">Zestawy <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> wartość w Konstruktorze z [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] szablon danych.</span><span class="sxs-lookup"><span data-stu-id="48bda-126">Sets the <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> value in the constructor with a [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] data template.</span></span> <span data-ttu-id="48bda-127">To mogą być tworzone w XAML, ale w tym przykładzie zostanie on utworzony w kodzie.</span><span class="sxs-lookup"><span data-stu-id="48bda-127">This can be created in XAML, but in this sample, this is created in code.</span></span>

3. <span data-ttu-id="48bda-128">Szablon danych ma kontekstu danych <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> elementu renderowane w siatce właściwości.</span><span class="sxs-lookup"><span data-stu-id="48bda-128">The data template has a data context of the <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> of the item rendered in the property grid.</span></span> <span data-ttu-id="48bda-129">W poniższym kodzie następnie powiąże `Value` właściwości.</span><span class="sxs-lookup"><span data-stu-id="48bda-129">In the following code, this then binds to the `Value` property.</span></span> <span data-ttu-id="48bda-130">Podstawowe znaczenie ma obejmować <xref:System.Activities.Presentation.PropertyEditing.EditModeSwitchButton> zapewnienie przycisk, który wywołuje okno dialogowe w FilePickerEditor.cs.</span><span class="sxs-lookup"><span data-stu-id="48bda-130">It is critical to also include an <xref:System.Activities.Presentation.PropertyEditing.EditModeSwitchButton> to provide the button that raises the dialog in FilePickerEditor.cs.</span></span>

    ```csharp
    this.InlineEditorTemplate = new DataTemplate();

    FrameworkElementFactory stack = new FrameworkElementFactory(typeof(StackPanel));
    stack.SetValue(StackPanel.OrientationProperty, Orientation.Horizontal);
    FrameworkElementFactory label = new FrameworkElementFactory(typeof(Label));
    Binding labelBinding = new Binding("Value");
    label.SetValue(Label.ContentProperty, labelBinding);
    label.SetValue(Label.MaxWidthProperty, 90.0);

    stack.AppendChild(label);

    FrameworkElementFactory editModeSwitch = new FrameworkElementFactory(typeof(EditModeSwitchButton));

    editModeSwitch.SetValue(EditModeSwitchButton.TargetEditModeProperty, PropertyContainerEditMode.Dialog);

    stack.AppendChild(editModeSwitch);

    this.InlineEditorTemplate.VisualTree = stack;
    ```

4. <span data-ttu-id="48bda-131">Zastępuje <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor.ShowDialog%2A> metoda w typie projektanta do obsługi wyświetlania okna dialogowego.</span><span class="sxs-lookup"><span data-stu-id="48bda-131">Overrides the <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor.ShowDialog%2A> method in the designer type to handle the display of the dialog.</span></span> <span data-ttu-id="48bda-132">W tym przykładzie podstawową <xref:System.Windows.Forms.FileDialog> jest wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="48bda-132">In this sample, a basic <xref:System.Windows.Forms.FileDialog> is shown.</span></span>

    ```csharp
    public override void ShowDialog(PropertyValue propertyValue, IInputElement commandSource)
    {
        Microsoft.Win32.OpenFileDialog ofd = new Microsoft.Win32.OpenFileDialog();
        if (ofd.ShowDialog() == true)
        {
            propertyValue.Value = ofd.FileName;
        }
    }
    ```

5. <span data-ttu-id="48bda-133">Ponieważ działania i Projektant znajdują się w tym samym zestawie, rejestracja atrybuty projektanta działań są realizowane w konstruktorze statycznym działania, jak pokazano w następującym przykładzie SimpleCodeActivity.cs.</span><span class="sxs-lookup"><span data-stu-id="48bda-133">Because the activity and the designer are in the same assembly, registration of the activity designer attributes are accomplished in the static constructor of the activity itself, as shown in the following example from SimpleCodeActivity.cs.</span></span>

    ```csharp
    static SimpleCodeActivity()
    {
        AttributeTableBuilder builder = new AttributeTableBuilder();
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "RepeatCount", new EditorAttribute(typeof(CustomInlineEditor), typeof(PropertyValueEditor)));
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "FileName", new EditorAttribute(typeof(FilePickerEditor), typeof(DialogPropertyValueEditor)));
        MetadataStore.AddAttributeTable(builder.CreateTable());
    }
    ```

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="48bda-134">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="48bda-134">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="48bda-135">Skompiluj rozwiązanie, a następnie otwórz Workflow1.xaml.</span><span class="sxs-lookup"><span data-stu-id="48bda-135">Build the solution, and then open Workflow1.xaml.</span></span>

2. <span data-ttu-id="48bda-136">Przeciągnij **SimpleCodeActivity** z przybornika na kanwie projektanta.</span><span class="sxs-lookup"><span data-stu-id="48bda-136">Drag a **SimpleCodeActivity** from the toolbox onto the designer canvas.</span></span>

3. <span data-ttu-id="48bda-137">Kliknij przycisk **SimpleCodeActivity** , a następnie otwórz siatki właściwości, gdy formant suwaka i plik pobrania kontroli.</span><span class="sxs-lookup"><span data-stu-id="48bda-137">Click the **SimpleCodeActivity** and then open the property grid where there is a slider control and a file picking control.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="48bda-138">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="48bda-138">The samples may already be installed on your machine.</span></span> <span data-ttu-id="48bda-139">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="48bda-139">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="48bda-140">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="48bda-140">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="48bda-141">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="48bda-141">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\PropertyGridExtensibility`