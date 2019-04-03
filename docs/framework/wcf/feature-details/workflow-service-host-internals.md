---
title: Elementy wewnętrzne hosta usługi przepływu pracy
ms.date: 03/30/2017
ms.assetid: af44596f-bf6a-4149-9f04-08d8e8f45250
ms.openlocfilehash: 0596e15e27460a08f859ec3398afbeae752c86fc
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826031"
---
# <a name="workflow-service-host-internals"></a>Elementy wewnętrzne hosta usługi przepływu pracy
<xref:System.ServiceModel.WorkflowServiceHost> zapewnia hosta usługi przepływu pracy. Jest odpowiedzialny za nasłuchiwanie przychodzących wiadomości i routing je do wystąpienia usługi odpowiednie przepływu pracy, kontroluje zwalnianie i przechowywanie bezczynności przepływów pracy i innych. W tym temacie opisano, jak WorkflowServiceHost przetwarza przychodzące wiadomości.  
  
## <a name="workflowservicehost-overview"></a>WorkflowServiceHost Overview  

<xref:System.ServiceModel.WorkflowServiceHost> Klasa jest używana do hostowania usług przepływu pracy. Jej nasłuchuje komunikatów przychodzących i kieruje je do wystąpienia odpowiednią usługę, tworzenie nowych wystąpień lub ładowania istniejących wystąpień z magazynu trwałego, zgodnie z potrzebami. Na poniższym diagramie przedstawiono wysokiego poziomu dotyczące <xref:System.ServiceModel.WorkflowServiceHost> działa: 
  
 ![Diagram, który zawiera przegląd hosta usługi przepływu pracy.](./media/workflow-service-host-internals/workflow-service-host-high-level-overview.gif)  
  
 Ten diagram pokazuje, że <xref:System.ServiceModel.WorkflowServiceHost> ładuje definicje usług przepływu pracy z plikami .xamlx i ładuje informacje o konfiguracji z pliku konfiguracji. Powoduje ono również pobieranie konfiguracji śledzenia z profilu śledzenia. <xref:System.ServiceModel.WorkflowServiceHost> udostępnia punkt końcowy kontroli przepływu pracy, co pozwala na wysyłanie operacje kontroli do wystąpienia przepływu pracy.  Aby uzyskać więcej informacji, zobacz [przykładowy punkt końcowy kontroli przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md).  
  
 <xref:System.ServiceModel.WorkflowServiceHost> udostępnia również punkty końcowe aplikacji, którzy nasłuchują komunikatów przychodzących aplikacji. Po nadejściu wiadomości przychodzących (jeśli jest aktualnie załadowana) są wysyłane do wystąpienia usługi odpowiednie przepływu pracy. W razie potrzeby nowe wystąpienie przepływu pracy jest tworzony. Lub jeśli istniejącego wystąpienia zostały utrwalone jest ładowany w trwałości sklepie.  
  
## <a name="workflowservicehost-details"></a>WorkflowServiceHost Details  
 Na poniższym diagramie przedstawiono, jak <xref:System.ServiceModel.WorkflowServiceHost> obsługi wiadomości w nieco więcej szczegółów:  
  
 ![Diagram pokazujący przepływ komunikatów hosta usługi przepływu pracy.](./media/workflow-service-host-internals/workflow-service-host-message-flow.gif)  
  
 Ten diagram przedstawia trzy różne punkty końcowe, punkt końcowy aplikacji, punkt końcowy kontroli przepływu pracy i punkt końcowy hostingu przepływu pracy. Punkt końcowy aplikacji odbiera komunikaty, które są powiązane dla wystąpienia określonego przepływu pracy. Punkt końcowy kontroli przepływu pracy nasłuchuje operacje kontroli. Przepływ pracy obsługujący punkt końcowy będzie nasłuchiwać pod kątem wiadomości, które powodują <xref:System.ServiceModel.WorkflowServiceHost> załadować i uruchomić przepływy pracy bez usługi. Jak pokazano na diagramie wszystkie komunikaty są przetwarzane przez środowisko wykonawcze programu WCF.  Ograniczenie wystąpienia usługi przepływu pracy jest realizowane za pośrednictwem <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> właściwości. Ta właściwość ograniczy liczbę wystąpień usługi przepływu pracy współbieżnych. Po przekroczeniu wszelkie dodatkowe tego ograniczania żądań dla nowych wystąpień usługi przepływu pracy lub żądań, które można aktywować wystąpienia przepływu pracy utrwalonych zostanie umieszczona w kolejce. Żądań w kolejce są przetwarzane w kolejności FIFO niezależnie od tego, czy są to żądania do nowego wystąpienia lub uruchomione wystąpienie utrwalonych. Informacje o zasadach hosta jest ładowany, który określa w jaki sposób są omówione nieobsługiwanych wyjątków oraz w jaki sposób usługi przepływu pracy bezczynności są załadowane i utrwalone. Aby uzyskać więcej informacji na temat tych tematów zobacz [jak: Konfigurowanie przepływu pracy nieobsłużony wyjątek zachowanie za pomocą elementu WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/config-workflow-unhandled-exception-workflowservicehost.md) i [jak: Konfigurowanie zachowania bezczynności za pomocą elementu WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/how-to-configure-idle-behavior-with-workflowservicehost.md). Wystąpienia przepływu pracy są zachowywane zgodnie z zasadami hosta i jest załadowany ponownie, gdy potrzebne. Aby uzyskać więcej informacji na temat trwałość przepływu pracy, zobacz: [Instrukcje: Konfigurowanie trwałości za pomocą elementu WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/how-to-configure-persistence-with-workflowservicehost.md), [tworzenie długo działającej usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md), i [trwałość przepływu pracy](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md).  
  
 Na poniższej ilustracji przedstawiono przepływ, gdy wywoływana jest WorkflowServiceHost.Open:  
  
 ![Diagram pokazujący przepływ, gdy wywoływana jest WorkflowServiceHost.Open.](./media/workflow-service-host-internals/workflow-service-host-open.gif)  
  
 Przepływ pracy jest ładowany z XAML i drzewo działanie jest tworzone. <xref:System.ServiceModel.WorkflowServiceHost> Przegląda drzewo działania i tworzy opisu usługi. Konfiguracja jest stosowana do hosta. Na koniec hosta rozpoczyna nasłuchiwanie przychodzących wiadomości.  
  
 Na poniższej ilustracji przedstawiono, jakie <xref:System.ServiceModel.WorkflowServiceHost> po otrzymaniu komunikatu powiązany do działania odbierania, które ma CanCreateInstance równa `true`:  
  
 ![Algorytm używany przez hosta WFS, gdy odbierze komunikat CanCreateInstance ma wartość true.](./media/workflow-service-host-internals/workflow-service-host-receive-message-cancreateinstance.gif)  
  
 Komunikat dociera i jest przetwarzany przez stos kanału WCF. Ograniczenia są sprawdzane i korelacja zapytania są wykonywane. Jeśli komunikat jest powiązany dla istniejącego wystąpienia jest dostarczyć wiadomości. Jeśli nowe wystąpienie musi zostać utworzona, działania odbierania CanCreateInstance właściwość jest sprawdzana. Jeśli jest ustawiona wartość true, tworzone jest nowe wystąpienie i dostarczyć wiadomości.  
  
 Na poniższej ilustracji przedstawiono, jakie <xref:System.ServiceModel.WorkflowServiceHost> po otrzymaniu komunikatu powiązane działania odbierania, CanCreateInstance ustawionym na wartość false.  
  
 ![Algorytm używany przez hosta WFS, gdy odbierze komunikat CanCreateInstance ma wartość false.](./media/workflow-service-host-internals/workflow-service-host-receive-message.gif)  
  
 Komunikat dociera i jest przetwarzany przez stos kanału WCF. Ograniczenia są sprawdzane i korelacja zapytania są wykonywane. Komunikat jest powiązany dla istniejącego wystąpienia (ponieważ CanCreateInstance ma wartość false), wystąpienie jest ładowany z magazynu, zakładka zostanie wznowione i wykonuje przepływ pracy.  
  
> [!WARNING]
> Hosta usługi przepływu pracy nie będzie można otworzyć, jeśli program SQL Server jest skonfigurowana do nasłuchiwania na tylko protokół nazwany potok.  
  
## <a name="see-also"></a>Zobacz także

- [Usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Hostowanie usług przepływu pracy](../../../../docs/framework/wcf/feature-details/hosting-workflow-services.md)
- [Punkt końcowy kontroli przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md)
- [Instrukcje: Konfigurowanie przepływu pracy nieobsłużony wyjątek zachowanie za pomocą elementu WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/config-workflow-unhandled-exception-workflowservicehost.md)
- [Tworzenie długo działającej usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md)
- [Trwałość przepływu pracy](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)
