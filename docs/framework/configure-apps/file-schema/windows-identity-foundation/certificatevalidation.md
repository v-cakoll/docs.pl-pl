---
title: <certificateValidation>
ms.date: 03/30/2017
ms.assetid: 6c54c704-b55e-4631-88ff-4d4a5621554c
author: BrucePerlerMS
ms.openlocfilehash: 8185153eb02c5794b0f6ac02a6837806f2073c07
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941920"
---
# <a name="certificatevalidation"></a><span data-ttu-id="41853-101">\<certificateValidation></span><span class="sxs-lookup"><span data-stu-id="41853-101">\<certificateValidation></span></span>
<span data-ttu-id="41853-102">Kontroluje ustawienia używane przez programy obsługi do sprawdzania poprawności certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="41853-102">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="41853-103">Te ustawienia są zastępowane, jeśli określony program obsługi jest skonfigurowany przy użyciu własnego modułu sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="41853-103">These settings are overridden if a specific handler is configured with its own validator.</span></span>  
  
 <span data-ttu-id="41853-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="41853-104">\<system.identityModel></span></span>  
<span data-ttu-id="41853-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="41853-105">\<identityConfiguration></span></span>  
<span data-ttu-id="41853-106">\<certificateValidation></span><span class="sxs-lookup"><span data-stu-id="41853-106">\<certificateValidation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41853-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="41853-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="41853-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="41853-108">Attributes and Elements</span></span>  
 <span data-ttu-id="41853-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="41853-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="41853-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="41853-110">Attributes</span></span>  
  
|<span data-ttu-id="41853-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="41853-111">Attribute</span></span>|<span data-ttu-id="41853-112">Opis</span><span class="sxs-lookup"><span data-stu-id="41853-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="41853-113">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="41853-113">certificateValidationMode</span></span>|<span data-ttu-id="41853-114"><xref:System.ServiceModel.Security.X509CertificateValidationMode> Wartość określająca tryb walidacji, który ma być używany dla certyfikatu X. 509.</span><span class="sxs-lookup"><span data-stu-id="41853-114">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="41853-115">Wartość domyślna to "PeerOrChainTrust".</span><span class="sxs-lookup"><span data-stu-id="41853-115">The default value is "PeerOrChainTrust".</span></span> <span data-ttu-id="41853-116">Aby określić niestandardowy moduł sprawdzania poprawności, ustaw ten atrybut na "niestandardowy" i określ moduł walidacji przy użyciu [ \<elementu certificateValidator >](certificatevalidator.md) .</span><span class="sxs-lookup"><span data-stu-id="41853-116">To specify a custom validator, set this attribute to "Custom" and specify the validator using the [\<certificateValidator>](certificatevalidator.md) element.</span></span> <span data-ttu-id="41853-117">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="41853-117">Optional.</span></span>|  
|<span data-ttu-id="41853-118">odwołaniemode</span><span class="sxs-lookup"><span data-stu-id="41853-118">revocationMode</span></span>|<span data-ttu-id="41853-119"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> Wartość określająca tryb odwołania, który ma być używany dla certyfikatu X. 509.</span><span class="sxs-lookup"><span data-stu-id="41853-119">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="41853-120">Wartość domyślna to "online".</span><span class="sxs-lookup"><span data-stu-id="41853-120">The default value is "Online".</span></span> <span data-ttu-id="41853-121">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="41853-121">Optional.</span></span>|  
|<span data-ttu-id="41853-122">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="41853-122">trustedStoreLocation</span></span>|<span data-ttu-id="41853-123"><xref:System.Security.Cryptography.X509Certificates.StoreLocation> Wartość określająca magazyn certyfikatów X. 509.</span><span class="sxs-lookup"><span data-stu-id="41853-123">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="41853-124">Wartość domyślna to "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="41853-124">The default value is "LocalMachine".</span></span> <span data-ttu-id="41853-125">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="41853-125">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="41853-126">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="41853-126">Child Elements</span></span>  
  
|<span data-ttu-id="41853-127">Element</span><span class="sxs-lookup"><span data-stu-id="41853-127">Element</span></span>|<span data-ttu-id="41853-128">Opis</span><span class="sxs-lookup"><span data-stu-id="41853-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="41853-129">\<certificateValidator ></span><span class="sxs-lookup"><span data-stu-id="41853-129">\<certificateValidator></span></span>](certificatevalidator.md)|<span data-ttu-id="41853-130">Określa typ niestandardowy na potrzeby walidacji certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="41853-130">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="41853-131">Ten typ jest używany tylko wtedy, `certificateValidationMode` gdy atrybut [ \<elementu certificateValidation >](certificatevalidation.md) jest ustawiony na wartość "Custom".</span><span class="sxs-lookup"><span data-stu-id="41853-131">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element is set to "Custom".</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="41853-132">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="41853-132">Parent Elements</span></span>  
  
|<span data-ttu-id="41853-133">Element</span><span class="sxs-lookup"><span data-stu-id="41853-133">Element</span></span>|<span data-ttu-id="41853-134">Opis</span><span class="sxs-lookup"><span data-stu-id="41853-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="41853-135">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="41853-135">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="41853-136">Określa ustawienia tożsamości na poziomie usług.</span><span class="sxs-lookup"><span data-stu-id="41853-136">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="41853-137">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="41853-137">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="41853-138">Zapewnia konfigurację kolekcji programów obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="41853-138">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="41853-139">Uwagi</span><span class="sxs-lookup"><span data-stu-id="41853-139">Remarks</span></span>  
 <span data-ttu-id="41853-140">Element można określić na poziomie usługi `<identityConfiguration>` pod elementem lub na poziomie kolekcji `<securityTokenHandlerConfiguration>` programu obsługi tokenów zabezpieczających w ramach elementu. `<certificateValidation>`</span><span class="sxs-lookup"><span data-stu-id="41853-140">A `<certificateValidation>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="41853-141">Ustawienia w kolekcji obsługi tokenów zastępują te określone w usłudze.</span><span class="sxs-lookup"><span data-stu-id="41853-141">Settings on a token handler collection override those specified on the service.</span></span> <span data-ttu-id="41853-142">Niektóre programy obsługi tokenów umożliwiają określanie ustawień weryfikacji certyfikatu w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="41853-142">Some token handlers allow you to specify certificate validation settings in configuration.</span></span> <span data-ttu-id="41853-143">Ustawienia poszczególnych programów obsługi tokenów przesłaniają te określone zarówno na poziomie usługi, jak i w kolekcji obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="41853-143">Settings on individual token handlers override those specified both at the service level and on the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="41853-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="41853-144">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="PeerOrChainTrust"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine" />  
```
