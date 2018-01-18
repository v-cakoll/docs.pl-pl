---
title: "Semantyka wartości null"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a97017ae-d634-4cf3-bbaf-054a528fd683
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 8d32f73c8c2095c23ec164ad40fd1ab27ef1153a
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="null-semantics"></a><span data-ttu-id="3bac1-102">Semantyka wartości null</span><span class="sxs-lookup"><span data-stu-id="3bac1-102">Null Semantics</span></span>
<span data-ttu-id="3bac1-103">Poniższa tabela zawiera linki do różnych części [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dokumentacji gdzie `null` (`Nothing` w [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) opisano problemy.</span><span class="sxs-lookup"><span data-stu-id="3bac1-103">The following table provides links to various parts of the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation where `null` (`Nothing` in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) issues are discussed.</span></span>  
  
|<span data-ttu-id="3bac1-104">Temat</span><span class="sxs-lookup"><span data-stu-id="3bac1-104">Topic</span></span>|<span data-ttu-id="3bac1-105">Opis</span><span class="sxs-lookup"><span data-stu-id="3bac1-105">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="3bac1-106">Niezgodność typu SQL CLR</span><span class="sxs-lookup"><span data-stu-id="3bac1-106">SQL-CLR Type Mismatches</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mismatches.md)|<span data-ttu-id="3bac1-107">Sekcja "Wartości Null semantyki" tego tematu zawiera omówienie trójstanowy SQL Boolean lub dwustanowy środowisko uruchomieniowe języka wspólnego (CLR) <xref:System.Boolean>, literał `Nothing` ([!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) i `null` (C#) i inne podobne zagadnienia.</span><span class="sxs-lookup"><span data-stu-id="3bac1-107">The "Null Semantics" section of this topic includes discussion of the three-state SQL Boolean versus the two-state common language runtime (CLR) <xref:System.Boolean>, the literal `Nothing` ([!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) and `null` (C#), and other similar issues.</span></span>|  
|[<span data-ttu-id="3bac1-108">Translacja standardowego operatora zapytania</span><span class="sxs-lookup"><span data-stu-id="3bac1-108">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)|<span data-ttu-id="3bac1-109">W sekcji "Semantyki Null" w tym temacie opisano semantykę porównania wartości null w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3bac1-109">The "Null Semantics" section of this topic describes null comparison semantics in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>|  
|[<span data-ttu-id="3bac1-110">Metody System.String</span><span class="sxs-lookup"><span data-stu-id="3bac1-110">System.String Methods</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/system-string-methods.md)|<span data-ttu-id="3bac1-111">W sekcji "Różnice z .NET" w tym temacie opisano, jak typ zwracany 0 z <xref:System.String.LastIndexOf%2A> może oznaczać, że ciąg ma wartość null albo czy znaleziono pozycji jest 0.</span><span class="sxs-lookup"><span data-stu-id="3bac1-111">The "Differences from .NET" section of this topic describes how a return of 0 from <xref:System.String.LastIndexOf%2A> might mean either that the string is null or that the found position is 0.</span></span>|  
|[<span data-ttu-id="3bac1-112">Obliczanie sumy wartości w sekwencji numerycznej</span><span class="sxs-lookup"><span data-stu-id="3bac1-112">Compute the Sum of Values in a Numeric Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/compute-the-sum-of-values-in-a-numeric-sequence.md)|<span data-ttu-id="3bac1-113">Opisuje sposób <xref:System.Linq.Enumerable.Sum%2A> operatora daje w wyniku `null` (`Nothing` w [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) zamiast 0 dla sekwencji, który zawiera tylko wartości null lub pustej sekwencji.</span><span class="sxs-lookup"><span data-stu-id="3bac1-113">Describes how the <xref:System.Linq.Enumerable.Sum%2A> operator evaluates to `null` (`Nothing` in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) instead of 0 for a sequence that contains only nulls or for an empty sequence.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3bac1-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3bac1-114">See Also</span></span>  
 [<span data-ttu-id="3bac1-115">Typy danych i funkcje</span><span class="sxs-lookup"><span data-stu-id="3bac1-115">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
