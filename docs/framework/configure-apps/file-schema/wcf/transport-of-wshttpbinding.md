---
title: <transport> z <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 21e38acf-450a-4bda-82b6-de305e1f7cd8
ms.openlocfilehash: 1c25ffd70ae83f14d5e596b1ee32d05abcc95184
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55267680"
---
# <a name="transport-of-wshttpbinding"></a><span data-ttu-id="23ca0-102">\<transport > z \<wsHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="23ca0-102">\<transport> of \<wsHttpBinding></span></span>
<span data-ttu-id="23ca0-103">Definiuje ustawienia uwierzytelniania dla protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="23ca0-103">Defines authentication settings for the HTTP transport.</span></span>  
  
 <span data-ttu-id="23ca0-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="23ca0-104">\<system.serviceModel></span></span>  
<span data-ttu-id="23ca0-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="23ca0-105">\<bindings></span></span>  
<span data-ttu-id="23ca0-106">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="23ca0-106">\<wsHttpBinding></span></span>  
<span data-ttu-id="23ca0-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="23ca0-107">\<binding></span></span>  
<span data-ttu-id="23ca0-108">\<security></span><span class="sxs-lookup"><span data-stu-id="23ca0-108">\<security></span></span>  
<span data-ttu-id="23ca0-109">\<transport></span><span class="sxs-lookup"><span data-stu-id="23ca0-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23ca0-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="23ca0-110">Syntax</span></span>  
  
```xml  
<wsHttpBinding>
  <binding>
    <security mode="None|Transport|TransportWithMessageCredential|TransportCredentialOnly">
      <transport clientCredentialType="Basic|Certificate|Digest|None|Ntlm|Windows"
                 proxyCredentialType="Basic|Digest|None|Ntlm|Windows"
                 realm="string" />
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtecutionPolicy>
      </transport>
    </security>
  </binding>
</wsHttpBinding>
```  
  
## <a name="type"></a><span data-ttu-id="23ca0-111">Typ</span><span class="sxs-lookup"><span data-stu-id="23ca0-111">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="23ca0-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="23ca0-112">Attributes and Elements</span></span>  
 <span data-ttu-id="23ca0-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="23ca0-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="23ca0-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="23ca0-114">Attributes</span></span>  
  
|<span data-ttu-id="23ca0-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="23ca0-115">Attribute</span></span>|<span data-ttu-id="23ca0-116">Opis</span><span class="sxs-lookup"><span data-stu-id="23ca0-116">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="23ca0-117">Określa poświadczenia używane do uwierzytelniania klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="23ca0-117">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="23ca0-118">Ten atrybut jest typu <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="23ca0-118">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="23ca0-119">Określa poświadczenia używane do uwierzytelniania klienta do domeny serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="23ca0-119">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="23ca0-120">Ten atrybut jest typu <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="23ca0-120">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="23ca0-121">Ciąg, który określa obszar uwierzytelniania dla uwierzytelniania podstawowego lub szyfrowanego.</span><span class="sxs-lookup"><span data-stu-id="23ca0-121">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="23ca0-122">Wartość domyślna to ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="23ca0-122">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="23ca0-123">Obszar uwierzytelniania co najmniej Określa nazwę hosta, który przeprowadza uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="23ca0-123">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="23ca0-124">Można również określić zbiór użytkowników, które ma dostęp.</span><span class="sxs-lookup"><span data-stu-id="23ca0-124">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="23ca0-125">Użytkownika można badać obszaru uwierzytelniania, aby upewnić się, co kilka możliwych nazw użytkowników i haseł może służyć.</span><span class="sxs-lookup"><span data-stu-id="23ca0-125">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|  
|`policyEnforcement`|<span data-ttu-id="23ca0-126">To wyliczenie Określa, kiedy <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> powinny być wymuszane.</span><span class="sxs-lookup"><span data-stu-id="23ca0-126">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="23ca0-127">1.  Nigdy nie — zasady nigdy nie są wymuszane (ochrony rozszerzonej jest wyłączone).</span><span class="sxs-lookup"><span data-stu-id="23ca0-127">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="23ca0-128">2.  WhenSupported — zasady są wymuszane tylko wtedy, gdy klient obsługuje ochrony rozszerzonej.</span><span class="sxs-lookup"><span data-stu-id="23ca0-128">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="23ca0-129">3.  Zawsze — zasady zawsze są wymuszane.</span><span class="sxs-lookup"><span data-stu-id="23ca0-129">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="23ca0-130">Klienci, którzy nie obsługują ochrony rozszerzonej zakończy się niepowodzeniem do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="23ca0-130">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="23ca0-131">właściwości ClientCredentialType o wartości atrybutu</span><span class="sxs-lookup"><span data-stu-id="23ca0-131">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="23ca0-132">Wartość</span><span class="sxs-lookup"><span data-stu-id="23ca0-132">Value</span></span>|<span data-ttu-id="23ca0-133">Opis</span><span class="sxs-lookup"><span data-stu-id="23ca0-133">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="23ca0-134">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="23ca0-134">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="23ca0-135">Korzysta z uwierzytelniania podstawowego.</span><span class="sxs-lookup"><span data-stu-id="23ca0-135">Uses basic authentication.</span></span>|  
|`Digest`|<span data-ttu-id="23ca0-136">Uwierzytelnianie szyfrowane używa.</span><span class="sxs-lookup"><span data-stu-id="23ca0-136">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="23ca0-137">Korzysta z uwierzytelniania NTLM, jako rezerwowe z domeną systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="23ca0-137">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="23ca0-138">Używa zintegrowanego uwierzytelniania Windows.</span><span class="sxs-lookup"><span data-stu-id="23ca0-138">Uses integrated Windows authentication.</span></span>|  
|`Certificate`|<span data-ttu-id="23ca0-139">Przy użyciu certyfikatów X.509 do uwierzytelniania klienta.</span><span class="sxs-lookup"><span data-stu-id="23ca0-139">Uses X.509 certificates to authenticate the client.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="23ca0-140">proxyCredentialType atrybutu</span><span class="sxs-lookup"><span data-stu-id="23ca0-140">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="23ca0-141">Wartość</span><span class="sxs-lookup"><span data-stu-id="23ca0-141">Value</span></span>|<span data-ttu-id="23ca0-142">Opis</span><span class="sxs-lookup"><span data-stu-id="23ca0-142">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="23ca0-143">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="23ca0-143">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="23ca0-144">Korzysta z uwierzytelniania podstawowego.</span><span class="sxs-lookup"><span data-stu-id="23ca0-144">Uses basic authentication.</span></span>|  
|`Digest`|<span data-ttu-id="23ca0-145">Uwierzytelnianie szyfrowane używa.</span><span class="sxs-lookup"><span data-stu-id="23ca0-145">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="23ca0-146">Wykorzystuje NTLM jako rezerwowe z domeną systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="23ca0-146">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="23ca0-147">Używa zintegrowanego uwierzytelniania Windows.</span><span class="sxs-lookup"><span data-stu-id="23ca0-147">Uses integrated Windows authentication.</span></span>|  
|`Certificate`|<span data-ttu-id="23ca0-148">Przy użyciu certyfikatów X.509 do uwierzytelniania klienta.</span><span class="sxs-lookup"><span data-stu-id="23ca0-148">Uses X.509 certificates to authenticate the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="23ca0-149">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="23ca0-149">Child Elements</span></span>  
 <span data-ttu-id="23ca0-150">Brak.</span><span class="sxs-lookup"><span data-stu-id="23ca0-150">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="23ca0-151">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="23ca0-151">Parent Elements</span></span>  
  
|<span data-ttu-id="23ca0-152">Element</span><span class="sxs-lookup"><span data-stu-id="23ca0-152">Element</span></span>|<span data-ttu-id="23ca0-153">Opis</span><span class="sxs-lookup"><span data-stu-id="23ca0-153">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="23ca0-154">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="23ca0-154">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)|<span data-ttu-id="23ca0-155">Reprezentuje możliwości zabezpieczeń [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="23ca0-155">Represents the security capabilities of the [\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="23ca0-156">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="23ca0-156">See also</span></span>
- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [<span data-ttu-id="23ca0-157">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="23ca0-157">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="23ca0-158">Powiązania</span><span class="sxs-lookup"><span data-stu-id="23ca0-158">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="23ca0-159">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="23ca0-159">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="23ca0-160">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="23ca0-160">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="23ca0-161">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="23ca0-161">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
