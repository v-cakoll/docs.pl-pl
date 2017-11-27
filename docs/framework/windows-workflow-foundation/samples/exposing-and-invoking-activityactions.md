---
title: "Udostępnianie i wywoływanie ActivityActions"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 97ce4797-426e-463d-9cc4-1261afad6df4
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8a87e4463689e9301045a55b16af46cb037c1fa5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="exposing-and-invoking-activityactions"></a><span data-ttu-id="60f38-102">Udostępnianie i wywoływanie ActivityActions</span><span class="sxs-lookup"><span data-stu-id="60f38-102">Exposing and Invoking ActivityActions</span></span>
<span data-ttu-id="60f38-103">W tym przykładzie pokazano, jak tworzenie działań niestandardowych, które ma <xref:System.Activities.ActivityAction>.</span><span class="sxs-lookup"><span data-stu-id="60f38-103">This sample demonstrates how to develop a custom activity that has an <xref:System.Activities.ActivityAction>.</span></span> <span data-ttu-id="60f38-104">Również przedstawia sposób użycia tego działania, dostarczając implementację <xref:System.Activities.ActivityAction>.</span><span class="sxs-lookup"><span data-stu-id="60f38-104">It also demonstrates how to use this activity by providing an implementation of the <xref:System.Activities.ActivityAction>.</span></span>  
  
 <span data-ttu-id="60f38-105"><xref:System.Activities.ActivityAction> Umożliwia autorowi działania ujawnia "dziury" z określonych podpisów gdzie działania użytkownika można dodać niestandardowe zachowanie.</span><span class="sxs-lookup"><span data-stu-id="60f38-105">An <xref:System.Activities.ActivityAction> allows an activity author to expose "holes" with specific signatures where the activity user can plug in a custom behavior.</span></span> <span data-ttu-id="60f38-106">Na przykład <!--zz <xref:System.Activities.Statements.ForEach>--> `System.Activities.Statements.ForEach` działania (które działa przez kolekcję elementów), ma <xref:System.Activities.ActivityAction> umożliwiająca użytkownikowi działanie Dołącz zachowanie, który działa w bieżącym elemencie iteracji.</span><span class="sxs-lookup"><span data-stu-id="60f38-106">For example, the <!--zz <xref:System.Activities.Statements.ForEach>--> `System.Activities.Statements.ForEach` activity, (which operates over a collection of items), has an <xref:System.Activities.ActivityAction> that allows the activity user to plug in behavior that operates on the current iteration item.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="60f38-107">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="60f38-107">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="60f38-108">Otwórz **ActivityAction.sln** przykładowe rozwiązanie w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="60f38-108">Open the **ActivityAction.sln** sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="60f38-109">Tworzenie i uruchamianie rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="60f38-109">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="60f38-110">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="60f38-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="60f38-111">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="60f38-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="60f38-112">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="60f38-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="60f38-113">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="60f38-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\ActivityAction`  
  
## <a name="see-also"></a><span data-ttu-id="60f38-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="60f38-114">See Also</span></span>
