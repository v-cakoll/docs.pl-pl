---
title: "POMIŃ (jednostka SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e2139412-8ea4-451b-8f10-91af18dfa3ec
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 0dd0754158000642dd078f00033c9ddc2f78686d
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="skip-entity-sql"></a>POMIŃ (jednostka SQL)
Stronicowanie fizycznych można wykonać za pomocą klauzul podrzędnych SKIP w klauzuli ORDER BY. POMIŃ nie można używać osobno z klauzuli ORDER BY.  
  
## <a name="syntax"></a>Składnia  
  
```  
[ SKIP n ]  
```  
  
## <a name="arguments"></a>Argumenty  
 `n`  
 Liczba elementów do pominięcia.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli klauzul podrzędnych SKIP w wyrażeniu znajduje się w klauzuli ORDER BY, będzie można posortować wyników według specyfikacji sortowania i zestaw wyników zawiera wiersze, zaczynając od następnego wiersza od razu po wyrażeniu SKIP. Na przykład 5 POMIŃ Pomiń pierwsze pięć wiersze i zwrócenia z wiersza szóstego do przodu.  
  
> [!NOTE]
>  [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Zapytanie jest nieprawidłowe, jeśli zarówno modyfikator TOP, jak i klauzul podrzędnych SKIP znajdują się w jednym wyrażeniu zapytania. Zapytanie powinno ulegną zmieniając wyrażenia TOP w wyrażeniu LIMIT.  
  
> [!NOTE]
>  W [!INCLUDE[ssVersion2000](../../../../../../includes/ssversion2000-md.md)], za pomocą POMIŃ z listą ORDER BY na niekluczowe może zwracać niepoprawne wyniki. Więcej niż określoną liczbę wierszy mogły zostać pominięte, jeśli kolumna klucza ma zduplikowane dane w nim. Jest to spowodowane jak SKIP jest translacja dla [!INCLUDE[ssVersion2000](../../../../../../includes/ssversion2000-md.md)]. Na przykład w poniższym kodzie więcej niż pięć wierszy mogły zostać pominięte Jeśli `E.NonKeyColumn` zawiera zduplikowane wartości:  
>   
>  `SELECT [E] FROM Container.EntitySet AS [E] ORDER BY [E].[NonKeyColumn] DESC SKIP 5L`  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Zapytania w [to](https://msdn.microsoft.com/library/bb738702\(v=vs.100\).aspx#_ESQL) przykładzie użyto operatora ORDER BY z pominięciem można określić kolejność sortowania użyć obiektów zwracanych w instrukcji SELECT.  
  
## <a name="see-also"></a>Zobacz też  
 [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)  
 [Porady: powoduje strony za pomocą kwerendy](http://msdn.microsoft.com/library/ffc0f920-e7de-42e0-9b12-ef356421d030)  
 [Stronicowanie](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)  
 [TOP](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
