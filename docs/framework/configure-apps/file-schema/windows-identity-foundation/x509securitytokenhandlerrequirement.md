---
title: <x509SecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: aca22c2c-5ae7-42af-9bbd-15c2524692ce
author: BrucePerlerMS
ms.openlocfilehash: 76eeea635fd65486a1c16bea15a49018876dae99
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251697"
---
# <a name="x509securitytokenhandlerrequirement"></a><span data-ttu-id="1db3d-101">\<x509SecurityTokenHandlerRequirement ></span><span class="sxs-lookup"><span data-stu-id="1db3d-101">\<x509SecurityTokenHandlerRequirement></span></span>
<span data-ttu-id="1db3d-102">Zapewnia opcjonalną konfigurację <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> klasy lub klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="1db3d-102">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>  
  
<span data-ttu-id="1db3d-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1db3d-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1db3d-104">&nbsp;&nbsp;[ **\<> System. identityModel**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="1db3d-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="1db3d-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="1db3d-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="1db3d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> obiektów securityTokenHandler**](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="1db3d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="1db3d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Dodaj >** ](add.md)</span><span class="sxs-lookup"><span data-stu-id="1db3d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)</span></span>\
<span data-ttu-id="1db3d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<x509SecurityTokenHandlerRequirement >**</span><span class="sxs-lookup"><span data-stu-id="1db3d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<x509SecurityTokenHandlerRequirement>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1db3d-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="1db3d-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1db3d-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1db3d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="1db3d-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1db3d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1db3d-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1db3d-112">Attributes</span></span>  
  
|<span data-ttu-id="1db3d-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="1db3d-113">Attribute</span></span>|<span data-ttu-id="1db3d-114">Opis</span><span class="sxs-lookup"><span data-stu-id="1db3d-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1db3d-115">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="1db3d-115">certificateValidationMode</span></span>|<span data-ttu-id="1db3d-116"><xref:System.ServiceModel.Security.X509CertificateValidationMode> Wartość określająca tryb walidacji, który ma być używany dla certyfikatu X. 509.</span><span class="sxs-lookup"><span data-stu-id="1db3d-116">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="1db3d-117">Wartość domyślna to "PeerOrChainTrust".</span><span class="sxs-lookup"><span data-stu-id="1db3d-117">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="1db3d-118">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="1db3d-118">mapToWindows</span></span>|<span data-ttu-id="1db3d-119">Określa, czy program obsługi tokenów powinien mapować token walidacji na konto systemu Windows przy użyciu przychodzącego oświadczenie nazwy UPN.</span><span class="sxs-lookup"><span data-stu-id="1db3d-119">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="1db3d-120">Wartość domyślna to "false".</span><span class="sxs-lookup"><span data-stu-id="1db3d-120">The default is "false".</span></span>|  
|<span data-ttu-id="1db3d-121">odwołaniemode</span><span class="sxs-lookup"><span data-stu-id="1db3d-121">revocationMode</span></span>|<span data-ttu-id="1db3d-122"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> Wartość określająca tryb odwołania, który ma być używany dla certyfikatu X. 509.</span><span class="sxs-lookup"><span data-stu-id="1db3d-122">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="1db3d-123">Wartość domyślna to "online".</span><span class="sxs-lookup"><span data-stu-id="1db3d-123">The default value is "Online".</span></span>|  
|<span data-ttu-id="1db3d-124">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="1db3d-124">trustedStoreLocation</span></span>|<span data-ttu-id="1db3d-125"><xref:System.Security.Cryptography.X509Certificates.StoreLocation> Wartość określająca magazyn certyfikatów X. 509.</span><span class="sxs-lookup"><span data-stu-id="1db3d-125">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="1db3d-126">Wartość domyślna to "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="1db3d-126">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="1db3d-127">certificateValidator</span><span class="sxs-lookup"><span data-stu-id="1db3d-127">certificateValidator</span></span>|<span data-ttu-id="1db3d-128">Typ niestandardowy, który pochodzi od <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="1db3d-128">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="1db3d-129">`certificateValidationMode` Jeśli atrybut jest "Custom", wystąpienie tego typu jest używane na potrzeby walidacji certyfikatu wystawcy.</span><span class="sxs-lookup"><span data-stu-id="1db3d-129">If the `certificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1db3d-130">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1db3d-130">Child Elements</span></span>  
 <span data-ttu-id="1db3d-131">Brak</span><span class="sxs-lookup"><span data-stu-id="1db3d-131">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1db3d-132">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1db3d-132">Parent Elements</span></span>  
  
|<span data-ttu-id="1db3d-133">Element</span><span class="sxs-lookup"><span data-stu-id="1db3d-133">Element</span></span>|<span data-ttu-id="1db3d-134">Opis</span><span class="sxs-lookup"><span data-stu-id="1db3d-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1db3d-135">\<add></span><span class="sxs-lookup"><span data-stu-id="1db3d-135">\<add></span></span>](add.md)|<span data-ttu-id="1db3d-136">Dodaje określony program obsługi tokenów zabezpieczających do kolekcji obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="1db3d-136">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1db3d-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="1db3d-137">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
    <x509SecurityTokenHandlerRequirement mapToWindows="true"   
                                         certificateValidationMode="PeerOrChainTrust"   
                                         revocationMode="Online"   
                                         trustedStoreLocation="LocalMachine" />  
</add>  
```
