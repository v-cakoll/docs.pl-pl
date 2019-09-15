---
title: 'Instrukcje: dodawanie przycisków załaduj, zapisz i anuluj do kontrolki BindingNavigator formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], manipulating
- BindingNavigator control [Windows Forms], adding buttons
ms.assetid: faa33042-186e-4bb2-8798-17ceb987ec62
ms.openlocfilehash: 2d4867c0bc4feb7b43e15614fc56a3c709cef9e7
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991742"
---
# <a name="how-to-add-load-save-and-cancel-buttons-to-the-windows-forms-bindingnavigator-control"></a><span data-ttu-id="04819-102">Instrukcje: dodawanie przycisków załaduj, zapisz i anuluj do kontrolki BindingNavigator formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="04819-102">How to: Add Load, Save, and Cancel Buttons to the Windows Forms BindingNavigator Control</span></span>

<span data-ttu-id="04819-103">Formant jest formantem specjalnego przeznaczenia <xref:System.Windows.Forms.ToolStrip> , który jest przeznaczony do nawigowania i manipulowania kontrolkami w formularzu, które są powiązane z danymi. <xref:System.Windows.Forms.BindingNavigator></span><span class="sxs-lookup"><span data-stu-id="04819-103">The <xref:System.Windows.Forms.BindingNavigator> control is a special-purpose <xref:System.Windows.Forms.ToolStrip> control that is intended for navigating and manipulating controls on your form that are bound to data.</span></span>

<span data-ttu-id="04819-104">Ponieważ jest <xref:System.Windows.Forms.ToolStrip> to formant <xref:System.Windows.Forms.BindingNavigator> , składnik można łatwo zmodyfikować w taki sposób, aby obejmował dodatkowe lub alternatywne polecenia dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="04819-104">Because it is a <xref:System.Windows.Forms.ToolStrip> control, the <xref:System.Windows.Forms.BindingNavigator> component can be easily modified to include additional or alternative commands for the user.</span></span>

<span data-ttu-id="04819-105">W poniższej procedurze <xref:System.Windows.Forms.TextBox> formant jest powiązany z danymi, <xref:System.Windows.Forms.ToolStrip> a kontrolka dodana do formularza zostanie zmodyfikowana w celu uwzględnienia przycisków ładowania, zapisywania i anulowania.</span><span class="sxs-lookup"><span data-stu-id="04819-105">In the following procedure, a <xref:System.Windows.Forms.TextBox> control is bound to data, and the <xref:System.Windows.Forms.ToolStrip> control that is added to the form is modified to include load, save, and cancel buttons.</span></span>

## <a name="add-load-save-and-cancel-buttons-to-the-bindingnavigator-component"></a><span data-ttu-id="04819-106">Dodawanie przycisków Załaduj, Zapisz i Anuluj do składnika BindingNavigator</span><span class="sxs-lookup"><span data-stu-id="04819-106">Add load, save, and cancel buttons to the BindingNavigator component</span></span>

1. <span data-ttu-id="04819-107">W programie Visual Studio Dodaj <xref:System.Windows.Forms.TextBox> kontrolkę do formularza.</span><span class="sxs-lookup"><span data-stu-id="04819-107">In Visual Studio, add a <xref:System.Windows.Forms.TextBox> control to your form.</span></span>

2. <span data-ttu-id="04819-108">Powiąż go z <xref:System.Windows.Forms.BindingSource>, który jest powiązany ze źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="04819-108">Bind it to a <xref:System.Windows.Forms.BindingSource>, which is bound to a data source.</span></span> <span data-ttu-id="04819-109">W tym przykładzie <xref:System.Windows.Forms.BindingSource> jest on powiązany z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="04819-109">For this example, the <xref:System.Windows.Forms.BindingSource> is bound to a database.</span></span>

3. <span data-ttu-id="04819-110">Po wygenerowaniu zestawu danych i karty tabeli przeciągnij <xref:System.Windows.Forms.BindingNavigator> kontrolkę do formularza.</span><span class="sxs-lookup"><span data-stu-id="04819-110">After the dataset and table adapter are generated, drag a <xref:System.Windows.Forms.BindingNavigator> control to the form.</span></span>

4. <span data-ttu-id="04819-111"><xref:System.Windows.Forms.BindingNavigator> Ustaw Właściwość<xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> kontrolki na formularzu, który jest powiązany z kontrolkami. <xref:System.Windows.Forms.BindingSource></span><span class="sxs-lookup"><span data-stu-id="04819-111">Set the <xref:System.Windows.Forms.BindingNavigator> control's <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> property to the <xref:System.Windows.Forms.BindingSource> on the form that is bound to the controls.</span></span>

5. <span data-ttu-id="04819-112"><xref:System.Windows.Forms.BindingNavigator> Zaznacz kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="04819-112">Select the <xref:System.Windows.Forms.BindingNavigator> control.</span></span>

6. <span data-ttu-id="04819-113">Kliknij symbol taga inteligentnego (![tag inteligentny](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")), aby otworzyć okno dialogowe **zadania** , a następnie wybierz pozycję **Edytuj elementy**.</span><span class="sxs-lookup"><span data-stu-id="04819-113">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) so the **BindingNavigator Tasks** dialog appears and select **Edit Items**.</span></span>

     <span data-ttu-id="04819-114">Zostanie wyświetlony **Edytor kolekcji Items** .</span><span class="sxs-lookup"><span data-stu-id="04819-114">The **Items Collection Editor** appears.</span></span>

7. <span data-ttu-id="04819-115">W **edytorze kolekcji elementów**wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="04819-115">In the **Items Collection Editor**, complete the following:</span></span>

    1. <span data-ttu-id="04819-116">Dodaj a <xref:System.Windows.Forms.ToolStripButton>itrzy elementy, <xref:System.Windows.Forms.ToolStripItem> wybierając odpowiedni typ i klikając przycisk Dodaj. <xref:System.Windows.Forms.ToolStripSeparator></span><span class="sxs-lookup"><span data-stu-id="04819-116">Add a <xref:System.Windows.Forms.ToolStripSeparator> and three <xref:System.Windows.Forms.ToolStripButton> items by selecting the appropriate type of <xref:System.Windows.Forms.ToolStripItem> and clicking the **Add** button.</span></span>

    2. <span data-ttu-id="04819-117">Ustaw odpowiednioWłaściwość przycisków na LoadButton, SaveButton i CancelButton. <xref:System.Windows.Forms.ToolStripItem.Name%2A></span><span class="sxs-lookup"><span data-stu-id="04819-117">Set the <xref:System.Windows.Forms.ToolStripItem.Name%2A> property of the buttons to **LoadButton**, **SaveButton**, and **CancelButton**, respectively.</span></span>

    3. <span data-ttu-id="04819-118">Ustaw właściwość przycisków do **załadowania**, **zapisania**i **anulowania.** <xref:System.Windows.Forms.ToolStripItem.Text%2A></span><span class="sxs-lookup"><span data-stu-id="04819-118">Set the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property of the buttons to **Load**, **Save**, and **Cancel**.</span></span>

    4. <span data-ttu-id="04819-119">Ustaw właściwość dla każdego przycisku na **tekst.** <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A></span><span class="sxs-lookup"><span data-stu-id="04819-119">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property for each of the buttons to **Text**.</span></span> <span data-ttu-id="04819-120">Alternatywnie możesz ustawić tę właściwość na **Image** lub **ImageAndText**i ustawić obraz, który ma być <xref:System.Windows.Forms.ToolStripItem.Image%2A> wyświetlany we właściwości.</span><span class="sxs-lookup"><span data-stu-id="04819-120">Alternatively, you can set this property to **Image** or **ImageAndText**, and set the image to be displayed in the <xref:System.Windows.Forms.ToolStripItem.Image%2A> property.</span></span>

    5. <span data-ttu-id="04819-121">Kliknij przycisk **OK** , aby zamknąć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="04819-121">Click **OK** to close the dialog box.</span></span> <span data-ttu-id="04819-122">Przyciski zostaną dodane do <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="04819-122">The buttons are added to the <xref:System.Windows.Forms.ToolStrip>.</span></span>

8. <span data-ttu-id="04819-123">Kliknij prawym przyciskiem myszy formularz i wybierz polecenie **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="04819-123">Right-click the form and choose **View Code**.</span></span>

9. <span data-ttu-id="04819-124">W edytorze kodu Znajdź wiersz kodu, który ładuje dane do karty tabeli.</span><span class="sxs-lookup"><span data-stu-id="04819-124">In the Code Editor, find the line of code that loads data into the table adapter.</span></span> <span data-ttu-id="04819-125">Ten kod został wygenerowany podczas konfigurowania powiązania danych w kroku 2.</span><span class="sxs-lookup"><span data-stu-id="04819-125">This code was generated when you set up the data binding in step 2.</span></span> <span data-ttu-id="04819-126">Kod powinien wyglądać podobnie do poniższego: `TableAdapterName.Fill(DataSetName.TableName)`.</span><span class="sxs-lookup"><span data-stu-id="04819-126">The code should be similar to the following: `TableAdapterName.Fill(DataSetName.TableName)`.</span></span> <span data-ttu-id="04819-127">Najprawdopodobniej będzie to w <xref:System.Windows.Forms.Form.Load> przypadku zdarzenia formularza.</span><span class="sxs-lookup"><span data-stu-id="04819-127">It will most likely be in the form's <xref:System.Windows.Forms.Form.Load> event.</span></span>

10. <span data-ttu-id="04819-128">Utwórz procedurę obsługi zdarzeń dla <xref:System.Windows.Forms.ToolStripItem.Click> zdarzenia utworzonego wcześniej **ładowania** <xref:System.Windows.Forms.ToolStripButton> i Przenieś do niego ten kod ładowania danych.</span><span class="sxs-lookup"><span data-stu-id="04819-128">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the **Load** <xref:System.Windows.Forms.ToolStripButton> you created earlier and move this data-loading code into it.</span></span>

     <span data-ttu-id="04819-129">Kod powinien teraz wyglądać podobnie do poniższego:</span><span class="sxs-lookup"><span data-stu-id="04819-129">Your code should now look similar to the following:</span></span>

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

11. <span data-ttu-id="04819-130">Utwórz procedurę obsługi zdarzeń dla <xref:System.Windows.Forms.ToolStripItem.Click> zdarzenia utworzonego wcześniej **zapisu** <xref:System.Windows.Forms.ToolStripButton> i napisz kod, aby zaktualizować dane w tabeli, z którą jest powiązany formant.</span><span class="sxs-lookup"><span data-stu-id="04819-130">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the **Save**<xref:System.Windows.Forms.ToolStripButton> you created earlier and write code to update the data within the table the control is bound to.</span></span>

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
    > <span data-ttu-id="04819-131">W niektórych przypadkach <xref:System.Windows.Forms.BindingNavigator> składnik ma już przycisk **Zapisz** , ale nie Wygenerowano żadnego kodu przez Projektant formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="04819-131">In some cases, the <xref:System.Windows.Forms.BindingNavigator> component already has a **Save** button, but no code has been generated by the Windows Forms Designer.</span></span> <span data-ttu-id="04819-132">W takim przypadku można umieścić poprzedni kod w <xref:System.Windows.Forms.ToolStripItem.Click> obsłudze zdarzeń dla tego przycisku zamiast tworzyć zupełnie nowy przycisk <xref:System.Windows.Forms.ToolStrip>na.</span><span class="sxs-lookup"><span data-stu-id="04819-132">In this case, you can place the preceding code in the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for that button, rather than creating an entirely new button on the <xref:System.Windows.Forms.ToolStrip>.</span></span> <span data-ttu-id="04819-133">Jednak przycisk jest domyślnie wyłączony, dlatego należy ustawić <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> właściwość przycisku na `true` tak, aby działał poprawnie.</span><span class="sxs-lookup"><span data-stu-id="04819-133">However, the button is disabled by default, so you must set the <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> property of the button to `true` to have the button function correctly.</span></span>

12. <span data-ttu-id="04819-134">Utwórz procedurę obsługi zdarzeń dla <xref:System.Windows.Forms.ToolStripItem.Click> zdarzenia **anulowania** <xref:System.Windows.Forms.ToolStripButton> utworzonego wcześniej i napisz kod, aby anulować wszystkie zmiany w wyświetlonym rekordzie danych.</span><span class="sxs-lookup"><span data-stu-id="04819-134">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the **Cancel** <xref:System.Windows.Forms.ToolStripButton> you created earlier and write code to cancel any changes to the data record that is displayed.</span></span>

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
    > <span data-ttu-id="04819-135"><xref:System.Windows.Forms.BindingSource.CancelEdit%2A> Metoda jest objęta zakresem wierszy danych.</span><span class="sxs-lookup"><span data-stu-id="04819-135">The <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> method is scoped to the row of data.</span></span> <span data-ttu-id="04819-136">Zapisz wszelkie zmiany wprowadzone podczas wyświetlania danego rekordu przed przejściem do następnego rekordu.</span><span class="sxs-lookup"><span data-stu-id="04819-136">Save any changes you make while viewing that individual record before navigating to the next record.</span></span>

## <a name="see-also"></a><span data-ttu-id="04819-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="04819-137">See also</span></span>

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.ToolStrip>
- [<span data-ttu-id="04819-138">BindingNavigator, kontrolka</span><span class="sxs-lookup"><span data-stu-id="04819-138">BindingNavigator Control</span></span>](bindingnavigator-control-windows-forms.md)
- [<span data-ttu-id="04819-139">BindingSource, składnik — omówienie</span><span class="sxs-lookup"><span data-stu-id="04819-139">BindingSource Component Overview</span></span>](bindingsource-component-overview.md)
