---
title: <securityTokenHandlers>
ms.date: 03/30/2017
ms.assetid: f11a631d-4094-4e11-bb03-4ede74b30281
author: BrucePerlerMS
ms.openlocfilehash: 017309436660991c69da569e9cc4219e842ecaa3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251874"
---
# \<securityTokenHandlers>
<span data-ttu-id="19f06-101">Określa kolekcję programów obsługi tokenów zabezpieczających, które są zarejestrowane w punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="19f06-101">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<securityTokenHandlers>**  
  
## <a name="syntax"></a><span data-ttu-id="19f06-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="19f06-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="19f06-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="19f06-103">Attributes and Elements</span></span>  
 <span data-ttu-id="19f06-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="19f06-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="19f06-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="19f06-105">Attributes</span></span>  
  
|<span data-ttu-id="19f06-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="19f06-106">Attribute</span></span>|<span data-ttu-id="19f06-107">Opis</span><span class="sxs-lookup"><span data-stu-id="19f06-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="19f06-108">name</span><span class="sxs-lookup"><span data-stu-id="19f06-108">name</span></span>|<span data-ttu-id="19f06-109">Określa nazwę kolekcji obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="19f06-109">Specifies the name of a token handler collection.</span></span> <span data-ttu-id="19f06-110">Jedyne wartości rozpoznawane przez platformę to "ActAs" i "OnBehalfOf".</span><span class="sxs-lookup"><span data-stu-id="19f06-110">The only values recognized by the framework are "ActAs" and "OnBehalfOf".</span></span> <span data-ttu-id="19f06-111">Jeśli kolekcje obsługi tokenów są określone przy użyciu jednej z tych nazw, kolekcja zostanie użyta podczas przetwarzania tokenów ActAs lub OnBehalfOf.</span><span class="sxs-lookup"><span data-stu-id="19f06-111">If token handler collections are specified with either of these names, the collection will be used when processing ActAs or OnBehalfOf tokens respectively.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="19f06-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="19f06-112">Child Elements</span></span>  
  
|<span data-ttu-id="19f06-113">Element</span><span class="sxs-lookup"><span data-stu-id="19f06-113">Element</span></span>|<span data-ttu-id="19f06-114">Opis</span><span class="sxs-lookup"><span data-stu-id="19f06-114">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add.md)|<span data-ttu-id="19f06-115">Dodaje procedurę obsługi tokenów zabezpieczających do kolekcji obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="19f06-115">Adds a security token handler to the token handler collection.</span></span>|  
|[\<clear>](clear.md)|<span data-ttu-id="19f06-116">Czyści wszystkie programy obsługi tokenów zabezpieczających z kolekcji obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="19f06-116">Clears all security token handlers from the token handler collection.</span></span>|  
|[\<remove>](remove.md)|<span data-ttu-id="19f06-117">Usuwa procedurę obsługi tokenu zabezpieczającego z kolekcji obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="19f06-117">Removes a security token handler from the token handler collection.</span></span>|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="19f06-118">Zapewnia konfigurację kolekcji programów obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="19f06-118">Provides configuration for the collection of token handlers.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="19f06-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="19f06-119">Parent Elements</span></span>  
  
|<span data-ttu-id="19f06-120">Element</span><span class="sxs-lookup"><span data-stu-id="19f06-120">Element</span></span>|<span data-ttu-id="19f06-121">Opis</span><span class="sxs-lookup"><span data-stu-id="19f06-121">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="19f06-122">Określa ustawienia tożsamości na poziomie usług.</span><span class="sxs-lookup"><span data-stu-id="19f06-122">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="19f06-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="19f06-123">Remarks</span></span>  
 <span data-ttu-id="19f06-124">W konfiguracji usługi można określić co najmniej jedną nazwę kolekcji programów obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="19f06-124">You can specify one or more named collections of security token handlers in a service configuration.</span></span> <span data-ttu-id="19f06-125">Możesz określić nazwę kolekcji przy użyciu `name` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="19f06-125">You can specify a name for a collection by using the `name` attribute.</span></span> <span data-ttu-id="19f06-126">Jedyne nazwy obsługiwane przez platformę to "ActAs" i "OnBehalfOf".</span><span class="sxs-lookup"><span data-stu-id="19f06-126">The only names that the framework handles are "ActAs" and "OnBehalfOf".</span></span> <span data-ttu-id="19f06-127">Jeśli w tych kolekcjach istnieją programy obsługi, są one używane przez usługę tokenu zabezpieczającego (STS) zamiast domyślnych programów obsługi podczas przetwarzania `ActAs` i `OnBehalfOf` tokenów.</span><span class="sxs-lookup"><span data-stu-id="19f06-127">If handlers exist in these collections, they are used by a security token service (STS) instead of the default handlers when processing `ActAs` and `OnBehalfOf` tokens.</span></span>  
  
 <span data-ttu-id="19f06-128">Domyślnie kolekcja jest wypełniana następującymi typami obsługi:,,,, <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> , <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler> <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler> <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler> <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> , i <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler> .</span><span class="sxs-lookup"><span data-stu-id="19f06-128">By default, the collection is populated with the following handler types: <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, and <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>.</span></span> <span data-ttu-id="19f06-129">Kolekcję można modyfikować za pomocą `<add>` `<remove>` elementów, i `<clear>` .</span><span class="sxs-lookup"><span data-stu-id="19f06-129">You can modify the collection by using the `<add>`, `<remove>`, and `<clear>` elements.</span></span> <span data-ttu-id="19f06-130">Musisz się upewnić, że w kolekcji istnieje tylko jedna procedura obsługi określonego typu.</span><span class="sxs-lookup"><span data-stu-id="19f06-130">You must ensure that only a single handler of any particular type exists in the collection.</span></span> <span data-ttu-id="19f06-131">Na przykład, jeśli pochodna jest procedura obsługi z <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> klasy, program obsługi lub <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> może być skonfigurowany w pojedynczej kolekcji, ale nie w obu tych przypadkach.</span><span class="sxs-lookup"><span data-stu-id="19f06-131">For example, if you derive a handler from the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, either your handler or the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> may be configured in a single collection, but not both.</span></span>  
  
 <span data-ttu-id="19f06-132">Użyj `<securityTokenHandlerConfiguration>` elementu, aby określić ustawienia konfiguracji dla programów obsługi w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="19f06-132">Use the `<securityTokenHandlerConfiguration>` element to specify configuration settings for the handlers in the collection.</span></span> <span data-ttu-id="19f06-133">Ustawienia określone za pomocą tego elementu zastępują te określone w usłudze za pomocą [\<identityConfiguration>](identityconfiguration.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="19f06-133">Settings specified through this element override those specified on the service through the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="19f06-134">Niektóre programy obsługi (w tym kilka wbudowanych typów obsługi) mogą obsługiwać dodatkową konfigurację za pomocą elementu podrzędnego `<add>` elementu.</span><span class="sxs-lookup"><span data-stu-id="19f06-134">Some handlers (including several of the built-in handler types) can support additional configuration through a child element of the `<add>` element.</span></span> <span data-ttu-id="19f06-135">Ustawienia określone w ustawieniach przesłonięcia programu obsługi określone w kolekcji lub usłudze.</span><span class="sxs-lookup"><span data-stu-id="19f06-135">Settings specified on a handler override equivalent settings specified on the collection or the service.</span></span>
