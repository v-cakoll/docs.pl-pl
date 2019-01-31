---
title: <transport> z <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 692befa3-8b0b-4ec5-b601-755874e98eb0
ms.openlocfilehash: b8f84d0ed6c6248e72e3353675c9da96a0678ae6
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55273309"
---
# <a name="transport-of-ws2007httpbinding"></a><span data-ttu-id="6505b-102">\<transport > z \<ws2007HttpBinding ></span><span class="sxs-lookup"><span data-stu-id="6505b-102">\<transport> of \<ws2007HttpBinding></span></span>
<span data-ttu-id="6505b-103">Definiuje ustawienia uwierzytelniania dla protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="6505b-103">Defines authentication settings for the HTTP transport.</span></span>  
  
 <span data-ttu-id="6505b-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="6505b-104">\<system.serviceModel></span></span>  
<span data-ttu-id="6505b-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="6505b-105">\<bindings></span></span>  
<span data-ttu-id="6505b-106">\<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="6505b-106">\<ws2007HttpBinding></span></span>  
<span data-ttu-id="6505b-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="6505b-107">\<binding></span></span>  
<span data-ttu-id="6505b-108">\<security></span><span class="sxs-lookup"><span data-stu-id="6505b-108">\<security></span></span>  
<span data-ttu-id="6505b-109">\<transport></span><span class="sxs-lookup"><span data-stu-id="6505b-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6505b-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="6505b-110">Syntax</span></span>  
  
```xml  
<transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
           proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
           realm="string" />
```  
  
## <a name="type"></a><span data-ttu-id="6505b-111">Typ</span><span class="sxs-lookup"><span data-stu-id="6505b-111">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6505b-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6505b-112">Attributes and Elements</span></span>  
 <span data-ttu-id="6505b-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6505b-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6505b-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6505b-114">Attributes</span></span>  
  
|<span data-ttu-id="6505b-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="6505b-115">Attribute</span></span>|<span data-ttu-id="6505b-116">Opis</span><span class="sxs-lookup"><span data-stu-id="6505b-116">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="6505b-117">Określa poświadczenia używane do uwierzytelniania klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="6505b-117">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="6505b-118">Ten atrybut jest typu <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="6505b-118">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="6505b-119">Określa poświadczenia używane do uwierzytelniania klienta do domeny serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="6505b-119">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="6505b-120">Ten atrybut jest typu <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="6505b-120">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="6505b-121">Obszar uwierzytelniania dla uwierzytelniania podstawowego lub szyfrowanego.</span><span class="sxs-lookup"><span data-stu-id="6505b-121">The authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="6505b-122">Wartość domyślna to ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="6505b-122">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="6505b-123">Obszar uwierzytelniania co najmniej Określa nazwę hosta, który przeprowadza uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="6505b-123">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="6505b-124">Można również określić zbiór użytkowników, którzy mają dostęp.</span><span class="sxs-lookup"><span data-stu-id="6505b-124">It can also specify a collection of users who have access.</span></span> <span data-ttu-id="6505b-125">Użytkownika można badać obszaru uwierzytelniania, aby określić jedną z kilku możliwych nazw użytkowników i haseł może służyć.</span><span class="sxs-lookup"><span data-stu-id="6505b-125">A user can query the authentication realm to determine which one of the several possible usernames and passwords can be used.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="6505b-126">właściwości ClientCredentialType o wartości atrybutu</span><span class="sxs-lookup"><span data-stu-id="6505b-126">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="6505b-127">Wartość</span><span class="sxs-lookup"><span data-stu-id="6505b-127">Value</span></span>|<span data-ttu-id="6505b-128">Opis</span><span class="sxs-lookup"><span data-stu-id="6505b-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6505b-129">Brak</span><span class="sxs-lookup"><span data-stu-id="6505b-129">None</span></span>|<span data-ttu-id="6505b-130">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="6505b-130">Security is disabled.</span></span>|  
|<span data-ttu-id="6505b-131">Podstawowy</span><span class="sxs-lookup"><span data-stu-id="6505b-131">Basic</span></span>|<span data-ttu-id="6505b-132">Korzysta z uwierzytelniania podstawowego.</span><span class="sxs-lookup"><span data-stu-id="6505b-132">Uses basic authentication.</span></span>|  
|<span data-ttu-id="6505b-133">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="6505b-133">Digest</span></span>|<span data-ttu-id="6505b-134">Uwierzytelnianie szyfrowane używa.</span><span class="sxs-lookup"><span data-stu-id="6505b-134">Uses digest authentication.</span></span>|  
|<span data-ttu-id="6505b-135">Ntlm</span><span class="sxs-lookup"><span data-stu-id="6505b-135">Ntlm</span></span>|<span data-ttu-id="6505b-136">Korzysta z uwierzytelniania NTLM, jako rezerwowe z domeną systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="6505b-136">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="6505b-137">Windows</span><span class="sxs-lookup"><span data-stu-id="6505b-137">Windows</span></span>|<span data-ttu-id="6505b-138">Używa zintegrowanego uwierzytelniania Windows.</span><span class="sxs-lookup"><span data-stu-id="6505b-138">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="6505b-139">Certyfikat</span><span class="sxs-lookup"><span data-stu-id="6505b-139">Certificate</span></span>|<span data-ttu-id="6505b-140">Przy użyciu certyfikatów X.509 do uwierzytelniania klienta.</span><span class="sxs-lookup"><span data-stu-id="6505b-140">Uses X.509 certificates to authenticate the client.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="6505b-141">proxyCredentialType atrybutu</span><span class="sxs-lookup"><span data-stu-id="6505b-141">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="6505b-142">Wartość</span><span class="sxs-lookup"><span data-stu-id="6505b-142">Value</span></span>|<span data-ttu-id="6505b-143">Opis</span><span class="sxs-lookup"><span data-stu-id="6505b-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6505b-144">Brak</span><span class="sxs-lookup"><span data-stu-id="6505b-144">None</span></span>|<span data-ttu-id="6505b-145">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="6505b-145">Security is disabled.</span></span>|  
|<span data-ttu-id="6505b-146">Podstawowy</span><span class="sxs-lookup"><span data-stu-id="6505b-146">Basic</span></span>|<span data-ttu-id="6505b-147">Korzysta z uwierzytelniania podstawowego.</span><span class="sxs-lookup"><span data-stu-id="6505b-147">Uses basic authentication.</span></span>|  
|<span data-ttu-id="6505b-148">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="6505b-148">Digest</span></span>|<span data-ttu-id="6505b-149">Uwierzytelnianie szyfrowane używa.</span><span class="sxs-lookup"><span data-stu-id="6505b-149">Uses digest authentication.</span></span>|  
|<span data-ttu-id="6505b-150">Ntlm</span><span class="sxs-lookup"><span data-stu-id="6505b-150">Ntlm</span></span>|<span data-ttu-id="6505b-151">Wykorzystuje NTLM jako rezerwowe z domeną systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="6505b-151">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="6505b-152">Windows</span><span class="sxs-lookup"><span data-stu-id="6505b-152">Windows</span></span>|<span data-ttu-id="6505b-153">Używa zintegrowanego uwierzytelniania Windows.</span><span class="sxs-lookup"><span data-stu-id="6505b-153">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="6505b-154">Certyfikat</span><span class="sxs-lookup"><span data-stu-id="6505b-154">Certificate</span></span>|<span data-ttu-id="6505b-155">Przy użyciu certyfikatów X.509 do uwierzytelniania klienta.</span><span class="sxs-lookup"><span data-stu-id="6505b-155">Uses X.509 certificates to authenticate the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6505b-156">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6505b-156">Child Elements</span></span>  
 <span data-ttu-id="6505b-157">Brak</span><span class="sxs-lookup"><span data-stu-id="6505b-157">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6505b-158">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6505b-158">Parent Elements</span></span>  
  
|<span data-ttu-id="6505b-159">Element</span><span class="sxs-lookup"><span data-stu-id="6505b-159">Element</span></span>|<span data-ttu-id="6505b-160">Opis</span><span class="sxs-lookup"><span data-stu-id="6505b-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6505b-161">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="6505b-161">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-ws2007httpbinding.md)|<span data-ttu-id="6505b-162">Reprezentuje możliwości zabezpieczeń [ \<ws2007HttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="6505b-162">Represents the security capabilities of the [\<ws2007HttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6505b-163">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6505b-163">See also</span></span>
- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpTransportSecurityElement>
- [<span data-ttu-id="6505b-164">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="6505b-164">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="6505b-165">Powiązania</span><span class="sxs-lookup"><span data-stu-id="6505b-165">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="6505b-166">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="6505b-166">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="6505b-167">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="6505b-167">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="6505b-168">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="6505b-168">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
