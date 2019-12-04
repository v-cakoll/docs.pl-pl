---
title: Lokalny kanał
ms.date: 03/30/2017
ms.assetid: fa1917a4-f701-4e82-a439-14a16282c7cc
ms.openlocfilehash: 6bc1fac22f6eed3c9acb6b86f7611cbfb4e1d371
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714884"
---
# <a name="local-channel"></a><span data-ttu-id="adb8c-102">Lokalny kanał</span><span class="sxs-lookup"><span data-stu-id="adb8c-102">Local Channel</span></span>
<span data-ttu-id="adb8c-103">Local Channel to kanał transportu usługi Windows Communication Foundation (WCF) używany do komunikacji w ramach tej samej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="adb8c-103">Local Channel is a Windows Communication Foundation (WCF) transport channel that is used for communication within the same application domain.</span></span> <span data-ttu-id="adb8c-104">Jest to przydatne w scenariuszach, w których klient i usługa działają w tej samej domenie aplikacji, a obciążenie typowym stosem kanału WCF (serializacji i deserializacji komunikatów) musi być nieuniknione.</span><span class="sxs-lookup"><span data-stu-id="adb8c-104">This is useful for scenarios where the client and the service are running in the same application domain and the overhead of the typical WCF channel stack (serialization and deserialization of messages) must be avoided.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="adb8c-105">Przedstawia</span><span class="sxs-lookup"><span data-stu-id="adb8c-105">Demonstrates</span></span>  
 <span data-ttu-id="adb8c-106">Lokalny kanał</span><span class="sxs-lookup"><span data-stu-id="adb8c-106">Local Channel</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="adb8c-107">Dyskusji</span><span class="sxs-lookup"><span data-stu-id="adb8c-107">Discussion</span></span>  
 <span data-ttu-id="adb8c-108">Przykład składa się z dwóch plików projektu:</span><span class="sxs-lookup"><span data-stu-id="adb8c-108">The sample consists of two project files:</span></span>  
  
- <span data-ttu-id="adb8c-109">**LocalChannel**: programowa reprezentacja kanału lokalnego w bieżącej domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="adb8c-109">**LocalChannel**: The programmatic representation of the local channel within the current application domain.</span></span> <span data-ttu-id="adb8c-110">W tym projekcie składnika wysyłającego umieszcza komunikat w kolejce w pamięci, a składnik odbierający anuluje Kolejkowanie wiadomości do wysłania.</span><span class="sxs-lookup"><span data-stu-id="adb8c-110">In this project, the sending component places the message in an in-memory queue and the receiving component de-queues the message to receive it.</span></span>  
  
- <span data-ttu-id="adb8c-111">**ClientAndService**: ten projekt hostuje usługę w aplikacji konsolowej, a następnie uruchamia klienta w celu wywołania usługi z poziomu tej samej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="adb8c-111">**ClientAndService**: This project hosts a service in a console application and then runs a client to call the service from within the same application domain.</span></span>  
  
 <span data-ttu-id="adb8c-112">Projekt lokalnego kanału pomija zarówno stos kanału, jak i proces serializacji, aby zwiększyć szybkość.</span><span class="sxs-lookup"><span data-stu-id="adb8c-112">The local channel design skips both the channel stack and the serialization process to increase speed.</span></span> <span data-ttu-id="adb8c-113">Lokalny kanał transportu jest implementowany przy użyciu kolejki do transportu wywołań usługi z klienta do usługi i zwracania wartości do klienta.</span><span class="sxs-lookup"><span data-stu-id="adb8c-113">The local transport channel is implemented using a queue to transport service calls from the client to the service and to return back the value to the client.</span></span> <span data-ttu-id="adb8c-114">Zamiast serializacji parametrów i zwracanych wartości, przykład kopiuje obiekty.</span><span class="sxs-lookup"><span data-stu-id="adb8c-114">Rather than serializing parameters and return values, the sample copies the objects.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="adb8c-115">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="adb8c-115">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="adb8c-116">Kompiluj i uruchamiaj rozwiązanie LocalChannel.</span><span class="sxs-lookup"><span data-stu-id="adb8c-116">Build and run the LocalChannel solution.</span></span>  
  
2. <span data-ttu-id="adb8c-117">Host usługi jest uruchomiony, a klient wywołuje usługę przy użyciu kanału lokalnego.</span><span class="sxs-lookup"><span data-stu-id="adb8c-117">The service host is started and the client calls the service using the local channel.</span></span> <span data-ttu-id="adb8c-118">Zostanie wyświetlone okno konsoli umożliwiające wyświetlenie wyników wywołania usługi.</span><span class="sxs-lookup"><span data-stu-id="adb8c-118">A console window appears to display the results of the service call.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="adb8c-119">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="adb8c-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="adb8c-120">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="adb8c-120">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="adb8c-121">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="adb8c-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="adb8c-122">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="adb8c-122">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\LocalChannel`
