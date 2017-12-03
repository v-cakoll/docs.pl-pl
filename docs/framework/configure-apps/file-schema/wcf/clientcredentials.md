---
title: '&lt;clientCredentials&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e6eef0d-a34e-4d74-b0f7-f65d2181858d
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 834853d8a922148d2810cd391a64a281f2f9ae3c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltclientcredentialsgt"></a><span data-ttu-id="031dd-102">&lt;clientCredentials&gt;</span><span class="sxs-lookup"><span data-stu-id="031dd-102">&lt;clientCredentials&gt;</span></span>
<span data-ttu-id="031dd-103">Określa poświadczenia używane do uwierzytelniania klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="031dd-103">Specifies the credentials used to authenticate the client to a service.</span></span>  
  
 <span data-ttu-id="031dd-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="031dd-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="031dd-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="031dd-105">\<behaviors></span></span>  
<span data-ttu-id="031dd-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="031dd-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="031dd-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="031dd-107">\<behavior></span></span>  
<span data-ttu-id="031dd-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="031dd-108">\<clientCredentials></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="031dd-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="031dd-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="031dd-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="031dd-110">Attributes and Elements</span></span>  
 <span data-ttu-id="031dd-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="031dd-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="031dd-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="031dd-112">Attributes</span></span>  
  
|<span data-ttu-id="031dd-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="031dd-113">Attribute</span></span>|<span data-ttu-id="031dd-114">Opis</span><span class="sxs-lookup"><span data-stu-id="031dd-114">Description</span></span>|  
|---------------|-----------------|  
|`supportInteractive`|<span data-ttu-id="031dd-115">Wartość logiczna określająca czy interaktywny użytkownik może być włączony do wyboru poświadczeń klienta w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="031dd-115">A Boolean value that specifies whether an interactive user can be involved in selecting a client credential at runtime.</span></span> <span data-ttu-id="031dd-116">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="031dd-116">The default value is `true`.</span></span>|  
|`type`|<span data-ttu-id="031dd-117">Ciąg określający typ tego elementu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="031dd-117">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="031dd-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="031dd-118">Child Elements</span></span>  
  
|<span data-ttu-id="031dd-119">Element</span><span class="sxs-lookup"><span data-stu-id="031dd-119">Element</span></span>|<span data-ttu-id="031dd-120">Opis</span><span class="sxs-lookup"><span data-stu-id="031dd-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="031dd-121">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="031dd-121">\<clientCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md)|<span data-ttu-id="031dd-122">Określa certyfikat używany do uwierzytelniania klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="031dd-122">Specifies the certificate used to authenticate the client to the service.</span></span> <span data-ttu-id="031dd-123">Ten element jest typu <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.</span><span class="sxs-lookup"><span data-stu-id="031dd-123">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.</span></span>|  
|[<span data-ttu-id="031dd-124">\<httpDigest ></span><span class="sxs-lookup"><span data-stu-id="031dd-124">\<httpDigest></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/httpdigest-element.md)|<span data-ttu-id="031dd-125">Określa skrót używany do uwierzytelniania klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="031dd-125">Specifies a digest used to authenticate the client to the service.</span></span> <span data-ttu-id="031dd-126">Ten element jest typu <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.</span><span class="sxs-lookup"><span data-stu-id="031dd-126">This element is of type <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.</span></span>|  
|[<span data-ttu-id="031dd-127">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="031dd-127">\<issuedToken></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|<span data-ttu-id="031dd-128">Określa typ niestandardowy token używany do uwierzytelniania klienta do Secure Token Service (STS).</span><span class="sxs-lookup"><span data-stu-id="031dd-128">Specifies a custom token type used to authenticate the client to a Secure Token Service (STS).</span></span> <span data-ttu-id="031dd-129">Ten element jest typu <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.</span><span class="sxs-lookup"><span data-stu-id="031dd-129">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.</span></span>|  
|[<span data-ttu-id="031dd-130">\<peer ></span><span class="sxs-lookup"><span data-stu-id="031dd-130">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|<span data-ttu-id="031dd-131">Określa bieżące poświadczenie elementu równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="031dd-131">Specifies a current peer credential.</span></span> <span data-ttu-id="031dd-132">Ten element jest typu <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span><span class="sxs-lookup"><span data-stu-id="031dd-132">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[<span data-ttu-id="031dd-133">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="031dd-133">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="031dd-134">Określa certyfikat używany do uwierzytelniania usługi dla klienta i zapewnia strukturę do ustawiania opcji certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="031dd-134">Specifies the certificate used to authenticate the service to the client and provides a structure for setting certificate options.</span></span> <span data-ttu-id="031dd-135">Ten certyfikat musi być dostarczony poza pasmem z usługi do klienta.</span><span class="sxs-lookup"><span data-stu-id="031dd-135">This certificate must be supplied out-of-band from the service to the client.</span></span> <span data-ttu-id="031dd-136">Ten element jest typu <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.</span><span class="sxs-lookup"><span data-stu-id="031dd-136">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.</span></span>|  
|[<span data-ttu-id="031dd-137">\<Windows ></span><span class="sxs-lookup"><span data-stu-id="031dd-137">\<windows></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/windows-of-clientcredentials-element.md)|<span data-ttu-id="031dd-138">Określa poświadczenia systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="031dd-138">Specifies a Windows credential.</span></span> <span data-ttu-id="031dd-139">Wartość domyślna to poświadczenie bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="031dd-139">The default is the credential of the current thread.</span></span> <span data-ttu-id="031dd-140">Ten element jest typu <xref:System.ServiceModel.Configuration.WindowsClientElement>.</span><span class="sxs-lookup"><span data-stu-id="031dd-140">This element is of type <xref:System.ServiceModel.Configuration.WindowsClientElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="031dd-141">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="031dd-141">Parent Elements</span></span>  
  
|<span data-ttu-id="031dd-142">Element</span><span class="sxs-lookup"><span data-stu-id="031dd-142">Element</span></span>|<span data-ttu-id="031dd-143">Opis</span><span class="sxs-lookup"><span data-stu-id="031dd-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="031dd-144">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="031dd-144">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="031dd-145">Określa zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="031dd-145">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="031dd-146">Uwagi</span><span class="sxs-lookup"><span data-stu-id="031dd-146">Remarks</span></span>  
 <span data-ttu-id="031dd-147">Poświadczenia klienta są używane do uwierzytelniania klienta do usług w przypadkach, gdy jest wymagane uwierzytelnianie wzajemne.</span><span class="sxs-lookup"><span data-stu-id="031dd-147">Client credentials are used to authenticate the client to services in cases where mutual authentication is required.</span></span> <span data-ttu-id="031dd-148">Ta sekcja konfiguracji może również określić usługi certyfikatów w scenariuszach, gdzie klient musi Zabezpieczanie komunikatów do usługi za pomocą certyfikatu usługi.</span><span class="sxs-lookup"><span data-stu-id="031dd-148">This configuration section can also be used to specify service certificates for scenarios where the client must secure messages to a service with the service's certificate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="031dd-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="031dd-149">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 [<span data-ttu-id="031dd-150">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="031dd-150">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="031dd-151">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="031dd-151">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
