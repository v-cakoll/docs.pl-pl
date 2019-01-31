---
title: <serviceCertificate>
ms.date: 03/30/2017
ms.assetid: 42c7f291-2ec3-43c5-8872-35897ff3c660
author: BrucePerlerMS
ms.openlocfilehash: 328d074f9edc5ddf871308a7e3d694bf94adea78
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55261610"
---
# <a name="servicecertificate"></a><span data-ttu-id="4dd2d-101">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="4dd2d-101">\<serviceCertificate></span></span>
<span data-ttu-id="4dd2d-102">Określa certyfikat X.509, który jest używany do szyfrowania i odszyfrowywania tokenów.</span><span class="sxs-lookup"><span data-stu-id="4dd2d-102">Configures the X.509 certificate that is used to encrypt and decrypt tokens.</span></span>  
  
 <span data-ttu-id="4dd2d-103">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="4dd2d-103">\<system.identityModel.services></span></span>  
<span data-ttu-id="4dd2d-104">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="4dd2d-104">\<federationConfiguration></span></span>  
<span data-ttu-id="4dd2d-105">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="4dd2d-105">\<serviceCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4dd2d-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="4dd2d-106">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4dd2d-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4dd2d-107">Attributes and Elements</span></span>  
 <span data-ttu-id="4dd2d-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4dd2d-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4dd2d-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4dd2d-109">Attributes</span></span>  
 <span data-ttu-id="4dd2d-110">Brak</span><span class="sxs-lookup"><span data-stu-id="4dd2d-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4dd2d-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4dd2d-111">Child Elements</span></span>  
  
|<span data-ttu-id="4dd2d-112">Element</span><span class="sxs-lookup"><span data-stu-id="4dd2d-112">Element</span></span>|<span data-ttu-id="4dd2d-113">Opis</span><span class="sxs-lookup"><span data-stu-id="4dd2d-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4dd2d-114">\<certificateReference ></span><span class="sxs-lookup"><span data-stu-id="4dd2d-114">\<certificateReference></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatereference.md)|<span data-ttu-id="4dd2d-115">Określa ustawienia, które są używane do znalezienia i sprawdź poprawność certyfikatu X.509 w magazynie certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="4dd2d-115">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4dd2d-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4dd2d-116">Parent Elements</span></span>  
  
|<span data-ttu-id="4dd2d-117">Element</span><span class="sxs-lookup"><span data-stu-id="4dd2d-117">Element</span></span>|<span data-ttu-id="4dd2d-118">Opis</span><span class="sxs-lookup"><span data-stu-id="4dd2d-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4dd2d-119">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="4dd2d-119">\<federationConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|<span data-ttu-id="4dd2d-120">Zawiera ustawienia, które skonfigurować <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) i <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span><span class="sxs-lookup"><span data-stu-id="4dd2d-120">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="4dd2d-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="4dd2d-121">Example</span></span>  
 <span data-ttu-id="4dd2d-122">Następujący kody XML pokazuje użycie \<serviceCertificate > element.</span><span class="sxs-lookup"><span data-stu-id="4dd2d-122">The following XML shows the use of the \<serviceCertificate> element.</span></span> <span data-ttu-id="4dd2d-123">Kod XML jest pobierana z `CustomToken` próbki.</span><span class="sxs-lookup"><span data-stu-id="4dd2d-123">The XML is taken from the `CustomToken` sample.</span></span>  
  
```xml  
<serviceCertificate>  
  <certificateReference x509FindType="FindBySubjectName" findValue="localhost" storeLocation="LocalMachine" storeName="My"/>  
</serviceCertificate>  
```
