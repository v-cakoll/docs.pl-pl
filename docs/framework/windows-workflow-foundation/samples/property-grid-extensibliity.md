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
# <a name="property-grid-extensibliity"></a>Rozszerzalność siatki właściwości
Deweloper może dostosować siatki właściwości, wyświetlanego po wybraniu danego działania w projektancie. Można to zrobić, aby utworzyć zaawansowane środowisko edycji. Niniejszy przykład pokazuje, jak można to zrobić.  
  
## <a name="demonstrates"></a>Demonstracje  
 Rozszerzalność siatki właściwości projektanta przepływu pracy.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\PropertyGridExtensibility`  
  
## <a name="discussion"></a>Dyskusja  
 Aby rozszerzyć siatki właściwości, deweloper ma opcje dostosowania wyglądu wbudowanego edytora siatki właściwości lub okno dialogowe, które pojawia się dla bardziej zaawansowanych powierzchni edycji. Istnieją dwa różne edytory przedstawiona w tym przykładzie; Edytor wbudowane i Edytor okien dialogowych.  
  
## <a name="inline-editor"></a>Edytor wbudowane  
 Przykład edytora wbudowane pokazuje następujące czynności:  
  
-   Tworzy typ, który pochodzi od klasy <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor>.  
  
-   W Konstruktorze <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> wartość została ustawiona za pomocą szablonu danych Windows Presentation Foundation (WPF). To może być powiązana z szablonem XAML, ale w tym przykładzie kodu służy do inicjowania powiązanie danych.  
  
-   Szablon danych ma kontekstu danych <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> elementu renderowane w siatce właściwości. Uwaga w poniższym kodzie (z CustomInlineEditor.cs), który następnie powiąże tego kontekstu `Value` właściwości.  
  
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
  
-   Ponieważ działania i Projektant znajdują się w tym samym zestawie, rejestracja atrybuty projektanta działań są realizowane w konstruktorze statycznym działania, jak pokazano w następującym przykładzie SimpleCodeActivity.cs.  
  
    ```  
    static SimpleCodeActivity()  
    {  
        AttributeTableBuilder builder = new AttributeTableBuilder();  
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "RepeatCount", new EditorAttribute(typeof(CustomInlineEditor), typeof(PropertyValueEditor)));  
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "FileName", new EditorAttribute(typeof(FilePickerEditor), typeof(DialogPropertyValueEditor)));  
        MetadataStore.AddAttributeTable(builder.CreateTable());  
    }  
    ```  
  
## <a name="dialog-editor"></a>Edytor okien dialogowych  
 Przykład edytora okna dialogowego pokazuje następujące czynności:  
  
1.  Tworzy typ, który pochodzi od klasy <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor>.  
  
2.  Zestawy <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> wartość w Konstruktorze z [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] szablon danych. To mogą być tworzone w XAML, ale w tym przykładzie zostanie on utworzony w kodzie.  
  
3.  Szablon danych ma kontekstu danych <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> elementu renderowane w siatce właściwości. W poniższym kodzie następnie powiąże `Value` właściwości. Podstawowe znaczenie ma obejmować <xref:System.Activities.Presentation.PropertyEditing.EditModeSwitchButton> zapewnienie przycisk, który wywołuje okno dialogowe w FilePickerEditor.cs.  
  
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
  
4.  Zastępuje <!--zz <xref:Microsoft.Windows.Design.PropertyEditing.ShowDialog%2A>--> `Microsoft.Windows.Design.PropertyEditing.ShowDialog` metoda w typie projektanta do obsługi wyświetlania okna dialogowego. W tym przykładzie podstawową <xref:System.Windows.Forms.FileDialog> jest wyświetlany.  
  
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
  
5.  Ponieważ działania i Projektant znajdują się w tym samym zestawie, rejestracja atrybuty projektanta działań są realizowane w konstruktorze statycznym działania, jak pokazano w następującym przykładzie SimpleCodeActivity.cs.  
  
    ```  
    static SimpleCodeActivity()  
    {  
        AttributeTableBuilder builder = new AttributeTableBuilder();  
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "RepeatCount", new EditorAttribute(typeof(CustomInlineEditor), typeof(PropertyValueEditor)));  
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "FileName", new EditorAttribute(typeof(FilePickerEditor), typeof(DialogPropertyValueEditor)));  
        MetadataStore.AddAttributeTable(builder.CreateTable());  
    }  
    ```  
  
## <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Skompiluj rozwiązanie, a następnie otwórz Workflow1.xaml.  
  
2.  Przeciągnij **SimpleCodeActivity** z przybornika na kanwie projektanta.  
  
3.  Kliknij przycisk **SimpleCodeActivity** , a następnie otwórz siatki właściwości, gdy formant suwaka i plik pobrania kontroli.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\PropertyGridExtensibility`
