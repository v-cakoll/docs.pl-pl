---
title: "Za pomocą działania InvokePowerShell"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 956251a0-31ca-4183-bf76-d277c08585df
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4cf7092d6eac4fc2d70c4606f4a76f3a83ed9dcf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="using-the-invokepowershell-activity"></a><span data-ttu-id="5c34e-102">Za pomocą działania InvokePowerShell</span><span class="sxs-lookup"><span data-stu-id="5c34e-102">Using the InvokePowerShell Activity</span></span>
<span data-ttu-id="5c34e-103">InvokePowerShell przykładowych pokazano, jak można wywołać za pomocą poleceń programu Windows PowerShell `InvokePowerShell` działania.</span><span class="sxs-lookup"><span data-stu-id="5c34e-103">The InvokePowerShell sample demonstrates how to invoke Windows PowerShell commands using the `InvokePowerShell` activity.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="5c34e-104">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="5c34e-104">Demonstrates</span></span>  
  
-   <span data-ttu-id="5c34e-105">Proste innowacji poleceń programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5c34e-105">Simple innovation of Windows PowerShell commands.</span></span>  
  
-   <span data-ttu-id="5c34e-106">Pobieranie wartości z potoku dane wyjściowe programu Windows PowerShell i zapisanie ich w zmiennych przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="5c34e-106">Retrieve values from the Windows PowerShell output pipeline and store them in workflow variables.</span></span>  
  
-   <span data-ttu-id="5c34e-107">Przekazywanie danych w systemie windows PowerShell jako wejściowych potoku wykonywania polecenia.</span><span class="sxs-lookup"><span data-stu-id="5c34e-107">Pass data into windows PowerShell as input pipeline for an executing command.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5c34e-108">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="5c34e-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5c34e-109">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="5c34e-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5c34e-110">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="5c34e-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5c34e-111">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="5c34e-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\PowerShell`  
  
## <a name="discussion"></a><span data-ttu-id="5c34e-112">Omówienie</span><span class="sxs-lookup"><span data-stu-id="5c34e-112">Discussion</span></span>  
 <span data-ttu-id="5c34e-113">Ten przykład zawiera następujące trzy projekty.</span><span class="sxs-lookup"><span data-stu-id="5c34e-113">This sample contains the following three projects.</span></span>  
  
|<span data-ttu-id="5c34e-114">Nazwa projektu</span><span class="sxs-lookup"><span data-stu-id="5c34e-114">Project Name</span></span>|<span data-ttu-id="5c34e-115">Opis</span><span class="sxs-lookup"><span data-stu-id="5c34e-115">Description</span></span>|<span data-ttu-id="5c34e-116">Główne pliki</span><span class="sxs-lookup"><span data-stu-id="5c34e-116">Main Files</span></span>|  
|------------------|-----------------|----------------|  
|<span data-ttu-id="5c34e-117">CodedClient</span><span class="sxs-lookup"><span data-stu-id="5c34e-117">CodedClient</span></span>|<span data-ttu-id="5c34e-118">Przykładowej aplikacji klienta, który używa działanie programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5c34e-118">A sample client application that uses the PowerShell activity.</span></span>|<span data-ttu-id="5c34e-119">-   **Plik program.cs**: programowane tworzy na podstawie sekwencji przepływu pracy, który wywołuje InvokePowerShell działania.</span><span class="sxs-lookup"><span data-stu-id="5c34e-119">-   **Program.cs**: Programmatically creates a sequence-based workflow that calls the InvokePowerShell activity.</span></span>|  
|<span data-ttu-id="5c34e-120">DesignerClient</span><span class="sxs-lookup"><span data-stu-id="5c34e-120">DesignerClient</span></span>|<span data-ttu-id="5c34e-121">Zestaw działań niestandardowych, które zawierają `InvokePowerShell` działań niestandardowych i innych dodatkowych działań niestandardowych i przepływu pracy, który używa ich.</span><span class="sxs-lookup"><span data-stu-id="5c34e-121">A set of custom activities that contain the `InvokePowerShell` custom activity and other miscellaneous custom activities, and a workflow that uses them.</span></span>|<ul><li><span data-ttu-id="5c34e-122">Działania:</span><span class="sxs-lookup"><span data-stu-id="5c34e-122">Activities:</span></span><br /><br /> <ul><li><span data-ttu-id="5c34e-123">**PrintCollection.cs**: działanie pomocnika, która wyświetla wszystkie elementy kolekcji do konsoli.</span><span class="sxs-lookup"><span data-stu-id="5c34e-123">**PrintCollection.cs**: A helper activity that prints all the items in a collection to the console.</span></span></li><li><span data-ttu-id="5c34e-124">**ReadLine.cs**: działaniem pomocnika dla danych wejściowych odczytu z konsoli.</span><span class="sxs-lookup"><span data-stu-id="5c34e-124">**ReadLine.cs**: A helper activity for reading input from the console.</span></span></li></ul></li><li><span data-ttu-id="5c34e-125">System plików:</span><span class="sxs-lookup"><span data-stu-id="5c34e-125">File System:</span></span><br /><br /> <ul><li><span data-ttu-id="5c34e-126">**Copy.XAML**: działanie, które kopiuje plik.</span><span class="sxs-lookup"><span data-stu-id="5c34e-126">**Copy.xaml**: An activity that copies a file.</span></span></li><li><span data-ttu-id="5c34e-127">**CreateFile.xaml**: działanie, które tworzy plik.</span><span class="sxs-lookup"><span data-stu-id="5c34e-127">**CreateFile.xaml**: An activity that creates a file.</span></span></li><li><span data-ttu-id="5c34e-128">**DeleteFile.xaml**: działanie, które usuwa plik.</span><span class="sxs-lookup"><span data-stu-id="5c34e-128">**DeleteFile.xaml**: An activity that deletes a file.</span></span></li><li><span data-ttu-id="5c34e-129">**MakeDir.xaml**: działanie, które tworzy katalog.</span><span class="sxs-lookup"><span data-stu-id="5c34e-129">**MakeDir.xaml**: An activity that creates a directory.</span></span></li><li><span data-ttu-id="5c34e-130">**Move.XAML**: działanie, które przenosi plik.</span><span class="sxs-lookup"><span data-stu-id="5c34e-130">**Move.xaml**: An activity that moves a file.</span></span></li><li><span data-ttu-id="5c34e-131">**ReadFile.xaml**: działanie, które umożliwia odczytanie pliku i zwraca jego zawartość.</span><span class="sxs-lookup"><span data-stu-id="5c34e-131">**ReadFile.xaml**: An activity that reads a file and returns its contents.</span></span></li><li><span data-ttu-id="5c34e-132">**TestPath.xaml**: działanie, które sprawdza istnienie ścieżki.</span><span class="sxs-lookup"><span data-stu-id="5c34e-132">**TestPath.xaml**: An activity that tests for the existence of a path.</span></span></li></ul></li><li><span data-ttu-id="5c34e-133">Proces:</span><span class="sxs-lookup"><span data-stu-id="5c34e-133">Process:</span></span><br /><br /> <ul><li><span data-ttu-id="5c34e-134">**GetProcess.xaml**: działanie, które pobiera listę uruchomionych procesów.</span><span class="sxs-lookup"><span data-stu-id="5c34e-134">**GetProcess.xaml**: An activity that gets a list of running processes.</span></span></li><li><span data-ttu-id="5c34e-135">**StopProcess.xaml**: działanie, które zatrzymuje określonego procesu.</span><span class="sxs-lookup"><span data-stu-id="5c34e-135">**StopProcess.xaml**: An activity that stops a specific process.</span></span></li></ul></li><li><span data-ttu-id="5c34e-136">**Plik program.cs**: wywołanie Sequence1 przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="5c34e-136">**Program.cs**: Calls the Sequence1 workflow.</span></span></li><li><span data-ttu-id="5c34e-137">**Sequence1.XAML**: przepływ pracy oparty na sekwencji.</span><span class="sxs-lookup"><span data-stu-id="5c34e-137">**Sequence1.xaml**: A sequence-based workflow.</span></span></li></ul>|  
|<span data-ttu-id="5c34e-138">PowerShell</span><span class="sxs-lookup"><span data-stu-id="5c34e-138">PowerShell</span></span>|<span data-ttu-id="5c34e-139">`InvokePowerShell` Działanie i jego skojarzony projektantów.</span><span class="sxs-lookup"><span data-stu-id="5c34e-139">The `InvokePowerShell` activity and its associated designers.</span></span>|<span data-ttu-id="5c34e-140">Pliki działań</span><span class="sxs-lookup"><span data-stu-id="5c34e-140">Activity Files</span></span><br /><br /> <span data-ttu-id="5c34e-141">-   **ExecutePowerShell.cs**: logiki główny wykonywania działania.</span><span class="sxs-lookup"><span data-stu-id="5c34e-141">-   **ExecutePowerShell.cs**: The main execution logic of the activity.</span></span><br /><span data-ttu-id="5c34e-142">-   **InvokePowerShell.cs**: otokę z logiką wykonywania głównych, zawiera ogólne (wartość zwrotna) i wersji nierodzajową (wartość-return).</span><span class="sxs-lookup"><span data-stu-id="5c34e-142">-   **InvokePowerShell.cs**: The wrapper around the main execution logic, which contains a generic (return value) version and a non-generic (non-return value) version.</span></span> <span data-ttu-id="5c34e-143">Jest to interfejs publiczny dla działania.</span><span class="sxs-lookup"><span data-stu-id="5c34e-143">This is the public interface for the activity.</span></span><br /><span data-ttu-id="5c34e-144">-   **NoPersistZone.cs**: działanie uniemożliwia utrwalanie żadnych działań podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="5c34e-144">-   **NoPersistZone.cs**: This activity prevents any child activities from persisting.</span></span> <span data-ttu-id="5c34e-145">Ta klasa jest używana w ramach `InvokePowerShell` implementacji działania uniemożliwi działanie utrwalone pośredniej wykonywania.</span><span class="sxs-lookup"><span data-stu-id="5c34e-145">This class is used within the `InvokePowerShell` activity implementation to prevent the activity from being persisted mid-execution.</span></span><br /><br /> <span data-ttu-id="5c34e-146">Projektant plików:</span><span class="sxs-lookup"><span data-stu-id="5c34e-146">Designer files:</span></span><br /><br /> <span data-ttu-id="5c34e-147">1.  **ArgumentDictionaryEditor.cs**: okno dialogowe systemu Windows, który umożliwia użytkownikom edytowanie argumenty `InvokePowerShell` działania.</span><span class="sxs-lookup"><span data-stu-id="5c34e-147">1.  **ArgumentDictionaryEditor.cs**: A Windows dialog that allows the user to edit the arguments of the `InvokePowerShell` activity.</span></span><br /><span data-ttu-id="5c34e-148">2.  **GenericInvokePowerShellDesigner.xaml** i **GenericInvokePowerShellDesigner.xaml.cs**: Określa wygląd ogólnego `InvokePowerShell` działania w [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5c34e-148">2.  **GenericInvokePowerShellDesigner.xaml** and **GenericInvokePowerShellDesigner.xaml.cs**: Defines the appearance of the generic `InvokePowerShell` activity in [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].</span></span><br /><span data-ttu-id="5c34e-149">3.  **InvokePowerShellDesigner.xaml** i **InvokePowerShellDesigner.cs**: Określa wygląd nieogólnego `InvokePowerShell` działania w [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5c34e-149">3.  **InvokePowerShellDesigner.xaml** and **InvokePowerShellDesigner.cs**: Defines the appearance of the non-generic `InvokePowerShell` activity in [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].</span></span>|  
  
 <span data-ttu-id="5c34e-150">Projektów klienckich omówiono najpierw, ponieważ jest łatwiejsze do zrozumienia funkcji wewnętrznego działania programu PowerShell, po jego użycia jest rozpoznawany.</span><span class="sxs-lookup"><span data-stu-id="5c34e-150">The client projects are discussed first, as it is easier to understand the internal functionality of the PowerShell activity once its use is understood.</span></span>  
  
## <a name="using-this-sample"></a><span data-ttu-id="5c34e-151">Za pomocą tego przykładu</span><span class="sxs-lookup"><span data-stu-id="5c34e-151">Using This Sample</span></span>  
 <span data-ttu-id="5c34e-152">W poniższych sekcjach opisano sposób użycia trzy projekty w próbce.</span><span class="sxs-lookup"><span data-stu-id="5c34e-152">The following sections describe how to use the three projects in the sample.</span></span>  
  
### <a name="using-the-coded-client-project"></a><span data-ttu-id="5c34e-153">Za pomocą programu Project kodowane klienta</span><span class="sxs-lookup"><span data-stu-id="5c34e-153">Using the Coded Client Project</span></span>  
 <span data-ttu-id="5c34e-154">Klient próbki programowo tworzy działania sequence, który zawiera przykłady kilka różnych metod za pomocą `InvokePowerShell` działania.</span><span class="sxs-lookup"><span data-stu-id="5c34e-154">The sample client programmatically creates a sequence activity, which contains examples of several different methods of using the `InvokePowerShell` activity.</span></span> <span data-ttu-id="5c34e-155">Pierwsze uruchomienie uruchamia Notatnik.</span><span class="sxs-lookup"><span data-stu-id="5c34e-155">The first invocation launches Notepad.</span></span>  
  
```  
new InvokePowerShell()  
{  
    CommandText = "notepad"  
},  
```  
  
 <span data-ttu-id="5c34e-156">Drugie wywołanie pobiera listę procesów uruchomionych na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="5c34e-156">The second invocation gets a list of the processes running on the local machine.</span></span>  
  
```  
new InvokePowerShell<Process>()  
{  
    CommandText = "Get-Process",  
    Output = processes1,  
},  
```  
  
 <span data-ttu-id="5c34e-157">`Output`zmienna jest używana do przechowywania danych wyjściowych polecenia.</span><span class="sxs-lookup"><span data-stu-id="5c34e-157">`Output` is the variable used to store the output of the command.</span></span>  
  
 <span data-ttu-id="5c34e-158">Następne wywołanie pokazuje, jak przetwarzanie końcowe krok zostanie uruchomiony na każdej poszczególnych danych wyjściowych wywołania programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5c34e-158">The next call demonstrates how to run a post-processing step on each individual output of the PowerShell invocation.</span></span> <span data-ttu-id="5c34e-159">`InitializationAction`ustawiono funkcji, które generuje reprezentację ciągu dla każdego procesu.</span><span class="sxs-lookup"><span data-stu-id="5c34e-159">`InitializationAction` is set to the function that outputs a string representation for each process.</span></span> <span data-ttu-id="5c34e-160">Kolekcja te ciągi, jest zwracany w `Output` zmiennej przez `InvokePowerShell<string>` działania.</span><span class="sxs-lookup"><span data-stu-id="5c34e-160">The collection of these strings is returned in the `Output` variable by the `InvokePowerShell<string>` activity.</span></span>  
  
 <span data-ttu-id="5c34e-161">Pomyślne `InvokePowerShell` wywołania pokazują przekazywanie danych do działania i pobierania danych wyjściowych i błędów wychodzących.</span><span class="sxs-lookup"><span data-stu-id="5c34e-161">The succeeding `InvokePowerShell` calls demonstrate passing data into the activity and getting outputs and errors out.</span></span>  
  
### <a name="using-the-designer-client-project"></a><span data-ttu-id="5c34e-162">Przy użyciu klienta projektanta projektu</span><span class="sxs-lookup"><span data-stu-id="5c34e-162">Using the Designer Client Project</span></span>  
 <span data-ttu-id="5c34e-163">Projekt DesignerClient składa się z zestawu działań niestandardowych prawie wszystkie są wbudowane, zawierający `InvokePowerShell` działania.</span><span class="sxs-lookup"><span data-stu-id="5c34e-163">The DesignerClient project consists of a set of custom activities, almost all of which are built containing the `InvokePowerShell` activity.</span></span> <span data-ttu-id="5c34e-164">Większość działań wywołać wersja nieogólnego `InvokePowerShell` działania i nie oczekuje wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="5c34e-164">Most of the activities call the non-generic version of the `InvokePowerShell` activity, and do not expect a return value.</span></span> <span data-ttu-id="5c34e-165">Inne działania przy użyciu wersji ogólnego `InvokePowerShell` działania i użyj `InitializationAction` argument po przetwarzaniu wyniki.</span><span class="sxs-lookup"><span data-stu-id="5c34e-165">Other activities use the generic version of the `InvokePowerShell` activity, and use the `InitializationAction` argument to post-process the results.</span></span>  
  
## <a name="using-the-powershell-project"></a><span data-ttu-id="5c34e-166">Przy użyciu programu PowerShell projektu</span><span class="sxs-lookup"><span data-stu-id="5c34e-166">Using the PowerShell Project</span></span>  
 <span data-ttu-id="5c34e-167">Akcja główna działania ma miejsce w `ExecutePowerShell` klasy.</span><span class="sxs-lookup"><span data-stu-id="5c34e-167">The main action of the activity takes place in the `ExecutePowerShell` class.</span></span> <span data-ttu-id="5c34e-168">Ponieważ wykonanie polecenia programu PowerShell nie powinny blokować wątku głównego przepływu pracy, działanie jest tworzony za działanie asynchroniczne poprzez dziedziczenie z <xref:System.Activities.AsyncCodeActivity> klasy.</span><span class="sxs-lookup"><span data-stu-id="5c34e-168">Because the execution of PowerShell commands should not block the main workflow thread, the activity is created to be an asynchronous activity by inheriting from the <xref:System.Activities.AsyncCodeActivity> class.</span></span>  
  
 <span data-ttu-id="5c34e-169"><xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> Metoda jest wywoływana przez środowisko uruchomieniowe przepływu pracy, aby rozpocząć uruchomienia działania.</span><span class="sxs-lookup"><span data-stu-id="5c34e-169">The <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> method is called by the workflow runtime to begin running the activity.</span></span> <span data-ttu-id="5c34e-170">Rozpoczyna się przez wywoływanie interfejsów API środowiska PowerShell, aby utworzyć potok programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5c34e-170">It starts by calling PowerShell APIs to create a PowerShell pipeline.</span></span>  
  
```  
runspace = RunspaceFactory.CreateRunspace();  
runspace.Open();  
pipeline = runspace.CreatePipeline();  
```  
  
 <span data-ttu-id="5c34e-171">Następnie tworzy polecenia programu PowerShell i wypełnia je parametry i zmienne.</span><span class="sxs-lookup"><span data-stu-id="5c34e-171">It then creates a PowerShell command and populates it with parameters and variables.</span></span>  
  
```  
Command cmd = new Command(this.CommandText, this.IsScript);   
// loop over parameters and run: cmd.Parameters.Add(...)  
// loop over variables and run: runspace.SessionStateProxy.SetVariable(...)  
pipeline.Commands.Add(cmd);  
```  
  
 <span data-ttu-id="5c34e-172">Dane wejściowe przekazywane w potoku w są także wysyłane do potoku w tym momencie.</span><span class="sxs-lookup"><span data-stu-id="5c34e-172">The inputs piped in are also sent to the pipeline at this point.</span></span> <span data-ttu-id="5c34e-173">Na koniec potoku jest ujęte w `PipelineInvokerAsyncResult` obiektu i zwracane.</span><span class="sxs-lookup"><span data-stu-id="5c34e-173">Finally, the pipeline is wrapped in a `PipelineInvokerAsyncResult` object and returned.</span></span> <span data-ttu-id="5c34e-174">`PipelineInvokerAsyncResult` Obiektu rejestruje odbiornik i wywołuje potok.</span><span class="sxs-lookup"><span data-stu-id="5c34e-174">The `PipelineInvokerAsyncResult` object registers a listener and invokes the pipeline.</span></span>  
  
```  
pipeline.InvokeAsync();  
```  
  
 <span data-ttu-id="5c34e-175">Po zakończeniu wykonywania, danych wyjściowych i błędów są przechowywane w tym samym `PipelineInvokerAsyncResult` obiektu i kontroli jest zwracane do środowiska uruchomieniowego przepływu pracy, wywołując metodę wywołania zwrotnego oryginalnie przekazana do <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A>.</span><span class="sxs-lookup"><span data-stu-id="5c34e-175">When execution finishes, output and errors are stored within the same `PipelineInvokerAsyncResult` object, and control is handed back to the workflow runtime by calling the callback method originally passed to <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A>.</span></span>  
  
 <span data-ttu-id="5c34e-176">Po zakończeniu wykonywania metody środowiska uruchomieniowego przepływu pracy wywołuje działania <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="5c34e-176">At the end of the method's execution, the workflow runtime calls the activity’s <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> method.</span></span>  
  
 <span data-ttu-id="5c34e-177">`InvokePowerShell` Klasy zawija `ExecutePowerShellCommand` klasy i tworzy dwie wersje działanie; ogólny wersja oraz wersja nierodzajową.</span><span class="sxs-lookup"><span data-stu-id="5c34e-177">The `InvokePowerShell` class wraps the `ExecutePowerShellCommand` class and creates two versions of the activity; a generic version and a non-generic version.</span></span> <span data-ttu-id="5c34e-178">Wersja nieogólnego zwraca dane wyjściowe wykonania programu PowerShell bezpośrednio, natomiast ogólnego wersji przekształca poszczególne wyniki do typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="5c34e-178">The non-generic version returns the output of the PowerShell execution directly, whereas the generic version transforms the individual results to the generic type.</span></span>  
  
 <span data-ttu-id="5c34e-179">Wersja ogólnego działania jest zaimplementowany jako sekwencyjnego przepływu pracy, który wywołuje `ExecutePowerShellCommand` i przetwarza po jego wyniki.</span><span class="sxs-lookup"><span data-stu-id="5c34e-179">The generic version of the activity is implemented as a sequential workflow that calls `ExecutePowerShellCommand` and post-processes its results.</span></span> <span data-ttu-id="5c34e-180">Dla każdego elementu w kolekcji wynik przetwarzania końcowego krok wywołuje `InitializationAction` Jeśli jest ustawiona.</span><span class="sxs-lookup"><span data-stu-id="5c34e-180">For each element in the result collection, the post-processing step calls `InitializationAction` if it is set.</span></span> <span data-ttu-id="5c34e-181">W przeciwnym razie ma prosty rzutowania.</span><span class="sxs-lookup"><span data-stu-id="5c34e-181">Otherwise, it does a simple cast.</span></span>  
  
```  
new ForEach<PSObject>  
{  
    Values = psObjects,  
    Body = new ActivityAction<PSObject>  
    {  
        Argument = psObject,  
        Handler = new Sequence  
        {  
            Activities =  
            {  
                new If  
                {  
                    Condition = // Is InitializationAction set?  
                    Then = new InvokeFunc<PSObject, TResult>  
                    {  
                        Argument = psObject,  
                        Result = outputObject,  
                        Func = this.InitializationAction  
                    },  
                    Else = new Assign<TResult>  
                    {  
                        To = outputObject,  
                        Value = new InArgument<TResult>(ctx => (TResult) psObject.Get(ctx).BaseObject),  
                    }  
                },  
                new AddToCollection<TResult>  
                {  
                    Collection = outputObjects,  
                    Item = outputObject  
                },  
            }  
        }  
    }  
},  
```  
  
 <span data-ttu-id="5c34e-182">Dla każdego z tych `InvokePowerShell` działania (ogólne i inny niż ogólny), projektanta został utworzony.</span><span class="sxs-lookup"><span data-stu-id="5c34e-182">For each of the two `InvokePowerShell` activities (generic, and non-generic), a designer was created.</span></span> <span data-ttu-id="5c34e-183">InvokePowerShellDesigner.xaml i jego plik skojarzony CS określenia jej wyglądu w [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)] wersji nieogólnego `InvokePowerShell` działania.</span><span class="sxs-lookup"><span data-stu-id="5c34e-183">InvokePowerShellDesigner.xaml and its associated .cs file define the appearance in [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)] for the non-generic version of the `InvokePowerShell` activity.</span></span> <span data-ttu-id="5c34e-184">Wewnątrz InvokePowerShellDesigner.xaml <xref:System.Windows.Controls.DockPanel> jest używana do reprezentowania interfejsu graficznego.</span><span class="sxs-lookup"><span data-stu-id="5c34e-184">Inside InvokePowerShellDesigner.xaml, a <xref:System.Windows.Controls.DockPanel> is used to represent the graphical interface.</span></span>  
  
```  
<DockPanel x:Uid="DockPanel_1" LastChildFill="True">  
        <TextBlock x:Uid="TextBlock_1" Text="CommandText" />  
        <TextBox x:Uid="TextBox_1" Text="{Binding Path=ModelItem.CommandText, Mode=TwoWay}"  
                 TextWrapping="WrapWithOverflow"  AcceptsReturn="True" MinLines="4" MaxLines="4"  
                 Background="{x:Null}" Margin="3" />  
    </DockPanel>  
```  
  
 <span data-ttu-id="5c34e-185">Należy pamiętać, że `Text` właściwości pola tekstowego jest wiązanie dwukierunkowe, który zapewnia, że wartość działania `CommandText` właściwości jest odpowiednikiem wartości danych wejściowych do projektanta.</span><span class="sxs-lookup"><span data-stu-id="5c34e-185">Note that the `Text` property of the text box is a two-way binding that ensures that the value of the activity’s `CommandText` property is equivalent to the value input into the designer.</span></span>  
  
 <span data-ttu-id="5c34e-186">GenericInvokePowerShellDesigner.xaml i jego plik skojarzony CS definiują interfejsu graficznego dla ogólnego `InvokePowerShell` działania.</span><span class="sxs-lookup"><span data-stu-id="5c34e-186">GenericInvokePowerShellDesigner.xaml and its associated .cs file define the graphical interface for the generic `InvokePowerShell` activity.</span></span> <span data-ttu-id="5c34e-187">Projektant jest nieco bardziej skomplikowane, ponieważ umożliwia użytkownikom ustawianie `InitializationAction`.</span><span class="sxs-lookup"><span data-stu-id="5c34e-187">The designer is slightly more complicated because it allows users to set an `InitializationAction`.</span></span> <span data-ttu-id="5c34e-188">Użycie jest kluczowym elementem <xref:System.Activities.Presentation.WorkflowItemPresenter> zezwalająca przeciągnij i upuść działań podrzędnych na `InvokePowerShell` powierzchnię projektanta.</span><span class="sxs-lookup"><span data-stu-id="5c34e-188">The key element is the usage of <xref:System.Activities.Presentation.WorkflowItemPresenter> to allow drag and drop of child activities onto the `InvokePowerShell` designer surface.</span></span>  
  
```  
<sap:WorkflowItemPresenter x:Uid="sap:WorkflowItemPresenter_1" Margin="0,10,0,10"  
    HintText="Drop Activities Here"  
    AllowedItemType="{x:Type sa:Activity}"  
    Item="{Binding Path=ModelItem.InitializationAction.Handler, Mode=TwoWay}"  
    Grid.Row="1" Grid.Column="1" />  
```  
  
 <span data-ttu-id="5c34e-189">Dostosowywanie projektanta nie zatrzymuje z plikami .xaml definiujących wygląd działania w obszarze roboczym projekt.</span><span class="sxs-lookup"><span data-stu-id="5c34e-189">The designer customization does not stop with the .xaml files that define the appearance of the activity on the design canvas.</span></span> <span data-ttu-id="5c34e-190">Okna dialogowe używany do wyświetlania parametry działania można również dostosować.</span><span class="sxs-lookup"><span data-stu-id="5c34e-190">The dialog boxes used to display the parameters of the activity can also be customized.</span></span> <span data-ttu-id="5c34e-191">Te parametry i zmienne środowiska PowerShell wpływają na zachowanie poleceń programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5c34e-191">These parameters and PowerShell variables affect the behavior of PowerShell commands.</span></span> <span data-ttu-id="5c34e-192">Działanie udostępnia je jako <!--zz <xref:System.Collections.Generic.Dictionary%601>--> `System.Collections.Generic.Dictionary` typów.</span><span class="sxs-lookup"><span data-stu-id="5c34e-192">The activity exposes them as <!--zz <xref:System.Collections.Generic.Dictionary%601>--> `System.Collections.Generic.Dictionary` types.</span></span> <span data-ttu-id="5c34e-193">ArgumentDictionaryEditor.cs, PropertyEditorResources.xaml i PropertyEditorResources.cs zdefiniować okno dialogowe, które umożliwia edytowanie tych typów.</span><span class="sxs-lookup"><span data-stu-id="5c34e-193">ArgumentDictionaryEditor.cs, PropertyEditorResources.xaml and PropertyEditorResources.cs define the dialog box that allows you to edit these types.</span></span>  
  
## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5c34e-194">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="5c34e-194">To set up, build, and run the sample</span></span>  
 <span data-ttu-id="5c34e-195">Należy zainstalować program Windows PowerShell, aby uruchomić ten przykład.</span><span class="sxs-lookup"><span data-stu-id="5c34e-195">You must install Windows PowerShell to run this sample.</span></span> <span data-ttu-id="5c34e-196">Z tej lokalizacji można zainstalować programu Windows PowerShell: [programu Windows PowerShell](http://go.microsoft.com/fwlink/?LinkId=150383).</span><span class="sxs-lookup"><span data-stu-id="5c34e-196">Windows PowerShell can be installed from this location: [Windows PowerShell](http://go.microsoft.com/fwlink/?LinkId=150383).</span></span>  
  
#### <a name="to-run-the-coded-client"></a><span data-ttu-id="5c34e-197">Do uruchomienia kodowanych klienta</span><span class="sxs-lookup"><span data-stu-id="5c34e-197">To run the coded client</span></span>  
  
1.  <span data-ttu-id="5c34e-198">Otwórz za pomocą PowerShell.sln [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5c34e-198">Open PowerShell.sln using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="5c34e-199">Kliknij prawym przyciskiem myszy rozwiązanie i jego tworzenia.</span><span class="sxs-lookup"><span data-stu-id="5c34e-199">Right-click the solution and build it.</span></span>  
  
3.  <span data-ttu-id="5c34e-200">Kliknij prawym przyciskiem myszy **CodedClient** projekt i wybierz **Ustaw jako projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="5c34e-200">Right-click the **CodedClient** project and select **Set as Startup Project**.</span></span>  
  
4.  <span data-ttu-id="5c34e-201">Naciśnij klawisze CTRL + F5, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="5c34e-201">Press CTRL+F5 to run the application.</span></span>  
  
#### <a name="to-run-the-designer-client"></a><span data-ttu-id="5c34e-202">Aby uruchomić projektanta klienta</span><span class="sxs-lookup"><span data-stu-id="5c34e-202">To run the designer client</span></span>  
  
1.  <span data-ttu-id="5c34e-203">Otwórz za pomocą PowerShell.sln [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5c34e-203">Open PowerShell.sln using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="5c34e-204">Kliknij prawym przyciskiem myszy rozwiązanie i jego tworzenia.</span><span class="sxs-lookup"><span data-stu-id="5c34e-204">Right-click the solution and build it.</span></span>  
  
3.  <span data-ttu-id="5c34e-205">Kliknij prawym przyciskiem myszy **DesignerClient** projekt i wybierz **Ustaw jako projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="5c34e-205">Right-click the **DesignerClient** project and select **Set as Startup Project**.</span></span>  
  
4.  <span data-ttu-id="5c34e-206">Naciśnij klawisze CTRL + F5, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="5c34e-206">Press CTRL+F5 to run the application.</span></span>  
  
## <a name="known-issues"></a><span data-ttu-id="5c34e-207">Znane problemy</span><span class="sxs-lookup"><span data-stu-id="5c34e-207">Known Issues</span></span>  
  
1.  <span data-ttu-id="5c34e-208">Jeśli odwołuje się do `InvokePowerShell` zestawu działań lub projektu z innego projektu spowoduje błąd kompilacji, może być konieczne ręczne dodanie `<SpecificVersion>True</SpecificVersion>` elementu do pliku .csproj nowy projekt w wierszu, który odwołuje się do `InvokePowerShell`.</span><span class="sxs-lookup"><span data-stu-id="5c34e-208">If referencing the `InvokePowerShell` activity assembly or project from another project results in a build error, you may need to manually add the `<SpecificVersion>True</SpecificVersion>` element to the .csproj file of the new project under the line that references `InvokePowerShell`.</span></span>  
  
2.  <span data-ttu-id="5c34e-209">Jeśli nie zainstalowano programu Windows PowerShell, komunikat o błędzie jest wyświetlany w programie Visual Studio, natychmiast po dodaniu `InvokePowerShell` działania do przepływu pracy:`Workflow Designer encountered problems with your document. Could not load file or assembly ‘System.Management.Automation’ ... or one of its dependencies. The system cannot find the file specified.`</span><span class="sxs-lookup"><span data-stu-id="5c34e-209">If Windows PowerShell is not installed, the following error message is displayed in Visual Studio as soon as you add an `InvokePowerShell` activity onto a workflow: `Workflow Designer encountered problems with your document. Could not load file or assembly ‘System.Management.Automation’ ... or one of its dependencies. The system cannot find the file specified.`</span></span>  
  
3.  <span data-ttu-id="5c34e-210">W programie Windows PowerShell 2.0 programowo wywoływania `$input.MoveNext()` kończy się niepowodzeniem i skrypty, używając `$input.MoveNext()` niezamierzone błędów i wyników.</span><span class="sxs-lookup"><span data-stu-id="5c34e-210">In Windows PowerShell 2.0, programmatically calling `$input.MoveNext()` fails and scripts using `$input.MoveNext()` produce unintended errors and results.</span></span> <span data-ttu-id="5c34e-211">Aby obejść ten problem, należy wziąć pod uwagę przy użyciu programu PowerShell zlecenie `foreach` zamiast wywoływać metodę `MoveNext()` podczas iteracji tablicy.</span><span class="sxs-lookup"><span data-stu-id="5c34e-211">To work around this issue, consider using the PowerShell verb `foreach` instead of calling `MoveNext()` when iterating an array.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5c34e-212">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="5c34e-212">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5c34e-213">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="5c34e-213">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5c34e-214">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="5c34e-214">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5c34e-215">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="5c34e-215">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\PowerShell`