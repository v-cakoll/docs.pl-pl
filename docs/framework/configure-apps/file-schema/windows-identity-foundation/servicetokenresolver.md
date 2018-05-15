---
title: '&lt;serviceTokenResolver&gt;'
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: c25ea1fc32c93e7eb57ef8ed06d6f786ae0a670e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltservicetokenresolvergt"></a><span data-ttu-id="fbab0-102">&lt;serviceTokenResolver&gt;</span><span class="sxs-lookup"><span data-stu-id="fbab0-102">&lt;serviceTokenResolver&gt;</span></span>
<span data-ttu-id="fbab0-103">Rejestruje mechanizm rozpoznawania tokenu usługi, używany przez programy obsługi zdarzeń w kolekcji programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="fbab0-103">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="fbab0-104">Program rozpoznawania nazw tokenów usługi jest używany do rozpoznawania tokenu szyfrowania na przychodzące tokeny i komunikatów.</span><span class="sxs-lookup"><span data-stu-id="fbab0-104">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span>  
  
 <span data-ttu-id="fbab0-105">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="fbab0-105">\<system.identityModel></span></span>  
<span data-ttu-id="fbab0-106">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="fbab0-106">\<identityConfiguration></span></span>  
<span data-ttu-id="fbab0-107">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="fbab0-107">\<securityTokenHandlers></span></span>  
<span data-ttu-id="fbab0-108">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="fbab0-108">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="fbab0-109">\<serviceTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="fbab0-109">\<serviceTokenResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbab0-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="fbab0-110">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <serviceTokenResolver type=xs:string>  
        </serviceTokenResolver>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fbab0-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="fbab0-111">Attributes and Elements</span></span>  
 <span data-ttu-id="fbab0-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="fbab0-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fbab0-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="fbab0-113">Attributes</span></span>  
  
|<span data-ttu-id="fbab0-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="fbab0-114">Attribute</span></span>|<span data-ttu-id="fbab0-115">Opis</span><span class="sxs-lookup"><span data-stu-id="fbab0-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fbab0-116">— typ</span><span class="sxs-lookup"><span data-stu-id="fbab0-116">type</span></span>|<span data-ttu-id="fbab0-117">Określa typ usługi program rozpoznawania nazw tokenów.</span><span class="sxs-lookup"><span data-stu-id="fbab0-117">Specifies the type of the service token resolver.</span></span> <span data-ttu-id="fbab0-118">Albo <xref:System.IdentityModel.Selectors.SecurityTokenResolver> typu lub typu pochodzącego od <xref:System.IdentityModel.Selectors.SecurityTokenResolver> klasy.</span><span class="sxs-lookup"><span data-stu-id="fbab0-118">Either the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> type or a type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span> <span data-ttu-id="fbab0-119">Aby uzyskać więcej informacji o sposobie określania `type` atrybutów, zobacz [odwołania do typu niestandardowego].</span><span class="sxs-lookup"><span data-stu-id="fbab0-119">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span> <span data-ttu-id="fbab0-120">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="fbab0-120">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fbab0-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="fbab0-121">Child Elements</span></span>  
 <span data-ttu-id="fbab0-122">Brak</span><span class="sxs-lookup"><span data-stu-id="fbab0-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fbab0-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="fbab0-123">Parent Elements</span></span>  
  
|<span data-ttu-id="fbab0-124">Element</span><span class="sxs-lookup"><span data-stu-id="fbab0-124">Element</span></span>|<span data-ttu-id="fbab0-125">Opis</span><span class="sxs-lookup"><span data-stu-id="fbab0-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fbab0-126">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="fbab0-126">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="fbab0-127">Zapewnia token obsługi konfiguracji dla kolekcji zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="fbab0-127">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fbab0-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fbab0-128">Remarks</span></span>  
 <span data-ttu-id="fbab0-129">Program rozpoznawania nazw tokenów usług można rozpoznać tokenu szyfrowania na przychodzące tokeny i komunikatów.</span><span class="sxs-lookup"><span data-stu-id="fbab0-129">The service token resolver can be used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="fbab0-130">Służy do pobierania klucza, które mają być używane do odszyfrowywania tokenów przychodzących.</span><span class="sxs-lookup"><span data-stu-id="fbab0-130">It is used to retrieve the key that should be used to decrypt incoming tokens.</span></span> <span data-ttu-id="fbab0-131">Należy określić `type` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="fbab0-131">You must specify the `type` attribute.</span></span> <span data-ttu-id="fbab0-132">Określony typ może być <xref:System.IdentityModel.Selectors.SecurityTokenResolver> lub pochodzącego od typu niestandardowego <xref:System.IdentityModel.Selectors.SecurityTokenResolver> klasy.</span><span class="sxs-lookup"><span data-stu-id="fbab0-132">The type specified can be either <xref:System.IdentityModel.Selectors.SecurityTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span>  
  
 <span data-ttu-id="fbab0-133">Niektóre obsługi tokenów umożliwiają określenie ustawień rozpoznawania tokenu usługi w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="fbab0-133">Some token handlers allow you to specify service token resolver settings in configuration.</span></span> <span data-ttu-id="fbab0-134">Ustawienia dotyczące poszczególnych programu obsługi tokenów zastąpić określonej w kolekcji programu obsługi tokenów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="fbab0-134">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fbab0-135">Określanie `<serviceTokenResolver>` element jako element podrzędny elementu [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element jest przestarzała, ale nadal jest obsługiwany dla zgodności z poprzednimi wersjami.</span><span class="sxs-lookup"><span data-stu-id="fbab0-135">Specifying the `<serviceTokenResolver>` element as a child element of the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="fbab0-136">Ustawienia na `<securityTokenHandlerConfiguration>` element przesłaniają akcje na `<identityConfiguration>` elementu.</span><span class="sxs-lookup"><span data-stu-id="fbab0-136">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fbab0-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="fbab0-137">Example</span></span>  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
