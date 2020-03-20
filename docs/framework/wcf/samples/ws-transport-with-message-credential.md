---
title: Transport WS z poświadczeniami komunikatu
ms.date: 03/30/2017
ms.assetid: 0d092f3a-b309-439b-920b-66d8f46a0e3c
ms.openlocfilehash: 076d4490f6edc6efa8eeb50ae8baa23d5c4e369a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183143"
---
# <a name="ws-transport-with-message-credential"></a><span data-ttu-id="c43d9-102">Transport WS z poświadczeniami komunikatu</span><span class="sxs-lookup"><span data-stu-id="c43d9-102">WS Transport With Message Credential</span></span>
<span data-ttu-id="c43d9-103">W tym przykładzie pokazano użycie zabezpieczeń transportu SSL w połączeniu z poświadczeniami klienta przenoszonymi w wiadomości.</span><span class="sxs-lookup"><span data-stu-id="c43d9-103">This sample demonstrates the use of SSL transport security in combination with client credential being carried in the message.</span></span> <span data-ttu-id="c43d9-104">W tym przykładzie użyto `wsHttpBinding` powiązania.</span><span class="sxs-lookup"><span data-stu-id="c43d9-104">This sample uses the `wsHttpBinding` binding.</span></span>  
  
 <span data-ttu-id="c43d9-105">Domyślnie powiązanie zapewnia komunikację `wsHttpBinding` HTTP.</span><span class="sxs-lookup"><span data-stu-id="c43d9-105">By default, the `wsHttpBinding` binding provides HTTP communication.</span></span> <span data-ttu-id="c43d9-106">Po skonfigurowaniu zabezpieczeń transportu powiązanie obsługuje komunikację HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c43d9-106">When configured for transport security, the binding supports HTTPS communication.</span></span> <span data-ttu-id="c43d9-107">Protokół HTTPS zapewnia ochronę poufności i integralności wiadomości przesyłanych przez sieć.</span><span class="sxs-lookup"><span data-stu-id="c43d9-107">HTTPS provides confidentiality and integrity protection for the messages that are transmitted over the wire.</span></span> <span data-ttu-id="c43d9-108">Jednak zestaw mechanizmów uwierzytelniania, które mogą służyć do uwierzytelniania klienta do usługi jest ograniczona do tego, co obsługuje transport HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c43d9-108">However the set of authentication mechanisms that can be used to authenticate the client to the service is limited to what the HTTPS transport supports.</span></span> <span data-ttu-id="c43d9-109">Windows Communication Foundation (WCF) oferuje tryb `TransportWithMessageCredential` zabezpieczeń, który jest przeznaczony do przezwyciężenia tego ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="c43d9-109">Windows Communication Foundation (WCF) offers a `TransportWithMessageCredential` security mode that is designed to overcome this limitation.</span></span> <span data-ttu-id="c43d9-110">Po skonfigurowaniu tego trybu zabezpieczeń zabezpieczenia transportu są używane do zapewnienia poufności i integralności przesyłanych wiadomości oraz do uwierzytelniania usługi.</span><span class="sxs-lookup"><span data-stu-id="c43d9-110">When this security mode is configured, the transport security is used to provide confidentiality and integrity for the transmitted messages and to perform the service authentication.</span></span> <span data-ttu-id="c43d9-111">Jednak uwierzytelnianie klienta jest wykonywane przez umieszczenie poświadczenia klienta bezpośrednio w komunikacie.</span><span class="sxs-lookup"><span data-stu-id="c43d9-111">However, the client authentication is performed by putting the client credential directly in the message.</span></span> <span data-ttu-id="c43d9-112">Dzięki temu można użyć dowolnego typu poświadczeń, który jest obsługiwany przez tryb zabezpieczeń wiadomości dla uwierzytelniania klienta przy zachowaniu korzyści wydajności transportu trybu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="c43d9-112">This allows you to use any credential type that is supported by the message security mode for the client authentication while keeping the performance benefit of transport security mode.</span></span>  
  
 <span data-ttu-id="c43d9-113">W tym przykładzie `UserName` typ poświadczeń jest używany do uwierzytelniania klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="c43d9-113">In this sample, a `UserName` credential type is used to authenticate the client to the service.</span></span>  
  
 <span data-ttu-id="c43d9-114">Ten przykład jest oparty na [wprowadzenie,](../../../../docs/framework/wcf/samples/getting-started-sample.md) który implementuje usługę kalkulatora.</span><span class="sxs-lookup"><span data-stu-id="c43d9-114">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="c43d9-115">Powiązanie `wsHttpBinding` jest określone i skonfigurowane w plikach konfiguracji aplikacji dla klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="c43d9-115">The `wsHttpBinding` binding is specified and configured in the application configuration files for the client and service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c43d9-116">Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="c43d9-116">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="c43d9-117">Kod programu w przykładzie jest prawie identyczny z usługą [Wprowadzenie.](../../../../docs/framework/wcf/samples/getting-started-sample.md)</span><span class="sxs-lookup"><span data-stu-id="c43d9-117">The program code in the sample is almost identical to that of the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) service.</span></span> <span data-ttu-id="c43d9-118">Istnieje jedna dodatkowa operacja przewidziana `GetCallerIdentity`w umowie serwisowej - .</span><span class="sxs-lookup"><span data-stu-id="c43d9-118">There is one additional operation provided by the service contract - `GetCallerIdentity`.</span></span> <span data-ttu-id="c43d9-119">Ta operacja zwraca nazwę tożsamości wywołującego do wywołującego.</span><span class="sxs-lookup"><span data-stu-id="c43d9-119">This operation returns the name of the caller's identity to the caller.</span></span>  

```csharp
public string GetCallerIdentity()  
{  
    // Use ServiceSecurityContext.WindowsIdentity to get the name of the caller.  
    return ServiceSecurityContext.Current.WindowsIdentity.Name;  
}  
```

 <span data-ttu-id="c43d9-120">Przed utworzeniem i uruchomieniem przykładu należy utworzyć certyfikat i przypisać go przy użyciu Kreatora certyfikatów serwera sieci Web.</span><span class="sxs-lookup"><span data-stu-id="c43d9-120">You must create a certificate and assign it by using the Web Server Certificate Wizard before building and running the sample.</span></span> <span data-ttu-id="c43d9-121">Definicja punktu końcowego i definicja `TransportWithMessageCredential` powiązania w ustawieniach pliku konfiguracji włączyć tryb zabezpieczeń, jak pokazano w poniższej konfiguracji przykładowej dla klienta.</span><span class="sxs-lookup"><span data-stu-id="c43d9-121">The endpoint definition and binding definition in the configuration file settings enable `TransportWithMessageCredential` security mode, as shown in the following sample configuration for the client.</span></span>  
  
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
  
 <span data-ttu-id="c43d9-122">Podany adres używa schematu https://.</span><span class="sxs-lookup"><span data-stu-id="c43d9-122">The address specified uses the https:// scheme.</span></span> <span data-ttu-id="c43d9-123">Konfiguracja powiązania ustawia tryb `TransportWithMessageCredential`zabezpieczeń na .</span><span class="sxs-lookup"><span data-stu-id="c43d9-123">The binding configuration sets the security mode to `TransportWithMessageCredential`.</span></span> <span data-ttu-id="c43d9-124">Ten sam tryb zabezpieczeń musi być określony w pliku Web.config usługi.</span><span class="sxs-lookup"><span data-stu-id="c43d9-124">The same security mode must be specified in the service's Web.config file.</span></span>  
  
 <span data-ttu-id="c43d9-125">Ponieważ certyfikat używany w tym przykładzie jest certyfikatem testowym utworzonym za pomocą pliku Makecert.exe, `https://localhost/servicemodelsamples/service.svc`podczas próby uzyskania dostępu do adresu https:, takiego jak , z przeglądarki, pojawia się alert zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="c43d9-125">Because the certificate used in this sample is a test certificate created with Makecert.exe, a security alert appears when you try to access an https: address, such as  `https://localhost/servicemodelsamples/service.svc`, from your browser.</span></span> <span data-ttu-id="c43d9-126">Aby umożliwić klientowi WCF pracę z certyfikatem testowym w miejscu, dodano do klienta dodatkowy kod w celu powstrzymania alertu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="c43d9-126">To allow the WCF client to work with a test certificate in place, some additional code has been added to the client to suppress the security alert.</span></span> <span data-ttu-id="c43d9-127">Ten kod i towarzysząca mu klasa nie jest wymagana podczas korzystania z certyfikatów produkcyjnych.</span><span class="sxs-lookup"><span data-stu-id="c43d9-127">This code, and the accompanying class, is not required when using production certificates.</span></span>  

```csharp
// WARNING: This code is only needed for test certificates such as those created by makecert. It is
// not recommended for production code.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```
  
 <span data-ttu-id="c43d9-128">Po uruchomieniu próbki żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="c43d9-128">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="c43d9-129">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="c43d9-129">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c43d9-130">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="c43d9-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="c43d9-131">Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c43d9-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="c43d9-132">Upewnij się, że wykonano [instrukcje instalacji certyfikatów serwera usług internetowych (IIS).](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md)</span><span class="sxs-lookup"><span data-stu-id="c43d9-132">Ensure that you have performed the [Internet Information Services (IIS) Server Certificate Installation Instructions](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span></span>  
  
3. <span data-ttu-id="c43d9-133">Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c43d9-133">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="c43d9-134">Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c43d9-134">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
