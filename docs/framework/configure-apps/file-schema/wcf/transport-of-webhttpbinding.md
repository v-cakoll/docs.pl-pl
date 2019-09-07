---
title: <transport> dla <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: f150fb19-7de1-44af-81f4-86cad881cd05
ms.openlocfilehash: 98cdaa86441f91552c7133d8e5694f88019a6dbf
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399277"
---
# <a name="transport-of-webhttpbinding"></a><span data-ttu-id="699bb-102">\<Transport > elementu \<WebHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="699bb-102">\<transport> of \<webHttpBinding></span></span>
<span data-ttu-id="699bb-103">Definiuje ustawienia zabezpieczeń na poziomie transportu dla punktu końcowego usługi skonfigurowanego do odbierania żądań HTTP.</span><span class="sxs-lookup"><span data-stu-id="699bb-103">Defines the transport-level security settings for a service endpoint configured to receive HTTP requests.</span></span>  
  
<span data-ttu-id="699bb-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="699bb-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="699bb-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="699bb-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="699bb-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> powiązań**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="699bb-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="699bb-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> WebHttpBinding**](webhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="699bb-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<webHttpBinding>**](webhttpbinding.md)</span></span>\
<span data-ttu-id="699bb-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> powiązania**</span><span class="sxs-lookup"><span data-stu-id="699bb-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="699bb-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zabezpieczeń**](security-of-webhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="699bb-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-webhttpbinding.md)</span></span>\
<span data-ttu-id="699bb-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> transportu**</span><span class="sxs-lookup"><span data-stu-id="699bb-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="699bb-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="699bb-111">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="699bb-112">Typ</span><span class="sxs-lookup"><span data-stu-id="699bb-112">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="699bb-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="699bb-113">Attributes and Elements</span></span>  
 <span data-ttu-id="699bb-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="699bb-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="699bb-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="699bb-115">Attributes</span></span>  
  
|<span data-ttu-id="699bb-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="699bb-116">Attribute</span></span>|<span data-ttu-id="699bb-117">Opis</span><span class="sxs-lookup"><span data-stu-id="699bb-117">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="699bb-118">Określa poświadczenie używane do uwierzytelniania klienta w usłudze.</span><span class="sxs-lookup"><span data-stu-id="699bb-118">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="699bb-119">Ten atrybut jest typu <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="699bb-119">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="699bb-120">Określa poświadczenie używane do uwierzytelniania klienta programu na serwerze proxy domeny.</span><span class="sxs-lookup"><span data-stu-id="699bb-120">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="699bb-121">Ten atrybut jest typu <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="699bb-121">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="699bb-122">Ciąg określający obszar uwierzytelniania dla uwierzytelniania szyfrowanego lub podstawowego.</span><span class="sxs-lookup"><span data-stu-id="699bb-122">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="699bb-123">Wartość domyślna to pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="699bb-123">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="699bb-124">Obszar uwierzytelniania określa co najmniej nazwę hosta, który wykonuje uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="699bb-124">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="699bb-125">Można również określić kolekcję użytkowników, którzy mają dostęp.</span><span class="sxs-lookup"><span data-stu-id="699bb-125">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="699bb-126">Użytkownik może wysyłać zapytania do obszaru uwierzytelniania, aby upewnić się, że można użyć jednej z kilku nazw użytkowników i haseł.</span><span class="sxs-lookup"><span data-stu-id="699bb-126">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|  
|`policyEnforcement`|<span data-ttu-id="699bb-127">To Wyliczenie określa, <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> Kiedy należy wymusić.</span><span class="sxs-lookup"><span data-stu-id="699bb-127">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="699bb-128">1.  Nigdy — zasady nigdy nie są wymuszane (ochrona rozszerzona jest wyłączona).</span><span class="sxs-lookup"><span data-stu-id="699bb-128">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="699bb-129">2.  WhenSupported — zasady są wymuszane tylko wtedy, gdy klient obsługuje ochronę rozszerzoną.</span><span class="sxs-lookup"><span data-stu-id="699bb-129">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="699bb-130">3.  Zawsze — zasady są zawsze wymuszane.</span><span class="sxs-lookup"><span data-stu-id="699bb-130">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="699bb-131">Klienci, którzy nie obsługują rozszerzonej ochrony, nie będą uwierzytelniani.</span><span class="sxs-lookup"><span data-stu-id="699bb-131">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="699bb-132">clientCredentialtype — atrybut</span><span class="sxs-lookup"><span data-stu-id="699bb-132">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="699bb-133">Wartość</span><span class="sxs-lookup"><span data-stu-id="699bb-133">Value</span></span>|<span data-ttu-id="699bb-134">Opis</span><span class="sxs-lookup"><span data-stu-id="699bb-134">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="699bb-135">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="699bb-135">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="699bb-136">Używa uwierzytelniania podstawowego.</span><span class="sxs-lookup"><span data-stu-id="699bb-136">Uses basic authentication.</span></span>|  
|`Certificate`|<span data-ttu-id="699bb-137">Uwierzytelnia klienta za pomocą certyfikatów X. 509.</span><span class="sxs-lookup"><span data-stu-id="699bb-137">Uses X.509 certificates to authenticate the client.</span></span>|  
|`Digest`|<span data-ttu-id="699bb-138">Używa uwierzytelniania szyfrowanego.</span><span class="sxs-lookup"><span data-stu-id="699bb-138">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="699bb-139">Używa uwierzytelniania NTLM jako rezerwy z domeną systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="699bb-139">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="699bb-140">Używa zintegrowanego uwierzytelniania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="699bb-140">Uses integrated Windows authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="699bb-141">proxyCredentialType — atrybut</span><span class="sxs-lookup"><span data-stu-id="699bb-141">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="699bb-142">Wartość</span><span class="sxs-lookup"><span data-stu-id="699bb-142">Value</span></span>|<span data-ttu-id="699bb-143">Opis</span><span class="sxs-lookup"><span data-stu-id="699bb-143">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="699bb-144">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="699bb-144">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="699bb-145">Używa uwierzytelniania podstawowego.</span><span class="sxs-lookup"><span data-stu-id="699bb-145">Uses basic authentication.</span></span>|  
|`Digest`|<span data-ttu-id="699bb-146">Używa uwierzytelniania szyfrowanego.</span><span class="sxs-lookup"><span data-stu-id="699bb-146">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="699bb-147">Używa protokołu NTLM jako rezerwy z domeną systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="699bb-147">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="699bb-148">Używa zintegrowanego uwierzytelniania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="699bb-148">Uses integrated Windows authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="699bb-149">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="699bb-149">Child Elements</span></span>  
 <span data-ttu-id="699bb-150">Brak.</span><span class="sxs-lookup"><span data-stu-id="699bb-150">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="699bb-151">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="699bb-151">Parent Elements</span></span>  
  
|<span data-ttu-id="699bb-152">Element</span><span class="sxs-lookup"><span data-stu-id="699bb-152">Element</span></span>|<span data-ttu-id="699bb-153">Opis</span><span class="sxs-lookup"><span data-stu-id="699bb-153">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="699bb-154">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="699bb-154">\<security></span></span>](security-of-webhttpbinding.md)|<span data-ttu-id="699bb-155">Reprezentuje możliwości [ \<zabezpieczeń elementu > WSHttpBinding](wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="699bb-155">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="699bb-156">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="699bb-156">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.WebHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WebHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [<span data-ttu-id="699bb-157">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="699bb-157">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="699bb-158">Powiązania</span><span class="sxs-lookup"><span data-stu-id="699bb-158">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="699bb-159">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="699bb-159">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="699bb-160">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="699bb-160">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="699bb-161">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="699bb-161">\<binding></span></span>](../../../misc/binding.md)
- [<span data-ttu-id="699bb-162">Model programowania protokołu HTTP sieci Web w programie WCF</span><span class="sxs-lookup"><span data-stu-id="699bb-162">WCF Web HTTP Programming Model</span></span>](../../../wcf/feature-details/wcf-web-http-programming-model.md)
