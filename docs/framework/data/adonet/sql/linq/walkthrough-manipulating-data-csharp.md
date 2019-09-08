---
title: 'Przewodnik: Manipulowanie danymi (C#)'
ms.date: 03/30/2017
ms.assetid: 24adfbe0-0ad6-449f-997d-8808e0770d2e
ms.openlocfilehash: 8941ac30a67406346e5448ca5af4af8512d168a8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781006"
---
# <a name="walkthrough-manipulating-data-c"></a><span data-ttu-id="8a1b5-102">Przewodnik: Manipulowanie danymi (C#)</span><span class="sxs-lookup"><span data-stu-id="8a1b5-102">Walkthrough: Manipulating Data (C#)</span></span>
<span data-ttu-id="8a1b5-103">Ten Instruktaż zawiera podstawowy kompleksowy [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenariusz służący do dodawania, modyfikowania i usuwania danych w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-103">This walkthrough provides a fundamental end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario for adding, modifying, and deleting data in a database.</span></span> <span data-ttu-id="8a1b5-104">Zostanie użyta kopia przykładowej bazy danych Northwind, aby dodać klienta, zmienić nazwę klienta i usunąć zamówienie.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-104">You will use a copy of the sample Northwind database to add a customer, change the name of a customer, and delete an order.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="8a1b5-105">Ten Instruktaż został zapisany przy użyciu ustawień C# deweloperskich.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-105">This walkthrough was written by using Visual C# Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8a1b5-106">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="8a1b5-106">Prerequisites</span></span>  
 <span data-ttu-id="8a1b5-107">Ten przewodnik wymaga następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="8a1b5-107">This walkthrough requires the following:</span></span>  
  
- <span data-ttu-id="8a1b5-108">W tym instruktażu do przechowywania plików służy dedykowany folder ("c:\linqtest6").</span><span class="sxs-lookup"><span data-stu-id="8a1b5-108">This walkthrough uses a dedicated folder ("c:\linqtest6") to hold files.</span></span> <span data-ttu-id="8a1b5-109">Utwórz ten folder przed rozpoczęciem przewodnika.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-109">Create this folder before you begin the walkthrough.</span></span>  
  
- <span data-ttu-id="8a1b5-110">Przykładowa bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-110">The Northwind sample database.</span></span>  
  
     <span data-ttu-id="8a1b5-111">Jeśli nie masz tej bazy danych na komputerze deweloperskim, możesz ją pobrać z witryny pobierania firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-111">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="8a1b5-112">Aby uzyskać instrukcje, zobacz [Pobieranie przykładowych baz danych](downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="8a1b5-112">For instructions, see [Downloading Sample Databases](downloading-sample-databases.md).</span></span> <span data-ttu-id="8a1b5-113">Po pobraniu bazy danych Skopiuj plik northwnd. mdf do folderu c:\linqtest6.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-113">After you have downloaded the database, copy the northwnd.mdf file to the c:\linqtest6 folder.</span></span>  
  
- <span data-ttu-id="8a1b5-114">Plik C# kodu wygenerowany na podstawie bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-114">A C# code file generated from the Northwind database.</span></span>  
  
     <span data-ttu-id="8a1b5-115">Ten plik można wygenerować przy użyciu Object Relational Designer lub narzędzia SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-115">You can generate this file by using either the Object Relational Designer or the SQLMetal tool.</span></span> <span data-ttu-id="8a1b5-116">Ten Instruktaż został zapisany przy użyciu narzędzia SQLMetal z następującym wierszem polecenia:</span><span class="sxs-lookup"><span data-stu-id="8a1b5-116">This walkthrough was written by using the SQLMetal tool with the following command line:</span></span>  
  
     <span data-ttu-id="8a1b5-117">**SQLMetal/Code: "c:\linqtest6\northwind.cs"/Language: CSharp "C:\linqtest6\northwnd.mdf"/pluralize**</span><span class="sxs-lookup"><span data-stu-id="8a1b5-117">**sqlmetal /code:"c:\linqtest6\northwind.cs" /language:csharp "C:\linqtest6\northwnd.mdf" /pluralize**</span></span>  
  
     <span data-ttu-id="8a1b5-118">Aby uzyskać więcej informacji, zobacz [SQLMetal. exe (Narzędzie generowania kodu)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="8a1b5-118">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="8a1b5-119">Omówienie</span><span class="sxs-lookup"><span data-stu-id="8a1b5-119">Overview</span></span>  
 <span data-ttu-id="8a1b5-120">Ten przewodnik składa się z sześciu głównych zadań:</span><span class="sxs-lookup"><span data-stu-id="8a1b5-120">This walkthrough consists of six main tasks:</span></span>  
  
- <span data-ttu-id="8a1b5-121">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Tworzenie rozwiązania w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-121">Creating the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>  
  
- <span data-ttu-id="8a1b5-122">Dodawanie pliku kodu bazy danych do projektu.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-122">Adding the database code file to the project.</span></span>  
  
- <span data-ttu-id="8a1b5-123">Tworzenie nowego obiektu klienta.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-123">Creating a new customer object.</span></span>  
  
- <span data-ttu-id="8a1b5-124">Modyfikowanie nazwy kontaktu klienta.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-124">Modifying the contact name of a customer.</span></span>  
  
- <span data-ttu-id="8a1b5-125">Usuwanie zamówienia.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-125">Deleting an order.</span></span>  
  
- <span data-ttu-id="8a1b5-126">Przesyłanie tych zmian do bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-126">Submitting these changes to the Northwind database.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="8a1b5-127">Tworzenie rozwiązania LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="8a1b5-127">Creating a LINQ to SQL Solution</span></span>  
 <span data-ttu-id="8a1b5-128">W tym pierwszym zadaniu utworzysz rozwiązanie programu Visual Studio, które zawiera niezbędne odwołania do kompilowania i uruchamiania [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-128">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="8a1b5-129">Aby utworzyć rozwiązanie LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="8a1b5-129">To create a LINQ to SQL solution</span></span>  
  
1. <span data-ttu-id="8a1b5-130">W menu **plik** programu Visual Studio wskaż polecenie **Nowy**, a następnie kliknij pozycję **projekt**.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-130">On the Visual Studio **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2. <span data-ttu-id="8a1b5-131">W okienku **typy projektów** okna dialogowego **Nowy projekt** kliknij pozycję **Wizualizacja C#** .</span><span class="sxs-lookup"><span data-stu-id="8a1b5-131">In the **Project types** pane in the **New Project** dialog box, click **Visual C#**.</span></span>  
  
3. <span data-ttu-id="8a1b5-132">W okienku **Szablony** kliknij pozycję **Aplikacja konsolowa**.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-132">In the **Templates** pane, click **Console Application**.</span></span>  
  
4. <span data-ttu-id="8a1b5-133">W polu **Nazwa** wpisz **LinqDataManipulationApp**.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-133">In the **Name** box, type **LinqDataManipulationApp**.</span></span>  
  
5. <span data-ttu-id="8a1b5-134">W polu **Lokalizacja** Sprawdź, gdzie mają być przechowywane pliki projektu.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-134">In the **Location** box, verify where you want to store your project files.</span></span>  
  
6. <span data-ttu-id="8a1b5-135">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-135">Click **OK**.</span></span>  
  
## <a name="adding-linq-references-and-directives"></a><span data-ttu-id="8a1b5-136">Dodawanie odwołań i dyrektyw LINQ</span><span class="sxs-lookup"><span data-stu-id="8a1b5-136">Adding LINQ References and Directives</span></span>  
 <span data-ttu-id="8a1b5-137">W tym instruktażu są używane zestawy, które mogą nie być instalowane domyślnie w projekcie.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-137">This walkthrough uses assemblies that might not be installed by default in your project.</span></span> <span data-ttu-id="8a1b5-138">Jeśli element System. Data. LINQ nie jest wymieniony jako odwołanie w projekcie, Dodaj go, jak wyjaśniono w następujących krokach:</span><span class="sxs-lookup"><span data-stu-id="8a1b5-138">If System.Data.Linq is not listed as a reference in your project, add it, as explained in the following steps:</span></span>  
  
#### <a name="to-add-systemdatalinq"></a><span data-ttu-id="8a1b5-139">To add System.Data.Linq</span><span class="sxs-lookup"><span data-stu-id="8a1b5-139">To add System.Data.Linq</span></span>  
  
1. <span data-ttu-id="8a1b5-140">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **odwołania**, a następnie kliknij pozycję **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-140">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
2. <span data-ttu-id="8a1b5-141">W oknie dialogowym **Dodawanie odwołania** kliknij pozycję **.NET**, kliknij zestaw system. Data. LINQ, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-141">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="8a1b5-142">Zestaw zostanie dodany do projektu.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-142">The assembly is added to the project.</span></span>  
  
3. <span data-ttu-id="8a1b5-143">Dodaj następujące dyrektywy w górnej części Program.cs:</span><span class="sxs-lookup"><span data-stu-id="8a1b5-143">Add the following directives at the top of Program.cs:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#1)]  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a><span data-ttu-id="8a1b5-144">Dodawanie pliku kodu Northwind do projektu</span><span class="sxs-lookup"><span data-stu-id="8a1b5-144">Adding the Northwind Code File to the Project</span></span>  
 <span data-ttu-id="8a1b5-145">W tych krokach przyjęto założenie, że użyto narzędzia SQLMetal do wygenerowania pliku kodu z przykładowej bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-145">These steps assume that you have used the SQLMetal tool to generate a code file from the Northwind sample database.</span></span> <span data-ttu-id="8a1b5-146">Aby uzyskać więcej informacji, zobacz sekcję wymagania wstępne we wcześniejszej części tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-146">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a><span data-ttu-id="8a1b5-147">Aby dodać plik kodu Northwind do projektu</span><span class="sxs-lookup"><span data-stu-id="8a1b5-147">To add the northwind code file to the project</span></span>  
  
1. <span data-ttu-id="8a1b5-148">W menu **projekt** kliknij polecenie **Dodaj istniejący element**.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-148">On the **Project** menu, click **Add Existing Item**.</span></span>  
  
2. <span data-ttu-id="8a1b5-149">W oknie dialogowym **Dodaj istniejący element** przejdź do c:\linqtest6\northwind.cs, a następnie kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-149">In the **Add Existing Item** dialog box, navigate to c:\linqtest6\northwind.cs, and then click **Add**.</span></span>  
  
     <span data-ttu-id="8a1b5-150">Plik northwind.cs jest dodawany do projektu.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-150">The northwind.cs file is added to the project.</span></span>  
  
## <a name="setting-up-the-database-connection"></a><span data-ttu-id="8a1b5-151">Konfigurowanie połączenia z bazą danych</span><span class="sxs-lookup"><span data-stu-id="8a1b5-151">Setting Up the Database Connection</span></span>  
 <span data-ttu-id="8a1b5-152">Najpierw Przetestuj połączenie z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-152">First, test your connection to the database.</span></span> <span data-ttu-id="8a1b5-153">Należy pamiętać, że w szczególności baza danych, northwnd, nie ma znaku.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-153">Note especially that the database, Northwnd, has no i character.</span></span> <span data-ttu-id="8a1b5-154">W przypadku wygenerowania błędów w następnych krokach przejrzyj plik northwind.cs, aby określić, w jaki sposób jest sprawdzana pisownia klasy częściowej Northwind.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-154">If you generate errors in the next steps, review the northwind.cs file to determine how the Northwind partial class is spelled.</span></span>  
  
#### <a name="to-set-up-and-test-the-database-connection"></a><span data-ttu-id="8a1b5-155">Aby skonfigurować i przetestować połączenie z bazą danych</span><span class="sxs-lookup"><span data-stu-id="8a1b5-155">To set up and test the database connection</span></span>  
  
1. <span data-ttu-id="8a1b5-156">Wpisz lub wklej następujący kod do `Main` metody w klasie program:</span><span class="sxs-lookup"><span data-stu-id="8a1b5-156">Type or paste the following code into the `Main` method in the Program class:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#2)]  
  
2. <span data-ttu-id="8a1b5-157">Naciśnij klawisz F5, aby przetestować aplikację w tym momencie.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-157">Press F5 to test the application at this point.</span></span>  
  
     <span data-ttu-id="8a1b5-158">Zostanie otwarte okno **konsoli** .</span><span class="sxs-lookup"><span data-stu-id="8a1b5-158">A **Console** window opens.</span></span>  
  
     <span data-ttu-id="8a1b5-159">Możesz zamknąć aplikację, naciskając klawisz ENTER w oknie **konsoli** lub klikając przycisk **Zatrzymaj debugowanie** w menu **debugowanie** programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-159">You can close the application by pressing Enter in the **Console** window, or by clicking **Stop Debugging** on the Visual Studio **Debug** menu.</span></span>  
  
## <a name="creating-a-new-entity"></a><span data-ttu-id="8a1b5-160">Tworzenie nowej jednostki</span><span class="sxs-lookup"><span data-stu-id="8a1b5-160">Creating a New Entity</span></span>  
 <span data-ttu-id="8a1b5-161">Tworzenie nowej jednostki jest proste.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-161">Creating a new entity is straightforward.</span></span> <span data-ttu-id="8a1b5-162">Możesz tworzyć obiekty (na przykład `Customer`) za `new` pomocą słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-162">You can create objects (such as `Customer`) by using the `new` keyword.</span></span>  
  
 <span data-ttu-id="8a1b5-163">W tym i w poniższych sekcjach wprowadzasz zmiany tylko do lokalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-163">In this and the following sections, you are making changes only to the local cache.</span></span> <span data-ttu-id="8a1b5-164">Żadne zmiany nie są wysyłane do bazy danych do momentu wywołania <xref:System.Data.Linq.DataContext.SubmitChanges%2A> końca tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-164">No changes are sent to the database until you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> toward the end of this walkthrough.</span></span>  
  
#### <a name="to-add-a-new-customer-entity-object"></a><span data-ttu-id="8a1b5-165">Aby dodać nowy obiekt jednostki klienta</span><span class="sxs-lookup"><span data-stu-id="8a1b5-165">To add a new Customer entity object</span></span>  
  
1. <span data-ttu-id="8a1b5-166">Utwórz nowy `Customer` , dodając następujący kod przed użyciem `Console.ReadLine();` `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="8a1b5-166">Create a new `Customer` by adding the following code before `Console.ReadLine();` in the `Main` method:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#3)]  
  
2. <span data-ttu-id="8a1b5-167">Naciśnij klawisz F5, aby debugować rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-167">Press F5 to debug the solution.</span></span>  
  
3. <span data-ttu-id="8a1b5-168">Naciśnij klawisz ENTER w oknie **konsoli** , aby zatrzymać debugowanie i kontynuować przewodnik.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-168">Press Enter in the **Console** window to stop debugging and continue the walkthrough.</span></span>  
  
## <a name="updating-an-entity"></a><span data-ttu-id="8a1b5-169">Aktualizowanie jednostki</span><span class="sxs-lookup"><span data-stu-id="8a1b5-169">Updating an Entity</span></span>  
 <span data-ttu-id="8a1b5-170">W poniższych krokach zostanie pobrany `Customer` obiekt i zostanie zmodyfikowana jedna z jego właściwości.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-170">In the following steps, you will retrieve a `Customer` object and modify one of its properties.</span></span>  
  
#### <a name="to-change-the-name-of-a-customer"></a><span data-ttu-id="8a1b5-171">Aby zmienić nazwę klienta</span><span class="sxs-lookup"><span data-stu-id="8a1b5-171">To change the name of a Customer</span></span>  
  
- <span data-ttu-id="8a1b5-172">Dodaj następujący kod powyżej `Console.ReadLine();`:</span><span class="sxs-lookup"><span data-stu-id="8a1b5-172">Add the following code above `Console.ReadLine();`:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#4)]  
  
## <a name="deleting-an-entity"></a><span data-ttu-id="8a1b5-173">Usuwanie jednostki</span><span class="sxs-lookup"><span data-stu-id="8a1b5-173">Deleting an Entity</span></span>  
 <span data-ttu-id="8a1b5-174">Przy użyciu tego samego obiektu klienta można usunąć pierwszą kolejność.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-174">Using the same customer object, you can delete the first order.</span></span>  
  
 <span data-ttu-id="8a1b5-175">Poniższy kod ilustruje sposób tworzenia relacji między wierszami i sposobu usuwania wiersza z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-175">The following code demonstrates how to sever relationships between rows, and how to delete a row from the database.</span></span> <span data-ttu-id="8a1b5-176">Dodaj poniższy kod przed `Console.ReadLine` , aby zobaczyć, jak można usunąć obiekty:</span><span class="sxs-lookup"><span data-stu-id="8a1b5-176">Add the following code before `Console.ReadLine` to see how objects can be deleted:</span></span>  
  
#### <a name="to-delete-a-row"></a><span data-ttu-id="8a1b5-177">Aby usunąć wiersz</span><span class="sxs-lookup"><span data-stu-id="8a1b5-177">To delete a row</span></span>  
  
- <span data-ttu-id="8a1b5-178">Dodaj poniższy kod bezpośrednio powyżej `Console.ReadLine();`:</span><span class="sxs-lookup"><span data-stu-id="8a1b5-178">Add the following code just above `Console.ReadLine();`:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#5)]  
  
## <a name="submitting-changes-to-the-database"></a><span data-ttu-id="8a1b5-179">Przesyłanie zmian do bazy danych</span><span class="sxs-lookup"><span data-stu-id="8a1b5-179">Submitting Changes to the Database</span></span>  
 <span data-ttu-id="8a1b5-180">Ostatnim krokiem wymaganym do tworzenia, aktualizowania i usuwania obiektów jest faktyczne przesłanie zmian do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-180">The final step required for creating, updating, and deleting objects, is to actually submit the changes to the database.</span></span> <span data-ttu-id="8a1b5-181">Bez tego kroku zmiany są tylko lokalne i nie będą wyświetlane w wynikach zapytania.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-181">Without this step, your changes are only local and will not appear in query results.</span></span>  
  
#### <a name="to-submit-changes-to-the-database"></a><span data-ttu-id="8a1b5-182">Aby przesłać zmiany do bazy danych</span><span class="sxs-lookup"><span data-stu-id="8a1b5-182">To submit changes to the database</span></span>  
  
1. <span data-ttu-id="8a1b5-183">Wstaw poniższy kod powyżej `Console.ReadLine`:</span><span class="sxs-lookup"><span data-stu-id="8a1b5-183">Insert the following code just above `Console.ReadLine`:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#6)]  
  
2. <span data-ttu-id="8a1b5-184">Wstaw poniższy kod (po `SubmitChanges`), aby wyświetlić efekty przesłania zmian:</span><span class="sxs-lookup"><span data-stu-id="8a1b5-184">Insert the following code (after `SubmitChanges`) to show the before and after effects of submitting the changes:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#7)]  
  
3. <span data-ttu-id="8a1b5-185">Naciśnij klawisz F5, aby debugować rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-185">Press F5 to debug the solution.</span></span>  
  
4. <span data-ttu-id="8a1b5-186">Naciśnij klawisz ENTER w oknie **konsoli** , aby zamknąć aplikację.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-186">Press Enter in the **Console** window to close the application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8a1b5-187">Po dodaniu nowego klienta przez przesłanie zmian nie można wykonać tego rozwiązania ponownie, ponieważ jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-187">After you have added the new customer by submitting the changes, you cannot execute this solution again as is.</span></span> <span data-ttu-id="8a1b5-188">Aby ponownie wykonać rozwiązanie, Zmień nazwę klienta i identyfikator klienta, który ma zostać dodany.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-188">To execute the solution again, change the name of the customer and customer ID to be added.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a1b5-189">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8a1b5-189">See also</span></span>

- [<span data-ttu-id="8a1b5-190">Nauka przez przewodniki</span><span class="sxs-lookup"><span data-stu-id="8a1b5-190">Learning by Walkthroughs</span></span>](learning-by-walkthroughs.md)
