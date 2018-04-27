---
title: Extensibliity siatki właściwości
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3530c3a3-756d-4712-9f10-fb2897414d3a
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9393947420709590312200e8f142092c95b91b1f
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="property-grid-extensibliity"></a>Extensibliity siatki właściwości
Projektant można dostosować siatki właściwości wyświetlane w przypadku wybrania konkretnych działań w projektancie. Można to zrobić, aby utworzyć zaawansowane środowisko edycji. W tym przykładzie pokazano, jak to zrobić.  
  
## <a name="demonstrates"></a>Demonstracje  
 Rozszerzalność siatki właściwości projektanta przepływu pracy.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\PropertyGridExtensibility`  
  
## <a name="discussion"></a>Omówienie  
 Aby rozszerzyć siatki właściwości, deweloper ma opcji, aby dostosować wygląd wbudowanego edytora siatki właściwości lub podaj okna dialogowego wyświetlanego dla bardziej zaawansowanych możliwości edycji. Istnieją dwa różne edytory zostało to pokazane w tym przykładzie; Edytor wbudowany i Edytor okien dialogowych.  
  
## <a name="inline-editor"></a>Edytor wbudowany  
 W przykładzie edytor wbudowany pokazano poniżej:  
  
-   Tworzy typ pochodzący z <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor>.  
  
-   W Konstruktorze <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> wartość przy użyciu szablonu danych systemu Windows Presentation Foundation (WPF). To może być powiązana z szablonem XAML, ale w tym przykładzie kodu służy do inicjowania wiązania z danymi.  
  
-   Szablon danych ma kontekstu danych <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> elementu renderowane w siatce właściwości. Uwaga w poniższym kodzie (od CustomInlineEditor.cs) tego kontekstu następnie wiąże `Value` właściwości.  
  
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
  
-   Ponieważ działania i Projektant znajdują się w tym samym zestawie, rejestracja atrybutów projektanta działania są wykonywane w konstruktorze statycznym działania, jak pokazano w poniższym przykładzie z SimpleCodeActivity.cs.  
  
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
 Okno dialogowe Edytor próbki przedstawiono poniżej:  
  
1.  Tworzy typ pochodzący z <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor>.  
  
2.  Ustawia <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> wartość w Konstruktorze z [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] szablon danych. Można go utworzyć w języku XAML, ale w tym przykładzie ten element jest tworzony w kodzie.  
  
3.  Szablon danych ma kontekstu danych <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> elementu renderowane w siatce właściwości. W poniższym kodzie, wówczas wiąże `Value` właściwości. Jest bardzo istotne, aby obejmować <xref:System.Activities.Presentation.PropertyEditing.EditModeSwitchButton> zapewnienie przycisku, który wywołuje okno dialogowe w FilePickerEditor.cs.  
  
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
  
4.  Zastępuje <!--zz <xref:Microsoft.Windows.Design.PropertyEditing.ShowDialog%2A>--> `Microsoft.Windows.Design.PropertyEditing.ShowDialog` metody w typie projektanta do obsługi wyświetlania okna dialogowego. W tym przykładzie podstawowego <xref:System.Windows.Forms.FileDialog> jest wyświetlany.  
  
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
  
5.  Ponieważ działania i Projektant znajdują się w tym samym zestawie, rejestracja atrybutów projektanta działania są wykonywane w konstruktorze statycznym działania, jak pokazano w poniższym przykładzie z SimpleCodeActivity.cs.  
  
    ```  
    static SimpleCodeActivity()  
    {  
        AttributeTableBuilder builder = new AttributeTableBuilder();  
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "RepeatCount", new EditorAttribute(typeof(CustomInlineEditor), typeof(PropertyValueEditor)));  
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "FileName", new EditorAttribute(typeof(FilePickerEditor), typeof(DialogPropertyValueEditor)));  
        MetadataStore.AddAttributeTable(builder.CreateTable());  
    }  
    ```  
  
## <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Skompiluj rozwiązanie, a następnie otwórz Workflow1.xaml.  
  
2.  Przeciągnij **SimpleCodeActivity** z przybornika do obszaru projektowania.  
  
3.  Kliknij przycisk **SimpleCodeActivity** , a następnie otwórz siatki właściwości w przypadku formantu suwaka i plik pobrania formantu.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\PropertyGridExtensibility`
