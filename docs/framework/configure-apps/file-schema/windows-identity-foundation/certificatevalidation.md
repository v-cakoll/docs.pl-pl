---
title: '&lt;certificateValidation&gt;'
ms.date: 03/30/2017
ms.assetid: 6c54c704-b55e-4631-88ff-4d4a5621554c
author: BrucePerlerMS
ms.openlocfilehash: 29881be43f02d275ad135efd97dc8b25a7409beb
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47074791"
---
# <a name="ltcertificatevalidationgt"></a><span data-ttu-id="1fb7f-102">&lt;certificateValidation&gt;</span><span class="sxs-lookup"><span data-stu-id="1fb7f-102">&lt;certificateValidation&gt;</span></span>
<span data-ttu-id="1fb7f-103">Określa ustawienia, które programy obsługi tokenów służący do weryfikowania certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="1fb7f-103">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="1fb7f-104">Te ustawienia zostaną zastąpione, jeśli określony program obsługi jest skonfigurowany przy użyciu własnego modułu sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="1fb7f-104">These settings are overridden if a specific handler is configured with its own validator.</span></span>  
  
 <span data-ttu-id="1fb7f-105">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="1fb7f-105">\<system.identityModel></span></span>  
<span data-ttu-id="1fb7f-106">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="1fb7f-106">\<identityConfiguration></span></span>  
<span data-ttu-id="1fb7f-107">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="1fb7f-107">\<certificateValidation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fb7f-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="1fb7f-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1fb7f-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1fb7f-109">Attributes and Elements</span></span>  
 <span data-ttu-id="1fb7f-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1fb7f-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1fb7f-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1fb7f-111">Attributes</span></span>  
  
|<span data-ttu-id="1fb7f-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="1fb7f-112">Attribute</span></span>|<span data-ttu-id="1fb7f-113">Opis</span><span class="sxs-lookup"><span data-stu-id="1fb7f-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1fb7f-114">tryb certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="1fb7f-114">certificateValidationMode</span></span>|<span data-ttu-id="1fb7f-115"><xref:System.ServiceModel.Security.X509CertificateValidationMode> Wartość, która określa tryb weryfikacji do użycia certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="1fb7f-115">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="1fb7f-116">Wartość domyślna to "PeerOrChainTrust".</span><span class="sxs-lookup"><span data-stu-id="1fb7f-116">The default value is "PeerOrChainTrust".</span></span> <span data-ttu-id="1fb7f-117">Aby określić niestandardowy moduł sprawdzania poprawności, należy ustawić tego atrybutu na "Niestandardowe", a następnie określ weryfikacji za pomocą [ \<certificateValidator >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="1fb7f-117">To specify a custom validator, set this attribute to "Custom" and specify the validator using the [\<certificateValidator>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md) element.</span></span> <span data-ttu-id="1fb7f-118">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="1fb7f-118">Optional.</span></span>|  
|<span data-ttu-id="1fb7f-119">revocationMode</span><span class="sxs-lookup"><span data-stu-id="1fb7f-119">revocationMode</span></span>|<span data-ttu-id="1fb7f-120"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> Wartość, która określa tryb odwołania dla certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="1fb7f-120">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="1fb7f-121">Wartość domyślna to "Online".</span><span class="sxs-lookup"><span data-stu-id="1fb7f-121">The default value is "Online".</span></span> <span data-ttu-id="1fb7f-122">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="1fb7f-122">Optional.</span></span>|  
|<span data-ttu-id="1fb7f-123">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="1fb7f-123">trustedStoreLocation</span></span>|<span data-ttu-id="1fb7f-124">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> wartość, która określa magazynu certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="1fb7f-124">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="1fb7f-125">Wartość domyślna to "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="1fb7f-125">The default value is "LocalMachine".</span></span> <span data-ttu-id="1fb7f-126">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="1fb7f-126">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1fb7f-127">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1fb7f-127">Child Elements</span></span>  
  
|<span data-ttu-id="1fb7f-128">Element</span><span class="sxs-lookup"><span data-stu-id="1fb7f-128">Element</span></span>|<span data-ttu-id="1fb7f-129">Opis</span><span class="sxs-lookup"><span data-stu-id="1fb7f-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1fb7f-130">\<certificateValidator ></span><span class="sxs-lookup"><span data-stu-id="1fb7f-130">\<certificateValidator></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md)|<span data-ttu-id="1fb7f-131">Określa typ niestandardowy do weryfikacji certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="1fb7f-131">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="1fb7f-132">Ten typ jest używany tylko wtedy, gdy `certificateValidationMode` atrybutu [ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element jest ustawiony na "Niestandardowe".</span><span class="sxs-lookup"><span data-stu-id="1fb7f-132">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element is set to "Custom".</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1fb7f-133">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1fb7f-133">Parent Elements</span></span>  
  
|<span data-ttu-id="1fb7f-134">Element</span><span class="sxs-lookup"><span data-stu-id="1fb7f-134">Element</span></span>|<span data-ttu-id="1fb7f-135">Opis</span><span class="sxs-lookup"><span data-stu-id="1fb7f-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1fb7f-136">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="1fb7f-136">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="1fb7f-137">Określa ustawienia tożsamości na poziomie usługi.</span><span class="sxs-lookup"><span data-stu-id="1fb7f-137">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="1fb7f-138">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="1fb7f-138">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="1fb7f-139">Udostępnia konfigurację dla kolekcji zabezpieczeń programy obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="1fb7f-139">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1fb7f-140">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1fb7f-140">Remarks</span></span>  
 <span data-ttu-id="1fb7f-141">A `<certificateValidation>` element może być określony na poziomie usługi w ramach `<identityConfiguration>` element lub na poziomie kolekcji programu obsługi tokenów zabezpieczeń w ramach `<securityTokenHandlerConfiguration>` elementu.</span><span class="sxs-lookup"><span data-stu-id="1fb7f-141">A `<certificateValidation>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="1fb7f-142">Ustawienia w kolekcji programu obsługi tokenów zastępują ustawienia określone w usłudze.</span><span class="sxs-lookup"><span data-stu-id="1fb7f-142">Settings on a token handler collection override those specified on the service.</span></span> <span data-ttu-id="1fb7f-143">Niektóre programy obsługi tokenów umożliwiają określanie ustawień weryfikacji certyfikatów w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="1fb7f-143">Some token handlers allow you to specify certificate validation settings in configuration.</span></span> <span data-ttu-id="1fb7f-144">Ustawienia dotyczące programu obsługi tokenów poszczególnych zastąpienia określone, zarówno na poziomie usługi, jak i w kolekcji programu obsługi tokenów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="1fb7f-144">Settings on individual token handlers override those specified both at the service level and on the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1fb7f-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="1fb7f-145">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="PeerOrChainTrust"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine" />  
```
