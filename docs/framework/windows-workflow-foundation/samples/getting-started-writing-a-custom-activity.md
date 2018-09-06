---
title: Wprowadzenie do zapisu działania niestandardowego
ms.date: 03/30/2017
ms.assetid: 3902f5fa-8a43-4048-8a6a-6b15472f90f0
ms.openlocfilehash: 4d9c140ca230750ca1119b33252b1edb8796d458
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43776661"
---
# <a name="getting-started-writing-a-custom-activity"></a><span data-ttu-id="48376-102">Wprowadzenie do zapisu działania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="48376-102">Getting Started Writing a Custom Activity</span></span>
<span data-ttu-id="48376-103">Niniejszy przykład pokazuje jak zdefiniować proste działanie niestandardowe w XAML.</span><span class="sxs-lookup"><span data-stu-id="48376-103">This sample demonstrates how to define a simple custom activity in XAML.</span></span> <span data-ttu-id="48376-104">Działanie jest nadawana nazwa `Rhyme`, i swojej logiki jest sekwencją trzy <xref:System.Activities.Statements.WriteLine> działań.</span><span class="sxs-lookup"><span data-stu-id="48376-104">The activity is given the name `Rhyme`, and its logic is a sequence of three <xref:System.Activities.Statements.WriteLine> activities.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="48376-105">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="48376-105">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="48376-106">Otwórz **Simple.sln** przykładowe rozwiązanie w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="48376-106">Open the **Simple.sln** sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="48376-107">Skompiluj i uruchom rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="48376-107">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="48376-108">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="48376-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="48376-109">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="48376-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="48376-110">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="48376-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="48376-111">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="48376-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Composite\GettingStarted`