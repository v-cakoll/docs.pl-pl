---
title: Zabezpieczenia transportu WS
ms.date: 03/30/2017
ms.assetid: 33a20358-5e1b-458a-a6a9-15753bc7b99b
ms.openlocfilehash: 5023e5a0233906a0766eb307f35094768ee372a4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942146"
---
# <a name="ws-transport-security"></a><span data-ttu-id="5aeb6-102">Zabezpieczenia transportu WS</span><span class="sxs-lookup"><span data-stu-id="5aeb6-102">WS Transport Security</span></span>
<span data-ttu-id="5aeb6-103">Ten przykład ilustruje użycie zabezpieczeń transportu SSL z <xref:System.ServiceModel.WSHttpBinding> powiązaniem.</span><span class="sxs-lookup"><span data-stu-id="5aeb6-103">This sample demonstrates the use of SSL transport security with the <xref:System.ServiceModel.WSHttpBinding> binding.</span></span> <span data-ttu-id="5aeb6-104">Domyślnie `wsHttpBinding` powiązanie zapewnia komunikację http.</span><span class="sxs-lookup"><span data-stu-id="5aeb6-104">By default, the `wsHttpBinding` binding provides HTTP communication.</span></span> <span data-ttu-id="5aeb6-105">W przypadku skonfigurowania zabezpieczeń transportu powiązanie obsługuje komunikację HTTPS.</span><span class="sxs-lookup"><span data-stu-id="5aeb6-105">When configured for transport security, the binding supports HTTPS communication.</span></span> <span data-ttu-id="5aeb6-106">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) , który implementuje usługę kalkulatora.</span><span class="sxs-lookup"><span data-stu-id="5aeb6-106">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="5aeb6-107">`wsHttpBinding` Jest określona i skonfigurowana w plikach konfiguracji aplikacji dla klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="5aeb6-107">The `wsHttpBinding` is specified and configured in the application configuration files for the client and service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5aeb6-108">Procedura konfiguracji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="5aeb6-108">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5aeb6-109">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="5aeb6-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5aeb6-110">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="5aeb6-110">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5aeb6-111">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="5aeb6-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5aeb6-112">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="5aeb6-112">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsTransportSecurity`  
  
 <span data-ttu-id="5aeb6-113">Kod programu w przykładzie jest taki sam jak w przypadku usługi [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) .</span><span class="sxs-lookup"><span data-stu-id="5aeb6-113">The program code in the sample is identical to that of the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) service.</span></span> <span data-ttu-id="5aeb6-114">Przed skompilowaniem i uruchomieniem przykładu należy utworzyć certyfikat i przypisać go przy użyciu kreatora certyfikatu serwera sieci Web.</span><span class="sxs-lookup"><span data-stu-id="5aeb6-114">You must create a certificate and assign it by using the Web Server Certificate Wizard before building and running the sample.</span></span> <span data-ttu-id="5aeb6-115">Definicja punktu końcowego i definicja powiązania w ustawieniach pliku konfiguracji Włącz `Transport` tryb zabezpieczeń, jak pokazano w poniższej konfiguracji przykładowej dla klienta.</span><span class="sxs-lookup"><span data-stu-id="5aeb6-115">The endpoint definition and binding definition in the configuration file settings enable `Transport` security mode, as shown in the following sample configuration for the client.</span></span>  
  
```xml  
<system.serviceModel>  
  
    <client>  
      <!-- this endpoint has an https: address -->  
      <endpoint address="https://localhost/servicemodelsamples/service.svc" binding="wsHttpBinding" bindingConfiguration="Binding1" contract="Microsoft.Samples.TransportSecurity.ICalculator"/>  
    </client>  
  
    <bindings>  
      <wsHttpBinding>  
        <!-- configure wsHttpbinding with Transport security mode  
                   and clientCredentialType as None -->  
        <binding name="Binding1">  
          <security mode="Transport">  
            <transport clientCredentialType="None"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
  
  </system.serviceModel>  
```  
  
 <span data-ttu-id="5aeb6-116">Określony adres używa schematu https://.</span><span class="sxs-lookup"><span data-stu-id="5aeb6-116">The address specified uses the https:// scheme.</span></span> <span data-ttu-id="5aeb6-117">Konfiguracja powiązania ustawia tryb zabezpieczenia na `Transport`.</span><span class="sxs-lookup"><span data-stu-id="5aeb6-117">The binding configuration sets the security mode to `Transport`.</span></span> <span data-ttu-id="5aeb6-118">Ten sam tryb zabezpieczeń musi być określony w pliku Web. config usługi.</span><span class="sxs-lookup"><span data-stu-id="5aeb6-118">The same security mode must be specified in the service's Web.config file.</span></span>  
  
 <span data-ttu-id="5aeb6-119">Ponieważ certyfikat używany w tym przykładzie jest certyfikatem testowym utworzonym za pomocą Makecert. exe, podczas próby uzyskania dostępu do adresu https:, takiego jak https://localhost/servicemodelsamples/service.svc, z przeglądarki, pojawia się Alert zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="5aeb6-119">Because the certificate used in this sample is a test certificate created with Makecert.exe, a security alert appears when you try to access an https: address, such as https://localhost/servicemodelsamples/service.svc, from your browser.</span></span> <span data-ttu-id="5aeb6-120">Aby umożliwić klientowi Windows Communication Foundation (WCF) współpracujący z certyfikatem testowym, do klienta został dodany dodatkowy kod, aby pominąć alert zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="5aeb6-120">To allow the Windows Communication Foundation (WCF) client to work with a test certificate in place, some additional code has been added to the client to suppress the security alert.</span></span> <span data-ttu-id="5aeb6-121">Ten kod i Klasa towarzysząca nie są wymagane w przypadku korzystania z certyfikatów produkcyjnych.</span><span class="sxs-lookup"><span data-stu-id="5aeb6-121">This code, and the accompanying class, is not required when using production certificates.</span></span>  

```csharp
// This code is required only for test certificates like those created by Makecert.exe.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```

 <span data-ttu-id="5aeb6-122">Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="5aeb6-122">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="5aeb6-123">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.</span><span class="sxs-lookup"><span data-stu-id="5aeb6-123">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5aeb6-124">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="5aeb6-124">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="5aeb6-125">Zainstaluj ASP.NET 4,0 przy użyciu następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="5aeb6-125">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="5aeb6-126">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5aeb6-126">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="5aeb6-127">Upewnij się, że wykonano [instrukcje instalacji certyfikatu serwera Internet Information Services (IIS)](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span><span class="sxs-lookup"><span data-stu-id="5aeb6-127">Ensure that you have performed the [Internet Information Services (IIS) Server Certificate Installation Instructions](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span></span>  
  
4. <span data-ttu-id="5aeb6-128">Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5aeb6-128">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
5. <span data-ttu-id="5aeb6-129">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5aeb6-129">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
