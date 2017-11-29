---
title: "Przy użyciu AsyncOperationContext w przykładowym działania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0888a0bd-d227-4c00-ad6a-b654a01740e8
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: aa2a68bccb4daff380b8de7368c6709c41c5799a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="using-asyncoperationcontext-in-an-activity-sample"></a><span data-ttu-id="27c76-102">Przy użyciu AsyncOperationContext w przykładowym działania</span><span class="sxs-lookup"><span data-stu-id="27c76-102">Using AsyncOperationContext in an Activity Sample</span></span>
<span data-ttu-id="27c76-103">W tym przykładzie pokazano, jak utworzyć niestandardowy <xref:System.Activities.CodeActivity> używającą <xref:System.Activities.AsyncCodeActivityContext> do wykonywania pracy asynchronicznie poza przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="27c76-103">This sample demonstrates how to develop a custom <xref:System.Activities.CodeActivity> that uses <xref:System.Activities.AsyncCodeActivityContext> to perform work asynchronously outside of the workflow.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="27c76-104">Szczegóły próbki</span><span class="sxs-lookup"><span data-stu-id="27c76-104">Sample Details</span></span>  
 <span data-ttu-id="27c76-105">Przykładowe działanie używa <xref:System.IO.FileStream.BeginWrite%2A> i <xref:System.IO.FileStream.EndWrite%2A> metody <xref:System.IO.FileStream> klasy do asynchronicznego zapisu danych do pliku.</span><span class="sxs-lookup"><span data-stu-id="27c76-105">The sample activity uses the <xref:System.IO.FileStream.BeginWrite%2A> and <xref:System.IO.FileStream.EndWrite%2A> methods on the <xref:System.IO.FileStream> class to asynchronously write data to a file.</span></span> <span data-ttu-id="27c76-106">Wzorzec wprowadzone w tym miejscu, mogą być dostosowywane do użycia z innych metod asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="27c76-106">The pattern introduced here can be adapted for use with other asynchronous methods.</span></span> <span data-ttu-id="27c76-107">Podczas wykonywania operacji asynchronicznej innych działań w przepływie pracy można wykonać, ale nie może zostać utrwalona przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="27c76-107">While the asynchronous operation is executing, other activities in the workflow can execute, but the workflow cannot be persisted.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="27c76-108">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="27c76-108">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="27c76-109">Otwórz rozwiązanie próbki Async.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="27c76-109">Open the Async.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="27c76-110">Tworzenie i uruchamianie rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="27c76-110">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="27c76-111">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="27c76-111">The samples may already be installed on your machine.</span></span> <span data-ttu-id="27c76-112">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="27c76-112">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="27c76-113">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="27c76-113">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="27c76-114">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="27c76-114">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\Async`  
  
## <a name="see-also"></a><span data-ttu-id="27c76-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="27c76-115">See Also</span></span>
