---
title: 'Instrukcje: Konfigurowanie usługi Windows Communication Foundation na potrzeby współużytkowania portów'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6400bc71-a858-4ac2-8d5a-caa72d3b5482
ms.openlocfilehash: cd8d76137ac195e452a7d66fb6ddbeda405a922f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185089"
---
# <a name="how-to-configure-a-windows-communication-foundation-service-to-use-port-sharing"></a>Instrukcje: Konfigurowanie usługi Windows Communication Foundation na potrzeby współużytkowania portów
Najprostszym sposobem użycia net.tcp:// udostępniania portów w aplikacji Windows Communication Foundation (WCF) jest udostępnienie usługi przy użyciu <xref:System.ServiceModel.NetTcpBinding>pliku .  
  
 To powiązanie <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> zawiera właściwość, która kontroluje, czy net.tcp:// udostępnianie portów jest włączone dla usługi skonfigurowane z tym powiązaniem.  
  
 Poniższa procedura pokazuje, <xref:System.ServiceModel.NetTcpBinding> jak użyć klasy, aby otworzyć punkt końcowy w jednolity identyfikator zasobu (URI) net.tcp://localhost/MyService, najpierw w kodzie, a następnie przy użyciu elementów konfiguracji.  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-code"></a>Aby włączyć udostępnianie portów net.tcp:// w kodzie NetTcpBinding  
  
1. Utwórz usługę, aby `IMyService` zaimplementować kontrakt o nazwie i wywołać go `MyService`, .  
  
     [!code-csharp[c_ConfigurePortSharing#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#1)]
     [!code-vb[c_ConfigurePortSharing#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#1)]  
  
2. Utwórz wystąpienie <xref:System.ServiceModel.NetTcpBinding> klasy i <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> ustaw `true`właściwość na .  
  
     [!code-csharp[c_ConfigurePortSharing#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#2)]
     [!code-vb[c_ConfigurePortSharing#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#2)]  
  
3. Utwórz <xref:System.ServiceModel.ServiceHost> i dodaj do niego `MyService` punkt końcowy usługi, który <xref:System.ServiceModel.NetTcpBinding> używa włączonego udostępniania portu i nasłuchuje w adresie końcowym URI "net.tcp://localhost/MyService".  
  
     [!code-csharp[c_ConfigurePortSharing#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#3)]
     [!code-vb[c_ConfigurePortSharing#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#3)]  
  
    > [!NOTE]
    > W tym przykładzie użyto domyślnego portu TCP 808, ponieważ identyfikator URI adresu punktu końcowego nie określa innego numeru portu. Ponieważ udostępnianie portów jest jawnie włączone w powiązaniu transportu, ta usługa może współużytkować port 808 innym usługom w innych procesach. Jeśli udostępnianie portów nie było dozwolone, a inna aplikacja już używała <xref:System.ServiceModel.AddressAlreadyInUseException> portu 808, ta usługa zgłaszałaby, kiedy została otwarta.  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-configuration"></a>Aby włączyć udostępnianie portów net.tcp:// w konfiguracji NetTcpBinding  
  
1. W poniższym przykładzie pokazano, jak włączyć udostępnianie portów i dodać punkt końcowy usługi przy użyciu elementów konfiguracji.  
  
```xml  
<system.serviceModel>  
  <bindings>  
    <netTcpBinding name="portSharingBinding"
                   portSharingEnabled="true" />  
  </bindings>  
  <services>  
    <service name="MyService">  
        <endpoint address="net.tcp://localhost/MyService"  
                  binding="netTcpBinding"  
                  contract="IMyService"  
                  bindingConfiguration="portSharingBinding" />  
    </service>  
  </services>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a>Zobacz też

- [Współużytkowanie portów w składniku Net.TCP](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)
- [Instrukcje: włączanie usługi współużytkowania portów Net.TCP](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md)
