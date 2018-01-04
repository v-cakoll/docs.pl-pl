---
title: Zabezpieczenia transportu WS
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33a20358-5e1b-458a-a6a9-15753bc7b99b
caps.latest.revision: "22"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 3435eab63cf745607b6ecf61b12123966f80442b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ws-transport-security"></a><span data-ttu-id="52492-102">Zabezpieczenia transportu WS</span><span class="sxs-lookup"><span data-stu-id="52492-102">WS Transport Security</span></span>
<span data-ttu-id="52492-103">W tym przykładzie przedstawiono użycie zabezpieczenia transportowe protokołu SSL z <xref:System.ServiceModel.WSHttpBinding> powiązania.</span><span class="sxs-lookup"><span data-stu-id="52492-103">This sample demonstrates the use of SSL transport security with the <xref:System.ServiceModel.WSHttpBinding> binding.</span></span> <span data-ttu-id="52492-104">Domyślnie `wsHttpBinding` powiązania zapewnia komunikację HTTP.</span><span class="sxs-lookup"><span data-stu-id="52492-104">By default, the `wsHttpBinding` binding provides HTTP communication.</span></span> <span data-ttu-id="52492-105">Gdy skonfigurowany pod kątem zabezpieczeń transportu, wiązanie obsługuje komunikację HTTPS.</span><span class="sxs-lookup"><span data-stu-id="52492-105">When configured for transport security, the binding supports HTTPS communication.</span></span> <span data-ttu-id="52492-106">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) implementującej usługi Kalkulator.</span><span class="sxs-lookup"><span data-stu-id="52492-106">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="52492-107">`wsHttpBinding` Jest określona i skonfigurowany w plikach konfiguracji aplikacji dla klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="52492-107">The `wsHttpBinding` is specified and configured in the application configuration files for the client and service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="52492-108">Procedury i kompilacji instrukcje dotyczące konfiguracji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="52492-108">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="52492-109">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="52492-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="52492-110">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="52492-110">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="52492-111">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="52492-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="52492-112">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="52492-112">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsTransportSecurity`  
  
 <span data-ttu-id="52492-113">Kod programu w próbce jest identyczna ze [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) usługi.</span><span class="sxs-lookup"><span data-stu-id="52492-113">The program code in the sample is identical to that of the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) service.</span></span> <span data-ttu-id="52492-114">Należy utworzyć certyfikat i przypisz go za pomocą kreatora certyfikatu serwera sieci Web przed tworzenia i uruchamiania przykładowych.</span><span class="sxs-lookup"><span data-stu-id="52492-114">You must create a certificate and assign it by using the Web Server Certificate Wizard before building and running the sample.</span></span> <span data-ttu-id="52492-115">Definicja punktu końcowego i definicji powiązania w konfiguracji pliku ustawienia umożliwiające `Transport` tryb zabezpieczeń, jak pokazano w poniższych Przykładowa konfiguracja klienta.</span><span class="sxs-lookup"><span data-stu-id="52492-115">The endpoint definition and binding definition in the configuration file settings enable `Transport` security mode, as shown in the following sample configuration for the client.</span></span>  
  
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
  
 <span data-ttu-id="52492-116">Określony adres wykorzystuje schemat https://.</span><span class="sxs-lookup"><span data-stu-id="52492-116">The address specified uses the https:// scheme.</span></span> <span data-ttu-id="52492-117">Konfiguracja powiązania Ustawia tryb zabezpieczeń `Transport`.</span><span class="sxs-lookup"><span data-stu-id="52492-117">The binding configuration sets the security mode to `Transport`.</span></span> <span data-ttu-id="52492-118">Należy określić ten sam tryb zabezpieczeń w pliku Web.config tej usługi.</span><span class="sxs-lookup"><span data-stu-id="52492-118">The same security mode must be specified in the service's Web.config file.</span></span>  
  
 <span data-ttu-id="52492-119">Ponieważ certyfikat użyty w tym przykładzie jest certyfikatu testowego utworzone za pomocą Makecert.exe, alert zabezpieczeń zostanie wyświetlony podczas próby uzyskania dostępu https: adres, takie jak https://localhost/servicemodelsamples/service.svc z przeglądarki.</span><span class="sxs-lookup"><span data-stu-id="52492-119">Because the certificate used in this sample is a test certificate created with Makecert.exe, a security alert appears when you try to access an https: address, such as https://localhost/servicemodelsamples/service.svc, from your browser.</span></span> <span data-ttu-id="52492-120">Aby umożliwić [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] klienta, aby pracować przy użyciu certyfikatu testowego w miejscu, dodatkowy kod został dodany do klienta dla pomijania alertu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="52492-120">To allow the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client to work with a test certificate in place, some additional code has been added to the client to suppress the security alert.</span></span> <span data-ttu-id="52492-121">Ten kod i towarzyszące klasy nie jest wymagana, podczas korzystania z certyfikatów w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="52492-121">This code, and the accompanying class, is not required when using production certificates.</span></span>  
  
```  
// This code is required only for test certificates like those created by Makecert.exe.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```  
  
 <span data-ttu-id="52492-122">Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="52492-122">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="52492-123">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="52492-123">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="52492-124">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="52492-124">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="52492-125">Zainstaluj [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 za pomocą następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="52492-125">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="52492-126">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="52492-126">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="52492-127">Upewnij się, że wykonano procedurę [instrukcje instalacji certyfikatu serwera Internet Information Services (IIS)](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span><span class="sxs-lookup"><span data-stu-id="52492-127">Ensure that you have performed the [Internet Information Services (IIS) Server Certificate Installation Instructions](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span></span>  
  
4.  <span data-ttu-id="52492-128">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="52492-128">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
5.  <span data-ttu-id="52492-129">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="52492-129">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52492-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="52492-130">See Also</span></span>
