---
title: Wysyłanie i obsługa błędów
ms.date: 03/30/2017
ms.assetid: 98e8e04d-2ac9-4a33-ae08-462f757a7a14
ms.openlocfilehash: 896f209e7daeeab2bb33c1fde15298aae96c8776
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43406661"
---
# <a name="sending-and-handling-faults"></a><span data-ttu-id="65cab-102">Wysyłanie i obsługa błędów</span><span class="sxs-lookup"><span data-stu-id="65cab-102">Sending and Handling Faults</span></span>
<span data-ttu-id="65cab-103">W tym przykładzie przedstawiono sposób użycia <xref:System.ServiceModel.Activities.SendReply> i <xref:System.ServiceModel.Activities.ReceiveReply> wiadomości działania do wysyłania i odbierania oczekiwane i nieoczekiwane błędy.</span><span class="sxs-lookup"><span data-stu-id="65cab-103">This sample demonstrates how to use the <xref:System.ServiceModel.Activities.SendReply> and <xref:System.ServiceModel.Activities.ReceiveReply> messaging activities to send and receive expected and unexpected faults.</span></span> <span data-ttu-id="65cab-104">W tym scenariuszu pierwszy klient żąda wyniki w oczekiwanym domenach błędów, która została uwzględniona w jego <xref:System.ServiceModel.Activities.Send.KnownTypes%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="65cab-104">In this scenario, the first client request results in an expected fault that has been included in its <xref:System.ServiceModel.Activities.Send.KnownTypes%2A> collection.</span></span> <span data-ttu-id="65cab-105">Dalej kilka żądań klientów doprowadzić do odbierania nieoczekiwane błędy przed ostatnim żądanie zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="65cab-105">The next few client requests result in receiving unexpected faults, before the final request succeeds.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="65cab-106">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="65cab-106">To use this sample</span></span>  
  
1.  <span data-ttu-id="65cab-107">Otwórz [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] z podwyższonym poziomem uprawnień, klikając prawym przyciskiem myszy [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ikonę i wybierając polecenie **Uruchom jako administrator**.</span><span class="sxs-lookup"><span data-stu-id="65cab-107">Open [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] with elevated permissions, by right-clicking the [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] icon and selecting **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="65cab-108">Otwórz plik rozwiązania Faults.sln.</span><span class="sxs-lookup"><span data-stu-id="65cab-108">Open the Faults.sln solution file.</span></span>  
  
3.  <span data-ttu-id="65cab-109">Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="65cab-109">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
4.  <span data-ttu-id="65cab-110">Uruchamianie projektu usługi.</span><span class="sxs-lookup"><span data-stu-id="65cab-110">Run the service project.</span></span>  
  
    1.  <span data-ttu-id="65cab-111">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy `FaultService` projektu, a następnie wybierz **Ustaw jako projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="65cab-111">In **Solution Explorer**, right-click the `FaultService` project and select **Set as StartUp Project**.</span></span>  
  
    2.  <span data-ttu-id="65cab-112">Naciśnij kombinację klawiszy CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="65cab-112">Press CTRL+F5.</span></span>  
  
5.  <span data-ttu-id="65cab-113">Otwórz inną kopię [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] z podwyższonym poziomem uprawnień, klikając prawym przyciskiem myszy [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ikonę i wybierając polecenie **Uruchom jako administrator**.</span><span class="sxs-lookup"><span data-stu-id="65cab-113">Open another copy of [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] with elevated permissions, by right-clicking the [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] icon and selecting **Run as administrator**.</span></span>  
  
6.  <span data-ttu-id="65cab-114">Otwórz plik rozwiązania Faults.sln.</span><span class="sxs-lookup"><span data-stu-id="65cab-114">Open the Faults.sln solution file.</span></span>  
  
7.  <span data-ttu-id="65cab-115">Uruchom projekt klienta.</span><span class="sxs-lookup"><span data-stu-id="65cab-115">Run the client project.</span></span>  
  
    1.  <span data-ttu-id="65cab-116">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy `FaultClient` projektu, a następnie wybierz **Ustaw jako projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="65cab-116">In **Solution Explorer**, right-click the `FaultClient` project and select **Set as StartUp Project**.</span></span>  
  
    2.  <span data-ttu-id="65cab-117">Naciśnij kombinację klawiszy CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="65cab-117">Press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="65cab-118">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="65cab-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="65cab-119">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="65cab-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="65cab-120">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="65cab-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="65cab-121">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="65cab-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\Faults`