---
title: '&lt;trustedIssuers&gt;'
ms.date: 03/30/2017
ms.assetid: d818c917-07b4-40db-9801-8676561859fd
author: BrucePerlerMS
ms.openlocfilehash: c390cecc265b27dfa8d9d0a892f5930c982f7054
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47206479"
---
# <a name="lttrustedissuersgt"></a><span data-ttu-id="e9c77-102">&lt;trustedIssuers&gt;</span><span class="sxs-lookup"><span data-stu-id="e9c77-102">&lt;trustedIssuers&gt;</span></span>
<span data-ttu-id="e9c77-103">Umożliwia skonfigurowanie listy zaufanych wystawców certyfikatów używane przez rejestru nazwy wystawcy oparta na konfiguracji (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>).</span><span class="sxs-lookup"><span data-stu-id="e9c77-103">Configures the list of trusted issuer certificates used by the configuration-based issuer name registry (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>).</span></span>  
  
 <span data-ttu-id="e9c77-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="e9c77-104">\<system.identityModel></span></span>  
<span data-ttu-id="e9c77-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="e9c77-105">\<identityConfiguration></span></span>  
<span data-ttu-id="e9c77-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="e9c77-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="e9c77-107">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="e9c77-107">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="e9c77-108">\<issuerNameRegistry ></span><span class="sxs-lookup"><span data-stu-id="e9c77-108">\<issuerNameRegistry></span></span>  
<span data-ttu-id="e9c77-109">\<trustedIssuers ></span><span class="sxs-lookup"><span data-stu-id="e9c77-109">\<trustedIssuers></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9c77-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="e9c77-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e9c77-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e9c77-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e9c77-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e9c77-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e9c77-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e9c77-113">Attributes</span></span>  
 <span data-ttu-id="e9c77-114">Brak</span><span class="sxs-lookup"><span data-stu-id="e9c77-114">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e9c77-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e9c77-115">Child Elements</span></span>  
  
|<span data-ttu-id="e9c77-116">Element</span><span class="sxs-lookup"><span data-stu-id="e9c77-116">Element</span></span>|<span data-ttu-id="e9c77-117">Opis</span><span class="sxs-lookup"><span data-stu-id="e9c77-117">Description</span></span>|  
|-------------|-----------------|  
|`<add thumbprint=xs:string name=xs:string>`|<span data-ttu-id="e9c77-118">Dodaje certyfikat do kolekcji zaufanych wystawców.</span><span class="sxs-lookup"><span data-stu-id="e9c77-118">Adds a certificate to the collection of trusted issuers.</span></span> <span data-ttu-id="e9c77-119">Certyfikat jest określony za pomocą `thumbprint` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="e9c77-119">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="e9c77-120">Ten atrybut jest wymagany i może zawierać formularz ASN.1 zakodowane odcisk palca certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="e9c77-120">This attribute is required and should contain the ASN.1 encoded form of the certificate thumbprint.</span></span> <span data-ttu-id="e9c77-121">`name` Atrybut jest opcjonalny i może służyć do Podaj przyjazną nazwę certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="e9c77-121">The `name` attribute is optional and can be used to specify a friendly name for the certificate.</span></span>|  
|`<clear>`|<span data-ttu-id="e9c77-122">Czyści wszystkie certyfikaty z kolekcji zaufanych wystawców.</span><span class="sxs-lookup"><span data-stu-id="e9c77-122">Clears all certificates from the collection of trusted issuers.</span></span>|  
|`<remove thumbprint=xs:string>`|<span data-ttu-id="e9c77-123">Usuwa certyfikat z kolekcji zaufanych wystawców.</span><span class="sxs-lookup"><span data-stu-id="e9c77-123">Removes a certificate from the collection of trusted issuers.</span></span> <span data-ttu-id="e9c77-124">Certyfikat jest określony za pomocą `thumbprint` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="e9c77-124">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="e9c77-125">Ten atrybut jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="e9c77-125">This attribute is required.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e9c77-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e9c77-126">Parent Elements</span></span>  
  
|<span data-ttu-id="e9c77-127">Element</span><span class="sxs-lookup"><span data-stu-id="e9c77-127">Element</span></span>|<span data-ttu-id="e9c77-128">Opis</span><span class="sxs-lookup"><span data-stu-id="e9c77-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e9c77-129">\<issuerNameRegistry ></span><span class="sxs-lookup"><span data-stu-id="e9c77-129">\<issuerNameRegistry></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)|<span data-ttu-id="e9c77-130">Konfiguruje rejestru nazwy wystawcy.</span><span class="sxs-lookup"><span data-stu-id="e9c77-130">Configures the issuer name registry.</span></span> <span data-ttu-id="e9c77-131">**Ważne:** `type` atrybutu `<issuerNameRegistry>` musi odwoływać się do elementu <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> klasy dla `<trustedIssuers>` element był prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="e9c77-131">**Important:**  The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9c77-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e9c77-132">Remarks</span></span>  
 <span data-ttu-id="e9c77-133">Windows Identity Foundation (WIF) udostępnia pojedynczą implementacją <xref:System.IdentityModel.Tokens.IssuerNameRegistry> klasy gotowych, <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> klasy.</span><span class="sxs-lookup"><span data-stu-id="e9c77-133">Windows Identity Foundation (WIF) provides a single implementation of the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="e9c77-134">Rejestru nazwy wystawcy konfiguracji utrzymuje listę zaufanych wystawców, który jest ładowany z konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e9c77-134">The configuration issuer name registry maintains a list of trusted issuers that is loaded from configuration.</span></span> <span data-ttu-id="e9c77-135">Lista kojarzy nazwy wystawcy przy użyciu certyfikatu X.509, który jest potrzebny do weryfikowania podpisu produkowane przez wystawcy tokenów.</span><span class="sxs-lookup"><span data-stu-id="e9c77-135">The list associates each issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by the issuer.</span></span> <span data-ttu-id="e9c77-136">Lista zaufanych wystawców certyfikatów jest określony w sekcji `<trustedIssuers>` elementu.</span><span class="sxs-lookup"><span data-stu-id="e9c77-136">The list of trusted issuer certificates is specified under the `<trustedIssuers>` element.</span></span> <span data-ttu-id="e9c77-137">Każdy element na liście kojarzy nazwę wystawcy mnemoników przy użyciu certyfikatu X.509, które są potrzebne do zweryfikowania podpisu generowane przez ten wystawcy tokenów.</span><span class="sxs-lookup"><span data-stu-id="e9c77-137">Each element in the list associates a mnemonic issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by that issuer.</span></span> <span data-ttu-id="e9c77-138">Zaufane certyfikaty są określane przy użyciu ASN.1 zakodowane w postaci odcisku palca certyfikatu i są dodawane kolekcji przy użyciu `<add>` elementu.</span><span class="sxs-lookup"><span data-stu-id="e9c77-138">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added the collection by using `<add>` element.</span></span> <span data-ttu-id="e9c77-139">Możesz wyczyścić, lub usunąć wystawców (certyfikatów) z listy przy użyciu `<clear>` i `<remove>` elementów.</span><span class="sxs-lookup"><span data-stu-id="e9c77-139">You can clear or remove issuers (certificates) from the list by using the `<clear>` and `<remove>` elements.</span></span>  
  
 <span data-ttu-id="e9c77-140">`type` Atrybutu `<issuerNameRegistry>` musi odwoływać się do elementu <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> klasy dla `<trustedIssuers>` element był prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="e9c77-140">The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9c77-141">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9c77-141">Example</span></span>  
 <span data-ttu-id="e9c77-142">Następujący kod XML pokazuje sposób określania wystawcy konfiguracji na podstawie nazwy rejestru.</span><span class="sxs-lookup"><span data-stu-id="e9c77-142">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB2F32 … B1DC01EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e9c77-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9c77-143">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>  
 <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
