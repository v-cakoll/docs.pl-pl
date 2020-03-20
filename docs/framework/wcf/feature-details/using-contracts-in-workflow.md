---
title: Używanie kontraktów w przepływie pracy
ms.date: 03/30/2017
ms.assetid: 939c64e9-e7cc-4abc-b41e-27cfce1d7e50
ms.openlocfilehash: 9f967d75a8e9d24fcfac8b7376a3d4840fba52f7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184272"
---
# <a name="using-contracts-in-workflow"></a><span data-ttu-id="f09ba-102">Używanie kontraktów w przepływie pracy</span><span class="sxs-lookup"><span data-stu-id="f09ba-102">Using Contracts in Workflow</span></span>
<span data-ttu-id="f09ba-103">Podczas implementowania usługi, można zdefiniować liczbę umów, które opisują usługi i dane, które wysyła i odbiera.</span><span class="sxs-lookup"><span data-stu-id="f09ba-103">When implementing a service, you define a number of contracts that describe the service and the data that it sends and receives.</span></span> <span data-ttu-id="f09ba-104">Dane są reprezentowane jako kontrakty danych i kontrakty komunikatów; zarówno WCF i usługi przepływu pracy używać umowy danych i umowy wiadomości definicje jako część opisów usług.</span><span class="sxs-lookup"><span data-stu-id="f09ba-104">The data is represented as data contracts and message contracts; both WCF and workflow services use data contract and message contract definitions as part of service descriptions.</span></span> <span data-ttu-id="f09ba-105">Sama usługa udostępnia metadane (w postaci WSDL) w celu opisania operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="f09ba-105">The service itself exposes metadata (in the form of WSDL) in order to describe the operations of the service.</span></span> <span data-ttu-id="f09ba-106">W WCF kontrakty serwisowe i umowy na operacje definiują usługę i operacje, które obsługuje.</span><span class="sxs-lookup"><span data-stu-id="f09ba-106">In WCF, service contracts and operation contracts define the service and the operations it supports.</span></span> <span data-ttu-id="f09ba-107">Jednak w usłudze przepływu pracy te umowy są częścią samego procesu biznesowego; są one widoczne w metadanych przez proces o nazwie wnioskowanie umowy.</span><span class="sxs-lookup"><span data-stu-id="f09ba-107">However, in a workflow service, these contracts are part of the business process itself; they are exposed in metadata by a process called contract inference.</span></span>  
  
## <a name="contract-inference"></a><span data-ttu-id="f09ba-108">Wnioskowanie o kontrakt</span><span class="sxs-lookup"><span data-stu-id="f09ba-108">Contract Inference</span></span>  
 <span data-ttu-id="f09ba-109">Gdy usługa przepływu pracy jest <xref:System.ServiceModel.Activities.WorkflowServiceHost>hostowana przy użyciu, definicja przepływu pracy jest analizowana, a kontrakt jest generowany na podstawie zestawu działań obsługi wiadomości znalezionych w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="f09ba-109">When a workflow service is hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>, the workflow definition is examined and a contract is generated based on the set of messaging activities found in the workflow.</span></span> <span data-ttu-id="f09ba-110">W szczególności do wygenerowania kontraktu wykorzystywane są następujące działania i właściwości:</span><span class="sxs-lookup"><span data-stu-id="f09ba-110">In particular the following activities and properties are used to generate the contract:</span></span>  
  
 <span data-ttu-id="f09ba-111"><xref:System.ServiceModel.Activities.Receive>Działania</span><span class="sxs-lookup"><span data-stu-id="f09ba-111"><xref:System.ServiceModel.Activities.Receive> Activity</span></span>  
  
- <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>  
  
- <xref:System.ServiceModel.Activities.Receive.OperationName%2A>
  
- <xref:System.ServiceModel.Activities.Receive.Action%2A>

 <span data-ttu-id="f09ba-112"><xref:System.ServiceModel.Activities.SendReply>Działania</span><span class="sxs-lookup"><span data-stu-id="f09ba-112"><xref:System.ServiceModel.Activities.SendReply> Activity</span></span>  
  
- <xref:System.ServiceModel.Activities.SendReply.Action%2A>  
  
 <span data-ttu-id="f09ba-113"><xref:System.ServiceModel.Activities.TransactedReceiveScope>Działania</span><span class="sxs-lookup"><span data-stu-id="f09ba-113"><xref:System.ServiceModel.Activities.TransactedReceiveScope> Activity</span></span>  
  
 <span data-ttu-id="f09ba-114">Wynik końcowy wnioskowania o kontrakt jest opis usługi przy użyciu tych samych struktur danych jako WCF umowy usługi i operacji.</span><span class="sxs-lookup"><span data-stu-id="f09ba-114">The end result of contract inference is a description of the service using the same data structures as WCF service and operation contracts.</span></span> <span data-ttu-id="f09ba-115">Te informacje są następnie używane do udostępnienia WSDL dla usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="f09ba-115">This information is then used to expose WSDL for the workflow service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f09ba-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f09ba-116">See also</span></span>

- [<span data-ttu-id="f09ba-117">Usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="f09ba-117">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [<span data-ttu-id="f09ba-118">Działania dotyczące komunikatów</span><span class="sxs-lookup"><span data-stu-id="f09ba-118">Messaging Activities</span></span>](../../../../docs/framework/wcf/feature-details/messaging-activities.md)
- [<span data-ttu-id="f09ba-119">Instrukcje: tworzenie przepływu pracy usługi przy użyciu działań dotyczących komunikatów</span><span class="sxs-lookup"><span data-stu-id="f09ba-119">How to: Create a Workflow Service with Messaging Activities</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)
- [<span data-ttu-id="f09ba-120">Instrukcje: Tworzenie usługi przepływu pracy wykorzystującej istniejący kontrakt usługi</span><span class="sxs-lookup"><span data-stu-id="f09ba-120">How to: Create a workflow service that consumes an existing service contract</span></span>](../../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)
