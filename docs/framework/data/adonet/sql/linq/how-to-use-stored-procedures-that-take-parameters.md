---
title: 'Instrukcje: Używanie procedur składowanych, które przyjmują parametry'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b935fd84-cb9c-4205-8c48-658d5db2ec93
ms.openlocfilehash: 4f2636d3bb248adbb6b912887012b0b9c246c590
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793072"
---
# <a name="how-to-use-stored-procedures-that-take-parameters"></a><span data-ttu-id="01c05-102">Instrukcje: Używanie procedur składowanych, które przyjmują parametry</span><span class="sxs-lookup"><span data-stu-id="01c05-102">How to: Use Stored Procedures that Take Parameters</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="01c05-103">mapuje parametry wyjściowe do parametrów referencyjnych, a dla typów wartości deklaruje parametr jako wartość null.</span><span class="sxs-lookup"><span data-stu-id="01c05-103">maps output parameters to reference parameters, and for value types declares the parameter as nullable.</span></span>  
  
 <span data-ttu-id="01c05-104">Aby zapoznać się z przykładem użycia parametru wejściowego w zapytaniu, które zwraca zestaw wierszy, [zobacz How to: Zwróć zestawy wierszy](how-to-return-rowsets.md).</span><span class="sxs-lookup"><span data-stu-id="01c05-104">For an example of how to use an input parameter in a query that returns a rowset, see [How to: Return Rowsets](how-to-return-rowsets.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="01c05-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="01c05-105">Example</span></span>  
 <span data-ttu-id="01c05-106">Poniższy przykład przyjmuje jeden parametr wejściowy (identyfikator klienta) i zwraca parametr out (całkowita sprzedaż dla tego klienta).</span><span class="sxs-lookup"><span data-stu-id="01c05-106">The following example takes a single input parameter (the customer ID) and returns an out parameter (the total sales for that customer).</span></span>  
  
```  
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
  
## <a name="example"></a><span data-ttu-id="01c05-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="01c05-107">Example</span></span>  
 <span data-ttu-id="01c05-108">Tę procedurę składowaną należy wywołać w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="01c05-108">You would call this stored procedure as follows:</span></span>  
  
 [!code-csharp[DLinqSprox#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#3)]
 [!code-vb[DLinqSprox#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="01c05-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="01c05-109">See also</span></span>

- [<span data-ttu-id="01c05-110">Procedury składowane</span><span class="sxs-lookup"><span data-stu-id="01c05-110">Stored Procedures</span></span>](stored-procedures.md)
- [<span data-ttu-id="01c05-111">Pobieranie przykładowych baz danych</span><span class="sxs-lookup"><span data-stu-id="01c05-111">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
- [<span data-ttu-id="01c05-112">Używanie typów dopuszczających wartości null</span><span class="sxs-lookup"><span data-stu-id="01c05-112">Using Nullable Types</span></span>](../../../../../csharp/programming-guide/nullable-types/using-nullable-types.md)
- [<span data-ttu-id="01c05-113">Typy wartości dopuszczających wartości null</span><span class="sxs-lookup"><span data-stu-id="01c05-113">Nullable Value Types</span></span>](../../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
