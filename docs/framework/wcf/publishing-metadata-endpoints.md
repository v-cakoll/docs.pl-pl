---
title: Publikowanie punktów końcowych metadanych
ms.date: 03/30/2017
ms.assetid: 29cd8a60-dfb7-460c-bf5a-c2b31b782671
ms.openlocfilehash: 5de1122a4b603e4c0cd3ae55f3ac7424a7fd77f8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54626596"
---
# <a name="publishing-metadata-endpoints"></a><span data-ttu-id="0f671-102">Publikowanie punktów końcowych metadanych</span><span class="sxs-lookup"><span data-stu-id="0f671-102">Publishing Metadata Endpoints</span></span>
<span data-ttu-id="0f671-103">Usługi Windows Communication Foundation (WCF) publikowanie metadanych przez publikowanie punktów końcowych metadanych.</span><span class="sxs-lookup"><span data-stu-id="0f671-103">Windows Communication Foundation (WCF) services publish metadata by publishing one or more metadata endpoints.</span></span> <span data-ttu-id="0f671-104">Publikowanie metadanych usługi udostępnia metadane za pomocą standardowych protokołów, takich jak żądania WS-MetadataExchange (MEX) i protokołu HTTP/GET.</span><span class="sxs-lookup"><span data-stu-id="0f671-104">Publishing service metadata makes the metadata available using standardized protocols, such as WS-MetadataExchange (MEX) and HTTP/GET requests.</span></span> <span data-ttu-id="0f671-105">Punkty końcowe metadanych są podobne do innych punktów końcowych usługi, w tym mają adres, powiązanie i kontrakt i można ich dodać do hosta usługi przy użyciu konfiguracji lub w kodzie.</span><span class="sxs-lookup"><span data-stu-id="0f671-105">Metadata endpoints are similar to other service endpoints in that they have an address, a binding, and a contract, and they can be added to a service host through configuration or in code.</span></span> <span data-ttu-id="0f671-106">Aby włączyć publikowanie punktów końcowych metadanych, należy dodać <xref:System.ServiceModel.Description.ServiceMetadataBehavior> usługi zachowanie do usługi.</span><span class="sxs-lookup"><span data-stu-id="0f671-106">To enable publishing metadata endpoints, you must add the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> service behavior to the service.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0f671-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="0f671-107">In This Section</span></span>  
 [<span data-ttu-id="0f671-108">Instrukcje: Publikowanie metadanych dla usługi przy użyciu pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="0f671-108">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 <span data-ttu-id="0f671-109">Pokazuje, jak skonfigurować usługę WCF w celu publikowania metadanych, aby klienci mogą pobierać metadane za pomocą usługi WS-MetadataExchange lub żądania HTTP/GET przy użyciu `?wsdl` ciągu zapytania.</span><span class="sxs-lookup"><span data-stu-id="0f671-109">Demonstrates how to configure a WCF service to publish metadata so that clients can retrieve the metadata using a WS-MetadataExchange or an HTTP/GET request using the `?wsdl` query string.</span></span>  
  
 [<span data-ttu-id="0f671-110">Instrukcje: Publikowanie metadanych dla usługi przy użyciu kodu</span><span class="sxs-lookup"><span data-stu-id="0f671-110">How to: Publish Metadata for a Service Using Code</span></span>](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 <span data-ttu-id="0f671-111">Pokazuje, jak włączyć publikowanie metadanych dla usługi WCF w kodzie, tak aby klienci mogą pobierać metadane za pomocą usługi WS-MetadataExchange lub żądania HTTP/GET przy użyciu `?wsdl` ciągu zapytania.</span><span class="sxs-lookup"><span data-stu-id="0f671-111">Demonstrates how to enable metadata publishing for a WCF service in code so that clients can retrieve the metadata using a WS-MetadataExchange or an HTTP/GET request using the `?wsdl` query string.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f671-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0f671-112">See also</span></span>
- [<span data-ttu-id="0f671-113">Publikowanie metadanych</span><span class="sxs-lookup"><span data-stu-id="0f671-113">Publishing Metadata</span></span>](../../../docs/framework/wcf/feature-details/publishing-metadata.md)
