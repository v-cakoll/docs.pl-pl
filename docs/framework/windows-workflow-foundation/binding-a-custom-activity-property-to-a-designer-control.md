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
# <a name="binding-a-custom-activity-property-to-a-designer-control"></a><span data-ttu-id="d5733-102">Powiązanie właściwości działań niestandardowych do projektanta formantu</span><span class="sxs-lookup"><span data-stu-id="d5733-102">Binding a custom activity property to a designer control</span></span>
<span data-ttu-id="d5733-103">Powiązanie formantu projektanta pola tekstowego z argumentem działanie jest bardzo prosta; Wiązanie złożonych projektanta formantu (np. pola kombi) argument działania mogą jednak stanowi wyzwanie.</span><span class="sxs-lookup"><span data-stu-id="d5733-103">Binding a text box designer control to an activity argument is fairly straightforward; binding a complex designer control (such as a combo box) to an activity argument may present challenges, however.</span></span> <span data-ttu-id="d5733-104">W tym temacie omówiono sposób powiązać argumentu działania kontrolki pola kombi na Projektant działań niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="d5733-104">This topic discusses how to bind an activity argument to a combo box control on a custom activity designer.</span></span>  
  
#### <a name="creating-the-combo-box-item-converter"></a><span data-ttu-id="d5733-105">Tworzenie konwertera elementu pola kombi</span><span class="sxs-lookup"><span data-stu-id="d5733-105">Creating the combo box item converter</span></span>  
  
1.  <span data-ttu-id="d5733-106">Utwórz nowe puste rozwiązanie w programie Visual Studio o nazwie właściwości niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="d5733-106">Create a new empty solution in Visual Studio called CustomProperty.</span></span>  
  
2.  <span data-ttu-id="d5733-107">Utwórz nową klasę o nazwie ComboBoxItemConverter.</span><span class="sxs-lookup"><span data-stu-id="d5733-107">Create a new class called ComboBoxItemConverter.</span></span> <span data-ttu-id="d5733-108">Dodaj odwołanie do System.Windows.Data i klasa pochodzi od <xref:System.Windows.Data.IValueConverter>.</span><span class="sxs-lookup"><span data-stu-id="d5733-108">Add a reference to System.Windows.Data, and have the class derive from <xref:System.Windows.Data.IValueConverter>.</span></span> <span data-ttu-id="d5733-109">Visual Studio, które implementuje interfejs służący do generowania zastępcze ma `Convert` i `ConvertBack`.</span><span class="sxs-lookup"><span data-stu-id="d5733-109">Have Visual Studio implement the interface to generate stubs for `Convert` and `ConvertBack`.</span></span>  
  
3.  <span data-ttu-id="d5733-110">Dodaj następujący kod do `Convert` metody.</span><span class="sxs-lookup"><span data-stu-id="d5733-110">Add the following code to the `Convert` method.</span></span> <span data-ttu-id="d5733-111">Ten kod konwertuje działania <xref:System.Activities.InArgument%601> typu <xref:System.String> wartości do umieszczenia w projektancie.</span><span class="sxs-lookup"><span data-stu-id="d5733-111">This code converts the activity's <xref:System.Activities.InArgument%601> of type <xref:System.String> to the value to be placed in the designer.</span></span>  
  
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
  
     <span data-ttu-id="d5733-112">Wyrażenie we fragmencie kodu powyżej można również utworzyć za pomocą <xref:Microsoft.CSharp.Activities.CSharpValue%601> zamiast <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>.</span><span class="sxs-lookup"><span data-stu-id="d5733-112">The expression in the above code snippet can also be created using <xref:Microsoft.CSharp.Activities.CSharpValue%601> instead of <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>.</span></span>  
  
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
  
4.  <span data-ttu-id="d5733-113">Dodaj następujący kod do `ConvertBack` metody.</span><span class="sxs-lookup"><span data-stu-id="d5733-113">Add the following code to the `ConvertBack` method.</span></span> <span data-ttu-id="d5733-114">Tym konwertuje kod przychodzącego elementu pola kombi z powrotem do <xref:System.Activities.InArgument%601>.</span><span class="sxs-lookup"><span data-stu-id="d5733-114">This code converts the incoming combo box item back to an <xref:System.Activities.InArgument%601>.</span></span>  
  
    ```  
    // Convert combo box value to InArgument<string>  
                string itemContent = (string)((ComboBoxItem)value).Content;  
                VisualBasicValue<string> vbArgument = new VisualBasicValue<string>(itemContent);  
                InArgument<string> inArgument = new InArgument<string>(vbArgument);  
                return inArgument;  
    ```  
  
     <span data-ttu-id="d5733-115">Wyrażenie we fragmencie kodu powyżej można również utworzyć za pomocą <xref:Microsoft.CSharp.Activities.CSharpValue%601> zamiast <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>.</span><span class="sxs-lookup"><span data-stu-id="d5733-115">The expression in the above code snippet can also be created using <xref:Microsoft.CSharp.Activities.CSharpValue%601> instead of <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>.</span></span>  
  
    ```  
    // Convert combo box value to InArgument<string>  
                string itemContent = (string)((ComboBoxItem)value).Content;  
                CSharpValue<string> csArgument = new CSharpValue<string>(itemContent);  
                InArgument<string> inArgument = new InArgument<string>(csArgument);  
                return inArgument;  
    ```  
  
#### <a name="adding-the-comboboxitemconverter-to-the-custom-designer-of-an-activity"></a><span data-ttu-id="d5733-116">Dodawanie ComboBoxItemConverter do projektanta niestandardowego działania</span><span class="sxs-lookup"><span data-stu-id="d5733-116">Adding the ComboBoxItemConverter to the custom designer of an activity</span></span>  
  
1.  <span data-ttu-id="d5733-117">Dodaj nowy element do projektu.</span><span class="sxs-lookup"><span data-stu-id="d5733-117">Add a new item to the project.</span></span> <span data-ttu-id="d5733-118">W oknie dialogowym Nowy element wybierz węzeł przepływu pracy, a następnie wybierz Projektant działań jako typ nowego elementu.</span><span class="sxs-lookup"><span data-stu-id="d5733-118">In the New Item dialog, select the Workflow node and select Activity Designer as the type of the new item.</span></span> <span data-ttu-id="d5733-119">Nazwa elementu CustomPropertyDesigner.</span><span class="sxs-lookup"><span data-stu-id="d5733-119">Name the item CustomPropertyDesigner.</span></span>  
  
2.  <span data-ttu-id="d5733-120">Dodaj pole kombi do nowego projektanta.</span><span class="sxs-lookup"><span data-stu-id="d5733-120">Add a Combo Box to the new designer.</span></span> <span data-ttu-id="d5733-121">We właściwości elementów, należy dodać kilka elementów do pola kombi z wartościami zawartości "Item1" i "Item2".</span><span class="sxs-lookup"><span data-stu-id="d5733-121">In the Items property, add a couple of items to the combo box, with Content values of "Item1" and 'Item2".</span></span>  
  
3.  <span data-ttu-id="d5733-122">Zmodyfikuj XAML pola kombi, aby dodać nowy konwerter elementu jako elementu konwerter służący do pola kombi.</span><span class="sxs-lookup"><span data-stu-id="d5733-122">Modify the XAML of the combo box to add the new item converter as the item converter to be used for the combo box.</span></span> <span data-ttu-id="d5733-123">Konwerter nie zostanie dodany jako zasób w segmencie ActivityDesigner.Resources i określa konwerter w atrybucie konwertera dla <xref:System.Windows.Controls.ComboBox>.</span><span class="sxs-lookup"><span data-stu-id="d5733-123">The converter is added as a resource in the ActivityDesigner.Resources segment, and specifies the converter in the Converter attribute for the <xref:System.Windows.Controls.ComboBox>.</span></span> <span data-ttu-id="d5733-124">Należy pamiętać, że przestrzeń nazw projektu została określona w przestrzeni nazw atrybutów dla Projektant działań; w przypadku projektanta do użycia w innym projekcie, ta przestrzeń nazw muszą zostać zmienione.</span><span class="sxs-lookup"><span data-stu-id="d5733-124">Note that the namespace of the project is specified in the namespaces attributes for the activity designer; if the designer is to be used in a different project, this namespace will need to be changed.</span></span>  
  
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
  
4.  <span data-ttu-id="d5733-125">Utwórz nowy element typu <xref:System.Activities.CodeActivity>.</span><span class="sxs-lookup"><span data-stu-id="d5733-125">Create a new item of type <xref:System.Activities.CodeActivity>.</span></span> <span data-ttu-id="d5733-126">Domyślny kod utworzony IDE dla działania będą wystarczające w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="d5733-126">The default code created by the IDE for the activity will be sufficient for this example.</span></span>  
  
5.  <span data-ttu-id="d5733-127">Dodaj następujący atrybut w definicji klasy:</span><span class="sxs-lookup"><span data-stu-id="d5733-127">Add the following attribute to the class definition:</span></span>  
  
    ```  
    [Designer(typeof(CustomPropertyDesigner))]  
    ```  
  
     <span data-ttu-id="d5733-128">Ten wiersz kojarzy nowe projektanta z nową klasę.</span><span class="sxs-lookup"><span data-stu-id="d5733-128">This line associates the new designer with the new class.</span></span>  
  
 <span data-ttu-id="d5733-129">Nowe działanie powinno być teraz skojarzone z projektanta.</span><span class="sxs-lookup"><span data-stu-id="d5733-129">The new activity should now be associated with the designer.</span></span> <span data-ttu-id="d5733-130">Aby przetestować nowe działanie, dodaj go do przepływu pracy i ustaw pole kombi na dwie wartości.</span><span class="sxs-lookup"><span data-stu-id="d5733-130">To test the new activity, add it to a workflow, and set the combo box to the two values.</span></span> <span data-ttu-id="d5733-131">Okno właściwości należy zaktualizować, aby odzwierciedlić wartość pola kombi.</span><span class="sxs-lookup"><span data-stu-id="d5733-131">The properties window should update to reflect the combo box value.</span></span>
