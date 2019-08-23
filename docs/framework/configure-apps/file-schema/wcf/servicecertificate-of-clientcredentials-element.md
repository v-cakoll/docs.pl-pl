---
title: <serviceCertificate><clientCredentials> elementu
ms.date: 03/30/2017
ms.assetid: e50c0ac5-f0df-4c90-b54b-fc602c1f84ea
ms.openlocfilehash: a3013d0f7efd3014892cf6400447d708809c5fcd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936340"
---
# <a name="servicecertificate-of-clientcredentials-element"></a><span data-ttu-id="22f74-102">\<> serviceCertificate obiektu \<ClientCredentials > elementu</span><span class="sxs-lookup"><span data-stu-id="22f74-102">\<serviceCertificate> of \<clientCredentials> Element</span></span>
<span data-ttu-id="22f74-103">Określa certyfikat, który ma być używany podczas uwierzytelniania usługi dla klienta.</span><span class="sxs-lookup"><span data-stu-id="22f74-103">Specifies a certificate to use when authenticating a service to the client.</span></span>  
  
 <span data-ttu-id="22f74-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="22f74-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="22f74-105">\<> zachowań</span><span class="sxs-lookup"><span data-stu-id="22f74-105">\<behaviors></span></span>  
<span data-ttu-id="22f74-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="22f74-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="22f74-107">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="22f74-107">\<behavior></span></span>  
<span data-ttu-id="22f74-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="22f74-108">\<clientCredentials></span></span>  
<span data-ttu-id="22f74-109">\<> serviceCertificate</span><span class="sxs-lookup"><span data-stu-id="22f74-109">\<serviceCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22f74-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="22f74-110">Syntax</span></span>  
  
```xml  
<serviceCertificate />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="22f74-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="22f74-111">Attributes and Elements</span></span>  
 <span data-ttu-id="22f74-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="22f74-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="22f74-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="22f74-113">Attributes</span></span>  
 <span data-ttu-id="22f74-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="22f74-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="22f74-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="22f74-115">Child Elements</span></span>  
  
|<span data-ttu-id="22f74-116">Element</span><span class="sxs-lookup"><span data-stu-id="22f74-116">Element</span></span>|<span data-ttu-id="22f74-117">Opis</span><span class="sxs-lookup"><span data-stu-id="22f74-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="22f74-118">\<defaultCertificate></span><span class="sxs-lookup"><span data-stu-id="22f74-118">\<defaultCertificate></span></span>](defaultcertificate-element.md)|<span data-ttu-id="22f74-119">Określa certyfikat X. 509, który ma być używany, gdy usługa lub STS nie zapewnia go za pośrednictwem protokołu negocjacji.</span><span class="sxs-lookup"><span data-stu-id="22f74-119">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>|  
|[<span data-ttu-id="22f74-120">\<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="22f74-120">\<scopedCertificates></span></span>](scopedcertificates-element.md)|<span data-ttu-id="22f74-121">Reprezentuje kolekcję certyfikatów X. 509 dostarczonych przez określone usługi (w zakresie) do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="22f74-121">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span> <span data-ttu-id="22f74-122">Ta kolekcja jest zwykle używana do określania certyfikatów usługi dla usług tokenów zabezpieczających w scenariuszu federacyjnym.</span><span class="sxs-lookup"><span data-stu-id="22f74-122">This collection is typically used to specify the service certificates for Security Token Services in a federated scenario.</span></span>|  
|[<span data-ttu-id="22f74-123">\<> uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="22f74-123">\<authentication></span></span>](authentication-of-servicecertificate-element.md)|<span data-ttu-id="22f74-124">Określa zachowania uwierzytelniania dla certyfikatów usługi używanych przez klienta programu.</span><span class="sxs-lookup"><span data-stu-id="22f74-124">Specifies authentication behaviors for service certificates used by a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="22f74-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="22f74-125">Parent Elements</span></span>  
  
|<span data-ttu-id="22f74-126">Element</span><span class="sxs-lookup"><span data-stu-id="22f74-126">Element</span></span>|<span data-ttu-id="22f74-127">Opis</span><span class="sxs-lookup"><span data-stu-id="22f74-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="22f74-128">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="22f74-128">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="22f74-129">Określa poświadczenia używane przez klienta do samodzielnego uwierzytelnienia w usłudze.</span><span class="sxs-lookup"><span data-stu-id="22f74-129">Specifies the credentials used by the client to authenticate itself to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="22f74-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="22f74-130">Remarks</span></span>  
 <span data-ttu-id="22f74-131">Ten element konfiguracji określa ustawienia używane przez klienta do weryfikowania certyfikatu przedstawionego przez usługę przy użyciu uwierzytelniania SSL.</span><span class="sxs-lookup"><span data-stu-id="22f74-131">This configuration element specifies the settings used by the client to validate the certificate presented by the service using SSL authentication.</span></span> <span data-ttu-id="22f74-132">Zawiera również certyfikat dla usługi, która jest jawnie skonfigurowana na kliencie do szyfrowania komunikatów w usłudze przy użyciu zabezpieczeń komunikatów.</span><span class="sxs-lookup"><span data-stu-id="22f74-132">It also contains any certificate for the service that is explicitly configured on the client to use for encrypting messages to the service using message security.</span></span>  
  
 <span data-ttu-id="22f74-133">Atrybuty `serviceCertificate` elementu są identyczne z atrybutami [ \<ClientCertificate >](clientcertificate-of-clientcredentials-element.md).</span><span class="sxs-lookup"><span data-stu-id="22f74-133">The attributes of the `serviceCertificate` element are identical to the attributes of the [\<clientCertificate>](clientcertificate-of-clientcredentials-element.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22f74-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="22f74-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ServiceCertificate%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- [<span data-ttu-id="22f74-135">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="22f74-135">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="22f74-136">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="22f74-136">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="22f74-137">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="22f74-137">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="22f74-138">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="22f74-138">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
