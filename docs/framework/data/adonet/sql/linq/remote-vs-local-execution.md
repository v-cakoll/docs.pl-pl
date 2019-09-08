---
title: Zdalne a lokalne wykonanie
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ee50e943-9349-4c84-ab1c-c35d3ada1a9c
ms.openlocfilehash: a21d5bbffdb1a78d3062929a1ca384a750af59a7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781156"
---
# <a name="remote-vs-local-execution"></a>Zdalne a lokalne wykonanie
Możesz zdecydować się na zdalne wykonywanie zapytań (to oznacza, że aparat bazy danych wykonuje zapytanie względem bazy danych) lub lokalnie ([!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] wykonuje zapytanie względem lokalnej pamięci podręcznej).  
  
## <a name="remote-execution"></a>Zdalne wykonywanie kodu  
 Rozważ następujące zapytanie:  
  
 [!code-csharp[DLinqQueryConcepts#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#7)]
 [!code-vb[DLinqQueryConcepts#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#7)]  
  
 Jeśli baza danych ma tysiące rzędów zamówień, nie chcesz pobierać ich wszystkich, aby przetwarzać mały podzestaw. W programie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Klasaimplementuje<xref:System.Linq.IQueryable>interfejs. <xref:System.Data.Linq.EntitySet%601> Takie podejście gwarantuje, że takie zapytania można wykonać zdalnie. Przepływ dwóch głównych korzyści z tej techniki:  
  
- Nie pobrano zbędnych danych.  
  
- Zapytanie wykonywane przez aparat bazy danych jest często wydajniejsze ze względu na indeksy bazy danych.  
  
## <a name="local-execution"></a>lokalne wykonanie  
 W innych sytuacjach może być konieczne posiadanie kompletnego zestawu powiązanych jednostek w lokalnej pamięci podręcznej. W tym celu <xref:System.Data.Linq.EntitySet%601> zapewnia metodę, <xref:System.Data.Linq.EntitySet%601.Load%2A> aby jawnie załadować <xref:System.Data.Linq.EntitySet%601>wszystkie elementy członkowskie.  
  
 <xref:System.Data.Linq.EntitySet%601> Jeśli jest już załadowany, kolejne zapytania są wykonywane lokalnie. To podejście jest pomocne na dwa sposoby:  
  
- Jeśli kompletny zestaw musi być używany lokalnie lub wiele razy, można uniknąć zdalnych zapytań i skojarzonych opóźnień.  
  
- Jednostkę można serializować jako kompletną jednostkę.  
  
 Poniższy fragment kodu ilustruje sposób uzyskania lokalnego wykonania:  
  
 [!code-csharp[DLinqQueryConcepts#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#8)]
 [!code-vb[DLinqQueryConcepts#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#8)]  
  
## <a name="comparison"></a>Porównanie  
 Te dwie możliwości oferują zaawansowaną kombinację opcji: zdalne wykonywanie dużych kolekcji i wykonywanie lokalne dla małych kolekcji lub, gdzie jest wymagana kompletna kolekcja. Implementowanie zdalnego wykonywania przez <xref:System.Linq.IQueryable>program i wykonywanie lokalne w odniesieniu do <xref:System.Collections.Generic.IEnumerable%601> kolekcji w pamięci. Aby wymusić wykonanie lokalne (czyli <xref:System.Collections.Generic.IEnumerable%601>), zobacz [konwertowanie typu na rodzajowy interfejs IEnumerable](convert-a-type-to-a-generic-ienumerable.md).  
  
### <a name="queries-against-unordered-sets"></a>Zapytania dotyczące nieuporządkowanych zestawów  
 Należy zwrócić uwagę na istotną różnicę między lokalną kolekcją, która implementuje <xref:System.Collections.Generic.List%601> i kolekcję, która zapewnia zapytania zdalne wykonywane w odniesieniu do *nieuporządkowanych zestawów* w relacyjnej bazie danych. <xref:System.Collections.Generic.List%601>metody, takie jak te, które używają wartości indeksu, wymagają semantyki list, która zazwyczaj nie można uzyskać za pomocą zapytania zdalnego dla nieuporządkowanego zestawu. Z tego powodu takie metody niejawnie ładują <xref:System.Data.Linq.EntitySet%601> , aby umożliwić wykonanie lokalne.  
  
## <a name="see-also"></a>Zobacz także

- [Pojęcia dotyczące zapytań](query-concepts.md)
