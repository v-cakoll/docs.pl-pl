---
title: "Powiązanie właściwości działań niestandardowych do projektanta formantu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2e8061ea-10f5-407c-a31f-d0d74ce12f27
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e9edc168dc6e4111e5f2d58a62c2b0341f74aa04
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="binding-a-custom-activity-property-to-a-designer-control"></a>Powiązanie właściwości działań niestandardowych do projektanta formantu
Powiązanie formantu projektanta pola tekstowego z argumentem działanie jest bardzo prosta; Wiązanie złożonych projektanta formantu (np. pola kombi) argument działania mogą jednak stanowi wyzwanie. W tym temacie omówiono sposób powiązać argumentu działania kontrolki pola kombi na Projektant działań niestandardowych.  
  
#### <a name="creating-the-combo-box-item-converter"></a>Tworzenie konwertera elementu pola kombi  
  
1.  Utwórz nowe puste rozwiązanie w programie Visual Studio o nazwie właściwości niestandardowej.  
  
2.  Utwórz nową klasę o nazwie ComboBoxItemConverter. Dodaj odwołanie do System.Windows.Data i klasa pochodzi od <xref:System.Windows.Data.IValueConverter>. Visual Studio, które implementuje interfejs służący do generowania zastępcze ma `Convert` i `ConvertBack`.  
  
3.  Dodaj następujący kod do `Convert` metody. Ten kod konwertuje działania <xref:System.Activities.InArgument%601> typu <xref:System.String> wartości do umieszczenia w projektancie.  
  
    ```  
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
  
     Wyrażenie we fragmencie kodu powyżej można również utworzyć za pomocą <xref:Microsoft.CSharp.Activities.CSharpValue%601> zamiast <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>.  
  
    ```  
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
  
4.  Dodaj następujący kod do `ConvertBack` metody. Tym konwertuje kod przychodzącego elementu pola kombi z powrotem do <xref:System.Activities.InArgument%601>.  
  
    ```  
    // Convert combo box value to InArgument<string>  
                string itemContent = (string)((ComboBoxItem)value).Content;  
                VisualBasicValue<string> vbArgument = new VisualBasicValue<string>(itemContent);  
                InArgument<string> inArgument = new InArgument<string>(vbArgument);  
                return inArgument;  
    ```  
  
     Wyrażenie we fragmencie kodu powyżej można również utworzyć za pomocą <xref:Microsoft.CSharp.Activities.CSharpValue%601> zamiast <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>.  
  
    ```  
    // Convert combo box value to InArgument<string>  
                string itemContent = (string)((ComboBoxItem)value).Content;  
                CSharpValue<string> csArgument = new CSharpValue<string>(itemContent);  
                InArgument<string> inArgument = new InArgument<string>(csArgument);  
                return inArgument;  
    ```  
  
#### <a name="adding-the-comboboxitemconverter-to-the-custom-designer-of-an-activity"></a>Dodawanie ComboBoxItemConverter do projektanta niestandardowego działania  
  
1.  Dodaj nowy element do projektu. W oknie dialogowym Nowy element wybierz węzeł przepływu pracy, a następnie wybierz Projektant działań jako typ nowego elementu. Nazwa elementu CustomPropertyDesigner.  
  
2.  Dodaj pole kombi do nowego projektanta. We właściwości elementów, należy dodać kilka elementów do pola kombi z wartościami zawartości "Item1" i "Item2".  
  
3.  Zmodyfikuj XAML pola kombi, aby dodać nowy konwerter elementu jako elementu konwerter służący do pola kombi. Konwerter nie zostanie dodany jako zasób w segmencie ActivityDesigner.Resources i określa konwerter w atrybucie konwertera dla <xref:System.Windows.Controls.ComboBox>. Należy pamiętać, że przestrzeń nazw projektu została określona w przestrzeni nazw atrybutów dla Projektant działań; w przypadku projektanta do użycia w innym projekcie, ta przestrzeń nazw muszą zostać zmienione.  
  
    ```  
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
  
4.  Utwórz nowy element typu <xref:System.Activities.CodeActivity>. Domyślny kod utworzony IDE dla działania będą wystarczające w tym przykładzie.  
  
5.  Dodaj następujący atrybut w definicji klasy:  
  
    ```  
    [Designer(typeof(CustomPropertyDesigner))]  
    ```  
  
     Ten wiersz kojarzy nowe projektanta z nową klasę.  
  
 Nowe działanie powinno być teraz skojarzone z projektanta. Aby przetestować nowe działanie, dodaj go do przepływu pracy i ustaw pole kombi na dwie wartości. Okno właściwości należy zaktualizować, aby odzwierciedlić wartość pola kombi.
