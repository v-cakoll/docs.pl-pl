---
title: "Wyrażenie typu &lt;typu&gt; nie jest zapytań"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36593
- vbc36593
helpviewer_keywords: BC36593
ms.assetid: 6f1f5860-bf97-4885-9ebb-bc87d028095c
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3f2b98bf48f0b3965929f9211c2944ff97754f23
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="expression-of-type-lttypegt-is-not-queryable"></a><span data-ttu-id="338e4-102">Wyrażenie typu &lt;typu&gt; nie jest zapytań</span><span class="sxs-lookup"><span data-stu-id="338e4-102">Expression of type &lt;type&gt; is not queryable</span></span>
<span data-ttu-id="338e4-103">Wyrażenie typu \<typu > nie jest obsługą zapytań.</span><span class="sxs-lookup"><span data-stu-id="338e4-103">Expression of type \<type> is not queryable.</span></span> <span data-ttu-id="338e4-104">Upewnij się, że nie brakuje zestawu importu odwołania i/lub przestrzeń nazw dla dostawcy LINQ.</span><span class="sxs-lookup"><span data-stu-id="338e4-104">Make sure you are not missing an assembly reference and/or namespace import for the LINQ provider.</span></span>  
  
 <span data-ttu-id="338e4-105">Typy zapytań są definiowane w <xref:System.Linq>, <xref:System.Data.Linq>, i <xref:System.Xml.Linq> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="338e4-105">Queryable types are defined in the <xref:System.Linq>, <xref:System.Data.Linq>, and <xref:System.Xml.Linq> namespaces.</span></span> <span data-ttu-id="338e4-106">Należy zaimportować co najmniej jednego z tych obszarów nazw do wykonywania zapytań LINQ.</span><span class="sxs-lookup"><span data-stu-id="338e4-106">You must import one or more of these namespaces to perform LINQ queries.</span></span>  
  
 <span data-ttu-id="338e4-107"><xref:System.Linq> Przestrzeni nazw umożliwia utworzenie zapytania obiektów, takich jak kolekcje i tablic za pomocą LINQ.</span><span class="sxs-lookup"><span data-stu-id="338e4-107">The <xref:System.Linq> namespace enables you to query objects such as collections and arrays by using LINQ.</span></span>  
  
 <span data-ttu-id="338e4-108"><xref:System.Data.Linq> Przestrzeni nazw umożliwia zapytania danych ADO.NET i baz danych programu SQL Server za pomocą LINQ.</span><span class="sxs-lookup"><span data-stu-id="338e4-108">The <xref:System.Data.Linq> namespace enables you to query ADO.NET Datasets and SQL Server databases by using LINQ.</span></span>  
  
 <span data-ttu-id="338e4-109"><xref:System.Xml.Linq> Przestrzeni nazw umożliwia utworzenie zapytania XML za pomocą LINQ i używać funkcji XML w Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="338e4-109">The <xref:System.Xml.Linq> namespace enables you to query XML by using LINQ and to use XML features in Visual Basic.</span></span>  
  
 <span data-ttu-id="338e4-110">**Identyfikator błędu:** BC36593</span><span class="sxs-lookup"><span data-stu-id="338e4-110">**Error ID:** BC36593</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="338e4-111">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="338e4-111">To correct this error</span></span>  
  
1.  <span data-ttu-id="338e4-112">Dodaj `Import` instrukcji dla <xref:System.Linq>, <xref:System.Data.Linq>, lub <xref:System.Xml.Linq> przestrzeni nazw do pliku kodu.</span><span class="sxs-lookup"><span data-stu-id="338e4-112">Add an `Import` statement for the <xref:System.Linq>, <xref:System.Data.Linq>, or <xref:System.Xml.Linq> namespace to your code file.</span></span> <span data-ttu-id="338e4-113">Możesz również zaimportować przestrzeni nazw w projekcie, za pomocą **odwołania** strony projektanta projektu (**mój projekt**).</span><span class="sxs-lookup"><span data-stu-id="338e4-113">You can also import namespaces for your project by using the **References** page of the Project Designer (**My Project**).</span></span>  
  
2.  <span data-ttu-id="338e4-114">Upewnij się, że typ, który zidentyfikowano jako źródło zapytania jest typu zapytań.</span><span class="sxs-lookup"><span data-stu-id="338e4-114">Ensure that the type that you have identified as the source of your query is a queryable type.</span></span> <span data-ttu-id="338e4-115">Oznacza to, typu, który implementuje <xref:System.Collections.Generic.IEnumerable%601> lub <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="338e4-115">That is, a type that implements <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="338e4-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="338e4-116">See Also</span></span>  
 <xref:System.Linq>  
 <xref:System.Data.Linq>  
 <xref:System.Xml.Linq>  
 [<span data-ttu-id="338e4-117">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="338e4-117">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="338e4-118">LINQ</span><span class="sxs-lookup"><span data-stu-id="338e4-118">LINQ</span></span>](../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="338e4-119">XML</span><span class="sxs-lookup"><span data-stu-id="338e4-119">XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [<span data-ttu-id="338e4-120">Referencje i Importy — instrukcja</span><span class="sxs-lookup"><span data-stu-id="338e4-120">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 [<span data-ttu-id="338e4-121">Imports — instrukcja (.NET Namespace i Type)</span><span class="sxs-lookup"><span data-stu-id="338e4-121">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [<span data-ttu-id="338e4-122">Strona odwołań, Projektant projektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="338e4-122">References Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/references-page-project-designer-visual-basic)
