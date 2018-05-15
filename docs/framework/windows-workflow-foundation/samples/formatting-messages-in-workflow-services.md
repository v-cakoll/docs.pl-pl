---
title: Formatowanie wiadomości w usług przepływu pracy
ms.date: 03/30/2017
ms.assetid: 6d15d44b-20f8-4cb7-bd4f-598c32781ebc
ms.openlocfilehash: eac9f7042dbcbd31f9a8c7d5e56c7b7d2ab62156
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="formatting-messages-in-workflow-services"></a><span data-ttu-id="af78c-102">Formatowanie wiadomości w usług przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="af78c-102">Formatting messages in Workflow Services</span></span>
<span data-ttu-id="af78c-103">W tym przykładzie pokazano sposób inny użytkownik, typy mogą być używane w działaniach obsługi komunikatów (WF usługi).</span><span class="sxs-lookup"><span data-stu-id="af78c-103">This sample shows how different user types can be used in messaging activities (WF services).</span></span> <span data-ttu-id="af78c-104">Usługa próbki jest usługą zatwierdzenia proste wydatków i udostępnia trzy operacje.</span><span class="sxs-lookup"><span data-stu-id="af78c-104">The sample service is a simple expense approval service and exposes three operations.</span></span> <span data-ttu-id="af78c-105">`ApproveExpense` pobiera typ kontraktu danych i przedstawia sposób użycia znanych typów.</span><span class="sxs-lookup"><span data-stu-id="af78c-105">`ApproveExpense` takes a data contract type and shows how to use known types.</span></span> <span data-ttu-id="af78c-106">Zwraca operacji `true` lub `false` na podstawie ilości wydatków.</span><span class="sxs-lookup"><span data-stu-id="af78c-106">The operation returns `true` or `false` based on the expense amount.</span></span> <span data-ttu-id="af78c-107">`ApprovePO` pobiera typ elementu XmlSerializer i zwraca `true` lub `false` na podstawie ilości wydatków.`ApprovedVendor`</span><span class="sxs-lookup"><span data-stu-id="af78c-107">`ApprovePO` takes an XmlSerializer type and returns `true` or `false` based on the expense amount.`ApprovedVendor`</span></span> <span data-ttu-id="af78c-108">pobiera typ kontraktu komunikatu i zwraca `true` lub `false` Jeśli dostawca znajduje się lista zatwierdzonych dostawców lub jeśli żądanie pochodzi z działu finansowego (dział finansowy może używać dowolnego dostawcy).</span><span class="sxs-lookup"><span data-stu-id="af78c-108">takes a message contract type and returns `true` or `false` if the vendor is in the list of approved vendors or if the request came from the finance department (the finance department can use any vendor).</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="af78c-109">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="af78c-109">To use this sample</span></span>  
  
1.  <span data-ttu-id="af78c-110">Załadowanie projektu rozwiązania w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] i skompilować projekt.</span><span class="sxs-lookup"><span data-stu-id="af78c-110">Load the project solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] and build the project.</span></span>  
  
2.  <span data-ttu-id="af78c-111">Najpierw uruchom usługę wygenerowanych w \FormatterService\bin\debug\ [katalogu podstawowego rozwiązania]</span><span class="sxs-lookup"><span data-stu-id="af78c-111">First run the service, generated in [solution base directory]\FormatterService\bin\debug\\</span></span>  
  
3.  <span data-ttu-id="af78c-112">Po drugie Uruchom aplikację klienta wygenerowanego w \FormatterClient\bin\debug [katalogu podstawowego rozwiązania].</span><span class="sxs-lookup"><span data-stu-id="af78c-112">Second, run the Client application generated in [solution base directory]\FormatterClient\bin\debug.</span></span>  
  
4.  <span data-ttu-id="af78c-113">Klient wymaga trzech operacji w usłudze i wyświetla wyniki.</span><span class="sxs-lookup"><span data-stu-id="af78c-113">The client calls three operations on the service and prints the results.</span></span> <span data-ttu-id="af78c-114">Po zakończeniu naciśnij klawisz ENTER, aby zamknąć klienta, a następnie usługi.</span><span class="sxs-lookup"><span data-stu-id="af78c-114">When complete, press ENTER to exit the client and then the service.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="af78c-115">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="af78c-115">The samples may already be installed on your machine.</span></span> <span data-ttu-id="af78c-116">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="af78c-116">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="af78c-117">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="af78c-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="af78c-118">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="af78c-118">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\Formatter`