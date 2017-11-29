---
title: "Porady: reprezentuje kolumn jako elementy członkowskie klasy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 7ab28021-4d15-4d9c-bf2e-6ccc0daa7d1a
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f0e797886b5e2fedafccf08b71e8cbb2791ea72b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-represent-columns-as-class-members"></a><span data-ttu-id="a7636-102">Porady: reprezentuje kolumn jako elementy członkowskie klasy</span><span class="sxs-lookup"><span data-stu-id="a7636-102">How to: Represent Columns as Class Members</span></span>
<span data-ttu-id="a7636-103">Użyj [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu, aby skojarzyć pola lub właściwości z kolumną bazy danych.</span><span class="sxs-lookup"><span data-stu-id="a7636-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to associate a field or property with a database column.</span></span>  
  
### <a name="to-map-a-field-or-property-to-a-database-column"></a><span data-ttu-id="a7636-104">Aby mapować pola lub właściwości do kolumny bazy danych</span><span class="sxs-lookup"><span data-stu-id="a7636-104">To map a field or property to a database column</span></span>  
  
-   <span data-ttu-id="a7636-105">Dodaj <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu deklaracji właściwości lub pola.</span><span class="sxs-lookup"><span data-stu-id="a7636-105">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to the property or field declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7636-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="a7636-106">Example</span></span>  
 <span data-ttu-id="a7636-107">Poniższy kod mapy `CustomerID` w `Customer` klasy do `CustomerID` kolumny w `Customers` tabeli bazy danych.</span><span class="sxs-lookup"><span data-stu-id="a7636-107">The following code maps the `CustomerID` field in the `Customer` class to the `CustomerID` column in the `Customers` database table.</span></span>  
  
 [!code-csharp[DLinqCustomize#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#2)]
 [!code-vb[DLinqCustomize#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#2)]  
  
 <span data-ttu-id="a7636-108">Nie trzeba określać <xref:System.Data.Linq.Mapping.DataAttribute.Name%2A> właściwości, jeśli można wywnioskować nazwy.</span><span class="sxs-lookup"><span data-stu-id="a7636-108">You do not have to specify the <xref:System.Data.Linq.Mapping.DataAttribute.Name%2A> property if the name can be inferred.</span></span> <span data-ttu-id="a7636-109">Jeśli nie określisz nazwy, nazwa jest uznawany za taką samą nazwę jak właściwości lub pola.</span><span class="sxs-lookup"><span data-stu-id="a7636-109">If you do not specify a name, the name is presumed to be the same name as that of the property or field.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7636-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a7636-110">See Also</span></span>  
 [<span data-ttu-id="a7636-111">LINQ do SQL modelu obiektów</span><span class="sxs-lookup"><span data-stu-id="a7636-111">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="a7636-112">Porady: dostosowywanie klas jednostek za pomocą edytora kodu</span><span class="sxs-lookup"><span data-stu-id="a7636-112">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
