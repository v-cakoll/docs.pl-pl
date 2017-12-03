---
title: "Właściwości wykonania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 31c009db-397c-4653-87e2-32dc77fa4b13
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fed33544654e6929997567198c0f07346e715d1e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="execution-properties"></a><span data-ttu-id="d11ad-102">Właściwości wykonania</span><span class="sxs-lookup"><span data-stu-id="d11ad-102">Execution Properties</span></span>
<span data-ttu-id="d11ad-103">W tym przykładzie pokazano, jak zdefiniować i wykonanie właściwości należy użyć niestandardowego działania.</span><span class="sxs-lookup"><span data-stu-id="d11ad-103">This sample shows how to define and use an execution property in a custom activity.</span></span> <span data-ttu-id="d11ad-104">W tym przykładzie właściwość wykonywania Określa kolor pierwszego planu konsoli.</span><span class="sxs-lookup"><span data-stu-id="d11ad-104">In this example, the execution property determines the console's foreground color.</span></span> <span data-ttu-id="d11ad-105">Przykładowy przepływ pracy przedstawia sposób różnych ścieżek logicznych wykonywania (gałęzi z <xref:System.Activities.Statements.Parallel> działania) można zachować konsoli różnych kolorów pomimo przeplotem wykonywania działań (przez oddziały <xref:System.Activities.Statements.Parallel> działania).</span><span class="sxs-lookup"><span data-stu-id="d11ad-105">An example workflow shows how different logical paths of execution (branches of a <xref:System.Activities.Statements.Parallel> activity) can maintain different console colors despite interleaved execution of activities (across the branches of the <xref:System.Activities.Statements.Parallel> activity).</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d11ad-106">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="d11ad-106">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="d11ad-107">Otwórz rozwiązanie próbki ExecutionProperties.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d11ad-107">Open the ExecutionProperties.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d11ad-108">Wyświetlanie ThreeColors.xaml przed kompilacją rozwiązania jest wyświetlany błąd, ponieważ muszą zostać skompilowane działań niestandardowych używane w tym samym czasie jako rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="d11ad-108">Viewing ThreeColors.xaml before building the solution displays an error, because the custom activities used must be built at the same time as the solution.</span></span>  
  
2.  <span data-ttu-id="d11ad-109">Tworzenie i uruchamianie rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="d11ad-109">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d11ad-110">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="d11ad-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d11ad-111">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="d11ad-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d11ad-112">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="d11ad-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d11ad-113">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="d11ad-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\ExecutionProperties`