---
title: 'Instrukcje: Reprezentacja kolumn jako wygenerowanych w bazie danych'
ms.date: 03/30/2017
ms.assetid: 6524b8a6-e5d2-4a3b-8e08-beafc4a84fd2
ms.openlocfilehash: 2803697c668a8e1dbbeb426ea41b64878f70c145
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59307915"
---
# <a name="how-to-represent-columns-as-database-generated"></a><span data-ttu-id="785eb-102">Instrukcje: Reprezentacja kolumn jako wygenerowanych w bazie danych</span><span class="sxs-lookup"><span data-stu-id="785eb-102">How to: Represent Columns as Database-Generated</span></span>
<span data-ttu-id="785eb-103">Użyj [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> właściwość <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu, aby wyznaczyć reprezentujący kolumnę wygenerowanych w bazie danych do pola lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="785eb-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a field or property as representing a database-generated column.</span></span>  
  
 <span data-ttu-id="785eb-104">Aby uzyskać przykłady kodu, zobacz <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span><span class="sxs-lookup"><span data-stu-id="785eb-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span></span>  
  
### <a name="to-designate-a-field-or-property-as-representing-a-database-generated-column"></a><span data-ttu-id="785eb-105">Aby wyznaczyć pole lub właściwość jako kolumnę wygenerowanych w bazie danych</span><span class="sxs-lookup"><span data-stu-id="785eb-105">To designate a field or property as representing a database-generated column</span></span>  
  
1. <span data-ttu-id="785eb-106">Dodaj <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> właściwość <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="785eb-106">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="785eb-107">Ustaw wartość właściwości `true`.</span><span class="sxs-lookup"><span data-stu-id="785eb-107">Set the property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="785eb-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="785eb-108">See also</span></span>

- [<span data-ttu-id="785eb-109">Model obiektu LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="785eb-109">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="785eb-110">Instrukcje: Dostosowywanie klas jednostek za pomocą edytora kodu</span><span class="sxs-lookup"><span data-stu-id="785eb-110">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
