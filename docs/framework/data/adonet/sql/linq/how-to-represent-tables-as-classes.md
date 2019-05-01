---
title: 'Instrukcje: Reprezentacja tabel jako klas'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 84dda12b-88a2-4cd2-92b3-8db87b28d14c
ms.openlocfilehash: 49e7d6768d8739bba94c9e8d38bcc582c8bd6e4e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61902905"
---
# <a name="how-to-represent-tables-as-classes"></a><span data-ttu-id="e70ec-102">Instrukcje: Reprezentacja tabel jako klas</span><span class="sxs-lookup"><span data-stu-id="e70ec-102">How to: Represent Tables as Classes</span></span>
<span data-ttu-id="e70ec-103">Użyj [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.TableAttribute> atrybutu, aby określić klasę jako klasę jednostki skojarzonej z tabelą bazy danych.</span><span class="sxs-lookup"><span data-stu-id="e70ec-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.TableAttribute> attribute to designate a class as an entity class associated with a database table.</span></span>  
  
### <a name="to-map-a-class-to-a-database-table"></a><span data-ttu-id="e70ec-104">Aby zamapować klasę do tabeli bazy danych</span><span class="sxs-lookup"><span data-stu-id="e70ec-104">To map a class to a database table</span></span>  
  
- <span data-ttu-id="e70ec-105">Dodaj <xref:System.Data.Linq.Mapping.TableAttribute> atrybutu deklaracji klasy.</span><span class="sxs-lookup"><span data-stu-id="e70ec-105">Add the <xref:System.Data.Linq.Mapping.TableAttribute> attribute to the class declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e70ec-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="e70ec-106">Example</span></span>  
 <span data-ttu-id="e70ec-107">Poniższy kod ustanawia `Customer` jak klasa jednostki, która jest skojarzona z `Customers` tabeli bazy danych.</span><span class="sxs-lookup"><span data-stu-id="e70ec-107">The following code establishes the `Customer` class as an entity class that is associated with the `Customers` database table.</span></span>  
  
 [!code-csharp[DLinqCustomize#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#1)]
 [!code-vb[DLinqCustomize#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#1)]  
  
 <span data-ttu-id="e70ec-108">Nie trzeba określać <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> nazwę można wywnioskować właściwość.</span><span class="sxs-lookup"><span data-stu-id="e70ec-108">You do not have to specify the <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> property if the name can be inferred.</span></span> <span data-ttu-id="e70ec-109">Jeśli nie określisz nazwy, nazwa jest uznawana za tę taką samą nazwę jak właściwość lub pole.</span><span class="sxs-lookup"><span data-stu-id="e70ec-109">If you do not specify a name, the name is presumed to be the same name as that of the property or field.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e70ec-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e70ec-110">See also</span></span>

- [<span data-ttu-id="e70ec-111">Model obiektu LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="e70ec-111">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="e70ec-112">Instrukcje: Dostosowywanie klas jednostek za pomocą edytora kodu</span><span class="sxs-lookup"><span data-stu-id="e70ec-112">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
