---
title: <certificateReference>
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
ms.openlocfilehash: 47d432a84d070476ddffd9b98a4ba46d8163bdc3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152817"
---
# <a name="certificatereference"></a><span data-ttu-id="c53fa-101">\<> odniesienia certyfikatu</span><span class="sxs-lookup"><span data-stu-id="c53fa-101">\<certificateReference></span></span>
<span data-ttu-id="c53fa-102">Określa ustawienia używane do znajdowania i sprawdzania poprawności certyfikatu X.509 w magazynie certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="c53fa-102">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>  
  
<span data-ttu-id="c53fa-103">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c53fa-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c53fa-104">&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)</span><span class="sxs-lookup"><span data-stu-id="c53fa-104">&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)</span></span>\
<span data-ttu-id="c53fa-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="c53fa-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)</span></span>\
<span data-ttu-id="c53fa-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serwisCertificate>**](servicecertificate.md)</span><span class="sxs-lookup"><span data-stu-id="c53fa-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate.md)</span></span>\
<span data-ttu-id="c53fa-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>odniesienia certyfikatu**</span><span class="sxs-lookup"><span data-stu-id="c53fa-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateReference>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c53fa-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="c53fa-108">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
      <certificateReference
        storeName="AddressBook||AuthRoot||CertificateAuthority||Disallowed||My||Root||TrustedPeople||TrustedPublisher"  
        storeLocation="CurrentUser||LocalMachine"  
        x509FindType="FindByThumbprint||FindBySubjectName||FindBySubjectDistinguishedName||FindByIssuerName||FindByIssuerDistinguishedName||FindBySerialNumber||FindByTimeValid||FindByTimeNotYetValid||FindByTimeExpired||FindByTemplateName||FindByApplicationPolicy||FindByCertificatePolicy||FindByExtension||FindByKeyUsage||FindBySubjectKeyIdentifier"  
        findValue=xs:String  
        isChainIncluded=xs:Boolean >  
      </certificateReference>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c53fa-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c53fa-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c53fa-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c53fa-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c53fa-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c53fa-111">Attributes</span></span>  
  
|<span data-ttu-id="c53fa-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c53fa-112">Attribute</span></span>|<span data-ttu-id="c53fa-113">Opis</span><span class="sxs-lookup"><span data-stu-id="c53fa-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c53fa-114">Storename</span><span class="sxs-lookup"><span data-stu-id="c53fa-114">storeName</span></span>|<span data-ttu-id="c53fa-115">Nazwa magazynu certyfikatów X.509.</span><span class="sxs-lookup"><span data-stu-id="c53fa-115">The name of the X.509 certificate store.</span></span> <span data-ttu-id="c53fa-116">Wartość domyślna to "Moje".</span><span class="sxs-lookup"><span data-stu-id="c53fa-116">The default is "My".</span></span> <span data-ttu-id="c53fa-117">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="c53fa-117">Optional.</span></span>|  
|<span data-ttu-id="c53fa-118">Storelocation</span><span class="sxs-lookup"><span data-stu-id="c53fa-118">storeLocation</span></span>|<span data-ttu-id="c53fa-119">Wartość <xref:System.Security.Cryptography.X509Certificates.StoreLocation> określająca lokalizację magazynu certyfikatów X.509.</span><span class="sxs-lookup"><span data-stu-id="c53fa-119">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the location of the X.509 certificate store.</span></span> <span data-ttu-id="c53fa-120">Wartością domyślną jest "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="c53fa-120">The default value is "LocalMachine".</span></span> <span data-ttu-id="c53fa-121">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="c53fa-121">Optional.</span></span>|  
|<span data-ttu-id="c53fa-122">X509findtype</span><span class="sxs-lookup"><span data-stu-id="c53fa-122">x509FindType</span></span>|<span data-ttu-id="c53fa-123">Wartość <xref:System.Security.Cryptography.X509Certificates.X509FindType> określająca typ wyszukiwania, które ma zostać wykonane.</span><span class="sxs-lookup"><span data-stu-id="c53fa-123">An <xref:System.Security.Cryptography.X509Certificates.X509FindType> value that specifies the type of search that is to be executed.</span></span> <span data-ttu-id="c53fa-124">Wartość domyślna to "FindBySubjectDistinguishedName".</span><span class="sxs-lookup"><span data-stu-id="c53fa-124">The default is "FindBySubjectDistinguishedName".</span></span> <span data-ttu-id="c53fa-125">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="c53fa-125">Optional.</span></span>|  
|<span data-ttu-id="c53fa-126">Findvalue</span><span class="sxs-lookup"><span data-stu-id="c53fa-126">findValue</span></span>|<span data-ttu-id="c53fa-127">Wartość do wyszukania w magazynie certyfikatów X.509.</span><span class="sxs-lookup"><span data-stu-id="c53fa-127">The value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="c53fa-128">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="c53fa-128">Optional.</span></span>|  
|<span data-ttu-id="c53fa-129">w zestawie isChain</span><span class="sxs-lookup"><span data-stu-id="c53fa-129">isChainIncluded</span></span>|<span data-ttu-id="c53fa-130">Określa, czy sprawdzanie poprawności ma być wykonywane przy użyciu łańcucha certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="c53fa-130">Specifies whether validation should be performed by using the certificate chain.</span></span> <span data-ttu-id="c53fa-131">Wartość domyślna to "true"; sprawdzania poprawności odbywa się przy użyciu łańcucha certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="c53fa-131">The default is "true"; validation is performed by using the certificate chain.</span></span> <span data-ttu-id="c53fa-132">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="c53fa-132">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c53fa-133">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c53fa-133">Child Elements</span></span>  
 <span data-ttu-id="c53fa-134">Brak</span><span class="sxs-lookup"><span data-stu-id="c53fa-134">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c53fa-135">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c53fa-135">Parent Elements</span></span>  
  
|<span data-ttu-id="c53fa-136">Element</span><span class="sxs-lookup"><span data-stu-id="c53fa-136">Element</span></span>|<span data-ttu-id="c53fa-137">Opis</span><span class="sxs-lookup"><span data-stu-id="c53fa-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c53fa-138">\<serwisCertificate></span><span class="sxs-lookup"><span data-stu-id="c53fa-138">\<serviceCertificate></span></span>](servicecertificate.md)|<span data-ttu-id="c53fa-139">Konfiguruje certyfikat używany do szyfrowania i odszyfrowywania tokenów.</span><span class="sxs-lookup"><span data-stu-id="c53fa-139">Configures the certificate that is used to encrypt and decrypt tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c53fa-140">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c53fa-140">Remarks</span></span>  
 <span data-ttu-id="c53fa-141">Element `<certificateReference>` określa ustawienia, które są używane do znajdowania i sprawdzania poprawności certyfikatu X.509 w magazynie certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="c53fa-141">The `<certificateReference>` element specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span> <span data-ttu-id="c53fa-142">Gdy jest określony jako element `<serviceCertificate>` podrzędny elementu, określa ustawienia lokalizacji i weryfikacji certyfikatu X.509, który jest używany do szyfrowania i odszyfrowywania tokenów.</span><span class="sxs-lookup"><span data-stu-id="c53fa-142">When it is specified as the child element of the `<serviceCertificate>` element, it specifies the location and verification settings of the X.509 certificate that is used to encrypt and decrypt tokens.</span></span> <span data-ttu-id="c53fa-143">Element `<certificateReference>` jest reprezentowany <xref:System.ServiceModel.Configuration.CertificateReferenceElement> przez klasę.</span><span class="sxs-lookup"><span data-stu-id="c53fa-143">The `<certificateReference>` element is represented by the <xref:System.ServiceModel.Configuration.CertificateReferenceElement> class.</span></span>
