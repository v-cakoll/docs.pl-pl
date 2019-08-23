---
title: <clientCredentials>
ms.date: 03/30/2017
ms.assetid: 1e6eef0d-a34e-4d74-b0f7-f65d2181858d
ms.openlocfilehash: c3e756f49b7054d6553eb6c3f1850f0fbce14943
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926107"
---
# <a name="clientcredentials"></a><span data-ttu-id="a6485-101">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="a6485-101">\<clientCredentials></span></span>
<span data-ttu-id="a6485-102">Określa poświadczenia używane do uwierzytelniania klienta w usłudze.</span><span class="sxs-lookup"><span data-stu-id="a6485-102">Specifies the credentials used to authenticate the client to a service.</span></span>  
  
 <span data-ttu-id="a6485-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a6485-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="a6485-104">\<> zachowań</span><span class="sxs-lookup"><span data-stu-id="a6485-104">\<behaviors></span></span>  
<span data-ttu-id="a6485-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="a6485-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="a6485-106">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="a6485-106">\<behavior></span></span>  
<span data-ttu-id="a6485-107">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="a6485-107">\<clientCredentials></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6485-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="a6485-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a6485-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a6485-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a6485-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a6485-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a6485-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a6485-111">Attributes</span></span>  
  
|<span data-ttu-id="a6485-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a6485-112">Attribute</span></span>|<span data-ttu-id="a6485-113">Opis</span><span class="sxs-lookup"><span data-stu-id="a6485-113">Description</span></span>|  
|---------------|-----------------|  
|`supportInteractive`|<span data-ttu-id="a6485-114">Wartość logiczna określająca, czy użytkownik interaktywny może uczestniczyć w wyborze poświadczenia klienta w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="a6485-114">A Boolean value that specifies whether an interactive user can be involved in selecting a client credential at runtime.</span></span> <span data-ttu-id="a6485-115">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="a6485-115">The default value is `true`.</span></span>|  
|`type`|<span data-ttu-id="a6485-116">Ciąg określający typ tego elementu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a6485-116">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a6485-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a6485-117">Child Elements</span></span>  
  
|<span data-ttu-id="a6485-118">Element</span><span class="sxs-lookup"><span data-stu-id="a6485-118">Element</span></span>|<span data-ttu-id="a6485-119">Opis</span><span class="sxs-lookup"><span data-stu-id="a6485-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a6485-120">\<> clientCertificate</span><span class="sxs-lookup"><span data-stu-id="a6485-120">\<clientCertificate></span></span>](clientcertificate-of-clientcredentials-element.md)|<span data-ttu-id="a6485-121">Określa certyfikat używany do uwierzytelniania klienta w usłudze.</span><span class="sxs-lookup"><span data-stu-id="a6485-121">Specifies the certificate used to authenticate the client to the service.</span></span> <span data-ttu-id="a6485-122">Ten element jest typu <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.</span><span class="sxs-lookup"><span data-stu-id="a6485-122">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.</span></span>|  
|[<span data-ttu-id="a6485-123">\<httpDigest></span><span class="sxs-lookup"><span data-stu-id="a6485-123">\<httpDigest></span></span>](httpdigest-element.md)|<span data-ttu-id="a6485-124">Określa skrót używany do uwierzytelniania klienta w usłudze.</span><span class="sxs-lookup"><span data-stu-id="a6485-124">Specifies a digest used to authenticate the client to the service.</span></span> <span data-ttu-id="a6485-125">Ten element jest typu <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.</span><span class="sxs-lookup"><span data-stu-id="a6485-125">This element is of type <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.</span></span>|  
|[<span data-ttu-id="a6485-126">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="a6485-126">\<issuedToken></span></span>](issuedtoken.md)|<span data-ttu-id="a6485-127">Określa niestandardowy typ tokenu używany do uwierzytelniania klienta w usłudze bezpiecznego tokenu (STS).</span><span class="sxs-lookup"><span data-stu-id="a6485-127">Specifies a custom token type used to authenticate the client to a Secure Token Service (STS).</span></span> <span data-ttu-id="a6485-128">Ten element jest typu <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.</span><span class="sxs-lookup"><span data-stu-id="a6485-128">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.</span></span>|  
|[<span data-ttu-id="a6485-129">\<> elementów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="a6485-129">\<peer></span></span>](peer-of-clientcredentials-element.md)|<span data-ttu-id="a6485-130">Określa bieżące poświadczenie elementu równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="a6485-130">Specifies a current peer credential.</span></span> <span data-ttu-id="a6485-131">Ten element jest typu <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span><span class="sxs-lookup"><span data-stu-id="a6485-131">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[<span data-ttu-id="a6485-132">\<> serviceCertificate</span><span class="sxs-lookup"><span data-stu-id="a6485-132">\<serviceCertificate></span></span>](servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="a6485-133">Określa certyfikat używany do uwierzytelniania usługi na kliencie i udostępnia strukturę do ustawiania opcji certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="a6485-133">Specifies the certificate used to authenticate the service to the client and provides a structure for setting certificate options.</span></span> <span data-ttu-id="a6485-134">Ten certyfikat musi być dostarczony z usługi do klienta jako poza pasmem.</span><span class="sxs-lookup"><span data-stu-id="a6485-134">This certificate must be supplied out-of-band from the service to the client.</span></span> <span data-ttu-id="a6485-135">Ten element jest typu <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.</span><span class="sxs-lookup"><span data-stu-id="a6485-135">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.</span></span>|  
|[<span data-ttu-id="a6485-136">\<windows></span><span class="sxs-lookup"><span data-stu-id="a6485-136">\<windows></span></span>](windows-of-clientcredentials-element.md)|<span data-ttu-id="a6485-137">Określa poświadczenie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="a6485-137">Specifies a Windows credential.</span></span> <span data-ttu-id="a6485-138">Wartość domyślna to poświadczenie bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="a6485-138">The default is the credential of the current thread.</span></span> <span data-ttu-id="a6485-139">Ten element jest typu <xref:System.ServiceModel.Configuration.WindowsClientElement>.</span><span class="sxs-lookup"><span data-stu-id="a6485-139">This element is of type <xref:System.ServiceModel.Configuration.WindowsClientElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a6485-140">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a6485-140">Parent Elements</span></span>  
  
|<span data-ttu-id="a6485-141">Element</span><span class="sxs-lookup"><span data-stu-id="a6485-141">Element</span></span>|<span data-ttu-id="a6485-142">Opis</span><span class="sxs-lookup"><span data-stu-id="a6485-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a6485-143">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="a6485-143">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="a6485-144">Określa zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="a6485-144">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a6485-145">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a6485-145">Remarks</span></span>  
 <span data-ttu-id="a6485-146">Poświadczenia klienta służą do uwierzytelniania klienta programu w przypadku, gdy wymagane jest uwierzytelnianie wzajemne.</span><span class="sxs-lookup"><span data-stu-id="a6485-146">Client credentials are used to authenticate the client to services in cases where mutual authentication is required.</span></span> <span data-ttu-id="a6485-147">Ta sekcja konfiguracji może również służyć do określania certyfikatów usługi dla scenariuszy, w których klient musi zabezpieczyć komunikaty do usługi za pomocą certyfikatu usługi.</span><span class="sxs-lookup"><span data-stu-id="a6485-147">This configuration section can also be used to specify service certificates for scenarios where the client must secure messages to a service with the service's certificate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6485-148">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a6485-148">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- [<span data-ttu-id="a6485-149">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="a6485-149">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="a6485-150">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="a6485-150">Securing Clients</span></span>](../../../wcf/securing-clients.md)
