---
title: <samlSecurityTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 09202d12-88d3-49cc-953b-703bcc1690eb
author: BrucePerlerMS
ms.openlocfilehash: e1b8acd48ee185b3c6c50f70321bb9ca66e8e02b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55284625"
---
# <a name="samlsecuritytokenrequirement"></a><span data-ttu-id="13350-101">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="13350-101">\<samlSecurityTokenRequirement></span></span>
<span data-ttu-id="13350-102">Udostępnia konfigurację dla <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> klasy <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> klasy lub klasy pochodnej z jednego z tych klas.</span><span class="sxs-lookup"><span data-stu-id="13350-102">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span> <span data-ttu-id="13350-103">Reprezentowane przez <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> klasy.</span><span class="sxs-lookup"><span data-stu-id="13350-103">Represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class.</span></span>  
  
 <span data-ttu-id="13350-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="13350-104">\<system.identityModel></span></span>  
<span data-ttu-id="13350-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="13350-105">\<identityConfiguration></span></span>  
<span data-ttu-id="13350-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="13350-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="13350-107">\<add></span><span class="sxs-lookup"><span data-stu-id="13350-107">\<add></span></span>  
<span data-ttu-id="13350-108">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="13350-108">\<samlSecurityTokenRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13350-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="13350-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="13350-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="13350-110">Attributes and Elements</span></span>  
 <span data-ttu-id="13350-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="13350-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="13350-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="13350-112">Attributes</span></span>  
  
|<span data-ttu-id="13350-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="13350-113">Attribute</span></span>|<span data-ttu-id="13350-114">Opis</span><span class="sxs-lookup"><span data-stu-id="13350-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="13350-115">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="13350-115">mapToWindows</span></span>|<span data-ttu-id="13350-116">Określa, czy programu obsługi tokenów powinny być mapowane sprawdzania poprawności tokenu z kontem Windows za pomocą przychodzące oświadczenia nazwy UPN.</span><span class="sxs-lookup"><span data-stu-id="13350-116">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="13350-117">Wartość domyślna to "false".</span><span class="sxs-lookup"><span data-stu-id="13350-117">The default is "false".</span></span>|  
|<span data-ttu-id="13350-118">issuerCertificateRevocationMode</span><span class="sxs-lookup"><span data-stu-id="13350-118">issuerCertificateRevocationMode</span></span>|<span data-ttu-id="13350-119"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> Wartość, która określa tryb odwołania dla certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="13350-119">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="13350-120">Wartość domyślna to "Online".</span><span class="sxs-lookup"><span data-stu-id="13350-120">The default value is "Online".</span></span>|  
|<span data-ttu-id="13350-121">issuerCertificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="13350-121">issuerCertificateValidationMode</span></span>|<span data-ttu-id="13350-122"><xref:System.ServiceModel.Security.X509CertificateValidationMode> Wartość, która określa tryb weryfikacji do użycia certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="13350-122">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="13350-123">Wartość domyślna to "PeerOrChainTrust".</span><span class="sxs-lookup"><span data-stu-id="13350-123">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="13350-124">issuerCertificateTrustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="13350-124">issuerCertificateTrustedStoreLocation</span></span>|<span data-ttu-id="13350-125">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> wartość, która określa magazynu certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="13350-125">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="13350-126">Wartość domyślna to "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="13350-126">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="13350-127">issuerCertificateValidator</span><span class="sxs-lookup"><span data-stu-id="13350-127">issuerCertificateValidator</span></span>|<span data-ttu-id="13350-128">Typ niestandardowy, który pochodzi od klasy <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="13350-128">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="13350-129">Jeśli `issuerCertificateValidationMode` atrybut jest "Niestandardowy", wystąpienia tego typu jest używany do walidacji certyfikatu wystawcy.</span><span class="sxs-lookup"><span data-stu-id="13350-129">If the `issuerCertificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="13350-130">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="13350-130">Child Elements</span></span>  
  
|<span data-ttu-id="13350-131">Element</span><span class="sxs-lookup"><span data-stu-id="13350-131">Element</span></span>|<span data-ttu-id="13350-132">Opis</span><span class="sxs-lookup"><span data-stu-id="13350-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="13350-133">\<nameClaimType></span><span class="sxs-lookup"><span data-stu-id="13350-133">\<nameClaimType></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/nameclaimtype.md)|<span data-ttu-id="13350-134">Ustawia typ oświadczenia, który określa <xref:System.Security.Principal.IIdentity.Name%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="13350-134">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span>|  
|[<span data-ttu-id="13350-135">\<roleClaimType></span><span class="sxs-lookup"><span data-stu-id="13350-135">\<roleClaimType></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/roleclaimtype.md)|<span data-ttu-id="13350-136">Określa typ oświadczenia, który definiuje typ oświadczenia roli w kolekcji <xref:System.Security.Claims.ClaimsIdentity> obiektów zwróconych przez <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> metodę programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="13350-136">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="13350-137">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="13350-137">Parent Elements</span></span>  
  
|<span data-ttu-id="13350-138">Element</span><span class="sxs-lookup"><span data-stu-id="13350-138">Element</span></span>|<span data-ttu-id="13350-139">Opis</span><span class="sxs-lookup"><span data-stu-id="13350-139">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="13350-140">\<add></span><span class="sxs-lookup"><span data-stu-id="13350-140">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="13350-141">Programu obsługi tokenów zabezpieczeń określone są dodawane do kolekcji programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="13350-141">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13350-142">Uwagi</span><span class="sxs-lookup"><span data-stu-id="13350-142">Remarks</span></span>  
 <span data-ttu-id="13350-143">`<samlSecurityTokenRequirement>` Element jest reprezentowany przez <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> klasy w modelu obiektów i służy do konfigurowania `SamlSecurityTokenRequirement` właściwość <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> lub <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.</span><span class="sxs-lookup"><span data-stu-id="13350-143">The `<samlSecurityTokenRequirement>` element is represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class in the object model and is used to configure the `SamlSecurityTokenRequirement` property on a <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> or a <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13350-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="13350-144">Example</span></span>  
  
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
