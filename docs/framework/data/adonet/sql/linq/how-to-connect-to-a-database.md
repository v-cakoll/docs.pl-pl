---
title: 'Instrukcje: łączenie z bazą danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c33d74b3-530d-421b-a121-96786dd263a5
ms.openlocfilehash: 837919b1cfcdf46026ccfb37cbbec951c0ae41b8
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634680"
---
# <a name="how-to-connect-to-a-database"></a>Instrukcje: łączenie z bazą danych
<xref:System.Data.Linq.DataContext> jest głównym przewodem, za pomocą którego nawiązujesz połączenie z bazą danych, pobierasz z niej obiekty i przesyłaj do niej zmiany. Używasz <xref:System.Data.Linq.DataContext> tak samo jak w przypadku użycia <xref:System.Data.SqlClient.SqlConnection>ADO.NET. W rzeczywistości <xref:System.Data.Linq.DataContext> jest inicjowana za pomocą połączenia lub parametrów połączenia, które są dostarczane. Aby uzyskać więcej informacji, zobacz [metody DataContext (O/R Designer)](/visualstudio/data-tools/datacontext-methods-o-r-designer).  
  
 Celem <xref:System.Data.Linq.DataContext> jest przetłumaczenie żądań dotyczących obiektów na zapytania SQL, które mają zostać wykonane względem bazy danych, a następnie do złożenia obiektów z wyników. <xref:System.Data.Linq.DataContext> umożliwia zaimplementowanie przy użyciu języka CLR (Language-Integrated Query) przez implementację tego samego wzorca operatora jako standardowych operatorów zapytań, takich jak `Where` i `Select`.  
  
> [!IMPORTANT]
> Utrzymywanie bezpiecznego połączenia ma najwyższy priorytet. Aby uzyskać więcej informacji, zobacz [zabezpieczenia w LINQ to SQL](security-in-linq-to-sql.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie <xref:System.Data.Linq.DataContext> jest używany do nawiązywania połączenia z przykładową bazą danych Northwind oraz do pobierania wierszy klientów, których miasto jest Londyn.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#1)]
 [!code-vb[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#1)]  
  
 Każda tabela bazy danych jest reprezentowana jako kolekcja `Table` dostępna za pomocą metody <xref:System.Data.Linq.DataContext.GetTable%2A> przy użyciu klasy Entity do jej identyfikacji.  
  
## <a name="example"></a>Przykład  
 Najlepszym rozwiązaniem jest zadeklarować silnie wpisaną <xref:System.Data.Linq.DataContext> zamiast polegać na podstawowej klasie <xref:System.Data.Linq.DataContext> i metodzie <xref:System.Data.Linq.DataContext.GetTable%2A>. <xref:System.Data.Linq.DataContext> o jednoznacznie określonym typie deklaruje wszystkie kolekcje `Table` jako elementy członkowskie kontekstu, jak w poniższym przykładzie.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#2)]
 [!code-vb[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#2)]  
  
 Następnie można wyrazić zapytanie dla klientów z Londynie w sposób bardziej prosty jako:  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#5)]
 [!code-vb[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>Zobacz także

- [Komunikacja z bazą danych](communicating-with-the-database.md)
