---
title: <clientCredentials>
ms.date: 03/30/2017
ms.assetid: 1e6eef0d-a34e-4d74-b0f7-f65d2181858d
ms.openlocfilehash: f295fe48e194611c80b78c0c23ab3e66ea1c0b64
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400497"
---
# \<clientCredentials>
<span data-ttu-id="87f85-101">Określa poświadczenia używane do uwierzytelniania klienta w usłudze.</span><span class="sxs-lookup"><span data-stu-id="87f85-101">Specifies the credentials used to authenticate the client to a service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clientCredentials>**  
  
## <a name="syntax"></a><span data-ttu-id="87f85-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="87f85-102">Syntax</span></span>  
  
```xml  
<clientCredentials type="String"
                   supportInteractive="Boolean" >
  <clientCertificate>
  </clientCertificate>
  <digest>
  </digest>
  <isuedToken>
  </isuedToken>
  <peer>
  </peer>
  <serviceCertificate>
  </serviceCertificate>
  <windowsAuthentication>
  </windowsAuthentication>
</clientCredentials>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="87f85-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="87f85-103">Attributes and Elements</span></span>  
 <span data-ttu-id="87f85-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="87f85-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="87f85-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="87f85-105">Attributes</span></span>  
  
|<span data-ttu-id="87f85-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="87f85-106">Attribute</span></span>|<span data-ttu-id="87f85-107">Opis</span><span class="sxs-lookup"><span data-stu-id="87f85-107">Description</span></span>|  
|---------------|-----------------|  
|`supportInteractive`|<span data-ttu-id="87f85-108">Wartość logiczna określająca, czy użytkownik interaktywny może uczestniczyć w wyborze poświadczenia klienta w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="87f85-108">A Boolean value that specifies whether an interactive user can be involved in selecting a client credential at runtime.</span></span> <span data-ttu-id="87f85-109">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="87f85-109">The default value is `true`.</span></span>|  
|`type`|<span data-ttu-id="87f85-110">Ciąg określający typ tego elementu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="87f85-110">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="87f85-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="87f85-111">Child Elements</span></span>  
  
|<span data-ttu-id="87f85-112">Element</span><span class="sxs-lookup"><span data-stu-id="87f85-112">Element</span></span>|<span data-ttu-id="87f85-113">Opis</span><span class="sxs-lookup"><span data-stu-id="87f85-113">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCertificate>](clientcertificate-of-clientcredentials-element.md)|<span data-ttu-id="87f85-114">Określa certyfikat używany do uwierzytelniania klienta w usłudze.</span><span class="sxs-lookup"><span data-stu-id="87f85-114">Specifies the certificate used to authenticate the client to the service.</span></span> <span data-ttu-id="87f85-115">Ten element jest typu <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement> .</span><span class="sxs-lookup"><span data-stu-id="87f85-115">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.</span></span>|  
|[\<httpDigest>](httpdigest-element.md)|<span data-ttu-id="87f85-116">Określa skrót używany do uwierzytelniania klienta w usłudze.</span><span class="sxs-lookup"><span data-stu-id="87f85-116">Specifies a digest used to authenticate the client to the service.</span></span> <span data-ttu-id="87f85-117">Ten element jest typu <xref:System.ServiceModel.Configuration.HttpDigestClientElement> .</span><span class="sxs-lookup"><span data-stu-id="87f85-117">This element is of type <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.</span></span>|  
|[\<issuedToken>](issuedtoken.md)|<span data-ttu-id="87f85-118">Określa niestandardowy typ tokenu używany do uwierzytelniania klienta w usłudze bezpiecznego tokenu (STS).</span><span class="sxs-lookup"><span data-stu-id="87f85-118">Specifies a custom token type used to authenticate the client to a Secure Token Service (STS).</span></span> <span data-ttu-id="87f85-119">Ten element jest typu <xref:System.ServiceModel.Configuration.IssuedTokenClientElement> .</span><span class="sxs-lookup"><span data-stu-id="87f85-119">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.</span></span>|  
|[\<peer>](peer-of-clientcredentials-element.md)|<span data-ttu-id="87f85-120">Określa bieżące poświadczenie elementu równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="87f85-120">Specifies a current peer credential.</span></span> <span data-ttu-id="87f85-121">Ten element jest typu <xref:System.ServiceModel.Configuration.PeerCredentialElement> .</span><span class="sxs-lookup"><span data-stu-id="87f85-121">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[\<serviceCertificate>](servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="87f85-122">Określa certyfikat używany do uwierzytelniania usługi na kliencie i udostępnia strukturę do ustawiania opcji certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="87f85-122">Specifies the certificate used to authenticate the service to the client and provides a structure for setting certificate options.</span></span> <span data-ttu-id="87f85-123">Ten certyfikat musi być dostarczony z usługi do klienta jako poza pasmem.</span><span class="sxs-lookup"><span data-stu-id="87f85-123">This certificate must be supplied out-of-band from the service to the client.</span></span> <span data-ttu-id="87f85-124">Ten element jest typu <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement> .</span><span class="sxs-lookup"><span data-stu-id="87f85-124">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.</span></span>|  
|[\<windows>](windows-of-clientcredentials-element.md)|<span data-ttu-id="87f85-125">Określa poświadczenie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="87f85-125">Specifies a Windows credential.</span></span> <span data-ttu-id="87f85-126">Wartość domyślna to poświadczenie bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="87f85-126">The default is the credential of the current thread.</span></span> <span data-ttu-id="87f85-127">Ten element jest typu <xref:System.ServiceModel.Configuration.WindowsClientElement> .</span><span class="sxs-lookup"><span data-stu-id="87f85-127">This element is of type <xref:System.ServiceModel.Configuration.WindowsClientElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="87f85-128">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="87f85-128">Parent Elements</span></span>  
  
|<span data-ttu-id="87f85-129">Element</span><span class="sxs-lookup"><span data-stu-id="87f85-129">Element</span></span>|<span data-ttu-id="87f85-130">Opis</span><span class="sxs-lookup"><span data-stu-id="87f85-130">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="87f85-131">Określa zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="87f85-131">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="87f85-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="87f85-132">Remarks</span></span>  
 <span data-ttu-id="87f85-133">Poświadczenia klienta służą do uwierzytelniania klienta programu w przypadku, gdy wymagane jest uwierzytelnianie wzajemne.</span><span class="sxs-lookup"><span data-stu-id="87f85-133">Client credentials are used to authenticate the client to services in cases where mutual authentication is required.</span></span> <span data-ttu-id="87f85-134">Ta sekcja konfiguracji może również służyć do określania certyfikatów usługi dla scenariuszy, w których klient musi zabezpieczyć komunikaty do usługi za pomocą certyfikatu usługi.</span><span class="sxs-lookup"><span data-stu-id="87f85-134">This configuration section can also be used to specify service certificates for scenarios where the client must secure messages to a service with the service's certificate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87f85-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="87f85-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- [<span data-ttu-id="87f85-136">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="87f85-136">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="87f85-137">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="87f85-137">Securing Clients</span></span>](../../../wcf/securing-clients.md)
