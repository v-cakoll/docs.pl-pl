---
title: <sslStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
ms.openlocfilehash: 9b7092878c604142c29dcd8d27e3c458d203f9fa
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399528"
---
# <a name="sslstreamsecurity"></a><span data-ttu-id="e6594-101">\<sslStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="e6594-101">\<sslStreamSecurity></span></span>
<span data-ttu-id="e6594-102">Reprezentuje element niestandardowego powiązania, który obsługuje zabezpieczenia kanału przy użyciu strumienia SSL.</span><span class="sxs-lookup"><span data-stu-id="e6594-102">Represents a custom binding element that supports channel security using an SSL stream.</span></span>  
  
<span data-ttu-id="e6594-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e6594-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e6594-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="e6594-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="e6594-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> powiązań**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="e6594-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="e6594-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<niestandardowy >Binding**](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="e6594-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="e6594-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> powiązania**</span><span class="sxs-lookup"><span data-stu-id="e6594-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="e6594-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<sslStreamSecurity >**</span><span class="sxs-lookup"><span data-stu-id="e6594-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sslStreamSecurity>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6594-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="e6594-109">Syntax</span></span>  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"
                   sslProtocols="Ssl3|Tls|Tls11|Tls12" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e6594-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e6594-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e6594-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e6594-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e6594-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e6594-112">Attributes</span></span>  
  
|<span data-ttu-id="e6594-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e6594-113">Attribute</span></span>|<span data-ttu-id="e6594-114">Opis</span><span class="sxs-lookup"><span data-stu-id="e6594-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e6594-115">requireClientCertificate</span><span class="sxs-lookup"><span data-stu-id="e6594-115">requireClientCertificate</span></span>|<span data-ttu-id="e6594-116">Wartość logiczna określająca, czy certyfikat klienta jest wymagany dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="e6594-116">A Boolean value that specifies if a client certificate is required for this binding.</span></span> <span data-ttu-id="e6594-117">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="e6594-117">The default is `false`.</span></span>|  
|<span data-ttu-id="e6594-118">SslProtocols określająca</span><span class="sxs-lookup"><span data-stu-id="e6594-118">sslProtocols</span></span>|<span data-ttu-id="e6594-119">Wartość flagi wyliczenia SslProtocols określająca, która określa, które SslProtocols określająca są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="e6594-119">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="e6594-120">Wartość domyślna to Ssl3&#124;TLS&#124;Tls11&#124;Tls12.</span><span class="sxs-lookup"><span data-stu-id="e6594-120">The default is Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e6594-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e6594-121">Child Elements</span></span>  
 <span data-ttu-id="e6594-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="e6594-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e6594-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e6594-123">Parent Elements</span></span>  
  
|<span data-ttu-id="e6594-124">Element</span><span class="sxs-lookup"><span data-stu-id="e6594-124">Element</span></span>|<span data-ttu-id="e6594-125">Opis</span><span class="sxs-lookup"><span data-stu-id="e6594-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e6594-126">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="e6594-126">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="e6594-127">Definiuje wszystkie możliwości powiązań niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="e6594-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e6594-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e6594-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>
- [<span data-ttu-id="e6594-129">Powiązania</span><span class="sxs-lookup"><span data-stu-id="e6594-129">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="e6594-130">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="e6594-130">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="e6594-131">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="e6594-131">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="e6594-132">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="e6594-132">\<customBinding></span></span>](custombinding.md)
