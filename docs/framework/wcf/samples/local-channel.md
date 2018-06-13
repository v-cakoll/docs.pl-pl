---
title: Lokalny kanał
ms.date: 03/30/2017
ms.assetid: fa1917a4-f701-4e82-a439-14a16282c7cc
ms.openlocfilehash: 2473704c751ad0ea2d2a00bf7f3ea43d6e39498f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33501510"
---
# <a name="local-channel"></a><span data-ttu-id="c58bd-102">Lokalny kanał</span><span class="sxs-lookup"><span data-stu-id="c58bd-102">Local Channel</span></span>
<span data-ttu-id="c58bd-103">Lokalny kanał to kanał transportu Windows Communication Foundation (WCF) używanego do komunikacji w obrębie tej samej domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c58bd-103">Local Channel is a Windows Communication Foundation (WCF) transport channel that is used for communication within the same application domain.</span></span> <span data-ttu-id="c58bd-104">Jest to przydatne w przypadku scenariuszy, w którym klient i usługa są uruchomione w tej samej domenie aplikacji należy unikać obciążenie typowe stosu kanału WCF (serializacji i deserializacji wiadomości).</span><span class="sxs-lookup"><span data-stu-id="c58bd-104">This is useful for scenarios where the client and the service are running in the same application domain and the overhead of the typical WCF channel stack (serialization and deserialization of messages) must be avoided.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="c58bd-105">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="c58bd-105">Demonstrates</span></span>  
 <span data-ttu-id="c58bd-106">Lokalny kanał</span><span class="sxs-lookup"><span data-stu-id="c58bd-106">Local Channel</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="c58bd-107">Omówienie</span><span class="sxs-lookup"><span data-stu-id="c58bd-107">Discussion</span></span>  
 <span data-ttu-id="c58bd-108">Przykład obejmuje dwa pliki projektu:</span><span class="sxs-lookup"><span data-stu-id="c58bd-108">The sample consists of two project files:</span></span>  
  
-   <span data-ttu-id="c58bd-109">**LocalChannel**: programowe reprezentację lokalnego kanału w bieżącej domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c58bd-109">**LocalChannel**: The programmatic representation of the local channel within the current application domain.</span></span> <span data-ttu-id="c58bd-110">W tym projekcie wysyłania składnika umieszcza wiadomości w kolejce w pamięci, a odbierania składnika cofnąć kolejki wiadomości odebrane.</span><span class="sxs-lookup"><span data-stu-id="c58bd-110">In this project, the sending component places the message in an in-memory queue and the receiving component de-queues the message to receive it.</span></span>  
  
-   <span data-ttu-id="c58bd-111">**ClientAndService**: ten projekt obsługuje usługę w aplikacji konsoli, a następnie uruchomi klienta do wywołania przez usługę w tej samej domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c58bd-111">**ClientAndService**: This project hosts a service in a console application and then runs a client to call the service from within the same application domain.</span></span>  
  
 <span data-ttu-id="c58bd-112">Projekt lokalnego kanału pomija zarówno stosu kanału i przyspieszyć proces serializacji.</span><span class="sxs-lookup"><span data-stu-id="c58bd-112">The local channel design skips both the channel stack and the serialization process to increase speed.</span></span> <span data-ttu-id="c58bd-113">Kanał transportu lokalnego jest zaimplementowany przy użyciu kolejki transportu wywołań usługi z klienta do usługi i zwraca wartość z powrotem do klienta.</span><span class="sxs-lookup"><span data-stu-id="c58bd-113">The local transport channel is implemented using a queue to transport service calls from the client to the service and to return back the value to the client.</span></span> <span data-ttu-id="c58bd-114">Zamiast serializacji, parametrów i zwracanych wartości, próbki kopiuje obiektów.</span><span class="sxs-lookup"><span data-stu-id="c58bd-114">Rather than serializing parameters and return values, the sample copies the objects.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c58bd-115">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="c58bd-115">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="c58bd-116">Tworzenie i uruchamianie rozwiązania LocalChannel.</span><span class="sxs-lookup"><span data-stu-id="c58bd-116">Build and run the LocalChannel solution.</span></span>  
  
2.  <span data-ttu-id="c58bd-117">Host usługi jest uruchomiona, a klient wywołuje usługę za pomocą lokalnego kanału.</span><span class="sxs-lookup"><span data-stu-id="c58bd-117">The service host is started and the client calls the service using the local channel.</span></span> <span data-ttu-id="c58bd-118">Aby wyświetlić wyniki wywołania usługi pojawi się okno konsoli.</span><span class="sxs-lookup"><span data-stu-id="c58bd-118">A console window appears to display the results of the service call.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c58bd-119">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="c58bd-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c58bd-120">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="c58bd-120">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c58bd-121">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="c58bd-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c58bd-122">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="c58bd-122">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\LocalChannel`
