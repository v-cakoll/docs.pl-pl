---
title: '&lt;add&gt;'
ms.date: 03/30/2017
ms.assetid: 4712a888-f154-4395-8887-ef14a88a6497
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 6ee6403fcfe741d3e38bf44eddb1cf52cf856ec8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32757856"
---
# <a name="ltaddgt"></a><span data-ttu-id="24542-102">&lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="24542-102">&lt;add&gt;</span></span>
<span data-ttu-id="24542-103">Dodaje określony zabezpieczenia programu obsługi tokenów do kolekcji programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="24542-103">Adds the specified security token handler to the token handler collection.</span></span>  
  
 <span data-ttu-id="24542-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="24542-104">\<system.identityModel></span></span>  
<span data-ttu-id="24542-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="24542-105">\<identityConfiguration></span></span>  
<span data-ttu-id="24542-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="24542-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="24542-107">\<add></span><span class="sxs-lookup"><span data-stu-id="24542-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24542-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="24542-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="24542-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="24542-109">Attributes and Elements</span></span>  
 <span data-ttu-id="24542-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="24542-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="24542-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="24542-111">Attributes</span></span>  
  
|<span data-ttu-id="24542-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="24542-112">Attribute</span></span>|<span data-ttu-id="24542-113">Opis</span><span class="sxs-lookup"><span data-stu-id="24542-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="24542-114">— typ</span><span class="sxs-lookup"><span data-stu-id="24542-114">type</span></span>|<span data-ttu-id="24542-115">Nazwa typu CLR programu obsługi tokenów do dodania.</span><span class="sxs-lookup"><span data-stu-id="24542-115">The CLR type name of the token handler to be added.</span></span> <span data-ttu-id="24542-116">Aby uzyskać więcej informacji o sposobie określania `type` atrybutów, zobacz [odwołuje się do niestandardowego typu](http://msdn.microsoft.com/library/7286d2e3-c63d-49fd-abdc-ce2705f22c24).</span><span class="sxs-lookup"><span data-stu-id="24542-116">For more information about how to specify the `type` attribute, see [Custom Type References](http://msdn.microsoft.com/library/7286d2e3-c63d-49fd-abdc-ce2705f22c24).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="24542-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="24542-117">Child Elements</span></span>  
  
|<span data-ttu-id="24542-118">Element</span><span class="sxs-lookup"><span data-stu-id="24542-118">Element</span></span>|<span data-ttu-id="24542-119">Opis</span><span class="sxs-lookup"><span data-stu-id="24542-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="24542-120">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="24542-120">\<samlSecurityTokenRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|<span data-ttu-id="24542-121">Zapewnia konfigurację <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> klasy <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> klasy lub klasy pochodnej każdej z tych klas.</span><span class="sxs-lookup"><span data-stu-id="24542-121">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
|[<span data-ttu-id="24542-122">\<sessionTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="24542-122">\<sessionTokenRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessiontokenrequirement.md)|<span data-ttu-id="24542-123">Zapewnia konfigurację <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> klasy lub klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="24542-123">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>|  
|[<span data-ttu-id="24542-124">\<userNameSecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="24542-124">\<userNameSecurityTokenHandlerRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/usernamesecuritytokenhandlerrequirement.md)|<span data-ttu-id="24542-125">Zapewnia konfigurację <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> klasy lub klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="24542-125">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>|  
|[<span data-ttu-id="24542-126">\<x509SecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="24542-126">\<x509SecurityTokenHandlerRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/x509securitytokenhandlerrequirement.md)|<span data-ttu-id="24542-127">Zapewnia opcjonalne konfigurację <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> klasy lub klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="24542-127">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="24542-128">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="24542-128">Parent Elements</span></span>  
  
|<span data-ttu-id="24542-129">Element</span><span class="sxs-lookup"><span data-stu-id="24542-129">Element</span></span>|<span data-ttu-id="24542-130">Opis</span><span class="sxs-lookup"><span data-stu-id="24542-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="24542-131">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="24542-131">\<securityTokenHandlers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|<span data-ttu-id="24542-132">Określa kolekcję programów obsługi tokenu zabezpieczeń, które są zarejestrowane z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="24542-132">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="24542-133">Uwagi</span><span class="sxs-lookup"><span data-stu-id="24542-133">Remarks</span></span>  
 <span data-ttu-id="24542-134">`<add>` Elementu można podjąć element pojedynczy element potomny, który określa konfigurację programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="24542-134">The `<add>` element can take a single child element that specifies the configuration for the token handler.</span></span> <span data-ttu-id="24542-135">Jest to zależne od tego, czy klasa obsługi, do których odwołuje się za pośrednictwem `type` atrybutu `<add>` element zapewnia obsługę dla tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="24542-135">This is dependent on whether the handler class referenced through the `type` attribute of the `<add>` element provides support for this feature.</span></span> <span data-ttu-id="24542-136">Klasy programu obsługi tokenów, które zapewniają ta funkcja musi ujawniać Konstruktor, który pobiera <xref:System.Xml.XmlElement> obiektu.</span><span class="sxs-lookup"><span data-stu-id="24542-136">Token handler classes that provide this feature must expose a constructor that takes an <xref:System.Xml.XmlElement> object.</span></span>  
  
```  
public class CustomTokenHandler : Microsoft.IdentityModel.Tokens.SecurityTokenHandler  
{  
    public CustomTokenHandler( XmlElement customConfig )  
    {  
    }  
}  
```  
  
 <span data-ttu-id="24542-137">Kilka klas programu obsługi tokenów zabezpieczeń zapewnienia tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="24542-137">Several of the built-in security token handler classes do provide this functionality.</span></span> <span data-ttu-id="24542-138">Te klasy są <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, i <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>.</span><span class="sxs-lookup"><span data-stu-id="24542-138">These classes are <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, and <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="24542-139">Kolekcja programu obsługi tokenów może zawierać tylko jeden program obsługi każdego typu.</span><span class="sxs-lookup"><span data-stu-id="24542-139">The token handler collection can only contain a single handler of any given type.</span></span> <span data-ttu-id="24542-140">Oznacza to, na przykład, że jeśli chcesz dodać obsługi, która jest pochodną <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> klasy do kolekcji, należy najpierw usunąć <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, który ma domyślnie z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="24542-140">This means, for example, that if you want to add a handler that is derived from the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class to the collection, you must first remove the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, which is present by default, from the collection.</span></span> <span data-ttu-id="24542-141">Można użyć [ \<Usuń >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/remove.md) elementu do usunięcia z kolekcji lub użyj pojedynczego obsługi [ \<Wyczyść >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/clear.md) elementu do usunięcia wszystkich programów obsługi z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="24542-141">You can use the [\<remove>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/remove.md) element to remove a single handler from the collection or use the [\<clear>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/clear.md) element to remove all handlers from the collection.</span></span>  
  
 <span data-ttu-id="24542-142">Ustawienia określone na program obsługi zastąpić równoważnym ustawień określonych w kolekcji programu obsługi tokenów [ \<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) elementu i określone na poziomie usługi w obszarze [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="24542-142">Settings specified on a handler override equivalent settings specified on the token handler collection under the [\<securityTokenHandlerConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) element and those specified at the service-level under the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24542-143">Przykład</span><span class="sxs-lookup"><span data-stu-id="24542-143">Example</span></span>  
 <span data-ttu-id="24542-144">Następujący kod XML pokazano sposób użycia `<add>` i `<remove>` elementy, aby zastąpić domyślny sesji programu obsługi tokenów niestandardową sesję programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="24542-144">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="24542-145">Kod XML jest pobierana z `ClaimsAwareWebFarm` próbki.</span><span class="sxs-lookup"><span data-stu-id="24542-145">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
