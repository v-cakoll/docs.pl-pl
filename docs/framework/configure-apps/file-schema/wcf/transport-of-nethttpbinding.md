---
title: '&lt;transport&gt; w &lt;netHttpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3b180006-1661-43bf-a699-96fd3da469af
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3128ac2f36d778bc502fe56b776a15c51f1fda69
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="lttransportgt-of-ltnethttpbindinggt"></a><span data-ttu-id="8a12a-102">&lt;transport&gt; w &lt;netHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="8a12a-102">&lt;transport&gt; of &lt;netHttpBinding&gt;</span></span>
<span data-ttu-id="8a12a-103">Definiuje właściwości sterujące parametrami uwierzytelniania dla transportu HTTP.</span><span class="sxs-lookup"><span data-stu-id="8a12a-103">Defines properties that control authentication parameters for the HTTP transport.</span></span>  
  
<span data-ttu-id="8a12a-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="8a12a-104">\<system.serviceModel></span></span>  
<span data-ttu-id="8a12a-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="8a12a-105">\<bindings></span></span>  
<span data-ttu-id="8a12a-106">\<netHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="8a12a-106">\<netHttpBinding></span></span>  
<span data-ttu-id="8a12a-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="8a12a-107">\<binding></span></span>  
<span data-ttu-id="8a12a-108">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="8a12a-108">\<security></span></span>  
<span data-ttu-id="8a12a-109">\<transport ></span><span class="sxs-lookup"><span data-stu-id="8a12a-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a12a-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="8a12a-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8a12a-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8a12a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="8a12a-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8a12a-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8a12a-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8a12a-113">Attributes</span></span>  
  
|<span data-ttu-id="8a12a-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="8a12a-114">Attribute</span></span>|<span data-ttu-id="8a12a-115">Opis</span><span class="sxs-lookup"><span data-stu-id="8a12a-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8a12a-116">Właściwość clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="8a12a-116">clientCredentialType</span></span>|<span data-ttu-id="8a12a-117">— Określa typ poświadczenia, które będą używane podczas uwierzytelniania klienta przy użyciu uwierzytelniania HTTP.</span><span class="sxs-lookup"><span data-stu-id="8a12a-117">-   Specifies the type of credential to be used when performing client authentication using HTTP authentication.</span></span>  <span data-ttu-id="8a12a-118">Wartość domyślna to `None`.</span><span class="sxs-lookup"><span data-stu-id="8a12a-118">The default is `None`.</span></span> <span data-ttu-id="8a12a-119">Ten atrybut jest typu <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="8a12a-119">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|<span data-ttu-id="8a12a-120">proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="8a12a-120">proxyCredentialType</span></span>|<span data-ttu-id="8a12a-121">— Określa typ poświadczenia, które będą używane podczas uwierzytelniania klienta z w obrębie domeny przy użyciu serwera proxy za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="8a12a-121">-   Specifies the type of credential to be used when performing client authentication from within a domain using a proxy over HTTP.</span></span> <span data-ttu-id="8a12a-122">Ten atrybut jest stosowane tylko wtedy, gdy `mode` atrybutu nadrzędnego `security` jest element `Transport` lub `TransportCredentialsOnly`.</span><span class="sxs-lookup"><span data-stu-id="8a12a-122">This attribute is applicable only when the `mode` attribute of the parent `security` element is `Transport` or `TransportCredentialsOnly`.</span></span> <span data-ttu-id="8a12a-123">Ten atrybut jest typu <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="8a12a-123">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|<span data-ttu-id="8a12a-124">obszar</span><span class="sxs-lookup"><span data-stu-id="8a12a-124">realm</span></span>|<span data-ttu-id="8a12a-125">Ciąg określający obszar, który jest używany przez schemat uwierzytelniania HTTP dla uwierzytelniania podstawowego lub szyfrowanego.</span><span class="sxs-lookup"><span data-stu-id="8a12a-125">A string that specifies the realm that is used by the HTTP authentication scheme for digest or basic authentication.</span></span> <span data-ttu-id="8a12a-126">Wartość domyślna to ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="8a12a-126">The default is an empty string.</span></span>|  
|<span data-ttu-id="8a12a-127">Właściwość policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="8a12a-127">policyEnforcement</span></span>|<span data-ttu-id="8a12a-128">To wyliczenie Określa, kiedy <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> powinny być wymuszane.</span><span class="sxs-lookup"><span data-stu-id="8a12a-128">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="8a12a-129">1.  Nigdy nie — zasady nigdy nie są wymuszane (ochrona rozszerzona jest wyłączona).</span><span class="sxs-lookup"><span data-stu-id="8a12a-129">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="8a12a-130">2.  WhenSupported — zasady są wymuszane tylko wtedy, gdy klient obsługuje ochrony rozszerzonej.</span><span class="sxs-lookup"><span data-stu-id="8a12a-130">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="8a12a-131">3.  Zawsze — zasady zawsze są wymuszane.</span><span class="sxs-lookup"><span data-stu-id="8a12a-131">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="8a12a-132">Klienci, którzy nie obsługują ochrony rozszerzonej będzie mogło uwierzytelnić.</span><span class="sxs-lookup"><span data-stu-id="8a12a-132">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
|<span data-ttu-id="8a12a-133">protectionScenario</span><span class="sxs-lookup"><span data-stu-id="8a12a-133">protectionScenario</span></span>|<span data-ttu-id="8a12a-134">To wyliczenie Określa scenariusz ochrony wymuszany przez zasady.</span><span class="sxs-lookup"><span data-stu-id="8a12a-134">This enumeration specifies the protection scenario enforced by the policy.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="8a12a-135">właściwości ClientCredentialType o wartości atrybutu</span><span class="sxs-lookup"><span data-stu-id="8a12a-135">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="8a12a-136">Wartość</span><span class="sxs-lookup"><span data-stu-id="8a12a-136">Value</span></span>|<span data-ttu-id="8a12a-137">Opis</span><span class="sxs-lookup"><span data-stu-id="8a12a-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8a12a-138">Brak</span><span class="sxs-lookup"><span data-stu-id="8a12a-138">None</span></span>|<span data-ttu-id="8a12a-139">Komunikaty nie są już zabezpieczone podczas transferu.</span><span class="sxs-lookup"><span data-stu-id="8a12a-139">Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="8a12a-140">Podstawowy</span><span class="sxs-lookup"><span data-stu-id="8a12a-140">Basic</span></span>|<span data-ttu-id="8a12a-141">Określa uwierzytelnianie podstawowe.</span><span class="sxs-lookup"><span data-stu-id="8a12a-141">Specifies basic authentication.</span></span>|  
|<span data-ttu-id="8a12a-142">Skrót</span><span class="sxs-lookup"><span data-stu-id="8a12a-142">Digest</span></span>|<span data-ttu-id="8a12a-143">Określa uwierzytelnianie szyfrowane.</span><span class="sxs-lookup"><span data-stu-id="8a12a-143">Specifies digest authentication.</span></span>|  
|<span data-ttu-id="8a12a-144">Uwierzytelnianie NTLM</span><span class="sxs-lookup"><span data-stu-id="8a12a-144">Ntlm</span></span>|<span data-ttu-id="8a12a-145">Określa uwierzytelniania NTLM, jeśli to możliwe, a w przypadku niepowodzenia uwierzytelniania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="8a12a-145">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="8a12a-146">Windows</span><span class="sxs-lookup"><span data-stu-id="8a12a-146">Windows</span></span>|<span data-ttu-id="8a12a-147">Określa zintegrowane uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="8a12a-147">Specifies Windows integrated authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="8a12a-148">proxyCredentialType atrybutu</span><span class="sxs-lookup"><span data-stu-id="8a12a-148">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="8a12a-149">Wartość</span><span class="sxs-lookup"><span data-stu-id="8a12a-149">Value</span></span>|<span data-ttu-id="8a12a-150">Opis</span><span class="sxs-lookup"><span data-stu-id="8a12a-150">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8a12a-151">Brak</span><span class="sxs-lookup"><span data-stu-id="8a12a-151">None</span></span>|<span data-ttu-id="8a12a-152">— Liczba komunikatów nie są już zabezpieczone podczas transferu.</span><span class="sxs-lookup"><span data-stu-id="8a12a-152">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="8a12a-153">Podstawowy</span><span class="sxs-lookup"><span data-stu-id="8a12a-153">Basic</span></span>|<span data-ttu-id="8a12a-154">Określa uwierzytelnianie podstawowe, zgodnie z definicją w dokumencie RFC 2617 — uwierzytelnianie HTTP: Basic i uwierzytelniania szyfrowanego.</span><span class="sxs-lookup"><span data-stu-id="8a12a-154">Specifies basic authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="8a12a-155">Skrót</span><span class="sxs-lookup"><span data-stu-id="8a12a-155">Digest</span></span>|<span data-ttu-id="8a12a-156">Określa uwierzytelnianie szyfrowane zgodnie z definicją w dokumencie RFC 2617 — uwierzytelnianie HTTP: Basic i uwierzytelniania szyfrowanego.</span><span class="sxs-lookup"><span data-stu-id="8a12a-156">Specifies digest authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="8a12a-157">Uwierzytelnianie NTLM</span><span class="sxs-lookup"><span data-stu-id="8a12a-157">Ntlm</span></span>|<span data-ttu-id="8a12a-158">Określa uwierzytelniania NTLM, jeśli to możliwe, a w przypadku niepowodzenia uwierzytelniania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="8a12a-158">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="8a12a-159">Windows</span><span class="sxs-lookup"><span data-stu-id="8a12a-159">Windows</span></span>|<span data-ttu-id="8a12a-160">Określa zintegrowane uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="8a12a-160">Specifies Windows integrated authentication.</span></span>|  
|<span data-ttu-id="8a12a-161">certyfikat</span><span class="sxs-lookup"><span data-stu-id="8a12a-161">Certificate</span></span>|<span data-ttu-id="8a12a-162">Wykonuje uwierzytelnianie klienta przy użyciu certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="8a12a-162">Performs client authentication using a certificate.</span></span> <span data-ttu-id="8a12a-163">Ta opcja działa tylko wtedy, gdy `Mode` atrybutu nadrzędnego `security` element ma ustawioną wartość transportu i nie będzie działać, jeśli jest ustawiona wartość TransportCredentialOnly.</span><span class="sxs-lookup"><span data-stu-id="8a12a-163">This option works only if the `Mode` attribute of the parent `security` element is set to Transport, and will not work if it is set to TransportCredentialOnly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8a12a-164">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8a12a-164">Child Elements</span></span>  
 <span data-ttu-id="8a12a-165">Brak</span><span class="sxs-lookup"><span data-stu-id="8a12a-165">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8a12a-166">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8a12a-166">Parent Elements</span></span>  
  
|<span data-ttu-id="8a12a-167">Element</span><span class="sxs-lookup"><span data-stu-id="8a12a-167">Element</span></span>|<span data-ttu-id="8a12a-168">Opis</span><span class="sxs-lookup"><span data-stu-id="8a12a-168">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8a12a-169">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="8a12a-169">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nethttpbinding.md)|<span data-ttu-id="8a12a-170">Definiuje funkcje zabezpieczeń dla [ \<netHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nethttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="8a12a-170">Defines the security capabilities for the [\<netHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/nethttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8a12a-171">Przykład</span><span class="sxs-lookup"><span data-stu-id="8a12a-171">Example</span></span>  
 <span data-ttu-id="8a12a-172">W poniższym przykładzie pokazano użycie zabezpieczenia transportowe protokołu SSL z powiązaniem podstawowe.</span><span class="sxs-lookup"><span data-stu-id="8a12a-172">The following example demonstrates the use of SSL transport security with the basic binding.</span></span> <span data-ttu-id="8a12a-173">Domyślnie podstawowe wiązanie obsługuje komunikację HTTP.</span><span class="sxs-lookup"><span data-stu-id="8a12a-173">By default, the basic binding supports HTTP communication.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8a12a-174">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8a12a-174">See Also</span></span>  
 <span data-ttu-id="8a12a-175"><xref:System.ServiceModel.BasicHttpSecurityMode.Transport><xref:System.ServiceModel.Configuration.HttpTransportSecurityElement></span><span class="sxs-lookup"><span data-stu-id="8a12a-175"><xref:System.ServiceModel.BasicHttpSecurityMode.Transport> <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement></span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 [<span data-ttu-id="8a12a-176">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="8a12a-176">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="8a12a-177">Powiązania</span><span class="sxs-lookup"><span data-stu-id="8a12a-177">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="8a12a-178">Konfigurowanie powiązań dostarczanych przez System</span><span class="sxs-lookup"><span data-stu-id="8a12a-178">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="8a12a-179">Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="8a12a-179">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="8a12a-180">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="8a12a-180">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
