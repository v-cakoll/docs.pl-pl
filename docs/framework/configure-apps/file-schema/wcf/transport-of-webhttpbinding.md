---
title: <transport> dla <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: f150fb19-7de1-44af-81f4-86cad881cd05
ms.openlocfilehash: e8016eb9058f132722587368f1f8c7c03220af4a
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73732789"
---
# <a name="transport-of-webhttpbinding"></a><span data-ttu-id="ff302-102">\<transportu > \<WebHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="ff302-102">\<transport> of \<webHttpBinding></span></span>
<span data-ttu-id="ff302-103">Definiuje ustawienia zabezpieczeń na poziomie transportu dla punktu końcowego usługi skonfigurowanego do odbierania żądań HTTP.</span><span class="sxs-lookup"><span data-stu-id="ff302-103">Defines the transport-level security settings for a service endpoint configured to receive HTTP requests.</span></span>  
  
<span data-ttu-id="ff302-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="ff302-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ff302-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="ff302-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="ff302-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<powiązań**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="ff302-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="ff302-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<WebHttpBinding**](webhttpbinding.md) ></span><span class="sxs-lookup"><span data-stu-id="ff302-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<webHttpBinding>**](webhttpbinding.md)</span></span>\
<span data-ttu-id="ff302-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<powiązania >** </span><span class="sxs-lookup"><span data-stu-id="ff302-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="ff302-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<zabezpieczeń**](security-of-webhttpbinding.md) ></span><span class="sxs-lookup"><span data-stu-id="ff302-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-webhttpbinding.md)</span></span>\
<span data-ttu-id="ff302-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<transport >**</span><span class="sxs-lookup"><span data-stu-id="ff302-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff302-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="ff302-111">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="ff302-112">Typ</span><span class="sxs-lookup"><span data-stu-id="ff302-112">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ff302-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ff302-113">Attributes and Elements</span></span>  
 <span data-ttu-id="ff302-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ff302-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ff302-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ff302-115">Attributes</span></span>  
  
|<span data-ttu-id="ff302-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ff302-116">Attribute</span></span>|<span data-ttu-id="ff302-117">Opis</span><span class="sxs-lookup"><span data-stu-id="ff302-117">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="ff302-118">Określa poświadczenie używane do uwierzytelniania klienta w usłudze.</span><span class="sxs-lookup"><span data-stu-id="ff302-118">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="ff302-119">Ten atrybut jest typu <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="ff302-119">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="ff302-120">Określa poświadczenie używane do uwierzytelniania klienta programu na serwerze proxy domeny.</span><span class="sxs-lookup"><span data-stu-id="ff302-120">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="ff302-121">Ten atrybut jest typu <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="ff302-121">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="ff302-122">Ciąg określający obszar uwierzytelniania dla uwierzytelniania szyfrowanego lub podstawowego.</span><span class="sxs-lookup"><span data-stu-id="ff302-122">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="ff302-123">Wartość domyślna to pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="ff302-123">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="ff302-124">Obszar uwierzytelniania określa co najmniej nazwę hosta, który wykonuje uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="ff302-124">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="ff302-125">Można również określić kolekcję użytkowników, którzy mają dostęp.</span><span class="sxs-lookup"><span data-stu-id="ff302-125">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="ff302-126">Użytkownik może wysyłać zapytania do obszaru uwierzytelniania, aby upewnić się, że można użyć jednej z kilku nazw użytkowników i haseł.</span><span class="sxs-lookup"><span data-stu-id="ff302-126">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|  
|`policyEnforcement`|<span data-ttu-id="ff302-127">To Wyliczenie określa, kiedy <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> należy wymusić.</span><span class="sxs-lookup"><span data-stu-id="ff302-127">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="ff302-128">1. nigdy — zasady nigdy nie są wymuszane (ochrona rozszerzona jest wyłączona).</span><span class="sxs-lookup"><span data-stu-id="ff302-128">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="ff302-129">2. WhenSupported — zasady są wymuszane tylko wtedy, gdy klient obsługuje ochronę rozszerzoną.</span><span class="sxs-lookup"><span data-stu-id="ff302-129">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="ff302-130">3. zawsze — zasady są zawsze wymuszane.</span><span class="sxs-lookup"><span data-stu-id="ff302-130">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="ff302-131">Klienci, którzy nie obsługują rozszerzonej ochrony, nie będą uwierzytelniani.</span><span class="sxs-lookup"><span data-stu-id="ff302-131">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="ff302-132">clientCredentialtype — atrybut</span><span class="sxs-lookup"><span data-stu-id="ff302-132">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="ff302-133">Wartość</span><span class="sxs-lookup"><span data-stu-id="ff302-133">Value</span></span>|<span data-ttu-id="ff302-134">Opis</span><span class="sxs-lookup"><span data-stu-id="ff302-134">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="ff302-135">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="ff302-135">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="ff302-136">Używa uwierzytelniania podstawowego.</span><span class="sxs-lookup"><span data-stu-id="ff302-136">Uses basic authentication.</span></span>|  
|`Certificate`|<span data-ttu-id="ff302-137">Uwierzytelnia klienta za pomocą certyfikatów X. 509.</span><span class="sxs-lookup"><span data-stu-id="ff302-137">Uses X.509 certificates to authenticate the client.</span></span>|  
|`Digest`|<span data-ttu-id="ff302-138">Używa uwierzytelniania szyfrowanego.</span><span class="sxs-lookup"><span data-stu-id="ff302-138">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="ff302-139">Używa uwierzytelniania NTLM jako rezerwy z domeną systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="ff302-139">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="ff302-140">Używa zintegrowanego uwierzytelniania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="ff302-140">Uses integrated Windows authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="ff302-141">proxyCredentialType — atrybut</span><span class="sxs-lookup"><span data-stu-id="ff302-141">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="ff302-142">Wartość</span><span class="sxs-lookup"><span data-stu-id="ff302-142">Value</span></span>|<span data-ttu-id="ff302-143">Opis</span><span class="sxs-lookup"><span data-stu-id="ff302-143">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="ff302-144">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="ff302-144">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="ff302-145">Używa uwierzytelniania podstawowego.</span><span class="sxs-lookup"><span data-stu-id="ff302-145">Uses basic authentication.</span></span>|  
|`Digest`|<span data-ttu-id="ff302-146">Używa uwierzytelniania szyfrowanego.</span><span class="sxs-lookup"><span data-stu-id="ff302-146">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="ff302-147">Używa protokołu NTLM jako rezerwy z domeną systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="ff302-147">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="ff302-148">Używa zintegrowanego uwierzytelniania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="ff302-148">Uses integrated Windows authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ff302-149">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ff302-149">Child Elements</span></span>  
 <span data-ttu-id="ff302-150">Brak.</span><span class="sxs-lookup"><span data-stu-id="ff302-150">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ff302-151">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ff302-151">Parent Elements</span></span>  
  
|<span data-ttu-id="ff302-152">Element</span><span class="sxs-lookup"><span data-stu-id="ff302-152">Element</span></span>|<span data-ttu-id="ff302-153">Opis</span><span class="sxs-lookup"><span data-stu-id="ff302-153">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ff302-154">> zabezpieczeń \<</span><span class="sxs-lookup"><span data-stu-id="ff302-154">\<security></span></span>](security-of-webhttpbinding.md)|<span data-ttu-id="ff302-155">Reprezentuje możliwości zabezpieczeń [\<elementu > WSHttpBinding](wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="ff302-155">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ff302-156">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ff302-156">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.WebHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WebHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [<span data-ttu-id="ff302-157">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="ff302-157">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="ff302-158">Powiązania</span><span class="sxs-lookup"><span data-stu-id="ff302-158">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="ff302-159">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="ff302-159">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="ff302-160">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="ff302-160">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="ff302-161">> powiązań \<</span><span class="sxs-lookup"><span data-stu-id="ff302-161">\<binding></span></span>](bindings.md)
- [<span data-ttu-id="ff302-162">Model programowania protokołu HTTP sieci Web w programie WCF</span><span class="sxs-lookup"><span data-stu-id="ff302-162">WCF Web HTTP Programming Model</span></span>](../../../wcf/feature-details/wcf-web-http-programming-model.md)
