---
title: '&lt;transport&gt; w &lt;netHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 3b180006-1661-43bf-a699-96fd3da469af
ms.openlocfilehash: 092072df2b88c59c7744a694175ce5ddf39cf79b
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48580537"
---
# <a name="lttransportgt-of-ltnethttpbindinggt"></a><span data-ttu-id="3bc84-102">&lt;transport&gt; w &lt;netHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="3bc84-102">&lt;transport&gt; of &lt;netHttpBinding&gt;</span></span>
<span data-ttu-id="3bc84-103">Definiuje właściwości sterujące parametrami uwierzytelniania dla protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="3bc84-103">Defines properties that control authentication parameters for the HTTP transport.</span></span>  
  
<span data-ttu-id="3bc84-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3bc84-104">\<system.serviceModel></span></span>  
<span data-ttu-id="3bc84-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="3bc84-105">\<bindings></span></span>  
<span data-ttu-id="3bc84-106">\<netHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="3bc84-106">\<netHttpBinding></span></span>  
<span data-ttu-id="3bc84-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="3bc84-107">\<binding></span></span>  
<span data-ttu-id="3bc84-108">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="3bc84-108">\<security></span></span>  
<span data-ttu-id="3bc84-109">\<transport></span><span class="sxs-lookup"><span data-stu-id="3bc84-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bc84-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="3bc84-110">Syntax</span></span>  
  
```xml
<netHttpBinding>  
  <binding>  
    <security mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">  
      <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"  
                 proxyCredentialType="None|Basic|Digest|Ntlm|Windows" realm="string">  
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"  
                                  protectionScenario="TransportSelected|TrustedProxy">  
          <customServiceNames></customServiceNames>  
        </extendedProtectionPolicy>  
      </transport>  
    </security>  
  </binding>  
</netHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3bc84-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3bc84-111">Attributes and Elements</span></span>  
 <span data-ttu-id="3bc84-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3bc84-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3bc84-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3bc84-113">Attributes</span></span>  
  
|<span data-ttu-id="3bc84-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="3bc84-114">Attribute</span></span>|<span data-ttu-id="3bc84-115">Opis</span><span class="sxs-lookup"><span data-stu-id="3bc84-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3bc84-116">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="3bc84-116">clientCredentialType</span></span>|<span data-ttu-id="3bc84-117">-Określa typ poświadczenia do użycia podczas przeprowadzania uwierzytelniania klienta przy użyciu uwierzytelniania HTTP.</span><span class="sxs-lookup"><span data-stu-id="3bc84-117">-   Specifies the type of credential to be used when performing client authentication using HTTP authentication.</span></span>  <span data-ttu-id="3bc84-118">Wartość domyślna to `None`.</span><span class="sxs-lookup"><span data-stu-id="3bc84-118">The default is `None`.</span></span> <span data-ttu-id="3bc84-119">Ten atrybut jest typu <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="3bc84-119">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|<span data-ttu-id="3bc84-120">proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="3bc84-120">proxyCredentialType</span></span>|<span data-ttu-id="3bc84-121">-Określa typ poświadczenia do użycia podczas przeprowadzania uwierzytelniania klienta z w obrębie domeny przy użyciu serwera proxy za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="3bc84-121">-   Specifies the type of credential to be used when performing client authentication from within a domain using a proxy over HTTP.</span></span> <span data-ttu-id="3bc84-122">Ten atrybut jest stosowane tylko wtedy, gdy `mode` atrybutu elementu nadrzędnego `security` element jest `Transport` lub `TransportCredentialsOnly`.</span><span class="sxs-lookup"><span data-stu-id="3bc84-122">This attribute is applicable only when the `mode` attribute of the parent `security` element is `Transport` or `TransportCredentialsOnly`.</span></span> <span data-ttu-id="3bc84-123">Ten atrybut jest typu <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="3bc84-123">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|<span data-ttu-id="3bc84-124">obszar</span><span class="sxs-lookup"><span data-stu-id="3bc84-124">realm</span></span>|<span data-ttu-id="3bc84-125">Ciąg, który określa obszar, który jest używany przez schemat uwierzytelniania HTTP digest lub uwierzytelnianie podstawowe.</span><span class="sxs-lookup"><span data-stu-id="3bc84-125">A string that specifies the realm that is used by the HTTP authentication scheme for digest or basic authentication.</span></span> <span data-ttu-id="3bc84-126">Wartość domyślna to ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="3bc84-126">The default is an empty string.</span></span>|  
|<span data-ttu-id="3bc84-127">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="3bc84-127">policyEnforcement</span></span>|<span data-ttu-id="3bc84-128">To wyliczenie Określa, kiedy <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> powinny być wymuszane.</span><span class="sxs-lookup"><span data-stu-id="3bc84-128">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="3bc84-129">1.  Nigdy nie — zasady nigdy nie są wymuszane (ochrony rozszerzonej jest wyłączone).</span><span class="sxs-lookup"><span data-stu-id="3bc84-129">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="3bc84-130">2.  WhenSupported — zasady są wymuszane tylko wtedy, gdy klient obsługuje ochrony rozszerzonej.</span><span class="sxs-lookup"><span data-stu-id="3bc84-130">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="3bc84-131">3.  Zawsze — zasady zawsze są wymuszane.</span><span class="sxs-lookup"><span data-stu-id="3bc84-131">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="3bc84-132">Klienci, którzy nie obsługują ochrony rozszerzonej zakończy się niepowodzeniem do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="3bc84-132">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
|<span data-ttu-id="3bc84-133">protectionScenario</span><span class="sxs-lookup"><span data-stu-id="3bc84-133">protectionScenario</span></span>|<span data-ttu-id="3bc84-134">To wyliczenie Określa scenariusz ochrony wymuszane przez zasady.</span><span class="sxs-lookup"><span data-stu-id="3bc84-134">This enumeration specifies the protection scenario enforced by the policy.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="3bc84-135">właściwości ClientCredentialType o wartości atrybutu</span><span class="sxs-lookup"><span data-stu-id="3bc84-135">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="3bc84-136">Wartość</span><span class="sxs-lookup"><span data-stu-id="3bc84-136">Value</span></span>|<span data-ttu-id="3bc84-137">Opis</span><span class="sxs-lookup"><span data-stu-id="3bc84-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3bc84-138">Brak</span><span class="sxs-lookup"><span data-stu-id="3bc84-138">None</span></span>|<span data-ttu-id="3bc84-139">Komunikaty nie są zabezpieczane podczas przesyłania.</span><span class="sxs-lookup"><span data-stu-id="3bc84-139">Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="3bc84-140">Podstawowy</span><span class="sxs-lookup"><span data-stu-id="3bc84-140">Basic</span></span>|<span data-ttu-id="3bc84-141">Określa uwierzytelnianie podstawowe.</span><span class="sxs-lookup"><span data-stu-id="3bc84-141">Specifies basic authentication.</span></span>|  
|<span data-ttu-id="3bc84-142">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="3bc84-142">Digest</span></span>|<span data-ttu-id="3bc84-143">Określa uwierzytelnianie szyfrowane.</span><span class="sxs-lookup"><span data-stu-id="3bc84-143">Specifies digest authentication.</span></span>|  
|<span data-ttu-id="3bc84-144">Uwierzytelnianie NTLM</span><span class="sxs-lookup"><span data-stu-id="3bc84-144">Ntlm</span></span>|<span data-ttu-id="3bc84-145">Określa uwierzytelniania NTLM, jeśli jest to możliwe, a w przypadku niepowodzenia uwierzytelniania Windows.</span><span class="sxs-lookup"><span data-stu-id="3bc84-145">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="3bc84-146">Windows</span><span class="sxs-lookup"><span data-stu-id="3bc84-146">Windows</span></span>|<span data-ttu-id="3bc84-147">Określa, czy zintegrowane uwierzytelnianie Windows</span><span class="sxs-lookup"><span data-stu-id="3bc84-147">Specifies Windows integrated authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="3bc84-148">proxyCredentialType atrybutu</span><span class="sxs-lookup"><span data-stu-id="3bc84-148">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="3bc84-149">Wartość</span><span class="sxs-lookup"><span data-stu-id="3bc84-149">Value</span></span>|<span data-ttu-id="3bc84-150">Opis</span><span class="sxs-lookup"><span data-stu-id="3bc84-150">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3bc84-151">Brak</span><span class="sxs-lookup"><span data-stu-id="3bc84-151">None</span></span>|<span data-ttu-id="3bc84-152">— Liczba komunikatów nie są zabezpieczane podczas przesyłania.</span><span class="sxs-lookup"><span data-stu-id="3bc84-152">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="3bc84-153">Podstawowy</span><span class="sxs-lookup"><span data-stu-id="3bc84-153">Basic</span></span>|<span data-ttu-id="3bc84-154">Określa uwierzytelnianie podstawowe, zgodnie z definicją w dokumencie RFC 2617 — uwierzytelnianie HTTP: podstawowe i uwierzytelnianie szyfrowane.</span><span class="sxs-lookup"><span data-stu-id="3bc84-154">Specifies basic authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="3bc84-155">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="3bc84-155">Digest</span></span>|<span data-ttu-id="3bc84-156">Określa uwierzytelnianie szyfrowane zgodnie z definicją w dokumencie RFC 2617 — uwierzytelnianie HTTP: podstawowe i uwierzytelnianie szyfrowane.</span><span class="sxs-lookup"><span data-stu-id="3bc84-156">Specifies digest authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="3bc84-157">Uwierzytelnianie NTLM</span><span class="sxs-lookup"><span data-stu-id="3bc84-157">Ntlm</span></span>|<span data-ttu-id="3bc84-158">Określa uwierzytelniania NTLM, jeśli jest to możliwe, a w przypadku niepowodzenia uwierzytelniania Windows.</span><span class="sxs-lookup"><span data-stu-id="3bc84-158">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="3bc84-159">Windows</span><span class="sxs-lookup"><span data-stu-id="3bc84-159">Windows</span></span>|<span data-ttu-id="3bc84-160">Określa, czy zintegrowane uwierzytelnianie Windows</span><span class="sxs-lookup"><span data-stu-id="3bc84-160">Specifies Windows integrated authentication.</span></span>|  
|<span data-ttu-id="3bc84-161">Certyfikat</span><span class="sxs-lookup"><span data-stu-id="3bc84-161">Certificate</span></span>|<span data-ttu-id="3bc84-162">Wykonuje uwierzytelnianie klienta przy użyciu certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="3bc84-162">Performs client authentication using a certificate.</span></span> <span data-ttu-id="3bc84-163">Ta opcja działa tylko wtedy, gdy `Mode` atrybutu elementu nadrzędnego `security` elementu jest ustawiona na Transport i nie będzie działać, jeśli jest ustawiona wartość TransportCredentialOnly.</span><span class="sxs-lookup"><span data-stu-id="3bc84-163">This option works only if the `Mode` attribute of the parent `security` element is set to Transport, and will not work if it is set to TransportCredentialOnly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3bc84-164">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3bc84-164">Child Elements</span></span>  
 <span data-ttu-id="3bc84-165">Brak</span><span class="sxs-lookup"><span data-stu-id="3bc84-165">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3bc84-166">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3bc84-166">Parent Elements</span></span>  
  
|<span data-ttu-id="3bc84-167">Element</span><span class="sxs-lookup"><span data-stu-id="3bc84-167">Element</span></span>|<span data-ttu-id="3bc84-168">Opis</span><span class="sxs-lookup"><span data-stu-id="3bc84-168">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3bc84-169">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="3bc84-169">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nethttpbinding.md)|<span data-ttu-id="3bc84-170">Definiuje funkcje bezpieczeństwa umożliwiające [ \<netHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nethttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="3bc84-170">Defines the security capabilities for the [\<netHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/nethttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3bc84-171">Przykład</span><span class="sxs-lookup"><span data-stu-id="3bc84-171">Example</span></span>  
 <span data-ttu-id="3bc84-172">Poniższy przykład pokazuje użycie protokołu SSL z zabezpieczeń transportu dla wiązania podstawowe.</span><span class="sxs-lookup"><span data-stu-id="3bc84-172">The following example demonstrates the use of SSL transport security with the basic binding.</span></span> <span data-ttu-id="3bc84-173">Domyślnie podstawowe powiązanie obsługuje komunikację HTTP.</span><span class="sxs-lookup"><span data-stu-id="3bc84-173">By default, the basic binding supports HTTP communication.</span></span>  
  
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
      <!-- Configure basicHttpBinding with Transport security -- >  
      <!-- mode and clientCredentialType set to None.-->  
      <binding name="Binding1">  
        <security mode="Transport">  
          <transport clientCredentialType="None"  
                     proxyCredentialType="None">  
            <extendedProtectionPolicy policyEnforcement="WhenSupported"  
                                      protectionScenario="TransportSelected">  
              <customServiceNames></customServiceNames>  
            </extendedProtectionPolicy>
          </transport> 
        </security>  
      </binding>  
    </netHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3bc84-174">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3bc84-174">See Also</span></span>  
 <span data-ttu-id="3bc84-175"><xref:System.ServiceModel.BasicHttpSecurityMode.Transport><xref:System.ServiceModel.Configuration.HttpTransportSecurityElement></span><span class="sxs-lookup"><span data-stu-id="3bc84-175"><xref:System.ServiceModel.BasicHttpSecurityMode.Transport> <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement></span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 [<span data-ttu-id="3bc84-176">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="3bc84-176">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="3bc84-177">Powiązania</span><span class="sxs-lookup"><span data-stu-id="3bc84-177">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="3bc84-178">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="3bc84-178">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="3bc84-179">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="3bc84-179">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="3bc84-180">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="3bc84-180">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
