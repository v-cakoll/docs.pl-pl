---
title: <transport> dla <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 692befa3-8b0b-4ec5-b601-755874e98eb0
ms.openlocfilehash: 4ea60ccaba58bc0b3fa8f2263295bf1413d25e89
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399266"
---
# <a name="transport-of-ws2007httpbinding"></a><span data-ttu-id="933ef-102">\<Transport > \<WS2007HttpBinding ></span><span class="sxs-lookup"><span data-stu-id="933ef-102">\<transport> of \<ws2007HttpBinding></span></span>
<span data-ttu-id="933ef-103">Definiuje ustawienia uwierzytelniania dla transportu HTTP.</span><span class="sxs-lookup"><span data-stu-id="933ef-103">Defines authentication settings for the HTTP transport.</span></span>  
  
<span data-ttu-id="933ef-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="933ef-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="933ef-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="933ef-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="933ef-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> powiązań**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="933ef-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="933ef-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<ws2007HttpBinding >** ](ws2007httpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="933ef-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007HttpBinding>**](ws2007httpbinding.md)</span></span>\
<span data-ttu-id="933ef-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> powiązania**</span><span class="sxs-lookup"><span data-stu-id="933ef-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="933ef-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zabezpieczeń**](security-of-ws2007httpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="933ef-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-ws2007httpbinding.md)</span></span>\
<span data-ttu-id="933ef-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> transportu**</span><span class="sxs-lookup"><span data-stu-id="933ef-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="933ef-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="933ef-111">Syntax</span></span>  
  
```xml  
<transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
           proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
           realm="string" />
```  
  
## <a name="type"></a><span data-ttu-id="933ef-112">Typ</span><span class="sxs-lookup"><span data-stu-id="933ef-112">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="933ef-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="933ef-113">Attributes and Elements</span></span>  
 <span data-ttu-id="933ef-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="933ef-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="933ef-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="933ef-115">Attributes</span></span>  
  
|<span data-ttu-id="933ef-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="933ef-116">Attribute</span></span>|<span data-ttu-id="933ef-117">Opis</span><span class="sxs-lookup"><span data-stu-id="933ef-117">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="933ef-118">Określa poświadczenie używane do uwierzytelniania klienta w usłudze.</span><span class="sxs-lookup"><span data-stu-id="933ef-118">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="933ef-119">Ten atrybut jest typu <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="933ef-119">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="933ef-120">Określa poświadczenie używane do uwierzytelniania klienta programu na serwerze proxy domeny.</span><span class="sxs-lookup"><span data-stu-id="933ef-120">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="933ef-121">Ten atrybut jest typu <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="933ef-121">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="933ef-122">Obszar uwierzytelniania dla uwierzytelniania szyfrowanego lub podstawowego.</span><span class="sxs-lookup"><span data-stu-id="933ef-122">The authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="933ef-123">Wartość domyślna to pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="933ef-123">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="933ef-124">Obszar uwierzytelniania określa co najmniej nazwę hosta, który wykonuje uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="933ef-124">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="933ef-125">Można również określić kolekcję użytkowników, którzy mają dostęp.</span><span class="sxs-lookup"><span data-stu-id="933ef-125">It can also specify a collection of users who have access.</span></span> <span data-ttu-id="933ef-126">Użytkownik może wysyłać zapytania do obszaru uwierzytelniania, aby określić, która z kilku możliwych nazw użytkowników i haseł może być używana.</span><span class="sxs-lookup"><span data-stu-id="933ef-126">A user can query the authentication realm to determine which one of the several possible usernames and passwords can be used.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="933ef-127">clientCredentialtype — atrybut</span><span class="sxs-lookup"><span data-stu-id="933ef-127">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="933ef-128">Wartość</span><span class="sxs-lookup"><span data-stu-id="933ef-128">Value</span></span>|<span data-ttu-id="933ef-129">Opis</span><span class="sxs-lookup"><span data-stu-id="933ef-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="933ef-130">Brak</span><span class="sxs-lookup"><span data-stu-id="933ef-130">None</span></span>|<span data-ttu-id="933ef-131">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="933ef-131">Security is disabled.</span></span>|  
|<span data-ttu-id="933ef-132">Podstawowy</span><span class="sxs-lookup"><span data-stu-id="933ef-132">Basic</span></span>|<span data-ttu-id="933ef-133">Używa uwierzytelniania podstawowego.</span><span class="sxs-lookup"><span data-stu-id="933ef-133">Uses basic authentication.</span></span>|  
|<span data-ttu-id="933ef-134">Szyfrowane</span><span class="sxs-lookup"><span data-stu-id="933ef-134">Digest</span></span>|<span data-ttu-id="933ef-135">Używa uwierzytelniania szyfrowanego.</span><span class="sxs-lookup"><span data-stu-id="933ef-135">Uses digest authentication.</span></span>|  
|<span data-ttu-id="933ef-136">NTLM</span><span class="sxs-lookup"><span data-stu-id="933ef-136">Ntlm</span></span>|<span data-ttu-id="933ef-137">Używa uwierzytelniania NTLM jako rezerwy z domeną systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="933ef-137">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="933ef-138">Windows</span><span class="sxs-lookup"><span data-stu-id="933ef-138">Windows</span></span>|<span data-ttu-id="933ef-139">Używa zintegrowanego uwierzytelniania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="933ef-139">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="933ef-140">Certyfikatu</span><span class="sxs-lookup"><span data-stu-id="933ef-140">Certificate</span></span>|<span data-ttu-id="933ef-141">Uwierzytelnia klienta za pomocą certyfikatów X. 509.</span><span class="sxs-lookup"><span data-stu-id="933ef-141">Uses X.509 certificates to authenticate the client.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="933ef-142">proxyCredentialType — atrybut</span><span class="sxs-lookup"><span data-stu-id="933ef-142">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="933ef-143">Wartość</span><span class="sxs-lookup"><span data-stu-id="933ef-143">Value</span></span>|<span data-ttu-id="933ef-144">Opis</span><span class="sxs-lookup"><span data-stu-id="933ef-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="933ef-145">Brak</span><span class="sxs-lookup"><span data-stu-id="933ef-145">None</span></span>|<span data-ttu-id="933ef-146">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="933ef-146">Security is disabled.</span></span>|  
|<span data-ttu-id="933ef-147">Podstawowy</span><span class="sxs-lookup"><span data-stu-id="933ef-147">Basic</span></span>|<span data-ttu-id="933ef-148">Używa uwierzytelniania podstawowego.</span><span class="sxs-lookup"><span data-stu-id="933ef-148">Uses basic authentication.</span></span>|  
|<span data-ttu-id="933ef-149">Szyfrowane</span><span class="sxs-lookup"><span data-stu-id="933ef-149">Digest</span></span>|<span data-ttu-id="933ef-150">Używa uwierzytelniania szyfrowanego.</span><span class="sxs-lookup"><span data-stu-id="933ef-150">Uses digest authentication.</span></span>|  
|<span data-ttu-id="933ef-151">NTLM</span><span class="sxs-lookup"><span data-stu-id="933ef-151">Ntlm</span></span>|<span data-ttu-id="933ef-152">Używa protokołu NTLM jako rezerwy z domeną systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="933ef-152">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="933ef-153">Windows</span><span class="sxs-lookup"><span data-stu-id="933ef-153">Windows</span></span>|<span data-ttu-id="933ef-154">Używa zintegrowanego uwierzytelniania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="933ef-154">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="933ef-155">Certyfikatu</span><span class="sxs-lookup"><span data-stu-id="933ef-155">Certificate</span></span>|<span data-ttu-id="933ef-156">Uwierzytelnia klienta za pomocą certyfikatów X. 509.</span><span class="sxs-lookup"><span data-stu-id="933ef-156">Uses X.509 certificates to authenticate the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="933ef-157">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="933ef-157">Child Elements</span></span>  
 <span data-ttu-id="933ef-158">Brak</span><span class="sxs-lookup"><span data-stu-id="933ef-158">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="933ef-159">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="933ef-159">Parent Elements</span></span>  
  
|<span data-ttu-id="933ef-160">Element</span><span class="sxs-lookup"><span data-stu-id="933ef-160">Element</span></span>|<span data-ttu-id="933ef-161">Opis</span><span class="sxs-lookup"><span data-stu-id="933ef-161">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="933ef-162">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="933ef-162">\<security></span></span>](security-of-ws2007httpbinding.md)|<span data-ttu-id="933ef-163">Reprezentuje możliwości [ \<zabezpieczeń elementu > WS2007HttpBinding](ws2007httpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="933ef-163">Represents the security capabilities of the [\<ws2007HttpBinding>](ws2007httpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="933ef-164">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="933ef-164">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpTransportSecurityElement>
- [<span data-ttu-id="933ef-165">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="933ef-165">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="933ef-166">Powiązania</span><span class="sxs-lookup"><span data-stu-id="933ef-166">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="933ef-167">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="933ef-167">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="933ef-168">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="933ef-168">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="933ef-169">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="933ef-169">\<binding></span></span>](../../../misc/binding.md)
