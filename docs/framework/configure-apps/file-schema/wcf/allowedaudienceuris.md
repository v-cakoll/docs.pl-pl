---
title: <allowedAudienceUris>
ms.date: 03/30/2017
ms.assetid: 0f4dc73d-d95d-4193-9755-7df4cf2b8e1c
ms.openlocfilehash: ea2d4bb285047939992e9b191abc2dc896bdaa6a
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398277"
---
# <a name="allowedaudienceuris"></a><span data-ttu-id="bf4d3-101">\<allowedAudienceUris></span><span class="sxs-lookup"><span data-stu-id="bf4d3-101">\<allowedAudienceUris></span></span>
<span data-ttu-id="bf4d3-102">Reprezentuje kolekcję docelowych identyfikatorów URI, dla których <xref:System.IdentityModel.Tokens.SamlSecurityToken> może być przeznaczony token zabezpieczający, aby można je było traktować jako prawidłowe <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> przez wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="bf4d3-102">Represents a collection of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>  
  
<span data-ttu-id="bf4d3-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="bf4d3-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="bf4d3-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="bf4d3-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="bf4d3-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowań**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="bf4d3-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="bf4d3-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> serviceBehaviors**](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="bf4d3-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="bf4d3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowania**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="bf4d3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="bf4d3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> ServiceCredentials**](servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="bf4d3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)</span></span>\
<span data-ttu-id="bf4d3-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<issuedTokenAuthentication >** ](issuedtokenauthentication-of-servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="bf4d3-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenAuthentication>**](issuedtokenauthentication-of-servicecredentials.md)</span></span>\
<span data-ttu-id="bf4d3-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<allowedAudienceUris >**</span><span class="sxs-lookup"><span data-stu-id="bf4d3-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<allowedAudienceUris>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf4d3-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="bf4d3-111">Syntax</span></span>  
  
```xml  
<allowedAudienceUris>
  <add allowedAudienceUri="String" />
</allowedAudienceUris>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bf4d3-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="bf4d3-112">Attributes and Elements</span></span>  
 <span data-ttu-id="bf4d3-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="bf4d3-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bf4d3-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="bf4d3-114">Attributes</span></span>  
 <span data-ttu-id="bf4d3-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="bf4d3-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bf4d3-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="bf4d3-116">Child Elements</span></span>  
  
|<span data-ttu-id="bf4d3-117">Element</span><span class="sxs-lookup"><span data-stu-id="bf4d3-117">Element</span></span>|<span data-ttu-id="bf4d3-118">Opis</span><span class="sxs-lookup"><span data-stu-id="bf4d3-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bf4d3-119">\<add></span><span class="sxs-lookup"><span data-stu-id="bf4d3-119">\<add></span></span>](add-of-allowedaudienceuris.md)|<span data-ttu-id="bf4d3-120">Dodaje docelowy identyfikator URI, dla którego <xref:System.IdentityModel.Tokens.SamlSecurityToken> może być przeznaczony token zabezpieczający, aby można go było traktować jako ważny <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> przez wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="bf4d3-120">Adds a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bf4d3-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="bf4d3-121">Parent Elements</span></span>  
  
|<span data-ttu-id="bf4d3-122">Element</span><span class="sxs-lookup"><span data-stu-id="bf4d3-122">Element</span></span>|<span data-ttu-id="bf4d3-123">Opis</span><span class="sxs-lookup"><span data-stu-id="bf4d3-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bf4d3-124">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="bf4d3-124">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="bf4d3-125">Określa token wystawiony jako poświadczenie usługi.</span><span class="sxs-lookup"><span data-stu-id="bf4d3-125">Specifies a token issued as a service credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf4d3-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bf4d3-126">Remarks</span></span>  
 <span data-ttu-id="bf4d3-127">Tej kolekcji należy używać w aplikacji federacyjnej, która używa usługi tokenu zabezpieczającego (STS), która wystawia <xref:System.IdentityModel.Tokens.SamlSecurityToken> tokeny zabezpieczające.</span><span class="sxs-lookup"><span data-stu-id="bf4d3-127">You should use this collection in a federated application that utilizes a security token service (STS) that issues <xref:System.IdentityModel.Tokens.SamlSecurityToken> security tokens.</span></span> <span data-ttu-id="bf4d3-128">Gdy usługa STS wystawia token zabezpieczający, może określić identyfikator URI usług sieci Web, dla których jest przeznaczony token zabezpieczający poprzez dodanie <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> do tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="bf4d3-128">When the STS issues the security token, it can specify the URI of the Web services for which the security token is intended by adding a <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> to the security token.</span></span> <span data-ttu-id="bf4d3-129">Dzięki temu <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> usługa sieci Web odbiorcy może sprawdzić, czy wystawiony token zabezpieczający jest przeznaczony dla tej usługi sieci Web, określając, że to sprawdzenie powinno nastąpić, wykonując następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="bf4d3-129">That allows the <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> for the recipient Web service to verify that the issued security token is intended for this Web service by specifying that this check should happen by doing the following:</span></span>  
  
- <span data-ttu-id="bf4d3-130">`audienceUriMode` Ustaw atrybut<xref:System.IdentityModel.Selectors.AudienceUriMode.Always> na lub .<xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly> `<issuedTokenAuthentication>`</span><span class="sxs-lookup"><span data-stu-id="bf4d3-130">Set the `audienceUriMode` attribute of `<issuedTokenAuthentication>` to <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> or <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span></span>  
  
- <span data-ttu-id="bf4d3-131">Określ zestaw prawidłowych identyfikatorów URI, dodając identyfikatory URI do tej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="bf4d3-131">Specify the set of valid URIs, by adding the URIs to this collection.</span></span>  
  
 <span data-ttu-id="bf4d3-132">Aby uzyskać więcej informacji, zobacz <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="bf4d3-132">For more information, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span></span>  
  
 <span data-ttu-id="bf4d3-133">Aby uzyskać więcej informacji na temat używania tego elementu konfiguracji [, zobacz How to: Skonfiguruj poświadczenia na usługa federacyjna](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="bf4d3-133">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf4d3-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bf4d3-134">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.AllowedAudienceUris%2A>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElementCollection>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowedAudienceUris%2A>
- [<span data-ttu-id="bf4d3-135">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="bf4d3-135">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)
- [<span data-ttu-id="bf4d3-136">\<add></span><span class="sxs-lookup"><span data-stu-id="bf4d3-136">\<add></span></span>](add-of-allowedaudienceuris.md)
- [<span data-ttu-id="bf4d3-137">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="bf4d3-137">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="bf4d3-138">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="bf4d3-138">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="bf4d3-139">Instrukcje: Konfigurowanie poświadczeń na usługa federacyjna</span><span class="sxs-lookup"><span data-stu-id="bf4d3-139">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
