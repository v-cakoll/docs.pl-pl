---
title: LINQ do obiektów (C#)
ms.date: 07/20/2015
ms.assetid: c5c2c178-3529-4f6c-b3df-2d5267af7f22
ms.openlocfilehash: ae4389aa1ce049edc71bff42c38f66fb328ba034
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75344781"
---
# <a name="linq-to-objects-c"></a>LINQ do obiektów (C#)
Termin "LINQ do obiektów" odnosi się do korzystania <xref:System.Collections.IEnumerable> z <xref:System.Collections.Generic.IEnumerable%601> zapytań LINQ z dowolnym lub kolekcji bezpośrednio, bez użycia pośredniego dostawcy LINQ lub interfejsu API, takich jak [LINQ do SQL](../../../../framework/data/adonet/sql/linq/index.md) lub [LINQ do XML](./linq-to-xml-overview.md). Linq służy do wykonywania zapytań do <xref:System.Collections.Generic.List%601> <xref:System.Array>wszystkich <xref:System.Collections.Generic.Dictionary%602>kolekcji wyliczanych, takich jak , , lub . Kolekcja może być zdefiniowana przez użytkownika lub może być zwracana przez interfejs API .NET Framework.  
  
 W sensie podstawowym LINQ do obiektów reprezentuje nowe podejście do kolekcji. W stary sposób trzeba było `foreach` napisać złożone pętle, które określały sposób pobierania danych z kolekcji. W podejściu LINQ piszesz kod deklaratywny, który opisuje, co chcesz pobrać.  
  
 Ponadto zapytania LINQ oferują trzy główne `foreach` zalety w porównaniu z tradycyjnymi pętlami:  
  
1. Są one bardziej zwięzłe i czytelne, zwłaszcza podczas filtrowania wielu warunków.  
  
2. Zapewniają one zaawansowane możliwości filtrowania, porządkowania i grupowania przy minimalnym kodzie aplikacji.  
  
3. Mogą być przenoszeni do innych źródeł danych z niewielkimi lub żadnymi modyfikacjami.  
  
 Ogólnie rzecz biorąc bardziej złożona operacja, którą chcesz wykonać na danych, tym więcej korzyści zrealizujesz przy użyciu LINQ zamiast tradycyjnych technik iteracji.  
  
 Celem tej sekcji jest wykazanie podejścia LINQ z niektórych przykładów wybierz. Nie ma być wyczerpujący.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [LINQ i ciągi (C#)](./linq-and-strings.md)  
 W tym artykule wyjaśniono, jak LINQ może służyć do wykonywania zapytań i przekształcania ciągów i kolekcji ciągów. Zawiera również linki do tematów, które pokazują te zasady.  
  
 [LINQ i odbicie (C#)](how-to-query-an-assembly-s-metadata-with-reflection-linq.md)  
 Łącza do próbki, która pokazuje, jak LINQ używa odbicia.  
  
 [LINQ i katalogi plików (C#)](./linq-and-file-directories.md)  
 W tym artykule wyjaśniono, w jaki sposób linq może służyć do interakcji z systemami plików. Zawiera również łącza do tematów, które pokazują te pojęcia.  
  
 [Jak zapytanie ArrayList z LINQ (C#)](./how-to-query-an-arraylist-with-linq.md)  
 Pokazuje, jak zapytanie ArrayList w języku C#.  
  
 [Jak dodać metody niestandardowe dla zapytań LINQ (C#)](./how-to-add-custom-methods-for-linq-queries.md)  
 W tym artykule wyjaśniono, jak rozszerzyć zestaw metod, których można <xref:System.Collections.Generic.IEnumerable%601> używać dla kwerend LINQ, dodając metody rozszerzenia do interfejsu.  
  
 [Zapytanie zintegrowane z językiem (LINQ) (C#)](./index.md)  
 Zawiera łącza do tematów, które wyjaśniają LINQ i podać przykłady kodu, który wykonuje kwerendy.
