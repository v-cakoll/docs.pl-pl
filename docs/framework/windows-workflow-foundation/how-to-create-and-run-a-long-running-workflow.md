---
title: Jak utworzyć i uruchomić długotrwały przepływ pracy
description: W tym artykule opisano sposób tworzenia aplikacji hosta Windows Forms, która obsługuje uruchamianie i wznawianie wielu wystąpień przepływów pracy i trwałego przepływu pracy.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c0043c89-2192-43c9-986d-3ecec4dd8c9c
ms.openlocfilehash: 557b3512e534198d47c0c6f6b0a7c5f92bb71739
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419554"
---
# <a name="how-to-create-and-run-a-long-running-workflow"></a><span data-ttu-id="a60d4-103">Jak utworzyć i uruchomić długotrwały przepływ pracy</span><span class="sxs-lookup"><span data-stu-id="a60d4-103">How to create and run a long-running workflow</span></span>

<span data-ttu-id="a60d4-104">Jedną z centralnych funkcji Windows Workflow Foundation (WF) jest zdolność środowiska uruchomieniowego do utrwalania i zwalniania bezczynnych przepływów pracy do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="a60d4-104">One of the central features of Windows Workflow Foundation (WF) is the runtime’s ability to persist and unload idle workflows to a database.</span></span> <span data-ttu-id="a60d4-105">Kroki opisane w temacie [How to: Run a Workflow](how-to-run-a-workflow.md) — podstawowe informacje o hostingu przepływu pracy przy użyciu aplikacji konsolowej.</span><span class="sxs-lookup"><span data-stu-id="a60d4-105">The steps in [How to: Run a Workflow](how-to-run-a-workflow.md) demonstrated the basics of workflow hosting using a console application.</span></span> <span data-ttu-id="a60d4-106">Przedstawiono przykłady uruchamiania przepływów pracy, obsługi cyklu życia przepływu pracy i wznawiania zakładek.</span><span class="sxs-lookup"><span data-stu-id="a60d4-106">Examples were shown of starting workflows, workflow lifecycle handlers, and resuming bookmarks.</span></span> <span data-ttu-id="a60d4-107">W celu efektywnego zademonstrowania trwałości przepływu pracy wymagany jest bardziej złożony host przepływu pracy, który obsługuje uruchamianie i wznawianie wielu wystąpień przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="a60d4-107">In order to demonstrate workflow persistence effectively, a more complex workflow host is required that supports starting and resuming multiple workflow instances.</span></span> <span data-ttu-id="a60d4-108">Ten krok w samouczku pokazuje, jak utworzyć aplikację hosta formularza systemu Windows, która obsługuje uruchamianie i wznawianie wielu wystąpień przepływów pracy, trwałość przepływu pracy i stanowi podstawę zaawansowanych funkcji, takich jak śledzenie i przechowywanie wersji, które przedstawiono w kolejnych krokach samouczka.</span><span class="sxs-lookup"><span data-stu-id="a60d4-108">This step in the tutorial demonstrates how to create a Windows form host application that supports starting and resuming multiple workflow instances, workflow persistence, and provides a basis for the advanced features such as tracking and versioning that are demonstrated in subsequent tutorial steps.</span></span>

> [!NOTE]
> <span data-ttu-id="a60d4-109">Ten krok samouczka i kolejne kroki używają wszystkich trzech typów przepływu pracy, [które są następujące: tworzenie przepływu pracy](how-to-create-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="a60d4-109">This tutorial step and the subsequent steps use all three workflow types from [How to: Create a Workflow](how-to-create-a-workflow.md).</span></span> <span data-ttu-id="a60d4-110">Jeśli wszystkie trzy typy nie zostały wykonane, można pobrać ukończoną wersję kroków z [Windows Workflow Foundation (WF45) — wprowadzenie samouczka](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="a60d4-110">If you did not complete all three types you can download a completed version of the steps from [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>

> [!NOTE]
> <span data-ttu-id="a60d4-111">Aby pobrać kompletną wersję lub wyświetlić przewodnik wideo samouczka, zobacz [Windows Workflow Foundation (WF45) — samouczek wprowadzenie](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="a60d4-111">To download a completed version or view a video walkthrough of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>

## <a name="to-create-the-persistence-database"></a><span data-ttu-id="a60d4-112">Aby utworzyć bazę danych trwałości</span><span class="sxs-lookup"><span data-stu-id="a60d4-112">To create the persistence database</span></span>

1. <span data-ttu-id="a60d4-113">Otwórz SQL Server Management Studio i Połącz się z serwerem lokalnym, na przykład **.\SQLEXPRESS**.</span><span class="sxs-lookup"><span data-stu-id="a60d4-113">Open SQL Server Management Studio and connect to the local server, for example **.\SQLEXPRESS**.</span></span> <span data-ttu-id="a60d4-114">Kliknij prawym przyciskiem myszy węzeł **bazy danych** na serwerze lokalnym, a następnie wybierz pozycję **Nowa baza danych**.</span><span class="sxs-lookup"><span data-stu-id="a60d4-114">Right-click the **Databases** node on the local server, and select **New Database**.</span></span> <span data-ttu-id="a60d4-115">Nazwa nowej bazy danych **WF45GettingStartedTutorial**, Zaakceptuj wszystkie inne wartości, a następnie wybierz **przycisk OK**.</span><span class="sxs-lookup"><span data-stu-id="a60d4-115">Name the new database **WF45GettingStartedTutorial**, accept all other values, and select **OK**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="a60d4-116">Przed utworzeniem bazy danych upewnij się, że masz uprawnienia do **tworzenia bazy danych** na serwerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="a60d4-116">Ensure that you have **Create Database** permission on the local server before creating the database.</span></span>

2. <span data-ttu-id="a60d4-117">Wybierz polecenie **Otwórz**, **plik** z menu **plik** .</span><span class="sxs-lookup"><span data-stu-id="a60d4-117">Choose **Open**, **File** from the **File** menu.</span></span> <span data-ttu-id="a60d4-118">Przejdź do następującego folderu: *C:\Windows\Microsoft.NET\Framework\v4.0.30319\sql\en*</span><span class="sxs-lookup"><span data-stu-id="a60d4-118">Browse to the following folder: *C:\Windows\Microsoft.NET\Framework\v4.0.30319\sql\en*</span></span>

    <span data-ttu-id="a60d4-119">Wybierz poniższe dwa pliki, a następnie kliknij przycisk **Otwórz**.</span><span class="sxs-lookup"><span data-stu-id="a60d4-119">Select the following two files and click **Open**.</span></span>

    - <span data-ttu-id="a60d4-120">*SqlWorkflowInstanceStoreLogic. SQL*</span><span class="sxs-lookup"><span data-stu-id="a60d4-120">*SqlWorkflowInstanceStoreLogic.sql*</span></span>

    - <span data-ttu-id="a60d4-121">*SqlWorkflowInstanceStoreSchema. SQL*</span><span class="sxs-lookup"><span data-stu-id="a60d4-121">*SqlWorkflowInstanceStoreSchema.sql*</span></span>

3. <span data-ttu-id="a60d4-122">Wybierz **SqlWorkflowInstanceStoreSchema. SQL** z menu **okno** .</span><span class="sxs-lookup"><span data-stu-id="a60d4-122">Choose **SqlWorkflowInstanceStoreSchema.sql** from the **Window** menu.</span></span> <span data-ttu-id="a60d4-123">Upewnij się, że wybrano pozycję **WF45GettingStartedTutorial** na liście rozwijanej **dostępne bazy danych** , a następnie wybierz polecenie **Wykonaj** z menu **zapytania** .</span><span class="sxs-lookup"><span data-stu-id="a60d4-123">Ensure that **WF45GettingStartedTutorial** is selected in the **Available Databases** drop-down and choose **Execute** from the **Query** menu.</span></span>

4. <span data-ttu-id="a60d4-124">Wybierz **SqlWorkflowInstanceStoreLogic. SQL** z menu **okno** .</span><span class="sxs-lookup"><span data-stu-id="a60d4-124">Choose **SqlWorkflowInstanceStoreLogic.sql** from the **Window** menu.</span></span> <span data-ttu-id="a60d4-125">Upewnij się, że wybrano pozycję **WF45GettingStartedTutorial** na liście rozwijanej **dostępne bazy danych** , a następnie wybierz polecenie **Wykonaj** z menu **zapytania** .</span><span class="sxs-lookup"><span data-stu-id="a60d4-125">Ensure that **WF45GettingStartedTutorial** is selected in the **Available Databases** drop-down and choose **Execute** from the **Query** menu.</span></span>

    > [!WARNING]
    > <span data-ttu-id="a60d4-126">Ważne jest, aby wykonać dwa poprzednie kroki w odpowiedniej kolejności.</span><span class="sxs-lookup"><span data-stu-id="a60d4-126">It is important to perform the previous two steps in the correct order.</span></span> <span data-ttu-id="a60d4-127">Jeśli zapytania są wykonywane poza kolejnością, wystąpią błędy i baza danych trwałości nie jest poprawnie skonfigurowana.</span><span class="sxs-lookup"><span data-stu-id="a60d4-127">If the queries are executed out of order, errors occur and the persistence database is not configured correctly.</span></span>

## <a name="to-add-the-reference-to-the-durableinstancing-assemblies"></a><span data-ttu-id="a60d4-128">Aby dodać odwołanie do zestawów DurableInstancing</span><span class="sxs-lookup"><span data-stu-id="a60d4-128">To add the reference to the DurableInstancing assemblies</span></span>

1. <span data-ttu-id="a60d4-129">Kliknij prawym przyciskiem myszy pozycję **NumberGuessWorkflowHost** w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="a60d4-129">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and select **Add Reference**.</span></span>

2. <span data-ttu-id="a60d4-130">Wybierz pozycję **zestawy** z listy **Dodaj odwołanie** , a następnie wpisz `DurableInstancing` w polu **wyszukiwania zestawów** .</span><span class="sxs-lookup"><span data-stu-id="a60d4-130">Select **Assemblies** from the **Add Reference** list, and type `DurableInstancing` into the **Search Assemblies** box.</span></span> <span data-ttu-id="a60d4-131">To filtruje zestawy i ułatwia wybór odpowiednich odwołań.</span><span class="sxs-lookup"><span data-stu-id="a60d4-131">This filters the assemblies and makes the desired references easier to select.</span></span>

3. <span data-ttu-id="a60d4-132">Zaznacz pole wyboru obok pozycji **System. Activities. DurableInstancing** i **System. Runtime. DurableInstancing** z listy **wyników wyszukiwania** , a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="a60d4-132">Check the checkbox beside **System.Activities.DurableInstancing** and **System.Runtime.DurableInstancing** from the **Search Results** list, and click **OK**.</span></span>

## <a name="to-create-the-workflow-host-form"></a><span data-ttu-id="a60d4-133">Aby utworzyć formularz hosta przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="a60d4-133">To create the workflow host form</span></span>

> [!NOTE]
> <span data-ttu-id="a60d4-134">Kroki opisane w tej procedurze opisują sposób ręcznego dodawania i konfigurowania formularza.</span><span class="sxs-lookup"><span data-stu-id="a60d4-134">The steps in this procedure describe how to add and configure the form manually.</span></span> <span data-ttu-id="a60d4-135">W razie potrzeby można pobrać pliki rozwiązania dla samouczka i dodać ukończony formularz do projektu.</span><span class="sxs-lookup"><span data-stu-id="a60d4-135">If desired, you can download the solution files for the tutorial and add the completed form to the project.</span></span> <span data-ttu-id="a60d4-136">Aby pobrać pliki samouczka, zobacz [Windows Workflow Foundation (WF45) — samouczek wprowadzenie](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="a60d4-136">To download the tutorial files, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span> <span data-ttu-id="a60d4-137">Po pobraniu plików kliknij prawym przyciskiem myszy pozycję **NumberGuessWorkflowHost** i wybierz polecenie **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="a60d4-137">Once the files are downloaded, right-click **NumberGuessWorkflowHost** and choose **Add Reference**.</span></span> <span data-ttu-id="a60d4-138">Dodaj odwołanie do **System. Windows. Forms** i **System. Drawing**.</span><span class="sxs-lookup"><span data-stu-id="a60d4-138">Add a reference to **System.Windows.Forms** and **System.Drawing**.</span></span> <span data-ttu-id="a60d4-139">Te odwołania są dodawane automatycznie po dodaniu nowego formularza z menu **Dodaj**, **nowy element** , ale należy dodać go ręcznie podczas importowania formularza.</span><span class="sxs-lookup"><span data-stu-id="a60d4-139">These references are added automatically if you add a new form from the **Add**, **New Item** menu, but must be added manually when importing a form.</span></span> <span data-ttu-id="a60d4-140">Po dodaniu odwołań kliknij prawym przyciskiem myszy pozycję **NumberGuessWorkflowHost** w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj**, **istniejący element**.</span><span class="sxs-lookup"><span data-stu-id="a60d4-140">Once the references are added, right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **Existing Item**.</span></span> <span data-ttu-id="a60d4-141">Przejdź do `Form` folderu w plikach projektu, wybierz pozycję **WorkflowHostForm.cs** (lub **WorkflowHostForm. vb**), a następnie kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="a60d4-141">Browse to the `Form` folder in the project files, select **WorkflowHostForm.cs** (or **WorkflowHostForm.vb**), and click **Add**.</span></span> <span data-ttu-id="a60d4-142">Jeśli zdecydujesz się zaimportować formularz, możesz przejść do następnej sekcji, [Aby dodać właściwości i metody pomocnika formularza](#to-add-the-properties-and-helper-methods-of-the-form).</span><span class="sxs-lookup"><span data-stu-id="a60d4-142">If you choose to import the form, then you can skip down to the next section, [To add the properties and helper methods of the form](#to-add-the-properties-and-helper-methods-of-the-form).</span></span>

1. <span data-ttu-id="a60d4-143">Kliknij prawym przyciskiem myszy pozycję **NumberGuessWorkflowHost** w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj**, **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="a60d4-143">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **New Item**.</span></span>

2. <span data-ttu-id="a60d4-144">Na liście **zainstalowane** szablony wybierz pozycję **formularz systemu Windows**, wpisz `WorkflowHostForm` w polu **Nazwa** , a następnie kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="a60d4-144">In the **Installed** templates list, choose **Windows Form**, type `WorkflowHostForm` in the **Name** box, and click **Add**.</span></span>

3. <span data-ttu-id="a60d4-145">Skonfiguruj następujące właściwości w formularzu.</span><span class="sxs-lookup"><span data-stu-id="a60d4-145">Configure the following properties on the form.</span></span>

    |<span data-ttu-id="a60d4-146">Właściwość</span><span class="sxs-lookup"><span data-stu-id="a60d4-146">Property</span></span>|<span data-ttu-id="a60d4-147">Wartość</span><span class="sxs-lookup"><span data-stu-id="a60d4-147">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="a60d4-148">FormBorderStyle</span><span class="sxs-lookup"><span data-stu-id="a60d4-148">FormBorderStyle</span></span>|<span data-ttu-id="a60d4-149">FixedSingle</span><span class="sxs-lookup"><span data-stu-id="a60d4-149">FixedSingle</span></span>|
    |<span data-ttu-id="a60d4-150">MaximizeBox</span><span class="sxs-lookup"><span data-stu-id="a60d4-150">MaximizeBox</span></span>|<span data-ttu-id="a60d4-151">False</span><span class="sxs-lookup"><span data-stu-id="a60d4-151">False</span></span>|
    |<span data-ttu-id="a60d4-152">Rozmiar</span><span class="sxs-lookup"><span data-stu-id="a60d4-152">Size</span></span>|<span data-ttu-id="a60d4-153">400, 420</span><span class="sxs-lookup"><span data-stu-id="a60d4-153">400, 420</span></span>|

4. <span data-ttu-id="a60d4-154">Dodaj następujące kontrolki do formularza w określonej kolejności i skonfiguruj właściwości jako kierowane.</span><span class="sxs-lookup"><span data-stu-id="a60d4-154">Add the following controls to the form in the order specified and configure the properties as directed.</span></span>

    |<span data-ttu-id="a60d4-155">Kontrola</span><span class="sxs-lookup"><span data-stu-id="a60d4-155">Control</span></span>|<span data-ttu-id="a60d4-156">Właściwość: wartość</span><span class="sxs-lookup"><span data-stu-id="a60d4-156">Property: Value</span></span>|
    |-------------|---------------------|
    |<span data-ttu-id="a60d4-157">**Przycisk**</span><span class="sxs-lookup"><span data-stu-id="a60d4-157">**Button**</span></span>|<span data-ttu-id="a60d4-158">Nazwa: NewGame</span><span class="sxs-lookup"><span data-stu-id="a60d4-158">Name: NewGame</span></span><br /><br /> <span data-ttu-id="a60d4-159">Lokalizacja: 13, 13</span><span class="sxs-lookup"><span data-stu-id="a60d4-159">Location: 13, 13</span></span><br /><br /> <span data-ttu-id="a60d4-160">Rozmiar: 75, 23</span><span class="sxs-lookup"><span data-stu-id="a60d4-160">Size: 75, 23</span></span><br /><br /> <span data-ttu-id="a60d4-161">Tekst: nowa gra</span><span class="sxs-lookup"><span data-stu-id="a60d4-161">Text: New Game</span></span>|
    |<span data-ttu-id="a60d4-162">**Etykieta**</span><span class="sxs-lookup"><span data-stu-id="a60d4-162">**Label**</span></span>|<span data-ttu-id="a60d4-163">Lokalizacja: 94, 18</span><span class="sxs-lookup"><span data-stu-id="a60d4-163">Location: 94, 18</span></span><br /><br /> <span data-ttu-id="a60d4-164">Tekst: zgadywanie liczby z 1 do</span><span class="sxs-lookup"><span data-stu-id="a60d4-164">Text: Guess a number from 1 to</span></span>|
    |<span data-ttu-id="a60d4-165">**ComboBox**</span><span class="sxs-lookup"><span data-stu-id="a60d4-165">**ComboBox**</span></span>|<span data-ttu-id="a60d4-166">Nazwa: NumberRange</span><span class="sxs-lookup"><span data-stu-id="a60d4-166">Name: NumberRange</span></span><br /><br /> <span data-ttu-id="a60d4-167">Lista rozwijana: DropDownList</span><span class="sxs-lookup"><span data-stu-id="a60d4-167">DropDownStyle: DropDownList</span></span><br /><br /> <span data-ttu-id="a60d4-168">Elementy: 10, 100, 1000</span><span class="sxs-lookup"><span data-stu-id="a60d4-168">Items: 10, 100, 1000</span></span><br /><br /> <span data-ttu-id="a60d4-169">Lokalizacja: 228, 12</span><span class="sxs-lookup"><span data-stu-id="a60d4-169">Location: 228, 12</span></span><br /><br /> <span data-ttu-id="a60d4-170">Rozmiar: 143, 21</span><span class="sxs-lookup"><span data-stu-id="a60d4-170">Size: 143, 21</span></span>|
    |<span data-ttu-id="a60d4-171">**Etykieta**</span><span class="sxs-lookup"><span data-stu-id="a60d4-171">**Label**</span></span>|<span data-ttu-id="a60d4-172">Lokalizacja: 13, 43</span><span class="sxs-lookup"><span data-stu-id="a60d4-172">Location: 13, 43</span></span><br /><br /> <span data-ttu-id="a60d4-173">Text: typ przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="a60d4-173">Text: Workflow type</span></span>|
    |<span data-ttu-id="a60d4-174">**ComboBox**</span><span class="sxs-lookup"><span data-stu-id="a60d4-174">**ComboBox**</span></span>|<span data-ttu-id="a60d4-175">Nazwa: WorkflowType</span><span class="sxs-lookup"><span data-stu-id="a60d4-175">Name: WorkflowType</span></span><br /><br /> <span data-ttu-id="a60d4-176">Lista rozwijana: DropDownList</span><span class="sxs-lookup"><span data-stu-id="a60d4-176">DropDownStyle: DropDownList</span></span><br /><br /> <span data-ttu-id="a60d4-177">Elementy: StateMachineNumberGuessWorkflow, FlowchartNumberGuessWorkflow, SequentialNumberGuessWorkflow</span><span class="sxs-lookup"><span data-stu-id="a60d4-177">Items: StateMachineNumberGuessWorkflow, FlowchartNumberGuessWorkflow, SequentialNumberGuessWorkflow</span></span><br /><br /> <span data-ttu-id="a60d4-178">Lokalizacja: 94, 40</span><span class="sxs-lookup"><span data-stu-id="a60d4-178">Location: 94, 40</span></span><br /><br /> <span data-ttu-id="a60d4-179">Rozmiar: 277, 21</span><span class="sxs-lookup"><span data-stu-id="a60d4-179">Size: 277, 21</span></span>|
    |<span data-ttu-id="a60d4-180">**Etykieta**</span><span class="sxs-lookup"><span data-stu-id="a60d4-180">**Label**</span></span>|<span data-ttu-id="a60d4-181">Nazwa: WorkflowVersion</span><span class="sxs-lookup"><span data-stu-id="a60d4-181">Name: WorkflowVersion</span></span><br /><br /> <span data-ttu-id="a60d4-182">Lokalizacja: 13, 362</span><span class="sxs-lookup"><span data-stu-id="a60d4-182">Location: 13, 362</span></span><br /><br /> <span data-ttu-id="a60d4-183">Tekst: wersja przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="a60d4-183">Text: Workflow version</span></span>|
    |<span data-ttu-id="a60d4-184">**GroupBox**</span><span class="sxs-lookup"><span data-stu-id="a60d4-184">**GroupBox**</span></span>|<span data-ttu-id="a60d4-185">Lokalizacja: 13, 67</span><span class="sxs-lookup"><span data-stu-id="a60d4-185">Location: 13, 67</span></span><br /><br /> <span data-ttu-id="a60d4-186">Rozmiar: 358, 287</span><span class="sxs-lookup"><span data-stu-id="a60d4-186">Size: 358, 287</span></span><br /><br /> <span data-ttu-id="a60d4-187">Tekst: gra</span><span class="sxs-lookup"><span data-stu-id="a60d4-187">Text: Game</span></span>|

    > [!NOTE]
    > <span data-ttu-id="a60d4-188">Podczas dodawania następujących kontrolek należy umieścić je w polu grupy.</span><span class="sxs-lookup"><span data-stu-id="a60d4-188">When adding the following controls, put them into the GroupBox.</span></span>

    |<span data-ttu-id="a60d4-189">Kontrola</span><span class="sxs-lookup"><span data-stu-id="a60d4-189">Control</span></span>|<span data-ttu-id="a60d4-190">Właściwość: wartość</span><span class="sxs-lookup"><span data-stu-id="a60d4-190">Property: Value</span></span>|
    |-------------|---------------------|
    |<span data-ttu-id="a60d4-191">**Etykieta**</span><span class="sxs-lookup"><span data-stu-id="a60d4-191">**Label**</span></span>|<span data-ttu-id="a60d4-192">Lokalizacja: 7, 20</span><span class="sxs-lookup"><span data-stu-id="a60d4-192">Location: 7, 20</span></span><br /><br /> <span data-ttu-id="a60d4-193">Tekst: identyfikator wystąpienia przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="a60d4-193">Text: Workflow Instance Id</span></span>|
    |<span data-ttu-id="a60d4-194">**ComboBox**</span><span class="sxs-lookup"><span data-stu-id="a60d4-194">**ComboBox**</span></span>|<span data-ttu-id="a60d4-195">Nazwa: identyfikator wystąpienia</span><span class="sxs-lookup"><span data-stu-id="a60d4-195">Name: InstanceId</span></span><br /><br /> <span data-ttu-id="a60d4-196">Lista rozwijana: DropDownList</span><span class="sxs-lookup"><span data-stu-id="a60d4-196">DropDownStyle: DropDownList</span></span><br /><br /> <span data-ttu-id="a60d4-197">Lokalizacja: 121, 17</span><span class="sxs-lookup"><span data-stu-id="a60d4-197">Location: 121, 17</span></span><br /><br /> <span data-ttu-id="a60d4-198">Rozmiar: 227, 21</span><span class="sxs-lookup"><span data-stu-id="a60d4-198">Size: 227, 21</span></span>|
    |<span data-ttu-id="a60d4-199">**Etykieta**</span><span class="sxs-lookup"><span data-stu-id="a60d4-199">**Label**</span></span>|<span data-ttu-id="a60d4-200">Lokalizacja: 7, 47</span><span class="sxs-lookup"><span data-stu-id="a60d4-200">Location: 7, 47</span></span><br /><br /> <span data-ttu-id="a60d4-201">Tekst: zgadywanie</span><span class="sxs-lookup"><span data-stu-id="a60d4-201">Text: Guess</span></span>|
    |<span data-ttu-id="a60d4-202">**Tekstowym**</span><span class="sxs-lookup"><span data-stu-id="a60d4-202">**TextBox**</span></span>|<span data-ttu-id="a60d4-203">Nazwa: zgadywanie</span><span class="sxs-lookup"><span data-stu-id="a60d4-203">Name: Guess</span></span><br /><br /> <span data-ttu-id="a60d4-204">Lokalizacja: 50, 44</span><span class="sxs-lookup"><span data-stu-id="a60d4-204">Location: 50, 44</span></span><br /><br /> <span data-ttu-id="a60d4-205">Rozmiar: 65, 20</span><span class="sxs-lookup"><span data-stu-id="a60d4-205">Size: 65, 20</span></span>|
    |<span data-ttu-id="a60d4-206">**Przycisk**</span><span class="sxs-lookup"><span data-stu-id="a60d4-206">**Button**</span></span>|<span data-ttu-id="a60d4-207">Nazwa: EnterGuess</span><span class="sxs-lookup"><span data-stu-id="a60d4-207">Name: EnterGuess</span></span><br /><br /> <span data-ttu-id="a60d4-208">Lokalizacja: 121, 42</span><span class="sxs-lookup"><span data-stu-id="a60d4-208">Location: 121, 42</span></span><br /><br /> <span data-ttu-id="a60d4-209">Rozmiar: 75, 23</span><span class="sxs-lookup"><span data-stu-id="a60d4-209">Size: 75, 23</span></span><br /><br /> <span data-ttu-id="a60d4-210">Tekst: wprowadź zgadywanie</span><span class="sxs-lookup"><span data-stu-id="a60d4-210">Text: Enter Guess</span></span>|
    |<span data-ttu-id="a60d4-211">**Przycisk**</span><span class="sxs-lookup"><span data-stu-id="a60d4-211">**Button**</span></span>|<span data-ttu-id="a60d4-212">Nazwa: QuitGame</span><span class="sxs-lookup"><span data-stu-id="a60d4-212">Name: QuitGame</span></span><br /><br /> <span data-ttu-id="a60d4-213">Lokalizacja: 274, 42</span><span class="sxs-lookup"><span data-stu-id="a60d4-213">Location: 274, 42</span></span><br /><br /> <span data-ttu-id="a60d4-214">Rozmiar: 75, 23</span><span class="sxs-lookup"><span data-stu-id="a60d4-214">Size: 75, 23</span></span><br /><br /> <span data-ttu-id="a60d4-215">Tekst: Zamknij</span><span class="sxs-lookup"><span data-stu-id="a60d4-215">Text: Quit</span></span>|
    |<span data-ttu-id="a60d4-216">**Tekstowym**</span><span class="sxs-lookup"><span data-stu-id="a60d4-216">**TextBox**</span></span>|<span data-ttu-id="a60d4-217">Nazwa: WorkflowStatus</span><span class="sxs-lookup"><span data-stu-id="a60d4-217">Name: WorkflowStatus</span></span><br /><br /> <span data-ttu-id="a60d4-218">Lokalizacja: 10, 73</span><span class="sxs-lookup"><span data-stu-id="a60d4-218">Location: 10, 73</span></span><br /><br /> <span data-ttu-id="a60d4-219">Wielowierszowy: prawda</span><span class="sxs-lookup"><span data-stu-id="a60d4-219">Multiline: True</span></span><br /><br /> <span data-ttu-id="a60d4-220">ReadOnly: true</span><span class="sxs-lookup"><span data-stu-id="a60d4-220">ReadOnly: True</span></span><br /><br /> <span data-ttu-id="a60d4-221">Paski przewijania: pionowa</span><span class="sxs-lookup"><span data-stu-id="a60d4-221">ScrollBars: Vertical</span></span><br /><br /> <span data-ttu-id="a60d4-222">Rozmiar: 338, 208</span><span class="sxs-lookup"><span data-stu-id="a60d4-222">Size: 338, 208</span></span>|

5. <span data-ttu-id="a60d4-223">Ustaw właściwość **AcceptButton** formularza na **EnterGuess**.</span><span class="sxs-lookup"><span data-stu-id="a60d4-223">Set the **AcceptButton** property of the form to **EnterGuess**.</span></span>

 <span data-ttu-id="a60d4-224">Poniższy przykład ilustruje ukończony formularz.</span><span class="sxs-lookup"><span data-stu-id="a60d4-224">The following example illustrates the completed form.</span></span>

 ![Zrzut ekranu przedstawiający formularz hosta przepływu Windows Workflow Foundation.](./media/how-to-create-and-run-a-long-running-workflow/windows-workflow-foundation-workflowhostform.png)

## <a name="to-add-the-properties-and-helper-methods-of-the-form"></a><span data-ttu-id="a60d4-226">Aby dodać właściwości i metody pomocnika formularza</span><span class="sxs-lookup"><span data-stu-id="a60d4-226">To add the properties and helper methods of the form</span></span>

<span data-ttu-id="a60d4-227">Kroki opisane w tej sekcji dodają właściwości i metody pomocnika do klasy form, która konfiguruje interfejs użytkownika formularza do obsługi uruchamiania i wznawiania przepływów pracy dotyczących liczby prób.</span><span class="sxs-lookup"><span data-stu-id="a60d4-227">The steps in this section add properties and helper methods to the form class that configure the UI of the form to support running and resuming number guess workflows.</span></span>

1. <span data-ttu-id="a60d4-228">Kliknij prawym przyciskiem myszy pozycję **WorkflowHostForm** w **Eksplorator rozwiązań** i wybierz polecenie **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="a60d4-228">Right-click **WorkflowHostForm** in **Solution Explorer** and choose **View Code**.</span></span>

2. <span data-ttu-id="a60d4-229">Dodaj następujące `using` instrukcje (lub `Imports` ) w górnej części pliku z innymi `using` instrukcjami (lub `Imports` ).</span><span class="sxs-lookup"><span data-stu-id="a60d4-229">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>

    ```vb
    Imports System.Activities
    Imports System.Activities.DurableInstancing
    Imports System.Data.SqlClient
    Imports System.IO
    Imports System.Windows.Forms
    ```

    ```csharp
    using System.Activities;
    using System.Activities.DurableInstancing;
    using System.Data.SqlClient;
    using System.IO;
    using System.Windows.Forms;
    ```

3. <span data-ttu-id="a60d4-230">Dodaj następujące deklaracje elementu członkowskiego do klasy **WorkflowHostForm** .</span><span class="sxs-lookup"><span data-stu-id="a60d4-230">Add the following member declarations to the **WorkflowHostForm** class.</span></span>

    ```vb
    Const connectionString = "Server=.\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI"
    Dim store As SqlWorkflowInstanceStore
    Dim workflowStarting As Boolean
    ```

    ```csharp
    const string connectionString = "Server=.\\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI";
    SqlWorkflowInstanceStore store;
    bool workflowStarting;
    ```

    > [!NOTE]
    > <span data-ttu-id="a60d4-231">Jeśli parametry połączenia są inne, zaktualizuj, `connectionString` Aby odwołać się do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="a60d4-231">If your connection string is different, update `connectionString` to refer to your database.</span></span>

4. <span data-ttu-id="a60d4-232">Dodaj `WorkflowInstanceId` Właściwość do `WorkflowFormHost` klasy.</span><span class="sxs-lookup"><span data-stu-id="a60d4-232">Add a `WorkflowInstanceId` property to the `WorkflowFormHost` class.</span></span>

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

    <span data-ttu-id="a60d4-233">`InstanceId`Pole kombi wyświetla listę utrwalonych identyfikatorów wystąpień przepływów pracy, a `WorkflowInstanceId` Właściwość zwraca aktualnie wybrany przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="a60d4-233">The `InstanceId` combo box displays a list of persisted workflow instance ids, and the `WorkflowInstanceId` property returns the currently selected workflow.</span></span>

5. <span data-ttu-id="a60d4-234">Dodaj procedurę obsługi dla zdarzenia formularza `Load` .</span><span class="sxs-lookup"><span data-stu-id="a60d4-234">Add a handler for the form `Load` event.</span></span> <span data-ttu-id="a60d4-235">Aby dodać procedurę obsługi, przełącz się do **widoku projektu** dla formularza, kliknij ikonę **zdarzenia** w górnej części okna **Właściwości** , a następnie kliknij dwukrotnie przycisk **Wczytaj**.</span><span class="sxs-lookup"><span data-stu-id="a60d4-235">To add the handler, switch to **Design View** for the form, click the **Events** icon at the top of the **Properties** window, and double-click **Load**.</span></span>

    ```vb
    Private Sub WorkflowHostForm_Load(sender As Object, e As EventArgs) Handles Me.Load

    End Sub
    ```

    ```csharp
    private void WorkflowHostForm_Load(object sender, EventArgs e)
    {

    }
    ```

6. <span data-ttu-id="a60d4-236">Dodaj następujący kod do `WorkflowHostForm_Load` .</span><span class="sxs-lookup"><span data-stu-id="a60d4-236">Add the following code to `WorkflowHostForm_Load`.</span></span>

    ```vb
    ' Initialize the store and configure it so that it can be used for
    ' multiple WorkflowApplication instances.
    store = New SqlWorkflowInstanceStore(connectionString)
    WorkflowApplication.CreateDefaultInstanceOwner(store, Nothing, WorkflowIdentityFilter.Any)

    ' Set default ComboBox selections.
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

    <span data-ttu-id="a60d4-237">Gdy formularz zostanie załadowany, `SqlWorkflowInstanceStore` jest skonfigurowany, pole kombi zakres i typ przepływu pracy są ustawiane na wartości domyślne, a wystąpienia utrwalonych przepływów pracy są dodawane do `InstanceId` pola kombi.</span><span class="sxs-lookup"><span data-stu-id="a60d4-237">When the form loads, the `SqlWorkflowInstanceStore` is configured, the range and workflow type combo boxes are set to default values, and the persisted workflow instances are added to the `InstanceId` combo box.</span></span>

7. <span data-ttu-id="a60d4-238">Dodaj `SelectedIndexChanged` program obsługi dla `InstanceId` .</span><span class="sxs-lookup"><span data-stu-id="a60d4-238">Add a `SelectedIndexChanged` handler for `InstanceId`.</span></span> <span data-ttu-id="a60d4-239">Aby dodać procedurę obsługi, przełącz się do **widoku projektu** dla formularza, zaznacz `InstanceId` pole kombi, kliknij ikonę **zdarzenia** w górnej części okna **Właściwości** , a następnie kliknij dwukrotnie pozycję **SelectedIndexChanged.**.</span><span class="sxs-lookup"><span data-stu-id="a60d4-239">To add the handler, switch to **Design View** for the form, select the `InstanceId` combo box, click the **Events** icon at the top of the **Properties** window, and double-click **SelectedIndexChanged**.</span></span>

    ```vb
    Private Sub InstanceId_SelectedIndexChanged(sender As Object, e As EventArgs) Handles InstanceId.SelectedIndexChanged

    End Sub
    ```

    ```csharp
    private void InstanceId_SelectedIndexChanged(object sender, EventArgs e)
    {

    }
    ```

8. <span data-ttu-id="a60d4-240">Dodaj następujący kod do `InstanceId_SelectedIndexChanged` .</span><span class="sxs-lookup"><span data-stu-id="a60d4-240">Add the following code to `InstanceId_SelectedIndexChanged`.</span></span> <span data-ttu-id="a60d4-241">Za każdym razem, gdy użytkownik wybierze przepływ pracy za pomocą pola kombi, ta procedura obsługi aktualizuje okno stanu.</span><span class="sxs-lookup"><span data-stu-id="a60d4-241">Whenever the user selects a workflow by using the combo box this handler updates the status window.</span></span>

    ```vb
    If InstanceId.SelectedIndex = -1 Then
        Return
    End If

    ' Clear the status window.
    WorkflowStatus.Clear()

    ' Get the workflow version and display it.
    ' If the workflow is just starting then this info will not
    ' be available in the persistence store so do not try and retrieve it.
    If Not workflowStarting Then
        Dim instance As WorkflowApplicationInstance = _
            WorkflowApplication.GetInstance(WorkflowInstanceId, store)

        WorkflowVersion.Text = _
            WorkflowVersionMap.GetIdentityDescription(instance.DefinitionIdentity)

        ' Unload the instance.
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
    if (!workflowStarting)
    {
        WorkflowApplicationInstance instance =
            WorkflowApplication.GetInstance(this.WorkflowInstanceId, store);

        WorkflowVersion.Text =
            WorkflowVersionMap.GetIdentityDescription(instance.DefinitionIdentity);

        // Unload the instance.
        instance.Abandon();
    }
    ```

9. <span data-ttu-id="a60d4-242">Dodaj następującą `ListPersistedWorkflows` metodę do klasy form.</span><span class="sxs-lookup"><span data-stu-id="a60d4-242">Add the following `ListPersistedWorkflows` method to the form class.</span></span>

    ```vb
    Private Sub ListPersistedWorkflows()
        Using localCon As New SqlConnection(connectionString)
            Dim localCmd As String = _
                "SELECT [InstanceId] FROM [System.Activities.DurableInstancing].[Instances] ORDER BY [CreationTime]"

            Dim cmd As SqlCommand = localCon.CreateCommand()
            cmd.CommandText = localCmd
            localCon.Open()
            Using reader As SqlDataReader = cmd.ExecuteReader(CommandBehavior.CloseConnection)

                While (reader.Read())
                    ' Get the InstanceId of the persisted Workflow.
                    Dim id As Guid = Guid.Parse(reader(0).ToString())
                    InstanceId.Items.Add(id)
                End While
            End Using
        End Using
    End Sub
    ```

    ```csharp
    using (var localCon = new SqlConnection(connectionString))
    {
        string localCmd =
            "SELECT [InstanceId] FROM [System.Activities.DurableInstancing].[Instances] ORDER BY [CreationTime]";

        SqlCommand cmd = localCon.CreateCommand();
        cmd.CommandText = localCmd;
        localCon.Open();
        using (SqlDataReader reader = cmd.ExecuteReader(CommandBehavior.CloseConnection))
        {
            while (reader.Read())
            {
                // Get the InstanceId of the persisted Workflow.
                Guid id = Guid.Parse(reader[0].ToString());
                InstanceId.Items.Add(id);
            }
        }
    }
    ```

    <span data-ttu-id="a60d4-243">`ListPersistedWorkflows`wysyła zapytanie do magazynu wystąpień dla utrwalonych wystąpień przepływu pracy i dodaje do `cboInstanceId` pola kombi identyfikatory wystąpień.</span><span class="sxs-lookup"><span data-stu-id="a60d4-243">`ListPersistedWorkflows` queries the instance store for persisted workflow instances, and adds the instance ids to the `cboInstanceId` combo box.</span></span>

10. <span data-ttu-id="a60d4-244">Dodaj następującą `UpdateStatus` metodę i odpowiedni delegat do klasy form.</span><span class="sxs-lookup"><span data-stu-id="a60d4-244">Add the following `UpdateStatus` method and corresponding delegate to the form class.</span></span> <span data-ttu-id="a60d4-245">Ta metoda aktualizuje okno stanu w formularzu przy użyciu stanu aktualnie uruchomionego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="a60d4-245">This method updates the status window on the form with the status of the currently running workflow.</span></span>

    ```vb
    Private Delegate Sub UpdateStatusDelegate(msg As String)
    Public Sub UpdateStatus(msg As String)
        ' We may be on a different thread so we need to
        ' make this call using BeginInvoke.
        If InvokeRequired Then
            BeginInvoke(New UpdateStatusDelegate(AddressOf UpdateStatus), msg)
        Else
            If Not msg.EndsWith(vbCrLf) Then
                msg = msg & vbCrLf
            End If

            WorkflowStatus.AppendText(msg)

            ' Ensure that the newly added status is visible.
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

11. <span data-ttu-id="a60d4-246">Dodaj następującą `GameOver` metodę i odpowiedni delegat do klasy form.</span><span class="sxs-lookup"><span data-stu-id="a60d4-246">Add the following `GameOver` method and corresponding delegate to the form class.</span></span> <span data-ttu-id="a60d4-247">Po zakończeniu przepływu pracy ta metoda aktualizuje interfejs użytkownika formularza, usuwając identyfikator wystąpienia ukończonego przepływu pracy z pola kombi **InstanceId** .</span><span class="sxs-lookup"><span data-stu-id="a60d4-247">When a workflow completes, this method updates the form UI by removing the instance id of the completed workflow from the **InstanceId** combo box.</span></span>

    ```vb
    Private Delegate Sub GameOverDelegate()
    Private Sub GameOver()
        If InvokeRequired Then
            BeginInvoke(New GameOverDelegate(AddressOf GameOver))
        Else
            ' Remove this instance from the InstanceId combo box.
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
            // Remove this instance from the combo box.
            InstanceId.Items.Remove(InstanceId.SelectedItem);
            InstanceId.SelectedIndex = -1;
        }
    }
    ```

## <a name="to-configure-the-instance-store-workflow-lifecycle-handlers-and-extensions"></a><span data-ttu-id="a60d4-248">Aby skonfigurować magazyn wystąpień, programy obsługi cyklu życia przepływu pracy i rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="a60d4-248">To configure the instance store, workflow lifecycle handlers, and extensions</span></span>

1. <span data-ttu-id="a60d4-249">Dodaj `ConfigureWorkflowApplication` metodę do klasy form.</span><span class="sxs-lookup"><span data-stu-id="a60d4-249">Add a `ConfigureWorkflowApplication` method to the form class.</span></span>

    ```vb
    Private Sub ConfigureWorkflowApplication(wfApp As WorkflowApplication)

    End Sub
    ```

    ```csharp
    private void ConfigureWorkflowApplication(WorkflowApplication wfApp)
    {
    }
    ```

    <span data-ttu-id="a60d4-250">Ta metoda służy do konfigurowania `WorkflowApplication` , dodawania wymaganych rozszerzeń i dodawania programów obsługi dla zdarzeń cyklu życia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="a60d4-250">This method configures the `WorkflowApplication`, adds the desired extensions, and adds handlers for the workflow lifecycle events.</span></span>

2. <span data-ttu-id="a60d4-251">W programie `ConfigureWorkflowApplication` Określ `SqlWorkflowInstanceStore` dla elementu `WorkflowApplication` .</span><span class="sxs-lookup"><span data-stu-id="a60d4-251">In `ConfigureWorkflowApplication`, specify the `SqlWorkflowInstanceStore` for the `WorkflowApplication`.</span></span>

    ```vb
    ' Configure the persistence store.
    wfApp.InstanceStore = store
    ```

    ```csharp
    // Configure the persistence store.
    wfApp.InstanceStore = store;
    ```

3. <span data-ttu-id="a60d4-252">Następnie Utwórz `StringWriter` wystąpienie i Dodaj je do `Extensions` kolekcji `WorkflowApplication` .</span><span class="sxs-lookup"><span data-stu-id="a60d4-252">Next, create a `StringWriter` instance and add it to the `Extensions` collection of the `WorkflowApplication`.</span></span> <span data-ttu-id="a60d4-253">Po `StringWriter` dodaniu do rozszerzeń przechwytuje wszystkie `WriteLine` dane wyjściowe działania.</span><span class="sxs-lookup"><span data-stu-id="a60d4-253">When a `StringWriter` is added to the extensions it captures all `WriteLine` activity output.</span></span> <span data-ttu-id="a60d4-254">Gdy przepływ pracy stanie się bezczynny, `WriteLine` dane wyjściowe można wyodrębnić z `StringWriter` i wyświetlić w formularzu.</span><span class="sxs-lookup"><span data-stu-id="a60d4-254">When the workflow becomes idle, the `WriteLine` output can be extracted from the `StringWriter` and displayed on the form.</span></span>

    ```vb
    ' Add a StringWriter to the extensions. This captures the output
    ' from the WriteLine activities so we can display it in the form.
    Dim sw As New StringWriter()
    wfApp.Extensions.Add(sw)
    ```

    ```csharp
    // Add a StringWriter to the extensions. This captures the output
    // from the WriteLine activities so we can display it in the form.
    var sw = new StringWriter();
    wfApp.Extensions.Add(sw);
    ```

4. <span data-ttu-id="a60d4-255">Dodaj następującą procedurę obsługi dla `Completed` zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="a60d4-255">Add the following handler for the `Completed` event.</span></span> <span data-ttu-id="a60d4-256">Po pomyślnym ukończeniu przepływu pracy Liczba przełączeń podjętych w celu odgadnięcia liczby zostanie wyświetlona w oknie stanu.</span><span class="sxs-lookup"><span data-stu-id="a60d4-256">When a workflow successfully completes, the number of turns taken to guess the number is displayed to the status window.</span></span> <span data-ttu-id="a60d4-257">Jeśli przepływ pracy zakończy działanie, zostanie wyświetlona informacja o wyjątku, która spowodowała zakończenie.</span><span class="sxs-lookup"><span data-stu-id="a60d4-257">If the workflow terminates, the exception information that caused the termination is displayed.</span></span> <span data-ttu-id="a60d4-258">Na końcu procedury obsługi `GameOver` wywoływana jest metoda, która usuwa ukończony przepływ pracy z listy przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="a60d4-258">At the end of the handler the `GameOver` method is called, which removes the completed workflow from the workflow list.</span></span>

    ```vb
    wfApp.Completed = _
        Sub(e As WorkflowApplicationCompletedEventArgs)
            If e.CompletionState = ActivityInstanceState.Faulted Then
                UpdateStatus($"Workflow Terminated. Exception: {e.TerminationException.GetType().FullName}{vbCrLf}{e.TerminationException.Message}")
            ElseIf e.CompletionState = ActivityInstanceState.Canceled Then
                UpdateStatus("Workflow Canceled.")
            Else
                Dim turns As Integer = Convert.ToInt32(e.Outputs("Turns"))
                UpdateStatus($"Congratulations, you guessed the number in {turns} turns.")
            End If
            GameOver()
        End Sub
    ```

    ```csharp
    wfApp.Completed = delegate(WorkflowApplicationCompletedEventArgs e)
    {
        if (e.CompletionState == ActivityInstanceState.Faulted)
        {
            UpdateStatus($"Workflow Terminated. Exception: {e.TerminationException.GetType().FullName}\r\n{e.TerminationException.Message}");
        }
        else if (e.CompletionState == ActivityInstanceState.Canceled)
        {
            UpdateStatus("Workflow Canceled.");
        }
        else
        {
            int turns = Convert.ToInt32(e.Outputs["Turns"]);
            UpdateStatus($"Congratulations, you guessed the number in {turns} turns.");
        }
        GameOver();
    };
    ```

5. <span data-ttu-id="a60d4-259">Dodaj poniższe `Aborted` i `OnUnhandledException` programy obsługi.</span><span class="sxs-lookup"><span data-stu-id="a60d4-259">Add the following `Aborted` and `OnUnhandledException` handlers.</span></span> <span data-ttu-id="a60d4-260">`GameOver`Metoda nie jest wywoływana z `Aborted` programu obsługi, ponieważ wystąpienie przepływu pracy zostało przerwane, nie kończy się i możliwe jest wznowienie wystąpienia w późniejszym czasie.</span><span class="sxs-lookup"><span data-stu-id="a60d4-260">The `GameOver` method is not called from the `Aborted` handler because when a workflow instance is aborted, it does not terminate, and it is possible to resume the instance at a later time.</span></span>

    ```vb
    wfApp.Aborted = _
        Sub(e As WorkflowApplicationAbortedEventArgs)
            UpdateStatus($"Workflow Aborted. Exception: {e.Reason.GetType().FullName}{vbCrLf}{e.Reason.Message}")
        End Sub

    wfApp.OnUnhandledException = _
        Function(e As WorkflowApplicationUnhandledExceptionEventArgs)
            UpdateStatus($"Unhandled Exception: {e.UnhandledException.GetType().FullName}{vbCrLf}{e.UnhandledException.Message}")
            GameOver()
            Return UnhandledExceptionAction.Terminate
        End Function
    ```

    ```csharp
    wfApp.Aborted = delegate(WorkflowApplicationAbortedEventArgs e)
    {
        UpdateStatus($"Workflow Aborted. Exception: {e.Reason.GetType().FullName}\r\n{e.Reason.Message}");
    };

    wfApp.OnUnhandledException = delegate(WorkflowApplicationUnhandledExceptionEventArgs e)
    {
        UpdateStatus($"Unhandled Exception: {e.UnhandledException.GetType().FullName}\r\n{e.UnhandledException.Message}");
        GameOver();
        return UnhandledExceptionAction.Terminate;
    };
    ```

6. <span data-ttu-id="a60d4-261">Dodaj następujący `PersistableIdle` program obsługi.</span><span class="sxs-lookup"><span data-stu-id="a60d4-261">Add the following `PersistableIdle` handler.</span></span> <span data-ttu-id="a60d4-262">Ta procedura obsługi pobiera `StringWriter` dodane rozszerzenie, wyodrębnia dane wyjściowe z `WriteLine` działań i wyświetla je w oknie stanu.</span><span class="sxs-lookup"><span data-stu-id="a60d4-262">This handler retrieves the `StringWriter` extension that was added, extracts the output from the `WriteLine` activities, and displays it in the status window.</span></span>

    ```vb
    wfApp.PersistableIdle = _
        Function(e As WorkflowApplicationIdleEventArgs)
            ' Send the current WriteLine outputs to the status window.
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

    <span data-ttu-id="a60d4-263"><xref:System.Activities.PersistableIdleAction>Wyliczenie ma trzy wartości: <xref:System.Activities.PersistableIdleAction.None> , <xref:System.Activities.PersistableIdleAction.Persist> , i <xref:System.Activities.PersistableIdleAction.Unload> .</span><span class="sxs-lookup"><span data-stu-id="a60d4-263">The <xref:System.Activities.PersistableIdleAction> enumeration has three values: <xref:System.Activities.PersistableIdleAction.None>, <xref:System.Activities.PersistableIdleAction.Persist>, and <xref:System.Activities.PersistableIdleAction.Unload>.</span></span> <span data-ttu-id="a60d4-264"><xref:System.Activities.PersistableIdleAction.Persist>powoduje, że przepływ pracy ma być trwały, ale nie powoduje jego zwolnienia.</span><span class="sxs-lookup"><span data-stu-id="a60d4-264"><xref:System.Activities.PersistableIdleAction.Persist> causes the workflow to persist but it does not cause the workflow to unload.</span></span> <span data-ttu-id="a60d4-265"><xref:System.Activities.PersistableIdleAction.Unload>powoduje, że przepływ pracy jest trwały i zwalniany.</span><span class="sxs-lookup"><span data-stu-id="a60d4-265"><xref:System.Activities.PersistableIdleAction.Unload> causes the workflow to persist and be unloaded.</span></span>

    <span data-ttu-id="a60d4-266">Poniższy przykład to `ConfigureWorkflowApplication` Metoda zakończona.</span><span class="sxs-lookup"><span data-stu-id="a60d4-266">The following example is the completed `ConfigureWorkflowApplication` method.</span></span>

    ```vb
    Private Sub ConfigureWorkflowApplication(wfApp As WorkflowApplication)
        ' Configure the persistence store.
        wfApp.InstanceStore = store

        ' Add a StringWriter to the extensions. This captures the output
        ' from the WriteLine activities so we can display it in the form.
        Dim sw As New StringWriter()
        wfApp.Extensions.Add(sw)

        wfApp.Completed = _
            Sub(e As WorkflowApplicationCompletedEventArgs)
                If e.CompletionState = ActivityInstanceState.Faulted Then
                    UpdateStatus($"Workflow Terminated. Exception: {e.TerminationException.GetType().FullName}{vbCrLf}{e.TerminationException.Message}")
                ElseIf e.CompletionState = ActivityInstanceState.Canceled Then
                    UpdateStatus("Workflow Canceled.")
                Else
                    Dim turns As Integer = Convert.ToInt32(e.Outputs("Turns"))
                    UpdateStatus($"Congratulations, you guessed the number in {turns} turns.")
                End If
                GameOver()
            End Sub

        wfApp.Aborted = _
            Sub(e As WorkflowApplicationAbortedEventArgs)
                UpdateStatus($"Workflow Aborted. Exception: {e.Reason.GetType().FullName}{vbCrLf}{e.Reason.Message}")
            End Sub

        wfApp.OnUnhandledException = _
            Function(e As WorkflowApplicationUnhandledExceptionEventArgs)
                UpdateStatus($"Unhandled Exception: {e.UnhandledException.GetType().FullName}{vbCrLf}{e.UnhandledException.Message}")
                GameOver()
                Return UnhandledExceptionAction.Terminate
            End Function

        wfApp.PersistableIdle = _
            Function(e As WorkflowApplicationIdleEventArgs)
                ' Send the current WriteLine outputs to the status window.
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
        var sw = new StringWriter();
        wfApp.Extensions.Add(sw);

        wfApp.Completed = delegate(WorkflowApplicationCompletedEventArgs e)
        {
            if (e.CompletionState == ActivityInstanceState.Faulted)
            {
                UpdateStatus($"Workflow Terminated. Exception: {e.TerminationException.GetType().FullName}\r\n{e.TerminationException.Message}");
            }
            else if (e.CompletionState == ActivityInstanceState.Canceled)
            {
                UpdateStatus("Workflow Canceled.");
            }
            else
            {
                int turns = Convert.ToInt32(e.Outputs["Turns"]);
                UpdateStatus($"Congratulations, you guessed the number in {turns} turns.");
            }
            GameOver();
        };

        wfApp.Aborted = delegate(WorkflowApplicationAbortedEventArgs e)
        {
            UpdateStatus($"Workflow Aborted. Exception: {e.Reason.GetType().FullName}\r\n{e.Reason.Message}");
        };

        wfApp.OnUnhandledException = delegate(WorkflowApplicationUnhandledExceptionEventArgs e)
        {
            UpdateStatus($"Unhandled Exception: {e.UnhandledException.GetType().FullName}\r\n{e.UnhandledException.Message}");
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

## <a name="to-enable-starting-and-resuming-multiple-workflow-types"></a><span data-ttu-id="a60d4-267">Aby włączyć uruchamianie i wznawianie wielu typów przepływów pracy</span><span class="sxs-lookup"><span data-stu-id="a60d4-267">To enable starting and resuming multiple workflow types</span></span>

<span data-ttu-id="a60d4-268">Aby wznowić wystąpienie przepływu pracy, host musi podać definicję przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="a60d4-268">In order to resume a workflow instance, the host has to provide the workflow definition.</span></span> <span data-ttu-id="a60d4-269">W tym samouczku istnieją trzy typy przepływów pracy, a kolejne kroki samouczka wprowadzają wiele wersji tych typów.</span><span class="sxs-lookup"><span data-stu-id="a60d4-269">In this tutorial there are three workflow types, and subsequent tutorial steps introduce multiple versions of these types.</span></span> <span data-ttu-id="a60d4-270">`WorkflowIdentity`umożliwia aplikacji hosta kojarzenie informacji identyfikacyjnych z utrwalonym wystąpieniem przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="a60d4-270">`WorkflowIdentity` provides a way for a host application to associate identifying information with a persisted workflow instance.</span></span> <span data-ttu-id="a60d4-271">Kroki opisane w tej sekcji przedstawiają sposób tworzenia klasy narzędzi, która pomaga w mapowaniu tożsamości przepływu pracy z utrwalonego wystąpienia przepływu pracy do odpowiedniej definicji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="a60d4-271">The steps in this section demonstrate how to create a utility class to assist with mapping the workflow identity from a persisted workflow instance to the corresponding workflow definition.</span></span> <span data-ttu-id="a60d4-272">Aby uzyskać więcej informacji na temat usługi `WorkflowIdentity` i przechowywania wersji, zobacz [Korzystanie z właściwości WorkflowIdentity i przechowywanie wersji](using-workflowidentity-and-versioning.md).</span><span class="sxs-lookup"><span data-stu-id="a60d4-272">For more information about `WorkflowIdentity` and versioning, see [Using WorkflowIdentity and Versioning](using-workflowidentity-and-versioning.md).</span></span>

1. <span data-ttu-id="a60d4-273">Kliknij prawym przyciskiem myszy pozycję **NumberGuessWorkflowHost** w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj**, **Klasa**.</span><span class="sxs-lookup"><span data-stu-id="a60d4-273">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **Class**.</span></span> <span data-ttu-id="a60d4-274">Wpisz tekst `WorkflowVersionMap` w polu **Nazwa** , a następnie kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="a60d4-274">Type `WorkflowVersionMap` into the **Name** box and click **Add**.</span></span>

2. <span data-ttu-id="a60d4-275">Dodaj następujące `using` instrukcje lub `Imports` na początku pliku z innymi `using` `Imports` instrukcjami or.</span><span class="sxs-lookup"><span data-stu-id="a60d4-275">Add the following `using` or `Imports` statements at the top of the file with the other `using` or `Imports` statements.</span></span>

    ```vb
    Imports System.Activities
    Imports NumberGuessWorkflowActivities
    ```

    ```csharp
    using System.Activities;
    using NumberGuessWorkflowActivities;
    ```

3. <span data-ttu-id="a60d4-276">Zastąp `WorkflowVersionMap` deklarację klasy następującą deklaracją.</span><span class="sxs-lookup"><span data-stu-id="a60d4-276">Replace the `WorkflowVersionMap` class declaration with the following declaration.</span></span>

    ```vb
    Public Module WorkflowVersionMap
        Dim map As Dictionary(Of WorkflowIdentity, Activity)

        ' Current version identities.
        Public StateMachineNumberGuessIdentity As WorkflowIdentity
        Public FlowchartNumberGuessIdentity As WorkflowIdentity
        Public SequentialNumberGuessIdentity As WorkflowIdentity

        Sub New()
            map = New Dictionary(Of WorkflowIdentity, Activity)

            ' Add the current workflow version identities.
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

    <span data-ttu-id="a60d4-277">`WorkflowVersionMap`zawiera trzy tożsamości przepływu pracy, które są mapowane na trzy definicje przepływu pracy z tego samouczka i są używane w poniższych sekcjach, gdy przepływy pracy są uruchamiane i wznawiane.</span><span class="sxs-lookup"><span data-stu-id="a60d4-277">`WorkflowVersionMap` contains three workflow identities that map to the three workflow definitions from this tutorial and is used in the following sections when workflows are started and resumed.</span></span>

## <a name="to-start-a-new-workflow"></a><span data-ttu-id="a60d4-278">Aby uruchomić nowy przepływ pracy</span><span class="sxs-lookup"><span data-stu-id="a60d4-278">To start a new workflow</span></span>

1. <span data-ttu-id="a60d4-279">Dodaj `Click` program obsługi dla `NewGame` .</span><span class="sxs-lookup"><span data-stu-id="a60d4-279">Add a `Click` handler for `NewGame`.</span></span> <span data-ttu-id="a60d4-280">Aby dodać procedurę obsługi, przełącz się do **widoku projektu** dla formularza i kliknij dwukrotnie `NewGame` .</span><span class="sxs-lookup"><span data-stu-id="a60d4-280">To add the handler, switch to **Design View** for the form, and double-click `NewGame`.</span></span> <span data-ttu-id="a60d4-281">`NewGame_Click`Dodano procedurę obsługi, a widok jest przełączany do widoku kodu formularza.</span><span class="sxs-lookup"><span data-stu-id="a60d4-281">A `NewGame_Click` handler is added and the view switches to code view for the form.</span></span> <span data-ttu-id="a60d4-282">Za każdym razem, gdy użytkownik kliknie ten przycisk, zostanie uruchomiony nowy przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="a60d4-282">Whenever the user clicks this button a new workflow is started.</span></span>

    ```vb
    Private Sub NewGame_Click(sender As Object, e As EventArgs) Handles NewGame.Click

    End Sub
    ```

    ```csharp
    private void NewGame_Click(object sender, EventArgs e)
    {

    }
    ```

2. <span data-ttu-id="a60d4-283">Dodaj następujący kod do programu obsługi kliknij.</span><span class="sxs-lookup"><span data-stu-id="a60d4-283">Add the following code to the click handler.</span></span> <span data-ttu-id="a60d4-284">Ten kod tworzy słownik argumentów wejściowych dla przepływu pracy, który jest poprzedzony przez nazwę argumentu.</span><span class="sxs-lookup"><span data-stu-id="a60d4-284">This code creates a dictionary of input arguments for the workflow, keyed by argument name.</span></span> <span data-ttu-id="a60d4-285">Ten słownik zawiera jeden wpis zawierający zakres losowo wygenerowanego numeru pobrany z pola kombi zakres.</span><span class="sxs-lookup"><span data-stu-id="a60d4-285">This dictionary has one entry that contains the range of the randomly generated number retrieved from the range combo box.</span></span>

    ```vb
    Dim inputs As New Dictionary(Of String, Object)()
    inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem))
    ```

    ```csharp
    var inputs = new Dictionary<string, object>();
    inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem));
    ```

3. <span data-ttu-id="a60d4-286">Następnie Dodaj następujący kod, który uruchamia przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="a60d4-286">Next, add the following code that starts the workflow.</span></span> <span data-ttu-id="a60d4-287">`WorkflowIdentity`Definicja przepływu pracy i odpowiadający typowi wybranego przepływu pracy są pobierane przy użyciu `WorkflowVersionMap` klasy pomocnika.</span><span class="sxs-lookup"><span data-stu-id="a60d4-287">The `WorkflowIdentity` and workflow definition corresponding to the type of workflow selected are retrieved using the `WorkflowVersionMap` helper class.</span></span> <span data-ttu-id="a60d4-288">Następnie nowe `WorkflowApplication` wystąpienie jest tworzone przy użyciu definicji przepływu pracy, `WorkflowIdentity` i słownika argumentów wejściowych.</span><span class="sxs-lookup"><span data-stu-id="a60d4-288">Next, a new `WorkflowApplication` instance is created using the workflow definition, `WorkflowIdentity`, and dictionary of input arguments.</span></span>

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

4. <span data-ttu-id="a60d4-289">Następnie Dodaj następujący kod, który dodaje przepływ pracy do listy przepływów pracy i wyświetla informacje o wersji przepływu pracy w formularzu.</span><span class="sxs-lookup"><span data-stu-id="a60d4-289">Next, add the following code which adds the workflow to the workflow list and displays the workflow's version information on the form.</span></span>

    ```vb
    ' Add the workflow to the list and display the version information.
    workflowStarting = True
    InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id)
    WorkflowVersion.Text = identity.ToString()
    workflowStarting = False
    ```

    ```csharp
    // Add the workflow to the list and display the version information.
    workflowStarting = true;
    InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id);
    WorkflowVersion.Text = identity.ToString();
    workflowStarting = false;
    ```

5. <span data-ttu-id="a60d4-290">Wywołaj, `ConfigureWorkflowApplication` Aby skonfigurować magazyn wystąpień, rozszerzenia i obsługę cyklu życia przepływu pracy dla tego `WorkflowApplication` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="a60d4-290">Call `ConfigureWorkflowApplication` to configure the instance store, extensions, and workflow lifecycle handlers for this `WorkflowApplication` instance.</span></span>

    ```vb
    ' Configure the instance store, extensions, and
    ' workflow lifecycle handlers.
    ConfigureWorkflowApplication(wfApp)
    ```

    ```csharp
    // Configure the instance store, extensions, and
    // workflow lifecycle handlers.
    ConfigureWorkflowApplication(wfApp);
    ```

6. <span data-ttu-id="a60d4-291">Na koniec Wywołaj metodę `Run` .</span><span class="sxs-lookup"><span data-stu-id="a60d4-291">Finally, call `Run`.</span></span>

    ```vb
    ' Start the workflow.
    wfApp.Run()
    ```

    ```csharp
    // Start the workflow.
    wfApp.Run();
    ```

     <span data-ttu-id="a60d4-292">Poniższy przykład to zakończono `NewGame_Click` procedurę obsługi.</span><span class="sxs-lookup"><span data-stu-id="a60d4-292">The following example is the completed `NewGame_Click` handler.</span></span>

    ```vb
    Private Sub NewGame_Click(sender As Object, e As EventArgs) Handles NewGame.Click
        ' Start a new workflow.
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

        ' Add the workflow to the list and display the version information.
        workflowStarting = True
        InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id)
        WorkflowVersion.Text = identity.ToString()
        workflowStarting = False

        ' Configure the instance store, extensions, and
        ' workflow lifecycle handlers.
        ConfigureWorkflowApplication(wfApp)

        ' Start the workflow.
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

        var wfApp = new WorkflowApplication(wf, inputs, identity);

        // Add the workflow to the list and display the version information.
        workflowStarting = true;
        InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id);
        WorkflowVersion.Text = identity.ToString();
        workflowStarting = false;

        // Configure the instance store, extensions, and
        // workflow lifecycle handlers.
        ConfigureWorkflowApplication(wfApp);

        // Start the workflow.
        wfApp.Run();
    }
    ```

## <a name="to-resume-a-workflow"></a><span data-ttu-id="a60d4-293">Aby wznowić przepływ pracy</span><span class="sxs-lookup"><span data-stu-id="a60d4-293">To resume a workflow</span></span>

1. <span data-ttu-id="a60d4-294">Dodaj `Click` program obsługi dla `EnterGuess` .</span><span class="sxs-lookup"><span data-stu-id="a60d4-294">Add a `Click` handler for `EnterGuess`.</span></span> <span data-ttu-id="a60d4-295">Aby dodać procedurę obsługi, przełącz się do **widoku projektu** dla formularza i kliknij dwukrotnie `EnterGuess` .</span><span class="sxs-lookup"><span data-stu-id="a60d4-295">To add the handler, switch to **Design View** for the form, and double-click `EnterGuess`.</span></span> <span data-ttu-id="a60d4-296">Za każdym razem, gdy użytkownik kliknie ten przycisk, przepływ pracy zostaje wznowiony.</span><span class="sxs-lookup"><span data-stu-id="a60d4-296">Whenever the user clicks this button a workflow is resumed.</span></span>

    ```vb
    Private Sub EnterGuess_Click(sender As Object, e As EventArgs) Handles EnterGuess.Click

    End Sub
    ```

    ```csharp
    private void EnterGuess_Click(object sender, EventArgs e)
    {

    }
    ```

2. <span data-ttu-id="a60d4-297">Dodaj następujący kod, aby upewnić się, że przepływ pracy został wybrany na liście przepływów pracy i czy jego wartość jest prawidłowa.</span><span class="sxs-lookup"><span data-stu-id="a60d4-297">Add the following code to ensure that a workflow is selected in the workflow list, and that the user's guess is valid.</span></span>

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

3. <span data-ttu-id="a60d4-298">Następnie Pobierz `WorkflowApplicationInstance` wystąpienie utrwalonego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="a60d4-298">Next, retrieve the `WorkflowApplicationInstance` of the persisted workflow instance.</span></span> <span data-ttu-id="a60d4-299">`WorkflowApplicationInstance`Reprezentuje wystąpienie utrwalonego przepływu pracy, które nie zostało jeszcze skojarzone z definicją przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="a60d4-299">A `WorkflowApplicationInstance` represents a persisted workflow instance that has not yet been associated with a workflow definition.</span></span> <span data-ttu-id="a60d4-300">Z `DefinitionIdentity` `WorkflowApplicationInstance` zawiera `WorkflowIdentity` wystąpienia utrwalonego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="a60d4-300">The `DefinitionIdentity` of the `WorkflowApplicationInstance` contains the `WorkflowIdentity` of the persisted workflow instance.</span></span> <span data-ttu-id="a60d4-301">W tym samouczku `WorkflowVersionMap` Klasa narzędzi służy do mapowania `WorkflowIdentity` do odpowiedniej definicji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="a60d4-301">In this tutorial, the `WorkflowVersionMap` utility class is used to map the `WorkflowIdentity` to the correct workflow definition.</span></span> <span data-ttu-id="a60d4-302">Po pobraniu definicji przepływu pracy jest ona `WorkflowApplication` tworzona przy użyciu prawidłowej definicji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="a60d4-302">Once the workflow definition is retrieved, a `WorkflowApplication` is created, using the correct workflow definition.</span></span>

    ```vb
    Dim instance As WorkflowApplicationInstance = _
        WorkflowApplication.GetInstance(WorkflowInstanceId, store)

    ' Use the persisted WorkflowIdentity to retrieve the correct workflow
    ' definition from the dictionary.
    Dim wf As Activity = _
        WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity)

    ' Associate the WorkflowApplication with the correct definition
    Dim wfApp As New WorkflowApplication(wf, instance.DefinitionIdentity)
    ```

    ```csharp
    WorkflowApplicationInstance instance =
        WorkflowApplication.GetInstance(WorkflowInstanceId, store);

    // Use the persisted WorkflowIdentity to retrieve the correct workflow
    // definition from the dictionary.
    Activity wf =
        WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity);

    // Associate the WorkflowApplication with the correct definition
    var wfApp = new WorkflowApplication(wf, instance.DefinitionIdentity);
    ```

4. <span data-ttu-id="a60d4-303">Po `WorkflowApplication` utworzeniu należy skonfigurować magazyn wystąpień, programy obsługi cyklu życia przepływu pracy i rozszerzenia przez wywołanie `ConfigureWorkflowApplication` .</span><span class="sxs-lookup"><span data-stu-id="a60d4-303">Once the `WorkflowApplication` is created, configure the instance store, workflow lifecycle handlers, and extensions by calling `ConfigureWorkflowApplication`.</span></span> <span data-ttu-id="a60d4-304">Te kroki należy wykonać za każdym razem, gdy `WorkflowApplication` tworzony jest nowy, i muszą one zostać wykonane przed załadowaniem wystąpienia przepływu pracy do `WorkflowApplication` .</span><span class="sxs-lookup"><span data-stu-id="a60d4-304">These steps must be done every time a new `WorkflowApplication` is created, and they must be done before the workflow instance is loaded into the `WorkflowApplication`.</span></span> <span data-ttu-id="a60d4-305">Po załadowaniu przepływu pracy zostanie on wznowiony z przypuszczeniem użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a60d4-305">After the workflow is loaded, it is resumed with the user's guess.</span></span>

    ```vb
    ' Configure the extensions and lifecycle handlers.
    ' Do this before the instance is loaded. Once the instance is
    ' loaded it is too late to add extensions.
    ConfigureWorkflowApplication(wfApp)

    ' Load the workflow.
    wfApp.Load(instance)

    ' Resume the workflow.
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

5. <span data-ttu-id="a60d4-306">Na koniec wyczyść pole tekstowe odgadnięcie i Przygotuj formularz do zaakceptowania innego argumentu.</span><span class="sxs-lookup"><span data-stu-id="a60d4-306">Finally, clear the guess textbox and prepare the form to accept another guess.</span></span>

    ```vb
    ' Clear the Guess textbox.
    Guess.Clear()
    Guess.Focus()
    ```

    ```csharp
    // Clear the Guess textbox.
    Guess.Clear();
    Guess.Focus();
    ```

    <span data-ttu-id="a60d4-307">Poniższy przykład to zakończono `EnterGuess_Click` procedurę obsługi.</span><span class="sxs-lookup"><span data-stu-id="a60d4-307">The following example is the completed `EnterGuess_Click` handler.</span></span>

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

        ' Use the persisted WorkflowIdentity to retrieve the correct workflow
        ' definition from the dictionary.
        Dim wf As Activity = _
            WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity)

        ' Associate the WorkflowApplication with the correct definition
        Dim wfApp As New WorkflowApplication(wf, instance.DefinitionIdentity)

        ' Configure the extensions and lifecycle handlers.
        ' Do this before the instance is loaded. Once the instance is
        ' loaded it is too late to add extensions.
        ConfigureWorkflowApplication(wfApp)

        ' Load the workflow.
        wfApp.Load(instance)

        ' Resume the workflow.
        wfApp.ResumeBookmark("EnterGuess", userGuess)

        ' Clear the Guess textbox.
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
        var wfApp = new WorkflowApplication(wf, instance.DefinitionIdentity);

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

## <a name="to-terminate-a-workflow"></a><span data-ttu-id="a60d4-308">Aby zakończyć przepływ pracy</span><span class="sxs-lookup"><span data-stu-id="a60d4-308">To terminate a workflow</span></span>

1. <span data-ttu-id="a60d4-309">Dodaj `Click` program obsługi dla `QuitGame` .</span><span class="sxs-lookup"><span data-stu-id="a60d4-309">Add a `Click` handler for `QuitGame`.</span></span> <span data-ttu-id="a60d4-310">Aby dodać procedurę obsługi, przełącz się do **widoku projektu** dla formularza i kliknij dwukrotnie `QuitGame` .</span><span class="sxs-lookup"><span data-stu-id="a60d4-310">To add the handler, switch to **Design View** for the form, and double-click `QuitGame`.</span></span> <span data-ttu-id="a60d4-311">Za każdym razem, gdy użytkownik kliknie ten przycisk, aktualnie wybrany przepływ pracy zostanie zakończony.</span><span class="sxs-lookup"><span data-stu-id="a60d4-311">Whenever the user clicks this button the currently selected workflow is terminated.</span></span>

    ```vb
    Private Sub QuitGame_Click(sender As Object, e As EventArgs) Handles QuitGame.Click

    End Sub
    ```

    ```csharp
    private void QuitGame_Click(object sender, EventArgs e)
    {

    }
    ```

2. <span data-ttu-id="a60d4-312">Dodaj następujący kod do `QuitGame_Click` procedury obsługi.</span><span class="sxs-lookup"><span data-stu-id="a60d4-312">Add the following code to the `QuitGame_Click` handler.</span></span> <span data-ttu-id="a60d4-313">Ten kod najpierw sprawdza, czy przepływ pracy został wybrany na liście przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="a60d4-313">This code first checks to ensure that a workflow is selected in the workflow list.</span></span> <span data-ttu-id="a60d4-314">Następnie ładuje wystąpienie utrwalone do `WorkflowApplicationInstance` , używa `DefinitionIdentity` do określenia prawidłowej definicji przepływu pracy, a następnie inicjuje `WorkflowApplication` .</span><span class="sxs-lookup"><span data-stu-id="a60d4-314">Then it loads the persisted instance into a `WorkflowApplicationInstance`, uses the `DefinitionIdentity` to determine the correct workflow definition, and then initializes the `WorkflowApplication`.</span></span> <span data-ttu-id="a60d4-315">Kolejne rozszerzenia i programy obsługi cyklu życia przepływu pracy są skonfigurowane z wywołaniem do `ConfigureWorkflowApplication` .</span><span class="sxs-lookup"><span data-stu-id="a60d4-315">Next the extensions and workflow lifecycle handlers are configured with a call to `ConfigureWorkflowApplication`.</span></span> <span data-ttu-id="a60d4-316">Po `WorkflowApplication` skonfigurowaniu jest on ładowany, a następnie `Terminate` wywoływany.</span><span class="sxs-lookup"><span data-stu-id="a60d4-316">Once the `WorkflowApplication` is configured, it is loaded, and then `Terminate` is called.</span></span>

    ```vb
    If WorkflowInstanceId = Guid.Empty Then
        MessageBox.Show("Please select a workflow.")
        Return
    End If

    Dim instance As WorkflowApplicationInstance = _
        WorkflowApplication.GetInstance(WorkflowInstanceId, store)

    ' Use the persisted WorkflowIdentity to retrieve the correct workflow
    ' definition from the dictionary.
    Dim wf As Activity = WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity)

    ' Associate the WorkflowApplication with the correct definition.
    Dim wfApp As New WorkflowApplication(wf, instance.DefinitionIdentity)

    ' Configure the extensions and lifecycle handlers.
    ConfigureWorkflowApplication(wfApp)

    ' Load the workflow.
    wfApp.Load(instance)

    ' Terminate the workflow.
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
    var wfApp = new WorkflowApplication(wf, instance.DefinitionIdentity);

    // Configure the extensions and lifecycle handlers
    ConfigureWorkflowApplication(wfApp);

    // Load the workflow.
    wfApp.Load(instance);

    // Terminate the workflow.
    wfApp.Terminate("User resigns.");
    ```

## <a name="to-build-and-run-the-application"></a><span data-ttu-id="a60d4-317">Aby skompilować i uruchomić aplikację</span><span class="sxs-lookup"><span data-stu-id="a60d4-317">To build and run the application</span></span>

1. <span data-ttu-id="a60d4-318">Kliknij dwukrotnie pozycję **program.cs** (lub **Module1. vb**) w **Eksplorator rozwiązań** , aby wyświetlić kod.</span><span class="sxs-lookup"><span data-stu-id="a60d4-318">Double-click **Program.cs** (or **Module1.vb**) in **Solution Explorer** to display the code.</span></span>

2. <span data-ttu-id="a60d4-319">Dodaj następującą `using` instrukcję (lub `Imports` ) w górnej części pliku z innymi `using` instrukcjami (lub `Imports` ).</span><span class="sxs-lookup"><span data-stu-id="a60d4-319">Add the following `using` (or `Imports`) statement at the top of the file with the other `using` (or `Imports`) statements.</span></span>

    ```vb
    Imports System.Windows.Forms
    ```

    ```csharp
    using System.Windows.Forms;
    ```

3. <span data-ttu-id="a60d4-320">Usuń lub Skomentuj istniejący kod hostingu przepływu pracy, korzystając z procedury [: uruchamianie przepływu pracy](how-to-run-a-workflow.md)i zastąp go następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="a60d4-320">Remove or comment out the existing workflow hosting code from [How to: Run a Workflow](how-to-run-a-workflow.md), and replace it with the following code.</span></span>

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

4. <span data-ttu-id="a60d4-321">Kliknij prawym przyciskiem myszy pozycję **NumberGuessWorkflowHost** w **Eksplorator rozwiązań** i wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="a60d4-321">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Properties**.</span></span> <span data-ttu-id="a60d4-322">Na karcie **aplikacja** Określ **aplikację systemu Windows** dla **typu danych wyjściowych**.</span><span class="sxs-lookup"><span data-stu-id="a60d4-322">In the **Application** tab, specify **Windows Application** for the **Output type**.</span></span> <span data-ttu-id="a60d4-323">Ten krok jest opcjonalny, ale jeśli nie jest zastosowana, okno konsoli jest wyświetlane oprócz formularza.</span><span class="sxs-lookup"><span data-stu-id="a60d4-323">This step is optional, but if it is not followed the console window is displayed in addition to the form.</span></span>

5. <span data-ttu-id="a60d4-324">Naciśnij klawisze CTRL + SHIFT + B, aby skompilować aplikację.</span><span class="sxs-lookup"><span data-stu-id="a60d4-324">Press Ctrl+Shift+B to build the application.</span></span>

6. <span data-ttu-id="a60d4-325">Upewnij się, że **NumberGuessWorkflowHost** jest ustawiony jako aplikacja startowa, a następnie naciśnij klawisze CTRL + F5, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="a60d4-325">Ensure that **NumberGuessWorkflowHost** is set as the startup application, and press Ctrl+F5 to start the application.</span></span>

7. <span data-ttu-id="a60d4-326">Wybierz zakres dla gry do odgadnięcia i typ przepływu pracy do uruchomienia, a następnie kliknij pozycję **Nowa gra**.</span><span class="sxs-lookup"><span data-stu-id="a60d4-326">Select a range for the guessing game and the type of workflow to start, and click **New Game**.</span></span> <span data-ttu-id="a60d4-327">Wprowadź wartość w polu **zgadywanie** i kliknij pozycję **Przejdź** , aby przesłać przypuszczenie.</span><span class="sxs-lookup"><span data-stu-id="a60d4-327">Enter a guess in the **Guess** box and click **Go** to submit your guess.</span></span> <span data-ttu-id="a60d4-328">Należy zauważyć, że dane wyjściowe `WriteLine` działań są wyświetlane w formularzu.</span><span class="sxs-lookup"><span data-stu-id="a60d4-328">Note that the output from the `WriteLine` activities is displayed on the form.</span></span>

8. <span data-ttu-id="a60d4-329">Rozpocznij pracę z kilkoma przepływami pracy przy użyciu różnych typów i zakresów liczbowych, wprowadź liczbę prób i przełączaj się między przepływami pracy, wybierając z listy **Identyfikator wystąpienia przepływu pracy** .</span><span class="sxs-lookup"><span data-stu-id="a60d4-329">Start several workflows using different workflow types and number ranges, enter some guesses, and switch between the workflows by selecting from the **Workflow Instance Id** list.</span></span>

    <span data-ttu-id="a60d4-330">Należy pamiętać, że po przełączeniu do nowego przepływu pracy poprzednie wartości i postęp przepływu pracy nie są wyświetlane w oknie stanu.</span><span class="sxs-lookup"><span data-stu-id="a60d4-330">Note that when you switch to a new workflow, the previous guesses and progress of the workflow are not displayed in the status window.</span></span> <span data-ttu-id="a60d4-331">Przyczyna stanu jest niedostępna, ponieważ nie jest ona przechwycona i zapisana w dowolnym miejscu.</span><span class="sxs-lookup"><span data-stu-id="a60d4-331">The reason the status is not available is because it is not captured and saved anywhere.</span></span> <span data-ttu-id="a60d4-332">W następnym kroku samouczka [: Tworzenie niestandardowego uczestnika śledzenia](how-to-create-a-custom-tracking-participant.md), tworzysz niestandardowego uczestnika śledzenia, który zapisuje te informacje.</span><span class="sxs-lookup"><span data-stu-id="a60d4-332">In the next step of the tutorial, [How to: Create a Custom Tracking Participant](how-to-create-a-custom-tracking-participant.md), you create a custom tracking participant that saves this information.</span></span>
