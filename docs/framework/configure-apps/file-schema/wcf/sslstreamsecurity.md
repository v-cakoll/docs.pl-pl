---
title: '&lt;sslStreamSecurity&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
caps.latest.revision: "11"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 65233bf416080212a5c1447cffd329eca1b921f4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltsslstreamsecuritygt"></a><span data-ttu-id="2155d-102">&lt;sslStreamSecurity&gt;</span><span class="sxs-lookup"><span data-stu-id="2155d-102">&lt;sslStreamSecurity&gt;</span></span>
<span data-ttu-id="2155d-103">Reprezentuje element niestandardowego powiązania, który obsługuje kanał zabezpieczenia za pomocą strumienia SSL.</span><span class="sxs-lookup"><span data-stu-id="2155d-103">Represents a custom binding element that supports channel security using an SSL stream.</span></span>  
  
 <span data-ttu-id="2155d-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="2155d-104">\<system.serviceModel></span></span>  
<span data-ttu-id="2155d-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="2155d-105">\<bindings></span></span>  
<span data-ttu-id="2155d-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="2155d-106">\<customBinding></span></span>  
<span data-ttu-id="2155d-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="2155d-107">\<binding></span></span>  
<span data-ttu-id="2155d-108">\<sslStreamSecurity ></span><span class="sxs-lookup"><span data-stu-id="2155d-108">\<sslStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2155d-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="2155d-109">Syntax</span></span>  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"      sslProtocols="Ssl3|Tls|Tls11|Tls12" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2155d-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2155d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2155d-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2155d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2155d-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2155d-112">Attributes</span></span>  
  
|<span data-ttu-id="2155d-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="2155d-113">Attribute</span></span>|<span data-ttu-id="2155d-114">Opis</span><span class="sxs-lookup"><span data-stu-id="2155d-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2155d-115">RequireClientCertificate</span><span class="sxs-lookup"><span data-stu-id="2155d-115">requireClientCertificate</span></span>|<span data-ttu-id="2155d-116">Wartość logiczna określająca, czy dla tego powiązania wymagany jest certyfikat klienta.</span><span class="sxs-lookup"><span data-stu-id="2155d-116">A Boolean value that specifies if a client certificate is required for this binding.</span></span> <span data-ttu-id="2155d-117">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="2155d-117">The default is `false`.</span></span>|  
|<span data-ttu-id="2155d-118">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="2155d-118">sslProtocols</span></span>|<span data-ttu-id="2155d-119">Wartość flagi wyliczenia SslProtocols określająca, które SslProtocols są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="2155d-119">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="2155d-120">Wartość domyślna to Ssl3 &#124; TLS &#124; Tls11 &#124; Tls12.</span><span class="sxs-lookup"><span data-stu-id="2155d-120">The default is Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2155d-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2155d-121">Child Elements</span></span>  
 <span data-ttu-id="2155d-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="2155d-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2155d-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2155d-123">Parent Elements</span></span>  
  
|<span data-ttu-id="2155d-124">Element</span><span class="sxs-lookup"><span data-stu-id="2155d-124">Element</span></span>|<span data-ttu-id="2155d-125">Opis</span><span class="sxs-lookup"><span data-stu-id="2155d-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2155d-126">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="2155d-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="2155d-127">Definiuje wszystkie możliwości powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="2155d-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2155d-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2155d-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
 [<span data-ttu-id="2155d-129">Powiązania</span><span class="sxs-lookup"><span data-stu-id="2155d-129">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="2155d-130">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="2155d-130">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="2155d-131">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="2155d-131">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="2155d-132">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="2155d-132">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
