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
# <a name="expression-of-type-lttypegt-is-not-queryable"></a>Wyrażenie typu &lt;typu&gt; nie jest zapytań
Wyrażenie typu \<typu > nie jest obsługą zapytań. Upewnij się, że nie brakuje zestawu importu odwołania i/lub przestrzeń nazw dla dostawcy LINQ.  
  
 Typy zapytań są definiowane w <xref:System.Linq>, <xref:System.Data.Linq>, i <xref:System.Xml.Linq> przestrzeni nazw. Należy zaimportować co najmniej jednego z tych obszarów nazw do wykonywania zapytań LINQ.  
  
 <xref:System.Linq> Przestrzeni nazw umożliwia utworzenie zapytania obiektów, takich jak kolekcje i tablic za pomocą LINQ.  
  
 <xref:System.Data.Linq> Przestrzeni nazw umożliwia zapytania danych ADO.NET i baz danych programu SQL Server za pomocą LINQ.  
  
 <xref:System.Xml.Linq> Przestrzeni nazw umożliwia utworzenie zapytania XML za pomocą LINQ i używać funkcji XML w Visual Basic.  
  
 **Identyfikator błędu:** BC36593  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Dodaj `Import` instrukcji dla <xref:System.Linq>, <xref:System.Data.Linq>, lub <xref:System.Xml.Linq> przestrzeni nazw do pliku kodu. Możesz również zaimportować przestrzeni nazw w projekcie, za pomocą **odwołania** strony projektanta projektu (**mój projekt**).  
  
2.  Upewnij się, że typ, który zidentyfikowano jako źródło zapytania jest typu zapytań. Oznacza to, typu, który implementuje <xref:System.Collections.Generic.IEnumerable%601> lub <xref:System.Linq.IQueryable%601>.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Linq>  
 <xref:System.Data.Linq>  
 <xref:System.Xml.Linq>  
 [Wprowadzenie do LINQ w Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [LINQ](../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [Referencje i Importy — instrukcja](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 [Imports — instrukcja (.NET Namespace i Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [Strona odwołań, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic)
