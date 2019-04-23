---
title: 'Przewodnik: Używanie tylko procedur składowanych (C#)'
ms.date: 03/30/2017
ms.assetid: ecde4bf2-fa4d-4252-b5e4-96a46b9e097d
ms.openlocfilehash: e5497c1c6bfe032ba272c911217adaa3bd7f4f4f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59332706"
---
# <a name="walkthrough-using-only-stored-procedures-c"></a><span data-ttu-id="e9d4e-102">Przewodnik: Używanie tylko procedur składowanych (C#)</span><span class="sxs-lookup"><span data-stu-id="e9d4e-102">Walkthrough: Using Only Stored Procedures (C#)</span></span>
<span data-ttu-id="e9d4e-103">Ten przewodnik zawiera podstawowe end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenariusz do uzyskiwania dostępu do danych, wykonując procedury składowane tylko.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-103">This walkthrough provides a basic end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario for accessing data by executing stored procedures only.</span></span> <span data-ttu-id="e9d4e-104">To podejście jest często używana przez administratorów baz danych, aby ograniczyć sposób dostępu do magazynu danych.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-104">This approach is often used by database administrators to limit how the datastore is accessed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e9d4e-105">Można również użyć procedur składowanych w programie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikacji, aby zastąpić domyślne zachowanie, szczególnie w przypadku `Create`, `Update`, i `Delete` procesów.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-105">You can also use stored procedures in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications to override default behavior, especially for `Create`, `Update`, and `Delete` processes.</span></span> <span data-ttu-id="e9d4e-106">Aby uzyskać więcej informacji, zobacz [Dostosowywanie Insert, Update i operacje usuwania](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="e9d4e-106">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
  
 <span data-ttu-id="e9d4e-107">Do celów tego przewodnika będziesz używać dwóch metod, które zostały zmapowane do procedur składowanych w bazie danych Northwind: CustOrdersDetail i CustOrderHist.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-107">For purposes of this walkthrough, you will use two methods that have been mapped to stored procedures in the Northwind sample database: CustOrdersDetail and CustOrderHist.</span></span> <span data-ttu-id="e9d4e-108">Mapowanie występuje podczas uruchamiania narzędzia wiersza polecenia SqlMetal można wygenerować C# pliku.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-108">The mapping occurs when you run the SqlMetal command-line tool to generate a C# file.</span></span> <span data-ttu-id="e9d4e-109">Aby uzyskać więcej informacji zobacz sekcję wymagania wstępne w dalszej części tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-109">For more information, see the Prerequisites section later in this walkthrough.</span></span>  
  
 <span data-ttu-id="e9d4e-110">W tym przewodniku nie zależą od [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e9d4e-110">This walkthrough does not rely on the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)].</span></span> <span data-ttu-id="e9d4e-111">Deweloperzy korzystający z programu Visual Studio można również użyć [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] do implementowania procedury składowanej.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-111">Developers using Visual Studio can also use the [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] to implement stored procedure functionality.</span></span> <span data-ttu-id="e9d4e-112">Zobacz [LINQ to SQL Tools w programie Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span><span class="sxs-lookup"><span data-stu-id="e9d4e-112">See [LINQ to SQL Tools in Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="e9d4e-113">W tym przewodniku została napisana przy użyciu Visual C# ustawieniami środowiska deweloperskiego.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-113">This walkthrough was written by using Visual C# Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="e9d4e-114">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="e9d4e-114">Prerequisites</span></span>  
 <span data-ttu-id="e9d4e-115">Ten przewodnik wymaga następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="e9d4e-115">This walkthrough requires the following:</span></span>  
  
-   <span data-ttu-id="e9d4e-116">W tym przewodniku używa dedykowanego folder ("c:\linqtest7") do przechowywania plików.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-116">This walkthrough uses a dedicated folder ("c:\linqtest7") to hold files.</span></span> <span data-ttu-id="e9d4e-117">Przed rozpoczęciem instruktażu, należy utworzyć ten folder.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-117">Create this folder before you begin the walkthrough.</span></span>  
  
-   <span data-ttu-id="e9d4e-118">Przykładowa bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-118">The Northwind sample database.</span></span>  
  
     <span data-ttu-id="e9d4e-119">Jeśli nie masz tej bazy danych na komputerze deweloperskim, możesz ją pobrać z witryny pobierania firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-119">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="e9d4e-120">Aby uzyskać instrukcje, zobacz [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="e9d4e-120">For instructions, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span> <span data-ttu-id="e9d4e-121">Po pobraniu bazy danych, skopiuj plik northwnd.mdf do folderu c:\linqtest7.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-121">After you have downloaded the database, copy the northwnd.mdf file to the c:\linqtest7 folder.</span></span>  
  
-   <span data-ttu-id="e9d4e-122">A C# plik kod wygenerowany z bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-122">A C# code file generated from the Northwind database.</span></span>  
  
     <span data-ttu-id="e9d4e-123">Ten instruktaż został napisany za pomocą narzędzia SqlMetal za pomocą następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="e9d4e-123">This walkthrough was written by using the SqlMetal tool with the following command line:</span></span>  
  
     <span data-ttu-id="e9d4e-124">**Program sqlmetal /code:"c:\linqtest7\northwind.cs" / Language: CSharp "c:\linqtest7\northwnd.mdf" /sprocs /functions / pluralize**</span><span class="sxs-lookup"><span data-stu-id="e9d4e-124">**sqlmetal /code:"c:\linqtest7\northwind.cs" /language:csharp "c:\linqtest7\northwnd.mdf" /sprocs /functions /pluralize**</span></span>  
  
     <span data-ttu-id="e9d4e-125">Aby uzyskać więcej informacji, zobacz [SqlMetal.exe (narzędzie generowania kodu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="e9d4e-125">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="e9d4e-126">Omówienie</span><span class="sxs-lookup"><span data-stu-id="e9d4e-126">Overview</span></span>  
 <span data-ttu-id="e9d4e-127">Ten przewodnik składa się z sześciu głównych zadań:</span><span class="sxs-lookup"><span data-stu-id="e9d4e-127">This walkthrough consists of six main tasks:</span></span>  
  
-   <span data-ttu-id="e9d4e-128">Konfigurowanie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] rozwiązania w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-128">Setting up the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>  
  
-   <span data-ttu-id="e9d4e-129">Trwa dodawanie zestawu System.Data.Linq do projektu.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-129">Adding the System.Data.Linq assembly to the project.</span></span>  
  
-   <span data-ttu-id="e9d4e-130">Dodawanie pliku kodu bazy danych do projektu.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-130">Adding the database code file to the project.</span></span>  
  
-   <span data-ttu-id="e9d4e-131">Tworzenie połączenia z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-131">Creating a connection with the database.</span></span>  
  
-   <span data-ttu-id="e9d4e-132">Konfigurowanie interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-132">Setting up the user interface.</span></span>  
  
-   <span data-ttu-id="e9d4e-133">Uruchamianie i testowanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-133">Running and testing the application.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="e9d4e-134">Tworzenie składnika LINQ to SQL rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="e9d4e-134">Creating a LINQ to SQL Solution</span></span>  
 <span data-ttu-id="e9d4e-135">W tym pierwszym zadaniu tworzyć rozwiązania programu Visual Studio, który zawiera niezbędne odwołania, aby skompilować i uruchomić [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-135">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="e9d4e-136">Aby utworzyć składnika LINQ to SQL rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="e9d4e-136">To create a LINQ to SQL solution</span></span>  
  
1. <span data-ttu-id="e9d4e-137">W programie Visual Studio **pliku** menu wskaż **New**, a następnie kliknij przycisk **projektu**.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-137">On the Visual Studio **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2. <span data-ttu-id="e9d4e-138">W **typów projektów** okienka **nowy projekt** okno dialogowe, kliknij przycisk **Visual C#** .</span><span class="sxs-lookup"><span data-stu-id="e9d4e-138">In the **Project types** pane in the **New Project** dialog box, click **Visual C#**.</span></span>  
  
3. <span data-ttu-id="e9d4e-139">W **szablony** okienku kliknij **aplikacja interfejsu Windows Forms**.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-139">In the **Templates** pane, click **Windows Forms Application**.</span></span>  
  
4. <span data-ttu-id="e9d4e-140">W **nazwa** wpisz **SprocOnlyApp**.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-140">In the **Name** box, type **SprocOnlyApp**.</span></span>  
  
5. <span data-ttu-id="e9d4e-141">W **lokalizacji** upewnij się, którym chcesz przechowywać swoje pliki projektu.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-141">In the **Location** box, verify where you want to store your project files.</span></span>  
  
6. <span data-ttu-id="e9d4e-142">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-142">Click **OK**.</span></span>  
  
     <span data-ttu-id="e9d4e-143">Zostanie otwarty projektant formularzy Windows.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-143">The Windows Forms Designer opens.</span></span>  
  
## <a name="adding-the-linq-to-sql-assembly-reference"></a><span data-ttu-id="e9d4e-144">Dodawanie programu LINQ do SQL odwołanie do zestawu</span><span class="sxs-lookup"><span data-stu-id="e9d4e-144">Adding the LINQ to SQL Assembly Reference</span></span>  
 <span data-ttu-id="e9d4e-145">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Moduł nie jest dołączony do standardowego szablonu aplikacja interfejsu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-145">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] assembly is not included in the standard Windows Forms Application template.</span></span> <span data-ttu-id="e9d4e-146">Trzeba będzie dodać zestaw samodzielnie, zgodnie z opisem w poniższych krokach:</span><span class="sxs-lookup"><span data-stu-id="e9d4e-146">You will have to add the assembly yourself, as explained in the following steps:</span></span>  
  
#### <a name="to-add-systemdatalinqdll"></a><span data-ttu-id="e9d4e-147">To add System.Data.Linq.dll</span><span class="sxs-lookup"><span data-stu-id="e9d4e-147">To add System.Data.Linq.dll</span></span>  
  
1. <span data-ttu-id="e9d4e-148">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania**, a następnie kliknij przycisk **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-148">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
2. <span data-ttu-id="e9d4e-149">W **Dodaj odwołanie** okno dialogowe, kliknij przycisk **.NET**, kliknij zestaw System.Data.Linq, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-149">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="e9d4e-150">Zestaw został dodany do projektu.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-150">The assembly is added to the project.</span></span>  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a><span data-ttu-id="e9d4e-151">Dodawanie pliku Northwind kodu do projektu</span><span class="sxs-lookup"><span data-stu-id="e9d4e-151">Adding the Northwind Code File to the Project</span></span>  
 <span data-ttu-id="e9d4e-152">Tego kroku przyjęto założenie, że trzeba użyć narzędzia SqlMetal do generowania pliku kodu z przykładowej bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-152">This step assumes that you have used the SqlMetal tool to generate a code file from the Northwind sample database.</span></span> <span data-ttu-id="e9d4e-153">Aby uzyskać więcej informacji zobacz sekcję wymagania wstępne we wcześniejszej części tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-153">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a><span data-ttu-id="e9d4e-154">Aby dodać plik kodu northwind do projektu</span><span class="sxs-lookup"><span data-stu-id="e9d4e-154">To add the northwind code file to the project</span></span>  
  
1. <span data-ttu-id="e9d4e-155">Na **projektu** menu, kliknij przycisk **Dodaj istniejący element**.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-155">On the **Project** menu, click **Add Existing Item**.</span></span>  
  
2. <span data-ttu-id="e9d4e-156">W **Dodaj istniejący element** przenieść c:\linqtest7\northwind.cs okno dialogowe, a następnie kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-156">In the **Add Existing Item** dialog box, move to c:\linqtest7\northwind.cs, and then click **Add**.</span></span>  
  
     <span data-ttu-id="e9d4e-157">Plik northwind.cs zostanie dodany do projektu.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-157">The northwind.cs file is added to the project.</span></span>  
  
## <a name="creating-a-database-connection"></a><span data-ttu-id="e9d4e-158">Tworzenie połączenia z bazą danych</span><span class="sxs-lookup"><span data-stu-id="e9d4e-158">Creating a Database Connection</span></span>  
 <span data-ttu-id="e9d4e-159">W tym kroku zdefiniujesz połączenia z przykładową bazą danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-159">In this step, you define the connection to the Northwind sample database.</span></span> <span data-ttu-id="e9d4e-160">W tym instruktażu wykorzystano "c:\linqtest7\northwnd.mdf", jako ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-160">This walkthrough uses "c:\linqtest7\northwnd.mdf" as the path.</span></span>  
  
#### <a name="to-create-the-database-connection"></a><span data-ttu-id="e9d4e-161">Aby utworzyć połączenie z bazą danych</span><span class="sxs-lookup"><span data-stu-id="e9d4e-161">To create the database connection</span></span>  
  
1. <span data-ttu-id="e9d4e-162">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **Form1.cs**, a następnie kliknij przycisk **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-162">In **Solution Explorer**, right-click **Form1.cs**, and then click **View Code**.</span></span>  
  
2. <span data-ttu-id="e9d4e-163">Wpisz następujący kod do `Form1` klasy:</span><span class="sxs-lookup"><span data-stu-id="e9d4e-163">Type the following code into the `Form1` class:</span></span>  
  
     [!code-csharp[DLinqWalk4CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#1)]  
  
## <a name="setting-up-the-user-interface"></a><span data-ttu-id="e9d4e-164">Konfigurowanie interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="e9d4e-164">Setting up the User Interface</span></span>  
 <span data-ttu-id="e9d4e-165">W tym zadaniu konfigurujesz interfejs, dzięki czemu użytkownicy mogą wykonać procedur składowanych na dostęp do danych w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-165">In this task you set up an interface so that users can execute stored procedures to access data in the database.</span></span> <span data-ttu-id="e9d4e-166">W aplikacjach, które tworzysz z tym przewodnikiem użytkownicy mogą korzystać tylko przy użyciu procedur składowanych osadzone w aplikacji, dane z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-166">In the applications that you are developing with this walkthrough, users can access data in the database only by using the stored procedures embedded in the application.</span></span>  
  
#### <a name="to-set-up-the-user-interface"></a><span data-ttu-id="e9d4e-167">Aby skonfigurować interfejs użytkownika</span><span class="sxs-lookup"><span data-stu-id="e9d4e-167">To set up the user interface</span></span>  
  
1. <span data-ttu-id="e9d4e-168">Wróć do Windows Forms Designer (**Form1.cs[Design]**).</span><span class="sxs-lookup"><span data-stu-id="e9d4e-168">Return to the Windows Forms Designer (**Form1.cs[Design]**).</span></span>  
  
2. <span data-ttu-id="e9d4e-169">Na **widoku** menu, kliknij przycisk **przybornika**.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-169">On the **View** menu, click **Toolbox**.</span></span>  
  
     <span data-ttu-id="e9d4e-170">Przybornik zostaje otwarty.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-170">The toolbox opens.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e9d4e-171">Kliknij przycisk **autoukrywania** pinezki, aby nie zamykaj przybornika podczas wykonywania pozostałych kroków w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-171">Click the **AutoHide** pushpin to keep the toolbox open while you perform the remaining steps in this section.</span></span>  
  
3. <span data-ttu-id="e9d4e-172">Przeciągnij z przybornika na dwa przyciski, dwóch pól tekstowych i dwie etykiety **Form1**.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-172">Drag two buttons, two text boxes, and two labels from the toolbox onto **Form1**.</span></span>  
  
     <span data-ttu-id="e9d4e-173">Kontrolki będą ułożone, jak pokazano na ilustracji towarzyszącej.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-173">Arrange the controls as in the accompanying illustration.</span></span> <span data-ttu-id="e9d4e-174">Rozwiń **Form1** tak, aby łatwo mieści się kontrolki.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-174">Expand **Form1** so that the controls fit easily.</span></span>  
  
4. <span data-ttu-id="e9d4e-175">Kliknij prawym przyciskiem myszy **label1**, a następnie kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-175">Right-click **label1**, and then click **Properties**.</span></span>  
  
5. <span data-ttu-id="e9d4e-176">Zmiana **tekstu** właściwość **label1** do **wprowadź OrderID:**.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-176">Change the **Text** property from **label1** to **Enter OrderID:**.</span></span>  
  
6. <span data-ttu-id="e9d4e-177">W ten sam sposób, aby uzyskać **etykiety 2**, zmienić **tekstu** właściwość **etykiety 2** do **wprowadź CustomerID:**.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-177">In the same way for **label2**, change the **Text** property from **label2** to **Enter CustomerID:**.</span></span>  
  
7. <span data-ttu-id="e9d4e-178">W ten sam sposób, jak zmienić **tekstu** właściwość **button1** do **Orderdetails**.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-178">In the same way, change the **Text** property for **button1** to **Order Details**.</span></span>  
  
8. <span data-ttu-id="e9d4e-179">Zmiana **tekstu** właściwość **button2** do **historii zamówień**.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-179">Change the **Text** property for **button2** to **Order History**.</span></span>  
  
     <span data-ttu-id="e9d4e-180">Tak, aby cały tekst jest widoczne, mogą zostać poszerzone formanty przycisków.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-180">Widen the button controls so that all the text is visible.</span></span>  
  
#### <a name="to-handle-button-clicks"></a><span data-ttu-id="e9d4e-181">Do obsługi kliknięcia przycisków</span><span class="sxs-lookup"><span data-stu-id="e9d4e-181">To handle button clicks</span></span>  
  
1. <span data-ttu-id="e9d4e-182">Kliknij dwukrotnie **Orderdetails** na **Form1** aby otworzyć program obsługi zdarzeń przycisku button1 w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-182">Double-click **Order Details** on **Form1** to open the button1 event handler in the code editor.</span></span>  
  
2. <span data-ttu-id="e9d4e-183">Wpisz następujący kod do `button1` procedury obsługi:</span><span class="sxs-lookup"><span data-stu-id="e9d4e-183">Type the following code into the `button1` handler:</span></span>  
  
     [!code-csharp[DLinqWalk4CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#2)]  
  
3. <span data-ttu-id="e9d4e-184">Teraz kliknij dwukrotnie **button2** na **Form1** otworzyć `button2` procedury obsługi</span><span class="sxs-lookup"><span data-stu-id="e9d4e-184">Now double-click **button2** on **Form1** to open the `button2` handler</span></span>  
  
4. <span data-ttu-id="e9d4e-185">Wpisz następujący kod do `button2` procedury obsługi:</span><span class="sxs-lookup"><span data-stu-id="e9d4e-185">Type the following code into the `button2` handler:</span></span>  
  
     [!code-csharp[DLinqWalk4CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#3)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="e9d4e-186">Testowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="e9d4e-186">Testing the Application</span></span>  
 <span data-ttu-id="e9d4e-187">Teraz nadszedł czas, aby przetestować aplikację.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-187">Now it is time to test your application.</span></span> <span data-ttu-id="e9d4e-188">Należy pamiętać, że kontaktu z magazynu danych jest ograniczony do dowolnych akcje można wykonać dwie procedury składowane.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-188">Note that your contact with the datastore is limited to whatever actions the two stored procedures can take.</span></span> <span data-ttu-id="e9d4e-189">Te akcje są do zwrócenia produktów, dostępny dla dowolnego orderID wprowadzona lub w celu zwrócenia historii produktów uporządkowane do dowolnego CustomerID wprowadzeniu.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-189">Those actions are to return the products included for any orderID you enter, or to return a history of products ordered for any CustomerID you enter.</span></span>  
  
#### <a name="to-test-the-application"></a><span data-ttu-id="e9d4e-190">Aby przetestować aplikację</span><span class="sxs-lookup"><span data-stu-id="e9d4e-190">To test the application</span></span>  
  
1. <span data-ttu-id="e9d4e-191">Naciśnij klawisz F5, aby rozpocząć debugowanie.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-191">Press F5 to start debugging.</span></span>  
  
     <span data-ttu-id="e9d4e-192">Zostanie wyświetlony formularz Form1.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-192">Form1 appears.</span></span>  
  
2. <span data-ttu-id="e9d4e-193">W **wprowadź OrderID** wpisz `10249`, a następnie kliknij przycisk **Orderdetails**.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-193">In the **Enter OrderID** box, type `10249`, and then click **Order Details**.</span></span>  
  
     <span data-ttu-id="e9d4e-194">Okno komunikatu Wyświetla listę produktów dołączone w kolejności 10249.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-194">A message box lists the products included in order 10249.</span></span>  
  
     <span data-ttu-id="e9d4e-195">Kliknij przycisk **OK** aby zamknąć okno komunikatu.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-195">Click **OK** to close the message box.</span></span>  
  
3. <span data-ttu-id="e9d4e-196">W **wprowadź CustomerID** wpisz `ALFKI`, a następnie kliknij przycisk **historii zamówień**.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-196">In the **Enter CustomerID** box, type `ALFKI`, and then click **Order History**.</span></span>  
  
     <span data-ttu-id="e9d4e-197">Pojawi się komunikat zawierający listę historii zamówień klienta Customer ALFKI.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-197">A message box appears that lists the order history for customer ALFKI.</span></span>  
  
     <span data-ttu-id="e9d4e-198">Kliknij przycisk **OK** aby zamknąć okno komunikatu.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-198">Click **OK** to close the message box.</span></span>  
  
4. <span data-ttu-id="e9d4e-199">W **wprowadź OrderID** wpisz `123`, a następnie kliknij przycisk **Orderdetails**.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-199">In the **Enter OrderID** box, type `123`, and then click **Order Details**.</span></span>  
  
     <span data-ttu-id="e9d4e-200">Okno komunikatu zostanie wyświetlone "Brak wyników".</span><span class="sxs-lookup"><span data-stu-id="e9d4e-200">A message box appears that displays "No results."</span></span>  
  
     <span data-ttu-id="e9d4e-201">Kliknij przycisk **OK** aby zamknąć okno komunikatu.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-201">Click **OK** to close the message box.</span></span>  
  
5. <span data-ttu-id="e9d4e-202">Na **debugowania** menu, kliknij przycisk **Zatrzymaj debugowanie**.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-202">On the **Debug** menu, click **Stop debugging**.</span></span>  
  
     <span data-ttu-id="e9d4e-203">Powoduje zamknięcie sesji debugowania.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-203">The debug session closes.</span></span>  
  
6. <span data-ttu-id="e9d4e-204">Jeśli zakończysz, eksperymentowanie, możesz kliknąć **Zamknij projekt** na **pliku** menu i zapisać projekt, po wyświetleniu monitu.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-204">If you have finished experimenting, you can click **Close Project** on the **File** menu, and save your project when you are prompted.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="e9d4e-205">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="e9d4e-205">Next Steps</span></span>  
 <span data-ttu-id="e9d4e-206">Ten projekt można zwiększyć, dokonując pewnych zmian.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-206">You can enhance this project by making some changes.</span></span> <span data-ttu-id="e9d4e-207">Na przykład możesz wyświetlić listę dostępnych procedur składowanych w polu listy i użytkownik powinien wybrać, które procedury musisz wykonać.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-207">For example, you could list available stored procedures in a list box and have the user select which procedures to execute.</span></span> <span data-ttu-id="e9d4e-208">Można również przesyłać strumieniowo dane wyjściowe raportów do pliku tekstowego.</span><span class="sxs-lookup"><span data-stu-id="e9d4e-208">You could also stream the output of the reports to a text file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9d4e-209">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e9d4e-209">See also</span></span>

- [<span data-ttu-id="e9d4e-210">Nauka przez przewodniki</span><span class="sxs-lookup"><span data-stu-id="e9d4e-210">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
- [<span data-ttu-id="e9d4e-211">Procedury składowane</span><span class="sxs-lookup"><span data-stu-id="e9d4e-211">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
