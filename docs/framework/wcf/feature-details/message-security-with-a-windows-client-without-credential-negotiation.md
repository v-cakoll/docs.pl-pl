---
title: Zabezpieczanie komunikatów za pomocą klienta systemu Windows bez negocjowania poświadczeń
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fc07a26c-cbee-41c5-8fb0-329085fef749
ms.openlocfilehash: 7845bc45d0baecb07e4c03531f21d900c4e23bf7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595248"
---
# <a name="message-security-with-a-windows-client-without-credential-negotiation"></a><span data-ttu-id="8b4ef-102">Zabezpieczanie komunikatów za pomocą klienta systemu Windows bez negocjowania poświadczeń</span><span class="sxs-lookup"><span data-stu-id="8b4ef-102">Message Security with a Windows Client without Credential Negotiation</span></span>

<span data-ttu-id="8b4ef-103">W poniższym scenariuszu przedstawiono klienta i usługę Windows Communication Foundation (WCF), zabezpieczone przez protokół Kerberos.</span><span class="sxs-lookup"><span data-stu-id="8b4ef-103">The following scenario shows a Windows Communication Foundation (WCF) client and service secured by the Kerberos protocol.</span></span>

<span data-ttu-id="8b4ef-104">Zarówno usługa, jak i klient znajdują się w tej samej domenie lub domenach zaufanych.</span><span class="sxs-lookup"><span data-stu-id="8b4ef-104">Both the service and the client are in the same domain or trusted domains.</span></span>

> [!NOTE]
> <span data-ttu-id="8b4ef-105">Różnica między tym scenariuszem a [zabezpieczeniami komunikatów klienta systemu Windows](message-security-with-a-windows-client.md) polega na tym, że ten scenariusz nie negocjuje poświadczeń usługi z usługą przed wysłaniem komunikatu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8b4ef-105">The difference between this scenario and [Message Security with a Windows Client](message-security-with-a-windows-client.md) is that this scenario does not negotiate the service credential with the service prior to sending the application message.</span></span> <span data-ttu-id="8b4ef-106">Ponadto, ponieważ wymaga to protokołu Kerberos, ten scenariusz wymaga środowiska domeny systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="8b4ef-106">Additionally, because this requires the Kerberos protocol, this scenario requires a Windows domain environment.</span></span>

<span data-ttu-id="8b4ef-107">![Zabezpieczenia komunikatów bez negocjowania poświadczeń](media/0c9f9baa-2439-4ef9-92f4-43c242d85d0d.gif "0c9f9baa-2439-4ef9-92f4-43c242d85d0d")</span><span class="sxs-lookup"><span data-stu-id="8b4ef-107">![Message security without credential negotiation](media/0c9f9baa-2439-4ef9-92f4-43c242d85d0d.gif "0c9f9baa-2439-4ef9-92f4-43c242d85d0d")</span></span>

|<span data-ttu-id="8b4ef-108">Charakterystyka</span><span class="sxs-lookup"><span data-stu-id="8b4ef-108">Characteristic</span></span>|<span data-ttu-id="8b4ef-109">Opis</span><span class="sxs-lookup"><span data-stu-id="8b4ef-109">Description</span></span>|
|--------------------|-----------------|
|<span data-ttu-id="8b4ef-110">Tryb zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="8b4ef-110">Security Mode</span></span>|<span data-ttu-id="8b4ef-111">Komunikat</span><span class="sxs-lookup"><span data-stu-id="8b4ef-111">Message</span></span>|
|<span data-ttu-id="8b4ef-112">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="8b4ef-112">Interoperability</span></span>|<span data-ttu-id="8b4ef-113">Tak, WS-Security z klientami zgodnymi z profilem tokenu Kerberos</span><span class="sxs-lookup"><span data-stu-id="8b4ef-113">Yes, WS-Security with Kerberos token-profile compatible clients</span></span>|
|<span data-ttu-id="8b4ef-114">Uwierzytelnianie (serwer)</span><span class="sxs-lookup"><span data-stu-id="8b4ef-114">Authentication (Server)</span></span>|<span data-ttu-id="8b4ef-115">Wzajemne uwierzytelnianie serwera i klienta</span><span class="sxs-lookup"><span data-stu-id="8b4ef-115">Mutual authentication of the server and client</span></span>|
|<span data-ttu-id="8b4ef-116">Uwierzytelnianie (klient)</span><span class="sxs-lookup"><span data-stu-id="8b4ef-116">Authentication (Client)</span></span>|<span data-ttu-id="8b4ef-117">Wzajemne uwierzytelnianie serwera i klienta</span><span class="sxs-lookup"><span data-stu-id="8b4ef-117">Mutual authentication of the server and client</span></span>|
|<span data-ttu-id="8b4ef-118">Integralność</span><span class="sxs-lookup"><span data-stu-id="8b4ef-118">Integrity</span></span>|<span data-ttu-id="8b4ef-119">Tak</span><span class="sxs-lookup"><span data-stu-id="8b4ef-119">Yes</span></span>|
|<span data-ttu-id="8b4ef-120">Poufność</span><span class="sxs-lookup"><span data-stu-id="8b4ef-120">Confidentiality</span></span>|<span data-ttu-id="8b4ef-121">Tak</span><span class="sxs-lookup"><span data-stu-id="8b4ef-121">Yes</span></span>|
|<span data-ttu-id="8b4ef-122">Transport</span><span class="sxs-lookup"><span data-stu-id="8b4ef-122">Transport</span></span>|<span data-ttu-id="8b4ef-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="8b4ef-123">HTTP</span></span>|
|<span data-ttu-id="8b4ef-124">Wiązanie</span><span class="sxs-lookup"><span data-stu-id="8b4ef-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|

## <a name="service"></a><span data-ttu-id="8b4ef-125">Usługa</span><span class="sxs-lookup"><span data-stu-id="8b4ef-125">Service</span></span>

<span data-ttu-id="8b4ef-126">Poniższy kod i konfiguracja są przeznaczone do niezależnego uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="8b4ef-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="8b4ef-127">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="8b4ef-127">Do one of the following:</span></span>

- <span data-ttu-id="8b4ef-128">Tworzenie usługi autonomicznej przy użyciu kodu bez konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8b4ef-128">Create a stand-alone service using the code with no configuration.</span></span>

- <span data-ttu-id="8b4ef-129">Utwórz usługę przy użyciu podanej konfiguracji, ale nie Definiuj żadnych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="8b4ef-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>

### <a name="code"></a><span data-ttu-id="8b4ef-130">Kod</span><span class="sxs-lookup"><span data-stu-id="8b4ef-130">Code</span></span>

<span data-ttu-id="8b4ef-131">Poniższy kod tworzy punkt końcowy usługi, który korzysta z zabezpieczeń komunikatów.</span><span class="sxs-lookup"><span data-stu-id="8b4ef-131">The following code creates a service endpoint that uses message security.</span></span> <span data-ttu-id="8b4ef-132">Kod wyłącza negocjowanie poświadczeń usługi i ustanawia token kontekstu zabezpieczeń (SCT).</span><span class="sxs-lookup"><span data-stu-id="8b4ef-132">The code disables service credential negotiation, and the establishment of a security context token (SCT).</span></span>

> [!NOTE]
> <span data-ttu-id="8b4ef-133">Aby użyć typu poświadczeń systemu Windows bez negocjowania, konto użytkownika usługi musi mieć dostęp do głównej nazwy usługi (SPN), która jest zarejestrowana w domenie Active Directory.</span><span class="sxs-lookup"><span data-stu-id="8b4ef-133">To use the Windows credential type without negotiation, the service's user account must have access to service principal name (SPN) that is registered with the Active Directory domain.</span></span> <span data-ttu-id="8b4ef-134">Możesz to zrobić na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="8b4ef-134">You can do this in two ways:</span></span>

1. <span data-ttu-id="8b4ef-135">Użyj `NetworkService` konta lub, `LocalSystem` Aby uruchomić usługę.</span><span class="sxs-lookup"><span data-stu-id="8b4ef-135">Use the `NetworkService` or `LocalSystem` account to run your service.</span></span> <span data-ttu-id="8b4ef-136">Ponieważ te konta mają dostęp do nazwy SPN maszyny, która została ustanowiona, gdy komputer jest przyłączony do domeny Active Directory, funkcja WCF automatycznie generuje prawidłowy element SPN w ramach punktu końcowego usługi w metadanych (Web Services Description Language lub WSDL) usługi.</span><span class="sxs-lookup"><span data-stu-id="8b4ef-136">Because those accounts have access to the machine SPN that is established when the machine joins the Active Directory domain, WCF automatically generates the proper SPN element inside the service's endpoint in the service's metadata (Web Services Description Language, or WSDL).</span></span>

2. <span data-ttu-id="8b4ef-137">Użyj dowolnego konta domeny Active Directory, aby uruchomić usługę.</span><span class="sxs-lookup"><span data-stu-id="8b4ef-137">Use an arbitrary Active Directory domain account to run your service.</span></span> <span data-ttu-id="8b4ef-138">W takim przypadku należy ustanowić nazwę SPN dla tego konta domeny.</span><span class="sxs-lookup"><span data-stu-id="8b4ef-138">In this case, you need to establish an SPN for that domain account.</span></span> <span data-ttu-id="8b4ef-139">Jednym z nich jest użycie narzędzia narzędzia Setspn. exe.</span><span class="sxs-lookup"><span data-stu-id="8b4ef-139">One way of doing this is to use the Setspn.exe utility tool.</span></span> <span data-ttu-id="8b4ef-140">Po utworzeniu nazwy SPN dla konta usługi Skonfiguruj funkcję WCF do publikowania tej nazwy SPN na klientach usługi za pomocą metadanych (WSDL).</span><span class="sxs-lookup"><span data-stu-id="8b4ef-140">Once the SPN is created for the service's account, configure WCF to publish that SPN to the service's clients through its metadata (WSDL).</span></span> <span data-ttu-id="8b4ef-141">W tym celu należy ustawić tożsamość punktu końcowego dla uwidocznionego punktu końcowego, chociaż plik lub kod konfiguracyjny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8b4ef-141">This is done by setting the endpoint identity for the exposed endpoint, either though an application configuration file or code.</span></span> <span data-ttu-id="8b4ef-142">Poniższy przykład umożliwia programistyczne publikowanie tożsamości.</span><span class="sxs-lookup"><span data-stu-id="8b4ef-142">The following example publishes the identity programmatically.</span></span>

<span data-ttu-id="8b4ef-143">Aby uzyskać więcej informacji na temat nazw SPN, protokołu Kerberos i Active Directory, zobacz [dodatek dotyczący protokołu Kerberos dla systemu Windows](https://docs.microsoft.com/previous-versions/msp-n-p/ff649429(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="8b4ef-143">For more information about SPNs, the Kerberos protocol, and Active Directory, see [Kerberos Technical Supplement for Windows](https://docs.microsoft.com/previous-versions/msp-n-p/ff649429(v=pandp.10)).</span></span> <span data-ttu-id="8b4ef-144">Aby uzyskać więcej informacji na temat tożsamości punktów końcowych, zobacz [elementu SecurityBindingElement Authentication Modes](securitybindingelement-authentication-modes.md).</span><span class="sxs-lookup"><span data-stu-id="8b4ef-144">For more information about endpoint identities, see [SecurityBindingElement Authentication Modes](securitybindingelement-authentication-modes.md).</span></span>

[!code-csharp[C_SecurityScenarios#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#12)]
[!code-vb[C_SecurityScenarios#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#12)]

### <a name="configuration"></a><span data-ttu-id="8b4ef-145">Konfigurowanie</span><span class="sxs-lookup"><span data-stu-id="8b4ef-145">Configuration</span></span>

<span data-ttu-id="8b4ef-146">Można użyć poniższej konfiguracji zamiast kodu.</span><span class="sxs-lookup"><span data-stu-id="8b4ef-146">The following configuration can be used instead of the code.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.serviceModel>
    <behaviors />
    <services>
      <service behaviorConfiguration="" name="ServiceModel.Calculator">
        <endpoint address="http://localhost/Calculator"
                  binding="wsHttpBinding"
                  bindingConfiguration="KerberosBinding"
                  name="WSHttpBinding_ICalculator"
                  contract="ServiceModel.ICalculator"
                  listenUri="net.tcp://localhost/metadata" >
         <identity>
            <servicePrincipalName value="service_spn_name" />
         </identity>
        </endpoint>
      </service>
    </services>
    <bindings>
      <wsHttpBinding>
        <binding name="KerberosBinding">
          <security>
            <message negotiateServiceCredential="false"
                     establishSecurityContext="false" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <client />
  </system.serviceModel>
</configuration>
```

## <a name="client"></a><span data-ttu-id="8b4ef-147">Klient</span><span class="sxs-lookup"><span data-stu-id="8b4ef-147">Client</span></span>

<span data-ttu-id="8b4ef-148">Poniższy kod i konfiguracja są przeznaczone do niezależnego uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="8b4ef-148">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="8b4ef-149">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="8b4ef-149">Do one of the following:</span></span>

- <span data-ttu-id="8b4ef-150">Utwórz klienta autonomicznego przy użyciu kodu (i kodu klienta).</span><span class="sxs-lookup"><span data-stu-id="8b4ef-150">Create a stand-alone client using the code (and client code).</span></span>

- <span data-ttu-id="8b4ef-151">Utwórz klienta, który nie definiuje żadnych adresów punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="8b4ef-151">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="8b4ef-152">Zamiast tego należy użyć konstruktora klienta, który przyjmuje nazwę konfiguracji jako argument.</span><span class="sxs-lookup"><span data-stu-id="8b4ef-152">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="8b4ef-153">Przykład:</span><span class="sxs-lookup"><span data-stu-id="8b4ef-153">For example:</span></span>

  [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
  [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]

### <a name="code"></a><span data-ttu-id="8b4ef-154">Kod</span><span class="sxs-lookup"><span data-stu-id="8b4ef-154">Code</span></span>

<span data-ttu-id="8b4ef-155">Poniższy kod konfiguruje klienta.</span><span class="sxs-lookup"><span data-stu-id="8b4ef-155">The following code configures the client.</span></span> <span data-ttu-id="8b4ef-156">Tryb zabezpieczeń jest ustawiony na wartość komunikat, a typ poświadczeń klienta to Windows.</span><span class="sxs-lookup"><span data-stu-id="8b4ef-156">The security mode is set to Message, and the client credential type is set to Windows.</span></span> <span data-ttu-id="8b4ef-157">Należy pamiętać, <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> że <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> właściwości i są ustawione na `false` .</span><span class="sxs-lookup"><span data-stu-id="8b4ef-157">Note that the <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> and <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> properties are set to `false`.</span></span>

> [!NOTE]
> <span data-ttu-id="8b4ef-158">Aby użyć typu poświadczeń systemu Windows bez negocjowania, przed rozpoczęciem komunikacji z usługą należy skonfigurować klienta przy użyciu nazwy SPN konta usługi.</span><span class="sxs-lookup"><span data-stu-id="8b4ef-158">To use Windows credential type without negotiation, the client must be configured with the service's account SPN prior to commencing the communication with the service.</span></span> <span data-ttu-id="8b4ef-159">Klient używa nazwy SPN, aby uzyskać token Kerberos do uwierzytelniania i zabezpieczania komunikacji z usługą.</span><span class="sxs-lookup"><span data-stu-id="8b4ef-159">The client uses the SPN to get the Kerberos token to authenticate and secure the communication with the service.</span></span> <span data-ttu-id="8b4ef-160">Poniższy przykład pokazuje, jak skonfigurować klienta przy użyciu nazwy SPN usługi.</span><span class="sxs-lookup"><span data-stu-id="8b4ef-160">The following sample shows how to configure the client with the service's SPN.</span></span> <span data-ttu-id="8b4ef-161">Jeśli używasz narzędzia do obsługi [metadanych ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) w celu wygenerowania klienta, Nazwa SPN usługi zostanie automatycznie rozpropagowana do klienta z metadanych usługi (WSDL), jeśli metadane usługi zawierają te informacje.</span><span class="sxs-lookup"><span data-stu-id="8b4ef-161">If you are using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the client, the service's SPN will be automatically propagated to the client from the service's metadata (WSDL), if the service's metadata contains that information.</span></span> <span data-ttu-id="8b4ef-162">Więcej informacji o sposobie konfigurowania usługi w celu uwzględnienia jej nazwy SPN w metadanych usługi znajduje się w sekcji "usługa" w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="8b4ef-162">For more information about how to configure the service to include its SPN in the service's metadata, see the "Service" section later in this topic .</span></span>
>
> <span data-ttu-id="8b4ef-163">Aby uzyskać więcej informacji na temat nazw SPN, Kerberos i Active Directory, zobacz [dodatek dotyczący protokołu Kerberos dla systemu Windows](https://docs.microsoft.com/previous-versions/msp-n-p/ff649429(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="8b4ef-163">For more information about SPNs, Kerberos, and Active Directory, see [Kerberos Technical Supplement for Windows](https://docs.microsoft.com/previous-versions/msp-n-p/ff649429(v=pandp.10)).</span></span> <span data-ttu-id="8b4ef-164">Aby uzyskać więcej informacji na temat tożsamości punktów końcowych, zobacz temat [tryby uwierzytelniania elementu SecurityBindingElement](securitybindingelement-authentication-modes.md) .</span><span class="sxs-lookup"><span data-stu-id="8b4ef-164">For more information about endpoint identities, see [SecurityBindingElement Authentication Modes](securitybindingelement-authentication-modes.md) topic.</span></span>

[!code-csharp[C_SecurityScenarios#19](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#19)]
[!code-vb[C_SecurityScenarios#19](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#19)]

### <a name="configuration"></a><span data-ttu-id="8b4ef-165">Konfigurowanie</span><span class="sxs-lookup"><span data-stu-id="8b4ef-165">Configuration</span></span>

<span data-ttu-id="8b4ef-166">Poniższy kod konfiguruje klienta.</span><span class="sxs-lookup"><span data-stu-id="8b4ef-166">The following code configures the client.</span></span> <span data-ttu-id="8b4ef-167">Należy pamiętać, że [\<servicePrincipalName>](../../configure-apps/file-schema/wcf/serviceprincipalname.md) element musi być ustawiony jako zgodny z nazwą SPN usługi zarejestrowanej dla konta usługi w domenie Active Directory.</span><span class="sxs-lookup"><span data-stu-id="8b4ef-167">Note that the [\<servicePrincipalName>](../../configure-apps/file-schema/wcf/serviceprincipalname.md) element must be set to match the service's SPN as registered for the service's account in the Active Directory domain.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.serviceModel>
    <bindings>
      <wsHttpBinding>
        <binding name="WSHttpBinding_ICalculator" >
          <security mode="Message">
            <message clientCredentialType="Windows"
                     negotiateServiceCredential="false"
                     establishSecurityContext="false" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <client>
      <endpoint address="http://localhost/Calculator"
                binding="wsHttpBinding"
                bindingConfiguration="WSHttpBinding_ICalculator"
                contract="ICalculator"
                name="WSHttpBinding_ICalculator">
        <identity>
          <servicePrincipalName value="service_spn_name" />
        </identity>
      </endpoint>
    </client>
  </system.serviceModel>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="8b4ef-168">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8b4ef-168">See also</span></span>

- [<span data-ttu-id="8b4ef-169">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="8b4ef-169">Security Overview</span></span>](security-overview.md)
- [<span data-ttu-id="8b4ef-170">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="8b4ef-170">Service Identity and Authentication</span></span>](service-identity-and-authentication.md)
- <span data-ttu-id="8b4ef-171">[Model zabezpieczeń dla sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="8b4ef-171">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
