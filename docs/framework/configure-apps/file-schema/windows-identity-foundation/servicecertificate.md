---
title: '&lt;serviceCertificate&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 42c7f291-2ec3-43c5-8872-35897ff3c660
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 177639b973bf8c597bc8b994d37c99647c72feb8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ltservicecertificategt"></a><span data-ttu-id="fa86a-102">&lt;serviceCertificate&gt;</span><span class="sxs-lookup"><span data-stu-id="fa86a-102">&lt;serviceCertificate&gt;</span></span>
<span data-ttu-id="fa86a-103">Umożliwia skonfigurowanie certyfikatu X.509, który jest używany do szyfrowania i odszyfrowywania tokenów.</span><span class="sxs-lookup"><span data-stu-id="fa86a-103">Configures the X.509 certificate that is used to encrypt and decrypt tokens.</span></span>  
  
 <span data-ttu-id="fa86a-104">\<system.identityModel.services ></span><span class="sxs-lookup"><span data-stu-id="fa86a-104">\<system.identityModel.services></span></span>  
<span data-ttu-id="fa86a-105">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="fa86a-105">\<federationConfiguration></span></span>  
<span data-ttu-id="fa86a-106">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="fa86a-106">\<serviceCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa86a-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="fa86a-107">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fa86a-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="fa86a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="fa86a-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="fa86a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fa86a-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="fa86a-110">Attributes</span></span>  
 <span data-ttu-id="fa86a-111">Brak</span><span class="sxs-lookup"><span data-stu-id="fa86a-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fa86a-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="fa86a-112">Child Elements</span></span>  
  
|<span data-ttu-id="fa86a-113">Element</span><span class="sxs-lookup"><span data-stu-id="fa86a-113">Element</span></span>|<span data-ttu-id="fa86a-114">Opis</span><span class="sxs-lookup"><span data-stu-id="fa86a-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fa86a-115">\<certificateReference ></span><span class="sxs-lookup"><span data-stu-id="fa86a-115">\<certificateReference></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatereference.md)|<span data-ttu-id="fa86a-116">Określa ustawienia, które są używane do znajdowania i zweryfikować certyfikatu w magazynie certyfikatów X.509.</span><span class="sxs-lookup"><span data-stu-id="fa86a-116">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fa86a-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="fa86a-117">Parent Elements</span></span>  
  
|<span data-ttu-id="fa86a-118">Element</span><span class="sxs-lookup"><span data-stu-id="fa86a-118">Element</span></span>|<span data-ttu-id="fa86a-119">Opis</span><span class="sxs-lookup"><span data-stu-id="fa86a-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fa86a-120">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="fa86a-120">\<federationConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|<span data-ttu-id="fa86a-121">Zawiera ustawienia, które konfigurują <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) i <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span><span class="sxs-lookup"><span data-stu-id="fa86a-121">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="fa86a-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="fa86a-122">Example</span></span>  
 <span data-ttu-id="fa86a-123">Następujący kod XML pokazano sposób użycia \<serviceCertificate > elementu.</span><span class="sxs-lookup"><span data-stu-id="fa86a-123">The following XML shows the use of the \<serviceCertificate> element.</span></span> <span data-ttu-id="fa86a-124">Kod XML jest pobierana z `CustomToken` próbki.</span><span class="sxs-lookup"><span data-stu-id="fa86a-124">The XML is taken from the `CustomToken` sample.</span></span>  
  
```xml  
<serviceCertificate>  
  <certificateReference x509FindType="FindBySubjectName" findValue="localhost" storeLocation="LocalMachine" storeName="My"/>  
</serviceCertificate>  
```
