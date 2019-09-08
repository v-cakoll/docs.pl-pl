---
title: 'Przewodnik: Używanie tylko procedur składowanych (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: 5a736a30-ba66-4adb-b87c-57d19476e862
ms.openlocfilehash: a1994d100c4d18d5fa3642e27d0dcb8823800549
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780969"
---
# <a name="walkthrough-using-only-stored-procedures-visual-basic"></a><span data-ttu-id="b8286-102">Przewodnik: Używanie tylko procedur składowanych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b8286-102">Walkthrough: Using Only Stored Procedures (Visual Basic)</span></span>
<span data-ttu-id="b8286-103">Ten Instruktaż przedstawia podstawowy [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenariusz kompleksowego dostępu do danych za pomocą procedur składowanych.</span><span class="sxs-lookup"><span data-stu-id="b8286-103">This walkthrough provides a basic end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario for accessing data by using stored procedures only.</span></span> <span data-ttu-id="b8286-104">Ta metoda jest często używana przez administratorów bazy danych do ograniczania dostępu do magazynu.</span><span class="sxs-lookup"><span data-stu-id="b8286-104">This approach is often used by database administrators to limit how the datastore is accessed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b8286-105">Można również użyć procedur składowanych w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikacjach, aby przesłonić zachowanie domyślne `Create`, szczególnie w `Delete` przypadku procesów, `Update`i.</span><span class="sxs-lookup"><span data-stu-id="b8286-105">You can also use stored procedures in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications to override default behavior, especially for `Create`, `Update`, and `Delete` processes.</span></span> <span data-ttu-id="b8286-106">Aby uzyskać więcej informacji, zobacz [Dostosowywanie operacji wstawiania, aktualizowania i usuwania](customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="b8286-106">For more information, see [Customizing Insert, Update, and Delete Operations](customizing-insert-update-and-delete-operations.md).</span></span>  
  
 <span data-ttu-id="b8286-107">Na potrzeby tego instruktażu zostaną użyte dwie metody, które zostały zamapowane na procedury składowane w przykładowej bazie danych Northwind: CustOrdersDetail i CustOrderHist.</span><span class="sxs-lookup"><span data-stu-id="b8286-107">For purposes of this walkthrough, you will use two methods that have been mapped to stored procedures in the Northwind sample database: CustOrdersDetail and CustOrderHist.</span></span> <span data-ttu-id="b8286-108">Mapowanie odbywa się po uruchomieniu narzędzia wiersza polecenia SqlMetal w celu wygenerowania pliku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b8286-108">The mapping occurs when you run the SqlMetal command-line tool to generate a Visual Basic file.</span></span> <span data-ttu-id="b8286-109">Aby uzyskać więcej informacji, zobacz sekcję wymagania wstępne w dalszej części tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="b8286-109">For more information, see the Prerequisites section later in this walkthrough.</span></span>  
  
 <span data-ttu-id="b8286-110">Ten Instruktaż nie bazuje na Object Relational Designer.</span><span class="sxs-lookup"><span data-stu-id="b8286-110">This walkthrough does not rely on the Object Relational Designer.</span></span> <span data-ttu-id="b8286-111">Deweloperzy korzystający z programu Visual Studio mogą również używać projektanta O/R do implementowania funkcjonalności procedury składowanej.</span><span class="sxs-lookup"><span data-stu-id="b8286-111">Developers using Visual Studio can also use the O/R Designer to implement stored procedure functionality.</span></span> <span data-ttu-id="b8286-112">Zobacz [narzędzia LINQ to SQL w programie Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span><span class="sxs-lookup"><span data-stu-id="b8286-112">See [LINQ to SQL Tools in Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="b8286-113">Ten Instruktaż został zapisany przy użyciu ustawień tworzenia Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b8286-113">This walkthrough was written by using Visual Basic Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b8286-114">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="b8286-114">Prerequisites</span></span>  
 <span data-ttu-id="b8286-115">Ten przewodnik wymaga następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="b8286-115">This walkthrough requires the following:</span></span>  
  
- <span data-ttu-id="b8286-116">W tym instruktażu do przechowywania plików służy dedykowany folder ("c:\linqtest3").</span><span class="sxs-lookup"><span data-stu-id="b8286-116">This walkthrough uses a dedicated folder ("c:\linqtest3") to hold files.</span></span> <span data-ttu-id="b8286-117">Utwórz ten folder przed rozpoczęciem przewodnika.</span><span class="sxs-lookup"><span data-stu-id="b8286-117">Create this folder before you begin the walkthrough.</span></span>  
  
- <span data-ttu-id="b8286-118">Przykładowa bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="b8286-118">The Northwind sample database.</span></span>  
  
     <span data-ttu-id="b8286-119">Jeśli nie masz tej bazy danych na komputerze deweloperskim, możesz ją pobrać z witryny pobierania firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="b8286-119">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="b8286-120">Aby uzyskać instrukcje, zobacz [Pobieranie przykładowych baz danych](downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="b8286-120">For instructions, see [Downloading Sample Databases](downloading-sample-databases.md).</span></span> <span data-ttu-id="b8286-121">Po pobraniu bazy danych Skopiuj plik northwnd. mdf do folderu c:\linqtest3.</span><span class="sxs-lookup"><span data-stu-id="b8286-121">After you have downloaded the database, copy the northwnd.mdf file to the c:\linqtest3 folder.</span></span>  
  
- <span data-ttu-id="b8286-122">Plik kodu Visual Basic wygenerowany na podstawie bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="b8286-122">A Visual Basic code file generated from the Northwind database.</span></span>  
  
     <span data-ttu-id="b8286-123">Ten Instruktaż został zapisany przy użyciu narzędzia SqlMetal z następującym wierszem polecenia:</span><span class="sxs-lookup"><span data-stu-id="b8286-123">This walkthrough was written by using the SqlMetal tool with the following command line:</span></span>  
  
     <span data-ttu-id="b8286-124">**SQLMetal/Code: "c:\linqtest3\northwind.vb"/Language: VB "c:\linqtest3\northwnd.mdf"/sprocs/Functions/pluralize**</span><span class="sxs-lookup"><span data-stu-id="b8286-124">**sqlmetal /code:"c:\linqtest3\northwind.vb" /language:vb "c:\linqtest3\northwnd.mdf" /sprocs /functions /pluralize**</span></span>  
  
     <span data-ttu-id="b8286-125">Aby uzyskać więcej informacji, zobacz [SQLMetal. exe (Narzędzie generowania kodu)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="b8286-125">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="b8286-126">Omówienie</span><span class="sxs-lookup"><span data-stu-id="b8286-126">Overview</span></span>  
 <span data-ttu-id="b8286-127">Ten przewodnik składa się z sześciu głównych zadań:</span><span class="sxs-lookup"><span data-stu-id="b8286-127">This walkthrough consists of six main tasks:</span></span>  
  
- <span data-ttu-id="b8286-128">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Konfigurowanie rozwiązania w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b8286-128">Setting up the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>  
  
- <span data-ttu-id="b8286-129">Dodawanie zestawu System. Data. LINQ do projektu.</span><span class="sxs-lookup"><span data-stu-id="b8286-129">Adding the System.Data.Linq assembly to the project.</span></span>  
  
- <span data-ttu-id="b8286-130">Dodawanie pliku kodu bazy danych do projektu.</span><span class="sxs-lookup"><span data-stu-id="b8286-130">Adding the database code file to the project.</span></span>  
  
- <span data-ttu-id="b8286-131">Tworzenie połączenia z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="b8286-131">Creating a connection to the database.</span></span>  
  
- <span data-ttu-id="b8286-132">Konfigurowanie interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b8286-132">Setting up the user interface.</span></span>  
  
- <span data-ttu-id="b8286-133">Uruchamianie i testowanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b8286-133">Running and testing the application.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="b8286-134">Tworzenie rozwiązania LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="b8286-134">Creating a LINQ to SQL Solution</span></span>  
 <span data-ttu-id="b8286-135">W tym pierwszym zadaniu utworzysz rozwiązanie programu Visual Studio, które zawiera niezbędne odwołania do kompilowania i uruchamiania [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu.</span><span class="sxs-lookup"><span data-stu-id="b8286-135">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="b8286-136">Aby utworzyć rozwiązanie LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="b8286-136">To create a LINQ to SQL solution</span></span>  
  
1. <span data-ttu-id="b8286-137">W menu **plik** programu Visual Studio kliknij pozycję **Nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="b8286-137">On the Visual Studio **File** menu, click **New Project**.</span></span>  
  
2. <span data-ttu-id="b8286-138">W okienku **typy projektów** okna dialogowego **Nowy projekt** rozwiń węzeł **Visual Basic**, a następnie kliknij pozycję **Windows**.</span><span class="sxs-lookup"><span data-stu-id="b8286-138">In the **Project types** pane in the **New Project** dialog box, expand **Visual Basic**, and then click **Windows**.</span></span>  
  
3. <span data-ttu-id="b8286-139">W okienku **Szablony** kliknij pozycję **Windows Forms aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="b8286-139">In the **Templates** pane, click **Windows Forms Application**.</span></span>  
  
4. <span data-ttu-id="b8286-140">W polu **Nazwa** wpisz **SprocOnlyApp**.</span><span class="sxs-lookup"><span data-stu-id="b8286-140">In the **Name** box, type **SprocOnlyApp**.</span></span>  
  
5. <span data-ttu-id="b8286-141">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="b8286-141">Click **OK**.</span></span>  
  
     <span data-ttu-id="b8286-142">Zostanie otwarty Projektant formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="b8286-142">The Windows Forms Designer opens.</span></span>  
  
## <a name="adding-the-linq-to-sql-assembly-reference"></a><span data-ttu-id="b8286-143">Dodawanie odwołania do zestawu LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="b8286-143">Adding the LINQ to SQL Assembly Reference</span></span>  
 <span data-ttu-id="b8286-144">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Zestaw nie jest uwzględniony w szablonie standardowej aplikacji Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="b8286-144">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] assembly is not included in the standard Windows Forms Application template.</span></span> <span data-ttu-id="b8286-145">Musisz samodzielnie dodać zestaw, jak wyjaśniono w następujących krokach:</span><span class="sxs-lookup"><span data-stu-id="b8286-145">You will have to add the assembly yourself, as explained in the following steps:</span></span>  
  
### <a name="to-add-systemdatalinqdll"></a><span data-ttu-id="b8286-146">To add System.Data.Linq.dll</span><span class="sxs-lookup"><span data-stu-id="b8286-146">To add System.Data.Linq.dll</span></span>  
  
1. <span data-ttu-id="b8286-147">W **Eksplorator rozwiązań**kliknij przycisk **Pokaż wszystkie pliki**.</span><span class="sxs-lookup"><span data-stu-id="b8286-147">In **Solution Explorer**, click **Show All Files**.</span></span>  
  
2. <span data-ttu-id="b8286-148">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **odwołania**, a następnie kliknij pozycję **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="b8286-148">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
3. <span data-ttu-id="b8286-149">W oknie dialogowym **Dodawanie odwołania** kliknij pozycję **.NET**, kliknij zestaw system. Data. LINQ, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="b8286-149">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="b8286-150">Zestaw zostanie dodany do projektu.</span><span class="sxs-lookup"><span data-stu-id="b8286-150">The assembly is added to the project.</span></span>  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a><span data-ttu-id="b8286-151">Dodawanie pliku kodu Northwind do projektu</span><span class="sxs-lookup"><span data-stu-id="b8286-151">Adding the Northwind Code File to the Project</span></span>  
 <span data-ttu-id="b8286-152">W tym kroku przyjęto założenie, że użyto narzędzia SqlMetal do wygenerowania pliku kodu z przykładowej bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="b8286-152">This step assumes that you have used the SqlMetal tool to generate a code file from the Northwind sample database.</span></span> <span data-ttu-id="b8286-153">Aby uzyskać więcej informacji, zobacz sekcję wymagania wstępne we wcześniejszej części tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="b8286-153">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
### <a name="to-add-the-northwind-code-file-to-the-project"></a><span data-ttu-id="b8286-154">Aby dodać plik kodu Northwind do projektu</span><span class="sxs-lookup"><span data-stu-id="b8286-154">To add the northwind code file to the project</span></span>  
  
1. <span data-ttu-id="b8286-155">W menu **projekt** kliknij polecenie **Dodaj istniejący element**.</span><span class="sxs-lookup"><span data-stu-id="b8286-155">On the **Project** menu, click **Add Existing Item**.</span></span>  
  
2. <span data-ttu-id="b8286-156">W oknie dialogowym **Dodaj istniejący element** przejdź do c:\linqtest3\northwind.vb, a następnie kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="b8286-156">In the **Add Existing Item** dialog box, move to c:\linqtest3\northwind.vb, and then click **Add**.</span></span>  
  
     <span data-ttu-id="b8286-157">Plik Northwind. vb zostanie dodany do projektu.</span><span class="sxs-lookup"><span data-stu-id="b8286-157">The northwind.vb file is added to the project.</span></span>  
  
## <a name="creating-a-database-connection"></a><span data-ttu-id="b8286-158">Tworzenie połączenia z bazą danych</span><span class="sxs-lookup"><span data-stu-id="b8286-158">Creating a Database Connection</span></span>  
 <span data-ttu-id="b8286-159">W tym kroku zdefiniujesz połączenie z przykładową bazą danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="b8286-159">In this step, you define the connection to the Northwind sample database.</span></span> <span data-ttu-id="b8286-160">W tym instruktażu jako ścieżki jest stosowany "c:\linqtest3\northwnd.mdf".</span><span class="sxs-lookup"><span data-stu-id="b8286-160">This walkthrough uses "c:\linqtest3\northwnd.mdf" as the path.</span></span>  
  
### <a name="to-create-the-database-connection"></a><span data-ttu-id="b8286-161">Aby utworzyć połączenie z bazą danych</span><span class="sxs-lookup"><span data-stu-id="b8286-161">To create the database connection</span></span>  
  
1. <span data-ttu-id="b8286-162">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **Form1. vb**, a następnie kliknij polecenie **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="b8286-162">In **Solution Explorer**, right-click **Form1.vb**, and then click **View Code**.</span></span>  
  
     <span data-ttu-id="b8286-163">`Class Form1`pojawia się w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="b8286-163">`Class Form1` appears in the code editor.</span></span>  
  
2. <span data-ttu-id="b8286-164">Wpisz następujący kod w `Form1` bloku kodu:</span><span class="sxs-lookup"><span data-stu-id="b8286-164">Type the following code into the `Form1` code block:</span></span>  
  
     [!code-vb[DLinqWalk4VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#1)]  
  
## <a name="setting-up-the-user-interface"></a><span data-ttu-id="b8286-165">Konfigurowanie interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="b8286-165">Setting up the User Interface</span></span>  
 <span data-ttu-id="b8286-166">W tym zadaniu utworzysz interfejs, dzięki czemu użytkownicy mogą wykonywać procedury składowane w celu uzyskania dostępu do danych w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="b8286-166">In this task you create an interface so that users can execute stored procedures to access data in the database.</span></span> <span data-ttu-id="b8286-167">W aplikacji opracowywanej przy użyciu tego przewodnika użytkownicy mogą uzyskiwać dostęp do danych w bazie danych tylko przy użyciu procedur przechowywanych osadzonych w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b8286-167">In the application that you are developing with this walkthrough, users can access data in the database only by using the stored procedures embedded in the application.</span></span>  
  
### <a name="to-set-up-the-user-interface"></a><span data-ttu-id="b8286-168">Aby skonfigurować interfejs użytkownika</span><span class="sxs-lookup"><span data-stu-id="b8286-168">To set up the user interface</span></span>  
  
1. <span data-ttu-id="b8286-169">Wróć do Projektant formularzy systemu Windows (**Form1. vb [projekt]** ).</span><span class="sxs-lookup"><span data-stu-id="b8286-169">Return to the Windows Forms Designer (**Form1.vb[Design]**).</span></span>  
  
2. <span data-ttu-id="b8286-170">W menu **Widok** kliknij pozycję **Przybornik**.</span><span class="sxs-lookup"><span data-stu-id="b8286-170">On the **View** menu, click **Toolbox**.</span></span>  
  
     <span data-ttu-id="b8286-171">Zostanie otwarty Przybornik.</span><span class="sxs-lookup"><span data-stu-id="b8286-171">The toolbox opens.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="b8286-172">Kliknij przycisk **Autoukrywanie** pinezki, aby zachować Przybornik otwarty podczas wykonywania pozostałych kroków w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="b8286-172">Click the **AutoHide** pushpin to keep the toolbox open while you perform the remaining steps in this section.</span></span>  
  
3. <span data-ttu-id="b8286-173">Przeciągnij dwa przyciski, dwa pola tekstowe i dwie etykiety z przybornika na **formularz Form1**.</span><span class="sxs-lookup"><span data-stu-id="b8286-173">Drag two buttons, two text boxes, and two labels from the toolbox onto **Form1**.</span></span>  
  
     <span data-ttu-id="b8286-174">Rozmieść formanty jako towarzyszącą ilustrację.</span><span class="sxs-lookup"><span data-stu-id="b8286-174">Arrange the controls as in the accompanying illustration.</span></span> <span data-ttu-id="b8286-175">Rozwiń **formularz Form1** , aby umożliwić łatwe dopasowanie formantów.</span><span class="sxs-lookup"><span data-stu-id="b8286-175">Expand **Form1** so that the controls fit easily.</span></span>  
  
4. <span data-ttu-id="b8286-176">Kliknij prawym przyciskiem myszy pozycję **Label1**, a następnie kliknij pozycję **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="b8286-176">Right-click **Label1**, and then click **Properties**.</span></span>  
  
5. <span data-ttu-id="b8286-177">Zmień właściwość **Text** z **Label1** , aby **wprowadzić IDZamówienia:** .</span><span class="sxs-lookup"><span data-stu-id="b8286-177">Change the **Text** property from **Label1** to **Enter OrderID:**.</span></span>  
  
6. <span data-ttu-id="b8286-178">W ten sam sposób dla **etykiety 2**Zmień właściwość **Text** z **etykiety 2** , aby **wprowadzić CustomerID:** .</span><span class="sxs-lookup"><span data-stu-id="b8286-178">In the same way for **Label2**, change the **Text** property from **Label2** to **Enter CustomerID:**.</span></span>  
  
7. <span data-ttu-id="b8286-179">W ten sam sposób Zmień właściwość **Text** dla **Button1** na **Order Details**.</span><span class="sxs-lookup"><span data-stu-id="b8286-179">In the same way, change the **Text** property for **Button1** to **Order Details**.</span></span>  
  
8. <span data-ttu-id="b8286-180">Zmień właściwość **Text** dla **Button2** na **historię kolejności**.</span><span class="sxs-lookup"><span data-stu-id="b8286-180">Change the **Text** property for **Button2** to **Order History**.</span></span>  
  
     <span data-ttu-id="b8286-181">Rozszerz kontrolki przycisku, aby cały tekst był widoczny.</span><span class="sxs-lookup"><span data-stu-id="b8286-181">Widen the button controls so that all the text is visible.</span></span>  
  
### <a name="to-handle-button-clicks"></a><span data-ttu-id="b8286-182">Aby obsłużyć kliknięcia przycisku</span><span class="sxs-lookup"><span data-stu-id="b8286-182">To handle button clicks</span></span>  
  
1. <span data-ttu-id="b8286-183">Kliknij dwukrotnie pozycję **szczegóły zamówienia** na **formularzu Form1** , `Button1` aby utworzyć program obsługi zdarzeń i otworzyć Edytor kodu.</span><span class="sxs-lookup"><span data-stu-id="b8286-183">Double-click **Order Details** on **Form1** to create the `Button1` event handler and open the code editor.</span></span>  
  
2. <span data-ttu-id="b8286-184">Wpisz następujący kod do `Button1` procedury obsługi:</span><span class="sxs-lookup"><span data-stu-id="b8286-184">Type the following code into the `Button1` handler:</span></span>  
  
     [!code-vb[DLinqWalk4VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#2)]  
  
3. <span data-ttu-id="b8286-185">Teraz kliknij dwukrotnie pozycję **Button2** na formularzu Form1, aby `Button2` utworzyć program obsługi zdarzeń i otworzyć Edytor kodu.</span><span class="sxs-lookup"><span data-stu-id="b8286-185">Now double-click **Button2** on Form1 to create the `Button2` event handler and open the code editor.</span></span>  
  
4. <span data-ttu-id="b8286-186">Wpisz następujący kod do `Button2` procedury obsługi:</span><span class="sxs-lookup"><span data-stu-id="b8286-186">Type the following code into the `Button2` handler:</span></span>  
  
     [!code-vb[DLinqWalk4VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#3)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="b8286-187">Testowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="b8286-187">Testing the Application</span></span>  
 <span data-ttu-id="b8286-188">Teraz czas na przetestowanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b8286-188">Now it is time to test your application.</span></span> <span data-ttu-id="b8286-189">Należy pamiętać, że kontakt z magazynem danych jest ograniczony do wszelkich akcji, które mogą wykonać dwie procedury składowane.</span><span class="sxs-lookup"><span data-stu-id="b8286-189">Note that your contact with the datastore is limited to whatever actions the two stored procedures can take.</span></span> <span data-ttu-id="b8286-190">Te akcje mają na celu zwrócenie produktów uwzględnionych w dowolnym przypisanym identyfikatorze IDZamówienia lub zwrócenie historii produktów zamówionych dla dowolnego elementu IDKlienta, który wprowadzasz.</span><span class="sxs-lookup"><span data-stu-id="b8286-190">Those actions are to return the products included for any orderID you enter, or to return a history of products ordered for any CustomerID you enter.</span></span>  
  
### <a name="to-test-the-application"></a><span data-ttu-id="b8286-191">Aby przetestować aplikację</span><span class="sxs-lookup"><span data-stu-id="b8286-191">To test the application</span></span>  
  
1. <span data-ttu-id="b8286-192">Naciśnij klawisz F5, aby rozpocząć debugowanie.</span><span class="sxs-lookup"><span data-stu-id="b8286-192">Press F5 to start debugging.</span></span>  
  
     <span data-ttu-id="b8286-193">Zostanie wyświetlony formularz Form1.</span><span class="sxs-lookup"><span data-stu-id="b8286-193">Form1 appears.</span></span>  
  
2. <span data-ttu-id="b8286-194">W polu **Wprowadź identyfikator zamówienia** wpisz **10249** , a następnie kliknij pozycję **szczegóły zamówienia**.</span><span class="sxs-lookup"><span data-stu-id="b8286-194">In the **Enter OrderID** box, type **10249** and then click **Order Details**.</span></span>  
  
     <span data-ttu-id="b8286-195">Okno komunikatu zawiera listę produktów uwzględnionych w kolejności 10249.</span><span class="sxs-lookup"><span data-stu-id="b8286-195">A message box lists the products included in order 10249.</span></span>  
  
     <span data-ttu-id="b8286-196">Kliknij przycisk **OK** , aby zamknąć okno komunikatu.</span><span class="sxs-lookup"><span data-stu-id="b8286-196">Click **OK** to close the message box.</span></span>  
  
3. <span data-ttu-id="b8286-197">W polu **wprowadź wartość IDKlienta** wpisz `ALFKI`, a następnie kliknij pozycję **historia kolejności**.</span><span class="sxs-lookup"><span data-stu-id="b8286-197">In the **Enter CustomerID** box, type `ALFKI`, and then click **Order History**.</span></span>  
  
     <span data-ttu-id="b8286-198">Okno komunikatu zawiera listę historii zamówień dla klienta ALFKI.</span><span class="sxs-lookup"><span data-stu-id="b8286-198">A message box lists the order history for customer ALFKI.</span></span>  
  
     <span data-ttu-id="b8286-199">Kliknij przycisk **OK** , aby zamknąć okno komunikatu.</span><span class="sxs-lookup"><span data-stu-id="b8286-199">Click **OK** to close the message box.</span></span>  
  
4. <span data-ttu-id="b8286-200">W polu **Wprowadź identyfikator zamówienia** wpisz `123`, a następnie kliknij pozycję **szczegóły zamówienia**.</span><span class="sxs-lookup"><span data-stu-id="b8286-200">In the **Enter OrderID** box, type `123`, and then click **Order Details**.</span></span>  
  
     <span data-ttu-id="b8286-201">Okno komunikatu wyświetla komunikat "Brak wyników".</span><span class="sxs-lookup"><span data-stu-id="b8286-201">A message box displays "No results."</span></span>  
  
     <span data-ttu-id="b8286-202">Kliknij przycisk **OK** , aby zamknąć okno komunikatu.</span><span class="sxs-lookup"><span data-stu-id="b8286-202">Click **OK** to close the message box.</span></span>  
  
5. <span data-ttu-id="b8286-203">W menu **debugowanie** kliknij **Zatrzymaj debugowanie**.</span><span class="sxs-lookup"><span data-stu-id="b8286-203">On the **Debug** menu, click **Stop debugging**.</span></span>  
  
     <span data-ttu-id="b8286-204">Sesja debugowania zostanie zamknięta.</span><span class="sxs-lookup"><span data-stu-id="b8286-204">The debug session closes.</span></span>  
  
6. <span data-ttu-id="b8286-205">Jeśli zakończysz eksperymentowanie, możesz kliknąć przycisk **Zamknij projekt** w menu **plik** i zapisać projekt po wyświetleniu monitu.</span><span class="sxs-lookup"><span data-stu-id="b8286-205">If you have finished experimenting, you can click **Close Project** on the **File** menu, and save your project when you are prompted.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="b8286-206">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="b8286-206">Next Steps</span></span>  
 <span data-ttu-id="b8286-207">Możesz udoskonalić ten projekt, wprowadzając pewne zmiany.</span><span class="sxs-lookup"><span data-stu-id="b8286-207">You can enhance this project by making some changes.</span></span> <span data-ttu-id="b8286-208">Na przykład można wyświetlić listę dostępnych procedur składowanych w polu listy i wybrać procedury, które należy wykonać.</span><span class="sxs-lookup"><span data-stu-id="b8286-208">For example, you could list available stored procedures in a list box and have the user select which procedures to execute.</span></span> <span data-ttu-id="b8286-209">Możesz również przesyłać strumieniowo dane wyjściowe raportów do pliku tekstowego.</span><span class="sxs-lookup"><span data-stu-id="b8286-209">You could also stream the output of the reports to a text file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8286-210">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b8286-210">See also</span></span>

- [<span data-ttu-id="b8286-211">Nauka przez przewodniki</span><span class="sxs-lookup"><span data-stu-id="b8286-211">Learning by Walkthroughs</span></span>](learning-by-walkthroughs.md)
- [<span data-ttu-id="b8286-212">Procedury składowane</span><span class="sxs-lookup"><span data-stu-id="b8286-212">Stored Procedures</span></span>](stored-procedures.md)
