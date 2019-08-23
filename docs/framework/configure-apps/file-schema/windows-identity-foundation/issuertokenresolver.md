---
title: <issuerTokenResolver>
ms.date: 03/30/2017
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
author: BrucePerlerMS
ms.openlocfilehash: da591940910b16d42ef8ab1a05c4b244dbe543f4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942629"
---
# <a name="issuertokenresolver"></a><span data-ttu-id="4d336-101">\<issuerTokenResolver></span><span class="sxs-lookup"><span data-stu-id="4d336-101">\<issuerTokenResolver></span></span>
<span data-ttu-id="4d336-102">Rejestruje program rozpoznawania tokenów wystawcy, który jest używany przez programy obsługi w kolekcji obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="4d336-102">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="4d336-103">Program rozpoznawania tokenów wystawcy służy do rozpoznawania tokenu podpisywania w przypadku przychodzących tokenów i komunikatów.</span><span class="sxs-lookup"><span data-stu-id="4d336-103">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span>  
  
 <span data-ttu-id="4d336-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="4d336-104">\<system.identityModel></span></span>  
<span data-ttu-id="4d336-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="4d336-105">\<identityConfiguration></span></span>  
<span data-ttu-id="4d336-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="4d336-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="4d336-107">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="4d336-107">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="4d336-108">\<issuerTokenResolver></span><span class="sxs-lookup"><span data-stu-id="4d336-108">\<issuerTokenResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d336-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="4d336-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4d336-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4d336-110">Attributes and Elements</span></span>  
 <span data-ttu-id="4d336-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4d336-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4d336-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4d336-112">Attributes</span></span>  
  
|<span data-ttu-id="4d336-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4d336-113">Attribute</span></span>|<span data-ttu-id="4d336-114">Opis</span><span class="sxs-lookup"><span data-stu-id="4d336-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4d336-115">— typ</span><span class="sxs-lookup"><span data-stu-id="4d336-115">type</span></span>|<span data-ttu-id="4d336-116">Określa typ programu rozpoznawania tokenów wystawcy.</span><span class="sxs-lookup"><span data-stu-id="4d336-116">Specifies the type of the issuer token resolver.</span></span> <span data-ttu-id="4d336-117">Musi być <xref:System.IdentityModel.Tokens.IssuerTokenResolver> klasą lub typem, który pochodzi <xref:System.IdentityModel.Tokens.IssuerTokenResolver> od klasy.</span><span class="sxs-lookup"><span data-stu-id="4d336-117">Must be either the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class or a type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span> <span data-ttu-id="4d336-118">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="4d336-118">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4d336-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4d336-119">Child Elements</span></span>  
 <span data-ttu-id="4d336-120">Brak</span><span class="sxs-lookup"><span data-stu-id="4d336-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4d336-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4d336-121">Parent Elements</span></span>  
  
|<span data-ttu-id="4d336-122">Element</span><span class="sxs-lookup"><span data-stu-id="4d336-122">Element</span></span>|<span data-ttu-id="4d336-123">Opis</span><span class="sxs-lookup"><span data-stu-id="4d336-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4d336-124">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="4d336-124">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="4d336-125">Zapewnia konfigurację kolekcji programów obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="4d336-125">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4d336-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4d336-126">Remarks</span></span>  
 <span data-ttu-id="4d336-127">Program rozpoznawania tokenów wystawcy służy do rozpoznawania tokenu podpisywania w przypadku przychodzących tokenów i komunikatów.</span><span class="sxs-lookup"><span data-stu-id="4d336-127">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="4d336-128">Służy do pobierania materiału kryptograficznego, który jest używany do sprawdzania podpisu.</span><span class="sxs-lookup"><span data-stu-id="4d336-128">It is used to retrieve the cryptographic material that is used for checking the signature.</span></span> <span data-ttu-id="4d336-129">Należy określić `type` atrybut.</span><span class="sxs-lookup"><span data-stu-id="4d336-129">You must specify the `type` attribute.</span></span> <span data-ttu-id="4d336-130">Określony typ może być albo <xref:System.IdentityModel.Tokens.IssuerTokenResolver> typem niestandardowym, który pochodzi <xref:System.IdentityModel.Tokens.IssuerTokenResolver> od klasy.</span><span class="sxs-lookup"><span data-stu-id="4d336-130">The type specified can be either <xref:System.IdentityModel.Tokens.IssuerTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span>  
  
 <span data-ttu-id="4d336-131">Niektóre programy obsługi tokenów umożliwiają określenie ustawień programu rozpoznawania tokenów wystawcy w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="4d336-131">Some token handlers allow you to specify issuer token resolver settings in configuration.</span></span> <span data-ttu-id="4d336-132">Ustawienia poszczególnych programów obsługi tokenów przesłaniają te określone w kolekcji obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="4d336-132">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4d336-133">Określanie elementu jako elementu [ \<](identityconfiguration.md) podrzędnego elementu IdentityConfiguration > jest przestarzałe, ale nadal jest on obsługiwany w celu zapewnienia zgodności z poprzednimi wersjami. `<issuerTokenResolver>`</span><span class="sxs-lookup"><span data-stu-id="4d336-133">Specifying the `<issuerTokenResolver>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="4d336-134">Ustawienia w `<securityTokenHandlerConfiguration>` elemencie Przesłoń te elementy `<identityConfiguration>` w elemencie.</span><span class="sxs-lookup"><span data-stu-id="4d336-134">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d336-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="4d336-135">Example</span></span>  
 <span data-ttu-id="4d336-136">W poniższym kodzie XML przedstawiono konfigurację programu rozpoznawania tokenów wystawcy opartą na niestandardowej klasie, która <xref:System.IdentityModel.Tokens.IssuerTokenResolver>pochodzi od.</span><span class="sxs-lookup"><span data-stu-id="4d336-136">The following XML shows configuration for an issuer token resolver that is based on a custom class that derives from <xref:System.IdentityModel.Tokens.IssuerTokenResolver>.</span></span> <span data-ttu-id="4d336-137">Program rozpoznawania tokenów obsługuje słownik par kluczy odbiorców, które są inicjowane z niestandardowego elementu konfiguracji (`<AddAudienceKeyPair>`) zdefiniowanego dla klasy.</span><span class="sxs-lookup"><span data-stu-id="4d336-137">The token resolver maintains a dictionary of audience-key pairs that is initialized from a custom configuration element (`<AddAudienceKeyPair>`) defined for the class.</span></span> <span data-ttu-id="4d336-138">Klasa przesłania <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> metodę w celu przetworzenia tego elementu.</span><span class="sxs-lookup"><span data-stu-id="4d336-138">The class overrides the <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> method to process this element.</span></span> <span data-ttu-id="4d336-139">Przesłonięcie pokazano w następującym przykładzie: jednak metody, które wywołuje, nie są wyświetlane dla zwięzłości.</span><span class="sxs-lookup"><span data-stu-id="4d336-139">The override is shown in the following example; however, the methods it calls are not shown for brevity.</span></span> <span data-ttu-id="4d336-140">Aby uzyskać pełny przykład, zobacz `CustomToken` przykład.</span><span class="sxs-lookup"><span data-stu-id="4d336-140">For the complete example, see the `CustomToken` sample.</span></span>  
  
```xml  
<issuerTokenResolver type="SimpleWebToken.CustomIssuerTokenResolver, SimpleWebToken">  
  <AddAudienceKeyPair  symmetricKey="wAVkldQiFypTQ+kdNdGWCYCHRcee8XmXxOvgmak8vSY=" audience="http://localhost:19851/" />  
</issuerTokenResolver>  
```  
  
## <a name="example"></a><span data-ttu-id="4d336-141">Przykład</span><span class="sxs-lookup"><span data-stu-id="4d336-141">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4d336-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4d336-142">See also</span></span>

- <xref:System.IdentityModel.Tokens.IssuerTokenResolver>
