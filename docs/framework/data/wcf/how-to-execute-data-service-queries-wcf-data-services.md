---
title: 'Instrukcje: Wykonywanie zapytań usługi danych (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- querying the data service [WCF Data Services]
- WCF Data Services, querying
- WCF Data Services, accessing data
ms.assetid: 62997821-e0c6-4c4d-9fb7-1273fb5e5d18
ms.openlocfilehash: c8df3d57e5a6ff1f0021381db189025719808641
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59517450"
---
# <a name="how-to-execute-data-service-queries-wcf-data-services"></a>Instrukcje: Wykonywanie zapytań usługi danych (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Umożliwia wykonywanie zapytań usługi danych z aplikacji klienta opartego na programie .NET Framework przy użyciu klas usługi danych wygenerowanego klienta. Zapytania można wykonywać przy użyciu jednej z następujących metod:  
  
-   Wykonywanie zapytania LINQ względem nazwany <xref:System.Data.Services.Client.DataServiceQuery%601> uzyskany z <xref:System.Data.Services.Client.DataServiceContext> , `Add Data Service Reference` narzędzie generuje.  
  
-   Niejawnie, wyliczając przez nazwany <xref:System.Data.Services.Client.DataServiceQuery%601> uzyskany z <xref:System.Data.Services.Client.DataServiceContext> , `Add Data Service Reference` narzędzie generuje.  
  
-   Jawnie, przez wywołanie metody <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> metody <xref:System.Data.Services.Client.DataServiceQuery%601>, lub <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> metodę dla operacji asynchronicznych.  
  
 Aby uzyskać więcej informacji, zobacz [zapytań usługi danych](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
 W przykładzie w tym temacie użyto Northwind przykładowe dane usługi i automatycznie wygenerowany klas usługi danych klienta. Ta usługa i klas danych klienta, są tworzone po ukończeniu [Szybki Start usług danych WCF](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje jak zdefiniować i wykonać zapytanie LINQ, które zwraca wszystkie `Customers` korzystająca z usługi danych Northwind.  
  
 [!code-csharp[Astoria Northwind Client#GetAllCustomersLinq](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getallcustomerslinq)]
 [!code-vb[Astoria Northwind Client#GetAllCustomersLinq](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getallcustomerslinq)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak używać kontekstu, `Add Data Service Reference` narzędzie generuje niejawnie wykonanie zapytania zwracającego wszystkie `Customers` korzystająca z usługi danych Northwind. Identyfikator URI żądanego `Customers` zestaw jednostek jest wyznaczany automatycznie na podstawie kontekstu. Zapytanie jest wykonywane niejawnie, gdy wystąpi wyliczenia.  
  
 [!code-csharp[Astoria Northwind Client#GetAllCustomers](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getallcustomers)]
 [!code-vb[Astoria Northwind Client#GetAllCustomers](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getallcustomers)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak używać <xref:System.Data.Services.Client.DataServiceContext> jawnie wykonanie zapytania zwracającego wszystkie `Customers` korzystająca z usługi danych Northwind.  
  
 [!code-csharp[Astoria Northwind Client#GetAllCustomersExplicit](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getallcustomersexplicit)]
 [!code-vb[Astoria Northwind Client#GetAllCustomersExplicit](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getallcustomersexplicit)]  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Dodawanie opcji zapytania do zapytania usługi danych](../../../../docs/framework/data/wcf/how-to-add-query-options-to-a-data-service-query-wcf-data-services.md)
