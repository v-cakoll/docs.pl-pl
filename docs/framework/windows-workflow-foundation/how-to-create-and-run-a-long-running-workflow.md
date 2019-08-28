---
title: 'Instrukcje: Tworzenie i uruchamianie długotrwałego przepływu pracy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c0043c89-2192-43c9-986d-3ecec4dd8c9c
ms.openlocfilehash: 15ee10120f4d4c92bdc95cb48cb3cb838f526343
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044379"
---
# <a name="how-to-create-and-run-a-long-running-workflow"></a><span data-ttu-id="96578-102">Instrukcje: Tworzenie i uruchamianie długotrwałego przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="96578-102">How to: Create and Run a Long Running Workflow</span></span>

<span data-ttu-id="96578-103">Jedną z centralnych funkcji Windows Workflow Foundation (WF) jest zdolność środowiska uruchomieniowego do utrwalania i zwalniania bezczynnych przepływów pracy do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="96578-103">One of the central features of Windows Workflow Foundation (WF) is the runtime’s ability to persist and unload idle workflows to a database.</span></span> <span data-ttu-id="96578-104">Kroki opisane w [temacie How to: Uruchom przepływ pracy](how-to-run-a-workflow.md) przedstawiający podstawowe informacje o hostingu przepływu pracy przy użyciu aplikacji konsolowej.</span><span class="sxs-lookup"><span data-stu-id="96578-104">The steps in [How to: Run a Workflow](how-to-run-a-workflow.md) demonstrated the basics of workflow hosting using a console application.</span></span> <span data-ttu-id="96578-105">Przedstawiono przykłady uruchamiania przepływów pracy, obsługi cyklu życia przepływu pracy i wznawiania zakładek.</span><span class="sxs-lookup"><span data-stu-id="96578-105">Examples were shown of starting workflows, workflow lifecycle handlers, and resuming bookmarks.</span></span> <span data-ttu-id="96578-106">W celu efektywnego zademonstrowania trwałości przepływu pracy wymagany jest bardziej złożony host przepływu pracy, który obsługuje uruchamianie i wznawianie wielu wystąpień przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="96578-106">In order to demonstrate workflow persistence effectively, a more complex workflow host is required that supports starting and resuming multiple workflow instances.</span></span> <span data-ttu-id="96578-107">Ten krok w samouczku pokazuje, jak utworzyć aplikację hosta formularza systemu Windows, która obsługuje uruchamianie i wznawianie wielu wystąpień przepływów pracy, trwałości przepływu pracy i stanowi podstawę zaawansowanych funkcji, takich jak śledzenie i przechowywanie wersji przedstawiono w kolejnych krokach samouczka.</span><span class="sxs-lookup"><span data-stu-id="96578-107">This step in the tutorial demonstrates how to create a Windows form host application that supports starting and resuming multiple workflow instances, workflow persistence, and provides a basis for the advanced features such as tracking and versioning that are demonstrated in subsequent tutorial steps.</span></span>

> [!NOTE]
> <span data-ttu-id="96578-108">Ten krok samouczka i kolejne kroki używają wszystkich trzech typów [przepływu pracy: Utwórz przepływ pracy](how-to-create-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="96578-108">This tutorial step and the subsequent steps use all three workflow types from [How to: Create a Workflow](how-to-create-a-workflow.md).</span></span> <span data-ttu-id="96578-109">Jeśli wszystkie trzy typy nie zostały wykonane, można pobrać ukończoną wersję kroków z [Windows Workflow Foundation (WF45) — wprowadzenie samouczka](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="96578-109">If you did not complete all three types you can download a completed version of the steps from [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>

> [!NOTE]
> <span data-ttu-id="96578-110">Aby pobrać kompletną wersję lub wyświetlić przewodnik wideo samouczka, zobacz [Windows Workflow Foundation (WF45) — samouczek wprowadzenie](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="96578-110">To download a completed version or view a video walkthrough of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>

## <a name="in-this-topic"></a><span data-ttu-id="96578-111">W tym temacie:</span><span class="sxs-lookup"><span data-stu-id="96578-111">In this topic</span></span>

- [<span data-ttu-id="96578-112">Aby utworzyć bazę danych trwałości</span><span class="sxs-lookup"><span data-stu-id="96578-112">To create the persistence database</span></span>](how-to-create-and-run-a-long-running-workflow.md#BKMK_CreatePersistenceDatabase)

- [<span data-ttu-id="96578-113">Aby dodać odwołanie do zestawów DurableInstancing</span><span class="sxs-lookup"><span data-stu-id="96578-113">To add the reference to the DurableInstancing assemblies</span></span>](how-to-create-and-run-a-long-running-workflow.md#BKMK_AddReference)

- [<span data-ttu-id="96578-114">Aby utworzyć formularz hosta przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="96578-114">To create the workflow host form</span></span>](how-to-create-and-run-a-long-running-workflow.md#BKMK_CreateForm)

- [<span data-ttu-id="96578-115">Aby dodać właściwości i metody pomocnika formularza</span><span class="sxs-lookup"><span data-stu-id="96578-115">To add the properties and helper methods of the form</span></span>](how-to-create-and-run-a-long-running-workflow.md#BKMK_AddHelperMethods)

- [<span data-ttu-id="96578-116">Aby skonfigurować magazyn wystąpień, programy obsługi cyklu życia przepływu pracy i rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="96578-116">To configure the instance store, workflow lifecycle handlers, and extensions</span></span>](how-to-create-and-run-a-long-running-workflow.md#BKMK_ConfigureWorkflowApplication)

- [<span data-ttu-id="96578-117">Aby włączyć uruchamianie i wznawianie wielu typów przepływów pracy</span><span class="sxs-lookup"><span data-stu-id="96578-117">To enable starting and resuming multiple workflow types</span></span>](how-to-create-and-run-a-long-running-workflow.md#BKMK_WorkflowVersionMap)

- [<span data-ttu-id="96578-118">Aby uruchomić nowy przepływ pracy</span><span class="sxs-lookup"><span data-stu-id="96578-118">To start a new workflow</span></span>](how-to-create-and-run-a-long-running-workflow.md#BKMK_StartWorkflow)

- [<span data-ttu-id="96578-119">Aby wznowić przepływ pracy</span><span class="sxs-lookup"><span data-stu-id="96578-119">To resume a workflow</span></span>](how-to-create-and-run-a-long-running-workflow.md#BKMK_ResumeWorkflow)

- [<span data-ttu-id="96578-120">Aby zakończyć przepływ pracy</span><span class="sxs-lookup"><span data-stu-id="96578-120">To terminate a workflow</span></span>](how-to-create-and-run-a-long-running-workflow.md#BKMK_TerminateWorkflow)

- [<span data-ttu-id="96578-121">Aby skompilować i uruchomić aplikację</span><span class="sxs-lookup"><span data-stu-id="96578-121">To build and run the application</span></span>](how-to-create-and-run-a-long-running-workflow.md#BKMK_BuildAndRun)

### <a name="BKMK_CreatePersistenceDatabase"></a><span data-ttu-id="96578-122">Aby utworzyć bazę danych trwałości</span><span class="sxs-lookup"><span data-stu-id="96578-122">To create the persistence database</span></span>

1. <span data-ttu-id="96578-123">Otwórz SQL Server Management Studio i Połącz się z serwerem lokalnym, na przykład **.\SQLEXPRESS**.</span><span class="sxs-lookup"><span data-stu-id="96578-123">Open SQL Server Management Studio and connect to the local server, for example **.\SQLEXPRESS**.</span></span> <span data-ttu-id="96578-124">Kliknij prawym przyciskiem myszy węzeł **bazy danych** na serwerze lokalnym, a następnie wybierz pozycję **Nowa baza danych**.</span><span class="sxs-lookup"><span data-stu-id="96578-124">Right-click the **Databases** node on the local server, and select **New Database**.</span></span> <span data-ttu-id="96578-125">Nazwa nowej bazy danych **WF45GettingStartedTutorial**, Zaakceptuj wszystkie inne wartości, a następnie wybierz **przycisk OK**.</span><span class="sxs-lookup"><span data-stu-id="96578-125">Name the new database **WF45GettingStartedTutorial**, accept all other values, and select **OK**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="96578-126">Przed utworzeniem bazy danych upewnij się, że masz uprawnienia do **tworzenia bazy danych** na serwerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="96578-126">Ensure that you have **Create Database** permission on the local server before creating the database.</span></span>

2. <span data-ttu-id="96578-127">Wybierz polecenie **Otwórz**, **plik** z menu **plik** .</span><span class="sxs-lookup"><span data-stu-id="96578-127">Choose **Open**, **File** from the **File** menu.</span></span> <span data-ttu-id="96578-128">Przejdź do następującego folderu:`C:\Windows\Microsoft.NET\Framework\v4.0.30319\sql\en`</span><span class="sxs-lookup"><span data-stu-id="96578-128">Browse to the following folder: `C:\Windows\Microsoft.NET\Framework\v4.0.30319\sql\en`</span></span>

    <span data-ttu-id="96578-129">Wybierz poniższe dwa pliki, a następnie kliknij przycisk **Otwórz**.</span><span class="sxs-lookup"><span data-stu-id="96578-129">Select the following two files and click **Open**.</span></span>

    - <span data-ttu-id="96578-130">SqlWorkflowInstanceStoreLogic.sql</span><span class="sxs-lookup"><span data-stu-id="96578-130">SqlWorkflowInstanceStoreLogic.sql</span></span>

    - <span data-ttu-id="96578-131">SqlWorkflowInstanceStoreSchema.sql</span><span class="sxs-lookup"><span data-stu-id="96578-131">SqlWorkflowInstanceStoreSchema.sql</span></span>

3. <span data-ttu-id="96578-132">Wybierz **SqlWorkflowInstanceStoreSchema. SQL** z menu **okno** .</span><span class="sxs-lookup"><span data-stu-id="96578-132">Choose **SqlWorkflowInstanceStoreSchema.sql** from the **Window** menu.</span></span> <span data-ttu-id="96578-133">Upewnij się, że wybrano pozycję **WF45GettingStartedTutorial** na liście rozwijanej **dostępne bazy danych** , a następnie wybierz polecenie **Wykonaj** z menu **zapytania** .</span><span class="sxs-lookup"><span data-stu-id="96578-133">Ensure that **WF45GettingStartedTutorial** is selected in the **Available Databases** drop-down and choose **Execute** from the **Query** menu.</span></span>

4. <span data-ttu-id="96578-134">Wybierz **SqlWorkflowInstanceStoreLogic. SQL** z menu **okno** .</span><span class="sxs-lookup"><span data-stu-id="96578-134">Choose **SqlWorkflowInstanceStoreLogic.sql** from the **Window** menu.</span></span> <span data-ttu-id="96578-135">Upewnij się, że wybrano pozycję **WF45GettingStartedTutorial** na liście rozwijanej **dostępne bazy danych** , a następnie wybierz polecenie **Wykonaj** z menu **zapytania** .</span><span class="sxs-lookup"><span data-stu-id="96578-135">Ensure that **WF45GettingStartedTutorial** is selected in the **Available Databases** drop-down and choose **Execute** from the **Query** menu.</span></span>

    > [!WARNING]
    > <span data-ttu-id="96578-136">Ważne jest, aby wykonać dwa poprzednie kroki w odpowiedniej kolejności.</span><span class="sxs-lookup"><span data-stu-id="96578-136">It is important to perform the previous two steps in the correct order.</span></span> <span data-ttu-id="96578-137">Jeśli zapytania są wykonywane poza kolejnością, wystąpią błędy i baza danych trwałości nie jest poprawnie skonfigurowana.</span><span class="sxs-lookup"><span data-stu-id="96578-137">If the queries are executed out of order, errors occur and the persistence database is not configured correctly.</span></span>

### <a name="BKMK_AddReference"></a><span data-ttu-id="96578-138">Aby dodać odwołanie do zestawów DurableInstancing</span><span class="sxs-lookup"><span data-stu-id="96578-138">To add the reference to the DurableInstancing assemblies</span></span>

1. <span data-ttu-id="96578-139">Kliknij prawym przyciskiem myszy pozycję **NumberGuessWorkflowHost** w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="96578-139">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and select **Add Reference**.</span></span>

2. <span data-ttu-id="96578-140">Wybierz pozycję **zestawy** z listy **Dodaj odwołanie** , a następnie `DurableInstancing` wpisz w polu **wyszukiwania zestawów** .</span><span class="sxs-lookup"><span data-stu-id="96578-140">Select **Assemblies** from the **Add Reference** list, and type `DurableInstancing` into the **Search Assemblies** box.</span></span> <span data-ttu-id="96578-141">To filtruje zestawy i ułatwia wybór odpowiednich odwołań.</span><span class="sxs-lookup"><span data-stu-id="96578-141">This filters the assemblies and makes the desired references easier to select.</span></span>

3. <span data-ttu-id="96578-142">Zaznacz pole wyboru obok pozycji **System. Activities. DurableInstancing** i **System. Runtime. DurableInstancing** z listy **wyników wyszukiwania** , a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="96578-142">Check the checkbox beside **System.Activities.DurableInstancing** and **System.Runtime.DurableInstancing** from the **Search Results** list, and click **OK**.</span></span>

### <a name="BKMK_CreateForm"></a><span data-ttu-id="96578-143">Aby utworzyć formularz hosta przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="96578-143">To create the workflow host form</span></span>

> [!NOTE]
> <span data-ttu-id="96578-144">Kroki opisane w tej procedurze opisują sposób ręcznego dodawania i konfigurowania formularza.</span><span class="sxs-lookup"><span data-stu-id="96578-144">The steps in this procedure describe how to add and configure the form manually.</span></span> <span data-ttu-id="96578-145">W razie potrzeby można pobrać pliki rozwiązania dla samouczka i dodać ukończony formularz do projektu.</span><span class="sxs-lookup"><span data-stu-id="96578-145">If desired, you can download the solution files for the tutorial and add the completed form to the project.</span></span> <span data-ttu-id="96578-146">Aby pobrać pliki samouczka, zobacz [Windows Workflow Foundation (WF45) — samouczek wprowadzenie](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="96578-146">To download the tutorial files, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span> <span data-ttu-id="96578-147">Po pobraniu plików kliknij prawym przyciskiem myszy pozycję **NumberGuessWorkflowHost** i wybierz polecenie **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="96578-147">Once the files are downloaded, right-click **NumberGuessWorkflowHost** and choose **Add Reference**.</span></span> <span data-ttu-id="96578-148">Dodaj odwołanie do **System. Windows. Forms** i **System. Drawing**.</span><span class="sxs-lookup"><span data-stu-id="96578-148">Add a reference to **System.Windows.Forms** and **System.Drawing**.</span></span> <span data-ttu-id="96578-149">Te odwołania są dodawane automatycznie po dodaniu nowego formularza z menu **Dodaj**, **nowy element** , ale należy dodać go ręcznie podczas importowania formularza.</span><span class="sxs-lookup"><span data-stu-id="96578-149">These references are added automatically if you add a new form from the **Add**, **New Item** menu, but must be added manually when importing a form.</span></span> <span data-ttu-id="96578-150">Po dodaniu odwołań kliknij prawym przyciskiem myszy pozycję **NumberGuessWorkflowHost** w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj**, **istniejący element**.</span><span class="sxs-lookup"><span data-stu-id="96578-150">Once the references are added, right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **Existing Item**.</span></span> <span data-ttu-id="96578-151">Przejdź `Form` do folderu w plikach projektu, wybierz pozycję **WorkflowHostForm.cs** (lub **WorkflowHostForm. vb**), a następnie kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="96578-151">Browse to the `Form` folder in the project files, select **WorkflowHostForm.cs** (or **WorkflowHostForm.vb**), and click **Add**.</span></span> <span data-ttu-id="96578-152">Jeśli zdecydujesz się zaimportować formularz, możesz przejść do następnej sekcji, [Aby dodać właściwości i metody pomocnika formularza](how-to-create-and-run-a-long-running-workflow.md#BKMK_AddHelperMethods).</span><span class="sxs-lookup"><span data-stu-id="96578-152">If you choose to import the form, then you can skip down to the next section, [To add the properties and helper methods of the form](how-to-create-and-run-a-long-running-workflow.md#BKMK_AddHelperMethods).</span></span>

1. <span data-ttu-id="96578-153">Kliknij prawym przyciskiem myszy pozycję **NumberGuessWorkflowHost** w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj**, **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="96578-153">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **New Item**.</span></span>

2. <span data-ttu-id="96578-154">Na liście **zainstalowane** szablony wybierz pozycję **formularz systemu Windows**, wpisz `WorkflowHostForm` w polu **Nazwa** , a następnie kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="96578-154">In the **Installed** templates list, choose **Windows Form**, type `WorkflowHostForm` in the **Name** box, and click **Add**.</span></span>

3. <span data-ttu-id="96578-155">Skonfiguruj następujące właściwości w formularzu.</span><span class="sxs-lookup"><span data-stu-id="96578-155">Configure the following properties on the form.</span></span>

    |<span data-ttu-id="96578-156">Właściwość</span><span class="sxs-lookup"><span data-stu-id="96578-156">Property</span></span>|<span data-ttu-id="96578-157">Wartość</span><span class="sxs-lookup"><span data-stu-id="96578-157">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="96578-158">FormBorderStyle</span><span class="sxs-lookup"><span data-stu-id="96578-158">FormBorderStyle</span></span>|<span data-ttu-id="96578-159">FixedSingle</span><span class="sxs-lookup"><span data-stu-id="96578-159">FixedSingle</span></span>|
    |<span data-ttu-id="96578-160">MaximizeBox</span><span class="sxs-lookup"><span data-stu-id="96578-160">MaximizeBox</span></span>|<span data-ttu-id="96578-161">False</span><span class="sxs-lookup"><span data-stu-id="96578-161">False</span></span>|
    |<span data-ttu-id="96578-162">Rozmiar</span><span class="sxs-lookup"><span data-stu-id="96578-162">Size</span></span>|<span data-ttu-id="96578-163">400, 420</span><span class="sxs-lookup"><span data-stu-id="96578-163">400, 420</span></span>|

4. <span data-ttu-id="96578-164">Dodaj następujące kontrolki do formularza w określonej kolejności i skonfiguruj właściwości jako kierowane.</span><span class="sxs-lookup"><span data-stu-id="96578-164">Add the following controls to the form in the order specified and configure the properties as directed.</span></span>

    |<span data-ttu-id="96578-165">formant</span><span class="sxs-lookup"><span data-stu-id="96578-165">Control</span></span>|<span data-ttu-id="96578-166">Wartość Wartość</span><span class="sxs-lookup"><span data-stu-id="96578-166">Property: Value</span></span>|
    |-------------|---------------------|
    |<span data-ttu-id="96578-167">**Przycisk**</span><span class="sxs-lookup"><span data-stu-id="96578-167">**Button**</span></span>|<span data-ttu-id="96578-168">Nazwij NewGame</span><span class="sxs-lookup"><span data-stu-id="96578-168">Name: NewGame</span></span><br /><br /> <span data-ttu-id="96578-169">Przeniesienie 13, 13</span><span class="sxs-lookup"><span data-stu-id="96578-169">Location: 13, 13</span></span><br /><br /> <span data-ttu-id="96578-170">Zmienia 75, 23</span><span class="sxs-lookup"><span data-stu-id="96578-170">Size: 75, 23</span></span><br /><br /> <span data-ttu-id="96578-171">Opis Nowa gra</span><span class="sxs-lookup"><span data-stu-id="96578-171">Text: New Game</span></span>|
    |<span data-ttu-id="96578-172">**Etykieta**</span><span class="sxs-lookup"><span data-stu-id="96578-172">**Label**</span></span>|<span data-ttu-id="96578-173">Przeniesienie 94, 18</span><span class="sxs-lookup"><span data-stu-id="96578-173">Location: 94, 18</span></span><br /><br /> <span data-ttu-id="96578-174">Opis Zgadywanie liczby z 1 do</span><span class="sxs-lookup"><span data-stu-id="96578-174">Text: Guess a number from 1 to</span></span>|
    |<span data-ttu-id="96578-175">**ComboBox**</span><span class="sxs-lookup"><span data-stu-id="96578-175">**ComboBox**</span></span>|<span data-ttu-id="96578-176">Nazwij NumberRange</span><span class="sxs-lookup"><span data-stu-id="96578-176">Name: NumberRange</span></span><br /><br /> <span data-ttu-id="96578-177">DropDownStyle: DropDownList</span><span class="sxs-lookup"><span data-stu-id="96578-177">DropDownStyle: DropDownList</span></span><br /><br /> <span data-ttu-id="96578-178">Produktów 10, 100, 1000</span><span class="sxs-lookup"><span data-stu-id="96578-178">Items: 10, 100, 1000</span></span><br /><br /> <span data-ttu-id="96578-179">Przeniesienie 228, 12</span><span class="sxs-lookup"><span data-stu-id="96578-179">Location: 228, 12</span></span><br /><br /> <span data-ttu-id="96578-180">Zmienia 143, 21</span><span class="sxs-lookup"><span data-stu-id="96578-180">Size: 143, 21</span></span>|
    |<span data-ttu-id="96578-181">**Etykieta**</span><span class="sxs-lookup"><span data-stu-id="96578-181">**Label**</span></span>|<span data-ttu-id="96578-182">Przeniesienie 13, 43</span><span class="sxs-lookup"><span data-stu-id="96578-182">Location: 13, 43</span></span><br /><br /> <span data-ttu-id="96578-183">Opis Typ przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="96578-183">Text: Workflow type</span></span>|
    |<span data-ttu-id="96578-184">**ComboBox**</span><span class="sxs-lookup"><span data-stu-id="96578-184">**ComboBox**</span></span>|<span data-ttu-id="96578-185">Nazwij Menedżer przepływów pracy</span><span class="sxs-lookup"><span data-stu-id="96578-185">Name: WorkflowType</span></span><br /><br /> <span data-ttu-id="96578-186">DropDownStyle: DropDownList</span><span class="sxs-lookup"><span data-stu-id="96578-186">DropDownStyle: DropDownList</span></span><br /><br /> <span data-ttu-id="96578-187">Produktów StateMachineNumberGuessWorkflow, FlowchartNumberGuessWorkflow, SequentialNumberGuessWorkflow</span><span class="sxs-lookup"><span data-stu-id="96578-187">Items: StateMachineNumberGuessWorkflow, FlowchartNumberGuessWorkflow, SequentialNumberGuessWorkflow</span></span><br /><br /> <span data-ttu-id="96578-188">Przeniesienie 94, 40</span><span class="sxs-lookup"><span data-stu-id="96578-188">Location: 94, 40</span></span><br /><br /> <span data-ttu-id="96578-189">Zmienia 277, 21</span><span class="sxs-lookup"><span data-stu-id="96578-189">Size: 277, 21</span></span>|
    |<span data-ttu-id="96578-190">**Etykieta**</span><span class="sxs-lookup"><span data-stu-id="96578-190">**Label**</span></span>|<span data-ttu-id="96578-191">Nazwij WorkflowVersion</span><span class="sxs-lookup"><span data-stu-id="96578-191">Name: WorkflowVersion</span></span><br /><br /> <span data-ttu-id="96578-192">Przeniesienie 13, 362</span><span class="sxs-lookup"><span data-stu-id="96578-192">Location: 13, 362</span></span><br /><br /> <span data-ttu-id="96578-193">Opis Wersja przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="96578-193">Text: Workflow version</span></span>|
    |<span data-ttu-id="96578-194">**GroupBox**</span><span class="sxs-lookup"><span data-stu-id="96578-194">**GroupBox**</span></span>|<span data-ttu-id="96578-195">Przeniesienie 13, 67</span><span class="sxs-lookup"><span data-stu-id="96578-195">Location: 13, 67</span></span><br /><br /> <span data-ttu-id="96578-196">Zmienia 358, 287</span><span class="sxs-lookup"><span data-stu-id="96578-196">Size: 358, 287</span></span><br /><br /> <span data-ttu-id="96578-197">Opis Rozgrywk</span><span class="sxs-lookup"><span data-stu-id="96578-197">Text: Game</span></span>|

    > [!NOTE]
    > <span data-ttu-id="96578-198">Podczas dodawania następujących kontrolek należy umieścić je w polu grupy.</span><span class="sxs-lookup"><span data-stu-id="96578-198">When adding the following controls, put them into the GroupBox.</span></span>

    |<span data-ttu-id="96578-199">formant</span><span class="sxs-lookup"><span data-stu-id="96578-199">Control</span></span>|<span data-ttu-id="96578-200">Wartość Wartość</span><span class="sxs-lookup"><span data-stu-id="96578-200">Property: Value</span></span>|
    |-------------|---------------------|
    |<span data-ttu-id="96578-201">**Etykieta**</span><span class="sxs-lookup"><span data-stu-id="96578-201">**Label**</span></span>|<span data-ttu-id="96578-202">Przeniesienie 7, 20</span><span class="sxs-lookup"><span data-stu-id="96578-202">Location: 7, 20</span></span><br /><br /> <span data-ttu-id="96578-203">Opis Identyfikator wystąpienia przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="96578-203">Text: Workflow Instance Id</span></span>|
    |<span data-ttu-id="96578-204">**ComboBox**</span><span class="sxs-lookup"><span data-stu-id="96578-204">**ComboBox**</span></span>|<span data-ttu-id="96578-205">Nazwij Identyfikator wystąpienia</span><span class="sxs-lookup"><span data-stu-id="96578-205">Name: InstanceId</span></span><br /><br /> <span data-ttu-id="96578-206">DropDownStyle: DropDownList</span><span class="sxs-lookup"><span data-stu-id="96578-206">DropDownStyle: DropDownList</span></span><br /><br /> <span data-ttu-id="96578-207">Przeniesienie 121, 17</span><span class="sxs-lookup"><span data-stu-id="96578-207">Location: 121, 17</span></span><br /><br /> <span data-ttu-id="96578-208">Zmienia 227, 21</span><span class="sxs-lookup"><span data-stu-id="96578-208">Size: 227, 21</span></span>|
    |<span data-ttu-id="96578-209">**Etykieta**</span><span class="sxs-lookup"><span data-stu-id="96578-209">**Label**</span></span>|<span data-ttu-id="96578-210">Przeniesienie 7, 47</span><span class="sxs-lookup"><span data-stu-id="96578-210">Location: 7, 47</span></span><br /><br /> <span data-ttu-id="96578-211">Opis Stanie</span><span class="sxs-lookup"><span data-stu-id="96578-211">Text: Guess</span></span>|
    |<span data-ttu-id="96578-212">**TextBox**</span><span class="sxs-lookup"><span data-stu-id="96578-212">**TextBox**</span></span>|<span data-ttu-id="96578-213">Nazwij Stanie</span><span class="sxs-lookup"><span data-stu-id="96578-213">Name: Guess</span></span><br /><br /> <span data-ttu-id="96578-214">Przeniesienie 50, 44</span><span class="sxs-lookup"><span data-stu-id="96578-214">Location: 50, 44</span></span><br /><br /> <span data-ttu-id="96578-215">Zmienia 65, 20</span><span class="sxs-lookup"><span data-stu-id="96578-215">Size: 65, 20</span></span>|
    |<span data-ttu-id="96578-216">**Przycisk**</span><span class="sxs-lookup"><span data-stu-id="96578-216">**Button**</span></span>|<span data-ttu-id="96578-217">Nazwij EnterGuess</span><span class="sxs-lookup"><span data-stu-id="96578-217">Name: EnterGuess</span></span><br /><br /> <span data-ttu-id="96578-218">Przeniesienie 121, 42</span><span class="sxs-lookup"><span data-stu-id="96578-218">Location: 121, 42</span></span><br /><br /> <span data-ttu-id="96578-219">Zmienia 75, 23</span><span class="sxs-lookup"><span data-stu-id="96578-219">Size: 75, 23</span></span><br /><br /> <span data-ttu-id="96578-220">Opis Wprowadź zgadywanie</span><span class="sxs-lookup"><span data-stu-id="96578-220">Text: Enter Guess</span></span>|
    |<span data-ttu-id="96578-221">**Przycisk**</span><span class="sxs-lookup"><span data-stu-id="96578-221">**Button**</span></span>|<span data-ttu-id="96578-222">Nazwij QuitGame</span><span class="sxs-lookup"><span data-stu-id="96578-222">Name: QuitGame</span></span><br /><br /> <span data-ttu-id="96578-223">Przeniesienie 274, 42</span><span class="sxs-lookup"><span data-stu-id="96578-223">Location: 274, 42</span></span><br /><br /> <span data-ttu-id="96578-224">Zmienia 75, 23</span><span class="sxs-lookup"><span data-stu-id="96578-224">Size: 75, 23</span></span><br /><br /> <span data-ttu-id="96578-225">Opis Spowoduje</span><span class="sxs-lookup"><span data-stu-id="96578-225">Text: Quit</span></span>|
    |<span data-ttu-id="96578-226">**TextBox**</span><span class="sxs-lookup"><span data-stu-id="96578-226">**TextBox**</span></span>|<span data-ttu-id="96578-227">Nazwij WorkflowStatus</span><span class="sxs-lookup"><span data-stu-id="96578-227">Name: WorkflowStatus</span></span><br /><br /> <span data-ttu-id="96578-228">Przeniesienie 10, 73</span><span class="sxs-lookup"><span data-stu-id="96578-228">Location: 10, 73</span></span><br /><br /> <span data-ttu-id="96578-229">Multiline Prawda</span><span class="sxs-lookup"><span data-stu-id="96578-229">Multiline: True</span></span><br /><br /> <span data-ttu-id="96578-230">Trybie Prawda</span><span class="sxs-lookup"><span data-stu-id="96578-230">ReadOnly: True</span></span><br /><br /> <span data-ttu-id="96578-231">Paski przewijania Pionow</span><span class="sxs-lookup"><span data-stu-id="96578-231">ScrollBars: Vertical</span></span><br /><br /> <span data-ttu-id="96578-232">Zmienia 338, 208</span><span class="sxs-lookup"><span data-stu-id="96578-232">Size: 338, 208</span></span>|

5. <span data-ttu-id="96578-233">Ustaw właściwość **AcceptButton** formularza na **EnterGuess**.</span><span class="sxs-lookup"><span data-stu-id="96578-233">Set the **AcceptButton** property of the form to **EnterGuess**.</span></span>

 <span data-ttu-id="96578-234">Poniższy przykład ilustruje ukończony formularz.</span><span class="sxs-lookup"><span data-stu-id="96578-234">The following example illustrates the completed form.</span></span>

 ![Zrzut ekranu przedstawiający formularz hosta przepływu Windows Workflow Foundation.](./media/how-to-create-and-run-a-long-running-workflow/windows-workflow-foundation-workflowhostform.png)

### <a name="BKMK_AddHelperMethods"></a><span data-ttu-id="96578-236">Aby dodać właściwości i metody pomocnika formularza</span><span class="sxs-lookup"><span data-stu-id="96578-236">To add the properties and helper methods of the form</span></span>

<span data-ttu-id="96578-237">Kroki opisane w tej sekcji dodają właściwości i metody pomocnika do klasy form, która konfiguruje interfejs użytkownika formularza do obsługi uruchamiania i wznawiania przepływów pracy dotyczących liczby prób.</span><span class="sxs-lookup"><span data-stu-id="96578-237">The steps in this section add properties and helper methods to the form class that configure the UI of the form to support running and resuming number guess workflows.</span></span>

1. <span data-ttu-id="96578-238">Kliknij prawym przyciskiem myszy pozycję **WorkflowHostForm** w **Eksplorator rozwiązań** i wybierz polecenie **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="96578-238">Right-click **WorkflowHostForm** in **Solution Explorer** and choose **View Code**.</span></span>

2. <span data-ttu-id="96578-239">Dodaj następujące `using` instrukcje (lub `Imports`) w górnej części pliku z innymi `using` instrukcjami (lub `Imports`).</span><span class="sxs-lookup"><span data-stu-id="96578-239">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>

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

3. <span data-ttu-id="96578-240">Dodaj następujące deklaracje elementu członkowskiego do klasy **WorkflowHostForm** .</span><span class="sxs-lookup"><span data-stu-id="96578-240">Add the following member declarations to the **WorkflowHostForm** class.</span></span>

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
    > <span data-ttu-id="96578-241">Jeśli parametry połączenia są inne, zaktualizuj `connectionString` , aby odwołać się do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="96578-241">If your connection string is different, update `connectionString` to refer to your database.</span></span>

4. <span data-ttu-id="96578-242">`WorkflowInstanceId` Dodaj Właściwość`WorkflowFormHost` do klasy.</span><span class="sxs-lookup"><span data-stu-id="96578-242">Add a `WorkflowInstanceId` property to the `WorkflowFormHost` class.</span></span>

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

    <span data-ttu-id="96578-243">Pole kombi wyświetla listę utrwalonych identyfikatorów wystąpień przepływów pracy, `WorkflowInstanceId` a właściwość zwraca aktualnie wybrany przepływ pracy. `InstanceId`</span><span class="sxs-lookup"><span data-stu-id="96578-243">The `InstanceId` combo box displays a list of persisted workflow instance ids, and the `WorkflowInstanceId` property returns the currently selected workflow.</span></span>

5. <span data-ttu-id="96578-244">Dodaj procedurę obsługi dla zdarzenia formularza `Load` .</span><span class="sxs-lookup"><span data-stu-id="96578-244">Add a handler for the form `Load` event.</span></span> <span data-ttu-id="96578-245">Aby dodać procedurę obsługi, przełącz się do **widoku projektu** dla formularza, kliknij ikonę **zdarzenia** w górnej części okna **Właściwości** , a następnie kliknij dwukrotnie przycisk Wczytaj.</span><span class="sxs-lookup"><span data-stu-id="96578-245">To add the handler, switch to **Design View** for the form, click the **Events** icon at the top of the **Properties** window, and double-click **Load**.</span></span>

    ```vb
    Private Sub WorkflowHostForm_Load(sender As Object, e As EventArgs) Handles Me.Load

    End Sub
    ```

    ```csharp
    private void WorkflowHostForm_Load(object sender, EventArgs e)
    {

    }
    ```

6. <span data-ttu-id="96578-246">Dodaj następujący kod do `WorkflowHostForm_Load`.</span><span class="sxs-lookup"><span data-stu-id="96578-246">Add the following code to `WorkflowHostForm_Load`.</span></span>

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

    <span data-ttu-id="96578-247">Gdy formularz `SqlWorkflowInstanceStore` zostanie załadowany, jest skonfigurowany, pole kombi zakres i typ przepływu pracy są ustawiane na wartości domyślne, a wystąpienia utrwalonych przepływów pracy są dodawane `InstanceId` do pola kombi.</span><span class="sxs-lookup"><span data-stu-id="96578-247">When the form loads, the `SqlWorkflowInstanceStore` is configured, the range and workflow type combo boxes are set to default values, and the persisted workflow instances are added to the `InstanceId` combo box.</span></span>

7. <span data-ttu-id="96578-248">Dodaj program obsługi dla `InstanceId`. `SelectedIndexChanged`</span><span class="sxs-lookup"><span data-stu-id="96578-248">Add a `SelectedIndexChanged` handler for `InstanceId`.</span></span> <span data-ttu-id="96578-249">Aby dodać procedurę obsługi, przełącz się **do widoku projektu** dla formularza, zaznacz `InstanceId` pole kombi, kliknij ikonę **zdarzenia** w górnej części okna **Właściwości** , a następnie kliknij dwukrotnie pozycję **SelectedIndexChanged.** .</span><span class="sxs-lookup"><span data-stu-id="96578-249">To add the handler, switch to **Design View** for the form, select the `InstanceId` combo box, click the **Events** icon at the top of the **Properties** window, and double-click **SelectedIndexChanged**.</span></span>

    ```vb
    Private Sub InstanceId_SelectedIndexChanged(sender As Object, e As EventArgs) Handles InstanceId.SelectedIndexChanged

    End Sub
    ```

    ```csharp
    private void InstanceId_SelectedIndexChanged(object sender, EventArgs e)
    {

    }
    ```

8. <span data-ttu-id="96578-250">Dodaj następujący kod do `InstanceId_SelectedIndexChanged`.</span><span class="sxs-lookup"><span data-stu-id="96578-250">Add the following code to `InstanceId_SelectedIndexChanged`.</span></span> <span data-ttu-id="96578-251">Za każdym razem, gdy użytkownik wybierze przepływ pracy za pomocą pola kombi, ta procedura obsługi aktualizuje okno stanu.</span><span class="sxs-lookup"><span data-stu-id="96578-251">Whenever the user selects a workflow by using the combo box this handler updates the status window.</span></span>

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

9. <span data-ttu-id="96578-252">Dodaj następującą `ListPersistedWorkflows` metodę do klasy form.</span><span class="sxs-lookup"><span data-stu-id="96578-252">Add the following `ListPersistedWorkflows` method to the form class.</span></span>

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

    <span data-ttu-id="96578-253">`ListPersistedWorkflows`wysyła zapytanie do magazynu wystąpień dla utrwalonych wystąpień przepływu pracy i dodaje do `cboInstanceId` pola kombi identyfikatory wystąpień.</span><span class="sxs-lookup"><span data-stu-id="96578-253">`ListPersistedWorkflows` queries the instance store for persisted workflow instances, and adds the instance ids to the `cboInstanceId` combo box.</span></span>

10. <span data-ttu-id="96578-254">Dodaj następującą `UpdateStatus` metodę i odpowiedni delegat do klasy form.</span><span class="sxs-lookup"><span data-stu-id="96578-254">Add the following `UpdateStatus` method and corresponding delegate to the form class.</span></span> <span data-ttu-id="96578-255">Ta metoda aktualizuje okno stanu w formularzu przy użyciu stanu aktualnie uruchomionego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="96578-255">This method updates the status window on the form with the status of the currently running workflow.</span></span>

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

11. <span data-ttu-id="96578-256">Dodaj następującą `GameOver` metodę i odpowiedni delegat do klasy form.</span><span class="sxs-lookup"><span data-stu-id="96578-256">Add the following `GameOver` method and corresponding delegate to the form class.</span></span> <span data-ttu-id="96578-257">Po zakończeniu przepływu pracy ta metoda aktualizuje interfejs użytkownika formularza, usuwając identyfikator wystąpienia ukończonego przepływu pracy z pola kombi **InstanceId** .</span><span class="sxs-lookup"><span data-stu-id="96578-257">When a workflow completes, this method updates the form UI by removing the instance id of the completed workflow from the **InstanceId** combo box.</span></span>

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

### <a name="BKMK_ConfigureWorkflowApplication"></a><span data-ttu-id="96578-258">Aby skonfigurować magazyn wystąpień, programy obsługi cyklu życia przepływu pracy i rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="96578-258">To configure the instance store, workflow lifecycle handlers, and extensions</span></span>

1. <span data-ttu-id="96578-259">`ConfigureWorkflowApplication` Dodaj metodę do klasy form.</span><span class="sxs-lookup"><span data-stu-id="96578-259">Add a `ConfigureWorkflowApplication` method to the form class.</span></span>

    ```vb
    Private Sub ConfigureWorkflowApplication(wfApp As WorkflowApplication)

    End Sub
    ```

    ```csharp
    private void ConfigureWorkflowApplication(WorkflowApplication wfApp)
    {
    }
    ```

    <span data-ttu-id="96578-260">Ta metoda służy do `WorkflowApplication`konfigurowania, dodawania wymaganych rozszerzeń i dodawania programów obsługi dla zdarzeń cyklu życia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="96578-260">This method configures the `WorkflowApplication`, adds the desired extensions, and adds handlers for the workflow lifecycle events.</span></span>

2. <span data-ttu-id="96578-261">W `ConfigureWorkflowApplication`programie `SqlWorkflowInstanceStore` Określ dla elementu. `WorkflowApplication`</span><span class="sxs-lookup"><span data-stu-id="96578-261">In `ConfigureWorkflowApplication`, specify the `SqlWorkflowInstanceStore` for the `WorkflowApplication`.</span></span>

    ```vb
    'Configure the persistence store.
    wfApp.InstanceStore = store
    ```

    ```csharp
    // Configure the persistence store.
    wfApp.InstanceStore = store;
    ```

3. <span data-ttu-id="96578-262">Następnie Utwórz `StringWriter` wystąpienie i Dodaj je `Extensions` do kolekcji `WorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="96578-262">Next, create a `StringWriter` instance and add it to the `Extensions` collection of the `WorkflowApplication`.</span></span> <span data-ttu-id="96578-263">Po dodaniu do rozszerzeń przechwytuje wszystkie `WriteLine` dane wyjściowe działania. `StringWriter`</span><span class="sxs-lookup"><span data-stu-id="96578-263">When a `StringWriter` is added to the extensions it captures all `WriteLine` activity output.</span></span> <span data-ttu-id="96578-264">Gdy przepływ pracy stanie się bezczynny, `WriteLine` dane wyjściowe można wyodrębnić `StringWriter` z i wyświetlić w formularzu.</span><span class="sxs-lookup"><span data-stu-id="96578-264">When the workflow becomes idle, the `WriteLine` output can be extracted from the `StringWriter` and displayed on the form.</span></span>

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

4. <span data-ttu-id="96578-265">Dodaj następującą procedurę obsługi dla `Completed` zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="96578-265">Add the following handler for the `Completed` event.</span></span> <span data-ttu-id="96578-266">Po pomyślnym ukończeniu przepływu pracy Liczba przełączeń podjętych w celu odgadnięcia liczby zostanie wyświetlona w oknie stanu.</span><span class="sxs-lookup"><span data-stu-id="96578-266">When a workflow successfully completes, the number of turns taken to guess the number is displayed to the status window.</span></span> <span data-ttu-id="96578-267">Jeśli przepływ pracy zakończy działanie, zostanie wyświetlona informacja o wyjątku, która spowodowała zakończenie.</span><span class="sxs-lookup"><span data-stu-id="96578-267">If the workflow terminates, the exception information that caused the termination is displayed.</span></span> <span data-ttu-id="96578-268">Na końcu procedury obsługi `GameOver` wywoływana jest metoda, która usuwa ukończony przepływ pracy z listy przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="96578-268">At the end of the handler the `GameOver` method is called, which removes the completed workflow from the workflow list.</span></span>

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

5. <span data-ttu-id="96578-269">Dodaj poniższe `Aborted` i `OnUnhandledException` programy obsługi.</span><span class="sxs-lookup"><span data-stu-id="96578-269">Add the following `Aborted` and `OnUnhandledException` handlers.</span></span> <span data-ttu-id="96578-270">Metoda nie jest wywoływana `Aborted` z programu obsługi, ponieważ wystąpienie przepływu pracy zostało przerwane, nie kończy się i możliwe jest wznowienie wystąpienia w późniejszym czasie. `GameOver`</span><span class="sxs-lookup"><span data-stu-id="96578-270">The `GameOver` method is not called from the `Aborted` handler because when a workflow instance is aborted, it does not terminate, and it is possible to resume the instance at a later time.</span></span>

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

6. <span data-ttu-id="96578-271">Dodaj następujący `PersistableIdle` program obsługi.</span><span class="sxs-lookup"><span data-stu-id="96578-271">Add the following `PersistableIdle` handler.</span></span> <span data-ttu-id="96578-272">Ta procedura obsługi pobiera `StringWriter` dodane rozszerzenie, wyodrębnia dane wyjściowe `WriteLine` z działań i wyświetla je w oknie stanu.</span><span class="sxs-lookup"><span data-stu-id="96578-272">This handler retrieves the `StringWriter` extension that was added, extracts the output from the `WriteLine` activities, and displays it in the status window.</span></span>

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

    <span data-ttu-id="96578-273">Wyliczenie ma trzy wartości: <xref:System.Activities.PersistableIdleAction.None>, <xref:System.Activities.PersistableIdleAction.Persist>, i <xref:System.Activities.PersistableIdleAction.Unload>. <xref:System.Activities.PersistableIdleAction></span><span class="sxs-lookup"><span data-stu-id="96578-273">The <xref:System.Activities.PersistableIdleAction> enumeration has three values: <xref:System.Activities.PersistableIdleAction.None>, <xref:System.Activities.PersistableIdleAction.Persist>, and <xref:System.Activities.PersistableIdleAction.Unload>.</span></span> <span data-ttu-id="96578-274"><xref:System.Activities.PersistableIdleAction.Persist>powoduje, że przepływ pracy ma być trwały, ale nie powoduje jego zwolnienia.</span><span class="sxs-lookup"><span data-stu-id="96578-274"><xref:System.Activities.PersistableIdleAction.Persist> causes the workflow to persist but it does not cause the workflow to unload.</span></span> <span data-ttu-id="96578-275"><xref:System.Activities.PersistableIdleAction.Unload>powoduje, że przepływ pracy jest trwały i zwalniany.</span><span class="sxs-lookup"><span data-stu-id="96578-275"><xref:System.Activities.PersistableIdleAction.Unload> causes the workflow to persist and be unloaded.</span></span>

    <span data-ttu-id="96578-276">Poniższy przykład to metoda zakończona `ConfigureWorkflowApplication` .</span><span class="sxs-lookup"><span data-stu-id="96578-276">The following example is the completed `ConfigureWorkflowApplication` method.</span></span>

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

### <a name="BKMK_WorkflowVersionMap"></a><span data-ttu-id="96578-277">Aby włączyć uruchamianie i wznawianie wielu typów przepływów pracy</span><span class="sxs-lookup"><span data-stu-id="96578-277">To enable starting and resuming multiple workflow types</span></span>

<span data-ttu-id="96578-278">Aby wznowić wystąpienie przepływu pracy, host musi podać definicję przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="96578-278">In order to resume a workflow instance, the host has to provide the workflow definition.</span></span> <span data-ttu-id="96578-279">W tym samouczku istnieją trzy typy przepływów pracy, a kolejne kroki samouczka wprowadzają wiele wersji tych typów.</span><span class="sxs-lookup"><span data-stu-id="96578-279">In this tutorial there are three workflow types, and subsequent tutorial steps introduce multiple versions of these types.</span></span> <span data-ttu-id="96578-280">`WorkflowIdentity`umożliwia aplikacji hosta kojarzenie informacji identyfikacyjnych z utrwalonym wystąpieniem przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="96578-280">`WorkflowIdentity` provides a way for a host application to associate identifying information with a persisted workflow instance.</span></span> <span data-ttu-id="96578-281">Kroki opisane w tej sekcji przedstawiają sposób tworzenia klasy narzędzi, która pomaga w mapowaniu tożsamości przepływu pracy z utrwalonego wystąpienia przepływu pracy do odpowiedniej definicji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="96578-281">The steps in this section demonstrate how to create a utility class to assist with mapping the workflow identity from a persisted workflow instance to the corresponding workflow definition.</span></span> <span data-ttu-id="96578-282">Aby uzyskać więcej informacji `WorkflowIdentity` na temat usługi i przechowywania wersji, zobacz [Korzystanie z właściwości WorkflowIdentity i przechowywanie wersji](using-workflowidentity-and-versioning.md).</span><span class="sxs-lookup"><span data-stu-id="96578-282">For more information about `WorkflowIdentity` and versioning, see [Using WorkflowIdentity and Versioning](using-workflowidentity-and-versioning.md).</span></span>

1. <span data-ttu-id="96578-283">Kliknij prawym przyciskiem myszy pozycję **NumberGuessWorkflowHost** w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj**, **Klasa**.</span><span class="sxs-lookup"><span data-stu-id="96578-283">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **Class**.</span></span> <span data-ttu-id="96578-284">Wpisz `WorkflowVersionMap` tekst w polu **Nazwa** , a następnie kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="96578-284">Type `WorkflowVersionMap` into the **Name** box and click **Add**.</span></span>

2. <span data-ttu-id="96578-285">Dodaj następujące `using` instrukcje lub `Imports` na początku pliku z innymi `using` instrukcjami or `Imports` .</span><span class="sxs-lookup"><span data-stu-id="96578-285">Add the following `using` or `Imports` statements at the top of the file with the other `using` or `Imports` statements.</span></span>

    ```vb
    Imports NumberGuessWorkflowActivities
    Imports System.Activities
    ```

    ```csharp
    using NumberGuessWorkflowActivities;
    using System.Activities;
    ```

3. <span data-ttu-id="96578-286">Zastąp `WorkflowVersionMap` deklarację klasy następującą deklaracją.</span><span class="sxs-lookup"><span data-stu-id="96578-286">Replace the `WorkflowVersionMap` class declaration with the following declaration.</span></span>

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

    <span data-ttu-id="96578-287">`WorkflowVersionMap`zawiera trzy tożsamości przepływu pracy, które są mapowane na trzy definicje przepływu pracy z tego samouczka i są używane w poniższych sekcjach, gdy przepływy pracy są uruchamiane i wznawiane.</span><span class="sxs-lookup"><span data-stu-id="96578-287">`WorkflowVersionMap` contains three workflow identities that map to the three workflow definitions from this tutorial and is used in the following sections when workflows are started and resumed.</span></span>

### <a name="BKMK_StartWorkflow"></a><span data-ttu-id="96578-288">Aby uruchomić nowy przepływ pracy</span><span class="sxs-lookup"><span data-stu-id="96578-288">To start a new workflow</span></span>

1. <span data-ttu-id="96578-289">Dodaj program obsługi dla `NewGame`. `Click`</span><span class="sxs-lookup"><span data-stu-id="96578-289">Add a `Click` handler for `NewGame`.</span></span> <span data-ttu-id="96578-290">Aby dodać procedurę obsługi, przełącz się do **widoku projektu** dla formularza i kliknij `NewGame`dwukrotnie.</span><span class="sxs-lookup"><span data-stu-id="96578-290">To add the handler, switch to **Design View** for the form, and double-click `NewGame`.</span></span> <span data-ttu-id="96578-291">Dodano `NewGame_Click` procedurę obsługi, a widok jest przełączany do widoku kodu formularza.</span><span class="sxs-lookup"><span data-stu-id="96578-291">A `NewGame_Click` handler is added and the view switches to code view for the form.</span></span> <span data-ttu-id="96578-292">Za każdym razem, gdy użytkownik kliknie ten przycisk, zostanie uruchomiony nowy przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="96578-292">Whenever the user clicks this button a new workflow is started.</span></span>

    ```vb
    Private Sub NewGame_Click(sender As Object, e As EventArgs) Handles NewGame.Click

    End Sub
    ```

    ```csharp
    private void NewGame_Click(object sender, EventArgs e)
    {

    }
    ```

2. <span data-ttu-id="96578-293">Dodaj następujący kod do programu obsługi kliknij.</span><span class="sxs-lookup"><span data-stu-id="96578-293">Add the following code to the click handler.</span></span> <span data-ttu-id="96578-294">Ten kod tworzy słownik argumentów wejściowych dla przepływu pracy, który jest poprzedzony przez nazwę argumentu.</span><span class="sxs-lookup"><span data-stu-id="96578-294">This code creates a dictionary of input arguments for the workflow, keyed by argument name.</span></span> <span data-ttu-id="96578-295">Ten słownik zawiera jeden wpis zawierający zakres losowo wygenerowanego numeru pobrany z pola kombi zakres.</span><span class="sxs-lookup"><span data-stu-id="96578-295">This dictionary has one entry that contains the range of the randomly generated number retrieved from the range combo box.</span></span>

    ```vb
    Dim inputs As New Dictionary(Of String, Object)()
    inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem))
    ```

    ```csharp
    var inputs = new Dictionary<string, object>();
    inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem));
    ```

3. <span data-ttu-id="96578-296">Następnie Dodaj następujący kod, który uruchamia przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="96578-296">Next, add the following code that starts the workflow.</span></span> <span data-ttu-id="96578-297">Definicja przepływu pracy `WorkflowVersionMap` iodpowiadającytypowiwybranegoprzepływupracysąpobieraneprzyużyciu`WorkflowIdentity` klasy pomocnika.</span><span class="sxs-lookup"><span data-stu-id="96578-297">The `WorkflowIdentity` and workflow definition corresponding to the type of workflow selected are retrieved using the `WorkflowVersionMap` helper class.</span></span> <span data-ttu-id="96578-298">Następnie nowe `WorkflowApplication` wystąpienie jest tworzone przy użyciu definicji przepływu pracy, `WorkflowIdentity`i słownika argumentów wejściowych.</span><span class="sxs-lookup"><span data-stu-id="96578-298">Next, a new `WorkflowApplication` instance is created using the workflow definition, `WorkflowIdentity`, and dictionary of input arguments.</span></span>

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

4. <span data-ttu-id="96578-299">Następnie Dodaj następujący kod, który dodaje przepływ pracy do listy przepływów pracy i wyświetla informacje o wersji przepływu pracy w formularzu.</span><span class="sxs-lookup"><span data-stu-id="96578-299">Next, add the following code which adds the workflow to the workflow list and displays the workflow's version information on the form.</span></span>

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

5. <span data-ttu-id="96578-300">Wywołaj `ConfigureWorkflowApplication` , aby skonfigurować magazyn wystąpień, rozszerzenia i obsługę cyklu życia przepływu pracy dla `WorkflowApplication` tego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="96578-300">Call `ConfigureWorkflowApplication` to configure the instance store, extensions, and workflow lifecycle handlers for this `WorkflowApplication` instance.</span></span>

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

6. <span data-ttu-id="96578-301">Na koniec Wywołaj metodę `Run`.</span><span class="sxs-lookup"><span data-stu-id="96578-301">Finally, call `Run`.</span></span>

    ```vb
    'Start the workflow.
    wfApp.Run()
    ```

    ```csharp
    // Start the workflow.
    wfApp.Run();
    ```

     <span data-ttu-id="96578-302">Poniższy przykład to zakończono `NewGame_Click` procedurę obsługi.</span><span class="sxs-lookup"><span data-stu-id="96578-302">The following example is the completed `NewGame_Click` handler.</span></span>

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

### <a name="BKMK_ResumeWorkflow"></a><span data-ttu-id="96578-303">Aby wznowić przepływ pracy</span><span class="sxs-lookup"><span data-stu-id="96578-303">To resume a workflow</span></span>

1. <span data-ttu-id="96578-304">Dodaj program obsługi dla `EnterGuess`. `Click`</span><span class="sxs-lookup"><span data-stu-id="96578-304">Add a `Click` handler for `EnterGuess`.</span></span> <span data-ttu-id="96578-305">Aby dodać procedurę obsługi, przełącz się do **widoku projektu** dla formularza i kliknij `EnterGuess`dwukrotnie.</span><span class="sxs-lookup"><span data-stu-id="96578-305">To add the handler, switch to **Design View** for the form, and double-click `EnterGuess`.</span></span> <span data-ttu-id="96578-306">Za każdym razem, gdy użytkownik kliknie ten przycisk, przepływ pracy zostaje wznowiony.</span><span class="sxs-lookup"><span data-stu-id="96578-306">Whenever the user clicks this button a workflow is resumed.</span></span>

    ```vb
    Private Sub EnterGuess_Click(sender As Object, e As EventArgs) Handles EnterGuess.Click

    End Sub
    ```

    ```csharp
    private void EnterGuess_Click(object sender, EventArgs e)
    {

    }
    ```

2. <span data-ttu-id="96578-307">Dodaj następujący kod, aby upewnić się, że przepływ pracy został wybrany na liście przepływów pracy i czy jego wartość jest prawidłowa.</span><span class="sxs-lookup"><span data-stu-id="96578-307">Add the following code to ensure that a workflow is selected in the workflow list, and that the user's guess is valid.</span></span>

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

3. <span data-ttu-id="96578-308">Następnie Pobierz `WorkflowApplicationInstance` wystąpienie utrwalonego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="96578-308">Next, retrieve the `WorkflowApplicationInstance` of the persisted workflow instance.</span></span> <span data-ttu-id="96578-309">`WorkflowApplicationInstance` Reprezentuje wystąpienie utrwalonego przepływu pracy, które nie zostało jeszcze skojarzone z definicją przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="96578-309">A `WorkflowApplicationInstance` represents a persisted workflow instance that has not yet been associated with a workflow definition.</span></span> <span data-ttu-id="96578-310">`DefinitionIdentity` Z`WorkflowApplicationInstance`zawierawystąpieniautrwalonegoprzepływupracy. `WorkflowIdentity`</span><span class="sxs-lookup"><span data-stu-id="96578-310">The `DefinitionIdentity` of the `WorkflowApplicationInstance` contains the `WorkflowIdentity` of the persisted workflow instance.</span></span> <span data-ttu-id="96578-311">W tym samouczku `WorkflowVersionMap` Klasa narzędzi służy do `WorkflowIdentity` mapowania do odpowiedniej definicji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="96578-311">In this tutorial, the `WorkflowVersionMap` utility class is used to map the `WorkflowIdentity` to the correct workflow definition.</span></span> <span data-ttu-id="96578-312">Po pobraniu `WorkflowApplication` definicji przepływu pracy jest ona tworzona przy użyciu prawidłowej definicji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="96578-312">Once the workflow definition is retrieved, a `WorkflowApplication` is created, using the correct workflow definition.</span></span>

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

4. <span data-ttu-id="96578-313">Po utworzeniu należy skonfigurować magazyn wystąpień, programy obsługi cyklu życia przepływu pracy i rozszerzenia przez wywołanie `ConfigureWorkflowApplication`. `WorkflowApplication`</span><span class="sxs-lookup"><span data-stu-id="96578-313">Once the `WorkflowApplication` is created, configure the instance store, workflow lifecycle handlers, and extensions by calling `ConfigureWorkflowApplication`.</span></span> <span data-ttu-id="96578-314">Te kroki należy wykonać za każdym razem, gdy `WorkflowApplication` tworzony jest nowy, i muszą one zostać wykonane przed załadowaniem wystąpienia przepływu pracy `WorkflowApplication`do.</span><span class="sxs-lookup"><span data-stu-id="96578-314">These steps must be done every time a new `WorkflowApplication` is created, and they must be done before the workflow instance is loaded into the `WorkflowApplication`.</span></span> <span data-ttu-id="96578-315">Po załadowaniu przepływu pracy zostanie on wznowiony z przypuszczeniem użytkownika.</span><span class="sxs-lookup"><span data-stu-id="96578-315">After the workflow is loaded, it is resumed with the user's guess.</span></span>

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

5. <span data-ttu-id="96578-316">Na koniec wyczyść pole tekstowe odgadnięcie i Przygotuj formularz do zaakceptowania innego argumentu.</span><span class="sxs-lookup"><span data-stu-id="96578-316">Finally, clear the guess textbox and prepare the form to accept another guess.</span></span>

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

    <span data-ttu-id="96578-317">Poniższy przykład to zakończono `EnterGuess_Click` procedurę obsługi.</span><span class="sxs-lookup"><span data-stu-id="96578-317">The following example is the completed `EnterGuess_Click` handler.</span></span>

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

### <a name="BKMK_TerminateWorkflow"></a><span data-ttu-id="96578-318">Aby zakończyć przepływ pracy</span><span class="sxs-lookup"><span data-stu-id="96578-318">To terminate a workflow</span></span>

1. <span data-ttu-id="96578-319">Dodaj program obsługi dla `QuitGame`. `Click`</span><span class="sxs-lookup"><span data-stu-id="96578-319">Add a `Click` handler for `QuitGame`.</span></span> <span data-ttu-id="96578-320">Aby dodać procedurę obsługi, przełącz się do **widoku projektu** dla formularza i kliknij `QuitGame`dwukrotnie.</span><span class="sxs-lookup"><span data-stu-id="96578-320">To add the handler, switch to **Design View** for the form, and double-click `QuitGame`.</span></span> <span data-ttu-id="96578-321">Za każdym razem, gdy użytkownik kliknie ten przycisk, aktualnie wybrany przepływ pracy zostanie zakończony.</span><span class="sxs-lookup"><span data-stu-id="96578-321">Whenever the user clicks this button the currently selected workflow is terminated.</span></span>

    ```vb
    Private Sub QuitGame_Click(sender As Object, e As EventArgs) Handles QuitGame.Click

    End Sub
    ```

    ```csharp
    private void QuitGame_Click(object sender, EventArgs e)
    {

    }
    ```

2. <span data-ttu-id="96578-322">Dodaj następujący kod do `QuitGame_Click` procedury obsługi.</span><span class="sxs-lookup"><span data-stu-id="96578-322">Add the following code to the `QuitGame_Click` handler.</span></span> <span data-ttu-id="96578-323">Ten kod najpierw sprawdza, czy przepływ pracy został wybrany na liście przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="96578-323">This code first checks to ensure that a workflow is selected in the workflow list.</span></span> <span data-ttu-id="96578-324">Następnie ładuje wystąpienie utrwalone do `WorkflowApplicationInstance`, `DefinitionIdentity` używa do określenia prawidłowej definicji przepływu pracy `WorkflowApplication`, a następnie inicjuje.</span><span class="sxs-lookup"><span data-stu-id="96578-324">Then it loads the persisted instance into a `WorkflowApplicationInstance`, uses the `DefinitionIdentity` to determine the correct workflow definition, and then initializes the `WorkflowApplication`.</span></span> <span data-ttu-id="96578-325">Kolejne rozszerzenia i programy obsługi cyklu życia przepływu pracy są skonfigurowane z wywołaniem `ConfigureWorkflowApplication`do.</span><span class="sxs-lookup"><span data-stu-id="96578-325">Next the extensions and workflow lifecycle handlers are configured with a call to `ConfigureWorkflowApplication`.</span></span> <span data-ttu-id="96578-326">Po skonfigurowaniu jest on ładowany, a następnie `Terminate` wywoływany. `WorkflowApplication`</span><span class="sxs-lookup"><span data-stu-id="96578-326">Once the `WorkflowApplication` is configured, it is loaded, and then `Terminate` is called.</span></span>

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

### <a name="BKMK_BuildAndRun"></a><span data-ttu-id="96578-327">Aby skompilować i uruchomić aplikację</span><span class="sxs-lookup"><span data-stu-id="96578-327">To build and run the application</span></span>

1. <span data-ttu-id="96578-328">Kliknij dwukrotnie pozycję **program.cs** (lub **Module1. vb**) w **Eksplorator rozwiązań** , aby wyświetlić kod.</span><span class="sxs-lookup"><span data-stu-id="96578-328">Double-click **Program.cs** (or **Module1.vb**) in **Solution Explorer** to display the code.</span></span>

2. <span data-ttu-id="96578-329">Dodaj następującą `using` instrukcję (lub `Imports`) w górnej części pliku z innymi `using` instrukcjami (lub `Imports`).</span><span class="sxs-lookup"><span data-stu-id="96578-329">Add the following `using` (or `Imports`) statement at the top of the file with the other `using` (or `Imports`) statements.</span></span>

    ```vb
    Imports System.Windows.Forms
    ```

    ```csharp
    using System.Windows.Forms;
    ```

3. <span data-ttu-id="96578-330">Usuń lub Skomentuj istniejący kod hostingu przepływu pracy z [: Uruchom przepływ pracy](how-to-run-a-workflow.md)i zastąp go następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="96578-330">Remove or comment out the existing workflow hosting code from [How to: Run a Workflow](how-to-run-a-workflow.md), and replace it with the following code.</span></span>

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

4. <span data-ttu-id="96578-331">Kliknij prawym przyciskiem myszy pozycję **NumberGuessWorkflowHost** w **Eksplorator rozwiązań** i wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="96578-331">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Properties**.</span></span> <span data-ttu-id="96578-332">Na karcie **aplikacja** Określ **aplikację systemu Windows** dla **typu danych wyjściowych**.</span><span class="sxs-lookup"><span data-stu-id="96578-332">In the **Application** tab, specify **Windows Application** for the **Output type**.</span></span> <span data-ttu-id="96578-333">Ten krok jest opcjonalny, ale jeśli nie jest zastosowana, okno konsoli jest wyświetlane oprócz formularza.</span><span class="sxs-lookup"><span data-stu-id="96578-333">This step is optional, but if it is not followed the console window is displayed in addition to the form.</span></span>

5. <span data-ttu-id="96578-334">Naciśnij klawisze CTRL + SHIFT + B, aby skompilować aplikację.</span><span class="sxs-lookup"><span data-stu-id="96578-334">Press Ctrl+Shift+B to build the application.</span></span>

6. <span data-ttu-id="96578-335">Upewnij się, że **NumberGuessWorkflowHost** jest ustawiony jako aplikacja startowa, a następnie naciśnij klawisze CTRL + F5, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="96578-335">Ensure that **NumberGuessWorkflowHost** is set as the startup application, and press Ctrl+F5 to start the application.</span></span>

7. <span data-ttu-id="96578-336">Wybierz zakres dla gry do odgadnięcia i typ przepływu pracy do uruchomienia, a następnie kliknij pozycję **Nowa gra**.</span><span class="sxs-lookup"><span data-stu-id="96578-336">Select a range for the guessing game and the type of workflow to start, and click **New Game**.</span></span> <span data-ttu-id="96578-337">Wprowadź wartość w polu **zgadywanie** i kliknij pozycję **Przejdź** , aby przesłać przypuszczenie.</span><span class="sxs-lookup"><span data-stu-id="96578-337">Enter a guess in the **Guess** box and click **Go** to submit your guess.</span></span> <span data-ttu-id="96578-338">Należy zauważyć, że dane wyjściowe `WriteLine` działań są wyświetlane w formularzu.</span><span class="sxs-lookup"><span data-stu-id="96578-338">Note that the output from the `WriteLine` activities is displayed on the form.</span></span>

8. <span data-ttu-id="96578-339">Rozpocznij pracę z kilkoma przepływami pracy przy użyciu różnych typów i zakresów liczbowych, wprowadź liczbę prób i przełączaj się między przepływami pracy, wybierając z listy **Identyfikator wystąpienia przepływu pracy** .</span><span class="sxs-lookup"><span data-stu-id="96578-339">Start several workflows using different workflow types and number ranges, enter some guesses, and switch between the workflows by selecting from the **Workflow Instance Id** list.</span></span>

    <span data-ttu-id="96578-340">Należy pamiętać, że po przełączeniu do nowego przepływu pracy poprzednie wartości i postęp przepływu pracy nie są wyświetlane w oknie stanu.</span><span class="sxs-lookup"><span data-stu-id="96578-340">Note that when you switch to a new workflow, the previous guesses and progress of the workflow are not displayed in the status window.</span></span> <span data-ttu-id="96578-341">Przyczyna stanu jest niedostępna, ponieważ nie jest ona przechwycona i zapisana w dowolnym miejscu.</span><span class="sxs-lookup"><span data-stu-id="96578-341">The reason the status is not available is because it is not captured and saved anywhere.</span></span> <span data-ttu-id="96578-342">W następnym kroku samouczka [: Utwórz niestandardowego uczestnika](how-to-create-a-custom-tracking-participant.md)śledzenia, tworząc niestandardowego uczestnika śledzenia, który zapisuje te informacje.</span><span class="sxs-lookup"><span data-stu-id="96578-342">In the next step of the tutorial, [How to: Create a Custom Tracking Participant](how-to-create-a-custom-tracking-participant.md), you create a custom tracking participant that saves this information.</span></span>
