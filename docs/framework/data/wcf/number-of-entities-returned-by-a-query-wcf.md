---
title: 'Instrukcje: Określ liczbę jednostek zwróconych przez zapytanie (Usługi danych programu WCF)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, row count
ms.assetid: 03d41a82-df95-40ac-8439-a6c327d37ba8
ms.openlocfilehash: 942fc6d6cbfb35d836ca5881958e7c9965a7d08b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70779840"
---
# <a name="how-to-determine-the-number-of-entities-returned-by-a-query-wcf-data-services"></a>Instrukcje: Określ liczbę jednostek zwróconych przez zapytanie (Usługi danych programu WCF)
Za [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]pomocą programu można określić liczbę jednostek, które znajdują się w zestawie jednostek określonym przez identyfikator URI zapytania. Tę liczbę można uwzględnić razem z wynikiem zapytania lub jako wartość całkowitą. Aby uzyskać więcej informacji, zobacz [wykonywanie zapytań dotyczących usługi danych](querying-the-data-service-wcf-data-services.md).  
  
 W przykładzie w tym temacie jest stosowana usługa danych przykładowych Northwind i klasy usługi danych klientów. Ta usługa i klasy danych klienta są tworzone po zakończeniu [usługi danych programu WCF szybkiego startu](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Przykład  
 Ten przykład wykonuje zapytanie po wywołaniu <xref:System.Data.Services.Client.DataServiceQuery%601.IncludeTotalCount%2A> metody. Właściwość zwraca liczbę jednostek `Customers` w zestawie jednostek. <xref:System.Data.Services.Client.QueryOperationResponse%601.TotalCount%2A>  
  
 [!code-csharp[Astoria Northwind Client#CountAllCustomers](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#countallcustomers)]
 [!code-vb[Astoria Northwind Client#CountAllCustomers](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#countallcustomers)]  
  
## <a name="example"></a>Przykład  
 Ten przykład wywołuje <xref:System.Linq.Enumerable.Count%2A> metodę zwracającą tylko liczbę całkowitą, która jest liczbą jednostek `Customers` w zestawie jednostek.  
  
 [!code-csharp[Astoria Northwind Client#CountAllCustomersValueOnly](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#countallcustomersvalueonly)]
 [!code-vb[Astoria Northwind Client#CountAllCustomersValueOnly](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#countallcustomersvalueonly)]  
  
## <a name="see-also"></a>Zobacz także

- [Wykonywanie zapytań do usługi danych](querying-the-data-service-wcf-data-services.md)
