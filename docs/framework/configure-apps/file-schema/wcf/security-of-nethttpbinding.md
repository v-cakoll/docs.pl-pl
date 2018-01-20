---
title: '&lt;security&gt; w &lt;netHttpBinding'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dc41f6f7-cabc-4a64-9fa0-ceabf861b348
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cbe36a801565af0d3664e5c827f8ce903be3b5c7
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="ltsecuritygt-of-ltnethttpbinding"></a><span data-ttu-id="0854d-102">&lt;security&gt; w &lt;netHttpBinding</span><span class="sxs-lookup"><span data-stu-id="0854d-102">&lt;security&gt; of &lt;netHttpBinding</span></span>
<span data-ttu-id="0854d-103">Możliwości zabezpieczeń definiuje [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="0854d-103">Defines the security capabilities of the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>  
  
 <span data-ttu-id="0854d-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="0854d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="0854d-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="0854d-105">\<bindings></span></span>  
<span data-ttu-id="0854d-106">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="0854d-106">\<netHttpBinding></span></span>  
<span data-ttu-id="0854d-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="0854d-107">\<binding></span></span>  
<span data-ttu-id="0854d-108">\<security></span><span class="sxs-lookup"><span data-stu-id="0854d-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0854d-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="0854d-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0854d-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0854d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0854d-111">W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0854d-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0854d-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0854d-112">Attributes</span></span>  
  
|<span data-ttu-id="0854d-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="0854d-113">Attribute</span></span>|<span data-ttu-id="0854d-114">Opis</span><span class="sxs-lookup"><span data-stu-id="0854d-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0854d-115">tryb</span><span class="sxs-lookup"><span data-stu-id="0854d-115">mode</span></span>|<span data-ttu-id="0854d-116">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="0854d-116">Optional.</span></span> <span data-ttu-id="0854d-117">Określa typ zabezpieczeń, który jest używany.</span><span class="sxs-lookup"><span data-stu-id="0854d-117">Specifies the type of security that is used.</span></span> <span data-ttu-id="0854d-118">Wartość domyślna to `None`.</span><span class="sxs-lookup"><span data-stu-id="0854d-118">The default is `None`.</span></span> <span data-ttu-id="0854d-119">Ten atrybut jest typu <!--zz <xref:System.ServiceModel.NetHttpSecurityMode> --> `System.ServiceModel.NetHttpSecurityMode`.</span><span class="sxs-lookup"><span data-stu-id="0854d-119">This attribute is of type <!--zz <xref:System.ServiceModel.NetHttpSecurityMode> -->`System.ServiceModel.NetHttpSecurityMode`.</span></span>|
  
## <a name="mode-attribute"></a><span data-ttu-id="0854d-120">Tryb atrybutu</span><span class="sxs-lookup"><span data-stu-id="0854d-120">mode Attribute</span></span>  
  
|<span data-ttu-id="0854d-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="0854d-121">Value</span></span>|<span data-ttu-id="0854d-122">Opis</span><span class="sxs-lookup"><span data-stu-id="0854d-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0854d-123">Brak</span><span class="sxs-lookup"><span data-stu-id="0854d-123">None</span></span>|<span data-ttu-id="0854d-124">— Liczba komunikatów nie są już zabezpieczone podczas transferu.</span><span class="sxs-lookup"><span data-stu-id="0854d-124">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="0854d-125">Transportu</span><span class="sxs-lookup"><span data-stu-id="0854d-125">Transport</span></span>|<span data-ttu-id="0854d-126">Zabezpieczenia transportu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="0854d-126">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="0854d-127">Wiadomości SOAP są chronione przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="0854d-127">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="0854d-128">Usługa jest uwierzytelniany przez klienta za pomocą certyfikatu X.509 usługi.</span><span class="sxs-lookup"><span data-stu-id="0854d-128">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="0854d-129">Klient jest uwierzytelniany przy użyciu ClientCredentialType dostarczony.</span><span class="sxs-lookup"><span data-stu-id="0854d-129">The client is authenticated using the ClientCredentialType supplied.</span></span>|  
|<span data-ttu-id="0854d-130">Komunikat</span><span class="sxs-lookup"><span data-stu-id="0854d-130">Message</span></span>|<span data-ttu-id="0854d-131">Zabezpieczenia korzystanie z zabezpieczeń komunikatów SOAP.</span><span class="sxs-lookup"><span data-stu-id="0854d-131">Security is provided using SOAP message security.</span></span> <span data-ttu-id="0854d-132">Domyślnie treści zostaje zaszyfrowany i podpisany.</span><span class="sxs-lookup"><span data-stu-id="0854d-132">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="0854d-133">Dla tego powiązania system wymaga podania certyfikatu serwera do klienta poza pasmem.</span><span class="sxs-lookup"><span data-stu-id="0854d-133">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="0854d-134">Jedyne prawidłowe `ClientCredentialType` dla tego powiązania jest `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="0854d-134">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|  
|<span data-ttu-id="0854d-135">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="0854d-135">TransportWithMessageCredential</span></span>|<span data-ttu-id="0854d-136">Uwierzytelnianie integralności i poufności serwera są udostępniane za pośrednictwem zabezpieczeń transportu.</span><span class="sxs-lookup"><span data-stu-id="0854d-136">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="0854d-137">Uwierzytelnianie klienta znajduje się za pomocą zabezpieczeń wiadomości protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="0854d-137">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="0854d-138">Ten tryb jest istotne, gdy uwierzytelnia użytkownika przy użyciu nazwy użytkownika i hasła i ma istniejącego wdrożenia protokołu HTTP do zabezpieczania transferu komunikatów.</span><span class="sxs-lookup"><span data-stu-id="0854d-138">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|  
|<span data-ttu-id="0854d-139">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="0854d-139">TransportCredentialOnly</span></span>|<span data-ttu-id="0854d-140">W tym trybie nie zapewnia integralności i poufności.</span><span class="sxs-lookup"><span data-stu-id="0854d-140">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="0854d-141">Zapewnia uwierzytelnianie oparte na protokole http klienta.</span><span class="sxs-lookup"><span data-stu-id="0854d-141">It provides http-based client authentication.</span></span> <span data-ttu-id="0854d-142">Tego trybu należy używać ostrożnie.</span><span class="sxs-lookup"><span data-stu-id="0854d-142">This mode should be used with caution.</span></span> <span data-ttu-id="0854d-143">Tej opcji należy używać w środowiskach, gdzie zabezpieczeń transportu jest świadczona w inny sposób (na przykład IPSec), a tylko uwierzytelnianie klienta jest zapewniana przez [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="0854d-143">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0854d-144">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0854d-144">Child Elements</span></span>  
  
|<span data-ttu-id="0854d-145">Element</span><span class="sxs-lookup"><span data-stu-id="0854d-145">Element</span></span>|<span data-ttu-id="0854d-146">Opis</span><span class="sxs-lookup"><span data-stu-id="0854d-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0854d-147">\<transport ></span><span class="sxs-lookup"><span data-stu-id="0854d-147">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-nethttpbinding.md)|<span data-ttu-id="0854d-148">Definiuje ustawienia zabezpieczeń transportu podstawowa usługa HTTP.</span><span class="sxs-lookup"><span data-stu-id="0854d-148">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="0854d-149">Ten element odpowiada <xref:System.ServiceModel.HttpTransportSecurity>.</span><span class="sxs-lookup"><span data-stu-id="0854d-149">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|  
|[<span data-ttu-id="0854d-150">\<message></span><span class="sxs-lookup"><span data-stu-id="0854d-150">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-nethttpbinding.md)|<span data-ttu-id="0854d-151">Definiuje ustawienia zabezpieczeń wiadomości dla podstawowa usługa HTTP.</span><span class="sxs-lookup"><span data-stu-id="0854d-151">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="0854d-152">Ten element odpowiada <!--zz <xref:System.ServiceModel.NetHttpMessageSecurity> --> `System.ServiceModel.NetHttpMessageSecurity`.</span><span class="sxs-lookup"><span data-stu-id="0854d-152">This element corresponds to <!--zz <xref:System.ServiceModel.NetHttpMessageSecurity> --> `System.ServiceModel.NetHttpMessageSecurity`.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0854d-153">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0854d-153">Parent Elements</span></span>  
  
|<span data-ttu-id="0854d-154">Element</span><span class="sxs-lookup"><span data-stu-id="0854d-154">Element</span></span>|<span data-ttu-id="0854d-155">Opis</span><span class="sxs-lookup"><span data-stu-id="0854d-155">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0854d-156">powiązanie</span><span class="sxs-lookup"><span data-stu-id="0854d-156">binding</span></span>|<span data-ttu-id="0854d-157">Element powiązania [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="0854d-157">The binding element of the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0854d-158">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0854d-158">Remarks</span></span>  
 <span data-ttu-id="0854d-159">Domyślnie komunikatu protokołu SOAP nie jest zabezpieczony, a klient nie jest uwierzytelniony.</span><span class="sxs-lookup"><span data-stu-id="0854d-159">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="0854d-160">Ten element umożliwia skonfigurowanie dodatkowych ustawień zabezpieczeń dla `netHttpBinding` elementu.</span><span class="sxs-lookup"><span data-stu-id="0854d-160">This element enables you to configure additional security settings for the `netHttpBinding` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0854d-161">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0854d-161">See Also</span></span>  
 <xref:System.ServiceModel.NetHttpBinding.Security%2A>  
 <span data-ttu-id="0854d-162"><xref:System.ServiceModel.Configuration.NetHttpBindingElement.Security%2A></span><span class="sxs-lookup"><span data-stu-id="0854d-162"><xref:System.ServiceModel.Configuration.NetHttpBindingElement.Security%2A></span></span>    
 [<span data-ttu-id="0854d-163">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="0854d-163">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="0854d-164">Wybieranie typu poświadczeń</span><span class="sxs-lookup"><span data-stu-id="0854d-164">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="0854d-165">Powiązania</span><span class="sxs-lookup"><span data-stu-id="0854d-165">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="0854d-166">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="0854d-166">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="0854d-167">Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="0854d-167">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="0854d-168">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="0854d-168">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
