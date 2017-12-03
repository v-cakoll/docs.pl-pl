---
title: "Publikowanie punktów końcowych metadanych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 29cd8a60-dfb7-460c-bf5a-c2b31b782671
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 64032fbc675e30e9f01a5db4d56ecc36574e08de
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="publishing-metadata-endpoints"></a><span data-ttu-id="15250-102">Publikowanie punktów końcowych metadanych</span><span class="sxs-lookup"><span data-stu-id="15250-102">Publishing Metadata Endpoints</span></span>
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]<span data-ttu-id="15250-103">usługi Publikowanie metadanych przez publikowanie punkty końcowe metadanych.</span><span class="sxs-lookup"><span data-stu-id="15250-103"> services publish metadata by publishing one or more metadata endpoints.</span></span> <span data-ttu-id="15250-104">Publikowanie metadanych usługi udostępnia metadane za pomocą standardowych protokołów, takich jak żądania WS-MetadataExchange (MEX) i HTTP/GET.</span><span class="sxs-lookup"><span data-stu-id="15250-104">Publishing service metadata makes the metadata available using standardized protocols, such as WS-MetadataExchange (MEX) and HTTP/GET requests.</span></span> <span data-ttu-id="15250-105">Punkty końcowe metadanych są podobne do innych punktów końcowych usługi, w tym mają address, binding i kontrakt i będzie możliwe ich dodanie do usługi hosta za pomocą konfiguracji lub w kodzie.</span><span class="sxs-lookup"><span data-stu-id="15250-105">Metadata endpoints are similar to other service endpoints in that they have an address, a binding, and a contract, and they can be added to a service host through configuration or in code.</span></span> <span data-ttu-id="15250-106">Aby włączyć publikowanie punktów końcowych metadanych, należy dodać <xref:System.ServiceModel.Description.ServiceMetadataBehavior> usługi zachowania do usługi.</span><span class="sxs-lookup"><span data-stu-id="15250-106">To enable publishing metadata endpoints, you must add the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> service behavior to the service.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="15250-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="15250-107">In This Section</span></span>  
 [<span data-ttu-id="15250-108">Porady: Publikowanie metadanych dla usługi przy użyciu pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="15250-108">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 <span data-ttu-id="15250-109">Pokazuje, jak skonfigurować [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Publikowanie metadanych, dzięki czemu klienci mogą pobierać za pomocą usługi WS-MetadataExchange lub żądania HTTP/GET przy użyciu usługi `?wsdl` ciągu zapytania.</span><span class="sxs-lookup"><span data-stu-id="15250-109">Demonstrates how to configure a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service to publish metadata so that clients can retrieve the metadata using a WS-MetadataExchange or an HTTP/GET request using the `?wsdl` query string.</span></span>  
  
 [<span data-ttu-id="15250-110">Porady: Publikowanie metadanych dla usługi przy użyciu kodu</span><span class="sxs-lookup"><span data-stu-id="15250-110">How to: Publish Metadata for a Service Using Code</span></span>](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 <span data-ttu-id="15250-111">Pokazuje, jak włączyć publikowanie metadanych dla [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usługi w kodzie, dzięki czemu klienci mogą pobierać za pomocą usługi WS-MetadataExchange lub żądania HTTP/GET przy użyciu `?wsdl` ciągu zapytania.</span><span class="sxs-lookup"><span data-stu-id="15250-111">Demonstrates how to enable metadata publishing for a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service in code so that clients can retrieve the metadata using a WS-MetadataExchange or an HTTP/GET request using the `?wsdl` query string.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15250-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="15250-112">See Also</span></span>  
 [<span data-ttu-id="15250-113">Publikowanie metadanych</span><span class="sxs-lookup"><span data-stu-id="15250-113">Publishing Metadata</span></span>](../../../docs/framework/wcf/feature-details/publishing-metadata.md)
