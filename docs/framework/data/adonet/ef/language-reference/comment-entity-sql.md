---
title: --(Komentarz) (jednostka SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5d9de735-2099-47f1-b7e7-60856f494924
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1961542e615bbbd99bbc517bdd7d649be3f3ef07
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="---comment-entity-sql"></a><span data-ttu-id="d6236-102">--(Komentarz) (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="d6236-102">-- (Comment) (Entity SQL)</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="d6236-103">zapytania mogą zawierać komentarzy.</span><span class="sxs-lookup"><span data-stu-id="d6236-103"> queries can contain comments.</span></span> <span data-ttu-id="d6236-104">Dwa łączniki (`--`) uruchom wiersz komentarza.</span><span class="sxs-lookup"><span data-stu-id="d6236-104">Two dashes (`--`) start a comment line.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6236-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d6236-105">Syntax</span></span>  
  
```  
-- text_of_comment  
```  
  
## <a name="arguments"></a><span data-ttu-id="d6236-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="d6236-106">Arguments</span></span>  
 `text_of_comment`  
 <span data-ttu-id="d6236-107">Jest ciąg znaków, który zawiera tekst komentarza.</span><span class="sxs-lookup"><span data-stu-id="d6236-107">Is the character string that contains the text of the comment.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6236-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="d6236-108">Example</span></span>  
 <span data-ttu-id="d6236-109">Następujące zapytanie SQL jednostki przedstawiono sposób użycia komentarze.</span><span class="sxs-lookup"><span data-stu-id="d6236-109">The following Entity SQL query demonstrates how to use comments.</span></span> <span data-ttu-id="d6236-110">Kwerenda jest oparta na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="d6236-110">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="d6236-111">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="d6236-111">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="d6236-112">Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="d6236-112">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="d6236-113">Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="d6236-113">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#COMMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#comment)]  
  
## <a name="see-also"></a><span data-ttu-id="d6236-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d6236-114">See Also</span></span>  
 [<span data-ttu-id="d6236-115">Omówienie SQL jednostki</span><span class="sxs-lookup"><span data-stu-id="d6236-115">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [<span data-ttu-id="d6236-116">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="d6236-116">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
