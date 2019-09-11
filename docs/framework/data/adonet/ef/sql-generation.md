---
title: Generowanie kodu SQL
ms.date: 03/30/2017
ms.assetid: 0e16aa02-d458-4418-a765-58b42aad9315
ms.openlocfilehash: 9c5301d3f4d5bc2e0db4a138c6d8ceb06d3a7845
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854356"
---
# <a name="sql-generation"></a><span data-ttu-id="06dda-102">Generowanie kodu SQL</span><span class="sxs-lookup"><span data-stu-id="06dda-102">SQL Generation</span></span>
<span data-ttu-id="06dda-103">Podczas pisania dostawcy dla Entity Framework należy przetłumaczyć drzewa poleceń Entity Framework na SQL, które mogą zrozumieć konkretną bazę danych, na przykład Transact-SQL dla SQL Server lub PL/SQL dla firmy Oracle.</span><span class="sxs-lookup"><span data-stu-id="06dda-103">When you write a provider for the Entity Framework, you must translate Entity Framework command trees into SQL that a specific database can understand, such as Transact-SQL for SQL Server or PL/SQL for Oracle.</span></span> <span data-ttu-id="06dda-104">W tej sekcji dowiesz się, jak opracowywać składnik generacji SQL (dla wybranych zapytań) dla dostawcy Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="06dda-104">In this section, you will learn how to develop a SQL generation component (for SELECT queries) for an Entity Framework provider.</span></span> <span data-ttu-id="06dda-105">Aby uzyskać informacje na temat zapytań INSERT, Update i DELETE, zobacz [Modyfikowanie generacji SQL](modification-sql-generation.md).</span><span class="sxs-lookup"><span data-stu-id="06dda-105">For information about insert, update, and delete queries, see [Modification SQL Generation](modification-sql-generation.md).</span></span>  
  
 <span data-ttu-id="06dda-106">Aby zrozumieć tę sekcję, należy zapoznać się z Entity Framework i modelem dostawcy ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="06dda-106">To understand this section, you should be familiar with the Entity Framework and the ADO.NET Provider Model.</span></span> <span data-ttu-id="06dda-107">Należy również zrozumieć drzewa poleceń i <xref:System.Data.Common.CommandTrees.DbExpression>.</span><span class="sxs-lookup"><span data-stu-id="06dda-107">You should also understand command trees and <xref:System.Data.Common.CommandTrees.DbExpression>.</span></span>  
  
## <a name="the-role-of-the-sql-generation-module"></a><span data-ttu-id="06dda-108">Rola modułu generacji SQL</span><span class="sxs-lookup"><span data-stu-id="06dda-108">The Role of the SQL Generation Module</span></span>  
 <span data-ttu-id="06dda-109">Moduł generowania kodu SQL dostawcy Entity Framework tłumaczy określone drzewo poleceń zapytania na pojedynczą instrukcję SQL SELECT, która jest przeznaczona dla bazy danych zgodnej z programem SQL: 1999.</span><span class="sxs-lookup"><span data-stu-id="06dda-109">The SQL generation module of an Entity Framework provider translates a given query command tree into a single SQL SELECT statement that targets a SQL:1999-compliant database.</span></span> <span data-ttu-id="06dda-110">Wygenerowany kod SQL powinien zawierać co najmniej kilka zagnieżdżonych zapytań.</span><span class="sxs-lookup"><span data-stu-id="06dda-110">The generated SQL should have as few nested queries as possible.</span></span> <span data-ttu-id="06dda-111">Moduł generowania kodu SQL nie powinien uprościć drzewa poleceń kwerendy wyjściowej.</span><span class="sxs-lookup"><span data-stu-id="06dda-111">The SQL generation module should not simplify the output query command tree.</span></span> <span data-ttu-id="06dda-112">Entity Framework wykona to na przykład przez wyeliminowanie sprzężeń i zwijanie kolejnych węzłów filtru.</span><span class="sxs-lookup"><span data-stu-id="06dda-112">The Entity Framework will do this, for example by eliminating joins and collapsing consecutive filter nodes.</span></span>  
  
 <span data-ttu-id="06dda-113">Klasa jest punktem początkowym uzyskiwania dostępu do warstwy generowania kodu SQL w celu konwertowania drzew poleceń <xref:System.Data.Common.DbCommand>na. <xref:System.Data.Common.DbProviderServices></span><span class="sxs-lookup"><span data-stu-id="06dda-113">The <xref:System.Data.Common.DbProviderServices> class is the starting point for accessing the SQL generation layer to convert command trees into <xref:System.Data.Common.DbCommand>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="06dda-114">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="06dda-114">In This Section</span></span>  
 [<span data-ttu-id="06dda-115">Kształt drzew poleceń</span><span class="sxs-lookup"><span data-stu-id="06dda-115">The Shape of the Command Trees</span></span>](the-shape-of-the-command-trees.md)  
  
 [<span data-ttu-id="06dda-116">Generowanie kodu SQL na podstawie drzew poleceń — najlepsze praktyki</span><span class="sxs-lookup"><span data-stu-id="06dda-116">Generating SQL from Command Trees - Best Practices</span></span>](generating-sql-from-command-trees-best-practices.md)  
  
 [<span data-ttu-id="06dda-117">Generowanie kodu SQL w dostawcy próbki</span><span class="sxs-lookup"><span data-stu-id="06dda-117">SQL Generation in the Sample Provider</span></span>](sql-generation-in-the-sample-provider.md)  
  
## <a name="see-also"></a><span data-ttu-id="06dda-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="06dda-118">See also</span></span>

- [<span data-ttu-id="06dda-119">Pisanie dostawcy danych programu Entity Framework</span><span class="sxs-lookup"><span data-stu-id="06dda-119">Writing an Entity Framework Data Provider</span></span>](writing-an-ef-data-provider.md)
