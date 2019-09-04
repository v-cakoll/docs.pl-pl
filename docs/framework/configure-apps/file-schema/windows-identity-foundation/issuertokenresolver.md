---
title: <issuerTokenResolver>
ms.date: 03/30/2017
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
author: BrucePerlerMS
ms.openlocfilehash: 8775e3044e58886cfa53a9fd9fc8b4b8ed2105b5
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251953"
---
# <a name="issuertokenresolver"></a><span data-ttu-id="6cb60-101">\<issuerTokenResolver></span><span class="sxs-lookup"><span data-stu-id="6cb60-101">\<issuerTokenResolver></span></span>
<span data-ttu-id="6cb60-102">Rejestruje program rozpoznawania tokenów wystawcy, który jest używany przez programy obsługi w kolekcji obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="6cb60-102">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="6cb60-103">Program rozpoznawania tokenów wystawcy służy do rozpoznawania tokenu podpisywania w przypadku przychodzących tokenów i komunikatów.</span><span class="sxs-lookup"><span data-stu-id="6cb60-103">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span>  
  
<span data-ttu-id="6cb60-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6cb60-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6cb60-105">&nbsp;&nbsp;[ **\<> System. identityModel**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="6cb60-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="6cb60-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="6cb60-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="6cb60-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> obiektów securityTokenHandler**](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="6cb60-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="6cb60-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlerConfiguration >** ](securitytokenhandlerconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="6cb60-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)</span></span>\
<span data-ttu-id="6cb60-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<issuerTokenResolver >**</span><span class="sxs-lookup"><span data-stu-id="6cb60-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerTokenResolver>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cb60-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="6cb60-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6cb60-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6cb60-111">Attributes and Elements</span></span>  
 <span data-ttu-id="6cb60-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6cb60-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6cb60-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6cb60-113">Attributes</span></span>  
  
|<span data-ttu-id="6cb60-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="6cb60-114">Attribute</span></span>|<span data-ttu-id="6cb60-115">Opis</span><span class="sxs-lookup"><span data-stu-id="6cb60-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6cb60-116">— typ</span><span class="sxs-lookup"><span data-stu-id="6cb60-116">type</span></span>|<span data-ttu-id="6cb60-117">Określa typ programu rozpoznawania tokenów wystawcy.</span><span class="sxs-lookup"><span data-stu-id="6cb60-117">Specifies the type of the issuer token resolver.</span></span> <span data-ttu-id="6cb60-118">Musi być <xref:System.IdentityModel.Tokens.IssuerTokenResolver> klasą lub typem, który pochodzi <xref:System.IdentityModel.Tokens.IssuerTokenResolver> od klasy.</span><span class="sxs-lookup"><span data-stu-id="6cb60-118">Must be either the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class or a type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span> <span data-ttu-id="6cb60-119">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="6cb60-119">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6cb60-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6cb60-120">Child Elements</span></span>  
 <span data-ttu-id="6cb60-121">Brak</span><span class="sxs-lookup"><span data-stu-id="6cb60-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6cb60-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6cb60-122">Parent Elements</span></span>  
  
|<span data-ttu-id="6cb60-123">Element</span><span class="sxs-lookup"><span data-stu-id="6cb60-123">Element</span></span>|<span data-ttu-id="6cb60-124">Opis</span><span class="sxs-lookup"><span data-stu-id="6cb60-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6cb60-125">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="6cb60-125">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="6cb60-126">Zapewnia konfigurację kolekcji programów obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="6cb60-126">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6cb60-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6cb60-127">Remarks</span></span>  
 <span data-ttu-id="6cb60-128">Program rozpoznawania tokenów wystawcy służy do rozpoznawania tokenu podpisywania w przypadku przychodzących tokenów i komunikatów.</span><span class="sxs-lookup"><span data-stu-id="6cb60-128">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="6cb60-129">Służy do pobierania materiału kryptograficznego, który jest używany do sprawdzania podpisu.</span><span class="sxs-lookup"><span data-stu-id="6cb60-129">It is used to retrieve the cryptographic material that is used for checking the signature.</span></span> <span data-ttu-id="6cb60-130">Należy określić `type` atrybut.</span><span class="sxs-lookup"><span data-stu-id="6cb60-130">You must specify the `type` attribute.</span></span> <span data-ttu-id="6cb60-131">Określony typ może być albo <xref:System.IdentityModel.Tokens.IssuerTokenResolver> typem niestandardowym, który pochodzi <xref:System.IdentityModel.Tokens.IssuerTokenResolver> od klasy.</span><span class="sxs-lookup"><span data-stu-id="6cb60-131">The type specified can be either <xref:System.IdentityModel.Tokens.IssuerTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span>  
  
 <span data-ttu-id="6cb60-132">Niektóre programy obsługi tokenów umożliwiają określenie ustawień programu rozpoznawania tokenów wystawcy w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="6cb60-132">Some token handlers allow you to specify issuer token resolver settings in configuration.</span></span> <span data-ttu-id="6cb60-133">Ustawienia poszczególnych programów obsługi tokenów przesłaniają te określone w kolekcji obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="6cb60-133">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6cb60-134">Określanie elementu jako elementu [ \<](identityconfiguration.md) podrzędnego elementu IdentityConfiguration > jest przestarzałe, ale nadal jest on obsługiwany w celu zapewnienia zgodności z poprzednimi wersjami. `<issuerTokenResolver>`</span><span class="sxs-lookup"><span data-stu-id="6cb60-134">Specifying the `<issuerTokenResolver>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="6cb60-135">Ustawienia w `<securityTokenHandlerConfiguration>` elemencie Przesłoń te elementy `<identityConfiguration>` w elemencie.</span><span class="sxs-lookup"><span data-stu-id="6cb60-135">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6cb60-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="6cb60-136">Example</span></span>  
 <span data-ttu-id="6cb60-137">W poniższym kodzie XML przedstawiono konfigurację programu rozpoznawania tokenów wystawcy opartą na niestandardowej klasie, która <xref:System.IdentityModel.Tokens.IssuerTokenResolver>pochodzi od.</span><span class="sxs-lookup"><span data-stu-id="6cb60-137">The following XML shows configuration for an issuer token resolver that is based on a custom class that derives from <xref:System.IdentityModel.Tokens.IssuerTokenResolver>.</span></span> <span data-ttu-id="6cb60-138">Program rozpoznawania tokenów obsługuje słownik par kluczy odbiorców, które są inicjowane z niestandardowego elementu konfiguracji (`<AddAudienceKeyPair>`) zdefiniowanego dla klasy.</span><span class="sxs-lookup"><span data-stu-id="6cb60-138">The token resolver maintains a dictionary of audience-key pairs that is initialized from a custom configuration element (`<AddAudienceKeyPair>`) defined for the class.</span></span> <span data-ttu-id="6cb60-139">Klasa przesłania <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> metodę w celu przetworzenia tego elementu.</span><span class="sxs-lookup"><span data-stu-id="6cb60-139">The class overrides the <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> method to process this element.</span></span> <span data-ttu-id="6cb60-140">Przesłonięcie pokazano w następującym przykładzie: jednak metody, które wywołuje, nie są wyświetlane dla zwięzłości.</span><span class="sxs-lookup"><span data-stu-id="6cb60-140">The override is shown in the following example; however, the methods it calls are not shown for brevity.</span></span> <span data-ttu-id="6cb60-141">Aby uzyskać pełny przykład, zobacz `CustomToken` przykład.</span><span class="sxs-lookup"><span data-stu-id="6cb60-141">For the complete example, see the `CustomToken` sample.</span></span>  
  
```xml  
<issuerTokenResolver type="SimpleWebToken.CustomIssuerTokenResolver, SimpleWebToken">  
  <AddAudienceKeyPair  symmetricKey="wAVkldQiFypTQ+kdNdGWCYCHRcee8XmXxOvgmak8vSY=" audience="http://localhost:19851/" />  
</issuerTokenResolver>  
```  
  
## <a name="example"></a><span data-ttu-id="6cb60-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="6cb60-142">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6cb60-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6cb60-143">See also</span></span>

- <xref:System.IdentityModel.Tokens.IssuerTokenResolver>
