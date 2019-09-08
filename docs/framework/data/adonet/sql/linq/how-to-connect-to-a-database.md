---
title: 'Instrukcje: Łączenie z bazą danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c33d74b3-530d-421b-a121-96786dd263a5
ms.openlocfilehash: 48ff4af2c881104d5699910e20ef86eea0466d2a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793861"
---
# <a name="how-to-connect-to-a-database"></a>Instrukcje: Łączenie z bazą danych
<xref:System.Data.Linq.DataContext> Jest głównym kanałem, za pomocą którego nawiązujesz połączenie z bazą danych, pobierają z niej obiekty i przesyłamy zmiany z powrotem. Używasz tak samo jak w przypadku korzystania z ADO.NET <xref:System.Data.SqlClient.SqlConnection>. <xref:System.Data.Linq.DataContext> W rzeczywistości <xref:System.Data.Linq.DataContext> jest inicjowany z użyciem parametrów połączenia lub połączenia, które są dostarczane. Aby uzyskać więcej informacji, zobacz [metody DataContext (O/R Designer)](/visualstudio/data-tools/datacontext-methods-o-r-designer).  
  
 Celem <xref:System.Data.Linq.DataContext> jest przetłumaczenie żądań obiektów na zapytania SQL, które mają zostać wykonane względem bazy danych, a następnie do złożenia obiektów z wyników. Włącza przez implementację tego samego wzorca operatora jako standardowych operatorów zapytań, takich jak `Where` i `Select`. <xref:System.Data.Linq.DataContext> [!INCLUDE[vbteclinqext](../../../../../../includes/vbteclinqext-md.md)]  
  
> [!IMPORTANT]
> Utrzymywanie bezpiecznego połączenia ma najwyższy priorytet. Aby uzyskać więcej informacji, zobacz [zabezpieczenia w LINQ to SQL](security-in-linq-to-sql.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie <xref:System.Data.Linq.DataContext> jest używany do nawiązywania połączenia z przykładową bazą danych Northwind oraz do pobierania wierszy klientów, których miasto jest Londyn.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#1)]
 [!code-vb[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#1)]  
  
 Każda tabela bazy danych jest reprezentowana jako `Table` kolekcja dostępna w <xref:System.Data.Linq.DataContext.GetTable%2A> drodze metody, przy użyciu klasy Entity do jej identyfikacji.  
  
## <a name="example"></a>Przykład  
 Najlepszym rozwiązaniem jest zadeklarować silnie wpisaną <xref:System.Data.Linq.DataContext> zamiast polegania na klasie podstawowej <xref:System.Data.Linq.DataContext> i <xref:System.Data.Linq.DataContext.GetTable%2A> metodzie. Silnie wpisana <xref:System.Data.Linq.DataContext> liczba deklaruje wszystkie `Table` kolekcje jako elementy członkowskie kontekstu, jak w poniższym przykładzie.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#2)]
 [!code-vb[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#2)]  
  
 Następnie można wyrazić zapytanie dla klientów z Londynie w sposób bardziej prosty jako:  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#5)]
 [!code-vb[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>Zobacz także

- [Komunikacja z bazą danych](communicating-with-the-database.md)
