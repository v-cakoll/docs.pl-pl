---
title: 'Instrukcje: hostowanie usługi WCF w usłudze WAS'
ms.date: 03/30/2017
ms.assetid: 9e3e213e-2dce-4f98-81a3-f62f44caeb54
ms.openlocfilehash: 157c18d1640ccf1a61f871e5e3e9fef70b6a7e79
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59326505"
---
# <a name="how-to-host-a-wcf-service-in-was"></a>Instrukcje: hostowanie usługi WCF w usłudze WAS
W tym temacie wymieniono podstawowe kroki wymagane do utworzenia usługi aktywacji procesów Windows (znany także jako WAS) hostowanych usług Windows Communication Foundation (WCF). ZOSTAŁA nowa usługa aktywacji procesów, która jest uogólnienie funkcji Internet Information Services (IIS), które działają z protokołami protokołu HTTP. Usługi WCF używa interfejsu karty odbiornika do komunikowania się żądania aktywacji, które są odbierane za pośrednictwem protokołów innych niż HTTP obsługiwane przez architekturę WCF, takich jak TCP, nazwanych potoków i usługi kolejkowania komunikatów.  
  
 Ta opcja hostingu wymaga składników aktywacji WAS są prawidłowo zainstalowane i skonfigurowane, ale nie wymaga hostowania kodu do zapisania jako część aplikacji. Aby uzyskać więcej informacji o instalowaniu i konfigurowaniu WAS, zobacz [jak: Instalowanie i konfigurowanie składników aktywacji programu WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).  
  
> [!WARNING]
>  BYŁA aktywacja nie jest obsługiwana, jeśli potok przetwarzania żądania serwer sieci web jest ustawiany w trybie klasycznym. Potok przetwarzania żądania serwer sieci web musi być równa w trybie zintegrowanym, w przypadku aktywacji WAS do użycia.  
  
 Gdy usługa WCF jest hostowana w WAS, standardowe powiązania są używane w zwykły sposób. Jednak przy użyciu <xref:System.ServiceModel.NetTcpBinding> i <xref:System.ServiceModel.NetNamedPipeBinding> do skonfigurowania usługi hostowanej WAS, muszą być spełnione ograniczenie. Korzystając z różnych punktów końcowych tego samego transportu, ustawienia powiązania muszą odpowiadać na następujące siedem właściwości:  
  
-   ConnectionBufferSize  
  
-   ChannelInitializationTimeout  
  
-   MaxPendingConnections  
  
-   MaxOutputDelay  
  
-   MaxPendingAccepts  
  
-   ConnectionPoolSettings.IdleTimeout  
  
-   ConnectionPoolSettings.MaxOutboundConnectionsPerEndpoint  
  
 W przeciwnym razie punkt końcowy, który jest inicjowany najpierw zawsze określi wartości tych właściwości i punktów końcowych, dodane później throw <xref:System.ServiceModel.ServiceActivationException> Jeśli te ustawienia są niezgodne.  
  
 Źródło kopię w tym przykładzie można zobaczyć [Aktywacja TCP](../../../../docs/framework/wcf/samples/tcp-activation.md).  
  
### <a name="to-create-a-basic-service-hosted-by-was"></a>Aby utworzyć podstawowej usługi hostowane przez WAS  
  
1. Definiowanie kontraktu usługi dla typu usługi.  
  
     [!code-csharp[C_HowTo_HostInWAS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1121)]  
  
2. Implementowanie kontraktu usługi, w klasie usługi. Należy pamiętać, że wewnątrz implementacji usługi nie określono adresu lub powiązania informacji. Ponadto kod nie ma do zapisania, aby pobrać te informacje z pliku konfiguracji.  
  
     [!code-csharp[C_HowTo_HostInWAS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1122)]  
  
3. Utwórz plik Web.config w celu zdefiniowania <xref:System.ServiceModel.NetTcpBinding> powiązania, który będzie używany przez `CalculatorService` punktów końcowych.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>  
        <bindings>  
          <netTcpBinding>  
            <binding portSharingEnabled="true">  
              <security mode="None" />  
            </binding>  
          </netTcpBinding>  
        </bindings>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
4. Utwórz plik Service.svc, który zawiera następujący kod.  
  
    ```  
    <%@ServiceHost language=c# Service="CalculatorService" %>   
    ```  
  
5. Umieść plik Service.svc w wirtualny katalog IIS.  
  
### <a name="to-create-a-client-to-use-the-service"></a>Można utworzyć klienta do korzystania z usługi  
  
1. Użyj [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) z poziomu wiersza polecenia, aby wygenerować kod z metadanych usługi.  
  
    ```  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2. Klient, który jest generowany zawiera `ICalculator` Interfejs definiujący kontrakt usługi, które muszą spełniać implementacji klienta.  
  
     [!code-csharp[C_HowTo_HostInWAS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1221)]  
  
3. Aplikacja wygenerowanego klienta zawiera również implementację `ClientCalculator`. Należy pamiętać, informacje dotyczące adresów i powiązania nie dowolnym określona wewnątrz implementacji usługi. Ponadto kod nie ma do zapisania, aby pobrać te informacje z pliku konfiguracji.  
  
     [!code-csharp[C_HowTo_HostInWAS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1222)]  
  
4. Konfiguracja klienta, który używa <xref:System.ServiceModel.NetTcpBinding> również jest generowany przez Svcutil.exe. Ten plik powinien zostać nazwany w pliku App.config, korzystając z programu Visual Studio.  
  
     [!code-xml[C_HowTo_HostInWAS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/common/app.config#2211)]   
  
5. Utwórz wystąpienie obiektu `ClientCalculator` w aplikacji, a następnie wywołać operacji usługi.  
  
     [!code-csharp[C_HowTo_HostInWAS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1223)]  
  
6. Kompilowanie i uruchamianie klienta.  
  
## <a name="see-also"></a>Zobacz także

- [Aktywacja TCP](../../../../docs/framework/wcf/samples/tcp-activation.md)
- [Windows Server AppFabric funkcje hostingu](https://go.microsoft.com/fwlink/?LinkId=201276)
