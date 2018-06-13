---
title: 'Porady: wykonywanie zapytań usługi danych (usługi danych WCF)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- querying the data service [WCF Data Services]
- WCF Data Services, querying
- WCF Data Services, accessing data
ms.assetid: 62997821-e0c6-4c4d-9fb7-1273fb5e5d18
ms.openlocfilehash: 574818c694b07775c4263dca066e0d2e462be27f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33363425"
---
# <a name="how-to-execute-data-service-queries-wcf-data-services"></a>Porady: wykonywanie zapytań usługi danych (usługi danych WCF)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Umożliwia to zapytanie usługi danych z aplikacji klienta opartego na programie .NET Framework za pomocą klasy usługi danych wygenerowanego klienta. Można wykonywać zapytania przy użyciu jednej z następujących metod:  
  
-   Wykonywanie zapytania LINQ przed nazwany <xref:System.Data.Services.Client.DataServiceQuery%601> uzyskanej od <xref:System.Data.Services.Client.DataServiceContext> który `Add Data Service Reference` narzędzie.  
  
-   Niejawnie, wyliczając przez nazwany <xref:System.Data.Services.Client.DataServiceQuery%601> uzyskanej od <xref:System.Data.Services.Client.DataServiceContext> który `Add Data Service Reference` narzędzie.  
  
-   Jawnie, wywołując <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> metoda <xref:System.Data.Services.Client.DataServiceQuery%601>, lub <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> metody dla operacji asynchronicznych.  
  
 Aby uzyskać więcej informacji, zobacz [zapytanie usługi danych](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
 Przykład, w tym temacie korzysta z Northwind przykładowych danych wygenerowany automatycznie i usługi klienta danych usługi klas. Ta usługa i klas danych klienta są tworzone po ukończeniu [szybkiego startu usługi danych WCF](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób definiowanie i wykonywanie zapytań LINQ, który zwraca wszystkie `Customers` z usługą danych Northwind.  
  
 [!code-csharp[Astoria Northwind Client#GetAllCustomersLinq](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#getallcustomerslinq)]
 [!code-vb[Astoria Northwind Client#GetAllCustomersLinq](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#getallcustomerslinq)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak używać kontekstu który `Add Data Service Reference` narzędzie generuje niejawnie wykonać zapytanie zwracające wszystkie `Customers` z usługą danych Northwind. Identyfikator URI żądanego `Customers` zestawu jednostek jest wyznaczany automatycznie na podstawie kontekstu. Kwerenda została wykonana niejawnie podczas wyliczania.  
  
 [!code-csharp[Astoria Northwind Client#GetAllCustomers](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#getallcustomers)]
 [!code-vb[Astoria Northwind Client#GetAllCustomers](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#getallcustomers)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie <xref:System.Data.Services.Client.DataServiceContext> jawnie wykonać zapytanie zwracające wszystkie `Customers` z usługą danych Northwind.  
  
 [!code-csharp[Astoria Northwind Client#GetAllCustomersExplicit](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#getallcustomersexplicit)]
 [!code-vb[Astoria Northwind Client#GetAllCustomersExplicit](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#getallcustomersexplicit)]  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Dodawanie opcji zapytania do zapytania usługi danych](../../../../docs/framework/data/wcf/how-to-add-query-options-to-a-data-service-query-wcf-data-services.md)
