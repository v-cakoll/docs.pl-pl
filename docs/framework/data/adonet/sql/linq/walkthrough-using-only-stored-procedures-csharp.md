---
title: 'Wskazówki: Tylko przy użyciu przechowywanych procedur (C#)'
ms.date: 03/30/2017
ms.assetid: ecde4bf2-fa4d-4252-b5e4-96a46b9e097d
ms.openlocfilehash: 223c93a790e610414aa48c2aea8e884b9d841666
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365426"
---
# <a name="walkthrough-using-only-stored-procedures-c"></a><span data-ttu-id="a7298-102">Wskazówki: Tylko przy użyciu przechowywanych procedur (C#)</span><span class="sxs-lookup"><span data-stu-id="a7298-102">Walkthrough: Using Only Stored Procedures (C#)</span></span>
<span data-ttu-id="a7298-103">Ten przewodnik zawiera podstawowe end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tylko procedury składowane scenariusz do uzyskiwania dostępu do danych, wykonując.</span><span class="sxs-lookup"><span data-stu-id="a7298-103">This walkthrough provides a basic end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario for accessing data by executing stored procedures only.</span></span> <span data-ttu-id="a7298-104">Ta metoda jest często używane przez administratorów bazy danych do ograniczenia, jak jest uzyskiwany dostęp do magazynu danych.</span><span class="sxs-lookup"><span data-stu-id="a7298-104">This approach is often used by database administrators to limit how the datastore is accessed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a7298-105">Można również użyć procedur składowanych w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikacji, aby zastąpić zachowanie domyślne, szczególnie w przypadku `Create`, `Update`, i `Delete` procesów.</span><span class="sxs-lookup"><span data-stu-id="a7298-105">You can also use stored procedures in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications to override default behavior, especially for `Create`, `Update`, and `Delete` processes.</span></span> <span data-ttu-id="a7298-106">Aby uzyskać więcej informacji, zobacz [Dostosowywanie Insert, Update i operacji usunięcia](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="a7298-106">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
  
 <span data-ttu-id="a7298-107">Do celów tego przewodnika, korzystasz z dwóch metod, które zostały zamapowane do procedur przechowywanych w bazie danych Northwind: CustOrdersDetail i CustOrderHist.</span><span class="sxs-lookup"><span data-stu-id="a7298-107">For purposes of this walkthrough, you will use two methods that have been mapped to stored procedures in the Northwind sample database: CustOrdersDetail and CustOrderHist.</span></span> <span data-ttu-id="a7298-108">Mapowanie występuje podczas uruchamiania narzędzia wiersza polecenia SqlMetal, aby wygenerować plik C#.</span><span class="sxs-lookup"><span data-stu-id="a7298-108">The mapping occurs when you run the SqlMetal command-line tool to generate a C# file.</span></span> <span data-ttu-id="a7298-109">Aby uzyskać więcej informacji zobacz sekcję wymagań wstępnych w dalszej części tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="a7298-109">For more information, see the Prerequisites section later in this walkthrough.</span></span>  
  
 <span data-ttu-id="a7298-110">Ten przewodnik nie bazuje na [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a7298-110">This walkthrough does not rely on the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)].</span></span> <span data-ttu-id="a7298-111">Za pomocą programu Visual Studio programiści mogą również wykorzystać [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] do implementowania procedury składowanej.</span><span class="sxs-lookup"><span data-stu-id="a7298-111">Developers using Visual Studio can also use the [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] to implement stored procedure functionality.</span></span> <span data-ttu-id="a7298-112">Zobacz [składnika LINQ to SQL narzędzia w programie Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span><span class="sxs-lookup"><span data-stu-id="a7298-112">See [LINQ to SQL Tools in Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="a7298-113">W tym przewodniku została napisana przy użyciu programu Visual C# programowanie ustawienia.</span><span class="sxs-lookup"><span data-stu-id="a7298-113">This walkthrough was written by using Visual C# Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a7298-114">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="a7298-114">Prerequisites</span></span>  
 <span data-ttu-id="a7298-115">W tym przewodniku wymaga następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="a7298-115">This walkthrough requires the following:</span></span>  
  
-   <span data-ttu-id="a7298-116">W tym przewodniku zastosowano dedykowanych folderów ("c:\linqtest7") do przechowywania plików.</span><span class="sxs-lookup"><span data-stu-id="a7298-116">This walkthrough uses a dedicated folder ("c:\linqtest7") to hold files.</span></span> <span data-ttu-id="a7298-117">Utwórz ten folder przed rozpoczęciem przewodnika.</span><span class="sxs-lookup"><span data-stu-id="a7298-117">Create this folder before you begin the walkthrough.</span></span>  
  
-   <span data-ttu-id="a7298-118">Przykładowa bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="a7298-118">The Northwind sample database.</span></span>  
  
     <span data-ttu-id="a7298-119">Jeśli nie ma tej bazy danych na komputerze deweloperskim, można go pobrać z witryny pobierania firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a7298-119">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="a7298-120">Aby uzyskać instrukcje, zobacz [pobieranie przykładowe bazy danych](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="a7298-120">For instructions, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span> <span data-ttu-id="a7298-121">Po pobraniu bazy danych, skopiuj plik northwnd.mdf do folderu c:\linqtest7.</span><span class="sxs-lookup"><span data-stu-id="a7298-121">After you have downloaded the database, copy the northwnd.mdf file to the c:\linqtest7 folder.</span></span>  
  
-   <span data-ttu-id="a7298-122">Plik kodu C# wygenerowany z bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="a7298-122">A C# code file generated from the Northwind database.</span></span>  
  
     <span data-ttu-id="a7298-123">W tym przewodniku została napisana przy użyciu narzędzia SqlMetal z następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="a7298-123">This walkthrough was written by using the SqlMetal tool with the following command line:</span></span>  
  
     <span data-ttu-id="a7298-124">**sqlmetal /code:"c:\linqtest7\northwind.cs" /language:csharp "c:\linqtest7\northwnd.mdf" /sprocs /functions / pluralize**</span><span class="sxs-lookup"><span data-stu-id="a7298-124">**sqlmetal /code:"c:\linqtest7\northwind.cs" /language:csharp "c:\linqtest7\northwnd.mdf" /sprocs /functions /pluralize**</span></span>  
  
     <span data-ttu-id="a7298-125">Aby uzyskać więcej informacji, zobacz [SqlMetal.exe (narzędzie generowania kodu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="a7298-125">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="a7298-126">Omówienie</span><span class="sxs-lookup"><span data-stu-id="a7298-126">Overview</span></span>  
 <span data-ttu-id="a7298-127">Ten przewodnik obejmuje sześć głównych zadań:</span><span class="sxs-lookup"><span data-stu-id="a7298-127">This walkthrough consists of six main tasks:</span></span>  
  
-   <span data-ttu-id="a7298-128">Konfigurowanie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] rozwiązania w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a7298-128">Setting up the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>  
  
-   <span data-ttu-id="a7298-129">Dodawanie zestawu System.Data.Linq do projektu.</span><span class="sxs-lookup"><span data-stu-id="a7298-129">Adding the System.Data.Linq assembly to the project.</span></span>  
  
-   <span data-ttu-id="a7298-130">Dodawanie plików kodu bazy danych do projektu.</span><span class="sxs-lookup"><span data-stu-id="a7298-130">Adding the database code file to the project.</span></span>  
  
-   <span data-ttu-id="a7298-131">Tworzenie połączenia z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="a7298-131">Creating a connection with the database.</span></span>  
  
-   <span data-ttu-id="a7298-132">Konfigurowanie interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a7298-132">Setting up the user interface.</span></span>  
  
-   <span data-ttu-id="a7298-133">Działa i testowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a7298-133">Running and testing the application.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="a7298-134">Tworzenie składnika LINQ to SQL rozwiązania</span><span class="sxs-lookup"><span data-stu-id="a7298-134">Creating a LINQ to SQL Solution</span></span>  
 <span data-ttu-id="a7298-135">W tym zadaniu pierwszego tworzenia rozwiązania Visual Studio, który zawiera niezbędne odwołania, aby skompilować i uruchomić [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu.</span><span class="sxs-lookup"><span data-stu-id="a7298-135">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="a7298-136">Aby utworzyć składnika LINQ to SQL rozwiązania</span><span class="sxs-lookup"><span data-stu-id="a7298-136">To create a LINQ to SQL solution</span></span>  
  
1.  <span data-ttu-id="a7298-137">W programie Visual Studio **pliku** menu wskaż **nowy**, a następnie kliknij przycisk **projektu**.</span><span class="sxs-lookup"><span data-stu-id="a7298-137">On the Visual Studio **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="a7298-138">W **typy projektów** okienka w **nowy projekt** okno dialogowe, kliknij przycisk **Visual C#**.</span><span class="sxs-lookup"><span data-stu-id="a7298-138">In the **Project types** pane in the **New Project** dialog box, click **Visual C#**.</span></span>  
  
3.  <span data-ttu-id="a7298-139">W **szablony** okienku, kliknij przycisk **aplikacji Windows Forms**.</span><span class="sxs-lookup"><span data-stu-id="a7298-139">In the **Templates** pane, click **Windows Forms Application**.</span></span>  
  
4.  <span data-ttu-id="a7298-140">W **nazwa** wpisz **SprocOnlyApp**.</span><span class="sxs-lookup"><span data-stu-id="a7298-140">In the **Name** box, type **SprocOnlyApp**.</span></span>  
  
5.  <span data-ttu-id="a7298-141">W **lokalizacji** upewnij się, którym chcesz przechowywać pliki projektu.</span><span class="sxs-lookup"><span data-stu-id="a7298-141">In the **Location** box, verify where you want to store your project files.</span></span>  
  
6.  <span data-ttu-id="a7298-142">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="a7298-142">Click **OK**.</span></span>  
  
     <span data-ttu-id="a7298-143">Zostanie otwarty projektant formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="a7298-143">The Windows Forms Designer opens.</span></span>  
  
## <a name="adding-the-linq-to-sql-assembly-reference"></a><span data-ttu-id="a7298-144">Dodawanie LINQ do SQL odwołanie do zestawu</span><span class="sxs-lookup"><span data-stu-id="a7298-144">Adding the LINQ to SQL Assembly Reference</span></span>  
 <span data-ttu-id="a7298-145">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Zestaw nie jest dołączony do standardowego szablonu aplikacji formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="a7298-145">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] assembly is not included in the standard Windows Forms Application template.</span></span> <span data-ttu-id="a7298-146">Należy dodać zestaw samodzielnie, zgodnie z objaśnieniem w poniższych krokach:</span><span class="sxs-lookup"><span data-stu-id="a7298-146">You will have to add the assembly yourself, as explained in the following steps:</span></span>  
  
#### <a name="to-add-systemdatalinqdll"></a><span data-ttu-id="a7298-147">To add System.Data.Linq.dll</span><span class="sxs-lookup"><span data-stu-id="a7298-147">To add System.Data.Linq.dll</span></span>  
  
1.  <span data-ttu-id="a7298-148">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania**, a następnie kliknij przycisk **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="a7298-148">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="a7298-149">W **Dodaj odwołanie** okno dialogowe, kliknij przycisk **.NET**, kliknij zestaw System.Data.Linq, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="a7298-149">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="a7298-150">Zestaw został dodany do projektu.</span><span class="sxs-lookup"><span data-stu-id="a7298-150">The assembly is added to the project.</span></span>  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a><span data-ttu-id="a7298-151">Dodawanie plików kodu Northwind do projektu</span><span class="sxs-lookup"><span data-stu-id="a7298-151">Adding the Northwind Code File to the Project</span></span>  
 <span data-ttu-id="a7298-152">W tym kroku przyjęto założenie, użycie narzędzia SqlMetal do wygenerowania pliku kodu z przykładowej bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="a7298-152">This step assumes that you have used the SqlMetal tool to generate a code file from the Northwind sample database.</span></span> <span data-ttu-id="a7298-153">Aby uzyskać więcej informacji zobacz sekcję wymagań wstępnych we wcześniejszej części tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="a7298-153">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a><span data-ttu-id="a7298-154">Aby dodać plik kodu northwind do projektu</span><span class="sxs-lookup"><span data-stu-id="a7298-154">To add the northwind code file to the project</span></span>  
  
1.  <span data-ttu-id="a7298-155">Na **projektu** menu, kliknij przycisk **Dodaj istniejący element**.</span><span class="sxs-lookup"><span data-stu-id="a7298-155">On the **Project** menu, click **Add Existing Item**.</span></span>  
  
2.  <span data-ttu-id="a7298-156">W **Dodaj istniejący element** okno dialogowe, Przenieś do c:\linqtest7\northwind.cs, a następnie kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="a7298-156">In the **Add Existing Item** dialog box, move to c:\linqtest7\northwind.cs, and then click **Add**.</span></span>  
  
     <span data-ttu-id="a7298-157">Plik northwind.cs zostanie dodany do projektu.</span><span class="sxs-lookup"><span data-stu-id="a7298-157">The northwind.cs file is added to the project.</span></span>  
  
## <a name="creating-a-database-connection"></a><span data-ttu-id="a7298-158">Tworzenie połączenia z bazą danych</span><span class="sxs-lookup"><span data-stu-id="a7298-158">Creating a Database Connection</span></span>  
 <span data-ttu-id="a7298-159">W tym kroku definiowane połączenie z przykładowej bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="a7298-159">In this step, you define the connection to the Northwind sample database.</span></span> <span data-ttu-id="a7298-160">W tym przewodniku zastosowano "c:\linqtest7\northwnd.mdf" jako ścieżka.</span><span class="sxs-lookup"><span data-stu-id="a7298-160">This walkthrough uses "c:\linqtest7\northwnd.mdf" as the path.</span></span>  
  
#### <a name="to-create-the-database-connection"></a><span data-ttu-id="a7298-161">Aby utworzyć połączenie z bazą danych</span><span class="sxs-lookup"><span data-stu-id="a7298-161">To create the database connection</span></span>  
  
1.  <span data-ttu-id="a7298-162">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **pliku Form1.cs**, a następnie kliknij przycisk **kod widoku**.</span><span class="sxs-lookup"><span data-stu-id="a7298-162">In **Solution Explorer**, right-click **Form1.cs**, and then click **View Code**.</span></span>  
  
2.  <span data-ttu-id="a7298-163">Wpisz następujący kod do `Form1` klasy:</span><span class="sxs-lookup"><span data-stu-id="a7298-163">Type the following code into the `Form1` class:</span></span>  
  
     [!code-csharp[DLinqWalk4CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#1)]  
  
## <a name="setting-up-the-user-interface"></a><span data-ttu-id="a7298-164">Konfigurowanie interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="a7298-164">Setting up the User Interface</span></span>  
 <span data-ttu-id="a7298-165">W tym zadaniu skonfigurowaniu interfejs, dzięki czemu użytkownicy mogą wykonywać procedur składowanych dostępu do danych w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="a7298-165">In this task you set up an interface so that users can execute stored procedures to access data in the database.</span></span> <span data-ttu-id="a7298-166">W aplikacjach, które tworzysz z tym przewodnikiem użytkownicy mogą korzystać w bazie danych tylko przy użyciu procedur składowanych osadzone w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a7298-166">In the applications that you are developing with this walkthrough, users can access data in the database only by using the stored procedures embedded in the application.</span></span>  
  
#### <a name="to-set-up-the-user-interface"></a><span data-ttu-id="a7298-167">Aby skonfigurować interfejs użytkownika</span><span class="sxs-lookup"><span data-stu-id="a7298-167">To set up the user interface</span></span>  
  
1.  <span data-ttu-id="a7298-168">Projektant Forms powrotu do systemu Windows (**Form1.cs[Design]**).</span><span class="sxs-lookup"><span data-stu-id="a7298-168">Return to the Windows Forms Designer (**Form1.cs[Design]**).</span></span>  
  
2.  <span data-ttu-id="a7298-169">Na **widoku** menu, kliknij przycisk **przybornika**.</span><span class="sxs-lookup"><span data-stu-id="a7298-169">On the **View** menu, click **Toolbox**.</span></span>  
  
     <span data-ttu-id="a7298-170">Otwiera przybornika.</span><span class="sxs-lookup"><span data-stu-id="a7298-170">The toolbox opens.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a7298-171">Kliknij przycisk **autohide —** pinezki, aby utrzymać otwarte przybornika podczas przeprowadzania pozostałe kroki w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="a7298-171">Click the **AutoHide** pushpin to keep the toolbox open while you perform the remaining steps in this section.</span></span>  
  
3.  <span data-ttu-id="a7298-172">Przeciągnij z przybornika do dwóch przycisków, dwa pola tekstowe i dwie etykiety **Form1**.</span><span class="sxs-lookup"><span data-stu-id="a7298-172">Drag two buttons, two text boxes, and two labels from the toolbox onto **Form1**.</span></span>  
  
     <span data-ttu-id="a7298-173">Rozmieszczanie formantów jak towarzyszący ilustracji.</span><span class="sxs-lookup"><span data-stu-id="a7298-173">Arrange the controls as in the accompanying illustration.</span></span> <span data-ttu-id="a7298-174">Rozwiń węzeł **Form1** tak, aby formanty łatwo Dopasuj.</span><span class="sxs-lookup"><span data-stu-id="a7298-174">Expand **Form1** so that the controls fit easily.</span></span>  
  
4.  <span data-ttu-id="a7298-175">Kliknij prawym przyciskiem myszy **label1**, a następnie kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="a7298-175">Right-click **label1**, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="a7298-176">Zmień **tekst** właściwość z **label1** do **wprowadź OrderID:**.</span><span class="sxs-lookup"><span data-stu-id="a7298-176">Change the **Text** property from **label1** to **Enter OrderID:**.</span></span>  
  
6.  <span data-ttu-id="a7298-177">W ten sam sposób dla **label2**, zmień **tekst** właściwość z **label2** do **wprowadź CustomerID:**.</span><span class="sxs-lookup"><span data-stu-id="a7298-177">In the same way for **label2**, change the **Text** property from **label2** to **Enter CustomerID:**.</span></span>  
  
7.  <span data-ttu-id="a7298-178">W ten sam sposób, zmień **tekst** właściwość **button1** do **szczegółów zamówienia**.</span><span class="sxs-lookup"><span data-stu-id="a7298-178">In the same way, change the **Text** property for **button1** to **Order Details**.</span></span>  
  
8.  <span data-ttu-id="a7298-179">Zmień **tekst** właściwość **button2** do **historii zamówień**.</span><span class="sxs-lookup"><span data-stu-id="a7298-179">Change the **Text** property for **button2** to **Order History**.</span></span>  
  
     <span data-ttu-id="a7298-180">Rozszerzenia kontrolki przycisku, dzięki czemu cały tekst jest widoczny.</span><span class="sxs-lookup"><span data-stu-id="a7298-180">Widen the button controls so that all the text is visible.</span></span>  
  
#### <a name="to-handle-button-clicks"></a><span data-ttu-id="a7298-181">Do obsługi kliknięcia przycisków</span><span class="sxs-lookup"><span data-stu-id="a7298-181">To handle button clicks</span></span>  
  
1.  <span data-ttu-id="a7298-182">Kliknij dwukrotnie **szczegółów zamówienia** na **Form1** aby otworzyć program obsługi zdarzeń button1 w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="a7298-182">Double-click **Order Details** on **Form1** to open the button1 event handler in the code editor.</span></span>  
  
2.  <span data-ttu-id="a7298-183">Wpisz następujący kod do `button1` obsługi:</span><span class="sxs-lookup"><span data-stu-id="a7298-183">Type the following code into the `button1` handler:</span></span>  
  
     [!code-csharp[DLinqWalk4CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#2)]  
  
3.  <span data-ttu-id="a7298-184">Teraz kliknij dwukrotnie **button2** na **Form1** otworzyć `button2` obsługi</span><span class="sxs-lookup"><span data-stu-id="a7298-184">Now double-click **button2** on **Form1** to open the `button2` handler</span></span>  
  
4.  <span data-ttu-id="a7298-185">Wpisz następujący kod do `button2` obsługi:</span><span class="sxs-lookup"><span data-stu-id="a7298-185">Type the following code into the `button2` handler:</span></span>  
  
     [!code-csharp[DLinqWalk4CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#3)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="a7298-186">Testowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="a7298-186">Testing the Application</span></span>  
 <span data-ttu-id="a7298-187">Teraz nadszedł czas, aby przetestować aplikację.</span><span class="sxs-lookup"><span data-stu-id="a7298-187">Now it is time to test your application.</span></span> <span data-ttu-id="a7298-188">Należy pamiętać, że kontakt z magazynu danych jest ograniczona do dowolnej akcji może zająć dwie procedury składowanej.</span><span class="sxs-lookup"><span data-stu-id="a7298-188">Note that your contact with the datastore is limited to whatever actions the two stored procedures can take.</span></span> <span data-ttu-id="a7298-189">Te akcje są do zwrócenia produkty uwzględnione wszelkie orderID wprowadzona lub do zwrócenia historii produktów, uporządkowany w celu żadnych CustomerID wprowadzasz.</span><span class="sxs-lookup"><span data-stu-id="a7298-189">Those actions are to return the products included for any orderID you enter, or to return a history of products ordered for any CustomerID you enter.</span></span>  
  
#### <a name="to-test-the-application"></a><span data-ttu-id="a7298-190">Aby przetestować aplikację</span><span class="sxs-lookup"><span data-stu-id="a7298-190">To test the application</span></span>  
  
1.  <span data-ttu-id="a7298-191">Naciśnij klawisz F5, aby rozpocząć debugowania.</span><span class="sxs-lookup"><span data-stu-id="a7298-191">Press F5 to start debugging.</span></span>  
  
     <span data-ttu-id="a7298-192">Zostanie wyświetlone Form1.</span><span class="sxs-lookup"><span data-stu-id="a7298-192">Form1 appears.</span></span>  
  
2.  <span data-ttu-id="a7298-193">W **wprowadź OrderID** wpisz `10249`, a następnie kliknij przycisk **szczegółów zamówienia**.</span><span class="sxs-lookup"><span data-stu-id="a7298-193">In the **Enter OrderID** box, type `10249`, and then click **Order Details**.</span></span>  
  
     <span data-ttu-id="a7298-194">Okno komunikatu wymieniono produkty uwzględnione w kolejności 10249.</span><span class="sxs-lookup"><span data-stu-id="a7298-194">A message box lists the products included in order 10249.</span></span>  
  
     <span data-ttu-id="a7298-195">Kliknij przycisk **OK** aby zamknąć okno komunikatu.</span><span class="sxs-lookup"><span data-stu-id="a7298-195">Click **OK** to close the message box.</span></span>  
  
3.  <span data-ttu-id="a7298-196">W **wprowadź CustomerID** wpisz `ALFKI`, a następnie kliknij przycisk **historii zamówień**.</span><span class="sxs-lookup"><span data-stu-id="a7298-196">In the **Enter CustomerID** box, type `ALFKI`, and then click **Order History**.</span></span>  
  
     <span data-ttu-id="a7298-197">Pojawi się komunikat z listą historii zamówień klienta ALFKI.</span><span class="sxs-lookup"><span data-stu-id="a7298-197">A message box appears that lists the order history for customer ALFKI.</span></span>  
  
     <span data-ttu-id="a7298-198">Kliknij przycisk **OK** aby zamknąć okno komunikatu.</span><span class="sxs-lookup"><span data-stu-id="a7298-198">Click **OK** to close the message box.</span></span>  
  
4.  <span data-ttu-id="a7298-199">W **wprowadź OrderID** wpisz `123`, a następnie kliknij przycisk **szczegółów zamówienia**.</span><span class="sxs-lookup"><span data-stu-id="a7298-199">In the **Enter OrderID** box, type `123`, and then click **Order Details**.</span></span>  
  
     <span data-ttu-id="a7298-200">Pojawi się komunikat wyświetlany "Żadne wyniki".</span><span class="sxs-lookup"><span data-stu-id="a7298-200">A message box appears that displays "No results."</span></span>  
  
     <span data-ttu-id="a7298-201">Kliknij przycisk **OK** aby zamknąć okno komunikatu.</span><span class="sxs-lookup"><span data-stu-id="a7298-201">Click **OK** to close the message box.</span></span>  
  
5.  <span data-ttu-id="a7298-202">Na **debugowania** menu, kliknij przycisk **Zatrzymaj debugowanie**.</span><span class="sxs-lookup"><span data-stu-id="a7298-202">On the **Debug** menu, click **Stop debugging**.</span></span>  
  
     <span data-ttu-id="a7298-203">Powoduje zamknięcie sesji debugowania.</span><span class="sxs-lookup"><span data-stu-id="a7298-203">The debug session closes.</span></span>  
  
6.  <span data-ttu-id="a7298-204">Jeśli zakończysz eksperymentowanie, możesz kliknąć **Zamknij projekt** na **pliku** menu i zapisać projekt po wyświetleniu monitu.</span><span class="sxs-lookup"><span data-stu-id="a7298-204">If you have finished experimenting, you can click **Close Project** on the **File** menu, and save your project when you are prompted.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="a7298-205">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="a7298-205">Next Steps</span></span>  
 <span data-ttu-id="a7298-206">Wprowadzenie pewnych zmian można zwiększyć ten projekt.</span><span class="sxs-lookup"><span data-stu-id="a7298-206">You can enhance this project by making some changes.</span></span> <span data-ttu-id="a7298-207">Na przykład możesz wyświetlić listę dostępnych procedur składowanych w polu listy i użytkownik powinien wybrać, które procedury musisz wykonać.</span><span class="sxs-lookup"><span data-stu-id="a7298-207">For example, you could list available stored procedures in a list box and have the user select which procedures to execute.</span></span> <span data-ttu-id="a7298-208">Można również strumienia wyjściowego raportów do pliku tekstowego.</span><span class="sxs-lookup"><span data-stu-id="a7298-208">You could also stream the output of the reports to a text file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7298-209">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a7298-209">See Also</span></span>  
 [<span data-ttu-id="a7298-210">Nauka przez przewodniki</span><span class="sxs-lookup"><span data-stu-id="a7298-210">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)  
 [<span data-ttu-id="a7298-211">Procedury składowane</span><span class="sxs-lookup"><span data-stu-id="a7298-211">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
