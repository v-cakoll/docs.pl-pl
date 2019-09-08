---
title: 'Instrukcje: Reprezentacja kolumn jako kolumn znacznika czasu lub wersji'
ms.date: 03/30/2017
ms.assetid: 5afd5ce8-1d20-4bc3-a34f-49d95449f493
ms.openlocfilehash: ef99e0420b328f94686e08256ecf229000467810
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793503"
---
# <a name="how-to-represent-columns-as-timestamp-or-version-columns"></a><span data-ttu-id="f8539-102">Instrukcje: Reprezentacja kolumn jako kolumn znacznika czasu lub wersji</span><span class="sxs-lookup"><span data-stu-id="f8539-102">How to: Represent Columns as Timestamp or Version Columns</span></span>
<span data-ttu-id="f8539-103">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Użyj<xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> właściwości atrybutu<xref:System.Data.Linq.Mapping.ColumnAttribute> , aby wyznaczyć pole lub właściwość w postaci kolumny bazy danych zawierającej sygnatury czasowe bazy danych lub numery wersji.</span><span class="sxs-lookup"><span data-stu-id="f8539-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property of the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a field or property as representing a database column that holds database timestamps or version numbers.</span></span>  
  
 <span data-ttu-id="f8539-104">Aby zapoznać się z przykładami kodu, zobacz <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span><span class="sxs-lookup"><span data-stu-id="f8539-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span></span>  
  
### <a name="to-designate-a-field-or-property-as-representing-a-timestamp-or-version-column"></a><span data-ttu-id="f8539-105">Aby wyznaczyć pole lub właściwość jako kolumnę sygnatury czasowej lub wersji</span><span class="sxs-lookup"><span data-stu-id="f8539-105">To designate a field or property as representing a timestamp or version column</span></span>  
  
1. <span data-ttu-id="f8539-106"><xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> Dodaj Właściwość<xref:System.Data.Linq.Mapping.ColumnAttribute> do atrybutu.</span><span class="sxs-lookup"><span data-stu-id="f8539-106">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="f8539-107">`true`Ustaw wartość <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> właściwości na.</span><span class="sxs-lookup"><span data-stu-id="f8539-107">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8539-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f8539-108">See also</span></span>

- [<span data-ttu-id="f8539-109">Model obiektu LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="f8539-109">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="f8539-110">Instrukcje: Określ, które składowe są testowane pod kątem konfliktów współbieżności</span><span class="sxs-lookup"><span data-stu-id="f8539-110">How to: Specify Which Members are Tested for Concurrency Conflicts</span></span>](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)
- [<span data-ttu-id="f8539-111">Instrukcje: Dostosowywanie klas jednostek przy użyciu edytora kodu</span><span class="sxs-lookup"><span data-stu-id="f8539-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
