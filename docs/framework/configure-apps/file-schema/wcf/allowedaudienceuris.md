---
title: '&lt;allowedAudienceUris&gt;'
ms.date: 03/30/2017
ms.assetid: 0f4dc73d-d95d-4193-9755-7df4cf2b8e1c
ms.openlocfilehash: b7a4ae230e9b8788d9ac23147a3fcf21637dadaf
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32754083"
---
# <a name="ltallowedaudienceurisgt"></a><span data-ttu-id="ece66-102">&lt;allowedAudienceUris&gt;</span><span class="sxs-lookup"><span data-stu-id="ece66-102">&lt;allowedAudienceUris&gt;</span></span>
<span data-ttu-id="ece66-103">Reprezentuje kolekcję docelowych URI, dla którego <xref:System.IdentityModel.Tokens.SamlSecurityToken> tokenu zabezpieczeń może być kierowany aby były uważany za prawidłowy przez <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="ece66-103">Represents a collection of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>  
  
 <span data-ttu-id="ece66-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ece66-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ece66-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="ece66-105">\<behaviors></span></span>  
<span data-ttu-id="ece66-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="ece66-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="ece66-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="ece66-107">\<behavior></span></span>  
<span data-ttu-id="ece66-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="ece66-108">\<serviceCredentials></span></span>  
<span data-ttu-id="ece66-109">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="ece66-109">\<issuedTokenAuthentication></span></span>  
<span data-ttu-id="ece66-110">\<allowedAudienceUris ></span><span class="sxs-lookup"><span data-stu-id="ece66-110">\<allowedAudienceUris></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ece66-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="ece66-111">Syntax</span></span>  
  
```xml  
<allowedAudienceUris>  
      <add allowedAudienceUri="String"/>  
</allowedAudienceUris>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ece66-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ece66-112">Attributes and Elements</span></span>  
 <span data-ttu-id="ece66-113">W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ece66-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ece66-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ece66-114">Attributes</span></span>  
 <span data-ttu-id="ece66-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="ece66-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ece66-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ece66-116">Child Elements</span></span>  
  
|<span data-ttu-id="ece66-117">Element</span><span class="sxs-lookup"><span data-stu-id="ece66-117">Element</span></span>|<span data-ttu-id="ece66-118">Opis</span><span class="sxs-lookup"><span data-stu-id="ece66-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ece66-119">\<add></span><span class="sxs-lookup"><span data-stu-id="ece66-119">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowedaudienceuris.md)|<span data-ttu-id="ece66-120">Dodaje obiekt docelowy identyfikator Uri dla którego <xref:System.IdentityModel.Tokens.SamlSecurityToken> tokenu zabezpieczeń może być kierowany aby były uważany za prawidłowy przez <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="ece66-120">Adds a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ece66-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ece66-121">Parent Elements</span></span>  
  
|<span data-ttu-id="ece66-122">Element</span><span class="sxs-lookup"><span data-stu-id="ece66-122">Element</span></span>|<span data-ttu-id="ece66-123">Opis</span><span class="sxs-lookup"><span data-stu-id="ece66-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ece66-124">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="ece66-124">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="ece66-125">Określa token wydany jako poświadczenie usługi.</span><span class="sxs-lookup"><span data-stu-id="ece66-125">Specifies a token issued as a service credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ece66-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ece66-126">Remarks</span></span>  
 <span data-ttu-id="ece66-127">Należy korzystać z tej kolekcji w aplikacji federacyjnych, który korzysta z usługą tokenu zabezpieczeń (STS), który wystawia <xref:System.IdentityModel.Tokens.SamlSecurityToken> tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="ece66-127">You should use this collection in a federated application that utilizes a security token service (STS) that issues <xref:System.IdentityModel.Tokens.SamlSecurityToken> security tokens.</span></span> <span data-ttu-id="ece66-128">Jeśli usługa tokenu Zabezpieczającego wystawia token zabezpieczający, można określić identyfikator URI usługi sieci Web, dla których token zabezpieczający jest przeznaczony przez dodanie <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> do tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="ece66-128">When the STS issues the security token, it can specify the URI of the Web services for which the security token is intended by adding a <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> to the security token.</span></span> <span data-ttu-id="ece66-129">Która umożliwia <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> odbiorcy usługi sieci Web sprawdzić, czy token zabezpieczeń jest przeznaczony dla tej usługi sieci Web, określając, że ten test powinno się zdarzyć, wykonując następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="ece66-129">That allows the <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> for the recipient Web service to verify that the issued security token is intended for this Web service by specifying that this check should happen by doing the following:</span></span>  
  
-   <span data-ttu-id="ece66-130">Ustaw `audienceUriMode` atrybutu `<issuedTokenAuthentication>` do <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> lub <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span><span class="sxs-lookup"><span data-stu-id="ece66-130">Set the `audienceUriMode` attribute of `<issuedTokenAuthentication>` to <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> or <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span></span>  
  
-   <span data-ttu-id="ece66-131">Określ zbiór prawidłowymi identyfikatorami URI, dodając identyfikatory URI do tej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="ece66-131">Specify the set of valid URIs, by adding the URIs to this collection.</span></span>  
  
 <span data-ttu-id="ece66-132">Aby uzyskać więcej informacji, zobacz <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="ece66-132">For more information, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span></span>  
  
 <span data-ttu-id="ece66-133">Aby uzyskać więcej informacji na temat używania tego elementu konfiguracji, zobacz [porady: Konfigurowanie poświadczeń usługi federacyjnej](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="ece66-133">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ece66-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ece66-134">See Also</span></span>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.AllowedAudienceUris%2A>  
 <xref:System.ServiceModel.Configuration.AllowedAudienceUriElementCollection>  
 <xref:System.ServiceModel.Configuration.AllowedAudienceUriElement>  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowedAudienceUris%2A>  
 [<span data-ttu-id="ece66-135">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="ece66-135">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)  
 [<span data-ttu-id="ece66-136">\<add></span><span class="sxs-lookup"><span data-stu-id="ece66-136">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowedaudienceuris.md)  
 [<span data-ttu-id="ece66-137">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="ece66-137">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="ece66-138">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="ece66-138">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="ece66-139">Instrukcje: konfigurowanie poświadczeń usługi federacyjnej</span><span class="sxs-lookup"><span data-stu-id="ece66-139">How to: Configure Credentials on a Federation Service</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
