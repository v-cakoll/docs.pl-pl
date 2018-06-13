---
title: Przy użyciu AsyncOperationContext w przykładowym działania
ms.date: 03/30/2017
ms.assetid: 0888a0bd-d227-4c00-ad6a-b654a01740e8
ms.openlocfilehash: da7b62ef9e29621d1e6ee1046afb5455af1164bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515500"
---
# <a name="using-asyncoperationcontext-in-an-activity-sample"></a><span data-ttu-id="2bc69-102">Przy użyciu AsyncOperationContext w przykładowym działania</span><span class="sxs-lookup"><span data-stu-id="2bc69-102">Using AsyncOperationContext in an Activity Sample</span></span>
<span data-ttu-id="2bc69-103">W tym przykładzie pokazano, jak utworzyć niestandardowy <xref:System.Activities.CodeActivity> używającą <xref:System.Activities.AsyncCodeActivityContext> do wykonywania pracy asynchronicznie poza przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="2bc69-103">This sample demonstrates how to develop a custom <xref:System.Activities.CodeActivity> that uses <xref:System.Activities.AsyncCodeActivityContext> to perform work asynchronously outside of the workflow.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="2bc69-104">Szczegóły próbki</span><span class="sxs-lookup"><span data-stu-id="2bc69-104">Sample Details</span></span>  
 <span data-ttu-id="2bc69-105">Przykładowe działanie używa <xref:System.IO.FileStream.BeginWrite%2A> i <xref:System.IO.FileStream.EndWrite%2A> metody <xref:System.IO.FileStream> klasy do asynchronicznego zapisu danych do pliku.</span><span class="sxs-lookup"><span data-stu-id="2bc69-105">The sample activity uses the <xref:System.IO.FileStream.BeginWrite%2A> and <xref:System.IO.FileStream.EndWrite%2A> methods on the <xref:System.IO.FileStream> class to asynchronously write data to a file.</span></span> <span data-ttu-id="2bc69-106">Wzorzec wprowadzone w tym miejscu, mogą być dostosowywane do użycia z innych metod asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="2bc69-106">The pattern introduced here can be adapted for use with other asynchronous methods.</span></span> <span data-ttu-id="2bc69-107">Podczas wykonywania operacji asynchronicznej innych działań w przepływie pracy można wykonać, ale nie może zostać utrwalona przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="2bc69-107">While the asynchronous operation is executing, other activities in the workflow can execute, but the workflow cannot be persisted.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2bc69-108">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="2bc69-108">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="2bc69-109">Otwórz rozwiązanie próbki Async.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2bc69-109">Open the Async.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="2bc69-110">Tworzenie i uruchamianie rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="2bc69-110">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2bc69-111">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="2bc69-111">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2bc69-112">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="2bc69-112">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="2bc69-113">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="2bc69-113">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2bc69-114">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="2bc69-114">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\Async`