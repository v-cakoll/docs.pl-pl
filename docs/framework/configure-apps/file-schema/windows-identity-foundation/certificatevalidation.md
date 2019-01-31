---
title: <certificateValidation>
ms.date: 03/30/2017
ms.assetid: 6c54c704-b55e-4631-88ff-4d4a5621554c
author: BrucePerlerMS
ms.openlocfilehash: 7b8823d792e3f15846a9483d670994be4b368980
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55273900"
---
# <a name="certificatevalidation"></a><span data-ttu-id="e3140-101">\<certificateValidation></span><span class="sxs-lookup"><span data-stu-id="e3140-101">\<certificateValidation></span></span>
<span data-ttu-id="e3140-102">Określa ustawienia, które programy obsługi tokenów służący do weryfikowania certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="e3140-102">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="e3140-103">Te ustawienia zostaną zastąpione, jeśli określony program obsługi jest skonfigurowany przy użyciu własnego modułu sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="e3140-103">These settings are overridden if a specific handler is configured with its own validator.</span></span>  
  
 <span data-ttu-id="e3140-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="e3140-104">\<system.identityModel></span></span>  
<span data-ttu-id="e3140-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="e3140-105">\<identityConfiguration></span></span>  
<span data-ttu-id="e3140-106">\<certificateValidation></span><span class="sxs-lookup"><span data-stu-id="e3140-106">\<certificateValidation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3140-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="e3140-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e3140-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e3140-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e3140-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e3140-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e3140-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e3140-110">Attributes</span></span>  
  
|<span data-ttu-id="e3140-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e3140-111">Attribute</span></span>|<span data-ttu-id="e3140-112">Opis</span><span class="sxs-lookup"><span data-stu-id="e3140-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e3140-113">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="e3140-113">certificateValidationMode</span></span>|<span data-ttu-id="e3140-114"><xref:System.ServiceModel.Security.X509CertificateValidationMode> Wartość, która określa tryb weryfikacji do użycia certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="e3140-114">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="e3140-115">Wartość domyślna to "PeerOrChainTrust".</span><span class="sxs-lookup"><span data-stu-id="e3140-115">The default value is "PeerOrChainTrust".</span></span> <span data-ttu-id="e3140-116">Aby określić niestandardowy moduł sprawdzania poprawności, należy ustawić tego atrybutu na "Niestandardowe", a następnie określ weryfikacji za pomocą [ \<certificateValidator >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="e3140-116">To specify a custom validator, set this attribute to "Custom" and specify the validator using the [\<certificateValidator>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md) element.</span></span> <span data-ttu-id="e3140-117">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="e3140-117">Optional.</span></span>|  
|<span data-ttu-id="e3140-118">revocationMode</span><span class="sxs-lookup"><span data-stu-id="e3140-118">revocationMode</span></span>|<span data-ttu-id="e3140-119"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> Wartość, która określa tryb odwołania dla certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="e3140-119">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="e3140-120">Wartość domyślna to "Online".</span><span class="sxs-lookup"><span data-stu-id="e3140-120">The default value is "Online".</span></span> <span data-ttu-id="e3140-121">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="e3140-121">Optional.</span></span>|  
|<span data-ttu-id="e3140-122">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="e3140-122">trustedStoreLocation</span></span>|<span data-ttu-id="e3140-123">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> wartość, która określa magazynu certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="e3140-123">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="e3140-124">Wartość domyślna to "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="e3140-124">The default value is "LocalMachine".</span></span> <span data-ttu-id="e3140-125">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="e3140-125">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e3140-126">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e3140-126">Child Elements</span></span>  
  
|<span data-ttu-id="e3140-127">Element</span><span class="sxs-lookup"><span data-stu-id="e3140-127">Element</span></span>|<span data-ttu-id="e3140-128">Opis</span><span class="sxs-lookup"><span data-stu-id="e3140-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e3140-129">\<certificateValidator></span><span class="sxs-lookup"><span data-stu-id="e3140-129">\<certificateValidator></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md)|<span data-ttu-id="e3140-130">Określa typ niestandardowy do weryfikacji certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="e3140-130">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="e3140-131">Ten typ jest używany tylko wtedy, gdy `certificateValidationMode` atrybutu [ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element jest ustawiony na "Niestandardowe".</span><span class="sxs-lookup"><span data-stu-id="e3140-131">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element is set to "Custom".</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e3140-132">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e3140-132">Parent Elements</span></span>  
  
|<span data-ttu-id="e3140-133">Element</span><span class="sxs-lookup"><span data-stu-id="e3140-133">Element</span></span>|<span data-ttu-id="e3140-134">Opis</span><span class="sxs-lookup"><span data-stu-id="e3140-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e3140-135">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="e3140-135">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="e3140-136">Określa ustawienia tożsamości na poziomie usługi.</span><span class="sxs-lookup"><span data-stu-id="e3140-136">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="e3140-137">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="e3140-137">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="e3140-138">Udostępnia konfigurację dla kolekcji zabezpieczeń programy obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="e3140-138">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e3140-139">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e3140-139">Remarks</span></span>  
 <span data-ttu-id="e3140-140">A `<certificateValidation>` element może być określony na poziomie usługi w ramach `<identityConfiguration>` element lub na poziomie kolekcji programu obsługi tokenów zabezpieczeń w ramach `<securityTokenHandlerConfiguration>` elementu.</span><span class="sxs-lookup"><span data-stu-id="e3140-140">A `<certificateValidation>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="e3140-141">Ustawienia w kolekcji programu obsługi tokenów zastępują ustawienia określone w usłudze.</span><span class="sxs-lookup"><span data-stu-id="e3140-141">Settings on a token handler collection override those specified on the service.</span></span> <span data-ttu-id="e3140-142">Niektóre programy obsługi tokenów umożliwiają określanie ustawień weryfikacji certyfikatów w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e3140-142">Some token handlers allow you to specify certificate validation settings in configuration.</span></span> <span data-ttu-id="e3140-143">Ustawienia dotyczące programu obsługi tokenów poszczególnych zastąpienia określone, zarówno na poziomie usługi, jak i w kolekcji programu obsługi tokenów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="e3140-143">Settings on individual token handlers override those specified both at the service level and on the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3140-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="e3140-144">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="PeerOrChainTrust"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine" />  
```
