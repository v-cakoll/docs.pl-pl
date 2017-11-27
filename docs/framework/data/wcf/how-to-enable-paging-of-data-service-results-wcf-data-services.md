---
title: "Porady: Włączanie stronicowania wyniki z danymi usługi (usługi danych WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: paging output [WCF Data Services]
ms.assetid: 9a316cbd-9612-4482-a541-a10bc78b2635
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6bf267cdc4ab3ec3bdc82a3da52cef21ef1d6b2b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-enable-paging-of-data-service-results-wcf-data-services"></a><span data-ttu-id="13adf-102">Porady: Włączanie stronicowania wyniki z danymi usługi (usługi danych WCF)</span><span class="sxs-lookup"><span data-stu-id="13adf-102">How to: Enable Paging of Data Service Results (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="13adf-103">pozwala ograniczyć liczbę jednostek zwróconych przez kwerendę usługi danych.</span><span class="sxs-lookup"><span data-stu-id="13adf-103"> enables you to limit the number of entities returned by a data service query.</span></span> <span data-ttu-id="13adf-104">Limity strony są definiowane w metodę, która jest wywoływana, gdy usługa jest zainicjowana i można ustawić osobno dla każdego zestawu jednostek.</span><span class="sxs-lookup"><span data-stu-id="13adf-104">Page limits are defined in the method that is called when the service is initialized and can be set separately for each entity set.</span></span>  
  
 <span data-ttu-id="13adf-105">Gdy jest włączone stronicowanie, końcowy wpis w źródle danych zawiera łącze do następnej strony danych.</span><span class="sxs-lookup"><span data-stu-id="13adf-105">When paging is enabled, the final entry in the feed contains a link to the next page of data.</span></span> <span data-ttu-id="13adf-106">Aby uzyskać więcej informacji, zobacz [Konfigurowanie usługi danych](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="13adf-106">For more information, see [Configuring the Data Service](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="13adf-107">W tym temacie przedstawiono sposób modyfikowania usługi danych, aby włączyć stronicowanie z zwrócony `Customers` i `Orders` zestawów jednostek.</span><span class="sxs-lookup"><span data-stu-id="13adf-107">This topic shows how to modify a data service to enable paging of returned `Customers` and `Orders` entity sets.</span></span> <span data-ttu-id="13adf-108">W przykładzie w tym temacie użyto usługę Northwind przykładowych danych.</span><span class="sxs-lookup"><span data-stu-id="13adf-108">The example in this topic uses the Northwind sample data service.</span></span> <span data-ttu-id="13adf-109">Ta usługa jest utworzone po zakończeniu [szybkiego startu usługi danych WCF](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="13adf-109">This service is created when you complete the [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span></span>  
  
### <a name="how-to-enable-paging-of-returned-customers-and-orders-entity-sets"></a><span data-ttu-id="13adf-110">Jak włączyć stronicowanie zwrócony klienci i zamówienia zestawów jednostek</span><span class="sxs-lookup"><span data-stu-id="13adf-110">How to enable paging of returned Customers and Orders entity sets</span></span>  
  
-   <span data-ttu-id="13adf-111">W kodzie dla usługi data, Zastąp kod symbol zastępczy w `InitializeService` funkcji z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="13adf-111">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>  
  
     [!code-csharp[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind.svc.cs#dataserviceconfigpaging)]
     [!code-vb[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind.svc.vb#dataserviceconfigpaging)]  
  
## <a name="see-also"></a><span data-ttu-id="13adf-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="13adf-112">See Also</span></span>  
 [<span data-ttu-id="13adf-113">Ładowanie odłożone zawartości</span><span class="sxs-lookup"><span data-stu-id="13adf-113">Loading Deferred Content</span></span>](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)  
 [<span data-ttu-id="13adf-114">Porady: obciążenia stronicowanej wyników</span><span class="sxs-lookup"><span data-stu-id="13adf-114">How to: Load Paged Results</span></span>](../../../../docs/framework/data/wcf/how-to-load-paged-results-wcf-data-services.md)
