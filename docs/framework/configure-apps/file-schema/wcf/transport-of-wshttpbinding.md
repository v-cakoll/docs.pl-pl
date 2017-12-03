---
title: '&lt;transport&gt; w &lt;wsHttpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21e38acf-450a-4bda-82b6-de305e1f7cd8
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e1ea5fc60f4dc64fd895469b580b81379da26191
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="lttransportgt-of-ltwshttpbindinggt"></a><span data-ttu-id="24165-102">&lt;transport&gt; w &lt;wsHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="24165-102">&lt;transport&gt; of &lt;wsHttpBinding&gt;</span></span>
<span data-ttu-id="24165-103">Definiuje ustawienia uwierzytelniania dla transportu HTTP.</span><span class="sxs-lookup"><span data-stu-id="24165-103">Defines authentication settings for the HTTP transport.</span></span>  
  
 <span data-ttu-id="24165-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="24165-104">\<system.serviceModel></span></span>  
<span data-ttu-id="24165-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="24165-105">\<bindings></span></span>  
<span data-ttu-id="24165-106">\<wsHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="24165-106">\<wsHttpBinding></span></span>  
<span data-ttu-id="24165-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="24165-107">\<binding></span></span>  
<span data-ttu-id="24165-108">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="24165-108">\<security></span></span>  
<span data-ttu-id="24165-109">\<transport ></span><span class="sxs-lookup"><span data-stu-id="24165-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24165-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="24165-110">Syntax</span></span>  
  
```xml  
<wsHttpBinding>  
    <binding>  
        <security mode="None|Transport|TransportWithMessageCredential|TransportCredentialOnly">  
            <transport  
            clientCredentialType="Basic|Certificate|Digest|None|Ntlm|Windows"  
            proxyCredentialType="Basic|Digest|None|Ntlm|Windows"  
            realm="string" />  
                <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always" protectionScenario="TransportSelected|TrustedProxy">  
                    <customServiceNames></customServiceNames>  
                </extendedProtecutionPolicy>  
            </transport>  
        </security>  
    </binding>  
</wsHttpBinding>  
```  
  
## <a name="type"></a><span data-ttu-id="24165-111">Typ</span><span class="sxs-lookup"><span data-stu-id="24165-111">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="24165-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="24165-112">Attributes and Elements</span></span>  
 <span data-ttu-id="24165-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="24165-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="24165-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="24165-114">Attributes</span></span>  
  
|<span data-ttu-id="24165-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="24165-115">Attribute</span></span>|<span data-ttu-id="24165-116">Opis</span><span class="sxs-lookup"><span data-stu-id="24165-116">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="24165-117">Określa poświadczenia używane do uwierzytelniania klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="24165-117">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="24165-118">Ten atrybut jest typu <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="24165-118">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="24165-119">Określa poświadczenia używane do uwierzytelniania klienta na serwerze proxy domeny.</span><span class="sxs-lookup"><span data-stu-id="24165-119">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="24165-120">Ten atrybut jest typu <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="24165-120">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="24165-121">Ciąg określający obszar uwierzytelniania dla uwierzytelniania podstawowego lub szyfrowanego.</span><span class="sxs-lookup"><span data-stu-id="24165-121">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="24165-122">Wartość domyślna to ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="24165-122">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="24165-123">Obszar uwierzytelniania określa co najmniej nazwę hosta, który przeprowadza uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="24165-123">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="24165-124">Można również określić zbiór użytkowników, które ma dostęp.</span><span class="sxs-lookup"><span data-stu-id="24165-124">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="24165-125">Użytkownik może zapytania obszaru uwierzytelniania, aby upewnić się, co kilka możliwych nazwy użytkownika i hasła może służyć.</span><span class="sxs-lookup"><span data-stu-id="24165-125">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|  
|`policyEnforcement`|<span data-ttu-id="24165-126">To wyliczenie Określa, kiedy <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> powinny być wymuszane.</span><span class="sxs-lookup"><span data-stu-id="24165-126">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="24165-127">1.  Nigdy nie — zasady nigdy nie są wymuszane (ochrona rozszerzona jest wyłączona).</span><span class="sxs-lookup"><span data-stu-id="24165-127">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="24165-128">2.  WhenSupported — zasady są wymuszane tylko wtedy, gdy klient obsługuje ochrony rozszerzonej.</span><span class="sxs-lookup"><span data-stu-id="24165-128">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="24165-129">3.  Zawsze — zasady zawsze są wymuszane.</span><span class="sxs-lookup"><span data-stu-id="24165-129">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="24165-130">Klienci, którzy nie obsługują ochrony rozszerzonej będzie mogło uwierzytelnić.</span><span class="sxs-lookup"><span data-stu-id="24165-130">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="24165-131">właściwości ClientCredentialType o wartości atrybutu</span><span class="sxs-lookup"><span data-stu-id="24165-131">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="24165-132">Wartość</span><span class="sxs-lookup"><span data-stu-id="24165-132">Value</span></span>|<span data-ttu-id="24165-133">Opis</span><span class="sxs-lookup"><span data-stu-id="24165-133">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="24165-134">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="24165-134">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="24165-135">Korzysta z uwierzytelniania podstawowego.</span><span class="sxs-lookup"><span data-stu-id="24165-135">Uses basic authentication.</span></span>|  
|`Digest`|<span data-ttu-id="24165-136">Uwierzytelnianie szyfrowane używa.</span><span class="sxs-lookup"><span data-stu-id="24165-136">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="24165-137">Korzysta z uwierzytelniania NTLM, jako rezerwowe z domeny systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="24165-137">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="24165-138">Używa zintegrowanego uwierzytelniania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="24165-138">Uses integrated Windows authentication.</span></span>|  
|`Certificate`|<span data-ttu-id="24165-139">Używa certyfikatów X.509 do uwierzytelniania klienta.</span><span class="sxs-lookup"><span data-stu-id="24165-139">Uses X.509 certificates to authenticate the client.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="24165-140">proxyCredentialType atrybutu</span><span class="sxs-lookup"><span data-stu-id="24165-140">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="24165-141">Wartość</span><span class="sxs-lookup"><span data-stu-id="24165-141">Value</span></span>|<span data-ttu-id="24165-142">Opis</span><span class="sxs-lookup"><span data-stu-id="24165-142">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="24165-143">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="24165-143">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="24165-144">Korzysta z uwierzytelniania podstawowego.</span><span class="sxs-lookup"><span data-stu-id="24165-144">Uses basic authentication.</span></span>|  
|`Digest`|<span data-ttu-id="24165-145">Uwierzytelnianie szyfrowane używa.</span><span class="sxs-lookup"><span data-stu-id="24165-145">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="24165-146">Używa protokołu NTLM jako rezerwowe z domeny systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="24165-146">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="24165-147">Używa zintegrowanego uwierzytelniania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="24165-147">Uses integrated Windows authentication.</span></span>|  
|`Certificate`|<span data-ttu-id="24165-148">Używa certyfikatów X.509 do uwierzytelniania klienta.</span><span class="sxs-lookup"><span data-stu-id="24165-148">Uses X.509 certificates to authenticate the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="24165-149">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="24165-149">Child Elements</span></span>  
 <span data-ttu-id="24165-150">Brak.</span><span class="sxs-lookup"><span data-stu-id="24165-150">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="24165-151">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="24165-151">Parent Elements</span></span>  
  
|<span data-ttu-id="24165-152">Element</span><span class="sxs-lookup"><span data-stu-id="24165-152">Element</span></span>|<span data-ttu-id="24165-153">Opis</span><span class="sxs-lookup"><span data-stu-id="24165-153">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="24165-154">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="24165-154">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)|<span data-ttu-id="24165-155">Reprezentuje możliwości zabezpieczeń [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="24165-155">Represents the security capabilities of the [\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="24165-156">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="24165-156">See Also</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>  
 [<span data-ttu-id="24165-157">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="24165-157">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="24165-158">Powiązania</span><span class="sxs-lookup"><span data-stu-id="24165-158">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="24165-159">Konfigurowanie powiązań dostarczanych przez System</span><span class="sxs-lookup"><span data-stu-id="24165-159">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="24165-160">Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="24165-160">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="24165-161">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="24165-161">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
