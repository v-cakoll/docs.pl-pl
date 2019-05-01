---
title: Przegląd usług przepływu pracy — WCF
ms.date: 03/30/2017
ms.assetid: e536dda3-e286-441e-99a7-49ddc004b646
ms.openlocfilehash: 1461ef545c4b31f84e62d82453320179d9aa74e0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62050340"
---
# <a name="workflow-services-overview"></a>Przegląd usług przepływu pracy

Usługi przepływu pracy są usługi oparte na protokole WCF, które są implementowane przy użyciu przepływów pracy. Usługi przepływu pracy są przepływy pracy korzystające z działań dotyczących komunikatów w celu wysyłania i odbierania komunikatów Windows Communication Foundation (WCF). .NET framework 4.5 wprowadzono szereg działań dotyczących komunikatów, które umożliwiają wysyłanie i odbieranie komunikatów z przepływu pracy. Aby uzyskać więcej informacji na temat obsługi komunikatów, działań i jak ich może służyć do implementowania wzorców exchange inny komunikat, zobacz [działań Messaging](messaging-activities.md).

## <a name="benefits-of-using-workflow-services"></a>Korzyści z używania usługi przepływu pracy

Jak aplikacje stają się coraz bardziej dystrybuowane, poszczególnych usług stają się odpowiada za wywołanie innych usług w celu odciążenia część obciążenia pracą. Implementowanie tych wywołań jako operacji asynchronicznych wprowadza złożoność w kodzie. Obsługa błędów dodaje dodatkowej złożoności w formie obsługi wyjątków, a także szczegółowe informacje śledzenia. Niektóre usługi są często długotrwałe i może potrwać cennych zasobów systemowych podczas oczekiwania na dane wejściowe. Ze względu na te problemy aplikacje rozproszone są często bardzo złożone i trudne do pisania i konserwacji. Przepływy pracy są w naturalny sposób wyrażania koordynacji prac asynchronicznych, szczególnie wywołania usług zewnętrznych. Przepływy pracy są również obowiązujące od reprezentujący długotrwałe procesy biznesowe. Jest tych klas, wchodzące w przepływie pracy wspaniałych zasobów do tworzenia usług w środowisku rozproszonym.

## <a name="implementing-a-workflow-service"></a>Wdrażanie usługi przepływu pracy

Podczas implementowania usługi WCF, należy zdefiniować liczbę zamówień, które opisują usługi i dane, które wysyła i odbiera. Dane są reprezentowane jako kontraktów danych i kontrakty komunikatów. Usługi WCF i przepływu pracy Użyj definicje kontraktu danych kontraktu i komunikat jako część opisy usług. Sama usługa udostępnia metadane (w formie WSDL) do opisywania operacje usługi. W programie WCF kontraktów usług i kontrakty operacji definiują usługi i operacje, które obsługuje. Jednak w usłudze przepływu pracy, umowy te są częścią procesu biznesowego, sam. Są one widoczne w metadanych w procesie nazywanym wnioskowania kontraktu. Gdy usługi przepływu pracy znajduje się za pomocą <xref:System.ServiceModel.Activities.WorkflowServiceHost>definicji przepływu pracy jest badany i kontrakt jest generowany na podstawie zestawu działań w przepływie pracy do obsługi komunikatów. W szczególności następujące działania i właściwości są używane do generowania umowy:

<xref:System.ServiceModel.Activities.Receive> Działanie

- <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>

- <xref:System.ServiceModel.Activities.Receive.OperationName%2A>

- <xref:System.ServiceModel.Activities.Receive.Action%2A>

<xref:System.ServiceModel.Activities.SendReply> Działanie

- <xref:System.ServiceModel.Activities.SendReply.Action%2A>

<xref:System.ServiceModel.Activities.TransactedReceiveScope> Działanie

Wynik końcowy wnioskowania kontraktu jest opis usługi przy użyciu tych samych struktur danych jako usługi WCF i kontrakty operacji. Te informacje jest następnie używane do udostępnienia WSDL usługi przepływu pracy.

> [!NOTE]
> [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] Umożliwia pisanie usług przepływu pracy przy użyciu istniejącą definicję kontraktu bez obsługi niektórych dodatkowych narzędzi. Kontrakty usług przepływu pracy są tworzone przez proces wnioskowania umowy omówionych wcześniej. Kontrakty komunikatów i kontrakty danych są w pełni obsługiwane, ale.

## <a name="workflow-services-and-msmq-based-bindings"></a>Usługi przepływu pracy i powiązań na podstawie usługi MSMQ

Usługi WCF definiuje dwa powiązania opartych na usłudze MSMQ <xref:System.ServiceModel.NetMsmqBinding> i <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.  Oparte na usłudze MSMQ powiązania są często używane przy użyciu usług przepływu pracy ze względu na charakter długotrwałych tych usług. Oparte na usłudze MSMQ powiązania ma `ValidityDuration` właściwość, która określa, ile wiadomości usługi MSMQ, można założyć był prawidłowy. Ze względu na rodzaj długo działającej usługi przepływu pracy jest możliwe, że okres ważności wiadomości usługi MSMQ może upłynąć, zanim usługa przepływu pracy można go przetworzyć. W związku z tym jest bardzo ważne, aby ustawić okres ważności powiązanie usługi MSMQ do odpowiedniej wartości. Ta wartość musi być wybierane na podstawie przepływu pracy i jak są przetwarzane komunikaty. Na przykład jeśli masz przepływ pracy o <xref:System.ServiceModel.Activities.Receive> działania niestandardowe działanie, które przyjmuje 10 minut, a następnie następuje innego <xref:System.ServiceModel.Activities.Receive> aktywności, poprawnej wartości `ValidityDuration` będzie większa niż 10 minut.

## <a name="hosting-a-workflow-service"></a>Hostowanie usługi przepływu pracy

Podobnie jak usługi WCF usług przepływu pracy musi być obsługiwana. Użyj usług WCF <xref:System.ServiceModel.ServiceHost> klasy do hostowania usług i przepływ pracy usługi użyj <xref:System.ServiceModel.Activities.WorkflowServiceHost> do hostowania usług. Podobnie jak usługi WCF usług przepływu pracy mogą być hostowane na wiele sposobów, na przykład:

- W zarządzanej [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aplikacji.

- In Internet Information Services (IIS).

- W przypadku usługi Windows Process Activation Service (WAS).

- W ramach zarządzanej usługi Windows.

Przepływ pracy usług hostowanych w zarządzanej [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aplikacji lub zarządzanych usług Windows, Utwórz wystąpienie obiektu <xref:System.ServiceModel.Activities.WorkflowServiceHost> klasy i przekazać go wystąpienie <xref:System.ServiceModel.Activities.WorkflowService> zawierający definicję przepływu pracy w ramach <xref:System.ServiceModel.Activities.WorkflowService.Body%2A> właściwości. Definicja przepływu pracy, który zawiera działań dotyczących komunikatów jest udostępniany jako usługa przepływu pracy.

Hostowanie usługi przepływu pracy w usługach IIS i WAS, należy umieścić plik .xamlx, który zawiera definicję usługi przepływu pracy do katalogu wirtualnego. Domyślny punkt końcowy (przy użyciu <xref:System.ServiceModel.BasicHttpBinding>) jest tworzone automatycznie, aby uzyskać więcej informacji, zobacz [uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md). Można także umieścić plik Web.config w katalogu wirtualnym, aby określić własne punkty końcowe. Jeśli Twoja definicja przepływu pracy jest w zestawie, można umieścić plików .svc w katalogu wirtualnego i zestawu przepływu pracy w katalogu App_Code. Plik .svc należy określić fabryki hostów usług i klasy, która implementuje usługi przepływu pracy. Poniższy przykład pokazuje, jak określić fabryki hostów usług i określić klasę, która implementuje usługi przepływu pracy.

```
<%@ServiceHost Factory=" System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory
Service="EchoService"%>
```