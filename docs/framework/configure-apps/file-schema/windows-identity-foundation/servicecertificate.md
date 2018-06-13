---
title: '&lt;ServiceCertificate&gt;'
ms.date: 03/30/2017
ms.assetid: 42c7f291-2ec3-43c5-8872-35897ff3c660
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: af59562dbf6c13970526f1665a9ba2c57c4f32ee
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32766780"
---
# <a name="ltservicecertificategt"></a><span data-ttu-id="e38f7-102">&lt;ServiceCertificate&gt;</span><span class="sxs-lookup"><span data-stu-id="e38f7-102">&lt;serviceCertificate&gt;</span></span>
<span data-ttu-id="e38f7-103">Umożliwia skonfigurowanie certyfikatu X.509, który jest używany do szyfrowania i odszyfrowywania tokenów.</span><span class="sxs-lookup"><span data-stu-id="e38f7-103">Configures the X.509 certificate that is used to encrypt and decrypt tokens.</span></span>  
  
 <span data-ttu-id="e38f7-104">\<system.identityModel.services ></span><span class="sxs-lookup"><span data-stu-id="e38f7-104">\<system.identityModel.services></span></span>  
<span data-ttu-id="e38f7-105">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="e38f7-105">\<federationConfiguration></span></span>  
<span data-ttu-id="e38f7-106">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="e38f7-106">\<serviceCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e38f7-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="e38f7-107">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e38f7-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e38f7-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e38f7-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e38f7-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e38f7-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e38f7-110">Attributes</span></span>  
 <span data-ttu-id="e38f7-111">Brak</span><span class="sxs-lookup"><span data-stu-id="e38f7-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e38f7-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e38f7-112">Child Elements</span></span>  
  
|<span data-ttu-id="e38f7-113">Element</span><span class="sxs-lookup"><span data-stu-id="e38f7-113">Element</span></span>|<span data-ttu-id="e38f7-114">Opis</span><span class="sxs-lookup"><span data-stu-id="e38f7-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e38f7-115">\<certificateReference ></span><span class="sxs-lookup"><span data-stu-id="e38f7-115">\<certificateReference></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatereference.md)|<span data-ttu-id="e38f7-116">Określa ustawienia, które są używane do znajdowania i zweryfikować certyfikatu w magazynie certyfikatów X.509.</span><span class="sxs-lookup"><span data-stu-id="e38f7-116">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e38f7-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e38f7-117">Parent Elements</span></span>  
  
|<span data-ttu-id="e38f7-118">Element</span><span class="sxs-lookup"><span data-stu-id="e38f7-118">Element</span></span>|<span data-ttu-id="e38f7-119">Opis</span><span class="sxs-lookup"><span data-stu-id="e38f7-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e38f7-120">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="e38f7-120">\<federationConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|<span data-ttu-id="e38f7-121">Zawiera ustawienia, które konfigurują <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) i <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span><span class="sxs-lookup"><span data-stu-id="e38f7-121">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e38f7-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="e38f7-122">Example</span></span>  
 <span data-ttu-id="e38f7-123">Następujący kod XML pokazano sposób użycia \<serviceCertificate > elementu.</span><span class="sxs-lookup"><span data-stu-id="e38f7-123">The following XML shows the use of the \<serviceCertificate> element.</span></span> <span data-ttu-id="e38f7-124">Kod XML jest pobierana z `CustomToken` próbki.</span><span class="sxs-lookup"><span data-stu-id="e38f7-124">The XML is taken from the `CustomToken` sample.</span></span>  
  
```xml  
<serviceCertificate>  
  <certificateReference x509FindType="FindBySubjectName" findValue="localhost" storeLocation="LocalMachine" storeName="My"/>  
</serviceCertificate>  
```
