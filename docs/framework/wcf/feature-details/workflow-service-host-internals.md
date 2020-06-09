---
title: Elementy wewnętrzne hosta usługi przepływu pracy
ms.date: 03/30/2017
ms.assetid: af44596f-bf6a-4149-9f04-08d8e8f45250
ms.openlocfilehash: 7b47293211ee8143b1ce713c64ff1d5b22161b45
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594884"
---
# <a name="workflow-service-host-internals"></a>Elementy wewnętrzne hosta usługi przepływu pracy
<xref:System.ServiceModel.WorkflowServiceHost>dostarcza hosta dla usług przepływu pracy. Jest on odpowiedzialny za nasłuchiwanie przychodzących komunikatów i kierowanie ich do odpowiedniego wystąpienia usługi przepływu pracy, kontroluje wyładowywanie i utrzymywanie bezczynnych przepływów pracy oraz nie tylko. W tym temacie opisano sposób przetwarzania komunikatów przychodzących przez obiekt WorkflowServiceHost.  
  
## <a name="workflowservicehost-overview"></a>Omówienie obiektu WorkflowServiceHost  

<xref:System.ServiceModel.WorkflowServiceHost>Klasa jest używana do hostowania usług przepływu pracy. Nasłuchuje komunikatów przychodzących i kieruje je do odpowiedniego wystąpienia usługi, tworząc nowe wystąpienia lub ładując istniejące wystąpienia z trwałego magazynu, zgodnie z potrzebami. Na poniższym diagramie przedstawiono, jak <xref:System.ServiceModel.WorkflowServiceHost> działa:
  
 ![Diagram przedstawiający przegląd hosta usługi przepływu pracy.](./media/workflow-service-host-internals/workflow-service-host-high-level-overview.gif)  
  
 Ten diagram pokazuje, że <xref:System.ServiceModel.WorkflowServiceHost> ładuje definicje usługi przepływu pracy z plików. xamlx i ładuje informacje o konfiguracji z pliku konfiguracyjnego. Ładuje również konfigurację śledzenia z profilu śledzenia. <xref:System.ServiceModel.WorkflowServiceHost>uwidacznia punkt końcowy sterowania przepływem pracy, który umożliwia wysyłanie operacji sterowania do wystąpień przepływu pracy.  Aby uzyskać więcej informacji, zobacz [przykład punktu końcowego kontroli przepływu pracy](workflow-control-endpoint.md).  
  
 <xref:System.ServiceModel.WorkflowServiceHost>udostępnia również punkty końcowe aplikacji, które nasłuchują przychodzących komunikatów aplikacji. Po nadejściu komunikatu przychodzącego jest on wysyłany do odpowiedniego wystąpienia usługi przepływu pracy (jeśli jest aktualnie załadowana). W razie konieczności zostanie utworzone nowe wystąpienie przepływu pracy. Lub jeśli istniejące wystąpienie zostało utrwalone, jest ładowane z magazynu trwałości.  
  
## <a name="workflowservicehost-details"></a>Szczegóły obiektu WorkflowServiceHost  
 Na poniższym diagramie przedstawiono sposób <xref:System.ServiceModel.WorkflowServiceHost> obsługi komunikatów na nieco bardziej szczegółowy:  
  
 ![Diagram przedstawiający przepływ komunikatów hosta usługi przepływu pracy.](./media/workflow-service-host-internals/workflow-service-host-message-flow.gif)  
  
 Ten diagram przedstawia trzy różne punkty końcowe, punkt końcowy aplikacji, punkt końcowy sterowania przepływem pracy oraz punkt końcowy hostingu przepływu pracy. Punkt końcowy aplikacji odbiera komunikaty, które są powiązane z określonym wystąpieniem przepływu pracy. Punkt końcowy sterowania przepływem pracy nasłuchuje operacji sterowania. Punkt końcowy hostingu przepływu pracy nasłuchuje komunikatów, które powodują <xref:System.ServiceModel.WorkflowServiceHost> ładowanie i wykonywanie przepływów pracy innych niż usługi. Jak pokazano na diagramie, wszystkie komunikaty są przetwarzane przez środowisko uruchomieniowe WCF.  Ograniczanie wystąpienia usługi przepływu pracy jest realizowane przy użyciu <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> właściwości. Ta właściwość ogranicza liczbę współbieżnych wystąpień usługi przepływu pracy. W przypadku przekroczenia limitu przepustowości wszystkie dodatkowe żądania dla nowych wystąpień usługi przepływu pracy lub żądania aktywowania utrwalonych wystąpień przepływów pracy zostaną dodane do kolejki. Żądania w kolejce są przetwarzane w kolejności FIFO niezależnie od tego, czy są żądaniami dla nowego wystąpienia, czy działającym, utrwalonym wystąpieniem. Załadowano informacje o zasadach hosta, które określają sposób postępowania z nieobsługiwanymi wyjątkami oraz sposób, w jaki bezczynne usługi przepływu pracy są zwalniane i utrwalane. Aby uzyskać więcej informacji na temat tych tematów, zobacz [jak: Konfigurowanie zachowania nieobsługiwanego wyjątku przepływu pracy przy użyciu obiektu WorkflowServiceHost](config-workflow-unhandled-exception-workflowservicehost.md) i [instrukcje: Konfigurowanie zachowania bezczynności z](how-to-configure-idle-behavior-with-workflowservicehost.md)obiektem WorkflowServiceHost. Wystąpienia przepływu pracy są utrwalane zgodnie z zasadami hosta i są ponownie ładowane w razie potrzeby. Aby uzyskać więcej informacji na temat trwałości przepływu pracy, zobacz: [How to: Configure trwałości with WorkflowServiceHost](how-to-configure-persistence-with-workflowservicehost.md), [Tworzenie długotrwałej usługi przepływu pracy](creating-a-long-running-workflow-service.md)i [trwałość przepływu pracy](../../windows-workflow-foundation/workflow-persistence.md).  
  
 Na poniższej ilustracji przedstawiono przepływ, gdy jest wywoływany obiekt WorkflowServiceHost. Open:  
  
 ![Diagram pokazujący przepływ, gdy jest wywoływany obiekt WorkflowServiceHost. Open.](./media/workflow-service-host-internals/workflow-service-host-open.gif)  
  
 Przepływ pracy jest ładowany z XAML i tworzone jest drzewo aktywności. <xref:System.ServiceModel.WorkflowServiceHost>przegląda drzewo aktywności i tworzy Opis usługi. Konfiguracja została zastosowana do hosta. Na koniec Host rozpocznie nasłuchiwanie komunikatów przychodzących.  
  
 Na poniższej ilustracji pokazano, co się stało, <xref:System.ServiceModel.WorkflowServiceHost> gdy odbierze komunikat powiązany dla działania Receive, które ma ustawioną CanCreateInstance `true` :  
  
 ![Drzewo decyzyjne używane przez hosta WFS, gdy odbierze komunikat, a CanCreateInstance ma wartość true.](./media/workflow-service-host-internals/workflow-service-host-receive-message-cancreateinstance.gif)  
  
 Wiadomość zostanie odebrana i przetworzona przez stos kanału WCF. Ograniczenia są zaznaczone, a zapytania korelacji są wykonywane. Jeśli komunikat jest powiązany z istniejącym wystąpieniem, komunikat zostanie dostarczony. Jeśli trzeba utworzyć nowe wystąpienie, właściwość CanCreateInstance działania Receive jest sprawdzana. Jeśli ma wartość true, zostanie utworzone nowe wystąpienie i zostanie wyświetlony komunikat.  
  
 Na poniższej ilustracji pokazano, co się stało, <xref:System.ServiceModel.WorkflowServiceHost> gdy odbierze komunikat powiązany dla działania Receive, którego wartość CanCreateInstance ma wartość false.  
  
 ![Drzewo decyzyjne używane przez hosta WFS, gdy odbierze komunikat, a CanCreateInstance ma wartość false.](./media/workflow-service-host-internals/workflow-service-host-receive-message.gif)  
  
 Wiadomość zostanie odebrana i przetworzona przez stos kanału WCF. Ograniczenia są zaznaczone, a zapytania korelacji są wykonywane. Komunikat jest powiązany z istniejącym wystąpieniem (ponieważ CanCreateInstance ma wartość false), więc wystąpienie jest ładowane z magazynu trwałości, zakładka jest wznawiana i przepływ pracy jest wykonywany.  
  
> [!WARNING]
> Jeśli SQL Server jest skonfigurowany do nasłuchiwania tylko w protokole nazwany potok, Host usługi przepływu pracy nie zostanie otwarty.  
  
## <a name="see-also"></a>Zobacz też

- [Usługi przepływu pracy](workflow-services.md)
- [Hostowanie usług przepływu pracy](hosting-workflow-services.md)
- [Punkt końcowy kontroli przepływu pracy](workflow-control-endpoint.md)
- [Instrukcje: konfigurowanie zachowania dotyczącego nieobsługiwanego wyjątku przepływu pracy przy użyciu klasy WorkflowServiceHost](config-workflow-unhandled-exception-workflowservicehost.md)
- [Tworzenie długo działającej usługi przepływu pracy](creating-a-long-running-workflow-service.md)
- [Trwałość przepływu pracy](../../windows-workflow-foundation/workflow-persistence.md)
