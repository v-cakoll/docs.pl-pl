---
title: '&lt;serviceCertificate&gt; w &lt;clientCredentials&gt;, element'
ms.date: 03/30/2017
ms.assetid: e50c0ac5-f0df-4c90-b54b-fc602c1f84ea
ms.openlocfilehash: 1d54c39fd681e0686e419b7b73243703e9184d1f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32750248"
---
# <a name="ltservicecertificategt-of-ltclientcredentialsgt-element"></a><span data-ttu-id="6bab9-102">&lt;serviceCertificate&gt; w &lt;clientCredentials&gt;, element</span><span class="sxs-lookup"><span data-stu-id="6bab9-102">&lt;serviceCertificate&gt; of &lt;clientCredentials&gt; Element</span></span>
<span data-ttu-id="6bab9-103">Określa certyfikat używany podczas uwierzytelniania usługi do klienta.</span><span class="sxs-lookup"><span data-stu-id="6bab9-103">Specifies a certificate to use when authenticating a service to the client.</span></span>  
  
 <span data-ttu-id="6bab9-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="6bab9-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="6bab9-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="6bab9-105">\<behaviors></span></span>  
<span data-ttu-id="6bab9-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="6bab9-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="6bab9-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="6bab9-107">\<behavior></span></span>  
<span data-ttu-id="6bab9-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="6bab9-108">\<clientCredentials></span></span>  
<span data-ttu-id="6bab9-109">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="6bab9-109">\<serviceCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bab9-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="6bab9-110">Syntax</span></span>  
  
```xml  
<serviceCertificate />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6bab9-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6bab9-111">Attributes and Elements</span></span>  
 <span data-ttu-id="6bab9-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6bab9-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6bab9-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6bab9-113">Attributes</span></span>  
 <span data-ttu-id="6bab9-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="6bab9-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6bab9-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6bab9-115">Child Elements</span></span>  
  
|<span data-ttu-id="6bab9-116">Element</span><span class="sxs-lookup"><span data-stu-id="6bab9-116">Element</span></span>|<span data-ttu-id="6bab9-117">Opis</span><span class="sxs-lookup"><span data-stu-id="6bab9-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6bab9-118">\<defaultCertificate ></span><span class="sxs-lookup"><span data-stu-id="6bab9-118">\<defaultCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md)|<span data-ttu-id="6bab9-119">Określa certyfikat X.509 do użycia podczas usługa lub STS nie zapewnia go poprzez protokół negocjacji.</span><span class="sxs-lookup"><span data-stu-id="6bab9-119">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>|  
|[<span data-ttu-id="6bab9-120">\<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="6bab9-120">\<scopedCertificates></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md)|<span data-ttu-id="6bab9-121">Reprezentuje kolekcję certyfikatów X.509 dostarczonych przez określone usługi (w zakresie) do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="6bab9-121">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span> <span data-ttu-id="6bab9-122">Ta kolekcja jest zwykle można określić certyfikaty usługi dla usługi tokenu zabezpieczeń w federacyjnym scenariuszu.</span><span class="sxs-lookup"><span data-stu-id="6bab9-122">This collection is typically used to specify the service certificates for Security Token Services in a federated scenario.</span></span>|  
|[<span data-ttu-id="6bab9-123">\<Uwierzytelnianie ></span><span class="sxs-lookup"><span data-stu-id="6bab9-123">\<authentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md)|<span data-ttu-id="6bab9-124">Określa zachowania uwierzytelnienia dla certyfikatów usługi używany przez klienta.</span><span class="sxs-lookup"><span data-stu-id="6bab9-124">Specifies authentication behaviors for service certificates used by a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6bab9-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6bab9-125">Parent Elements</span></span>  
  
|<span data-ttu-id="6bab9-126">Element</span><span class="sxs-lookup"><span data-stu-id="6bab9-126">Element</span></span>|<span data-ttu-id="6bab9-127">Opis</span><span class="sxs-lookup"><span data-stu-id="6bab9-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6bab9-128">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="6bab9-128">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="6bab9-129">Określa poświadczenia używane przez klienta do samodzielnego uwierzytelnienia usługi.</span><span class="sxs-lookup"><span data-stu-id="6bab9-129">Specifies the credentials used by the client to authenticate itself to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6bab9-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6bab9-130">Remarks</span></span>  
 <span data-ttu-id="6bab9-131">Ten element konfiguracji określa ustawienia używane przez klienta do weryfikacji certyfikatu przedstawionego przez tę usługę, używając uwierzytelniania protokołu SSL.</span><span class="sxs-lookup"><span data-stu-id="6bab9-131">This configuration element specifies the settings used by the client to validate the certificate presented by the service using SSL authentication.</span></span> <span data-ttu-id="6bab9-132">Zawiera ona także dowolny certyfikat dla usługi jawnie skonfigurowanego na kliencie do użycia na potrzeby szyfrowania wiadomości w usłudze przy użyciu zabezpieczeń wiadomości.</span><span class="sxs-lookup"><span data-stu-id="6bab9-132">It also contains any certificate for the service that is explicitly configured on the client to use for encrypting messages to the service using message security.</span></span>  
  
 <span data-ttu-id="6bab9-133">Atrybuty `serviceCertificate` elementu są takie same atrybuty [ \<clientCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).</span><span class="sxs-lookup"><span data-stu-id="6bab9-133">The attributes of the `serviceCertificate` element are identical to the attributes of the [\<clientCertificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bab9-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6bab9-134">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ServiceCertificate%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>  
 <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>  
 [<span data-ttu-id="6bab9-135">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="6bab9-135">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="6bab9-136">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="6bab9-136">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="6bab9-137">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="6bab9-137">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="6bab9-138">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="6bab9-138">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
