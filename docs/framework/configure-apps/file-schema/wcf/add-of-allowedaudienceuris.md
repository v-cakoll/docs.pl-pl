---
title: <add> dla <allowedAudienceUris>
ms.date: 03/30/2017
ms.assetid: 4e7b7637-e0ea-4a91-988f-6b6ef28d9fc3
ms.openlocfilehash: e15cb2d3e525d39a321bbe9760ddb8d72b02fffa
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398355"
---
# <a name="add-of-allowedaudienceuris"></a><span data-ttu-id="bd308-102">\<Dodawanie > \<AllowedAudienceUris ></span><span class="sxs-lookup"><span data-stu-id="bd308-102">\<add> of \<allowedAudienceUris></span></span>
<span data-ttu-id="bd308-103">Dodaje docelowy identyfikator URI, dla którego <xref:System.IdentityModel.Tokens.SamlSecurityToken> może być przeznaczony token zabezpieczający, aby można go było traktować jako ważny <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> przez wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="bd308-103">Adds a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>  
  
<span data-ttu-id="bd308-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="bd308-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="bd308-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="bd308-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="bd308-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowań**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="bd308-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="bd308-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> serviceBehaviors**](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="bd308-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="bd308-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowania**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="bd308-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="bd308-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> ServiceCredentials**](servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="bd308-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)</span></span>\
<span data-ttu-id="bd308-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<issuedTokenAuthentication >** ](issuedtokenauthentication-of-servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="bd308-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenAuthentication>**](issuedtokenauthentication-of-servicecredentials.md)</span></span>\
<span data-ttu-id="bd308-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<allowedAudienceUris >** ](allowedaudienceuris.md)</span><span class="sxs-lookup"><span data-stu-id="bd308-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<allowedAudienceUris>**](allowedaudienceuris.md)</span></span>\
<span data-ttu-id="bd308-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Dodaj >**</span><span class="sxs-lookup"><span data-stu-id="bd308-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd308-113">Składnia</span><span class="sxs-lookup"><span data-stu-id="bd308-113">Syntax</span></span>  
  
```xml  
<allowedAudienceUris>
  <add allowedAudienceUri="String" />
</allowedAudienceUris>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bd308-114">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="bd308-114">Attributes and Elements</span></span>  
 <span data-ttu-id="bd308-115">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="bd308-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bd308-116">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="bd308-116">Attributes</span></span>  
  
|<span data-ttu-id="bd308-117">Atrybut</span><span class="sxs-lookup"><span data-stu-id="bd308-117">Attribute</span></span>|<span data-ttu-id="bd308-118">Opis</span><span class="sxs-lookup"><span data-stu-id="bd308-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bd308-119">allowedAudienceUri</span><span class="sxs-lookup"><span data-stu-id="bd308-119">allowedAudienceUri</span></span>|<span data-ttu-id="bd308-120">Ciąg zawierający docelowy identyfikator URI, dla którego <xref:System.IdentityModel.Tokens.SamlSecurityToken> może być przeznaczony token zabezpieczający, aby można go było traktować jako ważny <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> przez wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="bd308-120">A string that contains a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bd308-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="bd308-121">Child Elements</span></span>  
 <span data-ttu-id="bd308-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="bd308-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bd308-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="bd308-123">Parent Elements</span></span>  
  
|<span data-ttu-id="bd308-124">Element</span><span class="sxs-lookup"><span data-stu-id="bd308-124">Element</span></span>|<span data-ttu-id="bd308-125">Opis</span><span class="sxs-lookup"><span data-stu-id="bd308-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bd308-126">\<allowedAudienceUris></span><span class="sxs-lookup"><span data-stu-id="bd308-126">\<allowedAudienceUris></span></span>](allowedaudienceuris.md)|<span data-ttu-id="bd308-127">Reprezentuje kolekcję docelowych identyfikatorów URI, dla których <xref:System.IdentityModel.Tokens.SamlSecurityToken> może być przeznaczony token zabezpieczający, aby można je było traktować jako prawidłowe <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> przez wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="bd308-127">Represents a collection of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bd308-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bd308-128">Remarks</span></span>  
 <span data-ttu-id="bd308-129">Tej kolekcji należy używać w aplikacji federacyjnej, która używa usługi tokenu zabezpieczającego (STS), która wystawia <xref:System.IdentityModel.Tokens.SamlSecurityToken> tokeny zabezpieczające.</span><span class="sxs-lookup"><span data-stu-id="bd308-129">You should use this collection in a federated application that utilizes a security token service (STS) that issues <xref:System.IdentityModel.Tokens.SamlSecurityToken> security tokens.</span></span> <span data-ttu-id="bd308-130">Gdy usługa STS wystawia token zabezpieczający, może określić identyfikator URI usług sieci Web, dla których jest przeznaczony token zabezpieczający poprzez dodanie <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> do tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="bd308-130">When the STS issues the security token, it can specify the URI of the Web services for which the security token is intended by adding a <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> to the security token.</span></span> <span data-ttu-id="bd308-131">Dzięki temu <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> usługa sieci Web odbiorcy może sprawdzić, czy wystawiony token zabezpieczający jest przeznaczony dla tej usługi sieci Web, określając, że to sprawdzenie powinno nastąpić, wykonując następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="bd308-131">That allows the <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> for the recipient Web service to verify that the issued security token is intended for this Web service by specifying that this check should happen by doing the following:</span></span>  
  
- <span data-ttu-id="bd308-132">`audienceUriMode` Ustaw atrybut<xref:System.IdentityModel.Selectors.AudienceUriMode.Always> na lub .<xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly> `<issuedTokenAuthentication>`</span><span class="sxs-lookup"><span data-stu-id="bd308-132">Set the `audienceUriMode` attribute of `<issuedTokenAuthentication>` to <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> or <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span></span>  
  
- <span data-ttu-id="bd308-133">Określ zestaw prawidłowych identyfikatorów URI, dodając identyfikatory URI do tej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="bd308-133">Specify the set of valid URIs, by adding the URIs to this collection.</span></span>  
  
 <span data-ttu-id="bd308-134">Aby uzyskać więcej informacji, zobacz <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="bd308-134">For more information, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span></span>  
  
 <span data-ttu-id="bd308-135">Aby uzyskać więcej informacji na temat używania tego elementu konfiguracji [, zobacz How to: Skonfiguruj poświadczenia na usługa federacyjna](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="bd308-135">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd308-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bd308-136">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.AllowedAudienceUris%2A>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElementCollection>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowedAudienceUris%2A>
- [<span data-ttu-id="bd308-137">\<allowedAudienceUris></span><span class="sxs-lookup"><span data-stu-id="bd308-137">\<allowedAudienceUris></span></span>](allowedaudienceuris.md)
- [<span data-ttu-id="bd308-138">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="bd308-138">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)
- [<span data-ttu-id="bd308-139">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="bd308-139">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="bd308-140">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="bd308-140">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="bd308-141">Instrukcje: Konfigurowanie poświadczeń na usługa federacyjna</span><span class="sxs-lookup"><span data-stu-id="bd308-141">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
