---
title: <certificateValidation>
ms.date: 03/30/2017
ms.assetid: 6c54c704-b55e-4631-88ff-4d4a5621554c
author: BrucePerlerMS
ms.openlocfilehash: c2d1a5d36cb5616ef06eedc093dd70a68a164a81
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252139"
---
# \<certificateValidation>
<span data-ttu-id="fcaf4-101">Kontroluje ustawienia używane przez programy obsługi do sprawdzania poprawności certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="fcaf4-101">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="fcaf4-102">Te ustawienia są zastępowane, jeśli określony program obsługi jest skonfigurowany przy użyciu własnego modułu sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="fcaf4-102">These settings are overridden if a specific handler is configured with its own validator.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateValidation>**  
  
## <a name="syntax"></a><span data-ttu-id="fcaf4-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="fcaf4-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fcaf4-104">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="fcaf4-104">Attributes and Elements</span></span>  
 <span data-ttu-id="fcaf4-105">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="fcaf4-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fcaf4-106">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="fcaf4-106">Attributes</span></span>  
  
|<span data-ttu-id="fcaf4-107">Atrybut</span><span class="sxs-lookup"><span data-stu-id="fcaf4-107">Attribute</span></span>|<span data-ttu-id="fcaf4-108">Opis</span><span class="sxs-lookup"><span data-stu-id="fcaf4-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fcaf4-109">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="fcaf4-109">certificateValidationMode</span></span>|<span data-ttu-id="fcaf4-110">Wartość określająca <xref:System.ServiceModel.Security.X509CertificateValidationMode> tryb walidacji, który ma być używany dla certyfikatu X. 509.</span><span class="sxs-lookup"><span data-stu-id="fcaf4-110">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="fcaf4-111">Wartość domyślna to "PeerOrChainTrust".</span><span class="sxs-lookup"><span data-stu-id="fcaf4-111">The default value is "PeerOrChainTrust".</span></span> <span data-ttu-id="fcaf4-112">Aby określić niestandardowy moduł sprawdzania poprawności, ustaw ten atrybut na "niestandardowy" i określ moduł walidacji przy użyciu [\<certificateValidator>](certificatevalidator.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="fcaf4-112">To specify a custom validator, set this attribute to "Custom" and specify the validator using the [\<certificateValidator>](certificatevalidator.md) element.</span></span> <span data-ttu-id="fcaf4-113">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="fcaf4-113">Optional.</span></span>|  
|<span data-ttu-id="fcaf4-114">odwołaniemode</span><span class="sxs-lookup"><span data-stu-id="fcaf4-114">revocationMode</span></span>|<span data-ttu-id="fcaf4-115"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>Wartość określająca tryb odwołania, który ma być używany dla certyfikatu X. 509.</span><span class="sxs-lookup"><span data-stu-id="fcaf4-115">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="fcaf4-116">Wartość domyślna to "online".</span><span class="sxs-lookup"><span data-stu-id="fcaf4-116">The default value is "Online".</span></span> <span data-ttu-id="fcaf4-117">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="fcaf4-117">Optional.</span></span>|  
|<span data-ttu-id="fcaf4-118">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="fcaf4-118">trustedStoreLocation</span></span>|<span data-ttu-id="fcaf4-119">Wartość określająca <xref:System.Security.Cryptography.X509Certificates.StoreLocation> Magazyn certyfikatów X. 509.</span><span class="sxs-lookup"><span data-stu-id="fcaf4-119">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="fcaf4-120">Wartość domyślna to "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="fcaf4-120">The default value is "LocalMachine".</span></span> <span data-ttu-id="fcaf4-121">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="fcaf4-121">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fcaf4-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="fcaf4-122">Child Elements</span></span>  
  
|<span data-ttu-id="fcaf4-123">Element</span><span class="sxs-lookup"><span data-stu-id="fcaf4-123">Element</span></span>|<span data-ttu-id="fcaf4-124">Opis</span><span class="sxs-lookup"><span data-stu-id="fcaf4-124">Description</span></span>|  
|-------------|-----------------|  
|[\<certificateValidator>](certificatevalidator.md)|<span data-ttu-id="fcaf4-125">Określa typ niestandardowy na potrzeby walidacji certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="fcaf4-125">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="fcaf4-126">Ten typ jest używany tylko wtedy, gdy `certificateValidationMode` atrybut [\<certificateValidation>](certificatevalidation.md) elementu jest ustawiony na wartość "Custom".</span><span class="sxs-lookup"><span data-stu-id="fcaf4-126">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element is set to "Custom".</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fcaf4-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="fcaf4-127">Parent Elements</span></span>  
  
|<span data-ttu-id="fcaf4-128">Element</span><span class="sxs-lookup"><span data-stu-id="fcaf4-128">Element</span></span>|<span data-ttu-id="fcaf4-129">Opis</span><span class="sxs-lookup"><span data-stu-id="fcaf4-129">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="fcaf4-130">Określa ustawienia tożsamości na poziomie usług.</span><span class="sxs-lookup"><span data-stu-id="fcaf4-130">Specifies service-level identity settings.</span></span>|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="fcaf4-131">Zapewnia konfigurację kolekcji programów obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="fcaf4-131">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fcaf4-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fcaf4-132">Remarks</span></span>  
 <span data-ttu-id="fcaf4-133">`<certificateValidation>`Element można określić na poziomie usługi pod `<identityConfiguration>` elementem lub na poziomie kolekcji programu obsługi tokenów zabezpieczających w ramach `<securityTokenHandlerConfiguration>` elementu.</span><span class="sxs-lookup"><span data-stu-id="fcaf4-133">A `<certificateValidation>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="fcaf4-134">Ustawienia w kolekcji obsługi tokenów zastępują te określone w usłudze.</span><span class="sxs-lookup"><span data-stu-id="fcaf4-134">Settings on a token handler collection override those specified on the service.</span></span> <span data-ttu-id="fcaf4-135">Niektóre programy obsługi tokenów umożliwiają określanie ustawień weryfikacji certyfikatu w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="fcaf4-135">Some token handlers allow you to specify certificate validation settings in configuration.</span></span> <span data-ttu-id="fcaf4-136">Ustawienia poszczególnych programów obsługi tokenów przesłaniają te określone zarówno na poziomie usługi, jak i w kolekcji obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="fcaf4-136">Settings on individual token handlers override those specified both at the service level and on the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fcaf4-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="fcaf4-137">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="PeerOrChainTrust"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine" />  
```
