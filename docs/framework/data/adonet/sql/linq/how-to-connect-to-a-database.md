---
title: 'Instrukcje: Łączenie z bazą danych'
description: Dowiedz się, jak używać elementu DataContext do łączenia się z bazą danych w LINQ to SQL. Zapoznaj się z tymi przykładami, aby użyć DataContext do nawiązania połączenia z bazą danych i pobrania wierszy.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c33d74b3-530d-421b-a121-96786dd263a5
ms.openlocfilehash: c3320a598cb8407ab584530c615c2e5ef0de53c8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286407"
---
# <a name="how-to-connect-to-a-database"></a>Instrukcje: Łączenie z bazą danych
<xref:System.Data.Linq.DataContext>Jest głównym kanałem, za pomocą którego nawiązujesz połączenie z bazą danych, pobierają z niej obiekty i przesyłamy zmiany z powrotem. Używasz <xref:System.Data.Linq.DataContext> tak samo jak w przypadku korzystania z ADO.NET <xref:System.Data.SqlClient.SqlConnection> . W rzeczywistości <xref:System.Data.Linq.DataContext> jest inicjowany z użyciem parametrów połączenia lub połączenia, które są dostarczane. Aby uzyskać więcej informacji, zobacz [metody DataContext (Projektant O/R)](/visualstudio/data-tools/datacontext-methods-o-r-designer).  
  
 Celem <xref:System.Data.Linq.DataContext> jest przetłumaczenie żądań obiektów na zapytania SQL, które mają zostać wykonane względem bazy danych, a następnie do złożenia obiektów z wyników. <xref:System.Data.Linq.DataContext>Włącza obsługę języka (LINQ) przez zaimplementowanie tego samego wzorca operatora jako standardowych operatorów zapytań, takich jak `Where` i `Select` .  
  
> [!IMPORTANT]
> Utrzymywanie bezpiecznego połączenia ma najwyższy priorytet. Aby uzyskać więcej informacji, zobacz [zabezpieczenia w LINQ to SQL](security-in-linq-to-sql.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie <xref:System.Data.Linq.DataContext> jest używany do nawiązywania połączenia z przykładową bazą danych Northwind oraz do pobierania wierszy klientów, których miasto jest Londyn.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#1)]
 [!code-vb[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#1)]  
  
 Każda tabela bazy danych jest reprezentowana jako `Table` Kolekcja dostępna w drodze <xref:System.Data.Linq.DataContext.GetTable%2A> metody, przy użyciu klasy Entity do jej identyfikacji.  
  
## <a name="example"></a>Przykład  
 Najlepszym rozwiązaniem jest zadeklarować silnie wpisaną <xref:System.Data.Linq.DataContext> zamiast polegania na <xref:System.Data.Linq.DataContext> klasie podstawowej i <xref:System.Data.Linq.DataContext.GetTable%2A> metodzie. Silnie wpisana <xref:System.Data.Linq.DataContext> Liczba deklaruje wszystkie `Table` kolekcje jako elementy członkowskie kontekstu, jak w poniższym przykładzie.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#2)]
 [!code-vb[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#2)]  
  
 Następnie można wyrazić zapytanie dla klientów z Londynie w sposób bardziej prosty jako:  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#5)]
 [!code-vb[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>Zobacz także

- [Komunikacja z bazą danych](communicating-with-the-database.md)
