---
title: '&lt;sslStreamSecurity&gt;'
ms.date: 03/30/2017
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
author: BrucePerlerMS
ms.openlocfilehash: 6eacf1833ecf980696d75c5dbcaaba3ba6403d92
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47087453"
---
# <a name="ltsslstreamsecuritygt"></a><span data-ttu-id="0cf41-102">&lt;sslStreamSecurity&gt;</span><span class="sxs-lookup"><span data-stu-id="0cf41-102">&lt;sslStreamSecurity&gt;</span></span>
<span data-ttu-id="0cf41-103">Reprezentuje element niestandardowego powiązania, który obsługuje kanał zabezpieczenia za pomocą strumienia SSL.</span><span class="sxs-lookup"><span data-stu-id="0cf41-103">Represents a custom binding element that supports channel security using an SSL stream.</span></span>  
  
 <span data-ttu-id="0cf41-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="0cf41-104">\<system.serviceModel></span></span>  
<span data-ttu-id="0cf41-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="0cf41-105">\<bindings></span></span>  
<span data-ttu-id="0cf41-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="0cf41-106">\<customBinding></span></span>  
<span data-ttu-id="0cf41-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="0cf41-107">\<binding></span></span>  
<span data-ttu-id="0cf41-108">\<sslStreamSecurity ></span><span class="sxs-lookup"><span data-stu-id="0cf41-108">\<sslStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cf41-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="0cf41-109">Syntax</span></span>  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"      sslProtocols="Ssl3|Tls|Tls11|Tls12" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0cf41-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0cf41-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0cf41-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0cf41-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0cf41-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0cf41-112">Attributes</span></span>  
  
|<span data-ttu-id="0cf41-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="0cf41-113">Attribute</span></span>|<span data-ttu-id="0cf41-114">Opis</span><span class="sxs-lookup"><span data-stu-id="0cf41-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0cf41-115">requireClientCertificate</span><span class="sxs-lookup"><span data-stu-id="0cf41-115">requireClientCertificate</span></span>|<span data-ttu-id="0cf41-116">Wartość logiczna, która określa, czy certyfikat klienta jest wymagany przez to powiązanie.</span><span class="sxs-lookup"><span data-stu-id="0cf41-116">A Boolean value that specifies if a client certificate is required for this binding.</span></span> <span data-ttu-id="0cf41-117">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="0cf41-117">The default is `false`.</span></span>|  
|<span data-ttu-id="0cf41-118">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="0cf41-118">sslProtocols</span></span>|<span data-ttu-id="0cf41-119">Wartość flagi wyliczenia SslProtocols określająca SslProtocols, które są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="0cf41-119">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="0cf41-120">Wartość domyślna to Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span><span class="sxs-lookup"><span data-stu-id="0cf41-120">The default is Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0cf41-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0cf41-121">Child Elements</span></span>  
 <span data-ttu-id="0cf41-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="0cf41-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0cf41-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0cf41-123">Parent Elements</span></span>  
  
|<span data-ttu-id="0cf41-124">Element</span><span class="sxs-lookup"><span data-stu-id="0cf41-124">Element</span></span>|<span data-ttu-id="0cf41-125">Opis</span><span class="sxs-lookup"><span data-stu-id="0cf41-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0cf41-126">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="0cf41-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="0cf41-127">Definiuje wszystkie funkcje powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="0cf41-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0cf41-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0cf41-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
 [<span data-ttu-id="0cf41-129">Powiązania</span><span class="sxs-lookup"><span data-stu-id="0cf41-129">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="0cf41-130">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="0cf41-130">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="0cf41-131">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="0cf41-131">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="0cf41-132">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="0cf41-132">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
