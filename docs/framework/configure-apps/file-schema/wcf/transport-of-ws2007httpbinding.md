---
title: <transport> dla <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 692befa3-8b0b-4ec5-b601-755874e98eb0
ms.openlocfilehash: 0cd20c607b0c4ddd3ecfd806d38ba63b4a5c5a25
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73732765"
---
# <a name="transport-of-ws2007httpbinding"></a><span data-ttu-id="e6ada-102">\<Transport > \<ws2007HttpBinding ></span><span class="sxs-lookup"><span data-stu-id="e6ada-102">\<transport> of \<ws2007HttpBinding></span></span>
<span data-ttu-id="e6ada-103">Definiuje ustawienia uwierzytelniania dla transportu HTTP.</span><span class="sxs-lookup"><span data-stu-id="e6ada-103">Defines authentication settings for the HTTP transport.</span></span>  
  
<span data-ttu-id="e6ada-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="e6ada-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e6ada-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="e6ada-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="e6ada-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<powiązań**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="e6ada-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="e6ada-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<WS2007HttpBinding**](ws2007httpbinding.md) ></span><span class="sxs-lookup"><span data-stu-id="e6ada-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007HttpBinding>**](ws2007httpbinding.md)</span></span>\
<span data-ttu-id="e6ada-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<powiązania >** </span><span class="sxs-lookup"><span data-stu-id="e6ada-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="e6ada-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<zabezpieczeń**](security-of-ws2007httpbinding.md) ></span><span class="sxs-lookup"><span data-stu-id="e6ada-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-ws2007httpbinding.md)</span></span>\
<span data-ttu-id="e6ada-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<transport >**</span><span class="sxs-lookup"><span data-stu-id="e6ada-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6ada-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="e6ada-111">Syntax</span></span>  
  
```xml  
<transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
           proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
           realm="string" />
```  
  
## <a name="type"></a><span data-ttu-id="e6ada-112">Typ</span><span class="sxs-lookup"><span data-stu-id="e6ada-112">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e6ada-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e6ada-113">Attributes and Elements</span></span>  
 <span data-ttu-id="e6ada-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e6ada-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e6ada-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e6ada-115">Attributes</span></span>  
  
|<span data-ttu-id="e6ada-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e6ada-116">Attribute</span></span>|<span data-ttu-id="e6ada-117">Opis</span><span class="sxs-lookup"><span data-stu-id="e6ada-117">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="e6ada-118">Określa poświadczenie używane do uwierzytelniania klienta w usłudze.</span><span class="sxs-lookup"><span data-stu-id="e6ada-118">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="e6ada-119">Ten atrybut jest typu <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="e6ada-119">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="e6ada-120">Określa poświadczenie używane do uwierzytelniania klienta programu na serwerze proxy domeny.</span><span class="sxs-lookup"><span data-stu-id="e6ada-120">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="e6ada-121">Ten atrybut jest typu <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="e6ada-121">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="e6ada-122">Obszar uwierzytelniania dla uwierzytelniania szyfrowanego lub podstawowego.</span><span class="sxs-lookup"><span data-stu-id="e6ada-122">The authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="e6ada-123">Wartość domyślna to pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="e6ada-123">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="e6ada-124">Obszar uwierzytelniania określa co najmniej nazwę hosta, który wykonuje uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="e6ada-124">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="e6ada-125">Można również określić kolekcję użytkowników, którzy mają dostęp.</span><span class="sxs-lookup"><span data-stu-id="e6ada-125">It can also specify a collection of users who have access.</span></span> <span data-ttu-id="e6ada-126">Użytkownik może wysyłać zapytania do obszaru uwierzytelniania, aby określić, która z kilku możliwych nazw użytkowników i haseł może być używana.</span><span class="sxs-lookup"><span data-stu-id="e6ada-126">A user can query the authentication realm to determine which one of the several possible usernames and passwords can be used.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="e6ada-127">clientCredentialtype — atrybut</span><span class="sxs-lookup"><span data-stu-id="e6ada-127">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="e6ada-128">Wartość</span><span class="sxs-lookup"><span data-stu-id="e6ada-128">Value</span></span>|<span data-ttu-id="e6ada-129">Opis</span><span class="sxs-lookup"><span data-stu-id="e6ada-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e6ada-130">Brak</span><span class="sxs-lookup"><span data-stu-id="e6ada-130">None</span></span>|<span data-ttu-id="e6ada-131">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="e6ada-131">Security is disabled.</span></span>|  
|<span data-ttu-id="e6ada-132">Podstawowy</span><span class="sxs-lookup"><span data-stu-id="e6ada-132">Basic</span></span>|<span data-ttu-id="e6ada-133">Używa uwierzytelniania podstawowego.</span><span class="sxs-lookup"><span data-stu-id="e6ada-133">Uses basic authentication.</span></span>|  
|<span data-ttu-id="e6ada-134">szyfrowane</span><span class="sxs-lookup"><span data-stu-id="e6ada-134">Digest</span></span>|<span data-ttu-id="e6ada-135">Używa uwierzytelniania szyfrowanego.</span><span class="sxs-lookup"><span data-stu-id="e6ada-135">Uses digest authentication.</span></span>|  
|<span data-ttu-id="e6ada-136">NTLM</span><span class="sxs-lookup"><span data-stu-id="e6ada-136">Ntlm</span></span>|<span data-ttu-id="e6ada-137">Używa uwierzytelniania NTLM jako rezerwy z domeną systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="e6ada-137">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="e6ada-138">Windows</span><span class="sxs-lookup"><span data-stu-id="e6ada-138">Windows</span></span>|<span data-ttu-id="e6ada-139">Używa zintegrowanego uwierzytelniania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="e6ada-139">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="e6ada-140">Certyfikatu</span><span class="sxs-lookup"><span data-stu-id="e6ada-140">Certificate</span></span>|<span data-ttu-id="e6ada-141">Uwierzytelnia klienta za pomocą certyfikatów X. 509.</span><span class="sxs-lookup"><span data-stu-id="e6ada-141">Uses X.509 certificates to authenticate the client.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="e6ada-142">proxyCredentialType — atrybut</span><span class="sxs-lookup"><span data-stu-id="e6ada-142">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="e6ada-143">Wartość</span><span class="sxs-lookup"><span data-stu-id="e6ada-143">Value</span></span>|<span data-ttu-id="e6ada-144">Opis</span><span class="sxs-lookup"><span data-stu-id="e6ada-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e6ada-145">Brak</span><span class="sxs-lookup"><span data-stu-id="e6ada-145">None</span></span>|<span data-ttu-id="e6ada-146">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="e6ada-146">Security is disabled.</span></span>|  
|<span data-ttu-id="e6ada-147">Podstawowy</span><span class="sxs-lookup"><span data-stu-id="e6ada-147">Basic</span></span>|<span data-ttu-id="e6ada-148">Używa uwierzytelniania podstawowego.</span><span class="sxs-lookup"><span data-stu-id="e6ada-148">Uses basic authentication.</span></span>|  
|<span data-ttu-id="e6ada-149">szyfrowane</span><span class="sxs-lookup"><span data-stu-id="e6ada-149">Digest</span></span>|<span data-ttu-id="e6ada-150">Używa uwierzytelniania szyfrowanego.</span><span class="sxs-lookup"><span data-stu-id="e6ada-150">Uses digest authentication.</span></span>|  
|<span data-ttu-id="e6ada-151">NTLM</span><span class="sxs-lookup"><span data-stu-id="e6ada-151">Ntlm</span></span>|<span data-ttu-id="e6ada-152">Używa protokołu NTLM jako rezerwy z domeną systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="e6ada-152">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="e6ada-153">Windows</span><span class="sxs-lookup"><span data-stu-id="e6ada-153">Windows</span></span>|<span data-ttu-id="e6ada-154">Używa zintegrowanego uwierzytelniania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="e6ada-154">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="e6ada-155">Certyfikatu</span><span class="sxs-lookup"><span data-stu-id="e6ada-155">Certificate</span></span>|<span data-ttu-id="e6ada-156">Uwierzytelnia klienta za pomocą certyfikatów X. 509.</span><span class="sxs-lookup"><span data-stu-id="e6ada-156">Uses X.509 certificates to authenticate the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e6ada-157">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e6ada-157">Child Elements</span></span>  
 <span data-ttu-id="e6ada-158">Brak</span><span class="sxs-lookup"><span data-stu-id="e6ada-158">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e6ada-159">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e6ada-159">Parent Elements</span></span>  
  
|<span data-ttu-id="e6ada-160">Element</span><span class="sxs-lookup"><span data-stu-id="e6ada-160">Element</span></span>|<span data-ttu-id="e6ada-161">Opis</span><span class="sxs-lookup"><span data-stu-id="e6ada-161">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e6ada-162">> zabezpieczeń \<</span><span class="sxs-lookup"><span data-stu-id="e6ada-162">\<security></span></span>](security-of-ws2007httpbinding.md)|<span data-ttu-id="e6ada-163">Reprezentuje możliwości zabezpieczeń [\<elementu > WS2007HttpBinding](ws2007httpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="e6ada-163">Represents the security capabilities of the [\<ws2007HttpBinding>](ws2007httpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e6ada-164">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e6ada-164">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpTransportSecurityElement>
- [<span data-ttu-id="e6ada-165">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="e6ada-165">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="e6ada-166">Powiązania</span><span class="sxs-lookup"><span data-stu-id="e6ada-166">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="e6ada-167">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="e6ada-167">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="e6ada-168">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="e6ada-168">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="e6ada-169">> powiązań \<</span><span class="sxs-lookup"><span data-stu-id="e6ada-169">\<binding></span></span>](bindings.md)
