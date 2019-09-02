---
title: Nawigowanie w elementach DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 202026a1-ec79-435e-b507-12a77f5011b2
ms.openlocfilehash: b5837d647b72f8dd17c4a6d3664faf8976243d36
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204556"
---
# <a name="navigating-datatables"></a><span data-ttu-id="6f50a-102">Nawigowanie w elementach DataTable</span><span class="sxs-lookup"><span data-stu-id="6f50a-102">Navigating DataTables</span></span>
<span data-ttu-id="6f50a-103">Uzyskuje zawartość co najmniej jednego <xref:System.Data.DataTable> obiektu w postaci co najmniej jednego zestawu wyników tylko do odczytu. <xref:System.Data.DataTableReader></span><span class="sxs-lookup"><span data-stu-id="6f50a-103">The <xref:System.Data.DataTableReader> obtains the contents of one or more <xref:System.Data.DataTable> objects in the form of one or more read-only, forward-only result sets.</span></span>  
  
 <span data-ttu-id="6f50a-104">Obiekt <xref:System.Data.DataTableReader> może zawierać wiele zestawów wyników, jeśli jest tworzony przy <xref:System.Data.DataSet.CreateDataReader%2A> użyciu metody.</span><span class="sxs-lookup"><span data-stu-id="6f50a-104">A <xref:System.Data.DataTableReader> may contain multiple result sets if it is created by using the <xref:System.Data.DataSet.CreateDataReader%2A> method.</span></span> <span data-ttu-id="6f50a-105">Jeśli istnieje więcej niż jeden zestaw wyników, <xref:System.Data.DataTableReader.NextResult%2A> Metoda przesuwa kursor do następnego zestawu wyników.</span><span class="sxs-lookup"><span data-stu-id="6f50a-105">When there is more than one result set, the <xref:System.Data.DataTableReader.NextResult%2A> method advances the cursor to the next result set.</span></span> <span data-ttu-id="6f50a-106">Jest to proces tylko do przesyłania dalej.</span><span class="sxs-lookup"><span data-stu-id="6f50a-106">This is a forward-only process.</span></span> <span data-ttu-id="6f50a-107">Nie można powrócić do poprzedniego zestawu wyników.</span><span class="sxs-lookup"><span data-stu-id="6f50a-107">It is not possible to return to a previous result set.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f50a-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="6f50a-108">Example</span></span>  
 <span data-ttu-id="6f50a-109">W poniższym przykładzie `TestConstructor` Metoda tworzy dwa <xref:System.Data.DataTable> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="6f50a-109">In the following example, the `TestConstructor` method creates two <xref:System.Data.DataTable> instances.</span></span> <span data-ttu-id="6f50a-110">Aby przedstawić ten Konstruktor dla <xref:System.Data.DataTableReader> klasy, przykład tworzy nowy **DataTableReader** na podstawie tablicy zawierającej dwie tabele DataTables i wykonuje prostą operację, drukując zawartość z pierwszych kilku kolumny do okna konsoli.</span><span class="sxs-lookup"><span data-stu-id="6f50a-110">In order to demonstrate this constructor for the <xref:System.Data.DataTableReader> class, the sample creates a new **DataTableReader** based on an array that contains the two **DataTables**, and performs a simple operation, printing the contents from the first few columns to the console window.</span></span>  
  
 [!code-csharp[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="6f50a-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6f50a-111">See also</span></span>

- [<span data-ttu-id="6f50a-112">Elementy DataTableReader</span><span class="sxs-lookup"><span data-stu-id="6f50a-112">DataTableReaders</span></span>](datatablereaders.md)
- [<span data-ttu-id="6f50a-113">ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="6f50a-113">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
