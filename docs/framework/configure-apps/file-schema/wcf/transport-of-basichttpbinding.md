---
title: <transport> dla <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 4c5ba293-3d7e-47a6-b84e-e9022857b7e5
ms.openlocfilehash: c563339e4f854cc4e60f92dd5b8c0b39112dc000
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736121"
---
# <a name="transport-of-basichttpbinding"></a><span data-ttu-id="525a3-102">\<transport> dla \<basicHttpBinding></span><span class="sxs-lookup"><span data-stu-id="525a3-102">\<transport> of \<basicHttpBinding></span></span>
<span data-ttu-id="525a3-103">Definiuje właściwości kontrolujące parametry uwierzytelniania dla transportu HTTP.</span><span class="sxs-lookup"><span data-stu-id="525a3-103">Defines properties that control authentication parameters for the HTTP transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<basicHttpBinding>**](basichttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-basichttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="525a3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="525a3-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="525a3-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="525a3-105">Attributes and Elements</span></span>  
 <span data-ttu-id="525a3-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="525a3-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="525a3-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="525a3-107">Attributes</span></span>  
  
|<span data-ttu-id="525a3-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="525a3-108">Attribute</span></span>|<span data-ttu-id="525a3-109">Opis</span><span class="sxs-lookup"><span data-stu-id="525a3-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="525a3-110">Powiązania ClientCredentialType</span><span class="sxs-lookup"><span data-stu-id="525a3-110">clientCredentialType</span></span>|<span data-ttu-id="525a3-111">-Określa typ poświadczeń, które mają być używane podczas uwierzytelniania klienta przy użyciu uwierzytelniania HTTP.</span><span class="sxs-lookup"><span data-stu-id="525a3-111">-   Specifies the type of credential to be used when performing client authentication using HTTP authentication.</span></span>  <span data-ttu-id="525a3-112">Wartość domyślna to `None`.</span><span class="sxs-lookup"><span data-stu-id="525a3-112">The default is `None`.</span></span> <span data-ttu-id="525a3-113">Ten atrybut jest typu <xref:System.ServiceModel.HttpClientCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="525a3-113">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|<span data-ttu-id="525a3-114">proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="525a3-114">proxyCredentialType</span></span>|<span data-ttu-id="525a3-115">-Określa typ poświadczeń, które mają być używane podczas uwierzytelniania klienta w domenie przy użyciu serwera proxy za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="525a3-115">-   Specifies the type of credential to be used when performing client authentication from within a domain using a proxy over HTTP.</span></span> <span data-ttu-id="525a3-116">Ten atrybut jest stosowany tylko wtedy, gdy `mode` atrybut elementu nadrzędnego `security` to `Transport` or `TransportCredentialsOnly` .</span><span class="sxs-lookup"><span data-stu-id="525a3-116">This attribute is applicable only when the `mode` attribute of the parent `security` element is `Transport` or `TransportCredentialsOnly`.</span></span> <span data-ttu-id="525a3-117">Ten atrybut jest typu <xref:System.ServiceModel.HttpProxyCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="525a3-117">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|<span data-ttu-id="525a3-118">obszarów</span><span class="sxs-lookup"><span data-stu-id="525a3-118">realm</span></span>|<span data-ttu-id="525a3-119">Ciąg określający obszar, który jest używany przez schemat uwierzytelniania HTTP na potrzeby uwierzytelniania szyfrowanego lub podstawowego.</span><span class="sxs-lookup"><span data-stu-id="525a3-119">A string that specifies the realm that is used by the HTTP authentication scheme for digest or basic authentication.</span></span> <span data-ttu-id="525a3-120">Wartość domyślna to pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="525a3-120">The default is an empty string.</span></span>|  
|<span data-ttu-id="525a3-121">Zasady PolicyEnforcement</span><span class="sxs-lookup"><span data-stu-id="525a3-121">policyEnforcement</span></span>|<span data-ttu-id="525a3-122">To Wyliczenie określa, kiedy <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> należy wymusić.</span><span class="sxs-lookup"><span data-stu-id="525a3-122">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="525a3-123">1. nigdy — zasady nigdy nie są wymuszane (ochrona rozszerzona jest wyłączona).</span><span class="sxs-lookup"><span data-stu-id="525a3-123">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="525a3-124">2. WhenSupported — zasady są wymuszane tylko wtedy, gdy klient obsługuje ochronę rozszerzoną.</span><span class="sxs-lookup"><span data-stu-id="525a3-124">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="525a3-125">3. zawsze — zasady są zawsze wymuszane.</span><span class="sxs-lookup"><span data-stu-id="525a3-125">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="525a3-126">Klienci, którzy nie obsługują rozszerzonej ochrony, nie będą uwierzytelniani.</span><span class="sxs-lookup"><span data-stu-id="525a3-126">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
|<span data-ttu-id="525a3-127">protectionScenario</span><span class="sxs-lookup"><span data-stu-id="525a3-127">protectionScenario</span></span>|<span data-ttu-id="525a3-128">To Wyliczenie określa scenariusz ochrony wymuszany przez zasady.</span><span class="sxs-lookup"><span data-stu-id="525a3-128">This enumeration specifies the protection scenario enforced by the policy.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="525a3-129">clientCredentialtype — atrybut</span><span class="sxs-lookup"><span data-stu-id="525a3-129">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="525a3-130">Wartość</span><span class="sxs-lookup"><span data-stu-id="525a3-130">Value</span></span>|<span data-ttu-id="525a3-131">Opis</span><span class="sxs-lookup"><span data-stu-id="525a3-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="525a3-132">Brak</span><span class="sxs-lookup"><span data-stu-id="525a3-132">None</span></span>|<span data-ttu-id="525a3-133">Komunikaty nie są zabezpieczane podczas transferu.</span><span class="sxs-lookup"><span data-stu-id="525a3-133">Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="525a3-134">Podstawowy</span><span class="sxs-lookup"><span data-stu-id="525a3-134">Basic</span></span>|<span data-ttu-id="525a3-135">Określa podstawowe uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="525a3-135">Specifies basic authentication.</span></span>|  
|<span data-ttu-id="525a3-136">Szyfrowane</span><span class="sxs-lookup"><span data-stu-id="525a3-136">Digest</span></span>|<span data-ttu-id="525a3-137">Określa uwierzytelnianie szyfrowane.</span><span class="sxs-lookup"><span data-stu-id="525a3-137">Specifies digest authentication.</span></span>|  
|<span data-ttu-id="525a3-138">NTLM</span><span class="sxs-lookup"><span data-stu-id="525a3-138">Ntlm</span></span>|<span data-ttu-id="525a3-139">Określa uwierzytelnianie NTLM, jeśli jest to możliwe, a uwierzytelnianie systemu Windows kończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="525a3-139">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="525a3-140">Windows</span><span class="sxs-lookup"><span data-stu-id="525a3-140">Windows</span></span>|<span data-ttu-id="525a3-141">Określa zintegrowane uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="525a3-141">Specifies Windows integrated authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="525a3-142">proxyCredentialType — atrybut</span><span class="sxs-lookup"><span data-stu-id="525a3-142">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="525a3-143">Wartość</span><span class="sxs-lookup"><span data-stu-id="525a3-143">Value</span></span>|<span data-ttu-id="525a3-144">Opis</span><span class="sxs-lookup"><span data-stu-id="525a3-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="525a3-145">Brak</span><span class="sxs-lookup"><span data-stu-id="525a3-145">None</span></span>|<span data-ttu-id="525a3-146">-Komunikaty nie są zabezpieczane podczas transferu.</span><span class="sxs-lookup"><span data-stu-id="525a3-146">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="525a3-147">Podstawowy</span><span class="sxs-lookup"><span data-stu-id="525a3-147">Basic</span></span>|<span data-ttu-id="525a3-148">Określa uwierzytelnianie podstawowe zgodnie z definicją w dokumencie RFC 2617 — uwierzytelnianie HTTP: uwierzytelnianie podstawowe i szyfrowane.</span><span class="sxs-lookup"><span data-stu-id="525a3-148">Specifies basic authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="525a3-149">Szyfrowane</span><span class="sxs-lookup"><span data-stu-id="525a3-149">Digest</span></span>|<span data-ttu-id="525a3-150">Określa uwierzytelnianie szyfrowane zgodnie z definicją w dokumencie RFC 2617 — uwierzytelnianie HTTP: uwierzytelnianie podstawowe i szyfrowane.</span><span class="sxs-lookup"><span data-stu-id="525a3-150">Specifies digest authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="525a3-151">NTLM</span><span class="sxs-lookup"><span data-stu-id="525a3-151">Ntlm</span></span>|<span data-ttu-id="525a3-152">Określa uwierzytelnianie NTLM, jeśli jest to możliwe, a uwierzytelnianie systemu Windows kończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="525a3-152">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="525a3-153">Windows</span><span class="sxs-lookup"><span data-stu-id="525a3-153">Windows</span></span>|<span data-ttu-id="525a3-154">Określa zintegrowane uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="525a3-154">Specifies Windows integrated authentication.</span></span>|  
|<span data-ttu-id="525a3-155">Certyfikat</span><span class="sxs-lookup"><span data-stu-id="525a3-155">Certificate</span></span>|<span data-ttu-id="525a3-156">Wykonuje uwierzytelnianie klienta przy użyciu certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="525a3-156">Performs client authentication using a certificate.</span></span> <span data-ttu-id="525a3-157">Ta opcja działa tylko wtedy `Mode` , gdy atrybut elementu nadrzędnego `security` jest ustawiony na transport i nie będzie działać, jeśli zostanie ustawiony na wartość TransportCredentialOnly.</span><span class="sxs-lookup"><span data-stu-id="525a3-157">This option works only if the `Mode` attribute of the parent `security` element is set to Transport, and will not work if it is set to TransportCredentialOnly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="525a3-158">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="525a3-158">Child Elements</span></span>  
 <span data-ttu-id="525a3-159">Brak</span><span class="sxs-lookup"><span data-stu-id="525a3-159">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="525a3-160">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="525a3-160">Parent Elements</span></span>  
  
|<span data-ttu-id="525a3-161">Element</span><span class="sxs-lookup"><span data-stu-id="525a3-161">Element</span></span>|<span data-ttu-id="525a3-162">Opis</span><span class="sxs-lookup"><span data-stu-id="525a3-162">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-basichttpbinding.md)|<span data-ttu-id="525a3-163">Definiuje funkcje zabezpieczeń dla programu [\<basicHttpBinding>](basichttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="525a3-163">Defines the security capabilities for the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="525a3-164">Przykład</span><span class="sxs-lookup"><span data-stu-id="525a3-164">Example</span></span>  
 <span data-ttu-id="525a3-165">Poniższy przykład ilustruje użycie zabezpieczeń transportu SSL z powiązaniem podstawowym.</span><span class="sxs-lookup"><span data-stu-id="525a3-165">The following example demonstrates the use of SSL transport security with the basic binding.</span></span> <span data-ttu-id="525a3-166">Domyślnie podstawowe powiązanie obsługuje komunikację HTTP.</span><span class="sxs-lookup"><span data-stu-id="525a3-166">By default, the basic binding supports HTTP communication.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="525a3-167">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="525a3-167">See also</span></span>

- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.BasicHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- <xref:System.ServiceModel.HttpTransportSecurity>
- [<span data-ttu-id="525a3-168">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="525a3-168">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="525a3-169">Powiązania</span><span class="sxs-lookup"><span data-stu-id="525a3-169">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="525a3-170">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="525a3-170">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="525a3-171">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="525a3-171">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
