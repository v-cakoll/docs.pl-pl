---
title: '&lt;security&gt; w &lt;msmqIntegrationBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae5c68a8-14a2-4c6e-b9e0-3e94e3e9135e
caps.latest.revision: "13"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 9bca2fea17ecb0a2acbafed9f6093b7103a1adc5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltsecuritygt-of-ltmsmqintegrationbindinggt"></a><span data-ttu-id="7e926-102">&lt;security&gt; w &lt;msmqIntegrationBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="7e926-102">&lt;security&gt; of &lt;msmqIntegrationBinding&gt;</span></span>
<span data-ttu-id="7e926-103">Definiuje ustawienia zabezpieczeń transportu kanał integracji usługi kolejkowania komunikatów (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="7e926-103">Defines the transport security settings for the Message Queuing (MSMQ) integration channel.</span></span>  
  
 <span data-ttu-id="7e926-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="7e926-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7e926-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="7e926-105">\<bindings></span></span>  
<span data-ttu-id="7e926-106">msmqIntegrationBinding</span><span class="sxs-lookup"><span data-stu-id="7e926-106">msmqIntegrationBinding</span></span>  
<span data-ttu-id="7e926-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="7e926-107">\<binding></span></span>  
<span data-ttu-id="7e926-108">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="7e926-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e926-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="7e926-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7e926-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7e926-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7e926-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7e926-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7e926-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7e926-112">Attributes</span></span>  
  
|<span data-ttu-id="7e926-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="7e926-113">Attribute</span></span>|<span data-ttu-id="7e926-114">Opis</span><span class="sxs-lookup"><span data-stu-id="7e926-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7e926-115">tryb</span><span class="sxs-lookup"><span data-stu-id="7e926-115">mode</span></span>|<span data-ttu-id="7e926-116">Określa typ zabezpieczeń tej kontroli integralności, poufność i uwierzytelnianie z kanał integracji usługi kolejkowania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="7e926-116">Specifies the type of security that controls integrity, confidentiality and authentication with the Message Queuing integration channel.</span></span> <span data-ttu-id="7e926-117">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="7e926-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="7e926-118">-Brak: Powoduje wyłączenie zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="7e926-118">-   None: This disables security.</span></span><br /><span data-ttu-id="7e926-119">-Transport: Ochrony i uwierzytelniania są oferowane przez transport.</span><span class="sxs-lookup"><span data-stu-id="7e926-119">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="7e926-120">Dotyczy to zabezpieczenia wiadomości między menedżerami kolejki dwa.</span><span class="sxs-lookup"><span data-stu-id="7e926-120">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="7e926-121">Nie ma żadnych zabezpieczeń oferowany między aplikacją a menedżera kolejek.</span><span class="sxs-lookup"><span data-stu-id="7e926-121">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="7e926-122">Istniejące aplikacje usługi Msmq są taką samą funkcję z tym typem tryb zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="7e926-122">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><br /> <span data-ttu-id="7e926-123">Wartość domyślna to `Transport`.</span><span class="sxs-lookup"><span data-stu-id="7e926-123">The default value is `Transport`.</span></span> <span data-ttu-id="7e926-124">Ten atrybut jest typu <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="7e926-124">This attribute is of type <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7e926-125">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7e926-125">Child Elements</span></span>  
  
|<span data-ttu-id="7e926-126">Element</span><span class="sxs-lookup"><span data-stu-id="7e926-126">Element</span></span>|<span data-ttu-id="7e926-127">Opis</span><span class="sxs-lookup"><span data-stu-id="7e926-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7e926-128">\<transport ></span><span class="sxs-lookup"><span data-stu-id="7e926-128">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-msmqintegrationbinding.md)|<span data-ttu-id="7e926-129">Definiuje ustawienia zabezpieczeń transport integracji usługi kolejkowania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="7e926-129">Defines the security settings for the Message Queuing integration transport.</span></span> <span data-ttu-id="7e926-130">Ten element jest typu <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="7e926-130">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7e926-131">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7e926-131">Parent Elements</span></span>  
  
|<span data-ttu-id="7e926-132">Element</span><span class="sxs-lookup"><span data-stu-id="7e926-132">Element</span></span>|<span data-ttu-id="7e926-133">Opis</span><span class="sxs-lookup"><span data-stu-id="7e926-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7e926-134">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="7e926-134">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="7e926-135">Element powiązania [ \<msmqIntegrationBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md).</span><span class="sxs-lookup"><span data-stu-id="7e926-135">The binding element of the [\<msmqIntegrationBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7e926-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7e926-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement>  
 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.MsmqIntegrationBindingElement.Security%2A>  
 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>  
 [<span data-ttu-id="7e926-137">Kolejki programu WCF</span><span class="sxs-lookup"><span data-stu-id="7e926-137">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [<span data-ttu-id="7e926-138">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="7e926-138">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="7e926-139">Powiązania</span><span class="sxs-lookup"><span data-stu-id="7e926-139">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="7e926-140">Konfigurowanie powiązań dostarczanych przez System</span><span class="sxs-lookup"><span data-stu-id="7e926-140">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="7e926-141">Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="7e926-141">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="7e926-142">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="7e926-142">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="7e926-143">\<msmqIntegrationBinding ></span><span class="sxs-lookup"><span data-stu-id="7e926-143">\<msmqIntegrationBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md)
