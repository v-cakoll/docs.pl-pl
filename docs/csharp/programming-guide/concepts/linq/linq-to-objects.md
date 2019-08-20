---
title: LINQ to Objects (C#)
ms.date: 07/20/2015
ms.assetid: c5c2c178-3529-4f6c-b3df-2d5267af7f22
ms.openlocfilehash: 9e20b2c7278787671c7a27646b7cbaac78b57d5f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591862"
---
# <a name="linq-to-objects-c"></a>LINQ to Objects (C#)
Termin "LINQ to Objects" odnosi się do użycia zapytań LINQ z <xref:System.Collections.IEnumerable> dowolnym lub <xref:System.Collections.Generic.IEnumerable%601> kolekcją bezpośrednio, bez użycia pośredniego dostawcy LINQ lub interfejsu API, takiego jak [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) lub [LINQ to XML](./linq-to-xml-overview.md). Za pomocą LINQ można badać wszystkie wyliczalne kolekcje, <xref:System.Collections.Generic.List%601>takie <xref:System.Array>jak, <xref:System.Collections.Generic.Dictionary%602>lub. Kolekcja może być zdefiniowana przez użytkownika lub może być zwrócona przez interfejs API .NET Framework.  
  
 W podstawowym sensie LINQ to Objects reprezentuje nowe podejście do kolekcji. W stary sposób należy napisać złożone `foreach` pętle, które określają sposób pobierania danych z kolekcji. W podejściu LINQ napiszesz kod deklaratywny opisujący, co chcesz pobrać.  
  
 Ponadto zapytania LINQ oferują trzy główne zalety przed tradycyjnymi `foreach` pętlami:  
  
1. Są one bardziej zwięzłe i czytelne, szczególnie w przypadku filtrowania wielu warunków.  
  
2. Zapewniają one zaawansowane możliwości filtrowania, porządkowania i grupowania przy minimalnym kodzie aplikacji.  
  
3. Można je przenieść do innych źródeł danych z niewielką lub bez modyfikacji.  
  
 Ogólnie rzecz biorąc, bardziej złożone operacje, które mają być wykonywane na danych, tym większe korzyści, które można wykorzystać przy użyciu LINQ zamiast tradycyjnych technik iteracji.  
  
 Celem tej sekcji jest zademonstrowanie podejścia LINQ z pewnymi przykładami. Nie jest to wyczerpujące.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [LINQ i ciągi (C#)](./linq-and-strings.md)  
 Wyjaśnia, w jaki sposób LINQ może służyć do wykonywania zapytań i przekształcania ciągów i kolekcji ciągów. Zawiera również linki do tematów demonstrujących te zasady.  
  
 [LINQ i odbicieC#()](./linq-and-reflection.md)  
 Linki do przykładu, który pokazuje, jak LINQ używa odbicia.  
  
 [LINQ i katalogi plików (C#)](./linq-and-file-directories.md)  
 Wyjaśnia, w jaki sposób LINQ może służyć do współdziałania z systemami plików. Zawiera również linki do tematów, które przedstawiają te koncepcje.  
  
 [Instrukcje: Kwerenda ArrayList za pomocą LINQ (C#)](./how-to-query-an-arraylist-with-linq.md)  
 Pokazuje, jak zbadać ArrayList w C#.  
  
 [Instrukcje: Dodaj niestandardowe metody dla zapytań LINQ (C#)](./how-to-add-custom-methods-for-linq-queries.md)  
 Wyjaśnia, w jaki sposób rozszerzać zestaw metod, których można użyć dla zapytań LINQ przez dodanie metod rozszerzenia do <xref:System.Collections.Generic.IEnumerable%601> interfejsu.  
  
 [Zapytanie zintegrowane z językiem (LINQ)C#()](./index.md)  
 Zawiera łącza do tematów, które wyjaśniają LINQ i dostarczają przykłady kodu, który wykonuje zapytania.
