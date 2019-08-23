---
title: <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 96db336c-4f7a-4193-81a5-910b8ffd804f
ms.openlocfilehash: b5d257b3082717ba94b9a4517ed5ccd4bd325c06
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936295"
---
# <a name="servicecredentials"></a><span data-ttu-id="c9697-101">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="c9697-101">\<serviceCredentials></span></span>
<span data-ttu-id="c9697-102">Określa poświadczenie, które ma być używane w uwierzytelnianiu usługi i ustawień związanych z walidacją poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="c9697-102">Specifies the credential to be used in authenticating the service and the client credential validation-related settings.</span></span>  
  
 <span data-ttu-id="c9697-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c9697-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="c9697-104">\<> zachowań</span><span class="sxs-lookup"><span data-stu-id="c9697-104">\<behaviors></span></span>  
<span data-ttu-id="c9697-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="c9697-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="c9697-106">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="c9697-106">\<behavior></span></span>  
<span data-ttu-id="c9697-107">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="c9697-107">\<serviceCredentials></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9697-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="c9697-108">Syntax</span></span>  
  
```xml  
<serviceCredentials type="String">
  <clientCertificate>
  </clientCertificate>
  <issuedTokenAuthentication>
  </issuedTokenAuthentication>
  <peer>
  </peer>
  <secureConversationAuthentication>
  </secureConversationAuthentication>
  <serviceCertificate>
  </serviceCertificate>
  <userNameAuthentication>
  </userNameAuthentication>
  <windowsAuthentication>
  </windowsAuthentication>
</serviceCredentials>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c9697-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c9697-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c9697-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c9697-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c9697-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c9697-111">Attributes</span></span>  
  
|<span data-ttu-id="c9697-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c9697-112">Attribute</span></span>|<span data-ttu-id="c9697-113">Opis</span><span class="sxs-lookup"><span data-stu-id="c9697-113">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="c9697-114">Ciąg określający typ tego elementu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c9697-114">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c9697-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c9697-115">Child Elements</span></span>  
  
|<span data-ttu-id="c9697-116">Element</span><span class="sxs-lookup"><span data-stu-id="c9697-116">Element</span></span>|<span data-ttu-id="c9697-117">Opis</span><span class="sxs-lookup"><span data-stu-id="c9697-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c9697-118">\<> clientCertificate</span><span class="sxs-lookup"><span data-stu-id="c9697-118">\<clientCertificate></span></span>](clientcertificate-of-servicecredentials.md)|<span data-ttu-id="c9697-119">Określa certyfikat, który ma być używany, gdy certyfikat klienta jest dostępny poza pasmem.</span><span class="sxs-lookup"><span data-stu-id="c9697-119">Specifies the certificate to be used when the client certificate is available out-of-band.</span></span> <span data-ttu-id="c9697-120">Ten element określa również ustawienia weryfikacji certyfikatu klienta.</span><span class="sxs-lookup"><span data-stu-id="c9697-120">This element also specifies client certificate validation settings.</span></span> <span data-ttu-id="c9697-121">Ten element jest typu <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="c9697-121">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="c9697-122">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="c9697-122">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="c9697-123">Określa bieżący token wystawiony dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="c9697-123">Specifies the current issued token for this service.</span></span> <span data-ttu-id="c9697-124">Ten element jest typu <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="c9697-124">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span></span>|  
|[<span data-ttu-id="c9697-125">\<> elementów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="c9697-125">\<peer></span></span>](peer-of-servicecredentials.md)|<span data-ttu-id="c9697-126">Określa bieżące poświadczenia dla węzła równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="c9697-126">Specifies the current credentials for a peer node.</span></span> <span data-ttu-id="c9697-127">Ten element jest typu <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span><span class="sxs-lookup"><span data-stu-id="c9697-127">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[<span data-ttu-id="c9697-128">\<secureConversationAuthentication></span><span class="sxs-lookup"><span data-stu-id="c9697-128">\<secureConversationAuthentication></span></span>](secureconversationauthentication-of-servicecredential.md)|<span data-ttu-id="c9697-129">Określa bieżące poświadczenia dla bezpiecznej konwersacji.</span><span class="sxs-lookup"><span data-stu-id="c9697-129">Specifies the current credentials for a secure conversation.</span></span> <span data-ttu-id="c9697-130">Ten element jest typu <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="c9697-130">This element is of type <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span></span>|  
|[<span data-ttu-id="c9697-131">\<> serviceCertificate</span><span class="sxs-lookup"><span data-stu-id="c9697-131">\<serviceCertificate></span></span>](servicecertificate-of-servicecredentials.md)|<span data-ttu-id="c9697-132">Określa certyfikat używany przez usługę do zidentyfikowania siebie.</span><span class="sxs-lookup"><span data-stu-id="c9697-132">Specifies a certificate used by a service to identify itself.</span></span> <span data-ttu-id="c9697-133">Ten element jest typu <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="c9697-133">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="c9697-134">\<userNameAuthentication></span><span class="sxs-lookup"><span data-stu-id="c9697-134">\<userNameAuthentication></span></span>](usernameauthentication.md)|<span data-ttu-id="c9697-135">Określa ustawienia dla walidacji hasła użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c9697-135">Specifies the settings for username password validation.</span></span> <span data-ttu-id="c9697-136">Ten element jest typu <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="c9697-136">This element is of type <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span></span>|  
|[<span data-ttu-id="c9697-137">\<windowsAuthentication></span><span class="sxs-lookup"><span data-stu-id="c9697-137">\<windowsAuthentication></span></span>](windowsauthentication-of-servicecredentials.md)|<span data-ttu-id="c9697-138">Określa ustawienia weryfikacji poświadczeń systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="c9697-138">Specifies the settings for Windows credential validation.</span></span> <span data-ttu-id="c9697-139">Ten element jest typu <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="c9697-139">This element is of type <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c9697-140">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c9697-140">Parent Elements</span></span>  
  
|<span data-ttu-id="c9697-141">Element</span><span class="sxs-lookup"><span data-stu-id="c9697-141">Element</span></span>|<span data-ttu-id="c9697-142">Opis</span><span class="sxs-lookup"><span data-stu-id="c9697-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c9697-143">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="c9697-143">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="c9697-144">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="c9697-144">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c9697-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c9697-145">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- [<span data-ttu-id="c9697-146">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="c9697-146">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
