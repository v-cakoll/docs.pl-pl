---
title: Używanie kontraktów w przepływie pracy
ms.date: 03/30/2017
ms.assetid: 939c64e9-e7cc-4abc-b41e-27cfce1d7e50
ms.openlocfilehash: dd35766011c412acc937eed75d523a0574f6b9cb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59150062"
---
# <a name="using-contracts-in-workflow"></a><span data-ttu-id="5ee4e-102">Używanie kontraktów w przepływie pracy</span><span class="sxs-lookup"><span data-stu-id="5ee4e-102">Using Contracts in Workflow</span></span>
<span data-ttu-id="5ee4e-103">Podczas wdrażania usługi, należy zdefiniować liczbę zamówień, które opisują usługi i dane, które wysyła i odbiera.</span><span class="sxs-lookup"><span data-stu-id="5ee4e-103">When implementing a service, you define a number of contracts that describe the service and the data that it sends and receives.</span></span> <span data-ttu-id="5ee4e-104">Dane są reprezentowane jako kontraktów danych i kontrakty komunikatów; usługi WCF i przepływu pracy Użyj definicje kontraktu danych kontraktu i komunikat jako część opisy usług.</span><span class="sxs-lookup"><span data-stu-id="5ee4e-104">The data is represented as data contracts and message contracts; both WCF and workflow services use data contract and message contract definitions as part of service descriptions.</span></span> <span data-ttu-id="5ee4e-105">Sama usługa udostępnia metadane (w formie WSDL), w celu opisania działania usługi.</span><span class="sxs-lookup"><span data-stu-id="5ee4e-105">The service itself exposes metadata (in the form of WSDL) in order to describe the operations of the service.</span></span> <span data-ttu-id="5ee4e-106">W programie WCF kontraktów usług i kontrakty operacji definiują usługi i operacje, które obsługuje.</span><span class="sxs-lookup"><span data-stu-id="5ee4e-106">In WCF, service contracts and operation contracts define the service and the operations it supports.</span></span> <span data-ttu-id="5ee4e-107">Jednak w usłudze przepływu pracy, umowy te są częścią procesu biznesowego. są one widoczne w metadanych w procesie nazywanym wnioskowania kontraktu.</span><span class="sxs-lookup"><span data-stu-id="5ee4e-107">However, in a workflow service, these contracts are part of the business process itself; they are exposed in metadata by a process called contract inference.</span></span>  
  
## <a name="contract-inference"></a><span data-ttu-id="5ee4e-108">Wnioskowanie kontraktu</span><span class="sxs-lookup"><span data-stu-id="5ee4e-108">Contract Inference</span></span>  
 <span data-ttu-id="5ee4e-109">Gdy usługi przepływu pracy znajduje się za pomocą <xref:System.ServiceModel.Activities.WorkflowServiceHost>definicji przepływu pracy jest badany i kontrakt jest generowany na podstawie zestawu działań w przepływie pracy do obsługi komunikatów.</span><span class="sxs-lookup"><span data-stu-id="5ee4e-109">When a workflow service is hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>, the workflow definition is examined and a contract is generated based on the set of messaging activities found in the workflow.</span></span> <span data-ttu-id="5ee4e-110">W szczególności następujące działania i właściwości są używane do generowania umowy:</span><span class="sxs-lookup"><span data-stu-id="5ee4e-110">In particular the following activities and properties are used to generate the contract:</span></span>  
  
 <xref:System.ServiceModel.Activities.Receive> <span data-ttu-id="5ee4e-111">Działanie</span><span class="sxs-lookup"><span data-stu-id="5ee4e-111">Activity</span></span>  
  
-   <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>  
  
-   <xref:System.ServiceModel.Activities.Receive.OperationName%2A>
  
-   <xref:System.ServiceModel.Activities.Receive.Action%2A>   
 
 <xref:System.ServiceModel.Activities.SendReply> <span data-ttu-id="5ee4e-112">Działanie</span><span class="sxs-lookup"><span data-stu-id="5ee4e-112">Activity</span></span>  
  
-   <xref:System.ServiceModel.Activities.SendReply.Action%2A>  
  
 <xref:System.ServiceModel.Activities.TransactedReceiveScope> <span data-ttu-id="5ee4e-113">Działanie</span><span class="sxs-lookup"><span data-stu-id="5ee4e-113">Activity</span></span>  
  
 <span data-ttu-id="5ee4e-114">Wynik końcowy wnioskowania kontraktu jest opis usługi przy użyciu tych samych struktur danych jako kontraktów usługi i operacji usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="5ee4e-114">The end result of contract inference is a description of the service using the same data structures as WCF service and operation contracts.</span></span> <span data-ttu-id="5ee4e-115">Te informacje jest następnie używane do udostępnienia WSDL usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="5ee4e-115">This information is then used to expose WSDL for the workflow service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ee4e-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5ee4e-116">See also</span></span>

- [<span data-ttu-id="5ee4e-117">Usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="5ee4e-117">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [<span data-ttu-id="5ee4e-118">Działania dotyczące komunikatów</span><span class="sxs-lookup"><span data-stu-id="5ee4e-118">Messaging Activities</span></span>](../../../../docs/framework/wcf/feature-details/messaging-activities.md)
- [<span data-ttu-id="5ee4e-119">Instrukcje: Tworzenie usługi przepływu pracy przy użyciu działań dotyczących komunikatów</span><span class="sxs-lookup"><span data-stu-id="5ee4e-119">How to: Create a Workflow Service with Messaging Activities</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)
- [<span data-ttu-id="5ee4e-120">Instrukcje: Tworzenie usługi przepływu pracy wykorzystującej istniejący kontrakt usługi</span><span class="sxs-lookup"><span data-stu-id="5ee4e-120">How to: Create a workflow service that consumes an existing service contract</span></span>](../../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)
