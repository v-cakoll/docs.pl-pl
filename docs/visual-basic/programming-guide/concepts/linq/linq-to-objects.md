---
title: LINQ do obiektów (Visual Basic)
ms.date: 07/20/2015
ms.assetid: dd4c30bc-1c9b-4781-a482-b5eada38deb2
ms.openlocfilehash: f04ccc3d8541c1d4327ff9356fe7c4105681bd0f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33645309"
---
# <a name="linq-to-objects-visual-basic"></a>LINQ do obiektów (Visual Basic)
Termin "LINQ do obiektów" odwołuje się do korzystania z LINQ zapytania ze wszystkimi <xref:System.Collections.IEnumerable> lub <xref:System.Collections.Generic.IEnumerable%601> kolekcji bezpośrednio, bez użycia pośredniego dostawcy LINQ lub interfejsu API, takich jak [LINQ do SQL](../../../../framework/data/adonet/sql/linq/index.md) lub [LINQ do XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13). Użyj rozszerzenia LINQ, takich jak zbadać wszystkie kolekcje wyliczalny <xref:System.Collections.Generic.List%601>, <xref:System.Array>, lub <xref:System.Collections.Generic.Dictionary%602>. Kolekcja może być zdefiniowana przez użytkownika lub mogą być zwrócone przez interfejs API programu .NET Framework.  
  
 W tym sensie podstawowe LINQ do obiektów reprezentuje nowe podejście do kolekcji. W ten sposób stare, trzeba było zapisać złożonych `For Each` pętle określonych sposobu pobierania danych z kolekcji. W ujęciu LINQ pisania deklaratywne kod, który opisuje ma zostać pobrane.  
  
 Ponadto zapytań LINQ oferuje trzy główne zalet w porównaniu z tradycyjnym `For Each` pętle:  
  
1.  Są one bardziej zwięzłe i do odczytu, szczególnie, gdy wiele warunków filtrowania.  
  
2.  Udostępniają zaawansowane filtrowanie, kolejność i grupowanie możliwości z co najmniej kodu aplikacji.  
  
3.  Mogą one być przenoszone do innych źródeł danych z żadnych modyfikacji.  
  
 W ogólności, tym bardziej złożone operację należy wykonać na danych, więcej korzyści będzie realizować za pomocą LINQ zamiast metod tradycyjnych iteracji.  
  
 Ta sekcja ma na celu pokazują podejście LINQ z przykładami select. Nie ma niepełna.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [LINQ i ciągi (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)  
 Wyjaśniono, jak LINQ może służyć do wykonywania zapytań i przekształcanie ciągów i kolekcji ciągów. Zawiera również linki do tematów, które przedstawiają tych zasad.  
  
 [LINQ i odbicie (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-reflection.md)  
 Łącza na przykład, który demonstruje sposób LINQ używa odbicia.  
  
 [LINQ i katalogi plików (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)  
 Wyjaśniono, jak LINQ może służyć do interakcji z systemów plików. Zawiera również linki do tematów, które przedstawiają te pojęcia.  
  
 [Porady: zapytanie w ArrayList za pomocą LINQ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)  
 Demonstracja zapytanie w ArrayList w języku C#.  
  
 [Porady: dodawanie metod niestandardowych do kwerend LINQ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-add-custom-methods-for-linq-queries.md)  
 Wyjaśniono, jak rozszerzyć zestaw metod, których można używać do kwerend LINQ przez dodanie metody rozszerzenia umożliwiające <xref:System.Collections.Generic.IEnumerable%601> interfejsu.  
  
 [Zapytanie o języku zintegrowanym (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 Zawiera łącza do tematów, w których opisano LINQ i zawierają przykłady kodu, które wykonywania zapytań.
