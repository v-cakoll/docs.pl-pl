---
title: "Usługi przepływu pracy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7b05c766-f181-425d-9a3d-2a5e150c85f7
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 043aa541e32077faf8141701a5ec7e8c0e711959
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="workflow-services"></a><span data-ttu-id="9ff1b-102">Usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="9ff1b-102">Workflow Services</span></span>
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]<span data-ttu-id="9ff1b-103">Umożliwia pełne opisanie usługi przepływu pracy na podstawie deklaratywnego w języku XAML.</span><span class="sxs-lookup"><span data-stu-id="9ff1b-103"> allows you to fully describe a workflow-based service declaratively in XAML.</span></span> <span data-ttu-id="9ff1b-104">Można zdefiniować przepływu pracy, który implementuje usługi i opisz punkty końcowe udostępnia usługi, wszystkie wyłącznie w języku XAML.</span><span class="sxs-lookup"><span data-stu-id="9ff1b-104">You can define a workflow that implements your service and describe endpoints the service exposes, all entirely in XAML.</span></span> <span data-ttu-id="9ff1b-105">Tematy w tej sekcji opisano szczegółowo, model programowania, który obsługuje usługi zapisu deklaratywnie.</span><span class="sxs-lookup"><span data-stu-id="9ff1b-105">The topics in this section describe, in detail, the programming model that supports writing services declaratively.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9ff1b-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="9ff1b-106">In This Section</span></span>  
 [<span data-ttu-id="9ff1b-107">Przegląd usług przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="9ff1b-107">Workflow Services Overview</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services-overview.md)  
 <span data-ttu-id="9ff1b-108">W tym artykule opisano składniki zaangażowane w tworzenie i obsługa usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="9ff1b-108">Describes the components involved in creating and hosting a workflow service.</span></span>  
  
 [<span data-ttu-id="9ff1b-109">Działania dotyczące komunikatów</span><span class="sxs-lookup"><span data-stu-id="9ff1b-109">Messaging Activities</span></span>](../../../../docs/framework/wcf/feature-details/messaging-activities.md)  
 <span data-ttu-id="9ff1b-110">W tym artykule omówiono działań, które umożliwiają przepływy pracy w celu wysyłania i odbierania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="9ff1b-110">Discusses activities that allow workflows to send and receive messages.</span></span>  
  
 [<span data-ttu-id="9ff1b-111">Porady: Tworzenie usługi przepływu pracy za pomocą działań dotyczących komunikatów</span><span class="sxs-lookup"><span data-stu-id="9ff1b-111">How to: Create a Workflow Service with Messaging Activities</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)  
 <span data-ttu-id="9ff1b-112">Informacje dotyczące używania działań obsługi komunikatów do tworzenia usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="9ff1b-112">Describes how to use messaging activities to create a workflow service.</span></span>  
  
 [<span data-ttu-id="9ff1b-113">Porady: Dostęp do usługi z poziomu aplikacji przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="9ff1b-113">How To: Access a Service From a Workflow Application</span></span>](../../../../docs/framework/wcf/feature-details/how-to-access-a-service-from-a-workflow-application.md)  
 <span data-ttu-id="9ff1b-114">W tym artykule omówiono sposób wywoływania usługi z poziomu aplikacji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="9ff1b-114">Discusses how to call a service from a workflow application.</span></span>  
  
 [<span data-ttu-id="9ff1b-115">Korelacji</span><span class="sxs-lookup"><span data-stu-id="9ff1b-115">Correlation</span></span>](../../../../docs/framework/wcf/feature-details/correlation.md)  
 <span data-ttu-id="9ff1b-116">W tym artykule omówiono sposób korelacji mapy wiadomości i wystąpień.</span><span class="sxs-lookup"><span data-stu-id="9ff1b-116">Discusses how correlation maps messages to each other and to instances.</span></span>  
  
 [<span data-ttu-id="9ff1b-117">Przetwarzanie komunikatów poza kolejnością.</span><span class="sxs-lookup"><span data-stu-id="9ff1b-117">Out-of-Order Message Processing</span></span>](../../../../docs/framework/wcf/feature-details/out-of-order-message-processing.md)  
 <span data-ttu-id="9ff1b-118">W tym artykule opisano konfigurowanie usługi ma akceptować komunikaty poza kolejnością.</span><span class="sxs-lookup"><span data-stu-id="9ff1b-118">Describes configuring a service to accept out of order messages.</span></span>  
  
 [<span data-ttu-id="9ff1b-119">Porady: Tworzenie usługi przepływu pracy wywołującej inną usługę przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="9ff1b-119">How to: Create a Workflow Service That Calls Another Workflow Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-that-calls-another-workflow-service.md)  
 <span data-ttu-id="9ff1b-120">Opisuje sposób synchronicznego wywoływania usługi przepływu pracy z innej usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="9ff1b-120">Describes how to synchronously call a workflow service from within another workflow service.</span></span>  
  
 [<span data-ttu-id="9ff1b-121">Kontrakt pierwszy programowanie usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="9ff1b-121">Contract First Workflow Service Development</span></span>](../../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md)  
 <span data-ttu-id="9ff1b-122">W tym artykule opisano tworzenie usługi przepływu pracy oparte na istniejący kontrakt usługi.</span><span class="sxs-lookup"><span data-stu-id="9ff1b-122">Describes creating a workflow service based on an existing service contract.</span></span>  
  
 [<span data-ttu-id="9ff1b-123">Porady: Tworzenie usługi przepływu pracy, który wykorzystuje istniejący kontrakt usługi</span><span class="sxs-lookup"><span data-stu-id="9ff1b-123">How to: Create a workflow service that consumes an existing service contract</span></span>](../../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)  
 <span data-ttu-id="9ff1b-124">Zawiera krok przykładem tworzenia usługi przepływu pracy przy użyciu istniejący kontrakt usługi.</span><span class="sxs-lookup"><span data-stu-id="9ff1b-124">Provides a step-by-step example of creating a workflow service using an existing service contract.</span></span>  
  
 [<span data-ttu-id="9ff1b-125">Przegląd hostowania usług przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="9ff1b-125">Hosting Workflow Services Overview</span></span>](../../../../docs/framework/wcf/feature-details/hosting-workflow-services-overview.md)  
 <span data-ttu-id="9ff1b-126">Zawiera opis różnych aspektów hosting usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="9ff1b-126">Describes the different aspects of hosting a workflow service.</span></span>  
  
 [<span data-ttu-id="9ff1b-127">Używanie kontraktów w przepływie pracy</span><span class="sxs-lookup"><span data-stu-id="9ff1b-127">Using Contracts in Workflow</span></span>](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md)  
 <span data-ttu-id="9ff1b-128">Opisano różne typy umów i wnioskowania kontraktu.</span><span class="sxs-lookup"><span data-stu-id="9ff1b-128">Describes the different types of contracts and contract inference.</span></span>
