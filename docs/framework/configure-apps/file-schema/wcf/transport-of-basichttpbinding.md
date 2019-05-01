---
title: <transport> dla <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 4c5ba293-3d7e-47a6-b84e-e9022857b7e5
ms.openlocfilehash: 5d1ef059f8fde7c41e333571d1c025a9c0c7e03f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788391"
---
# <a name="transport-of-basichttpbinding"></a><span data-ttu-id="91c44-102">\<transport > z \<basicHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="91c44-102">\<transport> of \<basicHttpBinding></span></span>
<span data-ttu-id="91c44-103">Definiuje właściwości sterujące parametrami uwierzytelniania dla protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="91c44-103">Defines properties that control authentication parameters for the HTTP transport.</span></span>  
  
 <span data-ttu-id="91c44-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="91c44-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="91c44-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="91c44-105">\<bindings></span></span>  
<span data-ttu-id="91c44-106">\<basicHttpBinding></span><span class="sxs-lookup"><span data-stu-id="91c44-106">\<basicHttpBinding></span></span>  
<span data-ttu-id="91c44-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="91c44-107">\<binding></span></span>  
<span data-ttu-id="91c44-108">\<security></span><span class="sxs-lookup"><span data-stu-id="91c44-108">\<security></span></span>  
<span data-ttu-id="91c44-109">\<transport></span><span class="sxs-lookup"><span data-stu-id="91c44-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91c44-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="91c44-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="91c44-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="91c44-111">Attributes and Elements</span></span>  
 <span data-ttu-id="91c44-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="91c44-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="91c44-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="91c44-113">Attributes</span></span>  
  
|<span data-ttu-id="91c44-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="91c44-114">Attribute</span></span>|<span data-ttu-id="91c44-115">Opis</span><span class="sxs-lookup"><span data-stu-id="91c44-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="91c44-116">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="91c44-116">clientCredentialType</span></span>|<span data-ttu-id="91c44-117">-Określa typ poświadczenia do użycia podczas przeprowadzania uwierzytelniania klienta przy użyciu uwierzytelniania HTTP.</span><span class="sxs-lookup"><span data-stu-id="91c44-117">-   Specifies the type of credential to be used when performing client authentication using HTTP authentication.</span></span>  <span data-ttu-id="91c44-118">Wartość domyślna to `None`.</span><span class="sxs-lookup"><span data-stu-id="91c44-118">The default is `None`.</span></span> <span data-ttu-id="91c44-119">Ten atrybut jest typu <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="91c44-119">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|<span data-ttu-id="91c44-120">proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="91c44-120">proxyCredentialType</span></span>|<span data-ttu-id="91c44-121">-Określa typ poświadczenia do użycia podczas przeprowadzania uwierzytelniania klienta z w obrębie domeny przy użyciu serwera proxy za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="91c44-121">-   Specifies the type of credential to be used when performing client authentication from within a domain using a proxy over HTTP.</span></span> <span data-ttu-id="91c44-122">Ten atrybut jest stosowane tylko wtedy, gdy `mode` atrybutu elementu nadrzędnego `security` element jest `Transport` lub `TransportCredentialsOnly`.</span><span class="sxs-lookup"><span data-stu-id="91c44-122">This attribute is applicable only when the `mode` attribute of the parent `security` element is `Transport` or `TransportCredentialsOnly`.</span></span> <span data-ttu-id="91c44-123">Ten atrybut jest typu <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="91c44-123">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|<span data-ttu-id="91c44-124">obszar</span><span class="sxs-lookup"><span data-stu-id="91c44-124">realm</span></span>|<span data-ttu-id="91c44-125">Ciąg, który określa obszar, który jest używany przez schemat uwierzytelniania HTTP digest lub uwierzytelnianie podstawowe.</span><span class="sxs-lookup"><span data-stu-id="91c44-125">A string that specifies the realm that is used by the HTTP authentication scheme for digest or basic authentication.</span></span> <span data-ttu-id="91c44-126">Wartość domyślna to ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="91c44-126">The default is an empty string.</span></span>|  
|<span data-ttu-id="91c44-127">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="91c44-127">policyEnforcement</span></span>|<span data-ttu-id="91c44-128">To wyliczenie Określa, kiedy <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> powinny być wymuszane.</span><span class="sxs-lookup"><span data-stu-id="91c44-128">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="91c44-129">1.  Nigdy nie — zasady nigdy nie są wymuszane (ochrony rozszerzonej jest wyłączone).</span><span class="sxs-lookup"><span data-stu-id="91c44-129">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="91c44-130">2.  WhenSupported — zasady są wymuszane tylko wtedy, gdy klient obsługuje ochrony rozszerzonej.</span><span class="sxs-lookup"><span data-stu-id="91c44-130">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="91c44-131">3.  Zawsze — zasady zawsze są wymuszane.</span><span class="sxs-lookup"><span data-stu-id="91c44-131">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="91c44-132">Klienci, którzy nie obsługują ochrony rozszerzonej zakończy się niepowodzeniem do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="91c44-132">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
|<span data-ttu-id="91c44-133">protectionScenario</span><span class="sxs-lookup"><span data-stu-id="91c44-133">protectionScenario</span></span>|<span data-ttu-id="91c44-134">To wyliczenie Określa scenariusz ochrony wymuszane przez zasady.</span><span class="sxs-lookup"><span data-stu-id="91c44-134">This enumeration specifies the protection scenario enforced by the policy.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="91c44-135">właściwości ClientCredentialType o wartości atrybutu</span><span class="sxs-lookup"><span data-stu-id="91c44-135">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="91c44-136">Wartość</span><span class="sxs-lookup"><span data-stu-id="91c44-136">Value</span></span>|<span data-ttu-id="91c44-137">Opis</span><span class="sxs-lookup"><span data-stu-id="91c44-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="91c44-138">Brak</span><span class="sxs-lookup"><span data-stu-id="91c44-138">None</span></span>|<span data-ttu-id="91c44-139">Komunikaty nie są zabezpieczane podczas przesyłania.</span><span class="sxs-lookup"><span data-stu-id="91c44-139">Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="91c44-140">Podstawowy</span><span class="sxs-lookup"><span data-stu-id="91c44-140">Basic</span></span>|<span data-ttu-id="91c44-141">Określa uwierzytelnianie podstawowe.</span><span class="sxs-lookup"><span data-stu-id="91c44-141">Specifies basic authentication.</span></span>|  
|<span data-ttu-id="91c44-142">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="91c44-142">Digest</span></span>|<span data-ttu-id="91c44-143">Określa uwierzytelnianie szyfrowane.</span><span class="sxs-lookup"><span data-stu-id="91c44-143">Specifies digest authentication.</span></span>|  
|<span data-ttu-id="91c44-144">Ntlm</span><span class="sxs-lookup"><span data-stu-id="91c44-144">Ntlm</span></span>|<span data-ttu-id="91c44-145">Określa uwierzytelniania NTLM, jeśli jest to możliwe, a w przypadku niepowodzenia uwierzytelniania Windows.</span><span class="sxs-lookup"><span data-stu-id="91c44-145">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="91c44-146">Windows</span><span class="sxs-lookup"><span data-stu-id="91c44-146">Windows</span></span>|<span data-ttu-id="91c44-147">Określa, czy zintegrowane uwierzytelnianie Windows</span><span class="sxs-lookup"><span data-stu-id="91c44-147">Specifies Windows integrated authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="91c44-148">proxyCredentialType atrybutu</span><span class="sxs-lookup"><span data-stu-id="91c44-148">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="91c44-149">Wartość</span><span class="sxs-lookup"><span data-stu-id="91c44-149">Value</span></span>|<span data-ttu-id="91c44-150">Opis</span><span class="sxs-lookup"><span data-stu-id="91c44-150">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="91c44-151">Brak</span><span class="sxs-lookup"><span data-stu-id="91c44-151">None</span></span>|<span data-ttu-id="91c44-152">— Liczba komunikatów nie są zabezpieczane podczas przesyłania.</span><span class="sxs-lookup"><span data-stu-id="91c44-152">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="91c44-153">Podstawowy</span><span class="sxs-lookup"><span data-stu-id="91c44-153">Basic</span></span>|<span data-ttu-id="91c44-154">Określa uwierzytelnianie podstawowe, zgodnie z definicją w dokumencie RFC 2617 — uwierzytelnianie HTTP: Podstawowe i uwierzytelnianie szyfrowane.</span><span class="sxs-lookup"><span data-stu-id="91c44-154">Specifies basic authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="91c44-155">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="91c44-155">Digest</span></span>|<span data-ttu-id="91c44-156">Określa uwierzytelniania szyfrowanego, zgodnie z definicją w dokumencie RFC 2617 — uwierzytelnianie HTTP: Podstawowe i uwierzytelnianie szyfrowane.</span><span class="sxs-lookup"><span data-stu-id="91c44-156">Specifies digest authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="91c44-157">Ntlm</span><span class="sxs-lookup"><span data-stu-id="91c44-157">Ntlm</span></span>|<span data-ttu-id="91c44-158">Określa uwierzytelniania NTLM, jeśli jest to możliwe, a w przypadku niepowodzenia uwierzytelniania Windows.</span><span class="sxs-lookup"><span data-stu-id="91c44-158">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="91c44-159">Windows</span><span class="sxs-lookup"><span data-stu-id="91c44-159">Windows</span></span>|<span data-ttu-id="91c44-160">Określa, czy zintegrowane uwierzytelnianie Windows</span><span class="sxs-lookup"><span data-stu-id="91c44-160">Specifies Windows integrated authentication.</span></span>|  
|<span data-ttu-id="91c44-161">Certyfikat</span><span class="sxs-lookup"><span data-stu-id="91c44-161">Certificate</span></span>|<span data-ttu-id="91c44-162">Wykonuje uwierzytelnianie klienta przy użyciu certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="91c44-162">Performs client authentication using a certificate.</span></span> <span data-ttu-id="91c44-163">Ta opcja działa tylko wtedy, gdy `Mode` atrybutu elementu nadrzędnego `security` elementu jest ustawiona na Transport i nie będzie działać, jeśli jest ustawiona wartość TransportCredentialOnly.</span><span class="sxs-lookup"><span data-stu-id="91c44-163">This option works only if the `Mode` attribute of the parent `security` element is set to Transport, and will not work if it is set to TransportCredentialOnly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="91c44-164">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="91c44-164">Child Elements</span></span>  
 <span data-ttu-id="91c44-165">Brak</span><span class="sxs-lookup"><span data-stu-id="91c44-165">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="91c44-166">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="91c44-166">Parent Elements</span></span>  
  
|<span data-ttu-id="91c44-167">Element</span><span class="sxs-lookup"><span data-stu-id="91c44-167">Element</span></span>|<span data-ttu-id="91c44-168">Opis</span><span class="sxs-lookup"><span data-stu-id="91c44-168">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="91c44-169">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="91c44-169">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)|<span data-ttu-id="91c44-170">Definiuje funkcje bezpieczeństwa umożliwiające [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="91c44-170">Defines the security capabilities for the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="91c44-171">Przykład</span><span class="sxs-lookup"><span data-stu-id="91c44-171">Example</span></span>  
 <span data-ttu-id="91c44-172">Poniższy przykład pokazuje użycie protokołu SSL z zabezpieczeń transportu dla wiązania podstawowe.</span><span class="sxs-lookup"><span data-stu-id="91c44-172">The following example demonstrates the use of SSL transport security with the basic binding.</span></span> <span data-ttu-id="91c44-173">Domyślnie podstawowe powiązanie obsługuje komunikację HTTP.</span><span class="sxs-lookup"><span data-stu-id="91c44-173">By default, the basic binding supports HTTP communication.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="91c44-174">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="91c44-174">See also</span></span>

- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.BasicHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- <xref:System.ServiceModel.HttpTransportSecurity>
- [<span data-ttu-id="91c44-175">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="91c44-175">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="91c44-176">Powiązania</span><span class="sxs-lookup"><span data-stu-id="91c44-176">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="91c44-177">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="91c44-177">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="91c44-178">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="91c44-178">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="91c44-179">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="91c44-179">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
