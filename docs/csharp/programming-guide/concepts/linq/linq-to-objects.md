---
title: LINQ to Objects (C#)
ms.date: 07/20/2015
ms.assetid: c5c2c178-3529-4f6c-b3df-2d5267af7f22
ms.openlocfilehash: f4ca6e57ffff026cb73121ecaf443ae54b25262c
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990026"
---
# <a name="linq-to-objects-c"></a>LINQ to Objects (C#)

Termin "LINQ to Objects" odnosi się do użycia zapytań LINQ z dowolnym <xref:System.Collections.IEnumerable> lub <xref:System.Collections.Generic.IEnumerable%601> kolekcją bezpośrednio, bez użycia pośredniego dostawcy LINQ lub interfejsu API, takiego jak [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) lub [LINQ to XML](./linq-to-xml-overview.md). Za pomocą LINQ można badać wszystkie wyliczalne kolekcje, takie jak <xref:System.Collections.Generic.List%601> , <xref:System.Array> lub <xref:System.Collections.Generic.Dictionary%602> . Kolekcja może być zdefiniowana przez użytkownika lub może być zwracana przez interfejs API platformy .NET.  
  
 W podstawowym sensie LINQ to Objects reprezentuje nowe podejście do kolekcji. W stary sposób należy napisać złożone `foreach` pętle, które określają sposób pobierania danych z kolekcji. W podejściu LINQ napiszesz kod deklaratywny opisujący, co chcesz pobrać.  
  
 Ponadto zapytania LINQ oferują trzy główne zalety przed tradycyjnymi `foreach` pętlami:  
  
- Są one bardziej zwięzłe i czytelne, szczególnie w przypadku filtrowania wielu warunków.  
  
- Zapewniają one zaawansowane możliwości filtrowania, porządkowania i grupowania przy minimalnym kodzie aplikacji.  
  
- Można je przenieść do innych źródeł danych z niewielką lub bez modyfikacji.  
  
 Ogólnie rzecz biorąc, bardziej złożone operacje, które mają być wykonywane na danych, tym większe korzyści można wykorzystać przy użyciu LINQ zamiast tradycyjnych technik iteracji.  
  
 Celem tej sekcji jest zademonstrowanie podejścia LINQ z pewnymi przykładami. Nie jest to wyczerpujące.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [LINQ i ciągi (C#)](./linq-and-strings.md)  
 Wyjaśnia, w jaki sposób LINQ może służyć do wykonywania zapytań i przekształcania ciągów i kolekcji ciągów. Zawiera również linki do artykułów demonstrujących te zasady.  
  
 [LINQ i odbicie (C#)](how-to-query-an-assembly-s-metadata-with-reflection-linq.md)  
 Linki do przykładu, który pokazuje, jak LINQ używa odbicia.  
  
 [LINQ i katalogi plików (C#)](./linq-and-file-directories.md)  
 Wyjaśnia, w jaki sposób LINQ może służyć do współdziałania z systemami plików. Zawiera również linki do artykułów, które przedstawiają te koncepcje.  
  
 [Jak zbadać ArrayList za pomocą LINQ (C#)](./how-to-query-an-arraylist-with-linq.md)  
 Pokazuje, jak zbadać ArrayList w języku C#.  
  
 [Jak dodać metody niestandardowe dla zapytań LINQ (C#)](./how-to-add-custom-methods-for-linq-queries.md)  
 Wyjaśnia, w jaki sposób rozszerzać zestaw metod, których można użyć dla zapytań LINQ przez dodanie metod rozszerzenia do <xref:System.Collections.Generic.IEnumerable%601> interfejsu.  
  
 [Language-Integrated Query (LINQ) (C#)](./index.md)  
 Zawiera łącza do artykułów, które objaśniają LINQ i dostarczają przykłady kodu, który wykonuje zapytania.
