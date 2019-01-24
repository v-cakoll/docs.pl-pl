---
title: '&lt;sslStreamSecurity&gt;'
ms.date: 03/30/2017
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
ms.openlocfilehash: fe633aa1ed2b165a83f415748b70b6a66bbb0130
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54540925"
---
# <a name="ltsslstreamsecuritygt"></a><span data-ttu-id="b986d-102">&lt;sslStreamSecurity&gt;</span><span class="sxs-lookup"><span data-stu-id="b986d-102">&lt;sslStreamSecurity&gt;</span></span>
<span data-ttu-id="b986d-103">Reprezentuje element niestandardowego powiązania, który obsługuje kanał zabezpieczenia za pomocą strumienia SSL.</span><span class="sxs-lookup"><span data-stu-id="b986d-103">Represents a custom binding element that supports channel security using an SSL stream.</span></span>  
  
 <span data-ttu-id="b986d-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="b986d-104">\<system.serviceModel></span></span>  
<span data-ttu-id="b986d-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="b986d-105">\<bindings></span></span>  
<span data-ttu-id="b986d-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="b986d-106">\<customBinding></span></span>  
<span data-ttu-id="b986d-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="b986d-107">\<binding></span></span>  
<span data-ttu-id="b986d-108">\<sslStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="b986d-108">\<sslStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b986d-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="b986d-109">Syntax</span></span>  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"
                   sslProtocols="Ssl3|Tls|Tls11|Tls12" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b986d-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b986d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b986d-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b986d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b986d-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b986d-112">Attributes</span></span>  
  
|<span data-ttu-id="b986d-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b986d-113">Attribute</span></span>|<span data-ttu-id="b986d-114">Opis</span><span class="sxs-lookup"><span data-stu-id="b986d-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b986d-115">requireClientCertificate</span><span class="sxs-lookup"><span data-stu-id="b986d-115">requireClientCertificate</span></span>|<span data-ttu-id="b986d-116">Wartość logiczna, która określa, czy certyfikat klienta jest wymagany przez to powiązanie.</span><span class="sxs-lookup"><span data-stu-id="b986d-116">A Boolean value that specifies if a client certificate is required for this binding.</span></span> <span data-ttu-id="b986d-117">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="b986d-117">The default is `false`.</span></span>|  
|<span data-ttu-id="b986d-118">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="b986d-118">sslProtocols</span></span>|<span data-ttu-id="b986d-119">Wartość flagi wyliczenia SslProtocols określająca SslProtocols, które są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="b986d-119">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="b986d-120">Wartość domyślna to Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span><span class="sxs-lookup"><span data-stu-id="b986d-120">The default is Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b986d-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b986d-121">Child Elements</span></span>  
 <span data-ttu-id="b986d-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="b986d-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b986d-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b986d-123">Parent Elements</span></span>  
  
|<span data-ttu-id="b986d-124">Element</span><span class="sxs-lookup"><span data-stu-id="b986d-124">Element</span></span>|<span data-ttu-id="b986d-125">Opis</span><span class="sxs-lookup"><span data-stu-id="b986d-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b986d-126">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="b986d-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="b986d-127">Definiuje wszystkie funkcje powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="b986d-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b986d-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b986d-128">See also</span></span>
- <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>
- [<span data-ttu-id="b986d-129">Powiązania</span><span class="sxs-lookup"><span data-stu-id="b986d-129">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="b986d-130">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="b986d-130">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="b986d-131">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="b986d-131">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="b986d-132">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="b986d-132">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
