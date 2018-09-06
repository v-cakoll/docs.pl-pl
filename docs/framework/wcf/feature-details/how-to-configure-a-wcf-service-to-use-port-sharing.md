---
title: 'Instrukcje: Konfigurowanie usługi Windows Communication Foundation na potrzeby współużytkowania portów'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6400bc71-a858-4ac2-8d5a-caa72d3b5482
ms.openlocfilehash: 2715e319772e4e0ae4cb38f3dbd1dd5133a2eef3
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43801076"
---
# <a name="how-to-configure-a-windows-communication-foundation-service-to-use-port-sharing"></a><span data-ttu-id="f8c29-102">Instrukcje: Konfigurowanie usługi Windows Communication Foundation na potrzeby współużytkowania portów</span><span class="sxs-lookup"><span data-stu-id="f8c29-102">How to: Configure a Windows Communication Foundation Service to Use Port Sharing</span></span>
<span data-ttu-id="f8c29-103">Najprostszym sposobem na korzystanie z portu net.tcp:// udostępniania w aplikacji Windows Communication Foundation (WCF) jest do udostępnienia usługi za pomocą <xref:System.ServiceModel.NetTcpBinding>.</span><span class="sxs-lookup"><span data-stu-id="f8c29-103">The easiest way to use net.tcp:// port sharing in your Windows Communication Foundation (WCF) application is to expose a service using the <xref:System.ServiceModel.NetTcpBinding>.</span></span>  
  
 <span data-ttu-id="f8c29-104">Zapewnia to powiązanie <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> właściwość, która określa, czy usługi są skonfigurowane z tym powiązaniem włączone jest udostępnianie portów net.tcp://.</span><span class="sxs-lookup"><span data-stu-id="f8c29-104">This binding provides a <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> property that controls whether net.tcp:// port sharing is enabled for the service being configured with this binding.</span></span>  
  
 <span data-ttu-id="f8c29-105">Poniższa procedura przedstawia sposób użycia <xref:System.ServiceModel.NetTcpBinding> klasy, aby najpierw otwórz punkt końcowy w net.tcp://localhost/MyService identyfikator (URI), w kodzie, a następnie za pomocą elementów konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f8c29-105">The following procedure shows how to use the <xref:System.ServiceModel.NetTcpBinding> class to open an endpoint at the Uniform Resource Identifier (URI) net.tcp://localhost/MyService, first in code and then by using configuration elements.</span></span>  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-code"></a><span data-ttu-id="f8c29-106">Aby włączyć port net.tcp:// udostępnianie na NetTcpBinding w kodzie</span><span class="sxs-lookup"><span data-stu-id="f8c29-106">To enable net.tcp:// port sharing on a NetTcpBinding in code</span></span>  
  
1.  <span data-ttu-id="f8c29-107">Tworzenie usługi, aby zaimplementować kontrakt o nazwie `IMyService` i nadać mu `MyService`,.</span><span class="sxs-lookup"><span data-stu-id="f8c29-107">Create a service to implement a contract called `IMyService` and call it `MyService`, .</span></span>  
  
     [!code-csharp[c_ConfigurePortSharing#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#1)]
     [!code-vb[c_ConfigurePortSharing#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#1)]  
  
2.  <span data-ttu-id="f8c29-108">Utwórz wystąpienie obiektu <xref:System.ServiceModel.NetTcpBinding> klasy i ustaw <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="f8c29-108">Create an instance of the <xref:System.ServiceModel.NetTcpBinding> class and set the <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> property to `true`.</span></span>  
  
     [!code-csharp[c_ConfigurePortSharing#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#2)]
     [!code-vb[c_ConfigurePortSharing#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#2)]  
  
3.  <span data-ttu-id="f8c29-109">Tworzenie <xref:System.ServiceModel.ServiceHost> i Dodaj punkt końcowy usługi do niej uzyskać `MyService` używający portu włączone udostępnianie <xref:System.ServiceModel.NetTcpBinding> i że nasłuchuje w punkcie końcowym adresu URI "net.tcp://localhost/MyService".</span><span class="sxs-lookup"><span data-stu-id="f8c29-109">Create a <xref:System.ServiceModel.ServiceHost> and add the service endpoint to it for `MyService` that uses the port sharing-enabled <xref:System.ServiceModel.NetTcpBinding> and that listens at the endpoint address URI "net.tcp://localhost/MyService".</span></span>  
  
     [!code-csharp[c_ConfigurePortSharing#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#3)]
     [!code-vb[c_ConfigurePortSharing#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#3)]  
  
    > [!NOTE]
    >  <span data-ttu-id="f8c29-110">Ten przykład używa domyślnego portu TCP 808, ponieważ adres punktu końcowego identyfikatora URI nie określa inny numer portu.</span><span class="sxs-lookup"><span data-stu-id="f8c29-110">This example uses the default TCP port of 808 because the endpoint address URI does not specify a different port number.</span></span> <span data-ttu-id="f8c29-111">Ponieważ jawnie powiązania transportu włączone udostępnianie portów, tej usługi można udostępniać port 808 z innymi usługami w innych procesów.</span><span class="sxs-lookup"><span data-stu-id="f8c29-111">Because port sharing is explicitly enabled on the transport binding, this service can share port 808 with other services in other processes.</span></span> <span data-ttu-id="f8c29-112">Jeśli Udostępnianie portów nie zezwolono na innej aplikacji zostały już używa portu 808, ta usługa będzie zgłaszają <xref:System.ServiceModel.AddressAlreadyInUseException> kiedy został otwarty.</span><span class="sxs-lookup"><span data-stu-id="f8c29-112">If port sharing were not allowed and another application were already using port 808, this service would throw an <xref:System.ServiceModel.AddressAlreadyInUseException> when it was opened.</span></span>  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-configuration"></a><span data-ttu-id="f8c29-113">Aby włączyć port net.tcp:// udostępnianie na NetTcpBinding w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="f8c29-113">To enable net.tcp:// port sharing on a NetTcpBinding in configuration</span></span>  
  
1.  <span data-ttu-id="f8c29-114">Poniższy przykład pokazuje, jak włączyć Udostępnianie portów i dodać punktu końcowego usługi za pomocą elementów konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f8c29-114">The following example shows how to enable port sharing and add the service endpoint using configuration elements.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f8c29-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f8c29-115">See Also</span></span>  
 [<span data-ttu-id="f8c29-116">Współużytkowanie portów w składniku Net.TCP</span><span class="sxs-lookup"><span data-stu-id="f8c29-116">Net.TCP Port Sharing</span></span>](https://msdn.microsoft.com/library/f13692ee-a179-4439-ae72-50db9534eded)  
 [<span data-ttu-id="f8c29-117">Instrukcje: włączanie usługi współużytkowania portów Net.TCP</span><span class="sxs-lookup"><span data-stu-id="f8c29-117">How to: Enable the Net.TCP Port Sharing Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md)
