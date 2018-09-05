---
title: 'Porady: tworzenie i uruchamianie długotrwałego uruchamiania przepływu pracy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c0043c89-2192-43c9-986d-3ecec4dd8c9c
ms.openlocfilehash: 2c3368bc73d54f2848cad3c1086b1d9733205d2b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43556642"
---
# <a name="how-to-create-and-run-a-long-running-workflow"></a><span data-ttu-id="50b88-102">Porady: tworzenie i uruchamianie długotrwałego uruchamiania przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="50b88-102">How to: Create and Run a Long Running Workflow</span></span>
<span data-ttu-id="50b88-103">Jedną z centralnej funkcji Windows Workflow Foundation (WF) jest możliwość w środowisku uruchomieniowym zostaną zachowane, a następnie zwolnij bezczynności przepływy pracy z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="50b88-103">One of the central features of Windows Workflow Foundation (WF) is the runtime’s ability to persist and unload idle workflows to a database.</span></span> <span data-ttu-id="50b88-104">Kroki opisane w [porady: uruchamianie przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) przedstawiono podstawowe informacje dotyczące przepływu pracy hostingu, za pomocą aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="50b88-104">The steps in [How to: Run a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) demonstrated the basics of workflow hosting using a console application.</span></span> <span data-ttu-id="50b88-105">Przykłady zostały przedstawione począwszy od przepływów pracy, przepływ pracy cyklu życia obsługi i wznawianie zakładek.</span><span class="sxs-lookup"><span data-stu-id="50b88-105">Examples were shown of starting workflows, workflow lifecycle handlers, and resuming bookmarks.</span></span> <span data-ttu-id="50b88-106">W celu przedstawienia skutecznie trwałość przepływu pracy, wymagane jest bardziej złożone hosta przepływu pracy, która obsługuje uruchamianie i wznawianie wielu wystąpień przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="50b88-106">In order to demonstrate workflow persistence effectively, a more complex workflow host is required that supports starting and resuming multiple workflow instances.</span></span> <span data-ttu-id="50b88-107">Ten krok, w tym samouczku przedstawiono sposób tworzenia hosta formularzy Windows, aplikacji, która obsługuje uruchamianie i wznawianie wielu wystąpień przepływu pracy, trwałość przepływu pracy i stanowi podstawę dla zaawansowanych funkcji, takich jak śledzenie i przechowywania wersji, które są przedstawione w kolejnych krokach samouczka.</span><span class="sxs-lookup"><span data-stu-id="50b88-107">This step in the tutorial demonstrates how to create a Windows form host application that supports starting and resuming multiple workflow instances, workflow persistence, and provides a basis for the advanced features such as tracking and versioning that are demonstrated in subsequent tutorial steps.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="50b88-108">Ten samouczek kroku oraz kolejnych kroków należy używać wszystkich trzech typów przepływu pracy z [porady: Tworzenie przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="50b88-108">This tutorial step and the subsequent steps use all three workflow types from [How to: Create a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md).</span></span> <span data-ttu-id="50b88-109">Jeśli nie została ukończona wszystkich trzech typów możesz pobrać pełną wersję z procedury [Windows Workflow Foundation (WF45) — Samouczek wprowadzający](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="50b88-109">If you did not complete all three types you can download a completed version of the steps from [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="50b88-110">Aby pobrać wersję inną ukończone lub wyświetlić Przewodnik wideo tego samouczka, zobacz [Windows Workflow Foundation (WF45) — Samouczek wprowadzający](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="50b88-110">To download a completed version or view a video walkthrough of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
## <a name="in-this-topic"></a><span data-ttu-id="50b88-111">W tym temacie:</span><span class="sxs-lookup"><span data-stu-id="50b88-111">In this topic</span></span>  
  
-   [<span data-ttu-id="50b88-112">Aby utworzyć bazę danych stanów trwałych</span><span class="sxs-lookup"><span data-stu-id="50b88-112">To create the persistence database</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_CreatePersistenceDatabase)  
  
-   [<span data-ttu-id="50b88-113">Można dodać odwołania do zestawów DurableInstancing</span><span class="sxs-lookup"><span data-stu-id="50b88-113">To add the reference to the DurableInstancing assemblies</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_AddReference)  
  
-   [<span data-ttu-id="50b88-114">Aby utworzyć formularz hosta przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="50b88-114">To create the workflow host form</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_CreateForm)  
  
-   [<span data-ttu-id="50b88-115">Aby dodać właściwości i metody pomocnicze formularza</span><span class="sxs-lookup"><span data-stu-id="50b88-115">To add the properties and helper methods of the form</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_AddHelperMethods)  
  
-   [<span data-ttu-id="50b88-116">Aby skonfigurować Magazyn wystąpień przepływu pracy cyklu życia obsługi i rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="50b88-116">To configure the instance store, workflow lifecycle handlers, and extensions</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_ConfigureWorkflowApplication)  
  
-   [<span data-ttu-id="50b88-117">Aby włączyć uruchamianie i wznawianie wielu typów przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="50b88-117">To enable starting and resuming multiple workflow types</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_WorkflowVersionMap)  
  
-   [<span data-ttu-id="50b88-118">Aby uruchomić nowy przepływ pracy</span><span class="sxs-lookup"><span data-stu-id="50b88-118">To start a new workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_StartWorkflow)  
  
-   [<span data-ttu-id="50b88-119">Aby wznowić przepływ pracy</span><span class="sxs-lookup"><span data-stu-id="50b88-119">To resume a workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_ResumeWorkflow)  
  
-   [<span data-ttu-id="50b88-120">Aby zakończyć przepływ pracy</span><span class="sxs-lookup"><span data-stu-id="50b88-120">To terminate a workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_TerminateWorkflow)  
  
-   [<span data-ttu-id="50b88-121">Aby skompilować i uruchomić aplikację</span><span class="sxs-lookup"><span data-stu-id="50b88-121">To build and run the application</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_BuildAndRun)  
  
###  <a name="BKMK_CreatePersistenceDatabase"></a> <span data-ttu-id="50b88-122">Aby utworzyć bazę danych stanów trwałych</span><span class="sxs-lookup"><span data-stu-id="50b88-122">To create the persistence database</span></span>  
  
1.  <span data-ttu-id="50b88-123">Otwórz program SQL Server Management Studio i połącz się z serwera lokalnego, na przykład **. \SQLEXPRESS**.</span><span class="sxs-lookup"><span data-stu-id="50b88-123">Open SQL Server Management Studio and connect to the local server, for example **.\SQLEXPRESS**.</span></span> <span data-ttu-id="50b88-124">Kliknij prawym przyciskiem myszy **baz danych** węzła na serwerze lokalnym, a następnie wybierz **nową bazę danych**.</span><span class="sxs-lookup"><span data-stu-id="50b88-124">Right-click the **Databases** node on the local server, and select **New Database**.</span></span> <span data-ttu-id="50b88-125">Nadaj nazwę nowej bazy danych **WF45GettingStartedTutorial**, Zaakceptuj pozostałe wartości i wybierz **OK**.</span><span class="sxs-lookup"><span data-stu-id="50b88-125">Name the new database **WF45GettingStartedTutorial**, accept all other values, and select **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="50b88-126">Upewnij się, że masz **Create Database** uprawnień na serwerze lokalnym przed utworzeniem bazy danych.</span><span class="sxs-lookup"><span data-stu-id="50b88-126">Ensure that you have **Create Database** permission on the local server before creating the database.</span></span>  
  
2.  <span data-ttu-id="50b88-127">Wybierz **Otwórz**, **pliku** z **pliku** menu.</span><span class="sxs-lookup"><span data-stu-id="50b88-127">Choose **Open**, **File** from the **File** menu.</span></span> <span data-ttu-id="50b88-128">Przejdź do następującego folderu: `C:\Windows\Microsoft.NET\Framework\v4.0.30319\sql\en`</span><span class="sxs-lookup"><span data-stu-id="50b88-128">Browse to the following folder: `C:\Windows\Microsoft.NET\Framework\v4.0.30319\sql\en`</span></span>  
  
     <span data-ttu-id="50b88-129">Wybierz następujące dwa pliki, a następnie kliknij przycisk **Otwórz**.</span><span class="sxs-lookup"><span data-stu-id="50b88-129">Select the following two files and click **Open**.</span></span>  
  
    -   <span data-ttu-id="50b88-130">SqlWorkflowInstanceStoreLogic.sql</span><span class="sxs-lookup"><span data-stu-id="50b88-130">SqlWorkflowInstanceStoreLogic.sql</span></span>  
  
    -   <span data-ttu-id="50b88-131">SqlWorkflowInstanceStoreSchema.sql</span><span class="sxs-lookup"><span data-stu-id="50b88-131">SqlWorkflowInstanceStoreSchema.sql</span></span>  
  
3.  <span data-ttu-id="50b88-132">Wybierz **SqlWorkflowInstanceStoreSchema.sql** z **okna** menu.</span><span class="sxs-lookup"><span data-stu-id="50b88-132">Choose **SqlWorkflowInstanceStoreSchema.sql** from the **Window** menu.</span></span> <span data-ttu-id="50b88-133">Upewnij się, że **WF45GettingStartedTutorial** wybrano **baz danych dostępności** listy rozwijanej i wybierz polecenie **Execute** z **zapytania**menu.</span><span class="sxs-lookup"><span data-stu-id="50b88-133">Ensure that **WF45GettingStartedTutorial** is selected in the **Available Databases** drop-down and choose **Execute** from the **Query** menu.</span></span>  
  
4.  <span data-ttu-id="50b88-134">Wybierz **SqlWorkflowInstanceStoreLogic.sql** z **okna** menu.</span><span class="sxs-lookup"><span data-stu-id="50b88-134">Choose **SqlWorkflowInstanceStoreLogic.sql** from the **Window** menu.</span></span> <span data-ttu-id="50b88-135">Upewnij się, że **WF45GettingStartedTutorial** wybrano **baz danych dostępności** listy rozwijanej i wybierz polecenie **Execute** z **zapytania**menu.</span><span class="sxs-lookup"><span data-stu-id="50b88-135">Ensure that **WF45GettingStartedTutorial** is selected in the **Available Databases** drop-down and choose **Execute** from the **Query** menu.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="50b88-136">Należy wykonać dwa poprzednie kroki w odpowiedniej kolejności.</span><span class="sxs-lookup"><span data-stu-id="50b88-136">It is important to perform the previous two steps in the correct order.</span></span> <span data-ttu-id="50b88-137">Jeśli zapytania są wykonywane poza kolejnością, wystąpią błędy, a baza danych stanów trwałych nie jest poprawnie skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="50b88-137">If the queries are executed out of order, errors occur and the persistence database is not configured correctly.</span></span>  
  
###  <a name="BKMK_AddReference"></a> <span data-ttu-id="50b88-138">Można dodać odwołania do zestawów DurableInstancing</span><span class="sxs-lookup"><span data-stu-id="50b88-138">To add the reference to the DurableInstancing assemblies</span></span>  
  
1.  <span data-ttu-id="50b88-139">Kliknij prawym przyciskiem myszy **NumberGuessWorkflowHost** w **Eksploratora rozwiązań** i wybierz **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="50b88-139">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and select **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="50b88-140">Wybierz **zestawy** z **Dodaj odwołanie** listy, a typ `DurableInstancing` do **wyszukiwania zestawów** pole.</span><span class="sxs-lookup"><span data-stu-id="50b88-140">Select **Assemblies** from the **Add Reference** list, and type `DurableInstancing` into the **Search Assemblies** box.</span></span> <span data-ttu-id="50b88-141">Filtry zestawów i ułatwia wybierz żądane odwołania.</span><span class="sxs-lookup"><span data-stu-id="50b88-141">This filters the assemblies and makes the desired references easier to select.</span></span>  
  
3.  <span data-ttu-id="50b88-142">Zaznacz pole wyboru obok pozycji **System.Activities.DurableInstancing** i **System.Runtime.DurableInstancing** z **wyniki wyszukiwania** listy, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="50b88-142">Check the checkbox beside **System.Activities.DurableInstancing** and **System.Runtime.DurableInstancing** from the **Search Results** list, and click **OK**.</span></span>  
  
###  <a name="BKMK_CreateForm"></a> <span data-ttu-id="50b88-143">Aby utworzyć formularz hosta przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="50b88-143">To create the workflow host form</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="50b88-144">W tej procedurze opisano sposób dodawania i konfigurowania formularza ręcznie.</span><span class="sxs-lookup"><span data-stu-id="50b88-144">The steps in this procedure describe how to add and configure the form manually.</span></span> <span data-ttu-id="50b88-145">Jeśli to konieczne, można pobrać plików rozwiązania dla tego samouczka i Dodaj wypełniony formularz do projektu.</span><span class="sxs-lookup"><span data-stu-id="50b88-145">If desired, you can download the solution files for the tutorial and add the completed form to the project.</span></span> <span data-ttu-id="50b88-146">Aby pobrać pliki samouczka, zobacz [Windows Workflow Foundation (WF45) — Samouczek wprowadzający](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="50b88-146">To download the tutorial files, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span> <span data-ttu-id="50b88-147">Po pobraniu plików, kliknij prawym przyciskiem myszy **NumberGuessWorkflowHost** i wybierz polecenie **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="50b88-147">Once the files are downloaded, right-click **NumberGuessWorkflowHost** and choose **Add Reference**.</span></span> <span data-ttu-id="50b88-148">Dodaj odwołanie do **System.Windows.Forms** i **System.Drawing**.</span><span class="sxs-lookup"><span data-stu-id="50b88-148">Add a reference to **System.Windows.Forms** and **System.Drawing**.</span></span> <span data-ttu-id="50b88-149">Te odwołania są dodawane automatycznie po dodaniu nowego formularza z **Dodaj**, **nowy element** menu, ale musisz ręcznie dodać podczas importowania formularza.</span><span class="sxs-lookup"><span data-stu-id="50b88-149">These references are added automatically if you add a new form from the **Add**, **New Item** menu, but must be added manually when importing a form.</span></span> <span data-ttu-id="50b88-150">Po dodaniu odwołania, kliknij prawym przyciskiem myszy **NumberGuessWorkflowHost** w **Eksploratora rozwiązań** i wybierz polecenie **Dodaj**, **istniejący element**.</span><span class="sxs-lookup"><span data-stu-id="50b88-150">Once the references are added, right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **Existing Item**.</span></span> <span data-ttu-id="50b88-151">Przejdź do `Form` folderu w plikach projektu, wybierz opcję **WorkflowHostForm.cs** (lub **WorkflowHostForm.vb**) i kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="50b88-151">Browse to the `Form` folder in the project files, select **WorkflowHostForm.cs** (or **WorkflowHostForm.vb**), and click **Add**.</span></span> <span data-ttu-id="50b88-152">Jeśli decydujesz się zaimportować formularza, a następnie w dół do następnej sekcji, możesz pominąć [można dodać właściwości i metody pomocnicze formularza](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_AddHelperMethods).</span><span class="sxs-lookup"><span data-stu-id="50b88-152">If you choose to import the form, then you can skip down to the next section, [To add the properties and helper methods of the form](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_AddHelperMethods).</span></span>  
  
1.  <span data-ttu-id="50b88-153">Kliknij prawym przyciskiem myszy **NumberGuessWorkflowHost** w **Eksploratora rozwiązań** i wybierz polecenie **Dodaj**, **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="50b88-153">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **New Item**.</span></span>  
  
2.  <span data-ttu-id="50b88-154">W **zainstalowane** szablonów wybierz **formularza Windows**, typ `WorkflowHostForm` w **nazwa** polu, a następnie kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="50b88-154">In the **Installed** templates list, choose **Windows Form**, type `WorkflowHostForm` in the **Name** box, and click **Add**.</span></span>  
  
3.  <span data-ttu-id="50b88-155">W formularzu, należy skonfigurować następujące właściwości.</span><span class="sxs-lookup"><span data-stu-id="50b88-155">Configure the following properties on the form.</span></span>  
  
    |<span data-ttu-id="50b88-156">Właściwość</span><span class="sxs-lookup"><span data-stu-id="50b88-156">Property</span></span>|<span data-ttu-id="50b88-157">Wartość</span><span class="sxs-lookup"><span data-stu-id="50b88-157">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="50b88-158">FormBorderStyle</span><span class="sxs-lookup"><span data-stu-id="50b88-158">FormBorderStyle</span></span>|<span data-ttu-id="50b88-159">FixedSingle</span><span class="sxs-lookup"><span data-stu-id="50b88-159">FixedSingle</span></span>|  
    |<span data-ttu-id="50b88-160">MaximizeBox</span><span class="sxs-lookup"><span data-stu-id="50b88-160">MaximizeBox</span></span>|<span data-ttu-id="50b88-161">False</span><span class="sxs-lookup"><span data-stu-id="50b88-161">False</span></span>|  
    |<span data-ttu-id="50b88-162">Rozmiar</span><span class="sxs-lookup"><span data-stu-id="50b88-162">Size</span></span>|<span data-ttu-id="50b88-163">400, 420</span><span class="sxs-lookup"><span data-stu-id="50b88-163">400, 420</span></span>|  
  
4.  <span data-ttu-id="50b88-164">Dodaj następujące formanty do formularza w kolejności określonej i skonfigurować właściwości, zgodnie z instrukcją.</span><span class="sxs-lookup"><span data-stu-id="50b88-164">Add the following controls to the form in the order specified and configure the properties as directed.</span></span>  
  
    |<span data-ttu-id="50b88-165">Formant</span><span class="sxs-lookup"><span data-stu-id="50b88-165">Control</span></span>|<span data-ttu-id="50b88-166">Właściwość: wartość</span><span class="sxs-lookup"><span data-stu-id="50b88-166">Property: Value</span></span>|  
    |-------------|---------------------|  
    |<span data-ttu-id="50b88-167">**Przycisk**</span><span class="sxs-lookup"><span data-stu-id="50b88-167">**Button**</span></span>|<span data-ttu-id="50b88-168">Nazwa: NewGame</span><span class="sxs-lookup"><span data-stu-id="50b88-168">Name: NewGame</span></span><br /><br /> <span data-ttu-id="50b88-169">Lokalizacja: 13, 13</span><span class="sxs-lookup"><span data-stu-id="50b88-169">Location: 13, 13</span></span><br /><br /> <span data-ttu-id="50b88-170">Rozmiar: 75, 23</span><span class="sxs-lookup"><span data-stu-id="50b88-170">Size: 75, 23</span></span><br /><br /> <span data-ttu-id="50b88-171">Tekst: Gra nowy</span><span class="sxs-lookup"><span data-stu-id="50b88-171">Text: New Game</span></span>|  
    |<span data-ttu-id="50b88-172">**Etykieta**</span><span class="sxs-lookup"><span data-stu-id="50b88-172">**Label**</span></span>|<span data-ttu-id="50b88-173">Lokalizacja: 94, 18</span><span class="sxs-lookup"><span data-stu-id="50b88-173">Location: 94, 18</span></span><br /><br /> <span data-ttu-id="50b88-174">Tekst: Odgadnięcia liczba z przedziału od 1 do</span><span class="sxs-lookup"><span data-stu-id="50b88-174">Text: Guess a number from 1 to</span></span>|  
    |<span data-ttu-id="50b88-175">**ComboBox**</span><span class="sxs-lookup"><span data-stu-id="50b88-175">**ComboBox**</span></span>|<span data-ttu-id="50b88-176">Nazwa: NumberRange</span><span class="sxs-lookup"><span data-stu-id="50b88-176">Name: NumberRange</span></span><br /><br /> <span data-ttu-id="50b88-177">Parametr DropDownStyle: kontrolki DropDownList</span><span class="sxs-lookup"><span data-stu-id="50b88-177">DropDownStyle: DropDownList</span></span><br /><br /> <span data-ttu-id="50b88-178">Elementy: 10, 100, 1000</span><span class="sxs-lookup"><span data-stu-id="50b88-178">Items: 10, 100, 1000</span></span><br /><br /> <span data-ttu-id="50b88-179">Lokalizacja: 228, 12</span><span class="sxs-lookup"><span data-stu-id="50b88-179">Location: 228, 12</span></span><br /><br /> <span data-ttu-id="50b88-180">Rozmiar: 143, 21</span><span class="sxs-lookup"><span data-stu-id="50b88-180">Size: 143, 21</span></span>|  
    |<span data-ttu-id="50b88-181">**Etykieta**</span><span class="sxs-lookup"><span data-stu-id="50b88-181">**Label**</span></span>|<span data-ttu-id="50b88-182">Lokalizacja: 13, 43</span><span class="sxs-lookup"><span data-stu-id="50b88-182">Location: 13, 43</span></span><br /><br /> <span data-ttu-id="50b88-183">Tekst: Typ przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="50b88-183">Text: Workflow type</span></span>|  
    |<span data-ttu-id="50b88-184">**ComboBox**</span><span class="sxs-lookup"><span data-stu-id="50b88-184">**ComboBox**</span></span>|<span data-ttu-id="50b88-185">Nazwa: WorkflowType</span><span class="sxs-lookup"><span data-stu-id="50b88-185">Name: WorkflowType</span></span><br /><br /> <span data-ttu-id="50b88-186">Parametr DropDownStyle: kontrolki DropDownList</span><span class="sxs-lookup"><span data-stu-id="50b88-186">DropDownStyle: DropDownList</span></span><br /><br /> <span data-ttu-id="50b88-187">Elementy: SequentialNumberGuessWorkflow StateMachineNumberGuessWorkflow, FlowchartNumberGuessWorkflow,</span><span class="sxs-lookup"><span data-stu-id="50b88-187">Items: StateMachineNumberGuessWorkflow, FlowchartNumberGuessWorkflow, SequentialNumberGuessWorkflow</span></span><br /><br /> <span data-ttu-id="50b88-188">Lokalizacja: 94, 40</span><span class="sxs-lookup"><span data-stu-id="50b88-188">Location: 94, 40</span></span><br /><br /> <span data-ttu-id="50b88-189">Rozmiar: 277, 21</span><span class="sxs-lookup"><span data-stu-id="50b88-189">Size: 277, 21</span></span>|  
    |<span data-ttu-id="50b88-190">**Etykieta**</span><span class="sxs-lookup"><span data-stu-id="50b88-190">**Label**</span></span>|<span data-ttu-id="50b88-191">Nazwa: WorkflowVersion</span><span class="sxs-lookup"><span data-stu-id="50b88-191">Name: WorkflowVersion</span></span><br /><br /> <span data-ttu-id="50b88-192">Lokalizacja: 13, 362</span><span class="sxs-lookup"><span data-stu-id="50b88-192">Location: 13, 362</span></span><br /><br /> <span data-ttu-id="50b88-193">Tekst: Wersja przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="50b88-193">Text: Workflow version</span></span>|  
    |<span data-ttu-id="50b88-194">**GroupBox**</span><span class="sxs-lookup"><span data-stu-id="50b88-194">**GroupBox**</span></span>|<span data-ttu-id="50b88-195">Lokalizacja: 13, 67</span><span class="sxs-lookup"><span data-stu-id="50b88-195">Location: 13, 67</span></span><br /><br /> <span data-ttu-id="50b88-196">Rozmiar: 358, 287</span><span class="sxs-lookup"><span data-stu-id="50b88-196">Size: 358, 287</span></span><br /><br /> <span data-ttu-id="50b88-197">Tekst: gra</span><span class="sxs-lookup"><span data-stu-id="50b88-197">Text: Game</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="50b88-198">Dodając następujące elementy sterujące, umieść je w GroupBox.</span><span class="sxs-lookup"><span data-stu-id="50b88-198">When adding the following controls, put them into the GroupBox.</span></span>  
  
    |<span data-ttu-id="50b88-199">Formant</span><span class="sxs-lookup"><span data-stu-id="50b88-199">Control</span></span>|<span data-ttu-id="50b88-200">Właściwość: wartość</span><span class="sxs-lookup"><span data-stu-id="50b88-200">Property: Value</span></span>|  
    |-------------|---------------------|  
    |<span data-ttu-id="50b88-201">**Etykieta**</span><span class="sxs-lookup"><span data-stu-id="50b88-201">**Label**</span></span>|<span data-ttu-id="50b88-202">Lokalizacja: 7, 20</span><span class="sxs-lookup"><span data-stu-id="50b88-202">Location: 7, 20</span></span><br /><br /> <span data-ttu-id="50b88-203">Tekst: Identyfikator wystąpienia przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="50b88-203">Text: Workflow Instance Id</span></span>|  
    |<span data-ttu-id="50b88-204">**ComboBox**</span><span class="sxs-lookup"><span data-stu-id="50b88-204">**ComboBox**</span></span>|<span data-ttu-id="50b88-205">Nazwa: InstanceId</span><span class="sxs-lookup"><span data-stu-id="50b88-205">Name: InstanceId</span></span><br /><br /> <span data-ttu-id="50b88-206">Parametr DropDownStyle: kontrolki DropDownList</span><span class="sxs-lookup"><span data-stu-id="50b88-206">DropDownStyle: DropDownList</span></span><br /><br /> <span data-ttu-id="50b88-207">Lokalizacja: 121, 17</span><span class="sxs-lookup"><span data-stu-id="50b88-207">Location: 121, 17</span></span><br /><br /> <span data-ttu-id="50b88-208">Rozmiar: 227, 21</span><span class="sxs-lookup"><span data-stu-id="50b88-208">Size: 227, 21</span></span>|  
    |<span data-ttu-id="50b88-209">**Etykieta**</span><span class="sxs-lookup"><span data-stu-id="50b88-209">**Label**</span></span>|<span data-ttu-id="50b88-210">Lokalizacja: 7, 47</span><span class="sxs-lookup"><span data-stu-id="50b88-210">Location: 7, 47</span></span><br /><br /> <span data-ttu-id="50b88-211">Tekst: odgadnięcia</span><span class="sxs-lookup"><span data-stu-id="50b88-211">Text: Guess</span></span>|  
    |<span data-ttu-id="50b88-212">**TextBox**</span><span class="sxs-lookup"><span data-stu-id="50b88-212">**TextBox**</span></span>|<span data-ttu-id="50b88-213">Nazwa: odgadnięcia</span><span class="sxs-lookup"><span data-stu-id="50b88-213">Name: Guess</span></span><br /><br /> <span data-ttu-id="50b88-214">Lokalizacja: 50, 44</span><span class="sxs-lookup"><span data-stu-id="50b88-214">Location: 50, 44</span></span><br /><br /> <span data-ttu-id="50b88-215">Rozmiar: 65, 20</span><span class="sxs-lookup"><span data-stu-id="50b88-215">Size: 65, 20</span></span>|  
    |<span data-ttu-id="50b88-216">**Przycisk**</span><span class="sxs-lookup"><span data-stu-id="50b88-216">**Button**</span></span>|<span data-ttu-id="50b88-217">Nazwa: EnterGuess</span><span class="sxs-lookup"><span data-stu-id="50b88-217">Name: EnterGuess</span></span><br /><br /> <span data-ttu-id="50b88-218">Lokalizacja: 121, 42</span><span class="sxs-lookup"><span data-stu-id="50b88-218">Location: 121, 42</span></span><br /><br /> <span data-ttu-id="50b88-219">Rozmiar: 75, 23</span><span class="sxs-lookup"><span data-stu-id="50b88-219">Size: 75, 23</span></span><br /><br /> <span data-ttu-id="50b88-220">Tekst: Wprowadź odgadnięcia</span><span class="sxs-lookup"><span data-stu-id="50b88-220">Text: Enter Guess</span></span>|  
    |<span data-ttu-id="50b88-221">**Przycisk**</span><span class="sxs-lookup"><span data-stu-id="50b88-221">**Button**</span></span>|<span data-ttu-id="50b88-222">Nazwa: QuitGame</span><span class="sxs-lookup"><span data-stu-id="50b88-222">Name: QuitGame</span></span><br /><br /> <span data-ttu-id="50b88-223">Lokalizacja: 274, 42</span><span class="sxs-lookup"><span data-stu-id="50b88-223">Location: 274, 42</span></span><br /><br /> <span data-ttu-id="50b88-224">Rozmiar: 75, 23</span><span class="sxs-lookup"><span data-stu-id="50b88-224">Size: 75, 23</span></span><br /><br /> <span data-ttu-id="50b88-225">Tekst: Zamknij</span><span class="sxs-lookup"><span data-stu-id="50b88-225">Text: Quit</span></span>|  
    |<span data-ttu-id="50b88-226">**TextBox**</span><span class="sxs-lookup"><span data-stu-id="50b88-226">**TextBox**</span></span>|<span data-ttu-id="50b88-227">Nazwa: element WorkflowStatus</span><span class="sxs-lookup"><span data-stu-id="50b88-227">Name: WorkflowStatus</span></span><br /><br /> <span data-ttu-id="50b88-228">Lokalizacja: 10, 73</span><span class="sxs-lookup"><span data-stu-id="50b88-228">Location: 10, 73</span></span><br /><br /> <span data-ttu-id="50b88-229">Wiele linii: True</span><span class="sxs-lookup"><span data-stu-id="50b88-229">Multiline: True</span></span><br /><br /> <span data-ttu-id="50b88-230">Tylko do odczytu: True</span><span class="sxs-lookup"><span data-stu-id="50b88-230">ReadOnly: True</span></span><br /><br /> <span data-ttu-id="50b88-231">Paski przewijania: pionowa</span><span class="sxs-lookup"><span data-stu-id="50b88-231">ScrollBars: Vertical</span></span><br /><br /> <span data-ttu-id="50b88-232">Rozmiar: 338, 208</span><span class="sxs-lookup"><span data-stu-id="50b88-232">Size: 338, 208</span></span>|  
  
5.  <span data-ttu-id="50b88-233">Ustaw **AcceptButton** właściwości formularza w celu **EnterGuess**.</span><span class="sxs-lookup"><span data-stu-id="50b88-233">Set the **AcceptButton** property of the form to **EnterGuess**.</span></span>  
  
 <span data-ttu-id="50b88-234">Poniższy przykład ilustruje wypełniony formularz.</span><span class="sxs-lookup"><span data-stu-id="50b88-234">The following example illustrates the completed form.</span></span>  
  
 <span data-ttu-id="50b88-235">![WF45 Wprowadzenie formularz hosta samouczek przepływu pracy](../../../docs/framework/windows-workflow-foundation/media/wf45gettingstartedtutorialworkflowhostform.png "WF45GettingStartedTutorialWorkflowHostForm")</span><span class="sxs-lookup"><span data-stu-id="50b88-235">![WF45 Getting Started Tutorial Workflow Host Form](../../../docs/framework/windows-workflow-foundation/media/wf45gettingstartedtutorialworkflowhostform.png "WF45GettingStartedTutorialWorkflowHostForm")</span></span>  
  
###  <a name="BKMK_AddHelperMethods"></a> <span data-ttu-id="50b88-236">Aby dodać właściwości i metody pomocnicze formularza</span><span class="sxs-lookup"><span data-stu-id="50b88-236">To add the properties and helper methods of the form</span></span>  
 <span data-ttu-id="50b88-237">Kroki opisane w tej sekcji Dodaj właściwości i metody pomocnicze do skonfigurowanego interfejsu użytkownika formularza, do obsługi uruchomiona i wznawianie numer odgadnięcia przepływy pracy klasy formularza.</span><span class="sxs-lookup"><span data-stu-id="50b88-237">The steps in this section add properties and helper methods to the form class that configure the UI of the form to support running and resuming number guess workflows.</span></span>  
  
1.  <span data-ttu-id="50b88-238">Kliknij prawym przyciskiem myszy **WorkflowHostForm** w **Eksploratora rozwiązań** i wybierz polecenie **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="50b88-238">Right-click **WorkflowHostForm** in **Solution Explorer** and choose **View Code**.</span></span>  
  
2.  <span data-ttu-id="50b88-239">Dodaj następujący kod `using` (lub `Imports`) instrukcji w górnej części pliku razem z innymi `using` (lub `Imports`) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="50b88-239">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports System.Windows.Forms  
    Imports System.Activities.DurableInstancing  
    Imports System.Activities  
    Imports System.Data.SqlClient  
    Imports System.IO  
    ```  
  
    ```csharp  
    using System.Windows.Forms;  
    using System.Activities.DurableInstancing;  
    using System.Activities;  
    using System.Data.SqlClient;  
    using System.IO;  
    ```  
  
3.  <span data-ttu-id="50b88-240">Dodaj następujące deklaracje elementu członkowskiego do **WorkflowHostForm** klasy.</span><span class="sxs-lookup"><span data-stu-id="50b88-240">Add the following member declarations to the **WorkflowHostForm** class.</span></span>  
  
    ```vb  
    Const connectionString = "Server=.\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI"  
    Dim store As SqlWorkflowInstanceStore  
    Dim WorkflowStarting As Boolean  
    ```  
  
    ```csharp  
    const string connectionString = "Server=.\\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI";  
    SqlWorkflowInstanceStore store;  
    bool WorkflowStarting;  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="50b88-241">Jeśli ciąg połączenia jest inna, zaktualizuj `connectionString` do odwoływania się do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="50b88-241">If your connection string is different, update `connectionString` to refer to your database.</span></span>  
  
4.  <span data-ttu-id="50b88-242">Dodaj `WorkflowInstanceId` właściwość `WorkflowFormHost` klasy.</span><span class="sxs-lookup"><span data-stu-id="50b88-242">Add a `WorkflowInstanceId` property to the `WorkflowFormHost` class.</span></span>  
  
    ```vb  
    Public ReadOnly Property WorkflowInstanceId() As Guid  
        Get  
            If InstanceId.SelectedIndex = -1 Then  
                Return Guid.Empty  
            Else  
                Return New Guid(InstanceId.SelectedItem.ToString())  
            End If  
        End Get  
    End Property  
    ```  
  
    ```csharp  
    public Guid WorkflowInstanceId  
    {  
        get  
        {  
            return InstanceId.SelectedIndex == -1 ? Guid.Empty : (Guid)InstanceId.SelectedItem;  
        }  
    }  
    ```  
  
     <span data-ttu-id="50b88-243">`InstanceId` Polu kombi zawiera listę identyfikatorów wystąpień utrwalonych przepływów pracy oraz `WorkflowInstanceId` właściwość zwraca aktualnie wybranego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="50b88-243">The `InstanceId` combo box displays a list of persisted workflow instance ids, and the `WorkflowInstanceId` property returns the currently selected workflow.</span></span>  
  
5.  <span data-ttu-id="50b88-244">Dodawanie obsługi dla formularza `Load` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="50b88-244">Add a handler for the form `Load` event.</span></span> <span data-ttu-id="50b88-245">Aby dodać program obsługi, przełącz się do **widoku projektu** formularza, kliknij przycisk **zdarzenia** ikonę u góry **właściwości** okna, a następnie kliknij dwukrotnie plik **obciążenia**.</span><span class="sxs-lookup"><span data-stu-id="50b88-245">To add the handler, switch to **Design View** for the form, click the **Events** icon at the top of the **Properties** window, and double-click **Load**.</span></span>  
  
    ```vb  
    Private Sub WorkflowHostForm_Load(sender As Object, e As EventArgs) Handles Me.Load  
  
    End Sub  
    ```  
  
    ```csharp  
    private void WorkflowHostForm_Load(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
6.  <span data-ttu-id="50b88-246">Dodaj następujący kod do `WorkflowHostForm_Load`.</span><span class="sxs-lookup"><span data-stu-id="50b88-246">Add the following code to `WorkflowHostForm_Load`.</span></span>  
  
    ```vb  
    'Initialize the store and configure it so that it can be used for  
    'multiple WorkflowApplication instances.  
    store = New SqlWorkflowInstanceStore(connectionString)  
    WorkflowApplication.CreateDefaultInstanceOwner(store, Nothing, WorkflowIdentityFilter.Any)  
  
    'Set default ComboBox selections.  
    NumberRange.SelectedIndex = 0  
    WorkflowType.SelectedIndex = 0  
  
    ListPersistedWorkflows()  
    ```  
  
    ```csharp  
    // Initialize the store and configure it so that it can be used for  
    // multiple WorkflowApplication instances.  
    store = new SqlWorkflowInstanceStore(connectionString);  
    WorkflowApplication.CreateDefaultInstanceOwner(store, null, WorkflowIdentityFilter.Any);  
  
    // Set default ComboBox selections.  
    NumberRange.SelectedIndex = 0;  
    WorkflowType.SelectedIndex = 0;  
  
    ListPersistedWorkflows();  
    ```  
  
     <span data-ttu-id="50b88-247">Podczas ładowania formularza, `SqlWorkflowInstanceStore` jest skonfigurowany, pola kombi typu zakres i przepływu pracy są ustawione wartości domyślne, a wystąpienia utrwalonych przepływu pracy są dodawane do `InstanceId` pola kombi.</span><span class="sxs-lookup"><span data-stu-id="50b88-247">When the form loads, the `SqlWorkflowInstanceStore` is configured, the range and workflow type combo boxes are set to default values, and the persisted workflow instances are added to the `InstanceId` combo box.</span></span>  
  
7.  <span data-ttu-id="50b88-248">Dodaj `SelectedIndexChanged` Obsługa `InstanceId`.</span><span class="sxs-lookup"><span data-stu-id="50b88-248">Add a `SelectedIndexChanged` handler for `InstanceId`.</span></span> <span data-ttu-id="50b88-249">Aby dodać program obsługi, przełącz się do **widoku projektu** w formularzu Wybierz `InstanceId` pola kombi, kliknij przycisk **zdarzenia** ikony w górnej części **właściwości** okna, i Kliknij dwukrotnie **selectedindexchanged**.</span><span class="sxs-lookup"><span data-stu-id="50b88-249">To add the handler, switch to **Design View** for the form, select the `InstanceId` combo box, click the **Events** icon at the top of the **Properties** window, and double-click **SelectedIndexChanged**.</span></span>  
  
    ```vb  
    Private Sub InstanceId_SelectedIndexChanged(sender As Object, e As EventArgs) Handles InstanceId.SelectedIndexChanged  
  
    End Sub  
    ```  
  
    ```csharp  
    private void InstanceId_SelectedIndexChanged(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
8.  <span data-ttu-id="50b88-250">Dodaj następujący kod do `InstanceId_SelectedIndexChanged`.</span><span class="sxs-lookup"><span data-stu-id="50b88-250">Add the following code to `InstanceId_SelectedIndexChanged`.</span></span> <span data-ttu-id="50b88-251">Zawsze, gdy użytkownik wybierze przepływu pracy za pomocą pola kombi ten program obsługi aktualizacji w oknie stanu.</span><span class="sxs-lookup"><span data-stu-id="50b88-251">Whenever the user selects a workflow by using the combo box this handler updates the status window.</span></span>  
  
    ```vb  
    If InstanceId.SelectedIndex = -1 Then  
        Return  
    End If  
  
    'Clear the status window.  
    WorkflowStatus.Clear()  
  
    'Get the workflow version and display it.  
    'If the workflow is just starting then this info will not  
    'be available in the persistence store so do not try and retrieve it.  
    If Not WorkflowStarting Then  
        Dim instance As WorkflowApplicationInstance = _  
            WorkflowApplication.GetInstance(WorkflowInstanceId, store)  
  
        WorkflowVersion.Text = _  
            WorkflowVersionMap.GetIdentityDescription(instance.DefinitionIdentity)  
  
        'Unload the instance.  
        instance.Abandon()  
    End If  
    ```  
  
    ```csharp  
    if (InstanceId.SelectedIndex == -1)  
    {  
        return;  
    }  
  
    // Clear the status window.  
    WorkflowStatus.Clear();  
  
    // Get the workflow version and display it.  
    // If the workflow is just starting then this info will not  
    // be available in the persistence store so do not try and retrieve it.  
    if (!WorkflowStarting)  
    {  
        WorkflowApplicationInstance instance =  
            WorkflowApplication.GetInstance(this.WorkflowInstanceId, store);  
  
        WorkflowVersion.Text =  
            WorkflowVersionMap.GetIdentityDescription(instance.DefinitionIdentity);  
  
        // Unload the instance.  
        instance.Abandon();  
    }  
    ```  
  
9. <span data-ttu-id="50b88-252">Dodaj następujący kod `ListPersistedWorkflows` metodę do klasy formularza.</span><span class="sxs-lookup"><span data-stu-id="50b88-252">Add the following `ListPersistedWorkflows` method to the form class.</span></span>  
  
    ```vb  
    Private Sub ListPersistedWorkflows()  
        Using localCon As New SqlConnection(connectionString)  
            Dim localCmd As String = _  
                "Select [InstanceId] from [System.Activities.DurableInstancing].[Instances] Order By [CreationTime]"  
  
            Dim cmd As SqlCommand = localCon.CreateCommand()  
            cmd.CommandText = localCmd  
            localCon.Open()  
            Using reader As SqlDataReader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
  
                While (reader.Read())  
                    'Get the InstanceId of the persisted Workflow.  
                    Dim id As Guid = Guid.Parse(reader(0).ToString())  
                    InstanceId.Items.Add(id)  
                End While  
            End Using  
        End Using  
    End Sub  
    ```  
  
    ```csharp  
    using (SqlConnection localCon = new SqlConnection(connectionString))  
    {  
        string localCmd =  
            "Select [InstanceId] from [System.Activities.DurableInstancing].[Instances] Order By [CreationTime]";  
  
        SqlCommand cmd = localCon.CreateCommand();  
        cmd.CommandText = localCmd;  
        localCon.Open();  
        using (SqlDataReader reader = cmd.ExecuteReader(CommandBehavior.CloseConnection))  
        {  
            while (reader.Read())  
            {  
                // Get the InstanceId of the persisted Workflow  
                Guid id = Guid.Parse(reader[0].ToString());  
                InstanceId.Items.Add(id);  
            }  
        }  
    }  
    ```  
  
     <span data-ttu-id="50b88-253">`ListPersistedWorkflows` zapytania w sklepie wystąpienia dla wystąpienia przepływu pracy utrwalonych i dodaje identyfikatorów wystąpień do `cboInstanceId` pola kombi.</span><span class="sxs-lookup"><span data-stu-id="50b88-253">`ListPersistedWorkflows` queries the instance store for persisted workflow instances, and adds the instance ids to the `cboInstanceId` combo box.</span></span>  
  
10. <span data-ttu-id="50b88-254">Dodaj następujący kod `UpdateStatus` metody i delegata odpowiedniej klasy formularza.</span><span class="sxs-lookup"><span data-stu-id="50b88-254">Add the following `UpdateStatus` method and corresponding delegate to the form class.</span></span> <span data-ttu-id="50b88-255">Ta metoda aktualizuje okno stanu w formularzu ze stanem obecnie uruchomiony przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="50b88-255">This method updates the status window on the form with the status of the currently running workflow.</span></span>  
  
    ```vb  
    Private Delegate Sub UpdateStatusDelegate(msg As String)  
    Public Sub UpdateStatus(msg As String)  
        'We may be on a different thread so we need to  
        'make this call using BeginInvoke.  
        If InvokeRequired Then  
            BeginInvoke(New UpdateStatusDelegate(AddressOf UpdateStatus), msg)  
        Else  
            If Not msg.EndsWith(vbCrLf) Then  
                msg = msg & vbCrLf  
            End If  
  
            WorkflowStatus.AppendText(msg)  
  
            'Ensure that the newly added status is visible.  
            WorkflowStatus.SelectionStart = WorkflowStatus.Text.Length  
            WorkflowStatus.ScrollToCaret()  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    private delegate void UpdateStatusDelegate(string msg);  
    public void UpdateStatus(string msg)  
    {  
        // We may be on a different thread so we need to  
        // make this call using BeginInvoke.  
        if (InvokeRequired)  
        {  
            BeginInvoke(new UpdateStatusDelegate(UpdateStatus), msg);  
        }  
        else  
        {  
            if (!msg.EndsWith("\r\n"))  
            {  
                msg += "\r\n";  
            }  
            WorkflowStatus.AppendText(msg);  
  
            WorkflowStatus.SelectionStart = WorkflowStatus.Text.Length;  
            WorkflowStatus.ScrollToCaret();  
        }  
    }  
    ```  
  
11. <span data-ttu-id="50b88-256">Dodaj następujący kod `GameOver` metody i delegata odpowiedniej klasy formularza.</span><span class="sxs-lookup"><span data-stu-id="50b88-256">Add the following `GameOver` method and corresponding delegate to the form class.</span></span> <span data-ttu-id="50b88-257">Po zakończeniu przepływu pracy, ta metoda aktualizuje formularza interfejsu użytkownika przez usunięcie identyfikatora wystąpienia przepływu pracy, ukończonej z **InstanceId** pola kombi.</span><span class="sxs-lookup"><span data-stu-id="50b88-257">When a workflow completes, this method updates the form UI by removing the instance id of the completed workflow from the **InstanceId** combo box.</span></span>  
  
    ```vb  
    Private Delegate Sub GameOverDelegate()  
    Private Sub GameOver()  
        If InvokeRequired Then  
            BeginInvoke(New GameOverDelegate(AddressOf GameOver))  
        Else  
            'Remove this instance from the InstanceId combo box.  
            InstanceId.Items.Remove(InstanceId.SelectedItem)  
            InstanceId.SelectedIndex = -1  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    private delegate void GameOverDelegate();  
    private void GameOver()  
    {  
        if (InvokeRequired)  
        {  
            BeginInvoke(new GameOverDelegate(GameOver));  
        }  
        else  
        {  
            // Remove this instance from the combo box  
            InstanceId.Items.Remove(InstanceId.SelectedItem);  
            InstanceId.SelectedIndex = -1;  
        }  
    }  
    ```  
  
###  <a name="BKMK_ConfigureWorkflowApplication"></a> <span data-ttu-id="50b88-258">Aby skonfigurować Magazyn wystąpień przepływu pracy cyklu życia obsługi i rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="50b88-258">To configure the instance store, workflow lifecycle handlers, and extensions</span></span>  
  
1.  <span data-ttu-id="50b88-259">Dodaj `ConfigureWorkflowApplication` metodę do klasy formularza.</span><span class="sxs-lookup"><span data-stu-id="50b88-259">Add a `ConfigureWorkflowApplication` method to the form class.</span></span>  
  
    ```vb  
    Private Sub ConfigureWorkflowApplication(wfApp As WorkflowApplication)  
  
    End Sub  
    ```  
  
    ```csharp  
    private void ConfigureWorkflowApplication(WorkflowApplication wfApp)  
    {      
    }  
    ```  
  
     <span data-ttu-id="50b88-260">Ta metoda umożliwia skonfigurowanie `WorkflowApplication`, dodaje rozszerzenia żądaną i dodaje programy obsługi zdarzeń cyklu życia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="50b88-260">This method configures the `WorkflowApplication`, adds the desired extensions, and adds handlers for the workflow lifecycle events.</span></span>  
  
2.  <span data-ttu-id="50b88-261">W `ConfigureWorkflowApplication`, określ `SqlWorkflowInstanceStore` dla `WorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="50b88-261">In `ConfigureWorkflowApplication`, specify the `SqlWorkflowInstanceStore` for the `WorkflowApplication`.</span></span>  
  
    ```vb  
    'Configure the persistence store.  
    wfApp.InstanceStore = store  
    ```  
  
    ```csharp  
    // Configure the persistence store.  
    wfApp.InstanceStore = store;  
    ```  
  
3.  <span data-ttu-id="50b88-262">Następnie należy utworzyć `StringWriter` wystąpienia i dodać go do `Extensions` zbiór `WorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="50b88-262">Next, create a `StringWriter` instance and add it to the `Extensions` collection of the `WorkflowApplication`.</span></span> <span data-ttu-id="50b88-263">Gdy `StringWriter` jest dodawany do rozszerzeń przechwytuje wszystkie `WriteLine` wyjście działania.</span><span class="sxs-lookup"><span data-stu-id="50b88-263">When a `StringWriter` is added to the extensions it captures all `WriteLine` activity output.</span></span> <span data-ttu-id="50b88-264">Gdy przepływ pracy staje się nieaktywna, `WriteLine` dane wyjściowe można wyodrębnić z `StringWriter` i wyświetlane w formularzu.</span><span class="sxs-lookup"><span data-stu-id="50b88-264">When the workflow becomes idle, the `WriteLine` output can be extracted from the `StringWriter` and displayed on the form.</span></span>  
  
    ```vb  
    'Add a StringWriter to the extensions. This captures the output  
    'from the WriteLine activities so we can display it in the form.  
    Dim sw As New StringWriter()  
    wfApp.Extensions.Add(sw)  
    ```  
  
    ```csharp  
    // Add a StringWriter to the extensions. This captures the output  
    // from the WriteLine activities so we can display it in the form.  
    StringWriter sw = new StringWriter();  
    wfApp.Extensions.Add(sw);  
    ```  
  
4.  <span data-ttu-id="50b88-265">Dodaj następujący program obsługi dla `Completed` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="50b88-265">Add the following handler for the `Completed` event.</span></span> <span data-ttu-id="50b88-266">Po pomyślnym ukończeniu przepływu pracy liczba włącza podjęte w celu odgadnięcia, że liczba zostanie wyświetlone okno stanu.</span><span class="sxs-lookup"><span data-stu-id="50b88-266">When a workflow successfully completes, the number of turns taken to guess the number is displayed to the status window.</span></span> <span data-ttu-id="50b88-267">Informacje o wyjątku, który spowodował przerwanie jest wyświetlany, jeśli kończy się przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="50b88-267">If the workflow terminates, the exception information that caused the termination is displayed.</span></span> <span data-ttu-id="50b88-268">Na koniec obsługi `GameOver` wywoływana jest metoda, która usuwa ukończony przepływ pracy z listy przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="50b88-268">At the end of the handler the `GameOver` method is called, which removes the completed workflow from the workflow list.</span></span>  
  
    ```vb  
    wfApp.Completed = _  
        Sub(e As WorkflowApplicationCompletedEventArgs)  
            If e.CompletionState = ActivityInstanceState.Faulted Then  
                UpdateStatus(String.Format("Workflow Terminated. Exception: {0}" & vbCrLf & "{1}", _  
                    e.TerminationException.GetType().FullName, _  
                    e.TerminationException.Message))  
            ElseIf e.CompletionState = ActivityInstanceState.Canceled Then  
                UpdateStatus("Workflow Canceled.")  
            Else  
                Dim Turns As Integer = Convert.ToInt32(e.Outputs("Turns"))  
                UpdateStatus(String.Format("Congratulations, you guessed the number in {0} turns.", Turns))  
            End If  
            GameOver()  
        End Sub  
    ```  
  
    ```csharp  
    wfApp.Completed = delegate(WorkflowApplicationCompletedEventArgs e)  
    {  
        if (e.CompletionState == ActivityInstanceState.Faulted)  
        {  
            UpdateStatus(string.Format("Workflow Terminated. Exception: {0}\r\n{1}",  
                e.TerminationException.GetType().FullName,  
                e.TerminationException.Message));  
        }  
        else if (e.CompletionState == ActivityInstanceState.Canceled)  
        {  
            UpdateStatus("Workflow Canceled.");  
        }  
        else  
        {  
            int Turns = Convert.ToInt32(e.Outputs["Turns"]);  
            UpdateStatus(string.Format("Congratulations, you guessed the number in {0} turns.", Turns));  
        }  
        GameOver();  
    };  
    ```  
  
5.  <span data-ttu-id="50b88-269">Dodaj następujący kod `Aborted` i `OnUnhandledException` programów obsługi.</span><span class="sxs-lookup"><span data-stu-id="50b88-269">Add the following `Aborted` and `OnUnhandledException` handlers.</span></span> <span data-ttu-id="50b88-270">`GameOver` Metoda nie jest wywoływana z `Aborted` obsługi gdy wystąpienie przepływu pracy zostało przerwane, nie kończy, dlatego można wznowić wystąpienia w późniejszym czasie.</span><span class="sxs-lookup"><span data-stu-id="50b88-270">The `GameOver` method is not called from the `Aborted` handler because when a workflow instance is aborted, it does not terminate, and it is possible to resume the instance at a later time.</span></span>  
  
    ```vb  
    wfApp.Aborted = _  
        Sub(e As WorkflowApplicationAbortedEventArgs)  
            UpdateStatus(String.Format("Workflow Aborted. Exception: {0}" & vbCrLf & "{1}", _  
                e.Reason.GetType().FullName, _  
                e.Reason.Message))  
        End Sub  
  
    wfApp.OnUnhandledException = _  
        Function(e As WorkflowApplicationUnhandledExceptionEventArgs)  
            UpdateStatus(String.Format("Unhandled Exception: {0}" & vbCrLf & "{1}", _  
                e.UnhandledException.GetType().FullName, _  
                e.UnhandledException.Message))  
            GameOver()  
            Return UnhandledExceptionAction.Terminate  
        End Function  
    ```  
  
    ```csharp  
    wfApp.Aborted = delegate(WorkflowApplicationAbortedEventArgs e)  
    {  
        UpdateStatus(string.Format("Workflow Aborted. Exception: {0}\r\n{1}",  
                e.Reason.GetType().FullName,  
                e.Reason.Message));  
    };  
  
    wfApp.OnUnhandledException = delegate(WorkflowApplicationUnhandledExceptionEventArgs e)  
    {  
        UpdateStatus(string.Format("Unhandled Exception: {0}\r\n{1}",  
                e.UnhandledException.GetType().FullName,  
                e.UnhandledException.Message));  
        GameOver();  
        return UnhandledExceptionAction.Terminate;  
    };  
    ```  
  
6.  <span data-ttu-id="50b88-271">Dodaj następujący kod `PersistableIdle` programu obsługi.</span><span class="sxs-lookup"><span data-stu-id="50b88-271">Add the following `PersistableIdle` handler.</span></span> <span data-ttu-id="50b88-272">Pobiera ten program obsługi `StringWriter` rozszerzenia, który został dodany, wyodrębnia dane wyjściowe z `WriteLine` działań i wyświetla go w oknie stanu.</span><span class="sxs-lookup"><span data-stu-id="50b88-272">This handler retrieves the `StringWriter` extension that was added, extracts the output from the `WriteLine` activities, and displays it in the status window.</span></span>  
  
    ```vb  
    wfApp.PersistableIdle = _  
        Function(e As WorkflowApplicationIdleEventArgs)  
            'Send the current WriteLine outputs to the status window.  
            Dim writers = e.GetInstanceExtensions(Of StringWriter)()  
            For Each writer In writers  
                UpdateStatus(writer.ToString())  
            Next  
            Return PersistableIdleAction.Unload  
        End Function  
    ```  
  
    ```csharp  
    wfApp.PersistableIdle = delegate(WorkflowApplicationIdleEventArgs e)  
    {  
        // Send the current WriteLine outputs to the status window.  
        var writers = e.GetInstanceExtensions<StringWriter>();  
        foreach (var writer in writers)  
        {  
            UpdateStatus(writer.ToString());  
        }  
        return PersistableIdleAction.Unload;  
    };  
    ```  
  
     <span data-ttu-id="50b88-273"><xref:System.Activities.PersistableIdleAction> Wyliczenie ma trzy wartości: <xref:System.Activities.PersistableIdleAction.None>, <xref:System.Activities.PersistableIdleAction.Persist>, i <xref:System.Activities.PersistableIdleAction.Unload>.</span><span class="sxs-lookup"><span data-stu-id="50b88-273">The <xref:System.Activities.PersistableIdleAction> enumeration has three values: <xref:System.Activities.PersistableIdleAction.None>, <xref:System.Activities.PersistableIdleAction.Persist>, and <xref:System.Activities.PersistableIdleAction.Unload>.</span></span> <span data-ttu-id="50b88-274"><xref:System.Activities.PersistableIdleAction.Persist> powoduje, że przepływ pracy, aby utrwalić, ale go nie powoduje przepływ pracy, aby zwolnić.</span><span class="sxs-lookup"><span data-stu-id="50b88-274"><xref:System.Activities.PersistableIdleAction.Persist> causes the workflow to persist but it does not cause the workflow to unload.</span></span> <span data-ttu-id="50b88-275"><xref:System.Activities.PersistableIdleAction.Unload> powoduje, że przepływ pracy, aby utrwalić i zostać zwolniony.</span><span class="sxs-lookup"><span data-stu-id="50b88-275"><xref:System.Activities.PersistableIdleAction.Unload> causes the workflow to persist and be unloaded.</span></span>  
  
     <span data-ttu-id="50b88-276">Poniższy przykład jest gotowy `ConfigureWorkflowApplication` metody.</span><span class="sxs-lookup"><span data-stu-id="50b88-276">The following example is the completed `ConfigureWorkflowApplication` method.</span></span>  
  
    ```vb  
    Private Sub ConfigureWorkflowApplication(wfApp As WorkflowApplication)  
        'Configure the persistence store.  
        wfApp.InstanceStore = store  
  
        'Add a StringWriter to the extensions. This captures the output  
        'from the WriteLine activities so we can display it in the form.  
        Dim sw As New StringWriter()  
        wfApp.Extensions.Add(sw)  
  
        wfApp.Completed = _  
            Sub(e As WorkflowApplicationCompletedEventArgs)  
                If e.CompletionState = ActivityInstanceState.Faulted Then  
                    UpdateStatus(String.Format("Workflow Terminated. Exception: {0}" & vbCrLf & "{1}", _  
                        e.TerminationException.GetType().FullName, _  
                        e.TerminationException.Message))  
                ElseIf e.CompletionState = ActivityInstanceState.Canceled Then  
                    UpdateStatus("Workflow Canceled.")  
                Else  
                    Dim Turns As Integer = Convert.ToInt32(e.Outputs("Turns"))  
                    UpdateStatus(String.Format("Congratulations, you guessed the number in {0} turns.", Turns))  
                End If  
                GameOver()  
            End Sub  
  
        wfApp.Aborted = _  
            Sub(e As WorkflowApplicationAbortedEventArgs)  
                UpdateStatus(String.Format("Workflow Aborted. Exception: {0}" & vbCrLf & "{1}", _  
                    e.Reason.GetType().FullName, _  
                    e.Reason.Message))  
            End Sub  
  
        wfApp.OnUnhandledException = _  
            Function(e As WorkflowApplicationUnhandledExceptionEventArgs)  
                UpdateStatus(String.Format("Unhandled Exception: {0}" & vbCrLf & "{1}", _  
                    e.UnhandledException.GetType().FullName, _  
                    e.UnhandledException.Message))  
                GameOver()  
                Return UnhandledExceptionAction.Terminate  
            End Function  
  
        wfApp.PersistableIdle = _  
            Function(e As WorkflowApplicationIdleEventArgs)  
                'Send the current WriteLine outputs to the status window.  
                Dim writers = e.GetInstanceExtensions(Of StringWriter)()  
                For Each writer In writers  
                    UpdateStatus(writer.ToString())  
                Next  
                Return PersistableIdleAction.Unload  
            End Function  
    End Sub  
    ```  
  
    ```csharp  
    private void ConfigureWorkflowApplication(WorkflowApplication wfApp)  
    {  
        // Configure the persistence store.  
        wfApp.InstanceStore = store;  
  
        // Add a StringWriter to the extensions. This captures the output  
        // from the WriteLine activities so we can display it in the form.  
        StringWriter sw = new StringWriter();  
        wfApp.Extensions.Add(sw);  
  
        wfApp.Completed = delegate(WorkflowApplicationCompletedEventArgs e)  
        {  
            if (e.CompletionState == ActivityInstanceState.Faulted)  
            {  
                UpdateStatus(string.Format("Workflow Terminated. Exception: {0}\r\n{1}",  
                    e.TerminationException.GetType().FullName,  
                    e.TerminationException.Message));  
            }  
            else if (e.CompletionState == ActivityInstanceState.Canceled)  
            {  
                UpdateStatus("Workflow Canceled.");  
            }  
            else  
            {  
                int Turns = Convert.ToInt32(e.Outputs["Turns"]);  
                UpdateStatus(string.Format("Congratulations, you guessed the number in {0} turns.", Turns));  
            }  
            GameOver();  
        };  
  
        wfApp.Aborted = delegate(WorkflowApplicationAbortedEventArgs e)  
        {  
            UpdateStatus(string.Format("Workflow Aborted. Exception: {0}\r\n{1}",  
                    e.Reason.GetType().FullName,  
                    e.Reason.Message));  
        };  
  
        wfApp.OnUnhandledException = delegate(WorkflowApplicationUnhandledExceptionEventArgs e)  
        {  
            UpdateStatus(string.Format("Unhandled Exception: {0}\r\n{1}",  
                    e.UnhandledException.GetType().FullName,  
                    e.UnhandledException.Message));  
            GameOver();  
            return UnhandledExceptionAction.Terminate;  
        };  
  
        wfApp.PersistableIdle = delegate(WorkflowApplicationIdleEventArgs e)  
        {  
            // Send the current WriteLine outputs to the status window.  
            var writers = e.GetInstanceExtensions<StringWriter>();  
            foreach (var writer in writers)  
            {  
                UpdateStatus(writer.ToString());  
            }  
            return PersistableIdleAction.Unload;  
        };  
    }  
    ```  
  
###  <a name="BKMK_WorkflowVersionMap"></a> <span data-ttu-id="50b88-277">Aby włączyć uruchamianie i wznawianie wielu typów przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="50b88-277">To enable starting and resuming multiple workflow types</span></span>  
 <span data-ttu-id="50b88-278">Aby wznowić działanie wystąpienia przepływu pracy, host musi podać definicję przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="50b88-278">In order to resume a workflow instance, the host has to provide the workflow definition.</span></span> <span data-ttu-id="50b88-279">W ramach tego samouczka istnieją trzy typy przepływu pracy, a kolejne kroki samouczka wprowadzenie wielu wersji tego typu.</span><span class="sxs-lookup"><span data-stu-id="50b88-279">In this tutorial there are three workflow types, and subsequent tutorial steps introduce multiple versions of these types.</span></span> <span data-ttu-id="50b88-280">`WorkflowIdentity` umożliwia aplikacji hosta skojarzyć informacje identyfikacyjne z istniejącym wystąpieniem przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="50b88-280">`WorkflowIdentity` provides a way for a host application to associate identifying information with a persisted workflow instance.</span></span> <span data-ttu-id="50b88-281">Kroki opisane w tej sekcji pokazują, jak utworzyć klasę użytkową uzyskanymi mapowania tożsamości przepływu pracy z istniejącym wystąpieniem przepływu pracy do odpowiedniej definicji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="50b88-281">The steps in this section demonstrate how to create a utility class to assist with mapping the workflow identity from a persisted workflow instance to the corresponding workflow definition.</span></span> <span data-ttu-id="50b88-282">Aby uzyskać więcej informacji na temat `WorkflowIdentity` i przechowywania wersji, zobacz [przy użyciu obiektu WorkflowIdentity i wersjonowanie](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md).</span><span class="sxs-lookup"><span data-stu-id="50b88-282">For more information about `WorkflowIdentity` and versioning, see [Using WorkflowIdentity and Versioning](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md).</span></span>  
  
1.  <span data-ttu-id="50b88-283">Kliknij prawym przyciskiem myszy **NumberGuessWorkflowHost** w **Eksploratora rozwiązań** i wybierz polecenie **Dodaj**, **klasy**.</span><span class="sxs-lookup"><span data-stu-id="50b88-283">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **Class**.</span></span> <span data-ttu-id="50b88-284">Typ `WorkflowVersionMap` do **nazwa** pole, a następnie kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="50b88-284">Type `WorkflowVersionMap` into the **Name** box and click **Add**.</span></span>  
  
2.  <span data-ttu-id="50b88-285">Dodaj następujący kod `using` lub `Imports` instrukcji w górnej części pliku razem z innymi `using` lub `Imports` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="50b88-285">Add the following `using` or `Imports` statements at the top of the file with the other `using` or `Imports` statements.</span></span>  
  
    ```vb  
    Imports NumberGuessWorkflowActivities  
    Imports System.Activities  
    ```  
  
    ```csharp  
    using NumberGuessWorkflowActivities;  
    using System.Activities;  
    ```  
  
3.  <span data-ttu-id="50b88-286">Zastąp `WorkflowVersionMap` deklaracji z następującą deklarację klasy.</span><span class="sxs-lookup"><span data-stu-id="50b88-286">Replace the `WorkflowVersionMap` class declaration with the following declaration.</span></span>  
  
    ```vb  
    Public Module WorkflowVersionMap  
        Dim map As Dictionary(Of WorkflowIdentity, Activity)  
  
        'Current version identities.  
        Public StateMachineNumberGuessIdentity As WorkflowIdentity  
        Public FlowchartNumberGuessIdentity As WorkflowIdentity  
        Public SequentialNumberGuessIdentity As WorkflowIdentity  
  
        Sub New()  
            map = New Dictionary(Of WorkflowIdentity, Activity)  
  
            'Add the current workflow version identities.  
            StateMachineNumberGuessIdentity = New WorkflowIdentity With  
            {  
                .Name = "StateMachineNumberGuessWorkflow",  
                .Version = New Version(1, 0, 0, 0)  
            }  
  
            FlowchartNumberGuessIdentity = New WorkflowIdentity With  
            {  
                .Name = "FlowchartNumberGuessWorkflow",  
                .Version = New Version(1, 0, 0, 0)  
            }  
  
            SequentialNumberGuessIdentity = New WorkflowIdentity With  
            {  
                .Name = "SequentialNumberGuessWorkflow",  
                .Version = New Version(1, 0, 0, 0)  
            }  
  
            map.Add(StateMachineNumberGuessIdentity, New StateMachineNumberGuessWorkflow())  
            map.Add(FlowchartNumberGuessIdentity, New FlowchartNumberGuessWorkflow())  
            map.Add(SequentialNumberGuessIdentity, New SequentialNumberGuessWorkflow())  
        End Sub  
  
        Public Function GetWorkflowDefinition(identity As WorkflowIdentity) As Activity  
            Return map(identity)  
        End Function  
  
        Public Function GetIdentityDescription(identity As WorkflowIdentity) As String  
            Return identity.ToString()  
        End Function  
    End Module  
    ```  
  
    ```csharp  
    public static class WorkflowVersionMap  
    {  
        static Dictionary<WorkflowIdentity, Activity> map;  
  
        // Current version identities.  
        static public WorkflowIdentity StateMachineNumberGuessIdentity;  
        static public WorkflowIdentity FlowchartNumberGuessIdentity;  
        static public WorkflowIdentity SequentialNumberGuessIdentity;  
  
        static WorkflowVersionMap()  
        {  
            map = new Dictionary<WorkflowIdentity, Activity>();  
  
            // Add the current workflow version identities.  
            StateMachineNumberGuessIdentity = new WorkflowIdentity  
            {  
                Name = "StateMachineNumberGuessWorkflow",  
                Version = new Version(1, 0, 0, 0)  
            };  
  
            FlowchartNumberGuessIdentity = new WorkflowIdentity  
            {  
                Name = "FlowchartNumberGuessWorkflow",  
                Version = new Version(1, 0, 0, 0)  
            };  
  
            SequentialNumberGuessIdentity = new WorkflowIdentity  
            {  
                Name = "SequentialNumberGuessWorkflow",  
                Version = new Version(1, 0, 0, 0)  
            };  
  
            map.Add(StateMachineNumberGuessIdentity, new StateMachineNumberGuessWorkflow());  
            map.Add(FlowchartNumberGuessIdentity, new FlowchartNumberGuessWorkflow());  
            map.Add(SequentialNumberGuessIdentity, new SequentialNumberGuessWorkflow());  
        }  
  
        public static Activity GetWorkflowDefinition(WorkflowIdentity identity)  
        {  
            return map[identity];  
        }  
  
        public static string GetIdentityDescription(WorkflowIdentity identity)  
        {          
            return identity.ToString();  
       }  
    }  
    ```  
  
     <span data-ttu-id="50b88-287">`WorkflowVersionMap` zawiera trzy tożsamości przepływu pracy, które mapują do trzech definicji przepływu pracy z tego samouczka i jest używana w poniższych sekcjach, gdy rozpoczyna się przepływy pracy i wznowić.</span><span class="sxs-lookup"><span data-stu-id="50b88-287">`WorkflowVersionMap` contains three workflow identities that map to the three workflow definitions from this tutorial and is used in the following sections when workflows are started and resumed.</span></span>  
  
###  <a name="BKMK_StartWorkflow"></a> <span data-ttu-id="50b88-288">Aby uruchomić nowy przepływ pracy</span><span class="sxs-lookup"><span data-stu-id="50b88-288">To start a new workflow</span></span>  
  
1.  <span data-ttu-id="50b88-289">Dodaj `Click` Obsługa `NewGame`.</span><span class="sxs-lookup"><span data-stu-id="50b88-289">Add a `Click` handler for `NewGame`.</span></span> <span data-ttu-id="50b88-290">Aby dodać program obsługi, przełącz się do **widoku projektu** formularza, a następnie kliknij dwukrotnie plik `NewGame`.</span><span class="sxs-lookup"><span data-stu-id="50b88-290">To add the handler, switch to **Design View** for the form, and double-click `NewGame`.</span></span> <span data-ttu-id="50b88-291">A `NewGame_Click` dodaniu programu obsługi i widoku przełącza do widoku kodu formularza.</span><span class="sxs-lookup"><span data-stu-id="50b88-291">A `NewGame_Click` handler is added and the view switches to code view for the form.</span></span> <span data-ttu-id="50b88-292">Gdy użytkownik kliknie ten przycisk Nowy przepływ pracy został uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="50b88-292">Whenever the user clicks this button a new workflow is started.</span></span>  
  
    ```vb  
    Private Sub NewGame_Click(sender As Object, e As EventArgs) Handles NewGame.Click  
  
    End Sub  
    ```  
  
    ```csharp  
    private void NewGame_Click(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
2.  <span data-ttu-id="50b88-293">Dodaj następujący kod programem obsługi kliknięcia.</span><span class="sxs-lookup"><span data-stu-id="50b88-293">Add the following code to the click handler.</span></span> <span data-ttu-id="50b88-294">Ten kod tworzy słownik argumenty wejściowe dla przepływu pracy, kluczach nazwę argumentu.</span><span class="sxs-lookup"><span data-stu-id="50b88-294">This code creates a dictionary of input arguments for the workflow, keyed by argument name.</span></span> <span data-ttu-id="50b88-295">Tego słownika ma jeden wpis, zawierający zakres generowany losowo numer pobierane pole kombi zakresu.</span><span class="sxs-lookup"><span data-stu-id="50b88-295">This dictionary has one entry that contains the range of the randomly generated number retrieved from the range combo box.</span></span>  
  
    ```vb  
    Dim inputs As New Dictionary(Of String, Object)()  
    inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem))  
    ```  
  
    ```csharp  
    var inputs = new Dictionary<string, object>();  
    inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem));  
    ```  
  
3.  <span data-ttu-id="50b88-296">Następnie dodaj następujący kod, który uruchamia przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="50b88-296">Next, add the following code that starts the workflow.</span></span> <span data-ttu-id="50b88-297">`WorkflowIdentity` i definicji przepływu pracy, odpowiadający typowi wybrane przepływu pracy są pobierane przy użyciu `WorkflowVersionMap` Klasa pomocy.</span><span class="sxs-lookup"><span data-stu-id="50b88-297">The `WorkflowIdentity` and workflow definition corresponding to the type of workflow selected are retrieved using the `WorkflowVersionMap` helper class.</span></span> <span data-ttu-id="50b88-298">Następnie, nowy `WorkflowApplication` przy użyciu definicji przepływu pracy, tworzone jest wystąpienie `WorkflowIdentity`i słownika argumentów wejściowych.</span><span class="sxs-lookup"><span data-stu-id="50b88-298">Next, a new `WorkflowApplication` instance is created using the workflow definition, `WorkflowIdentity`, and dictionary of input arguments.</span></span>  
  
    ```vb  
    Dim identity As WorkflowIdentity = Nothing  
    Select Case WorkflowType.SelectedItem.ToString()  
        Case "SequentialNumberGuessWorkflow"  
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity  
  
        Case "StateMachineNumberGuessWorkflow"  
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity  
  
        Case "FlowchartNumberGuessWorkflow"  
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity  
    End Select  
  
    Dim wf As Activity = WorkflowVersionMap.GetWorkflowDefinition(identity)  
  
    Dim wfApp = New WorkflowApplication(wf, inputs, identity)  
    ```  
  
    ```csharp  
    WorkflowIdentity identity = null;  
    switch (WorkflowType.SelectedItem.ToString())  
    {  
        case "SequentialNumberGuessWorkflow":  
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity;  
            break;  
  
        case "StateMachineNumberGuessWorkflow":  
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity;  
            break;  
  
        case "FlowchartNumberGuessWorkflow":  
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity;  
            break;  
    };  
  
    Activity wf = WorkflowVersionMap.GetWorkflowDefinition(identity);  
  
    WorkflowApplication wfApp = new WorkflowApplication(wf, inputs, identity);  
    ```  
  
4.  <span data-ttu-id="50b88-299">Następnie dodaj następujący kod, który dodaje przepływu pracy do listy przepływów pracy i wyświetla informacje o wersji przepływu pracy na formularzu.</span><span class="sxs-lookup"><span data-stu-id="50b88-299">Next, add the following code which adds the workflow to the workflow list and displays the workflow's version information on the form.</span></span>  
  
    ```vb  
    'Add the workflow to the list and display the version information.  
    WorkflowStarting = True  
    InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id)  
    WorkflowVersion.Text = identity.ToString()  
    WorkflowStarting = False  
    ```  
  
    ```csharp  
    // Add the workflow to the list and display the version information.  
    WorkflowStarting = true;  
    InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id);  
    WorkflowVersion.Text = identity.ToString();  
    WorkflowStarting = false;  
    ```  
  
5.  <span data-ttu-id="50b88-300">Wywołaj `ConfigureWorkflowApplication` do skonfigurowania obsługi cyklu życia magazynu, rozszerzenia i przepływ pracy wystąpienie tego `WorkflowApplication` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="50b88-300">Call `ConfigureWorkflowApplication` to configure the instance store, extensions, and workflow lifecycle handlers for this `WorkflowApplication` instance.</span></span>  
  
    ```vb  
    'Configure the instance store, extensions, and   
    'workflow lifecycle handlers.  
    ConfigureWorkflowApplication(wfApp)  
    ```  
  
    ```csharp  
    // Configure the instance store, extensions, and   
    // workflow lifecycle handlers.  
    ConfigureWorkflowApplication(wfApp);  
    ```  
  
6.  <span data-ttu-id="50b88-301">Na koniec Wywołaj `Run`.</span><span class="sxs-lookup"><span data-stu-id="50b88-301">Finally, call `Run`.</span></span>  
  
    ```vb  
    'Start the workflow.  
    wfApp.Run()  
    ```  
  
    ```  
    // Start the workflow.  
    wfApp.Run();  
    ```  
  
     <span data-ttu-id="50b88-302">Poniższy przykład jest gotowy `NewGame_Click` programu obsługi.</span><span class="sxs-lookup"><span data-stu-id="50b88-302">The following example is the completed `NewGame_Click` handler.</span></span>  
  
    ```vb  
    Private Sub NewGame_Click(sender As Object, e As EventArgs) Handles NewGame.Click  
        'Start a new workflow.  
        Dim inputs As New Dictionary(Of String, Object)()  
        inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem))  
  
        Dim identity As WorkflowIdentity = Nothing  
        Select Case WorkflowType.SelectedItem.ToString()  
            Case "SequentialNumberGuessWorkflow"  
                identity = WorkflowVersionMap.SequentialNumberGuessIdentity  
  
            Case "StateMachineNumberGuessWorkflow"  
                identity = WorkflowVersionMap.StateMachineNumberGuessIdentity  
  
            Case "FlowchartNumberGuessWorkflow"  
                identity = WorkflowVersionMap.FlowchartNumberGuessIdentity  
        End Select  
  
        Dim wf As Activity = WorkflowVersionMap.GetWorkflowDefinition(identity)  
  
        Dim wfApp = New WorkflowApplication(wf, inputs, identity)  
  
        'Add the workflow to the list and display the version information.  
        WorkflowStarting = True  
        InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id)  
        WorkflowVersion.Text = identity.ToString()  
        WorkflowStarting = False  
  
        'Configure the instance store, extensions, and   
        'workflow lifecycle handlers.  
        ConfigureWorkflowApplication(wfApp)  
  
        'Start the workflow.  
        wfApp.Run()  
    End Sub  
    ```  
  
    ```csharp  
    private void NewGame_Click(object sender, EventArgs e)  
    {  
        var inputs = new Dictionary<string, object>();  
        inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem));  
  
        WorkflowIdentity identity = null;  
        switch (WorkflowType.SelectedItem.ToString())  
        {  
            case "SequentialNumberGuessWorkflow":  
                identity = WorkflowVersionMap.SequentialNumberGuessIdentity;  
                break;  
  
            case "StateMachineNumberGuessWorkflow":  
                identity = WorkflowVersionMap.StateMachineNumberGuessIdentity;  
                break;  
  
            case "FlowchartNumberGuessWorkflow":  
                identity = WorkflowVersionMap.FlowchartNumberGuessIdentity;  
                break;  
        };  
  
        Activity wf = WorkflowVersionMap.GetWorkflowDefinition(identity);  
  
        WorkflowApplication wfApp = new WorkflowApplication(wf, inputs, identity);  
  
        // Add the workflow to the list and display the version information.  
        WorkflowStarting = true;  
        InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id);  
        WorkflowVersion.Text = identity.ToString();  
        WorkflowStarting = false;  
  
        // Configure the instance store, extensions, and   
        // workflow lifecycle handlers.  
        ConfigureWorkflowApplication(wfApp);  
  
        // Start the workflow.  
        wfApp.Run();  
    }  
    ```  
  
###  <a name="BKMK_ResumeWorkflow"></a> <span data-ttu-id="50b88-303">Aby wznowić przepływ pracy</span><span class="sxs-lookup"><span data-stu-id="50b88-303">To resume a workflow</span></span>  
  
1.  <span data-ttu-id="50b88-304">Dodaj `Click` Obsługa `EnterGuess`.</span><span class="sxs-lookup"><span data-stu-id="50b88-304">Add a `Click` handler for `EnterGuess`.</span></span> <span data-ttu-id="50b88-305">Aby dodać program obsługi, przełącz się do **widoku projektu** formularza, a następnie kliknij dwukrotnie plik `EnterGuess`.</span><span class="sxs-lookup"><span data-stu-id="50b88-305">To add the handler, switch to **Design View** for the form, and double-click `EnterGuess`.</span></span> <span data-ttu-id="50b88-306">Gdy użytkownik kliknie ten przycisk, przepływ pracy zostanie wznowione.</span><span class="sxs-lookup"><span data-stu-id="50b88-306">Whenever the user clicks this button a workflow is resumed.</span></span>  
  
    ```vb  
    Private Sub EnterGuess_Click(sender As Object, e As EventArgs) Handles EnterGuess.Click  
  
    End Sub  
    ```  
  
    ```csharp  
    private void EnterGuess_Click(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
2.  <span data-ttu-id="50b88-307">Dodaj następujący kod, aby upewnić się, że przepływ pracy jest zaznaczony na liście przepływów pracy i że odgadnięcia użytkownika jest prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="50b88-307">Add the following code to ensure that a workflow is selected in the workflow list, and that the user's guess is valid.</span></span>  
  
    ```vb  
    If WorkflowInstanceId = Guid.Empty Then  
        MessageBox.Show("Please select a workflow.")  
        Return  
    End If  
  
    Dim userGuess As Integer  
    If Not Int32.TryParse(Guess.Text, userGuess) Then  
        MessageBox.Show("Please enter an integer.")  
        Guess.SelectAll()  
        Guess.Focus()  
        Return  
    End If  
    ```  
  
    ```csharp  
    if (WorkflowInstanceId == Guid.Empty)  
    {  
        MessageBox.Show("Please select a workflow.");  
        return;  
    }  
  
    int guess;  
    if (!Int32.TryParse(Guess.Text, out guess))  
    {  
        MessageBox.Show("Please enter an integer.");  
        Guess.SelectAll();  
        Guess.Focus();  
        return;  
    }  
    ```  
  
3.  <span data-ttu-id="50b88-308">Następnie należy pobrać `WorkflowApplicationInstance` z istniejącym wystąpieniem przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="50b88-308">Next, retrieve the `WorkflowApplicationInstance` of the persisted workflow instance.</span></span> <span data-ttu-id="50b88-309">A `WorkflowApplicationInstance` reprezentuje utrwalonego wystąpienia przepływu pracy, który nie został jeszcze skojarzony z definicją przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="50b88-309">A `WorkflowApplicationInstance` represents a persisted workflow instance that has not yet been associated with a workflow definition.</span></span> <span data-ttu-id="50b88-310">`DefinitionIdentity` z `WorkflowApplicationInstance` zawiera `WorkflowIdentity` z istniejącym wystąpieniem przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="50b88-310">The `DefinitionIdentity` of the `WorkflowApplicationInstance` contains the `WorkflowIdentity` of the persisted workflow instance.</span></span> <span data-ttu-id="50b88-311">W tym samouczku `WorkflowVersionMap` klasy narzędzie służy do mapowania `WorkflowIdentity` do definicji poprawne przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="50b88-311">In this tutorial, the `WorkflowVersionMap` utility class is used to map the `WorkflowIdentity` to the correct workflow definition.</span></span> <span data-ttu-id="50b88-312">Po pobraniu definicji przepływu pracy `WorkflowApplication` jest tworzony przy użyciu definicji przepływu pracy poprawne.</span><span class="sxs-lookup"><span data-stu-id="50b88-312">Once the workflow definition is retrieved, a `WorkflowApplication` is created, using the correct workflow definition.</span></span>  
  
    ```vb  
    Dim instance As WorkflowApplicationInstance = _  
        WorkflowApplication.GetInstance(WorkflowInstanceId, store)  
  
    'Use the persisted WorkflowIdentity to retrieve the correct workflow  
    'definition from the dictionary.  
    Dim wf As Activity = _  
        WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity)  
  
    'Associate the WorkflowApplication with the correct definition  
    Dim wfApp As WorkflowApplication = _  
        New WorkflowApplication(wf, instance.DefinitionIdentity)  
    ```  
  
    ```csharp  
    WorkflowApplicationInstance instance =  
        WorkflowApplication.GetInstance(WorkflowInstanceId, store);  
  
    // Use the persisted WorkflowIdentity to retrieve the correct workflow  
    // definition from the dictionary.  
    Activity wf =  
        WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity);  
  
    // Associate the WorkflowApplication with the correct definition  
    WorkflowApplication wfApp =  
        new WorkflowApplication(wf, instance.DefinitionIdentity);  
    ```  
  
4.  <span data-ttu-id="50b88-313">Gdy `WorkflowApplication` jest utworzony, skonfiguruj magazyn wystąpień przepływu pracy cyklu życia obsługi i rozszerzeń, wywołując `ConfigureWorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="50b88-313">Once the `WorkflowApplication` is created, configure the instance store, workflow lifecycle handlers, and extensions by calling `ConfigureWorkflowApplication`.</span></span> <span data-ttu-id="50b88-314">Te kroki należy wykonać każdym nowej `WorkflowApplication` zostanie utworzony, muszą być wykonywane przed wystąpieniem przepływu pracy jest ładowany do `WorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="50b88-314">These steps must be done every time a new `WorkflowApplication` is created, and they must be done before the workflow instance is loaded into the `WorkflowApplication`.</span></span> <span data-ttu-id="50b88-315">Po załadowaniu przepływ pracy zostanie wznowione odgadnięcia użytkownika.</span><span class="sxs-lookup"><span data-stu-id="50b88-315">After the workflow is loaded, it is resumed with the user's guess.</span></span>  
  
    ```vb  
    'Configure the extensions and lifecycle handlers.  
    'Do this before the instance is loaded. Once the instance is  
    'loaded it is too late to add extensions.  
    ConfigureWorkflowApplication(wfApp)  
  
    'Load the workflow.  
    wfApp.Load(instance)  
  
    'Resume the workflow.  
    wfApp.ResumeBookmark("EnterGuess", userGuess)  
    ```  
  
    ```csharp  
    // Configure the extensions and lifecycle handlers.  
    // Do this before the instance is loaded. Once the instance is  
    // loaded it is too late to add extensions.  
    ConfigureWorkflowApplication(wfApp);  
  
    // Load the workflow.  
    wfApp.Load(instance);  
  
    // Resume the workflow.  
    wfApp.ResumeBookmark("EnterGuess", guess);  
    ```  
  
5.  <span data-ttu-id="50b88-316">Na koniec wyczyść pole tekstowe odgadnięcia i przygotować formularz, aby akceptować inny wynik.</span><span class="sxs-lookup"><span data-stu-id="50b88-316">Finally, clear the guess textbox and prepare the form to accept another guess.</span></span>  
  
    ```vb  
    'Clear the Guess textbox.  
    Guess.Clear()  
    Guess.Focus()  
    ```  
  
    ```csharp  
    // Clear the Guess textbox.  
    Guess.Clear();  
    Guess.Focus();  
    ```  
  
     <span data-ttu-id="50b88-317">Poniższy przykład jest gotowy `EnterGuess_Click` programu obsługi.</span><span class="sxs-lookup"><span data-stu-id="50b88-317">The following example is the completed `EnterGuess_Click` handler.</span></span>  
  
    ```vb  
    Private Sub EnterGuess_Click(sender As Object, e As EventArgs) Handles EnterGuess.Click  
        If WorkflowInstanceId = Guid.Empty Then  
            MessageBox.Show("Please select a workflow.")  
            Return  
        End If  
  
        Dim userGuess As Integer  
        If Not Int32.TryParse(Guess.Text, userGuess) Then  
            MessageBox.Show("Please enter an integer.")  
            Guess.SelectAll()  
            Guess.Focus()  
            Return  
        End If  
  
        Dim instance As WorkflowApplicationInstance = _  
            WorkflowApplication.GetInstance(WorkflowInstanceId, store)  
  
        'Use the persisted WorkflowIdentity to retrieve the correct workflow  
        'definition from the dictionary.  
        Dim wf As Activity = _  
            WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity)  
  
        'Associate the WorkflowApplication with the correct definition  
        Dim wfApp As WorkflowApplication = _  
            New WorkflowApplication(wf, instance.DefinitionIdentity)  
  
        'Configure the extensions and lifecycle handlers.  
        'Do this before the instance is loaded. Once the instance is  
        'loaded it is too late to add extensions.  
        ConfigureWorkflowApplication(wfApp)  
  
        'Load the workflow.  
        wfApp.Load(instance)  
  
        'Resume the workflow.  
        wfApp.ResumeBookmark("EnterGuess", userGuess)  
  
        'Clear the Guess textbox.  
        Guess.Clear()  
        Guess.Focus()  
    End Sub  
    ```  
  
    ```csharp  
    private void EnterGuess_Click(object sender, EventArgs e)  
    {  
        if (WorkflowInstanceId == Guid.Empty)  
        {  
            MessageBox.Show("Please select a workflow.");  
            return;  
        }  
  
        int guess;  
        if (!Int32.TryParse(Guess.Text, out guess))  
        {  
            MessageBox.Show("Please enter an integer.");  
            Guess.SelectAll();  
            Guess.Focus();  
            return;  
        }  
  
        WorkflowApplicationInstance instance =  
            WorkflowApplication.GetInstance(WorkflowInstanceId, store);  
  
        // Use the persisted WorkflowIdentity to retrieve the correct workflow  
        // definition from the dictionary.  
        Activity wf =  
            WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity);  
  
        // Associate the WorkflowApplication with the correct definition  
        WorkflowApplication wfApp =  
            new WorkflowApplication(wf, instance.DefinitionIdentity);  
  
        // Configure the extensions and lifecycle handlers.  
        // Do this before the instance is loaded. Once the instance is  
        // loaded it is too late to add extensions.  
        ConfigureWorkflowApplication(wfApp);  
  
        // Load the workflow.  
        wfApp.Load(instance);  
  
        // Resume the workflow.  
        wfApp.ResumeBookmark("EnterGuess", guess);  
  
        // Clear the Guess textbox.  
        Guess.Clear();  
        Guess.Focus();  
    }  
    ```  
  
###  <a name="BKMK_TerminateWorkflow"></a> <span data-ttu-id="50b88-318">Aby zakończyć przepływ pracy</span><span class="sxs-lookup"><span data-stu-id="50b88-318">To terminate a workflow</span></span>  
  
1.  <span data-ttu-id="50b88-319">Dodaj `Click` Obsługa `QuitGame`.</span><span class="sxs-lookup"><span data-stu-id="50b88-319">Add a `Click` handler for `QuitGame`.</span></span> <span data-ttu-id="50b88-320">Aby dodać program obsługi, przełącz się do **widoku projektu** formularza, a następnie kliknij dwukrotnie plik `QuitGame`.</span><span class="sxs-lookup"><span data-stu-id="50b88-320">To add the handler, switch to **Design View** for the form, and double-click `QuitGame`.</span></span> <span data-ttu-id="50b88-321">Gdy użytkownik kliknie ten przycisk aktualnie wybranego przepływu pracy zostało przerwane.</span><span class="sxs-lookup"><span data-stu-id="50b88-321">Whenever the user clicks this button the currently selected workflow is terminated.</span></span>  
  
    ```vb  
    Private Sub QuitGame_Click(sender As Object, e As EventArgs) Handles QuitGame.Click  
  
    End Sub  
    ```  
  
    ```csharp  
    private void QuitGame_Click(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
2.  <span data-ttu-id="50b88-322">Dodaj następujący kod do `QuitGame_Click` programu obsługi.</span><span class="sxs-lookup"><span data-stu-id="50b88-322">Add the following code to the `QuitGame_Click` handler.</span></span> <span data-ttu-id="50b88-323">Ten kod najpierw sprawdza, upewnij się, że przepływ pracy jest zaznaczony na liście przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="50b88-323">This code first checks to ensure that a workflow is selected in the workflow list.</span></span> <span data-ttu-id="50b88-324">A następnie ładuje utrwalonego wystąpienia do `WorkflowApplicationInstance`, używa `DefinitionIdentity` do określenia definicji przepływu pracy poprawne, a następnie inicjuje `WorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="50b88-324">Then it loads the persisted instance into a `WorkflowApplicationInstance`, uses the `DefinitionIdentity` to determine the correct workflow definition, and then initializes the `WorkflowApplication`.</span></span> <span data-ttu-id="50b88-325">Następnie rozszerzenia i obsługi cyklu życia przepływu pracy są skonfigurowane przy użyciu wywołania do `ConfigureWorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="50b88-325">Next the extensions and workflow lifecycle handlers are configured with a call to `ConfigureWorkflowApplication`.</span></span> <span data-ttu-id="50b88-326">Raz `WorkflowApplication` jest skonfigurowany, jej załadowaniu, a następnie `Terminate` jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="50b88-326">Once the `WorkflowApplication` is configured, it is loaded, and then `Terminate` is called.</span></span>  
  
    ```vb  
    If WorkflowInstanceId = Guid.Empty Then  
        MessageBox.Show("Please select a workflow.")  
        Return  
    End If  
  
    Dim instance As WorkflowApplicationInstance = _  
        WorkflowApplication.GetInstance(WorkflowInstanceId, store)  
  
    'Use the persisted WorkflowIdentity to retrieve the correct workflow  
    'definition from the dictionary.  
    Dim wf As Activity = WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity)  
  
    'Associate the WorkflowApplication with the correct definition.  
    Dim wfApp As WorkflowApplication = _  
        New WorkflowApplication(wf, instance.DefinitionIdentity)  
  
    'Configure the extensions and lifecycle handlers.  
    ConfigureWorkflowApplication(wfApp)  
  
    'Load the workflow.  
    wfApp.Load(instance)  
  
    'Terminate the workflow.  
    wfApp.Terminate("User resigns.")  
    ```  
  
    ```csharp  
    if (WorkflowInstanceId == Guid.Empty)  
    {  
        MessageBox.Show("Please select a workflow.");  
        return;  
    }  
  
    WorkflowApplicationInstance instance =  
        WorkflowApplication.GetInstance(WorkflowInstanceId, store);  
  
    // Use the persisted WorkflowIdentity to retrieve the correct workflow  
    // definition from the dictionary.  
    Activity wf = WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity);  
  
    // Associate the WorkflowApplication with the correct definition  
    WorkflowApplication wfApp =  
        new WorkflowApplication(wf, instance.DefinitionIdentity);  
  
    // Configure the extensions and lifecycle handlers  
    ConfigureWorkflowApplication(wfApp);  
  
    // Load the workflow.  
    wfApp.Load(instance);  
  
    // Terminate the workflow.  
    wfApp.Terminate("User resigns.");  
    ```  
  
###  <a name="BKMK_BuildAndRun"></a> <span data-ttu-id="50b88-327">Aby skompilować i uruchomić aplikację</span><span class="sxs-lookup"><span data-stu-id="50b88-327">To build and run the application</span></span>  
  
1.  <span data-ttu-id="50b88-328">Kliknij dwukrotnie **Program.cs** (lub **Module1.vb**) w **Eksploratora rozwiązań** Aby wyświetlić kod.</span><span class="sxs-lookup"><span data-stu-id="50b88-328">Double-click **Program.cs** (or **Module1.vb**) in **Solution Explorer** to display the code.</span></span>  
  
2.  <span data-ttu-id="50b88-329">Dodaj następujący kod `using` (lub `Imports`) instrukcji w górnej części pliku razem z innymi `using` (lub `Imports`) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="50b88-329">Add the following `using` (or `Imports`) statement at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports System.Windows.Forms  
    ```  
  
    ```csharp  
    using System.Windows.Forms;  
    ```  
  
3.  <span data-ttu-id="50b88-330">Usunąć lub skomentować istniejącego przepływu pracy obsługującego kod z [porady: uruchamianie przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)i zastąp go następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="50b88-330">Remove or comment out the existing workflow hosting code from [How to: Run a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md), and replace it with the following code.</span></span>  
  
    ```vb  
    Sub Main()  
        Application.EnableVisualStyles()  
        Application.Run(New WorkflowHostForm())  
    End Sub  
    ```  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        Application.EnableVisualStyles();  
        Application.Run(new WorkflowHostForm());  
    }  
    ```  
  
4.  <span data-ttu-id="50b88-331">Kliknij prawym przyciskiem myszy **NumberGuessWorkflowHost** w **Eksploratora rozwiązań** i wybierz polecenie **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="50b88-331">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Properties**.</span></span> <span data-ttu-id="50b88-332">W **aplikacji** określ **aplikacji Windows** dla **typ danych wyjściowych**.</span><span class="sxs-lookup"><span data-stu-id="50b88-332">In the **Application** tab, specify **Windows Application** for the **Output type**.</span></span> <span data-ttu-id="50b88-333">Ten krok jest opcjonalny, ale jeśli go nie zostanie zastosowane oprócz formularzu zostanie wyświetlone okno konsoli.</span><span class="sxs-lookup"><span data-stu-id="50b88-333">This step is optional, but if it is not followed the console window is displayed in addition to the form.</span></span>  
  
5.  <span data-ttu-id="50b88-334">Naciśnij klawisze Ctrl + Shift + B, aby skompilować aplikację.</span><span class="sxs-lookup"><span data-stu-id="50b88-334">Press Ctrl+Shift+B to build the application.</span></span>  
  
6.  <span data-ttu-id="50b88-335">Upewnij się, że **NumberGuessWorkflowHost** jest ustawiony jako aplikacja do uruchomienia, a następnie naciśnij klawisz Ctrl + F5, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="50b88-335">Ensure that **NumberGuessWorkflowHost** is set as the startup application, and press Ctrl+F5 to start the application.</span></span>  
  
7.  <span data-ttu-id="50b88-336">Wybierz zakres do odgadnięcia gier i typ przepływu pracy, aby rozpocząć, a następnie kliknij przycisk **nowych gier**.</span><span class="sxs-lookup"><span data-stu-id="50b88-336">Select a range for the guessing game and the type of workflow to start, and click **New Game**.</span></span> <span data-ttu-id="50b88-337">Wprowadź odgadnięcia w **odgadnięcia** pole, a następnie kliknij przycisk **Przejdź** przesłać przypuszczenie.</span><span class="sxs-lookup"><span data-stu-id="50b88-337">Enter a guess in the **Guess** box and click **Go** to submit your guess.</span></span> <span data-ttu-id="50b88-338">Należy pamiętać, że dane wyjściowe z `WriteLine` działania jest wyświetlany w formularzu.</span><span class="sxs-lookup"><span data-stu-id="50b88-338">Note that the output from the `WriteLine` activities is displayed on the form.</span></span>  
  
8.  <span data-ttu-id="50b88-339">Uruchom wiele przepływów pracy przy użyciu typów innego przepływu pracy i liczba zakresów, wprowadzić kilka prób i przełączać się między przepływami pracy, wybierając z **identyfikator wystąpienia przepływu pracy** listy.</span><span class="sxs-lookup"><span data-stu-id="50b88-339">Start several workflows using different workflow types and number ranges, enter some guesses, and switch between the workflows by selecting from the **Workflow Instance Id** list.</span></span>  
  
     <span data-ttu-id="50b88-340">Należy pamiętać, że przełączenie do nowego przepływu pracy liczbę poprzednich prób i postęp przepływu pracy nie są wyświetlane w oknie stanu.</span><span class="sxs-lookup"><span data-stu-id="50b88-340">Note that when you switch to a new workflow, the previous guesses and progress of the workflow are not displayed in the status window.</span></span> <span data-ttu-id="50b88-341">Powodów, dla którego stan nie jest dostępna jest, ponieważ nie jest przechwytywane i zapisane w dowolnym miejscu.</span><span class="sxs-lookup"><span data-stu-id="50b88-341">The reason the status is not available is because it is not captured and saved anywhere.</span></span> <span data-ttu-id="50b88-342">W następnym kroku samouczka [porady: Tworzenie niestandardowego uczestnika śledzenia](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md), Utwórz niestandardowe śledzenia uczestnika, który zapisuje te informacje.</span><span class="sxs-lookup"><span data-stu-id="50b88-342">In the next step of the tutorial, [How to: Create a Custom Tracking Participant](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md), you create a custom tracking participant that saves this information.</span></span>
