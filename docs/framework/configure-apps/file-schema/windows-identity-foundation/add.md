---
title: <add>
ms.date: 03/30/2017
ms.assetid: 4712a888-f154-4395-8887-ef14a88a6497
author: BrucePerlerMS
ms.openlocfilehash: 83ba51cbbd5100bf7412f9914a270cac88f7faa1
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73973801"
---
# <a name="add"></a><span data-ttu-id="77a3f-101">\<Dodaj ></span><span class="sxs-lookup"><span data-stu-id="77a3f-101">\<add></span></span>
<span data-ttu-id="77a3f-102">Dodaje określony program obsługi tokenów zabezpieczających do kolekcji obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="77a3f-102">Adds the specified security token handler to the token handler collection.</span></span>  
  
<span data-ttu-id="77a3f-103">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="77a3f-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="77a3f-104">&nbsp;&nbsp;[ **\<system. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="77a3f-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="77a3f-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="77a3f-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="77a3f-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**SecurityTokenHandler**](securitytokenhandlers.md) ></span><span class="sxs-lookup"><span data-stu-id="77a3f-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="77a3f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<dodaj >**</span><span class="sxs-lookup"><span data-stu-id="77a3f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77a3f-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="77a3f-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="77a3f-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="77a3f-109">Attributes and Elements</span></span>  
 <span data-ttu-id="77a3f-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="77a3f-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="77a3f-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="77a3f-111">Attributes</span></span>  
  
|<span data-ttu-id="77a3f-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="77a3f-112">Attribute</span></span>|<span data-ttu-id="77a3f-113">Opis</span><span class="sxs-lookup"><span data-stu-id="77a3f-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="77a3f-114">— typ</span><span class="sxs-lookup"><span data-stu-id="77a3f-114">type</span></span>|<span data-ttu-id="77a3f-115">Nazwa typu CLR programu obsługi tokenów, który ma zostać dodany.</span><span class="sxs-lookup"><span data-stu-id="77a3f-115">The CLR type name of the token handler to be added.</span></span> <span data-ttu-id="77a3f-116">Aby uzyskać więcej informacji na temat sposobu określania atrybutu `type`, zobacz [odwołania do typów niestandardowych](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span><span class="sxs-lookup"><span data-stu-id="77a3f-116">For more information about how to specify the `type` attribute, see [Custom Type References](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="77a3f-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="77a3f-117">Child Elements</span></span>  
  
|<span data-ttu-id="77a3f-118">Element</span><span class="sxs-lookup"><span data-stu-id="77a3f-118">Element</span></span>|<span data-ttu-id="77a3f-119">Opis</span><span class="sxs-lookup"><span data-stu-id="77a3f-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="77a3f-120">\<samlSecurityTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="77a3f-120">\<samlSecurityTokenRequirement></span></span>](samlsecuritytokenrequirement.md)|<span data-ttu-id="77a3f-121">Zapewnia konfigurację dla klasy <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, klasy <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> lub klasy pochodnej jednej z tych klas.</span><span class="sxs-lookup"><span data-stu-id="77a3f-121">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
|[<span data-ttu-id="77a3f-122">\<sessionTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="77a3f-122">\<sessionTokenRequirement></span></span>](sessiontokenrequirement.md)|<span data-ttu-id="77a3f-123">Zapewnia konfigurację dla klasy <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> lub klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="77a3f-123">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>|  
|[<span data-ttu-id="77a3f-124">\<userNameSecurityTokenHandlerRequirement ></span><span class="sxs-lookup"><span data-stu-id="77a3f-124">\<userNameSecurityTokenHandlerRequirement></span></span>](usernamesecuritytokenhandlerrequirement.md)|<span data-ttu-id="77a3f-125">Zapewnia konfigurację dla klasy <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> lub klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="77a3f-125">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>|  
|[<span data-ttu-id="77a3f-126">\<x509SecurityTokenHandlerRequirement ></span><span class="sxs-lookup"><span data-stu-id="77a3f-126">\<x509SecurityTokenHandlerRequirement></span></span>](x509securitytokenhandlerrequirement.md)|<span data-ttu-id="77a3f-127">Zapewnia opcjonalną konfigurację dla klasy <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> lub klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="77a3f-127">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="77a3f-128">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="77a3f-128">Parent Elements</span></span>  
  
|<span data-ttu-id="77a3f-129">Element</span><span class="sxs-lookup"><span data-stu-id="77a3f-129">Element</span></span>|<span data-ttu-id="77a3f-130">Opis</span><span class="sxs-lookup"><span data-stu-id="77a3f-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="77a3f-131">\<securityTokenHandler ></span><span class="sxs-lookup"><span data-stu-id="77a3f-131">\<securityTokenHandlers></span></span>](securitytokenhandlers.md)|<span data-ttu-id="77a3f-132">Określa kolekcję programów obsługi tokenów zabezpieczających, które są zarejestrowane w punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="77a3f-132">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="77a3f-133">Uwagi</span><span class="sxs-lookup"><span data-stu-id="77a3f-133">Remarks</span></span>  
 <span data-ttu-id="77a3f-134">Element `<add>` może przyjmować jeden element podrzędny, który określa konfigurację programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="77a3f-134">The `<add>` element can take a single child element that specifies the configuration for the token handler.</span></span> <span data-ttu-id="77a3f-135">Jest to zależne od tego, czy Klasa obsługi, do której odwołuje się atrybut `type` elementu `<add>`, zapewnia obsługę tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="77a3f-135">This is dependent on whether the handler class referenced through the `type` attribute of the `<add>` element provides support for this feature.</span></span> <span data-ttu-id="77a3f-136">Klasy obsługi tokenów, które udostępniają tę funkcję, muszą uwidaczniać konstruktora, który przyjmuje obiekt <xref:System.Xml.XmlElement>.</span><span class="sxs-lookup"><span data-stu-id="77a3f-136">Token handler classes that provide this feature must expose a constructor that takes an <xref:System.Xml.XmlElement> object.</span></span>  

```csharp  
public class CustomTokenHandler : Microsoft.IdentityModel.Tokens.SecurityTokenHandler  
{  
    public CustomTokenHandler( XmlElement customConfig )  
    {  
    }  
}  
```  
  
 <span data-ttu-id="77a3f-137">Niektóre wbudowane klasy procedury obsługi tokenów zabezpieczających zapewniają tę funkcję.</span><span class="sxs-lookup"><span data-stu-id="77a3f-137">Several of the built-in security token handler classes do provide this functionality.</span></span> <span data-ttu-id="77a3f-138">Te klasy to <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>i <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>.</span><span class="sxs-lookup"><span data-stu-id="77a3f-138">These classes are <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, and <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="77a3f-139">Kolekcja obsługi tokenów może zawierać tylko jedną procedurę obsługi dla danego typu.</span><span class="sxs-lookup"><span data-stu-id="77a3f-139">The token handler collection can only contain a single handler of any given type.</span></span> <span data-ttu-id="77a3f-140">Oznacza to, na przykład, że jeśli chcesz dodać program obsługi, który pochodzi od klasy <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> do kolekcji, musisz najpierw usunąć <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, który jest domyślnie obecny, z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="77a3f-140">This means, for example, that if you want to add a handler that is derived from the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class to the collection, you must first remove the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, which is present by default, from the collection.</span></span> <span data-ttu-id="77a3f-141">Można użyć elementu [\<remove >](remove.md) , aby usunąć pojedynczą procedurę obsługi z kolekcji lub użyć elementu [\<Clear >](clear.md) , aby usunąć wszystkie programy obsługi z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="77a3f-141">You can use the [\<remove>](remove.md) element to remove a single handler from the collection or use the [\<clear>](clear.md) element to remove all handlers from the collection.</span></span>  
  
 <span data-ttu-id="77a3f-142">Ustawienia określone w przesłonięciu programu obsługi, które zostały określone w kolekcji obsługi tokenów w elemencie [\<securityTokenHandlerConfiguration >](securitytokenhandlerconfiguration.md) i tych określonych na poziomie usługi w ramach elementu [\<IdentityConfiguration >](identityconfiguration.md) .</span><span class="sxs-lookup"><span data-stu-id="77a3f-142">Settings specified on a handler override equivalent settings specified on the token handler collection under the [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) element and those specified at the service-level under the [\<identityConfiguration>](identityconfiguration.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="77a3f-143">Przykład</span><span class="sxs-lookup"><span data-stu-id="77a3f-143">Example</span></span>  
 <span data-ttu-id="77a3f-144">Poniższy kod XML pokazuje użycie `<add>` i `<remove>` elementów, aby zastąpić domyślną procedurę obsługi tokena sesji za pomocą procedury obsługi niestandardowego tokenu sesji.</span><span class="sxs-lookup"><span data-stu-id="77a3f-144">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="77a3f-145">KOD XML jest pobierany z przykładu `ClaimsAwareWebFarm`.</span><span class="sxs-lookup"><span data-stu-id="77a3f-145">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
