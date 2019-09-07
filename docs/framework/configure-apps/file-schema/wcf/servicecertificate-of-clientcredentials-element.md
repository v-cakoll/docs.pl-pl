---
title: <serviceCertificate><clientCredentials> elementu
ms.date: 03/30/2017
ms.assetid: e50c0ac5-f0df-4c90-b54b-fc602c1f84ea
ms.openlocfilehash: 4c7489a171bdd5cb4b747ca99f1b7ff6dd65517b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399686"
---
# <a name="servicecertificate-of-clientcredentials-element"></a><span data-ttu-id="1f6b9-102">\<> serviceCertificate obiektu \<ClientCredentials > elementu</span><span class="sxs-lookup"><span data-stu-id="1f6b9-102">\<serviceCertificate> of \<clientCredentials> Element</span></span>
<span data-ttu-id="1f6b9-103">Określa certyfikat, który ma być używany podczas uwierzytelniania usługi dla klienta.</span><span class="sxs-lookup"><span data-stu-id="1f6b9-103">Specifies a certificate to use when authenticating a service to the client.</span></span>  
  
<span data-ttu-id="1f6b9-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1f6b9-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1f6b9-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="1f6b9-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="1f6b9-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowań**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="1f6b9-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="1f6b9-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="1f6b9-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="1f6b9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowania**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="1f6b9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="1f6b9-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Obiekt clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="1f6b9-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="1f6b9-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> serviceCertificate**</span><span class="sxs-lookup"><span data-stu-id="1f6b9-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceCertificate>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f6b9-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="1f6b9-111">Syntax</span></span>  
  
```xml  
<serviceCertificate />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1f6b9-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1f6b9-112">Attributes and Elements</span></span>  
 <span data-ttu-id="1f6b9-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1f6b9-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1f6b9-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1f6b9-114">Attributes</span></span>  
 <span data-ttu-id="1f6b9-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="1f6b9-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1f6b9-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1f6b9-116">Child Elements</span></span>  
  
|<span data-ttu-id="1f6b9-117">Element</span><span class="sxs-lookup"><span data-stu-id="1f6b9-117">Element</span></span>|<span data-ttu-id="1f6b9-118">Opis</span><span class="sxs-lookup"><span data-stu-id="1f6b9-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1f6b9-119">\<defaultCertificate></span><span class="sxs-lookup"><span data-stu-id="1f6b9-119">\<defaultCertificate></span></span>](defaultcertificate-element.md)|<span data-ttu-id="1f6b9-120">Określa certyfikat X. 509, który ma być używany, gdy usługa lub STS nie zapewnia go za pośrednictwem protokołu negocjacji.</span><span class="sxs-lookup"><span data-stu-id="1f6b9-120">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>|  
|[<span data-ttu-id="1f6b9-121">\<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="1f6b9-121">\<scopedCertificates></span></span>](scopedcertificates-element.md)|<span data-ttu-id="1f6b9-122">Reprezentuje kolekcję certyfikatów X. 509 dostarczonych przez określone usługi (w zakresie) do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="1f6b9-122">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span> <span data-ttu-id="1f6b9-123">Ta kolekcja jest zwykle używana do określania certyfikatów usługi dla usług tokenów zabezpieczających w scenariuszu federacyjnym.</span><span class="sxs-lookup"><span data-stu-id="1f6b9-123">This collection is typically used to specify the service certificates for Security Token Services in a federated scenario.</span></span>|  
|[<span data-ttu-id="1f6b9-124">\<> uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="1f6b9-124">\<authentication></span></span>](authentication-of-servicecertificate-element.md)|<span data-ttu-id="1f6b9-125">Określa zachowania uwierzytelniania dla certyfikatów usługi używanych przez klienta programu.</span><span class="sxs-lookup"><span data-stu-id="1f6b9-125">Specifies authentication behaviors for service certificates used by a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1f6b9-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1f6b9-126">Parent Elements</span></span>  
  
|<span data-ttu-id="1f6b9-127">Element</span><span class="sxs-lookup"><span data-stu-id="1f6b9-127">Element</span></span>|<span data-ttu-id="1f6b9-128">Opis</span><span class="sxs-lookup"><span data-stu-id="1f6b9-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1f6b9-129">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="1f6b9-129">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="1f6b9-130">Określa poświadczenia używane przez klienta do samodzielnego uwierzytelnienia w usłudze.</span><span class="sxs-lookup"><span data-stu-id="1f6b9-130">Specifies the credentials used by the client to authenticate itself to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1f6b9-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1f6b9-131">Remarks</span></span>  
 <span data-ttu-id="1f6b9-132">Ten element konfiguracji określa ustawienia używane przez klienta do weryfikowania certyfikatu przedstawionego przez usługę przy użyciu uwierzytelniania SSL.</span><span class="sxs-lookup"><span data-stu-id="1f6b9-132">This configuration element specifies the settings used by the client to validate the certificate presented by the service using SSL authentication.</span></span> <span data-ttu-id="1f6b9-133">Zawiera również certyfikat dla usługi, która jest jawnie skonfigurowana na kliencie do szyfrowania komunikatów w usłudze przy użyciu zabezpieczeń komunikatów.</span><span class="sxs-lookup"><span data-stu-id="1f6b9-133">It also contains any certificate for the service that is explicitly configured on the client to use for encrypting messages to the service using message security.</span></span>  
  
 <span data-ttu-id="1f6b9-134">Atrybuty `serviceCertificate` elementu są identyczne z atrybutami [ \<ClientCertificate >](clientcertificate-of-clientcredentials-element.md).</span><span class="sxs-lookup"><span data-stu-id="1f6b9-134">The attributes of the `serviceCertificate` element are identical to the attributes of the [\<clientCertificate>](clientcertificate-of-clientcredentials-element.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f6b9-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1f6b9-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ServiceCertificate%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- [<span data-ttu-id="1f6b9-136">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="1f6b9-136">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="1f6b9-137">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="1f6b9-137">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="1f6b9-138">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="1f6b9-138">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="1f6b9-139">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="1f6b9-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
