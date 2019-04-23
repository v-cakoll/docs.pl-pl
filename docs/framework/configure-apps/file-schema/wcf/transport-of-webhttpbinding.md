---
title: <transport> dla <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: f150fb19-7de1-44af-81f4-86cad881cd05
ms.openlocfilehash: 8dcd51cd248dbba3ccf60295cb1712167684328e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59116285"
---
# <a name="transport-of-webhttpbinding"></a><span data-ttu-id="f4051-102">\<transport > z \<webHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="f4051-102">\<transport> of \<webHttpBinding></span></span>
<span data-ttu-id="f4051-103">Określa ustawienia zabezpieczenia na poziomie transportu dla punktu końcowego skonfigurowanego do odbierania żądań HTTP.</span><span class="sxs-lookup"><span data-stu-id="f4051-103">Defines the transport-level security settings for a service endpoint configured to receive HTTP requests.</span></span>  
  
 <span data-ttu-id="f4051-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f4051-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f4051-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="f4051-105">\<bindings></span></span>  
<span data-ttu-id="f4051-106">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="f4051-106">\<webHttpBinding></span></span>  
<span data-ttu-id="f4051-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="f4051-107">\<binding></span></span>  
<span data-ttu-id="f4051-108">\<security></span><span class="sxs-lookup"><span data-stu-id="f4051-108">\<security></span></span>  
<span data-ttu-id="f4051-109">\<transport></span><span class="sxs-lookup"><span data-stu-id="f4051-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4051-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="f4051-110">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="f4051-111">Typ</span><span class="sxs-lookup"><span data-stu-id="f4051-111">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f4051-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f4051-112">Attributes and Elements</span></span>  
 <span data-ttu-id="f4051-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f4051-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f4051-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f4051-114">Attributes</span></span>  
  
|<span data-ttu-id="f4051-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f4051-115">Attribute</span></span>|<span data-ttu-id="f4051-116">Opis</span><span class="sxs-lookup"><span data-stu-id="f4051-116">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="f4051-117">Określa poświadczenia używane do uwierzytelniania klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="f4051-117">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="f4051-118">Ten atrybut jest typu <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="f4051-118">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="f4051-119">Określa poświadczenia używane do uwierzytelniania klienta do domeny serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="f4051-119">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="f4051-120">Ten atrybut jest typu <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="f4051-120">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="f4051-121">Ciąg, który określa obszar uwierzytelniania dla uwierzytelniania podstawowego lub szyfrowanego.</span><span class="sxs-lookup"><span data-stu-id="f4051-121">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="f4051-122">Wartość domyślna to ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="f4051-122">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="f4051-123">Obszar uwierzytelniania co najmniej Określa nazwę hosta, który przeprowadza uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="f4051-123">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="f4051-124">Można również określić zbiór użytkowników, które ma dostęp.</span><span class="sxs-lookup"><span data-stu-id="f4051-124">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="f4051-125">Użytkownika można badać obszaru uwierzytelniania, aby upewnić się, co kilka możliwych nazw użytkowników i haseł może służyć.</span><span class="sxs-lookup"><span data-stu-id="f4051-125">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|  
|`policyEnforcement`|<span data-ttu-id="f4051-126">To wyliczenie Określa, kiedy <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> powinny być wymuszane.</span><span class="sxs-lookup"><span data-stu-id="f4051-126">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="f4051-127">1.  Nigdy nie — zasady nigdy nie są wymuszane (ochrony rozszerzonej jest wyłączone).</span><span class="sxs-lookup"><span data-stu-id="f4051-127">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="f4051-128">2.  WhenSupported — zasady są wymuszane tylko wtedy, gdy klient obsługuje ochrony rozszerzonej.</span><span class="sxs-lookup"><span data-stu-id="f4051-128">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="f4051-129">3.  Zawsze — zasady zawsze są wymuszane.</span><span class="sxs-lookup"><span data-stu-id="f4051-129">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="f4051-130">Klienci, którzy nie obsługują ochrony rozszerzonej zakończy się niepowodzeniem do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="f4051-130">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="f4051-131">właściwości ClientCredentialType o wartości atrybutu</span><span class="sxs-lookup"><span data-stu-id="f4051-131">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="f4051-132">Wartość</span><span class="sxs-lookup"><span data-stu-id="f4051-132">Value</span></span>|<span data-ttu-id="f4051-133">Opis</span><span class="sxs-lookup"><span data-stu-id="f4051-133">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="f4051-134">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="f4051-134">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="f4051-135">Korzysta z uwierzytelniania podstawowego.</span><span class="sxs-lookup"><span data-stu-id="f4051-135">Uses basic authentication.</span></span>|  
|`Certificate`|<span data-ttu-id="f4051-136">Przy użyciu certyfikatów X.509 do uwierzytelniania klienta.</span><span class="sxs-lookup"><span data-stu-id="f4051-136">Uses X.509 certificates to authenticate the client.</span></span>|  
|`Digest`|<span data-ttu-id="f4051-137">Uwierzytelnianie szyfrowane używa.</span><span class="sxs-lookup"><span data-stu-id="f4051-137">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="f4051-138">Korzysta z uwierzytelniania NTLM, jako rezerwowe z domeną systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="f4051-138">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="f4051-139">Używa zintegrowanego uwierzytelniania Windows.</span><span class="sxs-lookup"><span data-stu-id="f4051-139">Uses integrated Windows authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="f4051-140">proxyCredentialType atrybutu</span><span class="sxs-lookup"><span data-stu-id="f4051-140">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="f4051-141">Wartość</span><span class="sxs-lookup"><span data-stu-id="f4051-141">Value</span></span>|<span data-ttu-id="f4051-142">Opis</span><span class="sxs-lookup"><span data-stu-id="f4051-142">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="f4051-143">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="f4051-143">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="f4051-144">Korzysta z uwierzytelniania podstawowego.</span><span class="sxs-lookup"><span data-stu-id="f4051-144">Uses basic authentication.</span></span>|  
|`Digest`|<span data-ttu-id="f4051-145">Uwierzytelnianie szyfrowane używa.</span><span class="sxs-lookup"><span data-stu-id="f4051-145">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="f4051-146">Wykorzystuje NTLM jako rezerwowe z domeną systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="f4051-146">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="f4051-147">Używa zintegrowanego uwierzytelniania Windows.</span><span class="sxs-lookup"><span data-stu-id="f4051-147">Uses integrated Windows authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f4051-148">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f4051-148">Child Elements</span></span>  
 <span data-ttu-id="f4051-149">Brak.</span><span class="sxs-lookup"><span data-stu-id="f4051-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f4051-150">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f4051-150">Parent Elements</span></span>  
  
|<span data-ttu-id="f4051-151">Element</span><span class="sxs-lookup"><span data-stu-id="f4051-151">Element</span></span>|<span data-ttu-id="f4051-152">Opis</span><span class="sxs-lookup"><span data-stu-id="f4051-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f4051-153">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="f4051-153">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-webhttpbinding.md)|<span data-ttu-id="f4051-154">Reprezentuje możliwości zabezpieczeń [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="f4051-154">Represents the security capabilities of the [\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f4051-155">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f4051-155">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.WebHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WebHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [<span data-ttu-id="f4051-156">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="f4051-156">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="f4051-157">Powiązania</span><span class="sxs-lookup"><span data-stu-id="f4051-157">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="f4051-158">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="f4051-158">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="f4051-159">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="f4051-159">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="f4051-160">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="f4051-160">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
- [<span data-ttu-id="f4051-161">Model programowania protokołu HTTP sieci Web w programie WCF</span><span class="sxs-lookup"><span data-stu-id="f4051-161">WCF Web HTTP Programming Model</span></span>](../../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
