---
title: Udostępnianie i wywoływanie ActivityActions
ms.date: 03/30/2017
ms.assetid: 97ce4797-426e-463d-9cc4-1261afad6df4
ms.openlocfilehash: 2d369ec4b028b047ce02016dd511c1c088b46a91
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33513155"
---
# <a name="exposing-and-invoking-activityactions"></a><span data-ttu-id="080cd-102">Udostępnianie i wywoływanie ActivityActions</span><span class="sxs-lookup"><span data-stu-id="080cd-102">Exposing and Invoking ActivityActions</span></span>
<span data-ttu-id="080cd-103">W tym przykładzie pokazano, jak tworzenie działań niestandardowych, które ma <xref:System.Activities.ActivityAction>.</span><span class="sxs-lookup"><span data-stu-id="080cd-103">This sample demonstrates how to develop a custom activity that has an <xref:System.Activities.ActivityAction>.</span></span> <span data-ttu-id="080cd-104">Również przedstawia sposób użycia tego działania, dostarczając implementację <xref:System.Activities.ActivityAction>.</span><span class="sxs-lookup"><span data-stu-id="080cd-104">It also demonstrates how to use this activity by providing an implementation of the <xref:System.Activities.ActivityAction>.</span></span>  
  
 <span data-ttu-id="080cd-105"><xref:System.Activities.ActivityAction> Umożliwia autorowi działania ujawnia "dziury" z określonych podpisów gdzie działania użytkownika można dodać niestandardowe zachowanie.</span><span class="sxs-lookup"><span data-stu-id="080cd-105">An <xref:System.Activities.ActivityAction> allows an activity author to expose "holes" with specific signatures where the activity user can plug in a custom behavior.</span></span> <span data-ttu-id="080cd-106">Na przykład <!--zz <xref:System.Activities.Statements.ForEach>--> `System.Activities.Statements.ForEach` działania (które działa przez kolekcję elementów), ma <xref:System.Activities.ActivityAction> umożliwiająca użytkownikowi działanie Dołącz zachowanie, który działa w bieżącym elemencie iteracji.</span><span class="sxs-lookup"><span data-stu-id="080cd-106">For example, the <!--zz <xref:System.Activities.Statements.ForEach>--> `System.Activities.Statements.ForEach` activity, (which operates over a collection of items), has an <xref:System.Activities.ActivityAction> that allows the activity user to plug in behavior that operates on the current iteration item.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="080cd-107">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="080cd-107">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="080cd-108">Otwórz **ActivityAction.sln** przykładowe rozwiązanie w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="080cd-108">Open the **ActivityAction.sln** sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="080cd-109">Tworzenie i uruchamianie rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="080cd-109">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="080cd-110">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="080cd-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="080cd-111">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="080cd-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="080cd-112">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="080cd-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="080cd-113">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="080cd-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\ActivityAction`