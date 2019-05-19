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
# <a name="how-to-connect-to-a-database"></a><span data-ttu-id="2bc98-102">Instrukcje: Łączenie z bazą danych</span><span class="sxs-lookup"><span data-stu-id="2bc98-102">How to: Connect to a Database</span></span>
<span data-ttu-id="2bc98-103"><xref:System.Data.Linq.DataContext> Jest głównym kanał za pomocą którego możesz nawiązać połączenie z bazą danych, pobieranie obiektów z niej i przesyłanie zmian do niej powrót po.</span><span class="sxs-lookup"><span data-stu-id="2bc98-103">The <xref:System.Data.Linq.DataContext> is the main conduit by which you connect to a database, retrieve objects from it, and submit changes back to it.</span></span> <span data-ttu-id="2bc98-104">Możesz użyć <xref:System.Data.Linq.DataContext> podobnie jak w przypadku ADO.NET <xref:System.Data.SqlClient.SqlConnection>.</span><span class="sxs-lookup"><span data-stu-id="2bc98-104">You use the <xref:System.Data.Linq.DataContext> just as you would use an ADO.NET <xref:System.Data.SqlClient.SqlConnection>.</span></span> <span data-ttu-id="2bc98-105">W rzeczywistości <xref:System.Data.Linq.DataContext> jest inicjowany za pomocą połączenia lub parametry połączenia, które dostarczasz.</span><span class="sxs-lookup"><span data-stu-id="2bc98-105">In fact, the <xref:System.Data.Linq.DataContext> is initialized with a connection or connection string that you supply.</span></span> <span data-ttu-id="2bc98-106">Aby uzyskać więcej informacji, zobacz [metody DataContext (O/R Designer)](/visualstudio/data-tools/datacontext-methods-o-r-designer).</span><span class="sxs-lookup"><span data-stu-id="2bc98-106">For more information, see [DataContext Methods (O/R Designer)](/visualstudio/data-tools/datacontext-methods-o-r-designer).</span></span>  
  
 <span data-ttu-id="2bc98-107">Celem <xref:System.Data.Linq.DataContext> jest do tłumaczenia żądań dla obiektów na zapytania SQL, które ma zostać wykonane w bazie danych, a następnie można złożyć obiektów poza wyniki.</span><span class="sxs-lookup"><span data-stu-id="2bc98-107">The purpose of the <xref:System.Data.Linq.DataContext> is to translate your requests for objects into SQL queries to be made against the database, and then to assemble objects out of the results.</span></span> <span data-ttu-id="2bc98-108"><xref:System.Data.Linq.DataContext> Umożliwia [!INCLUDE[vbteclinqext](../../../../../../includes/vbteclinqext-md.md)] poprzez implementację tego samego wzorca operatora jako standardowych operatorów zapytań, takich jak `Where` i `Select`.</span><span class="sxs-lookup"><span data-stu-id="2bc98-108">The <xref:System.Data.Linq.DataContext> enables [!INCLUDE[vbteclinqext](../../../../../../includes/vbteclinqext-md.md)] by implementing the same operator pattern as the Standard Query Operators, such as `Where` and `Select`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2bc98-109">Obsługa bezpiecznego połączenia jest najwyższej wagi.</span><span class="sxs-lookup"><span data-stu-id="2bc98-109">Maintaining a secure connection is of the highest importance.</span></span> <span data-ttu-id="2bc98-110">Aby uzyskać więcej informacji, zobacz [zabezpieczeń w składniku LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/security-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="2bc98-110">For more information, see [Security in LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/security-in-linq-to-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2bc98-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="2bc98-111">Example</span></span>  
 <span data-ttu-id="2bc98-112">W poniższym przykładzie <xref:System.Data.Linq.DataContext> służy do łączenia z przykładową bazą danych Northwind i pobierać wiersze klientów, których Miasto jest London.</span><span class="sxs-lookup"><span data-stu-id="2bc98-112">In the following example, the <xref:System.Data.Linq.DataContext> is used to connect to the Northwind sample database and to retrieve rows of customers whose city is London.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#1)]
 [!code-vb[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#1)]  
  
 <span data-ttu-id="2bc98-113">Każda tabela bazy danych jest przedstawiana jako `Table` kolekcję dostępnych za <xref:System.Data.Linq.DataContext.GetTable%2A> metody, za pomocą klasy jednostki, aby je zidentyfikować.</span><span class="sxs-lookup"><span data-stu-id="2bc98-113">Each database table is represented as a `Table` collection available by way of the <xref:System.Data.Linq.DataContext.GetTable%2A> method, by using the entity class to identify it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2bc98-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="2bc98-114">Example</span></span>  
 <span data-ttu-id="2bc98-115">Najlepszym rozwiązaniem jest do zadeklarowania silnie typizowaną <xref:System.Data.Linq.DataContext> zamiast polegania na podstawowa <xref:System.Data.Linq.DataContext> klasy i <xref:System.Data.Linq.DataContext.GetTable%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="2bc98-115">Best practice is to declare a strongly typed <xref:System.Data.Linq.DataContext> instead of relying on the basic <xref:System.Data.Linq.DataContext> class and the <xref:System.Data.Linq.DataContext.GetTable%2A> method.</span></span> <span data-ttu-id="2bc98-116">Silnie typizowane <xref:System.Data.Linq.DataContext> deklaruje wszystkie `Table` kolekcji jako elementy członkowskie kontekstu, jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="2bc98-116">A strongly typed <xref:System.Data.Linq.DataContext> declares all `Table` collections as members of the context, as in the following example.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#2)]
 [!code-vb[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#2)]  
  
 <span data-ttu-id="2bc98-117">Następnie można wyrazić zapytania dla klientów z Londynu po prostu jako:</span><span class="sxs-lookup"><span data-stu-id="2bc98-117">You can then express the query for customers from London more simply as:</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#5)]
 [!code-vb[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="2bc98-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2bc98-118">See also</span></span>

- [<span data-ttu-id="2bc98-119">Komunikacja z bazą danych</span><span class="sxs-lookup"><span data-stu-id="2bc98-119">Communicating with the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)
