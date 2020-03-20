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
# <a name="how-to-configure-a-windows-communication-foundation-service-to-use-port-sharing"></a><span data-ttu-id="1561c-102">Instrukcje: Konfigurowanie usługi Windows Communication Foundation na potrzeby współużytkowania portów</span><span class="sxs-lookup"><span data-stu-id="1561c-102">How to: Configure a Windows Communication Foundation Service to Use Port Sharing</span></span>
<span data-ttu-id="1561c-103">Najprostszym sposobem użycia net.tcp:// udostępniania portów w aplikacji Windows Communication Foundation (WCF) jest udostępnienie usługi przy użyciu <xref:System.ServiceModel.NetTcpBinding>pliku .</span><span class="sxs-lookup"><span data-stu-id="1561c-103">The easiest way to use net.tcp:// port sharing in your Windows Communication Foundation (WCF) application is to expose a service using the <xref:System.ServiceModel.NetTcpBinding>.</span></span>  
  
 <span data-ttu-id="1561c-104">To powiązanie <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> zawiera właściwość, która kontroluje, czy net.tcp:// udostępnianie portów jest włączone dla usługi skonfigurowane z tym powiązaniem.</span><span class="sxs-lookup"><span data-stu-id="1561c-104">This binding provides a <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> property that controls whether net.tcp:// port sharing is enabled for the service being configured with this binding.</span></span>  
  
 <span data-ttu-id="1561c-105">Poniższa procedura pokazuje, <xref:System.ServiceModel.NetTcpBinding> jak użyć klasy, aby otworzyć punkt końcowy w jednolity identyfikator zasobu (URI) net.tcp://localhost/MyService, najpierw w kodzie, a następnie przy użyciu elementów konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="1561c-105">The following procedure shows how to use the <xref:System.ServiceModel.NetTcpBinding> class to open an endpoint at the Uniform Resource Identifier (URI) net.tcp://localhost/MyService, first in code and then by using configuration elements.</span></span>  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-code"></a><span data-ttu-id="1561c-106">Aby włączyć udostępnianie portów net.tcp:// w kodzie NetTcpBinding</span><span class="sxs-lookup"><span data-stu-id="1561c-106">To enable net.tcp:// port sharing on a NetTcpBinding in code</span></span>  
  
1. <span data-ttu-id="1561c-107">Utwórz usługę, aby `IMyService` zaimplementować kontrakt o nazwie i wywołać go `MyService`, .</span><span class="sxs-lookup"><span data-stu-id="1561c-107">Create a service to implement a contract called `IMyService` and call it `MyService`, .</span></span>  
  
     [!code-csharp[c_ConfigurePortSharing#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#1)]
     [!code-vb[c_ConfigurePortSharing#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#1)]  
  
2. <span data-ttu-id="1561c-108">Utwórz wystąpienie <xref:System.ServiceModel.NetTcpBinding> klasy i <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> ustaw `true`właściwość na .</span><span class="sxs-lookup"><span data-stu-id="1561c-108">Create an instance of the <xref:System.ServiceModel.NetTcpBinding> class and set the <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> property to `true`.</span></span>  
  
     [!code-csharp[c_ConfigurePortSharing#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#2)]
     [!code-vb[c_ConfigurePortSharing#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#2)]  
  
3. <span data-ttu-id="1561c-109">Utwórz <xref:System.ServiceModel.ServiceHost> i dodaj do niego `MyService` punkt końcowy usługi, który <xref:System.ServiceModel.NetTcpBinding> używa włączonego udostępniania portu i nasłuchuje w adresie końcowym URI "net.tcp://localhost/MyService".</span><span class="sxs-lookup"><span data-stu-id="1561c-109">Create a <xref:System.ServiceModel.ServiceHost> and add the service endpoint to it for `MyService` that uses the port sharing-enabled <xref:System.ServiceModel.NetTcpBinding> and that listens at the endpoint address URI "net.tcp://localhost/MyService".</span></span>  
  
     [!code-csharp[c_ConfigurePortSharing#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#3)]
     [!code-vb[c_ConfigurePortSharing#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#3)]  
  
    > [!NOTE]
    > <span data-ttu-id="1561c-110">W tym przykładzie użyto domyślnego portu TCP 808, ponieważ identyfikator URI adresu punktu końcowego nie określa innego numeru portu.</span><span class="sxs-lookup"><span data-stu-id="1561c-110">This example uses the default TCP port of 808 because the endpoint address URI does not specify a different port number.</span></span> <span data-ttu-id="1561c-111">Ponieważ udostępnianie portów jest jawnie włączone w powiązaniu transportu, ta usługa może współużytkować port 808 innym usługom w innych procesach.</span><span class="sxs-lookup"><span data-stu-id="1561c-111">Because port sharing is explicitly enabled on the transport binding, this service can share port 808 with other services in other processes.</span></span> <span data-ttu-id="1561c-112">Jeśli udostępnianie portów nie było dozwolone, a inna aplikacja już używała <xref:System.ServiceModel.AddressAlreadyInUseException> portu 808, ta usługa zgłaszałaby, kiedy została otwarta.</span><span class="sxs-lookup"><span data-stu-id="1561c-112">If port sharing were not allowed and another application were already using port 808, this service would throw an <xref:System.ServiceModel.AddressAlreadyInUseException> when it was opened.</span></span>  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-configuration"></a><span data-ttu-id="1561c-113">Aby włączyć udostępnianie portów net.tcp:// w konfiguracji NetTcpBinding</span><span class="sxs-lookup"><span data-stu-id="1561c-113">To enable net.tcp:// port sharing on a NetTcpBinding in configuration</span></span>  
  
1. <span data-ttu-id="1561c-114">W poniższym przykładzie pokazano, jak włączyć udostępnianie portów i dodać punkt końcowy usługi przy użyciu elementów konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="1561c-114">The following example shows how to enable port sharing and add the service endpoint using configuration elements.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1561c-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1561c-115">See also</span></span>

- [<span data-ttu-id="1561c-116">Współużytkowanie portów w składniku Net.TCP</span><span class="sxs-lookup"><span data-stu-id="1561c-116">Net.TCP Port Sharing</span></span>](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)
- [<span data-ttu-id="1561c-117">Instrukcje: włączanie usługi współużytkowania portów Net.TCP</span><span class="sxs-lookup"><span data-stu-id="1561c-117">How to: Enable the Net.TCP Port Sharing Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md)
