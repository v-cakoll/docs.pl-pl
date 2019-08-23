---
title: <allowedAudienceUris>
ms.date: 03/30/2017
ms.assetid: 0f4dc73d-d95d-4193-9755-7df4cf2b8e1c
ms.openlocfilehash: 03888600a89d72f5216c8c8cac21c9da96879ba8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919974"
---
# <a name="allowedaudienceuris"></a><span data-ttu-id="182d0-101">\<allowedAudienceUris></span><span class="sxs-lookup"><span data-stu-id="182d0-101">\<allowedAudienceUris></span></span>
<span data-ttu-id="182d0-102">Reprezentuje kolekcję docelowych identyfikatorów URI, dla których <xref:System.IdentityModel.Tokens.SamlSecurityToken> może być przeznaczony token zabezpieczający, aby można je było traktować jako prawidłowe <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> przez wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="182d0-102">Represents a collection of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>  
  
 <span data-ttu-id="182d0-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="182d0-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="182d0-104">\<> zachowań</span><span class="sxs-lookup"><span data-stu-id="182d0-104">\<behaviors></span></span>  
<span data-ttu-id="182d0-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="182d0-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="182d0-106">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="182d0-106">\<behavior></span></span>  
<span data-ttu-id="182d0-107">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="182d0-107">\<serviceCredentials></span></span>  
<span data-ttu-id="182d0-108">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="182d0-108">\<issuedTokenAuthentication></span></span>  
<span data-ttu-id="182d0-109">\<allowedAudienceUris></span><span class="sxs-lookup"><span data-stu-id="182d0-109">\<allowedAudienceUris></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="182d0-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="182d0-110">Syntax</span></span>  
  
```xml  
<allowedAudienceUris>
  <add allowedAudienceUri="String" />
</allowedAudienceUris>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="182d0-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="182d0-111">Attributes and Elements</span></span>  
 <span data-ttu-id="182d0-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="182d0-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="182d0-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="182d0-113">Attributes</span></span>  
 <span data-ttu-id="182d0-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="182d0-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="182d0-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="182d0-115">Child Elements</span></span>  
  
|<span data-ttu-id="182d0-116">Element</span><span class="sxs-lookup"><span data-stu-id="182d0-116">Element</span></span>|<span data-ttu-id="182d0-117">Opis</span><span class="sxs-lookup"><span data-stu-id="182d0-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="182d0-118">\<add></span><span class="sxs-lookup"><span data-stu-id="182d0-118">\<add></span></span>](add-of-allowedaudienceuris.md)|<span data-ttu-id="182d0-119">Dodaje docelowy identyfikator URI, dla którego <xref:System.IdentityModel.Tokens.SamlSecurityToken> może być przeznaczony token zabezpieczający, aby można go było traktować jako ważny <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> przez wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="182d0-119">Adds a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="182d0-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="182d0-120">Parent Elements</span></span>  
  
|<span data-ttu-id="182d0-121">Element</span><span class="sxs-lookup"><span data-stu-id="182d0-121">Element</span></span>|<span data-ttu-id="182d0-122">Opis</span><span class="sxs-lookup"><span data-stu-id="182d0-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="182d0-123">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="182d0-123">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="182d0-124">Określa token wystawiony jako poświadczenie usługi.</span><span class="sxs-lookup"><span data-stu-id="182d0-124">Specifies a token issued as a service credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="182d0-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="182d0-125">Remarks</span></span>  
 <span data-ttu-id="182d0-126">Tej kolekcji należy używać w aplikacji federacyjnej, która używa usługi tokenu zabezpieczającego (STS), która wystawia <xref:System.IdentityModel.Tokens.SamlSecurityToken> tokeny zabezpieczające.</span><span class="sxs-lookup"><span data-stu-id="182d0-126">You should use this collection in a federated application that utilizes a security token service (STS) that issues <xref:System.IdentityModel.Tokens.SamlSecurityToken> security tokens.</span></span> <span data-ttu-id="182d0-127">Gdy usługa STS wystawia token zabezpieczający, może określić identyfikator URI usług sieci Web, dla których jest przeznaczony token zabezpieczający poprzez dodanie <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> do tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="182d0-127">When the STS issues the security token, it can specify the URI of the Web services for which the security token is intended by adding a <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> to the security token.</span></span> <span data-ttu-id="182d0-128">Dzięki temu <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> usługa sieci Web odbiorcy może sprawdzić, czy wystawiony token zabezpieczający jest przeznaczony dla tej usługi sieci Web, określając, że to sprawdzenie powinno nastąpić, wykonując następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="182d0-128">That allows the <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> for the recipient Web service to verify that the issued security token is intended for this Web service by specifying that this check should happen by doing the following:</span></span>  
  
- <span data-ttu-id="182d0-129">`audienceUriMode` Ustaw atrybut<xref:System.IdentityModel.Selectors.AudienceUriMode.Always> na lub .<xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly> `<issuedTokenAuthentication>`</span><span class="sxs-lookup"><span data-stu-id="182d0-129">Set the `audienceUriMode` attribute of `<issuedTokenAuthentication>` to <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> or <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span></span>  
  
- <span data-ttu-id="182d0-130">Określ zestaw prawidłowych identyfikatorów URI, dodając identyfikatory URI do tej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="182d0-130">Specify the set of valid URIs, by adding the URIs to this collection.</span></span>  
  
 <span data-ttu-id="182d0-131">Aby uzyskać więcej informacji, zobacz <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="182d0-131">For more information, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span></span>  
  
 <span data-ttu-id="182d0-132">Aby uzyskać więcej informacji na temat używania tego elementu konfiguracji [, zobacz How to: Skonfiguruj poświadczenia na usługa federacyjna](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="182d0-132">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="182d0-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="182d0-133">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.AllowedAudienceUris%2A>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElementCollection>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowedAudienceUris%2A>
- [<span data-ttu-id="182d0-134">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="182d0-134">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)
- [<span data-ttu-id="182d0-135">\<add></span><span class="sxs-lookup"><span data-stu-id="182d0-135">\<add></span></span>](add-of-allowedaudienceuris.md)
- [<span data-ttu-id="182d0-136">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="182d0-136">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="182d0-137">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="182d0-137">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="182d0-138">Instrukcje: Konfigurowanie poświadczeń na usługa federacyjna</span><span class="sxs-lookup"><span data-stu-id="182d0-138">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
