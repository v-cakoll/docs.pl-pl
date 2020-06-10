---
title: 'Instrukcje: konfigurowanie ustawień usługi COM+'
ms.date: 03/30/2017
helpviewer_keywords:
- COM+ [WCF], configuring service settings
ms.assetid: f42a55a8-3af8-4394-9fdd-bf12a93780eb
ms.openlocfilehash: 3fb4b31038845d223248e72d32b3e7413f2aef63
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597179"
---
# <a name="how-to-configure-com-service-settings"></a><span data-ttu-id="2c1cd-102">Instrukcje: konfigurowanie ustawień usługi COM+</span><span class="sxs-lookup"><span data-stu-id="2c1cd-102">How to: Configure COM+ Service Settings</span></span>
<span data-ttu-id="2c1cd-103">Gdy interfejs aplikacji zostanie dodany lub usunięty przy użyciu narzędzia konfiguracji usługi COM+, konfiguracja usługi sieci Web jest aktualizowana w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2c1cd-103">When an application interface is added or removed by using the COM+ Service Configuration tool, the Web service configuration is updated within the application's configuration file.</span></span> <span data-ttu-id="2c1cd-104">W trybie hostowanym modelu COM+ plik Application. config jest umieszczany w katalogu głównym aplikacji (domyślnie są to aplikacje%PROGRAMFILES%\ComPlus \\ {AppID}).</span><span class="sxs-lookup"><span data-stu-id="2c1cd-104">In the COM+ hosted mode, the Application.config file is placed in the Application Root Directory (%PROGRAMFILES%\ComPlus Applications\\{appid} is the default).</span></span> <span data-ttu-id="2c1cd-105">W każdym z trybów hostowanych w sieci Web plik Web. config znajduje się w określonym katalogu wirtualnym.</span><span class="sxs-lookup"><span data-stu-id="2c1cd-105">In either of the Web-hosted modes, the Web.config file is placed in the specified vroot directory.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2c1cd-106">Podpisywanie komunikatów należy używać do ochrony przed manipulacją komunikatów między klientem a serwerem.</span><span class="sxs-lookup"><span data-stu-id="2c1cd-106">Message signing should be used to protect against tampering of messages between a client and a server.</span></span> <span data-ttu-id="2c1cd-107">Ponadto w celu ochrony przed ujawnieniem informacji z komunikatów między klientem a serwerem należy użyć szyfrowania z warstwy komunikatów lub transportu.</span><span class="sxs-lookup"><span data-stu-id="2c1cd-107">Also, message or transport layer encryption should be used to protect against information disclosure from messages between a client and a server.</span></span> <span data-ttu-id="2c1cd-108">Podobnie jak w przypadku usług Windows Communication Foundation (WCF), należy użyć ograniczania przepustowości, aby ograniczyć liczbę współbieżnych wywołań, połączeń, wystąpień i oczekujących operacji.</span><span class="sxs-lookup"><span data-stu-id="2c1cd-108">As with Windows Communication Foundation (WCF) services, you should use throttling to limit the number of concurrent calls, connections, instances, and pending operations.</span></span> <span data-ttu-id="2c1cd-109">Pozwala to zapobiec nadmiernemu zużyciu zasobów.</span><span class="sxs-lookup"><span data-stu-id="2c1cd-109">This helps prevent over-consumption of resources.</span></span> <span data-ttu-id="2c1cd-110">Zachowanie ograniczania jest określone za poorednictwem ustawień pliku konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="2c1cd-110">Throttling behavior is specified through service configuration file settings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c1cd-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="2c1cd-111">Example</span></span>  
 <span data-ttu-id="2c1cd-112">Rozważmy składnik implementujący następujący interfejs:</span><span class="sxs-lookup"><span data-stu-id="2c1cd-112">Consider a component that implements the following interface:</span></span>  
  
```csharp
[Guid("C551FBA9-E3AA-4272-8C2A-84BD8D290AC7")]  
public interface IFinances  
{  
    string Debit(string accountNo, double amount);  
    string Credit(string accountNo, double amount);  
}  
```  
  
 <span data-ttu-id="2c1cd-113">Jeśli składnik jest udostępniany jako usługa sieci Web, odpowiadający mu kontrakt usługi, który jest udostępniany, a klienci muszą spełniać następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="2c1cd-113">If the component is exposed as a Web service, the corresponding service contract that is exposed, and that clients would need to conform to, is as follows:</span></span>  
  
```csharp
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
> <span data-ttu-id="2c1cd-114">Identyfikator IID stanowi część początkowej przestrzeni nazw dla kontraktu.</span><span class="sxs-lookup"><span data-stu-id="2c1cd-114">IID forms part of the initial namespace for the contract.</span></span>  
  
 <span data-ttu-id="2c1cd-115">Aplikacje klienckie korzystające z tej usługi muszą być zgodne z tym kontraktem wraz z użyciem powiązania, które jest zgodne z określonym w konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2c1cd-115">Client applications that use this service would need to conform to this contract, along with using a binding that is compatible with the one specified in the application configuration.</span></span>  
  
 <span data-ttu-id="2c1cd-116">Poniższy przykład kodu pokazuje domyślny plik konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="2c1cd-116">The following code example shows a default configuration file.</span></span> <span data-ttu-id="2c1cd-117">Jest to usługa sieci Web programu Windows Communication Foundation (WCF), która jest zgodna ze schematem konfiguracji standardowego modelu usług i można ją edytować w taki sam sposób, jak w przypadku innych plików konfiguracji usług WCF.</span><span class="sxs-lookup"><span data-stu-id="2c1cd-117">Being a Windows Communication Foundation (WCF) Web service, this conforms to the standard service model configuration schema and can be edited in the same way as other WCF services configuration files.</span></span>  
  
 <span data-ttu-id="2c1cd-118">Typowe modyfikacje obejmują:</span><span class="sxs-lookup"><span data-stu-id="2c1cd-118">Typical modifications would include:</span></span>  
  
- <span data-ttu-id="2c1cd-119">Zmiana adresu punktu końcowego z domyślnego typu ApplicationName/ComponentName/InterfaceName na bardziej użyteczny formularz.</span><span class="sxs-lookup"><span data-stu-id="2c1cd-119">Changing the endpoint address from the default ApplicationName/ComponentName/InterfaceName form to a more usable form.</span></span>  
  
- <span data-ttu-id="2c1cd-120">Modyfikowanie przestrzeni nazw usługi z poziomu `http://tempuri.org/InterfaceID` formularza domyślnego na bardziej istotny.</span><span class="sxs-lookup"><span data-stu-id="2c1cd-120">Modifying the namespace of the service from the default `http://tempuri.org/InterfaceID` form to a more relevant form.</span></span>  
  
- <span data-ttu-id="2c1cd-121">Zmiana punktu końcowego w taki sposób, aby używał innego powiązania transportowego.</span><span class="sxs-lookup"><span data-stu-id="2c1cd-121">Changing the endpoint to use a different transport binding.</span></span>  
  
     <span data-ttu-id="2c1cd-122">W przypadku aplikacji w przypadku modelu COM+ jest używana domyślnie transport potoków nazwanych, ale zamiast tego można użyć transportu poza komputerem.</span><span class="sxs-lookup"><span data-stu-id="2c1cd-122">In the COM+-hosted case, the named pipes transport is used by default, but an off-machine transport like TCP can be used instead.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2c1cd-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2c1cd-123">See also</span></span>

- [<span data-ttu-id="2c1cd-124">Integrowanie z aplikacjami COM+</span><span class="sxs-lookup"><span data-stu-id="2c1cd-124">Integrating with COM+ Applications</span></span>](integrating-with-com-plus-applications.md)
