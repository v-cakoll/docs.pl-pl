---
title: 'Instrukcje: korzystanie z procedur składowanych przyjmujących parametry'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b935fd84-cb9c-4205-8c48-658d5db2ec93
ms.openlocfilehash: faf4ea9c52b91c3fc0f2f775e7bd5dfe039c53a8
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738115"
---
# <a name="how-to-use-stored-procedures-that-take-parameters"></a><span data-ttu-id="92f23-102">Instrukcje: korzystanie z procedur składowanych przyjmujących parametry</span><span class="sxs-lookup"><span data-stu-id="92f23-102">How to: Use Stored Procedures that Take Parameters</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="92f23-103">mapuje parametry wyjściowe do parametrów referencyjnych, a dla typów wartości deklaruje parametr jako wartość null.</span><span class="sxs-lookup"><span data-stu-id="92f23-103">maps output parameters to reference parameters, and for value types declares the parameter as nullable.</span></span>  
  
 <span data-ttu-id="92f23-104">Aby zapoznać się z przykładem użycia parametru wejściowego w zapytaniu, które zwraca zestaw wierszy, zobacz [How to: Return Rowsets](how-to-return-rowsets.md).</span><span class="sxs-lookup"><span data-stu-id="92f23-104">For an example of how to use an input parameter in a query that returns a rowset, see [How to: Return Rowsets](how-to-return-rowsets.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="92f23-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="92f23-105">Example</span></span>  
 <span data-ttu-id="92f23-106">Poniższy przykład przyjmuje jeden parametr wejściowy (identyfikator klienta) i zwraca parametr out (całkowita sprzedaż dla tego klienta).</span><span class="sxs-lookup"><span data-stu-id="92f23-106">The following example takes a single input parameter (the customer ID) and returns an out parameter (the total sales for that customer).</span></span>  
  
```sql
CREATE PROCEDURE [dbo].[CustOrderTotal]   
@CustomerID nchar(5),  
@TotalSales money OUTPUT  
AS  
SELECT @TotalSales = SUM(OD.UNITPRICE*(1-OD.DISCOUNT) * OD.QUANTITY)  
FROM ORDERS O, "ORDER DETAILS" OD  
where O.CUSTOMERID = @CustomerID AND O.ORDERID = OD.ORDERID  
```  
  
 [!code-csharp[DLinqSprox#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#2)]
 [!code-vb[DLinqSprox#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="92f23-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="92f23-107">Example</span></span>  
 <span data-ttu-id="92f23-108">Tę procedurę składowaną należy wywołać w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="92f23-108">You would call this stored procedure as follows:</span></span>  
  
 [!code-csharp[DLinqSprox#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#3)]
 [!code-vb[DLinqSprox#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="92f23-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="92f23-109">See also</span></span>

- [<span data-ttu-id="92f23-110">Procedury składowane</span><span class="sxs-lookup"><span data-stu-id="92f23-110">Stored Procedures</span></span>](stored-procedures.md)
- [<span data-ttu-id="92f23-111">Pobieranie przykładowych baz danych</span><span class="sxs-lookup"><span data-stu-id="92f23-111">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
- [<span data-ttu-id="92f23-112">Typy wartości null (C#)</span><span class="sxs-lookup"><span data-stu-id="92f23-112">Nullable Value Types (C#)</span></span>](../../../../../csharp/language-reference/builtin-types/nullable-value-types.md)
- [<span data-ttu-id="92f23-113">Typy wartości null (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="92f23-113">Nullable Value Types (Visual Basic)</span></span>](../../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
