---
title: <security> dla <msmqIntegrationBinding>
ms.date: 03/30/2017
ms.assetid: ae5c68a8-14a2-4c6e-b9e0-3e94e3e9135e
ms.openlocfilehash: 5b74c95ef2933fcf7e8d49aed89d95acbd288b80
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936708"
---
# <a name="security-of-msmqintegrationbinding"></a><span data-ttu-id="87731-102">\<zabezpieczenia > \<MsmqIntegrationBinding ></span><span class="sxs-lookup"><span data-stu-id="87731-102">\<security> of \<msmqIntegrationBinding></span></span>
<span data-ttu-id="87731-103">Definiuje ustawienia zabezpieczeń transportu dla kanału integracji usługi kolejkowania komunikatów (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="87731-103">Defines the transport security settings for the Message Queuing (MSMQ) integration channel.</span></span>  
  
 <span data-ttu-id="87731-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="87731-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="87731-105">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="87731-105">\<bindings></span></span>  
<span data-ttu-id="87731-106">msmqIntegrationBinding</span><span class="sxs-lookup"><span data-stu-id="87731-106">msmqIntegrationBinding</span></span>  
<span data-ttu-id="87731-107">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="87731-107">\<binding></span></span>  
<span data-ttu-id="87731-108">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="87731-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87731-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="87731-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="87731-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="87731-110">Attributes and Elements</span></span>  
 <span data-ttu-id="87731-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="87731-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="87731-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="87731-112">Attributes</span></span>  
  
|<span data-ttu-id="87731-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="87731-113">Attribute</span></span>|<span data-ttu-id="87731-114">Opis</span><span class="sxs-lookup"><span data-stu-id="87731-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="87731-115">tryb</span><span class="sxs-lookup"><span data-stu-id="87731-115">mode</span></span>|<span data-ttu-id="87731-116">Określa typ zabezpieczeń, który kontroluje integralność, poufność i uwierzytelnianie przy użyciu kanału integracji usługi kolejkowania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="87731-116">Specifies the type of security that controls integrity, confidentiality and authentication with the Message Queuing integration channel.</span></span> <span data-ttu-id="87731-117">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="87731-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="87731-118">Dawaj Spowoduje to wyłączenie zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="87731-118">-   None: This disables security.</span></span><br /><span data-ttu-id="87731-119">Transportu Ochrona i uwierzytelnianie są oferowane przez transport.</span><span class="sxs-lookup"><span data-stu-id="87731-119">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="87731-120">Ma to zastosowanie do zabezpieczeń komunikatów między dwoma menedżerami kolejki.</span><span class="sxs-lookup"><span data-stu-id="87731-120">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="87731-121">Nie ma żadnych zabezpieczeń oferowanych między aplikacją a menedżerem kolejki.</span><span class="sxs-lookup"><span data-stu-id="87731-121">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="87731-122">Istniejące aplikacje MSMQ są funkcjonalnie równoważne z tego typu trybem zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="87731-122">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><br /> <span data-ttu-id="87731-123">Wartość domyślna to `Transport`.</span><span class="sxs-lookup"><span data-stu-id="87731-123">The default value is `Transport`.</span></span> <span data-ttu-id="87731-124">Ten atrybut jest typu <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="87731-124">This attribute is of type <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="87731-125">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="87731-125">Child Elements</span></span>  
  
|<span data-ttu-id="87731-126">Element</span><span class="sxs-lookup"><span data-stu-id="87731-126">Element</span></span>|<span data-ttu-id="87731-127">Opis</span><span class="sxs-lookup"><span data-stu-id="87731-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="87731-128">\<> transportu</span><span class="sxs-lookup"><span data-stu-id="87731-128">\<transport></span></span>](transport-of-msmqintegrationbinding.md)|<span data-ttu-id="87731-129">Definiuje ustawienia zabezpieczeń dla transportu integracji usługi kolejkowania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="87731-129">Defines the security settings for the Message Queuing integration transport.</span></span> <span data-ttu-id="87731-130">Ten element jest typu <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="87731-130">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="87731-131">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="87731-131">Parent Elements</span></span>  
  
|<span data-ttu-id="87731-132">Element</span><span class="sxs-lookup"><span data-stu-id="87731-132">Element</span></span>|<span data-ttu-id="87731-133">Opis</span><span class="sxs-lookup"><span data-stu-id="87731-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="87731-134">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="87731-134">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="87731-135">Element Binding elementu [ \<MsmqIntegrationBinding >](msmqintegrationbinding.md).</span><span class="sxs-lookup"><span data-stu-id="87731-135">The binding element of the [\<msmqIntegrationBinding>](msmqintegrationbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="87731-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="87731-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.MsmqIntegrationBindingElement.Security%2A>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>
- [<span data-ttu-id="87731-137">Kolejki programu WCF</span><span class="sxs-lookup"><span data-stu-id="87731-137">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="87731-138">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="87731-138">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="87731-139">Powiązania</span><span class="sxs-lookup"><span data-stu-id="87731-139">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="87731-140">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="87731-140">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="87731-141">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="87731-141">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="87731-142">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="87731-142">\<binding></span></span>](../../../misc/binding.md)
- [<span data-ttu-id="87731-143">\<msmqIntegrationBinding></span><span class="sxs-lookup"><span data-stu-id="87731-143">\<msmqIntegrationBinding></span></span>](msmqintegrationbinding.md)
