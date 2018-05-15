---
title: '&lt;security&gt; w &lt;netMsmqBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 001d11a9-7439-498c-b09d-fca20eaf8cd3
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 0ed1021bdc45d0d64a20ff19410ad56e0d304ed3
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltsecuritygt-of-ltnetmsmqbindinggt"></a><span data-ttu-id="102ef-102">&lt;security&gt; w &lt;netMsmqBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="102ef-102">&lt;security&gt; of &lt;netMsmqBinding&gt;</span></span>
<span data-ttu-id="102ef-103">Definiuje ustawienia zabezpieczeń dla powiązania usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="102ef-103">Defines the security settings for a MSMQ binding.</span></span> <span data-ttu-id="102ef-104">Określa, czy włączono transportu lub zabezpieczeń protokołu SOAP, a jeśli tak, poziomy tryb i ochrony uwierzytelniania są używane.</span><span class="sxs-lookup"><span data-stu-id="102ef-104">It specifies whether transport or SOAP security is enabled and, if so, what authentication mode and protection levels are in use.</span></span>  
  
 <span data-ttu-id="102ef-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="102ef-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="102ef-106">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="102ef-106">\<bindings></span></span>  
<span data-ttu-id="102ef-107">\<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="102ef-107">\<netMsmqBinding></span></span>  
<span data-ttu-id="102ef-108">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="102ef-108">\<binding></span></span>  
<span data-ttu-id="102ef-109">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="102ef-109">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="102ef-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="102ef-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="102ef-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="102ef-111">Attributes and Elements</span></span>  
 <span data-ttu-id="102ef-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="102ef-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="102ef-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="102ef-113">Attributes</span></span>  
  
|<span data-ttu-id="102ef-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="102ef-114">Attribute</span></span>|<span data-ttu-id="102ef-115">Opis</span><span class="sxs-lookup"><span data-stu-id="102ef-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="102ef-116">tryb</span><span class="sxs-lookup"><span data-stu-id="102ef-116">mode</span></span>|<span data-ttu-id="102ef-117">Określa typ zabezpieczeń, która kontroluje, integralności i poufności uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="102ef-117">Specifies the type of security that controls integrity, confidentiality and authentication.</span></span> <span data-ttu-id="102ef-118">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="102ef-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="102ef-119">-Brak: Powoduje wyłączenie zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="102ef-119">-   None: This disables security.</span></span><br /><span data-ttu-id="102ef-120">-Transport: Ochrony i uwierzytelniania są oferowane przez transport.</span><span class="sxs-lookup"><span data-stu-id="102ef-120">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="102ef-121">Dotyczy to zabezpieczenia wiadomości między menedżerami kolejki dwa.</span><span class="sxs-lookup"><span data-stu-id="102ef-121">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="102ef-122">Nie ma żadnych zabezpieczeń oferowany między aplikacją a menedżera kolejek.</span><span class="sxs-lookup"><span data-stu-id="102ef-122">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="102ef-123">Istniejące aplikacje usługi Msmq są taką samą funkcję z tym typem tryb zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="102ef-123">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><span data-ttu-id="102ef-124">-Komunikat o błędzie: Określa trasie zabezpieczeń aplikacji.</span><span class="sxs-lookup"><span data-stu-id="102ef-124">-   Message: Specifies end-end application security.</span></span> <span data-ttu-id="102ef-125">Nie ma żadnych zabezpieczeń oferowanych w warstwie transportowej.</span><span class="sxs-lookup"><span data-stu-id="102ef-125">There is no security offered at the transport layer.</span></span> <span data-ttu-id="102ef-126">Jest to podobne do zabezpieczeń oferowanych przez inne standardowe powiązania.</span><span class="sxs-lookup"><span data-stu-id="102ef-126">This is similar to the security offered by other standard bindings.</span></span><br /><span data-ttu-id="102ef-127">-Zarówno: Oferuje zabezpieczeń transportu i protokołu SOAP wiadomości warstwy.</span><span class="sxs-lookup"><span data-stu-id="102ef-127">-   Both: Offers security at both the transport and SOAP messaging layer.</span></span> <span data-ttu-id="102ef-128">Tych samych poświadczeń jest wymagany na obu poziomach.</span><span class="sxs-lookup"><span data-stu-id="102ef-128">The same credential is required at both the levels.</span></span><br /><br /> <span data-ttu-id="102ef-129">Wartość domyślna to transportu.</span><span class="sxs-lookup"><span data-stu-id="102ef-129">The default value is Transport.</span></span> <span data-ttu-id="102ef-130">Ten atrybut jest typu <xref:System.ServiceModel.NetMsmqSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="102ef-130">This attribute is of type <xref:System.ServiceModel.NetMsmqSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="102ef-131">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="102ef-131">Child Elements</span></span>  
  
|<span data-ttu-id="102ef-132">Element</span><span class="sxs-lookup"><span data-stu-id="102ef-132">Element</span></span>|<span data-ttu-id="102ef-133">Opis</span><span class="sxs-lookup"><span data-stu-id="102ef-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="102ef-134">\<message></span><span class="sxs-lookup"><span data-stu-id="102ef-134">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-netmsmqbinding.md)|<span data-ttu-id="102ef-135">Definiuje ustawienia zabezpieczeń wiadomości protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="102ef-135">Defines the SOAP message security settings.</span></span> <span data-ttu-id="102ef-136">Ten element jest typu <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>.</span><span class="sxs-lookup"><span data-stu-id="102ef-136">This element is of type <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>.</span></span>|  
|[<span data-ttu-id="102ef-137">\<transport ></span><span class="sxs-lookup"><span data-stu-id="102ef-137">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-netmsmqbinding.md)|<span data-ttu-id="102ef-138">Definiuje ustawienia zabezpieczeń dla transportu MSMQ.</span><span class="sxs-lookup"><span data-stu-id="102ef-138">Defines the security settings for the MSMQ transport.</span></span> <span data-ttu-id="102ef-139">Ten element jest typu <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="102ef-139">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="102ef-140">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="102ef-140">Parent Elements</span></span>  
  
|<span data-ttu-id="102ef-141">Element</span><span class="sxs-lookup"><span data-stu-id="102ef-141">Element</span></span>|<span data-ttu-id="102ef-142">Opis</span><span class="sxs-lookup"><span data-stu-id="102ef-142">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="102ef-143">powiązanie</span><span class="sxs-lookup"><span data-stu-id="102ef-143">binding</span></span>|<span data-ttu-id="102ef-144">Element powiązania [ \<netMsmqBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)</span><span class="sxs-lookup"><span data-stu-id="102ef-144">The binding element of the [\<netMsmqBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="102ef-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="102ef-145">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement>  
 <xref:System.ServiceModel.NetMsmqBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetMsmqBindingElement.Security%2A>  
 <xref:System.ServiceModel.NetMsmqSecurity>  
 [<span data-ttu-id="102ef-146">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="102ef-146">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="102ef-147">Powiązania</span><span class="sxs-lookup"><span data-stu-id="102ef-147">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="102ef-148">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="102ef-148">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="102ef-149">Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="102ef-149">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="102ef-150">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="102ef-150">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="102ef-151">Kolejki programu WCF</span><span class="sxs-lookup"><span data-stu-id="102ef-151">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
