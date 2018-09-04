---
title: Podstawowe użycia sposoby i ReceiveParameters działań
ms.date: 03/30/2017
ms.assetid: 1b6b1681-3d41-403f-bfe2-3f600f24aa8c
ms.openlocfilehash: c13999ad1571a6413e30e801b6c642000f8e4654
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43504011"
---
# <a name="basic-usage-of-sendparameters-and-receiveparameters-activities"></a><span data-ttu-id="20e25-102">Podstawowe użycia sposoby i ReceiveParameters działań</span><span class="sxs-lookup"><span data-stu-id="20e25-102">Basic Usage of SendParameters and ReceiveParameters Activities</span></span>
<span data-ttu-id="20e25-103">W tym przykładzie przedstawiono użycie <xref:System.ServiceModel.Activities.SendParametersContent> i <xref:System.ServiceModel.Activities.ReceiveParametersContent> działań.</span><span class="sxs-lookup"><span data-stu-id="20e25-103">This sample shows the use of <xref:System.ServiceModel.Activities.SendParametersContent> and <xref:System.ServiceModel.Activities.ReceiveParametersContent> activities.</span></span> <span data-ttu-id="20e25-104">Usługa udostępnia jedna operacja, która przyjmuje argument ciąg i zwraca dane wejściowe do klienta.</span><span class="sxs-lookup"><span data-stu-id="20e25-104">The service exposes one operation that takes a string argument and echoes the input back to the client.</span></span> <span data-ttu-id="20e25-105">Przykład przedstawia sposób ustawiania parametrów dla tych działań dotyczących komunikatów.</span><span class="sxs-lookup"><span data-stu-id="20e25-105">The sample shows how to set up the parameters for these messaging activities.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="20e25-106">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="20e25-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="20e25-107">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="20e25-107">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="20e25-108">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="20e25-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="20e25-109">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="20e25-109">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\SendReceiveParameters`  
  
#### <a name="using-this-sample"></a><span data-ttu-id="20e25-110">Za pomocą tego przykładu</span><span class="sxs-lookup"><span data-stu-id="20e25-110">Using this sample</span></span>  
  
1.  <span data-ttu-id="20e25-111">Załaduj projekt rozwiązanie w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] i skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="20e25-111">Load the project solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] and build the project.</span></span>  
  
2.  <span data-ttu-id="20e25-112">Pierwszym uruchomieniu aplikacji EchoWorkflowService wygenerowane w \EchoWorkflowService\bin\debug [katalog podstawowy rozwiązania].</span><span class="sxs-lookup"><span data-stu-id="20e25-112">First run the EchoWorkflowService application generated in [solution base directory]\EchoWorkflowService\bin\debug.</span></span>  
  
3.  <span data-ttu-id="20e25-113">Po drugie Uruchom aplikację EchoWorkflowClient, wygenerowane w \EchoWorkflowClient\bin\debug [katalog podstawowy rozwiązania].</span><span class="sxs-lookup"><span data-stu-id="20e25-113">Second, run the EchoWorkflowClient application generated in [solution base directory]\EchoWorkflowClient\bin\debug.</span></span>  
  
4.  <span data-ttu-id="20e25-114">Klient wywołuje działanie usługi Echo i drukuje wyniki.</span><span class="sxs-lookup"><span data-stu-id="20e25-114">The client calls Echo operation on the service and prints the results.</span></span> <span data-ttu-id="20e25-115">Po zakończeniu naciśnij klawisz ENTER, aby zamknąć klienta, a następnie usługi.</span><span class="sxs-lookup"><span data-stu-id="20e25-115">When complete, press ENTER to exit the client and then the service.</span></span>