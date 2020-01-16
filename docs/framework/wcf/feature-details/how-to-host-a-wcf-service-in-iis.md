---
title: 'Instrukcje: Hostowanie usługi WCF w programie IIS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b044b1c9-c1e5-4c9f-84d8-0f02f4537f8b
ms.openlocfilehash: 204aa9ce86e8798c1f2d8de664f53ad2a86555de
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964789"
---
# <a name="how-to-host-a-wcf-service-in-iis"></a>Instrukcje: Hostowanie usługi WCF w programie IIS
W tym temacie przedstawiono podstawowe kroki wymagane do utworzenia usługi Windows Communication Foundation (WCF), która jest hostowana w usłudze Internet Information Services (IIS). W tym temacie założono, że znasz usługi IIS i wiesz, jak używać narzędzia do zarządzania usługami IIS do tworzenia aplikacji usług IIS i zarządzania nimi. Aby uzyskać więcej informacji na temat usług IIS, zobacz [Internet Information Services](https://www.iis.net/). Usługa WCF działająca w środowisku usług IIS pełni funkcję usług IIS, taką jak odtwarzanie procesów, zamykanie bezczynności, monitorowanie kondycji procesu i Aktywacja oparta na komunikatach. Ta opcja hostingu wymaga poprawnego skonfigurowania usług IIS, ale nie wymaga, aby żaden kod hostingu był zapisywana jako część aplikacji. Hostingu usług IIS można używać tylko z transportem HTTP.  
  
 Aby uzyskać więcej informacji o tym, jak działa WCF i ASP.NET, zobacz [usługi WCF i ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md). Aby uzyskać więcej informacji o konfigurowaniu zabezpieczeń, zobacz [zabezpieczenia](../../../../docs/framework/wcf/feature-details/security.md).  
  
 Aby uzyskać kopię źródła tego przykładu, zobacz [hosting usług IIS przy użyciu kodu wbudowanego](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md).  
  
### <a name="to-create-a-service-hosted-by-iis"></a>Aby utworzyć usługę hostowaną przez usługi IIS  
  
1. Upewnij się, że usługi IIS są zainstalowane i uruchomione na komputerze. Aby uzyskać więcej informacji na temat instalowania i konfigurowania usług IIS, zobacz [Instalowanie i Konfigurowanie usług iis 7,0](https://docs.microsoft.com/iis/install/installing-iis-7/installing-necessary-iis-components-on-windows-vista)  
  
2. Utwórz nowy folder dla plików aplikacji o nazwie "IISHostedCalcService", upewnij się, że ASP.NET ma dostęp do zawartości folderu, a następnie użyj narzędzia do zarządzania usługami IIS, aby utworzyć nową aplikację usług IIS, która znajduje się fizycznie w tym katalogu aplikacji. Podczas tworzenia aliasu dla katalogu aplikacji użyj polecenia "IISHostedCalc".  
  
3. Utwórz nowy plik o nazwie "Service. svc" w katalogu aplikacji. Edytuj ten plik, dodając następujący @ServiceHost elementu.  
  
   ```
   <%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService"%>
   ```  
  
4. Utwórz podkatalog App_Code w katalogu aplikacji.  
  
5. Utwórz plik kodu o nazwie Service.cs w podkatalogu App_Code.  
  
6. Dodaj następujące instrukcje using na początku pliku Service.cs.  
  
    ```csharp  
    using System;  
    using System.ServiceModel;  
    ```  
  
7. Dodaj następującą deklarację przestrzeni nazw po instrukcjach using.  
  
    ```csharp  
    namespace Microsoft.ServiceModel.Samples  
    {  
    }  
    ```  
  
8. Zdefiniuj kontrakt usługi w deklaracji przestrzeni nazw, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[c_HowTo_HostInIIS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#11)]
     [!code-vb[c_HowTo_HostInIIS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#11)]  
  
9. Zaimplementuj kontrakt usługi po definicji kontraktu usługi, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[c_HowTo_HostInIIS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#12)]
     [!code-vb[c_HowTo_HostInIIS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#12)]  
  
10. Utwórz plik o nazwie "Web. config" w katalogu aplikacji i Dodaj następujący kod konfiguracyjny do pliku. W czasie wykonywania Infrastruktura WCF używa tych informacji do konstruowania punktu końcowego, z którym mogą komunikować się aplikacje klienckie.  
  
     [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]      
  
     Ten przykład jawnie określa punkty końcowe w pliku konfiguracji. Jeśli nie dodasz żadnych punktów końcowych do usługi, środowisko uruchomieniowe doda domyślne punkty końcowe. Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, powiązań i zachowań, zobacz [uproszczoną konfigurację](../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczoną konfigurację dla usług WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
11. Aby upewnić się, że usługa jest hostowana prawidłowo, Otwórz wystąpienie programu Internet Explorer i przejdź do adresu URL usługi: `http://localhost/IISHostedCalc/Service.svc`  
  
## <a name="example"></a>Przykład  
 Poniżej znajduje się kompletna lista kodu dla usługi hostowanego kalkulatora usług IIS.  
  
 [!code-csharp[C_HowTo_HostInIIS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#1)] 
 [!code-vb[C_HowTo_HostInIIS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#1)] 
 [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]  
  
## <a name="see-also"></a>Zobacz także

- [Hostowanie przez Internetowe usługi informacyjne](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)
- [Usługi hostingowe](../../../../docs/framework/wcf/hosting-services.md)
- [Usługi WCF i platforma ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)
- [Zabezpieczenia](../../../../docs/framework/wcf/feature-details/security.md)
- [Funkcje hostingu sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
