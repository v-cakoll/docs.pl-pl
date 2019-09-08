---
title: 'Instrukcje: Reprezentacja kolumn jako elementów członkowskich klas'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7ab28021-4d15-4d9c-bf2e-6ccc0daa7d1a
ms.openlocfilehash: 515a8477b3a9c72934e0ad11d7b1bf599e8b16a2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793514"
---
# <a name="how-to-represent-columns-as-class-members"></a><span data-ttu-id="8ab97-102">Instrukcje: Reprezentacja kolumn jako elementów członkowskich klas</span><span class="sxs-lookup"><span data-stu-id="8ab97-102">How to: Represent Columns as Class Members</span></span>
<span data-ttu-id="8ab97-103">Użyj atrybutu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , <xref:System.Data.Linq.Mapping.ColumnAttribute> aby skojarzyć pole lub właściwość z kolumną bazy danych.</span><span class="sxs-lookup"><span data-stu-id="8ab97-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to associate a field or property with a database column.</span></span>  
  
### <a name="to-map-a-field-or-property-to-a-database-column"></a><span data-ttu-id="8ab97-104">Aby zmapować pole lub właściwość do kolumny bazy danych</span><span class="sxs-lookup"><span data-stu-id="8ab97-104">To map a field or property to a database column</span></span>  
  
- <span data-ttu-id="8ab97-105"><xref:System.Data.Linq.Mapping.ColumnAttribute> Dodaj atrybut do deklaracji właściwości lub pola.</span><span class="sxs-lookup"><span data-stu-id="8ab97-105">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to the property or field declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ab97-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="8ab97-106">Example</span></span>  
 <span data-ttu-id="8ab97-107">Poniższy kod mapuje `CustomerID` pole `Customer` w klasie `Customers` do `CustomerID` kolumny w tabeli bazy danych.</span><span class="sxs-lookup"><span data-stu-id="8ab97-107">The following code maps the `CustomerID` field in the `Customer` class to the `CustomerID` column in the `Customers` database table.</span></span>  
  
 [!code-csharp[DLinqCustomize#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#2)]
 [!code-vb[DLinqCustomize#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#2)]  
  
 <span data-ttu-id="8ab97-108">Nie trzeba określać <xref:System.Data.Linq.Mapping.DataAttribute.Name%2A> właściwości, jeśli można wywnioskować nazwę.</span><span class="sxs-lookup"><span data-stu-id="8ab97-108">You do not have to specify the <xref:System.Data.Linq.Mapping.DataAttribute.Name%2A> property if the name can be inferred.</span></span> <span data-ttu-id="8ab97-109">Jeśli nie określisz nazwy, przyjmuje się, że nazwa jest taka sama jak nazwa właściwości lub pola.</span><span class="sxs-lookup"><span data-stu-id="8ab97-109">If you do not specify a name, the name is presumed to be the same name as that of the property or field.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ab97-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8ab97-110">See also</span></span>

- [<span data-ttu-id="8ab97-111">Model obiektu LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="8ab97-111">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="8ab97-112">Instrukcje: Dostosowywanie klas jednostek przy użyciu edytora kodu</span><span class="sxs-lookup"><span data-stu-id="8ab97-112">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
