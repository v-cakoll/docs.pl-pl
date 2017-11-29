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
ms.openlocfilehash: 88e30b947f18afd4ba93f816d9205c13d32fce82
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-represent-columns-as-timestamp-or-version-columns"></a><span data-ttu-id="df68c-102">Porady: reprezentowały kolumny znaczników czasu lub kolumny wersji</span><span class="sxs-lookup"><span data-stu-id="df68c-102">How to: Represent Columns as Timestamp or Version Columns</span></span>
<span data-ttu-id="df68c-103">Użyj [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> właściwość <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu określone pole lub właściwość jako reprezentujący kolumny bazy danych, który zawiera numery sygnatury czasowe lub wersji bazy danych.</span><span class="sxs-lookup"><span data-stu-id="df68c-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property of the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a field or property as representing a database column that holds database timestamps or version numbers.</span></span>  
  
 <span data-ttu-id="df68c-104">Aby uzyskać przykłady kodu, zobacz <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span><span class="sxs-lookup"><span data-stu-id="df68c-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span></span>  
  
### <a name="to-designate-a-field-or-property-as-representing-a-timestamp-or-version-column"></a><span data-ttu-id="df68c-105">Aby wyznaczyć kolumny znaczników czasu lub wersja reprezentujący pola lub właściwości</span><span class="sxs-lookup"><span data-stu-id="df68c-105">To designate a field or property as representing a timestamp or version column</span></span>  
  
1.  <span data-ttu-id="df68c-106">Dodaj <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> właściwości <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="df68c-106">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="df68c-107">Ustaw <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> wartości właściwości do `true`.</span><span class="sxs-lookup"><span data-stu-id="df68c-107">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df68c-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="df68c-108">See Also</span></span>  
 [<span data-ttu-id="df68c-109">LINQ do SQL modelu obiektów</span><span class="sxs-lookup"><span data-stu-id="df68c-109">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="df68c-110">Porady: Określanie, które elementy członkowskie są sprawdzane pod kątem konfliktom współbieżności</span><span class="sxs-lookup"><span data-stu-id="df68c-110">How to: Specify Which Members are Tested for Concurrency Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)  
 [<span data-ttu-id="df68c-111">Porady: dostosowywanie klas jednostek za pomocą edytora kodu</span><span class="sxs-lookup"><span data-stu-id="df68c-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
