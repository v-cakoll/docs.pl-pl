---
title: <add> dla <allowedAudienceUris>
ms.date: 03/30/2017
ms.assetid: 4e7b7637-e0ea-4a91-988f-6b6ef28d9fc3
ms.openlocfilehash: 64f0dd5c97ddfcd2fffd8ff4820d02af8c1ced54
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926892"
---
# <a name="add-of-allowedaudienceuris"></a><span data-ttu-id="98cfd-102">\<Dodawanie > \<AllowedAudienceUris ></span><span class="sxs-lookup"><span data-stu-id="98cfd-102">\<add> of \<allowedAudienceUris></span></span>
<span data-ttu-id="98cfd-103">Dodaje docelowy identyfikator URI, dla którego <xref:System.IdentityModel.Tokens.SamlSecurityToken> może być przeznaczony token zabezpieczający, aby można go było traktować jako ważny <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> przez wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="98cfd-103">Adds a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>  
  
 <span data-ttu-id="98cfd-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="98cfd-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="98cfd-105">\<> zachowań</span><span class="sxs-lookup"><span data-stu-id="98cfd-105">\<behaviors></span></span>  
<span data-ttu-id="98cfd-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="98cfd-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="98cfd-107">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="98cfd-107">\<behavior></span></span>  
<span data-ttu-id="98cfd-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="98cfd-108">\<serviceCredentials></span></span>  
<span data-ttu-id="98cfd-109">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="98cfd-109">\<issuedTokenAuthentication></span></span>  
<span data-ttu-id="98cfd-110">\<allowedAudienceUris></span><span class="sxs-lookup"><span data-stu-id="98cfd-110">\<allowedAudienceUris></span></span>  
<span data-ttu-id="98cfd-111">\<Dodaj element > dla \<AllowedAudienceUris ></span><span class="sxs-lookup"><span data-stu-id="98cfd-111">\<add> element for \<allowedAudienceUris></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98cfd-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="98cfd-112">Syntax</span></span>  
  
```xml  
<allowedAudienceUris>
  <add allowedAudienceUri="String" />
</allowedAudienceUris>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="98cfd-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="98cfd-113">Attributes and Elements</span></span>  
 <span data-ttu-id="98cfd-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="98cfd-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="98cfd-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="98cfd-115">Attributes</span></span>  
  
|<span data-ttu-id="98cfd-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="98cfd-116">Attribute</span></span>|<span data-ttu-id="98cfd-117">Opis</span><span class="sxs-lookup"><span data-stu-id="98cfd-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="98cfd-118">allowedAudienceUri</span><span class="sxs-lookup"><span data-stu-id="98cfd-118">allowedAudienceUri</span></span>|<span data-ttu-id="98cfd-119">Ciąg zawierający docelowy identyfikator URI, dla którego <xref:System.IdentityModel.Tokens.SamlSecurityToken> może być przeznaczony token zabezpieczający, aby można go było traktować jako ważny <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> przez wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="98cfd-119">A string that contains a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="98cfd-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="98cfd-120">Child Elements</span></span>  
 <span data-ttu-id="98cfd-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="98cfd-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="98cfd-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="98cfd-122">Parent Elements</span></span>  
  
|<span data-ttu-id="98cfd-123">Element</span><span class="sxs-lookup"><span data-stu-id="98cfd-123">Element</span></span>|<span data-ttu-id="98cfd-124">Opis</span><span class="sxs-lookup"><span data-stu-id="98cfd-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="98cfd-125">\<allowedAudienceUris></span><span class="sxs-lookup"><span data-stu-id="98cfd-125">\<allowedAudienceUris></span></span>](allowedaudienceuris.md)|<span data-ttu-id="98cfd-126">Reprezentuje kolekcję docelowych identyfikatorów URI, dla których <xref:System.IdentityModel.Tokens.SamlSecurityToken> może być przeznaczony token zabezpieczający, aby można je było traktować jako prawidłowe <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> przez wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="98cfd-126">Represents a collection of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="98cfd-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="98cfd-127">Remarks</span></span>  
 <span data-ttu-id="98cfd-128">Tej kolekcji należy używać w aplikacji federacyjnej, która używa usługi tokenu zabezpieczającego (STS), która wystawia <xref:System.IdentityModel.Tokens.SamlSecurityToken> tokeny zabezpieczające.</span><span class="sxs-lookup"><span data-stu-id="98cfd-128">You should use this collection in a federated application that utilizes a security token service (STS) that issues <xref:System.IdentityModel.Tokens.SamlSecurityToken> security tokens.</span></span> <span data-ttu-id="98cfd-129">Gdy usługa STS wystawia token zabezpieczający, może określić identyfikator URI usług sieci Web, dla których jest przeznaczony token zabezpieczający poprzez dodanie <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> do tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="98cfd-129">When the STS issues the security token, it can specify the URI of the Web services for which the security token is intended by adding a <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> to the security token.</span></span> <span data-ttu-id="98cfd-130">Dzięki temu <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> usługa sieci Web odbiorcy może sprawdzić, czy wystawiony token zabezpieczający jest przeznaczony dla tej usługi sieci Web, określając, że to sprawdzenie powinno nastąpić, wykonując następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="98cfd-130">That allows the <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> for the recipient Web service to verify that the issued security token is intended for this Web service by specifying that this check should happen by doing the following:</span></span>  
  
- <span data-ttu-id="98cfd-131">`audienceUriMode` Ustaw atrybut<xref:System.IdentityModel.Selectors.AudienceUriMode.Always> na lub .<xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly> `<issuedTokenAuthentication>`</span><span class="sxs-lookup"><span data-stu-id="98cfd-131">Set the `audienceUriMode` attribute of `<issuedTokenAuthentication>` to <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> or <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span></span>  
  
- <span data-ttu-id="98cfd-132">Określ zestaw prawidłowych identyfikatorów URI, dodając identyfikatory URI do tej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="98cfd-132">Specify the set of valid URIs, by adding the URIs to this collection.</span></span>  
  
 <span data-ttu-id="98cfd-133">Aby uzyskać więcej informacji, zobacz <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="98cfd-133">For more information, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span></span>  
  
 <span data-ttu-id="98cfd-134">Aby uzyskać więcej informacji na temat używania tego elementu konfiguracji [, zobacz How to: Skonfiguruj poświadczenia na usługa federacyjna](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="98cfd-134">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98cfd-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="98cfd-135">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.AllowedAudienceUris%2A>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElementCollection>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowedAudienceUris%2A>
- [<span data-ttu-id="98cfd-136">\<allowedAudienceUris></span><span class="sxs-lookup"><span data-stu-id="98cfd-136">\<allowedAudienceUris></span></span>](allowedaudienceuris.md)
- [<span data-ttu-id="98cfd-137">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="98cfd-137">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)
- [<span data-ttu-id="98cfd-138">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="98cfd-138">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="98cfd-139">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="98cfd-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="98cfd-140">Instrukcje: Konfigurowanie poświadczeń na usługa federacyjna</span><span class="sxs-lookup"><span data-stu-id="98cfd-140">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
