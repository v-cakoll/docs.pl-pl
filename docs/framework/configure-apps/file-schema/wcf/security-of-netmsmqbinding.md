---
title: <security> dla <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 001d11a9-7439-498c-b09d-fca20eaf8cd3
ms.openlocfilehash: 1bbc3a460ce707e71b72a469af2e03acd8dc79e5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936686"
---
# <a name="security-of-netmsmqbinding"></a><span data-ttu-id="baf65-102">\<> \<zabezpieczeń usługi msmqbinding ></span><span class="sxs-lookup"><span data-stu-id="baf65-102">\<security> of \<netMsmqBinding></span></span>
<span data-ttu-id="baf65-103">Definiuje ustawienia zabezpieczeń dla powiązania usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="baf65-103">Defines the security settings for a MSMQ binding.</span></span> <span data-ttu-id="baf65-104">Określa, czy zabezpieczenia transportu lub protokołu SOAP są włączone i, jeśli tak, jakiego trybu uwierzytelniania i poziomów ochrony są używane.</span><span class="sxs-lookup"><span data-stu-id="baf65-104">It specifies whether transport or SOAP security is enabled and, if so, what authentication mode and protection levels are in use.</span></span>  
  
 <span data-ttu-id="baf65-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="baf65-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="baf65-106">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="baf65-106">\<bindings></span></span>  
<span data-ttu-id="baf65-107">\<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="baf65-107">\<netMsmqBinding></span></span>  
<span data-ttu-id="baf65-108">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="baf65-108">\<binding></span></span>  
<span data-ttu-id="baf65-109">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="baf65-109">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="baf65-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="baf65-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="baf65-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="baf65-111">Attributes and Elements</span></span>  
 <span data-ttu-id="baf65-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="baf65-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="baf65-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="baf65-113">Attributes</span></span>  
  
|<span data-ttu-id="baf65-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="baf65-114">Attribute</span></span>|<span data-ttu-id="baf65-115">Opis</span><span class="sxs-lookup"><span data-stu-id="baf65-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="baf65-116">tryb</span><span class="sxs-lookup"><span data-stu-id="baf65-116">mode</span></span>|<span data-ttu-id="baf65-117">Określa typ zabezpieczeń, który kontroluje integralność, poufność i uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="baf65-117">Specifies the type of security that controls integrity, confidentiality and authentication.</span></span> <span data-ttu-id="baf65-118">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="baf65-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="baf65-119">Dawaj Spowoduje to wyłączenie zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="baf65-119">-   None: This disables security.</span></span><br /><span data-ttu-id="baf65-120">Transportu Ochrona i uwierzytelnianie są oferowane przez transport.</span><span class="sxs-lookup"><span data-stu-id="baf65-120">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="baf65-121">Ma to zastosowanie do zabezpieczeń komunikatów między dwoma menedżerami kolejki.</span><span class="sxs-lookup"><span data-stu-id="baf65-121">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="baf65-122">Nie ma żadnych zabezpieczeń oferowanych między aplikacją a menedżerem kolejki.</span><span class="sxs-lookup"><span data-stu-id="baf65-122">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="baf65-123">Istniejące aplikacje MSMQ są funkcjonalnie równoważne z tego typu trybem zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="baf65-123">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><span data-ttu-id="baf65-124">Pojawi Określa zabezpieczenia aplikacji końcowej.</span><span class="sxs-lookup"><span data-stu-id="baf65-124">-   Message: Specifies end-end application security.</span></span> <span data-ttu-id="baf65-125">Warstwa transportu nie oferuje żadnych zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="baf65-125">There is no security offered at the transport layer.</span></span> <span data-ttu-id="baf65-126">Jest to podobne do zabezpieczeń oferowanych przez inne powiązania standardowe.</span><span class="sxs-lookup"><span data-stu-id="baf65-126">This is similar to the security offered by other standard bindings.</span></span><br /><span data-ttu-id="baf65-127">Jedn Oferuje zabezpieczenia zarówno dla warstwy transportu, jak i protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="baf65-127">-   Both: Offers security at both the transport and SOAP messaging layer.</span></span> <span data-ttu-id="baf65-128">To samo poświadczenie jest wymagane na poziomie.</span><span class="sxs-lookup"><span data-stu-id="baf65-128">The same credential is required at both the levels.</span></span><br /><br /> <span data-ttu-id="baf65-129">Wartością domyślną jest transport.</span><span class="sxs-lookup"><span data-stu-id="baf65-129">The default value is Transport.</span></span> <span data-ttu-id="baf65-130">Ten atrybut jest typu <xref:System.ServiceModel.NetMsmqSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="baf65-130">This attribute is of type <xref:System.ServiceModel.NetMsmqSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="baf65-131">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="baf65-131">Child Elements</span></span>  
  
|<span data-ttu-id="baf65-132">Element</span><span class="sxs-lookup"><span data-stu-id="baf65-132">Element</span></span>|<span data-ttu-id="baf65-133">Opis</span><span class="sxs-lookup"><span data-stu-id="baf65-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="baf65-134">\<message></span><span class="sxs-lookup"><span data-stu-id="baf65-134">\<message></span></span>](message-of-netmsmqbinding.md)|<span data-ttu-id="baf65-135">Definiuje ustawienia zabezpieczeń wiadomości protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="baf65-135">Defines the SOAP message security settings.</span></span> <span data-ttu-id="baf65-136">Ten element jest typu <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>.</span><span class="sxs-lookup"><span data-stu-id="baf65-136">This element is of type <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>.</span></span>|  
|[<span data-ttu-id="baf65-137">\<> transportu</span><span class="sxs-lookup"><span data-stu-id="baf65-137">\<transport></span></span>](transport-of-netmsmqbinding.md)|<span data-ttu-id="baf65-138">Definiuje ustawienia zabezpieczeń dla transportu MSMQ.</span><span class="sxs-lookup"><span data-stu-id="baf65-138">Defines the security settings for the MSMQ transport.</span></span> <span data-ttu-id="baf65-139">Ten element jest typu <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="baf65-139">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="baf65-140">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="baf65-140">Parent Elements</span></span>  
  
|<span data-ttu-id="baf65-141">Element</span><span class="sxs-lookup"><span data-stu-id="baf65-141">Element</span></span>|<span data-ttu-id="baf65-142">Opis</span><span class="sxs-lookup"><span data-stu-id="baf65-142">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="baf65-143">powiązanie</span><span class="sxs-lookup"><span data-stu-id="baf65-143">binding</span></span>|<span data-ttu-id="baf65-144">Element Binding elementu [ \<webmsmqbinding >](netmsmqbinding.md)</span><span class="sxs-lookup"><span data-stu-id="baf65-144">The binding element of the [\<netMsmqBinding>](netmsmqbinding.md)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="baf65-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="baf65-145">See also</span></span>

- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement>
- <xref:System.ServiceModel.NetMsmqBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetMsmqBindingElement.Security%2A>
- <xref:System.ServiceModel.NetMsmqSecurity>
- [<span data-ttu-id="baf65-146">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="baf65-146">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="baf65-147">Powiązania</span><span class="sxs-lookup"><span data-stu-id="baf65-147">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="baf65-148">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="baf65-148">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="baf65-149">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="baf65-149">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="baf65-150">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="baf65-150">\<binding></span></span>](../../../misc/binding.md)
- [<span data-ttu-id="baf65-151">Kolejki programu WCF</span><span class="sxs-lookup"><span data-stu-id="baf65-151">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
