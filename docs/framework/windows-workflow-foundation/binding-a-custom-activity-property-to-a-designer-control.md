---
title: Wiązanie niestandardowych właściwości działań z kontrolką projektanta
ms.date: 03/30/2017
ms.assetid: 2e8061ea-10f5-407c-a31f-d0d74ce12f27
ms.openlocfilehash: 142a9eb273a98d3a2d83a1239d6d7c891d5cc305
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945902"
---
# <a name="binding-a-custom-activity-property-to-a-designer-control"></a>Wiązanie niestandardowych właściwości działań z kontrolką projektanta

Powiązywanie projektanta kontrolkę pola tekstowego argument działania jest dość prosta; powiązanie z kontrolką projektanta złożonych (np. pola kombi) z argument działania stwarza trudności, jednak. W tym temacie omówiono, jak powiązać argument działania do kontrolki pola kombi na niestandardowego projektanta działań.

## <a name="creating-the-combo-box-item-converter"></a>Tworzenie konwerter elementu pola kombi

1. Utwórz nowe, puste rozwiązanie w programie Visual Studio o nazwie właściwości niestandardowej.

2. Utwórz nową klasę o nazwie ComboBoxItemConverter. Dodaj odwołanie do System.Windows.Data i mieć klasę pochodną <xref:System.Windows.Data.IValueConverter>. Program Visual Studio zaimplementować interfejs służący do generowania wycinki `Convert` i `ConvertBack`.

3. Dodaj następujący kod do `Convert` metody. Ten kod konwertuje działania <xref:System.Activities.InArgument%601> typu <xref:System.String> wartości do umieszczenia w projektancie.

    ```csharp
    ModelItem modelItem = value as ModelItem;
    if (value != null)
    {
        InArgument<string> inArgument = modelItem.GetCurrentValue() as InArgument<string>;

        if (inArgument != null)
        {
            Activity<string> expression = inArgument.Expression;
            VisualBasicValue<string> vbexpression = expression as VisualBasicValue<string>;
            Literal<string> literal = expression as Literal<string>;

            if (literal != null)
            {
                return "\"" + literal.Value + "\"";
            }
            else if (vbexpression != null)
            {
                return vbexpression.ExpressionText;
            }
        }
    }
    return null;
    ```

     Wyrażenie w powyższym fragmencie kodu można również utworzyć przy użyciu <xref:Microsoft.CSharp.Activities.CSharpValue%601> zamiast <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>.

    ```csharp
    ModelItem modelItem = value as ModelItem;
    if (value != null)
    {
        InArgument<string> inArgument = modelItem.GetCurrentValue() as InArgument<string>;

        if (inArgument != null)
        {
            Activity<string> expression = inArgument.Expression;
            CSharpValue<string> csexpression = expression as CSharpValue<string>;
            Literal<string> literal = expression as Literal<string>;

            if (literal != null)
            {
                return "\"" + literal.Value + "\"";
            }
            else if (csexpression != null)
            {
                return csexpression.ExpressionText;
            }
        }
    }
    return null;
    ```

4. Dodaj następujący kod do `ConvertBack` metody. Ta konwertuje kod przychodzącego elementu pola kombi z powrotem do <xref:System.Activities.InArgument%601>.

    ```csharp
    // Convert combo box value to InArgument<string>
                string itemContent = (string)((ComboBoxItem)value).Content;
                VisualBasicValue<string> vbArgument = new VisualBasicValue<string>(itemContent);
                InArgument<string> inArgument = new InArgument<string>(vbArgument);
                return inArgument;
    ```

     Wyrażenie w powyższym fragmencie kodu można również utworzyć przy użyciu <xref:Microsoft.CSharp.Activities.CSharpValue%601> zamiast <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>.

    ```csharp
    // Convert combo box value to InArgument<string>
                string itemContent = (string)((ComboBoxItem)value).Content;
                CSharpValue<string> csArgument = new CSharpValue<string>(itemContent);
                InArgument<string> inArgument = new InArgument<string>(csArgument);
                return inArgument;
    ```

## <a name="adding-the-comboboxitemconverter-to-the-custom-designer-of-an-activity"></a>Dodawanie ComboBoxItemConverter do niestandardowego projektanta działań

1. Dodaj nowy element do projektu. W oknie dialogowym Nowy element wybierz węzeł przepływ pracy, a następnie wybierz projektanta działań jako typ nowego elementu. Nazwa elementu CustomPropertyDesigner.

2. Dodaj pola kombi do projektanta nowy. We właściwości elementów, należy dodać kilka elementów do pola kombi z wartościami zawartości item1 "—" i "item2 —".

3. Zmodyfikuj XAML pola kombi, aby dodać nowy konwerter elementu jako elementu konwerter służący do pola kombi. Konwerter jest dodawany jako zasób w segmencie ActivityDesigner.Resources i określa konwerter w atrybucie konwertera dla <xref:System.Windows.Controls.ComboBox>. Należy pamiętać, że przestrzeń nazw projektu określono w atrybucie przestrzeni nazw dla Projektant działań; w przypadku projektanta do użycia w innym projekcie, muszą zostać zmienione w tej przestrzeni nazw.

    ```xaml
    <sap:ActivityDesigner x:Class="CustomProperty.CustomPropertyDesigner"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:c="clr-namespace:CustomProperty"
        xmlns:sap="clr-namespace:System.Activities.Presentation;assembly=System.Activities.Presentation"
        xmlns:sapv="clr-namespace:System.Activities.Presentation.View;assembly=System.Activities.Presentation">

        <sap:ActivityDesigner.Resources>
            <ResourceDictionary>
                <c:ComboBoxItemConverter x:Key="comboBoxItemConverter"/>
            </ResourceDictionary>
        </sap:ActivityDesigner.Resources>
        <Grid>
            <ComboBox SelectedValue="{Binding Path=ModelItem.Text, Mode=TwoWay, Converter={StaticResource comboBoxItemConverter}}"  Height="23" HorizontalAlignment="Left" Margin="132,5,0,0" Name="comboBox1" VerticalAlignment="Top" Width="120" ItemsSource="{Binding}">
                <ComboBoxItem>item1</ComboBoxItem>
                <ComboBoxItem>item2</ComboBoxItem>
            </ComboBox>
        </Grid>
    </sap:ActivityDesigner>
    ```

4. Utwórz nowy element typu <xref:System.Activities.CodeActivity>. Domyślny kod utworzony przez środowisko IDE dla działania okażą się wystarczające w tym przykładzie.

5. Dodaj następujący atrybut do definicji klasy:

    ```csharp
    [Designer(typeof(CustomPropertyDesigner))]
    ```

     Ten wiersz kojarzy nowe narzędzia Projektant z nową klasę.

 Nowe działanie powinno być teraz skojarzone z projektanta. Aby przetestować nowe działanie, dodaj go do przepływu pracy i ustawić pole kombi na dwie wartości. W oknie właściwości powinna zostać zaktualizowana w celu odzwierciedlenia wartości pola kombi.
