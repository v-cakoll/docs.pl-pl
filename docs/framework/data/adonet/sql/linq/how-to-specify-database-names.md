---
title: 'Instrukcje: Określanie nazw bazy danych'
ms.date: 03/30/2017
ms.assetid: b80f0fd2-7f75-45fe-9e12-496f80f183df
ms.openlocfilehash: a43a7ac541adb984eeb8bb88b7ab96db86baf26c
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59335280"
---
# <a name="how-to-specify-database-names"></a><span data-ttu-id="a11f0-102">Instrukcje: Określanie nazw bazy danych</span><span class="sxs-lookup"><span data-stu-id="a11f0-102">How to: Specify Database Names</span></span>
<span data-ttu-id="a11f0-103">Użyj <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> właściwość <xref:System.Data.Linq.Mapping.DatabaseAttribute> atrybutu, aby określić nazwę bazy danych, jeśli nie podano nazwy przez połączenie.</span><span class="sxs-lookup"><span data-stu-id="a11f0-103">Use the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property on a <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute to specify the name of a database when a name is not supplied by the connection.</span></span>  
  
 <span data-ttu-id="a11f0-104">Aby uzyskać przykłady kodu, zobacz <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span><span class="sxs-lookup"><span data-stu-id="a11f0-104">For code samples, see <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span></span>  
  
### <a name="to-specify-the-name-of-the-database"></a><span data-ttu-id="a11f0-105">Aby określić nazwę bazy danych</span><span class="sxs-lookup"><span data-stu-id="a11f0-105">To specify the name of the database</span></span>  
  
1. <span data-ttu-id="a11f0-106">Dodaj <xref:System.Data.Linq.Mapping.DatabaseAttribute> atrybutu deklaracji klasy dla bazy danych.</span><span class="sxs-lookup"><span data-stu-id="a11f0-106">Add the <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute to the class declaration for the database.</span></span>  
  
2. <span data-ttu-id="a11f0-107">Dodaj <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> właściwość <xref:System.Data.Linq.Mapping.DatabaseAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="a11f0-107">Add the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property to the <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute.</span></span>  
  
3. <span data-ttu-id="a11f0-108">Ustaw <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> wartości właściwości, aby określić nazwę.</span><span class="sxs-lookup"><span data-stu-id="a11f0-108">Set the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property value to the name that you want to specify.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a11f0-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a11f0-109">See also</span></span>

- [<span data-ttu-id="a11f0-110">Model obiektu LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="a11f0-110">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="a11f0-111">Instrukcje: Dostosowywanie klas jednostek za pomocą edytora kodu</span><span class="sxs-lookup"><span data-stu-id="a11f0-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
