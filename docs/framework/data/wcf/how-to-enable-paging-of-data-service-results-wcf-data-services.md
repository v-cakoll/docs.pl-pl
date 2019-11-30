---
title: 'Instrukcje: Włączanie stronicowania wyników usługi danych (Usługi danych programu WCF)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- paging output [WCF Data Services]
ms.assetid: 9a316cbd-9612-4482-a541-a10bc78b2635
ms.openlocfilehash: 6b7cea2475a5c11091a04ef3044bbc958e55fc5d
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569092"
---
# <a name="how-to-enable-paging-of-data-service-results-wcf-data-services"></a>Instrukcje: Włączanie stronicowania wyników usługi danych (Usługi danych programu WCF)
Usługi danych programu WCF pozwala ograniczyć liczbę jednostek zwracanych przez zapytanie usługi danych. Limity stron są zdefiniowane w metodzie, która jest wywoływana, gdy usługa jest inicjowana i można ją ustawić osobno dla każdego zestawu jednostek.  
  
 Po włączeniu stronicowania końcowy wpis w kanale informacyjnym zawiera link do następnej strony danych. Aby uzyskać więcej informacji, zobacz [Konfigurowanie usługi danych](configuring-the-data-service-wcf-data-services.md).  
  
 W tym temacie przedstawiono sposób modyfikowania usługi danych w celu włączenia stronicowania zwracanych `Customers` i `Orders` zestawów jednostek. W przykładzie w tym temacie jest stosowana Przykładowa usługa danych Northwind. Ta usługa jest tworzona po zakończeniu [usługi danych programu WCF przewodnika Szybki Start](quickstart-wcf-data-services.md).  
  
### <a name="how-to-enable-paging-of-returned-customers-and-orders-entity-sets"></a>Jak włączyć stronicowanie zwracanych klientów i zestawów jednostek zamówień  
  
- W kodzie usługi danych Zastąp symbol zastępczy w funkcji `InitializeService` następującym:  
  
     [!code-csharp[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind.svc.cs#dataserviceconfigpaging)]
     [!code-vb[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind.svc.vb#dataserviceconfigpaging)]  
  
## <a name="see-also"></a>Zobacz także

- [Ładowanie odroczonej zawartości](loading-deferred-content-wcf-data-services.md)
- [Instrukcje: Ładowanie stronicowanych wyników](how-to-load-paged-results-wcf-data-services.md)
