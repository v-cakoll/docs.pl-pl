---
title: Zabezpieczenia komunikatów z anonimowym klientem
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cad53e1a-b7c9-4064-bc87-508c3d1dce49
ms.openlocfilehash: 058163c96bba036c3183695bf986b4d0424271ac
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595222"
---
# <a name="message-security-with-an-anonymous-client"></a><span data-ttu-id="09142-102">Zabezpieczenia komunikatów z anonimowym klientem</span><span class="sxs-lookup"><span data-stu-id="09142-102">Message Security with an Anonymous Client</span></span>

<span data-ttu-id="09142-103">W poniższym scenariuszu przedstawiono klienta i usługę zabezpieczone przez Windows Communication Foundation (WCF) zabezpieczenia komunikatów.</span><span class="sxs-lookup"><span data-stu-id="09142-103">The following scenario shows a client and service secured by Windows Communication Foundation (WCF) message security.</span></span> <span data-ttu-id="09142-104">Celem projektowania jest korzystanie z zabezpieczeń komunikatów zamiast zabezpieczeń transportu, dzięki czemu w przyszłości może obsługiwać bogatszy model oparty na oświadczeniach.</span><span class="sxs-lookup"><span data-stu-id="09142-104">A design goal is to use message security rather than transport security, so that in the future it can support a richer claims-based model.</span></span> <span data-ttu-id="09142-105">Aby uzyskać więcej informacji o korzystaniu z rozbudowanych oświadczeń do autoryzacji, zobacz [Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości](managing-claims-and-authorization-with-the-identity-model.md).</span><span class="sxs-lookup"><span data-stu-id="09142-105">For more information about using rich claims for authorization, see [Managing Claims and Authorization with the Identity Model](managing-claims-and-authorization-with-the-identity-model.md).</span></span>

<span data-ttu-id="09142-106">Aby zapoznać się z przykładową aplikacją, zobacz [zabezpieczenia wiadomości anonimowe](../samples/message-security-anonymous.md).</span><span class="sxs-lookup"><span data-stu-id="09142-106">For a sample application, see [Message Security Anonymous](../samples/message-security-anonymous.md).</span></span>

<span data-ttu-id="09142-107">![Zabezpieczenia komunikatów z anonimowym klientem](media/b361a565-831c-4c10-90d7-66d8eeece0a1.gif "b361a565-831c-4c10-90d7-66d8eeece0a1")</span><span class="sxs-lookup"><span data-stu-id="09142-107">![Message security with an anonymous client](media/b361a565-831c-4c10-90d7-66d8eeece0a1.gif "b361a565-831c-4c10-90d7-66d8eeece0a1")</span></span>

|<span data-ttu-id="09142-108">Charakterystyka</span><span class="sxs-lookup"><span data-stu-id="09142-108">Characteristic</span></span>|<span data-ttu-id="09142-109">Opis</span><span class="sxs-lookup"><span data-stu-id="09142-109">Description</span></span>|
|--------------------|-----------------|
|<span data-ttu-id="09142-110">Tryb zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="09142-110">Security Mode</span></span>|<span data-ttu-id="09142-111">Komunikat</span><span class="sxs-lookup"><span data-stu-id="09142-111">Message</span></span>|
|<span data-ttu-id="09142-112">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="09142-112">Interoperability</span></span>|<span data-ttu-id="09142-113">Tylko WCF</span><span class="sxs-lookup"><span data-stu-id="09142-113">WCF only</span></span>|
|<span data-ttu-id="09142-114">Uwierzytelnianie (serwer)</span><span class="sxs-lookup"><span data-stu-id="09142-114">Authentication (Server)</span></span>|<span data-ttu-id="09142-115">Początkowe negocjowanie wymaga uwierzytelniania serwera, ale nie uwierzytelniania klienta</span><span class="sxs-lookup"><span data-stu-id="09142-115">Initial negotiation requires server authentication, but not client authentication</span></span>|
|<span data-ttu-id="09142-116">Uwierzytelnianie (klient)</span><span class="sxs-lookup"><span data-stu-id="09142-116">Authentication (Client)</span></span>|<span data-ttu-id="09142-117">Brak</span><span class="sxs-lookup"><span data-stu-id="09142-117">None</span></span>|
|<span data-ttu-id="09142-118">Integralność</span><span class="sxs-lookup"><span data-stu-id="09142-118">Integrity</span></span>|<span data-ttu-id="09142-119">Tak, przy użyciu kontekstu zabezpieczeń udostępnionych</span><span class="sxs-lookup"><span data-stu-id="09142-119">Yes, using shared security context</span></span>|
|<span data-ttu-id="09142-120">Poufność</span><span class="sxs-lookup"><span data-stu-id="09142-120">Confidentiality</span></span>|<span data-ttu-id="09142-121">Tak, przy użyciu kontekstu zabezpieczeń udostępnionych</span><span class="sxs-lookup"><span data-stu-id="09142-121">Yes, using shared security context</span></span>|
|<span data-ttu-id="09142-122">Transport</span><span class="sxs-lookup"><span data-stu-id="09142-122">Transport</span></span>|<span data-ttu-id="09142-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="09142-123">HTTP</span></span>|

## <a name="service"></a><span data-ttu-id="09142-124">Usługa</span><span class="sxs-lookup"><span data-stu-id="09142-124">Service</span></span>

<span data-ttu-id="09142-125">Poniższy kod i konfiguracja są przeznaczone do niezależnego uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="09142-125">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="09142-126">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="09142-126">Do one of the following:</span></span>

- <span data-ttu-id="09142-127">Tworzenie usługi autonomicznej przy użyciu kodu bez konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="09142-127">Create a stand-alone service using the code with no configuration.</span></span>

- <span data-ttu-id="09142-128">Utwórz usługę przy użyciu podanej konfiguracji, ale nie Definiuj żadnych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="09142-128">Create a service using the supplied configuration, but do not define any endpoints.</span></span>

### <a name="code"></a><span data-ttu-id="09142-129">Kod</span><span class="sxs-lookup"><span data-stu-id="09142-129">Code</span></span>

<span data-ttu-id="09142-130">Poniższy kod przedstawia sposób tworzenia punktu końcowego usługi, który korzysta z zabezpieczeń komunikatów.</span><span class="sxs-lookup"><span data-stu-id="09142-130">The following code shows how to create a service endpoint that uses message security.</span></span>

[!code-csharp[C_SecurityScenarios#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#8)]
[!code-vb[C_SecurityScenarios#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#8)]

### <a name="configuration"></a><span data-ttu-id="09142-131">Konfigurowanie</span><span class="sxs-lookup"><span data-stu-id="09142-131">Configuration</span></span>

<span data-ttu-id="09142-132">Można użyć poniższej konfiguracji zamiast kodu.</span><span class="sxs-lookup"><span data-stu-id="09142-132">The following configuration can be used instead of the code.</span></span> <span data-ttu-id="09142-133">Element zachowania usługi służy do określania certyfikatu, który jest używany do uwierzytelniania usługi dla klienta.</span><span class="sxs-lookup"><span data-stu-id="09142-133">The service behavior element is used to specify a certificate that is used to authenticate the service to the client.</span></span> <span data-ttu-id="09142-134">Element Service musi określać zachowanie przy użyciu `behaviorConfiguration` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="09142-134">The service element must specify the behavior using the `behaviorConfiguration` attribute.</span></span> <span data-ttu-id="09142-135">Element Binding określa, że typ poświadczeń klienta to `None` , co umożliwia anonimowym klientom korzystanie z usługi.</span><span class="sxs-lookup"><span data-stu-id="09142-135">The binding element specifies that the client credential type is `None`, allowing anonymous clients to use the service.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.serviceModel>
    <behaviors>
      <serviceBehaviors>
        <behavior name="ServiceCredentialsBehavior">
          <serviceCredentials>
            <serviceCertificate findValue="contoso.com"
                                storeLocation="LocalMachine"
                                storeName="My" />
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>
    <services>
      <service behaviorConfiguration="ServiceCredentialsBehavior"
               name="ServiceModel.Calculator">
        <endpoint address="http://localhost/Calculator"
                  binding="wsHttpBinding"
                  bindingConfiguration="WSHttpBinding_ICalculator"
                  name="CalculatorService"
                  contract="ServiceModel.ICalculator" />
      </service>
    </services>
    <bindings>
      <wsHttpBinding>
        <binding name="WSHttpBinding_ICalculator" >
          <security mode="Message">
            <message clientCredentialType="None" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <client />
  </system.serviceModel>
</configuration>
```

## <a name="client"></a><span data-ttu-id="09142-136">Klient</span><span class="sxs-lookup"><span data-stu-id="09142-136">Client</span></span>

<span data-ttu-id="09142-137">Poniższy kod i konfiguracja są przeznaczone do niezależnego uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="09142-137">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="09142-138">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="09142-138">Do one of the following:</span></span>

- <span data-ttu-id="09142-139">Utwórz klienta autonomicznego przy użyciu kodu (i kodu klienta).</span><span class="sxs-lookup"><span data-stu-id="09142-139">Create a stand-alone client using the code (and client code).</span></span>

- <span data-ttu-id="09142-140">Utwórz klienta, który nie definiuje żadnych adresów punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="09142-140">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="09142-141">Zamiast tego należy użyć konstruktora klienta, który przyjmuje nazwę konfiguracji jako argument.</span><span class="sxs-lookup"><span data-stu-id="09142-141">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="09142-142">Przykład:</span><span class="sxs-lookup"><span data-stu-id="09142-142">For example:</span></span>

    [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
    [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]

### <a name="code"></a><span data-ttu-id="09142-143">Kod</span><span class="sxs-lookup"><span data-stu-id="09142-143">Code</span></span>

<span data-ttu-id="09142-144">Poniższy kod tworzy wystąpienie klienta.</span><span class="sxs-lookup"><span data-stu-id="09142-144">The following code creates an instance of the client.</span></span> <span data-ttu-id="09142-145">Powiązanie używa zabezpieczeń trybu komunikatów, a typ poświadczeń klienta ma wartość none.</span><span class="sxs-lookup"><span data-stu-id="09142-145">The binding uses message mode security, and the client credential type is set to none.</span></span>

[!code-csharp[C_SecurityScenarios#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#15)]
[!code-vb[C_SecurityScenarios#15](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#15)]

### <a name="configuration"></a><span data-ttu-id="09142-146">Konfigurowanie</span><span class="sxs-lookup"><span data-stu-id="09142-146">Configuration</span></span>

<span data-ttu-id="09142-147">Poniższy kod konfiguruje klienta.</span><span class="sxs-lookup"><span data-stu-id="09142-147">The following code configures the client.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.serviceModel>
    <bindings>
      <wsHttpBinding>
        <binding name="WSHttpBinding_ICalculator" >
          <security mode="Message">
            <message clientCredentialType="None" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <client>
      <endpoint address="http://machineName/Calculator"
        binding="wsHttpBinding"
        bindingConfiguration="WSHttpBinding_ICalculator"
        contract="ICalculator"
        name="WSHttpBinding_ICalculator">
        <identity>
          <dns value="contoso.com" />
        </identity>
      </endpoint>
    </client>
  </system.serviceModel>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="09142-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="09142-148">See also</span></span>

- [<span data-ttu-id="09142-149">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="09142-149">Security Overview</span></span>](security-overview.md)
- [<span data-ttu-id="09142-150">Rozproszone zabezpieczenia aplikacji</span><span class="sxs-lookup"><span data-stu-id="09142-150">Distributed Application Security</span></span>](distributed-application-security.md)
- [<span data-ttu-id="09142-151">Zabezpieczenia komunikatów z anonimowością</span><span class="sxs-lookup"><span data-stu-id="09142-151">Message Security Anonymous</span></span>](../samples/message-security-anonymous.md)
- [<span data-ttu-id="09142-152">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="09142-152">Service Identity and Authentication</span></span>](service-identity-and-authentication.md)
- <span data-ttu-id="09142-153">[Model zabezpieczeń dla sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="09142-153">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
