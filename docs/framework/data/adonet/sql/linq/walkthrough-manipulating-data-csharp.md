---
title: 'Wskazówki: Manipulowanie danych (C#)'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 24adfbe0-0ad6-449f-997d-8808e0770d2e
caps.latest.revision: 2
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: d1851bd4c358b96cc9b49f274b31f5f69d9b8d7b
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="walkthrough-manipulating-data-c"></a><span data-ttu-id="e22e8-102">Wskazówki: Manipulowanie danych (C#)</span><span class="sxs-lookup"><span data-stu-id="e22e8-102">Walkthrough: Manipulating Data (C#)</span></span>
<span data-ttu-id="e22e8-103">Ten przewodnik zawiera podstawowe end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenariusza Dodawanie, modyfikowanie i usuwanie danych z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="e22e8-103">This walkthrough provides a fundamental end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario for adding, modifying, and deleting data in a database.</span></span> <span data-ttu-id="e22e8-104">Aby dodać klienta, Zmień nazwę klienta i usunąć zamówienie będzie używał kopii przykładowej bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="e22e8-104">You will use a copy of the sample Northwind database to add a customer, change the name of a customer, and delete an order.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="e22e8-105">W tym przewodniku została napisana przy użyciu programu Visual C# programowanie ustawienia.</span><span class="sxs-lookup"><span data-stu-id="e22e8-105">This walkthrough was written by using Visual C# Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="e22e8-106">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="e22e8-106">Prerequisites</span></span>  
 <span data-ttu-id="e22e8-107">W tym przewodniku wymaga następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="e22e8-107">This walkthrough requires the following:</span></span>  
  
-   <span data-ttu-id="e22e8-108">W tym przewodniku zastosowano dedykowanych folderów ("c:\linqtest6") do przechowywania plików.</span><span class="sxs-lookup"><span data-stu-id="e22e8-108">This walkthrough uses a dedicated folder ("c:\linqtest6") to hold files.</span></span> <span data-ttu-id="e22e8-109">Utwórz ten folder przed rozpoczęciem przewodnika.</span><span class="sxs-lookup"><span data-stu-id="e22e8-109">Create this folder before you begin the walkthrough.</span></span>  
  
-   <span data-ttu-id="e22e8-110">Przykładowa bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="e22e8-110">The Northwind sample database.</span></span>  
  
     <span data-ttu-id="e22e8-111">Jeśli nie ma tej bazy danych na komputerze deweloperskim, można go pobrać z witryny pobierania firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="e22e8-111">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="e22e8-112">Aby uzyskać instrukcje, zobacz [pobieranie przykładowe bazy danych](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="e22e8-112">For instructions, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span> <span data-ttu-id="e22e8-113">Po pobraniu bazy danych, skopiuj plik northwnd.mdf do folderu c:\linqtest6.</span><span class="sxs-lookup"><span data-stu-id="e22e8-113">After you have downloaded the database, copy the northwnd.mdf file to the c:\linqtest6 folder.</span></span>  
  
-   <span data-ttu-id="e22e8-114">Plik kodu C# wygenerowany z bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="e22e8-114">A C# code file generated from the Northwind database.</span></span>  
  
     <span data-ttu-id="e22e8-115">Ten plik można wygenerować za pomocą [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] lub narzędzie SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="e22e8-115">You can generate this file by using either the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] or the SQLMetal tool.</span></span> <span data-ttu-id="e22e8-116">W tym przewodniku została napisana przy użyciu narzędzia SQLMetal z następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="e22e8-116">This walkthrough was written by using the SQLMetal tool with the following command line:</span></span>  
  
     <span data-ttu-id="e22e8-117">**sqlmetal /code:"c:\linqtest6\northwind.cs" /language:csharp "C:\linqtest6\northwnd.mdf" / pluralize**</span><span class="sxs-lookup"><span data-stu-id="e22e8-117">**sqlmetal /code:"c:\linqtest6\northwind.cs" /language:csharp "C:\linqtest6\northwnd.mdf" /pluralize**</span></span>  
  
     <span data-ttu-id="e22e8-118">Aby uzyskać więcej informacji, zobacz [SqlMetal.exe (narzędzie generowania kodu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="e22e8-118">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="e22e8-119">Omówienie</span><span class="sxs-lookup"><span data-stu-id="e22e8-119">Overview</span></span>  
 <span data-ttu-id="e22e8-120">Ten przewodnik obejmuje sześć głównych zadań:</span><span class="sxs-lookup"><span data-stu-id="e22e8-120">This walkthrough consists of six main tasks:</span></span>  
  
-   <span data-ttu-id="e22e8-121">Tworzenie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] rozwiązania w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e22e8-121">Creating the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>  
  
-   <span data-ttu-id="e22e8-122">Dodawanie plików kodu bazy danych do projektu.</span><span class="sxs-lookup"><span data-stu-id="e22e8-122">Adding the database code file to the project.</span></span>  
  
-   <span data-ttu-id="e22e8-123">Tworzenie nowego obiektu klienta.</span><span class="sxs-lookup"><span data-stu-id="e22e8-123">Creating a new customer object.</span></span>  
  
-   <span data-ttu-id="e22e8-124">Modyfikowanie nazwę kontaktu klienta.</span><span class="sxs-lookup"><span data-stu-id="e22e8-124">Modifying the contact name of a customer.</span></span>  
  
-   <span data-ttu-id="e22e8-125">Usuwanie zamówienia.</span><span class="sxs-lookup"><span data-stu-id="e22e8-125">Deleting an order.</span></span>  
  
-   <span data-ttu-id="e22e8-126">Przesyłanie te zmiany do bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="e22e8-126">Submitting these changes to the Northwind database.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="e22e8-127">Tworzenie składnika LINQ to SQL rozwiązania</span><span class="sxs-lookup"><span data-stu-id="e22e8-127">Creating a LINQ to SQL Solution</span></span>  
 <span data-ttu-id="e22e8-128">W tym zadaniu pierwszego tworzenia rozwiązania Visual Studio, który zawiera niezbędne odwołania, aby skompilować i uruchomić [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu.</span><span class="sxs-lookup"><span data-stu-id="e22e8-128">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="e22e8-129">Aby utworzyć składnika LINQ to SQL rozwiązania</span><span class="sxs-lookup"><span data-stu-id="e22e8-129">To create a LINQ to SQL solution</span></span>  
  
1.  <span data-ttu-id="e22e8-130">W programie Visual Studio **pliku** menu wskaż **nowy**, a następnie kliknij przycisk **projektu**.</span><span class="sxs-lookup"><span data-stu-id="e22e8-130">On the Visual Studio **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="e22e8-131">W **typy projektów** okienka w **nowy projekt** okno dialogowe, kliknij przycisk **Visual C#**.</span><span class="sxs-lookup"><span data-stu-id="e22e8-131">In the **Project types** pane in the **New Project** dialog box, click **Visual C#**.</span></span>  
  
3.  <span data-ttu-id="e22e8-132">W **szablony** okienku, kliknij przycisk **aplikacji konsoli**.</span><span class="sxs-lookup"><span data-stu-id="e22e8-132">In the **Templates** pane, click **Console Application**.</span></span>  
  
4.  <span data-ttu-id="e22e8-133">W **nazwa** wpisz **LinqDataManipulationApp**.</span><span class="sxs-lookup"><span data-stu-id="e22e8-133">In the **Name** box, type **LinqDataManipulationApp**.</span></span>  
  
5.  <span data-ttu-id="e22e8-134">W **lokalizacji** upewnij się, którym chcesz przechowywać pliki projektu.</span><span class="sxs-lookup"><span data-stu-id="e22e8-134">In the **Location** box, verify where you want to store your project files.</span></span>  
  
6.  <span data-ttu-id="e22e8-135">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="e22e8-135">Click **OK**.</span></span>  
  
## <a name="adding-linq-references-and-directives"></a><span data-ttu-id="e22e8-136">Dodawanie odwołań LINQ i dyrektywy</span><span class="sxs-lookup"><span data-stu-id="e22e8-136">Adding LINQ References and Directives</span></span>  
 <span data-ttu-id="e22e8-137">W tym przewodniku zastosowano zestawy, które nie mogą być instalowane domyślnie w projekcie.</span><span class="sxs-lookup"><span data-stu-id="e22e8-137">This walkthrough uses assemblies that might not be installed by default in your project.</span></span> <span data-ttu-id="e22e8-138">Jeśli System.Data.Linq nie jest wymieniony jako odwołanie do projektu, dodaj ją, zgodnie z objaśnieniem w poniższych krokach:</span><span class="sxs-lookup"><span data-stu-id="e22e8-138">If System.Data.Linq is not listed as a reference in your project, add it, as explained in the following steps:</span></span>  
  
#### <a name="to-add-systemdatalinq"></a><span data-ttu-id="e22e8-139">To add System.Data.Linq</span><span class="sxs-lookup"><span data-stu-id="e22e8-139">To add System.Data.Linq</span></span>  
  
1.  <span data-ttu-id="e22e8-140">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania**, a następnie kliknij przycisk **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="e22e8-140">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="e22e8-141">W **Dodaj odwołanie** okno dialogowe, kliknij przycisk **.NET**, kliknij zestaw System.Data.Linq, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="e22e8-141">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="e22e8-142">Zestaw został dodany do projektu.</span><span class="sxs-lookup"><span data-stu-id="e22e8-142">The assembly is added to the project.</span></span>  
  
3.  <span data-ttu-id="e22e8-143">Dodaj następujące dyrektywy na początku pliku Program.cs:</span><span class="sxs-lookup"><span data-stu-id="e22e8-143">Add the following directives at the top of Program.cs:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#1)]  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a><span data-ttu-id="e22e8-144">Dodawanie plików kodu Northwind do projektu</span><span class="sxs-lookup"><span data-stu-id="e22e8-144">Adding the Northwind Code File to the Project</span></span>  
 <span data-ttu-id="e22e8-145">Tych krokach przyjęto założenie, aby wygenerować plik kodu z przykładowej bazy danych Northwind użycie narzędzia SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="e22e8-145">These steps assume that you have used the SQLMetal tool to generate a code file from the Northwind sample database.</span></span> <span data-ttu-id="e22e8-146">Aby uzyskać więcej informacji zobacz sekcję wymagań wstępnych we wcześniejszej części tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="e22e8-146">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a><span data-ttu-id="e22e8-147">Aby dodać plik kodu northwind do projektu</span><span class="sxs-lookup"><span data-stu-id="e22e8-147">To add the northwind code file to the project</span></span>  
  
1.  <span data-ttu-id="e22e8-148">Na **projektu** menu, kliknij przycisk **Dodaj istniejący element**.</span><span class="sxs-lookup"><span data-stu-id="e22e8-148">On the **Project** menu, click **Add Existing Item**.</span></span>  
  
2.  <span data-ttu-id="e22e8-149">W **Dodaj istniejący element** okno dialogowe, przejdź do c:\linqtest6\northwind.cs, a następnie kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="e22e8-149">In the **Add Existing Item** dialog box, navigate to c:\linqtest6\northwind.cs, and then click **Add**.</span></span>  
  
     <span data-ttu-id="e22e8-150">Plik northwind.cs zostanie dodany do projektu.</span><span class="sxs-lookup"><span data-stu-id="e22e8-150">The northwind.cs file is added to the project.</span></span>  
  
## <a name="setting-up-the-database-connection"></a><span data-ttu-id="e22e8-151">Trwa konfigurowanie połączenia z bazą danych</span><span class="sxs-lookup"><span data-stu-id="e22e8-151">Setting Up the Database Connection</span></span>  
 <span data-ttu-id="e22e8-152">Najpierw należy przetestować połączenie z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="e22e8-152">First, test your connection to the database.</span></span> <span data-ttu-id="e22e8-153">Szczególnie Pamiętaj, że bazy danych, Northwnd, nie ma żadnych i znak.</span><span class="sxs-lookup"><span data-stu-id="e22e8-153">Note especially that the database, Northwnd, has no i character.</span></span> <span data-ttu-id="e22e8-154">Jeśli generować błędy w następnych krokach, przejrzyj plik northwind.cs ustalenie, jak została wpisana Northwind klasy częściowej.</span><span class="sxs-lookup"><span data-stu-id="e22e8-154">If you generate errors in the next steps, review the northwind.cs file to determine how the Northwind partial class is spelled.</span></span>  
  
#### <a name="to-set-up-and-test-the-database-connection"></a><span data-ttu-id="e22e8-155">Aby skonfigurować i przetestować połączenie z bazą danych</span><span class="sxs-lookup"><span data-stu-id="e22e8-155">To set up and test the database connection</span></span>  
  
1.  <span data-ttu-id="e22e8-156">Wpisz lub wklej następujący kod do `Main` metody w klasie Program:</span><span class="sxs-lookup"><span data-stu-id="e22e8-156">Type or paste the following code into the `Main` method in the Program class:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#2)]  
  
2.  <span data-ttu-id="e22e8-157">Naciśnij klawisz F5, aby przetestować aplikację na tym etapie.</span><span class="sxs-lookup"><span data-stu-id="e22e8-157">Press F5 to test the application at this point.</span></span>  
  
     <span data-ttu-id="e22e8-158">A **konsoli** zostanie otwarte okno.</span><span class="sxs-lookup"><span data-stu-id="e22e8-158">A **Console** window opens.</span></span>  
  
     <span data-ttu-id="e22e8-159">Możesz zamknąć aplikację, naciskając klawisz Enter w **konsoli** okna, lub przez kliknięcie przycisku **Zatrzymaj debugowanie** w programie Visual Studio **debugowania** menu.</span><span class="sxs-lookup"><span data-stu-id="e22e8-159">You can close the application by pressing Enter in the **Console** window, or by clicking **Stop Debugging** on the Visual Studio **Debug** menu.</span></span>  
  
## <a name="creating-a-new-entity"></a><span data-ttu-id="e22e8-160">Tworzenie nowej jednostki</span><span class="sxs-lookup"><span data-stu-id="e22e8-160">Creating a New Entity</span></span>  
 <span data-ttu-id="e22e8-161">Tworzenie nowej jednostki jest prosta.</span><span class="sxs-lookup"><span data-stu-id="e22e8-161">Creating a new entity is straightforward.</span></span> <span data-ttu-id="e22e8-162">Można utworzyć obiektów (takich jak `Customer`) przy użyciu `new` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="e22e8-162">You can create objects (such as `Customer`) by using the `new` keyword.</span></span>  
  
 <span data-ttu-id="e22e8-163">W tym i sekcje wprowadzania zmian tylko do lokalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="e22e8-163">In this and the following sections, you are making changes only to the local cache.</span></span> <span data-ttu-id="e22e8-164">Żadne zmiany nie są wysyłane do bazy danych do czasu wywołania <xref:System.Data.Linq.DataContext.SubmitChanges%2A> do końca tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="e22e8-164">No changes are sent to the database until you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> toward the end of this walkthrough.</span></span>  
  
#### <a name="to-add-a-new-customer-entity-object"></a><span data-ttu-id="e22e8-165">Aby dodać nowy obiekt jednostki klienta</span><span class="sxs-lookup"><span data-stu-id="e22e8-165">To add a new Customer entity object</span></span>  
  
1.  <span data-ttu-id="e22e8-166">Utwórz nową `Customer` przez dodanie poniższego kodu przed `Console.ReadLine();` w `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="e22e8-166">Create a new `Customer` by adding the following code before `Console.ReadLine();` in the `Main` method:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#3)]  
  
2.  <span data-ttu-id="e22e8-167">Naciśnij klawisz F5, aby debugować rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="e22e8-167">Press F5 to debug the solution.</span></span>  
  
3.  <span data-ttu-id="e22e8-168">Naciśnij klawisz Enter w **konsoli** okno, aby zatrzymać debugowanie i kontynuować przewodnika.</span><span class="sxs-lookup"><span data-stu-id="e22e8-168">Press Enter in the **Console** window to stop debugging and continue the walkthrough.</span></span>  
  
## <a name="updating-an-entity"></a><span data-ttu-id="e22e8-169">Aktualizowanie jednostki</span><span class="sxs-lookup"><span data-stu-id="e22e8-169">Updating an Entity</span></span>  
 <span data-ttu-id="e22e8-170">W poniższych krokach będą pobierane `Customer` obiektów i zmodyfikować jednej z jego właściwości.</span><span class="sxs-lookup"><span data-stu-id="e22e8-170">In the following steps, you will retrieve a `Customer` object and modify one of its properties.</span></span>  
  
#### <a name="to-change-the-name-of-a-customer"></a><span data-ttu-id="e22e8-171">Aby zmienić nazwę klienta</span><span class="sxs-lookup"><span data-stu-id="e22e8-171">To change the name of a Customer</span></span>  
  
-   <span data-ttu-id="e22e8-172">Dodaj następujący kod powyżej `Console.ReadLine();`:</span><span class="sxs-lookup"><span data-stu-id="e22e8-172">Add the following code above `Console.ReadLine();`:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#4)]  
  
## <a name="deleting-an-entity"></a><span data-ttu-id="e22e8-173">Usuwanie jednostki</span><span class="sxs-lookup"><span data-stu-id="e22e8-173">Deleting an Entity</span></span>  
 <span data-ttu-id="e22e8-174">Przy użyciu tego samego obiektu klienta, możesz usunąć pierwszej kolejności.</span><span class="sxs-lookup"><span data-stu-id="e22e8-174">Using the same customer object, you can delete the first order.</span></span>  
  
 <span data-ttu-id="e22e8-175">Poniższy kod przedstawia sposób sever relacje między wierszami i sposobu usunięcia wiersza z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="e22e8-175">The following code demonstrates how to sever relationships between rows, and how to delete a row from the database.</span></span> <span data-ttu-id="e22e8-176">Dodaj następujący kod przed `Console.ReadLine` aby zobaczyć, jak obiekty zostaną usunięte:</span><span class="sxs-lookup"><span data-stu-id="e22e8-176">Add the following code before `Console.ReadLine` to see how objects can be deleted:</span></span>  
  
#### <a name="to-delete-a-row"></a><span data-ttu-id="e22e8-177">Aby usunąć wiersz</span><span class="sxs-lookup"><span data-stu-id="e22e8-177">To delete a row</span></span>  
  
-   <span data-ttu-id="e22e8-178">Dodaj następujący kod po prostu powyżej `Console.ReadLine();`:</span><span class="sxs-lookup"><span data-stu-id="e22e8-178">Add the following code just above `Console.ReadLine();`:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#5)]  
  
## <a name="submitting-changes-to-the-database"></a><span data-ttu-id="e22e8-179">Przesyłanie zmian w bazie danych</span><span class="sxs-lookup"><span data-stu-id="e22e8-179">Submitting Changes to the Database</span></span>  
 <span data-ttu-id="e22e8-180">Ostatni krok wymagany do tworzenia, aktualizowania i usuwania obiektów, jest rzeczywiście przesłać zmiany w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="e22e8-180">The final step required for creating, updating, and deleting objects, is to actually submit the changes to the database.</span></span> <span data-ttu-id="e22e8-181">Bez tego kroku zmiany są tylko lokalne i nie będą widoczne w wynikach zapytania.</span><span class="sxs-lookup"><span data-stu-id="e22e8-181">Without this step, your changes are only local and will not appear in query results.</span></span>  
  
#### <a name="to-submit-changes-to-the-database"></a><span data-ttu-id="e22e8-182">Aby przesłać zmiany w bazie danych</span><span class="sxs-lookup"><span data-stu-id="e22e8-182">To submit changes to the database</span></span>  
  
1.  <span data-ttu-id="e22e8-183">Wstaw poniższy kod nad `Console.ReadLine`:</span><span class="sxs-lookup"><span data-stu-id="e22e8-183">Insert the following code just above `Console.ReadLine`:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#6)]  
  
2.  <span data-ttu-id="e22e8-184">Wstaw następujący kod (po `SubmitChanges`) do wyświetlenia przed i po skutków przesyłanie zmian:</span><span class="sxs-lookup"><span data-stu-id="e22e8-184">Insert the following code (after `SubmitChanges`) to show the before and after effects of submitting the changes:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#7)]  
  
3.  <span data-ttu-id="e22e8-185">Naciśnij klawisz F5, aby debugować rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="e22e8-185">Press F5 to debug the solution.</span></span>  
  
4.  <span data-ttu-id="e22e8-186">Naciśnij klawisz Enter w **konsoli** okno, aby zamknąć aplikację.</span><span class="sxs-lookup"><span data-stu-id="e22e8-186">Press Enter in the **Console** window to close the application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e22e8-187">Po dodaniu nowego klienta, przesyłając zmiany, nie można wykonać tego rozwiązania jest ponownie.</span><span class="sxs-lookup"><span data-stu-id="e22e8-187">After you have added the new customer by submitting the changes, you cannot execute this solution again as is.</span></span> <span data-ttu-id="e22e8-188">Aby wykonać ponownie rozwiązanie, Zmień nazwę klienta i identyfikator klienta, które ma zostać dodana.</span><span class="sxs-lookup"><span data-stu-id="e22e8-188">To execute the solution again, change the name of the customer and customer ID to be added.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e22e8-189">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e22e8-189">See Also</span></span>  
 [<span data-ttu-id="e22e8-190">Nauka przez przewodniki</span><span class="sxs-lookup"><span data-stu-id="e22e8-190">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
