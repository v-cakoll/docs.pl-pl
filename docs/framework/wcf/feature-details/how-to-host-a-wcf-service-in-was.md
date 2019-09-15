---
title: 'Instrukcje: hostowanie usługi WCF w usłudze WAS'
ms.date: 03/30/2017
ms.assetid: 9e3e213e-2dce-4f98-81a3-f62f44caeb54
ms.openlocfilehash: b6d3ace054260de1ca649fbf4bd54156bbea24ce
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972204"
---
# <a name="how-to-host-a-wcf-service-in-was"></a>Instrukcje: hostowanie usługi WCF w usłudze WAS
W tym temacie przedstawiono podstawowe kroki wymagane do utworzenia usług aktywacji procesów systemu Windows (znanych także jako usługa Windows Communication Foundation hostowanej usługi WCF). BYŁA to nowa usługa aktywacji procesów, która jest generalizacją funkcji Internet Information Services (IIS), które działają z protokołami transportu innym niż HTTP. Funkcja WCF używa interfejsu adaptera odbiornika do przekazywania żądań aktywacji odbieranych za pośrednictwem protokołów innych niż HTTP obsługiwanych przez program WCF, takich jak TCP, nazwane potoki i kolejkowanie komunikatów.  
  
 Ta opcja hostingu wymaga, aby składniki aktywacji zostały prawidłowo zainstalowane i skonfigurowane, ale nie wymagają zapisywania kodu hostingu jako części aplikacji. Aby uzyskać więcej informacji na temat instalowania i konfigurowania programu [, zobacz How to: Zainstaluj i Skonfiguruj składniki](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)aktywacji WCF.  
  
> [!WARNING]
> Aktywacja nie jest obsługiwana, jeśli potok przetwarzania żądań serwera sieci Web jest ustawiony na tryb klasyczny. Jeśli aktywacja ma być używana, potok przetwarzania żądań serwera sieci Web musi być ustawiony na tryb zintegrowany.  
  
 Gdy usługa WCF jest hostowana w programie, standardowe powiązania są używane w zwykły sposób. Jednak w przypadku korzystania z <xref:System.ServiceModel.NetTcpBinding> <xref:System.ServiceModel.NetNamedPipeBinding> i w celu skonfigurowania usługi hostowanej należy spełnić ograniczenie. Gdy różne punkty końcowe używają tego samego transportu, ustawienia powiązania muszą być zgodne z następującymi siedem właściwości:  
  
- ConnectionBufferSize  
  
- ChannelInitializationTimeout  
  
- MaxPendingConnections  
  
- MaxOutputDelay  
  
- MaxPendingAccepts  
  
- ConnectionPoolSettings.IdleTimeout  
  
- ConnectionPoolSettings.MaxOutboundConnectionsPerEndpoint  
  
 W przeciwnym razie punkt końcowy, który jest inicjowany najpierw zawsze określa wartości tych właściwości, i punkty końcowe dodane później <xref:System.ServiceModel.ServiceActivationException> throw, jeśli nie są zgodne z tymi ustawieniami.  
  
 Aby uzyskać kopię źródła tego przykładu, zobacz [Aktywacja protokołu TCP](../../../../docs/framework/wcf/samples/tcp-activation.md).  
  
### <a name="to-create-a-basic-service-hosted-by-was"></a>Aby utworzyć podstawową usługę hostowaną przez program:  
  
1. Zdefiniuj kontrakt usługi dla typu usługi.  
  
     [!code-csharp[C_HowTo_HostInWAS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1121)]  
  
2. Zaimplementuj kontrakt usługi w klasie usługi. Należy zauważyć, że informacje o adresie lub powiązaniu nie są określone w implementacji usługi. Ponadto kod nie musi być zapisany, aby można było pobrać te informacje z pliku konfiguracyjnego.  
  
     [!code-csharp[C_HowTo_HostInWAS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1122)]  
  
3. Utwórz plik Web. config, <xref:System.ServiceModel.NetTcpBinding> aby zdefiniować powiązanie, które ma być używane `CalculatorService` przez punkty końcowe.  
  
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
  
4. Utwórz plik Service. svc zawierający poniższy kod.  
  
   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```
  
5. Umieść plik Service. svc w katalogu wirtualnym usług IIS.  
  
### <a name="to-create-a-client-to-use-the-service"></a>Aby utworzyć klienta do korzystania z usługi  
  
1. Użyj [Narzędzia do obsługi metadanych ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) z wiersza polecenia, aby wygenerować kod na podstawie metadanych usługi.  
  
    ```console
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
    ```  
  
2. Wygenerowany klient zawiera `ICalculator` interfejs, który definiuje kontrakt usługi, który musi spełniać implementacja klienta.  
  
     [!code-csharp[C_HowTo_HostInWAS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1221)]  
  
3. Wygenerowana aplikacja kliencka zawiera również implementację `ClientCalculator`programu. Należy zauważyć, że informacje o adresie i powiązaniu nie są określone w dowolnym miejscu w implementacji usługi. Ponadto kod nie musi być zapisany, aby można było pobrać te informacje z pliku konfiguracyjnego.  
  
     [!code-csharp[C_HowTo_HostInWAS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1222)]  
  
4. Konfiguracja klienta korzystającego z programu <xref:System.ServiceModel.NetTcpBinding> jest również generowana przez Svcutil. exe. Ten plik powinien mieć nazwę w pliku App. config w przypadku korzystania z programu Visual Studio.  
  
     [!code-xml[C_HowTo_HostInWAS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/common/app.config#2211)]   
  
5. Utwórz wystąpienie `ClientCalculator` elementu w aplikacji, a następnie Wywołaj operacje usługi.  
  
     [!code-csharp[C_HowTo_HostInWAS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1223)]  
  
6. Kompiluj i uruchom klienta.  
  
## <a name="see-also"></a>Zobacz także

- [Aktywacja TCP](../../../../docs/framework/wcf/samples/tcp-activation.md)
- [Funkcje hostingu sieci szkieletowej aplikacji systemu Windows Server](https://go.microsoft.com/fwlink/?LinkId=201276)
