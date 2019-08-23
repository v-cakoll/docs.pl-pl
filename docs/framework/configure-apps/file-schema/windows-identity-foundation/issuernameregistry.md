---
title: <issuerNameRegistry>
ms.date: 03/30/2017
ms.assetid: 58b39d12-c953-40c4-88af-d7eb3343ca28
author: BrucePerlerMS
ms.openlocfilehash: d0a1f8dd0c29aaee56c2ca1162cc70cc1e5ed106
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942667"
---
# <a name="issuernameregistry"></a><span data-ttu-id="caa69-101">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="caa69-101">\<issuerNameRegistry></span></span>
<span data-ttu-id="caa69-102">Konfiguruje rejestr nazw wystawców, który jest używany przez programy obsługi w kolekcji obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="caa69-102">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span>  
  
 <span data-ttu-id="caa69-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="caa69-103">\<system.identityModel></span></span>  
<span data-ttu-id="caa69-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="caa69-104">\<identityConfiguration></span></span>  
<span data-ttu-id="caa69-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="caa69-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="caa69-106">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="caa69-106">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="caa69-107">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="caa69-107">\<issuerNameRegistry></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="caa69-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="caa69-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="caa69-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="caa69-109">Attributes and Elements</span></span>  
 <span data-ttu-id="caa69-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="caa69-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="caa69-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="caa69-111">Attributes</span></span>  
  
|<span data-ttu-id="caa69-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="caa69-112">Attribute</span></span>|<span data-ttu-id="caa69-113">Opis</span><span class="sxs-lookup"><span data-stu-id="caa69-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="caa69-114">— typ</span><span class="sxs-lookup"><span data-stu-id="caa69-114">type</span></span>|<span data-ttu-id="caa69-115">Typ, który pochodzi od <xref:System.IdentityModel.Tokens.IssuerNameRegistry> klasy.</span><span class="sxs-lookup"><span data-stu-id="caa69-115">A type that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="caa69-116">Aby uzyskać więcej informacji na temat sposobu określania niestandardowego `type`, zobacz [odwołania do typów niestandardowych].</span><span class="sxs-lookup"><span data-stu-id="caa69-116">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="caa69-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="caa69-117">Child Elements</span></span>  
  
|<span data-ttu-id="caa69-118">Element</span><span class="sxs-lookup"><span data-stu-id="caa69-118">Element</span></span>|<span data-ttu-id="caa69-119">Opis</span><span class="sxs-lookup"><span data-stu-id="caa69-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="caa69-120">\<trustedIssuers ></span><span class="sxs-lookup"><span data-stu-id="caa69-120">\<trustedIssuers></span></span>](trustedissuers.md)|<span data-ttu-id="caa69-121">Gdy atrybut określa rejestr nazw wystawcy oparty na konfiguracji <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> (Klasa), [ \<](trustedissuers.md) należy określić element trustedIssuers >. `type`</span><span class="sxs-lookup"><span data-stu-id="caa69-121">When the `type` attribute specifies the configuration-based issuer name registry (the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class), the [\<trustedIssuers>](trustedissuers.md) element must be specified.</span></span> <span data-ttu-id="caa69-122">`<add>` `<clear>` `<remove>` [ ElementtrustedIssuers\<>](trustedissuers.md) może przyjmować,, lub elementy jako elementy podrzędne.</span><span class="sxs-lookup"><span data-stu-id="caa69-122">The [\<trustedIssuers>](trustedissuers.md) element can take `<add>`, `<clear>`, or `<remove>` elements as child elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="caa69-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="caa69-123">Parent Elements</span></span>  
  
|<span data-ttu-id="caa69-124">Element</span><span class="sxs-lookup"><span data-stu-id="caa69-124">Element</span></span>|<span data-ttu-id="caa69-125">Opis</span><span class="sxs-lookup"><span data-stu-id="caa69-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="caa69-126">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="caa69-126">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="caa69-127">Zapewnia konfigurację kolekcji programów obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="caa69-127">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="caa69-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="caa69-128">Remarks</span></span>  
 <span data-ttu-id="caa69-129">Wszystkie tokeny wystawcy są weryfikowane przy użyciu rejestru nazwy wystawcy.</span><span class="sxs-lookup"><span data-stu-id="caa69-129">All issuer tokens are validated using an issuer name registry.</span></span> <span data-ttu-id="caa69-130">Jest to obiekt, który pochodzi od <xref:System.IdentityModel.Tokens.IssuerNameRegistry> klasy.</span><span class="sxs-lookup"><span data-stu-id="caa69-130">This is an object that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="caa69-131">Rejestr nazwy wystawcy służy do kojarzenia nazwy z materiałem kryptograficznym, który jest niezbędny do zweryfikowania podpisów tokenów wytworzonych przez odpowiedniego wystawcy.</span><span class="sxs-lookup"><span data-stu-id="caa69-131">The issuer name registry is used to associate a mnemonic name to the cryptographic material that is needed to verify the signatures of tokens produced by the corresponding issuer.</span></span> <span data-ttu-id="caa69-132">Nazwa wystawcy Rejestr zawiera listę wystawców, które są zaufane przez aplikację jednostki uzależnionej (RP).</span><span class="sxs-lookup"><span data-stu-id="caa69-132">The issuer name registry maintains a list of issuers that are trusted by the relying party (RP) application.</span></span> <span data-ttu-id="caa69-133">Typ rejestru Nazwa wystawcy jest określany przy użyciu `type` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="caa69-133">The type of the issuer name registry is specified using the `type` attribute.</span></span> <span data-ttu-id="caa69-134">`<issuerNameRegistry>` Element może mieć co najmniej jeden element podrzędny, który zapewnia konfigurację określonego typu.</span><span class="sxs-lookup"><span data-stu-id="caa69-134">The `<issuerNameRegistry>` element can have one or more child elements that provide configuration for the specified type.</span></span> <span data-ttu-id="caa69-135">Należy podać logikę, która przetwarza te elementy podrzędne, zastępując <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> metodę.</span><span class="sxs-lookup"><span data-stu-id="caa69-135">You provide the logic that processes these child elements by overriding the <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> method.</span></span>  
  
 <span data-ttu-id="caa69-136">WIF zawiera typ rejestru o pojedynczej nazwie wystawcy z pola, <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> Klasa.</span><span class="sxs-lookup"><span data-stu-id="caa69-136">WIF provides a single issuer name registry type out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="caa69-137">Ta klasa używa zestawu certyfikatów zaufanych wystawców, które są określone w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="caa69-137">This class uses a set of trusted issuer certificates that are specified in configuration.</span></span> <span data-ttu-id="caa69-138">Wymaga podrzędnego elementu `<trustedIssuers>`konfiguracji, w którym jest skonfigurowana kolekcja certyfikatów zaufanych wystawców.</span><span class="sxs-lookup"><span data-stu-id="caa69-138">It requires a child configuration element, `<trustedIssuers>`, under which the collection of trusted issuer certificates is configured.</span></span> <span data-ttu-id="caa69-139">Certyfikaty zaufane są określane przy użyciu formy z certyfikatem ASN. 1 zaszyfrowanego odcisku palca certyfikatu i są dodawane lub `<add>`usuwane `<clear>`z kolekcji `<remove>` przy użyciu elementów, lub.</span><span class="sxs-lookup"><span data-stu-id="caa69-139">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added or removed from the collection by using `<add>`, `<clear>`, or `<remove>` elements.</span></span>  
  
 <span data-ttu-id="caa69-140">Element jest reprezentowany <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> przez klasę. `<issuerNameRegistry>`</span><span class="sxs-lookup"><span data-stu-id="caa69-140">The `<issuerNameRegistry>` element is represented by the <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="caa69-141">Określanie elementu jako elementu [ \<](identityconfiguration.md) podrzędnego elementu IdentityConfiguration > jest przestarzałe, ale nadal jest on obsługiwany w celu zapewnienia zgodności z poprzednimi wersjami. `<issuerNameRegistry>`</span><span class="sxs-lookup"><span data-stu-id="caa69-141">Specifying the `<issuerNameRegistry>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="caa69-142">Ustawienia w `<securityTokenHandlerConfiguration>` elemencie Przesłoń te elementy `<identityConfiguration>` w elemencie.</span><span class="sxs-lookup"><span data-stu-id="caa69-142">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="caa69-143">Przykład</span><span class="sxs-lookup"><span data-stu-id="caa69-143">Example</span></span>  
 <span data-ttu-id="caa69-144">W poniższym kodzie XML pokazano, jak określić nazwę rejestru wystawcy na podstawie konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="caa69-144">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB … 1EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="caa69-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="caa69-145">See also</span></span>

- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
