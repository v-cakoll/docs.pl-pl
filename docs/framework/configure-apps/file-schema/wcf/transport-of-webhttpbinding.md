---
title: '&lt;transport&gt; w &lt;webHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: f150fb19-7de1-44af-81f4-86cad881cd05
ms.openlocfilehash: 17468bc2354dc2865f10384e918ffb821a28f059
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32767466"
---
# <a name="lttransportgt-of-ltwebhttpbindinggt"></a><span data-ttu-id="a3937-102">&lt;transport&gt; w &lt;webHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="a3937-102">&lt;transport&gt; of &lt;webHttpBinding&gt;</span></span>
<span data-ttu-id="a3937-103">Definiuje ustawienia zabezpieczeń na poziomie transportu dla punktu końcowego skonfigurowanego do odbierania żądań HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3937-103">Defines the transport-level security settings for a service endpoint configured to receive HTTP requests.</span></span>  
  
 <span data-ttu-id="a3937-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a3937-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a3937-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="a3937-105">\<bindings></span></span>  
<span data-ttu-id="a3937-106">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="a3937-106">\<webHttpBinding></span></span>  
<span data-ttu-id="a3937-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="a3937-107">\<binding></span></span>  
<span data-ttu-id="a3937-108">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="a3937-108">\<security></span></span>  
<span data-ttu-id="a3937-109">\<transport></span><span class="sxs-lookup"><span data-stu-id="a3937-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3937-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="a3937-110">Syntax</span></span>  
  
```xml  
<webHttpBinding>  
    <binding>  
        <security  
        mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">  
            <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"  
             proxyCredentialType="None|Basic|Digest|Ntlm|Windows" realm="string" >  
                <extendedProtectionPolicy  
                     policyEnforcement="Never|WhenSupported|Always"  
                     protectionScenario="TransportSelected|TrustedProxy">  
                    <customServiceNames></customServiceNames>  
                        </extendedProtectionPolicy>  
            </transport>  
        </security>  
    </binding>  
</WebHttpBinding>  
```  
  
## <a name="type"></a><span data-ttu-id="a3937-111">Typ</span><span class="sxs-lookup"><span data-stu-id="a3937-111">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a3937-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a3937-112">Attributes and Elements</span></span>  
 <span data-ttu-id="a3937-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a3937-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a3937-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a3937-114">Attributes</span></span>  
  
|<span data-ttu-id="a3937-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a3937-115">Attribute</span></span>|<span data-ttu-id="a3937-116">Opis</span><span class="sxs-lookup"><span data-stu-id="a3937-116">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="a3937-117">Określa poświadczenia używane do uwierzytelniania klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="a3937-117">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="a3937-118">Ten atrybut jest typu <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="a3937-118">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="a3937-119">Określa poświadczenia używane do uwierzytelniania klienta na serwerze proxy domeny.</span><span class="sxs-lookup"><span data-stu-id="a3937-119">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="a3937-120">Ten atrybut jest typu <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="a3937-120">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="a3937-121">Ciąg określający obszar uwierzytelniania dla uwierzytelniania podstawowego lub szyfrowanego.</span><span class="sxs-lookup"><span data-stu-id="a3937-121">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="a3937-122">Wartość domyślna to ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="a3937-122">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="a3937-123">Obszar uwierzytelniania określa co najmniej nazwę hosta, który przeprowadza uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="a3937-123">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="a3937-124">Można również określić zbiór użytkowników, które ma dostęp.</span><span class="sxs-lookup"><span data-stu-id="a3937-124">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="a3937-125">Użytkownik może zapytania obszaru uwierzytelniania, aby upewnić się, co kilka możliwych nazwy użytkownika i hasła może służyć.</span><span class="sxs-lookup"><span data-stu-id="a3937-125">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|  
|`policyEnforcement`|<span data-ttu-id="a3937-126">To wyliczenie Określa, kiedy <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> powinny być wymuszane.</span><span class="sxs-lookup"><span data-stu-id="a3937-126">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="a3937-127">1.  Nigdy nie — zasady nigdy nie są wymuszane (ochrona rozszerzona jest wyłączona).</span><span class="sxs-lookup"><span data-stu-id="a3937-127">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="a3937-128">2.  WhenSupported — zasady są wymuszane tylko wtedy, gdy klient obsługuje ochrony rozszerzonej.</span><span class="sxs-lookup"><span data-stu-id="a3937-128">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="a3937-129">3.  Zawsze — zasady zawsze są wymuszane.</span><span class="sxs-lookup"><span data-stu-id="a3937-129">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="a3937-130">Klienci, którzy nie obsługują ochrony rozszerzonej będzie mogło uwierzytelnić.</span><span class="sxs-lookup"><span data-stu-id="a3937-130">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="a3937-131">właściwości ClientCredentialType o wartości atrybutu</span><span class="sxs-lookup"><span data-stu-id="a3937-131">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="a3937-132">Wartość</span><span class="sxs-lookup"><span data-stu-id="a3937-132">Value</span></span>|<span data-ttu-id="a3937-133">Opis</span><span class="sxs-lookup"><span data-stu-id="a3937-133">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="a3937-134">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="a3937-134">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="a3937-135">Korzysta z uwierzytelniania podstawowego.</span><span class="sxs-lookup"><span data-stu-id="a3937-135">Uses basic authentication.</span></span>|  
|`Certificate`|<span data-ttu-id="a3937-136">Używa certyfikatów X.509 do uwierzytelniania klienta.</span><span class="sxs-lookup"><span data-stu-id="a3937-136">Uses X.509 certificates to authenticate the client.</span></span>|  
|`Digest`|<span data-ttu-id="a3937-137">Uwierzytelnianie szyfrowane używa.</span><span class="sxs-lookup"><span data-stu-id="a3937-137">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="a3937-138">Korzysta z uwierzytelniania NTLM, jako rezerwowe z domeny systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="a3937-138">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="a3937-139">Używa zintegrowanego uwierzytelniania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="a3937-139">Uses integrated Windows authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="a3937-140">proxyCredentialType atrybutu</span><span class="sxs-lookup"><span data-stu-id="a3937-140">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="a3937-141">Wartość</span><span class="sxs-lookup"><span data-stu-id="a3937-141">Value</span></span>|<span data-ttu-id="a3937-142">Opis</span><span class="sxs-lookup"><span data-stu-id="a3937-142">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="a3937-143">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="a3937-143">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="a3937-144">Korzysta z uwierzytelniania podstawowego.</span><span class="sxs-lookup"><span data-stu-id="a3937-144">Uses basic authentication.</span></span>|  
|`Digest`|<span data-ttu-id="a3937-145">Uwierzytelnianie szyfrowane używa.</span><span class="sxs-lookup"><span data-stu-id="a3937-145">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="a3937-146">Używa protokołu NTLM jako rezerwowe z domeny systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="a3937-146">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="a3937-147">Używa zintegrowanego uwierzytelniania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="a3937-147">Uses integrated Windows authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a3937-148">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a3937-148">Child Elements</span></span>  
 <span data-ttu-id="a3937-149">Brak.</span><span class="sxs-lookup"><span data-stu-id="a3937-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a3937-150">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a3937-150">Parent Elements</span></span>  
  
|<span data-ttu-id="a3937-151">Element</span><span class="sxs-lookup"><span data-stu-id="a3937-151">Element</span></span>|<span data-ttu-id="a3937-152">Opis</span><span class="sxs-lookup"><span data-stu-id="a3937-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a3937-153">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="a3937-153">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-webhttpbinding.md)|<span data-ttu-id="a3937-154">Reprezentuje możliwości zabezpieczeń [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="a3937-154">Represents the security capabilities of the [\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a3937-155">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a3937-155">See Also</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 <xref:System.ServiceModel.Configuration.WebHttpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.WebHttpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>  
 [<span data-ttu-id="a3937-156">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="a3937-156">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="a3937-157">Powiązania</span><span class="sxs-lookup"><span data-stu-id="a3937-157">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="a3937-158">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="a3937-158">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="a3937-159">Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="a3937-159">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="a3937-160">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="a3937-160">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="a3937-161">Model programowania protokołu HTTP sieci Web w programie WCF</span><span class="sxs-lookup"><span data-stu-id="a3937-161">WCF Web HTTP Programming Model</span></span>](../../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
