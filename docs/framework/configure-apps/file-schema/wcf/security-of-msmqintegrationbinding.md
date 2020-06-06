---
title: <security> dla <msmqIntegrationBinding>
ms.date: 03/30/2017
ms.assetid: ae5c68a8-14a2-4c6e-b9e0-3e94e3e9135e
ms.openlocfilehash: 2268bf48a2b86c3b3b25db006e6f8f55ea33af73
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738682"
---
# <a name="security-of-msmqintegrationbinding"></a><span data-ttu-id="f45bf-102">\<security> dla \<msmqIntegrationBinding></span><span class="sxs-lookup"><span data-stu-id="f45bf-102">\<security> of \<msmqIntegrationBinding></span></span>
<span data-ttu-id="f45bf-103">Definiuje ustawienia zabezpieczeń transportu dla kanału integracji usługi kolejkowania komunikatów (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="f45bf-103">Defines the transport security settings for the Message Queuing (MSMQ) integration channel.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<msmqIntegrationBinding>**](msmqintegrationbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="f45bf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f45bf-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f45bf-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f45bf-105">Attributes and Elements</span></span>  
 <span data-ttu-id="f45bf-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f45bf-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f45bf-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f45bf-107">Attributes</span></span>  
  
|<span data-ttu-id="f45bf-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f45bf-108">Attribute</span></span>|<span data-ttu-id="f45bf-109">Opis</span><span class="sxs-lookup"><span data-stu-id="f45bf-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f45bf-110">tryb</span><span class="sxs-lookup"><span data-stu-id="f45bf-110">mode</span></span>|<span data-ttu-id="f45bf-111">Określa typ zabezpieczeń, który kontroluje integralność, poufność i uwierzytelnianie przy użyciu kanału integracji usługi kolejkowania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="f45bf-111">Specifies the type of security that controls integrity, confidentiality and authentication with the Message Queuing integration channel.</span></span> <span data-ttu-id="f45bf-112">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="f45bf-112">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="f45bf-113">-Brak: spowoduje to wyłączenie zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="f45bf-113">-   None: This disables security.</span></span><br /><span data-ttu-id="f45bf-114">-Transport: Ochrona i uwierzytelnianie są oferowane przez transport.</span><span class="sxs-lookup"><span data-stu-id="f45bf-114">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="f45bf-115">Ma to zastosowanie do zabezpieczeń komunikatów między dwoma menedżerami kolejki.</span><span class="sxs-lookup"><span data-stu-id="f45bf-115">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="f45bf-116">Nie ma żadnych zabezpieczeń oferowanych między aplikacją a menedżerem kolejki.</span><span class="sxs-lookup"><span data-stu-id="f45bf-116">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="f45bf-117">Istniejące aplikacje MSMQ są funkcjonalnie równoważne z tego typu trybem zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="f45bf-117">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><br /> <span data-ttu-id="f45bf-118">Wartość domyślna to `Transport`.</span><span class="sxs-lookup"><span data-stu-id="f45bf-118">The default value is `Transport`.</span></span> <span data-ttu-id="f45bf-119">Ten atrybut jest typu <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="f45bf-119">This attribute is of type <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f45bf-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f45bf-120">Child Elements</span></span>  
  
|<span data-ttu-id="f45bf-121">Element</span><span class="sxs-lookup"><span data-stu-id="f45bf-121">Element</span></span>|<span data-ttu-id="f45bf-122">Opis</span><span class="sxs-lookup"><span data-stu-id="f45bf-122">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-msmqintegrationbinding.md)|<span data-ttu-id="f45bf-123">Definiuje ustawienia zabezpieczeń dla transportu integracji usługi kolejkowania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="f45bf-123">Defines the security settings for the Message Queuing integration transport.</span></span> <span data-ttu-id="f45bf-124">Ten element jest typu <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="f45bf-124">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f45bf-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f45bf-125">Parent Elements</span></span>  
  
|<span data-ttu-id="f45bf-126">Element</span><span class="sxs-lookup"><span data-stu-id="f45bf-126">Element</span></span>|<span data-ttu-id="f45bf-127">Opis</span><span class="sxs-lookup"><span data-stu-id="f45bf-127">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="f45bf-128">Element Binding elementu [\<msmqIntegrationBinding>](msmqintegrationbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="f45bf-128">The binding element of the [\<msmqIntegrationBinding>](msmqintegrationbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f45bf-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f45bf-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.MsmqIntegrationBindingElement.Security%2A>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>
- [<span data-ttu-id="f45bf-130">Kolejki programu WCF</span><span class="sxs-lookup"><span data-stu-id="f45bf-130">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="f45bf-131">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="f45bf-131">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="f45bf-132">Powiązania</span><span class="sxs-lookup"><span data-stu-id="f45bf-132">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f45bf-133">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="f45bf-133">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="f45bf-134">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="f45bf-134">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- [\<msmqIntegrationBinding>](msmqintegrationbinding.md)
