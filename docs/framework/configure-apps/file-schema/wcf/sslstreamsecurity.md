---
title: <sslStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
ms.openlocfilehash: 5ed87adfb3963513602844fc69afce8f7994fa8e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932420"
---
# <a name="sslstreamsecurity"></a><span data-ttu-id="01307-101">\<sslStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="01307-101">\<sslStreamSecurity></span></span>
<span data-ttu-id="01307-102">Reprezentuje element niestandardowego powiązania, który obsługuje zabezpieczenia kanału przy użyciu strumienia SSL.</span><span class="sxs-lookup"><span data-stu-id="01307-102">Represents a custom binding element that supports channel security using an SSL stream.</span></span>  
  
 <span data-ttu-id="01307-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="01307-103">\<system.serviceModel></span></span>  
<span data-ttu-id="01307-104">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="01307-104">\<bindings></span></span>  
<span data-ttu-id="01307-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="01307-105">\<customBinding></span></span>  
<span data-ttu-id="01307-106">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="01307-106">\<binding></span></span>  
<span data-ttu-id="01307-107">\<sslStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="01307-107">\<sslStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01307-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="01307-108">Syntax</span></span>  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"
                   sslProtocols="Ssl3|Tls|Tls11|Tls12" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="01307-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="01307-109">Attributes and Elements</span></span>  
 <span data-ttu-id="01307-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="01307-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="01307-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="01307-111">Attributes</span></span>  
  
|<span data-ttu-id="01307-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="01307-112">Attribute</span></span>|<span data-ttu-id="01307-113">Opis</span><span class="sxs-lookup"><span data-stu-id="01307-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="01307-114">requireClientCertificate</span><span class="sxs-lookup"><span data-stu-id="01307-114">requireClientCertificate</span></span>|<span data-ttu-id="01307-115">Wartość logiczna określająca, czy certyfikat klienta jest wymagany dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="01307-115">A Boolean value that specifies if a client certificate is required for this binding.</span></span> <span data-ttu-id="01307-116">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="01307-116">The default is `false`.</span></span>|  
|<span data-ttu-id="01307-117">SslProtocols określająca</span><span class="sxs-lookup"><span data-stu-id="01307-117">sslProtocols</span></span>|<span data-ttu-id="01307-118">Wartość flagi wyliczenia SslProtocols określająca, która określa, które SslProtocols określająca są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="01307-118">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="01307-119">Wartość domyślna to Ssl3&#124;TLS&#124;Tls11&#124;Tls12.</span><span class="sxs-lookup"><span data-stu-id="01307-119">The default is Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="01307-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="01307-120">Child Elements</span></span>  
 <span data-ttu-id="01307-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="01307-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="01307-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="01307-122">Parent Elements</span></span>  
  
|<span data-ttu-id="01307-123">Element</span><span class="sxs-lookup"><span data-stu-id="01307-123">Element</span></span>|<span data-ttu-id="01307-124">Opis</span><span class="sxs-lookup"><span data-stu-id="01307-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="01307-125">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="01307-125">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="01307-126">Definiuje wszystkie możliwości powiązań niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="01307-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="01307-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="01307-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>
- [<span data-ttu-id="01307-128">Powiązania</span><span class="sxs-lookup"><span data-stu-id="01307-128">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="01307-129">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="01307-129">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="01307-130">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="01307-130">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="01307-131">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="01307-131">\<customBinding></span></span>](custombinding.md)
