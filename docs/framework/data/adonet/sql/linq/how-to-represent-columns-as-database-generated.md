---
title: 'Instrukcje: Reprezentacja kolumn jako wygenerowanych w bazie danych'
ms.date: 03/30/2017
ms.assetid: 6524b8a6-e5d2-4a3b-8e08-beafc4a84fd2
ms.openlocfilehash: bb9510986581ad6d3bcd0711aed681ef3a7c4e45
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781783"
---
# <a name="how-to-represent-columns-as-database-generated"></a><span data-ttu-id="2484a-102">Instrukcje: Reprezentacja kolumn jako wygenerowanych w bazie danych</span><span class="sxs-lookup"><span data-stu-id="2484a-102">How to: Represent Columns as Database-Generated</span></span>
<span data-ttu-id="2484a-103">Właściwość w atrybuciesłuży<xref:System.Data.Linq.Mapping.ColumnAttribute> do wyznaczania pola lub właściwości reprezentującej kolumnę wygenerowaną przez bazę danych. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A></span><span class="sxs-lookup"><span data-stu-id="2484a-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a field or property as representing a database-generated column.</span></span>  
  
 <span data-ttu-id="2484a-104">Aby zapoznać się z przykładami kodu, zobacz <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span><span class="sxs-lookup"><span data-stu-id="2484a-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span></span>  
  
### <a name="to-designate-a-field-or-property-as-representing-a-database-generated-column"></a><span data-ttu-id="2484a-105">Aby wyznaczyć pole lub właściwość reprezentującą kolumnę wygenerowaną przez bazę danych</span><span class="sxs-lookup"><span data-stu-id="2484a-105">To designate a field or property as representing a database-generated column</span></span>  
  
1. <span data-ttu-id="2484a-106"><xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> Dodaj Właściwość<xref:System.Data.Linq.Mapping.ColumnAttribute> do atrybutu.</span><span class="sxs-lookup"><span data-stu-id="2484a-106">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="2484a-107">Ustaw wartość właściwości na `true`.</span><span class="sxs-lookup"><span data-stu-id="2484a-107">Set the property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2484a-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2484a-108">See also</span></span>

- [<span data-ttu-id="2484a-109">Model obiektu LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="2484a-109">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="2484a-110">Instrukcje: Dostosowywanie klas jednostek przy użyciu edytora kodu</span><span class="sxs-lookup"><span data-stu-id="2484a-110">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
