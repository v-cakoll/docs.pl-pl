---
title: "Wskazówki: wyświetlanie danych w formancie DataRepeater (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: DataRepeater, walkthrough
ms.assetid: 65dcdb95-6c3e-47cc-987d-190000f71653
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 93072bf30c8ee2a4a44c4862de0882072c298f8b
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="walkthrough-displaying-data-in-a-datarepeater-control-visual-studio"></a><span data-ttu-id="c595d-102">Wskazówki: wyświetlanie danych w formancie DataRepeater (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="c595d-102">Walkthrough: Displaying Data in a DataRepeater Control (Visual Studio)</span></span>
<span data-ttu-id="c595d-103">Ten przewodnik zawiera podstawowe scenariusz start zakończenie wyświetlanie powiązanych danych w <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu.</span><span class="sxs-lookup"><span data-stu-id="c595d-103">This walkthrough provides a basic start-to-finish scenario for displaying bound data in a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
## <a name="prerequisite"></a><span data-ttu-id="c595d-104">Wymaganie wstępne</span><span class="sxs-lookup"><span data-stu-id="c595d-104">Prerequisite</span></span>  
 <span data-ttu-id="c595d-105">W tym przewodniku wymaga przykładowej bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="c595d-105">This walkthrough requires the Northwind sample database.</span></span>  
  
 <span data-ttu-id="c595d-106">Jeśli nie ma tej bazy danych na komputerze deweloperskim, możesz pobrać go z [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088).</span><span class="sxs-lookup"><span data-stu-id="c595d-106">If you do not have this database on your development computer, you can download it from the [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088).</span></span> <span data-ttu-id="c595d-107">Aby uzyskać instrukcje, zobacz [pobieranie przykładowe bazy danych](../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="c595d-107">For instructions, see [Downloading Sample Databases](../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="c595d-108">Omówienie</span><span class="sxs-lookup"><span data-stu-id="c595d-108">Overview</span></span>  
 <span data-ttu-id="c595d-109">Pierwsza część tego przewodnika składa się z czterech głównych zadań:</span><span class="sxs-lookup"><span data-stu-id="c595d-109">The first part of this walkthrough consists of four main tasks:</span></span>  
  
-   <span data-ttu-id="c595d-110">Tworzenie rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="c595d-110">Creating a solution.</span></span>  
  
-   <span data-ttu-id="c595d-111">Dodawanie <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu.</span><span class="sxs-lookup"><span data-stu-id="c595d-111">Adding a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
-   <span data-ttu-id="c595d-112">Dodawanie źródła danych.</span><span class="sxs-lookup"><span data-stu-id="c595d-112">Adding a data source.</span></span>  
  
-   <span data-ttu-id="c595d-113">Dodawanie formantów powiązanych z danymi.</span><span class="sxs-lookup"><span data-stu-id="c595d-113">Adding data-bound controls.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-a-datarepeater-solution"></a><span data-ttu-id="c595d-114">Tworzenie rozwiązania DataRepeater</span><span class="sxs-lookup"><span data-stu-id="c595d-114">Creating a DataRepeater Solution</span></span>  
 <span data-ttu-id="c595d-115">W pierwszym kroku możesz utworzyć projektu i rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="c595d-115">In the first step, you create a project and solution.</span></span>  
  
#### <a name="to-create-a-datarepeater-solution"></a><span data-ttu-id="c595d-116">Tworzenie rozwiązań DataRepeater</span><span class="sxs-lookup"><span data-stu-id="c595d-116">To create a DataRepeater solution</span></span>  
  
1.  <span data-ttu-id="c595d-117">W programie Visual Studio **pliku** menu, kliknij przycisk **nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="c595d-117">On the Visual Studio **File** menu, click **New Project**.</span></span>  
  
2.  <span data-ttu-id="c595d-118">W **typy projektów** okienka w **nowy projekt** okna dialogowego rozwiń **Visual Basic**, a następnie kliknij przycisk **Windows**.</span><span class="sxs-lookup"><span data-stu-id="c595d-118">In the **Project types** pane in the **New Project** dialog box, expand **Visual Basic**, and then click **Windows**.</span></span>  
  
3.  <span data-ttu-id="c595d-119">W **szablony** okienku, kliknij przycisk **aplikacji Windows Forms**.</span><span class="sxs-lookup"><span data-stu-id="c595d-119">In the **Templates** pane, click **Windows Forms Application**.</span></span>  
  
4.  <span data-ttu-id="c595d-120">W **nazwa** wpisz `DataRepeaterApp`.</span><span class="sxs-lookup"><span data-stu-id="c595d-120">In the **Name** box, type `DataRepeaterApp`.</span></span>  
  
5.  <span data-ttu-id="c595d-121">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="c595d-121">Click **OK**.</span></span>  
  
     <span data-ttu-id="c595d-122">Zostanie otwarty projektant formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="c595d-122">The Windows Forms Designer opens.</span></span>  
  
6.  <span data-ttu-id="c595d-123">Wybierz formularza w narzędziu Projektant dla formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="c595d-123">Select the form in the Windows Forms Designer.</span></span> <span data-ttu-id="c595d-124">W **właściwości** ustaw **rozmiar** właściwości `800, 700`.</span><span class="sxs-lookup"><span data-stu-id="c595d-124">In the **Properties** window, set the **Size** property to `800, 700`.</span></span>  
  
## <a name="adding-a-datarepeater-control"></a><span data-ttu-id="c595d-125">Dodawanie formantu DataRepeater</span><span class="sxs-lookup"><span data-stu-id="c595d-125">Adding a DataRepeater Control</span></span>  
 <span data-ttu-id="c595d-126">W tym kroku, możesz dodać <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> sterowania do formularza.</span><span class="sxs-lookup"><span data-stu-id="c595d-126">In this step, you add a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control to the form.</span></span>  
  
#### <a name="to-add-a-datarepeater-control"></a><span data-ttu-id="c595d-127">Aby dodać formantu DataRepeater</span><span class="sxs-lookup"><span data-stu-id="c595d-127">To add a DataRepeater control</span></span>  
  
1.  <span data-ttu-id="c595d-128">Na **widoku** menu, kliknij przycisk **przybornika**.</span><span class="sxs-lookup"><span data-stu-id="c595d-128">On the **View** menu, click **Toolbox**.</span></span>  
  
     <span data-ttu-id="c595d-129">**Przybornika** otwiera.</span><span class="sxs-lookup"><span data-stu-id="c595d-129">The **Toolbox** opens.</span></span>  
  
2.  <span data-ttu-id="c595d-130">Wybierz **Visual Basic PowerPacks** kartę.</span><span class="sxs-lookup"><span data-stu-id="c595d-130">Select the **Visual Basic PowerPacks** tab.</span></span>  
  
3.  <span data-ttu-id="c595d-131">Przeciągnij <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontrolować na **Form1**.</span><span class="sxs-lookup"><span data-stu-id="c595d-131">Drag a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control onto **Form1**.</span></span>  
  
4.  <span data-ttu-id="c595d-132">W oknie właściwości ustaw **lokalizacji** właściwości `0, 25`.</span><span class="sxs-lookup"><span data-stu-id="c595d-132">In the Properties window, set the **Location** property to `0, 25`.</span></span>  
  
5.  <span data-ttu-id="c595d-133">Ustaw **rozmiar** właściwości `460, 600`.</span><span class="sxs-lookup"><span data-stu-id="c595d-133">Set the **Size** property to `460, 600`.</span></span>  
  
## <a name="adding-a-data-source"></a><span data-ttu-id="c595d-134">Dodawanie źródła danych</span><span class="sxs-lookup"><span data-stu-id="c595d-134">Adding a Data Source</span></span>  
 <span data-ttu-id="c595d-135">W tym kroku, Dodaj źródło danych dla <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu.</span><span class="sxs-lookup"><span data-stu-id="c595d-135">In this step, you add a data source for the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
#### <a name="to-add-a-data-source"></a><span data-ttu-id="c595d-136">Aby dodać źródła danych</span><span class="sxs-lookup"><span data-stu-id="c595d-136">To add a data source</span></span>  
  
1.  <span data-ttu-id="c595d-137">Na **danych** menu, kliknij przycisk **Pokaż źródeł danych**.</span><span class="sxs-lookup"><span data-stu-id="c595d-137">On the **Data** menu, click **Show Data Sources**.</span></span>  
  
2.  <span data-ttu-id="c595d-138">W **źródeł danych** okna, kliknij przycisk **Dodaj nowe źródło danych**.</span><span class="sxs-lookup"><span data-stu-id="c595d-138">In the **Data Sources** window, click **Add New Data Source**.</span></span>  
  
3.  <span data-ttu-id="c595d-139">Wybierz **bazy danych** na **wybierz typ źródła danych** , a następnie kliknij przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="c595d-139">Select **Database** on the **Choose a Data Source Type** page, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="c595d-140">Na **wybierz połączenie danych** wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="c595d-140">On the **Choose Your Data Connection** page, perform one of the following steps:</span></span>  
  
    -   <span data-ttu-id="c595d-141">Jeśli połączenie danych z przykładowej bazy danych Northwind jest dostępny na liście rozwijanej, kliknij go.</span><span class="sxs-lookup"><span data-stu-id="c595d-141">If a data connection to the Northwind sample database is available in the drop-down list, click it.</span></span>  
  
         <span data-ttu-id="c595d-142">—lub—</span><span class="sxs-lookup"><span data-stu-id="c595d-142">-or-</span></span>  
  
    -   <span data-ttu-id="c595d-143">Kliknij przycisk **nowe połączenie** można skonfigurować nowe połączenia danych.</span><span class="sxs-lookup"><span data-stu-id="c595d-143">Click **New Connection** to configure a new data connection.</span></span> <span data-ttu-id="c595d-144">Aby uzyskać więcej informacji, zobacz [dodać nowe połączenia](/visualstudio/data-tools/add-new-connections).</span><span class="sxs-lookup"><span data-stu-id="c595d-144">For more information, see [Add new connections](/visualstudio/data-tools/add-new-connections).</span></span>  
  
5.  <span data-ttu-id="c595d-145">Jeśli baza danych wymaga hasła, wybierz opcję, aby obejmować dane poufne, a następnie kliknij przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="c595d-145">If the database requires a password, select the option to include sensitive data, and then click **Next**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c595d-146">Jeśli zostanie wyświetlone okno dialogowe, kliknij przycisk **tak** można zapisać pliku do projektu.</span><span class="sxs-lookup"><span data-stu-id="c595d-146">If a dialog box appears, click **Yes** to save the file to your project.</span></span>  
  
6.  <span data-ttu-id="c595d-147">Kliknij przycisk **dalej** na **zapisać parametry połączenia do pliku konfiguracji aplikacji** strony.</span><span class="sxs-lookup"><span data-stu-id="c595d-147">Click **Next** on the **Save Connection String to the Application Configuration file** page.</span></span>  
  
7.  <span data-ttu-id="c595d-148">Rozwiń węzeł **tabel** węzła na **wybierz obiekty bazy danych użytkownika** strony.</span><span class="sxs-lookup"><span data-stu-id="c595d-148">Expand the **Tables** node on the **Choose Your Database Objects** page.</span></span>  
  
8.  <span data-ttu-id="c595d-149">Zaznacz pole wyboru obok pozycji **klientów** i **zamówień** tabel, a następnie kliknij przycisk **Zakończ**.</span><span class="sxs-lookup"><span data-stu-id="c595d-149">Select the check boxes next to the **Customers** and **Orders** tables, and then click **Finish**.</span></span>  
  
     <span data-ttu-id="c595d-150">**NorthwindDataSet** zostanie dodany do projektu i **klientów** i **zamówień** tabele są wyświetlane w **źródeł danych** okna.</span><span class="sxs-lookup"><span data-stu-id="c595d-150">**NorthwindDataSet** is added to your project and the **Customers** and **Orders** tables appear in the **Data Sources** window.</span></span>  
  
## <a name="adding-data-bound-controls"></a><span data-ttu-id="c595d-151">Dodawanie formantów powiązanych z danymi</span><span class="sxs-lookup"><span data-stu-id="c595d-151">Adding Data-Bound Controls</span></span>  
 <span data-ttu-id="c595d-152">W tym kroku, Dodaj formanty powiązane z danymi do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.</span><span class="sxs-lookup"><span data-stu-id="c595d-152">In this step, you add data-bound controls to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.</span></span>  
  
#### <a name="to-add-data-bound-controls"></a><span data-ttu-id="c595d-153">Aby dodać formanty powiązane z danymi</span><span class="sxs-lookup"><span data-stu-id="c595d-153">To add data-bound controls</span></span>  
  
1.  <span data-ttu-id="c595d-154">W **źródeł danych** okna, wybierz węzeł najwyższego poziomu **klientów** tabeli.</span><span class="sxs-lookup"><span data-stu-id="c595d-154">In the **Data Sources** window, select the top-level node for the **Customers** table.</span></span>  
  
2.  <span data-ttu-id="c595d-155">Zmień typ docelowej tabeli **szczegóły** klikając **szczegóły** na liście rozwijanej na węźle tabeli.</span><span class="sxs-lookup"><span data-stu-id="c595d-155">Change the drop type of the table to **Details** by clicking **Details** in the drop-down list on the table node.</span></span>  
  
3.  <span data-ttu-id="c595d-156">Wybierz **klientów** tabeli węzła i przeciągnij element szablonu regionie (górnej) <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu.</span><span class="sxs-lookup"><span data-stu-id="c595d-156">Select the **Customers** table node and drag it onto the item template region (the upper region) of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
     <span data-ttu-id="c595d-157">A <xref:System.Windows.Forms.BindingNavigator> formant został dodany do formularza i **NorthwindDataSet**, **CustomersBindingSource**, **CustomersTableAdapter**,  **TableAdapterManager**, i **CustomersBindingNavigator** składniki są dodawane do składnika na pasku zadań.</span><span class="sxs-lookup"><span data-stu-id="c595d-157">A <xref:System.Windows.Forms.BindingNavigator> control is added to the form, and the **NorthwindDataSet**, **CustomersBindingSource**, **CustomersTableAdapter**, **TableAdapterManager**, and **CustomersBindingNavigator** components are added to the Component Tray.</span></span>  
  
4.  <span data-ttu-id="c595d-158">Zaznacz wszystkie pola i ich etykiet skojarzonych i umieść je z lewą krawędzią obszaru szablonu elementu.</span><span class="sxs-lookup"><span data-stu-id="c595d-158">Select all of the fields and their associated labels and position them near the left edge of the item template region.</span></span>  
  
5.  <span data-ttu-id="c595d-159">Wybierz pola pięć ostatnich (**Region**, **kod pocztowy**, **kraju**, **Phone**, i **faksów**) i ich etykiet skojarzonych i przenieść je w górę i w prawo pierwszych sześciu pól.</span><span class="sxs-lookup"><span data-stu-id="c595d-159">Select the last five fields (**Region**, **Postal Code**, **Country**, **Phone**, and **Fax**) and their associated labels and move them up and to the right of the first six fields.</span></span>  
  
6.  <span data-ttu-id="c595d-160">Wybierz szablon elementu (górnej formantu).</span><span class="sxs-lookup"><span data-stu-id="c595d-160">Select the item template (the upper region of the control).</span></span>  
  
7.  <span data-ttu-id="c595d-161">W oknie właściwości ustaw **rozmiar** właściwości `427, 170`.</span><span class="sxs-lookup"><span data-stu-id="c595d-161">In the Properties window, set the **Size** property to `427, 170`.</span></span>  
  
 <span data-ttu-id="c595d-162">W tym momencie masz działającą aplikację, która będzie wyświetlana identycznych listę klientów.</span><span class="sxs-lookup"><span data-stu-id="c595d-162">At this point, you have a working application that will display a repeating list of customers.</span></span> <span data-ttu-id="c595d-163">Naciśnij klawisz F5, aby uruchomić aplikację, dane, zmiany i dodawania i usuwania rekordów klientów.</span><span class="sxs-lookup"><span data-stu-id="c595d-163">You can press F5 to run the application, change the data, and add or delete customer records.</span></span>  
  
 <span data-ttu-id="c595d-164">W następnych kroków opcjonalnych, przedstawiono sposób dostosowywania <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu.</span><span class="sxs-lookup"><span data-stu-id="c595d-164">In the next optional steps, you will learn how to customize the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
## <a name="next-steps-optional"></a><span data-ttu-id="c595d-165">Następne kroki (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="c595d-165">Next Steps (Optional)</span></span>  
 <span data-ttu-id="c595d-166">Ta część przewodnika obejmuje cztery opcjonalnych zadań:</span><span class="sxs-lookup"><span data-stu-id="c595d-166">This part of the walkthrough consists of four optional tasks:</span></span>  
  
-   <span data-ttu-id="c595d-167">Zmiana wyglądu <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu.</span><span class="sxs-lookup"><span data-stu-id="c595d-167">Changing the appearance of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
-   <span data-ttu-id="c595d-168">Uniemożliwia użytkownikom dodawanie i usuwanie rekordów.</span><span class="sxs-lookup"><span data-stu-id="c595d-168">Preventing users from adding or deleting records.</span></span>  
  
-   <span data-ttu-id="c595d-169">Dodawanie możliwości wyszukiwania do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu.</span><span class="sxs-lookup"><span data-stu-id="c595d-169">Adding search capability to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
-   <span data-ttu-id="c595d-170">Dodawanie głównego i szczegółów tabeli do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu.</span><span class="sxs-lookup"><span data-stu-id="c595d-170">Adding a master and detail table to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
## <a name="changing-the-appearance-of-the-datarepeater-control"></a><span data-ttu-id="c595d-171">Zmienianie wyglądu formantu DataRepeater</span><span class="sxs-lookup"><span data-stu-id="c595d-171">Changing the Appearance of the DataRepeater Control</span></span>  
 <span data-ttu-id="c595d-172">W tym kroku opcjonalne, zmień `BackColor` z <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="c595d-172">In this optional step, you change the `BackColor` of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control at design time.</span></span> <span data-ttu-id="c595d-173">Możesz również dodać kod, aby wyświetlić wiersze w naprzemiennych kolorów i aby zmienić etykietę `ForeColor` warunkowo.</span><span class="sxs-lookup"><span data-stu-id="c595d-173">You also add code to display rows in alternating colors and to change a label's `ForeColor` conditionally.</span></span>  
  
#### <a name="to-change-the-appearance-of-the-control"></a><span data-ttu-id="c595d-174">Aby zmienić wygląd formantu</span><span class="sxs-lookup"><span data-stu-id="c595d-174">To change the appearance of the control</span></span>  
  
1.  <span data-ttu-id="c595d-175">W narzędziu Projektant dla formularzy systemu Windows wybierz główny region (niższe) <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu.</span><span class="sxs-lookup"><span data-stu-id="c595d-175">In the Windows Forms Designer, select the main (lower) region of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
2.  <span data-ttu-id="c595d-176">W oknie właściwości ustaw `BackColor` właściwości na kolor biały.</span><span class="sxs-lookup"><span data-stu-id="c595d-176">In the Properties window, set the `BackColor` property to white.</span></span>  
  
3.  <span data-ttu-id="c595d-177">Kliknij dwukrotnie <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> można otworzyć edytora kodu.</span><span class="sxs-lookup"><span data-stu-id="c595d-177">Double-click the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> to open the Code Editor.</span></span>  
  
4.  <span data-ttu-id="c595d-178">W edytorze kodu, w przypadku menu rozwijanego, kliknij przycisk **DrawItem**.</span><span class="sxs-lookup"><span data-stu-id="c595d-178">In the Code Editor, in the Event drop-down list, click **DrawItem**.</span></span>  
  
5.  <span data-ttu-id="c595d-179">W <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> program obsługi zdarzeń, Dodaj następujący kod do alternatywnego `BackColor`:</span><span class="sxs-lookup"><span data-stu-id="c595d-179">In the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> event handler, add the following code to alternate the `BackColor`:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_1.vb)]  
  
6.  <span data-ttu-id="c595d-180">W <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> program obsługi zdarzeń, Dodaj następujący kod, aby zmienić `ForeColor` etykiety w zależności od warunek:</span><span class="sxs-lookup"><span data-stu-id="c595d-180">In the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> event handler, add the following code to change the `ForeColor` of a label depending on a condition:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_2.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_2.vb)]  
  
7.  <span data-ttu-id="c595d-181">Naciśnij klawisz F5, aby uruchomić aplikację i sprawdzić dostosowania.</span><span class="sxs-lookup"><span data-stu-id="c595d-181">Press F5 to run the application and see the customizations.</span></span>  
  
## <a name="preventing-users-from-adding-or-deleting-records"></a><span data-ttu-id="c595d-182">Uniemożliwia użytkownikom dodawanie i usuwanie rekordów</span><span class="sxs-lookup"><span data-stu-id="c595d-182">Preventing Users from Adding or Deleting Records</span></span>  
 <span data-ttu-id="c595d-183">W tym kroku opcjonalnie Dodaj kod, który uniemożliwia użytkownikom dodawanie i usuwanie rekordów w <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu.</span><span class="sxs-lookup"><span data-stu-id="c595d-183">In this optional step, you add code that prevents users from adding or deleting records in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
#### <a name="to-prevent-users-from-adding-and-deleting-records"></a><span data-ttu-id="c595d-184">Aby uniemożliwić użytkownikom dodawanie i usuwanie rekordów</span><span class="sxs-lookup"><span data-stu-id="c595d-184">To prevent users from adding and deleting records</span></span>  
  
1.  <span data-ttu-id="c595d-185">W narzędziu Projektant dla formularzy systemu Windows kliknij dwukrotnie formularza, aby otworzyć edytora kodu.</span><span class="sxs-lookup"><span data-stu-id="c595d-185">In the Windows Forms Designer, double-click the form to open the Code Editor.</span></span>  
  
2.  <span data-ttu-id="c595d-186">Dodaj następujący kod do `Form_Load` zdarzeń:</span><span class="sxs-lookup"><span data-stu-id="c595d-186">Add the following code to the `Form_Load` event:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_3.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_3.vb)]  
  
3.  <span data-ttu-id="c595d-187">Na liście rozwijanej nazwy klasy kliknij **BindingNavigatorDeleteItem**.</span><span class="sxs-lookup"><span data-stu-id="c595d-187">In the Class Name drop-down list, click **BindingNavigatorDeleteItem**.</span></span> <span data-ttu-id="c595d-188">Na liście rozwijanej nazwy metody kliknij **EnabledChanged**.</span><span class="sxs-lookup"><span data-stu-id="c595d-188">In the Method Name drop-down list, click **EnabledChanged**.</span></span>  
  
4.  <span data-ttu-id="c595d-189">Dodaj następujący kod do `BindingNavigatorDeleteItem_EnabledChanged` obsługi zdarzeń:</span><span class="sxs-lookup"><span data-stu-id="c595d-189">Add the following code to the `BindingNavigatorDeleteItem_EnabledChanged` event handler:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_4.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_4.vb)]  
  
    > [!NOTE]
    >  <span data-ttu-id="c595d-190">Ten krok jest niezbędny, ponieważ <xref:System.Windows.Forms.BindingSource> spowoduje włączenie **DeleteItem** przycisk zawsze zmiany bieżącego rekordu.</span><span class="sxs-lookup"><span data-stu-id="c595d-190">This step is necessary because the <xref:System.Windows.Forms.BindingSource> will enable the **DeleteItem** button every time that the current record changes.</span></span>  
  
5.  <span data-ttu-id="c595d-191">Naciśnij klawisz F5, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="c595d-191">Press F5 to run the application.</span></span> <span data-ttu-id="c595d-192">Zwróć uwagę, że **DeleteItem** przycisk jest wyłączony i że nie można usunąć elementów, naciskając klawisz DELETE.</span><span class="sxs-lookup"><span data-stu-id="c595d-192">Notice that the **DeleteItem** button is disabled and that you cannot delete items by pressing the DELETE key.</span></span>  
  
## <a name="adding-search-capability-to-the-datarepeater-control"></a><span data-ttu-id="c595d-193">Dodawanie możliwości wyszukiwania do formantu DataRepeater</span><span class="sxs-lookup"><span data-stu-id="c595d-193">Adding Search Capability to the DataRepeater Control</span></span>  
 <span data-ttu-id="c595d-194">W tym kroku opcjonalne wdrożenia możliwość wyszukiwania wartości w <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu.</span><span class="sxs-lookup"><span data-stu-id="c595d-194">In this optional step, you implement the capability to search for a value in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="c595d-195">Jeśli zostanie znaleziony ciąg wyszukiwania, formantu wybiera element zawiera wartość, którą można przewinąć element w widoku.</span><span class="sxs-lookup"><span data-stu-id="c595d-195">If the search string is found, the control selects the item that contains the value and scrolls the item into view.</span></span>  
  
#### <a name="to-add-search-capability"></a><span data-ttu-id="c595d-196">Aby dodać możliwości wyszukiwania</span><span class="sxs-lookup"><span data-stu-id="c595d-196">To add search capability</span></span>  
  
1.  <span data-ttu-id="c595d-197">Przeciągnij <xref:System.Windows.Forms.TextBox> kontrolować z **przybornika** na formularz, który zawiera <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu.</span><span class="sxs-lookup"><span data-stu-id="c595d-197">Drag a <xref:System.Windows.Forms.TextBox> control from the **Toolbox** onto the form that contains the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
     <span data-ttu-id="c595d-198">Umieść go w obszarze <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu.</span><span class="sxs-lookup"><span data-stu-id="c595d-198">Position it under the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
2.  <span data-ttu-id="c595d-199">W oknie Właściwości zmień **nazwa** właściwości **SearchTextBox**.</span><span class="sxs-lookup"><span data-stu-id="c595d-199">In the Properties window, change the **Name** property to **SearchTextBox**.</span></span>  
  
3.  <span data-ttu-id="c595d-200">Przeciągnij <xref:System.Windows.Forms.Button> kontrolować z **przybornika** na formularz, który zawiera <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu.</span><span class="sxs-lookup"><span data-stu-id="c595d-200">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto the form that contains the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="c595d-201">Umieść go w obszarze <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu.</span><span class="sxs-lookup"><span data-stu-id="c595d-201">Position it under the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
4.  <span data-ttu-id="c595d-202">W oknie Właściwości zmień **nazwa** właściwości **SearchButton**.</span><span class="sxs-lookup"><span data-stu-id="c595d-202">In the Properties window, change the **Name** property to **SearchButton**.</span></span> <span data-ttu-id="c595d-203">Zmień **tekst** właściwości **wyszukiwania**.</span><span class="sxs-lookup"><span data-stu-id="c595d-203">Change the **Text** property to **Search**.</span></span>  
  
5.  <span data-ttu-id="c595d-204">Kliknij dwukrotnie <xref:System.Windows.Forms.Button> sterowania, aby otworzyć edytora kodu i Dodaj następujący kod do `SearchButton_Click` obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="c595d-204">Double-click the <xref:System.Windows.Forms.Button> control to open the Code Editor, and add the following code to the `SearchButton_Click` event handler.</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_5.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_5.vb)]  
  
6.  <span data-ttu-id="c595d-205">Naciśnij klawisz F5, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="c595d-205">Press F5 to run the application.</span></span> <span data-ttu-id="c595d-206">Wpisz identyfikator klienta w **SearchTextBox** i kliknij przycisk **wyszukiwania** przycisku.</span><span class="sxs-lookup"><span data-stu-id="c595d-206">Type a customer ID in **SearchTextBox** and click the **Search** button.</span></span>  
  
## <a name="adding-a-master-and-detail-table-to-the-datarepeater"></a><span data-ttu-id="c595d-207">Dodawanie głównego i Tabela szczegółów do DataRepeater</span><span class="sxs-lookup"><span data-stu-id="c595d-207">Adding a Master and Detail Table to the DataRepeater</span></span>  
 <span data-ttu-id="c595d-208">W tym kroku opcjonalne, możesz dodać drugi <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu, aby wyświetlić powiązane zamówienia dla każdego klienta.</span><span class="sxs-lookup"><span data-stu-id="c595d-208">In this optional step, you add a second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control to display related orders for each customer.</span></span>  
  
#### <a name="to-add-a-master-and-detail-table"></a><span data-ttu-id="c595d-209">Aby dodać tabelę wzorca i szczegóły</span><span class="sxs-lookup"><span data-stu-id="c595d-209">To add a master and detail table</span></span>  
  
1.  <span data-ttu-id="c595d-210">Przeciągnij drugi <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontrolować z **Visual Basic PowerPacks** karcie **przybornika** na formularzu.</span><span class="sxs-lookup"><span data-stu-id="c595d-210">Drag a second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control from the **Visual Basic PowerPacks** tab in the **Toolbox** onto the form.</span></span>  
  
2.  <span data-ttu-id="c595d-211">W oknie właściwości ustaw **lokalizacji** właściwości `465, 25`.</span><span class="sxs-lookup"><span data-stu-id="c595d-211">In the Properties window, set the **Location** property to `465, 25`.</span></span>  
  
3.  <span data-ttu-id="c595d-212">Ustaw **rozmiar** właściwości `315, 600`.</span><span class="sxs-lookup"><span data-stu-id="c595d-212">Set the **Size** property to `315, 600`.</span></span>  
  
4.  <span data-ttu-id="c595d-213">W **źródeł danych** okna, rozwiń węzeł **klientów** tabeli węzeł, a następnie wybierz węzeł szczegółów **zamówień** tabeli.</span><span class="sxs-lookup"><span data-stu-id="c595d-213">In the **Data Sources** window, expand the **Customers** table node and select the detail node for the **Orders** table.</span></span>  
  
5.  <span data-ttu-id="c595d-214">Zmień typ listy **zamówień** tabeli, aby uzyskać szczegółowe informacje, klikając **szczegóły** na liście rozwijanej na węźle tabeli.</span><span class="sxs-lookup"><span data-stu-id="c595d-214">Change the drop type of this **Orders** table to Details by clicking **Details** in the drop-down list on the table node.</span></span>  
  
6.  <span data-ttu-id="c595d-215">Przeciągnij **zamówień** węzła tabeli na region szablonu elementu (górnej) drugiego <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu.</span><span class="sxs-lookup"><span data-stu-id="c595d-215">Drag this **Orders** table node onto the item template region (the upper region) of the second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
     <span data-ttu-id="c595d-216">**OrdersBindingSource** składnika i **OrdersTableAdapter** składnika są dodawane do składnika na pasku zadań.</span><span class="sxs-lookup"><span data-stu-id="c595d-216">An **OrdersBindingSource** component and an **OrdersTableAdapter** component are added to the Component Tray.</span></span>  
  
7.  <span data-ttu-id="c595d-217">Naciśnij klawisz F5, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="c595d-217">Press F5 to run the application.</span></span> <span data-ttu-id="c595d-218">Po wybraniu każdego klienta w pierwszym <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontrolować zamówienia dla tego klienta są wyświetlane w ciągu sekundy <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu.</span><span class="sxs-lookup"><span data-stu-id="c595d-218">When you select each customer in the first <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control, the orders for that customer are displayed in the second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c595d-219">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c595d-219">See Also</span></span>  
 [<span data-ttu-id="c595d-220">Wprowadzenie do kontrolki DataRepeater</span><span class="sxs-lookup"><span data-stu-id="c595d-220">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="c595d-221">Instrukcje: wyświetlanie powiązanych danych w kontrolce DataRepeater</span><span class="sxs-lookup"><span data-stu-id="c595d-221">How to: Display Bound Data in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="c595d-222">Instrukcje: wyświetlanie niepowiązanych kontrolek w kontrolce DataRepeater</span><span class="sxs-lookup"><span data-stu-id="c595d-222">How to: Display Unbound Controls in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="c595d-223">Instrukcje: zmienianie układu kontrolki DataRepeater</span><span class="sxs-lookup"><span data-stu-id="c595d-223">How to: Change the Layout of a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="c595d-224">Instrukcje: wyświetlanie nagłówków elementów w kontrolce DataRepeater</span><span class="sxs-lookup"><span data-stu-id="c595d-224">How to: Display Item Headers in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="c595d-225">Instrukcje: wyszukiwanie danych w kontrolce DataRepeater</span><span class="sxs-lookup"><span data-stu-id="c595d-225">How to: Search Data in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-search-data-in-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="c595d-226">Porady: Tworzenie formularza wzorzec/szczegół za pomocą dwóch formantów DataRepeater (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="c595d-226">How to: Create a Master/Detail Form by Using Two DataRepeater Controls (Visual Studio)</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)  
 [<span data-ttu-id="c595d-227">Instrukcje: zmienianie wyglądu kontrolki DataRepeater</span><span class="sxs-lookup"><span data-stu-id="c595d-227">How to: Change the Appearance of a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="c595d-228">Instrukcje: wyłączanie dodawania i usuwania elementów DataRepeater</span><span class="sxs-lookup"><span data-stu-id="c595d-228">How to: Disable Adding and Deleting DataRepeater Items</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio.md)  
 [<span data-ttu-id="c595d-229">Rozwiązywanie problemów z kontrolką DataRepeater</span><span class="sxs-lookup"><span data-stu-id="c595d-229">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
