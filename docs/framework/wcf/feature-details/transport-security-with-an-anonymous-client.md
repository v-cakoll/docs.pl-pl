---
title: Zabezpieczanie transportu za pomocą anonimowego klienta
description: Zapoznaj się z tym scenariuszem WCF, który korzysta z zabezpieczeń transportu do uwierzytelniania serwera przy użyciu certyfikatu, który ufa klientowi. Klient nie jest uwierzytelniony.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 056653a5-384e-4a02-ae3c-1b0157d2ccb4
ms.openlocfilehash: 08cfb8c1a5581f17a251224430018764bed80b0f
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245014"
---
# <a name="transport-security-with-an-anonymous-client"></a><span data-ttu-id="ec718-104">Zabezpieczanie transportu za pomocą anonimowego klienta</span><span class="sxs-lookup"><span data-stu-id="ec718-104">Transport security with an anonymous client</span></span>

<span data-ttu-id="ec718-105">W tym scenariuszu Windows Communication Foundation (WCF) do zapewnienia poufności i integralności jest stosowany protokół HTTPS (Transport Security).</span><span class="sxs-lookup"><span data-stu-id="ec718-105">This Windows Communication Foundation (WCF) scenario uses transport security (HTTPS) to ensure confidentiality and integrity.</span></span> <span data-ttu-id="ec718-106">Serwer musi być uwierzytelniany przy użyciu certyfikatu SSL (SSL), a klienci muszą ufać certyfikatowi serwera.</span><span class="sxs-lookup"><span data-stu-id="ec718-106">The server must be authenticated with a Secure Sockets Layer (SSL) certificate, and the clients must trust the server's certificate.</span></span> <span data-ttu-id="ec718-107">Klient nie jest uwierzytelniany przez żaden mechanizm i jest w tym przypadku anonimowy.</span><span class="sxs-lookup"><span data-stu-id="ec718-107">The client is not authenticated by any mechanism and is, therefore, anonymous.</span></span>

<span data-ttu-id="ec718-108">Aby uzyskać przykładową aplikację, zobacz [WS Transport Security](../samples/ws-transport-security.md).</span><span class="sxs-lookup"><span data-stu-id="ec718-108">For a sample application, see [WS Transport Security](../samples/ws-transport-security.md).</span></span> <span data-ttu-id="ec718-109">Aby uzyskać więcej informacji na temat zabezpieczeń transportu, zobacz [Omówienie zabezpieczeń transportu](transport-security-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ec718-109">For more information about transport security, see [Transport Security Overview](transport-security-overview.md).</span></span>

<span data-ttu-id="ec718-110">Aby uzyskać więcej informacji na temat korzystania z certyfikatu z usługą, zobacz [Praca z certyfikatami](working-with-certificates.md) i [instrukcje: Konfigurowanie portu z certyfikatem SSL](how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="ec718-110">For more information about using a certificate with a service, see [Working with Certificates](working-with-certificates.md) and [How to: Configure a Port with an SSL Certificate](how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>

![Korzystanie z zabezpieczeń transportu z anonimowym klientem](./media/8fa2e931-0cfb-4aaa-9272-91d652b85d8d.gif)

|<span data-ttu-id="ec718-112">Charakterystyka</span><span class="sxs-lookup"><span data-stu-id="ec718-112">Characteristic</span></span>|<span data-ttu-id="ec718-113">Opis</span><span class="sxs-lookup"><span data-stu-id="ec718-113">Description</span></span>|
|--------------------|-----------------|
|<span data-ttu-id="ec718-114">Tryb zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="ec718-114">Security Mode</span></span>|<span data-ttu-id="ec718-115">Transport</span><span class="sxs-lookup"><span data-stu-id="ec718-115">Transport</span></span>|
|<span data-ttu-id="ec718-116">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="ec718-116">Interoperability</span></span>|<span data-ttu-id="ec718-117">Z istniejącymi usługami i klientami sieci Web</span><span class="sxs-lookup"><span data-stu-id="ec718-117">With existing Web services and clients</span></span>|
|<span data-ttu-id="ec718-118">Uwierzytelnianie (serwer)</span><span class="sxs-lookup"><span data-stu-id="ec718-118">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="ec718-119">Uwierzytelnianie (klient)</span><span class="sxs-lookup"><span data-stu-id="ec718-119">Authentication (Client)</span></span>|<span data-ttu-id="ec718-120">Tak</span><span class="sxs-lookup"><span data-stu-id="ec718-120">Yes</span></span><br /><br /> <span data-ttu-id="ec718-121">Poziom aplikacji (brak obsługi WCF)</span><span class="sxs-lookup"><span data-stu-id="ec718-121">Application level (no WCF support)</span></span>|
|<span data-ttu-id="ec718-122">Integralność</span><span class="sxs-lookup"><span data-stu-id="ec718-122">Integrity</span></span>|<span data-ttu-id="ec718-123">Tak</span><span class="sxs-lookup"><span data-stu-id="ec718-123">Yes</span></span>|
|<span data-ttu-id="ec718-124">Poufność</span><span class="sxs-lookup"><span data-stu-id="ec718-124">Confidentiality</span></span>|<span data-ttu-id="ec718-125">Tak</span><span class="sxs-lookup"><span data-stu-id="ec718-125">Yes</span></span>|
|<span data-ttu-id="ec718-126">Transport</span><span class="sxs-lookup"><span data-stu-id="ec718-126">Transport</span></span>|<span data-ttu-id="ec718-127">HTTPS</span><span class="sxs-lookup"><span data-stu-id="ec718-127">HTTPS</span></span>|
|<span data-ttu-id="ec718-128">Wiązanie</span><span class="sxs-lookup"><span data-stu-id="ec718-128">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|

## <a name="service"></a><span data-ttu-id="ec718-129">Usługa</span><span class="sxs-lookup"><span data-stu-id="ec718-129">Service</span></span>

<span data-ttu-id="ec718-130">Poniższy kod i konfiguracja są przeznaczone do niezależnego uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="ec718-130">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="ec718-131">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="ec718-131">Do one of the following:</span></span>

- <span data-ttu-id="ec718-132">Tworzenie usługi autonomicznej przy użyciu kodu bez konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ec718-132">Create a stand-alone service using the code with no configuration.</span></span>

- <span data-ttu-id="ec718-133">Utwórz usługę przy użyciu podanej konfiguracji, ale nie Definiuj żadnych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="ec718-133">Create a service using the supplied configuration, but do not define any endpoints.</span></span>

### <a name="code"></a><span data-ttu-id="ec718-134">Kod</span><span class="sxs-lookup"><span data-stu-id="ec718-134">Code</span></span>

<span data-ttu-id="ec718-135">Poniższy kod pokazuje, jak utworzyć punkt końcowy przy użyciu zabezpieczeń transportu:</span><span class="sxs-lookup"><span data-stu-id="ec718-135">The following code shows how to create an endpoint using transport security:</span></span>

[!code-csharp[c_SecurityScenarios#5](~/samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#5)]
[!code-vb[c_SecurityScenarios#5](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#5)]

### <a name="configuration"></a><span data-ttu-id="ec718-136">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="ec718-136">Configuration</span></span>

<span data-ttu-id="ec718-137">Poniższy kod konfiguruje ten sam punkt końcowy przy użyciu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ec718-137">The following code sets up the same endpoint using configuration.</span></span> <span data-ttu-id="ec718-138">Klient nie jest uwierzytelniany przez żaden mechanizm i dlatego jest anonimowy.</span><span class="sxs-lookup"><span data-stu-id="ec718-138">The client is not authenticated by any mechanism, and is therefore anonymous.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.serviceModel>
    <services>
      <service name="ServiceModel.Calculator">
        <endpoint address="https://localhost/Calculator"
                  binding="wsHttpBinding"
                  bindingConfiguration="WSHttpBinding_ICalculator"
                  name="SecuredByTransportEndpoint"
                  contract="ServiceModel.ICalculator" />
      </service>
    </services>
    <bindings>
      <wsHttpBinding>
        <binding name="WSHttpBinding_ICalculator">
          <security mode="Transport">
            <transport clientCredentialType="None" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <client />
  </system.serviceModel>
</configuration>
```

## <a name="client"></a><span data-ttu-id="ec718-139">Klient</span><span class="sxs-lookup"><span data-stu-id="ec718-139">Client</span></span>

<span data-ttu-id="ec718-140">Poniższy kod i konfiguracja są przeznaczone do niezależnego uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="ec718-140">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="ec718-141">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="ec718-141">Do one of the following:</span></span>

- <span data-ttu-id="ec718-142">Utwórz klienta autonomicznego przy użyciu kodu (i kodu klienta).</span><span class="sxs-lookup"><span data-stu-id="ec718-142">Create a stand-alone client using the code (and client code).</span></span>

- <span data-ttu-id="ec718-143">Utwórz klienta, który nie definiuje żadnych adresów punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="ec718-143">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="ec718-144">Zamiast tego należy użyć konstruktora klienta, który przyjmuje nazwę konfiguracji jako argument.</span><span class="sxs-lookup"><span data-stu-id="ec718-144">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="ec718-145">Przykład:</span><span class="sxs-lookup"><span data-stu-id="ec718-145">For example:</span></span>

     [!code-csharp[C_SecurityScenarios#0](~/samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]

### <a name="code"></a><span data-ttu-id="ec718-146">Kod</span><span class="sxs-lookup"><span data-stu-id="ec718-146">Code</span></span>

[!code-csharp[c_SecurityScenarios#6](~/samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#6)]
[!code-vb[c_SecurityScenarios#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#6)]

### <a name="configuration"></a><span data-ttu-id="ec718-147">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="ec718-147">Configuration</span></span>

<span data-ttu-id="ec718-148">W celu skonfigurowania usługi można użyć następującej konfiguracji zamiast kodu.</span><span class="sxs-lookup"><span data-stu-id="ec718-148">The following configuration can be used instead of the code to set up the service.</span></span>

```xml
<configuration>
  <system.serviceModel>
    <bindings>
      <wsHttpBinding>
        <binding name="WSHttpBinding_ICalculator" >
          <security mode="Transport">
            <transport clientCredentialType="None" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <client>
      <endpoint address="https://machineName/Calculator"
                binding="wsHttpBinding"
                bindingConfiguration="WSHttpBinding_ICalculator"
                contract="ICalculator"
                name="WSHttpBinding_ICalculator" />
    </client>
  </system.serviceModel>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="ec718-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ec718-149">See also</span></span>

- [<span data-ttu-id="ec718-150">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="ec718-150">Security Overview</span></span>](security-overview.md)
- [<span data-ttu-id="ec718-151">Zabezpieczenia transportu WS</span><span class="sxs-lookup"><span data-stu-id="ec718-151">WS Transport Security</span></span>](../samples/ws-transport-security.md)
- [<span data-ttu-id="ec718-152">Przegląd zabezpieczeń transportu</span><span class="sxs-lookup"><span data-stu-id="ec718-152">Transport Security Overview</span></span>](transport-security-overview.md)
- <span data-ttu-id="ec718-153">[Model zabezpieczeń dla sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="ec718-153">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
