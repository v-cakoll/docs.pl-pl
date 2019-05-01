---
title: 'Instrukcje: Reprezentacja kolumn jako elementów członkowskich klas'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7ab28021-4d15-4d9c-bf2e-6ccc0daa7d1a
ms.openlocfilehash: 74966dd1661faa43df334987b2e3b0e84eff3446
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62037867"
---
# <a name="how-to-represent-columns-as-class-members"></a><span data-ttu-id="902df-102">Instrukcje: Reprezentacja kolumn jako elementów członkowskich klas</span><span class="sxs-lookup"><span data-stu-id="902df-102">How to: Represent Columns as Class Members</span></span>
<span data-ttu-id="902df-103">Użyj [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu, aby skojarzyć pola lub właściwości z kolumną bazy danych.</span><span class="sxs-lookup"><span data-stu-id="902df-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to associate a field or property with a database column.</span></span>  
  
### <a name="to-map-a-field-or-property-to-a-database-column"></a><span data-ttu-id="902df-104">Do mapowania pola lub właściwości kolumny bazy danych</span><span class="sxs-lookup"><span data-stu-id="902df-104">To map a field or property to a database column</span></span>  
  
- <span data-ttu-id="902df-105">Dodaj <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu deklaracji właściwości lub pola.</span><span class="sxs-lookup"><span data-stu-id="902df-105">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to the property or field declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="902df-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="902df-106">Example</span></span>  
 <span data-ttu-id="902df-107">Poniższy kod mapy `CustomerID` pole `Customer` klasy `CustomerID` kolumny w `Customers` tabeli bazy danych.</span><span class="sxs-lookup"><span data-stu-id="902df-107">The following code maps the `CustomerID` field in the `Customer` class to the `CustomerID` column in the `Customers` database table.</span></span>  
  
 [!code-csharp[DLinqCustomize#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#2)]
 [!code-vb[DLinqCustomize#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#2)]  
  
 <span data-ttu-id="902df-108">Nie trzeba określać <xref:System.Data.Linq.Mapping.DataAttribute.Name%2A> nazwę można wywnioskować właściwość.</span><span class="sxs-lookup"><span data-stu-id="902df-108">You do not have to specify the <xref:System.Data.Linq.Mapping.DataAttribute.Name%2A> property if the name can be inferred.</span></span> <span data-ttu-id="902df-109">Jeśli nie określisz nazwy, nazwa jest uznawana za tę taką samą nazwę jak właściwość lub pole.</span><span class="sxs-lookup"><span data-stu-id="902df-109">If you do not specify a name, the name is presumed to be the same name as that of the property or field.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="902df-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="902df-110">See also</span></span>

- [<span data-ttu-id="902df-111">Model obiektu LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="902df-111">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="902df-112">Instrukcje: Dostosowywanie klas jednostek za pomocą edytora kodu</span><span class="sxs-lookup"><span data-stu-id="902df-112">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
