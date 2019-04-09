---
title: 'Instrukcje: Włączanie stronicowania wyników usługi danych (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- paging output [WCF Data Services]
ms.assetid: 9a316cbd-9612-4482-a541-a10bc78b2635
ms.openlocfilehash: 77dbeba89b352fa470ab0523a830db9175a1a21a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122905"
---
# <a name="how-to-enable-paging-of-data-service-results-wcf-data-services"></a><span data-ttu-id="8f627-102">Instrukcje: Włączanie stronicowania wyników usługi danych (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="8f627-102">How to: Enable Paging of Data Service Results (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] <span data-ttu-id="8f627-103">Umożliwia ograniczenie liczby jednostek zwróconych przez zapytanie usługi danych.</span><span class="sxs-lookup"><span data-stu-id="8f627-103">enables you to limit the number of entities returned by a data service query.</span></span> <span data-ttu-id="8f627-104">Limity strony są definiowane w metodzie, która jest wywoływana, gdy usługa zostanie zainicjowana i mogą być ustawione osobno dla każdego zestawu jednostek.</span><span class="sxs-lookup"><span data-stu-id="8f627-104">Page limits are defined in the method that is called when the service is initialized and can be set separately for each entity set.</span></span>  
  
 <span data-ttu-id="8f627-105">Gdy jest włączone stronicowanie, końcowy wpis w źródle danych zawiera łącze do następnej strony danych.</span><span class="sxs-lookup"><span data-stu-id="8f627-105">When paging is enabled, the final entry in the feed contains a link to the next page of data.</span></span> <span data-ttu-id="8f627-106">Aby uzyskać więcej informacji, zobacz [Konfigurowanie usługi danych](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="8f627-106">For more information, see [Configuring the Data Service](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="8f627-107">W tym temacie przedstawiono sposób modyfikowania usługi danych pozwalają na stronicowanie zwrócone `Customers` i `Orders` zestawy jednostek.</span><span class="sxs-lookup"><span data-stu-id="8f627-107">This topic shows how to modify a data service to enable paging of returned `Customers` and `Orders` entity sets.</span></span> <span data-ttu-id="8f627-108">W przykładzie w tym temacie użyto usługi Northwind przykładowych danych.</span><span class="sxs-lookup"><span data-stu-id="8f627-108">The example in this topic uses the Northwind sample data service.</span></span> <span data-ttu-id="8f627-109">Ta usługa zostanie utworzona po zakończeniu [Szybki Start usług danych WCF](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="8f627-109">This service is created when you complete the [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span></span>  
  
### <a name="how-to-enable-paging-of-returned-customers-and-orders-entity-sets"></a><span data-ttu-id="8f627-110">Jak włączyć stronicowania zwracane zestawy jednostek klienci i zamówienia</span><span class="sxs-lookup"><span data-stu-id="8f627-110">How to enable paging of returned Customers and Orders entity sets</span></span>  
  
-   <span data-ttu-id="8f627-111">W kodzie dla usługi danych, Zastąp kod symbolu zastępczego `InitializeService` funkcji następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="8f627-111">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>  
  
     [!code-csharp[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind.svc.cs#dataserviceconfigpaging)]
     [!code-vb[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind.svc.vb#dataserviceconfigpaging)]  
  
## <a name="see-also"></a><span data-ttu-id="8f627-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8f627-112">See also</span></span>

- [<span data-ttu-id="8f627-113">Ładowanie odroczonej zawartości</span><span class="sxs-lookup"><span data-stu-id="8f627-113">Loading Deferred Content</span></span>](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)
- [<span data-ttu-id="8f627-114">Instrukcje: Ładowanie stronicowanych wyników</span><span class="sxs-lookup"><span data-stu-id="8f627-114">How to: Load Paged Results</span></span>](../../../../docs/framework/data/wcf/how-to-load-paged-results-wcf-data-services.md)
