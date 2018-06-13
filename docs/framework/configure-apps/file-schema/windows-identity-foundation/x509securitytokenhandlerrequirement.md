---
title: '&lt;x509SecurityTokenHandlerRequirement&gt;'
ms.date: 03/30/2017
ms.assetid: aca22c2c-5ae7-42af-9bbd-15c2524692ce
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 8af4a718fc9f4ba7f674d98e13424bb443693c6c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32755945"
---
# <a name="ltx509securitytokenhandlerrequirementgt"></a><span data-ttu-id="45965-102">&lt;x509SecurityTokenHandlerRequirement&gt;</span><span class="sxs-lookup"><span data-stu-id="45965-102">&lt;x509SecurityTokenHandlerRequirement&gt;</span></span>
<span data-ttu-id="45965-103">Zapewnia opcjonalne konfigurację <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> klasy lub klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="45965-103">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="45965-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="45965-104">\<system.identityModel></span></span>  
<span data-ttu-id="45965-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="45965-105">\<identityConfiguration></span></span>  
<span data-ttu-id="45965-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="45965-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="45965-107">\<add></span><span class="sxs-lookup"><span data-stu-id="45965-107">\<add></span></span>  
<span data-ttu-id="45965-108">\<x509SecurityTokenHandlerRequirement ></span><span class="sxs-lookup"><span data-stu-id="45965-108">\<x509SecurityTokenHandlerRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45965-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="45965-109">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
        <x509SecurityTokenHandlerRequirement>  
          mapToWindows=xs:boolean  
          certificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
          certificateValidator="Namespace.Class, Assembly"  
          revocationMode="NoCheck||Offline||Online"  
          trustedStoreLocation="CurrentUser||LocalMachine"  
        </x509SecurityTokenHandlerRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="45965-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="45965-110">Attributes and Elements</span></span>  
 <span data-ttu-id="45965-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="45965-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="45965-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="45965-112">Attributes</span></span>  
  
|<span data-ttu-id="45965-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="45965-113">Attribute</span></span>|<span data-ttu-id="45965-114">Opis</span><span class="sxs-lookup"><span data-stu-id="45965-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="45965-115">tryb certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="45965-115">certificateValidationMode</span></span>|<span data-ttu-id="45965-116"><xref:System.ServiceModel.Security.X509CertificateValidationMode> Wartość, która określa tryb walidacji do użycia na potrzeby certyfikatów X.509.</span><span class="sxs-lookup"><span data-stu-id="45965-116">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="45965-117">Wartość domyślna to "PeerOrChainTrust".</span><span class="sxs-lookup"><span data-stu-id="45965-117">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="45965-118">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="45965-118">mapToWindows</span></span>|<span data-ttu-id="45965-119">Określa, czy programu obsługi tokenów należy mapować sprawdzania poprawności tokenu konto systemu Windows przy użyciu nazwy UPN oświadczenia przychodzącego.</span><span class="sxs-lookup"><span data-stu-id="45965-119">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="45965-120">Wartość domyślna to "false".</span><span class="sxs-lookup"><span data-stu-id="45965-120">The default is "false".</span></span>|  
|<span data-ttu-id="45965-121">revocationMode</span><span class="sxs-lookup"><span data-stu-id="45965-121">revocationMode</span></span>|<span data-ttu-id="45965-122"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> Wartość, która określa tryb odwołania dla certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="45965-122">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="45965-123">Wartość domyślna to "Online".</span><span class="sxs-lookup"><span data-stu-id="45965-123">The default value is "Online".</span></span>|  
|<span data-ttu-id="45965-124">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="45965-124">trustedStoreLocation</span></span>|<span data-ttu-id="45965-125">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> wartość, która określa magazynu certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="45965-125">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="45965-126">Wartością domyślną jest "Komputer lokalny".</span><span class="sxs-lookup"><span data-stu-id="45965-126">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="45965-127">certificateValidator</span><span class="sxs-lookup"><span data-stu-id="45965-127">certificateValidator</span></span>|<span data-ttu-id="45965-128">Typ niestandardowy, która jest pochodną <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="45965-128">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="45965-129">Jeśli `certificateValidationMode` atrybutu jest "Custom", wystąpienie tego typu jest używany do sprawdzania poprawności wystawcy certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="45965-129">If the `certificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="45965-130">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="45965-130">Child Elements</span></span>  
 <span data-ttu-id="45965-131">Brak</span><span class="sxs-lookup"><span data-stu-id="45965-131">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="45965-132">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="45965-132">Parent Elements</span></span>  
  
|<span data-ttu-id="45965-133">Element</span><span class="sxs-lookup"><span data-stu-id="45965-133">Element</span></span>|<span data-ttu-id="45965-134">Opis</span><span class="sxs-lookup"><span data-stu-id="45965-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="45965-135">\<add></span><span class="sxs-lookup"><span data-stu-id="45965-135">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="45965-136">Dodaje określony zabezpieczenia programu obsługi tokenów do kolekcji programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="45965-136">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="45965-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="45965-137">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
    <x509SecurityTokenHandlerRequirement mapToWindows="true"   
                                         certificateValidationMode="PeerOrChainTrust"   
                                         revocationMode="Online"   
                                         trustedStoreLocation="LocalMachine" />  
</add>  
```
