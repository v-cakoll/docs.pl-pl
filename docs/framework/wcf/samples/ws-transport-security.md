---
title: Zabezpieczenia transportu WS
ms.date: 03/30/2017
ms.assetid: 33a20358-5e1b-458a-a6a9-15753bc7b99b
ms.openlocfilehash: c5a3b6df570dcdeae1c36c71ae772c30ec31178b
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832102"
---
# <a name="ws-transport-security"></a><span data-ttu-id="c145a-102">Zabezpieczenia transportu WS</span><span class="sxs-lookup"><span data-stu-id="c145a-102">WS Transport Security</span></span>
<span data-ttu-id="c145a-103">Niniejszy przykład pokazuje użycie protokołu SSL zabezpieczenia transportu z <xref:System.ServiceModel.WSHttpBinding> powiązania.</span><span class="sxs-lookup"><span data-stu-id="c145a-103">This sample demonstrates the use of SSL transport security with the <xref:System.ServiceModel.WSHttpBinding> binding.</span></span> <span data-ttu-id="c145a-104">Domyślnie `wsHttpBinding` powiązania zapewnia komunikację HTTP.</span><span class="sxs-lookup"><span data-stu-id="c145a-104">By default, the `wsHttpBinding` binding provides HTTP communication.</span></span> <span data-ttu-id="c145a-105">Po skonfigurowaniu zabezpieczeń transportu powiązanie obsługuje komunikację HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c145a-105">When configured for transport security, the binding supports HTTPS communication.</span></span> <span data-ttu-id="c145a-106">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) implementującej usługi kalkulatora.</span><span class="sxs-lookup"><span data-stu-id="c145a-106">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="c145a-107">`wsHttpBinding` Jest określona i skonfigurowane w plikach konfiguracji aplikacji dla klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="c145a-107">The `wsHttpBinding` is specified and configured in the application configuration files for the client and service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c145a-108">Procedury i kompilacja instrukcje dotyczące konfiguracji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="c145a-108">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c145a-109">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="c145a-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c145a-110">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="c145a-110">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c145a-111">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="c145a-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c145a-112">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="c145a-112">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsTransportSecurity`  
  
 <span data-ttu-id="c145a-113">Kod programu, w przykładzie jest taka sama jak w przypadku [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) usługi.</span><span class="sxs-lookup"><span data-stu-id="c145a-113">The program code in the sample is identical to that of the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) service.</span></span> <span data-ttu-id="c145a-114">Należy utworzyć certyfikat i przypisz go za pomocą kreatora certyfikatu serwera sieci Web przed kompilowanie i uruchamianie przykładu.</span><span class="sxs-lookup"><span data-stu-id="c145a-114">You must create a certificate and assign it by using the Web Server Certificate Wizard before building and running the sample.</span></span> <span data-ttu-id="c145a-115">Definicja punktu końcowego i definicji powiązania w konfiguracji pliku ustawienia umożliwiające `Transport` tryb zabezpieczeń, jak pokazano w poniższym Przykładowa konfiguracja klienta.</span><span class="sxs-lookup"><span data-stu-id="c145a-115">The endpoint definition and binding definition in the configuration file settings enable `Transport` security mode, as shown in the following sample configuration for the client.</span></span>  
  
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
  
 <span data-ttu-id="c145a-116">Określony adres wykorzystuje schemat https://.</span><span class="sxs-lookup"><span data-stu-id="c145a-116">The address specified uses the https:// scheme.</span></span> <span data-ttu-id="c145a-117">Konfiguracja powiązania Ustawia tryb zabezpieczeń `Transport`.</span><span class="sxs-lookup"><span data-stu-id="c145a-117">The binding configuration sets the security mode to `Transport`.</span></span> <span data-ttu-id="c145a-118">Taki sam tryb zabezpieczeń należy określić w pliku Web.config tej usługi.</span><span class="sxs-lookup"><span data-stu-id="c145a-118">The same security mode must be specified in the service's Web.config file.</span></span>  
  
 <span data-ttu-id="c145a-119">Ponieważ certyfikat używany w tym przykładzie jest utworzone za pomocą Makecert.exe certyfikat testowy, alert zabezpieczeń jest wyświetlany, gdy próbują uzyskać dostęp przy użyciu protokołu https: adres, takie jak https://localhost/servicemodelsamples/service.svc, z poziomu przeglądarki.</span><span class="sxs-lookup"><span data-stu-id="c145a-119">Because the certificate used in this sample is a test certificate created with Makecert.exe, a security alert appears when you try to access an https: address, such as https://localhost/servicemodelsamples/service.svc, from your browser.</span></span> <span data-ttu-id="c145a-120">Aby umożliwić klientowi usług Windows Communication Foundation (WCF) do pracy z certyfikatem testowym w miejscu, dodano dodatkowy kod klienta dla pomijania alertu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="c145a-120">To allow the Windows Communication Foundation (WCF) client to work with a test certificate in place, some additional code has been added to the client to suppress the security alert.</span></span> <span data-ttu-id="c145a-121">Ten kod i towarzyszące klasy, nie jest wymagane, podczas korzystania z certyfikatów w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="c145a-121">This code, and the accompanying class, is not required when using production certificates.</span></span>  

```csharp
// This code is required only for test certificates like those created by Makecert.exe.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```

 <span data-ttu-id="c145a-122">Po uruchomieniu przykładu, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="c145a-122">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="c145a-123">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="c145a-123">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c145a-124">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="c145a-124">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="c145a-125">Zainstaluj [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0, używając następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="c145a-125">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="c145a-126">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c145a-126">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="c145a-127">Upewnij się, że wykonano [instrukcje instalacji certyfikatu serwera Internet Information Services (IIS)](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span><span class="sxs-lookup"><span data-stu-id="c145a-127">Ensure that you have performed the [Internet Information Services (IIS) Server Certificate Installation Instructions](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span></span>  
  
4.  <span data-ttu-id="c145a-128">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c145a-128">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
5.  <span data-ttu-id="c145a-129">Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c145a-129">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
