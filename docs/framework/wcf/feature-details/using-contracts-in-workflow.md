---
title: Używanie kontraktów w przepływie pracy
ms.date: 03/30/2017
ms.assetid: 939c64e9-e7cc-4abc-b41e-27cfce1d7e50
ms.openlocfilehash: 5fd18e1a180aa390f8f0ce7ca414921723399eb0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54565604"
---
# <a name="using-contracts-in-workflow"></a>Używanie kontraktów w przepływie pracy
Podczas wdrażania usługi, należy zdefiniować liczbę zamówień, które opisują usługi i dane, które wysyła i odbiera. Dane są reprezentowane jako kontraktów danych i kontrakty komunikatów; usługi WCF i przepływu pracy Użyj definicje kontraktu danych kontraktu i komunikat jako część opisy usług. Sama usługa udostępnia metadane (w formie WSDL), w celu opisania działania usługi. W programie WCF kontraktów usług i kontrakty operacji definiują usługi i operacje, które obsługuje. Jednak w usłudze przepływu pracy, umowy te są częścią procesu biznesowego. są one widoczne w metadanych w procesie nazywanym wnioskowania kontraktu.  
  
## <a name="contract-inference"></a>Wnioskowanie kontraktu  
 Gdy usługi przepływu pracy znajduje się za pomocą <xref:System.ServiceModel.Activities.WorkflowServiceHost>definicji przepływu pracy jest badany i kontrakt jest generowany na podstawie zestawu działań w przepływie pracy do obsługi komunikatów. W szczególności następujące działania i właściwości są używane do generowania umowy:  
  
 <xref:System.ServiceModel.Activities.Receive> Działanie  
  
-   <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>  
  
-   <xref:System.ServiceModel.Activities.Receive.OperationName%2A>
  
-   <xref:System.ServiceModel.Activities.Receive.Action%2A>   
 
 <xref:System.ServiceModel.Activities.SendReply> Działanie  
  
-   <xref:System.ServiceModel.Activities.SendReply.Action%2A>  
  
 <xref:System.ServiceModel.Activities.TransactedReceiveScope> Działanie  
  
 Wynik końcowy wnioskowania kontraktu jest opis usługi przy użyciu tych samych struktur danych jako kontraktów usługi i operacji usługi WCF. Te informacje jest następnie używane do udostępnienia WSDL usługi przepływu pracy.  
  
## <a name="see-also"></a>Zobacz także
- [Usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Działania dotyczące komunikatów](../../../../docs/framework/wcf/feature-details/messaging-activities.md)
- [Instrukcje: Tworzenie usługi przepływu pracy przy użyciu działań dotyczących komunikatów](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)
- [Instrukcje: Tworzenie usługi przepływu pracy, który wykorzystuje istniejący kontrakt usługi](../../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)
