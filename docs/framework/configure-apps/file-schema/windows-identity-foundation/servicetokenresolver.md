---
title: <serviceTokenResolver>
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
ms.openlocfilehash: 30a53c11b551623311f7ca3f957143fc702568a1
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251849"
---
# <a name="servicetokenresolver"></a><span data-ttu-id="ed692-101">\<serviceTokenResolver></span><span class="sxs-lookup"><span data-stu-id="ed692-101">\<serviceTokenResolver></span></span>
<span data-ttu-id="ed692-102">Rejestruje program rozpoznawania tokenów usługi używany przez programy obsługi w kolekcji obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="ed692-102">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="ed692-103">Program rozpoznawania tokenów usługi jest używany do rozpoznawania tokenu szyfrowania przychodzących tokenów i komunikatów.</span><span class="sxs-lookup"><span data-stu-id="ed692-103">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span>  
  
<span data-ttu-id="ed692-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ed692-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ed692-105">&nbsp;&nbsp;[ **\<> System. identityModel**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="ed692-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="ed692-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="ed692-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="ed692-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> obiektów securityTokenHandler**](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="ed692-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="ed692-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlerConfiguration >** ](securitytokenhandlerconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="ed692-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)</span></span>\
<span data-ttu-id="ed692-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<serviceTokenResolver >**</span><span class="sxs-lookup"><span data-stu-id="ed692-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceTokenResolver>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed692-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="ed692-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ed692-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ed692-111">Attributes and Elements</span></span>  
 <span data-ttu-id="ed692-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ed692-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ed692-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ed692-113">Attributes</span></span>  
  
|<span data-ttu-id="ed692-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ed692-114">Attribute</span></span>|<span data-ttu-id="ed692-115">Opis</span><span class="sxs-lookup"><span data-stu-id="ed692-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ed692-116">— typ</span><span class="sxs-lookup"><span data-stu-id="ed692-116">type</span></span>|<span data-ttu-id="ed692-117">Określa typ programu rozpoznawania tokenów usług.</span><span class="sxs-lookup"><span data-stu-id="ed692-117">Specifies the type of the service token resolver.</span></span> <span data-ttu-id="ed692-118">Typ lub typ, który pochodzi <xref:System.IdentityModel.Selectors.SecurityTokenResolver> od klasy. <xref:System.IdentityModel.Selectors.SecurityTokenResolver></span><span class="sxs-lookup"><span data-stu-id="ed692-118">Either the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> type or a type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span> <span data-ttu-id="ed692-119">Aby uzyskać więcej informacji na temat sposobu określania `type` atrybutu, zobacz [odwołania do typów niestandardowych].</span><span class="sxs-lookup"><span data-stu-id="ed692-119">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span> <span data-ttu-id="ed692-120">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="ed692-120">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ed692-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ed692-121">Child Elements</span></span>  
 <span data-ttu-id="ed692-122">Brak</span><span class="sxs-lookup"><span data-stu-id="ed692-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ed692-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ed692-123">Parent Elements</span></span>  
  
|<span data-ttu-id="ed692-124">Element</span><span class="sxs-lookup"><span data-stu-id="ed692-124">Element</span></span>|<span data-ttu-id="ed692-125">Opis</span><span class="sxs-lookup"><span data-stu-id="ed692-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ed692-126">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="ed692-126">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="ed692-127">Zapewnia konfigurację kolekcji programów obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="ed692-127">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ed692-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ed692-128">Remarks</span></span>  
 <span data-ttu-id="ed692-129">Program rozpoznawania tokenów usług może służyć do rozwiązywania tokenu szyfrowania przychodzących tokenów i komunikatów.</span><span class="sxs-lookup"><span data-stu-id="ed692-129">The service token resolver can be used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="ed692-130">Służy do pobierania klucza, który ma być używany do odszyfrowywania tokenów przychodzących.</span><span class="sxs-lookup"><span data-stu-id="ed692-130">It is used to retrieve the key that should be used to decrypt incoming tokens.</span></span> <span data-ttu-id="ed692-131">Należy określić `type` atrybut.</span><span class="sxs-lookup"><span data-stu-id="ed692-131">You must specify the `type` attribute.</span></span> <span data-ttu-id="ed692-132">Określony typ może być albo <xref:System.IdentityModel.Selectors.SecurityTokenResolver> typem niestandardowym, który pochodzi <xref:System.IdentityModel.Selectors.SecurityTokenResolver> od klasy.</span><span class="sxs-lookup"><span data-stu-id="ed692-132">The type specified can be either <xref:System.IdentityModel.Selectors.SecurityTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span>  
  
 <span data-ttu-id="ed692-133">Niektóre programy obsługi tokenów umożliwiają określanie ustawień programu rozpoznawania tokenów usług w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ed692-133">Some token handlers allow you to specify service token resolver settings in configuration.</span></span> <span data-ttu-id="ed692-134">Ustawienia poszczególnych programów obsługi tokenów przesłaniają te określone w kolekcji obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="ed692-134">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ed692-135">Określanie elementu jako elementu [ \<](identityconfiguration.md) podrzędnego elementu IdentityConfiguration > jest przestarzałe, ale nadal jest on obsługiwany w celu zapewnienia zgodności z poprzednimi wersjami. `<serviceTokenResolver>`</span><span class="sxs-lookup"><span data-stu-id="ed692-135">Specifying the `<serviceTokenResolver>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="ed692-136">Ustawienia w `<securityTokenHandlerConfiguration>` elemencie Przesłoń te elementy `<identityConfiguration>` w elemencie.</span><span class="sxs-lookup"><span data-stu-id="ed692-136">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ed692-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="ed692-137">Example</span></span>  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
 