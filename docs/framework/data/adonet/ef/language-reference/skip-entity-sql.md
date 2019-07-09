---
title: POMIŃ (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: e2139412-8ea4-451b-8f10-91af18dfa3ec
ms.openlocfilehash: 88d4c9c987f451e9a653d5b9c213e7158670ed4b
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2019
ms.locfileid: "67662136"
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
>  W programie SQL Server 2000 przy POMIŃ ORDER BY-key kolumn może zwracać nieprawidłowe wyniki. Więcej niż określoną liczbę wierszy może zostać pominięta, jeżeli kolumnę niebędącą kolumną klucza zawiera zduplikowane dane. Jest to spowodowane jak SKIP jest tłumaczony dla programu SQL Server 2000. Na przykład w poniższym kodzie więcej niż pięć wierszy może zostać pominięta, jeżeli `E.NonKeyColumn` zawiera zduplikowane wartości:  
>   
>  `SELECT [E] FROM Container.EntitySet AS [E] ORDER BY [E].[NonKeyColumn] DESC SKIP 5L`  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Zapytania w [jak: Strona za pośrednictwem wyników zapytania](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100)) używa operatora klauzuli ORDER BY z pominięciem, aby określić kolejność sortowania na obiekty zwrócone w instrukcji SELECT.  
  
## <a name="see-also"></a>Zobacz także

- [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)
- [Instrukcje: Przejrzyj wyniki zapytania](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))
- [Stronicowanie](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)
- [TOP](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
