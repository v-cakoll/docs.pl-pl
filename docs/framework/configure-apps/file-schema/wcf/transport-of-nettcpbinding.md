---
title: <transport> dla <netTcpBinding>
ms.date: 03/30/2017
ms.assetid: 49462e0a-66e1-463f-b3e1-c83a441673c6
ms.openlocfilehash: 4ef08ad73a03dea21d27217364a7bacb46a3848e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73735934"
---
# <a name="transport-of-nettcpbinding"></a><span data-ttu-id="5c7b4-102">\<transport> dla \<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="5c7b4-102">\<transport> of \<netTcpBinding></span></span>
<span data-ttu-id="5c7b4-103">Definiuje typ wymagań dotyczących zabezpieczeń na poziomie komunikatów dla punktu końcowego skonfigurowanego przy użyciu [\<netTcpBinding>](nettcpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="5c7b4-103">Defines the type of message-level security requirements for an endpoint configured with the [\<netTcpBinding>](nettcpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netTcpBinding>**](nettcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-nettcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="5c7b4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5c7b4-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5c7b4-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5c7b4-105">Attributes and Elements</span></span>  
 <span data-ttu-id="5c7b4-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5c7b4-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5c7b4-107">Attributes</span></span>  
  
|<span data-ttu-id="5c7b4-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5c7b4-108">Attribute</span></span>|<span data-ttu-id="5c7b4-109">Opis</span><span class="sxs-lookup"><span data-stu-id="5c7b4-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5c7b4-110">Powiązania ClientCredentialType</span><span class="sxs-lookup"><span data-stu-id="5c7b4-110">clientCredentialType</span></span>|<span data-ttu-id="5c7b4-111">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-111">Optional.</span></span> <span data-ttu-id="5c7b4-112">Określa typ poświadczeń, które mają być używane podczas uwierzytelniania klienta przy użyciu zabezpieczeń transportu.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-112">Specifies the type of credential to be used when performing client authentication using Transport security.</span></span><br /><br /> <span data-ttu-id="5c7b4-113">— Wartość domyślna to `Windows` .</span><span class="sxs-lookup"><span data-stu-id="5c7b4-113">-   The default value is `Windows`.</span></span><br /><span data-ttu-id="5c7b4-114">-Ten atrybut jest typu <xref:System.ServiceModel.TcpClientCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="5c7b4-114">-   This attribute is of type <xref:System.ServiceModel.TcpClientCredentialType>.</span></span>|  
|<span data-ttu-id="5c7b4-115">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="5c7b4-115">protectionLevel</span></span>|<span data-ttu-id="5c7b4-116">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-116">Optional.</span></span> <span data-ttu-id="5c7b4-117">Definiuje zabezpieczenia na poziomie transportu TCP.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-117">Defines security at the level of the TCP transport.</span></span> <span data-ttu-id="5c7b4-118">Komunikaty podpisywania zmniejszają ryzyko naruszenia przez osobę trzecią komunikatu podczas jego przesyłania.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-118">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="5c7b4-119">Szyfrowanie zapewnia prywatność na poziomie danych podczas transportu.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-119">Encryption provides data-level privacy during transport.</span></span><br /><br /> <span data-ttu-id="5c7b4-120">Wartość domyślna to `EncryptAndSign`.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-120">The default value is `EncryptAndSign`.</span></span>|  
|<span data-ttu-id="5c7b4-121">SslProtocols określająca</span><span class="sxs-lookup"><span data-stu-id="5c7b4-121">sslProtocols</span></span>|<span data-ttu-id="5c7b4-122">Wartość flagi wyliczenia SslProtocols określająca, która określa, które SslProtocols określająca są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-122">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="5c7b4-123">Wartość domyślna to TLS&#124;Tls11&#124;Tls12.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-123">The default is Tls&#124;Tls11&#124;Tls12.</span></span>|  
|<span data-ttu-id="5c7b4-124">Zasady PolicyEnforcement</span><span class="sxs-lookup"><span data-stu-id="5c7b4-124">policyEnforcement</span></span>|<span data-ttu-id="5c7b4-125">To Wyliczenie określa, kiedy <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> należy wymusić.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-125">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="5c7b4-126">1. nigdy — zasady nigdy nie są wymuszane (ochrona rozszerzona jest wyłączona).</span><span class="sxs-lookup"><span data-stu-id="5c7b4-126">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="5c7b4-127">2. WhenSupported — zasady są wymuszane tylko wtedy, gdy klient obsługuje ochronę rozszerzoną.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-127">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="5c7b4-128">3. zawsze — zasady są zawsze wymuszane.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-128">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="5c7b4-129">Klienci, którzy nie obsługują rozszerzonej ochrony, nie będą uwierzytelniani.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-129">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="5c7b4-130">clientCredentialtype — atrybut</span><span class="sxs-lookup"><span data-stu-id="5c7b4-130">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="5c7b4-131">Wartość</span><span class="sxs-lookup"><span data-stu-id="5c7b4-131">Value</span></span>|<span data-ttu-id="5c7b4-132">Opis</span><span class="sxs-lookup"><span data-stu-id="5c7b4-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5c7b4-133">Brak</span><span class="sxs-lookup"><span data-stu-id="5c7b4-133">None</span></span>|<span data-ttu-id="5c7b4-134">Klient jest anonimowy.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-134">The client is anonymous.</span></span> <span data-ttu-id="5c7b4-135">Wymaga to certyfikatu dla usługi.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-135">This requires a certificate for the service.</span></span>|  
|<span data-ttu-id="5c7b4-136">Windows</span><span class="sxs-lookup"><span data-stu-id="5c7b4-136">Windows</span></span>|<span data-ttu-id="5c7b4-137">Określa uwierzytelnianie systemu Windows klienta przy użyciu negocjacji SP (negocjowanie protokołu Kerberos).</span><span class="sxs-lookup"><span data-stu-id="5c7b4-137">Specifies Windows authentication of the client using SP Negotiation (Kerberos negotiation).</span></span>|  
|<span data-ttu-id="5c7b4-138">Certyfikat</span><span class="sxs-lookup"><span data-stu-id="5c7b4-138">Certificate</span></span>|<span data-ttu-id="5c7b4-139">Klient jest uwierzytelniany przy użyciu certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-139">The client is authenticated using a certificate.</span></span> <span data-ttu-id="5c7b4-140">Powoduje to użycie negocjacji protokołu SSL i wymaga certyfikatu dla usługi.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-140">This uses SSL Negotiation and requires a certificate for the service.</span></span>|  
  
## <a name="protectionlevel-attribute"></a><span data-ttu-id="5c7b4-141">protectionLevel — atrybut</span><span class="sxs-lookup"><span data-stu-id="5c7b4-141">protectionLevel Attribute</span></span>  
  
|<span data-ttu-id="5c7b4-142">Wartość</span><span class="sxs-lookup"><span data-stu-id="5c7b4-142">Value</span></span>|<span data-ttu-id="5c7b4-143">Opis</span><span class="sxs-lookup"><span data-stu-id="5c7b4-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5c7b4-144">Brak</span><span class="sxs-lookup"><span data-stu-id="5c7b4-144">None</span></span>|<span data-ttu-id="5c7b4-145">Brak ochrony.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-145">No protection.</span></span>|  
|<span data-ttu-id="5c7b4-146">Znak</span><span class="sxs-lookup"><span data-stu-id="5c7b4-146">Sign</span></span>|<span data-ttu-id="5c7b4-147">Komunikaty są podpisane.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-147">Messages are signed.</span></span>|  
|<span data-ttu-id="5c7b4-148">EncryptAndSign</span><span class="sxs-lookup"><span data-stu-id="5c7b4-148">EncryptAndSign</span></span>|<span data-ttu-id="5c7b4-149">— Komunikaty są szyfrowane i podpisane.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-149">-   Messages are encrypted and signed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5c7b4-150">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5c7b4-150">Child Elements</span></span>  
 <span data-ttu-id="5c7b4-151">Brak</span><span class="sxs-lookup"><span data-stu-id="5c7b4-151">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5c7b4-152">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5c7b4-152">Parent Elements</span></span>  
  
|<span data-ttu-id="5c7b4-153">Element</span><span class="sxs-lookup"><span data-stu-id="5c7b4-153">Element</span></span>|<span data-ttu-id="5c7b4-154">Opis</span><span class="sxs-lookup"><span data-stu-id="5c7b4-154">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-nettcpbinding.md)|<span data-ttu-id="5c7b4-155">Określa możliwości zabezpieczeń programu [\<netTcpBinding>](nettcpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="5c7b4-155">Specifies the security capabilities of the [\<netTcpBinding>](nettcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5c7b4-156">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5c7b4-156">Remarks</span></span>  
 <span data-ttu-id="5c7b4-157">Zabezpieczenia transportu umożliwiają integralność i poufność komunikatu protokołu SOAP oraz uwierzytelnianie wzajemne.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-157">Use Transport security for integrity and confidentiality of the SOAP message and for mutual authentication.</span></span> <span data-ttu-id="5c7b4-158">Jeśli w powiązaniu wybrano ten tryb zabezpieczeń, stos kanału zostanie skonfigurowany przy użyciu bezpiecznego transportu, a komunikaty protokołu SOAP są zabezpieczone za pomocą zabezpieczeń transportu, takich jak Windows (Negotiate) lub SSL przez TCP.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-158">If this security mode is selected on a binding, the channel stack is configured using a secure transport and the SOAP messages are secured using transport security such as Windows (Negotiate) or SSL over TCP.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c7b4-159">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5c7b4-159">See also</span></span>

- <xref:System.ServiceModel.TcpTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetTcpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [<span data-ttu-id="5c7b4-160">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="5c7b4-160">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="5c7b4-161">Powiązania</span><span class="sxs-lookup"><span data-stu-id="5c7b4-161">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="5c7b4-162">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="5c7b4-162">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="5c7b4-163">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="5c7b4-163">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
