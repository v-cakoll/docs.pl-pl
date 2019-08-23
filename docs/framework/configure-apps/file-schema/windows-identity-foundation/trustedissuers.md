---
title: <trustedIssuers>
ms.date: 03/30/2017
ms.assetid: d818c917-07b4-40db-9801-8676561859fd
author: BrucePerlerMS
ms.openlocfilehash: 32aad3529ded6d0234b1bcb388ecbbc3b0a11c87
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944272"
---
# <a name="trustedissuers"></a><span data-ttu-id="ecf1f-101">\<trustedIssuers ></span><span class="sxs-lookup"><span data-stu-id="ecf1f-101">\<trustedIssuers></span></span>
<span data-ttu-id="ecf1f-102">Konfiguruje listę certyfikatów zaufanych wystawców używanych przez rejestr nazw wystawcy oparty na konfiguracji<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>().</span><span class="sxs-lookup"><span data-stu-id="ecf1f-102">Configures the list of trusted issuer certificates used by the configuration-based issuer name registry (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>).</span></span>  
  
 <span data-ttu-id="ecf1f-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="ecf1f-103">\<system.identityModel></span></span>  
<span data-ttu-id="ecf1f-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="ecf1f-104">\<identityConfiguration></span></span>  
<span data-ttu-id="ecf1f-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="ecf1f-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="ecf1f-106">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="ecf1f-106">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="ecf1f-107">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="ecf1f-107">\<issuerNameRegistry></span></span>  
<span data-ttu-id="ecf1f-108">\<trustedIssuers ></span><span class="sxs-lookup"><span data-stu-id="ecf1f-108">\<trustedIssuers></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecf1f-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="ecf1f-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ecf1f-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ecf1f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ecf1f-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ecf1f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ecf1f-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ecf1f-112">Attributes</span></span>  
 <span data-ttu-id="ecf1f-113">Brak</span><span class="sxs-lookup"><span data-stu-id="ecf1f-113">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ecf1f-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ecf1f-114">Child Elements</span></span>  
  
|<span data-ttu-id="ecf1f-115">Element</span><span class="sxs-lookup"><span data-stu-id="ecf1f-115">Element</span></span>|<span data-ttu-id="ecf1f-116">Opis</span><span class="sxs-lookup"><span data-stu-id="ecf1f-116">Description</span></span>|  
|-------------|-----------------|  
|`<add thumbprint=xs:string name=xs:string>`|<span data-ttu-id="ecf1f-117">Dodaje certyfikat do kolekcji zaufanych wystawców.</span><span class="sxs-lookup"><span data-stu-id="ecf1f-117">Adds a certificate to the collection of trusted issuers.</span></span> <span data-ttu-id="ecf1f-118">Certyfikat jest określony przy użyciu `thumbprint` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="ecf1f-118">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="ecf1f-119">Ten atrybut jest wymagany i powinien zawierać postać zaszyfrowanego numeru ASN. 1 odcisku palca certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="ecf1f-119">This attribute is required and should contain the ASN.1 encoded form of the certificate thumbprint.</span></span> <span data-ttu-id="ecf1f-120">`name` Atrybut jest opcjonalny i może służyć do określenia przyjaznej nazwy certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="ecf1f-120">The `name` attribute is optional and can be used to specify a friendly name for the certificate.</span></span>|  
|`<clear>`|<span data-ttu-id="ecf1f-121">Czyści wszystkie certyfikaty z kolekcji zaufanych wystawców.</span><span class="sxs-lookup"><span data-stu-id="ecf1f-121">Clears all certificates from the collection of trusted issuers.</span></span>|  
|`<remove thumbprint=xs:string>`|<span data-ttu-id="ecf1f-122">Usuwa certyfikat z kolekcji zaufanych wystawców.</span><span class="sxs-lookup"><span data-stu-id="ecf1f-122">Removes a certificate from the collection of trusted issuers.</span></span> <span data-ttu-id="ecf1f-123">Certyfikat jest określony przy użyciu `thumbprint` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="ecf1f-123">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="ecf1f-124">Ten atrybut jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="ecf1f-124">This attribute is required.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ecf1f-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ecf1f-125">Parent Elements</span></span>  
  
|<span data-ttu-id="ecf1f-126">Element</span><span class="sxs-lookup"><span data-stu-id="ecf1f-126">Element</span></span>|<span data-ttu-id="ecf1f-127">Opis</span><span class="sxs-lookup"><span data-stu-id="ecf1f-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ecf1f-128">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="ecf1f-128">\<issuerNameRegistry></span></span>](issuernameregistry.md)|<span data-ttu-id="ecf1f-129">Konfiguruje rejestr nazwy wystawcy.</span><span class="sxs-lookup"><span data-stu-id="ecf1f-129">Configures the issuer name registry.</span></span> <span data-ttu-id="ecf1f-130">**Ważne:**  Atrybut elementu musi odwoływać się <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> do klasy, `<trustedIssuers>` aby element był prawidłowy. `<issuerNameRegistry>` `type`</span><span class="sxs-lookup"><span data-stu-id="ecf1f-130">**Important:**  The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ecf1f-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ecf1f-131">Remarks</span></span>  
 <span data-ttu-id="ecf1f-132">Program Windows Identity Foundation (WIF) udostępnia jedną implementację <xref:System.IdentityModel.Tokens.IssuerNameRegistry> klasy z pola, klasy.<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="ecf1f-132">Windows Identity Foundation (WIF) provides a single implementation of the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="ecf1f-133">Nazwa wystawcy konfiguracji rejestru przechowuje listę zaufanych wystawców, które są ładowane z konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ecf1f-133">The configuration issuer name registry maintains a list of trusted issuers that is loaded from configuration.</span></span> <span data-ttu-id="ecf1f-134">Lista kojarzy nazwy poszczególnych wystawców z certyfikatem X. 509, który jest wymagany do zweryfikowania podpisu tokenów wygenerowanych przez wystawcę.</span><span class="sxs-lookup"><span data-stu-id="ecf1f-134">The list associates each issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by the issuer.</span></span> <span data-ttu-id="ecf1f-135">Lista zaufanych certyfikatów wystawcy jest określona w `<trustedIssuers>` elemencie.</span><span class="sxs-lookup"><span data-stu-id="ecf1f-135">The list of trusted issuer certificates is specified under the `<trustedIssuers>` element.</span></span> <span data-ttu-id="ecf1f-136">Każdy element na liście kojarzy nazwę wystawcy z certyfikatem X. 509, który jest niezbędny do zweryfikowania sygnatury tokenów wytworzonych przez tego wystawcy.</span><span class="sxs-lookup"><span data-stu-id="ecf1f-136">Each element in the list associates a mnemonic issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by that issuer.</span></span> <span data-ttu-id="ecf1f-137">Certyfikaty zaufane są określane przy użyciu formy z certyfikatem ASN. 1 i są dodawane do kolekcji `<add>` za pomocą elementu.</span><span class="sxs-lookup"><span data-stu-id="ecf1f-137">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added the collection by using `<add>` element.</span></span> <span data-ttu-id="ecf1f-138">Wystawcy (certyfikaty) można wyczyścić lub usunąć z listy za pomocą `<clear>` elementów i. `<remove>`</span><span class="sxs-lookup"><span data-stu-id="ecf1f-138">You can clear or remove issuers (certificates) from the list by using the `<clear>` and `<remove>` elements.</span></span>  
  
 <span data-ttu-id="ecf1f-139">Atrybut elementu musi odwoływać się <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> do klasy, `<trustedIssuers>` aby element był prawidłowy. `<issuerNameRegistry>` `type`</span><span class="sxs-lookup"><span data-stu-id="ecf1f-139">The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ecf1f-140">Przykład</span><span class="sxs-lookup"><span data-stu-id="ecf1f-140">Example</span></span>  
 <span data-ttu-id="ecf1f-141">W poniższym kodzie XML pokazano, jak określić nazwę rejestru wystawcy na podstawie konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ecf1f-141">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB2F32 … B1DC01EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ecf1f-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ecf1f-142">See also</span></span>

- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
