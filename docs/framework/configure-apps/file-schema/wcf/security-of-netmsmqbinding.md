---
title: <security> dla <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 001d11a9-7439-498c-b09d-fca20eaf8cd3
ms.openlocfilehash: 7877fd59aff581eee5b62a1ca224dbf51c956069
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738670"
---
# <a name="security-of-netmsmqbinding"></a><span data-ttu-id="6afb6-102">\<security> dla \<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="6afb6-102">\<security> of \<netMsmqBinding></span></span>
<span data-ttu-id="6afb6-103">Definiuje ustawienia zabezpieczeń dla powiązania usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="6afb6-103">Defines the security settings for a MSMQ binding.</span></span> <span data-ttu-id="6afb6-104">Określa, czy zabezpieczenia transportu lub protokołu SOAP są włączone i, jeśli tak, jakiego trybu uwierzytelniania i poziomów ochrony są używane.</span><span class="sxs-lookup"><span data-stu-id="6afb6-104">It specifies whether transport or SOAP security is enabled and, if so, what authentication mode and protection levels are in use.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netMsmqBinding>**](netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="6afb6-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="6afb6-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6afb6-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6afb6-106">Attributes and Elements</span></span>  
 <span data-ttu-id="6afb6-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6afb6-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6afb6-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6afb6-108">Attributes</span></span>  
  
|<span data-ttu-id="6afb6-109">Atrybut</span><span class="sxs-lookup"><span data-stu-id="6afb6-109">Attribute</span></span>|<span data-ttu-id="6afb6-110">Opis</span><span class="sxs-lookup"><span data-stu-id="6afb6-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6afb6-111">tryb</span><span class="sxs-lookup"><span data-stu-id="6afb6-111">mode</span></span>|<span data-ttu-id="6afb6-112">Określa typ zabezpieczeń, który kontroluje integralność, poufność i uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="6afb6-112">Specifies the type of security that controls integrity, confidentiality and authentication.</span></span> <span data-ttu-id="6afb6-113">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="6afb6-113">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="6afb6-114">-Brak: spowoduje to wyłączenie zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="6afb6-114">-   None: This disables security.</span></span><br /><span data-ttu-id="6afb6-115">-Transport: Ochrona i uwierzytelnianie są oferowane przez transport.</span><span class="sxs-lookup"><span data-stu-id="6afb6-115">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="6afb6-116">Ma to zastosowanie do zabezpieczeń komunikatów między dwoma menedżerami kolejki.</span><span class="sxs-lookup"><span data-stu-id="6afb6-116">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="6afb6-117">Nie ma żadnych zabezpieczeń oferowanych między aplikacją a menedżerem kolejki.</span><span class="sxs-lookup"><span data-stu-id="6afb6-117">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="6afb6-118">Istniejące aplikacje MSMQ są funkcjonalnie równoważne z tego typu trybem zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="6afb6-118">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><span data-ttu-id="6afb6-119">-Message: Określa zabezpieczenia aplikacji końcowej.</span><span class="sxs-lookup"><span data-stu-id="6afb6-119">-   Message: Specifies end-end application security.</span></span> <span data-ttu-id="6afb6-120">Warstwa transportu nie oferuje żadnych zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="6afb6-120">There is no security offered at the transport layer.</span></span> <span data-ttu-id="6afb6-121">Jest to podobne do zabezpieczeń oferowanych przez inne powiązania standardowe.</span><span class="sxs-lookup"><span data-stu-id="6afb6-121">This is similar to the security offered by other standard bindings.</span></span><br /><span data-ttu-id="6afb6-122">-Both: oferuje zabezpieczenia zarówno dla warstwy transportu, jak i protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="6afb6-122">-   Both: Offers security at both the transport and SOAP messaging layer.</span></span> <span data-ttu-id="6afb6-123">To samo poświadczenie jest wymagane na poziomie.</span><span class="sxs-lookup"><span data-stu-id="6afb6-123">The same credential is required at both the levels.</span></span><br /><br /> <span data-ttu-id="6afb6-124">Wartością domyślną jest transport.</span><span class="sxs-lookup"><span data-stu-id="6afb6-124">The default value is Transport.</span></span> <span data-ttu-id="6afb6-125">Ten atrybut jest typu <xref:System.ServiceModel.NetMsmqSecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="6afb6-125">This attribute is of type <xref:System.ServiceModel.NetMsmqSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6afb6-126">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6afb6-126">Child Elements</span></span>  
  
|<span data-ttu-id="6afb6-127">Element</span><span class="sxs-lookup"><span data-stu-id="6afb6-127">Element</span></span>|<span data-ttu-id="6afb6-128">Opis</span><span class="sxs-lookup"><span data-stu-id="6afb6-128">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-of-netmsmqbinding.md)|<span data-ttu-id="6afb6-129">Definiuje ustawienia zabezpieczeń wiadomości protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="6afb6-129">Defines the SOAP message security settings.</span></span> <span data-ttu-id="6afb6-130">Ten element jest typu <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement> .</span><span class="sxs-lookup"><span data-stu-id="6afb6-130">This element is of type <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>.</span></span>|  
|[\<transport>](transport-of-netmsmqbinding.md)|<span data-ttu-id="6afb6-131">Definiuje ustawienia zabezpieczeń dla transportu MSMQ.</span><span class="sxs-lookup"><span data-stu-id="6afb6-131">Defines the security settings for the MSMQ transport.</span></span> <span data-ttu-id="6afb6-132">Ten element jest typu <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="6afb6-132">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6afb6-133">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6afb6-133">Parent Elements</span></span>  
  
|<span data-ttu-id="6afb6-134">Element</span><span class="sxs-lookup"><span data-stu-id="6afb6-134">Element</span></span>|<span data-ttu-id="6afb6-135">Opis</span><span class="sxs-lookup"><span data-stu-id="6afb6-135">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6afb6-136">powiązanie</span><span class="sxs-lookup"><span data-stu-id="6afb6-136">binding</span></span>|<span data-ttu-id="6afb6-137">Element Binding elementu[\<netMsmqBinding>](netmsmqbinding.md)</span><span class="sxs-lookup"><span data-stu-id="6afb6-137">The binding element of the [\<netMsmqBinding>](netmsmqbinding.md)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6afb6-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6afb6-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement>
- <xref:System.ServiceModel.NetMsmqBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetMsmqBindingElement.Security%2A>
- <xref:System.ServiceModel.NetMsmqSecurity>
- [<span data-ttu-id="6afb6-139">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="6afb6-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="6afb6-140">Powiązania</span><span class="sxs-lookup"><span data-stu-id="6afb6-140">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="6afb6-141">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="6afb6-141">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="6afb6-142">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="6afb6-142">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- [<span data-ttu-id="6afb6-143">Kolejki programu WCF</span><span class="sxs-lookup"><span data-stu-id="6afb6-143">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
