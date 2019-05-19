---
title: 'Instrukcje: Łączenie z bazą danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c33d74b3-530d-421b-a121-96786dd263a5
ms.openlocfilehash: d38965288884bb72e102d6ec09deca57296c9b0f
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2019
ms.locfileid: "65882019"
---
# <a name="how-to-connect-to-a-database"></a>Instrukcje: Łączenie z bazą danych
<xref:System.Data.Linq.DataContext> Jest głównym kanał za pomocą którego możesz nawiązać połączenie z bazą danych, pobieranie obiektów z niej i przesyłanie zmian do niej powrót po. Możesz użyć <xref:System.Data.Linq.DataContext> podobnie jak w przypadku ADO.NET <xref:System.Data.SqlClient.SqlConnection>. W rzeczywistości <xref:System.Data.Linq.DataContext> jest inicjowany za pomocą połączenia lub parametry połączenia, które dostarczasz. Aby uzyskać więcej informacji, zobacz [metody DataContext (O/R Designer)](/visualstudio/data-tools/datacontext-methods-o-r-designer).  
  
 Celem <xref:System.Data.Linq.DataContext> jest do tłumaczenia żądań dla obiektów na zapytania SQL, które ma zostać wykonane w bazie danych, a następnie można złożyć obiektów poza wyniki. <xref:System.Data.Linq.DataContext> Umożliwia [!INCLUDE[vbteclinqext](../../../../../../includes/vbteclinqext-md.md)] poprzez implementację tego samego wzorca operatora jako standardowych operatorów zapytań, takich jak `Where` i `Select`.  
  
> [!IMPORTANT]
>  Obsługa bezpiecznego połączenia jest najwyższej wagi. Aby uzyskać więcej informacji, zobacz [zabezpieczeń w składniku LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/security-in-linq-to-sql.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie <xref:System.Data.Linq.DataContext> służy do łączenia z przykładową bazą danych Northwind i pobierać wiersze klientów, których Miasto jest London.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#1)]
 [!code-vb[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#1)]  
  
 Każda tabela bazy danych jest przedstawiana jako `Table` kolekcję dostępnych za <xref:System.Data.Linq.DataContext.GetTable%2A> metody, za pomocą klasy jednostki, aby je zidentyfikować.  
  
## <a name="example"></a>Przykład  
 Najlepszym rozwiązaniem jest do zadeklarowania silnie typizowaną <xref:System.Data.Linq.DataContext> zamiast polegania na podstawowa <xref:System.Data.Linq.DataContext> klasy i <xref:System.Data.Linq.DataContext.GetTable%2A> metody. Silnie typizowane <xref:System.Data.Linq.DataContext> deklaruje wszystkie `Table` kolekcji jako elementy członkowskie kontekstu, jak w poniższym przykładzie.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#2)]
 [!code-vb[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#2)]  
  
 Następnie można wyrazić zapytania dla klientów z Londynu po prostu jako:  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#5)]
 [!code-vb[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>Zobacz także

- [Komunikacja z bazą danych](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)
