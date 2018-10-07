---
title: '&lt;add&gt;'
ms.date: 03/30/2017
ms.assetid: 4712a888-f154-4395-8887-ef14a88a6497
author: BrucePerlerMS
ms.openlocfilehash: 4cd86a858223997ed379d2b26518e14f6d3ebb3e
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2018
ms.locfileid: "48845362"
---
# <a name="ltaddgt"></a><span data-ttu-id="f99d7-102">&lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="f99d7-102">&lt;add&gt;</span></span>
<span data-ttu-id="f99d7-103">Programu obsługi tokenów zabezpieczeń określone są dodawane do kolekcji programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="f99d7-103">Adds the specified security token handler to the token handler collection.</span></span>  
  
 <span data-ttu-id="f99d7-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="f99d7-104">\<system.identityModel></span></span>  
<span data-ttu-id="f99d7-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="f99d7-105">\<identityConfiguration></span></span>  
<span data-ttu-id="f99d7-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="f99d7-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="f99d7-107">\<add></span><span class="sxs-lookup"><span data-stu-id="f99d7-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f99d7-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="f99d7-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f99d7-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f99d7-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f99d7-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f99d7-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f99d7-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f99d7-111">Attributes</span></span>  
  
|<span data-ttu-id="f99d7-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f99d7-112">Attribute</span></span>|<span data-ttu-id="f99d7-113">Opis</span><span class="sxs-lookup"><span data-stu-id="f99d7-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f99d7-114">— typ</span><span class="sxs-lookup"><span data-stu-id="f99d7-114">type</span></span>|<span data-ttu-id="f99d7-115">Nazwa typu CLR programu obsługi tokenów do dodania.</span><span class="sxs-lookup"><span data-stu-id="f99d7-115">The CLR type name of the token handler to be added.</span></span> <span data-ttu-id="f99d7-116">Aby uzyskać więcej informacji o sposobie określania `type` atrybutów, zobacz [odwołań do typu niestandardowego](https://msdn.microsoft.com/library/7286d2e3-c63d-49fd-abdc-ce2705f22c24).</span><span class="sxs-lookup"><span data-stu-id="f99d7-116">For more information about how to specify the `type` attribute, see [Custom Type References](https://msdn.microsoft.com/library/7286d2e3-c63d-49fd-abdc-ce2705f22c24).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f99d7-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f99d7-117">Child Elements</span></span>  
  
|<span data-ttu-id="f99d7-118">Element</span><span class="sxs-lookup"><span data-stu-id="f99d7-118">Element</span></span>|<span data-ttu-id="f99d7-119">Opis</span><span class="sxs-lookup"><span data-stu-id="f99d7-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f99d7-120">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="f99d7-120">\<samlSecurityTokenRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|<span data-ttu-id="f99d7-121">Udostępnia konfigurację dla <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> klasy <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> klasy lub klasy pochodnej z jednego z tych klas.</span><span class="sxs-lookup"><span data-stu-id="f99d7-121">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
|[<span data-ttu-id="f99d7-122">\<sessionTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="f99d7-122">\<sessionTokenRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessiontokenrequirement.md)|<span data-ttu-id="f99d7-123">Udostępnia konfigurację dla <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> klasy lub klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="f99d7-123">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>|  
|[<span data-ttu-id="f99d7-124">\<userNameSecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="f99d7-124">\<userNameSecurityTokenHandlerRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/usernamesecuritytokenhandlerrequirement.md)|<span data-ttu-id="f99d7-125">Udostępnia konfigurację dla <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> klasy lub klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="f99d7-125">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>|  
|[<span data-ttu-id="f99d7-126">\<x509SecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="f99d7-126">\<x509SecurityTokenHandlerRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/x509securitytokenhandlerrequirement.md)|<span data-ttu-id="f99d7-127">Udostępnia konfigurację opcjonalne dla <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> klasy lub klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="f99d7-127">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f99d7-128">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f99d7-128">Parent Elements</span></span>  
  
|<span data-ttu-id="f99d7-129">Element</span><span class="sxs-lookup"><span data-stu-id="f99d7-129">Element</span></span>|<span data-ttu-id="f99d7-130">Opis</span><span class="sxs-lookup"><span data-stu-id="f99d7-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f99d7-131">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="f99d7-131">\<securityTokenHandlers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|<span data-ttu-id="f99d7-132">Określa kolekcję programy obsługi tokenów zabezpieczających, które są zarejestrowane z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="f99d7-132">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f99d7-133">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f99d7-133">Remarks</span></span>  
 <span data-ttu-id="f99d7-134">`<add>` Elementu może potrwać element pojedynczy element podrzędny, który określa konfigurację dla programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="f99d7-134">The `<add>` element can take a single child element that specifies the configuration for the token handler.</span></span> <span data-ttu-id="f99d7-135">To zależy od tego, czy klasa programu obsługi, do których odwołuje się za pośrednictwem `type` atrybutu `<add>` elementu obsługuje tę funkcję.</span><span class="sxs-lookup"><span data-stu-id="f99d7-135">This is dependent on whether the handler class referenced through the `type` attribute of the `<add>` element provides support for this feature.</span></span> <span data-ttu-id="f99d7-136">Klasy programu obsługi tokenów, które zapewnia tej funkcji należy ujawnić konstruktora przyjmującego <xref:System.Xml.XmlElement> obiektu.</span><span class="sxs-lookup"><span data-stu-id="f99d7-136">Token handler classes that provide this feature must expose a constructor that takes an <xref:System.Xml.XmlElement> object.</span></span>  
  
```  
public class CustomTokenHandler : Microsoft.IdentityModel.Tokens.SecurityTokenHandler  
{  
    public CustomTokenHandler( XmlElement customConfig )  
    {  
    }  
}  
```  
  
 <span data-ttu-id="f99d7-137">Niektóre z wbudowanych rozwiązań zabezpieczeń klasy programu obsługi tokenów zapewnienia tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="f99d7-137">Several of the built-in security token handler classes do provide this functionality.</span></span> <span data-ttu-id="f99d7-138">Te klasy są <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, i <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>.</span><span class="sxs-lookup"><span data-stu-id="f99d7-138">These classes are <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, and <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f99d7-139">Kolekcja programu obsługi tokenów może zawierać tylko pojedynczy program obsługi każdego typu.</span><span class="sxs-lookup"><span data-stu-id="f99d7-139">The token handler collection can only contain a single handler of any given type.</span></span> <span data-ttu-id="f99d7-140">Oznacza to, na przykład, że chcesz dodać program obsługi, który jest tworzony na podstawie <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> klasy do kolekcji, należy najpierw usunąć <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, która ma domyślnie z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="f99d7-140">This means, for example, that if you want to add a handler that is derived from the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class to the collection, you must first remove the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, which is present by default, from the collection.</span></span> <span data-ttu-id="f99d7-141">Możesz użyć [ \<Usuń >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/remove.md) element, aby usunąć pojedynczy program obsługi z kolekcji lub użyj [ \<Wyczyść >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/clear.md) elementu do usunięcia całej obsługi z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="f99d7-141">You can use the [\<remove>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/remove.md) element to remove a single handler from the collection or use the [\<clear>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/clear.md) element to remove all handlers from the collection.</span></span>  
  
 <span data-ttu-id="f99d7-142">Ustawienia określone na program obsługi zastąpić równoważnym ustawienia określone w kolekcji programu obsługi tokenów w węźle [ \<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) elementu, a określone na poziomie usługi w obszarze [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="f99d7-142">Settings specified on a handler override equivalent settings specified on the token handler collection under the [\<securityTokenHandlerConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) element and those specified at the service-level under the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f99d7-143">Przykład</span><span class="sxs-lookup"><span data-stu-id="f99d7-143">Example</span></span>  
 <span data-ttu-id="f99d7-144">Następujący kody XML pokazuje użycie `<add>` i `<remove>` elementów, aby zastąpić domyślne sesji programu obsługi tokenów niestandardową sesję programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="f99d7-144">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="f99d7-145">Kod XML jest pobierana z `ClaimsAwareWebFarm` próbki.</span><span class="sxs-lookup"><span data-stu-id="f99d7-145">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
