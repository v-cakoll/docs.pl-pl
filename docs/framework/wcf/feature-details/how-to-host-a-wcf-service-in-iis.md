---
title: 'Instrukcje: Hostowanie usługi WCF w programie IIS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b044b1c9-c1e5-4c9f-84d8-0f02f4537f8b
ms.openlocfilehash: 580b380a6c6349c6a4efa26e3eefe38bd660fa1b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184924"
---
# <a name="how-to-host-a-wcf-service-in-iis"></a>Instrukcje: Hostowanie usługi WCF w programie IIS
W tym temacie opisano podstawowe kroki wymagane do utworzenia usługi Windows Communication Foundation (WCF), która jest hostowana w internetowych usługach informacyjnych (IIS). W tym temacie założono, że użytkownik jest zaznajomiony z usługami IIS i jak używać narzędzia do zarządzania usługami IIS do tworzenia aplikacji usług IIS i zarządzania nimi. Aby uzyskać więcej informacji o usługach IIS, zobacz [Internetowe usługi informacyjne](https://www.iis.net/). Usługa WCF, która działa w środowisku usług IIS, w pełni wykorzystuje funkcje usług IIS, takie jak recykling procesów, bezczynne zamykanie systemu, monitorowanie kondycji procesu i aktywacja oparta na wiadomościach. Ta opcja hostingu wymaga prawidłowej konfiguracji usług IIS, ale nie wymaga, aby każdy kod hostingu był zapisywany jako część aplikacji. Hostingi iis można używać tylko z transportem HTTP.  
  
 Aby uzyskać więcej informacji o tym, jak WCF i ASP.NET współdziałają, zobacz [Usługi WCF i ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md). Aby uzyskać więcej informacji na temat konfigurowania zabezpieczeń, zobacz [Zabezpieczenia](../../../../docs/framework/wcf/feature-details/security.md).  
  
 Aby zapoznać się z kopią źródłową tego przykładu, zobacz [Hosting IIS przy użyciu kodu wbudowanego](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md).  
  
### <a name="to-create-a-service-hosted-by-iis"></a>Aby utworzyć usługę obsługiwaną przez usługi IIS  
  
1. Upewnij się, że usługi IIS są zainstalowane i uruchomione na komputerze. Aby uzyskać więcej informacji na temat instalowania i konfigurowania usługi IIS, zobacz [Instalowanie i konfigurowanie usługi IIS 7.0](https://docs.microsoft.com/iis/install/installing-iis-7/installing-necessary-iis-components-on-windows-vista)  
  
2. Utwórz nowy folder dla plików aplikacji o nazwie "IISHostedCalcService", upewnij się, że ASP.NET ma dostęp do zawartości folderu, a narzędzie do zarządzania usługami IIS służy do tworzenia nowej aplikacji usług IIS, która fizycznie znajduje się w tym katalogu aplikacji. Podczas tworzenia aliasu dla katalogu aplikacji użyj "IISHostedCalc".  
  
3. Utwórz nowy plik o nazwie "service.svc" w katalogu aplikacji. Edytuj ten plik, @ServiceHost dodając następujący element.  
  
   ```
   <%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService"%>
   ```  
  
4. Utwórz podkatalog App_Code w katalogu aplikacji.  
  
5. Utwórz plik kodu o nazwie Service.cs w podkatalogu App_Code.  
  
6. Dodaj następujące instrukcje do górnej części pliku Service.cs.  
  
    ```csharp  
    using System;  
    using System.ServiceModel;  
    ```  
  
7. Dodaj następującą deklarację obszaru nazw po using instrukcji.  
  
    ```csharp  
    namespace Microsoft.ServiceModel.Samples  
    {  
    }  
    ```  
  
8. Zdefiniuj umowę serwisową wewnątrz deklaracji obszaru nazw, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[c_HowTo_HostInIIS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#11)]
     [!code-vb[c_HowTo_HostInIIS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#11)]  
  
9. Zaimplementuj umowę serwisową po definicji umowy serwisowej, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[c_HowTo_HostInIIS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#12)]
     [!code-vb[c_HowTo_HostInIIS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#12)]  
  
10. Utwórz plik o nazwie "Web.config" w katalogu aplikacji i dodaj do pliku następujący kod konfiguracji. W czasie wykonywania WCF infrastruktury używa informacji do konstruowania punktu końcowego, który aplikacje klienckie mogą komunikować się z.  
  
     [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]
  
     W tym przykładzie jawnie określa punkty końcowe w pliku konfiguracji. Jeśli nie dodać żadnych punktów końcowych do usługi, środowisko wykonawcze dodaje domyślne punkty końcowe dla Ciebie. Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, powiązań i zachowań, zobacz [Uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
11. Aby upewnić się, że usługa jest obsługiwana poprawnie, otwórz wystąpienie programu Internet Explorer i przejdź do adresu URL usługi:`http://localhost/IISHostedCalc/Service.svc`  
  
## <a name="example"></a>Przykład  
 Poniżej znajduje się pełna lista kodu usługi kalkulatora hostowanego usług IIS.  
  
 [!code-csharp[C_HowTo_HostInIIS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#1)]
 [!code-vb[C_HowTo_HostInIIS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#1)]
 [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]  
  
## <a name="see-also"></a>Zobacz też

- [Hostowanie przez Internetowe usługi informacyjne](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)
- [Usługi hostingowe](../../../../docs/framework/wcf/hosting-services.md)
- [Usługi WCF i platforma ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)
- [Zabezpieczenia](../../../../docs/framework/wcf/feature-details/security.md)
- [Funkcje hostingu sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
