---
title: Transport WS z poświadczeniami komunikatu
ms.date: 03/30/2017
ms.assetid: 0d092f3a-b309-439b-920b-66d8f46a0e3c
ms.openlocfilehash: fb923fd4d7271f7f364d24743c3f9f6393ef8f9f
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/01/2019
ms.locfileid: "57200588"
---
# <a name="ws-transport-with-message-credential"></a><span data-ttu-id="41b09-102">Transport WS z poświadczeniami komunikatu</span><span class="sxs-lookup"><span data-stu-id="41b09-102">WS Transport With Message Credential</span></span>
<span data-ttu-id="41b09-103">Niniejszy przykład pokazuje korzystanie z zabezpieczeń transportu protokołu SSL w połączeniu z poświadczeniami klienta, które są przenoszone w komunikacie.</span><span class="sxs-lookup"><span data-stu-id="41b09-103">This sample demonstrates the use of SSL transport security in combination with client credential being carried in the message.</span></span> <span data-ttu-id="41b09-104">W tym przykładzie użyto `wsHttpBinding` powiązania.</span><span class="sxs-lookup"><span data-stu-id="41b09-104">This sample uses the `wsHttpBinding` binding.</span></span>  
  
 <span data-ttu-id="41b09-105">Domyślnie `wsHttpBinding` powiązania zapewnia komunikację HTTP.</span><span class="sxs-lookup"><span data-stu-id="41b09-105">By default, the `wsHttpBinding` binding provides HTTP communication.</span></span> <span data-ttu-id="41b09-106">Po skonfigurowaniu zabezpieczeń transportu powiązanie obsługuje komunikację HTTPS.</span><span class="sxs-lookup"><span data-stu-id="41b09-106">When configured for transport security, the binding supports HTTPS communication.</span></span> <span data-ttu-id="41b09-107">Protokół HTTPS oferuje poufność i ochrona integralności wiadomości, które są przesyłane przez sieć.</span><span class="sxs-lookup"><span data-stu-id="41b09-107">HTTPS provides confidentiality and integrity protection for the messages that are transmitted over the wire.</span></span> <span data-ttu-id="41b09-108">Jednak zestaw mechanizmów uwierzytelniania, które mogą służyć do uwierzytelniania klienta do usługi jest ograniczona do obsługuje transportu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="41b09-108">However the set of authentication mechanisms that can be used to authenticate the client to the service is limited to what the HTTPS transport supports.</span></span> <span data-ttu-id="41b09-109">Windows Communication Foundation (WCF) oferuje `TransportWithMessageCredential` tryb zabezpieczeń, której celem jest to ograniczenie.</span><span class="sxs-lookup"><span data-stu-id="41b09-109">Windows Communication Foundation (WCF) offers a `TransportWithMessageCredential` security mode that is designed to overcome this limitation.</span></span> <span data-ttu-id="41b09-110">Po skonfigurowaniu tego trybu zabezpieczeń zabezpieczeń transportu jest używany, zapewnienie poufności i integralności przesyłanych wiadomości i do wykonywania uwierzytelniania usługi.</span><span class="sxs-lookup"><span data-stu-id="41b09-110">When this security mode is configured, the transport security is used to provide confidentiality and integrity for the transmitted messages and to perform the service authentication.</span></span> <span data-ttu-id="41b09-111">Jednak uwierzytelnianie klienta odbywa się przez umieszczanie poświadczeń klienta bezpośrednio w wiadomości.</span><span class="sxs-lookup"><span data-stu-id="41b09-111">However, the client authentication is performed by putting the client credential directly in the message.</span></span> <span data-ttu-id="41b09-112">Dzięki temu można używać dowolnego typu poświadczeń, który jest obsługiwany przez trybu zabezpieczenia wiadomości do uwierzytelniania klientów przy zachowaniu zalet wydajności tryb zabezpieczeń transport.</span><span class="sxs-lookup"><span data-stu-id="41b09-112">This allows you to use any credential type that is supported by the message security mode for the client authentication while keeping the performance benefit of transport security mode.</span></span>  
  
 <span data-ttu-id="41b09-113">W tym przykładzie `UserName` typ poświadczeń jest używany do uwierzytelniania klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="41b09-113">In this sample, a `UserName` credential type is used to authenticate the client to the service.</span></span>  
  
 <span data-ttu-id="41b09-114">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) implementującej usługi kalkulatora.</span><span class="sxs-lookup"><span data-stu-id="41b09-114">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="41b09-115">`wsHttpBinding` Powiązania jest określona i skonfigurowany w plikach konfiguracji aplikacji dla klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="41b09-115">The `wsHttpBinding` binding is specified and configured in the application configuration files for the client and service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="41b09-116">Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="41b09-116">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="41b09-117">Kod programu, w przykładzie jest niemal identyczny z [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) usługi.</span><span class="sxs-lookup"><span data-stu-id="41b09-117">The program code in the sample is almost identical to that of the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) service.</span></span> <span data-ttu-id="41b09-118">Istnieje jedna operacja dodatkowe dostarczone przez kontrakt usługi - `GetCallerIdentity`.</span><span class="sxs-lookup"><span data-stu-id="41b09-118">There is one additional operation provided by the service contract - `GetCallerIdentity`.</span></span> <span data-ttu-id="41b09-119">Ta operacja zwraca Nazwa tożsamości elementu wywołującego do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="41b09-119">This operation returns the name of the caller's identity to the caller.</span></span>  

```csharp
public string GetCallerIdentity()  
{  
    // Use ServiceSecurityContext.WindowsIdentity to get the name of the caller.  
    return ServiceSecurityContext.Current.WindowsIdentity.Name;  
}  
```

 <span data-ttu-id="41b09-120">Należy utworzyć certyfikat i przypisz go za pomocą kreatora certyfikatu serwera sieci Web przed kompilowanie i uruchamianie przykładu.</span><span class="sxs-lookup"><span data-stu-id="41b09-120">You must create a certificate and assign it by using the Web Server Certificate Wizard before building and running the sample.</span></span> <span data-ttu-id="41b09-121">Definicja punktu końcowego i definicji powiązania w konfiguracji pliku ustawienia umożliwiające `TransportWithMessageCredential` tryb zabezpieczeń, jak pokazano w poniższym Przykładowa konfiguracja klienta.</span><span class="sxs-lookup"><span data-stu-id="41b09-121">The endpoint definition and binding definition in the configuration file settings enable `TransportWithMessageCredential` security mode, as shown in the following sample configuration for the client.</span></span>  
  
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
  
 <span data-ttu-id="41b09-122">Określony adres wykorzystuje schemat https://.</span><span class="sxs-lookup"><span data-stu-id="41b09-122">The address specified uses the https:// scheme.</span></span> <span data-ttu-id="41b09-123">Konfiguracja powiązania Ustawia tryb zabezpieczeń `TransportWithMessageCredential`.</span><span class="sxs-lookup"><span data-stu-id="41b09-123">The binding configuration sets the security mode to `TransportWithMessageCredential`.</span></span> <span data-ttu-id="41b09-124">Taki sam tryb zabezpieczeń należy określić w pliku Web.config tej usługi.</span><span class="sxs-lookup"><span data-stu-id="41b09-124">The same security mode must be specified in the service's Web.config file.</span></span>  
  
 <span data-ttu-id="41b09-125">Ponieważ certyfikat używany w tym przykładzie jest utworzone za pomocą Makecert.exe certyfikat testowy, alert zabezpieczeń jest wyświetlany, gdy próbują uzyskać dostęp przy użyciu protokołu https: adres, takie jak `https://localhost/servicemodelsamples/service.svc`, z poziomu przeglądarki.</span><span class="sxs-lookup"><span data-stu-id="41b09-125">Because the certificate used in this sample is a test certificate created with Makecert.exe, a security alert appears when you try to access an https: address, such as  `https://localhost/servicemodelsamples/service.svc`, from your browser.</span></span> <span data-ttu-id="41b09-126">Aby zezwolić na klienta platformy WCF do pracy z certyfikatem testowym w miejscu, dodano dodatkowy kod klienta dla pomijania alertu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="41b09-126">To allow the WCF client to work with a test certificate in place, some additional code has been added to the client to suppress the security alert.</span></span> <span data-ttu-id="41b09-127">Ten kod i towarzyszące klasy, nie jest wymagane, podczas korzystania z certyfikatów w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="41b09-127">This code, and the accompanying class, is not required when using production certificates.</span></span>  

```csharp
// WARNING: This code is only needed for test certificates such as those created by makecert. It is   
// not recommended for production code.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```
  
 <span data-ttu-id="41b09-128">Po uruchomieniu przykładu, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="41b09-128">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="41b09-129">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="41b09-129">Press ENTER in the client window to shut down the client.</span></span>  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="41b09-130">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="41b09-130">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="41b09-131">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="41b09-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="41b09-132">Upewnij się, że wykonano [instrukcje instalacji certyfikatu serwera Internet Information Services (IIS)](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span><span class="sxs-lookup"><span data-stu-id="41b09-132">Ensure that you have performed the [Internet Information Services (IIS) Server Certificate Installation Instructions](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span></span>  
  
3.  <span data-ttu-id="41b09-133">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="41b09-133">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="41b09-134">Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="41b09-134">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41b09-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="41b09-135">See also</span></span>
