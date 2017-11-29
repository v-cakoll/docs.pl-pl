---
title: "Porady: wykonywanie zapytań w partii (usługi danych WCF)"
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
helpviewer_keywords: WCF Data Services, batch requests
ms.assetid: 3b4db7df-bd33-43a1-8ea4-63a18e131f97
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d868881a3ff5c79f1f003881f58c726ebf25385e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-execute-queries-in-a-batch-wcf-data-services"></a>Porady: wykonywanie zapytań w partii (usługi danych WCF)
Za pomocą [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] biblioteki klienta, można wykonać zapytania więcej niż jeden z usługą danych w pojedynczej partii. Aby uzyskać więcej informacji, zobacz [przetwarzanie wsadowe operacji](../../../../docs/framework/data/wcf/batching-operations-wcf-data-services.md).  
  
 Przykład, w tym temacie korzysta z Northwind przykładowych danych wygenerowany automatycznie i usługi klienta danych usługi klas. Ta usługa i klas danych klienta są tworzone po ukończeniu [szybkiego startu usługi danych WCF](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób wywołania <xref:System.Data.Services.Client.DataServiceContext.ExecuteBatch%2A> metoda używana tablica <xref:System.Data.Services.Client.DataServiceRequest%601> obiektów, które zawiera zapytań zwracających zarówno `Customers` i `Products` obiektów z usług danych Northwind. Kolekcja <xref:System.Data.Services.Client.QueryOperationResponse%601> obiektów w zwróconym <xref:System.Data.Services.Client.DataServiceResponse> wyliczeniu i kolekcję obiektów zawartą w każdym <xref:System.Data.Services.Client.QueryOperationResponse%601> również wyliczeniu.  
  
 [!code-csharp[Astoria Northwind Client#BatchQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#batchquery)]
 [!code-vb[Astoria Northwind Client#BatchQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#batchquery)]  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteka klienta usługi danych WCF](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
