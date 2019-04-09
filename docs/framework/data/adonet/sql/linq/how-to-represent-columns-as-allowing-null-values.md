---
title: 'Instrukcje: Reprezentacja kolumn jako dopuszczających wartości Null'
ms.date: 03/30/2017
ms.assetid: ebb71a37-1f4c-4fa7-b2d2-d903f13c4af1
ms.openlocfilehash: e3bab3f307bcba77e0d311b96fa79d5a0d01e937
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59169640"
---
# <a name="how-to-represent-columns-as-allowing-null-values"></a><span data-ttu-id="ab8fc-102">Instrukcje: Reprezentacja kolumn jako dopuszczających wartości Null</span><span class="sxs-lookup"><span data-stu-id="ab8fc-102">How to: Represent Columns as Allowing Null Values</span></span>
<span data-ttu-id="ab8fc-103">Użyj [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> właściwość <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu, aby określić, że kolumny skojarzonej bazy danych może zawierać wartości null.</span><span class="sxs-lookup"><span data-stu-id="ab8fc-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to specify that the associated database column can hold null values.</span></span>  
  
 <span data-ttu-id="ab8fc-104">Aby uzyskać przykłady kodu, zobacz <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.</span><span class="sxs-lookup"><span data-stu-id="ab8fc-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.</span></span>  
  
### <a name="to-designate-a-column-as-allowing-null-values"></a><span data-ttu-id="ab8fc-105">Aby wyznaczyć kolumn jako dopuszczających wartości null</span><span class="sxs-lookup"><span data-stu-id="ab8fc-105">To designate a column as allowing null values</span></span>  
  
1.  <span data-ttu-id="ab8fc-106">Dodaj <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> właściwość <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="ab8fc-106">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="ab8fc-107">Ustaw <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> wartość właściwości `true`.</span><span class="sxs-lookup"><span data-stu-id="ab8fc-107">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab8fc-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ab8fc-108">See also</span></span>

- [<span data-ttu-id="ab8fc-109">Model obiektu LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="ab8fc-109">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="ab8fc-110">Instrukcje: Dostosowywanie klas jednostek za pomocą edytora kodu</span><span class="sxs-lookup"><span data-stu-id="ab8fc-110">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
