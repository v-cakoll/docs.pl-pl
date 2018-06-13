---
title: 'Porady: reprezentować kolumny dopuszczającej wartości Null'
ms.date: 03/30/2017
ms.assetid: ebb71a37-1f4c-4fa7-b2d2-d903f13c4af1
ms.openlocfilehash: 6700ee5d4de53dd82da29d48ca7c42785d52afc1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33355980"
---
# <a name="how-to-represent-columns-as-allowing-null-values"></a><span data-ttu-id="daed6-102">Porady: reprezentować kolumny dopuszczającej wartości Null</span><span class="sxs-lookup"><span data-stu-id="daed6-102">How to: Represent Columns as Allowing Null Values</span></span>
<span data-ttu-id="daed6-103">Użyj [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> właściwość <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu, aby określić, że kolumna skojarzonej bazy danych może zawierać wartości null.</span><span class="sxs-lookup"><span data-stu-id="daed6-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to specify that the associated database column can hold null values.</span></span>  
  
 <span data-ttu-id="daed6-104">Aby uzyskać przykłady kodu, zobacz <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.</span><span class="sxs-lookup"><span data-stu-id="daed6-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.</span></span>  
  
### <a name="to-designate-a-column-as-allowing-null-values"></a><span data-ttu-id="daed6-105">Aby wyznaczyć kolumny dopuszczającej wartości null</span><span class="sxs-lookup"><span data-stu-id="daed6-105">To designate a column as allowing null values</span></span>  
  
1.  <span data-ttu-id="daed6-106">Dodaj <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> właściwości <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="daed6-106">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="daed6-107">Ustaw <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> wartości właściwości do `true`.</span><span class="sxs-lookup"><span data-stu-id="daed6-107">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="daed6-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="daed6-108">See Also</span></span>  
 [<span data-ttu-id="daed6-109">Model obiektu LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="daed6-109">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="daed6-110">Instrukcje: Dostosowywanie klas jednostek za pomocą edytora kodu</span><span class="sxs-lookup"><span data-stu-id="daed6-110">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
