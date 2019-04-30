---
title: <security> dla <msmqIntegrationBinding>
ms.date: 03/30/2017
ms.assetid: ae5c68a8-14a2-4c6e-b9e0-3e94e3e9135e
ms.openlocfilehash: 8d79523db2a1567283b934abbd3de1adbbe6b0b5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61670537"
---
# <a name="security-of-msmqintegrationbinding"></a><span data-ttu-id="75b6a-102">\<Zabezpieczenia > z \<msmqIntegrationBinding ></span><span class="sxs-lookup"><span data-stu-id="75b6a-102">\<security> of \<msmqIntegrationBinding></span></span>
<span data-ttu-id="75b6a-103">Określa ustawienia zabezpieczenia transportu dla kanału Integracja usługi kolejkowania komunikatów (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="75b6a-103">Defines the transport security settings for the Message Queuing (MSMQ) integration channel.</span></span>  
  
 <span data-ttu-id="75b6a-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="75b6a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="75b6a-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="75b6a-105">\<bindings></span></span>  
<span data-ttu-id="75b6a-106">msmqIntegrationBinding</span><span class="sxs-lookup"><span data-stu-id="75b6a-106">msmqIntegrationBinding</span></span>  
<span data-ttu-id="75b6a-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="75b6a-107">\<binding></span></span>  
<span data-ttu-id="75b6a-108">\<security></span><span class="sxs-lookup"><span data-stu-id="75b6a-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75b6a-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="75b6a-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="75b6a-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="75b6a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="75b6a-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="75b6a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="75b6a-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="75b6a-112">Attributes</span></span>  
  
|<span data-ttu-id="75b6a-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="75b6a-113">Attribute</span></span>|<span data-ttu-id="75b6a-114">Opis</span><span class="sxs-lookup"><span data-stu-id="75b6a-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="75b6a-115">tryb</span><span class="sxs-lookup"><span data-stu-id="75b6a-115">mode</span></span>|<span data-ttu-id="75b6a-116">Określa typ zabezpieczeń tej kontroli integralności, poufność i uwierzytelnianie za pomocą kanału Integracja usługi kolejkowania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="75b6a-116">Specifies the type of security that controls integrity, confidentiality and authentication with the Message Queuing integration channel.</span></span> <span data-ttu-id="75b6a-117">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="75b6a-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="75b6a-118">-Brak: Powoduje to wyłączenie zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="75b6a-118">-   None: This disables security.</span></span><br /><span data-ttu-id="75b6a-119">-Transport: Ochrona i uwierzytelniania są oferowane przez transportu.</span><span class="sxs-lookup"><span data-stu-id="75b6a-119">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="75b6a-120">Dotyczy to zabezpieczeń wiadomości między menedżerami kolejki dwa.</span><span class="sxs-lookup"><span data-stu-id="75b6a-120">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="75b6a-121">Nie ma żadnych zabezpieczeń udostępniane między aplikacją i Menedżer kolejki.</span><span class="sxs-lookup"><span data-stu-id="75b6a-121">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="75b6a-122">Istniejące aplikacje usługi Msmq są funkcjonalnie równoważne z tym typem tryb zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="75b6a-122">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><br /> <span data-ttu-id="75b6a-123">Wartość domyślna to `Transport`.</span><span class="sxs-lookup"><span data-stu-id="75b6a-123">The default value is `Transport`.</span></span> <span data-ttu-id="75b6a-124">Ten atrybut jest typu <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="75b6a-124">This attribute is of type <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="75b6a-125">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="75b6a-125">Child Elements</span></span>  
  
|<span data-ttu-id="75b6a-126">Element</span><span class="sxs-lookup"><span data-stu-id="75b6a-126">Element</span></span>|<span data-ttu-id="75b6a-127">Opis</span><span class="sxs-lookup"><span data-stu-id="75b6a-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="75b6a-128">\<transport></span><span class="sxs-lookup"><span data-stu-id="75b6a-128">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-msmqintegrationbinding.md)|<span data-ttu-id="75b6a-129">Definiuje ustawienia zabezpieczeń transport integracji usługi kolejkowania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="75b6a-129">Defines the security settings for the Message Queuing integration transport.</span></span> <span data-ttu-id="75b6a-130">Ten element jest typu <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="75b6a-130">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="75b6a-131">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="75b6a-131">Parent Elements</span></span>  
  
|<span data-ttu-id="75b6a-132">Element</span><span class="sxs-lookup"><span data-stu-id="75b6a-132">Element</span></span>|<span data-ttu-id="75b6a-133">Opis</span><span class="sxs-lookup"><span data-stu-id="75b6a-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="75b6a-134">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="75b6a-134">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="75b6a-135">Element powiązania [ \<msmqIntegrationBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md).</span><span class="sxs-lookup"><span data-stu-id="75b6a-135">The binding element of the [\<msmqIntegrationBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="75b6a-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="75b6a-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.MsmqIntegrationBindingElement.Security%2A>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>
- [<span data-ttu-id="75b6a-137">Kolejki programu WCF</span><span class="sxs-lookup"><span data-stu-id="75b6a-137">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="75b6a-138">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="75b6a-138">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="75b6a-139">Powiązania</span><span class="sxs-lookup"><span data-stu-id="75b6a-139">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="75b6a-140">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="75b6a-140">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="75b6a-141">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="75b6a-141">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="75b6a-142">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="75b6a-142">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
- [<span data-ttu-id="75b6a-143">\<msmqIntegrationBinding></span><span class="sxs-lookup"><span data-stu-id="75b6a-143">\<msmqIntegrationBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md)
