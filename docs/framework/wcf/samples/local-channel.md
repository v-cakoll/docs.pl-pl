---
title: "Lokalny kanał"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fa1917a4-f701-4e82-a439-14a16282c7cc
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: dee09b8f7b1e48a84fa79381d44fe48a4da16129
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="local-channel"></a><span data-ttu-id="e4d3e-102">Lokalny kanał</span><span class="sxs-lookup"><span data-stu-id="e4d3e-102">Local Channel</span></span>
<span data-ttu-id="e4d3e-103">Lokalny kanał jest [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] kanał transportu, który jest używany do komunikacji w obrębie tej samej domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e4d3e-103">Local Channel is a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] transport channel that is used for communication within the same application domain.</span></span> <span data-ttu-id="e4d3e-104">Jest to przydatne w przypadku scenariuszy, w którym klient i usługa są uruchomione w tej samej domenie aplikacji należy unikać obciążenie typowe stosu kanału WCF (serializacji i deserializacji wiadomości).</span><span class="sxs-lookup"><span data-stu-id="e4d3e-104">This is useful for scenarios where the client and the service are running in the same application domain and the overhead of the typical WCF channel stack (serialization and deserialization of messages) must be avoided.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="e4d3e-105">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="e4d3e-105">Demonstrates</span></span>  
 <span data-ttu-id="e4d3e-106">Lokalny kanał</span><span class="sxs-lookup"><span data-stu-id="e4d3e-106">Local Channel</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="e4d3e-107">Omówienie</span><span class="sxs-lookup"><span data-stu-id="e4d3e-107">Discussion</span></span>  
 <span data-ttu-id="e4d3e-108">Przykład obejmuje dwa pliki projektu:</span><span class="sxs-lookup"><span data-stu-id="e4d3e-108">The sample consists of two project files:</span></span>  
  
-   <span data-ttu-id="e4d3e-109">**LocalChannel**: programowe reprezentację lokalnego kanału w bieżącej domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e4d3e-109">**LocalChannel**: The programmatic representation of the local channel within the current application domain.</span></span> <span data-ttu-id="e4d3e-110">W tym projekcie wysyłania składnika umieszcza wiadomości w kolejce w pamięci, a odbierania składnika cofnąć kolejki wiadomości odebrane.</span><span class="sxs-lookup"><span data-stu-id="e4d3e-110">In this project, the sending component places the message in an in-memory queue and the receiving component de-queues the message to receive it.</span></span>  
  
-   <span data-ttu-id="e4d3e-111">**ClientAndService**: ten projekt obsługuje usługę w aplikacji konsoli, a następnie uruchomi klienta do wywołania przez usługę w tej samej domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e4d3e-111">**ClientAndService**: This project hosts a service in a console application and then runs a client to call the service from within the same application domain.</span></span>  
  
 <span data-ttu-id="e4d3e-112">Projekt lokalnego kanału pomija zarówno stosu kanału i przyspieszyć proces serializacji.</span><span class="sxs-lookup"><span data-stu-id="e4d3e-112">The local channel design skips both the channel stack and the serialization process to increase speed.</span></span> <span data-ttu-id="e4d3e-113">Kanał transportu lokalnego jest zaimplementowany przy użyciu kolejki transportu wywołań usługi z klienta do usługi i zwraca wartość z powrotem do klienta.</span><span class="sxs-lookup"><span data-stu-id="e4d3e-113">The local transport channel is implemented using a queue to transport service calls from the client to the service and to return back the value to the client.</span></span> <span data-ttu-id="e4d3e-114">Zamiast serializacji, parametrów i zwracanych wartości, próbki kopiuje obiektów.</span><span class="sxs-lookup"><span data-stu-id="e4d3e-114">Rather than serializing parameters and return values, the sample copies the objects.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e4d3e-115">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="e4d3e-115">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="e4d3e-116">Tworzenie i uruchamianie rozwiązania LocalChannel.</span><span class="sxs-lookup"><span data-stu-id="e4d3e-116">Build and run the LocalChannel solution.</span></span>  
  
2.  <span data-ttu-id="e4d3e-117">Host usługi jest uruchomiona, a klient wywołuje usługę za pomocą lokalnego kanału.</span><span class="sxs-lookup"><span data-stu-id="e4d3e-117">The service host is started and the client calls the service using the local channel.</span></span> <span data-ttu-id="e4d3e-118">Aby wyświetlić wyniki wywołania usługi pojawi się okno konsoli.</span><span class="sxs-lookup"><span data-stu-id="e4d3e-118">A console window appears to display the results of the service call.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e4d3e-119">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="e4d3e-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e4d3e-120">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="e4d3e-120">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e4d3e-121">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="e4d3e-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e4d3e-122">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="e4d3e-122">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\LocalChannel`
