---
title: Elementy wewnętrzne hosta usługi przepływu pracy
ms.date: 03/30/2017
ms.assetid: af44596f-bf6a-4149-9f04-08d8e8f45250
ms.openlocfilehash: b95a59b0e1715b3cc18ccfea44d6c4ccd04ca5ad
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184174"
---
# <a name="workflow-service-host-internals"></a>Elementy wewnętrzne hosta usługi przepływu pracy
<xref:System.ServiceModel.WorkflowServiceHost>zapewnia hosta dla usług przepływu pracy. Jest odpowiedzialny za nasłuchiwanie wiadomości przychodzących i routing je do wystąpienia usługi przepływu pracy odpowiednie, kontroluje zwalnianie i utrwalanie bezczynnych przepływów pracy i więcej. W tym temacie opisano, jak Usługa WorkflowServiceHost przetwarza przychodzące wiadomości.  
  
## <a name="workflowservicehost-overview"></a>Omówienie usługi workflowHost  

Klasa <xref:System.ServiceModel.WorkflowServiceHost> jest używana do hosta usług przepływu pracy. Nasłuchuje wiadomości przychodzących i kieruje je do wystąpienia usługi odpowiednie, tworząc nowe wystąpienia lub ładując istniejące wystąpienia z magazynu trwałe w razie potrzeby. Na poniższym diagramie przedstawiono <xref:System.ServiceModel.WorkflowServiceHost> wysoki poziom działania:
  
 ![Diagram przedstawiający omówienie hosta usługi przepływu pracy.](./media/workflow-service-host-internals/workflow-service-host-high-level-overview.gif)  
  
 Ten diagram <xref:System.ServiceModel.WorkflowServiceHost> pokazuje, że wczytuje definicje usług przepływu pracy z plików xamlx i ładuje informacje o konfiguracji z pliku konfiguracji. Ładuje również konfigurację śledzenia z profilu śledzenia. <xref:System.ServiceModel.WorkflowServiceHost>udostępnia punkt końcowy kontroli przepływu pracy, który umożliwia wysyłanie operacji sterowania do wystąpień przepływu pracy.  Aby uzyskać więcej informacji, zobacz [przykład punktu końcowego kontroli przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md).  
  
 <xref:System.ServiceModel.WorkflowServiceHost>udostępnia również punkty końcowe aplikacji, które nasłuchują przychodzących komunikatów aplikacji. Po odebraniu wiadomości przychodzącej jest ona wysyłana do odpowiedniego wystąpienia usługi przepływu pracy (jeśli jest aktualnie załadowana). W razie potrzeby zostanie utworzone nowe wystąpienie przepływu pracy. Lub jeśli istniejące wystąpienie zostało utrwalone jest ładowany z magazynu trwałości.  
  
## <a name="workflowservicehost-details"></a>Szczegóły usługi WorkflowHost  
 Na poniższym <xref:System.ServiceModel.WorkflowServiceHost> diagramie pokazano, jak obsługuje wiadomości w nieco bardziej szczegółowo:  
  
 ![Diagram przedstawiający przepływ komunikatów hosta usługi przepływu pracy.](./media/workflow-service-host-internals/workflow-service-host-message-flow.gif)  
  
 Ten diagram przedstawia trzy różne punkty końcowe, punkt końcowy aplikacji, punkt końcowy kontroli przepływu pracy i punkt końcowy hostingu przepływu pracy. Punkt końcowy aplikacji odbiera komunikaty, które są powiązane dla określonego wystąpienia przepływu pracy. Punkt końcowy kontroli przepływu pracy nasłuchuje operacji sterowania. Punkt końcowy hostingu przepływu pracy nasłuchuje komunikatów, które powodują <xref:System.ServiceModel.WorkflowServiceHost> ładowanie i wykonywanie przepływów pracy nieusługowych. Jak pokazano na diagramie wszystkie komunikaty są przetwarzane za pośrednictwem środowiska wykonawczego WCF.  Ograniczanie wystąpienia usługi przepływu pracy jest <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> osiągane przy użyciu właściwości. Ta właściwość ograniczy liczbę wystąpień usługi równoczesnych przepływów pracy. Po przekroczeniu tej przepustnicy wszelkie dodatkowe żądania dla nowych wystąpień usługi przepływu pracy lub żądania aktywowania utrwalonych wystąpień przepływu pracy będą umieszczane w kolejce. Żądania w kolejce są przetwarzane w kolejności FIFO, niezależnie od tego, czy są to żądania dla nowego wystąpienia, czy uruchomione, utrwalone wystąpienie. Informacje o zasadach hosta są ładowane, który określa, jak nieobsługiwane wyjątki są rozpatrywane i jak bezczynne usługi przepływu pracy są zwalniane i utrwalone. Aby uzyskać więcej informacji na temat tych tematów, zobacz [Jak: Konfigurowanie zachowania nieobsługiwalnych wyjątków przepływu pracy za pomocą usługi WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/config-workflow-unhandled-exception-workflowservicehost.md) i [jak: Konfigurowanie zachowania bezczynności za pomocą usługi WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/how-to-configure-idle-behavior-with-workflowservicehost.md). Wystąpienia przepływu pracy są utrwalone zgodnie z zasadami hosta i są ponownie ładowane w razie potrzeby. Aby uzyskać więcej informacji na temat trwałości przepływu pracy, zobacz: [Jak: Konfigurowanie trwałości za pomocą usługi WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/how-to-configure-persistence-with-workflowservicehost.md), [Tworzenie długotrwałej usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md)i [Trwałość przepływu pracy](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md).  
  
 Na poniższej ilustracji przedstawiono przepływ, gdy wywoływany jest plik WorkflowServiceHost.Open:  
  
 ![Diagram, który pokazuje przepływ, gdy usługa WorkflowServiceHost.Open jest wywoływana.](./media/workflow-service-host-internals/workflow-service-host-open.gif)  
  
 Przepływ pracy jest ładowany z XAML i tworzone jest drzewo aktywności. <xref:System.ServiceModel.WorkflowServiceHost>prowadzi drzewo aktywności i tworzy opis usługi. Konfiguracja jest stosowana do hosta. Na koniec host zaczyna nasłuchiwać wiadomości przychodzących.  
  
 Na poniższej <xref:System.ServiceModel.WorkflowServiceHost> ilustracji przedstawiono, co robi po odebraniu wiadomości związane z `true`Receive działania, który cancreateinstance ustawiono:  
  
 ![Drzewo decyzyjne używane przez hosta WFS po odebraniu wiadomości i CanCreateInstance jest true.](./media/workflow-service-host-internals/workflow-service-host-receive-message-cancreateinstance.gif)  
  
 Komunikat dociera i jest przetwarzany przez stos kanału WCF. Throttles są sprawdzane i kwerendy korelacji są wykonywane. Jeśli wiadomość jest powiązana dla istniejącego wystąpienia, wiadomość jest dostarczana. Jeśli nowe wystąpienie musi zostać utworzone, receive działania CanCreateInstance właściwość jest zaznaczona. Jeśli jest ustawiona na true, zostanie utworzone nowe wystąpienie i wiadomość zostanie dostarczona.  
  
 Na poniższej <xref:System.ServiceModel.WorkflowServiceHost> ilustracji przedstawiono, co robi, gdy odbiera wiadomość powiązaną z Receive działania, który cancreateinstance ustawiono false.  
  
 ![Drzewo decyzyjne używane przez hosta WFS po odebraniu wiadomości i CanCreateInstance jest false.](./media/workflow-service-host-internals/workflow-service-host-receive-message.gif)  
  
 Komunikat dociera i jest przetwarzany przez stos kanału WCF. Throttles są sprawdzane i kwerendy korelacji są wykonywane. Wiadomość jest powiązana dla istniejącego wystąpienia (ponieważ CanCreateInstance jest false), więc wystąpienie jest ładowane z magazynu trwałości, zakładka jest wznawiana i wykonuje przepływ pracy.  
  
> [!WARNING]
> Host usługi przepływu pracy nie zostanie otwarty, jeśli program SQL Server jest skonfigurowany do nasłuchiwanie tylko na protokole NamedPipe.  
  
## <a name="see-also"></a>Zobacz też

- [Usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Hostowanie usług przepływu pracy](../../../../docs/framework/wcf/feature-details/hosting-workflow-services.md)
- [Punkt końcowy kontroli przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md)
- [Instrukcje: konfigurowanie zachowania dotyczącego nieobsługiwanego wyjątku przepływu pracy przy użyciu klasy WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/config-workflow-unhandled-exception-workflowservicehost.md)
- [Tworzenie długo działającej usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md)
- [Trwałość przepływu pracy](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)
