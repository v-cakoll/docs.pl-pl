---
title: Lokalny kanał
ms.date: 03/30/2017
ms.assetid: fa1917a4-f701-4e82-a439-14a16282c7cc
ms.openlocfilehash: 1711909ada4756dd2723f62160eef0ad12c03174
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59333226"
---
# <a name="local-channel"></a><span data-ttu-id="158c3-102">Lokalny kanał</span><span class="sxs-lookup"><span data-stu-id="158c3-102">Local Channel</span></span>
<span data-ttu-id="158c3-103">Lokalny kanał jest Windows Communication Foundation (WCF) kanał transportu, który jest używany do komunikacji w ramach tej samej domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="158c3-103">Local Channel is a Windows Communication Foundation (WCF) transport channel that is used for communication within the same application domain.</span></span> <span data-ttu-id="158c3-104">Jest to przydatne w scenariuszach, w którym klient i usługa są uruchomione w tej samej domenie aplikacji i należy unikać obciążenie typowe stosu kanału WCF (serializacji i deserializacji komunikatów).</span><span class="sxs-lookup"><span data-stu-id="158c3-104">This is useful for scenarios where the client and the service are running in the same application domain and the overhead of the typical WCF channel stack (serialization and deserialization of messages) must be avoided.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="158c3-105">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="158c3-105">Demonstrates</span></span>  
 <span data-ttu-id="158c3-106">Lokalny kanał</span><span class="sxs-lookup"><span data-stu-id="158c3-106">Local Channel</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="158c3-107">Dyskusja</span><span class="sxs-lookup"><span data-stu-id="158c3-107">Discussion</span></span>  
 <span data-ttu-id="158c3-108">Przykład składa się z dwóch plików projektu:</span><span class="sxs-lookup"><span data-stu-id="158c3-108">The sample consists of two project files:</span></span>  
  
-   <span data-ttu-id="158c3-109">**LocalChannel**: Programowe reprezentacja kanałów lokalnych w bieżącej domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="158c3-109">**LocalChannel**: The programmatic representation of the local channel within the current application domain.</span></span> <span data-ttu-id="158c3-110">W tym projekcie wysyłania składnika umieszcza komunikat w kolejce w pamięci i odbieranie składnika cofnąć kolejki komunikatów do jej otrzymania.</span><span class="sxs-lookup"><span data-stu-id="158c3-110">In this project, the sending component places the message in an in-memory queue and the receiving component de-queues the message to receive it.</span></span>  
  
-   <span data-ttu-id="158c3-111">**ClientAndService**: Ten projekt hostuje usługę w aplikacji konsoli, a następnie uruchamia klienta do wywołania z usług w ramach tej samej domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="158c3-111">**ClientAndService**: This project hosts a service in a console application and then runs a client to call the service from within the same application domain.</span></span>  
  
 <span data-ttu-id="158c3-112">Projekt lokalny kanał pomija stosu kanału i zwiększyć szybkość procesu serializacji.</span><span class="sxs-lookup"><span data-stu-id="158c3-112">The local channel design skips both the channel stack and the serialization process to increase speed.</span></span> <span data-ttu-id="158c3-113">Kanał transportowy lokalnego jest implementowany przy użyciu kolejki w celu transportu wywołań usługi od klienta do usługi i zwraca wartość z powrotem do klienta.</span><span class="sxs-lookup"><span data-stu-id="158c3-113">The local transport channel is implemented using a queue to transport service calls from the client to the service and to return back the value to the client.</span></span> <span data-ttu-id="158c3-114">Zamiast serializacji, parametrów i zwracanych wartości, przykładowy skrypt kopiuje obiektów.</span><span class="sxs-lookup"><span data-stu-id="158c3-114">Rather than serializing parameters and return values, the sample copies the objects.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="158c3-115">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="158c3-115">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="158c3-116">Twórz i uruchamiaj rozwiązania LocalChannel.</span><span class="sxs-lookup"><span data-stu-id="158c3-116">Build and run the LocalChannel solution.</span></span>  
  
2. <span data-ttu-id="158c3-117">Host usługi jest uruchomiona, a klient wywołuje usługę za pomocą lokalnego kanału.</span><span class="sxs-lookup"><span data-stu-id="158c3-117">The service host is started and the client calls the service using the local channel.</span></span> <span data-ttu-id="158c3-118">Aby wyświetlić wyniki wywołania usługi zostanie wyświetlone okno konsoli.</span><span class="sxs-lookup"><span data-stu-id="158c3-118">A console window appears to display the results of the service call.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="158c3-119">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="158c3-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="158c3-120">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="158c3-120">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="158c3-121">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="158c3-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="158c3-122">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="158c3-122">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\LocalChannel`
