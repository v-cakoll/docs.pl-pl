---
title: '&lt;security&gt; w &lt;netMsmqBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 001d11a9-7439-498c-b09d-fca20eaf8cd3
caps.latest.revision: "15"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: c6f0f2a6da3b5bc5cb33d20118c135b3b7652986
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltsecuritygt-of-ltnetmsmqbindinggt"></a><span data-ttu-id="e5a97-102">&lt;security&gt; w &lt;netMsmqBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="e5a97-102">&lt;security&gt; of &lt;netMsmqBinding&gt;</span></span>
<span data-ttu-id="e5a97-103">Definiuje ustawienia zabezpieczeń dla powiązania usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="e5a97-103">Defines the security settings for a MSMQ binding.</span></span> <span data-ttu-id="e5a97-104">Określa, czy włączono transportu lub zabezpieczeń protokołu SOAP, a jeśli tak, poziomy tryb i ochrony uwierzytelniania są używane.</span><span class="sxs-lookup"><span data-stu-id="e5a97-104">It specifies whether transport or SOAP security is enabled and, if so, what authentication mode and protection levels are in use.</span></span>  
  
 <span data-ttu-id="e5a97-105">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="e5a97-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="e5a97-106">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="e5a97-106">\<bindings></span></span>  
<span data-ttu-id="e5a97-107">\<netMsmqBinding ></span><span class="sxs-lookup"><span data-stu-id="e5a97-107">\<netMsmqBinding></span></span>  
<span data-ttu-id="e5a97-108">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="e5a97-108">\<binding></span></span>  
<span data-ttu-id="e5a97-109">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="e5a97-109">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5a97-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="e5a97-110">Syntax</span></span>  
  
```xml  
<security mode="None/Transport/Message/Both">  
   <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"  
      msmqEncryptionAlgorithm="RC4Stream/AES"  
      msmqProtectionLevel="None/Sign/EncryptAndSign"  
      msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />  
      <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
      clientCredentialType="None/Windows/UserName/Certificate/CardSpace"/>  
</security>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e5a97-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e5a97-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e5a97-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e5a97-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e5a97-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e5a97-113">Attributes</span></span>  
  
|<span data-ttu-id="e5a97-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e5a97-114">Attribute</span></span>|<span data-ttu-id="e5a97-115">Opis</span><span class="sxs-lookup"><span data-stu-id="e5a97-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e5a97-116">tryb</span><span class="sxs-lookup"><span data-stu-id="e5a97-116">mode</span></span>|<span data-ttu-id="e5a97-117">Określa typ zabezpieczeń, która kontroluje, integralności i poufności uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="e5a97-117">Specifies the type of security that controls integrity, confidentiality and authentication.</span></span> <span data-ttu-id="e5a97-118">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="e5a97-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="e5a97-119">-Brak: Powoduje wyłączenie zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="e5a97-119">-   None: This disables security.</span></span><br /><span data-ttu-id="e5a97-120">-Transport: Ochrony i uwierzytelniania są oferowane przez transport.</span><span class="sxs-lookup"><span data-stu-id="e5a97-120">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="e5a97-121">Dotyczy to zabezpieczenia wiadomości między menedżerami kolejki dwa.</span><span class="sxs-lookup"><span data-stu-id="e5a97-121">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="e5a97-122">Nie ma żadnych zabezpieczeń oferowany między aplikacją a menedżera kolejek.</span><span class="sxs-lookup"><span data-stu-id="e5a97-122">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="e5a97-123">Istniejące aplikacje usługi Msmq są taką samą funkcję z tym typem tryb zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="e5a97-123">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><span data-ttu-id="e5a97-124">-Komunikat o błędzie: Określa trasie zabezpieczeń aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e5a97-124">-   Message: Specifies end-end application security.</span></span> <span data-ttu-id="e5a97-125">Nie ma żadnych zabezpieczeń oferowanych w warstwie transportowej.</span><span class="sxs-lookup"><span data-stu-id="e5a97-125">There is no security offered at the transport layer.</span></span> <span data-ttu-id="e5a97-126">Jest to podobne do zabezpieczeń oferowanych przez inne standardowe powiązania.</span><span class="sxs-lookup"><span data-stu-id="e5a97-126">This is similar to the security offered by other standard bindings.</span></span><br /><span data-ttu-id="e5a97-127">-Zarówno: Oferuje zabezpieczeń transportu i protokołu SOAP wiadomości warstwy.</span><span class="sxs-lookup"><span data-stu-id="e5a97-127">-   Both: Offers security at both the transport and SOAP messaging layer.</span></span> <span data-ttu-id="e5a97-128">Tych samych poświadczeń jest wymagany na obu poziomach.</span><span class="sxs-lookup"><span data-stu-id="e5a97-128">The same credential is required at both the levels.</span></span><br /><br /> <span data-ttu-id="e5a97-129">Wartość domyślna to transportu.</span><span class="sxs-lookup"><span data-stu-id="e5a97-129">The default value is Transport.</span></span> <span data-ttu-id="e5a97-130">Ten atrybut jest typu <xref:System.ServiceModel.NetMsmqSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="e5a97-130">This attribute is of type <xref:System.ServiceModel.NetMsmqSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e5a97-131">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e5a97-131">Child Elements</span></span>  
  
|<span data-ttu-id="e5a97-132">Element</span><span class="sxs-lookup"><span data-stu-id="e5a97-132">Element</span></span>|<span data-ttu-id="e5a97-133">Opis</span><span class="sxs-lookup"><span data-stu-id="e5a97-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e5a97-134">\<komunikat ></span><span class="sxs-lookup"><span data-stu-id="e5a97-134">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-netmsmqbinding.md)|<span data-ttu-id="e5a97-135">Definiuje ustawienia zabezpieczeń wiadomości protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="e5a97-135">Defines the SOAP message security settings.</span></span> <span data-ttu-id="e5a97-136">Ten element jest typu <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>.</span><span class="sxs-lookup"><span data-stu-id="e5a97-136">This element is of type <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>.</span></span>|  
|[<span data-ttu-id="e5a97-137">\<transport ></span><span class="sxs-lookup"><span data-stu-id="e5a97-137">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-netmsmqbinding.md)|<span data-ttu-id="e5a97-138">Definiuje ustawienia zabezpieczeń dla transportu MSMQ.</span><span class="sxs-lookup"><span data-stu-id="e5a97-138">Defines the security settings for the MSMQ transport.</span></span> <span data-ttu-id="e5a97-139">Ten element jest typu <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="e5a97-139">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e5a97-140">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e5a97-140">Parent Elements</span></span>  
  
|<span data-ttu-id="e5a97-141">Element</span><span class="sxs-lookup"><span data-stu-id="e5a97-141">Element</span></span>|<span data-ttu-id="e5a97-142">Opis</span><span class="sxs-lookup"><span data-stu-id="e5a97-142">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e5a97-143">powiązanie</span><span class="sxs-lookup"><span data-stu-id="e5a97-143">binding</span></span>|<span data-ttu-id="e5a97-144">Element powiązania [ \<netMsmqBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)</span><span class="sxs-lookup"><span data-stu-id="e5a97-144">The binding element of the [\<netMsmqBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e5a97-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e5a97-145">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement>  
 <xref:System.ServiceModel.NetMsmqBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetMsmqBindingElement.Security%2A>  
 <xref:System.ServiceModel.NetMsmqSecurity>  
 [<span data-ttu-id="e5a97-146">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="e5a97-146">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="e5a97-147">Powiązania</span><span class="sxs-lookup"><span data-stu-id="e5a97-147">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="e5a97-148">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="e5a97-148">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="e5a97-149">Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="e5a97-149">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="e5a97-150">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="e5a97-150">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="e5a97-151">Kolejki programu WCF</span><span class="sxs-lookup"><span data-stu-id="e5a97-151">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
