---
title: "Podstawowe sposoby użycia SendParameters i ReceiveParameters działania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1b6b1681-3d41-403f-bfe2-3f600f24aa8c
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9c3b6f189f1a2564662af89961c9363f025ae8c3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="basic-usage-of-sendparameters-and-receiveparameters-activities"></a><span data-ttu-id="55d4b-102">Podstawowe sposoby użycia SendParameters i ReceiveParameters działania</span><span class="sxs-lookup"><span data-stu-id="55d4b-102">Basic Usage of SendParameters and ReceiveParameters Activities</span></span>
<span data-ttu-id="55d4b-103">W tym przykładzie pokazano sposób użycia <xref:System.ServiceModel.Activities.SendParametersContent> i <xref:System.ServiceModel.Activities.ReceiveParametersContent> działań.</span><span class="sxs-lookup"><span data-stu-id="55d4b-103">This sample shows the use of <xref:System.ServiceModel.Activities.SendParametersContent> and <xref:System.ServiceModel.Activities.ReceiveParametersContent> activities.</span></span> <span data-ttu-id="55d4b-104">Usługa przedstawia jedną operację, która przyjmuje argument będący ciągiem i zwraca dane wejściowe do klienta.</span><span class="sxs-lookup"><span data-stu-id="55d4b-104">The service exposes one operation that takes a string argument and echoes the input back to the client.</span></span> <span data-ttu-id="55d4b-105">Przykład pokazuje, jak do ustawiania parametrów dla tych działań komunikacji.</span><span class="sxs-lookup"><span data-stu-id="55d4b-105">The sample shows how to set up the parameters for these messaging activities.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="55d4b-106">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="55d4b-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="55d4b-107">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="55d4b-107">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="55d4b-108">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="55d4b-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="55d4b-109">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="55d4b-109">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\SendReceiveParameters`  
  
#### <a name="using-this-sample"></a><span data-ttu-id="55d4b-110">Za pomocą tego przykładu</span><span class="sxs-lookup"><span data-stu-id="55d4b-110">Using this sample</span></span>  
  
1.  <span data-ttu-id="55d4b-111">Załadowanie projektu rozwiązania w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] i skompilować projekt.</span><span class="sxs-lookup"><span data-stu-id="55d4b-111">Load the project solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] and build the project.</span></span>  
  
2.  <span data-ttu-id="55d4b-112">Najpierw uruchom aplikację EchoWorkflowService wygenerowanych w \EchoWorkflowService\bin\debug [katalogu podstawowego rozwiązania].</span><span class="sxs-lookup"><span data-stu-id="55d4b-112">First run the EchoWorkflowService application generated in [solution base directory]\EchoWorkflowService\bin\debug.</span></span>  
  
3.  <span data-ttu-id="55d4b-113">Po drugie Uruchom aplikację EchoWorkflowClient wygenerowanych w \EchoWorkflowClient\bin\debug [katalogu podstawowego rozwiązania].</span><span class="sxs-lookup"><span data-stu-id="55d4b-113">Second, run the EchoWorkflowClient application generated in [solution base directory]\EchoWorkflowClient\bin\debug.</span></span>  
  
4.  <span data-ttu-id="55d4b-114">Klient wywołuje operację Echo i wyświetla wyniki.</span><span class="sxs-lookup"><span data-stu-id="55d4b-114">The client calls Echo operation on the service and prints the results.</span></span> <span data-ttu-id="55d4b-115">Po zakończeniu naciśnij klawisz ENTER, aby zamknąć klienta, a następnie usługi.</span><span class="sxs-lookup"><span data-stu-id="55d4b-115">When complete, press ENTER to exit the client and then the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55d4b-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="55d4b-116">See Also</span></span>
