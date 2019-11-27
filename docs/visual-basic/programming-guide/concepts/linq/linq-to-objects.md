---
title: LINQ do obiektów
ms.date: 07/20/2015
ms.assetid: dd4c30bc-1c9b-4781-a482-b5eada38deb2
ms.openlocfilehash: ef7d6fe232a788ab77661e9c5f313a80df4779b5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354304"
---
# <a name="linq-to-objects-visual-basic"></a>LINQ to Objects (Visual Basic)
Termin "LINQ to Objects" odnosi się do używania zapytań LINQ z dowolnymi <xref:System.Collections.IEnumerable> lub <xref:System.Collections.Generic.IEnumerable%601> kolekcji bezpośrednio, bez użycia pośredniego dostawcy LINQ lub interfejsu API, takiego jak [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) lub [LINQ to XML](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md). Za pomocą LINQ można badać wszystkie wyliczalne kolekcje, takie jak <xref:System.Collections.Generic.List%601>, <xref:System.Array>lub <xref:System.Collections.Generic.Dictionary%602>. Kolekcja może być zdefiniowana przez użytkownika lub może być zwrócona przez interfejs API .NET Framework.  
  
 W podstawowym sensie LINQ to Objects reprezentuje nowe podejście do kolekcji. W stary sposób należy napisać złożone pętle `For Each`, które określają sposób pobierania danych z kolekcji. W podejściu LINQ napiszesz kod deklaratywny opisujący, co chcesz pobrać.  
  
 Ponadto zapytania LINQ oferują trzy główne zalety w porównaniu z tradycyjnymi pętlami `For Each`:  
  
1. Są one bardziej zwięzłe i czytelne, szczególnie w przypadku filtrowania wielu warunków.  
  
2. Zapewniają one zaawansowane możliwości filtrowania, porządkowania i grupowania przy minimalnym kodzie aplikacji.  
  
3. Można je przenieść do innych źródeł danych z niewielką lub bez modyfikacji.  
  
 Ogólnie rzecz biorąc, bardziej złożone operacje, które mają być wykonywane na danych, tym większe korzyści, które można wykorzystać przy użyciu LINQ zamiast tradycyjnych technik iteracji.  
  
 Celem tej sekcji jest zademonstrowanie podejścia LINQ z pewnymi przykładami. Nie jest to wyczerpujące.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [LINQ i ciągi (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)  
 Wyjaśnia, w jaki sposób LINQ może służyć do wykonywania zapytań i przekształcania ciągów i kolekcji ciągów. Zawiera również linki do tematów demonstrujących te zasady.  
  
 [LINQ i odbicie (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-reflection.md)  
 Linki do przykładu, który pokazuje, jak LINQ używa odbicia.  
  
 [LINQ i katalogi plików (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)  
 Wyjaśnia, w jaki sposób LINQ może służyć do współdziałania z systemami plików. Zawiera również linki do tematów, które przedstawiają te koncepcje.  
  
 [Instrukcje: wykonywanie zapytań do ArrayList za pomocą LINQ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)  
 Pokazuje, jak zbadać ArrayList w C#.  
  
 [Instrukcje: dodawanie metod niestandardowych dla zapytań LINQ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-add-custom-methods-for-linq-queries.md)  
 Wyjaśnia, w jaki sposób rozszerzać zestaw metod, których można użyć dla zapytań LINQ przez dodanie metod rozszerzenia do interfejsu <xref:System.Collections.Generic.IEnumerable%601>.  
  
 [Zapytanie zintegrowane z językiem (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 Zawiera łącza do tematów, które wyjaśniają LINQ i dostarczają przykłady kodu, który wykonuje zapytania.
