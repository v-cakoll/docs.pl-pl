---
title: <transport> dla <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: 3b180006-1661-43bf-a699-96fd3da469af
ms.openlocfilehash: f9f784329081f6a18560991378a4527c731f4d31
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934710"
---
# <a name="transport-of-nethttpbinding"></a><span data-ttu-id="d961b-102">\<> \<transportu > protokołu HttpBinding</span><span class="sxs-lookup"><span data-stu-id="d961b-102">\<transport> of \<netHttpBinding></span></span>
<span data-ttu-id="d961b-103">Definiuje właściwości kontrolujące parametry uwierzytelniania dla transportu HTTP.</span><span class="sxs-lookup"><span data-stu-id="d961b-103">Defines properties that control authentication parameters for the HTTP transport.</span></span>  
  
<span data-ttu-id="d961b-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d961b-104">\<system.serviceModel></span></span>  
<span data-ttu-id="d961b-105">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="d961b-105">\<bindings></span></span>  
<span data-ttu-id="d961b-106">\<> protokołu HttpBinding</span><span class="sxs-lookup"><span data-stu-id="d961b-106">\<netHttpBinding></span></span>  
<span data-ttu-id="d961b-107">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="d961b-107">\<binding></span></span>  
<span data-ttu-id="d961b-108">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="d961b-108">\<security></span></span>  
<span data-ttu-id="d961b-109">\<transport></span><span class="sxs-lookup"><span data-stu-id="d961b-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d961b-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="d961b-110">Syntax</span></span>  
  
```xml  
<netHttpBinding>
  <binding>
    <security mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">
      <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"
                 proxyCredentialType="None|Basic|Digest|Ntlm|Windows"
                 realm="string">
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</netHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d961b-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d961b-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d961b-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d961b-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d961b-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d961b-113">Attributes</span></span>  
  
|<span data-ttu-id="d961b-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d961b-114">Attribute</span></span>|<span data-ttu-id="d961b-115">Opis</span><span class="sxs-lookup"><span data-stu-id="d961b-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d961b-116">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="d961b-116">clientCredentialType</span></span>|<span data-ttu-id="d961b-117">-Określa typ poświadczeń, które mają być używane podczas uwierzytelniania klienta przy użyciu uwierzytelniania HTTP.</span><span class="sxs-lookup"><span data-stu-id="d961b-117">-   Specifies the type of credential to be used when performing client authentication using HTTP authentication.</span></span>  <span data-ttu-id="d961b-118">Wartość domyślna to `None`.</span><span class="sxs-lookup"><span data-stu-id="d961b-118">The default is `None`.</span></span> <span data-ttu-id="d961b-119">Ten atrybut jest typu <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="d961b-119">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|<span data-ttu-id="d961b-120">proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="d961b-120">proxyCredentialType</span></span>|<span data-ttu-id="d961b-121">-Określa typ poświadczeń, które mają być używane podczas uwierzytelniania klienta w domenie przy użyciu serwera proxy za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="d961b-121">-   Specifies the type of credential to be used when performing client authentication from within a domain using a proxy over HTTP.</span></span> <span data-ttu-id="d961b-122">Ten atrybut jest stosowany tylko wtedy, `mode` gdy atrybut elementu nadrzędnego `security` to `Transport` or `TransportCredentialsOnly`.</span><span class="sxs-lookup"><span data-stu-id="d961b-122">This attribute is applicable only when the `mode` attribute of the parent `security` element is `Transport` or `TransportCredentialsOnly`.</span></span> <span data-ttu-id="d961b-123">Ten atrybut jest typu <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="d961b-123">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|<span data-ttu-id="d961b-124">obszarów</span><span class="sxs-lookup"><span data-stu-id="d961b-124">realm</span></span>|<span data-ttu-id="d961b-125">Ciąg określający obszar, który jest używany przez schemat uwierzytelniania HTTP na potrzeby uwierzytelniania szyfrowanego lub podstawowego.</span><span class="sxs-lookup"><span data-stu-id="d961b-125">A string that specifies the realm that is used by the HTTP authentication scheme for digest or basic authentication.</span></span> <span data-ttu-id="d961b-126">Wartość domyślna to pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="d961b-126">The default is an empty string.</span></span>|  
|<span data-ttu-id="d961b-127">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="d961b-127">policyEnforcement</span></span>|<span data-ttu-id="d961b-128">To Wyliczenie określa, <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> Kiedy należy wymusić.</span><span class="sxs-lookup"><span data-stu-id="d961b-128">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="d961b-129">1.  Nigdy — zasady nigdy nie są wymuszane (ochrona rozszerzona jest wyłączona).</span><span class="sxs-lookup"><span data-stu-id="d961b-129">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="d961b-130">2.  WhenSupported — zasady są wymuszane tylko wtedy, gdy klient obsługuje ochronę rozszerzoną.</span><span class="sxs-lookup"><span data-stu-id="d961b-130">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="d961b-131">3.  Zawsze — zasady są zawsze wymuszane.</span><span class="sxs-lookup"><span data-stu-id="d961b-131">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="d961b-132">Klienci, którzy nie obsługują rozszerzonej ochrony, nie będą uwierzytelniani.</span><span class="sxs-lookup"><span data-stu-id="d961b-132">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
|<span data-ttu-id="d961b-133">protectionScenario</span><span class="sxs-lookup"><span data-stu-id="d961b-133">protectionScenario</span></span>|<span data-ttu-id="d961b-134">To Wyliczenie określa scenariusz ochrony wymuszany przez zasady.</span><span class="sxs-lookup"><span data-stu-id="d961b-134">This enumeration specifies the protection scenario enforced by the policy.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="d961b-135">clientCredentialtype — atrybut</span><span class="sxs-lookup"><span data-stu-id="d961b-135">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="d961b-136">Wartość</span><span class="sxs-lookup"><span data-stu-id="d961b-136">Value</span></span>|<span data-ttu-id="d961b-137">Opis</span><span class="sxs-lookup"><span data-stu-id="d961b-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d961b-138">Brak</span><span class="sxs-lookup"><span data-stu-id="d961b-138">None</span></span>|<span data-ttu-id="d961b-139">Komunikaty nie są zabezpieczane podczas transferu.</span><span class="sxs-lookup"><span data-stu-id="d961b-139">Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="d961b-140">Podstawowy</span><span class="sxs-lookup"><span data-stu-id="d961b-140">Basic</span></span>|<span data-ttu-id="d961b-141">Określa podstawowe uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="d961b-141">Specifies basic authentication.</span></span>|  
|<span data-ttu-id="d961b-142">Szyfrowane</span><span class="sxs-lookup"><span data-stu-id="d961b-142">Digest</span></span>|<span data-ttu-id="d961b-143">Określa uwierzytelnianie szyfrowane.</span><span class="sxs-lookup"><span data-stu-id="d961b-143">Specifies digest authentication.</span></span>|  
|<span data-ttu-id="d961b-144">NTLM</span><span class="sxs-lookup"><span data-stu-id="d961b-144">Ntlm</span></span>|<span data-ttu-id="d961b-145">Określa uwierzytelnianie NTLM, jeśli jest to możliwe, a uwierzytelnianie systemu Windows kończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="d961b-145">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="d961b-146">Windows</span><span class="sxs-lookup"><span data-stu-id="d961b-146">Windows</span></span>|<span data-ttu-id="d961b-147">Określa zintegrowane uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="d961b-147">Specifies Windows integrated authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="d961b-148">proxyCredentialType — atrybut</span><span class="sxs-lookup"><span data-stu-id="d961b-148">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="d961b-149">Wartość</span><span class="sxs-lookup"><span data-stu-id="d961b-149">Value</span></span>|<span data-ttu-id="d961b-150">Opis</span><span class="sxs-lookup"><span data-stu-id="d961b-150">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d961b-151">Brak</span><span class="sxs-lookup"><span data-stu-id="d961b-151">None</span></span>|<span data-ttu-id="d961b-152">-Komunikaty nie są zabezpieczane podczas transferu.</span><span class="sxs-lookup"><span data-stu-id="d961b-152">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="d961b-153">Podstawowy</span><span class="sxs-lookup"><span data-stu-id="d961b-153">Basic</span></span>|<span data-ttu-id="d961b-154">Określa uwierzytelnianie podstawowe zgodnie z definicją w dokumencie RFC 2617 — uwierzytelnianie HTTP: Uwierzytelnianie podstawowe i szyfrowane.</span><span class="sxs-lookup"><span data-stu-id="d961b-154">Specifies basic authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="d961b-155">Szyfrowane</span><span class="sxs-lookup"><span data-stu-id="d961b-155">Digest</span></span>|<span data-ttu-id="d961b-156">Określa uwierzytelnianie szyfrowane zgodnie z definicją w dokumencie RFC 2617 — uwierzytelnianie HTTP: Uwierzytelnianie podstawowe i szyfrowane.</span><span class="sxs-lookup"><span data-stu-id="d961b-156">Specifies digest authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="d961b-157">NTLM</span><span class="sxs-lookup"><span data-stu-id="d961b-157">Ntlm</span></span>|<span data-ttu-id="d961b-158">Określa uwierzytelnianie NTLM, jeśli jest to możliwe, a uwierzytelnianie systemu Windows kończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="d961b-158">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="d961b-159">Windows</span><span class="sxs-lookup"><span data-stu-id="d961b-159">Windows</span></span>|<span data-ttu-id="d961b-160">Określa zintegrowane uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="d961b-160">Specifies Windows integrated authentication.</span></span>|  
|<span data-ttu-id="d961b-161">Certyfikatu</span><span class="sxs-lookup"><span data-stu-id="d961b-161">Certificate</span></span>|<span data-ttu-id="d961b-162">Wykonuje uwierzytelnianie klienta przy użyciu certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="d961b-162">Performs client authentication using a certificate.</span></span> <span data-ttu-id="d961b-163">Ta opcja działa tylko wtedy, `Mode` gdy atrybut elementu nadrzędnego `security` jest ustawiony na transport i nie będzie działać, jeśli zostanie ustawiony na wartość TransportCredentialOnly.</span><span class="sxs-lookup"><span data-stu-id="d961b-163">This option works only if the `Mode` attribute of the parent `security` element is set to Transport, and will not work if it is set to TransportCredentialOnly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d961b-164">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d961b-164">Child Elements</span></span>  
 <span data-ttu-id="d961b-165">Brak</span><span class="sxs-lookup"><span data-stu-id="d961b-165">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d961b-166">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d961b-166">Parent Elements</span></span>  
  
|<span data-ttu-id="d961b-167">Element</span><span class="sxs-lookup"><span data-stu-id="d961b-167">Element</span></span>|<span data-ttu-id="d961b-168">Opis</span><span class="sxs-lookup"><span data-stu-id="d961b-168">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d961b-169">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="d961b-169">\<security></span></span>](security-of-nethttpbinding.md)|<span data-ttu-id="d961b-170">Definiuje możliwości zabezpieczeń dla [ \<protokołu HttpBinding >](nethttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="d961b-170">Defines the security capabilities for the [\<netHttpBinding>](nethttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d961b-171">Przykład</span><span class="sxs-lookup"><span data-stu-id="d961b-171">Example</span></span>  
 <span data-ttu-id="d961b-172">Poniższy przykład ilustruje użycie zabezpieczeń transportu SSL z powiązaniem podstawowym.</span><span class="sxs-lookup"><span data-stu-id="d961b-172">The following example demonstrates the use of SSL transport security with the basic binding.</span></span> <span data-ttu-id="d961b-173">Domyślnie podstawowe powiązanie obsługuje komunikację HTTP.</span><span class="sxs-lookup"><span data-stu-id="d961b-173">By default, the basic binding supports HTTP communication.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="netHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <netHttpBinding>
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
    </netHttpBinding>
  </bindings>
</system.serviceModel>
```  
  
## <a name="see-also"></a><span data-ttu-id="d961b-174">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d961b-174">See also</span></span>

- <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- <xref:System.ServiceModel.HttpTransportSecurity>
- [<span data-ttu-id="d961b-175">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="d961b-175">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="d961b-176">Powiązania</span><span class="sxs-lookup"><span data-stu-id="d961b-176">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="d961b-177">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="d961b-177">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="d961b-178">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="d961b-178">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="d961b-179">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="d961b-179">\<binding></span></span>](../../../misc/binding.md)
