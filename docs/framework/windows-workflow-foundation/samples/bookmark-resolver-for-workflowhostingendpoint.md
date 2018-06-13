---
title: Mechanizm rozpoznawania zakładki dla WorkflowHostingEndpoint
ms.date: 03/30/2017
ms.assetid: 97fd5816-935e-4625-ad04-e6f6befa07de
ms.openlocfilehash: f8afb804525ecf36127e32441c92f43af70f5099
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33514947"
---
# <a name="bookmark-resolver-for-workflowhostingendpoint"></a>Mechanizm rozpoznawania zakładki dla WorkflowHostingEndpoint
W przykładzie pokazano, jak <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> mogą być używane z <xref:System.ServiceModel.Activities.WorkflowServiceHost> można utworzyć wystąpienia przepływu pracy.  
  
## <a name="demonstrates"></a>Demonstracje  
 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
## <a name="discussion"></a>Omówienie  
 W przykładzie użyto <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> można utworzyć wystąpienia przepływu pracy hostowane przy użyciu <xref:System.ServiceModel.Activities.WorkflowServiceHost>. <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> punkt rozszerzalności dla <xref:System.ServiceModel.Activities.WorkflowServiceHost> które mogą być używane w następujących scenariuszach:  
  
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
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreationEndpoint`
