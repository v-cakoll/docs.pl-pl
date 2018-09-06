---
title: Uzyskiwanie pojedynczej wartości z bazy danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b38526cd-a62a-48cb-822a-e91dfa68e02d
ms.openlocfilehash: 1a0d92c7acad58d3618c3f50b7463022352cf542
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43741964"
---
# <a name="obtaining-a-single-value-from-a-database"></a><span data-ttu-id="bdc80-102">Uzyskiwanie pojedynczej wartości z bazy danych</span><span class="sxs-lookup"><span data-stu-id="bdc80-102">Obtaining a Single Value from a Database</span></span>
<span data-ttu-id="bdc80-103">Może być konieczne o zwracanym bazy danych, które są po prostu pojedynczej wartości, a nie w formie strumienia tabeli lub danych.</span><span class="sxs-lookup"><span data-stu-id="bdc80-103">You may need to return database information that is simply a single value rather than in the form of a table or data stream.</span></span> <span data-ttu-id="bdc80-104">Na przykład możesz chcieć zwracają wynik funkcji agregującej, takie jak liczba (\*), SUM(Price) lub AVG(Quantity).</span><span class="sxs-lookup"><span data-stu-id="bdc80-104">For example, you may want to return the result of an aggregate function such as COUNT(\*), SUM(Price), or AVG(Quantity).</span></span> <span data-ttu-id="bdc80-105">**Polecenia** obiekt umożliwia zwracanie wartości pojedynczej przy użyciu **ExecuteScalar** metody.</span><span class="sxs-lookup"><span data-stu-id="bdc80-105">The **Command** object provides the capability to return single values using the **ExecuteScalar** method.</span></span> <span data-ttu-id="bdc80-106">**ExecuteScalar** metoda zwróci wartość, jako wartość skalarną, wartość pierwszą kolumnę pierwszego wiersza w zestawie wyników.</span><span class="sxs-lookup"><span data-stu-id="bdc80-106">The **ExecuteScalar** method returns, as a scalar value, the value of the first column of the first row of the result set.</span></span>  
  
 <span data-ttu-id="bdc80-107">Poniższy przykład kodu Wstawia nową wartość w bazie danych przy użyciu <xref:System.Data.SqlClient.SqlCommand>.</span><span class="sxs-lookup"><span data-stu-id="bdc80-107">The following code example inserts a new value in the database using a <xref:System.Data.SqlClient.SqlCommand>.</span></span> <span data-ttu-id="bdc80-108"><xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> Metoda służy do zwracania wartości kolumny tożsamości dla wstawionego rekordu.</span><span class="sxs-lookup"><span data-stu-id="bdc80-108">The <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> method is used to return the identity column value for the inserted record.</span></span>  
  
 [!code-csharp[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/CS/source.cs#1)]
 [!code-vb[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="bdc80-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bdc80-109">See Also</span></span>  
 [<span data-ttu-id="bdc80-110">Polecenia i parametry</span><span class="sxs-lookup"><span data-stu-id="bdc80-110">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="bdc80-111">Wykonywanie polecenia</span><span class="sxs-lookup"><span data-stu-id="bdc80-111">Executing a Command</span></span>](../../../../docs/framework/data/adonet/executing-a-command.md)  
 [<span data-ttu-id="bdc80-112">DbConnection, DbCommand i DbException</span><span class="sxs-lookup"><span data-stu-id="bdc80-112">DbConnection, DbCommand and DbException</span></span>](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)  
 [<span data-ttu-id="bdc80-113">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="bdc80-113">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
