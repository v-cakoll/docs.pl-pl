---
title: <clientCredentials>
ms.date: 03/30/2017
ms.assetid: 1e6eef0d-a34e-4d74-b0f7-f65d2181858d
ms.openlocfilehash: ebe976df9af0c316e95a1e089412e57a575a6df1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59157238"
---
# <a name="clientcredentials"></a><span data-ttu-id="375b0-101">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="375b0-101">\<clientCredentials></span></span>
<span data-ttu-id="375b0-102">Określa poświadczenia używane do uwierzytelniania klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="375b0-102">Specifies the credentials used to authenticate the client to a service.</span></span>  
  
 <span data-ttu-id="375b0-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="375b0-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="375b0-104">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="375b0-104">\<behaviors></span></span>  
<span data-ttu-id="375b0-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="375b0-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="375b0-106">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="375b0-106">\<behavior></span></span>  
<span data-ttu-id="375b0-107">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="375b0-107">\<clientCredentials></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="375b0-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="375b0-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="375b0-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="375b0-109">Attributes and Elements</span></span>  
 <span data-ttu-id="375b0-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="375b0-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="375b0-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="375b0-111">Attributes</span></span>  
  
|<span data-ttu-id="375b0-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="375b0-112">Attribute</span></span>|<span data-ttu-id="375b0-113">Opis</span><span class="sxs-lookup"><span data-stu-id="375b0-113">Description</span></span>|  
|---------------|-----------------|  
|`supportInteractive`|<span data-ttu-id="375b0-114">Wartość logiczna określająca czy interaktywny użytkownik może być włączony do wyboru poświadczeń klienta w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="375b0-114">A Boolean value that specifies whether an interactive user can be involved in selecting a client credential at runtime.</span></span> <span data-ttu-id="375b0-115">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="375b0-115">The default value is `true`.</span></span>|  
|`type`|<span data-ttu-id="375b0-116">Ciąg określający typ tego elementu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="375b0-116">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="375b0-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="375b0-117">Child Elements</span></span>  
  
|<span data-ttu-id="375b0-118">Element</span><span class="sxs-lookup"><span data-stu-id="375b0-118">Element</span></span>|<span data-ttu-id="375b0-119">Opis</span><span class="sxs-lookup"><span data-stu-id="375b0-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="375b0-120">\<clientCertificate></span><span class="sxs-lookup"><span data-stu-id="375b0-120">\<clientCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md)|<span data-ttu-id="375b0-121">Określa certyfikat używany do uwierzytelniania klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="375b0-121">Specifies the certificate used to authenticate the client to the service.</span></span> <span data-ttu-id="375b0-122">Ten element jest typu <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.</span><span class="sxs-lookup"><span data-stu-id="375b0-122">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.</span></span>|  
|[<span data-ttu-id="375b0-123">\<httpDigest></span><span class="sxs-lookup"><span data-stu-id="375b0-123">\<httpDigest></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/httpdigest-element.md)|<span data-ttu-id="375b0-124">Określa szyfrowany używany do uwierzytelniania klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="375b0-124">Specifies a digest used to authenticate the client to the service.</span></span> <span data-ttu-id="375b0-125">Ten element jest typu <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.</span><span class="sxs-lookup"><span data-stu-id="375b0-125">This element is of type <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.</span></span>|  
|[<span data-ttu-id="375b0-126">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="375b0-126">\<issuedToken></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|<span data-ttu-id="375b0-127">Określa typ niestandardowy token używany do uwierzytelniania klienta do Secure Token Service (STS).</span><span class="sxs-lookup"><span data-stu-id="375b0-127">Specifies a custom token type used to authenticate the client to a Secure Token Service (STS).</span></span> <span data-ttu-id="375b0-128">Ten element jest typu <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.</span><span class="sxs-lookup"><span data-stu-id="375b0-128">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.</span></span>|  
|[<span data-ttu-id="375b0-129">\<elementu równorzędnego ></span><span class="sxs-lookup"><span data-stu-id="375b0-129">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|<span data-ttu-id="375b0-130">Określa bieżące poświadczenia elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="375b0-130">Specifies a current peer credential.</span></span> <span data-ttu-id="375b0-131">Ten element jest typu <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span><span class="sxs-lookup"><span data-stu-id="375b0-131">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[<span data-ttu-id="375b0-132">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="375b0-132">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="375b0-133">Określa certyfikat używany do uwierzytelniania usługi dla klienta i zapewnia struktury do ustawiania opcji certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="375b0-133">Specifies the certificate used to authenticate the service to the client and provides a structure for setting certificate options.</span></span> <span data-ttu-id="375b0-134">Ten certyfikat musi być podana poza pasmem z usługi do klienta.</span><span class="sxs-lookup"><span data-stu-id="375b0-134">This certificate must be supplied out-of-band from the service to the client.</span></span> <span data-ttu-id="375b0-135">Ten element jest typu <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.</span><span class="sxs-lookup"><span data-stu-id="375b0-135">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.</span></span>|  
|[<span data-ttu-id="375b0-136">\<windows></span><span class="sxs-lookup"><span data-stu-id="375b0-136">\<windows></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/windows-of-clientcredentials-element.md)|<span data-ttu-id="375b0-137">Określa poświadczenia Windows.</span><span class="sxs-lookup"><span data-stu-id="375b0-137">Specifies a Windows credential.</span></span> <span data-ttu-id="375b0-138">Wartość domyślna to poświadczenia bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="375b0-138">The default is the credential of the current thread.</span></span> <span data-ttu-id="375b0-139">Ten element jest typu <xref:System.ServiceModel.Configuration.WindowsClientElement>.</span><span class="sxs-lookup"><span data-stu-id="375b0-139">This element is of type <xref:System.ServiceModel.Configuration.WindowsClientElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="375b0-140">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="375b0-140">Parent Elements</span></span>  
  
|<span data-ttu-id="375b0-141">Element</span><span class="sxs-lookup"><span data-stu-id="375b0-141">Element</span></span>|<span data-ttu-id="375b0-142">Opis</span><span class="sxs-lookup"><span data-stu-id="375b0-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="375b0-143">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="375b0-143">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="375b0-144">Określa zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="375b0-144">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="375b0-145">Uwagi</span><span class="sxs-lookup"><span data-stu-id="375b0-145">Remarks</span></span>  
 <span data-ttu-id="375b0-146">Poświadczenia klienta są używane do uwierzytelniania klienta do usługi w przypadkach, gdy jest wymagane uwierzytelnianie wzajemne.</span><span class="sxs-lookup"><span data-stu-id="375b0-146">Client credentials are used to authenticate the client to services in cases where mutual authentication is required.</span></span> <span data-ttu-id="375b0-147">Ta sekcja konfiguracji może również określić usługi certyfikatów w scenariuszach gdzie klienta należy zabezpieczyć komunikaty do usługi za pomocą certyfikatu usługi.</span><span class="sxs-lookup"><span data-stu-id="375b0-147">This configuration section can also be used to specify service certificates for scenarios where the client must secure messages to a service with the service's certificate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="375b0-148">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="375b0-148">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- [<span data-ttu-id="375b0-149">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="375b0-149">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="375b0-150">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="375b0-150">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
