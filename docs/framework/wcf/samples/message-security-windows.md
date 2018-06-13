---
title: Zabezpieczenia komunikatów — Windows
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: d2221d1c-c9cb-48d1-b044-a3b4445c7f05
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 7bf731c1accd6eefc97c27af58ba139992ae1866
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33502364"
---
# <a name="message-security-windows"></a><span data-ttu-id="198af-102">Zabezpieczenia komunikatów — Windows</span><span class="sxs-lookup"><span data-stu-id="198af-102">Message Security Windows</span></span>
<span data-ttu-id="198af-103">W tym przykładzie pokazano, jak skonfigurować <xref:System.ServiceModel.WSHttpBinding> powiązania w celu użycia zabezpieczenia na poziomie komunikatu z uwierzytelnianiem systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="198af-103">This sample demonstrates how to configure a <xref:System.ServiceModel.WSHttpBinding> binding to use message-level security with Windows authentication.</span></span> <span data-ttu-id="198af-104">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="198af-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="198af-105">W tym przykładzie usługa jest obsługiwana w Internet Information Services (IIS) i klient jest aplikacji konsoli (.exe).</span><span class="sxs-lookup"><span data-stu-id="198af-105">In this sample, the service is hosted in Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="198af-106">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="198af-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="198af-107">Domyślne zabezpieczenia dla [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) zabezpieczeń wiadomości przy użyciu uwierzytelniania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="198af-107">The default security for the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) is message security using Windows authentication.</span></span> <span data-ttu-id="198af-108">Pliki konfiguracji, w tym przykładzie jawnie ustawiona `mode` atrybutu [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) do `Message` i `clientCredentialType` atrybutu `Windows`.</span><span class="sxs-lookup"><span data-stu-id="198af-108">The configuration files in this sample explicitly set the `mode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) to `Message` and the `clientCredentialType` attribute to `Windows`.</span></span> <span data-ttu-id="198af-109">Te wartości są wartościami domyślnymi dla tego powiązania, ale zostały jawnie skonfigurowane, jak pokazano w poniższych Przykładowa konfiguracja do zaprezentowania ich używania.</span><span class="sxs-lookup"><span data-stu-id="198af-109">These values are the default values for this binding, but they have been explicitly configured, as shown in the following sample configuration to demonstrate their use.</span></span>  
  
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
  
 <span data-ttu-id="198af-110">Konfiguracja punktu końcowego klienta składa się z adres bezwzględny dla punktu końcowego usługi, powiązanie i kontraktu.</span><span class="sxs-lookup"><span data-stu-id="198af-110">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="198af-111">Klient powiązanie jest skonfigurowany z użyciem odpowiednich `securityMode` i `authenticationMode`.</span><span class="sxs-lookup"><span data-stu-id="198af-111">The client binding is configured with the appropriate `securityMode` and `authenticationMode`.</span></span>  
  
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
      <!--   
      <!--The default security for the WSHttpBinding is-->  
      <!--Message security using Windows authentication. -->  
      <!--This configuration explicitly defines the security mode -->  
      <!--as Message and the clientCredentialType as Windows  -->  
      <!--for demonstration purposes. -->  
      <binding name="Binding1">  
        <security mode="Message">  
          <message clientCredentialType="Windows"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="198af-112">Kod źródłowy usługi został zmodyfikowany w celu pokazują, jak <xref:System.ServiceModel.OperationContext.ServiceSecurityContext%2A> mogą być używane do dostępu tożsamości obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="198af-112">The service source code has been modified to demonstrate how the <xref:System.ServiceModel.OperationContext.ServiceSecurityContext%2A> can be used to access the identity of the caller.</span></span>  

```csharp
public string GetCallerIdentity()  
{  
    // The Windows identity of the caller can be accessed on the ServiceSecurityContext.WindowsIdentity.  
    return OperationContext.Current.ServiceSecurityContext.WindowsIdentity.Name;  
}  
```

 <span data-ttu-id="198af-113">Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="198af-113">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="198af-114">Pierwsza metoda wywoływana - `GetCallerIdentity` — zwraca nazwę tożsamości wywołującego do klienta.</span><span class="sxs-lookup"><span data-stu-id="198af-114">The first method called - `GetCallerIdentity` - returns the name of the caller identity back to the client.</span></span> <span data-ttu-id="198af-115">Naciśnij klawisz ENTER w oknie konsoli, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="198af-115">Press ENTER in the console window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="198af-116">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="198af-116">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="198af-117">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="198af-117">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="198af-118">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="198af-118">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="198af-119">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="198af-119">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="198af-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="198af-120">See Also</span></span>
