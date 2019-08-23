---
title: <samlSecurityTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 09202d12-88d3-49cc-953b-703bcc1690eb
author: BrucePerlerMS
ms.openlocfilehash: df259398beb242ea95efb248d6b5140b38ca3c45
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942491"
---
# <a name="samlsecuritytokenrequirement"></a><span data-ttu-id="eb9cc-101">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="eb9cc-101">\<samlSecurityTokenRequirement></span></span>
<span data-ttu-id="eb9cc-102">Zapewnia konfigurację <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> klasy <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> , klasy lub klasy pochodnej jednej z tych klas.</span><span class="sxs-lookup"><span data-stu-id="eb9cc-102">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span> <span data-ttu-id="eb9cc-103">Reprezentowane przez <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> klasę.</span><span class="sxs-lookup"><span data-stu-id="eb9cc-103">Represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class.</span></span>  
  
 <span data-ttu-id="eb9cc-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="eb9cc-104">\<system.identityModel></span></span>  
<span data-ttu-id="eb9cc-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="eb9cc-105">\<identityConfiguration></span></span>  
<span data-ttu-id="eb9cc-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="eb9cc-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="eb9cc-107">\<add></span><span class="sxs-lookup"><span data-stu-id="eb9cc-107">\<add></span></span>  
<span data-ttu-id="eb9cc-108">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="eb9cc-108">\<samlSecurityTokenRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb9cc-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="eb9cc-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eb9cc-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="eb9cc-110">Attributes and Elements</span></span>  
 <span data-ttu-id="eb9cc-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="eb9cc-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eb9cc-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="eb9cc-112">Attributes</span></span>  
  
|<span data-ttu-id="eb9cc-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="eb9cc-113">Attribute</span></span>|<span data-ttu-id="eb9cc-114">Opis</span><span class="sxs-lookup"><span data-stu-id="eb9cc-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="eb9cc-115">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="eb9cc-115">mapToWindows</span></span>|<span data-ttu-id="eb9cc-116">Określa, czy program obsługi tokenów powinien mapować token walidacji na konto systemu Windows przy użyciu przychodzącego oświadczenie nazwy UPN.</span><span class="sxs-lookup"><span data-stu-id="eb9cc-116">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="eb9cc-117">Wartość domyślna to "false".</span><span class="sxs-lookup"><span data-stu-id="eb9cc-117">The default is "false".</span></span>|  
|<span data-ttu-id="eb9cc-118">issuerCertificateRevocationMode</span><span class="sxs-lookup"><span data-stu-id="eb9cc-118">issuerCertificateRevocationMode</span></span>|<span data-ttu-id="eb9cc-119"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> Wartość określająca tryb odwołania, który ma być używany dla certyfikatu X. 509.</span><span class="sxs-lookup"><span data-stu-id="eb9cc-119">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="eb9cc-120">Wartość domyślna to "online".</span><span class="sxs-lookup"><span data-stu-id="eb9cc-120">The default value is "Online".</span></span>|  
|<span data-ttu-id="eb9cc-121">issuerCertificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="eb9cc-121">issuerCertificateValidationMode</span></span>|<span data-ttu-id="eb9cc-122"><xref:System.ServiceModel.Security.X509CertificateValidationMode> Wartość określająca tryb walidacji, który ma być używany dla certyfikatu X. 509.</span><span class="sxs-lookup"><span data-stu-id="eb9cc-122">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="eb9cc-123">Wartość domyślna to "PeerOrChainTrust".</span><span class="sxs-lookup"><span data-stu-id="eb9cc-123">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="eb9cc-124">issuerCertificateTrustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="eb9cc-124">issuerCertificateTrustedStoreLocation</span></span>|<span data-ttu-id="eb9cc-125"><xref:System.Security.Cryptography.X509Certificates.StoreLocation> Wartość określająca magazyn certyfikatów X. 509.</span><span class="sxs-lookup"><span data-stu-id="eb9cc-125">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="eb9cc-126">Wartość domyślna to "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="eb9cc-126">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="eb9cc-127">issuerCertificateValidator</span><span class="sxs-lookup"><span data-stu-id="eb9cc-127">issuerCertificateValidator</span></span>|<span data-ttu-id="eb9cc-128">Typ niestandardowy, który pochodzi od <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="eb9cc-128">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="eb9cc-129">`issuerCertificateValidationMode` Jeśli atrybut jest "Custom", wystąpienie tego typu jest używane na potrzeby walidacji certyfikatu wystawcy.</span><span class="sxs-lookup"><span data-stu-id="eb9cc-129">If the `issuerCertificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="eb9cc-130">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="eb9cc-130">Child Elements</span></span>  
  
|<span data-ttu-id="eb9cc-131">Element</span><span class="sxs-lookup"><span data-stu-id="eb9cc-131">Element</span></span>|<span data-ttu-id="eb9cc-132">Opis</span><span class="sxs-lookup"><span data-stu-id="eb9cc-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eb9cc-133">\<nameClaimType ></span><span class="sxs-lookup"><span data-stu-id="eb9cc-133">\<nameClaimType></span></span>](nameclaimtype.md)|<span data-ttu-id="eb9cc-134">Ustawia typ zgłoszenia, który określa <xref:System.Security.Principal.IIdentity.Name%2A> właściwość.</span><span class="sxs-lookup"><span data-stu-id="eb9cc-134">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span>|  
|[<span data-ttu-id="eb9cc-135">\<roleClaimType></span><span class="sxs-lookup"><span data-stu-id="eb9cc-135">\<roleClaimType></span></span>](roleclaimtype.md)|<span data-ttu-id="eb9cc-136">Określa typ oświadczenia, który definiuje oświadczenia typu roli w kolekcji <xref:System.Security.Claims.ClaimsIdentity> obiektów zwracanych <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> przez metodę procedury obsługi tokenu.</span><span class="sxs-lookup"><span data-stu-id="eb9cc-136">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="eb9cc-137">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="eb9cc-137">Parent Elements</span></span>  
  
|<span data-ttu-id="eb9cc-138">Element</span><span class="sxs-lookup"><span data-stu-id="eb9cc-138">Element</span></span>|<span data-ttu-id="eb9cc-139">Opis</span><span class="sxs-lookup"><span data-stu-id="eb9cc-139">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eb9cc-140">\<add></span><span class="sxs-lookup"><span data-stu-id="eb9cc-140">\<add></span></span>](add.md)|<span data-ttu-id="eb9cc-141">Dodaje określony program obsługi tokenów zabezpieczających do kolekcji obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="eb9cc-141">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eb9cc-142">Uwagi</span><span class="sxs-lookup"><span data-stu-id="eb9cc-142">Remarks</span></span>  
 <span data-ttu-id="eb9cc-143"><xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> `SamlSecurityTokenRequirement` <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> Element jest reprezentowany przez klasę w modelu obiektów i służy do konfigurowania właściwości w lub <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>. `<samlSecurityTokenRequirement>`</span><span class="sxs-lookup"><span data-stu-id="eb9cc-143">The `<samlSecurityTokenRequirement>` element is represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class in the object model and is used to configure the `SamlSecurityTokenRequirement` property on a <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> or a <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb9cc-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="eb9cc-144">Example</span></span>  
  
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
