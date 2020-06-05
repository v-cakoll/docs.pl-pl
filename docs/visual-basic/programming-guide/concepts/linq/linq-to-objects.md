---
title: LINQ do obiektów
ms.date: 07/20/2015
ms.assetid: dd4c30bc-1c9b-4781-a482-b5eada38deb2
ms.openlocfilehash: 1dca449f12c312fd395be56ebcb426c3a63b64d0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84369066"
---
# <a name="linq-to-objects-visual-basic"></a>LINQ to Objects (Visual Basic)
Termin "LINQ to Objects" odnosi się do użycia zapytań LINQ z dowolnym <xref:System.Collections.IEnumerable> lub <xref:System.Collections.Generic.IEnumerable%601> kolekcją bezpośrednio, bez użycia pośredniego dostawcy LINQ lub interfejsu API, takiego jak [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) lub [LINQ to XML](linq-to-xml.md). Za pomocą LINQ można badać wszystkie wyliczalne kolekcje, takie jak <xref:System.Collections.Generic.List%601> , <xref:System.Array> lub <xref:System.Collections.Generic.Dictionary%602> . Kolekcja może być zdefiniowana przez użytkownika lub może być zwrócona przez interfejs API .NET Framework.  
  
 W podstawowym sensie LINQ to Objects reprezentuje nowe podejście do kolekcji. W stary sposób należy napisać złożone `For Each` pętle, które określają sposób pobierania danych z kolekcji. W podejściu LINQ napiszesz kod deklaratywny opisujący, co chcesz pobrać.  
  
 Ponadto zapytania LINQ oferują trzy główne zalety przed tradycyjnymi `For Each` pętlami:  
  
1. Są one bardziej zwięzłe i czytelne, szczególnie w przypadku filtrowania wielu warunków.  
  
2. Zapewniają one zaawansowane możliwości filtrowania, porządkowania i grupowania przy minimalnym kodzie aplikacji.  
  
3. Można je przenieść do innych źródeł danych z niewielką lub bez modyfikacji.  
  
 Ogólnie rzecz biorąc, bardziej złożone operacje, które mają być wykonywane na danych, tym większe korzyści, które można wykorzystać przy użyciu LINQ zamiast tradycyjnych technik iteracji.  
  
 Celem tej sekcji jest zademonstrowanie podejścia LINQ z pewnymi przykładami. Nie jest to wyczerpujące.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [LINQ i ciągi (Visual Basic)](linq-and-strings.md)  
 Wyjaśnia, w jaki sposób LINQ może służyć do wykonywania zapytań i przekształcania ciągów i kolekcji ciągów. Zawiera również linki do tematów demonstrujących te zasady.  
  
 [LINQ i odbicie (Visual Basic)](linq-and-reflection.md)  
 Linki do przykładu, który pokazuje, jak LINQ używa odbicia.  
  
 [LINQ i katalogi plików (Visual Basic)](linq-and-file-directories.md)  
 Wyjaśnia, w jaki sposób LINQ może służyć do współdziałania z systemami plików. Zawiera również linki do tematów, które przedstawiają te koncepcje.  
  
 [Instrukcje: wykonywanie zapytań do ArrayList za pomocą LINQ (Visual Basic)](how-to-query-an-arraylist-with-linq.md)  
 Pokazuje, jak zbadać ArrayList w języku C#.  
  
 [Instrukcje: dodawanie metod niestandardowych dla zapytań LINQ (Visual Basic)](how-to-add-custom-methods-for-linq-queries.md)  
 Wyjaśnia, w jaki sposób rozszerzać zestaw metod, których można użyć dla zapytań LINQ przez dodanie metod rozszerzenia do <xref:System.Collections.Generic.IEnumerable%601> interfejsu.  
  
 [Zapytanie zintegrowane z językiem (LINQ) (Visual Basic)](index.md)  
 Zawiera łącza do tematów, które wyjaśniają LINQ i dostarczają przykłady kodu, który wykonuje zapytania.
