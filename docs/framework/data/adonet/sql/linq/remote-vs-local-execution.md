---
title: Zdalne a lokalne wykonanie
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ee50e943-9349-4c84-ab1c-c35d3ada1a9c
ms.openlocfilehash: 02d0417bc05f8585dc469d365089c8123d395f64
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59164518"
---
# <a name="remote-vs-local-execution"></a>Zdalne a lokalne wykonanie
Możesz zdecydować się na wykonywanie zapytań albo zdalnie (oznacza to, że aparat bazy danych wykonuje zapytanie względem bazy danych) lub lokalnie ([!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] wykonuje zapytanie względem lokalnej pamięci podręcznej).  
  
## <a name="remote-execution"></a>Zdalne wykonywanie kodu  
 Należy wziąć pod uwagę następujące zapytanie:  
  
 [!code-csharp[DLinqQueryConcepts#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#7)]
 [!code-vb[DLinqQueryConcepts#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#7)]  
  
 Jeśli baza danych zawiera tysiące wierszy zamówienia, czy chcesz pobrać je wszystkie do przetworzenia przechowywanego. W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Data.Linq.EntitySet%601> klasy implementuje <xref:System.Linq.IQueryable> interfejsu. To podejście zapewnia, że takich zapytań może być wykonywane zdalnie. Przepływ dwie główne korzyści z tej techniki:  
  
-   Zbędne dane nie są pobierane.  
  
-   Zapytania wykonywane przez aparat bazy danych jest często bardziej efektywne z powodu indeksy bazy danych.  
  
## <a name="local-execution"></a>lokalne wykonanie  
 W innych sytuacjach możesz chcieć mieć kompletny zestaw powiązanych jednostek w lokalnej pamięci podręcznej. W tym celu <xref:System.Data.Linq.EntitySet%601> zapewnia <xref:System.Data.Linq.EntitySet%601.Load%2A> metodę, aby jawnie załadować wszystkie elementy członkowskie <xref:System.Data.Linq.EntitySet%601>.  
  
 Jeśli <xref:System.Data.Linq.EntitySet%601> jest już załadowany, kolejne zapytania są wykonywane lokalnie. Takie podejście pomaga na dwa sposoby:  
  
-   Jeśli kompletny zestaw musi używać lokalnie lub wiele razy, możesz uniknąć zapytań zdalnych i skojarzone opóźnienia.  
  
-   Jednostki może być Zserializowany jako całą jednostkę.  
  
 Poniższy fragment kodu ilustruje sposób lokalnego wykonania można uzyskać:  
  
 [!code-csharp[DLinqQueryConcepts#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#8)]
 [!code-vb[DLinqQueryConcepts#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#8)]  
  
## <a name="comparison"></a>Porównanie  
 Te dwie funkcje zapewniają kombinację opcji: zdalne wykonywanie kodu w dużych kolekcjach i lokalnych wykonań dla małych kolekcji lub w których wymagane jest pełną kolekcję. Implementowanie zdalne wykonywanie kodu za pomocą <xref:System.Linq.IQueryable>i lokalne miało zostać wykonane w pamięci <xref:System.Collections.Generic.IEnumerable%601> kolekcji. Aby wymusić wykonanie lokalne (czyli <xref:System.Collections.Generic.IEnumerable%601>), zobacz [Konwertowanie typu do ogólnego interfejsu IEnumerable](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-type-to-a-generic-ienumerable.md).  
  
### <a name="queries-against-unordered-sets"></a>Zapytania dotyczące nieuporządkowane zestawy  
 Należy pamiętać, istotną różnicą między kolekcji lokalnej, która implementuje <xref:System.Collections.Generic.List%601> i kolekcję, która umożliwia zdalne zapytania wykonywane względem *nieuporządkowane zestawy* relacyjnej bazy danych. <xref:System.Collections.Generic.List%601> metody, takich jak implementacje używające wartości indeksu wymagają semantyki listy, które zwykle nie można uzyskać za pośrednictwem zdalnego zapytanie względem zestawu nieuporządkowanego. Z tego powodu takie metody niejawnie obciążenia <xref:System.Data.Linq.EntitySet%601> i umożliwia wykonywanie lokalne.  
  
## <a name="see-also"></a>Zobacz także

- [Pojęcia dotyczące zapytań](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
