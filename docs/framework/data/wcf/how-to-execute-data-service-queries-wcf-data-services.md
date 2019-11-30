---
title: 'Instrukcje: wykonywanie zapytań dotyczących usługi danych (Usługi danych programu WCF)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- querying the data service [WCF Data Services]
- WCF Data Services, querying
- WCF Data Services, accessing data
ms.assetid: 62997821-e0c6-4c4d-9fb7-1273fb5e5d18
ms.openlocfilehash: b06a21a45dcf6e67c41287c4cd59cdda4aa7b447
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569080"
---
# <a name="how-to-execute-data-service-queries-wcf-data-services"></a>Instrukcje: wykonywanie zapytań dotyczących usługi danych (Usługi danych programu WCF)
Usługi danych programu WCF umożliwia wysyłanie zapytań do usługi danych z aplikacji klienckiej opartej na .NET Framework przy użyciu wygenerowanych klas usługi danych klienta. Zapytania można wykonywać za pomocą jednej z następujących metod:  
  
- Wykonywanie zapytania LINQ względem nazwanego <xref:System.Data.Services.Client.DataServiceQuery%601> uzyskanego od <xref:System.Data.Services.Client.DataServiceContext> wygenerowanego przez narzędzie `Add Data Service Reference`.  
  
- Niejawnie, przez Wyliczenie o nazwie <xref:System.Data.Services.Client.DataServiceQuery%601> uzyskanej od <xref:System.Data.Services.Client.DataServiceContext> wygenerowanego przez narzędzie `Add Data Service Reference`.  
  
- Jawnie, wywołując metodę <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> na <xref:System.Data.Services.Client.DataServiceQuery%601>lub metodę <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> na potrzeby wykonywania asynchronicznego.  
  
 Aby uzyskać więcej informacji, zobacz [wykonywanie zapytań dotyczących usługi danych](querying-the-data-service-wcf-data-services.md).  
  
 W przykładzie w tym temacie jest stosowana usługa danych przykładowych Northwind i klasy usługi danych klientów. Ta usługa i klasy danych klienta są tworzone po zakończeniu [usługi danych programu WCF szybkiego startu](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak zdefiniować i wykonać zapytanie LINQ zwracające wszystkie `Customers` do usługi danych Northwind.  
  
 [!code-csharp[Astoria Northwind Client#GetAllCustomersLinq](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getallcustomerslinq)]
 [!code-vb[Astoria Northwind Client#GetAllCustomersLinq](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getallcustomerslinq)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak użyć kontekstu, który generuje narzędzie `Add Data Service Reference`, aby niejawnie wykonać zapytanie zwracające wszystkie `Customers` do usługi danych Northwind. Identyfikator URI żądanego zestawu jednostek `Customers` jest określany automatycznie przez kontekst. Zapytanie jest wykonywane niejawnie, gdy występuje wyliczenie.  
  
 [!code-csharp[Astoria Northwind Client#GetAllCustomers](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getallcustomers)]
 [!code-vb[Astoria Northwind Client#GetAllCustomers](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getallcustomers)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak za pomocą <xref:System.Data.Services.Client.DataServiceContext> jawnie wykonać zapytanie zwracające wszystkie `Customers` do usługi danych Northwind.  
  
 [!code-csharp[Astoria Northwind Client#GetAllCustomersExplicit](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getallcustomersexplicit)]
 [!code-vb[Astoria Northwind Client#GetAllCustomersExplicit](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getallcustomersexplicit)]  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Dodawanie opcji zapytania do zapytania usługi danych](how-to-add-query-options-to-a-data-service-query-wcf-data-services.md)
