---
title: <transport> dla <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: f150fb19-7de1-44af-81f4-86cad881cd05
ms.openlocfilehash: e8016eb9058f132722587368f1f8c7c03220af4a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73732789"
---
# <a name="transport-of-webhttpbinding"></a><span data-ttu-id="ddf8c-102">\<transport> dla \<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="ddf8c-102">\<transport> of \<webHttpBinding></span></span>
<span data-ttu-id="ddf8c-103">Definiuje ustawienia zabezpieczeń na poziomie transportu dla punktu końcowego usługi skonfigurowanego do odbierania żądań HTTP.</span><span class="sxs-lookup"><span data-stu-id="ddf8c-103">Defines the transport-level security settings for a service endpoint configured to receive HTTP requests.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<webHttpBinding>**](webhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-webhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="ddf8c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ddf8c-104">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="ddf8c-105">Typ</span><span class="sxs-lookup"><span data-stu-id="ddf8c-105">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ddf8c-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ddf8c-106">Attributes and Elements</span></span>  
 <span data-ttu-id="ddf8c-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ddf8c-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ddf8c-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ddf8c-108">Attributes</span></span>  
  
|<span data-ttu-id="ddf8c-109">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ddf8c-109">Attribute</span></span>|<span data-ttu-id="ddf8c-110">Opis</span><span class="sxs-lookup"><span data-stu-id="ddf8c-110">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="ddf8c-111">Określa poświadczenie używane do uwierzytelniania klienta w usłudze.</span><span class="sxs-lookup"><span data-stu-id="ddf8c-111">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="ddf8c-112">Ten atrybut jest typu <xref:System.ServiceModel.HttpClientCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="ddf8c-112">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="ddf8c-113">Określa poświadczenie używane do uwierzytelniania klienta programu na serwerze proxy domeny.</span><span class="sxs-lookup"><span data-stu-id="ddf8c-113">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="ddf8c-114">Ten atrybut jest typu <xref:System.ServiceModel.HttpProxyCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="ddf8c-114">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="ddf8c-115">Ciąg określający obszar uwierzytelniania dla uwierzytelniania szyfrowanego lub podstawowego.</span><span class="sxs-lookup"><span data-stu-id="ddf8c-115">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="ddf8c-116">Wartość domyślna to pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="ddf8c-116">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="ddf8c-117">Obszar uwierzytelniania określa co najmniej nazwę hosta, który wykonuje uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="ddf8c-117">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="ddf8c-118">Można również określić kolekcję użytkowników, którzy mają dostęp.</span><span class="sxs-lookup"><span data-stu-id="ddf8c-118">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="ddf8c-119">Użytkownik może wysyłać zapytania do obszaru uwierzytelniania, aby upewnić się, że można użyć jednej z kilku nazw użytkowników i haseł.</span><span class="sxs-lookup"><span data-stu-id="ddf8c-119">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|  
|`policyEnforcement`|<span data-ttu-id="ddf8c-120">To Wyliczenie określa, kiedy <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> należy wymusić.</span><span class="sxs-lookup"><span data-stu-id="ddf8c-120">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="ddf8c-121">1. nigdy — zasady nigdy nie są wymuszane (ochrona rozszerzona jest wyłączona).</span><span class="sxs-lookup"><span data-stu-id="ddf8c-121">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="ddf8c-122">2. WhenSupported — zasady są wymuszane tylko wtedy, gdy klient obsługuje ochronę rozszerzoną.</span><span class="sxs-lookup"><span data-stu-id="ddf8c-122">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="ddf8c-123">3. zawsze — zasady są zawsze wymuszane.</span><span class="sxs-lookup"><span data-stu-id="ddf8c-123">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="ddf8c-124">Klienci, którzy nie obsługują rozszerzonej ochrony, nie będą uwierzytelniani.</span><span class="sxs-lookup"><span data-stu-id="ddf8c-124">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="ddf8c-125">clientCredentialtype — atrybut</span><span class="sxs-lookup"><span data-stu-id="ddf8c-125">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="ddf8c-126">Wartość</span><span class="sxs-lookup"><span data-stu-id="ddf8c-126">Value</span></span>|<span data-ttu-id="ddf8c-127">Opis</span><span class="sxs-lookup"><span data-stu-id="ddf8c-127">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="ddf8c-128">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="ddf8c-128">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="ddf8c-129">Używa uwierzytelniania podstawowego.</span><span class="sxs-lookup"><span data-stu-id="ddf8c-129">Uses basic authentication.</span></span>|  
|`Certificate`|<span data-ttu-id="ddf8c-130">Uwierzytelnia klienta za pomocą certyfikatów X. 509.</span><span class="sxs-lookup"><span data-stu-id="ddf8c-130">Uses X.509 certificates to authenticate the client.</span></span>|  
|`Digest`|<span data-ttu-id="ddf8c-131">Używa uwierzytelniania szyfrowanego.</span><span class="sxs-lookup"><span data-stu-id="ddf8c-131">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="ddf8c-132">Używa uwierzytelniania NTLM jako rezerwy z domeną systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="ddf8c-132">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="ddf8c-133">Używa zintegrowanego uwierzytelniania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="ddf8c-133">Uses integrated Windows authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="ddf8c-134">proxyCredentialType — atrybut</span><span class="sxs-lookup"><span data-stu-id="ddf8c-134">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="ddf8c-135">Wartość</span><span class="sxs-lookup"><span data-stu-id="ddf8c-135">Value</span></span>|<span data-ttu-id="ddf8c-136">Opis</span><span class="sxs-lookup"><span data-stu-id="ddf8c-136">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="ddf8c-137">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="ddf8c-137">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="ddf8c-138">Używa uwierzytelniania podstawowego.</span><span class="sxs-lookup"><span data-stu-id="ddf8c-138">Uses basic authentication.</span></span>|  
|`Digest`|<span data-ttu-id="ddf8c-139">Używa uwierzytelniania szyfrowanego.</span><span class="sxs-lookup"><span data-stu-id="ddf8c-139">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="ddf8c-140">Używa protokołu NTLM jako rezerwy z domeną systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="ddf8c-140">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="ddf8c-141">Używa zintegrowanego uwierzytelniania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="ddf8c-141">Uses integrated Windows authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ddf8c-142">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ddf8c-142">Child Elements</span></span>  
 <span data-ttu-id="ddf8c-143">Brak.</span><span class="sxs-lookup"><span data-stu-id="ddf8c-143">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ddf8c-144">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ddf8c-144">Parent Elements</span></span>  
  
|<span data-ttu-id="ddf8c-145">Element</span><span class="sxs-lookup"><span data-stu-id="ddf8c-145">Element</span></span>|<span data-ttu-id="ddf8c-146">Opis</span><span class="sxs-lookup"><span data-stu-id="ddf8c-146">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-webhttpbinding.md)|<span data-ttu-id="ddf8c-147">Reprezentuje możliwości zabezpieczeń [\<wsHttpBinding>](wshttpbinding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="ddf8c-147">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ddf8c-148">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ddf8c-148">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.WebHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WebHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [<span data-ttu-id="ddf8c-149">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="ddf8c-149">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="ddf8c-150">Powiązania</span><span class="sxs-lookup"><span data-stu-id="ddf8c-150">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="ddf8c-151">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="ddf8c-151">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="ddf8c-152">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="ddf8c-152">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- [<span data-ttu-id="ddf8c-153">Model programowania protokołu HTTP sieci Web w programie WCF</span><span class="sxs-lookup"><span data-stu-id="ddf8c-153">WCF Web HTTP Programming Model</span></span>](../../../wcf/feature-details/wcf-web-http-programming-model.md)
