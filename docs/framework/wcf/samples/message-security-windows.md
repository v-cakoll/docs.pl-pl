---
title: Zabezpieczenia komunikatów — Windows
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: d2221d1c-c9cb-48d1-b044-a3b4445c7f05
ms.openlocfilehash: f46eb12078082614cd6cdc75b7bc7eedb7c94de9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930432"
---
# <a name="message-security-windows"></a><span data-ttu-id="0d400-102">Zabezpieczenia komunikatów — Windows</span><span class="sxs-lookup"><span data-stu-id="0d400-102">Message Security Windows</span></span>
<span data-ttu-id="0d400-103">Ten przykład pokazuje, jak skonfigurować <xref:System.ServiceModel.WSHttpBinding> powiązanie do używania zabezpieczeń na poziomie komunikatów z uwierzytelnianiem systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="0d400-103">This sample demonstrates how to configure a <xref:System.ServiceModel.WSHttpBinding> binding to use message-level security with Windows authentication.</span></span> <span data-ttu-id="0d400-104">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="0d400-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="0d400-105">W tym przykładzie usługa jest hostowana w Internet Information Services (IIS), a klient jest aplikacją konsolową (. exe).</span><span class="sxs-lookup"><span data-stu-id="0d400-105">In this sample, the service is hosted in Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0d400-106">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="0d400-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="0d400-107">Domyślne zabezpieczenia [ \<WSHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) to zabezpieczenia komunikatów przy użyciu uwierzytelniania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="0d400-107">The default security for the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) is message security using Windows authentication.</span></span> <span data-ttu-id="0d400-108">Pliki konfiguracji w tym przykładzie jawnie ustawiają `mode` atrybut [ \<>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) `Message` zabezpieczeń i `clientCredentialType` atrybut do `Windows`.</span><span class="sxs-lookup"><span data-stu-id="0d400-108">The configuration files in this sample explicitly set the `mode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) to `Message` and the `clientCredentialType` attribute to `Windows`.</span></span> <span data-ttu-id="0d400-109">Te wartości są wartościami domyślnymi tego powiązania, ale zostały one jawnie skonfigurowane, jak pokazano w poniższej konfiguracji przykładowej w celu zademonstrowania ich użycia.</span><span class="sxs-lookup"><span data-stu-id="0d400-109">These values are the default values for this binding, but they have been explicitly configured, as shown in the following sample configuration to demonstrate their use.</span></span>  
  
```xml  
<bindings>  
    <wsHttpBinding>  
        <binding>  
            <security mode="Message">  
                <message clientCredentialType="Windows"/>  
            </security>  
        </binding>  
    </wsHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="0d400-110">Konfiguracja punktu końcowego klienta składa się z adresu bezwzględnego dla punktu końcowego usługi, powiązania i kontraktu.</span><span class="sxs-lookup"><span data-stu-id="0d400-110">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="0d400-111">Powiązanie klienta jest skonfigurowane z odpowiednimi `securityMode` i. `authenticationMode`</span><span class="sxs-lookup"><span data-stu-id="0d400-111">The client binding is configured with the appropriate `securityMode` and `authenticationMode`.</span></span>  
  
```xml  
<system.serviceModel>  
  <client>  
    <endpoint address=  
            "http://localhost/servicemodelsamples/service.svc"   
            binding="wsHttpBinding"   
            bindingConfiguration="Binding1"   
            contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </client>  
  
  <bindings>  
    <wsHttpBinding>  
      <!-- The default security for the WSHttpBinding is -->  
      <!-- Message security using Windows authentication. -->  
      <!-- This configuration explicitly defines the security mode -->  
      <!-- as Message and the clientCredentialType as Windows -->  
      <!-- for demonstration purposes. -->  
      <binding name="Binding1">  
        <security mode="Message">  
          <message clientCredentialType="Windows"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="0d400-112">Kod źródłowy usługi został zmodyfikowany, aby zademonstrować, <xref:System.ServiceModel.OperationContext.ServiceSecurityContext%2A> jak można go użyć w celu uzyskania dostępu do tożsamości obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="0d400-112">The service source code has been modified to demonstrate how the <xref:System.ServiceModel.OperationContext.ServiceSecurityContext%2A> can be used to access the identity of the caller.</span></span>  

```csharp
public string GetCallerIdentity()  
{  
    // The Windows identity of the caller can be accessed on the ServiceSecurityContext.WindowsIdentity.  
    return OperationContext.Current.ServiceSecurityContext.WindowsIdentity.Name;  
}  
```

 <span data-ttu-id="0d400-113">Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="0d400-113">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="0d400-114">Pierwsza wywoływana metoda- `GetCallerIdentity` -zwraca nazwę tożsamości obiektu wywołującego z powrotem do klienta.</span><span class="sxs-lookup"><span data-stu-id="0d400-114">The first method called - `GetCallerIdentity` - returns the name of the caller identity back to the client.</span></span> <span data-ttu-id="0d400-115">Naciśnij klawisz ENTER w oknie konsoli, aby zamknąć klienta programu.</span><span class="sxs-lookup"><span data-stu-id="0d400-115">Press ENTER in the console window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0d400-116">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="0d400-116">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="0d400-117">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0d400-117">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="0d400-118">Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0d400-118">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="0d400-119">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0d400-119">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
