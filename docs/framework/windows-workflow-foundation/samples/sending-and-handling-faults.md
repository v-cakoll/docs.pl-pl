---
title: "Wysyłanie i obsługa błędów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 98e8e04d-2ac9-4a33-ae08-462f757a7a14
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fc91b431123ff8776910550151a7783b2690d383
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="sending-and-handling-faults"></a><span data-ttu-id="903da-102">Wysyłanie i obsługa błędów</span><span class="sxs-lookup"><span data-stu-id="903da-102">Sending and Handling Faults</span></span>
<span data-ttu-id="903da-103">W tym przykładzie przedstawiono sposób użycia <xref:System.ServiceModel.Activities.SendReply> i <xref:System.ServiceModel.Activities.ReceiveReply> wiadomości działań do wysyłania i odbierania oczekiwane i nieoczekiwane błędy.</span><span class="sxs-lookup"><span data-stu-id="903da-103">This sample demonstrates how to use the <xref:System.ServiceModel.Activities.SendReply> and <xref:System.ServiceModel.Activities.ReceiveReply> messaging activities to send and receive expected and unexpected faults.</span></span> <span data-ttu-id="903da-104">W tym scenariuszu pierwszy klient żąda powoduje błąd oczekiwanego, która została uwzględniona w jego <xref:System.ServiceModel.Activities.Send.KnownTypes%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="903da-104">In this scenario, the first client request results in an expected fault that has been included in its <xref:System.ServiceModel.Activities.Send.KnownTypes%2A> collection.</span></span> <span data-ttu-id="903da-105">Następny kilka żądań klientów powoduje odbieranie nieoczekiwanych błędów, przed ostatnim żądanie zakończy się sukcesem.</span><span class="sxs-lookup"><span data-stu-id="903da-105">The next few client requests result in receiving unexpected faults, before the final request succeeds.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="903da-106">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="903da-106">To use this sample</span></span>  
  
1.  <span data-ttu-id="903da-107">Otwórz [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] z podwyższonym poziomem uprawnień, klikając prawym przyciskiem myszy [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ikony, jak i wybierając **Uruchom jako administrator**.</span><span class="sxs-lookup"><span data-stu-id="903da-107">Open [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] with elevated permissions, by right-clicking the [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] icon and selecting **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="903da-108">Otwórz plik rozwiązania Faults.sln.</span><span class="sxs-lookup"><span data-stu-id="903da-108">Open the Faults.sln solution file.</span></span>  
  
3.  <span data-ttu-id="903da-109">Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="903da-109">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
4.  <span data-ttu-id="903da-110">Uruchom projekt dla usługi.</span><span class="sxs-lookup"><span data-stu-id="903da-110">Run the service project.</span></span>  
  
    1.  <span data-ttu-id="903da-111">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy `FaultService` projekt i wybierz **Ustaw jako projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="903da-111">In **Solution Explorer**, right-click the `FaultService` project and select **Set as StartUp Project**.</span></span>  
  
    2.  <span data-ttu-id="903da-112">Naciśnij klawisze CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="903da-112">Press CTRL+F5.</span></span>  
  
5.  <span data-ttu-id="903da-113">Otwórz inną kopię [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] z podwyższonym poziomem uprawnień, klikając prawym przyciskiem myszy [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ikony, jak i wybierając **Uruchom jako administrator**.</span><span class="sxs-lookup"><span data-stu-id="903da-113">Open another copy of [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] with elevated permissions, by right-clicking the [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] icon and selecting **Run as administrator**.</span></span>  
  
6.  <span data-ttu-id="903da-114">Otwórz plik rozwiązania Faults.sln.</span><span class="sxs-lookup"><span data-stu-id="903da-114">Open the Faults.sln solution file.</span></span>  
  
7.  <span data-ttu-id="903da-115">Uruchamianie projektu klienta.</span><span class="sxs-lookup"><span data-stu-id="903da-115">Run the client project.</span></span>  
  
    1.  <span data-ttu-id="903da-116">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy `FaultClient` projekt i wybierz **Ustaw jako projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="903da-116">In **Solution Explorer**, right-click the `FaultClient` project and select **Set as StartUp Project**.</span></span>  
  
    2.  <span data-ttu-id="903da-117">Naciśnij klawisze CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="903da-117">Press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="903da-118">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="903da-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="903da-119">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="903da-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="903da-120">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="903da-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="903da-121">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="903da-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\Faults`