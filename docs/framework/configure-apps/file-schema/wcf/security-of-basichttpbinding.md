---
title: '&lt;security&gt; w &lt;basicHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 6432708d-5465-4bd9-bfc2-466742db99cb
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 2adb5736cca59d42ab3c62d61513bbfd80a4be04
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43565219"
---
# <a name="ltsecuritygt-of-ltbasichttpbindinggt"></a><span data-ttu-id="63c01-102">&lt;security&gt; w &lt;basicHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="63c01-102">&lt;security&gt; of &lt;basicHttpBinding&gt;</span></span>
<span data-ttu-id="63c01-103">Definiuje możliwości zabezpieczeń [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="63c01-103">Defines the security capabilities of the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>  
  
 <span data-ttu-id="63c01-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="63c01-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="63c01-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="63c01-105">\<bindings></span></span>  
<span data-ttu-id="63c01-106">\<basicHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="63c01-106">\<basicHttpBinding></span></span>  
<span data-ttu-id="63c01-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="63c01-107">\<binding></span></span>  
<span data-ttu-id="63c01-108">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="63c01-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63c01-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="63c01-109">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">  
   <transport  
      clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
      proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
      realm="string" />  
   <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
            clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />  
</security>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="63c01-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="63c01-110">Attributes and Elements</span></span>  
 <span data-ttu-id="63c01-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="63c01-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="63c01-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="63c01-112">Attributes</span></span>  
  
|<span data-ttu-id="63c01-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="63c01-113">Attribute</span></span>|<span data-ttu-id="63c01-114">Opis</span><span class="sxs-lookup"><span data-stu-id="63c01-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="63c01-115">tryb</span><span class="sxs-lookup"><span data-stu-id="63c01-115">mode</span></span>|<span data-ttu-id="63c01-116">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="63c01-116">Optional.</span></span> <span data-ttu-id="63c01-117">Określa typ zabezpieczeń, która jest używana.</span><span class="sxs-lookup"><span data-stu-id="63c01-117">Specifies the type of security that is used.</span></span> <span data-ttu-id="63c01-118">Wartość domyślna to `None`.</span><span class="sxs-lookup"><span data-stu-id="63c01-118">The default is `None`.</span></span> <span data-ttu-id="63c01-119">Ten atrybut jest typu <xref:System.ServiceModel.BasicHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="63c01-119">This attribute is of type <xref:System.ServiceModel.BasicHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="63c01-120">Tryb atrybutu</span><span class="sxs-lookup"><span data-stu-id="63c01-120">mode Attribute</span></span>  
  
|<span data-ttu-id="63c01-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="63c01-121">Value</span></span>|<span data-ttu-id="63c01-122">Opis</span><span class="sxs-lookup"><span data-stu-id="63c01-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="63c01-123">Brak</span><span class="sxs-lookup"><span data-stu-id="63c01-123">None</span></span>|<span data-ttu-id="63c01-124">— Liczba komunikatów nie są zabezpieczane podczas przesyłania.</span><span class="sxs-lookup"><span data-stu-id="63c01-124">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="63c01-125">Transportu</span><span class="sxs-lookup"><span data-stu-id="63c01-125">Transport</span></span>|<span data-ttu-id="63c01-126">Zabezpieczenia za pomocą transportu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="63c01-126">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="63c01-127">Komunikaty protokołu SOAP są chronione przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="63c01-127">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="63c01-128">Usługa jest uwierzytelniany przez klienta za pomocą certyfikatu X.509 usługi.</span><span class="sxs-lookup"><span data-stu-id="63c01-128">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="63c01-129">Klient jest uwierzytelniany przy użyciu właściwości ClientCredentialType o wartości dostarczone.</span><span class="sxs-lookup"><span data-stu-id="63c01-129">The client is authenticated using the ClientCredentialType supplied.</span></span> <span data-ttu-id="63c01-130">Zobacz [ \<transportu >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="63c01-130">See the [\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md).</span></span>|  
|<span data-ttu-id="63c01-131">Komunikat</span><span class="sxs-lookup"><span data-stu-id="63c01-131">Message</span></span>|<span data-ttu-id="63c01-132">Zabezpieczenia korzystanie z zabezpieczeń komunikatów protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="63c01-132">Security is provided using SOAP message security.</span></span> <span data-ttu-id="63c01-133">Domyślnie treść jest zaszyfrowany i podpisany.</span><span class="sxs-lookup"><span data-stu-id="63c01-133">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="63c01-134">Dla tego powiązania systemu wymaga podania certyfikatu serwera do klienta poza pasmem.</span><span class="sxs-lookup"><span data-stu-id="63c01-134">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="63c01-135">Jedyne prawidłowe `ClientCredentialType` dla tego powiązania jest `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="63c01-135">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|  
|<span data-ttu-id="63c01-136">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="63c01-136">TransportWithMessageCredential</span></span>|<span data-ttu-id="63c01-137">Uwierzytelnianie integralności, poufności i serwera są dostarczane przez zabezpieczeń transportu.</span><span class="sxs-lookup"><span data-stu-id="63c01-137">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="63c01-138">Uwierzytelnianie klienta znajduje się za pomocą zabezpieczeń wiadomości protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="63c01-138">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="63c01-139">Ten tryb jest istotne, po użytkownik jest uwierzytelniany przy użyciu nazwy użytkownika/hasła istniejącego wdrożenia protokołu HTTP do zabezpieczania transferu komunikatów.</span><span class="sxs-lookup"><span data-stu-id="63c01-139">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|  
|<span data-ttu-id="63c01-140">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="63c01-140">TransportCredentialOnly</span></span>|<span data-ttu-id="63c01-141">Ten tryb nie zapewnia integralność komunikatów i poufność.</span><span class="sxs-lookup"><span data-stu-id="63c01-141">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="63c01-142">Zapewnia uwierzytelnianie oparte na protokole http klienta.</span><span class="sxs-lookup"><span data-stu-id="63c01-142">It provides http-based client authentication.</span></span> <span data-ttu-id="63c01-143">W tym trybie, należy używać ostrożnie.</span><span class="sxs-lookup"><span data-stu-id="63c01-143">This mode should be used with caution.</span></span> <span data-ttu-id="63c01-144">Należy używać w środowiskach, gdzie zabezpieczenia transportu jest świadczona w inny sposób (takich jak IPSec), a tylko uwierzytelnianie klientów jest świadczona przez infrastrukturę usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="63c01-144">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="63c01-145">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="63c01-145">Child Elements</span></span>  
  
|<span data-ttu-id="63c01-146">Element</span><span class="sxs-lookup"><span data-stu-id="63c01-146">Element</span></span>|<span data-ttu-id="63c01-147">Opis</span><span class="sxs-lookup"><span data-stu-id="63c01-147">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="63c01-148">\<transport ></span><span class="sxs-lookup"><span data-stu-id="63c01-148">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md)|<span data-ttu-id="63c01-149">Określa ustawienia zabezpieczenia transportu podstawowa usługa HTTP.</span><span class="sxs-lookup"><span data-stu-id="63c01-149">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="63c01-150">Ten element odnosi się do <xref:System.ServiceModel.HttpTransportSecurity>.</span><span class="sxs-lookup"><span data-stu-id="63c01-150">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|  
|[<span data-ttu-id="63c01-151">\<message></span><span class="sxs-lookup"><span data-stu-id="63c01-151">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-basichttpbinding.md)|<span data-ttu-id="63c01-152">Definiuje ustawienia zabezpieczeń wiadomości dla podstawowa usługa HTTP.</span><span class="sxs-lookup"><span data-stu-id="63c01-152">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="63c01-153">Ten element odnosi się do <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span><span class="sxs-lookup"><span data-stu-id="63c01-153">This element corresponds to <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="63c01-154">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="63c01-154">Parent Elements</span></span>  
  
|<span data-ttu-id="63c01-155">Element</span><span class="sxs-lookup"><span data-stu-id="63c01-155">Element</span></span>|<span data-ttu-id="63c01-156">Opis</span><span class="sxs-lookup"><span data-stu-id="63c01-156">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="63c01-157">powiązanie</span><span class="sxs-lookup"><span data-stu-id="63c01-157">binding</span></span>|<span data-ttu-id="63c01-158">Element powiązania [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="63c01-158">The binding element of the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="63c01-159">Uwagi</span><span class="sxs-lookup"><span data-stu-id="63c01-159">Remarks</span></span>  
 <span data-ttu-id="63c01-160">Domyślnie komunikat protokołu SOAP nie jest zabezpieczony, a klient nie jest uwierzytelniony.</span><span class="sxs-lookup"><span data-stu-id="63c01-160">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="63c01-161">Ten element umożliwia konfigurowanie dodatkowych ustawień zabezpieczeń dla `basicHttpBinding` elementu.</span><span class="sxs-lookup"><span data-stu-id="63c01-161">This element enables you to configure additional security settings for the `basicHttpBinding` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63c01-162">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="63c01-162">See Also</span></span>  
 <xref:System.ServiceModel.BasicHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>  
 <xref:System.ServiceModel.BasicHttpSecurity>  
 [<span data-ttu-id="63c01-163">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="63c01-163">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="63c01-164">Wybieranie typu poświadczeń</span><span class="sxs-lookup"><span data-stu-id="63c01-164">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="63c01-165">Powiązania</span><span class="sxs-lookup"><span data-stu-id="63c01-165">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="63c01-166">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="63c01-166">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="63c01-167">Konfigurowanie Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="63c01-167">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="63c01-168">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="63c01-168">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
