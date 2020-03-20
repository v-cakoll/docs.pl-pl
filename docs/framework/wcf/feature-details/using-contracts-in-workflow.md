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
# <a name="using-contracts-in-workflow"></a>Używanie kontraktów w przepływie pracy
Podczas implementowania usługi, można zdefiniować liczbę umów, które opisują usługi i dane, które wysyła i odbiera. Dane są reprezentowane jako kontrakty danych i kontrakty komunikatów; zarówno WCF i usługi przepływu pracy używać umowy danych i umowy wiadomości definicje jako część opisów usług. Sama usługa udostępnia metadane (w postaci WSDL) w celu opisania operacji usługi. W WCF kontrakty serwisowe i umowy na operacje definiują usługę i operacje, które obsługuje. Jednak w usłudze przepływu pracy te umowy są częścią samego procesu biznesowego; są one widoczne w metadanych przez proces o nazwie wnioskowanie umowy.  
  
## <a name="contract-inference"></a>Wnioskowanie o kontrakt  
 Gdy usługa przepływu pracy jest <xref:System.ServiceModel.Activities.WorkflowServiceHost>hostowana przy użyciu, definicja przepływu pracy jest analizowana, a kontrakt jest generowany na podstawie zestawu działań obsługi wiadomości znalezionych w przepływie pracy. W szczególności do wygenerowania kontraktu wykorzystywane są następujące działania i właściwości:  
  
 <xref:System.ServiceModel.Activities.Receive>Działania  
  
- <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>  
  
- <xref:System.ServiceModel.Activities.Receive.OperationName%2A>
  
- <xref:System.ServiceModel.Activities.Receive.Action%2A>

 <xref:System.ServiceModel.Activities.SendReply>Działania  
  
- <xref:System.ServiceModel.Activities.SendReply.Action%2A>  
  
 <xref:System.ServiceModel.Activities.TransactedReceiveScope>Działania  
  
 Wynik końcowy wnioskowania o kontrakt jest opis usługi przy użyciu tych samych struktur danych jako WCF umowy usługi i operacji. Te informacje są następnie używane do udostępnienia WSDL dla usługi przepływu pracy.  
  
## <a name="see-also"></a>Zobacz też

- [Usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Działania dotyczące komunikatów](../../../../docs/framework/wcf/feature-details/messaging-activities.md)
- [Instrukcje: tworzenie przepływu pracy usługi przy użyciu działań dotyczących komunikatów](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)
- [Instrukcje: Tworzenie usługi przepływu pracy wykorzystującej istniejący kontrakt usługi](../../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)
