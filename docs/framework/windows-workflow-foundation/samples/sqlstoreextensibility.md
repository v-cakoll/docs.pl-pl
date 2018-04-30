---
title: SQLStoreExtensibility
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5da1b5a3-f144-41ba-b9c4-02818b28b15d
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 722c7cda49b2efc4c146970c69cc5e3c7bbad9b0
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="sqlstoreextensibility"></a><span data-ttu-id="fb679-102">SQLStoreExtensibility</span><span class="sxs-lookup"><span data-stu-id="fb679-102">SQLStoreExtensibility</span></span>
<span data-ttu-id="fb679-103">W przykładzie pokazano, używanie i konfigurację awansowanej właściwości w magazynie wystąpień przepływu pracy SQL.</span><span class="sxs-lookup"><span data-stu-id="fb679-103">This sample demonstrates the use and configuration of promoted properties in the SQL workflow instance store.</span></span> <span data-ttu-id="fb679-104">W magazynie wystąpień przepływu pracy SQL jest implementacją SQL na podstawie wystąpienia magazynu.</span><span class="sxs-lookup"><span data-stu-id="fb679-104">The SQL workflow instance store is a SQL-based implementation of an instance store.</span></span> <span data-ttu-id="fb679-105">Umożliwia on wystąpienie do zapisywania stanu i ładowania stanu do i z bazy danych programu SQL Server lub SQL Server Express.</span><span class="sxs-lookup"><span data-stu-id="fb679-105">It allows an instance to save its state and load its state to and from a SQL Server or SQL Server Express database.</span></span> <span data-ttu-id="fb679-106">Funkcja rozszerzalność magazyn zezwala użytkownikowi na definiowanie właściwości, które są przechowywane w magazynie wystąpień.</span><span class="sxs-lookup"><span data-stu-id="fb679-106">The store extensibility feature allows the user to define properties that are stored in the instance store.</span></span> <span data-ttu-id="fb679-107">Te właściwości są wyświetlane w widoku awansowanej właściwości, które umożliwia użytkownikowi zapytania dla nich.</span><span class="sxs-lookup"><span data-stu-id="fb679-107">These properties are displayed in a promoted properties view that allows the user to query for them.</span></span>  
  
 <span data-ttu-id="fb679-108">W tym przykładzie składa się z przepływu pracy, który implementuje usługi zliczania.</span><span class="sxs-lookup"><span data-stu-id="fb679-108">This sample consists of a workflow that implements a counting service.</span></span> <span data-ttu-id="fb679-109">Po wywołaniu metody uruchamiania usługi, usługi liczby z zakresu od 0 do 29.</span><span class="sxs-lookup"><span data-stu-id="fb679-109">Once the service's start method is invoked, the service counts from 0 to 29.</span></span> <span data-ttu-id="fb679-110">Licznik jest zwiększany co 2 sekundy.</span><span class="sxs-lookup"><span data-stu-id="fb679-110">The counter is incremented once every 2 seconds.</span></span> <span data-ttu-id="fb679-111">Po każdej liczby utrzymuje przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="fb679-111">After each count, the workflow persists.</span></span> <span data-ttu-id="fb679-112">Bieżącą wartość licznika jest przechowywane w magazynie wystąpień jako awansowanej właściwości.</span><span class="sxs-lookup"><span data-stu-id="fb679-112">The current counter value is stored in the instance store as a promoted property.</span></span>  
  
 <span data-ttu-id="fb679-113">Przepływ pracy zliczania własnym jest hostowana przez hosta usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="fb679-113">The Counting Workflow is self-hosted by a Workflow Service Host.</span></span> <span data-ttu-id="fb679-114">Program `Main` metoda wykonuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="fb679-114">The program's `Main` method performs the following actions:</span></span>  
  
-   <span data-ttu-id="fb679-115">Tworzy wystąpienie obsługuje zliczania przepływu pracy, który definiuje punkty końcowe, w których zliczania przepływu pracy można połączyć się z hosta usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="fb679-115">Creates an instance of the Workflow Service Host that hosts the Counting Workflow and defines the endpoints under which the Counting Workflow can be reached.</span></span>  
  
-   <span data-ttu-id="fb679-116">Definiuje SQL zachowanie magazynu wystąpienia przepływu pracy, który służy do konfigurowania w magazynie wystąpień przepływu pracy programu SQL.</span><span class="sxs-lookup"><span data-stu-id="fb679-116">Defines a SQL workflow instance store behavior, which is used to configure the SQL workflow instance store.</span></span> <span data-ttu-id="fb679-117">Magazyn jest instrukcją traktować `CountStatus` jako awansowanej właściwości.</span><span class="sxs-lookup"><span data-stu-id="fb679-117">The store is instructed to treat `CountStatus` as a promoted property.</span></span>  
  
-   <span data-ttu-id="fb679-118">Tworzy klienta, który wywołuje metodę start zliczania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="fb679-118">Creates a client that calls the start method of the counting workflow.</span></span>  
  
 <span data-ttu-id="fb679-119">Po uruchomieniu programu licznik uruchamia się automatycznie zliczania.</span><span class="sxs-lookup"><span data-stu-id="fb679-119">Once the program is started, the counter automatically starts counting.</span></span> <span data-ttu-id="fb679-120">Należy pamiętać, że może zająć kilka sekund, aby załadować wystąpienie i skonfigurować Magazyn wystąpienia przepływu pracy programu SQL.</span><span class="sxs-lookup"><span data-stu-id="fb679-120">Note that it might take a few seconds to load the instance and configure the SQL workflow instance store.</span></span>  
  
 <span data-ttu-id="fb679-121">Aby promować wartość licznika jako właściwość niestandardową, należy podjąć następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="fb679-121">To promote the counter value as a custom property, the following steps must be taken:</span></span>  
  
1.  <span data-ttu-id="fb679-122">Klasa `CounterStatus` definiuje rozszerzenie wystąpienia typu <xref:System.Activities.Persistence.PersistenceParticipant>, używany do dostarczania zmienne stanu przez działania.</span><span class="sxs-lookup"><span data-stu-id="fb679-122">The class `CounterStatus` defines an instance extension of type <xref:System.Activities.Persistence.PersistenceParticipant>, which is used by activities to supply the state variables.</span></span> <span data-ttu-id="fb679-123">`Count` nie zdefiniowano jako wartość tylko do zapisu.</span><span class="sxs-lookup"><span data-stu-id="fb679-123">`Count` is defined as a write-only value.</span></span> <span data-ttu-id="fb679-124">Gdy do punktu utrwalania wystąpienia przepływu pracy, rozszerzenie wystąpienia zapisuje `Count` właściwości do zbierania danych trwałości.</span><span class="sxs-lookup"><span data-stu-id="fb679-124">When a workflow instance comes to a persistence point, the instance extension saves the `Count` property into the persistence data collection.</span></span>  
  
2.  <span data-ttu-id="fb679-125">Podczas tworzenia w magazynie wystąpień nową właściwość `CountStatus`, jest zdefiniowana za pomocą `store.Promote()` metody.</span><span class="sxs-lookup"><span data-stu-id="fb679-125">When creating the instance store, a new property, `CountStatus`, is defined through the `store.Promote()` method.</span></span>  
  
3.  <span data-ttu-id="fb679-126">Przepływ pracy `SaveCounter` działania przypisuje bieżącą wartość licznika `Count` pole stanu.</span><span class="sxs-lookup"><span data-stu-id="fb679-126">The workflow's `SaveCounter` activity assigns the current counter value to the `Count` status field.</span></span>  
  
### <a name="to-use-this-sample"></a><span data-ttu-id="fb679-127">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="fb679-127">To use this sample</span></span>  
  
1.  <span data-ttu-id="fb679-128">Utwórz wystąpienie bazy danych magazynu.</span><span class="sxs-lookup"><span data-stu-id="fb679-128">Create the instance store database.</span></span>  
  
    1.  <span data-ttu-id="fb679-129">Otwórz [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="fb679-129">Open a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt.</span></span>  
  
    2.  <span data-ttu-id="fb679-130">Przejdź do katalogu próbki (\WF\Basic\Persistence\SqlStoreExtensibility\CS) i uruchom CreateInstanceStore.cmd [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="fb679-130">Navigate to the sample directory (\WF\Basic\Persistence\SqlStoreExtensibility\CS) and run CreateInstanceStore.cmd in the [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt.</span></span>  
  
        > [!WARNING]
        >  <span data-ttu-id="fb679-131">Skrypt CreateInstanceStore.cmd próbuje utworzyć bazę danych w domyślnym wystąpieniu programu SQL Server 2008 Express.</span><span class="sxs-lookup"><span data-stu-id="fb679-131">The CreateInstanceStore.cmd script attempts to create the database on the default instance of SQL Server 2008 Express.</span></span> <span data-ttu-id="fb679-132">Jeśli chcesz zainstalować bazy danych w innym wystąpieniu, należy zmodyfikować skrypt, aby to zrobić.</span><span class="sxs-lookup"><span data-stu-id="fb679-132">If you want to install the database on a different instance, modify the script to do so.</span></span>  
  
2.  <span data-ttu-id="fb679-133">Otwórz [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] i załadowania rozwiązania SqlStoreExtensibility.sln i skompiluj go, naciskając klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="fb679-133">Open [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] and load the SqlStoreExtensibility.sln solution and build it by pressing CTRL+SHIFT+B.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="fb679-134">Jeśli zainstalowano bazy danych w innych niż domyślne wystąpienie programu SQL Server, należy zaktualizować parametry połączenia w kodzie przed kompilacją rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="fb679-134">If you installed the database on a non-default instance of SQL Server, update the connection string in the code prior to building the solution.</span></span>  
  
3.  <span data-ttu-id="fb679-135">Uruchom próbki z uprawnieniami administratora, przechodząc do katalogu bin projektu (\WF\Basic\Persistence\SqlStoreExtensibility\bin\Debug) w [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], klikając prawym przyciskiem myszy SqlStoreExtensibility.exe i wybierając **Uruchom jako Administrator**.</span><span class="sxs-lookup"><span data-stu-id="fb679-135">Run the sample with administrator privileges by navigating to the project’s bin directory (\WF\Basic\Persistence\SqlStoreExtensibility\bin\Debug) in [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], right-clicking SqlStoreExtensibility.exe and selecting **Run as Administrator**.</span></span>  
  
### <a name="to-verify-the-sample-is-working-correctly"></a><span data-ttu-id="fb679-136">Aby zweryfikować próbki działa poprawnie</span><span class="sxs-lookup"><span data-stu-id="fb679-136">To verify the sample is working correctly</span></span>  
  
1.  <span data-ttu-id="fb679-137">Użyj programu SQL Server Management Studio, aby wyświetlić zawartość tej tabeli wystąpienia, wybierając **baz danych**, **InstanceStore**, a następnie  **System.ServiceModel.Activities.DurableInstancing.InstanceTable** w Eksploratorze obiektów kliknij prawym przyciskiem myszy **System.ServiceModel.Activities.DurableInstancing.InstanceTable** i wybierz  **Zaznacz 1000 pierwszych wierszy**.</span><span class="sxs-lookup"><span data-stu-id="fb679-137">Use SQL Server Management Studio to view the contents of the instance table by selecting **Databases**, **InstanceStore**, and then **System.ServiceModel.Activities.DurableInstancing.InstanceTable** in the Object Explorer, right-click **System.ServiceModel.Activities.DurableInstancing.InstanceTable** and select **Select Top 1000 Rows**.</span></span> <span data-ttu-id="fb679-138">Aby uzyskać więcej informacji na temat programu SQL Server Management Studio, zobacz [wprowadzenie do programu SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkId=165645)</span><span class="sxs-lookup"><span data-stu-id="fb679-138">For more information about SQL Server Management Studio, see [Introducing SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkId=165645)</span></span>  
  
2.  <span data-ttu-id="fb679-139">Obserwować wystąpień przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="fb679-139">Observe the workflow instances listed.</span></span>  
  
3.  <span data-ttu-id="fb679-140">W [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] wiersza polecenia, uruchom skrypt QueryInstanceStore.cmd znajduje się w katalogu próbki (\WF\Basic\Persistence\SqlStoreExtensibility).</span><span class="sxs-lookup"><span data-stu-id="fb679-140">In a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt, run the QueryInstanceStore.cmd script located in the sample directory (\WF\Basic\Persistence\SqlStoreExtensibility).</span></span>  
  
4.  <span data-ttu-id="fb679-141">Sprawdź wartość licznika jest wyświetlany w obszarze **CountStatus**.</span><span class="sxs-lookup"><span data-stu-id="fb679-141">Observe the counter value displayed under **CountStatus**.</span></span>  
  
5.  <span data-ttu-id="fb679-142">Uruchom skrypt kilka razy wyświetlić **CountStats** wartość zmiany.</span><span class="sxs-lookup"><span data-stu-id="fb679-142">Run the script a few times to see the **CountStats** value change.</span></span>  
  
6.  <span data-ttu-id="fb679-143">Naciśnij klawisz ENTER, aby zakończyć działanie aplikacji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="fb679-143">Press ENTER to terminate the workflow application.</span></span>  
  
### <a name="to-uninstall-the-sample"></a><span data-ttu-id="fb679-144">Aby odinstalować próbki</span><span class="sxs-lookup"><span data-stu-id="fb679-144">To uninstall the sample</span></span>  
  
1.  <span data-ttu-id="fb679-145">Usuń bazę danych magazynu wystąpienia przez uruchomienie skryptu RemoveInstanceStore.cmd znajduje się w katalogu próbki (\WF\Basic\Persistence\SqlStoreExtensibility).</span><span class="sxs-lookup"><span data-stu-id="fb679-145">Remove the instance store database by running the RemoveInstanceStore.cmd script located in the sample directory (\WF\Basic\Persistence\SqlStoreExtensibility).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="fb679-146">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="fb679-146">The samples may already be installed on your machine.</span></span> <span data-ttu-id="fb679-147">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="fb679-147">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="fb679-148">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="fb679-148">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fb679-149">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="fb679-149">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\SQLStoreExtensibility`  
  
## <a name="see-also"></a><span data-ttu-id="fb679-150">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fb679-150">See Also</span></span>  
 [<span data-ttu-id="fb679-151">Trwałość przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="fb679-151">Workflow Persistence</span></span>](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)  
 [<span data-ttu-id="fb679-152">Usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="fb679-152">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [<span data-ttu-id="fb679-153">Przykłady trwałości i hostingu AppFabric</span><span class="sxs-lookup"><span data-stu-id="fb679-153">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
