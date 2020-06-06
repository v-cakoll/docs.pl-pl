---
title: <transport> dla <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 692befa3-8b0b-4ec5-b601-755874e98eb0
ms.openlocfilehash: 0cd20c607b0c4ddd3ecfd806d38ba63b4a5c5a25
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73732765"
---
# <a name="transport-of-ws2007httpbinding"></a><span data-ttu-id="4e672-102">\<transport> dla \<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="4e672-102">\<transport> of \<ws2007HttpBinding></span></span>
<span data-ttu-id="4e672-103">Definiuje ustawienia uwierzytelniania dla transportu HTTP.</span><span class="sxs-lookup"><span data-stu-id="4e672-103">Defines authentication settings for the HTTP transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007HttpBinding>**](ws2007httpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-ws2007httpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="4e672-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4e672-104">Syntax</span></span>  
  
```xml  
<transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
           proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
           realm="string" />
```  
  
## <a name="type"></a><span data-ttu-id="4e672-105">Typ</span><span class="sxs-lookup"><span data-stu-id="4e672-105">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4e672-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4e672-106">Attributes and Elements</span></span>  
 <span data-ttu-id="4e672-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4e672-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4e672-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4e672-108">Attributes</span></span>  
  
|<span data-ttu-id="4e672-109">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4e672-109">Attribute</span></span>|<span data-ttu-id="4e672-110">Opis</span><span class="sxs-lookup"><span data-stu-id="4e672-110">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="4e672-111">Określa poświadczenie używane do uwierzytelniania klienta w usłudze.</span><span class="sxs-lookup"><span data-stu-id="4e672-111">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="4e672-112">Ten atrybut jest typu <xref:System.ServiceModel.HttpClientCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="4e672-112">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="4e672-113">Określa poświadczenie używane do uwierzytelniania klienta programu na serwerze proxy domeny.</span><span class="sxs-lookup"><span data-stu-id="4e672-113">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="4e672-114">Ten atrybut jest typu <xref:System.ServiceModel.HttpProxyCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="4e672-114">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="4e672-115">Obszar uwierzytelniania dla uwierzytelniania szyfrowanego lub podstawowego.</span><span class="sxs-lookup"><span data-stu-id="4e672-115">The authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="4e672-116">Wartość domyślna to pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="4e672-116">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="4e672-117">Obszar uwierzytelniania określa co najmniej nazwę hosta, który wykonuje uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="4e672-117">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="4e672-118">Można również określić kolekcję użytkowników, którzy mają dostęp.</span><span class="sxs-lookup"><span data-stu-id="4e672-118">It can also specify a collection of users who have access.</span></span> <span data-ttu-id="4e672-119">Użytkownik może wysyłać zapytania do obszaru uwierzytelniania, aby określić, która z kilku możliwych nazw użytkowników i haseł może być używana.</span><span class="sxs-lookup"><span data-stu-id="4e672-119">A user can query the authentication realm to determine which one of the several possible usernames and passwords can be used.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="4e672-120">clientCredentialtype — atrybut</span><span class="sxs-lookup"><span data-stu-id="4e672-120">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="4e672-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="4e672-121">Value</span></span>|<span data-ttu-id="4e672-122">Opis</span><span class="sxs-lookup"><span data-stu-id="4e672-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4e672-123">Brak</span><span class="sxs-lookup"><span data-stu-id="4e672-123">None</span></span>|<span data-ttu-id="4e672-124">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="4e672-124">Security is disabled.</span></span>|  
|<span data-ttu-id="4e672-125">Podstawowy</span><span class="sxs-lookup"><span data-stu-id="4e672-125">Basic</span></span>|<span data-ttu-id="4e672-126">Używa uwierzytelniania podstawowego.</span><span class="sxs-lookup"><span data-stu-id="4e672-126">Uses basic authentication.</span></span>|  
|<span data-ttu-id="4e672-127">Szyfrowane</span><span class="sxs-lookup"><span data-stu-id="4e672-127">Digest</span></span>|<span data-ttu-id="4e672-128">Używa uwierzytelniania szyfrowanego.</span><span class="sxs-lookup"><span data-stu-id="4e672-128">Uses digest authentication.</span></span>|  
|<span data-ttu-id="4e672-129">NTLM</span><span class="sxs-lookup"><span data-stu-id="4e672-129">Ntlm</span></span>|<span data-ttu-id="4e672-130">Używa uwierzytelniania NTLM jako rezerwy z domeną systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="4e672-130">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="4e672-131">Windows</span><span class="sxs-lookup"><span data-stu-id="4e672-131">Windows</span></span>|<span data-ttu-id="4e672-132">Używa zintegrowanego uwierzytelniania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="4e672-132">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="4e672-133">Certyfikat</span><span class="sxs-lookup"><span data-stu-id="4e672-133">Certificate</span></span>|<span data-ttu-id="4e672-134">Uwierzytelnia klienta za pomocą certyfikatów X. 509.</span><span class="sxs-lookup"><span data-stu-id="4e672-134">Uses X.509 certificates to authenticate the client.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="4e672-135">proxyCredentialType — atrybut</span><span class="sxs-lookup"><span data-stu-id="4e672-135">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="4e672-136">Wartość</span><span class="sxs-lookup"><span data-stu-id="4e672-136">Value</span></span>|<span data-ttu-id="4e672-137">Opis</span><span class="sxs-lookup"><span data-stu-id="4e672-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4e672-138">Brak</span><span class="sxs-lookup"><span data-stu-id="4e672-138">None</span></span>|<span data-ttu-id="4e672-139">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="4e672-139">Security is disabled.</span></span>|  
|<span data-ttu-id="4e672-140">Podstawowy</span><span class="sxs-lookup"><span data-stu-id="4e672-140">Basic</span></span>|<span data-ttu-id="4e672-141">Używa uwierzytelniania podstawowego.</span><span class="sxs-lookup"><span data-stu-id="4e672-141">Uses basic authentication.</span></span>|  
|<span data-ttu-id="4e672-142">Szyfrowane</span><span class="sxs-lookup"><span data-stu-id="4e672-142">Digest</span></span>|<span data-ttu-id="4e672-143">Używa uwierzytelniania szyfrowanego.</span><span class="sxs-lookup"><span data-stu-id="4e672-143">Uses digest authentication.</span></span>|  
|<span data-ttu-id="4e672-144">NTLM</span><span class="sxs-lookup"><span data-stu-id="4e672-144">Ntlm</span></span>|<span data-ttu-id="4e672-145">Używa protokołu NTLM jako rezerwy z domeną systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="4e672-145">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="4e672-146">Windows</span><span class="sxs-lookup"><span data-stu-id="4e672-146">Windows</span></span>|<span data-ttu-id="4e672-147">Używa zintegrowanego uwierzytelniania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="4e672-147">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="4e672-148">Certyfikat</span><span class="sxs-lookup"><span data-stu-id="4e672-148">Certificate</span></span>|<span data-ttu-id="4e672-149">Uwierzytelnia klienta za pomocą certyfikatów X. 509.</span><span class="sxs-lookup"><span data-stu-id="4e672-149">Uses X.509 certificates to authenticate the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4e672-150">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4e672-150">Child Elements</span></span>  
 <span data-ttu-id="4e672-151">Brak</span><span class="sxs-lookup"><span data-stu-id="4e672-151">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4e672-152">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4e672-152">Parent Elements</span></span>  
  
|<span data-ttu-id="4e672-153">Element</span><span class="sxs-lookup"><span data-stu-id="4e672-153">Element</span></span>|<span data-ttu-id="4e672-154">Opis</span><span class="sxs-lookup"><span data-stu-id="4e672-154">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-ws2007httpbinding.md)|<span data-ttu-id="4e672-155">Reprezentuje możliwości zabezpieczeń [\<ws2007HttpBinding>](ws2007httpbinding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="4e672-155">Represents the security capabilities of the [\<ws2007HttpBinding>](ws2007httpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4e672-156">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4e672-156">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpTransportSecurityElement>
- [<span data-ttu-id="4e672-157">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="4e672-157">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="4e672-158">Powiązania</span><span class="sxs-lookup"><span data-stu-id="4e672-158">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="4e672-159">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="4e672-159">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="4e672-160">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="4e672-160">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
