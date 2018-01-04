---
title: "Porady: reprezentuje kolumn jako baza danych wygenerowała"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6524b8a6-e5d2-4a3b-8e08-beafc4a84fd2
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 6081dd8b6771fc914634f126f7836b4c26147eea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-represent-columns-as-database-generated"></a><span data-ttu-id="22e44-102">Porady: reprezentuje kolumn jako baza danych wygenerowała</span><span class="sxs-lookup"><span data-stu-id="22e44-102">How to: Represent Columns as Database-Generated</span></span>
<span data-ttu-id="22e44-103">Użyj [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> właściwość <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu, aby wyznaczyć reprezentująca kolumnę baza danych wygenerowała pola lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="22e44-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a field or property as representing a database-generated column.</span></span>  
  
 <span data-ttu-id="22e44-104">Aby uzyskać przykłady kodu, zobacz <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span><span class="sxs-lookup"><span data-stu-id="22e44-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span></span>  
  
### <a name="to-designate-a-field-or-property-as-representing-a-database-generated-column"></a><span data-ttu-id="22e44-105">Aby wyznaczyć reprezentujący kolumny bazy danych, wygenerowane pole lub właściwość</span><span class="sxs-lookup"><span data-stu-id="22e44-105">To designate a field or property as representing a database-generated column</span></span>  
  
1.  <span data-ttu-id="22e44-106">Dodaj <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> właściwości <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="22e44-106">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="22e44-107">Ustaw wartość właściwości `true`.</span><span class="sxs-lookup"><span data-stu-id="22e44-107">Set the property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22e44-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="22e44-108">See Also</span></span>  
 [<span data-ttu-id="22e44-109">Model obiektu LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="22e44-109">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="22e44-110">Instrukcje: Dostosowywanie klas jednostek za pomocą edytora kodu</span><span class="sxs-lookup"><span data-stu-id="22e44-110">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
