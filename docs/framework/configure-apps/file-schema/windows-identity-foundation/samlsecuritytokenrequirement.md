---
title: <samlSecurityTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 09202d12-88d3-49cc-953b-703bcc1690eb
author: BrucePerlerMS
ms.openlocfilehash: b27f337189a7d0b66ffd38e032b5eb864e5094a1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152635"
---
# \<samlSecurityTokenRequirement>
<span data-ttu-id="e8144-101">Zapewnia konfigurację <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> klasy, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> klasy lub klasy pochodnej jednej z tych klas.</span><span class="sxs-lookup"><span data-stu-id="e8144-101">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span> <span data-ttu-id="e8144-102">Reprezentowane przez <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> klasę.</span><span class="sxs-lookup"><span data-stu-id="e8144-102">Represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<samlSecurityTokenRequirement>**  
  
## <a name="syntax"></a><span data-ttu-id="e8144-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="e8144-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e8144-104">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e8144-104">Attributes and Elements</span></span>  
 <span data-ttu-id="e8144-105">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e8144-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e8144-106">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e8144-106">Attributes</span></span>  
  
|<span data-ttu-id="e8144-107">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e8144-107">Attribute</span></span>|<span data-ttu-id="e8144-108">Opis</span><span class="sxs-lookup"><span data-stu-id="e8144-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e8144-109">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="e8144-109">mapToWindows</span></span>|<span data-ttu-id="e8144-110">Określa, czy program obsługi tokenów powinien mapować token walidacji na konto systemu Windows przy użyciu przychodzącego oświadczenie nazwy UPN.</span><span class="sxs-lookup"><span data-stu-id="e8144-110">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="e8144-111">Wartość domyślna to "false".</span><span class="sxs-lookup"><span data-stu-id="e8144-111">The default is "false".</span></span>|  
|<span data-ttu-id="e8144-112">issuerCertificateRevocationMode</span><span class="sxs-lookup"><span data-stu-id="e8144-112">issuerCertificateRevocationMode</span></span>|<span data-ttu-id="e8144-113"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>Wartość określająca tryb odwołania, który ma być używany dla certyfikatu X. 509.</span><span class="sxs-lookup"><span data-stu-id="e8144-113">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="e8144-114">Wartość domyślna to "online".</span><span class="sxs-lookup"><span data-stu-id="e8144-114">The default value is "Online".</span></span>|  
|<span data-ttu-id="e8144-115">issuerCertificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="e8144-115">issuerCertificateValidationMode</span></span>|<span data-ttu-id="e8144-116">Wartość określająca <xref:System.ServiceModel.Security.X509CertificateValidationMode> tryb walidacji, który ma być używany dla certyfikatu X. 509.</span><span class="sxs-lookup"><span data-stu-id="e8144-116">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="e8144-117">Wartość domyślna to "PeerOrChainTrust".</span><span class="sxs-lookup"><span data-stu-id="e8144-117">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="e8144-118">issuerCertificateTrustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="e8144-118">issuerCertificateTrustedStoreLocation</span></span>|<span data-ttu-id="e8144-119">Wartość określająca <xref:System.Security.Cryptography.X509Certificates.StoreLocation> Magazyn certyfikatów X. 509.</span><span class="sxs-lookup"><span data-stu-id="e8144-119">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="e8144-120">Wartość domyślna to "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="e8144-120">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="e8144-121">issuerCertificateValidator</span><span class="sxs-lookup"><span data-stu-id="e8144-121">issuerCertificateValidator</span></span>|<span data-ttu-id="e8144-122">Typ niestandardowy, który pochodzi od <xref:System.IdentityModel.Selectors.X509CertificateValidator> .</span><span class="sxs-lookup"><span data-stu-id="e8144-122">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="e8144-123">Jeśli `issuerCertificateValidationMode` atrybut jest "Custom", wystąpienie tego typu jest używane na potrzeby walidacji certyfikatu wystawcy.</span><span class="sxs-lookup"><span data-stu-id="e8144-123">If the `issuerCertificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e8144-124">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e8144-124">Child Elements</span></span>  
  
|<span data-ttu-id="e8144-125">Element</span><span class="sxs-lookup"><span data-stu-id="e8144-125">Element</span></span>|<span data-ttu-id="e8144-126">Opis</span><span class="sxs-lookup"><span data-stu-id="e8144-126">Description</span></span>|  
|-------------|-----------------|  
|[\<nameClaimType>](nameclaimtype.md)|<span data-ttu-id="e8144-127">Ustawia typ zgłoszenia, który określa <xref:System.Security.Principal.IIdentity.Name%2A> Właściwość.</span><span class="sxs-lookup"><span data-stu-id="e8144-127">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span>|  
|[\<roleClaimType>](roleclaimtype.md)|<span data-ttu-id="e8144-128">Określa typ oświadczenia, który definiuje oświadczenia typu roli w kolekcji <xref:System.Security.Claims.ClaimsIdentity> obiektów zwracanych przez <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> metodę procedury obsługi tokenu.</span><span class="sxs-lookup"><span data-stu-id="e8144-128">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e8144-129">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e8144-129">Parent Elements</span></span>  
  
|<span data-ttu-id="e8144-130">Element</span><span class="sxs-lookup"><span data-stu-id="e8144-130">Element</span></span>|<span data-ttu-id="e8144-131">Opis</span><span class="sxs-lookup"><span data-stu-id="e8144-131">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add.md)|<span data-ttu-id="e8144-132">Dodaje określony program obsługi tokenów zabezpieczających do kolekcji obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="e8144-132">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e8144-133">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e8144-133">Remarks</span></span>  
 <span data-ttu-id="e8144-134">`<samlSecurityTokenRequirement>`Element jest reprezentowany przez <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> klasę w modelu obiektów i służy do konfigurowania `SamlSecurityTokenRequirement` właściwości w <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> lub <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> .</span><span class="sxs-lookup"><span data-stu-id="e8144-134">The `<samlSecurityTokenRequirement>` element is represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class in the object model and is used to configure the `SamlSecurityTokenRequirement` property on a <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> or a <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8144-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="e8144-135">Example</span></span>  
  
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
