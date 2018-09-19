---
title: Formatowanie wiadomości w usługach przepływu pracy
ms.date: 03/30/2017
ms.assetid: 6d15d44b-20f8-4cb7-bd4f-598c32781ebc
ms.openlocfilehash: eb9a6b3a83a28154dc968bd4c1c41d34028bdd41
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46003038"
---
# <a name="formatting-messages-in-workflow-services"></a><span data-ttu-id="20f84-102">Formatowanie wiadomości w usługach przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="20f84-102">Formatting messages in Workflow Services</span></span>
<span data-ttu-id="20f84-103">Niniejszy przykład pokazuje jak innego użytkownika, typy mogą być używane w działań dotyczących komunikatów (WF usługi).</span><span class="sxs-lookup"><span data-stu-id="20f84-103">This sample shows how different user types can be used in messaging activities (WF services).</span></span> <span data-ttu-id="20f84-104">Usługa próbki jest usługą zatwierdzenia proste wydatków i udostępnia trzy operacje.</span><span class="sxs-lookup"><span data-stu-id="20f84-104">The sample service is a simple expense approval service and exposes three operations.</span></span> <span data-ttu-id="20f84-105">`ApproveExpense` pobiera typ kontraktu danych i pokazuje, jak używać znanych typów.</span><span class="sxs-lookup"><span data-stu-id="20f84-105">`ApproveExpense` takes a data contract type and shows how to use known types.</span></span> <span data-ttu-id="20f84-106">Operacja zwraca `true` lub `false` oparte na ilości wydatków.</span><span class="sxs-lookup"><span data-stu-id="20f84-106">The operation returns `true` or `false` based on the expense amount.</span></span> <span data-ttu-id="20f84-107">`ApprovePO` Typ elementu XmlSerializer przyjmuje i zwraca `true` lub `false` oparte na ilości wydatków.`ApprovedVendor`</span><span class="sxs-lookup"><span data-stu-id="20f84-107">`ApprovePO` takes an XmlSerializer type and returns `true` or `false` based on the expense amount.`ApprovedVendor`</span></span> <span data-ttu-id="20f84-108">pobiera typ kontraktu komunikatu i zwraca `true` lub `false` czy dostawca jest na liście zatwierdzonych dostawców, czy żądanie pochodzi z działu finansowego (dział finansowy może używać dowolnego dostawcy).</span><span class="sxs-lookup"><span data-stu-id="20f84-108">takes a message contract type and returns `true` or `false` if the vendor is in the list of approved vendors or if the request came from the finance department (the finance department can use any vendor).</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="20f84-109">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="20f84-109">To use this sample</span></span>  
  
1.  <span data-ttu-id="20f84-110">Załaduj projekt rozwiązanie w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] i skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="20f84-110">Load the project solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] and build the project.</span></span>  
  
2.  <span data-ttu-id="20f84-111">Najpierw uruchom usługę, wygenerowane w \FormatterService\bin\debug\ [katalog podstawowy rozwiązania]</span><span class="sxs-lookup"><span data-stu-id="20f84-111">First run the service, generated in [solution base directory]\FormatterService\bin\debug\\</span></span>  
  
3.  <span data-ttu-id="20f84-112">Po drugie Uruchom aplikację klienta, wygenerowane w \FormatterClient\bin\debug [katalog podstawowy rozwiązania].</span><span class="sxs-lookup"><span data-stu-id="20f84-112">Second, run the Client application generated in [solution base directory]\FormatterClient\bin\debug.</span></span>  
  
4.  <span data-ttu-id="20f84-113">Klient wywołuje trzy operacje w usłudze i drukuje wyniki.</span><span class="sxs-lookup"><span data-stu-id="20f84-113">The client calls three operations on the service and prints the results.</span></span> <span data-ttu-id="20f84-114">Po zakończeniu naciśnij klawisz ENTER, aby zamknąć klienta, a następnie usługi.</span><span class="sxs-lookup"><span data-stu-id="20f84-114">When complete, press ENTER to exit the client and then the service.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="20f84-115">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="20f84-115">The samples may already be installed on your machine.</span></span> <span data-ttu-id="20f84-116">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="20f84-116">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="20f84-117">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="20f84-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="20f84-118">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="20f84-118">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\Formatter`