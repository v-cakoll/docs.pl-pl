---
title: <security> z <msmqIntegrationBinding>
ms.date: 03/30/2017
ms.assetid: ae5c68a8-14a2-4c6e-b9e0-3e94e3e9135e
ms.openlocfilehash: ceda00615ae579edb0360006bb70acd11716ce6a
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55275174"
---
# <a name="security-of-msmqintegrationbinding"></a><span data-ttu-id="ca7d0-102">\<Zabezpieczenia > z \<msmqIntegrationBinding ></span><span class="sxs-lookup"><span data-stu-id="ca7d0-102">\<security> of \<msmqIntegrationBinding></span></span>
<span data-ttu-id="ca7d0-103">Określa ustawienia zabezpieczenia transportu dla kanału Integracja usługi kolejkowania komunikatów (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="ca7d0-103">Defines the transport security settings for the Message Queuing (MSMQ) integration channel.</span></span>  
  
 <span data-ttu-id="ca7d0-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ca7d0-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ca7d0-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="ca7d0-105">\<bindings></span></span>  
<span data-ttu-id="ca7d0-106">msmqIntegrationBinding</span><span class="sxs-lookup"><span data-stu-id="ca7d0-106">msmqIntegrationBinding</span></span>  
<span data-ttu-id="ca7d0-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="ca7d0-107">\<binding></span></span>  
<span data-ttu-id="ca7d0-108">\<security></span><span class="sxs-lookup"><span data-stu-id="ca7d0-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca7d0-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="ca7d0-109">Syntax</span></span>  
  
```xml  
<msmqIntegrationBinding>
  <binding>
    <security mode="None/Transport">
      <transport msmqAuthenticationMode="None/Windows/Certificate"
                 msmqEncryptionAlgorithm="RC4Stream/AES"
                 msmqProtectionLevel="None/Sign/EncryptAndSign"
                 msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
      <message algorithmSuite="Aes128/Aes192/Aes256/Rsa15Aes128/ Rsa15Aes256/TripleDes"
               clientCredentialType="None/Windows/UserName/Certificate/CardSpace"
               defaultProtectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</msmqIntegrationBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ca7d0-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ca7d0-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ca7d0-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ca7d0-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ca7d0-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ca7d0-112">Attributes</span></span>  
  
|<span data-ttu-id="ca7d0-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ca7d0-113">Attribute</span></span>|<span data-ttu-id="ca7d0-114">Opis</span><span class="sxs-lookup"><span data-stu-id="ca7d0-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ca7d0-115">tryb</span><span class="sxs-lookup"><span data-stu-id="ca7d0-115">mode</span></span>|<span data-ttu-id="ca7d0-116">Określa typ zabezpieczeń tej kontroli integralności, poufność i uwierzytelnianie za pomocą kanału Integracja usługi kolejkowania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="ca7d0-116">Specifies the type of security that controls integrity, confidentiality and authentication with the Message Queuing integration channel.</span></span> <span data-ttu-id="ca7d0-117">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="ca7d0-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="ca7d0-118">-Brak: Powoduje to wyłączenie zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="ca7d0-118">-   None: This disables security.</span></span><br /><span data-ttu-id="ca7d0-119">-Transport: Ochrona i uwierzytelniania są oferowane przez transportu.</span><span class="sxs-lookup"><span data-stu-id="ca7d0-119">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="ca7d0-120">Dotyczy to zabezpieczeń wiadomości między menedżerami kolejki dwa.</span><span class="sxs-lookup"><span data-stu-id="ca7d0-120">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="ca7d0-121">Nie ma żadnych zabezpieczeń udostępniane między aplikacją i Menedżer kolejki.</span><span class="sxs-lookup"><span data-stu-id="ca7d0-121">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="ca7d0-122">Istniejące aplikacje usługi Msmq są funkcjonalnie równoważne z tym typem tryb zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="ca7d0-122">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><br /> <span data-ttu-id="ca7d0-123">Wartość domyślna to `Transport`.</span><span class="sxs-lookup"><span data-stu-id="ca7d0-123">The default value is `Transport`.</span></span> <span data-ttu-id="ca7d0-124">Ten atrybut jest typu <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="ca7d0-124">This attribute is of type <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ca7d0-125">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ca7d0-125">Child Elements</span></span>  
  
|<span data-ttu-id="ca7d0-126">Element</span><span class="sxs-lookup"><span data-stu-id="ca7d0-126">Element</span></span>|<span data-ttu-id="ca7d0-127">Opis</span><span class="sxs-lookup"><span data-stu-id="ca7d0-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ca7d0-128">\<transport></span><span class="sxs-lookup"><span data-stu-id="ca7d0-128">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-msmqintegrationbinding.md)|<span data-ttu-id="ca7d0-129">Definiuje ustawienia zabezpieczeń transport integracji usługi kolejkowania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="ca7d0-129">Defines the security settings for the Message Queuing integration transport.</span></span> <span data-ttu-id="ca7d0-130">Ten element jest typu <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="ca7d0-130">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ca7d0-131">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ca7d0-131">Parent Elements</span></span>  
  
|<span data-ttu-id="ca7d0-132">Element</span><span class="sxs-lookup"><span data-stu-id="ca7d0-132">Element</span></span>|<span data-ttu-id="ca7d0-133">Opis</span><span class="sxs-lookup"><span data-stu-id="ca7d0-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ca7d0-134">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="ca7d0-134">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="ca7d0-135">Element powiązania [ \<msmqIntegrationBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md).</span><span class="sxs-lookup"><span data-stu-id="ca7d0-135">The binding element of the [\<msmqIntegrationBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ca7d0-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ca7d0-136">See also</span></span>
- <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.MsmqIntegrationBindingElement.Security%2A>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>
- [<span data-ttu-id="ca7d0-137">Kolejki programu WCF</span><span class="sxs-lookup"><span data-stu-id="ca7d0-137">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="ca7d0-138">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="ca7d0-138">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="ca7d0-139">Powiązania</span><span class="sxs-lookup"><span data-stu-id="ca7d0-139">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="ca7d0-140">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="ca7d0-140">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="ca7d0-141">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="ca7d0-141">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="ca7d0-142">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="ca7d0-142">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
- [<span data-ttu-id="ca7d0-143">\<msmqIntegrationBinding></span><span class="sxs-lookup"><span data-stu-id="ca7d0-143">\<msmqIntegrationBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md)
