---
title: Wyrażenie <type> nie umożliwia zadawania zapytań
ms.date: 07/20/2015
f1_keywords:
- bc36593
- vbc36593
helpviewer_keywords:
- BC36593
ms.assetid: 6f1f5860-bf97-4885-9ebb-bc87d028095c
ms.openlocfilehash: e61b4dac109f714b5cf25226d1029237ca77032d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409481"
---
# <a name="expression-of-type-type-is-not-queryable"></a><span data-ttu-id="b2e94-102">Wyrażenie \<type> nie umożliwia zadawania zapytań</span><span class="sxs-lookup"><span data-stu-id="b2e94-102">Expression of type \<type> is not queryable</span></span>
<span data-ttu-id="b2e94-103">Wyrażenie typu \<type> nie jest queryable.</span><span class="sxs-lookup"><span data-stu-id="b2e94-103">Expression of type \<type> is not queryable.</span></span> <span data-ttu-id="b2e94-104">Upewnij się, że nie brakuje importu odwołania do zestawu i/lub przestrzeni nazw dla dostawcy LINQ.</span><span class="sxs-lookup"><span data-stu-id="b2e94-104">Make sure you are not missing an assembly reference and/or namespace import for the LINQ provider.</span></span>  
  
 <span data-ttu-id="b2e94-105">Typy Queryable są zdefiniowane w <xref:System.Linq> <xref:System.Data.Linq> <xref:System.Xml.Linq> przestrzeniach nazw, i.</span><span class="sxs-lookup"><span data-stu-id="b2e94-105">Queryable types are defined in the <xref:System.Linq>, <xref:System.Data.Linq>, and <xref:System.Xml.Linq> namespaces.</span></span> <span data-ttu-id="b2e94-106">Aby wykonać zapytania LINQ, należy zaimportować co najmniej jedną z tych przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="b2e94-106">You must import one or more of these namespaces to perform LINQ queries.</span></span>  
  
 <span data-ttu-id="b2e94-107"><xref:System.Linq>Przestrzeń nazw umożliwia wykonywanie zapytań dotyczących obiektów, takich jak kolekcje i tablice, za pomocą LINQ.</span><span class="sxs-lookup"><span data-stu-id="b2e94-107">The <xref:System.Linq> namespace enables you to query objects such as collections and arrays by using LINQ.</span></span>  
  
 <span data-ttu-id="b2e94-108"><xref:System.Data.Linq>Przestrzeń nazw umożliwia wykonywanie zapytań dotyczących zestawów danych ADO.NET i baz SQL Server przy użyciu LINQ.</span><span class="sxs-lookup"><span data-stu-id="b2e94-108">The <xref:System.Data.Linq> namespace enables you to query ADO.NET Datasets and SQL Server databases by using LINQ.</span></span>  
  
 <span data-ttu-id="b2e94-109"><xref:System.Xml.Linq>Przestrzeń nazw umożliwia wykonywanie zapytań XML przy użyciu LINQ i używanie funkcji XML w Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b2e94-109">The <xref:System.Xml.Linq> namespace enables you to query XML by using LINQ and to use XML features in Visual Basic.</span></span>  
  
 <span data-ttu-id="b2e94-110">**Identyfikator błędu:** BC36593</span><span class="sxs-lookup"><span data-stu-id="b2e94-110">**Error ID:** BC36593</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b2e94-111">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="b2e94-111">To correct this error</span></span>  
  
1. <span data-ttu-id="b2e94-112">Dodaj `Import` instrukcję dla <xref:System.Linq> <xref:System.Data.Linq> przestrzeni nazw,, lub <xref:System.Xml.Linq> do pliku z kodem.</span><span class="sxs-lookup"><span data-stu-id="b2e94-112">Add an `Import` statement for the <xref:System.Linq>, <xref:System.Data.Linq>, or <xref:System.Xml.Linq> namespace to your code file.</span></span> <span data-ttu-id="b2e94-113">Możesz również zaimportować przestrzenie nazw dla projektu przy użyciu strony **odwołania** projektanta projektu (**mój projekt**).</span><span class="sxs-lookup"><span data-stu-id="b2e94-113">You can also import namespaces for your project by using the **References** page of the Project Designer (**My Project**).</span></span>  
  
2. <span data-ttu-id="b2e94-114">Upewnij się, że typ, który został zidentyfikowany jako źródło zapytania, jest typem queryable.</span><span class="sxs-lookup"><span data-stu-id="b2e94-114">Ensure that the type that you have identified as the source of your query is a queryable type.</span></span> <span data-ttu-id="b2e94-115">Oznacza to, że typ, który implementuje <xref:System.Collections.Generic.IEnumerable%601> lub <xref:System.Linq.IQueryable%601> .</span><span class="sxs-lookup"><span data-stu-id="b2e94-115">That is, a type that implements <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2e94-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b2e94-116">See also</span></span>

- <xref:System.Linq>
- <xref:System.Data.Linq>
- <xref:System.Xml.Linq>
- [<span data-ttu-id="b2e94-117">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b2e94-117">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="b2e94-118">LINQ</span><span class="sxs-lookup"><span data-stu-id="b2e94-118">LINQ</span></span>](../../programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="b2e94-119">XML</span><span class="sxs-lookup"><span data-stu-id="b2e94-119">XML</span></span>](../../programming-guide/language-features/xml/index.md)
- [<span data-ttu-id="b2e94-120">Referencje i instrukcja Imports</span><span class="sxs-lookup"><span data-stu-id="b2e94-120">References and the Imports Statement</span></span>](../../programming-guide/program-structure/references-and-the-imports-statement.md)
- [<span data-ttu-id="b2e94-121">Imports — Instrukcja (.NET Namespace i Type)</span><span class="sxs-lookup"><span data-stu-id="b2e94-121">Imports Statement (.NET Namespace and Type)</span></span>](../statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="b2e94-122">Strona odwołań, Projektant projektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b2e94-122">References Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/references-page-project-designer-visual-basic)
