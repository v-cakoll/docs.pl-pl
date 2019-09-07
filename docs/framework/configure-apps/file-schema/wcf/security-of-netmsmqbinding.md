---
title: <security> dla <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 001d11a9-7439-498c-b09d-fca20eaf8cd3
ms.openlocfilehash: c780b157d0d566e24c6826c253401a51fbfab69d
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399840"
---
# <a name="security-of-netmsmqbinding"></a><span data-ttu-id="7f371-102">\<> \<zabezpieczeń usługi msmqbinding ></span><span class="sxs-lookup"><span data-stu-id="7f371-102">\<security> of \<netMsmqBinding></span></span>
<span data-ttu-id="7f371-103">Definiuje ustawienia zabezpieczeń dla powiązania usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="7f371-103">Defines the security settings for a MSMQ binding.</span></span> <span data-ttu-id="7f371-104">Określa, czy zabezpieczenia transportu lub protokołu SOAP są włączone i, jeśli tak, jakiego trybu uwierzytelniania i poziomów ochrony są używane.</span><span class="sxs-lookup"><span data-stu-id="7f371-104">It specifies whether transport or SOAP security is enabled and, if so, what authentication mode and protection levels are in use.</span></span>  
  
<span data-ttu-id="7f371-105">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7f371-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7f371-106">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="7f371-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="7f371-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> powiązań**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="7f371-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="7f371-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> usługi Msmqbinding**](netmsmqbinding.md)</span><span class="sxs-lookup"><span data-stu-id="7f371-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netMsmqBinding>**](netmsmqbinding.md)</span></span>\
<span data-ttu-id="7f371-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> powiązania**</span><span class="sxs-lookup"><span data-stu-id="7f371-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="7f371-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> zabezpieczeń**</span><span class="sxs-lookup"><span data-stu-id="7f371-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f371-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="7f371-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7f371-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7f371-112">Attributes and Elements</span></span>  
 <span data-ttu-id="7f371-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7f371-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7f371-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7f371-114">Attributes</span></span>  
  
|<span data-ttu-id="7f371-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="7f371-115">Attribute</span></span>|<span data-ttu-id="7f371-116">Opis</span><span class="sxs-lookup"><span data-stu-id="7f371-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7f371-117">tryb</span><span class="sxs-lookup"><span data-stu-id="7f371-117">mode</span></span>|<span data-ttu-id="7f371-118">Określa typ zabezpieczeń, który kontroluje integralność, poufność i uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="7f371-118">Specifies the type of security that controls integrity, confidentiality and authentication.</span></span> <span data-ttu-id="7f371-119">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="7f371-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="7f371-120">Dawaj Spowoduje to wyłączenie zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="7f371-120">-   None: This disables security.</span></span><br /><span data-ttu-id="7f371-121">Transportu Ochrona i uwierzytelnianie są oferowane przez transport.</span><span class="sxs-lookup"><span data-stu-id="7f371-121">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="7f371-122">Ma to zastosowanie do zabezpieczeń komunikatów między dwoma menedżerami kolejki.</span><span class="sxs-lookup"><span data-stu-id="7f371-122">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="7f371-123">Nie ma żadnych zabezpieczeń oferowanych między aplikacją a menedżerem kolejki.</span><span class="sxs-lookup"><span data-stu-id="7f371-123">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="7f371-124">Istniejące aplikacje MSMQ są funkcjonalnie równoważne z tego typu trybem zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="7f371-124">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><span data-ttu-id="7f371-125">Pojawi Określa zabezpieczenia aplikacji końcowej.</span><span class="sxs-lookup"><span data-stu-id="7f371-125">-   Message: Specifies end-end application security.</span></span> <span data-ttu-id="7f371-126">Warstwa transportu nie oferuje żadnych zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="7f371-126">There is no security offered at the transport layer.</span></span> <span data-ttu-id="7f371-127">Jest to podobne do zabezpieczeń oferowanych przez inne powiązania standardowe.</span><span class="sxs-lookup"><span data-stu-id="7f371-127">This is similar to the security offered by other standard bindings.</span></span><br /><span data-ttu-id="7f371-128">Jedn Oferuje zabezpieczenia zarówno dla warstwy transportu, jak i protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="7f371-128">-   Both: Offers security at both the transport and SOAP messaging layer.</span></span> <span data-ttu-id="7f371-129">To samo poświadczenie jest wymagane na poziomie.</span><span class="sxs-lookup"><span data-stu-id="7f371-129">The same credential is required at both the levels.</span></span><br /><br /> <span data-ttu-id="7f371-130">Wartością domyślną jest transport.</span><span class="sxs-lookup"><span data-stu-id="7f371-130">The default value is Transport.</span></span> <span data-ttu-id="7f371-131">Ten atrybut jest typu <xref:System.ServiceModel.NetMsmqSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="7f371-131">This attribute is of type <xref:System.ServiceModel.NetMsmqSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7f371-132">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7f371-132">Child Elements</span></span>  
  
|<span data-ttu-id="7f371-133">Element</span><span class="sxs-lookup"><span data-stu-id="7f371-133">Element</span></span>|<span data-ttu-id="7f371-134">Opis</span><span class="sxs-lookup"><span data-stu-id="7f371-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7f371-135">\<message></span><span class="sxs-lookup"><span data-stu-id="7f371-135">\<message></span></span>](message-of-netmsmqbinding.md)|<span data-ttu-id="7f371-136">Definiuje ustawienia zabezpieczeń wiadomości protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="7f371-136">Defines the SOAP message security settings.</span></span> <span data-ttu-id="7f371-137">Ten element jest typu <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>.</span><span class="sxs-lookup"><span data-stu-id="7f371-137">This element is of type <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>.</span></span>|  
|[<span data-ttu-id="7f371-138">\<> transportu</span><span class="sxs-lookup"><span data-stu-id="7f371-138">\<transport></span></span>](transport-of-netmsmqbinding.md)|<span data-ttu-id="7f371-139">Definiuje ustawienia zabezpieczeń dla transportu MSMQ.</span><span class="sxs-lookup"><span data-stu-id="7f371-139">Defines the security settings for the MSMQ transport.</span></span> <span data-ttu-id="7f371-140">Ten element jest typu <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="7f371-140">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7f371-141">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7f371-141">Parent Elements</span></span>  
  
|<span data-ttu-id="7f371-142">Element</span><span class="sxs-lookup"><span data-stu-id="7f371-142">Element</span></span>|<span data-ttu-id="7f371-143">Opis</span><span class="sxs-lookup"><span data-stu-id="7f371-143">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7f371-144">powiązanie</span><span class="sxs-lookup"><span data-stu-id="7f371-144">binding</span></span>|<span data-ttu-id="7f371-145">Element Binding elementu [ \<webmsmqbinding >](netmsmqbinding.md)</span><span class="sxs-lookup"><span data-stu-id="7f371-145">The binding element of the [\<netMsmqBinding>](netmsmqbinding.md)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7f371-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7f371-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement>
- <xref:System.ServiceModel.NetMsmqBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetMsmqBindingElement.Security%2A>
- <xref:System.ServiceModel.NetMsmqSecurity>
- [<span data-ttu-id="7f371-147">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="7f371-147">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="7f371-148">Powiązania</span><span class="sxs-lookup"><span data-stu-id="7f371-148">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="7f371-149">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="7f371-149">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="7f371-150">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="7f371-150">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="7f371-151">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="7f371-151">\<binding></span></span>](../../../misc/binding.md)
- [<span data-ttu-id="7f371-152">Kolejki programu WCF</span><span class="sxs-lookup"><span data-stu-id="7f371-152">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
