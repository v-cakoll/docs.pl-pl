---
title: Wejściowy zestaw znaków (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 13d291d3-e6bc-4719-b953-758b61a590b6
ms.openlocfilehash: dce967ea8853f81fedaa53ea706fab4839b9f474
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54641203"
---
# <a name="input-character-set-entity-sql"></a>Wejściowy zestaw znaków (jednostka SQL)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] akceptuje znaków UNICODE zakodowanych w formacie UTF-16.  
  
 Literały ciągu może zawierać żadnych znaków UTF-16 ujęta w apostrofy. Na przykład N "文字列リテラル". Gdy literały ciągów są porównywane, oryginalne wartości UTF-16 są używane. Na przykład N'ABC "różni się w strony kodowe kalendarza japońskiego i łacińskiego.  
  
 Komentarze mogą zawierać dowolne znaki UTF-16.  
  
 Identyfikatory o zmienionym znaczeniu może zawierać żadnych znaków UTF-16 w nawiasach kwadratowych. Na przykład [エスケープされた識別子]. Porównanie identyfikatorów UTF-16, poprzedzone znakiem zmiany znaczenia jest uwzględniana wielkość liter. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] traktuje wersji liter, są wyświetlane takie same, które pochodzą z różne strony kodowe jako różne znaki. Na przykład [ABC] jest odpowiednikiem [abc], jeśli odpowiadające im znaki pochodzą z tej samej strony kodowej. Jednakże jeśli ten sam dwa identyfikatory są z różne strony kodowe, nie są równoważne.  
  
 Biały znak jest znakiem odstępu UTF-16.  
  
 Nowy wiersz jest dowolny znormalizowane znak nowego wiersza UTF-16. Na przykład "\n" i "\r\n" są traktowane jako znaki nowego wiersza, ale '\r' nie jest znakiem nowego wiersza.  
  
 Słowa kluczowe, wyrażenia i znaków interpunkcyjnych może być dowolnym znakiem UTF-16, który normalizuje do Latin. Na przykład wybór w japońskich strona kodowa jest nieprawidłowa — słowo kluczowe.  
  
 Słowa kluczowe, wyrażenia i znaków interpunkcyjnych może być tylko znaki alfabetu łacińskiego. `SELECT` w japońskich strona kodowa nie jest słowem kluczowym. +,-, *, /, = (,), ", [,] i innych konstrukcją języka pierwszej klasy, nie są podane w tym miejscu może zawierać tylko znaki alfabetu łacińskiego.  
  
 Proste identyfikatory mogą być tylko znaki alfabetu łacińskiego. Pozwala to uniknąć niejednoznaczności podczas porównywania, ponieważ oryginalne wartości są porównywane. Na przykład ABC będzie różnić się w w strony kodowe kalendarza japońskiego i łacińskiego.  
  
## <a name="see-also"></a>Zobacz także
- [Omówienie jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
