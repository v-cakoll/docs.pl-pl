---
title: <transport> z <netTcpBinding>
ms.date: 03/30/2017
ms.assetid: 49462e0a-66e1-463f-b3e1-c83a441673c6
ms.openlocfilehash: de1f87d8074bbf3d85f6092a4ac316f5fd20052c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57355605"
---
# <a name="transport-of-nettcpbinding"></a><span data-ttu-id="24274-102">\<transport > z \<netTcpBinding ></span><span class="sxs-lookup"><span data-stu-id="24274-102">\<transport> of \<netTcpBinding></span></span>
<span data-ttu-id="24274-103">Określa typ zabezpieczenia na poziomie wiadomości dotyczące punkty końcowe skonfigurowane za pomocą [ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="24274-103">Defines the type of message-level security requirements for an endpoint configured with the [\<netTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span></span>  
  
 <span data-ttu-id="24274-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="24274-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="24274-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="24274-105">\<bindings></span></span>  
<span data-ttu-id="24274-106">\<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="24274-106">\<netTcpBinding></span></span>  
<span data-ttu-id="24274-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="24274-107">\<binding></span></span>  
<span data-ttu-id="24274-108">\<security></span><span class="sxs-lookup"><span data-stu-id="24274-108">\<security></span></span>  
<span data-ttu-id="24274-109">\<transport></span><span class="sxs-lookup"><span data-stu-id="24274-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24274-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="24274-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="24274-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="24274-111">Attributes and Elements</span></span>  
 <span data-ttu-id="24274-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="24274-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="24274-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="24274-113">Attributes</span></span>  
  
|<span data-ttu-id="24274-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="24274-114">Attribute</span></span>|<span data-ttu-id="24274-115">Opis</span><span class="sxs-lookup"><span data-stu-id="24274-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="24274-116">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="24274-116">clientCredentialType</span></span>|<span data-ttu-id="24274-117">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="24274-117">Optional.</span></span> <span data-ttu-id="24274-118">Określa typ poświadczeń ma być używany podczas uwierzytelniania klientów za pomocą zabezpieczeń transportu.</span><span class="sxs-lookup"><span data-stu-id="24274-118">Specifies the type of credential to be used when performing client authentication using Transport security.</span></span><br /><br /> <span data-ttu-id="24274-119">— Wartość domyślna to `Windows`.</span><span class="sxs-lookup"><span data-stu-id="24274-119">-   The default value is `Windows`.</span></span><br /><span data-ttu-id="24274-120">— Ten atrybut jest typu <xref:System.ServiceModel.TcpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="24274-120">-   This attribute is of type <xref:System.ServiceModel.TcpClientCredentialType>.</span></span>|  
|<span data-ttu-id="24274-121">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="24274-121">protectionLevel</span></span>|<span data-ttu-id="24274-122">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="24274-122">Optional.</span></span> <span data-ttu-id="24274-123">Definiuje zabezpieczenia na poziomie warstwy transportowej TCP.</span><span class="sxs-lookup"><span data-stu-id="24274-123">Defines security at the level of the TCP transport.</span></span> <span data-ttu-id="24274-124">Podpisywania wiadomości zmniejsza ryzyko związane z innej naruszeniu komunikat, gdy są przesyłane.</span><span class="sxs-lookup"><span data-stu-id="24274-124">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="24274-125">Szyfrowanie zapewnia ochronę poufności poziom danych, podczas transportu.</span><span class="sxs-lookup"><span data-stu-id="24274-125">Encryption provides data-level privacy during transport.</span></span><br /><br /> <span data-ttu-id="24274-126">Wartość domyślna to `EncryptAndSign`.</span><span class="sxs-lookup"><span data-stu-id="24274-126">The default value is `EncryptAndSign`.</span></span>|  
|<span data-ttu-id="24274-127">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="24274-127">sslProtocols</span></span>|<span data-ttu-id="24274-128">Wartość flagi wyliczenia SslProtocols określająca SslProtocols, które są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="24274-128">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="24274-129">Wartość domyślna to protokołu Tls&#124;Tls11&#124;Tls12.</span><span class="sxs-lookup"><span data-stu-id="24274-129">The default is Tls&#124;Tls11&#124;Tls12.</span></span>|  
|<span data-ttu-id="24274-130">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="24274-130">policyEnforcement</span></span>|<span data-ttu-id="24274-131">To wyliczenie Określa, kiedy <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> powinny być wymuszane.</span><span class="sxs-lookup"><span data-stu-id="24274-131">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="24274-132">1.  Nigdy nie — zasady nigdy nie są wymuszane (ochrony rozszerzonej jest wyłączone).</span><span class="sxs-lookup"><span data-stu-id="24274-132">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="24274-133">2.  WhenSupported — zasady są wymuszane tylko wtedy, gdy klient obsługuje ochrony rozszerzonej.</span><span class="sxs-lookup"><span data-stu-id="24274-133">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="24274-134">3.  Zawsze — zasady zawsze są wymuszane.</span><span class="sxs-lookup"><span data-stu-id="24274-134">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="24274-135">Klienci, którzy nie obsługują ochrony rozszerzonej zakończy się niepowodzeniem do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="24274-135">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="24274-136">właściwości ClientCredentialType o wartości atrybutu</span><span class="sxs-lookup"><span data-stu-id="24274-136">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="24274-137">Wartość</span><span class="sxs-lookup"><span data-stu-id="24274-137">Value</span></span>|<span data-ttu-id="24274-138">Opis</span><span class="sxs-lookup"><span data-stu-id="24274-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="24274-139">Brak</span><span class="sxs-lookup"><span data-stu-id="24274-139">None</span></span>|<span data-ttu-id="24274-140">Klient jest anonimowy.</span><span class="sxs-lookup"><span data-stu-id="24274-140">The client is anonymous.</span></span> <span data-ttu-id="24274-141">Wymaga certyfikatu usługi.</span><span class="sxs-lookup"><span data-stu-id="24274-141">This requires a certificate for the service.</span></span>|  
|<span data-ttu-id="24274-142">Windows</span><span class="sxs-lookup"><span data-stu-id="24274-142">Windows</span></span>|<span data-ttu-id="24274-143">Określa Windows uwierzytelniania klienta przy użyciu negocjacji SP (negocjacji protokołu Kerberos).</span><span class="sxs-lookup"><span data-stu-id="24274-143">Specifies Windows authentication of the client using SP Negotiation (Kerberos negotiation).</span></span>|  
|<span data-ttu-id="24274-144">Certyfikat</span><span class="sxs-lookup"><span data-stu-id="24274-144">Certificate</span></span>|<span data-ttu-id="24274-145">Klient jest uwierzytelniany przy użyciu certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="24274-145">The client is authenticated using a certificate.</span></span> <span data-ttu-id="24274-146">Ten wymaga negocjacji w protokole SSL i wymaga certyfikatu usługi.</span><span class="sxs-lookup"><span data-stu-id="24274-146">This uses SSL Negotiation and requires a certificate for the service.</span></span>|  
  
## <a name="protectionlevel-attribute"></a><span data-ttu-id="24274-147">protectionLevel atrybutu</span><span class="sxs-lookup"><span data-stu-id="24274-147">protectionLevel Attribute</span></span>  
  
|<span data-ttu-id="24274-148">Wartość</span><span class="sxs-lookup"><span data-stu-id="24274-148">Value</span></span>|<span data-ttu-id="24274-149">Opis</span><span class="sxs-lookup"><span data-stu-id="24274-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="24274-150">Brak</span><span class="sxs-lookup"><span data-stu-id="24274-150">None</span></span>|<span data-ttu-id="24274-151">Brak ochrony.</span><span class="sxs-lookup"><span data-stu-id="24274-151">No protection.</span></span>|  
|<span data-ttu-id="24274-152">Logowanie</span><span class="sxs-lookup"><span data-stu-id="24274-152">Sign</span></span>|<span data-ttu-id="24274-153">Komunikaty są podpisane.</span><span class="sxs-lookup"><span data-stu-id="24274-153">Messages are signed.</span></span>|  
|<span data-ttu-id="24274-154">EncryptAndSign</span><span class="sxs-lookup"><span data-stu-id="24274-154">EncryptAndSign</span></span>|<span data-ttu-id="24274-155">— Liczba komunikatów jest zaszyfrowany i podpisany.</span><span class="sxs-lookup"><span data-stu-id="24274-155">-   Messages are encrypted and signed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="24274-156">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="24274-156">Child Elements</span></span>  
 <span data-ttu-id="24274-157">Brak</span><span class="sxs-lookup"><span data-stu-id="24274-157">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="24274-158">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="24274-158">Parent Elements</span></span>  
  
|<span data-ttu-id="24274-159">Element</span><span class="sxs-lookup"><span data-stu-id="24274-159">Element</span></span>|<span data-ttu-id="24274-160">Opis</span><span class="sxs-lookup"><span data-stu-id="24274-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="24274-161">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="24274-161">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)|<span data-ttu-id="24274-162">Określa możliwości zabezpieczeń [ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="24274-162">Specifies the security capabilities of the [\<netTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="24274-163">Uwagi</span><span class="sxs-lookup"><span data-stu-id="24274-163">Remarks</span></span>  
 <span data-ttu-id="24274-164">Za pomocą zabezpieczeń transportu integralności i poufności komunikatu protokołu SOAP, jak i do wzajemnego uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="24274-164">Use Transport security for integrity and confidentiality of the SOAP message and for mutual authentication.</span></span> <span data-ttu-id="24274-165">Zaznaczenie tego trybu zabezpieczeń w powiązaniu ze stosu kanał jest skonfigurowany przy użyciu bezpiecznym transportem i komunikaty protokołu SOAP są zabezpieczone za pomocą zabezpieczeń transportu, takich jak Windows (Negotiate) lub protokołu SSL, za pośrednictwem protokołu TCP.</span><span class="sxs-lookup"><span data-stu-id="24274-165">If this security mode is selected on a binding, the channel stack is configured using a secure transport and the SOAP messages are secured using transport security such as Windows (Negotiate) or SSL over TCP.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24274-166">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="24274-166">See also</span></span>
- <xref:System.ServiceModel.TcpTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetTcpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [<span data-ttu-id="24274-167">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="24274-167">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="24274-168">Powiązania</span><span class="sxs-lookup"><span data-stu-id="24274-168">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="24274-169">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="24274-169">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="24274-170">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="24274-170">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="24274-171">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="24274-171">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
