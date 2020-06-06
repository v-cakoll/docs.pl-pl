---
title: <security> dla <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 6432708d-5465-4bd9-bfc2-466742db99cb
ms.openlocfilehash: c8e4f2d000a155eecd2a6c7faaaf4af525b24ca3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738713"
---
# <a name="security-of-basichttpbinding"></a><span data-ttu-id="864f2-102">\<security> dla \<basicHttpBinding></span><span class="sxs-lookup"><span data-stu-id="864f2-102">\<security> of \<basicHttpBinding></span></span>
<span data-ttu-id="864f2-103">Definiuje możliwości zabezpieczeń programu [\<basicHttpBinding>](basichttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="864f2-103">Defines the security capabilities of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<basicHttpBinding>**](basichttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="864f2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="864f2-104">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="string" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="864f2-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="864f2-105">Attributes and Elements</span></span>  
 <span data-ttu-id="864f2-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="864f2-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="864f2-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="864f2-107">Attributes</span></span>  
  
|<span data-ttu-id="864f2-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="864f2-108">Attribute</span></span>|<span data-ttu-id="864f2-109">Opis</span><span class="sxs-lookup"><span data-stu-id="864f2-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="864f2-110">tryb</span><span class="sxs-lookup"><span data-stu-id="864f2-110">mode</span></span>|<span data-ttu-id="864f2-111">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="864f2-111">Optional.</span></span> <span data-ttu-id="864f2-112">Określa typ używanego zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="864f2-112">Specifies the type of security that is used.</span></span> <span data-ttu-id="864f2-113">Wartość domyślna to `None`.</span><span class="sxs-lookup"><span data-stu-id="864f2-113">The default is `None`.</span></span> <span data-ttu-id="864f2-114">Ten atrybut jest typu <xref:System.ServiceModel.BasicHttpSecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="864f2-114">This attribute is of type <xref:System.ServiceModel.BasicHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="864f2-115">Atrybut Mode</span><span class="sxs-lookup"><span data-stu-id="864f2-115">mode Attribute</span></span>  
  
|<span data-ttu-id="864f2-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="864f2-116">Value</span></span>|<span data-ttu-id="864f2-117">Opis</span><span class="sxs-lookup"><span data-stu-id="864f2-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="864f2-118">Brak</span><span class="sxs-lookup"><span data-stu-id="864f2-118">None</span></span>|<span data-ttu-id="864f2-119">-Komunikaty nie są zabezpieczane podczas transferu.</span><span class="sxs-lookup"><span data-stu-id="864f2-119">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="864f2-120">Transport</span><span class="sxs-lookup"><span data-stu-id="864f2-120">Transport</span></span>|<span data-ttu-id="864f2-121">Zabezpieczenia są udostępniane przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="864f2-121">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="864f2-122">Komunikaty protokołu SOAP są zabezpieczone przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="864f2-122">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="864f2-123">Usługa jest uwierzytelniana na kliencie przy użyciu certyfikatu X. 509 usługi.</span><span class="sxs-lookup"><span data-stu-id="864f2-123">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="864f2-124">Klient jest uwierzytelniany przy użyciu dostarczonego obiekt ClientCredentialtype.</span><span class="sxs-lookup"><span data-stu-id="864f2-124">The client is authenticated using the ClientCredentialType supplied.</span></span> <span data-ttu-id="864f2-125">Zobacz [\<transport>](transport-of-basichttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="864f2-125">See the [\<transport>](transport-of-basichttpbinding.md).</span></span>|  
|<span data-ttu-id="864f2-126">Komunikat</span><span class="sxs-lookup"><span data-stu-id="864f2-126">Message</span></span>|<span data-ttu-id="864f2-127">Zabezpieczenia są udostępniane przy użyciu zabezpieczeń komunikatów protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="864f2-127">Security is provided using SOAP message security.</span></span> <span data-ttu-id="864f2-128">Domyślnie treść jest zaszyfrowana i podpisana.</span><span class="sxs-lookup"><span data-stu-id="864f2-128">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="864f2-129">W przypadku tego powiązania system wymaga, aby certyfikat serwera został dostarczony do klienta poza pasmem.</span><span class="sxs-lookup"><span data-stu-id="864f2-129">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="864f2-130">Jedyna prawidłowa `ClientCredentialType` dla tego powiązania to `Certificate` .</span><span class="sxs-lookup"><span data-stu-id="864f2-130">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|  
|<span data-ttu-id="864f2-131">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="864f2-131">TransportWithMessageCredential</span></span>|<span data-ttu-id="864f2-132">Integralność, poufność i uwierzytelnianie serwera są udostępniane przez zabezpieczenia transportu.</span><span class="sxs-lookup"><span data-stu-id="864f2-132">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="864f2-133">Uwierzytelnianie klienta jest zapewniane przez zabezpieczenia komunikatów protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="864f2-133">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="864f2-134">Ten tryb jest istotny, gdy użytkownik jest uwierzytelniany przy użyciu nazwy użytkownika/hasła i istnieje wdrożenie HTTP na potrzeby zabezpieczania transferu komunikatów.</span><span class="sxs-lookup"><span data-stu-id="864f2-134">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|  
|<span data-ttu-id="864f2-135">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="864f2-135">TransportCredentialOnly</span></span>|<span data-ttu-id="864f2-136">Ten tryb nie zapewnia integralności i poufności komunikatów.</span><span class="sxs-lookup"><span data-stu-id="864f2-136">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="864f2-137">Zapewnia uwierzytelnianie klienta oparte na protokole HTTP.</span><span class="sxs-lookup"><span data-stu-id="864f2-137">It provides http-based client authentication.</span></span> <span data-ttu-id="864f2-138">Ten tryb powinien być używany z zachowaniem ostrożności.</span><span class="sxs-lookup"><span data-stu-id="864f2-138">This mode should be used with caution.</span></span> <span data-ttu-id="864f2-139">Powinna być używana w środowiskach, w których zabezpieczenia transportu są dostarczane przy użyciu innych metod (takich jak IPSec) i tylko uwierzytelnianie klienta jest udostępniane przez infrastrukturę WCF.</span><span class="sxs-lookup"><span data-stu-id="864f2-139">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="864f2-140">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="864f2-140">Child Elements</span></span>  
  
|<span data-ttu-id="864f2-141">Element</span><span class="sxs-lookup"><span data-stu-id="864f2-141">Element</span></span>|<span data-ttu-id="864f2-142">Opis</span><span class="sxs-lookup"><span data-stu-id="864f2-142">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-basichttpbinding.md)|<span data-ttu-id="864f2-143">Definiuje ustawienia zabezpieczeń transportu dla podstawowej usługi HTTP.</span><span class="sxs-lookup"><span data-stu-id="864f2-143">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="864f2-144">Ten element odnosi się do <xref:System.ServiceModel.HttpTransportSecurity> .</span><span class="sxs-lookup"><span data-stu-id="864f2-144">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|  
|[\<message>](message-of-basichttpbinding.md)|<span data-ttu-id="864f2-145">Definiuje ustawienia zabezpieczeń wiadomości dla podstawowej usługi HTTP.</span><span class="sxs-lookup"><span data-stu-id="864f2-145">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="864f2-146">Ten element odnosi się do <xref:System.ServiceModel.BasicHttpMessageSecurity> .</span><span class="sxs-lookup"><span data-stu-id="864f2-146">This element corresponds to <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="864f2-147">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="864f2-147">Parent Elements</span></span>  
  
|<span data-ttu-id="864f2-148">Element</span><span class="sxs-lookup"><span data-stu-id="864f2-148">Element</span></span>|<span data-ttu-id="864f2-149">Opis</span><span class="sxs-lookup"><span data-stu-id="864f2-149">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="864f2-150">powiązanie</span><span class="sxs-lookup"><span data-stu-id="864f2-150">binding</span></span>|<span data-ttu-id="864f2-151">Element Binding elementu [\<basicHttpBinding>](basichttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="864f2-151">The binding element of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="864f2-152">Uwagi</span><span class="sxs-lookup"><span data-stu-id="864f2-152">Remarks</span></span>  
 <span data-ttu-id="864f2-153">Domyślnie komunikat protokołu SOAP nie jest zabezpieczony i klient nie jest uwierzytelniany.</span><span class="sxs-lookup"><span data-stu-id="864f2-153">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="864f2-154">Ten element umożliwia skonfigurowanie dodatkowych ustawień zabezpieczeń dla `basicHttpBinding` elementu.</span><span class="sxs-lookup"><span data-stu-id="864f2-154">This element enables you to configure additional security settings for the `basicHttpBinding` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="864f2-155">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="864f2-155">See also</span></span>

- <xref:System.ServiceModel.BasicHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="864f2-156">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="864f2-156">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="864f2-157">Wybieranie typu poświadczeń</span><span class="sxs-lookup"><span data-stu-id="864f2-157">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="864f2-158">Powiązania</span><span class="sxs-lookup"><span data-stu-id="864f2-158">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="864f2-159">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="864f2-159">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="864f2-160">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="864f2-160">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
