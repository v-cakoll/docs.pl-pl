---
title: Używanie kontraktów w przepływie pracy
ms.date: 03/30/2017
ms.assetid: 939c64e9-e7cc-4abc-b41e-27cfce1d7e50
ms.openlocfilehash: def100f9483ea9ac8bf1aa3285d76edccffb030a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595014"
---
# <a name="using-contracts-in-workflow"></a>Używanie kontraktów w przepływie pracy
Podczas implementowania usługi należy zdefiniować kilka kontraktów, które opisują usługę i dane wysyłane i odbierane. Dane są reprezentowane jako Kontrakty danych i umowy dotyczące komunikatów; usługi WCF i Workflow Services korzystają z kontraktów danych i definicji kontraktu komunikatów w ramach opisów usług. Sama usługa ujawnia metadane (w formie WSDL) w celu opisania operacji usługi. W programie WCF kontrakty usług i kontrakty operacji definiują usługę i obsługiwane przez nią operacje. Jednak w usłudze przepływu pracy te kontrakty są częścią procesu biznesowego. są one ujawniane w metadanych przez proces o nazwie wnioskowanie kontraktu.  
  
## <a name="contract-inference"></a>Wnioskowanie o kontrakcie  
 Gdy usługa przepływu pracy jest hostowana przy użyciu <xref:System.ServiceModel.Activities.WorkflowServiceHost> , sprawdzana jest definicja przepływu pracy i jest generowana umowa oparta na zestawie działań obsługi komunikatów znalezionych w przepływie pracy. W szczególności następujące działania i właściwości są używane do generowania kontraktu:  
  
 <xref:System.ServiceModel.Activities.Receive>Interakcyjn  
  
- <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>  
  
- <xref:System.ServiceModel.Activities.Receive.OperationName%2A>
  
- <xref:System.ServiceModel.Activities.Receive.Action%2A>

 <xref:System.ServiceModel.Activities.SendReply>Interakcyjn  
  
- <xref:System.ServiceModel.Activities.SendReply.Action%2A>  
  
 <xref:System.ServiceModel.Activities.TransactedReceiveScope>Interakcyjn  
  
 Końcowy wynik wnioskowania o umowę to opis usługi przy użyciu tych samych struktur danych co usługa WCF i kontrakty operacji. Te informacje są następnie używane w celu udostępnienia WSDL dla usługi przepływu pracy.  
  
## <a name="see-also"></a>Zobacz też

- [Usługi przepływu pracy](workflow-services.md)
- [Działania dotyczące komunikatów](messaging-activities.md)
- [Instrukcje: tworzenie przepływu pracy usługi przy użyciu działań dotyczących komunikatów](how-to-create-a-workflow-service-with-messaging-activities.md)
- [Instrukcje: Tworzenie usługi przepływu pracy wykorzystującej istniejący kontrakt usługi](../../windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)
