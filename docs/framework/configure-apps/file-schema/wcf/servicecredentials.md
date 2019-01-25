---
title: '&lt;serviceCredentials&gt;'
ms.date: 03/30/2017
ms.assetid: 96db336c-4f7a-4193-81a5-910b8ffd804f
ms.openlocfilehash: 978439dfeb0c5275e2ec43f9c891b6927e7a7869
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54610438"
---
# <a name="ltservicecredentialsgt"></a><span data-ttu-id="de25c-102">&lt;serviceCredentials&gt;</span><span class="sxs-lookup"><span data-stu-id="de25c-102">&lt;serviceCredentials&gt;</span></span>
<span data-ttu-id="de25c-103">Określa poświadczenie do użycia w uwierzytelnianiu usługi i ustawień dotyczących walidacji poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="de25c-103">Specifies the credential to be used in authenticating the service and the client credential validation-related settings.</span></span>  
  
 <span data-ttu-id="de25c-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="de25c-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="de25c-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="de25c-105">\<behaviors></span></span>  
<span data-ttu-id="de25c-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="de25c-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="de25c-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="de25c-107">\<behavior></span></span>  
<span data-ttu-id="de25c-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="de25c-108">\<serviceCredentials></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de25c-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="de25c-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="de25c-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="de25c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="de25c-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="de25c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="de25c-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="de25c-112">Attributes</span></span>  
  
|<span data-ttu-id="de25c-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="de25c-113">Attribute</span></span>|<span data-ttu-id="de25c-114">Opis</span><span class="sxs-lookup"><span data-stu-id="de25c-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="de25c-115">Ciąg określający typ tego elementu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="de25c-115">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="de25c-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="de25c-116">Child Elements</span></span>  
  
|<span data-ttu-id="de25c-117">Element</span><span class="sxs-lookup"><span data-stu-id="de25c-117">Element</span></span>|<span data-ttu-id="de25c-118">Opis</span><span class="sxs-lookup"><span data-stu-id="de25c-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="de25c-119">\<clientCertificate></span><span class="sxs-lookup"><span data-stu-id="de25c-119">\<clientCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)|<span data-ttu-id="de25c-120">Określa certyfikat, który ma być używany, gdy certyfikat klienta jest dostępne poza pasmem.</span><span class="sxs-lookup"><span data-stu-id="de25c-120">Specifies the certificate to be used when the client certificate is available out-of-band.</span></span> <span data-ttu-id="de25c-121">Ten element określa również ustawienia weryfikacji certyfikatu klienta.</span><span class="sxs-lookup"><span data-stu-id="de25c-121">This element also specifies client certificate validation settings.</span></span> <span data-ttu-id="de25c-122">Ten element jest typu <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="de25c-122">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="de25c-123">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="de25c-123">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="de25c-124">Określa bieżący token wystawiony dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="de25c-124">Specifies the current issued token for this service.</span></span> <span data-ttu-id="de25c-125">Ten element jest typu <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="de25c-125">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span></span>|  
|[<span data-ttu-id="de25c-126">\<elementu równorzędnego ></span><span class="sxs-lookup"><span data-stu-id="de25c-126">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|<span data-ttu-id="de25c-127">Określa bieżące poświadczenia dla węzła równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="de25c-127">Specifies the current credentials for a peer node.</span></span> <span data-ttu-id="de25c-128">Ten element jest typu <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span><span class="sxs-lookup"><span data-stu-id="de25c-128">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[<span data-ttu-id="de25c-129">\<secureConversationAuthentication></span><span class="sxs-lookup"><span data-stu-id="de25c-129">\<secureConversationAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationauthentication-of-servicecredential.md)|<span data-ttu-id="de25c-130">Określa bieżące poświadczenia dla bezpiecznej konwersacji.</span><span class="sxs-lookup"><span data-stu-id="de25c-130">Specifies the current credentials for a secure conversation.</span></span> <span data-ttu-id="de25c-131">Ten element jest typu <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="de25c-131">This element is of type <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span></span>|  
|[<span data-ttu-id="de25c-132">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="de25c-132">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)|<span data-ttu-id="de25c-133">Określa certyfikat używany przez usługę do identyfikacji.</span><span class="sxs-lookup"><span data-stu-id="de25c-133">Specifies a certificate used by a service to identify itself.</span></span> <span data-ttu-id="de25c-134">Ten element jest typu <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="de25c-134">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="de25c-135">\<userNameAuthentication></span><span class="sxs-lookup"><span data-stu-id="de25c-135">\<userNameAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md)|<span data-ttu-id="de25c-136">Określa ustawienia dla sprawdzenie poprawności hasła nazwy użytkownika.</span><span class="sxs-lookup"><span data-stu-id="de25c-136">Specifies the settings for username password validation.</span></span> <span data-ttu-id="de25c-137">Ten element jest typu <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="de25c-137">This element is of type <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span></span>|  
|[<span data-ttu-id="de25c-138">\<windowsAuthentication></span><span class="sxs-lookup"><span data-stu-id="de25c-138">\<windowsAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/windowsauthentication-of-servicecredentials.md)|<span data-ttu-id="de25c-139">Określa ustawienia dla sprawdzanie poprawności poświadczeń Windows.</span><span class="sxs-lookup"><span data-stu-id="de25c-139">Specifies the settings for Windows credential validation.</span></span> <span data-ttu-id="de25c-140">Ten element jest typu <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="de25c-140">This element is of type <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="de25c-141">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="de25c-141">Parent Elements</span></span>  
  
|<span data-ttu-id="de25c-142">Element</span><span class="sxs-lookup"><span data-stu-id="de25c-142">Element</span></span>|<span data-ttu-id="de25c-143">Opis</span><span class="sxs-lookup"><span data-stu-id="de25c-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="de25c-144">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="de25c-144">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="de25c-145">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="de25c-145">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="de25c-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="de25c-146">See also</span></span>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- [<span data-ttu-id="de25c-147">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="de25c-147">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
