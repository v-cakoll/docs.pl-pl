---
title: 'Instrukcje: Określanie pól magazynu prywatnego'
ms.date: 03/30/2017
ms.assetid: 5a40e816-cc6e-43a0-b32a-9caaa0ab6912
ms.openlocfilehash: e0928b2f2e817c8cc936f7aa1190229842a121a3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59195439"
---
# <a name="how-to-specify-private-storage-fields"></a><span data-ttu-id="d6fe7-102">Instrukcje: Określanie pól magazynu prywatnego</span><span class="sxs-lookup"><span data-stu-id="d6fe7-102">How to: Specify Private Storage Fields</span></span>
<span data-ttu-id="d6fe7-103">Użyj [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> właściwość <xref:System.Data.Linq.Mapping.DataAttribute> atrybutu, aby wyznaczyć nazwę odpowiedniego pola magazynu.</span><span class="sxs-lookup"><span data-stu-id="d6fe7-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> property on the <xref:System.Data.Linq.Mapping.DataAttribute> attribute to designate the name of an underlying storage field.</span></span>  
  
 <span data-ttu-id="d6fe7-104">Aby uzyskać przykłady kodu, zobacz <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>.</span><span class="sxs-lookup"><span data-stu-id="d6fe7-104">For code examples, see <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>.</span></span>  
  
### <a name="to-specify-the-name-of-an-underlying-storage-field"></a><span data-ttu-id="d6fe7-105">Aby określić nazwę odpowiedniego pola magazynu</span><span class="sxs-lookup"><span data-stu-id="d6fe7-105">To specify the name of an underlying storage field</span></span>  
  
1.  <span data-ttu-id="d6fe7-106">Dodaj <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> właściwość <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="d6fe7-106">Add the <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="d6fe7-107">Przypisz nazwę pola jako wartość <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="d6fe7-107">Assign the name of the field as the value of the <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6fe7-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d6fe7-108">See also</span></span>

- [<span data-ttu-id="d6fe7-109">Model obiektu LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="d6fe7-109">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="d6fe7-110">Instrukcje: Dostosowywanie klas jednostek za pomocą edytora kodu</span><span class="sxs-lookup"><span data-stu-id="d6fe7-110">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
