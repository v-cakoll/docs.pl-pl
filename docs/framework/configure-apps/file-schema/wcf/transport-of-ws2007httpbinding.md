---
title: '&lt;transport&gt; w &lt;ws2007HttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 692befa3-8b0b-4ec5-b601-755874e98eb0
ms.openlocfilehash: 35af47551f742b0e48220611a874605fb752b626
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43396800"
---
# <a name="lttransportgt-of-ltws2007httpbindinggt"></a><span data-ttu-id="5794d-102">&lt;transport&gt; w &lt;ws2007HttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="5794d-102">&lt;transport&gt; of &lt;ws2007HttpBinding&gt;</span></span>
<span data-ttu-id="5794d-103">Definiuje ustawienia uwierzytelniania dla protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="5794d-103">Defines authentication settings for the HTTP transport.</span></span>  
  
 <span data-ttu-id="5794d-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="5794d-104">\<system.serviceModel></span></span>  
<span data-ttu-id="5794d-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="5794d-105">\<bindings></span></span>  
<span data-ttu-id="5794d-106">\<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="5794d-106">\<ws2007HttpBinding></span></span>  
<span data-ttu-id="5794d-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="5794d-107">\<binding></span></span>  
<span data-ttu-id="5794d-108">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="5794d-108">\<security></span></span>  
<span data-ttu-id="5794d-109">\<transport></span><span class="sxs-lookup"><span data-stu-id="5794d-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5794d-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="5794d-110">Syntax</span></span>  
  
```  
transport clientCredentialType =   
       "Basic/Certificate/Digest/None/Ntlm/Windows"  
       proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
       realm="string"   
```  
  
## <a name="type"></a><span data-ttu-id="5794d-111">Typ</span><span class="sxs-lookup"><span data-stu-id="5794d-111">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5794d-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5794d-112">Attributes and Elements</span></span>  
 <span data-ttu-id="5794d-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5794d-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5794d-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5794d-114">Attributes</span></span>  
  
|<span data-ttu-id="5794d-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5794d-115">Attribute</span></span>|<span data-ttu-id="5794d-116">Opis</span><span class="sxs-lookup"><span data-stu-id="5794d-116">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="5794d-117">Określa poświadczenia używane do uwierzytelniania klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="5794d-117">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="5794d-118">Ten atrybut jest typu <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="5794d-118">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="5794d-119">Określa poświadczenia używane do uwierzytelniania klienta do domeny serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="5794d-119">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="5794d-120">Ten atrybut jest typu <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="5794d-120">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="5794d-121">Obszar uwierzytelniania dla uwierzytelniania podstawowego lub szyfrowanego.</span><span class="sxs-lookup"><span data-stu-id="5794d-121">The authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="5794d-122">Wartość domyślna to ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="5794d-122">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="5794d-123">Obszar uwierzytelniania co najmniej Określa nazwę hosta, który przeprowadza uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="5794d-123">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="5794d-124">Można również określić zbiór użytkowników, którzy mają dostęp.</span><span class="sxs-lookup"><span data-stu-id="5794d-124">It can also specify a collection of users who have access.</span></span> <span data-ttu-id="5794d-125">Użytkownika można badać obszaru uwierzytelniania, aby określić jedną z kilku możliwych nazw użytkowników i haseł może służyć.</span><span class="sxs-lookup"><span data-stu-id="5794d-125">A user can query the authentication realm to determine which one of the several possible usernames and passwords can be used.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="5794d-126">właściwości ClientCredentialType o wartości atrybutu</span><span class="sxs-lookup"><span data-stu-id="5794d-126">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="5794d-127">Wartość</span><span class="sxs-lookup"><span data-stu-id="5794d-127">Value</span></span>|<span data-ttu-id="5794d-128">Opis</span><span class="sxs-lookup"><span data-stu-id="5794d-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5794d-129">Brak</span><span class="sxs-lookup"><span data-stu-id="5794d-129">None</span></span>|<span data-ttu-id="5794d-130">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="5794d-130">Security is disabled.</span></span>|  
|<span data-ttu-id="5794d-131">Podstawowy</span><span class="sxs-lookup"><span data-stu-id="5794d-131">Basic</span></span>|<span data-ttu-id="5794d-132">Korzysta z uwierzytelniania podstawowego.</span><span class="sxs-lookup"><span data-stu-id="5794d-132">Uses basic authentication.</span></span>|  
|<span data-ttu-id="5794d-133">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="5794d-133">Digest</span></span>|<span data-ttu-id="5794d-134">Uwierzytelnianie szyfrowane używa.</span><span class="sxs-lookup"><span data-stu-id="5794d-134">Uses digest authentication.</span></span>|  
|<span data-ttu-id="5794d-135">Uwierzytelnianie NTLM</span><span class="sxs-lookup"><span data-stu-id="5794d-135">Ntlm</span></span>|<span data-ttu-id="5794d-136">Korzysta z uwierzytelniania NTLM, jako rezerwowe z domeną systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="5794d-136">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="5794d-137">Windows</span><span class="sxs-lookup"><span data-stu-id="5794d-137">Windows</span></span>|<span data-ttu-id="5794d-138">Używa zintegrowanego uwierzytelniania Windows.</span><span class="sxs-lookup"><span data-stu-id="5794d-138">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="5794d-139">Certyfikat</span><span class="sxs-lookup"><span data-stu-id="5794d-139">Certificate</span></span>|<span data-ttu-id="5794d-140">Przy użyciu certyfikatów X.509 do uwierzytelniania klienta.</span><span class="sxs-lookup"><span data-stu-id="5794d-140">Uses X.509 certificates to authenticate the client.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="5794d-141">proxyCredentialType atrybutu</span><span class="sxs-lookup"><span data-stu-id="5794d-141">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="5794d-142">Wartość</span><span class="sxs-lookup"><span data-stu-id="5794d-142">Value</span></span>|<span data-ttu-id="5794d-143">Opis</span><span class="sxs-lookup"><span data-stu-id="5794d-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5794d-144">Brak</span><span class="sxs-lookup"><span data-stu-id="5794d-144">None</span></span>|<span data-ttu-id="5794d-145">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="5794d-145">Security is disabled.</span></span>|  
|<span data-ttu-id="5794d-146">Podstawowy</span><span class="sxs-lookup"><span data-stu-id="5794d-146">Basic</span></span>|<span data-ttu-id="5794d-147">Korzysta z uwierzytelniania podstawowego.</span><span class="sxs-lookup"><span data-stu-id="5794d-147">Uses basic authentication.</span></span>|  
|<span data-ttu-id="5794d-148">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="5794d-148">Digest</span></span>|<span data-ttu-id="5794d-149">Uwierzytelnianie szyfrowane używa.</span><span class="sxs-lookup"><span data-stu-id="5794d-149">Uses digest authentication.</span></span>|  
|<span data-ttu-id="5794d-150">Uwierzytelnianie NTLM</span><span class="sxs-lookup"><span data-stu-id="5794d-150">Ntlm</span></span>|<span data-ttu-id="5794d-151">Wykorzystuje NTLM jako rezerwowe z domeną systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="5794d-151">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="5794d-152">Windows</span><span class="sxs-lookup"><span data-stu-id="5794d-152">Windows</span></span>|<span data-ttu-id="5794d-153">Używa zintegrowanego uwierzytelniania Windows.</span><span class="sxs-lookup"><span data-stu-id="5794d-153">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="5794d-154">Certyfikat</span><span class="sxs-lookup"><span data-stu-id="5794d-154">Certificate</span></span>|<span data-ttu-id="5794d-155">Przy użyciu certyfikatów X.509 do uwierzytelniania klienta.</span><span class="sxs-lookup"><span data-stu-id="5794d-155">Uses X.509 certificates to authenticate the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5794d-156">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5794d-156">Child Elements</span></span>  
 <span data-ttu-id="5794d-157">Brak</span><span class="sxs-lookup"><span data-stu-id="5794d-157">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5794d-158">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5794d-158">Parent Elements</span></span>  
  
|<span data-ttu-id="5794d-159">Element</span><span class="sxs-lookup"><span data-stu-id="5794d-159">Element</span></span>|<span data-ttu-id="5794d-160">Opis</span><span class="sxs-lookup"><span data-stu-id="5794d-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5794d-161">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="5794d-161">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-ws2007httpbinding.md)|<span data-ttu-id="5794d-162">Reprezentuje możliwości zabezpieczeń [ \<ws2007HttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="5794d-162">Represents the security capabilities of the [\<ws2007HttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5794d-163">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5794d-163">See Also</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpTransportSecurityElement>  
 [<span data-ttu-id="5794d-164">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="5794d-164">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="5794d-165">Powiązania</span><span class="sxs-lookup"><span data-stu-id="5794d-165">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="5794d-166">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="5794d-166">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="5794d-167">Konfigurowanie Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="5794d-167">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="5794d-168">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="5794d-168">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
