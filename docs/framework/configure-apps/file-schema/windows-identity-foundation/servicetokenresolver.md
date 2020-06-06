---
title: <serviceTokenResolver>
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
ms.openlocfilehash: 0983380e553acfe246d6b987784d818b8ae85b17
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152583"
---
# \<serviceTokenResolver>
<span data-ttu-id="0b5e9-101">Rejestruje program rozpoznawania tokenów usługi używany przez programy obsługi w kolekcji obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="0b5e9-101">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="0b5e9-102">Program rozpoznawania tokenów usługi jest używany do rozpoznawania tokenu szyfrowania przychodzących tokenów i komunikatów.</span><span class="sxs-lookup"><span data-stu-id="0b5e9-102">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceTokenResolver>**  
  
## <a name="syntax"></a><span data-ttu-id="0b5e9-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="0b5e9-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0b5e9-104">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0b5e9-104">Attributes and Elements</span></span>  
 <span data-ttu-id="0b5e9-105">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0b5e9-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0b5e9-106">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0b5e9-106">Attributes</span></span>  
  
|<span data-ttu-id="0b5e9-107">Atrybut</span><span class="sxs-lookup"><span data-stu-id="0b5e9-107">Attribute</span></span>|<span data-ttu-id="0b5e9-108">Opis</span><span class="sxs-lookup"><span data-stu-id="0b5e9-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0b5e9-109">typ</span><span class="sxs-lookup"><span data-stu-id="0b5e9-109">type</span></span>|<span data-ttu-id="0b5e9-110">Określa typ programu rozpoznawania tokenów usług.</span><span class="sxs-lookup"><span data-stu-id="0b5e9-110">Specifies the type of the service token resolver.</span></span> <span data-ttu-id="0b5e9-111"><xref:System.IdentityModel.Selectors.SecurityTokenResolver>Typ lub typ, który pochodzi od <xref:System.IdentityModel.Selectors.SecurityTokenResolver> klasy.</span><span class="sxs-lookup"><span data-stu-id="0b5e9-111">Either the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> type or a type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span> <span data-ttu-id="0b5e9-112">Aby uzyskać więcej informacji na temat sposobu określania `type` atrybutu, zobacz [odwołania do typów niestandardowych].</span><span class="sxs-lookup"><span data-stu-id="0b5e9-112">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span> <span data-ttu-id="0b5e9-113">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="0b5e9-113">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0b5e9-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0b5e9-114">Child Elements</span></span>  
 <span data-ttu-id="0b5e9-115">Brak</span><span class="sxs-lookup"><span data-stu-id="0b5e9-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0b5e9-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0b5e9-116">Parent Elements</span></span>  
  
|<span data-ttu-id="0b5e9-117">Element</span><span class="sxs-lookup"><span data-stu-id="0b5e9-117">Element</span></span>|<span data-ttu-id="0b5e9-118">Opis</span><span class="sxs-lookup"><span data-stu-id="0b5e9-118">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="0b5e9-119">Zapewnia konfigurację kolekcji programów obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="0b5e9-119">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0b5e9-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0b5e9-120">Remarks</span></span>  
 <span data-ttu-id="0b5e9-121">Program rozpoznawania tokenów usług może służyć do rozwiązywania tokenu szyfrowania przychodzących tokenów i komunikatów.</span><span class="sxs-lookup"><span data-stu-id="0b5e9-121">The service token resolver can be used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="0b5e9-122">Służy do pobierania klucza, który ma być używany do odszyfrowywania tokenów przychodzących.</span><span class="sxs-lookup"><span data-stu-id="0b5e9-122">It is used to retrieve the key that should be used to decrypt incoming tokens.</span></span> <span data-ttu-id="0b5e9-123">Należy określić `type` atrybut.</span><span class="sxs-lookup"><span data-stu-id="0b5e9-123">You must specify the `type` attribute.</span></span> <span data-ttu-id="0b5e9-124">Określony typ może być albo <xref:System.IdentityModel.Selectors.SecurityTokenResolver> typem niestandardowym, który pochodzi od <xref:System.IdentityModel.Selectors.SecurityTokenResolver> klasy.</span><span class="sxs-lookup"><span data-stu-id="0b5e9-124">The type specified can be either <xref:System.IdentityModel.Selectors.SecurityTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span>  
  
 <span data-ttu-id="0b5e9-125">Niektóre programy obsługi tokenów umożliwiają określanie ustawień programu rozpoznawania tokenów usług w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="0b5e9-125">Some token handlers allow you to specify service token resolver settings in configuration.</span></span> <span data-ttu-id="0b5e9-126">Ustawienia poszczególnych programów obsługi tokenów przesłaniają te określone w kolekcji obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="0b5e9-126">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0b5e9-127">Określanie `<serviceTokenResolver>` elementu jako elementu podrzędnego [\<identityConfiguration>](identityconfiguration.md) elementu jest przestarzałe, ale nadal jest ono obsługiwane w celu zapewnienia zgodności z poprzednimi wersjami.</span><span class="sxs-lookup"><span data-stu-id="0b5e9-127">Specifying the `<serviceTokenResolver>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="0b5e9-128">Ustawienia w `<securityTokenHandlerConfiguration>` elemencie Przesłoń te elementy w `<identityConfiguration>` elemencie.</span><span class="sxs-lookup"><span data-stu-id="0b5e9-128">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b5e9-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="0b5e9-129">Example</span></span>  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
