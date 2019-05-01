---
title: LINQ to Objects (Visual Basic)
ms.date: 07/20/2015
ms.assetid: dd4c30bc-1c9b-4781-a482-b5eada38deb2
ms.openlocfilehash: c1e2e8fbaaf984fec69322a459fc7c55890965ad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791992"
---
# <a name="linq-to-objects-visual-basic"></a>LINQ to Objects (Visual Basic)
Termin "LINQ do obiektów" odnosi się do korzystania z LINQ zapytania ze wszystkimi <xref:System.Collections.IEnumerable> lub <xref:System.Collections.Generic.IEnumerable%601> kolekcji bezpośrednio, bez użycia pośrednie dostawcy LINQ lub interfejsu API, takie jak [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) lub [LINQ to XML](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md). LINQ umożliwia zapytania wszelkie przeliczalne kolekcje, takie jak <xref:System.Collections.Generic.List%601>, <xref:System.Array>, lub <xref:System.Collections.Generic.Dictionary%602>. Kolekcja może być zdefiniowana przez użytkownika lub mogą być zwrócone przez interfejs API programu .NET Framework.  
  
 W tym sensie podstawowe LINQ to Objects reprezentuje nowe podejście do kolekcji. W stary sposób było zapisać złożonych `For Each` pętli, które określa sposób pobierania danych z kolekcji. W przypadku zastosowania podejścia LINQ piszesz kod deklaratywny, opisujący, co ma zostać pobrane.  
  
 Ponadto zapytań LINQ oferuje trzy główne zalety w porównaniu z tradycyjnym `For Each` pętli:  
  
1. Są one bardziej zwięzły, czytelny, szczególnie w przypadku, gdy wiele warunków filtrowania.  
  
2. Zapewniają zaawansowane filtrowanie, porządkowanie i możliwości przy minimalnej ilości kodu aplikacji grupowania.  
  
3. Można ich przenieść do innych źródeł danych przy użyciu niewielkich modyfikacji.  
  
 Ogólnie rzecz biorąc, tym bardziej złożone operację, którą chcesz wykonać na danych, więcej korzyści będą weź pod uwagę przy użyciu LINQ zamiast iteracji tradycyjnych technik.  
  
 Ta sekcja ma na celu wykazania podejście LINQ z przykładami wybierz. Nie ma niepełna.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [LINQ i ciągi (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)  
 W tym artykule wyjaśniono, jak LINQ może służyć do wykonywania zapytań i przekształcanie ciągów i zbiorów ciągów. Zawiera także łącza do tematów, które pokazują tych zasad.  
  
 [LINQ i odbicie (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-reflection.md)  
 Zawiera łącza do przykładu, który demonstruje, jak LINQ używa odbicia.  
  
 [LINQ i katalogi plików (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)  
 W tym artykule wyjaśniono, jak LINQ może służyć do interakcji z systemami plików. Zawiera także łącza do tematów, które pokazują te pojęcia.  
  
 [Instrukcje: Zapytanie w ArrayList za pomocą LINQ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)  
 Pokazuje, jak zapytanie w ArrayList w języku C#.  
  
 [Instrukcje: Dodawanie metod niestandardowych do kwerend LINQ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-add-custom-methods-for-linq-queries.md)  
 Wyjaśnia, jak rozszerzyć zbiór metod, które służy do zapytań LINQ, dodając metody rozszerzenia umożliwiające <xref:System.Collections.Generic.IEnumerable%601> interfejsu.  
  
 [Zapytanie o języku zintegrowanym (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 Zawiera łącza do tematów, które wyjaśniają LINQ i podają przykłady kodu, wykonujących zapytania.
