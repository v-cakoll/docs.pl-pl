---
title: <serviceCertificate><clientCredentials>elementu
ms.date: 03/30/2017
ms.assetid: e50c0ac5-f0df-4c90-b54b-fc602c1f84ea
ms.openlocfilehash: 4c7489a171bdd5cb4b747ca99f1b7ff6dd65517b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399686"
---
# <a name="servicecertificate-of-clientcredentials-element"></a><span data-ttu-id="03328-102">\<serviceCertificate>\<clientCredentials>elementu</span><span class="sxs-lookup"><span data-stu-id="03328-102">\<serviceCertificate> of \<clientCredentials> Element</span></span>
<span data-ttu-id="03328-103">Określa certyfikat, który ma być używany podczas uwierzytelniania usługi dla klienta.</span><span class="sxs-lookup"><span data-stu-id="03328-103">Specifies a certificate to use when authenticating a service to the client.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceCertificate>**  
  
## <a name="syntax"></a><span data-ttu-id="03328-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="03328-104">Syntax</span></span>  
  
```xml  
<serviceCertificate />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="03328-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="03328-105">Attributes and Elements</span></span>  
 <span data-ttu-id="03328-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="03328-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="03328-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="03328-107">Attributes</span></span>  
 <span data-ttu-id="03328-108">Brak.</span><span class="sxs-lookup"><span data-stu-id="03328-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="03328-109">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="03328-109">Child Elements</span></span>  
  
|<span data-ttu-id="03328-110">Element</span><span class="sxs-lookup"><span data-stu-id="03328-110">Element</span></span>|<span data-ttu-id="03328-111">Opis</span><span class="sxs-lookup"><span data-stu-id="03328-111">Description</span></span>|  
|-------------|-----------------|  
|[\<defaultCertificate>](defaultcertificate-element.md)|<span data-ttu-id="03328-112">Określa certyfikat X. 509, który ma być używany, gdy usługa lub STS nie zapewnia go za pośrednictwem protokołu negocjacji.</span><span class="sxs-lookup"><span data-stu-id="03328-112">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>|  
|[\<scopedCertificates>](scopedcertificates-element.md)|<span data-ttu-id="03328-113">Reprezentuje kolekcję certyfikatów X. 509 dostarczonych przez określone usługi (w zakresie) do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="03328-113">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span> <span data-ttu-id="03328-114">Ta kolekcja jest zwykle używana do określania certyfikatów usługi dla usług tokenów zabezpieczających w scenariuszu federacyjnym.</span><span class="sxs-lookup"><span data-stu-id="03328-114">This collection is typically used to specify the service certificates for Security Token Services in a federated scenario.</span></span>|  
|[\<authentication>](authentication-of-servicecertificate-element.md)|<span data-ttu-id="03328-115">Określa zachowania uwierzytelniania dla certyfikatów usługi używanych przez klienta programu.</span><span class="sxs-lookup"><span data-stu-id="03328-115">Specifies authentication behaviors for service certificates used by a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="03328-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="03328-116">Parent Elements</span></span>  
  
|<span data-ttu-id="03328-117">Element</span><span class="sxs-lookup"><span data-stu-id="03328-117">Element</span></span>|<span data-ttu-id="03328-118">Opis</span><span class="sxs-lookup"><span data-stu-id="03328-118">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|<span data-ttu-id="03328-119">Określa poświadczenia używane przez klienta do samodzielnego uwierzytelnienia w usłudze.</span><span class="sxs-lookup"><span data-stu-id="03328-119">Specifies the credentials used by the client to authenticate itself to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="03328-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="03328-120">Remarks</span></span>  
 <span data-ttu-id="03328-121">Ten element konfiguracji określa ustawienia używane przez klienta do weryfikowania certyfikatu przedstawionego przez usługę przy użyciu uwierzytelniania SSL.</span><span class="sxs-lookup"><span data-stu-id="03328-121">This configuration element specifies the settings used by the client to validate the certificate presented by the service using SSL authentication.</span></span> <span data-ttu-id="03328-122">Zawiera również certyfikat dla usługi, która jest jawnie skonfigurowana na kliencie do szyfrowania komunikatów w usłudze przy użyciu zabezpieczeń komunikatów.</span><span class="sxs-lookup"><span data-stu-id="03328-122">It also contains any certificate for the service that is explicitly configured on the client to use for encrypting messages to the service using message security.</span></span>  
  
 <span data-ttu-id="03328-123">Atrybuty `serviceCertificate` elementu są identyczne z atrybutami [\<clientCertificate>](clientcertificate-of-clientcredentials-element.md) .</span><span class="sxs-lookup"><span data-stu-id="03328-123">The attributes of the `serviceCertificate` element are identical to the attributes of the [\<clientCertificate>](clientcertificate-of-clientcredentials-element.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03328-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="03328-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ServiceCertificate%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- [<span data-ttu-id="03328-125">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="03328-125">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="03328-126">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="03328-126">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="03328-127">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="03328-127">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="03328-128">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="03328-128">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
