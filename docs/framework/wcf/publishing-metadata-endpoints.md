---
title: Publikowanie punktów końcowych metadanych
ms.date: 03/30/2017
ms.assetid: 29cd8a60-dfb7-460c-bf5a-c2b31b782671
ms.openlocfilehash: 4c6ac81f0c97415dc21ff3346178dd1e9936b7a5
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319894"
---
# <a name="publishing-metadata-endpoints"></a><span data-ttu-id="115d1-102">Publikowanie punktów końcowych metadanych</span><span class="sxs-lookup"><span data-stu-id="115d1-102">Publishing Metadata Endpoints</span></span>
<span data-ttu-id="115d1-103">Usługi Windows Communication Foundation (WCF) publikują metadane, publikując co najmniej jeden punkt końcowy metadanych.</span><span class="sxs-lookup"><span data-stu-id="115d1-103">Windows Communication Foundation (WCF) services publish metadata by publishing one or more metadata endpoints.</span></span> <span data-ttu-id="115d1-104">Publikowanie metadanych usługi sprawia, że metadane są dostępne przy użyciu standardowych protokołów, takich jak WS-MetadataExchange (MEX) i HTTP/GET.</span><span class="sxs-lookup"><span data-stu-id="115d1-104">Publishing service metadata makes the metadata available using standardized protocols, such as WS-MetadataExchange (MEX) and HTTP/GET requests.</span></span> <span data-ttu-id="115d1-105">Punkty końcowe metadanych są podobne do innych punktów końcowych usługi, które mają adres, powiązanie i kontrakt oraz mogą być dodawane do hosta usługi za pomocą konfiguracji lub w kodzie.</span><span class="sxs-lookup"><span data-stu-id="115d1-105">Metadata endpoints are similar to other service endpoints in that they have an address, a binding, and a contract, and they can be added to a service host through configuration or in code.</span></span> <span data-ttu-id="115d1-106">Aby włączyć Publikowanie punktów końcowych metadanych, należy dodać do usługi zachowanie usługi <xref:System.ServiceModel.Description.ServiceMetadataBehavior>.</span><span class="sxs-lookup"><span data-stu-id="115d1-106">To enable publishing metadata endpoints, you must add the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> service behavior to the service.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="115d1-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="115d1-107">In This Section</span></span>  
 [<span data-ttu-id="115d1-108">Instrukcje: publikowanie metadanych dla usługi za pomocą pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="115d1-108">How to: Publish Metadata for a Service Using a Configuration File</span></span>](./feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 <span data-ttu-id="115d1-109">Demonstruje sposób konfigurowania usługi WCF w celu publikowania metadanych, dzięki czemu klienci mogą pobierać metadane przy użyciu protokołu WS-MetadataExchange lub żądania HTTP/GET przy użyciu ciągu zapytania `?wsdl`.</span><span class="sxs-lookup"><span data-stu-id="115d1-109">Demonstrates how to configure a WCF service to publish metadata so that clients can retrieve the metadata using a WS-MetadataExchange or an HTTP/GET request using the `?wsdl` query string.</span></span>  
  
 [<span data-ttu-id="115d1-110">Instrukcje: publikowanie metadanych dla usługi przy użyciu kodu</span><span class="sxs-lookup"><span data-stu-id="115d1-110">How to: Publish Metadata for a Service Using Code</span></span>](./feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 <span data-ttu-id="115d1-111">Pokazuje, jak włączyć Publikowanie metadanych dla usługi WCF w kodzie, aby klienci mogli pobrać metadane przy użyciu protokołu WS-MetadataExchange lub żądania HTTP/GET przy użyciu ciągu zapytania `?wsdl`.</span><span class="sxs-lookup"><span data-stu-id="115d1-111">Demonstrates how to enable metadata publishing for a WCF service in code so that clients can retrieve the metadata using a WS-MetadataExchange or an HTTP/GET request using the `?wsdl` query string.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="115d1-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="115d1-112">See also</span></span>

- [<span data-ttu-id="115d1-113">Publikowanie metadanych</span><span class="sxs-lookup"><span data-stu-id="115d1-113">Publishing Metadata</span></span>](./feature-details/publishing-metadata.md)
