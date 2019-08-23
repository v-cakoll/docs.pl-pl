---
title: <serviceTokenResolver>
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
ms.openlocfilehash: 69d34cb54c2236f178ac4291ed24a3f5b45db48e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923109"
---
# <a name="servicetokenresolver"></a><span data-ttu-id="4ce62-101">\<serviceTokenResolver></span><span class="sxs-lookup"><span data-stu-id="4ce62-101">\<serviceTokenResolver></span></span>
<span data-ttu-id="4ce62-102">Rejestruje program rozpoznawania tokenów usługi używany przez programy obsługi w kolekcji obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="4ce62-102">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="4ce62-103">Program rozpoznawania tokenów usługi jest używany do rozpoznawania tokenu szyfrowania przychodzących tokenów i komunikatów.</span><span class="sxs-lookup"><span data-stu-id="4ce62-103">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span>  
  
 <span data-ttu-id="4ce62-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="4ce62-104">\<system.identityModel></span></span>  
<span data-ttu-id="4ce62-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="4ce62-105">\<identityConfiguration></span></span>  
<span data-ttu-id="4ce62-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="4ce62-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="4ce62-107">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="4ce62-107">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="4ce62-108">\<serviceTokenResolver></span><span class="sxs-lookup"><span data-stu-id="4ce62-108">\<serviceTokenResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ce62-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="4ce62-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4ce62-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4ce62-110">Attributes and Elements</span></span>  
 <span data-ttu-id="4ce62-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4ce62-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4ce62-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4ce62-112">Attributes</span></span>  
  
|<span data-ttu-id="4ce62-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4ce62-113">Attribute</span></span>|<span data-ttu-id="4ce62-114">Opis</span><span class="sxs-lookup"><span data-stu-id="4ce62-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4ce62-115">— typ</span><span class="sxs-lookup"><span data-stu-id="4ce62-115">type</span></span>|<span data-ttu-id="4ce62-116">Określa typ programu rozpoznawania tokenów usług.</span><span class="sxs-lookup"><span data-stu-id="4ce62-116">Specifies the type of the service token resolver.</span></span> <span data-ttu-id="4ce62-117">Typ lub typ, który pochodzi <xref:System.IdentityModel.Selectors.SecurityTokenResolver> od klasy. <xref:System.IdentityModel.Selectors.SecurityTokenResolver></span><span class="sxs-lookup"><span data-stu-id="4ce62-117">Either the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> type or a type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span> <span data-ttu-id="4ce62-118">Aby uzyskać więcej informacji na temat sposobu określania `type` atrybutu, zobacz [odwołania do typów niestandardowych].</span><span class="sxs-lookup"><span data-stu-id="4ce62-118">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span> <span data-ttu-id="4ce62-119">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="4ce62-119">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4ce62-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4ce62-120">Child Elements</span></span>  
 <span data-ttu-id="4ce62-121">Brak</span><span class="sxs-lookup"><span data-stu-id="4ce62-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4ce62-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4ce62-122">Parent Elements</span></span>  
  
|<span data-ttu-id="4ce62-123">Element</span><span class="sxs-lookup"><span data-stu-id="4ce62-123">Element</span></span>|<span data-ttu-id="4ce62-124">Opis</span><span class="sxs-lookup"><span data-stu-id="4ce62-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4ce62-125">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="4ce62-125">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="4ce62-126">Zapewnia konfigurację kolekcji programów obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="4ce62-126">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4ce62-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4ce62-127">Remarks</span></span>  
 <span data-ttu-id="4ce62-128">Program rozpoznawania tokenów usług może służyć do rozwiązywania tokenu szyfrowania przychodzących tokenów i komunikatów.</span><span class="sxs-lookup"><span data-stu-id="4ce62-128">The service token resolver can be used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="4ce62-129">Służy do pobierania klucza, który ma być używany do odszyfrowywania tokenów przychodzących.</span><span class="sxs-lookup"><span data-stu-id="4ce62-129">It is used to retrieve the key that should be used to decrypt incoming tokens.</span></span> <span data-ttu-id="4ce62-130">Należy określić `type` atrybut.</span><span class="sxs-lookup"><span data-stu-id="4ce62-130">You must specify the `type` attribute.</span></span> <span data-ttu-id="4ce62-131">Określony typ może być albo <xref:System.IdentityModel.Selectors.SecurityTokenResolver> typem niestandardowym, który pochodzi <xref:System.IdentityModel.Selectors.SecurityTokenResolver> od klasy.</span><span class="sxs-lookup"><span data-stu-id="4ce62-131">The type specified can be either <xref:System.IdentityModel.Selectors.SecurityTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span>  
  
 <span data-ttu-id="4ce62-132">Niektóre programy obsługi tokenów umożliwiają określanie ustawień programu rozpoznawania tokenów usług w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="4ce62-132">Some token handlers allow you to specify service token resolver settings in configuration.</span></span> <span data-ttu-id="4ce62-133">Ustawienia poszczególnych programów obsługi tokenów przesłaniają te określone w kolekcji obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="4ce62-133">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4ce62-134">Określanie elementu jako elementu [ \<](identityconfiguration.md) podrzędnego elementu IdentityConfiguration > jest przestarzałe, ale nadal jest on obsługiwany w celu zapewnienia zgodności z poprzednimi wersjami. `<serviceTokenResolver>`</span><span class="sxs-lookup"><span data-stu-id="4ce62-134">Specifying the `<serviceTokenResolver>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="4ce62-135">Ustawienia w `<securityTokenHandlerConfiguration>` elemencie Przesłoń te elementy `<identityConfiguration>` w elemencie.</span><span class="sxs-lookup"><span data-stu-id="4ce62-135">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ce62-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="4ce62-136">Example</span></span>  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
