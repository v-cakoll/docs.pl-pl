---
title: '&lt;x509SecurityTokenHandlerRequirement&gt;'
ms.date: 03/30/2017
ms.assetid: aca22c2c-5ae7-42af-9bbd-15c2524692ce
author: BrucePerlerMS
ms.openlocfilehash: 994677904cada71dbc7cce4b6ca0de1d4dc65014
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47085666"
---
# <a name="ltx509securitytokenhandlerrequirementgt"></a><span data-ttu-id="4b154-102">&lt;x509SecurityTokenHandlerRequirement&gt;</span><span class="sxs-lookup"><span data-stu-id="4b154-102">&lt;x509SecurityTokenHandlerRequirement&gt;</span></span>
<span data-ttu-id="4b154-103">Udostępnia konfigurację opcjonalne dla <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> klasy lub klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="4b154-103">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="4b154-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="4b154-104">\<system.identityModel></span></span>  
<span data-ttu-id="4b154-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="4b154-105">\<identityConfiguration></span></span>  
<span data-ttu-id="4b154-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="4b154-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="4b154-107">\<add></span><span class="sxs-lookup"><span data-stu-id="4b154-107">\<add></span></span>  
<span data-ttu-id="4b154-108">\<x509SecurityTokenHandlerRequirement ></span><span class="sxs-lookup"><span data-stu-id="4b154-108">\<x509SecurityTokenHandlerRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b154-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="4b154-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4b154-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4b154-110">Attributes and Elements</span></span>  
 <span data-ttu-id="4b154-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4b154-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4b154-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4b154-112">Attributes</span></span>  
  
|<span data-ttu-id="4b154-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4b154-113">Attribute</span></span>|<span data-ttu-id="4b154-114">Opis</span><span class="sxs-lookup"><span data-stu-id="4b154-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4b154-115">tryb certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="4b154-115">certificateValidationMode</span></span>|<span data-ttu-id="4b154-116"><xref:System.ServiceModel.Security.X509CertificateValidationMode> Wartość, która określa tryb weryfikacji do użycia certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="4b154-116">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="4b154-117">Wartość domyślna to "PeerOrChainTrust".</span><span class="sxs-lookup"><span data-stu-id="4b154-117">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="4b154-118">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="4b154-118">mapToWindows</span></span>|<span data-ttu-id="4b154-119">Określa, czy programu obsługi tokenów powinny być mapowane sprawdzania poprawności tokenu z kontem Windows za pomocą przychodzące oświadczenia nazwy UPN.</span><span class="sxs-lookup"><span data-stu-id="4b154-119">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="4b154-120">Wartość domyślna to "false".</span><span class="sxs-lookup"><span data-stu-id="4b154-120">The default is "false".</span></span>|  
|<span data-ttu-id="4b154-121">revocationMode</span><span class="sxs-lookup"><span data-stu-id="4b154-121">revocationMode</span></span>|<span data-ttu-id="4b154-122"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> Wartość, która określa tryb odwołania dla certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="4b154-122">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="4b154-123">Wartość domyślna to "Online".</span><span class="sxs-lookup"><span data-stu-id="4b154-123">The default value is "Online".</span></span>|  
|<span data-ttu-id="4b154-124">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="4b154-124">trustedStoreLocation</span></span>|<span data-ttu-id="4b154-125">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> wartość, która określa magazynu certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="4b154-125">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="4b154-126">Wartość domyślna to "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="4b154-126">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="4b154-127">certificateValidator</span><span class="sxs-lookup"><span data-stu-id="4b154-127">certificateValidator</span></span>|<span data-ttu-id="4b154-128">Typ niestandardowy, który pochodzi od klasy <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="4b154-128">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="4b154-129">Jeśli `certificateValidationMode` atrybut jest "Niestandardowy", wystąpienia tego typu jest używany do walidacji certyfikatu wystawcy.</span><span class="sxs-lookup"><span data-stu-id="4b154-129">If the `certificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4b154-130">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4b154-130">Child Elements</span></span>  
 <span data-ttu-id="4b154-131">Brak</span><span class="sxs-lookup"><span data-stu-id="4b154-131">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4b154-132">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4b154-132">Parent Elements</span></span>  
  
|<span data-ttu-id="4b154-133">Element</span><span class="sxs-lookup"><span data-stu-id="4b154-133">Element</span></span>|<span data-ttu-id="4b154-134">Opis</span><span class="sxs-lookup"><span data-stu-id="4b154-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4b154-135">\<add></span><span class="sxs-lookup"><span data-stu-id="4b154-135">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="4b154-136">Programu obsługi tokenów zabezpieczeń określone są dodawane do kolekcji programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="4b154-136">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="4b154-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="4b154-137">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
    <x509SecurityTokenHandlerRequirement mapToWindows="true"   
                                         certificateValidationMode="PeerOrChainTrust"   
                                         revocationMode="Online"   
                                         trustedStoreLocation="LocalMachine" />  
</add>  
```
