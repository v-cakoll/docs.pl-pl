---
title: '&lt;serviceTokenResolver&gt;'
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
ms.openlocfilehash: d4b64e2c88e153834b7cf5a83bd6258b6dfd471f
ms.sourcegitcommit: fd8d4587cc26e53f0e27e230d6e27d828ef4306b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2018
ms.locfileid: "49347527"
---
# <a name="ltservicetokenresolvergt"></a><span data-ttu-id="06019-102">&lt;serviceTokenResolver&gt;</span><span class="sxs-lookup"><span data-stu-id="06019-102">&lt;serviceTokenResolver&gt;</span></span>
<span data-ttu-id="06019-103">Rejestruje usługę program rozpoznawania tokenów, który jest używany przez programy obsługi w kolekcji programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="06019-103">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="06019-104">Program rozpoznawania tokenów usługi jest używany do rozpoznawania tokenu szyfrowania na przychodzące tokeny i komunikatów.</span><span class="sxs-lookup"><span data-stu-id="06019-104">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span>  
  
 <span data-ttu-id="06019-105">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="06019-105">\<system.identityModel></span></span>  
<span data-ttu-id="06019-106">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="06019-106">\<identityConfiguration></span></span>  
<span data-ttu-id="06019-107">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="06019-107">\<securityTokenHandlers></span></span>  
<span data-ttu-id="06019-108">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="06019-108">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="06019-109">\<serviceTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="06019-109">\<serviceTokenResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06019-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="06019-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="06019-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="06019-111">Attributes and Elements</span></span>  
 <span data-ttu-id="06019-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="06019-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="06019-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="06019-113">Attributes</span></span>  
  
|<span data-ttu-id="06019-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="06019-114">Attribute</span></span>|<span data-ttu-id="06019-115">Opis</span><span class="sxs-lookup"><span data-stu-id="06019-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="06019-116">— typ</span><span class="sxs-lookup"><span data-stu-id="06019-116">type</span></span>|<span data-ttu-id="06019-117">Określa typ program rozpoznawania tokenów usługi.</span><span class="sxs-lookup"><span data-stu-id="06019-117">Specifies the type of the service token resolver.</span></span> <span data-ttu-id="06019-118">Albo <xref:System.IdentityModel.Selectors.SecurityTokenResolver> typu lub typ pochodzący z <xref:System.IdentityModel.Selectors.SecurityTokenResolver> klasy.</span><span class="sxs-lookup"><span data-stu-id="06019-118">Either the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> type or a type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span> <span data-ttu-id="06019-119">Aby uzyskać więcej informacji o sposobie określania `type` atrybutów, zobacz [odwołań do niestandardowego typu].</span><span class="sxs-lookup"><span data-stu-id="06019-119">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span> <span data-ttu-id="06019-120">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="06019-120">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="06019-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="06019-121">Child Elements</span></span>  
 <span data-ttu-id="06019-122">Brak</span><span class="sxs-lookup"><span data-stu-id="06019-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="06019-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="06019-123">Parent Elements</span></span>  
  
|<span data-ttu-id="06019-124">Element</span><span class="sxs-lookup"><span data-stu-id="06019-124">Element</span></span>|<span data-ttu-id="06019-125">Opis</span><span class="sxs-lookup"><span data-stu-id="06019-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="06019-126">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="06019-126">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="06019-127">Udostępnia konfigurację dla kolekcji zabezpieczeń programy obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="06019-127">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="06019-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="06019-128">Remarks</span></span>  
 <span data-ttu-id="06019-129">Program rozpoznawania tokenów usługi można rozpoznać tokenu szyfrowania na przychodzące tokeny i komunikatów.</span><span class="sxs-lookup"><span data-stu-id="06019-129">The service token resolver can be used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="06019-130">Służy do pobierania klucza, które mają być używane do odszyfrowywania tokenów przychodzących.</span><span class="sxs-lookup"><span data-stu-id="06019-130">It is used to retrieve the key that should be used to decrypt incoming tokens.</span></span> <span data-ttu-id="06019-131">Należy określić `type` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="06019-131">You must specify the `type` attribute.</span></span> <span data-ttu-id="06019-132">Określony typ może być <xref:System.IdentityModel.Selectors.SecurityTokenResolver> lub typ niestandardowy, który pochodzi od klasy <xref:System.IdentityModel.Selectors.SecurityTokenResolver> klasy.</span><span class="sxs-lookup"><span data-stu-id="06019-132">The type specified can be either <xref:System.IdentityModel.Selectors.SecurityTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span>  
  
 <span data-ttu-id="06019-133">Niektóre programy obsługi tokenów umożliwiają określanie ustawień program rozpoznawania tokenów usługi w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="06019-133">Some token handlers allow you to specify service token resolver settings in configuration.</span></span> <span data-ttu-id="06019-134">Ustawienia dotyczące programu obsługi tokenów poszczególnych zastąpienia określonej w kolekcji programu obsługi tokenów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="06019-134">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="06019-135">Określanie `<serviceTokenResolver>` element jako element podrzędny [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elementu jest przestarzałe, ale nadal jest obsługiwany dla zgodności z poprzednimi wersjami.</span><span class="sxs-lookup"><span data-stu-id="06019-135">Specifying the `<serviceTokenResolver>` element as a child element of the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="06019-136">Ustawienia na `<securityTokenHandlerConfiguration>` elemencie przesłaniają akcje na `<identityConfiguration>` elementu.</span><span class="sxs-lookup"><span data-stu-id="06019-136">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="06019-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="06019-137">Example</span></span>  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
