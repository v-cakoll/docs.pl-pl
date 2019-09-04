---
title: <add>
ms.date: 03/30/2017
ms.assetid: 4712a888-f154-4395-8887-ef14a88a6497
author: BrucePerlerMS
ms.openlocfilehash: 932e8452542ace66824fba1262694c220ce88676
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252185"
---
# <a name="add"></a><span data-ttu-id="ec7dc-101">\<add></span><span class="sxs-lookup"><span data-stu-id="ec7dc-101">\<add></span></span>
<span data-ttu-id="ec7dc-102">Dodaje określony program obsługi tokenów zabezpieczających do kolekcji obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="ec7dc-102">Adds the specified security token handler to the token handler collection.</span></span>  
  
<span data-ttu-id="ec7dc-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ec7dc-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ec7dc-104">&nbsp;&nbsp;[ **\<> System. identityModel**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="ec7dc-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="ec7dc-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="ec7dc-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="ec7dc-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> obiektów securityTokenHandler**](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="ec7dc-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="ec7dc-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Dodaj >**</span><span class="sxs-lookup"><span data-stu-id="ec7dc-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec7dc-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="ec7dc-108">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type=xs:string>  
        <optionalConfigurationElement>  
        </optionalConfigurationElement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ec7dc-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ec7dc-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ec7dc-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ec7dc-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ec7dc-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ec7dc-111">Attributes</span></span>  
  
|<span data-ttu-id="ec7dc-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ec7dc-112">Attribute</span></span>|<span data-ttu-id="ec7dc-113">Opis</span><span class="sxs-lookup"><span data-stu-id="ec7dc-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ec7dc-114">— typ</span><span class="sxs-lookup"><span data-stu-id="ec7dc-114">type</span></span>|<span data-ttu-id="ec7dc-115">Nazwa typu CLR programu obsługi tokenów, który ma zostać dodany.</span><span class="sxs-lookup"><span data-stu-id="ec7dc-115">The CLR type name of the token handler to be added.</span></span> <span data-ttu-id="ec7dc-116">Aby uzyskać więcej informacji na temat sposobu określania `type` atrybutu, zobacz [odwołania do typów niestandardowych](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span><span class="sxs-lookup"><span data-stu-id="ec7dc-116">For more information about how to specify the `type` attribute, see [Custom Type References](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ec7dc-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ec7dc-117">Child Elements</span></span>  
  
|<span data-ttu-id="ec7dc-118">Element</span><span class="sxs-lookup"><span data-stu-id="ec7dc-118">Element</span></span>|<span data-ttu-id="ec7dc-119">Opis</span><span class="sxs-lookup"><span data-stu-id="ec7dc-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ec7dc-120">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="ec7dc-120">\<samlSecurityTokenRequirement></span></span>](samlsecuritytokenrequirement.md)|<span data-ttu-id="ec7dc-121">Zapewnia konfigurację <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> klasy <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> , klasy lub klasy pochodnej jednej z tych klas.</span><span class="sxs-lookup"><span data-stu-id="ec7dc-121">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
|[<span data-ttu-id="ec7dc-122">\<sessionTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="ec7dc-122">\<sessionTokenRequirement></span></span>](sessiontokenrequirement.md)|<span data-ttu-id="ec7dc-123">Zapewnia konfigurację <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> klasy lub klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="ec7dc-123">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>|  
|[<span data-ttu-id="ec7dc-124">\<userNameSecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="ec7dc-124">\<userNameSecurityTokenHandlerRequirement></span></span>](usernamesecuritytokenhandlerrequirement.md)|<span data-ttu-id="ec7dc-125">Zapewnia konfigurację <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> klasy lub klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="ec7dc-125">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>|  
|[<span data-ttu-id="ec7dc-126">\<x509SecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="ec7dc-126">\<x509SecurityTokenHandlerRequirement></span></span>](x509securitytokenhandlerrequirement.md)|<span data-ttu-id="ec7dc-127">Zapewnia opcjonalną konfigurację <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> klasy lub klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="ec7dc-127">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ec7dc-128">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ec7dc-128">Parent Elements</span></span>  
  
|<span data-ttu-id="ec7dc-129">Element</span><span class="sxs-lookup"><span data-stu-id="ec7dc-129">Element</span></span>|<span data-ttu-id="ec7dc-130">Opis</span><span class="sxs-lookup"><span data-stu-id="ec7dc-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ec7dc-131">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="ec7dc-131">\<securityTokenHandlers></span></span>](securitytokenhandlers.md)|<span data-ttu-id="ec7dc-132">Określa kolekcję programów obsługi tokenów zabezpieczających, które są zarejestrowane w punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="ec7dc-132">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ec7dc-133">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ec7dc-133">Remarks</span></span>  
 <span data-ttu-id="ec7dc-134">`<add>` Element może przyjmować jeden element podrzędny, który określa konfigurację programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="ec7dc-134">The `<add>` element can take a single child element that specifies the configuration for the token handler.</span></span> <span data-ttu-id="ec7dc-135">Jest to zależne od tego, czy Klasa obsługi, `type` do której odwołuje się atrybut `<add>` elementu, zapewnia obsługę tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="ec7dc-135">This is dependent on whether the handler class referenced through the `type` attribute of the `<add>` element provides support for this feature.</span></span> <span data-ttu-id="ec7dc-136">Klasy obsługi tokenów, które udostępniają tę funkcję, muszą uwidaczniać <xref:System.Xml.XmlElement> Konstruktor, który pobiera obiekt.</span><span class="sxs-lookup"><span data-stu-id="ec7dc-136">Token handler classes that provide this feature must expose a constructor that takes an <xref:System.Xml.XmlElement> object.</span></span>  
  
```  
public class CustomTokenHandler : Microsoft.IdentityModel.Tokens.SecurityTokenHandler  
{  
    public CustomTokenHandler( XmlElement customConfig )  
    {  
    }  
}  
```  
  
 <span data-ttu-id="ec7dc-137">Niektóre wbudowane klasy procedury obsługi tokenów zabezpieczających zapewniają tę funkcję.</span><span class="sxs-lookup"><span data-stu-id="ec7dc-137">Several of the built-in security token handler classes do provide this functionality.</span></span> <span data-ttu-id="ec7dc-138">Te klasy to <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> ,<xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>,, i<xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>. <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler></span><span class="sxs-lookup"><span data-stu-id="ec7dc-138">These classes are <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, and <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ec7dc-139">Kolekcja obsługi tokenów może zawierać tylko jedną procedurę obsługi dla danego typu.</span><span class="sxs-lookup"><span data-stu-id="ec7dc-139">The token handler collection can only contain a single handler of any given type.</span></span> <span data-ttu-id="ec7dc-140">Oznacza to, na przykład, że jeśli chcesz dodać program obsługi, który pochodzi od <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> klasy do kolekcji, musisz najpierw <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>usunąć element, który jest domyślnie obecny, z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="ec7dc-140">This means, for example, that if you want to add a handler that is derived from the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class to the collection, you must first remove the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, which is present by default, from the collection.</span></span> <span data-ttu-id="ec7dc-141">Można użyć elementu [ \<Remove >](remove.md) , aby usunąć pojedynczą procedurę obsługi z kolekcji lub użyć elementu [ \<Clear >](clear.md) , aby usunąć wszystkie programy obsługi z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="ec7dc-141">You can use the [\<remove>](remove.md) element to remove a single handler from the collection or use the [\<clear>](clear.md) element to remove all handlers from the collection.</span></span>  
  
 <span data-ttu-id="ec7dc-142">Ustawienia określone w ustawieniach przesłonięcia programu obsługi określone w kolekcji obsługi tokenów w [ \<elemencie securityTokenHandlerConfiguration >](securitytokenhandlerconfiguration.md) i określonych na poziomie usługi w ramach [ \< identityConfiguration >](identityconfiguration.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="ec7dc-142">Settings specified on a handler override equivalent settings specified on the token handler collection under the [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) element and those specified at the service-level under the [\<identityConfiguration>](identityconfiguration.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec7dc-143">Przykład</span><span class="sxs-lookup"><span data-stu-id="ec7dc-143">Example</span></span>  
 <span data-ttu-id="ec7dc-144">Poniższy kod XML pokazuje użycie `<add>` elementów i `<remove>` , aby zastąpić domyślną procedurę obsługi tokena sesji za pomocą procedury obsługi niestandardowego tokenu sesji.</span><span class="sxs-lookup"><span data-stu-id="ec7dc-144">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="ec7dc-145">Kod XML jest pobierany z `ClaimsAwareWebFarm` przykładu.</span><span class="sxs-lookup"><span data-stu-id="ec7dc-145">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
