---
title: Wyrażenie <type> nie umożliwia zadawania zapytań
ms.date: 07/20/2015
f1_keywords:
- bc36593
- vbc36593
helpviewer_keywords:
- BC36593
ms.assetid: 6f1f5860-bf97-4885-9ebb-bc87d028095c
ms.openlocfilehash: 7f74d56b47629ff76f9b935d26278ace8df4c353
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842333"
---
# <a name="expression-of-type-type-is-not-queryable"></a>Wyrażenie typu \<typ > nie umożliwia zadawania zapytań
Wyrażenie typu \<typ > nie umożliwia zadawania zapytań. Upewnij się, że nie brakuje importu zestawu odwołania i/lub przestrzeń nazw dla dostawcy LINQ.  
  
 Typami odpytywalnymi są zdefiniowane w <xref:System.Linq>, <xref:System.Data.Linq>, i <xref:System.Xml.Linq> przestrzeni nazw. Należy zaimportować co najmniej jedną z tych obszarów nazw, aby wykonać zapytania LINQ.  
  
 <xref:System.Linq> Przestrzeni nazw pozwala przesyłać zapytania obiektów, takich jak kolekcje i tablice za pomocą LINQ.  
  
 <xref:System.Data.Linq> Przestrzeń nazw umożliwia zapytania z zestawami danych ADO.NET i baz danych programu SQL Server za pomocą LINQ.  
  
 <xref:System.Xml.Linq> Przestrzeni nazw pozwala przesyłać zapytania XML za pomocą LINQ i korzystanie z funkcji XML w Visual Basic.  
  
 **Identyfikator błędu:** BC36593  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Dodaj `Import` poufności informacji dotyczące <xref:System.Linq>, <xref:System.Data.Linq>, lub <xref:System.Xml.Linq> przestrzeni nazw do pliku kodu. Możesz również zaimportować przestrzeni nazw dla projektu, przy użyciu **odwołania** strony Projektant projektu (**mój projekt**).  
  
2.  Upewnij się, że typ, który masz zidentyfikowane jako źródła zapytania jest typem odpytywalnym. Oznacza to, że typ, który implementuje <xref:System.Collections.Generic.IEnumerable%601> lub <xref:System.Linq.IQueryable%601>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Linq>
- <xref:System.Data.Linq>
- <xref:System.Xml.Linq>
- [Wprowadzenie do LINQ w Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [LINQ](../../../visual-basic/programming-guide/language-features/linq/index.md)
- [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)
- [Referencje i instrukcja Imports](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)
- [Imports, instrukcja (przestrzeń nazw i typ .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [Strona odwołań, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic)
