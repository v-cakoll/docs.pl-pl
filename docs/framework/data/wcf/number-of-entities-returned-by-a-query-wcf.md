---
title: 'Porady: określić liczbę jednostek zwróconych przez zapytanie (usługi danych WCF)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, row count
ms.assetid: 03d41a82-df95-40ac-8439-a6c327d37ba8
ms.openlocfilehash: 183fed2d267fc16767c902cdd69513aa9986ff78
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365002"
---
# <a name="how-to-determine-the-number-of-entities-returned-by-a-query-wcf-data-services"></a>Porady: określić liczbę jednostek zwróconych przez zapytanie (usługi danych WCF)
Z [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], można określić liczbę jednostek, które są w jednostce określony przez identyfikator URI zapytania zestaw. Ta liczba może być uwzględnione wraz z wyniku zapytania lub jako wartość całkowitą. Aby uzyskać więcej informacji, zobacz [zapytanie usługi danych](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
 Przykład, w tym temacie korzysta z Northwind przykładowych danych wygenerowany automatycznie i usługi klienta danych usługi klas. Ta usługa i klas danych klienta są tworzone po ukończeniu [szybkiego startu usługi danych WCF](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Przykład  
 W tym przykładzie wykonuje zapytanie po wywołaniu <xref:System.Data.Services.Client.DataServiceQuery%601.IncludeTotalCount%2A> metody. <xref:System.Data.Services.Client.QueryOperationResponse%601.TotalCount%2A> Właściwość zwraca liczbę jednostek w `Customers` zestawu jednostek.  
  
 [!code-csharp[Astoria Northwind Client#CountAllCustomers](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#countallcustomers)]
 [!code-vb[Astoria Northwind Client#CountAllCustomers](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#countallcustomers)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie wywołuje <xref:System.Linq.Enumerable.Count%2A> metoda zwraca tylko liczbę całkowitą czyli wartość liczby jednostek w `Customers` zestawu jednostek.  
  
 [!code-csharp[Astoria Northwind Client#CountAllCustomersValueOnly](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#countallcustomersvalueonly)]
 [!code-vb[Astoria Northwind Client#CountAllCustomersValueOnly](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#countallcustomersvalueonly)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wykonywanie zapytań do usługi danych](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)
