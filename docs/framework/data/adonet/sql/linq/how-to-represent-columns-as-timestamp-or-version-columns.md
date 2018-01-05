---
title: "Porady: reprezentowały kolumny znaczników czasu lub kolumny wersji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5afd5ce8-1d20-4bc3-a34f-49d95449f493
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 465be5cc0125d0ac45c0a00d7f1f238f3de8a390
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-represent-columns-as-timestamp-or-version-columns"></a><span data-ttu-id="77efa-102">Porady: reprezentowały kolumny znaczników czasu lub kolumny wersji</span><span class="sxs-lookup"><span data-stu-id="77efa-102">How to: Represent Columns as Timestamp or Version Columns</span></span>
<span data-ttu-id="77efa-103">Użyj [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> właściwość <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu określone pole lub właściwość jako reprezentujący kolumny bazy danych, który zawiera numery sygnatury czasowe lub wersji bazy danych.</span><span class="sxs-lookup"><span data-stu-id="77efa-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property of the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a field or property as representing a database column that holds database timestamps or version numbers.</span></span>  
  
 <span data-ttu-id="77efa-104">Aby uzyskać przykłady kodu, zobacz <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span><span class="sxs-lookup"><span data-stu-id="77efa-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span></span>  
  
### <a name="to-designate-a-field-or-property-as-representing-a-timestamp-or-version-column"></a><span data-ttu-id="77efa-105">Aby wyznaczyć kolumny znaczników czasu lub wersja reprezentujący pola lub właściwości</span><span class="sxs-lookup"><span data-stu-id="77efa-105">To designate a field or property as representing a timestamp or version column</span></span>  
  
1.  <span data-ttu-id="77efa-106">Dodaj <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> właściwości <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="77efa-106">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="77efa-107">Ustaw <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> wartości właściwości do `true`.</span><span class="sxs-lookup"><span data-stu-id="77efa-107">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77efa-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="77efa-108">See Also</span></span>  
 [<span data-ttu-id="77efa-109">Model obiektu LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="77efa-109">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="77efa-110">Instrukcje: Określanie, które elementy członkowskie są sprawdzane pod kątem konfliktów współbieżności</span><span class="sxs-lookup"><span data-stu-id="77efa-110">How to: Specify Which Members are Tested for Concurrency Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)  
 [<span data-ttu-id="77efa-111">Instrukcje: Dostosowywanie klas jednostek za pomocą edytora kodu</span><span class="sxs-lookup"><span data-stu-id="77efa-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
