---
title: 'Instrukcje: ładowanie powiązanych jednostek (Usługi danych programu WCF)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, deferred content
- WCF Data Services, loading data
ms.assetid: 6f143d30-d997-4e6b-bcf0-d5c394ecb108
ms.openlocfilehash: 84c2448f317e813a95688feaaac1c97436de1b16
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569014"
---
# <a name="how-to-load-related-entities-wcf-data-services"></a>Instrukcje: ładowanie powiązanych jednostek (Usługi danych programu WCF)
Gdy zachodzi potrzeba załadowania skojarzonych jednostek w Usługi danych programu WCF, można użyć metody <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> na klasie <xref:System.Data.Services.Client.DataServiceContext>. Można również użyć metody <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> na <xref:System.Data.Services.Client.DataServiceQuery%601>, aby wymagać eagerly powiązanych jednostek w tej samej odpowiedzi na zapytanie.  
  
 W przykładzie w tym temacie jest stosowana usługa danych przykładowych Northwind i klasy usługi danych klientów. Ta usługa i klasy danych klienta są tworzone po zakończeniu [usługi danych programu WCF szybkiego startu](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak jawnie załadować `Customer`, która jest powiązana z każdym zwróconym wystąpieniem `Orders`.  
  
 [!code-csharp[Astoria Northwind Client#LoadRelatedOrderCustomer](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#loadrelatedordercustomer)]
 [!code-vb[Astoria Northwind Client#LoadRelatedOrderCustomer](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#loadrelatedordercustomer)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak używać metody <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A>, aby zwrócić `Order Details`, które należą do `Orders` zwróconego przez zapytanie.  
  
 [!code-csharp[Astoria Northwind Client#ExpandOrderDetails](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#expandorderdetails)]
 [!code-vb[Astoria Northwind Client#ExpandOrderDetails](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#expandorderdetails)]  
  
## <a name="see-also"></a>Zobacz także

- [Wykonywanie zapytań do usługi danych](querying-the-data-service-wcf-data-services.md)
