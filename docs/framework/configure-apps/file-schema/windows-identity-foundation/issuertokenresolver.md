---
title: <issuerTokenResolver>
ms.date: 03/30/2017
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
author: BrucePerlerMS
ms.openlocfilehash: 67d7e0aa5b6b05bfe8b17a1b1efebb1fbddbb0eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152674"
---
# <a name="issuertokenresolver"></a><span data-ttu-id="334ba-101">\<>></span><span class="sxs-lookup"><span data-stu-id="334ba-101">\<issuerTokenResolver></span></span>
<span data-ttu-id="334ba-102">Rejestruje program rozpoznawania nazw tokenów wystawcy, który jest używany przez programy obsługi w kolekcji obsługi tokenu.</span><span class="sxs-lookup"><span data-stu-id="334ba-102">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="334ba-103">Program rozpoznawania nazw tokenów wystawcy służy do rozpoznawania tokenu podpisywania na przychodzących tokenach i wiadomościach.</span><span class="sxs-lookup"><span data-stu-id="334ba-103">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span>  
  
<span data-ttu-id="334ba-104">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="334ba-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="334ba-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="334ba-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="334ba-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<>konfiguracji tożsamości**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="334ba-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="334ba-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>securityTokenHandlers**](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="334ba-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="334ba-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>konfiguracji securityTokenHandler**](securitytokenhandlerconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="334ba-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)</span></span>\
<span data-ttu-id="334ba-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>>**</span><span class="sxs-lookup"><span data-stu-id="334ba-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerTokenResolver>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="334ba-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="334ba-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="334ba-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="334ba-111">Attributes and Elements</span></span>  
 <span data-ttu-id="334ba-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="334ba-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="334ba-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="334ba-113">Attributes</span></span>  
  
|<span data-ttu-id="334ba-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="334ba-114">Attribute</span></span>|<span data-ttu-id="334ba-115">Opis</span><span class="sxs-lookup"><span data-stu-id="334ba-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="334ba-116">type</span><span class="sxs-lookup"><span data-stu-id="334ba-116">type</span></span>|<span data-ttu-id="334ba-117">Określa typ programu rozpoznawania tokenów wystawcy.</span><span class="sxs-lookup"><span data-stu-id="334ba-117">Specifies the type of the issuer token resolver.</span></span> <span data-ttu-id="334ba-118">Musi być klasą <xref:System.IdentityModel.Tokens.IssuerTokenResolver> lub typem, który <xref:System.IdentityModel.Tokens.IssuerTokenResolver> wywodzi się z klasy.</span><span class="sxs-lookup"><span data-stu-id="334ba-118">Must be either the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class or a type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span> <span data-ttu-id="334ba-119">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="334ba-119">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="334ba-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="334ba-120">Child Elements</span></span>  
 <span data-ttu-id="334ba-121">Brak</span><span class="sxs-lookup"><span data-stu-id="334ba-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="334ba-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="334ba-122">Parent Elements</span></span>  
  
|<span data-ttu-id="334ba-123">Element</span><span class="sxs-lookup"><span data-stu-id="334ba-123">Element</span></span>|<span data-ttu-id="334ba-124">Opis</span><span class="sxs-lookup"><span data-stu-id="334ba-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="334ba-125">\<>konfiguracji securityTokenHandler</span><span class="sxs-lookup"><span data-stu-id="334ba-125">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="334ba-126">Zapewnia konfigurację dla kolekcji obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="334ba-126">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="334ba-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="334ba-127">Remarks</span></span>  
 <span data-ttu-id="334ba-128">Program rozpoznawania nazw tokenów wystawcy służy do rozpoznawania tokenu podpisywania na przychodzących tokenach i wiadomościach.</span><span class="sxs-lookup"><span data-stu-id="334ba-128">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="334ba-129">Służy do pobierania materiału kryptograficznego, który jest używany do sprawdzania podpisu.</span><span class="sxs-lookup"><span data-stu-id="334ba-129">It is used to retrieve the cryptographic material that is used for checking the signature.</span></span> <span data-ttu-id="334ba-130">Należy określić `type` atrybut.</span><span class="sxs-lookup"><span data-stu-id="334ba-130">You must specify the `type` attribute.</span></span> <span data-ttu-id="334ba-131">Określony typ może być <xref:System.IdentityModel.Tokens.IssuerTokenResolver> albo typu niestandardowego, <xref:System.IdentityModel.Tokens.IssuerTokenResolver> który pochodzi od klasy.</span><span class="sxs-lookup"><span data-stu-id="334ba-131">The type specified can be either <xref:System.IdentityModel.Tokens.IssuerTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span>  
  
 <span data-ttu-id="334ba-132">Niektóre programy obsługi tokenu umożliwiają określenie ustawień rozpoznawania nazw tokenów wystawcy w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="334ba-132">Some token handlers allow you to specify issuer token resolver settings in configuration.</span></span> <span data-ttu-id="334ba-133">Ustawienia poszczególnych programów obsługi tokenów zastępują te określone w kolekcji obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="334ba-133">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="334ba-134">Określanie `<issuerTokenResolver>` elementu jako elementu podrzędnego [ \<identityConfiguration>](identityconfiguration.md) element został przestarzały, ale nadal jest obsługiwany dla zgodności z powrotem.</span><span class="sxs-lookup"><span data-stu-id="334ba-134">Specifying the `<issuerTokenResolver>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="334ba-135">Ustawienia elementu `<securityTokenHandlerConfiguration>` zastąpić te na `<identityConfiguration>` elemencie.</span><span class="sxs-lookup"><span data-stu-id="334ba-135">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="334ba-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="334ba-136">Example</span></span>  
 <span data-ttu-id="334ba-137">Poniższy kod XML przedstawia konfigurację programu rozpoznawania tokenów wystawcy, <xref:System.IdentityModel.Tokens.IssuerTokenResolver>która jest oparta na klasie niestandardowej, która wywodzi się z .</span><span class="sxs-lookup"><span data-stu-id="334ba-137">The following XML shows configuration for an issuer token resolver that is based on a custom class that derives from <xref:System.IdentityModel.Tokens.IssuerTokenResolver>.</span></span> <span data-ttu-id="334ba-138">Program rozpoznawania nazw tokenów przechowuje słownik par klucza odbiorców, który jest`<AddAudienceKeyPair>`inicjowany z niestandardowego elementu konfiguracji ( ) zdefiniowanego dla klasy.</span><span class="sxs-lookup"><span data-stu-id="334ba-138">The token resolver maintains a dictionary of audience-key pairs that is initialized from a custom configuration element (`<AddAudienceKeyPair>`) defined for the class.</span></span> <span data-ttu-id="334ba-139">Klasa zastępuje <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> metodę przetwarzania tego elementu.</span><span class="sxs-lookup"><span data-stu-id="334ba-139">The class overrides the <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> method to process this element.</span></span> <span data-ttu-id="334ba-140">Zastąpienie jest pokazane w poniższym przykładzie; jednak metody, które wywołuje, nie są wyświetlane dla zwięzłości.</span><span class="sxs-lookup"><span data-stu-id="334ba-140">The override is shown in the following example; however, the methods it calls are not shown for brevity.</span></span> <span data-ttu-id="334ba-141">Pełny przykład można znaleźć `CustomToken` w przykładzie.</span><span class="sxs-lookup"><span data-stu-id="334ba-141">For the complete example, see the `CustomToken` sample.</span></span>  
  
```xml  
<issuerTokenResolver type="SimpleWebToken.CustomIssuerTokenResolver, SimpleWebToken">  
  <AddAudienceKeyPair  symmetricKey="wAVkldQiFypTQ+kdNdGWCYCHRcee8XmXxOvgmak8vSY=" audience="http://localhost:19851/" />  
</issuerTokenResolver>  
```  
  
## <a name="example"></a><span data-ttu-id="334ba-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="334ba-142">Example</span></span>
  
```csharp
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
  
## <a name="see-also"></a><span data-ttu-id="334ba-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="334ba-143">See also</span></span>

- <xref:System.IdentityModel.Tokens.IssuerTokenResolver>
