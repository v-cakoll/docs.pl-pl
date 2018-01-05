---
title: Generowanie kodu SQL
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e16aa02-d458-4418-a765-58b42aad9315
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 7c0f0b8734de219208cba3caf0220d1e9436a3c8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="sql-generation"></a><span data-ttu-id="ba5ca-102">Generowanie kodu SQL</span><span class="sxs-lookup"><span data-stu-id="ba5ca-102">SQL Generation</span></span>
<span data-ttu-id="ba5ca-103">Podczas zapisu dostawcę dla [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], muszą tłumaczyć [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] polecenia drzew SQL, który można zrozumieć określonej bazy danych, takich jak języka Transact-SQL dla programu SQL Server lub PL/SQL dla programu Oracle.</span><span class="sxs-lookup"><span data-stu-id="ba5ca-103">When you write a provider for the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], you must translate [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] command trees into SQL that a specific database can understand, such as Transact-SQL for SQL Server or PL/SQL for Oracle.</span></span> <span data-ttu-id="ba5ca-104">W tej sekcji przedstawiono tworzenia składnik generowania SQL (do kwerend WYBIERAJĄCYCH) dla [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] dostawcy.</span><span class="sxs-lookup"><span data-stu-id="ba5ca-104">In this section, you will learn how to develop a SQL generation component (for SELECT queries) for an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provider.</span></span> <span data-ttu-id="ba5ca-105">Informacje o wstawiania, aktualizacji i usunąć zapytania, zobacz [generowanie kodu SQL modyfikacji](../../../../../docs/framework/data/adonet/ef/modification-sql-generation.md).</span><span class="sxs-lookup"><span data-stu-id="ba5ca-105">For information about insert, update, and delete queries, see [Modification SQL Generation](../../../../../docs/framework/data/adonet/ef/modification-sql-generation.md).</span></span>  
  
 <span data-ttu-id="ba5ca-106">Aby poznać tę sekcję, należy się zapoznać z [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] i Model dostawcy ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="ba5ca-106">To understand this section, you should be familiar with the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] and the ADO.NET Provider Model.</span></span> <span data-ttu-id="ba5ca-107">Należy również poznać drzew poleceń i <xref:System.Data.Common.CommandTrees.DbExpression>.</span><span class="sxs-lookup"><span data-stu-id="ba5ca-107">You should also understand command trees and <xref:System.Data.Common.CommandTrees.DbExpression>.</span></span>  
  
## <a name="the-role-of-the-sql-generation-module"></a><span data-ttu-id="ba5ca-108">Rola modułu generowania SQL</span><span class="sxs-lookup"><span data-stu-id="ba5ca-108">The Role of the SQL Generation Module</span></span>  
 <span data-ttu-id="ba5ca-109">Moduł generowania SQL z [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] dostawcy przekształca poziomu drzewa poleceń określonego zapytania w jednej instrukcji SQL SELECT, przeznaczonego dla SQL:1999-zgodny z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="ba5ca-109">The SQL generation module of an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provider translates a given query command tree into a single SQL SELECT statement that targets a SQL:1999-compliant database.</span></span> <span data-ttu-id="ba5ca-110">Wygenerowany SQL powinien mieć jako kilka zagnieżdżonych zapytania jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="ba5ca-110">The generated SQL should have as few nested queries as possible.</span></span> <span data-ttu-id="ba5ca-111">Moduł generowania SQL nie należy uprościć drzewa poleceń zapytania danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="ba5ca-111">The SQL generation module should not simplify the output query command tree.</span></span> <span data-ttu-id="ba5ca-112">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Będzie to zrobić, na przykład przez wyeliminowanie sprzężenia i zwijanie węzły kolejnych filtru.</span><span class="sxs-lookup"><span data-stu-id="ba5ca-112">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] will do this, for example by eliminating joins and collapsing consecutive filter nodes.</span></span>  
  
 <span data-ttu-id="ba5ca-113"><xref:System.Data.Common.DbProviderServices> Klasy jest punkt początkowy do uzyskiwania dostępu do warstwy generowania SQL można przekonwertować drzew poleceń w <xref:System.Data.Common.DbCommand>.</span><span class="sxs-lookup"><span data-stu-id="ba5ca-113">The <xref:System.Data.Common.DbProviderServices> class is the starting point for accessing the SQL generation layer to convert command trees into <xref:System.Data.Common.DbCommand>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ba5ca-114">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="ba5ca-114">In This Section</span></span>  
 [<span data-ttu-id="ba5ca-115">Kształt drzew poleceń</span><span class="sxs-lookup"><span data-stu-id="ba5ca-115">The Shape of the Command Trees</span></span>](../../../../../docs/framework/data/adonet/ef/the-shape-of-the-command-trees.md)  
  
 [<span data-ttu-id="ba5ca-116">Generowanie kodu SQL na podstawie drzew poleceń — najlepsze praktyki</span><span class="sxs-lookup"><span data-stu-id="ba5ca-116">Generating SQL from Command Trees - Best Practices</span></span>](../../../../../docs/framework/data/adonet/ef/generating-sql-from-command-trees-best-practices.md)  
  
 [<span data-ttu-id="ba5ca-117">Generowanie kodu SQL w dostawcy próbki</span><span class="sxs-lookup"><span data-stu-id="ba5ca-117">SQL Generation in the Sample Provider</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation-in-the-sample-provider.md)  
  
## <a name="see-also"></a><span data-ttu-id="ba5ca-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ba5ca-118">See Also</span></span>  
 [<span data-ttu-id="ba5ca-119">Pisanie dostawcy danych programu Entity Framework</span><span class="sxs-lookup"><span data-stu-id="ba5ca-119">Writing an Entity Framework Data Provider</span></span>](../../../../../docs/framework/data/adonet/ef/writing-an-ef-data-provider.md)
