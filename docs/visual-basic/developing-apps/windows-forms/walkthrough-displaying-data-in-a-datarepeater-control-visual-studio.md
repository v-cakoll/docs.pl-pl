---
title: 'Wskazówki: wyświetlanie danych w formancie DataRepeater (Visual Studio)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, walkthrough
ms.assetid: 65dcdb95-6c3e-47cc-987d-190000f71653
ms.openlocfilehash: 8e64a819e9670a29e97140a32c81f5ff9006f83e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43388555"
---
# <a name="walkthrough-displaying-data-in-a-datarepeater-control-visual-studio"></a><span data-ttu-id="8ceb1-102">Wskazówki: wyświetlanie danych w formancie DataRepeater (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="8ceb1-102">Walkthrough: Displaying Data in a DataRepeater Control (Visual Studio)</span></span>
<span data-ttu-id="8ceb1-103">Ten przewodnik zawiera podstawowy scenariusz rozpoczęcia do zakończenia do wyświetlania powiązanych danych w <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-103">This walkthrough provides a basic start-to-finish scenario for displaying bound data in a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
## <a name="prerequisite"></a><span data-ttu-id="8ceb1-104">Wymaganie wstępne</span><span class="sxs-lookup"><span data-stu-id="8ceb1-104">Prerequisite</span></span>  
 <span data-ttu-id="8ceb1-105">Ten poradnik wymaga przykładowej bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-105">This walkthrough requires the Northwind sample database.</span></span>  
  
 <span data-ttu-id="8ceb1-106">Jeśli nie masz tej bazy danych na komputerze deweloperskim, możesz ją pobrać z Microsoft Download Center.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-106">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="8ceb1-107">Aby uzyskać instrukcje, zobacz [Downloading Sample Databases](../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="8ceb1-107">For instructions, see [Downloading Sample Databases](../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="8ceb1-108">Omówienie</span><span class="sxs-lookup"><span data-stu-id="8ceb1-108">Overview</span></span>  
 <span data-ttu-id="8ceb1-109">Pierwsza część w tym przewodniku składa się z czterech głównych zadań:</span><span class="sxs-lookup"><span data-stu-id="8ceb1-109">The first part of this walkthrough consists of four main tasks:</span></span>  
  
-   <span data-ttu-id="8ceb1-110">Tworzenie rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-110">Creating a solution.</span></span>  
  
-   <span data-ttu-id="8ceb1-111">Dodawanie <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-111">Adding a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
-   <span data-ttu-id="8ceb1-112">Dodawanie źródła danych.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-112">Adding a data source.</span></span>  
  
-   <span data-ttu-id="8ceb1-113">Dodawanie formantów powiązanych z danymi.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-113">Adding data-bound controls.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-a-datarepeater-solution"></a><span data-ttu-id="8ceb1-114">Tworzenie rozwiązania DataRepeater</span><span class="sxs-lookup"><span data-stu-id="8ceb1-114">Creating a DataRepeater Solution</span></span>  
 <span data-ttu-id="8ceb1-115">W pierwszym kroku utworzysz projekt i rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-115">In the first step, you create a project and solution.</span></span>  
  
#### <a name="to-create-a-datarepeater-solution"></a><span data-ttu-id="8ceb1-116">Aby utworzyć rozwiązanie DataRepeater</span><span class="sxs-lookup"><span data-stu-id="8ceb1-116">To create a DataRepeater solution</span></span>  
  
1.  <span data-ttu-id="8ceb1-117">W programie Visual Studio **pliku** menu, kliknij przycisk **nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-117">On the Visual Studio **File** menu, click **New Project**.</span></span>  
  
2.  <span data-ttu-id="8ceb1-118">W **typów projektów** okienka **nowy projekt** okna dialogowego rozwiń **języka Visual Basic**, a następnie kliknij przycisk **Windows**.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-118">In the **Project types** pane in the **New Project** dialog box, expand **Visual Basic**, and then click **Windows**.</span></span>  
  
3.  <span data-ttu-id="8ceb1-119">W **szablony** okienku kliknij **aplikacja interfejsu Windows Forms**.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-119">In the **Templates** pane, click **Windows Forms Application**.</span></span>  
  
4.  <span data-ttu-id="8ceb1-120">W **nazwa** wpisz `DataRepeaterApp`.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-120">In the **Name** box, type `DataRepeaterApp`.</span></span>  
  
5.  <span data-ttu-id="8ceb1-121">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-121">Click **OK**.</span></span>  
  
     <span data-ttu-id="8ceb1-122">Zostanie otwarty projektant formularzy Windows.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-122">The Windows Forms Designer opens.</span></span>  
  
6.  <span data-ttu-id="8ceb1-123">Wybierz formularz w programie Windows Forms Designer.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-123">Select the form in the Windows Forms Designer.</span></span> <span data-ttu-id="8ceb1-124">W **właściwości** oknie **rozmiar** właściwość `800, 700`.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-124">In the **Properties** window, set the **Size** property to `800, 700`.</span></span>  
  
## <a name="adding-a-datarepeater-control"></a><span data-ttu-id="8ceb1-125">Dodawanie kontrolki DataRepeater</span><span class="sxs-lookup"><span data-stu-id="8ceb1-125">Adding a DataRepeater Control</span></span>  
 <span data-ttu-id="8ceb1-126">W tym kroku dodasz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu do formularza.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-126">In this step, you add a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control to the form.</span></span>  
  
#### <a name="to-add-a-datarepeater-control"></a><span data-ttu-id="8ceb1-127">Aby dodać kontrolki DataRepeater</span><span class="sxs-lookup"><span data-stu-id="8ceb1-127">To add a DataRepeater control</span></span>  
  
1.  <span data-ttu-id="8ceb1-128">Na **widoku** menu, kliknij przycisk **przybornika**.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-128">On the **View** menu, click **Toolbox**.</span></span>  
  
     <span data-ttu-id="8ceb1-129">**Przybornika** zostanie otwarty.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-129">The **Toolbox** opens.</span></span>  
  
2.  <span data-ttu-id="8ceb1-130">Wybierz **Visual Basic PowerPacks** kartę.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-130">Select the **Visual Basic PowerPacks** tab.</span></span>  
  
3.  <span data-ttu-id="8ceb1-131">Przeciągnij <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontrolować na **Form1**.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-131">Drag a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control onto **Form1**.</span></span>  
  
4.  <span data-ttu-id="8ceb1-132">W oknie właściwości ustaw **lokalizacji** właściwość `0, 25`.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-132">In the Properties window, set the **Location** property to `0, 25`.</span></span>  
  
5.  <span data-ttu-id="8ceb1-133">Ustaw **rozmiar** właściwość `460, 600`.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-133">Set the **Size** property to `460, 600`.</span></span>  
  
## <a name="adding-a-data-source"></a><span data-ttu-id="8ceb1-134">Dodawanie źródła danych</span><span class="sxs-lookup"><span data-stu-id="8ceb1-134">Adding a Data Source</span></span>  
 <span data-ttu-id="8ceb1-135">W tym kroku należy dodać źródła danych dla <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-135">In this step, you add a data source for the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
#### <a name="to-add-a-data-source"></a><span data-ttu-id="8ceb1-136">Aby dodać źródło danych</span><span class="sxs-lookup"><span data-stu-id="8ceb1-136">To add a data source</span></span>  
  
1.  <span data-ttu-id="8ceb1-137">Na **danych** menu, kliknij przycisk **Pokaż źródła danych**.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-137">On the **Data** menu, click **Show Data Sources**.</span></span>  
  
2.  <span data-ttu-id="8ceb1-138">W **źródeł danych** okna, kliknij przycisk **Dodaj nowe źródło danych**.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-138">In the **Data Sources** window, click **Add New Data Source**.</span></span>  
  
3.  <span data-ttu-id="8ceb1-139">Wybierz **bazy danych** na **wybierz typ źródła danych** strony, a następnie kliknij przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-139">Select **Database** on the **Choose a Data Source Type** page, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="8ceb1-140">Na **wybierz połączenie danych** strony, wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="8ceb1-140">On the **Choose Your Data Connection** page, perform one of the following steps:</span></span>  
  
    -   <span data-ttu-id="8ceb1-141">Jeśli połączenie danych z przykładowej bazy danych Northwind jest dostępne na liście rozwijanej, kliknij go.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-141">If a data connection to the Northwind sample database is available in the drop-down list, click it.</span></span>  
  
         <span data-ttu-id="8ceb1-142">—lub—</span><span class="sxs-lookup"><span data-stu-id="8ceb1-142">-or-</span></span>  
  
    -   <span data-ttu-id="8ceb1-143">Kliknij przycisk **nowe połączenie** Aby skonfigurować nowe połączenie danych.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-143">Click **New Connection** to configure a new data connection.</span></span> <span data-ttu-id="8ceb1-144">Aby uzyskać więcej informacji, zobacz [dodać nowe połączenia](/visualstudio/data-tools/add-new-connections).</span><span class="sxs-lookup"><span data-stu-id="8ceb1-144">For more information, see [Add new connections](/visualstudio/data-tools/add-new-connections).</span></span>  
  
5.  <span data-ttu-id="8ceb1-145">Jeśli baza danych wymaga hasła, wybierz opcję dołączenia danych poufnych, a następnie kliknij przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-145">If the database requires a password, select the option to include sensitive data, and then click **Next**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8ceb1-146">Jeśli pojawi się okno dialogowe, kliknij przycisk **tak** można zapisać pliku do projektu.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-146">If a dialog box appears, click **Yes** to save the file to your project.</span></span>  
  
6.  <span data-ttu-id="8ceb1-147">Kliknij przycisk **dalej** na **Zapisz parametry połączenia do pliku konfiguracyjnego aplikacji** strony.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-147">Click **Next** on the **Save Connection String to the Application Configuration file** page.</span></span>  
  
7.  <span data-ttu-id="8ceb1-148">Rozwiń **tabel** węzeł **wybierz obiekty bazy danych** strony.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-148">Expand the **Tables** node on the **Choose Your Database Objects** page.</span></span>  
  
8.  <span data-ttu-id="8ceb1-149">Zaznacz pole wyboru obok pozycji **klientów** i **zamówienia** tabel, a następnie kliknij **Zakończ**.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-149">Select the check boxes next to the **Customers** and **Orders** tables, and then click **Finish**.</span></span>  
  
     <span data-ttu-id="8ceb1-150">**NorthwindDataSet** zostanie dodany do projektu i **klientów** i **zamówienia** tabele są wyświetlane w **źródeł danych** okna.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-150">**NorthwindDataSet** is added to your project and the **Customers** and **Orders** tables appear in the **Data Sources** window.</span></span>  
  
## <a name="adding-data-bound-controls"></a><span data-ttu-id="8ceb1-151">Dodawanie formantów powiązanych z danymi</span><span class="sxs-lookup"><span data-stu-id="8ceb1-151">Adding Data-Bound Controls</span></span>  
 <span data-ttu-id="8ceb1-152">W tym kroku dodaj formanty powiązane z danymi do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-152">In this step, you add data-bound controls to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.</span></span>  
  
#### <a name="to-add-data-bound-controls"></a><span data-ttu-id="8ceb1-153">Aby dodać formanty powiązane z danymi</span><span class="sxs-lookup"><span data-stu-id="8ceb1-153">To add data-bound controls</span></span>  
  
1.  <span data-ttu-id="8ceb1-154">W **źródeł danych** okna, wybierz węzeł najwyższego poziomu dla **klientów** tabeli.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-154">In the **Data Sources** window, select the top-level node for the **Customers** table.</span></span>  
  
2.  <span data-ttu-id="8ceb1-155">Zmień upuszczany typ tabeli, aby **szczegóły** , klikając **szczegóły** w węźle tabeli na liście rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-155">Change the drop type of the table to **Details** by clicking **Details** in the drop-down list on the table node.</span></span>  
  
3.  <span data-ttu-id="8ceb1-156">Wybierz **klientów** tabeli węzła i przeciągnij element szablonu region (górnego regionu) <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-156">Select the **Customers** table node and drag it onto the item template region (the upper region) of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
     <span data-ttu-id="8ceb1-157">A <xref:System.Windows.Forms.BindingNavigator> formant jest dodawany do formularza i **NorthwindDataSet**, **CustomersBindingSource**, **CustomersTableAdapter**,  **TableAdapterManager**, i **CustomersBindingNavigator** składniki są dodawane do zasobnika składnika.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-157">A <xref:System.Windows.Forms.BindingNavigator> control is added to the form, and the **NorthwindDataSet**, **CustomersBindingSource**, **CustomersTableAdapter**, **TableAdapterManager**, and **CustomersBindingNavigator** components are added to the Component Tray.</span></span>  
  
4.  <span data-ttu-id="8ceb1-158">Zaznacz wszystkie pola i ich etykiet skojarzonych i umieść je w pobliżu lewej krawędzi region szablonu elementu.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-158">Select all of the fields and their associated labels and position them near the left edge of the item template region.</span></span>  
  
5.  <span data-ttu-id="8ceb1-159">Wybierz pola pięć ostatnich (**Region**, **kod pocztowy**, **kraju**, **Phone**, i **faks**) i ich etykiet skojarzonych i przenieść je w górę i w prawo pierwszych sześciu pól.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-159">Select the last five fields (**Region**, **Postal Code**, **Country**, **Phone**, and **Fax**) and their associated labels and move them up and to the right of the first six fields.</span></span>  
  
6.  <span data-ttu-id="8ceb1-160">Wybierz szablon elementu (górnej kontrolki).</span><span class="sxs-lookup"><span data-stu-id="8ceb1-160">Select the item template (the upper region of the control).</span></span>  
  
7.  <span data-ttu-id="8ceb1-161">W oknie właściwości ustaw **rozmiar** właściwość `427, 170`.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-161">In the Properties window, set the **Size** property to `427, 170`.</span></span>  
  
 <span data-ttu-id="8ceb1-162">W tym momencie masz działającą aplikację, która będzie wyświetlana lista powtarzające się klientów.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-162">At this point, you have a working application that will display a repeating list of customers.</span></span> <span data-ttu-id="8ceb1-163">Można nacisnąć klawisz F5, aby uruchomić aplikację, zmieniać dane i dodawanie lub usuwanie rekordów klientów.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-163">You can press F5 to run the application, change the data, and add or delete customer records.</span></span>  
  
 <span data-ttu-id="8ceb1-164">W następnych kroków opcjonalnych, będzie dowiesz się, jak dostosować <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-164">In the next optional steps, you will learn how to customize the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
## <a name="next-steps-optional"></a><span data-ttu-id="8ceb1-165">Następne kroki (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="8ceb1-165">Next Steps (Optional)</span></span>  
 <span data-ttu-id="8ceb1-166">Ta część przewodnika obejmuje cztery opcjonalnych zadań:</span><span class="sxs-lookup"><span data-stu-id="8ceb1-166">This part of the walkthrough consists of four optional tasks:</span></span>  
  
-   <span data-ttu-id="8ceb1-167">Zmiana wyglądu <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-167">Changing the appearance of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
-   <span data-ttu-id="8ceb1-168">Uniemożliwia użytkownikom dodawanie i usuwanie rekordów.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-168">Preventing users from adding or deleting records.</span></span>  
  
-   <span data-ttu-id="8ceb1-169">Dodawanie możliwości wyszukiwania do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-169">Adding search capability to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
-   <span data-ttu-id="8ceb1-170">Dodawanie tabeli do wzorca i szczegółów <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-170">Adding a master and detail table to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
## <a name="changing-the-appearance-of-the-datarepeater-control"></a><span data-ttu-id="8ceb1-171">Zmienianie wyglądu formantu DataRepeater</span><span class="sxs-lookup"><span data-stu-id="8ceb1-171">Changing the Appearance of the DataRepeater Control</span></span>  
 <span data-ttu-id="8ceb1-172">W tym kroku Opcjonalnie możesz zmienić `BackColor` z <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-172">In this optional step, you change the `BackColor` of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control at design time.</span></span> <span data-ttu-id="8ceb1-173">Możesz również dodać kod, aby wyświetlać tylko wiersze w naprzemiennych kolorów i aby zmienić etykietę `ForeColor` warunkowo.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-173">You also add code to display rows in alternating colors and to change a label's `ForeColor` conditionally.</span></span>  
  
#### <a name="to-change-the-appearance-of-the-control"></a><span data-ttu-id="8ceb1-174">Aby zmienić wygląd formantu</span><span class="sxs-lookup"><span data-stu-id="8ceb1-174">To change the appearance of the control</span></span>  
  
1.  <span data-ttu-id="8ceb1-175">W programie Windows Forms Designer wybierz główny region (niższe) <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-175">In the Windows Forms Designer, select the main (lower) region of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
2.  <span data-ttu-id="8ceb1-176">W oknie właściwości ustaw `BackColor` właściwości na biały.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-176">In the Properties window, set the `BackColor` property to white.</span></span>  
  
3.  <span data-ttu-id="8ceb1-177">Kliknij dwukrotnie <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> można otworzyć edytora kodu.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-177">Double-click the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> to open the Code Editor.</span></span>  
  
4.  <span data-ttu-id="8ceb1-178">W edytorze kodu, w przypadku menu rozwijanego, kliknij przycisk **drawitem —**.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-178">In the Code Editor, in the Event drop-down list, click **DrawItem**.</span></span>  
  
5.  <span data-ttu-id="8ceb1-179">W <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> procedura obsługi zdarzeń, Dodaj następujący kod do alternatywnego `BackColor`:</span><span class="sxs-lookup"><span data-stu-id="8ceb1-179">In the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> event handler, add the following code to alternate the `BackColor`:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_1.vb)]  
  
6.  <span data-ttu-id="8ceb1-180">W <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> procedura obsługi zdarzeń, Dodaj następujący kod, aby zmienić `ForeColor` etykiety w zależności od warunku:</span><span class="sxs-lookup"><span data-stu-id="8ceb1-180">In the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> event handler, add the following code to change the `ForeColor` of a label depending on a condition:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_2.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_2.vb)]  
  
7.  <span data-ttu-id="8ceb1-181">Naciśnij klawisz F5, aby uruchomić aplikację i wyświetlić dostosowań.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-181">Press F5 to run the application and see the customizations.</span></span>  
  
## <a name="preventing-users-from-adding-or-deleting-records"></a><span data-ttu-id="8ceb1-182">Uniemożliwia użytkownikom dodawanie i usuwanie rekordów</span><span class="sxs-lookup"><span data-stu-id="8ceb1-182">Preventing Users from Adding or Deleting Records</span></span>  
 <span data-ttu-id="8ceb1-183">W tym kroku opcjonalnie Dodaj kod, który uniemożliwia użytkownikom dodawanie i usuwanie rekordów w <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-183">In this optional step, you add code that prevents users from adding or deleting records in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
#### <a name="to-prevent-users-from-adding-and-deleting-records"></a><span data-ttu-id="8ceb1-184">Aby uniemożliwić użytkownikom dodawanie i usuwanie rekordów</span><span class="sxs-lookup"><span data-stu-id="8ceb1-184">To prevent users from adding and deleting records</span></span>  
  
1.  <span data-ttu-id="8ceb1-185">W Windows Forms Designer kliknij dwukrotnie formularza, aby otworzyć Edytor kodu.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-185">In the Windows Forms Designer, double-click the form to open the Code Editor.</span></span>  
  
2.  <span data-ttu-id="8ceb1-186">Dodaj następujący kod do `Form_Load` zdarzeń:</span><span class="sxs-lookup"><span data-stu-id="8ceb1-186">Add the following code to the `Form_Load` event:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_3.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_3.vb)]  
  
3.  <span data-ttu-id="8ceb1-187">Na liście rozwijanej nazwy klasy kliknij **BindingNavigatorDeleteItem**.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-187">In the Class Name drop-down list, click **BindingNavigatorDeleteItem**.</span></span> <span data-ttu-id="8ceb1-188">Na liście rozwijanej nazwy metody kliknij **EnabledChanged**.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-188">In the Method Name drop-down list, click **EnabledChanged**.</span></span>  
  
4.  <span data-ttu-id="8ceb1-189">Dodaj następujący kod do `BindingNavigatorDeleteItem_EnabledChanged` program obsługi zdarzeń:</span><span class="sxs-lookup"><span data-stu-id="8ceb1-189">Add the following code to the `BindingNavigatorDeleteItem_EnabledChanged` event handler:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_4.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_4.vb)]  
  
    > [!NOTE]
    >  <span data-ttu-id="8ceb1-190">Ten krok jest niezbędny, ponieważ <xref:System.Windows.Forms.BindingSource> umożliwi **DeleteItem** przycisk ilekroć dany zmiany bieżącego rekordu.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-190">This step is necessary because the <xref:System.Windows.Forms.BindingSource> will enable the **DeleteItem** button every time that the current record changes.</span></span>  
  
5.  <span data-ttu-id="8ceb1-191">Naciśnij klawisz F5, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-191">Press F5 to run the application.</span></span> <span data-ttu-id="8ceb1-192">Należy zauważyć, że **DeleteItem** przycisk jest wyłączony i że nie można usunąć elementów, naciskając klawisz DELETE.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-192">Notice that the **DeleteItem** button is disabled and that you cannot delete items by pressing the DELETE key.</span></span>  
  
## <a name="adding-search-capability-to-the-datarepeater-control"></a><span data-ttu-id="8ceb1-193">Dodawanie możliwości wyszukiwania do formantu DataRepeater</span><span class="sxs-lookup"><span data-stu-id="8ceb1-193">Adding Search Capability to the DataRepeater Control</span></span>  
 <span data-ttu-id="8ceb1-194">W tym kroku opcjonalnie zaimplementować możliwość wyszukiwania wartości w <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-194">In this optional step, you implement the capability to search for a value in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="8ceb1-195">Jeśli zostanie znaleziony ciąg wyszukiwania, formant wybiera element, który zawiera wartość się i przewija elementu w widoku.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-195">If the search string is found, the control selects the item that contains the value and scrolls the item into view.</span></span>  
  
#### <a name="to-add-search-capability"></a><span data-ttu-id="8ceb1-196">Aby dodać możliwości wyszukiwania</span><span class="sxs-lookup"><span data-stu-id="8ceb1-196">To add search capability</span></span>  
  
1.  <span data-ttu-id="8ceb1-197">Przeciągnij <xref:System.Windows.Forms.TextBox> z kontrolować **przybornika** na formularz, który zawiera <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-197">Drag a <xref:System.Windows.Forms.TextBox> control from the **Toolbox** onto the form that contains the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
     <span data-ttu-id="8ceb1-198">Umieść ją w obszarze <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-198">Position it under the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
2.  <span data-ttu-id="8ceb1-199">W oknie Właściwości zmień **nazwa** właściwości **SearchTextBox**.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-199">In the Properties window, change the **Name** property to **SearchTextBox**.</span></span>  
  
3.  <span data-ttu-id="8ceb1-200">Przeciągnij <xref:System.Windows.Forms.Button> z kontrolować **przybornika** na formularz, który zawiera <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-200">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto the form that contains the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="8ceb1-201">Umieść ją w obszarze <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-201">Position it under the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
4.  <span data-ttu-id="8ceb1-202">W oknie Właściwości zmień **nazwa** właściwości **SearchButton**.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-202">In the Properties window, change the **Name** property to **SearchButton**.</span></span> <span data-ttu-id="8ceb1-203">Zmiana **tekstu** właściwości **wyszukiwania**.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-203">Change the **Text** property to **Search**.</span></span>  
  
5.  <span data-ttu-id="8ceb1-204">Kliknij dwukrotnie <xref:System.Windows.Forms.Button> sterowania, aby otworzyć Edytor kodu i Dodaj następujący kod do `SearchButton_Click` programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-204">Double-click the <xref:System.Windows.Forms.Button> control to open the Code Editor, and add the following code to the `SearchButton_Click` event handler.</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_5.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_5.vb)]  
  
6.  <span data-ttu-id="8ceb1-205">Naciśnij klawisz F5, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-205">Press F5 to run the application.</span></span> <span data-ttu-id="8ceb1-206">Wpisz identyfikator klienta w **SearchTextBox** i kliknij przycisk **wyszukiwania** przycisku.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-206">Type a customer ID in **SearchTextBox** and click the **Search** button.</span></span>  
  
## <a name="adding-a-master-and-detail-table-to-the-datarepeater"></a><span data-ttu-id="8ceb1-207">Dodawanie głównego i tabelę szczegółów do DataRepeater</span><span class="sxs-lookup"><span data-stu-id="8ceb1-207">Adding a Master and Detail Table to the DataRepeater</span></span>  
 <span data-ttu-id="8ceb1-208">W tym kroku opcjonalnie Dodaj sekundy <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu, aby wyświetlić powiązane zamówienia dla każdego klienta.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-208">In this optional step, you add a second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control to display related orders for each customer.</span></span>  
  
#### <a name="to-add-a-master-and-detail-table"></a><span data-ttu-id="8ceb1-209">Aby dodać tabelę głównego i szczegółów</span><span class="sxs-lookup"><span data-stu-id="8ceb1-209">To add a master and detail table</span></span>  
  
1.  <span data-ttu-id="8ceb1-210">Przeciągnij sekundy <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> z kontrolować **Visual Basic PowerPacks** karcie **przybornika** na formularz.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-210">Drag a second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control from the **Visual Basic PowerPacks** tab in the **Toolbox** onto the form.</span></span>  
  
2.  <span data-ttu-id="8ceb1-211">W oknie właściwości ustaw **lokalizacji** właściwość `465, 25`.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-211">In the Properties window, set the **Location** property to `465, 25`.</span></span>  
  
3.  <span data-ttu-id="8ceb1-212">Ustaw **rozmiar** właściwość `315, 600`.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-212">Set the **Size** property to `315, 600`.</span></span>  
  
4.  <span data-ttu-id="8ceb1-213">W **źródeł danych** okna, rozwiń węzeł **klientów** tabeli węzła, a następnie wybierz węzeł szczegółów **zamówienia** tabeli.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-213">In the **Data Sources** window, expand the **Customers** table node and select the detail node for the **Orders** table.</span></span>  
  
5.  <span data-ttu-id="8ceb1-214">Zmień upuszczany typ to **zamówienia** tabeli, aby uzyskać szczegółowe informacje, klikając **szczegóły** w węźle tabeli na liście rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-214">Change the drop type of this **Orders** table to Details by clicking **Details** in the drop-down list on the table node.</span></span>  
  
6.  <span data-ttu-id="8ceb1-215">Przeciągnij to **zamówienia** węzeł tabeli na region szablonu elementu (górnego regionu) drugiego <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-215">Drag this **Orders** table node onto the item template region (the upper region) of the second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
     <span data-ttu-id="8ceb1-216">**OrdersBindingSource** składnika i **OrdersTableAdapter** składników są dodawane do zasobnika składnika.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-216">An **OrdersBindingSource** component and an **OrdersTableAdapter** component are added to the Component Tray.</span></span>  
  
7.  <span data-ttu-id="8ceb1-217">Naciśnij klawisz F5, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-217">Press F5 to run the application.</span></span> <span data-ttu-id="8ceb1-218">Po wybraniu każdego klienta w pierwszym <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontrolować zamówień dla tego klienta są wyświetlane w ciągu sekundy <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli.</span><span class="sxs-lookup"><span data-stu-id="8ceb1-218">When you select each customer in the first <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control, the orders for that customer are displayed in the second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ceb1-219">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8ceb1-219">See Also</span></span>  
 [<span data-ttu-id="8ceb1-220">Wprowadzenie do kontrolki DataRepeater</span><span class="sxs-lookup"><span data-stu-id="8ceb1-220">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="8ceb1-221">Instrukcje: wyświetlanie powiązanych danych w kontrolce DataRepeater</span><span class="sxs-lookup"><span data-stu-id="8ceb1-221">How to: Display Bound Data in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="8ceb1-222">Instrukcje: wyświetlanie niepowiązanych kontrolek w kontrolce DataRepeater</span><span class="sxs-lookup"><span data-stu-id="8ceb1-222">How to: Display Unbound Controls in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="8ceb1-223">Instrukcje: zmienianie układu kontrolki DataRepeater</span><span class="sxs-lookup"><span data-stu-id="8ceb1-223">How to: Change the Layout of a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="8ceb1-224">Instrukcje: wyświetlanie nagłówków elementów w kontrolce DataRepeater</span><span class="sxs-lookup"><span data-stu-id="8ceb1-224">How to: Display Item Headers in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="8ceb1-225">Instrukcje: wyszukiwanie danych w kontrolce DataRepeater</span><span class="sxs-lookup"><span data-stu-id="8ceb1-225">How to: Search Data in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-search-data-in-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="8ceb1-226">Porady: Tworzenie formularza wzorzec/szczegół za pomocą dwóch formantów DataRepeater (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="8ceb1-226">How to: Create a Master/Detail Form by Using Two DataRepeater Controls (Visual Studio)</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)  
 [<span data-ttu-id="8ceb1-227">Instrukcje: zmienianie wyglądu kontrolki DataRepeater</span><span class="sxs-lookup"><span data-stu-id="8ceb1-227">How to: Change the Appearance of a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="8ceb1-228">Instrukcje: wyłączanie dodawania i usuwania elementów DataRepeater</span><span class="sxs-lookup"><span data-stu-id="8ceb1-228">How to: Disable Adding and Deleting DataRepeater Items</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio.md)  
 [<span data-ttu-id="8ceb1-229">Rozwiązywanie problemów z kontrolką DataRepeater</span><span class="sxs-lookup"><span data-stu-id="8ceb1-229">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
