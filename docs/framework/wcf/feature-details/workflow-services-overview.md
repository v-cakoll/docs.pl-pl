---
title: Przegląd usług przepływu pracy
ms.date: 03/30/2017
ms.assetid: e536dda3-e286-441e-99a7-49ddc004b646
ms.openlocfilehash: eaf5fb4b20aca0983dcbe00724ab81803834940a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="workflow-services-overview"></a>Przegląd usług przepływu pracy
Usługi przepływu pracy są usług WCF, które są implementowane przy użyciu przepływów pracy. Usługi przepływu pracy są przepływy pracy używające działania obsługi wiadomości do wysyłania i odbierania wiadomości Windows Communication Foundation (WCF). .NET framework 4.5 wprowadzono wiele działań obsługi komunikatów, które umożliwia wysyłanie i odbieranie wiadomości z poziomu przepływu pracy. Aby uzyskać więcej informacji dotyczących działań i jak one używane do implementowania wzorce exchange inny komunikat do obsługi komunikatów, zobacz [wiadomości działania](../../../../docs/framework/wcf/feature-details/messaging-activities.md).  
  
## <a name="benefits-of-using-workflow-services"></a>Korzyści wynikające ze stosowania usług przepływu pracy  
 Jak aplikacje stają się coraz bardziej dystrybuowane, poszczególnych usług stają się odpowiedzialny za wywoływanie innych usług w celu odciążenia część obciążenia pracą. Wdrażanie tych wywołań jako operacji asynchronicznych wprowadza pewne złożoności do kodu. Obsługa błędów dodaje stopnia złożoności w formularzu, obsługa wyjątków i udostępnia szczegółowe informacje śledzenia. Niektóre usługi są często, długotrwałą i może trwać cenne zasoby systemowe podczas oczekiwania na dane wejściowe. Z powodu problemów z tymi aplikacje rozproszone są często bardzo złożonych i trudne do zapisu i zarządzania. Przepływy pracy są fizyczną sposobem express koordynacji zadanie asynchroniczne, szczególnie wywołania usług zewnętrznych. Przepływy pracy są również obowiązujące reprezentujący długotrwałe procesów biznesowych. Jest tych klas, wchodzące w przepływie pracy dużą zasobów do tworzenia usług w środowisku rozproszonym.  
  
## <a name="implementing-a-workflow-service"></a>Wdrażanie usługi przepływu pracy  
 Podczas wdrażania usługi WCF, należy określić numer kontraktów opisujących usługę i wysyła i odbiera dane. Dane są reprezentowane jako kontraktów danych i kontrakty komunikatu. Usługi WCF, zarówno i przepływu pracy Użyj definicje kontraktu danych kontraktu i wiadomości jako części opisy usług. Sama usługa przedstawia metadanych (w formie WSDL) do opisania działania usługi. W programie WCF kontraktów usług i kontrakty operacji definiują usługi i operacje, które obsługuje. Jednak w usłudze przepływu pracy, umowy te są częścią sam proces biznesowy. Są one widoczne w metadanych przez proces, nazywany wnioskowania kontraktu. Gdy usługa przepływu pracy jest obsługiwana przy użyciu <xref:System.ServiceModel.Activities.WorkflowServiceHost>, definicji przepływu pracy się zbadana i kontrakt jest generowany na podstawie zestawu działań w przepływie pracy do obsługi komunikatów. W szczególności następujące działania i właściwości są używane do generowania kontraktu:  
  
 <xref:System.ServiceModel.Activities.Receive> Działanie  
  
-   <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>  
  
-   <!--zz <xref:System.ServiceModel.Activities.Receive.OperationContractName%2A>  --> `System.ServiceModel.Activities.Receive.OperationContractName`
  
-   <xref:System.ServiceModel.Activities.Receive.Action%2A>  
  
-   <!--zz <xref:System.ServiceModel.Activities.Receive.ValueType%2A>  --> `System.ServiceModel.Activities.Receive.ValueType`
  
 <xref:System.ServiceModel.Activities.SendReply> Działanie  
  
-   <xref:System.ServiceModel.Activities.SendReply.Action%2A>  
  
-   <!--zz <xref:System.ServiceModel.Activities.SendReply.ValueType%2A> -->
`xref:System.ServiceModel.Activities.SendReply.ValueType`
  
 <xref:System.ServiceModel.Activities.TransactedReceiveScope> Działanie  
  
 W rezultacie wnioskowania kontraktu jest opis usługi przy użyciu tych samych struktur danych jako usługi WCF i kontrakty operacji. Te informacje jest następnie używane do udostępnienia WSDL usługi przepływu pracy.  
  
> [!NOTE]
>  [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] nie pozwalają na zapis usług przepływu pracy przy użyciu istniejącej definicji kontraktu nie obsługują kilka dodatkowych narzędzi. Kontrakty usług przepływu pracy są tworzone przez proces wnioskowania umowy omówionych wcześniej. Kontrakty komunikatów i kontraktów danych są w pełni obsługiwane, ale.  
  
## <a name="workflow-services-and-msmq-based-bindings"></a>Usługi przepływu pracy i powiązania na podstawie usługi MSMQ  
 Usługi WCF definiuje dwa powiązania usługi MSMQ na podstawie <xref:System.ServiceModel.NetMsmqBinding> i <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.  Na podstawie MSMQ powiązania są często używane z usług przepływu pracy z powodu długotrwałej rodzaj takich usług. Na podstawie MSMQ powiązania mieć `ValidityDuration` właściwość, która określa, jak długo można założyć wiadomości usługi MSMQ, aby identyfikator był prawidłowy. Z powodu długotrwałej rodzaj usług przepływu pracy jest możliwe, że okres ważności wiadomości MSMQ może upłynąć usługi przepływu pracy można go przetworzyć. W związku z tym jest bardzo ważne, aby ustawić okres ważności wiązania usługi MSMQ do odpowiedniej wartości. Ta wartość musi być wybrana oparte na przepływie pracy i jak przetwarza wiadomości. Na przykład jeśli masz przepływu pracy z <xref:System.ServiceModel.Activities.Receive> działania następuje działań niestandardowych, który przyjmuje 10 minut, a następnie przez inny <xref:System.ServiceModel.Activities.Receive> działanie, poprawną wartość dla `ValidityDuration` będzie większa niż 10 minut.  
  
## <a name="hosting-a-workflow-service"></a>Hosting usług przepływu pracy  
 Jak usługi WCF usług przepływu pracy musi być obsługiwana. Użyj usług WCF <xref:System.ServiceModel.ServiceHost> klasy do hostowania usług i przepływ pracy usług użyj <xref:System.ServiceModel.Activities.WorkflowServiceHost> do hostowania usług. Jak usługi WCF usług przepływu pracy mogą być hostowane na wiele sposobów, na przykład:  
  
-   W zarządzanych [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aplikacji.  
  
-   W Internetowych usługach informacyjnych (IIS).  
  
-   W usłudze aktywacji procesów systemu Windows (WAS).  
  
-   W zarządzanych usług systemu Windows.  
  
 Przepływ pracy usług hostowanych w zarządzanych [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aplikacji lub zarządzanych usług systemu Windows, Utwórz wystąpienie <xref:System.ServiceModel.Activities.WorkflowServiceHost> klasy i przekaż go wystąpienia <xref:System.ServiceModel.Activities.WorkflowService> zawierający definicję przepływu pracy w <xref:System.ServiceModel.Activities.WorkflowService.Body%2A> właściwości. Definicji przepływu pracy, który obejmuje działania dotyczące komunikatów jest udostępniany jako usługa przepływu pracy.  
  
 Do hosta usługi przepływu pracy w usługach IIS lub WAS, umieść plik .xamlx, który zawiera definicję usługi przepływu pracy do katalogu wirtualnego. Domyślny punkt końcowy (przy użyciu <xref:System.ServiceModel.BasicHttpBinding>) jest tworzone automatycznie, aby uzyskać więcej informacji, zobacz [uproszczony konfiguracji](../../../../docs/framework/wcf/simplified-configuration.md). Można również umieścić plik Web.config w katalogu wirtualnego, aby określić własne punktów końcowych. Jeśli definicja przepływu pracy znajduje się w zestawie można umieścić plików .svc w katalogu wirtualnym i zestawu przepływu pracy w katalogu App_Code. W pliku svc należy określić fabryki hostów usług i klasy, która implementuje usługi przepływu pracy. Poniższy przykład pokazuje, jak wybierz fabryki hostów usług i określ klasy, która implementuje usługi przepływu pracy.  
  
```  
<%@ServiceHost Factory=" System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory  
Service="EchoService"%>  
```
