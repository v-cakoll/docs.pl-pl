---
title: <trustedIssuers>
ms.date: 03/30/2017
ms.assetid: d818c917-07b4-40db-9801-8676561859fd
author: BrucePerlerMS
ms.openlocfilehash: 50fc7194823fb0c5c426fb54ffd50b17c3714ed9
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251760"
---
# <a name="trustedissuers"></a><span data-ttu-id="50d1a-101">\<trustedIssuers ></span><span class="sxs-lookup"><span data-stu-id="50d1a-101">\<trustedIssuers></span></span>
<span data-ttu-id="50d1a-102">Konfiguruje listę certyfikatów zaufanych wystawców używanych przez rejestr nazw wystawcy oparty na konfiguracji<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>().</span><span class="sxs-lookup"><span data-stu-id="50d1a-102">Configures the list of trusted issuer certificates used by the configuration-based issuer name registry (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>).</span></span>  
  
<span data-ttu-id="50d1a-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="50d1a-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="50d1a-104">&nbsp;&nbsp;[ **\<> System. identityModel**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="50d1a-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="50d1a-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="50d1a-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="50d1a-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> obiektów securityTokenHandler**](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="50d1a-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="50d1a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlerConfiguration >** ](securitytokenhandlerconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="50d1a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)</span></span>\
<span data-ttu-id="50d1a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<issuerNameRegistry >** ](issuernameregistry.md)</span><span class="sxs-lookup"><span data-stu-id="50d1a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuerNameRegistry>**](issuernameregistry.md)</span></span>\
<span data-ttu-id="50d1a-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<trustedIssuers >**</span><span class="sxs-lookup"><span data-stu-id="50d1a-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<trustedIssuers>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50d1a-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="50d1a-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="50d1a-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="50d1a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="50d1a-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="50d1a-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="50d1a-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="50d1a-113">Attributes</span></span>  
 <span data-ttu-id="50d1a-114">Brak</span><span class="sxs-lookup"><span data-stu-id="50d1a-114">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="50d1a-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="50d1a-115">Child Elements</span></span>  
  
|<span data-ttu-id="50d1a-116">Element</span><span class="sxs-lookup"><span data-stu-id="50d1a-116">Element</span></span>|<span data-ttu-id="50d1a-117">Opis</span><span class="sxs-lookup"><span data-stu-id="50d1a-117">Description</span></span>|  
|-------------|-----------------|  
|`<add thumbprint=xs:string name=xs:string>`|<span data-ttu-id="50d1a-118">Dodaje certyfikat do kolekcji zaufanych wystawców.</span><span class="sxs-lookup"><span data-stu-id="50d1a-118">Adds a certificate to the collection of trusted issuers.</span></span> <span data-ttu-id="50d1a-119">Certyfikat jest określony przy użyciu `thumbprint` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="50d1a-119">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="50d1a-120">Ten atrybut jest wymagany i powinien zawierać postać zaszyfrowanego numeru ASN. 1 odcisku palca certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="50d1a-120">This attribute is required and should contain the ASN.1 encoded form of the certificate thumbprint.</span></span> <span data-ttu-id="50d1a-121">`name` Atrybut jest opcjonalny i może służyć do określenia przyjaznej nazwy certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="50d1a-121">The `name` attribute is optional and can be used to specify a friendly name for the certificate.</span></span>|  
|`<clear>`|<span data-ttu-id="50d1a-122">Czyści wszystkie certyfikaty z kolekcji zaufanych wystawców.</span><span class="sxs-lookup"><span data-stu-id="50d1a-122">Clears all certificates from the collection of trusted issuers.</span></span>|  
|`<remove thumbprint=xs:string>`|<span data-ttu-id="50d1a-123">Usuwa certyfikat z kolekcji zaufanych wystawców.</span><span class="sxs-lookup"><span data-stu-id="50d1a-123">Removes a certificate from the collection of trusted issuers.</span></span> <span data-ttu-id="50d1a-124">Certyfikat jest określony przy użyciu `thumbprint` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="50d1a-124">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="50d1a-125">Ten atrybut jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="50d1a-125">This attribute is required.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="50d1a-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="50d1a-126">Parent Elements</span></span>  
  
|<span data-ttu-id="50d1a-127">Element</span><span class="sxs-lookup"><span data-stu-id="50d1a-127">Element</span></span>|<span data-ttu-id="50d1a-128">Opis</span><span class="sxs-lookup"><span data-stu-id="50d1a-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="50d1a-129">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="50d1a-129">\<issuerNameRegistry></span></span>](issuernameregistry.md)|<span data-ttu-id="50d1a-130">Konfiguruje rejestr nazwy wystawcy.</span><span class="sxs-lookup"><span data-stu-id="50d1a-130">Configures the issuer name registry.</span></span> <span data-ttu-id="50d1a-131">**Ważne:**  Atrybut elementu musi odwoływać się <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> do klasy, `<trustedIssuers>` aby element był prawidłowy. `<issuerNameRegistry>` `type`</span><span class="sxs-lookup"><span data-stu-id="50d1a-131">**Important:**  The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50d1a-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="50d1a-132">Remarks</span></span>  
 <span data-ttu-id="50d1a-133">Program Windows Identity Foundation (WIF) udostępnia jedną implementację <xref:System.IdentityModel.Tokens.IssuerNameRegistry> klasy z pola, klasy.<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="50d1a-133">Windows Identity Foundation (WIF) provides a single implementation of the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="50d1a-134">Nazwa wystawcy konfiguracji rejestru przechowuje listę zaufanych wystawców, które są ładowane z konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="50d1a-134">The configuration issuer name registry maintains a list of trusted issuers that is loaded from configuration.</span></span> <span data-ttu-id="50d1a-135">Lista kojarzy nazwy poszczególnych wystawców z certyfikatem X. 509, który jest wymagany do zweryfikowania podpisu tokenów wygenerowanych przez wystawcę.</span><span class="sxs-lookup"><span data-stu-id="50d1a-135">The list associates each issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by the issuer.</span></span> <span data-ttu-id="50d1a-136">Lista zaufanych certyfikatów wystawcy jest określona w `<trustedIssuers>` elemencie.</span><span class="sxs-lookup"><span data-stu-id="50d1a-136">The list of trusted issuer certificates is specified under the `<trustedIssuers>` element.</span></span> <span data-ttu-id="50d1a-137">Każdy element na liście kojarzy nazwę wystawcy z certyfikatem X. 509, który jest niezbędny do zweryfikowania sygnatury tokenów wytworzonych przez tego wystawcy.</span><span class="sxs-lookup"><span data-stu-id="50d1a-137">Each element in the list associates a mnemonic issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by that issuer.</span></span> <span data-ttu-id="50d1a-138">Certyfikaty zaufane są określane przy użyciu formy z certyfikatem ASN. 1 i są dodawane do kolekcji `<add>` za pomocą elementu.</span><span class="sxs-lookup"><span data-stu-id="50d1a-138">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added the collection by using `<add>` element.</span></span> <span data-ttu-id="50d1a-139">Wystawcy (certyfikaty) można wyczyścić lub usunąć z listy za pomocą `<clear>` elementów i. `<remove>`</span><span class="sxs-lookup"><span data-stu-id="50d1a-139">You can clear or remove issuers (certificates) from the list by using the `<clear>` and `<remove>` elements.</span></span>  
  
 <span data-ttu-id="50d1a-140">Atrybut elementu musi odwoływać się <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> do klasy, `<trustedIssuers>` aby element był prawidłowy. `<issuerNameRegistry>` `type`</span><span class="sxs-lookup"><span data-stu-id="50d1a-140">The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>  
  
## <a name="example"></a><span data-ttu-id="50d1a-141">Przykład</span><span class="sxs-lookup"><span data-stu-id="50d1a-141">Example</span></span>  
 <span data-ttu-id="50d1a-142">W poniższym kodzie XML pokazano, jak określić nazwę rejestru wystawcy na podstawie konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="50d1a-142">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB2F32 … B1DC01EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="50d1a-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="50d1a-143">See also</span></span>

- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
