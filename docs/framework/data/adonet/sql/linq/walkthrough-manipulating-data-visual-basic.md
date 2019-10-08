---
title: 'Przewodnik: manipulowanie danymi (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: 1f6a54f6-ec33-452a-a37d-48122207bf14
ms.openlocfilehash: 7acce3f8483fab3c2978de7cbd1b9d875900f1d3
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003399"
---
# <a name="walkthrough-manipulating-data-visual-basic"></a><span data-ttu-id="eb165-102">Przewodnik: manipulowanie danymi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eb165-102">Walkthrough: Manipulating Data (Visual Basic)</span></span>
<span data-ttu-id="eb165-103">Ten Instruktaż zawiera podstawowy, kompleksowy scenariusz [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] na potrzeby dodawania, modyfikowania i usuwania danych w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="eb165-103">This walkthrough provides a fundamental end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario for adding, modifying, and deleting data in a database.</span></span> <span data-ttu-id="eb165-104">Zostanie użyta kopia przykładowej bazy danych Northwind, aby dodać klienta, zmienić nazwę klienta i usunąć zamówienie.</span><span class="sxs-lookup"><span data-stu-id="eb165-104">You will use a copy of the sample Northwind database to add a customer, change the name of a customer, and delete an order.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="eb165-105">Ten Instruktaż został zapisany przy użyciu ustawień tworzenia Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="eb165-105">This walkthrough was written by using Visual Basic Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="eb165-106">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="eb165-106">Prerequisites</span></span>  
 <span data-ttu-id="eb165-107">Ten przewodnik wymaga następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="eb165-107">This walkthrough requires the following:</span></span>  
  
- <span data-ttu-id="eb165-108">W tym instruktażu do przechowywania plików służy dedykowany folder ("c:\linqtest2").</span><span class="sxs-lookup"><span data-stu-id="eb165-108">This walkthrough uses a dedicated folder ("c:\linqtest2") to hold files.</span></span> <span data-ttu-id="eb165-109">Utwórz ten folder przed rozpoczęciem przewodnika.</span><span class="sxs-lookup"><span data-stu-id="eb165-109">Create this folder before you begin the walkthrough.</span></span>  
  
- <span data-ttu-id="eb165-110">Przykładowa bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="eb165-110">The Northwind sample database.</span></span>  
  
     <span data-ttu-id="eb165-111">Jeśli nie masz tej bazy danych na komputerze deweloperskim, możesz ją pobrać z witryny pobierania firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="eb165-111">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="eb165-112">Aby uzyskać instrukcje, zobacz [Pobieranie przykładowych baz danych](downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="eb165-112">For instructions, see [Downloading Sample Databases](downloading-sample-databases.md).</span></span> <span data-ttu-id="eb165-113">Po pobraniu bazy danych Skopiuj plik northwnd. mdf do folderu c:\linqtest2.</span><span class="sxs-lookup"><span data-stu-id="eb165-113">After you have downloaded the database, copy the northwnd.mdf file to the c:\linqtest2 folder.</span></span>  
  
- <span data-ttu-id="eb165-114">Plik kodu Visual Basic wygenerowany na podstawie bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="eb165-114">A Visual Basic code file generated from the Northwind database.</span></span>  
  
     <span data-ttu-id="eb165-115">Ten plik można wygenerować przy użyciu Object Relational Designer lub narzędzia SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="eb165-115">You can generate this file by using either the Object Relational Designer or the SQLMetal tool.</span></span> <span data-ttu-id="eb165-116">Ten Instruktaż został zapisany przy użyciu narzędzia SQLMetal z następującym wierszem polecenia:</span><span class="sxs-lookup"><span data-stu-id="eb165-116">This walkthrough was written by using the SQLMetal tool with the following command line:</span></span>  
  
     <span data-ttu-id="eb165-117">**SQLMetal/Code: "c:\linqtest2\northwind.vb"/Language: VB "C:\linqtest2\northwnd.mdf"/pluralize**</span><span class="sxs-lookup"><span data-stu-id="eb165-117">**sqlmetal /code:"c:\linqtest2\northwind.vb" /language:vb "C:\linqtest2\northwnd.mdf" /pluralize**</span></span>  
  
     <span data-ttu-id="eb165-118">Aby uzyskać więcej informacji, zobacz [SQLMetal. exe (Narzędzie generowania kodu)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="eb165-118">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="eb165-119">Omówienie</span><span class="sxs-lookup"><span data-stu-id="eb165-119">Overview</span></span>  
 <span data-ttu-id="eb165-120">Ten przewodnik składa się z sześciu głównych zadań:</span><span class="sxs-lookup"><span data-stu-id="eb165-120">This walkthrough consists of six main tasks:</span></span>  
  
- <span data-ttu-id="eb165-121">Tworzenie rozwiązania [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="eb165-121">Creating the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>  
  
- <span data-ttu-id="eb165-122">Dodawanie pliku kodu bazy danych do projektu.</span><span class="sxs-lookup"><span data-stu-id="eb165-122">Adding the database code file to the project.</span></span>  
  
- <span data-ttu-id="eb165-123">Tworzenie nowego obiektu klienta.</span><span class="sxs-lookup"><span data-stu-id="eb165-123">Creating a new customer object.</span></span>  
  
- <span data-ttu-id="eb165-124">Modyfikowanie nazwy kontaktu klienta.</span><span class="sxs-lookup"><span data-stu-id="eb165-124">Modifying the contact name of a customer.</span></span>  
  
- <span data-ttu-id="eb165-125">Usuwanie zamówienia.</span><span class="sxs-lookup"><span data-stu-id="eb165-125">Deleting an order.</span></span>  
  
- <span data-ttu-id="eb165-126">Przesyłanie tych zmian do bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="eb165-126">Submitting these changes to the Northwind database.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="eb165-127">Tworzenie rozwiązania LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="eb165-127">Creating a LINQ to SQL Solution</span></span>  
 <span data-ttu-id="eb165-128">W tym pierwszym zadaniu utworzysz rozwiązanie programu Visual Studio, które zawiera niezbędne odwołania do kompilowania i uruchamiania projektu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eb165-128">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="eb165-129">Aby utworzyć rozwiązanie LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="eb165-129">To create a LINQ to SQL solution</span></span>  
  
1. <span data-ttu-id="eb165-130">W menu **plik** programu Visual Studio kliknij pozycję **Nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="eb165-130">On the Visual Studio **File** menu, click **New Project**.</span></span>  
  
2. <span data-ttu-id="eb165-131">W okienku **typy projektów** okna dialogowego **nowy projekt** kliknij **Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="eb165-131">In the **Project types** pane in the **New Project** dialog box, click **Visual Basic**.</span></span>  
  
3. <span data-ttu-id="eb165-132">W okienku **Szablony** kliknij pozycję **Aplikacja konsolowa**.</span><span class="sxs-lookup"><span data-stu-id="eb165-132">In the **Templates** pane, click **Console Application**.</span></span>  
  
4. <span data-ttu-id="eb165-133">W polu **Nazwa** wpisz **LinqDataManipulationApp**.</span><span class="sxs-lookup"><span data-stu-id="eb165-133">In the **Name** box, type **LinqDataManipulationApp**.</span></span>  
  
5. <span data-ttu-id="eb165-134">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="eb165-134">Click **OK**.</span></span>  
  
## <a name="adding-linq-references-and-directives"></a><span data-ttu-id="eb165-135">Dodawanie odwołań i dyrektyw LINQ</span><span class="sxs-lookup"><span data-stu-id="eb165-135">Adding LINQ References and Directives</span></span>  
 <span data-ttu-id="eb165-136">W tym instruktażu są używane zestawy, które mogą nie być instalowane domyślnie w projekcie.</span><span class="sxs-lookup"><span data-stu-id="eb165-136">This walkthrough uses assemblies that might not be installed by default in your project.</span></span> <span data-ttu-id="eb165-137">Jeśli `System.Data.Linq` nie jest wymieniony jako odwołanie w projekcie (kliknij przycisk **Pokaż wszystkie pliki** w **Eksplorator rozwiązań** i rozwiń węzeł **odwołania** ), Dodaj go, jak wyjaśniono w poniższych krokach.</span><span class="sxs-lookup"><span data-stu-id="eb165-137">If `System.Data.Linq` is not listed as a reference in your project (click **Show All Files** in **Solution Explorer** and expand the **References** node), add it, as explained in the following steps.</span></span>  
  
#### <a name="to-add-systemdatalinq"></a><span data-ttu-id="eb165-138">Aby dodać system. Data. LINQ</span><span class="sxs-lookup"><span data-stu-id="eb165-138">To add System.Data.Linq</span></span>  
  
1. <span data-ttu-id="eb165-139">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **odwołania**, a następnie kliknij pozycję **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="eb165-139">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
2. <span data-ttu-id="eb165-140">W oknie dialogowym **Dodawanie odwołania** kliknij pozycję **.NET**, kliknij zestaw system. Data. LINQ, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="eb165-140">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="eb165-141">Zestaw zostanie dodany do projektu.</span><span class="sxs-lookup"><span data-stu-id="eb165-141">The assembly is added to the project.</span></span>  
  
3. <span data-ttu-id="eb165-142">W edytorze kodu Dodaj następujące dyrektywy powyżej **Module1**:</span><span class="sxs-lookup"><span data-stu-id="eb165-142">In the code editor, add the following directives above **Module1**:</span></span>  
  
     [!code-vb[DLinqWalk3VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#1)]  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a><span data-ttu-id="eb165-143">Dodawanie pliku kodu Northwind do projektu</span><span class="sxs-lookup"><span data-stu-id="eb165-143">Adding the Northwind Code File to the Project</span></span>  
 <span data-ttu-id="eb165-144">W tych krokach przyjęto założenie, że użyto narzędzia SQLMetal do wygenerowania pliku kodu z przykładowej bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="eb165-144">These steps assume that you have used the SQLMetal tool to generate a code file from the Northwind sample database.</span></span> <span data-ttu-id="eb165-145">Aby uzyskać więcej informacji, zobacz sekcję wymagania wstępne we wcześniejszej części tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="eb165-145">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a><span data-ttu-id="eb165-146">Aby dodać plik kodu Northwind do projektu</span><span class="sxs-lookup"><span data-stu-id="eb165-146">To add the northwind code file to the project</span></span>  
  
1. <span data-ttu-id="eb165-147">W menu **projekt** kliknij polecenie **Dodaj istniejący element**.</span><span class="sxs-lookup"><span data-stu-id="eb165-147">On the **Project** menu, click **Add Existing Item**.</span></span>  
  
2. <span data-ttu-id="eb165-148">W oknie dialogowym **Dodaj istniejący element** przejdź do c:\linqtest2\northwind.vb, a następnie kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="eb165-148">In the **Add Existing Item** dialog box, navigate to c:\linqtest2\northwind.vb, and then click **Add**.</span></span>  
  
     <span data-ttu-id="eb165-149">Plik Northwind. vb zostanie dodany do projektu.</span><span class="sxs-lookup"><span data-stu-id="eb165-149">The northwind.vb file is added to the project.</span></span>  
  
## <a name="setting-up-the-database-connection"></a><span data-ttu-id="eb165-150">Konfigurowanie połączenia z bazą danych</span><span class="sxs-lookup"><span data-stu-id="eb165-150">Setting Up the Database Connection</span></span>  
 <span data-ttu-id="eb165-151">Najpierw Przetestuj połączenie z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="eb165-151">First, test your connection to the database.</span></span> <span data-ttu-id="eb165-152">Należy pamiętać, że nazwa bazy danych, northwnd, nie ma znaku.</span><span class="sxs-lookup"><span data-stu-id="eb165-152">Note especially that the name of the database, Northwnd, has no i character.</span></span> <span data-ttu-id="eb165-153">W przypadku wygenerowania błędów w następnych krokach przejrzyj plik Northwind. vb, aby określić sposób pisowni klasy częściowej Northwind.</span><span class="sxs-lookup"><span data-stu-id="eb165-153">If you generate errors in the next steps, review the northwind.vb file to determine how the Northwind partial class is spelled.</span></span>  
  
#### <a name="to-set-up-and-test-the-database-connection"></a><span data-ttu-id="eb165-154">Aby skonfigurować i przetestować połączenie z bazą danych</span><span class="sxs-lookup"><span data-stu-id="eb165-154">To set up and test the database connection</span></span>  
  
1. <span data-ttu-id="eb165-155">Wpisz lub wklej następujący kod do `Sub Main`:</span><span class="sxs-lookup"><span data-stu-id="eb165-155">Type or paste the following code into `Sub Main`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#2)]  
  
2. <span data-ttu-id="eb165-156">Naciśnij klawisz F5, aby przetestować aplikację w tym momencie.</span><span class="sxs-lookup"><span data-stu-id="eb165-156">Press F5 to test the application at this point.</span></span>  
  
     <span data-ttu-id="eb165-157">Zostanie otwarte okno **konsoli** .</span><span class="sxs-lookup"><span data-stu-id="eb165-157">A **Console** window opens.</span></span>  
  
     <span data-ttu-id="eb165-158">Zamknij aplikację, naciskając klawisz ENTER w oknie **konsoli** lub klikając przycisk **Zatrzymaj debugowanie** w menu **debugowanie** programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="eb165-158">Close the application by pressing Enter in the **Console** window, or by clicking **Stop Debugging** on the Visual Studio **Debug** menu.</span></span>  
  
## <a name="creating-a-new-entity"></a><span data-ttu-id="eb165-159">Tworzenie nowej jednostki</span><span class="sxs-lookup"><span data-stu-id="eb165-159">Creating a New Entity</span></span>  
 <span data-ttu-id="eb165-160">Tworzenie nowej jednostki jest proste.</span><span class="sxs-lookup"><span data-stu-id="eb165-160">Creating a new entity is straightforward.</span></span> <span data-ttu-id="eb165-161">Obiekty (takie jak `Customer`) można tworzyć za pomocą słowa kluczowego `New`.</span><span class="sxs-lookup"><span data-stu-id="eb165-161">You can create objects (such as `Customer`) by using the `New` keyword.</span></span>  
  
 <span data-ttu-id="eb165-162">W tym i w poniższych sekcjach wprowadzasz zmiany tylko do lokalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="eb165-162">In this and the following sections, you are making changes only to the local cache.</span></span> <span data-ttu-id="eb165-163">Żadne zmiany nie są wysyłane do bazy danych do momentu wywołania <xref:System.Data.Linq.DataContext.SubmitChanges%2A> na końcu tego instruktażu.</span><span class="sxs-lookup"><span data-stu-id="eb165-163">No changes are sent to the database until you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> toward the end of this walkthrough.</span></span>  
  
#### <a name="to-add-a-new-customer-entity-object"></a><span data-ttu-id="eb165-164">Aby dodać nowy obiekt jednostki klienta</span><span class="sxs-lookup"><span data-stu-id="eb165-164">To add a new Customer entity object</span></span>  
  
1. <span data-ttu-id="eb165-165">Utwórz nowy `Customer`, dodając następujący kod przed `Console.ReadLine` w `Sub Main`:</span><span class="sxs-lookup"><span data-stu-id="eb165-165">Create a new `Customer` by adding the following code before `Console.ReadLine` in `Sub Main`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#3)]  
  
2. <span data-ttu-id="eb165-166">Naciśnij klawisz F5, aby debugować rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="eb165-166">Press F5 to debug the solution.</span></span>  
  
     <span data-ttu-id="eb165-167">Wyniki wyświetlane w oknie konsoli są następujące:</span><span class="sxs-lookup"><span data-stu-id="eb165-167">The results that are shown in the console window are as follows:</span></span>  
  
     `Customers matching CA before insert:`  
  
     `Customer ID: CACTU`  
  
     `Customer ID: RICAR`  
  
     <span data-ttu-id="eb165-168">Należy zauważyć, że nowy wiersz nie jest wyświetlany w wynikach.</span><span class="sxs-lookup"><span data-stu-id="eb165-168">Note that the new row does not appear in the results.</span></span> <span data-ttu-id="eb165-169">Nowe dane nie zostały jeszcze przesłane do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="eb165-169">The new data has not yet been submitted to the database.</span></span>  
  
3. <span data-ttu-id="eb165-170">Naciśnij klawisz ENTER w oknie **konsoli** , aby zatrzymać debugowanie.</span><span class="sxs-lookup"><span data-stu-id="eb165-170">Press Enter in the **Console** window to stop debugging.</span></span>  
  
## <a name="updating-an-entity"></a><span data-ttu-id="eb165-171">Aktualizowanie jednostki</span><span class="sxs-lookup"><span data-stu-id="eb165-171">Updating an Entity</span></span>  
 <span data-ttu-id="eb165-172">W poniższych krokach zostanie pobrany obiekt `Customer` i zostanie zmodyfikowana jedna z jego właściwości.</span><span class="sxs-lookup"><span data-stu-id="eb165-172">In the following steps, you will retrieve a `Customer` object and modify one of its properties.</span></span>  
  
#### <a name="to-change-the-name-of-a-customer"></a><span data-ttu-id="eb165-173">Aby zmienić nazwę klienta</span><span class="sxs-lookup"><span data-stu-id="eb165-173">To change the name of a Customer</span></span>  
  
- <span data-ttu-id="eb165-174">Dodaj następujący kod powyżej `Console.ReadLine()`:</span><span class="sxs-lookup"><span data-stu-id="eb165-174">Add the following code above `Console.ReadLine()`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#4)]  
  
## <a name="deleting-an-entity"></a><span data-ttu-id="eb165-175">Usuwanie jednostki</span><span class="sxs-lookup"><span data-stu-id="eb165-175">Deleting an Entity</span></span>  
 <span data-ttu-id="eb165-176">Przy użyciu tego samego obiektu klienta można usunąć pierwszą kolejność.</span><span class="sxs-lookup"><span data-stu-id="eb165-176">Using the same customer object, you can delete the first order.</span></span>  
  
 <span data-ttu-id="eb165-177">Poniższy kod ilustruje sposób tworzenia relacji między wierszami i sposobu usuwania wiersza z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="eb165-177">The following code demonstrates how to sever relationships between rows, and how to delete a row from the database.</span></span>  
  
#### <a name="to-delete-a-row"></a><span data-ttu-id="eb165-178">Aby usunąć wiersz</span><span class="sxs-lookup"><span data-stu-id="eb165-178">To delete a row</span></span>  
  
- <span data-ttu-id="eb165-179">Dodaj następujący kod tuż powyżej `Console.ReadLine()`:</span><span class="sxs-lookup"><span data-stu-id="eb165-179">Add the following code just above `Console.ReadLine()`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#5)]  
  
## <a name="submitting-changes-to-the-database"></a><span data-ttu-id="eb165-180">Przesyłanie zmian do bazy danych</span><span class="sxs-lookup"><span data-stu-id="eb165-180">Submitting Changes to the Database</span></span>  
 <span data-ttu-id="eb165-181">Ostatnim krokiem wymaganym do tworzenia, aktualizowania i usuwania obiektów jest faktyczne przesłanie zmian do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="eb165-181">The final step required for creating, updating, and deleting objects is to actually submit the changes to the database.</span></span> <span data-ttu-id="eb165-182">Bez tego kroku zmiany są tylko lokalne i nie będą wyświetlane w wynikach zapytania.</span><span class="sxs-lookup"><span data-stu-id="eb165-182">Without this step, your changes are only local and will not appear in query results.</span></span>  
  
#### <a name="to-submit-changes-to-the-database"></a><span data-ttu-id="eb165-183">Aby przesłać zmiany do bazy danych</span><span class="sxs-lookup"><span data-stu-id="eb165-183">To submit changes to the database</span></span>  
  
1. <span data-ttu-id="eb165-184">Wstaw następujący kod tuż powyżej `Console.ReadLine`:</span><span class="sxs-lookup"><span data-stu-id="eb165-184">Insert the following code just above `Console.ReadLine`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#6)]  
  
2. <span data-ttu-id="eb165-185">Wstaw następujący kod (po `SubmitChanges`), aby pokazać efekt przed i po przesłaniu zmian:</span><span class="sxs-lookup"><span data-stu-id="eb165-185">Insert the following code (after `SubmitChanges`) to show the before and after effects of submitting the changes:</span></span>  
  
     [!code-vb[DLinqWalk3VB#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#7)]  
  
3. <span data-ttu-id="eb165-186">Naciśnij klawisz F5, aby debugować rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="eb165-186">Press F5 to debug the solution.</span></span>  
  
     <span data-ttu-id="eb165-187">Okno konsoli jest wyświetlane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="eb165-187">The console window appears as follows:</span></span>  
  
    ```console
    Customers matching CA before update:  
    Customer ID: CACTU  
    Customer ID: RICAR  
  
    The Order Detail to be deleted is: OrderID = 10643  
  
    Customers matching CA after update:  
    Customer ID: A3VCA  
    Customer ID: CACTU  
    Customer ID: RICAR  
    ```  
  
4. <span data-ttu-id="eb165-188">Naciśnij klawisz ENTER w oknie **konsoli** , aby zatrzymać debugowanie.</span><span class="sxs-lookup"><span data-stu-id="eb165-188">Press Enter in the **Console** window to stop debugging.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="eb165-189">Po dodaniu nowego klienta przez przesłanie zmian nie można wykonać tego rozwiązania ponownie, ponieważ nie można ponownie dodać tego samego klienta.</span><span class="sxs-lookup"><span data-stu-id="eb165-189">After you have added the new customer by submitting the changes, you cannot execute this solution again as is, because you cannot add the same customer again as is.</span></span> <span data-ttu-id="eb165-190">Aby ponownie wykonać rozwiązanie, należy zmienić wartość identyfikatora klienta, który ma zostać dodany.</span><span class="sxs-lookup"><span data-stu-id="eb165-190">To execute the solution again, change the value of the customer ID to be added.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb165-191">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eb165-191">See also</span></span>

- [<span data-ttu-id="eb165-192">Nauka przez przewodniki</span><span class="sxs-lookup"><span data-stu-id="eb165-192">Learning by Walkthroughs</span></span>](learning-by-walkthroughs.md)
