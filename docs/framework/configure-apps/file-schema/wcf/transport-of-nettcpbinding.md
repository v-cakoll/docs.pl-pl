---
title: <transport> dla <netTcpBinding>
ms.date: 03/30/2017
ms.assetid: 49462e0a-66e1-463f-b3e1-c83a441673c6
ms.openlocfilehash: 265b68e058919d1d5c5f1dbcfb1419b57be9aeab
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915548"
---
# <a name="transport-of-nettcpbinding"></a><span data-ttu-id="9775d-102">\<Transport > \<NetTcpBinding ></span><span class="sxs-lookup"><span data-stu-id="9775d-102">\<transport> of \<netTcpBinding></span></span>
<span data-ttu-id="9775d-103">Definiuje typ wymagań dotyczących zabezpieczeń na poziomie komunikatów dla punktu końcowego skonfigurowanego przy użyciu [ \<> NetTcpBinding](nettcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="9775d-103">Defines the type of message-level security requirements for an endpoint configured with the [\<netTcpBinding>](nettcpbinding.md).</span></span>  
  
 <span data-ttu-id="9775d-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9775d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="9775d-105">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="9775d-105">\<bindings></span></span>  
<span data-ttu-id="9775d-106">\<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="9775d-106">\<netTcpBinding></span></span>  
<span data-ttu-id="9775d-107">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="9775d-107">\<binding></span></span>  
<span data-ttu-id="9775d-108">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="9775d-108">\<security></span></span>  
<span data-ttu-id="9775d-109">\<transport></span><span class="sxs-lookup"><span data-stu-id="9775d-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9775d-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="9775d-110">Syntax</span></span>  
  
```xml  
<netTcpBinding>
  <binding>
    <security mode="None|Transport|Message|TransportWithMessageCredential">
      <transport clientCredentialType="None|Windows|Certificate"
                 protectionLevel="None|Sign|EncryptAndSign"
                 sslProtocols="Tls|Tls11|Tls12">
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</netTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9775d-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9775d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="9775d-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9775d-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9775d-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9775d-113">Attributes</span></span>  
  
|<span data-ttu-id="9775d-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="9775d-114">Attribute</span></span>|<span data-ttu-id="9775d-115">Opis</span><span class="sxs-lookup"><span data-stu-id="9775d-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9775d-116">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="9775d-116">clientCredentialType</span></span>|<span data-ttu-id="9775d-117">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="9775d-117">Optional.</span></span> <span data-ttu-id="9775d-118">Określa typ poświadczeń, które mają być używane podczas uwierzytelniania klienta przy użyciu zabezpieczeń transportu.</span><span class="sxs-lookup"><span data-stu-id="9775d-118">Specifies the type of credential to be used when performing client authentication using Transport security.</span></span><br /><br /> <span data-ttu-id="9775d-119">— Wartość domyślna to `Windows`.</span><span class="sxs-lookup"><span data-stu-id="9775d-119">-   The default value is `Windows`.</span></span><br /><span data-ttu-id="9775d-120">-Ten atrybut jest typu <xref:System.ServiceModel.TcpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="9775d-120">-   This attribute is of type <xref:System.ServiceModel.TcpClientCredentialType>.</span></span>|  
|<span data-ttu-id="9775d-121">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="9775d-121">protectionLevel</span></span>|<span data-ttu-id="9775d-122">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="9775d-122">Optional.</span></span> <span data-ttu-id="9775d-123">Definiuje zabezpieczenia na poziomie transportu TCP.</span><span class="sxs-lookup"><span data-stu-id="9775d-123">Defines security at the level of the TCP transport.</span></span> <span data-ttu-id="9775d-124">Komunikaty podpisywania zmniejszają ryzyko naruszenia przez osobę trzecią komunikatu podczas jego przesyłania.</span><span class="sxs-lookup"><span data-stu-id="9775d-124">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="9775d-125">Szyfrowanie zapewnia prywatność na poziomie danych podczas transportu.</span><span class="sxs-lookup"><span data-stu-id="9775d-125">Encryption provides data-level privacy during transport.</span></span><br /><br /> <span data-ttu-id="9775d-126">Wartość domyślna to `EncryptAndSign`.</span><span class="sxs-lookup"><span data-stu-id="9775d-126">The default value is `EncryptAndSign`.</span></span>|  
|<span data-ttu-id="9775d-127">SslProtocols określająca</span><span class="sxs-lookup"><span data-stu-id="9775d-127">sslProtocols</span></span>|<span data-ttu-id="9775d-128">Wartość flagi wyliczenia SslProtocols określająca, która określa, które SslProtocols określająca są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="9775d-128">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="9775d-129">Wartość domyślna to TLS&#124;Tls11&#124;Tls12.</span><span class="sxs-lookup"><span data-stu-id="9775d-129">The default is Tls&#124;Tls11&#124;Tls12.</span></span>|  
|<span data-ttu-id="9775d-130">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="9775d-130">policyEnforcement</span></span>|<span data-ttu-id="9775d-131">To Wyliczenie określa, <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> Kiedy należy wymusić.</span><span class="sxs-lookup"><span data-stu-id="9775d-131">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="9775d-132">1.  Nigdy — zasady nigdy nie są wymuszane (ochrona rozszerzona jest wyłączona).</span><span class="sxs-lookup"><span data-stu-id="9775d-132">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="9775d-133">2.  WhenSupported — zasady są wymuszane tylko wtedy, gdy klient obsługuje ochronę rozszerzoną.</span><span class="sxs-lookup"><span data-stu-id="9775d-133">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="9775d-134">3.  Zawsze — zasady są zawsze wymuszane.</span><span class="sxs-lookup"><span data-stu-id="9775d-134">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="9775d-135">Klienci, którzy nie obsługują rozszerzonej ochrony, nie będą uwierzytelniani.</span><span class="sxs-lookup"><span data-stu-id="9775d-135">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="9775d-136">clientCredentialtype — atrybut</span><span class="sxs-lookup"><span data-stu-id="9775d-136">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="9775d-137">Wartość</span><span class="sxs-lookup"><span data-stu-id="9775d-137">Value</span></span>|<span data-ttu-id="9775d-138">Opis</span><span class="sxs-lookup"><span data-stu-id="9775d-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9775d-139">Brak</span><span class="sxs-lookup"><span data-stu-id="9775d-139">None</span></span>|<span data-ttu-id="9775d-140">Klient jest anonimowy.</span><span class="sxs-lookup"><span data-stu-id="9775d-140">The client is anonymous.</span></span> <span data-ttu-id="9775d-141">Wymaga to certyfikatu dla usługi.</span><span class="sxs-lookup"><span data-stu-id="9775d-141">This requires a certificate for the service.</span></span>|  
|<span data-ttu-id="9775d-142">Windows</span><span class="sxs-lookup"><span data-stu-id="9775d-142">Windows</span></span>|<span data-ttu-id="9775d-143">Określa uwierzytelnianie systemu Windows klienta przy użyciu negocjacji SP (negocjowanie protokołu Kerberos).</span><span class="sxs-lookup"><span data-stu-id="9775d-143">Specifies Windows authentication of the client using SP Negotiation (Kerberos negotiation).</span></span>|  
|<span data-ttu-id="9775d-144">Certyfikatu</span><span class="sxs-lookup"><span data-stu-id="9775d-144">Certificate</span></span>|<span data-ttu-id="9775d-145">Klient jest uwierzytelniany przy użyciu certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="9775d-145">The client is authenticated using a certificate.</span></span> <span data-ttu-id="9775d-146">Powoduje to użycie negocjacji protokołu SSL i wymaga certyfikatu dla usługi.</span><span class="sxs-lookup"><span data-stu-id="9775d-146">This uses SSL Negotiation and requires a certificate for the service.</span></span>|  
  
## <a name="protectionlevel-attribute"></a><span data-ttu-id="9775d-147">protectionLevel — atrybut</span><span class="sxs-lookup"><span data-stu-id="9775d-147">protectionLevel Attribute</span></span>  
  
|<span data-ttu-id="9775d-148">Wartość</span><span class="sxs-lookup"><span data-stu-id="9775d-148">Value</span></span>|<span data-ttu-id="9775d-149">Opis</span><span class="sxs-lookup"><span data-stu-id="9775d-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9775d-150">Brak</span><span class="sxs-lookup"><span data-stu-id="9775d-150">None</span></span>|<span data-ttu-id="9775d-151">Brak ochrony.</span><span class="sxs-lookup"><span data-stu-id="9775d-151">No protection.</span></span>|  
|<span data-ttu-id="9775d-152">Zapis</span><span class="sxs-lookup"><span data-stu-id="9775d-152">Sign</span></span>|<span data-ttu-id="9775d-153">Komunikaty są podpisane.</span><span class="sxs-lookup"><span data-stu-id="9775d-153">Messages are signed.</span></span>|  
|<span data-ttu-id="9775d-154">EncryptAndSign</span><span class="sxs-lookup"><span data-stu-id="9775d-154">EncryptAndSign</span></span>|<span data-ttu-id="9775d-155">— Komunikaty są szyfrowane i podpisane.</span><span class="sxs-lookup"><span data-stu-id="9775d-155">-   Messages are encrypted and signed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9775d-156">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9775d-156">Child Elements</span></span>  
 <span data-ttu-id="9775d-157">Brak</span><span class="sxs-lookup"><span data-stu-id="9775d-157">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9775d-158">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9775d-158">Parent Elements</span></span>  
  
|<span data-ttu-id="9775d-159">Element</span><span class="sxs-lookup"><span data-stu-id="9775d-159">Element</span></span>|<span data-ttu-id="9775d-160">Opis</span><span class="sxs-lookup"><span data-stu-id="9775d-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9775d-161">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="9775d-161">\<security></span></span>](security-of-nettcpbinding.md)|<span data-ttu-id="9775d-162">Określa możliwości [ \<zabezpieczeń > NetTcpBinding](nettcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="9775d-162">Specifies the security capabilities of the [\<netTcpBinding>](nettcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9775d-163">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9775d-163">Remarks</span></span>  
 <span data-ttu-id="9775d-164">Zabezpieczenia transportu umożliwiają integralność i poufność komunikatu protokołu SOAP oraz uwierzytelnianie wzajemne.</span><span class="sxs-lookup"><span data-stu-id="9775d-164">Use Transport security for integrity and confidentiality of the SOAP message and for mutual authentication.</span></span> <span data-ttu-id="9775d-165">Jeśli w powiązaniu wybrano ten tryb zabezpieczeń, stos kanału zostanie skonfigurowany przy użyciu bezpiecznego transportu, a komunikaty protokołu SOAP są zabezpieczone za pomocą zabezpieczeń transportu, takich jak Windows (Negotiate) lub SSL przez TCP.</span><span class="sxs-lookup"><span data-stu-id="9775d-165">If this security mode is selected on a binding, the channel stack is configured using a secure transport and the SOAP messages are secured using transport security such as Windows (Negotiate) or SSL over TCP.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9775d-166">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9775d-166">See also</span></span>

- <xref:System.ServiceModel.TcpTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetTcpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [<span data-ttu-id="9775d-167">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="9775d-167">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="9775d-168">Powiązania</span><span class="sxs-lookup"><span data-stu-id="9775d-168">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="9775d-169">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="9775d-169">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="9775d-170">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="9775d-170">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="9775d-171">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="9775d-171">\<binding></span></span>](../../../misc/binding.md)
