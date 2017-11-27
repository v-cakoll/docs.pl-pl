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
# <a name="how-to-enable-paging-of-data-service-results-wcf-data-services"></a>Porady: Włączanie stronicowania wyniki z danymi usługi (usługi danych WCF)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]pozwala ograniczyć liczbę jednostek zwróconych przez kwerendę usługi danych. Limity strony są definiowane w metodę, która jest wywoływana, gdy usługa jest zainicjowana i można ustawić osobno dla każdego zestawu jednostek.  
  
 Gdy jest włączone stronicowanie, końcowy wpis w źródle danych zawiera łącze do następnej strony danych. Aby uzyskać więcej informacji, zobacz [Konfigurowanie usługi danych](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).  
  
 W tym temacie przedstawiono sposób modyfikowania usługi danych, aby włączyć stronicowanie z zwrócony `Customers` i `Orders` zestawów jednostek. W przykładzie w tym temacie użyto usługę Northwind przykładowych danych. Ta usługa jest utworzone po zakończeniu [szybkiego startu usługi danych WCF](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
### <a name="how-to-enable-paging-of-returned-customers-and-orders-entity-sets"></a>Jak włączyć stronicowanie zwrócony klienci i zamówienia zestawów jednostek  
  
-   W kodzie dla usługi data, Zastąp kod symbol zastępczy w `InitializeService` funkcji z następujących czynności:  
  
     [!code-csharp[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind.svc.cs#dataserviceconfigpaging)]
     [!code-vb[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind.svc.vb#dataserviceconfigpaging)]  
  
## <a name="see-also"></a>Zobacz też  
 [Ładowanie odłożone zawartości](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)  
 [Porady: obciążenia stronicowanej wyników](../../../../docs/framework/data/wcf/how-to-load-paged-results-wcf-data-services.md)
