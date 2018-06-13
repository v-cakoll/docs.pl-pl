---
title: Kalkulator skorelowane
ms.date: 03/30/2017
ms.assetid: c365166e-6552-49a4-bf17-9f4e597d4d41
ms.openlocfilehash: 77e13b3ca913d2432cfe5d4a95e83764effbb109
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33514144"
---
# <a name="correlated-calculator"></a><span data-ttu-id="303ee-102">Kalkulator skorelowane</span><span class="sxs-lookup"><span data-stu-id="303ee-102">Correlated Calculator</span></span>
<span data-ttu-id="303ee-103">W tym przykładzie przedstawiono sposób użycia działania obsługi komunikatów (<xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply>) w Projektancie z korelacją na podstawie zawartości na podstawie parametru w komunikacie.</span><span class="sxs-lookup"><span data-stu-id="303ee-103">This sample demonstrates how to use the messaging activities (<xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply>) in the designer with content-based correlation based on a parameter in the message.</span></span> <span data-ttu-id="303ee-104">W tym scenariuszu operacje Kalkulator znajdują się w który równoległych.</span><span class="sxs-lookup"><span data-stu-id="303ee-104">In this scenario, the operations of the calculator are in a parallel convoy.</span></span> <span data-ttu-id="303ee-105">Zarówno wystąpienia, jak i korelacja (na podstawie `CalculatorId`) są tworzone, gdy pierwszy komunikat jest wysyłany do przepływu pracy i kolejnych komunikatów o takim samym `CalculatorId` są wysyłane do tego wystąpienia, dopóki nosi nazwę operację resetowania.</span><span class="sxs-lookup"><span data-stu-id="303ee-105">Both an instance and a correlation (based on `CalculatorId`) are created when the first message is sent to the workflow, and subsequent messages with the same `CalculatorId` are dispatched to that instance until the Reset operation is called.</span></span> <span data-ttu-id="303ee-106">Klient jest implementowany jako aplikacji WPF, która używa serwera proxy klienta oparte na kodzie do komunikowania się z usługą.</span><span class="sxs-lookup"><span data-stu-id="303ee-106">The client is implemented as a WPF application that uses a code-based client proxy to communicate with the service.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="303ee-107">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="303ee-107">To use this sample</span></span>  
  
1.  <span data-ttu-id="303ee-108">Uruchom [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] w podwyższonym poziomem uprawnień, otwórz plik rozwiązania For.sln.</span><span class="sxs-lookup"><span data-stu-id="303ee-108">Start [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] in elevated permissions, open the For.sln solution file.</span></span>  
  
    1.  <span data-ttu-id="303ee-109">Przejdź do folderu, który zawiera [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="303ee-109">Navigate to the folder that contains [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
    2.  <span data-ttu-id="303ee-110">Kliknij prawym przyciskiem myszy Devenv.exe i wybierz **Uruchom jako administrator**.</span><span class="sxs-lookup"><span data-stu-id="303ee-110">Right-click Devenv.exe and select **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="303ee-111">Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania CorrelatedCalculator.sln.</span><span class="sxs-lookup"><span data-stu-id="303ee-111">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the CorrelatedCalculator.sln solution file.</span></span>  
  
3.  <span data-ttu-id="303ee-112">Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="303ee-112">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
4.  <span data-ttu-id="303ee-113">Aby uruchomić projekt usługi, naciśnij kombinację klawiszy CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="303ee-113">To run the service project, press CTRL+F5.</span></span>  
  
5.  <span data-ttu-id="303ee-114">Gdy usługa jest gotowa i nasłuchiwania dla wiadomości w Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt klienta i uruchom go.</span><span class="sxs-lookup"><span data-stu-id="303ee-114">Once the service is ready and listening for messages, in Solution Explorer, right-click the Client project and run it.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="303ee-115">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="303ee-115">The samples may already be installed on your machine.</span></span> <span data-ttu-id="303ee-116">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="303ee-116">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="303ee-117">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="303ee-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="303ee-118">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="303ee-118">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\CorellatedCalculator`