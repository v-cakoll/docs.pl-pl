---
title: <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 96db336c-4f7a-4193-81a5-910b8ffd804f
ms.openlocfilehash: 54ac4f0aa31a4311976449d545880d825c06337d
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55256475"
---
# <a name="servicecredentials"></a><span data-ttu-id="10e70-101">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="10e70-101">\<serviceCredentials></span></span>
<span data-ttu-id="10e70-102">Określa poświadczenie do użycia w uwierzytelnianiu usługi i ustawień dotyczących walidacji poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="10e70-102">Specifies the credential to be used in authenticating the service and the client credential validation-related settings.</span></span>  
  
 <span data-ttu-id="10e70-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="10e70-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="10e70-104">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="10e70-104">\<behaviors></span></span>  
<span data-ttu-id="10e70-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="10e70-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="10e70-106">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="10e70-106">\<behavior></span></span>  
<span data-ttu-id="10e70-107">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="10e70-107">\<serviceCredentials></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10e70-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="10e70-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="10e70-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="10e70-109">Attributes and Elements</span></span>  
 <span data-ttu-id="10e70-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="10e70-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="10e70-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="10e70-111">Attributes</span></span>  
  
|<span data-ttu-id="10e70-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="10e70-112">Attribute</span></span>|<span data-ttu-id="10e70-113">Opis</span><span class="sxs-lookup"><span data-stu-id="10e70-113">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="10e70-114">Ciąg określający typ tego elementu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="10e70-114">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="10e70-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="10e70-115">Child Elements</span></span>  
  
|<span data-ttu-id="10e70-116">Element</span><span class="sxs-lookup"><span data-stu-id="10e70-116">Element</span></span>|<span data-ttu-id="10e70-117">Opis</span><span class="sxs-lookup"><span data-stu-id="10e70-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="10e70-118">\<clientCertificate></span><span class="sxs-lookup"><span data-stu-id="10e70-118">\<clientCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)|<span data-ttu-id="10e70-119">Określa certyfikat, który ma być używany, gdy certyfikat klienta jest dostępne poza pasmem.</span><span class="sxs-lookup"><span data-stu-id="10e70-119">Specifies the certificate to be used when the client certificate is available out-of-band.</span></span> <span data-ttu-id="10e70-120">Ten element określa również ustawienia weryfikacji certyfikatu klienta.</span><span class="sxs-lookup"><span data-stu-id="10e70-120">This element also specifies client certificate validation settings.</span></span> <span data-ttu-id="10e70-121">Ten element jest typu <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="10e70-121">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="10e70-122">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="10e70-122">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="10e70-123">Określa bieżący token wystawiony dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="10e70-123">Specifies the current issued token for this service.</span></span> <span data-ttu-id="10e70-124">Ten element jest typu <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="10e70-124">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span></span>|  
|[<span data-ttu-id="10e70-125">\<elementu równorzędnego ></span><span class="sxs-lookup"><span data-stu-id="10e70-125">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|<span data-ttu-id="10e70-126">Określa bieżące poświadczenia dla węzła równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="10e70-126">Specifies the current credentials for a peer node.</span></span> <span data-ttu-id="10e70-127">Ten element jest typu <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span><span class="sxs-lookup"><span data-stu-id="10e70-127">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[<span data-ttu-id="10e70-128">\<secureConversationAuthentication></span><span class="sxs-lookup"><span data-stu-id="10e70-128">\<secureConversationAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationauthentication-of-servicecredential.md)|<span data-ttu-id="10e70-129">Określa bieżące poświadczenia dla bezpiecznej konwersacji.</span><span class="sxs-lookup"><span data-stu-id="10e70-129">Specifies the current credentials for a secure conversation.</span></span> <span data-ttu-id="10e70-130">Ten element jest typu <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="10e70-130">This element is of type <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span></span>|  
|[<span data-ttu-id="10e70-131">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="10e70-131">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)|<span data-ttu-id="10e70-132">Określa certyfikat używany przez usługę do identyfikacji.</span><span class="sxs-lookup"><span data-stu-id="10e70-132">Specifies a certificate used by a service to identify itself.</span></span> <span data-ttu-id="10e70-133">Ten element jest typu <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="10e70-133">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="10e70-134">\<userNameAuthentication></span><span class="sxs-lookup"><span data-stu-id="10e70-134">\<userNameAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md)|<span data-ttu-id="10e70-135">Określa ustawienia dla sprawdzenie poprawności hasła nazwy użytkownika.</span><span class="sxs-lookup"><span data-stu-id="10e70-135">Specifies the settings for username password validation.</span></span> <span data-ttu-id="10e70-136">Ten element jest typu <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="10e70-136">This element is of type <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span></span>|  
|[<span data-ttu-id="10e70-137">\<windowsAuthentication></span><span class="sxs-lookup"><span data-stu-id="10e70-137">\<windowsAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/windowsauthentication-of-servicecredentials.md)|<span data-ttu-id="10e70-138">Określa ustawienia dla sprawdzanie poprawności poświadczeń Windows.</span><span class="sxs-lookup"><span data-stu-id="10e70-138">Specifies the settings for Windows credential validation.</span></span> <span data-ttu-id="10e70-139">Ten element jest typu <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="10e70-139">This element is of type <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="10e70-140">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="10e70-140">Parent Elements</span></span>  
  
|<span data-ttu-id="10e70-141">Element</span><span class="sxs-lookup"><span data-stu-id="10e70-141">Element</span></span>|<span data-ttu-id="10e70-142">Opis</span><span class="sxs-lookup"><span data-stu-id="10e70-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="10e70-143">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="10e70-143">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="10e70-144">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="10e70-144">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="10e70-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="10e70-145">See also</span></span>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- [<span data-ttu-id="10e70-146">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="10e70-146">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
