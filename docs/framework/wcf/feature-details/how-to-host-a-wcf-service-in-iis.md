---
title: 'Instrukcje: Hostowanie usługi WCF w programie IIS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b044b1c9-c1e5-4c9f-84d8-0f02f4537f8b
ms.openlocfilehash: a1759434d259cdffe1dac6b19a6582bfb83784bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33492488"
---
# <a name="how-to-host-a-wcf-service-in-iis"></a>Instrukcje: Hostowanie usługi WCF w programie IIS
W tym temacie przedstawiono podstawowe czynności wymagane do utworzenia usługi Windows Communication Foundation (WCF), który znajduje się w Internet Information Services (IIS). W tym temacie założono zapoznali się z usługami IIS i zrozumieć, jak używać narzędzia zarządzania usług IIS do tworzenia i zarządzania aplikacjami usług IIS. Aby uzyskać więcej informacji na temat usług IIS zobacz [Internetowe usługi informacyjne](http://go.microsoft.com/fwlink/?LinkId=132449). Usługi WCF pobierającej jest uruchamiany w środowisku usług IIS w pełni korzystać z funkcji usług IIS, takie jak odtwarzanie procesów, bezczynności zamykania, monitorowanie kondycji procesów i aktywacji opartej na wiadomość. Ta opcja hostingu wymaga usług IIS zostać prawidłowo skonfigurowane, ale nie wymaga się, że każdy kod hostingu można zapisywać w ramach aplikacji. Można użyć tylko z transportem HTTP hostowanie usług IIS.  
  
 Aby uzyskać więcej informacji na temat usługi WCF i [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] interakcji, zobacz [usługi WCF i platformy ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md). Aby uzyskać więcej informacji na temat konfigurowania zabezpieczeń, zobacz [zabezpieczeń](../../../../docs/framework/wcf/feature-details/security.md).  
  
 Dla źródła kopię w tym przykładzie [IIS Hosting przy użyciu kodu wbudowanego](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md).  
  
### <a name="to-create-a-service-hosted-by-iis"></a>Tworzenie usługi hostowanej przez Internetowe usługi informacyjne  
  
1.  Upewnij się, że usługi IIS jest zainstalowana i uruchomiona na tym komputerze. Aby uzyskać więcej informacji na temat instalowania i konfigurowania usług IIS zobacz [Instalowanie i konfigurowanie usług IIS 7.0](http://go.microsoft.com/fwlink/?LinkID=132128)  
  
2.  Utwórz nowy folder o nazwie "IISHostedCalcService" plików aplikacji, upewnij się, że [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ma dostęp do zawartości folderu i narzędzia zarządzania usług IIS umożliwia utworzenie nowej aplikacji usług IIS, która jest fizycznie zlokalizowany w tej aplikacji katalog. Podczas tworzenia aliasu katalogu aplikacji do użytku "IISHostedCalc".  
  
3.  Utwórz nowy plik o nazwie "service.svc" w katalogu aplikacji. Edytowanie tego pliku przez dodanie poniższego @ServiceHost elementu.  
  
    ```  
    <%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService"%>  
    ```  
  
4.  Utwórz App_Code podkatalogu w katalogu aplikacji.  
  
5.  Utwórz plik kodu o nazwie Service.cs w podkatalogu App_Code.  
  
6.  Dodaj następujące instrukcje using do początku pliku Service.cs.  
  
    ```csharp  
    using System;  
    using System.ServiceModel;  
    ```  
  
7.  Dodaj następujące deklaracji przestrzeni nazw przy użyciu instrukcji.  
  
    ```csharp  
    namespace Microsoft.ServiceModel.Samples  
    {  
    }  
    ```  
  
8.  Definiowanie kontraktu usługi wewnątrz deklaracji przestrzeni nazw, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[c_HowTo_HostInIIS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#11)]
     [!code-vb[c_HowTo_HostInIIS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#11)]  
  
9. Implementowanie kontraktu usługi, po usługi definicja kontraktu, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[c_HowTo_HostInIIS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#12)]
     [!code-vb[c_HowTo_HostInIIS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#12)]  
  
10. Utwórz plik o nazwie "Web.config" w katalogu aplikacji i Dodaj następujący kod konfiguracji do pliku. W czasie wykonywania infrastruktura WCF używa tych informacji do utworzenia punktu końcowego, który aplikacje klienckie mogą komunikować się z.  
  
     [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]      
  
     W tym przykładzie jawnie określa punkty końcowe w pliku konfiguracji. Jeśli nie dodawaj żadnych punktów końcowych do usługi, środowisko uruchomieniowe dodaje domyślne punkty końcowe. Aby uzyskać więcej informacji o domyślnych punktów końcowych, powiązania i zachowania, zobacz [uproszczony konfiguracji](../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
11. Aby upewnić się, że usługa działa prawidłowo, otwórz wystąpienie programu Internet Explorer i przejdź do adresu URL usługi: `http://localhost/IISHostedCalc/Service.svc`  
  
## <a name="example"></a>Przykład  
 Poniżej znajduje się, że Kalkulator usługi hostowanej pełną listę kod dla usług IIS.  
  
 [!code-csharp[C_HowTo_HostInIIS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#1)] 
 [!code-vb[C_HowTo_HostInIIS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#1)] 
 [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]  
  
## <a name="see-also"></a>Zobacz też  
 [Hostowanie przez Internetowe usługi informacyjne](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)  
 [Usługi hostingowe](../../../../docs/framework/wcf/hosting-services.md)  
 [Usługi WCF i platforma ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)  
 [Zabezpieczenia](../../../../docs/framework/wcf/feature-details/security.md)  
 [Windows Server AppFabric funkcje hostingu](http://go.microsoft.com/fwlink/?LinkId=201276)
