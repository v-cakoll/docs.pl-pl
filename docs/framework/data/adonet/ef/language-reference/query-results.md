---
title: Wyniki zapytania
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: bcd7b699-4e50-4523-8c33-2f54a103d94e
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 32133d1b6fce619fb9990ab89820b7f19b6a5926
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="query-results"></a>Wyniki zapytania
Po [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] zapytania jest konwertować na drzewa polecenia i wykonywane, wyniki zapytania są zazwyczaj zwracane jako jedną z następujących:  
  
-   Kolekcja zero lub więcej obiektów typów jednostek lub dla projekcji typu złożonego w modelu koncepcyjnym.  
  
-   Typy CLR obsługiwane przez modelu koncepcyjnego.  
  
-   Kolekcje wbudowane.  
  
-   Typy anonimowe.  
  
 Zapytanie zostało wykonane w źródle danych, wyniki są zmaterializowany na typy CLR i zwracany do klienta. Wszystkie materialization obiektu jest wykonywane przez [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]. Błędów spowodowanych brakiem do mapowania między [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] i spowoduje, że wyjątki, aby zostać wygenerowany podczas materialization obiektu CLR.  
  
 Jeśli wykonanie kwerendy zwraca typów pierwotnych modelu koncepcyjnego, wyniki składają się z typów CLR, które są autonomiczne i jest odłączony od [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]. Jednak jeśli zapytanie zwraca kolekcję obiektów typów jednostek, reprezentowany przez <xref:System.Data.Objects.ObjectQuery%601>, te typy są śledzone przez obiekt kontekstu. Wszystkie zachowanie obiektu (na przykład kolekcje podrzędne i nadrzędne, śledzenia zmian polimorfizm i tak dalej) zostały zdefiniowane w [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]. Te funkcje mogą być używane w jego pojemność, zgodnie z definicją w [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]. Aby uzyskać więcej informacji, zobacz [Praca z obiektami](../../../../../../docs/framework/data/adonet/ef/working-with-objects.md).  
  
 Typy struktur zwracane z zapytań (np. typy anonimowe i typy złożone dopuszczające wartości zerowe) mogą być `null` wartość. <xref:System.Data.Objects.DataClasses.EntityCollection%601> Właściwości zwróconą jednostkę również mogą być `null` wartość. Może to wynikać z projekcji właściwości kolekcji jednostki, która jest `null` wartość, na przykład wywołanie <xref:System.Linq.Queryable.FirstOrDefault%2A> na <xref:System.Data.Objects.ObjectQuery%601> który nie ma żadnych elementów.  
  
 W niektórych sytuacjach zapytania mogą być wyświetlane do generowania zmaterializowanym wyniku podczas jej wykonywania, ale będzie można wykonać zapytania na serwerze i nigdy nie będzie można było zmaterializować obiekt jednostki w środowisku CLR. Może to powodować problemy, jeśli są zależnie od efektami ubocznymi materialization obiektu.  
  
 Poniższy przykład zawiera klasy niestandardowej `MyContact`, z `LastName` właściwości. Gdy `LastName` właściwość jest ustawiona, `count` zmiennej jest zwiększany. Jeśli można wykonywać następujące dwa zapytania, pierwsza kwerenda powoduje zwiększenie `count` podczas, gdy nie będzie drugiego zapytania. Wynika to z faktu w drugiej kwerendy `LastName` właściwości jest zaprojektowana z wyników i `MyContact` klasa jest tworzona nigdy, ponieważ nie jest wymagane do wykonania zapytania w magazynie.  
  
 [!code-csharp[DP L2E Materialization Example#MaterializationSideEffects](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Materialization Example/CS/Program.cs#materializationsideeffects)]
 [!code-vb[DP L2E Materialization Example#MaterializationSideEffects](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Materialization Example/VB/Module1.vb#materializationsideeffects)]  
  
 [!code-csharp[DP L2E Materialization Example#MyContactClass](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Materialization Example/CS/Program.cs#mycontactclass)]
 [!code-vb[DP L2E Materialization Example#MyContactClass](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Materialization Example/VB/Module1.vb#mycontactclass)]
