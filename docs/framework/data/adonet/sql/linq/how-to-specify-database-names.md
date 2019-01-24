---
title: 'Instrukcje: Określanie nazw bazy danych'
ms.date: 03/30/2017
ms.assetid: b80f0fd2-7f75-45fe-9e12-496f80f183df
ms.openlocfilehash: a1198a294cd4921728919981bae213c0ee891da6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54556385"
---
# <a name="how-to-specify-database-names"></a><span data-ttu-id="e7215-102">Instrukcje: Określanie nazw bazy danych</span><span class="sxs-lookup"><span data-stu-id="e7215-102">How to: Specify Database Names</span></span>
<span data-ttu-id="e7215-103">Użyj <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> właściwość <xref:System.Data.Linq.Mapping.DatabaseAttribute> atrybutu, aby określić nazwę bazy danych, jeśli nie podano nazwy przez połączenie.</span><span class="sxs-lookup"><span data-stu-id="e7215-103">Use the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property on a <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute to specify the name of a database when a name is not supplied by the connection.</span></span>  
  
 <span data-ttu-id="e7215-104">Aby uzyskać przykłady kodu, zobacz <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span><span class="sxs-lookup"><span data-stu-id="e7215-104">For code samples, see <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span></span>  
  
### <a name="to-specify-the-name-of-the-database"></a><span data-ttu-id="e7215-105">Aby określić nazwę bazy danych</span><span class="sxs-lookup"><span data-stu-id="e7215-105">To specify the name of the database</span></span>  
  
1.  <span data-ttu-id="e7215-106">Dodaj <xref:System.Data.Linq.Mapping.DatabaseAttribute> atrybutu deklaracji klasy dla bazy danych.</span><span class="sxs-lookup"><span data-stu-id="e7215-106">Add the <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute to the class declaration for the database.</span></span>  
  
2.  <span data-ttu-id="e7215-107">Dodaj <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> właściwość <xref:System.Data.Linq.Mapping.DatabaseAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="e7215-107">Add the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property to the <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute.</span></span>  
  
3.  <span data-ttu-id="e7215-108">Ustaw <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> wartości właściwości, aby określić nazwę.</span><span class="sxs-lookup"><span data-stu-id="e7215-108">Set the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property value to the name that you want to specify.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7215-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e7215-109">See also</span></span>
- [<span data-ttu-id="e7215-110">Model obiektu LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="e7215-110">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="e7215-111">Instrukcje: Dostosowywanie klas jednostek za pomocą edytora kodu</span><span class="sxs-lookup"><span data-stu-id="e7215-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
