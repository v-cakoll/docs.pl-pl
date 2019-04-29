---
title: <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 96db336c-4f7a-4193-81a5-910b8ffd804f
ms.openlocfilehash: d9f8fdf272962916cd08aede484e9bbde55b96a3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61670290"
---
# <a name="servicecredentials"></a><span data-ttu-id="365cf-101">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="365cf-101">\<serviceCredentials></span></span>
<span data-ttu-id="365cf-102">Określa poświadczenie do użycia w uwierzytelnianiu usługi i ustawień dotyczących walidacji poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="365cf-102">Specifies the credential to be used in authenticating the service and the client credential validation-related settings.</span></span>  
  
 <span data-ttu-id="365cf-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="365cf-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="365cf-104">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="365cf-104">\<behaviors></span></span>  
<span data-ttu-id="365cf-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="365cf-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="365cf-106">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="365cf-106">\<behavior></span></span>  
<span data-ttu-id="365cf-107">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="365cf-107">\<serviceCredentials></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="365cf-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="365cf-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="365cf-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="365cf-109">Attributes and Elements</span></span>  
 <span data-ttu-id="365cf-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="365cf-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="365cf-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="365cf-111">Attributes</span></span>  
  
|<span data-ttu-id="365cf-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="365cf-112">Attribute</span></span>|<span data-ttu-id="365cf-113">Opis</span><span class="sxs-lookup"><span data-stu-id="365cf-113">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="365cf-114">Ciąg określający typ tego elementu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="365cf-114">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="365cf-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="365cf-115">Child Elements</span></span>  
  
|<span data-ttu-id="365cf-116">Element</span><span class="sxs-lookup"><span data-stu-id="365cf-116">Element</span></span>|<span data-ttu-id="365cf-117">Opis</span><span class="sxs-lookup"><span data-stu-id="365cf-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="365cf-118">\<clientCertificate></span><span class="sxs-lookup"><span data-stu-id="365cf-118">\<clientCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)|<span data-ttu-id="365cf-119">Określa certyfikat, który ma być używany, gdy certyfikat klienta jest dostępne poza pasmem.</span><span class="sxs-lookup"><span data-stu-id="365cf-119">Specifies the certificate to be used when the client certificate is available out-of-band.</span></span> <span data-ttu-id="365cf-120">Ten element określa również ustawienia weryfikacji certyfikatu klienta.</span><span class="sxs-lookup"><span data-stu-id="365cf-120">This element also specifies client certificate validation settings.</span></span> <span data-ttu-id="365cf-121">Ten element jest typu <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="365cf-121">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="365cf-122">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="365cf-122">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="365cf-123">Określa bieżący token wystawiony dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="365cf-123">Specifies the current issued token for this service.</span></span> <span data-ttu-id="365cf-124">Ten element jest typu <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="365cf-124">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span></span>|  
|[<span data-ttu-id="365cf-125">\<elementu równorzędnego ></span><span class="sxs-lookup"><span data-stu-id="365cf-125">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|<span data-ttu-id="365cf-126">Określa bieżące poświadczenia dla węzła równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="365cf-126">Specifies the current credentials for a peer node.</span></span> <span data-ttu-id="365cf-127">Ten element jest typu <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span><span class="sxs-lookup"><span data-stu-id="365cf-127">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[<span data-ttu-id="365cf-128">\<secureConversationAuthentication></span><span class="sxs-lookup"><span data-stu-id="365cf-128">\<secureConversationAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationauthentication-of-servicecredential.md)|<span data-ttu-id="365cf-129">Określa bieżące poświadczenia dla bezpiecznej konwersacji.</span><span class="sxs-lookup"><span data-stu-id="365cf-129">Specifies the current credentials for a secure conversation.</span></span> <span data-ttu-id="365cf-130">Ten element jest typu <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="365cf-130">This element is of type <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span></span>|  
|[<span data-ttu-id="365cf-131">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="365cf-131">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)|<span data-ttu-id="365cf-132">Określa certyfikat używany przez usługę do identyfikacji.</span><span class="sxs-lookup"><span data-stu-id="365cf-132">Specifies a certificate used by a service to identify itself.</span></span> <span data-ttu-id="365cf-133">Ten element jest typu <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="365cf-133">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="365cf-134">\<userNameAuthentication></span><span class="sxs-lookup"><span data-stu-id="365cf-134">\<userNameAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md)|<span data-ttu-id="365cf-135">Określa ustawienia dla sprawdzenie poprawności hasła nazwy użytkownika.</span><span class="sxs-lookup"><span data-stu-id="365cf-135">Specifies the settings for username password validation.</span></span> <span data-ttu-id="365cf-136">Ten element jest typu <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="365cf-136">This element is of type <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span></span>|  
|[<span data-ttu-id="365cf-137">\<windowsAuthentication></span><span class="sxs-lookup"><span data-stu-id="365cf-137">\<windowsAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/windowsauthentication-of-servicecredentials.md)|<span data-ttu-id="365cf-138">Określa ustawienia dla sprawdzanie poprawności poświadczeń Windows.</span><span class="sxs-lookup"><span data-stu-id="365cf-138">Specifies the settings for Windows credential validation.</span></span> <span data-ttu-id="365cf-139">Ten element jest typu <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="365cf-139">This element is of type <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="365cf-140">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="365cf-140">Parent Elements</span></span>  
  
|<span data-ttu-id="365cf-141">Element</span><span class="sxs-lookup"><span data-stu-id="365cf-141">Element</span></span>|<span data-ttu-id="365cf-142">Opis</span><span class="sxs-lookup"><span data-stu-id="365cf-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="365cf-143">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="365cf-143">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="365cf-144">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="365cf-144">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="365cf-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="365cf-145">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- [<span data-ttu-id="365cf-146">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="365cf-146">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
