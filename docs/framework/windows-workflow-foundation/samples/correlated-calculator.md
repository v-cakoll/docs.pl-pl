---
title: Skorelowany Kalkulator
ms.date: 03/30/2017
ms.assetid: c365166e-6552-49a4-bf17-9f4e597d4d41
ms.openlocfilehash: 71cfdd0906ef20ec36b76ef5e508a4551b9fe3fe
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43517316"
---
# <a name="correlated-calculator"></a><span data-ttu-id="cde7b-102">Skorelowany Kalkulator</span><span class="sxs-lookup"><span data-stu-id="cde7b-102">Correlated Calculator</span></span>
<span data-ttu-id="cde7b-103">W tym przykładzie przedstawiono sposób użycia działań dotyczących komunikatów (<xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply>) w Projektancie z korelacją opartego na zawartości, na podstawie parametru w komunikacie.</span><span class="sxs-lookup"><span data-stu-id="cde7b-103">This sample demonstrates how to use the messaging activities (<xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply>) in the designer with content-based correlation based on a parameter in the message.</span></span> <span data-ttu-id="cde7b-104">W tym scenariuszu operacje Kalkulator znajdują się w konwoju równoległych.</span><span class="sxs-lookup"><span data-stu-id="cde7b-104">In this scenario, the operations of the calculator are in a parallel convoy.</span></span> <span data-ttu-id="cde7b-105">Zarówno w przypadku wystąpienia, jak i korelacja (na podstawie `CalculatorId`) są tworzone, gdy pierwszy komunikat jest wysyłany do przepływu pracy, a kolejne komunikaty z taką samą `CalculatorId` są wysyłane do tego wystąpienia, dopóki nie jest wywoływana przez operację resetowania.</span><span class="sxs-lookup"><span data-stu-id="cde7b-105">Both an instance and a correlation (based on `CalculatorId`) are created when the first message is sent to the workflow, and subsequent messages with the same `CalculatorId` are dispatched to that instance until the Reset operation is called.</span></span> <span data-ttu-id="cde7b-106">Klient jest implementowany jako aplikację WPF, która używa serwer proxy oparty na kodzie klienta do komunikowania się z usługą.</span><span class="sxs-lookup"><span data-stu-id="cde7b-106">The client is implemented as a WPF application that uses a code-based client proxy to communicate with the service.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="cde7b-107">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="cde7b-107">To use this sample</span></span>  
  
1.  <span data-ttu-id="cde7b-108">Rozpocznij [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] w podwyższonym poziomem uprawnień, otwórz plik rozwiązania For.sln.</span><span class="sxs-lookup"><span data-stu-id="cde7b-108">Start [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] in elevated permissions, open the For.sln solution file.</span></span>  
  
    1.  <span data-ttu-id="cde7b-109">Przejdź do folderu, który zawiera [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cde7b-109">Navigate to the folder that contains [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
    2.  <span data-ttu-id="cde7b-110">Kliknij prawym przyciskiem myszy Devenv.exe, a następnie wybierz pozycję **Uruchom jako administrator**.</span><span class="sxs-lookup"><span data-stu-id="cde7b-110">Right-click Devenv.exe and select **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="cde7b-111">Za pomocą [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania CorrelatedCalculator.sln.</span><span class="sxs-lookup"><span data-stu-id="cde7b-111">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the CorrelatedCalculator.sln solution file.</span></span>  
  
3.  <span data-ttu-id="cde7b-112">Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="cde7b-112">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
4.  <span data-ttu-id="cde7b-113">Aby uruchomić projekt usługi, naciśnij kombinację klawiszy CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="cde7b-113">To run the service project, press CTRL+F5.</span></span>  
  
5.  <span data-ttu-id="cde7b-114">Gdy usługa jest gotowy i nasłuchuje komunikatów w Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt klienta, a następnie uruchom go.</span><span class="sxs-lookup"><span data-stu-id="cde7b-114">Once the service is ready and listening for messages, in Solution Explorer, right-click the Client project and run it.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="cde7b-115">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="cde7b-115">The samples may already be installed on your machine.</span></span> <span data-ttu-id="cde7b-116">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="cde7b-116">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="cde7b-117">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="cde7b-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cde7b-118">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="cde7b-118">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\CorellatedCalculator`