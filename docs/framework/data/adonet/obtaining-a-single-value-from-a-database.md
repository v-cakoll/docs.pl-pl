---
title: Uzyskiwanie pojedynczą wartość z bazy danych
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: b38526cd-a62a-48cb-822a-e91dfa68e02d
caps.latest.revision: ''
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 41c3547d203a9958d3ad84303469c1e9591e6bd3
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2018
---
# <a name="obtaining-a-single-value-from-a-database"></a><span data-ttu-id="4a7bb-102">Uzyskiwanie pojedynczą wartość z bazy danych</span><span class="sxs-lookup"><span data-stu-id="4a7bb-102">Obtaining a Single Value from a Database</span></span>
<span data-ttu-id="4a7bb-103">Informacje o zwracany bazy danych, które są po prostu pojedynczą wartość, a nie w formie tabeli lub strumień danych może być konieczne.</span><span class="sxs-lookup"><span data-stu-id="4a7bb-103">You may need to return database information that is simply a single value rather than in the form of a table or data stream.</span></span> <span data-ttu-id="4a7bb-104">Na przykład można zwrócić wyników funkcji agregującej, takie jak liczba (\*), SUM(Price) lub AVG(Quantity).</span><span class="sxs-lookup"><span data-stu-id="4a7bb-104">For example, you may want to return the result of an aggregate function such as COUNT(\*), SUM(Price), or AVG(Quantity).</span></span> <span data-ttu-id="4a7bb-105">**Polecenia** obiektu oferuje możliwość zwrócić jednej wartości przy użyciu **ExecuteScalar** metody.</span><span class="sxs-lookup"><span data-stu-id="4a7bb-105">The **Command** object provides the capability to return single values using the **ExecuteScalar** method.</span></span> <span data-ttu-id="4a7bb-106">**ExecuteScalar** metoda zwróci wartość, jako wartość skalarną, wartość pierwszą kolumnę pierwszego wiersza w zestawie wyników.</span><span class="sxs-lookup"><span data-stu-id="4a7bb-106">The **ExecuteScalar** method returns, as a scalar value, the value of the first column of the first row of the result set.</span></span>  
  
 <span data-ttu-id="4a7bb-107">Poniższy przykład kodu Wstawia nową wartość w bazie danych przy użyciu <xref:System.Data.SqlClient.SqlCommand>.</span><span class="sxs-lookup"><span data-stu-id="4a7bb-107">The following code example inserts a new value in the database using a <xref:System.Data.SqlClient.SqlCommand>.</span></span> <span data-ttu-id="4a7bb-108"><xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> Metoda służy do zwracania wartości kolumny tożsamości wstawionego rekordu.</span><span class="sxs-lookup"><span data-stu-id="4a7bb-108">The <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> method is used to return the identity column value for the inserted record.</span></span>  
  
 [!code-csharp[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/CS/source.cs#1)]
 [!code-vb[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="4a7bb-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4a7bb-109">See Also</span></span>  
 [<span data-ttu-id="4a7bb-110">Polecenia i parametry</span><span class="sxs-lookup"><span data-stu-id="4a7bb-110">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="4a7bb-111">Wykonywanie polecenia</span><span class="sxs-lookup"><span data-stu-id="4a7bb-111">Executing a Command</span></span>](../../../../docs/framework/data/adonet/executing-a-command.md)  
 [<span data-ttu-id="4a7bb-112">DbConnection, DbCommand i DbException</span><span class="sxs-lookup"><span data-stu-id="4a7bb-112">DbConnection, DbCommand and DbException</span></span>](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)  
 [<span data-ttu-id="4a7bb-113">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="4a7bb-113">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
