---
title: Zabezpieczanie transportu za pomocą anonimowego klienta - usługi WCF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 056653a5-384e-4a02-ae3c-1b0157d2ccb4
ms.openlocfilehash: aac3b2ac6cfcca137bddaefafd290e744ee991eb
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65637437"
---
# <a name="transport-security-with-an-anonymous-client"></a><span data-ttu-id="65e17-102">Zabezpieczanie transportu za pomocą anonimowego klienta</span><span class="sxs-lookup"><span data-stu-id="65e17-102">Transport security with an anonymous client</span></span>

<span data-ttu-id="65e17-103">W tym scenariuszu usług Windows Communication Foundation (WCF) używane zabezpieczeń transportowych (HTTPS), aby upewnić się, poufności i integralności.</span><span class="sxs-lookup"><span data-stu-id="65e17-103">This Windows Communication Foundation (WCF) scenario uses transport security (HTTPS) to ensure confidentiality and integrity.</span></span> <span data-ttu-id="65e17-104">Serwer musi zostać uwierzytelniony przy użyciu certyfikatu Secure Sockets Layer (SSL), a klienci muszą ufać certyfikatowi serwera.</span><span class="sxs-lookup"><span data-stu-id="65e17-104">The server must be authenticated with a Secure Sockets Layer (SSL) certificate, and the clients must trust the server's certificate.</span></span> <span data-ttu-id="65e17-105">Klient nie został uwierzytelniony przy użyciu dowolnego mechanizmu i jest zatem anonimowe.</span><span class="sxs-lookup"><span data-stu-id="65e17-105">The client is not authenticated by any mechanism and is, therefore, anonymous.</span></span>

<span data-ttu-id="65e17-106">Dla przykładowej aplikacji, zobacz [zabezpieczenia transportu WS](../samples/ws-transport-security.md).</span><span class="sxs-lookup"><span data-stu-id="65e17-106">For a sample application, see [WS Transport Security](../samples/ws-transport-security.md).</span></span> <span data-ttu-id="65e17-107">Aby uzyskać więcej informacji na temat zabezpieczeń transportu zobacz [Przegląd zabezpieczeń transportu](transport-security-overview.md).</span><span class="sxs-lookup"><span data-stu-id="65e17-107">For more information about transport security, see [Transport Security Overview](transport-security-overview.md).</span></span>

<span data-ttu-id="65e17-108">Aby uzyskać więcej informacji na temat używania certyfikatu z usługą, zobacz [Working with Certificates](working-with-certificates.md) i [jak: Konfigurowanie portu z certyfikatem SSL](how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="65e17-108">For more information about using a certificate with a service, see [Working with Certificates](working-with-certificates.md) and [How to: Configure a Port with an SSL Certificate](how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>

![Za pomocą zabezpieczeń transportu z anonimowym klientem](./media/8fa2e931-0cfb-4aaa-9272-91d652b85d8d.gif)

|<span data-ttu-id="65e17-110">Cechy</span><span class="sxs-lookup"><span data-stu-id="65e17-110">Characteristic</span></span>|<span data-ttu-id="65e17-111">Opis</span><span class="sxs-lookup"><span data-stu-id="65e17-111">Description</span></span>|
|--------------------|-----------------|
|<span data-ttu-id="65e17-112">Tryb zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="65e17-112">Security Mode</span></span>|<span data-ttu-id="65e17-113">Transport</span><span class="sxs-lookup"><span data-stu-id="65e17-113">Transport</span></span>|
|<span data-ttu-id="65e17-114">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="65e17-114">Interoperability</span></span>|<span data-ttu-id="65e17-115">Przy użyciu istniejących usług sieci Web i klientów</span><span class="sxs-lookup"><span data-stu-id="65e17-115">With existing Web services and clients</span></span>|
|<span data-ttu-id="65e17-116">Uwierzytelnianie (serwer)</span><span class="sxs-lookup"><span data-stu-id="65e17-116">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="65e17-117">Uwierzytelnianie (klient)</span><span class="sxs-lookup"><span data-stu-id="65e17-117">Authentication (Client)</span></span>|<span data-ttu-id="65e17-118">Tak</span><span class="sxs-lookup"><span data-stu-id="65e17-118">Yes</span></span><br /><br /> <span data-ttu-id="65e17-119">Poziom aplikacji (bez obsługi WCF)</span><span class="sxs-lookup"><span data-stu-id="65e17-119">Application level (no WCF support)</span></span>|
|<span data-ttu-id="65e17-120">Integralność</span><span class="sxs-lookup"><span data-stu-id="65e17-120">Integrity</span></span>|<span data-ttu-id="65e17-121">Tak</span><span class="sxs-lookup"><span data-stu-id="65e17-121">Yes</span></span>|
|<span data-ttu-id="65e17-122">Poufność</span><span class="sxs-lookup"><span data-stu-id="65e17-122">Confidentiality</span></span>|<span data-ttu-id="65e17-123">Tak</span><span class="sxs-lookup"><span data-stu-id="65e17-123">Yes</span></span>|
|<span data-ttu-id="65e17-124">Transport</span><span class="sxs-lookup"><span data-stu-id="65e17-124">Transport</span></span>|<span data-ttu-id="65e17-125">HTTPS</span><span class="sxs-lookup"><span data-stu-id="65e17-125">HTTPS</span></span>|
|<span data-ttu-id="65e17-126">Wiązanie</span><span class="sxs-lookup"><span data-stu-id="65e17-126">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|

## <a name="service"></a><span data-ttu-id="65e17-127">Usługa</span><span class="sxs-lookup"><span data-stu-id="65e17-127">Service</span></span>

<span data-ttu-id="65e17-128">Następujący kod i konfiguracji są przeznaczone do uruchamiania niezależnie.</span><span class="sxs-lookup"><span data-stu-id="65e17-128">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="65e17-129">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="65e17-129">Do one of the following:</span></span>

- <span data-ttu-id="65e17-130">Tworzenie autonomicznego usługi przy użyciu kodu bez konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="65e17-130">Create a stand-alone service using the code with no configuration.</span></span>

- <span data-ttu-id="65e17-131">Tworzenie usługi przy użyciu wprowadzonej konfiguracji, ale nie definiują żadnych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="65e17-131">Create a service using the supplied configuration, but do not define any endpoints.</span></span>

### <a name="code"></a><span data-ttu-id="65e17-132">Kod</span><span class="sxs-lookup"><span data-stu-id="65e17-132">Code</span></span>

<span data-ttu-id="65e17-133">Poniższy kod przedstawia sposób tworzenia punktu końcowego za pomocą zabezpieczeń transportu:</span><span class="sxs-lookup"><span data-stu-id="65e17-133">The following code shows how to create an endpoint using transport security:</span></span>

[!code-csharp[c_SecurityScenarios#5](~/samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#5)]
[!code-vb[c_SecurityScenarios#5](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#5)]

### <a name="configuration"></a><span data-ttu-id="65e17-134">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="65e17-134">Configuration</span></span>

<span data-ttu-id="65e17-135">Poniższy kod ustawia ten sam punkt końcowy, za pomocą konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="65e17-135">The following code sets up the same endpoint using configuration.</span></span> <span data-ttu-id="65e17-136">Klient nie został uwierzytelniony przy użyciu dowolnego mechanizmu i w związku z tym jest anonimowy.</span><span class="sxs-lookup"><span data-stu-id="65e17-136">The client is not authenticated by any mechanism, and is therefore anonymous.</span></span>

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

## <a name="client"></a><span data-ttu-id="65e17-137">Klient</span><span class="sxs-lookup"><span data-stu-id="65e17-137">Client</span></span>

<span data-ttu-id="65e17-138">Następujący kod i konfiguracji są przeznaczone do uruchamiania niezależnie.</span><span class="sxs-lookup"><span data-stu-id="65e17-138">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="65e17-139">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="65e17-139">Do one of the following:</span></span>

- <span data-ttu-id="65e17-140">Tworzenie klienta autonomicznego przy użyciu kodu (i kodu klienta).</span><span class="sxs-lookup"><span data-stu-id="65e17-140">Create a stand-alone client using the code (and client code).</span></span>

- <span data-ttu-id="65e17-141">Tworzenie klienta, który nie definiuje żadnych adresy punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="65e17-141">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="65e17-142">Zamiast tego należy użyć konstruktora klienta, który przyjmuje nazwę konfiguracji jako argument.</span><span class="sxs-lookup"><span data-stu-id="65e17-142">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="65e17-143">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="65e17-143">For example:</span></span>

     [!code-csharp[C_SecurityScenarios#0](~/samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]

### <a name="code"></a><span data-ttu-id="65e17-144">Kod</span><span class="sxs-lookup"><span data-stu-id="65e17-144">Code</span></span>

[!code-csharp[c_SecurityScenarios#6](~/samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#6)]
[!code-vb[c_SecurityScenarios#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#6)]

### <a name="configuration"></a><span data-ttu-id="65e17-145">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="65e17-145">Configuration</span></span>

<span data-ttu-id="65e17-146">Następująca konfiguracja może służyć zamiast kodu do konfiguracji obsługiwanej usługi.</span><span class="sxs-lookup"><span data-stu-id="65e17-146">The following configuration can be used instead of the code to set up the service.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="65e17-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="65e17-147">See also</span></span>

- [<span data-ttu-id="65e17-148">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="65e17-148">Security Overview</span></span>](security-overview.md)
- [<span data-ttu-id="65e17-149">Zabezpieczenia transportu WS</span><span class="sxs-lookup"><span data-stu-id="65e17-149">WS Transport Security</span></span>](../samples/ws-transport-security.md)
- [<span data-ttu-id="65e17-150">Przegląd zabezpieczeń transportu</span><span class="sxs-lookup"><span data-stu-id="65e17-150">Transport Security Overview</span></span>](transport-security-overview.md)
- <span data-ttu-id="65e17-151">[Model zabezpieczeń dla systemu Windows Server AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="65e17-151">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
