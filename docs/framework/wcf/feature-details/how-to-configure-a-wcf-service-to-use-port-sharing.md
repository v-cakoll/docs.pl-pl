---
title: 'Instrukcje: Konfigurowanie usługi Windows Communication Foundation na potrzeby współużytkowania portów'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6400bc71-a858-4ac2-8d5a-caa72d3b5482
ms.openlocfilehash: 0a3aca2bac546c9142137afc025133bc1154ff90
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33495245"
---
# <a name="how-to-configure-a-windows-communication-foundation-service-to-use-port-sharing"></a>Instrukcje: Konfigurowanie usługi Windows Communication Foundation na potrzeby współużytkowania portów
Najprostszym sposobem, aby używał portu net.tcp:// udostępnianie w aplikacji Windows Communication Foundation (WCF) jest do udostępnienia usługi za pomocą <xref:System.ServiceModel.NetTcpBinding>.  
  
 Zapewnia to powiązanie <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> właściwość, która określa, czy włączone jest udostępnianie portów net.tcp:// usługi są skonfigurowane dla tego wiązania.  
  
 Poniższa procedura przedstawia sposób użycia <xref:System.ServiceModel.NetTcpBinding> klasę, aby najpierw otwórz punkt końcowy pod net.tcp://localhost/MyService identyfikator URI (Uniform Resource) w kodzie, a następnie za pomocą elementów konfiguracji.  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-code"></a>Aby włączyć port net.tcp:// udostępniania NetTcpBinding w kodzie  
  
1.  Tworzenie usługi do implementowania kontraktu o nazwie `IMyService` i nadaj mu `MyService`,.  
  
     [!code-csharp[c_ConfigurePortSharing#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#1)]
     [!code-vb[c_ConfigurePortSharing#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#1)]  
  
2.  Utwórz wystąpienie <xref:System.ServiceModel.NetTcpBinding> klasy i ustaw <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> właściwości `true`.  
  
     [!code-csharp[c_ConfigurePortSharing#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#2)]
     [!code-vb[c_ConfigurePortSharing#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#2)]  
  
3.  Utwórz <xref:System.ServiceModel.ServiceHost> i Dodaj do niej dla punktu końcowego usługi `MyService` używającej portu włączone udostępnianie <xref:System.ServiceModel.NetTcpBinding> i że odbiera w punkcie końcowym adresu URI "net.tcp://localhost/MyService".  
  
     [!code-csharp[c_ConfigurePortSharing#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#3)]
     [!code-vb[c_ConfigurePortSharing#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#3)]  
  
    > [!NOTE]
    >  W tym przykładzie używa domyślnego portu TCP 808, ponieważ adres URI punktu końcowego nie określa inny numer portu. Ponieważ jawnie powiązania transportu włączone udostępnianie portów, tej usługi można udostępniać port 808 z innymi usługami w innych procesów. Jeśli inna aplikacja była już używa portu 808 Udostępnianie portów są niedozwolone, tej usługi spowoduje zgłoszenie <xref:System.ServiceModel.AddressAlreadyInUseException> kiedy został otwarty.  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-configuration"></a>Aby włączyć net.tcp:// udostępniania na NetTcpBinding w konfiguracji portów  
  
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
 [Współużytkowanie portów w składniku Net.TCP](http://msdn.microsoft.com/library/f13692ee-a179-4439-ae72-50db9534eded)  
 [Instrukcje: włączanie usługi współużytkowania portów Net.TCP](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md)
