---
title: Uzyskiwanie pojedynczej wartości z bazy danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b38526cd-a62a-48cb-822a-e91dfa68e02d
ms.openlocfilehash: fb43d21546a0e98e87aab23db9213309b62320b9
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794748"
---
# <a name="obtaining-a-single-value-from-a-database"></a><span data-ttu-id="97a96-102">Uzyskiwanie pojedynczej wartości z bazy danych</span><span class="sxs-lookup"><span data-stu-id="97a96-102">Obtaining a Single Value from a Database</span></span>
<span data-ttu-id="97a96-103">Może być konieczne zwrócenie informacji o bazie danych, która jest po prostu pojedynczą wartością, a nie w formie tabeli lub strumienia danych.</span><span class="sxs-lookup"><span data-stu-id="97a96-103">You may need to return database information that is simply a single value rather than in the form of a table or data stream.</span></span> <span data-ttu-id="97a96-104">Na przykład możesz chcieć zwrócić wynik funkcji agregującej, takiej jak Count (\*), sum (Price) lub AVG (ilość).</span><span class="sxs-lookup"><span data-stu-id="97a96-104">For example, you may want to return the result of an aggregate function such as COUNT(\*), SUM(Price), or AVG(Quantity).</span></span> <span data-ttu-id="97a96-105">Obiekt **Command** oferuje możliwość zwracania pojedynczych wartości przy użyciu metody **ExecuteScalar** .</span><span class="sxs-lookup"><span data-stu-id="97a96-105">The **Command** object provides the capability to return single values using the **ExecuteScalar** method.</span></span> <span data-ttu-id="97a96-106">Metoda **ExecuteScalar** zwraca, jako wartość skalarną, wartość pierwszej kolumny pierwszego wiersza w zestawie wyników.</span><span class="sxs-lookup"><span data-stu-id="97a96-106">The **ExecuteScalar** method returns, as a scalar value, the value of the first column of the first row of the result set.</span></span>  
  
 <span data-ttu-id="97a96-107">Poniższy przykład kodu wstawia nową wartość w bazie danych przy użyciu <xref:System.Data.SqlClient.SqlCommand>.</span><span class="sxs-lookup"><span data-stu-id="97a96-107">The following code example inserts a new value in the database using a <xref:System.Data.SqlClient.SqlCommand>.</span></span> <span data-ttu-id="97a96-108"><xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> Metoda jest używana do zwracania wartości kolumny Identity dla wstawionego rekordu.</span><span class="sxs-lookup"><span data-stu-id="97a96-108">The <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> method is used to return the identity column value for the inserted record.</span></span>  
  
 [!code-csharp[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/CS/source.cs#1)]
 [!code-vb[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="97a96-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="97a96-109">See also</span></span>

- [<span data-ttu-id="97a96-110">Polecenia i parametry</span><span class="sxs-lookup"><span data-stu-id="97a96-110">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="97a96-111">Wykonywanie polecenia</span><span class="sxs-lookup"><span data-stu-id="97a96-111">Executing a Command</span></span>](executing-a-command.md)
- [<span data-ttu-id="97a96-112">DbConnection, DbCommand i DbException</span><span class="sxs-lookup"><span data-stu-id="97a96-112">DbConnection, DbCommand and DbException</span></span>](dbconnection-dbcommand-and-dbexception.md)
- [<span data-ttu-id="97a96-113">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="97a96-113">ADO.NET Overview</span></span>](ado-net-overview.md)
