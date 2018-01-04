---
title: "Porady: tworzenie i uruchamianie długi uruchamiania przepływu pracy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: c0043c89-2192-43c9-986d-3ecec4dd8c9c
caps.latest.revision: "40"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a667c303cd1a98e0b027ca2026fe9c719e6baf4f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-and-run-a-long-running-workflow"></a><span data-ttu-id="681ce-102">Porady: tworzenie i uruchamianie długi uruchamiania przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="681ce-102">How to: Create and Run a Long Running Workflow</span></span>
<span data-ttu-id="681ce-103">Jedną z centralnej funkcji [!INCLUDE[wf](../../../includes/wf-md.md)] jest możliwość środowiska uruchomieniowego utrwalić i zwolnić bezczynne przepływy pracy z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="681ce-103">One of the central features of [!INCLUDE[wf](../../../includes/wf-md.md)] is the runtime’s ability to persist and unload idle workflows to a database.</span></span> <span data-ttu-id="681ce-104">Kroki opisane w [porady: uruchamianie przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) przedstawiono podstawowe informacje dotyczące obsługi przepływu pracy za pomocą aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="681ce-104">The steps in [How to: Run a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) demonstrated the basics of workflow hosting using a console application.</span></span> <span data-ttu-id="681ce-105">Przykłady zostały przedstawione początkowy przepływy pracy, programy obsługi cyklu życia przepływu pracy i wznawianie zakładki.</span><span class="sxs-lookup"><span data-stu-id="681ce-105">Examples were shown of starting workflows, workflow lifecycle handlers, and resuming bookmarks.</span></span> <span data-ttu-id="681ce-106">W celu zaprezentowania skutecznie utrwalania przepływu pracy, konieczne jest bardziej złożonych hosta przepływu pracy obsługującego uruchamianie i wznawianie wielu wystąpień przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="681ce-106">In order to demonstrate workflow persistence effectively, a more complex workflow host is required that supports starting and resuming multiple workflow instances.</span></span> <span data-ttu-id="681ce-107">Ten krok samouczka przedstawia sposób tworzenia hosta formularzy systemu Windows, aplikacji, która obsługuje uruchamianie i wznawianie wielu wystąpień przepływu pracy, utrwalania przepływu pracy i stanowi podstawę do zaawansowanych funkcji, takich jak śledzenia i wersjonowania, które są zostało to pokazane w kolejnych krokach samouczka.</span><span class="sxs-lookup"><span data-stu-id="681ce-107">This step in the tutorial demonstrates how to create a Windows form host application that supports starting and resuming multiple workflow instances, workflow persistence, and provides a basis for the advanced features such as tracking and versioning that are demonstrated in subsequent tutorial steps.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="681ce-108">Ten samouczek kroku oraz kolejnych kroków należy używać wszystkich trzech typów przepływu pracy z [porady: tworzenie przepływów pracy](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="681ce-108">This tutorial step and the subsequent steps use all three workflow types from [How to: Create a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md).</span></span> <span data-ttu-id="681ce-109">Jeśli nie zostało ukończone wszystkie trzy typy możesz pobrać ukończoną wersję kroki z [Windows Workflow Foundation (WF45) — Samouczek wprowadzający](http://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="681ce-109">If you did not complete all three types you can download a completed version of the steps from [Windows Workflow Foundation (WF45) - Getting Started Tutorial](http://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="681ce-110">Aby pobrać wersję zakończone lub wyświetlić Przewodnik wideo samouczka, zobacz [Windows Workflow Foundation (WF45) — Samouczek wprowadzający](http://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="681ce-110">To download a completed version or view a video walkthrough of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](http://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
## <a name="in-this-topic"></a><span data-ttu-id="681ce-111">W tym temacie:</span><span class="sxs-lookup"><span data-stu-id="681ce-111">In this topic</span></span>  
  
-   [<span data-ttu-id="681ce-112">Aby utworzyć bazę danych trwałości</span><span class="sxs-lookup"><span data-stu-id="681ce-112">To create the persistence database</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_CreatePersistenceDatabase)  
  
-   [<span data-ttu-id="681ce-113">Można dodać odwołania do zestawów DurableInstancing</span><span class="sxs-lookup"><span data-stu-id="681ce-113">To add the reference to the DurableInstancing assemblies</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_AddReference)  
  
-   [<span data-ttu-id="681ce-114">Aby utworzyć formularz hosta przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="681ce-114">To create the workflow host form</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_CreateForm)  
  
-   [<span data-ttu-id="681ce-115">Aby dodać właściwości i metody pomocnicze formularza</span><span class="sxs-lookup"><span data-stu-id="681ce-115">To add the properties and helper methods of the form</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_AddHelperMethods)  
  
-   [<span data-ttu-id="681ce-116">Aby skonfigurować Magazyn wystąpienia przepływu pracy obsługi cyklu życia i rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="681ce-116">To configure the instance store, workflow lifecycle handlers, and extensions</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_ConfigureWorkflowApplication)  
  
-   [<span data-ttu-id="681ce-117">Aby włączyć uruchamianie i wznawianie wielu typów przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="681ce-117">To enable starting and resuming multiple workflow types</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_WorkflowVersionMap)  
  
-   [<span data-ttu-id="681ce-118">Aby uruchomić nowy przepływ pracy</span><span class="sxs-lookup"><span data-stu-id="681ce-118">To start a new workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_StartWorkflow)  
  
-   [<span data-ttu-id="681ce-119">Aby wznowić przepływ pracy</span><span class="sxs-lookup"><span data-stu-id="681ce-119">To resume a workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_ResumeWorkflow)  
  
-   [<span data-ttu-id="681ce-120">Zakończenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="681ce-120">To terminate a workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_TerminateWorkflow)  
  
-   [<span data-ttu-id="681ce-121">Aby skompilować i uruchomić aplikację</span><span class="sxs-lookup"><span data-stu-id="681ce-121">To build and run the application</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_BuildAndRun)  
  
###  <a name="BKMK_CreatePersistenceDatabase"></a><span data-ttu-id="681ce-122">Aby utworzyć bazę danych trwałości</span><span class="sxs-lookup"><span data-stu-id="681ce-122">To create the persistence database</span></span>  
  
1.  <span data-ttu-id="681ce-123">Otwórz program SQL Server Management Studio i połączyć się z serwerem lokalnym, na przykład **. \SQLEXPRESS**.</span><span class="sxs-lookup"><span data-stu-id="681ce-123">Open SQL Server Management Studio and connect to the local server, for example **.\SQLEXPRESS**.</span></span> <span data-ttu-id="681ce-124">Kliknij prawym przyciskiem myszy **baz danych** węzła na serwerze lokalnym, a następnie wybierz **nową bazę danych**.</span><span class="sxs-lookup"><span data-stu-id="681ce-124">Right-click the **Databases** node on the local server, and select **New Database**.</span></span> <span data-ttu-id="681ce-125">Nazwa nowej bazy danych **WF45GettingStartedTutorial**Zaakceptuj wszystkie inne wartości, a wybierz **OK**.</span><span class="sxs-lookup"><span data-stu-id="681ce-125">Name the new database **WF45GettingStartedTutorial**, accept all other values, and select **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="681ce-126">Upewnij się, że masz **Create Database** uprawnienia na serwerze lokalnym, przed utworzeniem bazy danych.</span><span class="sxs-lookup"><span data-stu-id="681ce-126">Ensure that you have **Create Database** permission on the local server before creating the database.</span></span>  
  
2.  <span data-ttu-id="681ce-127">Wybierz **Otwórz**, **pliku** z **pliku** menu.</span><span class="sxs-lookup"><span data-stu-id="681ce-127">Choose **Open**, **File** from the **File** menu.</span></span> <span data-ttu-id="681ce-128">Przejdź do folderu:`C:\Windows\Microsoft.NET\Framework\4.0.30319\sql\en`</span><span class="sxs-lookup"><span data-stu-id="681ce-128">Browse to the following folder: `C:\Windows\Microsoft.NET\Framework\4.0.30319\sql\en`</span></span>  
  
     <span data-ttu-id="681ce-129">Wybierz następujące dwa pliki, a następnie kliknij przycisk **Otwórz**.</span><span class="sxs-lookup"><span data-stu-id="681ce-129">Select the following two files and click **Open**.</span></span>  
  
    -   <span data-ttu-id="681ce-130">SqlWorkflowInstanceStoreLogic.sql</span><span class="sxs-lookup"><span data-stu-id="681ce-130">SqlWorkflowInstanceStoreLogic.sql</span></span>  
  
    -   <span data-ttu-id="681ce-131">SqlWorkflowInstanceStoreSchema.sql</span><span class="sxs-lookup"><span data-stu-id="681ce-131">SqlWorkflowInstanceStoreSchema.sql</span></span>  
  
3.  <span data-ttu-id="681ce-132">Wybierz **SqlWorkflowInstanceStoreSchema.sql** z **okna** menu.</span><span class="sxs-lookup"><span data-stu-id="681ce-132">Choose **SqlWorkflowInstanceStoreSchema.sql** from the **Window** menu.</span></span> <span data-ttu-id="681ce-133">Upewnij się, że **WF45GettingStartedTutorial** wybrano **dostępnych baz danych** listy rozwijanej i wybierz polecenie **Execute** z **zapytania**menu.</span><span class="sxs-lookup"><span data-stu-id="681ce-133">Ensure that **WF45GettingStartedTutorial** is selected in the **Available Databases** drop-down and choose **Execute** from the **Query** menu.</span></span>  
  
4.  <span data-ttu-id="681ce-134">Wybierz **SqlWorkflowInstanceStoreLogic.sql** z **okna** menu.</span><span class="sxs-lookup"><span data-stu-id="681ce-134">Choose **SqlWorkflowInstanceStoreLogic.sql** from the **Window** menu.</span></span> <span data-ttu-id="681ce-135">Upewnij się, że **WF45GettingStartedTutorial** wybrano **dostępnych baz danych** listy rozwijanej i wybierz polecenie **Execute** z **zapytania**menu.</span><span class="sxs-lookup"><span data-stu-id="681ce-135">Ensure that **WF45GettingStartedTutorial** is selected in the **Available Databases** drop-down and choose **Execute** from the **Query** menu.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="681ce-136">Należy wykonać dwa poprzednie kroki w odpowiedniej kolejności.</span><span class="sxs-lookup"><span data-stu-id="681ce-136">It is important to perform the previous two steps in the correct order.</span></span> <span data-ttu-id="681ce-137">Jeśli zapytania są wykonywane poza kolejnością, występują błędy, a trwałości bazy danych nie jest poprawnie skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="681ce-137">If the queries are executed out of order, errors occur and the persistence database is not configured correctly.</span></span>  
  
###  <a name="BKMK_AddReference"></a><span data-ttu-id="681ce-138">Można dodać odwołania do zestawów DurableInstancing</span><span class="sxs-lookup"><span data-stu-id="681ce-138">To add the reference to the DurableInstancing assemblies</span></span>  
  
1.  <span data-ttu-id="681ce-139">Kliknij prawym przyciskiem myszy **NumberGuessWorkflowHost** w **Eksploratora rozwiązań** i wybierz **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="681ce-139">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and select **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="681ce-140">Wybierz **zestawy** z **Dodaj odwołanie** listy i typ `DurableInstancing` do **wyszukiwania zestawów** pole.</span><span class="sxs-lookup"><span data-stu-id="681ce-140">Select **Assemblies** from the **Add Reference** list, and type `DurableInstancing` into the **Search Assemblies** box.</span></span> <span data-ttu-id="681ce-141">Filtry zestawy i ułatwia wybierz żądany odwołań.</span><span class="sxs-lookup"><span data-stu-id="681ce-141">This filters the assemblies and makes the desired references easier to select.</span></span>  
  
3.  <span data-ttu-id="681ce-142">Zaznacz pole wyboru obok **System.Activities.DurableInstancing** i **System.Runtime.DurableInstancing** z **wyniki wyszukiwania** listy, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="681ce-142">Check the checkbox beside **System.Activities.DurableInstancing** and **System.Runtime.DurableInstancing** from the **Search Results** list, and click **OK**.</span></span>  
  
###  <a name="BKMK_CreateForm"></a><span data-ttu-id="681ce-143">Aby utworzyć formularz hosta przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="681ce-143">To create the workflow host form</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="681ce-144">W tej procedurze opisano sposób dodać i skonfigurować ręcznie formularza.</span><span class="sxs-lookup"><span data-stu-id="681ce-144">The steps in this procedure describe how to add and configure the form manually.</span></span> <span data-ttu-id="681ce-145">W razie potrzeby można pobrać plików rozwiązania samouczka i Dodaj wypełnionego formularza do projektu.</span><span class="sxs-lookup"><span data-stu-id="681ce-145">If desired, you can download the solution files for the tutorial and add the completed form to the project.</span></span> <span data-ttu-id="681ce-146">Aby pobrać pliki samouczka, zobacz [Windows Workflow Foundation (WF45) — Samouczek wprowadzający](http://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="681ce-146">To download the tutorial files, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](http://go.microsoft.com/fwlink/?LinkID=248976).</span></span> <span data-ttu-id="681ce-147">Po pobraniu plików, kliknij prawym przyciskiem myszy **NumberGuessWorkflowHost** i wybierz polecenie **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="681ce-147">Once the files are downloaded, right-click **NumberGuessWorkflowHost** and choose **Add Reference**.</span></span> <span data-ttu-id="681ce-148">Dodaj odwołanie do **System.Windows.Forms** i **System.Drawing**.</span><span class="sxs-lookup"><span data-stu-id="681ce-148">Add a reference to **System.Windows.Forms** and **System.Drawing**.</span></span> <span data-ttu-id="681ce-149">Te odwołania są dodawane automatycznie po dodaniu nowego formularza z **Dodaj**, **nowy element** menu, ale należy je dodać ręcznie, podczas importowania formularza.</span><span class="sxs-lookup"><span data-stu-id="681ce-149">These references are added automatically if you add a new form from the **Add**, **New Item** menu, but must be added manually when importing a form.</span></span> <span data-ttu-id="681ce-150">Po dodaniu odwołań, kliknij prawym przyciskiem myszy **NumberGuessWorkflowHost** w **Eksploratora rozwiązań** i wybierz polecenie **Dodaj**, **istniejący element**.</span><span class="sxs-lookup"><span data-stu-id="681ce-150">Once the references are added, right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **Existing Item**.</span></span> <span data-ttu-id="681ce-151">Przejdź do `Form` folderu plików projektu, zaznacz opcję **WorkflowHostForm.cs** (lub **WorkflowHostForm.vb**) i kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="681ce-151">Browse to the `Form` folder in the project files, select **WorkflowHostForm.cs** (or **WorkflowHostForm.vb**), and click **Add**.</span></span> <span data-ttu-id="681ce-152">Jeśli chcesz zaimportować formularz, a następnie można przejść do następnej sekcji [można dodać właściwości i metody pomocnicze formularza](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_AddHelperMethods).</span><span class="sxs-lookup"><span data-stu-id="681ce-152">If you choose to import the form, then you can skip down to the next section, [To add the properties and helper methods of the form](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_AddHelperMethods).</span></span>  
  
1.  <span data-ttu-id="681ce-153">Kliknij prawym przyciskiem myszy **NumberGuessWorkflowHost** w **Eksploratora rozwiązań** i wybierz polecenie **Dodaj**, **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="681ce-153">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **New Item**.</span></span>  
  
2.  <span data-ttu-id="681ce-154">W **zainstalowana** szablonów wybierz **formularza systemu Windows**, typ `WorkflowHostForm` w **nazwa** i kliknij **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="681ce-154">In the **Installed** templates list, choose **Windows Form**, type `WorkflowHostForm` in the **Name** box, and click **Add**.</span></span>  
  
3.  <span data-ttu-id="681ce-155">W formularzu, należy skonfigurować następujące właściwości.</span><span class="sxs-lookup"><span data-stu-id="681ce-155">Configure the following properties on the form.</span></span>  
  
    |<span data-ttu-id="681ce-156">Właściwość</span><span class="sxs-lookup"><span data-stu-id="681ce-156">Property</span></span>|<span data-ttu-id="681ce-157">Wartość</span><span class="sxs-lookup"><span data-stu-id="681ce-157">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="681ce-158">FormBorderStyle</span><span class="sxs-lookup"><span data-stu-id="681ce-158">FormBorderStyle</span></span>|<span data-ttu-id="681ce-159">FixedSingle</span><span class="sxs-lookup"><span data-stu-id="681ce-159">FixedSingle</span></span>|  
    |<span data-ttu-id="681ce-160">MaximizeBox</span><span class="sxs-lookup"><span data-stu-id="681ce-160">MaximizeBox</span></span>|<span data-ttu-id="681ce-161">False</span><span class="sxs-lookup"><span data-stu-id="681ce-161">False</span></span>|  
    |<span data-ttu-id="681ce-162">Rozmiar</span><span class="sxs-lookup"><span data-stu-id="681ce-162">Size</span></span>|<span data-ttu-id="681ce-163">400, 420</span><span class="sxs-lookup"><span data-stu-id="681ce-163">400, 420</span></span>|  
  
4.  <span data-ttu-id="681ce-164">Dodaj następujących formantów do formularza w kolejności określonej i skonfigurować właściwości zgodnie z instrukcją.</span><span class="sxs-lookup"><span data-stu-id="681ce-164">Add the following controls to the form in the order specified and configure the properties as directed.</span></span>  
  
    |<span data-ttu-id="681ce-165">Formant</span><span class="sxs-lookup"><span data-stu-id="681ce-165">Control</span></span>|<span data-ttu-id="681ce-166">Właściwość: wartość</span><span class="sxs-lookup"><span data-stu-id="681ce-166">Property: Value</span></span>|  
    |-------------|---------------------|  
    |<span data-ttu-id="681ce-167">**Przycisk**</span><span class="sxs-lookup"><span data-stu-id="681ce-167">**Button**</span></span>|<span data-ttu-id="681ce-168">Nazwa: NewGame</span><span class="sxs-lookup"><span data-stu-id="681ce-168">Name: NewGame</span></span><br /><br /> <span data-ttu-id="681ce-169">Lokalizacja: 13, 13</span><span class="sxs-lookup"><span data-stu-id="681ce-169">Location: 13, 13</span></span><br /><br /> <span data-ttu-id="681ce-170">Rozmiar: 75, 23</span><span class="sxs-lookup"><span data-stu-id="681ce-170">Size: 75, 23</span></span><br /><br /> <span data-ttu-id="681ce-171">Tekst: Gry nowy</span><span class="sxs-lookup"><span data-stu-id="681ce-171">Text: New Game</span></span>|  
    |<span data-ttu-id="681ce-172">**Etykieta**</span><span class="sxs-lookup"><span data-stu-id="681ce-172">**Label**</span></span>|<span data-ttu-id="681ce-173">Lokalizacji: 94, 18</span><span class="sxs-lookup"><span data-stu-id="681ce-173">Location: 94, 18</span></span><br /><br /> <span data-ttu-id="681ce-174">Tekst: Liczba z przedziału od 1 do odgadnięcia</span><span class="sxs-lookup"><span data-stu-id="681ce-174">Text: Guess a number from 1 to</span></span>|  
    |<span data-ttu-id="681ce-175">**ComboBox**</span><span class="sxs-lookup"><span data-stu-id="681ce-175">**ComboBox**</span></span>|<span data-ttu-id="681ce-176">Nazwa: NumberRange</span><span class="sxs-lookup"><span data-stu-id="681ce-176">Name: NumberRange</span></span><br /><br /> <span data-ttu-id="681ce-177">Parametr DropDownStyle: Lista DropDownList</span><span class="sxs-lookup"><span data-stu-id="681ce-177">DropDownStyle: DropDownList</span></span><br /><br /> <span data-ttu-id="681ce-178">Elementy: 10, 100, 1000</span><span class="sxs-lookup"><span data-stu-id="681ce-178">Items: 10, 100, 1000</span></span><br /><br /> <span data-ttu-id="681ce-179">Lokalizacja: 228, 12</span><span class="sxs-lookup"><span data-stu-id="681ce-179">Location: 228, 12</span></span><br /><br /> <span data-ttu-id="681ce-180">Rozmiar: 143, 21</span><span class="sxs-lookup"><span data-stu-id="681ce-180">Size: 143, 21</span></span>|  
    |<span data-ttu-id="681ce-181">**Etykieta**</span><span class="sxs-lookup"><span data-stu-id="681ce-181">**Label**</span></span>|<span data-ttu-id="681ce-182">Lokalizacji: 13, 43</span><span class="sxs-lookup"><span data-stu-id="681ce-182">Location: 13, 43</span></span><br /><br /> <span data-ttu-id="681ce-183">Tekst: Typ przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="681ce-183">Text: Workflow type</span></span>|  
    |<span data-ttu-id="681ce-184">**ComboBox**</span><span class="sxs-lookup"><span data-stu-id="681ce-184">**ComboBox**</span></span>|<span data-ttu-id="681ce-185">Nazwa: WorkflowType</span><span class="sxs-lookup"><span data-stu-id="681ce-185">Name: WorkflowType</span></span><br /><br /> <span data-ttu-id="681ce-186">Parametr DropDownStyle: Lista DropDownList</span><span class="sxs-lookup"><span data-stu-id="681ce-186">DropDownStyle: DropDownList</span></span><br /><br /> <span data-ttu-id="681ce-187">Elementy: SequentialNumberGuessWorkflow StateMachineNumberGuessWorkflow, FlowchartNumberGuessWorkflow,</span><span class="sxs-lookup"><span data-stu-id="681ce-187">Items: StateMachineNumberGuessWorkflow, FlowchartNumberGuessWorkflow, SequentialNumberGuessWorkflow</span></span><br /><br /> <span data-ttu-id="681ce-188">Lokalizacji: 94, 40</span><span class="sxs-lookup"><span data-stu-id="681ce-188">Location: 94, 40</span></span><br /><br /> <span data-ttu-id="681ce-189">Rozmiar: 277, 21</span><span class="sxs-lookup"><span data-stu-id="681ce-189">Size: 277, 21</span></span>|  
    |<span data-ttu-id="681ce-190">**Etykieta**</span><span class="sxs-lookup"><span data-stu-id="681ce-190">**Label**</span></span>|<span data-ttu-id="681ce-191">Nazwa: WorkflowVersion</span><span class="sxs-lookup"><span data-stu-id="681ce-191">Name: WorkflowVersion</span></span><br /><br /> <span data-ttu-id="681ce-192">Lokalizacji: 13, 362</span><span class="sxs-lookup"><span data-stu-id="681ce-192">Location: 13, 362</span></span><br /><br /> <span data-ttu-id="681ce-193">Tekst: Wersja przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="681ce-193">Text: Workflow version</span></span>|  
    |<span data-ttu-id="681ce-194">**GroupBox**</span><span class="sxs-lookup"><span data-stu-id="681ce-194">**GroupBox**</span></span>|<span data-ttu-id="681ce-195">Lokalizacji: 13, 67</span><span class="sxs-lookup"><span data-stu-id="681ce-195">Location: 13, 67</span></span><br /><br /> <span data-ttu-id="681ce-196">Rozmiar: 358, 287</span><span class="sxs-lookup"><span data-stu-id="681ce-196">Size: 358, 287</span></span><br /><br /> <span data-ttu-id="681ce-197">Tekst: gry</span><span class="sxs-lookup"><span data-stu-id="681ce-197">Text: Game</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="681ce-198">Podczas dodawania z poniższych formantów, umieść je w GroupBox.</span><span class="sxs-lookup"><span data-stu-id="681ce-198">When adding the following controls, put them into the GroupBox.</span></span>  
  
    |<span data-ttu-id="681ce-199">Formant</span><span class="sxs-lookup"><span data-stu-id="681ce-199">Control</span></span>|<span data-ttu-id="681ce-200">Właściwość: wartość</span><span class="sxs-lookup"><span data-stu-id="681ce-200">Property: Value</span></span>|  
    |-------------|---------------------|  
    |<span data-ttu-id="681ce-201">**Etykieta**</span><span class="sxs-lookup"><span data-stu-id="681ce-201">**Label**</span></span>|<span data-ttu-id="681ce-202">Lokalizacji: 7, 20</span><span class="sxs-lookup"><span data-stu-id="681ce-202">Location: 7, 20</span></span><br /><br /> <span data-ttu-id="681ce-203">Tekst: Identyfikator wystąpienia przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="681ce-203">Text: Workflow Instance Id</span></span>|  
    |<span data-ttu-id="681ce-204">**ComboBox**</span><span class="sxs-lookup"><span data-stu-id="681ce-204">**ComboBox**</span></span>|<span data-ttu-id="681ce-205">Nazwa: identyfikator wystąpienia</span><span class="sxs-lookup"><span data-stu-id="681ce-205">Name: InstanceId</span></span><br /><br /> <span data-ttu-id="681ce-206">Parametr DropDownStyle: Lista DropDownList</span><span class="sxs-lookup"><span data-stu-id="681ce-206">DropDownStyle: DropDownList</span></span><br /><br /> <span data-ttu-id="681ce-207">Lokalizacji: 121, 17</span><span class="sxs-lookup"><span data-stu-id="681ce-207">Location: 121, 17</span></span><br /><br /> <span data-ttu-id="681ce-208">Rozmiar: 227, 21</span><span class="sxs-lookup"><span data-stu-id="681ce-208">Size: 227, 21</span></span>|  
    |<span data-ttu-id="681ce-209">**Etykieta**</span><span class="sxs-lookup"><span data-stu-id="681ce-209">**Label**</span></span>|<span data-ttu-id="681ce-210">Lokalizacji: 7, 47</span><span class="sxs-lookup"><span data-stu-id="681ce-210">Location: 7, 47</span></span><br /><br /> <span data-ttu-id="681ce-211">Tekst: odgadnięcia</span><span class="sxs-lookup"><span data-stu-id="681ce-211">Text: Guess</span></span>|  
    |<span data-ttu-id="681ce-212">**TextBox**</span><span class="sxs-lookup"><span data-stu-id="681ce-212">**TextBox**</span></span>|<span data-ttu-id="681ce-213">Nazwa: odgadnięcia</span><span class="sxs-lookup"><span data-stu-id="681ce-213">Name: Guess</span></span><br /><br /> <span data-ttu-id="681ce-214">Lokalizacji: 50, 44</span><span class="sxs-lookup"><span data-stu-id="681ce-214">Location: 50, 44</span></span><br /><br /> <span data-ttu-id="681ce-215">Rozmiar: 65, 20</span><span class="sxs-lookup"><span data-stu-id="681ce-215">Size: 65, 20</span></span>|  
    |<span data-ttu-id="681ce-216">**Przycisk**</span><span class="sxs-lookup"><span data-stu-id="681ce-216">**Button**</span></span>|<span data-ttu-id="681ce-217">Nazwa: EnterGuess</span><span class="sxs-lookup"><span data-stu-id="681ce-217">Name: EnterGuess</span></span><br /><br /> <span data-ttu-id="681ce-218">Lokalizacji: 121, 42</span><span class="sxs-lookup"><span data-stu-id="681ce-218">Location: 121, 42</span></span><br /><br /> <span data-ttu-id="681ce-219">Rozmiar: 75, 23</span><span class="sxs-lookup"><span data-stu-id="681ce-219">Size: 75, 23</span></span><br /><br /> <span data-ttu-id="681ce-220">Tekst: Wynik wprowadź</span><span class="sxs-lookup"><span data-stu-id="681ce-220">Text: Enter Guess</span></span>|  
    |<span data-ttu-id="681ce-221">**Przycisk**</span><span class="sxs-lookup"><span data-stu-id="681ce-221">**Button**</span></span>|<span data-ttu-id="681ce-222">Nazwa: QuitGame</span><span class="sxs-lookup"><span data-stu-id="681ce-222">Name: QuitGame</span></span><br /><br /> <span data-ttu-id="681ce-223">Lokalizacji: 274, 42</span><span class="sxs-lookup"><span data-stu-id="681ce-223">Location: 274, 42</span></span><br /><br /> <span data-ttu-id="681ce-224">Rozmiar: 75, 23</span><span class="sxs-lookup"><span data-stu-id="681ce-224">Size: 75, 23</span></span><br /><br /> <span data-ttu-id="681ce-225">Tekst: Zamknij</span><span class="sxs-lookup"><span data-stu-id="681ce-225">Text: Quit</span></span>|  
    |<span data-ttu-id="681ce-226">**TextBox**</span><span class="sxs-lookup"><span data-stu-id="681ce-226">**TextBox**</span></span>|<span data-ttu-id="681ce-227">Nazwa: WorkflowStatus</span><span class="sxs-lookup"><span data-stu-id="681ce-227">Name: WorkflowStatus</span></span><br /><br /> <span data-ttu-id="681ce-228">Lokalizacja: 10, 73</span><span class="sxs-lookup"><span data-stu-id="681ce-228">Location: 10, 73</span></span><br /><br /> <span data-ttu-id="681ce-229">Wiele linii: True</span><span class="sxs-lookup"><span data-stu-id="681ce-229">Multiline: True</span></span><br /><br /> <span data-ttu-id="681ce-230">Tylko do odczytu: True</span><span class="sxs-lookup"><span data-stu-id="681ce-230">ReadOnly: True</span></span><br /><br /> <span data-ttu-id="681ce-231">Paski przewijania: pionowe</span><span class="sxs-lookup"><span data-stu-id="681ce-231">ScrollBars: Vertical</span></span><br /><br /> <span data-ttu-id="681ce-232">Rozmiar: 338, 208</span><span class="sxs-lookup"><span data-stu-id="681ce-232">Size: 338, 208</span></span>|  
  
5.  <span data-ttu-id="681ce-233">Ustaw **AcceptButton** właściwości formularza, aby **EnterGuess**.</span><span class="sxs-lookup"><span data-stu-id="681ce-233">Set the **AcceptButton** property of the form to **EnterGuess**.</span></span>  
  
 <span data-ttu-id="681ce-234">Poniższy przykład przedstawia wypełnionego formularza.</span><span class="sxs-lookup"><span data-stu-id="681ce-234">The following example illustrates the completed form.</span></span>  
  
 <span data-ttu-id="681ce-235">![WF45 Wprowadzenie formularz hosta przepływu pracy samouczek](../../../docs/framework/windows-workflow-foundation/media/wf45gettingstartedtutorialworkflowhostform.png "WF45GettingStartedTutorialWorkflowHostForm")</span><span class="sxs-lookup"><span data-stu-id="681ce-235">![WF45 Getting Started Tutorial Workflow Host Form](../../../docs/framework/windows-workflow-foundation/media/wf45gettingstartedtutorialworkflowhostform.png "WF45GettingStartedTutorialWorkflowHostForm")</span></span>  
  
###  <a name="BKMK_AddHelperMethods"></a><span data-ttu-id="681ce-236">Aby dodać właściwości i metody pomocnicze formularza</span><span class="sxs-lookup"><span data-stu-id="681ce-236">To add the properties and helper methods of the form</span></span>  
 <span data-ttu-id="681ce-237">Kroki opisane w tej sekcji Dodaj właściwości i metody pomocnicze do klasy formularza, które skonfigurować interfejsu użytkownika w postaci do obsługi uruchomiona i wznawianie numer argumentu przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="681ce-237">The steps in this section add properties and helper methods to the form class that configure the UI of the form to support running and resuming number guess workflows.</span></span>  
  
1.  <span data-ttu-id="681ce-238">Kliknij prawym przyciskiem myszy **WorkflowHostForm** w **Eksploratora rozwiązań** i wybierz polecenie **kod widoku**.</span><span class="sxs-lookup"><span data-stu-id="681ce-238">Right-click **WorkflowHostForm** in **Solution Explorer** and choose **View Code**.</span></span>  
  
2.  <span data-ttu-id="681ce-239">Dodaj następujące `using` (lub `Imports`) instrukcje w górnej części pliku z innym `using` (lub `Imports`) instrukcje.</span><span class="sxs-lookup"><span data-stu-id="681ce-239">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
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
  
3.  <span data-ttu-id="681ce-240">Dodaj następujące deklaracje elementu członkowskiego do **WorkflowHostForm** klasy.</span><span class="sxs-lookup"><span data-stu-id="681ce-240">Add the following member declarations to the **WorkflowHostForm** class.</span></span>  
  
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
    >  <span data-ttu-id="681ce-241">Jeśli ciąg połączenia jest inna, należy zaktualizować `connectionString` do odwoływania się do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="681ce-241">If your connection string is different, update `connectionString` to refer to your database.</span></span>  
  
4.  <span data-ttu-id="681ce-242">Dodaj `WorkflowInstanceId` właściwości `WorkflowFormHost` klasy.</span><span class="sxs-lookup"><span data-stu-id="681ce-242">Add a `WorkflowInstanceId` property to the `WorkflowFormHost` class.</span></span>  
  
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
  
     <span data-ttu-id="681ce-243">`InstanceId` Pola kombi zostanie wyświetlona lista identyfikatorów wystąpień utrwalonych przepływów pracy oraz `WorkflowInstanceId` właściwość zwraca aktualnie wybrany przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="681ce-243">The `InstanceId` combo box displays a list of persisted workflow instance ids, and the `WorkflowInstanceId` property returns the currently selected workflow.</span></span>  
  
5.  <span data-ttu-id="681ce-244">Dodaj obsługę formularza `Load` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="681ce-244">Add a handler for the form `Load` event.</span></span> <span data-ttu-id="681ce-245">Aby dodać program obsługi, przełącz się do **widoku Projekt** formularza, kliknij przycisk **zdarzenia** ikony na początku **właściwości** okna, a następnie kliknij dwukrotnie **obciążenia**.</span><span class="sxs-lookup"><span data-stu-id="681ce-245">To add the handler, switch to **Design View** for the form, click the **Events** icon at the top of the **Properties** window, and double-click **Load**.</span></span>  
  
    ```vb  
    Private Sub WorkflowHostForm_Load(sender As Object, e As EventArgs) Handles Me.Load  
  
    End Sub  
    ```  
  
    ```csharp  
    private void WorkflowHostForm_Load(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
6.  <span data-ttu-id="681ce-246">Dodaj następujący kod do `WorkflowHostForm_Load`.</span><span class="sxs-lookup"><span data-stu-id="681ce-246">Add the following code to `WorkflowHostForm_Load`.</span></span>  
  
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
  
     <span data-ttu-id="681ce-247">Załadowanie formularza, `SqlWorkflowInstanceStore` jest skonfigurowany, pola kombi typ zakresu i przepływu pracy są ustawione na wartości domyślne, a także wystąpień utrwalonych przepływów pracy są dodawane do `InstanceId` pola kombi.</span><span class="sxs-lookup"><span data-stu-id="681ce-247">When the form loads, the `SqlWorkflowInstanceStore` is configured, the range and workflow type combo boxes are set to default values, and the persisted workflow instances are added to the `InstanceId` combo box.</span></span>  
  
7.  <span data-ttu-id="681ce-248">Dodaj `SelectedIndexChanged` obsługę `InstanceId`.</span><span class="sxs-lookup"><span data-stu-id="681ce-248">Add a `SelectedIndexChanged` handler for `InstanceId`.</span></span> <span data-ttu-id="681ce-249">Aby dodać program obsługi, przełącz się do **widoku Projekt** formularza, wybierz `InstanceId` pola kombi kliknij **zdarzenia** ikony na początku **właściwości** okna, i Kliknij dwukrotnie **SelectedIndexChanged**.</span><span class="sxs-lookup"><span data-stu-id="681ce-249">To add the handler, switch to **Design View** for the form, select the `InstanceId` combo box, click the **Events** icon at the top of the **Properties** window, and double-click **SelectedIndexChanged**.</span></span>  
  
    ```vb  
    Private Sub InstanceId_SelectedIndexChanged(sender As Object, e As EventArgs) Handles InstanceId.SelectedIndexChanged  
  
    End Sub  
    ```  
  
    ```csharp  
    private void InstanceId_SelectedIndexChanged(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
8.  <span data-ttu-id="681ce-250">Dodaj następujący kod do `InstanceId_SelectedIndexChanged`.</span><span class="sxs-lookup"><span data-stu-id="681ce-250">Add the following code to `InstanceId_SelectedIndexChanged`.</span></span> <span data-ttu-id="681ce-251">Zawsze, gdy użytkownik wybierze przepływu pracy za pomocą pola kombi ten program obsługi aktualizacji okna stanu.</span><span class="sxs-lookup"><span data-stu-id="681ce-251">Whenever the user selects a workflow by using the combo box this handler updates the status window.</span></span>  
  
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
  
9. <span data-ttu-id="681ce-252">Dodaj następujące `ListPersistedWorkflows` metodę do klasy formularza.</span><span class="sxs-lookup"><span data-stu-id="681ce-252">Add the following `ListPersistedWorkflows` method to the form class.</span></span>  
  
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
  
     <span data-ttu-id="681ce-253">`ListPersistedWorkflows`wysyła kwerendy w magazynie wystąpień dla wystąpień utrwalonych przepływów pracy i dodaje identyfikatorów wystąpienia `cboInstanceId` pola kombi.</span><span class="sxs-lookup"><span data-stu-id="681ce-253">`ListPersistedWorkflows` queries the instance store for persisted workflow instances, and adds the instance ids to the `cboInstanceId` combo box.</span></span>  
  
10. <span data-ttu-id="681ce-254">Dodaj następujące `UpdateStatus` metody oraz odpowiednich delegowanie do klasy formularza.</span><span class="sxs-lookup"><span data-stu-id="681ce-254">Add the following `UpdateStatus` method and corresponding delegate to the form class.</span></span> <span data-ttu-id="681ce-255">Ta metoda aktualizacji okno stanu w formularzu ze stanem obecnie uruchomiony przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="681ce-255">This method updates the status window on the form with the status of the currently running workflow.</span></span>  
  
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
  
11. <span data-ttu-id="681ce-256">Dodaj następujące `GameOver` metody oraz odpowiednich delegowanie do klasy formularza.</span><span class="sxs-lookup"><span data-stu-id="681ce-256">Add the following `GameOver` method and corresponding delegate to the form class.</span></span> <span data-ttu-id="681ce-257">Po zakończeniu przepływu pracy, ta metoda aktualizacji formularza interfejsu użytkownika poprzez usunięcie identyfikator wystąpienia przepływu pracy ukończonych od **InstanceId** pola kombi.</span><span class="sxs-lookup"><span data-stu-id="681ce-257">When a workflow completes, this method updates the form UI by removing the instance id of the completed workflow from the **InstanceId** combo box.</span></span>  
  
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
  
###  <a name="BKMK_ConfigureWorkflowApplication"></a><span data-ttu-id="681ce-258">Aby skonfigurować Magazyn wystąpienia przepływu pracy obsługi cyklu życia i rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="681ce-258">To configure the instance store, workflow lifecycle handlers, and extensions</span></span>  
  
1.  <span data-ttu-id="681ce-259">Dodaj `ConfigureWorkflowApplication` metodę do klasy formularza.</span><span class="sxs-lookup"><span data-stu-id="681ce-259">Add a `ConfigureWorkflowApplication` method to the form class.</span></span>  
  
    ```vb  
    Private Sub ConfigureWorkflowApplication(wfApp As WorkflowApplication)  
  
    End Sub  
    ```  
  
    ```csharp  
    private void ConfigureWorkflowApplication(WorkflowApplication wfApp)  
    {      
    }  
    ```  
  
     <span data-ttu-id="681ce-260">Ta metoda umożliwia skonfigurowanie `WorkflowApplication`, dodaje żądanego rozszerzenia i dodaje obsługę zdarzeń cyklu życia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="681ce-260">This method configures the `WorkflowApplication`, adds the desired extensions, and adds handlers for the workflow lifecycle events.</span></span>  
  
2.  <span data-ttu-id="681ce-261">W `ConfigureWorkflowApplication`, określ `SqlWorkflowInstanceStore` dla `WorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="681ce-261">In `ConfigureWorkflowApplication`, specify the `SqlWorkflowInstanceStore` for the `WorkflowApplication`.</span></span>  
  
    ```vb  
    'Configure the persistence store.  
    wfApp.InstanceStore = store  
    ```  
  
    ```csharp  
    // Configure the persistence store.  
    wfApp.InstanceStore = store;  
    ```  
  
3.  <span data-ttu-id="681ce-262">Następnie należy utworzyć `StringWriter` wystąpienia i dodaj go do `Extensions` kolekcji `WorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="681ce-262">Next, create a `StringWriter` instance and add it to the `Extensions` collection of the `WorkflowApplication`.</span></span> <span data-ttu-id="681ce-263">Gdy `StringWriter` zostanie dodany do rozszerzeń zapisywane, wszystkie `WriteLine` dane wyjściowe działania.</span><span class="sxs-lookup"><span data-stu-id="681ce-263">When a `StringWriter` is added to the extensions it captures all `WriteLine` activity output.</span></span> <span data-ttu-id="681ce-264">Gdy przepływ pracy, staje się bezczynny, `WriteLine` można wyodrębnić dane wyjściowe z `StringWriter` i wyświetlane w formularzu.</span><span class="sxs-lookup"><span data-stu-id="681ce-264">When the workflow becomes idle, the `WriteLine` output can be extracted from the `StringWriter` and displayed on the form.</span></span>  
  
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
  
4.  <span data-ttu-id="681ce-265">Dodaj następujące obsługę `Completed` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="681ce-265">Add the following handler for the `Completed` event.</span></span> <span data-ttu-id="681ce-266">Po pomyślnym zakończeniu przepływu pracy, liczba włącza podjęte w celu odgadnięcia się, że liczba jest wyświetlana w oknie stanu.</span><span class="sxs-lookup"><span data-stu-id="681ce-266">When a workflow successfully completes, the number of turns taken to guess the number is displayed to the status window.</span></span> <span data-ttu-id="681ce-267">Jeśli przepływ pracy zakończy, informacje o wyjątku, który spowodował przerwanie jest wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="681ce-267">If the workflow terminates, the exception information that caused the termination is displayed.</span></span> <span data-ttu-id="681ce-268">Po zakończeniu obsługi `GameOver` wywoływana jest metoda, która usuwa z listy przepływu pracy ukończonych przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="681ce-268">At the end of the handler the `GameOver` method is called, which removes the completed workflow from the workflow list.</span></span>  
  
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
  
5.  <span data-ttu-id="681ce-269">Dodaj następujące `Aborted` i `OnUnhandledException` programów obsługi.</span><span class="sxs-lookup"><span data-stu-id="681ce-269">Add the following `Aborted` and `OnUnhandledException` handlers.</span></span> <span data-ttu-id="681ce-270">`GameOver` Metoda nie jest wywoływana z `Aborted` obsługi, ponieważ gdy wystąpienia przepływu pracy zostało przerwane, nie zakończy i jest możliwe wznowienie wystąpienie w późniejszym czasie.</span><span class="sxs-lookup"><span data-stu-id="681ce-270">The `GameOver` method is not called from the `Aborted` handler because when a workflow instance is aborted, it does not terminate, and it is possible to resume the instance at a later time.</span></span>  
  
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
  
6.  <span data-ttu-id="681ce-271">Dodaj następujące `PersistableIdle` obsługi.</span><span class="sxs-lookup"><span data-stu-id="681ce-271">Add the following `PersistableIdle` handler.</span></span> <span data-ttu-id="681ce-272">Pobiera ten program obsługi `StringWriter` rozszerzenia, które zostały dodane, wyodrębnia dane wyjściowe z `WriteLine` działań i wyświetla je w oknie stanu.</span><span class="sxs-lookup"><span data-stu-id="681ce-272">This handler retrieves the `StringWriter` extension that was added, extracts the output from the `WriteLine` activities, and displays it in the status window.</span></span>  
  
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
  
     <span data-ttu-id="681ce-273"><xref:System.Activities.PersistableIdleAction> Wyliczenie ma trzy wartości: <xref:System.Activities.PersistableIdleAction.None>, <xref:System.Activities.PersistableIdleAction.Persist>, i <xref:System.Activities.PersistableIdleAction.Unload>.</span><span class="sxs-lookup"><span data-stu-id="681ce-273">The <xref:System.Activities.PersistableIdleAction> enumeration has three values: <xref:System.Activities.PersistableIdleAction.None>, <xref:System.Activities.PersistableIdleAction.Persist>, and <xref:System.Activities.PersistableIdleAction.Unload>.</span></span> <span data-ttu-id="681ce-274"><xref:System.Activities.PersistableIdleAction.Persist>przyczyny przepływu pracy, aby utrwalić jednak nie spowoduje zwolnienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="681ce-274"><xref:System.Activities.PersistableIdleAction.Persist> causes the workflow to persist but it does not cause the workflow to unload.</span></span> <span data-ttu-id="681ce-275"><xref:System.Activities.PersistableIdleAction.Unload>powoduje, że przepływ pracy do utrwalenia i zostać zwolniony.</span><span class="sxs-lookup"><span data-stu-id="681ce-275"><xref:System.Activities.PersistableIdleAction.Unload> causes the workflow to persist and be unloaded.</span></span>  
  
     <span data-ttu-id="681ce-276">Poniższy przykład jest wypełniony `ConfigureWorkflowApplication` metody.</span><span class="sxs-lookup"><span data-stu-id="681ce-276">The following example is the completed `ConfigureWorkflowApplication` method.</span></span>  
  
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
  
###  <a name="BKMK_WorkflowVersionMap"></a><span data-ttu-id="681ce-277">Aby włączyć uruchamianie i wznawianie wielu typów przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="681ce-277">To enable starting and resuming multiple workflow types</span></span>  
 <span data-ttu-id="681ce-278">Aby wznowić wystąpienia przepływu pracy, host musi dostarczyć definicji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="681ce-278">In order to resume a workflow instance, the host has to provide the workflow definition.</span></span> <span data-ttu-id="681ce-279">W tym samouczku są trzy typy przepływu pracy, a kolejne kroki samouczka wprowadzić wiele wersji tych typów.</span><span class="sxs-lookup"><span data-stu-id="681ce-279">In this tutorial there are three workflow types, and subsequent tutorial steps introduce multiple versions of these types.</span></span> <span data-ttu-id="681ce-280">`WorkflowIdentity`umożliwia aplikacji hosta skojarzyć z wystąpieniem przepływu pracy utrwalonych informacje identyfikacyjne.</span><span class="sxs-lookup"><span data-stu-id="681ce-280">`WorkflowIdentity` provides a way for a host application to associate identifying information with a persisted workflow instance.</span></span> <span data-ttu-id="681ce-281">Kroki opisane w tej sekcji przedstawiają sposób utworzyć klasę narzędzie pomagające mapowania tożsamości przepływu pracy z wystąpienia utrwalonego przepływu pracy do odpowiedniej definicji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="681ce-281">The steps in this section demonstrate how to create a utility class to assist with mapping the workflow identity from a persisted workflow instance to the corresponding workflow definition.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="681ce-282">`WorkflowIdentity` i wersji, zobacz [za pomocą właściwości WorkflowIdentity and Versioning](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md).</span><span class="sxs-lookup"><span data-stu-id="681ce-282"> `WorkflowIdentity` and versioning, see [Using WorkflowIdentity and Versioning](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md).</span></span>  
  
1.  <span data-ttu-id="681ce-283">Kliknij prawym przyciskiem myszy **NumberGuessWorkflowHost** w **Eksploratora rozwiązań** i wybierz polecenie **Dodaj**, **klasy**.</span><span class="sxs-lookup"><span data-stu-id="681ce-283">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **Class**.</span></span> <span data-ttu-id="681ce-284">Typ `WorkflowVersionMap` do **nazwa** polu i kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="681ce-284">Type `WorkflowVersionMap` into the **Name** box and click **Add**.</span></span>  
  
2.  <span data-ttu-id="681ce-285">Dodaj następujące `using` lub `Imports` instrukcje w górnej części pliku z innym `using` lub `Imports` instrukcje.</span><span class="sxs-lookup"><span data-stu-id="681ce-285">Add the following `using` or `Imports` statements at the top of the file with the other `using` or `Imports` statements.</span></span>  
  
    ```vb  
    Imports NumberGuessWorkflowActivities  
    Imports System.Activities  
    ```  
  
    ```csharp  
    using NumberGuessWorkflowActivities;  
    using System.Activities;  
    ```  
  
3.  <span data-ttu-id="681ce-286">Zastąp `WorkflowVersionMap` deklaracji z następujących deklaracją klasy.</span><span class="sxs-lookup"><span data-stu-id="681ce-286">Replace the `WorkflowVersionMap` class declaration with the following declaration.</span></span>  
  
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
  
     <span data-ttu-id="681ce-287">`WorkflowVersionMap`zawiera trzy tożsamości przepływu pracy, które mapują do trzech definicji przepływu pracy z tego samouczka i jest używany w następujących sekcjach, gdy przepływy pracy są uruchomione i wznowione.</span><span class="sxs-lookup"><span data-stu-id="681ce-287">`WorkflowVersionMap` contains three workflow identities that map to the three workflow definitions from this tutorial and is used in the following sections when workflows are started and resumed.</span></span>  
  
###  <a name="BKMK_StartWorkflow"></a><span data-ttu-id="681ce-288">Aby uruchomić nowy przepływ pracy</span><span class="sxs-lookup"><span data-stu-id="681ce-288">To start a new workflow</span></span>  
  
1.  <span data-ttu-id="681ce-289">Dodaj `Click` obsługę `NewGame`.</span><span class="sxs-lookup"><span data-stu-id="681ce-289">Add a `Click` handler for `NewGame`.</span></span> <span data-ttu-id="681ce-290">Aby dodać program obsługi, przełącz się do **widoku Projekt** formularza i kliknij dwukrotnie `NewGame`.</span><span class="sxs-lookup"><span data-stu-id="681ce-290">To add the handler, switch to **Design View** for the form, and double-click `NewGame`.</span></span> <span data-ttu-id="681ce-291">A `NewGame_Click` dodaniu obsługi, a widok przełączenie się do widoku kodu formularza.</span><span class="sxs-lookup"><span data-stu-id="681ce-291">A `NewGame_Click` handler is added and the view switches to code view for the form.</span></span> <span data-ttu-id="681ce-292">Gdy użytkownik kliknie ten przycisk Nowy przepływ pracy jest uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="681ce-292">Whenever the user clicks this button a new workflow is started.</span></span>  
  
    ```vb  
    Private Sub NewGame_Click(sender As Object, e As EventArgs) Handles NewGame.Click  
  
    End Sub  
    ```  
  
    ```csharp  
    private void NewGame_Click(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
2.  <span data-ttu-id="681ce-293">Dodaj następujący kod do obsługi kliknięcia.</span><span class="sxs-lookup"><span data-stu-id="681ce-293">Add the following code to the click handler.</span></span> <span data-ttu-id="681ce-294">Ten kod tworzy słownika argumentów wejściowych przepływu pracy, wyznaczaną przez Nazwa argumentu.</span><span class="sxs-lookup"><span data-stu-id="681ce-294">This code creates a dictionary of input arguments for the workflow, keyed by argument name.</span></span> <span data-ttu-id="681ce-295">Ten słownik ma jeden wpis zawierający zakres generowany losowo numer pobierane z zakresu pola kombi.</span><span class="sxs-lookup"><span data-stu-id="681ce-295">This dictionary has one entry that contains the range of the randomly generated number retrieved from the range combo box.</span></span>  
  
    ```vb  
    Dim inputs As New Dictionary(Of String, Object)()  
    inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem))  
    ```  
  
    ```csharp  
    var inputs = new Dictionary<string, object>();  
    inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem));  
    ```  
  
3.  <span data-ttu-id="681ce-296">Następnie dodaj następujący kod, który uruchamia przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="681ce-296">Next, add the following code that starts the workflow.</span></span> <span data-ttu-id="681ce-297">`WorkflowIdentity` i odpowiednio do typu przepływu pracy wybrane definicji przepływu pracy są pobierane przy użyciu `WorkflowVersionMap` Klasa pomocy.</span><span class="sxs-lookup"><span data-stu-id="681ce-297">The `WorkflowIdentity` and workflow definition corresponding to the type of workflow selected are retrieved using the `WorkflowVersionMap` helper class.</span></span> <span data-ttu-id="681ce-298">Następnie, nowy `WorkflowApplication` wystąpienia jest tworzony przy użyciu definicji przepływu pracy `WorkflowIdentity`i słownika argumentów wejściowych.</span><span class="sxs-lookup"><span data-stu-id="681ce-298">Next, a new `WorkflowApplication` instance is created using the workflow definition, `WorkflowIdentity`, and dictionary of input arguments.</span></span>  
  
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
  
4.  <span data-ttu-id="681ce-299">Następnie dodaj następujący kod, który dodaje przepływu pracy do listy przepływu pracy i wyświetla informacje o wersji przepływu pracy w formularzu.</span><span class="sxs-lookup"><span data-stu-id="681ce-299">Next, add the following code which adds the workflow to the workflow list and displays the workflow's version information on the form.</span></span>  
  
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
  
5.  <span data-ttu-id="681ce-300">Wywołanie `ConfigureWorkflowApplication` do skonfigurowania obsługi cyklu życia magazynu, rozszerzenia i przepływu pracy wystąpienia tego `WorkflowApplication` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="681ce-300">Call `ConfigureWorkflowApplication` to configure the instance store, extensions, and workflow lifecycle handlers for this `WorkflowApplication` instance.</span></span>  
  
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
  
6.  <span data-ttu-id="681ce-301">Na koniec wywołania `Run`.</span><span class="sxs-lookup"><span data-stu-id="681ce-301">Finally, call `Run`.</span></span>  
  
    ```vb  
    'Start the workflow.  
    wfApp.Run()  
    ```  
  
    ```  
    // Start the workflow.  
    wfApp.Run();  
    ```  
  
     <span data-ttu-id="681ce-302">Poniższy przykład jest wypełniony `NewGame_Click` obsługi.</span><span class="sxs-lookup"><span data-stu-id="681ce-302">The following example is the completed `NewGame_Click` handler.</span></span>  
  
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
  
###  <a name="BKMK_ResumeWorkflow"></a><span data-ttu-id="681ce-303">Aby wznowić przepływ pracy</span><span class="sxs-lookup"><span data-stu-id="681ce-303">To resume a workflow</span></span>  
  
1.  <span data-ttu-id="681ce-304">Dodaj `Click` obsługę `EnterGuess`.</span><span class="sxs-lookup"><span data-stu-id="681ce-304">Add a `Click` handler for `EnterGuess`.</span></span> <span data-ttu-id="681ce-305">Aby dodać program obsługi, przełącz się do **widoku Projekt** formularza i kliknij dwukrotnie `EnterGuess`.</span><span class="sxs-lookup"><span data-stu-id="681ce-305">To add the handler, switch to **Design View** for the form, and double-click `EnterGuess`.</span></span> <span data-ttu-id="681ce-306">Gdy użytkownik kliknie przycisk ten przepływ pracy jest wznawiana.</span><span class="sxs-lookup"><span data-stu-id="681ce-306">Whenever the user clicks this button a workflow is resumed.</span></span>  
  
    ```vb  
    Private Sub EnterGuess_Click(sender As Object, e As EventArgs) Handles EnterGuess.Click  
  
    End Sub  
    ```  
  
    ```csharp  
    private void EnterGuess_Click(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
2.  <span data-ttu-id="681ce-307">Dodaj następujący kod, aby upewnić się, że przepływ pracy jest zaznaczony na liście przepływu pracy i że wynik użytkownika jest prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="681ce-307">Add the following code to ensure that a workflow is selected in the workflow list, and that the user's guess is valid.</span></span>  
  
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
  
3.  <span data-ttu-id="681ce-308">Następnie należy pobrać `WorkflowApplicationInstance` wystąpienia utrwalonego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="681ce-308">Next, retrieve the `WorkflowApplicationInstance` of the persisted workflow instance.</span></span> <span data-ttu-id="681ce-309">A `WorkflowApplicationInstance` reprezentuje wystąpienie utrwalonych przepływów pracy, który nie został jeszcze skojarzony z definicją przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="681ce-309">A `WorkflowApplicationInstance` represents a persisted workflow instance that has not yet been associated with a workflow definition.</span></span> <span data-ttu-id="681ce-310">`DefinitionIdentity` z `WorkflowApplicationInstance` zawiera `WorkflowIdentity` wystąpienia utrwalonego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="681ce-310">The `DefinitionIdentity` of the `WorkflowApplicationInstance` contains the `WorkflowIdentity` of the persisted workflow instance.</span></span> <span data-ttu-id="681ce-311">W tym samouczku `WorkflowVersionMap` klasy narzędzia są używane do mapowania `WorkflowIdentity` do definicji przepływu pracy poprawne.</span><span class="sxs-lookup"><span data-stu-id="681ce-311">In this tutorial, the `WorkflowVersionMap` utility class is used to map the `WorkflowIdentity` to the correct workflow definition.</span></span> <span data-ttu-id="681ce-312">Po pobraniu definicji przepływu pracy `WorkflowApplication` jest tworzony przy użyciu definicji przepływu pracy poprawne.</span><span class="sxs-lookup"><span data-stu-id="681ce-312">Once the workflow definition is retrieved, a `WorkflowApplication` is created, using the correct workflow definition.</span></span>  
  
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
  
4.  <span data-ttu-id="681ce-313">Raz `WorkflowApplication` jest tworzony, skonfigurować Magazyn wystąpienia przepływu pracy obsługi cyklu życia i rozszerzeń przez wywołanie metody `ConfigureWorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="681ce-313">Once the `WorkflowApplication` is created, configure the instance store, workflow lifecycle handlers, and extensions by calling `ConfigureWorkflowApplication`.</span></span> <span data-ttu-id="681ce-314">Te kroki należy wykonać zawsze nowy `WorkflowApplication` jest tworzony, i musi zostać wykonane przed załadowaniem wystąpienia przepływu pracy do `WorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="681ce-314">These steps must be done every time a new `WorkflowApplication` is created, and they must be done before the workflow instance is loaded into the `WorkflowApplication`.</span></span> <span data-ttu-id="681ce-315">Po załadowaniu przepływ pracy zostanie wznowione od wartości wynik użytkownika.</span><span class="sxs-lookup"><span data-stu-id="681ce-315">After the workflow is loaded, it is resumed with the user's guess.</span></span>  
  
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
  
5.  <span data-ttu-id="681ce-316">Na koniec wyczyść pole tekstowe wynik i przygotowanie formularz, aby akceptować inny wynik.</span><span class="sxs-lookup"><span data-stu-id="681ce-316">Finally, clear the guess textbox and prepare the form to accept another guess.</span></span>  
  
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
  
     <span data-ttu-id="681ce-317">Poniższy przykład jest wypełniony `EnterGuess_Click` obsługi.</span><span class="sxs-lookup"><span data-stu-id="681ce-317">The following example is the completed `EnterGuess_Click` handler.</span></span>  
  
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
  
###  <a name="BKMK_TerminateWorkflow"></a><span data-ttu-id="681ce-318">Zakończenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="681ce-318">To terminate a workflow</span></span>  
  
1.  <span data-ttu-id="681ce-319">Dodaj `Click` obsługę `QuitGame`.</span><span class="sxs-lookup"><span data-stu-id="681ce-319">Add a `Click` handler for `QuitGame`.</span></span> <span data-ttu-id="681ce-320">Aby dodać program obsługi, przełącz się do **widoku Projekt** formularza i kliknij dwukrotnie `QuitGame`.</span><span class="sxs-lookup"><span data-stu-id="681ce-320">To add the handler, switch to **Design View** for the form, and double-click `QuitGame`.</span></span> <span data-ttu-id="681ce-321">Gdy użytkownik kliknie ten przycisk aktualnie wybrany przepływ pracy zostanie zakończony.</span><span class="sxs-lookup"><span data-stu-id="681ce-321">Whenever the user clicks this button the currently selected workflow is terminated.</span></span>  
  
    ```vb  
    Private Sub QuitGame_Click(sender As Object, e As EventArgs) Handles QuitGame.Click  
  
    End Sub  
    ```  
  
    ```csharp  
    private void QuitGame_Click(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
2.  <span data-ttu-id="681ce-322">Dodaj następujący kod do `QuitGame_Click` obsługi.</span><span class="sxs-lookup"><span data-stu-id="681ce-322">Add the following code to the `QuitGame_Click` handler.</span></span> <span data-ttu-id="681ce-323">Ten kod najpierw sprawdza, upewnij się, że przepływ pracy jest zaznaczony na liście przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="681ce-323">This code first checks to ensure that a workflow is selected in the workflow list.</span></span> <span data-ttu-id="681ce-324">Następnie ładuje trwałego wystąpienia do `WorkflowApplicationInstance`, używa `DefinitionIdentity` do określenia definicji przepływu pracy poprawne, a następnie inicjuje `WorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="681ce-324">Then it loads the persisted instance into a `WorkflowApplicationInstance`, uses the `DefinitionIdentity` to determine the correct workflow definition, and then initializes the `WorkflowApplication`.</span></span> <span data-ttu-id="681ce-325">Obok rozszerzeń i obsługi cyklu życia przepływu pracy są skonfigurowane przy użyciu wywołania do `ConfigureWorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="681ce-325">Next the extensions and workflow lifecycle handlers are configured with a call to `ConfigureWorkflowApplication`.</span></span> <span data-ttu-id="681ce-326">Raz `WorkflowApplication` jest skonfigurowany, załadowaniu go, a następnie `Terminate` jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="681ce-326">Once the `WorkflowApplication` is configured, it is loaded, and then `Terminate` is called.</span></span>  
  
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
  
###  <a name="BKMK_BuildAndRun"></a><span data-ttu-id="681ce-327">Aby skompilować i uruchomić aplikację</span><span class="sxs-lookup"><span data-stu-id="681ce-327">To build and run the application</span></span>  
  
1.  <span data-ttu-id="681ce-328">Kliknij dwukrotnie **Program.cs** (lub **Module1.vb**) w **Eksploratora rozwiązań** Aby wyświetlić kod.</span><span class="sxs-lookup"><span data-stu-id="681ce-328">Double-click **Program.cs** (or **Module1.vb**) in **Solution Explorer** to display the code.</span></span>  
  
2.  <span data-ttu-id="681ce-329">Dodaj następujące `using` (lub `Imports`) instrukcji w górnej części pliku z innym `using` (lub `Imports`) instrukcje.</span><span class="sxs-lookup"><span data-stu-id="681ce-329">Add the following `using` (or `Imports`) statement at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports System.Windows.Forms  
    ```  
  
    ```csharp  
    using System.Windows.Forms;  
    ```  
  
3.  <span data-ttu-id="681ce-330">Usuń lub komentarz istniejący kod z obsługującym przepływ pracy [porady: uruchamianie przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)i zastąp go następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="681ce-330">Remove or comment out the existing workflow hosting code from [How to: Run a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md), and replace it with the following code.</span></span>  
  
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
  
4.  <span data-ttu-id="681ce-331">Kliknij prawym przyciskiem myszy **NumberGuessWorkflowHost** w **Eksploratora rozwiązań** i wybierz polecenie **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="681ce-331">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Properties**.</span></span> <span data-ttu-id="681ce-332">W **aplikacji** karcie, określ **aplikacji systemu Windows** dla **Output typu**.</span><span class="sxs-lookup"><span data-stu-id="681ce-332">In the **Application** tab, specify **Windows Application** for the **Output type**.</span></span> <span data-ttu-id="681ce-333">Ten krok jest opcjonalny, ale jeśli nie występuje w oknie konsoli zostanie wyświetlony oprócz formularza.</span><span class="sxs-lookup"><span data-stu-id="681ce-333">This step is optional, but if it is not followed the console window is displayed in addition to the form.</span></span>  
  
5.  <span data-ttu-id="681ce-334">Naciśnij klawisze Ctrl + Shift + B do skompilowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="681ce-334">Press Ctrl+Shift+B to build the application.</span></span>  
  
6.  <span data-ttu-id="681ce-335">Upewnij się, że **NumberGuessWorkflowHost** jest ustawiony jako aplikacja do uruchomienia, a następnie naciśnij klawisz Ctrl + F5, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="681ce-335">Ensure that **NumberGuessWorkflowHost** is set as the startup application, and press Ctrl+F5 to start the application.</span></span>  
  
7.  <span data-ttu-id="681ce-336">Wybierz zakres guessing gry i typ przepływu pracy, aby rozpocząć, a następnie kliknij przycisk **nowych gier**.</span><span class="sxs-lookup"><span data-stu-id="681ce-336">Select a range for the guessing game and the type of workflow to start, and click **New Game**.</span></span> <span data-ttu-id="681ce-337">Wprowadź wynik w **Guess** polu i kliknij przycisk **Przejdź** można przesłać z wynik.</span><span class="sxs-lookup"><span data-stu-id="681ce-337">Enter a guess in the **Guess** box and click **Go** to submit your guess.</span></span> <span data-ttu-id="681ce-338">Należy pamiętać, że dane wyjściowe z `WriteLine` działania jest wyświetlana w formularzu.</span><span class="sxs-lookup"><span data-stu-id="681ce-338">Note that the output from the `WriteLine` activities is displayed on the form.</span></span>  
  
8.  <span data-ttu-id="681ce-339">Uruchom kilka przepływów pracy za pomocą typów innego przepływu pracy i liczba zakresów, wprowadź niektórych prób, a następnie przełączać się między przepływami pracy, wybierając z **identyfikator wystąpienia przepływu pracy** listy.</span><span class="sxs-lookup"><span data-stu-id="681ce-339">Start several workflows using different workflow types and number ranges, enter some guesses, and switch between the workflows by selecting from the **Workflow Instance Id** list.</span></span>  
  
     <span data-ttu-id="681ce-340">Należy pamiętać, że przełączenie do nowego przepływu pracy poprzednich prób i postęp przepływu pracy nie są wyświetlane w oknie stanu.</span><span class="sxs-lookup"><span data-stu-id="681ce-340">Note that when you switch to a new workflow, the previous guesses and progress of the workflow are not displayed in the status window.</span></span> <span data-ttu-id="681ce-341">Przyczyny stanu nie jest dostępna jest ponieważ zostaną zebrane i nie zapisano w dowolnym miejscu.</span><span class="sxs-lookup"><span data-stu-id="681ce-341">The reason the status is not available is because it is not captured and saved anywhere.</span></span> <span data-ttu-id="681ce-342">W następnym kroku samouczka [porady: Tworzenie niestandardowych uczestnika śledzenia](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md), Utwórz uczestnika niestandardowych śledzenia, który zapisuje te informacje.</span><span class="sxs-lookup"><span data-stu-id="681ce-342">In the next step of the tutorial, [How to: Create a Custom Tracking Participant](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md), you create a custom tracking participant that saves this information.</span></span>
