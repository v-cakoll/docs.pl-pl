---
title: Zabezpieczanie transportu za pomocą anonimowego klienta - usługi WCF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 056653a5-384e-4a02-ae3c-1b0157d2ccb4
ms.openlocfilehash: 20d7e59ba2b4b9dedc0b0daff1c1aa9c5210e61b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55260388"
---
# <a name="transport-security-with-an-anonymous-client"></a><span data-ttu-id="d0c87-102">Zabezpieczanie transportu za pomocą anonimowego klienta</span><span class="sxs-lookup"><span data-stu-id="d0c87-102">Transport security with an anonymous client</span></span>

<span data-ttu-id="d0c87-103">W tym scenariuszu usług Windows Communication Foundation (WCF) używane zabezpieczeń transportowych (HTTPS), aby upewnić się, poufności i integralności.</span><span class="sxs-lookup"><span data-stu-id="d0c87-103">This Windows Communication Foundation (WCF) scenario uses transport security (HTTPS) to ensure confidentiality and integrity.</span></span> <span data-ttu-id="d0c87-104">Serwer musi zostać uwierzytelniony przy użyciu certyfikatu Secure Sockets Layer (SSL), a klienci muszą ufać certyfikatowi serwera.</span><span class="sxs-lookup"><span data-stu-id="d0c87-104">The server must be authenticated with a Secure Sockets Layer (SSL) certificate, and the clients must trust the server's certificate.</span></span> <span data-ttu-id="d0c87-105">Klient nie został uwierzytelniony przy użyciu dowolnego mechanizmu i jest zatem anonimowe.</span><span class="sxs-lookup"><span data-stu-id="d0c87-105">The client is not authenticated by any mechanism and is, therefore, anonymous.</span></span>

<span data-ttu-id="d0c87-106">Dla przykładowej aplikacji, zobacz [zabezpieczenia transportu WS](../samples/ws-transport-security.md).</span><span class="sxs-lookup"><span data-stu-id="d0c87-106">For a sample application, see [WS Transport Security](../samples/ws-transport-security.md).</span></span> <span data-ttu-id="d0c87-107">Aby uzyskać więcej informacji na temat zabezpieczeń transportu zobacz [Przegląd zabezpieczeń transportu](transport-security-overview.md).</span><span class="sxs-lookup"><span data-stu-id="d0c87-107">For more information about transport security, see [Transport Security Overview](transport-security-overview.md).</span></span>

<span data-ttu-id="d0c87-108">Aby uzyskać więcej informacji na temat używania certyfikatu z usługą, zobacz [Working with Certificates](working-with-certificates.md) i [jak: Konfigurowanie portu z certyfikatem SSL](how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="d0c87-108">For more information about using a certificate with a service, see [Working with Certificates](working-with-certificates.md) and [How to: Configure a Port with an SSL Certificate](how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>

![Za pomocą zabezpieczeń transportu z anonimowym klientem](./media/8fa2e931-0cfb-4aaa-9272-91d652b85d8d.gif)

|<span data-ttu-id="d0c87-110">Cechy</span><span class="sxs-lookup"><span data-stu-id="d0c87-110">Characteristic</span></span>|<span data-ttu-id="d0c87-111">Opis</span><span class="sxs-lookup"><span data-stu-id="d0c87-111">Description</span></span>|
|--------------------|-----------------|
|<span data-ttu-id="d0c87-112">Tryb zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="d0c87-112">Security Mode</span></span>|<span data-ttu-id="d0c87-113">Transport</span><span class="sxs-lookup"><span data-stu-id="d0c87-113">Transport</span></span>|
|<span data-ttu-id="d0c87-114">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="d0c87-114">Interoperability</span></span>|<span data-ttu-id="d0c87-115">Przy użyciu istniejących usług sieci Web i klientów</span><span class="sxs-lookup"><span data-stu-id="d0c87-115">With existing Web services and clients</span></span>|
|<span data-ttu-id="d0c87-116">Uwierzytelnianie (serwer)</span><span class="sxs-lookup"><span data-stu-id="d0c87-116">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="d0c87-117">Uwierzytelnianie (klient)</span><span class="sxs-lookup"><span data-stu-id="d0c87-117">Authentication (Client)</span></span>|<span data-ttu-id="d0c87-118">Tak</span><span class="sxs-lookup"><span data-stu-id="d0c87-118">Yes</span></span><br /><br /> <span data-ttu-id="d0c87-119">Poziom aplikacji (bez obsługi WCF)</span><span class="sxs-lookup"><span data-stu-id="d0c87-119">Application level (no WCF support)</span></span>|
|<span data-ttu-id="d0c87-120">Integralność</span><span class="sxs-lookup"><span data-stu-id="d0c87-120">Integrity</span></span>|<span data-ttu-id="d0c87-121">Tak</span><span class="sxs-lookup"><span data-stu-id="d0c87-121">Yes</span></span>|
|<span data-ttu-id="d0c87-122">Poufność</span><span class="sxs-lookup"><span data-stu-id="d0c87-122">Confidentiality</span></span>|<span data-ttu-id="d0c87-123">Tak</span><span class="sxs-lookup"><span data-stu-id="d0c87-123">Yes</span></span>|
|<span data-ttu-id="d0c87-124">Transport</span><span class="sxs-lookup"><span data-stu-id="d0c87-124">Transport</span></span>|<span data-ttu-id="d0c87-125">HTTPS</span><span class="sxs-lookup"><span data-stu-id="d0c87-125">HTTPS</span></span>|
|<span data-ttu-id="d0c87-126">Powiązanie</span><span class="sxs-lookup"><span data-stu-id="d0c87-126">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|

## <a name="service"></a><span data-ttu-id="d0c87-127">Usługa</span><span class="sxs-lookup"><span data-stu-id="d0c87-127">Service</span></span>

<span data-ttu-id="d0c87-128">Następujący kod i konfiguracji są przeznaczone do uruchamiania niezależnie.</span><span class="sxs-lookup"><span data-stu-id="d0c87-128">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="d0c87-129">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="d0c87-129">Do one of the following:</span></span>

- <span data-ttu-id="d0c87-130">Tworzenie autonomicznego usługi przy użyciu kodu bez konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="d0c87-130">Create a stand-alone service using the code with no configuration.</span></span>

- <span data-ttu-id="d0c87-131">Tworzenie usługi przy użyciu wprowadzonej konfiguracji, ale nie definiują żadnych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="d0c87-131">Create a service using the supplied configuration, but do not define any endpoints.</span></span>

### <a name="code"></a><span data-ttu-id="d0c87-132">Kod</span><span class="sxs-lookup"><span data-stu-id="d0c87-132">Code</span></span>

<span data-ttu-id="d0c87-133">Poniższy kod przedstawia sposób tworzenia punktu końcowego za pomocą zabezpieczeń transportu:</span><span class="sxs-lookup"><span data-stu-id="d0c87-133">The following code shows how to create an endpoint using transport security:</span></span>

[!code-csharp[c_SecurityScenarios#5](~/samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#5)]
[!code-vb[c_SecurityScenarios#5](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#5)]

### <a name="configuration"></a><span data-ttu-id="d0c87-134">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="d0c87-134">Configuration</span></span>

<span data-ttu-id="d0c87-135">Poniższy kod ustawia ten sam punkt końcowy, za pomocą konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="d0c87-135">The following code sets up the same endpoint using configuration.</span></span> <span data-ttu-id="d0c87-136">Klient nie został uwierzytelniony przy użyciu dowolnego mechanizmu i w związku z tym jest anonimowy.</span><span class="sxs-lookup"><span data-stu-id="d0c87-136">The client is not authenticated by any mechanism, and is therefore anonymous.</span></span>

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

## <a name="client"></a><span data-ttu-id="d0c87-137">Klient</span><span class="sxs-lookup"><span data-stu-id="d0c87-137">Client</span></span>

<span data-ttu-id="d0c87-138">Następujący kod i konfiguracji są przeznaczone do uruchamiania niezależnie.</span><span class="sxs-lookup"><span data-stu-id="d0c87-138">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="d0c87-139">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="d0c87-139">Do one of the following:</span></span>

- <span data-ttu-id="d0c87-140">Tworzenie klienta autonomicznego przy użyciu kodu (i kodu klienta).</span><span class="sxs-lookup"><span data-stu-id="d0c87-140">Create a stand-alone client using the code (and client code).</span></span>

- <span data-ttu-id="d0c87-141">Tworzenie klienta, który nie definiuje żadnych adresy punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="d0c87-141">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="d0c87-142">Zamiast tego należy użyć konstruktora klienta, który przyjmuje nazwę konfiguracji jako argument.</span><span class="sxs-lookup"><span data-stu-id="d0c87-142">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="d0c87-143">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="d0c87-143">For example:</span></span>

     [!code-csharp[C_SecurityScenarios#0](~/samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]

### <a name="code"></a><span data-ttu-id="d0c87-144">Kod</span><span class="sxs-lookup"><span data-stu-id="d0c87-144">Code</span></span>

[!code-csharp[c_SecurityScenarios#6](~/samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#6)]
[!code-vb[c_SecurityScenarios#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#6)]

### <a name="configuration"></a><span data-ttu-id="d0c87-145">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="d0c87-145">Configuration</span></span>

<span data-ttu-id="d0c87-146">Następująca konfiguracja może służyć zamiast kodu do konfiguracji obsługiwanej usługi.</span><span class="sxs-lookup"><span data-stu-id="d0c87-146">The following configuration can be used instead of the code to set up the service.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d0c87-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d0c87-147">See also</span></span>

- [<span data-ttu-id="d0c87-148">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="d0c87-148">Security Overview</span></span>](security-overview.md)
- [<span data-ttu-id="d0c87-149">Zabezpieczenia transportu WS</span><span class="sxs-lookup"><span data-stu-id="d0c87-149">WS Transport Security</span></span>](../samples/ws-transport-security.md)
- [<span data-ttu-id="d0c87-150">Przegląd zabezpieczeń transportu</span><span class="sxs-lookup"><span data-stu-id="d0c87-150">Transport Security Overview</span></span>](transport-security-overview.md)
- <span data-ttu-id="d0c87-151">[Model zabezpieczeń dla systemu Windows Server AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="d0c87-151">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>