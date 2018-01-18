---
title: "Wskazówki: Manipulowanie danych (Visual Basic)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: vb
ms.assetid: 1f6a54f6-ec33-452a-a37d-48122207bf14
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: b4bc7baee8e95243cf05a52f49c37aa2d8916666
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="walkthrough-manipulating-data-visual-basic"></a><span data-ttu-id="bac35-102">Wskazówki: Manipulowanie danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bac35-102">Walkthrough: Manipulating Data (Visual Basic)</span></span>
<span data-ttu-id="bac35-103">Ten przewodnik zawiera podstawowe end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenariusza Dodawanie, modyfikowanie i usuwanie danych z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="bac35-103">This walkthrough provides a fundamental end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario for adding, modifying, and deleting data in a database.</span></span> <span data-ttu-id="bac35-104">Aby dodać klienta, Zmień nazwę klienta i usunąć zamówienie będzie używał kopii przykładowej bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="bac35-104">You will use a copy of the sample Northwind database to add a customer, change the name of a customer, and delete an order.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="bac35-105">W tym przewodniku została napisana przy użyciu ustawienia środowiska deweloperskiego Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="bac35-105">This walkthrough was written by using Visual Basic Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="bac35-106">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="bac35-106">Prerequisites</span></span>  
 <span data-ttu-id="bac35-107">W tym przewodniku wymaga następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="bac35-107">This walkthrough requires the following:</span></span>  
  
-   <span data-ttu-id="bac35-108">W tym przewodniku zastosowano dedykowanych folderów ("c:\linqtest2") do przechowywania plików.</span><span class="sxs-lookup"><span data-stu-id="bac35-108">This walkthrough uses a dedicated folder ("c:\linqtest2") to hold files.</span></span> <span data-ttu-id="bac35-109">Utwórz ten folder przed rozpoczęciem przewodnika.</span><span class="sxs-lookup"><span data-stu-id="bac35-109">Create this folder before you begin the walkthrough.</span></span>  
  
-   <span data-ttu-id="bac35-110">Przykładowa bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="bac35-110">The Northwind sample database.</span></span>  
  
     <span data-ttu-id="bac35-111">Jeśli nie ma tej bazy danych na komputerze deweloperskim, można go pobrać z witryny pobierania firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="bac35-111">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="bac35-112">Aby uzyskać instrukcje, zobacz [pobieranie przykładowe bazy danych](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="bac35-112">For instructions, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span> <span data-ttu-id="bac35-113">Po pobraniu bazy danych, skopiuj plik northwnd.mdf do folderu c:\linqtest2.</span><span class="sxs-lookup"><span data-stu-id="bac35-113">After you have downloaded the database, copy the northwnd.mdf file to the c:\linqtest2 folder.</span></span>  
  
-   <span data-ttu-id="bac35-114">Plik kodu języka Visual Basic wygenerowany z bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="bac35-114">A Visual Basic code file generated from the Northwind database.</span></span>  
  
     <span data-ttu-id="bac35-115">Ten plik można wygenerować za pomocą [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] lub narzędzie SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="bac35-115">You can generate this file by using either the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] or the SQLMetal tool.</span></span> <span data-ttu-id="bac35-116">W tym przewodniku została napisana przy użyciu narzędzia SQLMetal z następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="bac35-116">This walkthrough was written by using the SQLMetal tool with the following command line:</span></span>  
  
     <span data-ttu-id="bac35-117">**sqlmetal /code:"c:\linqtest2\northwind.vb" /language:vb "C:\linqtest2\northwnd.mdf" /pluralize**</span><span class="sxs-lookup"><span data-stu-id="bac35-117">**sqlmetal /code:"c:\linqtest2\northwind.vb" /language:vb "C:\linqtest2\northwnd.mdf" /pluralize**</span></span>  
  
     <span data-ttu-id="bac35-118">Aby uzyskać więcej informacji, zobacz [SqlMetal.exe (narzędzie generowania kodu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="bac35-118">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="bac35-119">Omówienie</span><span class="sxs-lookup"><span data-stu-id="bac35-119">Overview</span></span>  
 <span data-ttu-id="bac35-120">Ten przewodnik obejmuje sześć głównych zadań:</span><span class="sxs-lookup"><span data-stu-id="bac35-120">This walkthrough consists of six main tasks:</span></span>  
  
-   <span data-ttu-id="bac35-121">Tworzenie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] rozwiązania [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bac35-121">Creating the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)].</span></span>  
  
-   <span data-ttu-id="bac35-122">Dodawanie plików kodu bazy danych do projektu.</span><span class="sxs-lookup"><span data-stu-id="bac35-122">Adding the database code file to the project.</span></span>  
  
-   <span data-ttu-id="bac35-123">Tworzenie nowego obiektu klienta.</span><span class="sxs-lookup"><span data-stu-id="bac35-123">Creating a new customer object.</span></span>  
  
-   <span data-ttu-id="bac35-124">Modyfikowanie nazwę kontaktu klienta.</span><span class="sxs-lookup"><span data-stu-id="bac35-124">Modifying the contact name of a customer.</span></span>  
  
-   <span data-ttu-id="bac35-125">Usuwanie zamówienia.</span><span class="sxs-lookup"><span data-stu-id="bac35-125">Deleting an order.</span></span>  
  
-   <span data-ttu-id="bac35-126">Przesyłanie te zmiany do bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="bac35-126">Submitting these changes to the Northwind database.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="bac35-127">Tworzenie składnika LINQ to SQL rozwiązania</span><span class="sxs-lookup"><span data-stu-id="bac35-127">Creating a LINQ to SQL Solution</span></span>  
 <span data-ttu-id="bac35-128">W tym zadaniu pierwszym utworzeniu [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] rozwiązania zawierającego niezbędne odwołania, aby skompilować i uruchomić [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu.</span><span class="sxs-lookup"><span data-stu-id="bac35-128">In this first task, you create a [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="bac35-129">Aby utworzyć składnika LINQ to SQL rozwiązania</span><span class="sxs-lookup"><span data-stu-id="bac35-129">To create a LINQ to SQL solution</span></span>  
  
1.  <span data-ttu-id="bac35-130">Na [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] **pliku** menu, kliknij przycisk **nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="bac35-130">On the [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] **File** menu, click **New Project**.</span></span>  
  
2.  <span data-ttu-id="bac35-131">W **typy projektów** okienka w **nowy projekt** okno dialogowe, kliknij przycisk **Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="bac35-131">In the **Project types** pane in the **New Project** dialog box, click **Visual Basic**.</span></span>  
  
3.  <span data-ttu-id="bac35-132">W **szablony** okienku, kliknij przycisk **aplikacji konsoli**.</span><span class="sxs-lookup"><span data-stu-id="bac35-132">In the **Templates** pane, click **Console Application**.</span></span>  
  
4.  <span data-ttu-id="bac35-133">W **nazwa** wpisz **LinqDataManipulationApp**.</span><span class="sxs-lookup"><span data-stu-id="bac35-133">In the **Name** box, type **LinqDataManipulationApp**.</span></span>  
  
5.  <span data-ttu-id="bac35-134">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="bac35-134">Click **OK**.</span></span>  
  
## <a name="adding-linq-references-and-directives"></a><span data-ttu-id="bac35-135">Dodawanie odwołań LINQ i dyrektywy</span><span class="sxs-lookup"><span data-stu-id="bac35-135">Adding LINQ References and Directives</span></span>  
 <span data-ttu-id="bac35-136">W tym przewodniku zastosowano zestawy, które nie mogą być instalowane domyślnie w projekcie.</span><span class="sxs-lookup"><span data-stu-id="bac35-136">This walkthrough uses assemblies that might not be installed by default in your project.</span></span> <span data-ttu-id="bac35-137">Jeśli `System.Data.Linq` nie jest wymieniony jako odwołanie do projektu (kliknij **Pokaż wszystkie pliki** w **Eksploratora rozwiązań** i rozwiń **odwołania** węzła), dodaj ją, zgodnie z objaśnieniem w Poniższe kroki.</span><span class="sxs-lookup"><span data-stu-id="bac35-137">If `System.Data.Linq` is not listed as a reference in your project (click **Show All Files** in **Solution Explorer** and expand the **References** node), add it, as explained in the following steps.</span></span>  
  
#### <a name="to-add-systemdatalinq"></a><span data-ttu-id="bac35-138">To add System.Data.Linq</span><span class="sxs-lookup"><span data-stu-id="bac35-138">To add System.Data.Linq</span></span>  
  
1.  <span data-ttu-id="bac35-139">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania**, a następnie kliknij przycisk **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="bac35-139">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="bac35-140">W **Dodaj odwołanie** okno dialogowe, kliknij przycisk **.NET**, kliknij zestaw System.Data.Linq, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="bac35-140">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="bac35-141">Zestaw został dodany do projektu.</span><span class="sxs-lookup"><span data-stu-id="bac35-141">The assembly is added to the project.</span></span>  
  
3.  <span data-ttu-id="bac35-142">W edytorze kodu, Dodaj następujące dyrektywy powyżej **Module1**:</span><span class="sxs-lookup"><span data-stu-id="bac35-142">In the code editor, add the following directives above **Module1**:</span></span>  
  
     [!code-vb[DLinqWalk3VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#1)]  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a><span data-ttu-id="bac35-143">Dodawanie plików kodu Northwind do projektu</span><span class="sxs-lookup"><span data-stu-id="bac35-143">Adding the Northwind Code File to the Project</span></span>  
 <span data-ttu-id="bac35-144">Tych krokach przyjęto założenie, aby wygenerować plik kodu z przykładowej bazy danych Northwind użycie narzędzia SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="bac35-144">These steps assume that you have used the SQLMetal tool to generate a code file from the Northwind sample database.</span></span> <span data-ttu-id="bac35-145">Aby uzyskać więcej informacji zobacz sekcję wymagań wstępnych we wcześniejszej części tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="bac35-145">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a><span data-ttu-id="bac35-146">Aby dodać plik kodu northwind do projektu</span><span class="sxs-lookup"><span data-stu-id="bac35-146">To add the northwind code file to the project</span></span>  
  
1.  <span data-ttu-id="bac35-147">Na **projektu** menu, kliknij przycisk **Dodaj istniejący element**.</span><span class="sxs-lookup"><span data-stu-id="bac35-147">On the **Project** menu, click **Add Existing Item**.</span></span>  
  
2.  <span data-ttu-id="bac35-148">W **Dodaj istniejący element** okno dialogowe, przejdź do c:\linqtest2\northwind.vb, a następnie kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="bac35-148">In the **Add Existing Item** dialog box, navigate to c:\linqtest2\northwind.vb, and then click **Add**.</span></span>  
  
     <span data-ttu-id="bac35-149">Plik northwind.vb zostanie dodany do projektu.</span><span class="sxs-lookup"><span data-stu-id="bac35-149">The northwind.vb file is added to the project.</span></span>  
  
## <a name="setting-up-the-database-connection"></a><span data-ttu-id="bac35-150">Trwa konfigurowanie połączenia z bazą danych</span><span class="sxs-lookup"><span data-stu-id="bac35-150">Setting Up the Database Connection</span></span>  
 <span data-ttu-id="bac35-151">Najpierw należy przetestować połączenie z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="bac35-151">First, test your connection to the database.</span></span> <span data-ttu-id="bac35-152">Szczególnie Pamiętaj, że nazwa bazy danych, Northwnd, nie ma żadnych i znak.</span><span class="sxs-lookup"><span data-stu-id="bac35-152">Note especially that the name of the database, Northwnd, has no i character.</span></span> <span data-ttu-id="bac35-153">Jeśli generować błędy w następnych krokach, przejrzyj plik northwind.vb ustalenie, jak została wpisana Northwind klasy częściowej.</span><span class="sxs-lookup"><span data-stu-id="bac35-153">If you generate errors in the next steps, review the northwind.vb file to determine how the Northwind partial class is spelled.</span></span>  
  
#### <a name="to-set-up-and-test-the-database-connection"></a><span data-ttu-id="bac35-154">Aby skonfigurować i przetestować połączenie z bazą danych</span><span class="sxs-lookup"><span data-stu-id="bac35-154">To set up and test the database connection</span></span>  
  
1.  <span data-ttu-id="bac35-155">Wpisz lub wklej następujący kod do `Sub Main`:</span><span class="sxs-lookup"><span data-stu-id="bac35-155">Type or paste the following code into `Sub Main`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#2)]  
  
2.  <span data-ttu-id="bac35-156">Naciśnij klawisz F5, aby przetestować aplikację na tym etapie.</span><span class="sxs-lookup"><span data-stu-id="bac35-156">Press F5 to test the application at this point.</span></span>  
  
     <span data-ttu-id="bac35-157">A **konsoli** zostanie otwarte okno.</span><span class="sxs-lookup"><span data-stu-id="bac35-157">A **Console** window opens.</span></span>  
  
     <span data-ttu-id="bac35-158">Zamknij aplikację, naciskając klawisz Enter w **konsoli** okna, lub przez kliknięcie przycisku **Zatrzymaj debugowanie** na [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] **debugowania** menu.</span><span class="sxs-lookup"><span data-stu-id="bac35-158">Close the application by pressing Enter in the **Console** window, or by clicking **Stop Debugging** on the [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] **Debug** menu.</span></span>  
  
## <a name="creating-a-new-entity"></a><span data-ttu-id="bac35-159">Tworzenie nowej jednostki</span><span class="sxs-lookup"><span data-stu-id="bac35-159">Creating a New Entity</span></span>  
 <span data-ttu-id="bac35-160">Tworzenie nowej jednostki jest prosta.</span><span class="sxs-lookup"><span data-stu-id="bac35-160">Creating a new entity is straightforward.</span></span> <span data-ttu-id="bac35-161">Można utworzyć obiektów (takich jak `Customer`) przy użyciu `New` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="bac35-161">You can create objects (such as `Customer`) by using the `New` keyword.</span></span>  
  
 <span data-ttu-id="bac35-162">W tym i sekcje wprowadzania zmian tylko do lokalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="bac35-162">In this and the following sections, you are making changes only to the local cache.</span></span> <span data-ttu-id="bac35-163">Żadne zmiany nie są wysyłane do bazy danych do czasu wywołania <xref:System.Data.Linq.DataContext.SubmitChanges%2A> do końca tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="bac35-163">No changes are sent to the database until you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> toward the end of this walkthrough.</span></span>  
  
#### <a name="to-add-a-new-customer-entity-object"></a><span data-ttu-id="bac35-164">Aby dodać nowy obiekt jednostki klienta</span><span class="sxs-lookup"><span data-stu-id="bac35-164">To add a new Customer entity object</span></span>  
  
1.  <span data-ttu-id="bac35-165">Utwórz nową `Customer` przez dodanie poniższego kodu przed `Console.ReadLine` w `Sub Main`:</span><span class="sxs-lookup"><span data-stu-id="bac35-165">Create a new `Customer` by adding the following code before `Console.ReadLine` in `Sub Main`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#3)]  
  
2.  <span data-ttu-id="bac35-166">Naciśnij klawisz F5, aby debugować rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="bac35-166">Press F5 to debug the solution.</span></span>  
  
     <span data-ttu-id="bac35-167">Wyniki, które są wyświetlane w oknie konsoli są następujące:</span><span class="sxs-lookup"><span data-stu-id="bac35-167">The results that are shown in the console window are as follows:</span></span>  
  
     `Customers matching CA before insert:`  
  
     `Customer ID: CACTU`  
  
     `Customer ID: RICAR`  
  
     <span data-ttu-id="bac35-168">Należy pamiętać, że nowy wiersz nie są wyświetlane w wynikach.</span><span class="sxs-lookup"><span data-stu-id="bac35-168">Note that the new row does not appear in the results.</span></span> <span data-ttu-id="bac35-169">Nowe dane nie ma jeszcze przesłane do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="bac35-169">The new data has not yet been submitted to the database.</span></span>  
  
3.  <span data-ttu-id="bac35-170">Naciśnij klawisz Enter w **konsoli** okno, aby zatrzymać debugowanie.</span><span class="sxs-lookup"><span data-stu-id="bac35-170">Press Enter in the **Console** window to stop debugging.</span></span>  
  
## <a name="updating-an-entity"></a><span data-ttu-id="bac35-171">Aktualizowanie jednostki</span><span class="sxs-lookup"><span data-stu-id="bac35-171">Updating an Entity</span></span>  
 <span data-ttu-id="bac35-172">W poniższych krokach będą pobierane `Customer` obiektów i zmodyfikować jednej z jego właściwości.</span><span class="sxs-lookup"><span data-stu-id="bac35-172">In the following steps, you will retrieve a `Customer` object and modify one of its properties.</span></span>  
  
#### <a name="to-change-the-name-of-a-customer"></a><span data-ttu-id="bac35-173">Aby zmienić nazwę klienta</span><span class="sxs-lookup"><span data-stu-id="bac35-173">To change the name of a Customer</span></span>  
  
-   <span data-ttu-id="bac35-174">Dodaj następujący kod powyżej `Console.ReadLine()`:</span><span class="sxs-lookup"><span data-stu-id="bac35-174">Add the following code above `Console.ReadLine()`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#4)]  
  
## <a name="deleting-an-entity"></a><span data-ttu-id="bac35-175">Usuwanie jednostki</span><span class="sxs-lookup"><span data-stu-id="bac35-175">Deleting an Entity</span></span>  
 <span data-ttu-id="bac35-176">Przy użyciu tego samego obiektu klienta, możesz usunąć pierwszej kolejności.</span><span class="sxs-lookup"><span data-stu-id="bac35-176">Using the same customer object, you can delete the first order.</span></span>  
  
 <span data-ttu-id="bac35-177">Poniższy kod przedstawia sposób sever relacje między wierszami i sposobu usunięcia wiersza z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="bac35-177">The following code demonstrates how to sever relationships between rows, and how to delete a row from the database.</span></span>  
  
#### <a name="to-delete-a-row"></a><span data-ttu-id="bac35-178">Aby usunąć wiersz</span><span class="sxs-lookup"><span data-stu-id="bac35-178">To delete a row</span></span>  
  
-   <span data-ttu-id="bac35-179">Dodaj następujący kod po prostu powyżej `Console.ReadLine()`:</span><span class="sxs-lookup"><span data-stu-id="bac35-179">Add the following code just above `Console.ReadLine()`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#5)]  
  
## <a name="submitting-changes-to-the-database"></a><span data-ttu-id="bac35-180">Przesyłanie zmian w bazie danych</span><span class="sxs-lookup"><span data-stu-id="bac35-180">Submitting Changes to the Database</span></span>  
 <span data-ttu-id="bac35-181">Ostatni krok wymagany do tworzenia, aktualizowania i usuwania obiektów jest rzeczywiście przesłać zmiany w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="bac35-181">The final step required for creating, updating, and deleting objects is to actually submit the changes to the database.</span></span> <span data-ttu-id="bac35-182">Bez tego kroku zmiany są tylko lokalne i nie będą widoczne w wynikach zapytania.</span><span class="sxs-lookup"><span data-stu-id="bac35-182">Without this step, your changes are only local and will not appear in query results.</span></span>  
  
#### <a name="to-submit-changes-to-the-database"></a><span data-ttu-id="bac35-183">Aby przesłać zmiany w bazie danych</span><span class="sxs-lookup"><span data-stu-id="bac35-183">To submit changes to the database</span></span>  
  
1.  <span data-ttu-id="bac35-184">Wstaw poniższy kod nad `Console.ReadLine`:</span><span class="sxs-lookup"><span data-stu-id="bac35-184">Insert the following code just above `Console.ReadLine`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#6)]  
  
2.  <span data-ttu-id="bac35-185">Wstaw następujący kod (po `SubmitChanges`) do wyświetlenia przed i po skutków przesyłanie zmian:</span><span class="sxs-lookup"><span data-stu-id="bac35-185">Insert the following code (after `SubmitChanges`) to show the before and after effects of submitting the changes:</span></span>  
  
     [!code-vb[DLinqWalk3VB#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#7)]  
  
3.  <span data-ttu-id="bac35-186">Naciśnij klawisz F5, aby debugować rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="bac35-186">Press F5 to debug the solution.</span></span>  
  
     <span data-ttu-id="bac35-187">W oknie konsoli wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="bac35-187">The console window appears as follows:</span></span>  
  
    ```  
    Customers matching CA before update:  
    Customer ID: CACTU  
    Customer ID: RICAR  
  
    The Order Detail to be deleted is: OrderID = 10643  
  
    Customers matching CA after update:  
    Customer ID: A3VCA  
    Customer ID: CACTU  
    Customer ID: RICAR  
    ```  
  
4.  <span data-ttu-id="bac35-188">Naciśnij klawisz Enter w **konsoli** okno, aby zatrzymać debugowanie.</span><span class="sxs-lookup"><span data-stu-id="bac35-188">Press Enter in the **Console** window to stop debugging.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bac35-189">Po dodaniu nowego klienta, przesyłając zmiany, nie można wykonać tego rozwiązania ponownie, ponieważ nie można dodać tego samego klienta ponownie jako jest.</span><span class="sxs-lookup"><span data-stu-id="bac35-189">After you have added the new customer by submitting the changes, you cannot execute this solution again as is, because you cannot add the same customer again as is.</span></span> <span data-ttu-id="bac35-190">Aby wykonać ponownie rozwiązanie, zmienić wartości Identyfikatora klienta ma zostać dodana.</span><span class="sxs-lookup"><span data-stu-id="bac35-190">To execute the solution again, change the value of the customer ID to be added.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bac35-191">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bac35-191">See Also</span></span>  
 [<span data-ttu-id="bac35-192">Nauka przez przewodniki</span><span class="sxs-lookup"><span data-stu-id="bac35-192">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
