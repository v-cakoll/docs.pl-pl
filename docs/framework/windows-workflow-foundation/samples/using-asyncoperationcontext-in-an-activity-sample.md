---
title: Używanie AsyncOperationContext w przykładzie działania
ms.date: 03/30/2017
ms.assetid: 0888a0bd-d227-4c00-ad6a-b654a01740e8
ms.openlocfilehash: 4358a364a3f7ec69b7c1c548fcf82fe494f37505
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45742891"
---
# <a name="using-asyncoperationcontext-in-an-activity-sample"></a><span data-ttu-id="98e4b-102">Używanie AsyncOperationContext w przykładzie działania</span><span class="sxs-lookup"><span data-stu-id="98e4b-102">Using AsyncOperationContext in an Activity Sample</span></span>
<span data-ttu-id="98e4b-103">W tym przykładzie pokazano, jak tworzyć niestandardowe <xref:System.Activities.CodeActivity> , który używa <xref:System.Activities.AsyncCodeActivityContext> do wykonywania pracy asynchronicznie poza przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="98e4b-103">This sample demonstrates how to develop a custom <xref:System.Activities.CodeActivity> that uses <xref:System.Activities.AsyncCodeActivityContext> to perform work asynchronously outside of the workflow.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="98e4b-104">Przykład szczegółów</span><span class="sxs-lookup"><span data-stu-id="98e4b-104">Sample Details</span></span>  
 <span data-ttu-id="98e4b-105">Korzysta z przykładowym działaniem <xref:System.IO.FileStream.BeginWrite%2A> i <xref:System.IO.FileStream.EndWrite%2A> metod <xref:System.IO.FileStream> klasy do asynchronicznego zapisu danych do pliku.</span><span class="sxs-lookup"><span data-stu-id="98e4b-105">The sample activity uses the <xref:System.IO.FileStream.BeginWrite%2A> and <xref:System.IO.FileStream.EndWrite%2A> methods on the <xref:System.IO.FileStream> class to asynchronously write data to a file.</span></span> <span data-ttu-id="98e4b-106">Wzorzec wprowadzone w tym miejscu mogą być dostosowane do użytku z innych metod asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="98e4b-106">The pattern introduced here can be adapted for use with other asynchronous methods.</span></span> <span data-ttu-id="98e4b-107">Podczas wykonywania operacji asynchronicznej może wykonywać inne działania w przepływie pracy, ale nie może zostać utrwalona przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="98e4b-107">While the asynchronous operation is executing, other activities in the workflow can execute, but the workflow cannot be persisted.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="98e4b-108">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="98e4b-108">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="98e4b-109">Otwórz rozwiązanie przykładowe Async.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="98e4b-109">Open the Async.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="98e4b-110">Skompiluj i uruchom rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="98e4b-110">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="98e4b-111">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="98e4b-111">The samples may already be installed on your machine.</span></span> <span data-ttu-id="98e4b-112">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="98e4b-112">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="98e4b-113">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="98e4b-113">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="98e4b-114">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="98e4b-114">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\Async`