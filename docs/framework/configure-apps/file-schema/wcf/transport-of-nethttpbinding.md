---
title: '&lt;transport&gt; w &lt;netHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 3b180006-1661-43bf-a699-96fd3da469af
ms.openlocfilehash: 3110a93d224ee2be078727df65b92e9987445c43
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54151296"
---
# <a name="lttransportgt-of-ltnethttpbindinggt"></a><span data-ttu-id="c9eae-102">&lt;transport&gt; w &lt;netHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="c9eae-102">&lt;transport&gt; of &lt;netHttpBinding&gt;</span></span>
<span data-ttu-id="c9eae-103">Definiuje właściwości sterujące parametrami uwierzytelniania dla protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="c9eae-103">Defines properties that control authentication parameters for the HTTP transport.</span></span>  
  
<span data-ttu-id="c9eae-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="c9eae-104">\<system.serviceModel></span></span>  
<span data-ttu-id="c9eae-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="c9eae-105">\<bindings></span></span>  
<span data-ttu-id="c9eae-106">\<netHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="c9eae-106">\<netHttpBinding></span></span>  
<span data-ttu-id="c9eae-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="c9eae-107">\<binding></span></span>  
<span data-ttu-id="c9eae-108">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="c9eae-108">\<security></span></span>  
<span data-ttu-id="c9eae-109">\<transport></span><span class="sxs-lookup"><span data-stu-id="c9eae-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9eae-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="c9eae-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c9eae-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c9eae-111">Attributes and Elements</span></span>  
 <span data-ttu-id="c9eae-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c9eae-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c9eae-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c9eae-113">Attributes</span></span>  
  
|<span data-ttu-id="c9eae-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c9eae-114">Attribute</span></span>|<span data-ttu-id="c9eae-115">Opis</span><span class="sxs-lookup"><span data-stu-id="c9eae-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c9eae-116">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="c9eae-116">clientCredentialType</span></span>|<span data-ttu-id="c9eae-117">-Określa typ poświadczenia do użycia podczas przeprowadzania uwierzytelniania klienta przy użyciu uwierzytelniania HTTP.</span><span class="sxs-lookup"><span data-stu-id="c9eae-117">-   Specifies the type of credential to be used when performing client authentication using HTTP authentication.</span></span>  <span data-ttu-id="c9eae-118">Wartość domyślna to `None`.</span><span class="sxs-lookup"><span data-stu-id="c9eae-118">The default is `None`.</span></span> <span data-ttu-id="c9eae-119">Ten atrybut jest typu <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="c9eae-119">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|<span data-ttu-id="c9eae-120">proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="c9eae-120">proxyCredentialType</span></span>|<span data-ttu-id="c9eae-121">-Określa typ poświadczenia do użycia podczas przeprowadzania uwierzytelniania klienta z w obrębie domeny przy użyciu serwera proxy za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="c9eae-121">-   Specifies the type of credential to be used when performing client authentication from within a domain using a proxy over HTTP.</span></span> <span data-ttu-id="c9eae-122">Ten atrybut jest stosowane tylko wtedy, gdy `mode` atrybutu elementu nadrzędnego `security` element jest `Transport` lub `TransportCredentialsOnly`.</span><span class="sxs-lookup"><span data-stu-id="c9eae-122">This attribute is applicable only when the `mode` attribute of the parent `security` element is `Transport` or `TransportCredentialsOnly`.</span></span> <span data-ttu-id="c9eae-123">Ten atrybut jest typu <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="c9eae-123">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|<span data-ttu-id="c9eae-124">obszar</span><span class="sxs-lookup"><span data-stu-id="c9eae-124">realm</span></span>|<span data-ttu-id="c9eae-125">Ciąg, który określa obszar, który jest używany przez schemat uwierzytelniania HTTP digest lub uwierzytelnianie podstawowe.</span><span class="sxs-lookup"><span data-stu-id="c9eae-125">A string that specifies the realm that is used by the HTTP authentication scheme for digest or basic authentication.</span></span> <span data-ttu-id="c9eae-126">Wartość domyślna to ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="c9eae-126">The default is an empty string.</span></span>|  
|<span data-ttu-id="c9eae-127">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="c9eae-127">policyEnforcement</span></span>|<span data-ttu-id="c9eae-128">To wyliczenie Określa, kiedy <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> powinny być wymuszane.</span><span class="sxs-lookup"><span data-stu-id="c9eae-128">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="c9eae-129">1.  Nigdy nie — zasady nigdy nie są wymuszane (ochrony rozszerzonej jest wyłączone).</span><span class="sxs-lookup"><span data-stu-id="c9eae-129">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="c9eae-130">2.  WhenSupported — zasady są wymuszane tylko wtedy, gdy klient obsługuje ochrony rozszerzonej.</span><span class="sxs-lookup"><span data-stu-id="c9eae-130">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="c9eae-131">3.  Zawsze — zasady zawsze są wymuszane.</span><span class="sxs-lookup"><span data-stu-id="c9eae-131">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="c9eae-132">Klienci, którzy nie obsługują ochrony rozszerzonej zakończy się niepowodzeniem do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="c9eae-132">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
|<span data-ttu-id="c9eae-133">protectionScenario</span><span class="sxs-lookup"><span data-stu-id="c9eae-133">protectionScenario</span></span>|<span data-ttu-id="c9eae-134">To wyliczenie Określa scenariusz ochrony wymuszane przez zasady.</span><span class="sxs-lookup"><span data-stu-id="c9eae-134">This enumeration specifies the protection scenario enforced by the policy.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="c9eae-135">właściwości ClientCredentialType o wartości atrybutu</span><span class="sxs-lookup"><span data-stu-id="c9eae-135">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="c9eae-136">Wartość</span><span class="sxs-lookup"><span data-stu-id="c9eae-136">Value</span></span>|<span data-ttu-id="c9eae-137">Opis</span><span class="sxs-lookup"><span data-stu-id="c9eae-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c9eae-138">Brak</span><span class="sxs-lookup"><span data-stu-id="c9eae-138">None</span></span>|<span data-ttu-id="c9eae-139">Komunikaty nie są zabezpieczane podczas przesyłania.</span><span class="sxs-lookup"><span data-stu-id="c9eae-139">Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="c9eae-140">Podstawowy</span><span class="sxs-lookup"><span data-stu-id="c9eae-140">Basic</span></span>|<span data-ttu-id="c9eae-141">Określa uwierzytelnianie podstawowe.</span><span class="sxs-lookup"><span data-stu-id="c9eae-141">Specifies basic authentication.</span></span>|  
|<span data-ttu-id="c9eae-142">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="c9eae-142">Digest</span></span>|<span data-ttu-id="c9eae-143">Określa uwierzytelnianie szyfrowane.</span><span class="sxs-lookup"><span data-stu-id="c9eae-143">Specifies digest authentication.</span></span>|  
|<span data-ttu-id="c9eae-144">Uwierzytelnianie NTLM</span><span class="sxs-lookup"><span data-stu-id="c9eae-144">Ntlm</span></span>|<span data-ttu-id="c9eae-145">Określa uwierzytelniania NTLM, jeśli jest to możliwe, a w przypadku niepowodzenia uwierzytelniania Windows.</span><span class="sxs-lookup"><span data-stu-id="c9eae-145">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="c9eae-146">Windows</span><span class="sxs-lookup"><span data-stu-id="c9eae-146">Windows</span></span>|<span data-ttu-id="c9eae-147">Określa, czy zintegrowane uwierzytelnianie Windows</span><span class="sxs-lookup"><span data-stu-id="c9eae-147">Specifies Windows integrated authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="c9eae-148">proxyCredentialType atrybutu</span><span class="sxs-lookup"><span data-stu-id="c9eae-148">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="c9eae-149">Wartość</span><span class="sxs-lookup"><span data-stu-id="c9eae-149">Value</span></span>|<span data-ttu-id="c9eae-150">Opis</span><span class="sxs-lookup"><span data-stu-id="c9eae-150">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c9eae-151">Brak</span><span class="sxs-lookup"><span data-stu-id="c9eae-151">None</span></span>|<span data-ttu-id="c9eae-152">— Liczba komunikatów nie są zabezpieczane podczas przesyłania.</span><span class="sxs-lookup"><span data-stu-id="c9eae-152">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="c9eae-153">Podstawowy</span><span class="sxs-lookup"><span data-stu-id="c9eae-153">Basic</span></span>|<span data-ttu-id="c9eae-154">Określa uwierzytelnianie podstawowe, zgodnie z definicją w dokumencie RFC 2617 — uwierzytelnianie HTTP: Podstawowe i uwierzytelnianie szyfrowane.</span><span class="sxs-lookup"><span data-stu-id="c9eae-154">Specifies basic authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="c9eae-155">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="c9eae-155">Digest</span></span>|<span data-ttu-id="c9eae-156">Określa uwierzytelniania szyfrowanego, zgodnie z definicją w dokumencie RFC 2617 — uwierzytelnianie HTTP: Podstawowe i uwierzytelnianie szyfrowane.</span><span class="sxs-lookup"><span data-stu-id="c9eae-156">Specifies digest authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="c9eae-157">Uwierzytelnianie NTLM</span><span class="sxs-lookup"><span data-stu-id="c9eae-157">Ntlm</span></span>|<span data-ttu-id="c9eae-158">Określa uwierzytelniania NTLM, jeśli jest to możliwe, a w przypadku niepowodzenia uwierzytelniania Windows.</span><span class="sxs-lookup"><span data-stu-id="c9eae-158">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="c9eae-159">Windows</span><span class="sxs-lookup"><span data-stu-id="c9eae-159">Windows</span></span>|<span data-ttu-id="c9eae-160">Określa, czy zintegrowane uwierzytelnianie Windows</span><span class="sxs-lookup"><span data-stu-id="c9eae-160">Specifies Windows integrated authentication.</span></span>|  
|<span data-ttu-id="c9eae-161">Certyfikat</span><span class="sxs-lookup"><span data-stu-id="c9eae-161">Certificate</span></span>|<span data-ttu-id="c9eae-162">Wykonuje uwierzytelnianie klienta przy użyciu certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="c9eae-162">Performs client authentication using a certificate.</span></span> <span data-ttu-id="c9eae-163">Ta opcja działa tylko wtedy, gdy `Mode` atrybutu elementu nadrzędnego `security` elementu jest ustawiona na Transport i nie będzie działać, jeśli jest ustawiona wartość TransportCredentialOnly.</span><span class="sxs-lookup"><span data-stu-id="c9eae-163">This option works only if the `Mode` attribute of the parent `security` element is set to Transport, and will not work if it is set to TransportCredentialOnly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c9eae-164">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c9eae-164">Child Elements</span></span>  
 <span data-ttu-id="c9eae-165">Brak</span><span class="sxs-lookup"><span data-stu-id="c9eae-165">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c9eae-166">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c9eae-166">Parent Elements</span></span>  
  
|<span data-ttu-id="c9eae-167">Element</span><span class="sxs-lookup"><span data-stu-id="c9eae-167">Element</span></span>|<span data-ttu-id="c9eae-168">Opis</span><span class="sxs-lookup"><span data-stu-id="c9eae-168">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c9eae-169">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="c9eae-169">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nethttpbinding.md)|<span data-ttu-id="c9eae-170">Definiuje funkcje bezpieczeństwa umożliwiające [ \<netHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nethttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="c9eae-170">Defines the security capabilities for the [\<netHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/nethttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c9eae-171">Przykład</span><span class="sxs-lookup"><span data-stu-id="c9eae-171">Example</span></span>  
 <span data-ttu-id="c9eae-172">Poniższy przykład pokazuje użycie protokołu SSL z zabezpieczeń transportu dla wiązania podstawowe.</span><span class="sxs-lookup"><span data-stu-id="c9eae-172">The following example demonstrates the use of SSL transport security with the basic binding.</span></span> <span data-ttu-id="c9eae-173">Domyślnie podstawowe powiązanie obsługuje komunikację HTTP.</span><span class="sxs-lookup"><span data-stu-id="c9eae-173">By default, the basic binding supports HTTP communication.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c9eae-174">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c9eae-174">See Also</span></span>  
 <span data-ttu-id="c9eae-175"><xref:System.ServiceModel.BasicHttpSecurityMode.Transport><xref:System.ServiceModel.Configuration.HttpTransportSecurityElement></span><span class="sxs-lookup"><span data-stu-id="c9eae-175"><xref:System.ServiceModel.BasicHttpSecurityMode.Transport> <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement></span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 [<span data-ttu-id="c9eae-176">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="c9eae-176">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="c9eae-177">Powiązania</span><span class="sxs-lookup"><span data-stu-id="c9eae-177">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="c9eae-178">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="c9eae-178">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="c9eae-179">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="c9eae-179">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="c9eae-180">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="c9eae-180">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
