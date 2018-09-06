---
title: Rozszerzalność siatki właściwości
ms.date: 03/30/2017
ms.assetid: 3530c3a3-756d-4712-9f10-fb2897414d3a
ms.openlocfilehash: b7c3e3dbc3ccd95fc12dffd40927b3e2bbbc8226
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43779302"
---
# <a name="property-grid-extensibliity"></a><span data-ttu-id="4abd4-102">Rozszerzalność siatki właściwości</span><span class="sxs-lookup"><span data-stu-id="4abd4-102">Property Grid Extensibliity</span></span>
<span data-ttu-id="4abd4-103">Deweloper może dostosować siatki właściwości, wyświetlanego po wybraniu danego działania w projektancie.</span><span class="sxs-lookup"><span data-stu-id="4abd4-103">A developer can customize the property grid that is displayed when a given activity is selected within the designer.</span></span> <span data-ttu-id="4abd4-104">Można to zrobić, aby utworzyć zaawansowane środowisko edycji.</span><span class="sxs-lookup"><span data-stu-id="4abd4-104">This can be done to create a rich editing experience.</span></span> <span data-ttu-id="4abd4-105">Niniejszy przykład pokazuje, jak można to zrobić.</span><span class="sxs-lookup"><span data-stu-id="4abd4-105">This sample shows how this can be done.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="4abd4-106">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="4abd4-106">Demonstrates</span></span>  
 <span data-ttu-id="4abd4-107">Rozszerzalność siatki właściwości projektanta przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="4abd4-107">Workflow designer property grid extensibility.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4abd4-108">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="4abd4-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4abd4-109">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="4abd4-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4abd4-110">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="4abd4-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4abd4-111">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="4abd4-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\PropertyGridExtensibility`  
  
## <a name="discussion"></a><span data-ttu-id="4abd4-112">Dyskusja</span><span class="sxs-lookup"><span data-stu-id="4abd4-112">Discussion</span></span>  
 <span data-ttu-id="4abd4-113">Aby rozszerzyć siatki właściwości, deweloper ma opcje dostosowania wyglądu wbudowanego edytora siatki właściwości lub okno dialogowe, które pojawia się dla bardziej zaawansowanych powierzchni edycji.</span><span class="sxs-lookup"><span data-stu-id="4abd4-113">To extend the property grid, a developer has options to customize the inline appearance of a property grid editor or provide a dialog that appears for a more advanced editing surface.</span></span> <span data-ttu-id="4abd4-114">Istnieją dwa różne edytory przedstawiona w tym przykładzie; Edytor wbudowane i Edytor okien dialogowych.</span><span class="sxs-lookup"><span data-stu-id="4abd4-114">There are two different editors demonstrated in this sample; an inline editor and a dialog editor.</span></span>  
  
## <a name="inline-editor"></a><span data-ttu-id="4abd4-115">Edytor wbudowane</span><span class="sxs-lookup"><span data-stu-id="4abd4-115">Inline Editor</span></span>  
 <span data-ttu-id="4abd4-116">Przykład edytora wbudowane pokazuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="4abd4-116">The inline editor sample demonstrates the following:</span></span>  
  
-   <span data-ttu-id="4abd4-117">Tworzy typ, który pochodzi od klasy <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor>.</span><span class="sxs-lookup"><span data-stu-id="4abd4-117">Creates a type that derives from <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor>.</span></span>  
  
-   <span data-ttu-id="4abd4-118">W Konstruktorze <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> wartość została ustawiona za pomocą szablonu danych Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="4abd4-118">In the constructor, the <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> value is set with a Windows Presentation Foundation (WPF) data template.</span></span> <span data-ttu-id="4abd4-119">To może być powiązana z szablonem XAML, ale w tym przykładzie kodu służy do inicjowania powiązanie danych.</span><span class="sxs-lookup"><span data-stu-id="4abd4-119">This can be bound to a XAML template, but in this sample, code is used to initialize data binding.</span></span>  
  
-   <span data-ttu-id="4abd4-120">Szablon danych ma kontekstu danych <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> elementu renderowane w siatce właściwości.</span><span class="sxs-lookup"><span data-stu-id="4abd4-120">The data template has a data context of the <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> of the item rendered in the property grid.</span></span> <span data-ttu-id="4abd4-121">Uwaga w poniższym kodzie (z CustomInlineEditor.cs), który następnie powiąże tego kontekstu `Value` właściwości.</span><span class="sxs-lookup"><span data-stu-id="4abd4-121">Note in the following code (from CustomInlineEditor.cs) that this context then binds to the `Value` property.</span></span>  
  
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
  
-   <span data-ttu-id="4abd4-122">Ponieważ działania i Projektant znajdują się w tym samym zestawie, rejestracja atrybuty projektanta działań są realizowane w konstruktorze statycznym działania, jak pokazano w następującym przykładzie SimpleCodeActivity.cs.</span><span class="sxs-lookup"><span data-stu-id="4abd4-122">Because the activity and the designer are in the same assembly, registration of the activity designer attributes are accomplished in the static constructor of the activity itself, as shown in the following example from SimpleCodeActivity.cs.</span></span>  
  
    ```  
    static SimpleCodeActivity()  
    {  
        AttributeTableBuilder builder = new AttributeTableBuilder();  
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "RepeatCount", new EditorAttribute(typeof(CustomInlineEditor), typeof(PropertyValueEditor)));  
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "FileName", new EditorAttribute(typeof(FilePickerEditor), typeof(DialogPropertyValueEditor)));  
        MetadataStore.AddAttributeTable(builder.CreateTable());  
    }  
    ```  
  
## <a name="dialog-editor"></a><span data-ttu-id="4abd4-123">Edytor okien dialogowych</span><span class="sxs-lookup"><span data-stu-id="4abd4-123">Dialog Editor</span></span>  
 <span data-ttu-id="4abd4-124">Przykład edytora okna dialogowego pokazuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="4abd4-124">The dialog editor sample demonstrates the following:</span></span>  
  
1.  <span data-ttu-id="4abd4-125">Tworzy typ, który pochodzi od klasy <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor>.</span><span class="sxs-lookup"><span data-stu-id="4abd4-125">Creates a type that derives from <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor>.</span></span>  
  
2.  <span data-ttu-id="4abd4-126">Zestawy <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> wartość w Konstruktorze z [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] szablon danych.</span><span class="sxs-lookup"><span data-stu-id="4abd4-126">Sets the <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> value in the constructor with a [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] data template.</span></span> <span data-ttu-id="4abd4-127">To mogą być tworzone w XAML, ale w tym przykładzie zostanie on utworzony w kodzie.</span><span class="sxs-lookup"><span data-stu-id="4abd4-127">This can be created in XAML, but in this sample, this is created in code.</span></span>  
  
3.  <span data-ttu-id="4abd4-128">Szablon danych ma kontekstu danych <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> elementu renderowane w siatce właściwości.</span><span class="sxs-lookup"><span data-stu-id="4abd4-128">The data template has a data context of the <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> of the item rendered in the property grid.</span></span> <span data-ttu-id="4abd4-129">W poniższym kodzie następnie powiąże `Value` właściwości.</span><span class="sxs-lookup"><span data-stu-id="4abd4-129">In the following code, this then binds to the `Value` property.</span></span> <span data-ttu-id="4abd4-130">Podstawowe znaczenie ma obejmować <xref:System.Activities.Presentation.PropertyEditing.EditModeSwitchButton> zapewnienie przycisk, który wywołuje okno dialogowe w FilePickerEditor.cs.</span><span class="sxs-lookup"><span data-stu-id="4abd4-130">It is critical to also include an <xref:System.Activities.Presentation.PropertyEditing.EditModeSwitchButton> to provide the button that raises the dialog in FilePickerEditor.cs.</span></span>  
  
    ```  
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
  
4.  <span data-ttu-id="4abd4-131">Zastępuje <!--zz <xref:Microsoft.Windows.Design.PropertyEditing.ShowDialog%2A>--> `Microsoft.Windows.Design.PropertyEditing.ShowDialog` metoda w typie projektanta do obsługi wyświetlania okna dialogowego.</span><span class="sxs-lookup"><span data-stu-id="4abd4-131">Overrides the <!--zz <xref:Microsoft.Windows.Design.PropertyEditing.ShowDialog%2A>--> `Microsoft.Windows.Design.PropertyEditing.ShowDialog` method in the designer type to handle the display of the dialog.</span></span> <span data-ttu-id="4abd4-132">W tym przykładzie podstawową <xref:System.Windows.Forms.FileDialog> jest wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="4abd4-132">In this sample, a basic <xref:System.Windows.Forms.FileDialog> is shown.</span></span>  
  
    ```  
    public override void ShowDialog(PropertyValue propertyValue, IInputElement commandSource)  
    {  
        Microsoft.Win32.OpenFileDialog ofd = new Microsoft.Win32.OpenFileDialog();  
        if (ofd.ShowDialog() == true)  
        {  
            propertyValue.Value = ofd.FileName;  
        }  
    }  
    ```  
  
5.  <span data-ttu-id="4abd4-133">Ponieważ działania i Projektant znajdują się w tym samym zestawie, rejestracja atrybuty projektanta działań są realizowane w konstruktorze statycznym działania, jak pokazano w następującym przykładzie SimpleCodeActivity.cs.</span><span class="sxs-lookup"><span data-stu-id="4abd4-133">Because the activity and the designer are in the same assembly, registration of the activity designer attributes are accomplished in the static constructor of the activity itself, as shown in the following example from SimpleCodeActivity.cs.</span></span>  
  
    ```  
    static SimpleCodeActivity()  
    {  
        AttributeTableBuilder builder = new AttributeTableBuilder();  
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "RepeatCount", new EditorAttribute(typeof(CustomInlineEditor), typeof(PropertyValueEditor)));  
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "FileName", new EditorAttribute(typeof(FilePickerEditor), typeof(DialogPropertyValueEditor)));  
        MetadataStore.AddAttributeTable(builder.CreateTable());  
    }  
    ```  
  
## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4abd4-134">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="4abd4-134">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="4abd4-135">Skompiluj rozwiązanie, a następnie otwórz Workflow1.xaml.</span><span class="sxs-lookup"><span data-stu-id="4abd4-135">Build the solution, and then open Workflow1.xaml.</span></span>  
  
2.  <span data-ttu-id="4abd4-136">Przeciągnij **SimpleCodeActivity** z przybornika na kanwie projektanta.</span><span class="sxs-lookup"><span data-stu-id="4abd4-136">Drag a **SimpleCodeActivity** from the toolbox onto the designer canvas.</span></span>  
  
3.  <span data-ttu-id="4abd4-137">Kliknij przycisk **SimpleCodeActivity** , a następnie otwórz siatki właściwości, gdy formant suwaka i plik pobrania kontroli.</span><span class="sxs-lookup"><span data-stu-id="4abd4-137">Click the **SimpleCodeActivity** and then open the property grid where there is a slider control and a file picking control.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4abd4-138">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="4abd4-138">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4abd4-139">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="4abd4-139">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4abd4-140">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="4abd4-140">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4abd4-141">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="4abd4-141">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\PropertyGridExtensibility`
