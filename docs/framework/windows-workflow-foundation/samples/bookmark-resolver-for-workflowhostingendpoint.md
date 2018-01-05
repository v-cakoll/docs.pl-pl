---
title: "Mechanizm rozpoznawania zakładki dla WorkflowHostingEndpoint"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 97fd5816-935e-4625-ad04-e6f6befa07de
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 596aac72572853f65608b21f89077a993c0c0d73
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="bookmark-resolver-for-workflowhostingendpoint"></a>Mechanizm rozpoznawania zakładki dla WorkflowHostingEndpoint
W przykładzie pokazano, jak <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> mogą być używane z <xref:System.ServiceModel.Activities.WorkflowServiceHost> można utworzyć wystąpienia przepływu pracy.  
  
## <a name="demonstrates"></a>Demonstracje  
 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
## <a name="discussion"></a>Omówienie  
 W przykładzie użyto <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> można utworzyć wystąpienia przepływu pracy hostowane przy użyciu <xref:System.ServiceModel.Activities.WorkflowServiceHost>. <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>punkt rozszerzalności dla <xref:System.ServiceModel.Activities.WorkflowServiceHost> które mogą być używane w następujących scenariuszach:  
  
-   Tworzenie nowego wystąpienia przepływu pracy.  
  
-   Wznawianie zakładki w wystąpieniu przepływu pracy hostowanych w <xref:System.ServiceModel.Activities.WorkflowServiceHost>.  
  
 Punkt końcowy próbki, który znajduje się przedstawia kontraktu, który udostępnia operacje w celu utworzenia przepływu pracy i zwraca identyfikator wystąpienia lub tworzy wystąpienie z określonym identyfikatorem. Przykładowa aplikacja konsolowa tworzy <xref:System.ServiceModel.Activities.WorkflowServiceHost> wystąpienia z definicją przepływu pracy i dodaje `CreationEndpoint` do hosta. Następnie wywołuje `Create` operacji na punkt końcowy do utworzenia nowego wystąpienia przepływu pracy.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Skompiluj rozwiązanie.  
  
2.  Uruchom aplikację. `CreationEndpoint` Konsoli Pokazuje komunikat, który zawiera identyfikator wystąpienia, gdy jest tworzone wystąpienie przepływu pracy. Komunikat "Hello World!" wydrukowaniu wystąpienia przepływu pracy.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreationEndpoint`
