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
ms.openlocfilehash: 5c801562339f02ff983bb5a755fda6718185ba5a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltsslstreamsecuritygt"></a><span data-ttu-id="b5289-102">&lt;sslStreamSecurity&gt;</span><span class="sxs-lookup"><span data-stu-id="b5289-102">&lt;sslStreamSecurity&gt;</span></span>
<span data-ttu-id="b5289-103">Reprezentuje element niestandardowego powiązania, który obsługuje kanał zabezpieczenia za pomocą strumienia SSL.</span><span class="sxs-lookup"><span data-stu-id="b5289-103">Represents a custom binding element that supports channel security using an SSL stream.</span></span>  
  
 <span data-ttu-id="b5289-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="b5289-104">\<system.serviceModel></span></span>  
<span data-ttu-id="b5289-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="b5289-105">\<bindings></span></span>  
<span data-ttu-id="b5289-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="b5289-106">\<customBinding></span></span>  
<span data-ttu-id="b5289-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="b5289-107">\<binding></span></span>  
<span data-ttu-id="b5289-108">\<sslStreamSecurity ></span><span class="sxs-lookup"><span data-stu-id="b5289-108">\<sslStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5289-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="b5289-109">Syntax</span></span>  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"      sslProtocols="Ssl3|Tls|Tls11|Tls12" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b5289-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b5289-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b5289-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b5289-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b5289-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b5289-112">Attributes</span></span>  
  
|<span data-ttu-id="b5289-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b5289-113">Attribute</span></span>|<span data-ttu-id="b5289-114">Opis</span><span class="sxs-lookup"><span data-stu-id="b5289-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b5289-115">RequireClientCertificate</span><span class="sxs-lookup"><span data-stu-id="b5289-115">requireClientCertificate</span></span>|<span data-ttu-id="b5289-116">Wartość logiczna określająca, czy dla tego powiązania wymagany jest certyfikat klienta.</span><span class="sxs-lookup"><span data-stu-id="b5289-116">A Boolean value that specifies if a client certificate is required for this binding.</span></span> <span data-ttu-id="b5289-117">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="b5289-117">The default is `false`.</span></span>|  
|<span data-ttu-id="b5289-118">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="b5289-118">sslProtocols</span></span>|<span data-ttu-id="b5289-119">Wartość flagi wyliczenia SslProtocols określająca, które SslProtocols są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="b5289-119">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="b5289-120">Wartość domyślna to Ssl3 &#124; TLS &#124; Tls11 &#124; Tls12.</span><span class="sxs-lookup"><span data-stu-id="b5289-120">The default is Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b5289-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b5289-121">Child Elements</span></span>  
 <span data-ttu-id="b5289-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="b5289-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b5289-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b5289-123">Parent Elements</span></span>  
  
|<span data-ttu-id="b5289-124">Element</span><span class="sxs-lookup"><span data-stu-id="b5289-124">Element</span></span>|<span data-ttu-id="b5289-125">Opis</span><span class="sxs-lookup"><span data-stu-id="b5289-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b5289-126">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="b5289-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="b5289-127">Definiuje wszystkie możliwości powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="b5289-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b5289-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b5289-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
 [<span data-ttu-id="b5289-129">Powiązania</span><span class="sxs-lookup"><span data-stu-id="b5289-129">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="b5289-130">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="b5289-130">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="b5289-131">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="b5289-131">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="b5289-132">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="b5289-132">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
