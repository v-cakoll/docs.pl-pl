---
title: <sslStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
ms.openlocfilehash: f66569f36dc61a063b79a088dcbc405126a074d8
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55284600"
---
# <a name="sslstreamsecurity"></a><span data-ttu-id="55ea6-101">\<sslStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="55ea6-101">\<sslStreamSecurity></span></span>
<span data-ttu-id="55ea6-102">Reprezentuje element niestandardowego powiązania, który obsługuje kanał zabezpieczenia za pomocą strumienia SSL.</span><span class="sxs-lookup"><span data-stu-id="55ea6-102">Represents a custom binding element that supports channel security using an SSL stream.</span></span>  
  
 <span data-ttu-id="55ea6-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="55ea6-103">\<system.serviceModel></span></span>  
<span data-ttu-id="55ea6-104">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="55ea6-104">\<bindings></span></span>  
<span data-ttu-id="55ea6-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="55ea6-105">\<customBinding></span></span>  
<span data-ttu-id="55ea6-106">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="55ea6-106">\<binding></span></span>  
<span data-ttu-id="55ea6-107">\<sslStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="55ea6-107">\<sslStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55ea6-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="55ea6-108">Syntax</span></span>  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"
                   sslProtocols="Ssl3|Tls|Tls11|Tls12" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="55ea6-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="55ea6-109">Attributes and Elements</span></span>  
 <span data-ttu-id="55ea6-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="55ea6-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="55ea6-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="55ea6-111">Attributes</span></span>  
  
|<span data-ttu-id="55ea6-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="55ea6-112">Attribute</span></span>|<span data-ttu-id="55ea6-113">Opis</span><span class="sxs-lookup"><span data-stu-id="55ea6-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="55ea6-114">requireClientCertificate</span><span class="sxs-lookup"><span data-stu-id="55ea6-114">requireClientCertificate</span></span>|<span data-ttu-id="55ea6-115">Wartość logiczna, która określa, czy certyfikat klienta jest wymagany przez to powiązanie.</span><span class="sxs-lookup"><span data-stu-id="55ea6-115">A Boolean value that specifies if a client certificate is required for this binding.</span></span> <span data-ttu-id="55ea6-116">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="55ea6-116">The default is `false`.</span></span>|  
|<span data-ttu-id="55ea6-117">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="55ea6-117">sslProtocols</span></span>|<span data-ttu-id="55ea6-118">Wartość flagi wyliczenia SslProtocols określająca SslProtocols, które są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="55ea6-118">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="55ea6-119">Wartość domyślna to Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span><span class="sxs-lookup"><span data-stu-id="55ea6-119">The default is Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="55ea6-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="55ea6-120">Child Elements</span></span>  
 <span data-ttu-id="55ea6-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="55ea6-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="55ea6-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="55ea6-122">Parent Elements</span></span>  
  
|<span data-ttu-id="55ea6-123">Element</span><span class="sxs-lookup"><span data-stu-id="55ea6-123">Element</span></span>|<span data-ttu-id="55ea6-124">Opis</span><span class="sxs-lookup"><span data-stu-id="55ea6-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="55ea6-125">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="55ea6-125">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="55ea6-126">Definiuje wszystkie funkcje powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="55ea6-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="55ea6-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="55ea6-127">See also</span></span>
- <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>
- [<span data-ttu-id="55ea6-128">Powiązania</span><span class="sxs-lookup"><span data-stu-id="55ea6-128">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="55ea6-129">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="55ea6-129">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="55ea6-130">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="55ea6-130">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="55ea6-131">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="55ea6-131">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
