---
title: <x509SecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: aca22c2c-5ae7-42af-9bbd-15c2524692ce
author: BrucePerlerMS
ms.openlocfilehash: 30ce69a35cfdd34e0dfea5c682347eb9187e04ed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152453"
---
# <a name="x509securitytokenhandlerrequirement"></a><span data-ttu-id="45da2-101">\<x509SecurityTokenHandlerOquirement></span><span class="sxs-lookup"><span data-stu-id="45da2-101">\<x509SecurityTokenHandlerRequirement></span></span>
<span data-ttu-id="45da2-102">Zapewnia opcjonalną <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> konfigurację dla klasy lub klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="45da2-102">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>  
  
<span data-ttu-id="45da2-103">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="45da2-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="45da2-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="45da2-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="45da2-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<>konfiguracji tożsamości**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="45da2-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="45da2-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>securityTokenHandlers**](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="45da2-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="45da2-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dodaj>**](add.md)</span><span class="sxs-lookup"><span data-stu-id="45da2-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)</span></span>\
<span data-ttu-id="45da2-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<x509SecurityTokenHandlerOquirement>**</span><span class="sxs-lookup"><span data-stu-id="45da2-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<x509SecurityTokenHandlerRequirement>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45da2-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="45da2-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="45da2-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="45da2-110">Attributes and Elements</span></span>  
 <span data-ttu-id="45da2-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="45da2-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="45da2-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="45da2-112">Attributes</span></span>  
  
|<span data-ttu-id="45da2-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="45da2-113">Attribute</span></span>|<span data-ttu-id="45da2-114">Opis</span><span class="sxs-lookup"><span data-stu-id="45da2-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="45da2-115">Certificatevalidationmode</span><span class="sxs-lookup"><span data-stu-id="45da2-115">certificateValidationMode</span></span>|<span data-ttu-id="45da2-116">Wartość <xref:System.ServiceModel.Security.X509CertificateValidationMode> określająca tryb sprawdzania poprawności dla certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="45da2-116">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="45da2-117">Wartością domyślną jest "PeerOrChainTrust".</span><span class="sxs-lookup"><span data-stu-id="45da2-117">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="45da2-118">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="45da2-118">mapToWindows</span></span>|<span data-ttu-id="45da2-119">Określa, czy program obsługi tokenu powinien mapować token sprawdzania poprawności na konto systemu Windows przy użyciu przychodzącego oświadczenia upn.</span><span class="sxs-lookup"><span data-stu-id="45da2-119">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="45da2-120">Wartość domyślna to "false".</span><span class="sxs-lookup"><span data-stu-id="45da2-120">The default is "false".</span></span>|  
|<span data-ttu-id="45da2-121">revocationMode</span><span class="sxs-lookup"><span data-stu-id="45da2-121">revocationMode</span></span>|<span data-ttu-id="45da2-122">Wartość <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> określająca tryb odwołania do użycia dla certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="45da2-122">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="45da2-123">Wartością domyślną jest "Online".</span><span class="sxs-lookup"><span data-stu-id="45da2-123">The default value is "Online".</span></span>|  
|<span data-ttu-id="45da2-124">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="45da2-124">trustedStoreLocation</span></span>|<span data-ttu-id="45da2-125">Wartość <xref:System.Security.Cryptography.X509Certificates.StoreLocation> określająca magazyn certyfikatów X.509.</span><span class="sxs-lookup"><span data-stu-id="45da2-125">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="45da2-126">Wartością domyślną jest "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="45da2-126">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="45da2-127">certificateValidator</span><span class="sxs-lookup"><span data-stu-id="45da2-127">certificateValidator</span></span>|<span data-ttu-id="45da2-128">Typ niestandardowy, który <xref:System.IdentityModel.Selectors.X509CertificateValidator>pochodzi od .</span><span class="sxs-lookup"><span data-stu-id="45da2-128">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="45da2-129">Jeśli `certificateValidationMode` atrybut jest "Niestandardowe", wystąpienie tego typu jest używane do sprawdzania poprawności certyfikatu wystawcy.</span><span class="sxs-lookup"><span data-stu-id="45da2-129">If the `certificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="45da2-130">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="45da2-130">Child Elements</span></span>  
 <span data-ttu-id="45da2-131">Brak</span><span class="sxs-lookup"><span data-stu-id="45da2-131">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="45da2-132">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="45da2-132">Parent Elements</span></span>  
  
|<span data-ttu-id="45da2-133">Element</span><span class="sxs-lookup"><span data-stu-id="45da2-133">Element</span></span>|<span data-ttu-id="45da2-134">Opis</span><span class="sxs-lookup"><span data-stu-id="45da2-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="45da2-135">\<dodaj></span><span class="sxs-lookup"><span data-stu-id="45da2-135">\<add></span></span>](add.md)|<span data-ttu-id="45da2-136">Dodaje określony program obsługi tokenu zabezpieczającego do kolekcji obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="45da2-136">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="45da2-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="45da2-137">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
    <x509SecurityTokenHandlerRequirement mapToWindows="true"
                                         certificateValidationMode="PeerOrChainTrust"
                                         revocationMode="Online"
                                         trustedStoreLocation="LocalMachine" />  
</add>  
```
