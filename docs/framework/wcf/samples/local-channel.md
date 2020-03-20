---
title: Lokalny kanał
ms.date: 03/30/2017
ms.assetid: fa1917a4-f701-4e82-a439-14a16282c7cc
ms.openlocfilehash: 87e140395ac2fb5702d8655cf970da8a60c991ec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144510"
---
# <a name="local-channel"></a><span data-ttu-id="72546-102">Lokalny kanał</span><span class="sxs-lookup"><span data-stu-id="72546-102">Local Channel</span></span>
<span data-ttu-id="72546-103">Kanał lokalny to kanał transportu Programu Windows Communication Foundation (WCF), który jest używany do komunikacji w tej samej domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="72546-103">Local Channel is a Windows Communication Foundation (WCF) transport channel that is used for communication within the same application domain.</span></span> <span data-ttu-id="72546-104">Jest to przydatne w scenariuszach, w których klient i usługa są uruchomione w tej samej domenie aplikacji i obciążenie typowego stosu kanału WCF (serializacji i deserializacji wiadomości) należy unikać.</span><span class="sxs-lookup"><span data-stu-id="72546-104">This is useful for scenarios where the client and the service are running in the same application domain and the overhead of the typical WCF channel stack (serialization and deserialization of messages) must be avoided.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="72546-105">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="72546-105">Demonstrates</span></span>  
 <span data-ttu-id="72546-106">Lokalny kanał</span><span class="sxs-lookup"><span data-stu-id="72546-106">Local Channel</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="72546-107">Dyskusji</span><span class="sxs-lookup"><span data-stu-id="72546-107">Discussion</span></span>  
 <span data-ttu-id="72546-108">Próbka składa się z dwóch plików projektu:</span><span class="sxs-lookup"><span data-stu-id="72546-108">The sample consists of two project files:</span></span>  
  
- <span data-ttu-id="72546-109">**LocalChannel**: Programowa reprezentacja kanału lokalnego w bieżącej domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="72546-109">**LocalChannel**: The programmatic representation of the local channel within the current application domain.</span></span> <span data-ttu-id="72546-110">W tym projekcie składnik wysyłania umieszcza wiadomość w kolejce w pamięci, a składnik odbierający usuwa kolejki wiadomości, aby ją odebrać.</span><span class="sxs-lookup"><span data-stu-id="72546-110">In this project, the sending component places the message in an in-memory queue and the receiving component de-queues the message to receive it.</span></span>  
  
- <span data-ttu-id="72546-111">**ClientAndService:** Ten projekt obsługuje usługę w aplikacji konsoli, a następnie uruchamia klienta, aby wywołać usługę z tej samej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="72546-111">**ClientAndService**: This project hosts a service in a console application and then runs a client to call the service from within the same application domain.</span></span>  
  
 <span data-ttu-id="72546-112">Projekt kanału lokalnego pomija zarówno stos kanału, jak i proces serializacji, aby zwiększyć szybkość.</span><span class="sxs-lookup"><span data-stu-id="72546-112">The local channel design skips both the channel stack and the serialization process to increase speed.</span></span> <span data-ttu-id="72546-113">Kanał transportu lokalnego jest implementowany przy użyciu kolejki do transportu wywołań usługi od klienta do usługi i do powrotu wartości do klienta.</span><span class="sxs-lookup"><span data-stu-id="72546-113">The local transport channel is implemented using a queue to transport service calls from the client to the service and to return back the value to the client.</span></span> <span data-ttu-id="72546-114">Zamiast serializacji parametrów i zwracanych wartości, próbka kopiuje obiekty.</span><span class="sxs-lookup"><span data-stu-id="72546-114">Rather than serializing parameters and return values, the sample copies the objects.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="72546-115">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="72546-115">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="72546-116">Tworzenie i uruchamianie rozwiązania LocalChannel.</span><span class="sxs-lookup"><span data-stu-id="72546-116">Build and run the LocalChannel solution.</span></span>  
  
2. <span data-ttu-id="72546-117">Host usługi jest uruchamiany, a klient wywołuje usługę przy użyciu kanału lokalnego.</span><span class="sxs-lookup"><span data-stu-id="72546-117">The service host is started and the client calls the service using the local channel.</span></span> <span data-ttu-id="72546-118">Pojawi się okno konsoli, aby wyświetlić wyniki wywołania usługi.</span><span class="sxs-lookup"><span data-stu-id="72546-118">A console window appears to display the results of the service call.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="72546-119">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="72546-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="72546-120">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="72546-120">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="72546-121">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="72546-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="72546-122">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="72546-122">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\LocalChannel`
