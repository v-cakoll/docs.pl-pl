---
title: <transport> dla <netTcpBinding>
ms.date: 03/30/2017
ms.assetid: 49462e0a-66e1-463f-b3e1-c83a441673c6
ms.openlocfilehash: 41f11be9b4ae8f7a7535c9766965de8575cff784
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399321"
---
# <a name="transport-of-nettcpbinding"></a><span data-ttu-id="66b55-102">\<Transport > \<NetTcpBinding ></span><span class="sxs-lookup"><span data-stu-id="66b55-102">\<transport> of \<netTcpBinding></span></span>
<span data-ttu-id="66b55-103">Definiuje typ wymagań dotyczących zabezpieczeń na poziomie komunikatów dla punktu końcowego skonfigurowanego przy użyciu [ \<> NetTcpBinding](nettcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="66b55-103">Defines the type of message-level security requirements for an endpoint configured with the [\<netTcpBinding>](nettcpbinding.md).</span></span>  
  
<span data-ttu-id="66b55-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="66b55-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="66b55-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="66b55-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="66b55-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> powiązań**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="66b55-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="66b55-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netTcpBinding >** ](nettcpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="66b55-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netTcpBinding>**](nettcpbinding.md)</span></span>\
<span data-ttu-id="66b55-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> powiązania**</span><span class="sxs-lookup"><span data-stu-id="66b55-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="66b55-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zabezpieczeń**](security-of-nettcpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="66b55-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-nettcpbinding.md)</span></span>\
<span data-ttu-id="66b55-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> transportu**</span><span class="sxs-lookup"><span data-stu-id="66b55-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66b55-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="66b55-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="66b55-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="66b55-112">Attributes and Elements</span></span>  
 <span data-ttu-id="66b55-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="66b55-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="66b55-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="66b55-114">Attributes</span></span>  
  
|<span data-ttu-id="66b55-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="66b55-115">Attribute</span></span>|<span data-ttu-id="66b55-116">Opis</span><span class="sxs-lookup"><span data-stu-id="66b55-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="66b55-117">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="66b55-117">clientCredentialType</span></span>|<span data-ttu-id="66b55-118">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="66b55-118">Optional.</span></span> <span data-ttu-id="66b55-119">Określa typ poświadczeń, które mają być używane podczas uwierzytelniania klienta przy użyciu zabezpieczeń transportu.</span><span class="sxs-lookup"><span data-stu-id="66b55-119">Specifies the type of credential to be used when performing client authentication using Transport security.</span></span><br /><br /> <span data-ttu-id="66b55-120">— Wartość domyślna to `Windows`.</span><span class="sxs-lookup"><span data-stu-id="66b55-120">-   The default value is `Windows`.</span></span><br /><span data-ttu-id="66b55-121">-Ten atrybut jest typu <xref:System.ServiceModel.TcpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="66b55-121">-   This attribute is of type <xref:System.ServiceModel.TcpClientCredentialType>.</span></span>|  
|<span data-ttu-id="66b55-122">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="66b55-122">protectionLevel</span></span>|<span data-ttu-id="66b55-123">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="66b55-123">Optional.</span></span> <span data-ttu-id="66b55-124">Definiuje zabezpieczenia na poziomie transportu TCP.</span><span class="sxs-lookup"><span data-stu-id="66b55-124">Defines security at the level of the TCP transport.</span></span> <span data-ttu-id="66b55-125">Komunikaty podpisywania zmniejszają ryzyko naruszenia przez osobę trzecią komunikatu podczas jego przesyłania.</span><span class="sxs-lookup"><span data-stu-id="66b55-125">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="66b55-126">Szyfrowanie zapewnia prywatność na poziomie danych podczas transportu.</span><span class="sxs-lookup"><span data-stu-id="66b55-126">Encryption provides data-level privacy during transport.</span></span><br /><br /> <span data-ttu-id="66b55-127">Wartość domyślna to `EncryptAndSign`.</span><span class="sxs-lookup"><span data-stu-id="66b55-127">The default value is `EncryptAndSign`.</span></span>|  
|<span data-ttu-id="66b55-128">SslProtocols określająca</span><span class="sxs-lookup"><span data-stu-id="66b55-128">sslProtocols</span></span>|<span data-ttu-id="66b55-129">Wartość flagi wyliczenia SslProtocols określająca, która określa, które SslProtocols określająca są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="66b55-129">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="66b55-130">Wartość domyślna to TLS&#124;Tls11&#124;Tls12.</span><span class="sxs-lookup"><span data-stu-id="66b55-130">The default is Tls&#124;Tls11&#124;Tls12.</span></span>|  
|<span data-ttu-id="66b55-131">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="66b55-131">policyEnforcement</span></span>|<span data-ttu-id="66b55-132">To Wyliczenie określa, <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> Kiedy należy wymusić.</span><span class="sxs-lookup"><span data-stu-id="66b55-132">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="66b55-133">1.  Nigdy — zasady nigdy nie są wymuszane (ochrona rozszerzona jest wyłączona).</span><span class="sxs-lookup"><span data-stu-id="66b55-133">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="66b55-134">2.  WhenSupported — zasady są wymuszane tylko wtedy, gdy klient obsługuje ochronę rozszerzoną.</span><span class="sxs-lookup"><span data-stu-id="66b55-134">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="66b55-135">3.  Zawsze — zasady są zawsze wymuszane.</span><span class="sxs-lookup"><span data-stu-id="66b55-135">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="66b55-136">Klienci, którzy nie obsługują rozszerzonej ochrony, nie będą uwierzytelniani.</span><span class="sxs-lookup"><span data-stu-id="66b55-136">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="66b55-137">clientCredentialtype — atrybut</span><span class="sxs-lookup"><span data-stu-id="66b55-137">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="66b55-138">Wartość</span><span class="sxs-lookup"><span data-stu-id="66b55-138">Value</span></span>|<span data-ttu-id="66b55-139">Opis</span><span class="sxs-lookup"><span data-stu-id="66b55-139">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="66b55-140">Brak</span><span class="sxs-lookup"><span data-stu-id="66b55-140">None</span></span>|<span data-ttu-id="66b55-141">Klient jest anonimowy.</span><span class="sxs-lookup"><span data-stu-id="66b55-141">The client is anonymous.</span></span> <span data-ttu-id="66b55-142">Wymaga to certyfikatu dla usługi.</span><span class="sxs-lookup"><span data-stu-id="66b55-142">This requires a certificate for the service.</span></span>|  
|<span data-ttu-id="66b55-143">Windows</span><span class="sxs-lookup"><span data-stu-id="66b55-143">Windows</span></span>|<span data-ttu-id="66b55-144">Określa uwierzytelnianie systemu Windows klienta przy użyciu negocjacji SP (negocjowanie protokołu Kerberos).</span><span class="sxs-lookup"><span data-stu-id="66b55-144">Specifies Windows authentication of the client using SP Negotiation (Kerberos negotiation).</span></span>|  
|<span data-ttu-id="66b55-145">Certyfikatu</span><span class="sxs-lookup"><span data-stu-id="66b55-145">Certificate</span></span>|<span data-ttu-id="66b55-146">Klient jest uwierzytelniany przy użyciu certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="66b55-146">The client is authenticated using a certificate.</span></span> <span data-ttu-id="66b55-147">Powoduje to użycie negocjacji protokołu SSL i wymaga certyfikatu dla usługi.</span><span class="sxs-lookup"><span data-stu-id="66b55-147">This uses SSL Negotiation and requires a certificate for the service.</span></span>|  
  
## <a name="protectionlevel-attribute"></a><span data-ttu-id="66b55-148">protectionLevel — atrybut</span><span class="sxs-lookup"><span data-stu-id="66b55-148">protectionLevel Attribute</span></span>  
  
|<span data-ttu-id="66b55-149">Wartość</span><span class="sxs-lookup"><span data-stu-id="66b55-149">Value</span></span>|<span data-ttu-id="66b55-150">Opis</span><span class="sxs-lookup"><span data-stu-id="66b55-150">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="66b55-151">Brak</span><span class="sxs-lookup"><span data-stu-id="66b55-151">None</span></span>|<span data-ttu-id="66b55-152">Brak ochrony.</span><span class="sxs-lookup"><span data-stu-id="66b55-152">No protection.</span></span>|  
|<span data-ttu-id="66b55-153">Zapis</span><span class="sxs-lookup"><span data-stu-id="66b55-153">Sign</span></span>|<span data-ttu-id="66b55-154">Komunikaty są podpisane.</span><span class="sxs-lookup"><span data-stu-id="66b55-154">Messages are signed.</span></span>|  
|<span data-ttu-id="66b55-155">EncryptAndSign</span><span class="sxs-lookup"><span data-stu-id="66b55-155">EncryptAndSign</span></span>|<span data-ttu-id="66b55-156">— Komunikaty są szyfrowane i podpisane.</span><span class="sxs-lookup"><span data-stu-id="66b55-156">-   Messages are encrypted and signed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="66b55-157">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="66b55-157">Child Elements</span></span>  
 <span data-ttu-id="66b55-158">Brak</span><span class="sxs-lookup"><span data-stu-id="66b55-158">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="66b55-159">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="66b55-159">Parent Elements</span></span>  
  
|<span data-ttu-id="66b55-160">Element</span><span class="sxs-lookup"><span data-stu-id="66b55-160">Element</span></span>|<span data-ttu-id="66b55-161">Opis</span><span class="sxs-lookup"><span data-stu-id="66b55-161">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="66b55-162">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="66b55-162">\<security></span></span>](security-of-nettcpbinding.md)|<span data-ttu-id="66b55-163">Określa możliwości [ \<zabezpieczeń > NetTcpBinding](nettcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="66b55-163">Specifies the security capabilities of the [\<netTcpBinding>](nettcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="66b55-164">Uwagi</span><span class="sxs-lookup"><span data-stu-id="66b55-164">Remarks</span></span>  
 <span data-ttu-id="66b55-165">Zabezpieczenia transportu umożliwiają integralność i poufność komunikatu protokołu SOAP oraz uwierzytelnianie wzajemne.</span><span class="sxs-lookup"><span data-stu-id="66b55-165">Use Transport security for integrity and confidentiality of the SOAP message and for mutual authentication.</span></span> <span data-ttu-id="66b55-166">Jeśli w powiązaniu wybrano ten tryb zabezpieczeń, stos kanału zostanie skonfigurowany przy użyciu bezpiecznego transportu, a komunikaty protokołu SOAP są zabezpieczone za pomocą zabezpieczeń transportu, takich jak Windows (Negotiate) lub SSL przez TCP.</span><span class="sxs-lookup"><span data-stu-id="66b55-166">If this security mode is selected on a binding, the channel stack is configured using a secure transport and the SOAP messages are secured using transport security such as Windows (Negotiate) or SSL over TCP.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66b55-167">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="66b55-167">See also</span></span>

- <xref:System.ServiceModel.TcpTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetTcpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [<span data-ttu-id="66b55-168">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="66b55-168">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="66b55-169">Powiązania</span><span class="sxs-lookup"><span data-stu-id="66b55-169">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="66b55-170">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="66b55-170">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="66b55-171">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="66b55-171">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="66b55-172">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="66b55-172">\<binding></span></span>](../../../misc/binding.md)
