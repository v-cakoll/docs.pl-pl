---
title: <samlSecurityTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 09202d12-88d3-49cc-953b-703bcc1690eb
author: BrucePerlerMS
ms.openlocfilehash: cab7572518a7a6dc26f8bbcf67cd424fa1c01085
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251902"
---
# <a name="samlsecuritytokenrequirement"></a><span data-ttu-id="2c5ee-101">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="2c5ee-101">\<samlSecurityTokenRequirement></span></span>
<span data-ttu-id="2c5ee-102">Zapewnia konfigurację <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> klasy <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> , klasy lub klasy pochodnej jednej z tych klas.</span><span class="sxs-lookup"><span data-stu-id="2c5ee-102">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span> <span data-ttu-id="2c5ee-103">Reprezentowane przez <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> klasę.</span><span class="sxs-lookup"><span data-stu-id="2c5ee-103">Represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class.</span></span>  
  
<span data-ttu-id="2c5ee-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2c5ee-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2c5ee-105">&nbsp;&nbsp;[ **\<> System. identityModel**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="2c5ee-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="2c5ee-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="2c5ee-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="2c5ee-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> obiektów securityTokenHandler**](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="2c5ee-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="2c5ee-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Dodaj >** ](add.md)</span><span class="sxs-lookup"><span data-stu-id="2c5ee-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)</span></span>\
<span data-ttu-id="2c5ee-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<samlSecurityTokenRequirement >**</span><span class="sxs-lookup"><span data-stu-id="2c5ee-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<samlSecurityTokenRequirement>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c5ee-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="2c5ee-110">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add>  
        <samlSecurityTokenRequirement   
            issuerCertificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
            issuerCertificateRevocationMode="NoCheck||Offline||Online"  
            issuerCertificateTrustedStoreLocation="CurrentLocation||LocalMachine"  
            issuerCertificateValidator="Namespace.Class Assembly"  
            mapToWindows=xs:boolean  
          <nameClaimType value=xs:string />  
          <roleClaimType value=xs:string />  
        </samlSecurityTokenRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2c5ee-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2c5ee-111">Attributes and Elements</span></span>  
 <span data-ttu-id="2c5ee-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2c5ee-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2c5ee-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2c5ee-113">Attributes</span></span>  
  
|<span data-ttu-id="2c5ee-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="2c5ee-114">Attribute</span></span>|<span data-ttu-id="2c5ee-115">Opis</span><span class="sxs-lookup"><span data-stu-id="2c5ee-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2c5ee-116">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="2c5ee-116">mapToWindows</span></span>|<span data-ttu-id="2c5ee-117">Określa, czy program obsługi tokenów powinien mapować token walidacji na konto systemu Windows przy użyciu przychodzącego oświadczenie nazwy UPN.</span><span class="sxs-lookup"><span data-stu-id="2c5ee-117">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="2c5ee-118">Wartość domyślna to "false".</span><span class="sxs-lookup"><span data-stu-id="2c5ee-118">The default is "false".</span></span>|  
|<span data-ttu-id="2c5ee-119">issuerCertificateRevocationMode</span><span class="sxs-lookup"><span data-stu-id="2c5ee-119">issuerCertificateRevocationMode</span></span>|<span data-ttu-id="2c5ee-120"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> Wartość określająca tryb odwołania, który ma być używany dla certyfikatu X. 509.</span><span class="sxs-lookup"><span data-stu-id="2c5ee-120">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="2c5ee-121">Wartość domyślna to "online".</span><span class="sxs-lookup"><span data-stu-id="2c5ee-121">The default value is "Online".</span></span>|  
|<span data-ttu-id="2c5ee-122">issuerCertificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="2c5ee-122">issuerCertificateValidationMode</span></span>|<span data-ttu-id="2c5ee-123"><xref:System.ServiceModel.Security.X509CertificateValidationMode> Wartość określająca tryb walidacji, który ma być używany dla certyfikatu X. 509.</span><span class="sxs-lookup"><span data-stu-id="2c5ee-123">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="2c5ee-124">Wartość domyślna to "PeerOrChainTrust".</span><span class="sxs-lookup"><span data-stu-id="2c5ee-124">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="2c5ee-125">issuerCertificateTrustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="2c5ee-125">issuerCertificateTrustedStoreLocation</span></span>|<span data-ttu-id="2c5ee-126"><xref:System.Security.Cryptography.X509Certificates.StoreLocation> Wartość określająca magazyn certyfikatów X. 509.</span><span class="sxs-lookup"><span data-stu-id="2c5ee-126">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="2c5ee-127">Wartość domyślna to "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="2c5ee-127">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="2c5ee-128">issuerCertificateValidator</span><span class="sxs-lookup"><span data-stu-id="2c5ee-128">issuerCertificateValidator</span></span>|<span data-ttu-id="2c5ee-129">Typ niestandardowy, który pochodzi od <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="2c5ee-129">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="2c5ee-130">`issuerCertificateValidationMode` Jeśli atrybut jest "Custom", wystąpienie tego typu jest używane na potrzeby walidacji certyfikatu wystawcy.</span><span class="sxs-lookup"><span data-stu-id="2c5ee-130">If the `issuerCertificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2c5ee-131">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2c5ee-131">Child Elements</span></span>  
  
|<span data-ttu-id="2c5ee-132">Element</span><span class="sxs-lookup"><span data-stu-id="2c5ee-132">Element</span></span>|<span data-ttu-id="2c5ee-133">Opis</span><span class="sxs-lookup"><span data-stu-id="2c5ee-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2c5ee-134">\<nameClaimType ></span><span class="sxs-lookup"><span data-stu-id="2c5ee-134">\<nameClaimType></span></span>](nameclaimtype.md)|<span data-ttu-id="2c5ee-135">Ustawia typ zgłoszenia, który określa <xref:System.Security.Principal.IIdentity.Name%2A> właściwość.</span><span class="sxs-lookup"><span data-stu-id="2c5ee-135">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span>|  
|[<span data-ttu-id="2c5ee-136">\<roleClaimType></span><span class="sxs-lookup"><span data-stu-id="2c5ee-136">\<roleClaimType></span></span>](roleclaimtype.md)|<span data-ttu-id="2c5ee-137">Określa typ oświadczenia, który definiuje oświadczenia typu roli w kolekcji <xref:System.Security.Claims.ClaimsIdentity> obiektów zwracanych <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> przez metodę procedury obsługi tokenu.</span><span class="sxs-lookup"><span data-stu-id="2c5ee-137">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2c5ee-138">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2c5ee-138">Parent Elements</span></span>  
  
|<span data-ttu-id="2c5ee-139">Element</span><span class="sxs-lookup"><span data-stu-id="2c5ee-139">Element</span></span>|<span data-ttu-id="2c5ee-140">Opis</span><span class="sxs-lookup"><span data-stu-id="2c5ee-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2c5ee-141">\<add></span><span class="sxs-lookup"><span data-stu-id="2c5ee-141">\<add></span></span>](add.md)|<span data-ttu-id="2c5ee-142">Dodaje określony program obsługi tokenów zabezpieczających do kolekcji obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="2c5ee-142">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c5ee-143">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2c5ee-143">Remarks</span></span>  
 <span data-ttu-id="2c5ee-144"><xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> `SamlSecurityTokenRequirement` <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> Element jest reprezentowany przez klasę w modelu obiektów i służy do konfigurowania właściwości w lub <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>. `<samlSecurityTokenRequirement>`</span><span class="sxs-lookup"><span data-stu-id="2c5ee-144">The `<samlSecurityTokenRequirement>` element is represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class in the object model and is used to configure the `SamlSecurityTokenRequirement` property on a <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> or a <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c5ee-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="2c5ee-145">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement issuerCertificateValidationMode="PeerOrChainTrust"  
                                  issuerCertificateRevocationMode="Online"  
                                  issuerCertificateTrustedStoreLocation="LocalMachine"  
                                  mapToWindows="false">  
  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```
