---
title: '&lt;issuerTokenResolver&gt;'
ms.date: 03/30/2017
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 646833f277c3ef4675a835ca0af3daf647e01224
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltissuertokenresolvergt"></a><span data-ttu-id="34a25-102">&lt;issuerTokenResolver&gt;</span><span class="sxs-lookup"><span data-stu-id="34a25-102">&lt;issuerTokenResolver&gt;</span></span>
<span data-ttu-id="34a25-103">Rejestruje mechanizm rozpoznawania tokenów wystawcy, używanego przez programy obsługi zdarzeń w kolekcji programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="34a25-103">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="34a25-104">Program rozpoznawania nazw tokenów wystawcy jest używany do rozpoznawania token podpisujący na przychodzące tokeny i komunikatów.</span><span class="sxs-lookup"><span data-stu-id="34a25-104">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span>  
  
 <span data-ttu-id="34a25-105">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="34a25-105">\<system.identityModel></span></span>  
<span data-ttu-id="34a25-106">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="34a25-106">\<identityConfiguration></span></span>  
<span data-ttu-id="34a25-107">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="34a25-107">\<securityTokenHandlers></span></span>  
<span data-ttu-id="34a25-108">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="34a25-108">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="34a25-109">\<issuerTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="34a25-109">\<issuerTokenResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34a25-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="34a25-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="34a25-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="34a25-111">Attributes and Elements</span></span>  
 <span data-ttu-id="34a25-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="34a25-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="34a25-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="34a25-113">Attributes</span></span>  
  
|<span data-ttu-id="34a25-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="34a25-114">Attribute</span></span>|<span data-ttu-id="34a25-115">Opis</span><span class="sxs-lookup"><span data-stu-id="34a25-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="34a25-116">— typ</span><span class="sxs-lookup"><span data-stu-id="34a25-116">type</span></span>|<span data-ttu-id="34a25-117">Określa typ wystawcy program rozpoznawania nazw tokenów.</span><span class="sxs-lookup"><span data-stu-id="34a25-117">Specifies the type of the issuer token resolver.</span></span> <span data-ttu-id="34a25-118">Musi być równa albo <xref:System.IdentityModel.Tokens.IssuerTokenResolver> klasy lub typu pochodzącego od <xref:System.IdentityModel.Tokens.IssuerTokenResolver> klasy.</span><span class="sxs-lookup"><span data-stu-id="34a25-118">Must be either the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class or a type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span> <span data-ttu-id="34a25-119">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="34a25-119">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="34a25-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="34a25-120">Child Elements</span></span>  
 <span data-ttu-id="34a25-121">Brak</span><span class="sxs-lookup"><span data-stu-id="34a25-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="34a25-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="34a25-122">Parent Elements</span></span>  
  
|<span data-ttu-id="34a25-123">Element</span><span class="sxs-lookup"><span data-stu-id="34a25-123">Element</span></span>|<span data-ttu-id="34a25-124">Opis</span><span class="sxs-lookup"><span data-stu-id="34a25-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="34a25-125">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="34a25-125">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="34a25-126">Zapewnia token obsługi konfiguracji dla kolekcji zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="34a25-126">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="34a25-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="34a25-127">Remarks</span></span>  
 <span data-ttu-id="34a25-128">Program rozpoznawania nazw tokenów wystawcy jest używany do rozpoznawania token podpisujący na przychodzące tokeny i komunikatów.</span><span class="sxs-lookup"><span data-stu-id="34a25-128">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="34a25-129">Służy do pobierania kryptograficznych materiału, który służy do sprawdzania podpisu.</span><span class="sxs-lookup"><span data-stu-id="34a25-129">It is used to retrieve the cryptographic material that is used for checking the signature.</span></span> <span data-ttu-id="34a25-130">Należy określić `type` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="34a25-130">You must specify the `type` attribute.</span></span> <span data-ttu-id="34a25-131">Określony typ może być <xref:System.IdentityModel.Tokens.IssuerTokenResolver> lub pochodzącego od typu niestandardowego <xref:System.IdentityModel.Tokens.IssuerTokenResolver> klasy.</span><span class="sxs-lookup"><span data-stu-id="34a25-131">The type specified can be either <xref:System.IdentityModel.Tokens.IssuerTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span>  
  
 <span data-ttu-id="34a25-132">Niektóre obsługi tokenów umożliwiają określenie wystawcy program rozpoznawania nazw tokenów ustawienia w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="34a25-132">Some token handlers allow you to specify issuer token resolver settings in configuration.</span></span> <span data-ttu-id="34a25-133">Ustawienia dotyczące poszczególnych programu obsługi tokenów zastąpić określonej w kolekcji programu obsługi tokenów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="34a25-133">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="34a25-134">Określanie `<issuerTokenResolver>` element jako element podrzędny elementu [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element jest przestarzała, ale nadal jest obsługiwany dla zgodności z poprzednimi wersjami.</span><span class="sxs-lookup"><span data-stu-id="34a25-134">Specifying the `<issuerTokenResolver>` element as a child element of the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="34a25-135">Ustawienia na `<securityTokenHandlerConfiguration>` element przesłaniają akcje na `<identityConfiguration>` elementu.</span><span class="sxs-lookup"><span data-stu-id="34a25-135">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="34a25-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="34a25-136">Example</span></span>  
 <span data-ttu-id="34a25-137">Następujący kod XML przedstawia konfigurację dla wystawcy tokenu programu rozpoznawania nazw oparty na niestandardowej klasy, która jest pochodną <xref:System.IdentityModel.Tokens.IssuerTokenResolver>.</span><span class="sxs-lookup"><span data-stu-id="34a25-137">The following XML shows configuration for an issuer token resolver that is based on a custom class that derives from <xref:System.IdentityModel.Tokens.IssuerTokenResolver>.</span></span> <span data-ttu-id="34a25-138">Program rozpoznawania nazw tokenów utrzymują słownik par klucz odbiorców inicjowane z elementu Konfiguracja niestandardowa (`<AddAudienceKeyPair>`) zdefiniowany dla klasy.</span><span class="sxs-lookup"><span data-stu-id="34a25-138">The token resolver maintains a dictionary of audience-key pairs that is initialized from a custom configuration element (`<AddAudienceKeyPair>`) defined for the class.</span></span> <span data-ttu-id="34a25-139">Przesłonięć klasy <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> metody w celu przetworzenia tego elementu.</span><span class="sxs-lookup"><span data-stu-id="34a25-139">The class overrides the <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> method to process this element.</span></span> <span data-ttu-id="34a25-140">Zastąpienie przedstawiono w poniższym przykładzie; metod wywoływanych przez nią nie są wyświetlane do skrócenia.</span><span class="sxs-lookup"><span data-stu-id="34a25-140">The override is shown in the following example; however, the methods it calls are not shown for brevity.</span></span> <span data-ttu-id="34a25-141">Aby uzyskać pełny przykład, zobacz `CustomToken` próbki.</span><span class="sxs-lookup"><span data-stu-id="34a25-141">For the complete example, see the `CustomToken` sample.</span></span>  
  
```xml  
<issuerTokenResolver type="SimpleWebToken.CustomIssuerTokenResolver, SimpleWebToken">  
  <AddAudienceKeyPair  symmetricKey="wAVkldQiFypTQ+kdNdGWCYCHRcee8XmXxOvgmak8vSY=" audience="http://localhost:19851/" />  
</issuerTokenResolver>  
```  
  
## <a name="example"></a><span data-ttu-id="34a25-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="34a25-142">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="34a25-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="34a25-143">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.IssuerTokenResolver>
