---
title: 'Instrukcje: wykonywanie zapytań w partii (Usługi danych programu WCF)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, batch requests
ms.assetid: 3b4db7df-bd33-43a1-8ea4-63a18e131f97
ms.openlocfilehash: 0ddf5b4f68ca08fca0c55cfcdfcd5431bcec6de2
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569051"
---
# <a name="how-to-execute-queries-in-a-batch-wcf-data-services"></a>Instrukcje: wykonywanie zapytań w partii (Usługi danych programu WCF)
Za pomocą biblioteki klienta Usługi danych programu WCF można wykonać kilka zapytań dotyczących usługi danych w pojedynczej partii. Aby uzyskać więcej informacji, zobacz [Przetwarzanie wsadowe operacji](batching-operations-wcf-data-services.md).  
  
 W przykładzie w tym temacie jest stosowana usługa danych przykładowych Northwind i klasy usługi danych klientów. Ta usługa i klasy danych klienta są tworzone po zakończeniu [usługi danych programu WCF szybkiego startu](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak wywołać metodę <xref:System.Data.Services.Client.DataServiceContext.ExecuteBatch%2A>, aby wykonać tablicę obiektów <xref:System.Data.Services.Client.DataServiceRequest%601>, które zawierają zapytania, które zwracają zarówno obiekty `Customers`, jak i `Products` z usługi danych Northwind. Kolekcja <xref:System.Data.Services.Client.QueryOperationResponse%601> obiektów w zwróconym <xref:System.Data.Services.Client.DataServiceResponse> jest wyliczana i wyliczana jest kolekcja obiektów zawartych w każdym <xref:System.Data.Services.Client.QueryOperationResponse%601>.  
  
 [!code-csharp[Astoria Northwind Client#BatchQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#batchquery)]
 [!code-vb[Astoria Northwind Client#BatchQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#batchquery)]  
  
## <a name="see-also"></a>Zobacz także

- [Biblioteka klienta usług danych WCF](wcf-data-services-client-library.md)
