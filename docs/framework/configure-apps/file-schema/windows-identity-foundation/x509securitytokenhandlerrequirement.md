---
title: <x509SecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: aca22c2c-5ae7-42af-9bbd-15c2524692ce
author: BrucePerlerMS
ms.openlocfilehash: 30ce69a35cfdd34e0dfea5c682347eb9187e04ed
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152453"
---
# \<x509SecurityTokenHandlerRequirement>
<span data-ttu-id="f8451-101">Zapewnia opcjonalną konfigurację <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> klasy lub klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="f8451-101">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<x509SecurityTokenHandlerRequirement>**  
  
## <a name="syntax"></a><span data-ttu-id="f8451-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="f8451-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f8451-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f8451-103">Attributes and Elements</span></span>  
 <span data-ttu-id="f8451-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f8451-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f8451-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f8451-105">Attributes</span></span>  
  
|<span data-ttu-id="f8451-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f8451-106">Attribute</span></span>|<span data-ttu-id="f8451-107">Opis</span><span class="sxs-lookup"><span data-stu-id="f8451-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f8451-108">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="f8451-108">certificateValidationMode</span></span>|<span data-ttu-id="f8451-109">Wartość określająca <xref:System.ServiceModel.Security.X509CertificateValidationMode> tryb walidacji, który ma być używany dla certyfikatu X. 509.</span><span class="sxs-lookup"><span data-stu-id="f8451-109">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="f8451-110">Wartość domyślna to "PeerOrChainTrust".</span><span class="sxs-lookup"><span data-stu-id="f8451-110">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="f8451-111">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="f8451-111">mapToWindows</span></span>|<span data-ttu-id="f8451-112">Określa, czy program obsługi tokenów powinien mapować token walidacji na konto systemu Windows przy użyciu przychodzącego oświadczenie nazwy UPN.</span><span class="sxs-lookup"><span data-stu-id="f8451-112">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="f8451-113">Wartość domyślna to "false".</span><span class="sxs-lookup"><span data-stu-id="f8451-113">The default is "false".</span></span>|  
|<span data-ttu-id="f8451-114">odwołaniemode</span><span class="sxs-lookup"><span data-stu-id="f8451-114">revocationMode</span></span>|<span data-ttu-id="f8451-115"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>Wartość określająca tryb odwołania, który ma być używany dla certyfikatu X. 509.</span><span class="sxs-lookup"><span data-stu-id="f8451-115">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="f8451-116">Wartość domyślna to "online".</span><span class="sxs-lookup"><span data-stu-id="f8451-116">The default value is "Online".</span></span>|  
|<span data-ttu-id="f8451-117">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="f8451-117">trustedStoreLocation</span></span>|<span data-ttu-id="f8451-118">Wartość określająca <xref:System.Security.Cryptography.X509Certificates.StoreLocation> Magazyn certyfikatów X. 509.</span><span class="sxs-lookup"><span data-stu-id="f8451-118">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="f8451-119">Wartość domyślna to "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="f8451-119">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="f8451-120">certificateValidator</span><span class="sxs-lookup"><span data-stu-id="f8451-120">certificateValidator</span></span>|<span data-ttu-id="f8451-121">Typ niestandardowy, który pochodzi od <xref:System.IdentityModel.Selectors.X509CertificateValidator> .</span><span class="sxs-lookup"><span data-stu-id="f8451-121">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="f8451-122">Jeśli `certificateValidationMode` atrybut jest "Custom", wystąpienie tego typu jest używane na potrzeby walidacji certyfikatu wystawcy.</span><span class="sxs-lookup"><span data-stu-id="f8451-122">If the `certificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f8451-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f8451-123">Child Elements</span></span>  
 <span data-ttu-id="f8451-124">Brak</span><span class="sxs-lookup"><span data-stu-id="f8451-124">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f8451-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f8451-125">Parent Elements</span></span>  
  
|<span data-ttu-id="f8451-126">Element</span><span class="sxs-lookup"><span data-stu-id="f8451-126">Element</span></span>|<span data-ttu-id="f8451-127">Opis</span><span class="sxs-lookup"><span data-stu-id="f8451-127">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add.md)|<span data-ttu-id="f8451-128">Dodaje określony program obsługi tokenów zabezpieczających do kolekcji obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="f8451-128">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f8451-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="f8451-129">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
    <x509SecurityTokenHandlerRequirement mapToWindows="true"
                                         certificateValidationMode="PeerOrChainTrust"
                                         revocationMode="Online"
                                         trustedStoreLocation="LocalMachine" />  
</add>  
```
