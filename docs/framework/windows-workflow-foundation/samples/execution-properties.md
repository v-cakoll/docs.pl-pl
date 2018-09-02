---
title: Właściwości wykonania
ms.date: 03/30/2017
ms.assetid: 31c009db-397c-4653-87e2-32dc77fa4b13
ms.openlocfilehash: 4906c2ad11c8b5822764435d2b39a5b51f2673ba
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43409092"
---
# <a name="execution-properties"></a><span data-ttu-id="e9574-102">Właściwości wykonania</span><span class="sxs-lookup"><span data-stu-id="e9574-102">Execution Properties</span></span>
<span data-ttu-id="e9574-103">Ten przykład pokazuje jak zdefiniować i wykonywania właściwości należy użyć działań niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="e9574-103">This sample shows how to define and use an execution property in a custom activity.</span></span> <span data-ttu-id="e9574-104">W tym przykładzie właściwość wykonywania Określa kolor pierwszego planu przez konsolę.</span><span class="sxs-lookup"><span data-stu-id="e9574-104">In this example, the execution property determines the console's foreground color.</span></span> <span data-ttu-id="e9574-105">Przykładowy przepływ pracy pokazuje, jak różne ścieżek logicznych wykonywania (gałęzie z <xref:System.Activities.Statements.Parallel> działania) może zachować konsoli różne kolory pomimo przeplatane wykonywanie funkcji działań (w rozgałęzieniach z <xref:System.Activities.Statements.Parallel> działanie).</span><span class="sxs-lookup"><span data-stu-id="e9574-105">An example workflow shows how different logical paths of execution (branches of a <xref:System.Activities.Statements.Parallel> activity) can maintain different console colors despite interleaved execution of activities (across the branches of the <xref:System.Activities.Statements.Parallel> activity).</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e9574-106">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="e9574-106">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="e9574-107">Otwórz rozwiązanie przykładowe ExecutionProperties.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e9574-107">Open the ExecutionProperties.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e9574-108">Wyświetlanie ThreeColors.xaml przed kompilacją rozwiązania wyświetla komunikat o błędzie, ponieważ muszą zostać skompilowane niestandardowe działania, które są używane w tym samym czasie jako rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="e9574-108">Viewing ThreeColors.xaml before building the solution displays an error, because the custom activities used must be built at the same time as the solution.</span></span>  
  
2.  <span data-ttu-id="e9574-109">Skompiluj i uruchom rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="e9574-109">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e9574-110">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="e9574-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e9574-111">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="e9574-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e9574-112">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="e9574-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e9574-113">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="e9574-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\ExecutionProperties`