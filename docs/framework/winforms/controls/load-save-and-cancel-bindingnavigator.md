---
title: Dodawanie przycisków Załaduj, Zapisz i Anuluj do kontrolki BindingNavigator
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], manipulating
- BindingNavigator control [Windows Forms], adding buttons
ms.assetid: faa33042-186e-4bb2-8798-17ceb987ec62
ms.openlocfilehash: 0305df5e7566f9441ce09fa3346a8b2dc67c8943
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77627971"
---
# <a name="how-to-add-load-save-and-cancel-buttons-to-the-windows-forms-bindingnavigator-control"></a><span data-ttu-id="f5a10-102">Porady: dodawanie przycisków załaduj, zapisz i anuluj do kontrolki BindingNavigator formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="f5a10-102">How to: Add Load, Save, and Cancel Buttons to the Windows Forms BindingNavigator Control</span></span>

<span data-ttu-id="f5a10-103">Formant <xref:System.Windows.Forms.BindingNavigator> to specjalny <xref:System.Windows.Forms.ToolStrip> formant, który jest przeznaczony do nawigowania i manipulowania kontrolkami w formularzu, które są powiązane z danymi.</span><span class="sxs-lookup"><span data-stu-id="f5a10-103">The <xref:System.Windows.Forms.BindingNavigator> control is a special-purpose <xref:System.Windows.Forms.ToolStrip> control that is intended for navigating and manipulating controls on your form that are bound to data.</span></span>

<span data-ttu-id="f5a10-104">Ponieważ jest to formant <xref:System.Windows.Forms.ToolStrip>, składnik <xref:System.Windows.Forms.BindingNavigator> można łatwo zmodyfikować w taki sposób, aby obejmował dodatkowe lub alternatywne polecenia dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="f5a10-104">Because it is a <xref:System.Windows.Forms.ToolStrip> control, the <xref:System.Windows.Forms.BindingNavigator> component can be easily modified to include additional or alternative commands for the user.</span></span>

<span data-ttu-id="f5a10-105">W poniższej procedurze formant <xref:System.Windows.Forms.TextBox> jest powiązany z danymi, a kontrolka <xref:System.Windows.Forms.ToolStrip>, która jest dodawana do formularza, zostanie zmodyfikowana w taki sposób, aby obejmowała przyciski Load, Save i Cancel.</span><span class="sxs-lookup"><span data-stu-id="f5a10-105">In the following procedure, a <xref:System.Windows.Forms.TextBox> control is bound to data, and the <xref:System.Windows.Forms.ToolStrip> control that is added to the form is modified to include load, save, and cancel buttons.</span></span>

## <a name="add-load-save-and-cancel-buttons-to-the-bindingnavigator-component"></a><span data-ttu-id="f5a10-106">Dodawanie przycisków Załaduj, Zapisz i Anuluj do składnika BindingNavigator</span><span class="sxs-lookup"><span data-stu-id="f5a10-106">Add load, save, and cancel buttons to the BindingNavigator component</span></span>

1. <span data-ttu-id="f5a10-107">W programie Visual Studio Dodaj kontrolkę <xref:System.Windows.Forms.TextBox> do formularza.</span><span class="sxs-lookup"><span data-stu-id="f5a10-107">In Visual Studio, add a <xref:System.Windows.Forms.TextBox> control to your form.</span></span>

2. <span data-ttu-id="f5a10-108">Powiąż go z <xref:System.Windows.Forms.BindingSource>, który jest powiązany ze źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="f5a10-108">Bind it to a <xref:System.Windows.Forms.BindingSource>, which is bound to a data source.</span></span> <span data-ttu-id="f5a10-109">W tym przykładzie <xref:System.Windows.Forms.BindingSource> jest powiązany z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="f5a10-109">For this example, the <xref:System.Windows.Forms.BindingSource> is bound to a database.</span></span>

3. <span data-ttu-id="f5a10-110">Po wygenerowaniu karty zestawu danych i tabeli przeciągnij kontrolkę <xref:System.Windows.Forms.BindingNavigator> do formularza.</span><span class="sxs-lookup"><span data-stu-id="f5a10-110">After the dataset and table adapter are generated, drag a <xref:System.Windows.Forms.BindingNavigator> control to the form.</span></span>

4. <span data-ttu-id="f5a10-111">Ustaw właściwość <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> kontrolki <xref:System.Windows.Forms.BindingNavigator> na <xref:System.Windows.Forms.BindingSource> w formularzu, który jest powiązany z kontrolkami.</span><span class="sxs-lookup"><span data-stu-id="f5a10-111">Set the <xref:System.Windows.Forms.BindingNavigator> control's <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> property to the <xref:System.Windows.Forms.BindingSource> on the form that is bound to the controls.</span></span>

5. <span data-ttu-id="f5a10-112">Wybierz kontrolkę <xref:System.Windows.Forms.BindingNavigator>.</span><span class="sxs-lookup"><span data-stu-id="f5a10-112">Select the <xref:System.Windows.Forms.BindingNavigator> control.</span></span>

6. <span data-ttu-id="f5a10-113">Kliknij symbol akcji projektanta (![małą czarną strzałkę](./media/designer-actions-glyph.gif)), a następnie wyświetlenie okna dialogowego **zadania BindingNavigator** i wybierz pozycję **Edytuj elementy**.</span><span class="sxs-lookup"><span data-stu-id="f5a10-113">Click the designer actions glyph (![Small black arrow](./media/designer-actions-glyph.gif)) so the **BindingNavigator Tasks** dialog appears and select **Edit Items**.</span></span>

     <span data-ttu-id="f5a10-114">Zostanie wyświetlony **Edytor kolekcji Items** .</span><span class="sxs-lookup"><span data-stu-id="f5a10-114">The **Items Collection Editor** appears.</span></span>

7. <span data-ttu-id="f5a10-115">W **edytorze kolekcji elementów**wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="f5a10-115">In the **Items Collection Editor**, complete the following:</span></span>

    1. <span data-ttu-id="f5a10-116">Dodaj <xref:System.Windows.Forms.ToolStripSeparator> i trzy elementy <xref:System.Windows.Forms.ToolStripButton>, wybierając odpowiedni typ <xref:System.Windows.Forms.ToolStripItem> i klikając przycisk **Dodaj** .</span><span class="sxs-lookup"><span data-stu-id="f5a10-116">Add a <xref:System.Windows.Forms.ToolStripSeparator> and three <xref:System.Windows.Forms.ToolStripButton> items by selecting the appropriate type of <xref:System.Windows.Forms.ToolStripItem> and clicking the **Add** button.</span></span>

    2. <span data-ttu-id="f5a10-117">Ustaw odpowiednio Właściwość <xref:System.Windows.Forms.ToolStripItem.Name%2A> przycisków **LoadButton**, **SaveButton**i **CancelButton**.</span><span class="sxs-lookup"><span data-stu-id="f5a10-117">Set the <xref:System.Windows.Forms.ToolStripItem.Name%2A> property of the buttons to **LoadButton**, **SaveButton**, and **CancelButton**, respectively.</span></span>

    3. <span data-ttu-id="f5a10-118">Ustaw właściwość <xref:System.Windows.Forms.ToolStripItem.Text%2A> przycisków do **załadowania**, **zapisania**i **anulowania**.</span><span class="sxs-lookup"><span data-stu-id="f5a10-118">Set the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property of the buttons to **Load**, **Save**, and **Cancel**.</span></span>

    4. <span data-ttu-id="f5a10-119">Ustaw właściwość <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> dla każdego przycisku na **tekst**.</span><span class="sxs-lookup"><span data-stu-id="f5a10-119">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property for each of the buttons to **Text**.</span></span> <span data-ttu-id="f5a10-120">Alternatywnie możesz ustawić tę właściwość na **Image** lub **ImageAndText**i ustawić obraz, który ma być wyświetlany we właściwości <xref:System.Windows.Forms.ToolStripItem.Image%2A>.</span><span class="sxs-lookup"><span data-stu-id="f5a10-120">Alternatively, you can set this property to **Image** or **ImageAndText**, and set the image to be displayed in the <xref:System.Windows.Forms.ToolStripItem.Image%2A> property.</span></span>

    5. <span data-ttu-id="f5a10-121">Kliknij przycisk **OK**, aby zamknąć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="f5a10-121">Click **OK** to close the dialog box.</span></span> <span data-ttu-id="f5a10-122">Przyciski są dodawane do <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="f5a10-122">The buttons are added to the <xref:System.Windows.Forms.ToolStrip>.</span></span>

8. <span data-ttu-id="f5a10-123">Kliknij prawym przyciskiem myszy formularz i wybierz polecenie **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="f5a10-123">Right-click the form and choose **View Code**.</span></span>

9. <span data-ttu-id="f5a10-124">W edytorze kodu Znajdź wiersz kodu, który ładuje dane do karty tabeli.</span><span class="sxs-lookup"><span data-stu-id="f5a10-124">In the Code Editor, find the line of code that loads data into the table adapter.</span></span> <span data-ttu-id="f5a10-125">Ten kod został wygenerowany podczas konfigurowania powiązania danych w kroku 2.</span><span class="sxs-lookup"><span data-stu-id="f5a10-125">This code was generated when you set up the data binding in step 2.</span></span> <span data-ttu-id="f5a10-126">Kod powinien wyglądać podobnie do poniższego: `TableAdapterName.Fill(DataSetName.TableName)`.</span><span class="sxs-lookup"><span data-stu-id="f5a10-126">The code should be similar to the following: `TableAdapterName.Fill(DataSetName.TableName)`.</span></span> <span data-ttu-id="f5a10-127">Najprawdopodobniej będzie to w zdarzeniu <xref:System.Windows.Forms.Form.Load> formularza.</span><span class="sxs-lookup"><span data-stu-id="f5a10-127">It will most likely be in the form's <xref:System.Windows.Forms.Form.Load> event.</span></span>

10. <span data-ttu-id="f5a10-128">Utwórz procedurę obsługi zdarzeń dla zdarzenia <xref:System.Windows.Forms.ToolStripItem.Click> <xref:System.Windows.Forms.ToolStripButton> **Załaduj** wcześniej utworzonego i Przenieś do niego ten kod ładowania danych.</span><span class="sxs-lookup"><span data-stu-id="f5a10-128">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the **Load** <xref:System.Windows.Forms.ToolStripButton> you created earlier and move this data-loading code into it.</span></span>

     <span data-ttu-id="f5a10-129">Kod powinien teraz wyglądać podobnie do poniższego:</span><span class="sxs-lookup"><span data-stu-id="f5a10-129">Your code should now look similar to the following:</span></span>

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

11. <span data-ttu-id="f5a10-130">Utwórz procedurę obsługi zdarzeń dla zdarzenia <xref:System.Windows.Forms.ToolStripItem.Click> utworzonego wcześniej<xref:System.Windows.Forms.ToolStripButton> **zapisywania** i napisz kod, aby zaktualizować dane w tabeli, z którą jest powiązany formant.</span><span class="sxs-lookup"><span data-stu-id="f5a10-130">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the **Save**<xref:System.Windows.Forms.ToolStripButton> you created earlier and write code to update the data within the table the control is bound to.</span></span>

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
    > <span data-ttu-id="f5a10-131">W niektórych przypadkach składnik <xref:System.Windows.Forms.BindingNavigator> ma już przycisk **Zapisz** , ale nie Wygenerowano żadnego kodu przez Projektant formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="f5a10-131">In some cases, the <xref:System.Windows.Forms.BindingNavigator> component already has a **Save** button, but no code has been generated by the Windows Forms Designer.</span></span> <span data-ttu-id="f5a10-132">W takim przypadku można umieścić poprzedni kod w obsłudze zdarzeń <xref:System.Windows.Forms.ToolStripItem.Click> dla tego przycisku zamiast tworzyć zupełnie nowy przycisk na <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="f5a10-132">In this case, you can place the preceding code in the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for that button, rather than creating an entirely new button on the <xref:System.Windows.Forms.ToolStrip>.</span></span> <span data-ttu-id="f5a10-133">Jednak przycisk jest domyślnie wyłączony, dlatego należy ustawić właściwość <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> przycisku, aby `true`, aby działał poprawnie.</span><span class="sxs-lookup"><span data-stu-id="f5a10-133">However, the button is disabled by default, so you must set the <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> property of the button to `true` to have the button function correctly.</span></span>

12. <span data-ttu-id="f5a10-134">Utwórz procedurę obsługi zdarzeń dla zdarzenia <xref:System.Windows.Forms.ToolStripItem.Click> <xref:System.Windows.Forms.ToolStripButton> utworzonego wcześniej i napisz **kod, aby** anulować wszystkie zmiany w wyświetlonym rekordzie danych.</span><span class="sxs-lookup"><span data-stu-id="f5a10-134">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the **Cancel** <xref:System.Windows.Forms.ToolStripButton> you created earlier and write code to cancel any changes to the data record that is displayed.</span></span>

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
    > <span data-ttu-id="f5a10-135">Metoda <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> jest objęta zakresem wierszy danych.</span><span class="sxs-lookup"><span data-stu-id="f5a10-135">The <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> method is scoped to the row of data.</span></span> <span data-ttu-id="f5a10-136">Zapisz wszelkie zmiany wprowadzone podczas wyświetlania danego rekordu przed przejściem do następnego rekordu.</span><span class="sxs-lookup"><span data-stu-id="f5a10-136">Save any changes you make while viewing that individual record before navigating to the next record.</span></span>

## <a name="see-also"></a><span data-ttu-id="f5a10-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f5a10-137">See also</span></span>

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.ToolStrip>
- [<span data-ttu-id="f5a10-138">BindingNavigator, kontrolka</span><span class="sxs-lookup"><span data-stu-id="f5a10-138">BindingNavigator Control</span></span>](bindingnavigator-control-windows-forms.md)
- [<span data-ttu-id="f5a10-139">BindingSource, składnik — omówienie</span><span class="sxs-lookup"><span data-stu-id="f5a10-139">BindingSource Component Overview</span></span>](bindingsource-component-overview.md)
