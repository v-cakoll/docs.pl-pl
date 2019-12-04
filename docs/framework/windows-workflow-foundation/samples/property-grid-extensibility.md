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
# <a name="property-grid-extensibility"></a>Rozszerzalność siatki właściwości

Deweloper może dostosować siatkę właściwości, która jest wyświetlana po wybraniu danego działania w projektancie. Można to zrobić, aby utworzyć bogate środowisko edycji. Ten przykład pokazuje, jak można to zrobić.

## <a name="demonstrates"></a>Przedstawia

Rozszerzalność siatki właściwości projektanta przepływu pracy.

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\PropertyGridExtensibility`

## <a name="discussion"></a>Dyskusji

Aby można było rozwinąć siatkę właściwości, deweloper ma opcje umożliwiające dostosowanie wbudowanego elementu edytora siatki właściwości lub wyświetlenie okna dialogowego, które jest wyświetlane dla bardziej zaawansowanej powierzchni edycji. W tym przykładzie przedstawiono dwa różne edytory: Edytor wbudowany i Edytor okna dialogowego.

## <a name="inline-editor"></a>Edytor wbudowany

W przykładzie edytora wbudowanego zademonstrowano następujące elementy:

- Tworzy typ, który pochodzi od <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor>.

- W konstruktorze wartość <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> jest ustawiana za pomocą szablonu danych Windows Presentation Foundation (WPF). Może to być powiązane z szablonem XAML, ale w tym przykładzie kod jest używany do inicjowania powiązania danych.

- Szablon danych zawiera kontekst danych <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> elementu renderowanego w siatce właściwości. Zwróć uwagę na następujący kod (z CustomInlineEditor.cs), który następnie tworzy powiązanie z właściwością `Value`.

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

- Ponieważ działanie i Projektant znajdują się w tym samym zestawie, rejestracja atrybutów projektanta działań jest realizowana w konstruktorze statycznym działania, jak pokazano w poniższym przykładzie z SimpleCodeActivity.cs.

    ```csharp
    static SimpleCodeActivity()
    {
        AttributeTableBuilder builder = new AttributeTableBuilder();
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "RepeatCount", new EditorAttribute(typeof(CustomInlineEditor), typeof(PropertyValueEditor)));
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "FileName", new EditorAttribute(typeof(FilePickerEditor), typeof(DialogPropertyValueEditor)));
        MetadataStore.AddAttributeTable(builder.CreateTable());
    }
    ```

## <a name="dialog-editor"></a>edytor okien dialogowych

W przykładzie edytora okien dialogowych przedstawiono następujące elementy:

1. Tworzy typ, który pochodzi od <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor>.

2. Ustawia wartość <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> w konstruktorze z szablonem danych WPF. Tę opcję można utworzyć w języku XAML, ale w tym przykładzie jest to tworzone w kodzie.

3. Szablon danych zawiera kontekst danych <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> elementu renderowanego w siatce właściwości. W poniższym kodzie, następnie tworzy powiązanie z właściwością `Value`. Należy również uwzględnić <xref:System.Activities.Presentation.PropertyEditing.EditModeSwitchButton>, aby udostępnić przycisk, który wywołuje okno dialogowe w FilePickerEditor.cs.

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

4. Zastępuje metodę <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor.ShowDialog%2A> w typie projektanta, aby obsłużyć wyświetlanie okna dialogowego. W tym przykładzie jest pokazywana podstawowa <xref:System.Windows.Forms.FileDialog>.

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

5. Ponieważ działanie i Projektant znajdują się w tym samym zestawie, rejestracja atrybutów projektanta działań jest realizowana w konstruktorze statycznym działania, jak pokazano w poniższym przykładzie z SimpleCodeActivity.cs.

    ```csharp
    static SimpleCodeActivity()
    {
        AttributeTableBuilder builder = new AttributeTableBuilder();
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "RepeatCount", new EditorAttribute(typeof(CustomInlineEditor), typeof(PropertyValueEditor)));
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "FileName", new EditorAttribute(typeof(FilePickerEditor), typeof(DialogPropertyValueEditor)));
        MetadataStore.AddAttributeTable(builder.CreateTable());
    }
    ```

## <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład

1. Skompiluj rozwiązanie, a następnie otwórz Workflow1. XAML.

2. Przeciągnij **SimpleCodeActivity** z przybornika na kanwę projektanta.

3. Kliknij **SimpleCodeActivity** , a następnie otwórz siatkę właściwości, w której znajduje się kontrolka suwaka i formant wyboru pliku.

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\PropertyGridExtensibility`
