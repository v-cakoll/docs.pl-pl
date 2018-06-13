---
title: Używanie kontraktów w przepływie pracy
ms.date: 03/30/2017
ms.assetid: 939c64e9-e7cc-4abc-b41e-27cfce1d7e50
ms.openlocfilehash: 1772c61147bb8a96f3f78b4226a1d341df3eb9d9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33498306"
---
# <a name="using-contracts-in-workflow"></a>Używanie kontraktów w przepływie pracy
Podczas wdrażania usługi, należy określić numer kontraktów opisujących usługę i wysyła i odbiera dane. Dane są reprezentowane jako kontraktów danych i kontrakty komunikatu; usługi WCF, zarówno i przepływu pracy Użyj definicje kontraktu danych kontraktu i wiadomości jako części opisy usług. Sama usługa przedstawia metadanych (w formie WSDL) w celu opisania działania usługi. W programie WCF kontraktów usług i kontrakty operacji definiują usługi i operacje, które obsługuje. Jednak w usłudze przepływu pracy, umowy te są częścią procesu biznesowego. są one widoczne w metadanych przez proces, nazywany wnioskowania kontraktu.  
  
## <a name="contract-inference"></a>Kontrakt wnioskowania  
 Gdy usługa przepływu pracy jest obsługiwana przy użyciu <xref:System.ServiceModel.Activities.WorkflowServiceHost>, definicji przepływu pracy się zbadana i kontrakt jest generowany na podstawie zestawu działań w przepływie pracy do obsługi komunikatów. W szczególności następujące działania i właściwości są używane do generowania kontraktu:  
  
 <xref:System.ServiceModel.Activities.Receive> Działanie  
  
-   <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>  
  
-   <xref:System.ServiceModel.Activities.Receive.OperationName%2A>
  
-   <xref:System.ServiceModel.Activities.Receive.Action%2A>   
 
 <xref:System.ServiceModel.Activities.SendReply> Działanie  
  
-   <xref:System.ServiceModel.Activities.SendReply.Action%2A>  
  
 <xref:System.ServiceModel.Activities.TransactedReceiveScope> Działanie  
  
 W rezultacie wnioskowania kontraktu jest opis usługi przy użyciu tych samych struktur danych jako WCF kontraktów usługi i działania. Te informacje jest następnie używane do udostępnienia WSDL usługi przepływu pracy.  
  
## <a name="see-also"></a>Zobacz też  
 [Usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [Działania dotyczące komunikatów](../../../../docs/framework/wcf/feature-details/messaging-activities.md)  
 [Instrukcje: tworzenie przepływu pracy usługi przy użyciu działań dotyczących komunikatów](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)  
 [Instrukcje: Tworzenie usługi przepływu pracy wykorzystującej istniejący kontrakt usługi](../../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)
