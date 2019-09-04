---
title: <certificateValidation>
ms.date: 03/30/2017
ms.assetid: 6c54c704-b55e-4631-88ff-4d4a5621554c
author: BrucePerlerMS
ms.openlocfilehash: c2d1a5d36cb5616ef06eedc093dd70a68a164a81
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252139"
---
# <a name="certificatevalidation"></a><span data-ttu-id="d872b-101">\<certificateValidation></span><span class="sxs-lookup"><span data-stu-id="d872b-101">\<certificateValidation></span></span>
<span data-ttu-id="d872b-102">Kontroluje ustawienia używane przez programy obsługi do sprawdzania poprawności certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="d872b-102">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="d872b-103">Te ustawienia są zastępowane, jeśli określony program obsługi jest skonfigurowany przy użyciu własnego modułu sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="d872b-103">These settings are overridden if a specific handler is configured with its own validator.</span></span>  
  
<span data-ttu-id="d872b-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d872b-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d872b-105">&nbsp;&nbsp;[ **\<> System. identityModel**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="d872b-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="d872b-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="d872b-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="d872b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<certificateValidation >**</span><span class="sxs-lookup"><span data-stu-id="d872b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateValidation>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d872b-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="d872b-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d872b-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d872b-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d872b-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d872b-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d872b-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d872b-111">Attributes</span></span>  
  
|<span data-ttu-id="d872b-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d872b-112">Attribute</span></span>|<span data-ttu-id="d872b-113">Opis</span><span class="sxs-lookup"><span data-stu-id="d872b-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d872b-114">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="d872b-114">certificateValidationMode</span></span>|<span data-ttu-id="d872b-115"><xref:System.ServiceModel.Security.X509CertificateValidationMode> Wartość określająca tryb walidacji, który ma być używany dla certyfikatu X. 509.</span><span class="sxs-lookup"><span data-stu-id="d872b-115">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="d872b-116">Wartość domyślna to "PeerOrChainTrust".</span><span class="sxs-lookup"><span data-stu-id="d872b-116">The default value is "PeerOrChainTrust".</span></span> <span data-ttu-id="d872b-117">Aby określić niestandardowy moduł sprawdzania poprawności, ustaw ten atrybut na "niestandardowy" i określ moduł walidacji przy użyciu [ \<elementu certificateValidator >](certificatevalidator.md) .</span><span class="sxs-lookup"><span data-stu-id="d872b-117">To specify a custom validator, set this attribute to "Custom" and specify the validator using the [\<certificateValidator>](certificatevalidator.md) element.</span></span> <span data-ttu-id="d872b-118">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="d872b-118">Optional.</span></span>|  
|<span data-ttu-id="d872b-119">odwołaniemode</span><span class="sxs-lookup"><span data-stu-id="d872b-119">revocationMode</span></span>|<span data-ttu-id="d872b-120"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> Wartość określająca tryb odwołania, który ma być używany dla certyfikatu X. 509.</span><span class="sxs-lookup"><span data-stu-id="d872b-120">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="d872b-121">Wartość domyślna to "online".</span><span class="sxs-lookup"><span data-stu-id="d872b-121">The default value is "Online".</span></span> <span data-ttu-id="d872b-122">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="d872b-122">Optional.</span></span>|  
|<span data-ttu-id="d872b-123">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="d872b-123">trustedStoreLocation</span></span>|<span data-ttu-id="d872b-124"><xref:System.Security.Cryptography.X509Certificates.StoreLocation> Wartość określająca magazyn certyfikatów X. 509.</span><span class="sxs-lookup"><span data-stu-id="d872b-124">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="d872b-125">Wartość domyślna to "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="d872b-125">The default value is "LocalMachine".</span></span> <span data-ttu-id="d872b-126">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="d872b-126">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d872b-127">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d872b-127">Child Elements</span></span>  
  
|<span data-ttu-id="d872b-128">Element</span><span class="sxs-lookup"><span data-stu-id="d872b-128">Element</span></span>|<span data-ttu-id="d872b-129">Opis</span><span class="sxs-lookup"><span data-stu-id="d872b-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d872b-130">\<certificateValidator ></span><span class="sxs-lookup"><span data-stu-id="d872b-130">\<certificateValidator></span></span>](certificatevalidator.md)|<span data-ttu-id="d872b-131">Określa typ niestandardowy na potrzeby walidacji certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="d872b-131">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="d872b-132">Ten typ jest używany tylko wtedy, `certificateValidationMode` gdy atrybut [ \<elementu certificateValidation >](certificatevalidation.md) jest ustawiony na wartość "Custom".</span><span class="sxs-lookup"><span data-stu-id="d872b-132">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element is set to "Custom".</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d872b-133">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d872b-133">Parent Elements</span></span>  
  
|<span data-ttu-id="d872b-134">Element</span><span class="sxs-lookup"><span data-stu-id="d872b-134">Element</span></span>|<span data-ttu-id="d872b-135">Opis</span><span class="sxs-lookup"><span data-stu-id="d872b-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d872b-136">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="d872b-136">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="d872b-137">Określa ustawienia tożsamości na poziomie usług.</span><span class="sxs-lookup"><span data-stu-id="d872b-137">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="d872b-138">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="d872b-138">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="d872b-139">Zapewnia konfigurację kolekcji programów obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="d872b-139">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d872b-140">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d872b-140">Remarks</span></span>  
 <span data-ttu-id="d872b-141">Element można określić na poziomie usługi `<identityConfiguration>` pod elementem lub na poziomie kolekcji `<securityTokenHandlerConfiguration>` programu obsługi tokenów zabezpieczających w ramach elementu. `<certificateValidation>`</span><span class="sxs-lookup"><span data-stu-id="d872b-141">A `<certificateValidation>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="d872b-142">Ustawienia w kolekcji obsługi tokenów zastępują te określone w usłudze.</span><span class="sxs-lookup"><span data-stu-id="d872b-142">Settings on a token handler collection override those specified on the service.</span></span> <span data-ttu-id="d872b-143">Niektóre programy obsługi tokenów umożliwiają określanie ustawień weryfikacji certyfikatu w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="d872b-143">Some token handlers allow you to specify certificate validation settings in configuration.</span></span> <span data-ttu-id="d872b-144">Ustawienia poszczególnych programów obsługi tokenów przesłaniają te określone zarówno na poziomie usługi, jak i w kolekcji obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="d872b-144">Settings on individual token handlers override those specified both at the service level and on the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d872b-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="d872b-145">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="PeerOrChainTrust"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine" />  
```
