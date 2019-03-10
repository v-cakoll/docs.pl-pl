---
title: 'Instrukcje: Dodaj obciążenia, Zapisz i Anuluj przycisków Windows kontrolki BindingNavigator formularzy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], manipulating
- BindingNavigator control [Windows Forms], adding buttons
ms.assetid: faa33042-186e-4bb2-8798-17ceb987ec62
ms.openlocfilehash: d86ded0b93d876eac4b97938678cafbb22c3ac8a
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57722441"
---
# <a name="how-to-add-load-save-and-cancel-buttons-to-the-windows-forms-bindingnavigator-control"></a><span data-ttu-id="3119c-102">Instrukcje: Dodaj obciążenia, Zapisz i Anuluj przycisków Windows kontrolki BindingNavigator formularzy</span><span class="sxs-lookup"><span data-stu-id="3119c-102">How to: Add Load, Save, and Cancel Buttons to the Windows Forms BindingNavigator Control</span></span>
<span data-ttu-id="3119c-103"><xref:System.Windows.Forms.BindingNavigator> Formant jest specjalny <xref:System.Windows.Forms.ToolStrip> formant, który jest przeznaczony do nawigowania i manipulowanie nimi formantów w formularzu, które są powiązane z danymi.</span><span class="sxs-lookup"><span data-stu-id="3119c-103">The <xref:System.Windows.Forms.BindingNavigator> control is a special-purpose <xref:System.Windows.Forms.ToolStrip> control that is intended for navigating and manipulating controls on your form that are bound to data.</span></span>  
  
 <span data-ttu-id="3119c-104">Ponieważ jest on <xref:System.Windows.Forms.ToolStrip> kontroli <xref:System.Windows.Forms.BindingNavigator> składnika można łatwo zmodyfikowany w celu dodania dodatkowych lub alternatywnych poleceń dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="3119c-104">Because it is a <xref:System.Windows.Forms.ToolStrip> control, the <xref:System.Windows.Forms.BindingNavigator> component can be easily modified to include additional or alternative commands for the user.</span></span>  
  
 <span data-ttu-id="3119c-105">W poniższej procedurze <xref:System.Windows.Forms.TextBox> kontrolka jest powiązana z danymi i <xref:System.Windows.Forms.ToolStrip> formant, który zostanie dodany do formularza zostanie zmodyfikowany na potrzeby obejmują Załaduj, Zapisz i przyciski "Anuluj".</span><span class="sxs-lookup"><span data-stu-id="3119c-105">In the following procedure, a <xref:System.Windows.Forms.TextBox> control is bound to data, and the <xref:System.Windows.Forms.ToolStrip> control that is added to the form is modified to include load, save, and cancel buttons.</span></span>  
  
### <a name="to-add-load-save-and-cancel-buttons-to-the-bindingnavigator-component"></a><span data-ttu-id="3119c-106">Aby dodać obciążenia, Zapisz i przyciski do składnika BindingNavigator "Anuluj"</span><span class="sxs-lookup"><span data-stu-id="3119c-106">To add load, save, and cancel buttons to the BindingNavigator component</span></span>  
  
1.  <span data-ttu-id="3119c-107">Dodaj <xref:System.Windows.Forms.TextBox> formantu do formularza.</span><span class="sxs-lookup"><span data-stu-id="3119c-107">Add a <xref:System.Windows.Forms.TextBox> control to your form.</span></span>  
  
2.  <span data-ttu-id="3119c-108">Powiązać <xref:System.Windows.Forms.BindingSource>, która jest powiązana ze źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="3119c-108">Bind it to a <xref:System.Windows.Forms.BindingSource>, which is bound to a data source.</span></span> <span data-ttu-id="3119c-109">W tym przykładzie <xref:System.Windows.Forms.BindingSource> jest powiązana z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="3119c-109">For this example, the <xref:System.Windows.Forms.BindingSource> is bound to a database.</span></span>  
  
3.  <span data-ttu-id="3119c-110">Po wygenerowaniu karty zestaw danych i tabeli, przeciągnij <xref:System.Windows.Forms.BindingNavigator> formantu do formularza.</span><span class="sxs-lookup"><span data-stu-id="3119c-110">After the dataset and table adapter are generated, drag a <xref:System.Windows.Forms.BindingNavigator> control to the form.</span></span>  
  
4.  <span data-ttu-id="3119c-111">Ustaw <xref:System.Windows.Forms.BindingNavigator> kontrolki <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> właściwości <xref:System.Windows.Forms.BindingSource> w formularzu, który jest powiązany z kontrolki.</span><span class="sxs-lookup"><span data-stu-id="3119c-111">Set the <xref:System.Windows.Forms.BindingNavigator> control's <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> property to the <xref:System.Windows.Forms.BindingSource> on the form that is bound to the controls.</span></span>  
  
5.  <span data-ttu-id="3119c-112">Wybierz <xref:System.Windows.Forms.BindingNavigator> kontroli.</span><span class="sxs-lookup"><span data-stu-id="3119c-112">Select the <xref:System.Windows.Forms.BindingNavigator> control.</span></span>  
  
6.  <span data-ttu-id="3119c-113">Kliknij symbol tagu inteligentnego (![symbol tagu inteligentnego](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) więc **zadania BindingNavigator** pojawi się okno dialogowe i wybierz **Edytuj elementy**.</span><span class="sxs-lookup"><span data-stu-id="3119c-113">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) so the **BindingNavigator Tasks** dialog appears and select **Edit Items**.</span></span>  
  
     <span data-ttu-id="3119c-114">**Edytor kolekcji elementów** pojawia się.</span><span class="sxs-lookup"><span data-stu-id="3119c-114">The **Items Collection Editor** appears.</span></span>  
  
7.  <span data-ttu-id="3119c-115">W **Edytor kolekcji elementów**, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="3119c-115">In the **Items Collection Editor**, complete the following:</span></span>  
  
    1.  <span data-ttu-id="3119c-116">Dodaj <xref:System.Windows.Forms.ToolStripSeparator> i trzema <xref:System.Windows.Forms.ToolStripButton> elementów, wybierając odpowiedni typ <xref:System.Windows.Forms.ToolStripItem> i klikając **Dodaj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="3119c-116">Add a <xref:System.Windows.Forms.ToolStripSeparator> and three <xref:System.Windows.Forms.ToolStripButton> items by selecting the appropriate type of <xref:System.Windows.Forms.ToolStripItem> and clicking the **Add** button.</span></span>  
  
    2.  <span data-ttu-id="3119c-117">Ustaw <xref:System.Windows.Forms.ToolStripItem.Name%2A> właściwość przyciski **LoadButton**, **SaveButton**, i **CancelButton**, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="3119c-117">Set the <xref:System.Windows.Forms.ToolStripItem.Name%2A> property of the buttons to **LoadButton**, **SaveButton**, and **CancelButton**, respectively.</span></span>  
  
    3.  <span data-ttu-id="3119c-118">Ustaw <xref:System.Windows.Forms.ToolStripItem.Text%2A> właściwość przyciski **obciążenia**, **Zapisz**, i **anulować**.</span><span class="sxs-lookup"><span data-stu-id="3119c-118">Set the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property of the buttons to **Load**, **Save**, and **Cancel**.</span></span>  
  
    4.  <span data-ttu-id="3119c-119">Ustaw <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> właściwości dla każdego z przycisków, aby **tekstu**.</span><span class="sxs-lookup"><span data-stu-id="3119c-119">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property for each of the buttons to **Text**.</span></span> <span data-ttu-id="3119c-120">Alternatywnie, można ustawić tę właściwość **obraz** lub **ImageAndText**i Ustaw obraz, który ma być wyświetlany w <xref:System.Windows.Forms.ToolStripItem.Image%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="3119c-120">Alternatively, you can set this property to **Image** or **ImageAndText**, and set the image to be displayed in the <xref:System.Windows.Forms.ToolStripItem.Image%2A> property.</span></span>  
  
    5.  <span data-ttu-id="3119c-121">Kliknij przycisk **OK** aby zamknąć okno dialogowe. Przyciski są dodawane do <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="3119c-121">Click **OK** to close the dialog box.The buttons are added to the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
8.  <span data-ttu-id="3119c-122">Kliknij prawym przyciskiem myszy formularz, a następnie wybierz **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="3119c-122">Right-click the form and choose **View Code**.</span></span>  
  
9. <span data-ttu-id="3119c-123">W edytorze kodu Znajdź wiersz kodu, który ładuje dane do karty tabeli.</span><span class="sxs-lookup"><span data-stu-id="3119c-123">In the Code Editor, find the line of code that loads data into the table adapter.</span></span> <span data-ttu-id="3119c-124">Ten kod został wygenerowany podczas tworzenia powiązań danych, w kroku 2.</span><span class="sxs-lookup"><span data-stu-id="3119c-124">This code was generated when you set up the data binding in step 2.</span></span> <span data-ttu-id="3119c-125">Kod powinien być podobny do następującego: `TableAdapterName.Fill(DataSetName.TableName)`.</span><span class="sxs-lookup"><span data-stu-id="3119c-125">The code should be similar to the following: `TableAdapterName.Fill(DataSetName.TableName)`.</span></span> <span data-ttu-id="3119c-126">Będzie ono najbardziej prawdopodobnie w formie <xref:System.Windows.Forms.Form.Load> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="3119c-126">It will most likely be in the form's <xref:System.Windows.Forms.Form.Load> event.</span></span>  
  
10. <span data-ttu-id="3119c-127">Utwórz procedurę obsługi zdarzeń dla <xref:System.Windows.Forms.ToolStripItem.Click> zdarzenia **obciążenia** <xref:System.Windows.Forms.ToolStripButton> utworzonej wcześniej i przenieść ten kod ładowania danych do niego.</span><span class="sxs-lookup"><span data-stu-id="3119c-127">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the **Load** <xref:System.Windows.Forms.ToolStripButton> you created earlier and move this data-loading code into it.</span></span>  
  
     <span data-ttu-id="3119c-128">Kod powinien teraz wyglądać podobnie do poniższej:</span><span class="sxs-lookup"><span data-stu-id="3119c-128">Your code should now look similar to the following:</span></span>  
  
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
  
11. <span data-ttu-id="3119c-129">Utwórz procedurę obsługi zdarzeń dla <xref:System.Windows.Forms.ToolStripItem.Click> zdarzenia **Zapisz** <xref:System.Windows.Forms.ToolStripButton> została utworzona wcześniej, a następnie napisz kod, aby zaktualizować dane w tabeli formant jest powiązany z.</span><span class="sxs-lookup"><span data-stu-id="3119c-129">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the **Save**<xref:System.Windows.Forms.ToolStripButton> you created earlier and write code to update the data within the table the control is bound to.</span></span>  
  
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
    > <span data-ttu-id="3119c-130">W niektórych przypadkach <xref:System.Windows.Forms.BindingNavigator> mają już składnik **Zapisz** przycisk, ale żaden kod nie zostanie wygenerowane przez Windows Forms Designer.</span><span class="sxs-lookup"><span data-stu-id="3119c-130">In some cases, the <xref:System.Windows.Forms.BindingNavigator> component will already have a **Save** button, but no code will have been generated by the Windows Forms Designer.</span></span> <span data-ttu-id="3119c-131">W takim przypadku można umieścić powyższy kod w <xref:System.Windows.Forms.ToolStripItem.Click> program obsługi zdarzeń dla tego przycisku, zamiast tworzenia całkowicie nowego przycisku na <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="3119c-131">In this case, you can place the preceding code in the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for that button, rather than creating an entirely new button on the <xref:System.Windows.Forms.ToolStrip>.</span></span> <span data-ttu-id="3119c-132">Jednak przycisk jest domyślnie wyłączony, musisz więc ustawić <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> właściwości przycisku `true` poprawnie mieć funkcję przycisku.</span><span class="sxs-lookup"><span data-stu-id="3119c-132">However, the button is disabled by default, so you must set the <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> property of the button to `true` to have the button function correctly.</span></span>
  
12. <span data-ttu-id="3119c-133">Utwórz procedurę obsługi zdarzeń dla <xref:System.Windows.Forms.ToolStripItem.Click> zdarzenia **anulować** <xref:System.Windows.Forms.ToolStripButton> utworzonej wcześniej i napisać kod, aby anulować wszelkie zmiany do rekordu danych, która jest wyświetlana.</span><span class="sxs-lookup"><span data-stu-id="3119c-133">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the **Cancel** <xref:System.Windows.Forms.ToolStripButton> you created earlier and write code to cancel any changes to the data record that is displayed.</span></span>  
  
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
    >  <span data-ttu-id="3119c-134"><xref:System.Windows.Forms.BindingSource.CancelEdit%2A> Metody jest ograniczone do wiersza danych.</span><span class="sxs-lookup"><span data-stu-id="3119c-134">The <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> method is scoped to the row of data.</span></span> <span data-ttu-id="3119c-135">Zapisz wszelkie zmiany wprowadzone podczas wyświetlania tego pojedynczego rekordu przed przejdź do następnego rekordu.</span><span class="sxs-lookup"><span data-stu-id="3119c-135">Save any changes you make while viewing that individual record before navigating to the next record.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3119c-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3119c-136">See also</span></span>
- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.ToolStrip>
- [<span data-ttu-id="3119c-137">BindingNavigator, kontrolka</span><span class="sxs-lookup"><span data-stu-id="3119c-137">BindingNavigator Control</span></span>](bindingnavigator-control-windows-forms.md)
- [<span data-ttu-id="3119c-138">BindingSource, składnik — omówienie</span><span class="sxs-lookup"><span data-stu-id="3119c-138">BindingSource Component Overview</span></span>](bindingsource-component-overview.md)
