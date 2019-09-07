---
title: <security> dla <msmqIntegrationBinding>
ms.date: 03/30/2017
ms.assetid: ae5c68a8-14a2-4c6e-b9e0-3e94e3e9135e
ms.openlocfilehash: e4f10ab994429c6cbb690caef38114b8340e6839
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399865"
---
# <a name="security-of-msmqintegrationbinding"></a><span data-ttu-id="18c04-102">\<zabezpieczenia > \<MsmqIntegrationBinding ></span><span class="sxs-lookup"><span data-stu-id="18c04-102">\<security> of \<msmqIntegrationBinding></span></span>
<span data-ttu-id="18c04-103">Definiuje ustawienia zabezpieczeń transportu dla kanału integracji usługi kolejkowania komunikatów (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="18c04-103">Defines the transport security settings for the Message Queuing (MSMQ) integration channel.</span></span>  
  
<span data-ttu-id="18c04-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="18c04-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="18c04-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="18c04-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="18c04-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> powiązań**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="18c04-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="18c04-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<msmqIntegrationBinding >** ](msmqintegrationbinding.md)</span><span class="sxs-lookup"><span data-stu-id="18c04-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<msmqIntegrationBinding>**](msmqintegrationbinding.md)</span></span>\
<span data-ttu-id="18c04-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> powiązania**</span><span class="sxs-lookup"><span data-stu-id="18c04-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="18c04-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> zabezpieczeń**</span><span class="sxs-lookup"><span data-stu-id="18c04-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18c04-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="18c04-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="18c04-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="18c04-111">Attributes and Elements</span></span>  
 <span data-ttu-id="18c04-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="18c04-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="18c04-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="18c04-113">Attributes</span></span>  
  
|<span data-ttu-id="18c04-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="18c04-114">Attribute</span></span>|<span data-ttu-id="18c04-115">Opis</span><span class="sxs-lookup"><span data-stu-id="18c04-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="18c04-116">tryb</span><span class="sxs-lookup"><span data-stu-id="18c04-116">mode</span></span>|<span data-ttu-id="18c04-117">Określa typ zabezpieczeń, który kontroluje integralność, poufność i uwierzytelnianie przy użyciu kanału integracji usługi kolejkowania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="18c04-117">Specifies the type of security that controls integrity, confidentiality and authentication with the Message Queuing integration channel.</span></span> <span data-ttu-id="18c04-118">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="18c04-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="18c04-119">Dawaj Spowoduje to wyłączenie zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="18c04-119">-   None: This disables security.</span></span><br /><span data-ttu-id="18c04-120">Transportu Ochrona i uwierzytelnianie są oferowane przez transport.</span><span class="sxs-lookup"><span data-stu-id="18c04-120">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="18c04-121">Ma to zastosowanie do zabezpieczeń komunikatów między dwoma menedżerami kolejki.</span><span class="sxs-lookup"><span data-stu-id="18c04-121">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="18c04-122">Nie ma żadnych zabezpieczeń oferowanych między aplikacją a menedżerem kolejki.</span><span class="sxs-lookup"><span data-stu-id="18c04-122">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="18c04-123">Istniejące aplikacje MSMQ są funkcjonalnie równoważne z tego typu trybem zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="18c04-123">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><br /> <span data-ttu-id="18c04-124">Wartość domyślna to `Transport`.</span><span class="sxs-lookup"><span data-stu-id="18c04-124">The default value is `Transport`.</span></span> <span data-ttu-id="18c04-125">Ten atrybut jest typu <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="18c04-125">This attribute is of type <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="18c04-126">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="18c04-126">Child Elements</span></span>  
  
|<span data-ttu-id="18c04-127">Element</span><span class="sxs-lookup"><span data-stu-id="18c04-127">Element</span></span>|<span data-ttu-id="18c04-128">Opis</span><span class="sxs-lookup"><span data-stu-id="18c04-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="18c04-129">\<> transportu</span><span class="sxs-lookup"><span data-stu-id="18c04-129">\<transport></span></span>](transport-of-msmqintegrationbinding.md)|<span data-ttu-id="18c04-130">Definiuje ustawienia zabezpieczeń dla transportu integracji usługi kolejkowania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="18c04-130">Defines the security settings for the Message Queuing integration transport.</span></span> <span data-ttu-id="18c04-131">Ten element jest typu <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="18c04-131">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="18c04-132">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="18c04-132">Parent Elements</span></span>  
  
|<span data-ttu-id="18c04-133">Element</span><span class="sxs-lookup"><span data-stu-id="18c04-133">Element</span></span>|<span data-ttu-id="18c04-134">Opis</span><span class="sxs-lookup"><span data-stu-id="18c04-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="18c04-135">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="18c04-135">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="18c04-136">Element Binding elementu [ \<MsmqIntegrationBinding >](msmqintegrationbinding.md).</span><span class="sxs-lookup"><span data-stu-id="18c04-136">The binding element of the [\<msmqIntegrationBinding>](msmqintegrationbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="18c04-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="18c04-137">See also</span></span>

- <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.MsmqIntegrationBindingElement.Security%2A>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>
- [<span data-ttu-id="18c04-138">Kolejki programu WCF</span><span class="sxs-lookup"><span data-stu-id="18c04-138">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="18c04-139">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="18c04-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="18c04-140">Powiązania</span><span class="sxs-lookup"><span data-stu-id="18c04-140">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="18c04-141">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="18c04-141">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="18c04-142">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="18c04-142">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="18c04-143">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="18c04-143">\<binding></span></span>](../../../misc/binding.md)
- [<span data-ttu-id="18c04-144">\<msmqIntegrationBinding></span><span class="sxs-lookup"><span data-stu-id="18c04-144">\<msmqIntegrationBinding></span></span>](msmqintegrationbinding.md)
