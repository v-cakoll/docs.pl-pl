---
title: 'Instrukcje: Filtrowanie powiązanych danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec8b8f97-5d01-4f31-9b97-d1556df6a4bc
ms.openlocfilehash: 3dbedfb7065ac4b1a570a3f6cdbcdcc2177f20cf
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59218228"
---
# <a name="how-to-filter-related-data"></a><span data-ttu-id="0ce98-102">Instrukcje: Filtrowanie powiązanych danych</span><span class="sxs-lookup"><span data-stu-id="0ce98-102">How to: Filter Related Data</span></span>
<span data-ttu-id="0ce98-103">Użyj <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> metodę, aby określić podzapytaniach, aby ograniczyć ilość pobierane są dane.</span><span class="sxs-lookup"><span data-stu-id="0ce98-103">Use the <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> method to specify sub-queries to limit the amount of retrieved data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ce98-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="0ce98-104">Example</span></span>  
 <span data-ttu-id="0ce98-105">W poniższym przykładzie <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> limity metoda `Orders` pobierane do tych, które nie zostały wysłane już dziś.</span><span class="sxs-lookup"><span data-stu-id="0ce98-105">In the following example, the <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> method limits the `Orders` retrieved to those that have not been shipped today.</span></span> <span data-ttu-id="0ce98-106">Bez tego podejścia wszystkich `Orders` będzie pobierana, nawet jeśli wymagane jest tylko ich podzestaw.</span><span class="sxs-lookup"><span data-stu-id="0ce98-106">Without this approach, all `Orders` would have been retrieved even though only a subset is desired.</span></span>  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="0ce98-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0ce98-107">See also</span></span>

- [<span data-ttu-id="0ce98-108">Wykonywanie zapytania w bazie danych</span><span class="sxs-lookup"><span data-stu-id="0ce98-108">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
