---
title: <allowedAudienceUris>
ms.date: 03/30/2017
ms.assetid: 0f4dc73d-d95d-4193-9755-7df4cf2b8e1c
ms.openlocfilehash: f188f1ecbfc172995ec7cf6dd38b184c2a96ed55
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592618"
---
# <a name="allowedaudienceuris"></a><span data-ttu-id="f414d-101">\<allowedAudienceUris></span><span class="sxs-lookup"><span data-stu-id="f414d-101">\<allowedAudienceUris></span></span>
<span data-ttu-id="f414d-102">Reprezentuje kolekcję docelowych URI, dla którego <xref:System.IdentityModel.Tokens.SamlSecurityToken> tokenu zabezpieczeń może być kierowany aby były uważane za prawidłowe przez <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="f414d-102">Represents a collection of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>  
  
 <span data-ttu-id="f414d-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f414d-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="f414d-104">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="f414d-104">\<behaviors></span></span>  
<span data-ttu-id="f414d-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="f414d-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="f414d-106">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="f414d-106">\<behavior></span></span>  
<span data-ttu-id="f414d-107">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="f414d-107">\<serviceCredentials></span></span>  
<span data-ttu-id="f414d-108">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="f414d-108">\<issuedTokenAuthentication></span></span>  
<span data-ttu-id="f414d-109">\<allowedAudienceUris></span><span class="sxs-lookup"><span data-stu-id="f414d-109">\<allowedAudienceUris></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f414d-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="f414d-110">Syntax</span></span>  
  
```xml  
<allowedAudienceUris>
  <add allowedAudienceUri="String" />
</allowedAudienceUris>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f414d-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f414d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="f414d-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f414d-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f414d-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f414d-113">Attributes</span></span>  
 <span data-ttu-id="f414d-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="f414d-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f414d-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f414d-115">Child Elements</span></span>  
  
|<span data-ttu-id="f414d-116">Element</span><span class="sxs-lookup"><span data-stu-id="f414d-116">Element</span></span>|<span data-ttu-id="f414d-117">Opis</span><span class="sxs-lookup"><span data-stu-id="f414d-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f414d-118">\<add></span><span class="sxs-lookup"><span data-stu-id="f414d-118">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowedaudienceuris.md)|<span data-ttu-id="f414d-119">Dodaje identyfikator Uri elementu docelowego dla którego <xref:System.IdentityModel.Tokens.SamlSecurityToken> tokenu zabezpieczeń może być kierowany aby były uważane za prawidłowe przez <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="f414d-119">Adds a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f414d-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f414d-120">Parent Elements</span></span>  
  
|<span data-ttu-id="f414d-121">Element</span><span class="sxs-lookup"><span data-stu-id="f414d-121">Element</span></span>|<span data-ttu-id="f414d-122">Opis</span><span class="sxs-lookup"><span data-stu-id="f414d-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f414d-123">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="f414d-123">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="f414d-124">Określa token wydany jako poświadczenie usługi.</span><span class="sxs-lookup"><span data-stu-id="f414d-124">Specifies a token issued as a service credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f414d-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f414d-125">Remarks</span></span>  
 <span data-ttu-id="f414d-126">Należy używać tej kolekcji w federacyjnej aplikacji, która korzysta z usługi tokenu zabezpieczającego (STS) wysyłający <xref:System.IdentityModel.Tokens.SamlSecurityToken> tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="f414d-126">You should use this collection in a federated application that utilizes a security token service (STS) that issues <xref:System.IdentityModel.Tokens.SamlSecurityToken> security tokens.</span></span> <span data-ttu-id="f414d-127">Gdy Usługa STS wystawia token zabezpieczający, można określić identyfikator URI usługi sieci Web, dla których token zabezpieczający jest przeznaczony przez dodanie <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> do tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="f414d-127">When the STS issues the security token, it can specify the URI of the Web services for which the security token is intended by adding a <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> to the security token.</span></span> <span data-ttu-id="f414d-128">Umożliwiająca <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> odbiorcy usługi sieci Web sprawdzić, czy token zabezpieczeń jest przeznaczony dla tej usługi sieci Web, określając, że ten test ma się zdarzyć, wykonując następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="f414d-128">That allows the <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> for the recipient Web service to verify that the issued security token is intended for this Web service by specifying that this check should happen by doing the following:</span></span>  
  
- <span data-ttu-id="f414d-129">Ustaw `audienceUriMode` atrybutu `<issuedTokenAuthentication>` do <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> lub <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span><span class="sxs-lookup"><span data-stu-id="f414d-129">Set the `audienceUriMode` attribute of `<issuedTokenAuthentication>` to <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> or <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span></span>  
  
- <span data-ttu-id="f414d-130">Określ zbiór prawidłowe identyfikatory URI, dodając identyfikatory URI do tej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="f414d-130">Specify the set of valid URIs, by adding the URIs to this collection.</span></span>  
  
 <span data-ttu-id="f414d-131">Aby uzyskać więcej informacji, zobacz <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="f414d-131">For more information, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span></span>  
  
 <span data-ttu-id="f414d-132">Aby uzyskać więcej informacji na temat korzystania z tego elementu konfiguracji, zobacz [jak: Konfigurowanie poświadczeń usługi federacyjnej](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="f414d-132">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f414d-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f414d-133">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.AllowedAudienceUris%2A>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElementCollection>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowedAudienceUris%2A>
- [<span data-ttu-id="f414d-134">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="f414d-134">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)
- [<span data-ttu-id="f414d-135">\<add></span><span class="sxs-lookup"><span data-stu-id="f414d-135">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowedaudienceuris.md)
- [<span data-ttu-id="f414d-136">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="f414d-136">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="f414d-137">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="f414d-137">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="f414d-138">Instrukcje: Konfigurowanie poświadczeń usługi federacyjnej</span><span class="sxs-lookup"><span data-stu-id="f414d-138">How to: Configure Credentials on a Federation Service</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
