---
title: '&lt;issuerNameRegistry&gt;'
ms.date: 03/30/2017
ms.assetid: 58b39d12-c953-40c4-88af-d7eb3343ca28
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: b695cc6d66e5b9e45bb6a5fd22d594bc22ea3cba
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32757531"
---
# <a name="ltissuernameregistrygt"></a><span data-ttu-id="2fa26-102">&lt;issuerNameRegistry&gt;</span><span class="sxs-lookup"><span data-stu-id="2fa26-102">&lt;issuerNameRegistry&gt;</span></span>
<span data-ttu-id="2fa26-103">Konfiguruje rejestru nazwy dostawcy, który jest używany przez programy obsługi zdarzeń w kolekcji programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="2fa26-103">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span>  
  
 <span data-ttu-id="2fa26-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="2fa26-104">\<system.identityModel></span></span>  
<span data-ttu-id="2fa26-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="2fa26-105">\<identityConfiguration></span></span>  
<span data-ttu-id="2fa26-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="2fa26-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="2fa26-107">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="2fa26-107">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="2fa26-108">\<issuerNameRegistry ></span><span class="sxs-lookup"><span data-stu-id="2fa26-108">\<issuerNameRegistry></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fa26-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="2fa26-109">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerNameRegistry type=xs:string>  
          <optionalCustomConfigurationElements />  
        </issuerNameRegistry>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2fa26-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2fa26-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2fa26-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2fa26-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2fa26-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2fa26-112">Attributes</span></span>  
  
|<span data-ttu-id="2fa26-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="2fa26-113">Attribute</span></span>|<span data-ttu-id="2fa26-114">Opis</span><span class="sxs-lookup"><span data-stu-id="2fa26-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2fa26-115">— typ</span><span class="sxs-lookup"><span data-stu-id="2fa26-115">type</span></span>|<span data-ttu-id="2fa26-116">Typ, który pochodzi z <xref:System.IdentityModel.Tokens.IssuerNameRegistry> klasy.</span><span class="sxs-lookup"><span data-stu-id="2fa26-116">A type that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="2fa26-117">Aby uzyskać więcej informacji o sposobie określania niestandardowej `type`, zobacz [odwołania do niestandardowego typu].</span><span class="sxs-lookup"><span data-stu-id="2fa26-117">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2fa26-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2fa26-118">Child Elements</span></span>  
  
|<span data-ttu-id="2fa26-119">Element</span><span class="sxs-lookup"><span data-stu-id="2fa26-119">Element</span></span>|<span data-ttu-id="2fa26-120">Opis</span><span class="sxs-lookup"><span data-stu-id="2fa26-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2fa26-121">\<trustedIssuers ></span><span class="sxs-lookup"><span data-stu-id="2fa26-121">\<trustedIssuers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md)|<span data-ttu-id="2fa26-122">Gdy `type` atrybut określa rejestru nazwy dostawcy oparta na konfiguracji ( <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> klasy), [ \<trustedIssuers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md) musi być określony element.</span><span class="sxs-lookup"><span data-stu-id="2fa26-122">When the `type` attribute specifies the configuration-based issuer name registry (the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class), the [\<trustedIssuers>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md) element must be specified.</span></span> <span data-ttu-id="2fa26-123">[ \<TrustedIssuers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md) elementu można podjąć `<add>`, `<clear>`, lub `<remove>` jako elementy podrzędne.</span><span class="sxs-lookup"><span data-stu-id="2fa26-123">The [\<trustedIssuers>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md) element can take `<add>`, `<clear>`, or `<remove>` elements as child elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2fa26-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2fa26-124">Parent Elements</span></span>  
  
|<span data-ttu-id="2fa26-125">Element</span><span class="sxs-lookup"><span data-stu-id="2fa26-125">Element</span></span>|<span data-ttu-id="2fa26-126">Opis</span><span class="sxs-lookup"><span data-stu-id="2fa26-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2fa26-127">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="2fa26-127">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="2fa26-128">Zapewnia token obsługi konfiguracji dla kolekcji zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="2fa26-128">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2fa26-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2fa26-129">Remarks</span></span>  
 <span data-ttu-id="2fa26-130">Wszystkie tokeny wystawcy są weryfikowane przy użyciu rejestru nazwy dostawcy.</span><span class="sxs-lookup"><span data-stu-id="2fa26-130">All issuer tokens are validated using an issuer name registry.</span></span> <span data-ttu-id="2fa26-131">To jest obiekt pochodzący z <xref:System.IdentityModel.Tokens.IssuerNameRegistry> klasy.</span><span class="sxs-lookup"><span data-stu-id="2fa26-131">This is an object that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="2fa26-132">Rejestru nazwy dostawcy jest używany do kojarzenia nazwy skrótu do materiałów kryptograficznych, potrzebnego do weryfikowania podpisów tokenów utworzonego przez odpowiednie wystawcy.</span><span class="sxs-lookup"><span data-stu-id="2fa26-132">The issuer name registry is used to associate a mnemonic name to the cryptographic material that is needed to verify the signatures of tokens produced by the corresponding issuer.</span></span> <span data-ttu-id="2fa26-133">Rejestru nazwy dostawcy przechowuje listę wystawców, które są zaufane przez aplikację jednostki uzależnionej strony (RP).</span><span class="sxs-lookup"><span data-stu-id="2fa26-133">The issuer name registry maintains a list of issuers that are trusted by the relying party (RP) application.</span></span> <span data-ttu-id="2fa26-134">Typ rejestru nazwy dostawcy jest określona za pomocą `type` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="2fa26-134">The type of the issuer name registry is specified using the `type` attribute.</span></span> <span data-ttu-id="2fa26-135">`<issuerNameRegistry>` Element może mieć elementów podrzędnych, które zapewniają konfiguracji dla określonego typu.</span><span class="sxs-lookup"><span data-stu-id="2fa26-135">The `<issuerNameRegistry>` element can have one or more child elements that provide configuration for the specified type.</span></span> <span data-ttu-id="2fa26-136">Podaj logikę, która przetwarza te elementy podrzędne przez zastąpienie <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="2fa26-136">You provide the logic that processes these child elements by overriding the <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> method.</span></span>  
  
 <span data-ttu-id="2fa26-137">WIF zawiera wystawcy pojedynczy typ rejestru nazwy fabrycznej, <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> klasy.</span><span class="sxs-lookup"><span data-stu-id="2fa26-137">WIF provides a single issuer name registry type out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="2fa26-138">Ta klasa korzysta z zestawu zaufanych wystawców certyfikatów, które są określone w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="2fa26-138">This class uses a set of trusted issuer certificates that are specified in configuration.</span></span> <span data-ttu-id="2fa26-139">Wymaga elementu podrzędnego konfiguracji `<trustedIssuers>`, w obszarze, która jest skonfigurowana w kolekcji certyfikatów zaufanych wystawców.</span><span class="sxs-lookup"><span data-stu-id="2fa26-139">It requires a child configuration element, `<trustedIssuers>`, under which the collection of trusted issuer certificates is configured.</span></span> <span data-ttu-id="2fa26-140">Zaufane certyfikaty są określone za pomocą ASN.1 zakodowane formularza odcisk palca certyfikatu i zostały dodane lub usunięte z kolekcji przy użyciu `<add>`, `<clear>`, lub `<remove>` elementów.</span><span class="sxs-lookup"><span data-stu-id="2fa26-140">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added or removed from the collection by using `<add>`, `<clear>`, or `<remove>` elements.</span></span>  
  
 <span data-ttu-id="2fa26-141">`<issuerNameRegistry>` Reprezentowany przez element <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> klasy.</span><span class="sxs-lookup"><span data-stu-id="2fa26-141">The `<issuerNameRegistry>` element is represented by the <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2fa26-142">Określanie `<issuerNameRegistry>` element jako element podrzędny elementu [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element jest przestarzała, ale nadal jest obsługiwany dla zgodności z poprzednimi wersjami.</span><span class="sxs-lookup"><span data-stu-id="2fa26-142">Specifying the `<issuerNameRegistry>` element as a child element of the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="2fa26-143">Ustawienia na `<securityTokenHandlerConfiguration>` element przesłaniają akcje na `<identityConfiguration>` elementu.</span><span class="sxs-lookup"><span data-stu-id="2fa26-143">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2fa26-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="2fa26-144">Example</span></span>  
 <span data-ttu-id="2fa26-145">Następujący kod XML pokazano, jak określić wystawcę na podstawie konfiguracji rejestru nazwy.</span><span class="sxs-lookup"><span data-stu-id="2fa26-145">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB … 1EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2fa26-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2fa26-146">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.IssuerNameRegistry>  
 <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
