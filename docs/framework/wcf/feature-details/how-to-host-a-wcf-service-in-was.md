---
title: 'Instrukcje: Hostowanie usługi WCF w usłudze WAS'
ms.date: 03/30/2017
ms.assetid: 9e3e213e-2dce-4f98-81a3-f62f44caeb54
ms.openlocfilehash: 823c3b8452a3fd1c95758d2d09a9effdf02075c8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184914"
---
# <a name="how-to-host-a-wcf-service-in-was"></a>Instrukcje: Hostowanie usługi WCF w usłudze WAS
W tym temacie opisano podstawowe kroki wymagane do utworzenia usługi aktywacji procesów systemu Windows (znanej również jako WAS) hostowanej w usłudze Windows Communication Foundation (WCF). WAS to nowa usługa aktywacji procesu, która jest uogólnienie funkcji internetowych usług informacyjnych (IIS), które działają z protokołami transportu innych niż HTTP. WCF używa interfejsu karty odbiornika do przekazywania żądań aktywacji, które są odbierane za pośrednictwem protokołów innych niż HTTP obsługiwanych przez WCF, takich jak TCP, nazwane potoki i Usługi kolejkowania wiadomości.  
  
 Ta opcja hostingu wymaga, aby składniki aktywacji WAS były poprawnie zainstalowane i skonfigurowane, ale nie wymaga żadnego kodu hostingu do zapisania jako część aplikacji. Aby uzyskać więcej informacji na temat instalowania i konfigurowania usługi WAS, zobacz [Jak: Instalowanie i konfigurowanie składników aktywacji WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).  
  
> [!WARNING]
> Aktywacja usługi WAS nie jest obsługiwana, jeśli potok przetwarzania żądań serwera sieci web jest ustawiony na tryb klasyczny. Potok przetwarzania żądań serwera sieci web musi być ustawiony na tryb zintegrowany, jeśli ma być używana aktywacja WAS.  
  
 Gdy usługa WCF jest hostowana wsłudze WAS, standardowe powiązania są używane w zwykły sposób. Jednak podczas korzystania <xref:System.ServiceModel.NetTcpBinding> z <xref:System.ServiceModel.NetNamedPipeBinding> i do konfigurowania usługi hostowane przez USŁUGI, musi być spełnione ograniczenie. Gdy różne punkty końcowe używają tego samego transportu, ustawienia powiązania muszą być zgodne z następującymi siedmioma właściwościami:  
  
- Rozmiar bufora połączenia  
  
- Limit czasu na kanały  
  
- Maxpendingconnections  
  
- MaxOutputDelay (MaxOutputDelay)  
  
- Maxpendingaccepts  
  
- ConnectionPoolSettings.IdleTimeout  
  
- ConnectionPoolSettings.MaxOutboundConnectionsPerEndpoint  
  
 W przeciwnym razie punkt końcowy, który jest inicjowany najpierw zawsze określa wartości <xref:System.ServiceModel.ServiceActivationException> tych właściwości, a punkty końcowe dodane później zgłosić, jeśli nie pasują do tych ustawień.  
  
 Aby zapoznać się z kopią źródłową tego przykładu, zobacz [Aktywacja TCP](../../../../docs/framework/wcf/samples/tcp-activation.md).  
  
### <a name="to-create-a-basic-service-hosted-by-was"></a>Aby utworzyć podstawową usługę obsługiwaną przez usługę WAS  
  
1. Zdefiniuj umowę serwisową dla typu usługi.  
  
     [!code-csharp[C_HowTo_HostInWAS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1121)]  
  
2. Zaimplementuj umowę serwisową w klasie usługi. Należy zauważyć, że adres lub powiązanie informacje nie jest określony wewnątrz implementacji usługi. Ponadto kod nie musi być zapisywany, aby pobrać te informacje z pliku konfiguracji.  
  
     [!code-csharp[C_HowTo_HostInWAS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1122)]  
  
3. Utwórz plik Web.config, <xref:System.ServiceModel.NetTcpBinding> aby zdefiniować `CalculatorService` powiązanie, które ma być używane przez punkty końcowe.  
  
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
  
4. Utwórz plik Service.svc zawierający następujący kod.  
  
   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```
  
5. Umieść plik Service.svc w katalogu wirtualnym usług IIS.  
  
### <a name="to-create-a-client-to-use-the-service"></a>Aby utworzyć klienta do korzystania z usługi  
  
1. Użyj [narzędzia narzędzia metadanych ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) z wiersza polecenia, aby wygenerować kod z metadanych usługi.  
  
    ```console
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
    ```  
  
2. Klient, który jest `ICalculator` generowany zawiera interfejs, który definiuje umowy serwisowej, że implementacja klienta musi spełniać.  
  
     [!code-csharp[C_HowTo_HostInWAS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1221)]  
  
3. Wygenerowana aplikacja kliencka zawiera `ClientCalculator`również implementację pliku . Należy zauważyć, że adres i informacje o powiązaniach nie jest określony w dowolnym miejscu wewnątrz implementacji usługi. Ponadto kod nie musi być zapisywany, aby pobrać te informacje z pliku konfiguracji.  
  
     [!code-csharp[C_HowTo_HostInWAS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1222)]  
  
4. Konfiguracja dla klienta, który <xref:System.ServiceModel.NetTcpBinding> używa jest również generowany przez Svcutil.exe. Ten plik powinien być nazwany w pliku App.config podczas korzystania z programu Visual Studio.  
  
     [!code-xml[C_HowTo_HostInWAS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/common/app.config#2211)]
  
5. Utwórz wystąpienie `ClientCalculator` w aplikacji, a następnie wywołaj operacje usługi.  
  
     [!code-csharp[C_HowTo_HostInWAS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1223)]  
  
6. Skompiluj i uruchom klienta.  
  
## <a name="see-also"></a>Zobacz też

- [Aktywacja TCP](../../../../docs/framework/wcf/samples/tcp-activation.md)
- [Funkcje hostingu sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
