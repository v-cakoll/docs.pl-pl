---
title: Zabezpieczenia komunikatów z anonimowym klientem
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cad53e1a-b7c9-4064-bc87-508c3d1dce49
ms.openlocfilehash: 613b85e18109faa2a4386090e91aaddcfd8e0b68
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62038588"
---
# <a name="message-security-with-an-anonymous-client"></a><span data-ttu-id="4e5c5-102">Zabezpieczenia komunikatów z anonimowym klientem</span><span class="sxs-lookup"><span data-stu-id="4e5c5-102">Message Security with an Anonymous Client</span></span>

<span data-ttu-id="4e5c5-103">Następujący scenariusz pokazuje, klient i usługa zabezpieczane na komunikat usług Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="4e5c5-103">The following scenario shows a client and service secured by Windows Communication Foundation (WCF) message security.</span></span> <span data-ttu-id="4e5c5-104">Celem projektu jest użycie zabezpieczeń wiadomości, a nie z zabezpieczeń transportu, aby w przyszłości może obsługiwać rozbudowane modelu opartego na oświadczeniach.</span><span class="sxs-lookup"><span data-stu-id="4e5c5-104">A design goal is to use message security rather than transport security, so that in the future it can support a richer claims-based model.</span></span> <span data-ttu-id="4e5c5-105">Aby uzyskać więcej informacji o korzystaniu z zaawansowanych oświadczenia dotyczące autoryzacji, zobacz [Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).</span><span class="sxs-lookup"><span data-stu-id="4e5c5-105">For more information about using rich claims for authorization, see [Managing Claims and Authorization with the Identity Model](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).</span></span>

<span data-ttu-id="4e5c5-106">Dla przykładowej aplikacji, zobacz [komunikat zabezpieczeń anonimowe](../../../../docs/framework/wcf/samples/message-security-anonymous.md).</span><span class="sxs-lookup"><span data-stu-id="4e5c5-106">For a sample application, see [Message Security Anonymous](../../../../docs/framework/wcf/samples/message-security-anonymous.md).</span></span>

<span data-ttu-id="4e5c5-107">![Zabezpieczenia z anonimowym klientem wiadomości](../../../../docs/framework/wcf/feature-details/media/b361a565-831c-4c10-90d7-66d8eeece0a1.gif "b361a565-831c-4c10-90d7-66d8eeece0a1")</span><span class="sxs-lookup"><span data-stu-id="4e5c5-107">![Message security with an anonymous client](../../../../docs/framework/wcf/feature-details/media/b361a565-831c-4c10-90d7-66d8eeece0a1.gif "b361a565-831c-4c10-90d7-66d8eeece0a1")</span></span>

|<span data-ttu-id="4e5c5-108">Cechy</span><span class="sxs-lookup"><span data-stu-id="4e5c5-108">Characteristic</span></span>|<span data-ttu-id="4e5c5-109">Opis</span><span class="sxs-lookup"><span data-stu-id="4e5c5-109">Description</span></span>|
|--------------------|-----------------|
|<span data-ttu-id="4e5c5-110">Tryb zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="4e5c5-110">Security Mode</span></span>|<span data-ttu-id="4e5c5-111">Komunikat</span><span class="sxs-lookup"><span data-stu-id="4e5c5-111">Message</span></span>|
|<span data-ttu-id="4e5c5-112">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="4e5c5-112">Interoperability</span></span>|<span data-ttu-id="4e5c5-113">Tylko usługi WCF</span><span class="sxs-lookup"><span data-stu-id="4e5c5-113">WCF only</span></span>|
|<span data-ttu-id="4e5c5-114">Uwierzytelnianie (serwer)</span><span class="sxs-lookup"><span data-stu-id="4e5c5-114">Authentication (Server)</span></span>|<span data-ttu-id="4e5c5-115">Początkowego negocjowania wymaga uwierzytelniania serwera, ale nie uwierzytelnianie klienta</span><span class="sxs-lookup"><span data-stu-id="4e5c5-115">Initial negotiation requires server authentication, but not client authentication</span></span>|
|<span data-ttu-id="4e5c5-116">Uwierzytelnianie (klient)</span><span class="sxs-lookup"><span data-stu-id="4e5c5-116">Authentication (Client)</span></span>|<span data-ttu-id="4e5c5-117">Brak</span><span class="sxs-lookup"><span data-stu-id="4e5c5-117">None</span></span>|
|<span data-ttu-id="4e5c5-118">Integralność</span><span class="sxs-lookup"><span data-stu-id="4e5c5-118">Integrity</span></span>|<span data-ttu-id="4e5c5-119">Tak, za pomocą kontekstu zabezpieczeń udostępnionego</span><span class="sxs-lookup"><span data-stu-id="4e5c5-119">Yes, using shared security context</span></span>|
|<span data-ttu-id="4e5c5-120">Poufność</span><span class="sxs-lookup"><span data-stu-id="4e5c5-120">Confidentiality</span></span>|<span data-ttu-id="4e5c5-121">Tak, za pomocą kontekstu zabezpieczeń udostępnionego</span><span class="sxs-lookup"><span data-stu-id="4e5c5-121">Yes, using shared security context</span></span>|
|<span data-ttu-id="4e5c5-122">Transport</span><span class="sxs-lookup"><span data-stu-id="4e5c5-122">Transport</span></span>|<span data-ttu-id="4e5c5-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="4e5c5-123">HTTP</span></span>|

## <a name="service"></a><span data-ttu-id="4e5c5-124">Usługa</span><span class="sxs-lookup"><span data-stu-id="4e5c5-124">Service</span></span>

<span data-ttu-id="4e5c5-125">Następujący kod i konfiguracji są przeznaczone do uruchamiania niezależnie.</span><span class="sxs-lookup"><span data-stu-id="4e5c5-125">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="4e5c5-126">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="4e5c5-126">Do one of the following:</span></span>

- <span data-ttu-id="4e5c5-127">Tworzenie autonomicznego usługi przy użyciu kodu bez konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="4e5c5-127">Create a stand-alone service using the code with no configuration.</span></span>

- <span data-ttu-id="4e5c5-128">Tworzenie usługi przy użyciu wprowadzonej konfiguracji, ale nie definiują żadnych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="4e5c5-128">Create a service using the supplied configuration, but do not define any endpoints.</span></span>

### <a name="code"></a><span data-ttu-id="4e5c5-129">Kod</span><span class="sxs-lookup"><span data-stu-id="4e5c5-129">Code</span></span>

<span data-ttu-id="4e5c5-130">Poniższy kod przedstawia sposób tworzenia punktu końcowego usługi, która używa zabezpieczenia wiadomości.</span><span class="sxs-lookup"><span data-stu-id="4e5c5-130">The following code shows how to create a service endpoint that uses message security.</span></span>

[!code-csharp[C_SecurityScenarios#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#8)]
[!code-vb[C_SecurityScenarios#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#8)]

### <a name="configuration"></a><span data-ttu-id="4e5c5-131">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="4e5c5-131">Configuration</span></span>

<span data-ttu-id="4e5c5-132">Następująca konfiguracja można używać zamiast kodu.</span><span class="sxs-lookup"><span data-stu-id="4e5c5-132">The following configuration can be used instead of the code.</span></span> <span data-ttu-id="4e5c5-133">Element zachowanie usługi jest używany do określenia certyfikatu, który jest używany do uwierzytelniania usługi dla klienta.</span><span class="sxs-lookup"><span data-stu-id="4e5c5-133">The service behavior element is used to specify a certificate that is used to authenticate the service to the client.</span></span> <span data-ttu-id="4e5c5-134">Element usługi należy określić przy użyciu zachowanie `behaviorConfiguration` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="4e5c5-134">The service element must specify the behavior using the `behaviorConfiguration` attribute.</span></span> <span data-ttu-id="4e5c5-135">Element powiązania Określa, że typ poświadczeń klienta jest `None`, umożliwiając klientom anonimowych do korzystania z usługi.</span><span class="sxs-lookup"><span data-stu-id="4e5c5-135">The binding element specifies that the client credential type is `None`, allowing anonymous clients to use the service.</span></span>

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

## <a name="client"></a><span data-ttu-id="4e5c5-136">Klient</span><span class="sxs-lookup"><span data-stu-id="4e5c5-136">Client</span></span>

<span data-ttu-id="4e5c5-137">Następujący kod i konfiguracji są przeznaczone do uruchamiania niezależnie.</span><span class="sxs-lookup"><span data-stu-id="4e5c5-137">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="4e5c5-138">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="4e5c5-138">Do one of the following:</span></span>

- <span data-ttu-id="4e5c5-139">Tworzenie klienta autonomicznego przy użyciu kodu (i kodu klienta).</span><span class="sxs-lookup"><span data-stu-id="4e5c5-139">Create a stand-alone client using the code (and client code).</span></span>

- <span data-ttu-id="4e5c5-140">Tworzenie klienta, który nie definiuje żadnych adresy punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="4e5c5-140">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="4e5c5-141">Zamiast tego należy użyć konstruktora klienta, który przyjmuje nazwę konfiguracji jako argument.</span><span class="sxs-lookup"><span data-stu-id="4e5c5-141">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="4e5c5-142">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="4e5c5-142">For example:</span></span>

    [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
    [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]

### <a name="code"></a><span data-ttu-id="4e5c5-143">Kod</span><span class="sxs-lookup"><span data-stu-id="4e5c5-143">Code</span></span>

<span data-ttu-id="4e5c5-144">Poniższy kod tworzy wystąpienie klienta.</span><span class="sxs-lookup"><span data-stu-id="4e5c5-144">The following code creates an instance of the client.</span></span> <span data-ttu-id="4e5c5-145">Powiązanie używa komunikatów tryb zabezpieczeń, a typu poświadczeń klienta jest ustawiona na wartość none.</span><span class="sxs-lookup"><span data-stu-id="4e5c5-145">The binding uses message mode security, and the client credential type is set to none.</span></span>

[!code-csharp[C_SecurityScenarios#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#15)]
[!code-vb[C_SecurityScenarios#15](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#15)]

### <a name="configuration"></a><span data-ttu-id="4e5c5-146">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="4e5c5-146">Configuration</span></span>

<span data-ttu-id="4e5c5-147">Poniższy kod konfiguruje klienta.</span><span class="sxs-lookup"><span data-stu-id="4e5c5-147">The following code configures the client.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="4e5c5-148">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4e5c5-148">See also</span></span>

- [<span data-ttu-id="4e5c5-149">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="4e5c5-149">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="4e5c5-150">Rozproszone zabezpieczenia aplikacji</span><span class="sxs-lookup"><span data-stu-id="4e5c5-150">Distributed Application Security</span></span>](../../../../docs/framework/wcf/feature-details/distributed-application-security.md)
- [<span data-ttu-id="4e5c5-151">Zabezpieczenia komunikatów z anonimowością</span><span class="sxs-lookup"><span data-stu-id="4e5c5-151">Message Security Anonymous</span></span>](../../../../docs/framework/wcf/samples/message-security-anonymous.md)
- [<span data-ttu-id="4e5c5-152">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="4e5c5-152">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="4e5c5-153">Model zabezpieczeń dla systemu Windows Server AppFabric</span><span class="sxs-lookup"><span data-stu-id="4e5c5-153">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
