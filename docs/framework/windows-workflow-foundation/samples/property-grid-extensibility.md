---
title: Rozszerzalność siatki właściwości — przykład WF
ms.date: 03/30/2017
ms.assetid: 3530c3a3-756d-4712-9f10-fb2897414d3a
ms.openlocfilehash: 130d8702795bccf0d5f28b5c0940bd7c25be3556
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715603"
---
# <a name="property-grid-extensibility"></a><span data-ttu-id="7efbb-102">Rozszerzalność siatki właściwości</span><span class="sxs-lookup"><span data-stu-id="7efbb-102">Property grid extensibility</span></span>

<span data-ttu-id="7efbb-103">Deweloper może dostosować siatkę właściwości, która jest wyświetlana po wybraniu danego działania w projektancie.</span><span class="sxs-lookup"><span data-stu-id="7efbb-103">A developer can customize the property grid that is displayed when a given activity is selected within the designer.</span></span> <span data-ttu-id="7efbb-104">Można to zrobić, aby utworzyć bogate środowisko edycji.</span><span class="sxs-lookup"><span data-stu-id="7efbb-104">This can be done to create a rich editing experience.</span></span> <span data-ttu-id="7efbb-105">Ten przykład pokazuje, jak można to zrobić.</span><span class="sxs-lookup"><span data-stu-id="7efbb-105">This sample shows how this can be done.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="7efbb-106">Przedstawia</span><span class="sxs-lookup"><span data-stu-id="7efbb-106">Demonstrates</span></span>

<span data-ttu-id="7efbb-107">Rozszerzalność siatki właściwości projektanta przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="7efbb-107">Workflow designer property grid extensibility.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7efbb-108">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="7efbb-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7efbb-109">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="7efbb-109">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="7efbb-110">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7efbb-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7efbb-111">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="7efbb-111">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\PropertyGridExtensibility`

## <a name="discussion"></a><span data-ttu-id="7efbb-112">Dyskusji</span><span class="sxs-lookup"><span data-stu-id="7efbb-112">Discussion</span></span>

<span data-ttu-id="7efbb-113">Aby można było rozwinąć siatkę właściwości, deweloper ma opcje umożliwiające dostosowanie wbudowanego elementu edytora siatki właściwości lub wyświetlenie okna dialogowego, które jest wyświetlane dla bardziej zaawansowanej powierzchni edycji.</span><span class="sxs-lookup"><span data-stu-id="7efbb-113">To extend the property grid, a developer has options to customize the inline appearance of a property grid editor or provide a dialog that appears for a more advanced editing surface.</span></span> <span data-ttu-id="7efbb-114">W tym przykładzie przedstawiono dwa różne edytory: Edytor wbudowany i Edytor okna dialogowego.</span><span class="sxs-lookup"><span data-stu-id="7efbb-114">There are two different editors demonstrated in this sample; an inline editor and a dialog editor.</span></span>

## <a name="inline-editor"></a><span data-ttu-id="7efbb-115">Edytor wbudowany</span><span class="sxs-lookup"><span data-stu-id="7efbb-115">Inline editor</span></span>

<span data-ttu-id="7efbb-116">W przykładzie edytora wbudowanego zademonstrowano następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="7efbb-116">The inline editor sample demonstrates the following:</span></span>

- <span data-ttu-id="7efbb-117">Tworzy typ, który pochodzi od <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor>.</span><span class="sxs-lookup"><span data-stu-id="7efbb-117">Creates a type that derives from <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor>.</span></span>

- <span data-ttu-id="7efbb-118">W konstruktorze wartość <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> jest ustawiana za pomocą szablonu danych Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="7efbb-118">In the constructor, the <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> value is set with a Windows Presentation Foundation (WPF) data template.</span></span> <span data-ttu-id="7efbb-119">Może to być powiązane z szablonem XAML, ale w tym przykładzie kod jest używany do inicjowania powiązania danych.</span><span class="sxs-lookup"><span data-stu-id="7efbb-119">This can be bound to a XAML template, but in this sample, code is used to initialize data binding.</span></span>

- <span data-ttu-id="7efbb-120">Szablon danych zawiera kontekst danych <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> elementu renderowanego w siatce właściwości.</span><span class="sxs-lookup"><span data-stu-id="7efbb-120">The data template has a data context of the <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> of the item rendered in the property grid.</span></span> <span data-ttu-id="7efbb-121">Zwróć uwagę na następujący kod (z CustomInlineEditor.cs), który następnie tworzy powiązanie z właściwością `Value`.</span><span class="sxs-lookup"><span data-stu-id="7efbb-121">Note in the following code (from CustomInlineEditor.cs) that this context then binds to the `Value` property.</span></span>

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

- <span data-ttu-id="7efbb-122">Ponieważ działanie i Projektant znajdują się w tym samym zestawie, rejestracja atrybutów projektanta działań jest realizowana w konstruktorze statycznym działania, jak pokazano w poniższym przykładzie z SimpleCodeActivity.cs.</span><span class="sxs-lookup"><span data-stu-id="7efbb-122">Because the activity and the designer are in the same assembly, registration of the activity designer attributes are accomplished in the static constructor of the activity itself, as shown in the following example from SimpleCodeActivity.cs.</span></span>

    ```csharp
    static SimpleCodeActivity()
    {
        AttributeTableBuilder builder = new AttributeTableBuilder();
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "RepeatCount", new EditorAttribute(typeof(CustomInlineEditor), typeof(PropertyValueEditor)));
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "FileName", new EditorAttribute(typeof(FilePickerEditor), typeof(DialogPropertyValueEditor)));
        MetadataStore.AddAttributeTable(builder.CreateTable());
    }
    ```

## <a name="dialog-editor"></a><span data-ttu-id="7efbb-123">edytor okien dialogowych</span><span class="sxs-lookup"><span data-stu-id="7efbb-123">Dialog editor</span></span>

<span data-ttu-id="7efbb-124">W przykładzie edytora okien dialogowych przedstawiono następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="7efbb-124">The dialog editor sample demonstrates the following:</span></span>

1. <span data-ttu-id="7efbb-125">Tworzy typ, który pochodzi od <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor>.</span><span class="sxs-lookup"><span data-stu-id="7efbb-125">Creates a type that derives from <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor>.</span></span>

2. <span data-ttu-id="7efbb-126">Ustawia wartość <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> w konstruktorze z szablonem danych WPF.</span><span class="sxs-lookup"><span data-stu-id="7efbb-126">Sets the <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> value in the constructor with a WPF data template.</span></span> <span data-ttu-id="7efbb-127">Tę opcję można utworzyć w języku XAML, ale w tym przykładzie jest to tworzone w kodzie.</span><span class="sxs-lookup"><span data-stu-id="7efbb-127">This can be created in XAML, but in this sample, this is created in code.</span></span>

3. <span data-ttu-id="7efbb-128">Szablon danych zawiera kontekst danych <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> elementu renderowanego w siatce właściwości.</span><span class="sxs-lookup"><span data-stu-id="7efbb-128">The data template has a data context of the <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> of the item rendered in the property grid.</span></span> <span data-ttu-id="7efbb-129">W poniższym kodzie, następnie tworzy powiązanie z właściwością `Value`.</span><span class="sxs-lookup"><span data-stu-id="7efbb-129">In the following code, this then binds to the `Value` property.</span></span> <span data-ttu-id="7efbb-130">Należy również uwzględnić <xref:System.Activities.Presentation.PropertyEditing.EditModeSwitchButton>, aby udostępnić przycisk, który wywołuje okno dialogowe w FilePickerEditor.cs.</span><span class="sxs-lookup"><span data-stu-id="7efbb-130">It is critical to also include an <xref:System.Activities.Presentation.PropertyEditing.EditModeSwitchButton> to provide the button that raises the dialog in FilePickerEditor.cs.</span></span>

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

4. <span data-ttu-id="7efbb-131">Zastępuje metodę <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor.ShowDialog%2A> w typie projektanta, aby obsłużyć wyświetlanie okna dialogowego.</span><span class="sxs-lookup"><span data-stu-id="7efbb-131">Overrides the <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor.ShowDialog%2A> method in the designer type to handle the display of the dialog.</span></span> <span data-ttu-id="7efbb-132">W tym przykładzie jest pokazywana podstawowa <xref:System.Windows.Forms.FileDialog>.</span><span class="sxs-lookup"><span data-stu-id="7efbb-132">In this sample, a basic <xref:System.Windows.Forms.FileDialog> is shown.</span></span>

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

5. <span data-ttu-id="7efbb-133">Ponieważ działanie i Projektant znajdują się w tym samym zestawie, rejestracja atrybutów projektanta działań jest realizowana w konstruktorze statycznym działania, jak pokazano w poniższym przykładzie z SimpleCodeActivity.cs.</span><span class="sxs-lookup"><span data-stu-id="7efbb-133">Because the activity and the designer are in the same assembly, registration of the activity designer attributes are accomplished in the static constructor of the activity itself, as shown in the following example from SimpleCodeActivity.cs.</span></span>

    ```csharp
    static SimpleCodeActivity()
    {
        AttributeTableBuilder builder = new AttributeTableBuilder();
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "RepeatCount", new EditorAttribute(typeof(CustomInlineEditor), typeof(PropertyValueEditor)));
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "FileName", new EditorAttribute(typeof(FilePickerEditor), typeof(DialogPropertyValueEditor)));
        MetadataStore.AddAttributeTable(builder.CreateTable());
    }
    ```

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7efbb-134">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="7efbb-134">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="7efbb-135">Skompiluj rozwiązanie, a następnie otwórz Workflow1. XAML.</span><span class="sxs-lookup"><span data-stu-id="7efbb-135">Build the solution, and then open Workflow1.xaml.</span></span>

2. <span data-ttu-id="7efbb-136">Przeciągnij **SimpleCodeActivity** z przybornika na kanwę projektanta.</span><span class="sxs-lookup"><span data-stu-id="7efbb-136">Drag a **SimpleCodeActivity** from the toolbox onto the designer canvas.</span></span>

3. <span data-ttu-id="7efbb-137">Kliknij **SimpleCodeActivity** , a następnie otwórz siatkę właściwości, w której znajduje się kontrolka suwaka i formant wyboru pliku.</span><span class="sxs-lookup"><span data-stu-id="7efbb-137">Click the **SimpleCodeActivity** and then open the property grid where there is a slider control and a file picking control.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7efbb-138">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="7efbb-138">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7efbb-139">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="7efbb-139">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="7efbb-140">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7efbb-140">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7efbb-141">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="7efbb-141">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\PropertyGridExtensibility`
