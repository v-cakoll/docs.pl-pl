---
title: '&lt;ClientCredentials&gt;'
ms.date: 03/30/2017
ms.assetid: 1e6eef0d-a34e-4d74-b0f7-f65d2181858d
ms.openlocfilehash: 3f70a4e6e27507c3820e1b67f49664e538ac736f
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145752"
---
# <a name="ltclientcredentialsgt"></a><span data-ttu-id="cfcb6-102">&lt;ClientCredentials&gt;</span><span class="sxs-lookup"><span data-stu-id="cfcb6-102">&lt;clientCredentials&gt;</span></span>
<span data-ttu-id="cfcb6-103">Określa poświadczenia używane do uwierzytelniania klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="cfcb6-103">Specifies the credentials used to authenticate the client to a service.</span></span>  
  
 <span data-ttu-id="cfcb6-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="cfcb6-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="cfcb6-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="cfcb6-105">\<behaviors></span></span>  
<span data-ttu-id="cfcb6-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="cfcb6-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="cfcb6-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="cfcb6-107">\<behavior></span></span>  
<span data-ttu-id="cfcb6-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="cfcb6-108">\<clientCredentials></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfcb6-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="cfcb6-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cfcb6-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="cfcb6-110">Attributes and Elements</span></span>  
 <span data-ttu-id="cfcb6-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="cfcb6-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cfcb6-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="cfcb6-112">Attributes</span></span>  
  
|<span data-ttu-id="cfcb6-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="cfcb6-113">Attribute</span></span>|<span data-ttu-id="cfcb6-114">Opis</span><span class="sxs-lookup"><span data-stu-id="cfcb6-114">Description</span></span>|  
|---------------|-----------------|  
|`supportInteractive`|<span data-ttu-id="cfcb6-115">Wartość logiczna określająca czy interaktywny użytkownik może być włączony do wyboru poświadczeń klienta w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="cfcb6-115">A Boolean value that specifies whether an interactive user can be involved in selecting a client credential at runtime.</span></span> <span data-ttu-id="cfcb6-116">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="cfcb6-116">The default value is `true`.</span></span>|  
|`type`|<span data-ttu-id="cfcb6-117">Ciąg określający typ tego elementu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="cfcb6-117">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cfcb6-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="cfcb6-118">Child Elements</span></span>  
  
|<span data-ttu-id="cfcb6-119">Element</span><span class="sxs-lookup"><span data-stu-id="cfcb6-119">Element</span></span>|<span data-ttu-id="cfcb6-120">Opis</span><span class="sxs-lookup"><span data-stu-id="cfcb6-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cfcb6-121">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="cfcb6-121">\<clientCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md)|<span data-ttu-id="cfcb6-122">Określa certyfikat używany do uwierzytelniania klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="cfcb6-122">Specifies the certificate used to authenticate the client to the service.</span></span> <span data-ttu-id="cfcb6-123">Ten element jest typu <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.</span><span class="sxs-lookup"><span data-stu-id="cfcb6-123">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.</span></span>|  
|[<span data-ttu-id="cfcb6-124">\<httpDigest ></span><span class="sxs-lookup"><span data-stu-id="cfcb6-124">\<httpDigest></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/httpdigest-element.md)|<span data-ttu-id="cfcb6-125">Określa szyfrowany używany do uwierzytelniania klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="cfcb6-125">Specifies a digest used to authenticate the client to the service.</span></span> <span data-ttu-id="cfcb6-126">Ten element jest typu <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.</span><span class="sxs-lookup"><span data-stu-id="cfcb6-126">This element is of type <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.</span></span>|  
|[<span data-ttu-id="cfcb6-127">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="cfcb6-127">\<issuedToken></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|<span data-ttu-id="cfcb6-128">Określa typ niestandardowy token używany do uwierzytelniania klienta do Secure Token Service (STS).</span><span class="sxs-lookup"><span data-stu-id="cfcb6-128">Specifies a custom token type used to authenticate the client to a Secure Token Service (STS).</span></span> <span data-ttu-id="cfcb6-129">Ten element jest typu <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.</span><span class="sxs-lookup"><span data-stu-id="cfcb6-129">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.</span></span>|  
|[<span data-ttu-id="cfcb6-130">\<elementu równorzędnego ></span><span class="sxs-lookup"><span data-stu-id="cfcb6-130">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|<span data-ttu-id="cfcb6-131">Określa bieżące poświadczenia elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="cfcb6-131">Specifies a current peer credential.</span></span> <span data-ttu-id="cfcb6-132">Ten element jest typu <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span><span class="sxs-lookup"><span data-stu-id="cfcb6-132">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[<span data-ttu-id="cfcb6-133">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="cfcb6-133">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="cfcb6-134">Określa certyfikat używany do uwierzytelniania usługi dla klienta i zapewnia struktury do ustawiania opcji certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="cfcb6-134">Specifies the certificate used to authenticate the service to the client and provides a structure for setting certificate options.</span></span> <span data-ttu-id="cfcb6-135">Ten certyfikat musi być podana poza pasmem z usługi do klienta.</span><span class="sxs-lookup"><span data-stu-id="cfcb6-135">This certificate must be supplied out-of-band from the service to the client.</span></span> <span data-ttu-id="cfcb6-136">Ten element jest typu <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.</span><span class="sxs-lookup"><span data-stu-id="cfcb6-136">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.</span></span>|  
|[<span data-ttu-id="cfcb6-137">\<Windows ></span><span class="sxs-lookup"><span data-stu-id="cfcb6-137">\<windows></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/windows-of-clientcredentials-element.md)|<span data-ttu-id="cfcb6-138">Określa poświadczenia Windows.</span><span class="sxs-lookup"><span data-stu-id="cfcb6-138">Specifies a Windows credential.</span></span> <span data-ttu-id="cfcb6-139">Wartość domyślna to poświadczenia bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="cfcb6-139">The default is the credential of the current thread.</span></span> <span data-ttu-id="cfcb6-140">Ten element jest typu <xref:System.ServiceModel.Configuration.WindowsClientElement>.</span><span class="sxs-lookup"><span data-stu-id="cfcb6-140">This element is of type <xref:System.ServiceModel.Configuration.WindowsClientElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cfcb6-141">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="cfcb6-141">Parent Elements</span></span>  
  
|<span data-ttu-id="cfcb6-142">Element</span><span class="sxs-lookup"><span data-stu-id="cfcb6-142">Element</span></span>|<span data-ttu-id="cfcb6-143">Opis</span><span class="sxs-lookup"><span data-stu-id="cfcb6-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cfcb6-144">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="cfcb6-144">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="cfcb6-145">Określa zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="cfcb6-145">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cfcb6-146">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cfcb6-146">Remarks</span></span>  
 <span data-ttu-id="cfcb6-147">Poświadczenia klienta są używane do uwierzytelniania klienta do usługi w przypadkach, gdy jest wymagane uwierzytelnianie wzajemne.</span><span class="sxs-lookup"><span data-stu-id="cfcb6-147">Client credentials are used to authenticate the client to services in cases where mutual authentication is required.</span></span> <span data-ttu-id="cfcb6-148">Ta sekcja konfiguracji może również określić usługi certyfikatów w scenariuszach gdzie klienta należy zabezpieczyć komunikaty do usługi za pomocą certyfikatu usługi.</span><span class="sxs-lookup"><span data-stu-id="cfcb6-148">This configuration section can also be used to specify service certificates for scenarios where the client must secure messages to a service with the service's certificate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfcb6-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cfcb6-149">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 [<span data-ttu-id="cfcb6-150">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="cfcb6-150">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="cfcb6-151">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="cfcb6-151">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
