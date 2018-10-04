---
title: '&lt;transport&gt; w &lt;ws2007HttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 692befa3-8b0b-4ec5-b601-755874e98eb0
ms.openlocfilehash: 5c7e96beee2fc1e4780729e56f10a52b63dde4e8
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48580066"
---
# <a name="lttransportgt-of-ltws2007httpbindinggt"></a><span data-ttu-id="72ac5-102">&lt;transport&gt; w &lt;ws2007HttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="72ac5-102">&lt;transport&gt; of &lt;ws2007HttpBinding&gt;</span></span>
<span data-ttu-id="72ac5-103">Definiuje ustawienia uwierzytelniania dla protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="72ac5-103">Defines authentication settings for the HTTP transport.</span></span>  
  
 <span data-ttu-id="72ac5-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="72ac5-104">\<system.serviceModel></span></span>  
<span data-ttu-id="72ac5-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="72ac5-105">\<bindings></span></span>  
<span data-ttu-id="72ac5-106">\<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="72ac5-106">\<ws2007HttpBinding></span></span>  
<span data-ttu-id="72ac5-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="72ac5-107">\<binding></span></span>  
<span data-ttu-id="72ac5-108">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="72ac5-108">\<security></span></span>  
<span data-ttu-id="72ac5-109">\<transport></span><span class="sxs-lookup"><span data-stu-id="72ac5-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72ac5-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="72ac5-110">Syntax</span></span>  
  
```  
transport clientCredentialType =   
       "Basic/Certificate/Digest/None/Ntlm/Windows"  
       proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
       realm="string"   
```  
  
## <a name="type"></a><span data-ttu-id="72ac5-111">Typ</span><span class="sxs-lookup"><span data-stu-id="72ac5-111">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="72ac5-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="72ac5-112">Attributes and Elements</span></span>  
 <span data-ttu-id="72ac5-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="72ac5-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="72ac5-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="72ac5-114">Attributes</span></span>  
  
|<span data-ttu-id="72ac5-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="72ac5-115">Attribute</span></span>|<span data-ttu-id="72ac5-116">Opis</span><span class="sxs-lookup"><span data-stu-id="72ac5-116">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="72ac5-117">Określa poświadczenia używane do uwierzytelniania klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="72ac5-117">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="72ac5-118">Ten atrybut jest typu <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="72ac5-118">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="72ac5-119">Określa poświadczenia używane do uwierzytelniania klienta do domeny serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="72ac5-119">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="72ac5-120">Ten atrybut jest typu <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="72ac5-120">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="72ac5-121">Obszar uwierzytelniania dla uwierzytelniania podstawowego lub szyfrowanego.</span><span class="sxs-lookup"><span data-stu-id="72ac5-121">The authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="72ac5-122">Wartość domyślna to ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="72ac5-122">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="72ac5-123">Obszar uwierzytelniania co najmniej Określa nazwę hosta, który przeprowadza uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="72ac5-123">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="72ac5-124">Można również określić zbiór użytkowników, którzy mają dostęp.</span><span class="sxs-lookup"><span data-stu-id="72ac5-124">It can also specify a collection of users who have access.</span></span> <span data-ttu-id="72ac5-125">Użytkownika można badać obszaru uwierzytelniania, aby określić jedną z kilku możliwych nazw użytkowników i haseł może służyć.</span><span class="sxs-lookup"><span data-stu-id="72ac5-125">A user can query the authentication realm to determine which one of the several possible usernames and passwords can be used.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="72ac5-126">właściwości ClientCredentialType o wartości atrybutu</span><span class="sxs-lookup"><span data-stu-id="72ac5-126">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="72ac5-127">Wartość</span><span class="sxs-lookup"><span data-stu-id="72ac5-127">Value</span></span>|<span data-ttu-id="72ac5-128">Opis</span><span class="sxs-lookup"><span data-stu-id="72ac5-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="72ac5-129">Brak</span><span class="sxs-lookup"><span data-stu-id="72ac5-129">None</span></span>|<span data-ttu-id="72ac5-130">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="72ac5-130">Security is disabled.</span></span>|  
|<span data-ttu-id="72ac5-131">Podstawowy</span><span class="sxs-lookup"><span data-stu-id="72ac5-131">Basic</span></span>|<span data-ttu-id="72ac5-132">Korzysta z uwierzytelniania podstawowego.</span><span class="sxs-lookup"><span data-stu-id="72ac5-132">Uses basic authentication.</span></span>|  
|<span data-ttu-id="72ac5-133">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="72ac5-133">Digest</span></span>|<span data-ttu-id="72ac5-134">Uwierzytelnianie szyfrowane używa.</span><span class="sxs-lookup"><span data-stu-id="72ac5-134">Uses digest authentication.</span></span>|  
|<span data-ttu-id="72ac5-135">Uwierzytelnianie NTLM</span><span class="sxs-lookup"><span data-stu-id="72ac5-135">Ntlm</span></span>|<span data-ttu-id="72ac5-136">Korzysta z uwierzytelniania NTLM, jako rezerwowe z domeną systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="72ac5-136">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="72ac5-137">Windows</span><span class="sxs-lookup"><span data-stu-id="72ac5-137">Windows</span></span>|<span data-ttu-id="72ac5-138">Używa zintegrowanego uwierzytelniania Windows.</span><span class="sxs-lookup"><span data-stu-id="72ac5-138">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="72ac5-139">Certyfikat</span><span class="sxs-lookup"><span data-stu-id="72ac5-139">Certificate</span></span>|<span data-ttu-id="72ac5-140">Przy użyciu certyfikatów X.509 do uwierzytelniania klienta.</span><span class="sxs-lookup"><span data-stu-id="72ac5-140">Uses X.509 certificates to authenticate the client.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="72ac5-141">proxyCredentialType atrybutu</span><span class="sxs-lookup"><span data-stu-id="72ac5-141">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="72ac5-142">Wartość</span><span class="sxs-lookup"><span data-stu-id="72ac5-142">Value</span></span>|<span data-ttu-id="72ac5-143">Opis</span><span class="sxs-lookup"><span data-stu-id="72ac5-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="72ac5-144">Brak</span><span class="sxs-lookup"><span data-stu-id="72ac5-144">None</span></span>|<span data-ttu-id="72ac5-145">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="72ac5-145">Security is disabled.</span></span>|  
|<span data-ttu-id="72ac5-146">Podstawowy</span><span class="sxs-lookup"><span data-stu-id="72ac5-146">Basic</span></span>|<span data-ttu-id="72ac5-147">Korzysta z uwierzytelniania podstawowego.</span><span class="sxs-lookup"><span data-stu-id="72ac5-147">Uses basic authentication.</span></span>|  
|<span data-ttu-id="72ac5-148">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="72ac5-148">Digest</span></span>|<span data-ttu-id="72ac5-149">Uwierzytelnianie szyfrowane używa.</span><span class="sxs-lookup"><span data-stu-id="72ac5-149">Uses digest authentication.</span></span>|  
|<span data-ttu-id="72ac5-150">Uwierzytelnianie NTLM</span><span class="sxs-lookup"><span data-stu-id="72ac5-150">Ntlm</span></span>|<span data-ttu-id="72ac5-151">Wykorzystuje NTLM jako rezerwowe z domeną systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="72ac5-151">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="72ac5-152">Windows</span><span class="sxs-lookup"><span data-stu-id="72ac5-152">Windows</span></span>|<span data-ttu-id="72ac5-153">Używa zintegrowanego uwierzytelniania Windows.</span><span class="sxs-lookup"><span data-stu-id="72ac5-153">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="72ac5-154">Certyfikat</span><span class="sxs-lookup"><span data-stu-id="72ac5-154">Certificate</span></span>|<span data-ttu-id="72ac5-155">Przy użyciu certyfikatów X.509 do uwierzytelniania klienta.</span><span class="sxs-lookup"><span data-stu-id="72ac5-155">Uses X.509 certificates to authenticate the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="72ac5-156">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="72ac5-156">Child Elements</span></span>  
 <span data-ttu-id="72ac5-157">Brak</span><span class="sxs-lookup"><span data-stu-id="72ac5-157">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="72ac5-158">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="72ac5-158">Parent Elements</span></span>  
  
|<span data-ttu-id="72ac5-159">Element</span><span class="sxs-lookup"><span data-stu-id="72ac5-159">Element</span></span>|<span data-ttu-id="72ac5-160">Opis</span><span class="sxs-lookup"><span data-stu-id="72ac5-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="72ac5-161">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="72ac5-161">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-ws2007httpbinding.md)|<span data-ttu-id="72ac5-162">Reprezentuje możliwości zabezpieczeń [ \<ws2007HttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="72ac5-162">Represents the security capabilities of the [\<ws2007HttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="72ac5-163">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="72ac5-163">See Also</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpTransportSecurityElement>  
 [<span data-ttu-id="72ac5-164">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="72ac5-164">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="72ac5-165">Powiązania</span><span class="sxs-lookup"><span data-stu-id="72ac5-165">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="72ac5-166">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="72ac5-166">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="72ac5-167">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="72ac5-167">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="72ac5-168">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="72ac5-168">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
