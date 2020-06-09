---
title: Usługi przepływu pracy
ms.date: 03/30/2017
ms.assetid: 7b05c766-f181-425d-9a3d-2a5e150c85f7
ms.openlocfilehash: c7a5c6245702497fcd75341b3ff7ba08dc190fa5
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600130"
---
# <a name="workflow-services"></a><span data-ttu-id="ea409-102">Usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="ea409-102">Workflow Services</span></span>
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]<span data-ttu-id="ea409-103">umożliwia pełne Opisanie usługi opartej na przepływie pracy w języku XAML.</span><span class="sxs-lookup"><span data-stu-id="ea409-103">allows you to fully describe a workflow-based service declaratively in XAML.</span></span> <span data-ttu-id="ea409-104">Można zdefiniować przepływ pracy, który implementuje usługę i opisywać punkty końcowe, które udostępnia usługa, całkowicie w języku XAML.</span><span class="sxs-lookup"><span data-stu-id="ea409-104">You can define a workflow that implements your service and describe endpoints the service exposes, all entirely in XAML.</span></span> <span data-ttu-id="ea409-105">W tematach w tej sekcji opisano szczegółowo model programowania obsługujący pisanie usług.</span><span class="sxs-lookup"><span data-stu-id="ea409-105">The topics in this section describe, in detail, the programming model that supports writing services declaratively.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ea409-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="ea409-106">In This Section</span></span>  
 [<span data-ttu-id="ea409-107">Przegląd usług przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="ea409-107">Workflow Services Overview</span></span>](workflow-services-overview.md)  
 <span data-ttu-id="ea409-108">Opisuje składniki wykorzystywane podczas tworzenia i hostowania usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="ea409-108">Describes the components involved in creating and hosting a workflow service.</span></span>  
  
 [<span data-ttu-id="ea409-109">Działania dotyczące komunikatów</span><span class="sxs-lookup"><span data-stu-id="ea409-109">Messaging Activities</span></span>](messaging-activities.md)  
 <span data-ttu-id="ea409-110">W tym artykule omówiono działania umożliwiające wysyłanie i odbieranie komunikatów przez przepływy pracy.</span><span class="sxs-lookup"><span data-stu-id="ea409-110">Discusses activities that allow workflows to send and receive messages.</span></span>  
  
 [<span data-ttu-id="ea409-111">Instrukcje: tworzenie przepływu pracy usługi przy użyciu działań dotyczących komunikatów</span><span class="sxs-lookup"><span data-stu-id="ea409-111">How to: Create a Workflow Service with Messaging Activities</span></span>](how-to-create-a-workflow-service-with-messaging-activities.md)  
 <span data-ttu-id="ea409-112">Opisuje sposób korzystania z działań związanych z obsługą komunikatów w celu utworzenia usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="ea409-112">Describes how to use messaging activities to create a workflow service.</span></span>  
  
 [<span data-ttu-id="ea409-113">Instrukcje: uzyskiwanie dostępu do usługi z poziomu aplikacji przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="ea409-113">How To: Access a Service From a Workflow Application</span></span>](how-to-access-a-service-from-a-workflow-application.md)  
 <span data-ttu-id="ea409-114">W tym artykule omówiono sposób wywoływania usługi z poziomu aplikacji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="ea409-114">Discusses how to call a service from a workflow application.</span></span>  
  
 [<span data-ttu-id="ea409-115">Korelacja</span><span class="sxs-lookup"><span data-stu-id="ea409-115">Correlation</span></span>](correlation.md)  
 <span data-ttu-id="ea409-116">W tym artykule omówiono sposób mapowania przez korelacji komunikatów między sobą i wystąpieniami.</span><span class="sxs-lookup"><span data-stu-id="ea409-116">Discusses how correlation maps messages to each other and to instances.</span></span>  
  
 [<span data-ttu-id="ea409-117">Przetwarzanie komunikatów poza kolejnością</span><span class="sxs-lookup"><span data-stu-id="ea409-117">Out-of-Order Message Processing</span></span>](out-of-order-message-processing.md)  
 <span data-ttu-id="ea409-118">Opisuje Konfigurowanie usługi do akceptowania komunikatów poza kolejnością.</span><span class="sxs-lookup"><span data-stu-id="ea409-118">Describes configuring a service to accept out of order messages.</span></span>  
  
 [<span data-ttu-id="ea409-119">Programowanie usługi przepływu pracy narzędzia Contract-First</span><span class="sxs-lookup"><span data-stu-id="ea409-119">Contract First Workflow Service Development</span></span>](../../windows-workflow-foundation/contract-first-workflow-service-development.md)  
 <span data-ttu-id="ea409-120">Opisuje tworzenie usługi przepływu pracy na podstawie istniejącego kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="ea409-120">Describes creating a workflow service based on an existing service contract.</span></span>  
  
 [<span data-ttu-id="ea409-121">Instrukcje: Tworzenie usługi przepływu pracy wykorzystującej istniejący kontrakt usługi</span><span class="sxs-lookup"><span data-stu-id="ea409-121">How to: Create a workflow service that consumes an existing service contract</span></span>](../../windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)  
 <span data-ttu-id="ea409-122">Zawiera przykładowy krok po kroku tworzenia usługi przepływu pracy przy użyciu istniejącego kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="ea409-122">Provides a step-by-step example of creating a workflow service using an existing service contract.</span></span>  
  
 [<span data-ttu-id="ea409-123">Przegląd hostowania usług przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="ea409-123">Hosting Workflow Services Overview</span></span>](hosting-workflow-services-overview.md)  
 <span data-ttu-id="ea409-124">Opisuje różne aspekty hostingu usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="ea409-124">Describes the different aspects of hosting a workflow service.</span></span>  
  
 [<span data-ttu-id="ea409-125">Używanie kontraktów w przepływie pracy</span><span class="sxs-lookup"><span data-stu-id="ea409-125">Using Contracts in Workflow</span></span>](using-contracts-in-workflow.md)  
 <span data-ttu-id="ea409-126">Opisuje różne typy kontraktów i wnioskowania o umowę.</span><span class="sxs-lookup"><span data-stu-id="ea409-126">Describes the different types of contracts and contract inference.</span></span>
