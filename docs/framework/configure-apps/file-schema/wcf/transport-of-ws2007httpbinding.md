---
title: <transport> dla <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 692befa3-8b0b-4ec5-b601-755874e98eb0
ms.openlocfilehash: ce8b2acb7d87b094958e20ca0b6cca9fc8266a8d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911988"
---
# <a name="transport-of-ws2007httpbinding"></a><span data-ttu-id="a41aa-102">\<Transport > \<WS2007HttpBinding ></span><span class="sxs-lookup"><span data-stu-id="a41aa-102">\<transport> of \<ws2007HttpBinding></span></span>
<span data-ttu-id="a41aa-103">Definiuje ustawienia uwierzytelniania dla transportu HTTP.</span><span class="sxs-lookup"><span data-stu-id="a41aa-103">Defines authentication settings for the HTTP transport.</span></span>  
  
 <span data-ttu-id="a41aa-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a41aa-104">\<system.serviceModel></span></span>  
<span data-ttu-id="a41aa-105">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="a41aa-105">\<bindings></span></span>  
<span data-ttu-id="a41aa-106">\<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="a41aa-106">\<ws2007HttpBinding></span></span>  
<span data-ttu-id="a41aa-107">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="a41aa-107">\<binding></span></span>  
<span data-ttu-id="a41aa-108">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="a41aa-108">\<security></span></span>  
<span data-ttu-id="a41aa-109">\<transport></span><span class="sxs-lookup"><span data-stu-id="a41aa-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a41aa-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="a41aa-110">Syntax</span></span>  
  
```xml  
<transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
           proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
           realm="string" />
```  
  
## <a name="type"></a><span data-ttu-id="a41aa-111">Typ</span><span class="sxs-lookup"><span data-stu-id="a41aa-111">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a41aa-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a41aa-112">Attributes and Elements</span></span>  
 <span data-ttu-id="a41aa-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a41aa-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a41aa-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a41aa-114">Attributes</span></span>  
  
|<span data-ttu-id="a41aa-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a41aa-115">Attribute</span></span>|<span data-ttu-id="a41aa-116">Opis</span><span class="sxs-lookup"><span data-stu-id="a41aa-116">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="a41aa-117">Określa poświadczenie używane do uwierzytelniania klienta w usłudze.</span><span class="sxs-lookup"><span data-stu-id="a41aa-117">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="a41aa-118">Ten atrybut jest typu <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="a41aa-118">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="a41aa-119">Określa poświadczenie używane do uwierzytelniania klienta programu na serwerze proxy domeny.</span><span class="sxs-lookup"><span data-stu-id="a41aa-119">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="a41aa-120">Ten atrybut jest typu <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="a41aa-120">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="a41aa-121">Obszar uwierzytelniania dla uwierzytelniania szyfrowanego lub podstawowego.</span><span class="sxs-lookup"><span data-stu-id="a41aa-121">The authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="a41aa-122">Wartość domyślna to pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="a41aa-122">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="a41aa-123">Obszar uwierzytelniania określa co najmniej nazwę hosta, który wykonuje uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="a41aa-123">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="a41aa-124">Można również określić kolekcję użytkowników, którzy mają dostęp.</span><span class="sxs-lookup"><span data-stu-id="a41aa-124">It can also specify a collection of users who have access.</span></span> <span data-ttu-id="a41aa-125">Użytkownik może wysyłać zapytania do obszaru uwierzytelniania, aby określić, która z kilku możliwych nazw użytkowników i haseł może być używana.</span><span class="sxs-lookup"><span data-stu-id="a41aa-125">A user can query the authentication realm to determine which one of the several possible usernames and passwords can be used.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="a41aa-126">clientCredentialtype — atrybut</span><span class="sxs-lookup"><span data-stu-id="a41aa-126">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="a41aa-127">Wartość</span><span class="sxs-lookup"><span data-stu-id="a41aa-127">Value</span></span>|<span data-ttu-id="a41aa-128">Opis</span><span class="sxs-lookup"><span data-stu-id="a41aa-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a41aa-129">Brak</span><span class="sxs-lookup"><span data-stu-id="a41aa-129">None</span></span>|<span data-ttu-id="a41aa-130">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="a41aa-130">Security is disabled.</span></span>|  
|<span data-ttu-id="a41aa-131">Podstawowy</span><span class="sxs-lookup"><span data-stu-id="a41aa-131">Basic</span></span>|<span data-ttu-id="a41aa-132">Używa uwierzytelniania podstawowego.</span><span class="sxs-lookup"><span data-stu-id="a41aa-132">Uses basic authentication.</span></span>|  
|<span data-ttu-id="a41aa-133">Szyfrowane</span><span class="sxs-lookup"><span data-stu-id="a41aa-133">Digest</span></span>|<span data-ttu-id="a41aa-134">Używa uwierzytelniania szyfrowanego.</span><span class="sxs-lookup"><span data-stu-id="a41aa-134">Uses digest authentication.</span></span>|  
|<span data-ttu-id="a41aa-135">NTLM</span><span class="sxs-lookup"><span data-stu-id="a41aa-135">Ntlm</span></span>|<span data-ttu-id="a41aa-136">Używa uwierzytelniania NTLM jako rezerwy z domeną systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="a41aa-136">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="a41aa-137">Windows</span><span class="sxs-lookup"><span data-stu-id="a41aa-137">Windows</span></span>|<span data-ttu-id="a41aa-138">Używa zintegrowanego uwierzytelniania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="a41aa-138">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="a41aa-139">Certyfikatu</span><span class="sxs-lookup"><span data-stu-id="a41aa-139">Certificate</span></span>|<span data-ttu-id="a41aa-140">Uwierzytelnia klienta za pomocą certyfikatów X. 509.</span><span class="sxs-lookup"><span data-stu-id="a41aa-140">Uses X.509 certificates to authenticate the client.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="a41aa-141">proxyCredentialType — atrybut</span><span class="sxs-lookup"><span data-stu-id="a41aa-141">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="a41aa-142">Wartość</span><span class="sxs-lookup"><span data-stu-id="a41aa-142">Value</span></span>|<span data-ttu-id="a41aa-143">Opis</span><span class="sxs-lookup"><span data-stu-id="a41aa-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a41aa-144">Brak</span><span class="sxs-lookup"><span data-stu-id="a41aa-144">None</span></span>|<span data-ttu-id="a41aa-145">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="a41aa-145">Security is disabled.</span></span>|  
|<span data-ttu-id="a41aa-146">Podstawowy</span><span class="sxs-lookup"><span data-stu-id="a41aa-146">Basic</span></span>|<span data-ttu-id="a41aa-147">Używa uwierzytelniania podstawowego.</span><span class="sxs-lookup"><span data-stu-id="a41aa-147">Uses basic authentication.</span></span>|  
|<span data-ttu-id="a41aa-148">Szyfrowane</span><span class="sxs-lookup"><span data-stu-id="a41aa-148">Digest</span></span>|<span data-ttu-id="a41aa-149">Używa uwierzytelniania szyfrowanego.</span><span class="sxs-lookup"><span data-stu-id="a41aa-149">Uses digest authentication.</span></span>|  
|<span data-ttu-id="a41aa-150">NTLM</span><span class="sxs-lookup"><span data-stu-id="a41aa-150">Ntlm</span></span>|<span data-ttu-id="a41aa-151">Używa protokołu NTLM jako rezerwy z domeną systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="a41aa-151">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="a41aa-152">Windows</span><span class="sxs-lookup"><span data-stu-id="a41aa-152">Windows</span></span>|<span data-ttu-id="a41aa-153">Używa zintegrowanego uwierzytelniania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="a41aa-153">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="a41aa-154">Certyfikatu</span><span class="sxs-lookup"><span data-stu-id="a41aa-154">Certificate</span></span>|<span data-ttu-id="a41aa-155">Uwierzytelnia klienta za pomocą certyfikatów X. 509.</span><span class="sxs-lookup"><span data-stu-id="a41aa-155">Uses X.509 certificates to authenticate the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a41aa-156">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a41aa-156">Child Elements</span></span>  
 <span data-ttu-id="a41aa-157">Brak</span><span class="sxs-lookup"><span data-stu-id="a41aa-157">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a41aa-158">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a41aa-158">Parent Elements</span></span>  
  
|<span data-ttu-id="a41aa-159">Element</span><span class="sxs-lookup"><span data-stu-id="a41aa-159">Element</span></span>|<span data-ttu-id="a41aa-160">Opis</span><span class="sxs-lookup"><span data-stu-id="a41aa-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a41aa-161">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="a41aa-161">\<security></span></span>](security-of-ws2007httpbinding.md)|<span data-ttu-id="a41aa-162">Reprezentuje możliwości [ \<zabezpieczeń elementu > WS2007HttpBinding](ws2007httpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="a41aa-162">Represents the security capabilities of the [\<ws2007HttpBinding>](ws2007httpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a41aa-163">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a41aa-163">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpTransportSecurityElement>
- [<span data-ttu-id="a41aa-164">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="a41aa-164">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="a41aa-165">Powiązania</span><span class="sxs-lookup"><span data-stu-id="a41aa-165">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="a41aa-166">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="a41aa-166">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="a41aa-167">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="a41aa-167">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="a41aa-168">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="a41aa-168">\<binding></span></span>](../../../misc/binding.md)
