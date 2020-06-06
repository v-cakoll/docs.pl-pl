---
title: <sslStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
ms.openlocfilehash: c5c7ec2b18143ff4d71540a60e24b8225ca4db16
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738593"
---
# \<sslStreamSecurity>
<span data-ttu-id="49b6f-101">Reprezentuje element niestandardowego powiązania, który obsługuje zabezpieczenia kanału przy użyciu strumienia SSL.</span><span class="sxs-lookup"><span data-stu-id="49b6f-101">Represents a custom binding element that supports channel security using an SSL stream.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sslStreamSecurity>**  
  
## <a name="syntax"></a><span data-ttu-id="49b6f-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="49b6f-102">Syntax</span></span>  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"
                   sslProtocols="Ssl3|Tls|Tls11|Tls12" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="49b6f-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="49b6f-103">Attributes and Elements</span></span>  
 <span data-ttu-id="49b6f-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="49b6f-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="49b6f-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="49b6f-105">Attributes</span></span>  
  
|<span data-ttu-id="49b6f-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="49b6f-106">Attribute</span></span>|<span data-ttu-id="49b6f-107">Opis</span><span class="sxs-lookup"><span data-stu-id="49b6f-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="49b6f-108">requireClientCertificate</span><span class="sxs-lookup"><span data-stu-id="49b6f-108">requireClientCertificate</span></span>|<span data-ttu-id="49b6f-109">Wartość logiczna określająca, czy certyfikat klienta jest wymagany dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="49b6f-109">A Boolean value that specifies if a client certificate is required for this binding.</span></span> <span data-ttu-id="49b6f-110">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="49b6f-110">The default is `false`.</span></span>|  
|<span data-ttu-id="49b6f-111">SslProtocols określająca</span><span class="sxs-lookup"><span data-stu-id="49b6f-111">sslProtocols</span></span>|<span data-ttu-id="49b6f-112">Wartość flagi wyliczenia SslProtocols określająca, która określa, które SslProtocols określająca są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="49b6f-112">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="49b6f-113">Wartość domyślna to Ssl3&#124;TLS&#124;Tls11&#124;Tls12.</span><span class="sxs-lookup"><span data-stu-id="49b6f-113">The default is Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="49b6f-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="49b6f-114">Child Elements</span></span>  
 <span data-ttu-id="49b6f-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="49b6f-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="49b6f-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="49b6f-116">Parent Elements</span></span>  
  
|<span data-ttu-id="49b6f-117">Element</span><span class="sxs-lookup"><span data-stu-id="49b6f-117">Element</span></span>|<span data-ttu-id="49b6f-118">Opis</span><span class="sxs-lookup"><span data-stu-id="49b6f-118">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="49b6f-119">Definiuje wszystkie możliwości powiązań niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="49b6f-119">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="49b6f-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="49b6f-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>
- [<span data-ttu-id="49b6f-121">Powiązania</span><span class="sxs-lookup"><span data-stu-id="49b6f-121">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="49b6f-122">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="49b6f-122">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="49b6f-123">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="49b6f-123">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
