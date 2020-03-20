---
title: <serviceTokenResolver>
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
ms.openlocfilehash: 0983380e553acfe246d6b987784d818b8ae85b17
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152583"
---
# <a name="servicetokenresolver"></a><span data-ttu-id="47e9e-101">\<> serviceTokenResolver</span><span class="sxs-lookup"><span data-stu-id="47e9e-101">\<serviceTokenResolver></span></span>
<span data-ttu-id="47e9e-102">Rejestruje program rozpoznawania tokenów usługi, który jest używany przez programy obsługi w kolekcji obsługi tokenu.</span><span class="sxs-lookup"><span data-stu-id="47e9e-102">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="47e9e-103">Program rozpoznawania nazw tokenów usługi służy do rozpoznawania tokenu szyfrowania na przychodzących tokenach i wiadomościach.</span><span class="sxs-lookup"><span data-stu-id="47e9e-103">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span>  
  
<span data-ttu-id="47e9e-104">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="47e9e-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="47e9e-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="47e9e-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="47e9e-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<>konfiguracji tożsamości**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="47e9e-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="47e9e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>securityTokenHandlers**](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="47e9e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="47e9e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>konfiguracji securityTokenHandler**](securitytokenhandlerconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="47e9e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)</span></span>\
<span data-ttu-id="47e9e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>serviceTokenResolver**</span><span class="sxs-lookup"><span data-stu-id="47e9e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceTokenResolver>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47e9e-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="47e9e-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="47e9e-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="47e9e-111">Attributes and Elements</span></span>  
 <span data-ttu-id="47e9e-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="47e9e-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="47e9e-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="47e9e-113">Attributes</span></span>  
  
|<span data-ttu-id="47e9e-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="47e9e-114">Attribute</span></span>|<span data-ttu-id="47e9e-115">Opis</span><span class="sxs-lookup"><span data-stu-id="47e9e-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="47e9e-116">type</span><span class="sxs-lookup"><span data-stu-id="47e9e-116">type</span></span>|<span data-ttu-id="47e9e-117">Określa typ programu rozpoznawania tokenów usługi.</span><span class="sxs-lookup"><span data-stu-id="47e9e-117">Specifies the type of the service token resolver.</span></span> <span data-ttu-id="47e9e-118">Typ <xref:System.IdentityModel.Selectors.SecurityTokenResolver> lub typ, który pochodzi od <xref:System.IdentityModel.Selectors.SecurityTokenResolver> klasy.</span><span class="sxs-lookup"><span data-stu-id="47e9e-118">Either the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> type or a type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span> <span data-ttu-id="47e9e-119">Aby uzyskać więcej informacji `type` na temat określania atrybutu, zobacz [Odwołania do typów niestandardowych].</span><span class="sxs-lookup"><span data-stu-id="47e9e-119">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span> <span data-ttu-id="47e9e-120">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="47e9e-120">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="47e9e-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="47e9e-121">Child Elements</span></span>  
 <span data-ttu-id="47e9e-122">Brak</span><span class="sxs-lookup"><span data-stu-id="47e9e-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="47e9e-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="47e9e-123">Parent Elements</span></span>  
  
|<span data-ttu-id="47e9e-124">Element</span><span class="sxs-lookup"><span data-stu-id="47e9e-124">Element</span></span>|<span data-ttu-id="47e9e-125">Opis</span><span class="sxs-lookup"><span data-stu-id="47e9e-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="47e9e-126">\<>konfiguracji securityTokenHandler</span><span class="sxs-lookup"><span data-stu-id="47e9e-126">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="47e9e-127">Zapewnia konfigurację dla kolekcji obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="47e9e-127">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="47e9e-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="47e9e-128">Remarks</span></span>  
 <span data-ttu-id="47e9e-129">Program rozpoznawania nazw tokenów usługi może służyć do rozpoznawania tokenu szyfrowania na przychodzących tokenów i wiadomości.</span><span class="sxs-lookup"><span data-stu-id="47e9e-129">The service token resolver can be used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="47e9e-130">Służy do pobierania klucza, który powinien służyć do odszyfrowywania tokenów przychodzących.</span><span class="sxs-lookup"><span data-stu-id="47e9e-130">It is used to retrieve the key that should be used to decrypt incoming tokens.</span></span> <span data-ttu-id="47e9e-131">Należy określić `type` atrybut.</span><span class="sxs-lookup"><span data-stu-id="47e9e-131">You must specify the `type` attribute.</span></span> <span data-ttu-id="47e9e-132">Określony typ może być <xref:System.IdentityModel.Selectors.SecurityTokenResolver> albo typu niestandardowego, <xref:System.IdentityModel.Selectors.SecurityTokenResolver> który pochodzi od klasy.</span><span class="sxs-lookup"><span data-stu-id="47e9e-132">The type specified can be either <xref:System.IdentityModel.Selectors.SecurityTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span>  
  
 <span data-ttu-id="47e9e-133">Niektóre programy obsługi tokenu umożliwiają określenie ustawień rozpoznawania nazw tokenów usługi w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="47e9e-133">Some token handlers allow you to specify service token resolver settings in configuration.</span></span> <span data-ttu-id="47e9e-134">Ustawienia poszczególnych programów obsługi tokenów zastępują te określone w kolekcji obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="47e9e-134">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="47e9e-135">Określanie `<serviceTokenResolver>` elementu jako elementu podrzędnego [ \<identityConfiguration>](identityconfiguration.md) element został przestarzały, ale nadal jest obsługiwany dla zgodności z powrotem.</span><span class="sxs-lookup"><span data-stu-id="47e9e-135">Specifying the `<serviceTokenResolver>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="47e9e-136">Ustawienia elementu `<securityTokenHandlerConfiguration>` zastąpić te na `<identityConfiguration>` elemencie.</span><span class="sxs-lookup"><span data-stu-id="47e9e-136">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="47e9e-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="47e9e-137">Example</span></span>  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
