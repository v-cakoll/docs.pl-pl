---
title: <transport> dla <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 4c5ba293-3d7e-47a6-b84e-e9022857b7e5
ms.openlocfilehash: 2cf69c48a51ce2c687ebcfe9f87f7c22f5f86084
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399384"
---
# <a name="transport-of-basichttpbinding"></a><span data-ttu-id="b6336-102">\<Transport > \<BasicHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="b6336-102">\<transport> of \<basicHttpBinding></span></span>
<span data-ttu-id="b6336-103">Definiuje właściwości kontrolujące parametry uwierzytelniania dla transportu HTTP.</span><span class="sxs-lookup"><span data-stu-id="b6336-103">Defines properties that control authentication parameters for the HTTP transport.</span></span>  
  
<span data-ttu-id="b6336-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b6336-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b6336-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="b6336-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="b6336-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> powiązań**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="b6336-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="b6336-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<basicHttpBinding >** ](basichttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="b6336-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<basicHttpBinding>**](basichttpbinding.md)</span></span>\
<span data-ttu-id="b6336-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> powiązania**</span><span class="sxs-lookup"><span data-stu-id="b6336-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="b6336-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zabezpieczeń**](security-of-basichttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="b6336-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-basichttpbinding.md)</span></span>\
<span data-ttu-id="b6336-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> transportu**</span><span class="sxs-lookup"><span data-stu-id="b6336-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6336-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="b6336-111">Syntax</span></span>  
  
```xml  
<basicHttpBinding>
  <binding>
    <security mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">
      <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"
                 proxyCredentialType="None|Basic|Digest|Ntlm|Windows"
                 realm="String">
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</basicHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b6336-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b6336-112">Attributes and Elements</span></span>  
 <span data-ttu-id="b6336-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b6336-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b6336-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b6336-114">Attributes</span></span>  
  
|<span data-ttu-id="b6336-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b6336-115">Attribute</span></span>|<span data-ttu-id="b6336-116">Opis</span><span class="sxs-lookup"><span data-stu-id="b6336-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b6336-117">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="b6336-117">clientCredentialType</span></span>|<span data-ttu-id="b6336-118">-Określa typ poświadczeń, które mają być używane podczas uwierzytelniania klienta przy użyciu uwierzytelniania HTTP.</span><span class="sxs-lookup"><span data-stu-id="b6336-118">-   Specifies the type of credential to be used when performing client authentication using HTTP authentication.</span></span>  <span data-ttu-id="b6336-119">Wartość domyślna to `None`.</span><span class="sxs-lookup"><span data-stu-id="b6336-119">The default is `None`.</span></span> <span data-ttu-id="b6336-120">Ten atrybut jest typu <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="b6336-120">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|<span data-ttu-id="b6336-121">proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="b6336-121">proxyCredentialType</span></span>|<span data-ttu-id="b6336-122">-Określa typ poświadczeń, które mają być używane podczas uwierzytelniania klienta w domenie przy użyciu serwera proxy za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="b6336-122">-   Specifies the type of credential to be used when performing client authentication from within a domain using a proxy over HTTP.</span></span> <span data-ttu-id="b6336-123">Ten atrybut jest stosowany tylko wtedy, `mode` gdy atrybut elementu nadrzędnego `security` to `Transport` or `TransportCredentialsOnly`.</span><span class="sxs-lookup"><span data-stu-id="b6336-123">This attribute is applicable only when the `mode` attribute of the parent `security` element is `Transport` or `TransportCredentialsOnly`.</span></span> <span data-ttu-id="b6336-124">Ten atrybut jest typu <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="b6336-124">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|<span data-ttu-id="b6336-125">obszarów</span><span class="sxs-lookup"><span data-stu-id="b6336-125">realm</span></span>|<span data-ttu-id="b6336-126">Ciąg określający obszar, który jest używany przez schemat uwierzytelniania HTTP na potrzeby uwierzytelniania szyfrowanego lub podstawowego.</span><span class="sxs-lookup"><span data-stu-id="b6336-126">A string that specifies the realm that is used by the HTTP authentication scheme for digest or basic authentication.</span></span> <span data-ttu-id="b6336-127">Wartość domyślna to pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="b6336-127">The default is an empty string.</span></span>|  
|<span data-ttu-id="b6336-128">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="b6336-128">policyEnforcement</span></span>|<span data-ttu-id="b6336-129">To Wyliczenie określa, <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> Kiedy należy wymusić.</span><span class="sxs-lookup"><span data-stu-id="b6336-129">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="b6336-130">1.  Nigdy — zasady nigdy nie są wymuszane (ochrona rozszerzona jest wyłączona).</span><span class="sxs-lookup"><span data-stu-id="b6336-130">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="b6336-131">2.  WhenSupported — zasady są wymuszane tylko wtedy, gdy klient obsługuje ochronę rozszerzoną.</span><span class="sxs-lookup"><span data-stu-id="b6336-131">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="b6336-132">3.  Zawsze — zasady są zawsze wymuszane.</span><span class="sxs-lookup"><span data-stu-id="b6336-132">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="b6336-133">Klienci, którzy nie obsługują rozszerzonej ochrony, nie będą uwierzytelniani.</span><span class="sxs-lookup"><span data-stu-id="b6336-133">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
|<span data-ttu-id="b6336-134">protectionScenario</span><span class="sxs-lookup"><span data-stu-id="b6336-134">protectionScenario</span></span>|<span data-ttu-id="b6336-135">To Wyliczenie określa scenariusz ochrony wymuszany przez zasady.</span><span class="sxs-lookup"><span data-stu-id="b6336-135">This enumeration specifies the protection scenario enforced by the policy.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="b6336-136">clientCredentialtype — atrybut</span><span class="sxs-lookup"><span data-stu-id="b6336-136">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="b6336-137">Wartość</span><span class="sxs-lookup"><span data-stu-id="b6336-137">Value</span></span>|<span data-ttu-id="b6336-138">Opis</span><span class="sxs-lookup"><span data-stu-id="b6336-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b6336-139">Brak</span><span class="sxs-lookup"><span data-stu-id="b6336-139">None</span></span>|<span data-ttu-id="b6336-140">Komunikaty nie są zabezpieczane podczas transferu.</span><span class="sxs-lookup"><span data-stu-id="b6336-140">Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="b6336-141">Podstawowy</span><span class="sxs-lookup"><span data-stu-id="b6336-141">Basic</span></span>|<span data-ttu-id="b6336-142">Określa podstawowe uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="b6336-142">Specifies basic authentication.</span></span>|  
|<span data-ttu-id="b6336-143">Szyfrowane</span><span class="sxs-lookup"><span data-stu-id="b6336-143">Digest</span></span>|<span data-ttu-id="b6336-144">Określa uwierzytelnianie szyfrowane.</span><span class="sxs-lookup"><span data-stu-id="b6336-144">Specifies digest authentication.</span></span>|  
|<span data-ttu-id="b6336-145">NTLM</span><span class="sxs-lookup"><span data-stu-id="b6336-145">Ntlm</span></span>|<span data-ttu-id="b6336-146">Określa uwierzytelnianie NTLM, jeśli jest to możliwe, a uwierzytelnianie systemu Windows kończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="b6336-146">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="b6336-147">Windows</span><span class="sxs-lookup"><span data-stu-id="b6336-147">Windows</span></span>|<span data-ttu-id="b6336-148">Określa zintegrowane uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="b6336-148">Specifies Windows integrated authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="b6336-149">proxyCredentialType — atrybut</span><span class="sxs-lookup"><span data-stu-id="b6336-149">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="b6336-150">Wartość</span><span class="sxs-lookup"><span data-stu-id="b6336-150">Value</span></span>|<span data-ttu-id="b6336-151">Opis</span><span class="sxs-lookup"><span data-stu-id="b6336-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b6336-152">Brak</span><span class="sxs-lookup"><span data-stu-id="b6336-152">None</span></span>|<span data-ttu-id="b6336-153">-Komunikaty nie są zabezpieczane podczas transferu.</span><span class="sxs-lookup"><span data-stu-id="b6336-153">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="b6336-154">Podstawowy</span><span class="sxs-lookup"><span data-stu-id="b6336-154">Basic</span></span>|<span data-ttu-id="b6336-155">Określa uwierzytelnianie podstawowe zgodnie z definicją w dokumencie RFC 2617 — uwierzytelnianie HTTP: Uwierzytelnianie podstawowe i szyfrowane.</span><span class="sxs-lookup"><span data-stu-id="b6336-155">Specifies basic authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="b6336-156">Szyfrowane</span><span class="sxs-lookup"><span data-stu-id="b6336-156">Digest</span></span>|<span data-ttu-id="b6336-157">Określa uwierzytelnianie szyfrowane zgodnie z definicją w dokumencie RFC 2617 — uwierzytelnianie HTTP: Uwierzytelnianie podstawowe i szyfrowane.</span><span class="sxs-lookup"><span data-stu-id="b6336-157">Specifies digest authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="b6336-158">NTLM</span><span class="sxs-lookup"><span data-stu-id="b6336-158">Ntlm</span></span>|<span data-ttu-id="b6336-159">Określa uwierzytelnianie NTLM, jeśli jest to możliwe, a uwierzytelnianie systemu Windows kończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="b6336-159">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="b6336-160">Windows</span><span class="sxs-lookup"><span data-stu-id="b6336-160">Windows</span></span>|<span data-ttu-id="b6336-161">Określa zintegrowane uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="b6336-161">Specifies Windows integrated authentication.</span></span>|  
|<span data-ttu-id="b6336-162">Certyfikatu</span><span class="sxs-lookup"><span data-stu-id="b6336-162">Certificate</span></span>|<span data-ttu-id="b6336-163">Wykonuje uwierzytelnianie klienta przy użyciu certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="b6336-163">Performs client authentication using a certificate.</span></span> <span data-ttu-id="b6336-164">Ta opcja działa tylko wtedy, `Mode` gdy atrybut elementu nadrzędnego `security` jest ustawiony na transport i nie będzie działać, jeśli zostanie ustawiony na wartość TransportCredentialOnly.</span><span class="sxs-lookup"><span data-stu-id="b6336-164">This option works only if the `Mode` attribute of the parent `security` element is set to Transport, and will not work if it is set to TransportCredentialOnly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b6336-165">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b6336-165">Child Elements</span></span>  
 <span data-ttu-id="b6336-166">Brak</span><span class="sxs-lookup"><span data-stu-id="b6336-166">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b6336-167">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b6336-167">Parent Elements</span></span>  
  
|<span data-ttu-id="b6336-168">Element</span><span class="sxs-lookup"><span data-stu-id="b6336-168">Element</span></span>|<span data-ttu-id="b6336-169">Opis</span><span class="sxs-lookup"><span data-stu-id="b6336-169">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b6336-170">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="b6336-170">\<security></span></span>](security-of-basichttpbinding.md)|<span data-ttu-id="b6336-171">Definiuje możliwości zabezpieczeń dla [ \<> BasicHttpBinding](basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="b6336-171">Defines the security capabilities for the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b6336-172">Przykład</span><span class="sxs-lookup"><span data-stu-id="b6336-172">Example</span></span>  
 <span data-ttu-id="b6336-173">Poniższy przykład ilustruje użycie zabezpieczeń transportu SSL z powiązaniem podstawowym.</span><span class="sxs-lookup"><span data-stu-id="b6336-173">The following example demonstrates the use of SSL transport security with the basic binding.</span></span> <span data-ttu-id="b6336-174">Domyślnie podstawowe powiązanie obsługuje komunikację HTTP.</span><span class="sxs-lookup"><span data-stu-id="b6336-174">By default, the basic binding supports HTTP communication.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="basicHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <basicHttpBinding>
      <!-- Configure basicHttpBinding with Transport security -->
      <!-- mode and clientCredentialType set to None. -->
      <binding name="Binding1">
        <security mode="Transport">
          <transport clientCredentialType="None"
                     proxyCredentialType="None">
            <extendedProtectionPolicy policyEnforcement="WhenSupported"
                                      protectionScenario="TransportSelected">
              <customServiceNames>
              </customServiceNames>
            </extendedProtectionPolicy>
          </transport>
        </security>
      </binding>
    </basicHttpBinding>
  </bindings>
</system.serviceModel>
```  
  
## <a name="see-also"></a><span data-ttu-id="b6336-175">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b6336-175">See also</span></span>

- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.BasicHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- <xref:System.ServiceModel.HttpTransportSecurity>
- [<span data-ttu-id="b6336-176">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="b6336-176">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="b6336-177">Powiązania</span><span class="sxs-lookup"><span data-stu-id="b6336-177">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="b6336-178">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="b6336-178">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="b6336-179">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="b6336-179">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="b6336-180">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="b6336-180">\<binding></span></span>](../../../misc/binding.md)
