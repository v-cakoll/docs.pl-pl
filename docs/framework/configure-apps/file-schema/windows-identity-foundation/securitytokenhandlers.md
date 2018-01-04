---
title: '&lt;securityTokenHandlers&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f11a631d-4094-4e11-bb03-4ede74b30281
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: de19fffdeae801163ec991ecf08d00b1286781d8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltsecuritytokenhandlersgt"></a><span data-ttu-id="b3fe6-102">&lt;securityTokenHandlers&gt;</span><span class="sxs-lookup"><span data-stu-id="b3fe6-102">&lt;securityTokenHandlers&gt;</span></span>
<span data-ttu-id="b3fe6-103">Określa kolekcję programów obsługi tokenu zabezpieczeń, które są zarejestrowane z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="b3fe6-103">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>  
  
 <span data-ttu-id="b3fe6-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="b3fe6-104">\<system.identityModel></span></span>  
<span data-ttu-id="b3fe6-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="b3fe6-105">\<identityConfiguration></span></span>  
<span data-ttu-id="b3fe6-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="b3fe6-106">\<securityTokenHandlers></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3fe6-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="b3fe6-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b3fe6-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b3fe6-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b3fe6-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b3fe6-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b3fe6-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b3fe6-110">Attributes</span></span>  
  
|<span data-ttu-id="b3fe6-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b3fe6-111">Attribute</span></span>|<span data-ttu-id="b3fe6-112">Opis</span><span class="sxs-lookup"><span data-stu-id="b3fe6-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b3fe6-113">nazwa</span><span class="sxs-lookup"><span data-stu-id="b3fe6-113">name</span></span>|<span data-ttu-id="b3fe6-114">Określa nazwę kolekcji programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="b3fe6-114">Specifies the name of a token handler collection.</span></span> <span data-ttu-id="b3fe6-115">Tylko wartości, które są rozpoznawane przez platformę są "ActAs" i "OnBehalfOf".</span><span class="sxs-lookup"><span data-stu-id="b3fe6-115">The only values recognized by the framework are "ActAs" and "OnBehalfOf".</span></span> <span data-ttu-id="b3fe6-116">Jeśli program obsługi tokena kolekcje są określone przy użyciu jednej z następujących nazw, kolekcji będzie używany podczas przetwarzania ActAs lub OnBehalfOf odpowiednio tokenów.</span><span class="sxs-lookup"><span data-stu-id="b3fe6-116">If token handler collections are specified with either of these names, the collection will be used when processing ActAs or OnBehalfOf tokens respectively.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b3fe6-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b3fe6-117">Child Elements</span></span>  
  
|<span data-ttu-id="b3fe6-118">Element</span><span class="sxs-lookup"><span data-stu-id="b3fe6-118">Element</span></span>|<span data-ttu-id="b3fe6-119">Opis</span><span class="sxs-lookup"><span data-stu-id="b3fe6-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b3fe6-120">\<Dodaj ></span><span class="sxs-lookup"><span data-stu-id="b3fe6-120">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="b3fe6-121">Dodaje programu obsługi tokenów zabezpieczających do kolekcji programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="b3fe6-121">Adds a security token handler to the token handler collection.</span></span>|  
|[<span data-ttu-id="b3fe6-122">\<Wyczyść ></span><span class="sxs-lookup"><span data-stu-id="b3fe6-122">\<clear></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/clear.md)|<span data-ttu-id="b3fe6-123">Czyści wszystkie obsługi token zabezpieczeń z kolekcji programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="b3fe6-123">Clears all security token handlers from the token handler collection.</span></span>|  
|[<span data-ttu-id="b3fe6-124">\<Usuń ></span><span class="sxs-lookup"><span data-stu-id="b3fe6-124">\<remove></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/remove.md)|<span data-ttu-id="b3fe6-125">Usuwa programu obsługi tokenów zabezpieczeń z kolekcji programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="b3fe6-125">Removes a security token handler from the token handler collection.</span></span>|  
|[<span data-ttu-id="b3fe6-126">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="b3fe6-126">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="b3fe6-127">Udostępnia konfiguracji dla kolekcji programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="b3fe6-127">Provides configuration for the collection of token handlers.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b3fe6-128">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b3fe6-128">Parent Elements</span></span>  
  
|<span data-ttu-id="b3fe6-129">Element</span><span class="sxs-lookup"><span data-stu-id="b3fe6-129">Element</span></span>|<span data-ttu-id="b3fe6-130">Opis</span><span class="sxs-lookup"><span data-stu-id="b3fe6-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b3fe6-131">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="b3fe6-131">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="b3fe6-132">Określa ustawienia tożsamości poziomu usług.</span><span class="sxs-lookup"><span data-stu-id="b3fe6-132">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b3fe6-133">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b3fe6-133">Remarks</span></span>  
 <span data-ttu-id="b3fe6-134">Można określić jedną lub więcej kolekcji nazwanych programów obsługi tokenu zabezpieczeń w konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="b3fe6-134">You can specify one or more named collections of security token handlers in a service configuration.</span></span> <span data-ttu-id="b3fe6-135">Można określić nazwę dla kolekcji przy użyciu `name` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="b3fe6-135">You can specify a name for a collection by using the `name` attribute.</span></span> <span data-ttu-id="b3fe6-136">Tylko nazwy, które obsługuje w ramach są "ActAs" i "OnBehalfOf".</span><span class="sxs-lookup"><span data-stu-id="b3fe6-136">The only names that the framework handles are "ActAs" and "OnBehalfOf".</span></span> <span data-ttu-id="b3fe6-137">Jeśli programów obsługi istnieje w tych kolekcjach, są one używane przez usługę tokenu zabezpieczającego (STS) zamiast domyślnej obsługi podczas przetwarzania `ActAs` i `OnBehalfOf` tokenów.</span><span class="sxs-lookup"><span data-stu-id="b3fe6-137">If handlers exist in these collections, they are used by a security token service (STS) instead of the default handlers when processing `ActAs` and `OnBehalfOf` tokens.</span></span>  
  
 <span data-ttu-id="b3fe6-138">Domyślnie kolekcji jest wypełniana następujące typy programów obsługi: <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, i <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>.</span><span class="sxs-lookup"><span data-stu-id="b3fe6-138">By default, the collection is populated with the following handler types: <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, and <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>.</span></span> <span data-ttu-id="b3fe6-139">Można zmodyfikować kolekcji za pomocą `<add>`, `<remove>`, i `<clear>` elementy.</span><span class="sxs-lookup"><span data-stu-id="b3fe6-139">You can modify the collection by using the `<add>`, `<remove>`, and `<clear>` elements.</span></span> <span data-ttu-id="b3fe6-140">Należy się upewnić, że tylko jeden obsługi określonego typu istnieje w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="b3fe6-140">You must ensure that only a single handler of any particular type exists in the collection.</span></span> <span data-ttu-id="b3fe6-141">Na przykład, jeśli pochodzi z obsługi <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> klasy, albo z obsługi lub <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> mogą być konfigurowane w jednej kolekcji, ale nie oba.</span><span class="sxs-lookup"><span data-stu-id="b3fe6-141">For example, if you derive a handler from the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, either your handler or the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> may be configured in a single collection, but not both.</span></span>  
  
 <span data-ttu-id="b3fe6-142">Użyj `<securityTokenHandlerConfiguration>` element, aby określić ustawienia konfiguracji dla programów obsługi w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="b3fe6-142">Use the `<securityTokenHandlerConfiguration>` element to specify configuration settings for the handlers in the collection.</span></span> <span data-ttu-id="b3fe6-143">Za pośrednictwem tego elementu zastępują ustawienia określone na usługi za pośrednictwem [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="b3fe6-143">Settings specified through this element override those specified on the service through the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span> <span data-ttu-id="b3fe6-144">Niektóre programy obsługi (w tym kilka typów wbudowanego programu obsługi) może obsługiwać dodatkowej konfiguracji za pomocą elementu podrzędnego `<add>` elementu.</span><span class="sxs-lookup"><span data-stu-id="b3fe6-144">Some handlers (including several of the built-in handler types) can support additional configuration through a child element of the `<add>` element.</span></span> <span data-ttu-id="b3fe6-145">Ustawienia określone na program obsługi zastąpić równoważnym ustawień określonych w kolekcji lub usługi.</span><span class="sxs-lookup"><span data-stu-id="b3fe6-145">Settings specified on a handler override equivalent settings specified on the collection or the service.</span></span>
