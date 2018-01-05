---
title: 'Porady: reprezentuje tabele jako klasy'
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
ms.assetid: 84dda12b-88a2-4cd2-92b3-8db87b28d14c
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 27e3d21e42dbf841768e2a68ccbfff62368500bb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-represent-tables-as-classes"></a><span data-ttu-id="f60b2-102">Porady: reprezentuje tabele jako klasy</span><span class="sxs-lookup"><span data-stu-id="f60b2-102">How to: Represent Tables as Classes</span></span>
<span data-ttu-id="f60b2-103">Użyj [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.TableAttribute> atrybutu, aby wyznaczyć klasy klasę jednostki skojarzonej z tabelą bazy danych.</span><span class="sxs-lookup"><span data-stu-id="f60b2-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.TableAttribute> attribute to designate a class as an entity class associated with a database table.</span></span>  
  
### <a name="to-map-a-class-to-a-database-table"></a><span data-ttu-id="f60b2-104">Do mapowania klasy tabeli bazy danych</span><span class="sxs-lookup"><span data-stu-id="f60b2-104">To map a class to a database table</span></span>  
  
-   <span data-ttu-id="f60b2-105">Dodaj <xref:System.Data.Linq.Mapping.TableAttribute> atrybutu deklaracji klasy.</span><span class="sxs-lookup"><span data-stu-id="f60b2-105">Add the <xref:System.Data.Linq.Mapping.TableAttribute> attribute to the class declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f60b2-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="f60b2-106">Example</span></span>  
 <span data-ttu-id="f60b2-107">Poniższy kod ustanawia `Customer` jak klasa jednostki, z którym skojarzony jest `Customers` tabeli bazy danych.</span><span class="sxs-lookup"><span data-stu-id="f60b2-107">The following code establishes the `Customer` class as an entity class that is associated with the `Customers` database table.</span></span>  
  
 [!code-csharp[DLinqCustomize#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#1)]
 [!code-vb[DLinqCustomize#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#1)]  
  
 <span data-ttu-id="f60b2-108">Nie trzeba określać <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> właściwości, jeśli można wywnioskować nazwy.</span><span class="sxs-lookup"><span data-stu-id="f60b2-108">You do not have to specify the <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> property if the name can be inferred.</span></span> <span data-ttu-id="f60b2-109">Jeśli nie określisz nazwy, nazwa jest uznawany za taką samą nazwę jak właściwości lub pola.</span><span class="sxs-lookup"><span data-stu-id="f60b2-109">If you do not specify a name, the name is presumed to be the same name as that of the property or field.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f60b2-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f60b2-110">See Also</span></span>  
 [<span data-ttu-id="f60b2-111">Model obiektu LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="f60b2-111">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="f60b2-112">Instrukcje: Dostosowywanie klas jednostek za pomocą edytora kodu</span><span class="sxs-lookup"><span data-stu-id="f60b2-112">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
