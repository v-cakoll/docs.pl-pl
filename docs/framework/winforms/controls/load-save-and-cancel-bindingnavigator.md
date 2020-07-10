---
title: Dodawanie przycisków Załaduj, Zapisz i Anuluj do kontrolki BindingNavigator
description: Dowiedz się, jak dodać przyciski Załaduj, Zapisz i Anuluj do kontrolki Windows Forms BindingNavigator.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], manipulating
- BindingNavigator control [Windows Forms], adding buttons
ms.assetid: faa33042-186e-4bb2-8798-17ceb987ec62
ms.openlocfilehash: d4db91b8cfaf2df253d0c4cf5d8a66e9157d4986
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86173422"
---
# <a name="how-to-add-load-save-and-cancel-buttons-to-the-windows-forms-bindingnavigator-control"></a><span data-ttu-id="b6fcb-103">Porady: dodawanie przycisków załaduj, zapisz i anuluj do kontrolki BindingNavigator formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b6fcb-103">How to: Add Load, Save, and Cancel Buttons to the Windows Forms BindingNavigator Control</span></span>

<span data-ttu-id="b6fcb-104"><xref:System.Windows.Forms.BindingNavigator>Formant jest <xref:System.Windows.Forms.ToolStrip> formantem specjalnego przeznaczenia, który jest przeznaczony do nawigowania i manipulowania kontrolkami w formularzu, które są powiązane z danymi.</span><span class="sxs-lookup"><span data-stu-id="b6fcb-104">The <xref:System.Windows.Forms.BindingNavigator> control is a special-purpose <xref:System.Windows.Forms.ToolStrip> control that is intended for navigating and manipulating controls on your form that are bound to data.</span></span>

<span data-ttu-id="b6fcb-105">Ponieważ jest to <xref:System.Windows.Forms.ToolStrip> formant, <xref:System.Windows.Forms.BindingNavigator> składnik można łatwo zmodyfikować w taki sposób, aby obejmował dodatkowe lub alternatywne polecenia dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b6fcb-105">Because it's a <xref:System.Windows.Forms.ToolStrip> control, the <xref:System.Windows.Forms.BindingNavigator> component can be easily modified to include additional or alternative commands for the user.</span></span>

<span data-ttu-id="b6fcb-106">W poniższej procedurze <xref:System.Windows.Forms.TextBox> formant jest powiązany z danymi, a <xref:System.Windows.Forms.ToolStrip> kontrolka dodana do formularza zostanie zmodyfikowana w celu uwzględnienia przycisków ładowania, zapisywania i anulowania.</span><span class="sxs-lookup"><span data-stu-id="b6fcb-106">In the following procedure, a <xref:System.Windows.Forms.TextBox> control is bound to data, and the <xref:System.Windows.Forms.ToolStrip> control that is added to the form is modified to include load, save, and cancel buttons.</span></span>

## <a name="add-load-save-and-cancel-buttons-to-the-bindingnavigator-component"></a><span data-ttu-id="b6fcb-107">Dodawanie przycisków Załaduj, Zapisz i Anuluj do składnika BindingNavigator</span><span class="sxs-lookup"><span data-stu-id="b6fcb-107">Add load, save, and cancel buttons to the BindingNavigator component</span></span>

1. <span data-ttu-id="b6fcb-108">W programie Visual Studio Dodaj <xref:System.Windows.Forms.TextBox> kontrolkę do formularza.</span><span class="sxs-lookup"><span data-stu-id="b6fcb-108">In Visual Studio, add a <xref:System.Windows.Forms.TextBox> control to your form.</span></span>

2. <span data-ttu-id="b6fcb-109">Powiąż go z <xref:System.Windows.Forms.BindingSource> , który jest powiązany ze źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="b6fcb-109">Bind it to a <xref:System.Windows.Forms.BindingSource>, which is bound to a data source.</span></span> <span data-ttu-id="b6fcb-110">W tym przykładzie jest on <xref:System.Windows.Forms.BindingSource> powiązany z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="b6fcb-110">For this example, the <xref:System.Windows.Forms.BindingSource> is bound to a database.</span></span>

3. <span data-ttu-id="b6fcb-111">Po wygenerowaniu zestawu danych i karty tabeli przeciągnij <xref:System.Windows.Forms.BindingNavigator> kontrolkę do formularza.</span><span class="sxs-lookup"><span data-stu-id="b6fcb-111">After the dataset and table adapter are generated, drag a <xref:System.Windows.Forms.BindingNavigator> control to the form.</span></span>

4. <span data-ttu-id="b6fcb-112">Ustaw <xref:System.Windows.Forms.BindingNavigator> Właściwość kontrolki <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> <xref:System.Windows.Forms.BindingSource> na formularzu, który jest powiązany z kontrolkami.</span><span class="sxs-lookup"><span data-stu-id="b6fcb-112">Set the <xref:System.Windows.Forms.BindingNavigator> control's <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> property to the <xref:System.Windows.Forms.BindingSource> on the form that is bound to the controls.</span></span>

5. <span data-ttu-id="b6fcb-113">Zaznacz <xref:System.Windows.Forms.BindingNavigator> kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="b6fcb-113">Select the <xref:System.Windows.Forms.BindingNavigator> control.</span></span>

6. <span data-ttu-id="b6fcb-114">Kliknij symbol akcji projektanta ( ![ Mała czarna strzałka ](./media/designer-actions-glyph.gif) ), aby okno dialogowe **BindingNavigator zadania** pojawiło się i wybierz pozycję **Edytuj elementy**.</span><span class="sxs-lookup"><span data-stu-id="b6fcb-114">Click the designer actions glyph (![Small black arrow](./media/designer-actions-glyph.gif)) so the **BindingNavigator Tasks** dialog appears and select **Edit Items**.</span></span>

     <span data-ttu-id="b6fcb-115">Zostanie wyświetlony **Edytor kolekcji Items** .</span><span class="sxs-lookup"><span data-stu-id="b6fcb-115">The **Items Collection Editor** appears.</span></span>

7. <span data-ttu-id="b6fcb-116">W **edytorze kolekcji elementów**wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="b6fcb-116">In the **Items Collection Editor**, complete the following:</span></span>

    1. <span data-ttu-id="b6fcb-117">Dodaj a <xref:System.Windows.Forms.ToolStripSeparator> i trzy <xref:System.Windows.Forms.ToolStripButton> elementy, wybierając odpowiedni typ <xref:System.Windows.Forms.ToolStripItem> i klikając przycisk **Dodaj** .</span><span class="sxs-lookup"><span data-stu-id="b6fcb-117">Add a <xref:System.Windows.Forms.ToolStripSeparator> and three <xref:System.Windows.Forms.ToolStripButton> items by selecting the appropriate type of <xref:System.Windows.Forms.ToolStripItem> and clicking the **Add** button.</span></span>

    2. <span data-ttu-id="b6fcb-118">Ustaw <xref:System.Windows.Forms.ToolStripItem.Name%2A> odpowiednio Właściwość przycisków na **LoadButton**, **SaveButton**i **CancelButton**.</span><span class="sxs-lookup"><span data-stu-id="b6fcb-118">Set the <xref:System.Windows.Forms.ToolStripItem.Name%2A> property of the buttons to **LoadButton**, **SaveButton**, and **CancelButton**, respectively.</span></span>

    3. <span data-ttu-id="b6fcb-119">Ustaw <xref:System.Windows.Forms.ToolStripItem.Text%2A> Właściwość przycisków do **załadowania**, **zapisania**i **anulowania**.</span><span class="sxs-lookup"><span data-stu-id="b6fcb-119">Set the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property of the buttons to **Load**, **Save**, and **Cancel**.</span></span>

    4. <span data-ttu-id="b6fcb-120">Ustaw <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> Właściwość dla każdego przycisku na **tekst**.</span><span class="sxs-lookup"><span data-stu-id="b6fcb-120">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property for each of the buttons to **Text**.</span></span> <span data-ttu-id="b6fcb-121">Alternatywnie możesz ustawić tę właściwość na **Image** lub **ImageAndText**i ustawić obraz, który ma być wyświetlany we <xref:System.Windows.Forms.ToolStripItem.Image%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="b6fcb-121">Alternatively, you can set this property to **Image** or **ImageAndText**, and set the image to be displayed in the <xref:System.Windows.Forms.ToolStripItem.Image%2A> property.</span></span>

    5. <span data-ttu-id="b6fcb-122">Kliknij przycisk **OK**, aby zamknąć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="b6fcb-122">Click **OK** to close the dialog box.</span></span> <span data-ttu-id="b6fcb-123">Przyciski zostaną dodane do <xref:System.Windows.Forms.ToolStrip> .</span><span class="sxs-lookup"><span data-stu-id="b6fcb-123">The buttons are added to the <xref:System.Windows.Forms.ToolStrip>.</span></span>

8. <span data-ttu-id="b6fcb-124">Kliknij prawym przyciskiem myszy formularz i wybierz polecenie **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="b6fcb-124">Right-click the form and choose **View Code**.</span></span>

9. <span data-ttu-id="b6fcb-125">W edytorze kodu Znajdź wiersz kodu, który ładuje dane do karty tabeli.</span><span class="sxs-lookup"><span data-stu-id="b6fcb-125">In the Code Editor, find the line of code that loads data into the table adapter.</span></span> <span data-ttu-id="b6fcb-126">Ten kod został wygenerowany podczas konfigurowania powiązania danych w kroku 2.</span><span class="sxs-lookup"><span data-stu-id="b6fcb-126">This code was generated when you set up the data binding in step 2.</span></span> <span data-ttu-id="b6fcb-127">Kod powinien wyglądać podobnie do poniższego: `TableAdapterName.Fill(DataSetName.TableName)` .</span><span class="sxs-lookup"><span data-stu-id="b6fcb-127">The code should be similar to the following: `TableAdapterName.Fill(DataSetName.TableName)`.</span></span> <span data-ttu-id="b6fcb-128">Najprawdopodobniej będzie to w <xref:System.Windows.Forms.Form.Load> przypadku zdarzenia formularza.</span><span class="sxs-lookup"><span data-stu-id="b6fcb-128">It will most likely be in the form's <xref:System.Windows.Forms.Form.Load> event.</span></span>

10. <span data-ttu-id="b6fcb-129">Utwórz procedurę obsługi zdarzeń dla <xref:System.Windows.Forms.ToolStripItem.Click> zdarzenia **Load** <xref:System.Windows.Forms.ToolStripButton> utworzonego wcześniej ładowania i Przenieś do niego ten kod ładowania danych.</span><span class="sxs-lookup"><span data-stu-id="b6fcb-129">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the **Load** <xref:System.Windows.Forms.ToolStripButton> you created earlier and move this data-loading code into it.</span></span>

     <span data-ttu-id="b6fcb-130">Kod powinien teraz wyglądać podobnie do poniższego:</span><span class="sxs-lookup"><span data-stu-id="b6fcb-130">Your code should now look similar to the following:</span></span>

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

11. <span data-ttu-id="b6fcb-131">Utwórz procedurę obsługi zdarzeń dla <xref:System.Windows.Forms.ToolStripItem.Click> zdarzenia **Save** <xref:System.Windows.Forms.ToolStripButton> utworzonego wcześniej zapisu i napisz kod, aby zaktualizować dane w tabeli, z którą jest powiązany formant.</span><span class="sxs-lookup"><span data-stu-id="b6fcb-131">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the **Save**<xref:System.Windows.Forms.ToolStripButton> you created earlier and write code to update the data within the table the control is bound to.</span></span>

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
    > <span data-ttu-id="b6fcb-132">W niektórych przypadkach <xref:System.Windows.Forms.BindingNavigator> składnik ma już przycisk **Zapisz** , ale nie Wygenerowano żadnego kodu przez Projektant formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="b6fcb-132">In some cases, the <xref:System.Windows.Forms.BindingNavigator> component already has a **Save** button, but no code has been generated by the Windows Forms Designer.</span></span> <span data-ttu-id="b6fcb-133">W takim przypadku można umieścić poprzedni kod w <xref:System.Windows.Forms.ToolStripItem.Click> obsłudze zdarzeń dla tego przycisku zamiast tworzyć zupełnie nowy przycisk na <xref:System.Windows.Forms.ToolStrip> .</span><span class="sxs-lookup"><span data-stu-id="b6fcb-133">In this case, you can place the preceding code in the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for that button, rather than creating an entirely new button on the <xref:System.Windows.Forms.ToolStrip>.</span></span> <span data-ttu-id="b6fcb-134">Jednak przycisk jest domyślnie wyłączony, dlatego należy ustawić <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> Właściwość przycisku na tak, aby `true` działał poprawnie.</span><span class="sxs-lookup"><span data-stu-id="b6fcb-134">However, the button is disabled by default, so you must set the <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> property of the button to `true` to have the button function correctly.</span></span>

12. <span data-ttu-id="b6fcb-135">Utwórz procedurę obsługi zdarzeń dla <xref:System.Windows.Forms.ToolStripItem.Click> zdarzenia **anulowania** <xref:System.Windows.Forms.ToolStripButton> utworzonego wcześniej i napisz kod, aby anulować wszystkie zmiany w wyświetlonym rekordzie danych.</span><span class="sxs-lookup"><span data-stu-id="b6fcb-135">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the **Cancel** <xref:System.Windows.Forms.ToolStripButton> you created earlier and write code to cancel any changes to the data record that is displayed.</span></span>

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
    > <span data-ttu-id="b6fcb-136"><xref:System.Windows.Forms.BindingSource.CancelEdit%2A>Metoda jest objęta zakresem wierszy danych.</span><span class="sxs-lookup"><span data-stu-id="b6fcb-136">The <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> method is scoped to the row of data.</span></span> <span data-ttu-id="b6fcb-137">Zapisz wszelkie zmiany wprowadzone podczas wyświetlania danego rekordu przed przejściem do następnego rekordu.</span><span class="sxs-lookup"><span data-stu-id="b6fcb-137">Save any changes you make while viewing that individual record before navigating to the next record.</span></span>

## <a name="see-also"></a><span data-ttu-id="b6fcb-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b6fcb-138">See also</span></span>

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.ToolStrip>
- [<span data-ttu-id="b6fcb-139">BindingNavigator — Formant</span><span class="sxs-lookup"><span data-stu-id="b6fcb-139">BindingNavigator Control</span></span>](bindingnavigator-control-windows-forms.md)
- [<span data-ttu-id="b6fcb-140">BindingSource — Informacje o składniku</span><span class="sxs-lookup"><span data-stu-id="b6fcb-140">BindingSource Component Overview</span></span>](bindingsource-component-overview.md)
