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
ms.openlocfilehash: 292447fa3cf2dbad70dbfef32b7c184b250ed25e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32744827"
---
# <a name="walkthrough-creating-an-extensible-application"></a><span data-ttu-id="0b02d-102">Wskazówki: tworzenie aplikacji rozszerzalnej</span><span class="sxs-lookup"><span data-stu-id="0b02d-102">Walkthrough: Creating an Extensible Application</span></span>
<span data-ttu-id="0b02d-103">Ten przewodnik zawiera opis sposobu tworzenia potoku dodatku pełni prosty kalkulator funkcji.</span><span class="sxs-lookup"><span data-stu-id="0b02d-103">This walkthrough describes how to create a pipeline for an add-in that performs simple calculator functions.</span></span> <span data-ttu-id="0b02d-104">Nie wykazują rzeczywistych scenariuszy; zamiast go przedstawiono podstawowe funkcje potoku i jak dodatek może zapewnić usługi hosta.</span><span class="sxs-lookup"><span data-stu-id="0b02d-104">It does not demonstrate a real-world scenario; rather, it demonstrates the basic functionality of a pipeline and how an add-in can provide services for a host.</span></span>  
  
 <span data-ttu-id="0b02d-105">W tym przewodniku opisano następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="0b02d-105">This walkthrough describes the following tasks:</span></span>  
  
-   <span data-ttu-id="0b02d-106">Tworzenie rozwiązania Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0b02d-106">Creating a Visual Studio solution.</span></span>  
  
-   <span data-ttu-id="0b02d-107">Tworzenie potoku struktury katalogów.</span><span class="sxs-lookup"><span data-stu-id="0b02d-107">Creating the pipeline directory structure.</span></span>  
  
-   <span data-ttu-id="0b02d-108">Trwa tworzenie kontraktu i widoków.</span><span class="sxs-lookup"><span data-stu-id="0b02d-108">Creating the contract and views.</span></span>  
  
-   <span data-ttu-id="0b02d-109">Tworzenie Dodaj strony karty.</span><span class="sxs-lookup"><span data-stu-id="0b02d-109">Creating the add-in-side adapter.</span></span>  
  
-   <span data-ttu-id="0b02d-110">Tworzenie karty po stronie hosta.</span><span class="sxs-lookup"><span data-stu-id="0b02d-110">Creating the host-side adapter.</span></span>  
  
-   <span data-ttu-id="0b02d-111">Tworzenie hosta.</span><span class="sxs-lookup"><span data-stu-id="0b02d-111">Creating the host.</span></span>  
  
-   <span data-ttu-id="0b02d-112">Tworzenie dodatku.</span><span class="sxs-lookup"><span data-stu-id="0b02d-112">Creating the add-in.</span></span>  
  
-   <span data-ttu-id="0b02d-113">Wdrażanie potoku.</span><span class="sxs-lookup"><span data-stu-id="0b02d-113">Deploying the pipeline.</span></span>  
  
-   <span data-ttu-id="0b02d-114">Uruchomienie aplikacji hosta.</span><span class="sxs-lookup"><span data-stu-id="0b02d-114">Running the host application.</span></span>  
  
 <span data-ttu-id="0b02d-115">Tego potoku przekazuje tylko dla typów możliwych do serializacji (<xref:System.Double> i <xref:System.String>), między hostem a dodatku.</span><span class="sxs-lookup"><span data-stu-id="0b02d-115">This pipeline passes only serializable types (<xref:System.Double> and <xref:System.String>), between the host and the add-in.</span></span> <span data-ttu-id="0b02d-116">Na przykład pokazujący sposób przekazywania kolekcji typów złożonych danych zobacz [wskazówki: przekazywanie kolekcje między hostami i dodatki](http://msdn.microsoft.com/library/b532c604-548e-4fab-b11c-377257dd0ee5).</span><span class="sxs-lookup"><span data-stu-id="0b02d-116">For an example that shows how to pass collections of complex data types, see [Walkthrough: Passing Collections Between Hosts and Add-Ins](http://msdn.microsoft.com/library/b532c604-548e-4fab-b11c-377257dd0ee5).</span></span>  
  
 <span data-ttu-id="0b02d-117">Model obiektowy cztery operacje arytmetyczne definiuje kontrakt dla tego potoku: Dodawanie, odejmowanie mnożenia i dzielenia.</span><span class="sxs-lookup"><span data-stu-id="0b02d-117">The contract for this pipeline defines an object model of four arithmetic operations: add, subtract, multiply, and divide.</span></span> <span data-ttu-id="0b02d-118">Host udostępnia dodatek równości, aby obliczyć, takich jak 2 + 2 i dodatek zwraca wynik do hosta.</span><span class="sxs-lookup"><span data-stu-id="0b02d-118">The host provides the add-in with an equation to calculate, such as 2 + 2, and the add-in returns the result to the host.</span></span>  
  
 <span data-ttu-id="0b02d-119">W wersji 2 dodatku Kalkulator zapewnia możliwości bardziej obliczania i prezentuje przechowywania wersji.</span><span class="sxs-lookup"><span data-stu-id="0b02d-119">Version 2 of the calculator add-in provides more calculating possibilities and demonstrates versioning.</span></span> <span data-ttu-id="0b02d-120">Opisano w [wskazówki: Włączanie zgodności z poprzednimi wersjami jako Twoje zmiany hosta](http://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848).</span><span class="sxs-lookup"><span data-stu-id="0b02d-120">It is described in [Walkthrough: Enabling Backward Compatibility as Your Host Changes](http://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="0b02d-121">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="0b02d-121">Prerequisites</span></span>  
 <span data-ttu-id="0b02d-122">Potrzebne w tym przewodniku:</span><span class="sxs-lookup"><span data-stu-id="0b02d-122">You need the following to complete this walkthrough:</span></span>  
  
-   <span data-ttu-id="0b02d-123">Program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0b02d-123">Visual Studio.</span></span>  
  
## <a name="creating-a-visual-studio-solution"></a><span data-ttu-id="0b02d-124">Tworzenie rozwiązania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0b02d-124">Creating a Visual Studio Solution</span></span>  
 <span data-ttu-id="0b02d-125">Za pomocą rozwiązania w programie Visual Studio zawiera projekty segmentów potoku.</span><span class="sxs-lookup"><span data-stu-id="0b02d-125">Use a solution in Visual Studio to contain the projects of your pipeline segments.</span></span>  
  
#### <a name="to-create-the-pipeline-solution"></a><span data-ttu-id="0b02d-126">Tworzenie rozwiązań potoku</span><span class="sxs-lookup"><span data-stu-id="0b02d-126">To create the pipeline solution</span></span>  
  
1.  <span data-ttu-id="0b02d-127">W programie Visual Studio Utwórz nowy projekt o nazwie `Calc1Contract`.</span><span class="sxs-lookup"><span data-stu-id="0b02d-127">In Visual Studio, create a new project named `Calc1Contract`.</span></span> <span data-ttu-id="0b02d-128">Na podstawie **biblioteki klas** szablonu.</span><span class="sxs-lookup"><span data-stu-id="0b02d-128">Base it on the **Class Library** template.</span></span>  
  
2.  <span data-ttu-id="0b02d-129">Nazwa rozwiązania `CalculatorV1`.</span><span class="sxs-lookup"><span data-stu-id="0b02d-129">Name the solution `CalculatorV1`.</span></span>  
  
## <a name="creating-the-pipeline-directory-structure"></a><span data-ttu-id="0b02d-130">Tworzenie potoku struktury katalogów</span><span class="sxs-lookup"><span data-stu-id="0b02d-130">Creating the Pipeline Directory Structure</span></span>  
 <span data-ttu-id="0b02d-131">Model dodatku wymaga zestawy segmentów potoku do umieszczenia w strukturze określonego katalogu.</span><span class="sxs-lookup"><span data-stu-id="0b02d-131">The add-in model requires the pipeline segment assemblies to be placed in a specified directory structure.</span></span> <span data-ttu-id="0b02d-132">Aby uzyskać więcej informacji o strukturze potoku, zobacz [wymagania rozwój potoku](http://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span><span class="sxs-lookup"><span data-stu-id="0b02d-132">For more information about the pipeline structure, see [Pipeline Development Requirements](http://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span></span>  
  
#### <a name="to-create-the-pipeline-directory-structure"></a><span data-ttu-id="0b02d-133">Aby utworzyć struktury katalogu potoku</span><span class="sxs-lookup"><span data-stu-id="0b02d-133">To create the pipeline directory structure</span></span>  
  
1.  <span data-ttu-id="0b02d-134">Utwórz folder aplikacji dowolnego miejsca na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="0b02d-134">Create an application folder anywhere on your computer.</span></span>  
  
2.  <span data-ttu-id="0b02d-135">W tym folderze utwórz następującą strukturę:</span><span class="sxs-lookup"><span data-stu-id="0b02d-135">In that folder, create the following structure:</span></span>  
  
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
  
     <span data-ttu-id="0b02d-136">Nie jest konieczne umieszczanie potoku struktury folderów w folderze aplikacji; została ona wysłana tutaj wyłącznie dla wygody.</span><span class="sxs-lookup"><span data-stu-id="0b02d-136">It is not necessary to put the pipeline folder structure in your application folder; it is done here only for convenience.</span></span> <span data-ttu-id="0b02d-137">Na odpowiedni krok przewodnika wyjaśniono, jak zmienić kod, jeśli struktura folderów potoku jest w innej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="0b02d-137">At the appropriate step, the walkthrough explains how to change the code if the pipeline folder structure is in a different location.</span></span> <span data-ttu-id="0b02d-138">Zawiera omówienie wymagań katalogu potoku w [wymagania rozwój potoku](http://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span><span class="sxs-lookup"><span data-stu-id="0b02d-138">See the discussion of pipeline directory requirements in [Pipeline Development Requirements](http://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0b02d-139">`CalcV2` Folder nie jest używany w tym przewodniku; jest symbolem zastępczym dla [wskazówki: Włączanie zgodności z poprzednimi wersjami jako Twoje zmiany hosta](http://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848).</span><span class="sxs-lookup"><span data-stu-id="0b02d-139">The `CalcV2` folder is not used in this walkthrough; it is a placeholder for [Walkthrough: Enabling Backward Compatibility as Your Host Changes](http://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848).</span></span>  
  
## <a name="creating-the-contract-and-views"></a><span data-ttu-id="0b02d-140">Tworzenie kontraktu i widoków</span><span class="sxs-lookup"><span data-stu-id="0b02d-140">Creating the Contract and Views</span></span>  
 <span data-ttu-id="0b02d-141">Definiuje kontrakt segmentu dla tego potoku `ICalc1Contract` interfejs, który definiuje cztery metody: `add`, `subtract`, `multiply`, i `divide`.</span><span class="sxs-lookup"><span data-stu-id="0b02d-141">The contract segment for this pipeline defines the `ICalc1Contract` interface, which defines four methods: `add`, `subtract`, `multiply`, and `divide`.</span></span>  
  
#### <a name="to-create-the-contract"></a><span data-ttu-id="0b02d-142">Aby utworzyć kontrakt</span><span class="sxs-lookup"><span data-stu-id="0b02d-142">To create the contract</span></span>  
  
1.  <span data-ttu-id="0b02d-143">W rozwiązaniu Visual Studio o nazwie `CalculatorV1`, otwórz `Calc1Contract` projektu.</span><span class="sxs-lookup"><span data-stu-id="0b02d-143">In the Visual Studio solution named `CalculatorV1`, open the `Calc1Contract` project.</span></span>  
  
2.  <span data-ttu-id="0b02d-144">W **Eksploratora rozwiązań**, dodaj odwołania do następujących zestawów do `Calc1Contract` projektu:</span><span class="sxs-lookup"><span data-stu-id="0b02d-144">In **Solution Explorer**, add references to the following assemblies to the `Calc1Contract` project:</span></span>  
  
     <span data-ttu-id="0b02d-145">System.AddIn.Contract.dll</span><span class="sxs-lookup"><span data-stu-id="0b02d-145">System.AddIn.Contract.dll</span></span>  
  
     <span data-ttu-id="0b02d-146">System.AddIn.dll</span><span class="sxs-lookup"><span data-stu-id="0b02d-146">System.AddIn.dll</span></span>  
  
3.  <span data-ttu-id="0b02d-147">W **Eksploratora rozwiązań**, Wyklucz domyślną klasę, który jest dodawany do nowego **biblioteki klas** projektów.</span><span class="sxs-lookup"><span data-stu-id="0b02d-147">In **Solution Explorer**, exclude the default class that is added to new **Class Library** projects.</span></span>  
  
4.  <span data-ttu-id="0b02d-148">W **Eksploratora rozwiązań**, Dodaj nowy element do projektu przy użyciu **interfejsu** szablonu.</span><span class="sxs-lookup"><span data-stu-id="0b02d-148">In **Solution Explorer**, add a new item to the project, using the **Interface** template.</span></span> <span data-ttu-id="0b02d-149">W **Dodaj nowy element** okno dialogowe, nazwa interfejsu `ICalc1Contract`.</span><span class="sxs-lookup"><span data-stu-id="0b02d-149">In the **Add New Item** dialog box, name the interface `ICalc1Contract`.</span></span>  
  
5.  <span data-ttu-id="0b02d-150">W pliku interfejsu dodać odwołania do przestrzeni nazw do <xref:System.AddIn.Contract> i <xref:System.AddIn.Pipeline>.</span><span class="sxs-lookup"><span data-stu-id="0b02d-150">In the interface file, add namespace references to <xref:System.AddIn.Contract> and <xref:System.AddIn.Pipeline>.</span></span>  
  
6.  <span data-ttu-id="0b02d-151">Użyć poniższego kodu, aby ukończyć ten segment kontraktu.</span><span class="sxs-lookup"><span data-stu-id="0b02d-151">Use the following code to complete this contract segment.</span></span> <span data-ttu-id="0b02d-152">Należy pamiętać, że ten interfejs musi mieć <xref:System.AddIn.Pipeline.AddInContractAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="0b02d-152">Note that this interface must have the <xref:System.AddIn.Pipeline.AddInContractAttribute> attribute.</span></span>  
  
     [!code-csharp[AddInP1Contract#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1Contract/cs/ICalc1Contract.cs#1)]
     [!code-vb[AddInP1Contract#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1Contract/vb/ICalc1Contract.vb#1)]  
  
7.  <span data-ttu-id="0b02d-153">Opcjonalnie tworzenie rozwiązań programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0b02d-153">Optionally, build the Visual Studio solution.</span></span> <span data-ttu-id="0b02d-154">Nie można uruchomić do momentu ostatnia procedura, ale skompilowanie go po każdej procedury powoduje, że każdy projekt ma Popraw.</span><span class="sxs-lookup"><span data-stu-id="0b02d-154">The solution cannot be run until the final procedure, but building it after each procedure ensures that each project is correct.</span></span>  
  
 <span data-ttu-id="0b02d-155">Ponieważ widok dodatku i host Widok dodatku zwykle mają ten sam kod, szczególnie w pierwszej wersji dodatku, można jednak łatwo tworzyć widoki w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="0b02d-155">Because the add-in view and the host view of the add-in usually have the same code, especially in the first version of an add-in, you can easily create the views at the same time.</span></span> <span data-ttu-id="0b02d-156">Różnią się tylko jeden składnik: Wyświetl dodatek wymaga <xref:System.AddIn.Pipeline.AddInBaseAttribute> atrybutu, podczas gdy widoku hosta dodatku nie wymagają żadnych atrybutów.</span><span class="sxs-lookup"><span data-stu-id="0b02d-156">They differ by only one factor: the add-in view requires the <xref:System.AddIn.Pipeline.AddInBaseAttribute> attribute, while the host view of the add-in does not require any attributes.</span></span>  
  
#### <a name="to-create-the-add-in-view"></a><span data-ttu-id="0b02d-157">Aby utworzyć widok dodatku</span><span class="sxs-lookup"><span data-stu-id="0b02d-157">To create the add-in view</span></span>  
  
1.  <span data-ttu-id="0b02d-158">Dodawanie nowego projektu o nazwie `Calc1AddInView` do `CalculatorV1` rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="0b02d-158">Add a new project named `Calc1AddInView` to the `CalculatorV1` solution.</span></span> <span data-ttu-id="0b02d-159">Na podstawie **biblioteki klas** szablonu.</span><span class="sxs-lookup"><span data-stu-id="0b02d-159">Base it on the **Class Library** template.</span></span>  
  
2.  <span data-ttu-id="0b02d-160">W **Eksploratora rozwiązań**, Dodaj odwołanie do System.AddIn.dll do `Calc1AddInView` projektu.</span><span class="sxs-lookup"><span data-stu-id="0b02d-160">In **Solution Explorer**, add a reference to System.AddIn.dll to the `Calc1AddInView` project.</span></span>  
  
3.  <span data-ttu-id="0b02d-161">W **Eksploratora rozwiązań**, Wyklucz domyślną klasę, który jest dodawany do nowego **biblioteki klas** projektów, a następnie dodaj nowy element do projektu przy użyciu **interfejsu** szablonu.</span><span class="sxs-lookup"><span data-stu-id="0b02d-161">In **Solution Explorer**, exclude the default class that is added to new **Class Library** projects, and add a new item to the project, using the **Interface** template.</span></span> <span data-ttu-id="0b02d-162">W **Dodaj nowy element** okno dialogowe, nazwa interfejsu `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="0b02d-162">In the **Add New Item** dialog box, name the interface `ICalculator`.</span></span>  
  
4.  <span data-ttu-id="0b02d-163">W pliku interfejs Dodaj odwołanie do przestrzeni nazw <xref:System.AddIn.Pipeline>.</span><span class="sxs-lookup"><span data-stu-id="0b02d-163">In the interface file, add a namespace reference to <xref:System.AddIn.Pipeline>.</span></span>  
  
5.  <span data-ttu-id="0b02d-164">Aby ukończyć ten widok dodatku, należy użyć poniższego kodu.</span><span class="sxs-lookup"><span data-stu-id="0b02d-164">Use the following code to complete this add-in view.</span></span> <span data-ttu-id="0b02d-165">Należy pamiętać, że ten interfejs musi mieć <xref:System.AddIn.Pipeline.AddInBaseAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="0b02d-165">Note that this interface must have the <xref:System.AddIn.Pipeline.AddInBaseAttribute> attribute.</span></span>  
  
     [!code-csharp[AddInP1AddInViews#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInViews/cs/Calc1AddInView.cs#1)]
     [!code-vb[AddInP1AddInViews#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInViews/vb/Calc1AddInView.vb#1)]  
  
6.  <span data-ttu-id="0b02d-166">Opcjonalnie tworzenie rozwiązań programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0b02d-166">Optionally, build the Visual Studio solution.</span></span>  
  
#### <a name="to-create-the-host-view-of-the-add-in"></a><span data-ttu-id="0b02d-167">Aby utworzyć widok hosta dodatku</span><span class="sxs-lookup"><span data-stu-id="0b02d-167">To create the host view of the add-in</span></span>  
  
1.  <span data-ttu-id="0b02d-168">Dodawanie nowego projektu o nazwie `Calc1HVA` do `CalculatorV1` rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="0b02d-168">Add a new project named `Calc1HVA` to the `CalculatorV1` solution.</span></span> <span data-ttu-id="0b02d-169">Na podstawie **biblioteki klas** szablonu.</span><span class="sxs-lookup"><span data-stu-id="0b02d-169">Base it on the **Class Library** template.</span></span>  
  
2.  <span data-ttu-id="0b02d-170">W **Eksploratora rozwiązań**, Wyklucz domyślną klasę, który jest dodawany do nowego **biblioteki klas** projektów, a następnie dodaj nowy element do projektu przy użyciu **interfejsu** szablonu.</span><span class="sxs-lookup"><span data-stu-id="0b02d-170">In **Solution Explorer**, exclude the default class that is added to new **Class Library** projects, and add a new item to the project, using the **Interface** template.</span></span> <span data-ttu-id="0b02d-171">W **Dodaj nowy element** okno dialogowe, nazwa interfejsu `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="0b02d-171">In the **Add New Item** dialog box, name the interface `ICalculator`.</span></span>  
  
3.  <span data-ttu-id="0b02d-172">W pliku interfejsu należy użyć poniższego kodu do wykonania widoku hosta dodatku.</span><span class="sxs-lookup"><span data-stu-id="0b02d-172">In the interface file, use the following code to complete the host view of the add-in.</span></span>  
  
     [!code-csharp[AddInP1HVA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1HVA/cs/calc1hva.cs#1)]
     [!code-vb[AddInP1HVA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1HVA/vb/Calc1HVA.vb#1)]  
  
4.  <span data-ttu-id="0b02d-173">Opcjonalnie tworzenie rozwiązań programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0b02d-173">Optionally, build the Visual Studio solution.</span></span>  
  
## <a name="creating-the-add-in-side-adapter"></a><span data-ttu-id="0b02d-174">Tworzenie karty Dodaj strony</span><span class="sxs-lookup"><span data-stu-id="0b02d-174">Creating the Add-in-side Adapter</span></span>  
 <span data-ttu-id="0b02d-175">Ta karta dodać stronie składa się z jednej karty widoku do kontraktu.</span><span class="sxs-lookup"><span data-stu-id="0b02d-175">This add-in-side adapter consists of one view-to-contract adapter.</span></span> <span data-ttu-id="0b02d-176">Ten segment potoku konwertuje typy w widoku Dodaj umowy.</span><span class="sxs-lookup"><span data-stu-id="0b02d-176">This pipeline segment converts the types from the add-in view to the contract.</span></span>  
  
 <span data-ttu-id="0b02d-177">W tym potoku dodatku udostępnia usługę na hoście, a typy przepływać z dodatku do hosta.</span><span class="sxs-lookup"><span data-stu-id="0b02d-177">In this pipeline, the add-in provides a service to the host, and the types flow from the add-in to the host.</span></span> <span data-ttu-id="0b02d-178">Ponieważ żaden z typów przepływać z hosta do dodatku, masz nie zawiera karty Widok kontraktów po stronie dodatku tego potoku.</span><span class="sxs-lookup"><span data-stu-id="0b02d-178">Because no types flow from the host to the add-in, you do not have to include a contract-to-view adapter on the add-in side of this pipeline.</span></span>  
  
#### <a name="to-create-the-add-in-side-adapter"></a><span data-ttu-id="0b02d-179">Aby utworzyć karty Dodaj strony</span><span class="sxs-lookup"><span data-stu-id="0b02d-179">To create the add-in-side adapter</span></span>  
  
1.  <span data-ttu-id="0b02d-180">Dodawanie nowego projektu o nazwie `Calc1AddInSideAdapter` do `CalculatorV1` rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="0b02d-180">Add a new project named `Calc1AddInSideAdapter` to the `CalculatorV1` solution.</span></span> <span data-ttu-id="0b02d-181">Na podstawie **biblioteki klas** szablonu.</span><span class="sxs-lookup"><span data-stu-id="0b02d-181">Base it on the **Class Library** template.</span></span>  
  
2.  <span data-ttu-id="0b02d-182">W **Eksploratora rozwiązań**, dodaj odwołania do następujących zestawów do `Calc1AddInSideAdapter` projektu:</span><span class="sxs-lookup"><span data-stu-id="0b02d-182">In **Solution Explorer**, add references to the following assemblies to the `Calc1AddInSideAdapter` project:</span></span>  
  
     <span data-ttu-id="0b02d-183">System.AddIn.dll</span><span class="sxs-lookup"><span data-stu-id="0b02d-183">System.AddIn.dll</span></span>  
  
     <span data-ttu-id="0b02d-184">System.AddIn.Contract.dll</span><span class="sxs-lookup"><span data-stu-id="0b02d-184">System.AddIn.Contract.dll</span></span>  
  
3.  <span data-ttu-id="0b02d-185">Dodawanie odwołań do projektów dla segmentów potoku sąsiadujących projektu:</span><span class="sxs-lookup"><span data-stu-id="0b02d-185">Add project references to the projects for the adjacent pipeline segments:</span></span>  
  
     `Calc1AddInView`  
  
     `Calc1Contract`  
  
4.  <span data-ttu-id="0b02d-186">Wybierz odwołanie do każdego projektu, a następnie w **właściwości** ustawić **Kopiuj lokalnie** do **False**.</span><span class="sxs-lookup"><span data-stu-id="0b02d-186">Select each project reference, and in **Properties** set **Copy Local** to **False**.</span></span> <span data-ttu-id="0b02d-187">W języku Visual Basic, użyj **odwołania** karty **właściwości projektu** można ustawić **Kopiuj lokalnie** do **False** projektu dwa odwołania.</span><span class="sxs-lookup"><span data-stu-id="0b02d-187">In Visual Basic, use the **References** tab of **Project Properties** to set **Copy Local** to **False** for the two project references.</span></span>  
  
5.  <span data-ttu-id="0b02d-188">Zmień nazwę projektu domyślną klasę `CalculatorViewToContractAddInSideAdapter`.</span><span class="sxs-lookup"><span data-stu-id="0b02d-188">Rename the project's default class `CalculatorViewToContractAddInSideAdapter`.</span></span>  
  
6.  <span data-ttu-id="0b02d-189">Plik klasy, dodaj odwołania do przestrzeni nazw do <xref:System.AddIn.Pipeline>.</span><span class="sxs-lookup"><span data-stu-id="0b02d-189">In the class file, add namespace references to <xref:System.AddIn.Pipeline>.</span></span>  
  
7.  <span data-ttu-id="0b02d-190">Plik klasy, dodaj odwołania do przestrzeni nazw dla sąsiadujących segmentów: `CalcAddInViews` i `CalculatorContracts`.</span><span class="sxs-lookup"><span data-stu-id="0b02d-190">In the class file, add namespace references for the adjacent segments: `CalcAddInViews` and `CalculatorContracts`.</span></span> <span data-ttu-id="0b02d-191">(W języku Visual Basic są te odwołania do przestrzeni nazw `Calc1AddInView.CalcAddInViews` i `Calc1Contract.CalculatorContracts`, chyba że wyłączono domyślne obszary nazw w projektach Visual Basic.)</span><span class="sxs-lookup"><span data-stu-id="0b02d-191">(In Visual Basic, these namespace references are `Calc1AddInView.CalcAddInViews` and `Calc1Contract.CalculatorContracts`, unless you have turned off the default namespaces in your Visual Basic projects.)</span></span>  
  
8.  <span data-ttu-id="0b02d-192">Zastosuj <xref:System.AddIn.Pipeline.AddInAdapterAttribute> atrybutu `CalculatorViewToContractAddInSideAdapter` klasy, aby zidentyfikować go jako Dodaj strony karty.</span><span class="sxs-lookup"><span data-stu-id="0b02d-192">Apply the <xref:System.AddIn.Pipeline.AddInAdapterAttribute> attribute to the `CalculatorViewToContractAddInSideAdapter` class, to identify it as the add-in-side adapter.</span></span>  
  
9. <span data-ttu-id="0b02d-193">Należy `CalculatorViewToContractAddInSideAdapter` klasa dziedziczy <xref:System.AddIn.Pipeline.ContractBase>, który udostępnia domyślną implementację <xref:System.AddIn.Contract.IContract> interfejsu i implementować interfejs kontraktu dla potoku, `ICalc1Contract`.</span><span class="sxs-lookup"><span data-stu-id="0b02d-193">Make the `CalculatorViewToContractAddInSideAdapter` class inherit <xref:System.AddIn.Pipeline.ContractBase>, which provides a default implementation of the <xref:System.AddIn.Contract.IContract> interface, and implement the contract interface for the pipeline, `ICalc1Contract`.</span></span>  
  
10. <span data-ttu-id="0b02d-194">Dodaj publiczny konstruktor, który akceptuje `ICalculator`, przechowuje go w pole prywatne i wywołuje konstruktor klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="0b02d-194">Add a public constructor that accepts an `ICalculator`, caches it in a private field, and calls the base class constructor.</span></span>  
  
11. <span data-ttu-id="0b02d-195">Aby zaimplementować członków `ICalc1Contract`, po prostu Wywołaj odpowiednie elementy członkowskie z `ICalculator` wystąpienia, który jest przekazywany do konstruktora, a następnie zwracają wyniki.</span><span class="sxs-lookup"><span data-stu-id="0b02d-195">To implement the members of `ICalc1Contract`, simply call the corresponding members of the `ICalculator` instance that is passed to the constructor, and return the results.</span></span> <span data-ttu-id="0b02d-196">To dostosowuje widok (`ICalculator`) do kontraktu (`ICalc1Contract`).</span><span class="sxs-lookup"><span data-stu-id="0b02d-196">This adapts the view (`ICalculator`) to the contract (`ICalc1Contract`).</span></span>  
  
     <span data-ttu-id="0b02d-197">Poniższy kod przedstawia ukończone karty Dodaj strony.</span><span class="sxs-lookup"><span data-stu-id="0b02d-197">The following code shows the completed add-in-side adapter.</span></span>  
  
     [!code-csharp[AddInP1AddInSideAdapters#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInSideAdapters/cs/Calc1ViewToContractAddInSideAdapter.cs#1)]
     [!code-vb[AddInP1AddInSideAdapters#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInSideAdapters/vb/Calc1ViewToContractAddInSideAdapter.vb#1)]  
  
12. <span data-ttu-id="0b02d-198">Opcjonalnie tworzenie rozwiązań programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0b02d-198">Optionally, build the Visual Studio solution.</span></span>  
  
## <a name="creating-the-host-side-adapter"></a><span data-ttu-id="0b02d-199">Tworzenie karty po stronie hosta</span><span class="sxs-lookup"><span data-stu-id="0b02d-199">Creating the Host-side Adapter</span></span>  
 <span data-ttu-id="0b02d-200">Ta karta po stronie hosta składa się z jednej karty kontraktu do widoku.</span><span class="sxs-lookup"><span data-stu-id="0b02d-200">This host-side adapter consists of one contract-to-view adapter.</span></span> <span data-ttu-id="0b02d-201">Ten segment dostosowuje kontraktu do widoku hosta dodatku.</span><span class="sxs-lookup"><span data-stu-id="0b02d-201">This segment adapts the contract to the host view of the add-in.</span></span>  
  
 <span data-ttu-id="0b02d-202">W tym potoku dodatku udostępnia usługę do hosta i przepływ typów z dodatku do hosta.</span><span class="sxs-lookup"><span data-stu-id="0b02d-202">In this pipeline, the add-in provides a service to the host and the types flow from the add-in to the host.</span></span> <span data-ttu-id="0b02d-203">Ponieważ żaden z typów przepływać z hosta do dodatku, masz nie zawiera karty widoku do kontraktu.</span><span class="sxs-lookup"><span data-stu-id="0b02d-203">Because no types flow from the host to the add-in, you do not have to include a view-to-contract adapter.</span></span>  
  
 <span data-ttu-id="0b02d-204">Aby zaimplementować Zarządzanie okresem istnienia, należy użyć <xref:System.AddIn.Pipeline.ContractHandle> obiekt można dołączyć do kontraktu tokenu okresu istnienia.</span><span class="sxs-lookup"><span data-stu-id="0b02d-204">To implement lifetime management, use a <xref:System.AddIn.Pipeline.ContractHandle> object to attach a lifetime token to the contract.</span></span> <span data-ttu-id="0b02d-205">Odwołanie do tego dojścia muszą zapewnić, aby zarządzanie okresem istnienia do pracy.</span><span class="sxs-lookup"><span data-stu-id="0b02d-205">You must keep a reference to this handle in order for lifetime management to work.</span></span> <span data-ttu-id="0b02d-206">Po zastosowaniu token nie dodatkowego programowania jest wymagana, ponieważ system dodatku można zlikwidować obiektów gdy nie są używane i udostępnienia ich do pamięci.</span><span class="sxs-lookup"><span data-stu-id="0b02d-206">After the token is applied, no additional programming is required because the add-in system can dispose of objects when they are no longer being used and make them available for garbage collection.</span></span> <span data-ttu-id="0b02d-207">Aby uzyskać więcej informacji, zobacz [Zarządzanie okresem istnienia](http://msdn.microsoft.com/library/57a9c87e-394c-4fef-89f2-aa4223a2aeb5).</span><span class="sxs-lookup"><span data-stu-id="0b02d-207">For more information, see [Lifetime Management](http://msdn.microsoft.com/library/57a9c87e-394c-4fef-89f2-aa4223a2aeb5).</span></span>  
  
#### <a name="to-create-the-host-side-adapter"></a><span data-ttu-id="0b02d-208">Aby utworzyć karty po stronie hosta</span><span class="sxs-lookup"><span data-stu-id="0b02d-208">To create the host-side adapter</span></span>  
  
1.  <span data-ttu-id="0b02d-209">Dodawanie nowego projektu o nazwie `Calc1HostSideAdapter` do `CalculatorV1` rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="0b02d-209">Add a new project named `Calc1HostSideAdapter` to the `CalculatorV1` solution.</span></span> <span data-ttu-id="0b02d-210">Na podstawie **biblioteki klas** szablonu.</span><span class="sxs-lookup"><span data-stu-id="0b02d-210">Base it on the **Class Library** template.</span></span>  
  
2.  <span data-ttu-id="0b02d-211">W **Eksploratora rozwiązań**, dodaj odwołania do następujących zestawów do `Calc1HostSideAdapter` projektu:</span><span class="sxs-lookup"><span data-stu-id="0b02d-211">In **Solution Explorer**, add references to the following assemblies to the `Calc1HostSideAdapter` project:</span></span>  
  
     <span data-ttu-id="0b02d-212">System.AddIn.dll</span><span class="sxs-lookup"><span data-stu-id="0b02d-212">System.AddIn.dll</span></span>  
  
     <span data-ttu-id="0b02d-213">System.AddIn.Contract.dll</span><span class="sxs-lookup"><span data-stu-id="0b02d-213">System.AddIn.Contract.dll</span></span>  
  
3.  <span data-ttu-id="0b02d-214">Dodawanie odwołań do projektów dla sąsiadujących segmentów projektu:</span><span class="sxs-lookup"><span data-stu-id="0b02d-214">Add project references to the projects for the adjacent segments:</span></span>  
  
     `Calc1Contract`  
  
     `Calc1HVA`  
  
4.  <span data-ttu-id="0b02d-215">Wybierz odwołanie do każdego projektu, a następnie w **właściwości** ustawić **Kopiuj lokalnie** do **False**.</span><span class="sxs-lookup"><span data-stu-id="0b02d-215">Select each project reference, and in **Properties** set **Copy Local** to **False**.</span></span> <span data-ttu-id="0b02d-216">W języku Visual Basic, użyj **odwołania** karty **właściwości projektu** można ustawić **Kopiuj lokalnie** do **False** projektu dwa odwołania.</span><span class="sxs-lookup"><span data-stu-id="0b02d-216">In Visual Basic, use the **References** tab of **Project Properties** to set **Copy Local** to **False** for the two project references.</span></span>  
  
5.  <span data-ttu-id="0b02d-217">Zmień nazwę projektu domyślną klasę `CalculatorContractToViewHostSideAdapter`.</span><span class="sxs-lookup"><span data-stu-id="0b02d-217">Rename the project's default class `CalculatorContractToViewHostSideAdapter`.</span></span>  
  
6.  <span data-ttu-id="0b02d-218">Plik klasy, dodaj odwołania do przestrzeni nazw do <xref:System.AddIn.Pipeline>.</span><span class="sxs-lookup"><span data-stu-id="0b02d-218">In the class file, add namespace references to <xref:System.AddIn.Pipeline>.</span></span>  
  
7.  <span data-ttu-id="0b02d-219">Plik klasy, dodaj odwołania do przestrzeni nazw dla sąsiadujących segmentów: `CalcHVAs` i `CalculatorContracts`.</span><span class="sxs-lookup"><span data-stu-id="0b02d-219">In the class file, add namespace references for the adjacent segments: `CalcHVAs` and `CalculatorContracts`.</span></span> <span data-ttu-id="0b02d-220">(W języku Visual Basic są te odwołania do przestrzeni nazw `Calc1HVA.CalcHVAs` i `Calc1Contract.CalculatorContracts`, chyba że wyłączono domyślne obszary nazw w projektach Visual Basic.)</span><span class="sxs-lookup"><span data-stu-id="0b02d-220">(In Visual Basic, these namespace references are `Calc1HVA.CalcHVAs` and `Calc1Contract.CalculatorContracts`, unless you have turned off the default namespaces in your Visual Basic projects.)</span></span>  
  
8.  <span data-ttu-id="0b02d-221">Zastosuj <xref:System.AddIn.Pipeline.HostAdapterAttribute> atrybutu `CalculatorContractToViewHostSideAdapter` klasy, aby zidentyfikować go jako segment karty po stronie hosta.</span><span class="sxs-lookup"><span data-stu-id="0b02d-221">Apply the <xref:System.AddIn.Pipeline.HostAdapterAttribute> attribute to the `CalculatorContractToViewHostSideAdapter` class, to identify it as the host-side adapter segment.</span></span>  
  
9. <span data-ttu-id="0b02d-222">Wprowadź `CalculatorContractToViewHostSideAdapter` klasa implementuje interfejs, który reprezentuje widoku hosta dodatku: `Calc1HVAs.ICalculator` (`Calc1HVA.CalcHVAs.ICalculator` w języku Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="0b02d-222">Make the `CalculatorContractToViewHostSideAdapter` class implement the interface that represents the host view of the add-in: `Calc1HVAs.ICalculator` (`Calc1HVA.CalcHVAs.ICalculator` in Visual Basic).</span></span>  
  
10. <span data-ttu-id="0b02d-223">Dodaj publicznego konstruktora akceptującego typ kontraktu potoku `ICalc1Contract`.</span><span class="sxs-lookup"><span data-stu-id="0b02d-223">Add a public constructor that accepts the pipeline contract type, `ICalc1Contract`.</span></span> <span data-ttu-id="0b02d-224">Konstruktor musi pamięci podręcznej odwołanie do kontraktu.</span><span class="sxs-lookup"><span data-stu-id="0b02d-224">The constructor must cache the reference to the contract.</span></span> <span data-ttu-id="0b02d-225">Należy także utworzyć i pamięci podręcznej nowy <xref:System.AddIn.Pipeline.ContractHandle> kontraktu, do zarządzania przez czas ich istnienia dodatku.</span><span class="sxs-lookup"><span data-stu-id="0b02d-225">It must also create and cache a new <xref:System.AddIn.Pipeline.ContractHandle> for the contract, to manage the lifetime of the add-in.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="0b02d-226"><xref:System.AddIn.Pipeline.ContractHandle> Jest najważniejszym czynnikiem umożliwiającym zarządzanie okresem istnienia.</span><span class="sxs-lookup"><span data-stu-id="0b02d-226">The <xref:System.AddIn.Pipeline.ContractHandle> is critical to lifetime management.</span></span> <span data-ttu-id="0b02d-227">Jeśli nie zostanie utrzymywać odwołania do <xref:System.AddIn.Pipeline.ContractHandle> obiektu, wyrzucanie elementów bezużytecznych spowoduje jego odzyskanie i potoku zostanie zamknięty, gdy program nie oczekuje.</span><span class="sxs-lookup"><span data-stu-id="0b02d-227">If you fail to keep a reference to the <xref:System.AddIn.Pipeline.ContractHandle> object, garbage collection will reclaim it, and the pipeline will shut down when your program does not expect it.</span></span> <span data-ttu-id="0b02d-228">Może to prowadzić do błędów, które są trudne do diagnozowania, takich jak <xref:System.AppDomainUnloadedException>.</span><span class="sxs-lookup"><span data-stu-id="0b02d-228">This can lead to errors that are difficult to diagnose, such as <xref:System.AppDomainUnloadedException>.</span></span> <span data-ttu-id="0b02d-229">Zamknięcie jest normalne etap życia potoku, nie istnieje sposób zarządzania okres istnienia kodu wykrywa, że ten stan jest błąd.</span><span class="sxs-lookup"><span data-stu-id="0b02d-229">Shutdown is a normal stage in the life of a pipeline, so there is no way for the lifetime management code to detect that this condition is an error.</span></span>  
  
11. <span data-ttu-id="0b02d-230">Aby zaimplementować członków `ICalculator`, po prostu Wywołaj odpowiednie elementy członkowskie z `ICalc1Contract` wystąpienia, który jest przekazywany do konstruktora, a następnie zwracają wyniki.</span><span class="sxs-lookup"><span data-stu-id="0b02d-230">To implement the members of `ICalculator`, simply call the corresponding members of the `ICalc1Contract` instance that is passed to the constructor, and return the results.</span></span> <span data-ttu-id="0b02d-231">Dostosowuje to kontrakt (`ICalc1Contract`) do widoku (`ICalculator`).</span><span class="sxs-lookup"><span data-stu-id="0b02d-231">This adapts the contract (`ICalc1Contract`) to the view (`ICalculator`).</span></span>  
  
     <span data-ttu-id="0b02d-232">Poniższy kod przedstawia ukończone karty po stronie hosta.</span><span class="sxs-lookup"><span data-stu-id="0b02d-232">The following code shows the completed host-side adapter.</span></span>  
  
     [!code-csharp[AddInP1HostSideAdapters#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1HostSideAdapters/cs/Calc1ContractToViewHostSideAdapter.cs#1)]
     [!code-vb[AddInP1HostSideAdapters#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1HostSideAdapters/vb/Calc1ContractToViewHostSideAdapter.vb#1)]  
  
12. <span data-ttu-id="0b02d-233">Opcjonalnie tworzenie rozwiązań programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0b02d-233">Optionally, build the Visual Studio solution.</span></span>  
  
## <a name="creating-the-host"></a><span data-ttu-id="0b02d-234">Tworzenie hosta</span><span class="sxs-lookup"><span data-stu-id="0b02d-234">Creating the Host</span></span>  
 <span data-ttu-id="0b02d-235">Aplikacja hosta wchodzi w interakcję z dodatku za pośrednictwem widoku hosta dodatku.</span><span class="sxs-lookup"><span data-stu-id="0b02d-235">A host application interacts with the add-in through the host view of the add-in.</span></span> <span data-ttu-id="0b02d-236">Używa dodatku odnajdywania aktywacji metody i udostępniane przez <xref:System.AddIn.Hosting.AddInStore> i <xref:System.AddIn.Hosting.AddInToken> klasy wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="0b02d-236">It uses add-in discovery and activation methods provided by the <xref:System.AddIn.Hosting.AddInStore> and <xref:System.AddIn.Hosting.AddInToken> classes to do the following:</span></span>  
  
-   <span data-ttu-id="0b02d-237">Aktualizacja pamięci podręcznej informacji o potoku i dodatku.</span><span class="sxs-lookup"><span data-stu-id="0b02d-237">Update the cache of pipeline and add-in information.</span></span>  
  
-   <span data-ttu-id="0b02d-238">Znajdź dodatki typu widoku hosta `ICalculator`, w katalogu głównym określonej potoku.</span><span class="sxs-lookup"><span data-stu-id="0b02d-238">Find add-ins of the host view type, `ICalculator`, under the specified pipeline root directory.</span></span>  
  
-   <span data-ttu-id="0b02d-239">Monituj użytkownika do określenia, które dodatku do użycia.</span><span class="sxs-lookup"><span data-stu-id="0b02d-239">Prompt the user to specify which add-in to use.</span></span>  
  
-   <span data-ttu-id="0b02d-240">Aktywuj wybrany dodatek w nowej domenie z poziomem zaufania zabezpieczeń określonych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0b02d-240">Activate the selected add-in in a new application domain with a specified security trust level.</span></span>  
  
-   <span data-ttu-id="0b02d-241">Uruchom niestandardowego `RunCalculator` metodę, która wywołuje metody dodatku dla określonych w widoku hosta dodatku.</span><span class="sxs-lookup"><span data-stu-id="0b02d-241">Run the custom `RunCalculator` method, which calls the add-in's methods as specified by the host view of the add-in.</span></span>  
  
#### <a name="to-create-the-host"></a><span data-ttu-id="0b02d-242">Aby utworzyć hosta</span><span class="sxs-lookup"><span data-stu-id="0b02d-242">To create the host</span></span>  
  
1.  <span data-ttu-id="0b02d-243">Dodawanie nowego projektu o nazwie `Calc1Host` do `CalculatorV1` rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="0b02d-243">Add a new project named `Calc1Host` to the `CalculatorV1` solution.</span></span> <span data-ttu-id="0b02d-244">Na podstawie **aplikacji konsoli** szablonu.</span><span class="sxs-lookup"><span data-stu-id="0b02d-244">Base it on the **Console Application** template.</span></span>  
  
2.  <span data-ttu-id="0b02d-245">W **Eksploratora rozwiązań**, Dodaj odwołanie do zestawu System.AddIn.dll do `Calc1Host` projektu.</span><span class="sxs-lookup"><span data-stu-id="0b02d-245">In **Solution Explorer**, add a reference to the System.AddIn.dll assembly to the `Calc1Host` project.</span></span>  
  
3.  <span data-ttu-id="0b02d-246">Dodaj odwołanie projektu do `Calc1HVA` projektu.</span><span class="sxs-lookup"><span data-stu-id="0b02d-246">Add a project reference to the `Calc1HVA` project.</span></span> <span data-ttu-id="0b02d-247">Wybierz odwołanie do projektu i **właściwości** ustawić **Kopiuj lokalnie** do **False**.</span><span class="sxs-lookup"><span data-stu-id="0b02d-247">Select the project reference, and in **Properties** set **Copy Local** to **False**.</span></span> <span data-ttu-id="0b02d-248">W języku Visual Basic, użyj **odwołania** karcie **właściwości projektu** można ustawić **Kopiuj lokalnie** do **False**.</span><span class="sxs-lookup"><span data-stu-id="0b02d-248">In Visual Basic, use the **References** tab of **Project Properties** to set **Copy Local** to **False**.</span></span>  
  
4.  <span data-ttu-id="0b02d-249">Zmień nazwę pliku klasy (moduł w języku Visual Basic) `MathHost1`.</span><span class="sxs-lookup"><span data-stu-id="0b02d-249">Rename the class file (module in Visual Basic) `MathHost1`.</span></span>  
  
5.  <span data-ttu-id="0b02d-250">W języku Visual Basic, użyj **aplikacji** karcie **właściwości projektu** okno dialogowe, aby ustawić **obiekt uruchomieniowy** do **Sub Main**.</span><span class="sxs-lookup"><span data-stu-id="0b02d-250">In Visual Basic, use the **Application** tab of the **Project Properties** dialog box to set **Startup object** to **Sub Main**.</span></span>  
  
6.  <span data-ttu-id="0b02d-251">W pliku klasę lub moduł, Dodaj odwołanie do przestrzeni nazw <xref:System.AddIn.Hosting>.</span><span class="sxs-lookup"><span data-stu-id="0b02d-251">In the class or module file, add a namespace reference to <xref:System.AddIn.Hosting>.</span></span>  
  
7.  <span data-ttu-id="0b02d-252">W pliku klasę lub moduł, dodaj odwołania do przestrzeni nazw dla widoku hosta dodatku: `CalcHVAs`.</span><span class="sxs-lookup"><span data-stu-id="0b02d-252">In the class or module file, add a namespace reference for the host view of the add-in: `CalcHVAs`.</span></span> <span data-ttu-id="0b02d-253">(W języku Visual Basic tego odwołania do przestrzeni nazw jest `Calc1HVA.CalcHVAs`, chyba że wyłączono domyślne obszary nazw w projektach Visual Basic.)</span><span class="sxs-lookup"><span data-stu-id="0b02d-253">(In Visual Basic, this namespace reference is `Calc1HVA.CalcHVAs`, unless you have turned off the default namespaces in your Visual Basic projects.)</span></span>  
  
8.  <span data-ttu-id="0b02d-254">W **Eksploratora rozwiązań**, wybierz rozwiązanie i z **projektu** menu wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="0b02d-254">In **Solution Explorer**, select the solution and from the **Project** menu choose **Properties**.</span></span> <span data-ttu-id="0b02d-255">W **strony właściwości rozwiązania** okno dialogowe, zestaw **jednego projektu startowego** za ten projekt aplikacji hosta.</span><span class="sxs-lookup"><span data-stu-id="0b02d-255">In the **Solution Property Pages** dialog box, set the **Single Startup Project** to be this host application project.</span></span>  
  
9. <span data-ttu-id="0b02d-256">W pliku klasę lub moduł, użyj <xref:System.AddIn.Hosting.AddInStore.Update%2A?displayProperty=nameWithType> metodę aktualizowania pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="0b02d-256">In the class or module file, use the <xref:System.AddIn.Hosting.AddInStore.Update%2A?displayProperty=nameWithType> method to update the cache.</span></span> <span data-ttu-id="0b02d-257">Użyj <xref:System.AddIn.Hosting.AddInStore.FindAddIn%2A?displayProperty=nameWithType> metodę, aby uzyskać kolekcję tokenów oraz <xref:System.AddIn.Hosting.AddInToken.Activate%2A?displayProperty=nameWithType> metodę, aby aktywować dodatku.</span><span class="sxs-lookup"><span data-stu-id="0b02d-257">Use the <xref:System.AddIn.Hosting.AddInStore.FindAddIn%2A?displayProperty=nameWithType> method to get a collection of tokens, and use the <xref:System.AddIn.Hosting.AddInToken.Activate%2A?displayProperty=nameWithType> method to activate an add-in.</span></span>  
  
     <span data-ttu-id="0b02d-258">Poniższy kod przedstawia aplikacji hosta ukończone.</span><span class="sxs-lookup"><span data-stu-id="0b02d-258">The following code shows the completed host application.</span></span>  
  
     [!code-csharp[AddInP1Host#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1Host/cs/MathHost1.cs#1)]
     [!code-vb[AddInP1Host#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1Host/vb/MathHost1.vb#1)]  
  
    > [!NOTE]
    >  <span data-ttu-id="0b02d-259">Ten kod przyjęto założenie, że struktura folderów potoku znajduje się w folderze aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0b02d-259">This code assumes that the pipeline folder structure is located in the application folder.</span></span> <span data-ttu-id="0b02d-260">Jeśli użytkownik znajduje się on w innym miejscu, zmień wiersz kodu, który ustawia `addInRoot` zmiennej, tak aby zmienna zawiera ścieżkę do potoku struktury katalogów.</span><span class="sxs-lookup"><span data-stu-id="0b02d-260">If you located it elsewhere, change the line of code that sets the `addInRoot` variable, so that the variable contains the path to your pipeline directory structure.</span></span>  
  
     <span data-ttu-id="0b02d-261">W kodzie użyto `ChooseCalculator` metodę do listy tokenów i monitowanie użytkownika o wybranie dodatku.</span><span class="sxs-lookup"><span data-stu-id="0b02d-261">The code uses a `ChooseCalculator` method to list the tokens and to prompt the user to choose an add-in.</span></span> <span data-ttu-id="0b02d-262">`RunCalculator` Metoda monituje użytkownika o matematyczne proste wyrażenia, analizuje wyrażenia przy użyciu `Parser` klasy i wyświetla wyniki zwrócone przez dodatek.</span><span class="sxs-lookup"><span data-stu-id="0b02d-262">The `RunCalculator` method prompts the user for simple math expressions, parses the expressions using the `Parser` class, and displays the results returned by the add-in.</span></span>  
  
10. <span data-ttu-id="0b02d-263">Opcjonalnie tworzenie rozwiązań programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0b02d-263">Optionally, build the Visual Studio solution.</span></span>  
  
## <a name="creating-the-add-in"></a><span data-ttu-id="0b02d-264">Tworzenie dodatku</span><span class="sxs-lookup"><span data-stu-id="0b02d-264">Creating the Add-In</span></span>  
 <span data-ttu-id="0b02d-265">Dodatek implementuje metody określone przez widok dodatku.</span><span class="sxs-lookup"><span data-stu-id="0b02d-265">An add-in implements the methods specified by the add-in view.</span></span> <span data-ttu-id="0b02d-266">Ten dodatek implementuje `Add`, `Subtract`, `Multiply`, i `Divide` operacji oraz zwraca wyniki do hosta.</span><span class="sxs-lookup"><span data-stu-id="0b02d-266">This add-in implements the `Add`, `Subtract`, `Multiply`, and `Divide` operations and returns the results to the host.</span></span>  
  
#### <a name="to-create-the-add-in"></a><span data-ttu-id="0b02d-267">Aby utworzyć dodatku</span><span class="sxs-lookup"><span data-stu-id="0b02d-267">To create the add-in</span></span>  
  
1.  <span data-ttu-id="0b02d-268">Dodawanie nowego projektu o nazwie `AddInCalcV1` do `CalculatorV1` rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="0b02d-268">Add a new project named `AddInCalcV1` to the `CalculatorV1` solution.</span></span> <span data-ttu-id="0b02d-269">Na podstawie **biblioteki klas** szablonu.</span><span class="sxs-lookup"><span data-stu-id="0b02d-269">Base it on the **Class Library** template.</span></span>  
  
2.  <span data-ttu-id="0b02d-270">W **Eksploratora rozwiązań**, Dodaj odwołanie do zestawu System.AddIn.dll do projektu.</span><span class="sxs-lookup"><span data-stu-id="0b02d-270">In **Solution Explorer**, add a reference to the System.AddIn.dll assembly to the project.</span></span>  
  
3.  <span data-ttu-id="0b02d-271">Dodaj odwołanie projektu do `Calc1AddInView` projektu.</span><span class="sxs-lookup"><span data-stu-id="0b02d-271">Add a project reference to the `Calc1AddInView` project.</span></span> <span data-ttu-id="0b02d-272">Wybierz odwołanie do projektu i **właściwości**ustaw **Kopiuj lokalnie** do **False**.</span><span class="sxs-lookup"><span data-stu-id="0b02d-272">Select the project reference, and in **Properties**, set **Copy Local** to **False**.</span></span> <span data-ttu-id="0b02d-273">W języku Visual Basic, użyj **odwołania** karcie **właściwości projektu** można ustawić **Kopiuj lokalnie** do **False** dla odwołania do projektu.</span><span class="sxs-lookup"><span data-stu-id="0b02d-273">In Visual Basic, use the **References** tab of **Project Properties** to set **Copy Local** to **False** for the project reference.</span></span>  
  
4.  <span data-ttu-id="0b02d-274">Zmień nazwę klasy `AddInCalcV1`.</span><span class="sxs-lookup"><span data-stu-id="0b02d-274">Rename the class `AddInCalcV1`.</span></span>  
  
5.  <span data-ttu-id="0b02d-275">Plik klasy, Dodaj odwołanie do przestrzeni nazw <xref:System.AddIn> i segmentów widoku dodatku: `CalcAddInViews` (`Calc1AddInView.CalcAddInViews` w języku Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="0b02d-275">In the class file, add a namespace reference to <xref:System.AddIn> and the add-in view segment: `CalcAddInViews` (`Calc1AddInView.CalcAddInViews` in Visual Basic).</span></span>  
  
6.  <span data-ttu-id="0b02d-276">Zastosuj <xref:System.AddIn.AddInAttribute> atrybutu `AddInCalcV1` klasy, aby zidentyfikować klasy jako dodatek.</span><span class="sxs-lookup"><span data-stu-id="0b02d-276">Apply the <xref:System.AddIn.AddInAttribute> attribute to the `AddInCalcV1` class, to identify the class as an add-in.</span></span>  
  
7.  <span data-ttu-id="0b02d-277">Wprowadź `AddInCalcV1` klasa implementuje interfejs, który reprezentuje Widok dodatku: `CalcAddInViews.ICalculator` (`Calc1AddInView.CalcAddInViews.ICalculator` w języku Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="0b02d-277">Make the `AddInCalcV1` class implement the interface that represents the add-in view: `CalcAddInViews.ICalculator` (`Calc1AddInView.CalcAddInViews.ICalculator` in Visual Basic).</span></span>  
  
8.  <span data-ttu-id="0b02d-278">Implementować członków `ICalculator` przez zwrócenie wyników obliczeń odpowiednie.</span><span class="sxs-lookup"><span data-stu-id="0b02d-278">Implement the members of `ICalculator` by returning the results of the appropriate calculations.</span></span>  
  
     <span data-ttu-id="0b02d-279">Poniższy kod przedstawia ukończone dodatek.</span><span class="sxs-lookup"><span data-stu-id="0b02d-279">The following code shows the completed add-in.</span></span>  
  
     [!code-csharp[AddInP1AddInCalcV1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInCalcV1/cs/AddInCalcV1.cs#1)]
     [!code-vb[AddInP1AddInCalcV1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInCalcV1/vb/AddInCalcV1.vb#1)]  
  
9. <span data-ttu-id="0b02d-280">Opcjonalnie tworzenie rozwiązań programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0b02d-280">Optionally, build the Visual Studio solution.</span></span>  
  
## <a name="deploying-the-pipeline"></a><span data-ttu-id="0b02d-281">Wdrażanie potoku</span><span class="sxs-lookup"><span data-stu-id="0b02d-281">Deploying the Pipeline</span></span>  
 <span data-ttu-id="0b02d-282">Teraz można przystąpić do tworzenia i wdrażania segmentów dodatku do potoku wymagane struktury katalogów.</span><span class="sxs-lookup"><span data-stu-id="0b02d-282">You are now ready to build and deploy the add-in segments to the required pipeline directory structure.</span></span>  
  
#### <a name="to-deploy-the-segments-to-the-pipeline"></a><span data-ttu-id="0b02d-283">Aby wdrożyć segmentów potoku</span><span class="sxs-lookup"><span data-stu-id="0b02d-283">To deploy the segments to the pipeline</span></span>  
  
1.  <span data-ttu-id="0b02d-284">Dla każdego projektu w rozwiązaniu, użyj **kompilacji** karcie **właściwości projektu** ( **skompilować** kartę w języku Visual Basic) można ustawić wartości **ścieżki wyjściowej**  ( **ścieżki wyjściowej kompilacji** w języku Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="0b02d-284">For each project in the solution, use the **Build** tab of **Project Properties** (the **Compile** tab in Visual Basic) to set the value of the **Output path** (the **Build output path** in Visual Basic).</span></span> <span data-ttu-id="0b02d-285">Jeśli nazwany folderze aplikacji `MyApp`, na przykład projektów czy kompilacji do następujących folderów:</span><span class="sxs-lookup"><span data-stu-id="0b02d-285">If you named your application folder `MyApp`, for example, your projects would build into the following folders:</span></span>  
  
    |<span data-ttu-id="0b02d-286">Projekt</span><span class="sxs-lookup"><span data-stu-id="0b02d-286">Project</span></span>|<span data-ttu-id="0b02d-287">Ścieżka</span><span class="sxs-lookup"><span data-stu-id="0b02d-287">Path</span></span>|  
    |-------------|----------|  
    |<span data-ttu-id="0b02d-288">AddInCalcV1</span><span class="sxs-lookup"><span data-stu-id="0b02d-288">AddInCalcV1</span></span>|<span data-ttu-id="0b02d-289">MyApp\Pipeline\AddIns\CalcV1</span><span class="sxs-lookup"><span data-stu-id="0b02d-289">MyApp\Pipeline\AddIns\CalcV1</span></span>|  
    |<span data-ttu-id="0b02d-290">Calc1AddInSideAdapter</span><span class="sxs-lookup"><span data-stu-id="0b02d-290">Calc1AddInSideAdapter</span></span>|<span data-ttu-id="0b02d-291">MyApp\Pipeline\AddInSideAdapters</span><span class="sxs-lookup"><span data-stu-id="0b02d-291">MyApp\Pipeline\AddInSideAdapters</span></span>|  
    |<span data-ttu-id="0b02d-292">Calc1AddInView</span><span class="sxs-lookup"><span data-stu-id="0b02d-292">Calc1AddInView</span></span>|<span data-ttu-id="0b02d-293">MyApp\Pipeline\AddInViews</span><span class="sxs-lookup"><span data-stu-id="0b02d-293">MyApp\Pipeline\AddInViews</span></span>|  
    |<span data-ttu-id="0b02d-294">Calc1Contract</span><span class="sxs-lookup"><span data-stu-id="0b02d-294">Calc1Contract</span></span>|<span data-ttu-id="0b02d-295">MyApp\Pipeline\Contracts</span><span class="sxs-lookup"><span data-stu-id="0b02d-295">MyApp\Pipeline\Contracts</span></span>|  
    |<span data-ttu-id="0b02d-296">Calc1Host</span><span class="sxs-lookup"><span data-stu-id="0b02d-296">Calc1Host</span></span>|<span data-ttu-id="0b02d-297">MyApp</span><span class="sxs-lookup"><span data-stu-id="0b02d-297">MyApp</span></span>|  
    |<span data-ttu-id="0b02d-298">Calc1HostSideAdapter</span><span class="sxs-lookup"><span data-stu-id="0b02d-298">Calc1HostSideAdapter</span></span>|<span data-ttu-id="0b02d-299">MyApp\Pipeline\HostSideAdapters</span><span class="sxs-lookup"><span data-stu-id="0b02d-299">MyApp\Pipeline\HostSideAdapters</span></span>|  
    |<span data-ttu-id="0b02d-300">Calc1HVA</span><span class="sxs-lookup"><span data-stu-id="0b02d-300">Calc1HVA</span></span>|<span data-ttu-id="0b02d-301">MyApp</span><span class="sxs-lookup"><span data-stu-id="0b02d-301">MyApp</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="0b02d-302">Jeśli zdecydujesz się na umieszczanie strukturę folderu potoku w lokalizacji innej niż folderze aplikacji, należy zmodyfikować ścieżki odpowiednio wymienionych w tabeli.</span><span class="sxs-lookup"><span data-stu-id="0b02d-302">If you decided to put your pipeline folder structure in a location other than your application folder, you must modify the paths shown in the table accordingly.</span></span> <span data-ttu-id="0b02d-303">Zawiera omówienie wymagań katalogu potoku w [wymagania rozwój potoku](http://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span><span class="sxs-lookup"><span data-stu-id="0b02d-303">See the discussion of pipeline directory requirements in [Pipeline Development Requirements](http://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span></span>  
  
2.  <span data-ttu-id="0b02d-304">Skompiluj rozwiązanie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0b02d-304">Build the Visual Studio solution.</span></span>  
  
3.  <span data-ttu-id="0b02d-305">Sprawdź katalogów aplikacji i potoku, aby upewnić się, że zestawy zostały skopiowane do katalogów poprawne i czy w folderach niewłaściwy zostały zainstalowane żadne dodatkowe kopie zestawów.</span><span class="sxs-lookup"><span data-stu-id="0b02d-305">Check the application and pipeline directories to ensure that the assemblies were copied to the correct directories and that no extra copies of assemblies were installed in the wrong folders.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0b02d-306">Jeśli nie została zmieniona **Kopiuj lokalnie** do **False** dla `Calc1AddInView` projektu odwołania w `AddInCalcV1` projektu, problemów z kontekstami modułu ładującego uniemożliwi dodatek znajdujących się.</span><span class="sxs-lookup"><span data-stu-id="0b02d-306">If you did not change **Copy Local** to **False** for the `Calc1AddInView` project reference in the `AddInCalcV1` project, loader context problems will prevent the add-in from being located.</span></span>  
  
     <span data-ttu-id="0b02d-307">Informacje o wdrażaniu do potoku, zobacz [wymagania rozwój potoku](http://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span><span class="sxs-lookup"><span data-stu-id="0b02d-307">For information about deploying to the pipeline, see [Pipeline Development Requirements](http://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span></span>  
  
## <a name="running-the-host-application"></a><span data-ttu-id="0b02d-308">Uruchomienie aplikacji hosta</span><span class="sxs-lookup"><span data-stu-id="0b02d-308">Running the Host Application</span></span>  
 <span data-ttu-id="0b02d-309">Teraz można przystąpić do uruchomienia hosta i interakcji z dodatku.</span><span class="sxs-lookup"><span data-stu-id="0b02d-309">You are now ready to run the host and interact with the add-in.</span></span>  
  
#### <a name="to-run-the-host-application"></a><span data-ttu-id="0b02d-310">Aby uruchomić aplikację hosta</span><span class="sxs-lookup"><span data-stu-id="0b02d-310">To run the host application</span></span>  
  
1.  <span data-ttu-id="0b02d-311">W wierszu polecenia przejdź do katalogu aplikacji i uruchomić aplikację hosta `Calc1Host.exe`.</span><span class="sxs-lookup"><span data-stu-id="0b02d-311">At the command prompt, go to the application directory and run the host application, `Calc1Host.exe`.</span></span>  
  
2.  <span data-ttu-id="0b02d-312">Host znajduje wszystkie dostępne dodatki jej typu i wyświetla monit o wybranie dodatku.</span><span class="sxs-lookup"><span data-stu-id="0b02d-312">The host finds all available add-ins of its type and prompts you to select an add-in.</span></span> <span data-ttu-id="0b02d-313">Wprowadź **1** dostępne tylko w dodatku.</span><span class="sxs-lookup"><span data-stu-id="0b02d-313">Enter **1** for the only available add-in.</span></span>  
  
3.  <span data-ttu-id="0b02d-314">Wprowadź równania Kalkulator, takich jak **2 + 2**.</span><span class="sxs-lookup"><span data-stu-id="0b02d-314">Enter an equation for the calculator, such as **2 + 2**.</span></span> <span data-ttu-id="0b02d-315">Musi to być odstępy między liczb i operatora.</span><span class="sxs-lookup"><span data-stu-id="0b02d-315">There must be spaces between the numbers and the operator.</span></span>  
  
4.  <span data-ttu-id="0b02d-316">Typ **zakończyć** i naciśnij klawisz **Enter** klawisz, aby zamknąć aplikację.</span><span class="sxs-lookup"><span data-stu-id="0b02d-316">Type **exit** and press the **Enter** key to close the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b02d-317">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0b02d-317">See Also</span></span>  
 [<span data-ttu-id="0b02d-318">Wskazówki: Włączanie zgodności z poprzednimi wersjami zmiana hosta</span><span class="sxs-lookup"><span data-stu-id="0b02d-318">Walkthrough: Enabling Backward Compatibility as Your Host Changes</span></span>](http://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848)  
 [<span data-ttu-id="0b02d-319">Wskazówki: Przekazywanie kolekcje między hostami oraz dodatki</span><span class="sxs-lookup"><span data-stu-id="0b02d-319">Walkthrough: Passing Collections Between Hosts and Add-Ins</span></span>](http://msdn.microsoft.com/library/b532c604-548e-4fab-b11c-377257dd0ee5)  
 [<span data-ttu-id="0b02d-320">Wymagania dotyczące rozwój potoku</span><span class="sxs-lookup"><span data-stu-id="0b02d-320">Pipeline Development Requirements</span></span>](http://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5)  
 [<span data-ttu-id="0b02d-321">Kontrakty, widoków i kart</span><span class="sxs-lookup"><span data-stu-id="0b02d-321">Contracts, Views, and Adapters</span></span>](http://msdn.microsoft.com/library/a6460173-9507-4b87-8c07-d4ee245d715c)  
 [<span data-ttu-id="0b02d-322">Opracowywanie potoku</span><span class="sxs-lookup"><span data-stu-id="0b02d-322">Pipeline Development</span></span>](../../../docs/framework/add-ins/pipeline-development.md)
