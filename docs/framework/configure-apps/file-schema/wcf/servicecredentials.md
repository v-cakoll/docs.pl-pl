---
title: '&lt;serviceCredentials&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 96db336c-4f7a-4193-81a5-910b8ffd804f
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 00567c32b800bb98386e15b2ba822ccc9623d72b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltservicecredentialsgt"></a><span data-ttu-id="28654-102">&lt;serviceCredentials&gt;</span><span class="sxs-lookup"><span data-stu-id="28654-102">&lt;serviceCredentials&gt;</span></span>
<span data-ttu-id="28654-103">Określa poświadczenia do użycia w uwierzytelnianiu usługi i ustawień dotyczących walidacji poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="28654-103">Specifies the credential to be used in authenticating the service and the client credential validation-related settings.</span></span>  
  
 <span data-ttu-id="28654-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="28654-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="28654-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="28654-105">\<behaviors></span></span>  
<span data-ttu-id="28654-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="28654-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="28654-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="28654-107">\<behavior></span></span>  
<span data-ttu-id="28654-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="28654-108">\<serviceCredentials></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28654-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="28654-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="28654-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="28654-110">Attributes and Elements</span></span>  
 <span data-ttu-id="28654-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="28654-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="28654-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="28654-112">Attributes</span></span>  
  
|<span data-ttu-id="28654-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="28654-113">Attribute</span></span>|<span data-ttu-id="28654-114">Opis</span><span class="sxs-lookup"><span data-stu-id="28654-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="28654-115">Ciąg określający typ tego elementu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="28654-115">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="28654-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="28654-116">Child Elements</span></span>  
  
|<span data-ttu-id="28654-117">Element</span><span class="sxs-lookup"><span data-stu-id="28654-117">Element</span></span>|<span data-ttu-id="28654-118">Opis</span><span class="sxs-lookup"><span data-stu-id="28654-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="28654-119">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="28654-119">\<clientCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)|<span data-ttu-id="28654-120">Określa certyfikat, który ma być używany podczas certyfikat klienta jest dostępny poza pasmem.</span><span class="sxs-lookup"><span data-stu-id="28654-120">Specifies the certificate to be used when the client certificate is available out-of-band.</span></span> <span data-ttu-id="28654-121">Ten element określa również ustawienia weryfikacji certyfikatu klienta.</span><span class="sxs-lookup"><span data-stu-id="28654-121">This element also specifies client certificate validation settings.</span></span> <span data-ttu-id="28654-122">Ten element jest typu <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="28654-122">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="28654-123">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="28654-123">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="28654-124">Określa bieżący wystawionego tokenu dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="28654-124">Specifies the current issued token for this service.</span></span> <span data-ttu-id="28654-125">Ten element jest typu <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="28654-125">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span></span>|  
|[<span data-ttu-id="28654-126">\<peer ></span><span class="sxs-lookup"><span data-stu-id="28654-126">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|<span data-ttu-id="28654-127">Określa bieżące poświadczenia dla węzła równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="28654-127">Specifies the current credentials for a peer node.</span></span> <span data-ttu-id="28654-128">Ten element jest typu <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span><span class="sxs-lookup"><span data-stu-id="28654-128">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[<span data-ttu-id="28654-129">\<secureConversationAuthentication ></span><span class="sxs-lookup"><span data-stu-id="28654-129">\<secureConversationAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationauthentication-of-servicecredential.md)|<span data-ttu-id="28654-130">Określa bieżące poświadczenia dla bezpiecznej konwersacji.</span><span class="sxs-lookup"><span data-stu-id="28654-130">Specifies the current credentials for a secure conversation.</span></span> <span data-ttu-id="28654-131">Ten element jest typu <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="28654-131">This element is of type <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span></span>|  
|[<span data-ttu-id="28654-132">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="28654-132">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)|<span data-ttu-id="28654-133">Określa certyfikat używany przez usługę do identyfikacji.</span><span class="sxs-lookup"><span data-stu-id="28654-133">Specifies a certificate used by a service to identify itself.</span></span> <span data-ttu-id="28654-134">Ten element jest typu <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="28654-134">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="28654-135">\<userNameAuthentication ></span><span class="sxs-lookup"><span data-stu-id="28654-135">\<userNameAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md)|<span data-ttu-id="28654-136">Określa ustawienia dla nazwy użytkownika sprawdzenie poprawności hasła.</span><span class="sxs-lookup"><span data-stu-id="28654-136">Specifies the settings for username password validation.</span></span> <span data-ttu-id="28654-137">Ten element jest typu <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="28654-137">This element is of type <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span></span>|  
|[<span data-ttu-id="28654-138">\<windowsAuthentication ></span><span class="sxs-lookup"><span data-stu-id="28654-138">\<windowsAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/windowsauthentication-of-servicecredentials.md)|<span data-ttu-id="28654-139">Określa ustawienia dla sprawdzanie poprawności poświadczeń systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="28654-139">Specifies the settings for Windows credential validation.</span></span> <span data-ttu-id="28654-140">Ten element jest typu <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="28654-140">This element is of type <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="28654-141">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="28654-141">Parent Elements</span></span>  
  
|<span data-ttu-id="28654-142">Element</span><span class="sxs-lookup"><span data-stu-id="28654-142">Element</span></span>|<span data-ttu-id="28654-143">Opis</span><span class="sxs-lookup"><span data-stu-id="28654-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="28654-144">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="28654-144">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="28654-145">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="28654-145">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="28654-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="28654-146">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>  
 <xref:System.ServiceModel.Description.ServiceCredentials>  
 [<span data-ttu-id="28654-147">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="28654-147">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
