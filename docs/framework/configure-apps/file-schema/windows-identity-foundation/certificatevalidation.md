---
title: '&lt;certificateValidation&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6c54c704-b55e-4631-88ff-4d4a5621554c
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 778088f2e0508f5a80c29ae027b2442a80286795
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ltcertificatevalidationgt"></a><span data-ttu-id="4bec9-102">&lt;certificateValidation&gt;</span><span class="sxs-lookup"><span data-stu-id="4bec9-102">&lt;certificateValidation&gt;</span></span>
<span data-ttu-id="4bec9-103">Określa ustawienia, które programy obsługi token służący do weryfikowania certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="4bec9-103">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="4bec9-104">Te ustawienia zostały zastąpione, jeśli określony program obsługi jest skonfigurowany z własnego modułu sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="4bec9-104">These settings are overridden if a specific handler is configured with its own validator.</span></span>  
  
 <span data-ttu-id="4bec9-105">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="4bec9-105">\<system.identityModel></span></span>  
<span data-ttu-id="4bec9-106">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="4bec9-106">\<identityConfiguration></span></span>  
<span data-ttu-id="4bec9-107">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="4bec9-107">\<certificateValidation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bec9-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="4bec9-108">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <certificateValidation  
      certificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
      revocationMode="NoCheck||Offline||Online"  
      trustedStoreLocation="CurrentLocation||LocalMachine" >  
    </certificateValidation>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4bec9-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4bec9-109">Attributes and Elements</span></span>  
 <span data-ttu-id="4bec9-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4bec9-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4bec9-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4bec9-111">Attributes</span></span>  
  
|<span data-ttu-id="4bec9-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4bec9-112">Attribute</span></span>|<span data-ttu-id="4bec9-113">Opis</span><span class="sxs-lookup"><span data-stu-id="4bec9-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4bec9-114">tryb certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="4bec9-114">certificateValidationMode</span></span>|<span data-ttu-id="4bec9-115"><xref:System.ServiceModel.Security.X509CertificateValidationMode> Wartość, która określa tryb walidacji do użycia na potrzeby certyfikatów X.509.</span><span class="sxs-lookup"><span data-stu-id="4bec9-115">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="4bec9-116">Wartość domyślna to "PeerOrChainTrust".</span><span class="sxs-lookup"><span data-stu-id="4bec9-116">The default value is "PeerOrChainTrust".</span></span> <span data-ttu-id="4bec9-117">Aby określić niestandardowego modułu weryfikacji, wartość tego atrybutu na "Custom", i określ modułu sprawdzania poprawności przy użyciu [ \<certificateValidator >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="4bec9-117">To specify a custom validator, set this attribute to "Custom" and specify the validator using the [\<certificateValidator>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md) element.</span></span> <span data-ttu-id="4bec9-118">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="4bec9-118">Optional.</span></span>|  
|<span data-ttu-id="4bec9-119">revocationMode</span><span class="sxs-lookup"><span data-stu-id="4bec9-119">revocationMode</span></span>|<span data-ttu-id="4bec9-120"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> Wartość, która określa tryb odwołania dla certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="4bec9-120">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="4bec9-121">Wartość domyślna to "Online".</span><span class="sxs-lookup"><span data-stu-id="4bec9-121">The default value is "Online".</span></span> <span data-ttu-id="4bec9-122">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="4bec9-122">Optional.</span></span>|  
|<span data-ttu-id="4bec9-123">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="4bec9-123">trustedStoreLocation</span></span>|<span data-ttu-id="4bec9-124">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> wartość, która określa magazynu certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="4bec9-124">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="4bec9-125">Wartością domyślną jest "Komputer lokalny".</span><span class="sxs-lookup"><span data-stu-id="4bec9-125">The default value is "LocalMachine".</span></span> <span data-ttu-id="4bec9-126">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="4bec9-126">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4bec9-127">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4bec9-127">Child Elements</span></span>  
  
|<span data-ttu-id="4bec9-128">Element</span><span class="sxs-lookup"><span data-stu-id="4bec9-128">Element</span></span>|<span data-ttu-id="4bec9-129">Opis</span><span class="sxs-lookup"><span data-stu-id="4bec9-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4bec9-130">\<certificateValidator ></span><span class="sxs-lookup"><span data-stu-id="4bec9-130">\<certificateValidator></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md)|<span data-ttu-id="4bec9-131">Określa typ niestandardowy o sprawdzenie poprawności certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="4bec9-131">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="4bec9-132">Ten typ jest używany tylko wtedy, gdy `certificateValidationMode` atrybutu [ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element jest ustawiony na "Custom".</span><span class="sxs-lookup"><span data-stu-id="4bec9-132">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element is set to "Custom".</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4bec9-133">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4bec9-133">Parent Elements</span></span>  
  
|<span data-ttu-id="4bec9-134">Element</span><span class="sxs-lookup"><span data-stu-id="4bec9-134">Element</span></span>|<span data-ttu-id="4bec9-135">Opis</span><span class="sxs-lookup"><span data-stu-id="4bec9-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4bec9-136">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="4bec9-136">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="4bec9-137">Określa ustawienia tożsamości poziomu usług.</span><span class="sxs-lookup"><span data-stu-id="4bec9-137">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="4bec9-138">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="4bec9-138">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="4bec9-139">Zapewnia token obsługi konfiguracji dla kolekcji zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="4bec9-139">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4bec9-140">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4bec9-140">Remarks</span></span>  
 <span data-ttu-id="4bec9-141">A `<certificateValidation>` elementu można określić na poziomie usługi pod `<identityConfiguration>` element lub na poziomie kolekcji programu obsługi tokenów zabezpieczeń w obszarze `<securityTokenHandlerConfiguration>` elementu.</span><span class="sxs-lookup"><span data-stu-id="4bec9-141">A `<certificateValidation>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="4bec9-142">Ustawienia w kolekcji programu obsługi tokenów zastępują ustawienia określone w usłudze.</span><span class="sxs-lookup"><span data-stu-id="4bec9-142">Settings on a token handler collection override those specified on the service.</span></span> <span data-ttu-id="4bec9-143">Niektóre obsługi tokenów umożliwiają określenie ustawienia sprawdzania poprawności certyfikatu w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="4bec9-143">Some token handlers allow you to specify certificate validation settings in configuration.</span></span> <span data-ttu-id="4bec9-144">Ustawienia dotyczące poszczególnych programu obsługi tokenów zastąpić określone, zarówno na poziomie usługi, jak i dla kolekcji programu obsługi tokenów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="4bec9-144">Settings on individual token handlers override those specified both at the service level and on the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4bec9-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="4bec9-145">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="PeerOrChainTrust"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine" />  
```
