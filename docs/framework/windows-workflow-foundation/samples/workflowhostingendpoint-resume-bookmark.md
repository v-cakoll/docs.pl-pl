---
title: Wznowienie zakładki WorkflowHostingEndpoint
ms.date: 03/30/2017
ms.assetid: a708064f-50b0-4751-b44e-d5410d08d451
ms.openlocfilehash: 8b435a50801e03ec6ed00bcfef3c7e9198a7e7e5
ms.sourcegitcommit: a368166a51e5204c0224fbf5e46476e3ed122817
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2018
ms.locfileid: "43332164"
---
# <a name="workflowhostingendpoint-resume-bookmark"></a>Wznowienie zakładki WorkflowHostingEndpoint
W tym przykładzie przedstawiono sposób, w jaki <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> mogą być używane z <xref:System.ServiceModel.Activities.WorkflowServiceHost> do utworzenia wystąpienia przepływu pracy.  
  
## <a name="demonstrates"></a>Demonstracje  
 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
## <a name="discussion"></a>Dyskusja  
 W tym przykładzie użyto <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> można utworzyć wystąpienia przepływu pracy, hostowane przy użyciu <xref:System.ServiceModel.Activities.WorkflowServiceHost>. <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> jest punktem rozszerzalności dla <xref:System.ServiceModel.Activities.WorkflowServiceHost> mogą służyć w następujących scenariuszach:  
  
-   Tworzenie nowego wystąpienia przepływu pracy.  
  
-   Wznowienie zakładki w wystąpieniu przepływu pracy hostowane w <xref:System.ServiceModel.Activities.WorkflowServiceHost>.  
  
 Punkt końcowy przykład, który jest dołączony udostępnia kontraktu, który zawiera operacje tworzenia przepływu pracy i zwracają Identyfikatora wystąpienia, aby utworzyć wystąpienie z określonym identyfikatorem. Przykładowa aplikacja konsolowa tworzy <xref:System.ServiceModel.Activities.WorkflowServiceHost> wystąpienia z definicją podstawowy przepływ pracy i dodaje `CreationEndpoint` do hosta. Następnie wywołuje `Create` operacji w punkcie końcowym, aby utworzyć nowe wystąpienie przepływu pracy.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Skompiluj rozwiązanie.  
  
2.  Uruchom aplikację. `CreationEndpoint` Konsoli Pokazuje komunikat, który zawiera identyfikator wystąpienia, gdy tworzone jest wystąpienie przepływu pracy. Komunikat "Hello World!" jest drukowany przez przepływ pracy na pomyślne wznowienie zakładki.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ResumeBookmarkEndpoint`
