---
title: '&lt;samlSecurityTokenRequirement&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 09202d12-88d3-49cc-953b-703bcc1690eb
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: a642a79618329a55afa98dba04e4ac5f419cae7c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltsamlsecuritytokenrequirementgt"></a><span data-ttu-id="2d267-102">&lt;samlSecurityTokenRequirement&gt;</span><span class="sxs-lookup"><span data-stu-id="2d267-102">&lt;samlSecurityTokenRequirement&gt;</span></span>
<span data-ttu-id="2d267-103">Zapewnia konfigurację <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> klasy <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> klasy lub klasy pochodnej każdej z tych klas.</span><span class="sxs-lookup"><span data-stu-id="2d267-103">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span> <span data-ttu-id="2d267-104">Reprezentowane przez <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> klasy.</span><span class="sxs-lookup"><span data-stu-id="2d267-104">Represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class.</span></span>  
  
 <span data-ttu-id="2d267-105">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="2d267-105">\<system.identityModel></span></span>  
<span data-ttu-id="2d267-106">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="2d267-106">\<identityConfiguration></span></span>  
<span data-ttu-id="2d267-107">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="2d267-107">\<securityTokenHandlers></span></span>  
<span data-ttu-id="2d267-108">\<Dodaj ></span><span class="sxs-lookup"><span data-stu-id="2d267-108">\<add></span></span>  
<span data-ttu-id="2d267-109">\<samlSecurityTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="2d267-109">\<samlSecurityTokenRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d267-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="2d267-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2d267-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2d267-111">Attributes and Elements</span></span>  
 <span data-ttu-id="2d267-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2d267-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2d267-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2d267-113">Attributes</span></span>  
  
|<span data-ttu-id="2d267-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="2d267-114">Attribute</span></span>|<span data-ttu-id="2d267-115">Opis</span><span class="sxs-lookup"><span data-stu-id="2d267-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2d267-116">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="2d267-116">mapToWindows</span></span>|<span data-ttu-id="2d267-117">Określa, czy programu obsługi tokenów należy mapować sprawdzania poprawności tokenu konto systemu Windows przy użyciu nazwy UPN oświadczenia przychodzącego.</span><span class="sxs-lookup"><span data-stu-id="2d267-117">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="2d267-118">Wartość domyślna to "false".</span><span class="sxs-lookup"><span data-stu-id="2d267-118">The default is "false".</span></span>|  
|<span data-ttu-id="2d267-119">issuerCertificateRevocationMode</span><span class="sxs-lookup"><span data-stu-id="2d267-119">issuerCertificateRevocationMode</span></span>|<span data-ttu-id="2d267-120"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> Wartość, która określa tryb odwołania dla certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="2d267-120">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="2d267-121">Wartość domyślna to "Online".</span><span class="sxs-lookup"><span data-stu-id="2d267-121">The default value is "Online".</span></span>|  
|<span data-ttu-id="2d267-122">issuerCertificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="2d267-122">issuerCertificateValidationMode</span></span>|<span data-ttu-id="2d267-123"><xref:System.ServiceModel.Security.X509CertificateValidationMode> Wartość, która określa tryb walidacji do użycia na potrzeby certyfikatów X.509.</span><span class="sxs-lookup"><span data-stu-id="2d267-123">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="2d267-124">Wartość domyślna to "PeerOrChainTrust".</span><span class="sxs-lookup"><span data-stu-id="2d267-124">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="2d267-125">issuerCertificateTrustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="2d267-125">issuerCertificateTrustedStoreLocation</span></span>|<span data-ttu-id="2d267-126">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> wartość, która określa magazynu certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="2d267-126">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="2d267-127">Wartością domyślną jest "Komputer lokalny".</span><span class="sxs-lookup"><span data-stu-id="2d267-127">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="2d267-128">issuerCertificateValidator</span><span class="sxs-lookup"><span data-stu-id="2d267-128">issuerCertificateValidator</span></span>|<span data-ttu-id="2d267-129">Typ niestandardowy, która jest pochodną <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="2d267-129">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="2d267-130">Jeśli `issuerCertificateValidationMode` atrybutu jest "Custom", wystąpienie tego typu jest używany do sprawdzania poprawności wystawcy certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="2d267-130">If the `issuerCertificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2d267-131">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2d267-131">Child Elements</span></span>  
  
|<span data-ttu-id="2d267-132">Element</span><span class="sxs-lookup"><span data-stu-id="2d267-132">Element</span></span>|<span data-ttu-id="2d267-133">Opis</span><span class="sxs-lookup"><span data-stu-id="2d267-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2d267-134">\<nameClaimType ></span><span class="sxs-lookup"><span data-stu-id="2d267-134">\<nameClaimType></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/nameclaimtype.md)|<span data-ttu-id="2d267-135">Ustawia typ oświadczenia, która określa <xref:System.Security.Principal.IIdentity.Name%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="2d267-135">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span>|  
|[<span data-ttu-id="2d267-136">\<roleClaimType ></span><span class="sxs-lookup"><span data-stu-id="2d267-136">\<roleClaimType></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/roleclaimtype.md)|<span data-ttu-id="2d267-137">Określa typ oświadczenia, który definiuje oświadczeń Typ roli w kolekcji <xref:System.Security.Claims.ClaimsIdentity> obiekty zwrócone przez <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> metody programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="2d267-137">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2d267-138">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2d267-138">Parent Elements</span></span>  
  
|<span data-ttu-id="2d267-139">Element</span><span class="sxs-lookup"><span data-stu-id="2d267-139">Element</span></span>|<span data-ttu-id="2d267-140">Opis</span><span class="sxs-lookup"><span data-stu-id="2d267-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2d267-141">\<Dodaj ></span><span class="sxs-lookup"><span data-stu-id="2d267-141">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="2d267-142">Dodaje określony zabezpieczenia programu obsługi tokenów do kolekcji programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="2d267-142">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2d267-143">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2d267-143">Remarks</span></span>  
 <span data-ttu-id="2d267-144">`<samlSecurityTokenRequirement>` Element jest reprezentowana przez <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> klasy w modelu obiektów i jest używany do konfigurowania `SamlSecurityTokenRequirement` właściwość <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> lub <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.</span><span class="sxs-lookup"><span data-stu-id="2d267-144">The `<samlSecurityTokenRequirement>` element is represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class in the object model and is used to configure the `SamlSecurityTokenRequirement` property on a <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> or a <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d267-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d267-145">Example</span></span>  
  
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
