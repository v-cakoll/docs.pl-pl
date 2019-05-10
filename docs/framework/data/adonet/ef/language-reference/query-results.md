---
title: Wyniki zapytania
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: bcd7b699-4e50-4523-8c33-2f54a103d94e
ms.openlocfilehash: 98dbb0185de88c6fd69c6daf1540e997c14cc9e2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64641429"
---
# <a name="query-results"></a>Wyniki zapytania
Po [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] zapytania jest konwertowana na drzew poleceń i wykonywane, wyniki zapytania zwykle są zwracane jako jeden z następujących czynności:  
  
- Kolekcja zero lub więcej obiektów typów jednostek lub złożonych typów w modelu koncepcyjnym projekcji.  
  
- Obsługiwane przez model koncepcyjny typy CLR.  
  
- Kolekcje wbudowane.  
  
- Typy anonimowe.  
  
 Gdy zapytanie zostało wykonane względem źródła danych, wyniki są zmaterializowanego na typy CLR i zwracany do klienta. Wszystkie materializacja obiektu odbywa się przez [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]. Wszelkie błędy, które wynikają z brakiem połączenia do mapowania miedzy [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] i środowiska CLR spowoduje, że wyjątki zostanie wygenerowany podczas materializacja obiektu.  
  
 Jeśli wykonanie zapytania zwraca typów pierwotnych modelu koncepcyjnego, wyniki składają się z typów CLR, które są autonomiczne i jest odłączony od [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]. Jednakże, jeśli zapytanie zwraca kolekcję obiektów typów jednostek, reprezentowane przez <xref:System.Data.Objects.ObjectQuery%601>, te typy są śledzone przez obiekt kontekstu. Czy wszystkie zachowanie obiektu (na przykład kolekcje nadrzędny/podrzędny, śledzenia zmian, polimorfizm i tak dalej), zgodnie z definicją w [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]. Ta funkcja może służyć w jego możliwości, zgodnie z definicją w [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]. Aby uzyskać więcej informacji, zobacz [Praca z obiektami](../../../../../../docs/framework/data/adonet/ef/working-with-objects.md).  
  
 Struktura typy zwracane z zapytań (na przykład typy anonimowe i typy złożone dopuszczające wartości zerowe) mogą być `null` wartość. <xref:System.Data.Objects.DataClasses.EntityCollection%601> Również mogą być właściwość zwróconą jednostkę `null` wartość. Może to wynikać z projekcji kolekcji właściwości jednostki, która jest `null` wartości, takich jak wywoływanie <xref:System.Linq.Queryable.FirstOrDefault%2A> na <xref:System.Data.Objects.ObjectQuery%601> , nie ma żadnych elementów.  
  
 W niektórych sytuacjach zapytanie, może pojawić się do generowania zmaterializowanych wynik podczas jego realizacji, ale będzie można wykonać zapytania na serwerze i obiekt jednostki nigdy nie będzie można zmaterializowanego w CLR. Może to powodować problemy, jeśli zależy efekty uboczne materializacja obiektu.  
  
 Poniższy przykład zawiera klasę niestandardową `MyContact`, za pomocą `LastName` właściwości. Gdy `LastName` ustawiono właściwość `count` zmiennej jest zwiększany. Jeśli dwa następujące zapytania są wykonywane, pierwsze zapytanie powoduje zwiększenie `count` podczas drugiego zapytania nie będą działać. Jest to spowodowane w drugiego zapytania `LastName` właściwość jest rzutowany na liście wyników i `MyContact` klasy nigdy nie utworzono, ponieważ nie jest wymagane do wykonania zapytania w sklepie.  
  
 [!code-csharp[DP L2E Materialization Example#MaterializationSideEffects](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Materialization Example/CS/Program.cs#materializationsideeffects)]
 [!code-vb[DP L2E Materialization Example#MaterializationSideEffects](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Materialization Example/VB/Module1.vb#materializationsideeffects)]  
  
 [!code-csharp[DP L2E Materialization Example#MyContactClass](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Materialization Example/CS/Program.cs#mycontactclass)]
 [!code-vb[DP L2E Materialization Example#MyContactClass](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Materialization Example/VB/Module1.vb#mycontactclass)]
