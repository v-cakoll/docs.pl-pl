---
title: <issuerNameRegistry>
ms.date: 03/30/2017
ms.assetid: 58b39d12-c953-40c4-88af-d7eb3343ca28
author: BrucePerlerMS
ms.openlocfilehash: db4e0492772d6fd0e155843422b7350aa630f713
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57369685"
---
# <a name="issuernameregistry"></a><span data-ttu-id="f57a4-101">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="f57a4-101">\<issuerNameRegistry></span></span>
<span data-ttu-id="f57a4-102">Konfiguruje rejestru nazwy wystawcy, który jest używany przez programy obsługi w kolekcji programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="f57a4-102">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span>  
  
 <span data-ttu-id="f57a4-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="f57a4-103">\<system.identityModel></span></span>  
<span data-ttu-id="f57a4-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="f57a4-104">\<identityConfiguration></span></span>  
<span data-ttu-id="f57a4-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="f57a4-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="f57a4-106">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="f57a4-106">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="f57a4-107">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="f57a4-107">\<issuerNameRegistry></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f57a4-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="f57a4-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f57a4-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f57a4-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f57a4-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f57a4-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f57a4-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f57a4-111">Attributes</span></span>  
  
|<span data-ttu-id="f57a4-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f57a4-112">Attribute</span></span>|<span data-ttu-id="f57a4-113">Opis</span><span class="sxs-lookup"><span data-stu-id="f57a4-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f57a4-114"> — typ</span><span class="sxs-lookup"><span data-stu-id="f57a4-114">type</span></span>|<span data-ttu-id="f57a4-115">Typ, który pochodzi od klasy <xref:System.IdentityModel.Tokens.IssuerNameRegistry> klasy.</span><span class="sxs-lookup"><span data-stu-id="f57a4-115">A type that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="f57a4-116">Aby uzyskać więcej informacji o sposobie określania niestandardowej `type`, zobacz [odwołań do niestandardowego typu].</span><span class="sxs-lookup"><span data-stu-id="f57a4-116">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f57a4-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f57a4-117">Child Elements</span></span>  
  
|<span data-ttu-id="f57a4-118">Element</span><span class="sxs-lookup"><span data-stu-id="f57a4-118">Element</span></span>|<span data-ttu-id="f57a4-119">Opis</span><span class="sxs-lookup"><span data-stu-id="f57a4-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f57a4-120">\<trustedIssuers></span><span class="sxs-lookup"><span data-stu-id="f57a4-120">\<trustedIssuers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md)|<span data-ttu-id="f57a4-121">Gdy `type` atrybut określa rejestru nazwy wystawcy oparta na konfiguracji ( <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> klasy), [ \<trustedIssuers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md) element musi być określona.</span><span class="sxs-lookup"><span data-stu-id="f57a4-121">When the `type` attribute specifies the configuration-based issuer name registry (the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class), the [\<trustedIssuers>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md) element must be specified.</span></span> <span data-ttu-id="f57a4-122">[ \<TrustedIssuers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md) elementu może potrwać `<add>`, `<clear>`, lub `<remove>` jako elementy podrzędne.</span><span class="sxs-lookup"><span data-stu-id="f57a4-122">The [\<trustedIssuers>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md) element can take `<add>`, `<clear>`, or `<remove>` elements as child elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f57a4-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f57a4-123">Parent Elements</span></span>  
  
|<span data-ttu-id="f57a4-124">Element</span><span class="sxs-lookup"><span data-stu-id="f57a4-124">Element</span></span>|<span data-ttu-id="f57a4-125">Opis</span><span class="sxs-lookup"><span data-stu-id="f57a4-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f57a4-126">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="f57a4-126">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="f57a4-127">Udostępnia konfigurację dla kolekcji zabezpieczeń programy obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="f57a4-127">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f57a4-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f57a4-128">Remarks</span></span>  
 <span data-ttu-id="f57a4-129">Wszystkie tokeny wystawcy są weryfikowane za pomocą rejestru nazwy wystawcy.</span><span class="sxs-lookup"><span data-stu-id="f57a4-129">All issuer tokens are validated using an issuer name registry.</span></span> <span data-ttu-id="f57a4-130">Jest to obiekt, który pochodzi od klasy <xref:System.IdentityModel.Tokens.IssuerNameRegistry> klasy.</span><span class="sxs-lookup"><span data-stu-id="f57a4-130">This is an object that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="f57a4-131">Rejestru nazwy wystawcy jest używany do kojarzenia mnemoników nazwy do materiałami kryptograficznymi, potrzebnego do weryfikowania podpisów tokenów produkowane przez odpowiednie wystawcy.</span><span class="sxs-lookup"><span data-stu-id="f57a4-131">The issuer name registry is used to associate a mnemonic name to the cryptographic material that is needed to verify the signatures of tokens produced by the corresponding issuer.</span></span> <span data-ttu-id="f57a4-132">Rejestru nazwy wystawcy utrzymuje listę wystawców, które są zaufane przez aplikację jednostki uzależnionej (RP).</span><span class="sxs-lookup"><span data-stu-id="f57a4-132">The issuer name registry maintains a list of issuers that are trusted by the relying party (RP) application.</span></span> <span data-ttu-id="f57a4-133">Typ rejestru nazwy wystawcy jest określony, przy użyciu `type` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="f57a4-133">The type of the issuer name registry is specified using the `type` attribute.</span></span> <span data-ttu-id="f57a4-134">`<issuerNameRegistry>` Element może mieć elementów podrzędnych, które zapewniają konfiguracji dla określonego typu.</span><span class="sxs-lookup"><span data-stu-id="f57a4-134">The `<issuerNameRegistry>` element can have one or more child elements that provide configuration for the specified type.</span></span> <span data-ttu-id="f57a4-135">Zapewnić logikę, która przetwarza te elementy podrzędne, zastępowanie <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f57a4-135">You provide the logic that processes these child elements by overriding the <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> method.</span></span>  
  
 <span data-ttu-id="f57a4-136">Program WIF oferuje wystawcy pojedynczy typ rejestru nazwy gotowych, <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> klasy.</span><span class="sxs-lookup"><span data-stu-id="f57a4-136">WIF provides a single issuer name registry type out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="f57a4-137">Ta klasa używa zestawu zaufanych wystawców certyfikatów, które są określone w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f57a4-137">This class uses a set of trusted issuer certificates that are specified in configuration.</span></span> <span data-ttu-id="f57a4-138">Wymaga elementu podrzędnego konfiguracji `<trustedIssuers>`, pod którym kolekcji certyfikatów zaufanych wystawców jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="f57a4-138">It requires a child configuration element, `<trustedIssuers>`, under which the collection of trusted issuer certificates is configured.</span></span> <span data-ttu-id="f57a4-139">Zaufane certyfikaty są określone za pomocą ASN.1 zakodowane w postaci odcisku palca certyfikatu i są dodawane lub usuwane z kolekcji przy użyciu `<add>`, `<clear>`, lub `<remove>` elementów.</span><span class="sxs-lookup"><span data-stu-id="f57a4-139">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added or removed from the collection by using `<add>`, `<clear>`, or `<remove>` elements.</span></span>  
  
 <span data-ttu-id="f57a4-140">`<issuerNameRegistry>` Element jest reprezentowany przez <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> klasy.</span><span class="sxs-lookup"><span data-stu-id="f57a4-140">The `<issuerNameRegistry>` element is represented by the <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f57a4-141">Określanie `<issuerNameRegistry>` element jako element podrzędny [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elementu jest przestarzałe, ale nadal jest obsługiwany dla zgodności z poprzednimi wersjami.</span><span class="sxs-lookup"><span data-stu-id="f57a4-141">Specifying the `<issuerNameRegistry>` element as a child element of the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="f57a4-142">Ustawienia na `<securityTokenHandlerConfiguration>` elemencie przesłaniają akcje na `<identityConfiguration>` elementu.</span><span class="sxs-lookup"><span data-stu-id="f57a4-142">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f57a4-143">Przykład</span><span class="sxs-lookup"><span data-stu-id="f57a4-143">Example</span></span>  
 <span data-ttu-id="f57a4-144">Następujący kod XML pokazuje sposób określania wystawcy konfiguracji na podstawie nazwy rejestru.</span><span class="sxs-lookup"><span data-stu-id="f57a4-144">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB … 1EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f57a4-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f57a4-145">See also</span></span>
- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
