---
title: "Porady: Określanie nazwy bazy danych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b80f0fd2-7f75-45fe-9e12-496f80f183df
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: d0dffe22205b2d59dbd77bcd8f86efe4fa56be3b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-database-names"></a><span data-ttu-id="f94af-102">Porady: Określanie nazwy bazy danych</span><span class="sxs-lookup"><span data-stu-id="f94af-102">How to: Specify Database Names</span></span>
<span data-ttu-id="f94af-103">Użyj <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> właściwość <xref:System.Data.Linq.Mapping.DatabaseAttribute> atrybutu, aby określić nazwę bazy danych, kiedy nie podano nazwy dla tego połączenia.</span><span class="sxs-lookup"><span data-stu-id="f94af-103">Use the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property on a <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute to specify the name of a database when a name is not supplied by the connection.</span></span>  
  
 <span data-ttu-id="f94af-104">Aby uzyskać przykłady kodu, zobacz <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span><span class="sxs-lookup"><span data-stu-id="f94af-104">For code samples, see <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span></span>  
  
### <a name="to-specify-the-name-of-the-database"></a><span data-ttu-id="f94af-105">Aby określić nazwę bazy danych</span><span class="sxs-lookup"><span data-stu-id="f94af-105">To specify the name of the database</span></span>  
  
1.  <span data-ttu-id="f94af-106">Dodaj <xref:System.Data.Linq.Mapping.DatabaseAttribute> atrybutu deklaracji klasy dla bazy danych.</span><span class="sxs-lookup"><span data-stu-id="f94af-106">Add the <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute to the class declaration for the database.</span></span>  
  
2.  <span data-ttu-id="f94af-107">Dodaj <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> właściwości <xref:System.Data.Linq.Mapping.DatabaseAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="f94af-107">Add the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property to the <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute.</span></span>  
  
3.  <span data-ttu-id="f94af-108">Ustaw <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> wartość właściwości na nazwę, która ma zostać określony.</span><span class="sxs-lookup"><span data-stu-id="f94af-108">Set the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property value to the name that you want to specify.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f94af-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f94af-109">See Also</span></span>  
 [<span data-ttu-id="f94af-110">Model obiektu LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="f94af-110">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="f94af-111">Instrukcje: Dostosowywanie klas jednostek za pomocą edytora kodu</span><span class="sxs-lookup"><span data-stu-id="f94af-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
