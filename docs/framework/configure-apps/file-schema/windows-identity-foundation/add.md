---
title: <add>
ms.date: 03/30/2017
ms.assetid: 4712a888-f154-4395-8887-ef14a88a6497
author: BrucePerlerMS
ms.openlocfilehash: 34643d10ef1ed2e87152e5013634e62859e0594e
ms.sourcegitcommit: 01ea420eaa4bf76d5fc47673294c8881379b3369
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/06/2019
ms.locfileid: "55759486"
---
# <a name="add"></a><span data-ttu-id="4544f-101">\<add></span><span class="sxs-lookup"><span data-stu-id="4544f-101">\<add></span></span>
<span data-ttu-id="4544f-102">Programu obsługi tokenów zabezpieczeń określone są dodawane do kolekcji programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="4544f-102">Adds the specified security token handler to the token handler collection.</span></span>  
  
 <span data-ttu-id="4544f-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="4544f-103">\<system.identityModel></span></span>  
<span data-ttu-id="4544f-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="4544f-104">\<identityConfiguration></span></span>  
<span data-ttu-id="4544f-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="4544f-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="4544f-106">\<add></span><span class="sxs-lookup"><span data-stu-id="4544f-106">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4544f-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="4544f-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4544f-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4544f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="4544f-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4544f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4544f-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4544f-110">Attributes</span></span>  
  
|<span data-ttu-id="4544f-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4544f-111">Attribute</span></span>|<span data-ttu-id="4544f-112">Opis</span><span class="sxs-lookup"><span data-stu-id="4544f-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4544f-113">— typ</span><span class="sxs-lookup"><span data-stu-id="4544f-113">type</span></span>|<span data-ttu-id="4544f-114">Nazwa typu CLR programu obsługi tokenów do dodania.</span><span class="sxs-lookup"><span data-stu-id="4544f-114">The CLR type name of the token handler to be added.</span></span> <span data-ttu-id="4544f-115">Aby uzyskać więcej informacji o sposobie określania `type` atrybutów, zobacz [odwołań do typu niestandardowego](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span><span class="sxs-lookup"><span data-stu-id="4544f-115">For more information about how to specify the `type` attribute, see [Custom Type References](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4544f-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4544f-116">Child Elements</span></span>  
  
|<span data-ttu-id="4544f-117">Element</span><span class="sxs-lookup"><span data-stu-id="4544f-117">Element</span></span>|<span data-ttu-id="4544f-118">Opis</span><span class="sxs-lookup"><span data-stu-id="4544f-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4544f-119">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="4544f-119">\<samlSecurityTokenRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|<span data-ttu-id="4544f-120">Udostępnia konfigurację dla <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> klasy <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> klasy lub klasy pochodnej z jednego z tych klas.</span><span class="sxs-lookup"><span data-stu-id="4544f-120">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
|[<span data-ttu-id="4544f-121">\<sessionTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="4544f-121">\<sessionTokenRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessiontokenrequirement.md)|<span data-ttu-id="4544f-122">Udostępnia konfigurację dla <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> klasy lub klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="4544f-122">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>|  
|[<span data-ttu-id="4544f-123">\<userNameSecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="4544f-123">\<userNameSecurityTokenHandlerRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/usernamesecuritytokenhandlerrequirement.md)|<span data-ttu-id="4544f-124">Udostępnia konfigurację dla <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> klasy lub klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="4544f-124">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>|  
|[<span data-ttu-id="4544f-125">\<x509SecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="4544f-125">\<x509SecurityTokenHandlerRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/x509securitytokenhandlerrequirement.md)|<span data-ttu-id="4544f-126">Udostępnia konfigurację opcjonalne dla <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> klasy lub klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="4544f-126">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4544f-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4544f-127">Parent Elements</span></span>  
  
|<span data-ttu-id="4544f-128">Element</span><span class="sxs-lookup"><span data-stu-id="4544f-128">Element</span></span>|<span data-ttu-id="4544f-129">Opis</span><span class="sxs-lookup"><span data-stu-id="4544f-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4544f-130">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="4544f-130">\<securityTokenHandlers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|<span data-ttu-id="4544f-131">Określa kolekcję programy obsługi tokenów zabezpieczających, które są zarejestrowane z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="4544f-131">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4544f-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4544f-132">Remarks</span></span>  
 <span data-ttu-id="4544f-133">`<add>` Elementu może potrwać element pojedynczy element podrzędny, który określa konfigurację dla programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="4544f-133">The `<add>` element can take a single child element that specifies the configuration for the token handler.</span></span> <span data-ttu-id="4544f-134">To zależy od tego, czy klasa programu obsługi, do których odwołuje się za pośrednictwem `type` atrybutu `<add>` elementu obsługuje tę funkcję.</span><span class="sxs-lookup"><span data-stu-id="4544f-134">This is dependent on whether the handler class referenced through the `type` attribute of the `<add>` element provides support for this feature.</span></span> <span data-ttu-id="4544f-135">Klasy programu obsługi tokenów, które zapewnia tej funkcji należy ujawnić konstruktora przyjmującego <xref:System.Xml.XmlElement> obiektu.</span><span class="sxs-lookup"><span data-stu-id="4544f-135">Token handler classes that provide this feature must expose a constructor that takes an <xref:System.Xml.XmlElement> object.</span></span>  
  
```  
public class CustomTokenHandler : Microsoft.IdentityModel.Tokens.SecurityTokenHandler  
{  
    public CustomTokenHandler( XmlElement customConfig )  
    {  
    }  
}  
```  
  
 <span data-ttu-id="4544f-136">Niektóre z wbudowanych rozwiązań zabezpieczeń klasy programu obsługi tokenów zapewnienia tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="4544f-136">Several of the built-in security token handler classes do provide this functionality.</span></span> <span data-ttu-id="4544f-137">Te klasy są <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, i <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>.</span><span class="sxs-lookup"><span data-stu-id="4544f-137">These classes are <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, and <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4544f-138">Kolekcja programu obsługi tokenów może zawierać tylko pojedynczy program obsługi każdego typu.</span><span class="sxs-lookup"><span data-stu-id="4544f-138">The token handler collection can only contain a single handler of any given type.</span></span> <span data-ttu-id="4544f-139">Oznacza to, na przykład, że chcesz dodać program obsługi, który jest tworzony na podstawie <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> klasy do kolekcji, należy najpierw usunąć <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, która ma domyślnie z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="4544f-139">This means, for example, that if you want to add a handler that is derived from the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class to the collection, you must first remove the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, which is present by default, from the collection.</span></span> <span data-ttu-id="4544f-140">Możesz użyć [ \<Usuń >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/remove.md) element, aby usunąć pojedynczy program obsługi z kolekcji lub użyj [ \<Wyczyść >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/clear.md) elementu do usunięcia całej obsługi z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="4544f-140">You can use the [\<remove>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/remove.md) element to remove a single handler from the collection or use the [\<clear>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/clear.md) element to remove all handlers from the collection.</span></span>  
  
 <span data-ttu-id="4544f-141">Ustawienia określone na program obsługi zastąpić równoważnym ustawienia określone w kolekcji programu obsługi tokenów w węźle [ \<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) elementu, a określone na poziomie usługi w obszarze [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="4544f-141">Settings specified on a handler override equivalent settings specified on the token handler collection under the [\<securityTokenHandlerConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) element and those specified at the service-level under the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4544f-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="4544f-142">Example</span></span>  
 <span data-ttu-id="4544f-143">Następujący kody XML pokazuje użycie `<add>` i `<remove>` elementów, aby zastąpić domyślne sesji programu obsługi tokenów niestandardową sesję programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="4544f-143">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="4544f-144">Kod XML jest pobierana z `ClaimsAwareWebFarm` próbki.</span><span class="sxs-lookup"><span data-stu-id="4544f-144">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
