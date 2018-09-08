---
title: '&lt;security&gt; w &lt;msmqIntegrationBinding&gt;'
ms.date: 03/30/2017
ms.assetid: ae5c68a8-14a2-4c6e-b9e0-3e94e3e9135e
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 6419c2157281d00cf79de16d4f494fc52bcee598
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44195598"
---
# <a name="ltsecuritygt-of-ltmsmqintegrationbindinggt"></a><span data-ttu-id="d4497-102">&lt;security&gt; w &lt;msmqIntegrationBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="d4497-102">&lt;security&gt; of &lt;msmqIntegrationBinding&gt;</span></span>
<span data-ttu-id="d4497-103">Określa ustawienia zabezpieczenia transportu dla kanału Integracja usługi kolejkowania komunikatów (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="d4497-103">Defines the transport security settings for the Message Queuing (MSMQ) integration channel.</span></span>  
  
 <span data-ttu-id="d4497-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d4497-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d4497-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="d4497-105">\<bindings></span></span>  
<span data-ttu-id="d4497-106">msmqIntegrationBinding</span><span class="sxs-lookup"><span data-stu-id="d4497-106">msmqIntegrationBinding</span></span>  
<span data-ttu-id="d4497-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="d4497-107">\<binding></span></span>  
<span data-ttu-id="d4497-108">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="d4497-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4497-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="d4497-109">Syntax</span></span>  
  
```xml  
<msmqIntegrationBinding>  
   <binding>   
       <security mode="None/Transport">  
         <transport msmqAuthenticationMode="None/Windows/Certificate"  
            msmqEncryptionAlgorithm="RC4Stream/AES"  
            msmqProtectionLevel="None/Sign/EncryptAndSign"  
            msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />  
          <message  algorithmSuite="Aes128/Aes192/Aes256/Rsa15Aes128/ Rsa15Aes256/TripleDes"  
                        clientCredentialType="None/Windows/UserName/Certificate/CardSpace"  
            defaultProtectionLevel="None/Sign/EncryptAndSign" />  
       </security>  
   </binding>  
</msmqIntegrationBinding>   
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d4497-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d4497-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d4497-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d4497-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d4497-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d4497-112">Attributes</span></span>  
  
|<span data-ttu-id="d4497-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d4497-113">Attribute</span></span>|<span data-ttu-id="d4497-114">Opis</span><span class="sxs-lookup"><span data-stu-id="d4497-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d4497-115">tryb</span><span class="sxs-lookup"><span data-stu-id="d4497-115">mode</span></span>|<span data-ttu-id="d4497-116">Określa typ zabezpieczeń tej kontroli integralności, poufność i uwierzytelnianie za pomocą kanału Integracja usługi kolejkowania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="d4497-116">Specifies the type of security that controls integrity, confidentiality and authentication with the Message Queuing integration channel.</span></span> <span data-ttu-id="d4497-117">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="d4497-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="d4497-118">-Brak: Powoduje to wyłączenie zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="d4497-118">-   None: This disables security.</span></span><br /><span data-ttu-id="d4497-119">-Transport: Ochrony i uwierzytelniania oferowana przez transportu.</span><span class="sxs-lookup"><span data-stu-id="d4497-119">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="d4497-120">Dotyczy to zabezpieczeń wiadomości między menedżerami kolejki dwa.</span><span class="sxs-lookup"><span data-stu-id="d4497-120">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="d4497-121">Nie ma żadnych zabezpieczeń udostępniane między aplikacją i Menedżer kolejki.</span><span class="sxs-lookup"><span data-stu-id="d4497-121">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="d4497-122">Istniejące aplikacje usługi Msmq są funkcjonalnie równoważne z tym typem tryb zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="d4497-122">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><br /> <span data-ttu-id="d4497-123">Wartość domyślna to `Transport`.</span><span class="sxs-lookup"><span data-stu-id="d4497-123">The default value is `Transport`.</span></span> <span data-ttu-id="d4497-124">Ten atrybut jest typu <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="d4497-124">This attribute is of type <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d4497-125">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d4497-125">Child Elements</span></span>  
  
|<span data-ttu-id="d4497-126">Element</span><span class="sxs-lookup"><span data-stu-id="d4497-126">Element</span></span>|<span data-ttu-id="d4497-127">Opis</span><span class="sxs-lookup"><span data-stu-id="d4497-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d4497-128">\<transport ></span><span class="sxs-lookup"><span data-stu-id="d4497-128">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-msmqintegrationbinding.md)|<span data-ttu-id="d4497-129">Definiuje ustawienia zabezpieczeń transport integracji usługi kolejkowania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="d4497-129">Defines the security settings for the Message Queuing integration transport.</span></span> <span data-ttu-id="d4497-130">Ten element jest typu <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="d4497-130">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d4497-131">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d4497-131">Parent Elements</span></span>  
  
|<span data-ttu-id="d4497-132">Element</span><span class="sxs-lookup"><span data-stu-id="d4497-132">Element</span></span>|<span data-ttu-id="d4497-133">Opis</span><span class="sxs-lookup"><span data-stu-id="d4497-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d4497-134">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="d4497-134">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="d4497-135">Element powiązania [ \<msmqIntegrationBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md).</span><span class="sxs-lookup"><span data-stu-id="d4497-135">The binding element of the [\<msmqIntegrationBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d4497-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d4497-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement>  
 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.MsmqIntegrationBindingElement.Security%2A>  
 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>  
 [<span data-ttu-id="d4497-137">Kolejki programu WCF</span><span class="sxs-lookup"><span data-stu-id="d4497-137">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [<span data-ttu-id="d4497-138">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="d4497-138">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="d4497-139">Powiązania</span><span class="sxs-lookup"><span data-stu-id="d4497-139">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="d4497-140">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="d4497-140">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="d4497-141">Konfigurowanie Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="d4497-141">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="d4497-142">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="d4497-142">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="d4497-143">\<msmqIntegrationBinding></span><span class="sxs-lookup"><span data-stu-id="d4497-143">\<msmqIntegrationBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md)
