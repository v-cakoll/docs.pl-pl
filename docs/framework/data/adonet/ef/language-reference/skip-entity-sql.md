---
title: POMIŃ (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: e2139412-8ea4-451b-8f10-91af18dfa3ec
ms.openlocfilehash: 321f6c5ae62ce21249ae4c1081b8e98427bc3df2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43500745"
---
# <a name="skip-entity-sql"></a>POMIŃ (jednostka SQL)
Stronicowania fizycznych można wykonać przy użyciu Podklauzula POMIŃ w klauzuli ORDER BY. POMIŃ nie można użyć oddzielnie od klauzuli ORDER BY.  
  
## <a name="syntax"></a>Składnia  
  
```  
[ SKIP n ]  
```  
  
## <a name="arguments"></a>Argumenty  
 `n`  
 Liczba elementów do pominięcia.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli POMIŃ wyrażenie Podklauzula znajduje się w klauzuli ORDER BY, wyniki będą sortowane według specyfikacji sortowania i zestawu wyników będzie zawierać wiersze, rozpoczynając od następnego wiersza od razu po wyrażeniu SKIP. Na przykład 5 POMIŃ Pomiń pierwsze pięć wierszy i zwraca od szóstego wierszy do przodu.  
  
> [!NOTE]
>  [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Zapytanie jest nieprawidłowe, jeśli modyfikator GÓRNYM i POMIŃ Podklauzula znajdują się w jednym wyrażeniu zapytania. Zmieniając wyrażenia TOP wyrażenie LIMIT powinien zostać przepisany z zapytania.  
  
> [!NOTE]
>  W [!INCLUDE[ssVersion2000](../../../../../../includes/ssversion2000-md.md)], za pomocą POMIŃ z listą ORDER BY-key kolumn może zwracać nieprawidłowe wyniki. Więcej niż określoną liczbę wierszy może zostać pominięta, jeżeli kolumnę niebędącą kolumną klucza zawiera zduplikowane dane. Jest to spowodowane jak SKIP jest tłumaczony na [!INCLUDE[ssVersion2000](../../../../../../includes/ssversion2000-md.md)]. Na przykład w poniższym kodzie więcej niż pięć wierszy może zostać pominięta, jeżeli `E.NonKeyColumn` zawiera zduplikowane wartości:  
>   
>  `SELECT [E] FROM Container.EntitySet AS [E] ORDER BY [E].[NonKeyColumn] DESC SKIP 5L`  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Zapytania w [to](https://msdn.microsoft.com/library/bb738702\(v=vs.100\).aspx#_ESQL) przykładzie użyto operatora w klauzuli ORDER BY z pominięciem określić kolejność sortowania na obiekty zwrócone w instrukcji SELECT.  
  
## <a name="see-also"></a>Zobacz też  
 [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)  
 [Porady: wyniki strony za pomocą kwerendy](https://msdn.microsoft.com/library/ffc0f920-e7de-42e0-9b12-ef356421d030)  
 [Stronicowanie](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)  
 [TOP](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
