---
title: Kalkulator skorelowane
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c365166e-6552-49a4-bf17-9f4e597d4d41
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 53d96e090edabc65b7356497c3726d29e46c4ea7
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2017
---
# <a name="correlated-calculator"></a><span data-ttu-id="24d61-102">Kalkulator skorelowane</span><span class="sxs-lookup"><span data-stu-id="24d61-102">Correlated Calculator</span></span>
<span data-ttu-id="24d61-103">W tym przykładzie przedstawiono sposób użycia działania obsługi komunikatów (<xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply>) w Projektancie z korelacją na podstawie zawartości na podstawie parametru w komunikacie.</span><span class="sxs-lookup"><span data-stu-id="24d61-103">This sample demonstrates how to use the messaging activities (<xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply>) in the designer with content-based correlation based on a parameter in the message.</span></span> <span data-ttu-id="24d61-104">W tym scenariuszu operacje Kalkulator znajdują się w który równoległych.</span><span class="sxs-lookup"><span data-stu-id="24d61-104">In this scenario, the operations of the calculator are in a parallel convoy.</span></span> <span data-ttu-id="24d61-105">Zarówno wystąpienia, jak i korelacja (na podstawie `CalculatorId`) są tworzone, gdy pierwszy komunikat jest wysyłany do przepływu pracy i kolejnych komunikatów o takim samym `CalculatorId` są wysyłane do tego wystąpienia, dopóki nosi nazwę operację resetowania.</span><span class="sxs-lookup"><span data-stu-id="24d61-105">Both an instance and a correlation (based on `CalculatorId`) are created when the first message is sent to the workflow, and subsequent messages with the same `CalculatorId` are dispatched to that instance until the Reset operation is called.</span></span> <span data-ttu-id="24d61-106">Klient jest implementowany jako aplikacji WPF, która używa serwera proxy klienta oparte na kodzie do komunikowania się z usługą.</span><span class="sxs-lookup"><span data-stu-id="24d61-106">The client is implemented as a WPF application that uses a code-based client proxy to communicate with the service.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="24d61-107">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="24d61-107">To use this sample</span></span>  
  
1.  <span data-ttu-id="24d61-108">Uruchom [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] w podwyższonym poziomem uprawnień, otwórz plik rozwiązania For.sln.</span><span class="sxs-lookup"><span data-stu-id="24d61-108">Start [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] in elevated permissions, open the For.sln solution file.</span></span>  
  
    1.  <span data-ttu-id="24d61-109">Przejdź do folderu, który zawiera [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="24d61-109">Navigate to the folder that contains [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
    2.  <span data-ttu-id="24d61-110">Kliknij prawym przyciskiem myszy Devenv.exe i wybierz **Uruchom jako administrator**.</span><span class="sxs-lookup"><span data-stu-id="24d61-110">Right-click Devenv.exe and select **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="24d61-111">Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania CorrelatedCalculator.sln.</span><span class="sxs-lookup"><span data-stu-id="24d61-111">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the CorrelatedCalculator.sln solution file.</span></span>  
  
3.  <span data-ttu-id="24d61-112">Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="24d61-112">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
4.  <span data-ttu-id="24d61-113">Aby uruchomić projekt usługi, naciśnij kombinację klawiszy CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="24d61-113">To run the service project, press CTRL+F5.</span></span>  
  
5.  <span data-ttu-id="24d61-114">Gdy usługa jest gotowa i nasłuchiwania dla wiadomości w Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt klienta i uruchom go.</span><span class="sxs-lookup"><span data-stu-id="24d61-114">Once the service is ready and listening for messages, in Solution Explorer, right-click the Client project and run it.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="24d61-115">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="24d61-115">The samples may already be installed on your machine.</span></span> <span data-ttu-id="24d61-116">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="24d61-116">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="24d61-117">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="24d61-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="24d61-118">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="24d61-118">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\CorellatedCalculator`