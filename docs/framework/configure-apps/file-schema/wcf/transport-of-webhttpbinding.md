---
title: <transport> dla <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: f150fb19-7de1-44af-81f4-86cad881cd05
ms.openlocfilehash: f78add5397644dc40bfd22f10bd84aa5c5eb29e6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923210"
---
# <a name="transport-of-webhttpbinding"></a><span data-ttu-id="65257-102">\<Transport > elementu \<WebHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="65257-102">\<transport> of \<webHttpBinding></span></span>
<span data-ttu-id="65257-103">Definiuje ustawienia zabezpieczeń na poziomie transportu dla punktu końcowego usługi skonfigurowanego do odbierania żądań HTTP.</span><span class="sxs-lookup"><span data-stu-id="65257-103">Defines the transport-level security settings for a service endpoint configured to receive HTTP requests.</span></span>  
  
 <span data-ttu-id="65257-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="65257-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="65257-105">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="65257-105">\<bindings></span></span>  
<span data-ttu-id="65257-106">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="65257-106">\<webHttpBinding></span></span>  
<span data-ttu-id="65257-107">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="65257-107">\<binding></span></span>  
<span data-ttu-id="65257-108">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="65257-108">\<security></span></span>  
<span data-ttu-id="65257-109">\<transport></span><span class="sxs-lookup"><span data-stu-id="65257-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65257-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="65257-110">Syntax</span></span>  
  
```xml  
<webHttpBinding>
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
</webHttpBinding>
```  
  
## <a name="type"></a><span data-ttu-id="65257-111">Typ</span><span class="sxs-lookup"><span data-stu-id="65257-111">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="65257-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="65257-112">Attributes and Elements</span></span>  
 <span data-ttu-id="65257-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="65257-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="65257-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="65257-114">Attributes</span></span>  
  
|<span data-ttu-id="65257-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="65257-115">Attribute</span></span>|<span data-ttu-id="65257-116">Opis</span><span class="sxs-lookup"><span data-stu-id="65257-116">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="65257-117">Określa poświadczenie używane do uwierzytelniania klienta w usłudze.</span><span class="sxs-lookup"><span data-stu-id="65257-117">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="65257-118">Ten atrybut jest typu <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="65257-118">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="65257-119">Określa poświadczenie używane do uwierzytelniania klienta programu na serwerze proxy domeny.</span><span class="sxs-lookup"><span data-stu-id="65257-119">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="65257-120">Ten atrybut jest typu <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="65257-120">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="65257-121">Ciąg określający obszar uwierzytelniania dla uwierzytelniania szyfrowanego lub podstawowego.</span><span class="sxs-lookup"><span data-stu-id="65257-121">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="65257-122">Wartość domyślna to pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="65257-122">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="65257-123">Obszar uwierzytelniania określa co najmniej nazwę hosta, który wykonuje uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="65257-123">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="65257-124">Można również określić kolekcję użytkowników, którzy mają dostęp.</span><span class="sxs-lookup"><span data-stu-id="65257-124">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="65257-125">Użytkownik może wysyłać zapytania do obszaru uwierzytelniania, aby upewnić się, że można użyć jednej z kilku nazw użytkowników i haseł.</span><span class="sxs-lookup"><span data-stu-id="65257-125">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|  
|`policyEnforcement`|<span data-ttu-id="65257-126">To Wyliczenie określa, <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> Kiedy należy wymusić.</span><span class="sxs-lookup"><span data-stu-id="65257-126">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="65257-127">1.  Nigdy — zasady nigdy nie są wymuszane (ochrona rozszerzona jest wyłączona).</span><span class="sxs-lookup"><span data-stu-id="65257-127">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="65257-128">2.  WhenSupported — zasady są wymuszane tylko wtedy, gdy klient obsługuje ochronę rozszerzoną.</span><span class="sxs-lookup"><span data-stu-id="65257-128">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="65257-129">3.  Zawsze — zasady są zawsze wymuszane.</span><span class="sxs-lookup"><span data-stu-id="65257-129">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="65257-130">Klienci, którzy nie obsługują rozszerzonej ochrony, nie będą uwierzytelniani.</span><span class="sxs-lookup"><span data-stu-id="65257-130">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="65257-131">clientCredentialtype — atrybut</span><span class="sxs-lookup"><span data-stu-id="65257-131">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="65257-132">Wartość</span><span class="sxs-lookup"><span data-stu-id="65257-132">Value</span></span>|<span data-ttu-id="65257-133">Opis</span><span class="sxs-lookup"><span data-stu-id="65257-133">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="65257-134">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="65257-134">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="65257-135">Używa uwierzytelniania podstawowego.</span><span class="sxs-lookup"><span data-stu-id="65257-135">Uses basic authentication.</span></span>|  
|`Certificate`|<span data-ttu-id="65257-136">Uwierzytelnia klienta za pomocą certyfikatów X. 509.</span><span class="sxs-lookup"><span data-stu-id="65257-136">Uses X.509 certificates to authenticate the client.</span></span>|  
|`Digest`|<span data-ttu-id="65257-137">Używa uwierzytelniania szyfrowanego.</span><span class="sxs-lookup"><span data-stu-id="65257-137">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="65257-138">Używa uwierzytelniania NTLM jako rezerwy z domeną systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="65257-138">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="65257-139">Używa zintegrowanego uwierzytelniania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="65257-139">Uses integrated Windows authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="65257-140">proxyCredentialType — atrybut</span><span class="sxs-lookup"><span data-stu-id="65257-140">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="65257-141">Wartość</span><span class="sxs-lookup"><span data-stu-id="65257-141">Value</span></span>|<span data-ttu-id="65257-142">Opis</span><span class="sxs-lookup"><span data-stu-id="65257-142">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="65257-143">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="65257-143">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="65257-144">Używa uwierzytelniania podstawowego.</span><span class="sxs-lookup"><span data-stu-id="65257-144">Uses basic authentication.</span></span>|  
|`Digest`|<span data-ttu-id="65257-145">Używa uwierzytelniania szyfrowanego.</span><span class="sxs-lookup"><span data-stu-id="65257-145">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="65257-146">Używa protokołu NTLM jako rezerwy z domeną systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="65257-146">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="65257-147">Używa zintegrowanego uwierzytelniania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="65257-147">Uses integrated Windows authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="65257-148">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="65257-148">Child Elements</span></span>  
 <span data-ttu-id="65257-149">Brak.</span><span class="sxs-lookup"><span data-stu-id="65257-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="65257-150">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="65257-150">Parent Elements</span></span>  
  
|<span data-ttu-id="65257-151">Element</span><span class="sxs-lookup"><span data-stu-id="65257-151">Element</span></span>|<span data-ttu-id="65257-152">Opis</span><span class="sxs-lookup"><span data-stu-id="65257-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="65257-153">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="65257-153">\<security></span></span>](security-of-webhttpbinding.md)|<span data-ttu-id="65257-154">Reprezentuje możliwości [ \<zabezpieczeń elementu > WSHttpBinding](wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="65257-154">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="65257-155">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="65257-155">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.WebHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WebHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [<span data-ttu-id="65257-156">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="65257-156">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="65257-157">Powiązania</span><span class="sxs-lookup"><span data-stu-id="65257-157">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="65257-158">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="65257-158">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="65257-159">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="65257-159">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="65257-160">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="65257-160">\<binding></span></span>](../../../misc/binding.md)
- [<span data-ttu-id="65257-161">Model programowania protokołu HTTP sieci Web w programie WCF</span><span class="sxs-lookup"><span data-stu-id="65257-161">WCF Web HTTP Programming Model</span></span>](../../../wcf/feature-details/wcf-web-http-programming-model.md)
