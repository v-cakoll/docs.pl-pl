---
title: 'Wskazówki: tworzenie aplikacji rozszerzalnej'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- views [.NET Framework], add-in pipeline
- host-side adapters for add-ins [.NET Framework]
- add-in pipeline [.NET Framework], creating
- add-in-side adapter [.NET Framework]
- contracts for add-in pipelines [.NET Framework]
ms.assetid: 694a33c5-a040-450d-aed5-ac49fc88ce61
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5d2aaeaffaf3abbe1e8efcdb57d40e6ae60f89b5
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43552338"
---
# <a name="walkthrough-creating-an-extensible-application"></a><span data-ttu-id="745a6-102">Wskazówki: tworzenie aplikacji rozszerzalnej</span><span class="sxs-lookup"><span data-stu-id="745a6-102">Walkthrough: Creating an Extensible Application</span></span>
<span data-ttu-id="745a6-103">W tym przewodniku opisano tworzenie potoku dodatku, który wykonuje funkcje prosty kalkulator.</span><span class="sxs-lookup"><span data-stu-id="745a6-103">This walkthrough describes how to create a pipeline for an add-in that performs simple calculator functions.</span></span> <span data-ttu-id="745a6-104">Nie przedstawiono tu rzeczywistych scenariuszy; zamiast pokazuje podstawową funkcjonalność potoku i jak dodatek mogą udostępniać usługi hosta.</span><span class="sxs-lookup"><span data-stu-id="745a6-104">It does not demonstrate a real-world scenario; rather, it demonstrates the basic functionality of a pipeline and how an add-in can provide services for a host.</span></span>  
  
 <span data-ttu-id="745a6-105">W tym przewodniku opisano następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="745a6-105">This walkthrough describes the following tasks:</span></span>  
  
-   <span data-ttu-id="745a6-106">Tworzenie rozwiązania programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="745a6-106">Creating a Visual Studio solution.</span></span>  
  
-   <span data-ttu-id="745a6-107">Tworzenie struktury katalogów potoku.</span><span class="sxs-lookup"><span data-stu-id="745a6-107">Creating the pipeline directory structure.</span></span>  
  
-   <span data-ttu-id="745a6-108">Tworzenie kontraktu i widoków.</span><span class="sxs-lookup"><span data-stu-id="745a6-108">Creating the contract and views.</span></span>  
  
-   <span data-ttu-id="745a6-109">Tworzenie adaptera add w side.</span><span class="sxs-lookup"><span data-stu-id="745a6-109">Creating the add-in-side adapter.</span></span>  
  
-   <span data-ttu-id="745a6-110">Tworzenie karty po stronie hosta.</span><span class="sxs-lookup"><span data-stu-id="745a6-110">Creating the host-side adapter.</span></span>  
  
-   <span data-ttu-id="745a6-111">Tworzenie hosta.</span><span class="sxs-lookup"><span data-stu-id="745a6-111">Creating the host.</span></span>  
  
-   <span data-ttu-id="745a6-112">Tworzenie dodatku.</span><span class="sxs-lookup"><span data-stu-id="745a6-112">Creating the add-in.</span></span>  
  
-   <span data-ttu-id="745a6-113">Wdrażanie potoku.</span><span class="sxs-lookup"><span data-stu-id="745a6-113">Deploying the pipeline.</span></span>  
  
-   <span data-ttu-id="745a6-114">Uruchamianie aplikacji hosta.</span><span class="sxs-lookup"><span data-stu-id="745a6-114">Running the host application.</span></span>  
  
 <span data-ttu-id="745a6-115">Ten potok przekazuje tylko typów możliwych do serializacji (<xref:System.Double> i <xref:System.String>), między hostem a dodatkiem.</span><span class="sxs-lookup"><span data-stu-id="745a6-115">This pipeline passes only serializable types (<xref:System.Double> and <xref:System.String>), between the host and the add-in.</span></span> <span data-ttu-id="745a6-116">Aby uzyskać przykład pokazujący sposób przekazywania kolekcji typów złożonych danych, zobacz [wskazówki: przekazywanie kolekcji między hostami i Add-Ins](https://msdn.microsoft.com/library/b532c604-548e-4fab-b11c-377257dd0ee5).</span><span class="sxs-lookup"><span data-stu-id="745a6-116">For an example that shows how to pass collections of complex data types, see [Walkthrough: Passing Collections Between Hosts and Add-Ins](https://msdn.microsoft.com/library/b532c604-548e-4fab-b11c-377257dd0ee5).</span></span>  
  
 <span data-ttu-id="745a6-117">Kontrakt dla tego potoku definiuje model obiektu cztery operacje arytmetyczne: dodawania, odejmowania, mnożenia i dzielenia.</span><span class="sxs-lookup"><span data-stu-id="745a6-117">The contract for this pipeline defines an object model of four arithmetic operations: add, subtract, multiply, and divide.</span></span> <span data-ttu-id="745a6-118">Host zapewnia dodatek równania, aby obliczyć, takie jak 2 + 2, i dodatku zwraca wynik do hosta.</span><span class="sxs-lookup"><span data-stu-id="745a6-118">The host provides the add-in with an equation to calculate, such as 2 + 2, and the add-in returns the result to the host.</span></span>  
  
 <span data-ttu-id="745a6-119">W wersji 2 dodatku Kalkulator zapewnia możliwości bardziej obliczania i przedstawia przechowywanie wersji.</span><span class="sxs-lookup"><span data-stu-id="745a6-119">Version 2 of the calculator add-in provides more calculating possibilities and demonstrates versioning.</span></span> <span data-ttu-id="745a6-120">Jest on opisany w [przewodnik: Włączanie zgodności z poprzednimi wersjami Your zmian hosta](https://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848).</span><span class="sxs-lookup"><span data-stu-id="745a6-120">It is described in [Walkthrough: Enabling Backward Compatibility as Your Host Changes](https://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="745a6-121">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="745a6-121">Prerequisites</span></span>  
 <span data-ttu-id="745a6-122">Potrzebne są następujące czynności w celu przeprowadzenia tego instruktażu:</span><span class="sxs-lookup"><span data-stu-id="745a6-122">You need the following to complete this walkthrough:</span></span>  
  
-   <span data-ttu-id="745a6-123">Program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="745a6-123">Visual Studio.</span></span>  
  
## <a name="creating-a-visual-studio-solution"></a><span data-ttu-id="745a6-124">Tworzenie rozwiązań programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="745a6-124">Creating a Visual Studio Solution</span></span>  
 <span data-ttu-id="745a6-125">Zawiera projekty segmentów potoku przy użyciu rozwiązania w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="745a6-125">Use a solution in Visual Studio to contain the projects of your pipeline segments.</span></span>  
  
#### <a name="to-create-the-pipeline-solution"></a><span data-ttu-id="745a6-126">Aby utworzyć rozwiązanie potoku</span><span class="sxs-lookup"><span data-stu-id="745a6-126">To create the pipeline solution</span></span>  
  
1.  <span data-ttu-id="745a6-127">W programie Visual Studio Utwórz nowy projekt o nazwie `Calc1Contract`.</span><span class="sxs-lookup"><span data-stu-id="745a6-127">In Visual Studio, create a new project named `Calc1Contract`.</span></span> <span data-ttu-id="745a6-128">Oparte na **biblioteki klas** szablonu.</span><span class="sxs-lookup"><span data-stu-id="745a6-128">Base it on the **Class Library** template.</span></span>  
  
2.  <span data-ttu-id="745a6-129">Nazwij rozwiązanie `CalculatorV1`.</span><span class="sxs-lookup"><span data-stu-id="745a6-129">Name the solution `CalculatorV1`.</span></span>  
  
## <a name="creating-the-pipeline-directory-structure"></a><span data-ttu-id="745a6-130">Tworzenie struktury katalogów potoku</span><span class="sxs-lookup"><span data-stu-id="745a6-130">Creating the Pipeline Directory Structure</span></span>  
 <span data-ttu-id="745a6-131">Model dodatku wymaga zestawy segmentów potoku do umieszczenia w strukturze określonego katalogu.</span><span class="sxs-lookup"><span data-stu-id="745a6-131">The add-in model requires the pipeline segment assemblies to be placed in a specified directory structure.</span></span> <span data-ttu-id="745a6-132">Aby uzyskać więcej informacji na temat struktury potoku, zobacz [wymagania dotyczące opracowywania potoku](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span><span class="sxs-lookup"><span data-stu-id="745a6-132">For more information about the pipeline structure, see [Pipeline Development Requirements](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span></span>  
  
#### <a name="to-create-the-pipeline-directory-structure"></a><span data-ttu-id="745a6-133">Aby utworzyć potok struktury katalogów</span><span class="sxs-lookup"><span data-stu-id="745a6-133">To create the pipeline directory structure</span></span>  
  
1.  <span data-ttu-id="745a6-134">Utwórz folder aplikacji w dowolnym miejscu na komputerze.</span><span class="sxs-lookup"><span data-stu-id="745a6-134">Create an application folder anywhere on your computer.</span></span>  
  
2.  <span data-ttu-id="745a6-135">W tym folderze utwórz następującą strukturę:</span><span class="sxs-lookup"><span data-stu-id="745a6-135">In that folder, create the following structure:</span></span>  
  
    ```  
    Pipeline  
      AddIns  
        CalcV1  
        CalcV2  
      AddInSideAdapters  
      AddInViews  
      Contracts  
      HostSideAdapters  
    ```  
  
     <span data-ttu-id="745a6-136">Nie jest konieczne umieścić potoku strukturę folderów w folderze aplikacji; jest wykonywane tutaj wyłącznie dla wygody.</span><span class="sxs-lookup"><span data-stu-id="745a6-136">It is not necessary to put the pipeline folder structure in your application folder; it is done here only for convenience.</span></span> <span data-ttu-id="745a6-137">Na etapie odpowiednie przewodnik wyjaśnia, jak zmiany kodu, jeśli struktura folderów potoku znajduje się w innej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="745a6-137">At the appropriate step, the walkthrough explains how to change the code if the pipeline folder structure is in a different location.</span></span> <span data-ttu-id="745a6-138">Zobacz Omówienie wymagań katalogu potoku w [wymagania dotyczące opracowywania potoku](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span><span class="sxs-lookup"><span data-stu-id="745a6-138">See the discussion of pipeline directory requirements in [Pipeline Development Requirements](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="745a6-139">`CalcV2` Folder nie jest używany w tym przewodniku; jest symbolem zastępczym dla [przewodnik: Włączanie zgodności z poprzednimi wersjami Your zmian hosta](https://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848).</span><span class="sxs-lookup"><span data-stu-id="745a6-139">The `CalcV2` folder is not used in this walkthrough; it is a placeholder for [Walkthrough: Enabling Backward Compatibility as Your Host Changes](https://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848).</span></span>  
  
## <a name="creating-the-contract-and-views"></a><span data-ttu-id="745a6-140">Tworzenie kontraktu i widoków</span><span class="sxs-lookup"><span data-stu-id="745a6-140">Creating the Contract and Views</span></span>  
 <span data-ttu-id="745a6-141">Określa segment umowy, dla tego potoku `ICalc1Contract` interfejs, który definiuje cztery metody: `add`, `subtract`, `multiply`, i `divide`.</span><span class="sxs-lookup"><span data-stu-id="745a6-141">The contract segment for this pipeline defines the `ICalc1Contract` interface, which defines four methods: `add`, `subtract`, `multiply`, and `divide`.</span></span>  
  
#### <a name="to-create-the-contract"></a><span data-ttu-id="745a6-142">Aby utworzyć kontrakt</span><span class="sxs-lookup"><span data-stu-id="745a6-142">To create the contract</span></span>  
  
1.  <span data-ttu-id="745a6-143">W rozwiązaniu Visual Studio o nazwie `CalculatorV1`, otwórz `Calc1Contract` projektu.</span><span class="sxs-lookup"><span data-stu-id="745a6-143">In the Visual Studio solution named `CalculatorV1`, open the `Calc1Contract` project.</span></span>  
  
2.  <span data-ttu-id="745a6-144">W **Eksploratora rozwiązań**, dodaj odwołania do następujących zestawów, które mają `Calc1Contract` projektu:</span><span class="sxs-lookup"><span data-stu-id="745a6-144">In **Solution Explorer**, add references to the following assemblies to the `Calc1Contract` project:</span></span>  
  
     <span data-ttu-id="745a6-145">System.AddIn.Contract.dll</span><span class="sxs-lookup"><span data-stu-id="745a6-145">System.AddIn.Contract.dll</span></span>  
  
     <span data-ttu-id="745a6-146">System.AddIn.dll</span><span class="sxs-lookup"><span data-stu-id="745a6-146">System.AddIn.dll</span></span>  
  
3.  <span data-ttu-id="745a6-147">W **Eksploratora rozwiązań**, Wyklucz domyślnej klasy, który jest dodawany do nowego **biblioteki klas** projektów.</span><span class="sxs-lookup"><span data-stu-id="745a6-147">In **Solution Explorer**, exclude the default class that is added to new **Class Library** projects.</span></span>  
  
4.  <span data-ttu-id="745a6-148">W **Eksploratora rozwiązań**, Dodaj nowy element do projektu, przy użyciu **interfejsu** szablonu.</span><span class="sxs-lookup"><span data-stu-id="745a6-148">In **Solution Explorer**, add a new item to the project, using the **Interface** template.</span></span> <span data-ttu-id="745a6-149">W **Dodaj nowy element** okno dialogowe, nazwa interfejsu `ICalc1Contract`.</span><span class="sxs-lookup"><span data-stu-id="745a6-149">In the **Add New Item** dialog box, name the interface `ICalc1Contract`.</span></span>  
  
5.  <span data-ttu-id="745a6-150">W pliku interfejsu, należy dodać odwołania do przestrzeni nazw do <xref:System.AddIn.Contract> i <xref:System.AddIn.Pipeline>.</span><span class="sxs-lookup"><span data-stu-id="745a6-150">In the interface file, add namespace references to <xref:System.AddIn.Contract> and <xref:System.AddIn.Pipeline>.</span></span>  
  
6.  <span data-ttu-id="745a6-151">Użyj poniższego kodu, aby ukończyć ten segment kontraktu.</span><span class="sxs-lookup"><span data-stu-id="745a6-151">Use the following code to complete this contract segment.</span></span> <span data-ttu-id="745a6-152">Należy zauważyć, że ten interfejs musi mieć <xref:System.AddIn.Pipeline.AddInContractAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="745a6-152">Note that this interface must have the <xref:System.AddIn.Pipeline.AddInContractAttribute> attribute.</span></span>  
  
     [!code-csharp[AddInP1Contract#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1Contract/cs/ICalc1Contract.cs#1)]
     [!code-vb[AddInP1Contract#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1Contract/vb/ICalc1Contract.vb#1)]  
  
7.  <span data-ttu-id="745a6-153">Opcjonalnie można tworzyć rozwiązania programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="745a6-153">Optionally, build the Visual Studio solution.</span></span> <span data-ttu-id="745a6-154">Rozwiązania nie można uruchomić, dopóki ostatecznej procedurze, ale wbudowanie jej po każdej procedury gwarantuje, że każdy projekt jest rozwiązać.</span><span class="sxs-lookup"><span data-stu-id="745a6-154">The solution cannot be run until the final procedure, but building it after each procedure ensures that each project is correct.</span></span>  
  
 <span data-ttu-id="745a6-155">Widok dodatku i host widoku dodatku zazwyczaj mają ten sam kod, szczególnie w pierwszej wersji dodatku, można łatwo utworzyć widoków, w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="745a6-155">Because the add-in view and the host view of the add-in usually have the same code, especially in the first version of an add-in, you can easily create the views at the same time.</span></span> <span data-ttu-id="745a6-156">Różnią się tylko jeden składnik: widok dodatek wymaga <xref:System.AddIn.Pipeline.AddInBaseAttribute> atrybutu, natomiast widok hosta dodatków nie wymaga żadnych atrybutów.</span><span class="sxs-lookup"><span data-stu-id="745a6-156">They differ by only one factor: the add-in view requires the <xref:System.AddIn.Pipeline.AddInBaseAttribute> attribute, while the host view of the add-in does not require any attributes.</span></span>  
  
#### <a name="to-create-the-add-in-view"></a><span data-ttu-id="745a6-157">Aby utworzyć widok dodatku</span><span class="sxs-lookup"><span data-stu-id="745a6-157">To create the add-in view</span></span>  
  
1.  <span data-ttu-id="745a6-158">Dodaj nowy projekt o nazwie `Calc1AddInView` do `CalculatorV1` rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="745a6-158">Add a new project named `Calc1AddInView` to the `CalculatorV1` solution.</span></span> <span data-ttu-id="745a6-159">Oparte na **biblioteki klas** szablonu.</span><span class="sxs-lookup"><span data-stu-id="745a6-159">Base it on the **Class Library** template.</span></span>  
  
2.  <span data-ttu-id="745a6-160">W **Eksploratora rozwiązań**, Dodaj odwołanie do System.AddIn.dll do `Calc1AddInView` projektu.</span><span class="sxs-lookup"><span data-stu-id="745a6-160">In **Solution Explorer**, add a reference to System.AddIn.dll to the `Calc1AddInView` project.</span></span>  
  
3.  <span data-ttu-id="745a6-161">W **Eksploratora rozwiązań**, Wyklucz domyślnej klasy, który jest dodawany do nowego **biblioteki klas** projektów i Dodaj nowy element do projektu, przy użyciu **interfejsu** szablonu.</span><span class="sxs-lookup"><span data-stu-id="745a6-161">In **Solution Explorer**, exclude the default class that is added to new **Class Library** projects, and add a new item to the project, using the **Interface** template.</span></span> <span data-ttu-id="745a6-162">W **Dodaj nowy element** okno dialogowe, nazwa interfejsu `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="745a6-162">In the **Add New Item** dialog box, name the interface `ICalculator`.</span></span>  
  
4.  <span data-ttu-id="745a6-163">W pliku interfejsu, Dodaj odwołanie do przestrzeni nazw <xref:System.AddIn.Pipeline>.</span><span class="sxs-lookup"><span data-stu-id="745a6-163">In the interface file, add a namespace reference to <xref:System.AddIn.Pipeline>.</span></span>  
  
5.  <span data-ttu-id="745a6-164">Użyj poniższego kodu, aby ukończyć ten widok dodatku.</span><span class="sxs-lookup"><span data-stu-id="745a6-164">Use the following code to complete this add-in view.</span></span> <span data-ttu-id="745a6-165">Należy zauważyć, że ten interfejs musi mieć <xref:System.AddIn.Pipeline.AddInBaseAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="745a6-165">Note that this interface must have the <xref:System.AddIn.Pipeline.AddInBaseAttribute> attribute.</span></span>  
  
     [!code-csharp[AddInP1AddInViews#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInViews/cs/Calc1AddInView.cs#1)]
     [!code-vb[AddInP1AddInViews#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInViews/vb/Calc1AddInView.vb#1)]  
  
6.  <span data-ttu-id="745a6-166">Opcjonalnie można tworzyć rozwiązania programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="745a6-166">Optionally, build the Visual Studio solution.</span></span>  
  
#### <a name="to-create-the-host-view-of-the-add-in"></a><span data-ttu-id="745a6-167">Aby utworzyć widok hosta dodatków</span><span class="sxs-lookup"><span data-stu-id="745a6-167">To create the host view of the add-in</span></span>  
  
1.  <span data-ttu-id="745a6-168">Dodaj nowy projekt o nazwie `Calc1HVA` do `CalculatorV1` rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="745a6-168">Add a new project named `Calc1HVA` to the `CalculatorV1` solution.</span></span> <span data-ttu-id="745a6-169">Oparte na **biblioteki klas** szablonu.</span><span class="sxs-lookup"><span data-stu-id="745a6-169">Base it on the **Class Library** template.</span></span>  
  
2.  <span data-ttu-id="745a6-170">W **Eksploratora rozwiązań**, Wyklucz domyślnej klasy, który jest dodawany do nowego **biblioteki klas** projektów i Dodaj nowy element do projektu, przy użyciu **interfejsu** szablonu.</span><span class="sxs-lookup"><span data-stu-id="745a6-170">In **Solution Explorer**, exclude the default class that is added to new **Class Library** projects, and add a new item to the project, using the **Interface** template.</span></span> <span data-ttu-id="745a6-171">W **Dodaj nowy element** okno dialogowe, nazwa interfejsu `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="745a6-171">In the **Add New Item** dialog box, name the interface `ICalculator`.</span></span>  
  
3.  <span data-ttu-id="745a6-172">W pliku interfejsu użyj następującego kodu, aby ukończyć widok hosta dodatków.</span><span class="sxs-lookup"><span data-stu-id="745a6-172">In the interface file, use the following code to complete the host view of the add-in.</span></span>  
  
     [!code-csharp[AddInP1HVA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1HVA/cs/calc1hva.cs#1)]
     [!code-vb[AddInP1HVA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1HVA/vb/Calc1HVA.vb#1)]  
  
4.  <span data-ttu-id="745a6-173">Opcjonalnie można tworzyć rozwiązania programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="745a6-173">Optionally, build the Visual Studio solution.</span></span>  
  
## <a name="creating-the-add-in-side-adapter"></a><span data-ttu-id="745a6-174">Tworzenie adaptera dodać strony</span><span class="sxs-lookup"><span data-stu-id="745a6-174">Creating the Add-in-side Adapter</span></span>  
 <span data-ttu-id="745a6-175">Ta karta Dodaj stronie składa się z jednej karty kontraktu na widok.</span><span class="sxs-lookup"><span data-stu-id="745a6-175">This add-in-side adapter consists of one view-to-contract adapter.</span></span> <span data-ttu-id="745a6-176">Ten segment potoku konwertuje typy w widoku Dodaj umowy.</span><span class="sxs-lookup"><span data-stu-id="745a6-176">This pipeline segment converts the types from the add-in view to the contract.</span></span>  
  
 <span data-ttu-id="745a6-177">W tym potoku dodatku udostępnia usługę na hoście, a typy przepływu z dodatku na hoście.</span><span class="sxs-lookup"><span data-stu-id="745a6-177">In this pipeline, the add-in provides a service to the host, and the types flow from the add-in to the host.</span></span> <span data-ttu-id="745a6-178">Ponieważ żaden z typów usługi flow z hosta do dodatku, ma zawierać adapter kontraktu na widok po stronie dodatku w tym potoku.</span><span class="sxs-lookup"><span data-stu-id="745a6-178">Because no types flow from the host to the add-in, you do not have to include a contract-to-view adapter on the add-in side of this pipeline.</span></span>  
  
#### <a name="to-create-the-add-in-side-adapter"></a><span data-ttu-id="745a6-179">Aby utworzyć adapter add w side</span><span class="sxs-lookup"><span data-stu-id="745a6-179">To create the add-in-side adapter</span></span>  
  
1.  <span data-ttu-id="745a6-180">Dodaj nowy projekt o nazwie `Calc1AddInSideAdapter` do `CalculatorV1` rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="745a6-180">Add a new project named `Calc1AddInSideAdapter` to the `CalculatorV1` solution.</span></span> <span data-ttu-id="745a6-181">Oparte na **biblioteki klas** szablonu.</span><span class="sxs-lookup"><span data-stu-id="745a6-181">Base it on the **Class Library** template.</span></span>  
  
2.  <span data-ttu-id="745a6-182">W **Eksploratora rozwiązań**, dodaj odwołania do następujących zestawów, które mają `Calc1AddInSideAdapter` projektu:</span><span class="sxs-lookup"><span data-stu-id="745a6-182">In **Solution Explorer**, add references to the following assemblies to the `Calc1AddInSideAdapter` project:</span></span>  
  
     <span data-ttu-id="745a6-183">System.AddIn.dll</span><span class="sxs-lookup"><span data-stu-id="745a6-183">System.AddIn.dll</span></span>  
  
     <span data-ttu-id="745a6-184">System.AddIn.Contract.dll</span><span class="sxs-lookup"><span data-stu-id="745a6-184">System.AddIn.Contract.dll</span></span>  
  
3.  <span data-ttu-id="745a6-185">Dodaj odwołania do projektu do projektów segmentów potoku sąsiadujące:</span><span class="sxs-lookup"><span data-stu-id="745a6-185">Add project references to the projects for the adjacent pipeline segments:</span></span>  
  
     `Calc1AddInView`  
  
     `Calc1Contract`  
  
4.  <span data-ttu-id="745a6-186">Wybierz odwołanie do każdego projektu, a następnie w **właściwości** ustaw **Kopiuj lokalnie** do **False**.</span><span class="sxs-lookup"><span data-stu-id="745a6-186">Select each project reference, and in **Properties** set **Copy Local** to **False**.</span></span> <span data-ttu-id="745a6-187">W języku Visual Basic należy używać **odwołania** karcie **właściwości projektu** można ustawić **Kopiuj lokalnie** do **False** dwa projektu odwołania.</span><span class="sxs-lookup"><span data-stu-id="745a6-187">In Visual Basic, use the **References** tab of **Project Properties** to set **Copy Local** to **False** for the two project references.</span></span>  
  
5.  <span data-ttu-id="745a6-188">Zmień nazwę projektu domyślną klasę `CalculatorViewToContractAddInSideAdapter`.</span><span class="sxs-lookup"><span data-stu-id="745a6-188">Rename the project's default class `CalculatorViewToContractAddInSideAdapter`.</span></span>  
  
6.  <span data-ttu-id="745a6-189">W pliku klasy należy dodać odwołania do przestrzeni nazw do <xref:System.AddIn.Pipeline>.</span><span class="sxs-lookup"><span data-stu-id="745a6-189">In the class file, add namespace references to <xref:System.AddIn.Pipeline>.</span></span>  
  
7.  <span data-ttu-id="745a6-190">W pliku klasy należy dodać odwołania do przestrzeni nazw dla sąsiadujących segmentów: `CalcAddInViews` i `CalculatorContracts`.</span><span class="sxs-lookup"><span data-stu-id="745a6-190">In the class file, add namespace references for the adjacent segments: `CalcAddInViews` and `CalculatorContracts`.</span></span> <span data-ttu-id="745a6-191">(W języku Visual Basic są te odwołania do przestrzeni nazw `Calc1AddInView.CalcAddInViews` i `Calc1Contract.CalculatorContracts`, o ile nie wyłączysz domyślne obszary nazw w projektach języka Visual Basic.)</span><span class="sxs-lookup"><span data-stu-id="745a6-191">(In Visual Basic, these namespace references are `Calc1AddInView.CalcAddInViews` and `Calc1Contract.CalculatorContracts`, unless you have turned off the default namespaces in your Visual Basic projects.)</span></span>  
  
8.  <span data-ttu-id="745a6-192">Zastosuj <xref:System.AddIn.Pipeline.AddInAdapterAttribute> atrybutu `CalculatorViewToContractAddInSideAdapter` klasy, aby je zidentyfikować jako karta add w side.</span><span class="sxs-lookup"><span data-stu-id="745a6-192">Apply the <xref:System.AddIn.Pipeline.AddInAdapterAttribute> attribute to the `CalculatorViewToContractAddInSideAdapter` class, to identify it as the add-in-side adapter.</span></span>  
  
9. <span data-ttu-id="745a6-193">Wprowadzić `CalculatorViewToContractAddInSideAdapter` klasa dziedziczy <xref:System.AddIn.Pipeline.ContractBase>, który udostępnia domyślną implementację elementu <xref:System.AddIn.Contract.IContract> interfejs i implementować interfejs kontraktu dla potoku, `ICalc1Contract`.</span><span class="sxs-lookup"><span data-stu-id="745a6-193">Make the `CalculatorViewToContractAddInSideAdapter` class inherit <xref:System.AddIn.Pipeline.ContractBase>, which provides a default implementation of the <xref:System.AddIn.Contract.IContract> interface, and implement the contract interface for the pipeline, `ICalc1Contract`.</span></span>  
  
10. <span data-ttu-id="745a6-194">Dodaj Konstruktor publiczny, który akceptuje `ICalculator`, zapisuje go w pamięci podręcznej w pole prywatne i wywołuje konstruktora klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="745a6-194">Add a public constructor that accepts an `ICalculator`, caches it in a private field, and calls the base class constructor.</span></span>  
  
11. <span data-ttu-id="745a6-195">Do zaimplementowania elementów członkowskich `ICalc1Contract`, wystarczy wywołać odpowiednie elementy członkowskie `ICalculator` wystąpienia, który jest przekazywany do konstruktora, a następnie zwracają wyniki.</span><span class="sxs-lookup"><span data-stu-id="745a6-195">To implement the members of `ICalc1Contract`, simply call the corresponding members of the `ICalculator` instance that is passed to the constructor, and return the results.</span></span> <span data-ttu-id="745a6-196">To dostosowuje widoku (`ICalculator`) z umową (`ICalc1Contract`).</span><span class="sxs-lookup"><span data-stu-id="745a6-196">This adapts the view (`ICalculator`) to the contract (`ICalc1Contract`).</span></span>  
  
     <span data-ttu-id="745a6-197">Poniższy kod przedstawia ukończone karty dodać strony.</span><span class="sxs-lookup"><span data-stu-id="745a6-197">The following code shows the completed add-in-side adapter.</span></span>  
  
     [!code-csharp[AddInP1AddInSideAdapters#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInSideAdapters/cs/Calc1ViewToContractAddInSideAdapter.cs#1)]
     [!code-vb[AddInP1AddInSideAdapters#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInSideAdapters/vb/Calc1ViewToContractAddInSideAdapter.vb#1)]  
  
12. <span data-ttu-id="745a6-198">Opcjonalnie można tworzyć rozwiązania programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="745a6-198">Optionally, build the Visual Studio solution.</span></span>  
  
## <a name="creating-the-host-side-adapter"></a><span data-ttu-id="745a6-199">Tworzenie adaptera po stronie hosta</span><span class="sxs-lookup"><span data-stu-id="745a6-199">Creating the Host-side Adapter</span></span>  
 <span data-ttu-id="745a6-200">Ten adapter po stronie hosta składa się z jednej karty kontraktu na widok.</span><span class="sxs-lookup"><span data-stu-id="745a6-200">This host-side adapter consists of one contract-to-view adapter.</span></span> <span data-ttu-id="745a6-201">Ten segment dostosowuje się kontraktu na widok hosta dodatków.</span><span class="sxs-lookup"><span data-stu-id="745a6-201">This segment adapts the contract to the host view of the add-in.</span></span>  
  
 <span data-ttu-id="745a6-202">W tym potoku dodatku udostępnia usługę hosta i przepływ typów w dodatku do hosta.</span><span class="sxs-lookup"><span data-stu-id="745a6-202">In this pipeline, the add-in provides a service to the host and the types flow from the add-in to the host.</span></span> <span data-ttu-id="745a6-203">Ponieważ żaden z typów usługi flow z hosta do dodatku, ma zawierać adapter kontraktu na widok.</span><span class="sxs-lookup"><span data-stu-id="745a6-203">Because no types flow from the host to the add-in, you do not have to include a view-to-contract adapter.</span></span>  
  
 <span data-ttu-id="745a6-204">Aby zaimplementować Zarządzanie okresem istnienia, należy użyć <xref:System.AddIn.Pipeline.ContractHandle> obiekt można dołączyć okres istnienia tokenu do Umowy.</span><span class="sxs-lookup"><span data-stu-id="745a6-204">To implement lifetime management, use a <xref:System.AddIn.Pipeline.ContractHandle> object to attach a lifetime token to the contract.</span></span> <span data-ttu-id="745a6-205">Odwołanie do tego dojścia musi przechowywać w kolejności do działania zarządzania okresem istnienia.</span><span class="sxs-lookup"><span data-stu-id="745a6-205">You must keep a reference to this handle in order for lifetime management to work.</span></span> <span data-ttu-id="745a6-206">Po zastosowaniu token nie dodatkowego programowania jest wymagane, ponieważ system dodatku można usuwania obiektów, kiedy są już używane i udostępnić je do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="745a6-206">After the token is applied, no additional programming is required because the add-in system can dispose of objects when they are no longer being used and make them available for garbage collection.</span></span> <span data-ttu-id="745a6-207">Aby uzyskać więcej informacji, zobacz [Zarządzanie okresem istnienia](https://msdn.microsoft.com/library/57a9c87e-394c-4fef-89f2-aa4223a2aeb5).</span><span class="sxs-lookup"><span data-stu-id="745a6-207">For more information, see [Lifetime Management](https://msdn.microsoft.com/library/57a9c87e-394c-4fef-89f2-aa4223a2aeb5).</span></span>  
  
#### <a name="to-create-the-host-side-adapter"></a><span data-ttu-id="745a6-208">Aby utworzyć adapter po stronie hosta</span><span class="sxs-lookup"><span data-stu-id="745a6-208">To create the host-side adapter</span></span>  
  
1.  <span data-ttu-id="745a6-209">Dodaj nowy projekt o nazwie `Calc1HostSideAdapter` do `CalculatorV1` rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="745a6-209">Add a new project named `Calc1HostSideAdapter` to the `CalculatorV1` solution.</span></span> <span data-ttu-id="745a6-210">Oparte na **biblioteki klas** szablonu.</span><span class="sxs-lookup"><span data-stu-id="745a6-210">Base it on the **Class Library** template.</span></span>  
  
2.  <span data-ttu-id="745a6-211">W **Eksploratora rozwiązań**, dodaj odwołania do następujących zestawów, które mają `Calc1HostSideAdapter` projektu:</span><span class="sxs-lookup"><span data-stu-id="745a6-211">In **Solution Explorer**, add references to the following assemblies to the `Calc1HostSideAdapter` project:</span></span>  
  
     <span data-ttu-id="745a6-212">System.AddIn.dll</span><span class="sxs-lookup"><span data-stu-id="745a6-212">System.AddIn.dll</span></span>  
  
     <span data-ttu-id="745a6-213">System.AddIn.Contract.dll</span><span class="sxs-lookup"><span data-stu-id="745a6-213">System.AddIn.Contract.dll</span></span>  
  
3.  <span data-ttu-id="745a6-214">Dodaj odwołania do projektu do projektów sąsiadujących segmentów:</span><span class="sxs-lookup"><span data-stu-id="745a6-214">Add project references to the projects for the adjacent segments:</span></span>  
  
     `Calc1Contract`  
  
     `Calc1HVA`  
  
4.  <span data-ttu-id="745a6-215">Wybierz odwołanie do każdego projektu, a następnie w **właściwości** ustaw **Kopiuj lokalnie** do **False**.</span><span class="sxs-lookup"><span data-stu-id="745a6-215">Select each project reference, and in **Properties** set **Copy Local** to **False**.</span></span> <span data-ttu-id="745a6-216">W języku Visual Basic należy używać **odwołania** karcie **właściwości projektu** można ustawić **Kopiuj lokalnie** do **False** dwa projektu odwołania.</span><span class="sxs-lookup"><span data-stu-id="745a6-216">In Visual Basic, use the **References** tab of **Project Properties** to set **Copy Local** to **False** for the two project references.</span></span>  
  
5.  <span data-ttu-id="745a6-217">Zmień nazwę projektu domyślną klasę `CalculatorContractToViewHostSideAdapter`.</span><span class="sxs-lookup"><span data-stu-id="745a6-217">Rename the project's default class `CalculatorContractToViewHostSideAdapter`.</span></span>  
  
6.  <span data-ttu-id="745a6-218">W pliku klasy należy dodać odwołania do przestrzeni nazw do <xref:System.AddIn.Pipeline>.</span><span class="sxs-lookup"><span data-stu-id="745a6-218">In the class file, add namespace references to <xref:System.AddIn.Pipeline>.</span></span>  
  
7.  <span data-ttu-id="745a6-219">W pliku klasy należy dodać odwołania do przestrzeni nazw dla sąsiadujących segmentów: `CalcHVAs` i `CalculatorContracts`.</span><span class="sxs-lookup"><span data-stu-id="745a6-219">In the class file, add namespace references for the adjacent segments: `CalcHVAs` and `CalculatorContracts`.</span></span> <span data-ttu-id="745a6-220">(W języku Visual Basic są te odwołania do przestrzeni nazw `Calc1HVA.CalcHVAs` i `Calc1Contract.CalculatorContracts`, o ile nie wyłączysz domyślne obszary nazw w projektach języka Visual Basic.)</span><span class="sxs-lookup"><span data-stu-id="745a6-220">(In Visual Basic, these namespace references are `Calc1HVA.CalcHVAs` and `Calc1Contract.CalculatorContracts`, unless you have turned off the default namespaces in your Visual Basic projects.)</span></span>  
  
8.  <span data-ttu-id="745a6-221">Zastosuj <xref:System.AddIn.Pipeline.HostAdapterAttribute> atrybutu `CalculatorContractToViewHostSideAdapter` klasy, aby je zidentyfikować jako segment adaptery po stronie hosta.</span><span class="sxs-lookup"><span data-stu-id="745a6-221">Apply the <xref:System.AddIn.Pipeline.HostAdapterAttribute> attribute to the `CalculatorContractToViewHostSideAdapter` class, to identify it as the host-side adapter segment.</span></span>  
  
9. <span data-ttu-id="745a6-222">Wprowadź `CalculatorContractToViewHostSideAdapter` klasa implementuje interfejs, który reprezentuje widok hosta dodatków: `Calc1HVAs.ICalculator` (`Calc1HVA.CalcHVAs.ICalculator` w języku Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="745a6-222">Make the `CalculatorContractToViewHostSideAdapter` class implement the interface that represents the host view of the add-in: `Calc1HVAs.ICalculator` (`Calc1HVA.CalcHVAs.ICalculator` in Visual Basic).</span></span>  
  
10. <span data-ttu-id="745a6-223">Dodaj Konstruktor publiczny, który akceptuje typ kontraktu potoku, `ICalc1Contract`.</span><span class="sxs-lookup"><span data-stu-id="745a6-223">Add a public constructor that accepts the pipeline contract type, `ICalc1Contract`.</span></span> <span data-ttu-id="745a6-224">Konstruktor musi pamięci podręcznej odwołanie do Umowy.</span><span class="sxs-lookup"><span data-stu-id="745a6-224">The constructor must cache the reference to the contract.</span></span> <span data-ttu-id="745a6-225">Należy także utworzyć i pamięci podręcznej nową <xref:System.AddIn.Pipeline.ContractHandle> dla umowy, aby zarządzać okresem istnienia dodatku.</span><span class="sxs-lookup"><span data-stu-id="745a6-225">It must also create and cache a new <xref:System.AddIn.Pipeline.ContractHandle> for the contract, to manage the lifetime of the add-in.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="745a6-226"><xref:System.AddIn.Pipeline.ContractHandle> Mają kluczowe znaczenie dla zarządzania okresem istnienia.</span><span class="sxs-lookup"><span data-stu-id="745a6-226">The <xref:System.AddIn.Pipeline.ContractHandle> is critical to lifetime management.</span></span> <span data-ttu-id="745a6-227">Jeśli nie zostanie utrzymywać odwołania do <xref:System.AddIn.Pipeline.ContractHandle> obiektów, wyrzucanie elementów bezużytecznych będzie go odzyskać, a potoku zostanie zamknięty, gdy program nie oczekuje.</span><span class="sxs-lookup"><span data-stu-id="745a6-227">If you fail to keep a reference to the <xref:System.AddIn.Pipeline.ContractHandle> object, garbage collection will reclaim it, and the pipeline will shut down when your program does not expect it.</span></span> <span data-ttu-id="745a6-228">Może to prowadzić do błędów, które są trudne do zdiagnozowania, takich jak <xref:System.AppDomainUnloadedException>.</span><span class="sxs-lookup"><span data-stu-id="745a6-228">This can lead to errors that are difficult to diagnose, such as <xref:System.AppDomainUnloadedException>.</span></span> <span data-ttu-id="745a6-229">Zamknięcie jest normalne etapie w cyklu życia potoku, dlatego nie ma możliwości dla kodu zarządzania okres istnienia wykryć, czy ten warunek występuje błąd.</span><span class="sxs-lookup"><span data-stu-id="745a6-229">Shutdown is a normal stage in the life of a pipeline, so there is no way for the lifetime management code to detect that this condition is an error.</span></span>  
  
11. <span data-ttu-id="745a6-230">Do zaimplementowania elementów członkowskich `ICalculator`, wystarczy wywołać odpowiednie elementy członkowskie `ICalc1Contract` wystąpienia, który jest przekazywany do konstruktora, a następnie zwracają wyniki.</span><span class="sxs-lookup"><span data-stu-id="745a6-230">To implement the members of `ICalculator`, simply call the corresponding members of the `ICalc1Contract` instance that is passed to the constructor, and return the results.</span></span> <span data-ttu-id="745a6-231">To dostosowuje kontraktu (`ICalc1Contract`) do widoku (`ICalculator`).</span><span class="sxs-lookup"><span data-stu-id="745a6-231">This adapts the contract (`ICalc1Contract`) to the view (`ICalculator`).</span></span>  
  
     <span data-ttu-id="745a6-232">Poniższy kod przedstawia ukończone adapter po stronie hosta.</span><span class="sxs-lookup"><span data-stu-id="745a6-232">The following code shows the completed host-side adapter.</span></span>  
  
     [!code-csharp[AddInP1HostSideAdapters#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1HostSideAdapters/cs/Calc1ContractToViewHostSideAdapter.cs#1)]
     [!code-vb[AddInP1HostSideAdapters#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1HostSideAdapters/vb/Calc1ContractToViewHostSideAdapter.vb#1)]  
  
12. <span data-ttu-id="745a6-233">Opcjonalnie można tworzyć rozwiązania programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="745a6-233">Optionally, build the Visual Studio solution.</span></span>  
  
## <a name="creating-the-host"></a><span data-ttu-id="745a6-234">Tworzenie hosta</span><span class="sxs-lookup"><span data-stu-id="745a6-234">Creating the Host</span></span>  
 <span data-ttu-id="745a6-235">Aplikacja hosta wchodzi w interakcje przy użyciu dodatku za pośrednictwem widoku hosta dodatku.</span><span class="sxs-lookup"><span data-stu-id="745a6-235">A host application interacts with the add-in through the host view of the add-in.</span></span> <span data-ttu-id="745a6-236">Używa dodatku odnajdywania i aktywacja metod dostarczonych przez <xref:System.AddIn.Hosting.AddInStore> i <xref:System.AddIn.Hosting.AddInToken> klasy, aby wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="745a6-236">It uses add-in discovery and activation methods provided by the <xref:System.AddIn.Hosting.AddInStore> and <xref:System.AddIn.Hosting.AddInToken> classes to do the following:</span></span>  
  
-   <span data-ttu-id="745a6-237">Aktualizacja pamięci podręcznej informacje o potoku i dodatku.</span><span class="sxs-lookup"><span data-stu-id="745a6-237">Update the cache of pipeline and add-in information.</span></span>  
  
-   <span data-ttu-id="745a6-238">Znajdź dodatki typu widoku hosta `ICalculator`, w katalogu głównym określonej potoku.</span><span class="sxs-lookup"><span data-stu-id="745a6-238">Find add-ins of the host view type, `ICalculator`, under the specified pipeline root directory.</span></span>  
  
-   <span data-ttu-id="745a6-239">Monituj użytkownika o określenie, której dodatek do użycia.</span><span class="sxs-lookup"><span data-stu-id="745a6-239">Prompt the user to specify which add-in to use.</span></span>  
  
-   <span data-ttu-id="745a6-240">Aktywuj wybrany dodatek w nowej domenie aplikacji z poziomu zaufania zabezpieczeń określone.</span><span class="sxs-lookup"><span data-stu-id="745a6-240">Activate the selected add-in in a new application domain with a specified security trust level.</span></span>  
  
-   <span data-ttu-id="745a6-241">Uruchom niestandardowe `RunCalculator` metody, która wywołuje metody w dodatku, określony przez widok hosta dodatków.</span><span class="sxs-lookup"><span data-stu-id="745a6-241">Run the custom `RunCalculator` method, which calls the add-in's methods as specified by the host view of the add-in.</span></span>  
  
#### <a name="to-create-the-host"></a><span data-ttu-id="745a6-242">W celu utworzenia hosta</span><span class="sxs-lookup"><span data-stu-id="745a6-242">To create the host</span></span>  
  
1.  <span data-ttu-id="745a6-243">Dodaj nowy projekt o nazwie `Calc1Host` do `CalculatorV1` rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="745a6-243">Add a new project named `Calc1Host` to the `CalculatorV1` solution.</span></span> <span data-ttu-id="745a6-244">Oparte na **aplikację Konsolową** szablonu.</span><span class="sxs-lookup"><span data-stu-id="745a6-244">Base it on the **Console Application** template.</span></span>  
  
2.  <span data-ttu-id="745a6-245">W **Eksploratora rozwiązań**, Dodaj odwołanie do zestawu System.AddIn.dll `Calc1Host` projektu.</span><span class="sxs-lookup"><span data-stu-id="745a6-245">In **Solution Explorer**, add a reference to the System.AddIn.dll assembly to the `Calc1Host` project.</span></span>  
  
3.  <span data-ttu-id="745a6-246">Dodaj odwołanie do `Calc1HVA` projektu.</span><span class="sxs-lookup"><span data-stu-id="745a6-246">Add a project reference to the `Calc1HVA` project.</span></span> <span data-ttu-id="745a6-247">Wybierz odwołanie do projektu, a następnie w **właściwości** ustaw **Kopiuj lokalnie** do **False**.</span><span class="sxs-lookup"><span data-stu-id="745a6-247">Select the project reference, and in **Properties** set **Copy Local** to **False**.</span></span> <span data-ttu-id="745a6-248">W języku Visual Basic należy używać **odwołania** karcie **właściwości projektu** można ustawić **Kopiuj lokalnie** do **False**.</span><span class="sxs-lookup"><span data-stu-id="745a6-248">In Visual Basic, use the **References** tab of **Project Properties** to set **Copy Local** to **False**.</span></span>  
  
4.  <span data-ttu-id="745a6-249">Zmień nazwę pliku klasy (modułu w języku Visual Basic) `MathHost1`.</span><span class="sxs-lookup"><span data-stu-id="745a6-249">Rename the class file (module in Visual Basic) `MathHost1`.</span></span>  
  
5.  <span data-ttu-id="745a6-250">W języku Visual Basic należy używać **aplikacji** karcie **właściwości projektu** okno dialogowe, aby ustawić **obiekt początkowy** do **Sub Main**.</span><span class="sxs-lookup"><span data-stu-id="745a6-250">In Visual Basic, use the **Application** tab of the **Project Properties** dialog box to set **Startup object** to **Sub Main**.</span></span>  
  
6.  <span data-ttu-id="745a6-251">W pliku klasę lub moduł, należy dodać odwołanie do przestrzeni nazw <xref:System.AddIn.Hosting>.</span><span class="sxs-lookup"><span data-stu-id="745a6-251">In the class or module file, add a namespace reference to <xref:System.AddIn.Hosting>.</span></span>  
  
7.  <span data-ttu-id="745a6-252">W pliku klasę lub moduł, Dodaj odwołanie przestrzeni nazw dla widoku hosta dodatku: `CalcHVAs`.</span><span class="sxs-lookup"><span data-stu-id="745a6-252">In the class or module file, add a namespace reference for the host view of the add-in: `CalcHVAs`.</span></span> <span data-ttu-id="745a6-253">(W języku Visual Basic to odwołanie do przestrzeni nazw jest `Calc1HVA.CalcHVAs`, o ile nie wyłączysz domyślne obszary nazw w projektach języka Visual Basic.)</span><span class="sxs-lookup"><span data-stu-id="745a6-253">(In Visual Basic, this namespace reference is `Calc1HVA.CalcHVAs`, unless you have turned off the default namespaces in your Visual Basic projects.)</span></span>  
  
8.  <span data-ttu-id="745a6-254">W **Eksploratora rozwiązań**, wybierz rozwiązanie i **projektu** menu wybierz opcję **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="745a6-254">In **Solution Explorer**, select the solution and from the **Project** menu choose **Properties**.</span></span> <span data-ttu-id="745a6-255">W **strony właściwości rozwiązania** okno dialogowe, zestaw **pojedynczy projekt startowy** za ten projekt aplikacji hosta.</span><span class="sxs-lookup"><span data-stu-id="745a6-255">In the **Solution Property Pages** dialog box, set the **Single Startup Project** to be this host application project.</span></span>  
  
9. <span data-ttu-id="745a6-256">W pliku klasę lub moduł, użyj <xref:System.AddIn.Hosting.AddInStore.Update%2A?displayProperty=nameWithType> metodę, aby zaktualizować pamięć podręczną.</span><span class="sxs-lookup"><span data-stu-id="745a6-256">In the class or module file, use the <xref:System.AddIn.Hosting.AddInStore.Update%2A?displayProperty=nameWithType> method to update the cache.</span></span> <span data-ttu-id="745a6-257">Użyj <xref:System.AddIn.Hosting.AddInStore.FindAddIn%2A?displayProperty=nameWithType> metodę, aby uzyskać kolekcję tokenów oraz <xref:System.AddIn.Hosting.AddInToken.Activate%2A?displayProperty=nameWithType> metodę, aby aktywować dodatku.</span><span class="sxs-lookup"><span data-stu-id="745a6-257">Use the <xref:System.AddIn.Hosting.AddInStore.FindAddIn%2A?displayProperty=nameWithType> method to get a collection of tokens, and use the <xref:System.AddIn.Hosting.AddInToken.Activate%2A?displayProperty=nameWithType> method to activate an add-in.</span></span>  
  
     <span data-ttu-id="745a6-258">Poniższy kod przedstawia aplikacji hosta ukończone.</span><span class="sxs-lookup"><span data-stu-id="745a6-258">The following code shows the completed host application.</span></span>  
  
     [!code-csharp[AddInP1Host#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1Host/cs/MathHost1.cs#1)]
     [!code-vb[AddInP1Host#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1Host/vb/MathHost1.vb#1)]  
  
    > [!NOTE]
    >  <span data-ttu-id="745a6-259">Ten kod zakłada, że struktura folderów potoku znajduje się w folderze aplikacji.</span><span class="sxs-lookup"><span data-stu-id="745a6-259">This code assumes that the pipeline folder structure is located in the application folder.</span></span> <span data-ttu-id="745a6-260">Jeśli użytkownik znajduje się go innym miejscu, zmień wiersz kodu, który ustawia `addInRoot` zmiennej, tak aby zmienna zawiera ścieżkę do potoku struktury katalogów.</span><span class="sxs-lookup"><span data-stu-id="745a6-260">If you located it elsewhere, change the line of code that sets the `addInRoot` variable, so that the variable contains the path to your pipeline directory structure.</span></span>  
  
     <span data-ttu-id="745a6-261">Kod używa `ChooseCalculator` metody, aby wyświetlić listę tokenów i aby monitować użytkownika o wybranie dodatku.</span><span class="sxs-lookup"><span data-stu-id="745a6-261">The code uses a `ChooseCalculator` method to list the tokens and to prompt the user to choose an add-in.</span></span> <span data-ttu-id="745a6-262">`RunCalculator` Metoda monituje użytkownika o wyrażeń matematycznych prosty, analizuje wyrażeń przy użyciu `Parser` klasy i wyświetla wyniki zwrócone przez dodatek.</span><span class="sxs-lookup"><span data-stu-id="745a6-262">The `RunCalculator` method prompts the user for simple math expressions, parses the expressions using the `Parser` class, and displays the results returned by the add-in.</span></span>  
  
10. <span data-ttu-id="745a6-263">Opcjonalnie można tworzyć rozwiązania programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="745a6-263">Optionally, build the Visual Studio solution.</span></span>  
  
## <a name="creating-the-add-in"></a><span data-ttu-id="745a6-264">Tworzenie dodatku</span><span class="sxs-lookup"><span data-stu-id="745a6-264">Creating the Add-In</span></span>  
 <span data-ttu-id="745a6-265">Dodatek implementuje metody określonej przez widok dodatku.</span><span class="sxs-lookup"><span data-stu-id="745a6-265">An add-in implements the methods specified by the add-in view.</span></span> <span data-ttu-id="745a6-266">Ten dodatek implementuje `Add`, `Subtract`, `Multiply`, i `Divide` operacje i zwraca wyniki do hosta.</span><span class="sxs-lookup"><span data-stu-id="745a6-266">This add-in implements the `Add`, `Subtract`, `Multiply`, and `Divide` operations and returns the results to the host.</span></span>  
  
#### <a name="to-create-the-add-in"></a><span data-ttu-id="745a6-267">Aby utworzyć dodatek</span><span class="sxs-lookup"><span data-stu-id="745a6-267">To create the add-in</span></span>  
  
1.  <span data-ttu-id="745a6-268">Dodaj nowy projekt o nazwie `AddInCalcV1` do `CalculatorV1` rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="745a6-268">Add a new project named `AddInCalcV1` to the `CalculatorV1` solution.</span></span> <span data-ttu-id="745a6-269">Oparte na **biblioteki klas** szablonu.</span><span class="sxs-lookup"><span data-stu-id="745a6-269">Base it on the **Class Library** template.</span></span>  
  
2.  <span data-ttu-id="745a6-270">W **Eksploratora rozwiązań**, Dodaj odwołanie do zestawu System.AddIn.dll do projektu.</span><span class="sxs-lookup"><span data-stu-id="745a6-270">In **Solution Explorer**, add a reference to the System.AddIn.dll assembly to the project.</span></span>  
  
3.  <span data-ttu-id="745a6-271">Dodaj odwołanie do `Calc1AddInView` projektu.</span><span class="sxs-lookup"><span data-stu-id="745a6-271">Add a project reference to the `Calc1AddInView` project.</span></span> <span data-ttu-id="745a6-272">Wybierz odwołanie do projektu, a następnie w **właściwości**ustaw **Kopiuj lokalnie** do **False**.</span><span class="sxs-lookup"><span data-stu-id="745a6-272">Select the project reference, and in **Properties**, set **Copy Local** to **False**.</span></span> <span data-ttu-id="745a6-273">W języku Visual Basic należy używać **odwołania** karcie **właściwości projektu** można ustawić **Kopiuj lokalnie** do **False** odwołania projektu.</span><span class="sxs-lookup"><span data-stu-id="745a6-273">In Visual Basic, use the **References** tab of **Project Properties** to set **Copy Local** to **False** for the project reference.</span></span>  
  
4.  <span data-ttu-id="745a6-274">Zmień nazwę klasy `AddInCalcV1`.</span><span class="sxs-lookup"><span data-stu-id="745a6-274">Rename the class `AddInCalcV1`.</span></span>  
  
5.  <span data-ttu-id="745a6-275">W pliku klasy należy dodać odwołanie do przestrzeni nazw <xref:System.AddIn> i segmentów widoku dodatku: `CalcAddInViews` (`Calc1AddInView.CalcAddInViews` w języku Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="745a6-275">In the class file, add a namespace reference to <xref:System.AddIn> and the add-in view segment: `CalcAddInViews` (`Calc1AddInView.CalcAddInViews` in Visual Basic).</span></span>  
  
6.  <span data-ttu-id="745a6-276">Zastosuj <xref:System.AddIn.AddInAttribute> atrybutu `AddInCalcV1` klasy, aby zidentyfikować klasy jako dodatek.</span><span class="sxs-lookup"><span data-stu-id="745a6-276">Apply the <xref:System.AddIn.AddInAttribute> attribute to the `AddInCalcV1` class, to identify the class as an add-in.</span></span>  
  
7.  <span data-ttu-id="745a6-277">Wprowadź `AddInCalcV1` klasa implementuje interfejs, który reprezentuje Widok dodatku: `CalcAddInViews.ICalculator` (`Calc1AddInView.CalcAddInViews.ICalculator` w języku Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="745a6-277">Make the `AddInCalcV1` class implement the interface that represents the add-in view: `CalcAddInViews.ICalculator` (`Calc1AddInView.CalcAddInViews.ICalculator` in Visual Basic).</span></span>  
  
8.  <span data-ttu-id="745a6-278">Implementowanie członkowie `ICalculator` , zwracając wyniki obliczeń odpowiednie.</span><span class="sxs-lookup"><span data-stu-id="745a6-278">Implement the members of `ICalculator` by returning the results of the appropriate calculations.</span></span>  
  
     <span data-ttu-id="745a6-279">Poniższy kod przedstawia ukończone dodatku programu.</span><span class="sxs-lookup"><span data-stu-id="745a6-279">The following code shows the completed add-in.</span></span>  
  
     [!code-csharp[AddInP1AddInCalcV1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInCalcV1/cs/AddInCalcV1.cs#1)]
     [!code-vb[AddInP1AddInCalcV1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInCalcV1/vb/AddInCalcV1.vb#1)]  
  
9. <span data-ttu-id="745a6-280">Opcjonalnie można tworzyć rozwiązania programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="745a6-280">Optionally, build the Visual Studio solution.</span></span>  
  
## <a name="deploying-the-pipeline"></a><span data-ttu-id="745a6-281">Wdrażania potoku</span><span class="sxs-lookup"><span data-stu-id="745a6-281">Deploying the Pipeline</span></span>  
 <span data-ttu-id="745a6-282">Teraz można przystąpić do tworzenia i wdrażania segmentów w dodatku do potoku wymagane struktury katalogów.</span><span class="sxs-lookup"><span data-stu-id="745a6-282">You are now ready to build and deploy the add-in segments to the required pipeline directory structure.</span></span>  
  
#### <a name="to-deploy-the-segments-to-the-pipeline"></a><span data-ttu-id="745a6-283">Aby wdrożyć segmenty potoku</span><span class="sxs-lookup"><span data-stu-id="745a6-283">To deploy the segments to the pipeline</span></span>  
  
1.  <span data-ttu-id="745a6-284">Dla każdego projektu w rozwiązaniu, użyj **kompilacji** karcie **właściwości projektu** ( **skompilować** kartę w języku Visual Basic) można ustawić wartość **ścieżka wyjściowa**  ( **ścieżkę wyjściową kompilacji** w języku Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="745a6-284">For each project in the solution, use the **Build** tab of **Project Properties** (the **Compile** tab in Visual Basic) to set the value of the **Output path** (the **Build output path** in Visual Basic).</span></span> <span data-ttu-id="745a6-285">Jeśli nazwany folderze aplikacji `MyApp`, na przykład projekty będzie umieszczenie w następujących folderów:</span><span class="sxs-lookup"><span data-stu-id="745a6-285">If you named your application folder `MyApp`, for example, your projects would build into the following folders:</span></span>  
  
    |<span data-ttu-id="745a6-286">Projekt</span><span class="sxs-lookup"><span data-stu-id="745a6-286">Project</span></span>|<span data-ttu-id="745a6-287">Ścieżka</span><span class="sxs-lookup"><span data-stu-id="745a6-287">Path</span></span>|  
    |-------------|----------|  
    |<span data-ttu-id="745a6-288">AddInCalcV1</span><span class="sxs-lookup"><span data-stu-id="745a6-288">AddInCalcV1</span></span>|<span data-ttu-id="745a6-289">MyApp\Pipeline\AddIns\CalcV1</span><span class="sxs-lookup"><span data-stu-id="745a6-289">MyApp\Pipeline\AddIns\CalcV1</span></span>|  
    |<span data-ttu-id="745a6-290">Calc1AddInSideAdapter</span><span class="sxs-lookup"><span data-stu-id="745a6-290">Calc1AddInSideAdapter</span></span>|<span data-ttu-id="745a6-291">MyApp\Pipeline\AddInSideAdapters</span><span class="sxs-lookup"><span data-stu-id="745a6-291">MyApp\Pipeline\AddInSideAdapters</span></span>|  
    |<span data-ttu-id="745a6-292">Calc1AddInView</span><span class="sxs-lookup"><span data-stu-id="745a6-292">Calc1AddInView</span></span>|<span data-ttu-id="745a6-293">MyApp\Pipeline\AddInViews</span><span class="sxs-lookup"><span data-stu-id="745a6-293">MyApp\Pipeline\AddInViews</span></span>|  
    |<span data-ttu-id="745a6-294">Calc1Contract</span><span class="sxs-lookup"><span data-stu-id="745a6-294">Calc1Contract</span></span>|<span data-ttu-id="745a6-295">MyApp\Pipeline\Contracts</span><span class="sxs-lookup"><span data-stu-id="745a6-295">MyApp\Pipeline\Contracts</span></span>|  
    |<span data-ttu-id="745a6-296">Calc1Host</span><span class="sxs-lookup"><span data-stu-id="745a6-296">Calc1Host</span></span>|<span data-ttu-id="745a6-297">MyApp</span><span class="sxs-lookup"><span data-stu-id="745a6-297">MyApp</span></span>|  
    |<span data-ttu-id="745a6-298">Calc1HostSideAdapter</span><span class="sxs-lookup"><span data-stu-id="745a6-298">Calc1HostSideAdapter</span></span>|<span data-ttu-id="745a6-299">MyApp\Pipeline\HostSideAdapters</span><span class="sxs-lookup"><span data-stu-id="745a6-299">MyApp\Pipeline\HostSideAdapters</span></span>|  
    |<span data-ttu-id="745a6-300">Calc1HVA</span><span class="sxs-lookup"><span data-stu-id="745a6-300">Calc1HVA</span></span>|<span data-ttu-id="745a6-301">MyApp</span><span class="sxs-lookup"><span data-stu-id="745a6-301">MyApp</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="745a6-302">Jeśli zdecydujesz się na umieszczenie Twoja struktura folderów potoku w lokalizacji innej niż folder aplikacji, należy zmodyfikować ścieżek przedstawionych w tabeli, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="745a6-302">If you decided to put your pipeline folder structure in a location other than your application folder, you must modify the paths shown in the table accordingly.</span></span> <span data-ttu-id="745a6-303">Zobacz Omówienie wymagań katalogu potoku w [wymagania dotyczące opracowywania potoku](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span><span class="sxs-lookup"><span data-stu-id="745a6-303">See the discussion of pipeline directory requirements in [Pipeline Development Requirements](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span></span>  
  
2.  <span data-ttu-id="745a6-304">Twórz rozwiązania Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="745a6-304">Build the Visual Studio solution.</span></span>  
  
3.  <span data-ttu-id="745a6-305">Sprawdź katalogów aplikacji i potoku, aby upewnić się, że zestawy zostały skopiowane do katalogu poprawny katalogów, a nie dodatkowe kopie zestawów zostały zainstalowane w folderach problem.</span><span class="sxs-lookup"><span data-stu-id="745a6-305">Check the application and pipeline directories to ensure that the assemblies were copied to the correct directories and that no extra copies of assemblies were installed in the wrong folders.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="745a6-306">Jeśli nie zmieniono **Kopiuj lokalnie** do **False** dla `Calc1AddInView` projektu odwołania w `AddInCalcV1` projektu, problemy kontekst modułu ładującego uniemożliwi dodatek znajdujących się.</span><span class="sxs-lookup"><span data-stu-id="745a6-306">If you did not change **Copy Local** to **False** for the `Calc1AddInView` project reference in the `AddInCalcV1` project, loader context problems will prevent the add-in from being located.</span></span>  
  
     <span data-ttu-id="745a6-307">Aby uzyskać informacji o wdrażaniu do potoku, zobacz [wymagania dotyczące opracowywania potoku](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span><span class="sxs-lookup"><span data-stu-id="745a6-307">For information about deploying to the pipeline, see [Pipeline Development Requirements](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span></span>  
  
## <a name="running-the-host-application"></a><span data-ttu-id="745a6-308">Uruchamianie aplikacji hosta</span><span class="sxs-lookup"><span data-stu-id="745a6-308">Running the Host Application</span></span>  
 <span data-ttu-id="745a6-309">Teraz można przystąpić do uruchamiania hosta i korzystać z dodatku.</span><span class="sxs-lookup"><span data-stu-id="745a6-309">You are now ready to run the host and interact with the add-in.</span></span>  
  
#### <a name="to-run-the-host-application"></a><span data-ttu-id="745a6-310">Aby uruchomić aplikację hosta</span><span class="sxs-lookup"><span data-stu-id="745a6-310">To run the host application</span></span>  
  
1.  <span data-ttu-id="745a6-311">W wierszu polecenia przejdź do katalogu aplikacji i uruchom aplikację hosta `Calc1Host.exe`.</span><span class="sxs-lookup"><span data-stu-id="745a6-311">At the command prompt, go to the application directory and run the host application, `Calc1Host.exe`.</span></span>  
  
2.  <span data-ttu-id="745a6-312">Host znajduje wszystkie dostępne dodatki dla jego typu i monit o wybranie dodatku.</span><span class="sxs-lookup"><span data-stu-id="745a6-312">The host finds all available add-ins of its type and prompts you to select an add-in.</span></span> <span data-ttu-id="745a6-313">Wprowadź **1** jedyną dostępną dodatku.</span><span class="sxs-lookup"><span data-stu-id="745a6-313">Enter **1** for the only available add-in.</span></span>  
  
3.  <span data-ttu-id="745a6-314">Wprowadź równania Kalkulator, taki jak **2 + 2**.</span><span class="sxs-lookup"><span data-stu-id="745a6-314">Enter an equation for the calculator, such as **2 + 2**.</span></span> <span data-ttu-id="745a6-315">Musi to być odstępy między liczb i operatora.</span><span class="sxs-lookup"><span data-stu-id="745a6-315">There must be spaces between the numbers and the operator.</span></span>  
  
4.  <span data-ttu-id="745a6-316">Typ **wyjść** i naciśnij klawisz **Enter** klawisz, aby zamknąć aplikację.</span><span class="sxs-lookup"><span data-stu-id="745a6-316">Type **exit** and press the **Enter** key to close the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="745a6-317">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="745a6-317">See Also</span></span>  
 [<span data-ttu-id="745a6-318">Przewodnik: Włączanie zgodności z poprzednimi wersjami w miarę zmieniania hosta</span><span class="sxs-lookup"><span data-stu-id="745a6-318">Walkthrough: Enabling Backward Compatibility as Your Host Changes</span></span>](https://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848)  
 [<span data-ttu-id="745a6-319">Wskazówki: Przekazywanie kolekcji między hostami i dodatkami</span><span class="sxs-lookup"><span data-stu-id="745a6-319">Walkthrough: Passing Collections Between Hosts and Add-Ins</span></span>](https://msdn.microsoft.com/library/b532c604-548e-4fab-b11c-377257dd0ee5)  
 [<span data-ttu-id="745a6-320">Wymagania dotyczące opracowywania potoku</span><span class="sxs-lookup"><span data-stu-id="745a6-320">Pipeline Development Requirements</span></span>](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5)  
 [<span data-ttu-id="745a6-321">Kontrakty, widoki i adaptery</span><span class="sxs-lookup"><span data-stu-id="745a6-321">Contracts, Views, and Adapters</span></span>](https://msdn.microsoft.com/library/a6460173-9507-4b87-8c07-d4ee245d715c)  
 [<span data-ttu-id="745a6-322">Opracowywanie potoku</span><span class="sxs-lookup"><span data-stu-id="745a6-322">Pipeline Development</span></span>](../../../docs/framework/add-ins/pipeline-development.md)
