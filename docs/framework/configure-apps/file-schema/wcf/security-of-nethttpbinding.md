---
title: '&lt;security&gt; w &lt;netHttpBinding'
ms.date: 03/30/2017
ms.assetid: dc41f6f7-cabc-4a64-9fa0-ceabf861b348
ms.openlocfilehash: a03553c5afe78b3f95526411b8187464da08161b
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149693"
---
# <a name="ltsecuritygt-of-ltnethttpbinding"></a><span data-ttu-id="c3d3c-102">&lt;security&gt; w &lt;netHttpBinding</span><span class="sxs-lookup"><span data-stu-id="c3d3c-102">&lt;security&gt; of &lt;netHttpBinding</span></span>
<span data-ttu-id="c3d3c-103">Definiuje możliwości zabezpieczeń [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="c3d3c-103">Defines the security capabilities of the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>  
  
<span data-ttu-id="c3d3c-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c3d3c-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="c3d3c-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="c3d3c-105">\<bindings></span></span>  
<span data-ttu-id="c3d3c-106">\<netHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="c3d3c-106">\<netHttpBinding></span></span>  
<span data-ttu-id="c3d3c-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="c3d3c-107">\<binding></span></span>  
<span data-ttu-id="c3d3c-108">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="c3d3c-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3d3c-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="c3d3c-109">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="string" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c3d3c-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c3d3c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c3d3c-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c3d3c-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c3d3c-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c3d3c-112">Attributes</span></span>  
  
|<span data-ttu-id="c3d3c-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c3d3c-113">Attribute</span></span>|<span data-ttu-id="c3d3c-114">Opis</span><span class="sxs-lookup"><span data-stu-id="c3d3c-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c3d3c-115">tryb</span><span class="sxs-lookup"><span data-stu-id="c3d3c-115">mode</span></span>|<span data-ttu-id="c3d3c-116">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="c3d3c-116">Optional.</span></span> <span data-ttu-id="c3d3c-117">Określa typ zabezpieczeń, która jest używana.</span><span class="sxs-lookup"><span data-stu-id="c3d3c-117">Specifies the type of security that is used.</span></span> <span data-ttu-id="c3d3c-118">Wartość domyślna to `None`.</span><span class="sxs-lookup"><span data-stu-id="c3d3c-118">The default is `None`.</span></span> <span data-ttu-id="c3d3c-119">Ten atrybut jest typu <xref:System.ServiceModel.BasicHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="c3d3c-119">This attribute is of type <xref:System.ServiceModel.BasicHttpSecurityMode>.</span></span>|
  
## <a name="mode-attribute"></a><span data-ttu-id="c3d3c-120">Tryb atrybutu</span><span class="sxs-lookup"><span data-stu-id="c3d3c-120">mode Attribute</span></span>  
  
|<span data-ttu-id="c3d3c-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="c3d3c-121">Value</span></span>|<span data-ttu-id="c3d3c-122">Opis</span><span class="sxs-lookup"><span data-stu-id="c3d3c-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c3d3c-123">Brak</span><span class="sxs-lookup"><span data-stu-id="c3d3c-123">None</span></span>|<span data-ttu-id="c3d3c-124">— Liczba komunikatów nie są zabezpieczane podczas przesyłania.</span><span class="sxs-lookup"><span data-stu-id="c3d3c-124">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="c3d3c-125">Transportu</span><span class="sxs-lookup"><span data-stu-id="c3d3c-125">Transport</span></span>|<span data-ttu-id="c3d3c-126">Zabezpieczenia za pomocą transportu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c3d3c-126">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="c3d3c-127">Komunikaty protokołu SOAP są chronione przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c3d3c-127">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="c3d3c-128">Usługa jest uwierzytelniany przez klienta za pomocą certyfikatu X.509 usługi.</span><span class="sxs-lookup"><span data-stu-id="c3d3c-128">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="c3d3c-129">Klient jest uwierzytelniany przy użyciu właściwości ClientCredentialType o wartości dostarczone.</span><span class="sxs-lookup"><span data-stu-id="c3d3c-129">The client is authenticated using the ClientCredentialType supplied.</span></span>|  
|<span data-ttu-id="c3d3c-130">Komunikat</span><span class="sxs-lookup"><span data-stu-id="c3d3c-130">Message</span></span>|<span data-ttu-id="c3d3c-131">Zabezpieczenia korzystanie z zabezpieczeń komunikatów protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="c3d3c-131">Security is provided using SOAP message security.</span></span> <span data-ttu-id="c3d3c-132">Domyślnie treść jest zaszyfrowany i podpisany.</span><span class="sxs-lookup"><span data-stu-id="c3d3c-132">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="c3d3c-133">Dla tego powiązania systemu wymaga podania certyfikatu serwera do klienta poza pasmem.</span><span class="sxs-lookup"><span data-stu-id="c3d3c-133">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="c3d3c-134">Jedyne prawidłowe `ClientCredentialType` dla tego powiązania jest `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="c3d3c-134">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|  
|<span data-ttu-id="c3d3c-135">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="c3d3c-135">TransportWithMessageCredential</span></span>|<span data-ttu-id="c3d3c-136">Uwierzytelnianie integralności, poufności i serwera są dostarczane przez zabezpieczeń transportu.</span><span class="sxs-lookup"><span data-stu-id="c3d3c-136">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="c3d3c-137">Uwierzytelnianie klienta znajduje się za pomocą zabezpieczeń wiadomości protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="c3d3c-137">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="c3d3c-138">Ten tryb jest istotne, po użytkownik jest uwierzytelniany przy użyciu nazwy użytkownika/hasła istniejącego wdrożenia protokołu HTTP do zabezpieczania transferu komunikatów.</span><span class="sxs-lookup"><span data-stu-id="c3d3c-138">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|  
|<span data-ttu-id="c3d3c-139">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="c3d3c-139">TransportCredentialOnly</span></span>|<span data-ttu-id="c3d3c-140">Ten tryb nie zapewnia integralność komunikatów i poufność.</span><span class="sxs-lookup"><span data-stu-id="c3d3c-140">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="c3d3c-141">Zapewnia uwierzytelnianie oparte na protokole http klienta.</span><span class="sxs-lookup"><span data-stu-id="c3d3c-141">It provides http-based client authentication.</span></span> <span data-ttu-id="c3d3c-142">W tym trybie, należy używać ostrożnie.</span><span class="sxs-lookup"><span data-stu-id="c3d3c-142">This mode should be used with caution.</span></span> <span data-ttu-id="c3d3c-143">Należy używać w środowiskach, gdzie zabezpieczenia transportu jest świadczona w inny sposób (takich jak IPSec), a tylko uwierzytelnianie klientów jest świadczona przez infrastrukturę usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="c3d3c-143">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c3d3c-144">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c3d3c-144">Child Elements</span></span>  
  
|<span data-ttu-id="c3d3c-145">Element</span><span class="sxs-lookup"><span data-stu-id="c3d3c-145">Element</span></span>|<span data-ttu-id="c3d3c-146">Opis</span><span class="sxs-lookup"><span data-stu-id="c3d3c-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c3d3c-147">\<transport ></span><span class="sxs-lookup"><span data-stu-id="c3d3c-147">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-nethttpbinding.md)|<span data-ttu-id="c3d3c-148">Określa ustawienia zabezpieczenia transportu podstawowa usługa HTTP.</span><span class="sxs-lookup"><span data-stu-id="c3d3c-148">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="c3d3c-149">Ten element odnosi się do <xref:System.ServiceModel.HttpTransportSecurity>.</span><span class="sxs-lookup"><span data-stu-id="c3d3c-149">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|  
|[<span data-ttu-id="c3d3c-150">\<message></span><span class="sxs-lookup"><span data-stu-id="c3d3c-150">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-nethttpbinding.md)|<span data-ttu-id="c3d3c-151">Definiuje ustawienia zabezpieczeń wiadomości dla podstawowa usługa HTTP.</span><span class="sxs-lookup"><span data-stu-id="c3d3c-151">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="c3d3c-152">Ten element odnosi się do <!--zz <xref:System.ServiceModel.NetHttpMessageSecurity> --> `System.ServiceModel.NetHttpMessageSecurity`.</span><span class="sxs-lookup"><span data-stu-id="c3d3c-152">This element corresponds to <!--zz <xref:System.ServiceModel.NetHttpMessageSecurity> --> `System.ServiceModel.NetHttpMessageSecurity`.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c3d3c-153">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c3d3c-153">Parent Elements</span></span>  
  
|<span data-ttu-id="c3d3c-154">Element</span><span class="sxs-lookup"><span data-stu-id="c3d3c-154">Element</span></span>|<span data-ttu-id="c3d3c-155">Opis</span><span class="sxs-lookup"><span data-stu-id="c3d3c-155">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c3d3c-156">powiązanie</span><span class="sxs-lookup"><span data-stu-id="c3d3c-156">binding</span></span>|<span data-ttu-id="c3d3c-157">Element powiązania [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="c3d3c-157">The binding element of the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c3d3c-158">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c3d3c-158">Remarks</span></span>  
 <span data-ttu-id="c3d3c-159">Domyślnie komunikat protokołu SOAP nie jest zabezpieczony, a klient nie jest uwierzytelniony.</span><span class="sxs-lookup"><span data-stu-id="c3d3c-159">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="c3d3c-160">Ten element umożliwia konfigurowanie dodatkowych ustawień zabezpieczeń dla `netHttpBinding` elementu.</span><span class="sxs-lookup"><span data-stu-id="c3d3c-160">This element enables you to configure additional security settings for the `netHttpBinding` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3d3c-161">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c3d3c-161">See Also</span></span>  
 <xref:System.ServiceModel.NetHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetHttpBindingElement.Security%2A>    
 [<span data-ttu-id="c3d3c-162">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="c3d3c-162">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="c3d3c-163">Wybieranie typu poświadczeń</span><span class="sxs-lookup"><span data-stu-id="c3d3c-163">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="c3d3c-164">Powiązania</span><span class="sxs-lookup"><span data-stu-id="c3d3c-164">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="c3d3c-165">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="c3d3c-165">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="c3d3c-166">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="c3d3c-166">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="c3d3c-167">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="c3d3c-167">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
