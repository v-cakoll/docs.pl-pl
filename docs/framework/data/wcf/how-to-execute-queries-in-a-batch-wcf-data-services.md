---
title: 'Instrukcje: Wykonywanie zapytań w partii (Usługi danych programu WCF)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, batch requests
ms.assetid: 3b4db7df-bd33-43a1-8ea4-63a18e131f97
ms.openlocfilehash: a825fe83ff62d935740fb69871ba2d1e2120e9ec
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790490"
---
# <a name="how-to-execute-queries-in-a-batch-wcf-data-services"></a>Instrukcje: Wykonywanie zapytań w partii (Usługi danych programu WCF)
Za pomocą [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] biblioteki klienckiej można wykonać kilka zapytań dotyczących usługi danych w pojedynczej partii. Aby uzyskać więcej informacji, zobacz [Przetwarzanie wsadowe operacji](batching-operations-wcf-data-services.md).  
  
 W przykładzie w tym temacie jest stosowana usługa danych przykładowych Northwind i klasy usługi danych klientów. Ta usługa i klasy danych klienta są tworzone po zakończeniu [usługi danych programu WCF szybkiego startu](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Przykład  
 <xref:System.Data.Services.Client.DataServiceContext.ExecuteBatch%2A> Poniższy przykład pokazuje, jak wywołać metodę, aby wykonać <xref:System.Data.Services.Client.DataServiceRequest%601> tablicę obiektów, które zawierają zapytania, które zwracają zarówno `Customers` obiekty `Products` , jak i z usługi danych Northwind. Kolekcja <xref:System.Data.Services.Client.QueryOperationResponse%601> obiektów w zwracanym <xref:System.Data.Services.Client.DataServiceResponse> elemencie jest wyliczana i wyliczana jest również kolekcja obiektów zawartych w każdej <xref:System.Data.Services.Client.QueryOperationResponse%601> z nich.  
  
 [!code-csharp[Astoria Northwind Client#BatchQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#batchquery)]
 [!code-vb[Astoria Northwind Client#BatchQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#batchquery)]  
  
## <a name="see-also"></a>Zobacz także

- [Biblioteka klienta usług danych WCF](wcf-data-services-client-library.md)
