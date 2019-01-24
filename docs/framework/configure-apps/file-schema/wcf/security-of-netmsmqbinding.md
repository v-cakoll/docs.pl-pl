---
title: '&lt;security&gt; w &lt;netMsmqBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 001d11a9-7439-498c-b09d-fca20eaf8cd3
ms.openlocfilehash: 71f0c10c336a9682971bc774141cb0c3bd37c092
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54696389"
---
# <a name="ltsecuritygt-of-ltnetmsmqbindinggt"></a><span data-ttu-id="ca0af-102">&lt;security&gt; w &lt;netMsmqBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="ca0af-102">&lt;security&gt; of &lt;netMsmqBinding&gt;</span></span>
<span data-ttu-id="ca0af-103">Definiuje ustawienia zabezpieczeń dla powiązanie usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="ca0af-103">Defines the security settings for a MSMQ binding.</span></span> <span data-ttu-id="ca0af-104">Określa, czy włączono transportu lub zabezpieczeń protokołu SOAP, a jeśli tak, jakie poziomy tryb i ochrona uwierzytelniania są używane.</span><span class="sxs-lookup"><span data-stu-id="ca0af-104">It specifies whether transport or SOAP security is enabled and, if so, what authentication mode and protection levels are in use.</span></span>  
  
 <span data-ttu-id="ca0af-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ca0af-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="ca0af-106">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="ca0af-106">\<bindings></span></span>  
<span data-ttu-id="ca0af-107">\<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="ca0af-107">\<netMsmqBinding></span></span>  
<span data-ttu-id="ca0af-108">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="ca0af-108">\<binding></span></span>  
<span data-ttu-id="ca0af-109">\<security></span><span class="sxs-lookup"><span data-stu-id="ca0af-109">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca0af-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="ca0af-110">Syntax</span></span>  
  
```xml  
<security mode="None/Transport/Message/Both">
  <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"
             msmqEncryptionAlgorithm="RC4Stream/AES"
             msmqProtectionLevel="None/Sign/EncryptAndSign"
             msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
    <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
             clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ca0af-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ca0af-111">Attributes and Elements</span></span>  
 <span data-ttu-id="ca0af-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ca0af-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ca0af-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ca0af-113">Attributes</span></span>  
  
|<span data-ttu-id="ca0af-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ca0af-114">Attribute</span></span>|<span data-ttu-id="ca0af-115">Opis</span><span class="sxs-lookup"><span data-stu-id="ca0af-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ca0af-116">tryb</span><span class="sxs-lookup"><span data-stu-id="ca0af-116">mode</span></span>|<span data-ttu-id="ca0af-117">Określa typ bezpieczeństwa, kontrolujące integralności, poufności i uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="ca0af-117">Specifies the type of security that controls integrity, confidentiality and authentication.</span></span> <span data-ttu-id="ca0af-118">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="ca0af-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="ca0af-119">-Brak: Powoduje to wyłączenie zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="ca0af-119">-   None: This disables security.</span></span><br /><span data-ttu-id="ca0af-120">-Transport: Ochrona i uwierzytelniania są oferowane przez transportu.</span><span class="sxs-lookup"><span data-stu-id="ca0af-120">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="ca0af-121">Dotyczy to zabezpieczeń wiadomości między menedżerami kolejki dwa.</span><span class="sxs-lookup"><span data-stu-id="ca0af-121">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="ca0af-122">Nie ma żadnych zabezpieczeń udostępniane między aplikacją i Menedżer kolejki.</span><span class="sxs-lookup"><span data-stu-id="ca0af-122">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="ca0af-123">Istniejące aplikacje usługi Msmq są funkcjonalnie równoważne z tym typem tryb zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="ca0af-123">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><span data-ttu-id="ca0af-124">-Komunikat o błędzie: Określa kompleksowe zabezpieczenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ca0af-124">-   Message: Specifies end-end application security.</span></span> <span data-ttu-id="ca0af-125">Nie ma żadnych zabezpieczeń będzie oferowana w cenie warstwy transportowej.</span><span class="sxs-lookup"><span data-stu-id="ca0af-125">There is no security offered at the transport layer.</span></span> <span data-ttu-id="ca0af-126">Jest to podobne do zabezpieczeń oferowanych przez inne standardowe powiązania.</span><span class="sxs-lookup"><span data-stu-id="ca0af-126">This is similar to the security offered by other standard bindings.</span></span><br /><span data-ttu-id="ca0af-127">-Zarówno: Zapewnia bezpieczeństwo na transport i Warstwa obsługi wiadomości SOAP.</span><span class="sxs-lookup"><span data-stu-id="ca0af-127">-   Both: Offers security at both the transport and SOAP messaging layer.</span></span> <span data-ttu-id="ca0af-128">Te same poświadczenia jest wymagana na obu poziomach.</span><span class="sxs-lookup"><span data-stu-id="ca0af-128">The same credential is required at both the levels.</span></span><br /><br /> <span data-ttu-id="ca0af-129">Wartość domyślna to transportu.</span><span class="sxs-lookup"><span data-stu-id="ca0af-129">The default value is Transport.</span></span> <span data-ttu-id="ca0af-130">Ten atrybut jest typu <xref:System.ServiceModel.NetMsmqSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="ca0af-130">This attribute is of type <xref:System.ServiceModel.NetMsmqSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ca0af-131">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ca0af-131">Child Elements</span></span>  
  
|<span data-ttu-id="ca0af-132">Element</span><span class="sxs-lookup"><span data-stu-id="ca0af-132">Element</span></span>|<span data-ttu-id="ca0af-133">Opis</span><span class="sxs-lookup"><span data-stu-id="ca0af-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ca0af-134">\<message></span><span class="sxs-lookup"><span data-stu-id="ca0af-134">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-netmsmqbinding.md)|<span data-ttu-id="ca0af-135">Określa ustawienia zabezpieczenia wiadomości protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="ca0af-135">Defines the SOAP message security settings.</span></span> <span data-ttu-id="ca0af-136">Ten element jest typu <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>.</span><span class="sxs-lookup"><span data-stu-id="ca0af-136">This element is of type <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>.</span></span>|  
|[<span data-ttu-id="ca0af-137">\<transport></span><span class="sxs-lookup"><span data-stu-id="ca0af-137">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-netmsmqbinding.md)|<span data-ttu-id="ca0af-138">Definiuje ustawienia zabezpieczenia transportu usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="ca0af-138">Defines the security settings for the MSMQ transport.</span></span> <span data-ttu-id="ca0af-139">Ten element jest typu <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="ca0af-139">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ca0af-140">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ca0af-140">Parent Elements</span></span>  
  
|<span data-ttu-id="ca0af-141">Element</span><span class="sxs-lookup"><span data-stu-id="ca0af-141">Element</span></span>|<span data-ttu-id="ca0af-142">Opis</span><span class="sxs-lookup"><span data-stu-id="ca0af-142">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ca0af-143">powiązanie</span><span class="sxs-lookup"><span data-stu-id="ca0af-143">binding</span></span>|<span data-ttu-id="ca0af-144">Element powiązania [ \<netMsmqBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)</span><span class="sxs-lookup"><span data-stu-id="ca0af-144">The binding element of the [\<netMsmqBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ca0af-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ca0af-145">See also</span></span>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement>
- <xref:System.ServiceModel.NetMsmqBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetMsmqBindingElement.Security%2A>
- <xref:System.ServiceModel.NetMsmqSecurity>
- [<span data-ttu-id="ca0af-146">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="ca0af-146">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="ca0af-147">Powiązania</span><span class="sxs-lookup"><span data-stu-id="ca0af-147">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="ca0af-148">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="ca0af-148">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="ca0af-149">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="ca0af-149">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="ca0af-150">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="ca0af-150">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
- [<span data-ttu-id="ca0af-151">Kolejki programu WCF</span><span class="sxs-lookup"><span data-stu-id="ca0af-151">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
