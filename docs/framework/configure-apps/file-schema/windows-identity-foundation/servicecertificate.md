---
title: '&lt;serviceCertificate&gt;'
ms.date: 03/30/2017
ms.assetid: 42c7f291-2ec3-43c5-8872-35897ff3c660
author: BrucePerlerMS
ms.openlocfilehash: 008d2269a72759117658e27ec130cc8cf62cfdfa
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2018
ms.locfileid: "47400416"
---
# <a name="ltservicecertificategt"></a><span data-ttu-id="1a8cb-102">&lt;serviceCertificate&gt;</span><span class="sxs-lookup"><span data-stu-id="1a8cb-102">&lt;serviceCertificate&gt;</span></span>
<span data-ttu-id="1a8cb-103">Określa certyfikat X.509, który jest używany do szyfrowania i odszyfrowywania tokenów.</span><span class="sxs-lookup"><span data-stu-id="1a8cb-103">Configures the X.509 certificate that is used to encrypt and decrypt tokens.</span></span>  
  
 <span data-ttu-id="1a8cb-104">\<system.identityModel.services ></span><span class="sxs-lookup"><span data-stu-id="1a8cb-104">\<system.identityModel.services></span></span>  
<span data-ttu-id="1a8cb-105">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="1a8cb-105">\<federationConfiguration></span></span>  
<span data-ttu-id="1a8cb-106">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="1a8cb-106">\<serviceCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a8cb-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="1a8cb-107">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1a8cb-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1a8cb-108">Attributes and Elements</span></span>  
 <span data-ttu-id="1a8cb-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1a8cb-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1a8cb-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1a8cb-110">Attributes</span></span>  
 <span data-ttu-id="1a8cb-111">Brak</span><span class="sxs-lookup"><span data-stu-id="1a8cb-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1a8cb-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1a8cb-112">Child Elements</span></span>  
  
|<span data-ttu-id="1a8cb-113">Element</span><span class="sxs-lookup"><span data-stu-id="1a8cb-113">Element</span></span>|<span data-ttu-id="1a8cb-114">Opis</span><span class="sxs-lookup"><span data-stu-id="1a8cb-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1a8cb-115">\<certificateReference ></span><span class="sxs-lookup"><span data-stu-id="1a8cb-115">\<certificateReference></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatereference.md)|<span data-ttu-id="1a8cb-116">Określa ustawienia, które są używane do znalezienia i sprawdź poprawność certyfikatu X.509 w magazynie certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="1a8cb-116">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1a8cb-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1a8cb-117">Parent Elements</span></span>  
  
|<span data-ttu-id="1a8cb-118">Element</span><span class="sxs-lookup"><span data-stu-id="1a8cb-118">Element</span></span>|<span data-ttu-id="1a8cb-119">Opis</span><span class="sxs-lookup"><span data-stu-id="1a8cb-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1a8cb-120">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="1a8cb-120">\<federationConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|<span data-ttu-id="1a8cb-121">Zawiera ustawienia, które skonfigurować <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) i <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span><span class="sxs-lookup"><span data-stu-id="1a8cb-121">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1a8cb-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="1a8cb-122">Example</span></span>  
 <span data-ttu-id="1a8cb-123">Następujący kody XML pokazuje użycie \<serviceCertificate > element.</span><span class="sxs-lookup"><span data-stu-id="1a8cb-123">The following XML shows the use of the \<serviceCertificate> element.</span></span> <span data-ttu-id="1a8cb-124">Kod XML jest pobierana z `CustomToken` próbki.</span><span class="sxs-lookup"><span data-stu-id="1a8cb-124">The XML is taken from the `CustomToken` sample.</span></span>  
  
```xml  
<serviceCertificate>  
  <certificateReference x509FindType="FindBySubjectName" findValue="localhost" storeLocation="LocalMachine" storeName="My"/>  
</serviceCertificate>  
```
