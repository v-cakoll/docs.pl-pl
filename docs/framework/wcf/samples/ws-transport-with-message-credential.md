---
title: "Transport WS z poświadczeniami komunikatu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d092f3a-b309-439b-920b-66d8f46a0e3c
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 858ed1b3d7a1114a475e9479e4398ce7896f4bd4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ws-transport-with-message-credential"></a><span data-ttu-id="2979c-102">Transport WS z poświadczeniami komunikatu</span><span class="sxs-lookup"><span data-stu-id="2979c-102">WS Transport With Message Credential</span></span>
<span data-ttu-id="2979c-103">W przykładzie pokazano użycie zabezpieczenia transportowe protokołu SSL w połączeniu z poświadczeniami klienta odbywa się w komunikacie.</span><span class="sxs-lookup"><span data-stu-id="2979c-103">This sample demonstrates the use of SSL transport security in combination with client credential being carried in the message.</span></span> <span data-ttu-id="2979c-104">W przykładzie użyto `wsHttpBinding` powiązania.</span><span class="sxs-lookup"><span data-stu-id="2979c-104">This sample uses the `wsHttpBinding` binding.</span></span>  
  
 <span data-ttu-id="2979c-105">Domyślnie `wsHttpBinding` powiązania zapewnia komunikację HTTP.</span><span class="sxs-lookup"><span data-stu-id="2979c-105">By default, the `wsHttpBinding` binding provides HTTP communication.</span></span> <span data-ttu-id="2979c-106">Gdy skonfigurowany pod kątem zabezpieczeń transportu, wiązanie obsługuje komunikację HTTPS.</span><span class="sxs-lookup"><span data-stu-id="2979c-106">When configured for transport security, the binding supports HTTPS communication.</span></span> <span data-ttu-id="2979c-107">Protokół HTTPS oferuje poufności i ochrony integralność komunikatów, które są przesyłane przez sieć.</span><span class="sxs-lookup"><span data-stu-id="2979c-107">HTTPS provides confidentiality and integrity protection for the messages that are transmitted over the wire.</span></span> <span data-ttu-id="2979c-108">Jednakże zestaw mechanizmów uwierzytelniania, które mogą służyć do uwierzytelniania klienta do usługi jest ograniczone do obsługuje transportu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="2979c-108">However the set of authentication mechanisms that can be used to authenticate the client to the service is limited to what the HTTPS transport supports.</span></span> [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="2979c-109">oferuje `TransportWithMessageCredential` tryb zabezpieczeń, której celem jest obejść to ograniczenie.</span><span class="sxs-lookup"><span data-stu-id="2979c-109"> offers a `TransportWithMessageCredential` security mode that is designed to overcome this limitation.</span></span> <span data-ttu-id="2979c-110">Po skonfigurowaniu tego trybu zabezpieczeń transportu używane zabezpieczenia zapewnienie poufności i integralności wiadomości przesyłane i do uwierzytelniania usługi.</span><span class="sxs-lookup"><span data-stu-id="2979c-110">When this security mode is configured, the transport security is used to provide confidentiality and integrity for the transmitted messages and to perform the service authentication.</span></span> <span data-ttu-id="2979c-111">Jednak uwierzytelnianie klienta jest wykonywane przez wprowadzenie poświadczeń klienta bezpośrednio w komunikacie.</span><span class="sxs-lookup"><span data-stu-id="2979c-111">However, the client authentication is performed by putting the client credential directly in the message.</span></span> <span data-ttu-id="2979c-112">Dzięki temu można użyć dowolnego typu poświadczeń, która jest obsługiwana przez tryb zabezpieczeń wiadomości do uwierzytelniania klientów przy zachowaniu wydajności zaletą tryb zabezpieczeń transport.</span><span class="sxs-lookup"><span data-stu-id="2979c-112">This allows you to use any credential type that is supported by the message security mode for the client authentication while keeping the performance benefit of transport security mode.</span></span>  
  
 <span data-ttu-id="2979c-113">W tym przykładzie `UserName` typ poświadczeń jest używany do uwierzytelniania klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="2979c-113">In this sample, a `UserName` credential type is used to authenticate the client to the service.</span></span>  
  
 <span data-ttu-id="2979c-114">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) implementującej usługi Kalkulator.</span><span class="sxs-lookup"><span data-stu-id="2979c-114">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="2979c-115">`wsHttpBinding` Powiązania jest określona i skonfigurowany w plikach konfiguracji aplikacji dla klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="2979c-115">The `wsHttpBinding` binding is specified and configured in the application configuration files for the client and service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2979c-116">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="2979c-116">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="2979c-117">Kod programu w próbce jest niemal identyczna ze [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) usługi.</span><span class="sxs-lookup"><span data-stu-id="2979c-117">The program code in the sample is almost identical to that of the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) service.</span></span> <span data-ttu-id="2979c-118">Brak jednej operacji dodatkowe podał kontraktu usługi - `GetCallerIdentity`.</span><span class="sxs-lookup"><span data-stu-id="2979c-118">There is one additional operation provided by the service contract - `GetCallerIdentity`.</span></span> <span data-ttu-id="2979c-119">Ta operacja zwraca nazwę tożsamości obiektu wywołującego do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="2979c-119">This operation returns the name of the caller's identity to the caller.</span></span>  
  
```  
public string GetCallerIdentity()  
{  
    // Use ServiceSecurityContext.WindowsIdentity to get the name of the caller.  
    return ServiceSecurityContext.Current.WindowsIdentity.Name;  
}  
```  
  
 <span data-ttu-id="2979c-120">Należy utworzyć certyfikat i przypisz go za pomocą kreatora certyfikatu serwera sieci Web przed tworzenia i uruchamiania przykładowych.</span><span class="sxs-lookup"><span data-stu-id="2979c-120">You must create a certificate and assign it by using the Web Server Certificate Wizard before building and running the sample.</span></span> <span data-ttu-id="2979c-121">Definicja punktu końcowego i definicji powiązania w konfiguracji pliku ustawienia umożliwiające `TransportWithMessageCredential` tryb zabezpieczeń, jak pokazano w poniższych Przykładowa konfiguracja klienta.</span><span class="sxs-lookup"><span data-stu-id="2979c-121">The endpoint definition and binding definition in the configuration file settings enable `TransportWithMessageCredential` security mode, as shown in the following sample configuration for the client.</span></span>  
  
```xml  
<system.serviceModel>  
  <client>  
    <endpoint name=""  
              address="https://localhost/servicemodelsamples/service.svc"   
              binding="wsHttpBinding"   
              bindingConfiguration="Binding1"   
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </client>  
  
  <bindings>  
    <wsHttpBinding>  
      <!--   
        This configuration defines the security mode as TransportWithMessageCredential.  
        and the clientCredentialType as UserName.  
        -->  
      <binding name="Binding1">  
        <security mode ="TransportWithMessageCredential">  
          <message clientCredentialType="UserName" />  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="2979c-122">Określony adres wykorzystuje schemat https://.</span><span class="sxs-lookup"><span data-stu-id="2979c-122">The address specified uses the https:// scheme.</span></span> <span data-ttu-id="2979c-123">Konfiguracja powiązania Ustawia tryb zabezpieczeń `TransportWithMessageCredential`.</span><span class="sxs-lookup"><span data-stu-id="2979c-123">The binding configuration sets the security mode to `TransportWithMessageCredential`.</span></span> <span data-ttu-id="2979c-124">Należy określić ten sam tryb zabezpieczeń w pliku Web.config tej usługi.</span><span class="sxs-lookup"><span data-stu-id="2979c-124">The same security mode must be specified in the service's Web.config file.</span></span>  
  
 <span data-ttu-id="2979c-125">Ponieważ certyfikat użyty w tym przykładzie jest certyfikatu testowego utworzone za pomocą Makecert.exe, alert zabezpieczeń zostanie wyświetlony podczas próby uzyskania dostępu https: adres, takie jak https://localhost/servicemodelsamples/service.svc z przeglądarki.</span><span class="sxs-lookup"><span data-stu-id="2979c-125">Because the certificate used in this sample is a test certificate created with Makecert.exe, a security alert appears when you try to access an https: address, such as https://localhost/servicemodelsamples/service.svc, from your browser.</span></span> <span data-ttu-id="2979c-126">Aby umożliwić [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta, aby pracować przy użyciu certyfikatu testowego w miejscu, dodatkowy kod został dodany do klienta dla pomijania alertu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="2979c-126">To allow the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client to work with a test certificate in place, some additional code has been added to the client to suppress the security alert.</span></span> <span data-ttu-id="2979c-127">Ten kod i towarzyszące klasy nie jest wymagana, podczas korzystania z certyfikatów w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="2979c-127">This code, and the accompanying class, is not required when using production certificates.</span></span>  
  
```  
// WARNING: This code is only needed for test certificates such as those created by makecert. It is   
// not recommended for production code.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```  
  
 <span data-ttu-id="2979c-128">Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="2979c-128">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="2979c-129">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="2979c-129">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Username authentication required.  
Provide a valid machine or domain account. [domain\\user]  
   Enter username:   
YourDomainName\YourAccountName  
   Enter password:   
********  
YourDomainName\YourAccountName  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2979c-130">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="2979c-130">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="2979c-131">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2979c-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="2979c-132">Upewnij się, że wykonano procedurę [instrukcje instalacji certyfikatu serwera Internet Information Services (IIS)](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span><span class="sxs-lookup"><span data-stu-id="2979c-132">Ensure that you have performed the [Internet Information Services (IIS) Server Certificate Installation Instructions](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span></span>  
  
3.  <span data-ttu-id="2979c-133">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2979c-133">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="2979c-134">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2979c-134">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2979c-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2979c-135">See Also</span></span>
