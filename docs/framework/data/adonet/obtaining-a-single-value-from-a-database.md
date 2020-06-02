---
title: Uzyskiwanie pojedynczej wartości z bazy danych
description: Dowiedz się, jak zwrócić pojedynczą wartość w ADO.NET. Ten przykładowy kod zwraca wartość kolumny tożsamości dla wstawionego rekordu.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b38526cd-a62a-48cb-822a-e91dfa68e02d
ms.openlocfilehash: a6f268f72f8b8a09ae48ba3cad6254323cb95a20
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286705"
---
# <a name="obtaining-a-single-value-from-a-database"></a><span data-ttu-id="adc2b-104">Uzyskiwanie pojedynczej wartości z bazy danych</span><span class="sxs-lookup"><span data-stu-id="adc2b-104">Obtaining a Single Value from a Database</span></span>
<span data-ttu-id="adc2b-105">Może być konieczne zwrócenie informacji o bazie danych, która jest po prostu pojedynczą wartością, a nie w formie tabeli lub strumienia danych.</span><span class="sxs-lookup"><span data-stu-id="adc2b-105">You may need to return database information that is simply a single value rather than in the form of a table or data stream.</span></span> <span data-ttu-id="adc2b-106">Na przykład możesz chcieć zwrócić wynik funkcji agregującej, takiej jak COUNT ( \* ), sum (Price) lub AVG (ilość).</span><span class="sxs-lookup"><span data-stu-id="adc2b-106">For example, you may want to return the result of an aggregate function such as COUNT(\*), SUM(Price), or AVG(Quantity).</span></span> <span data-ttu-id="adc2b-107">Obiekt **Command** oferuje możliwość zwracania pojedynczych wartości przy użyciu metody **ExecuteScalar** .</span><span class="sxs-lookup"><span data-stu-id="adc2b-107">The **Command** object provides the capability to return single values using the **ExecuteScalar** method.</span></span> <span data-ttu-id="adc2b-108">Metoda **ExecuteScalar** zwraca, jako wartość skalarną, wartość pierwszej kolumny pierwszego wiersza w zestawie wyników.</span><span class="sxs-lookup"><span data-stu-id="adc2b-108">The **ExecuteScalar** method returns, as a scalar value, the value of the first column of the first row of the result set.</span></span>  
  
 <span data-ttu-id="adc2b-109">Poniższy przykład kodu wstawia nową wartość w bazie danych przy użyciu <xref:System.Data.SqlClient.SqlCommand> .</span><span class="sxs-lookup"><span data-stu-id="adc2b-109">The following code example inserts a new value in the database using a <xref:System.Data.SqlClient.SqlCommand>.</span></span> <span data-ttu-id="adc2b-110"><xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A>Metoda jest używana do zwracania wartości kolumny Identity dla wstawionego rekordu.</span><span class="sxs-lookup"><span data-stu-id="adc2b-110">The <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> method is used to return the identity column value for the inserted record.</span></span>  
  
 [!code-csharp[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/CS/source.cs#1)]
 [!code-vb[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="adc2b-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="adc2b-111">See also</span></span>

- [<span data-ttu-id="adc2b-112">Polecenia i parametry</span><span class="sxs-lookup"><span data-stu-id="adc2b-112">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="adc2b-113">Wykonywanie polecenia</span><span class="sxs-lookup"><span data-stu-id="adc2b-113">Executing a Command</span></span>](executing-a-command.md)
- [<span data-ttu-id="adc2b-114">DbConnection, DbCommand i DbException</span><span class="sxs-lookup"><span data-stu-id="adc2b-114">DbConnection, DbCommand and DbException</span></span>](dbconnection-dbcommand-and-dbexception.md)
- [<span data-ttu-id="adc2b-115">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="adc2b-115">ADO.NET Overview</span></span>](ado-net-overview.md)
