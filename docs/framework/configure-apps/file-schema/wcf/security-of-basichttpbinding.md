---
title: '&lt;security&gt; w &lt;basicHttpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6432708d-5465-4bd9-bfc2-466742db99cb
caps.latest.revision: "16"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 8d61075bc96427736f7e6f5a39302bbd59d434f9
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="ltsecuritygt-of-ltbasichttpbindinggt"></a><span data-ttu-id="bc14d-102">&lt;security&gt; w &lt;basicHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="bc14d-102">&lt;security&gt; of &lt;basicHttpBinding&gt;</span></span>
<span data-ttu-id="bc14d-103">Możliwości zabezpieczeń definiuje [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="bc14d-103">Defines the security capabilities of the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>  
  
 <span data-ttu-id="bc14d-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="bc14d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="bc14d-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="bc14d-105">\<bindings></span></span>  
<span data-ttu-id="bc14d-106">\<basicHttpBinding></span><span class="sxs-lookup"><span data-stu-id="bc14d-106">\<basicHttpBinding></span></span>  
<span data-ttu-id="bc14d-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="bc14d-107">\<binding></span></span>  
<span data-ttu-id="bc14d-108">\<security></span><span class="sxs-lookup"><span data-stu-id="bc14d-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc14d-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="bc14d-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bc14d-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="bc14d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="bc14d-111">W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="bc14d-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bc14d-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="bc14d-112">Attributes</span></span>  
  
|<span data-ttu-id="bc14d-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="bc14d-113">Attribute</span></span>|<span data-ttu-id="bc14d-114">Opis</span><span class="sxs-lookup"><span data-stu-id="bc14d-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bc14d-115">tryb</span><span class="sxs-lookup"><span data-stu-id="bc14d-115">mode</span></span>|<span data-ttu-id="bc14d-116">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="bc14d-116">Optional.</span></span> <span data-ttu-id="bc14d-117">Określa typ zabezpieczeń, który jest używany.</span><span class="sxs-lookup"><span data-stu-id="bc14d-117">Specifies the type of security that is used.</span></span> <span data-ttu-id="bc14d-118">Wartość domyślna to `None`.</span><span class="sxs-lookup"><span data-stu-id="bc14d-118">The default is `None`.</span></span> <span data-ttu-id="bc14d-119">Ten atrybut jest typu <xref:System.ServiceModel.BasicHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="bc14d-119">This attribute is of type <xref:System.ServiceModel.BasicHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="bc14d-120">Tryb atrybutu</span><span class="sxs-lookup"><span data-stu-id="bc14d-120">mode Attribute</span></span>  
  
|<span data-ttu-id="bc14d-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="bc14d-121">Value</span></span>|<span data-ttu-id="bc14d-122">Opis</span><span class="sxs-lookup"><span data-stu-id="bc14d-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="bc14d-123">Brak</span><span class="sxs-lookup"><span data-stu-id="bc14d-123">None</span></span>|<span data-ttu-id="bc14d-124">— Liczba komunikatów nie są już zabezpieczone podczas transferu.</span><span class="sxs-lookup"><span data-stu-id="bc14d-124">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="bc14d-125">Transportu</span><span class="sxs-lookup"><span data-stu-id="bc14d-125">Transport</span></span>|<span data-ttu-id="bc14d-126">Zabezpieczenia transportu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="bc14d-126">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="bc14d-127">Wiadomości SOAP są chronione przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="bc14d-127">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="bc14d-128">Usługa jest uwierzytelniany przez klienta za pomocą certyfikatu X.509 usługi.</span><span class="sxs-lookup"><span data-stu-id="bc14d-128">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="bc14d-129">Klient jest uwierzytelniany przy użyciu ClientCredentialType dostarczony.</span><span class="sxs-lookup"><span data-stu-id="bc14d-129">The client is authenticated using the ClientCredentialType supplied.</span></span> <span data-ttu-id="bc14d-130">Zobacz [ \<transportu >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="bc14d-130">See the [\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md).</span></span>|  
|<span data-ttu-id="bc14d-131">Komunikat</span><span class="sxs-lookup"><span data-stu-id="bc14d-131">Message</span></span>|<span data-ttu-id="bc14d-132">Zabezpieczenia korzystanie z zabezpieczeń komunikatów SOAP.</span><span class="sxs-lookup"><span data-stu-id="bc14d-132">Security is provided using SOAP message security.</span></span> <span data-ttu-id="bc14d-133">Domyślnie treści zostaje zaszyfrowany i podpisany.</span><span class="sxs-lookup"><span data-stu-id="bc14d-133">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="bc14d-134">Dla tego powiązania system wymaga podania certyfikatu serwera do klienta poza pasmem.</span><span class="sxs-lookup"><span data-stu-id="bc14d-134">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="bc14d-135">Jedyne prawidłowe `ClientCredentialType` dla tego powiązania jest `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="bc14d-135">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|  
|<span data-ttu-id="bc14d-136">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="bc14d-136">TransportWithMessageCredential</span></span>|<span data-ttu-id="bc14d-137">Uwierzytelnianie integralności i poufności serwera są udostępniane za pośrednictwem zabezpieczeń transportu.</span><span class="sxs-lookup"><span data-stu-id="bc14d-137">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="bc14d-138">Uwierzytelnianie klienta znajduje się za pomocą zabezpieczeń wiadomości protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="bc14d-138">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="bc14d-139">Ten tryb jest istotne, gdy uwierzytelnia użytkownika przy użyciu nazwy użytkownika i hasła i ma istniejącego wdrożenia protokołu HTTP do zabezpieczania transferu komunikatów.</span><span class="sxs-lookup"><span data-stu-id="bc14d-139">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|  
|<span data-ttu-id="bc14d-140">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="bc14d-140">TransportCredentialOnly</span></span>|<span data-ttu-id="bc14d-141">W tym trybie nie zapewnia integralności i poufności.</span><span class="sxs-lookup"><span data-stu-id="bc14d-141">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="bc14d-142">Zapewnia uwierzytelnianie oparte na protokole http klienta.</span><span class="sxs-lookup"><span data-stu-id="bc14d-142">It provides http-based client authentication.</span></span> <span data-ttu-id="bc14d-143">Tego trybu należy używać ostrożnie.</span><span class="sxs-lookup"><span data-stu-id="bc14d-143">This mode should be used with caution.</span></span> <span data-ttu-id="bc14d-144">Tej opcji należy używać w środowiskach, gdzie zabezpieczeń transportu jest świadczona w inny sposób (na przykład IPSec), a tylko uwierzytelnianie klienta jest zapewniana przez [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="bc14d-144">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bc14d-145">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="bc14d-145">Child Elements</span></span>  
  
|<span data-ttu-id="bc14d-146">Element</span><span class="sxs-lookup"><span data-stu-id="bc14d-146">Element</span></span>|<span data-ttu-id="bc14d-147">Opis</span><span class="sxs-lookup"><span data-stu-id="bc14d-147">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bc14d-148">\<transport ></span><span class="sxs-lookup"><span data-stu-id="bc14d-148">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md)|<span data-ttu-id="bc14d-149">Definiuje ustawienia zabezpieczeń transportu podstawowa usługa HTTP.</span><span class="sxs-lookup"><span data-stu-id="bc14d-149">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="bc14d-150">Ten element odpowiada <xref:System.ServiceModel.HttpTransportSecurity>.</span><span class="sxs-lookup"><span data-stu-id="bc14d-150">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|  
|[<span data-ttu-id="bc14d-151">\<message></span><span class="sxs-lookup"><span data-stu-id="bc14d-151">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-basichttpbinding.md)|<span data-ttu-id="bc14d-152">Definiuje ustawienia zabezpieczeń wiadomości dla podstawowa usługa HTTP.</span><span class="sxs-lookup"><span data-stu-id="bc14d-152">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="bc14d-153">Ten element odpowiada <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span><span class="sxs-lookup"><span data-stu-id="bc14d-153">This element corresponds to <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bc14d-154">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="bc14d-154">Parent Elements</span></span>  
  
|<span data-ttu-id="bc14d-155">Element</span><span class="sxs-lookup"><span data-stu-id="bc14d-155">Element</span></span>|<span data-ttu-id="bc14d-156">Opis</span><span class="sxs-lookup"><span data-stu-id="bc14d-156">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bc14d-157">powiązanie</span><span class="sxs-lookup"><span data-stu-id="bc14d-157">binding</span></span>|<span data-ttu-id="bc14d-158">Element powiązania [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="bc14d-158">The binding element of the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc14d-159">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bc14d-159">Remarks</span></span>  
 <span data-ttu-id="bc14d-160">Domyślnie komunikatu protokołu SOAP nie jest zabezpieczony, a klient nie jest uwierzytelniony.</span><span class="sxs-lookup"><span data-stu-id="bc14d-160">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="bc14d-161">Ten element umożliwia skonfigurowanie dodatkowych ustawień zabezpieczeń dla `basicHttpBinding` elementu.</span><span class="sxs-lookup"><span data-stu-id="bc14d-161">This element enables you to configure additional security settings for the `basicHttpBinding` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc14d-162">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bc14d-162">See Also</span></span>  
 <xref:System.ServiceModel.BasicHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>  
 <xref:System.ServiceModel.BasicHttpSecurity>  
 [<span data-ttu-id="bc14d-163">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="bc14d-163">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="bc14d-164">Wybieranie typu poświadczeń</span><span class="sxs-lookup"><span data-stu-id="bc14d-164">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="bc14d-165">Powiązania</span><span class="sxs-lookup"><span data-stu-id="bc14d-165">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="bc14d-166">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="bc14d-166">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="bc14d-167">Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="bc14d-167">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="bc14d-168">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="bc14d-168">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
