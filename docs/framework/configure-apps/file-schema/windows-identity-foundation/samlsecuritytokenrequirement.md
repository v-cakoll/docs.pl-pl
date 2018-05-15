---
title: '&lt;samlSecurityTokenRequirement&gt;'
ms.date: 03/30/2017
ms.assetid: 09202d12-88d3-49cc-953b-703bcc1690eb
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 86a9b9dcf0b9f5971e50ff7d1f1c37ca2e5f778a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltsamlsecuritytokenrequirementgt"></a><span data-ttu-id="4a924-102">&lt;samlSecurityTokenRequirement&gt;</span><span class="sxs-lookup"><span data-stu-id="4a924-102">&lt;samlSecurityTokenRequirement&gt;</span></span>
<span data-ttu-id="4a924-103">Zapewnia konfigurację <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> klasy <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> klasy lub klasy pochodnej każdej z tych klas.</span><span class="sxs-lookup"><span data-stu-id="4a924-103">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span> <span data-ttu-id="4a924-104">Reprezentowane przez <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> klasy.</span><span class="sxs-lookup"><span data-stu-id="4a924-104">Represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class.</span></span>  
  
 <span data-ttu-id="4a924-105">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="4a924-105">\<system.identityModel></span></span>  
<span data-ttu-id="4a924-106">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="4a924-106">\<identityConfiguration></span></span>  
<span data-ttu-id="4a924-107">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="4a924-107">\<securityTokenHandlers></span></span>  
<span data-ttu-id="4a924-108">\<add></span><span class="sxs-lookup"><span data-stu-id="4a924-108">\<add></span></span>  
<span data-ttu-id="4a924-109">\<samlSecurityTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="4a924-109">\<samlSecurityTokenRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a924-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="4a924-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4a924-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4a924-111">Attributes and Elements</span></span>  
 <span data-ttu-id="4a924-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4a924-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4a924-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4a924-113">Attributes</span></span>  
  
|<span data-ttu-id="4a924-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4a924-114">Attribute</span></span>|<span data-ttu-id="4a924-115">Opis</span><span class="sxs-lookup"><span data-stu-id="4a924-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4a924-116">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="4a924-116">mapToWindows</span></span>|<span data-ttu-id="4a924-117">Określa, czy programu obsługi tokenów należy mapować sprawdzania poprawności tokenu konto systemu Windows przy użyciu nazwy UPN oświadczenia przychodzącego.</span><span class="sxs-lookup"><span data-stu-id="4a924-117">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="4a924-118">Wartość domyślna to "false".</span><span class="sxs-lookup"><span data-stu-id="4a924-118">The default is "false".</span></span>|  
|<span data-ttu-id="4a924-119">issuerCertificateRevocationMode</span><span class="sxs-lookup"><span data-stu-id="4a924-119">issuerCertificateRevocationMode</span></span>|<span data-ttu-id="4a924-120"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> Wartość, która określa tryb odwołania dla certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="4a924-120">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="4a924-121">Wartość domyślna to "Online".</span><span class="sxs-lookup"><span data-stu-id="4a924-121">The default value is "Online".</span></span>|  
|<span data-ttu-id="4a924-122">issuerCertificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="4a924-122">issuerCertificateValidationMode</span></span>|<span data-ttu-id="4a924-123"><xref:System.ServiceModel.Security.X509CertificateValidationMode> Wartość, która określa tryb walidacji do użycia na potrzeby certyfikatów X.509.</span><span class="sxs-lookup"><span data-stu-id="4a924-123">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="4a924-124">Wartość domyślna to "PeerOrChainTrust".</span><span class="sxs-lookup"><span data-stu-id="4a924-124">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="4a924-125">issuerCertificateTrustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="4a924-125">issuerCertificateTrustedStoreLocation</span></span>|<span data-ttu-id="4a924-126">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> wartość, która określa magazynu certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="4a924-126">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="4a924-127">Wartością domyślną jest "Komputer lokalny".</span><span class="sxs-lookup"><span data-stu-id="4a924-127">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="4a924-128">issuerCertificateValidator</span><span class="sxs-lookup"><span data-stu-id="4a924-128">issuerCertificateValidator</span></span>|<span data-ttu-id="4a924-129">Typ niestandardowy, która jest pochodną <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="4a924-129">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="4a924-130">Jeśli `issuerCertificateValidationMode` atrybutu jest "Custom", wystąpienie tego typu jest używany do sprawdzania poprawności wystawcy certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="4a924-130">If the `issuerCertificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4a924-131">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4a924-131">Child Elements</span></span>  
  
|<span data-ttu-id="4a924-132">Element</span><span class="sxs-lookup"><span data-stu-id="4a924-132">Element</span></span>|<span data-ttu-id="4a924-133">Opis</span><span class="sxs-lookup"><span data-stu-id="4a924-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4a924-134">\<nameClaimType ></span><span class="sxs-lookup"><span data-stu-id="4a924-134">\<nameClaimType></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/nameclaimtype.md)|<span data-ttu-id="4a924-135">Ustawia typ oświadczenia, która określa <xref:System.Security.Principal.IIdentity.Name%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="4a924-135">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span>|  
|[<span data-ttu-id="4a924-136">\<roleClaimType ></span><span class="sxs-lookup"><span data-stu-id="4a924-136">\<roleClaimType></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/roleclaimtype.md)|<span data-ttu-id="4a924-137">Określa typ oświadczenia, który definiuje oświadczeń Typ roli w kolekcji <xref:System.Security.Claims.ClaimsIdentity> obiekty zwrócone przez <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> metody programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="4a924-137">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4a924-138">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4a924-138">Parent Elements</span></span>  
  
|<span data-ttu-id="4a924-139">Element</span><span class="sxs-lookup"><span data-stu-id="4a924-139">Element</span></span>|<span data-ttu-id="4a924-140">Opis</span><span class="sxs-lookup"><span data-stu-id="4a924-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4a924-141">\<add></span><span class="sxs-lookup"><span data-stu-id="4a924-141">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="4a924-142">Dodaje określony zabezpieczenia programu obsługi tokenów do kolekcji programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="4a924-142">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a924-143">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4a924-143">Remarks</span></span>  
 <span data-ttu-id="4a924-144">`<samlSecurityTokenRequirement>` Element jest reprezentowana przez <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> klasy w modelu obiektów i jest używany do konfigurowania `SamlSecurityTokenRequirement` właściwość <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> lub <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.</span><span class="sxs-lookup"><span data-stu-id="4a924-144">The `<samlSecurityTokenRequirement>` element is represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class in the object model and is used to configure the `SamlSecurityTokenRequirement` property on a <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> or a <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4a924-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="4a924-145">Example</span></span>  
  
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
