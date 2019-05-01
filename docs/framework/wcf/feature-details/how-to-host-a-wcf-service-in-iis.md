---
title: 'Instrukcje: hostowanie usługi WCF w usługach IIS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b044b1c9-c1e5-4c9f-84d8-0f02f4537f8b
ms.openlocfilehash: f106ce1bca67f8b88df0835496eea0b3297ac946
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000834"
---
# <a name="how-to-host-a-wcf-service-in-iis"></a>Instrukcje: hostowanie usługi WCF w usługach IIS
W tym temacie przedstawiono podstawowe kroki wymagane do utworzenia usługi Windows Communication Foundation (WCF), który znajduje się w Internet Information Services (IIS). W tym temacie przyjęto założenie, są zaznajomieni z usług IIS i dowiedzieć się, jak używać narzędzia do zarządzania usług IIS do tworzenia i obsługi aplikacji programu IIS. Aby uzyskać więcej informacji na temat usług IIS zobacz [Internetowe usługi informacyjne](https://go.microsoft.com/fwlink/?LinkId=132449). Usługi WCF, który jest uruchamiany w środowisku usług IIS wykorzystuje pełną funkcje usług IIS, takie jak odtwarzanie procesów, bezczynności zamykania, monitorowania kondycji procesu i aktywacja oparta na komunikatach. Ta opcja hostingu wymaga, aby poprawnie skonfigurować usługi IIS, ale nie wymaga się, że każdy kod hostingu zapisywane jako część aplikacji. Umożliwia hostowanie usług IIS tylko w przypadku transportu HTTP.  
  
 Aby uzyskać więcej informacji na temat usługi WCF i [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] wchodzić w interakcje, zobacz [usługi WCF i platforma ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md). Aby uzyskać więcej informacji na temat konfigurowania zabezpieczeń, zobacz [zabezpieczeń](../../../../docs/framework/wcf/feature-details/security.md).  
  
 Źródło kopię w tym przykładzie można zobaczyć [IIS hostingu przy użyciu kodu wbudowanego](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md).  
  
### <a name="to-create-a-service-hosted-by-iis"></a>Tworzenie usługi hostowanej przez Internetowe usługi informacyjne  
  
1. Upewnij się, czy program IIS jest zainstalowana i uruchomiona na komputerze. Aby uzyskać więcej informacji na temat instalowania i konfigurowania usług IIS zobacz [Instalowanie i konfigurowanie usług IIS 7.0](https://go.microsoft.com/fwlink/?LinkID=132128)  
  
2. Utwórz nowy folder na potrzeby plików aplikacji o nazwie "IISHostedCalcService", upewnij się, że [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ma dostęp do zawartości folderu i użyć narzędzia do zarządzania usług IIS, aby utworzyć nową aplikację usług IIS, która fizycznie znajduje się w tej aplikacji katalog. Podczas tworzenia alias do użytku w katalogu aplikacji "IISHostedCalc".  
  
3. Utwórz nowy plik o nazwie "service.svc" w katalogu aplikacji. Edytuj ten plik, dodając następujące @ServiceHost elementu.  
  
    ```  
    <%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService"%>  
    ```  
  
4. Utwórz podkatalog App_Code w katalogu aplikacji.  
  
5. Utwórz plik kodu o nazwie Service.cs w podkatalogu App_Code.  
  
6. Dodaj następujące za pomocą instrukcji na górze pliku Service.cs.  
  
    ```csharp  
    using System;  
    using System.ServiceModel;  
    ```  
  
7. Dodaj następującą deklarację przestrzeni nazw, gdy po użyciu instrukcji.  
  
    ```csharp  
    namespace Microsoft.ServiceModel.Samples  
    {  
    }  
    ```  
  
8. Definiowanie kontraktu usługi, wewnątrz deklaracji przestrzeni nazw, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[c_HowTo_HostInIIS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#11)]
     [!code-vb[c_HowTo_HostInIIS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#11)]  
  
9. Implementowanie kontraktu usługi, po usługę definicję kontraktu, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[c_HowTo_HostInIIS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#12)]
     [!code-vb[c_HowTo_HostInIIS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#12)]  
  
10. Utwórz plik o nazwie "Web.config" w katalogu aplikacji, a następnie dodaj następujący kod konfiguracji do pliku. W czasie wykonywania infrastruktura WCF używa tych informacji do utworzenia punktu końcowego, który aplikacje klienckie mogą się komunikować.  
  
     [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]      
  
     Ten przykład jawnie określa punkty końcowe w pliku konfiguracji. Jeśli nie dodasz żadnych punktów końcowych do usługi, środowiska uruchomieniowego dodaje domyślne punkty końcowe. Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, powiązania i zachowań, zobacz [uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
11. Aby upewnić się, że usługa jest hostowana poprawnie, otwórz wystąpienie programu Internet Explorer i przejdź do adresu URL usługi: `http://localhost/IISHostedCalc/Service.svc`  
  
## <a name="example"></a>Przykład  
 Poniżej znajduje się że kalkulatora usługi hostowanej pełną listę kod dla usług IIS.  
  
 [!code-csharp[C_HowTo_HostInIIS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#1)] 
 [!code-vb[C_HowTo_HostInIIS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#1)] 
 [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]  
  
## <a name="see-also"></a>Zobacz także

- [Hostowanie przez Internetowe usługi informacyjne](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)
- [Usługi hostingowe](../../../../docs/framework/wcf/hosting-services.md)
- [Usługi WCF i platforma ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)
- [Zabezpieczenia](../../../../docs/framework/wcf/feature-details/security.md)
- [Windows Server AppFabric funkcje hostingu](https://go.microsoft.com/fwlink/?LinkId=201276)
