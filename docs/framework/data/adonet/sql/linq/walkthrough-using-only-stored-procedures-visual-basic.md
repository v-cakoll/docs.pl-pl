---
title: 'Przewodnik: Używanie tylko procedur składowanych (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: 5a736a30-ba66-4adb-b87c-57d19476e862
ms.openlocfilehash: 686d1797666c36f47d1ab0244754bbf2daf97eaf
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59188581"
---
# <a name="walkthrough-using-only-stored-procedures-visual-basic"></a><span data-ttu-id="7b872-102">Przewodnik: Używanie tylko procedur składowanych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b872-102">Walkthrough: Using Only Stored Procedures (Visual Basic)</span></span>
<span data-ttu-id="7b872-103">Ten przewodnik zawiera podstawowe end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenariusz do uzyskiwania dostępu do danych za pomocą procedury składowane tylko.</span><span class="sxs-lookup"><span data-stu-id="7b872-103">This walkthrough provides a basic end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario for accessing data by using stored procedures only.</span></span> <span data-ttu-id="7b872-104">To podejście jest często używana przez administratorów baz danych, aby ograniczyć sposób dostępu do magazynu danych.</span><span class="sxs-lookup"><span data-stu-id="7b872-104">This approach is often used by database administrators to limit how the datastore is accessed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7b872-105">Można również użyć procedur składowanych w programie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikacji, aby zastąpić domyślne zachowanie, szczególnie w przypadku `Create`, `Update`, i `Delete` procesów.</span><span class="sxs-lookup"><span data-stu-id="7b872-105">You can also use stored procedures in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications to override default behavior, especially for `Create`, `Update`, and `Delete` processes.</span></span> <span data-ttu-id="7b872-106">Aby uzyskać więcej informacji, zobacz [Dostosowywanie Insert, Update i operacje usuwania](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="7b872-106">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
  
 <span data-ttu-id="7b872-107">Do celów tego przewodnika będziesz używać dwóch metod, które zostały zmapowane do procedur składowanych w bazie danych Northwind: CustOrdersDetail i CustOrderHist.</span><span class="sxs-lookup"><span data-stu-id="7b872-107">For purposes of this walkthrough, you will use two methods that have been mapped to stored procedures in the Northwind sample database: CustOrdersDetail and CustOrderHist.</span></span> <span data-ttu-id="7b872-108">Mapowanie występuje po uruchomieniu narzędzia wiersza polecenia SqlMetal, aby wygenerować plik języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="7b872-108">The mapping occurs when you run the SqlMetal command-line tool to generate a Visual Basic file.</span></span> <span data-ttu-id="7b872-109">Aby uzyskać więcej informacji zobacz sekcję wymagania wstępne w dalszej części tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="7b872-109">For more information, see the Prerequisites section later in this walkthrough.</span></span>  
  
 <span data-ttu-id="7b872-110">W tym przewodniku nie zależą od [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7b872-110">This walkthrough does not rely on the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)].</span></span> <span data-ttu-id="7b872-111">Deweloperzy korzystający z programu Visual Studio można również użyć [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] do implementowania procedury składowanej.</span><span class="sxs-lookup"><span data-stu-id="7b872-111">Developers using Visual Studio can also use the [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] to implement stored procedure functionality.</span></span> <span data-ttu-id="7b872-112">Zobacz [LINQ to SQL Tools w programie Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span><span class="sxs-lookup"><span data-stu-id="7b872-112">See [LINQ to SQL Tools in Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="7b872-113">W tym przewodniku została napisana przy użyciu ustawień środowiska deweloperskiego Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="7b872-113">This walkthrough was written by using Visual Basic Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="7b872-114">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="7b872-114">Prerequisites</span></span>  
 <span data-ttu-id="7b872-115">Ten przewodnik wymaga następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="7b872-115">This walkthrough requires the following:</span></span>  
  
-   <span data-ttu-id="7b872-116">W tym przewodniku używa dedykowanego folder ("c:\linqtest3") do przechowywania plików.</span><span class="sxs-lookup"><span data-stu-id="7b872-116">This walkthrough uses a dedicated folder ("c:\linqtest3") to hold files.</span></span> <span data-ttu-id="7b872-117">Przed rozpoczęciem instruktażu, należy utworzyć ten folder.</span><span class="sxs-lookup"><span data-stu-id="7b872-117">Create this folder before you begin the walkthrough.</span></span>  
  
-   <span data-ttu-id="7b872-118">Przykładowa bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="7b872-118">The Northwind sample database.</span></span>  
  
     <span data-ttu-id="7b872-119">Jeśli nie masz tej bazy danych na komputerze deweloperskim, możesz ją pobrać z witryny pobierania firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="7b872-119">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="7b872-120">Aby uzyskać instrukcje, zobacz [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="7b872-120">For instructions, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span> <span data-ttu-id="7b872-121">Po pobraniu bazy danych, skopiuj plik northwnd.mdf do folderu c:\linqtest3.</span><span class="sxs-lookup"><span data-stu-id="7b872-121">After you have downloaded the database, copy the northwnd.mdf file to the c:\linqtest3 folder.</span></span>  
  
-   <span data-ttu-id="7b872-122">Plik kodu języka Visual Basic, wygenerowany na podstawie bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="7b872-122">A Visual Basic code file generated from the Northwind database.</span></span>  
  
     <span data-ttu-id="7b872-123">Ten instruktaż został napisany za pomocą narzędzia SqlMetal za pomocą następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="7b872-123">This walkthrough was written by using the SqlMetal tool with the following command line:</span></span>  
  
     **<span data-ttu-id="7b872-124">Program sqlmetal /code:"c:\linqtest3\northwind.vb" /language:vb "c:\linqtest3\northwnd.mdf" /sprocs /functions / pluralize</span><span class="sxs-lookup"><span data-stu-id="7b872-124">sqlmetal /code:"c:\linqtest3\northwind.vb" /language:vb "c:\linqtest3\northwnd.mdf" /sprocs /functions /pluralize</span></span>**  
  
     <span data-ttu-id="7b872-125">Aby uzyskać więcej informacji, zobacz [SqlMetal.exe (narzędzie generowania kodu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="7b872-125">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="7b872-126">Omówienie</span><span class="sxs-lookup"><span data-stu-id="7b872-126">Overview</span></span>  
 <span data-ttu-id="7b872-127">Ten przewodnik składa się z sześciu głównych zadań:</span><span class="sxs-lookup"><span data-stu-id="7b872-127">This walkthrough consists of six main tasks:</span></span>  
  
-   <span data-ttu-id="7b872-128">Konfigurowanie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] rozwiązania w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7b872-128">Setting up the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>  
  
-   <span data-ttu-id="7b872-129">Trwa dodawanie zestawu System.Data.Linq do projektu.</span><span class="sxs-lookup"><span data-stu-id="7b872-129">Adding the System.Data.Linq assembly to the project.</span></span>  
  
-   <span data-ttu-id="7b872-130">Dodawanie pliku kodu bazy danych do projektu.</span><span class="sxs-lookup"><span data-stu-id="7b872-130">Adding the database code file to the project.</span></span>  
  
-   <span data-ttu-id="7b872-131">Tworzenie połączenia z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="7b872-131">Creating a connection to the database.</span></span>  
  
-   <span data-ttu-id="7b872-132">Konfigurowanie interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="7b872-132">Setting up the user interface.</span></span>  
  
-   <span data-ttu-id="7b872-133">Uruchamianie i testowanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7b872-133">Running and testing the application.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="7b872-134">Tworzenie składnika LINQ to SQL rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="7b872-134">Creating a LINQ to SQL Solution</span></span>  
 <span data-ttu-id="7b872-135">W tym pierwszym zadaniu tworzyć rozwiązania programu Visual Studio, który zawiera niezbędne odwołania, aby skompilować i uruchomić [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu.</span><span class="sxs-lookup"><span data-stu-id="7b872-135">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="7b872-136">Aby utworzyć składnika LINQ to SQL rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="7b872-136">To create a LINQ to SQL solution</span></span>  
  
1.  <span data-ttu-id="7b872-137">W programie Visual Studio **pliku** menu, kliknij przycisk **nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="7b872-137">On the Visual Studio **File** menu, click **New Project**.</span></span>  
  
2.  <span data-ttu-id="7b872-138">W **typów projektów** okienka **nowy projekt** okna dialogowego rozwiń **języka Visual Basic**, a następnie kliknij przycisk **Windows**.</span><span class="sxs-lookup"><span data-stu-id="7b872-138">In the **Project types** pane in the **New Project** dialog box, expand **Visual Basic**, and then click **Windows**.</span></span>  
  
3.  <span data-ttu-id="7b872-139">W **szablony** okienku kliknij **aplikacja interfejsu Windows Forms**.</span><span class="sxs-lookup"><span data-stu-id="7b872-139">In the **Templates** pane, click **Windows Forms Application**.</span></span>  
  
4.  <span data-ttu-id="7b872-140">W **nazwa** wpisz **SprocOnlyApp**.</span><span class="sxs-lookup"><span data-stu-id="7b872-140">In the **Name** box, type **SprocOnlyApp**.</span></span>  
  
5.  <span data-ttu-id="7b872-141">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="7b872-141">Click **OK**.</span></span>  
  
     <span data-ttu-id="7b872-142">Zostanie otwarty projektant formularzy Windows.</span><span class="sxs-lookup"><span data-stu-id="7b872-142">The Windows Forms Designer opens.</span></span>  
  
## <a name="adding-the-linq-to-sql-assembly-reference"></a><span data-ttu-id="7b872-143">Dodawanie programu LINQ do SQL odwołanie do zestawu</span><span class="sxs-lookup"><span data-stu-id="7b872-143">Adding the LINQ to SQL Assembly Reference</span></span>  
 <span data-ttu-id="7b872-144">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Moduł nie jest dołączony do standardowego szablonu aplikacja interfejsu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="7b872-144">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] assembly is not included in the standard Windows Forms Application template.</span></span> <span data-ttu-id="7b872-145">Trzeba będzie dodać zestaw samodzielnie, zgodnie z opisem w poniższych krokach:</span><span class="sxs-lookup"><span data-stu-id="7b872-145">You will have to add the assembly yourself, as explained in the following steps:</span></span>  
  
#### <a name="to-add-systemdatalinqdll"></a><span data-ttu-id="7b872-146">To add System.Data.Linq.dll</span><span class="sxs-lookup"><span data-stu-id="7b872-146">To add System.Data.Linq.dll</span></span>  
  
1.  <span data-ttu-id="7b872-147">W **Eksploratora rozwiązań**, kliknij przycisk **Pokaż wszystkie pliki**.</span><span class="sxs-lookup"><span data-stu-id="7b872-147">In **Solution Explorer**, click **Show All Files**.</span></span>  
  
2.  <span data-ttu-id="7b872-148">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania**, a następnie kliknij przycisk **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="7b872-148">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
3.  <span data-ttu-id="7b872-149">W **Dodaj odwołanie** okno dialogowe, kliknij przycisk **.NET**, kliknij zestaw System.Data.Linq, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="7b872-149">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="7b872-150">Zestaw został dodany do projektu.</span><span class="sxs-lookup"><span data-stu-id="7b872-150">The assembly is added to the project.</span></span>  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a><span data-ttu-id="7b872-151">Dodawanie pliku Northwind kodu do projektu</span><span class="sxs-lookup"><span data-stu-id="7b872-151">Adding the Northwind Code File to the Project</span></span>  
 <span data-ttu-id="7b872-152">Tego kroku przyjęto założenie, że trzeba użyć narzędzia SqlMetal do generowania pliku kodu z przykładowej bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="7b872-152">This step assumes that you have used the SqlMetal tool to generate a code file from the Northwind sample database.</span></span> <span data-ttu-id="7b872-153">Aby uzyskać więcej informacji zobacz sekcję wymagania wstępne we wcześniejszej części tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="7b872-153">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a><span data-ttu-id="7b872-154">Aby dodać plik kodu northwind do projektu</span><span class="sxs-lookup"><span data-stu-id="7b872-154">To add the northwind code file to the project</span></span>  
  
1.  <span data-ttu-id="7b872-155">Na **projektu** menu, kliknij przycisk **Dodaj istniejący element**.</span><span class="sxs-lookup"><span data-stu-id="7b872-155">On the **Project** menu, click **Add Existing Item**.</span></span>  
  
2.  <span data-ttu-id="7b872-156">W **Dodaj istniejący element** przenieść c:\linqtest3\northwind.vb okno dialogowe, a następnie kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="7b872-156">In the **Add Existing Item** dialog box, move to c:\linqtest3\northwind.vb, and then click **Add**.</span></span>  
  
     <span data-ttu-id="7b872-157">Plik northwind.vb zostanie dodany do projektu.</span><span class="sxs-lookup"><span data-stu-id="7b872-157">The northwind.vb file is added to the project.</span></span>  
  
## <a name="creating-a-database-connection"></a><span data-ttu-id="7b872-158">Tworzenie połączenia z bazą danych</span><span class="sxs-lookup"><span data-stu-id="7b872-158">Creating a Database Connection</span></span>  
 <span data-ttu-id="7b872-159">W tym kroku zdefiniujesz połączenia z przykładową bazą danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="7b872-159">In this step, you define the connection to the Northwind sample database.</span></span> <span data-ttu-id="7b872-160">W tym instruktażu wykorzystano "c:\linqtest3\northwnd.mdf", jako ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="7b872-160">This walkthrough uses "c:\linqtest3\northwnd.mdf" as the path.</span></span>  
  
#### <a name="to-create-the-database-connection"></a><span data-ttu-id="7b872-161">Aby utworzyć połączenie z bazą danych</span><span class="sxs-lookup"><span data-stu-id="7b872-161">To create the database connection</span></span>  
  
1.  <span data-ttu-id="7b872-162">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **Form1.vb**, a następnie kliknij przycisk **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="7b872-162">In **Solution Explorer**, right-click **Form1.vb**, and then click **View Code**.</span></span>  
  
     `Class Form1` <span data-ttu-id="7b872-163">zostanie wyświetlony w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="7b872-163">appears in the code editor.</span></span>  
  
2.  <span data-ttu-id="7b872-164">Wpisz następujący kod do `Form1` blok kodu:</span><span class="sxs-lookup"><span data-stu-id="7b872-164">Type the following code into the `Form1` code block:</span></span>  
  
     [!code-vb[DLinqWalk4VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#1)]  
  
## <a name="setting-up-the-user-interface"></a><span data-ttu-id="7b872-165">Konfigurowanie interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="7b872-165">Setting up the User Interface</span></span>  
 <span data-ttu-id="7b872-166">W tym zadaniu utworzysz interfejs, dzięki czemu użytkownicy mogą wykonać procedur składowanych na dostęp do danych w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="7b872-166">In this task you create an interface so that users can execute stored procedures to access data in the database.</span></span> <span data-ttu-id="7b872-167">W aplikacji, która jest tworzona przy użyciu tego przewodnika użytkownicy mogą korzystać tylko przy użyciu procedur składowanych osadzone w aplikacji, dane z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="7b872-167">In the application that you are developing with this walkthrough, users can access data in the database only by using the stored procedures embedded in the application.</span></span>  
  
#### <a name="to-set-up-the-user-interface"></a><span data-ttu-id="7b872-168">Aby skonfigurować interfejs użytkownika</span><span class="sxs-lookup"><span data-stu-id="7b872-168">To set up the user interface</span></span>  
  
1.  <span data-ttu-id="7b872-169">Wróć do Windows Forms Designer (**Form1.vb[Design]**).</span><span class="sxs-lookup"><span data-stu-id="7b872-169">Return to the Windows Forms Designer (**Form1.vb[Design]**).</span></span>  
  
2.  <span data-ttu-id="7b872-170">Na **widoku** menu, kliknij przycisk **przybornika**.</span><span class="sxs-lookup"><span data-stu-id="7b872-170">On the **View** menu, click **Toolbox**.</span></span>  
  
     <span data-ttu-id="7b872-171">Przybornik zostaje otwarty.</span><span class="sxs-lookup"><span data-stu-id="7b872-171">The toolbox opens.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7b872-172">Kliknij przycisk **autoukrywania** pinezki, aby nie zamykaj przybornika podczas wykonywania pozostałych kroków w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="7b872-172">Click the **AutoHide** pushpin to keep the toolbox open while you perform the remaining steps in this section.</span></span>  
  
3.  <span data-ttu-id="7b872-173">Przeciągnij z przybornika na dwa przyciski, dwóch pól tekstowych i dwie etykiety **Form1**.</span><span class="sxs-lookup"><span data-stu-id="7b872-173">Drag two buttons, two text boxes, and two labels from the toolbox onto **Form1**.</span></span>  
  
     <span data-ttu-id="7b872-174">Kontrolki będą ułożone, jak pokazano na ilustracji towarzyszącej.</span><span class="sxs-lookup"><span data-stu-id="7b872-174">Arrange the controls as in the accompanying illustration.</span></span> <span data-ttu-id="7b872-175">Rozwiń **Form1** tak, aby łatwo mieści się kontrolki.</span><span class="sxs-lookup"><span data-stu-id="7b872-175">Expand **Form1** so that the controls fit easily.</span></span>  
  
4.  <span data-ttu-id="7b872-176">Kliknij prawym przyciskiem myszy **Label1**, a następnie kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="7b872-176">Right-click **Label1**, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="7b872-177">Zmiana **tekstu** właściwość **Label1** do **wprowadź OrderID:**.</span><span class="sxs-lookup"><span data-stu-id="7b872-177">Change the **Text** property from **Label1** to **Enter OrderID:**.</span></span>  
  
6.  <span data-ttu-id="7b872-178">W ten sam sposób, aby uzyskać **etykiety 2**, zmienić **tekstu** właściwość **etykiety 2** do **wprowadź CustomerID:**.</span><span class="sxs-lookup"><span data-stu-id="7b872-178">In the same way for **Label2**, change the **Text** property from **Label2** to **Enter CustomerID:**.</span></span>  
  
7.  <span data-ttu-id="7b872-179">W ten sam sposób, jak zmienić **tekstu** właściwość **Button1** do **Orderdetails**.</span><span class="sxs-lookup"><span data-stu-id="7b872-179">In the same way, change the **Text** property for **Button1** to **Order Details**.</span></span>  
  
8.  <span data-ttu-id="7b872-180">Zmiana **tekstu** właściwość **Button2** do **historii zamówień**.</span><span class="sxs-lookup"><span data-stu-id="7b872-180">Change the **Text** property for **Button2** to **Order History**.</span></span>  
  
     <span data-ttu-id="7b872-181">Tak, aby cały tekst jest widoczne, mogą zostać poszerzone formanty przycisków.</span><span class="sxs-lookup"><span data-stu-id="7b872-181">Widen the button controls so that all the text is visible.</span></span>  
  
#### <a name="to-handle-button-clicks"></a><span data-ttu-id="7b872-182">Do obsługi kliknięcia przycisków</span><span class="sxs-lookup"><span data-stu-id="7b872-182">To handle button clicks</span></span>  
  
1.  <span data-ttu-id="7b872-183">Kliknij dwukrotnie **Orderdetails** na **Form1** utworzyć `Button1` program obsługi zdarzeń i otworzyć Edytor kodu.</span><span class="sxs-lookup"><span data-stu-id="7b872-183">Double-click **Order Details** on **Form1** to create the `Button1` event handler and open the code editor.</span></span>  
  
2.  <span data-ttu-id="7b872-184">Wpisz następujący kod do `Button1` procedury obsługi:</span><span class="sxs-lookup"><span data-stu-id="7b872-184">Type the following code into the `Button1` handler:</span></span>  
  
     [!code-vb[DLinqWalk4VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#2)]  
  
3.  <span data-ttu-id="7b872-185">Teraz kliknij dwukrotnie **Button2** na formularzu Form1, aby utworzyć `Button2` program obsługi zdarzeń i otworzyć Edytor kodu.</span><span class="sxs-lookup"><span data-stu-id="7b872-185">Now double-click **Button2** on Form1 to create the `Button2` event handler and open the code editor.</span></span>  
  
4.  <span data-ttu-id="7b872-186">Wpisz następujący kod do `Button2` procedury obsługi:</span><span class="sxs-lookup"><span data-stu-id="7b872-186">Type the following code into the `Button2` handler:</span></span>  
  
     [!code-vb[DLinqWalk4VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#3)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="7b872-187">Testowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="7b872-187">Testing the Application</span></span>  
 <span data-ttu-id="7b872-188">Teraz nadszedł czas, aby przetestować aplikację.</span><span class="sxs-lookup"><span data-stu-id="7b872-188">Now it is time to test your application.</span></span> <span data-ttu-id="7b872-189">Należy pamiętać, że kontaktu z magazynu danych jest ograniczony do dowolnych akcje można wykonać dwie procedury składowane.</span><span class="sxs-lookup"><span data-stu-id="7b872-189">Note that your contact with the datastore is limited to whatever actions the two stored procedures can take.</span></span> <span data-ttu-id="7b872-190">Te akcje są do zwrócenia produktów, dostępny dla dowolnego orderID wprowadzona lub w celu zwrócenia historii produktów uporządkowane do dowolnego CustomerID wprowadzeniu.</span><span class="sxs-lookup"><span data-stu-id="7b872-190">Those actions are to return the products included for any orderID you enter, or to return a history of products ordered for any CustomerID you enter.</span></span>  
  
#### <a name="to-test-the-application"></a><span data-ttu-id="7b872-191">Aby przetestować aplikację</span><span class="sxs-lookup"><span data-stu-id="7b872-191">To test the application</span></span>  
  
1.  <span data-ttu-id="7b872-192">Naciśnij klawisz F5, aby rozpocząć debugowanie.</span><span class="sxs-lookup"><span data-stu-id="7b872-192">Press F5 to start debugging.</span></span>  
  
     <span data-ttu-id="7b872-193">Zostanie wyświetlony formularz Form1.</span><span class="sxs-lookup"><span data-stu-id="7b872-193">Form1 appears.</span></span>  
  
2.  <span data-ttu-id="7b872-194">W **wprowadź OrderID** wpisz **10249** a następnie kliknij przycisk **Orderdetails**.</span><span class="sxs-lookup"><span data-stu-id="7b872-194">In the **Enter OrderID** box, type **10249** and then click **Order Details**.</span></span>  
  
     <span data-ttu-id="7b872-195">Okno komunikatu Wyświetla listę produktów dołączone w kolejności 10249.</span><span class="sxs-lookup"><span data-stu-id="7b872-195">A message box lists the products included in order 10249.</span></span>  
  
     <span data-ttu-id="7b872-196">Kliknij przycisk **OK** aby zamknąć okno komunikatu.</span><span class="sxs-lookup"><span data-stu-id="7b872-196">Click **OK** to close the message box.</span></span>  
  
3.  <span data-ttu-id="7b872-197">W **wprowadź CustomerID** wpisz `ALFKI`, a następnie kliknij przycisk **historii zamówień**.</span><span class="sxs-lookup"><span data-stu-id="7b872-197">In the **Enter CustomerID** box, type `ALFKI`, and then click **Order History**.</span></span>  
  
     <span data-ttu-id="7b872-198">Okno komunikatu Wyświetla listę historii zamówień klienta Customer ALFKI.</span><span class="sxs-lookup"><span data-stu-id="7b872-198">A message box lists the order history for customer ALFKI.</span></span>  
  
     <span data-ttu-id="7b872-199">Kliknij przycisk **OK** aby zamknąć okno komunikatu.</span><span class="sxs-lookup"><span data-stu-id="7b872-199">Click **OK** to close the message box.</span></span>  
  
4.  <span data-ttu-id="7b872-200">W **wprowadź OrderID** wpisz `123`, a następnie kliknij przycisk **Orderdetails**.</span><span class="sxs-lookup"><span data-stu-id="7b872-200">In the **Enter OrderID** box, type `123`, and then click **Order Details**.</span></span>  
  
     <span data-ttu-id="7b872-201">Okno komunikatu Wyświetla "Brak wyników".</span><span class="sxs-lookup"><span data-stu-id="7b872-201">A message box displays "No results."</span></span>  
  
     <span data-ttu-id="7b872-202">Kliknij przycisk **OK** aby zamknąć okno komunikatu.</span><span class="sxs-lookup"><span data-stu-id="7b872-202">Click **OK** to close the message box.</span></span>  
  
5.  <span data-ttu-id="7b872-203">Na **debugowania** menu, kliknij przycisk **Zatrzymaj debugowanie**.</span><span class="sxs-lookup"><span data-stu-id="7b872-203">On the **Debug** menu, click **Stop debugging**.</span></span>  
  
     <span data-ttu-id="7b872-204">Powoduje zamknięcie sesji debugowania.</span><span class="sxs-lookup"><span data-stu-id="7b872-204">The debug session closes.</span></span>  
  
6.  <span data-ttu-id="7b872-205">Jeśli zakończysz, eksperymentowanie, możesz kliknąć **Zamknij projekt** na **pliku** menu i zapisać projekt, po wyświetleniu monitu.</span><span class="sxs-lookup"><span data-stu-id="7b872-205">If you have finished experimenting, you can click **Close Project** on the **File** menu, and save your project when you are prompted.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="7b872-206">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="7b872-206">Next Steps</span></span>  
 <span data-ttu-id="7b872-207">Ten projekt można zwiększyć, dokonując pewnych zmian.</span><span class="sxs-lookup"><span data-stu-id="7b872-207">You can enhance this project by making some changes.</span></span> <span data-ttu-id="7b872-208">Na przykład możesz wyświetlić listę dostępnych procedur składowanych w polu listy i użytkownik powinien wybrać, które procedury musisz wykonać.</span><span class="sxs-lookup"><span data-stu-id="7b872-208">For example, you could list available stored procedures in a list box and have the user select which procedures to execute.</span></span> <span data-ttu-id="7b872-209">Można również przesyłać strumieniowo dane wyjściowe raportów do pliku tekstowego.</span><span class="sxs-lookup"><span data-stu-id="7b872-209">You could also stream the output of the reports to a text file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b872-210">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7b872-210">See also</span></span>

- [<span data-ttu-id="7b872-211">Nauka przez przewodniki</span><span class="sxs-lookup"><span data-stu-id="7b872-211">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
- [<span data-ttu-id="7b872-212">Procedury składowane</span><span class="sxs-lookup"><span data-stu-id="7b872-212">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
