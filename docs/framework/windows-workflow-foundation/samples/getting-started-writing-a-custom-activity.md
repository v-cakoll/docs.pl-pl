---
title: Pobieranie rozpoczęte pisania działania niestandardowego
ms.date: 03/30/2017
ms.assetid: 3902f5fa-8a43-4048-8a6a-6b15472f90f0
ms.openlocfilehash: 1c455009a0c658429c13da5e93d07c744402dd61
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="getting-started-writing-a-custom-activity"></a><span data-ttu-id="29ec6-102">Pobieranie rozpoczęte pisania działania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="29ec6-102">Getting Started Writing a Custom Activity</span></span>
<span data-ttu-id="29ec6-103">W przykładzie pokazano sposób definiowania proste działania niestandardowego w języku XAML.</span><span class="sxs-lookup"><span data-stu-id="29ec6-103">This sample demonstrates how to define a simple custom activity in XAML.</span></span> <span data-ttu-id="29ec6-104">Działanie podano nazwę `Rhyme`, i jego logiki jest sekwencją trzy <xref:System.Activities.Statements.WriteLine> działań.</span><span class="sxs-lookup"><span data-stu-id="29ec6-104">The activity is given the name `Rhyme`, and its logic is a sequence of three <xref:System.Activities.Statements.WriteLine> activities.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="29ec6-105">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="29ec6-105">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="29ec6-106">Otwórz **Simple.sln** przykładowe rozwiązanie w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="29ec6-106">Open the **Simple.sln** sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="29ec6-107">Tworzenie i uruchamianie rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="29ec6-107">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="29ec6-108">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="29ec6-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="29ec6-109">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="29ec6-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="29ec6-110">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="29ec6-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="29ec6-111">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="29ec6-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Composite\GettingStarted`