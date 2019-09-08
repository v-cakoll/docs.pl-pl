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
# <a name="how-to-connect-to-a-database"></a><span data-ttu-id="2a5ca-102">Instrukcje: Łączenie z bazą danych</span><span class="sxs-lookup"><span data-stu-id="2a5ca-102">How to: Connect to a Database</span></span>
<span data-ttu-id="2a5ca-103"><xref:System.Data.Linq.DataContext> Jest głównym kanałem, za pomocą którego nawiązujesz połączenie z bazą danych, pobierają z niej obiekty i przesyłamy zmiany z powrotem.</span><span class="sxs-lookup"><span data-stu-id="2a5ca-103">The <xref:System.Data.Linq.DataContext> is the main conduit by which you connect to a database, retrieve objects from it, and submit changes back to it.</span></span> <span data-ttu-id="2a5ca-104">Używasz tak samo jak w przypadku korzystania z ADO.NET <xref:System.Data.SqlClient.SqlConnection>. <xref:System.Data.Linq.DataContext></span><span class="sxs-lookup"><span data-stu-id="2a5ca-104">You use the <xref:System.Data.Linq.DataContext> just as you would use an ADO.NET <xref:System.Data.SqlClient.SqlConnection>.</span></span> <span data-ttu-id="2a5ca-105">W rzeczywistości <xref:System.Data.Linq.DataContext> jest inicjowany z użyciem parametrów połączenia lub połączenia, które są dostarczane.</span><span class="sxs-lookup"><span data-stu-id="2a5ca-105">In fact, the <xref:System.Data.Linq.DataContext> is initialized with a connection or connection string that you supply.</span></span> <span data-ttu-id="2a5ca-106">Aby uzyskać więcej informacji, zobacz [metody DataContext (O/R Designer)](/visualstudio/data-tools/datacontext-methods-o-r-designer).</span><span class="sxs-lookup"><span data-stu-id="2a5ca-106">For more information, see [DataContext Methods (O/R Designer)](/visualstudio/data-tools/datacontext-methods-o-r-designer).</span></span>  
  
 <span data-ttu-id="2a5ca-107">Celem <xref:System.Data.Linq.DataContext> jest przetłumaczenie żądań obiektów na zapytania SQL, które mają zostać wykonane względem bazy danych, a następnie do złożenia obiektów z wyników.</span><span class="sxs-lookup"><span data-stu-id="2a5ca-107">The purpose of the <xref:System.Data.Linq.DataContext> is to translate your requests for objects into SQL queries to be made against the database, and then to assemble objects out of the results.</span></span> <span data-ttu-id="2a5ca-108">Włącza przez implementację tego samego wzorca operatora jako standardowych operatorów zapytań, takich jak `Where` i `Select`. <xref:System.Data.Linq.DataContext> [!INCLUDE[vbteclinqext](../../../../../../includes/vbteclinqext-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a5ca-108">The <xref:System.Data.Linq.DataContext> enables [!INCLUDE[vbteclinqext](../../../../../../includes/vbteclinqext-md.md)] by implementing the same operator pattern as the Standard Query Operators, such as `Where` and `Select`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="2a5ca-109">Utrzymywanie bezpiecznego połączenia ma najwyższy priorytet.</span><span class="sxs-lookup"><span data-stu-id="2a5ca-109">Maintaining a secure connection is of the highest importance.</span></span> <span data-ttu-id="2a5ca-110">Aby uzyskać więcej informacji, zobacz [zabezpieczenia w LINQ to SQL](security-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="2a5ca-110">For more information, see [Security in LINQ to SQL](security-in-linq-to-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a5ca-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="2a5ca-111">Example</span></span>  
 <span data-ttu-id="2a5ca-112">W poniższym przykładzie <xref:System.Data.Linq.DataContext> jest używany do nawiązywania połączenia z przykładową bazą danych Northwind oraz do pobierania wierszy klientów, których miasto jest Londyn.</span><span class="sxs-lookup"><span data-stu-id="2a5ca-112">In the following example, the <xref:System.Data.Linq.DataContext> is used to connect to the Northwind sample database and to retrieve rows of customers whose city is London.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#1)]
 [!code-vb[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#1)]  
  
 <span data-ttu-id="2a5ca-113">Każda tabela bazy danych jest reprezentowana jako `Table` kolekcja dostępna w <xref:System.Data.Linq.DataContext.GetTable%2A> drodze metody, przy użyciu klasy Entity do jej identyfikacji.</span><span class="sxs-lookup"><span data-stu-id="2a5ca-113">Each database table is represented as a `Table` collection available by way of the <xref:System.Data.Linq.DataContext.GetTable%2A> method, by using the entity class to identify it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a5ca-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="2a5ca-114">Example</span></span>  
 <span data-ttu-id="2a5ca-115">Najlepszym rozwiązaniem jest zadeklarować silnie wpisaną <xref:System.Data.Linq.DataContext> zamiast polegania na klasie podstawowej <xref:System.Data.Linq.DataContext> i <xref:System.Data.Linq.DataContext.GetTable%2A> metodzie.</span><span class="sxs-lookup"><span data-stu-id="2a5ca-115">Best practice is to declare a strongly typed <xref:System.Data.Linq.DataContext> instead of relying on the basic <xref:System.Data.Linq.DataContext> class and the <xref:System.Data.Linq.DataContext.GetTable%2A> method.</span></span> <span data-ttu-id="2a5ca-116">Silnie wpisana <xref:System.Data.Linq.DataContext> liczba deklaruje wszystkie `Table` kolekcje jako elementy członkowskie kontekstu, jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="2a5ca-116">A strongly typed <xref:System.Data.Linq.DataContext> declares all `Table` collections as members of the context, as in the following example.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#2)]
 [!code-vb[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#2)]  
  
 <span data-ttu-id="2a5ca-117">Następnie można wyrazić zapytanie dla klientów z Londynie w sposób bardziej prosty jako:</span><span class="sxs-lookup"><span data-stu-id="2a5ca-117">You can then express the query for customers from London more simply as:</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#5)]
 [!code-vb[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="2a5ca-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2a5ca-118">See also</span></span>

- [<span data-ttu-id="2a5ca-119">Komunikacja z bazą danych</span><span class="sxs-lookup"><span data-stu-id="2a5ca-119">Communicating with the Database</span></span>](communicating-with-the-database.md)
