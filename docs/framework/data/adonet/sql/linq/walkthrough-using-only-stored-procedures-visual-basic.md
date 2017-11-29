---
title: "Wskazówki: Tylko przy użyciu przechowywanych procedur (Visual Basic)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: vb
ms.assetid: 5a736a30-ba66-4adb-b87c-57d19476e862
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2facb328791f07d6def2d466c799f031fe500d6f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-using-only-stored-procedures-visual-basic"></a><span data-ttu-id="f8ec0-102">Wskazówki: Tylko przy użyciu przechowywanych procedur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f8ec0-102">Walkthrough: Using Only Stored Procedures (Visual Basic)</span></span>
<span data-ttu-id="f8ec0-103">Ten przewodnik zawiera podstawowe end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tylko procedury składowane scenariusz do uzyskiwania dostępu do danych za pomocą.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-103">This walkthrough provides a basic end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario for accessing data by using stored procedures only.</span></span> <span data-ttu-id="f8ec0-104">Ta metoda jest często używane przez administratorów bazy danych do ograniczenia, jak jest uzyskiwany dostęp do magazynu danych.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-104">This approach is often used by database administrators to limit how the datastore is accessed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f8ec0-105">Można również użyć procedur składowanych w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikacji, aby zastąpić zachowanie domyślne, szczególnie w przypadku `Create`, `Update`, i `Delete` procesów.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-105">You can also use stored procedures in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications to override default behavior, especially for `Create`, `Update`, and `Delete` processes.</span></span> <span data-ttu-id="f8ec0-106">Aby uzyskać więcej informacji, zobacz [Dostosowywanie Insert, Update i operacji usunięcia](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="f8ec0-106">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
  
 <span data-ttu-id="f8ec0-107">Do celów tego przewodnika, korzystasz z dwóch metod, które zostały zamapowane do procedur przechowywanych w bazie danych Northwind: CustOrdersDetail i CustOrderHist.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-107">For purposes of this walkthrough, you will use two methods that have been mapped to stored procedures in the Northwind sample database: CustOrdersDetail and CustOrderHist.</span></span> <span data-ttu-id="f8ec0-108">Mapowanie występuje podczas uruchamiania narzędzia wiersza polecenia SqlMetal, aby wygenerować [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] pliku.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-108">The mapping occurs when you run the SqlMetal command-line tool to generate a [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] file.</span></span> <span data-ttu-id="f8ec0-109">Aby uzyskać więcej informacji zobacz sekcję wymagań wstępnych w dalszej części tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-109">For more information, see the Prerequisites section later in this walkthrough.</span></span>  
  
 <span data-ttu-id="f8ec0-110">Ten przewodnik nie bazuje na [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f8ec0-110">This walkthrough does not rely on the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)].</span></span> <span data-ttu-id="f8ec0-111">Deweloperzy przy użyciu [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] także [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] do implementowania procedury składowanej.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-111">Developers using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] can also use the [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] to implement stored procedure functionality.</span></span> <span data-ttu-id="f8ec0-112">Zobacz [składnika LINQ to SQL narzędzia w programie Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span><span class="sxs-lookup"><span data-stu-id="f8ec0-112">See [LINQ to SQL Tools in Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="f8ec0-113">W tym przewodniku została napisana przy użyciu ustawienia środowiska deweloperskiego Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-113">This walkthrough was written by using Visual Basic Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f8ec0-114">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="f8ec0-114">Prerequisites</span></span>  
 <span data-ttu-id="f8ec0-115">W tym przewodniku wymaga następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="f8ec0-115">This walkthrough requires the following:</span></span>  
  
-   <span data-ttu-id="f8ec0-116">W tym przewodniku zastosowano dedykowanych folderów ("c:\linqtest3") do przechowywania plików.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-116">This walkthrough uses a dedicated folder ("c:\linqtest3") to hold files.</span></span> <span data-ttu-id="f8ec0-117">Utwórz ten folder przed rozpoczęciem przewodnika.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-117">Create this folder before you begin the walkthrough.</span></span>  
  
-   <span data-ttu-id="f8ec0-118">Przykładowa bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-118">The Northwind sample database.</span></span>  
  
     <span data-ttu-id="f8ec0-119">Jeśli nie ma tej bazy danych na komputerze deweloperskim, można go pobrać z witryny pobierania firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-119">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="f8ec0-120">Aby uzyskać instrukcje, zobacz [pobieranie przykładowe bazy danych](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="f8ec0-120">For instructions, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span> <span data-ttu-id="f8ec0-121">Po pobraniu bazy danych, skopiuj plik northwnd.mdf do folderu c:\linqtest3.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-121">After you have downloaded the database, copy the northwnd.mdf file to the c:\linqtest3 folder.</span></span>  
  
-   <span data-ttu-id="f8ec0-122">A [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] wygenerowane z bazy danych Northwind pliku kodu.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-122">A [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] code file generated from the Northwind database.</span></span>  
  
     <span data-ttu-id="f8ec0-123">W tym przewodniku została napisana przy użyciu narzędzia SqlMetal z następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="f8ec0-123">This walkthrough was written by using the SqlMetal tool with the following command line:</span></span>  
  
     <span data-ttu-id="f8ec0-124">**sqlmetal /code:"c:\linqtest3\northwind.vb" /language:vb "c:\linqtest3\northwnd.mdf" /sprocs /functions / pluralize**</span><span class="sxs-lookup"><span data-stu-id="f8ec0-124">**sqlmetal /code:"c:\linqtest3\northwind.vb" /language:vb "c:\linqtest3\northwnd.mdf" /sprocs /functions /pluralize**</span></span>  
  
     <span data-ttu-id="f8ec0-125">Aby uzyskać więcej informacji, zobacz [SqlMetal.exe (narzędzie generowania kodu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="f8ec0-125">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="f8ec0-126">Omówienie</span><span class="sxs-lookup"><span data-stu-id="f8ec0-126">Overview</span></span>  
 <span data-ttu-id="f8ec0-127">Ten przewodnik obejmuje sześć głównych zadań:</span><span class="sxs-lookup"><span data-stu-id="f8ec0-127">This walkthrough consists of six main tasks:</span></span>  
  
-   <span data-ttu-id="f8ec0-128">Konfigurowanie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] rozwiązania [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f8ec0-128">Setting up the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)].</span></span>  
  
-   <span data-ttu-id="f8ec0-129">Dodawanie zestawu System.Data.Linq do projektu.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-129">Adding the System.Data.Linq assembly to the project.</span></span>  
  
-   <span data-ttu-id="f8ec0-130">Dodawanie plików kodu bazy danych do projektu.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-130">Adding the database code file to the project.</span></span>  
  
-   <span data-ttu-id="f8ec0-131">Tworzenie połączenia z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-131">Creating a connection to the database.</span></span>  
  
-   <span data-ttu-id="f8ec0-132">Konfigurowanie interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-132">Setting up the user interface.</span></span>  
  
-   <span data-ttu-id="f8ec0-133">Działa i testowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-133">Running and testing the application.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="f8ec0-134">Tworzenie składnika LINQ to SQL rozwiązania</span><span class="sxs-lookup"><span data-stu-id="f8ec0-134">Creating a LINQ to SQL Solution</span></span>  
 <span data-ttu-id="f8ec0-135">W tym zadaniu pierwszym utworzeniu [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] rozwiązania zawierającego niezbędne odwołania, aby skompilować i uruchomić [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-135">In this first task, you create a [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="f8ec0-136">Aby utworzyć składnika LINQ to SQL rozwiązania</span><span class="sxs-lookup"><span data-stu-id="f8ec0-136">To create a LINQ to SQL solution</span></span>  
  
1.  <span data-ttu-id="f8ec0-137">Na [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] **pliku** menu, kliknij przycisk **nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-137">On the [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] **File** menu, click **New Project**.</span></span>  
  
2.  <span data-ttu-id="f8ec0-138">W **typy projektów** okienka w **nowy projekt** okna dialogowego rozwiń **Visual Basic**, a następnie kliknij przycisk **Windows**.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-138">In the **Project types** pane in the **New Project** dialog box, expand **Visual Basic**, and then click **Windows**.</span></span>  
  
3.  <span data-ttu-id="f8ec0-139">W **szablony** okienku, kliknij przycisk **aplikacji Windows Forms**.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-139">In the **Templates** pane, click **Windows Forms Application**.</span></span>  
  
4.  <span data-ttu-id="f8ec0-140">W **nazwa** wpisz **SprocOnlyApp**.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-140">In the **Name** box, type **SprocOnlyApp**.</span></span>  
  
5.  <span data-ttu-id="f8ec0-141">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-141">Click **OK**.</span></span>  
  
     <span data-ttu-id="f8ec0-142">Zostanie otwarty projektant formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-142">The Windows Forms Designer opens.</span></span>  
  
## <a name="adding-the-linq-to-sql-assembly-reference"></a><span data-ttu-id="f8ec0-143">Dodawanie LINQ do SQL odwołanie do zestawu</span><span class="sxs-lookup"><span data-stu-id="f8ec0-143">Adding the LINQ to SQL Assembly Reference</span></span>  
 <span data-ttu-id="f8ec0-144">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Zestaw nie jest dołączony do standardowego szablonu aplikacji formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-144">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] assembly is not included in the standard Windows Forms Application template.</span></span> <span data-ttu-id="f8ec0-145">Należy dodać zestaw samodzielnie, zgodnie z objaśnieniem w poniższych krokach:</span><span class="sxs-lookup"><span data-stu-id="f8ec0-145">You will have to add the assembly yourself, as explained in the following steps:</span></span>  
  
#### <a name="to-add-systemdatalinqdll"></a><span data-ttu-id="f8ec0-146">Aby dodać System.Data.Linq.dll</span><span class="sxs-lookup"><span data-stu-id="f8ec0-146">To add System.Data.Linq.dll</span></span>  
  
1.  <span data-ttu-id="f8ec0-147">W **Eksploratora rozwiązań**, kliknij przycisk **Pokaż wszystkie pliki**.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-147">In **Solution Explorer**, click **Show All Files**.</span></span>  
  
2.  <span data-ttu-id="f8ec0-148">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania**, a następnie kliknij przycisk **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-148">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
3.  <span data-ttu-id="f8ec0-149">W **Dodaj odwołanie** okno dialogowe, kliknij przycisk **.NET**, kliknij zestaw System.Data.Linq, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-149">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="f8ec0-150">Zestaw został dodany do projektu.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-150">The assembly is added to the project.</span></span>  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a><span data-ttu-id="f8ec0-151">Dodawanie plików kodu Northwind do projektu</span><span class="sxs-lookup"><span data-stu-id="f8ec0-151">Adding the Northwind Code File to the Project</span></span>  
 <span data-ttu-id="f8ec0-152">W tym kroku przyjęto założenie, użycie narzędzia SqlMetal do wygenerowania pliku kodu z przykładowej bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-152">This step assumes that you have used the SqlMetal tool to generate a code file from the Northwind sample database.</span></span> <span data-ttu-id="f8ec0-153">Aby uzyskać więcej informacji zobacz sekcję wymagań wstępnych we wcześniejszej części tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-153">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a><span data-ttu-id="f8ec0-154">Aby dodać plik kodu northwind do projektu</span><span class="sxs-lookup"><span data-stu-id="f8ec0-154">To add the northwind code file to the project</span></span>  
  
1.  <span data-ttu-id="f8ec0-155">Na **projektu** menu, kliknij przycisk **Dodaj istniejący element**.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-155">On the **Project** menu, click **Add Existing Item**.</span></span>  
  
2.  <span data-ttu-id="f8ec0-156">W **Dodaj istniejący element** okno dialogowe, Przenieś do c:\linqtest3\northwind.vb, a następnie kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-156">In the **Add Existing Item** dialog box, move to c:\linqtest3\northwind.vb, and then click **Add**.</span></span>  
  
     <span data-ttu-id="f8ec0-157">Plik northwind.vb zostanie dodany do projektu.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-157">The northwind.vb file is added to the project.</span></span>  
  
## <a name="creating-a-database-connection"></a><span data-ttu-id="f8ec0-158">Tworzenie połączenia z bazą danych</span><span class="sxs-lookup"><span data-stu-id="f8ec0-158">Creating a Database Connection</span></span>  
 <span data-ttu-id="f8ec0-159">W tym kroku definiowane połączenie z przykładowej bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-159">In this step, you define the connection to the Northwind sample database.</span></span> <span data-ttu-id="f8ec0-160">W tym przewodniku zastosowano "c:\linqtest3\northwnd.mdf" jako ścieżka.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-160">This walkthrough uses "c:\linqtest3\northwnd.mdf" as the path.</span></span>  
  
#### <a name="to-create-the-database-connection"></a><span data-ttu-id="f8ec0-161">Aby utworzyć połączenie z bazą danych</span><span class="sxs-lookup"><span data-stu-id="f8ec0-161">To create the database connection</span></span>  
  
1.  <span data-ttu-id="f8ec0-162">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **Form1.vb**, a następnie kliknij przycisk **kod widoku**.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-162">In **Solution Explorer**, right-click **Form1.vb**, and then click **View Code**.</span></span>  
  
     <span data-ttu-id="f8ec0-163">`Class Form1`zostanie wyświetlony w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-163">`Class Form1` appears in the code editor.</span></span>  
  
2.  <span data-ttu-id="f8ec0-164">Wpisz następujący kod do `Form1` blok kodu:</span><span class="sxs-lookup"><span data-stu-id="f8ec0-164">Type the following code into the `Form1` code block:</span></span>  
  
     [!code-vb[DLinqWalk4VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#1)]  
  
## <a name="setting-up-the-user-interface"></a><span data-ttu-id="f8ec0-165">Konfigurowanie interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="f8ec0-165">Setting up the User Interface</span></span>  
 <span data-ttu-id="f8ec0-166">W tym zadaniu tworzenia interfejsu, aby użytkownicy można wykonać procedur składowanych dostępu do danych w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-166">In this task you create an interface so that users can execute stored procedures to access data in the database.</span></span> <span data-ttu-id="f8ec0-167">W aplikacji, który tworzysz z tym przewodnikiem użytkownicy mogą korzystać tylko za pomocą procedur składowanych osadzone w aplikacji, w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-167">In the application that you are developing with this walkthrough, users can access data in the database only by using the stored procedures embedded in the application.</span></span>  
  
#### <a name="to-set-up-the-user-interface"></a><span data-ttu-id="f8ec0-168">Aby skonfigurować interfejs użytkownika</span><span class="sxs-lookup"><span data-stu-id="f8ec0-168">To set up the user interface</span></span>  
  
1.  <span data-ttu-id="f8ec0-169">Projektant Forms powrotu do systemu Windows (**Form1.vb[Design]**).</span><span class="sxs-lookup"><span data-stu-id="f8ec0-169">Return to the Windows Forms Designer (**Form1.vb[Design]**).</span></span>  
  
2.  <span data-ttu-id="f8ec0-170">Na **widoku** menu, kliknij przycisk **przybornika**.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-170">On the **View** menu, click **Toolbox**.</span></span>  
  
     <span data-ttu-id="f8ec0-171">Otwiera przybornika.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-171">The toolbox opens.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f8ec0-172">Kliknij przycisk **autohide —** pinezki, aby utrzymać otwarte przybornika podczas przeprowadzania pozostałe kroki w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-172">Click the **AutoHide** pushpin to keep the toolbox open while you perform the remaining steps in this section.</span></span>  
  
3.  <span data-ttu-id="f8ec0-173">Przeciągnij z przybornika do dwóch przycisków, dwa pola tekstowe i dwie etykiety **Form1**.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-173">Drag two buttons, two text boxes, and two labels from the toolbox onto **Form1**.</span></span>  
  
     <span data-ttu-id="f8ec0-174">Rozmieszczanie formantów jak towarzyszący ilustracji.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-174">Arrange the controls as in the accompanying illustration.</span></span> <span data-ttu-id="f8ec0-175">Rozwiń węzeł **Form1** tak, aby formanty łatwo Dopasuj.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-175">Expand **Form1** so that the controls fit easily.</span></span>  
  
4.  <span data-ttu-id="f8ec0-176">Kliknij prawym przyciskiem myszy **Label1**, a następnie kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-176">Right-click **Label1**, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="f8ec0-177">Zmień **tekst** właściwość z **Label1** do **wprowadź OrderID:**.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-177">Change the **Text** property from **Label1** to **Enter OrderID:**.</span></span>  
  
6.  <span data-ttu-id="f8ec0-178">W ten sam sposób dla **Label2**, zmień **tekst** właściwość z **Label2** do **wprowadź CustomerID:**.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-178">In the same way for **Label2**, change the **Text** property from **Label2** to **Enter CustomerID:**.</span></span>  
  
7.  <span data-ttu-id="f8ec0-179">W ten sam sposób, zmień **tekst** właściwość **Button1** do **szczegółów zamówienia**.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-179">In the same way, change the **Text** property for **Button1** to **Order Details**.</span></span>  
  
8.  <span data-ttu-id="f8ec0-180">Zmień **tekst** właściwość **Button2** do **historii zamówień**.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-180">Change the **Text** property for **Button2** to **Order History**.</span></span>  
  
     <span data-ttu-id="f8ec0-181">Rozszerzenia kontrolki przycisku, dzięki czemu cały tekst jest widoczny.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-181">Widen the button controls so that all the text is visible.</span></span>  
  
#### <a name="to-handle-button-clicks"></a><span data-ttu-id="f8ec0-182">Do obsługi kliknięcia przycisków</span><span class="sxs-lookup"><span data-stu-id="f8ec0-182">To handle button clicks</span></span>  
  
1.  <span data-ttu-id="f8ec0-183">Kliknij dwukrotnie **szczegółów zamówienia** na **Form1** utworzyć `Button1` obsługi zdarzeń i otworzyć edytora kodu.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-183">Double-click **Order Details** on **Form1** to create the `Button1` event handler and open the code editor.</span></span>  
  
2.  <span data-ttu-id="f8ec0-184">Wpisz następujący kod do `Button1` obsługi:</span><span class="sxs-lookup"><span data-stu-id="f8ec0-184">Type the following code into the `Button1` handler:</span></span>  
  
     [!code-vb[DLinqWalk4VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#2)]  
  
3.  <span data-ttu-id="f8ec0-185">Teraz kliknij dwukrotnie **Button2** na Form1 utworzyć `Button2` obsługi zdarzeń i otworzyć edytora kodu.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-185">Now double-click **Button2** on Form1 to create the `Button2` event handler and open the code editor.</span></span>  
  
4.  <span data-ttu-id="f8ec0-186">Wpisz następujący kod do `Button2` obsługi:</span><span class="sxs-lookup"><span data-stu-id="f8ec0-186">Type the following code into the `Button2` handler:</span></span>  
  
     [!code-vb[DLinqWalk4VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#3)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="f8ec0-187">Testowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="f8ec0-187">Testing the Application</span></span>  
 <span data-ttu-id="f8ec0-188">Teraz nadszedł czas, aby przetestować aplikację.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-188">Now it is time to test your application.</span></span> <span data-ttu-id="f8ec0-189">Należy pamiętać, że kontakt z magazynu danych jest ograniczona do dowolnej akcji może zająć dwie procedury składowanej.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-189">Note that your contact with the datastore is limited to whatever actions the two stored procedures can take.</span></span> <span data-ttu-id="f8ec0-190">Te akcje są do zwrócenia produkty uwzględnione wszelkie orderID wprowadzona lub do zwrócenia historii produktów, uporządkowany w celu żadnych CustomerID wprowadzasz.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-190">Those actions are to return the products included for any orderID you enter, or to return a history of products ordered for any CustomerID you enter.</span></span>  
  
#### <a name="to-test-the-application"></a><span data-ttu-id="f8ec0-191">Aby przetestować aplikację</span><span class="sxs-lookup"><span data-stu-id="f8ec0-191">To test the application</span></span>  
  
1.  <span data-ttu-id="f8ec0-192">Naciśnij klawisz F5, aby rozpocząć debugowania.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-192">Press F5 to start debugging.</span></span>  
  
     <span data-ttu-id="f8ec0-193">Zostanie wyświetlone Form1.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-193">Form1 appears.</span></span>  
  
2.  <span data-ttu-id="f8ec0-194">W **wprowadź OrderID** wpisz **10249** , a następnie kliknij przycisk **szczegółów zamówienia**.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-194">In the **Enter OrderID** box, type **10249** and then click **Order Details**.</span></span>  
  
     <span data-ttu-id="f8ec0-195">Okno komunikatu wymieniono produkty uwzględnione w kolejności 10249.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-195">A message box lists the products included in order 10249.</span></span>  
  
     <span data-ttu-id="f8ec0-196">Kliknij przycisk **OK** aby zamknąć okno komunikatu.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-196">Click **OK** to close the message box.</span></span>  
  
3.  <span data-ttu-id="f8ec0-197">W **wprowadź CustomerID** wpisz `ALFKI`, a następnie kliknij przycisk **historii zamówień**.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-197">In the **Enter CustomerID** box, type `ALFKI`, and then click **Order History**.</span></span>  
  
     <span data-ttu-id="f8ec0-198">Okno komunikatu listy historii zamówień klienta ALFKI.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-198">A message box lists the order history for customer ALFKI.</span></span>  
  
     <span data-ttu-id="f8ec0-199">Kliknij przycisk **OK** aby zamknąć okno komunikatu.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-199">Click **OK** to close the message box.</span></span>  
  
4.  <span data-ttu-id="f8ec0-200">W **wprowadź OrderID** wpisz `123`, a następnie kliknij przycisk **szczegółów zamówienia**.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-200">In the **Enter OrderID** box, type `123`, and then click **Order Details**.</span></span>  
  
     <span data-ttu-id="f8ec0-201">Okno komunikatu Wyświetla "Żadne wyniki".</span><span class="sxs-lookup"><span data-stu-id="f8ec0-201">A message box displays "No results."</span></span>  
  
     <span data-ttu-id="f8ec0-202">Kliknij przycisk **OK** aby zamknąć okno komunikatu.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-202">Click **OK** to close the message box.</span></span>  
  
5.  <span data-ttu-id="f8ec0-203">Na **debugowania** menu, kliknij przycisk **Zatrzymaj debugowanie**.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-203">On the **Debug** menu, click **Stop debugging**.</span></span>  
  
     <span data-ttu-id="f8ec0-204">Powoduje zamknięcie sesji debugowania.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-204">The debug session closes.</span></span>  
  
6.  <span data-ttu-id="f8ec0-205">Jeśli zakończysz eksperymentowanie, możesz kliknąć **Zamknij projekt** na **pliku** menu i zapisać projekt po wyświetleniu monitu.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-205">If you have finished experimenting, you can click **Close Project** on the **File** menu, and save your project when you are prompted.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="f8ec0-206">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="f8ec0-206">Next Steps</span></span>  
 <span data-ttu-id="f8ec0-207">Wprowadzenie pewnych zmian można zwiększyć ten projekt.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-207">You can enhance this project by making some changes.</span></span> <span data-ttu-id="f8ec0-208">Na przykład możesz wyświetlić listę dostępnych procedur składowanych w polu listy i użytkownik powinien wybrać, które procedury musisz wykonać.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-208">For example, you could list available stored procedures in a list box and have the user select which procedures to execute.</span></span> <span data-ttu-id="f8ec0-209">Można również strumienia wyjściowego raportów do pliku tekstowego.</span><span class="sxs-lookup"><span data-stu-id="f8ec0-209">You could also stream the output of the reports to a text file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8ec0-210">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f8ec0-210">See Also</span></span>  
 [<span data-ttu-id="f8ec0-211">Learning przez — wskazówki</span><span class="sxs-lookup"><span data-stu-id="f8ec0-211">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)  
 [<span data-ttu-id="f8ec0-212">Procedury składowane</span><span class="sxs-lookup"><span data-stu-id="f8ec0-212">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
