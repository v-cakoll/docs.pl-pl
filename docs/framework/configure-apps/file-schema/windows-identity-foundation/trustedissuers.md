---
title: '&lt;trustedIssuers&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d818c917-07b4-40db-9801-8676561859fd
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 33ef3ca88462595d81d269a92a643b43c9aea025
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="lttrustedissuersgt"></a><span data-ttu-id="11571-102">&lt;trustedIssuers&gt;</span><span class="sxs-lookup"><span data-stu-id="11571-102">&lt;trustedIssuers&gt;</span></span>
<span data-ttu-id="11571-103">Umożliwia skonfigurowanie listy zaufanych wystawców certyfikatów używanych przez wystawców na podstawie konfiguracji rejestru nazwy (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>).</span><span class="sxs-lookup"><span data-stu-id="11571-103">Configures the list of trusted issuer certificates used by the configuration-based issuer name registry (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>).</span></span>  
  
 <span data-ttu-id="11571-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="11571-104">\<system.identityModel></span></span>  
<span data-ttu-id="11571-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="11571-105">\<identityConfiguration></span></span>  
<span data-ttu-id="11571-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="11571-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="11571-107">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="11571-107">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="11571-108">\<issuerNameRegistry ></span><span class="sxs-lookup"><span data-stu-id="11571-108">\<issuerNameRegistry></span></span>  
<span data-ttu-id="11571-109">\<trustedIssuers ></span><span class="sxs-lookup"><span data-stu-id="11571-109">\<trustedIssuers></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11571-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="11571-110">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerNameRegistry>  
          <trustedIssuers>  
            <add thumbprint=xs:string name=xs:string>  
            <clear>  
            <remove thumbprint=xs:string>  
          </trustedIssuers>  
        </issuerNameRegistry>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="11571-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="11571-111">Attributes and Elements</span></span>  
 <span data-ttu-id="11571-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="11571-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="11571-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="11571-113">Attributes</span></span>  
 <span data-ttu-id="11571-114">Brak</span><span class="sxs-lookup"><span data-stu-id="11571-114">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="11571-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="11571-115">Child Elements</span></span>  
  
|<span data-ttu-id="11571-116">Element</span><span class="sxs-lookup"><span data-stu-id="11571-116">Element</span></span>|<span data-ttu-id="11571-117">Opis</span><span class="sxs-lookup"><span data-stu-id="11571-117">Description</span></span>|  
|-------------|-----------------|  
|`<add thumbprint=xs:string name=xs:string>`|<span data-ttu-id="11571-118">Dodaje certyfikat do kolekcji zaufanych wystawców.</span><span class="sxs-lookup"><span data-stu-id="11571-118">Adds a certificate to the collection of trusted issuers.</span></span> <span data-ttu-id="11571-119">Certyfikat zostanie określony z `thumbprint` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="11571-119">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="11571-120">Ten atrybut jest wymagany i musi zawierać formularza kodowane ASN.1 odcisk palca certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="11571-120">This attribute is required and should contain the ASN.1 encoded form of the certificate thumbprint.</span></span> <span data-ttu-id="11571-121">`name` Atrybutu jest opcjonalny i może służyć do Określ przyjazną nazwę certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="11571-121">The `name` attribute is optional and can be used to specify a friendly name for the certificate.</span></span>|  
|`<clear>`|<span data-ttu-id="11571-122">Usuwa wszystkie certyfikaty z kolekcji zaufanych wystawców.</span><span class="sxs-lookup"><span data-stu-id="11571-122">Clears all certificates from the collection of trusted issuers.</span></span>|  
|`<remove thumbprint=xs:string>`|<span data-ttu-id="11571-123">Usuwa certyfikat z kolekcji zaufanych wystawców.</span><span class="sxs-lookup"><span data-stu-id="11571-123">Removes a certificate from the collection of trusted issuers.</span></span> <span data-ttu-id="11571-124">Certyfikat zostanie określony z `thumbprint` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="11571-124">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="11571-125">Ten atrybut jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="11571-125">This attribute is required.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="11571-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="11571-126">Parent Elements</span></span>  
  
|<span data-ttu-id="11571-127">Element</span><span class="sxs-lookup"><span data-stu-id="11571-127">Element</span></span>|<span data-ttu-id="11571-128">Opis</span><span class="sxs-lookup"><span data-stu-id="11571-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="11571-129">\<issuerNameRegistry ></span><span class="sxs-lookup"><span data-stu-id="11571-129">\<issuerNameRegistry></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)|<span data-ttu-id="11571-130">Konfiguruje rejestru nazwy dostawcy.</span><span class="sxs-lookup"><span data-stu-id="11571-130">Configures the issuer name registry.</span></span> <span data-ttu-id="11571-131">**Ważne:** `type` atrybutu `<issuerNameRegistry>` element musi odwoływać się <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> klasy dla `<trustedIssuers>` elementu jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="11571-131">**Important:**  The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="11571-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="11571-132">Remarks</span></span>  
 <span data-ttu-id="11571-133">Windows Identity Foundation (WIF) zawiera pojedynczą implementacją właściwości <xref:System.IdentityModel.Tokens.IssuerNameRegistry> klasy fabrycznej, <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> klasy.</span><span class="sxs-lookup"><span data-stu-id="11571-133">Windows Identity Foundation (WIF) provides a single implementation of the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="11571-134">Rejestru nazwy dostawcy konfiguracji przechowuje listę zaufanych wystawców, które są ładowane z konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="11571-134">The configuration issuer name registry maintains a list of trusted issuers that is loaded from configuration.</span></span> <span data-ttu-id="11571-135">Listy kojarzy nazwy wystawcy z certyfikatu X.509, który jest potrzebne do zweryfikowania podpisu utworzonego przez wystawcy tokenów.</span><span class="sxs-lookup"><span data-stu-id="11571-135">The list associates each issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by the issuer.</span></span> <span data-ttu-id="11571-136">Lista zaufanych wystawców certyfikatów jest określony w `<trustedIssuers>` elementu.</span><span class="sxs-lookup"><span data-stu-id="11571-136">The list of trusted issuer certificates is specified under the `<trustedIssuers>` element.</span></span> <span data-ttu-id="11571-137">Każdy element na liście kojarzy nazwę skrótu wystawcy z certyfikatu X.509, który jest potrzebny do zweryfikowania podpisu utworzone przez tego wystawcy tokenów.</span><span class="sxs-lookup"><span data-stu-id="11571-137">Each element in the list associates a mnemonic issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by that issuer.</span></span> <span data-ttu-id="11571-138">Zaufane certyfikaty są określone za pomocą ASN.1 zakodowane formularza odcisk palca certyfikatu i są dodawane kolekcji przy użyciu `<add>` elementu.</span><span class="sxs-lookup"><span data-stu-id="11571-138">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added the collection by using `<add>` element.</span></span> <span data-ttu-id="11571-139">Możesz wyczyścić lub Usuń z listy wystawców (certyfikatów), za pomocą `<clear>` i `<remove>` elementy.</span><span class="sxs-lookup"><span data-stu-id="11571-139">You can clear or remove issuers (certificates) from the list by using the `<clear>` and `<remove>` elements.</span></span>  
  
 <span data-ttu-id="11571-140">`type` Atrybutu `<issuerNameRegistry>` element musi odwoływać się <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> klasy dla `<trustedIssuers>` elementu jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="11571-140">The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11571-141">Przykład</span><span class="sxs-lookup"><span data-stu-id="11571-141">Example</span></span>  
 <span data-ttu-id="11571-142">Następujący kod XML pokazano, jak określić wystawcę na podstawie konfiguracji rejestru nazwy.</span><span class="sxs-lookup"><span data-stu-id="11571-142">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB2F32 … B1DC01EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="11571-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="11571-143">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>  
 <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
