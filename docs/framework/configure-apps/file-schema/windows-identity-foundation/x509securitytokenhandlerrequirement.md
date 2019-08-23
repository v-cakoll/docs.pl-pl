---
title: <x509SecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: aca22c2c-5ae7-42af-9bbd-15c2524692ce
author: BrucePerlerMS
ms.openlocfilehash: 2851820460a34d62175929b48ad57914df557059
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945181"
---
# <a name="x509securitytokenhandlerrequirement"></a><span data-ttu-id="35c40-101">\<x509SecurityTokenHandlerRequirement ></span><span class="sxs-lookup"><span data-stu-id="35c40-101">\<x509SecurityTokenHandlerRequirement></span></span>
<span data-ttu-id="35c40-102">Zapewnia opcjonalną konfigurację <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> klasy lub klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="35c40-102">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="35c40-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="35c40-103">\<system.identityModel></span></span>  
<span data-ttu-id="35c40-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="35c40-104">\<identityConfiguration></span></span>  
<span data-ttu-id="35c40-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="35c40-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="35c40-106">\<add></span><span class="sxs-lookup"><span data-stu-id="35c40-106">\<add></span></span>  
<span data-ttu-id="35c40-107">\<x509SecurityTokenHandlerRequirement ></span><span class="sxs-lookup"><span data-stu-id="35c40-107">\<x509SecurityTokenHandlerRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35c40-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="35c40-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="35c40-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="35c40-109">Attributes and Elements</span></span>  
 <span data-ttu-id="35c40-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="35c40-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="35c40-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="35c40-111">Attributes</span></span>  
  
|<span data-ttu-id="35c40-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="35c40-112">Attribute</span></span>|<span data-ttu-id="35c40-113">Opis</span><span class="sxs-lookup"><span data-stu-id="35c40-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="35c40-114">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="35c40-114">certificateValidationMode</span></span>|<span data-ttu-id="35c40-115"><xref:System.ServiceModel.Security.X509CertificateValidationMode> Wartość określająca tryb walidacji, który ma być używany dla certyfikatu X. 509.</span><span class="sxs-lookup"><span data-stu-id="35c40-115">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="35c40-116">Wartość domyślna to "PeerOrChainTrust".</span><span class="sxs-lookup"><span data-stu-id="35c40-116">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="35c40-117">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="35c40-117">mapToWindows</span></span>|<span data-ttu-id="35c40-118">Określa, czy program obsługi tokenów powinien mapować token walidacji na konto systemu Windows przy użyciu przychodzącego oświadczenie nazwy UPN.</span><span class="sxs-lookup"><span data-stu-id="35c40-118">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="35c40-119">Wartość domyślna to "false".</span><span class="sxs-lookup"><span data-stu-id="35c40-119">The default is "false".</span></span>|  
|<span data-ttu-id="35c40-120">odwołaniemode</span><span class="sxs-lookup"><span data-stu-id="35c40-120">revocationMode</span></span>|<span data-ttu-id="35c40-121"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> Wartość określająca tryb odwołania, który ma być używany dla certyfikatu X. 509.</span><span class="sxs-lookup"><span data-stu-id="35c40-121">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="35c40-122">Wartość domyślna to "online".</span><span class="sxs-lookup"><span data-stu-id="35c40-122">The default value is "Online".</span></span>|  
|<span data-ttu-id="35c40-123">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="35c40-123">trustedStoreLocation</span></span>|<span data-ttu-id="35c40-124"><xref:System.Security.Cryptography.X509Certificates.StoreLocation> Wartość określająca magazyn certyfikatów X. 509.</span><span class="sxs-lookup"><span data-stu-id="35c40-124">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="35c40-125">Wartość domyślna to "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="35c40-125">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="35c40-126">certificateValidator</span><span class="sxs-lookup"><span data-stu-id="35c40-126">certificateValidator</span></span>|<span data-ttu-id="35c40-127">Typ niestandardowy, który pochodzi od <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="35c40-127">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="35c40-128">`certificateValidationMode` Jeśli atrybut jest "Custom", wystąpienie tego typu jest używane na potrzeby walidacji certyfikatu wystawcy.</span><span class="sxs-lookup"><span data-stu-id="35c40-128">If the `certificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="35c40-129">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="35c40-129">Child Elements</span></span>  
 <span data-ttu-id="35c40-130">Brak</span><span class="sxs-lookup"><span data-stu-id="35c40-130">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="35c40-131">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="35c40-131">Parent Elements</span></span>  
  
|<span data-ttu-id="35c40-132">Element</span><span class="sxs-lookup"><span data-stu-id="35c40-132">Element</span></span>|<span data-ttu-id="35c40-133">Opis</span><span class="sxs-lookup"><span data-stu-id="35c40-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="35c40-134">\<add></span><span class="sxs-lookup"><span data-stu-id="35c40-134">\<add></span></span>](add.md)|<span data-ttu-id="35c40-135">Dodaje określony program obsługi tokenów zabezpieczających do kolekcji obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="35c40-135">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="35c40-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="35c40-136">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
    <x509SecurityTokenHandlerRequirement mapToWindows="true"   
                                         certificateValidationMode="PeerOrChainTrust"   
                                         revocationMode="Online"   
                                         trustedStoreLocation="LocalMachine" />  
</add>  
```
