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
ms.openlocfilehash: f302e3f24b844bf0357b00bcd97ab074ac972bff
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-connect-to-a-database"></a><span data-ttu-id="764d9-102">Porady: połączenie z bazą danych</span><span class="sxs-lookup"><span data-stu-id="764d9-102">How to: Connect to a Database</span></span>
<span data-ttu-id="764d9-103"><xref:System.Data.Linq.DataContext> Jest głównym połączenie za pomocą którego można nawiązać połączenia z bazą danych, pobrać obiekty i przesyłania zmian z powrotem na.</span><span class="sxs-lookup"><span data-stu-id="764d9-103">The <xref:System.Data.Linq.DataContext> is the main conduit by which you connect to a database, retrieve objects from it, and submit changes back to it.</span></span> <span data-ttu-id="764d9-104">Możesz użyć <xref:System.Data.Linq.DataContext> podobnie jak w przypadku [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] <xref:System.Data.SqlClient.SqlConnection>.</span><span class="sxs-lookup"><span data-stu-id="764d9-104">You use the <xref:System.Data.Linq.DataContext> just as you would use an [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] <xref:System.Data.SqlClient.SqlConnection>.</span></span> <span data-ttu-id="764d9-105">W rzeczywistości <xref:System.Data.Linq.DataContext> jest inicjowany z połączenia lub parametry połączenia, które należy podać.</span><span class="sxs-lookup"><span data-stu-id="764d9-105">In fact, the <xref:System.Data.Linq.DataContext> is initialized with a connection or connection string that you supply.</span></span> <span data-ttu-id="764d9-106">Aby uzyskać więcej informacji, zobacz [metodę DataContext (Projektanta obiektów relacyjnych)](/visualstudio/data-tools/datacontext-methods-o-r-designer).</span><span class="sxs-lookup"><span data-stu-id="764d9-106">For more information, see [DataContext Methods (O/R Designer)](/visualstudio/data-tools/datacontext-methods-o-r-designer).</span></span>  
  
 <span data-ttu-id="764d9-107">Celem <xref:System.Data.Linq.DataContext> jest sformułowanie żądań dla obiektów do zapytania SQL, które ma zostać wykonane w bazie danych, a następnie do łączenia obiektów poza wyniki.</span><span class="sxs-lookup"><span data-stu-id="764d9-107">The purpose of the <xref:System.Data.Linq.DataContext> is to translate your requests for objects into SQL queries to be made against the database, and then to assemble objects out of the results.</span></span> <span data-ttu-id="764d9-108"><xref:System.Data.Linq.DataContext> Umożliwia [!INCLUDE[vbteclinqext](../../../../../../includes/vbteclinqext-md.md)] zaimplementowanie tego samego wzorca operatora jako standardowych operatorów zapytań, takich jak `Where` i `Select`.</span><span class="sxs-lookup"><span data-stu-id="764d9-108">The <xref:System.Data.Linq.DataContext> enables [!INCLUDE[vbteclinqext](../../../../../../includes/vbteclinqext-md.md)] by implementing the same operator pattern as the Standard Query Operators, such as `Where` and `Select`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="764d9-109">Obsługa bezpiecznego połączenia jest najwyższej wagi.</span><span class="sxs-lookup"><span data-stu-id="764d9-109">Maintaining a secure connection is of the highest importance.</span></span> <span data-ttu-id="764d9-110">Aby uzyskać więcej informacji, zobacz [zabezpieczeń w składniku LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/security-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="764d9-110">For more information, see [Security in LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/security-in-linq-to-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="764d9-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="764d9-111">Example</span></span>  
 <span data-ttu-id="764d9-112">W poniższym przykładzie <xref:System.Data.Linq.DataContext> służy do łączenia z przykładową bazą danych Northwind i pobierać wiersze klientów, których Miasto Londynie.</span><span class="sxs-lookup"><span data-stu-id="764d9-112">In the following example, the <xref:System.Data.Linq.DataContext> is used to connect to the Northwind sample database and to retrieve rows of customers whose city is London.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#1)]
 [!code-vb[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#1)]  
  
 <span data-ttu-id="764d9-113">Każda tabela bazy danych jest reprezentowany jako `Table` kolekcji dostępne poprzez <xref:System.Data.Linq.DataContext.GetTable%2A> — metoda, za pomocą klasy jednostki, aby zidentyfikować go.</span><span class="sxs-lookup"><span data-stu-id="764d9-113">Each database table is represented as a `Table` collection available by way of the <xref:System.Data.Linq.DataContext.GetTable%2A> method, by using the entity class to identify it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="764d9-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="764d9-114">Example</span></span>  
 <span data-ttu-id="764d9-115">Najlepszym rozwiązaniem jest, aby zadeklarować silnie typizowaną <xref:System.Data.Linq.DataContext> zamiast polegania na podstawowe <xref:System.Data.Linq.DataContext> klasy i <xref:System.Data.Linq.DataContext.GetTable%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="764d9-115">Best practice is to declare a strongly typed <xref:System.Data.Linq.DataContext> instead of relying on the basic <xref:System.Data.Linq.DataContext> class and the <xref:System.Data.Linq.DataContext.GetTable%2A> method.</span></span> <span data-ttu-id="764d9-116">Silnie typizowaną <xref:System.Data.Linq.DataContext> deklaruje wszystkich `Table` kolekcje w postaci członkami kontekst, jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="764d9-116">A strongly typed <xref:System.Data.Linq.DataContext> declares all `Table` collections as members of the context, as in the following example.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#2)]
 [!code-vb[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#2)]  
  
 <span data-ttu-id="764d9-117">Zapytania można następnie express dla klientów z Londynu po prostu jako:</span><span class="sxs-lookup"><span data-stu-id="764d9-117">You can then express the query for customers from London more simply as:</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#5)]
 [!code-vb[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="764d9-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="764d9-118">See Also</span></span>  
 [<span data-ttu-id="764d9-119">Podczas komunikacji z bazą danych</span><span class="sxs-lookup"><span data-stu-id="764d9-119">Communicating with the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)
