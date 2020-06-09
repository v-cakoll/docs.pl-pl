---
title: 'Instrukcje: Konfigurowanie usługi Windows Communication Foundation na potrzeby współużytkowania portów'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6400bc71-a858-4ac2-8d5a-caa72d3b5482
ms.openlocfilehash: 28f2858d68de99839d7fec66b0fe4528d7e42325
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579530"
---
# <a name="how-to-configure-a-windows-communication-foundation-service-to-use-port-sharing"></a><span data-ttu-id="9180b-102">Instrukcje: Konfigurowanie usługi Windows Communication Foundation na potrzeby współużytkowania portów</span><span class="sxs-lookup"><span data-stu-id="9180b-102">How to: Configure a Windows Communication Foundation Service to Use Port Sharing</span></span>
<span data-ttu-id="9180b-103">Najprostszym sposobem korzystania z net. TCP://udostępniania portów w aplikacji Windows Communication Foundation (WCF) jest udostępnienie usługi przy użyciu <xref:System.ServiceModel.NetTcpBinding> .</span><span class="sxs-lookup"><span data-stu-id="9180b-103">The easiest way to use net.tcp:// port sharing in your Windows Communication Foundation (WCF) application is to expose a service using the <xref:System.ServiceModel.NetTcpBinding>.</span></span>  
  
 <span data-ttu-id="9180b-104">To powiązanie zawiera <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> Właściwość, która kontroluje, czy jest włączone udostępnianie net. TCP://portu dla usługi skonfigurowanej przy użyciu tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="9180b-104">This binding provides a <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> property that controls whether net.tcp:// port sharing is enabled for the service being configured with this binding.</span></span>  
  
 <span data-ttu-id="9180b-105">Poniższa procedura pokazuje, jak używać <xref:System.ServiceModel.NetTcpBinding> klasy do otwierania punktu końcowego w Uniform Resource Identifier (URI) net. TCP://localhost/MyService, najpierw w kodzie, a następnie za pomocą elementów konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="9180b-105">The following procedure shows how to use the <xref:System.ServiceModel.NetTcpBinding> class to open an endpoint at the Uniform Resource Identifier (URI) net.tcp://localhost/MyService, first in code and then by using configuration elements.</span></span>  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-code"></a><span data-ttu-id="9180b-106">Aby włączyć udostępnianie za pomocą protokołu net. TCP://portu na NetTcpBinding w kodzie</span><span class="sxs-lookup"><span data-stu-id="9180b-106">To enable net.tcp:// port sharing on a NetTcpBinding in code</span></span>  
  
1. <span data-ttu-id="9180b-107">Utwórz usługę do implementowania kontraktu o nazwie `IMyService` i Wywołaj ją `MyService` ,.</span><span class="sxs-lookup"><span data-stu-id="9180b-107">Create a service to implement a contract called `IMyService` and call it `MyService`, .</span></span>  
  
     [!code-csharp[c_ConfigurePortSharing#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#1)]
     [!code-vb[c_ConfigurePortSharing#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#1)]  
  
2. <span data-ttu-id="9180b-108">Utwórz wystąpienie <xref:System.ServiceModel.NetTcpBinding> klasy i ustaw <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> Właściwość na `true` .</span><span class="sxs-lookup"><span data-stu-id="9180b-108">Create an instance of the <xref:System.ServiceModel.NetTcpBinding> class and set the <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> property to `true`.</span></span>  
  
     [!code-csharp[c_ConfigurePortSharing#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#2)]
     [!code-vb[c_ConfigurePortSharing#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#2)]  
  
3. <span data-ttu-id="9180b-109">Utwórz <xref:System.ServiceModel.ServiceHost> i Dodaj do niego punkt końcowy usługi dla programu `MyService` , który korzysta z włączonego udostępniania portów <xref:System.ServiceModel.NetTcpBinding> i który nasłuchuje pod adresem punktu końcowego URI "net. TCP://localhost/MyService".</span><span class="sxs-lookup"><span data-stu-id="9180b-109">Create a <xref:System.ServiceModel.ServiceHost> and add the service endpoint to it for `MyService` that uses the port sharing-enabled <xref:System.ServiceModel.NetTcpBinding> and that listens at the endpoint address URI "net.tcp://localhost/MyService".</span></span>  
  
     [!code-csharp[c_ConfigurePortSharing#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#3)]
     [!code-vb[c_ConfigurePortSharing#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#3)]  
  
    > [!NOTE]
    > <span data-ttu-id="9180b-110">W tym przykładzie jest stosowany domyślny port TCP 808, ponieważ identyfikator URI adresu punktu końcowego nie określa innego numeru portu.</span><span class="sxs-lookup"><span data-stu-id="9180b-110">This example uses the default TCP port of 808 because the endpoint address URI does not specify a different port number.</span></span> <span data-ttu-id="9180b-111">Ponieważ Udostępnianie portów jest jawnie włączone dla powiązania transportowego, ta usługa może współużytkować port 808 z innymi usługami w innych procesach.</span><span class="sxs-lookup"><span data-stu-id="9180b-111">Because port sharing is explicitly enabled on the transport binding, this service can share port 808 with other services in other processes.</span></span> <span data-ttu-id="9180b-112">Jeśli Udostępnianie portów było niedozwolone, a inna aplikacja już korzysta z portu 808, ta usługa spowodowałaby zgłoszenie <xref:System.ServiceModel.AddressAlreadyInUseException> podczas otwierania.</span><span class="sxs-lookup"><span data-stu-id="9180b-112">If port sharing were not allowed and another application were already using port 808, this service would throw an <xref:System.ServiceModel.AddressAlreadyInUseException> when it was opened.</span></span>  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-configuration"></a><span data-ttu-id="9180b-113">Aby włączyć udostępnianie za pomocą protokołu net. TCP://portu na NetTcpBinding w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="9180b-113">To enable net.tcp:// port sharing on a NetTcpBinding in configuration</span></span>  
  
1. <span data-ttu-id="9180b-114">Poniższy przykład pokazuje, jak włączyć Udostępnianie portów i dodać punkt końcowy usługi przy użyciu elementów konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="9180b-114">The following example shows how to enable port sharing and add the service endpoint using configuration elements.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9180b-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9180b-115">See also</span></span>

- [<span data-ttu-id="9180b-116">Współużytkowanie portów w składniku Net.TCP</span><span class="sxs-lookup"><span data-stu-id="9180b-116">Net.TCP Port Sharing</span></span>](net-tcp-port-sharing.md)
- [<span data-ttu-id="9180b-117">Instrukcje: włączanie usługi współużytkowania portów Net.TCP</span><span class="sxs-lookup"><span data-stu-id="9180b-117">How to: Enable the Net.TCP Port Sharing Service</span></span>](how-to-enable-the-net-tcp-port-sharing-service.md)
