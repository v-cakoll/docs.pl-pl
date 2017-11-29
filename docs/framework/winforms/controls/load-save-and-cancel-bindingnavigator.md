---
title: "Porady: dodawanie przycisków załaduj, zapisz i anuluj do kontrolki BindingNavigator formularzy systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], manipulating
- BindingNavigator control [Windows Forms], adding buttons
ms.assetid: faa33042-186e-4bb2-8798-17ceb987ec62
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4bc4f53c404e3767b9f98ca5ab46b19db31f9c6e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-load-save-and-cancel-buttons-to-the-windows-forms-bindingnavigator-control"></a><span data-ttu-id="aa4f9-102">Porady: dodawanie przycisków załaduj, zapisz i anuluj do kontrolki BindingNavigator formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="aa4f9-102">How to: Add Load, Save, and Cancel Buttons to the Windows Forms BindingNavigator Control</span></span>
<span data-ttu-id="aa4f9-103"><xref:System.Windows.Forms.BindingNavigator> Formant jest specjalnych <xref:System.Windows.Forms.ToolStrip> formant, który jest przeznaczony do nawigowania i operowanie nimi formantów w formularzu, które są związane z danymi.</span><span class="sxs-lookup"><span data-stu-id="aa4f9-103">The <xref:System.Windows.Forms.BindingNavigator> control is a special-purpose <xref:System.Windows.Forms.ToolStrip> control that is intended for navigating and manipulating controls on your form that are bound to data.</span></span>  
  
 <span data-ttu-id="aa4f9-104">Ponieważ jest on <xref:System.Windows.Forms.ToolStrip> kontroli, <xref:System.Windows.Forms.BindingNavigator> składnika można łatwo zmodyfikowany w celu dodania dodatkowych lub alternatywnych poleceń dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="aa4f9-104">Because it is a <xref:System.Windows.Forms.ToolStrip> control, the <xref:System.Windows.Forms.BindingNavigator> component can be easily modified to include additional or alternative commands for the user.</span></span>  
  
 <span data-ttu-id="aa4f9-105">W poniższej procedurze <xref:System.Windows.Forms.TextBox> formant jest powiązany z danymi, a <xref:System.Windows.Forms.ToolStrip> formant, który zostanie dodany do formularza są modyfikowane w celu uwzględnienia obciążenia, Zapisz, a przyciski "Anuluj".</span><span class="sxs-lookup"><span data-stu-id="aa4f9-105">In the following procedure, a <xref:System.Windows.Forms.TextBox> control is bound to data, and the <xref:System.Windows.Forms.ToolStrip> control that is added to the form is modified to include load, save, and cancel buttons.</span></span>  
  
### <a name="to-add-load-save-and-cancel-buttons-to-the-bindingnavigator-component"></a><span data-ttu-id="aa4f9-106">Aby dodać obciążenia, Zapisz i Anuluj przycisków składnika BindingNavigator</span><span class="sxs-lookup"><span data-stu-id="aa4f9-106">To add load, save, and cancel buttons to the BindingNavigator component</span></span>  
  
1.  <span data-ttu-id="aa4f9-107">Dodaj <xref:System.Windows.Forms.TextBox> sterowania do formularza.</span><span class="sxs-lookup"><span data-stu-id="aa4f9-107">Add a <xref:System.Windows.Forms.TextBox> control to your form.</span></span>  
  
2.  <span data-ttu-id="aa4f9-108">Aby powiązać <xref:System.Windows.Forms.BindingSource>, która jest powiązana ze źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="aa4f9-108">Bind it to a <xref:System.Windows.Forms.BindingSource>, which is bound to a data source.</span></span> <span data-ttu-id="aa4f9-109">Na przykład <xref:System.Windows.Forms.BindingSource> jest powiązany z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="aa4f9-109">For this example, the <xref:System.Windows.Forms.BindingSource> is bound to a database.</span></span>  
  
3.  <span data-ttu-id="aa4f9-110">Po wygenerowaniu zestawu danych i tabeli karty, przeciągnij <xref:System.Windows.Forms.BindingNavigator> sterowania do formularza.</span><span class="sxs-lookup"><span data-stu-id="aa4f9-110">After the dataset and table adapter are generated, drag a <xref:System.Windows.Forms.BindingNavigator> control to the form.</span></span>  
  
4.  <span data-ttu-id="aa4f9-111">Ustaw <xref:System.Windows.Forms.BindingNavigator> formantu <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> właściwości <xref:System.Windows.Forms.BindingSource> na formularz, który jest powiązany z kontrolki.</span><span class="sxs-lookup"><span data-stu-id="aa4f9-111">Set the <xref:System.Windows.Forms.BindingNavigator> control's <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> property to the <xref:System.Windows.Forms.BindingSource> on the form that is bound to the controls.</span></span>  
  
5.  <span data-ttu-id="aa4f9-112">Wybierz <xref:System.Windows.Forms.BindingNavigator> formantu.</span><span class="sxs-lookup"><span data-stu-id="aa4f9-112">Select the <xref:System.Windows.Forms.BindingNavigator> control.</span></span>  
  
6.  <span data-ttu-id="aa4f9-113">Kliknij symbol tagu inteligentnego (![symbol tagu inteligentnego](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) tak **zadania BindingNavigator** pojawi się okno dialogowe i wybierz **edytowanie elementów**.</span><span class="sxs-lookup"><span data-stu-id="aa4f9-113">Click the smart tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) so the **BindingNavigator Tasks** dialog appears and select **Edit Items**.</span></span>  
  
     <span data-ttu-id="aa4f9-114">**Edytora kolekcji elementy** pojawi się.</span><span class="sxs-lookup"><span data-stu-id="aa4f9-114">The **Items Collection Editor** appears.</span></span>  
  
7.  <span data-ttu-id="aa4f9-115">W **edytora kolekcji elementy**, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="aa4f9-115">In the **Items Collection Editor**, complete the following:</span></span>  
  
    1.  <span data-ttu-id="aa4f9-116">Dodaj <xref:System.Windows.Forms.ToolStripSeparator> i trzy <xref:System.Windows.Forms.ToolStripButton> elementów, wybierając odpowiedni typ <xref:System.Windows.Forms.ToolStripItem> i klikając **Dodaj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="aa4f9-116">Add a <xref:System.Windows.Forms.ToolStripSeparator> and three <xref:System.Windows.Forms.ToolStripButton> items by selecting the appropriate type of <xref:System.Windows.Forms.ToolStripItem> and clicking the **Add** button.</span></span>  
  
    2.  <span data-ttu-id="aa4f9-117">Ustaw <xref:System.Windows.Forms.ToolStripItem.Name%2A> właściwości przycisków, aby**LoadButton**,**SaveButton**, i**CancelButton**odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="aa4f9-117">Set the <xref:System.Windows.Forms.ToolStripItem.Name%2A> property of the buttons to**LoadButton**,**SaveButton**, and**CancelButton**, respectively.</span></span>  
  
    3.  <span data-ttu-id="aa4f9-118">Ustaw <xref:System.Windows.Forms.ToolStripItem.Text%2A> właściwości przycisków, aby**obciążenia** `,` **zapisać**, i**anulować**.</span><span class="sxs-lookup"><span data-stu-id="aa4f9-118">Set the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property of the buttons to**Load**`,` **Save**, and**Cancel**.</span></span>  
  
    4.  <span data-ttu-id="aa4f9-119">Ustaw <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> właściwości dla każdego z przycisków, aby**tekstu**.</span><span class="sxs-lookup"><span data-stu-id="aa4f9-119">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property for each of the buttons to**Text**.</span></span> <span data-ttu-id="aa4f9-120">Można też ustawić tę właściwość na**obrazu**lub**ImageAndText**i Ustaw obraz, który ma być wyświetlany w <xref:System.Windows.Forms.ToolStripItem.Image%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="aa4f9-120">Alternatively, you can set this property to**Image**or**ImageAndText**and set the image to be displayed in the <xref:System.Windows.Forms.ToolStripItem.Image%2A> property.</span></span>  
  
    5.  <span data-ttu-id="aa4f9-121">Kliknij przycisk **OK** aby zamknąć okno dialogowe. Przyciski są dodawane do <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="aa4f9-121">Click **OK** to close the dialog box.The buttons are added to the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
8.  <span data-ttu-id="aa4f9-122">Kliknij prawym przyciskiem myszy formularz, a następnie wybierz pozycję **kod widoku**.</span><span class="sxs-lookup"><span data-stu-id="aa4f9-122">Right-click the form and choose **View Code**.</span></span>  
  
9. <span data-ttu-id="aa4f9-123">W edytorze kodu Znajdź wiersz kodu wczytuje dane do karty tabeli.</span><span class="sxs-lookup"><span data-stu-id="aa4f9-123">In the Code Editor, find the line of code that loads data into the table adapter.</span></span> <span data-ttu-id="aa4f9-124">Ten kod został wygenerowany podczas konfigurowania powiązania danych w kroku 2.</span><span class="sxs-lookup"><span data-stu-id="aa4f9-124">This code was generated when you set up the data binding in step 2.</span></span> <span data-ttu-id="aa4f9-125">Kod powinien być podobny do następującego: `TableAdapterName.Fill(DataSetName.TableName)`.</span><span class="sxs-lookup"><span data-stu-id="aa4f9-125">The code should be similar to the following: `TableAdapterName.Fill(DataSetName.TableName)`.</span></span> <span data-ttu-id="aa4f9-126">Będzie on większość prawdopodobnie w postaci <xref:System.Windows.Forms.Form.Load> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="aa4f9-126">It will most likely be in the form's <xref:System.Windows.Forms.Form.Load> event.</span></span>  
  
10. <span data-ttu-id="aa4f9-127">Tworzenie procedury obsługi zdarzeń dla <xref:System.Windows.Forms.ToolStripItem.Click> zdarzenie**obciążenia** <xref:System.Windows.Forms.ToolStripButton> utworzonego wcześniej i Przenieś ten kod ładowania danych do niego.</span><span class="sxs-lookup"><span data-stu-id="aa4f9-127">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the**Load**<xref:System.Windows.Forms.ToolStripButton> you created earlier and move this data-loading code into it.</span></span>  
  
     <span data-ttu-id="aa4f9-128">Kod powinna wyglądać podobnie do poniższej:</span><span class="sxs-lookup"><span data-stu-id="aa4f9-128">Your code should now look similar to the following:</span></span>  
  
    ```vb  
    Private Sub LoadButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles LoadButton.Click  
        TableAdapterName.Fill(DataSetName.TableName)  
    End Sub  
    ```  
  
    ```csharp  
    private void LoadButton_Click(System.Object sender,   
        System.EventArgs e)  
    {  
        TableAdapterName.Fill(DataSetName.TableName);  
    }  
    ```  
  
11. <span data-ttu-id="aa4f9-129">Tworzenie procedury obsługi zdarzeń dla <xref:System.Windows.Forms.ToolStripItem.Click> zdarzenie **zapisać** <xref:System.Windows.Forms.ToolStripButton> wcześniej utworzony i kod zapisu, aby zaktualizować dane w tabeli formant jest powiązany z.</span><span class="sxs-lookup"><span data-stu-id="aa4f9-129">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the **Save**<xref:System.Windows.Forms.ToolStripButton> you created earlier and write code to update the data within the table the control is bound to.</span></span>  
  
    ```vb  
    Private Sub SaveButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles SaveButton.Click  
        TableAdapterName.Update(DataSetName.TableName)  
    End Sub  
    ```  
  
    ```csharp  
    private void SaveButton_Click(System.Object sender,   
        System.EventArgs e)  
    {  
        TableAdapterName.Update(DataSetName.TableName);  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="aa4f9-130">W niektórych przypadkach <xref:System.Windows.Forms.BindingNavigator> składnik nie ma jeszcze**zapisać** przycisku, ale żaden kod nie zostanie wygenerowane przez projektanta formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="aa4f9-130">In some cases, the <xref:System.Windows.Forms.BindingNavigator> component will already have a**Save** button, but no code will have been generated by the Windows Forms Designer.</span></span> <span data-ttu-id="aa4f9-131">W takim przypadku można umieścić w powyższym kodzie <xref:System.Windows.Forms.ToolStripItem.Click> programu obsługi zdarzeń dla tego przycisku, zamiast tworzenia zupełnie nowy przycisk na <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="aa4f9-131">In this case, you can place the preceding code in the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for that button, rather than creating an entirely new button on the <xref:System.Windows.Forms.ToolStrip>.</span></span> <span data-ttu-id="aa4f9-132">Jednak przycisku jest domyślnie wyłączona, dlatego należy ustawić <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> właściwość przycisk, aby `true` mają poprawnie funkcja przycisku.</span><span class="sxs-lookup"><span data-stu-id="aa4f9-132">However, the button is disabled by default, so you must set the <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> property of the button to `true` to have the button function correctly.</span></span>  
  
12. <span data-ttu-id="aa4f9-133">Tworzenie procedury obsługi zdarzeń dla <xref:System.Windows.Forms.ToolStripItem.Click> zdarzenie**anulować** <xref:System.Windows.Forms.ToolStripButton> utworzonego wcześniej i napisać kod, aby anulować wszystkie zmiany do rekordu danych, która jest wyświetlana.</span><span class="sxs-lookup"><span data-stu-id="aa4f9-133">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the**Cancel**<xref:System.Windows.Forms.ToolStripButton> you created earlier and write code to cancel any changes to the data record that is displayed.</span></span>  
  
    ```vb  
    Private Sub CancelButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles CancelButton.Click  
        BindingSourceName.CancelEdit()  
    End Sub  
    ```  
  
    ```csharp  
    private void CancelButton_Click(System.Object sender, System.EventArgs e)  
    {  
        BindingSourceName.CancelEdit();  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="aa4f9-134"><xref:System.Windows.Forms.BindingSource.CancelEdit%2A> Metoda obejmuje wiersz danych.</span><span class="sxs-lookup"><span data-stu-id="aa4f9-134">The <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> method is scoped to the row of data.</span></span> <span data-ttu-id="aa4f9-135">Zapisz wszelkie zmiany wprowadzone podczas wyświetlania tego pojedynczego rekordu przed przejście do następnego rekordu.</span><span class="sxs-lookup"><span data-stu-id="aa4f9-135">Save any changes you make while viewing that individual record before navigating to the next record.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa4f9-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aa4f9-136">See Also</span></span>  
 <xref:System.Windows.Forms.BindingNavigator>  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.Windows.Forms.ToolStrip>  
 [<span data-ttu-id="aa4f9-137">BindingNavigator — formant</span><span class="sxs-lookup"><span data-stu-id="aa4f9-137">BindingNavigator Control</span></span>](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)  
 [<span data-ttu-id="aa4f9-138">Informacje o składniku BindingSource</span><span class="sxs-lookup"><span data-stu-id="aa4f9-138">BindingSource Component Overview</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component-overview.md)
