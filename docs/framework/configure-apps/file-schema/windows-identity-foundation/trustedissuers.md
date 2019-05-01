---
title: <trustedIssuers>
ms.date: 03/30/2017
ms.assetid: d818c917-07b4-40db-9801-8676561859fd
author: BrucePerlerMS
ms.openlocfilehash: cebfc2f3598f32f233db6039dfe82076d2ffce46
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790484"
---
# <a name="trustedissuers"></a><span data-ttu-id="84c96-101">\<trustedIssuers></span><span class="sxs-lookup"><span data-stu-id="84c96-101">\<trustedIssuers></span></span>
<span data-ttu-id="84c96-102">Umożliwia skonfigurowanie listy zaufanych wystawców certyfikatów używane przez rejestru nazwy wystawcy oparta na konfiguracji (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>).</span><span class="sxs-lookup"><span data-stu-id="84c96-102">Configures the list of trusted issuer certificates used by the configuration-based issuer name registry (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>).</span></span>  
  
 <span data-ttu-id="84c96-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="84c96-103">\<system.identityModel></span></span>  
<span data-ttu-id="84c96-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="84c96-104">\<identityConfiguration></span></span>  
<span data-ttu-id="84c96-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="84c96-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="84c96-106">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="84c96-106">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="84c96-107">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="84c96-107">\<issuerNameRegistry></span></span>  
<span data-ttu-id="84c96-108">\<trustedIssuers></span><span class="sxs-lookup"><span data-stu-id="84c96-108">\<trustedIssuers></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84c96-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="84c96-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="84c96-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="84c96-110">Attributes and Elements</span></span>  
 <span data-ttu-id="84c96-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="84c96-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="84c96-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="84c96-112">Attributes</span></span>  
 <span data-ttu-id="84c96-113">Brak</span><span class="sxs-lookup"><span data-stu-id="84c96-113">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="84c96-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="84c96-114">Child Elements</span></span>  
  
|<span data-ttu-id="84c96-115">Element</span><span class="sxs-lookup"><span data-stu-id="84c96-115">Element</span></span>|<span data-ttu-id="84c96-116">Opis</span><span class="sxs-lookup"><span data-stu-id="84c96-116">Description</span></span>|  
|-------------|-----------------|  
|`<add thumbprint=xs:string name=xs:string>`|<span data-ttu-id="84c96-117">Dodaje certyfikat do kolekcji zaufanych wystawców.</span><span class="sxs-lookup"><span data-stu-id="84c96-117">Adds a certificate to the collection of trusted issuers.</span></span> <span data-ttu-id="84c96-118">Certyfikat jest określony za pomocą `thumbprint` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="84c96-118">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="84c96-119">Ten atrybut jest wymagany i może zawierać formularz ASN.1 zakodowane odcisk palca certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="84c96-119">This attribute is required and should contain the ASN.1 encoded form of the certificate thumbprint.</span></span> <span data-ttu-id="84c96-120">`name` Atrybut jest opcjonalny i może służyć do Podaj przyjazną nazwę certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="84c96-120">The `name` attribute is optional and can be used to specify a friendly name for the certificate.</span></span>|  
|`<clear>`|<span data-ttu-id="84c96-121">Czyści wszystkie certyfikaty z kolekcji zaufanych wystawców.</span><span class="sxs-lookup"><span data-stu-id="84c96-121">Clears all certificates from the collection of trusted issuers.</span></span>|  
|`<remove thumbprint=xs:string>`|<span data-ttu-id="84c96-122">Usuwa certyfikat z kolekcji zaufanych wystawców.</span><span class="sxs-lookup"><span data-stu-id="84c96-122">Removes a certificate from the collection of trusted issuers.</span></span> <span data-ttu-id="84c96-123">Certyfikat jest określony za pomocą `thumbprint` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="84c96-123">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="84c96-124">Ten atrybut jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="84c96-124">This attribute is required.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="84c96-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="84c96-125">Parent Elements</span></span>  
  
|<span data-ttu-id="84c96-126">Element</span><span class="sxs-lookup"><span data-stu-id="84c96-126">Element</span></span>|<span data-ttu-id="84c96-127">Opis</span><span class="sxs-lookup"><span data-stu-id="84c96-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="84c96-128">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="84c96-128">\<issuerNameRegistry></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)|<span data-ttu-id="84c96-129">Konfiguruje rejestru nazwy wystawcy.</span><span class="sxs-lookup"><span data-stu-id="84c96-129">Configures the issuer name registry.</span></span> <span data-ttu-id="84c96-130">**Ważne:**  `type` Atrybutu `<issuerNameRegistry>` musi odwoływać się do elementu <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> klasy dla `<trustedIssuers>` element był prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="84c96-130">**Important:**  The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="84c96-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="84c96-131">Remarks</span></span>  
 <span data-ttu-id="84c96-132">Windows Identity Foundation (WIF) udostępnia pojedynczą implementacją <xref:System.IdentityModel.Tokens.IssuerNameRegistry> klasy gotowych, <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> klasy.</span><span class="sxs-lookup"><span data-stu-id="84c96-132">Windows Identity Foundation (WIF) provides a single implementation of the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="84c96-133">Rejestru nazwy wystawcy konfiguracji utrzymuje listę zaufanych wystawców, który jest ładowany z konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="84c96-133">The configuration issuer name registry maintains a list of trusted issuers that is loaded from configuration.</span></span> <span data-ttu-id="84c96-134">Lista kojarzy nazwy wystawcy przy użyciu certyfikatu X.509, który jest potrzebny do weryfikowania podpisu produkowane przez wystawcy tokenów.</span><span class="sxs-lookup"><span data-stu-id="84c96-134">The list associates each issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by the issuer.</span></span> <span data-ttu-id="84c96-135">Lista zaufanych wystawców certyfikatów jest określony w sekcji `<trustedIssuers>` elementu.</span><span class="sxs-lookup"><span data-stu-id="84c96-135">The list of trusted issuer certificates is specified under the `<trustedIssuers>` element.</span></span> <span data-ttu-id="84c96-136">Każdy element na liście kojarzy nazwę wystawcy mnemoników przy użyciu certyfikatu X.509, które są potrzebne do zweryfikowania podpisu generowane przez ten wystawcy tokenów.</span><span class="sxs-lookup"><span data-stu-id="84c96-136">Each element in the list associates a mnemonic issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by that issuer.</span></span> <span data-ttu-id="84c96-137">Zaufane certyfikaty są określane przy użyciu ASN.1 zakodowane w postaci odcisku palca certyfikatu i są dodawane kolekcji przy użyciu `<add>` elementu.</span><span class="sxs-lookup"><span data-stu-id="84c96-137">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added the collection by using `<add>` element.</span></span> <span data-ttu-id="84c96-138">Możesz wyczyścić, lub usunąć wystawców (certyfikatów) z listy przy użyciu `<clear>` i `<remove>` elementów.</span><span class="sxs-lookup"><span data-stu-id="84c96-138">You can clear or remove issuers (certificates) from the list by using the `<clear>` and `<remove>` elements.</span></span>  
  
 <span data-ttu-id="84c96-139">`type` Atrybutu `<issuerNameRegistry>` musi odwoływać się do elementu <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> klasy dla `<trustedIssuers>` element był prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="84c96-139">The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>  
  
## <a name="example"></a><span data-ttu-id="84c96-140">Przykład</span><span class="sxs-lookup"><span data-stu-id="84c96-140">Example</span></span>  
 <span data-ttu-id="84c96-141">Następujący kod XML pokazuje sposób określania wystawcy konfiguracji na podstawie nazwy rejestru.</span><span class="sxs-lookup"><span data-stu-id="84c96-141">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB2F32 … B1DC01EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="84c96-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="84c96-142">See also</span></span>

- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
