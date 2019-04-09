---
title: 'Instrukcje: Wykonywanie zapytań w partii (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, batch requests
ms.assetid: 3b4db7df-bd33-43a1-8ea4-63a18e131f97
ms.openlocfilehash: a917659092890c95dfd65ede358d9c4b5a0e62cb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59117913"
---
# <a name="how-to-execute-queries-in-a-batch-wcf-data-services"></a>Instrukcje: Wykonywanie zapytań w partii (WCF Data Services)
Za pomocą [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] biblioteki klienta, można wykonać więcej niż jednego zapytania względem usługi danych w jednej partii. Aby uzyskać więcej informacji, zobacz [przetwarzanie wsadowe operacji](../../../../docs/framework/data/wcf/batching-operations-wcf-data-services.md).  
  
 W przykładzie w tym temacie użyto Northwind przykładowe dane usługi i automatycznie wygenerowany klas usługi danych klienta. Ta usługa i klas danych klienta, są tworzone po ukończeniu [Szybki Start usług danych WCF](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje sposób wywoływania <xref:System.Data.Services.Client.DataServiceContext.ExecuteBatch%2A> metodę, aby wykonać szereg <xref:System.Data.Services.Client.DataServiceRequest%601> obiektów, które zawiera zapytania, które zwracają zarówno `Customers` i `Products` obiektów z usługi danych Northwind. Kolekcja <xref:System.Data.Services.Client.QueryOperationResponse%601> obiektów w zwróconym elemencie <xref:System.Data.Services.Client.DataServiceResponse> są wyliczane i kolekcję obiektów zawartą w każdym <xref:System.Data.Services.Client.QueryOperationResponse%601> również jest wyliczany.  
  
 [!code-csharp[Astoria Northwind Client#BatchQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#batchquery)]
 [!code-vb[Astoria Northwind Client#BatchQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#batchquery)]  
  
## <a name="see-also"></a>Zobacz także

- [Biblioteka klienta usług danych WCF](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
