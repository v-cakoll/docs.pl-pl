---
title: "Używanie kontraktów w przepływie pracy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 939c64e9-e7cc-4abc-b41e-27cfce1d7e50
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5c13da32e304e54d1826c6dd4ad83d5fbb17702a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="using-contracts-in-workflow"></a>Używanie kontraktów w przepływie pracy
Podczas wdrażania usługi, należy określić numer kontraktów opisujących usługę i wysyła i odbiera dane. Dane są reprezentowane jako kontraktów danych i kontrakty komunikatu; zarówno [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] i usług przepływu pracy Użyj definicji kontraktu danych kontraktu i komunikatu jako części opisy usług. Sama usługa przedstawia metadanych (w formie WSDL) w celu opisania działania usługi. W [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], usługa kontrakty i kontrakty operacji usługi i operacje, obsługuje on definiować. Jednak w usłudze przepływu pracy, umowy te są częścią procesu biznesowego. są one widoczne w metadanych przez proces, nazywany wnioskowania kontraktu.  
  
## <a name="contract-inference"></a>Kontrakt wnioskowania  
 Gdy usługa przepływu pracy jest obsługiwana przy użyciu <xref:System.ServiceModel.Activities.WorkflowServiceHost>, definicji przepływu pracy się zbadana i kontrakt jest generowany na podstawie zestawu działań w przepływie pracy do obsługi komunikatów. W szczególności następujące działania i właściwości są używane do generowania kontraktu:  
  
 <xref:System.ServiceModel.Activities.Receive>Działanie  
  
-   <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>  
  
-   <xref:System.ServiceModel.Activities.Receive.OperationName%2A>
  
-   <xref:System.ServiceModel.Activities.Receive.Action%2A>   
 
 <xref:System.ServiceModel.Activities.SendReply>Działanie  
  
-   <xref:System.ServiceModel.Activities.SendReply.Action%2A>  
  
 <xref:System.ServiceModel.Activities.TransactedReceiveScope>Działanie  
  
 W rezultacie wnioskowania kontraktu jest opis usługi przy użyciu tych samych struktur danych jako WCF kontraktów usługi i działania. Te informacje jest następnie używane do udostępnienia WSDL usługi przepływu pracy.  
  
## <a name="see-also"></a>Zobacz też  
 [Usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [Działania dotyczące komunikatów](../../../../docs/framework/wcf/feature-details/messaging-activities.md)  
 [Porady: Tworzenie usługi przepływu pracy za pomocą działań dotyczących komunikatów](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)  
 [Porady: Tworzenie usługi przepływu pracy, który wykorzystuje istniejący kontrakt usługi](../../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)
