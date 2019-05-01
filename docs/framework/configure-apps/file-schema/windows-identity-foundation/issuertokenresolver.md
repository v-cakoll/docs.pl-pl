---
title: <issuerTokenResolver>
ms.date: 03/30/2017
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
author: BrucePerlerMS
ms.openlocfilehash: 08082d2e6647f07f33df72ab79dac00c15a1cd1b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791615"
---
# <a name="issuertokenresolver"></a><span data-ttu-id="c350c-101">\<issuerTokenResolver></span><span class="sxs-lookup"><span data-stu-id="c350c-101">\<issuerTokenResolver></span></span>
<span data-ttu-id="c350c-102">Rejestruje wystawcy program rozpoznawania tokenów, który jest używany przez programy obsługi w kolekcji programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="c350c-102">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="c350c-103">Program rozpoznawania tokenów wystawcy jest używany do rozpoznawania token podpisujący na przychodzące tokeny i komunikatów.</span><span class="sxs-lookup"><span data-stu-id="c350c-103">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span>  
  
 <span data-ttu-id="c350c-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="c350c-104">\<system.identityModel></span></span>  
<span data-ttu-id="c350c-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="c350c-105">\<identityConfiguration></span></span>  
<span data-ttu-id="c350c-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="c350c-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="c350c-107">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="c350c-107">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="c350c-108">\<issuerTokenResolver></span><span class="sxs-lookup"><span data-stu-id="c350c-108">\<issuerTokenResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c350c-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="c350c-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c350c-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c350c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c350c-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c350c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c350c-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c350c-112">Attributes</span></span>  
  
|<span data-ttu-id="c350c-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c350c-113">Attribute</span></span>|<span data-ttu-id="c350c-114">Opis</span><span class="sxs-lookup"><span data-stu-id="c350c-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c350c-115">— typ</span><span class="sxs-lookup"><span data-stu-id="c350c-115">type</span></span>|<span data-ttu-id="c350c-116">Określa typ program rozpoznawania tokenów wystawcy.</span><span class="sxs-lookup"><span data-stu-id="c350c-116">Specifies the type of the issuer token resolver.</span></span> <span data-ttu-id="c350c-117">Musi być albo <xref:System.IdentityModel.Tokens.IssuerTokenResolver> klasy lub typu, która pochodzi od klasy <xref:System.IdentityModel.Tokens.IssuerTokenResolver> klasy.</span><span class="sxs-lookup"><span data-stu-id="c350c-117">Must be either the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class or a type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span> <span data-ttu-id="c350c-118">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="c350c-118">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c350c-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c350c-119">Child Elements</span></span>  
 <span data-ttu-id="c350c-120">Brak</span><span class="sxs-lookup"><span data-stu-id="c350c-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c350c-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c350c-121">Parent Elements</span></span>  
  
|<span data-ttu-id="c350c-122">Element</span><span class="sxs-lookup"><span data-stu-id="c350c-122">Element</span></span>|<span data-ttu-id="c350c-123">Opis</span><span class="sxs-lookup"><span data-stu-id="c350c-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c350c-124">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="c350c-124">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="c350c-125">Udostępnia konfigurację dla kolekcji zabezpieczeń programy obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="c350c-125">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c350c-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c350c-126">Remarks</span></span>  
 <span data-ttu-id="c350c-127">Program rozpoznawania tokenów wystawcy jest używany do rozpoznawania token podpisujący na przychodzące tokeny i komunikatów.</span><span class="sxs-lookup"><span data-stu-id="c350c-127">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="c350c-128">Służy do pobierania materiałami kryptograficznymi, który służy do sprawdzania podpisu.</span><span class="sxs-lookup"><span data-stu-id="c350c-128">It is used to retrieve the cryptographic material that is used for checking the signature.</span></span> <span data-ttu-id="c350c-129">Należy określić `type` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="c350c-129">You must specify the `type` attribute.</span></span> <span data-ttu-id="c350c-130">Określony typ może być <xref:System.IdentityModel.Tokens.IssuerTokenResolver> lub typ niestandardowy, który pochodzi od klasy <xref:System.IdentityModel.Tokens.IssuerTokenResolver> klasy.</span><span class="sxs-lookup"><span data-stu-id="c350c-130">The type specified can be either <xref:System.IdentityModel.Tokens.IssuerTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span>  
  
 <span data-ttu-id="c350c-131">Niektóre programy obsługi tokenów umożliwiają określanie ustawień program rozpoznawania tokenów wystawcy w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c350c-131">Some token handlers allow you to specify issuer token resolver settings in configuration.</span></span> <span data-ttu-id="c350c-132">Ustawienia dotyczące programu obsługi tokenów poszczególnych zastąpienia określonej w kolekcji programu obsługi tokenów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="c350c-132">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c350c-133">Określanie `<issuerTokenResolver>` element jako element podrzędny [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elementu jest przestarzałe, ale nadal jest obsługiwany dla zgodności z poprzednimi wersjami.</span><span class="sxs-lookup"><span data-stu-id="c350c-133">Specifying the `<issuerTokenResolver>` element as a child element of the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="c350c-134">Ustawienia na `<securityTokenHandlerConfiguration>` elemencie przesłaniają akcje na `<identityConfiguration>` elementu.</span><span class="sxs-lookup"><span data-stu-id="c350c-134">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c350c-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="c350c-135">Example</span></span>  
 <span data-ttu-id="c350c-136">Następujący kody XML pokazuje konfigurację dla wystawcy program rozpoznawania tokenów opartego na klasę niestandardową, która pochodzi od klasy <xref:System.IdentityModel.Tokens.IssuerTokenResolver>.</span><span class="sxs-lookup"><span data-stu-id="c350c-136">The following XML shows configuration for an issuer token resolver that is based on a custom class that derives from <xref:System.IdentityModel.Tokens.IssuerTokenResolver>.</span></span> <span data-ttu-id="c350c-137">Program rozpoznawania tokenów przechowuje słownika par klucz odbiorców, który jest inicjowany z niestandardowy element konfiguracji (`<AddAudienceKeyPair>`) zdefiniowane dla klasy.</span><span class="sxs-lookup"><span data-stu-id="c350c-137">The token resolver maintains a dictionary of audience-key pairs that is initialized from a custom configuration element (`<AddAudienceKeyPair>`) defined for the class.</span></span> <span data-ttu-id="c350c-138">Przesłonięć klasy <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> metody do przetworzenia tego elementu.</span><span class="sxs-lookup"><span data-stu-id="c350c-138">The class overrides the <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> method to process this element.</span></span> <span data-ttu-id="c350c-139">Zastąpienie przedstawiono w poniższym przykładzie; jednak metod wywoływanych przez nią nie są wyświetlane w celu skrócenia programu.</span><span class="sxs-lookup"><span data-stu-id="c350c-139">The override is shown in the following example; however, the methods it calls are not shown for brevity.</span></span> <span data-ttu-id="c350c-140">Aby uzyskać kompletny przykład, zobacz `CustomToken` próbki.</span><span class="sxs-lookup"><span data-stu-id="c350c-140">For the complete example, see the `CustomToken` sample.</span></span>  
  
```xml  
<issuerTokenResolver type="SimpleWebToken.CustomIssuerTokenResolver, SimpleWebToken">  
  <AddAudienceKeyPair  symmetricKey="wAVkldQiFypTQ+kdNdGWCYCHRcee8XmXxOvgmak8vSY=" audience="http://localhost:19851/" />  
</issuerTokenResolver>  
```  
  
## <a name="example"></a><span data-ttu-id="c350c-141">Przykład</span><span class="sxs-lookup"><span data-stu-id="c350c-141">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c350c-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c350c-142">See also</span></span>

- <xref:System.IdentityModel.Tokens.IssuerTokenResolver>
