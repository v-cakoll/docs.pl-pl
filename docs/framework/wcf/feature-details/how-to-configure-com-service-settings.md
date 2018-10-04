---
title: 'Porady: Konfigurowanie ustawień usługi COM +'
ms.date: 03/30/2017
helpviewer_keywords:
- COM+ [WCF], configuring service settings
ms.assetid: f42a55a8-3af8-4394-9fdd-bf12a93780eb
ms.openlocfilehash: d14fd1434cb87dc62babeabb79cb780e568aacb7
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48581843"
---
# <a name="how-to-configure-com-service-settings"></a><span data-ttu-id="547a9-102">Porady: Konfigurowanie ustawień usługi COM +</span><span class="sxs-lookup"><span data-stu-id="547a9-102">How to: Configure COM+ Service Settings</span></span>
<span data-ttu-id="547a9-103">Interfejs aplikacji są dodawane lub usuwane za pomocą narzędzia konfiguracji usług COM +, konfiguracji usługi sieci Web jest aktualizowana w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="547a9-103">When an application interface is added or removed by using the COM+ Service Configuration tool, the Web service configuration is updated within the application's configuration file.</span></span> <span data-ttu-id="547a9-104">W trybie hostowanej modelu COM + plik Application.config jest umieszczany w katalogu głównym aplikacji (aplikacje %PROGRAMFILES%\ComPlus\\{appid} jest wartością domyślną).</span><span class="sxs-lookup"><span data-stu-id="547a9-104">In the COM+ hosted mode, the Application.config file is placed in the Application Root Directory (%PROGRAMFILES%\ComPlus Applications\\{appid} is the default).</span></span> <span data-ttu-id="547a9-105">W obu trybach hostowanych w sieci Web w katalogu określonym vroot znajduje się plik Web.config.</span><span class="sxs-lookup"><span data-stu-id="547a9-105">In either of the Web-hosted modes, the Web.config file is placed in the specified vroot directory.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="547a9-106">Podpisywanie komunikatów należy chronić je przed naruszeniem wiadomości między klientem a serwerem.</span><span class="sxs-lookup"><span data-stu-id="547a9-106">Message signing should be used to protect against tampering of messages between a client and a server.</span></span> <span data-ttu-id="547a9-107">Wiadomości lub transportu szyfrowanie warstwy należy również chronić przed ujawnieniem informacji z komunikatów między klientem a serwerem.</span><span class="sxs-lookup"><span data-stu-id="547a9-107">Also, message or transport layer encryption should be used to protect against information disclosure from messages between a client and a server.</span></span> <span data-ttu-id="547a9-108">Podobnie jak w przypadku usług Windows Communication Foundation (WCF), należy używać ograniczania można ograniczyć liczbę współbieżnych wywołań, połączeń, wystąpienia i oczekujących operacji.</span><span class="sxs-lookup"><span data-stu-id="547a9-108">As with Windows Communication Foundation (WCF) services, you should use throttling to limit the number of concurrent calls, connections, instances, and pending operations.</span></span> <span data-ttu-id="547a9-109">Pozwala to zapobiec nadmiernego zużycia zasobów.</span><span class="sxs-lookup"><span data-stu-id="547a9-109">This helps prevent over-consumption of resources.</span></span> <span data-ttu-id="547a9-110">Zachowanie funkcji ograniczania przepływności jest określony za pomocą ustawień pliku konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="547a9-110">Throttling behavior is specified through service configuration file settings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="547a9-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="547a9-111">Example</span></span>  
 <span data-ttu-id="547a9-112">Należy wziąć pod uwagę składnika, który implementuje interfejs następujące:</span><span class="sxs-lookup"><span data-stu-id="547a9-112">Consider a component that implements the following interface:</span></span>  
  
```  
[Guid("C551FBA9-E3AA-4272-8C2A-84BD8D290AC7")]  
public interface IFinances  
{  
    string Debit(string accountNo, double amount);  
    string Credit(string accountNo, double amount);  
}  
```  
  
 <span data-ttu-id="547a9-113">Jeśli składnik jest udostępniany jako usługa sieci Web, odpowiedni kontrakt usługi, które będzie widoczne, a klienci będą powinny być zgodne, jest następujący:</span><span class="sxs-lookup"><span data-stu-id="547a9-113">If the component is exposed as a Web service, the corresponding service contract that is exposed, and that clients would need to conform to, is as follows:</span></span>  
  
```  
[ServiceContract(Session = true,  
Namespace = "http://tempuri.org/C551FBA9-E3AA-4272-8C2A-84BD8D290AC7",  
Name = "IFinances")]  
public interface IFinancesContract : IDisposable  
{  
    [OperationContract]  
    string Debit(string accountNo, double amount);  
    [OperationContract]  
    string Credit(string accountNo, double amount);  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="547a9-114">IID częścią początkowej przestrzeni nazw kontraktu.</span><span class="sxs-lookup"><span data-stu-id="547a9-114">IID forms part of the initial namespace for the contract.</span></span>  
  
 <span data-ttu-id="547a9-115">Aplikacje klienckie, które używają tej usługi musi być zgodna z niniejszej Umowy oraz za pomocą powiązania, która jest zgodna z długością zawartą w konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="547a9-115">Client applications that use this service would need to conform to this contract, along with using a binding that is compatible with the one specified in the application configuration.</span></span>  
  
 <span data-ttu-id="547a9-116">Poniższy przykładowy kod przedstawia domyślny plik konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="547a9-116">The following code example shows a default configuration file.</span></span> <span data-ttu-id="547a9-117">Usługi sieci Web Windows Communication Foundation (WCF), to jest zgodny ze schematem konfiguracji modelu usług w warstwie standardowa i można je edytować w taki sam sposób jak inne pliki konfiguracji usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="547a9-117">Being a Windows Communication Foundation (WCF) Web service, this conforms to the standard service model configuration schema and can be edited in the same way as other WCF services configuration files.</span></span>  
  
 <span data-ttu-id="547a9-118">Modyfikacje Typowa zamieści:</span><span class="sxs-lookup"><span data-stu-id="547a9-118">Typical modifications would include:</span></span>  
  
- <span data-ttu-id="547a9-119">Zmienianie adresu punktu końcowego z domyślnego formularza ApplicationName/ComponentName/InterfaceName do bardziej użytecznej postaci.</span><span class="sxs-lookup"><span data-stu-id="547a9-119">Changing the endpoint address from the default ApplicationName/ComponentName/InterfaceName form to a more usable form.</span></span>  
  
- <span data-ttu-id="547a9-120">Modyfikowanie przestrzeni nazw usługi z domyślnego `http://tempuri.org/InterfaceID` formularz, aby lepiej dopasowane formularza.</span><span class="sxs-lookup"><span data-stu-id="547a9-120">Modifying the namespace of the service from the default `http://tempuri.org/InterfaceID` form to a more relevant form.</span></span>  
  
- <span data-ttu-id="547a9-121">Zmiana punktu końcowego, aby użyć powiązania innego transportu.</span><span class="sxs-lookup"><span data-stu-id="547a9-121">Changing the endpoint to use a different transport binding.</span></span>  
  
     <span data-ttu-id="547a9-122">W modelu COM +-hostowanej przypadkach transportu do potoków nazwanych jest używany domyślnie, ale zamiast tego można transportu wyłączyć maszyny, podobnie jak protokół TCP.</span><span class="sxs-lookup"><span data-stu-id="547a9-122">In the COM+-hosted case, the named pipes transport is used by default, but an off-machine transport like TCP can be used instead.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
    <system.serviceModel>  
        <bindings>  
            <netNamedPipeBinding>  
                <binding name="comNonTransactionalBinding" />  
                <binding name="comTransactionalBinding" transactionFlow="true" />  
            </netNamedPipeBinding>  
        </bindings>  
        <comContracts>  
            <comContract contract="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}"  
                name="IFinances" namespace="http://tempuri.org/C551FBA9-E3AA-4272-8C2A-84BD8D290AC7"  
                requiresSession="true">  
                <exposedMethods>  
                    <add exposedMethod="Debit" />  
                    <add exposedMethod="Credit" />  
                </exposedMethods>  
            </comContract>  
        </comContracts>  
        <services>  
            <service name="{DCDB24CC-0B19-4534-95CD-FBBFF4D67DD9},{C942B840-AD54-4A44-B5F7-928130980AB9}">  
                <endpoint address="IFinances" binding="netNamedPipeBinding" bindingConfiguration="comNonTransactionalBinding"  
                    contract="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}" />  
                <host>  
                    <baseAddresses>  
                        <add baseAddress="net.pipe://localhost/ServiceModelDocSampleApp/ServiceModelDocSample.esFinance" />  
                    </baseAddresses>  
                </host>  
            </service>  
        </services>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="547a9-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="547a9-123">See Also</span></span>  
 [<span data-ttu-id="547a9-124">Współdziałanie z aplikacjami COM+</span><span class="sxs-lookup"><span data-stu-id="547a9-124">Integrating with COM+ Applications</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
