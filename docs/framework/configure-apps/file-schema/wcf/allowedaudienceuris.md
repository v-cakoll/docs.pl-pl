---
title: '&lt;allowedAudienceUris&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f4dc73d-d95d-4193-9755-7df4cf2b8e1c
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b3259b7e75c700befe3117563fd2d3da6e01f927
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltallowedaudienceurisgt"></a><span data-ttu-id="69165-102">&lt;allowedAudienceUris&gt;</span><span class="sxs-lookup"><span data-stu-id="69165-102">&lt;allowedAudienceUris&gt;</span></span>
<span data-ttu-id="69165-103">Reprezentuje kolekcję docelowych URI, dla którego <xref:System.IdentityModel.Tokens.SamlSecurityToken> tokenu zabezpieczeń może być kierowany aby były uważany za prawidłowy przez <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="69165-103">Represents a collection of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>  
  
 <span data-ttu-id="69165-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="69165-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="69165-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="69165-105">\<behaviors></span></span>  
<span data-ttu-id="69165-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="69165-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="69165-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="69165-107">\<behavior></span></span>  
<span data-ttu-id="69165-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="69165-108">\<serviceCredentials></span></span>  
<span data-ttu-id="69165-109">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="69165-109">\<issuedTokenAuthentication></span></span>  
<span data-ttu-id="69165-110">\<allowedAudienceUris ></span><span class="sxs-lookup"><span data-stu-id="69165-110">\<allowedAudienceUris></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69165-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="69165-111">Syntax</span></span>  
  
```xml  
<allowedAudienceUris>  
      <add allowedAudienceUri="String"/>  
</allowedAudienceUris>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="69165-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="69165-112">Attributes and Elements</span></span>  
 <span data-ttu-id="69165-113">W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="69165-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="69165-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="69165-114">Attributes</span></span>  
 <span data-ttu-id="69165-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="69165-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="69165-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="69165-116">Child Elements</span></span>  
  
|<span data-ttu-id="69165-117">Element</span><span class="sxs-lookup"><span data-stu-id="69165-117">Element</span></span>|<span data-ttu-id="69165-118">Opis</span><span class="sxs-lookup"><span data-stu-id="69165-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="69165-119">\<Dodaj ></span><span class="sxs-lookup"><span data-stu-id="69165-119">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowedaudienceuris.md)|<span data-ttu-id="69165-120">Dodaje obiekt docelowy identyfikator Uri dla którego <xref:System.IdentityModel.Tokens.SamlSecurityToken> tokenu zabezpieczeń może być kierowany aby były uważany za prawidłowy przez <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="69165-120">Adds a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="69165-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="69165-121">Parent Elements</span></span>  
  
|<span data-ttu-id="69165-122">Element</span><span class="sxs-lookup"><span data-stu-id="69165-122">Element</span></span>|<span data-ttu-id="69165-123">Opis</span><span class="sxs-lookup"><span data-stu-id="69165-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="69165-124">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="69165-124">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="69165-125">Określa token wydany jako poświadczenie usługi.</span><span class="sxs-lookup"><span data-stu-id="69165-125">Specifies a token issued as a service credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="69165-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="69165-126">Remarks</span></span>  
 <span data-ttu-id="69165-127">Należy korzystać z tej kolekcji w aplikacji federacyjnych, który korzysta z usługą tokenu zabezpieczeń (STS), który wystawia <xref:System.IdentityModel.Tokens.SamlSecurityToken> tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="69165-127">You should use this collection in a federated application that utilizes a security token service (STS) that issues <xref:System.IdentityModel.Tokens.SamlSecurityToken> security tokens.</span></span> <span data-ttu-id="69165-128">Jeśli usługa tokenu Zabezpieczającego wystawia token zabezpieczający, można określić identyfikator URI usługi sieci Web, dla których token zabezpieczający jest przeznaczony przez dodanie <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> do tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="69165-128">When the STS issues the security token, it can specify the URI of the Web services for which the security token is intended by adding a <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> to the security token.</span></span> <span data-ttu-id="69165-129">Która umożliwia <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> odbiorcy usługi sieci Web sprawdzić, czy token zabezpieczeń jest przeznaczony dla tej usługi sieci Web, określając, że ten test powinno się zdarzyć, wykonując następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="69165-129">That allows the <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> for the recipient Web service to verify that the issued security token is intended for this Web service by specifying that this check should happen by doing the following:</span></span>  
  
-   <span data-ttu-id="69165-130">Ustaw `audienceUriMode` atrybutu `<issuedTokenAuthentication>` do <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> lub <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span><span class="sxs-lookup"><span data-stu-id="69165-130">Set the `audienceUriMode` attribute of `<issuedTokenAuthentication>` to <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> or <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span></span>  
  
-   <span data-ttu-id="69165-131">Określ zbiór prawidłowymi identyfikatorami URI, dodając identyfikatory URI do tej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="69165-131">Specify the set of valid URIs, by adding the URIs to this collection.</span></span>  
  
 <span data-ttu-id="69165-132">Aby uzyskać więcej informacji, zobacz <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="69165-132">For more information, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span></span>  
  
 <span data-ttu-id="69165-133">Aby uzyskać więcej informacji na temat używania tego elementu konfiguracji, zobacz [porady: Konfigurowanie poświadczeń usługi federacyjnej](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="69165-133">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69165-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="69165-134">See Also</span></span>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.AllowedAudienceUris%2A>  
 <xref:System.ServiceModel.Configuration.AllowedAudienceUriElementCollection>  
 <xref:System.ServiceModel.Configuration.AllowedAudienceUriElement>  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowedAudienceUris%2A>  
 [<span data-ttu-id="69165-135">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="69165-135">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)  
 [<span data-ttu-id="69165-136">\<Dodaj ></span><span class="sxs-lookup"><span data-stu-id="69165-136">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowedaudienceuris.md)  
 [<span data-ttu-id="69165-137">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="69165-137">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="69165-138">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="69165-138">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="69165-139">Porady: Konfigurowanie poświadczeń usługi federacyjnej</span><span class="sxs-lookup"><span data-stu-id="69165-139">How to: Configure Credentials on a Federation Service</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
