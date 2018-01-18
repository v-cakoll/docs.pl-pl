---
title: "Literały null i wnioskowanie o typie (jednostka SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: edd56afb-af1b-4e7d-b210-cb8998143426
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: eeea6a6b1674361a605d5236e203699d08724df3
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="null-literals-and-type-inference-entity-sql"></a>Literały null i wnioskowanie o typie (jednostka SQL)
Literały null są zgodne z dowolnego typu w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] system typów. Niemniej jednak w przypadku typ literału null do można wywnioskować poprawnie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nakłada pewne ograniczenia, na której można użyć literału null.  
  
## <a name="typed-nulls"></a>Wartości null bez typu  
 Wartości null bez typu może być używana w dowolnym. Wnioskowanie o typie nie jest wymagana dla wartości null bez typu, ponieważ jest on znany typ. Na przykład można utworzyć wartości null typu Int16 z następującymi [!INCLUDE[esql](../../../../../../includes/esql-md.md)] utworzyć:  
  
 `(cast(null as Int16))`  
  
## <a name="free-floating-null-literals"></a>Swobodnego literałów wartości Null  
 Swobodnego literałów wartości null, mogą być używane w następujących sytuacjach:  
  
-   Jako argument wyrażenia RZUTOWANIA lub TRAKTUJ. Jest to zalecany sposób utworzyć wyrażenie typu o wartości null.  
  
-   Jako argument do metody lub funkcji. Mają zastosowanie standardowe przeciążenia reguły.  
  
-   Jako jeden z argumentów wyrażenia arytmetyczne, takie jak +, -, lub /. Inne argumenty nie może być literałów wartości null, w przeciwnym razie wnioskowanie typu nie jest możliwe.  
  
-   Jako argumenty do wyrażenie logiczne (AND, OR lub nie). Wszystkie argumenty są określane jako typu Boolean.  
  
-   Jako argumentu wyrażenia IS NULL i IS NOT NULL.  
  
-   Jako co najmniej jeden z argumentów do wyrażenia LIKE. Wszystkie argumenty powinny być ciągami.  
  
-   Jako jeden lub więcej argumentów konstruktora o nazwie typu.  
  
-   Jako jeden lub więcej argumentów konstruktora multiset —. Co najmniej jeden argument multiset — Konstruktor musi być wyrażenie, które nie jest literałem wartości null.  
  
-   Co najmniej jednego wyrażenia w wyrażeniu CASE następnie możesz też. Przynajmniej jedno z wyrażeń w wyrażeniu CASE następnie możesz też musi być wyrażeniem innym niż null literału.  
  
 Swobodnego literałów wartości null nie można używać w innych scenariuszach. Na przykład nie może być używane jako argumenty konstruktora wiersza.  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
