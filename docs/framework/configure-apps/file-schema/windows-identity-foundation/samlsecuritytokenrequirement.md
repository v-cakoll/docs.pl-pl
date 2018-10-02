---
title: '&lt;samlSecurityTokenRequirement&gt;'
ms.date: 03/30/2017
ms.assetid: 09202d12-88d3-49cc-953b-703bcc1690eb
author: BrucePerlerMS
ms.openlocfilehash: c9856dae971691baf9dabe845bdecae90cbc8aa5
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2018
ms.locfileid: "48031893"
---
# <a name="ltsamlsecuritytokenrequirementgt"></a><span data-ttu-id="313f6-102">&lt;samlSecurityTokenRequirement&gt;</span><span class="sxs-lookup"><span data-stu-id="313f6-102">&lt;samlSecurityTokenRequirement&gt;</span></span>
<span data-ttu-id="313f6-103">Udostępnia konfigurację dla <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> klasy <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> klasy lub klasy pochodnej z jednego z tych klas.</span><span class="sxs-lookup"><span data-stu-id="313f6-103">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span> <span data-ttu-id="313f6-104">Reprezentowane przez <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> klasy.</span><span class="sxs-lookup"><span data-stu-id="313f6-104">Represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class.</span></span>  
  
 <span data-ttu-id="313f6-105">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="313f6-105">\<system.identityModel></span></span>  
<span data-ttu-id="313f6-106">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="313f6-106">\<identityConfiguration></span></span>  
<span data-ttu-id="313f6-107">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="313f6-107">\<securityTokenHandlers></span></span>  
<span data-ttu-id="313f6-108">\<add></span><span class="sxs-lookup"><span data-stu-id="313f6-108">\<add></span></span>  
<span data-ttu-id="313f6-109">\<samlSecurityTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="313f6-109">\<samlSecurityTokenRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="313f6-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="313f6-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="313f6-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="313f6-111">Attributes and Elements</span></span>  
 <span data-ttu-id="313f6-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="313f6-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="313f6-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="313f6-113">Attributes</span></span>  
  
|<span data-ttu-id="313f6-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="313f6-114">Attribute</span></span>|<span data-ttu-id="313f6-115">Opis</span><span class="sxs-lookup"><span data-stu-id="313f6-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="313f6-116">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="313f6-116">mapToWindows</span></span>|<span data-ttu-id="313f6-117">Określa, czy programu obsługi tokenów powinny być mapowane sprawdzania poprawności tokenu z kontem Windows za pomocą przychodzące oświadczenia nazwy UPN.</span><span class="sxs-lookup"><span data-stu-id="313f6-117">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="313f6-118">Wartość domyślna to "false".</span><span class="sxs-lookup"><span data-stu-id="313f6-118">The default is "false".</span></span>|  
|<span data-ttu-id="313f6-119">issuerCertificateRevocationMode</span><span class="sxs-lookup"><span data-stu-id="313f6-119">issuerCertificateRevocationMode</span></span>|<span data-ttu-id="313f6-120"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> Wartość, która określa tryb odwołania dla certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="313f6-120">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="313f6-121">Wartość domyślna to "Online".</span><span class="sxs-lookup"><span data-stu-id="313f6-121">The default value is "Online".</span></span>|  
|<span data-ttu-id="313f6-122">issuerCertificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="313f6-122">issuerCertificateValidationMode</span></span>|<span data-ttu-id="313f6-123"><xref:System.ServiceModel.Security.X509CertificateValidationMode> Wartość, która określa tryb weryfikacji do użycia certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="313f6-123">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="313f6-124">Wartość domyślna to "PeerOrChainTrust".</span><span class="sxs-lookup"><span data-stu-id="313f6-124">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="313f6-125">issuerCertificateTrustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="313f6-125">issuerCertificateTrustedStoreLocation</span></span>|<span data-ttu-id="313f6-126">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> wartość, która określa magazynu certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="313f6-126">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="313f6-127">Wartość domyślna to "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="313f6-127">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="313f6-128">issuerCertificateValidator</span><span class="sxs-lookup"><span data-stu-id="313f6-128">issuerCertificateValidator</span></span>|<span data-ttu-id="313f6-129">Typ niestandardowy, który pochodzi od klasy <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="313f6-129">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="313f6-130">Jeśli `issuerCertificateValidationMode` atrybut jest "Niestandardowy", wystąpienia tego typu jest używany do walidacji certyfikatu wystawcy.</span><span class="sxs-lookup"><span data-stu-id="313f6-130">If the `issuerCertificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="313f6-131">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="313f6-131">Child Elements</span></span>  
  
|<span data-ttu-id="313f6-132">Element</span><span class="sxs-lookup"><span data-stu-id="313f6-132">Element</span></span>|<span data-ttu-id="313f6-133">Opis</span><span class="sxs-lookup"><span data-stu-id="313f6-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="313f6-134">\<nameClaimType ></span><span class="sxs-lookup"><span data-stu-id="313f6-134">\<nameClaimType></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/nameclaimtype.md)|<span data-ttu-id="313f6-135">Ustawia typ oświadczenia, który określa <xref:System.Security.Principal.IIdentity.Name%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="313f6-135">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span>|  
|[<span data-ttu-id="313f6-136">\<roleClaimType ></span><span class="sxs-lookup"><span data-stu-id="313f6-136">\<roleClaimType></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/roleclaimtype.md)|<span data-ttu-id="313f6-137">Określa typ oświadczenia, który definiuje typ oświadczenia roli w kolekcji <xref:System.Security.Claims.ClaimsIdentity> obiektów zwróconych przez <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> metodę programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="313f6-137">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="313f6-138">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="313f6-138">Parent Elements</span></span>  
  
|<span data-ttu-id="313f6-139">Element</span><span class="sxs-lookup"><span data-stu-id="313f6-139">Element</span></span>|<span data-ttu-id="313f6-140">Opis</span><span class="sxs-lookup"><span data-stu-id="313f6-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="313f6-141">\<add></span><span class="sxs-lookup"><span data-stu-id="313f6-141">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="313f6-142">Programu obsługi tokenów zabezpieczeń określone są dodawane do kolekcji programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="313f6-142">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="313f6-143">Uwagi</span><span class="sxs-lookup"><span data-stu-id="313f6-143">Remarks</span></span>  
 <span data-ttu-id="313f6-144">`<samlSecurityTokenRequirement>` Element jest reprezentowany przez <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> klasy w modelu obiektów i służy do konfigurowania `SamlSecurityTokenRequirement` właściwość <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> lub <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.</span><span class="sxs-lookup"><span data-stu-id="313f6-144">The `<samlSecurityTokenRequirement>` element is represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class in the object model and is used to configure the `SamlSecurityTokenRequirement` property on a <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> or a <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="313f6-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="313f6-145">Example</span></span>  
  
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
