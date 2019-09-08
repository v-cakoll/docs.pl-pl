---
title: 'Instrukcje: Określanie nazw bazy danych'
ms.date: 03/30/2017
ms.assetid: b80f0fd2-7f75-45fe-9e12-496f80f183df
ms.openlocfilehash: 0daf754edf624410e0ea725acd6c266ccb7828dc
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781576"
---
# <a name="how-to-specify-database-names"></a><span data-ttu-id="53d33-102">Instrukcje: Określanie nazw bazy danych</span><span class="sxs-lookup"><span data-stu-id="53d33-102">How to: Specify Database Names</span></span>
<span data-ttu-id="53d33-103"><xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> Użyj właściwości<xref:System.Data.Linq.Mapping.DatabaseAttribute> dla atrybutu, aby określić nazwę bazy danych, gdy nazwa nie jest dostarczana przez połączenie.</span><span class="sxs-lookup"><span data-stu-id="53d33-103">Use the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property on a <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute to specify the name of a database when a name is not supplied by the connection.</span></span>  
  
 <span data-ttu-id="53d33-104">Aby zapoznać się z przykładami kodu, zobacz <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span><span class="sxs-lookup"><span data-stu-id="53d33-104">For code samples, see <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span></span>  
  
### <a name="to-specify-the-name-of-the-database"></a><span data-ttu-id="53d33-105">Aby określić nazwę bazy danych</span><span class="sxs-lookup"><span data-stu-id="53d33-105">To specify the name of the database</span></span>  
  
1. <span data-ttu-id="53d33-106"><xref:System.Data.Linq.Mapping.DatabaseAttribute> Dodaj atrybut do deklaracji klasy dla bazy danych.</span><span class="sxs-lookup"><span data-stu-id="53d33-106">Add the <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute to the class declaration for the database.</span></span>  
  
2. <span data-ttu-id="53d33-107"><xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> Dodaj Właściwość<xref:System.Data.Linq.Mapping.DatabaseAttribute> do atrybutu.</span><span class="sxs-lookup"><span data-stu-id="53d33-107">Add the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property to the <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute.</span></span>  
  
3. <span data-ttu-id="53d33-108">Ustaw wartość <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> właściwości na nazwę, która ma zostać określona.</span><span class="sxs-lookup"><span data-stu-id="53d33-108">Set the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property value to the name that you want to specify.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53d33-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="53d33-109">See also</span></span>

- [<span data-ttu-id="53d33-110">Model obiektu LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="53d33-110">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="53d33-111">Instrukcje: Dostosowywanie klas jednostek przy użyciu edytora kodu</span><span class="sxs-lookup"><span data-stu-id="53d33-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
