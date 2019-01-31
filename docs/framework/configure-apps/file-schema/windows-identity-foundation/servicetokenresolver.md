---
title: <serviceTokenResolver>
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
ms.openlocfilehash: 1143717882652fc8a03947327b5f1ea89dde7373
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55267433"
---
# <a name="servicetokenresolver"></a><span data-ttu-id="37c84-101">\<serviceTokenResolver></span><span class="sxs-lookup"><span data-stu-id="37c84-101">\<serviceTokenResolver></span></span>
<span data-ttu-id="37c84-102">Rejestruje usługę program rozpoznawania tokenów, który jest używany przez programy obsługi w kolekcji programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="37c84-102">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="37c84-103">Program rozpoznawania tokenów usługi jest używany do rozpoznawania tokenu szyfrowania na przychodzące tokeny i komunikatów.</span><span class="sxs-lookup"><span data-stu-id="37c84-103">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span>  
  
 <span data-ttu-id="37c84-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="37c84-104">\<system.identityModel></span></span>  
<span data-ttu-id="37c84-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="37c84-105">\<identityConfiguration></span></span>  
<span data-ttu-id="37c84-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="37c84-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="37c84-107">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="37c84-107">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="37c84-108">\<serviceTokenResolver></span><span class="sxs-lookup"><span data-stu-id="37c84-108">\<serviceTokenResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37c84-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="37c84-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="37c84-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="37c84-110">Attributes and Elements</span></span>  
 <span data-ttu-id="37c84-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="37c84-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="37c84-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="37c84-112">Attributes</span></span>  
  
|<span data-ttu-id="37c84-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="37c84-113">Attribute</span></span>|<span data-ttu-id="37c84-114">Opis</span><span class="sxs-lookup"><span data-stu-id="37c84-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="37c84-115">— typ</span><span class="sxs-lookup"><span data-stu-id="37c84-115">type</span></span>|<span data-ttu-id="37c84-116">Określa typ program rozpoznawania tokenów usługi.</span><span class="sxs-lookup"><span data-stu-id="37c84-116">Specifies the type of the service token resolver.</span></span> <span data-ttu-id="37c84-117">Albo <xref:System.IdentityModel.Selectors.SecurityTokenResolver> typu lub typ pochodzący z <xref:System.IdentityModel.Selectors.SecurityTokenResolver> klasy.</span><span class="sxs-lookup"><span data-stu-id="37c84-117">Either the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> type or a type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span> <span data-ttu-id="37c84-118">Aby uzyskać więcej informacji o sposobie określania `type` atrybutów, zobacz [odwołań do niestandardowego typu].</span><span class="sxs-lookup"><span data-stu-id="37c84-118">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span> <span data-ttu-id="37c84-119">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="37c84-119">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="37c84-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="37c84-120">Child Elements</span></span>  
 <span data-ttu-id="37c84-121">Brak</span><span class="sxs-lookup"><span data-stu-id="37c84-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="37c84-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="37c84-122">Parent Elements</span></span>  
  
|<span data-ttu-id="37c84-123">Element</span><span class="sxs-lookup"><span data-stu-id="37c84-123">Element</span></span>|<span data-ttu-id="37c84-124">Opis</span><span class="sxs-lookup"><span data-stu-id="37c84-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="37c84-125">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="37c84-125">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="37c84-126">Udostępnia konfigurację dla kolekcji zabezpieczeń programy obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="37c84-126">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37c84-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="37c84-127">Remarks</span></span>  
 <span data-ttu-id="37c84-128">Program rozpoznawania tokenów usługi można rozpoznać tokenu szyfrowania na przychodzące tokeny i komunikatów.</span><span class="sxs-lookup"><span data-stu-id="37c84-128">The service token resolver can be used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="37c84-129">Służy do pobierania klucza, które mają być używane do odszyfrowywania tokenów przychodzących.</span><span class="sxs-lookup"><span data-stu-id="37c84-129">It is used to retrieve the key that should be used to decrypt incoming tokens.</span></span> <span data-ttu-id="37c84-130">Należy określić `type` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="37c84-130">You must specify the `type` attribute.</span></span> <span data-ttu-id="37c84-131">Określony typ może być <xref:System.IdentityModel.Selectors.SecurityTokenResolver> lub typ niestandardowy, który pochodzi od klasy <xref:System.IdentityModel.Selectors.SecurityTokenResolver> klasy.</span><span class="sxs-lookup"><span data-stu-id="37c84-131">The type specified can be either <xref:System.IdentityModel.Selectors.SecurityTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span>  
  
 <span data-ttu-id="37c84-132">Niektóre programy obsługi tokenów umożliwiają określanie ustawień program rozpoznawania tokenów usługi w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="37c84-132">Some token handlers allow you to specify service token resolver settings in configuration.</span></span> <span data-ttu-id="37c84-133">Ustawienia dotyczące programu obsługi tokenów poszczególnych zastąpienia określonej w kolekcji programu obsługi tokenów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="37c84-133">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="37c84-134">Określanie `<serviceTokenResolver>` element jako element podrzędny [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elementu jest przestarzałe, ale nadal jest obsługiwany dla zgodności z poprzednimi wersjami.</span><span class="sxs-lookup"><span data-stu-id="37c84-134">Specifying the `<serviceTokenResolver>` element as a child element of the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="37c84-135">Ustawienia na `<securityTokenHandlerConfiguration>` elemencie przesłaniają akcje na `<identityConfiguration>` elementu.</span><span class="sxs-lookup"><span data-stu-id="37c84-135">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="37c84-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="37c84-136">Example</span></span>  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
