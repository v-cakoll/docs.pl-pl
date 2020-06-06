---
title: <trustedIssuers>
ms.date: 03/30/2017
ms.assetid: d818c917-07b4-40db-9801-8676561859fd
author: BrucePerlerMS
ms.openlocfilehash: 50fc7194823fb0c5c426fb54ffd50b17c3714ed9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251760"
---
# \<trustedIssuers>
<span data-ttu-id="808b5-101">Konfiguruje listę certyfikatów zaufanych wystawców używanych przez rejestr nazw wystawcy oparty na konfiguracji ( <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> ).</span><span class="sxs-lookup"><span data-stu-id="808b5-101">Configures the list of trusted issuer certificates used by the configuration-based issuer name registry (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuerNameRegistry>**](issuernameregistry.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<trustedIssuers>**  
  
## <a name="syntax"></a><span data-ttu-id="808b5-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="808b5-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="808b5-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="808b5-103">Attributes and Elements</span></span>  
 <span data-ttu-id="808b5-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="808b5-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="808b5-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="808b5-105">Attributes</span></span>  
 <span data-ttu-id="808b5-106">Brak</span><span class="sxs-lookup"><span data-stu-id="808b5-106">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="808b5-107">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="808b5-107">Child Elements</span></span>  
  
|<span data-ttu-id="808b5-108">Element</span><span class="sxs-lookup"><span data-stu-id="808b5-108">Element</span></span>|<span data-ttu-id="808b5-109">Opis</span><span class="sxs-lookup"><span data-stu-id="808b5-109">Description</span></span>|  
|-------------|-----------------|  
|`<add thumbprint=xs:string name=xs:string>`|<span data-ttu-id="808b5-110">Dodaje certyfikat do kolekcji zaufanych wystawców.</span><span class="sxs-lookup"><span data-stu-id="808b5-110">Adds a certificate to the collection of trusted issuers.</span></span> <span data-ttu-id="808b5-111">Certyfikat jest określony przy użyciu `thumbprint` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="808b5-111">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="808b5-112">Ten atrybut jest wymagany i powinien zawierać postać zaszyfrowanego numeru ASN. 1 odcisku palca certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="808b5-112">This attribute is required and should contain the ASN.1 encoded form of the certificate thumbprint.</span></span> <span data-ttu-id="808b5-113">`name`Atrybut jest opcjonalny i może służyć do określenia przyjaznej nazwy certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="808b5-113">The `name` attribute is optional and can be used to specify a friendly name for the certificate.</span></span>|  
|`<clear>`|<span data-ttu-id="808b5-114">Czyści wszystkie certyfikaty z kolekcji zaufanych wystawców.</span><span class="sxs-lookup"><span data-stu-id="808b5-114">Clears all certificates from the collection of trusted issuers.</span></span>|  
|`<remove thumbprint=xs:string>`|<span data-ttu-id="808b5-115">Usuwa certyfikat z kolekcji zaufanych wystawców.</span><span class="sxs-lookup"><span data-stu-id="808b5-115">Removes a certificate from the collection of trusted issuers.</span></span> <span data-ttu-id="808b5-116">Certyfikat jest określony przy użyciu `thumbprint` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="808b5-116">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="808b5-117">Ten atrybut jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="808b5-117">This attribute is required.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="808b5-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="808b5-118">Parent Elements</span></span>  
  
|<span data-ttu-id="808b5-119">Element</span><span class="sxs-lookup"><span data-stu-id="808b5-119">Element</span></span>|<span data-ttu-id="808b5-120">Opis</span><span class="sxs-lookup"><span data-stu-id="808b5-120">Description</span></span>|  
|-------------|-----------------|  
|[\<issuerNameRegistry>](issuernameregistry.md)|<span data-ttu-id="808b5-121">Konfiguruje rejestr nazwy wystawcy.</span><span class="sxs-lookup"><span data-stu-id="808b5-121">Configures the issuer name registry.</span></span> <span data-ttu-id="808b5-122">**Ważne:**  `type`Atrybut `<issuerNameRegistry>` elementu musi odwoływać się do <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> klasy, aby `<trustedIssuers>` element był prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="808b5-122">**Important:**  The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="808b5-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="808b5-123">Remarks</span></span>  
 <span data-ttu-id="808b5-124">Program Windows Identity Foundation (WIF) udostępnia jedną implementację <xref:System.IdentityModel.Tokens.IssuerNameRegistry> klasy z pola, <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> klasy.</span><span class="sxs-lookup"><span data-stu-id="808b5-124">Windows Identity Foundation (WIF) provides a single implementation of the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="808b5-125">Nazwa wystawcy konfiguracji rejestru przechowuje listę zaufanych wystawców, które są ładowane z konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="808b5-125">The configuration issuer name registry maintains a list of trusted issuers that is loaded from configuration.</span></span> <span data-ttu-id="808b5-126">Lista kojarzy nazwy poszczególnych wystawców z certyfikatem X. 509, który jest wymagany do zweryfikowania podpisu tokenów wygenerowanych przez wystawcę.</span><span class="sxs-lookup"><span data-stu-id="808b5-126">The list associates each issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by the issuer.</span></span> <span data-ttu-id="808b5-127">Lista zaufanych certyfikatów wystawcy jest określona w `<trustedIssuers>` elemencie.</span><span class="sxs-lookup"><span data-stu-id="808b5-127">The list of trusted issuer certificates is specified under the `<trustedIssuers>` element.</span></span> <span data-ttu-id="808b5-128">Każdy element na liście kojarzy nazwę wystawcy z certyfikatem X. 509, który jest niezbędny do zweryfikowania sygnatury tokenów wytworzonych przez tego wystawcy.</span><span class="sxs-lookup"><span data-stu-id="808b5-128">Each element in the list associates a mnemonic issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by that issuer.</span></span> <span data-ttu-id="808b5-129">Certyfikaty zaufane są określane przy użyciu formy z certyfikatem ASN. 1 i są dodawane do kolekcji za pomocą `<add>` elementu.</span><span class="sxs-lookup"><span data-stu-id="808b5-129">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added the collection by using `<add>` element.</span></span> <span data-ttu-id="808b5-130">Wystawcy (certyfikaty) można wyczyścić lub usunąć z listy za pomocą `<clear>` `<remove>` elementów i.</span><span class="sxs-lookup"><span data-stu-id="808b5-130">You can clear or remove issuers (certificates) from the list by using the `<clear>` and `<remove>` elements.</span></span>  
  
 <span data-ttu-id="808b5-131">`type`Atrybut `<issuerNameRegistry>` elementu musi odwoływać się do <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> klasy, aby `<trustedIssuers>` element był prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="808b5-131">The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>  
  
## <a name="example"></a><span data-ttu-id="808b5-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="808b5-132">Example</span></span>  
 <span data-ttu-id="808b5-133">W poniższym kodzie XML pokazano, jak określić nazwę rejestru wystawcy na podstawie konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="808b5-133">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB2F32 … B1DC01EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="808b5-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="808b5-134">See also</span></span>

- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
