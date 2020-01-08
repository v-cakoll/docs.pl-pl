---
title: Usługi przepływu pracy — Omówienie
ms.date: 03/30/2017
ms.assetid: e536dda3-e286-441e-99a7-49ddc004b646
ms.openlocfilehash: cb013dd419d09af61eaff290709164427b1b655f
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347864"
---
# <a name="workflow-services-overview"></a>Usługi przepływu pracy — Omówienie

Usługi przepływu pracy są usługami opartymi na WCF, które są implementowane za pomocą przepływów pracy. Usługi przepływu pracy to przepływy pracy korzystające z działań związanych z przesyłaniem komunikatów w celu wysyłania i odbierania komunikatów Windows Communication Foundation (WCF). W .NET Framework 4,5 wprowadzono wiele działań związanych z obsługą komunikatów, które umożliwiają wysyłanie i odbieranie komunikatów z przepływu pracy. Aby uzyskać więcej informacji o działaniach związanych z obsługą komunikatów i sposobach ich użycia do implementowania różnych wzorców wymiany komunikatów, zobacz [działania dotyczące komunikatów](messaging-activities.md).

## <a name="benefits-of-using-workflow-services"></a>Zalety korzystania z usług Workflow Services

Gdy aplikacje stają się coraz bardziej dystrybuowane, poszczególne usługi staną się odpowiedzialne za wywoływanie innych usług w celu odciążenia części pracy. Implementacja tych wywołań jako operacje asynchroniczne wprowadza pewną złożoność do kodu. Obsługa błędów dodaje dodatkową złożoność w postaci obsługi wyjątków i dostarczając szczegółowe informacje o śledzeniu. Niektóre usługi są często długotrwałe i mogą przyjmować cenne zasoby systemowe podczas oczekiwania na dane wejściowe. Ze względu na te problemy aplikacje rozproszone są często bardzo skomplikowane i trudno je pisać i konserwować. Przepływy pracy są naturalnym sposobem wyrażania koordynacji pracy asynchronicznej, szczególnie wywołań usług zewnętrznych. Przepływy pracy są również efektywne dla reprezentowania długotrwałych procesów roboczych. Są to te jakości, które sprawiają, że przepływ pracy jest doskonałym zasobem do kompilowania usług w środowisku rozproszonym.

## <a name="implementing-a-workflow-service"></a>Implementowanie usługi przepływu pracy

Podczas implementowania usługi WCF należy zdefiniować kilka kontraktów, które opisują usługę i dane wysyłane i odbierane. Dane są reprezentowane jako Kontrakty danych i kontrakty komunikatów. Usługi WCF i Workflow Services korzystają z kontraktów danych i definicji kontraktu komunikatów w ramach opisów usług. Sama usługa ujawnia metadane (w postaci WSDL) opisujące operacje usługi. W programie WCF kontrakty usług i kontrakty operacji definiują usługę i obsługiwane przez nią operacje. Jednak w usłudze przepływu pracy te kontrakty są częścią procesu biznesowego. Są one ujawniane w metadanych przez proces o nazwie wnioskowanie kontraktu. Gdy usługa przepływu pracy jest hostowana przy użyciu <xref:System.ServiceModel.Activities.WorkflowServiceHost>, sprawdzana jest definicja przepływu pracy i jest generowana umowa oparta na zestawie działań obsługi komunikatów znalezionych w przepływie pracy. W szczególności następujące działania i właściwości są używane do generowania kontraktu:

Działanie <xref:System.ServiceModel.Activities.Receive>

- <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>

- <xref:System.ServiceModel.Activities.Receive.OperationName%2A>

- <xref:System.ServiceModel.Activities.Receive.Action%2A>

Działanie <xref:System.ServiceModel.Activities.SendReply>

- <xref:System.ServiceModel.Activities.SendReply.Action%2A>

Działanie <xref:System.ServiceModel.Activities.TransactedReceiveScope>

Końcowy wynik wnioskowania o umowę to opis usługi przy użyciu tych samych struktur danych, co w przypadku usług WCF i kontraktów operacji. Te informacje są następnie używane w celu udostępnienia WSDL dla usługi przepływu pracy.

> [!NOTE]
> [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] nie pozwala na pisanie usług przepływu pracy przy użyciu istniejącej definicji kontraktu bez dodatkowej obsługi narzędzi. Kontrakty usługi przepływu pracy są tworzone w omawianym wcześniej procesie wnioskowania o umowę. Umowy dotyczące komunikatów i kontrakty danych są jednak w pełni obsługiwane.

## <a name="workflow-services-and-msmq-based-bindings"></a>Usługi przepływu pracy i powiązania oparte na usłudze MSMQ

Funkcja WCF definiuje dwa powiązania oparte na usłudze MSMQ <xref:System.ServiceModel.NetMsmqBinding> i <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.  Powiązania oparte na usłudze MSMQ są często używane z usługami Workflow Services ze względu na długotrwały charakter takich usług. Powiązania oparte na usłudze MSMQ mają właściwość `ValidityDuration`, która określa, jak długo komunikaty MSMQ mogą być prawidłowe. Ze względu na długotrwały charakter usług przepływu pracy istnieje możliwość, że okres ważności komunikatu MSMQ może upłynąć, zanim usługa przepływu pracy będzie mogła je przetworzyć. Dlatego bardzo ważne jest, aby ustawić okres ważności powiązania usługi MSMQ na odpowiednią wartość. Ta wartość musi być wybierana na podstawie przepływu pracy i sposobu przetwarzania komunikatów przez nią. Na przykład jeśli masz przepływ pracy z działaniem <xref:System.ServiceModel.Activities.Receive>, po którym następuje działanie niestandardowe, które trwa 10 minut, a po nim działa inne działanie <xref:System.ServiceModel.Activities.Receive>, poprawna wartość dla `ValidityDuration` będzie większa niż 10 minut.

## <a name="hosting-a-workflow-service"></a>Hostowanie usługi przepływu pracy

Podobnie jak w przypadku usług WCF usługi przepływu pracy muszą być hostowane. Usługi WCF używają klasy <xref:System.ServiceModel.ServiceHost>, aby hostować usługi i usługi przepływu pracy przy użyciu <xref:System.ServiceModel.Activities.WorkflowServiceHost> do usług hosta. Podobnie jak w przypadku usług WCF usługi przepływu pracy mogą być hostowane na różne sposoby, na przykład:

- W zarządzanej aplikacji .NET Framework.

- W Internet Information Services (IIS).

- W usłudze aktywacji procesów systemu Windows (WAS).

- W usłudze zarządzanej systemu Windows.

Usługi przepływu pracy hostowane w zarządzanej aplikacji .NET Framework lub zarządzanej usłudze systemu Windows tworzą wystąpienie klasy <xref:System.ServiceModel.Activities.WorkflowServiceHost> i przekażą wystąpienie <xref:System.ServiceModel.Activities.WorkflowService>, które zawiera definicję przepływu pracy w ramach właściwości <xref:System.ServiceModel.Activities.WorkflowService.Body%2A>. Definicja przepływu pracy, która zawiera działania dotyczące komunikatów, jest udostępniana jako usługa przepływu pracy.

Aby hostować usługę przepływu pracy w usługach IIS lub WAS, Umieść plik. xamlx, który zawiera definicję usługi przepływu pracy w katalogu wirtualnym. Domyślny punkt końcowy (przy użyciu <xref:System.ServiceModel.BasicHttpBinding>) jest tworzony automatycznie, aby uzyskać więcej informacji, zobacz [Uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md). Możesz również umieścić plik Web. config w katalogu wirtualnym, aby określić własne punkty końcowe. Jeśli definicja przepływu pracy znajduje się w zestawie, można umieścić plik. svc w katalogu wirtualnym i zestaw przepływu pracy w katalogu App_Code. Plik SVC musi określać fabrykę hosta usługi i klasę implementującą usługę przepływu pracy. Poniższy przykład pokazuje, jak określić fabrykę hosta usługi i określić klasę implementującą usługę przepływu pracy.

```
<%@ServiceHost Factory=" System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory
Service="EchoService"%>
```
