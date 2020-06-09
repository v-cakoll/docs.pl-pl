---
title: Zabezpieczenia komunikatów — Windows
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: d2221d1c-c9cb-48d1-b044-a3b4445c7f05
ms.openlocfilehash: 7b5b9ba0cc9a6d867b0478720b6151c7a561da16
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84584717"
---
# <a name="message-security-windows"></a><span data-ttu-id="d305e-102">Zabezpieczenia komunikatów — Windows</span><span class="sxs-lookup"><span data-stu-id="d305e-102">Message Security Windows</span></span>
<span data-ttu-id="d305e-103">Ten przykład pokazuje, jak skonfigurować <xref:System.ServiceModel.WSHttpBinding> powiązanie do używania zabezpieczeń na poziomie komunikatów z uwierzytelnianiem systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="d305e-103">This sample demonstrates how to configure a <xref:System.ServiceModel.WSHttpBinding> binding to use message-level security with Windows authentication.</span></span> <span data-ttu-id="d305e-104">Ten przykład jest oparty na [wprowadzenie](getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="d305e-104">This sample is based on the [Getting Started](getting-started-sample.md).</span></span> <span data-ttu-id="d305e-105">W tym przykładzie usługa jest hostowana w Internet Information Services (IIS), a klient jest aplikacją konsolową (. exe).</span><span class="sxs-lookup"><span data-stu-id="d305e-105">In this sample, the service is hosted in Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d305e-106">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="d305e-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="d305e-107">Domyślne zabezpieczenia [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) wiadomości są zabezpieczane przy użyciu uwierzytelniania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="d305e-107">The default security for the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) is message security using Windows authentication.</span></span> <span data-ttu-id="d305e-108">Pliki konfiguracji w tym przykładzie jawnie ustawiają `mode` atrybut [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) do `Message` i `clientCredentialType` atrybut na `Windows` .</span><span class="sxs-lookup"><span data-stu-id="d305e-108">The configuration files in this sample explicitly set the `mode` attribute of the [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) to `Message` and the `clientCredentialType` attribute to `Windows`.</span></span> <span data-ttu-id="d305e-109">Te wartości są wartościami domyślnymi tego powiązania, ale zostały one jawnie skonfigurowane, jak pokazano w poniższej konfiguracji przykładowej w celu zademonstrowania ich użycia.</span><span class="sxs-lookup"><span data-stu-id="d305e-109">These values are the default values for this binding, but they have been explicitly configured, as shown in the following sample configuration to demonstrate their use.</span></span>  
  
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
  
 <span data-ttu-id="d305e-110">Konfiguracja punktu końcowego klienta składa się z adresu bezwzględnego dla punktu końcowego usługi, powiązania i kontraktu.</span><span class="sxs-lookup"><span data-stu-id="d305e-110">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="d305e-111">Powiązanie klienta jest skonfigurowane z odpowiednimi `securityMode` i `authenticationMode` .</span><span class="sxs-lookup"><span data-stu-id="d305e-111">The client binding is configured with the appropriate `securityMode` and `authenticationMode`.</span></span>  
  
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
  
 <span data-ttu-id="d305e-112">Kod źródłowy usługi został zmodyfikowany, aby zademonstrować, jak <xref:System.ServiceModel.OperationContext.ServiceSecurityContext%2A> można go użyć w celu uzyskania dostępu do tożsamości obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="d305e-112">The service source code has been modified to demonstrate how the <xref:System.ServiceModel.OperationContext.ServiceSecurityContext%2A> can be used to access the identity of the caller.</span></span>  

```csharp
public string GetCallerIdentity()  
{  
    // The Windows identity of the caller can be accessed on the ServiceSecurityContext.WindowsIdentity.  
    return OperationContext.Current.ServiceSecurityContext.WindowsIdentity.Name;  
}  
```

 <span data-ttu-id="d305e-113">Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="d305e-113">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="d305e-114">Pierwsza wywoływana metoda- `GetCallerIdentity` -zwraca nazwę tożsamości obiektu wywołującego z powrotem do klienta.</span><span class="sxs-lookup"><span data-stu-id="d305e-114">The first method called - `GetCallerIdentity` - returns the name of the caller identity back to the client.</span></span> <span data-ttu-id="d305e-115">Naciśnij klawisz ENTER w oknie konsoli, aby zamknąć klienta programu.</span><span class="sxs-lookup"><span data-stu-id="d305e-115">Press ENTER in the console window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d305e-116">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="d305e-116">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="d305e-117">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d305e-117">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="d305e-118">Aby skompilować wersję rozwiązania w języku C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d305e-118">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="d305e-119">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d305e-119">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
