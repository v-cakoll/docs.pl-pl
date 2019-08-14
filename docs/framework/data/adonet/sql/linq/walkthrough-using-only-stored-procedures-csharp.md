---
title: 'Przewodnik: Używanie tylko procedur składowanych (C#)'
ms.date: 03/30/2017
ms.assetid: ecde4bf2-fa4d-4252-b5e4-96a46b9e097d
ms.openlocfilehash: 69419dd5bb49c2e47315d0079df3a7b575ad9afd
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971777"
---
# <a name="walkthrough-using-only-stored-procedures-c"></a><span data-ttu-id="6e85c-102">Przewodnik: Używanie tylko procedur składowanych (C#)</span><span class="sxs-lookup"><span data-stu-id="6e85c-102">Walkthrough: Using Only Stored Procedures (C#)</span></span>

<span data-ttu-id="6e85c-103">Ten Instruktaż zawiera podstawowy kompleksowy [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenariusz uzyskiwania dostępu do danych przez wykonywanie procedur składowanych.</span><span class="sxs-lookup"><span data-stu-id="6e85c-103">This walkthrough provides a basic end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario for accessing data by executing stored procedures only.</span></span> <span data-ttu-id="6e85c-104">Ta metoda jest często używana przez administratorów bazy danych do ograniczania dostępu do magazynu.</span><span class="sxs-lookup"><span data-stu-id="6e85c-104">This approach is often used by database administrators to limit how the datastore is accessed.</span></span>

> [!NOTE]
> <span data-ttu-id="6e85c-105">Można również użyć procedur składowanych w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikacjach, aby przesłonić zachowanie domyślne `Create`, szczególnie w `Delete` przypadku procesów, `Update`i.</span><span class="sxs-lookup"><span data-stu-id="6e85c-105">You can also use stored procedures in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications to override default behavior, especially for `Create`, `Update`, and `Delete` processes.</span></span> <span data-ttu-id="6e85c-106">Aby uzyskać więcej informacji, zobacz [Dostosowywanie operacji wstawiania, aktualizowania i usuwania](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="6e85c-106">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>

<span data-ttu-id="6e85c-107">Na potrzeby tego instruktażu zostaną użyte dwie metody, które zostały zamapowane na procedury składowane w przykładowej bazie danych Northwind: CustOrdersDetail i CustOrderHist.</span><span class="sxs-lookup"><span data-stu-id="6e85c-107">For purposes of this walkthrough, you will use two methods that have been mapped to stored procedures in the Northwind sample database: CustOrdersDetail and CustOrderHist.</span></span> <span data-ttu-id="6e85c-108">Mapowanie odbywa się po uruchomieniu narzędzia wiersza polecenia SqlMetal w celu wygenerowania C# pliku.</span><span class="sxs-lookup"><span data-stu-id="6e85c-108">The mapping occurs when you run the SqlMetal command-line tool to generate a C# file.</span></span> <span data-ttu-id="6e85c-109">Aby uzyskać więcej informacji, zobacz sekcję wymagania wstępne w dalszej części tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="6e85c-109">For more information, see the Prerequisites section later in this walkthrough.</span></span>

<span data-ttu-id="6e85c-110">Ten Instruktaż nie bazuje na Object Relational Designer.</span><span class="sxs-lookup"><span data-stu-id="6e85c-110">This walkthrough does not rely on the Object Relational Designer.</span></span> <span data-ttu-id="6e85c-111">Deweloperzy korzystający z programu Visual Studio mogą również używać projektanta O/R do implementowania funkcjonalności procedury składowanej.</span><span class="sxs-lookup"><span data-stu-id="6e85c-111">Developers using Visual Studio can also use the O/R Designer to implement stored procedure functionality.</span></span> <span data-ttu-id="6e85c-112">Zobacz [narzędzia LINQ to SQL w programie Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span><span class="sxs-lookup"><span data-stu-id="6e85c-112">See [LINQ to SQL Tools in Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span></span>

[!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]

<span data-ttu-id="6e85c-113">Ten Instruktaż został zapisany przy użyciu ustawień C# deweloperskich.</span><span class="sxs-lookup"><span data-stu-id="6e85c-113">This walkthrough was written by using Visual C# Development Settings.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6e85c-114">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="6e85c-114">Prerequisites</span></span>

<span data-ttu-id="6e85c-115">Ten przewodnik wymaga następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="6e85c-115">This walkthrough requires the following:</span></span>

- <span data-ttu-id="6e85c-116">W tym instruktażu do przechowywania plików służy dedykowany folder ("c:\linqtest7").</span><span class="sxs-lookup"><span data-stu-id="6e85c-116">This walkthrough uses a dedicated folder ("c:\linqtest7") to hold files.</span></span> <span data-ttu-id="6e85c-117">Utwórz ten folder przed rozpoczęciem przewodnika.</span><span class="sxs-lookup"><span data-stu-id="6e85c-117">Create this folder before you begin the walkthrough.</span></span>

- <span data-ttu-id="6e85c-118">Przykładowa bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="6e85c-118">The Northwind sample database.</span></span>

     <span data-ttu-id="6e85c-119">Jeśli nie masz tej bazy danych na komputerze deweloperskim, możesz ją pobrać z witryny pobierania firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="6e85c-119">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="6e85c-120">Aby uzyskać instrukcje, zobacz [Pobieranie przykładowych baz danych](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="6e85c-120">For instructions, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span> <span data-ttu-id="6e85c-121">Po pobraniu bazy danych Skopiuj plik northwnd. mdf do folderu c:\linqtest7.</span><span class="sxs-lookup"><span data-stu-id="6e85c-121">After you have downloaded the database, copy the northwnd.mdf file to the c:\linqtest7 folder.</span></span>

- <span data-ttu-id="6e85c-122">Plik C# kodu wygenerowany na podstawie bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="6e85c-122">A C# code file generated from the Northwind database.</span></span>

     <span data-ttu-id="6e85c-123">Ten Instruktaż został zapisany przy użyciu narzędzia SqlMetal z następującym wierszem polecenia:</span><span class="sxs-lookup"><span data-stu-id="6e85c-123">This walkthrough was written by using the SqlMetal tool with the following command line:</span></span>

     <span data-ttu-id="6e85c-124">**SQLMetal/Code: "c:\linqtest7\northwind.cs"/Language: CSharp "c:\linqtest7\northwnd.mdf"/sprocs/Functions/pluralize**</span><span class="sxs-lookup"><span data-stu-id="6e85c-124">**sqlmetal /code:"c:\linqtest7\northwind.cs" /language:csharp "c:\linqtest7\northwnd.mdf" /sprocs /functions /pluralize**</span></span>

     <span data-ttu-id="6e85c-125">Aby uzyskać więcej informacji, zobacz [SQLMetal. exe (Narzędzie generowania kodu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="6e85c-125">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>

## <a name="overview"></a><span data-ttu-id="6e85c-126">Omówienie</span><span class="sxs-lookup"><span data-stu-id="6e85c-126">Overview</span></span>

<span data-ttu-id="6e85c-127">Ten przewodnik składa się z sześciu głównych zadań:</span><span class="sxs-lookup"><span data-stu-id="6e85c-127">This walkthrough consists of six main tasks:</span></span>

- <span data-ttu-id="6e85c-128">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Konfigurowanie rozwiązania w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6e85c-128">Setting up the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>

- <span data-ttu-id="6e85c-129">Dodawanie zestawu System. Data. LINQ do projektu.</span><span class="sxs-lookup"><span data-stu-id="6e85c-129">Adding the System.Data.Linq assembly to the project.</span></span>

- <span data-ttu-id="6e85c-130">Dodawanie pliku kodu bazy danych do projektu.</span><span class="sxs-lookup"><span data-stu-id="6e85c-130">Adding the database code file to the project.</span></span>

- <span data-ttu-id="6e85c-131">Tworzenie połączenia z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="6e85c-131">Creating a connection with the database.</span></span>

- <span data-ttu-id="6e85c-132">Konfigurowanie interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="6e85c-132">Setting up the user interface.</span></span>

- <span data-ttu-id="6e85c-133">Uruchamianie i testowanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6e85c-133">Running and testing the application.</span></span>

## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="6e85c-134">Tworzenie rozwiązania LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="6e85c-134">Creating a LINQ to SQL Solution</span></span>

<span data-ttu-id="6e85c-135">W tym pierwszym zadaniu utworzysz rozwiązanie programu Visual Studio, które zawiera niezbędne odwołania do kompilowania i uruchamiania [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu.</span><span class="sxs-lookup"><span data-stu-id="6e85c-135">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>

### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="6e85c-136">Aby utworzyć rozwiązanie LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="6e85c-136">To create a LINQ to SQL solution</span></span>

1. <span data-ttu-id="6e85c-137">W menu **plik** programu Visual Studio wskaż polecenie **Nowy**, a następnie kliknij pozycję **projekt**.</span><span class="sxs-lookup"><span data-stu-id="6e85c-137">On the Visual Studio **File** menu, point to **New**, and then click **Project**.</span></span>

2. <span data-ttu-id="6e85c-138">W okienku **typy projektów** okna dialogowego **Nowy projekt** kliknij pozycję Wizualizacja. **C#**</span><span class="sxs-lookup"><span data-stu-id="6e85c-138">In the **Project types** pane in the **New Project** dialog box, click **Visual C#**.</span></span>

3. <span data-ttu-id="6e85c-139">W okienku **Szablony** kliknij pozycję **Windows Forms aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="6e85c-139">In the **Templates** pane, click **Windows Forms Application**.</span></span>

4. <span data-ttu-id="6e85c-140">W polu **Nazwa** wpisz **SprocOnlyApp**.</span><span class="sxs-lookup"><span data-stu-id="6e85c-140">In the **Name** box, type **SprocOnlyApp**.</span></span>

5. <span data-ttu-id="6e85c-141">W polu **Lokalizacja** Sprawdź, gdzie mają być przechowywane pliki projektu.</span><span class="sxs-lookup"><span data-stu-id="6e85c-141">In the **Location** box, verify where you want to store your project files.</span></span>

6. <span data-ttu-id="6e85c-142">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="6e85c-142">Click **OK**.</span></span>

     <span data-ttu-id="6e85c-143">Zostanie otwarty Projektant formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="6e85c-143">The Windows Forms Designer opens.</span></span>

## <a name="adding-the-linq-to-sql-assembly-reference"></a><span data-ttu-id="6e85c-144">Dodawanie odwołania do zestawu LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="6e85c-144">Adding the LINQ to SQL Assembly Reference</span></span>

<span data-ttu-id="6e85c-145">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Zestaw nie jest uwzględniony w szablonie standardowej aplikacji Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="6e85c-145">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] assembly is not included in the standard Windows Forms Application template.</span></span> <span data-ttu-id="6e85c-146">Musisz samodzielnie dodać zestaw, jak wyjaśniono w następujących krokach:</span><span class="sxs-lookup"><span data-stu-id="6e85c-146">You will have to add the assembly yourself, as explained in the following steps:</span></span>

### <a name="to-add-systemdatalinqdll"></a><span data-ttu-id="6e85c-147">To add System.Data.Linq.dll</span><span class="sxs-lookup"><span data-stu-id="6e85c-147">To add System.Data.Linq.dll</span></span>

1. <span data-ttu-id="6e85c-148">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **odwołania**, a następnie kliknij pozycję **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="6e85c-148">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>

2. <span data-ttu-id="6e85c-149">W oknie dialogowym **Dodawanie odwołania** kliknij pozycję **.NET**, kliknij zestaw system. Data. LINQ, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="6e85c-149">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>

     <span data-ttu-id="6e85c-150">Zestaw zostanie dodany do projektu.</span><span class="sxs-lookup"><span data-stu-id="6e85c-150">The assembly is added to the project.</span></span>

## <a name="adding-the-northwind-code-file-to-the-project"></a><span data-ttu-id="6e85c-151">Dodawanie pliku kodu Northwind do projektu</span><span class="sxs-lookup"><span data-stu-id="6e85c-151">Adding the Northwind Code File to the Project</span></span>

<span data-ttu-id="6e85c-152">W tym kroku przyjęto założenie, że użyto narzędzia SqlMetal do wygenerowania pliku kodu z przykładowej bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="6e85c-152">This step assumes that you have used the SqlMetal tool to generate a code file from the Northwind sample database.</span></span> <span data-ttu-id="6e85c-153">Aby uzyskać więcej informacji, zobacz sekcję wymagania wstępne we wcześniejszej części tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="6e85c-153">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>

### <a name="to-add-the-northwind-code-file-to-the-project"></a><span data-ttu-id="6e85c-154">Aby dodać plik kodu Northwind do projektu</span><span class="sxs-lookup"><span data-stu-id="6e85c-154">To add the northwind code file to the project</span></span>

1. <span data-ttu-id="6e85c-155">W menu **projekt** kliknij polecenie **Dodaj istniejący element**.</span><span class="sxs-lookup"><span data-stu-id="6e85c-155">On the **Project** menu, click **Add Existing Item**.</span></span>

2. <span data-ttu-id="6e85c-156">W oknie dialogowym **Dodaj istniejący element** przejdź do c:\linqtest7\northwind.cs, a następnie kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="6e85c-156">In the **Add Existing Item** dialog box, move to c:\linqtest7\northwind.cs, and then click **Add**.</span></span>

     <span data-ttu-id="6e85c-157">Plik northwind.cs jest dodawany do projektu.</span><span class="sxs-lookup"><span data-stu-id="6e85c-157">The northwind.cs file is added to the project.</span></span>

## <a name="creating-a-database-connection"></a><span data-ttu-id="6e85c-158">Tworzenie połączenia z bazą danych</span><span class="sxs-lookup"><span data-stu-id="6e85c-158">Creating a Database Connection</span></span>

<span data-ttu-id="6e85c-159">W tym kroku zdefiniujesz połączenie z przykładową bazą danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="6e85c-159">In this step, you define the connection to the Northwind sample database.</span></span> <span data-ttu-id="6e85c-160">W tym instruktażu jako ścieżki jest stosowany "c:\linqtest7\northwnd.mdf".</span><span class="sxs-lookup"><span data-stu-id="6e85c-160">This walkthrough uses "c:\linqtest7\northwnd.mdf" as the path.</span></span>

### <a name="to-create-the-database-connection"></a><span data-ttu-id="6e85c-161">Aby utworzyć połączenie z bazą danych</span><span class="sxs-lookup"><span data-stu-id="6e85c-161">To create the database connection</span></span>

1. <span data-ttu-id="6e85c-162">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **Form1.cs**, a następnie kliknij pozycję **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="6e85c-162">In **Solution Explorer**, right-click **Form1.cs**, and then click **View Code**.</span></span>

2. <span data-ttu-id="6e85c-163">Wpisz następujący kod do `Form1` klasy:</span><span class="sxs-lookup"><span data-stu-id="6e85c-163">Type the following code into the `Form1` class:</span></span>

     [!code-csharp[DLinqWalk4CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#1)]

## <a name="setting-up-the-user-interface"></a><span data-ttu-id="6e85c-164">Konfigurowanie interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="6e85c-164">Setting up the User Interface</span></span>

<span data-ttu-id="6e85c-165">To zadanie służy do konfigurowania interfejsu, dzięki czemu użytkownicy mogą wykonywać procedury składowane w celu uzyskania dostępu do danych w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="6e85c-165">In this task you set up an interface so that users can execute stored procedures to access data in the database.</span></span> <span data-ttu-id="6e85c-166">W aplikacjach opracowywanych przy użyciu tego przewodnika użytkownicy mogą uzyskać dostęp do danych w bazie danych tylko przy użyciu procedur przechowywanych osadzonych w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6e85c-166">In the applications that you are developing with this walkthrough, users can access data in the database only by using the stored procedures embedded in the application.</span></span>

### <a name="to-set-up-the-user-interface"></a><span data-ttu-id="6e85c-167">Aby skonfigurować interfejs użytkownika</span><span class="sxs-lookup"><span data-stu-id="6e85c-167">To set up the user interface</span></span>

1. <span data-ttu-id="6e85c-168">Wróć do Projektant formularzy systemu Windows (**Form1. cs [Design]** ).</span><span class="sxs-lookup"><span data-stu-id="6e85c-168">Return to the Windows Forms Designer (**Form1.cs[Design]**).</span></span>

2. <span data-ttu-id="6e85c-169">W menu **Widok** kliknij pozycję **Przybornik**.</span><span class="sxs-lookup"><span data-stu-id="6e85c-169">On the **View** menu, click **Toolbox**.</span></span>

     <span data-ttu-id="6e85c-170">Zostanie otwarty Przybornik.</span><span class="sxs-lookup"><span data-stu-id="6e85c-170">The toolbox opens.</span></span>

    > [!NOTE]
    > <span data-ttu-id="6e85c-171">Kliknij przycisk **Autoukrywanie** pinezki, aby zachować Przybornik otwarty podczas wykonywania pozostałych kroków w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="6e85c-171">Click the **AutoHide** pushpin to keep the toolbox open while you perform the remaining steps in this section.</span></span>

3. <span data-ttu-id="6e85c-172">Przeciągnij dwa przyciski, dwa pola tekstowe i dwie etykiety z przybornika na **formularz Form1**.</span><span class="sxs-lookup"><span data-stu-id="6e85c-172">Drag two buttons, two text boxes, and two labels from the toolbox onto **Form1**.</span></span>

     <span data-ttu-id="6e85c-173">Rozmieść formanty jako towarzyszącą ilustrację.</span><span class="sxs-lookup"><span data-stu-id="6e85c-173">Arrange the controls as in the accompanying illustration.</span></span> <span data-ttu-id="6e85c-174">Rozwiń **formularz Form1** , aby umożliwić łatwe dopasowanie formantów.</span><span class="sxs-lookup"><span data-stu-id="6e85c-174">Expand **Form1** so that the controls fit easily.</span></span>

4. <span data-ttu-id="6e85c-175">Kliknij prawym przyciskiem myszy pozycję **Label1**, a następnie kliknij pozycję **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="6e85c-175">Right-click **label1**, and then click **Properties**.</span></span>

5. <span data-ttu-id="6e85c-176">Zmień właściwość **Text** z **Label1** , aby **wprowadzić IDZamówienia:** .</span><span class="sxs-lookup"><span data-stu-id="6e85c-176">Change the **Text** property from **label1** to **Enter OrderID:**.</span></span>

6. <span data-ttu-id="6e85c-177">W ten sam sposób dla **etykiety 2**Zmień właściwość **Text** z **etykiety 2** , aby **wprowadzić CustomerID:** .</span><span class="sxs-lookup"><span data-stu-id="6e85c-177">In the same way for **label2**, change the **Text** property from **label2** to **Enter CustomerID:**.</span></span>

7. <span data-ttu-id="6e85c-178">W ten sam sposób Zmień właściwość **Text** dla **Button1** na **Order**details.</span><span class="sxs-lookup"><span data-stu-id="6e85c-178">In the same way, change the **Text** property for **button1** to **Order Details**.</span></span>

8. <span data-ttu-id="6e85c-179">Zmień właściwość **Text** dla **Button2** na **historię kolejności**.</span><span class="sxs-lookup"><span data-stu-id="6e85c-179">Change the **Text** property for **button2** to **Order History**.</span></span>

     <span data-ttu-id="6e85c-180">Rozszerz kontrolki przycisku, aby cały tekst był widoczny.</span><span class="sxs-lookup"><span data-stu-id="6e85c-180">Widen the button controls so that all the text is visible.</span></span>

### <a name="to-handle-button-clicks"></a><span data-ttu-id="6e85c-181">Aby obsłużyć kliknięcia przycisku</span><span class="sxs-lookup"><span data-stu-id="6e85c-181">To handle button clicks</span></span>

1. <span data-ttu-id="6e85c-182">Kliknij dwukrotnie pozycję **szczegóły zamówienia** na **formularzu Form1** , aby otworzyć program obsługi zdarzeń Button1 w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="6e85c-182">Double-click **Order Details** on **Form1** to open the button1 event handler in the code editor.</span></span>

2. <span data-ttu-id="6e85c-183">Wpisz następujący kod do `button1` procedury obsługi:</span><span class="sxs-lookup"><span data-stu-id="6e85c-183">Type the following code into the `button1` handler:</span></span>

     [!code-csharp[DLinqWalk4CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#2)]

3. <span data-ttu-id="6e85c-184">Teraz kliknij dwukrotnie pozycję **Button2** na **formularzu Form1** , `button2` aby otworzyć procedurę obsługi</span><span class="sxs-lookup"><span data-stu-id="6e85c-184">Now double-click **button2** on **Form1** to open the `button2` handler</span></span>

4. <span data-ttu-id="6e85c-185">Wpisz następujący kod do `button2` procedury obsługi:</span><span class="sxs-lookup"><span data-stu-id="6e85c-185">Type the following code into the `button2` handler:</span></span>

     [!code-csharp[DLinqWalk4CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#3)]

## <a name="testing-the-application"></a><span data-ttu-id="6e85c-186">Testowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="6e85c-186">Testing the Application</span></span>

<span data-ttu-id="6e85c-187">Teraz czas na przetestowanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6e85c-187">Now it is time to test your application.</span></span> <span data-ttu-id="6e85c-188">Należy pamiętać, że kontakt z magazynem danych jest ograniczony do wszelkich akcji, które mogą wykonać dwie procedury składowane.</span><span class="sxs-lookup"><span data-stu-id="6e85c-188">Note that your contact with the datastore is limited to whatever actions the two stored procedures can take.</span></span> <span data-ttu-id="6e85c-189">Te akcje mają na celu zwrócenie produktów uwzględnionych w dowolnym przypisanym identyfikatorze IDZamówienia lub zwrócenie historii produktów zamówionych dla dowolnego elementu IDKlienta, który wprowadzasz.</span><span class="sxs-lookup"><span data-stu-id="6e85c-189">Those actions are to return the products included for any orderID you enter, or to return a history of products ordered for any CustomerID you enter.</span></span>

### <a name="to-test-the-application"></a><span data-ttu-id="6e85c-190">Aby przetestować aplikację</span><span class="sxs-lookup"><span data-stu-id="6e85c-190">To test the application</span></span>

1. <span data-ttu-id="6e85c-191">Naciśnij klawisz F5, aby rozpocząć debugowanie.</span><span class="sxs-lookup"><span data-stu-id="6e85c-191">Press F5 to start debugging.</span></span>

     <span data-ttu-id="6e85c-192">Zostanie wyświetlony formularz Form1.</span><span class="sxs-lookup"><span data-stu-id="6e85c-192">Form1 appears.</span></span>

2. <span data-ttu-id="6e85c-193">W polu **Wprowadź identyfikator zamówienia** wpisz `10249`, a następnie kliknij pozycję **szczegóły zamówienia**.</span><span class="sxs-lookup"><span data-stu-id="6e85c-193">In the **Enter OrderID** box, type `10249`, and then click **Order Details**.</span></span>

     <span data-ttu-id="6e85c-194">Okno komunikatu zawiera listę produktów uwzględnionych w kolejności 10249.</span><span class="sxs-lookup"><span data-stu-id="6e85c-194">A message box lists the products included in order 10249.</span></span>

     <span data-ttu-id="6e85c-195">Kliknij przycisk **OK** , aby zamknąć okno komunikatu.</span><span class="sxs-lookup"><span data-stu-id="6e85c-195">Click **OK** to close the message box.</span></span>

3. <span data-ttu-id="6e85c-196">W polu **wprowadź wartość IDKlienta** wpisz `ALFKI`, a następnie kliknij pozycję **historia kolejności**.</span><span class="sxs-lookup"><span data-stu-id="6e85c-196">In the **Enter CustomerID** box, type `ALFKI`, and then click **Order History**.</span></span>

     <span data-ttu-id="6e85c-197">Zostanie wyświetlone okno komunikatu z listą historii zamówień dla klienta ALFKI.</span><span class="sxs-lookup"><span data-stu-id="6e85c-197">A message box appears that lists the order history for customer ALFKI.</span></span>

     <span data-ttu-id="6e85c-198">Kliknij przycisk **OK** , aby zamknąć okno komunikatu.</span><span class="sxs-lookup"><span data-stu-id="6e85c-198">Click **OK** to close the message box.</span></span>

4. <span data-ttu-id="6e85c-199">W polu **Wprowadź identyfikator zamówienia** wpisz `123`, a następnie kliknij pozycję **szczegóły zamówienia**.</span><span class="sxs-lookup"><span data-stu-id="6e85c-199">In the **Enter OrderID** box, type `123`, and then click **Order Details**.</span></span>

     <span data-ttu-id="6e85c-200">Zostanie wyświetlone okno komunikatu z napisem "Brak wyników".</span><span class="sxs-lookup"><span data-stu-id="6e85c-200">A message box appears that displays "No results."</span></span>

     <span data-ttu-id="6e85c-201">Kliknij przycisk **OK** , aby zamknąć okno komunikatu.</span><span class="sxs-lookup"><span data-stu-id="6e85c-201">Click **OK** to close the message box.</span></span>

5. <span data-ttu-id="6e85c-202">W menu **debugowanie** kliknij **Zatrzymaj debugowanie**.</span><span class="sxs-lookup"><span data-stu-id="6e85c-202">On the **Debug** menu, click **Stop debugging**.</span></span>

     <span data-ttu-id="6e85c-203">Sesja debugowania zostanie zamknięta.</span><span class="sxs-lookup"><span data-stu-id="6e85c-203">The debug session closes.</span></span>

6. <span data-ttu-id="6e85c-204">Jeśli zakończysz eksperymentowanie, możesz kliknąć przycisk **Zamknij projekt** w menu **plik** i zapisać projekt po wyświetleniu monitu.</span><span class="sxs-lookup"><span data-stu-id="6e85c-204">If you have finished experimenting, you can click **Close Project** on the **File** menu, and save your project when you are prompted.</span></span>

## <a name="next-steps"></a><span data-ttu-id="6e85c-205">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="6e85c-205">Next Steps</span></span>

<span data-ttu-id="6e85c-206">Możesz udoskonalić ten projekt, wprowadzając pewne zmiany.</span><span class="sxs-lookup"><span data-stu-id="6e85c-206">You can enhance this project by making some changes.</span></span> <span data-ttu-id="6e85c-207">Na przykład można wyświetlić listę dostępnych procedur składowanych w polu listy i wybrać procedury, które należy wykonać.</span><span class="sxs-lookup"><span data-stu-id="6e85c-207">For example, you could list available stored procedures in a list box and have the user select which procedures to execute.</span></span> <span data-ttu-id="6e85c-208">Możesz również przesyłać strumieniowo dane wyjściowe raportów do pliku tekstowego.</span><span class="sxs-lookup"><span data-stu-id="6e85c-208">You could also stream the output of the reports to a text file.</span></span>

## <a name="see-also"></a><span data-ttu-id="6e85c-209">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6e85c-209">See also</span></span>

- [<span data-ttu-id="6e85c-210">Nauka przez przewodniki</span><span class="sxs-lookup"><span data-stu-id="6e85c-210">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
- [<span data-ttu-id="6e85c-211">Procedury składowane</span><span class="sxs-lookup"><span data-stu-id="6e85c-211">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
