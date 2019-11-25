---
title: LINQ to Objects (C#)
ms.date: 07/20/2015
ms.assetid: c5c2c178-3529-4f6c-b3df-2d5267af7f22
ms.openlocfilehash: b0cc47604b65a5883643d61b44b1e9878ec4b1bf
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2019
ms.locfileid: "74140890"
---
# <a name="linq-to-objects-c"></a>LINQ to Objects (C#)
Termin "LINQ to Objects" odnosi się do używania zapytań LINQ z dowolnymi <xref:System.Collections.IEnumerable> lub <xref:System.Collections.Generic.IEnumerable%601> kolekcji bezpośrednio, bez użycia pośredniego dostawcy LINQ lub interfejsu API, takiego jak [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) lub [LINQ to XML](./linq-to-xml-overview.md). Za pomocą LINQ można badać wszystkie wyliczalne kolekcje, takie jak <xref:System.Collections.Generic.List%601>, <xref:System.Array>lub <xref:System.Collections.Generic.Dictionary%602>. Kolekcja może być zdefiniowana przez użytkownika lub może być zwrócona przez interfejs API .NET Framework.  
  
 W podstawowym sensie LINQ to Objects reprezentuje nowe podejście do kolekcji. W stary sposób należy napisać złożone pętle `foreach`, które określają sposób pobierania danych z kolekcji. W podejściu LINQ napiszesz kod deklaratywny opisujący, co chcesz pobrać.  
  
 Ponadto zapytania LINQ oferują trzy główne zalety w porównaniu z tradycyjnymi pętlami `foreach`:  
  
1. Są one bardziej zwięzłe i czytelne, szczególnie w przypadku filtrowania wielu warunków.  
  
2. Zapewniają one zaawansowane możliwości filtrowania, porządkowania i grupowania przy minimalnym kodzie aplikacji.  
  
3. Można je przenieść do innych źródeł danych z niewielką lub bez modyfikacji.  
  
 Ogólnie rzecz biorąc, bardziej złożone operacje, które mają być wykonywane na danych, tym większe korzyści, które można wykorzystać przy użyciu LINQ zamiast tradycyjnych technik iteracji.  
  
 Celem tej sekcji jest zademonstrowanie podejścia LINQ z pewnymi przykładami. Nie jest to wyczerpujące.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [LINQ i ciągi (C#)](./linq-and-strings.md)  
 Wyjaśnia, w jaki sposób LINQ może służyć do wykonywania zapytań i przekształcania ciągów i kolekcji ciągów. Zawiera również linki do tematów demonstrujących te zasady.  
  
 [LINQ i odbicieC#()](how-to-query-an-assembly-s-metadata-with-reflection-linq.md)  
 Linki do przykładu, który pokazuje, jak LINQ używa odbicia.  
  
 [LINQ i katalogi plików (C#)](./linq-and-file-directories.md)  
 Wyjaśnia, w jaki sposób LINQ może służyć do współdziałania z systemami plików. Zawiera również linki do tematów, które przedstawiają te koncepcje.  
  
 [Instrukcje: zapytanie do ArrayList za pomocą LINQ (C#)](./how-to-query-an-arraylist-with-linq.md)  
 Pokazuje, jak zbadać ArrayList w C#.  
  
 [Jak dodać metody niestandardowe dla zapytań LINQ (C#)](./how-to-add-custom-methods-for-linq-queries.md)  
 Wyjaśnia, w jaki sposób rozszerzać zestaw metod, których można użyć dla zapytań LINQ przez dodanie metod rozszerzenia do interfejsu <xref:System.Collections.Generic.IEnumerable%601>.  
  
 [Zapytanie zintegrowane z językiem (LINQ)C#()](./index.md)  
 Zawiera łącza do tematów, które wyjaśniają LINQ i dostarczają przykłady kodu, który wykonuje zapytania.
