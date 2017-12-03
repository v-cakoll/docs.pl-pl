---
title: "Zabezpieczenia przepływu pracy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: programming [WF], workflow security
ms.assetid: d712a566-f435-44c0-b8c0-49298e84b114
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 47d06950f8aa9b85420d873adcc4b1acb89a5219
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="workflow-security"></a>Zabezpieczenia przepływu pracy
[!INCLUDE[wf](../../../includes/wf-md.md)]jest zintegrowany z wielu różnych technologii, takich jak Microsoft SQL Server i [!INCLUDE[indigo1](../../../includes/indigo1-md.md)]. Interakcja z tych technologii może powodować problemy z zabezpieczeniami z przepływem pracy, jeśli wykonane nieprawidłowo.  
  
## <a name="persistence-security-concerns"></a>Problemy z zabezpieczeniami trwałości  
  
1.  Przepływy pracy używające <xref:System.Activities.Statements.Delay> działania i trwałości konieczności ponownej aktywacji przez usługę. Windows AppFabric używa usługi zarządzania przepływu pracy (WMS) z wygasłych czasomierze ponownego uaktywnienia przepływów pracy. Tworzy WMS <xref:System.ServiceModel.WorkflowServiceHost> do hostowania uaktywnionym ponownie przepływ pracy. Po zatrzymaniu usługi WMS do obsługi utrwalonych przepływów pracy będzie nie będzie ponownie aktywować po upływie limitu czasu ich czasomierze.  
  
2.  Dostęp do wystąpień trwałe powinny być chronione przed złośliwym podmiotom spoza domeny aplikacji. Ponadto deweloperzy powinien upewnij się, że złośliwy kod nie można wykonać w tej samej domenie aplikacji jako trwałe kod wystąpień.  
  
3.  Tworzenie wystąpienia trwałe nie powinien być uruchamiany z podwyższonym poziomem uprawnień (Administrator).  
  
4.  Dane są przetwarzane spoza domeny aplikacji powinny być chronione.  
  
5.  Aplikacje wymagające zabezpieczeń izolacji nie powinny współużytkować to samo wystąpienie elementu abstrakcji schematu. Takich aplikacji należy użyć magazynu różnych dostawców, lub przechowywać dostawców skonfigurowana do używania magazynu różnych wystąpień.  
  
## <a name="sql-server-security-concerns"></a>Zagadnienia dotyczące zabezpieczeń programu SQL Server  
  
-   Jeśli dużej liczby działań podrzędnych, lokalizacji, zakładki, rozszerzenia hosta lub zakresy są używane, lub zakładki z bardzo dużych ładunki są używane, pamięci można wyczerpane lub nadmiernej ilości miejsca w bazie danych, którą można przydzielić podczas utrwalania. Można to zminimalizować przy użyciu zabezpieczeń na poziomie bazy danych i na poziomie obiektu.  
  
-   Korzystając z <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, muszą być zabezpieczone w magazynie wystąpień. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Programu SQL Server najlepsze rozwiązania](http://go.microsoft.com/fwlink/?LinkId=164972).  
  
-   Powinny być szyfrowane poufnych danych w magazynie wystąpień. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Szyfrowania zabezpieczeń SQL](http://go.microsoft.com/fwlink/?LinkId=164976).  
  
-   Ponieważ często zawiera parametry połączenia bazy danych w pliku konfiguracji, zabezpieczenia na poziomie systemu windows (ACL) powinien być używany do zapewnienia, że plik konfiguracyjny (zwykle w pliku Web.Config) jest bezpieczne i informacje logowania i hasła nie są uwzględnione w Parametry połączenia. Uwierzytelnianie systemu Windows należy użyć między bazy danych i serwera sieci web.  
  
## <a name="considerations-for-workflowservicehost"></a>Zagadnienia dotyczące obiektu WorkflowServiceHost  
  
-   [!INCLUDE[indigo1](../../../includes/indigo1-md.md)]punkty końcowe używane w przepływach pracy powinny być chronione. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Omówienie zabezpieczeń usługi WCF](http://go.microsoft.com/fwlink/?LinkID=164975).  
  
-   Zezwolenie na poziomie hosta można zaimplementować przy użyciu <xref:System.ServiceModel.ServiceAuthorizationManager>. Zobacz [jak: tworzenie Menedżera autoryzacji niestandardowej dla usługi](http://go.microsoft.com/fwlink/?LinkId=192228) szczegółowe informacje. Jest to również przedstawiono w poniższym przykładzie: [zabezpieczania usług przepływu pracy](../../../docs/framework/windows-workflow-foundation/samples/securing-workflow-services.md).  
  
-   ServiceSecurityContext wiadomości przychodzącej jest również dostępna z poziomu przepływu pracy po zalogowaniu się do elementu OperationContext.  Zobacz [podczas uzyskiwania dostępu do elementu OperationContext z usługi przepływu pracy](../../../docs/framework/wcf/feature-details/accessing-operationcontext-from-a-workflow-service.md) szczegółowe informacje.  
  
## <a name="wf-security-pack-ctp"></a>Pakiet zabezpieczeń WF CTP  
 Microsoft WF zabezpieczeń pakietu CTP 1 jest pierwszy wersja zapoznawcza (CTP) technologii społeczności zestawu działań i ich wdrażania w oparciu [Windows Workflow Foundation](http://msdn.microsoft.com/netframework/aa663328.aspx)w [.NET Framework 4](http://msdn.microsoft.com/netframework/default.aspx) (WF (4) i [Windows Identity Foundation (WIF)](http://msdn.microsoft.com/security/aa570351.aspx).  Microsoft WF zabezpieczeń pakietu CTP 1 zawiera działań i ich projektantów, które przedstawiają sposób pozwala łatwo stosować różne scenariusze związane z zabezpieczeniami, za pomocą przepływu pracy, w tym:  
  
1.  Personifikacja tożsamości klienta, w przepływie pracy  
  
2.  Autoryzacja w przepływie pracy, takich jak PrincipalPermission i sprawdzania poprawności oświadczeń  
  
3.  Wiadomości uwierzytelnione przy użyciu ClientCredentials określone w przepływie pracy, takie jak nazwa użytkownika/hasło lub token pobrane z zabezpieczeń tokenu usługi (STS)  
  
4.  Token zabezpieczający klienta do usługi zaplecza (delegacji opartej na oświadczeniach) przy użyciu protokołu WS-Trust ActAs przepływu  
  
Aby uzyskać więcej informacji i Pobierz CTP pakietu zabezpieczeń WF, zobacz: [CTP pakietu zabezpieczeń WF](http://wf.codeplex.com/releases/view/48114)