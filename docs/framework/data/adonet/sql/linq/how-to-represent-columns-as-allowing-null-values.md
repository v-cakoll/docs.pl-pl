---
title: 'Instrukcje: Reprezentacja kolumn jako dopuszczających wartości Null'
ms.date: 03/30/2017
ms.assetid: ebb71a37-1f4c-4fa7-b2d2-d903f13c4af1
ms.openlocfilehash: 00a837467010c2d8a9f0ca16d6aba2fc5f4c973f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781811"
---
# <a name="how-to-represent-columns-as-allowing-null-values"></a><span data-ttu-id="a3105-102">Instrukcje: Reprezentacja kolumn jako dopuszczających wartości Null</span><span class="sxs-lookup"><span data-stu-id="a3105-102">How to: Represent Columns as Allowing Null Values</span></span>
<span data-ttu-id="a3105-103">Użyj właściwości w<xref:System.Data.Linq.Mapping.ColumnAttribute> atrybucie, aby określić, że skojarzona kolumna bazy danych może zawierać wartości null. <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3105-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to specify that the associated database column can hold null values.</span></span>  
  
 <span data-ttu-id="a3105-104">Aby zapoznać się z przykładami kodu, zobacz <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.</span><span class="sxs-lookup"><span data-stu-id="a3105-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.</span></span>  
  
### <a name="to-designate-a-column-as-allowing-null-values"></a><span data-ttu-id="a3105-105">Aby wyznaczyć kolumnę jako zezwalającą na wartości null</span><span class="sxs-lookup"><span data-stu-id="a3105-105">To designate a column as allowing null values</span></span>  
  
1. <span data-ttu-id="a3105-106"><xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> Dodaj Właściwość<xref:System.Data.Linq.Mapping.ColumnAttribute> do atrybutu.</span><span class="sxs-lookup"><span data-stu-id="a3105-106">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="a3105-107">`true`Ustaw wartość <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> właściwości na.</span><span class="sxs-lookup"><span data-stu-id="a3105-107">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3105-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a3105-108">See also</span></span>

- [<span data-ttu-id="a3105-109">Model obiektu LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="a3105-109">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="a3105-110">Instrukcje: Dostosowywanie klas jednostek przy użyciu edytora kodu</span><span class="sxs-lookup"><span data-stu-id="a3105-110">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
