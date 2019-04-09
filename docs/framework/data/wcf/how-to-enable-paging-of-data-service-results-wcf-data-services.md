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
# <a name="how-to-enable-paging-of-data-service-results-wcf-data-services"></a>Instrukcje: Włączanie stronicowania wyników usługi danych (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Umożliwia ograniczenie liczby jednostek zwróconych przez zapytanie usługi danych. Limity strony są definiowane w metodzie, która jest wywoływana, gdy usługa zostanie zainicjowana i mogą być ustawione osobno dla każdego zestawu jednostek.  
  
 Gdy jest włączone stronicowanie, końcowy wpis w źródle danych zawiera łącze do następnej strony danych. Aby uzyskać więcej informacji, zobacz [Konfigurowanie usługi danych](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).  
  
 W tym temacie przedstawiono sposób modyfikowania usługi danych pozwalają na stronicowanie zwrócone `Customers` i `Orders` zestawy jednostek. W przykładzie w tym temacie użyto usługi Northwind przykładowych danych. Ta usługa zostanie utworzona po zakończeniu [Szybki Start usług danych WCF](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
### <a name="how-to-enable-paging-of-returned-customers-and-orders-entity-sets"></a>Jak włączyć stronicowania zwracane zestawy jednostek klienci i zamówienia  
  
-   W kodzie dla usługi danych, Zastąp kod symbolu zastępczego `InitializeService` funkcji następującym kodem:  
  
     [!code-csharp[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind.svc.cs#dataserviceconfigpaging)]
     [!code-vb[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind.svc.vb#dataserviceconfigpaging)]  
  
## <a name="see-also"></a>Zobacz także

- [Ładowanie odroczonej zawartości](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)
- [Instrukcje: Ładowanie stronicowanych wyników](../../../../docs/framework/data/wcf/how-to-load-paged-results-wcf-data-services.md)
