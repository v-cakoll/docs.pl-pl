---
title: <samlSecurityTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 09202d12-88d3-49cc-953b-703bcc1690eb
author: BrucePerlerMS
ms.openlocfilehash: b27f337189a7d0b66ffd38e032b5eb864e5094a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152635"
---
# <a name="samlsecuritytokenrequirement"></a><span data-ttu-id="677e2-101">\<samlSecurityTokenOkiwkość></span><span class="sxs-lookup"><span data-stu-id="677e2-101">\<samlSecurityTokenRequirement></span></span>
<span data-ttu-id="677e2-102">Zawiera konfigurację <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> dla <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> klasy, klasy lub klasy pochodnej jednej z tych klas.</span><span class="sxs-lookup"><span data-stu-id="677e2-102">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span> <span data-ttu-id="677e2-103">Reprezentowana przez <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> klasę.</span><span class="sxs-lookup"><span data-stu-id="677e2-103">Represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class.</span></span>  
  
<span data-ttu-id="677e2-104">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="677e2-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="677e2-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="677e2-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="677e2-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<>konfiguracji tożsamości**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="677e2-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="677e2-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>securityTokenHandlers**](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="677e2-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="677e2-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dodaj>**](add.md)</span><span class="sxs-lookup"><span data-stu-id="677e2-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)</span></span>\
<span data-ttu-id="677e2-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<samlSecurityTokenOkiwkość>**</span><span class="sxs-lookup"><span data-stu-id="677e2-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<samlSecurityTokenRequirement>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="677e2-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="677e2-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="677e2-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="677e2-111">Attributes and Elements</span></span>  
 <span data-ttu-id="677e2-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="677e2-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="677e2-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="677e2-113">Attributes</span></span>  
  
|<span data-ttu-id="677e2-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="677e2-114">Attribute</span></span>|<span data-ttu-id="677e2-115">Opis</span><span class="sxs-lookup"><span data-stu-id="677e2-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="677e2-116">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="677e2-116">mapToWindows</span></span>|<span data-ttu-id="677e2-117">Określa, czy program obsługi tokenu powinien mapować token sprawdzania poprawności na konto systemu Windows przy użyciu przychodzącego oświadczenia upn.</span><span class="sxs-lookup"><span data-stu-id="677e2-117">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="677e2-118">Wartość domyślna to "false".</span><span class="sxs-lookup"><span data-stu-id="677e2-118">The default is "false".</span></span>|  
|<span data-ttu-id="677e2-119">issuerCertificateRevocationMode</span><span class="sxs-lookup"><span data-stu-id="677e2-119">issuerCertificateRevocationMode</span></span>|<span data-ttu-id="677e2-120">Wartość <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> określająca tryb odwołania do użycia dla certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="677e2-120">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="677e2-121">Wartością domyślną jest "Online".</span><span class="sxs-lookup"><span data-stu-id="677e2-121">The default value is "Online".</span></span>|  
|<span data-ttu-id="677e2-122">issuerCertificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="677e2-122">issuerCertificateValidationMode</span></span>|<span data-ttu-id="677e2-123">Wartość <xref:System.ServiceModel.Security.X509CertificateValidationMode> określająca tryb sprawdzania poprawności dla certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="677e2-123">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="677e2-124">Wartością domyślną jest "PeerOrChainTrust".</span><span class="sxs-lookup"><span data-stu-id="677e2-124">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="677e2-125">issuerCertificateTrustedStoreLokation</span><span class="sxs-lookup"><span data-stu-id="677e2-125">issuerCertificateTrustedStoreLocation</span></span>|<span data-ttu-id="677e2-126">Wartość <xref:System.Security.Cryptography.X509Certificates.StoreLocation> określająca magazyn certyfikatów X.509.</span><span class="sxs-lookup"><span data-stu-id="677e2-126">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="677e2-127">Wartością domyślną jest "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="677e2-127">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="677e2-128">issuerCertificateValidator</span><span class="sxs-lookup"><span data-stu-id="677e2-128">issuerCertificateValidator</span></span>|<span data-ttu-id="677e2-129">Typ niestandardowy, który <xref:System.IdentityModel.Selectors.X509CertificateValidator>pochodzi od .</span><span class="sxs-lookup"><span data-stu-id="677e2-129">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="677e2-130">Jeśli `issuerCertificateValidationMode` atrybut jest "Niestandardowe", wystąpienie tego typu jest używane do sprawdzania poprawności certyfikatu wystawcy.</span><span class="sxs-lookup"><span data-stu-id="677e2-130">If the `issuerCertificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="677e2-131">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="677e2-131">Child Elements</span></span>  
  
|<span data-ttu-id="677e2-132">Element</span><span class="sxs-lookup"><span data-stu-id="677e2-132">Element</span></span>|<span data-ttu-id="677e2-133">Opis</span><span class="sxs-lookup"><span data-stu-id="677e2-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="677e2-134">\<nazwaClaimType></span><span class="sxs-lookup"><span data-stu-id="677e2-134">\<nameClaimType></span></span>](nameclaimtype.md)|<span data-ttu-id="677e2-135">Ustawia typ oświadczenia, który <xref:System.Security.Principal.IIdentity.Name%2A> określa właściwość.</span><span class="sxs-lookup"><span data-stu-id="677e2-135">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span>|  
|[<span data-ttu-id="677e2-136">\<>roleClaimType</span><span class="sxs-lookup"><span data-stu-id="677e2-136">\<roleClaimType></span></span>](roleclaimtype.md)|<span data-ttu-id="677e2-137">Określa typ oświadczenia, który definiuje oświadczenia typu roli <xref:System.Security.Claims.ClaimsIdentity> w kolekcji obiektów zwracanych przez <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> metodę obsługi tokenu.</span><span class="sxs-lookup"><span data-stu-id="677e2-137">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="677e2-138">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="677e2-138">Parent Elements</span></span>  
  
|<span data-ttu-id="677e2-139">Element</span><span class="sxs-lookup"><span data-stu-id="677e2-139">Element</span></span>|<span data-ttu-id="677e2-140">Opis</span><span class="sxs-lookup"><span data-stu-id="677e2-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="677e2-141">\<dodaj></span><span class="sxs-lookup"><span data-stu-id="677e2-141">\<add></span></span>](add.md)|<span data-ttu-id="677e2-142">Dodaje określony program obsługi tokenu zabezpieczającego do kolekcji obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="677e2-142">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="677e2-143">Uwagi</span><span class="sxs-lookup"><span data-stu-id="677e2-143">Remarks</span></span>  
 <span data-ttu-id="677e2-144">Element `<samlSecurityTokenRequirement>` jest reprezentowany <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> przez klasę w modelu obiektu i `SamlSecurityTokenRequirement` służy do <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> konfigurowania właściwości na a lub <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.</span><span class="sxs-lookup"><span data-stu-id="677e2-144">The `<samlSecurityTokenRequirement>` element is represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class in the object model and is used to configure the `SamlSecurityTokenRequirement` property on a <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> or a <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="677e2-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="677e2-145">Example</span></span>  
  
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
