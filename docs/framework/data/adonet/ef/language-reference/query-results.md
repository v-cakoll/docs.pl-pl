---
title: Wyniki zapytania
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: bcd7b699-4e50-4523-8c33-2f54a103d94e
ms.openlocfilehash: 3ac80cfe06f8531dcd2343f676a6f78f8eb0e8f6
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854305"
---
# <a name="query-results"></a>Wyniki zapytania
Po przekonwertowaniu LINQ to Entities zapytania do drzew poleceń i wykonaniu wyniki zapytania są zwykle zwracane jako jeden z następujących elementów:  
  
- Kolekcja obiektów jednostek typu "zero" lub "rzutowanie typów złożonych" w modelu koncepcyjnym.  
  
- Typy CLR obsługiwane przez model koncepcyjny.  
  
- Kolekcje wbudowane.  
  
- Typy anonimowe.  
  
 Gdy zapytanie zostało wykonane względem źródła danych, wyniki są uwzględniane w typach CLR i zwracane do klienta. Wszystkie materializację obiektów są wykonywane przez Entity Framework. Wszelkie błędy, które wynikają z braku możliwości mapowania między Entity Framework i CLR spowodują, że wyjątki będą zgłaszane podczas materializację obiektów.
  
 Jeśli wykonanie zapytania zwróci podstawowe typy modelu koncepcyjnego, wyniki składają się z typów CLR, które są autonomiczne i odłączone od Entity Framework. Jeśli jednak zapytanie zwraca kolekcję obiektów jednostek z określonym typem, reprezentowane przez <xref:System.Data.Objects.ObjectQuery%601>, te typy są śledzone przez kontekst obiektu. Wszystkie zachowania obiektów (takie jak kolekcje podrzędne/nadrzędne, śledzenie zmian, polimorfizm i tak dalej) są zdefiniowane w Entity Framework. Tej funkcji można użyć w swojej pojemności, zgodnie z definicją w Entity Framework. Aby uzyskać więcej informacji, zobacz [Praca z obiektami](../working-with-objects.md).
  
 Typy struktur zwracane z zapytań (takich jak typy anonimowe i typy złożone o wartości null) `null` mogą być wartościami. Właściwość zwróconego obiektu może `null` być również wartością. <xref:System.Data.Objects.DataClasses.EntityCollection%601> Może to wynikać z projekcji właściwości kolekcji jednostki, która jest `null` wartością, taką jak wywołanie <xref:System.Linq.Queryable.FirstOrDefault%2A> elementu <xref:System.Data.Objects.ObjectQuery%601> , który nie ma żadnych elementów.  
  
 W niektórych sytuacjach może wydawać się, że zapytanie generuje materiałowy wynik w trakcie jego wykonywania, ale zapytanie zostanie wykonane na serwerze, a obiekt Entity nie będzie nigdy materiałowy w środowisku CLR. Może to spowodować problemy, jeśli są zależne od efektów ubocznych obiektu materializację.  
  
 Poniższy przykład zawiera klasę `MyContact`niestandardową, `LastName` z właściwością. Gdy właściwość jest ustawiona, zmienna jest zwiększana. `count` `LastName` Jeśli wykonasz dwa następujące zapytania, pierwsze zapytanie zostanie rozrastane `count` , gdy drugie zapytanie nie zostanie wykonane. Wynika to z faktu, że w `LastName` drugim zapytaniu właściwość jest rzutowana z wyników `MyContact` , a Klasa nigdy nie jest tworzona, ponieważ nie jest wymagana do wykonania zapytania w sklepie.  
  
 [!code-csharp[DP L2E Materialization Example#MaterializationSideEffects](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Materialization Example/CS/Program.cs#materializationsideeffects)]
 [!code-vb[DP L2E Materialization Example#MaterializationSideEffects](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Materialization Example/VB/Module1.vb#materializationsideeffects)]  
  
 [!code-csharp[DP L2E Materialization Example#MyContactClass](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Materialization Example/CS/Program.cs#mycontactclass)]
 [!code-vb[DP L2E Materialization Example#MyContactClass](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Materialization Example/VB/Module1.vb#mycontactclass)]
