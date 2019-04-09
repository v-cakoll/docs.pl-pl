---
title: <add> z <allowedAudienceUris>
ms.date: 03/30/2017
ms.assetid: 4e7b7637-e0ea-4a91-988f-6b6ef28d9fc3
ms.openlocfilehash: a3ad50462cfa268a1826b62603110be3c5ba33db
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59148281"
---
# <a name="add-of-allowedaudienceuris"></a><span data-ttu-id="ebc44-102">\<Dodaj > z \<allowedAudienceUris ></span><span class="sxs-lookup"><span data-stu-id="ebc44-102">\<add> of \<allowedAudienceUris></span></span>
<span data-ttu-id="ebc44-103">Dodaje identyfikator Uri elementu docelowego dla którego <xref:System.IdentityModel.Tokens.SamlSecurityToken> tokenu zabezpieczeń może być kierowany aby były uważane za prawidłowe przez <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="ebc44-103">Adds a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>  
  
 <span data-ttu-id="ebc44-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ebc44-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ebc44-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="ebc44-105">\<behaviors></span></span>  
<span data-ttu-id="ebc44-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="ebc44-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="ebc44-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="ebc44-107">\<behavior></span></span>  
<span data-ttu-id="ebc44-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="ebc44-108">\<serviceCredentials></span></span>  
<span data-ttu-id="ebc44-109">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="ebc44-109">\<issuedTokenAuthentication></span></span>  
<span data-ttu-id="ebc44-110">\<allowedAudienceUris></span><span class="sxs-lookup"><span data-stu-id="ebc44-110">\<allowedAudienceUris></span></span>  
<span data-ttu-id="ebc44-111">\<Dodaj >, element dla \<allowedAudienceUris ></span><span class="sxs-lookup"><span data-stu-id="ebc44-111">\<add> element for \<allowedAudienceUris></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebc44-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="ebc44-112">Syntax</span></span>  
  
```xml  
<allowedAudienceUris>
  <add allowedAudienceUri="String" />
</allowedAudienceUris>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ebc44-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ebc44-113">Attributes and Elements</span></span>  
 <span data-ttu-id="ebc44-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ebc44-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ebc44-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ebc44-115">Attributes</span></span>  
  
|<span data-ttu-id="ebc44-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ebc44-116">Attribute</span></span>|<span data-ttu-id="ebc44-117">Opis</span><span class="sxs-lookup"><span data-stu-id="ebc44-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ebc44-118">allowedAudienceUri</span><span class="sxs-lookup"><span data-stu-id="ebc44-118">allowedAudienceUri</span></span>|<span data-ttu-id="ebc44-119">Ciąg, który zawiera docelowy identyfikator Uri dla którego <xref:System.IdentityModel.Tokens.SamlSecurityToken> tokenu zabezpieczeń może być kierowany aby były uważane za prawidłowe przez <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="ebc44-119">A string that contains a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ebc44-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ebc44-120">Child Elements</span></span>  
 <span data-ttu-id="ebc44-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="ebc44-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ebc44-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ebc44-122">Parent Elements</span></span>  
  
|<span data-ttu-id="ebc44-123">Element</span><span class="sxs-lookup"><span data-stu-id="ebc44-123">Element</span></span>|<span data-ttu-id="ebc44-124">Opis</span><span class="sxs-lookup"><span data-stu-id="ebc44-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ebc44-125">\<allowedAudienceUris></span><span class="sxs-lookup"><span data-stu-id="ebc44-125">\<allowedAudienceUris></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowedaudienceuris.md)|<span data-ttu-id="ebc44-126">Reprezentuje kolekcję docelowych URI, dla którego <xref:System.IdentityModel.Tokens.SamlSecurityToken> tokenu zabezpieczeń może być kierowany aby były uważane za prawidłowe przez <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="ebc44-126">Represents a collection of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ebc44-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ebc44-127">Remarks</span></span>  
 <span data-ttu-id="ebc44-128">Należy używać tej kolekcji w federacyjnej aplikacji, która korzysta z usługi tokenu zabezpieczającego (STS) wysyłający <xref:System.IdentityModel.Tokens.SamlSecurityToken> tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="ebc44-128">You should use this collection in a federated application that utilizes a security token service (STS) that issues <xref:System.IdentityModel.Tokens.SamlSecurityToken> security tokens.</span></span> <span data-ttu-id="ebc44-129">Gdy Usługa STS wystawia token zabezpieczający, można określić identyfikator URI usługi sieci Web, dla których token zabezpieczający jest przeznaczony przez dodanie <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> do tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="ebc44-129">When the STS issues the security token, it can specify the URI of the Web services for which the security token is intended by adding a <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> to the security token.</span></span> <span data-ttu-id="ebc44-130">Umożliwiająca <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> odbiorcy usługi sieci Web sprawdzić, czy token zabezpieczeń jest przeznaczony dla tej usługi sieci Web, określając, że ten test ma się zdarzyć, wykonując następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="ebc44-130">That allows the <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> for the recipient Web service to verify that the issued security token is intended for this Web service by specifying that this check should happen by doing the following:</span></span>  
  
-   <span data-ttu-id="ebc44-131">Ustaw `audienceUriMode` atrybutu `<issuedTokenAuthentication>` do <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> lub <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span><span class="sxs-lookup"><span data-stu-id="ebc44-131">Set the `audienceUriMode` attribute of `<issuedTokenAuthentication>` to <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> or <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span></span>  
  
-   <span data-ttu-id="ebc44-132">Określ zbiór prawidłowe identyfikatory URI, dodając identyfikatory URI do tej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="ebc44-132">Specify the set of valid URIs, by adding the URIs to this collection.</span></span>  
  
 <span data-ttu-id="ebc44-133">Aby uzyskać więcej informacji, zobacz <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="ebc44-133">For more information, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span></span>  
  
 <span data-ttu-id="ebc44-134">Aby uzyskać więcej informacji na temat korzystania z tego elementu konfiguracji, zobacz [jak: Konfigurowanie poświadczeń usługi federacyjnej](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="ebc44-134">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebc44-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ebc44-135">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.AllowedAudienceUris%2A>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElementCollection>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowedAudienceUris%2A>
- [<span data-ttu-id="ebc44-136">\<allowedAudienceUris></span><span class="sxs-lookup"><span data-stu-id="ebc44-136">\<allowedAudienceUris></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowedaudienceuris.md)
- [<span data-ttu-id="ebc44-137">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="ebc44-137">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)
- [<span data-ttu-id="ebc44-138">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="ebc44-138">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="ebc44-139">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="ebc44-139">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="ebc44-140">Instrukcje: konfigurowanie poświadczeń usługi federacyjnej</span><span class="sxs-lookup"><span data-stu-id="ebc44-140">How to: Configure Credentials on a Federation Service</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
