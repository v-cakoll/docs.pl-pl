---
title: '&lt;issuerTokenResolver&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
caps.latest.revision: "9"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: e859f99768eae5c931618d5902caf40dfad95d54
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltissuertokenresolvergt"></a><span data-ttu-id="e9ee8-102">&lt;issuerTokenResolver&gt;</span><span class="sxs-lookup"><span data-stu-id="e9ee8-102">&lt;issuerTokenResolver&gt;</span></span>
<span data-ttu-id="e9ee8-103">Rejestruje mechanizm rozpoznawania tokenów wystawcy, używanego przez programy obsługi zdarzeń w kolekcji programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="e9ee8-103">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="e9ee8-104">Program rozpoznawania nazw tokenów wystawcy jest używany do rozpoznawania token podpisujący na przychodzące tokeny i komunikatów.</span><span class="sxs-lookup"><span data-stu-id="e9ee8-104">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span>  
  
 <span data-ttu-id="e9ee8-105">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="e9ee8-105">\<system.identityModel></span></span>  
<span data-ttu-id="e9ee8-106">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="e9ee8-106">\<identityConfiguration></span></span>  
<span data-ttu-id="e9ee8-107">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="e9ee8-107">\<securityTokenHandlers></span></span>  
<span data-ttu-id="e9ee8-108">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="e9ee8-108">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="e9ee8-109">\<issuerTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="e9ee8-109">\<issuerTokenResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9ee8-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="e9ee8-110">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerTokenResolver type=xs:string>  
        </issuerTokenResolver>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e9ee8-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e9ee8-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e9ee8-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e9ee8-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e9ee8-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e9ee8-113">Attributes</span></span>  
  
|<span data-ttu-id="e9ee8-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e9ee8-114">Attribute</span></span>|<span data-ttu-id="e9ee8-115">Opis</span><span class="sxs-lookup"><span data-stu-id="e9ee8-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e9ee8-116">— typ</span><span class="sxs-lookup"><span data-stu-id="e9ee8-116">type</span></span>|<span data-ttu-id="e9ee8-117">Określa typ wystawcy program rozpoznawania nazw tokenów.</span><span class="sxs-lookup"><span data-stu-id="e9ee8-117">Specifies the type of the issuer token resolver.</span></span> <span data-ttu-id="e9ee8-118">Musi być równa albo <xref:System.IdentityModel.Tokens.IssuerTokenResolver> klasy lub typu pochodzącego od <xref:System.IdentityModel.Tokens.IssuerTokenResolver> klasy.</span><span class="sxs-lookup"><span data-stu-id="e9ee8-118">Must be either the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class or a type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span> <span data-ttu-id="e9ee8-119">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="e9ee8-119">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e9ee8-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e9ee8-120">Child Elements</span></span>  
 <span data-ttu-id="e9ee8-121">Brak</span><span class="sxs-lookup"><span data-stu-id="e9ee8-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e9ee8-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e9ee8-122">Parent Elements</span></span>  
  
|<span data-ttu-id="e9ee8-123">Element</span><span class="sxs-lookup"><span data-stu-id="e9ee8-123">Element</span></span>|<span data-ttu-id="e9ee8-124">Opis</span><span class="sxs-lookup"><span data-stu-id="e9ee8-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e9ee8-125">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="e9ee8-125">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="e9ee8-126">Zapewnia token obsługi konfiguracji dla kolekcji zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="e9ee8-126">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9ee8-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e9ee8-127">Remarks</span></span>  
 <span data-ttu-id="e9ee8-128">Program rozpoznawania nazw tokenów wystawcy jest używany do rozpoznawania token podpisujący na przychodzące tokeny i komunikatów.</span><span class="sxs-lookup"><span data-stu-id="e9ee8-128">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="e9ee8-129">Służy do pobierania kryptograficznych materiału, który służy do sprawdzania podpisu.</span><span class="sxs-lookup"><span data-stu-id="e9ee8-129">It is used to retrieve the cryptographic material that is used for checking the signature.</span></span> <span data-ttu-id="e9ee8-130">Należy określić `type` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="e9ee8-130">You must specify the `type` attribute.</span></span> <span data-ttu-id="e9ee8-131">Określony typ może być <xref:System.IdentityModel.Tokens.IssuerTokenResolver> lub pochodzącego od typu niestandardowego <xref:System.IdentityModel.Tokens.IssuerTokenResolver> klasy.</span><span class="sxs-lookup"><span data-stu-id="e9ee8-131">The type specified can be either <xref:System.IdentityModel.Tokens.IssuerTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span>  
  
 <span data-ttu-id="e9ee8-132">Niektóre obsługi tokenów umożliwiają określenie wystawcy program rozpoznawania nazw tokenów ustawienia w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e9ee8-132">Some token handlers allow you to specify issuer token resolver settings in configuration.</span></span> <span data-ttu-id="e9ee8-133">Ustawienia dotyczące poszczególnych programu obsługi tokenów zastąpić określonej w kolekcji programu obsługi tokenów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="e9ee8-133">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e9ee8-134">Określanie `<issuerTokenResolver>` element jako element podrzędny elementu [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element jest przestarzała, ale nadal jest obsługiwany dla zgodności z poprzednimi wersjami.</span><span class="sxs-lookup"><span data-stu-id="e9ee8-134">Specifying the `<issuerTokenResolver>` element as a child element of the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="e9ee8-135">Ustawienia na `<securityTokenHandlerConfiguration>` element przesłaniają akcje na `<identityConfiguration>` elementu.</span><span class="sxs-lookup"><span data-stu-id="e9ee8-135">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9ee8-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9ee8-136">Example</span></span>  
 <span data-ttu-id="e9ee8-137">Następujący kod XML przedstawia konfigurację dla wystawcy tokenu programu rozpoznawania nazw oparty na niestandardowej klasy, która jest pochodną <xref:System.IdentityModel.Tokens.IssuerTokenResolver>.</span><span class="sxs-lookup"><span data-stu-id="e9ee8-137">The following XML shows configuration for an issuer token resolver that is based on a custom class that derives from <xref:System.IdentityModel.Tokens.IssuerTokenResolver>.</span></span> <span data-ttu-id="e9ee8-138">Program rozpoznawania nazw tokenów utrzymują słownik par klucz odbiorców inicjowane z elementu Konfiguracja niestandardowa (`<AddAudienceKeyPair>`) zdefiniowany dla klasy.</span><span class="sxs-lookup"><span data-stu-id="e9ee8-138">The token resolver maintains a dictionary of audience-key pairs that is initialized from a custom configuration element (`<AddAudienceKeyPair>`) defined for the class.</span></span> <span data-ttu-id="e9ee8-139">Przesłonięć klasy <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> metody w celu przetworzenia tego elementu.</span><span class="sxs-lookup"><span data-stu-id="e9ee8-139">The class overrides the <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> method to process this element.</span></span> <span data-ttu-id="e9ee8-140">Zastąpienie przedstawiono w poniższym przykładzie; metod wywoływanych przez nią nie są wyświetlane do skrócenia.</span><span class="sxs-lookup"><span data-stu-id="e9ee8-140">The override is shown in the following example; however, the methods it calls are not shown for brevity.</span></span> <span data-ttu-id="e9ee8-141">Aby uzyskać pełny przykład, zobacz `CustomToken` próbki.</span><span class="sxs-lookup"><span data-stu-id="e9ee8-141">For the complete example, see the `CustomToken` sample.</span></span>  
  
```xml  
<issuerTokenResolver type="SimpleWebToken.CustomIssuerTokenResolver, SimpleWebToken">  
  <AddAudienceKeyPair  symmetricKey="wAVkldQiFypTQ+kdNdGWCYCHRcee8XmXxOvgmak8vSY=" audience="http://localhost:19851/" />  
</issuerTokenResolver>  
```  
  
## <a name="example"></a><span data-ttu-id="e9ee8-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9ee8-142">Example</span></span>  
  
```  
public override void LoadCustomConfiguration(System.Xml.XmlNodeList nodelist)  
{  
    foreach (XmlNode node in nodelist)  
    {  
        XmlDictionaryReader rdr = XmlDictionaryReader.CreateDictionaryReader(new XmlTextReader(new StringReader(node.OuterXml)));  
        rdr.MoveToContent();  
  
        string symmetricKey = rdr.GetAttribute("symmetricKey");  
        string audience = rdr.GetAttribute("audience");  
  
        this.AddAudienceKeyPair(audience, symmetricKey);  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="e9ee8-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9ee8-143">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.IssuerTokenResolver>
