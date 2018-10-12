---
title: 'Instrukcje: Konfigurowanie usługi Windows Communication Foundation na potrzeby współużytkowania portów'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6400bc71-a858-4ac2-8d5a-caa72d3b5482
ms.openlocfilehash: 19f61e6e38a5eeb477833b0d5ea94c1b1a8447b4
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2018
ms.locfileid: "49121921"
---
# <a name="how-to-configure-a-windows-communication-foundation-service-to-use-port-sharing"></a>Instrukcje: Konfigurowanie usługi Windows Communication Foundation na potrzeby współużytkowania portów
Najprostszym sposobem na korzystanie z portu net.tcp:// udostępniania w aplikacji Windows Communication Foundation (WCF) jest do udostępnienia usługi za pomocą <xref:System.ServiceModel.NetTcpBinding>.  
  
 Zapewnia to powiązanie <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> właściwość, która określa, czy usługi są skonfigurowane z tym powiązaniem włączone jest udostępnianie portów net.tcp://.  
  
 Poniższa procedura przedstawia sposób użycia <xref:System.ServiceModel.NetTcpBinding> klasy, aby najpierw otwórz punkt końcowy w net.tcp://localhost/MyService identyfikator (URI), w kodzie, a następnie za pomocą elementów konfiguracji.  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-code"></a>Aby włączyć port net.tcp:// udostępnianie na NetTcpBinding w kodzie  
  
1.  Tworzenie usługi, aby zaimplementować kontrakt o nazwie `IMyService` i nadać mu `MyService`,.  
  
     [!code-csharp[c_ConfigurePortSharing#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#1)]
     [!code-vb[c_ConfigurePortSharing#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#1)]  
  
2.  Utwórz wystąpienie obiektu <xref:System.ServiceModel.NetTcpBinding> klasy i ustaw <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> właściwość `true`.  
  
     [!code-csharp[c_ConfigurePortSharing#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#2)]
     [!code-vb[c_ConfigurePortSharing#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#2)]  
  
3.  Tworzenie <xref:System.ServiceModel.ServiceHost> i Dodaj punkt końcowy usługi do niej uzyskać `MyService` używający portu włączone udostępnianie <xref:System.ServiceModel.NetTcpBinding> i że nasłuchuje w punkcie końcowym adresu URI "net.tcp://localhost/MyService".  
  
     [!code-csharp[c_ConfigurePortSharing#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#3)]
     [!code-vb[c_ConfigurePortSharing#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#3)]  
  
    > [!NOTE]
    >  Ten przykład używa domyślnego portu TCP 808, ponieważ adres punktu końcowego identyfikatora URI nie określa inny numer portu. Ponieważ jawnie powiązania transportu włączone udostępnianie portów, tej usługi można udostępniać port 808 z innymi usługami w innych procesów. Jeśli Udostępnianie portów nie zezwolono na innej aplikacji zostały już używa portu 808, ta usługa będzie zgłaszają <xref:System.ServiceModel.AddressAlreadyInUseException> kiedy został otwarty.  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-configuration"></a>Aby włączyć port net.tcp:// udostępnianie na NetTcpBinding w konfiguracji  
  
1.  Poniższy przykład pokazuje, jak włączyć Udostępnianie portów i dodać punktu końcowego usługi za pomocą elementów konfiguracji.  
  
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
* [Współużytkowanie portów w składniku Net.TCP](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)  
* [Instrukcje: włączanie usługi współużytkowania portów Net.TCP](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md)
