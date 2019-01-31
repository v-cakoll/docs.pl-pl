---
title: <x509SecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: aca22c2c-5ae7-42af-9bbd-15c2524692ce
author: BrucePerlerMS
ms.openlocfilehash: 6e8267f170dbb26381564be7b66df5f617156885
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55271953"
---
# <a name="x509securitytokenhandlerrequirement"></a><span data-ttu-id="cbdfa-101">\<x509SecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="cbdfa-101">\<x509SecurityTokenHandlerRequirement></span></span>
<span data-ttu-id="cbdfa-102">Udostępnia konfigurację opcjonalne dla <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> klasy lub klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="cbdfa-102">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="cbdfa-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="cbdfa-103">\<system.identityModel></span></span>  
<span data-ttu-id="cbdfa-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="cbdfa-104">\<identityConfiguration></span></span>  
<span data-ttu-id="cbdfa-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="cbdfa-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="cbdfa-106">\<add></span><span class="sxs-lookup"><span data-stu-id="cbdfa-106">\<add></span></span>  
<span data-ttu-id="cbdfa-107">\<x509SecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="cbdfa-107">\<x509SecurityTokenHandlerRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbdfa-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="cbdfa-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cbdfa-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="cbdfa-109">Attributes and Elements</span></span>  
 <span data-ttu-id="cbdfa-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="cbdfa-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cbdfa-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="cbdfa-111">Attributes</span></span>  
  
|<span data-ttu-id="cbdfa-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="cbdfa-112">Attribute</span></span>|<span data-ttu-id="cbdfa-113">Opis</span><span class="sxs-lookup"><span data-stu-id="cbdfa-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cbdfa-114">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="cbdfa-114">certificateValidationMode</span></span>|<span data-ttu-id="cbdfa-115"><xref:System.ServiceModel.Security.X509CertificateValidationMode> Wartość, która określa tryb weryfikacji do użycia certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="cbdfa-115">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="cbdfa-116">Wartość domyślna to "PeerOrChainTrust".</span><span class="sxs-lookup"><span data-stu-id="cbdfa-116">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="cbdfa-117">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="cbdfa-117">mapToWindows</span></span>|<span data-ttu-id="cbdfa-118">Określa, czy programu obsługi tokenów powinny być mapowane sprawdzania poprawności tokenu z kontem Windows za pomocą przychodzące oświadczenia nazwy UPN.</span><span class="sxs-lookup"><span data-stu-id="cbdfa-118">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="cbdfa-119">Wartość domyślna to "false".</span><span class="sxs-lookup"><span data-stu-id="cbdfa-119">The default is "false".</span></span>|  
|<span data-ttu-id="cbdfa-120">revocationMode</span><span class="sxs-lookup"><span data-stu-id="cbdfa-120">revocationMode</span></span>|<span data-ttu-id="cbdfa-121"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> Wartość, która określa tryb odwołania dla certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="cbdfa-121">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="cbdfa-122">Wartość domyślna to "Online".</span><span class="sxs-lookup"><span data-stu-id="cbdfa-122">The default value is "Online".</span></span>|  
|<span data-ttu-id="cbdfa-123">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="cbdfa-123">trustedStoreLocation</span></span>|<span data-ttu-id="cbdfa-124">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> wartość, która określa magazynu certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="cbdfa-124">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="cbdfa-125">Wartość domyślna to "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="cbdfa-125">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="cbdfa-126">certificateValidator</span><span class="sxs-lookup"><span data-stu-id="cbdfa-126">certificateValidator</span></span>|<span data-ttu-id="cbdfa-127">Typ niestandardowy, który pochodzi od klasy <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="cbdfa-127">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="cbdfa-128">Jeśli `certificateValidationMode` atrybut jest "Niestandardowy", wystąpienia tego typu jest używany do walidacji certyfikatu wystawcy.</span><span class="sxs-lookup"><span data-stu-id="cbdfa-128">If the `certificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cbdfa-129">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="cbdfa-129">Child Elements</span></span>  
 <span data-ttu-id="cbdfa-130">Brak</span><span class="sxs-lookup"><span data-stu-id="cbdfa-130">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cbdfa-131">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="cbdfa-131">Parent Elements</span></span>  
  
|<span data-ttu-id="cbdfa-132">Element</span><span class="sxs-lookup"><span data-stu-id="cbdfa-132">Element</span></span>|<span data-ttu-id="cbdfa-133">Opis</span><span class="sxs-lookup"><span data-stu-id="cbdfa-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cbdfa-134">\<add></span><span class="sxs-lookup"><span data-stu-id="cbdfa-134">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="cbdfa-135">Programu obsługi tokenów zabezpieczeń określone są dodawane do kolekcji programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="cbdfa-135">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="cbdfa-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="cbdfa-136">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
    <x509SecurityTokenHandlerRequirement mapToWindows="true"   
                                         certificateValidationMode="PeerOrChainTrust"   
                                         revocationMode="Online"   
                                         trustedStoreLocation="LocalMachine" />  
</add>  
```
