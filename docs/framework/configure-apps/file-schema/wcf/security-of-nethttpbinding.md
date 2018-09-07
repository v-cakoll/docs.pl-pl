---
title: '&lt;security&gt; w &lt;netHttpBinding'
ms.date: 03/30/2017
ms.assetid: dc41f6f7-cabc-4a64-9fa0-ceabf861b348
ms.openlocfilehash: 6357593be17c2d008204598d51610fa3dbf77c27
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44061081"
---
# <a name="ltsecuritygt-of-ltnethttpbinding"></a><span data-ttu-id="d4576-102">&lt;security&gt; w &lt;netHttpBinding</span><span class="sxs-lookup"><span data-stu-id="d4576-102">&lt;security&gt; of &lt;netHttpBinding</span></span>
<span data-ttu-id="d4576-103">Definiuje możliwości zabezpieczeń [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="d4576-103">Defines the security capabilities of the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>  
  
 <span data-ttu-id="d4576-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d4576-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d4576-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="d4576-105">\<bindings></span></span>  
<span data-ttu-id="d4576-106">\<netHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="d4576-106">\<netHttpBinding></span></span>  
<span data-ttu-id="d4576-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="d4576-107">\<binding></span></span>  
<span data-ttu-id="d4576-108">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="d4576-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4576-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="d4576-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d4576-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d4576-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d4576-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d4576-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d4576-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d4576-112">Attributes</span></span>  
  
|<span data-ttu-id="d4576-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d4576-113">Attribute</span></span>|<span data-ttu-id="d4576-114">Opis</span><span class="sxs-lookup"><span data-stu-id="d4576-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d4576-115">tryb</span><span class="sxs-lookup"><span data-stu-id="d4576-115">mode</span></span>|<span data-ttu-id="d4576-116">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="d4576-116">Optional.</span></span> <span data-ttu-id="d4576-117">Określa typ zabezpieczeń, która jest używana.</span><span class="sxs-lookup"><span data-stu-id="d4576-117">Specifies the type of security that is used.</span></span> <span data-ttu-id="d4576-118">Wartość domyślna to `None`.</span><span class="sxs-lookup"><span data-stu-id="d4576-118">The default is `None`.</span></span> <span data-ttu-id="d4576-119">Ten atrybut jest typu <!--zz <xref:System.ServiceModel.NetHttpSecurityMode> --> `System.ServiceModel.NetHttpSecurityMode`.</span><span class="sxs-lookup"><span data-stu-id="d4576-119">This attribute is of type <!--zz <xref:System.ServiceModel.NetHttpSecurityMode> -->`System.ServiceModel.NetHttpSecurityMode`.</span></span>|
  
## <a name="mode-attribute"></a><span data-ttu-id="d4576-120">Tryb atrybutu</span><span class="sxs-lookup"><span data-stu-id="d4576-120">mode Attribute</span></span>  
  
|<span data-ttu-id="d4576-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="d4576-121">Value</span></span>|<span data-ttu-id="d4576-122">Opis</span><span class="sxs-lookup"><span data-stu-id="d4576-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d4576-123">Brak</span><span class="sxs-lookup"><span data-stu-id="d4576-123">None</span></span>|<span data-ttu-id="d4576-124">— Liczba komunikatów nie są zabezpieczane podczas przesyłania.</span><span class="sxs-lookup"><span data-stu-id="d4576-124">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="d4576-125">Transportu</span><span class="sxs-lookup"><span data-stu-id="d4576-125">Transport</span></span>|<span data-ttu-id="d4576-126">Zabezpieczenia za pomocą transportu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="d4576-126">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="d4576-127">Komunikaty protokołu SOAP są chronione przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="d4576-127">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="d4576-128">Usługa jest uwierzytelniany przez klienta za pomocą certyfikatu X.509 usługi.</span><span class="sxs-lookup"><span data-stu-id="d4576-128">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="d4576-129">Klient jest uwierzytelniany przy użyciu właściwości ClientCredentialType o wartości dostarczone.</span><span class="sxs-lookup"><span data-stu-id="d4576-129">The client is authenticated using the ClientCredentialType supplied.</span></span>|  
|<span data-ttu-id="d4576-130">Komunikat</span><span class="sxs-lookup"><span data-stu-id="d4576-130">Message</span></span>|<span data-ttu-id="d4576-131">Zabezpieczenia korzystanie z zabezpieczeń komunikatów protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="d4576-131">Security is provided using SOAP message security.</span></span> <span data-ttu-id="d4576-132">Domyślnie treść jest zaszyfrowany i podpisany.</span><span class="sxs-lookup"><span data-stu-id="d4576-132">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="d4576-133">Dla tego powiązania systemu wymaga podania certyfikatu serwera do klienta poza pasmem.</span><span class="sxs-lookup"><span data-stu-id="d4576-133">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="d4576-134">Jedyne prawidłowe `ClientCredentialType` dla tego powiązania jest `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="d4576-134">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|  
|<span data-ttu-id="d4576-135">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="d4576-135">TransportWithMessageCredential</span></span>|<span data-ttu-id="d4576-136">Uwierzytelnianie integralności, poufności i serwera są dostarczane przez zabezpieczeń transportu.</span><span class="sxs-lookup"><span data-stu-id="d4576-136">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="d4576-137">Uwierzytelnianie klienta znajduje się za pomocą zabezpieczeń wiadomości protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="d4576-137">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="d4576-138">Ten tryb jest istotne, po użytkownik jest uwierzytelniany przy użyciu nazwy użytkownika/hasła istniejącego wdrożenia protokołu HTTP do zabezpieczania transferu komunikatów.</span><span class="sxs-lookup"><span data-stu-id="d4576-138">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|  
|<span data-ttu-id="d4576-139">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="d4576-139">TransportCredentialOnly</span></span>|<span data-ttu-id="d4576-140">Ten tryb nie zapewnia integralność komunikatów i poufność.</span><span class="sxs-lookup"><span data-stu-id="d4576-140">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="d4576-141">Zapewnia uwierzytelnianie oparte na protokole http klienta.</span><span class="sxs-lookup"><span data-stu-id="d4576-141">It provides http-based client authentication.</span></span> <span data-ttu-id="d4576-142">W tym trybie, należy używać ostrożnie.</span><span class="sxs-lookup"><span data-stu-id="d4576-142">This mode should be used with caution.</span></span> <span data-ttu-id="d4576-143">Należy używać w środowiskach, gdzie zabezpieczenia transportu jest świadczona w inny sposób (takich jak IPSec), a tylko uwierzytelnianie klientów jest świadczona przez infrastrukturę usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="d4576-143">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d4576-144">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d4576-144">Child Elements</span></span>  
  
|<span data-ttu-id="d4576-145">Element</span><span class="sxs-lookup"><span data-stu-id="d4576-145">Element</span></span>|<span data-ttu-id="d4576-146">Opis</span><span class="sxs-lookup"><span data-stu-id="d4576-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d4576-147">\<transport ></span><span class="sxs-lookup"><span data-stu-id="d4576-147">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-nethttpbinding.md)|<span data-ttu-id="d4576-148">Określa ustawienia zabezpieczenia transportu podstawowa usługa HTTP.</span><span class="sxs-lookup"><span data-stu-id="d4576-148">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="d4576-149">Ten element odnosi się do <xref:System.ServiceModel.HttpTransportSecurity>.</span><span class="sxs-lookup"><span data-stu-id="d4576-149">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|  
|[<span data-ttu-id="d4576-150">\<message></span><span class="sxs-lookup"><span data-stu-id="d4576-150">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-nethttpbinding.md)|<span data-ttu-id="d4576-151">Definiuje ustawienia zabezpieczeń wiadomości dla podstawowa usługa HTTP.</span><span class="sxs-lookup"><span data-stu-id="d4576-151">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="d4576-152">Ten element odnosi się do <!--zz <xref:System.ServiceModel.NetHttpMessageSecurity> --> `System.ServiceModel.NetHttpMessageSecurity`.</span><span class="sxs-lookup"><span data-stu-id="d4576-152">This element corresponds to <!--zz <xref:System.ServiceModel.NetHttpMessageSecurity> --> `System.ServiceModel.NetHttpMessageSecurity`.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d4576-153">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d4576-153">Parent Elements</span></span>  
  
|<span data-ttu-id="d4576-154">Element</span><span class="sxs-lookup"><span data-stu-id="d4576-154">Element</span></span>|<span data-ttu-id="d4576-155">Opis</span><span class="sxs-lookup"><span data-stu-id="d4576-155">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d4576-156">powiązanie</span><span class="sxs-lookup"><span data-stu-id="d4576-156">binding</span></span>|<span data-ttu-id="d4576-157">Element powiązania [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="d4576-157">The binding element of the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d4576-158">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d4576-158">Remarks</span></span>  
 <span data-ttu-id="d4576-159">Domyślnie komunikat protokołu SOAP nie jest zabezpieczony, a klient nie jest uwierzytelniony.</span><span class="sxs-lookup"><span data-stu-id="d4576-159">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="d4576-160">Ten element umożliwia konfigurowanie dodatkowych ustawień zabezpieczeń dla `netHttpBinding` elementu.</span><span class="sxs-lookup"><span data-stu-id="d4576-160">This element enables you to configure additional security settings for the `netHttpBinding` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4576-161">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d4576-161">See Also</span></span>  
 <xref:System.ServiceModel.NetHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetHttpBindingElement.Security%2A>    
 [<span data-ttu-id="d4576-162">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="d4576-162">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="d4576-163">Wybieranie typu poświadczeń</span><span class="sxs-lookup"><span data-stu-id="d4576-163">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="d4576-164">Powiązania</span><span class="sxs-lookup"><span data-stu-id="d4576-164">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="d4576-165">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="d4576-165">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="d4576-166">Konfigurowanie Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="d4576-166">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="d4576-167">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="d4576-167">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
