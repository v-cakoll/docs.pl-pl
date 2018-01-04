---
title: "Porady: połączenie z bazą danych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: c33d74b3-530d-421b-a121-96786dd263a5
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: d03dc5a3775ee9396573d58637c32f824760768f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-connect-to-a-database"></a>Porady: połączenie z bazą danych
<xref:System.Data.Linq.DataContext> Jest głównym połączenie za pomocą którego można nawiązać połączenia z bazą danych, pobrać obiekty i przesyłania zmian z powrotem na. Możesz użyć <xref:System.Data.Linq.DataContext> podobnie jak w przypadku [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] <xref:System.Data.SqlClient.SqlConnection>. W rzeczywistości <xref:System.Data.Linq.DataContext> jest inicjowany z połączenia lub parametry połączenia, które należy podać. Aby uzyskać więcej informacji, zobacz [metodę DataContext (Projektanta obiektów relacyjnych)](/visualstudio/data-tools/datacontext-methods-o-r-designer).  
  
 Celem <xref:System.Data.Linq.DataContext> jest sformułowanie żądań dla obiektów do zapytania SQL, które ma zostać wykonane w bazie danych, a następnie do łączenia obiektów poza wyniki. <xref:System.Data.Linq.DataContext> Umożliwia [!INCLUDE[vbteclinqext](../../../../../../includes/vbteclinqext-md.md)] zaimplementowanie tego samego wzorca operatora jako standardowych operatorów zapytań, takich jak `Where` i `Select`.  
  
> [!IMPORTANT]
>  Obsługa bezpiecznego połączenia jest najwyższej wagi. Aby uzyskać więcej informacji, zobacz [zabezpieczeń w składniku LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/security-in-linq-to-sql.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie <xref:System.Data.Linq.DataContext> służy do łączenia z przykładową bazą danych Northwind i pobierać wiersze klientów, których Miasto Londynie.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#1)]
 [!code-vb[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#1)]  
  
 Każda tabela bazy danych jest reprezentowany jako `Table` kolekcji dostępne poprzez <xref:System.Data.Linq.DataContext.GetTable%2A> — metoda, za pomocą klasy jednostki, aby zidentyfikować go.  
  
## <a name="example"></a>Przykład  
 Najlepszym rozwiązaniem jest, aby zadeklarować silnie typizowaną <xref:System.Data.Linq.DataContext> zamiast polegania na podstawowe <xref:System.Data.Linq.DataContext> klasy i <xref:System.Data.Linq.DataContext.GetTable%2A> metody. Silnie typizowaną <xref:System.Data.Linq.DataContext> deklaruje wszystkich `Table` kolekcje w postaci członkami kontekst, jak w poniższym przykładzie.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#2)]
 [!code-vb[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#2)]  
  
 Zapytania można następnie express dla klientów z Londynu po prostu jako:  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#5)]
 [!code-vb[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>Zobacz też  
 [Komunikacja z bazą danych](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)
