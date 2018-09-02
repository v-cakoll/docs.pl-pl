---
title: Uwidacznianie i wywoływanie działań ActivityActions
ms.date: 03/30/2017
ms.assetid: 97ce4797-426e-463d-9cc4-1261afad6df4
ms.openlocfilehash: f36d88fc54e5150927113ed8825fbccad84129d4
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43387597"
---
# <a name="exposing-and-invoking-activityactions"></a><span data-ttu-id="b5562-102">Uwidacznianie i wywoływanie działań ActivityActions</span><span class="sxs-lookup"><span data-stu-id="b5562-102">Exposing and Invoking ActivityActions</span></span>
<span data-ttu-id="b5562-103">W tym przykładzie pokazano, jak tworzyć niestandardowe działanie, które ma <xref:System.Activities.ActivityAction>.</span><span class="sxs-lookup"><span data-stu-id="b5562-103">This sample demonstrates how to develop a custom activity that has an <xref:System.Activities.ActivityAction>.</span></span> <span data-ttu-id="b5562-104">Ilustruje też sposób użycia tego działania, zapewniając implementację <xref:System.Activities.ActivityAction>.</span><span class="sxs-lookup"><span data-stu-id="b5562-104">It also demonstrates how to use this activity by providing an implementation of the <xref:System.Activities.ActivityAction>.</span></span>  
  
 <span data-ttu-id="b5562-105"><xref:System.Activities.ActivityAction> Umożliwia autorowi działania do udostępnienia "otworów" przy użyciu określonej sygnatury niestandardowe zachowanie, na którym użytkownik działania można podłączyć.</span><span class="sxs-lookup"><span data-stu-id="b5562-105">An <xref:System.Activities.ActivityAction> allows an activity author to expose "holes" with specific signatures where the activity user can plug in a custom behavior.</span></span> <span data-ttu-id="b5562-106">Na przykład <!--zz <xref:System.Activities.Statements.ForEach>--> `System.Activities.Statements.ForEach` działania (który działa przez kolekcję elementów), ma <xref:System.Activities.ActivityAction> umożliwiająca użytkownikowi działanie wtyczki zachowanie, które działa w bieżącym elemencie iteracji.</span><span class="sxs-lookup"><span data-stu-id="b5562-106">For example, the <!--zz <xref:System.Activities.Statements.ForEach>--> `System.Activities.Statements.ForEach` activity, (which operates over a collection of items), has an <xref:System.Activities.ActivityAction> that allows the activity user to plug in behavior that operates on the current iteration item.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b5562-107">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="b5562-107">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="b5562-108">Otwórz **ActivityAction.sln** przykładowe rozwiązanie w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b5562-108">Open the **ActivityAction.sln** sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="b5562-109">Skompiluj i uruchom rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="b5562-109">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b5562-110">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="b5562-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b5562-111">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="b5562-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b5562-112">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="b5562-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b5562-113">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="b5562-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\ActivityAction`